[index.html](https://github.com/user-attachments/files/34033775/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
<title>For My Favorite Girl 💗</title>
<style>
  :root { 
    --pink: #5da878; 
    --rose: #d5f0dc; 
    --cream: #f5fff7; 
    --ink: #294b37;
    --touch-target: 48px;
  }

  * { 
    box-sizing: border-box; 
    -webkit-tap-highlight-color: transparent;
  }
  
  html, body {
    height: 100%;
    height: 100dvh;
    margin: 0;
    padding: 0;
    font-family: "Trebuchet MS", system-ui, -apple-system, sans-serif;
    color: var(--ink);
    background: linear-gradient(145deg, #f5fff7 0%, #d8f2df 48%, #edf9ef 100%);
    overflow: hidden;
    touch-action: manipulation;
  }

  /* Audio Widget */
  .music-widget {
    position: fixed;
    top: calc(12px + env(safe-area-inset-top));
    right: calc(12px + env(safe-area-inset-right));
    z-index: 10;
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 14px;
    background: rgba(255, 255, 255, 0.85);
    border: 1px solid rgba(255, 255, 255, 0.95);
    border-radius: 999px;
    box-shadow: 0 8px 24px rgba(40, 115, 70, 0.15);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    cursor: pointer;
    user-select: none;
  }

  .music-btn {
    width: 32px;
    height: 32px;
    border-radius: 50%;
    background: #378653;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.85rem;
    box-shadow: 0 4px 10px rgba(55, 134, 83, 0.3);
  }

  .music-text {
    font-size: 0.8rem;
    font-weight: 700;
    color: #287346;
  }

  /* Animated Equalizer */
  .eq-bars {
    display: flex;
    align-items: flex-end;
    gap: 2px;
    height: 14px;
  }

  .eq-bar {
    width: 3px;
    background: #378653;
    border-radius: 2px;
    height: 4px;
  }

  .playing .eq-bar:nth-child(1) { animation: eq 0.6s infinite ease-in-out alternate; }
  .playing .eq-bar:nth-child(2) { animation: eq 0.8s infinite ease-in-out alternate 0.2s; }
  .playing .eq-bar:nth-child(3) { animation: eq 0.5s infinite ease-in-out alternate 0.4s; }

  @keyframes eq {
    0% { height: 4px; }
    100% { height: 14px; }
  }

  /* Background Floating Hearts */
  .hearts { position: fixed; inset: 0; pointer-events: none; overflow: hidden; z-index: 0; }
  .heart { position: absolute; bottom: -40px; color: #79c795; opacity: .45; animation: floatUp linear infinite; }
  @keyframes floatUp { to { transform: translateY(-115vh) rotate(25deg); opacity: 0; } }

  main {
    position: relative;
    z-index: 1;
    height: 100dvh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: clamp(12px, 3vw, 20px);
    padding-top: calc(56px + env(safe-area-inset-top));
    padding-bottom: calc(12px + env(safe-area-inset-bottom));
  }

  .view-container {
    width: min(720px, 100%);
    max-height: calc(100dvh - 72px - env(safe-area-inset-top) - env(safe-area-inset-bottom));
    overflow-y: auto;
    -webkit-overflow-scrolling: touch;
    background: rgba(255, 255, 255, 0.88);
    border: 1px solid rgba(255, 255, 255, 0.95);
    border-radius: 28px;
    box-shadow: 0 20px 70px rgba(79, 154, 104, 0.15);
    backdrop-filter: blur(10px);
    -webkit-backdrop-filter: blur(10px);
    padding: clamp(20px, 5vw, 40px);
    text-align: center;
    position: relative;
    transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1), opacity 0.4s ease-in-out;
    opacity: 1;
    transform: scale(1) translateY(0);
  }

  .view-container.slide-out-left { opacity: 0; transform: scale(0.95) translateX(-40px); }
  .view-container.slide-out-right { opacity: 0; transform: scale(0.95) translateX(40px); }
  .view-container.slide-in { animation: slideInFromRight 0.4s cubic-bezier(0.4, 0, 0.2, 1) forwards; }

  @keyframes slideInFromRight {
    from { opacity: 0; transform: scale(0.95) translateX(40px); }
    to { opacity: 1; transform: scale(1) translateY(0); }
  }

  .view-section { display: none; }
  .view-section.active { display: block; }

  .eyebrow { letter-spacing: .18em; text-transform: uppercase; font-size: .75rem; color: #43845a; font-weight: 700; }
  h1 { font-family: Georgia, serif; font-size: clamp(2.1rem, 7vw, 3.8rem); line-height: 1.05; margin: 14px 0; color: #287346; }
  .subtitle { font-size: clamp(0.9rem, 2.8vw, 1.1rem); line-height: 1.6; max-width: 530px; margin: 0 auto 22px; }
  .big-heart { font-size: clamp(3rem, 10vw, 3.8rem); display: inline-block; animation: beat 1.25s infinite; filter: drop-shadow(0 6px 10px #f79bb6); }
  @keyframes beat { 0%,100%{transform:scale(1)} 15%{transform:scale(1.13)} 30%{transform:scale(1)} 45%{transform:scale(1.08)} }

  .button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    min-height: var(--touch-target);
    border: 0;
    border-radius: 999px;
    padding: 12px 24px;
    margin: 6px;
    background: #378653;
    color: white;
    font-size: 0.95rem;
    font-weight: 700;
    cursor: pointer;
    text-decoration: none;
    box-shadow: 0 8px 18px rgba(55, 134, 83, 0.25);
    transition: transform 0.15s ease, background 0.2s ease;
    touch-action: manipulation;
  }
  .button:active { transform: scale(0.96); background: #286b40; }
  .button.secondary { background: #eaf8ee; color: #287346; box-shadow: none; border: 1px solid #a8e0b9; }

  h2 { font: bold clamp(1.6rem, 5vw, 2.3rem) Georgia, serif; color: #287346; text-align: center; margin: 0 0 10px; }
  .lead { text-align: center; line-height: 1.5; max-width: 650px; margin: 0 auto 18px; font-size: 0.9rem; }

  .letter {
    text-align: left;
    background: #fffdfd;
    border-radius: 12px 20px 20px 12px;
    padding: clamp(16px, 4vw, 28px);
    box-shadow: 0 10px 30px rgba(167, 71, 104, 0.08);
    border-left: 5px solid #8fd0a2;
    font: 0.95rem/1.75 Georgia, serif;
  }
  .letter p { margin-top: 0; margin-bottom: 1rem; }

  .reasons { max-width: 650px; margin: auto; text-align: left; }
  .reason { background: rgba(255, 255, 255, 0.75); padding: 12px 16px; margin: 8px 0; border-radius: 14px; line-height: 1.5; font-size: 0.9rem; }
  .reason b { color: #378653; margin-right: 8px; }

  .promise { text-align: center; background: #378653; color: white; border-radius: 20px; padding: 20px 16px; margin-top: 16px; }
  .promise h3 { font: bold 1.35rem Georgia, serif; margin: 0 0 8px; }
  .promise p { line-height: 1.55; max-width: 600px; margin: auto; font-size: 0.9rem; }

  #surprise {
    display: none;
    margin: 16px auto 0;
    padding: 16px;
    border-radius: 16px;
    background: #eaf8ee;
    line-height: 1.6;
    animation: appear 0.5s ease;
  }
  @keyframes appear { from{opacity:0; transform:translateY(8px)} to{opacity:1; transform:none} }

  .nav-group {
    margin-top: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 8px;
  }

  @media(prefers-reduced-motion:reduce) { *,*::before,*::after { animation-duration:.01ms!important; } }
</style>
</head>
<body>

<!-- Background Audio Player linked to your Google Drive file -->
<audio id="bgAudio" loop preload="auto">
  <source src="https://litter.catbox.moe/c79b0sn118dpanu2.mp3" type="audio/mpeg">
  <!-- Fallback track just in case -->
  <source src="https://cdn.pixabay.com/download/audio/2022/05/27/audio_1808fbf07a.mp3" type="audio/mpeg">
</audio>

<!-- Audio Widget -->
<div class="music-widget" id="musicToggle" role="button" aria-label="Toggle Background Music">
  <div class="music-btn" id="musicBtnIcon">▶</div>
  <div class="eq-bars" id="eqBars">
    <div class="eq-bar"></div>
    <div class="eq-bar"></div>
    <div class="eq-bar"></div>
  </div>
  <span class="music-text" id="musicText">Music</span>
</div>

<div class="hearts" id="hearts" aria-hidden="true"></div>

<main>
  <div class="view-container" id="cardContainer">
    
    <!-- HOME SECTION -->
    <div class="view-section active" id="home">
      <div class="big-heart" aria-hidden="true">💗</div>
      <div class="eyebrow">A little corner of the internet, just for you</div>
      <h1>For My<br>Favorite Girl</h1>
      <p class="subtitle">If I could give you one thing in this world, it would be the chance to see yourself through my eyes. Maybe then you'd understand just how special you are to me.</p>
      
      <div>
        <button class="button" onclick="goToSlide('letter', 'right')">Open your letter 💌</button>
      </div>
    </div>

    <!-- LETTER SECTION -->
    <div class="view-section" id="letter">
      <h2>A letter for you</h2>
      <p class="lead">For the girl who makes ordinary days feel a little more beautiful.</p>
      <article class="letter">
        <p>Hi, love. ❤️</p>
        <p>I just want you to know how grateful I am that you came into my life. You make me smile in ways you probably don't even notice, and somehow, even the smallest moments with you become memories I want to keep.</p>
        <p>I know not every day will be easy. There may be moments when we're tired, quiet, or figuring things out. But I don't want to be here only for the happy days. I want to listen when things feel heavy, celebrate your little wins, hold your hand through the uncertain moments, and keep choosing us with patience and love.</p>
        <p>You don't have to be perfect with me. You can be yourself—the happy you, the sleepy you, the overthinking you, and the you that just needs a little reassurance. I want you to feel loved without having to earn it.</p>
        <p>Thank you for being you, love. If I could choose all over again, I'd still want to find my way to you. Today, tomorrow, and in all the little days after. 💗</p>
        <p style="margin-bottom:0">Always yours,<br><strong>Dustine ♡</strong></p>
      </article>
      <div class="nav-group">
        <button class="button secondary" onclick="goToSlide('home', 'left')">← Back</button>
        <button class="button" onclick="goToSlide('reasons', 'right')">Next →</button>
      </div>
    </div>

    <!-- REASONS SECTION -->
    <div class="view-section" id="reasons">
      <h2>Little things I love about you</h2>
      <p class="lead">It's never just one big thing. It's a hundred little things that make you, you.</p>
      <div class="reasons">
        <div class="reason"><b>01.</b> The way you can make me smile without even trying.</div>
        <div class="reason"><b>02.</b> Your heart, your kindness, and the way you care.</div>
        <div class="reason"><b>03.</b> The little things you say that stay in my mind all day.</div>
        <div class="reason"><b>04.</b> The comfort of talking to you, even when we have nothing special to say.</div>
        <div class="reason"><b>05.</b> The fact that you're you—and that's already more than enough.</div>
        <div class="reason"><b>06.</b> Every new memory we get to make together.</div>
        <div class="reason"><b>07.</b> The way talking to you makes me feel like I'm home.</div>
      </div>
      <div class="nav-group">
        <button class="button secondary" onclick="goToSlide('letter', 'left')">← Back</button>
        <button class="button" onclick="goToSlide('promise', 'right')">Next →</button>
      </div>
    </div>

    <!-- PROMISE SECTION -->
    <div class="view-section" id="promise">
      <h2>One little promise</h2>
      <p class="lead">Not a promise that everything will always be perfect, but a promise to keep showing up.</p>
      <div class="promise">
        <h3>It's you and me, love. 🫶</h3>
        <p>I promise to keep learning how to love you better, to make room for your feelings, to communicate honestly, and to remember that we're on the same team—even on the hard days.</p>
      </div>
      <div style="text-align:center;margin-top:20px">
        <button class="button" id="surpriseBtn" type="button">One last thing… 💝</button>
        <div id="surprise" role="status">
          In case you ever forget: you are loved, you are appreciated, and you matter so much to me. You don't have to do anything extraordinary to deserve that love. Just being you is enough. <br>
          <span style="font-size:1.2rem; font-weight: bold; color: #287346;">I love you, always. 💗</span>
        </div>
      </div>
      <div class="nav-group">
        <button class="button secondary" onclick="goToSlide('reasons', 'left')">← Back</button>
        <button class="button secondary" onclick="goToSlide('home', 'left')">🏠 Home</button>
      </div>
    </div>

  </div>
</main>

<script>
  // Floating background hearts generator
  const heartLayer = document.getElementById('hearts');
  const symbols = ['♡','♥','💕','✧'];
  for (let i = 0; i < 20; i++) {
    const heart = document.createElement('span');
    heart.className = 'heart';
    heart.textContent = symbols[Math.floor(Math.random() * symbols.length)];
    heart.style.left = Math.random() * 100 + '%';
    heart.style.fontSize = (14 + Math.random() * 20) + 'px';
    heart.style.animationDuration = (12 + Math.random() * 15) + 's';
    heart.style.animationDelay = (-Math.random() * 25) + 's';
    heartLayer.appendChild(heart);
  }

  // Audio Controls & Autoplay Policy Unlock
  const audio = document.getElementById('bgAudio');
  const musicToggle = document.getElementById('musicToggle');
  const musicBtnIcon = document.getElementById('musicBtnIcon');
  const eqBars = document.getElementById('eqBars');
  const musicText = document.getElementById('musicText');
  let isPlaying = false;
  let hasInteracted = false;

  function playMusic() {
    audio.play().then(() => {
      isPlaying = true;
      musicBtnIcon.textContent = '⏸';
      eqBars.classList.add('playing');
      musicText.textContent = 'Playing';
    }).catch(err => {
      console.log('Autoplay prevented. User tap required.');
    });
  }

  function pauseMusic() {
    audio.pause();
    isPlaying = false;
    musicBtnIcon.textContent = '▶';
    eqBars.classList.remove('playing');
    musicText.textContent = 'Music';
  }

  musicToggle.addEventListener('click', (e) => {
    e.stopPropagation();
    if (isPlaying) {
      pauseMusic();
    } else {
      playMusic();
    }
  });

  // Unlock audio on first touch/tap anywhere on mobile screen
  function handleFirstInteraction() {
    if (!hasInteracted) {
      hasInteracted = true;
      playMusic();
      document.removeEventListener('touchstart', handleFirstInteraction);
      document.removeEventListener('click', handleFirstInteraction);
    }
  }

  document.addEventListener('touchstart', handleFirstInteraction, { passive: true });
  document.addEventListener('click', handleFirstInteraction, { passive: true });

  // Slideshow transition logic
  const slideOrder = ['home', 'letter', 'reasons', 'promise'];
  
  function goToSlide(targetId, direction) {
    const container = document.getElementById('cardContainer');
    
    // Slide out current card
    container.classList.add(direction === 'right' ? 'slide-out-left' : 'slide-out-right');

    setTimeout(() => {
      // Hide all sections, show target section
      document.querySelectorAll('.view-section').forEach(sec => sec.classList.remove('active'));
      document.getElementById(targetId).classList.add('active');
      
      // Reset scroll position of the container
      container.scrollTop = 0;

      // Remove exit classes and slide in the new card
      container.classList.remove('slide-out-left', 'slide-out-right');
      container.classList.add('slide-in');

      setTimeout(() => {
        container.classList.remove('slide-in');
      }, 400);
    }, 300);
  }

  // Swipe gesture support for touchscreen navigation
  let touchStartX = 0;
  let touchEndX = 0;
  const container = document.getElementById('cardContainer');

  container.addEventListener('touchstart', e => {
    touchStartX = e.changedTouches[0].screenX;
  }, { passive: true });

  container.addEventListener('touchend', e => {
    touchEndX = e.changedTouches[0].screenX;
    handleSwipe();
  }, { passive: true });

  function handleSwipe() {
    const swipeThreshold = 50;
    const currentActive = document.querySelector('.view-section.active').id;
    const currentIndex = slideOrder.indexOf(currentActive);

    if (touchStartX - touchEndX > swipeThreshold) {
      // Swipe Left -> Next Slide
      if (currentIndex < slideOrder.length - 1) {
        goToSlide(slideOrder[currentIndex + 1], 'right');
      }
    } else if (touchEndX - touchStartX > swipeThreshold) {
      // Swipe Right -> Previous Slide
      if (currentIndex > 0) {
        goToSlide(slideOrder[currentIndex - 1], 'left');
      }
    }
  }

  // Toggle surprise note
  document.getElementById('surpriseBtn').addEventListener('click', () => {
    const note = document.getElementById('surprise');
    note.style.display = note.style.display === 'block' ? 'none' : 'block';
  });
</script>
</body>
</html>
