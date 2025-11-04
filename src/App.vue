<template>
  <div class="app">
    <div class="container">
      <AppHeader />
      <main>
        <HeroSection />
        <AdvantagesSection />
        <InfoSection />
        <GallerySection />
        <MapSection />
        <AppFooter />
      </main>
    </div>
    <CallbackModal />
  </div>
</template>

<script setup>
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import CallbackModal from './components/CallbackModal.vue'
import AdvantagesSection from './components/AdvantagesSection.vue'
import InfoSection from './components/InfoSection.vue'
import GallerySection from './components/GallerySection.vue'
import MapSection from './components/MapSection.vue'
import AppFooter from './components/AppFooter.vue'
</script>

<style scoped>
.app {
  min-height: 100vh;
  background-color: var(--color-background);
}

.container {
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  min-height: 100vh;
  padding-top: 24px;
  padding-bottom: 26px;
}

@media (max-width: 768px) {
  .container {
    padding-top: 16px;
  }
}
</style>
