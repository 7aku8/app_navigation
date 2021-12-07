<script setup lang="ts">
import Navigation from './components/Navigation.vue'
</script>

<template>
  <div
    class="background"
  >
    <div
      class="application"
    >
      <Navigation
        class="application__nav"
      />
    </div>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Baloo+Bhaijaan+2:wght@400;500;600&family=Poppins:wght@100;200;300;400;500;600;700&display=swap');

:root {
  --bg-color: #262626;
  --nav-bg: #FFFFFF;
  --icon-color: var(--bg-color);
  --text-color: var(--bg-color);
  --active-bg: #d34e20;
  --active-border: var(--bg-color);
}

#app {
  font-family: 'Baloo Bhaijaan 2', cursive, 'Poppins', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
}

.background {
  width: 100vw;
  height: 100vh;

  display: flex;
  place-content: center;
  align-items: center;
}

.application {
  height: 736px;
  width: 414px;
  max-height: 90vh;
  max-width: 90vw;

  padding: 20px 7px !important;

  display: flex;

  background-color: var(--bg-color);

  &__nav {
    margin-top: auto !important;
  }
}
</style>
