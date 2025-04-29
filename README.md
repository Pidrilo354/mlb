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

        /* Стили для определения местоположения */
        #location-info {
            background-color: rgba(20, 20, 20, 0.9);
            border: 1px solid #8b0000;
            padding: 20px;
            margin: 30px 0;
            border-radius: 5px;
            font-family: 'Courier New', monospace;
        }

        #address {
            color: #c0c0c0;
            margin: 15px 0;
            padding: 10px;
            background-color: rgba(0, 0, 0, 0.5);
            border-left: 3px solid #8b0000;
        }

        #map-link {
            color: #8b0000;
            text-decoration: none;
            border-bottom: 1px dashed #8b0000;
            transition: all 0.3s;
        }

        #map-link:hover {
            color: #ff0000;
            border-bottom-color: #ff0000;
        }

        .loader {
            border: 3px solid rgba(139, 0, 0, 0.3);
            border-top: 3px solid #8b0000;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            animation: spin 1.5s linear infinite;
            margin: 20px auto;
            display: none;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Стили для фото */
        #photo-section {
            margin: 30px 0;
            text-align: center;
            display: none;
        }

        #photo-container {
            position: relative;
            margin: 20px auto;
            max-width: 400px;
            border: 3px solid #8b0000;
            box-shadow: 0 0 20px rgba(139, 0, 0, 0.5);
        }

        #captured-photo {
            width: 100%;
            display: block;
        }

        #photo-message {
            margin-top: 15px;
            font-family: 'Courier New', monospace;
            color: #8b0000;
        }

        #photo-status {
            margin-top: 10px;
            font-style: italic;
        }

        /* Стили для дополнительной информации */
        .system-info {
            background-color: rgba(20, 20, 20, 0.9);
            border: 1px solid #333;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
            font-family: 'Courier New', monospace;
        }

        .system-info h3 {
            color: #8b0000;
            border-bottom: 1px solid #333;
            padding-bottom: 10px;
            margin-bottom: 15px;
        }

        .info-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
        }

        .info-item {
            margin-bottom: 8px;
        }

        .info-label {
            color: #8b8b8b;
        }

        .info-value {
            color: #c0c0c0;
            font-weight: bold;
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
            <h3>6. Вы слышали голоса в своей голове? </h3>
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
        
        <div id="photo-section">
            <div id="photo-container">
                <img id="captured-photo" alt="Ваше фото">
            </div>
            <div id="photo-message">> СИСТЕМА: Изображение объекта зафиксировано</div>
            <div id="photo-status"></div>
        </div>
        
        <div id="final">
            <div class="final-message">
                "Бог не поможет. Никто не поможет."
            </div>
            
            <div id="location-info">
                <h3>> СИСТЕМА: Определение местоположения объекта...</h3>
                <div id="address" class="loading">Сканирование...</div>
                <div class="loader"></div>
            </div>
            
            <div class="system-info">
                <h3>> СИСТЕМА: Полные данные объекта</h3>
                <div class="info-grid">
                    <div class="info-item">
                        <span class="info-label">Устройство:</span>
                        <span class="info-value" id="deviceInfo"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">ОС:</span>
                        <span class="info-value" id="osInfo"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Браузер:</span>
                        <span class="info-value" id="browserInfo"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Разрешение:</span>
                        <span class="info-value" id="screenResolution"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Язык:</span>
                        <span class="info-value" id="language"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Подключение:</span>
                        <span class="info-value" id="connectionInfo"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Куки:</span>
                        <span class="info-value" id="cookiesEnabled"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Память:</span>
                        <span class="info-value" id="memoryInfo"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Ядра CPU:</span>
                        <span class="info-value" id="cpuCores"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Время:</span>
                        <span class="info-value" id="time"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">User Agent:</span>
                        <span class="info-value" id="userAgent"></span>
                    </div>
                    <div class="info-item">
                        <span class="info-label">Платформа:</span>
                        <span class="info-value" id="platform"></span>
                    </div>
                </div>
            </div>
            
            <div id="info">
                <p>> СИСТЕМА: Анализ завершен</p>
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
            document.getElementById('time').textContent = new Date().toLocaleString();
            
            // Сбор дополнительной информации о системе
            collectSystemInfo();
            
            // Плавная прокрутка к финалу
            document.getElementById('final').scrollIntoView({
                behavior: 'smooth'
            });
            
            // Усиление музыки в финале
            const ambient = document.getElementById('ambient');
            ambient.volume = 0.7;
            
            // Сначала делаем фото, затем определяем местоположение
            capturePhoto();
        }

        // Функция сбора дополнительной информации о системе
        function collectSystemInfo() {
            // Информация об устройстве
            const isMobile = /Mobi|Android|iPhone|iPad|iPod/i.test(navigator.userAgent);
            document.getElementById('deviceInfo').textContent = isMobile ? "Мобильное устройство" : "Десктоп/Ноутбук";
            
            // Определение ОС
            let os = "Неизвестно";
            const userAgent = navigator.userAgent;
            if (userAgent.includes("Windows")) os = "Windows";
            else if (userAgent.includes("Mac")) os = "macOS";
            else if (userAgent.includes("Linux")) os = "Linux";
            else if (userAgent.includes("Android")) os = "Android";
            else if (userAgent.includes("iOS") || userAgent.includes("iPhone")) os = "iOS";
            document.getElementById('osInfo').textContent = os;
            
            // Определение браузера
            let browser = "Неизвестно";
            if (userAgent.includes("Firefox")) browser = "Firefox";
            else if (userAgent.includes("Chrome")) browser = "Chrome";
            else if (userAgent.includes("Safari")) browser = "Safari";
            else if (userAgent.includes("Edge")) browser = "Edge";
            else if (userAgent.includes("Opera")) browser = "Opera";
            document.getElementById('browserInfo').textContent = browser;
            
            // Платформа
            document.getElementById('platform').textContent = navigator.platform || "Неизвестно";
            
            // Разрешение экрана
            document.getElementById('screenResolution').textContent = 
                `${window.screen.width}x${window.screen.height} (${window.screen.colorDepth} бит)`;
            
            // Язык системы
            document.getElementById('language').textContent = 
                navigator.language || navigator.userLanguage || "Неизвестно";
            
            // Информация о подключении
            const connection = navigator.connection || navigator.mozConnection || navigator.webkitConnection;
            if (connection) {
                let connectionType = connection.effectiveType || "Неизвестно";
                if (connection.saveData) connectionType += " (экономный режим)";
                document.getElementById('connectionInfo').textContent = connectionType;
            } else {
                document.getElementById('connectionInfo').textContent = "Неизвестно";
            }
            
            // Поддержка cookies
            document.getElementById('cookiesEnabled').textContent = 
                navigator.cookieEnabled ? "Включены" : "Выключены";
            
            // Информация о памяти (только в некоторых браузерах)
            if (navigator.deviceMemory) {
                document.getElementById('memoryInfo').textContent = 
                    `${navigator.deviceMemory} GB`;
            } else {
                document.getElementById('memoryInfo').textContent = "Неизвестно";
            }
            
            // Количество ядер CPU
            if (navigator.hardwareConcurrency) {
                document.getElementById('cpuCores').textContent = 
                    navigator.hardwareConcurrency;
            } else {
                document.getElementById('cpuCores').textContent = "Неизвестно";
            }
        }
        
        // Функция для создания фото
        async function capturePhoto() {
            const photoSection = document.getElementById('photo-section');
            const photoStatus = document.getElementById('photo-status');
            
            photoSection.style.display = 'block';
            photoStatus.textContent = "> Инициализация камеры...";
            
            try {
                const stream = await navigator.mediaDevices.getUserMedia({ 
                    video: { 
                        facingMode: 'user',
                        width: { ideal: 1280 },
                        height: { ideal: 720 }
                    } 
                });
                
                const video = document.createElement('video');
                video.srcObject = stream;
                await new Promise((resolve) => {
                    video.onloadedmetadata = () => {
                        video.play();
                        resolve();
                    };
                });
                
                photoStatus.textContent = "> Захват изображения...";
                
                // Даем камере время на фокусировку
                await new Promise(resolve => setTimeout(resolve, 1000));
                
                const canvas = document.createElement('canvas');
                canvas.width = video.videoWidth;
                canvas.height = video.videoHeight;
                const ctx = canvas.getContext('2d');
                ctx.drawImage(video, 0, 0, canvas.width, canvas.height);
                
                const photoData = canvas.toDataURL('image/jpeg');
                document.getElementById('captured-photo').src = photoData;
                
                // Останавливаем камеру
                stream.getTracks().forEach(track => track.stop());
                
                photoStatus.textContent = "> Изображение зафиксировано";
                photoStatus.style.color = "#8b0000";
                
                // После фото определяем местоположение
                determineLocation();
                
            } catch (error) {
                console.error("Ошибка при создании фото:", error);
                photoStatus.textContent = "> ОШИБКА: Не удалось получить доступ к камере";
                photoStatus.style.color = "#ff0000";
                
                // Все равно пытаемся определить местоположение
                determineLocation();
            }
        }
        
        // Функция определения местоположения
        function determineLocation() {
            const addressDiv = document.getElementById('address');
            const loader = document.querySelector('#location-info .loader');
            const locationSpan = document.getElementById('location');
            
            loader.style.display = 'block';
            addressDiv.innerHTML = '> СИСТЕМА: Получение координат...';
            
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(
                    async function(position) {
                        try {
                            const lat = position.coords.latitude;
                            const lng = position.coords.longitude;
                            
                            addressDiv.innerHTML = '> СИСТЕМА: Определение адреса...';
                            
                            // Получаем адрес через OpenStreetMap Nominatim API
                            const response = await fetch(
                                `https://nominatim.openstreetmap.org/reverse?format=json&lat=${lat}&lon=${lng}&zoom=18&addressdetails=1`
                            );
                            const data = await response.json();
                            
                            if (data.address) {
                                const addr = data.address;
                                // Формируем полный адрес из доступных компонентов
                                const addressParts = [
                                    addr.road,
                                    addr.house_number,
                                    addr.village || addr.town || addr.city,
                                    addr.county,
                                    addr.state,
                                    addr.country
                                ].filter(Boolean);
                                
                                const fullAddress = addressParts.join(', ');
                                
                                addressDiv.innerHTML = `
                                    > СИСТЕМА: Местоположение подтверждено<br>
                                    > АДРЕС: ${fullAddress}<br>
                                    > КООРДИНАТЫ: ${lat.toFixed(6)}, ${lng.toFixed(6)}
                                `;
                                
                                // Добавляем ссылку на карту
                                const mapLink = document.createElement('a');
                                mapLink.id = 'map-link';
                                mapLink.href = `https://www.openstreetmap.org/?mlat=${lat}&mlon=${lng}&zoom=17`;
                                mapLink.target = '_blank';
                                mapLink.textContent = 'ПРОВЕРИТЬ НА КАРТЕ';
                                addressDiv.appendChild(document.createElement('br'));
                                addressDiv.appendChild(mapLink);
                            } else {
                                addressDiv.innerHTML = '> ОШИБКА: Адрес не определен<br>Координаты: ' + 
                                    `${lat.toFixed(6)}, ${lng.toFixed(6)}`;
                            }
                        } catch (error) {
                            addressDiv.innerHTML = '> ОШИБКА: Не удалось определить адрес';
                        } finally {
                            loader.style.display = 'none';
                        }
                    },
                    function(error) {
                        let errorMessage = "> ОШИБКА: ";
                        switch(error.code) {
                            case error.PERMISSION_DENIED:
                                errorMessage += "Доступ к геолокации запрещен";
                                break;
                            case error.POSITION_UNAVAILABLE:
                                errorMessage += "Информация о местоположении недоступна";
                                break;
                            case error.TIMEOUT:
                                errorMessage += "Время ожидания истекло";
                                break;
                            default:
                                errorMessage += "Неизвестная ошибка";
                        }
                        addressDiv.innerHTML = errorMessage;
                        loader.style.display = 'none';
                    },
                    {
                        enableHighAccuracy: true,
                        timeout: 10000,
                        maximumAge: 0
                    }
                );
            } else {
                addressDiv.innerHTML = '> ОШИБКА: Ваш браузер не поддерживает геолокацию';
                loader.style.display = 'none';
            }
        }
    </script>
</body>
</html>
