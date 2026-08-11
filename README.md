<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes, viewport-fit=cover">
    <title>Hoshino AI - Lobby</title>
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
            background: #0e0c12;
            font-family: 'Inter', system-ui, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .app-container {
            width: 100%;
            height: 100dvh;
            max-width: 480px;
            background: #0e0c12;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            position: relative;
        }

        /* --- HEADER --- */
        .header {
            background: #1e1420;
            padding: 12px 16px 10px;
            border-bottom: 1px solid #2a1a2a;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-shrink: 0;
        }
        .header-left {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .header-left i {
            font-size: 18px;
            color: #ff88bb;
            cursor: pointer;
        }
        .header-left h1 {
            color: #fff;
            font-size: 17px;
            font-weight: 700;
        }
        .header-left h1 span {
            color: #ff88bb;
        }
        .header-right i {
            color: #d0b0c0;
            font-size: 16px;
            margin-left: 12px;
            cursor: pointer;
        }

        /* --- SEARCH BAR --- */
        .search-bar {
            background: #1a121a;
            padding: 6px 12px;
            border-bottom: 1px solid #2a1a2a;
            flex-shrink: 0;
        }
        .search-bar .search-box {
            display: flex;
            align-items: center;
            background: #0a0a0a;
            border-radius: 30px;
            padding: 4px 12px;
            border: 1px solid #2a1a2a;
        }
        .search-box i {
            color: #777;
            font-size: 13px;
            margin-right: 8px;
        }
        .search-box input {
            background: transparent;
            border: none;
            outline: none;
            color: #d0b0c0;
            font-size: 13px;
            width: 100%;
            padding: 6px 0;
        }
        .search-box input::placeholder {
            color: #555;
        }

        /* --- CONTACT LIST --- */
        .contact-list {
            flex: 1;
            overflow-y: auto;
            padding: 4px 0;
            background: #0e0c12;
            -webkit-overflow-scrolling: touch;
        }
        .contact-list::-webkit-scrollbar {
            width: 3px;
        }
        .contact-list::-webkit-scrollbar-thumb {
            background: #ff88bb;
            border-radius: 10px;
        }

        /* --- CONTACT ITEM --- */
        .contact-item {
            display: flex;
            align-items: center;
            padding: 10px 14px;
            border-bottom: 1px solid #1a121a;
            cursor: pointer;
            transition: all 0.1s ease;
            text-decoration: none;
            color: inherit;
            min-height: 60px;
        }
        .contact-item:active {
            background: #1a121a;
            transform: scale(0.98);
        }

        .contact-avatar {
            width: 44px;
            height: 44px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
            margin-right: 12px;
            overflow: hidden;
            border: 1px solid #3a1a3a;
        }
        .contact-avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .contact-avatar i {
            color: #ff88bb;
            font-size: 20px;
        }

        .contact-info {
            flex: 1;
            min-width: 0;
        }
        .contact-name {
            color: #fff;
            font-size: 15px;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 6px;
            flex-wrap: wrap;
        }
        .contact-name .badge {
            font-size: 9px;
            font-weight: 700;
            padding: 1px 8px;
            border-radius: 30px;
        }
        .badge.online {
            background: #88ffaa;
            color: #0a0a0a;
        }
        .badge.offline {
            background: #666;
            color: #ddd;
        }
        .contact-message {
            color: #a08890;
            font-size: 12px;
            margin-top: 1px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        .contact-time {
            color: #777;
            font-size: 10px;
            text-align: right;
            flex-shrink: 0;
            margin-left: 8px;
        }

        /* --- WARNA KHUSUS --- */
        .contact-item.hoshino .contact-avatar {
            border-color: #e84393;
        }
        .contact-item.hoshino .contact-name {
            color: #f06292;
        }
        .contact-item.azure .contact-avatar {
            border-color: #8866ff;
        }
        .contact-item.suna .contact-avatar {
            border-color: #ff88bb;
        }
        .contact-item.arona .contact-avatar {
            border-color: #ffdd44;
        }

        /* --- FOOTER --- */
        .footer {
            background: #1e1420;
            padding: 8px 14px;
            border-top: 1px solid #2a1a2a;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-shrink: 0;
        }
        .footer span {
            color: #777;
            font-size: 11px;
        }
        .footer i {
            color: #ff88bb;
            font-size: 14px;
            cursor: pointer;
            margin-left: 12px;
        }

        /* --- RESPONSIVE UNTUK HP KECIL --- */
        @media (max-width: 380px) {
            .header-left h1 {
                font-size: 15px;
            }
            .contact-item {
                padding: 8px 10px;
                min-height: 50px;
            }
            .contact-avatar {
                width: 38px;
                height: 38px;
                margin-right: 10px;
            }
            .contact-name {
                font-size: 13px;
            }
            .contact-message {
                font-size: 11px;
            }
            .contact-time {
                font-size: 9px;
            }
            .footer span {
                font-size: 10px;
            }
        }

        @media (min-width: 481px) {
            .app-container {
                height: 90vh;
                border-radius: 24px;
                box-shadow: 0 20px 40px rgba(0,0,0,0.8);
                border: 1px solid #2a1a2a;
            }
        }
    </style>
</head>
<body>

<div class="app-container">

    <!-- HEADER -->
    <div class="header">
        <div class="header-left">
            <i class="fas fa-chevron-left"></i>
            <h1>Wilte<span>Chat</span></h1>
        </div>
        <div class="header-right">
            <i class="fas fa-camera"></i>
            <i class="fas fa-ellipsis-v"></i>
        </div>
    </div>

    <!-- SEARCH BAR -->
    <div class="search-bar">
        <div class="search-box">
            <i class="fas fa-search"></i>
            <input type="text" placeholder="Cari chat atau kontak..." id="searchInput" onkeyup="filterContacts()">
        </div>
    </div>

    <!-- CONTACT LIST -->
    <div class="contact-list" id="contactList">

        <!-- HOSHINO -->
        <a href="myai.html" class="contact-item hoshino">
            <div class="contact-avatar">
                <img src="hoshino3.png" alt="Hoshino" onerror="this.style.display='none';this.parentElement.innerHTML='<i class=\'fas fa-heart\'></i>'">
            </div>
            <div class="contact-info">
                <div class="contact-name">
                    🌸 Hoshino
                    <span class="badge online">Online</span>
                </div>
                <div class="contact-message">Uhe~ Halo Sensei! 💕</div>
            </div>
            <div class="contact-time">Sekarang</div>
        </a>

        <!-- AZURE -->
        <a href="myai2.html" class="contact-item azure">
            <div class="contact-avatar">
                <img src="azure.png" alt="Azure" onerror="this.style.display='none';this.parentElement.innerHTML='<i class=\'fas fa-moon\'></i>'">
            </div>
            <div class="contact-info">
                <div class="contact-name">
                    🌙 Azure
                    <span class="badge online">Online</span>
                </div>
                <div class="contact-message">Ada yang bisa saya bantu? 🌙</div>
            </div>
            <div class="contact-time">Sekarang</div>
        </a>

        <!-- SUNA -->
        <a href="suna%20ai.html" class="contact-item suna">
            <div class="contact-avatar">
                <img src="suna.png" alt="Suna" onerror="this.style.display='none';this.parentElement.innerHTML='<i class=\'fas fa-cat\'></i>'">
            </div>
            <div class="contact-info">
                <div class="contact-name">
                    🐱 Suna
                    <span class="badge offline">Offline</span>
                </div>
                <div class="contact-message">... Suna lagi tidur...</div>
            </div>
            <div class="contact-time">5 menit lalu</div>
        </a>

        <!-- ARONA -->
        <a href="myarona.html" class="contact-item arona">
            <div class="contact-avatar">
                <img src="arona.png" alt="Arona" onerror="this.style.display='none';this.parentElement.innerHTML='<i class=\'fas fa-star\'></i>'">
            </div>
            <div class="contact-info">
                <div class="contact-name">
                    ⭐ Arona
                    <span class="badge offline">Offline</span>
                </div>
                <div class="contact-message">Halo~ Sensei! 👋</div>
            </div>
            <div class="contact-time">2 jam lalu</div>
        </a>

    </div>

    <!-- FOOTER -->
    <div class="footer">
        <span><i class="fas fa-lock" style="margin-right: 6px;"></i> End-to-end encrypted</span>
        <div>
            <i class="fas fa-chart-simple"></i>
            <i class="fas fa-cog"></i>
        </div>
    </div>

</div>

<script>
    function filterContacts() {
        const input = document.getElementById('searchInput');
        const filter = input.value.toLowerCase();
        const contacts = document.querySelectorAll('.contact-item');

        contacts.forEach(item => {
            const name = item.querySelector('.contact-name')?.innerText?.toLowerCase() || '';
            const message = item.querySelector('.contact-message')?.innerText?.toLowerCase() || '';
            if (name.includes(filter) || message.includes(filter)) {
                item.style.display = 'flex';
            } else {
                item.style.display = 'none';
            }
        });
    }

    // Efek klik & langsung pindah
    document.querySelectorAll('.contact-item').forEach(el => {
        el.addEventListener('click', function(e) {
            e.preventDefault();
            this.style.opacity = '0.5';
            setTimeout(() => {
                window.location.href = this.getAttribute('href');
            }, 150);
        });
    });
</script>

</body>
</html>
