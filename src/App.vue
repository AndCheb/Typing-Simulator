<script setup>
import InputArea from './components/InputArea.vue';
</script>

<template>
  <div class="wrapper">
    <h1>Typing Simulator</h1>
    <InputArea />
  </div>
</template>

<style scoped>
.wrapper {
  display: grid;
  justify-content: center;
  align-content: start;
  grid-template-rows: max-content, 1fr;
  row-gap: 30px;
  padding-top: 50px;
  width: 100%;
  height: 100%;
}
</style>
