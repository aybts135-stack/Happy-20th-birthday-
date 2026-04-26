            #Happiest 20th birthday 
            <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happiest Birthday!</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body, html {
            width: 100%;
            height: 100%;
            background-color: #1a052e;
            font-family: 'Segoe UI', Roboto, sans-serif;
            color: #ffffff;
            overflow: hidden;
        }

        /* Twinkling Sparkling Background */
        #starCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            background: radial-gradient(circle at center, #3d0a6b 0%, #1a052e 100%);
        }

        .wrapper {
            position: relative;
            z-index: 100;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            padding: 20px;
        }

        /* Glass Card */
        .glass-card {
            background: rgba(255, 255, 255, 0.07);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            border-radius: 20px;
            padding: 40px 25px;
            width: 100%;
            max-width: 420px;
            text-align: center;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.4);
            animation: slideUp 0.8s ease-out;
        }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .highlight-gold {
            color: #ffd700;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 2px;
            display: block;
            margin-bottom: 15px;
        }

        h1 { font-size: 1.8rem; font-weight: 400; margin-bottom: 25px; line-height: 1.3; }

        /* Buttons */
        button {
            background: rgba(255, 255, 255, 0.1);
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.3);
            padding: 10px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            transition: 0.3s;
            margin: 5px;
        }

        button:hover { background: white; color: #1a052e; }

        /* Celebration Elements */
        .pop-item {
            position: absolute;
            top: -50px;
            z-index: 50;
            pointer-events: none;
            animation: fall linear forwards;
        }

        @keyframes fall {
            to { transform: translateY(110vh) rotate(360deg); opacity: 0; }
        }

        .hidden { display: none; }
        .footer { margin-top: 30px; padding-top: 20px; border-top: 1px solid rgba(255, 255, 255, 0.1); }
        .pink-glow { color: #ffb3c1; text-shadow: 0 0 5px rgba(255, 179, 193, 0.3); }
    </style>
</head>
<body>

    <canvas id="starCanvas"></canvas>

    <div class="wrapper">
        <div id="page1" class="glass-card">
            <span class="highlight-gold">✨ FOREVER BOND ✨</span>
            <h1>siblings forever????</h1>
            <div class="btn-group">
                <button onclick="nextPage()">Yes</button>
                <button onclick="showPls()">No</button>
            </div>
            <p id="pretty-msg" style="margin-top: 15px; color: #ff85a1; min-height: 20px;"></p>
        </div>

        <div id="page2" class="glass-card hidden">
            <span class="highlight-gold">✨ CHEERS TO 20 YEARS ✨</span>
            <h1>happiest 20th birthday myyy darling sister💐💕</h1>
            
            <div id="enjoy-prompt">
                <button onclick="sayMeToo()">are you enjoying this?</button>
            </div>

            <div id="me-too-resp" class="hidden">
                <h2 style="color: #00f2ff; margin-bottom: 15px;">me toooo sis🥳</h2>
            </div>

            <div class="footer">
                with immense love from <br>
                <span class="pink-glow" style="font-weight: 600;">Akash and Tiya 💖💐💕</span>
            </div>
        </div>
    </div>

    <script>
        // Background Stars
        const canvas = document.getElementById('starCanvas');
        const ctx = canvas.getContext('2d');
        let stars = [];

        function init() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            stars = [];
            for (let i = 0; i < 150; i++) {
                stars.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 1.5,
                    opacity: Math.random(),
                    speed: Math.random() * 0.01 + 0.005
                });
            }
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            stars.forEach(s => {
                s.opacity += s.speed;
                if (s.opacity > 1 || s.opacity < 0) s.speed *= -1;
                ctx.fillStyle = `rgba(255, 255, 255, ${Math.abs(s.opacity)})`;
                ctx.beginPath();
                ctx.arc(s.x, s.y, s.size, 0, Math.PI * 2);
                ctx.fill();
            });
            requestAnimationFrame(animate);
        }

        // Light Celebration Logic (Confetti and Balloons)
        function spawnPop() {
            const items = ['🎈', '🎊', '✨', '🎈'];
            const item = document.createElement('div');
            item.className = 'pop-item';
            item.innerText = items[Math.floor(Math.random() * items.length)];
            item.style.left = Math.random() * 100 + 'vw';
            
            // Randomize size and speed
            const size = item.innerText === '🎈' ? 35 : 20;
            item.style.fontSize = (Math.random() * 10 + size) + 'px';
            const duration = Math.random() * 3 + 4;
            item.style.animationDuration = duration + 's';
            
            // Add light opacity
            item.style.opacity = '0.7';

            document.body.appendChild(item);
            setTimeout(() => item.remove(), duration * 1000);
        }

        // Navigation
        function showPls() {
            document.getElementById('pretty-msg').innerText = "prweeeeety pls💖";
        }

        function nextPage() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
            // Increase celebration frequency slightly when birthday is revealed
            setInterval(spawnPop, 300);
        }

        function sayMeToo() {
            document.getElementById('enjoy-prompt').classList.add('hidden');
            document.getElementById('me-too-resp').classList.remove('hidden');
        }

        window.addEventListener('resize', init);
        init();
        animate();
        setInterval(spawnPop, 600); // Constant light flow
    </script>
</body>
</html>
