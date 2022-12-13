<template>
  <StickyNote />
</template>

<script>
export default {
  name: "App",
};
</script>
<script setup>
import StickyNote from "./components/StickyNote.vue";
</script>

<style>
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}
* {
  margin: 0;
  padding: 0;
  /* background: #009578; */
}
</style>
