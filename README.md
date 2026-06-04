<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>Rekhapalli Uma Satya Santosh | Python Full Stack Dev + Snake Game</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
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

    .profile-container {
      max-width: 1200px;
      width: 100%;
      background: rgba(18, 25, 45, 0.65);
      backdrop-filter: blur(2px);
      border-radius: 3rem;
      padding: 2rem 2rem 2.5rem;
      box-shadow: 0 25px 45px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(255, 255, 255, 0.05);
    }

    h1 {
      font-size: 2.3rem;
      text-align: center;
      margin-bottom: 0.5rem;
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
    .btn-link {
      background: #ff5e6e20;
      border: 1px solid #ff7e5e;
      border-radius: 2rem;
      padding: 6px 16px;
      text-decoration: none;
      color: #ffb47b;
      font-weight: 500;
      transition: 0.2s;
      display: inline-block;
    }
    .btn-link:hover {
      background: #ff5733;
      color: white;
      border-color: #ff5733;
    }

    .tools-icons {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      align-items: center;
      margin: 0.5rem 0 1rem;
    }

    .snake-section {
      margin: 2rem 0 1rem;
      background: rgba(0, 0, 0, 0.5);
      border-radius: 2rem;
      padding: 1.2rem;
      text-align: center;
      border: 1px solid rgba(255, 100, 100, 0.2);
    }
    .snake-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
      margin-bottom: 1rem;
      padding: 0 1rem;
    }
    .score-board {
      background: #0f172a;
      padding: 8px 24px;
      border-radius: 40px;
      font-weight: bold;
      font-size: 1.3rem;
      font-family: monospace;
    }
    .score-board span:first-child {
      color: #ffcc88;
      font-size: 1.5rem;
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
      padding: 8px 20px;
      border-radius: 40px;
      color: #f0f3fa;
      cursor: pointer;
      transition: all 0.2s;
      font-size: 0.9rem;
    }
    .game-btn:hover {
      background: #ff5733;
      transform: scale(0.96);
    }
    canvas {
      background-color: #0a0f1f;
      border-radius: 20px;
      box-shadow: 0 10px 30px -5px black;
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
      cursor: pointer;
      user-select: none;
      transition: 0.05s linear;
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
      padding: 4px 20px;
      border-radius: 20px;
    }
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
  <h1 align="center">
    <span>Hi 👋, I'm</span>
    <span> Rekhapalli Uma Satya Santosh</span>
  </h1>
  <div class="typing-wrapper">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&pause=1000&color=FF1493&center=true&vCenter=true&width=700&lines=A+Passionate+Python+Full+Stack+Developer+from+India" alt="Typing SVG" style="max-width:100%;" />
  </div>

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

  <h3 style="color:#00cc99;">💻 Languages and Tools</h3>
  <div class="tools-icons">
    <img src="https://skillicons.dev/icons?i=python,html,css,js,mysql" />
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/oracle/oracle-original.svg" width="50" />
  </div>

  <!-- SNAKE GAME SECTION - WORKING VERSION -->
  <div class="snake-section">
    <div class="snake-header">
      <div class="score-board"><span>🐍</span> SCORE: <span id="snakeScore">0</span></div>
      <div class="game-controls">
        <button class="game-btn" id="restartBtn"><i class="fas fa-redo-alt"></i> RESTART</button>
        <button class="game-btn" id="pauseBtn"><i class="fas fa-pause"></i> PAUSE</button>
      </div>
    </div>
    <canvas id="snakeCanvas" width="500" height="500" style="width:100%; height:auto; max-width:500px; aspect-ratio:1/1"></canvas>
    <div class="mobile-controls">
      <div class="arrow-btn" data-dir="UP">⬆️</div>
      <div class="arrow-btn" data-dir="LEFT">⬅️</div>
      <div class="arrow-btn" data-dir="DOWN">⬇️</div>
      <div class="arrow-btn" data-dir="RIGHT">➡️</div>
    </div>
    <div class="status-msg" id="gameStatusMsg">🎮 Use arrow keys or buttons to play!</div>
  </div>

  <div class="stats-row">
    <p align="left">
      <img src="https://komarev.com/ghpvc/?username=rekhapalliumasatyasantosh&label=Profile%20Views&color=blueviolet&style=for-the-badge" alt="profile views" />
    </p>
    <p style="font-size: 0.8rem;">✨ Classic Snake Game · Eat red apples · Avoid walls & yourself ✨</p>
  </div>
  
  <h3 align="center">🔥 GitHub Streak</h3>
  <p align="center">
    <img src="https://github-readme-streak-stats.herokuapp.com/?user=rekhapalliumasatyasantosh&theme=radical" alt="GitHub Streak" style="max-width:100%;" />
  </p>
  <hr />
  <p align="center"><small>🐍 Python Full Stack Developer — Keep coding & keep playing!</small></p>
