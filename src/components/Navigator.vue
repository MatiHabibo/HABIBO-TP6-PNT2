<template>
  <section class="src-components-navigator">
    <div id="navigator">
      <button id="reset" @click="restart()">New colors</button>
      <span id="message"> Juega! </span>

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
  props: [],
  mounted() {
    this.emit();
  },
  data() {
    return {
      isHard: true,
      colCount : 6,
    };
  },
  methods: {
    emit() {
      this.$emit("isHard", this.isHard);
      this.$emit("colCount", this.colCount);
    },
    easyToHard() {
      this.isHard = false;
      this.colCount = 3;
      this.$emit("isHard", this.isHard);
      this.$emit("colCount", this.colCount);

    },
    hardToEasy() {
      this.isHard = true;
      this.colCount = 6;
      this.$emit("isHard", this.isHard);
      this.$emit("colCount", this.colCount);
    },
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
