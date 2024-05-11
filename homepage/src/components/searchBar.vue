<script setup>
    import { ref } from 'vue';

    let inputContent = ref("");
    let searchEngine = 'https://search.brave.com/search?q='

    function search() {
        if((inputContent.value) != "") {
        window.location.href = `${searchEngine}${inputContent.value}`;
        }
    }

</script>

<template>
    <div class="container flex justify-center mt-64">
        <label class="input input-bordered flex items-center gap-2 w-3/5 h-14 pr-1">
            <input type="text" class="grow" v-model="inputContent" @keyup.enter="search" placeholder="Search" />
            <button class="btn btn-ghost">
            <svg @click="search" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16" fill="currentColor" class="w-6 h-6 opacity-70 cursor-pointer"><path fill-rule="evenodd" d="M9.965 11.026a5 5 0 1 1 1.06-1.06l2.755 2.754a.75.75 0 1 1-1.06 1.06l-2.755-2.754ZM10.5 7a3.5 3.5 0 1 1-7 0 3.5 3.5 0 0 1 7 0Z" clip-rule="evenodd" /></svg>
            </button>
        </label>
    </div>
</template>

<style scoped>

</style>