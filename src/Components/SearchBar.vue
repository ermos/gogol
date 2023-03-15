<script setup>

import SearchIcon from "./SearchIcon.vue";
import MicIcon from "./MicIcon.vue";
import CamIcon from "./CamIcon.vue";
</script>

<template>
  <div class="searchbar">
    <search-icon />
    <input type="text" />
    <mic-icon />
    <cam-icon />
  </div>
</template>

<style lang="scss">
.searchbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  z-index: 3;
  height: 44px;
  background: #fff;
  border: 1px solid #dfe1e5;
  box-shadow: none;
  border-radius: 24px;
  margin: 20px auto 0;
  padding: 10px 15px;
  width: auto;
  max-width: 584px;

  &:hover {
    background-color: #fff;
    box-shadow: 0 1px 6px rgba(32,33,36,.28);
    border-color: rgba(223,225,229,0);
  }

  input {
    background-color: transparent;
    border: none;
    padding: 0;
    color: rgba(0,0,0,.87);
    word-wrap: break-word;
    outline: none;
    display: flex;
    -webkit-tap-highlight-color: transparent;
    flex: 1;
  }
}
</style>