<template>
  <section class="hero" id="main">
    <div class="hero-content">
      <h1 class="hero-title">
        Hi, I'm <span class="name">Alejandro</span>
      </h1>
      <p class="hero-subtitle">
        Software Engineer passionate about creating clean and functional<br>
        digital experiences
      </p>
      <div class="hero-buttons">
        <button class="btn btn-primary">View my work</button>
        <button class="btn btn-secondary">Download CV</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Main'
}
</script>

<style scoped>
.hero {
  width: 100%;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #0a0a0a;
  padding: 0;
  margin: 0;
}

.hero-content {
  text-align: center;
  max-width: 900px;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 700;
  color: white;
  margin-bottom: 1.5rem;
  line-height: 1.2;
}

.name {
  color: #00d4aa;
}

.hero-subtitle {
  font-size: 1.25rem;
  color: #9ca3af;
  margin-bottom: 3rem;
  line-height: 1.6;
  font-weight: 400;
}

.hero-buttons {
  display: flex;
  gap: 1.5rem;
  justify-content: center;
  align-items: center;
}

.btn {
  padding: 1rem 2rem;
  font-size: 1rem;
  font-weight: 500;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  border: 2px solid transparent;
}

.btn-primary {
  background-color: #00d4aa;
  color: #0a0a0a;
  border-color: #00d4aa;
}

.btn-primary:hover {
  background-color: #00b894;
  border-color: #00b894;
  transform: translateY(-2px);
}

.btn-secondary {
  background-color: transparent;
  color: white;
  border-color: #333;
}

.btn-secondary:hover {
  border-color: #00d4aa;
  color: #00d4aa;
  transform: translateY(-2px);
}

/* Responsive */
@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-subtitle {
    font-size: 1.1rem;
  }
  
  .hero-buttons {
    flex-direction: column;
    gap: 1rem;
  }
  
  .btn {
    width: 100%;
  }
}
</style>