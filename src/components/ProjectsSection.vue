<template>
  <section id="projects" class="py-20 bg-gray-50">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-4xl font-bold text-center mb-4 text-gray-900">项目作品</h2>
      <p class="text-center text-gray-600 mb-12">这里是我的一些代表性项目</p>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="project in projects"
          :key="project.title"
          class="bg-white rounded-xl shadow-md hover:shadow-xl transition-shadow duration-300 overflow-hidden group"
        >
          <div class="h-48 bg-gradient-to-br overflow-hidden" :class="project.gradient">
            <div
              class="w-full h-full flex items-center justify-center text-white text-6xl font-bold opacity-20 group-hover:opacity-30 transition-opacity"
            >
              {{ project.icon }}
            </div>
          </div>

          <div class="p-6">
            <h3 class="text-xl font-bold mb-2 text-gray-900">{{ project.title }}</h3>
            <p class="text-gray-600 mb-4">{{ project.description }}</p>

            <div class="flex flex-wrap gap-2 mb-4">
              <span
                v-for="tech in project.technologies"
                :key="tech"
                class="px-3 py-1 bg-blue-100 text-blue-700 text-sm rounded-full"
              >
                {{ tech }}
              </span>
            </div>

            <div class="flex gap-4">
              <a
                :href="project.github"
                class="text-blue-600 hover:text-blue-800 flex items-center gap-1"
              >
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                  <path
                    d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                  />
                </svg>
                GitHub
              </a>
              <a
                v-if="project.demo"
                :href="project.demo"
                class="text-green-600 hover:text-green-800 flex items-center gap-1"
              >
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"
                  />
                </svg>
                演示
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const projects = [
  {
    title: '个人博客系统',
    description: '基于 Vue 3 和 Node.js 开发的全栈博客平台，支持 Markdown 编辑和评论功能。',
    technologies: ['Vue 3', 'Node.js', 'MongoDB'],
    github: '#',
    demo: '#',
    icon: '📝',
    gradient: 'from-blue-400 to-blue-600',
  },
  {
    title: '任务管理工具',
    description: '一个高效的任务管理应用，支持项目协作、时间跟踪和数据可视化。',
    technologies: ['React', 'TypeScript', 'Firebase'],
    github: '#',
    demo: '#',
    icon: '✓',
    gradient: 'from-green-400 to-green-600',
  },
  {
    title: '算法可视化平台',
    description: '直观展示常见算法运行过程的教育性工具，帮助理解数据结构和算法。',
    technologies: ['JavaScript', 'Canvas', 'D3.js'],
    github: '#',
    demo: '#',
    icon: '🔍',
    gradient: 'from-purple-400 to-purple-600',
  },
  {
    title: '天气预报应用',
    description: '集成第三方 API 的天气预报应用，提供实时天气和未来预报信息。',
    technologies: ['Vue', 'Tailwind', 'API'],
    github: '#',
    demo: null,
    icon: '☁️',
    gradient: 'from-cyan-400 to-cyan-600',
  },
  {
    title: 'E-commerce 前端',
    description: '现代化的电商前端界面，包含商品展示、购物车和支付流程。',
    technologies: ['Next.js', 'Stripe', 'Redux'],
    github: '#',
    demo: '#',
    icon: '🛒',
    gradient: 'from-orange-400 to-orange-600',
  },
  {
    title: 'AI 聊天助手',
    description: '集成 AI 的智能聊天机器人，支持自然语言对话和上下文理解。',
    technologies: ['Python', 'OpenAI', 'FastAPI'],
    github: '#',
    demo: null,
    icon: '🤖',
    gradient: 'from-pink-400 to-pink-600',
  },
]
</script>
