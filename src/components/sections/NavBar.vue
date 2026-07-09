<script setup lang="ts">
  import type { SectionData } from '@/content/siteText'

  defineProps<{
    data: SectionData<'nav-bar'>
  }>()
</script>

<template>
  <header class="nav-bar">
    <nav class="nav-bar__inner shell-container" aria-label="Primary">
      <a class="nav-bar__brand" href="#hero">{{ data.logoText }}</a>

      <div class="nav-bar__links" aria-label="Primary links">
        <a v-for="link in data.links" :key="link.href" :href="link.href">
          {{ link.label }}
        </a>
      </div>

      <a class="shell-button shell-button--primary nav-bar__cta" :href="data.cta.href">
        {{ data.cta.label }}
      </a>
    </nav>
  </header>
</template>

<style scoped>
  .nav-bar {
    position: sticky;
    top: 0;
    z-index: 20;
    min-height: 100px;
    border-bottom: 1px solid var(--shell-color-hairline);
    background: color-mix(in srgb, var(--shell-color-canvas) 92%, transparent);
    backdrop-filter: blur(16px);
  }

  .nav-bar__inner {
    display: grid;
    min-height: 100px;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    gap: var(--shell-space-6);
  }

  .nav-bar__brand {
    font-size: 1.125rem;
    font-weight: 800;
  }

  .nav-bar__links {
    display: flex;
    align-items: center;
    gap: var(--shell-space-6);
    color: var(--shell-color-muted);
    font-size: 0.9375rem;
    font-weight: 650;
  }

  .nav-bar__links a:hover {
    color: var(--shell-color-ink);
  }

  .nav-bar__cta {
    justify-self: end;
  }

  @media (max-width: 760px) {
    .nav-bar,
    .nav-bar__inner {
      min-height: 76px;
    }

    .nav-bar__inner {
      grid-template-columns: 1fr auto;
    }

    .nav-bar__links {
      display: none;
    }
  }
</style>
