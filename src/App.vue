<template>
  <div class="flex flex-row">
    <div>
      <BarraLateral />
    </div>
    <div>
      <div class="flex flex-col">
        <div class="mb-5 shadow-md">
          <Formulario @sTarefa="salvarTarefa" />
        </div>
        <div v-show="tarefas.length == 0">
          <div class="flex justify-center m-5 p-5 border shadow rounded-md ">
            <div>Usuario sem atividades</div>
          </div>
        </div>
        <div v-show="tarefas.length > 0">
          <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import Formulario from "./components/Formulario.vue";
import Tarefa from "./components/Tarefa.vue";
import ITarefa from "./interfaces/ITarefas";

export default defineComponent({
  name: "App",
  components: { BarraLateral, Formulario, Tarefa },
  data() {
    return {
      tarefas: [] as ITarefa[],
    };
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
  },
});
</script>

<style>
</style>
