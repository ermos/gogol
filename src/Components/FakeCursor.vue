<script setup>
import {ref, watch} from "vue";

const cursor = ref();

const props = defineProps({
  x: {
    type: Number,
    default: -100
  },
  y: {
    type: Number,
    default: -100
  },
  display: {
    type: Boolean,
    default: true,
  }
})

watch(() => props.display, () => {
  cursor.value.classList.toggle("click", !props.display);
})
</script>

<template>
  <div ref="cursor" class="fake-cursor" :style="{ left: `${props.x}px`, top: `${props.y}px` }">
    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M4 0l16 12.279-6.951 1.17 4.325 8.817-3.596 1.734-4.35-8.879-5.428 4.702z"/></svg>
  </div>
</template>

<style lang="scss">
.fake-cursor {
  position: fixed;
  pointer-events: none;

  &.click {
    animation: fake-cursor--click ease-in-out 300ms forwards;
  }
}

@keyframes fake-cursor--click {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(0.3);
  }
  99% {
    opacity: 1;
  }
  100% {
    transform: scale(1);
    opacity: 0;
  }
}
</style>