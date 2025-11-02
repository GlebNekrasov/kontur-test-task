<template>
  <section class="hero">
    <Swiper
      :modules="swiperModules"
      :autoplay="{
        delay: 500000,
        disableOnInteraction: false,
      }"
      :pagination="{
        clickable: true,
        bulletClass: 'hero__bullet',
        bulletActiveClass: 'hero__bullet--active',
      }"
      :navigation="navigationConfig"
      :loop="true"
      class="hero__swiper"
    >
      <SwiperSlide v-for="slide in slides" :key="slide.id" class="hero__slide">
        <div class="hero__content">
          <div
            class="hero__content-text"
            :style="{ marginBottom: slide.id !== 1 ? '36px' : isMobile ? '24px' : '16px' }"
          >
            <h1 class="hero__title">
              <span v-html="slide.title"></span>
            </h1>
            <div class="hero__divider" aria-hidden="true"></div>
            <p class="hero__subtitle" v-html="slide.subtitle"></p>
          </div>
          <ActionButton :text="slide.buttonText" @click="openModal" />
        </div>
        <div class="hero__background" :style="{ backgroundColor: slide.backgroundColor }">
          <div class="hero__circles">
            <picture>
              <source media="(max-width: 859px)" :srcset="bannerCirclesSmallMobile" />
              <source media="(max-width: 1199px)" :srcset="bannerCirclesSmall" />
              <img :src="bannerCircles" alt="Background circles" />
            </picture>
          </div>
          <div class="hero__illustration">
            <img :src="slide.backgroundImage" :alt="slide.title" />
          </div>
        </div>
      </SwiperSlide>
    </Swiper>

    <!-- Custom SVG navigation with circular background -->
    <button
      v-if="slides.length > 1"
      class="hero__nav hero__nav--prev"
      type="button"
      aria-label="Prev slide"
    >
      <span class="hero__nav-icon">
        <img :src="arrowLeft" alt="" />
      </span>
    </button>
    <button
      v-if="slides.length > 1"
      class="hero__nav hero__nav--next"
      type="button"
      aria-label="Next slide"
    >
      <span class="hero__nav-icon">
        <img :src="arrowRight" alt="" />
      </span>
    </button>

    <CallbackModal ref="modalRef" />
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Pagination, Navigation } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/pagination'
import 'swiper/css/navigation'

// Импорт модального окна
import CallbackModal from './CallbackModal.vue'
import ActionButton from './ui/ActionButton.vue'

// Импорт изображений для корректной работы в продакшене
import banner1 from '@/assets/banner-1.svg'
import banner1Small from '@/assets/banner-1-small.svg'
import banner1SmallMobile from '@/assets/banner-1-small-mobile.svg'
import banner2 from '@/assets/banner-2.svg'
import banner2Small from '@/assets/banner-2-small.svg'
import banner3 from '@/assets/banner-3.svg'
import banner3Small from '@/assets/banner-3-small.svg'
import bannerCircles from '@/assets/banner-circles.svg'
import bannerCirclesSmall from '@/assets/banner-circles-small.svg'
import bannerCirclesSmallMobile from '@/assets/banner-circles-small-mobile.svg'
import arrowLeft from '@/assets/arrow-left.svg'
import arrowRight from '@/assets/arrow-right.svg'

const modalRef = ref(null)

const openModal = () => {
  if (modalRef.value) {
    modalRef.value.openModal()
  }
}

// Базовые данные слайдов
const baseSlides = [
  {
    id: 1,
    title:
      "Школа <span class='hero__color'>{</span><span class='hero__bold'>программирования</span><span class='hero__color'>}</span><br/>для тех, кому нужны<br/>реальные навыки,<br/>а не просто сертификат",
    subtitle: 'Закажите звонок, и наш специалист свяжется с вами в ближайшее время',
    buttonText: 'Заказать звонок',
    backgroundImage: banner1,
    backgroundImageSmall: banner1Small,
    backgroundImageSmallMobile: banner1SmallMobile,
    backgroundColor: '#eaf2f5',
  },
  {
    id: 2,
    title: 'Обучение<br/>через практику',
    subtitle:
      'Всё, что вы узнали, вы тут же начинаете применять на практике. Вы сразу видите результаты своего труда.',
    buttonText: 'Заказать звонок',
    backgroundImage: banner2,
    backgroundImageSmall: banner2Small,
    backgroundColor: '#eaf2f5',
  },
  {
    id: 3,
    title: 'Весь материал разбит на<br/>небольшие уроки',
    subtitle:
      'Теория и практика подаются маленькими порциями. Так вам будет легче усваивать новые знания.',
    buttonText: 'Заказать звонок',
    backgroundImage: banner3,
    backgroundImageSmall: banner3Small,
    backgroundColor: '#eaf2f5',
  },
]

// Отслеживание размера экрана
const isTablet = ref(false)
const isMobile = ref(false)

const updateBreakpoints = () => {
  isTablet.value = window.matchMedia('(max-width: 1199px)').matches
  isMobile.value = window.matchMedia('(max-width: 859px)').matches
}

onMounted(() => {
  updateBreakpoints()
  window.addEventListener('resize', updateBreakpoints)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateBreakpoints)
})

