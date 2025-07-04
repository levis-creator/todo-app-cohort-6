<script setup>
import { defineProps } from "vue";
const { data, index } = defineProps(['data', 'index'])

const emit=defineEmits(['delete', 'edit'])
</script>
<template>
  <div class="bg-white shadow-md rounded-md p-4 hover:shadow-2xl">
    <div class="flex justify-between">
      <h2 class="font-semibold text-lg" :class="{ 'line-through': data.isCompleted }">{{ data.title }}</h2>
      <input type="checkbox" :checked="data.isCompleted" />
    </div>
    <div>
      <p class="text-gray-500 italic" v-if="data.description"> {{ data.description }}</p>
      <p v-else class="text-gray-500 italic">no description</p>
    </div>
    <div class="flex justify-end gap-3">
      <button @click="$emit('delete',index)">delete</button>
      <button @click="$emit('edit',index)">edit</button>
    </div>
  </div>
</template>
