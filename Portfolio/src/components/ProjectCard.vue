<template>
  <article class="card">
    <div class="preview">
      <span v-if="category" class="badge">{{ category }}</span>
      <!-- Try live embed first for embeddable hosts -->
      <iframe
        v-if="isEmbeddable && url"
        class="frame"
        :src="url"
        loading="lazy"
        referrerpolicy="no-referrer"
        sandbox="allow-same-origin allow-scripts allow-forms allow-popups allow-pointer-lock allow-top-navigation-by-user-activation"
        :title="title"
        :style="frameStyle"
      />
      <!-- Otherwise, use a robust screenshot service -->
      <img v-else-if="previewImage" :src="previewImage" :alt="title" />
      <div v-else class="preview-fallback">No preview available</div>
      <!-- Click-through overlay to open in new tab -->
      <a
        v-if="url"
        class="preview-link"
        :href="url"
        target="_blank"
        rel="noopener noreferrer"
        :aria-label="`Open ${title}`"
      />
    </div>
    <div class="content">
      <h3 class="title">{{ title }}</h3>
      <p class="desc">{{ description }}</p>
      <ul class="tags" v-if="tags?.length">
        <li v-for="(t, i) in tags" :key="i" class="tag">{{ t }}</li>
      </ul>
    </div>
  </article>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  title: { type: String, required: true },
  description: { type: String, default: '' },
  url: { type: String, default: '' },
  image: { type: String, default: '' },
  tags: { type: Array, default: () => [] },
  category: { type: String, default: '' },
  // 0.5 – 1 recommended; smaller means more zoomed out
  previewScale: { type: Number, default: 0.75 },
})

const previewImage = computed(() => {
  if (props.image) return props.image
  if (props.url) {
    // Use a public screenshot service as a safe preview fallback (no key required)
    // WordPress mShots tends to be reliable without API keys
    const encoded = encodeURIComponent(props.url)
    return `https://s.wordpress.com/mshots/v1/${encoded}?w=1200`
  }
  return ''
})

const isEmbeddable = computed(() => {
  if (!props.url) return false
  try {
    const { hostname } = new URL(props.url)
    // Allowlist common hosts that typically permit iframing (adjust as needed)
    const allowlist = [
      'vercel.app',
      'aleleon.dev',
      'github.io',
    ]
    return allowlist.some((d) => hostname.endsWith(d))
  } catch {
    return false
  }
})

const safeScale = computed(() => {
  const s = Number.isFinite(props.previewScale) ? props.previewScale : 0.75
  return Math.min(1, Math.max(0.5, s))
})

const frameStyle = computed(() => ({
  width: `calc(100% / ${safeScale.value})`,
  height: `calc(100% / ${safeScale.value})`,
  transform: `scale(${safeScale.value})`,
  transformOrigin: 'top left',
}))
</script>

<style scoped>
.card {
  background: #0f0f0f;
  border: 1px solid #1f1f1f;
  border-radius: 14px;
  overflow: hidden;
  box-shadow: 0 4px 16px rgba(0,0,0,0.25);
  display: flex;
  flex-direction: column;
}

.preview {
  position: relative;
  aspect-ratio: 16 / 9;
  background: #0b0b0b;
  overflow: hidden;
}
.badge {
  position: absolute;
  top: 10px;
  left: 10px;
  z-index: 1;
  background: #071a19;
  color: #00d4aa;
  border: 1px solid #0f2c2a;
  padding: 0.25rem 0.6rem;
  border-radius: 999px;
  font-size: 0.75rem;
  text-transform: capitalize;
}
.frame {
  width: 100%;
  height: 100%;
  border: 0;
  display: block;
}
.preview img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
}
.preview-fallback {
  width: 100%;
  height: 100%;
  display: grid;
  place-items: center;
  color: #9ca3af;
  font-size: 0.95rem;
}

.preview-link {
  position: absolute;
  inset: 0;
  display: block;
}

.content {
  padding: 1rem 1.1rem 1.25rem;
}
.title {
  color: #e5e7eb;
  font-size: 1.1rem;
  font-weight: 700;
  margin: 0 0 0.5rem 0;
}
.desc {
  color: #9ca3af;
  font-size: 0.95rem;
  margin: 0 0 0.9rem 0;
}
.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem 0.6rem;
  list-style: none;
  margin: 0;
  padding: 0;
}
.tag {
  background: #071a19;
  color: #00d4aa;
  border: 1px solid #0f2c2a;
  padding: 0.35rem 0.6rem;
  border-radius: 999px;
  font-size: 0.8rem;
}
</style>
