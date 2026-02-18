<template>
  <nav class="fixed top-0 left-0 right-0 bg-white/80 backdrop-blur-md z-50 shadow-sm">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <a href="#" class="text-xl font-bold text-gray-900">Hunter</a>

        <!-- Desktop Menu -->
        <div class="hidden md:flex space-x-8">
          <a
            v-for="item in menuItems"
            :key="item.name"
            :href="item.href"
            class="text-gray-700 hover:text-blue-600 transition-colors duration-200"
          >
            {{ item.name }}
          </a>
        </div>

        <!-- Mobile Menu Button -->
        <button @click="mobileMenuOpen = !mobileMenuOpen" class="md:hidden">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              :d="mobileMenuOpen ? 'M6 18L18 6M6 6l12 12' : 'M4 6h16M4 12h16M4 18h16'"
            />
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <div v-if="mobileMenuOpen" class="md:hidden pb-4">
        <a
          v-for="item in menuItems"
          :key="item.name"
          :href="item.href"
          @click="mobileMenuOpen = false"
          class="block py-2 text-gray-700 hover:text-blue-600 transition-colors duration-200"
        >
          {{ item.name }}
        </a>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const mobileMenuOpen = ref(false)

const menuItems = [
  { name: '首页', href: '#hero' },
  { name: '关于', href: '#about' },
  { name: '项目', href: '#projects' },
  { name: '技能', href: '#skills' },
  { name: '联系', href: '#contact' },
]
</script>
