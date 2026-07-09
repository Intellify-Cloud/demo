<script setup lang="ts">
  import type { SectionData } from '@/content/siteText'

  defineProps<{
    data: SectionData<'contact'>
  }>()
</script>

<template>
  <section id="contact" class="contact-section shell-section" aria-labelledby="contact-title">
    <div class="contact-section__inner shell-container">
      <div>
        <p class="shell-eyebrow">{{ data.eyebrow }}</p>
        <h2 id="contact-title" class="shell-heading">{{ data.title }}</h2>
        <p class="shell-lead">{{ data.body }}</p>
      </div>

      <form class="contact-section__form shell-card" :action="data.action" :method="data.method">
        <label>
          <span>{{ data.fields.name }}</span>
          <input name="name" type="text" autocomplete="name" required />
        </label>
        <label>
          <span>{{ data.fields.email }}</span>
          <input name="email" type="email" autocomplete="email" required />
        </label>
        <label>
          <span>{{ data.fields.phone }}</span>
          <input name="phone" type="tel" autocomplete="tel" />
        </label>
        <label>
          <span>{{ data.fields.message }}</span>
          <textarea name="message" rows="5" required></textarea>
        </label>
        <button class="shell-button shell-button--primary" type="submit">
          {{ data.submit }}
        </button>
      </form>
    </div>
  </section>
</template>

<style scoped>
  .contact-section {
    background: var(--shell-color-surface-muted);
  }

  .contact-section__inner {
    display: grid;
    grid-template-columns: minmax(0, 0.8fr) minmax(18rem, 1fr);
    gap: clamp(2rem, 6vw, 5rem);
  }

  .contact-section__form {
    display: grid;
    gap: var(--shell-space-4);
    padding: var(--shell-space-6);
  }

  .contact-section__form label {
    display: grid;
    gap: var(--shell-space-2);
    font-weight: 700;
  }

  .contact-section__form input,
  .contact-section__form textarea {
    width: 100%;
    border: 1px solid var(--shell-color-hairline);
    border-radius: var(--shell-radius-md);
    background: var(--shell-color-surface);
    color: var(--shell-color-ink);
    font: inherit;
    padding: 0.8rem 0.9rem;
  }

  .contact-section__form textarea {
    resize: vertical;
  }

  .contact-section__form button {
    justify-self: start;
    border: 0;
    cursor: pointer;
  }

  @media (max-width: 860px) {
    .contact-section__inner {
      grid-template-columns: 1fr;
    }
  }
</style>
