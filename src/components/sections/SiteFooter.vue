<script setup lang="ts">
  import { computed } from 'vue'
  import { siteText, type SectionData } from '@/content/siteText'
  import { useHead } from '@unhead/vue'

  const props = defineProps<{
    data: SectionData<'footer'>
  }>()

  const jsonLd = computed(() =>
    JSON.stringify({
      '@context': 'https://schema.org',
      '@type': 'Organization',
      name: siteText.site.name,
      url: siteText.site.url,
      description: siteText.site.description,
    }),
  )

  useHead({
    script: [
      {
        type: 'application/ld+json',
        textContent: jsonLd,
      },
    ],
  })
</script>

<template>
  <footer class="site-footer" aria-label="Footer">
    <div class="site-footer__inner shell-container">
      <div>
        <a class="site-footer__brand" href="#hero">{{ siteText.site.name }}</a>
        <p>{{ props.data.brand }}</p>
      </div>

      <div class="site-footer__columns">
        <div v-for="column in props.data.columns" :key="column.title" class="site-footer__column">
          <h2>{{ column.title }}</h2>
          <a v-for="link in column.links" :key="link.href" :href="link.href">
            {{ link.label }}
          </a>
        </div>
      </div>
    </div>

    <div class="site-footer__bottom shell-container">
      <small>&copy; {{ new Date().getFullYear() }} {{ siteText.site.name }}</small>
      <div>
        <a v-for="link in props.data.legalLinks" :key="link.href" :href="link.href">
          {{ link.label }}
        </a>
      </div>
    </div>
  </footer>
</template>

<style scoped>
  .site-footer {
    border-top: 1px solid var(--shell-color-hairline);
    padding-block: var(--shell-space-16) var(--shell-space-8);
  }

  .site-footer__inner {
    display: grid;
    grid-template-columns: minmax(0, 1fr) minmax(20rem, 0.8fr);
    gap: var(--shell-space-12);
  }

  .site-footer__brand {
    font-size: 1.125rem;
    font-weight: 800;
  }

  .site-footer p {
    max-width: 32rem;
    margin: var(--shell-space-4) 0 0;
    color: var(--shell-color-muted);
    line-height: 1.65;
  }

  .site-footer__columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: var(--shell-space-8);
  }

  .site-footer__column {
    display: grid;
    align-content: start;
    gap: var(--shell-space-3);
  }

  .site-footer__column h2 {
    margin: 0;
    font-size: 0.875rem;
  }

  .site-footer__column a,
  .site-footer__bottom {
    color: var(--shell-color-muted);
  }

  .site-footer__bottom {
    display: flex;
    justify-content: space-between;
    gap: var(--shell-space-4);
    margin-top: var(--shell-space-12);
    padding-top: var(--shell-space-6);
    border-top: 1px solid var(--shell-color-hairline);
  }

  @media (max-width: 760px) {
    .site-footer__inner,
    .site-footer__columns {
      grid-template-columns: 1fr;
    }

    .site-footer__bottom {
      flex-direction: column;
    }
  }
</style>
