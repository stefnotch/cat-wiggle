<script setup lang="ts">
import TwinklingStar from "./components/TwinklingStar.vue";
import Sakana from "sakana";
import { computed, onMounted, ref } from "vue";
import { useWindowSize } from "vue-window-size";

const { width, height } = useWindowSize();

const twinklingStars = computed(() => {
  const w = width.value;
  const h = height.value;
  const stars = [];
  for (let i = 0; i < 100; i++) {
    stars.push({
      left: Math.random() * w,
      top: Math.random() * h,
    });
  }
  return stars;
});

onMounted(() => {
  let x = Sakana.init({
    el: ".sakana-box", // 启动元素 node 或 选择器
    scale: 0.9, // 缩放倍数
    canSwitchCharacter: false, // 允许换角色
    character: "takina",
  });
});
</script>

<template>
  <main>
    <div class="fixed flex-center-both">
      <div class="sakana-box"></div>
    </div>
    <div class="fixed">
      <TwinklingStar
        v-for="(star, index) in twinklingStars"
        :key="index"
        :style="{
          left: star.left + 'px',
          top: star.top + 'px',
        }"
      />
    </div>
  </main>
</template>

<style scoped>
.fixed {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
main {
  width: 100%;
  height: 100%;

  background-color: #1a1a2e;
  background-image: linear-gradient(
    180deg,
    #1a1a2e 0%,
    #16213e 33%,
    #0f3460 66%,
    #0b6875 100%
  );
}

.flex-center-both {
  display: flex;
  justify-content: center;
  align-items: center;
}

.sakana-box {
  position: fixed;
  bottom: 0;
}
</style>
