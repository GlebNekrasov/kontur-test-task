<template>
  <section class="info">
    <div class="info__block">
      <div class="info__image">
        <img :src="info1Image" alt="Info 1" />
      </div>

      <div class="info__content">
        <h2 class="info__title">Помощь и поддержка</h2>
        <p class="info__text text-1">
          Если в процессе обучения возникнут сложности, вы всегда сможете задать вопрос своему
          наставнику.
        </p>
        <p class="info__text text-2">
          Раз в несколько уроков вы будете получать большое задание, которое нужно будет сдавать на
          проверку код-ревьюеру. Он внимательно изучит ваш код, найдет ошибки и поможет вам стать
          лучше.
        </p>
      </div>
    </div>

    <div class="info__block info__block--mobile-reverse">
      <div class="info__content">
        <h2 class="info__title">Методика обучения</h2>
        <p class="info__text text-3">
          Весь учебный материал структурирован по принципу «спирального обучения». Сначала вы
          получаете базовые знания, а затем на каждом витке спирали углубляетесь в изученные темы,
          доводя их понимание до совершенства. Такой подход упрощает обучение и гарантирует, что вы
          не пропустите ничего важного.
        </p>
      </div>

      <div class="info__image">
        <img :src="info2Image" alt="Info 2" />
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import info1 from '@/assets/photo-info-1.png'
import info2 from '@/assets/photo-info-2.png'
import info1Mobile from '@/assets/photo-info-1-mobile.png'
import info2Mobile from '@/assets/photo-info-2-mobile.png'

const isMobile = ref(false)

const updateBreakpoints = () => {
  isMobile.value = window.matchMedia('(max-width: 859px)').matches
}

const info1Image = computed(() => {
  return isMobile.value ? info1Mobile : info1
})
const info2Image = computed(() => {
  return isMobile.value ? info2Mobile : info2
})

onMounted(() => {
  updateBreakpoints()
  window.addEventListener('resize', updateBreakpoints)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateBreakpoints)
})
</script>

<style scoped>
.info {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  gap: 32px;
  width: calc(100% - 48px);
  max-width: 1160px;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 60px;
  opacity: 1;
}

.info__block {
  display: flex;
  flex-direction: row;
  align-items: stretch;
  justify-content: space-between;
  gap: 32px;
  width: 100%;
}

.info__image {
  border-radius: 40px;
}

.info__content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 18px;
  flex-shrink: 1;
  flex-grow: 1;
  flex-basis: 360px;
  max-width: 730px;
  padding-left: 100px;
  padding-right: 50px;
  border-radius: 40px;
  background: #eaf2f5;
}

.info__title {
  font-size: 32px;
  font-weight: 400;
  line-height: 30px;
}

.info__text {
  font-size: 16px;
  font-weight: 400;
  line-height: 25px;
}

.text-1 {
  max-width: 435px;
}

.text-2 {
  max-width: 549px;
}

.text-3 {
  max-width: 502px;
}

@media (max-width: 1199px) {
  .info__content {
    padding-left: 50px;
    padding-right: 25px;
  }

  .info__title {
    font-size: 28px;
    line-height: 26px;
  }
}

@media (max-width: 1023px) {
  .info__text {
    font-size: 14px;
    line-height: 20px;
  }

  .info__title {
    font-size: 24px;
    line-height: 22px;
  }
}

@media (max-width: 859px) {
  .info {
    display: flex;
    gap: 12px;
    width: 300px;
    margin-bottom: 24px;
  }

  .info__block {
    flex-direction: column;
    align-items: center;
    gap: 12px;
  }

  .info__block--mobile-reverse {
    flex-direction: column-reverse;
  }

  .info__content {
    justify-content: center;
    gap: 18px;
    flex-basis: content;
    width: 100%;
    padding-left: 20px;
    padding-top: 30px;
    padding-bottom: 30px;
    border-radius: 30px;
  }

  .info__title {
    font-size: 20px;
    line-height: 19px;
  }

  .info__text {
    font-size: 12px;
    line-height: 17px;
  }

  .text-1 {
    max-width: 220px;
  }

  .text-2 {
    max-width: 257px;
  }

  .text-3 {
    max-width: 245px;
  }
}
</style>
