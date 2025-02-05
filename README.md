# Valentine
Valentine
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine's Special</title>
    <style>
        body {
            text-align: center;
            font-family: Arial, sans-serif;
            background-color: #ffebee;
            overflow: hidden;
        }

        /* Curtain Animation */
        .curtain {
            position: fixed;
            top: 0;
            width: 50%;
            height: 100vh;
            background: linear-gradient(to right, red, darkred);
            z-index: 1000;
        }

        .curtain-left {
            left: 0;
            animation: openLeft 2.5s ease-out forwards;
        }

        .curtain-right {
            right: 0;
            background: linear-gradient(to left, red, darkred);
            animation: openRight 2.5s ease-out forwards;
        }

        @keyframes openLeft {
            0% { left: 0; }
            100% { left: -50%; }
        }

        @keyframes openRight {
            0% { right: 0; }
            100% { right: -50%; }
        }

        /* Moving Text (Hallinu) */
        .moving-text {
            display: inline-block;
            font-size: 28px;
            font-weight: bold;
            color: red;
            text-transform: uppercase;
            animation: moveText 3s ease-in-out infinite alternate;
        }

        @keyframes moveText {
            0% { transform: translateX(-30px); }
            100% { transform: translateX(30px); }
        }

        /* Floating Hearts */
        .heart-border {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
        }

        .heart {
            position: absolute;
            font-size: 20px;
            color: red;
            animation: floatHearts 5s infinite linear;
        }

        .heart::before { content: "❤️"; }

        @keyframes floatHearts {
            0% { transform: translateY(100vh) scale(0.5); opacity: 1; }
            100% { transform: translateY(-10vh) scale(1.5); opacity: 0; }
        }

        /* Random Heart Positions */
        .heart:nth-child(1) { left: 10%; animation-duration: 4s; }
        .heart:nth-child(2) { left: 25%; animation-duration: 6s; }
        .heart:nth-child(3) { left: 40%; animation-duration: 5s; }
        .heart:nth-child(4) { left: 55%; animation-duration: 7s; }
        .heart:nth-child(5) { left: 70%; animation-duration: 4.5s; }
        .heart:nth-child(6) { left: 85%; animation-duration: 5.5s; }

        /* Gradient Text */
        h1 {
            font-size: 30px;
            font-weight: bold;
            background-image: linear-gradient(to right, red, orange, yellow, green, blue, indigo, violet);
            -webkit-background-clip: text;
            color: transparent;
        }

        /* Countdown Timer */
        .countdown-text {
            font-size: 24px;
            font-weight: bold;
            color: blue;
            margin: 10px 0;
        }

        /* Valentine's Day Text */
        .valentine-text {
            font-size: 28px;
            font-weight: bold;
            color: black;
        }

        /* Image Styling */
        .image-container {
            margin: 20px 0;
        }

        .image-container img {
            width: 250px;
            border-radius: 10px;
        }

        /* Input Field */
        .name-input {
            padding: 10px;
            border: 2px solid black;
            font-size: 16px;
            width: 80%;
            max-width: 300px;
            text-align: center;
        }

        /* GO Button */
        .go-button {
            background-color: green;
            color: white;
            padding: 10px;
            border: none;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <!-- Curtain Effect -->
    <div class="curtain curtain-left"></div>
    <div class="curtain curtain-right"></div>

    <!-- Floating Hearts -->
    <div class="heart-border">
        <span class="heart"></span>
        <span class="heart"></span>
        <span class="heart"></span>
        <span class="heart"></span>
        <span class="heart"></span>
        <span class="heart"></span>
    </div>

    <!-- Dynamic Name Display -->
    <h1 id="displayName">Your Name Here</h1>

    <!-- Moving Wishing Text -->
    <h2 class="moving-text">Wishing You</h2>

    <!-- Countdown Timer -->
    <p class="countdown-text" id="countdownTimer">Loading...</p>

    <!-- Moving Valentine's Day Message -->
    <h1 class="valentine-text moving-text">HAPPY VALENTINE'S DAY</h1>

    <!-- Image with Link -->
    <div class="image-container">
        <a href="https://ibb.co/g5dF5Xw" target="_blank">
            <img src="https://i.ibb.co/HWCpWMY/pngtree-a-couple-proposing-with-red-rose-on-valentine-day-boy-knee-png-image-16994497.png" 
                 alt="Valentine Image">
        </a>
    </div>

    <!-- Name Input Field -->
    <input type="text" class="name-input" id="nameInput" placeholder="Enter Your Name Here...">
    
    <!-- GO Button -->
    <button class="go-button">GO</button>

    <script>
        // Update the name in real-time
        document.getElementById("nameInput").addEventListener("input", function() {
            let inputName = this.value.trim();
            document.getElementById("displayName").innerText = inputName ? inputName : "Your Name Here";
        });

        // Countdown Timer
        function startCountdown() {
            let targetDate = new Date("February 14, " + new Date().getFullYear() + " 00:00:00").getTime();
            
            let timer = setInterval(function() {
                let now = new Date().getTime();
                let timeLeft = targetDate - now;

                if (timeLeft <= 0) {
                    clearInterval(timer);
                    document.getElementById("countdownTimer").innerText = "Happy Valentine's Day!";
                    return;
                }

                let days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
                let hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                let minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
                let seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);

                document.getElementById("countdownTimer").innerText = `${days}d ${hours}h ${minutes}m ${seconds}s`;
            }, 1000);
        }

        // Start countdown on load
        startCountdown();
    </script>

</body>
</html>
