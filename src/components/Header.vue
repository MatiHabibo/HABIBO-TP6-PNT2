<template>
  <section class="src-components-header">
    <div id="header">
      <h1>
        COLOR The Great <br />
        <span id="colorDisplay"> {{ pickedColor }}</span>
        <br />
        Guessing Game
      </h1>
    </div>
  </section>
</template>

<script>
export default {
  name: "src-components-header",
  props: ['pickedColor'],
  mounted() {
  },
  data() {
    return {};
  },
  methods: {
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

#header {
  transition: all 0.3s;
  background: steelblue;
  text-transform: uppercase;
  text-align: center;
  margin: 0;
  color: white;
}
</style>
