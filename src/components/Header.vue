<template>
   <section class="header-component">
    <div id="header" :style="{background: this.setCol }">
      <h1>The Great <br>
        <span id="colorDisplay"></span>
        <h2>{{ pickedColor }}</h2>
        <br>
        Guessing Game
      </h1>
    </div>
  </section>

</template>

<script lang="js">
export default {
  name: 'header-component',
  props: [],
  mounted() {
  },
  data() {
    return {
    }
  },
  methods: {
  },
  computed: {
    setCol(){
      return this.message == 'You win' ?  this.pickedColor : 'steelblue'
    },
     
  }
}
</script>

<style scoped lang="css">
#header {
  transition: all 0.3s;
  text-transform: uppercase;
  text-align: center;
  margin: 0;
  color: white;
}
h1 {
  font-weight: normal;
  line-height: 1.1;
  padding: 20px 0;
}
#colorDisplay {
  font-size: 200%;
}
</style>