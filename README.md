#Happiest 20th Birthday 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Darling Sister</title>
    <style>
        /* Base Styling */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background: #1a052e; /* Deep purple base */
            font-family: 'Arial Rounded MT Bold', 'Helvetica', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Canvas for Sparkling Background */
        #glitterCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        /* Content Card */
        .card {
            position: relative;
            z-index: 10;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border: 2px solid rgba(255, 255, 255, 0.2);
            padding: 40px;
            border-radius: 30px;
            text-align: center;
            color: white;
            box-shadow: 0 0 50px rgba(106, 13, 173, 0.5);
            max-width: 450px;
            width: 90%;
            animation: fadeIn 1s ease-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        h1 {
            font-size: 2.2rem;
            margin-bottom: 25px;
            text-shadow: 0 0 10px #ff00de;
        }

        .btn-group {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
        }

        button {
            padding: 12px 25px;
            font-size: 1.1rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        .btn-yes { background: #ff4d6d; color: white; }
        .btn-no { background: #6c757d; color: white; }
        .btn-enjoy { background: #ffd700; color: #333; margin-top: 20px; }
        
        button:hover { transform: scale(1.1); filter: brightness(1.2); }

        #plsMsg {
            color: #ffbd00;
            font-weight: bold;
            margin-top: 15px;
            font-size: 1.2rem;
            display: none;
        }

        .hidden { display: none; }

        .signature {
            margin-top: 30px;
            font-size: 1.2rem;
            color: #fce4ec;
            line-height: 1.6;
        }

        /* Floating Elements */
        .floating {
            position: absolute;
            pointer-events: none;
            z-index: 5;
            animation: floatUp linear forwards;
        }

        @keyframes floatUp {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <canvas id="glitterCanvas"></canvas>

    <div id="page1" class="card">
        <h1>siblings forever????</h1>
        <div class="btn-group">
            <button class="btn-yes" onclick="showPage2()">Yes</button>
            <button class="btn-no" onclick="showPls()">No</button>
        </div>
        <div id="plsMsg">prweeeeety pls💖</div>
    </div>

    <div id="page2" class="card hidden">
        <h1 style="color: #ffd700;">happiest 20th birthday myyy darling sister💐💕</h1>
        
        <div id="enjoySection">
            <button class="btn-enjoy" onclick="showMeToo()">are you enjoying this?</button>
        </div>
        
        <div id="meTooSection" class="hidden">
            <h2 style="color: #00d4ff; font-size: 1.8rem; margin: 20px 0;">me toooo sis🥳</h2>
        </div>

        <div class="signature">
            With immense love from<br>
            <strong>Akash and Tiya 💖💐💕</strong>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('glitterCanvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        // Sparkle/Glitter System
        function initCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            particles = [];
            for (let i = 0; i < 150; i++) {
                particles.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 2 + 1,
                    speed: Math.random() * 0.5 + 0.2,
                    opacity: Math.random(),
                    velX: (Math.random() - 0.5) * 0.5
                });
            }
        }

        function drawSparkles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            // Draw purple gradient background
            let grad = ctx.createRadialGradient(canvas.width/2, canvas.height/2, 0, canvas.width/2, canvas.height/2, canvas.width);
            grad.addColorStop(0, '#302b63');
            grad.addColorStop(1, '#0f0c29');
            ctx.fillStyle = grad;
            ctx.fillRect(0,0, canvas.width, canvas.height);

            particles.forEach(p => {
                ctx.fillStyle = `rgba(255, 255, 255, ${p.opacity})`;
                ctx.shadowBlur = 10;
                ctx.shadowColor = "white";
                ctx.beginPath();
                ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                ctx.fill();
                
                p.y -= p.speed;
                p.x += p.velX;
                if (p.y < -10) p.y = canvas.height + 10;
            });
            requestAnimationFrame(drawSparkles);
        }

        // Balloons, Confetti, Stars, and Hearts
        function spawnCelebration() {
            const types = ['🎈', '🎊', '⭐', '💖', '❤️', '✨'];
            const el = document.createElement('div');
            el.className = 'floating';
            el.innerHTML = types[Math.floor(Math.random() * types.length)];
            el.style.left = Math.random() * 100 + 'vw';
            el.style.top = '100vh';
            el.style.fontSize = (Math.random() * 20 + 20) + 'px';
            
            const duration = Math.random() * 5 + 5;
            el.style.animationDuration = duration + 's';
            
            document.body.appendChild(el);
            setTimeout(() => el.remove(), duration * 1000);
        }

        // Logic Functions
        function showPls() {
            document.getElementById('plsMsg').style.display = 'block';
        }

        function showPage2() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
            // Start heavy celebration
            setInterval(spawnCelebration, 200);
        }

        function showMeToo() {
            document.getElementById('enjoySection').classList.add('hidden');
            document.getElementById('meTooSection').classList.remove('hidden');
        }

        window.addEventListener('resize', initCanvas);
        initCanvas();
        drawSparkles();
        // Initial light sparkles
        setInterval(spawnCelebration, 800);
    </script>
</body>
</html>
