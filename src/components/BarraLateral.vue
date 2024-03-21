<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="">
    </h1>
    <button class="button" @click="alterarTema">
      {{ textoBotao }}
    </button>
  </header>
</template>

<script setup lang="ts">

import {computed, ref} from "vue";

const emits = defineEmits(['aoTemaAlterado'])
const modoEscuroAtivo = ref(false);
const textoBotao = computed(() => {
  if (modoEscuroAtivo.value) {
    return 'Desativar modo escuro';
  }
  return 'Ativar modo escuro';
})
const alterarTema = () => {
  modoEscuroAtivo.value = !modoEscuroAtivo.value;
  emits('aoTemaAlterado', modoEscuroAtivo.value)
}
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>