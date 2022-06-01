<template>
  <section class="src-components-container">
    <div id="container">

      <h2 style="color: red">{{ isHard }}</h2>
      <Square v-for="(color, index) in colors" :color="color" :key="index"/>

      <!-- <div v-if="hardAPasar">
        <Square />
        <Square />
        <Square />
        <Square />
        <Square />
        <Square />
      </div>
      <div v-else>
        <Square />
        <Square />
        <Square />
      </div> -->
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
  props: [
    'isHard'
    //"hardAPasar"
  // , "cantidadSquare"
  ],
  mounted() {
    
  },
  data() {
    return {
      colors:['red', 'green', 'brown', 'blue', 'yellow', 'grey']
    };
  },
  methods: {},

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
