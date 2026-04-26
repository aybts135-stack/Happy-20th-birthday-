# Happy 20th birthday
        <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Sis!</title>
    <style>
        /* Base Styles */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #2e0854; /* Deep Purple */
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Sparkling Glitter Background */
        #glitterCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            background: radial-gradient(circle at center, #4b0082, #2e0854, #1a052e);
        }

        /* Glass Container (The Card) */
        .container {
            position: relative;
            z-index: 100;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            padding: 40px 30px;
            border-radius: 25px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            text-align: center;
            color: white;
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.8);
            width: 85%;
            max-width: 450px;
            animation: fadeIn 1s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        h1 {
            font-size: 2.2rem;
            margin-bottom: 20px;
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
        }

        /* Buttons Styling */
        .btn-group {
            margin-top: 25px;
        }

        button {
            padding: 12px 28px;
            font-size: 1.1rem;
            margin: 10px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 600;
            transition: 0.3s;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }

        .btn-yes { background: #ff4d6d; color: white; }
        .btn-no { background: #6c757d; color: white; }
        .btn-enjoy { background: #ffd700; color: #333; }

        button:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 6px 20px rgba(255, 255, 255, 0.2);
        }

        /* Balloons and Confetti Animation */
        .falling-element {
            position: absolute;
            top: -100px;
            z-index: 50;
            pointer-events: none;
            animation: fallDown linear forwards;
        }

        @keyframes fallDown {
            0% { transform: translateY(0) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            100% { transform: translateY(110vh) rotate(360deg); opacity: 0.7; }
        }

        /* Specific styles for elements */
        .hidden { display: none; }
        .pink-text { color: #ffb3c1; font-weight: bold; }
        .gold-text { color: #ffd700; }
        .footer-note {
            margin-top: 30px;
            font-style: italic;
            font-size: 1.1rem;
            line-height: 1.6;
            color: #ffc2d1;
        }

        #plsDisplay {
            margin-top: 15px;
            font-size: 1.4rem;
            color: #ffeb3b;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <canvas id="glitterCanvas"></canvas>

    <div id="page1" class="container">
        <h1>siblings forever????</h1>
        <div class="btn-group">
            <button class="btn-yes" onclick="goToBirthday()">Yes!</button>
            <button class="btn-no" onclick="showPls()">No</button>
        </div>
        <div id="plsDisplay"></div>
    </div>

    <div id="page2" class="container hidden">
        <h1 class="gold-text">happiest 20th birthday myyy darling sister💐💕</h1>
        
        <div id="enjoySection">
            <p style="font-size: 1.2rem;">Hope you're having the best day!</p>
            <button class="btn-enjoy" onclick="showMeToo()">are you enjoying this?</button>
        </div>

        <div id="meTooDisplay" class="hidden">
            <h2 style="color: #00f2ff; font-size: 1.8rem; margin: 20px 0;">me toooo sis🥳</h2>
        </div>

        <div class="footer-note">
            with immense love from <br>
            <span style="font-size: 1.3rem;">Akash and Tiya 💖💐💕</span>
        </div>
    </div>

    <script>
        // --- Glitter Background Logic ---
        const canvas = document.getElementById('glitterCanvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function initCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            particles = [];
            for (let i = 0; i < 150; i++) {
                particles.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 2 + 1,
                    speed: Math.random() * 0.5 + 0.1,
                    opacity: Math.random()
                });
            }
        }

        function animateGlitter() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                ctx.fillStyle = `rgba(255, 255, 255, ${Math.abs(Math.sin(Date.now() * 0.001 + p.opacity * 10))})`;
                ctx.beginPath();
                ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                ctx.fill();
                p.y += p.speed;
                if (p.y > canvas.height) p.y = -5;
            });
            requestAnimationFrame(animateGlitter);
        }

        // --- Celebration Elements (Balloons, Confetti, Hearts) ---
        function createCelebration() {
            const elements = ['🎈', '🎊', '💖', '❤️', '🎈', '🎉'];
            const el = document.createElement('div');
            el.className = 'falling-element';
            el.innerText = elements[Math.floor(Math.random() * elements.length)];
            
            el.style.left = Math.random() * 100 + 'vw';
            
            let fontSize = Math.random() * 20 + 20;
            if (el.innerText === '🎈') fontSize += 15; // Make balloons bigger
            el.style.fontSize = fontSize + 'px';
            
            const duration = Math.random() * 3 + 4;
            el.style.animationDuration = duration + 's';
            
            document.body.appendChild(el);
            setTimeout(() => el.remove(), duration * 1000);
        }

        // --- Navigation Functions ---
        function showPls() {
            document.getElementById('plsDisplay').innerText = "prweeeeety pls💖";
        }

        function goToBirthday() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
            // Increase celebration frequency on birthday page
            setInterval(createCelebration, 150);
        }

        function showMeToo() {
            document.getElementById('enjoySection').classList.add('hidden');
            document.getElementById('meTooDisplay').classList.remove('hidden');
        }

        // --- Initialization ---
        window.addEventListener('resize', initCanvas);
        initCanvas();
        animateGlitter();
        setInterval(createCelebration, 300); // Start falling elements
    </script>
</body>
</html>
