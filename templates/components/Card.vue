<script setup lang="ts">
/**
 * Card Component
 * A gradient card with icon, title, and content
 * Used for grouping related information on slides
 */
defineProps<{
  title: string
  icon?: string
  color?: 'blue' | 'green' | 'amber' | 'red' | 'purple' | 'gray'
  size?: 'sm' | 'md' | 'lg'
}>()
</script>

<template>
  <div
    class="card"
    :class="[
      `card--${color || 'blue'}`,
      `card--${size || 'md'}`
    ]"
  >
    <div class="card__header" v-if="title || icon">
      <span v-if="icon" class="card__icon">{{ icon }}</span>
      <h3 class="card__title">{{ title }}</h3>
    </div>
    <div class="card__content">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.card {
  background-color: var(--color-card, #2d2d44);
  border-radius: 0.75rem;
  padding: 1.25rem;
  position: relative;
  overflow: hidden;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.card:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.3);
}

/* Top gradient border */
.card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
}

/* Color variants */
.card--blue::before {
  background: linear-gradient(90deg, #0ea5e9, #38bdf8);
}

.card--green::before {
  background: linear-gradient(90deg, #10b981, #34d399);
}

.card--amber::before {
  background: linear-gradient(90deg, #f59e0b, #fbbf24);
}

.card--red::before {
  background: linear-gradient(90deg, #ef4444, #f87171);
}

.card--purple::before {
  background: linear-gradient(90deg, #8b5cf6, #a78bfa);
}

.card--gray::before {
  background: linear-gradient(90deg, #64748b, #94a3b8);
}

/* Size variants */
.card--sm {
  padding: 0.875rem;
}

.card--sm .card__title {
  font-size: 0.9rem;
}

.card--lg {
  padding: 1.75rem;
}

.card--lg .card__title {
  font-size: 1.25rem;
}

/* Header */
.card__header {
  display: flex;
  align-items: center;
  gap: 0.625rem;
  margin-bottom: 0.75rem;
}

.card__icon {
  font-size: 1.5rem;
}

.card__title {
  font-size: 1.1rem;
  font-weight: 600;
  color: #ffffff;
  margin: 0;
}

/* Color-coded titles */
.card--blue .card__title { color: #38bdf8; }
.card--green .card__title { color: #34d399; }
.card--amber .card__title { color: #fbbf24; }
.card--red .card__title { color: #f87171; }
.card--purple .card__title { color: #a78bfa; }

/* Content */
.card__content {
  color: #e2e8f0;
  font-size: 0.95rem;
  line-height: 1.6;
}

.card__content :deep(ul) {
  margin: 0.5rem 0;
  padding-left: 1.25rem;
}

.card__content :deep(li) {
  margin-bottom: 0.375rem;
}

.card__content :deep(strong) {
  color: #ffffff;
}
</style>
