<!-- <script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style> -->

You must have setup to start this vue file
<!-- <script setup>
import { reactive, ref } from "vue";
let counter = reactive({ count: 0 });
let message = ref("Hello World!");
</script>
<template>
  <div>
    <h1>Hello</h1>
    <h1>{{ message }}</h1>
    <h2>{{ counter.count }}</h2>
  </div>
</template> -->

Make me red
1st You must use :class
2nd ref was relative to css style
3rd class was relative to constant variable
which means :class first goes to the variable then redirected to style
<!-- <script setup>
import { ref } from "vue";
const titleClass = ref("title");
</script>

<template>
  <h1 :class="titleClass">Make me red</h1>
</template>

<style scoped>
.title {
  color: red;
}
</style> -->
Event Listeners counter project
remember .value when using ref to initiate values

<!-- <script setup>
import { ref } from "vue";
const counter = ref(0);
const increment = () => {
  counter.value += 1;
};
</script>
<template>
  <button @click="increment">increment</button>
  <h1>Count is:{{ counter }}</h1>
</template> -->

<script setup>
import { ref } from "vue";

const text = ref("");
const changeValue = (e) => {
  text.value = e.target.value;
};
</script>
<template>
  <input :value="text" v-on:input="changeValue" />
  <!-- <input v-model="text" /> -->
  {{ text }}
</template>