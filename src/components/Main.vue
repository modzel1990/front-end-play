<template>
  <div class="container">
    <div v-for="(item,index) in fetchedData.data" :key="index">
      <List :item="item" :index="index"/>
    </div>
  </div>
</template>

<script>
import List from './List'

export default {
  name: 'Main',
  components: {
    List
  },
  data () {
    return {
      dataUrl: 'https://run.mocky.io/v3/dfe80d90-c9d6-4add-bd64-a1fbaa1b5f73',
      fetchedData: '',
      errorMessage: ''
    }
  },
  async mounted () {
    fetch(this.dataUrl)
      .then(async response => {
        this.fetchedData = await response.json()

        if (!response.ok) {
          // get error message from body or default to response statusText
          const error = (this.fetchedData && this.fetchedData.message) || response.statusText
          return Promise.reject(error)
        }
      })
      .catch(error => {
        this.errorMessage = error
        console.error('There was an error!', error)
      })
  }
}
</script>

<style scoped lang="scss">

</style>
