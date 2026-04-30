<script setup lang="ts">
import { ref } from 'vue'
import headLogo from './assets/imgs/head_logo.png'
import heroLogo from './assets/imgs/logo-stand600.png'
import footerLogo from './assets/imgs/logo-stand120.png'
import microIcon from './assets/svgs/micro.svg'
import iconDownload from './assets/svgs/icon-setting.svg'
import iconSkills from './assets/svgs/icon-skills.svg'
import iconMemory from './assets/svgs/icon-momery.svg'
import iconLocal from './assets/svgs/icon-loak.svg'
import stepDownload from './assets/svgs/icon-downfiles.svg'
import stepLink from './assets/svgs/icon-link.svg'
import stepComputer from './assets/svgs/icon-com.svg'
import sceneMeeting from './assets/imgs/image_scene1.png'
import sceneTrip from './assets/imgs/image_scene2.png'
import sceneDecision from './assets/imgs/image_scene.png'
import sceneOps from './assets/imgs/image_scene4.png'

const downloadUrl = 'http://qub.ai.fj.cmcc:48801/devbucket/fxx-install/fxz-Setup.exe'

const navItems = [
  { label: '功能优势', target: 'advantages' },
  { label: '快速上手', target: 'quick-start' },
  { label: '使用场景', target: 'scenarios' },
]

const featureCards = [
  {
    title: '自动部署，开箱即用',
    description: '支持 Windows 客户端，预置优质模型能力，安装完成后即可直接体验。',
    tag: '开箱即用',
    icon: iconDownload,
    tone: 'blue',
  },
  {
    title: '丰富 Skills 生态',
    description: '支持多种 Skill 扩展能力，覆盖检索、协作、办公等高频场景。',
    tag: '能力丰富',
    icon: iconSkills,
    tone: 'gold',
  },
  {
    title: '持续记忆，你的专属福小智',
    description: '能够记住偏好和上下文，随着使用不断成长，回应更贴近你的习惯。',
    tag: '智能升级',
    icon: iconMemory,
    tone: 'orange',
  },
  {
    title: '本地部署，办公更高效',
    description: '可协助处理文件、浏览器和日常任务，不只是简单对话，而是真正的桌面助手。',
    tag: '高效办公',
    icon: iconLocal,
    tone: 'green',
  },
]

const quickSteps = [
  {
    title: '下载安装',
    description: '下载 Windows 安装包，一键安装即可使用。',
    icon: stepDownload,
    accent: 'blue',
  },
  {
    title: '短信验证码登录',
    description: '绑定手机号完成登录，快速建立专属身份。',
    icon: stepLink,
    accent: 'indigo',
  },
  {
    title: '电脑端发指令立即开干',
    description: '登录客户端后直接下达任务，福小智即可开始协助。',
    icon: stepComputer,
    accent: 'violet',
  },
]

const scenarioCards = [
  {
    label: '日常办公',
    title: '会议纪要整理',
    description: '自动整理会议内容、提炼重点和待办事项，减少重复记录与归档成本。',
    image: sceneMeeting,
  },
  {
    label: '出行规划',
    title: '出行规划',
    description: '帮助安排行程、整理方案和信息要点，让出差与日常出行更省心。',
    image: sceneTrip,
  },
  {
    label: '项目管理',
    title: '项目管理决策',
    description: '支持方案整理、任务拆解和信息汇总，为管理与决策提供清晰参考。',
    image: sceneDecision,
  },
  {
    label: '生产运维',
    title: '生产运维',
    description: '结合行业流程沉淀专属能力模板，协助处理更贴近业务的一线事务。',
    image: sceneOps,
  },
]

const activeNav = ref('advantages')

function scrollToSection(target: string) {
  activeNav.value = target
  const section = document.getElementById(target)

  if (!section) return

  const offsetTop = section.getBoundingClientRect().top + window.scrollY - 92
  window.scrollTo({ top: offsetTop, behavior: 'smooth' })
}

function handleDownload() {
  window.open(downloadUrl, '_blank', 'noopener')
}
</script>