// Динамические слайды в зависимости от размера экрана
const slides = computed(() => {
  if (isMobile.value) {
    // Для мобильных: только первый слайд с banner-1-small-mobile.svg
    return [
      {
        ...baseSlides[0],
        backgroundImage: baseSlides[0].backgroundImageSmallMobile,
        subtitle: 'Пройдите тестирование, чтобы получить доступ к бесплатным вводным урокам',
        title:
          "Школа<br/><span class='hero__italic'>программирования</span><br/>для тех, кому нужны<br/>реальные навыки,<br/>а не просто сертификат",
      },
    ]
  } else if (isTablet.value) {
    // Для планшетов: все слайды с версиями -small
    return baseSlides.map((slide) => ({
      ...slide,
      backgroundImage: slide.backgroundImageSmall || slide.backgroundImage,
    }))
  } else {
    // Для десктопа: оригинальные слайды
    return baseSlides
  }
})

const swiperModules = [Autoplay, Pagination, Navigation]

// Navigation только если больше 1 слайда
const navigationConfig = computed(() => {
  return slides.value.length > 1
    ? { prevEl: '.hero__nav--prev', nextEl: '.hero__nav--next' }
    : false
})
</script>

<style scoped>
.hero {
  height: 481px;
  width: calc(100% - 48px);
  max-width: 1160px;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 60px;
  overflow: hidden;
  background: #eaf2f5;
  border-radius: 48px;
  position: relative;
}

.hero__swiper {
  width: 100%;
  height: 100% !important;
}

.hero__content {
  position: absolute;
  bottom: 56px;
  z-index: 2;
  width: 100%;
  padding-left: 98px;
}

.hero__content-text {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  gap: 24px;
}

.hero__title {
  width: 638px;
  font-family: 'Gilroy', sans-serif;
  font-weight: 500;
  font-size: 46px;
  line-height: 100%;
  color: #22253b;
}

.hero__divider {
  width: 365px;
  height: 1px;
  background: #dedede;
}

.hero__subtitle {
  width: 365px;
  font-family: 'Gilroy', sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 23px;
  color: #22253b;
}

.hero__slide {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

.hero__highlight {
  color: var(--color-blue);
}

:deep(.hero__color) {
  color: var(--color-orange);
  font-weight: 400;
}

:deep(.hero__bold) {
  font-weight: 700;
}

:deep(.hero__italic) {
  font-style: italic;
  font-weight: 600;
}

.hero__background {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  overflow: hidden;
  pointer-events: none;
}

/* Концентрические круги */
.hero__circles {
  position: absolute;
  top: 0;
  right: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  overflow: hidden;
}

.hero__circles img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover; /* cover to eliminate visual gaps */
  object-position: right center;
}

/* Основная иллюстрация */
.hero__illustration {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 2;
}

.hero__illustration img {
  position: absolute;
  top: 80px;
  right: 75px;
  height: 320px;
  object-fit: contain;
  object-position: right center;
}

/* Swiper Navigation */
.hero__nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 37px;
  height: 37px;
  border: none;
  border-radius: 50%;
  background: transparent;
  display: grid;
  place-items: center;
  cursor: pointer;
  z-index: 5;
  outline: none;
  box-shadow: none;
}

.hero__nav--prev {
  left: 25px;
  background: var(--color-orange);
}

.hero__nav--next {
  right: 25px;
  background: #ffffff;
  box-shadow: none;
}

.hero__nav--prev:hover {
  background: var(--color-blue);
}
.hero__nav--next:hover {
  background: #fafafa;
}

.hero__nav:focus-visible {
  outline: 2px solid #22253b;
  outline-offset: 2px;
}

.hero__nav-icon {
  position: relative;
  width: 18px;
  height: 18px;
}

.hero__nav-icon img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: contain;
  pointer-events: none;
}

/* Icons have desired colors in SVG assets; do not alter with filters */
.hero__nav--prev .hero__nav-icon img {
  filter: none;
}
.hero__nav--next .hero__nav-icon img {
  filter: none;
}

/* Swiper Pagination */
:deep(.swiper-pagination) {
  bottom: 40px;
}

.hero__bullet {
  width: 12px;
  height: 12px;
  background: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  margin: 0 6px;
  transition: all var(--transition-fast);
}

.hero__bullet--active {
  background: var(--color-blue);
  transform: scale(1.2);
}

/* Tablet */
@media (max-width: 1199px) {
  .hero__title {
    width: 485px;
    font-size: 36px;
  }
}

@media (max-width: 1023px) {
  .hero__title {
    width: 485px;
    font-size: 24px;
  }

  .hero__subtitle {
    width: 280px;
    font-size: 12px;
  }

  .hero__divider {
    width: 280px;
  }
}

/* Mobile */
@media (max-width: 859px) {
  .hero {
    height: 609px;
    width: calc(100% - 26px);
    margin-bottom: 32px;
  }

  .hero__slide {
    align-items: flex-start;
  }

  .hero__content {
    position: relative;
    padding-left: 0;
    padding-top: 32px;
    bottom: auto;
  }

  .hero__content-text {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    gap: 16px;
    width: 100%;
  }

  .hero__title {
    font-size: 24px;
    line-height: 24px;
    width: 100%;
    text-align: center;
  }

  .hero__divider {
    max-width: 280px;
  }

  .hero__subtitle {
    font-size: 12px;
    line-height: 18px;
    text-align: center;
    max-width: 270px;
  }

  :deep(.action-button) {
    margin-left: auto;
    margin-right: auto;
  }

  .hero__circles img {
    object-position: center center;
  }

  .hero__illustration img {
    position: absolute;
    top: 344px;
    right: calc(50% - 109.5px);
    height: 219px;
    object-position: center center;
  }
}
</style>
