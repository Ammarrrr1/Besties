<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Sorry Fariii 💔</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to top, #ffe6e6, #fff);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      overflow: hidden;
    }

    h1 {
      font-size: 3rem;
      color: #ff4d4d;
      margin-bottom: 0;
    }

    .message {
      font-size: 1.3rem;
      color: #444;
      max-width: 600px;
      text-align: center;
      margin: 20px;
      background-color: #fff8f8;
      padding: 20px 30px;
      border-radius: 20px;
      box-shadow: 0 0 10px rgba(255, 0, 0, 0.1);
    }

    canvas {
      position: absolute;
      bottom: 0;
      left: 0;
      z-index: -1;
    }

    audio {
      display: none;
    }

    .heart {
      font-size: 4rem;
      animation: pulse 1.5s infinite;
      color: #ff4d4d;
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }
  </style>
</head>
<body onload="document.getElementById('sorryAudio').play()">

  <h1>I'm Sorry, Fariii 💔</h1>
  <div class="heart">❤️</div>
  <div class="message" id="msg">
    I never meant to hurt you. <br />
    You mean the world to me and your smile is everything. <br /><br />
    I'm truly sorry for the pain I caused. I value you more than words can say. <br />
    Please forgive me and let’s bring back the joy we share. <br /><br />
    I promise to always try better—for you, for us. 💫
  </div>

  <audio id="sorryAudio" autoplay loop>
    <source src="sorry-melody.mp3" type="audio/mp3">
    Your browser does not support audio.
  </audio>

  <canvas id="bgCanvas"></canvas>

  <script>
    const canvas = document.getElementById("bgCanvas");
    const ctx = canvas.getContext("2d");
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    let petals = [];

    function createPetal() {
      const x = Math.random() * canvas.width;
      const y = -20;
      const size = Math.random() * 6 + 2;
      const speed = Math.random() * 1 + 0.5;
      const drift = Math.random() * 2 - 1;
      petals.push({ x, y, size, speed, drift });
    }

    function drawPetals() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = "rgba(255, 182, 193, 0.7)";
      for (let i = 0; i < petals.length; i++) {
        const p = petals[i];
        ctx.beginPath();
        ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
        ctx.fill();
        p.y += p.speed;
        p.x += p.drift;
        if (p.y > canvas.height) {
          petals.splice(i, 1);
          i--;
        }
      }
    }

    function animate() {
      if (Math.random() < 0.3) {
        createPetal();
      }
      drawPetals();
      requestAnimationFrame(animate);
    }

    animate();
  </script>

</body>
</html>
