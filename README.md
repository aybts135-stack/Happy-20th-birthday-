# Happy 20th birthday
      
                                <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happiest Birthday!</title>
    <style>
        /* Modern, Clean Styles inspired by the link */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body, html {
            width: 100%;
            height: 100%;
            background-color: #1a052e; /* The deep dark purple from the site */
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            color: #ffffff;
            overflow-x: hidden;
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
            z-index: 10;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            padding: 20px;
        }

        /* The Main Glass Card */
        .glass-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 40px 25px;
            width: 100%;
            max-width: 400px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            animation: slideUp 0.8s ease-out;
        }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1 {
            font-size: 1.8rem;
            font-weight: 400;
            line-height: 1.4;
            margin-bottom: 20px;
        }

        .highlight-gold {
            color: #ffd700;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 2px;
            display: block;
            margin-bottom: 10px;
        }

        /* Buttons */
        .btn-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 25px;
        }

        button {
            background: transparent;
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.4);
            padding: 10px 25px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            transition: 0.3s;
        }

        button:hover {
            background: white;
            color: #1a052e;
        }

        #pretty-msg {
            margin-top: 20px;
            color: #ff85a1;
            font-weight: 500;
            min-height: 24px;
        }

        .hidden { display: none; }

        /* Signature Section */
        .footer {
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            font-size: 1rem;
            line-height: 1.6;
        }

        .pink-glow {
            color: #ffb3c1;
            text-shadow: 0 0 5px rgba(255, 179, 193, 0.5);
        }
    </style>
</head>
<body>

    <canvas id="starCanvas"></canvas>

    <div class="wrapper">
        <div id="page1" class="glass-card">
            <span class="highlight-gold">✨ FOREVER BOND ✨</span>
            <h1>siblings forever????</h1>
            <div class="btn-container">
                <button onclick="nextPage()">Yes</button>
                <button onclick="showPls()">No</button>
            </div>
            <div id="pretty-msg"></div>
        </div>

        <div id="page2" class="glass-card hidden">
            <span class="highlight-gold">✨ CHEERS TO 20 YEARS ✨</span>
            <h1>happiest 20th birthday myyy darling sister💐💕</h1>
            
            <div id="enjoy-prompt">
                <button onclick="sayMeToo()" style="margin-top: 10px;">are you enjoying this?</button>
            </div>

            <div id="me-too-resp" class="hidden">
                <h2 style="color: #00f2ff; margin: 15px 0;">me toooo sis🥳</h2>
            </div>

            <div class="footer">
                with immense love from <br>
                <span class="pink-glow">Akash and Tiya 💖💐💕</span>
            </div>
        </div>
    </div>

    <script>
        // Sparkle/Glitter Background Animation
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
                    speed: Math.random() * 0.02 + 0.005
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

        // Logic
        function showPls() {
            document.getElementById('pretty-msg').innerText = "prweeeeety pls💖";
        }

        function nextPage() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
        }

        function sayMeToo() {
            document.getElementById('enjoy-prompt').classList.add('hidden');
            document.getElementById('me-too-resp').classList.remove('hidden');
        }

        window.addEventListener('resize', init);
        init();
        animate();
    </script>
</body>
</html>
