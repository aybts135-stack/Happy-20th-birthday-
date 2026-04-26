#Happiest 20th birthday            
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happiest Birthday!</title>
    <style>
        /* Exact layout and color palette from the provided link */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: #2e0854; /* Deep Royal Purple */
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
            text-align: center;
        }

        /* Twinkling Glitter Canvas Background */
        #glitterCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            background: radial-gradient(circle at center, #4b0082, #2e0854, #1a052e);
        }

        /* The Main White Content Box */
        .main-card {
            position: relative;
            z-index: 100;
            background: rgba(255, 255, 255, 0.98);
            color: #333;
            padding: 40px 25px;
            border-radius: 15px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
            width: 90%;
            max-width: 440px;
            animation: cardAppear 0.8s ease-out;
        }

        @keyframes cardAppear {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .gold-sparkle-text {
            color: #b8860b;
            font-weight: bold;
            letter-spacing: 2px;
            font-size: 0.85rem;
            margin-bottom: 15px;
            display: block;
            text-transform: uppercase;
        }

        h1 {
            font-size: 1.8rem;
            margin-bottom: 25px;
            line-height: 1.4;
            color: #2e0854;
        }

        /* Buttons matching the site's minimalist style */
        .button-group {
            margin-top: 10px;
        }

        button {
            padding: 12px 30px;
            font-size: 1rem;
            margin: 8px;
            border: 2px solid #2e0854;
            border-radius: 6px;
            background: transparent;
            color: #2e0854;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        button:hover {
            background: #2e0854;
            color: #fff;
        }

        #noMsg {
            margin-top: 15px;
            color: #d63384;
            font-weight: bold;
            font-style: italic;
            min-height: 24px;
        }

        .hidden { display: none; }

        /* Celebration Items: Balloons and Confetti popping from top */
        .celebration-pop {
            position: absolute;
            top: -60px;
            z-index: 50;
            pointer-events: none;
            animation: dropDown linear forwards;
        }

        @keyframes dropDown {
            to { transform: translateY(110vh) rotate(360deg); opacity: 0; }
        }

        /* Footer and Signature */
        .footer-line {
            margin-top: 35px;
            padding-top: 20px;
            border-top: 1px solid #eee;
            color: #666;
            font-size: 0.95rem;
            line-height: 1.6;
        }

        .names {
            color: #d63384;
            font-weight: bold;
            display: block;
            margin-top: 8px;
            font-size: 1.1rem;
        }
    </style>
</head>
<body>

    <canvas id="glitterCanvas"></canvas>

    <div id="page1" class="main-card">
        <span class="gold-sparkle-text">✨ FOREVER BOND ✨</span>
        <h1>siblings forever????</h1>
        <div class="button-group">
            <button onclick="showBirthdayPage()">Yes</button>
            <button onclick="showPleaseText()">No</button>
        </div>
        <p id="noMsg"></p>
    </div>

    <div id="page2" class="main-card hidden">
        <span class="gold-sparkle-text">✨ CHEERS TO 20 YEARS ✨</span>
        <h1>happiest 20th birthday myyy darling sister💐💕</h1>
        
        <div id="enjoyQuestion">
            <button onclick="displayMeToo()">are you enjoying this?</button>
        </div>

        <div id="meTooResponse" class="hidden">
            <h2 style="color: #2e0854; margin: 15px 0;">me toooo sis🥳</h2>
        </div>

        <div class="footer-line">
            with immense love from
            <span class="names">Akash and Tiya 💖💐💕</span>
        </div>
    </div>

    <script>
        // --- Background Glitter Shine Animation ---
        const canvas = document.getElementById('glitterCanvas');
        const ctx = canvas.getContext('2d');
        let glitterParticles = [];

        function resize() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            glitterParticles = [];
            for (let i = 0; i < 150; i++) {
                glitterParticles.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 1.5 + 0.5,
                    speed: Math.random() * 0.4 + 0.1,
                    opacity: Math.random()
                });
            }
        }

        function animateGlitter() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            glitterParticles.forEach(p => {
                ctx.fillStyle = `rgba(255, 255, 255, ${Math.abs(Math.sin(Date.now() * 0.001 + p.opacity * 10))})`;
                ctx.beginPath();
                ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                ctx.fill();
                p.y += p.speed;
                if (p.y > canvas.height) p.y = -10;
            });
            requestAnimationFrame(animateGlitter);
        }

        // --- Balloons and Confetti Spawning ---
        function startCelebration() {
            const icons = ['🎈', '🎊', '❤️', '🎈', '🎉', '💖'];
            const item = document.createElement('div');
            item.className = 'celebration-pop';
            item.innerText = icons[Math.floor(Math.random() * icons.length)];
            item.style.left = Math.random() * 100 + 'vw';
            
            const isBalloon = item.innerText === '🎈';
            item.style.fontSize = (isBalloon ? 45 : 25) + 'px';
            
            const duration = Math.random() * 3 + 4;
            item.style.animationDuration = duration + 's';
            item.style.opacity = '0.8';

            document.body.appendChild(item);
            setTimeout(() => item.remove(), duration * 1000);
        }

        // --- Button Logic ---
        function showPleaseText() {
            document.getElementById('noMsg').innerText = "prweeeeety pls💖";
        }

        function showBirthdayPage() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
            // Start the balloons and confetti flow
            setInterval(startCelebration, 250);
        }

        function displayMeToo() {
            document.getElementById('enjoyQuestion').classList.add('hidden');
            document.getElementById('meTooResponse').classList.remove('hidden');
        }

        window.addEventListener('resize', resize);
        resize();
        animateGlitter();
    </script>
</body>
</html>
