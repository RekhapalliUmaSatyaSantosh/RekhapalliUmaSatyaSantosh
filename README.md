<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>Rekhapalli Uma Satya Santosh | Python Full Stack Dev + Snake Game</title>
  <!-- Font Awesome Icons (optional but nice) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- Google Fonts: Fira Code -->
  <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: linear-gradient(145deg, #0a0f1e 0%, #0c1222 100%);
      font-family: 'Fira Code', 'Segoe UI', monospace;
      color: #eef5ff;
      padding: 2rem 1rem;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }

    /* main container */
    .profile-container {
      max-width: 1200px;
      width: 100%;
      background: rgba(18, 25, 45, 0.65);
      backdrop-filter: blur(2px);
      border-radius: 3rem;
      padding: 2rem 2rem 2.5rem;
      box-shadow: 0 25px 45px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(255, 255, 255, 0.05);
      transition: all 0.2s;
    }

    /* headings with gradient */
    h1 {
      font-size: 2.3rem;
      text-align: center;
      margin-bottom: 0.5rem;
      letter-spacing: -0.5px;
    }
    h1 span:first-child {
      background: linear-gradient(135deg, #ff5733, #ff9f4a);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    h1 span:last-child {
      background: linear-gradient(135deg, #9b9e9a, #d4d9ce);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    h3 {
      margin: 1.2rem 0 0.8rem 0;
      font-weight: 600;
      font-size: 1.6rem;
      border-left: 5px solid;
      padding-left: 15px;
    }

    .typing-wrapper {
      text-align: center;
      margin: 0.8rem 0 1rem;
    }

    /* about & contact */
    .about-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      gap: 1.5rem;
      background: rgba(0, 0, 0, 0.35);
      border-radius: 2rem;
      padding: 1.3rem 1.8rem;
      margin: 1rem 0;
    }
    .about-text {
      flex: 2;
    }
    .about-text p {
      margin: 0.6rem 0;
      font-size: 1rem;
      line-height: 1.5;
      display: flex;
      align-items: center;
      gap: 12px;
      flex-wrap: wrap;
    }
    .badge-icon {
      background: #1e2a3e;
      border-radius: 2rem;
      padding: 6px 12px;
      font-size: 0.85rem;
      font-weight: 500;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      color: #bbd9ff;
    }
    .btn-link {
      background: #ff5e6e20;
      border: 1px solid #ff7e5e;
      border-radius: 2rem;
      padding: 6px 16px;
      text-decoration: none;
      color: #ffb47b;
      font-weight: 500;
      transition: 0.2s;
    }
    .btn-link:hover {
      background: #ff5733;
      color: white;
      border-color: #ff5733;
    }

    /* tools icons */
    .tools-icons {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      align-items: center;
      margin: 0.5rem 0 1rem;
    }

    /* snake game section */
    .snake-section {
      margin: 2rem 0 1rem;
      background: rgba(0, 0, 0, 0.5);
      border-radius: 2rem;
      padding: 1.2rem;
      text-align: center;
      border: 1px solid rgba(255, 100, 100, 0.2);
      transition: 0.25s;
    }
    .snake-header {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      flex-wrap: wrap;
      gap: 12px;
      margin-bottom: 1rem;
      padding: 0 1rem;
    }
    .score-board {
      background: #0f172a;
      padding: 6px 20px;
      border-radius: 40px;
      font-weight: bold;
      font-size: 1.3rem;
      font-family: monospace;
      box-shadow: inset 0 0 4px #00000055, 0 4px 10px rgba(0,0,0,0.3);
    }
    .score-board span {
      color: #ffcc88;
      font-size: 1.8rem;
      margin-right: 8px;
    }
    .game-controls {
      display: flex;
      gap: 12px;
    }
    .game-btn {
      background: #1f2a3e;
      border: none;
      font-family: 'Fira Code', monospace;
      font-weight: bold;
      padding: 8px 16px;
      border-radius: 40px;
      color: #f0f3fa;
      cursor: pointer;
      transition: all 0.2s;
      font-size: 0.9rem;
      box-shadow: 0 2px 5px rgba(0,0,0,0.3);
    }
    .game-btn:hover {
      background: #ff5733;
      transform: scale(0.96);
      color: white;
    }
    canvas {
      background-color: #0a0f1f;
      border-radius: 28px;
      box-shadow: 0 20px 30px -10px black;
      display: block;
      margin: 0 auto;
      border: 3px solid #ff7e5e66;
      cursor: pointer;
    }
    .mobile-controls {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin-top: 18px;
      flex-wrap: wrap;
    }
    .arrow-btn {
      background: #1e2a3ecc;
      backdrop-filter: blur(8px);
      border: 1px solid #ffaa77;
      font-size: 1.8rem;
      width: 65px;
      padding: 12px 0;
      border-radius: 60px;
      font-weight: bold;
      color: #ffdd99;
      transition: 0.1s linear;
      cursor: pointer;
      user-select: none;
    }
    .arrow-btn:active {
      background: #ff5733;
      transform: scale(0.92);
    }
    .status-msg {
      margin-top: 12px;
      font-size: 0.9rem;
      font-weight: 500;
      background: #00000066;
      display: inline-block;
      padding: 4px 16px;
      border-radius: 20px;
    }

    /* footer stats */
    .stats-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 15px;
      margin-top: 2rem;
      padding-top: 1rem;
      border-top: 1px solid #2a3650;
    }
    hr {
      border-color: #2e3a55;
      margin: 0.5rem 0;
    }

    @media (max-width: 700px) {
      .profile-container {
        padding: 1rem;
      }
      canvas {
        width: 100%;
        height: auto;
      }
      .arrow-btn {
        width: 55px;
        font-size: 1.5rem;
      }
      h1 {
        font-size: 1.5rem;
      }
    }
  </style>
