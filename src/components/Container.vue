<template>
  <section class="src-components-container">
    <div id="container">
      <h2 style="color: red">{{ isHard }}</h2>
      <h3 style="color: red">{{ colCount }}</h3>
      <Square
        v-for="(color, index) in colors"
        :color="color"
        :key="index"
      />
              <!-- @click="this.clickEnSquare()" -->
    </div>
  </section>
</template>

<script>
import Square from "./Square.vue";

export default {
  components: {
    Square,
  },
  name: "src-components-container",
  props: ["isHard", "colCount"],
  // beforeMounted(){
  //   this.init()
  // },
  mounted() {
    this.init();
  },
  // beforeUpdated(){
  //   this.init()
  // },
  updated() {
    // this.createNewColors(this.colCount)
    //  this.nuevosColores()
    // this.init()
    //  this.restart() //ESTO FALLA!
    
  },
  data() {
    return {
      squares: [],
      colors: [],
      pickedColor: "",
    };
  },
  methods: {
    init() {
      console.log("hola");
      this.colors = [];
      this.colors = this.createNewColors(this.colCount);

      for (var i = 0; i < this.colCount; i++) {
        // console.log(colors[i]);
        // this.colors.push("red")
        this.squares[i].style.backgroundColor = this.colors[i];
      }
      console.log(this.colors);
      //  this.restart();
    },
    restart() {
      //  this.colors = [];
      console.log("hola 2");
      //  this.colors = this.createNewColors(this.colCount); //EL PROBLEMA ESTA EN EL THIS.COLORS

      for (var i = 0; i < this.colCount; i++) {
        // console.log(colors[i]);

        this.squares[i].style.backgroundColor = this.colors[i];
      }
      console.log(this.colors);
      //  this.restart();
    },

    clickEnSquare() {
      console.log("hiciste click en square");
      var clickedColor = "red";
      if (clickedColor === this.pickedColor) {
        // messageDisplay.textContent = "You Picked Right!";
        this.setAllColorsTo(this.pickedColor);
        // restartButton.textContent = "Play Again!";
        // header.style.backgroundColor = pickedColor;
      } else {
        // this.style.backgroundColor = "#232323";
        // messageDisplay.textContent = "Try Again!";
        // messageDisplay.style.color = "#000000";
      }
    },

    // restart() {
    //   console.log("tocaste new");
    //   this.colors = this.createNewColors(this.colorCount);
    //   this.pickedColor = this.colors[this.PickColor()];
    //   // this.colorDisplay.textContent = this.pickedColor;
    //   // this.textContent = "Pick New Colors!";
    //   // this.header.style.backgroundColor = "steelblue";
    //   // this.messageDisplay.textContent = "";
    //   // this.restartButton.textContent = "New Colors!";
    //   this.ifIsHard();
    //   for (var i = 0; i < this.colorCount; i++) {
    //     this.squares[i].style.backgroundColor = this.colors[i];
    //   }
    // },

    createRandomStringColor() {
      var newColor =
        "rgb(" +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ")";
      //	console.log(newColor);
      this.$emit("colorRgb", newColor);
      return newColor;
    },
    randomInt() {
      return Math.floor(Math.random() * 256);
    },
    PickColor() {
      if (this.isHard) {
        this.colorCount = 6;
      } else {
        this.colorCount = 3;
      }
      return Math.floor(Math.random() * this.colCount);
    },
    createNewColors(numbers) {
      // if (this.colCount) {
        var arr = [];
        for (var i = 0; i < numbers; i++) {
          //arr.push("red");
           arr.push(this.createRandomStringColor());
        }
        return arr;
      // }
    },
    // setAllColorsTo(color) {
    //   this.squares.forEach(function (square) {
    //     this.square.style.backgroundColor = this.color;
    //   });
    // },
  },

  computed: {},
};
</script>

<style scoped lang="css">
.src-components-container {
}
#container {
  margin: 20px auto;
  max-width: 600px;
}
</style>
