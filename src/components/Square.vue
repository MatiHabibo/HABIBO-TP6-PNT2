<template>
  <section class="src-components-square">
    <div class="square" :style="{background: this.color}"></div>
  </section>
</template>

<script>
export default {
  name: "src-components-square",
  props: ['color'],
  mounted() {},
  data() {
    return {};
  },
  methods: {},
  computed: {},
};
</script>

<style scoped lang="css">
.src-components-square {
}
.square {
  width: 30%;
  background: blue;
  padding-bottom: 30%;
  float: left;
  margin: 1.66%;
  border-radius: 10%;
  transition: background 0.8s;
  -webkit-transition: background 0.8s;
  -moz-transition: background 0.8s;
}
</style>
