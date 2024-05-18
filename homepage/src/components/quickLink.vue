<script setup>
	const { title, logo, url } = defineProps(["title", "logo", "url"]);

	function click() {
		window.location.href = url;
	}
</script>

<template>
	<button
		class="btn w-fit h-fit flex justify-center items-center flex-col gap-0 pr-2 pl-2"
		@click.prevent="click"
	>
		<div class="avatar pt-2">
			<div class="w-24 h-24 rounded">
				<img :src="logo" />
			</div>
		</div>
		<span class="badge mt-2 mb-1">{{ title }}</span>
	</button>
</template>

<style scoped>
	.h-38 {
		height: 9.5rem;
	}
</style>
