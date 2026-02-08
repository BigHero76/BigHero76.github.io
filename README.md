<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bouncing Image</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: white;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            font-family: Arial, sans-serif;
            overflow: hidden;
        }

        .container {
            text-align: center;
            position: relative;
            z-index: 10;
        }

        h1 {
            font-size: 2.5em;
            margin-bottom: 30px;
            color: #333;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        h1.show {
            opacity: 1;
        }

        button {
            padding: 12px 30px;
            font-size: 1.1em;
            background-color: #ff6b9d;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: background-color 0.3s ease;
            position: relative;
            z-index: 10;
        }

        button:hover {
            background-color: #ff5a8c;
        }

        button:active {
            transform: scale(0.98);
        }

        .animation-container {
            position: fixed;
            top: 50%;
            left: -200px;
            transform: translateY(-50%);
            z-index: 5;
        }

        .animation-container img {
            width: 150px;
            height: 150px;
            object-fit: cover;
            display: block;
        }

        @keyframes slideToRight {
            0% {
                left: -200px;
            }
            100% {
                left: calc(100vw);
            }
        }

        @keyframes bounce {
            0%, 100% {
                transform: translateY(0);
            }
            25% {
                transform: translateY(-60px);
            }
            50% {
                transform: translateY(0);
            }
            75% {
                transform: translateY(-30px);
            }
        }

        .bounce-animation {
            animation: slideToRight 6s linear forwards, bounce 0.6s ease-in-out infinite;
        }

        audio {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 id="text">you're cute fr</h1>
        <button onclick="startBouncing()">Click Me!</button>
    </div>

    <div class="animation-container" id="animationContainer">
        <img id="bouncingImage" src="" alt="Bouncing Image">
    </div>

    <audio id="audio"></audio>

    <script>
        function startBouncing() {
            const text = document.getElementById('text');
            const audio = document.getElementById('audio');
            const animationContainer = document.getElementById('animationContainer');

            text.classList.add('show');

            if (audio.src) {
                audio.play().catch(err => console.log('Audio play failed:', err));
            }

            animationContainer.classList.remove('bounce-animation');
            void animationContainer.offsetWidth; 
            animationContainer.classList.add('bounce-animation');

            
            setTimeout(() => {
                animationContainer.classList.remove('bounce-animation');
            }, 6500);
        }

        document.getElementById('bouncingImage').src = 'emoji.webp.webp';
        document.getElementById('audio').src = 'champagne.mp3.mp3';
    </script>
</body>
</html>
