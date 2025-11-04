# .

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Vue (Official)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Recommended Browser Setup

- Chromium-based browsers (Chrome, Edge, Brave, etc.):
  - [Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd) 
  - [Turn on Custom Object Formatter in Chrome DevTools](http://bit.ly/object-formatters)
- Firefox:
  - [Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
  - [Turn on Custom Object Formatter in Firefox DevTools](https://fxdx.dev/firefox-devtools-custom-object-formatters/)

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Environment Variables

После клонирования проекта необходимо настроить переменные окружения:

1. Скопируйте файл `.env.example` в `.env`:
   ```sh
   cp .env.example .env
   ```

2. Откройте файл `.env` и вставьте валидный API ключ к JavaScript API Яндекс Карт:
   ```
   VITE_YANDEX_MAPS_API_KEY=your_yandex_maps_api_key_here
   ```

Получить API ключ можно на странице [JavaScript API и HTTP Геокодер](https://developer.tech.yandex.ru/services/) в кабинете разработчика Яндекс.

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
