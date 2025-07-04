<script setup>
import TodoItem from './TodoItem.vue';

const {todos}=defineProps(['todos'])
const emit= defineEmits(['delete','edit']);

</script>
<template>
  <div class="mt-10 px-10">
    <h1 class="text-2xl font-bold text-center">Todo List</h1>
    <!-- the list -->
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4">
      <TodoItem
      v-for="(todo, index) in todos"
        :key="index"
        @delete="emit('delete', $event)"
        @edit="emit('edit', $event)"
        :data="todo" :index="index" />
    </div>
  </div>
</template>
