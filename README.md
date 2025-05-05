# music-player-using-javascript
<title>Music Player</title> <style> body { font-family: Arial, sans-serif; display: flex; justify-content: center; align-items: center; height: 100vh; background-color: #1e1e1e; color: white; }
    .player {
        background: #333;
        padding: 20px;
        border-radius: 10px;
        text-align: center;
        box-shadow: 0px 0px 10px rgba(255, 255, 255, 0.2);
    }

    .controls {
        display: flex;
        justify-content: center;
        gap: 10px;
        margin-top: 15px;
    }

    button {
        background-color: #6200ea;
        color: white;
        border: none;
        padding: 10px 20px;
        font-size: 20px;
        cursor: pointer;
        border-radius: 5px;
    }

    button:hover {
        background-color: #3700b3;
    }

    #volume {
        width: 80%;
        margin-top: 15px;
    }
</style>
<div class="player">
    <h2>Simple Music Player</h2>
    <audio id="audio" src="song1.mp3"></audio>
    <div class="controls">
        <button id="prev">⏮</button>
        <button id="play">▶</button>
        <button id="next">⏭</button>
    </div>
    <input type="range" id="volume" min="0" max="1" step="0.1">
</div>

<script>
    const audio = document.getElementById("audio");
    const playButton = document.getElementById("play");
    const prevButton = document.getElementById("prev");
    const nextButton = document.getElementById("next");
    const volumeControl = document.getElementById("volume");

    const songs = ["song1.mp3", "song2.mp3", "song3.mp3"];
    let songIndex = 0;

    playButton.addEventListener("click", () => {
        if (audio.paused) {
            audio.play();
            playButton.innerText = "⏸";
        } else {
            audio.pause();
            playButton.innerText = "▶";
        }
    });

    nextButton.addEventListener("click", () => {
        songIndex = (songIndex + 1) % songs.length;
        audio.src = songs[songIndex];
        audio.play();
        playButton.innerText = "⏸";
    });

    prevButton.addEventListener("click", () => {
        songIndex = (songIndex - 1 + songs.length) % songs.length;
        audio.src = songs[songIndex];
        audio.play();
        playButton.innerText = "⏸";
    });

    volumeControl.addEventListener("input", () => {
        audio.volume = volumeControl.value;
    });
</script>
