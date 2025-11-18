<script setup>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import About from './components/About.vue';
import Education from './components/Education.vue';
import Projects from './components/Projects.vue';
import Contact from './components/Contact.vue';
</script>

<template>
  <div class="app">
    <Header />
    <main class="main-content">
      <Main />
    </main>
    <About />
    <Education />
    <Projects />
    <Contact />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

.app {
  width: 100%;
  min-height: 100vh;
  background-color: #0a0a0a;
  margin: 0;
  padding: 0;
}

.main-content {
  width: 100%;
  padding-top: 80px;
  margin: 0;
}
</style>