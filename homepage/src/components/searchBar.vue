<script setup>
	import { ref } from "vue";

	let inputContent = ref("");
	let searchEngine = "https://search.brave.com/search?q=";
	let autolinks = [
		{
			locater: "@y ",
			url: "https://www.youtube.com/results?search_query=",
		},
		{
			locator: "@w ",
			url: "https://www.wolframalpha.com/input?i=",
		},
		{
			locator: "@p ",
			url: "https://www.phind.com/search?q=",
		},
	];

	const isValidUrl = () => {
		var urlPattern = new RegExp(
			"^(https?:\\/\\/)?" + // validate protocol
				"((([a-z\\d]([a-z\\d-]*[a-z\\d])*)\\.)+[a-z]{2,}|" + // validate domain name
				"((\\d{1,3}\\.){3}\\d{1,3}))" + // validate OR ip (v4) address
				"(\\:\\d+)?(\\/[-a-z\\d%_.~+]*)*" + // validate port and path
				"(\\?[;&a-z\\d%_.~+=-]*)?" + // validate query string
				"(\\#[-a-z\\d_]*)?$",
			"i"
		); // validate fragment locator
		return !!urlPattern.test(inputContent.value);
	};

	const isUsingAutoLinks = () => {
		let autolinkIndex = -1;
		for (let i = 0; i < autolinks.length; i++) {
			const pattern = new RegExp(`^${autolinks[i].locater}`);
			if (pattern.test(inputContent.value)) {
				autolinkIndex = i;
				break;
			}
		}
		return autolinkIndex;
	};

	function search() {
		if (inputContent.value != "") {
			if (isUsingAutoLinks() == -1) {
				if (isValidUrl() == true) {
					window.location.href = inputContent.value;
				} else {
					window.location.href = `${searchEngine}${inputContent.value}`;
				}
			} else {
				window.location.href = `${
					autolinks[isUsingAutoLinks()].url
				}${encodeURIComponent(inputContent.value.slice(3))}`;
			}
		}
	}
</script>

<template>
	<div class="container flex justify-center mb-7">
		<label class="input input-bordered flex items-center gap-2 w-3/5 h-14 pr-1">
			<input
				type="text"
				class="grow"
				v-model="inputContent"
				@keyup.enter="search"
				placeholder="Search"
				autofocus
			/>
			<button class="btn btn-ghost">
				<svg
					@click="search"
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 16 16"
					fill="currentColor"
					class="w-6 h-6 opacity-70 cursor-pointer"
				>
					<path
						fill-rule="evenodd"
						d="M9.965 11.026a5 5 0 1 1 1.06-1.06l2.755 2.754a.75.75 0 1 1-1.06 1.06l-2.755-2.754ZM10.5 7a3.5 3.5 0 1 1-7 0 3.5 3.5 0 0 1 7 0Z"
						clip-rule="evenodd"
					/>
				</svg>
			</button>
		</label>
	</div>
</template>

<style scoped></style>
