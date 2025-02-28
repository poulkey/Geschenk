<!DOCTYPE html> 
<html lang="de"> 
<head> 
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Geschwisterwochenende Einladung</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');
        body {
            font-family: 'Poppins', sans-serif;
            text-align: center;
            background: radial-gradient(circle, #ffe8c6, #ffd9a4, #ffc78c, #ffb366);
            background-size: cover;
            padding: 20px;
            color: #2c3e50;
            overflow-x: hidden;
            position: relative;
        }
        .balloons {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
        }
        .balloon {
            position: absolute;
            width: 50px;
            height: 70px;
            background: rgba(255, 140, 0, 0.2);
            border-radius: 50%;
            animation: floatUp 12s infinite ease-in-out;
        }
        @keyframes floatUp {
            0% { transform: translateY(100vh); opacity: 0.6; }
            100% { transform: translateY(-10vh); opacity: 0; }
        }
        .container {
            max-width: 600px;
            margin: auto;
            background: rgba(255, 255, 255, 0.95);
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            display: none;
        }
        h1 {
            color: #e67e22;
        }
        p {
            font-size: 18px;
        }
        .btn {
            display: inline-block;
            padding: 12px 24px;
            background: #e67e22;
            color: white;
            text-decoration: none;
            border-radius: 8px;
            margin-top: 20px;
            font-weight: 600;
            transition: background 0.3s ease;
            cursor: pointer;
            position: relative;
        }
        .btn:hover {
            background: #d35400;
        }
        .gift-box {
            width: 120px;
            height: 120px;
            background: #e67e22;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 16px;
            color: white;
            font-size: 28px;
            font-weight: bold;
            margin: auto;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
            animation: wobble 1s ease-in-out infinite alternate;
        }
        @keyframes wobble {
            0% { transform: rotate(-5deg); }
            100% { transform: rotate(5deg); }
        }
        .gift-box.explode {
            animation: explode 0.8s forwards;
        }
        @keyframes explode {
            0% { transform: scale(1) rotate(0); opacity: 1; }
            50% { transform: scale(1.4) rotate(15deg); }
            100% { transform: scale(2) rotate(0); opacity: 0; }
        }
        .heart {
            position: absolute;
            font-size: 24px;
            color: rgba(255, 0, 0, 0.7);
            animation: floatHearts 2s ease-in-out forwards;
        }
        @keyframes floatHearts {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(-50px); opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="balloons"></div>
    <div class="gift-box" onclick="explodeGift()">🎁</div>
    <div class="container" id="invitation">
        <h1>Ein unvergessliches Wochenende!</h1>
        <p>Du wirst mit uns ein wunderschönes Geschwisterwochenende feiern und eine großartige Zeit erleben.</p>
        <p><strong>Wann:</strong> 24. - 27. April</p>
        <p><strong>Wo:</strong> Hamburg</p>
        <p>Freu dich auf ein entspanntes und schönes Wochenende mit deinen wundervollen Geschwistern!</p>
        <a href="#" class="btn" onclick="sprayHearts(event); return false;">Ich bin dabei!</a>
    </div>
    <script>
        function createBalloons() {
            const container = document.querySelector('.balloons');
            for (let i = 0; i < 15; i++) {
                let balloon = document.createElement('div');
                balloon.classList.add('balloon');
                balloon.style.left = Math.random() * 100 + '%';
                balloon.style.animationDuration = (Math.random() * 5 + 7) + 's';
                container.appendChild(balloon);
            }
        }
        createBalloons();

        function explodeGift() {
            let giftBox = document.querySelector('.gift-box');
            giftBox.classList.add('explode');
            setTimeout(() => {
                giftBox.style.display = 'none';
                document.getElementById('invitation').style.display = 'block';
                document.body.style.overflow = 'auto';
            }, 800);
        }

        function sprayHearts(event) {
            for (let i = 0; i < 12; i++) {
                let heart = document.createElement('div');
                heart.classList.add('heart');
                heart.innerHTML = '❤️';
                document.body.appendChild(heart);
                
                let x = event.clientX + (Math.random() * 200 - 100);
                let y = event.clientY + (Math.random() * 200 - 100);
                heart.style.left = `${x}px`;
                heart.style.top = `${y}px`;
                
                setTimeout(() => heart.remove(), 2000);
            }
        }
    </script>
</body>
</html> 
