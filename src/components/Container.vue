<template>
  <section class="src-components-container">
    <div id="container">
      <h2 style="color: red">{{ isHard }}</h2>
      <Square
        v-for="(color, index) in colors"
        :color="color"
        :key="index"
        @click="this.clickEnSquare()"
      />
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
  props: ["isHard"],
  mounted() {
    this.init();
  },
  data() {
    return {
      squares: [],
      colors: [],
      colorCount: 6,
      pickedColor: "",
    };
  },
  methods: {
    ifIsHard() {
      if (this.isHard) {
        this.colorCount = 6;
      } else {
        this.colorCount = 3;
      }
    },
    init() {
      this.colors = this.createNewColors(this.colorCount);

      for (var i = 0; i < this.colorCount; i++) {
        // console.log(colors[i]);

        this.squares[i].style.backgroundColor = this.colors[i];
      }
      this.restart();
    },

    clickEnSquare() {
      var clickedColor = this.style.backgroundColor;
      if (clickedColor === this.pickedColor) {
        // messageDisplay.textContent = "You Picked Right!";
        this.setAllColorsTo(this.pickedColor);
        // restartButton.textContent = "Play Again!";
        // header.style.backgroundColor = pickedColor;
      } else {
        this.style.backgroundColor = "#232323";
        // messageDisplay.textContent = "Try Again!";
        // messageDisplay.style.color = "#000000";
      }
    },

    restart() {
      console.log("tocaste new");
      this.colors = this.createNewColors(this.colorCount);
      this.pickedColor = this.colors[this.PickColor()];
      // this.colorDisplay.textContent = this.pickedColor;
      // this.textContent = "Pick New Colors!";
      // this.header.style.backgroundColor = "steelblue";
      // this.messageDisplay.textContent = "";
      // this.restartButton.textContent = "New Colors!";
      this.ifIsHard();
      for (var i = 0; i < this.colorCount; i++) {
        this.squares[i].style.backgroundColor = this.colors[i];
      }
    },

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
      return Math.floor(Math.random() * this.colorCount);
    },
    createNewColors(numbers) {
      var arr = [];
      for (var i = 0; i < numbers; i++) {
        arr.push(this.createRandomStringColor());
      }
      return arr;
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
