<template>
  <div class="select-wrapper"></div>
  <select class="lang_switcher" v-model="locale">
    <option value="en">en <img src="assets/united-kingdom.png" alt="United kingdom"/></option>
    <option value="de">de <img src="assets/germany.png" alt="Germany"/></option>
  </select>
  <div>
    <NuxtPage />
  </div>
</template>


<script setup>

const { locale } = useI18n()
</script>
<style>


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
  padding: 10px 40px 10px 10px;
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