# Happy 20th birthday
        
               <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Birthday Magic for Sis</title>
    <style>
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background: #2e0854; /* Deep Purple */
            font-family: 'Arial Rounded MT Bold', 'Helvetica', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Shining Background */
        #glitterCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            background: radial-gradient(circle at center, #6a0dad, #2e0854, #1a052e);
        }

        .main-card {
            position: relative;
            z-index: 100;
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(15px);
            padding: 50px;
            border-radius: 40px;
            border: 3px solid rgba(255, 215, 0, 0.5);
            box-shadow: 0 0 50px rgba(255, 0, 255, 0.3);
            text-align: center;
            color: white;
            max-width: 80%;
        }

        h1 { font-size: 3.5rem; text-shadow: 0 0 20px #fff, 0 0 30px #ff00ff; }
        
        .btn {
            padding: 15px 40px;
            font-size: 1.5rem;
            margin: 15px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
            box-shadow: 0 0 15px rgba(255, 255, 255, 0.4);
        }

        .btn-yes { background: linear-gradient(45deg, #ff4d6d, #ff758c); color: white; }
        .btn-no { background: #888; color: white; }
        .btn-enjoy { background: linear-gradient(45deg, #ffd700, #ffae00); color: #333; margin-top: 25px; }
        
        .btn:hover { transform: scale(1.1); box-shadow: 0 0 25px gold; }

        /* Flowing Elements */
        .magic-item {
            position: absolute;
            top: -100px;
            z-index: 50;
            pointer-events: none;
            animation: fall linear forwards;
            filter: drop-shadow(0 0 10px white);
        }

        @keyframes fall {
            0% { transform: translateY(0) translateX(0) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(110vh) translateX(100px) rotate(720deg); opacity: 0; }
        }

        .hidden { display: none; }
        .signature { margin-top: 40px; font-size: 1.4rem; color: #ffb3c1; text-shadow: 0 0 5px black; }
    </style>
</head>
<body>

    <canvas id="glitterCanvas"></canvas>

    <div class="main-card">
        <div id="page1">
            <h1>siblings forever????</h1>
            <button class="btn btn-yes" onclick="showBirthday()">Yes!</button>
            <button class="btn btn-no" onclick="showPretty()">No</button>
            <h2 id="prettyText" style="color: #ffeb3b; margin-top: 20px;"></h2>
        </div>

        <div id="page2" class="hidden">
            <h1 style="color: #ffd700;">happiest 20th birthday myyy darling sister💐💕</h1>
            
            <div id="enjoyBox">
                <button class="btn btn-enjoy" onclick="showMeToo()">are you enjoying this?</button>
            </div>
            
            <h2 id="meToo" class="hidden" style="color: #00f2ff; font-size: 2.5rem; animation: pulse 1s infinite alternate;">me toooo sis🥳</h2>

            <div class="signature">
                with immense love from Akash and Tiya 💖💐💕
            </div>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('glitterCanvas');
        const ctx = canvas.getContext('2d');
        let dots = [];

        function init() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            for(let i=0; i<200; i++) {
                dots.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    r: Math.random() * 2 + 1,
                    d: Math.random() * 200,
                    v: Math.random() * 0.5 + 0.2
                });
            }
        }

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = "rgba(255, 255, 255, 0.8)";
            dots.forEach(p => {
                ctx.beginPath();
                ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
                ctx.fill();
                p.y += p.v;
                if(p.y > canvas.height) p.y = -10;
            });
            requestAnimationFrame(draw);
        }

        // CREATE TONS OF FLOWING STUFF
        function createMagic() {
            const container = document.body;
            const items = ['🎈', '✨', '⭐', '🎊', '💖', '❤️', '🌟', '💎', '✨'];
            const item = items[Math.floor(Math.random() * items.length)];
            
            const div = document.createElement('div');
            div.className = 'magic-item';
            div.innerText = item;
            
            // Random horizontal start
            div.style.left = Math.random() * 100 + 'vw';
            
            // Random size - balloons bigger
            let size = Math.random() * 30 + 20;
            if(item === '🎈') size += 20;
            div.style.fontSize = size + 'px';
            
            // Random speed
            const duration = Math.random() * 3 + 3;
            div.style.animationDuration = duration + 's';

            container.appendChild(div);

            // Remove after animation
            setTimeout(() => div.remove(), duration * 1000);
        }

        // Spawn very frequently for "Alot of" effect
        setInterval(createMagic, 80);

        // Interaction Logic
        function showPretty() {
            document.getElementById('prettyText').innerText = "prweeeeety pls💖";
        }

        function showBirthday() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
        }

        function showMeToo() {
            document.getElementById('enjoyBox').classList.add('hidden');
            document.getElementById('meToo').classList.remove('hidden');
        }

        init();
        draw();
        window.addEventListener('resize', init);
    </script>
</body>
</html>

