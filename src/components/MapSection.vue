<template>
  <div v-if="!isErrorLoading" id="map-container"></div>
</template>

<script setup>
import { onMounted, ref, onUnmounted, computed, watch } from 'vue'

const isErrorLoading = ref(false)
const YANDEX_API_KEY = import.meta.env.VITE_YANDEX_MAPS_API_KEY
const isMobile = ref(false)
const myMap = ref(null)
const zoom = computed(() => {
  return isMobile.value ? 14 : 15
})

const updateBreakpoints = () => {
  isMobile.value = window.matchMedia('(max-width: 859px)').matches
}

function init() {
  const coordinates = [55.028894, 82.926493] // Координаты центра карты

  // Создаем карту только если она еще не создана
  if (!myMap.value) {
    // Инициализируем карту
    myMap.value = new ymaps.Map('map-container', {
      center: coordinates,
      zoom: zoom.value,
      controls: [], // Отключаем все управляющие элементы
    })

    // Получаем адрес по координатам
    ymaps.geocode(coordinates).then(function (res) {
      const firstGeoObject = res.geoObjects.get(0)

      // Получаем компоненты адреса без города
      const thoroughfare = firstGeoObject.getThoroughfare() || ''
      const premiseNumber = firstGeoObject.getPremiseNumber() || ''
      const address =
        thoroughfare && premiseNumber
          ? `${thoroughfare}, ${premiseNumber}`
          : firstGeoObject.getAddressLine()

      // Создаем метку с подписью справа от указателя
      const placemark = new ymaps.Placemark(
        coordinates,
        {
          iconCaption: address,
        },
        {
          preset: 'islands#redDotIcon',
        },
      )

      // Добавляем метку на карту
      myMap.value.geoObjects.add(placemark)
    })
  }
}

watch(zoom, (newZoom) => {
  if (myMap.value) {
    myMap.value.setZoom(newZoom)
  }
})

onMounted(() => {
  updateBreakpoints()
  window.addEventListener('resize', updateBreakpoints)
  if (!YANDEX_API_KEY) {
    isErrorLoading.value = true
    return
  }

  // Создаем скрипт для загрузки API
  const script = document.createElement('script')
  script.src = `https://api-maps.yandex.ru/2.1/?apikey=${YANDEX_API_KEY}&lang=ru_RU`
  script.type = 'text/javascript'
  script.onload = () => {
    // Функция, которая будет выполнена после загрузки скрипта
    ymaps.ready(init)
  }
  script.onerror = () => {
    console.error('Failed to load Yandex Maps API')
    isErrorLoading.value = true
  }
  document.head.appendChild(script)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateBreakpoints)
  if (myMap.value) {
    myMap.value.destroy()
  }
})
</script>

<style scoped>
#map-container {
  width: calc(100% - 48px);
  max-width: 1161px;
  height: 423px;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 60px;
  border-radius: 30px;
  overflow: hidden;
}

@media (max-width: 859px) {
  #map-container {
    width: calc(100% - 20px);
    height: 415px;
    margin-bottom: 39px;
  }
}
</style>
