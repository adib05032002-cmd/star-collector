
<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>لعبة جمع النجوم</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #eaf4ff;
      color: #203050;
    }
    canvas {
      background: white;
      border: 3px solid royalblue;
      border-radius: 12px;
      max-width: 95%;
    }
  </style>
</head>
<body>
  <h1>⭐ اجمع النجوم</h1>
  <p>حرّك المربع بالأسهم واجمع النجوم!</p>
  <p>النقاط: <span id="score">0</span></p>
  <canvas id="game" width="400" height="400"></canvas>

  <script>
    const canvas = document.getElementById("game");
    const ctx = canvas.getContext("2d");
    const scoreText = document.getElementById("score");

    const player = { x: 20, y: 20, size: 25 };
    const star = { x: 200, y: 200 };
    let score = 0;

    function draw() {
      ctx.clearRect(0, 0, 400, 400);
      ctx.fillStyle = "blue";
      ctx.fillRect(player.x, player.y, 25, 25);
      ctx.font = "25px Arial";
      ctx.fillText("⭐", star.x, star.y + 10);
    }

    document.addEventListener("keydown", function(e) {
      if (e.key === "ArrowUp") player.y -= 10;
      if (e.key === "ArrowDown") player.y += 10;
      if (e.key === "ArrowLeft") player.x -= 10;
      if (e.key === "ArrowRight") player.x += 10;

      player.x = Math.max(0, Math.min(375, player.x));
      player.y = Math.max(0, Math.min(375, player.y));

      if (Math.abs(player.x - star.x) < 25 &&
          Math.abs(player.y - star.y) < 25) {
        score++;
        scoreText.textContent = score;
        star.x = Math.random() * 340 + 20;
        star.y = Math.random() * 340 + 20;
      }

      draw();
    });

    draw();
  </script>
</body>
</html>
