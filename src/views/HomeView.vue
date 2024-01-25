<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo-osmd.svg">
    <h1>Open Sheet Music Display example with Vue.js 3</h1>
    <select name="file" id="file" v-model="selectedSheetMusic">
      <option disabled select value>Select your sheet music</option>
      <option v-for="(item, index) in sheetMusicFiles" :key="index" :value="item">
        {{ `${item.author}-${item.title}` }}
      </option>
    </select>
    <OsmdComponent v-if="selectedSheetMusic" :file="selectedSheetMusic.file" :key="selectedSheetMusic.file">
    </OsmdComponent>
  </div>
</template>

<script setup lang="ts">
import OsmdComponent from '@/components/OsmdComponent.vue';
import { ref } from 'vue';

const selectedSheetMusic = ref();
const sheetMusicFiles = [
  {
    author: 'Mozart',
    title: 'An Chloe',
    file: 'sheet-music-files/mozart-an_chloe.xml'
  },
  {
    author: 'Mozart',
    title: 'Das Veilchen',
    file: 'sheet-music-files/mozart-das_veilchen.xml'
  },
]
</script>

