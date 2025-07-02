<script setup>
import { ref } from "vue";
import TodoForm from "./components/TodoForm.vue";
import TodoList from "./components/TodoList.vue";
import TopBar from "./components/TopBar.vue";
const displayForm=ref(false)
function closeForm() {
  displayForm.value=false
}
function openForm() {
  displayForm.value=true
}
</script>

<template>
  <TopBar @add="openForm"/>
  <TodoForm v-if="displayForm" @close="closeForm"/>
  <TodoList/>
</template>

