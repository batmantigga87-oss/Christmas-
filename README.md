<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>For Ashita 🎄</title>
    <style>
        :root { 
            /* Deep Christmas Gradient */
            --bg: radial-gradient(circle, #2d0a0a 0%, #0b0d17 100%); 
            --card-bg: #fffcf2; /* Elegant Cream */
            --accent: #ff4d4d;
            --gold: #d4af37;
        }
        body { 
            margin: 0; 
            background: var(--bg); 
            background-attachment: fixed;
            color: white; 
            font-family: 'Georgia', serif; 
            overflow: hidden; 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            height: 100vh; 
            touch-action: manipulation; 
        }
        
        #snow-container { position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 1; }

        /* Step Sections */
        .step { display: none; text-align: center; padding: 20px; animation: fadeIn 0.8s ease; z-index: 10; position: relative; }
        .active { display: block; }

        .gift-box { font-size: 80px; cursor: pointer; animation: pulse 2s infinite; margin-bottom: 20px; filter: drop-shadow(0 0 15px rgba(255,255,255,0.3)); }
        .text-line { font-size: 1.3rem; line-height: 1.6; font-style: italic; color: #fdf0d5; max-width: 280px; margin: 0 auto; text-shadow: 1px 1px 5px rgba(0,0,0,0.5); }
        
        /* The Note Cards (Boxes) at the end */
        .gallery { position: relative; width: 100vw; height: 100vh; display: none; z-index: 5; }
        .polaroid { 
            position: absolute; 
            background: var(--card-bg); 
            padding: 15px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.6); 
            width: 120px; 
            height: 140px;
            border-radius: 5px;
            border: 2px solid var(--gold); /* Gold border for elegance */
            display: flex; 
            justify-content: center; 
            align-items: center;
            animation: dropIn 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards; 
            opacity: 0;
        }
        .polaroid-text { font-size: 0.95rem; font-weight: bold; color: #441414; text-align: center; line-height: 1.3; }

        .final-msg { 
            position: absolute; bottom: 10%; width: 100%; text-align: center; 
            font-size: 1.8rem; font-weight: bold; color: #fff;
            text-shadow: 0 0 20px rgba(255, 77, 77, 0.8);
            z-index: 100; animation: fadeIn 2s ease;
        }

        /* Animations */
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes pulse { 0% { transform: scale(1); } 50% { transform: scale(1.15); } 100% { transform: scale(1); } }
        @keyframes dropIn { from { transform: translateY(-700px) rotate(50deg); opacity: 0; } to { opacity: 1; transform: translateY(0) rotate(var(--r)); } }

        .snowflake { position: fixed; top: -10px; color: white; pointer-events: none; z-index: 2; }
    </style>
</head>
<body onclick="nextStep()">

    <div id="snow-container"></div>

    <div class="step active" id="s1">
        <div class="gift-box">🎁</div>
        <p class="text-line">Hey Ashita, tap the gift...</p>
    </div>

    <div class="step" id="s2">
        <p class="text-line">Sometimes you just want to make Christmas...</p>
    </div>

    <div class="step" id="s3">
        <p class="text-line">...feel a little more special for them.</p>
    </div>

    <div class="step" id="s4">
        <p class="text-line">So you create something unique.</p>
    </div>

    <div class="gallery" id="s5">
        <div class="polaroid" style="top:15%; left:10%; --r:-12deg;">
            <div class="polaroid-text">My Favorite<br>Person ❤️</div>
        </div>
        <div class="polaroid" style="top:10%; left:58%; --r:15deg; animation-delay: 0.4s;">
            <div class="polaroid-text">My Whole<br>World 🌍</div>
        </div>
        <div class="polaroid" style="top:42%; left:18%; --r:-8deg; animation-delay: 0.8s;">
            <div class="polaroid-text">The Prettiest<br>Smile ✨</div>
        </div>
        <div class="polaroid" style="top:38%; left:62%; --r:12deg; animation-delay: 1.2s;">
            <div class="polaroid-text">Bestest<br>Friend 👩‍❤️‍👨</div>
        </div>
        
        <div class="final-msg">I love you meri Ashita 💕</div>
    </div>

    <script>
        let current = 1;
        function nextStep() {
            if (current < 4) {
                document.getElementById('s' + current).classList.remove('active');
                current++;
                document.getElementById('s' + current).classList.add('active');
            } else if (current === 4) {
                document.getElementById('s4').classList.remove('active');
                document.getElementById('s5').style.display = 'block';
                current++;
            }
        }

        function createSnow() {
            const flake = document.createElement('div');
            flake.className = 'snowflake';
            flake.innerHTML = '❄';
            flake.style.left = Math.random() * 100 + 'vw';
            flake.style.fontSize = Math.random() * 1 + 0.5 + 'rem';
            flake.style.opacity = Math.random();
            document.getElementById('snow-container').appendChild(flake);
            let pos = -10;
            let int = setInterval(() => {
                pos += 1.8;
                flake.style.top = pos + 'px';
                if (pos > window.innerHeight) { clearInterval(int); flake.remove(); }
            }, 20);
        }
        setInterval(createSnow, 250);
    </script>
</body>
</html>
