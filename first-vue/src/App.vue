<template>
  <div id="app">
    <!-- <Console msg="text" text="text2" /> -->
    <Library v-on:change="printData" />
  </div>
</template>

<script>
// import Console from "./components/Console.vue";
import Library from "./components/Library.vue";


export default {
  name: "App",
  components: {
    // Console,
    Library,

  },
  methods: {
    printData(e) {
      console.log(e);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
