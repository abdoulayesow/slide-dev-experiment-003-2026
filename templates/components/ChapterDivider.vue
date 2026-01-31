<script setup lang="ts">
/**
 * ChapterDivider Component
 * Large numbered section break for presentations
 * Creates visual separation between major sections
 */
defineProps<{
  number: string | number
  title: string
  subtitle?: string
}>()
</script>

<template>
  <div class="chapter-divider">
    <div class="chapter-divider__number">{{ number }}</div>
    <h2 class="chapter-divider__title">{{ title }}</h2>
    <p v-if="subtitle" class="chapter-divider__subtitle">{{ subtitle }}</p>
  </div>
</template>

<style scoped>
.chapter-divider {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  height: 100%;
  width: 100%;
  padding: 2rem;
  background: linear-gradient(135deg, #0ea5e9 0%, #8b5cf6 100%);
  position: relative;
}

/* Subtle pattern overlay */
.chapter-divider::before {
  content: '';
  position: absolute;
  inset: 0;
  background-image: radial-gradient(circle at 25% 25%, rgba(255,255,255,0.1) 0%, transparent 50%);
  pointer-events: none;
}

.chapter-divider__number {
  font-size: 10rem;
  font-weight: 800;
  color: rgba(255, 255, 255, 0.15);
  line-height: 1;
  position: relative;
  z-index: 1;
  text-shadow: 0 4px 30px rgba(0, 0, 0, 0.2);
}

.chapter-divider__title {
  font-size: 3.5rem;
  font-weight: 700;
  color: #ffffff;
  margin: -1rem 0 0 0;
  position: relative;
  z-index: 2;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
}

.chapter-divider__subtitle {
  font-size: 1.25rem;
  color: rgba(255, 255, 255, 0.8);
  margin-top: 0.75rem;
  font-weight: 400;
  position: relative;
  z-index: 2;
}

/* Animation */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.chapter-divider__number {
  animation: fadeInUp 0.6s ease-out;
}

.chapter-divider__title {
  animation: fadeInUp 0.6s ease-out 0.1s both;
}

.chapter-divider__subtitle {
  animation: fadeInUp 0.6s ease-out 0.2s both;
}
</style>
