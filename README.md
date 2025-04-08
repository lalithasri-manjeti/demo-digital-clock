<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Futuristic Digital Clock</title>
    <style>
        /* Reset margin and padding */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* Body styling */
        body {
            background: #141414;
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            color: #fff;
            overflow: hidden;
        }

        /* Container for clock and date */
        .clock-container {
            text-align: center;
            animation: fadeIn 1s ease-out;
        }

        /* Styling for the clock */
        .clock {
            font-size: 90px;
            font-weight: 900;
            letter-spacing: 8px;
            color: #fff;
            padding: 20px;
            background: #222;
            border-radius: 20px;
            text-transform: uppercase;
            box-shadow: 0 0 10px rgba(0, 255, 255, 1), 0 0 20px rgba(0, 255, 255, 1), 0 0 40px rgba(0, 255, 255, 1);
            animation: glowing 1.5s ease-in-out infinite alternate;
        }

        /* Styling for the date */
        .date {
            font-size: 24px;
            margin-top: 10px;
            color: #ccc;
            text-shadow: 0 0 5px rgba(255, 255, 255, 0.5), 0 0 10px rgba(255, 255, 255, 0.5);
        }

        /* Animation for glowing effect */
        @keyframes glowing {
            0% {
                text-shadow: 0 0 10px rgba(0, 255, 255, 1), 0 0 20px rgba(0, 255, 255, 1), 0 0 30px rgba(0, 255, 255, 1);
            }
            100% {
                text-shadow: 0 0 20px rgba(0, 255, 255, 1), 0 0 40px rgba(0, 255, 255, 1), 0 0 50px rgba(0, 255, 255, 1);
            }
        }

        /* Animation for fade-in effect */
        @keyframes fadeIn {
            0% {
                opacity: 0;
                transform: translateY(50px);
            }
            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }
    </style>
</head>
<body>
    <div class="clock-container">
        <div id="clock" class="clock"></div>
        <div id="date" class="date"></div>
    </div>

    <script>
        // Function to update the clock
        function updateClock() {
            const clockElement = document.getElementById('clock');
            const dateElement = document.getElementById('date');

            const now = new Date();

            // Format hours, minutes, and seconds
            const hours = now.getHours().toString().padStart(2, '0');
            const minutes = now.getMinutes().toString().padStart(2, '0');
            const seconds = now.getSeconds().toString().padStart(2, '0');

            // Display time
            clockElement.textContent = `${hours}:${minutes}:${seconds}`;

            // Format date (Day, Month Date, Year)
            const options = { weekday: 'long', month: 'long', day: 'numeric', year: 'numeric' };
            const formattedDate = now.toLocaleDateString('en-US', options);

            // Display date
            dateElement.textContent = formattedDate;
        }

        // Call updateClock every second
        setInterval(updateClock, 1000);

        // Initialize clock when page loads
        window.onload = updateClock;
    </script>
</body>
</html>
