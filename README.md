<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sonic Plinko Stars</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #0e1a47;
            color: #fff;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        #header {
            display: flex;
            justify-content: space-between;
            width: 100%;
            padding: 20px;
            background-color: #ffcc00;
            color: #0e1a47;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }

        #balance-section h2, #cashout-section button {
            margin: 0;
            padding: 5px 10px;
        }

        #cashout-btn {
            background-color: #ff6600;
            color: white;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
        }

        #cashout-btn:hover {
            background-color: #e65c00;
        }

        #progress-section {
            margin-top: 30px;
            text-align: center;
            width: 80%;
        }

        progress {
            width: 100%;
            height: 30px;
            margin-top: 10px;
            border-radius: 10px;
        }

        #game-area {
            margin-top: 40px;
            text-align: center;
        }

        #play-btn {
            background-color: #00bfff;
            color: white;
            padding: 15px 30px;
            border: none;
            cursor: pointer;
            font-size: 18px;
            border-radius: 10px;
        }

        #play-btn:hover {
            background-color: #008fb3;
        }
    </style>
</head>
<body>
    <!-- Header Section -->
    <div id="header">
        <div id="balance-section">
            <h2>Balance: £<span id="balance">0.00</span></h2>
        </div>
        <div id="cashout-section">
            <button id="cashout-btn" disabled>Cash Out</button>
        </div>
    </div>

    <!-- Progress Bar Section -->
    <div id="progress-section">
        <progress id="progress-bar" value="0" max="10"></progress>
        <p>Progress: £<span id="progress-value">0.00</span> / £10.00</p>
    </div>

    <!-- Game Area -->
    <div id="game-area">
        <h1>Drop Your Sonic Ring!</h1>
        <button id="play-btn">Play</button>
    </div>

    <script>
        let balance = 0.00;  // Initial balance
        let progressBar = document.getElementById("progress-bar");
        let balanceElement = document.getElementById("balance");
        let progressValueElement = document.getElementById("progress-value");

        // Play button function
        document.getElementById("play-btn").addEventListener("click", function() {
            let winAmount = (Math.random() * 1.00 + 0.10).toFixed(2); // Win between £0.10 and £1.00
            balance += parseFloat(winAmount);
            progressBar.value = balance;  // Update progress bar
            balanceElement.textContent = balance.toFixed(2);  // Update balance display
            progressValueElement.textContent = balance.toFixed(2); // Update progress value

            // Check if the player has reached £10 to allow cashout
            if (balance >= 10.00) {
                alert("Congratulations! You've reached £10.00. You can now cash out!");
                document.getElementById("cashout-btn").disabled = false;  // Enable cashout button
            }
        });

        // Cashout button function
        document.getElementById("cashout-btn").addEventListener("click", function() {
            // Here, the cashout link could be customized to redirect the user to PayPal
            window.location.href = "https://www.paypal.com";  // Redirect to PayPal (example link)
        });
    </script>
</body>
</html>
