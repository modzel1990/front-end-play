<template>
  <div class="row">
    <div class="col-xs-12 col-sm-12 col-md-7 col-lg-7">
      <div class="info-container">
        <ul class="list-unstyled text-start">
          <li>
            <span class="fw-bold">Name:</span> {{ item.name ? item.name : 'No name provided' }}
          </li>
          <li>
            <span class="fw-bold">Description:</span> {{ item.description ? item.description: 'No description provided' }}
          </li>
          <li>
            <span class="fw-bold">Start Date:</span> {{ item.starts_at ? convertDate(item.starts_at) : 'Continuous' }}
          </li>
          <li>
            <span class="fw-bold">End Date:</span> {{ item.ends_at ? convertDate(item.ends_at) : 'Continuous'}}
          </li>
          <li>
            <span class="fw-bold">Enabled:</span> {{ isEnabled(item.is_enabled, item.ends_at) ? 'Yes' : 'No' }}
          </li>
          <li>
            <button @click="isHidden = !isHidden" class="btn btn-outline-primary mt-2 mb-2">Show info</button>
            <p v-if="!isHidden"><span class="fw-bold">Voucher code:</span> {{ item.voucher_code ? item.voucher_code : 'No voucher code provided' }}</p>
            <p v-if="!isHidden"><span class="fw-bold">Voucher Expiry Days:</span> {{ item.voucher_code_expires_days ? item.voucher_code_expires_days : 'No voucher code expiry provided' }}</p>
          </li>
          <li>
            <button @click="isHiddenHtml = !isHiddenHtml" class="btn btn-outline-dark mt-2 mb-2" :data-bs-target="'#campaignModal' + index">Preview</button>
            <br/>
          </li>
        </ul>

        <!-- Modal -->
        <div v-show="!isHiddenHtml" :class="'modal-style modal' + index" :id="'campaignModal' + index" tabindex="-1" aria-labelledby="campaignModalLabel" aria-hidden="true">
          <div class="modal-dialog">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title" id="campaignModalLabel">{{ item.name }}</h5>
                <button @click="isHiddenHtml = !isHiddenHtml" type="button" class="btn-close" aria-label="Close"></button>
              </div>
              <div class="modal-body">
                <iframe :srcdoc="item.html" class="w-100 h-100"></iframe>
              </div>
              <div class="modal-footer">
                <button @click="isHiddenHtml = !isHiddenHtml" type="button" class="btn btn-secondary">Close</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-xs-12 col-sm-12 col-md-5 col-lg-5">
      <div class="img-container">
        <a v-if="item.screenshot_url" :href="item.screenshot_url" target="_blank"><img v-if="item.screenshot_url" :src="item.screenshot_url" class="img-fluid" :alt="item.name"/></a>
        <img v-else :src="require(`@/assets/no-image-found.png`)" class="img-fluid" alt="no-image-found"/>
      </div>
    </div>
    <br/>
    <div class="animate-one"></div>
    <div class="animate-two"></div>
    <br/>
  </div>
</template>

<script>

export default {
  name: 'Main',
  props: ['item', 'index'],
  data () {
    return {
      isHidden: true,
      isHiddenHtml: true
    }
  },
  methods: {
    convertDate (date) {
      return new Date(date).toLocaleDateString()
    },
    isEnabled (enabled, date) {
      // If not date, return value of enabled
      if (date === null) {
        return enabled
      }
      // Check if endDate is > than currentDate (if so return TRUE)
      return this.checkDate(date)
    },
    checkDate (date) {
      const endDate = Date.parse(date)
      let currentDate = new Date()
      currentDate = Date.parse(currentDate)

      return currentDate < endDate
    }
  }
}
</script>

<style scoped lang="scss">

.img-container {
  margin: 15px;
  padding: 30px;
  border: 1px solid darkgrey;
  border-radius: 10px;
  box-shadow: 0 1rem 1rem rgba(0, 0, 0, .25);
  transition: 0.5s;
  transform: scale(1);
}

.img-container:hover {
  transition: 0.5s;
  transform: scale(1.05);
}

.info-container {
  margin: 15px;
  padding: 30px;
  border: 1px solid darkgrey;
  border-radius: 10px;
  box-shadow: 0 1rem 1rem rgba(0, 0, 0, .25);
  transition: 0.5s;
  transform: scale(1);
}

.info-container:hover {
  transition: 0.5s;
  transform: scale(1.05);
}

.animate-one {
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background-color: red;
  position: relative;
  z-index: 99;
  animation-name: moveDotOne;
  animation-duration: 6s;
  animation-iteration-count: infinite;
}

@keyframes moveDotOne {
  0%   {background-color:red; left:2%; top:0px;}
  25%  {background-color:red; left:50%; top:0px;}
  50%  {background-color:blue; left:50%; top:10px;}
  75%  {background-color:blue; left:2%; top:10px;}
  100% {background-color:red; left:2%; top:0px;}
}

.animate-two {
  width: 25px;
  height: 25px;
  border-radius: 50%;
  background-color: blue;
  position: relative;
  z-index: 99;
  animation-name: moveDotTwo;
  animation-duration: 6s;
  animation-iteration-count: infinite;
}

@keyframes moveDotTwo {
  0%   {background-color:blue; left:94%; top:0px;}
  25%  {background-color:blue; left:50%; top:0px;}
  50%  {background-color:red; left:50%; top:10px;}
  75%  {background-color:red; left:94%; top:10px;}
  100% {background-color:blue; left:94%; top:0px;}
}

.modal-style {
  position: fixed;
  left: 0;
  top: 20%;
  width: 100%;
  height: auto;
  z-index: 9999;
  .modal-dialog {
    width: 100%;
    max-width: 100%;
    z-index: 9999;
  }
}
</style>
