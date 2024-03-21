<template>
  <div class="box formulario">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
        <input
            type="text"
            class="input"
            placeholder="Qual tarefa voce deseja iniciar?"
            v-model="descricao"
        >
      </div>
      <div class="column">
        <TemporizadorTracker @aoTemporizadorFinalizado="finalizarTarefa"/>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
<script setup lang="ts">
import TemporizadorTracker from "@/components/TemporizadorTracker.vue";
import {ref} from "vue";

const emits = defineEmits(['aoSalvarTarefa'])

const descricao = ref('');
const finalizarTarefa = (tempoDecorrido: number) : void => {
  emits('aoSalvarTarefa', {
    duracaoEmSegundos: tempoDecorrido,
    descricao: descricao.value
  })
  descricao.value = '';
}
</script>

<style>
.formulario {
  color: var(--texto-primario);
  background-color: var(--bg-primario);
}
</style>