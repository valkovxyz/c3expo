<template>
    <NuxtPage />
  <CookieControl />
</template>


<script setup>
import {onMounted} from "vue";
const { locale } = useI18n()

function setLightThemeForSamsung() {
  const isSamsungBrowser = /SamsungBrowser/i.test(navigator.userAgent);
  if (isSamsungBrowser) {
    document.documentElement.setAttribute('data-theme', 'light');
  }
}

onMounted(() => {
  setLightThemeForSamsung()
})

const {
  cookiesEnabled,
  cookiesEnabledIds,
  isConsentGiven,
  isModalActive,
  moduleOptions,
} = useCookieControl()

// example: react to a cookie being accepted
watch(
    () => cookiesEnabledIds.value,
    (current, previous) => {
      if (
          !previous?.includes('google-analytics') &&
          current?.includes('google-analytics')
      ) {
        // cookie with id `google-analytics` got added
        window.location.reload() // placeholder for your custom change handler
      }
    },
    { deep: true },
)
</script>
<style>


.cookieControl__BarButtons button:nth-child(3) {
  display: none;
}

.cookieControl__BarButtons > button {
  background-color: #555555;
  color: #fff;
}

.cookieControl__BarButtons > button:hover {
  color: #36e4da;
}

.cookieControl__BarContainer > div > p {
  color: #888888;
}

.cookieControl__ControlButton {
  display: none;
}

.select-wrapper {
  position: relative;
  top: 30px;
  right: 30px;
  width: 200px;
}

.lang_switcher {
  appearance: none;
  background-color: #303030;
  border: 1px solid #34495e;
  border-radius: 4px;
  padding: 5px 10px;
  color: #ecf0f1;
  font-size: 16px;
  cursor: pointer;
  position: fixed;
  transition: background-color 0.3s ease;
}

.lang_switcher:focus {
  outline: none;
  border-color: #3498db;
}

.lang_switcher:hover {
  background-color: #34495e;
}

/* Стиль для стрелки селектора */
.select-wrapper::after {
  content: '';
  position: absolute;
  top: 50%;
  right: 15px;
  transform: translateY(-50%);
  border: 6px solid transparent;
  border-top-color: #ecf0f1;
  pointer-events: none; /* Убирает взаимодействие с указателем */
}

body {
  margin: 0 !important;
  background-color: #000;
}


body::-webkit-scrollbar {
  width: 10px;
}

body::-webkit-scrollbar-track {
  background: #f1f1f1;
}

body::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 10px; /* Увеличенный радиус для более круглых углов */
}

body::-webkit-scrollbar-thumb:hover {
  background: #555;
}

.lang_switcher {
  position: absolute;
  top: 50px;
  right: 50px;
  z-index: 1000;
}

</style>