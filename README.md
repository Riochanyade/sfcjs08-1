# sfcjs08-1

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>情報基礎第8回</title>
  </head>
  <body>
   <audio src="assets/Sean_Fournier_-_06_-_Falling_For_You_Piano_Version.mp3"></audio>

   <button id="play-button" type="button">再生</button>
   <button id="pause-button" type="button">停止</button> 

   <input id ="volume" type="range" min="0" max="1" step="0.1" value="1" >
   <input type ="range" id="seek-bar" min="0" step="0.5" value="0">

   <script src="scripts/main.js"></script>
　</body>
</html>


function play(){
    let player =document.querySelector("audio");
     player.play();
}

function pause(){
    let player =document.querySelector("audio");
    player.pause();
}

function rewind(sec){
    let player =document.querySelector("audio");
    player.currentTime =player.currentTime - sec;
    return sec;
}

function updateVolume(){
    let slider = document.querySelector("#volume");
    let value = slider.value
    let player = document.querySelector("audio");
    player.volume = value;
}

function configureSeekbar(){
    let seekbar = document.querySelector("#seek-bar");
    let player  = document.querySelector("audio");
    seekbar.max = player.duration;
}

function updateCurrentTime(){
    let seekbar=document.querySelector("#seek-bar");
    let player=document.querySelector("audio");
    player.currentTime=seekbar.value;
}

function updateSeekbar(){
    let seekbar= document.querySelector("#seek-bar");
    let player=document.querySelector("audio");
    seekbar.value=player.currentTime;
}




let playButton = document.querySelector("#play-button");
playButton.addEventListener("click", play);

let pauseButton = document.querySelector("#pause-button");
pauseButton.addEventListener("click", pause);

let volume = document.querySelector("#volume");
volume.addEventListener("input", updateVolume);

let player = document.querySelector("audio");
player.addEventListener("canplay", configureSeekbar);
player.addEventListener("timeupdate", updateSeekbar);

let seekbar = document.querySelector("#seek-bar");
seekbar.addEventListener("input", updateCurrentTime);