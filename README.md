<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Birthday Wish 🌹✨</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Great+Vibes&family=Roboto&display=swap');

    body {
      margin: 0;
      padding: 0;
      font-family: 'Roboto', sans-serif;
      background: linear-gradient(to bottom right, #ffecd2, #fcb69f);
      display: flex;
      justify-content: center;
      -: center;
      min-height: 100vh;
      text-align: center;
      color: #3b2f2f;
      overflow: hidden;
    }

    .card-container {
      position: relative;
      z-index: 1;
      width: 90%;
      max-width: 350px; /* optimized for mobile */
    }

    .card {
      position: relative;
      z-index: 2;
      background: rgba(255,255,255,0.95);
      border-radius: 20px;
      padding: 15px 12px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.25);
      animation: fadeIn 2s ease-in-out;
    }

    h1 {
      font-family: 'Great Vibes', cursive;
      font-size: 1.5em;
      color: #d94f6d;
      margin-bottom: 10px;
    }

    p {
      font-size: 0.9em;
      line-height: 1.3;
      margin: 8px 0;
    }

    .emoji {
      font-size: 1.2em;
      display: inline-block;
      animation: bounce 1.5s infinite;
    }

    .flower {
      font-size: 1.3em;
      margin: 6px 0;
      display: inline-block;
      animation: pop 1.2s ease-in-out infinite alternate;
    }

    @keyframes fadeIn {
      from { opacity:0; transform: translateY(15px);}
      to { opacity:1; transform: translateY(0);}
    }

    @keyframes bounce {
      0%,100%{transform:translateY(0);}
      50%{transform:translateY(-6px);}
    }

    @keyframes pop {
      0%{transform:scale(1);}
      50%{transform:scale(1.2);}
      100%{transform:scale(1);}
    }

    .heart-container {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      overflow: visible;
      z-index: 3;
    }

    .heart, .mini {
      position: absolute;
      opacity: 0;
      user-select: none;
    }
  </style>
</head>
<body>
  <div class="card-container">
    <div class="card">
      <h1>For You on Your Birthday <span class="emoji">🌹✨</span></h1>
      <p>🎂 <strong>Happy Birthday Krali!</strong></p>
      <p>You will always be a beautiful chapter in my story…</p>
      <p>Life’s choices took us apart, but my heart still remembers the warmth we shared. ❤️</p>
      <p class="flower">🌸🌼🌷</p>
      <p>Distance may have changed our paths, but my wishes for you remain the same:<br>
         may your days be full of love, peace, and everything your soul longs for. 🌸</p>
      <p>No matter where life takes us, I will always wish you happiness. ✨💛</p>
      <p>Yours, Xewang ❤️</p>
    </div>
    <div class="heart-container"></div>
  </div>

  <script>
    const container = document.querySelector('.heart-container');
    const hearts = ['❤️','💖','💗','💓','💘'];
    const sparkles = ['✨','🌟','💛'];

    function createHeart() {
      const heart = document.createElement('div');
      heart.classList.add('heart');
      heart.textContent = hearts[Math.floor(Math.random()*hearts.length)];

      const cardWidth = container.offsetWidth;
      const cardHeight = container.offsetHeight;

      heart.style.left = Math.random()*cardWidth + 'px';
      heart.style.top = cardHeight + 'px';
      heart.style.fontSize = (18 + Math.random()*16) + 'px';
      container.appendChild(heart);

      const endY = Math.random()*cardHeight/2 + 20;
      const duration = 5000 + Math.random()*2000;

      let start = null;
      function animate(timestamp) {
        if(!start) start = timestamp;
        const progress = timestamp - start;
        const pct = progress/duration;
        heart.style.top = cardHeight - pct*(cardHeight + endY) + 'px';
        heart.style.left = parseFloat(heart.style.left) + Math.sin(pct*10)*15 + 'px';
        heart.style.opacity = Math.min(pct*2,1);

        if(progress < duration) {
          requestAnimationFrame(animate);
        } else {
          explodeHeart(heart);
          container.removeChild(heart);
        }
      }
      requestAnimationFrame(animate);
    }

    function explodeHeart(heart) {
      for(let i=0;i<6;i++){
        const mini = document.createElement('div');
        mini.classList.add('mini');
        mini.textContent = [...hearts, ...sparkles][Math.floor(Math.random()*8)];
        mini.style.left = parseFloat(heart.style.left) + 'px';
        mini.style.top = parseFloat(heart.style.top) + 'px';
        mini.style.fontSize = (12 + Math.random()*14) + 'px';
        container.appendChild(mini);

        const angle = Math.random()*2*Math.PI;
        const distance = 20 + Math.random()*30;
        const duration = 600 + Math.random()*400;

        let start = null;
        function miniAnimate(timestamp){
          if(!start) start = timestamp;
          const progress = timestamp - start;
          const pct = progress/duration;
          mini.style.left = parseFloat(heart.style.left) + Math.cos(angle)*distance*pct + 'px';
          mini.style.top = parseFloat(heart.style.top) + Math.sin(angle)*distance*pct + 'px';
          mini.style.opacity = 1-pct;
          if(progress < duration){
            requestAnimationFrame(miniAnimate);
          } else {
            container.removeChild(mini);
          }
        }
        requestAnimationFrame(miniAnimate);
      }
    }

    setInterval(createHeart, 600);
  </script>
  </body>
</html>

difs
