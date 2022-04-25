<script setup>
import Header from '@/components/Header.vue'
</script>

<template>
  <Header />
  <RouterView />
</template>

<style>
@import '@/assets/base.css';

#app {
  font-weight: normal;
  max-width: 1300px;
  margin: 10px auto;
  padding: 10px;
}
a {
  text-decoration: none;
  color: #000;
}
@media (max-width:425px) {
  #app {
    padding: 0;
  }
}
</style>
