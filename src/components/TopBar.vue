<script setup>
const emit=defineEmits(['add']);
function addTodo(){
  emit('add')
}

</script>
<template>
  <header>
    <nav class="flex py-5 px-10 justify-between bg-white shadow items-center">
      <h1 class="font-bold">Logo</h1>
      <button class="primary-btn" @click="addTodo">Add todo</button>
    </nav>
  </header>
</template>
