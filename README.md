<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jackpot Game</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
            background-color: black;
            color: white;
        }
        h1 {
            color: yellow;
        }
        #game-container {
            display: flex;
            justify-content: space-around;
            align-items: center;
            margin-top: 30px;
        }
        .slot-container {
            width: 120px;
            height: 120px;
            border: 5px solid white;
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }
        .slot {
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 24px;
            font-weight: bold;
            color: white;
            background-color: #333;
            border-radius: 5px;
            position: absolute;
        }
        #result {
            font-size: 20px;
            margin-top: 20px;
        }
        #jackpot-container {
            position: relative;
        }
        #jackpot {
            width: 100px;
            height: 100px;
            background-color: red;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 24px;
            font-weight: bold;
            color: white;
        }
        @keyframes spin {
            0% { transform: translateY(0); }
            25% { transform: translateY(-200%); }
            50% { transform: translateY(-400%); }
            75% { transform: translateY(-600%); }
            100% { transform: translateY(-800%); }
        }
        #footer-message {
            position: fixed;
            bottom: 10px;
            right: 10px;
            color: red;
            font-size: 12px;
        }
    </style>
</head>
<body>

<h1>Welcome to the Jackpot Game!</h1>

<script>
    // First alert
    const ageConfirmation = confirm("Are you above 21 years old?");
    if (!ageConfirmation) {
        alert("You must be above 21 years old to access this game. Please leave the site.");
        throw new Error("User is not above 21 years old");
    }

    // Second alert
    const betDangerConfirmation = confirm("Betting can be dangerous. Are you sure about that?");
    if (!betDangerConfirmation) {
        alert("You've decided not to proceed with the bet. It's a wise choice.");
        throw new Error("User is not sure about the bet");
    }

    // Third alert
    const addictionWarningConfirmation = confirm("Betting can be addictive and may lead to financial loss. Are you sure you want to proceed?");
    if (!addictionWarningConfirmation) {
        alert("You've decided not to proceed. It's a responsible decision. Please be cautious.");
        throw new Error("User is not sure about proceeding with the game");
    } <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jackpot Game</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
            background-color: black;
            color: white;
        }
        h1 {
            color: yellow;
        }
        #game-container {
            display: flex;
            justify-content: space-around;
            align-items: center;
            margin-top: 30px;
        }
        .slot-container {
            width: 120px;
            height: 120px;
            border: 5px solid white;
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }
        .slot {
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 24px;
            font-weight: bold;
            color: white;
            background-color: #333;
            border-radius: 5px;
            position: absolute;
        }
        #result {
            font-size: 20px;
            margin-top: 20px;
        }
        #jackpot-container {
            position: relative;
        }
        #jackpot {
            width: 100px;
            height: 100px;
            background-color: red;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 24px;
            font-weight: bold;
            color: white;
        }
        @keyframes spin {
            0% { transform: translateY(0); }
            25% { transform: translateY(-200%); }
            50% { transform: translateY(-400%); }
            75% { transform: translateY(-600%); }
            100% { transform: translateY(-800%); }
        }
        #footer-message {
            position: fixed;
            bottom: 10px;
            right: 10px;
            color: red;
            font-size: 12px;
        }
    </style>
</head>
<body>

<h1>Welcome to the Jackpot Game!</h1>

<div id="game-container">
    <div class="slot-container" id="slot1-container">
        <div class="slot" id="slot1"></div>
    </div>
    <div class="slot-container" id="slot2-container">
        <div class="slot" id="slot2"></div>
    </div>
    <div class="slot-container" id="slot3-container">
        <div class="slot" id="slot3"></div>
    </div>
</div>

<div id="jackpot-container">
    <div id="jackpot">$</div>
</div>

<div id="result"></div>

<label for="bet-input">Bet Size: $</label>
<input type="number" id="bet-input" placeholder="Enter your bet" min="1" step="1">
<button id="play-btn" onclick="playRound()">Play Round</button>

<div>
    <p>Current Balance: $<span id="current-balance">1000</span></p>
    <p>Amount Won: $<span id="amount-won">0</span></p>
</div>

<div id="footer-message">Bet is not good</div>

<script>
    let balance = 1000;

    function playRound() {
        const betInput = document.getElementById('bet-input');
        const resultDiv = document.getElementById('result');
        const jackpot = document.getElementById('jackpot');
        const currentBalance = document.getElementById('current-balance');
        const amountWonDisplay = document.getElementById('amount-won');

        const betAmount = parseFloat(betInput.value);

        if (isNaN(betAmount) || betAmount <= 0 || betAmount > balance) {
            resultDiv.innerText = "Invalid bet amount. Please enter a valid value.";
            return;
        }

        // Clear previous results
        resultDiv.innerText = '';
        amountWonDisplay.innerText = '';

        // Simulate the spinning of the slots
        spinSlot('slot1');
        spinSlot('slot2');
        spinSlot('slot3');

        setTimeout(() => {
            // Stop the spinning after a brief delay
            stopSpin('slot1');
            stopSpin('slot2');
            stopSpin('slot3');

            // Check if the player wins
            const win = checkWin();

            if (win) {
                let multiplier = 1;
                if (document.getElementById('slot1').innerText === '7') {
                    multiplier = 10;
                } else {
                    multiplier = 0.6;
                }

                const amountWon = betAmount * multiplier;
                balance += amountWon;
                resultDiv.innerText = `Congratulations! You won $${amountWon.toFixed(2)}!`;
                amountWonDisplay.innerText = amountWon.toFixed(2);
            } else {
                balance -= betAmount;
                resultDiv.innerText = `Sorry, you lost. Try again!`;
            }

            // Update the current balance
            currentBalance.innerText = balance;

            // Reset jackpot display
            jackpot.innerText = "$";
        }, 3000); // Spinning for 1 seconds
    }

    function spinSlot(slotId) {
        const slot = document.getElementById(slotId);
        slot.style.animation = 'spin 3s infinite ease-in-out';
    }

    function stopSpin(slotId) {
        const slot = document.getElementById(slotId);
        slot.style.animation = 'none'; // Remove the spinning animation
    }

    function checkWin() {
        const slot1 = document.getElementById('slot1').innerText;
        const slot2 = document.getElementById('slot2').innerText;
        const slot3 = document.getElementById('slot3').innerText;

        return (slot1 === slot2 && slot2 === slot3);
    }

    function getRandomSymbol() {
        const symbols = ['7', '🍇', '🍊', '🍋', '🍒', '🍓', '🍉'];
        return symbols[Math.floor(Math.random() * symbols.length)];
    }

    // Initial symbols
    document.getElementById('slot1').innerText = getRandomSymbol();
    document.getElementById('slot2').innerText = getRandomSymbol();
    document.getElementById('slot3').innerText = getRandomSymbol();
</script>

</body>
</html>
