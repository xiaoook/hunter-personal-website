<template>
  <section id="about" class="py-20 bg-white">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-4xl font-bold text-center mb-12 text-gray-900">关于我</h2>

      <div class="grid md:grid-cols-2 gap-12 items-center">
        <div class="space-y-6">
          <p class="text-lg text-gray-700 leading-relaxed">
            我是一名充满热情的计算机科学学生，对软件开发和技术创新有着浓厚的兴趣。 目前专注于全栈
            Web 开发、数据结构与算法，以及软件工程实践。
          </p>
          <p class="text-lg text-gray-700 leading-relaxed">
            我相信通过持续学习和实践，可以不断提升自己的技术能力。
            在学习之余，我喜欢参与开源项目，与其他开发者交流分享经验。
          </p>

          <div class="pt-4">
            <h3 class="text-xl font-semibold mb-4 text-gray-900">教育背景</h3>
            <div class="space-y-3">
              <div
                v-for="edu in education"
                :key="edu.school"
                class="bg-gray-50 p-4 rounded-lg"
              >
                <p class="font-semibold text-gray-900">{{ edu.degree }}</p>
                <p class="text-gray-600">{{ edu.school }} | {{ edu.period }}</p>
                <p v-if="edu.gpa" class="text-gray-600 mt-2">GPA: {{ edu.gpa }}</p>
              </div>
            </div>
          </div>
        </div>

        <div class="space-y-6">
          <div class="bg-gradient-to-br from-blue-50 to-purple-50 p-8 rounded-xl">
            <h3 class="text-xl font-semibold mb-4 text-gray-900">兴趣方向</h3>
            <ul class="space-y-3">
              <li
                v-for="interest in interests"
                :key="interest"
                class="flex items-center text-gray-700"
              >
                <svg class="w-5 h-5 text-blue-600 mr-3" fill="currentColor" viewBox="0 0 20 20">
                  <path
                    fill-rule="evenodd"
                    d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                    clip-rule="evenodd"
                  />
                </svg>
                {{ interest }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const education = [
  {
    degree: '计算机科学 学士',
    school: '宁波诺丁汉大学',
    period: '2023 - 2027',
    gpa: '3.8/4.0',
  },
  // 可以在这里添加更多教育经历
  // {
  //   degree: '硕士学位',
  //   school: '学校名称',
  //   period: '年份',
  //   gpa: '可选',
  // },
]

const interests = [
  '全栈 Web 开发',
  '算法设计与优化',
  '开源项目贡献',
  '机器学习基础',
  '物联网与智能家居',
]
</script>
