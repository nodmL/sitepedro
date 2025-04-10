
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Parabéns Pedro FDP</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: #000;
      color: #fff;
      font-family: 'Comic Sans MS', cursive;
      text-align: center;
    }

    h1 {
      margin-top: 15vh;
      font-size: 4em;
      color: #ff4d4d;
      text-shadow: 3px 3px 10px #000;
      cursor: pointer;
      animation: shake 0.6s infinite;
    }

    @keyframes shake {
      0% { transform: rotate(0deg); }
      25% { transform: rotate(2deg); }
      50% { transform: rotate(-2deg); }
      75% { transform: rotate(2deg); }
      100% { transform: rotate(0deg); }
    }

    .emoji {
      font-size: 4em;
      animation: dance 1s infinite;
    }

    @keyframes dance {
      0%, 100% { transform: scale(1) rotate(0deg); }
      50% { transform: scale(1.3) rotate(20deg); }
    }

    #party-btn {
      margin-top: 30px;
      padding: 15px 30px;
      font-size: 1.5em;
      background: #ff00ff;
      border: none;
      border-radius: 10px;
      color: white;
      cursor: pointer;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0% { box-shadow: 0 0 10px #ff00ff; }
      50% { box-shadow: 0 0 40px #ff00ff; }
      100% { box-shadow: 0 0 10px #ff00ff; }
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      pointer-events: none;
    }
  </style>
</head>
<body>
  <canvas id="confetti"></canvas>

  <div class="emoji">**</div>
  <h1 onclick="explodeText(this)">Feliz aniversário, Pedro filha da puta!</h1>
  <div class="emoji">**</div>

  <button id="party-btn" onclick="triggerParty()">MANDAR MAIS ZOEIRA</button>

  <audio autoplay loop>
    <source src="https://www.myinstants.com/media/sounds/rick-roll.mp3" type="audio/mpeg">
    Seu navegador não suporta áudio.
  </audio>

  <script>
    // Confetti
    const canvas = document.getElementById('confetti');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const confetti = Array.from({length: 300}, () => ({
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height,
      r: Math.random() * 6 + 2,
      dx: Math.random() - 0.5,
      dy: Math.random() * 2 + 1,
      color: `hsl(${Math.random() * 360}, 100%, 50%)`
    }));

    function drawConfetti() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      confetti.forEach(p => {
        ctx.beginPath();
        ctx.arc(p.x, p.y, p.r, 0, 2 * Math.PI);
        ctx.fillStyle = p.color;
        ctx.fill();
        p.x += p.dx;
        p.y += p.dy;
        if (p.y > canvas.height) p.y = -10;
        if (p.x > canvas.width || p.x < 0) p.x = Math.random() * canvas.width;
      });
      requestAnimationFrame(drawConfetti);
    }
    drawConfetti();

    // Exploding text
    function explodeText(el) {
      el.style.transition = "all 0.2s";
      el.style.transform = "scale(1.5) rotate(720deg)";
      el.style.opacity = "0";
      setTimeout(() => {
        el.style.display = "none";
      }, 200);
    }

    // Extra chaos
    function triggerParty() {
      for (let i = 0; i < 10; i++) {
        const newEmoji = document.createElement('div');
        newEmoji.textContent = 'HAHA';
        newEmoji.style.position = 'absolute';
        newEmoji.style.left = `${Math.random() * 100}%`;
        newEmoji.style.top = `${Math.random() * 100}%`;
        newEmoji.style.fontSize = `${Math.random() * 2 + 1}em`;
        newEmoji.style.color = 'hsl(' + Math.random() * 360 + ', 100%, 50%)';
        newEmoji.style.animation = 'dance 1s infinite';
        document.body.appendChild(newEmoji);
      }
    }
  </script>
</body>
</html>
