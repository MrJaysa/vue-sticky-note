<template>
  <div id="wrapper">
    <div class="container" v-for="(input, k) in inputs" :key="k">
      <div class="bar">
        <div class="delete" @click="deleteNote(k)">
          <p class="minus">-</p>
        </div>
        <div class="colors" :id="k" @click="popUp(k)"></div>
      </div>
      <div class="theme-options" v-show="themes">
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
      <textarea
        :class="currentTheme"
        class="note"
        v-model="input.name"
        placeholder="Enter note here"
      ></textarea>
    </div>
    <button class="add-note" @click="addnote">+</button>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Switcher from "./Switcher.vue";

const inputs = ref([{ name: "" }]);

const themes = ref(false);

const popUp = (index) => {
  themes.value = !themes.value;
};

const currentTheme = ref(localStorage.getItem("theme-color"));
const switchTheme = (theme) => {
  localStorage.setItem("theme-color", theme);
  currentTheme.value = localStorage.getItem("theme-color");
};

const hex = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, "A", "B", "C", "D", "E", "F"];
// const textarea = document.querySelector(".note");

const addnote = (index) => {
  inputs.value.push({ name: "" });

  let ex = "#";
  for (let i = 0; i < 6; i++) {
    ex += hex[hexColor()];
    console.log(ex);
    // color.textContent = ex;
    // document.querySelectorAll(".note").forEach((e) => {
    //   e.style.backgroundColor = ex;
    // });

    document.querySelectorAll(".note")[
      document.querySelectorAll(".note").length - 1
    ].style.backgroundColor = ex;
  }
};
let hexColor = () => {
  return Math.floor(Math.random() * hex.length);
};

const deleteNote = (index) => {
  inputs.value.splice(index, 1);
};
</script>

<style scoped>
@import "../assets/css/main.css";
#wrapper {
  display: grid;
  grid-template-columns: repeat(auto-fill, 300px);
  padding: 24px;
  gap: 24px;
  justify-content: center;
}
.bar {
  background: #333;
  display: flex;
  flex-direction: row-reverse;
  height: 2rem;
  transform: translateY(18.9rem);
  border-end-end-radius: 10px;
  border-end-start-radius: 10px;
}
.delete {
  background: #ff0000;
  position: absolute;
  height: 12px;
  width: 12px;
  border-radius: 50px;
  transform: translate(-5px, 10px);
  cursor: pointer;
  display: grid;
  place-items: center;
}
.minus {
  position: relative;
  background: transparent;
  transform: translateY(-4.5px);
  color: transparent;
}
.minus:hover {
  color: #333;
}
.colors {
  position: absolute;
  background: #ffffff;
  height: 12px;
  width: 12px;
  border-radius: 50px;
  transform: translate(-25px, 10px);
  cursor: pointer;
}
.note {
  height: 300px;
  width: 300px;
  box-sizing: border-box;
  /* background: #ffffff; */
  padding: 16px;
  border: none;
  outline: none;
  border-radius: 10px;
  box-shadow: 0 0 7px rgba(0, 0, 0, 0.15);
  resize: none;
  font-family: sans-serif;
  font-size: 16px;
}
.add-note {
  height: 300px;
  border: none;
  outline: none;
  background: rgba(0, 0, 0, 0.1);
  color: rgba(0, 0, 0, 0.5);
  border-radius: 10px;
  font-size: 120px;
  cursor: pointer;
  transition: background 0.2s;
  transform: translateY(2rem);
}
.add-note:hover {
  background: rgba(0, 0, 0, 0.2);
}
</style>

<!-- <template>
  <div>
    <div v-for="(input, k) in inputs" :key="k">
      <textarea v-model="input.name"></textarea>
      <p @click="add(k)">add</p>
      <p @click="remove(k)">remove</p>
      <p @click="togglePopUp(k)">popUp</p>
      <Switcher v-show="popUp" />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Switcher from "./Switcher.vue";

const inputs = ref([{ name: "" }]);
const popUp = ref(false);

const add = (index) => {
  inputs.value.push({ nmae: "" });
};

const remove = (index) => {
  inputs.value.splice(index, 1);
};

const togglePopUp = (index) => {
  popUp.value = !popUp.value;
};
</script>

<style></style> -->
