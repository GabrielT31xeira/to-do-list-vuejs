<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
        <div class="column is-7">
            Descrição da Tarefa
        </div>
        <div class="column">
            <Cronometro :tempoSeg="15"/>
        </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from '@vue/runtime-core';
import Cronometro from './Cronometro.vue';

export default defineComponent({
    components: {
        Cronometro
    }
})
</script>

<style>

</style>