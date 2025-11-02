<script setup>
// Секция с карточками преимуществ
const advantages = [
  {
    id: 1,
    title: 'Огромное количество практики',
    description: 'Более 500 самостоятельных заданий и 20 полноценных больших проектов',
  },
  {
    id: 2,
    title: 'Современные методики обучения',
    description: 'Спиральное обучение: погружаемся в материал постепенно, виток за витком',
  },
  {
    id: 3,
    title: 'Простое и понятное изложение',
    description: 'Вместо заумных терминов – примеры из реального мира',
  },
  {
    id: 4,
    title: 'Гибкий график занятий',
    description: 'Учитесь в любое время в удобном для вас темпе',
  },
  {
    id: 5,
    title: 'Прямая связь с опытными программистами',
    description: 'Задавайте вопросы и отправляйте свой код на проверку',
  },
  {
    id: 6,
    title: 'Оплата небольшими частями',
    description: 'Платите только за тот материал, который сейчас изучаете, а не за весь курс сразу',
  },
  {
    id: 7,
    title: 'Быстрый и легкий возврат',
    description: 'Если передумаете учиться – вернем деньги за 3 рабочих дня',
  },
]
</script>

<template>
  <section class="advantages">
    <div class="container">
      <h2 class="advantages__title">Обучение в CoDe – это удобно и результативно</h2>
      <div class="advantages__grid">
        <div v-for="advantage in advantages" :key="advantage.id" class="advantage-card">
          <div class="advantage-card__icon">
            <!-- Icon placeholder -->
          </div>
          <h3 class="advantage-card__title">{{ advantage.title }}</h3>
          <p class="advantage-card__description">{{ advantage.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.advantages {
  padding: 80px 0;
}

.advantages__title {
  text-align: center;
  margin-bottom: 40px;
  font-size: 32px;
}

.advantages__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.advantage-card {
  padding: 40px 20px;
  background: white;
  border-radius: 12px;
  border: 1px solid #e0e0e0;
}

.advantage-card__title {
  margin: 20px 0 10px;
  font-size: 18px;
}

.advantage-card__description {
  color: #666;
  font-size: 14px;
}
</style>