</head>
<body>
<div class="profile-container">
  <!-- HEADER -->
  <h1 align="center">
    <span>Hi 👋, I'm</span>
    <span> Rekhapalli Uma Satya Santosh</span>
  </h1>
  <div class="typing-wrapper">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&pause=1000&color=FF1493&center=true&vCenter=true&width=700&lines=A+Passionate+Python+Full+Stack+Developer+from+India" alt="Typing SVG" style="max-width:100%;" />
  </div>

  <!-- ABOUT + CONTACT -->
  <div class="about-grid">
    <div class="about-text">
      <p><i class="fas fa-seedling" style="color:#8bc34a;"></i> 🌱 Currently learning <strong>Python Full Stack Development</strong></p>
      <p><i class="fas fa-briefcase"></i> 👨‍💻 Portfolio: <a href="https://satyasantosh.lovable.app/" target="_blank" class="btn-link">satyasantosh.lovable.app</a></p>
      <p><i class="fas fa-comment"></i> 💬 Ask me about <strong>Python, SQL, HTML, CSS, JavaScript</strong></p>
      <p><i class="fas fa-envelope"></i> 📫 Email: <strong>santoshrekahapalli@gmail.com</strong></p>
      <p><i class="fas fa-file-alt"></i> 📄 Resume: <a href="https://drive.google.com/file/d/1yvYr79iVbUvSpiHsPY1MCjmtuLCS4m2n/view?usp=drivesdk" target="_blank" class="btn-link">Google Drive Resume</a></p>
    </div>
    <div class="connect-links">
      <h3 style="margin-top:0; border-left-color:#ff6600;">🌐 Connect</h3>
      <p align="left" style="display: flex; gap: 16px;">
        <a href="https://www.linkedin.com/in/uma-satya-santosh-rekhapalli/" target="_blank"><img src="https://skillicons.dev/icons?i=linkedin" width="48" /></a>
        <a href="https://www.hackerrank.com/profile/santoshrekahapa1" target="_blank"><img src="https://cdn.simpleicons.org/hackerrank/2EC866" width="48" height="48"/></a>
      </p>
    </div>
  </div>

  <!-- LANGUAGES & TOOLS -->
  <h3 style="color:#00cc99;">💻 Languages and Tools</h3>
  <div class="tools-icons">
    <img src="https://skillicons.dev/icons?i=python,html,css,js,mysql" />
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/oracle/oracle-original.svg" width="50" />
  </div>

  <!-- SNAKE GAME SECTION (PLAYABLE & ADDED) -->
  <div class="snake-section">
    <div class="snake-header">
      <div class="score-board"><span>🐍</span> SCORE: <span id="snakeScore">0</span></div>
      <div class="game-controls">
        <button class="game-btn" id="restartBtn"><i class="fas fa-redo-alt"></i> RESTART</button>
        <button class="game-btn" id="pauseBtn"><i class="fas fa-pause"></i> PAUSE</button>
      </div>
    </div>
    <canvas id="snakeCanvas" width="600" height="400" style="width:100%; height:auto; max-width:600px; aspect-ratio:600/400"></canvas>
    <div class="mobile-controls">
      <div class="arrow-btn" data-dir="UP">⬆️</div>
      <div class="arrow-btn" data-dir="LEFT">⬅️</div>
      <div class="arrow-btn" data-dir="DOWN">⬇️</div>
      <div class="arrow-btn" data-dir="RIGHT">➡️</div>
    </div>
    <div class="status-msg" id="gameStatusMsg">▶️ Use arrow keys or on-screen buttons</div>
  </div>

  <!-- STATS + VIEWS (GitHub like) -->
  <div class="stats-row">
    <p align="left">
      <img src="https://komarev.com/ghpvc/?username=rekhapalliumasatyasantosh&label=Profile%20Views&color=blueviolet&style=for-the-badge" alt="profile views" />
    </p>
    <p style="font-size: 0.8rem;">✨ Classic Snake · Eat red food · Avoid walls & yourself ✨</p>
  </div>
  
  <h3 align="center">🔥 GitHub Streak</h3>
  <p align="center">
    <img src="https://github-readme-streak-stats.herokuapp.com/?user=rekhapalliumasatyasantosh&theme=radical" alt="GitHub Streak" style="max-width:100%;" />
  </p>
  <hr />
  <p align="center"><small>🐍 Python Full Stack Developer — Keep coding & keep playing!</small></p>
