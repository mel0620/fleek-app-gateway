<template>
	<div id="q-app">
		<div v-if="!loading">
			<router-view />
		</div>
		<div v-else style="height: 100vh; width: 100vw; background-color: #202124" class="row items-center justify-center">
			<q-spinner
				color="white"
				size="3em"
			/>
		</div>
	</div>
</template>

<script>
export default {
	name: "App",
	data: () => ({
		loading: true
	}),
	created() {
		window.addEventListener("load", () => {
			setTimeout(() => {
				this.loading = false;
			}, 3000);
		});
	}
}
</script>