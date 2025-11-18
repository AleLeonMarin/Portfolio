<template>
  <section id="contact" class="contact">
    <div class="container">
      <h2 class="title">Let's work together</h2>
      <p class="subtitle">
        If you have a project in mind or simply want to chat, I'd love to hear from you.
      </p>

      <form class="form" @submit.prevent="onSubmit">
        <div class="row">
          <label class="field">
            <span>Name</span>
            <input v-model.trim="form.name" type="text" name="name" placeholder="Your full name" autocomplete="name" required />
          </label>
          <label class="field">
            <span>Email</span>
            <input v-model.trim="form.email" type="email" name="email" placeholder="your@email.com" autocomplete="email" required />
          </label>
        </div>
        <label class="field full">
          <span>Subject (optional)</span>
          <input v-model.trim="form.subject" type="text" name="subject" placeholder="Web project, consulting, collaboration..." />
        </label>
        <label class="field full">
          <span>Message</span>
          <textarea v-model.trim="form.message" name="message" rows="6" placeholder="Tell me about your project or what you have in mind..." required />
        </label>

        <div class="actions">
          <button class="btn" type="submit" :disabled="loading">
            <span v-if="!loading">Send Message</span>
            <span v-else>Sending…</span>
          </button>
          <p v-if="notice && notice.type === 'ok'" class="notice ok">Message sent! I'll get back to you soon.</p>
          <p v-else-if="notice && notice.type === 'err'" class="notice err">Could not send your message. Please try again in a few minutes.</p>
        </div>

        <p v-if="!endpointConfigured" class="config-hint">
          Note: configure the <code>VITE_FORMSPREE_ENDPOINT</code> variable with your Formspree URL to enable sending.
        </p>
      </form>

      <div class="meta">
        <p class="email">aleleonmarin01@gmail.com</p>
        <div class="icons">
          <a class="icon" href="https://www.linkedin.com/in/alejandro-le%C3%B3n-mar%C3%ADn-311846245/" target="_blank" rel="noopener noreferrer" aria-label="LinkedIn" v-html="icons.linkedin" />
          <a class="icon" href="https://github.com/AleLeonMarin" target="_blank" rel="noopener noreferrer" aria-label="GitHub" v-html="icons.github" />
         
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { reactive, ref, computed } from 'vue'

const form = reactive({ name: '', email: '', subject: '', message: '' })
const loading = ref(false)
const notice = ref(null)

const endpoint = import.meta.env.VITE_FORMSPREE_ENDPOINT || ''
const endpointConfigured = computed(() => !!endpoint)

async function onSubmit() {
  if (!endpointConfigured.value) {
    notice.value = { type: 'err' }
    return
  }
  if (!form.name || !form.email || !form.message) {
    notice.value = { type: 'err' }
    return
  }
  loading.value = true
  notice.value = null
  try {
    const res = await fetch(endpoint, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Accept': 'application/json',
      },
      body: JSON.stringify({
        name: form.name,
        email: form.email,
        subject: form.subject,
        message: form.message,
      }),
    })
    if (res.ok) {
      notice.value = { type: 'ok' }
      form.name = ''
      form.email = ''
      form.subject = ''
      form.message = ''
    } else {
      notice.value = { type: 'err' }
    }
  } catch (e) {
    notice.value = { type: 'err' }
  } finally {
    loading.value = false
  }
}

