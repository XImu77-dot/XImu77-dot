<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Portofolio RGB | NAMA KAMU</title>
<meta name="description" content="Portofolio developer bertema RGB">
<style>
/* =====================================================
   TEMPLAT PORTOFOLIO RGB
   Ubah warna di :root. Ubah teks langsung di HTML.
   ===================================================== */
@property --a { syntax: "<angle>"; initial-value: 0deg; inherits: false; }

:root {
  --bg: #07070d;
  --panel: #0e0e18;
  --text: #e8e8f2;
  --muted: #8a8aa3;
  --r: #ff0055;   /* Merah */
  --g: #00ff88;   /* Hijau */
  --b: #0088ff;   /* Biru */
  --rgb: conic-gradient(from var(--a), var(--r), var(--g), var(--b), var(--r));
  --rgb-line: linear-gradient(90deg, var(--r), var(--g), var(--b), var(--r));
}

* { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  background: var(--bg);
  color: var(--text);
  font-family: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
  line-height: 1.6;
  overflow-x: hidden;
}
section { max-width: 1050px; margin: 0 auto; padding: 90px 22px; }
h2 { font-size: clamp(1.8rem, 4vw, 2.4rem); margin-bottom: 36px; }
.rgb-text {
  background: var(--rgb-line);
  background-size: 300% 100%;
  -webkit-background-clip: text; background-clip: text;
  color: transparent;
  animation: slide 6s linear infinite;
}
@keyframes slide { to { background-position: 300% 0; } }
@keyframes spin { to { --a: 360deg; } }

/* ---------- Glow mengikuti kursor ---------- */
#glow {
  position: fixed; width: 420px; height: 420px; border-radius: 50%;
  pointer-events: none; z-index: 0; opacity: .18; filter: blur(70px);
  background: var(--rgb); animation: spin 6s linear infinite;
  transform: translate(-50%, -50%); left: 50%; top: 30%;
}

/* ---------- Navbar ---------- */
nav {
  position: sticky; top: 0; z-index: 10;
  display: flex; justify-content: space-between; align-items: center;
  padding: 14px 24px; background: rgba(7,7,13,.8); backdrop-filter: blur(12px);
  border-bottom: 1px solid #1c1c2b;
}
nav::after { content: ""; position: absolute; left: 0; right: 0; bottom: -1px; height: 2px;
  background: var(--rgb-line); background-size: 300% 100%; animation: slide 6s linear infinite; }
.logo { font-weight: 800; font-size: 1.2rem; text-decoration: none; }
nav ul { display: flex; gap: 22px; list-style: none; }
nav a { color: var(--muted); text-decoration: none; font-size: .95rem; transition: color .2s; }
nav ul a:hover { color: var(--g); }

/* ---------- Hero ---------- */
.hero { min-height: 88vh; display: flex; flex-direction: column; justify-content: center; position: relative; z-index: 1; }
.hero small { color: var(--g); font-family: ui-monospace, Menlo, Consolas, monospace; }
.hero h1 { font-size: clamp(2.6rem, 8vw, 5rem); line-height: 1.1; margin: 10px 0; }
.typing { font-size: clamp(1.1rem, 3vw, 1.6rem); color: var(--muted); min-height: 2em; }
.typing::after { content: "|"; color: var(--b); animation: blink 1s steps(1) infinite; }
@keyframes blink { 50% { opacity: 0; } }
.hero p.desc { max-width: 560px; margin: 18px 0 30px; color: var(--muted); }
.btns { display: flex; gap: 14px; flex-wrap: wrap; }

