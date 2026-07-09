<script setup lang="ts">
  import { defineAsyncComponent, type Component } from 'vue'
  import { siteText, type SectionName } from '@/content/siteText'

  const componentMap: Record<SectionName, Component> = {
    'contact-bar': defineAsyncComponent(() => import('@/components/sections/ContactBar.vue')),
    'nav-bar': defineAsyncComponent(() => import('@/components/sections/NavBar.vue')),
    hero: defineAsyncComponent(() => import('@/components/sections/HeroSection.vue')),
    about: defineAsyncComponent(() => import('@/components/sections/AboutSection.vue')),
    steps: defineAsyncComponent(() => import('@/components/sections/StepsSection.vue')),
    map: defineAsyncComponent(() => import('@/components/sections/MapSection.vue')),
    team: defineAsyncComponent(() => import('@/components/sections/TeamSection.vue')),
    testimonials: defineAsyncComponent(
      () => import('@/components/sections/TestimonialsSection.vue'),
    ),
    contact: defineAsyncComponent(() => import('@/components/sections/ContactSection.vue')),
    footer: defineAsyncComponent(() => import('@/components/sections/SiteFooter.vue')),
  }
</script>

<template>
  <main id="main-content">
    <component
      :is="componentMap[name]"
      v-for="name in siteText.sections"
      :key="name"
      :data="siteText[name]"
    />
  </main>
</template>
