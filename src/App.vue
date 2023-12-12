<script setup>
import { RouterView } from 'vue-router'
import Heading from './components/Heading.vue'
</script>

<template>
  <div class="component">
    <header class="component__header">
      <Heading />
    </header>
    <main class="component__main">
      <RouterView />
    </main>
  </div>
  
</template>

<style scoped>
  .component {
    position: absolute;
    top: 50vh;
    left: 50vw;
    width: min(80vw, 600px);
    height: min(80vh, 600px);
    transform: translate(-50%, -50%);
  }
  .component__header {
    border: 4px solid #EAEAEA;
    padding: 1em;
    background-color: #F7F7FF;
    height: 15%;
  }
  .component__main {
    border: 4px solid #EAEAEA;
    padding: 1em;
    background-color: #F7F7FF;
    background-image: url('assets/bg2.png');
    background-position: bottom right;
    background-repeat: no-repeat;
    background-size: initial;
    height: 85%;
  }
</style>
