<template>
  <div class="flex flex-row" :class="{ 'escuro': modoEsc }">
    <div>
      <BarraLateral />
    </div>
    <div class="" >
      <div class="flex flex-col" :class="{ 'background-dark': modoEsc }">
        <div class="shadow-lg">
          <Formulario @sTarefa="salvarTarefa" @aoTema="alterTema"/>
        </div>
        <div>
          <div v-show="tarefas.length == 0">
            <div class="flex justify-center m-5 p-5 border shadow rounded-md">
              <p>Usuario sem atividades</p>
            </div>
          </div>
          <div v-show="tarefas.length > 0">
            <Tarefa
              v-for="(tarefa, index) in tarefas"
              :key="index"
              :tarefa="tarefa"
            />
          </div>
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
      modoEsc: false
    };
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
    alterTema(modoEsc: boolean) {
      this.modoEsc = modoEsc;
    }
  },
});
</script>

<style>
.claro {
  --bg-primario: #fff;
  --texto-primario: #000;
}
.escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.background-dark {
  background-color: var(--bg-primario);
  height: 965px;
}
p {
  color: var(--texto-primario);
}
</style>
