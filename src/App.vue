<script setup>
import SearchBar from "./Components/SearchBar.vue";
import SubmitBtn from "./Components/SubmitBtn.vue";
import Notification from "./Components/Notification.vue";
import {reactive} from "vue";

const data = reactive({
  notification: false,
  scaleBtn: false,
})
</script>

<template>
  <div class="header">
    <img src="./assets/images/logo.svg" />
  </div>
  <search-bar @end="data.scaleBtn = true"/>
  <div class="btn-group">
    <submit-btn @click="data.notification = true" value="Recherche Google" aria-label="Recherche Google" :class="{ 'scale': data.scaleBtn }" />
    <submit-btn @click="data.notification = true" value="J'ai de la chance" aria-label="J'ai de la chance" />
  </div>
  <audio id="notification" src="/notification.mp3"></audio>
  <notification v-if="data.notification" />
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

.btn-group {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
