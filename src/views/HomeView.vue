<template>
  <div class="max-w-md w-full mx-auto">
    <!-- 头像 + 简介 -->
    <div class="flex flex-col items-center mb-8">
      <img
        src="../assets/avatar.jpg"
        alt="头像"
        class="w-28 h-28 rounded-full object-cover border-4 border-white dark:border-gray-800 shadow-lg mb-4"
      />
      <h1 class="text-2xl font-bold text-gray-900 dark:text-white mb-1">MQY</h1>
      <p class="text-gray-600 dark:text-gray-400 text-center">前端开发者 · 正在构建我的网络名片</p>
    </div>

    <!-- 创建的LinkButton组件修饰a标签 -->
    <div class="flex flex-col gap-3">
      <LinkButton v-for="link in links" :key="link.id" :link="link" />
    </div>

    <div class="flex justify-center gap-4 mt-8">
      <a
        v-for="social in socials"
        :key="social.id"
        :href="social.url"
        target="_blank"
        class="p-3 rounded-full bg-gray-100 dark:bg-gray-800 text-gray-700 dark:text-gray-300 hover:bg-gray-200 dark:hover:bg-gray-700 transition"
        :aria-label="social.name"
        @click.prevent="handleSocialClick(social)"
      >
        <component :is="social.icon" class="w-5 h-5" />
      </a>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Github, Twitter, Mail, type LucideIcon } from 'lucide-vue-next'
import LinkButton from '../components/LinkButton.vue'

// 定义社交账号的类型
interface SocialItem {
  id: number
  name: string
  url: string
  enabled: boolean
  icon: LucideIcon
}

// 定义链接按钮的类型
interface LinkItem {
  id: number
  title: string
  url: string
  description: string
}

const links: LinkItem[] = [
  { id: 1, title: '个人博客', url: '#', description: '技术笔记与生活随想' },
  {
    id: 2,
    title: 'B站',
    url: 'https://space.bilibili.com/3546905212619476',
    description: '很高兴认识你',
  },
  {
    id: 3,
    title: 'GitHub',
    url: 'https://github.com/love404notfound',
    description: '我的开源项目',
  },
  {
    id: 4,
    title: '小红书',
    url: 'https://www.xiaohongshu.com/user/profile/68e687990000000037008389',
    description: '生活与摄影记录',
  },
]

const socials: SocialItem[] = [
  { id: 1, name: 'GitHub', url: 'https://github.com/love404notfound', enabled: true, icon: Github },
  { id: 2, name: 'Twitter', url: '', enabled: false, icon: Twitter },
  { id: 3, name: 'Email', url: 'mailto:13975952132@163.com', enabled: true, icon: Mail },
]

const handleSocialClick = (social: SocialItem): void => {
  if (social.enabled) {
    window.open(social.url, '_blank')
  } else {
    alert(`博主暂时没有${social.name}账号，欢迎通过其他方式联系～`)
  }
}
</script>
