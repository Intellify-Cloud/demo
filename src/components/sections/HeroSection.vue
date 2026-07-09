<script setup lang="ts">
  import type { SectionData } from '@/content/siteText'

  defineProps<{
    data: SectionData<'hero'>
  }>()
</script>

<template>
  <section id="hero" class="hero-section" aria-labelledby="hero-title">
    <div class="hero-section__inner shell-container">
      <div class="hero-section__copy">
        <p class="shell-eyebrow">{{ data.eyebrow }}</p>
        <h1 id="hero-title" class="hero-section__title">{{ data.title }}</h1>
        <p class="hero-section__body">{{ data.body }}</p>
        <div class="hero-section__actions" aria-label="Hero actions">
          <a class="shell-button shell-button--primary" :href="data.primaryCta.href">
            {{ data.primaryCta.label }}
          </a>
          <a class="shell-button shell-button--secondary" :href="data.secondaryCta.href">
            {{ data.secondaryCta.label }}
          </a>
        </div>
      </div>

      <div class="hero-section__panel shell-card" aria-label="Template preview">
        <div class="hero-section__panel-line hero-section__panel-line--wide"></div>
        <div class="hero-section__panel-grid">
          <span></span>
          <span></span>
          <span></span>
          <span></span>
        </div>
        <div class="hero-section__panel-line"></div>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .hero-section {
    min-height: 80vh;
    display: grid;
    align-items: center;
    padding-block: clamp(4rem, 10vw, 8rem);
  }

  .hero-section__inner {
    display: grid;
    grid-template-columns: minmax(0, 1fr) minmax(18rem, 0.78fr);
    align-items: center;
    gap: clamp(2rem, 6vw, 5rem);
  }

  .hero-section__title {
    max-width: 11ch;
    margin: var(--shell-space-4) 0 0;
    font-size: clamp(3rem, 8vw, 5.75rem);
    font-weight: 650;
    letter-spacing: -0.03em;
    line-height: 0.98;
  }

  .hero-section__body {
    max-width: 42rem;
    margin: var(--shell-space-6) 0 0;
    color: var(--shell-color-muted);
    font-size: clamp(1.125rem, 2vw, 1.375rem);
    line-height: 1.6;
  }

  .hero-section__actions {
    display: flex;
    flex-wrap: wrap;
    gap: var(--shell-space-3);
    margin-top: var(--shell-space-8);
  }

  .hero-section__panel {
    min-height: 26rem;
    padding: var(--shell-space-8);
  }

  .hero-section__panel-line {
    height: 1rem;
    width: 62%;
    border-radius: 999px;
    background: var(--shell-color-surface-muted);
  }

  .hero-section__panel-line--wide {
    width: 84%;
    background: var(--shell-color-accent-soft);
  }

  .hero-section__panel-grid {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: var(--shell-space-4);
    margin-block: var(--shell-space-8);
  }

  .hero-section__panel-grid span {
    aspect-ratio: 1.35;
    border: 1px solid var(--shell-color-hairline);
    border-radius: var(--shell-radius-md);
    background: var(--shell-color-canvas);
  }

  @media (max-width: 860px) {
    .hero-section__inner {
      grid-template-columns: 1fr;
    }

    .hero-section__panel {
      min-height: 18rem;
    }
  }
</style>
