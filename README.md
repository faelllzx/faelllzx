// Get the canvas element
var canvas = document.getElementById('canvas');
var ctx = canvas.getContext('2d');

// Set the canvas dimensions
canvas.width = 400;
canvas.height = 400;

// Set the player properties
var player = {
  x: 200,
  y: 200,
  width: 20,
  height: 20,
  speed: 5
};

// Set the block properties
var block = {
  x: Math.random() * (canvas.width - 20),
  y: 0,
  width: 20,
  height: 20,
  speed: 2
};

// Draw the player and block
function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.fillStyle = 'blue';
  ctx.fillRect(player.x, player.y, player.width, player.height);
  ctx.fillStyle = 'ed';
  ctx.fillRect(block.x, block.y, block.width, block.height);
}

// Update the game state
function update() {
  block.y += block.speed;
  if (block.y > canvas.height) {
    block.x = Math.random() * (canvas.width - 20);
    block.y = 0;
  }
}

// Handle keyboard input
document.addEventListener('keydown', function(event) {
  switch (event.key) {
    case 'ArrowUp':
      player.y -= player.speed;
      break;
    case 'ArrowDown':
      player.y += player.speed;
      break;
    case 'ArrowLeft':
      player.x -= player.speed;
      break;
    case 'ArrowRight':
      player.x += player.speed;
      break;
  }
});

// Game loop
setInterval(function() {
  update();
  draw();
}, 1000 / 60);
