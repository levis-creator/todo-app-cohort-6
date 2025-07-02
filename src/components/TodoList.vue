<script setup>
import { ref } from "vue";
import TodoItem from "./TodoItem.vue";
const todos=ref([
  {
    title:"todo 1",
    description:"this is todo 1",
    isCompleted:false
  },  {
    title:"todo 2",
    description:"this is todo 2",
    isCompleted:false
  },  {
    title:"todo 3",
    description:"this is todo 3",
    isCompleted:true
  },  {
    title:"todo 4",
    description:"this is todo 4",
    isCompleted:true
  },  {
    title:"todo 5",
    description:"this is todo 5",
    isCompleted:false
  },
])
</script>
<template>
  <div class="mt-10 px-10">
    <h1 class="text-2xl font-bold text-center">Todo List</h1>
    <!-- the list -->
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4">
      <TodoItem v-for="(todo, index) in todos"  :key="index" :data="todo" />
    </div>
  </div>
</template>
