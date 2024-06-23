<script setup>
import { useFocus } from '@vueuse/core';
import data from '@/data/texts.json';
import { ref, computed, watch } from 'vue';

const input = ref();
const inputText = ref('');
const text = ref('');

text.value = data[0].text;

const { focused: inputFocus } = useFocus(input, { initialValue: true });

const changeText = (e) => {
  const value = e.target.value;

  if (!value) return;

  if (value[value.length - 1] === text.value[0]) {
    text.value = text.value.slice(1);
  } else {
    inputText.value = inputText.value.slice(0, -1);
  }
}

</script>

<template>
  <div class="area">
    <span class="input-text">{{ inputText }}</span>
    <span class="text">{{ text }}</span>
    <input type="text" ref="input" v-model="inputText" @keydown.delete.prevent @input="changeText" />
  </div>
  <button type="button" @click="inputFocus = !inputFocus">Начать</button>
</template>

<style lang="scss" scoped>
.area {
  width: 300px;
  border: 1px solid #000;

  &:focus-within {
    outline: 1px solid red;
  }
}

input {
  opacity: 0;
}

.input-text {
  background-color: #d9f7a9;
}

.text {
  color: #a1a1a1;
}
</style>
