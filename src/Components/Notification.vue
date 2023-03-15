<script setup>
import {onBeforeMount, onMounted, ref} from "vue";

const show = ref(false);

onMounted(() => {
  document.getElementById("notification").play().then(() => {
    setTimeout(() => show.value = true, 300);
  });
})
</script>

<template>
  <div v-show="show" class="notification"></div>
</template>

<style lang="scss">
.notification {
  position: fixed;
  z-index: 999;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: url("/screamer.jpg");
  background-size: cover;
}
</style>