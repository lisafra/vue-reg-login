<template>
<div id="app">
  <div class="background-img">
    <img src="./assets/bj.jpg" />
  </div>
  <reglogin></reglogin>
</div>
</template>

<script>
import Reglogin from './components/reglogin/Reglogin'

export default {
  name: 'app',
  components: {
    Reglogin
  }
}
</script>

<style>
.background-img {
  position: absolute;
  z-index: -1;
}
</style>
