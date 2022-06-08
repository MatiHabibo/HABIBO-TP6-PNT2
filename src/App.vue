<template>
  <div class="app">
       <Header :pickedColor="pickedColor" />
    <Navigator @isHard="isHard = $event" @squareQty="squareQty = $event" @colors="getColors" @pickedColor="getPicked"
      :message="message" />
    <Container :squareQty="squareQty" :colors="colors" @selectedColor="getSelected" @pickedColor="getPicked"
      @message="getMessage" :pickedColor="pickedColor" />
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
      isHard: true,
      squareQty: 0,
      colors: [],
      selectedColor: '',
      pickedColor: '',
      message: '',
    }
  },
  methods : {
    getColors(e) {
      this.colors = e;
    },
    getSelected(e) {
      this.selectedColor = e;
    },
    getPicked(e) {
      console.log(e);
      this.pickedColor = e;
    },
    getMessage(e) {
      this.message = e;
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
