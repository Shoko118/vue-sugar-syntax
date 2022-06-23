<script setup>
import { watchEffect } from "vue";

const name = "Uwu";
const input = $ref("");
const users = $ref([
  {
    id: 1,
    name: "Leon",
  },
  {
    id: 2,
    name: "Ada",
  },
  {
    id: 3,
    name: "Chris",
  },
]);

function addUsers() {
  if (!input) return;

  users.push({ name: input });

  input = "";
}

function deleteUsers(user) {
  users = users.filter((item) => item.id !== user.id);
}

watchEffect(() => {
  console.log(name);
});
</script>

<template>
  <h1>Sugar Syntax Vue</h1>

  <label>Type Me</label>
  <input type="text" placeholder="type me....." v-model="input" @keydown.enter="addUsers" />
  {{ input }}

  <button @click.prevent="addUsers">Add</button>

  <ul v-for="user in users" :key="user.id">
    <li>{{ user.name }}</li>
    <button @click.prevent="deleteUsers(user)">Delete</button>
  </ul>
</template>
