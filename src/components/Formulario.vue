<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form">
        <input
          type="text"
          class="input"
          placeholder="Qual a tarefa voce deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <div
          class="is-flex is-aling-items-center is-justify-content-space-between"
        >
          <Temporizador @aoTemp="fimTarefa" />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import Temporizador from "./Temporizador.vue";

export default defineComponent({
    components: { Temporizador },
    data() {
        return {
            descricao: ''
        }
    },
    methods: {
        fimTarefa(tempDeco: number): void {
            console.log(tempDeco)
        }
    }
});
</script>

<style></style>
