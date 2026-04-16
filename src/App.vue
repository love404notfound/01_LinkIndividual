<template>
  <div
    class="min-h-screen flex flex-col bg-gray-50 dark:bg-gray-900 transition-colors duration-300"
  >
    <!-- 顶部占位放置主题切换按键 -->
    <header class="sticky top-0 z-50 bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm shadow-sm">
      <div class="container mx-auto px-4 py-3 flex justify-end">
        <button
          @click="toggleDark"
          class="p-2 rounded-full bg-gray-100 dark:bg-gray-700 text-gray-700 dark:text-gray-300 hover:bg-gray-200 dark:hover:bg-gray-600 transition"
        >
          <Sun v-if="isDark" class="w-5 h-5" />
          <Moon v-else class="w-5 h-5" />
        </button>
      </div>
    </header>

    <!-- 主角栏：使用占位符顶替 -->
    <main class="flex-1 container mx-auto px-4 py-8 flex items-center justify-center">
      <RouterView />
    </main>

    <!-- 底部版权 -->
    <footer class="py-6 text-center text-sm text-gray-500 dark:text-gray-400">
      <p>© {{ currentYear }} LinkIndividual · MQY的网络名片</p>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import { Sun, Moon } from 'lucide-vue-next'

const isDark = ref(false)

const toggleDark = () => {
  isDark.value = !isDark.value
  document.documentElement.classList.toggle('dark', isDark.value)
}

const currentYear = computed(() => new Date().getFullYear())
</script>
