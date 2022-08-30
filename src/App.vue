<template>
  <div id="app">
	<header>
		<h1>Music player</h1>
	</header>
	<main>
		<div class="player">
			<h2 class="song-title"></h2>
		</div>
	</main>
  </div>
</template>

<script>
export default {
  name: "App",
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
  margin-top: 60px;
}
</style>
