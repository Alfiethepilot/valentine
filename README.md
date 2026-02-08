# <!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Terriann 💘 Will you be my Valentine?</title>
  <style>
    :root{
      --bg1:#0b1020;
      --bg2:#1b0b2a;
      --card:#10162a;
      --text:#eef2ff;
      --muted:#b8c0ff;
      --yes1:#ff4d7d;
      --yes2:#ff7aa2;
      --shadow: 0 20px 50px rgba(0,0,0,.45);
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji","Segoe UI Emoji";
      color:var(--text);
      background: radial-gradient(1200px 800px at 20% 20%, #25104a 0%, transparent 55%),
                  radial-gradient(900px 600px at 80% 30%, #3b1233 0%, transparent 60%),
                  linear-gradient(160deg, var(--bg1), var(--bg2));
      overflow:hidden;
    }

    /* Floating hearts */
    .hearts{
      position:fixed; inset:0;
      pointer-events:none;
      opacity:.7;
      filter: drop-shadow(0 6px 10px rgba(0,0,0,.25));
    }
    .heart{
      position:absolute;
      font-size: clamp(14px, 2.8vw, 26px);
      animation: floatUp linear infinite;
      transform: translateY(110vh);
      opacity:.9;
    }
    @keyframes floatUp{
      from{ transform: translateY(110vh) translateX(0) rotate(0deg); opacity:0}
      10%{opacity:.9}
      to{ transform: translateY(-20vh) translateX(var(--drift)) rotate(20deg); opacity:0}
    }

    .wrap{
      height:100%;
      display:grid;
      place-items:center;
      padding:24px;
    }

    .card{
      width:min(720px, 100%);
      background: linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.03));
      border:1px solid rgba(255,255,255,.14);
      border-radius: 26px;
      box-shadow: var(--shadow);
      backdrop-filter: blur(10px);
      padding: clamp(18px, 3vw, 34px);
      position:relative;
      overflow:hidden;
    }
    .card:before{
      content:"";
      position:absolute; inset:-2px;
      background: radial-gradient(500px 220px at 20% 10%, rgba(255,77,125,.35), transparent 60%),
                  radial-gradient(480px 240px at 80% 0%, rgba(255,180,200,.22), transparent 60%);
      opacity:.9;
      pointer-events:none;
    }
    .content{position:relative}

    .badge{
      display:inline-flex;
      align-items:center;
      gap:10px;
      padding:10px 14px;
      border-radius:999px;
      border:1px solid rgba(255,255,255,.16);
      background: rgba(0,0,0,.18);
      color: var(--muted);
      font-weight:600;
      letter-spacing:.2px;
      user-select:none;
    }
    .badge .dot{
      width:10px; height:10px; border-radius:50%;
      background: linear-gradient(180deg, #ff4d7d, #ffd1dc);
      box-shadow: 0 0 0 6px rgba(255,77,125,.12);
    }

    h1{
      margin:16px 0 8px;
      font-size: clamp(28px, 5.2vw, 48px);
      line-height:1.05;
      letter-spacing:-.02em;
    }
    .sub{
      margin:0 0 22px;
      color: rgba(238,242,255,.82);
      font-size: clamp(14px, 2.2vw, 18px);
      line-height:1.55;
      max-width: 55ch;
    }

    .name{
      background: linear-gradient(90deg, #ffd1dc, #ff4d7d, #ffb3c6);
      -webkit-background-clip:text;
      background-clip:text;
      color:transparent;
      font-weight:800;
    }

    .actions{
      display:flex;
      gap:14px;
      flex-wrap:wrap;
      align-items:center;
      margin-top: 10px;
    }

    .btn{
      appearance:none;
      border:0;
      border-radius: 16px;
      padding: 14px 18px;
      font-weight:800;
      font-size:16px;
      cursor:pointer;
      transition: transform .15s ease, box-shadow .15s ease, filter .15s ease;
      user-select:none;
      display:inline-flex;
      align-items:center;
      gap:10px;
      text-decoration:none;
    }
    .btn:active{ transform: translateY(1px) scale(.99); }

    .btn-yes{
      color:#230713;
      background: linear-gradient(180deg, var(--yes2), var(--yes1));
      box-shadow: 0 14px 34px rgba(255,77,125,.28);
    }
    .btn-yes:hover{ filter: brightness(1.05); transform: translateY(-1px); }

    .btn-no{
      color: rgba(238,242,255,.55);
      background: rgba(255,255,255,.06);
      border: 1px solid rgba(255,255,255,.14);
      cursor: not-allowed;
      pointer-events: none; /* ✅ makes NO not clickable */
      opacity: .55;
    }

    .note{
      margin-top:14px;
      color: rgba(238,242,255,.65);
      font-size: 13px;
    }

    .footer{
      margin-top: 26px;
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      align-items:center;
      color: rgba(238,242,255,.55);
      font-size: 12px;
    }
    .pill{
      padding: 8px 10px;
      border-radius:999px;
      border: 1px solid rgba(255,255,255,.12);
      background: rgba(0,0,0,.16);
    }

    /* Modal */
    .overlay{
      position:fixed; inset:0;
      background: rgba(0,0,0,.55);
      display:none;
      align-items:center;
      justify-content:center;
      padding: 20px;
    }
    .overlay.show{ display:flex; }

    .modal{
      width:min(560px, 100%);
      background: linear-gradient(180deg, rgba(255,255,255,.10), rgba(255,255,255,.06));
      border:1px solid rgba(255,255,255,.18);
      border-radius: 24px;
      box-shadow: var(--shadow);
      backdrop-filter: blur(12px);
      padding: 22px;
      position:relative;
      overflow:hidden;
    }
    .modal:before{
      content:"";
      position:absolute; inset:-2px;
      background: radial-gradient(500px 220px at 20% 10%, rgba(255,77,125,.28), transparent 60%),
                  radial-gradient(520px 240px at 80% 20%, rgba(255,209,220,.18), transparent 60%);
      pointer-events:none;
    }
    .modal .inner{ position:relative; }
    .modal h2{
      margin: 0 0 10px;
      font-size: 26px;
      letter-spacing:-.01em;
    }
    .modal p{
      margin:0 0 16px;
      color: rgba(238,242,255,.85);
      line-height:1.55;
    }
    .modal .row{
      display:flex; gap:12px; flex-wrap:wrap;
    }
    .btn-secondary{
      color: rgba(238,242,255,.9);
      background: rgba(255,255,255,.08);
      border: 1px solid rgba(255,255,255,.16);
    }
    .btn-secondary:hover{ transform: translateY(-1px); }
    .tiny{
      font-size: 12px;
      color: rgba(238,242,255,.6);
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <div class="hearts" aria-hidden="true" id="hearts"></div>

  <main class="wrap">
    <section class="card" role="region" aria-label="Valentine card">
      <div class="content">
        <div class="badge">
          <span class="dot"></span>
          <span>Valentine’s Invite</span>
        </div>

        <h1>
          Terriann, <br />
          will you be my <span class="name">Valentine</span>? 💘
        </h1>

        <p class="sub">
          One click and it’s official: cute dates, good vibes, and me treating you right.
          (No pressure… but also yes pressure 😄)
        </p>

        <div class="actions">
          <button class="btn btn-yes" id="yesBtn" type="button" aria-label="Yes">
            ✅ Yes
          </button>

          <button class="btn btn-no" type="button" aria-label="No (disabled)">
            ❌ No
          </button>
        </div>

        <div class="note">
          *P.S. The “No” button is disabled on purpose 😌
        </div>

        <div class="footer">
          <span class="pill">Made with 💗</span>
          <span class="pill">Clickable “Yes”</span>
          <span class="pill">“No” is locked</span>
        </div>
      </div>
    </section>
  </main>

  <!-- Modal -->
  <div class="overlay" id="overlay" role="dialog" aria-modal="true" aria-label="Yes modal">
    <div class="modal">
      <div class="inner">
        <h2>She said YES! 🥰</h2>
        <p>
          Terriann, you just made my day. <br/>
          Now we’re officially Valentine’s. 💘
        </p>
        <div class="row">
          <button class="btn btn-yes" id="confettiBtn" type="button">🎉 Celebrate</button>
          <button class="btn btn-secondary" id="closeBtn" type="button">Close</button>
        </div>
        <div class="tiny">Tip: You can change the message text inside the HTML anytime.</div>
      </div>
    </div>
  </div>

  <script>
    // Make floating hearts
    const hearts = document.getElementById("hearts");
    const heartEmojis = ["💗","💖","💘","💕","💞","❤️"];
    const count = 22;

    function rand(min, max){ return Math.random() * (max - min) + min; }

    for(let i=0;i<count;i++){
      const s = document.createElement("div");
      s.className = "heart";
      s.textContent = heartEmojis[Math.floor(Math.random()*heartEmojis.length)];
      s.style.left = rand(0, 100) + "vw";
      s.style.animationDuration = rand(6, 12) + "s";
      s.style.animationDelay = rand(0, 8) + "s";
      s.style.setProperty("--drift", rand(-40, 40) + "px");
      s.style.opacity = rand(0.35, 0.95);
      hearts.appendChild(s);
    }

    // Interactions
    const yesBtn = document.getElementById("yesBtn");
    const overlay = document.getElementById("overlay");
    const closeBtn = document.getElementById("closeBtn");
    const confettiBtn = document.getElementById("confettiBtn");

    yesBtn.addEventListener("click", () => {
      overlay.classList.add("show");
    });

    closeBtn.addEventListener("click", () => {
      overlay.classList.remove("show");
    });

    overlay.addEventListener("click", (e) => {
      if(e.target === overlay) overlay.classList.remove("show");
    });

    // Simple “confetti” effect using emojis
    confettiBtn.addEventListener("click", () => {
      for(let i=0;i<28;i++){
        const p = document.createElement("div");
        p.style.position = "fixed";
        p.style.left = rand(10, 90) + "vw";
        p.style.top = "-10vh";
        p.style.fontSize = rand(16, 34) + "px";
        p.style.zIndex = 9999;
        p.style.pointerEvents = "none";
        p.textContent = heartEmojis[Math.floor(Math.random()*heartEmojis.length)];

        const dur = rand(1.8, 3.3);
        const drift = rand(-120, 120);
        p.animate([
          { transform: `translate(0, 0) rotate(0deg)`, opacity: 0 },
          { opacity: 1, offset: 0.15 },
          { transform: `translate(${drift}px, 115vh) rotate(220deg)`, opacity: 0 }
        ], {
          duration: dur * 1000,
          easing: "cubic-bezier(.2,.7,.2,1)"
        });

        document.body.appendChild(p);
        setTimeout(() => p.remove(), dur * 1000);
      }
    });
  </script>
</body>
</html>