<script setup>
import SearchBar from "./Components/SearchBar.vue";
import SubmitBtn from "./Components/SubmitBtn.vue";
</script>

<template>
  <div class="header">
    <img src="./assets/images/logo.svg" />
  </div>
  <search-bar />
  <center>

    <submit-btn value="Recherche Google" aria-label="Recherche Google" />
    <submit-btn value="J'ai de la chance" aria-label="J'ai de la chance" />

    </center>
</template>

<style lang="scss">
#app {
  height: 100%;
}

.header {
  display: flex;
  align-items: flex-end;
  justify-content: center;
  height: calc(100% - 560px);
}
</style>
