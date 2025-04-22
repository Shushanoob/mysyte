<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Для любимой</title>
    <style>
        body {
            background-color: #fff0f5;
            font-family: "Arial", sans-serif;
            text-align: center;
            padding-top: 100px;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            position: relative;
            overflow: hidden;
        }

        #passwordSection, #heartSection {
            display: none;
        }

        #passwordSection {
            display: block;
        }

        input[type="password"] {
            padding: 12px;
            font-size: 18px;
            border: 2px solid #ffb6c1;
            border-radius: 10px;
            background-color: #fff;
            margin-bottom: 15px;
        }

        button {
            padding: 12px 25px;
            font-size: 18px;
            margin-top: 15px;
            background-color: #ffb6c1;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #ff80bf;
        }

        .heart-container {
            width: 220px;
            margin: 40px auto;
            cursor: pointer;
            transition: transform 0.3s ease-in-out;
        }

        svg {
            width: 100%;
            height: 100%;
            transition: transform 0.2s ease-in-out;
        }

        svg:hover {
            transform: scale(1.1);
        }

        .heart-container:active svg {
            transform: scale(1.4);
        }

        #errorMsg {
            color: red;
            font-size: 14px;
        }

        /* Маленькие сердечки */
        .small-heart {
            position: absolute;
            width: 45px;
            height: 45px;
            fill: #ffc0cb;
            animation: moveHeart 4s linear infinite;
        }

        .small-heart2 {
            position: absolute;
            width: 45px;
            height: 45px;
            fill: #ffb6c1;
            animation: moveHeart2 4s linear infinite;
        }

        /* Анимация для маленьких сердечек */
        @keyframes moveHeart {
            0% {
                top: -5%;
                left: 10%;
                transform: scale(0.8);
            }
            100% {
                top: 100%;
                left: 10%;
                transform: scale(0.8);
            }
        }

        @keyframes moveHeart2 {
            0% {
                top: -5%;
                right: 15%;
                transform: scale(0.8);
            }
            100% {
                top: 100%;
                right: 15%;
                transform: scale(0.8);
            }
        }

    </style>
</head>
<body>

<div id="passwordSection">
    <h2 style="font-size: 24px; color: #ff80bf;">Введите пароль</h2>
    <input type="password" id="passwordInput" placeholder="Пароль">
    <br>
    <button onclick="checkPassword()">Войти</button>
    <p id="errorMsg"></p>
</div>

<div id="heartSection">
    <div class="heart-container" onclick="showRandomMessage(event)">
        <svg viewBox="0 0 32 29.6" xmlns="http://www.w3.org/2000/svg">
            <path d="M23.6,0c-3.4,0-6.4,2.1-7.6,5.1C14.8,2.1,11.8,0,8.4,0C3.8,0,0,3.8,0,8.4c0,9.6,16,21.2,16,21.2s16-11.6,16-21.2
                C32,3.8,28.2,0,23.6,0z"
                fill="#ffc0cb"/>
        </svg>
    </div>
</div>

<!-- Маленькие сердечки -->
<svg class="small-heart" viewBox="0 0 32 29.6" xmlns="http://www.w3.org/2000/svg">
    <path d="M23.6,0c-3.4,0-6.4,2.1-7.6,5.1C14.8,2.1,11.8,0,8.4,0C3.8,0,0,3.8,0,8.4c0,9.6,16,21.2,16,21.2s16-11.6,16-21.2
        C32,3.8,28.2,0,23.6,0z" fill="#ffc0cb"/>
</svg>

<svg class="small-heart2" viewBox="0 0 32 29.6" xmlns="http://www.w3.org/2000/svg">
    <path d="M23.6,0c-3.4,0-6.4,2.1-7.6,5.1C14.8,2.1,11.8,0,8.4,0C3.8,0,0,3.8,0,8.4c0,9.6,16,21.2,16,21.2s16-11.6,16-21.2
        C32,3.8,28.2,0,23.6,0z" fill="#ffb6c1"/>
</svg>

<script>
    const messages = [
        "Я тебя люблю",
        "Милая",
        "Любимая",
        "Солнышко",
        "Дорогая",
        "Ты самая лучшая на свете",
        "Звездочка"
    ];

    function checkPassword() {
        const input = document.getElementById("passwordInput").value;
        if (input === "0129") {
            document.getElementById("passwordSection").style.display = "none";
            document.getElementById("heartSection").style.display = "block";
            addRandomHearts();
        } else {
            document.getElementById("errorMsg").innerText = "Пароль не верный";
        }
    }

    function showRandomMessage(event) {
        const message = messages[Math.floor(Math.random() * messages.length)];
        alert(message);

        // Увеличиваем сердечко при каждом нажатии
        const heart = document.querySelector('.heart-container svg');
        heart.style.transition = 'transform 0.5s ease-in-out';
        heart.style.transform = 'scale(1.4)';
        setTimeout(() => {
            heart.style.transition = 'transform 0.3s ease-in-out';
            heart.style.transform = 'scale(1)';
        }, 500);
    }

    // Добавляем случайное количество маленьких сердечек (от 3 до 5)
    function addRandomHearts() {
        const numberOfHearts = Math.floor(Math.random() * 3) + 3; // от 3 до 5
        for (let i = 0; i < numberOfHearts; i++) {
            const heart = document.createElement('svg');
            heart.classList.add('small-heart');
            heart.setAttribute('viewBox', '0 0 32 29.6');
            heart.setAttribute('xmlns', 'http://www.w3.org/2000/svg');
            heart.innerHTML = '<path d="M23.6,0c-3.4,0-6.4,2.1-7.6,5.1C14.8,2.1,11.8,0,8.4,0C3.8,0,0,3.8,0,8.4c0,9.6,16,21.2,16,21.2s16-11.6,16-21.2C32,3.8,28.2,0,23.6,0z" fill="#ffc0cb"/>';
            document.body.appendChild(heart);
        }
    }
</script>

</body>
</html>
 
