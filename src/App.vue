<script setup>
import { ref, computed } from 'vue';

const cont = ref(0);

const arreglo = ref([]);

const incrementar = () => {
  cont.value++;
}

const disminuir = () => {
  cont.value--;
}

const resetear = () => {
  cont.value = 0;
}

const agregar = (num) => {
  arreglo.value.push(num);
  console.log(arreglo.value)
}

const deshabilitar = (num) => {
  return arreglo.value.includes(num);
}

const color = computed(() => {
  if (cont.value === 0) {
    return "zero";
  }
  return cont.value > 0 ? "positive" : "negative";
});

</script>

<template>
  <div class="container text-center mt-5">
    <h1 :class="color">{{ cont }}</h1>
    <br>
    <h5>Elegí un número y agregalo. El número no se puede repetir.</h5>
    <h6>Si el número es 0, su color el blanco. Si el número es negativo, su color es rojo. Si el número es positivo, su
      color es verde.</h6>
    <br>
    <div class="btn-group">
      <button class="btn btn-success btn-lg" @click="incrementar">Incrementar</button>
      <button class="btn btn-danger btn-lg" @click="disminuir">Disminuir</button>
      <button class="btn btn-secondary btn-lg" @click="resetear">Resetear</button>
      <button class="btn btn-primary btn-lg" @click="agregar(cont)" :disabled="deshabilitar(cont)">Add</button>
    </div>
    <ul class="list-group mt-2">
      <li class="list-group-item" v-for="num in arreglo" :key="num">
        {{ num }}</li>
    </ul>
  </div>
</template>

<style>
h1 {
  font-size: 80px;
}

h6 {
  font-size: small;
}

.zero {
  color: white;
}

.positive {
  color: green;
}

.negative {
  color: red;
}
</style>