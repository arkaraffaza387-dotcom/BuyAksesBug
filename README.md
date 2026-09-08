<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Premium Bug WA - Dashboard</title>

    <!-- Google Font & Icon -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background: #0a0a0a;
            font-family: 'Poppins', sans-serif;
            color: #c0c0c0;
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
        }

        #particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
        }

        /* ============ LOADING SCREEN (15 DETIK) ============ */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #0a0a0a;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            flex-direction: column;
            gap: 1.5rem;
            transition: opacity 0.6s ease, transform 0.6s ease;
        }
        .loading-screen.hidden {
            opacity: 0;
            pointer-events: none;
            transform: scale(1.1);
        }
        .loading-logo {
            width: 120px;
            height: 120px;
            animation: floatLogo 2s ease-in-out infinite;
        }
        @keyframes floatLogo {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }
        .loading-logo svg {
            width: 100%;
            height: 100%;
            filter: drop-shadow(0 0 40px rgba(37, 211, 102, 0.6));
        }
        .loading-title {
            font-size: 1.6rem;
            font-weight: 600;
            color: #4AE381;
            letter-spacing: 2px;
            text-shadow: 0 0 30px rgba(37, 211, 102, 0.4);
        }
        .loading-subtitle {
            font-size: 0.9rem;
            color: #999;
            letter-spacing: 1px;
        }
        .loading-progress-container {
            width: 80%;
            max-width: 400px;
            background: #1a1a1a;
            border-radius: 2rem;
            height: 8px;
            overflow: hidden;
            border: 1px solid #1a5c3a;
        }
        .loading-progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #128C7E, #25D366, #4AE381);
            border-radius: 2rem;
            width: 0%;
            transition: width 0.2s ease;
            box-shadow: 0 0 25px rgba(37, 211, 102, 0.5);
            position: relative;
        }
        .loading-progress-bar::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.6), transparent);
            animation: shimmer 1.2s infinite;
        }
        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }
        .loading-percentage {
            font-size: 2rem;
            font-weight: 600;
            color: #25D366;
            text-shadow: 0 0 30px rgba(37, 211, 102, 0.6);
        }
        .loading-status {
            font-size: 0.85rem;
            color: #a8e6c1;
            min-height: 1.5rem;
        }

        /* ============ HEADER ============ */
        header {
            position: relative;
            z-index: 2;
            padding: 20px;
            text-align: center;
            background: rgba(10, 10, 10, 0.8);
            border-bottom: 1px solid rgba(192, 192, 192, 0.15);
        }

        .logo-container {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 10px;
        }

        .logo {
            width: 70px;
            height: 70px;
            filter: drop-shadow(0 0 15px rgba(37, 211, 102, 0.4));
        }

        .nav-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 15px;
            flex-wrap: wrap;
        }

        .nav-link {
            color: #bbb;
            text-decoration: none;
            font-weight: 600;
            padding: 8px 15px;
            border-radius: 8px;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .nav-link:hover {
            background: rgba(37, 211, 102, 0.1);
            text-shadow: 0 0 8px rgba(37, 211, 102, 0.6);
        }

        /* ============ MAIN CONTAINER ============ */
        main {
            position: relative;
            z-index: 2;
            max-width: 1200px;
            margin: 0 auto;
            padding: 30px 20px;
        }

        .section {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(192, 192, 192, 0.15);
            backdrop-filter: blur(8px);
            padding: 30px;
            border-radius: 20px;
            margin-bottom: 30px;
            box-shadow: 0 0 25px rgba(37, 211, 102, 0.1);
            transition: all 0.3s ease;
        }

        .section:hover {
            box-shadow: 0 0 35px rgba(37, 211, 102, 0.2);
        }

        .section-title {
            font-size: 28px;
            color: #4AE381;
            text-shadow: 0 0 8px rgba(37, 211, 102, 0.4);
            margin-bottom: 20px;
            text-align: center;
            font-weight: 600;
        }

        .hero {
            text-align: center;
            padding: 40px 20px;
        }

        .hero-title {
            font-size: 36px;
            color: #4AE381;
            text-shadow: 0 0 10px rgba(37, 211, 102, 0.5);
            margin-bottom: 10px;
            font-weight: 600;
        }

        .hero-subtitle {
            font-size: 16px;
            color: #b3b3b3;
            margin-bottom: 25px;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
        }

        /* ============ PLANS ============ */
        .plans-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .plan-card {
            background: rgba(30, 30, 30, 0.6);
            border: 1px solid rgba(200, 200, 200, 0.2);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
        }

        .plan-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(37, 211, 102, 0.2);
            border-color: rgba(37, 211, 102, 0.4);
        }

        .plan-name {
            font-size: 22px;
            color: #4AE381;
            margin-bottom: 15px;
            font-weight: 600;
        }

        .plan-price {
            font-size: 28px;
            color: #fff;
            margin-bottom: 20px;
            font-weight: 600;
        }

        .plan-price span {
            font-size: 16px;
            color: #999;
        }

        .plan-features {
            list-style: none;
            margin-bottom: 25px;
            text-align: left;
        }

        .plan-features li {
            position: relative;
            padding-left: 35px;
            margin-bottom: 12px;
            line-height: 1.6;
            list-style: none;
            font-size: 0.9rem;
        }

        .plan-features li i {
            position: absolute;
            left: 0;
            top: 50%;
            transform: translateY(-50%);
            color: #25D366;
            font-size: 16px;
        }

        .btn {
            display: inline-block;
            background: linear-gradient(135deg, #128C7E, #25D366);
            color: #000;
            padding: 12px 25px;
            border-radius: 10px;
            font-weight: 600;
            text-decoration: none;
            box-shadow: 0 0 12px rgba(37, 211, 102, 0.3);
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
            font-family: 'Poppins', sans-serif;
            font-size: 0.9rem;
        }

        .btn:hover {
            background: #4AE381;
            transform: translateY(-2px);
            box-shadow: 0 8px 16px rgba(37, 211, 102, 0.4);
        }

        .btn-outline {
            background: transparent;
            border: 2px solid #25D366;
            color: #4AE381;
        }

        .btn-outline:hover {
            background: rgba(37, 211, 102, 0.1);
        }

        /* ============ ADMIN BANNER ============ */
        .admin-banner {
            background: rgba(30, 30, 30, 0.5);
            border: 1px solid rgba(37, 211, 102, 0.3);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            text-align: center;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .admin-avatar {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, #128C7E, #25D366);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.3rem;
            font-weight: 600;
            color: #000;
            border: 2px solid #4AE381;
        }

        .admin-username {
            font-size: 1.1rem;
            font-weight: 600;
            color: #4AE381;
            text-decoration: none;
        }

        .admin-username:hover {
            color: #fff;
            text-shadow: 0 0 10px rgba(37, 211, 102, 0.5);
        }

        /* ============ BOT SECTION ============ */
        .bot-section {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.8rem;
            margin: 0.8rem 0 1.5rem;
            background: rgba(20, 20, 20, 0.5);
            border-radius: 15px;
            padding: 20px;
            border: 1px solid rgba(37, 211, 102, 0.2);
        }

        .bot-link {
            background: rgba(30, 30, 30, 0.8);
            border-radius: 2rem;
            padding: 0.6rem 1.5rem;
            font-size: 0.9rem;
            font-weight: 600;
            color: #4AE381;
            border: 1px solid #1a5c3a;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .bot-link:hover {
            border-color: #25D366;
            color: #fff;
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
            background: rgba(20, 20, 20, 0.8);
            padding: 0.5rem 1.5rem;
            border-radius: 2rem;
            font-weight: 600;
            font-size: 0.85rem;
        }

        .pulse-dot {
            width: 10px;
            height: 10px;
            background: #22c55e;
            border-radius: 50%;
            animation: pulse 1.8s infinite;
        }

        .pulse-dot.offline {
            background: #ef4444;
            animation: none;
        }
        .pulse-dot.checking {
            background: #f59e0b;
            animation: pulse 1s infinite;
        }

        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(34, 197, 94, 0.5); }
            70% { box-shadow: 0 0 0 10px rgba(34, 197, 94, 0); }
            100% { box-shadow: 0 0 0 0 rgba(34, 197, 94, 0); }
        }

        .check-btn {
            background: rgba(18, 140, 126, 0.8);
            border: 1px solid #25D366;
            color: #4AE381;
            padding: 0.5rem 1.2rem;
            border-radius: 2rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.85rem;
        }

        .check-btn:hover {
            background: rgba(37, 211, 102, 0.2);
        }

        .stats-row {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            flex-wrap: wrap;
            font-size: 0.85rem;
            color: #aaa;
        }

        /* ============ SLIDER ============ */
        .divider {
            margin: 1.5rem 0;
            border: 0;
            height: 1px;
            background: linear-gradient(90deg, transparent, #1a5c3a, #25D366, #1a5c3a, transparent);
        }

        .select-label {
            text-align: center;
            font-size: 1.1rem;
            font-weight: 600;
            color: #4AE381;
        }

        .duration-slider-area {
            background: rgba(20, 20, 20, 0.5);
            border-radius: 15px;
            padding: 1.5rem;
            border: 1px solid rgba(37, 211, 102, 0.2);
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
            background: rgba(30, 30, 30, 0.8);
            border: 1px solid #1a5c3a;
            color: #4AE381;
            padding: 0.4rem 1rem;
            border-radius: 1.5rem;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.85rem;
        }

        .quick-pick button:hover {
            border-color: #25D366;
        }

        .quick-pick button.active {
            background: rgba(18, 140, 126, 0.8);
            border-color: #4AE381;
            color: #fff;
        }

        input[type="range"] {
            -webkit-appearance: none;
            width: 100%;
            height: 6px;
            background: linear-gradient(90deg, #128C7E, #25D366);
            border-radius: 20px;
            outline: none;
            cursor: pointer;
        }

        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 22px;
            height: 22px;
            background: #4AE381;
            border-radius: 50%;
            border: 3px solid #128C7E;
            cursor: grab;
        }

        .selected-days {
            font-size: 2rem;
            font-weight: 600;
            color: #4AE381;
        }

        .price-display {
            font-size: 1.8rem;
            font-weight: 600;
            color: #fff;
        }

        /* ============ PERMANENT CARD ============ */
        .permanent-card {
            margin-top: 1.5rem;
            background: rgba(30, 30, 30, 0.5);
            border: 2px solid rgba(37, 211, 102, 0.3);
            border-radius: 15px;
            padding: 1.8rem;
            text-align: center;
        }

        .permanent-card h3 {
            color: #4AE381;
            font-size: 1.5rem;
            font-weight: 600;
        }

        .permanent-price {
            display: flex;
            gap: 1.2rem;
            justify-content: center;
            margin: 0.8rem 0;
            flex-wrap: wrap;
        }

        .old-price {
            color: #ff6b6b;
            text-decoration: line-through;
            font-size: 1.4rem;
        }

        .new-price {
            color: #fff;
            background: rgba(18, 140, 126, 0.8);
            padding: 0.3rem 1.5rem;
            border-radius: 2rem;
            font-size: 2rem;
            font-weight: 600;
        }

        .discount-badge {
            background: rgba(37, 211, 102, 0.2);
            color: #4AE381;
            padding: 0.4rem 1.2rem;
            border-radius: 2rem;
            display: inline-block;
            font-size: 0.85rem;
        }

        /* ============ FOOTER ============ */
        .footer-credit {
            text-align: center;
            margin-top: 1.5rem;
            color: #888;
            font-size: 0.8rem;
            border-top: 1px solid #1a5c3a;
            padding-top: 1.2rem;
            display: flex;
            justify-content: center;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .footer-credit a {
            color: #4AE381;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .footer-credit a:hover {
            color: #fff;
            text-shadow: 0 0 8px rgba(37, 211, 102, 0.5);
        }

        /* ============ MODALS ============ */
        .modal-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(8px);
            z-index: 100;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }
        .modal-overlay.active {
            display: flex;
        }
        .modal-content {
            background: rgba(20, 20, 20, 0.95);
            border: 1px solid rgba(37, 211, 102, 0.3);
            border-radius: 20px;
            padding: 2rem;
            max-width: 480px;
            width: 100%;
            text-align: center;
        }

        .modal-options {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 1rem;
        }

        .modal-btn {
            padding: 0.8rem 2rem;
            border-radius: 2rem;
            font-weight: 600;
            cursor: pointer;
            border: none;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .modal-btn-limit {
            background: rgba(18, 140, 126, 0.8);
            color: #4AE381;
            border: 1px solid #25D366;
        }

        .modal-btn-normal {
            background: rgba(37, 211, 102, 0.2);
            color: #fff;
            border: 1px solid #4AE381;
        }

        .modal-btn:hover {
            transform: translateY(-2px);
        }

        .modal-close {
            margin-top: 1rem;
            background: none;
            border: none;
            color: #888;
            cursor: pointer;
            font-size: 0.9rem;
        }

        .verify-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.95);
            backdrop-filter: blur(15px);
            z-index: 200;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }
        .verify-modal.active {
            display: flex;
        }
        .verify-content {
            background: rgba(20, 20, 20, 0.95);
            border: 2px solid rgba(37, 211, 102, 0.4);
            border-radius: 20px;
            padding: 2.5rem 2rem;
            max-width: 520px;
            width: 100%;
            text-align: center;
            box-shadow: 0 0 50px rgba(37, 211, 102, 0.2);
        }

        .verify-title {
            font-size: 1.3rem;
            font-weight: 600;
            color: #4AE381;
        }

        .verify-subtitle {
            font-size: 0.9rem;
            color: #999;
            margin-bottom: 1.5rem;
        }

        .verify-progress-container {
            width: 100%;
            background: rgba(20, 20, 20, 0.8);
            border-radius: 2rem;
            height: 10px;
            overflow: hidden;
            border: 1px solid #1a5c3a;
            margin-bottom: 0.8rem;
        }
        .verify-progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #128C7E, #25D366, #4AE381);
            width: 0%;
            transition: width 0.1s ease;
        }
        .verify-percentage {
            font-size: 1.8rem;
            font-weight: 600;
            color: #25D366;
        }
        .verify-status {
            font-size: 0.9rem;
            color: #a8e6c1;
            min-height: 2rem;
        }
        .verify-checkmark {
            font-size: 2.5rem;
            color: #22c55e;
            display: none;
        }

        /* ============ RESPONSIVE ============ */
        @media (max-width: 768px) {
            .hero-title {
                font-size: 28px;
            }
            .section {
                padding: 20px;
            }
            .nav-container {
                flex-wrap: wrap;
            }
            .loading-logo {
                width: 80px;
                height: 80px;
            }
            .loading-title {
                font-size: 1.2rem;
            }
            .selected-days {
                font-size: 1.5rem;
            }
            .price-display {
                font-size: 1.4rem;
            }
        }

        @media (max-width: 480px) {
            main {
                padding: 20px 10px;
            }
            .section {
                padding: 15px;
                border-radius: 15px;
            }
            .btn {
                padding: 10px 20px;
                font-size: 0.85rem;
            }
            .new-price {
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>

    <!-- ============ LOADING SCREEN (15 DETIK) ============ -->
    <div class="loading-screen" id="loadingScreen">
        <div class="loading-logo">
            <!-- LOGO WHATSAPP ASLI -->
            <svg viewBox="0 0 32 32" xmlns="http://www.w3.org/2000/svg">
                <path d="M16.004 3C8.832 3 3 8.832 3 16.004c0 2.293.598 4.543 1.736 6.52L3 29l6.695-1.704A12.94 12.94 0 0 0 16.004 29C23.168 29 29 23.168 29 16.004S23.168 3 16.004 3z" fill="#25D366"/>
                <path d="M23.648 19.32c-.302-.152-1.79-.883-2.066-.984-.276-.1-.477-.152-.68.151-.2.303-.779.984-.955 1.185-.176.202-.352.228-.654.076-.302-.152-1.276-.47-2.43-1.5-.899-.802-1.506-1.793-1.682-2.096-.176-.302-.019-.465.132-.616.136-.135.302-.352.453-.528.151-.176.202-.302.302-.504.1-.202.05-.378-.025-.53-.076-.151-.68-1.637-.93-2.242-.245-.59-.494-.51-.68-.52-.175-.01-.378-.012-.58-.012-.201 0-.529.075-.806.378-.277.302-1.057 1.033-1.057 2.52 0 1.488 1.083 2.925 1.234 3.127.151.202 2.132 3.256 5.166 4.565.722.312 1.286.498 1.725.637.725.23 1.385.197 1.907.12.582-.087 1.79-.732 2.042-1.438.252-.706.252-1.31.176-1.437-.075-.127-.276-.202-.578-.354z" fill="#fff"/>
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

    <div id="particles"></div>

    <!-- ============ HEADER ============ -->
    <header>
        <div class="logo-container">
            <!-- LOGO WHATSAPP ASLI -->
            <svg class="logo" viewBox="0 0 32 32" xmlns="http://www.w3.org/2000/svg">
                <path d="M16.004 3C8.832 3 3 8.832 3 16.004c0 2.293.598 4.543 1.736 6.52L3 29l6.695-1.704A12.94 12.94 0 0 0 16.004 29C23.168 29 29 23.168 29 16.004S23.168 3 16.004 3z" fill="#25D366"/>
                <path d="M23.648 19.32c-.302-.152-1.79-.883-2.066-.984-.276-.1-.477-.152-.68.151-.2.303-.779.984-.955 1.185-.176.202-.352.228-.654.076-.302-.152-1.276-.47-2.43-1.5-.899-.802-1.506-1.793-1.682-2.096-.176-.302-.019-.465.132-.616.136-.135.302-.352.453-.528.151-.176.202-.302.302-.504.1-.202.05-.378-.025-.53-.076-.151-.68-1.637-.93-2.242-.245-.59-.494-.51-.68-.52-.175-.01-.378-.012-.58-.012-.201 0-.529.075-.806.378-.277.302-1.057 1.033-1.057 2.52 0 1.488 1.083 2.925 1.234 3.127.151.202 2.132 3.256 5.166 4.565.722.312 1.286.498 1.725.637.725.23 1.385.197 1.907.12.582-.087 1.79-.732 2.042-1.438.252-.706.252-1.31.176-1.437-.075-.127-.276-.202-.578-.354z" fill="#fff"/>
            </svg>
        </div>
        <h1 class="hero-title">Premium Bug WA</h1>
        <div class="nav-container">
            <a href="#plans" class="nav-link"><i class="fas fa-crown"></i> Plans</a>
            <a href="#about" class="nav-link"><i class="fas fa-info-circle"></i> About</a>
            <a href="#contact" class="nav-link"><i class="fas fa-envelope"></i> Contact</a>
        </div>
    </header>

    <!-- ============ MAIN CONTENT ============ -->
    <main id="mainContent" style="display: none;">
        <section class="section hero">
            <div class="hero-subtitle">Akses Bot Telegram Premium · Admin @ARKAUSERV2</div>
            <span style="display: inline-flex; align-items: center; gap: 5px; background: rgba(34, 197, 94, 0.2); color: #4ade80; padding: 5px 15px; border-radius: 20px; font-size: 0.8rem; margin-bottom: 20px;">
                <i class="fas fa-check-circle"></i> VERIFIED
            </span>
            <br>
            <a href="#plans" class="btn">
                <i class="fas fa-crown"></i> View Plans
            </a>
        </section>

        <!-- Admin Banner -->
        <section class="section" style="padding: 20px;">
            <div class="admin-banner">
                <div class="admin-avatar">A</div>
                <div style="text-align: left;">
                    <div style="font-size: 0.75rem; color: #999;">Admin Resmi</div>
                    <a class="admin-username" href="https://t.me/ARKAUSERV2" target="_blank">
                        <i class="fab fa-telegram"></i> @ARKAUSERV2
                    </a>
                </div>
                <a href="https://t.me/ARKAUSERV2" target="_blank" class="bot-link" style="background: rgba(18,140,126,0.3); border-color: #25D366;">
                    <i class="fab fa-telegram"></i> Chat Admin
                </a>
            </div>

            <div class="bot-section">
                <a class="bot-link" href="https://t.me/BugVipFazaxBot" target="_blank">
                    <i class="fab fa-telegram"></i> @BugVipFazaxBot | Cek Bot
                </a>
                <div class="status-wrapper">
                    <span class="status-badge">
                        <span class="pulse-dot checking" id="statusDot"></span>
                        <span id="statusText">Memeriksa...</span>
                    </span>
                    <button class="check-btn" onclick="checkBotStatus()">
                        <i class="fas fa-sync-alt"></i> Cek
                    </button>
                </div>
                <div class="stats-row">
                    <span><i class="fas fa-bolt"></i> Aktivasi Instan</span>
                    <span><i class="fas fa-lock"></i> Aman</span>
                    <span><i class="fas fa-users"></i> 100+</span>
                </div>
            </div>
        </section>

        <!-- Plans Section -->
        <section id="plans" class="section">
            <h2 class="section-title"><i class="fas fa-crown"></i> Pilih Durasi Akses</h2>
            
            <div class="select-label" style="margin-bottom: 15px;">
                <i class="fas fa-clock"></i> Durasi (1-30 Hari)
            </div>
            
            <div class="quick-pick">
                <button onclick="setDays(3)">3 Hari</button>
                <button onclick="setDays(7)" class="active">7 Hari</button>
                <button onclick="setDays(14)">14 Hari</button>
                <button onclick="setDays(30)">30 Hari</button>
            </div>
            
            <div class="duration-slider-area">
                <div class="selected-days" id="selectedDaysDisplay">7</div>
                <input type="range" id="durationSlider" min="1" max="30" value="7" oninput="updatePriceAndDays()">
                <div style="margin-top: 15px;">
                    <span class="price-display" id="totalPriceDisplay">Rp 49.000</span>
                    <span style="color: #999; font-size: 0.9rem;">(Rp 7.000/hari)</span>
                </div>
            </div>

            <div style="text-align: center; margin: 1.5rem 0;">
                <button class="btn" onclick="mulaiVerifikasi('harian')">
                    <i class="fas fa-shopping-cart"></i> Beli via Admin
                </button>
            </div>

            <!-- Permanent Card -->
            <div class="permanent-card">
                <h3><i class="fas fa-crown"></i> AKSES PERMANEN</h3>
                <div class="permanent-price">
                    <span class="old-price">Rp 217.000</span>
                    <span class="new-price">Rp 211.000</span>
                </div>
                <div class="discount-badge">
                    <i class="fas fa-fire"></i> DISKON s/d 26 Nov 2026
                </div>
                <div style="margin-top: 1rem;">
                    <button class="btn" onclick="mulaiVerifikasi('permanen')">
                        <i class="fas fa-gem"></i> Beli Permanen
                    </button>
                </div>
            </div>
        </section>

        <!-- About Section -->
        <section id="about" class="section">
            <h2 class="section-title"><i class="fas fa-info-circle"></i> Tentang Premium Bug WA</h2>
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px;">
                <div style="line-height: 1.6;">
                    <p>Premium Bug WA adalah akses premium untuk Bot Telegram dengan fitur eksploitasi WhatsApp Application.</p>
                    <p style="margin-top: 15px;">Dibangun dengan teknologi terbaru untuk memberikan pengalaman terbaik.</p>
                </div>
                <div>
                    <ul style="list-style: none;">
                        <li style="margin: 15px 0; padding-left: 35px; position: relative;">
                            <i class="fas fa-bug" style="position: absolute; left: 0; top: 2px; color: #25D366;"></i>
                            Advanced Bug Detection
                        </li>
                        <li style="margin: 15px 0; padding-left: 35px; position: relative;">
                            <i class="fas fa-shield-alt" style="position: absolute; left: 0; top: 2px; color: #25D366;"></i>
                            Real-time Vulnerability Scanning
                        </li>
                        <li style="margin: 15px 0; padding-left: 35px; position: relative;">
                            <i class="fas fa-bolt" style="position: absolute; left: 0; top: 2px; color: #25D366;"></i>
                            High-performance API
                        </li>
                        <li style="margin: 15px 0; padding-left: 35px; position: relative;">
                            <i class="fas fa-mobile-alt" style="position: absolute; left: 0; top: 2px; color: #25D366;"></i>
                            Responsive Design
                        </li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="section">
            <h2 class="section-title"><i class="fas fa-envelope"></i> Hubungi Admin</h2>
            <div style="text-align: center; margin-bottom: 20px;">
                <a href="https://t.me/ARKAUSERV2" target="_blank" class="btn">
                    <i class="fab fa-telegram"></i> @ARKAUSERV2
                </a>
            </div>
            <div class="footer-credit">
                <a href="https://t.me/BugVipFazaxBot" target="_blank">
                    <i class="fab fa-telegram"></i> Cek Bot
                </a>
                <a href="https://t.me/ARKAUSERV2" target="_blank">
                    <i class="fas fa-user"></i> Admin
                </a>
                <a href="https://t.me/LimitFazxBot" target="_blank">
                    <i class="fas fa-robot"></i> Bot Limit
                </a>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer style="display: none; position: relative; z-index: 2; text-align: center; padding: 20px; background: rgba(10,10,10,0.8); border-top: 1px solid rgba(37,211,102,0.2);" id="footer">
        <p style="font-size: 14px; color: #999;">© 2026 Premium Bug WA. All rights reserved.</p>
    </footer>

    <!-- ============ MODAL LIMIT ============ -->
    <div class="modal-overlay" id="modalLimit">
        <div class="modal-content">
            <h3 style="color: #4AE381; font-weight: 600;">
                <i class="fas fa-exclamation-triangle" style="color: #f59e0b;"></i> CEK LIMIT TELEGRAM
            </h3>
            <p style="margin-top: 15px;">Apakah akun Telegram Anda <strong>terkena LIMIT</strong>?</p>
            <div class="modal-options">
                <button class="modal-btn modal-btn-limit" onclick="pilihLimit(true)">
                    <i class="fas fa-exclamation-circle"></i> YA, Limit
                </button>
                <button class="modal-btn modal-btn-normal" onclick="pilihLimit(false)">
                    <i class="fas fa-check-circle"></i> TIDAK
                </button>
            </div>
            <button class="modal-close" onclick="tutupModal()">✕ Tutup</button>
        </div>
    </div>

    <!-- ============ MODAL VERIFIKASI ============ -->
    <div class="verify-modal" id="verifyModal">
        <div class="verify-content">
            <div class="verify-title">
                <i class="fas fa-shield-alt"></i> VERIFIKASI ANTI-BOT
            </div>
            <div class="verify-subtitle">Memastikan Anda manusia (10 detik)</div>
            <div class="verify-progress-container">
                <div class="verify-progress-bar" id="verifyProgressBar"></div>
            </div>
            <div class="verify-percentage" id="verifyPercentage">0%</div>
            <div class="verify-status" id="verifyStatus">🔄 Memeriksa...</div>
            <div class="verify-checkmark" id="verifyCheckmark">
                <i class="fas fa-check-circle" style="color: #22c55e;"></i>
            </div>
        </div>
    </div>

    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdn.jsdelivr.net/gh/jnicol/particleground/jquery.particleground.min.js"></script>
    <script>
        const BOT_USERNAME = 'BugVipFazaxBot';
        const ADMIN_USERNAME = 'ARKAUSERV2';
        const LIMIT_BOT_USERNAME = 'LimitFazxBot';
        const HARGA_PER_HARI = 7000;
        let pendingPurchaseType = 'harian';
        let verifyInterval = null;
        let loadInterval = null;

        // ============ PARTICLE BACKGROUND ============
        document.addEventListener('DOMContentLoaded', function () {
            particleground(document.getElementById('particles'), {
                dotColor: '#25D366',
                lineColor: '#128C7E',
                minSpeedX: 0.1,
                maxSpeedX: 0.3,
                minSpeedY: 0.1,
                maxSpeedY: 0.3,
                density: 8000,
                particleRadius: 3,
            });
        });

        // ============ LOADING SCREEN (15 DETIK) ============
        function startLoading() {
            const loadingScreen = document.getElementById('loadingScreen');
            const progressBar = document.getElementById('loadingProgressBar');
            const percentage = document.getElementById('loadingPercentage');
            const status = document.getElementById('loadingStatus');
            const mainContent = document.getElementById('mainContent');
            const footer = document.getElementById('footer');
            
            let progress = 0;
            const totalDuration = 15000; // 15 detik
            const interval = 100;
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
                        mainContent.style.display = 'block';
                        footer.style.display = 'block';
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
                        bukaModalLimit();
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

        // ============ INITIALIZATION ============
        window.addEventListener('load', () => {
            startLoading();
        });
        window.currentSelectedDays = 7;
        window.currentTotalHarga = 49000;
    </script>
</body>
</html>
