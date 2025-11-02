<script setup>
// Footer с логотипом, навигацией, соцсетями и контактами
</script>

<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__top">
        <div class="footer__brand">
          <div class="footer__logo">CoDe</div>
          <p class="footer__tagline">Школа программирования</p>
        </div>

        <nav class="footer__nav">
          <a href="#" class="footer__link">Чему вы научитесь</a>
          <a href="#" class="footer__link">Процесс обучения</a>
          <a href="#" class="footer__link">Стоимость</a>
          <a href="#" class="footer__link">Контакты</a>
          <a href="#" class="footer__link">Регистрация</a>
        </nav>

        <div class="footer__contacts">
          <a href="tel:+79999999999" class="footer__phone">+7 (999) 999 99 99</a>
          <a href="mailto:info@code.ru" class="footer__email">info@code.ru</a>
        </div>
      </div>

      <div class="footer__socials">
        <!-- Social icons placeholder -->
      </div>

      <div class="footer__bottom">
        <p class="footer__copyright">© 2023 — Все права защищены</p>
        <div class="footer__legal">
          <a href="#" class="footer__link">Пользовательское соглашение</a>
          <a href="#" class="footer__link">Политика конфиденциальности</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  margin-top: 600px; /* Отступ сверху, чтобы не заезжать под баннер */
  padding: 60px 0 30px;
  background: #2a2a2a;
  color: white;
}

.footer__top {
  display: flex;
  flex-wrap: wrap;
  gap: 40px;
  margin-bottom: 40px;
}

.footer__logo {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 10px;
}

.footer__nav {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.footer__link {
  color: #ccc;
  transition: color var(--transition-fast);
}

.footer__link:hover {
  color: var(--color-blue);
}

.footer__phone,
.footer__email {
  color: var(--color-blue);
  display: block;
  margin-bottom: 10px;
}

.footer__bottom {
  padding-top: 30px;
  border-top: 1px solid #444;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 20px;
}

.footer__legal {
  display: flex;
  gap: 30px;
}

/* Адаптивность */
@media (max-width: 768px) {
  .footer {
    margin-top: 500px; /* Меньший отступ на мобильных */
    padding: 40px 0 20px;
  }

  .footer__top {
    flex-direction: column;
    gap: 30px;
  }

  .footer__nav {
    flex-direction: row;
    flex-wrap: wrap;
    gap: 20px;
  }

  .footer__bottom {
    flex-direction: column;
    text-align: center;
  }

  .footer__legal {
    justify-content: center;
    flex-wrap: wrap;
  }
}
</style>
