<template>
    <div class="flex flex-row pt-6 pl-5">
      <div>
        <input
          type="text"
          style="width: 1000px;"
          class="p-3 border rounded-md mt-1"
          placeholder="Qual a tarefa voce deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="basis-1/2">
        <div
        >
          <Temporizador @aoTemp="fimTarefa" />
        </div>
      </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import Temporizador from "./Temporizador.vue";

export default defineComponent({
    components: { Temporizador },
    emits: ['sTarefa'],
    data() {
        return {
            descricao: ''
        }
    },
    methods: {
        fimTarefa(tempDeco: number): void {
            this.$emit('sTarefa', {
              duraSegun: tempDeco,
              descri: this.descricao
            })
        }
    }
});
</script>

<style></style>
