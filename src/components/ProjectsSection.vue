<template>
  <section id="projects" class="py-20 bg-gray-50">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-4xl font-bold text-center mb-4 text-gray-900">项目作品</h2>
      <p class="text-center text-gray-600 mb-12">这里是我的一些代表性项目</p>
      <!-- 加载状态 -->
      <div v-if="loading" class="text-center py-12">
        <div class="inline-block animate-spin rounded-full h-12 w-12 border-b-2 border-blue-600"></div>
        <p class="mt-4 text-gray-600">正在加载项目...</p>
      </div>

      <!-- 错误状态 -->
      <div v-else-if="error" class="text-center py-12">
        <p class="text-red-600">{{ error }}</p>
        <button
          @click="fetchProjects"
          class="mt-4 px-6 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors"
        >
          重试
        </button>
      </div>

      <!-- 项目列表 -->
      <div v-else class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="project in displayProjects"
          :key="project.name"
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
            <h3 class="text-xl font-bold mb-2 text-gray-900">{{ project.displayName }}</h3>
            <p class="text-gray-600 mb-4 line-clamp-2">
              {{ project.description || '暂无描述' }}
            </p>

            <!-- GitHub 数据 -->
            <div class="flex gap-4 mb-4 text-sm text-gray-600">
              <div class="flex items-center gap-1" v-if="project.stars !== undefined">
                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 20 20">
                  <path
                    d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"
                  />
                </svg>
                {{ project.stars }}
              </div>
              <div class="flex items-center gap-1" v-if="project.forks !== undefined">
                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 16 16">
                  <path
                    d="M5 3.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm0 2.122a2.25 2.25 0 10-1.5 0v.878A2.25 2.25 0 005.75 8.5h1.5v2.128a2.251 2.251 0 101.5 0V8.5h1.5a2.25 2.25 0 002.25-2.25v-.878a2.25 2.25 0 10-1.5 0v.878a.75.75 0 01-.75.75h-4.5A.75.75 0 015 6.25v-.878zm3.75 7.378a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm3-8.75a.75.75 0 100-1.5.75.75 0 000 1.5z"
                  />
                </svg>
                {{ project.forks }}
              </div>
            </div>

            <!-- 技术栈 -->
            <div class="flex flex-wrap gap-2 mb-4" v-if="project.topics && project.topics.length > 0">
              <span
                v-for="tech in project.topics.slice(0, 4)"
                :key="tech"
                class="px-3 py-1 bg-blue-100 text-blue-700 text-sm rounded-full"
              >
                {{ tech }}
              </span>
            </div>
            <div v-else-if="project.language" class="mb-4">
              <span class="px-3 py-1 bg-blue-100 text-blue-700 text-sm rounded-full">
                {{ project.language }}
              </span>
            </div>

            <div class="flex gap-4">
              <a
                :href="project.html_url"
                target="_blank"
                rel="noopener noreferrer"
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
                v-if="project.homepage"
                :href="project.homepage"
                target="_blank"
                rel="noopener noreferrer"
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
import { ref, onMounted, computed } from 'vue'

interface GitHubRepo {
  name: string
  displayName: string
  description: string
  html_url: string
  homepage: string | null
  language: string | null
  stargazers_count: number
  forks_count: number
  topics: string[]
  icon: string
  gradient: string
  stars?: number
  forks?: number
}

// 从环境变量读取配置
const GITHUB_USERNAME = import.meta.env.VITE_GITHUB_USERNAME || ''
const FEATURED_REPOS = import.meta.env.VITE_FEATURED_REPOS
  ? import.meta.env.VITE_FEATURED_REPOS.split(',').map((repo: string) => repo.trim()).filter(Boolean)
  : []

const projects = ref<GitHubRepo[]>([])
const loading = ref(false)
const error = ref('')

// 为不同类型的项目分配图标和渐变色
const getProjectStyle = (repo: GitHubRepo | any, index: number) => {
  const styles = [
    { icon: '💻', gradient: 'from-blue-400 to-blue-600' },
    { icon: '🚀', gradient: 'from-green-400 to-green-600' },
    { icon: '📱', gradient: 'from-purple-400 to-purple-600' },
    { icon: '🎨', gradient: 'from-cyan-400 to-cyan-600' },
    { icon: '🔧', gradient: 'from-orange-400 to-orange-600' },
    { icon: '⚡', gradient: 'from-pink-400 to-pink-600' },
  ]

  // 根据语言或索引选择样式
  return styles[index % styles.length]
}

const fetchProjects = async () => {
  loading.value = true
  error.value = ''

  // 检查是否配置了 GitHub 用户名
  if (!GITHUB_USERNAME) {
    error.value = '请在 .env 文件中配置 VITE_GITHUB_USERNAME'
    loading.value = false
    return
  }

  try {
    let repos = []

    if (FEATURED_REPOS.length > 0) {
      // 获取指定的仓库（支持 owner/repo 格式）
      const promises = FEATURED_REPOS.map((repoPath: string) => {
        // 支持 "org/repo" 或 "repo" 格式
        const [owner, repo] = repoPath.includes('/')
          ? repoPath.split('/')
          : [GITHUB_USERNAME, repoPath]

        return fetch(`https://api.github.com/repos/${owner}/${repo}`).then((res) =>
          res.json()
        )
      })
      repos = await Promise.all(promises)
    } else {
      // 获取所有公开仓库，按星标排序
      const response = await fetch(
        `https://api.github.com/users/${GITHUB_USERNAME}/repos?sort=stars&per_page=6`
      )
      repos = await response.json()
    }

    if (repos.message) {
      throw new Error(repos.message)
    }

    projects.value = repos.map((repo: GitHubRepo | any, index: number) => {
      const style = getProjectStyle(repo, index)
      return {
        name: repo.name,
        displayName: repo.name
          .split('-')
          .map((word: string) => word.charAt(0).toUpperCase() + word.slice(1))
          .join(' '),
        description: repo.description,
        html_url: repo.html_url,
        homepage: repo.homepage,
        language: repo.language,
        stars: repo.stargazers_count,
        forks: repo.forks_count,
        topics: repo.topics || [],
        ...style,
      }
    })
  } catch (err) {
    error.value = (err as Error).message || '加载项目失败，请稍后重试'
    console.error('获取 GitHub 项目失败:', err)
  } finally {
    loading.value = false
  }
}

const displayProjects = computed(() => projects.value)

onMounted(() => {
  fetchProjects()
})
</script>

<style scoped>
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>
