<template>
  <a
    :href="link.url"
    target="_blank"
    rel="noopener noreferrer"
    class="flex items-center justify-between w-full px-5 py-4 bg-white dark:bg-gray-800 rounded-xl shadow-sm border border-gray-200 dark:border-gray-700 hover:shadow-md hover:border-blue-300 dark:hover:border-blue-600 transition group"
  >
    <div class="flex flex-col gap-1">
      <span
        class="text-lg font-semibold text-gray-900 dark:text-white group-hover:text-blue-600 dark:group-hover:text-blue-400 transition"
      >
        {{ link.title }}
      </span>
      <span class="text-sm text-gray-500 dark:text-gray-400">{{ link.description }}</span>
    </div>
    <div
      class="text-gray-400 dark:text-gray-500 group-hover:text-blue-600 dark:group-hover:text-blue-400 transition"
    >
      <ChevronRight class="w-5 h-5" />
    </div>
  </a>
</template>

<script setup lang="ts">
import { ChevronRight } from 'lucide-vue-next'

interface LinkItem {
  id: number
  title: string
  url: string
  description: string
}

defineProps<{
  link: LinkItem
}>()
</script>
