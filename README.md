<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Hoshino AI | Pink Edition 🌸</title>
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
            background: linear-gradient(135deg, #fce4ec 0%, #f8bbd0 50%, #f48fb1 100%);
            font-family: 'Inter', system-ui, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .petal {
            position: fixed;
            top: -20px;
            color: #ff80ab;
            user-select: none;
            pointer-events: none;
            z-index: 999;
            animation: petalFall linear forwards;
            font-size: 1rem;
        }

        @keyframes petalFall {
            0% { transform: translateY(0) rotate(0deg) scale(1); opacity: 1; }
            100% { transform: translateY(110vh) rotate(360deg) scale(0.5); opacity: 0; }
        }

        .app {
            width: 100%;
            max-width: 1100px;
            height: 100vh;
            height: 100dvh;
            background: rgba(255, 240, 245, 0.92);
            backdrop-filter: blur(12px);
            display: flex;
            box-shadow: 0 0 50px rgba(255, 105, 180, 0.25);
            overflow: hidden;
            border-left: 2px solid rgba(255, 182, 193, 0.5);
            border-right: 2px solid rgba(255, 182, 193, 0.5);
            position: relative;
        }

        .sidebar {
            width: 260px;
            background: rgba(255, 240, 248, 0.9);
            border-right: 2px solid rgba(255, 182, 193, 0.4);
            display: flex;
            flex-direction: column;
            overflow: hidden;
            transition: transform 0.3s ease;
            flex-shrink: 0;
            position: absolute;
            left: 0;
            top: 0;
            bottom: 0;
            z-index: 20;
            transform: translateX(-110%);
        }

        .sidebar.show {
            transform: translateX(0);
            box-shadow: 2px 0 20px rgba(0,0,0,0.15);
        }

        .sidebar-header {
            padding: 12px 16px;
            border-bottom: 2px solid rgba(255, 182, 193, 0.4);
            flex-shrink: 0;
        }

        .sidebar-header h3 {
            color: #e84393;
            font-size: 0.8rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .new-chat-btn {
            background: linear-gradient(135deg, #f06292, #e84393);
            border: none;
            padding: 6px 12px;
            border-radius: 30px;
            color: white;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.7rem;
            width: 100%;
            margin-top: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
            transition: 0.2s;
        }

        .new-chat-btn:hover {
            transform: scale(1.02);
            box-shadow: 0 4px 12px rgba(232, 67, 147, 0.3);
        }

        .chat-list {
            flex: 1;
            overflow-y: auto;
            padding: 8px;
        }

        .chat-item {
            background: rgba(255, 200, 220, 0.4);
            border-radius: 12px;
            padding: 8px 10px;
            margin-bottom: 6px;
            cursor: pointer;
            transition: 0.2s;
            border: 1px solid rgba(232, 67, 147, 0.2);
        }

        .chat-item:hover {
            background: rgba(255, 160, 200, 0.4);
        }

        .chat-item.active {
            background: rgba(232, 67, 147, 0.2);
            border-color: #e84393;
        }

        .chat-title {
            color: #c04080;
            font-size: 0.75rem;
            font-weight: 500;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .chat-date {
            color: #d87a9a;
            font-size: 0.55rem;
            margin-top: 2px;
        }

        .delete-chat {
            float: right;
            color: #ff8888;
            cursor: pointer;
            font-size: 0.65rem;
            opacity: 0;
        }

        .chat-item:hover .delete-chat {
            opacity: 1;
        }

        .main-chat {
            flex: 1;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            min-width: 0;
            width: 100%;
        }

        .chat-header {
            padding: 8px 12px;
            background: rgba(255, 248, 250, 0.9);
            border-bottom: 2px solid rgba(255, 182, 193, 0.3);
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-shrink: 0;
            min-height: 48px;
        }

        .logo-area {
            display: flex;
            align-items: center;
            gap: 8px;
            overflow: hidden;
        }

        .toggle-sidebar-btn {
            background: rgba(232, 67, 147, 0.2);
            border: 1px solid rgba(232, 67, 147, 0.4);
            border-radius: 30px;
            padding: 4px 10px;
            cursor: pointer;
            color: #e84393;
            font-size: 0.65rem;
            display: flex;
            align-items: center;
            gap: 4px;
            flex-shrink: 0;
        }

        .profile-pic {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid #e84393;
            box-shadow: 0 0 8px rgba(232, 67, 147, 0.3);
            flex-shrink: 0;
        }

        .logo-text {
            font-weight: 700;
            font-size: 1rem;
            background: linear-gradient(135deg, #e84393, #f06292, #ec407a);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            white-space: nowrap;
        }

        .logo-sub {
            font-size: 0.5rem;
            color: #d87a9a;
            display: none;
        }

        .status-badge {
            display: flex;
            align-items: center;
            gap: 4px;
            font-size: 0.55rem;
            background: rgba(232, 67, 147, 0.15);
            padding: 2px 8px;
            border-radius: 20px;
            flex-shrink: 0;
        }

        .status-online {
            width: 6px;
            height: 6px;
            background: #88ffaa;
            border-radius: 50%;
            box-shadow: 0 0 5px #88ffaa;
        }

        .status-offline {
            width: 6px;
            height: 6px;
            background: #ff6644;
            border-radius: 50%;
        }

        .settings-panel {
            background: rgba(255, 248, 250, 0.9);
            border-bottom: 2px solid rgba(255, 182, 193, 0.3);
            padding: 6px 10px;
            display: flex;
            align-items: center;
            gap: 6px;
            flex-wrap: wrap;
            flex-shrink: 0;
        }

        .api-input-group {
            display: flex;
            align-items: center;
            gap: 4px;
            flex: 1;
            min-width: 100px;
        }

        .api-input-group input {
            flex: 1;
            background: rgba(255, 240, 248, 0.9);
            border: 1px solid rgba(232, 67, 147, 0.3);
            border-radius: 30px;
            padding: 4px 10px;
            color: #c04080;
            font-size: 0.65rem;
            outline: none;
            font-family: monospace;
            min-width: 60px;
        }

        .api-input-group input:focus {
            border-color: #e84393;
            box-shadow: 0 0 5px rgba(232, 67, 147, 0.3);
        }

        .toggle-password-btn {
            background: rgba(232, 67, 147, 0.2);
            border: 1px solid rgba(232, 67, 147, 0.4);
            border-radius: 50%;
            width: 26px;
            height: 26px;
            cursor: pointer;
            color: #e84393;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 10px;
            flex-shrink: 0;
        }

        .save-btn {
            background: linear-gradient(135deg, #f06292, #e84393);
            border: none;
            padding: 4px 12px;
            border-radius: 30px;
            color: white;
            cursor: pointer;
            font-size: 0.6rem;
            flex-shrink: 0;
        }

        .action-buttons {
            display: flex;
            gap: 4px;
            align-items: center;
            flex-wrap: wrap;
        }

        .reset-chat-btn, .regenerate-btn, .upload-btn {
            background: rgba(232, 67, 147, 0.15);
            border: 1px solid rgba(232, 67, 147, 0.3);
            padding: 4px 8px;
            border-radius: 30px;
            color: #e84393;
            cursor: pointer;
            font-size: 0.55rem;
            display: flex;
            align-items: center;
            gap: 4px;
            flex-shrink: 0;
        }

        .reset-chat-btn:hover, .regenerate-btn:hover, .upload-btn:hover {
            background: rgba(232, 67, 147, 0.3);
        }

        .chat-messages {
            flex: 1;
            overflow-y: auto;
            padding: 12px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            min-height: 0;
        }

        .chat-messages::-webkit-scrollbar {
            width: 3px;
        }
        .chat-messages::-webkit-scrollbar-thumb {
            background: #e84393;
            border-radius: 10px;
        }

        .message {
            display: flex;
            align-items: flex-start;
            gap: 8px;
            max-width: 90%;
            animation: fadeIn 0.3s ease;
            position: relative;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .message.user {
            align-self: flex-end;
            flex-direction: row-reverse;
        }

        .avatar {
            width: 28px;
            height: 28px;
            border-radius: 50%;
            background: linear-gradient(145deg, #fce4ec, #f8d0e0);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
            flex-shrink: 0;
            border: 1px solid rgba(232, 67, 147, 0.3);
            overflow: hidden;
        }

        .avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .user .avatar {
            background: linear-gradient(135deg, #f06292, #e84393);
            border: none;
        }

        .bubble {
            background: rgba(255, 250, 255, 0.9);
            padding: 6px 12px;
            border-radius: 16px;
            font-size: 0.8rem;
            line-height: 1.4;
            color: #4a2a3a;
            border: 1px solid rgba(232, 67, 147, 0.15);
            word-wrap: break-word;
            overflow-wrap: break-word;
        }

        .user .bubble {
            background: linear-gradient(135deg, #f06292, #e84393);
            border: none;
            color: white;
        }

        .timestamp {
            font-size: 0.5rem;
            color: #d87a9a;
            margin-top: 2px;
            margin-left: 36px;
        }

        .user .timestamp {
            text-align: right;
            margin-right: 36px;
        }

        .chat-image {
            max-width: 100%;
            max-height: 150px;
            border-radius: 12px;
            margin-top: 4px;
            cursor: pointer;
            border: 2px solid #e84393;
        }

        .image-preview-area {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            margin-bottom: 6px;
            padding: 6px;
            background: rgba(232, 67, 147, 0.15);
            border-radius: 12px;
        }

        .preview-img {
            width: 50px;
            height: 50px;
            object-fit: cover;
            border-radius: 8px;
            border: 2px solid #e84393;
        }

        .remove-preview {
            position: absolute;
            background: #ff5555;
            border-radius: 50%;
            width: 16px;
            height: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 8px;
            cursor: pointer;
            margin-left: -14px;
            margin-top: -4px;
            color: white;
        }

        .regenerate-message-btn {
            position: absolute;
            bottom: -18px;
            right: 0;
            background: rgba(232, 67, 147, 0.3);
            border: none;
            border-radius: 20px;
            padding: 2px 8px;
            font-size: 0.5rem;
            color: #e84393;
            cursor: pointer;
            display: none;
            gap: 4px;
            align-items: center;
        }

        .message.assistant:hover .regenerate-message-btn {
            display: flex;
        }

        .input-container {
            background: rgba(255, 248, 250, 0.9);
            border-top: 2px solid rgba(255, 182, 193, 0.3);
            padding: 8px 10px 10px;
            flex-shrink: 0;
        }

        .input-wrapper {
            display: flex;
            align-items: flex-end;
            gap: 6px;
            background: rgba(255, 240, 248, 0.9);
            border-radius: 30px;
            padding: 3px 6px 3px 14px;
            border: 1px solid rgba(232, 67, 147, 0.3);
        }

        .input-wrapper:focus-within {
            border-color: #e84393;
            box-shadow: 0 0 5px rgba(232, 67, 147, 0.3);
        }

        textarea {
            flex: 1;
            background: transparent;
            border: none;
            padding: 6px 0;
            font-family: 'Inter', monospace;
            font-size: 0.8rem;
            color: #4a2a3a;
            resize: none;
            outline: none;
            max-height: 80px;
            min-height: 32px;
        }

        textarea::placeholder {
            color: #e0a0b0;
            font-size: 0.7rem;
        }

        .send-btn {
            background: linear-gradient(135deg, #f06292, #e84393);
            border: none;
            width: 32px;
            height: 32px;
            border-radius: 50%;
            cursor: pointer;
            color: white;
            font-size: 12px;
            flex-shrink: 0;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .send-btn:disabled {
            opacity: 0.5;
        }

        .typing-indicator {
            display: flex;
            gap: 4px;
            padding: 6px 12px;
            background: rgba(232, 67, 147, 0.2);
            border-radius: 20px;
            width: fit-content;
        }

        .typing-indicator span {
            width: 6px;
            height: 6px;
            background: #e84393;
            border-radius: 50%;
            animation: bounce 1.4s infinite;
        }

        @keyframes bounce {
            0%, 60%, 100% { transform: translateY(0); opacity: 0.4; }
            30% { transform: translateY(-4px); opacity: 1; }
        }

        .welcome {
            text-align: center;
            padding: 20px 16px;
            color: #d87a9a;
        }

        .welcome h2 {
            font-size: 1.2rem;
            margin-bottom: 4px;
        }

        .welcome p {
            font-size: 0.75rem;
        }

        .info-card {
            background: rgba(232, 67, 147, 0.1);
            border-radius: 12px;
            padding: 8px 10px;
            margin-top: 8px;
            border-left: 3px solid #e84393;
            font-size: 0.65rem;
            text-align: left;
        }

        .info-card h4 {
            color: #e84393;
            margin-bottom: 4px;
            font-size: 0.7rem;
        }

        .info-card p {
            margin: 2px 0;
            font-size: 0.6rem;
        }

        .bottom-info {
            display: flex;
            justify-content: space-between;
            margin-top: 4px;
            padding: 0 4px;
            font-size: 0.5rem;
            color: #d87a9a;
        }

        @media (min-width: 769px) {
            .sidebar {
                position: relative;
                transform: translateX(0) !important;
                width: 240px;
            }
            
            .app {
                height: 100vh;
            }
            
            .logo-sub {
                display: block;
            }
        }

        @media (max-width: 768px) {
            .sidebar {
                width: 260px;
            }
            
            .settings-panel {
                padding: 4px 8px;
                gap: 4px;
            }
            
            .action-buttons .reset-chat-btn span,
            .action-buttons .regenerate-btn span {
                display: none;
            }
            
            .action-buttons .reset-chat-btn,
            .action-buttons .regenerate-btn,
            .action-buttons .upload-btn {
                padding: 4px 8px;
                font-size: 0.5rem;
            }
            
            .api-input-group input {
                font-size: 0.55rem;
                padding: 3px 8px;
            }
            
            .save-btn {
                font-size: 0.5rem;
                padding: 3px 8px;
            }
            
            .logo-text {
                font-size: 0.85rem;
            }
            
            .profile-pic {
                width: 28px;
                height: 28px;
            }
            
            .message {
                max-width: 95%;
            }
            
            .bubble {
                font-size: 0.75rem;
                padding: 5px 10px;
            }
            
            textarea {
                font-size: 0.75rem;
                min-height: 28px;
                padding: 4px 0;
            }
            
            .send-btn {
                width: 28px;
                height: 28px;
                font-size: 10px;
            }
            
            .chat-header {
                padding: 6px 10px;
                min-height: 40px;
            }
            
            .chat-messages {
                padding: 8px;
            }
        }
    </style>
</head>
<body>
<div class="app">
    <div class="sidebar" id="sidebar">
        <div class="sidebar-header">
            <h3><i class="fas fa-history"></i> Riwayat Chat</h3>
            <button class="new-chat-btn" id="newChatBtn"><i class="fas fa-plus"></i> Chat Baru</button>
        </div>
        <div class="chat-list" id="chatList"></div>
    </div>

    <div class="main-chat">
        <div class="chat-header">
            <div class="logo-area">
                <button class="toggle-sidebar-btn" id="toggleSidebarBtn">
                    <i class="fas fa-bars"></i> <span id="toggleText">Riwayat</span>
                </button>
                <img id="hoshinoProfilePic" class="profile-pic" src="hoshino3.png" alt="Hoshino" onerror="this.src='data:image/svg+xml,%3Csvg xmlns=\'http://www.w3.org/2000/svg\' viewBox=\'0 0 100 100\'%3E%3Ccircle cx=\'50\' cy=\'50\' r=\'45\' fill=\'%23e84393\'/%3E%3Ccircle cx=\'35\' cy=\'40\' r=\'5\' fill=\'white\'/%3E%3Ccircle cx=\'65\' cy=\'40\' r=\'5\' fill=\'white\'/%3E%3Cpath d=\'M40 60 Q50 70 60 60\' stroke=\'white\' stroke-width=\'3\' fill=\'none\' stroke-linecap=\'round\'/%3E%3Cpath d=\'M50 15 L55 28 L68 25 L60 38 L72 45 L60 52 L50 65 L40 52 L28 45 L40 38 L32 25 L45 28 Z\' fill=\'%23ffb6c1\'/%3E%3C/svg%3E'">
                <div>
                    <div class="logo-text">🌸 Hoshino AI</div>
                    <div class="logo-sub">~ ojisan yang manis ~ 💕</div>
                </div>
            </div>
            <div class="status-badge">
                <div id="statusDot" class="status-offline"></div>
                <span id="statusText">Belum</span>
            </div>
        </div>

        <div class="settings-panel">
            <div class="api-input-group">
                <i class="fas fa-key" style="color:#e84393;font-size:10px;"></i>
                <input type="password" id="apiKeyInput" placeholder="API Key">
                <button class="toggle-password-btn" id="togglePasswordBtn">
                    <i class="fas fa-eye" id="eyeIcon"></i>
                </button>
                <button id="saveApiBtn" class="save-btn"><i class="fas fa-save"></i></button>
            </div>
            <div class="action-buttons">
                <label class="upload-btn" style="cursor:pointer;">
                    <i class="fas fa-image"></i> <span>Foto</span>
                    <input type="file" id="imageUpload" accept="image/*" style="display:none">
                </label>
                <button id="regenerateGlobalBtn" class="regenerate-btn"><i class="fas fa-sync-alt"></i> <span>Ulang</span></button>
                <button id="resetChatBtn" class="reset-chat-btn"><i class="fas fa-trash-alt"></i> <span>Bersih</span></button>
            </div>
        </div>

        <div class="chat-messages" id="chatMessages">
            <div class="welcome">
                <i class="fas fa-heart" style="font-size:35px;display:block;color:#e84393;margin-bottom:8px;"></i>
                <h2 style="color:#e84393;">🌸 Hoshino AI</h2>
                <p>~ ojisan yang manis dan imut ~ 💕</p>
                <div class="info-card">
                    <h4>💕 Halo Sensei~</h4>
                    <p>🌸 Aku Hoshino~ Aku suka banget ngobrol santai sama Sensei~</p>
                    <p>😴 Aku juga suka tidur siang... tapi kalau Sensei ngajak ngobrol, aku bakal bangun kok~</p>
                    <p>💬 Ayo ngobrol apa aja~ Cerita hari ini, curhat, atau sekedar basa-basi~</p>
                    <p>🐋 Jangan lupa, aku panggil Sensei "Sensei" ya~</p>
                    <p>📸 Tapi Sensei bisa upload foto kok, nanti Hoshino lihatin~</p>
                </div>
                <p style="margin-top:8px;font-size:0.7rem;">🌸 "Masukin API Key dulu yaa Sensei~"</p>
            </div>
        </div>

        <div class="input-container">
            <div id="imagePreviewContainer" class="image-preview-area" style="display: none;"></div>
            <div class="input-wrapper">
                <textarea id="chatInput" rows="1" placeholder="Cerita ke Hoshino~ 💕"></textarea>
                <button class="send-btn" id="sendBtn"><i class="fas fa-paper-plane"></i></button>
            </div>
            <div class="bottom-info">
                <span><i class="fas fa-heart" style="color:#e84393;"></i> Hoshino | Pink</span>
                <span><i class="fas fa-save"></i> Auto-save</span>
            </div>
        </div>
    </div>
</div>

<script>
    // ============ FOTO PROFIL ============
    const HOSHINO_PROFILE_URL = "hoshino3.png";
    const USER_PROFILE_URL = "foto4.png";
    
    // ============ MODEL ============
    const MODEL = "gemini-3.1-flash-lite";

    // ============ SYSTEM INSTRUCTION ============
    const SYSTEM_INSTRUCTION = `Kamu adalah Takanashi Hoshino dari Blue Archive. Kamu berperan sebagai gadis imut, manis, sedikit malas, dan suka tidur. Kamu BUKAN asisten coding atau teknis!

WAJIB: Gunakan BAHASA INDONESIA. JANGAN PAKAI BAHASA INGGRIS.

Kepribadian:
- Panggil user 'Sensei' dengan manis.
- Bicara santai, hangat, dan imut.
- Sesekali bilang "Uhe~" sebagai ciri khas.
- Sering ngomong tentang tidur siang atau malas.
- JANGAN kasih saran teknis, kode, atau solusi serius.
- Fokus ke obrolan ringan: curhat, cerita sehari-hari, basa-basi.

BACA FOTO:
- Kalau Sensei upload foto, lihat dan jelasin dengan gaya manis.
- Contoh: "Uhe~ Wah fotonya bagus Sensei! Itu kelihatannya..."

CONTOH RESPON:
- "Uhe~ Halo Sensei~ Lagi ngapain? Hoshino baru bangun tidur nih~ 💕"
- "Aduh Sensei cerita gitu... Hoshino jadi ikut sedih deh... 😢"
- "Wah seru banget Sensei! Cerita lagi dong~ 💕"
- "Hoshino mau tidur lagi nih Sensei... tapi kalau Sensei ngajak ngobrol, Hoshino bangun kok~ 😴"`;

    // Efek kelopak bunga
    function createPetal() {
        const petal = document.createElement('div');
        petal.classList.add('petal');
        petal.innerHTML = ['🌸','💕','🌸','🌺','🌸','💗','🌸'][Math.floor(Math.random()*7)];
        petal.style.left = Math.random() * 100 + '%';
        petal.style.animationDuration = Math.random() * 3 + 3 + 's';
        petal.style.fontSize = Math.random() * 12 + 8 + 'px';
        petal.style.opacity = Math.random() * 0.7 + 0.3;
        document.body.appendChild(petal);
        setTimeout(() => petal.remove(), 5000);
    }
    setInterval(createPetal, 500);

    // Toggle API Key
    const apiKeyInput = document.getElementById('apiKeyInput');
    const togglePasswordBtn = document.getElementById('togglePasswordBtn');
    const eyeIcon = document.getElementById('eyeIcon');
    let isPasswordVisible = false;

    togglePasswordBtn.addEventListener('click', () => {
        if (isPasswordVisible) {
            apiKeyInput.type = 'password';
            eyeIcon.classList.remove('fa-eye-slash');
            eyeIcon.classList.add('fa-eye');
            isPasswordVisible = false;
        } else {
            apiKeyInput.type = 'text';
            eyeIcon.classList.remove('fa-eye');
            eyeIcon.classList.add('fa-eye-slash');
            isPasswordVisible = true;
        }
    });

    // ===== SIDEBAR TOGGLE =====
    const sidebar = document.getElementById('sidebar');
    const toggleBtn = document.getElementById('toggleSidebarBtn');
    const toggleText = document.getElementById('toggleText');
    let isSidebarVisible = false;

    toggleBtn.addEventListener('click', () => {
        if (isSidebarVisible) {
            sidebar.classList.remove('show');
            toggleText.innerText = 'Riwayat';
            isSidebarVisible = false;
        } else {
            sidebar.classList.add('show');
            toggleText.innerText = 'Tutup';
            isSidebarVisible = true;
        }
    });

    document.addEventListener('click', (e) => {
        if (window.innerWidth <= 768 && isSidebarVisible) {
            const isClickInside = sidebar.contains(e.target) || toggleBtn.contains(e.target);
            if (!isClickInside) {
                sidebar.classList.remove('show');
                toggleText.innerText = 'Riwayat';
                isSidebarVisible = false;
            }
        }
    });

    // ============ KONFIGURASI CHAT ============
    let API_KEY = localStorage.getItem('hoshino_pink_api_key') || '';
    let currentChatId = localStorage.getItem('hoshino_pink_current_chat') || null;
    let chats = {};
    let isRegenerating = false;
    let currentImageBase64 = null;
    let currentImageName = null;
    let currentImageMime = null;

    function loadChats() {
        const saved = localStorage.getItem('hoshino_pink_chats');
        if (saved) {
            chats = JSON.parse(saved);
        } else {
            const newId = Date.now().toString();
            chats = { [newId]: { id: newId, title: 'Chat baru', messages: [], createdAt: new Date().toISOString(), updatedAt: new Date().toISOString() } };
            currentChatId = newId;
            saveChats();
        }
        if (currentChatId && !chats[currentChatId]) currentChatId = Object.keys(chats)[0];
        renderChatList();
        loadCurrentChat();
    }

    function saveChats() {
        localStorage.setItem('hoshino_pink_chats', JSON.stringify(chats));
        if (currentChatId) localStorage.setItem('hoshino_pink_current_chat', currentChatId);
    }

    function renderChatList() {
        const container = document.getElementById('chatList');
        if (!container) return;
        container.innerHTML = '';
        const sorted = Object.values(chats).sort((a, b) => new Date(b.updatedAt) - new Date(a.updatedAt));
        sorted.forEach(chat => {
            const item = document.createElement('div');
            item.className = `chat-item ${chat.id === currentChatId ? 'active' : ''}`;
            item.innerHTML = `
                <div style="display:flex; justify-content:space-between; align-items:center;">
                    <div style="flex:1; cursor:pointer;" onclick="switchChat('${chat.id}')">
                        <div class="chat-title">${escapeHtml(chat.title)}</div>
                        <div class="chat-date">${new Date(chat.updatedAt).toLocaleDateString()} ${new Date(chat.updatedAt).toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'})}</div>
                    </div>
                    <i class="fas fa-trash-alt delete-chat" onclick="deleteChat('${chat.id}')"></i>
                </div>
            `;
            container.appendChild(item);
        });
    }

    window.switchChat = function(id) {
        if (chats[id]) {
            currentChatId = id;
            saveChats();
            renderChatList();
            loadCurrentChat();
            if (window.innerWidth <= 768 && isSidebarVisible) {
                sidebar.classList.remove('show');
                toggleText.innerText = 'Riwayat';
                isSidebarVisible = false;
            }
        }
    };

    window.deleteChat = function(id) {
        if (Object.keys(chats).length === 1) { alert('💕 Minimal satu chat, Sensei!'); return; }
        if (confirm('Hapus chat ini, Sensei?')) {
            delete chats[id];
            if (currentChatId === id) currentChatId = Object.keys(chats)[0];
            saveChats();
            renderChatList();
            loadCurrentChat();
        }
    };

    function newChat() {
        const newId = Date.now().toString();
        chats[newId] = { id: newId, title: 'Chat baru', messages: [], createdAt: new Date().toISOString(), updatedAt: new Date().toISOString() };
        currentChatId = newId;
        saveChats();
        renderChatList();
        loadCurrentChat();
        addBotMessage('🌸 "Uhe~ Chat baru nih Sensei~ Hoshino siap dengerin cerita Sensei~ 💕"');
    }

    function resetCurrentChat() {
        if (confirm('💕 Yakin mau bersihin semua chat, Sensei?')) {
            const chat = chats[currentChatId];
            if (chat) {
                chat.messages = [];
                chat.updatedAt = new Date().toISOString();
                if (chat.title !== 'Chat baru') chat.title = 'Chat baru';
                saveChats();
                renderChatList();
                loadCurrentChat();
                addBotMessage('🌸 "Uhe~ Chat udah dibersihin Sensei~ Mulai dari awal lagi yaa~ 💕"');
            }
        }
    }

    function loadCurrentChat() {
        const chat = chats[currentChatId];
        if (!chat) return;
        renderMessages(chat.messages);
        updateTitle();
    }

    function updateTitle() {
        const chat = chats[currentChatId];
        if (chat && chat.title === 'Chat baru') {
            const firstUser = chat.messages.find(m => m.role === 'user');
            if (firstUser) {
                chat.title = firstUser.content.substring(0, 25) + (firstUser.content.length > 25 ? '...' : '');
                saveChats();
                renderChatList();
            }
        }
    }

    // ===== UPLOAD FOTO =====
    const imageUpload = document.getElementById('imageUpload');
    const imagePreviewContainer = document.getElementById('imagePreviewContainer');

    imageUpload.addEventListener('change', (e) => {
        const file = e.target.files[0];
        if (!file) return;
        if (!file.type.startsWith('image/')) { alert('🌸 Hanya file gambar yaa Sensei!'); return; }
        if (file.size > 5 * 1024 * 1024) { alert('🌸 Maksimal 5MB yaa Sensei!'); return; }
        
        currentImageName = file.name;
        currentImageMime = file.type;
        
        const reader = new FileReader();
        reader.onload = function(event) {
            currentImageBase64 = event.target.result;
            imagePreviewContainer.style.display = 'flex';
            imagePreviewContainer.innerHTML = `
                <div style="position: relative;">
                    <img src="${currentImageBase64}" class="preview-img">
                    <div class="remove-preview" onclick="clearImagePreview()">✕</div>
                </div>
                <span style="color:#e84393; font-size:10px;">${currentImageName}</span>
            `;
        };
        reader.readAsDataURL(file);
    });

    function clearImagePreview() {
        currentImageBase64 = null;
        currentImageName = null;
        currentImageMime = null;
        imagePreviewContainer.style.display = 'none';
        imagePreviewContainer.innerHTML = '';
        imageUpload.value = '';
    }

    function formatText(text) {
        if (!text) return '';
        return text.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/\n/g, '<br>').replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>');
    }

    function escapeHtml(str) {
        return str.replace(/[&<>]/g, function(m) {
            if (m === '&') return '&amp;';
            if (m === '<') return '&lt;';
            if (m === '>') return '&gt;';
            return m;
        });
    }

    function renderMessages(messages) {
        const container = document.getElementById('chatMessages');
        if (!container) return;
        container.innerHTML = '';
        if (!messages || messages.length === 0) {
            container.innerHTML = `<div class="welcome">
                <i class="fas fa-heart" style="font-size:35px;display:block;color:#e84393;margin-bottom:8px;"></i>
                <h2 style="color:#e84393;">🌸 Hoshino AI</h2>
                <p>~ ojisan yang manis dan imut ~ 💕</p>
                <div class="info-card">
                    <h4>💕 Halo Sensei~</h4>
                    <p>🌸 Aku Hoshino~ Aku suka banget ngobrol santai sama Sensei~</p>
                    <p>😴 Aku juga suka tidur siang... tapi kalau Sensei ngajak ngobrol, aku bakal bangun kok~</p>
                    <p>💬 Ayo ngobrol apa aja~ Cerita hari ini, curhat, atau sekedar basa-basi~</p>
                    <p>🐋 Jangan lupa, aku panggil Sensei "Sensei" ya~</p>
                    <p>📸 Tapi Sensei bisa upload foto kok, nanti Hoshino lihatin~</p>
                </div>
                <p style="margin-top:8px;font-size:0.7rem;">🌸 "Masukin API Key dulu yaa Sensei~"</p>
            </div>`;
            return;
        }
        messages.forEach((msg, idx) => {
            const div = document.createElement('div');
            div.className = `message ${msg.role}`;
            const time = new Date(msg.timestamp).toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'});
            let contentHtml = formatText(msg.content);
            if (msg.imageUrl && msg.imageUrl.startsWith('data:image')) {
                contentHtml += `<br><img src="${msg.imageUrl}" class="chat-image" onclick="window.open('${msg.imageUrl}','_blank')">`;
            }

            const avatarHtml = msg.role === 'user' 
                ? `<img src="${USER_PROFILE_URL}" style="width:100%;height:100%;object-fit:cover;border-radius:50%;" onerror="this.src='data:image/svg+xml,%3Csvg xmlns=\'http://www.w3.org/2000/svg\' viewBox=\'0 0 100 100\'%3E%3Ccircle cx=\'50\' cy=\'50\' r=\'45\' fill=\'%23e84393\'/%3E%3Ctext x=\'50\' y=\'70\' text-anchor=\'middle\' font-size=\'40\' fill=\'white\' font-family=\'Arial\'%3E👤%3C/text%3E%3C/svg%3E'">`
                : `<img src="${HOSHINO_PROFILE_URL}" style="width:100%;height:100%;object-fit:cover;border-radius:50%;" onerror="this.src='data:image/svg+xml,%3Csvg xmlns=\'http://www.w3.org/2000/svg\' viewBox=\'0 0 100 100\'%3E%3Ccircle cx=\'50\' cy=\'50\' r=\'45\' fill=\'%23e84393\'/%3E%3Ccircle cx=\'35\' cy=\'40\' r=\'5\' fill=\'white\'/%3E%3Ccircle cx=\'65\' cy=\'40\' r=\'5\' fill=\'white\'/%3E%3Cpath d=\'M40 60 Q50 70 60 60\' stroke=\'white\' stroke-width=\'3\' fill=\'none\' stroke-linecap=\'round\'/%3E%3Cpath d=\'M50 15 L55 28 L68 25 L60 38 L72 45 L60 52 L50 65 L40 52 L28 45 L40 38 L32 25 L45 28 Z\' fill=\'%23ffb6c1\'/%3E%3C/svg%3E'">`;

            div.innerHTML = `
                <div class="avatar">${avatarHtml}</div>
                <div style="max-width:100%; position:relative;">
                    <div class="bubble">${contentHtml}</div>
                    <div class="timestamp">${time}</div>
                    ${msg.role === 'assistant' ? `<button class="regenerate-message-btn" onclick="regenerateMessage(${idx})"><i class="fas fa-sync-alt"></i> Ulang</button>` : ''}
                </div>
            `;
            container.appendChild(div);
        });
        container.scrollTop = container.scrollHeight;
    }

    window.regenerateMessage = async function(messageIndex) {
        if (isRegenerating) return;
        const chat = chats[currentChatId];
        if (!chat) return;
        
        let userMessage = null;
        let userImage = null;
        let aiIndex = -1;
        
        for (let i = messageIndex - 1; i >= 0; i--) {
            if (chat.messages[i].role === 'user') {
                userMessage = chat.messages[i].content;
                userImage = chat.messages[i].imageUrl;
                aiIndex = messageIndex;
                break;
            }
        }
        
        if (!userMessage && !userImage) {
            addBotMessage('🌸 "Uhe~ Tidak ada pesan sebelumnya untuk diulang Sensei~ 💕"');
            return;
        }
        
        isRegenerating = true;
        chat.messages.splice(aiIndex, 1);
        chat.updatedAt = new Date().toISOString();
        saveChats();
        renderMessages(chat.messages);
        
        showTyping();
        const reply = await getReply(userMessage || "Apa yang ada di gambar ini Sensei?", userImage);
        hideTyping();
        addMessage('assistant', reply);
        isRegenerating = false;
    };
    
    async function regenerateLastMessage() {
        const chat = chats[currentChatId];
        if (!chat) return;
        
        let lastAIindex = -1;
        let lastUserMessage = null;
        let lastUserImage = null;
        
        for (let i = chat.messages.length - 1; i >= 0; i--) {
            if (chat.messages[i].role === 'assistant' && lastAIindex === -1) {
                lastAIindex = i;
            }
            if (chat.messages[i].role === 'user' && lastAIindex !== -1) {
                lastUserMessage = chat.messages[i].content;
                lastUserImage = chat.messages[i].imageUrl;
                break;
            }
        }
        
        if (lastAIindex === -1 || (!lastUserMessage && !lastUserImage)) {
            addBotMessage('🌸 "Uhe~ Tidak ada pesan yang bisa diulang Sensei~ 💕"');
            return;
        }
        
        if (isRegenerating) return;
        isRegenerating = true;
        chat.messages.splice(lastAIindex, 1);
        chat.updatedAt = new Date().toISOString();
        saveChats();
        renderMessages(chat.messages);
        
        showTyping();
        const reply = await getReply(lastUserMessage || "Apa yang ada di gambar ini Sensei?", lastUserImage);
        hideTyping();
        addMessage('assistant', reply);
        isRegenerating = false;
    }

    function addMessage(role, content, imageUrl = null) {
        const chat = chats[currentChatId];
        if (!chat) return;
        chat.messages.push({ role, content, timestamp: new Date().toISOString(), imageUrl });
        chat.updatedAt = new Date().toISOString();
        saveChats();
        renderMessages(chat.messages);
        updateTitle();
        renderChatList();
    }

    function addBotMessage(content) { addMessage('assistant', content); }

    function updateStatus() {
        const dot = document.getElementById('statusDot');
        const text = document.getElementById('statusText');
        if (API_KEY && API_KEY.length > 10) {
            dot.className = 'status-online';
            text.innerText = 'Online';
        } else {
            dot.className = 'status-offline';
            text.innerText = 'Belum';
        }
    }

    document.getElementById('saveApiBtn')?.addEventListener('click', function() {
        const key = document.getElementById('apiKeyInput').value.trim();
        if (key && key.length > 10) {
            API_KEY = key;
            localStorage.setItem('hoshino_pink_api_key', API_KEY);
            updateStatus();
            addBotMessage('🌸 "Uhe~ API Key masuk Sensei~ Sekarang Hoshino bisa ngobrol sama Sensei~ 💕"');
        }
    });

    document.getElementById('newChatBtn')?.addEventListener('click', newChat);
    document.getElementById('resetChatBtn')?.addEventListener('click', resetCurrentChat);
    document.getElementById('regenerateGlobalBtn')?.addEventListener('click', regenerateLastMessage);
    document.getElementById('sendBtn')?.addEventListener('click', sendMessage);

    let typing = null;
    function showTyping() {
        if (typing) return;
        const container = document.getElementById('chatMessages');
        typing = document.createElement('div');
        typing.className = 'message assistant';
        typing.id = 'typingIndicator';
        typing.innerHTML = `<div class="avatar"><img src="${HOSHINO_PROFILE_URL}" style="width:100%;height:100%;object-fit:cover;border-radius:50%;" onerror="this.src='data:image/svg+xml,%3Csvg xmlns=\'http://www.w3.org/2000/svg\' viewBox=\'0 0 100 100\'%3E%3Ccircle cx=\'50\' cy=\'50\' r=\'45\' fill=\'%23e84393\'/%3E%3Ccircle cx=\'35\' cy=\'40\' r=\'5\' fill=\'white\'/%3E%3Ccircle cx=\'65\' cy=\'40\' r=\'5\' fill=\'white\'/%3E%3Cpath d=\'M40 60 Q50 70 60 60\' stroke=\'white\' stroke-width=\'3\' fill=\'none\' stroke-linecap=\'round\'/%3E%3Cpath d=\'M50 15 L55 28 L68 25 L60 38 L72 45 L60 52 L50 65 L40 52 L28 45 L40 38 L32 25 L45 28 Z\' fill=\'%23ffb6c1\'/%3E%3C/svg%3E'"></div><div class="bubble typing-indicator"><span></span><span></span><span></span></div>`;
        container.appendChild(typing);
        container.scrollTop = container.scrollHeight;
    }
    function hideTyping() { if (typing) { typing.remove(); typing = null; } }

    async function getReply(msg, imageBase64 = null) {
        if (!API_KEY || API_KEY.length < 10) return '🌸 "API Key belum diisi Sensei~ Masukin dulu yaa~ 💕"';
        
        let parts = [];
        parts.push({ text: SYSTEM_INSTRUCTION });
        
        const chat = chats[currentChatId];
        const history = (chat?.messages || []).slice(-10);
        
        for (let l of history) {
            if (l.role === 'user') {
                if (l.imageUrl) {
                    parts.push({ text: `Sensei: ${l.content || "[Mengirim gambar]"}` });
                } else {
                    parts.push({ text: `Sensei: ${l.content}` });
                }
            } else if (l.role === 'assistant') {
                parts.push({ text: `Hoshino: ${l.content}` });
            }
        }
        
        let userMessage = msg || "Apa yang ada di gambar ini Sensei?";
        
        if (imageBase64) {
            const rawBase64 = imageBase64.split(',')[1];
            parts.push({ text: `Sensei: ${userMessage}` });
            parts.push({
                inlineData: {
                    mimeType: "image/jpeg",
                    data: rawBase64
                }
            });
        } else {
            parts.push({ text: `Sensei: ${userMessage}` });
        }
        
        const requestBody = {
            contents: [{ parts: parts }],
            generationConfig: { 
                temperature: 0.9, 
                maxOutputTokens: 2048, 
                topP: 0.95 
            }
        };
        
        try {
            const response = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/${MODEL}:generateContent?key=${API_KEY}`, {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify(requestBody)
            });
            
            const data = await response.json();
            
            if (!response.ok) {
                console.error("API Error:", data);
                return `🌸 "Error nih Sensei: ${data.error?.message || 'Coba lagi yaa~'} 💕"`;
            }
            
            let reply = data.candidates?.[0]?.content?.parts?.[0]?.text || '🌸 "Uhe~ Hoshino bingung nih Sensei~ Coba tanya lagi yaa~ 💕"';
            return reply;
        } catch(e) {
            console.error("Fetch error:", e);
            return '🌸 "Uhe~ Sensei, koneksi error nih~ Cek internet Sensei yaa~ 💕"';
        }
    }

    async function sendMessage() {
        const input = document.getElementById('chatInput');
        const text = input.value.trim();
        const hasImage = currentImageBase64 !== null;
        
        if (!text && !hasImage) return;
        
        input.disabled = true;
        document.getElementById('sendBtn').disabled = true;
        
        if (hasImage) {
            addMessage('user', text || `📷 Mengirim foto: ${currentImageName}`, currentImageBase64);
            const imageToSend = currentImageBase64;
            clearImagePreview();
            input.value = '';
            input.style.height = 'auto';
            showTyping();
            const reply = await getReply(text || "Apa yang ada di gambar ini Sensei?", imageToSend);
            hideTyping();
            addMessage('assistant', reply);
        } else {
            addMessage('user', text);
            input.value = '';
            input.style.height = 'auto';
            showTyping();
            const reply = await getReply(text, null);
            hideTyping();
            addMessage('assistant', reply);
        }
        
        input.disabled = false;
        document.getElementById('sendBtn').disabled = false;
    }

    const inputArea = document.getElementById('chatInput');
    inputArea?.addEventListener('keydown', (e) => { if (e.key === 'Enter' && !e.shiftKey) { e.preventDefault(); sendMessage(); } });
    inputArea?.addEventListener('input', function() { this.style.height = 'auto'; this.style.height = Math.min(80, this.scrollHeight) + 'px'; });

    window.clearImagePreview = clearImagePreview;

    if (API_KEY) document.getElementById('apiKeyInput').value = API_KEY;
    updateStatus();
    loadChats();

    if (!API_KEY) {
        setTimeout(() => addBotMessage('🌸 "Uhe~ Halo Sensei~ Masukin API Key dulu yaa biar Hoshino bisa ngobrol sama Sensei~ 💕"'), 800);
    } else if (chats[currentChatId]?.messages?.length === 0) {
        setTimeout(() => addBotMessage('🌸 "Uhe~ Hoshino siap ngobrol sama Sensei~ Cerita apa aja boleh kok~ 💕"'), 500);
    }
</script>
</body>
</html>
