<script setup lang="ts">
/**
 * Checklist Component
 * Display learning objectives or task lists with checkmarks
 * Items appear with a satisfying check animation
 */
defineProps<{
  items: string[]
  title?: string
  color?: 'green' | 'blue' | 'amber'
}>()
</script>

<template>
  <div class="checklist" :class="`checklist--${color || 'green'}`">
    <h3 v-if="title" class="checklist__title">{{ title }}</h3>
    <ul class="checklist__list">
      <li
        v-for="(item, index) in items"
        :key="index"
        class="checklist__item"
        :style="{ animationDelay: `${index * 0.1}s` }"
      >
        <span class="checklist__icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3">
            <polyline points="20 6 9 17 4 12"></polyline>
          </svg>
        </span>
        <span class="checklist__text">{{ item }}</span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.checklist {
  padding: 0.5rem 0;
}

.checklist__title {
  font-size: 1.25rem;
  font-weight: 600;
  color: #ffffff;
  margin-bottom: 1rem;
}

.checklist__list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.checklist__item {
  display: flex;
  align-items: flex-start;
  gap: 0.875rem;
  padding: 0.625rem 0;
  animation: checkIn 0.4s ease-out both;
}

.checklist__icon {
  flex-shrink: 0;
  width: 1.5rem;
  height: 1.5rem;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 0.125rem;
}

.checklist__icon svg {
  width: 1rem;
  height: 1rem;
}

/* Color variants */
.checklist--green .checklist__icon {
  background: linear-gradient(135deg, #10b981, #059669);
  color: #ffffff;
}

.checklist--blue .checklist__icon {
  background: linear-gradient(135deg, #0ea5e9, #0284c7);
  color: #ffffff;
}

.checklist--amber .checklist__icon {
  background: linear-gradient(135deg, #f59e0b, #d97706);
  color: #ffffff;
}

.checklist__text {
  color: #e2e8f0;
  font-size: 1.05rem;
  line-height: 1.5;
}

/* Animation */
@keyframes checkIn {
  from {
    opacity: 0;
    transform: translateX(-10px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* Hover effect */
.checklist__item:hover .checklist__icon {
  transform: scale(1.1);
  transition: transform 0.2s ease;
}
</style>
