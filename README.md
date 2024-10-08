<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Lisa</title>
    <style>
        body {
            background-color: pink;
            font-family: Arial, sans-serif;
            text-align: center;
            overflow: hidden; /* Prevents scrollbars */
        }

        h1 {
            font-size: 3em;
            margin-top: 20%;
            color: red;
            display: none;
        }

        p {
            font-size: 1.5em;
            display: none;
        }

        .hearts {
            font-size: 2em;
            color: red;
            margin-top: 20px;
            display: none;
        }

        /* Explosion piece style */
        .explosion-piece {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            border-radius: 50%;
            opacity: 1;
            animation: explode-chaos 3s ease-out forwards;
        }

        @keyframes explode-chaos {
            0% {
                transform: translate(0, 0) scale(1);
                opacity: 1;
            }
            100% {
                transform: translate(var(--x-dir), var(--y-dir)) scale(0.1);
                opacity: 0;
            }
        }

        /* Stationary heart in the top right corner */
        .moving-heart {
            position: fixed;
            top: 20px;
            right: 20px;
            font-size: 300px; /* Adjust size as needed */
            color: red;
        }

        /* Heart in the bottom left */
        .bottom-left-heart {
            position: fixed;
            bottom: 20px;
            left: 20px;
            font-size: 300px; /* Adjust size as needed */
            color: red;
        }

        /* Confetti styles */
        .confetti {
            position: fixed;
            top: 0;
            width: 10px;
            height: 20px;
            animation: fall 3s linear infinite;
            opacity: 0.8;
        }

        @keyframes fall {
            0% {
                transform: translateY(0) rotate(0deg);
            }
            100% {
                transform: translateY(100vh) rotate(360deg);
            }
        }

        /* Button styling */
        .gift-button {
            display: none; /* Initially hidden */
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 20px;
            background-color: red;
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
        }

        /* Image styles (hidden initially, centered) */
        .gift-image {
            display: none;
            width: 50px;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            transition: width 3s ease-in-out; /* Smooth grow effect */
        }

        /* Second image styles (hidden initially, positioned in the top left) */
        .gift-image-2 {
            display: none;
            width: 50px;
            position: fixed;
            top: 250px; /* Positioned lower from the top */
            left: 200px; /* Adjusted to bring it more to the center */
            transform: translate(-50%, -50%);
            transition: width 3s ease-in-out; /* Smooth grow effect */
        }

        /* Third image styles (hidden initially, positioned in the bottom right) */
        .gift-image-3 {
            display: none;
            width: 50px;
            position: fixed;
            bottom: -50px; /* Positioned near the bottom */
            right: -100px; /* Positioned near the right */
            transform: translate(-50%, -50%);
            transition: width 3s ease-in-out; /* Smooth grow effect */
        }
    </style>
</head>
<body>

    <!-- Content after explosion -->
    <h1>Happy Birthday Lisa!</h1>
    <p>You are the best!</p>
    <div class="hearts">❤️❤️❤️❤️❤️❤️❤️</div>

    <!-- Stationary heart in the top right -->
    <div class="moving-heart">&#10084;</div> 

    <!-- Stationary heart in the bottom left -->
    <div class="bottom-left-heart">&#10084;</div>

    <!-- "Gschänkli" button -->
    <button class="gift-button" onclick="showGift()">Gschänkli</button>

    <!-- Hidden gift images (centered, top left, and bottom right) -->
    <img class="gift-image" src="https://www.zauberwald.ch/wp-content/uploads/2023/11/ZW_2022_NOA_OMEN_01_CemilErkoc_1920x1280mC.jpg" alt="Gschänkli">
    <img class="gift-image-2" src="https://www.openairguide.net/img/1200/zauberwald-lenzerheide.jpg" alt="Zauberwald Lenzerheide">
    <img class="gift-image-3" src="https://i.scdn.co/image/ab67616d00001e02c600152326191d7a6137899c" alt="Gschänkli Image 3">

    <script>
        function createExplosion() {
            const numPieces = 50;
            const centerX = window.innerWidth / 2;
            const centerY = window.innerHeight / 2;

            for (let i = 0; i < numPieces; i++) {
                let piece = document.createElement('div');
                piece.classList.add('explosion-piece');

                let xDir = (Math.random() - 0.5) * 2500 + 'px';
                let yDir = (Math.random() - 0.5) * 2500 + 'px';

                piece.style.setProperty('--x-dir', xDir);
                piece.style.setProperty('--y-dir', yDir);

                piece.style.width = Math.random() * 30 + 10 + 'px';
                piece.style.height = piece.style.width;

                piece.style.left = centerX + 'px';
                piece.style.top = centerY + 'px';

                document.body.appendChild(piece);

                setTimeout(() => piece.remove(), 3000);
            }
        }

        function createConfetti() {
            for (let i = 0; i < 100; i++) {
                let confetti = document.createElement('div');
                confetti.classList.add('confetti');

                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.backgroundColor = `hsl(${Math.random() * 360}, 100%, 50%)`;
                confetti.style.animationDuration = Math.random() * 3 + 2 + 's';

                document.body.appendChild(confetti);
            }
        }

        // Function to show gift images and animate their growth
        function showGift() {
            const giftImage1 = document.querySelector('.gift-image');
            const giftImage2 = document.querySelector('.gift-image-2');
            const giftImage3 = document.querySelector('.gift-image-3'); // New third image

            giftImage1.style.display = 'block';
            giftImage2.style.display = 'block';
            giftImage3.style.display = 'block'; // Display the third image

            setTimeout(() => {
                giftImage1.style.width = '600px'; // First image grows bigger
                giftImage2.style.width = '600px'; // Second image grows bigger
                giftImage3.style.width = '400px'; // Third image grows bigger
            }, 100); // Delay for animation
        }

        window.onload = function() {
            createExplosion();

            const content = document.querySelectorAll('h1, p, .hearts');

            setTimeout(function() {
                content.forEach(function(el) {
                    el.style.display = 'block';
                });

                createConfetti();

                // Show the "Gschänkli" button after 8 seconds
                setTimeout(() => {
                    document.querySelector('.gift-button').style.display = 'inline-block';
                }, 5000);
            }, 3000);
        };
    </script>

</body>
</html>
