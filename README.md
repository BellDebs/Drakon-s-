<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>System Boot - Drakon</title>

<style>

body{
margin:0;
background:#050505;
color:#00ffcc;
font-family:monospace;
overflow-x:hidden;
text-align:center;
}

/* Stars */
.star{
position:absolute;
width:2px;
height:2px;
background:white;
animation:twinkle 4s infinite;
}
@keyframes twinkle{
0%,100%{opacity:0.2;}
50%{opacity:1;}
}

/* Center */
.center{
position:absolute;
top:50%;
left:50%;
transform:translate(-50%,-50%);
width:90%;
max-width:600px;
}

/* Cursor */
.cursor{
display:inline-block;
width:10px;
background:#00ffcc;
margin-left:5px;
animation:blink 1s infinite;
}
@keyframes blink{
50%{opacity:0;}
}

.hidden{display:none;}

input{
padding:12px;
font-size:18px;
border-radius:6px;
border:none;
text-align:center;
width:80%;
}

button{
padding:12px 22px;
margin-top:12px;
background:#00ffcc;
border:none;
cursor:pointer;
border-radius:6px;
font-size:16px;
}

.card{
background:rgba(255,255,255,0.05);
padding:30px;
border-radius:15px;
backdrop-filter:blur(12px);
box-shadow:0 0 25px #00ffcc55;
color:white;
animation:fadeIn 1.5s;
}

@keyframes fadeIn{
from{opacity:0;transform:translateY(20px);}
to{opacity:1;}
}

/* Progress Bar */
.bar{
width:100%;
height:8px;
background:#111;
margin-top:15px;
border-radius:10px;
overflow:hidden;
}
.progress{
height:100%;
width:0%;
background:#00ffcc;
transition:width .3s;
}

#message{
white-space:pre-line;
line-height:1.7;
font-size:18px;
}

#perks{
margin-top:20px;
color:#ffd700;
font-weight:bold;
opacity:0;
transition:1s;
}

.show{
opacity:1 !important;
}

</style>
</head>

<body>

<audio id="music" loop>
<source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3">
</audio>

<!-- Boot -->
<div id="boot" class="center">
<h2 id="bootText"></h2><span class="cursor"></span>

<div class="bar">
<div id="progress" class="progress"></div>
</div>
</div>

<!-- Unlock -->
<div id="unlock" class="center hidden">
<h2>SYSTEM AUTHENTICATION</h2>
<p>Enter Codename</p>
<input id="nameInput" placeholder="Codename">
<br>
<button onclick="checkName()">UNLOCK</button>
<p id="error"></p>
</div>

<!-- Gift -->
<div id="gift" class="center hidden">
<div class="card">
<h1>Welcome, Drakon 🐉</h1>
<p id="message"></p>

<div id="perks">
⚡ SYSTEM PERKS UPGRADED ⚡<br><br>
Writing Skill +100<br>
Wealth +100<br>
Health +100
</div>

</div>
</div>

<script>

/* Stars */
for(let i=0;i<120;i++){
let s=document.createElement("div");
s.className="star";
s.style.top=Math.random()*100+"%";
s.style.left=Math.random()*100+"%";
document.body.appendChild(s);
}

/* Boot Text */
const bootMsg=
"System Initializing...\n"+
"Scanning Identity...\n"+
"Loading Destiny Modules...\n"+
"Synchronizing Future Path...\n"+
"Access Preparing...\n";

let i=0;
let load=0;

function boot(){
if(i<bootMsg.length){
bootText.textContent+=bootMsg.charAt(i);
i++;
setTimeout(boot,30);
}

load+=2;
progress.style.width=load+"%";

if(load<100){
requestAnimationFrame(boot);
}else{
setTimeout(()=>{
boot.classList.add("hidden");
unlock.classList.remove("hidden");
},800);
}
}
boot();

/* Unlock */
let started=false;

function checkName(){
let name=nameInput.value.trim().toLowerCase();

if(name==="drakon"){
unlock.classList.add("hidden");
gift.classList.remove("hidden");

music.play().catch(()=>{});

if(!started){
started=true;
typeMessage();
}

}else{
error.innerText="Identity Not Recognized ❌";
}
}

/* Message Typing */
const msg=`Today marks the rise of greatness.

Emmanuel • Praise • Sunbola

Your journey moves toward success.
Inspiration surrounds you.
Motivation strengthens you.

Soon, you will live the life you envision.

Keep ascending, Drakon.`;

let t=0;

function typeMessage(){
if(t<msg.length){
message.textContent+=msg.charAt(t);
t++;
setTimeout(typeMessage,25);
}else{
setTimeout(()=>{
perks.classList.add("show");
},700);
}
}

</script>

</body>
</html>  transform: translate(-50%,-50%);
  width:90%;
  max-width:600px;
}
.hidden {display:none;}

