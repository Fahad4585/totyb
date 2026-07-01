<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<title>تسنيم 🤍</title>

<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Cairo',sans-serif;}
body{
height:100vh;display:flex;justify-content:center;align-items:center;
background:linear-gradient(135deg,#e0c3fc,#8ec5fc);
}

.container{
width:92%;max-width:420px;
background:rgba(255,255,255,.35);
backdrop-filter:blur(20px);
border-radius:28px;
padding:25px;
box-shadow:0 10px 40px rgba(0,0,0,.18);
text-align:center;
position:relative;
}

.name-bg{
position:absolute;top:50%;left:50%;
transform:translate(-50%,-50%) rotate(-15deg);
font-size:5rem;
color:rgba(255,255,255,.2);
pointer-events:none;
}

.page{display:none;animation:fade .8s;}
.page.active{display:block;}
@keyframes fade{from{opacity:0;transform:translateY(15px)}to{opacity:1;transform:none}}

h1,h2{color:#8e44ad;text-shadow:0 2px 5px rgba(255,255,255,.6);margin-bottom:10px;}

input{
width:100%;padding:12px;border-radius:30px;border:none;margin:10px 0;
text-align:center;font-size:1rem;
}

.btn{
background:linear-gradient(45deg,#8e44ad,#c0392b);
color:white;border:none;
padding:12px 25px;
border-radius:50px;
width:100%;margin:8px 0;
font-size:1rem;
cursor:pointer;
}

.date-badge{
background:white;padding:6px 15px;border-radius:20px;
display:inline-block;margin:6px 0;color:#8e44ad;font-weight:bold;
}

.timeline{display:flex;justify-content:center;gap:15px;font-size:2rem;cursor:pointer;margin-top:5px}
.timeline div{color:#8e44ad;transition:.3s}
.timeline div:hover{transform:scale(1.3)}

.music-player{
background:#8e44ad;padding:10px;border-radius:15px;
color:white;display:flex;align-items:center;gap:10px;margin-top:10px;
}
.music-player button{
background:white;color:#8e44ad;border:none;
width:36px;height:36px;border-radius:50%;cursor:pointer;
}
</style>
</head>

<body>

<div class="container">
<div class="name-bg">تسنيم</div>

<div id="page1" class="page active">
<h2>Enter Password 💜</h2>
<input type="password" id="pass" placeholder="اكتب السر...">
<button class="btn" onclick="check()">Unlock 💗</button>
</div>

<div id="page2" class="page">
<h2>My Love Letter 💌</h2>
<p>من أول لحظة شوفتك فيها،  
حسيت إن حياتي اتلوّنت بالراحة والضحكة.</p>
<p>إنتي حكايتي المفضلة… وأجمل لحن في قلبي 🤍</p>
<button class="btn" onclick="go(3)">Next ✨</button>
</div>

<div id="page3" class="page">

<div class="date-badge" id="loveCounter"></div>
<div id="loveMessage"></div>

<div style="margin:15px 0;">
<iframe id="ytPlayer" width="100%" height="180"
style="border-radius:15px;border:none"
src="https://www.youtube.com/embed/Ie5O1KdKUqE?enablejsapi=1&rel=0"
allow="autoplay; encrypted-media"></iframe>
</div>

<div class="music-player">
<div style="flex:1;text-align:right">
<b>أغنيتنا الخاصة 💜</b><br><small>لأنها بتفكرني بتسنيم</small>
</div>
<button onclick="toggleMusic()"><i class="fas fa-play" id="playIcon"></i></button>
</div>

<button class="btn" onclick="showMemory()">🧳 كبسولة الذكريات</button>
<p id="memoryBox"></p>

<h3>رحلتنا 🗺️</h3>
<div class="timeline">
<div onclick="showEvent('10 / 7 / 2023 — بداية الحكاية 💖')">●</div>
<div onclick="showEvent('أول خروجة… وأول ضحكة 🥰')">●</div>
<div onclick="showEvent('أول خلاف… واخترنا بعض 🤍')">●</div>
<div onclick="showEvent('أول بحبك… وكانت وعد عمر 💍')">●</div>
</div>
<p id="eventText"></p>

<button class="btn" onclick="go(4)">Next 🌷</button>
</div>

<div id="page4" class="page">
<h2>Forever & Always ♾️</h2>
<p>مهما الدنيا ودّت بينا…  
هتفضلي أعلى حد عندي،  
وأمان قلبي، وبيتي اللي بارتاح فيه 🤍</p>
<button class="btn" onclick="showFinal()">اقري لما تحبي تطمني 💌</button>
</div>

</div>

<div id="finalLetter" style="position:fixed;top:0;left:0;width:100%;height:100%;
background:rgba(0,0,0,.85);display:none;justify-content:center;align-items:center;
flex-direction:column;color:white;text-align:center;padding:20px;">
<h2>تسنيم…</h2>
<p>أنا معاكي مهما الدنيا تعبتنا،</p>
<p>واختياري ليكي ثابت… دايمًا وأبدًا 🤍</p>
<button class="btn" onclick="this.parentElement.style.display='none'">قفل الرسالة</button>
</div>

<script src="https://www.youtube.com/iframe_api"></script>

<script>
function go(n){
document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
document.getElementById('page'+n).classList.add('active');
}

function check(){
if(document.getElementById('pass').value==="0710") go(2);
}

const memories=[
"أول ضحكة من القلب 🥹",
"أول مكالمة طولت ساعات 📞",
"أول مرة قولنا بحبك 💌",
"أول زعل واتصالحنا 🤍",
"أول وعد ما اتكسرش ✨"
];

function showMemory(){
memoryBox.innerText=memories[Math.floor(Math.random()*memories.length)];
}

function showEvent(t){eventText.innerText=t;}

function showFinal(){finalLetter.style.display="flex";}

function updateLove(){
let start=new Date("2023-07-10"),now=new Date();
let d=Math.floor((now-start)/(1000*60*60*24));
loveCounter.innerText="❤️ "+d+" يوم حب مع تسنيم";

let m="";
if(d<300)m="لسه في أول الحكاية… والأحلى جاي 💞";
else if(d<600)m="بقينا مش ذكرى… بقينا تاريخ 🕊️";
else if(d<900)m="إحنا وطن لبعض 🏡";
else m="العمر كله جنبك قليل يا تسنيم 💍";

loveMessage.innerText=m;
}
updateLove();

let player;
function onYouTubeIframeAPIReady(){player=new YT.Player('ytPlayer');}

function toggleMusic(){
if(!player) return;
const s=player.getPlayerState();
if(s===1){player.pauseVideo();playIcon.className="fas fa-play";}
else{player.playVideo();playIcon.className="fas fa-pause";}
}
</script>

</body>
</html>
​