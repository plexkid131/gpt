<!DOCTYPE html>
<html>
<head>
    <title>Dino Game</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: #f7f7f7;
        }
        #game {
            border: 2px solid #000;
            width: 600px;
            height: 200px;
            position: relative;
            background: #fff;
        }
        #dino {
            width: 40px;
            height: 40px;
            background: #000;
            position: absolute;
            bottom: 0;
            left: 50px;
        }
        #obstacle {
            width: 20px;
            height: 40px;
            background: #f00;
            position: absolute;
            right: 0;
            bottom: 0;
        }
    </style>
</head>
<body>
    <div id="game">
        <div id="dino"></div>
        <div id="obstacle"></div>
    </div>
    <script>
        document.addEventListener('keydown', function(event) {
            if (event.code === 'Space') {
                jump();
            }
        });

        function jump() {
            let dino = document.getElementById('dino');
            if (dino.classList != 'jump') {
                dino.classList.add('jump');
                setTimeout(function() {
                    dino.classList.remove('jump');
                }, 300);
            }
        }

        let isAlive = setInterval(function() {
            let dino = document.getElementById('dino');
            let obstacle = document.getElementById('obstacle');

            let dinoTop = parseInt(window.getComputedStyle(dino).getPropertyValue('top'));
            let obstacleLeft = parseInt(window.getComputedStyle(obstacle).getPropertyValue('left'));

            if (obstacleLeft < 50 && obstacleLeft > 0 && dinoTop >= 160) {
                alert('Game Over!');
            }
        }, 10);
    </script>
</body>
</html>
