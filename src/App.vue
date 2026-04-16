<template>
  <div
    class="min-h-screen flex flex-col bg-gray-50 dark:bg-gray-900 transition-colors duration-300"
  >
    <!-- 可选的顶部占位（主题切换按钮放这里） -->
    <header class="sticky top-0 z-50 bg-white/80 dark:bg-gray-800/80 backdrop-blur-sm shadow-sm">
      <div class="container mx-auto px-4 py-3 flex justify-end">
        <button
          @click="toggleDark"
          class="p-2 rounded-full bg-gray-100 dark:bg-gray-700 text-gray-700 dark:text-gray-300 hover:bg-gray-200 dark:hover:bg-gray-600 transition"
        >
          <!-- 图标用 lucide-vue-next，稍后引入 -->
          <Sun v-if="isDark" class="w-5 h-5" />
          <Moon v-else class="w-5 h-5" />
        </button>
      </div>
    </header>

    <!-- 主角栏：个人链接内容 -->
    <main class="flex-1 container mx-auto px-4 py-8 flex items-center justify-center">
      <RouterView />
    </main>

    <!-- 底部版权 -->
    <footer class="py-6 text-center text-sm text-gray-500 dark:text-gray-400">
      <p>© {{ currentYear }} SparkLink · MQY的网络名片</p>
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
