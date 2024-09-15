<script setup>
import { ref, computed } from 'vue';

// Variable reactiva para el contador
const counter = ref(10);

// Array reactivo para los números
const listNums = ref([]);

// Computed para manejar la clase del contador
const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'zero';
  } else if (counter.value < 0) {
    return 'negative';
  } else {
    return 'positive';
  }
});

// Función para disminuir el contador
const decrement = () => {
  counter.value--;
};

// Función para resetear el contador a cero
const reset = () => {
  counter.value = 0;
};

// Función para incrementar el contador
const increment = () => {
  counter.value++;
};


// Función para agregar el valor del contador a la lista de números, evitando duplicados
const add = () => {
  if (!listNums.value.includes(counter.value)) {
    listNums.value.push(counter.value);
  }
};
</script>



<template>
<div  class="container mx-auto p-4">
  <div class="p-4 flex flex-col lg:flex-row">
  <button @click="increment" class="bg-cyan-600 text-center text-white p-2 mx-3">
    Incrementar
  </button>
  <button @click="decrement" class="bg-black text-center text-white p-2 mx-3">
    Disminuir contador
  </button>
  <button @click="reset" class="bg-red-600 text-center text-white p-2 mx-3">
    Resetear contador
  </button>
  <button @click="add" :disabled="listNums.value && listNums.value.includes(counter.value)" class="bg-blue-600 text-center text-white p-2 mx-3">
    Agregar
  </button>
  </div>
  <div class="text-center p-4 ">
    <h2 class="text-3xl" :class="classCounter">{{ counter }}</h2>
    <h2 class="font-bold text-cente font-bold text-3xl" >Lista</h2>
  </div>
  <ul>
    <template v-for="value in listNums">
      <li class="border-b-4 border-cyan-600">{{ value }}</li>
    </template>
  </ul>
</div>

</template>

<style>
h1 {
  color: blue;
}

/* Estilos basados en el valor del contador */
.zero {
  color: black;
}

.negative {
  color: red;
}

.positive {
  color: green;
}
</style>
