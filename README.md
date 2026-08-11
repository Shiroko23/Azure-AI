<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes, viewport-fit=cover">
    <title>WilteChat - Loading</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html, body {
            height: 100%;
            overflow: hidden;
        }

        body {
            background: #0a0a0a;
            font-family: 'Inter', system-ui, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .container {
            width: 100%;
            max-width: 420px;
            height: 100dvh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 24px;
            position: relative;
        }

        /* --- BINTANG JATUH PINK --- */
        .star-bg {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            pointer-events: none;
            z-index: 0;
            overflow: hidden;
        }

        .star-particle {
            position: absolute;
            width: 2px;
            height: 2px;
            background: #ff88bb;
            border-radius: 50%;
            opacity: 0;
            animation: starFloat 2.5s ease-in-out infinite;
            box-shadow: 0 0 4px #ff88bb;
        }

        @keyframes starFloat {
            0% { opacity: 0; transform: translateY(0) scale(0.5); }
            50% { opacity: 1; transform: translateY(-40px) scale(1); }
            100% { opacity: 0; transform: translateY(-80px) scale(0.5); }
        }

        /* --- LOGO & JUDUL --- */
        .logo-wrapper {
            text-align: center;
            z-index: 1;
            margin-bottom: 10px;
        }

        .logo-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #ff66aa, #cc3388);
            border-radius: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 16px;
            box-shadow: 0 0 40px rgba(255, 102, 170, 0.3);
            animation: pulseGlow 2s infinite ease-in-out;
        }

        @keyframes pulseGlow {
            0%, 100% { box-shadow: 0 0 40px rgba(255, 102, 170, 0.3); }
            50% { box-shadow: 0 0 60px rgba(255, 102, 170, 0.6); }
        }

        .logo-icon i {
            font-size: 36px;
            color: white;
        }

        .logo-title {
            font-size: 28px;
            font-weight: 800;
            background: linear-gradient(135deg, #ff88bb, #ff66aa);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: -0.5px;
        }

        .logo-sub {
            font-size: 13px;
            color: #aa6688;
            margin-top: 4px;
            font-weight: 400;
            letter-spacing: 2px;
        }

        /* --- LOADING BAR --- */
        .loading-wrapper {
            width: 100%;
            max-width: 280px;
            z-index: 1;
            margin-top: 20px;
        }

        .loading-bar-track {
            width: 100%;
            height: 4px;
            background: rgba(255, 255, 255, 0.06);
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }

        .loading-bar-fill {
            width: 0%;
            height: 100%;
            background: linear-gradient(90deg, #ff66aa, #ff88bb, #ff66aa);
            border-radius: 10px;
            animation: loadingFill 2.5s ease-in-out forwards;
            box-shadow: 0 0 12px rgba(255, 102, 170, 0.5);
        }

        @keyframes loadingFill {
            0% { width: 0%; }
            20% { width: 25%; }
            40% { width: 50%; }
            60% { width: 70%; }
            80% { width: 88%; }
            95% { width: 95%; }
            100% { width: 100%; }
        }

        .loading-text {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
            color: #885577;
            font-size: 12px;
            font-weight: 500;
        }

        .loading-text .dots {
            display: flex;
            gap: 4px;
            align-items: center;
        }

        .loading-text .dots span {
            display: inline-block;
            width: 4px;
            height: 4px;
            background: #ff66aa;
            border-radius: 50%;
            animation: dotBounce 1.4s infinite;
        }

        .loading-text .dots span:nth-child(2) {
            animation-delay: 0.2s;
        }

        .loading-text .dots span:nth-child(3) {
            animation-delay: 0.4s;
        }

        @keyframes dotBounce {
            0%, 60%, 100% { transform: translateY(0); opacity: 0.4; }
            30% { transform: translateY(-4px); opacity: 1; }
        }

        /* --- TOMBOL BUKA --- */
        .btn-wrapper {
            z-index: 1;
            margin-top: 28px;
            opacity: 0;
            animation: fadeInBtn 0.5s ease forwards;
            animation-delay: 2.6s;
        }

        @keyframes fadeInBtn {
            0% { opacity: 0; transform: translateY(10px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        .btn-buka {
            display: inline-flex;
            align-items: center;
            gap: 12px;
            padding: 14px 40px;
            background: linear-gradient(135deg, #ff66aa, #cc3388);
            border: none;
            border-radius: 50px;
            color: white;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.2s ease;
            box-shadow: 0 0 30px rgba(255, 102, 170, 0.25);
            text-decoration: none;
            font-family: 'Inter', system-ui, sans-serif;
            position: relative;
            overflow: hidden;
        }

        .btn-buka i {
            font-size: 18px;
            transition: transform 0.3s ease;
        }

        .btn-buka:hover {
            transform: scale(1.02);
            box-shadow: 0 0 40px rgba(255, 102, 170, 0.5);
        }

        .btn-buka:hover i {
            transform: translateX(4px);
        }

        .btn-buka:active {
            transform: scale(0.96);
        }

        /* --- WATERMARK --- */
        .watermark {
            position: absolute;
            bottom: 24px;
            left: 0;
            right: 0;
            text-align: center;
            color: #332233;
            font-size: 11px;
            z-index: 1;
            letter-spacing: 1px;
            font-weight: 300;
        }

        .watermark span {
            color: #ff66aa;
            font-weight: 500;
        }

        /* --- RESPONSIVE --- */
        @media (max-width: 400px) {
            .logo-title {
                font-size: 22px;
            }
            .logo-icon {
                width: 64px;
                height: 64px;
            }
            .logo-icon i {
                font-size: 28px;
            }
            .btn-buka {
                padding: 12px 32px;
                font-size: 14px;
            }
        }

        @media (min-width: 481px) {
            .container {
                height: 90vh;
                max-width: 400px;
                border-radius: 24px;
                background: rgba(10, 10, 10, 0.85);
                backdrop-filter: blur(12px);
                border: 1px solid rgba(255, 102, 170, 0.15);
                box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6);
            }
        }
    </style>
</head>
<body>

<!-- BINTANG DI BELAKANG -->
<div class="star-bg" id="starBg"></div>

<div class="container">

    <!-- LOGO & JUDUL -->
    <div class="logo-wrapper">
        <div class="logo-icon">
            <i class="fas fa-comment-dots"></i>
        </div>
        <h1 class="logo-title">WilteChat</h1>
        <p class="logo-sub">~ siap untukmu ~ ✨</p>
    </div>

    <!-- LOADING BAR -->
    <div class="loading-wrapper">
        <div class="loading-bar-track">
            <div class="loading-bar-fill"></div>
        </div>
        <div class="loading-text">
            <span>Memuat WilteChat...</span>
            <span class="dots">
                <span></span>
                <span></span>
                <span></span>
            </span>
        </div>
    </div>

    <!-- TOMBOL BUKA -->
    <div class="btn-wrapper">
        <a href="mywilte.html" class="btn-buka" id="btnBuka">
            <span>Buka Wilte!!</span>
            <i class="fas fa-arrow-right"></i>
        </a>
    </div>

    <!-- WATERMARK -->
    <div class="watermark">
        <span>✦</span> WilteChat <span>✦</span>
    </div>
</div>

<script>
    // --- BINTANG JATUH ---
    function createStars() {
        const container = document.getElementById('starBg');
        for (let i = 0; i < 35; i++) {
            const star = document.createElement('div');
            star.className = 'star-particle';
            star.style.left = Math.random() * 100 + '%';
            star.style.top = Math.random() * 100 + '%';
            star.style.animationDelay = Math.random() * 2.5 + 's';
            star.style.animationDuration = (Math.random() * 2 + 2) + 's';
            star.style.width = (Math.random() * 3 + 1) + 'px';
            star.style.height = star.style.width;
            container.appendChild(star);
        }
    }
    createStars();

    // --- EFEK KLIK TOMBOL ---
    document.getElementById('btnBuka').addEventListener('click', function(e) {
        e.preventDefault();
        this.style.transform = 'scale(0.92)';
        this.style.opacity = '0.7';
        setTimeout(() => {
            window.location.href = this.getAttribute('href');
        }, 200);
    });

    // --- PASTI TOMBOL MUNCUL ---
    window.addEventListener('load', function() {
        const btnWrapper = document.querySelector('.btn-wrapper');
        if (btnWrapper) {
            btnWrapper.style.animation = 'fadeInBtn 0.5s ease forwards';
        }
    });
</script>

</body>
</html>
