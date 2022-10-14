<template>
    <div class="flex flex-row pt-6 pl-5 pb-5" style="width: 1456px">
      <div>
        <input
          type="text"
          style="width: 950px;"
          class="p-3 border rounded-md mt-1"
          placeholder="Qual a tarefa voce deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div>
        <div
        >
          <Temporizador @aoTemp="fimTarefa" />
        </div>
      </div>
      <div>
        <button class="mt-2 ml-2 py-2 px-2  bg-slate-400 rounded border" @click="ligEscu" v-show="escuro == false">
          <p>Ativar modo escuro</p>
        </button>
        <button class="mt-2 ml-2 py-2 px-2 bg-gray-700 rounded border" @click="desEscu" v-show="escuro == true">
          <p class="text-slate-50">Desativar modo escuro</p>
        </button>
      </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import Temporizador from "./Temporizador.vue";

export default defineComponent({
    components: { Temporizador },
    emits: ['sTarefa','aoTema'],
    data() {
        return {
            descricao: '',
            escuro: false
        }
    },
    methods: {
        fimTarefa(tempDeco: number): void {
            this.$emit('sTarefa', {
              duraSegun: tempDeco,
              descri: this.descricao
            })
        },
        desEscu(): void{
          this.escuro = false
          this.$emit('aoTema', this.escuro)
        },
        ligEscu(): void{
          this.escuro = true;
          this.$emit('aoTema', this.escuro)
        }
    }
});
</script>

<style>
.background-dark {
  background-color: var(--bg-primario);
}
</style>
