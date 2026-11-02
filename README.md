
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Happy 47th Birthday, Dad!</title>
<style>
:root{--bg:#fff7ec;--card:#ffffff;--text:#2b2118;--muted:#6f5d4c;--accent:#e8590c;--accent2:#f59f00;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#1c1511;--card:#2a1f18;--text:#fbefe0;--muted:#c9b39d;--accent:#ff8a3d;--accent2:#ffc53d}}
:root[data-theme="dark"]{--bg:#1c1511;--card:#2a1f18;--text:#fbefe0;--muted:#c9b39d;--accent:#ff8a3d;--accent2:#ffc53d}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font-family:Georgia,"Times New Roman",serif;text-align:center;line-height:1.6;overflow-x:hidden}
canvas{position:fixed;inset:0;pointer-events:none;z-index:5}
.hero{padding:56px 20px 36px}
.age{font-size:clamp(110px,32vw,220px);font-weight:700;line-height:1;margin:0;background:linear-gradient(135deg,var(--accent),var(--accent2));-webkit-background-clip:text;background-clip:text;color:transparent;font-family:Georgia,serif}
h1{font-size:clamp(28px,7vw,48px);margin:8px 0}
.sub{color:var(--muted);font-size:18px;margin:0 auto;max-width:34ch}
.cd{margin:18px auto 0;display:inline-block;padding:8px 18px;border-radius:999px;background:var(--card);color:var(--muted);font-family:system-ui,sans-serif;font-size:15px}
button{font:600 17px system-ui,sans-serif;background:var(--accent);color:#fff;border:0;border-radius:999px;padding:14px 28px;margin-top:24px;cursor:pointer}
button:active{transform:scale(.97)}
section{max-width:640px;margin:0 auto;padding:12px 20px 28px}
.card{background:var(--card);border-radius:20px;padding:24px;margin:16px 0;box-shadow:0 4px 18px rgba(0,0,0,.08)}
.card h2{margin:0 0 8px;color:var(--accent);font-size:22px}
.card p{margin:0}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:12px}
.grid .card{margin:0;padding:18px}
.big{font-size:34px}
footer{padding:24px 20px 40px;color:var(--muted);font-size:15px}
</style>
</head>
<body>
<canvas id="c"></canvas>
<div class="hero">
  <div style="font-size:44px">🎉🎂🎈</div>
  <p class="age">47</p>
  <h1>Happy Birthday, Dad!</h1>
  <p class="sub">Forty-seven years of being awesome</p>
  <button id="party">Tap for a party 🎊</button>
</div>
<section>
  <div class="card">
    <h2>A message just for you</h2>
    <p>Dad, thank you for everything you do for us. You work hard, you care deeply, and you always make our home feel safe and warm. I hope your 47th birthday is filled with laughter, good food, and all the love you give to others every day.</p>
  </div>
  <div class="grid">
    <div class="card"><div class="big">💪</div><h2>Strong</h2><p>You&rsquo;re always there when we need you.</p></div>
    <div class="card"><div class="big">❤️</div><h2>Caring</h2><p>Your love shows in everything you do.</p></div>
    <div class="card"><div class="big">🌟</div><h2>My hero</h2><p>I look up to you more than you know.</p></div>
  </div>
  <div class="card">
    <h2>47 wishes for you</h2>
    <p id="wish">Tap the button below to read a wish.</p>
    <button id="nw" style="margin-top:16px">Next wish ✨</button>
  </div>
</section>
<footer>Made with love for the best dad in the world. Happy 47th! 🎁</footer>
<script>
var wishes=["May this year bring you good health and lots of energy.","May every day have more smiles than worries.","May your hard work be rewarded in the best ways.","May you always have time to rest and enjoy life.","May your favorite meals taste even better this year.","May your family be a never-ending source of joy.","May all your dreams slowly come true.","May you laugh until your stomach hurts.","May your 47th year be your best yet.","Forty-seven is just the beginning of the good stuff!","Thank you for always believing in me.","You are the strongest person I know.","I love you, Dad, today and always."];
var wi=0;
function nextWish(){document.getElementById("wish").textContent="\u201C"+wishes[wi%wishes.length]+"\u201D";wi++}
document.getElementById("nw").onclick=nextWish;

var cv=document.getElementById("c"),cx=cv.getContext("2d"),ps=[],run=false;
function size(){cv.width=innerWidth;cv.height=innerHeight}
size();addEventListener("resize",size);
var cols=["#e8590c","#f59f00","#fa5252","#40c057","#339af0","#be4bdb"];
function burst(){
  for(var i=0;i<140;i++)ps.push({x:Math.random()*cv.width,y:-10-Math.random()*cv.height*.4,vx:(Math.random()-.5)*3,vy:2+Math.random()*4,s:5+Math.random()*7,r:Math.random()*6,vr:(Math.random()-.5)*.3,c:cols[i%cols.length]});
  if(!run){run=true;loop()}
}
function loop(){
  cx.clearRect(0,0,cv.width,cv.height);
  ps=ps.filter(function(p){return p.y<cv.height+20});
  ps.forEach(function(p){p.x+=p.vx;p.y+=p.vy;p.r+=p.vr;cx.save();cx.translate(p.x,p.y);cx.rotate(p.r);cx.fillStyle=p.c;cx.fillRect(-p.s/2,-p.s/4,p.s,p.s/2);cx.restore()});
  if(ps.length)requestAnimationFrame(loop);else{run=false;cx.clearRect(0,0,cv.width,cv.height)}
}
document.getElementById("party").onclick=burst;
setTimeout(burst,500);
</script>
</body>
</html>