/* Tombol dengan border RGB berputar */
.btn {
  position: relative; display: inline-block; padding: 13px 28px; border-radius: 10px;
  text-decoration: none; color: var(--text); font-weight: 600; background: var(--panel);
  isolation: isolate; transition: transform .2s;
}
.btn::before {
  content: ""; position: absolute; inset: -2px; border-radius: 12px; z-index: -2;
  background: var(--rgb); animation: spin 3s linear infinite;
}
.btn::after { content: ""; position: absolute; inset: 0; border-radius: 10px; background: var(--panel); z-index: -1; }
.btn:hover { transform: translateY(-3px); }
.btn.fill::after { background: transparent; }
.btn.fill { color: #000; }

/* ---------- Kartu dengan border RGB ---------- */
.grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(270px, 1fr)); gap: 24px; }
.card {
  position: relative; background: var(--panel); border-radius: 14px; padding: 26px;
  isolation: isolate; transition: transform .3s;
}
.card::before {
  content: ""; position: absolute; inset: -2px; border-radius: 16px; z-index: -2;
  background: var(--rgb); animation: spin 5s linear infinite; opacity: .35; transition: opacity .3s;
}
.card::after { content: ""; position: absolute; inset: 0; border-radius: 14px; background: var(--panel); z-index: -1; }
.card:hover { transform: translateY(-6px); }
.card:hover::before { opacity: 1; }
.card h3 { margin-bottom: 8px; }
.card p { color: var(--muted); font-size: .95rem; }
.tags { display: flex; gap: 8px; flex-wrap: wrap; margin-top: 16px; }
.tags span { font-size: .75rem; padding: 4px 10px; border-radius: 99px; border: 1px solid #2a2a40; color: var(--g); }
.card a.link { display: inline-block; margin-top: 16px; color: var(--b); text-decoration: none; font-weight: 600; }
.thumb { height: 140px; border-radius: 10px; margin-bottom: 18px; background: var(--rgb-line); background-size: 300% 100%; animation: slide 8s linear infinite; opacity: .85; }

/* ---------- Tentang & Skill ---------- */
.about { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: start; }
.about p { color: var(--muted); margin-bottom: 14px; }
.skill { margin-bottom: 18px; }
.skill div.row { display: flex; justify-content: space-between; font-size: .9rem; margin-bottom: 6px; }
.bar { height: 8px; background: #1a1a2a; border-radius: 99px; overflow: hidden; }
.bar i { display: block; height: 100%; width: 0; border-radius: 99px;
  background: var(--rgb-line); background-size: 300% 100%; animation: slide 5s linear infinite;
  transition: width 1.4s cubic-bezier(.2,.8,.2,1); box-shadow: 0 0 12px var(--g); }

/* ---------- Kontak & Footer ---------- */
.contact { text-align: center; }
.contact p { color: var(--muted); max-width: 480px; margin: 0 auto 28px; }
.socials { display: flex; justify-content: center; gap: 14px; margin-top: 30px; flex-wrap: wrap; }
.socials a { color: var(--muted); text-decoration: none; padding: 8px 16px; border: 1px solid #2a2a40; border-radius: 8px; transition: .2s; }
.socials a:hover { color: var(--g); border-color: var(--g); box-shadow: 0 0 14px rgba(0,255,136,.4); }
footer { text-align: center; padding: 26px; color: var(--muted); font-size: .85rem; border-top: 1px solid #1c1c2b; position: relative; z-index: 1; }

/* ---------- Animasi muncul saat scroll ---------- */
.reveal { opacity: 0; transform: translateY(30px); transition: opacity .7s, transform .7s; }
.reveal.show { opacity: 1; transform: none; }
main, nav, footer { position: relative; z-index: 1; }

@media (max-width: 760px) {
  .about { grid-template-columns: 1fr; }
  nav ul { gap: 14px; }
  nav a { font-size: .85rem; }
}
@media (prefers-reduced-motion: reduce) { * { animation: none !important; transition: none !important; } .reveal { opacity: 1; transform: none; } }
</style>
</head>
<body>
<div id="glow"></div>

<nav>
  <a href="#home" class="logo rgb-text">&lt;NAMA/&gt;</a>
  <ul>
    <li><a href="#about">Tentang</a></li>
    <li><a href="#projects">Proyek</a></li>
    <li><a href="#contact">Kontak</a></li>
  </ul>
</nav>

<main>
  <!-- ========== HERO ========== -->
  <section class="hero" id="home">
    <small>// Halo, saya</small>
    <h1 class="rgb-text">NAMA KAMU</h1>
    <div class="typing" id="typing"></div>
    <p class="desc">Saya membuat website dan aplikasi yang cepat, rapi, dan enak dilihat. Ganti paragraf ini dengan perkenalan singkat tentang kamu.</p>
    <div class="btns">
      <a href="#projects" class="btn">Lihat Proyek</a>
      <a href="#contact" class="btn">Hubungi Saya</a>
    </div>
  </section>

  <!-- ========== TENTANG ========== -->
  <section id="about">
    <h2 class="reveal">Tentang <span class="rgb-text">Saya</span></h2>
    <div class="about reveal">
      <div>
        <p>Ceritakan siapa kamu, apa yang kamu kerjakan, dan apa yang membuat kamu bersemangat soal teknologi.</p>
        <p>Tambahkan pengalaman, pendidikan, atau fun fact supaya portofolio terasa personal.</p>
      </div>
      <div id="skills">
        <div class="skill"><div class="row"><span>HTML &amp; CSS</span><span>90%</span></div><div class="bar"><i data-w="90"></i></div></div>
        <div class="skill"><div class="row"><span>JavaScript</span><span>85%</span></div><div class="bar"><i data-w="85"></i></div></div>
        <div class="skill"><div class="row"><span>React</span><span>75%</span></div><div class="bar"><i data-w="75"></i></div></div>
        <div class="skill"><div class="row"><span>Node.js</span><span>70%</span></div><div class="bar"><i data-w="70"></i></div></div>
      </div>
    </div>
  </section>

  <!-- ========== PROYEK ========== -->
  <section id="projects">
    <h2 class="reveal">Proyek <span class="rgb-text">Pilihan</span></h2>
    <div class="grid">
      <article class="card reveal">
        <div class="thumb"></div>
        <h3>Nama Proyek 1</h3>
        <p>Deskripsi singkat proyek: apa masalahnya dan bagaimana kamu menyelesaikannya.</p>
        <div class="tags"><span>React</span><span>Node.js</span><span>MongoDB</span></div>
        <a class="link" href="#">Lihat Proyek →</a>
      </article>
      <article class="card reveal">
        <div class="thumb"></div>
        <h3>Nama Proyek 2</h3>
        <p>Deskripsi singkat proyek. Sebutkan hasil atau dampak yang kamu capai.</p>
        <div class="tags"><span>Next.js</span><span>Tailwind</span></div>
        <a class="link" href="#">Lihat Proyek →</a>
      </article>
      <article class="card reveal">
        <div class="thumb"></div>
        <h3>Nama Proyek 3</h3>
        <p>Deskripsi singkat proyek. Tambahkan link GitHub atau demo langsung.</p>
        <div class="tags"><span>Python</span><span>Flask</span></div>
        <a class="link" href="#">Lihat Proyek →</a>
      </article>
    </div>
  </section>

  <!-- ========== KONTAK ========== -->
  <section id="contact" class="contact">
    <h2 class="reveal">Ayo <span class="rgb-text">Berkolaborasi</span></h2>
    <p class="reveal">Punya ide atau proyek? Kirim pesan, saya senang berdiskusi.</p>
    <a href="mailto:EMAIL@KAMU.COM" class="btn reveal">Kirim Email</a>
    <div class="socials reveal">
      <a href="https://github.com/USERNAME" target="_blank" rel="noopener">GitHub</a>
      <a href="https://linkedin.com/in/USERNAME" target="_blank" rel="noopener">LinkedIn</a>
      <a href="https://instagram.com/USERNAME" target="_blank" rel="noopener">Instagram</a>
    </div>
  </section>
</main>

<footer>© <span id="year"></span> NAMA KAMU. Dibuat dengan HTML, CSS &amp; sedikit warna RGB.</footer>

<script>
// ===== Teks ketik (ubah daftar kalimat di sini) =====
const lines = ["Web Developer", "UI Enthusiast", "Open Source Contributor"];
const el = document.getElementById("typing");
let li = 0, ci = 0, del = false;
(function type() {
  const t = lines[li];
  el.textContent = t.slice(0, ci);
  if (!del && ci < t.length) ci++;
  else if (!del) { del = true; return setTimeout(type, 1400); }
  else if (ci > 0) ci--;
  else { del = false; li = (li + 1) % lines.length; }
  setTimeout(type, del ? 40 : 90);
})();

// ===== Glow mengikuti kursor =====
const glow = document.getElementById("glow");
addEventListener("pointermove", e => { glow.style.left = e.clientX + "px"; glow.style.top = e.clientY + "px"; });

// ===== Animasi muncul + bar skill =====
const io = new IntersectionObserver(entries => {
  entries.forEach(en => {
    if (!en.isIntersecting) return;
    en.target.classList.add("show");
    en.target.querySelectorAll("[data-w]").forEach(i => i.style.width = i.dataset.w + "%");
    io.unobserve(en.target);
  });
}, { threshold: .15 });
document.querySelectorAll(".reveal").forEach(n => io.observe(n));

document.getElementById("year").textContent = new Date().getFullYear();
</script>
</body>
</html>
