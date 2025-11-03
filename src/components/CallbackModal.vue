<template>
  <Teleport to="body">
    <Transition name="modal">
      <div v-if="isOpen" class="modal-overlay" @click.self="closeModal">
        <div class="modal">
          <button class="modal__close" @click="closeModal" aria-label="Закрыть">
            <img src="@/assets/close-icon.svg" alt="Закрыть" />
          </button>

          <h2 class="modal__title">Заказать звонок</h2>

          <form class="modal__form" @submit.prevent="submitForm">
            <div class="form-group">
              <label for="name" class="form-group__label">Имя</label>
              <input
                id="name"
                v-model="formData.name"
                type="text"
                class="form-group__input"
                placeholder="ваше имя"
              />
            </div>

            <div class="form-group">
              <label for="phone" class="form-group__label">Телефон</label>
              <input
                id="phone"
                v-model="formData.phone"
                type="tel"
                class="form-group__input"
                placeholder="+7 ХХХ - ХХХ - ХХ -ХХ"
              />
            </div>

            <div class="form-group">
              <label for="email" class="form-group__label">Email</label>
              <input
                id="email"
                v-model="formData.email"
                type="email"
                class="form-group__input"
                placeholder="mail@site.com"
              />
            </div>

            <div class="form-group">
              <label for="message" class="form-group__label">Сообщение</label>
              <textarea
                id="message"
                v-model="formData.message"
                class="form-group__textarea"
                placeholder="Ваше сообщение ..."
              >
      Ваше сообщение ...
              </textarea>
            </div>

            <p class="modal__disclaimer">
              Нажимая кнопку "Отправить", соглашаюсь с
              <span class="modal__disclaimer-accent">политикой конфидениальности</span>
            </p>

            <ActionButton text="Отправить" type="submit" />
          </form>
        </div>
      </div>
    </Transition>
  </Teleport>
</template>

<script setup>
import { ref } from 'vue'
import ActionButton from './ui/ActionButton.vue'

// Модальное окно с формой заказа звонка
const isOpen = ref(false)
const formData = ref({
  name: '',
  phone: '',
  email: '',
  message: '',
})

const openModal = () => {
  isOpen.value = true
}

const closeModal = () => {
  isOpen.value = false
}

const submitForm = () => {
  console.log('Form submitted:', formData.value)
  closeModal()
}

defineExpose({ openModal })
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal {
  background: #fff;
  padding: 80px 53px 40px;
  width: 635px;
  max-width: 90vw;
  max-height: 100vh;
  overflow-y: auto;
  position: relative;
}

.modal__close {
  position: absolute;
  top: 24px;
  right: 24px;
  background: none;
  border: none;
  cursor: pointer;
}

.modal__close img {
  display: block;
}

.modal__title {
  font-family: 'Gilroy', sans-serif;
  font-size: 32px;
  font-weight: 400;
  line-height: 30px;
  margin-bottom: 46px;
  color: #22253b;
  text-align: center;
}

.modal__form {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.form-group__label {
  font-family: 'Gilroy', sans-serif;
  font-weight: 500;
  font-size: 16px;
  line-height: normal;
  color: #000;
}

.form-group__input,
.form-group__textarea {
  font-family: 'Gilroy', sans-serif;
  padding: 0 30px;
  height: 75px;
  border: 1px solid #9f9f9f;
  border-radius: 10px;
  font-size: 16px;
  font-weight: 400;
}

.form-group__input::placeholder,
.form-group__textarea::placeholder {
  color: #9f9f9f;
}

.form-group__textarea {
  height: 120px;
  padding-top: 23px;
  padding-bottom: 23px;
  resize: none;
}

.modal__disclaimer {
  font-family: 'Gilroy', sans-serif;
  font-size: 16px;
  font-weight: 400;
  color: #9f9f9f;
  line-height: normal;
  max-width: 345px;
  margin-top: -8px;
}

.modal__disclaimer-accent {
  color: var(--color-orange);
}

.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.3s;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

@media (max-width: 859px) {
  .modal {
    width: 100%;
    max-width: 100%;
    height: 100%;
    max-height: 100%;
    padding: 40px 26px 20px;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 1000;
  }

  .modal__title {
    font-size: 24px;
    margin-bottom: 24px;
  }

  .modal__form {
    gap: 16px;
  }

  .form-group {
    gap: 8px;
  }

  .form-group__label {
    font-size: 14px;
  }

  .form-group__input,
  .form-group__textarea {
    font-family: 'Gilroy', sans-serif;
    padding: 0 15px;
    height: 45px;
    border-radius: 6px;
    font-size: 14px;
    font-weight: 400;
  }

  .modal__disclaimer {
    font-family: 'Gilroy', sans-serif;
    font-size: 14px;
    font-weight: 400;
    color: #9f9f9f;
    line-height: normal;
    max-width: 345px;
    margin-top: -8px;
  }
}
</style>
