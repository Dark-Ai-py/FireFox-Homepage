<script setup>
import searchBar from './components/searchBar.vue'
import quickLink from './components/quickLink.vue';
import { ref } from 'vue';

const links = ref([{
  title: "youtube",
  description: "videos",
  logo: "https://m.youtube.com/static/apple-touch-icon-114x114-precomposed.png",
url: "https://www.youtube.com/"
},])

const addlink = (newLink) => {
  const genLogo = `https://besticon-demo.herokuapp.com/icon?url=${newLink.url}&size=80..120..200`
  links.value.push({title: newLink.title, description: newLink.description, logo: genLogo, url: newLink.url})
}


const theme = 'dim'

</script>

<template>
  <div class="flex flex-col justify-center w-screen h-screen items-center" :data-theme="theme">
  <searchBar />
  <div class="flex space-x-2 flex-wrap w-4/5 justify-center">
    <quickLink v-for="link in links" :key="link" :title="link.title" :description="link.description" :logo="link.logo" :url="link.url" />    
  </div>
  <button class="btn" onclick="my_modal_1.showModal()">open modal</button>
  <dialog id="my_modal_1" class="modal">
    <div class="modal-box">
      <h3 class="font-bold text-lg">Add a Link</h3>
      <p class="py-4">Name</p><input type="text" class="input mt-2">
      <div class="modal-action">
        <form method="dialog">
          <!-- if there is a button in form, it will close the modal -->
          <button class="btn">Close</button>
          <button class="btn btn-primary ml-2">Submit</button>
        </form>
      </div>
    </div>
  </dialog>
  </div>
</template>

<style scoped>

</style>
