<script setup>
import searchBar from './components/searchBar.vue'
import quickLink from './components/quickLink.vue';
import { ref } from 'vue';



const links = ref([{
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
},])
function updateLinks() {
  for(let i; numOfLinks() >= i; i++) {
    links.push(getLink[i]);
  }
}

function addLink(newlink) {
  let currentLinks = localStorage.getItem('links');
  currentLinks = JSON.parse(currentLinks);
  let newLinks = JSON.stringify([...currentLinks, {
    title: newlink.title,
    description: newlink.description,
    logo: newlink.logo
  }]);
  localStorage.setItem('links', newLinks);
}

function getLink(i) {
  let rawLinks = localStorage.getItem('links');
  rawLinks = JSON.parse(rawLinks)
  let cleanLinks = [...rawLinks];
  return cleanLinks[i];
}

function numOfLinks() {
  let rawLinks = localStorage.getItem('links');
  rawLinks = JSON.parse(rawLinks)
  let cleanLinks = [...rawLinks];
  return cleanLinks.length;
}

const theme = 'dim'

</script>

<template>
  <div class="flex flex-col justify-center w-screen h-screen items-center" :data-theme="theme">
  <searchBar />
  <div class="flex space-x-2 flex-wrap w-4/5 justify-center">
    <quickLink v-for="(link, index) in links" :key="index" :title="link.title" :description="link.description" :logo="link.logo" />    
  </div>
    <button class="btn" @click.prevent="addLink(links[1]), updateLinks">addlink</button>
  </div>
</template>

<style scoped>

</style>
