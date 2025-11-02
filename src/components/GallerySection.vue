<script setup>
// Секция с галереей фотографий
</script>

<template>
  <section class="gallery">
    <div class="container">
      <div class="gallery__grid">
        <div class="gallery__item gallery__item--large">
          <!-- Large image placeholder -->
        </div>
        <div class="gallery__item">
          <!-- Image placeholder -->
        </div>
        <div class="gallery__item">
          <!-- Image placeholder -->
        </div>
        <div class="gallery__item">
          <!-- Image placeholder -->
        </div>
        <div class="gallery__item">
          <!-- Image placeholder -->
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.gallery {
  padding: 80px 0;
}

.gallery__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.gallery__item {
  height: 250px;
  background: #ddd;
  border-radius: 12px;
}

.gallery__item--large {
  grid-column: span 2;
  height: 520px;
}

@media (max-width: 767px) {
  .gallery__item--large {
    grid-column: span 1;
    height: 250px;
  }
}
</style>