<template>
  <div class="page-shell">
    <header class="site-header">
      <div class="brand-block">
        <img class="brand-mark" :src="headLogo" alt="福小智" />
        <span class="brand-text">福小智</span>
      </div>

      <nav class="site-nav" aria-label="页面导航">
        <button
          v-for="item in navItems"
          :key="item.target"
          :class="['nav-link', { active: activeNav === item.target }]"
          type="button"
          @click="scrollToSection(item.target)"
        >
          {{ item.label }}
        </button>
      </nav>

      <button class="download-button" type="button" @click="handleDownload">立即下载</button>
    </header>

    <main class="page-main">
      <section class="hero-section">
        <div class="hero-orb hero-orb-left"></div>
        <div class="hero-orb hero-orb-right"></div>

        <div class="hero-visual">
          <img :src="heroLogo" alt="福小智角色形象" />
        </div>

        <div class="hero-copy">
          <h1 class="hero-title">福小智</h1>
          <p class="hero-subtitle">随时随地，唤起你的桌面 AI 助手</p>

          <button class="hero-download" type="button" @click="handleDownload">
            <img :src="microIcon" alt="" />
            <span>Windows 版本安装包</span>
          </button>
        </div>

        <div id="advantages" class="feature-grid">
          <article
            v-for="card in featureCards"
            :key="card.title"
            :class="['feature-card', `feature-card--${card.tone}`]"
          >
            <div class="feature-card__icon">
              <img :src="card.icon" :alt="card.title" />
            </div>
            <h3>{{ card.title }}</h3>
            <p>{{ card.description }}</p>
            <span class="feature-card__tag">{{ card.tag }}</span>
          </article>
        </div>
      </section>

      <section id="quick-start" class="content-section">
        <div class="section-heading">
          <p class="section-kicker">HOW IT WORKS</p>
          <h2>几分钟即可上手</h2>
          <p class="section-desc">从下载到开始咨询，几分钟即可以开始使用。</p>
        </div>

        <div class="step-grid">
          <article
            v-for="(step, index) in quickSteps"
            :key="step.title"
            :class="['step-card', `step-card--${step.accent}`]"
          >
            <div class="step-icon">
              <img :src="step.icon" :alt="step.title" />
            </div>
            <div class="step-index">0{{ index + 1 }}</div>
            <h3>{{ step.title }}</h3>
            <p>{{ step.description }}</p>
          </article>
        </div>
      </section>

      <section id="scenarios" class="content-section content-section--scenes">
        <div class="section-heading">
          <p class="section-kicker">USE CASES</p>
          <h2>真实场景，随时体验</h2>
          <p class="section-desc">从日常办公到专业服务，福小智能够陪你处理各种任务。</p>
        </div>

        <div class="scene-grid">
          <article v-for="card in scenarioCards" :key="card.title" class="scene-card">
            <div class="scene-card__image">
              <img :src="card.image" :alt="card.title" />
              <span class="scene-card__label">{{ card.label }}</span>
            </div>
            <div class="scene-card__body">
              <h3>{{ card.title }}</h3>
              <p>{{ card.description }}</p>
            </div>
          </article>
        </div>
      </section>

      <section class="footer-cta">
        <img class="footer-cta__logo" :src="footerLogo" alt="福小智" />
        <h2>福小智</h2>
        <p>随时随地，唤起你的桌面 AI 助手</p>
        <button class="hero-download hero-download--small" type="button" @click="handleDownload">
          <img :src="microIcon" alt="" />
          <span>Windows 版本安装包</span>
        </button>
      </section>

      <footer class="site-footer">
        <div class="site-footer__brand">
          <img :src="headLogo" alt="福小智" />
          <span>福小智</span>
        </div>
        <p>Copyright © 2025 - 2026 FUXIAOZHI All Rights Reserved.</p>
        <div class="site-footer__links">
          <a href="javascript:void(0)">福小智</a>
          <span>|</span>
          <a href="javascript:void(0)">版权所有</a>
          <span>|</span>
          <a href="javascript:void(0)">使用协议</a>
          <span>|</span>
          <a href="javascript:void(0)">隐私条款</a>
        </div>
      </footer>
    </main>
  </div>
</template>
