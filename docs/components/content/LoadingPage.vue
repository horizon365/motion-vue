<script setup lang="tsx">
import { motion } from 'motion-v'
import { slideUp } from '@/lib/motion'

const links = [
  { text: 'Documentation', href: '#' },
  { text: 'Examples', href: '#' },
  { text: 'Showcase', href: '#' },
  { text: 'GitHub', href: '#' },
]

const features = [
  {
    icon: <Icon name="lucide:wand" />,
    title: 'Declarative Animations',
    description: '简洁的声明式语法，用于复杂动画。使用 Vue 模板定义动画，无需 imperative 代码。',
  },
  {
    icon: <Icon name="lucide:layout-grid" />,
    title: 'Layout Animations',
    description: '强大的 FLIP 动画，实现平滑的布局过渡和共享元素动画。',
  },
  {
    icon: <Icon name="lucide:hand" />,
    title: 'Gesture Controls',
    description: '丰富的手势系统，支持拖动、平移、悬停和按压交互，具有弹簧物理效果。',
  },
  {
    icon: <Icon name="lucide:box" />,
    title: 'Motion Values',
    description: '可变换、组合和弹簧动画的动态动画值。',
  },
]

const floatingItems = [
  {
    class: 'w-8 h-8 rounded bg-green-500/20',
    style: { top: '15%', left: '10%', animationDelay: '0s' },
  },
  {
    class: 'w-12 h-12 rounded-full bg-blue-500/20',
    style: { top: '25%', right: '15%', animationDelay: '0.5s' },
  },
  {
    class: 'w-6 h-6 rounded-full bg-yellow-500/20',
    style: { bottom: '20%', left: '20%', animationDelay: '1s' },
  },
  {
    class: 'w-10 h-10 rounded bg-purple-500/20',
    style: { bottom: '30%', right: '25%', animationDelay: '1.5s' },
  },
]
</script>

<template>
  <div class="min-h-screen bg-background">
    <!-- Hero Section -->
    <div class="relative pt-32 pb-20 sm:pt-40 sm:pb-24">
      <!-- Main Content -->
      <motion.div
        initial="hidden"
        in-view="visible"
        :transition="{
          staggerChildren: 0.2,
        }"
        :in-view-options="{ once: true }"
        class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8"
      >
        <div class="text-center">
          <motion.h1
            v-bind="slideUp"
            class="text-5xl md:text-7xl font-bold text-foreground mb-6 "
          >
            Motion for
            <span class="text-green-500">Vue.</span>
          </motion.h1>
          <motion.p
            v-bind="slideUp"
            class="max-w-2xl mx-auto text-xl text-muted-foreground mb-10 "
          >
            构建基于 Vue.js 的美丽动态界面，基于 <a
              href="https://www.framer.com/motion/"
              target="_blank"
              class="text-primary hover:underline"
            >motion</a>.
            简单、强大且性能优异的动画，适用于现代网络应用程序。
          </motion.p>
          <motion.div
            v-bind="slideUp"
            class="flex justify-center space-x-4 "
          >
            <UiButton
              size="lg"
              class="rounded-full text-primary-foreground"
              as="a"
              href="/getting-started"
            >
              Get Started
            </UiButton>
            <UiButton
              variant="outline"
              class="rounded-full"
              size="lg"
              as="a"
              href="https://github.com/motiondivision/motion-vue"
              target="_blank"
            >
              <Icon
                name="uil:github"
                class="w-5 h-5"
              />
              GitHub
            </UiButton>
          </motion.div>
        </div>
      </motion.div>
    </div>

    <!-- Features Grid -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20">
      <motion.div
        class="grid md:grid-cols-4 gap-8"
        initial="hidden"
        in-view="visible"
        :transition="{
          delayChildren: 0.2,
          staggerChildren: 0.1,
        }"
      >
        <motion.div
          v-for="feature in features"
          :key="feature.title"
          v-bind="slideUp"
          class="p-6 rounded-xl hover:bg-primary/5 transition-colors"
        >
          <div class="w-12 h-12 rounded-lg bg-primary/10 flex items-center justify-center mb-4">
            <component
              :is="feature.icon"
              class="w-6 h-6 text-primary"
            />
          </div>
          <h3 class="text-xl font-semibold mb-2">
            {{ feature.title }}
          </h3>
          <p class="text-muted-foreground">
            {{ feature.description }}
          </p>
        </motion.div>
      </motion.div>
    </div>
  </div>
</template>
