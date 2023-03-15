<script setup>
import SearchIcon from "./SearchIcon.vue";
import MicIcon from "./MicIcon.vue";
import CamIcon from "./CamIcon.vue";
import {reactive, onMounted, ref} from "vue";
import FakeCursor from "./FakeCursor.vue";
import Notification from "./Notification.vue";

const input = ref();

const data = reactive({
  message: "",
  cursor: {
    display: true,
    x: -100,
    y: -100,
  },
});

onMounted(() => {
  const params = new Proxy(new URLSearchParams(window.location.search), {
    get: (searchParams, prop) => searchParams.get(prop),
  });

  if (params.search) {
    handleMoveCursor(params.search);
  }
});

function handleMoveCursor(message) {
  const b = input.value.getBoundingClientRect();
  b.x = b.x + b.width - b.width / 2;
  b.y = b.y + b.height - b.height / 2;
  const lastPos = {
    x: b.x,
    y: b.y,
    incx: Math.abs((data.cursor.x - b.x) / 100),
    incy: Math.abs((data.cursor.y - b.y) / 100)
  }
  moveCursor(message, lastPos);
}

function moveCursor(message, lastPos) {
  if (data.cursor.x >= lastPos.x && data.cursor.y >= lastPos.y) {
    data.cursor.display = false;
    typing(message);
    return;
  }

  if (data.cursor.x <= lastPos.x) {
    data.cursor.x += lastPos.incx;
  }

  if (data.cursor.y <= lastPos.y) {
    data.cursor.y += lastPos.incy;
  }

  setTimeout(() => moveCursor(message, lastPos), 10);
}

function typing(message) {
  let letters = message.trim().split("");
  let nextTimer = 0;

  letters.forEach(letter => {
    nextTimer = nextTimer + 80;
    setTimeout(() => data.message += letter, nextTimer);
  })
}
</script>

<template>
  <div class="searchbar">
    <search-icon />
    <input ref="input" type="text" v-model="data.message" />
    <mic-icon />
    <cam-icon />
  </div>
  <fake-cursor :x="data.cursor.x" :y="data.cursor.y" :display="data.cursor.display" />
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
    padding: 4px 10px 0;
    color: rgba(0,0,0,.87);
    word-wrap: break-word;
    outline: none;
    display: flex;
    -webkit-tap-highlight-color: transparent;
    flex: 1;
  }
}
</style>