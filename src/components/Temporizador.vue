<template>
  <div class="flex flex-row mt-3 ml-4">
    <Cronometro :tempoSeg="tempoSeg" />
    <button class="ml-4 bg-green-500 py-1 px-2 rounded" @click="iniciar" :disabled="crorun">
      <span class="icon mt-1 mr-2">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="ml-4 bg-red-500 py-1 px-2 rounded" @click="finalizar" :disabled="!crorun">
      <span class="icon mt-1 mr-2">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
    data() {
        return {
            tempoSeg: 0,
            cro: 0,
            crorun: false
        };
    },
    emits: ['aoTemp'],
    methods: {
        iniciar() {
            this.crorun = true;
            this.cro = setInterval(() => {
                this.tempoSeg += 1;
            }, 1000);
        },
        finalizar() {
            this.crorun = false;
            clearInterval(this.cro);
            this.$emit('aoTemp', this.tempoSeg);
            this.tempoSeg = 0;
        }
    },
    components: { Cronometro }
});
</script>
<style></style>
