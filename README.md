# TicTacToe

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.10.0/css/all.min.css"
      integrity="sha512-PgQMlq+nqFLV4ylk1gwUOgm6CtIIXkKwaIHp/PAIWHzig/lKZSEGKEysh0TCVbHJXCLN7WetD8TFecIky75ZfQ=="
      crossorigin="anonymous"
    />
    <link rel="stylesheet" href="css/style.css" />
  </head>
  <body>
    <div class="main_div">
      <div class="main_container music_container">
        <h2 id="title">BROWN MUNDE</h2>
        <h3 id="artist">ISHA</h3>
        <div class="img_container">
          <img src="images/Brown_munde.jpg" />
        </div>
        <audio src="songs/Brown_Munde.mp3"></audio>
        <div class="music_controls">
          <i class="fas fa-backward" id="prev" title="Previous"></i>
          <i class="fas fa-play main_button" id="play" title="Play"></i>
          <i class="fas fa-forward" id="next" title="Next"></i>
        </div>
      </div>
    </div>
    <script>
      const music = document.querySelector("audio");
      const play = document.getElementById("play");
      const img = document.querySelector("img");
      const title = document.getElementById("title");
      const artist = document.getElementById("artist");
      const prev = document.getElementById("prev");
      const next = document.getElementById("next");

      const songs = [
        {
          name: "Brown_munde",
          title: "Brown Munde",
          artist: "Isha",
        },
        {
          name: "Sira_e_hou",
          title: "Sira E Hou",
          artist: "Harshit",
        },
      ];

      let isPlaying = false;

      const playMusic = function () {
        isPlaying = true;
        music.play();
        play.classList.replace("fa-play", "fa-pause");
        img.classList.add("anime");
      };

      // for pause functionality
      const pauseMusic = function () {
        isPlaying = false;
        music.pause();
        play.classList.replace("fa-pause", "fa-play");
        img.classList.remove("anime");
      };

      play.addEventListener("click", () => {
        if (isPlaying) {
          pauseMusic();
        } else {
          playMusic();
        }
      });

      //changing the music data
      const loadSong = (songs) => {
        title.textContent = songs.title;
        artist.textContent = songs.artist;
        music.src = "songs/" + songs.name + ".mp3";
        img.src = "images/" + songs.name + ".jpg";
      };
      songIndex = 0;

      // loadSong(songs[1]);

      const nextSong = () => {
        songIndex = (songIndex + 1) % songs.length;
        loadSong(songs[songIndex]);
        playMusic();
      };

      const prevSong = () => {
        songIndex = (songIndex - 1 + songs.length) % songs.length;
        loadSong(songs[songIndex]);
        playMusic();
      };
      next.addEventListener("click", nextSong);
      prev.addEventListener("click", prevSong);
    </script>
  </body>
</html>




style.css

*,
*::before,
*::after {
  margin: 0;
  padding: 0%;
  box-sizing: border-box;
}

html {
  font-size: 62.5%;
  font-family: "Jost", sans-serif;
}

.main_div {
  width: 100vw;
  height: 100vh;
  background-color: #f6f6f6;
  display: grid;
  place-items: center;
}

.main_container {
  width: 35rem;
  height: 55rem;
  background-color: #ffffff;
  border-radius: 2rem;
  padding: 3rem;
  text-align: center;
  box-shadow: 0 1.2rem 3rem 0.5rem rgba(0, 0, 0, 0.2);
}

.music_container #title {
  text-transform: uppercase;
  letter-spacing: 0.2rem;
  word-spacing: 0.5rem;
  color: #171717;
  margin: 2rem 0.5rem 0;
  font-size: 2.5rem;
  font-weight: 500;
  text-shadow: 0 0.3rem 0.5rem rgba(0, 0, 0, 0.3);
}

.music_container #artist {
  color: #cccaca;
  text-transform: capitalize;
  letter-spacing: 0.1rem;
  font-size: 2rem;
  margin-bottom: 4rem;
  font-weight: 300;
}

.img_container {
  width: 25rem;
  height: 25rem;
  margin: auto;
}

img {
  /* make the img object fit and circle */
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
  box-shadow: 0 1.2rem 3rem 0.5rem rgba(0, 0, 0, 0.4);
}

.music_controls .fas {
  color: #111111;
  font-size: 2rem;
  cursor: pointer;
  filter: drop-shadow(0 1.2rem 3rem 0.5rem rgba(0, 0, 0, 0.4));
}

.music_controls .main_button {
  width: 5rem;
  height: 5rem;
  border-radius: 50%;
  background-color: #111;
  color: #f6f6f6;
  /*add display flex to center the icons*/
  font-size: 1.4rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

.music_controls {
  width: 20rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: auto;
  margin-top: 5rem;
}

.music_controls .fas:hover {
  color: grey;
}

.music_controls .fa-play:hover {
  background-color: #f6f6f6;
  color: #111;
  box-shadow: 0 1rem 2rem 0.2rem rgba(0, 0, 0, 0.4);
}

.anime {
  animation: rotatePlayer 3s linear infinite;
}

@-webkit-keyframes rotatePlayer {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

@-o-keyframes rotatePlayer {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
