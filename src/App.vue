<script setup>
import Countdown from './components/Countdown.vue'
</script>

<template>
  <main>
    <Countdown />
  </main>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Bruno+Ace+SC&display=swap');

#app {
  height: 100%;
}

main {
  height: 100%;

  font-family: 'Bruno Ace SC', cursive;
}

body,
html {
  height: 100%;

  background: #000;
}
</style>
