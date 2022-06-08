<template>
  <section class="src-components-container">
    <div id="container">
      <h2 style="color: red">{{ isHard }}</h2>
      <h3 style="color: red">{{ colCount }}</h3>
      <Square v-for="(square, index) in squareQty" :key="index" :color="colors[index]" :pickedColor="
      pickedColor" @selectedColor="selectedColor = $event" />
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
  props: ["squareQty", "colors", "pickedColor"],

  data() {
    return {

    };
  },
  methods: {
   
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
