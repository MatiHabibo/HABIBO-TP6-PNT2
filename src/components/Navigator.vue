<template>
  <section class="src-components-navigator">
    <div id="navigator">
      <button id="reset" @click="restart()">New colors</button>
      <span id="message"> Juega! </span>

      <!-- <button id="easy" @click="easyBtn()" :class="getClass(isHard)">easy</button>
      <button id="hard" class="selected" :class="getClass(isHard)" @click="hardBtn()">hard</button> -->

      <button
        id="easy"
        :class="[!isHard ? 'selected' : '']"
        @click="easyToHard()"
      >
        easy
      </button>
      <button
        id="hard"
        :class="[isHard ? 'selected' : '']"
        @click="hardToEasy()"
      >
        hard
      </button>

      <Container :hardAPasar="isHard" />
    </div>
  </section>
</template>

<script>
import Container from "./Container.vue";

export default {
  name: "src-components-navigator",
  components: {
    Container,
  },
  props: [],
  mounted() {},
  data() {
    return {
      isHard: true,
      colorCount: 6,
      // pickedColor = colors[PickColor()],
      // colors = [],
      // squares = []
    };
  },
  methods: {
    easyToHard() {
      if (this.isHard) {
        this.colorCount = 3;
        this.isHard = !this.isHard;
        this.restart();
      }
    },
    hardToEasy() {
      if (!this.isHard) {
        this.isHard = !this.isHard;
        this.colorCount = 6;
         this.restart();
      }
    },

//  init(){
// 	for (var i = 0; i <squares.length; i++) {
// 		console.log(colors[i])
// 	squares[i].style.backgroundColor = colors[i];
// 	squares[i].addEventListener("click", function(){
// 		var clickedColor = this.style.backgroundColor;
// 		if (clickedColor === pickedColor) {
// 			messageDisplay.textContent = "You Picked Right!";
// 			setAllColorsTo(pickedColor);
// 			restartButton.textContent = "Play Again!";
// 			header.style.backgroundColor = pickedColor;
// 		} else {
// 			this.style.backgroundColor = "#232323";
// 			messageDisplay.textContent = "Try Again!";
// 			messageDisplay.style.color = "#000000";
// 		}
// 	});
// }

//  restart();
// }

    restart() {
      console.log('tocaste new');
      this.colors = this.createNewColors(this.colorCount);
      this.pickedColor = this.colors[this.PickColor()];
      this.colorDisplay.textContent = this.pickedColor;
      this.textContent = "Pick New Colors!";
      this.header.style.backgroundColor = "steelblue";
      this.messageDisplay.textContent = "";
      this.restartButton.textContent = "New Colors!";
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
    createNewColors(numbers){
	var arr = [];
	for (var i = 0; i < numbers; i++) {
		arr.push(this.createRandomStringColor());
	}
    return arr;
},

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
