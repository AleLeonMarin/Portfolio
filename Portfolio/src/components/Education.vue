<template>
  <section id="education" class="education">
    <div class="container">
      <SectionHeader title="Education & Certifications" />

      <div class="timeline">
        <!-- University/School -->
        <article class="entry">
          <div class="icon-wrapper">
            <svg class="icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M12 3L1 9L12 15L21 10.09V17H23V9M5 13.18V17.18L12 21L19 17.18V13.18L12 17L5 13.18Z" fill="currentColor"/>
            </svg>
          </div>
          <div class="content">
            <h3 class="degree">Diplomacy Degree in Software Engineering</h3>
            <p class="institution">Universidad Nacional de Costa Rica</p>
            <p class="period">2022 - 2025</p>
            <p class="description">
              Focused on software development, algorithms, databases, and modern web technologies.
            </p>
          </div>
        </article>

        <!-- Add more education entries here -->
        <!-- Example:
        <article class="entry">
          <div class="icon-wrapper">
            <svg class="icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M12 3L1 9L12 15L21 10.09V17H23V9M5 13.18V17.18L12 21L19 17.18V13.18L12 17L5 13.18Z" fill="currentColor"/>
            </svg>
          </div>
          <div class="content">
            <h3 class="degree">High School Diploma</h3>
            <p class="institution">Your High School</p>
            <p class="period">2015 - 2018</p>
          </div>
        </article>
        -->
      </div>

      <h3 class="certs-title">Certifications</h3>
      <div class="certs-grid">
        <article class="cert-card">
          <div class="cert-icon">
            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M9 16.17L4.83 12L3.41 13.41L9 19L21 7L19.59 5.59L9 16.17Z" fill="currentColor"/>
            </svg>
          </div>
          <h4 class="cert-name">Linux Essentials</h4>
          <p class="cert-issuer">Cisco Academy</p>
          <p class="cert-date">2025</p>
        </article>

        <article class="cert-card">
          <div class="cert-icon">
            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M9 16.17L4.83 12L3.41 13.41L9 19L21 7L19.59 5.59L9 16.17Z" fill="currentColor"/>
            </svg>
          </div>
          <h4 class="cert-name">Scrum Master Certification</h4>
          <p class="cert-issuer">Coursera</p>
          <p class="cert-date">2025</p>
        </article>

        <article class="cert-card">
          <div class="cert-icon">
            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M9 16.17L4.83 12L3.41 13.41L9 19L21 7L19.59 5.59L9 16.17Z" fill="currentColor"/>
            </svg>
          </div>
          <h4 class="cert-name">Linux Unhatched</h4>
          <p class="cert-issuer">Cisco Academy</p>
          <p class="cert-date">2025</p>
        </article>

        <article class="cert-card">
          <div class="cert-icon">
            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M9 16.17L4.83 12L3.41 13.41L9 19L21 7L19.59 5.59L9 16.17Z" fill="currentColor"/>
            </svg>
          </div>
          <h4 class="cert-name">Operating Systems Basics</h4>
          <p class="cert-issuer">Cisco Academy</p>
          <p class="cert-date">2025</p>
        </article>

        <!-- Add more certificates as needed -->
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionHeader from './SectionHeader.vue'
</script>

<style scoped>
.education {
  background: #0a0a0a;
  padding: 6rem 0;
  scroll-margin-top: 90px;
}

/* Timeline for education entries */
.timeline {
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.entry {
  display: flex;
  gap: 1.25rem;
  align-items: flex-start;
}

.icon-wrapper {
  flex-shrink: 0;
  width: 48px;
  height: 48px;
  background: #071a19;
  border: 1px solid #0f2c2a;
  border-radius: 12px;
  display: grid;
  place-items: center;
}

.icon {
  width: 24px;
  height: 24px;
  color: #00d4aa;
}

.entry .content {
  flex: 1;
}

.degree {
  color: #e5e7eb;
  font-size: 1.25rem;
  font-weight: 700;
  margin: 0 0 0.4rem 0;
}

.institution {
  color: #00d4aa;
  font-size: 1rem;
  font-weight: 600;
  margin: 0 0 0.25rem 0;
}

.period {
  color: #9ca3af;
  font-size: 0.9rem;
  margin: 0 0 0.5rem 0;
}

.description {
  color: #9ca3af;
  font-size: 0.95rem;
  line-height: 1.6;
  margin: 0;
}

/* Certifications */
.certs-title {
  color: #e5e7eb;
  font-size: 1.5rem;
  font-weight: 700;
  margin: 3rem 0 1.5rem 0;
  text-align: center;
}

.certs-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;
  margin-top: 1.5rem;
}

@media (min-width: 720px) {
  .certs-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .certs-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.cert-card {
  background: #0f0f0f;
  border: 1px solid #1f1f1f;
  border-radius: 14px;
  padding: 1.5rem;
  text-align: center;
  transition: all 0.3s ease;
}

.cert-card:hover {
  border-color: #00d4aa;
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 212, 170, 0.1);
}

.cert-icon {
  width: 56px;
  height: 56px;
  margin: 0 auto 1rem;
  background: #071a19;
  border: 1px solid #0f2c2a;
  border-radius: 50%;
  display: grid;
  place-items: center;
}

.cert-icon svg {
  width: 28px;
  height: 28px;
  color: #00d4aa;
}

.cert-name {
  color: #e5e7eb;
  font-size: 1.1rem;
  font-weight: 700;
  margin: 0 0 0.5rem 0;
}

.cert-issuer {
  color: #9ca3af;
  font-size: 0.9rem;
  margin: 0 0 0.25rem 0;
}

.cert-date {
  color: #00d4aa;
  font-size: 0.85rem;
  font-weight: 600;
  margin: 0;
}
</style>
