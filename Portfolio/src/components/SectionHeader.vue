<template>
  <div class="section-header">
    <h2>{{ title }}</h2>
    <div class="underline" :style="{ backgroundColor: accentColor }" />
  </div>
  
</template>

<script setup>
const props = defineProps({
  title: { type: String, required: true },
  accentColor: { type: String, default: '#00d4aa' },
});
</script>

<style scoped>
.section-header {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 1.25rem;
}

.section-header h2 {
  color: #ffffff;
  font-size: 2.75rem;
  line-height: 1.1;
  font-weight: 800;
  letter-spacing: -0.02em;
}

.underline {
  width: 96px;
  height: 4px;
  border-radius: 999px;
}
</style>
