# Jhonx_animasi
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Love Animation</title>
    <style>
        body {
            margin: 0;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            font-family: 'Arial', sans-serif;
            flex-direction: column;
        }

        .heart {
            position: relative;
            width: 120px;
            height: 110px;
            transform: rotate(-45deg);
            animation: beat 1s infinite;
            margin-bottom: 20px;
        }

        .heart::before,
        .heart::after {
            content: "";
            position: absolute;
            width: 120px;
            height: 110px;
            background: red;
            border-radius: 50%;
        }

        .heart::before {
            top: -60px;
            left: 0;
        }

        .heart::after {
            left: 60px;
            top: 0;
        }

        @keyframes beat {
            0%, 100% { transform: rotate(-45deg) scale(1); }
            50% { transform: rotate(-45deg) scale(1.2); }
        }

        .text {
            font-size: 1.5rem;
            color: white;
            text-align: center;
            opacity: 0;
            animation: fadeIn 2s forwards;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .star {
            position: absolute;
            width: 4px;
            height: 4px;
            background: white;
            border-radius: 50%;
            animation: twinkle 2s infinite alternate;
        }

        @keyframes twinkle {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>
    <div class="heart"></div>
    <div class="text" id="romanticText"></div>

    <script>
        // Efek bintang
        for(let i = 0; i < 50; i++){
            const star = document.createElement('div');
            star.className = 'star';
            star.style.top = Math.random() * window.innerHeight + 'px';
            star.style.left = Math.random() * window.innerWidth + 'px';
            star.style.animationDuration = (Math.random() * 2 + 1) + 's';
            star.style.opacity = Math.random();
            document.body.appendChild(star);
        }

        // Kata-kata romantis satu per satu
        const lines = [
            "Natalia Hondro...",
            "Sejak aku mengenalmu, hatiku selalu berdebar 💓",
            "Setiap senyummu adalah alasan aku tersenyum 😊",
            "Aku ingin selalu dekat denganmu...",
            "Apakah kau mau menjadi pacarku 💞"
        ];

        let i = 0;
        const textEl = document.getElementById('romanticText');

        function showLine() {
            if(i < lines.length) {
                textEl.innerText = lines[i];
                textEl.style.opacity = 0;
                textEl.style.animation = 'fadeIn 2s forwards';
                i++;
                setTimeout(showLine, 3000); // tiap 3 detik muncul baris berikutnya
            }
        }

        showLine();
    </script>
</body>
</html>
