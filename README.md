<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Koin Clicker Game</title>
    <!-- Menghubungkan Telegram Web Apps SDK -->
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #1a1a1a;
            color: white;
            text-align: center;
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 90vh;
        }
        #coin {
            width: 150px;
            height: 150px;
            background: gold;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 50px;
            cursor: pointer;
            box-shadow: 0 0 20px rgba(255, 215, 0, 0.6);
            transition: transform 0.1s;
            user-select: none;
        }
        #coin:active {
            transform: scale(0.9);
        }
        h1 { font-size: 24px; margin-bottom: 10px; }
        .score { font-size: 32px; font-weight: bold; margin: 20px 0; }
    </style>
</head>
<body>

    <h1>Ketuk Koinnya!</h1>
    <div class="score">Skor: <span id="score-val">0</span></div>
    <div id="coin">🪙</div>

    <script>
        // Inisialisasi Telegram Web App
        const tg = window.Telegram.WebApp;
        tg.ready(); // Memberitahu Telegram bahwa aplikasi siap
        tg.expand(); // Membuka aplikasi dalam layar penuh

        let score = 0;
        const scoreEl = document.getElementById('score-val');
        const coinEl = document.getElementById('coin');

        coinEl.addEventListener('click', () => {
            score++;
            scoreEl.innerText = score;
            
            // Memberikan efek getar (vibrate) jika didukung perangkat haptic Telegram
            if (tg.HapticFeedback) {
                tg.HapticFeedback.impactOccurred('medium');
            }
        });
    </script>
</body>
</html>
