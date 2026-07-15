<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Eldavily — Maison de Couture</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,600;1,9..144,400&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --ivory:#F6F3EC;
    --ink:#171510;
    --taupe:#A79680;
    --wine:#5E2331;
    --gold:#AD8A54;
    --line: rgba(23,21,16,0.14);
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--ivory);
    color:var(--ink);
    font-family:'Inter', sans-serif;
    font-weight:400;
    overflow-x:hidden;
  }
  a{color:inherit; text-decoration:none;}
  .serif{font-family:'Fraunces', serif;}
  .eyebrow{
    font-size:11px;
    letter-spacing:0.22em;
    text-transform:uppercase;
    color:var(--wine);
    font-weight:500;
  }

  /* ---------- NAV ---------- */
  nav{
    position:fixed; top:0; left:0; right:0; z-index:100;
    display:flex; align-items:center; justify-content:space-between;
    padding:26px 48px;
    mix-blend-mode:difference;
    color:var(--ivory);
    transition:padding 0.4s ease;
  }
  nav.scrolled{ padding:16px 48px; }
  .wordmark{
    font-family:'Fraunces', serif;
    font-size:20px;
    letter-spacing:0.14em;
    font-weight:400;
  }
  .nav-links{display:flex; gap:36px; font-size:12px; letter-spacing:0.1em; text-transform:uppercase;}
  .nav-links a{position:relative; padding-bottom:4px;}
  .nav-links a::after{
    content:''; position:absolute; left:0; bottom:0; width:0; height:1px;
    background:var(--ivory); transition:width 0.35s ease;
  }
  .nav-links a:hover::after{width:100%;}
  .nav-icon{display:none; font-size:22px; cursor:pointer;}

  /* ---------- HERO ---------- */
  .hero{
    position:relative;
    height:100vh; min-height:640px;
    display:flex; align-items:flex-end;
    padding:0 48px 72px;
    background:linear-gradient(180deg, #EFEADD 0%, var(--ivory) 55%, var(--ivory) 100%);
    overflow:hidden;
  }
  .hero-figure{
    position:absolute; top:0; right:6%; height:100%; width:auto;
    opacity:0.9; pointer-events:none;
  }
  .hero-inner{ position:relative; z-index:2; max-width:760px; }
  .hero h1{
    font-size:clamp(48px, 8vw, 108px);
    line-height:0.95;
    font-weight:400;
    letter-spacing:-0.01em;
  }
  .hero h1 em{font-style:italic; color:var(--wine);}
  .hero p{
    margin-top:22px; max-width:420px;
    font-size:15px; line-height:1.7; color:#4A473F;
  }
  .hero-cta{
    display:inline-flex; align-items:center; gap:10px;
    margin-top:34px; font-size:12px; letter-spacing:0.12em; text-transform:uppercase;
    border-bottom:1px solid var(--ink); padding-bottom:6px;
  }
  .hero-cta:hover{ border-color:var(--wine); color:var(--wine); }
  .scroll-cue{
    position:absolute; right:48px; bottom:40px; z-index:2;
    writing-mode:vertical-rl; font-size:11px; letter-spacing:0.2em;
    text-transform:uppercase; display:flex; align-items:center; gap:10px; color:#6B675C;
  }
  .scroll-cue::after{content:''; width:1px; height:60px; background:#6B675C; display:block;}

  /* ---------- MARQUEE ---------- */
  .marquee-band{
    border-top:1px solid var(--line); border-bottom:1px solid var(--line);
    padding:18px 0; overflow:hidden; white-space:nowrap; background:var(--ink);
  }
  .marquee-track{ display:inline-block; animation: scroll-left 32s linear infinite; }
  .marquee-track span{
    font-family:'Fraunces', serif; font-style:italic; font-size:20px;
    color:var(--ivory); margin:0 32px; opacity:0.85;
  }
  @keyframes scroll-left{ from{transform:translateX(0);} to{transform:translateX(-50%);} }

  /* ---------- COLLECTION ---------- */
  .section{ padding:120px 48px; max-width:1400px; margin:0 auto; }
  .section-head{
    display:flex; justify-content:space-between; align-items:flex-end;
    margin-bottom:56px; gap:24px; flex-wrap:wrap;
    border-bottom:1px solid var(--line); padding-bottom:28px;
  }
  .section-head h2{ font-size:clamp(30px,4vw,52px); font-weight:400; }
  .section-head p{ font-size:13px; color:#6B675C; max-width:260px; }

  .grid{
    display:grid; grid-template-columns:repeat(3, 1fr); gap:2px;
  }
  .piece{
    position:relative; aspect-ratio:3/4; overflow:hidden;
    background:#E7E1D2; cursor:pointer;
  }
  .piece:nth-child(2){ margin-top:64px; }
  .piece:nth-child(5){ margin-top:-64px; }
  .piece-art{ position:absolute; inset:0; }
  .piece-caption{
    position:absolute; left:0; right:0; bottom:0; padding:20px;
    background:linear-gradient(0deg, rgba(23,21,16,0.55), transparent);
    color:var(--ivory); transform:translateY(8px); opacity:0;
    transition:all 0.35s ease;
  }
  .piece:hover .piece-caption{ transform:translateY(0); opacity:1; }
  .piece:hover .piece-art{ transform:scale(1.04); }
  .piece-art{ transition:transform 0.6s ease; }
  .piece-caption .num{ font-size:11px; letter-spacing:0.14em; color:var(--gold); }
  .piece-caption .name{ font-family:'Fraunces', serif; font-size:19px; font-style:italic; margin-top:4px; }

  /* ---------- ATELIER NOTE (editorial) ---------- */
  .atelier{
    display:grid; grid-template-columns:0.9fr 1.1fr; gap:80px; align-items:center;
  }
  .atelier-visual{
    aspect-ratio:4/5; background:#EFEADD; position:relative; overflow:hidden;
  }
  .atelier-text .eyebrow{ margin-bottom:18px; display:block; }
  .atelier-text h2{ font-size:clamp(28px,3.4vw,44px); font-weight:400; line-height:1.15; margin-bottom:24px; }
  .atelier-text p{ font-size:15px; line-height:1.85; color:#4A473F; max-width:460px; margin-bottom:16px; }
  .stitch{
    position:absolute; left:0; top:50%; height:1px; width:0%; background:var(--wine);
    transition:width 1.4s cubic-bezier(.2,.8,.2,1);
  }
  .atelier-visual.in-view .stitch{ width:100%; }

  /* ---------- NEWSLETTER / FOOTER ---------- */
  footer{
    background:var(--ink); color:var(--ivory); padding:100px 48px 40px;
  }
  .foot-top{
    display:flex; justify-content:space-between; align-items:flex-end; gap:40px; flex-wrap:wrap;
    border-bottom:1px solid rgba(246,243,236,0.16); padding-bottom:56px; margin-bottom:40px;
  }
  .foot-top h3{ font-family:'Fraunces', serif; font-size:clamp(28px,4vw,46px); font-weight:400; max-width:520px; }
  .signup{ display:flex; border-bottom:1px solid var(--ivory); min-width:300px; }
  .signup input{
    background:transparent; border:none; outline:none; color:var(--ivory);
    font-family:'Inter'; font-size:14px; padding:10px 0; flex:1;
  }
  .signup input::placeholder{ color:rgba(246,243,236,0.5); }
  .signup button{
    background:none; border:none; color:var(--gold); font-size:12px;
    letter-spacing:0.12em; text-transform:uppercase; cursor:pointer;
  }
  .foot-cols{ display:flex; gap:64px; flex-wrap:wrap; font-size:13px; color:rgba(246,243,236,0.6); }
  .foot-col h4{ font-size:11px; letter-spacing:0.14em; text-transform:uppercase; color:var(--ivory); margin-bottom:14px; }
  .foot-col a{ display:block; margin-bottom:9px; }
  .foot-col a:hover{ color:var(--ivory); }
  .foot-bottom{ margin-top:56px; font-size:11px; color:rgba(246,243,236,0.4); display:flex; justify-content:space-between; flex-wrap:wrap; gap:12px;}

  @media (max-width: 900px){
    nav{padding:20px 24px;}
    .nav-links{display:none;}
    .nav-icon{display:block;}
    .section{padding:80px 24px;}
    .grid{grid-template-columns:1fr;}
    .piece:nth-child(2), .piece:nth-child(5){margin-top:0;}
    .atelier{grid-template-columns:1fr;}
    .hero{padding:0 24px 56px;}
    .scroll-cue{display:none;}
  }
</style>
</head>
<body>

<nav id="nav">
  <div class="wordmark">ELDAVILY</div>
  <div class="nav-links">
    <a href="#collection">Collection</a>
    <a href="#atelier">Maison</a>
    <a href="#lookbook">Lookbook</a>
    <a href="#footer">Contact</a>
  </div>
  <div class="nav-icon">☰</div>
</nav>

<section class="hero">
  <svg class="hero-figure" viewBox="0 0 300 700" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M150 40 C 120 60, 110 100, 120 140 C 90 160, 70 220, 80 300 C 60 340, 55 420, 70 500 L 100 690 M 150 40 C 180 60, 190 100, 180 140 C 210 160, 230 220, 220 300 C 240 340, 245 420, 230 500 L 200 690" stroke="#171510" stroke-opacity="0.10" stroke-width="1.4"/>
    <path d="M120 140 C 110 220, 115 400, 130 560" stroke="#5E2331" stroke-opacity="0.18" stroke-width="1"/>
    <path d="M180 140 C 190 220, 185 400, 170 560" stroke="#5E2331" stroke-opacity="0.18" stroke-width="1"/>
    <ellipse cx="150" cy="20" rx="18" ry="20" stroke="#171510" stroke-opacity="0.12" stroke-width="1.4"/>
  </svg>
  <div class="hero-inner">
    <p class="eyebrow">Fall / Winter Collection — No. 12</p>
    <h1 class="serif">Cut from<br><em>quiet</em> conviction.</h1>
    <p>Eldavily builds garments the way a letter is written by hand — slowly, deliberately, and meant to be kept. Every piece is finished in our Lyon workshop.</p>
    <a href="#collection" class="hero-cta">View the collection →</a>
  </div>
  <div class="scroll-cue">Scroll</div>
</section>

<div class="marquee-band">
  <div class="marquee-track">
    <span>Hand-finished seams</span><span>Lyon workshop</span><span>Season No. 12</span><span>Wool, silk, raw linen</span><span>Numbered editions</span>
    <span>Hand-finished seams</span><span>Lyon workshop</span><span>Season No. 12</span><span>Wool, silk, raw linen</span><span>Numbered editions</span>
  </div>
</div>

<section class="section" id="collection">
  <div class="section-head">
    <h2 class="serif">The collection</h2>
    <p>Six silhouettes, each numbered and produced in a limited run of 200.</p>
  </div>
  <div class="grid">
    <div class="piece">
      <div class="piece-art" style="background:linear-gradient(160deg,#DCD3BE,#C6B89C);"></div>
      <div class="piece-caption"><div class="num">01 — Outerwear</div><div class="name serif">The Marchand coat</div></div>
    </div>
    <div class="piece">
      <div class="piece-art" style="background:linear-gradient(160deg,#E2DED0,#B9A88C);"></div>
      <div class="piece-caption"><div class="num">02 — Tailoring</div><div class="name serif">Rue Vide trouser</div></div>
    </div>
    <div class="piece">
      <div class="piece-art" style="background:linear-gradient(160deg,#D8CFC0,#8E7A63);"></div>
      <div class="piece-caption"><div class="num">03 — Evening</div><div class="name serif">Soir noir gown</div></div>
    </div>
    <div class="piece">
      <div class="piece-art" style="background:linear-gradient(160deg,#E7E1D2,#C9BBA0);"></div>
      <div class="piece-caption"><div class="num">04 — Knitwear</div><div class="name serif">Hiver cardigan</div></div>
    </div>
    <div class="piece">
      <div class="piece-art" style="background:linear-gradient(160deg,#DED5C4,#A3907A);"></div>
      <div class="piece-caption"><div class="num">05 — Accessory</div><div class="name serif">Cinq à sept bag</div></div>
    </div>
    <div class="piece">
      <div class="piece-art" style="background:linear-gradient(160deg,#E4DDCE,#B6A489);"></div>
      <div class="piece-caption"><div class="num">06 — Tailoring</div><div class="name serif">Auguste blazer</div></div>
    </div>
  </div>
</section>

<section class="section" id="atelier">
  <div class="atelier">
    <div class="atelier-visual" id="atelierVisual">
      <div style="position:absolute; inset:0; background:linear-gradient(200deg,#EFEADD,#D9CDB5);"></div>
      <div class="stitch"></div>
    </div>
    <div class="atelier-text">
      <span class="eyebrow">The Maison</span>
      <h2 class="serif">Every seam has a name behind it.</h2>
      <p>Founded in 2011 above a fabric market in Lyon, Eldavily still cuts every pattern by hand before it ever reaches a machine. Our seamstresses average fourteen years at the bench.</p>
      <p>We work in small batches on purpose — no piece is made until it's ordered, and no fabric is chosen until it's felt.</p>
      <a href="#lookbook" class="hero-cta">Read our story →</a>
    </div>
  </div>
</section>

<footer id="footer">
  <div class="foot-top">
    <h3>Join the atelier list for early access to each new season.</h3>
    <div class="signup">
      <input type="email" placeholder="Your email address">
      <button type="button">Subscribe →</button>
    </div>
  </div>
  <div class="foot-cols">
    <div class="foot-col">
      <h4>Shop</h4>
      <a href="#">Collection</a>
      <a href="#">Accessories</a>
      <a href="#">Gift cards</a>
    </div>
    <div class="foot-col">
      <h4>Maison</h4>
      <a href="#">Our story</a>
      <a href="#">Ateliers</a>
      <a href="#">Sustainability</a>
    </div>
    <div class="foot-col">
      <h4>Client care</h4>
      <a href="#">Contact</a>
      <a href="#">Shipping</a>
      <a href="#">Returns</a>
    </div>
  </div>
  <div class="foot-bottom">
    <span>© 2026 Eldavily. All rights reserved.</span>
    <span>Lyon — Paris — Kyoto</span>
  </div>
</footer>

<script>
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 40);
  });

  const atelierVisual = document.getElementById('atelierVisual');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => { if(e.isIntersecting) e.target.classList.add('in-view'); });
  }, { threshold: 0.4 });
  io.observe(atelierVisual);
</script>

</body>
</html>
