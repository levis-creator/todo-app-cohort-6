<script setup>
import { ref } from "vue";
import TodoForm from "./components/TodoForm.vue";
import TodoList from "./components/TodoList.vue";
import TopBar from "./components/TopBar.vue";
const displayForm=ref(false)
const data=ref([
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
const editIndex=ref(null)

function closeForm() {
  displayForm.value=false
  editIndex.value=null
}
function openForm() {
  displayForm.value=true
}
function handleSubmit(newData) {
  if(editIndex.value!==null){
    // editting data
    data.value[editIndex.value]={
      ...data.value[editIndex],
      ...newData
    }
  }else{
    // adding new data
    data.value.push({
      ...newData,
      isCompleted:false
    })
  }
  closeForm()
}
function handleDelete(index) {

}
function handleEdit(index){
  editIndex.value=index
  openForm()
}
</script>

<template>
  <TopBar @add="openForm"/>
  <TodoForm
  v-if="displayForm"
   @close="closeForm"
   @submit="handleSubmit"
   :initialData="editIndex!==null?data[editIndex]:null"
   />
  <TodoList :todos="data" @delete="handleDelete" @edit="handleEdit"/>
</template>

