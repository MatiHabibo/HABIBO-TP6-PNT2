<template>
  <section class="src-components-container">
    <div id="container">
      <div v-if="isHard">
        <Square/>
        <Square/>
        <Square/>
        <Square/>
        <Square/>
        <Square/>
      </div>
      <div v-else>
        <Square/>
        <Square/>
        <Square/>
      </div>
    </div>
  </section>
</template>

<script>
import Square from './Square.vue';
export default {
  components: { 
    Square 
  },
  name: "src-components-container",
  props: [],
  mounted() {},
  data() {
    return {
       isHard : true
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
