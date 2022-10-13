<template>
  <div class="is-flex is-aling-items-center is-justify-content-space-between">
    <Cronometro :tempoSeg="tempoSeg" />
    <button class="buttom" @click="iniciar" :disabled="crorun">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="buttom" @click="finalizar" :disabled="!crorun">
      <span class="icon">
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
            this.crorun = true;
            clearInterval(this.cro);
            this.$emit('aoTemp', this.tempoSeg);
            this.tempoSeg = 0;
        }
    },
    components: { Cronometro }
});
</script>
<style></style>
