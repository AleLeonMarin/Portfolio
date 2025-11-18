<template>
  <div class="feature">
    <h3 class="feature-title">{{ title }}</h3>
    <p class="feature-text">{{ description }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: { type: String, required: true },
  description: { type: String, required: true },
});
</script>

<style scoped>
.feature-title {
  color: #e5e7eb;
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0 0 1rem 0;
}

.feature-text {
  color: #9ca3af;
  font-size: 1.125rem;
  line-height: 1.75rem;
}
</style>
