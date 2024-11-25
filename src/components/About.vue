<template>

  <div :class="bemm">

    tig<span>.mt</span>
  </div>
</template>

<script lang="ts" setup>
import { useBemm } from "@/utils";
const bemm = useBemm('about');
</script>


<style lang="scss">
 .intro {
    font-weight: bold;
    font-size: clamp(1.5em, 6vw, 5em);
    height: 100vh;
    background-color: black;
    span{
      // opacity: .25;
      font-weight: 400;
      color: #ffae00;
    }
  }
</style>
