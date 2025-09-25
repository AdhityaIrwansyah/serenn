<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link rel="icon" type="image/png" href="bday.png" />
  <title>happy birthday </title>
  <link rel="icon" href="https://cdn-icons-png.flaticon.com/512/5275/5275881.png">
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: #ffc1cc;
      color: #1e3a8a;
      font-family: 'Poppins', sans-serif;
      overflow: hidden;
    }

    .page {
      height: 100vh;
      width: 100vw;
      position: absolute;
      top: 0;
      left: 0;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 20px;
      opacity: 0;
      pointer-events: none;
      transition: opacity 1s ease;
    }

    .page.active {
      opacity: 1;
      pointer-events: auto;
    }

    h1 {
      font-size: 2.2rem;
      margin-bottom: 1rem;
    }

    h2 {
      font-size: 1.8rem;
      margin-bottom: 1rem;
    }

    .highlight {
      color: #1e3a8a;
      font-weight: bold;
    }

    .button {
      background-color: #ff69b4;
      color: #fff;
      border: none;
      border-radius: 25px;
      padding: 15px 30px;
      font-size: 1.2rem;
      cursor: pointer;
      margin-top: 30px;
      transition: background 0.3s;
    }

    .button:hover {
      background-color: #fc6c85;
    }

    img {
      max-width: 70vw;
      max-height: 50vh;
      margin-bottom: 20px;
    }

    .letter {
      white-space: pre-line;
      font-size: 1.1rem;
      max-width: 600px;
      text-align: left;
      border-left: 3px solid #1e3a8a;
      padding-left: 15px;
      min-height: 200px;
    }

    .falling {
      position: fixed;
      top: -30px;
      font-size: 24px;
      animation: fall linear infinite;
      pointer-events: none;
      z-index: 9999;
    }

    .blue-heart {
      color: #1e3a8a;
    }

    .yellow-star {
      color: #facc15;
    }

    @keyframes fall {
      to {
        transform: translateY(120vh) rotate(360deg);
        opacity: 0;
      }
    }

    @media (max-width: 600px) {
      h1 {
        font-size: 1.8rem;
      }

      h2 {
        font-size: 1.5rem;
      }

      .button {
        padding: 10px 20px;
        font-size: 1rem;
      }

      .letter {
        font-size: 1rem;
      }
    }
  </style>
</head>
<body>
  <div class="page active" id="page1">
    <img src="https://64.media.tumblr.com/f8e985db839547751df138a46a564880/0b8cd0511fb8dd71-14/s400x600/6c9b6e2268e123a8aa544d042401e0cec1583bf1.gif" alt="Cute Icon" />
    <h1>Happy Birthday <span class="highlight">
      ⋆˚✿˖° Shereen Miracly Saleh ˶ᵔ ᵕ ᵔ✿˶ </span></h1>
    <p> I want to say something to you ✨</p>
    <button class="button" onclick="goToPage(2)">oke </button>
  </div>

  <div class="page" id="page2">
    <img src="download.gif" alt="Envelope" />
    <p>Klik 1 kalau penasaran!!!</p>
    <button class="button" onclick="goToPage(3)">11111111111 </button>
  </div>

<div class="page" id="page3" style="font-family: 'Dancing Script', cursive;">
    <h2> ⋆˚✿˖°Happy Birthday Eyen⋆˚✿˖° .ᐟ </h2>
    <div class="letter" id="letterText"></div>
</div>

  <audio id="bg-music" src="Party.mp3" autoplay loop muted></audio>

  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <script>
    const fullLetter = `Happy 18th birthday, Teman Baik (˶ᵔ ᵕ ᵔ˶)

    Thank you for being yourself this year and doing your best, don't forget to rest if you feel tired.

    May your day be filled with good people, happiness, gentle laughter, and tender moments that make your heart flutter and may this year you can make what you dream of come true and be one of the best years of your life!!!

    thank you for being a good person and always being a good person

    Dari orang keren
Adhitya Irwansyah •ᴗ•`;

    function goToPage(pageNum) {
      const pages = document.querySelectorAll('.page');
      pages.forEach(p => p.classList.remove('active'));
      const next = document.getElementById(`page${pageNum}`);
      next.classList.add('active');

      if (pageNum === 3) {
        const music = document.getElementById("bg-music");
        music.muted = false;
        music.play().catch(e => console.log("Autoplay blocked:", e));

        confetti({ particleCount: 150, spread: 100, origin: { y: 0.6 } });
        typeText(fullLetter, document.getElementById('letterText'), 25);
        startFallingSymbols();
      }
    }

    function typeText(text, element, speed) {
      element.innerHTML = '';
      let i = 0;
      function type() {
        if (i < text.length) {
          element.innerHTML += text.charAt(i);
          i++;
          setTimeout(type, speed);
        }
      }
      type();
    }

    function startFallingSymbols() {
      setInterval(() => {
        const el = document.createElement('div');
        el.classList.add('falling');
        const isHeart = Math.random() < 0.5;
        el.innerText = isHeart ? '🌸' : '💐';
        el.classList.add(isHeart ? 'blue-heart' : 'yellow-star');
        el.style.left = Math.random() * 100 + 'vw';
        el.style.animationDuration = (3 + Math.random() * 2) + 's';
        document.body.appendChild(el);
        setTimeout(() => el.remove(), 6000);
      }, 300);
    }
  </script>
</body>
</html>
