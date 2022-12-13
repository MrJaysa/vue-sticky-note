<template>
  <div :class="currentTheme" class="theme-options">
    <div
      id="theme-white"
      :class="{ active: currentTheme === 'theme-white' }"
      @click="switchTheme('theme-white')"
    ></div>
    <div
      id="theme-black"
      :class="{ active: currentTheme === 'theme-black' }"
      @click="switchTheme('theme-black')"
    ></div>
    <div
      id="theme-orange"
      :class="{ active: currentTheme === 'theme-orange' }"
      @click="switchTheme('theme-orange')"
    ></div>
    <div
      id="theme-purple"
      :class="{ active: currentTheme === 'theme-purple' }"
      @click="switchTheme('theme-purple')"
    ></div>
    <div
      id="theme-green"
      :class="{ active: currentTheme === 'theme-green' }"
      @click="switchTheme('theme-green')"
    ></div>
    <div
      id="theme-black"
      :class="{ active: currentTheme === 'theme-black' }"
      @click="switchTheme('theme-black')"
    ></div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const currentTheme = ref(localStorage.getItem("theme-color"));

const emit = defineEmits("toggleColor");

const switchTheme = (theme) => {
  localStorage.setItem("theme-color", theme);
  currentTheme.value = localStorage.getItem("theme-color");
};
</script>

<style scoped>
@import "../assets/css/main.css";
</style>
