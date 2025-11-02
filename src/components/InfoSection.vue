<script setup>
// Секция с информационными блоками (помощь и поддержка, методика обучения)
</script>

<template>
  <section class="info">
    <div class="container">
      <div class="info__block">
        <div class="info__image">
          <!-- Image placeholder -->
        </div>
        <div class="info__content">
          <h2 class="info__title">Помощь и поддержка</h2>
          <p class="info__text">
            Если в процессе обучения возникнут сложности, вы всегда сможете задать вопрос своему
            наставнику.
          </p>
          <p class="info__text">
            Раз в несколько уроков вы будете получать большое задание, которое нужно будет сдавать
            на проверку код-ревьюеру. Он внимательно изучит ваш код, найдет ошибки и поможет вам
            стать лучше.
          </p>
        </div>
      </div>

      <div class="info__block info__block--reverse">
        <div class="info__image">
          <!-- Image placeholder -->
        </div>
        <div class="info__content">
          <h2 class="info__title">Методика обучения</h2>
          <p class="info__text">
            Весь учебный материал структурирован по принципу «спирального обучения». Сначала вы
            получаете базовые знания, а затем на каждом витке спирали углубляетесь в изученные темы,
            доводя их понимание до совершенства. Такой подход упрощает обучение и гарантирует, что
            вы не пропустите ничего важного.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.info {
  padding: 80px 0;
  background: #f9f9f9;
}

.info__block {
  margin-bottom: 60px;
}

.info__title {
  font-size: 28px;
  margin-bottom: 20px;
}

.info__text {
  margin-bottom: 15px;
  color: #333;
  line-height: 1.6;
}

.info__image {
  width: 100%;
  height: 300px;
  background: #ddd;
  border-radius: 12px;
  margin-bottom: 20px;
}
</style>
