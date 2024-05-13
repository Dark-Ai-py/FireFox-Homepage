<script setup>
import searchBar from './components/searchBar.vue'
import quickLink from './components/quickLink.vue';
import { ref } from 'vue';

const links = [{
  title: "youtube",
  description: "videos",
  logo: "https://m.youtube.com/static/apple-touch-icon-114x114-precomposed.png",
},{
  title: "youtube",
  description: "videos",
  logo: "https://m.youtube.com/static/apple-touch-icon-114x114-precomposed.png",
},{
  title: "youtube",
  description: "videos",
  logo: "https://m.youtube.com/static/apple-touch-icon-114x114-precomposed.png",
},]

const theme = 'dim'

</script>

<template>
  <div class="flex flex-col justify-center w-screen h-screen items-center" :data-theme="theme">
  <searchBar />
  <div class="flex space-x-2 flex-wrap w-4/5 justify-center">
    <quickLink v-for="(link, index) in links" :key="index" :title="link.title" :description="link.description" :logo="link.logo" />    
  </div>
  </div>
</template>

<style scoped>

</style>
