<template>
  <footer class="footer">
    <div class="footer__top">
      <div class="footer__brand-container">
        <div class="footer__brand">
          <div class="footer__logo">
            <span class="footer__logo-c">C</span>
            <span class="footer__logo-o">o</span>
            <span class="footer__logo-d">D</span>
            <span class="footer__logo-e">e</span>
          </div>
          <p class="footer__tagline">Школа программирования</p>
        </div>
        <div class="footer__socials">
          <InstagramIcon class="footer__icon" />
          <VkIcon class="footer__icon" />
          <FacebookIcon class="footer__icon" />
          <YoutubeIcon class="footer__icon" />
        </div>
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

    <div class="footer__bottom">
      <p class="footer__copyright">© 2023 — Все права защищены</p>
      <div class="footer__legal">
        <a href="#" class="footer__link">Пользовательское соглашение</a>
        <a href="#" class="footer__link">Политика конфиденциальности</a>
      </div>
    </div>
  </footer>
</template>

<script setup>
import InstagramIcon from '@/components/ui/InstagramIcon.vue'
import VkIcon from '@/components/ui/VkIcon.vue'
import FacebookIcon from '@/components/ui/FacebookIcon.vue'
import YoutubeIcon from '@/components/ui/YoutubeIcon.vue'
</script>

<style scoped>
.footer {
  width: calc(100% - 48px);
  max-width: 1161px;
  margin-left: auto;
  margin-right: auto;
  opacity: 1;
}

.footer__top {
  display: flex;
  flex-wrap: wrap;
  margin-bottom: 52px;
  padding-right: 30px;
}

.footer__brand-container {
  margin-right: auto;
}

.footer__brand {
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  gap: 10px;
  margin-bottom: 37px;
}

.footer__logo {
  font-family: 'Gilroy', sans-serif;
  font-weight: 500;
  font-size: 36px;
  line-height: 1.044;
  padding-top: 3px;
  color: #000000;
}

.footer__logo-c {
  color: var(--color-blue);
}

.footer__logo-d {
  color: var(--color-orange);
}

.footer__tagline {
  max-width: 151px;
  font-family: 'Gilroy', sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 19px;
  color: #8e8e8e;
}

.footer__socials {
  display: flex;
  gap: 16px;
}

.footer__icon {
  color: #22253b;
  transition: color var(--transition-fast);
  cursor: pointer;
}

.footer__icon:hover {
  color: var(--color-orange);
}

.footer__nav {
  display: flex;
  flex-direction: column;
  gap: 25px;
  font-family: 'Gilroy', sans-serif;
  font-size: 13px;
  font-weight: 400;
  line-height: 104.4%;
  color: #22253b;
  padding-top: 4px;
  margin-right: 166px;
}

.footer__link {
  transition: color var(--transition-fast);
}

.footer__link:hover {
  color: var(--color-blue);
}

.footer__contacts {
  display: flex;
  flex-direction: column;
  gap: 3px;
  font-family: 'Gilroy', sans-serif;
}

.footer__phone {
  display: block;
  font-size: 16px;
  font-weight: 400;
  line-height: 23px;
  color: var(--color-blue);
}

.footer__email {
  display: block;
  font-size: 16px;
  font-weight: 400;
  line-height: 23px;
  color: #22253b;
}

.footer__bottom {
  display: flex;
  flex-wrap: wrap;
  padding-top: 28px;
  border-top: 1px solid #d8d8d8;
  font-family: 'Gilroy', sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 23px;
  color: #8e8e8e;
}

.footer__copyright {
  margin-right: auto;
}

.footer__legal {
  display: flex;
  gap: 64px;
}

@media (max-width: 1023px) {
  .footer__nav {
    margin-right: 83px;
  }

  .footer__legal {
    gap: 32px;
  }
}

@media (max-width: 859px) {
  .footer {
    width: calc(100% - 20px);
  }

  .footer__top {
    flex-direction: column;
    align-items: center;
    gap: 43px;
    margin-bottom: 32px;
    padding-right: 0px;
  }

  .footer__brand-container {
    margin-right: 0px;
  }

  .footer__brand {
    gap: 8px;
    margin-bottom: 23px;
  }

  .footer__tagline {
    font-size: 15px;
  }

  .footer__socials {
    justify-content: center;
  }

  .footer__nav {
    align-items: center;
    padding-top: 0px;
    margin-right: 0px;
  }

  .footer__contacts {
    align-items: center;
    gap: 4px;
  }

  .footer__bottom {
    flex-direction: column;
    align-items: center;
    gap: 13px;
    padding-top: 25px;
    font-size: 12px;
    font-weight: 400;
    line-height: 23px;
  }

  .footer__copyright {
    margin-right: 0px;
  }

  .footer__legal {
    flex-direction: column;
    align-items: center;
    gap: 6px;
    color: var(--color-orange);
  }
}
</style>
