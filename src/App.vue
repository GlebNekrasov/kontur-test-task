<script setup>
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import CallbackModal from './components/CallbackModal.vue'
</script>

<template>
  <div class="app">
    <div class="container">
      <AppHeader />
      <main>
        <HeroSection />
      </main>
    </div>
    <CallbackModal />
  </div>
</template>

<style scoped>
.app {
  min-height: 100vh;
  background-color: #f9f8fd;
}

.container {
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  min-height: 100vh;
  padding-top: 24px;
}

/* main {
  flex: 1;
} */

@media (max-width: 768px) {
  .container {
    padding-top: 16px;
  }
}
</style>
