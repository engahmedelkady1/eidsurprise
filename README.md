<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Nadody, you will be my Eid?</title>
  <style>
    * {
      box-sizing: border-box;
    }

    :root {
      --bg1: #0f172a;
      --bg2: #1e293b;
      --gold: #f8d66d;
      --gold-soft: #fde68a;
      --green: #22c55e;
      --red: #ef4444;
      --text: #ffffff;
      --card: rgba(255, 255, 255, 0.08);
      --border: rgba(255, 255, 255, 0.18);
    }

    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: Arial, Helvetica, sans-serif;
      color: var(--text);
      background:
        radial-gradient(circle at top, rgba(250, 204, 21, 0.12), transparent 25%),
        linear-gradient(180deg, var(--bg2), var(--bg1));
      overflow: hidden;
      position: relative;
    }

    .stars, .hearts {
      position: fixed;
      inset: 0;
      pointer-events: none;
      overflow: hidden;
    }

    .star {
      position: absolute;
      width: 3px;
      height: 3px;
      background: white;
      border-radius: 50%;
      opacity: 0.8;
      animation: twinkle 2.5s infinite ease-in-out;
    }

    @keyframes twinkle {
      0%, 100% { opacity: 0.25; transform: scale(1); }
      50% { opacity: 1; transform: scale(1.8); }
    }

    .moon {
      position: fixed;
      top: 40px;
      right: 60px;
      width: 86px;
      height: 86px;
      border-radius: 50%;
      background: var(--gold-soft);
      box-shadow: 0 0 30px rgba(253, 224, 71, 0.45);
      opacity: 0.95;
    }

    .moon::after {
      content: "";
      position: absolute;
      top: 8px;
      left: 22px;
      width: 86px;
      height: 86px;
      border-radius: 50%;
      background: var(--bg2);
    }

    .container {
      position: relative;
      width: min(92vw, 680px);
      text-align: center;
      padding: 30px 22px 40px;
      border: 1px solid var(--border);
      background: var(--card);
      backdrop-filter: blur(12px);
      border-radius: 28px;
      box-shadow: 0 10px 40px rgba(0, 0, 0, 0.25);
      z-index: 2;
    }

    .eid-badge {
      display: inline-block;
      margin-bottom: 12px;
      padding: 8px 16px;
      border-radius: 999px;
      background: rgba(248, 214, 109, 0.14);
      border: 1px solid rgba(248, 214, 109, 0.35);
      color: var(--gold-soft);
      font-weight: 700;
      letter-spacing: 0.4px;
      font-size: 0.95rem;
    }

    h1 {
      margin: 0;
      font-size: clamp(2rem, 5vw, 3.3rem);
      line-height: 1.15;
      font-weight: 800;
    }

    .subtitle {
      margin: 14px auto 18px;
      font-size: 1rem;
      line-height: 1.7;
      max-width: 520px;
      color: rgba(255,255,255,0.88);
    }

    .image-wrap {
      width: min(270px, 68vw);
      margin: 0 auto 16px;
      aspect-ratio: 1 / 1;
      display: grid;
      place-items: center;
    }

    .image-wrap img {
      width: 100%;
      height: 100%;
      object-fit: contain;
      user-select: none;
      -webkit-user-drag: none;
      filter: drop-shadow(0 8px 22px rgba(0,0,0,0.2));
    }

    .buttons {
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 14px;
      min-height: 64px;
      margin-top: 6px;
    }

    button {
      border: none;
      padding: 14px 30px;
      font-size: 1.05rem;
      font-weight: 800;
      border-radius: 14px;
      cursor: pointer;
      transition: transform 0.18s ease, box-shadow 0.18s ease, opacity 0.18s ease;
      box-shadow: 0 8px 18px rgba(0,0,0,0.18);
    }

    button:hover {
      transform: translateY(-1px);
    }

    #yesBtn {
      background: var(--green);
      color: white;
    }

    #noBtn {
      background: var(--red);
      color: white;
      position: relative;
    }

    .message {
      display: none;
      margin-top: 18px;
      font-size: clamp(1.2rem, 3vw, 1.8rem);
      font-weight: 800;
      color: var(--gold-soft);
    }

    .note {
      display: none;
      margin-top: 12px;
      color: rgba(255,255,255,0.92);
      font-size: 1rem;
      line-height: 1.7;
    }

    .show {
      display: block;
    }

    .heart {
      position: absolute;
      bottom: -30px;
      font-size: 24px;
      animation: floatUp linear forwards;
      opacity: 0.95;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(0.9);
        opacity: 0;
      }
      15% {
        opacity: 1;
      }
      100% {
        transform: translateY(-110vh) scale(1.4) rotate(10deg);
        opacity: 0;
      }
    }

    .footer {
      margin-top: 18px;
      font-size: 0.9rem;
      color: rgba(255,255,255,0.62);
    }

    @media (max-width: 640px) {
      .moon {
        top: 24px;
        right: 24px;
        width: 64px;
        height: 64px;
      }

      .moon::after {
        width: 64px;
        height: 64px;
        left: 16px;
        top: 7px;
      }

      .container {
        padding: 24px 16px 32px;
        border-radius: 22px;
      }
    }
  </style>
