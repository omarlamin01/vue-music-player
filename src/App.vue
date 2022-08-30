<template>
	<div id="app">
		<header>
			<h1>Music player</h1>
		</header>
		<main>
			<div class="player">
				<h2 class="song-title">{{ current.title }}</h2>
			</div>
		</main>
	</div>
</template>

<script>
export default {
	name: "App",
	data() {
		return {
			current: {
				title: "song title",
				artist: "Test",
				album: "Test",
				cover: "https://picsum.photos/200/200",
				file: "https://picsum.photos/200/200",
				duration: "00:00"
			}
		};
	},
	methods: {},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	padding: 0;
	margin: 0;
}

header {
	display: flex;
	justify-content: center;
	align-items: center;
	padding: 20px;
	background-color: #212121;
	color: #fff;
}
</style>
