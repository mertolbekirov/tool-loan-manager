<template>
    <div class="p-4 bg-white rounded shadow">
      <h2 class="text-xl font-semibold mb-2">Filter Tools</h2>
      <input
        v-model="filterText"
        type="text"
        placeholder="Filter by tool name"
        class="border border-gray-300 p-1 w-full rounded"
      />
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue'
  
  const filterText = ref('')
  
  // Emit definition
  const emit = defineEmits(['filter-changed'])
  
  // Watch for changes in filterText, emit upward
  watch(filterText, (newVal) => {
    emit('filter-changed', newVal)
  })
  </script>
  
  <style scoped>
  </style>
  