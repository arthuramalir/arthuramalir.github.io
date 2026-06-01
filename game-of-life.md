---
layout: page
title: Game of Life
permalink: /game-of-life/
---

<div id="gol-container" style="max-width: 800px; margin: 0 auto;">
  <div style="margin-bottom: 20px;">
    <button id="startBtn" style="padding: 8px 16px; margin-right: 10px; background: #59ACFF; color: white; border: none; border-radius: 4px; cursor: pointer;">▶ Start</button>
    <button id="pauseBtn" style="padding: 8px 16px; margin-right: 10px; background: #79B5F2; color: white; border: none; border-radius: 4px; cursor: pointer;">⏸ Pause</button>
    <button id="resetBtn" style="padding: 8px 16px; margin-right: 10px; background: #96BEE6; color: white; border: none; border-radius: 4px; cursor: pointer;">↻ Reset</button>
    <button id="randomBtn" style="padding: 8px 16px; background: #AEC3D9; color: #000; border: none; border-radius: 4px; cursor: pointer;">🎲 Random</button>
  </div>
  
  <div style="margin-bottom: 15px; font-size: 0.9rem; color: #96BEE6;">
    <strong>Generation:</strong> <span id="generation">0</span> | 
    <strong>Live Cells:</strong> <span id="cellCount">0</span> |
    <strong>Speed:</strong> 
    <input type="range" id="speedSlider" min="50" max="500" value="100" style="width: 100px; vertical-align: middle;">
  </div>
  
  <canvas id="gameCanvas" width="600" height="600" style="border: 2px solid #79B5F2; display: block; background: #000; image-rendering: pixelated; margin: 0 auto; max-width: 100%;"></canvas>
  
  <div style="margin-top: 20px; font-size: 0.85rem; color: #AEC3D9; line-height: 1.6;">
    <p><strong>Conway's Game of Life Rules:</strong></p>
    <ul style="list-style: none; padding-left: 0;">
      <li>✓ Any live cell with 2-3 live neighbors survives</li>
      <li>✓ Any dead cell with exactly 3 live neighbors becomes alive</li>
      <li>✓ All other cells die or stay dead (overpopulation/underpopulation)</li>
    </ul>
    <p style="margin-top: 15px; color: #79B5F2;">
      <em>Click on the canvas to toggle cells. Complex patterns emerge from simple rules—a fascinating analog to computational modeling.</em>
    </p>
  </div>
</div>

<script>
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

const CELL_SIZE = canvas.width / 100;
const GRID_WIDTH = Math.floor(canvas.width / CELL_SIZE);
const GRID_HEIGHT = Math.floor(canvas.height / CELL_SIZE);

let grid = Array(GRID_HEIGHT).fill(null).map(() => Array(GRID_WIDTH).fill(0));
let running = false;
let generation = 0;
let speed = 100;
let animationId = null;

// Initialize random grid
function randomizeGrid() {
  for (let y = 0; y < GRID_HEIGHT; y++) {
    for (let x = 0; x < GRID_WIDTH; x++) {
      grid[y][x] = Math.random() > 0.7 ? 1 : 0;
    }
  }
  generation = 0;
  draw();
  updateStats();
}

// Reset grid
function resetGrid() {
  grid = Array(GRID_HEIGHT).fill(null).map(() => Array(GRID_WIDTH).fill(0));
  running = false;
  generation = 0;
  draw();
  updateStats();
  if (animationId) cancelAnimationFrame(animationId);
  document.getElementById('startBtn').textContent = '▶ Start';
}

// Count live neighbors
function countNeighbors(x, y) {
  let count = 0;
  for (let dy = -1; dy <= 1; dy++) {
    for (let dx = -1; dx <= 1; dx++) {
      if (dx === 0 && dy === 0) continue;
      const ny = (y + dy + GRID_HEIGHT) % GRID_HEIGHT;
      const nx = (x + dx + GRID_WIDTH) % GRID_WIDTH;
      count += grid[ny][nx];
    }
  }
  return count;
}

// Update grid generation
function step() {
  const newGrid = Array(GRID_HEIGHT).fill(null).map(() => Array(GRID_WIDTH).fill(0));
  
  for (let y = 0; y < GRID_HEIGHT; y++) {
    for (let x = 0; x < GRID_WIDTH; x++) {
      const neighbors = countNeighbors(x, y);
      const alive = grid[y][x];
      
      if (alive && (neighbors === 2 || neighbors === 3)) {
        newGrid[y][x] = 1;
      } else if (!alive && neighbors === 3) {
        newGrid[y][x] = 1;
      }
    }
  }
  
  grid = newGrid;
  generation++;
  updateStats();
}

// Draw grid
function draw() {
  ctx.fillStyle = '#000';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  
  ctx.fillStyle = '#59ACFF';
  for (let y = 0; y < GRID_HEIGHT; y++) {
    for (let x = 0; x < GRID_WIDTH; x++) {
      if (grid[y][x]) {
        ctx.fillRect(x * CELL_SIZE, y * CELL_SIZE, CELL_SIZE - 1, CELL_SIZE - 1);
      }
    }
  }
}

// Update statistics
function updateStats() {
  document.getElementById('generation').textContent = generation;
  const count = grid.flat().reduce((a, b) => a + b, 0);
  document.getElementById('cellCount').textContent = count;
}

// Animation loop
function animate() {
  step();
  draw();
  animationId = setTimeout(animate, 501 - speed);
}

// Event listeners
document.getElementById('startBtn').addEventListener('click', () => {
  if (!running) {
    running = true;
    document.getElementById('startBtn').textContent = '⏸ Pause';
    animate();
  } else {
    running = false;
    document.getElementById('startBtn').textContent = '▶ Start';
    if (animationId) cancelAnimationFrame(animationId);
  }
});

document.getElementById('pauseBtn').addEventListener('click', () => {
  running = false;
  document.getElementById('startBtn').textContent = '▶ Start';
  if (animationId) cancelAnimationFrame(animationId);
});

document.getElementById('resetBtn').addEventListener('click', resetGrid);

document.getElementById('randomBtn').addEventListener('click', () => {
  randomizeGrid();
  running = false;
  document.getElementById('startBtn').textContent = '▶ Start';
  if (animationId) cancelAnimationFrame(animationId);
});

document.getElementById('speedSlider').addEventListener('input', (e) => {
  speed = parseInt(e.target.value);
});

// Click to toggle cells
canvas.addEventListener('click', (e) => {
  if (running) return;
  const rect = canvas.getBoundingClientRect();
  const x = Math.floor((e.clientX - rect.left) / CELL_SIZE);
  const y = Math.floor((e.clientY - rect.top) / CELL_SIZE);
  
  if (x >= 0 && x < GRID_WIDTH && y >= 0 && y < GRID_HEIGHT) {
    grid[y][x] = grid[y][x] ? 0 : 1;
    draw();
    updateStats();
  }
});

// Initialize
draw();
updateStats();
</script>
