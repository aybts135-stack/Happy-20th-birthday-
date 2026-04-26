# Happy 20th birthday
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy 20th Birthday!</title>
    <style>
        :root {
            --purple-dark: #2e0854;
            --purple-light: #6a0dad;
            --gold: #ffd700;
        }

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background: radial-gradient(circle at center, var(--purple-light), var(--purple-dark));
            font-family: 'Comic Sans MS', cursive, sans-serif;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        /* Sparkle Canvas for Background */
        #bgCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
        }

        .content-box {
            position: relative;
            z-index: 10;
            background: rgba(0, 0, 0, 0.3);
            padding: 40px;
            border-radius: 30px;
            backdrop-filter: blur(8px);
            border: 2px solid rgba(255, 215, 0, 0.3);
            box-shadow: 0 0 30px rgba(0,0,0,0.5);
            max-width: 85%;
        }

        h1 { font-size: 3.5rem; text-shadow: 0 0 15px #ff00ff; margin-bottom: 20px; }
        
        button {
            padding: 15px 30px;
            font-size: 1.3rem;
            margin: 10px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        .btn-yes { background: #ff4d6d; color: white; }
        .btn-no { background: #aeaeae; color: white; }
        .btn-enjoy { background: var(--gold); color: #333; margin-top: 20px; }
        button:hover { transform: scale(1.1) rotate(-2deg); }

        /* Floating Elements Styling */
        .particle {
            position: absolute;
            pointer-events: none;
            z-index: 5;
            animation: floatUp linear forwards;
        }

        @keyframes floatUp {
            0% { transform: translateY(110vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-20vh) rotate(720deg); opacity: 0; }
        }

        .hidden { display: none; }
        .footer { margin-top: 30px; font-size: 1.2rem; color: #ffb3c1; }
    </style>
</head>
<body>

    <canvas id="bgCanvas"></canvas>

    <div id="ui-container" class="content-box">
        <div id="page1">
            <h1>siblings forever????</h1>
            <button class="btn-yes" onclick="goToBirthday()">Yes!</button>
            <button class="btn-no" onclick="showPretty()">No</button>
            <p id="pretty-pls" style="font-size: 1.8rem; margin-top: 20px; color: #ffeb3b;"></p>
        </div>

        <div id="page2" class="hidden">
            <h1 style="color: var(--gold);">happiest 20th birthday myyy darling sister💐💕</h1>
            
            <div id="enjoy-btn-wrapper">
                <button class="btn-enjoy" onclick="sayMeToo()">are you enjoying this?</button>
            </div>
            
            <h2 id="me-tooo" class="hidden" style="color: #00e5ff; font-size: 2.5rem;">me toooo sis🥳</h2>

            <div class="footer">
                with immense love from Akash and Tiya 💖💐💕
            </div>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('bgCanvas');
        const ctx = canvas.getContext('2d');
        let width, height;

        function resize() {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resize);
        resize();

        // Background Sparkle Stars
        const sparkles = [];
        for(let i = 0; i < 150; i++) {
            sparkles.push({
                x: Math.random() * width,
                y: Math.random() * height,
                size: Math.random() * 2,
                opacity: Math.random(),
                speed: 0.01 + Math.random() * 0.02
            });
        }

        function drawBackground() {
            ctx.clearRect(0, 0, width, height);
            sparkles.forEach(s => {
                s.opacity += s.speed;
                if(s.opacity > 1 || s.opacity < 0) s.speed *= -1;
                ctx.fillStyle = `rgba(255, 255, 255, ${Math.abs(s.opacity)})`;
                ctx.beginPath();
                ctx.arc(s.x, s.y, s.size, 0, Math.PI * 2);
                ctx.fill();
            });
            requestAnimationFrame(drawBackground);
        }
        drawBackground();

        // Continuous Flowing Elements: Confetti, Balloons, Stars, Hearts
        function spawnParticle() {
            const items = [
                { text: '🎈', type: 'balloon' },
                { text: '✨', type: 'sparkle' },
                { text: '⭐', type: 'star' },
                { text: '🎊', type: 'confetti' },
                { text: '💖', type: 'heart' },
                { text: '❤️', type: 'heart' },
                { text: '🌸', type: 'flower' }
            ];
            
            const item = items[Math.floor(Math.random() * items.length)];
            const div = document.createElement('div');
            div.className = 'particle';
            div.innerText = item.text;
            
            // Random horizontal position
            div.style.left = Math.random() * 100 + 'vw';
            
            // Varied sizes
            const size = item.type === 'balloon' ? (30 + Math.random() * 20) : (15 + Math.random() * 15);
            div.style.fontSize = size + 'px';
            
            // Varied animation speeds for depth
            const duration = 4 + Math.random() * 6;
            div.style.animationDuration = duration + 's';
            
            // Add slight glowing effect to stars and sparkles
            if(item.type === 'star' || item.type === 'sparkle') {
                div.style.textShadow = "0 0 10px white, 0 0 20px gold";
            }

            document.body.appendChild(div);

            // Cleanup
            setTimeout(() => {
                div.remove();
            }, duration * 1000);
        }

        // Keep the screen filled with a lot of flowing items
        setInterval(spawnParticle, 150);

        // Logic Functions
        function showPretty() {
            document.getElementById('pretty-pls').innerText = "prweeeeety pls💖";
        }

        function goToBirthday() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
        }

        function sayMeToo() {
            document.getElementById('enjoy-btn-wrapper').classList.add('hidden');
            document.getElementById('me-tooo').classList.remove('hidden');
        }
    </script>
</body>
</html>
