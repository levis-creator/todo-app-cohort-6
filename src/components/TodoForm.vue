<script setup>
const emit = defineEmits(['close', 'submit'])
function closeForm() {
  emit('close')
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
        <form>
          <div class="form-container">
            <label for="title">Title</label>
            <input class="form-input" type="text" name="title" id="title">
          </div>
          <div class="form-container">
            <label for="description">Description</label>
            <textarea class="form-input" type="text" name="description" id="description" />
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
