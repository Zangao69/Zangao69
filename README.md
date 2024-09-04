🎵🎵🎵 "You Are My Sunshine...
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mini Mario Game</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #87CEEB; /* Cor do fundo para simular o céu */
        }
        canvas {
            display: block;
            margin: 0 auto;
            background: #8B4513; /* Cor do fundo para simular o chão */
        }
        #gameCanvas {
            border: 1px solid #000;
        }
    </style>
</head>
<body>
    <canvas id="gameCanvas"></canvas>
    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const canvasWidth = window.innerWidth;
        const canvasHeight = window.innerHeight;
        canvas.width = canvasWidth;
        canvas.height = canvasHeight;
        const mario = {
            x: canvasWidth / 2,
            y: canvasHeight - 150,
            width: 50,
            height: 50,
            speed: 5,
            dy: 0,
            gravity: 0.5,
            jumpPower: -10,
            jumping: false
        };
        // Load Mario's image
        const marioImage = new Image();
        marioImage.src = 'https://raw.githubusercontent.com/TheDudeThatCode/TheDudeThatCode/master/Assets/Mario_Gameplay.gif';
        function drawMario() {
            ctx.drawImage(marioImage, mario.x, mario.y, mario.width, mario.height);
        }
        function update() {
            if (keys[87] && !mario.jumping) { // W key for jump
                mario.dy = mario.jumpPower;
                mario.jumping = true;
            }
            mario.dy += mario.gravity;
            mario.y += mario.dy;
            if (mario.y + mario.height >= canvasHeight) {
                mario.y = canvasHeight - mario.height;
                mario.dy = 0;
                mario.jumping = false;
            }
            if (keys[65]) { // A key for move left
                mario.x -= mario.speed;
            }
            if (keys[68]) { // D key for move right
                mario.x += mario.speed;
            }
            // Keep Mario within the canvas
            if (mario.x < 0) mario.x = 0;
            if (mario.x + mario.width > canvasWidth) mario.x = canvasWidth - mario.width;
        }
        function render() {
            ctx.clearRect(0, 0, canvasWidth, canvasHeight);
            drawMario();
        }
        function gameLoop() {
            update();
            render();
            requestAnimationFrame(gameLoop);
        }
        const keys = {};
        window.addEventListener('keydown', (e) => {
            keys[e.keyCode] = true;
        });
        window.addEventListener('keyup', (e) => {
            keys[e.keyCode] = false;
        });
        marioImage.onload = () => {
            gameLoop();
        };
    </script>
</body>
</html>

<!---
Zangao69/Zangao69 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
