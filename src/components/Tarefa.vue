<template>
  <div>
    <div class="flex flex-row m-5 p-5 border shadow rounded-md">
      <div class="mt-1 mr-96 ml-56">
        <p>
          {{ tarefa.descri || "Tarefa sem descrição" }}
        </p>
      </div>
      <div>
        <Cronometro :tempoSeg="tarefa.duraSegun" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import ITarefa from "@/interfaces/ITarefas";
import { defineComponent, PropType } from "@vue/runtime-core";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
  components: {
    Cronometro,
  },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      required: true,
    },
  },
});
</script>

<style></style>
