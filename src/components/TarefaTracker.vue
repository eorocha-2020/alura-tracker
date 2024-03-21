<template>
  <BoxTracker class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">
        {{ tarefa.descricao || 'Tarefa sem descrição'}}
      </div>
      <div class="column">
        <CronometroTracker :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
      </div>
    </div>
  </BoxTracker>
</template>

<script setup lang="ts">
import CronometroTracker from "@/components/CronometroTracker.vue";
import {PropType} from "vue";
import ITarefa from "@/interfaces/ITarefa";
import BoxTracker from "@/components/BoxTracker.vue";

const props = defineProps({
  tarefa: {
    type: Object as PropType<ITarefa>,
    required: true
  }
})
</script>

