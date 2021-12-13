<template>
  <div class="about">
    <h1 class="fw-bold">Hi, my name is Rafal!</h1>
    <p class="small">This is a sample project showing some of the coding traits that I've got. Having more time it would
    definitely evolve to something much better, nevertheless I hope you have enjoyed seeing this.
    </p>
    <br/><br/>
    <div class="pulse"><p class="para-item">Enjoy</p></div>
  </div>
</template>

<style>

.para-item {
  vertical-align: center;
  line-height: 150px;
}

.pulse {
  height: 150px;
  width: 150px;
  margin: 0 auto;
  background-color: red;
  animation-name: pulse;
  animation-duration: 1.2s;
  animation-direction: alternate;
  animation-iteration-count: infinite;
  animation-timing-function: ease-out;
}

@keyframes pulse {
  0% {
    transform: scale(0.4);
    background-color: red;
    border-radius: 100%;
  }
  50% {
    background-color: green;
  }
  100% {
    transform: scale(1.5);
    background-color: lightgreen;
    border-radius: 10%;
  }
}

</style>
