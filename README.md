````
<!DOCTYPE html>
<html>
<head>
    <title>Bouncing Image Example</title>
    <style>
        .bouncy {
            position: relative;
            animation: bounce 2s infinite;
        }
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateY(0);
            }
            40% {
                transform: translateY(-30px);
            }
            60% {
                transform: translateY(-15px);
            }
        }
    </style>
</head>
<body>
    <h1>Bouncing Image Example</h1>
    <img src="your-image-url.jpg" alt="Bouncing Image" class="bouncy" width="300" />
</body>
</html>
````