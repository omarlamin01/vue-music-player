<template>
  <div id="app">
    <header>
      <h1>Music player</h1>
    </header>
    <main>
		<div class="player">
			<div class="track">
				<h2 class="title">
					{{ current.name }} - 
					<span>{{ current.artist }}</span>
				</h2>
				<img 
					class="cover"
					:src="current.cover" 
					alt="cover"
				>
				<!-- progress bar -->
				<div class="progress">
					<progress class="progress-bar" :max="player.duration" :value="player.currentTime" />
				</div>
			</div>
			
			<div class="player-controls">
				<button
					v-if="!isPlaying"
					class="player-controls-button"
					@click="playTrack()"
				>
					<i class="fas fa-play"></i>
				</button>
				<button
					v-else-if="isPlaying"
					class="player-controls-button" 
					@click="pauseTrack()"
				>
					<i class="fas fa-pause"></i>
				</button>
				<button class="player-controls-button" @click="prev()">
					<i class="fas fa-step-backward"></i>
				</button>
				<button class="player-controls-button" @click="next()">
					<i class="fas fa-step-forward"></i>
				</button>
				<button class="player-controls-button" @click="random = !random">
					<i class="fas fa-random"></i>
				</button>
				<button class="player-controls-button" @click="songs[index].favorited = !songs[index].favorited">
					<i class="fas fa-random"></i>
				</button>
				<button class="player-controls-button" @click="fastForward()">
					<i class="fas fa-fast-forward"></i>
				</button>
				<button class="player-controls-button" @click="fastBackward()">
					<i class="fas fa-fast-backward"></i>
				</button>
			</div>
		</div>
	</main>
  </div>
</template>

<script>

export default {
	name: "App",
	data() {
		return {
			current: {},
			index: 0,
			songs: [
				{
				name: "Mekanın Sahibi",
				artist: "Norm Ender",
				cover: "https://picsum.photos/200/200",
				source:
					"https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/1.mp3",
				url: require("@/assets/Tracks/1.mp3"),
				favorited: false,
				},
				{
				name: "Everybody Knows",
				artist: "Leonard Cohen",
				cover: "https://picsum.photos/200/200",
				source:
					"https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/2.mp3",
				url: require("@/assets/Tracks/2.mp3"),
				favorited: true,
				},
				{
				name: "Extreme Ways",
				artist: "Moby",
				cover: "https://picsum.photos/200/200",
				source:
					"https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/3.mp3",
				url: require("@/assets/Tracks/3.mp3"),
				favorited: false,
				},
				{
				name: "Butterflies",
				artist: "Sia",
				cover: "https://picsum.photos/200/200",
				source:
					"https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/4.mp3",
				url: require("@/assets/Tracks/4.mp3"),
				favorited: false,
				},
				{
				name: "The Final Victory",
				artist: "Haggard",
				cover: "https://picsum.photos/200/200",
				source:
					"https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/5.mp3",
				url: require("@/assets/Tracks/5.mp3"),
				favorited: true,
				},
				{
				name: "Genius ft. Sia, Diplo, Labrinth",
				artist: "LSD",
				cover: "https://picsum.photos/200/200",
				source:
					"https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/6.mp3",
				url: require("@/assets/Tracks/6.mp3"),
				favorited: false,
				},
				{
				name: "The Comeback Kid",
				artist: "Lindi Ortega",
				cover: "https://picsum.photos/200/200",
				source:
					"https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/7.mp3",
				url: require("@/assets/Tracks/7.mp3"),
				favorited: true,
				},
				{
				name: "Overdose",
				artist: "Grandson",
				cover: "https://picsum.photos/200/200",
				source:
					"https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/8.mp3",
				url: require("@/assets/Tracks/8.mp3"),
				favorited: false,
				},
				{
				name: "Rag'n'Bone Man",
				artist: "Human",
				cover: "https://picsum.photos/200/200",
				source:
					"https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/9.mp3",
				url: require("@/assets/Tracks/9.mp3"),
				favorited: false,
				},
			],
			player: new Audio(),
			isPlaying: false,
			random: false,
			repeat: true,
		};
	},
	methods: {
		playTrack() {
			this.player.play();
			this.player.autoplay = this.repeat;
			this.isPlaying = true;
			this.player.addEventListener('ended', function() {
				this.current = this.songs[this.index];
				this.player.src = this.current.url;
				console.log('>>> ended')
				console.log('>>> ' + this.current)
			});
		},
		pauseTrack() {
			this.player.pause();
			this.isPlaying = false;
		},
		next() {
			if (this.random) {
				if (Math.floor(Math.random() * this.songs.length) != this.index) {
					this.index = Math.floor(Math.random() * this.songs.length);
				} else {
					this.index++;
				}

			} else {
				this.index++;
			}
			if (this.index > this.songs.length - 1) {
				this.index = 0;
			}
			this.current = this.songs[this.index];
			this.player.src = this.current.url;
			if (this.isPlaying) {
				this.playTrack();
			} else {
				this.pauseTrack();
			}
		},
		prev () {
			if (this.random) {
				if (Math.floor(Math.random() * this.songs.length) != this.index) {
					this.index = Math.floor(Math.random() * this.songs.length);
				} else {
					this.index--;
				}
			} else {
				this.index--;
			}
			if (this.index < 0) {
				this.index = this.songs.length - 1;
			}
			this.current = this.songs[this.index];
			this.player.src = this.current.url;
			if (this.isPlaying) {
				this.playTrack();
			} else {
				this.pauseTrack();
			}
		},
		fastForward() {
			/*
			this.current = this.songs[this.songs.length - 1];
			this.player.src = this.current.url;
			if (this.isPlaying) {
				this.playTrack();
			} else {
				this.pauseTrack();
			}
			*/
			this.player.currentTime += 15;
		},
		fastBackward() {
			/*
			this.current = this.songs[0];
			this.player.src = this.current.url;
			if (this.isPlaying) {
				this.playTrack();
			} else {
				this.pauseTrack();
			}
			*/
			this.player.currentTime -= 15;
		},
	},
	created() {
		this.player.pause();
		this.current = this.songs[this.index];
		this.player.src = this.current.url;
	},
	};
</script>

<style scoped>
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
.title {
	font-size: 32px;
	font-weight: 700;
	text-transform: uppercase;
	text-align: center;
}
.cover {
	width: 200px;
	height: 200px;
}
.progress progress {
	width: 200px;
	height: 5px;
	border-radius: 99999999999999px;
	margin: 16px;
}
</style>
