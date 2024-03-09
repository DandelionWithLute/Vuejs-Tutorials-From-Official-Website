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


Use v-model to connect variables 
<!-- <script setup>
import { ref } from "vue";

const text = ref("");
const changeValue = (e) => {
  text.value = e.target.value;
};
</script>
The later one was better.
<template>
  <input :value="text" v-on:input="changeValue" />
  <input v-model="text" />
  {{ text }}
</template> -->

List Rendering
1. Check the differences between react and vue
  li key={items.id} /li vs. li key="items.id" /li
2. Console Error: Assignment to constant variable
3. Cannot use e.target.value
  You need to use ref("").value
4. e.preventDefault(); is changed to form @submit.prevent="variable"  /form
5. You must say todos.value = todos.value.filter((t) arrow t !== todoprop) instead of just using .filter method
<!-- <script setup>
import { ref } from "vue";
let id = 0;
const newToDo = ref("");
const todos = ref([
  { id: id++, text: "Play Counter-Strike" },
  { id: id++, text: "Play League of Legend" },
  { id: id++, text: "Play Player Unknown's Battle Grounds" },
]);

const addTodo = () => {
  todos.value.push({ id: id++, text: newToDo.value });
  newToDo.value = "";
};

const removeToDo = (todo) => {
  todos.value = todos.value.filter((t) => t !== todo);
};
</script>
<template>
  <form @submit.prevent="addTodo">
    <input v-model="newToDo" required placeholder="add new todo here..." />
    <button>Add Todo</button>
  </form>
  <ui>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <button @click="removeToDo(todo)">X</button>
    </li>
  </ui>
</template> -->

The Computed Property Part was ignored
I guess it's AKA conditional rendering
just add another key with value in object to the array
<!-- <script setup>
</script>

<template>
  <p>This is <s>strikethrough</s> text.</p>
  <p>This is <strike>strikethrough</strike> text.</p>
  <p>This is <del>strikethrough</del> text.</p>
</template> -->

Lifecycle and Template Refs
relative to useEffect(()arrow{setMounted(true)},[])
[important]watch was like useEffect Hook testing for data changes and update
!!!!!!
While React's approach with useEffect is different from Vue's watchers, the underlying concepts are similar. Both aim to provide a way to reactively respond to changes in data or component lifecycle events. By understanding the nuances of React's useEffect hook and how it handles side effects, you can mitigate many of the common problems associated with data fetching and state updates in React applications.
!!!!!!
<!-- <script setup>
import { ref, watch } from 'vue'

const todoId = ref(1)
const todoData = ref(null)

async function fetchData() {
  todoData.value = null
  const res = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
  )
  todoData.value = await res.json()
}

fetchData()

watch(todoId, fetchData)
</script>

<template>
  <p>Todo id: {{ todoId }}</p>
  <button @click="todoId++" :disabled="!todoData">Fetch next todo</button>
  <pre>{{ todoData }}</pre>
</template> -->

<!-- <script setup>
import ChildComponent from './ChildComponent.vue'
</script>

<template>
  <ChildComponent />
</template> -->

Emits
A child component can also emit events to the parent
[ignored]no need to dive that deep

<script setup>
import { ref } from "vue";
import ChildComponent from "./ChildComponent.vue";
const msg = ref("from parent");
</script>

<template>
  <ChildComponent> Message:{{ msg }} </ChildComponent>
  <!-- <ChildComponent /> -->
</template>