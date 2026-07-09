<script setup lang="ts">
  import type { SectionData } from '@/content/siteText'

  defineProps<{
    data: SectionData<'team'>
  }>()
</script>

<template>
  <section id="team" class="team-section shell-section" aria-labelledby="team-title">
    <div class="shell-container">
      <p class="shell-eyebrow">{{ data.eyebrow }}</p>
      <h2 id="team-title" class="shell-heading">{{ data.title }}</h2>

      <div v-if="data.members.length" class="team-section__grid">
        <article
          v-for="member in data.members"
          :key="member.name + member.role"
          class="team-section__card shell-card"
        >
          <div class="team-section__avatar" aria-hidden="true">{{ member.name.slice(0, 1) }}</div>
          <h3>{{ member.name }}</h3>
          <p class="team-section__role">{{ member.role }}</p>
          <p>{{ member.bio }}</p>
        </article>
      </div>

      <div v-else class="team-section__empty shell-card">
        Add team members in `siteText.ts`, or remove `team` from the section registry.
      </div>
    </div>
  </section>
</template>

<style scoped>
  .team-section__grid {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: var(--shell-space-4);
    margin-top: var(--shell-space-10);
  }

  .team-section__card,
  .team-section__empty {
    padding: var(--shell-space-6);
  }

  .team-section__avatar {
    display: grid;
    width: 3rem;
    height: 3rem;
    place-items: center;
    border-radius: 999px;
    background: var(--shell-color-accent-soft);
    color: var(--shell-color-accent);
    font-weight: 800;
  }

  .team-section__card h3 {
    margin: var(--shell-space-5) 0 var(--shell-space-1);
  }

  .team-section__card p {
    margin: var(--shell-space-3) 0 0;
    color: var(--shell-color-muted);
    line-height: 1.65;
  }

  .team-section__role {
    color: var(--shell-color-ink) !important;
    font-weight: 700;
  }

  .team-section__empty {
    margin-top: var(--shell-space-10);
    color: var(--shell-color-muted);
  }

  @media (max-width: 860px) {
    .team-section__grid {
      grid-template-columns: 1fr;
    }
  }
</style>
