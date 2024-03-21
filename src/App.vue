<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivado }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioTracker @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TarefaTracker v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxTracker v-if="tarefas.length === 0">
          Você não está muito produtivo hoje :(
        </BoxTracker>
      </div>
    </div>
  </main>
</template>

<script setup lang="ts">
import BarraLateral from "@/components/BarraLateral.vue";
import FormularioTracker from "@/components/FormularioTracker.vue";
import TarefaTracker from "@/components/TarefaTracker.vue";
import {ref} from "vue";
import ITarefa from "@/interfaces/ITarefa";
import BoxTracker from "@/components/BoxTracker.vue";

const tarefas = ref([] as ITarefa[])
const modoEscuroAtivado = ref(false);

const salvarTarefa = (tarefa: ITarefa) => {
  tarefas.value.push(tarefa);
}

const trocarTema = (modoEscuroAtivo: boolean) => {
  modoEscuroAtivado.value = modoEscuroAtivo
}
</script>

<style>
.lista {
  padding: 1.25rem;
}
main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario
  );
}
</style>
