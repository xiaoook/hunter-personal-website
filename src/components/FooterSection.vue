<template>
  <footer class="bg-gray-900 text-white py-8">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex flex-col md:flex-row justify-between items-center">
        <div class="mb-4 md:mb-0">
          <p class="text-gray-400">&copy; {{ currentYear }} Hunter. All rights reserved.</p>
        </div>

        <div class="flex gap-6">
          <a href="#hero" class="text-gray-400 hover:text-white transition-colors">首页</a>
          <a href="#about" class="text-gray-400 hover:text-white transition-colors">关于</a>
          <a href="#projects" class="text-gray-400 hover:text-white transition-colors">项目</a>
          <a href="#contact" class="text-gray-400 hover:text-white transition-colors">联系</a>
        </div>
      </div>

      <div class="mt-4 text-center text-gray-500 text-sm">
        <p>Built with ❤️ using Vue 3 & Tailwind CSS</p>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
import { computed } from 'vue'

const currentYear = computed(() => new Date().getFullYear())
</script>
