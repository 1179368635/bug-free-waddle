<script setup lang="ts">
import { ref } from 'vue'
import headLogo from './assets/imgs/head_logo.png'
import mainLogo from './assets/imgs/logo-stand600.png'
import microIcon from './assets/svgs/micro.svg'
import iconSetting from './assets/svgs/icon-setting.svg'
import iconSkills from './assets/svgs/icon-skills.svg'
import iconMomery from './assets/svgs/icon-momery.svg'
import iconLoak from './assets/svgs/icon-loak.svg'
import iconDownfiles from './assets/svgs/icon-downfiles.svg'
import iconLink from './assets/svgs/icon-link.svg'
import iconCom from './assets/svgs/icon-com.svg'
import imageScene from './assets/imgs/image_scene.png'
import imageScene1 from './assets/imgs/image_scene1.png'
import imageScene2 from './assets/imgs/image_scene2.png'
import imageScene4 from './assets/imgs/image_scene4.png'

const navItems = [
  { label: '功能优势', target: 'hero-cards' },
  { label: '快速上手', target: 'quick-start' },
  { label: '使用场景', target: 'scenarios' },
]

const activeNav = ref('hero-cards')

const heroCards = [
  {
    title: '自动部署，打开即用',
    description: '支持Windows系统，内置国产优质大模型，支持切换模型',
    tag: '开箱即用',
    icon: iconSetting,
    tagBgColor: '#006fff1a',
    tagColor: '#006fff',
  },
  {
    title: '丰富Skill生态',
    description: '支持丰富Skill，如CowClub、GitHub等丰富生态，Skills 随取随用',
    tag: '丰富生态',
    icon: iconSkills,
    tagBgColor: '#ffa2001a',
    tagColor: '#ffa200',
  },
  {
    title: '持续记忆，你的专属福小智',
    description: '记住偏好和上下文，持续成长，越来越懂你的 AI',
    tag: '智能升级',
    icon: iconMomery,
    tagBgColor: '#fe6c451a',
    tagColor: '#fe6c45',
  },
  {
    title: '本地部署，办公更高效',
    description: '直接操控文件、浏览器、邮件，不只是简单对话',
    tag: '高效办公',
    icon: iconLoak,
    tagBgColor: '#00B8991a',
    tagColor: '#00B899',
  },
]

const quickSteps = [
  {
    title: '下载安装',
    description: '一键安装，无需配置环境',
    icon: iconDownfiles,
  },
  {
    title: '短信验证登录',
    description: '通过短信验证码关联手机号码',
    icon: iconLink,
  },
  {
    title: '电脑发指令立刻工作',
    description: '通过电脑客户端，立刻执行你在任务',
    icon: iconCom,
  },
]

const scenarioCards = [
  {
    tag: '日常办公',
    title: '会议纪要整理',
    description: '智能处理文档、撰写工作文案、管理日程待办、分析办公数据，批量解决重复工作，办公效率提升80%。',
    image: imageScene1,
  },
  {
    tag: '生活助理',
    title: '出行规划',
    description: '规划旅行健身饮食，管理出差费用收支，精准检索生活信息，自定义提醒服务，一站式搞定员工的衣食住行。',
    image: imageScene2,
  },
  {
    tag: '管理决策',
    title: '项目管理决策',
    description: '多方案对比、风险预判、逻辑梳理、趋势分析，基于数据给出决策参考，降低选择风险。',
    image: imageScene,
  },
  {
    tag: '定制专属',
    title: '生产运维',
    description: '定制技能模板、适配行业需求、创建快捷指令、组合多技能，打造贴合你需求的专属AI助手。',
    image: imageScene4,
  },
]

function scrollToSection(target: string) {
  const section = document.getElementById(target)
  if (!section) return
  activeNav.value = target
  const headerHeight = 100
  const sectionTop = section.getBoundingClientRect().top + window.pageYOffset - headerHeight
  window.scrollTo({ top: sectionTop, behavior: 'smooth' })
}

function handleDownload() {
  window.open('https://ai.suoyoubao.com.cn/devbucket/fxx-install/fxz-Setup.exe', '_blank')
}
</script>

<template>
  <div class="page-shell">
    <header class="site-header">
      <div class="brand-block">
        <img class="brand-logo" :src="headLogo" alt="福小智" />
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
      <button class="download-button desktop-only" type="button" @click="handleDownload">
        立即下载
      </button>
    </header>

    <main>
      <section class="hero-section">
        <div class="hero-visual">
          <img class="hero-avatar" :src="mainLogo" alt="福小智" />
        </div>
        <div class="hero-copy">
          <h1 class="eyebrow">福小智</h1>
          <div class="descript-tip">随时随地，唤起你的桌面AI助手</div>
          <div class="hero-text" @click="handleDownload">
            <img class="hero-text-icon" :src="microIcon" alt="Windows" />
            Windows版本安装包
          </div>
          <div id="hero-cards" class="hero-cards">
            <article v-for="card in heroCards" :key="card.title" class="hero-card">
              <div class="hero-card-icon">
                <img :src="card.icon" :alt="card.title" />
              </div>
              <h3>{{ card.title }}</h3>
              <p>{{ card.description }}</p>
              <div class="hero-card-tag" :style="{ backgroundColor: card.tagBgColor, color: card.tagColor }">
                {{ card.tag }}
              </div>
            </article>
          </div>
        </div>
      </section>

      <section id="quick-start" class="content-section">
        <div class="section-heading">
          <p class="work-title">—— HOW IT WORKS ——</p>
          <h2>几分钟即可上手</h2>
          <p class="work-tip">
            从下载到开始咨询，几分钟即可上手
          </p>
        </div>
        <div class="step-grid">
          <article v-for="(step, index) in quickSteps" :key="step.title" class="step-card">
            <div class="step-icon">
              <div class="icon-container">
                <img :src="step.icon" :alt="step.title" />
              </div>
            </div>
            <div class="step-number">0{{ index + 1 }}</div>
            <h3>{{ step.title }}</h3>
            <p>{{ step.description }}</p>
          </article>
        </div>
      </section>

      <section id="scenarios" class="content-section">
        <div class="section-heading">
          <p class="work-title">—— SCENARIOS ——</p>
          <h2>真实场景，随时体验</h2>
          <p class="work-tip">
            从日常办公到专业服务，福小智帮您解锁无限可能
          </p>
        </div>
        <div class="scenario-grid">
          <article v-for="card in scenarioCards" :key="card.title" class="scenario-card">
            <div class="scenario-image">
              <img :src="card.image" :alt="card.title" />
              <div class="scenario-progress">
                <span class="card-tag">{{ card.tag }}</span>
              </div>
            </div>
            <h3>{{ card.title }}</h3>
            <p>{{ card.description }}</p>
          </article>
        </div>
      </section>

      <section class="cta-section">
        <div class="footer-content">
          <div class="footer-logo">
            <img class="brand-logo" :src="headLogo" alt="福小智" />
            <span class="footer-brand">福小智</span>
          </div>
          <div class="footer-info">
            <p class="copyright">Copyright © 2025 - 2026 FUXIAOZHI All Rights Reserved.</p>
            <div class="footer-links">
              <a href="#">福小智</a>
              <span>|</span>
              <a href="#">版权所有</a>
              <span>|</span>
              <a href="#">使用协议</a>
              <span>|</span>
              <a href="#">隐私条款</a>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>
