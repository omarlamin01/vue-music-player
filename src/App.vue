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
        name: "song title",
        artist: "Test",
        album: "Test",
        cover: "https://picsum.photos/200/200",
        url: require("@/assets/Tracks/1.mp3"),
        favorited: true,
      },

      songs: [
        {
          name: "Mekanın Sahibi",
          artist: "Norm Ender",
          cover:
            "https://picsum.photos/200/200",
          source:
            "https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/1.mp3",
          url: "https://www.youtube.com/watch?v=z3wAjJXbYzA",
          favorited: false,
        },
        {
          name: "Everybody Knows",
          artist: "Leonard Cohen",
          cover:
            "https://picsum.photos/200/200",
          source:
            "https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/2.mp3",
          url: "https://www.youtube.com/watch?v=Lin-a2lTelg",
          favorited: true,
        },
        {
          name: "Extreme Ways",
          artist: "Moby",
          cover:
            "https://picsum.photos/200/200",
          source:
            "https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/3.mp3",
          url: "https://www.youtube.com/watch?v=ICjyAe9S54c",
          favorited: false,
        },
        {
          name: "Butterflies",
          artist: "Sia",
          cover:
            "https://picsum.photos/200/200",
          source:
            "https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/4.mp3",
          url: "https://www.youtube.com/watch?v=kYgGwWYOd9Y",
          favorited: false,
        },
        {
          name: "The Final Victory",
          artist: "Haggard",
          cover:
            "https://picsum.photos/200/200",
          source:
            "https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/5.mp3",
          url: "https://www.youtube.com/watch?v=0WlpALnQdN8",
          favorited: true,
        },
        {
          name: "Genius ft. Sia, Diplo, Labrinth",
          artist: "LSD",
          cover:
            "https://picsum.photos/200/200",
          source:
            "https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/6.mp3",
          url: "https://www.youtube.com/watch?v=HhoATZ1Imtw",
          favorited: false,
        },
        {
          name: "The Comeback Kid",
          artist: "Lindi Ortega",
          cover:
            "https://picsum.photos/200/200",
          source:
            "https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/7.mp3",
          url: "https://www.youtube.com/watch?v=me6aoX0wCV8",
          favorited: true,
        },
        {
          name: "Overdose",
          artist: "Grandson",
          cover:
            "https://picsum.photos/200/200",
          source:
            "https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/8.mp3",
          url: "https://www.youtube.com/watch?v=00-Rl3Jlx-o",
          favorited: false,
        },
        {
          name: "Rag'n'Bone Man",
          artist: "Human",
          cover:
            "https://picsum.photos/200/200",
          source:
            "https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/9.mp3",
          url: "https://www.youtube.com/watch?v=L3wKzyIN1yk",
          favorited: false,
        },
      ],
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
