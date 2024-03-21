<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroTracker :tempoEmSegundos="tempoEmSegundos"/>
    <button @click="iniciar" class="button" :disabled="cronometroRodando">
          <span class="icon">
            <i class="fas fa-play"></i>
          </span>
      <span>Play</span>
    </button>
    <button @click="finalizar" class="button" :disabled="!cronometroRodando">
          <span class="icon">
            <i class="fas fa-stop"></i>
          </span>
      <span>Stop</span>
    </button>
  </div>
</template>

<script setup lang="ts">

import {ref} from "vue";
import CronometroTracker from "@/components/CronometroTracker.vue";

const cronometro = ref(0);
const tempoEmSegundos = ref(0);
const cronometroRodando = ref(false);
const emits = defineEmits(['aoTemporizadorFinalizado'])
const iniciar = () => {
  cronometroRodando.value = true;
  cronometro.value = setInterval(() => {
    tempoEmSegundos.value += 1
  }, 1000)
}

const finalizar = () => {
  cronometroRodando.value = false;
  clearInterval(cronometro.value);
  emits('aoTemporizadorFinalizado', tempoEmSegundos.value);
  tempoEmSegundos.value = 0;
}
</script>

<style scoped>

</style>