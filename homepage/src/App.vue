<script setup>
	import searchBar from "./components/searchBar.vue";
	import quickLink from "./components/quickLink.vue";
	import { ref } from "vue";

	const links = ref([
		{
			title: "Youtube",
			logo: "https://m.youtube.com/static/apple-touch-icon-114x114-precomposed.png",
			url: "https://www.youtube.com/",
		},
		{
			title: "Github",
			logo: "https://github.githubassets.com/assets/apple-touch-icon-180x180-a80b8e11abe2.png",
			url: "https://github.com/",
		},
		{
			title: "Gmail",
			logo: "https://www.gstatic.com/images/branding/product/2x/gmail_2020q4_512dp.png",
			url: "https://mail.google.com/mail/u/0/",
		},
		{
			title: "Drive",
			logo: "https://ssl.gstatic.com/images/branding/product/2x/hh_drive_36dp.png",
			url: "https://drive.google.com/",
		},
	]);

	const theme = "dim";
</script>

<template>
	<div
		class="flex flex-col justify-center w-screen h-screen items-center"
		:data-theme="theme"
	>
		<searchBar />
		<div class="flex space-x-2 flex-wrap w-4/5 justify-center">
			<quickLink
				v-for="link in links"
				:key="link"
				:title="link.title"
				:description="link.description"
				:logo="link.logo"
				:url="link.url"
			/>
		</div>
	</div>
</template>

<style scoped></style>
