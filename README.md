# Happy 20th birthday
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Birthday Surprise!</title>
    <style>
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background: #2e0854;
            font-family: 'Arial Rounded MT Bold', sans-serif;
        }

        /* Glittery Purple Shine Background */
        #glitterCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            background: radial-gradient(circle at center, #5d0c91, #2e0854, #1a052e);
        }

        .content-card {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 100;
            background: rgba(255, 255, 255, 0.12);
            backdrop-filter: blur(20px);
            padding: 45px;
            border-radius: 35px;
            border: 2px solid rgba(255, 255, 255, 0.3);
            text-align: center;
            color: white;
            box-shadow: 0 0 40px rgba(0, 0, 0, 0.6);
            width: 85%;
            max-width: 480px;
        }

        h1 { font-size: 2.5rem; text-shadow: 0 0 15px #ff00ff; }
        
        .btn {
            padding: 15px 35px;
            font-size: 1.2rem;
            margin: 10px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
        }

        .btn-yes { background: #ff4d6d; color: white; box-shadow: 0 0 15px #ff4d6d; }
        .btn-no { background: #6c757d; color: white; }
        .btn-enjoy { background: #ffd700; color: #333; margin-top: 20px; }
        
        .btn:hover { transform: scale(1.1); filter: brightness(1.2); }

        /* Celebration Elements */
        .celebration-item {
            position: absolute;
            top: -100px;
            z-index: 50;
            pointer-events: none;
            animation: fallDown linear forwards;
        }

        @keyframes fallDown {
            0% { transform: translateY(0) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            100% { transform: translateY(110vh) rotate(360deg); opacity: 0.8; }
        }

        .hidden { display: none; }
        .footer { margin-top: 35px; font-size: 1.3rem; color: #ffb3c1; }
        .glow { text-shadow: 0 0 10px #fff, 0 0 20px #ff00ff; }
    </style>
</head>
<body>

    <canvas id="glitterCanvas"></canvas>

    <div class="content-card">
        <div id="page1">
            <h1 class="glow">siblings forever????</h1>
            <button class="btn btn-yes" onclick="showBday()">Yes!</button>
            <button class="btn btn-no" onclick="showPls()">No</button>
            <p id="plsText" style="color: #ffd700; font-size: 1.5rem; margin-top: 20px; font-weight: bold;"></p>
        </div>

        <div id="page2" class="hidden">
            <h1 style="color: #ffd700;">happiest 20th birthday myyy darling sister💐💕</h1>
            
            <div id="enjoyWrap">
                <button class="btn btn-enjoy" onclick="enjoyed()">are you enjoying this?</button>
            </div>
            
            <h2 id="meToo" class="hidden glow" style="color: #00f2ff; font-size: 2rem; margin-top: 20px;">me toooo sis🥳</h2>

            <div class="footer">
                with immense love from <br>
                <strong>Akash and Tiya 💖💐💕</strong>
            </div>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('glitterCanvas');
        const ctx = canvas.getContext('2d');
        let glitters = [];

        function init() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            glitters = [];
            for (let i = 0; i < 100; i++) {
                glitters.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 2 + 1,
                    speed: Math.random() * 0.5 + 0.1,
                    alpha: Math.random()
                });
            }
        }

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            glitters.forEach(g => {
                ctx.fillStyle = `rgba(255, 255, 255, ${Math.sin(Date.now() * 0.002 + g.alpha * 10)})`;
                ctx.beginPath();
                ctx.arc(g.x, g.y, g.size, 0, Math.PI * 2);
                ctx.fill();
                g.y += g.speed;
                if(g.y > canvas.height) g.y = -5;
            });
            requestAnimationFrame(draw);
        }

        function createItem() {
            const types = ['🎈', '🎊', '💖', '❤️', '🎈', '🎊'];
            const item = document.createElement('div');
            item.className = 'celebration-item';
            item.innerText = types[Math.floor(Math.random() * types.length)];
            
            item.style.left = Math.random() * 100 + 'vw';
            
            let fontSize = Math.random() * 20 + 20;
            if(item.innerText === '🎈') fontSize += 15;
            item.style.fontSize = fontSize + 'px';
            
            const duration = Math.random() * 3 + 4;
            item.style.animationDuration = duration + 's';
            
            document.body.appendChild(item);
            setTimeout(() => item.remove(), duration * 1000);
        }

        // High frequency for a rich "confetti and balloons" feel
        setInterval(createItem, 120);

        function showPls() {
            document.getElementById('plsText').innerText = "prweeeeety pls💖";
        }

        function showBday() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
        }

        function enjoyed() {
            document.getElementById('enjoyWrap').classList.add('hidden');
            document.getElementById('meToo').classList.remove('hidden');
        }

        window.addEventListener('resize', init);
        init();
        draw();
    </script>
</body>
</html>

               
            