</head>
<body>
  <div class="stars" id="stars"></div>
  <div class="hearts" id="hearts"></div>
  <div class="moon"></div>

  <main class="container">
    <div class="eid-badge">🌙 Eid Surprise</div>
    <h1 id="title">Nadody, you will be my Eid?</h1>
    <p class="subtitle">I only need one answer… and I really hope it is yes 💛</p>

    <div class="image-wrap">
      <img
        id="mainImage"
        src="https://media.tenor.com/4RZs0d5gYpAAAAAi/milk-and-mocha-bear-hearts.gif"
        alt="cute character"
      />
    </div>

    <div class="buttons" id="buttons">
      <button id="yesBtn">Yes ✨</button>
      <button id="noBtn">No</button>
    </div>

    <div class="message" id="message">Knew it, Nadody 😌🌙</div>
    <div class="note" id="note">Now Eid is officially sweeter with you 💖</div>
    <div class="footer">Made with love for Nadody</div>
  </main>

  <script>
    const yesBtn = document.getElementById('yesBtn');
    const noBtn = document.getElementById('noBtn');
    const title = document.getElementById('title');
    const message = document.getElementById('message');
    const note = document.getElementById('note');
    const buttons = document.getElementById('buttons');
    const mainImage = document.getElementById('mainImage');
    const hearts = document.getElementById('hearts');
    const stars = document.getElementById('stars');

    let yesScale = 1;
    const noTexts = [
      'No',
      'Are you sure?',
      'Really?',
      'Think again',
      'Please?',
      'Last chance?',
      'Still no?'
    ];
    let noIndex = 0;

    function createStars() {
      for (let i = 0; i < 45; i++) {
        const star = document.createElement('span');
        star.className = 'star';
        star.style.left = Math.random() * 100 + 'vw';
        star.style.top = Math.random() * 100 + 'vh';
        star.style.animationDelay = (Math.random() * 2.8) + 's';
        star.style.animationDuration = (1.8 + Math.random() * 2.5) + 's';
        stars.appendChild(star);
      }
    }

    function moveNoButton() {
      const maxX = window.innerWidth - noBtn.offsetWidth - 18;
      const maxY = window.innerHeight - noBtn.offsetHeight - 18;
      const randomX = Math.max(8, Math.floor(Math.random() * maxX));
      const randomY = Math.max(8, Math.floor(Math.random() * maxY));

      noBtn.style.position = 'fixed';
      noBtn.style.left = `${randomX}px`;
      noBtn.style.top = `${randomY}px`;

      yesScale += 0.14;
      yesBtn.style.transform = `scale(${yesScale})`;

      noIndex = (noIndex + 1) % noTexts.length;
      noBtn.textContent = noTexts[noIndex];
    }

    function launchHearts(count = 18) {
      for (let i = 0; i < count; i++) {
        const heart = document.createElement('div');
        heart.className = 'heart';
        heart.textContent = Math.random() > 0.5 ? '💖' : '🌙';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = (3 + Math.random() * 2.4) + 's';
        heart.style.fontSize = (20 + Math.random() * 18) + 'px';
        heart.style.animationDelay = (Math.random() * 0.35) + 's';
        hearts.appendChild(heart);

        setTimeout(() => heart.remove(), 6000);
      }
    }

    noBtn.addEventListener('mouseenter', moveNoButton);
    noBtn.addEventListener('click', moveNoButton);
    noBtn.addEventListener('touchstart', moveNoButton, { passive: true });

    yesBtn.addEventListener('click', () => {
      title.textContent = 'Knew it, Nadody 😌🌙';
      message.classList.add('show');
      note.classList.add('show');
      buttons.style.display = 'none';
      mainImage.src = 'https://media.tenor.com/sJQJmT4mP6oAAAAi/milk-and-mocha-bear-couple.gif';
      launchHearts(28);
    });

    createStars();
  </script>
</body>
</html>
