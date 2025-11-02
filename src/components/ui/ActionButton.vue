<template>
  <button :type="type" class="action-button" @click="handleClick">
    <div class="action-button__text">{{ text }}</div>
    <img src="/src/assets/arrow-button.svg" alt="" class="action-button__arrow" />
  </button>
</template>

<script setup>
defineProps({
  text: {
    type: String,
    required: true,
  },
  type: {
    type: String,
    default: 'button',
    validator: (value) => ['button', 'submit'].includes(value),
  },
})

const emit = defineEmits(['click'])

const handleClick = (event) => {
  emit('click', event)
}
</script>

<style scoped>
.action-button {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 12px;
  height: 70px;
  width: 265px;
  padding-left: 46px;
  padding-right: 38px;
  background: var(--color-orange);
  color: white;
  border-radius: 82px;
  font-family: 'Gilroy', sans-serif;
  font-weight: 400;
  font-size: 20px;
  line-height: 96.688%;
  letter-spacing: -0.6px;
  border: none;
  cursor: pointer;
  transition: all var(--transition-fast);
}

.action-button:hover {
  background: var(--color-blue);
  transform: translateY(-2px);
}

.action-button__text {
  flex-grow: 1;
}

.action-button__arrow {
  flex-shrink: 0;
  width: 15px;
  height: 15px;
  transition: transform var(--transition-fast);
}

.action-button:hover .action-button__arrow {
  transform: translateX(4px);
}
</style>
