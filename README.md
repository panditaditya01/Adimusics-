# Adimusics-
Here you can find any type of music
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Music Streaming</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Search and Play Music</h1>
    <input type="text" id="searchBox" onkeyup="searchMusic()" placeholder="Type song or artist...">
    <div id="results"></div>
    <audio id="audioPlayer" controls></audio>

    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    text-align: center;
    padding: 20px;
}

h1 {
    color: #333;
}

input[type="text"] {
    width: 80%;
    padding: 10px;
    margin-bottom: 20px;
    font-size: 16px;
}

#results div {
    background-color: #fff;
    border: 1px solid #ddd;
    padding: 10px;
    margin: 5px;
    cursor: pointer;
}

#results div:hover {
    background-color: #f0f0f0;
}

audio {
    margin-top: 20px;
}
const musicData = [
    { song: "Shape of You", artist: "Ed Sheeran", file: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" },
    { song: "Blinding Lights", artist: "The Weeknd", file: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3" },
    { song: "Levitating", artist: "Dua Lipa", file: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3" },
    { song: "Tum Hi Ho", artist: "Arijit Singh", file: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-4.mp3" },
    { song: "Despacito", artist: "Luis Fonsi", file: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-5.mp3" }
];

function searchMusic() {
    const input = document.getElementById('searchBox').value.toLowerCase();
    const results = document.getElementById('results');
    results.innerHTML = '';

    const filteredMusic = musicData.filter(m => 
        m.song.toLowerCase().includes(input) || 
        m.artist.toLowerCase().includes(input)
    );

    filteredMusic.forEach(m => {
        const div = document.createElement('div');
        div.innerHTML = `<strong>${m.song}</strong> by ${m.artist}`;
        div.onclick = () => playMusic(m.file);
        results.appendChild(div);
    });
}

function playMusic(file) {
    const player = document.getElementById('audioPlayer');
    player.src = file;
    player.play();
}
