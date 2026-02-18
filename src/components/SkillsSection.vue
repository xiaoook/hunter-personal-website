<template>
  <section id="skills" class="py-20 bg-white">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-4xl font-bold text-center mb-4 text-gray-900">技能专长</h2>
      <p class="text-center text-gray-600 mb-12">我掌握的技术栈和工具</p>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="category in skillCategories"
          :key="category.name"
          class="bg-gradient-to-br from-gray-50 to-white p-6 rounded-xl shadow-md hover:shadow-xl transition-all duration-300 border border-gray-100"
        >
          <div class="flex items-center mb-6">
            <div
              class="w-12 h-12 rounded-full flex items-center justify-center text-2xl mr-4"
              :class="category.bgColor"
            >
              {{ category.icon }}
            </div>
            <h3 class="text-xl font-semibold text-gray-900">{{ category.name }}</h3>
          </div>

          <div class="flex flex-wrap gap-2">
            <span
              v-for="skill in category.skills"
              :key="skill"
              class="px-3 py-1.5 text-sm font-medium rounded-full transition-all duration-200 hover:scale-105"
              :class="category.skillStyle"
            >
              {{ skill }}
            </span>
          </div>
        </div>
      </div>

      <!-- Additional Tools -->
      <div class="mt-16">
        <h3 class="text-2xl font-bold text-center mb-8 text-gray-900">开发工具 & 环境</h3>
        <div class="flex flex-wrap justify-center gap-4">
          <span
            v-for="tool in tools"
            :key="tool"
            class="px-6 py-3 bg-gradient-to-r from-gray-50 to-gray-100 text-gray-700 rounded-lg hover:from-gray-100 hover:to-gray-200 transition-all duration-200 font-medium shadow-sm hover:shadow-md"
          >
            {{ tool }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const skillCategories = [
  {
    name: '编程语言',
    icon: '💻',
    bgColor: 'bg-blue-100',
    skillStyle: 'bg-blue-100 text-blue-700 hover:bg-blue-200',
    skills: ['C/C++', 'Python', 'Java', 'Golang (学习中)'],
  },
  {
    name: '后端开发',
    icon: '⚙️',
    bgColor: 'bg-green-100',
    skillStyle: 'bg-green-100 text-green-700 hover:bg-green-200',
    skills: ['Flask', 'RESTful API', 'Web 开发', 'API 设计'],
  },
  {
    name: '数据库',
    icon: '🗄️',
    bgColor: 'bg-purple-100',
    skillStyle: 'bg-purple-100 text-purple-700 hover:bg-purple-200',
    skills: ['PostgreSQL', 'SQLite', 'SQL 查询', '数据库设计'],
  },
  {
    name: 'DevOps & 工具',
    icon: '🔧',
    bgColor: 'bg-orange-100',
    skillStyle: 'bg-orange-100 text-orange-700 hover:bg-orange-200',
    skills: ['Git/GitHub', 'Docker', 'Linux', 'CI/CD'],
  },
  {
    name: '系统编程',
    icon: '🖥️',
    bgColor: 'bg-cyan-100',
    skillStyle: 'bg-cyan-100 text-cyan-700 hover:bg-cyan-200',
    skills: ['C 语言编程', '内存管理', '数据结构', '算法设计'],
  },
  {
    name: '软件工程',
    icon: '📐',
    bgColor: 'bg-pink-100',
    skillStyle: 'bg-pink-100 text-pink-700 hover:bg-pink-200',
    skills: ['版本控制', '代码规范', '问题解决', '项目管理'],
  },
]

const tools = [
  'VS Code',
  'IntelliJ IDEA',
  'Git',
  'Docker',
  'PostgreSQL',
  'SQLite',
  'Postman',
  'Linux',
  'GCC/Clang',
]
</script>
