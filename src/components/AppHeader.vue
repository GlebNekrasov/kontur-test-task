<template>
  <header class="header">
    <div class="header__content">
      <div class="header__logo">
        <span class="header__logo-c">C</span>
        <span class="header__logo-o">o</span>
        <span class="header__logo-d">D</span>
        <span class="header__logo-e">e</span>
      </div>

      <nav class="header__nav">
        <a href="#learn" class="header__link">Чему вы научитесь</a>
        <a href="#process" class="header__link">Процесс обучения</a>
        <a href="#pricing" class="header__link">Стоимость</a>
        <a href="#contacts" class="header__link">Контакты</a>
      </nav>

      <a href="tel:+74993489396" class="header__phone">+7 (499) 348 93 96</a>

      <button class="header__burger" @click="toggleMobileMenu" aria-label="Меню">
        <img :src="MenuIcon" alt="Меню" />
      </button>
    </div>

    <!-- Mobile Menu -->
    <Teleport to="body">
      <Transition name="mobile-menu">
        <div v-if="isMobileMenuOpen" class="mobile-menu">
          <button class="mobile-menu__close" @click="toggleMobileMenu" aria-label="Закрыть меню">
            <img :src="CloseIcon" alt="Закрыть" />
          </button>
          <nav class="mobile-menu__nav">
            <a href="#learn" class="mobile-menu__link" @click="toggleMobileMenu"
              >Чему вы научитесь</a
            >
            <a href="#process" class="mobile-menu__link" @click="toggleMobileMenu"
              >Процесс обучения</a
            >
            <a href="#pricing" class="mobile-menu__link" @click="toggleMobileMenu">Стоимость</a>
            <a href="#contacts" class="mobile-menu__link" @click="toggleMobileMenu">Контакты</a>
            <a href="#register" class="mobile-menu__link" @click="toggleMobileMenu">Регистрация</a>
          </nav>
        </div>
      </Transition>
    </Teleport>
  </header>
</template>

<script setup>
import { ref } from 'vue'
import MenuIcon from '@/assets/menu-icon.svg'
import CloseIcon from '@/assets/close-icon.svg'

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}
</script>

<style scoped>
.header {
  height: 51px;
  width: calc(100% - 48px);
  max-width: 1160px;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 24px;
  padding-left: 34px;
  padding-right: 34px;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(7.5px);
  border-radius: 75px;
}

.header__content {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
}

.header__logo {
  font-family: 'Gilroy', sans-serif;
  font-weight: 500;
  font-size: 24px;
  line-height: 1.044;
  display: flex;
  gap: 1px;
  align-self: flex-start;
  padding-top: 11px;
  flex-shrink: 0;
}

.header__logo-c {
  color: var(--color-blue);
}

.header__logo-o {
  color: #000000;
}

.header__logo-d {
  color: var(--color-orange);
}

.header__logo-e {
  color: #000000;
}

.header__nav {
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  gap: 41px;
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: auto;
  min-width: 0;
  padding-top: 22px;
  padding-left: 49px;
}

.header__link {
  font-family: 'Gilroy', sans-serif;
  font-weight: 400;
  font-size: 13px;
  line-height: 1.044;
  color: #22253b;
  white-space: nowrap;
  transition: color var(--transition-fast);
}

.header__link:hover {
  color: var(--color-blue);
}

.header__phone {
  font-family: 'Gilroy', sans-serif;
  font-weight: 400;
  font-size: 16px;
  font-style: normal;
  line-height: 23px;
  color: var(--color-blue);
  transition: opacity var(--transition-fast);
  align-self: flex-start;
  padding-top: 15px;
  flex-shrink: 0;
}

.header__phone:hover {
  opacity: 0.8;
}

.header__burger {
  display: none;
}

.header__burger img {
  display: block;
}

@media (max-width: 1023px) {
  .header__nav {
    gap: 20px;
    padding-left: 25px;
  }
}

/* Mobile */
@media (max-width: 859px) {
  .header {
    height: 41px;
    width: calc(100% - 26px);
    margin-bottom: 13px;
    padding-left: 17px;
    padding-right: 17px;
  }

  .header__logo {
    padding-top: 8px;
  }

  .header__nav {
    display: none;
  }

  .header__phone {
    font-size: 14px;
    padding-top: 11px;
  }

  .header__burger {
    display: block;
    width: 17px;
    padding-top: 13px;
    cursor: pointer;
  }
}

/* Mobile Menu */
.mobile-menu {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: white;
  z-index: 1000;
}

.mobile-menu__close {
  margin-left: calc(100vw - 45px);
  margin-top: 32px;
  width: 15px;
  height: 15px;
  padding: 0;
  background: none;
  border: none;
  cursor: pointer;
}

.mobile-menu__nav {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 1px;
  margin-top: 32px;
  margin-left: 41px;
  margin-right: 86px;
}

.mobile-menu__link {
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 40px;
  font-family: 'Gilroy', sans-serif;
  font-weight: 500;
  font-size: 20px;
  line-height: 1;
  color: #22253b;
  transition: color var(--transition-fast);
}

.mobile-menu__link:hover {
  color: var(--color-blue);
}

/* Mobile Menu Transitions */
.mobile-menu-enter-active,
.mobile-menu-leave-active {
  transition: opacity 0.3s ease;
}

.mobile-menu-enter-from,
.mobile-menu-leave-to {
  opacity: 0;
}
</style>
