<template>
  <section class="gallery">
    <div class="gallery__grid">
      <div class="gallery__item gallery__item--large">
        <a :href="gallery1" data-fancybox="gallery" data-caption="Gallery 1">
          <img :src="gallery1" alt="Gallery 1" />
        </a>
      </div>
      <div class="gallery__item">
        <a :href="gallery2" data-fancybox="gallery" data-caption="Gallery 2">
          <img :src="gallery2" alt="Gallery 2" />
        </a>
      </div>
      <div class="gallery__item">
        <a :href="gallery3" data-fancybox="gallery" data-caption="Gallery 3">
          <img :src="gallery3" alt="Gallery 3" />
        </a>
      </div>
      <div class="gallery__item">
        <a :href="gallery4" data-fancybox="gallery" data-caption="Gallery 4">
          <img :src="gallery4" alt="Gallery 4" />
        </a>
      </div>
      <div class="gallery__item">
        <a :href="gallery5" data-fancybox="gallery" data-caption="Gallery 5">
          <img :src="gallery5" alt="Gallery 5" />
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, onBeforeUnmount } from 'vue'
import { Fancybox } from '@fancyapps/ui'
import '@fancyapps/ui/dist/fancybox/fancybox.css'
import gallery1 from '@/assets/photo-gallery-1.png'
import gallery2 from '@/assets/photo-gallery-2.png'
import gallery3 from '@/assets/photo-gallery-3.png'
import gallery4 from '@/assets/photo-gallery-4.png'
import gallery5 from '@/assets/photo-gallery-5.png'

onMounted(() => {
  const images = [
    { src: gallery1, caption: 'Gallery 1' },
    { src: gallery2, caption: 'Gallery 2' },
    { src: gallery3, caption: 'Gallery 3' },
    { src: gallery4, caption: 'Gallery 4' },
    { src: gallery5, caption: 'Gallery 5' },
  ]

  // Создаем элементы галереи с background-image
  const galleryItems = document.querySelectorAll("[data-fancybox='gallery']")
  galleryItems.forEach((item, index) => {
    item.addEventListener('click', (e) => {
      e.preventDefault()

      Fancybox.show(
        images.map((img) => ({
          html: `
            <div class="fancybox-outer-wrapper">
              <div class="fancybox-bg-image" style="background-image: url('${img.src}');"></div>
            </div>
          `,
          caption: img.caption,
        })),
        {
          startIndex: index,
        },
      )
    })
  })
})

onBeforeUnmount(() => {
  Fancybox.destroy()
})
</script>

<style scoped>
.gallery {
  width: calc(100% - 48px);
  max-width: 1160px;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 60px;
  opacity: 1;
}

.gallery__grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  grid-template-rows: 275.5px 275.5px;
  gap: 20px;
}

.gallery__item {
  background: #ddd;
  border-radius: 30px;
  overflow: hidden;
}

.gallery__item--large {
  grid-column: 1 / 2;
  grid-row: 1 / span 2;
  height: 100%;
}

.gallery__item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

@media (max-width: 1199px) {
  .gallery__grid {
    grid-template-columns: 275.5px 275.5px;
    grid-template-rows: none;
    grid-auto-rows: 275.5px;
    justify-content: center;
    gap: 10px;
  }
  .gallery__item--large {
    grid-column: 1 / -1;
    grid-row: 1 / span 2;
    height: 100%;
  }
  .gallery__item img {
    height: 100%;
  }
}

@media (max-width: 859px) {
  .gallery__grid {
    grid-template-columns: 145px 145px;
    grid-template-rows: none;
    grid-auto-rows: 145px;
    justify-content: center;
  }
  .gallery__item--large {
    grid-column: 1 / -1;
    grid-row: 1 / span 2;
    height: 100%;
  }
  .gallery__item img {
    height: 100%;
  }
}
</style>

<style>
.fancybox__slide {
  padding: 80px 60px 60px 60px !important;
}

.fancybox-outer-wrapper {
  width: 100%;
  height: 100%;
  background: transparent;
  display: flex;
  align-items: center;
  justify-content: center;
}

.fancybox-bg-image {
  width: 100%;
  height: 100%;
  aspect-ratio: 1/1;
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
}

/* Убеждаемся что HTML контент занимает всё пространство */
.fancybox__slide .f-html {
  width: 100%;
  height: 100%;
  padding: 0;
}

@media (max-width: 859px) {
  .fancybox__slide {
    padding: 40px 10px 30px 10px !important;
  }
}
</style>
