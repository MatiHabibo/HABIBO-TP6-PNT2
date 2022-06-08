<template>
  <section class="src-components-navigator">
    <div id="navigator">
      <button id="reset" @click="restart()">New colors</button>
      <span class="msg">{{ message }} </span>

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
    </div>
  </section>
</template>

<script>
export default {
  name: "src-components-navigator",
  components: {},
  props: ['message'],
  mounted() {
    this.init(this.squareQty)
  },
  data() {
    return {
      isHard: false,
      squareQty: 6,
      colors: [],
      pickedColor: '',
    };
  },
  methods: {
    emit() {
      this.$emit("isHard", this.isHard);   
      this.$emit('squareQty', this.squareQty);
    },
    easyToHard() {
      this.isHard = false;
      this.squareQty = 3;
      this.$emit("isHard", this.isHard);
      this.$emit("squareQty", this.squareQty);

    },
    hardToEasy() {
      this.isHard = true;
      this.squareQty = 6;
      this.$emit("isHard", this.isHard);
      this.$emit("squareQty", this.squareQty);
    },
        init(squareQty) {
      this.colors = this.createNewColors(squareQty);
      this.pickedColor = this.colors[this.pickColor()];
      this.$emit('colors', this.colors);
      this.$emit('pickedColor', this.pickedColor);
    },
    createNewColors(numbers) {
      const arr = [];
      for (let i = 0; i < numbers; i++) {
        arr.push(this.createRandomStringColor());
      }
      return arr;
    },
    createRandomStringColor() {
      const newColor = "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")";
      return newColor;
    },
    randomInt() {
      return Math.floor(Math.random() * 256);
    },
    pickColor() {
      let quantity;
      if (this.isHard) {
        quantity = 6;
      } else {
        quantity = 3;
      }
      return Math.floor(Math.random() * quantity);
    },
    restart() {
      this.colors = this.createNewColors(this.squareQty);
      this.$emit('colors', this.colors);

    }
  },
  computed: {},
};
</script>

<style scoped lang="css">
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

.msg {
  color: red;
  display: inline-block;
  width: 20%;
}
</style>
