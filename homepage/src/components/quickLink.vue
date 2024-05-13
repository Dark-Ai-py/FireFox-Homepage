<script setup>

const {title, description, logo} = defineProps(['title', 'description', 'logo'])

function click() {
    alert('hi');
}

</script>

<template>
    <button class="btn w-32 h-36 flex justify-center items-center">
        <div class="avatar">
            <div class="w-24 rounded">
                <img :src="logo" />
            </div>
        </div>
        <span class="badge">{{ title }}</span>
    </button>
</template>

<style scoped>

</style>