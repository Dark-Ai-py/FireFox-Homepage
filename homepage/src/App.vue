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
		{
			title: "iCloud",
			logo: "https://t1.gstatic.com/faviconV2?client=SOCIAL&type=FAVICON&fallback_opts=TYPE,SIZE,URL&url=http://icloud.com&size=128",
			url: "https://www.icloud.com/",
		},
	]);

	let tokenActiveCalender = ref(true);
	// false for google
	// true for apple

	const theme = "dim";
</script>

<template>
	<div class="flex flex-col justify-center w-screen h-screen items-center" :data-theme="theme">
		<searchBar />
		<div class="flex space-x-2 flex-wrap w-4/5 justify-center">
			<quickLink
				v-for="link in links"
				:key="link"
				:title="link.title"
				:logo="link.logo"
				:url="link.url"
				:canClick="true"
			/>
			<quickLink
				:title="`Calender`"
				:logo="`https://calendar.google.com/googlecalendar/images/favicons_2020q4/calendar_31_256.ico`"
				:canClick="false"
				onclick="my_modal_2.showModal()"
			/>
			<dialog id="my_modal_2" class="modal m-h-800">
				<div class="modal-box max-w-fit m-h-800 overflow-hidden">
					<div class="join w-full">
						<input
							class="join-item btn btn-square w-fit p-4 ml-auto"
							type="radio"
							name="options"
							checked="checked"
							aria-label="Apple Calender"
							@click="tokenActiveCalender = true"
						/>
						<input
							class="join-item btn btn-square w-fit p-4 mr-auto"
							type="radio"
							name="options"
							aria-label="Google Calender"
							@click="tokenActiveCalender = false"
						/>
					</div>
					<div class="divider"></div>
					<!-- <iframe
						src="https://calendar.google.com/calendar/embed?height=600&wkst=1&ctz=America%2FDenver&bgcolor=%23ffffff&showPrint=0&showCalendars=0&title=Google&src=ZjhudWh2MWw0OWtsczVidmZncnZnZWNrOW5rdmtua25AaW1wb3J0LmNhbGVuZGFyLmdvb2dsZS5jb20&color=%23D50000"
						style="border-width: 0"
						width="800"
						height="600"
						frameborder="0"
						scrolling="no"
						
					></iframe>

					<iframe
						src="https://calendar.google.com/calendar/embed?height=600&wkst=1&ctz=America%2FDenver&bgcolor=%23ffffff&showPrint=0&showCalendars=0&mode=WEEK&title=Google&src=dGhlc29oYW44NEBnbWFpbC5jb20&color=%237CB342"
						style="border-width: 0"
						width="800"
						height="600"
						frameborder="0"
						scrolling="no"
						:class="tokenActiveCalender ? `opacity-100` : `opacity-0 h-0`"
						class="rounded"
					></iframe> -->
					<iframe
						src="https://calendar.google.com/calendar/embed?height=600&wkst=1&ctz=America%2FDenver&bgcolor=%23ffffff&showCalendars=0&showPrint=0&title=Apple&mode=WEEK&src=ZWRzajM3djM1bjEzbnFhN3FibmY2dmkydTVuZ25hZGxAaW1wb3J0LmNhbGVuZGFyLmdvb2dsZS5jb20&src=ZjhudWh2MWw0OWtsczVidmZncnZnZWNrOW5rdmtua25AaW1wb3J0LmNhbGVuZGFyLmdvb2dsZS5jb20&color=%23D81B60&color=%23D50000"
						style="border-width: 0"
						width="800"
						height="600"
						frameborder="0"
						scrolling="no"
						:class="tokenActiveCalender ? `opacity-100` : `opacity-0 h-0`"
						class="rounded"
					></iframe>
					<iframe
						src="https://calendar.google.com/calendar/embed?height=600&wkst=1&ctz=America%2FDenver&bgcolor=%23ffffff&showCalendars=0&showPrint=0&mode=WEEK&src=dGhlc29oYW44NEBnbWFpbC5jb20&color=%237CB342"
						style="border-width: 0"
						width="800"
						height="600"
						frameborder="0"
						scrolling="no"
						:class="tokenActiveCalender ? `opacity-0 h-0` : `opacity-100`"
						class="rounded"
					></iframe>
				</div>
				<form method="dialog" class="modal-backdrop">
					<button>close</button>
				</form>
			</dialog>
		</div>
	</div>
</template>

<style scoped>
	.m-h-800 {
		max-height: 800px;
	}
</style>
