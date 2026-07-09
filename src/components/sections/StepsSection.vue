<script setup lang="ts">
  import type { SectionData } from '@/content/siteText'

  defineProps<{
    data: SectionData<'steps'>
  }>()
</script>

<template>
  <section id="steps" class="steps-section shell-section" aria-labelledby="steps-title">
    <div class="shell-container">
      <p class="shell-eyebrow">{{ data.eyebrow }}</p>
      <h2 id="steps-title" class="shell-heading">{{ data.title }}</h2>

      <div class="steps-section__grid">
        <article
          v-for="(item, index) in data.items"
          :key="item.title"
          class="steps-section__card shell-card"
        >
          <span class="steps-section__number">{{ String(index + 1).padStart(2, '0') }}</span>
          <h3>{{ item.title }}</h3>
          <p>{{ item.body }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .steps-section__grid {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: var(--shell-space-4);
    margin-top: var(--shell-space-10);
  }

  .steps-section__card {
    padding: var(--shell-space-6);
  }

  .steps-section__number {
    color: var(--shell-color-accent);
    font-size: 0.875rem;
    font-weight: 800;
  }

  .steps-section__card h3 {
    margin: var(--shell-space-5) 0 var(--shell-space-3);
    font-size: 1.375rem;
  }

  .steps-section__card p {
    margin: 0;
    color: var(--shell-color-muted);
    line-height: 1.65;
  }

  @media (max-width: 860px) {
    .steps-section__grid {
      grid-template-columns: 1fr;
    }
  }
</style>
