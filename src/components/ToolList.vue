<template>
    <!-- grid classes for responsive layout -->
    <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-3">
      <ToolCard
        v-for="tool in tools"
        :key="tool.id"
        :tool="tool"
        @delete-tool="onDeleteTool"
      />
    </div>
  </template>
  
  <script setup>
  import ToolCard from './ToolCard.vue'
  import { defineProps, defineEmits } from 'vue'
  
  // Props
  const props = defineProps({
    tools: {
      type: Array,
      required: true
    }
  })
  
  // Emits
  const emit = defineEmits(['delete-tool'])
  
  function onDeleteTool(toolId) {
    emit('delete-tool', toolId)
  }
  </script>
  
  <style scoped>
  </style>
  