const icons = {
  linkedin: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M4.98 3.5C4.98 4.88 3.86 6 2.5 6C1.12 6 0 4.88 0 3.5C0 2.12 1.12 1 2.5 1C3.86 1 4.98 2.12 4.98 3.5ZM0.22 8.98H4.78V24H0.22V8.98ZM8.44 8.98H12.82V11.04H12.88C13.5 9.86 15.1 8.62 17.42 8.62C22.22 8.62 23 11.78 23 16.02V24H18.44V16.96C18.44 15.2 18.4 12.94 16 12.94C13.56 12.94 13.2 14.86 13.2 16.82V24H8.64V8.98H8.44Z" fill="#9CA3AF"/></svg>`,
  github: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12 .5C5.73.5.98 5.24.98 11.5c0 4.85 3.14 8.96 7.5 10.41.55.1.75-.24.75-.53 0-.26-.01-1.12-.02-2.03-3.05.66-3.69-1.3-3.69-1.3-.5-1.26-1.22-1.6-1.22-1.6-.99-.68.08-.66.08-.66 1.1.08 1.68 1.13 1.68 1.13.98 1.68 2.57 1.2 3.2.92.1-.71.38-1.2.68-1.48-2.43-.28-4.98-1.21-4.98-5.4 0-1.19.43-2.16 1.12-2.92-.11-.28-.49-1.42.1-2.96 0 0 .93-.3 3.05 1.12.89-.25 1.84-.38 2.8-.38.95 0 1.9.13 2.79.38 2.12-1.43 3.05-1.12 3.05-1.12.59 1.54.21 2.68.1 2.96.7.76 1.12 1.73 1.12 2.92 0 4.2-2.56 5.12-4.99 5.39.39.34.74 1.01.74 2.04 0 1.47-.01 2.65-.01 3.01 0 .29.2.64.76.53 4.35-1.46 7.49-5.56 7.49-10.41C23.02 5.24 18.27.5 12 .5Z" fill="#9CA3AF"/></svg>`,
  x: `<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M18.244 2H21.5l-7.5 8.573L23 22h-6.91l-5.41-6.68L4.5 22H1.244l8.156-9.326L1 2h7.09l4.908 6.03L18.244 2Zm-1.213 18h2.087L7.03 4H4.883L17.03 20Z" fill="#9CA3AF"/></svg>`
}
</script>

<style scoped>
.contact {
  background: #0a0a0a;
  /* Fill viewport minus fixed header height and center vertically */
  min-height: calc(100vh - 80px);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 6rem 0 7rem;
  text-align: center;
  /* Ensure anchor navigation accounts for the fixed header */
  scroll-margin-top: 90px;
}

.title {
  color: #e5e7eb;
  font-size: 2.25rem;
  line-height: 1.2;
  font-weight: 800;
  letter-spacing: -0.02em;
}

.subtitle {
  color: #9ca3af;
  margin: 0.9rem auto 2rem;
  max-width: 52rem;
  font-size: 1.05rem;
}

.form {
  margin: 0 auto;
  max-width: 48rem;
  background: #0f0f0f;
  border: 1px solid #1f1f1f;
  border-radius: 14px;
  padding: 1.25rem;
  text-align: left;
}

.row {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}

@media (min-width: 720px) {
  .row { grid-template-columns: 1fr 1fr; }
}

.field { display: flex; flex-direction: column; gap: 0.45rem; }
.field span { color: #9ca3af; font-size: 0.9rem; }
.field input,
.field textarea {
  background: #0a0a0a;
  color: #e5e7eb;
  border: 1px solid #1f1f1f;
  border-radius: 10px;
  padding: 0.8rem 0.9rem;
  outline: none;
}
.field input:focus,
.field textarea:focus { border-color: #00d4aa; box-shadow: 0 0 0 3px rgba(0,212,170,0.15); }

.field.full { margin-top: 1rem; }

.actions {
  display: flex; align-items: center; gap: 1rem; flex-wrap: wrap; margin-top: 1rem;
}

.btn {
  background: #00d4aa;
  color: #0a0a0a;
  font-weight: 700;
  border: 1px solid #0f2c2a;
  padding: 0.75rem 1.1rem;
  border-radius: 10px;
  cursor: pointer;
}
.btn[disabled] { opacity: 0.6; cursor: not-allowed; }

.notice { font-size: 0.95rem; }
.notice.ok { color: #34d399; }
.notice.err { color: #f87171; }

.config-hint { color: #9ca3af; font-size: 0.9rem; margin-top: 0.5rem; }
.config-hint code { background: #0f0f0f; padding: 0.1rem 0.35rem; border-radius: 6px; border: 1px solid #1f1f1f; }

.meta { margin-top: 2.25rem; }
.email { color: #9ca3af; }
.icons { display: flex; justify-content: center; gap: 1.25rem; margin-top: 1.25rem; }
.icon { display: inline-flex; opacity: 0.9; }
.icon:hover { opacity: 1; }
</style>
