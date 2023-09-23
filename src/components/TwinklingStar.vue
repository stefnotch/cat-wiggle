<script setup lang="ts">
import { ref } from "vue";
let animationDuration = ref(Math.random() * 3 + 1);
let animationStart = ref(Math.random() * 3);
</script>

<template>
  <div class="twinkling-star"></div>
</template>

<style scoped>
/** A twinkling star */
.twinkling-star {
  position: absolute;
  width: 4px;
  height: 4px;
  background-color: #fff;
  border-radius: 50%;
  box-shadow: 0 0 2px #fff;
  animation: twinkling calc(v-bind(animationDuration) * 1s)
    calc(v-bind(animationStart) * 1s) linear infinite;
}

@keyframes twinkling {
  0% {
    transform: scale(1);
    opacity: 0.8;
  }
  50% {
    transform: scale(0.5);
    opacity: 0.5;
  }
  100% {
    transform: scale(1);
    opacity: 0.8;
  }
}
</style>
