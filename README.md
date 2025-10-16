        <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Heart's Secret</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Georgia', serif;
        }
        
        body {
            background: linear-gradient(135deg, #ffafbd, #ffc3a0);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }
        
        .container {
            width: 100%;
            max-width: 800px;
            text-align: center;
            padding: 20px;
        }
        
        /* Password Screen */
        #password-screen {
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            animation: fadeIn 1s ease;
        }
        
        #password-screen h1 {
            color: #d63384;
            margin-bottom: 20px;
            font-size: 2.5rem;
        }
        
        #password-screen p {
            color: #555;
            margin-bottom: 30px;
            font-size: 1.2rem;
        }
        
        .password-input {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
        }
        
        #password {
            padding: 12px 20px;
            border: 2px solid #ffafbd;
            border-radius: 50px;
            width: 70%;
            font-size: 1.1rem;
            outline: none;
            transition: all 0.3s;
        }
        
        #password:focus {
            border-color: #d63384;
            box-shadow: 0 0 10px rgba(214, 51, 132, 0.3);
        }
        
        #submit-password {
            background: linear-gradient(to right, #ffafbd, #d63384);
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 50px;
            cursor: pointer;
            font-size: 1.1rem;
            margin-left: 10px;
            transition: all 0.3s;
        }
        
        #submit-password:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(214, 51, 132, 0.4);
        }
        
        #error-message {
            color: #ff4d4d;
            margin-top: 10px;
            font-weight: bold;
            display: none;
        }
        
        /* Main Content */
        #main-content {
            display: none;
            animation: fadeIn 1.5s ease;
        }
        
        .header {
            margin-bottom: 40px;
        }
        
        .header h1 {
            color: #d63384;
            font-size: 3rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .header p {
            color: #555;
            font-size: 1.3rem;
        }
        
        .poem-container {
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            padding: 40px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        .poem-title {
            color: #d63384;
            margin-bottom: 20px;
            font-size: 1.8rem;
        }
        
        .poem {
            font-size: 1.3rem;
            line-height: 1.8;
            color: #333;
            text-align: left;
            white-space: pre-line;
        }
        
        .proposal-section {
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
        }
        
        .proposal-section h2 {
            color: #d63384;
            margin-bottom: 20px;
            font-size: 2.2rem;
        }
        
        .proposal-text {
            font-size: 1.5rem;
            line-height: 1.6;
            color: #333;
            margin-bottom: 30px;
        }
        
        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
        }
        
        .btn {
            padding: 15px 40px;
            border: none;
            border-radius: 50px;
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        #yes-btn {
            background: linear-gradient(to right, #56ab2f, #a8e063);
            color: white;
        }
        
        #no-btn {
            background: linear-gradient(to right, #ff416c, #ff4b2b);
            color: white;
        }
        
        .btn:hover {
            transform: scale(1.1);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .hearts {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            z-index: -1;
        }
        
        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background: #ff4d79;
            transform: rotate(45deg);
            opacity: 0.7;
            animation: float 5s infinite ease-in-out;
        }
        
        .heart:before,
        .heart:after {
            content: '';
            width: 20px;
            height: 20px;
            background: #ff4d79;
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
        
        .response-message {
            display: none;
            margin-top: 30px;
            font-size: 2rem;
            color: #d63384;
            font-weight: bold;
            animation: pulse 1.5s infinite;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(45deg); }
            50% { transform: translateY(-20px) rotate(45deg); }
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }
            
            .header h1 {
                font-size: 2.2rem;
            }
            
            .poem-container, .proposal-section {
                padding: 20px;
            }
            
            .poem {
                font-size: 1.1rem;
            }
            
            .buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 80%;
                margin-bottom: 10px;
            }
        }
    </style>
