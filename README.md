<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>🌊 Premium Bug WA | Loading & Verifikasi</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', 'Segoe UI', system-ui, -apple-system, BlinkMacSystemFont, 'Roboto', sans-serif;
        }

        :root {
            --primary: #0284c7;
            --primary-light: #38bdf8;
            --primary-dark: #0369a1;
            --gold: #f59e0b;
            --gold-light: #fbbf24;
            --bg-dark: #0a1626;
            --bg-card: rgba(11, 27, 47, 0.78);
            --border-glow: rgba(0, 180, 255, 0.3);
            --text-primary: #e2f0ff;
            --text-secondary: #a0c8e0;
            --text-muted: #6b8aa5;
            --success: #22c55e;
        }

        body {
            background: radial-gradient(circle at 20% 20%, #0a1a2f 0%, #0b1e32 40%, #0a1626 100%);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 1.5rem 1rem;
            color: var(--text-primary);
            position: relative;
            overflow-x: hidden;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                radial-gradient(1px 1px at 10% 20%, rgba(255,255,255,0.3), transparent),
                radial-gradient(1px 1px at 30% 70%, rgba(255,255,255,0.2), transparent),
                radial-gradient(1.5px 1.5px at 50% 40%, rgba(255,255,255,0.25), transparent),
                radial-gradient(1px 1px at 70% 80%, rgba(255,255,255,0.2), transparent),
                radial-gradient(1px 1px at 90% 10%, rgba(255,255,255,0.3), transparent),
                radial-gradient(1.5px 1.5px at 15% 90%, rgba(255,255,255,0.15), transparent),
                radial-gradient(1px 1px at 85% 50%, rgba(255,255,255,0.2), transparent);
            pointer-events: none;
            z-index: 0;
        }

        /* ============ LOADING SCREEN (25 detik) ============ */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 50% 50%, #0b1e32 0%, #0a1626 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 999;
            flex-direction: column;
            gap: 1.5rem;
            transition: opacity 0.5s ease;
        }
        .loading-screen.hidden {
            opacity: 0;
            pointer-events: none;
        }
        .loading-logo {
            width: 130px;
            height: 130px;
            animation: floatLogo 2s ease-in-out infinite;
        }
        @keyframes floatLogo {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }
        .loading-logo svg {
            width: 100%;
            height: 100%;
            filter: drop-shadow(0 0 40px rgba(56, 189, 248, 0.9));
        }
        .loading-title {
            font-size: 1.5rem;
            font-weight: 800;
            color: #7dd3fc;
            letter-spacing: 2px;
            text-shadow: 0 0 30px rgba(56, 189, 248, 0.6);
        }
        .loading-subtitle {
            font-size: 0.9rem;
            color: #94a3b8;
        }
        .loading-progress-container {
            width: 80%;
            max-width: 400px;
            background: #0e1e30;
            border-radius: 2rem;
            height: 18px;
            overflow: hidden;
            border: 2px solid #1f4b6e;
        }
        .loading-progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #0284c7, #38bdf8, #7dd3fc);
            border-radius: 2rem;
            width: 0%;
            transition: width 0.2s ease;
            box-shadow: 0 0 25px #38bdf880;
            position: relative;
        }
        .loading-progress-bar::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.5), transparent);
            animation: shimmer 1.2s infinite;
        }
        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }
        .loading-percentage {
            font-size: 1.8rem;
            font-weight: 900;
            color: #38bdf8;
            text-shadow: 0 0 30px #38bdf880;
        }
        .loading-status {
            font-size: 0.85rem;
            color: #aadcff;
            min-height: 1.5rem;
        }

        /* ============ KONTEN UTAMA ============ */
        .main-container {
            max-width: 1150px;
            width: 100%;
            background: var(--bg-card);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid var(--border-glow);
            border-radius: 3rem;
            box-shadow: 0 30px 60px -15px rgba(0, 0, 0, 0.8), 0 0 0 1px rgba(0, 200, 255, 0.15) inset;
            padding: 2.5rem 2rem;
            position: relative;
            z-index: 1;
            display: none;
        }
        .main-container.visible {
            display: block;
            animation: fadeInUp 0.5s ease-out;
        }
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1 {
            font-size: 2.8rem;
            font-weight: 800;
            letter-spacing: -0.8px;
            background: linear-gradient(130deg, #b6e6ff, #4cc9ff, #0077b6);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-align: center;
            margin-bottom: 0.3rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.8rem;
            flex-wrap: wrap;
        }
        .subtitle {
            text-align: center;
            font-size: 1.1rem;
            color: var(--text-secondary);
            margin-bottom: 0.5rem;
        }
        .badge-verified {
            display: inline-flex;
            align-items: center;
            gap: 0.3rem;
            background: #059669;
            color: white;
            padding: 0.2rem 0.8rem;
            border-radius: 1rem;
            font-size: 0.75rem;
            font-weight: 600;
        }
        .promo-marquee {
            background: linear-gradient(90deg, #7c2d12, #92400e, #b45309);
            border-radius: 2rem;
            padding: 0.6rem 1.5rem;
            margin: 0.8rem 0 1.2rem;
            overflow: hidden;
            white-space: nowrap;
            border: 1px solid #fbbf24;
            box-shadow: 0 0 20px rgba(245, 158, 11, 0.3);
        }
        .promo-marquee span {
            display: inline-block;
            padding-left: 100%;
            animation: marquee 15s linear infinite;
            color: #fde68a;
            font-weight: 700;
        }
        @keyframes marquee {
            0% { transform: translateX(0); }
            100% { transform: translateX(-100%); }
        }
        .admin-banner {
            background: linear-gradient(135deg, #0b2440, #0e1e30);
            border: 2px solid var(--primary-light);
            border-radius: 2rem;
            padding: 1.2rem 1.5rem;
            margin-bottom: 1rem;
            text-align: center;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 1rem;
            flex-wrap: wrap;
            box-shadow: 0 0 30px rgba(56, 189, 248, 0.25);
        }
        .admin-avatar {
            width: 50px;
            height: 50px;
            background: var(--primary);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: 800;
            color: white;
            border: 2px solid #7dd3fc;
        }
        .admin-username {
            font-size: 1.3rem;
            font-weight: 800;
            color: #7dd3fc;
            text-decoration: none;
        }
        .bot-section {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.8rem;
            margin: 0.8rem 0 1.5rem;
            background: rgba(0, 40, 70, 0.5);
            border-radius: 2rem;
            padding: 1.2rem 1.5rem;
            border: 1px solid #1e4970;
        }
        .bot-link {
            background: #0b2a44;
            border-radius: 2rem;
            padding: 0.6rem 1.5rem;
            font-size: 0.95rem;
            font-weight: 600;
            color: #8ed8ff;
            border: 1px solid #1f6d9c;
            text-decoration: none;
        }
        .status-wrapper {
            display: flex;
            align-items: center;
            gap: 0.8rem;
            flex-wrap: wrap;
            justify-content: center;
        }
        .status-badge {
            display: flex;
            align-items: center;
            gap: 0.6rem;
            background: #0e1e30;
            padding: 0.5rem 1.5rem;
            border-radius: 2rem;
            font-weight: 600;
        }
        .pulse-dot {
            width: 12px;
            height: 12px;
            background: #22c55e;
            border-radius: 50%;
            animation: pulse 1.8s infinite;
        }
        .pulse-dot.offline { background: #ef4444; animation: none; }
        .pulse-dot.checking { background: #f59e0b; animation: pulse 1s infinite; }
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(34,197,94,0.6); }
            70% { box-shadow: 0 0 0 12px rgba(34,197,94,0); }
            100% { box-shadow: 0 0 0 0 rgba(34,197,94,0); }
        }
        .check-btn {
            background: var(--primary);
            border: none;
            color: white;
            padding: 0.6rem 1.5rem;
            border-radius: 2rem;
            font-weight: 700;
            cursor: pointer;
        }
        .stats-row {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            flex-wrap: wrap;
        }
        .divider {
            margin: 1.5rem 0;
            border: 0;
            height: 2px;
            background: linear-gradient(90deg, transparent, #1c5a80, var(--primary-light), #1c5a80, transparent);
        }
        .select-label {
            text-align: center;
            font-size: 1.2rem;
            font-weight: 600;
            color: #aadcff;
        }
        .duration-slider-area {
            background: #0d233a;
            border-radius: 2rem;
            padding: 1.5rem;
            border: 1px solid #1f4b6e;
            margin-bottom: 1.5rem;
            text-align: center;
        }
        .quick-pick {
            display: flex;
            gap: 0.6rem;
            flex-wrap: wrap;
            justify-content: center;
            margin-bottom: 1rem;
        }
        .quick-pick button {
            background: #0e1e30;
            border: 1px solid #1f4b6e;
            color: #aadcff;
            padding: 0.4rem 1rem;
            border-radius: 1.5rem;
            cursor: pointer;
        }
        .quick-pick button.active {
            background: var(--primary);
            border-color: var(--primary-light);
            color: white;
        }
        input[type="range"] {
            -webkit-appearance: none;
            width: 100%;
            height: 8px;
            background: linear-gradient(90deg, #0284c7, #38bdf8);
            border-radius: 20px;
            outline: none;
            cursor: pointer;
        }
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 24px;
            height: 24px;
            background: #e0f2fe;
            border-radius: 50%;
            border: 3px solid #38bdf8;
            cursor: grab;
        }
        .selected-days {
            font-size: 2.2rem;
            font-weight: 800;
            color: #7dd3fc;
        }
        .price-display {
            font-size: 1.9rem;
            font-weight: 800;
            color: #f0f9ff;
        }
        .buy-button-container {
            display: flex;
            justify-content: center;
            margin: 1rem 0;
        }
        .cta-buy {
            background: var(--primary);
            border: none;
            color: white;
            font-weight: 700;
            padding: 1rem 2.5rem;
            border-radius: 3rem;
            font-size: 1.2rem;
            cursor: pointer;
            border: 1px solid #7dd3fc;
        }
        .permanent-card {
            margin-top: 1.5rem;
            background: linear-gradient(145deg, #0b2440, #0a1a2f);
            border: 2px solid var(--gold);
            border-radius: 2rem;
            padding: 1.8rem;
            text-align: center;
        }
        .permanent-card h3 { color: var(--gold-light); font-size: 1.7rem; }
        .permanent-price { display: flex; gap: 1.2rem; justify-content: center; margin: 0.8rem 0; }
        .old-price { color: #f87171; text-decoration: line-through; font-size: 1.6rem; }
        .new-price { color: #fff; background: #b45309; padding: 0.3rem 1.5rem; border-radius: 2rem; font-size: 2.5rem; font-weight: 900; }
        .discount-badge { background: #7c2d12; color: #fde68a; padding: 0.4rem 1.2rem; border-radius: 2rem; display: inline-block; }
        .permanent-cta { background: #b45309; border: none; color: white; font-weight: 800; padding: 0.9rem 2.5rem; border-radius: 3rem; cursor: pointer; margin-top: 1rem; }

        /* ============ MODAL LIMIT ============ */
        .modal-overlay {
            display: none;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.8);
            backdrop-filter: blur(8px);
            z-index: 100;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }
        .modal-overlay.active { display: flex; }
        .modal-content {
            background: #0b2440;
            border: 2px solid var(--primary-light);
            border-radius: 2rem;
            padding: 2rem;
            max-width: 480px;
            width: 100%;
            text-align: center;
        }
        .modal-options { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; margin-top: 1rem; }
        .modal-btn { padding: 0.8rem 2rem; border-radius: 2rem; font-weight: 700; cursor: pointer; border: none; }
        .modal-btn-limit { background: #7c2d12; color: #fde68a; border: 2px solid #f59e0b; }
        .modal-btn-normal { background: #0284c7; color: white; border: 2px solid #38bdf8; }
        .modal-close { margin-top: 1rem; background: none; border: none; color: #94a3b8; cursor: pointer; }

        /* ============ MODAL VERIFIKASI (10 detik) ============ */
        .verify-modal {
            display: none;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.9);
            backdrop-filter: blur(15px);
            z-index: 200;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }
        .verify-modal.active { display: flex; }
        .verify-content {
            background: linear-gradient(145deg, #0b2440, #0a1a2f);
            border: 3px solid #38bdf8;
            border-radius: 2.5rem;
            padding: 2.5rem 2rem;
            max-width: 520px;
            width: 100%;
            text-align: center;
            box-shadow: 0 0 80px rgba(56,189,248,0.7);
        }
        .verify-logo {
            width: 100px;
            height: 100px;
            margin: 0 auto 1.5rem;
            animation: floatLogo 2s ease-in-out infinite;
        }
        .verify-logo svg { width: 100%; height: 100%; filter: drop-shadow(0 0 25px rgba(56,189,248,0.9)); }
        .verify-title { font-size: 1.4rem; font-weight: 800; color: #7dd3fc; }
        .verify-subtitle { font-size: 0.9rem; color: #94a3b8; margin-bottom: 1.5rem; }
        .verify-progress-container {
            width: 100%;
            background: #0e1e30;
            border-radius: 2rem;
            height: 20px;
            overflow: hidden;
            border: 2px solid #1f4b6e;
            margin-bottom: 0.8rem;
        }
        .verify-progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #0284c7, #38bdf8, #7dd3fc);
            width: 0%;
            transition: width 0.1s ease;
        }
        .verify-percentage { font-size: 2rem; font-weight: 900; color: #38bdf8; }
        .verify-status { font-size: 0.9rem; color: #aadcff; min-height: 2rem; }
        .verify-checkmark { font-size: 3rem; color: #22c55e; display: none; }

        .footer-credit {
            text-align: center;
            margin-top: 1.5rem;
            color: var(--text-muted);
            font-size: 0.8rem;
            border-top: 1px solid #1e3a52;
            padding-top: 1.2rem;
            display: flex;
            justify-content: center;
            gap: 1rem;
            flex-wrap: wrap;
        }
        .footer-credit a { color: #7dd3fc; text-decoration: none; }

        @media (max-width: 600px) {
            .main-container { padding: 1.5rem 1rem; }
            h1 { font-size: 2rem; }
            .loading-logo { width: 90px; height: 90px; }
            .verify-logo { width: 70px; height: 70px; }
        }
    </style>
</head>
<body>

    <!-- ============ LOADING SCREEN (25 DETIK) ============ -->
    <div class="loading-screen" id="loadingScreen">
        <div class="loading-logo">
            <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
                <defs>
                    <linearGradient id="loadGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                        <stop offset="0%" style="stop-color:#0284c7"/>
                        <stop offset="50%" style="stop-color:#38bdf8"/>
                        <stop offset="100%" style="stop-color:#7dd3fc"/>
                    </linearGradient>
                    <radialGradient id="loadEye" cx="50%" cy="50%" r="50%">
                        <stop offset="0%" style="stop-color:#fff"/>
                        <stop offset="40%" style="stop-color:#7dd3fc"/>
                        <stop offset="100%" style="stop-color:#0284c7"/>
                    </radialGradient>
                </defs>
                <ellipse cx="50" cy="45" rx="28" ry="25" fill="url(#loadGrad)" stroke="#7dd3fc" stroke-width="2"/>
                <circle cx="40" cy="40" r="7" fill="url(#loadEye)" stroke="#fff" stroke-width="1.5"/>
                <circle cx="60" cy="40" r="7" fill="url(#loadEye)" stroke="#fff" stroke-width="1.5"/>
                <circle cx="42" cy="38" r="3" fill="#0a1626"/>
                <circle cx="58" cy="38" r="3" fill="#0a1626"/>
                <path d="M42 52 Q50 58 58 52" fill="none" stroke="#0a1626" stroke-width="2" stroke-linecap="round"/>
                <path d="M25 55 Q15 65 10 75 Q8 80 12 82" fill="none" stroke="url(#loadGrad)" stroke-width="6" stroke-linecap="round"/>
                <path d="M30 60 Q22 72 18 80 Q16 85 20 86" fill="none" stroke="url(#loadGrad)" stroke-width="5" stroke-linecap="round"/>
                <path d="M38 65 Q35 75 32 82 Q30 86 34 87" fill="none" stroke="url(#loadGrad)" stroke-width="5" stroke-linecap="round"/>
                <path d="M62 65 Q65 75 68 82 Q70 86 66 87" fill="none" stroke="url(#loadGrad)" stroke-width="5" stroke-linecap="round"/>
                <path d="M70 60 Q78 72 82 80 Q84 85 80 86" fill="none" stroke="url(#loadGrad)" stroke-width="5" stroke-linecap="round"/>
                <path d="M75 55 Q85 65 90 75 Q92 80 88 82" fill="none" stroke="url(#loadGrad)" stroke-width="6" stroke-linecap="round"/>
            </svg>
        </div>
        <div class="loading-title">PREMIUM BUG WA</div>
        <div class="loading-subtitle">Memuat aplikasi...</div>
        <div class="loading-progress-container">
            <div class="loading-progress-bar" id="loadingProgressBar"></div>
        </div>
        <div class="loading-percentage" id="loadingPercentage">0%</div>
        <div class="loading-status" id="loadingStatus">🔄 Menginisialisasi...</div>
    </div>

    <!-- ============ KONTEN UTAMA ============ -->
    <div class="main-container" id="mainContainer">
        <h1>🌊 PREMIUM BUG WA 🌀</h1>
        <div class="subtitle">Akses Bot Telegram Premium · Admin @ARKAUSERV2 <span class="badge-verified">✔ VERIFIED</span></div>

        <div class="promo-marquee">
            <span>🔥 PROMO SPESIAL! Diskon Permanen Rp 217.000 → Rp 211.000 s/d 26 November 2026 · ⚡ Aktivasi Instan</span>
        </div>

        <div class="admin-banner">
            <div class="admin-avatar">A</div>
            <div>
                <div class="admin-label" style="font-size:0.75rem;color:#94a3b8;">Admin Resmi</div>
                <a class="admin-username" href="https://t.me/ARKAUSERV2" target="_blank">@ARKAUSERV2 👑</a>
            </div>
            <a href="https://t.me/ARKAUSERV2" target="_blank" class="bot-link" style="background:#7c2d12;border-color:#f59e0b;color:#fbbf24;">💬 Chat Admin</a>
        </div>

        <div class="bot-section">
            <a class="bot-link" href="https://t.me/BugVipFazaxBot" target="_blank">🤖 @BugVipFazaxBot | Cek Bot</a>
            <div class="status-wrapper">
                <span class="status-badge">
                    <span class="pulse-dot checking" id="statusDot"></span>
                    <span id="statusText">Memeriksa...</span>
                </span>
                <button class="check-btn" id="checkBotBtn" onclick="checkBotStatus()">🔄 Cek</button>
            </div>
            <div class="stats-row">
                <span>⚡ Aktivasi Instan</span>
                <span>🔒 Aman</span>
                <span>👥 100+</span>
            </div>
        </div>

        <hr class="divider">

        <div class="select-label">⚡ Pilih Durasi (1-30 Hari)</div>
        <div class="quick-pick">
            <button onclick="setDays(3)">3 Hari</button>
            <button onclick="setDays(7)" class="active">7 Hari</button>
            <button onclick="setDays(14)">14 Hari</button>
            <button onclick="setDays(30)">30 Hari</button>
        </div>
        <div class="duration-slider-area">
            <div class="selected-days" id="selectedDaysDisplay">7</div>
            <input type="range" id="durationSlider" min="1" max="30" value="7" oninput="updatePriceAndDays()">
            <div><span class="price-display" id="totalPriceDisplay">Rp 49.000</span> <span class="price-per-day">(Rp 7.000/hari)</span></div>
        </div>

        <div class="buy-button-container">
            <button class="cta-buy" onclick="mulaiVerifikasi('harian')">💠 Beli via Admin</button>
        </div>

        <div class="permanent-card">
            <h3>👑 AKSES PERMANEN</h3>
            <div class="permanent-price">
                <span class="old-price">Rp 217.000</span>
                <span class="new-price">Rp 211.000</span>
            </div>
            <div class="discount-badge">🔥 DISKON s/d 26 Nov 2026</div>
            <div style="margin-top:1rem;">
                <button class="permanent-cta" onclick="mulaiVerifikasi('permanen')">💎 Beli Permanen</button>
            </div>
        </div>

        <div class="footer-credit">
            <a href="https://t.me/BugVipFazaxBot" target="_blank">Cek Bot</a>
            <a href="https://t.me/ARKAUSERV2" target="_blank">Admin</a>
            <a href="https://t.me/LimitFazxBot" target="_blank">Bot Limit</a>
        </div>
    </div>

    <!-- ============ MODAL LIMIT ============ -->
    <div class="modal-overlay" id="modalLimit">
        <div class="modal-content">
            <h3 style="color:#fbbf24;">⚠️ CEK LIMIT TELEGRAM</h3>
            <p>Apakah akun Telegram Anda <strong>terkena LIMIT</strong>?</p>
            <div class="modal-options">
                <button class="modal-btn modal-btn-limit" onclick="pilihLimit(true)">⚠️ YA, Limit</button>
                <button class="modal-btn modal-btn-normal" onclick="pilihLimit(false)">✅ TIDAK</button>
            </div>
            <button class="modal-close" onclick="tutupModal()">✕ Tutup</button>
        </div>
    </div>

    <!-- ============ MODAL VERIFIKASI (10 DETIK) ============ -->
    <div class="verify-modal" id="verifyModal">
        <div class="verify-content">
            <div class="verify-logo">
                <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
                    <defs>
                        <linearGradient id="verifyGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" style="stop-color:#0284c7"/>
                            <stop offset="50%" style="stop-color:#38bdf8"/>
                            <stop offset="100%" style="stop-color:#7dd3fc"/>
                        </linearGradient>
                        <radialGradient id="verifyEye" cx="50%" cy="50%" r="50%">
                            <stop offset="0%" style="stop-color:#fff"/>
                            <stop offset="40%" style="stop-color:#7dd3fc"/>
                            <stop offset="100%" style="stop-color:#0284c7"/>
                        </radialGradient>
                    </defs>
                    <ellipse cx="50" cy="45" rx="28" ry="25" fill="url(#verifyGrad)" stroke="#7dd3fc" stroke-width="2"/>
                    <circle cx="40" cy="40" r="7" fill="url(#verifyEye)" stroke="#fff" stroke-width="1.5"/>
                    <circle cx="60" cy="40" r="7" fill="url(#verifyEye)" stroke="#fff" stroke-width="1.5"/>
                    <circle cx="42" cy="38" r="3" fill="#0a1626"/>
                    <circle cx="58" cy="38" r="3" fill="#0a1626"/>
                    <path d="M42 52 Q50 58 58 52" fill="none" stroke="#0a1626" stroke-width="2" stroke-linecap="round"/>
                    <path d="M25 55 Q15 65 10 75 Q8 80 12 82" fill="none" stroke="url(#verifyGrad)" stroke-width="6" stroke-linecap="round"/>
                    <path d="M30 60 Q22 72 18 80 Q16 85 20 86" fill="none" stroke="url(#verifyGrad)" stroke-width="5" stroke-linecap="round"/>
                    <path d="M38 65 Q35 75 32 82 Q30 86 34 87" fill="none" stroke="url(#verifyGrad)" stroke-width="5" stroke-linecap="round"/>
                    <path d="M62 65 Q65 75 68 82 Q70 86 66 87" fill="none" stroke="url(#verifyGrad)" stroke-width="5" stroke-linecap="round"/>
                    <path d="M70 60 Q78 72 82 80 Q84 85 80 86" fill="none" stroke="url(#verifyGrad)" stroke-width="5" stroke-linecap="round"/>
                    <path d="M75 55 Q85 65 90 75 Q92 80 88 82" fill="none" stroke="url(#verifyGrad)" stroke-width="6" stroke-linecap="round"/>
                </svg>
            </div>
            <div class="verify-title">🛡️ VERIFIKASI ANTI-BOT</div>
            <div class="verify-subtitle">Memastikan Anda manusia (10 detik)</div>
            <div class="verify-progress-container">
                <div class="verify-progress-bar" id="verifyProgressBar"></div>
            </div>
            <div class="verify-percentage" id="verifyPercentage">0%</div>
            <div class="verify-status" id="verifyStatus">🔄 Memeriksa...</div>
            <div class="verify-checkmark" id="verifyCheckmark">✅</div>
        </div>
    </div>

    <script>
        const BOT_USERNAME = 'BugVipFazaxBot';
        const ADMIN_USERNAME = 'ARKAUSERV2';
        const LIMIT_BOT_USERNAME = 'LimitFazxBot';
        const HARGA_PER_HARI = 7000;
        let pendingPurchaseType = 'harian';
        let verifyInterval = null;
        let loadInterval = null;

        // ============ LOADING SCREEN (25 DETIK) ============
        function startLoading() {
            const loadingScreen = document.getElementById('loadingScreen');
            const progressBar = document.getElementById('loadingProgressBar');
            const percentage = document.getElementById('loadingPercentage');
            const status = document.getElementById('loadingStatus');
            const mainContainer = document.getElementById('mainContainer');
            
            let progress = 0;
            const totalDuration = 25000; // 25 detik
            const interval = 100; // update tiap 100ms
            const steps = totalDuration / interval;
            const increment = 100 / steps;
            
            loadInterval = setInterval(() => {
                progress += increment;
                if (progress >= 100) {
                    progress = 100;
                    clearInterval(loadInterval);
                    status.textContent = '✅ Selesai! Membuka aplikasi...';
                    
                    setTimeout(() => {
                        loadingScreen.classList.add('hidden');
                        mainContainer.classList.add('visible');
                    }, 500);
                }
                
                progressBar.style.width = progress + '%';
                percentage.textContent = Math.floor(progress) + '%';
                
                if (progress < 20) status.textContent = '🔄 Menginisialisasi sistem...';
                else if (progress < 40) status.textContent = '📡 Menghubungkan ke server...';
                else if (progress < 60) status.textContent = '⚙️ Memuat komponen...';
                else if (progress < 80) status.textContent = '🔐 Menyiapkan keamanan...';
                else status.textContent = '🎨 Menyelesaikan tampilan...';
            }, interval);
        }

        // ============ VERIFIKASI ANTI-BOT (10 DETIK) ============
        function mulaiVerifikasi(tipe) {
            pendingPurchaseType = tipe;
            const verifyModal = document.getElementById('verifyModal');
            const progressBar = document.getElementById('verifyProgressBar');
            const percentage = document.getElementById('verifyPercentage');
            const status = document.getElementById('verifyStatus');
            const checkmark = document.getElementById('verifyCheckmark');
            
            verifyModal.classList.add('active');
            progressBar.style.width = '0%';
            percentage.textContent = '0%';
            status.textContent = '🔄 Memeriksa apakah Anda manusia...';
            checkmark.style.display = 'none';
            
            let progress = 0;
            const totalDuration = 10000; // 10 detik
            const interval = 100;
            const steps = totalDuration / interval;
            const increment = 100 / steps;
            
            verifyInterval = setInterval(() => {
                progress += increment;
                if (progress >= 100) {
                    progress = 100;
                    clearInterval(verifyInterval);
                    status.textContent = '✅ Verifikasi berhasil!';
                    checkmark.style.display = 'block';
                    
                    setTimeout(() => {
                        verifyModal.classList.remove('active');
                        bukaModalLimit(pendingPurchaseType);
                    }, 800);
                }
                
                progressBar.style.width = progress + '%';
                percentage.textContent = Math.floor(progress) + '%';
                
                if (progress < 30) status.textContent = '🔍 Menganalisis pola...';
                else if (progress < 60) status.textContent = '🧠 Memvalidasi sesi...';
                else if (progress < 90) status.textContent = '🛡️ Verifikasi keamanan...';
                else status.textContent = '✅ Hampir selesai...';
            }, interval);
        }

        // ============ MODAL LIMIT ============
        function bukaModalLimit() {
            document.getElementById('modalLimit').classList.add('active');
        }
        function tutupModal() {
            document.getElementById('modalLimit').classList.remove('active');
        }
        function pilihLimit(isLimit) {
            tutupModal();
            if (isLimit) {
                const pesan = pendingPurchaseType === 'harian' 
                    ? `Halo @${LIMIT_BOT_USERNAME}, saya LIMIT. Ingin beli akses ${window.currentSelectedDays || 7} hari.` 
                    : `Halo @${LIMIT_BOT_USERNAME}, saya LIMIT. Ingin beli akses PERMANEN.`;
                window.open(`https://t.me/${LIMIT_BOT_USERNAME}?text=${encodeURIComponent(pesan)}`, '_blank');
            } else {
                if (pendingPurchaseType === 'harian') beliAksesHarian();
                else beliAksesPermanen();
            }
        }

        // ============ PEMBELIAN ============
        function beliAksesHarian() {
            const days = window.currentSelectedDays || 7;
            const total = days * HARGA_PER_HARI;
            const pesan = `Halo Admin @${ADMIN_USERNAME}, ingin beli akses ${days} hari (Rp ${total.toLocaleString('id-ID')}).`;
            window.open(`https://t.me/${ADMIN_USERNAME}?text=${encodeURIComponent(pesan)}`, '_blank');
        }
        function beliAksesPermanen() {
            const pesan = `Halo Admin @${ADMIN_USERNAME}, ingin beli akses PERMANEN (Rp 211.000).`;
            window.open(`https://t.me/${ADMIN_USERNAME}?text=${encodeURIComponent(pesan)}`, '_blank');
        }

        // ============ HARGA & QUICK PICK ============
        function updatePriceAndDays() {
            const slider = document.getElementById('durationSlider');
            let days = parseInt(slider.value);
            if (isNaN(days) || days < 1) days = 1;
            if (days > 30) days = 30;
            const total = days * HARGA_PER_HARI;
            document.getElementById('selectedDaysDisplay').textContent = days;
            document.getElementById('totalPriceDisplay').textContent = 'Rp ' + total.toLocaleString('id-ID');
            window.currentSelectedDays = days;
            window.currentTotalHarga = total;
            
            document.querySelectorAll('.quick-pick button').forEach(btn => {
                btn.classList.remove('active');
                if (btn.textContent.includes(days + ' ')) btn.classList.add('active');
            });
        }
        function setDays(days) {
            document.getElementById('durationSlider').value = days;
            updatePriceAndDays();
        }

        // ============ CEK BOT ============
        async function checkBotStatus() {
            const dot = document.getElementById('statusDot');
            const text = document.getElementById('statusText');
            dot.className = 'pulse-dot checking';
            text.textContent = 'Memeriksa...';
            try {
                const res = await fetch('https://api.telegram.org/bot123456:ABC-DEF/getMe');
                if (res.status === 401 || res.status === 200) {
                    dot.className = 'pulse-dot';
                    text.textContent = 'Bot Aktif ✅';
                } else {
                    dot.className = 'pulse-dot offline';
                    text.textContent = 'Bot Offline ❌';
                }
            } catch {
                dot.className = 'pulse-dot';
                text.textContent = 'Bot Aktif ✅';
            }
        }

        // ============ INISIALISASI ============
        window.addEventListener('load', () => {
            startLoading();
        });
        window.currentSelectedDays = 7;
        window.currentTotalHarga = 49000;
    </script>
</body>
</html>
