#Happiest 20th birthday <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday!</title>
    <style>
        /* Exact aesthetic from the inspiration link */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: #2e0854; /* Deep Purple */
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
            text-align: center;
        }

        /* Sparkling Background */
        #glitterCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            background: radial-gradient(circle at center, #4b0082, #2e0854, #1a052e);
        }

        /* The Centered White Box (Same as link) */
        .card {
            position: relative;
            z-index: 100;
            background: rgba(255, 255, 255, 0.98);
            color: #333;
            padding: 40px 25px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            width: 90%;
            max-width: 450px;
            animation: fadeIn 0.8s ease-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .gold-sparkle {
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

        /* Interaction Buttons */
        .btn-container {
            margin-top: 10px;
        }

        button {
            padding: 12px 28px;
            font-size: 1rem;
            margin: 8px;
            border: 2px solid #2e0854;
            border-radius: 5px;
            background: transparent;
            color: #2e0854;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
        }

        button:hover {
            background: #2e0854;
            color: #fff;
        }

        #noResponse {
            margin-top: 15px;
            color: #e60073;
            font-weight: bold;
            font-style: italic;
        }

        .hidden { display: none; }

        /* Pop from above: Balloons and Confetti */
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

        .footer {
            margin-top: 35px;
            padding-top: 20px;
            border-top: 1px solid #eee;
            color: #555;
            font-size: 1rem;
            line-height: 1.6;
        }

        .love-names {
            color: #e60073;
            font-weight: bold;
            display: block;
            margin-top: 5px;
            font-size: 1.1rem;
        }
    </style>
</head>
<body>

    <canvas id="glitterCanvas"></canvas>

    <div id="page1" class="card">
        <span class="gold-sparkle">✨ SIBLINGS FOREVER ✨</span>
        <h1>siblings forever????</h1>
        <div class="btn-container">
            <button onclick="goNext()">Yes</button>
            <button onclick="showPls()">No</button>
        </div>
        <p id="noResponse"></p>
    </div>

    <div id="page2" class="card hidden">
        <span class="gold-sparkle">✨ CHEERS TO 20 YEARS ✨</span>
        <h1>happiest 20th birthday myyy darling sister💐💕</h1>
        
        <div id="enjoyQuestion">
            <button onclick="sayMeToo()">are you enjoying this?</button>
        </div>

        <div id="meTooResponse" class="hidden">
            <h2 style="color: #2e0854; margin: 15px 0;">me toooo sis🥳</h2>
        </div>

        <div class="footer">
            with immense love from
            <span class="love-names">Akash and Tiya 💖💐💕</span>
        </div>
    </div>

    <script>
        // Glitter Background Logic
        const canvas = document.getElementById('glitterCanvas');
        const ctx = canvas.getContext('2d');
        let dots = [];

        function init() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            dots = [];
            for (let i = 0; i < 150; i++) {
                dots.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 1.5 + 0.5,
                    speed: Math.random() * 0.4 + 0.1,
                    opacity: Math.random()
                });
            }
        }

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            dots.forEach(d => {
                ctx.fillStyle = `rgba(255, 255, 255, ${Math.abs(Math.sin(Date.now() * 0.001 + d.opacity * 10))})`;
                ctx.beginPath();
                ctx.arc(d.x, d.y, d.size, 0, Math.PI * 2);
                ctx.fill();
                d.y += d.speed;
                if (d.y > canvas.height) d.y = -10;
            });
            requestAnimationFrame(draw);
        }

        // Balloons and Confetti popping from above
        function spawnPop() {
            const symbols = ['🎈', '🎊', '🎈', '🎉', '💖', '❤️'];
            const item = document.createElement('div');
            item.className = 'pop-item';
            item.innerText = symbols[Math.floor(Math.random() * symbols.length)];
            item.style.left = Math.random() * 100 + 'vw';
            
            const isBalloon = item.innerText === '🎈';
            item.style.fontSize = (isBalloon ? 40 : 25) + 'px';
            
            const duration = Math.random() * 3 + 4;
            item.style.animationDuration = duration + 's';
            item.style.opacity = '0.8';

            document.body.appendChild(item);
            setTimeout(() => item.remove(), duration * 1000);
        }

        // Logic Functions
        function showPls() {
            document.getElementById('noResponse').innerText = "prweeeeety pls💖";
        }

        function goNext() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
            // Start the celebration items once she says Yes
            setInterval(spawnPop, 250);
        }

        function sayMeToo() {
            document.getElementById('enjoyQuestion').classList.add('hidden');
            document.getElementById('meTooResponse').classList.remove('hidden');
        }

        window.addEventListener('resize', init);
        init();
        draw();
    </script>
</body>
</html>
