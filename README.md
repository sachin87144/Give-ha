<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Dearest Tamanna</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background: linear-gradient(135deg, #ffafbd, #ffc3a0);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        #password-container {
            background: rgba(255, 255, 255, 0.9);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            text-align: center;
            z-index: 100;
        }

        #password-container h2 {
            color: #ff6b6b;
            margin-bottom: 20px;
        }

        #password-input {
            padding: 10px 15px;
            border: 2px solid #ffafbd;
            border-radius: 8px;
            margin-bottom: 15px;
            width: 200px;
            font-size: 16px;
        }

        #submit-btn {
            background: #ff6b6b;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            transition: all 0.3s ease;
        }

        #submit-btn:hover {
            background: #ff5252;
            transform: scale(1.05);
        }

        #error-message {
            color: #ff5252;
            margin-top: 10px;
            display: none;
        }

        #proposal-container {
            display: none;
            text-align: center;
            color: white;
            position: relative;
            width: 100%;
            height: 100%;
        }

        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background: #ff6b6b;
            transform: rotate(45deg);
            animation: float 5s infinite ease-in-out;
        }

        .heart:before, .heart:after {
            content: '';
            width: 20px;
            height: 20px;
            background: #ff6b6b;
            border-radius: 50%;
            position: absolute;
        }

        .heart:before {
            top: -10px;
            left: 0;
        }

        .heart:after {
            top: 0;
            left: -10px;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(45deg); }
            50% { transform: translateY(-20px) rotate(45deg); }
        }

        .message {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(255, 255, 255, 0.9);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            color: #ff6b6b;
            max-width: 500px;
            width: 80%;
            opacity: 0;
            animation: fadeIn 2s forwards 1s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        p {
            font-size: 1.2rem;
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .buttons {
            margin-top: 20px;
        }

        button {
            padding: 12px 25px;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            cursor: pointer;
            margin: 0 10px;
            transition: all 0.3s ease;
        }

        #yes-btn {
            background: #4CAF50;
            color: white;
        }

        #no-btn {
            background: #ff5252;
            color: white;
            position: relative;
        }

        #yes-btn:hover {
            background: #45a049;
            transform: scale(1.1);
        }

        #no-btn:hover {
            background: #ff0000;
        }

        .flowers {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 100px;
            display: flex;
            justify-content: space-around;
            align-items: flex-end;
        }

        .flower {
            width: 50px;
            height: 50px;
            position: relative;
            animation: grow 2s forwards;
            opacity: 0;
        }

        .flower:nth-child(1) { animation-delay: 2s; }
        .flower:nth-child(2) { animation-delay: 2.5s; }
        .flower:nth-child(3) { animation-delay: 3s; }
        .flower:nth-child(4) { animation-delay: 3.5s; }
        .flower:nth-child(5) { animation-delay: 4s; }

        @keyframes grow {
            from { 
                transform: scale(0) translateY(100px); 
                opacity: 0;
            }
            to { 
                transform: scale(1) translateY(0); 
                opacity: 1;
            }
        }

        .petal {
            position: absolute;
            width: 20px;
            height: 20px;
            background: #ff6b6b;
            border-radius: 50%;
        }

        .petal:nth-child(1) { top: 0; left: 15px; }
        .petal:nth-child(2) { top: 15px; left: 0; }
        .petal:nth-child(3) { top: 15px; right: 0; }
        .petal:nth-child(4) { bottom: 0; left: 15px; }
        .petal.center {
            width: 15px;
            height: 15px;
            background: #ffd700;
            top: 17.5px;
            left: 17.5px;
            z-index: 2;
        }

        .stem {
            position: absolute;
            width: 5px;
            height: 60px;
            background: #4CAF50;
            top: 50px;
            left: 22.5px;
        }

        .final-message {
            display: none;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(255, 255, 255, 0.95);
            padding: 40px;
            border-radius: 15px;
            text-align: center;
            color: #ff6b6b;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            animation: popIn 1s forwards;
        }

        @keyframes popIn {
            0% { transform: translate(-50%, -50%) scale(0); opacity: 0; }
            70% { transform: translate(-50%, -50%) scale(1.1); opacity: 1; }
            100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
        }

        .fireworks {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .firework {
            position: absolute;
            width: 5px;
            height: 5px;
            border-radius: 50%;
            animation: explode 1s forwards;
        }

        @keyframes explode {
            0% { transform: translateY(0) scale(1); opacity: 1; }
            100% { transform: translateY(-100px) scale(0); opacity: 0; }
        }

        /* New styles for the animated girl */
        .girl-container {
            position: absolute;
            bottom: 100px;
            left: 10%;
            animation: moveGirl 15s infinite ease-in-out;
            z-index: 10;
        }

        .girl {
            width: 80px;
            height: 120px;
            position: relative;
            transform-origin: bottom center;
        }

        .girl-body {
            width: 40px;
            height: 60px;
            background: #ff9eb5;
            border-radius: 20px 20px 0 0;
            position: absolute;
            bottom: 0;
            left: 20px;
        }

        .girl-head {
            width: 50px;
            height: 50px;
            background: #ffd1dc;
            border-radius: 50%;
            position: absolute;
            bottom: 60px;
            left: 15px;
        }

        .girl-hair {
            width: 60px;
            height: 30px;
            background: #8B4513;
            border-radius: 50% 50% 0 0;
            position: absolute;
            bottom: 85px;
            left: 10px;
        }

        .girl-eye {
            width: 8px;
            height: 8px;
            background: #333;
            border-radius: 50%;
            position: absolute;
        }

        .girl-eye.left {
            bottom: 80px;
            left: 25px;
        }

        .girl-eye.right {
            bottom: 80px;
            left: 45px;
        }

        .girl-mouth {
            width: 15px;
            height: 5px;
            background: #ff6b6b;
            border-radius: 0 0 10px 10px;
            position: absolute;
            bottom: 70px;
            left: 32px;
        }

        .girl-dress {
            width: 50px;
            height: 40px;
            background: #ff6b6b;
            border-radius: 10px 10px 0 0;
            position: absolute;
            bottom: 20px;
            left: 15px;
        }

        .girl-arm {
            width: 8px;
            height: 40px;
            background: #ffd1dc;
            position: absolute;
            bottom: 50px;
            border-radius: 4px;
        }

        .girl-arm.left {
            left: 10px;
            transform-origin: top center;
            animation: waveArm 3s infinite ease-in-out;
        }

        .girl-arm.right {
            right: 10px;
        }

        .girl-leg {
            width: 10px;
            height: 40px;
            background: #ffd1dc;
            position: absolute;
            bottom: -40px;
            border-radius: 5px 5px 0 0;
        }

        .girl-leg.left {
            left: 25px;
        }

        .girl-leg.right {
            right: 25px;
        }

        @keyframes moveGirl {
            0%, 100% {
                left: 10%;
                transform: scaleX(1);
            }
            25% {
                left: 30%;
                transform: scaleX(1);
            }
            50% {
                left: 60%;
                transform: scaleX(-1);
            }
            75% {
                left: 40%;
                transform: scaleX(-1);
            }
        }

        @keyframes waveArm {
            0%, 100% {
                transform: rotate(0deg);
            }
            50% {
                transform: rotate(-20deg);
            }
        }

        .girl-speech-bubble {
            position: absolute;
            bottom: 150px;
            left: 50%;
            transform: translateX(-50%);
            background: white;
            padding: 10px 15px;
            border-radius: 20px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.2);
            font-size: 14px;
            color: #ff6b6b;
            opacity: 0;
            animation: showSpeech 15s infinite ease-in-out;
            width: 180px;
            text-align: center;
        }

        .girl-speech-bubble:after {
            content: '';
            position: absolute;
            top: 100%;
            left: 50%;
            transform: translateX(-50%);
            border: 10px solid transparent;
            border-top-color: white;
        }

        @keyframes showSpeech {
            0%, 100% {
                opacity: 0;
            }
            10%, 30% {
                opacity: 1;
            }
            40%, 60% {
                opacity: 0;
            }
            70%, 90% {
                opacity: 1;
            }
        }

        .attraction-line {
            position: absolute;
            top: 20%;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(255, 255, 255, 0.9);
            padding: 15px 25px;
            border-radius: 30px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            font-size: 18px;
            color: #ff6b6b;
            text-align: center;
            opacity: 0;
            animation: fadeInOut 8s infinite;
            max-width: 80%;
        }

        @keyframes fadeInOut {
            0%, 100% {
                opacity: 0;
                transform: translateX(-50%) translateY(-20px);
            }
            20%, 80% {
                opacity: 1;
                transform: translateX(-50%) translateY(0);
            }
        }
    </style>