</div>

<script>
(function() {
  // Get canvas element
  const canvas = document.getElementById('snakeCanvas');
  const ctx = canvas.getContext('2d');
  const scoreSpan = document.getElementById('snakeScore');
  const statusMsg = document.getElementById('gameStatusMsg');
  
  // Game settings
  const GRID_SIZE = 20; // 20x20 grid
  const CELL_SIZE = canvas.width / GRID_SIZE; // 25px
  
  // Snake initial position
  let snake = [
    {x: 10, y: 10},
    {x: 9, y: 10},
    {x: 8, y: 10},
    {x: 7, y: 10}
  ];
  
  let direction = 'RIGHT';
  let nextDirection = 'RIGHT';
  let food = {x: 15, y: 10};
  let score = 0;
  let gameInterval = null;
  let isGameRunning = true;
  let isPaused = false;
  let gameSpeed = 120; // milliseconds per frame
  
  // Generate random food not on snake
  function generateRandomFood() {
    const maxAttempts = 1000;
    for(let i = 0; i < maxAttempts; i++) {
      const randomX = Math.floor(Math.random() * GRID_SIZE);
      const randomY = Math.floor(Math.random() * GRID_SIZE);
      let isOnSnake = false;
      for(let segment of snake) {
        if(segment.x === randomX && segment.y === randomY) {
          isOnSnake = true;
          break;
        }
      }
      if(!isOnSnake) {
        return {x: randomX, y: randomY};
      }
    }
    // If snake is almost full, find empty cell
    for(let i = 0; i < GRID_SIZE; i++) {
      for(let j = 0; j < GRID_SIZE; j++) {
        let isOnSnake = false;
        for(let segment of snake) {
          if(segment.x === i && segment.y === j) {
            isOnSnake = true;
            break;
          }
        }
        if(!isOnSnake) {
          return {x: i, y: j};
        }
      }
    }
    return null; // Game win - board full
  }
  
  // Draw everything
  function draw() {
    // Clear canvas
    ctx.fillStyle = '#0a0f1f';
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    
    // Draw grid
    ctx.strokeStyle = '#1f2b3f';
    ctx.lineWidth = 0.5;
    for(let i = 0; i <= GRID_SIZE; i++) {
      ctx.beginPath();
      ctx.moveTo(i * CELL_SIZE, 0);
      ctx.lineTo(i * CELL_SIZE, canvas.height);
      ctx.stroke();
      ctx.beginPath();
      ctx.moveTo(0, i * CELL_SIZE);
      ctx.lineTo(canvas.width, i * CELL_SIZE);
      ctx.stroke();
    }
    
    // Draw food (apple)
    ctx.fillStyle = '#ff4444';
    ctx.shadowBlur = 8;
    ctx.shadowColor = '#ff0000';
    ctx.beginPath();
    ctx.arc(food.x * CELL_SIZE + CELL_SIZE/2, food.y * CELL_SIZE + CELL_SIZE/2, CELL_SIZE/2 - 2, 0, Math.PI * 2);
    ctx.fill();
    ctx.fillStyle = '#ffffff';
    ctx.beginPath();
    ctx.arc(food.x * CELL_SIZE + CELL_SIZE/2 - 3, food.y * CELL_SIZE + CELL_SIZE/2 - 3, 3, 0, Math.PI * 2);
    ctx.fill();
    ctx.fillStyle = '#228b22';
    ctx.fillRect(food.x * CELL_SIZE + CELL_SIZE/2 - 2, food.y * CELL_SIZE - 2, 4, 6);
    
    // Draw snake
    for(let i = 0; i < snake.length; i++) {
      const seg = snake[i];
      const gradient = ctx.createLinearGradient(
        seg.x * CELL_SIZE, seg.y * CELL_SIZE,
        seg.x * CELL_SIZE + CELL_SIZE, seg.y * CELL_SIZE + CELL_SIZE
      );
      if(i === 0) {
        gradient.addColorStop(0, '#5aff8e');
        gradient.addColorStop(1, '#2ecc71');
      } else {
        gradient.addColorStop(0, '#3cb371');
        gradient.addColorStop(1, '#228b22');
      }
      ctx.fillStyle = gradient;
      ctx.fillRect(seg.x * CELL_SIZE + 1, seg.y * CELL_SIZE + 1, CELL_SIZE - 2, CELL_SIZE - 2);
      
      // Draw eyes on head
      if(i === 0) {
        ctx.fillStyle = '#ffffff';
        const eyeSize = CELL_SIZE / 6;
        const eyeOffset = CELL_SIZE / 3;
        if(direction === 'RIGHT') {
          ctx.fillRect(seg.x * CELL_SIZE + CELL_SIZE - eyeOffset, seg.y * CELL_SIZE + eyeOffset, eyeSize, eyeSize);
          ctx.fillRect(seg.x * CELL_SIZE + CELL_SIZE - eyeOffset, seg.y * CELL_SIZE + CELL_SIZE - eyeOffset - eyeSize, eyeSize, eyeSize);
          ctx.fillStyle = '#000000';
          ctx.fillRect(seg.x * CELL_SIZE + CELL_SIZE - eyeOffset + 2, seg.y * CELL_SIZE + eyeOffset + 2, eyeSize/1.5, eyeSize/1.5);
          ctx.fillRect(seg.x * CELL_SIZE + CELL_SIZE - eyeOffset + 2, seg.y * CELL_SIZE + CELL_SIZE - eyeOffset - eyeSize + 2, eyeSize/1.5, eyeSize/1.5);
        } else if(direction === 'LEFT') {
          ctx.fillRect(seg.x * CELL_SIZE + eyeOffset - eyeSize, seg.y * CELL_SIZE + eyeOffset, eyeSize, eyeSize);
          ctx.fillRect(seg.x * CELL_SIZE + eyeOffset - eyeSize, seg.y * CELL_SIZE + CELL_SIZE - eyeOffset - eyeSize, eyeSize, eyeSize);
          ctx.fillStyle = '#000000';
          ctx.fillRect(seg.x * CELL_SIZE + eyeOffset - eyeSize + 2, seg.y * CELL_SIZE + eyeOffset + 2, eyeSize/1.5, eyeSize/1.5);
          ctx.fillRect(seg.x * CELL_SIZE + eyeOffset - eyeSize + 2, seg.y * CELL_SIZE + CELL_SIZE - eyeOffset - eyeSize + 2, eyeSize/1.5, eyeSize/1.5);
        } else if(direction === 'UP') {
          ctx.fillRect(seg.x * CELL_SIZE + eyeOffset, seg.y * CELL_SIZE + eyeOffset - eyeSize, eyeSize, eyeSize);
          ctx.fillRect(seg.x * CELL_SIZE + CELL_SIZE - eyeOffset - eyeSize, seg.y * CELL_SIZE + eyeOffset - eyeSize, eyeSize, eyeSize);
          ctx.fillStyle = '#000000';
          ctx.fillRect(seg.x * CELL_SIZE + eyeOffset + 2, seg.y * CELL_SIZE + eyeOffset - eyeSize + 2, eyeSize/1.5, eyeSize/1.5);
          ctx.fillRect(seg.x * CELL_SIZE + CELL_SIZE - eyeOffset - eyeSize + 2, seg.y * CELL_SIZE + eyeOffset - eyeSize + 2, eyeSize/1.5, eyeSize/1.5);
        } else {
          ctx.fillRect(seg.x * CELL_SIZE + eyeOffset, seg.y * CELL_SIZE + CELL_SIZE - eyeOffset, eyeSize, eyeSize);
          ctx.fillRect(seg.x * CELL_SIZE + CELL_SIZE - eyeOffset - eyeSize, seg.y * CELL_SIZE + CELL_SIZE - eyeOffset, eyeSize, eyeSize);
          ctx.fillStyle = '#000000';
          ctx.fillRect(seg.x * CELL_SIZE + eyeOffset + 2, seg.y * CELL_SIZE + CELL_SIZE - eyeOffset + 2, eyeSize/1.5, eyeSize/1.5);
          ctx.fillRect(seg.x * CELL_SIZE + CELL_SIZE - eyeOffset - eyeSize + 2, seg.y * CELL_SIZE + CELL_SIZE - eyeOffset + 2, eyeSize/1.5, eyeSize/1.5);
        }
      }
    }
    ctx.shadowBlur = 0;
    
    // Draw game over or pause message
    if(!isGameRunning) {
      ctx.fillStyle = 'rgba(0, 0, 0, 0.8)';
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      ctx.font = 'bold 24px "Fira Code"';
      ctx.fillStyle = '#ff8888';
      ctx.textAlign = 'center';
      ctx.fillText('GAME OVER', canvas.width/2, canvas.height/2 - 20);
      ctx.font = '16px "Fira Code"';
      ctx.fillStyle = '#cccccc';
      ctx.fillText('Click RESTART to play again', canvas.width/2, canvas.height/2 + 30);
      ctx.textAlign = 'left';
    } else if(isPaused) {
      ctx.fillStyle = 'rgba(0, 0, 0, 0.7)';
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      ctx.font = 'bold 24px "Fira Code"';
      ctx.fillStyle = '#ffcc88';
      ctx.textAlign = 'center';
      ctx.fillText('PAUSED', canvas.width/2, canvas.height/2);
      ctx.textAlign = 'left';
    }
  }
  
  // Update game logic
  function update() {
    if(!isGameRunning || isPaused) return;
    
    // Apply direction
    direction = nextDirection;
    
    // Calculate new head position
    let newHead = {x: snake[0].x, y: snake[0].y};
    switch(direction) {
      case 'RIGHT': newHead.x++; break;
      case 'LEFT': newHead.x--; break;
      case 'UP': newHead.y--; break;
      case 'DOWN': newHead.y++; break;
    }
    
    // Check if food is eaten
    const willEat = (newHead.x === food.x && newHead.y === food.y);
    
    if(willEat) {
      // Add new head and keep tail (snake grows)
      snake = [newHead, ...snake];
      score++;
      scoreSpan.textContent = score;
      
      // Generate new food
      const newFood = generateRandomFood();
      if(newFood === null) {
        // Win condition - board is full
        if(gameInterval) clearInterval(gameInterval);
        isGameRunning = false;
        statusMsg.textContent = '🎉 VICTORY! You filled the board! 🎉';
        draw();
        return;
      }
      food = newFood;
    } else {
      // Normal move: add new head, remove tail
      snake = [newHead, ...snake.slice(0, -1)];
    }
    
    // Check collisions
    const head = snake[0];
    
    // Wall collision
    if(head.x < 0 || head.x >= GRID_SIZE || head.y < 0 || head.y >= GRID_SIZE) {
      gameOver();
      return;
    }
    
    // Self collision
    for(let i = 1; i < snake.length; i++) {
      if(snake[i].x === head.x && snake[i].y === head.y) {
        gameOver();
        return;
      }
    }
    
    // Redraw
    draw();
  }
  
  function gameOver() {
    if(!isGameRunning) return;
    if(gameInterval) {
      clearInterval(gameInterval);
      gameInterval = null;
    }
    isGameRunning = false;
    statusMsg.textContent = `💀 GAME OVER! Final score: ${score} 💀`;
    draw();
  }
  
  function restart() {
    // Reset snake
    snake = [
      {x: 10, y: 10},
      {x: 9, y: 10},
      {x: 8, y: 10},
      {x: 7, y: 10}
    ];
    direction = 'RIGHT';
    nextDirection = 'RIGHT';
    score = 0;
    scoreSpan.textContent = '0';
    isGameRunning = true;
    isPaused = false;
    statusMsg.textContent = '🎮 Game running! Use arrow keys';
    
    // Generate valid food
    const newFood = generateRandomFood();
    if(newFood) food = newFood;
    else food = {x: 15, y: 10};
    
    // Clear old interval and start new
    if(gameInterval) clearInterval(gameInterval);
    gameInterval = setInterval(() => update(), gameSpeed);
    draw();
  }
  
  function togglePause() {
    if(!isGameRunning) return;
    isPaused = !isPaused;
    if(isPaused) {
      statusMsg.textContent = '⏸️ PAUSED - Press PAUSE to resume';
      if(gameInterval) {
        clearInterval(gameInterval);
        gameInterval = null;
      }
    } else {
      statusMsg.textContent = '▶️ Game resumed';
      if(gameInterval) clearInterval(gameInterval);
      gameInterval = setInterval(() => update(), gameSpeed);
    }
    draw();
  }
  
  function changeDirection(newDir) {
    if(!isGameRunning || isPaused) return;
    const opposite = {
      'UP': 'DOWN', 'DOWN': 'UP', 'LEFT': 'RIGHT', 'RIGHT': 'LEFT'
    };
    if(opposite[newDir] !== direction) {
      nextDirection = newDir;
    }
  }
  
  // Keyboard controls
  document.addEventListener('keydown', (e) => {
    const key = e.key;
    if(key === 'ArrowUp') {
      e.preventDefault();
      changeDirection('UP');
    } else if(key === 'ArrowDown') {
      e.preventDefault();
      changeDirection('DOWN');
    } else if(key === 'ArrowLeft') {
      e.preventDefault();
      changeDirection('LEFT');
    } else if(key === 'ArrowRight') {
      e.preventDefault();
      changeDirection('RIGHT');
    } else if(key === ' ' || key === 'Space') {
      e.preventDefault();
      if(isGameRunning) togglePause();
    }
  });
  
  // Mobile buttons
  document.querySelectorAll('.arrow-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      const dir = btn.getAttribute('data-dir');
      changeDirection(dir);
    });
  });
  
  // Restart and pause buttons
  document.getElementById('restartBtn').addEventListener('click', restart);
  document.getElementById('pauseBtn').addEventListener('click', () => {
    if(isGameRunning) togglePause();
    else if(!isGameRunning) restart();
  });
  
  // Start the game
  restart();
})();
</script>
</body>
</html>
