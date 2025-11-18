<template>
  <header class="header">
    <div class="container header-container">
      <!-- Logo -->
      <div class="logo">
        <a href="#main" class="logo-link" aria-label="Ir al inicio" @click.prevent="scrollTo('main')">
          <h1>Alejandro</h1>
        </a>
      </div>

      <!-- Navigation -->
      <nav class="nav">
        <ul class="nav-list">
          <li><a href="#about" @click.prevent="scrollTo('about')">About me</a></li>
          <li><a href="#education" @click.prevent="scrollTo('education')">Education</a></li>
          <li><a href="#projects" @click.prevent="scrollTo('projects')">Projects</a></li>
          <li><a href="#contact" @click.prevent="scrollTo('contact')">Contact</a></li>
        </ul>
      </nav>
    </div>
  </header>
  
</template>

<script>
export default {
  name: 'Header',
  methods: {
    scrollTo(id) {
      const el = document.getElementById(id)
      if (!el) return
      const headerOffset = 85
      const targetY = el.getBoundingClientRect().top + window.pageYOffset - headerOffset
      this.easeScrollTo(targetY, 650)
    },
    easeScrollTo(target, duration = 600) {
      const start = window.pageYOffset
      const distance = target - start
      const startTime = performance.now()
      const easeInOutCubic = (t) => (t < 0.5 ? 4 * t * t * t : 1 - Math.pow(-2 * t + 2, 3) / 2)

      const step = (now) => {
        const elapsed = Math.min((now - startTime) / duration, 1)
        const eased = easeInOutCubic(elapsed)
        window.scrollTo(0, start + distance * eased)
        if (elapsed < 1) requestAnimationFrame(step)
      }
      requestAnimationFrame(step)
    },
  },
}
</script>

<style scoped>
.header {
  background-color: #0a0a0a;
  color: white;
  padding: 1.25rem 0; /* vertical only; width handled by .container */
  border-bottom: 1px solid #1a1a1a;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  z-index: 1000;
  box-sizing: border-box;
}

.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.logo h1 {
  margin: 0;
  font-size: 1.5rem;
  font-weight: 600;
  color: #00d4aa;
  letter-spacing: -0.5px;
}

.logo-link {
  text-decoration: none;
  color: inherit;
  display: inline-block;
  padding: 0 !important;
  background: transparent !important;
  -webkit-tap-highlight-color: transparent;
}

.logo-link:hover,
.logo-link:focus,
.logo-link:active {
  background: transparent !important;
  outline: none;
  box-shadow: none;
}

.nav-list {
  display: flex;
  gap: 4rem;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-list a {
  color: #9ca3af;
  text-decoration: none;
  font-size: 1rem;
  font-weight: 400;
  position: relative;
  padding-bottom: 4px;
  transition: color 0.3s ease;
  -webkit-tap-highlight-color: transparent;
}

.nav-list a::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -4px;
  width: 100%;
  height: 2px;
  background-color: #00d4aa;
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.25s ease;
}

.nav-list a:hover,
.nav-list a:focus,
.nav-list a:active {
  color: #00d4aa;
  background: transparent !important; /* Override global anchor hover bg */
  outline: none;
}

.nav-list a:hover::after,
.nav-list a:focus::after,
.nav-list a:active::after {
  transform: scaleX(1);
}

/* Responsive */
@media (max-width: 768px) {
  .header-container {
    padding: 0 2rem;
  }
  
  .nav-list {
    gap: 2rem;
  }
  
  .nav-list a {
    font-size: 0.9rem;
  }
}
</style>