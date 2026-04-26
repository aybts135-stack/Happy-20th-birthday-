# Happy 20th birthday
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Sis!</title>
    <style>
        /* Modern aesthetic inspired by the provided link */
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #1a052e; /* Very dark purple base */
            font-family: 'Poppins', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Sparkling Glitter Canvas - Just like the website */
        #glitterCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            background: radial-gradient(circle at center, #4b0082, #1a052e);
        }

        /* Glassmorphism Card Effect */
        .glass-card {
            position: relative;
            z-index: 10;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 40px;
            text-align: center;
            color: #ffffff;
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
            width: 85%;
            max-width: 450px;
            transition: all 0.5s ease;
        }

        h1 {
            font-weight: 300;
            letter-spacing: 1px;
            line-height: 1.4;
            margin-bottom: 30px;
        }

        /* Shining/Glow effect for the text */
        .shimmer {
            background: linear-gradient(to right, #ffffff 0, #f2a2ff 10%, #ffffff 20%);
            background-position: 0;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: shine 3s infinite linear;
            background-size: 200% auto;
        }

        @keyframes shine {
            to { background-position: 200% center; }
        }

        /* Button Styling */
        .btn-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
        }

        button {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.4);
            color: white;
            padding: 12px 30px;
            border-radius: 30px;
            cursor: pointer;
            font-size: 1rem;
            transition: 0.3s;
            backdrop-filter: blur(5px);
        }

        button:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
            border-color: #f2a2ff;
        }

        #pretty-msg {
            margin-top: 20px;
            color: #f2a2ff;
            font-style: italic;
            height: 24px;
        }

        .hidden { display: none; }

        .footer {
            margin-top: 40px;
            font-size: 0.9rem;
            opacity: 0.8;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            padding-top: 20px;
        }

        strong { color: #f2a2ff; }
    </style>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500&display=swap" rel="stylesheet">
</head>
<body>

    <canvas id="glitterCanvas"></canvas>

    <div id="page1" class="glass-card">
        <h1 class="shimmer">siblings forever????</h1>
        <div class="btn-container">
            <button onclick="goToBirthday()">Yes</button>
            <button onclick="showPretty()">No</button>
        </div>
        <div id="pretty-msg"></div>
    </div>

    <div id="page2" class="glass-card hidden">
        <h1 class="shimmer">happiest 20th birthday myyy darling sister💐💕</h1>
        
        <div id="enjoy-section">
            <button onclick="showMeToo()">are you enjoying this?</button>
        </div>
        
        <div id="me-too-msg" class="hidden">
            <h2 style="color: #f2a2ff; font-weight: 300;">me toooo sis🥳</h2>
        </div>

        <div class="footer">
            with immense love from<br>
            <strong>Akash and Tiya 💖💐💕</strong>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('glitterCanvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function init() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            particles = [];
            // Create the "Glitter" background
            for (let i = 0; i < 200; i++) {
                particles.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 1.5 + 0.5,
                    speedY: Math.random() * 0.4 + 0.1,
                    opacity: Math.random(),
                    blinkSpeed: Math.random() * 0.02 + 0.01
                });
            }
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            particles.forEach(p => {
                // Glitter twinkle effect
                p.opacity += p.blinkSpeed;
                if (p.opacity > 1 || p.opacity < 0.1) p.blinkSpeed *= -1;

                ctx.fillStyle = `rgba(255, 255, 255, ${Math.abs(p.opacity)})`;
                ctx.beginPath();
                ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                ctx.fill();

                // Slow downward drift
                p.y += p.speedY;
                if (p.y > canvas.height) p.y = -10;
            });
            requestAnimationFrame(animate);
        }

        function showPretty() {
            document.getElementById('pretty-msg').innerText = "prweeeeety pls💖";
        }

        function goToBirthday() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
        }

        function showMeToo() {
            document.getElementById('enjoy-section').classList.add('hidden');
            document.getElementById('me-too-msg').classList.remove('hidden');
        }

        window.addEventListener('resize', init);
        init();
        animate();
    </script>
</body>
</html>

            
