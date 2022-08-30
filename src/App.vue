<template>
  <div id="app">
    <header>
      <h1>Music player</h1>
    </header>
    <main>
		<div class="player">
			<div class="track">
				<h2>{{ current.name }} - <span>{{ current.artist }}</span></h2>
				<img :src="current.cover" alt="cover">
				<!-- progress bar -->
				<div class="progress">
					<progress class="progress-bar" :max="player.duration" :value="player.currentTime" />
				</div>
			</div>
			
			<div class="player-controls">
				<button
					v-if="!isPlaying"
					class="player-controls-button"
					@click="togglePlay"
				>
					<i class="fas fa-play"></i>
				</button>
				<button
					v-else-if="isPlaying"
					class="player-controls-button" 
					@click="togglePlay()"
				>
					<i class="fas fa-pause"></i>
				</button>
				<button class="player-controls-button" @click="togglePlay()">
					<i class="fas fa-stop"></i>
				</button>
				<button class="player-controls-button" @click="togglePlay()">
					<i class="fas fa-step-backward"></i>
				</button>
				<button class="player-controls-button" @click="togglePlay()">
					<i class="fas fa-step-forward"></i>
				</button>
				<button class="player-controls-button" @click="togglePlay()">
					<i class="fas fa-random"></i>
				</button>
				<button class="player-controls-button" @click="togglePlay()">
					<i class="fas fa-redo-alt"></i>
				</button>
				<button class="player-controls-button" @click="togglePlay()">
					<i class="fas fa-undo-alt"></i>
				</button>
				<button class="player-controls-button" @click="togglePlay()">
					<i class="fas fa-fast-forward"></i>
				</button>
				<button class="player-controls-button" @click="togglePlay()">
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
		index: 1,
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
    };
  },
  methods: {
	togglePlay() {
		if (this.isPlaying) {
			this.player.pause();
		} else {
			this.player.play();
		}
		this.isPlaying = !this.isPlaying;
	},
  },
  created() {
    this.current = this.songs[4];
    this.player.src = this.current.url;
  },
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
*:focus {
  outline: none;
}
html {
  background: #f2f2f2;
}
body {
  margin: 0;
  font-family: "Raleway", sans-serif;
}
h1 {
  margin: 0;
  font-size: 33px;
  color: #fff;
  padding: 0 10%;
}
h3 {
  margin: 0;
  font-size: 17px;
  font-weight: 500;
  color: #ccc;
  padding: 0 10%;
}
.container {
  display: block;
  width: 100%;
  height: 750px;
  margin: auto;
  overflow: hidden;
  background-image: url("https://mariongrandvincent.github.io/HTML-Personal-website/img-codePen/bg-music-player.jpg");
  background-repeat: repeat;
  background-size: cover;
}
.music-player {
  display: block;
  position: relative;
  width: 400px;
  height: 570px;
  margin: auto;
  margin-top: 6%;
  border-radius: 0 0 10px 10px;
  background: transparent
    linear-gradient(to bottom, rgba(10, 11, 31, 0.9) 50%, rgb(10, 11, 31) 70%)
    repeat scroll 0 0;
  box-shadow: 1px 10px 20px 5px #222;
}
.cover {
  float: left;
  width: 100%;
  height: 66%;
}
.cover img {
  display: block;
  position: absolute;
  top: 8%;
  left: 14%;
  width: 70%;
  margin: auto;
  text-align: center;
}
.titre {
  float: left;
  width: 100%;
}
.lecteur {
  width: 100%;
  display: block;
  height: auto;
  position: relative;
  float: left;
}
.mejs__button > button:focus {
  outline: 0px dotted #999;
}
.mejs__container {
  position: relative;
  background-color: transparent;
  min-width: auto !important;
}
.mejs__controls {
  padding: 0 10%;
  background: transparent !important;
  display: block;
  position: relative;
}
.mejs__controls div {
  display: block;
  float: left;
  position: relative;
}
.mejs__controls .mejs__playpause-button {
  position: absolute !important;
  right: 8%;
  bottom: 95%;
  width: 40px;
}
.mejs__controls .mejs__playpause-button button {
  display: block;
  width: 40px;
  height: 40px;
  padding: 0;
  border: 0;
  font-family: FontAwesome;
  font-size: 23px;
  color: #5bbb95;
  background: transparent;
  padding: 0;
  margin: 0;
}
.mejs__controls .mejs__play button:before {
  content: "\f04b";
}
.mejs__controls .mejs__pause button:before {
  content: "\f04c";
}
.mejs__controls .mejs__volume-button button {
  display: block;
  width: 40px;
  height: 40px;
  padding: 0;
  border: 0;
  font-family: FontAwesome;
  font-size: 20px;
  color: #5bbb95;
  background: transparent;
  margin: 0;
  padding: 0;
}
.mejs__controls .mejs__mute button:before {
  content: "\f028";
}
.mejs__controls .mejs__unmute button:before {
  content: "\f026";
}
.mejs__controls .mejs__time {
  width: 100%;
  margin-top: 7%;
  margin-bottom: 3%;
  color: #fff;
  height: auto;
  padding: 0;
  overflow: visible;
  min-width: 100%;
}
.mejs__controls .mejs__time span {
  font-size: 15px;
}
.mejs__controls span.mejs__duration {
  float: right;
  text-align: right;
  color: #ccc;
}
.mejs__controls span.mejs__currenttime {
  font-weight: 700;
  float: left;
}
.mejs__controls .mejs__time-rail {
  width: 100%;
  margin: 0;
}
.mejs__controls .mejs__time-rail span {
  position: absolute;
  top: 0;
  width: 100%;
  height: 4px;
  border-radius: 50px;
  cursor: pointer;
}
.mejs__controls .mejs__time-rail .mejs__time-loaded {
  background: rgba(255, 255, 255, 0.2);
}
.mejs__controls .mejs__time-rail .mejs__time-float {
  display: none;
  top: -40px;
  width: 40px;
  height: 25px;
  margin-left: 0px;
  text-align: center;
  font-size: 10px;
  background: #fff;
  border: 0;
}
.mejs__controls .mejs__time-rail .mejs__time-float-current {
  display: block;
  position: relative;
  top: 0;
  margin: 0;
  line-height: 26px;
  color: #100d28;
}
.mejs__controls .mejs__time-rail .mejs__time-float-corner {
  top: auto;
  bottom: -9px;
  left: 50%;
  width: 0;
  height: 0;
  border-top: 6px solid #fff;
  border-right: 6px solid transparent;
  border-left: 6px solid transparent;
}
.mejs__controls .mejs__time-rail .mejs__time-current {
  background: #5bbb95 none repeat scroll 0 0;
}
.mejs__controls .mejs__time-handle {
  display: none;
}
.mejs__controls .mejs__volume-button {
  position: relative;
  position: absolute !important;
  top: 70px;
  right: 25%;
  width: 40px;
  height: 40px;
}
.mejs__controls .mejs__horizontal-volume-slider {
  display: block;
  position: absolute !important;
  position: relative;
  top: 70px;
  right: 10%;
  width: 60px;
  height: 4px;
  margin-top: 18px;
  border-radius: 50px;
  line-height: 11px;
}
.mejs__controls .mejs__horizontal-volume-slider .mejs__horizontal-volume-total,
.mejs__controls
  .mejs__horizontal-volume-slider
  .mejs__horizontal-volume-current {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0.1);
}
.mejs__controls
  .mejs__horizontal-volume-slider
  .mejs__horizontal-volume-current {
  background: #fff;
}
</style>
