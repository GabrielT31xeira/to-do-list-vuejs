<template>
  <section>
    <strong>{{ tempDeco }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";

export default defineComponent({
  props: {
    tempoSeg: {
      type: Number,
      default: 0
    },
  },
  computed: {
    tempDeco(): string {
      return new Date(this.tempoSeg * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>

<style></style>
