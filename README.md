<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Date?</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            font-family: 'Arial', sans-serif;
            background-color: #ffe6e6;
            text-align: center;
        }

        h1 {
            color: #d63384;
            font-size: 2.5rem;
            margin-bottom: 30px;
        }

        .buttons {
            display: flex;
            align-items: center;
            gap: 20px;
            flex-wrap: wrap;
            justify-content: center;
        }

        button {
            padding: 15px 30px;
            font-size: 1.2rem;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        #yesBtn {
            background-color: #28a745;
            color: white;
        }

        #noBtn {
            background-color: #dc3545;
            color: white;
        }

        .success-message {
            display: none;
            font-size: 2rem;
            color: #d63384;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div id="question-container">
        <h1>Willst du mit mir auf ein Date gehen? ❤️</h1>
        <div class="buttons">
            <button id="yesBtn">Ja</button>
            <button id="noBtn">Nein</button>
        </div>
    </div>

    <div id="success" class="success-message">
        Juhu! Ich wusste es! 🥰✨
    </div>

    <script>
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const questionContainer = document.getElementById('question-container');
        const successMessage = document.getElementById('success');

        let yesSize = 1.2; // Startgröße in rem
        let noClickCount = 0;

        const messages = [
            "Bist du sicher?",
            "Wirklich ganz sicher?",
            "Überleg es dir nochmal...",
            "Gib dir einen Ruck!",
            "Ich bin doch so nett :(",
            "Letzte Chance zu sagen!",
            "Och menno...",
            "Du klickst das Falsche!",
            "Jetzt sag schon Ja!"
        ];

        noBtn.addEventListener('click', () => {
            noClickCount++;
            
            // Ja-Button vergrößern
            yesSize += 0.5;
            yesBtn.style.fontSize = yesSize + "rem";
            yesBtn.style.padding = (15 + noClickCount * 10) + "px " + (30 + noClickCount * 20) + "px";

            // Text auf Nein-Button ändern
            const nextMessage = messages[Math.min(noClickCount - 1, messages.length - 1)];
            noBtn.innerText = nextMessage;

            // Optional: Den Nein-Button ein bisschen schrumpfen lassen
            let currentNoSize = 1.2 - (noClickCount * 0.05);
            if(currentNoSize > 0.5) noBtn.style.fontSize = currentNoSize + "rem";
        });

        yesBtn.addEventListener('click', () => {
            questionContainer.style.display = 'none';
            successMessage.style.display = 'block';
        });
    </script>
</body>
</html>
