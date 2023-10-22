<template>
  <div class="box" v-for="item in list">
    <div>{{ item.title }}</div>
    <img
      :src="item.img"
      @mouseover="handleOver(item, $event)"
      @mouseleave="handleLeave(item, $event)"
    />
  </div>
</template>

<script setup>
import img1 from './assets/服务机构1.png';
import img2 from './assets/服务机构.png';
import img3 from './assets/地理标志.png';
import img4 from './assets/地理标志 (1).png';

import { ref } from 'vue';

const list = ref([
  {
    title: '111',
    img: img1,
    key: 1,
  },
  {
    title: '222',
    img: img3,
    key: 2,
  },
]);

const handleOver = (e, a) => {
  if (e.key === 1) {
    e.img = img2;
    a.currentTarget.className = 'active';
  } else if (e.key === 2) {
    e.img = img4;
    a.currentTarget.className = 'active';
  }
};

const handleLeave = (e, a) => {
  a.currentTarget.className = '';
  if (e.key === 1) {
    e.img = img1;
  } else if (e.key === 2) {
    e.img = img3;
  }
};
</script>

<style scoped>
.box {
  width: 300px;
  height: 140px;
}

.box img {
  width: 100%;
  height: 100%;
}

img.active {
  transition: all 0.1s;
  width: 315px;
  height: 140px;
}
</style>
