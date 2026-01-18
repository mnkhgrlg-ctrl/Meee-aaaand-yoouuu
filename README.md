# only suwdaa
<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<title>For You</title>

<style>
body{
  margin:0;
  height:100vh;
  overflow:hidden;
  background:radial-gradient(circle at center,#ff6b9a,#4b0012);
  font-family:-apple-system;
}

/* ===== BACKGROUND FLOATING WORDS ===== */
.bg-word{
  position:fixed;
  color:rgba(255,255,255,.15);
  font-size:22px;
  animation:floatBg linear forwards;
  pointer-events:none;
  white-space:nowrap;
}
@keyframes floatBg{
  from{transform:translateY(110vh)}
  to{transform:translateY(-120px)}
}

/* ===== BACKGROUND HEARTS ===== */
.bg-heart{
  position:fixed;
  font-size:18px;
  opacity:.25;
  animation:rise linear forwards;
  pointer-events:none;
}
@keyframes rise{
  from{transform:translateY(110vh)}
  to{transform:translateY(-120px)}
}

/* ===== CENTER AREA ===== */
.center{
  position:absolute;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
}

/* ===== GIFT BOX ===== */
#gift{
  width:180px;
  height:130px;
  background:#c8002d;
  border-radius:14px;
  position:relative;
  cursor:pointer;
  box-shadow:0 25px 45px rgba(0,0,0,.45);
  animation:float 2.5s infinite ease-in-out;
  z-index:5;
}
#gift:before{
  content:"";
  position:absolute;
  width:36px;
  height:130px;
  background:#ffd1dc;
  left:72px;
}
#gift:after{
  content:"";
  position:absolute;
  width:180px;
  height:36px;
  background:#ffd1dc;
  top:47px;
}
#lid{
  width:200px;
  height:46px;
  background:#ff0033;
  position:absolute;
  top:-46px;
  left:-10px;
  border-radius:12px;
  transition:1s ease;
}

@keyframes float{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-14px)}
}

/* ===== MAIN MESSAGE ===== */
#msg{
  display:none;
  position:absolute;
  color:white;
  font-size:44px;
  font-weight:800;
  text-align:center;
  line-height:1.25;
  text-shadow:0 0 30px rgba(255,255,255,.9);
  animation:pop 1s ease forwards;
  z-index:10;
}
@keyframes pop{
  from{opacity:0;transform:scale(.6)}
  to{opacity:1;transform:scale(1)}
}

/* ===== EXPLOSION WORDS ===== */
.word{
  position:fixed;
  font-size:28px;
  font-weight:600;
  color:white;
  text-shadow:0 0 18px rgba(255,255,255,.9);
  animation:fly 3.2s ease forwards;
  pointer-events:none;
}
@keyframes fly{
  to{transform:translateY(-160px);opacity:0}
}

/* ===== EXPLOSION HEARTS ===== */
.heart{
  position:fixed;
  font-size:28px;
  animation:burst 2.8s ease forwards;
  pointer-events:none;
}
@keyframes burst{
  to{
    transform:translate(
      calc(-160px + 320px * var(--x)),
      calc(-160px + 320px * var(--y))
    );
    opacity:0;
  }
}
</style>
</head>

<body>

<div class="center">
  <div id="gift">
    <div id="lid"></div>
  </div>

  <div id="msg">
    Suwdaa<br>
    би чамд хайртай ❤️
  </div>
</div>

<script>
/* ===== TEXT SOURCES ===== */
const bgWords=[
  "Love","Forever","Suwdaa","Хайр","Үүрд","Only you",
  "My heart","Dream","Together","❤️"
];

const boomWords=[
  "Хайр","Чи минийх","Үүрд","Аз жаргал",
  "Forever","Only you","Love","❤️"
];

/* ===== BACKGROUND LOOP ===== */
setInterval(()=>{
  createBgWord();
  createBgHeart();
},600);

function createBgWord(){
  const w=document.createElement("div");
  w.className="bg-word";
  w.innerHTML=bgWords[Math.floor(Math.random()*bgWords.length)];
  w.style.left=Math.random()*100+"vw";
  w.style.animationDuration=10+Math.random()*10+"s";
  document.body.appendChild(w);
  setTimeout(()=>w.remove(),20000);
}

function createBgHeart(){
  const h=document.createElement("div");
  h.className="bg-heart";
  h.innerHTML="❤️";
  h.style.left=Math.random()*100+"vw";
  h.style.animationDuration=8+Math.random()*8+"s";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),18000);
}

/* ===== CLICK EVENT ===== */
gift.onclick=()=>{
  lid.style.transform="rotateX(150deg) translateY(-70px)";
  gift.style.display="none";
  msg.style.display="block";

  for(let i=0;i<30;i++){
    setTimeout(makeHeart,i*50);
    setTimeout(makeWord,i*90);
  }
};

function makeHeart(){
  const h=document.createElement("div");
  h.className="heart";
  h.innerHTML="❤️";
  h.style.left=window.innerWidth/2+"px";
  h.style.top=window.innerHeight/2+"px";
  h.style.setProperty("--x",Math.random());
  h.style.setProperty("--y",Math.random());
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),3000);
}

function makeWord(){
  const w=document.createElement("div");
  w.className="word";
  w.innerHTML=boomWords[Math.floor(Math.random()*boomWords.length)];
  w.style.left=window.innerWidth/2+(Math.random()*220-110)+"px";
  w.style.top=window.innerHeight/2+(Math.random()*140-70)+"px";
  document.body.appendChild(w);
  setTimeout(()=>w.remove(),3200);
}
</script>

</body>
</html>
