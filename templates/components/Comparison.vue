<script setup lang="ts">
/**
 * Comparison Component
 * Side-by-side do's and don'ts or before/after comparison
 * Great for showing contrasts and best practices
 */
defineProps<{
  doTitle?: string
  dontTitle?: string
  layout?: 'horizontal' | 'vertical'
}>()
</script>

<template>
  <div class="comparison" :class="`comparison--${layout || 'horizontal'}`">
    <div class="comparison__column comparison__column--do">
      <div class="comparison__header comparison__header--do">
        <span class="comparison__icon">&#10003;</span>
        <span class="comparison__label">{{ doTitle || 'Do' }}</span>
      </div>
      <ul class="comparison__list">
        <slot name="do" />
      </ul>
    </div>
    <div class="comparison__column comparison__column--dont">
      <div class="comparison__header comparison__header--dont">
        <span class="comparison__icon">&#10007;</span>
        <span class="comparison__label">{{ dontTitle || "Don't" }}</span>
      </div>
      <ul class="comparison__list">
        <slot name="dont" />
      </ul>
    </div>
  </div>
</template>

<style scoped>
.comparison {
  display: grid;
  gap: 1.5rem;
  width: 100%;
}

.comparison--horizontal {
  grid-template-columns: 1fr 1fr;
}

.comparison--vertical {
  grid-template-columns: 1fr;
}

.comparison__column {
  background-color: var(--color-card, #2d2d44);
  border-radius: 0.75rem;
  overflow: hidden;
}

.comparison__header {
  display: flex;
  align-items: center;
  gap: 0.625rem;
  padding: 0.875rem 1.25rem;
  font-weight: 600;
  font-size: 1.1rem;
}

.comparison__header--do {
  background: linear-gradient(90deg, rgba(16, 185, 129, 0.2), transparent);
  color: #34d399;
  border-bottom: 2px solid #10b981;
}

.comparison__header--dont {
  background: linear-gradient(90deg, rgba(239, 68, 68, 0.2), transparent);
  color: #f87171;
  border-bottom: 2px solid #ef4444;
}

.comparison__icon {
  font-size: 1.25rem;
  font-weight: bold;
}

.comparison__list {
  list-style: none;
  padding: 1rem 1.25rem;
  margin: 0;
}

.comparison__list :deep(li) {
  display: flex;
  align-items: flex-start;
  gap: 0.625rem;
  padding: 0.5rem 0;
  color: #e2e8f0;
  font-size: 0.95rem;
  line-height: 1.5;
}

.comparison__column--do .comparison__list :deep(li)::before {
  content: '\\2713';
  color: #10b981;
  font-weight: bold;
  flex-shrink: 0;
}

.comparison__column--dont .comparison__list :deep(li)::before {
  content: '\\2717';
  color: #ef4444;
  font-weight: bold;
  flex-shrink: 0;
}

/* Animation */
.comparison__column {
  animation: slideIn 0.5s ease-out both;
}

.comparison__column--dont {
  animation-delay: 0.1s;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
