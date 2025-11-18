<template>
  <ul class="chips">
    <li v-for="(skill, idx) in skills" :key="idx" class="chip">{{ skill }}</li>
  </ul>
</template>

<script setup>
defineProps({
  skills: { type: Array, default: () => [] },
});
</script>

<style scoped>
.chips {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem 1rem;
  padding: 0;
  margin: 0;
  list-style: none;
}

.chip {
  background: #071a19;
  color: #00d4aa;
  border: 1px solid #0f2c2a;
  padding: 0.5rem 0.9rem;
  border-radius: 999px;
  font-size: 0.95rem;
}
</style>
