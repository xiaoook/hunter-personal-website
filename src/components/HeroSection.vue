<template>
  <section
    id="hero"
    class="min-h-screen flex items-center justify-center bg-gradient-to-br from-blue-50 via-white to-purple-50 pt-16"
  >
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-20 text-center">
      <div class="animate-fade-in">
        <h1 class="text-5xl sm:text-6xl md:text-7xl font-bold text-gray-900 mb-6">
          你好，我是
          <span class="bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
            Hunter
          </span>
        </h1>
        <p class="text-xl sm:text-2xl text-gray-600 mb-8 max-w-2xl mx-auto">
          计算机科学学生 | 全栈开发者 | 技术爱好者
        </p>
        <p class="text-lg text-gray-500 mb-12 max-w-3xl mx-auto">
          宁诺大三计算机在读学生，热爱编程、智能家居和游戏。
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <a
            href="#projects"
            class="px-8 py-3 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-all duration-200 shadow-lg hover:shadow-xl"
          >
            查看项目
          </a>
          <a
            href="#contact"
            class="px-8 py-3 bg-white text-blue-600 border-2 border-blue-600 rounded-lg hover:bg-blue-50 transition-all duration-200"
          >
            联系我
          </a>
        </div>
      </div>

      <!-- Scroll Indicator -->
      <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
        <svg class="w-6 h-6 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M19 14l-7 7m0 0l-7-7m7 7V3"
          />
        </svg>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts"></script>

<style scoped>
@keyframes fade-in {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in {
  animation: fade-in 1s ease-out;
}
</style>
