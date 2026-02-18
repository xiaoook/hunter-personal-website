<template>
  <section id="contact" class="py-20 bg-gray-50">
    <div class="max-w-2xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-4xl font-bold text-center mb-4 text-gray-900">联系我</h2>
      <p class="text-center text-gray-600 mb-12">很高兴能与你交流，欢迎随时联系我！</p>

      <!-- Contact Form -->
      <div class="bg-white p-8 rounded-xl shadow-lg">
        <form v-if="formspreeId" :action="formspreeUrl" method="POST" class="space-y-6">
          <div>
            <label for="name" class="block text-sm font-medium text-gray-700 mb-2">姓名</label>
            <input
              id="name"
              name="name"
              type="text"
              required
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none transition"
              placeholder="请输入您的姓名"
            />
          </div>
          <div>
            <label for="email" class="block text-sm font-medium text-gray-700 mb-2">邮箱</label>
            <input
              id="email"
              name="email"
              type="email"
              required
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none transition"
              placeholder="your@email.com"
            />
          </div>
          <div>
            <label for="message" class="block text-sm font-medium text-gray-700 mb-2"
              >消息</label
            >
            <textarea
              id="message"
              name="message"
              rows="5"
              required
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none transition resize-none"
              placeholder="请输入您的消息..."
            ></textarea>
          </div>
          <button
            type="submit"
            class="w-full px-6 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors font-medium text-lg shadow-md hover:shadow-lg"
          >
            发送消息
          </button>
        </form>

        <!-- 未配置提示 -->
        <div v-else class="text-center py-8">
          <p class="text-gray-600 mb-4">表单服务未配置</p>
          <p class="text-sm text-gray-500">
            请在 .env 文件中配置 VITE_FORMSPREE_ID 以启用联系表单
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue'

// 从环境变量读取 Formspree ID
const formspreeId = import.meta.env.VITE_FORMSPREE_ID || ''
const formspreeUrl = computed(() => `https://formspree.io/f/${formspreeId}`)
</script>
