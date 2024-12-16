<template>
    <div class="bg-white rounded shadow p-4">
      <img
        class="w-full h-32 object-contain mb-2"
        :src="tool.imageSrc"
        :alt="tool.name"
      />
      <h3 class="font-bold text-lg mb-1">{{ tool.name }}</h3>
      <p class="text-gray-600 mb-2">{{ tool.description }}</p>
      <button
        class="bg-red-600 text-white px-2 py-1 rounded hover:bg-red-700"
        @click="onDelete"
      >
        Delete Tool
      </button>
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue'
  
  const props = defineProps({
    tool: {
      type: Object,
      required: true
    }
  })
  
  const emit = defineEmits(['delete-tool'])
  
  function onDelete() {
    emit('delete-tool', props.tool.id)
  }
  </script>
  
  <style scoped>
  </style>
  