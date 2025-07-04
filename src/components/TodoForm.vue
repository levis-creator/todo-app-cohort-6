<script setup>
import { ref, watch } from 'vue';

const emit = defineEmits(['close', 'submit'])
const {initialData}=defineProps(['initialData'])
const formData=ref({
  title:'',
  description:""
})

watch(
  ()=>initialData,
  (val)=>{
    if(val){
      formData.value.title=val.title;
      formData.value.description=val.description;
    }else{
      formData.value.title='';
      formData.value.description='';
    }
  },
  {immediate:true}
)

function closeForm() {
  emit('close')
}

function handleSubmit() {
  emit('submit', formData.value)
}
</script>
<template>
  <div class=" absolute top-0 left-0 right-0 bottom-0  z-10  ">
    <div class="absolute top-0 left-0 right-0 bottom-0 bg-black opacity-50"></div>
    <div class="bg-white max-w-md m-auto h-auto p-5 rounded-md z-20 relative">
      <!-- header -->
      <div class="flex justify-between">
        <h1>Add todo</h1>
        <button @click="closeForm">close</button>
      </div>
      <div>
        <form @submit.prevent="handleSubmit">
          <div class="form-container">
            <label for="title">Title</label>
            <input v-model="formData.title" class="form-input" type="text" name="title" id="title">
          </div>
          <div class="form-container">
            <label for="description">Description</label>
            <textarea v-model="formData.description" class="form-input" name="description" id="description" />
          </div>
          <div class="flex justify-end gap-2">
            <button class="primary-btn" type="submit">
              Add
            </button>
            <button class="danger-btn" @click="closeForm">
              Cancel
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<style scoped></style>
