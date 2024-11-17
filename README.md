# <!DOCTYPE html>
<html>
<head>
    <title>Кликер за 10 секунд</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        #clickButton {
            font-size: 24px;
            padding: 10px 20px;
            margin-top: 20px;
        }
        #score, #record {
            font-size: 20px;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <h1>Кликер за 10 секунд</h1>
    <p>Нажимайте на кнопку как можно больше раз за 10 секунд!</p>
    <button id="clickButton" onclick="countClick()">Кликни меня!</button>
    <div id="score">Счет: 0</div>
    <div id="record">Рекорд: 0</div>

    <script>
        let score = 0;
        let record = 0;
        let timeLeft = 10;
        let timerStarted = false;

        function countClick() {
            if (!timerStarted) {
                timerStarted = true;
                let timer = setInterval(() => {
                    timeLeft--;
                    if (timeLeft <= 0) {
                        clearInterval(timer);
                        timerStarted = false;
                        if (score > record) {
                            record = score;
                            document.getElementById("record").innerText = "Рекорд: " + record;
                        }
                        score = 0;
                        timeLeft = 10;
                    }
                }, 1000);
            }
            score++;
            document.getElementById("score").innerText = "Счет: " + score;
        }
    </script>
</body>
</html>

