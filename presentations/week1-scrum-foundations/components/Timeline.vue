<script setup lang="ts">
/**
 * Timeline Component
 * Display events in sequence with times and descriptions
 * Useful for agendas, process flows, and event schedules
 */
interface TimelineEvent {
  time: string
  title: string
  description?: string
  color?: 'blue' | 'green' | 'amber' | 'purple'
}

defineProps<{
  events: TimelineEvent[]
  orientation?: 'vertical' | 'horizontal'
}>()
</script>

<template>
  <div class="timeline" :class="`timeline--${orientation || 'vertical'}`">
    <div
      v-for="(event, index) in events"
      :key="index"
      class="timeline__item"
      :class="`timeline__item--${event.color || 'blue'}`"
      :style="{ animationDelay: `${index * 0.1}s` }"
    >
      <div class="timeline__marker">
        <div class="timeline__dot"></div>
        <div v-if="index < events.length - 1" class="timeline__line"></div>
      </div>
      <div class="timeline__content">
        <span class="timeline__time">{{ event.time }}</span>
        <h4 class="timeline__title">{{ event.title }}</h4>
        <p v-if="event.description" class="timeline__description">{{ event.description }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.timeline {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.timeline--horizontal {
  flex-direction: row;
  overflow-x: auto;
  padding-bottom: 1rem;
}

.timeline__item {
  display: flex;
  gap: 1rem;
  animation: fadeIn 0.4s ease-out both;
}

.timeline--horizontal .timeline__item {
  flex-direction: column;
  min-width: 150px;
  text-align: center;
}

.timeline__marker {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-shrink: 0;
}

.timeline--horizontal .timeline__marker {
  flex-direction: row;
}

.timeline__dot {
  width: 1rem;
  height: 1rem;
  border-radius: 50%;
  background: currentColor;
  box-shadow: 0 0 0 4px rgba(255, 255, 255, 0.1);
}

.timeline__line {
  width: 2px;
  flex: 1;
  min-height: 2rem;
  background: linear-gradient(to bottom, currentColor, transparent);
  opacity: 0.3;
}

.timeline--horizontal .timeline__line {
  width: auto;
  height: 2px;
  min-width: 2rem;
  flex: 1;
  background: linear-gradient(to right, currentColor, transparent);
}

/* Color variants */
.timeline__item--blue { color: #0ea5e9; }
.timeline__item--green { color: #10b981; }
.timeline__item--amber { color: #f59e0b; }
.timeline__item--purple { color: #8b5cf6; }

.timeline__content {
  padding-bottom: 1.5rem;
}

.timeline--horizontal .timeline__content {
  padding-bottom: 0;
  padding-right: 1.5rem;
}

.timeline__time {
  display: inline-block;
  font-size: 0.85rem;
  font-weight: 600;
  color: currentColor;
  background: rgba(255, 255, 255, 0.1);
  padding: 0.125rem 0.5rem;
  border-radius: 0.25rem;
  margin-bottom: 0.375rem;
}

.timeline__title {
  font-size: 1rem;
  font-weight: 600;
  color: #ffffff;
  margin: 0.25rem 0;
}

.timeline__description {
  font-size: 0.9rem;
  color: #94a3b8;
  margin: 0;
  line-height: 1.4;
}

/* Animation */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateX(-10px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>
