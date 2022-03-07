<script setup>
import { ref } from "vue";

let id = 0;
let start = true;
const newTodo = ref("");
const todos = ref([]);

function add() {
  todos.value.push({ id: id++, name: newTodo.value, complete: false });
  newTodo.value = "";
}

function removeItem(todo) {
  todos.value = todos.value.filter((t) => t !== todo);
}

function save() {
  const data = JSON.stringify(todos.value);
  localStorage.setItem("myActivities", data);
}

function removeAll() {
  localStorage.clear();
  todos.value = [];
}
function markAsDone(todo) {
  todo.complete = !todo.complete;
}

function runOnce() {
  if (start) {
    return (todos.value =
      JSON.parse(localStorage.getItem("myActivities")) || []);
  }
  start = !start;
}

runOnce();
</script> 

<template>
  <div class="box">
    <input
      v-model="newTodo"
      placeholder="Task"
      type="text"
      @keyup.enter="add"
    />
    <button @click="add">Add</button>
    <button @click="save">Save</button>
    <button @click="removeAll">Delete All</button>
  </div>
  <ul>
    <li
      v-for="todo in todos"
      v-bind:key="todo.id"
      v-bind:class="{ complete: todo.complete }"
    >
      {{ todo.name }}
      <button @click="markAsDone(todo)">✔</button>
      <button @click="removeItem(todo)">✖</button>
    </li>
  </ul>
  <footer>
    <h5>
      <a
        href="https://www.linkedin.com/in/tim-gottling-tegman-b31262227/"
        target="_blank"
      >
        Linkedin
      </a>
      <a href="https://github.com/Namget92" target="_blank"> Github </a>
      <br />
      2022 - Tim Gottling Tegman
    </h5>
  </footer>
</template> 

<style>
html {
  display: grid;
  justify-content: center;
  padding: 0;
  font-size: 1.5rem;
}
li {
  list-style-type: none;
  font-weight: bold;
  padding: 0.25rem;
}
.complete {
  color: green;
  text-decoration-line: line-through;
}
.box {
  display: grid;
  grid-template-columns: 5fr 1fr 1fr 2fr;
  justify-content: center;
}
input,
button {
  text-align: center;
  font-size: 1rem;
}
a {
  padding: 1%;
  text-decoration: none;
  color: black;
}
</style>