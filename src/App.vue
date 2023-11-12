<script setup>
import HelloWorld from './components/HelloWorld.vue'
import {BILIBILISPACE, YOUTUBESPACE} from './const.js'
</script>

<template>
  <div>
    <a :href="BILIBILISPACE" target="_blank">
      BILIBILI
    </a>
    <a :href="YOUTUBESPACE" target="_blank">
      YOUTUBE
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>

.logo {
  height: 1em;
  padding: .5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.bilibili:hover {
  filter: drop-shadow(0 0 2em #F9F9F9);
}
.logo.youtube:hover {
  filter: drop-shadow(0 0 2em #F9F9F9);
}
</style>
