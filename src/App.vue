<script setup>
import { ref, computed } from 'vue';

const name = "Vue 3";
let counter = ref(0);
const arrayFvorito = ref([]);

const increment = () => {
  counter.value++;
};

const decrement = () => {
  counter.value--;
};

const reset = () => {
  counter.value = 0;
};

const add = () => {
  arrayFvorito.value.push(counter.value);
};

const bloquearBtnAdd = computed(() => {
  const numSearch = arrayFvorito.value.includes(counter.value);
  return numSearch;

});

const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'cero'
  }
  if (counter.value > 0) {
    return 'positive'
  } else {
    return 'negative'
  }

});
</script>

<template>
  <div class="container text-center mt-3">
    <h1> Hola {{ name }}</h1>

    <h2 :class="classCounter">{{ counter }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <button @click="decrement" class="btn btn-danger">Disminuir</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-primary">Add</button>
    </div>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="num in arrayFvorito" :key="num">
        {{ num }}
      </li>
    </ul>
  </div>
</template>

<style>
h1 {
  color: rgb(255, 0, 64);
}

.positive {
  color: green
}

.negative {
  color: red
}

.cero {
  color: aqua
}
</style>