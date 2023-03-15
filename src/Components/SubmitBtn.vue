<script setup>

</script>

<template>
  <input class="submit-btn" role="button" tabindex="0" type="submit" />
</template>

<style lang="scss">
.submit-btn {
  background-color: #f8f9fa;
  border: 1px solid #f8f9fa;
  border-radius: 4px;
  color: #3c4043;
  font-family: arial,sans-serif;
  font-size: 14px;
  margin: 20px 6px 11px;
  padding: 0 16px;
  line-height: 27px;
  height: 36px;
  min-width: 54px;
  text-align: center;
  cursor: pointer;
  user-select: none;

  &.scale {
    transform: scale(1.4);
    box-shadow: 0 0 10px #fff;
    color: #fff;
    background-color: #319a6e;
    border: 1px solid #319a6e;
    transition: all ease-in-out 200ms;
    animation: animation-scale 2000ms ease-in-out infinite;
  }
}

@keyframes animation-scale {
  0% {
    transform: scale(1.2);
  }
  50% {
    transform: scale(1.4);
  }
  100% {
    transform: scale(1.2);
  }
}
</style>