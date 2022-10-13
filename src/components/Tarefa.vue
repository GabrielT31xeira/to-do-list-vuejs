<template>
  <div>
    <div class="flex flex-row m-5 p-5 border shadow rounded-md">
        <div class="mt-1 mr-96 ml-56">
            Descrição da Tarefa
        </div>
        <div>
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