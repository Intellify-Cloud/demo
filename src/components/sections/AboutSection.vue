<script setup lang="ts">
  import type { SectionData } from '@/content/siteText'

  defineProps<{
    data: SectionData<'about'>
  }>()
</script>

<template>
  <section id="about" class="about-section shell-section" aria-labelledby="about-title">
    <div class="about-section__inner shell-container">
      <div>
        <p class="shell-eyebrow">{{ data.eyebrow }}</p>
        <h2 id="about-title" class="shell-heading">{{ data.title }}</h2>
      </div>
      <div class="about-section__body">
        <p>{{ data.body }}</p>
        <ul class="about-section__highlights" aria-label="Template highlights">
          <li v-for="highlight in data.highlights" :key="highlight">{{ highlight }}</li>
        </ul>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .about-section__inner {
    display: grid;
    grid-template-columns: minmax(0, 0.8fr) minmax(0, 1fr);
    gap: clamp(2rem, 6vw, 5rem);
  }

  .about-section__body {
    color: var(--shell-color-muted);
    font-size: 1.125rem;
    line-height: 1.7;
  }

  .about-section__body p {
    margin: 0;
  }

  .about-section__highlights {
    display: grid;
    gap: var(--shell-space-3);
    margin: var(--shell-space-8) 0 0;
    padding: 0;
    list-style: none;
  }

  .about-section__highlights li {
    border: 1px solid var(--shell-color-hairline);
    border-radius: var(--shell-radius-md);
    background: var(--shell-color-surface);
    padding: var(--shell-space-4);
    color: var(--shell-color-ink);
    font-weight: 650;
  }

  @media (max-width: 760px) {
    .about-section__inner {
      grid-template-columns: 1fr;
    }
  }
</style>
