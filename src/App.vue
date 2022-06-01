<template>
  <div class="app">
    <Header :colorRgb="colorRgb"/>
    <Navigator @isHard="isHard = $event"/>
    <Container :isHard="isHard" @colorRgb="colorRgb = $event"/>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.min.css";
import "jquery";
import "popper.js";
import "bootstrap";

import Header from "./components/Header.vue";
import Navigator from "./components/Navigator.vue";
 import Container from "./components/Container.vue";


export default {
  name: "App",
  components: {
    Header,
    Navigator,
    Container
  },
  data(){
    return{
      isHard:false
    }
  }
};
</script>

<style>
body {
	background: #232323;
	margin: 0;
	font-family: "Montserrat", "Avenir";
}

</style>
