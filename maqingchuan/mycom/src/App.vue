<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <slider de_num="10"></slider>
    <slider max="50" show_input="true" de_num="25"></slider>
    <transfer :data="[1,2,3,4,5,6]"></transfer>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import slider from "./components/slider.vue"; //滑动块
import transfer from "./components/transfer"; //穿梭框

export default {
  name: "App",
  components: {
    slider,
    transfer
  }
};
</script>

<style>
* {
  list-style: none;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