</div>

<script>
  (function(){
    // ---------- SNAKE GAME ----------
    const canvas = document.getElementById('snakeCanvas');
    const ctx = canvas.getContext('2d');
    const scoreSpan = document.getElementById('snakeScore');
    const statusMsgDiv = document.getElementById('gameStatusMsg');

    // Game settings
    const GRID_SIZE = 20;      // 20x20 grid cells
    const CELL_SIZE = canvas.width / GRID_SIZE;  // 30px (600/20)
    
    let snake = [
      {x: 10, y: 10},
      {x: 9, y: 10},
      {x: 8, y: 10},
      {x: 7, y: 10}
    ];
    let direction = 'RIGHT';    // current moving direction
    let nextDirection = 'RIGHT';
    let food = {x: 15, y: 10};
    let score = 0;
    let gameLoop = null;
    let isGameRunning = true;
    let isPaused = false;
    let gameSpeed = 130;        // ms per frame

    // helper: generate random food avoiding snake
    function generateRandomFood() {
      const totalCells = GRID_SIZE * GRID_SIZE;
      if(snake.length >= totalCells) {
        // win condition
        if(gameLoop) clearInterval(gameLoop);
        gameLoop = null;
        isGameRunning = false;
        statusMsgDiv.innerText = "✨ YOU WIN! PERFECT! ✨ Click RESTART";
        return null;
      }
      const snakeSet = new Set(snake.map(seg => `${seg.x},${seg.y}`));
      let freeCells = [];
      for(let i=0; i<GRID_SIZE; i++) {
        for(let j=0; j<GRID_SIZE; j++) {
          if(!snakeSet.has(`${i},${j}`)) freeCells.push({x: i, y: j});
        }
      }
      if(freeCells.length === 0) return null;
      const rand = Math.floor(Math.random() * freeCells.length);
      return freeCells[rand];
    }

    // initial food (avoid snake)
    function initFood() {
      let newFood = generateRandomFood();
      if(newFood) food = newFood;
      else {
        // if somehow full, but game would end anyway
        food = {x: 5, y: 5};
      }
    }

    // game logic (move snake)
    function updateGame() {
      if(!isGameRunning || isPaused) return;
      
      // commit next valid direction
      direction = nextDirection;
      
      // compute new head
      let newHead = {...snake[0]};
      switch(direction) {
        case 'RIGHT': newHead.x += 1; break;
        case 'LEFT':  newHead.x -= 1; break;
        case 'UP':    newHead.y -= 1; break;
        case 'DOWN':  newHead.y += 1; break;
        default: break;
      }
      
      // check food collision
      const willEat = (newHead.x === food.x && newHead.y === food.y);
      
      // perform move
      if(willEat) {
        // add new head, keep tail (grow)
        snake = [newHead, ...snake];
        score++;
        scoreSpan.innerText = score;
        // generate new food
        const newFood = generateRandomFood();
        if(newFood === null) {
          // win case: board full
          if(gameLoop) clearInterval(gameLoop);
          gameLoop = null;
          isGameRunning = false;
          statusMsgDiv.innerText = "🎉 VICTORY! You filled the board! 🎉";
          drawCanvas();
          return;
        }
        food = newFood;
      } else {
        // normal move: insert new head, remove tail
        snake = [newHead, ...snake.slice(0, -1)];
      }
      
      // check collision with walls or self
      const head = snake[0];
      // wall collision
      if(head.x < 0 || head.x >= GRID_SIZE || head.y < 0 || head.y >= GRID_SIZE) {
        gameOver();
        return;
      }
      // self collision (skip first element)
      for(let i = 1; i < snake.length; i++) {
        if(snake[i].x === head.x && snake[i].y === head.y) {
          gameOver();
          return;
        }
      }
      
      drawCanvas();
    }
    
    function gameOver() {
      if(!isGameRunning) return;
      if(gameLoop) {
        clearInterval(gameLoop);
        gameLoop = null;
      }
      isGameRunning = false;
      statusMsgDiv.innerText = `💀 GAME OVER! Score: ${score} 💀 Press RESTART`;
      drawCanvas(); // draw final frame with "game over" overlay
    }
    
    function restartGame() {
      // reset variables
      snake = [
        {x: 10, y: 10},
        {x: 9, y: 10},
        {x: 8, y: 10},
        {x: 7, y: 10}
      ];
      direction = 'RIGHT';
      nextDirection = 'RIGHT';
      score = 0;
      scoreSpan.innerText = "0";
      isGameRunning = true;
      isPaused = false;
      statusMsgDiv.innerText = "▶️ Game running - use arrows / buttons";
      // generate safe food
      const snakeSet = new Set(snake.map(s => `${s.x},${s.y}`));
      let freeSpots = [];
      for(let i=0;i<GRID_SIZE;i++) for(let j=0;j<GRID_SIZE;j++) if(!snakeSet.has(`${i},${j}`)) freeSpots.push({x:i,y:j});
      if(freeSpots.length) food = freeSpots[Math.floor(Math.random()*freeSpots.length)];
      else food = {x: 5, y: 5};
      
      if(gameLoop) clearInterval(gameLoop);
      gameLoop = setInterval(() => updateGame(), gameSpeed);
      drawCanvas();
    }
    
    function togglePause() {
      if(!isGameRunning) return;
      isPaused = !isPaused;
      if(isPaused) {
        statusMsgDiv.innerText = "⏸️ PAUSED - press PAUSE or restart";
        if(gameLoop) clearInterval(gameLoop);
        gameLoop = null;
      } else {
        statusMsgDiv.innerText = "▶️ Game resumed";
        if(gameLoop) clearInterval(gameLoop);
        gameLoop = setInterval(() => updateGame(), gameSpeed);
      }
      drawCanvas();
    }
    
    // drawing function with decorations
    function drawCanvas() {
      if(!ctx) return;
      // background grid
      ctx.fillStyle = "#0a0f1f";
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      // grid lines
      ctx.strokeStyle = "#1f2b3f";
      ctx.lineWidth = 0.5;
      for(let i = 0; i <= GRID_SIZE; i++) {
        ctx.beginPath();
        ctx.moveTo(i * CELL_SIZE, 0);
        ctx.lineTo(i * CELL_SIZE, canvas.height);
        ctx.stroke();
        ctx.moveTo(0, i * CELL_SIZE);
        ctx.lineTo(canvas.width, i * CELL_SIZE);
        ctx.stroke();
      }
      // draw food
      ctx.shadowBlur = 0;
      ctx.fillStyle = "#ff4d4d";
      ctx.beginPath();
      ctx.arc(food.x * CELL_SIZE + CELL_SIZE/2, food.y * CELL_SIZE + CELL_SIZE/2, CELL_SIZE/2.4, 0, Math.PI*2);
      ctx.fill();
      ctx.fillStyle = "#ffaa66";
      ctx.beginPath();
      ctx.arc(food.x * CELL_SIZE + CELL_SIZE/2, food.y * CELL_SIZE + CELL_SIZE/2, CELL_SIZE/5, 0, Math.PI*2);
      ctx.fill();
      
      // draw snake
      for(let i=0; i<snake.length; i++) {
        const seg = snake[i];
        const grad = ctx.createLinearGradient(seg.x*CELL_SIZE, seg.y*CELL_SIZE, (seg.x+1)*CELL_SIZE, (seg.y+1)*CELL_SIZE);
        if(i===0) {
          grad.addColorStop(0, '#6eff8e');
          grad.addColorStop(1, '#2ecc71');
        } else {
          grad.addColorStop(0, '#44cc66');
          grad.addColorStop(1, '#239b56');
        }
        ctx.fillStyle = grad;
        ctx.fillRect(seg.x * CELL_SIZE + 1, seg.y * CELL_SIZE + 1, CELL_SIZE - 2, CELL_SIZE - 2);
        // eyes on head
        if(i===0) {
          ctx.fillStyle = "white";
          const eyeSize = CELL_SIZE/6;
          const eyeOff = CELL_SIZE/3;
          if(direction === 'RIGHT') {
            ctx.fillRect(seg.x*CELL_SIZE + CELL_SIZE - eyeOff, seg.y*CELL_SIZE + eyeOff, eyeSize, eyeSize);
            ctx.fillRect(seg.x*CELL_SIZE + CELL_SIZE - eyeOff, seg.y*CELL_SIZE + CELL_SIZE - eyeOff - eyeSize, eyeSize, eyeSize);
          } else if(direction === 'LEFT') {
            ctx.fillRect(seg.x*CELL_SIZE + eyeOff - eyeSize, seg.y*CELL_SIZE + eyeOff, eyeSize, eyeSize);
            ctx.fillRect(seg.x*CELL_SIZE + eyeOff - eyeSize, seg.y*CELL_SIZE + CELL_SIZE - eyeOff - eyeSize, eyeSize, eyeSize);
          } else if(direction === 'UP') {
            ctx.fillRect(seg.x*CELL_SIZE + eyeOff, seg.y*CELL_SIZE + eyeOff - eyeSize, eyeSize, eyeSize);
            ctx.fillRect(seg.x*CELL_SIZE + CELL_SIZE - eyeOff - eyeSize, seg.y*CELL_SIZE + eyeOff - eyeSize, eyeSize, eyeSize);
          } else {
            ctx.fillRect(seg.x*CELL_SIZE + eyeOff, seg.y*CELL_SIZE + CELL_SIZE - eyeOff, eyeSize, eyeSize);
            ctx.fillRect(seg.x*CELL_SIZE + CELL_SIZE - eyeOff - eyeSize, seg.y*CELL_SIZE + CELL_SIZE - eyeOff, eyeSize, eyeSize);
          }
          ctx.fillStyle = "#000";
          const pupil = eyeSize/1.6;
          if(direction === 'RIGHT') {
            ctx.fillRect(seg.x*CELL_SIZE + CELL_SIZE - eyeOff+2, seg.y*CELL_SIZE + eyeOff+2, pupil, pupil);
            ctx.fillRect(seg.x*CELL_SIZE + CELL_SIZE - eyeOff+2, seg.y*CELL_SIZE + CELL_SIZE - eyeOff - eyeSize+2, pupil, pupil);
          } else if(direction === 'LEFT') {
            ctx.fillRect(seg.x*CELL_SIZE + eyeOff - eyeSize+2, seg.y*CELL_SIZE + eyeOff+2, pupil, pupil);
            ctx.fillRect(seg.x*CELL_SIZE + eyeOff - eyeSize+2, seg.y*CELL_SIZE + CELL_SIZE - eyeOff - eyeSize+2, pupil, pupil);
          } else if(direction === 'UP') {
            ctx.fillRect(seg.x*CELL_SIZE + eyeOff+2, seg.y*CELL_SIZE + eyeOff - eyeSize+2, pupil, pupil);
            ctx.fillRect(seg.x*CELL_SIZE + CELL_SIZE - eyeOff - eyeSize+2, seg.y*CELL_SIZE + eyeOff - eyeSize+2, pupil, pupil);
          } else {
            ctx.fillRect(seg.x*CELL_SIZE + eyeOff+2, seg.y*CELL_SIZE + CELL_SIZE - eyeOff+2, pupil, pupil);
            ctx.fillRect(seg.x*CELL_SIZE + CELL_SIZE - eyeOff - eyeSize+2, seg.y*CELL_SIZE + CELL_SIZE - eyeOff+2, pupil, pupil);
          }
        }
      }
      
      // game over overlay
      if(!isGameRunning && !gameLoop && !isPaused) {
        ctx.fillStyle = "rgba(0,0,0,0.75)";
        ctx.fillRect(0,0,canvas.width, canvas.height);
        ctx.font = "bold 24px 'Fira Code'";
        ctx.fillStyle = "#ffaa88";
        ctx.shadowBlur = 0;
        ctx.fillText("GAME OVER", canvas.width/2-90, canvas.height/2);
        ctx.font = "16px monospace";
        ctx.fillStyle = "#ccc";
        ctx.fillText("click RESTART", canvas.width/2-65, canvas.height/2+40);
      } else if(isPaused && isGameRunning) {
        ctx.fillStyle = "rgba(0,0,0,0.6)";
        ctx.fillRect(0,0,canvas.width, canvas.height);
        ctx.font = "bold 20px 'Fira Code'";
        ctx.fillStyle = "#ffe0a3";
        ctx.fillText("⏸ PAUSED", canvas.width/2-55, canvas.height/2);
      }
      ctx.shadowBlur = 0;
    }
    
    // direction changes (prevent opposite)
    function setDirection(newDir) {
      if(!isGameRunning || isPaused) return;
      const opposite = {
        'UP': 'DOWN', 'DOWN': 'UP', 'LEFT': 'RIGHT', 'RIGHT': 'LEFT'
      };
      if(opposite[newDir] !== direction) {
        nextDirection = newDir;
      }
    }
    
    // keyboard controls
    function handleKey(e) {
      const key = e.key;
      e.preventDefault();
      if(key === 'ArrowUp') setDirection('UP');
      else if(key === 'ArrowDown') setDirection('DOWN');
      else if(key === 'ArrowLeft') setDirection('LEFT');
      else if(key === 'ArrowRight') setDirection('RIGHT');
      else if(key === ' ' || key === 'Space') {
        e.preventDefault();
        if(isGameRunning) togglePause();
      }
    }
    
    // event binding
    window.addEventListener('keydown', (e) => {
      if(e.key.startsWith('Arrow') || e.key === ' ' || e.key === 'Space') {
        e.preventDefault();
        handleKey(e);
      }
    });
    
    // mobile buttons
    document.querySelectorAll('.arrow-btn').forEach(btn => {
      btn.addEventListener('click', (e) => {
        const dir = btn.getAttribute('data-dir');
        if(dir === 'UP') setDirection('UP');
        else if(dir === 'LEFT') setDirection('LEFT');
        else if(dir === 'DOWN') setDirection('DOWN');
        else if(dir === 'RIGHT') setDirection('RIGHT');
      });
    });
    
    document.getElementById('restartBtn').addEventListener('click', () => {
      restartGame();
    });
    document.getElementById('pauseBtn').addEventListener('click', () => {
      if(isGameRunning) togglePause();
      else if(!isGameRunning) restartGame();
    });
    
    // initial start
    initFood();
    gameLoop = setInterval(() => updateGame(), gameSpeed);
    drawCanvas();
    // ensure canvas redraws also if needed
  })();
</script>
</body>
</html>