/* Input and button */
input {
  padding:12px;
  width:80%;
  border:none;
  border-radius:6px;
  text-align:center;
  font-size:18px;
  margin-top: 10px;
}
button {
  padding:12px 22px;
  margin-top:12px;
  background:#00ff99;
  border:none;
  border-radius:6px;
  cursor:pointer;
  font-size:16px;
}

/* Card */
.card {
  background: rgba(255,255,255,0.05);
  padding:30px;
  border-radius:15px;
  backdrop-filter: blur(8px);
  color:white;
  box-shadow:0 0 20px #00ff9955;
}

/* Message styling */
#message {
  white-space: pre-line;
  line-height:1.8;
  font-size:18px;
  color:#00ff99;
  opacity:0;
  transition:1s;
}

/* Dragon */
#dragon {
  font-size:50px;
  margin-bottom:10px;
  animation:dragonPulse 1.5s infinite alternate;
}
@keyframes dragonPulse {
  0%{transform:scale(1); opacity:0.7;}
  100%{transform:scale(1.2); opacity:1;}
}

/* Reward */
#reward {
  margin-top:20px;
  font-weight:bold;
  color: gold;
  font-size:18px;
  opacity:0;
  transition:1s;
}
.show {opacity:1;}

/* Sparkles */
.sparkle {
  position: absolute;
  width:4px;
  height:4px;
  background:white;
  border-radius:50%;
  pointer-events:none;
  animation:sparkleMove 1s forwards;
}
@keyframes sparkleMove {
  0% {transform:translate(0,0) scale(1); opacity:1;}
  100% {transform:translate(var(--x), var(--y)) scale(0); opacity:0;}
}
</style>
</head>
<body>

<!-- Audio -->
<audio id="music" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<!-- Login -->
<div id="login" class="center">
  <h2>System Authentication</h2>
  <input id="nameInput" placeholder="Enter Codename"><br>
  <button onclick="checkLogin()">Unlock</button>
  <p id="error"></p>
</div>

<!-- Gift -->
<div id="gift" class="center hidden">
  <div class="card">
    <div id="dragon">🐉</div>
    <h1>Welcome, Drakon</h1>
    <p id="message"></p>
    <button id="rewardBtn" class="hidden" onclick="showReward()">Accept Reward</button>
    <div id="reward">
      Wealth: <span id="wealth">0</span><br>
      Good Health: <span id="health">0</span><br>
      Happiness: <span id="happiness">0</span>
    </div>
  </div>
</div>

<script>
// check login
function checkLogin(){
  let name = document.getElementById("nameInput").value.trim().toLowerCase();
  if(name === "drakon"){
    document.getElementById("login").classList.add("hidden");
    document.getElementById("gift").classList.remove("hidden");

    // play music
    document.getElementById("music").play().catch(()=>{});

    // show message
    showMessage();
  } else {
    document.getElementById("error").innerText="Identity not recognized ❌";
  }
}

// show message with fade-in
function showMessage(){
  const msg=`Today we celebrate someone extraordinary.\n\nEmmanuel • Praise • Sunbola\n\nMay your life be filled with joy, success, and happiness.\nYour dreams will be realized.\nYour future is bright and unstoppable.\n\nKeep conquering, Drakon! 🥂✨`;
  let messageEl = document.getElementById("message");
  messageEl.innerText = msg;
  setTimeout(()=>{messageEl.style.opacity=1;},1000);
  // show reward button after delay
  setTimeout(()=>{document.getElementById("rewardBtn").classList.remove("hidden");},2000);
}

// show reward with counting and sparkles
function showReward(){
  const rewardEl = document.getElementById("reward");
  rewardEl.classList.add("show");
  document.getElementById("rewardBtn").disabled=true;

  animateValue("wealth",0,100,1000);
  animateValue("health",0,100,1000);
  animateValue("happiness",0,100,1000);

  // small sparkles
  for(let i=0;i<30;i++){
    createSparkle();
  }
}

// counting numbers
function animateValue(id, start, end, duration){
  let obj=document.getElementById(id);
  let range=end-start;
  let current=start;
  let increment=end>start?1:-1;
  let stepTime=Math.abs(Math.floor(duration/range));
  let timer=setInterval(function(){
    current+=increment;
    obj.innerText=current;
    if(current==end){clearInterval(timer);}
  },stepTime);
}

// sparkle effect
function createSparkle(){
  let sparkle=document.createElement("div");
  sparkle.className="sparkle";
  sparkle.style.top=Math.random()*80+"%";
  sparkle.style.left=Math.random()*80+"%";
  sparkle.style.setProperty("--x",(Math.random()*200-100)+"px");
  sparkle.style.setProperty("--y",(Math.random()*-200-50)+"px");
  document.body.appendChild(sparkle);
  setTimeout(()=>{sparkle.remove();},1000);
}
</script>

</body>
</html>
