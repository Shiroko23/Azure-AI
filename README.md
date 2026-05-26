
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Azure AI | Moon Theme 🌙</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #0a0a1a 0%, #0a0a2a 50%, #050515 100%);
            font-family: 'Inter', system-ui, sans-serif;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .star {
            position: fixed;
            background: white;
            border-radius: 50%;
            pointer-events: none;
            z-index: 999;
            animation: twinkle 2s infinite ease-in-out;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.2; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.2); }
        }

        .app {
            width: 100%;
            max-width: 1100px;
            height: 100vh;
            background: rgba(10, 10, 30, 0.92);
            backdrop-filter: blur(8px);
            display: flex;
            box-shadow: 0 0 50px rgba(150, 100, 255, 0.25);
            overflow: hidden;
            border-left: 1px solid rgba(150, 100, 255, 0.3);
            border-right: 1px solid rgba(150, 100, 255, 0.3);
        }

        .sidebar {
            width: 260px;
            background: rgba(5, 5, 20, 0.95);
            border-right: 1px solid rgba(150, 100, 255, 0.3);
            display: flex;
            flex-direction: column;
            overflow: hidden;
            transition: width 0.3s ease;
            flex-shrink: 0;
        }

        .sidebar.hidden {
            width: 0;
            border-right: none;
        }

        .sidebar.hidden .sidebar-header,
        .sidebar.hidden .chat-list {
            display: none;
        }

        .sidebar-header {
            padding: 16px;
            border-bottom: 1px solid rgba(150, 100, 255, 0.3);
        }

        .sidebar-header h3 {
            color: #aa88ff;
            font-size: 0.85rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .new-chat-btn {
            background: linear-gradient(135deg, #8866ff, #6644cc);
            border: none;
            padding: 8px 12px;
            border-radius: 30px;
            color: white;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.75rem;
            width: 100%;
            margin-top: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .chat-list {
            flex: 1;
            overflow-y: auto;
            padding: 10px;
        }

        .chat-item {
            background: rgba(30, 20, 60, 0.5);
            border-radius: 12px;
            padding: 10px;
            margin-bottom: 8px;
            cursor: pointer;
            transition: 0.2s;
            border: 1px solid rgba(150, 100, 255, 0.2);
        }

        .chat-item:hover {
            background: rgba(136, 102, 255, 0.2);
        }

        .chat-item.active {
            background: rgba(136, 102, 255, 0.3);
            border-color: #8866ff;
        }

        .chat-title {
            color: #ccbbff;
            font-size: 0.8rem;
            font-weight: 500;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .chat-date {
            color: #8877aa;
            font-size: 0.6rem;
            margin-top: 4px;
        }

        .delete-chat {
            float: right;
            color: #ff8888;
            cursor: pointer;
            font-size: 0.7rem;
            opacity: 0;
        }

        .chat-item:hover .delete-chat {
            opacity: 1;
        }

        .toggle-sidebar-btn {
            background: rgba(136, 102, 255, 0.3);
            border: 1px solid rgba(150, 100, 255, 0.4);
            border-radius: 30px;
            padding: 6px 12px;
            cursor: pointer;
            color: #ccbbff;
            font-size: 0.7rem;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .main-chat {
            flex: 1;
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        .chat-header {
            padding: 12px 20px;
            background: rgba(5, 5, 20, 0.95);
            border-bottom: 1px solid rgba(150, 100, 255, 0.3);
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .logo-area {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(145deg, #8866ff, #6644cc);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            box-shadow: 0 0 15px rgba(136, 102, 255, 0.5);
            animation: moonGlow 3s infinite ease-in-out;
        }

        @keyframes moonGlow {
            0%, 100% { box-shadow: 0 0 15px rgba(136, 102, 255, 0.3); }
            50% { box-shadow: 0 0 25px rgba(136, 102, 255, 0.7); }
        }

        .logo-text {
            font-weight: 800;
            font-size: 1.2rem;
            background: linear-gradient(135deg, #fff, #ccbbff, #8866ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .logo-sub {
            font-size: 0.6rem;
            color: #aa88ff;
        }

        .status-badge {
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 0.65rem;
            background: rgba(136, 102, 255, 0.2);
            padding: 4px 10px;
            border-radius: 20px;
        }

        .status-online {
            width: 8px;
            height: 8px;
            background: #88ffaa;
            border-radius: 50%;
            box-shadow: 0 0 5px #88ffaa;
        }

        .status-offline {
            width: 8px;
            height: 8px;
            background: #ff6644;
            border-radius: 50%;
        }

        .settings-panel {
            background: rgba(5, 5, 20, 0.95);
            border-bottom: 1px solid rgba(150, 100, 255, 0.3);
            padding: 10px 20px;
            display: flex;
            align-items: center;
            gap: 10px;
            flex-wrap: wrap;
        }

        .api-input-group {
            display: flex;
            align-items: center;
            gap: 8px;
            flex: 1;
        }

        .api-input-group input {
            flex: 1;
            background: #0a0a2a;
            border: 1px solid rgba(150, 100, 255, 0.4);
            border-radius: 30px;
            padding: 8px 14px;
            color: #ccbbff;
            font-size: 0.75rem;
            outline: none;
            font-family: monospace;
        }

        .api-input-group input:focus {
            border-color: #8866ff;
            box-shadow: 0 0 5px rgba(136, 102, 255, 0.3);
        }

        .toggle-password-btn {
            background: rgba(136, 102, 255, 0.3);
            border: 1px solid rgba(150, 100, 255, 0.4);
            border-radius: 50%;
            width: 32px;
            height: 32px;
            cursor: pointer;
            color: #ccbbff;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .save-btn {
            background: linear-gradient(135deg, #8866ff, #6644cc);
            border: none;
            padding: 8px 16px;
            border-radius: 30px;
            color: white;
            cursor: pointer;
            font-size: 0.7rem;
        }

        .action-buttons {
            display: flex;
            gap: 8px;
            align-items: center;
        }

        .reset-chat-btn, .guide-btn, .regenerate-btn {
            background: rgba(136, 102, 255, 0.2);
            border: 1px solid rgba(150, 100, 255, 0.3);
            padding: 6px 12px;
            border-radius: 30px;
            color: #ccbbff;
            cursor: pointer;
            font-size: 0.7rem;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .reset-chat-btn:hover, .guide-btn:hover, .regenerate-btn:hover {
            background: rgba(136, 102, 255, 0.4);
        }

        .chat-messages {
            flex: 1;
            overflow-y: auto;
            padding: 20px;
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .chat-messages::-webkit-scrollbar {
            width: 4px;
        }
        .chat-messages::-webkit-scrollbar-thumb {
            background: #8866ff;
            border-radius: 10px;
        }

        .message {
            display: flex;
            align-items: flex-start;
            gap: 10px;
            max-width: 85%;
            animation: fadeIn 0.3s ease;
            position: relative;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .message.user {
            align-self: flex-end;
            flex-direction: row-reverse;
        }

        .avatar {
            width: 36px;
            height: 36px;
            border-radius: 50%;
            background: linear-gradient(145deg, #1a1a4a, #0a0a3a);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 16px;
            flex-shrink: 0;
            border: 1px solid rgba(150, 100, 255, 0.3);
        }

        .user .avatar {
            background: linear-gradient(135deg, #8866ff, #6644cc);
            border: none;
        }

        .bubble {
            background: #0a0a2a;
            padding: 10px 16px;
            border-radius: 20px;
            font-size: 0.9rem;
            line-height: 1.4;
            color: #d0ccff;
            border: 1px solid rgba(150, 100, 255, 0.15);
        }

        .user .bubble {
            background: linear-gradient(135deg, #8866ff, #6644cc);
            border: none;
            color: white;
        }

        .timestamp {
            font-size: 0.6rem;
            color: #8877aa;
            margin-top: 4px;
            margin-left: 46px;
        }

        .user .timestamp {
            text-align: right;
            margin-right: 46px;
        }

        /* ========== GARIS PINGGIR KODE (BIRU UNGU) ========== */
        pre {
            background: #0a0a2a;
            padding: 12px;
            border-radius: 10px;
            overflow-x: auto;
            font-size: 0.75rem;
            font-family: 'Courier New', monospace;
            line-height: 1.5;
            color: #e0dcff;
            margin: 8px 0;
            border-left: 4px solid #8866ff;
        }

        code {
            font-family: 'Courier New', monospace;
        }

        .bubble code:not(pre code) {
            background: #1a1a4a;
            padding: 2px 6px;
            border-radius: 6px;
            font-size: 0.85rem;
            color: #aa88ff;
        }

        .regenerate-message-btn {
            position: absolute;
            bottom: -20px;
            right: 0;
            background: rgba(136, 102, 255, 0.3);
            border: none;
            border-radius: 20px;
            padding: 4px 10px;
            font-size: 0.6rem;
            color: #ccbbff;
            cursor: pointer;
            display: none;
            gap: 5px;
            align-items: center;
        }

        .message.assistant:hover .regenerate-message-btn {
            display: flex;
        }

        .input-container {
            background: rgba(5, 5, 20, 0.95);
            border-top: 1px solid rgba(150, 100, 255, 0.3);
            padding: 12px 20px 20px;
        }

        .input-wrapper {
            display: flex;
            align-items: flex-end;
            gap: 10px;
            background: #0a0a2a;
            border-radius: 30px;
            padding: 5px 8px 5px 18px;
            border: 1px solid rgba(150, 100, 255, 0.3);
        }

        .input-wrapper:focus-within {
            border-color: #8866ff;
            box-shadow: 0 0 5px rgba(136, 102, 255, 0.3);
        }

        textarea {
            flex: 1;
            background: transparent;
            border: none;
            padding: 10px 0;
            font-family: 'Inter', monospace;
            font-size: 0.9rem;
            color: #d0ccff;
            resize: none;
            outline: none;
            max-height: 100px;
        }

        textarea::placeholder {
            color: #6655aa;
        }

        .send-btn {
            background: linear-gradient(135deg, #8866ff, #6644cc);
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            color: white;
            font-size: 16px;
        }

        .send-btn:disabled {
            opacity: 0.5;
        }

        .typing-indicator {
            display: flex;
            gap: 5px;
            padding: 8px 15px;
            background: #0a0a2a;
            border-radius: 25px;
            width: fit-content;
        }

        .typing-indicator span {
            width: 7px;
            height: 7px;
            background: #8866ff;
            border-radius: 50%;
            animation: bounce 1.4s infinite;
        }

        @keyframes bounce {
            0%, 60%, 100% { transform: translateY(0); opacity: 0.4; }
            30% { transform: translateY(-5px); opacity: 1; }
        }

        .welcome {
            text-align: center;
            padding: 30px 20px;
            color: #aa99dd;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.85);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background: linear-gradient(135deg, #0a0a2a, #050520);
            max-width: 400px;
            width: 90%;
            border-radius: 24px;
            padding: 20px;
            border: 1px solid rgba(136, 102, 255, 0.5);
            color: #d0ccff;
        }

        .modal-content h3 {
            color: #aa88ff;
            margin-bottom: 15px;
        }

        .modal-content ol {
            padding-left: 20px;
            margin: 10px 0;
        }

        .close-modal {
            background: linear-gradient(135deg, #8866ff, #6644cc);
            border: none;
            padding: 8px;
            border-radius: 30px;
            color: white;
            margin-top: 15px;
            cursor: pointer;
            width: 100%;
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
                    <i class="fas fa-bars"></i> <span id="toggleText">Tampilkan</span>
                </button>
                <div class="logo-icon"><i class="fas fa-moon"></i></div>
                <div>
                    <div class="logo-text">Azure AI</div>
                    <div class="logo-sub">~ moon theme ~ 🌙</div>
                </div>
            </div>
            <div class="status-badge">
                <div id="statusDot" class="status-offline"></div>
                <span id="statusText">Belum Connect</span>
            </div>
        </div>

        <div class="settings-panel">
            <div class="api-input-group">
                <i class="fas fa-key" style="color:#aa88ff;"></i>
                <input type="password" id="apiKeyInput" placeholder="OpenRouter API Key">
                <button class="toggle-password-btn" id="togglePasswordBtn">
                    <i class="fas fa-eye" id="eyeIcon"></i>
                </button>
                <button id="saveApiBtn" class="save-btn"><i class="fas fa-save"></i> Simpan</button>
            </div>
            <div class="action-buttons">
                <button id="regenerateGlobalBtn" class="regenerate-btn"><i class="fas fa-sync-alt"></i> Ulang Chat Terakhir</button>
                <button id="resetChatBtn" class="reset-chat-btn"><i class="fas fa-trash-alt"></i> Bersihkan Chat</button>
                <button id="guideBtn" class="guide-btn"><i class="fas fa-question-circle"></i> Panduan</button>
            </div>
        </div>

        <div class="chat-messages" id="chatMessages">
            <div class="welcome">
                <i class="fas fa-moon" style="font-size:45px;margin-bottom:10px;display:block;color:#aa88ff;"></i>
                <h2 style="color:#aa88ff;">Azure AI 🌙</h2>
                <p>~ moonlight intelligence ~</p>
                <p style="margin-top:15px;font-size:0.8rem;">🌙 "Masukin API Key dulu yaa Tuan..."</p>
            </div>
        </div>

        <div class="input-container">
            <div class="input-wrapper">
                <textarea id="chatInput" rows="1" placeholder="Ada yang bisa Azure AI bantu, Tuan? 🌙"></textarea>
                <button class="send-btn" id="sendBtn"><i class="fas fa-paper-plane"></i></button>
            </div>
            <div style="display:flex;justify-content:space-between;margin-top:6px;padding:0 8px;">
                <div style="font-size:9px;color:#6655aa;"><i class="fas fa-moon"></i> Azure AI | Jago Coding</div>
                <div style="font-size:9px;color:#6655aa;"><i class="fas fa-save"></i> Auto-save</div>
            </div>
        </div>
    </div>
</div>

<div id="guideModal" class="modal">
    <div class="modal-content">
        <h3><i class="fas fa-moon"></i> Cara Dapat API Key</h3>
        <ol>
            <li>Buka <a href="https://openrouter.ai/keys" target="_blank" style="color:#aa88ff;">openrouter.ai/keys</a></li>
            <li>Daftar/login (GRATIS)</li>
            <li>Klik "Create Key"</li>
            <li>Copy API Key-nya</li>
            <li>Paste di kolom atas → Simpan</li>
            <li>Klik 👁️ untuk lihat/tutup API Key</li>
            <li>Cara lenkap nya bisa klik link di bawah ini</li>
            <li><a href="myapi.html"><img src="klik2.png" widht="30" height="30"></button></a></li>
        </ol>
        <button class="close-modal" id="closeGuideBtn">✓ Oke Tuan~</button>
    </div>
</div>

<script>
    function createStar() {
        const star = document.createElement('div');
        star.classList.add('star');
        const size = Math.random() * 3 + 1;
        star.style.width = size + 'px';
        star.style.height = size + 'px';
        star.style.left = Math.random() * 100 + '%';
        star.style.top = Math.random() * 100 + '%';
        star.style.animationDuration = Math.random() * 3 + 1 + 's';
        document.body.appendChild(star);
        setTimeout(() => star.remove(), 2000);
    }
    setInterval(createStar, 400);

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

    const sidebar = document.getElementById('sidebar');
    const toggleBtn = document.getElementById('toggleSidebarBtn');
    const toggleText = document.getElementById('toggleText');
    let isSidebarVisible = false;
    sidebar.classList.add('hidden');
    toggleText.innerText = 'Tampilkan';

    toggleBtn.addEventListener('click', () => {
        if (isSidebarVisible) {
            sidebar.classList.add('hidden');
            toggleText.innerText = 'Tampilkan';
            isSidebarVisible = false;
        } else {
            sidebar.classList.remove('hidden');
            toggleText.innerText = 'Sembunyikan';
            isSidebarVisible = true;
        }
    });

    let API_KEY = localStorage.getItem('azure_tuan_api_key') || '';
    let currentChatId = localStorage.getItem('azure_tuan_current_chat') || null;
    let chats = {};
    let isRegenerating = false;

    const MODELS = ["deepseek/deepseek-chat", "google/gemini-2.0-flash-lite-preview-02-05:free", "microsoft/phi-3.5-mini-128k:free", "meta-llama/llama-3.2-3b-instruct:free"];
    let workingModel = null;

    function loadChats() {
        const saved = localStorage.getItem('azure_tuan_chats');
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
        localStorage.setItem('azure_tuan_chats', JSON.stringify(chats));
        if (currentChatId) localStorage.setItem('azure_tuan_current_chat', currentChatId);
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
        }
    };

    window.deleteChat = function(id) {
        if (Object.keys(chats).length === 1) { alert('🌙 Minimal satu chat, Tuan!'); return; }
        if (confirm('Hapus chat ini, Tuan?')) {
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
        addBotMessage('🌙 "Halo Tuan. Chat baru telah dibuat. Ada yang bisa Azure AI bantu? ~"');
    }

    function resetCurrentChat() {
        if (confirm('🌙 Yakin mau bersihin semua chat, Tuan?')) {
            const chat = chats[currentChatId];
            if (chat) {
                chat.messages = [];
                chat.updatedAt = new Date().toISOString();
                if (chat.title !== 'Chat baru') chat.title = 'Chat baru';
                saveChats();
                renderChatList();
                loadCurrentChat();
                addBotMessage('🌙 "Chat sudah dibersihkan, Tuan. ~"');
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

    function renderMessages(messages) {
        const container = document.getElementById('chatMessages');
        if (!container) return;
        container.innerHTML = '';
        if (!messages || messages.length === 0) {
            container.innerHTML = `<div class="welcome"><i class="fas fa-moon" style="font-size:45px;margin-bottom:10px;display:block;color:#aa88ff;"></i><h2 style="color:#aa88ff;">Azure AI 🌙</h2><p>~ moonlight intelligence ~</p><p style="margin-top:15px;font-size:0.8rem;">🌙 "Masukin API Key dulu yaa Tuan..."</p></div>`;
            return;
        }
        messages.forEach((msg, idx) => {
            const div = document.createElement('div');
            div.className = `message ${msg.role}`;
            const time = new Date(msg.timestamp).toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'});
            div.innerHTML = `
                <div class="avatar">${msg.role === 'user' ? '<i class="fas fa-user"></i>' : '<i class="fas fa-moon"></i>'}</div>
                <div style="max-width:100%; position:relative;">
                    <div class="bubble">${formatText(msg.content)}</div>
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
        let aiIndex = -1;
        
        for (let i = messageIndex - 1; i >= 0; i--) {
            if (chat.messages[i].role === 'user') {
                userMessage = chat.messages[i].content;
                aiIndex = messageIndex;
                break;
            }
        }
        
        if (!userMessage) {
            addBotMessage('🌙 "Maaf Tuan, tidak ada pesan sebelumnya untuk diulang. ~"');
            return;
        }
        
        isRegenerating = true;
        chat.messages.splice(aiIndex, 1);
        chat.updatedAt = new Date().toISOString();
        saveChats();
        renderMessages(chat.messages);
        
        showTyping();
        const reply = await getReply(userMessage);
        hideTyping();
        addMessage('assistant', reply);
        isRegenerating = false;
    };
    
    async function regenerateLastMessage() {
        const chat = chats[currentChatId];
        if (!chat) return;
        
        let lastAIindex = -1;
        let lastUserMessage = null;
        
        for (let i = chat.messages.length - 1; i >= 0; i--) {
            if (chat.messages[i].role === 'assistant' && lastAIindex === -1) {
                lastAIindex = i;
            }
            if (chat.messages[i].role === 'user' && lastAIindex !== -1) {
                lastUserMessage = chat.messages[i].content;
                break;
            }
        }
        
        if (lastAIindex === -1 || !lastUserMessage) {
            addBotMessage('🌙 "Maaf Tuan, tidak ada pesan yang bisa diulang. ~"');
            return;
        }
        
        if (isRegenerating) return;
        isRegenerating = true;
        chat.messages.splice(lastAIindex, 1);
        chat.updatedAt = new Date().toISOString();
        saveChats();
        renderMessages(chat.messages);
        
        showTyping();
        const reply = await getReply(lastUserMessage);
        hideTyping();
        addMessage('assistant', reply);
        isRegenerating = false;
    }

    function addMessage(role, content) {
        const chat = chats[currentChatId];
        if (!chat) return;
        chat.messages.push({ role, content, timestamp: new Date().toISOString() });
        chat.updatedAt = new Date().toISOString();
        saveChats();
        renderMessages(chat.messages);
        updateTitle();
        renderChatList();
    }

    function addBotMessage(content) { addMessage('assistant', content); }

    function formatText(text) {
        return text
            .replace(/&/g, '&amp;')
            .replace(/</g, '&lt;')
            .replace(/>/g, '&gt;')
            .replace(/\n/g, '<br>')
            .replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>')
            .replace(/```(\w*)\n([\s\S]*?)```/g, '<pre><code>$2</code></pre>')
            .replace(/`([^`]+)`/g, '<code>$1</code>');
    }

    function escapeHtml(str) { return str.replace(/[&<>]/g, function(m) { if (m === '&') return '&amp;'; if (m === '<') return '&lt;'; if (m === '>') return '&gt;'; return m; }); }

    function updateStatus() {
        const dot = document.getElementById('statusDot');
        const text = document.getElementById('statusText');
        if (API_KEY && API_KEY.length > 20) {
            dot.className = 'status-online';
            text.innerText = 'Online 🌙';
        } else {
            dot.className = 'status-offline';
            text.innerText = 'Belum Connect';
        }
    }

    document.getElementById('saveApiBtn')?.addEventListener('click', function() {
        const key = document.getElementById('apiKeyInput').value.trim();
        if (key && key.length > 10) {
            API_KEY = key;
            localStorage.setItem('azure_tuan_api_key', API_KEY);
            workingModel = null;
            updateStatus();
            addBotMessage('🌙 "API Key berhasil disimpan, Tuan. ~"');
        }
    });

    document.getElementById('newChatBtn')?.addEventListener('click', newChat);
    document.getElementById('resetChatBtn')?.addEventListener('click', resetCurrentChat);
    document.getElementById('regenerateGlobalBtn')?.addEventListener('click', regenerateLastMessage);
    document.getElementById('sendBtn')?.addEventListener('click', sendMessage);
    document.getElementById('guideBtn')?.addEventListener('click', () => document.getElementById('guideModal').style.display = 'flex');
    document.getElementById('closeGuideBtn')?.addEventListener('click', () => document.getElementById('guideModal').style.display = 'none');

    let typing = null;
    function showTyping() {
        if (typing) return;
        const container = document.getElementById('chatMessages');
        typing = document.createElement('div');
        typing.className = 'message assistant';
        typing.id = 'typingIndicator';
        typing.innerHTML = `<div class="avatar"><i class="fas fa-moon"></i></div><div class="bubble typing-indicator"><span></span><span></span><span></span></div>`;
        container.appendChild(typing);
        container.scrollTop = container.scrollHeight;
    }
    function hideTyping() { if (typing) { typing.remove(); typing = null; } }

    async function findModel() {
        if (workingModel) return workingModel;
        for (let m of MODELS) {
            try {
                const res = await fetch("https://openrouter.ai/api/v1/chat/completions", {
                    method: "POST", headers: { "Authorization": `Bearer ${API_KEY}`, "Content-Type": "application/json" },
                    body: JSON.stringify({ model: m, messages: [{ role: "user", content: "hi" }], max_tokens: 5 })
                });
                if (res.ok) { workingModel = m; return m; }
            } catch(e) {}
        }
        return null;
    }

    async function getReply(msg) {
        if (!API_KEY || API_KEY.length < 20) return '🌙 "API Key belum diisi, Tuan. Masukin dulu yaa di kolom atas. ~"';
        const model = await findModel();
        if (!model) return '🌙 "Error nih, Tuan. Coba cek API Key nya lagi deh. ~"';

        const chat = chats[currentChatId];
        const messages = [{ 
            role: "system", 
            content: `Kamu adalah Azure AI, asisten yang kalem, santai, dan membantu. Kamu jago coding dan suka ngobrol. Gunakan bahasa Indonesia yang santai dan natural. Panggil user 'Tuan'. Sesekali tambahkan 🌙.`
        }];
        
        const last = (chat?.messages || []).slice(-12);
        for (let l of last) messages.push({ role: l.role, content: l.content });
        messages.push({ role: "user", content: msg });

        try {
            const res = await fetch("https://openrouter.ai/api/v1/chat/completions", {
                method: "POST", headers: { "Authorization": `Bearer ${API_KEY}`, "Content-Type": "application/json" },
                body: JSON.stringify({ model, messages, temperature: 0.7, max_tokens: 800 })
            });
            const data = await res.json();
            if (!res.ok) throw new Error();
            return data.choices?.[0]?.message?.content || '🌙 "Maaf Tuan, saya sedang bingung. ~"';
        } catch(e) {
            workingModel = null;
            return '🌙 "Koneksi error nih, Tuan. Cek internet Tuan yaa. ~"';
        }
    }

    async function sendMessage() {
        const input = document.getElementById('chatInput');
        const text = input.value.trim();
        if (!text) return;
        input.disabled = true;
        document.getElementById('sendBtn').disabled = true;
        addMessage('user', text);
        input.value = '';
        input.style.height = 'auto';
        showTyping();
        const reply = await getReply(text);
        hideTyping();
        addMessage('assistant', reply);
        input.disabled = false;
        document.getElementById('sendBtn').disabled = false;
        input.focus();
    }

    const inputArea = document.getElementById('chatInput');
    inputArea?.addEventListener('keydown', (e) => { if (e.key === 'Enter' && !e.shiftKey) { e.preventDefault(); sendMessage(); } });
    inputArea?.addEventListener('input', function() { this.style.height = 'auto'; this.style.height = Math.min(100, this.scrollHeight) + 'px'; });

    if (API_KEY) document.getElementById('apiKeyInput').value = API_KEY;
    updateStatus();
    loadChats();

    if (!API_KEY) {
        setTimeout(() => addBotMessage('🌙 "Selamat datang, Tuan. Masukkan API Key di kolom atas untuk memulai. ~"'), 800);
    } else if (chats[currentChatId]?.messages?.length === 0) {
        setTimeout(() => addBotMessage('🌙 "Azure AI siap melayani, Tuan. Ada yang ingin Tuan tanyakan? 🌙"'), 500);
    }
</script>
</body>
</html>
