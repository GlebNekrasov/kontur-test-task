<template>
  <section class="advantages">
    <h2 class="advantages__title">
      <span>Обучение в CoDe – это</span>
      <span>удобно и результативно</span>
    </h2>
    <div class="advantages__cards">
      <div v-for="advantage in advantagesData" :key="advantage.id" class="advantage-card">
        <div class="advantage-card__icon">
          <img :src="advantage.image" :alt="advantage.title" />
        </div>
        <div class="advantage-card__content">
          <h3 class="advantage-card__title">
            <span v-for="title in advantage.title" :key="title">{{ title }}</span>
          </h3>
          <p class="advantage-card__description">
            <span v-for="description in advantage.description" :key="description">{{
              description
            }}</span>
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import advantage1 from '@/assets/advantage-1.svg'
import advantage2 from '@/assets/advantage-2.svg'
import advantage3 from '@/assets/advantage-3.svg'
import advantage4 from '@/assets/advantage-4.svg'
import advantage5 from '@/assets/advantage-5.svg'
import advantage6 from '@/assets/advantage-6.svg'
import advantage7 from '@/assets/advantage-7.svg'
import advantage1Mobile from '@/assets/advantage-1-small.svg'
import advantage2Mobile from '@/assets/advantage-2-small.svg'
import advantage3Mobile from '@/assets/advantage-3-small.svg'
import advantage4Mobile from '@/assets/advantage-4-small.svg'
import advantage5Mobile from '@/assets/advantage-5-small.svg'
import advantage6Mobile from '@/assets/advantage-6-small.svg'
import advantage7Mobile from '@/assets/advantage-7-small.svg'

const isMobile = ref(false)

const updateBreakpoints = () => {
  isMobile.value = window.matchMedia('(max-width: 859px)').matches
}

const advantagesData = computed(() => {
  return isMobile.value ? advantagesMobile : advantages
})
const advantages = [
  {
    id: 1,
    title: ['Огромное', 'количество практики'],
    description: ['Более 500 самостоятельных', 'заданий и 20 полноценных', 'больших проектов'],
    image: advantage1,
  },
  {
    id: 2,
    title: ['Современные', 'методики обучения'],
    description: ['Спиральное обучение:', 'погружаемся в материал', 'постепенно, виток за витком'],
    image: advantage2,
  },
  {
    id: 3,
    title: ['Простое и понятное', 'изложение'],
    description: ['Вместо заумных', 'терминов – примеры', 'из реального мира'],
    image: advantage3,
  },
  {
    id: 4,
    title: ['Гибкий график', 'занятий'],
    description: ['Учитесь в любое', 'время в удобном', 'для вас темпе'],
    image: advantage4,
  },
  {
    id: 5,
    title: ['Прямая связь с опытными', 'программистами'],
    description: ['Задавайте вопросы', 'и отправляйте свой код', 'на проверку'],
    image: advantage5,
  },
  {
    id: 6,
    title: ['Оплата небольшими', 'частями'],
    description: [
      'Платите только за тот материал,',
      'который сейчас изучаете,',
      'а не за весь курс сразу',
    ],
    image: advantage6,
  },
  {
    id: 7,
    title: ['Быстрый и легкий', 'возврат'],
    description: ['Если передумаете учиться –', 'вернем деньги за 3', 'рабочих дня'],
    image: advantage7,
  },
]

const advantagesMobile = [
  {
    id: 1,
    title: ['Огромное', 'количество', 'практики'],
    description: ['Более 500 самостоятельных', 'заданий и 20 полноценных', 'больших проектов'],
    image: advantage1Mobile,
  },
  {
    id: 5,
    title: ['Прямая связь', 'с опытными', 'программистами'],
    description: ['Задавайте вопросы', 'и отправляйте свой', 'код на проверку'],
    image: advantage5Mobile,
  },
  {
    id: 3,
    title: ['Простое и понятное', 'изложение'],
    description: ['Вместо заумных терминов –', 'примеры из реального мира'],
    image: advantage3Mobile,
  },
  {
    id: 4,
    title: ['Гибкий график', 'занятий'],
    description: ['Учитесь в любо время и', 'в удобном для вас темпе'],
    image: advantage4Mobile,
  },
  {
    id: 2,
    title: ['Современные', 'методики обучения'],
    description: [
      'Спиральное обучение:',
      'на каждом витке вы',
      'узнаете что-то новое об',
      'уже знакомых вещах',
    ],
    image: advantage2Mobile,
  },
  {
    id: 6,
    title: ['Гибкая оплата', 'частями'],
    description: [
      'Платите только за тот',
      'материао, который',
      'изучаете прямо сейчас, а',
      'не за весь курс сразу',
    ],
    image: advantage6Mobile,
  },
  {
    id: 7,
    title: ['Быстрый и легкий возврат'],
    description: ['Если передумаете учиться –', 'вернем деньги за 3 рабочих дня'],
    image: advantage7Mobile,
  },
]

onMounted(() => {
  updateBreakpoints()
  window.addEventListener('resize', updateBreakpoints)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateBreakpoints)
})
</script>

<style scoped>
.advantages {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 34px;
  width: calc(100% - 48px);
  max-width: 1161px;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 60px;
  opacity: 1;
}

.advantages__title {
  display: block;
  text-align: center;
  font-size: 46px;
  line-height: 46px;
  font-weight: 600;
}

.advantages__title span {
  display: block;
}

.advantages__cards {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  gap: 27px;
  row-gap: 27px;
}

.advantage-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
  gap: 18px;
  width: 270px;
  height: 254px;
  padding-bottom: 31px;
  background: #eaf2f5;
  border-radius: 30px;
}

.advantage-card__content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
  gap: 10px;
}

.advantage-card__title {
  font-size: 16px;
  line-height: 18.5px;
  font-weight: 400;
  text-align: center;
}

.advantage-card__title span {
  display: block;
}

.advantage-card__description {
  font-size: 13px;
  line-height: 15px;
  font-weight: 400;
  text-align: center;
}

.advantage-card__description span {
  display: block;
}

@media (max-width: 1199px) {
  .advantages__title {
    font-size: 36px;
    line-height: 36px;
  }
}

@media (max-width: 1023px) {
  .advantages__title {
    font-size: 24px;
    line-height: 24px;
  }
}

@media (max-width: 859px) {
  .advantages {
    width: calc(100% - 16px);
    margin-bottom: 30px;
    gap: 24px;
  }

  .advantages__title {
    font-size: 24px;
    font-weight: 500;
    line-height: 26px;
  }

  .advantages__cards {
    align-items: stretch;
    gap: 10px;
    row-gap: 10px;
  }

  .advantage-card {
    gap: 10px;
    width: auto;
    flex-basis: calc((100% - 10px) / 2);
    max-width: 270px;
    min-width: 145px;
    height: auto;
    padding-bottom: 19px;
    padding-top: 25px;
    border-radius: 20px;
  }

  .advantages__cards > .advantage-card:last-child {
    flex-basis: 100%;
    max-width: 550px;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 20px;
  }

  .advantage-card__content {
    gap: 5px;
  }

  .advantage-card__title {
    font-size: 12px;
    line-height: 12px;
  }

  .advantage-card__description {
    font-size: 9px;
    line-height: 12px;
  }
}
</style>
