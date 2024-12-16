<template>
  <div class="min-h-screen bg-gray-100 p-4">
    <!-- Header -->
    <header class="mb-4">
      <h1 class="text-3xl font-bold mb-2">Tool Loan Manager</h1>
    </header>

    <!-- AddTool Component -->
    <section class="mb-4">
      <AddTool @add-tool="handleAddTool" />
    </section>

    <!-- Filter Component -->
    <section class="mb-4">
      <ToolFilter @filter-changed="handleFilterChanged" />
    </section>

    <!-- ToolList Component -->
    <section>
      <ToolList
        :tools="filteredTools"
        @delete-tool="handleDeleteTool"
      />
    </section>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// Import child components
import AddTool from './components/AddTool.vue'
import ToolFilter from './components/ToolFilter.vue'
import ToolList from './components/ToolList.vue'

// Tools (seed data)
const tools = ref([
  {
    id: 1,
    name: 'Гедоре',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Gedore',
    description: 'Даден на Иван Петров',
  },
  {
    id: 2,
    name: 'Динамометричен ключ',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=DinamKey',
    description: 'Даден на Мартин Стоянов',
  },
  {
    id: 3,
    name: 'Раздвижен ключ',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Adjustable',
    description: 'Даден на Георги Димитров',
  },
  {
    id: 4,
    name: 'Клещи',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Pliers',
    description: 'Даден на Никола Иванов',
  },
  {
    id: 5,
    name: 'Чук',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Hammer',
    description: 'Даден на Милена Николова',
  },
  {
    id: 6,
    name: 'Бормашина',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Drill',
    description: 'Даден на Асен Михайлов',
  },
  {
    id: 7,
    name: 'Ъглошлайф',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Grinder',
    description: 'Даден на Елица Христова',
  },
  {
    id: 8,
    name: 'Кръстата отвертка',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Phillips',
    description: 'Даден на Мария Георгиева',
  },
  {
    id: 9,
    name: 'Поялник',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Solder',
    description: 'Даден на Стефан Тодоров',
  },
  {
    id: 10,
    name: 'Тресчотка',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Ratchet',
    description: 'Даден на Радослав Василев',
  },
  {
    id: 11,
    name: 'Ножовка',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Saw',
    description: 'Даден на Ивелина Стоянова',
  },
  {
    id: 12,
    name: 'Пистолет за горещ въздух',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=HeatGun',
    description: 'Даден на Димитър Коларов',
  },
  {
    id: 13,
    name: 'Такер',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Stapler',
    description: 'Даден на Кристина Маринова',
  },
  {
    id: 14,
    name: 'Мултицет',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=Multimeter',
    description: 'Даден на Ваня Петрова',
  },
  {
    id: 15,
    name: 'Клещи за кабели',
    imageSrc: 'https://via.placeholder.com/100x100.png?text=WireStrips',
    description: 'Даден на Светослав Георгиев',
  },
])


// Filter term
const filterTerm = ref('')

// Computed property for filtered tools
const filteredTools = computed(() => {
  if (!filterTerm.value) return tools.value
  const term = filterTerm.value.toLowerCase()
  return tools.value.filter(tool =>
    tool.name.toLowerCase().includes(term)
  )
})

// Handler: add a new tool
function handleAddTool(newTool) {
  // Generate a new id
  const newId = tools.value.length
    ? Math.max(...tools.value.map(t => t.id)) + 1
    : 1

  tools.value.push({
    id: newId,
    ...newTool
  })
}

// Handler: update filter
function handleFilterChanged(newFilter) {
  filterTerm.value = newFilter
}

// Handler: delete a tool
function handleDeleteTool(toolId) {
  tools.value = tools.value.filter(t => t.id !== toolId)
}
</script>
