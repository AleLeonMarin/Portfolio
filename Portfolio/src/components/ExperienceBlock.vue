<template>
  <div class="experience">
    <h3 class="experience-title">{{ title }}</h3>
    <p class="experience-text">{{ text }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: { type: String, default: '' },
  text: { type: String, required: true },
});
</script>

<style scoped>
.experience-title {
  color: #e5e7eb;
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0 0 1rem 0;
}

.experience-text {
  color: #9ca3af;
  font-size: 1.125rem;
  line-height: 1.75rem;
}
</style>
