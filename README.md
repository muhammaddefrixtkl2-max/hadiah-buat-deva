
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Untuk Kamu ❤️</title>

<style>
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: black;
    overflow: hidden;
}

/* INTRO */
.intro {
    position: absolute;
    width: 100%;
    height: 100%;
    background: black;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.intro h1 {
    opacity: 0;
    animation: fadeText 2s forwards;
}

.intro h1:nth-child(2){ animation-delay: 2s; }
.intro h1:nth-child(3){ animation-delay: 4s; }

@keyframes fadeText {
    to { opacity: 1; }
}

/* MAIN */
.popup {
    position: absolute;
    width: 100%;
    height: 100%;
    display: none;
}

/* SLIDER */
.slider {
    display: none;
}

.slider img {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    opacity: 0;
}

.slider img.active {
    opacity: 1;
    animation: zoomFade 4s ease;
}

@keyframes zoomFade {
    from { opacity: 0; transform: scale(1.2); }
    to { opacity: 1; transform: scale(1); }
}

/* overlay */
.overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.4);
}

/* TEXT DI PINGGIR */
.text {
    position: absolute;
    bottom: 30px;
    left: 30px;
    color: white;
    z-index: 2;
}

#text {
    font-size: 26px;
    background: rgba(0,0,0,0.5);
    padding: 10px 15px;
    border-radius: 10px;
    text-shadow: 0 0 10px pink;
    transition: all 0.5s ease;
}

/* BUTTON */
.btn {
    padding: 12px 25px;
    margin-top: 10px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
}

.yes { background: #28a745; color: white; }
.no {
    background: red;
    color: white;
    position: absolute;
}

/* EFFECT */
.effect {
    position: fixed;
    top: -50px;
    font-size: 20px;
    animation: fall linear forwards;
}

@keyframes fall {
    to {
        transform: translateY(110vh) rotate(360deg);
        opacity: 0;
    }
}
</style>
</head>

<body>

<!-- INTRO -->
<div class="intro" id="intro">
    <h1>Untuk Kamu ❤️</h1>
    <h1>Yang habis sidang...</h1>
    <h1>Selamat Atas gelarnya sayangku ✨</h1>
</div>

<!-- MAIN -->
<div class="popup" id="popup">

    <!-- FOTO -->
    <div class="slider" id="slider">
        <img src="WhatsApp Image 2026-05-04 at 17.59.30.jpeg" class="slide active">
           <img src="WhatsApp Image 2026-05-04 at 17.59.31.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 17.59.32.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 18.13.24.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 18.13.25.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 18.13.26.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 18.15.40.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 18.15.41.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 18.15.42.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 18.15.43.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 18.15.45.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 18.13.27.jpeg" class="slide">
            <img src="WhatsApp Image 2026-05-04 at 18.15.42.jpeg" class="slide">
    </div>

    <div class="overlay"></div>

    <div class="text">
        <div id="text">Kamu sayang aku nggak? ❤️</div>

        <button class="btn yes" id="btnYes" onclick="jawabIya()">Iya ❤️</button>
        <button class="btn no" id="btnNo">Tidak 😢</button>
    </div>

</div>

<!-- MUSIK -->
<audio id="musik" loop>
    <source src="Nadhif Basalamah (with Aziz Harun & Aisha Retno) - kota ini tak sama tanpamu (Official Lyric Video).mp3" type="audio/mpeg">
</audio>

<script>
/* INTRO */
setTimeout(() => {
    document.getElementById("intro").style.display = "none";
    document.getElementById("popup").style.display = "block";
}, 6000);

/* SLIDER */
let index = 0;
let running = false;

function startSlider() {
    if (running) return;
    running = true;

    const slides = document.querySelectorAll(".slide");

    setInterval(() => {
        slides[index].classList.remove("active");
        index = (index + 1) % slides.length;
        slides[index].classList.add("active");
    }, 4000);
}

/* EFFECT */
function createEffect(symbol) {
    const el = document.createElement("div");
    el.classList.add("effect");
    el.innerHTML = symbol;

    el.style.left = Math.random() * 100 + "vw";
    el.style.animationDuration = (Math.random()*3+2)+"s";

    document.body.appendChild(el);
    setTimeout(() => el.remove(), 5000);
}

function startEffects() {
    setInterval(() => createEffect("❤️"), 300);
    setInterval(() => createEffect("🎉"), 400);
    setInterval(() => createEffect("🌸"), 500);
}

/* MUSIK */
function playMusic() {
    document.getElementById("musik").play();
}

/* KLIK IYA */
function jawabIya() {
    document.getElementById("slider").style.display = "block";

    document.getElementById("btnYes").style.display = "none";
    document.getElementById("btnNo").style.display = "none";

    document.getElementById("text").innerHTML = "Aku juga sayang kamu sayang ❤️ maaf ya aku gabisa dateng my ratu kebo ini hadiah dari aku buat kamu";

    playMusic();
    startSlider();
    startEffects();
}

/* TOMBOL KABUR */
const noBtn = document.getElementById("btnNo");

noBtn.addEventListener("mouseover", () => {
    const x = Math.random()*200-100;
    const y = Math.random()*200-100;
    noBtn.style.transform = `translate(${x}px, ${y}px)`;
});
</script>

</body>
</html>
