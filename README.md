
Radio en vivo DJ WILMER
<html><head><base href="https://player.voxhd.com.br/player-app-multi-plataforma2/10788">
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DJ WILMER EN  - EN VIVO </title>

<style>
:root {
  --primary: #10bec1;
  --dark: #111;
  --light: #fff;
}

body {
  margin: 0;
  padding: 0;
  font-family: 'Open Sans', sans-serif;
  background: var(--dark);
  color: var(--light);
}

.player-container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: linear-gradient(45deg, var(--dark), var(--primary));
  padding: 2rem;
}

.logo {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  margin-bottom: 2rem;
  background: var(--light);
  padding: 1rem;
  box-shadow: 0 0 30px rgba(0,0,0,0.3);
  animation: pulse 2s infinite;
}

.controls {
  display: flex;
  gap: 1rem;
  margin: 2rem 0;
}

.btn {
  background: var(--light);
  border: none;
  padding: 1rem 2rem;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s;
}

.btn:hover {
  transform: scale(1.1);
  box-shadow: 0 0 20px rgba(255,255,255,0.3);
}

.visualizer {
  width: 300px;
  height: 100px;
  margin: 2rem 0;
}

@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.05); }
  100% { transform: scale(1); }
}

.wave {
  stroke-dasharray: 0 16 0 16;
  animation: dash 1.5s linear infinite;
}

@keyframes dash {
  to {
    stroke-dashoffset: 32;
  }
}
</style>
</head>
<body>
<div class="player-container">
  <img class="logo" src=" https://i.ibb.co/mhw9LGh/DJ-WILMER-PNG-ORIGINAL.png" alt="DJ WILMER" width="200" height="200">
  
  <svg class="visualizer" viewBox="0 0 300 100">
    <path class="wave" d="M 0,50 Q 75,30 150,50 T 300,50" fill="none" stroke="white" stroke-width="2"/>
    <path class="wave" d="M 0,50 Q 75,70 150,50 T 300,50" fill="none" stroke="white" stroke-width="2"/>
  </svg>

  <div class="controls">
    <button class="btn" id="playBtn">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="var(--primary)">
        <path d="M8 5v14l11-7z"/>
      </svg>
    </button>
    <button class="btn" id="stopBtn">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="var(--primary)">
        <path d="M6 6h12v12H6z"/>
      </svg>
    </button>
  </div>

  <div id="nowPlaying">EN VIVO: DJ WILMER </div>
</div>

<script>
let audio = new Audio(' https://stream.zeno.fm/wttrxavefwzuv');
let isPlaying = false;

document.getElementById('playBtn').addEventListener('click', () => {
  if (!isPlaying) {
    audio.play();
    isPlaying = true;
  } else {
    audio.pause();
    isPlaying = false;
  }
});

document.getElementById('stopBtn').addEventListener('click', () => {
  audio.pause();
  audio.currentTime = 0;
  isPlaying = false;
});

// PWA Install prompt
let deferredPrompt;
window.addEventListener('beforeinstallprompt', (e) => {
  e.preventDefault();
  deferredPrompt = e;
});

// Add install button if PWA installable
if (window.matchMedia('(display-mode: standalone)').matches) {
  // Already installed
} else {
  const installBtn = document.createElement('button');
  installBtn.classList.add('btn');
  installBtn.textContent = 'Install App';
  installBtn.addEventListener('click', async () => {
    if (deferredPrompt) {
      deferredPrompt.prompt();
      const { outcome } = await deferredPrompt.userChoice;
      deferredPrompt = null;
    }
  });
  document.querySelector('.controls').appendChild(installBtn);
}
</script>
</body></html>
