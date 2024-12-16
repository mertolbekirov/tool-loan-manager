<template>
  <div class="p-4 bg-white rounded shadow">
    <h2 class="text-xl font-semibold mb-2">Add a New Tool</h2>
    <form @submit.prevent="onSubmit">
      <div class="mb-2">
        <label class="block font-medium" for="toolName">Tool Name:</label>
        <input
          id="toolName"
          v-model="name"
          type="text"
          class="border border-gray-300 p-1 w-full rounded"
          required
        />
      </div>

      <div class="mb-2">
        <label class="block font-medium" for="toolImage">Image URL:</label>
        <input
          id="toolImage"
          v-model="imageSrc"
          type="text"
          class="border border-gray-300 p-1 w-full rounded"
          required
        />
      </div>

      <div class="mb-2">
        <label class="block font-medium" for="toolDesc">Description:</label>
        <input
          id="toolDesc"
          v-model="description"
          type="text"
          class="border border-gray-300 p-1 w-full rounded"
          required
        />
      </div>

      <button
        type="submit"
        class="bg-blue-600 text-white px-3 py-1 rounded hover:bg-blue-700"
      >
        Add Tool
      </button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const name = ref('')
const imageSrc = ref('')
const description = ref('')

// Define emits
const emit = defineEmits(['add-tool'])

function onSubmit() {
  // Construct a new tool object
  const newTool = {
    name: name.value,
    imageSrc: imageSrc.value,
    description: description.value
  }

  // Emit upwards
  emit('add-tool', newTool)

  // Clear form fields
  name.value = ''
  imageSrc.value = ''
  description.value = ''
}
</script>