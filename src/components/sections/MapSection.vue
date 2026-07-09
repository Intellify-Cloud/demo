<script setup lang="ts">
  import type { SectionData } from '@/content/siteText'

  defineProps<{
    data: SectionData<'map'>
  }>()
</script>

<template>
  <section id="map" class="map-section shell-section" aria-labelledby="map-title">
    <div class="map-section__inner shell-container">
      <div>
        <p class="shell-eyebrow">{{ data.eyebrow }}</p>
        <h2 id="map-title" class="shell-heading">{{ data.title }}</h2>
        <p class="shell-lead">{{ data.body }}</p>
        <p v-if="data.address" class="map-section__address">{{ data.address }}</p>
      </div>

      <div class="map-section__frame shell-card">
        <iframe
          v-if="data.embedUrl"
          :src="data.embedUrl"
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
          title="Map"
        ></iframe>
        <div v-else class="map-section__placeholder">
          <span>Map embed placeholder</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .map-section__inner {
    display: grid;
    grid-template-columns: minmax(0, 0.75fr) minmax(0, 1fr);
    align-items: center;
    gap: clamp(2rem, 6vw, 5rem);
  }

  .map-section__address {
    margin-top: var(--shell-space-6);
    font-weight: 700;
  }

  .map-section__frame {
    overflow: hidden;
    aspect-ratio: 16 / 10;
  }

  .map-section__frame iframe,
  .map-section__placeholder {
    width: 100%;
    height: 100%;
    border: 0;
  }

  .map-section__placeholder {
    display: grid;
    place-items: center;
    background:
      linear-gradient(var(--shell-color-hairline) 1px, transparent 1px),
      linear-gradient(90deg, var(--shell-color-hairline) 1px, transparent 1px),
      var(--shell-color-surface-muted);
    background-size: 32px 32px;
    color: var(--shell-color-muted);
    font-weight: 700;
  }

  @media (max-width: 860px) {
    .map-section__inner {
      grid-template-columns: 1fr;
    }
  }
</style>