</head>
<body>
    <div class="hearts" id="hearts-container"></div>
    
    <div class="container">
        <!-- Password Screen -->
        <div id="password-screen">
            <h1>My Heart's Secret</h1>
            <p>Enter the password to unlock my heart's message for you</p>
            <div class="password-input">
                <input type="password" id="password" placeholder="Enter our special word...">
                <button id="submit-password">Unlock</button>
            </div>
            <p id="error-message">Incorrect password. Please try again.</p>
        </div>
        
        <!-- Main Content (Hidden until password is correct) -->
        <div id="main-content">
            <div class="header">
                <h1>For My Beloved</h1>
                <p>A message from my heart to yours</p>
            </div>
            
            <div class="poem-container">
                <h2 class="poem-title">My Love For You</h2>
                <div class="poem" id="poem-text">
                    In your eyes, I found my home,
                    A place where my heart no longer roams.
                    Your smile, a light that guides my way,
                    Brightening even my darkest day.
                    
                    Your laughter is my favorite song,
                    A melody to which I belong.
                    In your embrace, I've found my peace,
                    Where all my worries and fears cease.
                    
                    With every beat, my heart does say,
                    I'll love you more with each passing day.
                    You are the dream I never knew I had,
                    The greatest joy, making my heart glad.
                </div>
            </div>
            
            <div class="proposal-section">
                <h2>The Most Important Question</h2>
                <p class="proposal-text">
                    My dearest love, from the moment we met, 
                    my life has been brighter, fuller, and more beautiful. 
                    You've shown me what true happiness means, 
                    and I can't imagine my future without you in it.
                    
                    Will you make me the happiest person alive and be my forever?
                </p>
                
                <div class="buttons">
                    <button class="btn" id="yes-btn">Yes, Forever!</button>
                    <button class="btn" id="no-btn">No</button>
                </div>
                
                <div class="response-message" id="response-yes">
                    You've made me the happiest person in the world! I love you!
                </div>
                <div class="response-message" id="response-no">
                    Please reconsider! My heart belongs only to you!
                </div>
            </div>
        </div>
    </div>

    <script>
        // Create floating hearts
        function createHearts() {
            const heartsContainer = document.getElementById('hearts-container');
            for (let i = 0; i < 15; i++) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.animationDelay = Math.random() * 5 + 's';
                heartsContainer.appendChild(heart);
            }
        }
        
        // Password verification
        document.getElementById('submit-password').addEventListener('click', function() {
            const password = document.getElementById('password').value.toLowerCase();
            // Change this password to something meaningful for you both
            const correctPassword = "forever"; 
            
            if (password === correctPassword) {
                document.getElementById('password-screen').style.display = 'none';
                document.getElementById('main-content').style.display = 'block';
            } else {
                document.getElementById('error-message').style.display = 'block';
            }
        });
        
        // Allow pressing Enter to submit password
        document.getElementById('password').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                document.getElementById('submit-password').click();
            }
        });
        
        // Proposal response buttons
        document.getElementById('yes-btn').addEventListener('click', function() {
            document.getElementById('response-yes').style.display = 'block';
            document.getElementById('response-no').style.display = 'none';
            createFireworks();
        });
        
        document.getElementById('no-btn').addEventListener('click', function() {
            document.getElementById('response-no').style.display = 'block';
            document.getElementById('response-yes').style.display = 'none';
            
            // Move the "No" button randomly when hovered
            const noBtn = document.getElementById('no-btn');
            noBtn.addEventListener('mouseover', function() {
                const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
                const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
                noBtn.style.position = 'absolute';
                noBtn.style.left = x + 'px';
                noBtn.style.top = y + 'px';
            });
        });
        
        // Simple fireworks effect for "Yes" response
        function createFireworks() {
            const colors = ['#ff4d79', '#ffafbd', '#d63384', '#ffc3a0', '#ff6b6b'];
            const container = document.querySelector('.container');
            
            for (let i = 0; i < 50; i++) {
                setTimeout(() => {
                    const firework = document.createElement('div');
                    firework.classList.add('heart');
                    firework.style.left = Math.random() * 100 + 'vw';
                    firework.style.top = Math.random() * 100 + 'vh';
                    firework.style.background = colors[Math.floor(Math.random() * colors.length)];
                    firework.style.width = '15px';
                    firework.style.height = '15px';
                    container.appendChild(firework);
                    
                    setTimeout(() => {
                        firework.remove();
                    }, 3000);
                }, i * 100);
            }
        }
        
        // Initialize the page
        window.onload = function() {
            createHearts();
        };
    </script>
</body>
</html>
