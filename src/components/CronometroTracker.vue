<template>
  <section>
    <strong class="display">{{ tempoDecorrido }}</strong>
  </section>
</template>

<script setup lang="ts">
import {computed} from "vue";

const props = defineProps(['tempoEmSegundos']);
const tempoDecorrido = computed(() : string => {
  return new Date(props.tempoEmSegundos * 1000).toISOString().substr(11, 8)
})

</script>

<style>
.display {
  color: var(--texto-primario);
}
</style>