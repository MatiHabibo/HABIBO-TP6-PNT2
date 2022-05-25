<template>
  <section class="src-components-navigator">
    <div id="navigator">
      <button id="reset">New colors</button>
      <span id="message"> </span>

      <!-- <button id="easy" @click="easyBtn()" :class="getClass(isHard)">easy</button>
      <button id="hard" class="selected" :class="getClass(isHard)" @click="hardBtn()">hard</button> -->

      <button id="easy">easy</button>
      <button id="hard" class="selected">hard</button>
     
    </div>
  </section>
</template>

<script>
export default {
  name: "src-components-navigator",
  props: [],
  mounted() {},
  data() {
    return {
      // isHard: true,
    };
  },
  methods: {
  //   getClass(isHard){
  //     if(isHard){
  //       return "selected"
  //     }else{
  //       return ""
  //     }
  //   }
  //   ,
  //   easyBtn() {
  //     if (this.isHard) {
  //       this.isHard = true;
  //       // easyButton.classList.add("selected");
  //       // hardButton.classList.remove("selected");
  //       // colorCount = 3;
  //       // for (var i = 0; i < colorCount; i++) {
  //       //   squares[i + 3].style.display = "none";
  //       // }
  //       // restart();
  //     }
  //   },
  //   hardBtn() {
  //     if (!this.isHard) {
  //       this.isHard = false;
  //       // hardButton.classList.add("selected");
  //       // easyButton.classList.remove("selected");
  //       // colorCount = 6;
  //       // restart();
  //       // for (var i = 3; i < 6; i++) {
  //       // 	squares[i].style.display = "block";
  //       // }
  //     }
  //   },
  //   // restart() {
  //   //   colors = createNewColors(colorCount);
  //   //   pickedColor = colors[PickColor()];
  //   //   colorDisplay.textContent = pickedColor;
  //   //   this.textContent = "Pick New Colors!";
  //   //   header.style.backgroundColor = "steelblue";
  //   //   messageDisplay.textContent = "";
  //   //   restartButton.textContent = "New Colors!";
  //   //   for (var i = 0; i < squares.length; i++) {
  //   //     squares[i].style.backgroundColor = colors[i];
  //   //   }
  //   // },
 },
  computed: {},
  };
</script>

<style scoped lang="css">
/* .src-components-navigator {

  } */
h1 {
  font-weight: normal;
  line-height: 1.1;
  padding: 20px 0;
}
#navigator {
  background: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;
}
.selected {
  background-color: steelblue;
  color: white;
}
button {
  border: none;
  background-color: white;
  font-family: "Montserrat", "Avenir";
  text-transform: uppercase;
  height: 100%;
  font-weight: 700;
  letter-spacing: 1px;
  color: steelblue;
  transition: all 0.3s;
  outline: none;
}
button:hover {
  color: white;
  background-color: steelblue;
}
</style>