</head>
<body>
    <!-- Password Section -->
    <div id="password-container">
        <h2>Enter the Secret Code</h2>
        <p>(Hint: Our special date in DDMMYYYY format)</p>
        <input type="password" id="password-input" placeholder="Enter password">
        <button id="submit-btn">Enter</button>
        <p id="error-message">Incorrect password. Please try again.</p>
    </div>

    <!-- Proposal Section -->
    <div id="proposal-container">
        <!-- Attraction lines -->
        <div class="attraction-line" id="attraction-line-1">Every moment with you feels like a beautiful dream!</div>
        <div class="attraction-line" id="attraction-line-2" style="animation-delay: 4s;">Your smile lights up my world!</div>
        
        <!-- Animated girl -->
        <div class="girl-container">
            <div class="girl">
                <div class="girl-hair"></div>
                <div class="girl-head"></div>
                <div class="girl-body"></div>
                <div class="girl-dress"></div>
                <div class="girl-eye left"></div>
                <div class="girl-eye right"></div>
                <div class="girl-mouth"></div>
                <div class="girl-arm left"></div>
                <div class="girl-arm right"></div>
                <div class="girl-leg left"></div>
                <div class="girl-leg right"></div>
            </div>
            <div class="girl-speech-bubble">
                You make my heart skip a beat!
            </div>
        </div>

        <div class="message">
            <h1>My Dearest Tamanna,</h1>
            <p>From the moment I met you, my life has been filled with joy, laughter, and love. You are the most amazing person I've ever known, and I can't imagine my future without you.</p>
            <p>Will you make me the happiest person in the world and marry me?</p>
            <div class="buttons">
                <button id="yes-btn">Yes, I will!</button>
                <button id="no-btn">No</button>
            </div>
        </div>
        <div class="flowers">
            <div class="flower">
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal center"></div>
                <div class="stem"></div>
            </div>
            <div class="flower">
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal center"></div>
                <div class="stem"></div>
            </div>
            <div class="flower">
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal center"></div>
                <div class="stem"></div>
            </div>
            <div class="flower">
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal center"></div>
                <div class="stem"></div>
            </div>
            <div class="flower">
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal"></div>
                <div class="petal center"></div>
                <div class="stem"></div>
            </div>
        </div>
        <div class="final-message">
            <h1>You've Made Me The Happiest Person!</h1>
            <p>I love you more than words can express, Tamanna. I can't wait to spend the rest of my life with you!</p>
            <p>❤️ Forever Yours ❤️</p>
        </div>
        <div class="fireworks"></div>
    </div>

    <script>
        // Set the password (change this to your special date)
        const correctPassword = "sharmaji"; // Format: DDMMYYYY

        // DOM Elements
        const passwordContainer = document.getElementById('password-container');
        const proposalContainer = document.getElementById('proposal-container');
        const passwordInput = document.getElementById('password-input');
        const submitBtn = document.getElementById('submit-btn');
        const errorMessage = document.getElementById('error-message');
        const yesBtn = document.getElementById('yes-btn');
        const noBtn = document.getElementById('no-btn');
        const finalMessage = document.querySelector('.final-message');
        const fireworksContainer = document.querySelector('.fireworks');

        // Password Check
        submitBtn.addEventListener('click', checkPassword);
        passwordInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                checkPassword();
            }
        });

        function checkPassword() {
            if (passwordInput.value === correctPassword) {
                passwordContainer.style.display = 'none';
                proposalContainer.style.display = 'block';
                createHearts();
            } else {
                errorMessage.style.display = 'block';
                passwordInput.value = '';
                passwordInput.focus();
            }
        }

        // Create floating hearts
        function createHearts() {
            for (let i = 0; i < 20; i++) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.animationDelay = Math.random() * 5 + 's';
                heart.style.width = Math.random() * 20 + 10 + 'px';
                heart.style.height = heart.style.width;
                proposalContainer.appendChild(heart);
            }
        }

        // Yes button click
        yesBtn.addEventListener('click', function() {
            document.querySelector('.message').style.display = 'none';
            finalMessage.style.display = 'block';
            createFireworks();
        });

        // No button behavior
        noBtn.addEventListener('mouseover', function() {
            const x = Math.random() * (window.innerWidth - 100);
            const y = Math.random() * (window.innerHeight - 50);
            noBtn.style.position = 'absolute';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
        });

        // Create fireworks
        function createFireworks() {
            for (let i = 0; i < 50; i++) {
                setTimeout(() => {
                    const firework = document.createElement('div');
                    firework.classList.add('firework');
                    firework.style.left = Math.random() * 100 + 'vw';
                    firework.style.top = Math.random() * 100 + 'vh';
                    firework.style.backgroundColor = getRandomColor();
                    fireworksContainer.appendChild(firework);
                    
                    setTimeout(() => {
                        firework.remove();
                    }, 1000);
                }, i * 100);
            }
        }

        function getRandomColor() {
            const colors = ['#ff6b6b', '#4CAF50', '#2196F3', '#FFC107', '#9C27B0'];
            return colors[Math.floor(Math.random() * colors.length)];
        }
    </script>
</body>
</html>
