<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Premium Bug WA - Dashboard</title>

    <!-- Google Font & Icon -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">

    <style>
        :root {
            --wa-green: #25D366;
            --wa-dark: #128C7E;
            --wa-light: #4AE381;
            --bg-dark: #0a0a0a;
            --bg-card: rgba(30, 30, 30, 0.7);
            --border-green: rgba(37, 211, 102, 0.3);
            --text-primary: #e0e0e0;
            --text-secondary: #aaa;
            --text-muted: #777;
            --gold: #fbbf24;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background: var(--bg-dark);
            font-family: 'Poppins', sans-serif;
            color: var(--text-primary);
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
        }

        /* ============ PARTICLE BACKGROUND ============ */
        #particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        /* ============ LOADING SCREEN ============ */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 50% 50%, #0d1a12 0%, #0a0a0a 100%);
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
            width: 110px;
            height: 110px;
            animation: floatLogo 2s ease-in-out infinite;
        }
        @keyframes floatLogo {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }
        .loading-logo svg {
            width: 100%;
            height: 100%;
            filter: drop-shadow(0 0 40px rgba(37, 211, 102, 0.7));
        }
        .loading-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--wa-light);
            letter-spacing: 3px;
            text-shadow: 0 0 30px rgba(37, 211, 102, 0.5);
        }
        .loading-subtitle {
            font-size: 0.85rem;
            color: #a8e6c1;
            letter-spacing: 1px;
        }
        .loading-progress-container {
            width: 80%;
            max-width: 350px;
            background: rgba(255,255,255,0.05);
            border-radius: 2rem;
            height: 10px;
            overflow: hidden;
            border: 1px solid rgba(37, 211, 102, 0.3);
            box-shadow: inset 0 2px 10px rgba(0,0,0,0.5);
        }
        .loading-progress-bar {
            height: 100%;
            background: linear-gradient(90deg, var(--wa-dark), var(--wa-green), var(--wa-light));
            border-radius: 2rem;
            width: 0%;
            transition: width 0.2s ease;
            box-shadow: 0 0 25px rgba(37, 211, 102, 0.6);
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
            font-size: 2rem;
            font-weight: 700;
            color: var(--wa-green);
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
            background: rgba(10, 10, 10, 0.85);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(37, 211, 102, 0.25);
            box-shadow: 0 5px 30px rgba(0,0,0,0.5);
        }
        .logo-container {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 12px;
            margin-bottom: 12px;
        }
        .logo {
            width: 55px;
            height: 55px;
            filter: drop-shadow(0 0 15px rgba(37, 211, 102, 0.5));
        }
        .header-title {
            font-size: 1.6rem;
            font-weight: 700;
            background: linear-gradient(130deg, #a8e6c1, #4AE381, #25D366);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: -0.5px;
        }
        .nav-container {
            display: flex;
            justify-content: center;
            gap: 8px;
            flex-wrap: wrap;
        }
        .nav-link {
            color: #ccc;
            text-decoration: none;
            font-weight: 500;
            padding: 8px 14px;
            border-radius: 20px;
            font-size: 0.8rem;
            transition: all 0.3s ease;
            border: 1px solid transparent;
        }
        .nav-link:hover {
            background: rgba(37, 211, 102, 0.15);
            border-color: rgba(37, 211, 102, 0.3);
            color: var(--wa-light);
            text-shadow: 0 0 10px rgba(37, 211, 102, 0.5);
        }

        /* ============ MAIN ============ */
        main {
            position: relative;
            z-index: 2;
            max-width: 1100px;
            margin: 0 auto;
            padding: 25px 15px;
        }
        .section {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(37, 211, 102, 0.2);
            backdrop-filter: blur(15px);
            border-radius: 20px;
            padding: 30px 20px;
            margin-bottom: 25px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.3), 0 0 20px rgba(37, 211, 102, 0.08);
            transition: all 0.3s ease;
        }
        .section:hover {
            border-color: rgba(37, 211, 102, 0.4);
            box-shadow: 0 15px 50px rgba(0,0,0,0.4), 0 0 30px rgba(37, 211, 102, 0.15);
        }
        .section-title {
            font-size: 1.5rem;
            color: var(--wa-light);
            text-align: center;
            margin-bottom: 15px;
            font-weight: 700;
            text-shadow: 0 0 15px rgba(37, 211, 102, 0.4);
        }
        .section-subtitle {
            text-align: center;
            color: var(--text-secondary);
            font-size: 0.85rem;
            margin-bottom: 25px;
            letter-spacing: 0.5px;
        }

        /* ============ TRUST BADGES ============ */
        .trust-badges {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
            gap: 15px;
        }
        .trust-badge {
            background: rgba(30, 30, 30, 0.7);
            border: 1px solid rgba(37, 211, 102, 0.25);
            border-radius: 15px;
            padding: 20px 15px;
            text-align: center;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        .trust-badge::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--wa-green), transparent);
        }
        .trust-badge:hover {
            transform: translateY(-3px);
            border-color: rgba(37, 211, 102, 0.5);
            box-shadow: 0 8px 25px rgba(37, 211, 102, 0.2);
        }
        .trust-badge i {
            font-size: 2rem;
            color: var(--wa-green);
            margin-bottom: 10px;
            filter: drop-shadow(0 0 10px rgba(37, 211, 102, 0.5));
        }
        .trust-badge h4 {
            font-size: 0.85rem;
            color: #fff;
            margin-bottom: 5px;
            font-weight: 600;
        }
        .trust-badge p {
            font-size: 0.7rem;
            color: var(--text-secondary);
        }

        /* ============ FEATURES ============ */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
            gap: 15px;
        }
        .feature-card {
            background: rgba(30, 30, 30, 0.7);
            border: 1px solid rgba(37, 211, 102, 0.25);
            border-radius: 15px;
            padding: 20px 15px;
            text-align: center;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        .feature-card::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--wa-green), transparent);
            opacity: 0;
            transition: opacity 0.3s;
        }
        .feature-card:hover::after {
            opacity: 1;
        }
        .feature-card:hover {
            transform: translateY(-3px);
            border-color: rgba(37, 211, 102, 0.5);
            box-shadow: 0 8px 25px rgba(37, 211, 102, 0.2);
        }
        .feature-card i {
            font-size: 2rem;
            color: var(--wa-green);
            margin-bottom: 12px;
            filter: drop-shadow(0 0 10px rgba(37, 211, 102, 0.5));
        }
        .feature-card h4 {
            font-size: 0.9rem;
            color: #fff;
            margin-bottom: 8px;
            font-weight: 600;
        }
        .feature-card p {
            font-size: 0.75rem;
            color: var(--text-secondary);
            line-height: 1.5;
        }

        /* ============ TESTIMONIALS ============ */
        .testimonial-stats {
            display: flex;
            justify-content: center;
            gap: 40px;
            margin-bottom: 25px;
            flex-wrap: wrap;
        }
        .testimonial-stat {
            text-align: center;
            background: rgba(30, 30, 30, 0.7);
            border: 1px solid rgba(37, 211, 102, 0.25);
            border-radius: 15px;
            padding: 15px 25px;
        }
        .testimonial-stat .number {
            font-size: 1.8rem;
            font-weight: 800;
            background: linear-gradient(130deg, #a8e6c1, #4AE381, #25D366);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        .testimonial-stat .label {
            font-size: 0.7rem;
            color: var(--text-secondary);
            letter-spacing: 0.5px;
        }
        .testimonials-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 12px;
            max-height: 500px;
            overflow-y: auto;
            padding-right: 8px;
        }
        .testimonials-grid::-webkit-scrollbar {
            width: 6px;
        }
        .testimonials-grid::-webkit-scrollbar-track {
            background: rgba(255,255,255,0.05);
            border-radius: 10px;
        }
        .testimonials-grid::-webkit-scrollbar-thumb {
            background: var(--wa-dark);
            border-radius: 10px;
        }
        .testimonial-card {
            background: rgba(30, 30, 30, 0.7);
            border: 1px solid rgba(37, 211, 102, 0.2);
            border-radius: 12px;
            padding: 18px 15px;
            transition: all 0.3s ease;
        }
        .testimonial-card:hover {
            border-color: rgba(37, 211, 102, 0.4);
            box-shadow: 0 5px 20px rgba(37, 211, 102, 0.15);
        }
        .testimonial-header {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 10px;
        }
        .testimonial-avatar {
            width: 38px;
            height: 38px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--wa-dark), var(--wa-green));
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 0.9rem;
            color: #000;
            flex-shrink: 0;
            box-shadow: 0 0 15px rgba(37, 211, 102, 0.4);
        }
        .testimonial-info h5 {
            font-size: 0.8rem;
            color: #fff;
            font-weight: 600;
        }
        .testimonial-info span {
            font-size: 0.65rem;
            color: var(--text-muted);
        }
        .testimonial-stars {
            font-size: 0.75rem;
            color: var(--gold);
            margin-bottom: 8px;
            letter-spacing: 2px;
        }
        .testimonial-text {
            font-size: 0.75rem;
            color: #ccc;
            line-height: 1.5;
            font-style: italic;
            border-left: 2px solid rgba(37, 211, 102, 0.3);
            padding-left: 10px;
        }

        /* ============ FAQ ============ */
        .faq-item {
            background: rgba(30, 30, 30, 0.7);
            border: 1px solid rgba(37, 211, 102, 0.2);
            border-radius: 12px;
            margin-bottom: 10px;
            overflow: hidden;
            transition: all 0.3s ease;
        }
        .faq-item:hover {
            border-color: rgba(37, 211, 102, 0.4);
        }
        .faq-question {
            padding: 15px 18px;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.85rem;
            font-weight: 600;
            color: #fff;
            transition: all 0.3s;
        }
        .faq-question:hover {
            background: rgba(37, 211, 102, 0.08);
        }
        .faq-question i {
            color: var(--wa-green);
            font-size: 0.7rem;
            transition: transform 0.3s;
        }
        .faq-question.active i {
            transform: rotate(180deg);
        }
        .faq-answer {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease;
        }
        .faq-answer.active {
            max-height: 200px;
        }
        .faq-answer p {
            padding: 0 18px 15px;
            font-size: 0.75rem;
            color: var(--text-secondary);
            line-height: 1.6;
        }

        /* ============ PLANS ============ */
        .duration-slider-area {
            background: rgba(30, 30, 30, 0.7);
            border: 1px solid rgba(37, 211, 102, 0.3);
            border-radius: 15px;
            padding: 25px 20px;
            margin-bottom: 20px;
            text-align: center;
            box-shadow: inset 0 0 30px rgba(37, 211, 102, 0.05);
        }
        .quick-pick {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            justify-content: center;
            margin-bottom: 15px;
        }
        .quick-pick button {
            background: rgba(20, 20, 20, 0.8);
            border: 1px solid rgba(37, 211, 102, 0.3);
            color: #ccc;
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.75rem;
            font-weight: 500;
            transition: all 0.3s;
        }
        .quick-pick button:hover {
            border-color: var(--wa-green);
            color: var(--wa-light);
        }
        .quick-pick button.active {
            background: rgba(18, 140, 126, 0.8);
            border-color: var(--wa-light);
            color: #fff;
            box-shadow: 0 0 15px rgba(37, 211, 102, 0.4);
        }
        input[type="range"] {
            -webkit-appearance: none;
            width: 100%;
            height: 6px;
            background: linear-gradient(90deg, var(--wa-dark), var(--wa-green), var(--wa-light));
            border-radius: 10px;
            outline: none;
            margin: 15px 0;
            box-shadow: 0 0 15px rgba(37, 211, 102, 0.3);
        }
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 22px;
            height: 22px;
            background: #fff;
            border-radius: 50%;
            border: 3px solid var(--wa-green);
            cursor: grab;
            box-shadow: 0 0 20px rgba(37, 211, 102, 0.5);
        }
        .selected-days {
            font-size: 2.2rem;
            font-weight: 800;
            background: linear-gradient(130deg, #a8e6c1, #4AE381, #25D366);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        .price-display {
            font-size: 1.8rem;
            font-weight: 700;
            color: #fff;
            text-shadow: 0 0 20px rgba(255,255,255,0.3);
        }
        .permanent-card {
            background: rgba(30, 30, 30, 0.7);
            border: 2px solid rgba(37, 211, 102, 0.4);
            border-radius: 15px;
            padding: 25px 20px;
            text-align: center;
            box-shadow: 0 0 40px rgba(37, 211, 102, 0.15);
            position: relative;
            overflow: hidden;
        }
        .permanent-card::before {
            content: '★ PREMIUM ★';
            position: absolute;
            top: 10px;
            left: 50%;
            transform: translateX(-50%);
            background: linear-gradient(135deg, var(--wa-dark), var(--wa-green));
            color: #000;
            font-size: 0.6rem;
            font-weight: 700;
            letter-spacing: 2px;
            padding: 3px 15px;
            border-radius: 15px;
        }
        .permanent-card h3 {
            color: var(--wa-light);
            font-size: 1.2rem;
            margin-top: 20px;
            margin-bottom: 10px;
            font-weight: 700;
        }
        .permanent-price {
            display: flex;
            gap: 12px;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
            margin: 15px 0;
        }
        .old-price {
            color: #ff6b6b;
            text-decoration: line-through;
            font-size: 1.1rem;
        }
        .new-price {
            color: #fff;
            background: linear-gradient(135deg, var(--wa-dark), var(--wa-green));
            padding: 8px 20px;
            border-radius: 25px;
            font-size: 1.5rem;
            font-weight: 800;
            box-shadow: 0 0 20px rgba(37, 211, 102, 0.4);
        }
        .discount-badge {
            background: rgba(251, 191, 36, 0.2);
            color: var(--gold);
            padding: 5px 15px;
            border-radius: 20px;
            display: inline-block;
            font-size: 0.7rem;
            font-weight: 600;
            border: 1px solid rgba(251, 191, 36, 0.4);
        }
        .btn {
            display: inline-block;
            background: linear-gradient(135deg, var(--wa-dark), var(--wa-green));
            color: #000;
            padding: 12px 25px;
            border-radius: 25px;
            font-weight: 700;
            border: none;
            cursor: pointer;
            font-family: 'Poppins', sans-serif;
            font-size: 0.85rem;
            transition: all 0.3s;
            box-shadow: 0 5px 20px rgba(37, 211, 102, 0.3);
            letter-spacing: 0.5px;
        }
        .btn:hover {
            background: var(--wa-light);
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(37, 211, 102, 0.5);
        }

        /* ============ FOOTER ============ */
        .footer-credit {
            text-align: center;
            margin-top: 20px;
            color: var(--text-muted);
            font-size: 0.75rem;
            border-top: 1px solid rgba(37, 211, 102, 0.2);
            padding-top: 20px;
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }
        .footer-credit a {
            color: var(--wa-light);
            text-decoration: none;
            transition: all 0.3s;
        }
        .footer-credit a:hover {
            color: #fff;
            text-shadow: 0 0 10px rgba(37, 211, 102, 0.5);
        }

        /* ============ MODALS ============ */
        .modal-overlay, .verify-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(15px);
            z-index: 100;
            align-items: center;
            justify-content: center;
            padding: 15px;
        }
        .modal-overlay.active, .verify-modal.active {
            display: flex;
        }
        .modal-content, .verify-content {
            background: rgba(20, 20, 20, 0.95);
            border: 1px solid rgba(37, 211, 102, 0.4);
            border-radius: 20px;
            padding: 30px 25px;
            max-width: 450px;
            width: 100%;
            text-align: center;
            box-shadow: 0 0 60px rgba(37, 211, 102, 0.3);
        }
        .modal-options {
            display: flex;
            gap: 12px;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 20px;
        }
        .modal-btn {
            padding: 10px 22px;
            border-radius: 25px;
            font-weight: 600;
            cursor: pointer;
            border: none;
            font-size: 0.8rem;
            transition: all 0.3s;
        }
        .modal-btn:hover {
            transform: translateY(-2px);
        }
        .modal-btn-limit {
            background: rgba(18, 140, 126, 0.8);
            color: var(--wa-light);
            border: 1px solid var(--wa-green);
        }
        .modal-btn-normal {
            background: rgba(37, 211, 102, 0.2);
            color: #fff;
            border: 1px solid var(--wa-light);
        }
        .modal-close {
            margin-top: 15px;
            background: none;
            border: none;
            color: var(--text-muted);
            cursor: pointer;
            font-size: 0.8rem;
        }
        .verify-progress-container {
            width: 100%;
            background: rgba(0,0,0,0.5);
            border-radius: 20px;
            height: 10px;
            overflow: hidden;
            border: 1px solid rgba(37, 211, 102, 0.3);
            margin: 15px 0;
        }
        .verify-progress-bar {
            height: 100%;
            background: linear-gradient(90deg, var(--wa-dark), var(--wa-green), var(--wa-light));
            width: 0%;
            transition: width 0.1s ease;
            box-shadow: 0 0 20px rgba(37, 211, 102, 0.6);
        }

        /* ============ RESPONSIVE ============ */
        @media (max-width: 600px) {
            .trust-badges { grid-template-columns: repeat(2, 1fr); }
            .features-grid { grid-template-columns: 1fr; }
            .testimonials-grid { grid-template-columns: 1fr; max-height: 400px; }
            .section-title { font-size: 1.2rem; }
            .testimonial-stats { gap: 15px; }
            .testimonial-stat { padding: 10px 15px; }
            .testimonial-stat .number { font-size: 1.4rem; }
        }
        @media (min-width: 601px) and (max-width: 900px) {
            .trust-badges { grid-template-columns: repeat(3, 1fr); }
            .features-grid { grid-template-columns: repeat(2, 1fr); }
            .testimonials-grid { grid-template-columns: repeat(2, 1fr); }
        }
        @media (min-width: 901px) {
            .trust-badges { grid-template-columns: repeat(6, 1fr); }
            .features-grid { grid-template-columns: repeat(4, 1fr); }
            .testimonials-grid { grid-template-columns: repeat(3, 1fr); }
        }
    </style>
</head>
<body>

    <!-- LOADING SCREEN -->
    <div class="loading-screen" id="loadingScreen">
        <div class="loading-logo">
            <svg viewBox="0 0 32 32" xmlns="http://www.w3.org/2000/svg">
                <path d="M16.004 3C8.832 3 3 8.832 3 16.004c0 2.293.598 4.543 1.736 6.52L3 29l6.695-1.704A12.94 12.94 0 0 0 16.004 29C23.168 29 29 23.168 29 16.004S23.168 3 16.004 3z" fill="#25D366"/>
                <path d="M23.648 19.32c-.302-.152-1.79-.883-2.066-.984-.276-.1-.477-.152-.68.151-.2.303-.779.984-.955 1.185-.176.202-.352.228-.654.076-.302-.152-1.276-.47-2.43-1.5-.899-.802-1.506-1.793-1.682-2.096-.176-.302-.019-.465.132-.616.136-.135.302-.352.453-.528.151-.176.202-.302.302-.504.1-.202.05-.378-.025-.53-.076-.151-.68-1.637-.93-2.242-.245-.59-.494-.51-.68-.52-.175-.01-.378-.012-.58-.012-.201 0-.529.075-.806.378-.277.302-1.057 1.033-1.057 2.52 0 1.488 1.083 2.925 1.234 3.127.151.202 2.132 3.256 5.166 4.565.722.312 1.286.498 1.725.637.725.23 1.385.197 1.907.12.582-.087 1.79-.732 2.042-1.438.252-.706.252-1.31.176-1.437-.075-.127-.276-.202-.578-.354z" fill="#fff"/>
            </svg>
        </div>
        <div class="loading-title">PREMIUM BUG WA</div>
        <div class="loading-subtitle">Memuat aplikasi premium...</div>
        <div class="loading-progress-container">
            <div class="loading-progress-bar" id="loadingProgressBar"></div>
        </div>
        <div class="loading-percentage" id="loadingPercentage">0%</div>
        <div class="loading-status" id="loadingStatus">🔄 Menginisialisasi...</div>
    </div>

    <!-- PARTICLES BACKGROUND -->
    <div id="particles"></div>

    <!-- HEADER -->
    <header>
        <div class="logo-container">
            <svg class="logo" viewBox="0 0 32 32" xmlns="http://www.w3.org/2000/svg">
                <path d="M16.004 3C8.832 3 3 8.832 3 16.004c0 2.293.598 4.543 1.736 6.52L3 29l6.695-1.704A12.94 12.94 0 0 0 16.004 29C23.168 29 29 23.168 29 16.004S23.168 3 16.004 3z" fill="#25D366"/>
                <path d="M23.648 19.32c-.302-.152-1.79-.883-2.066-.984-.276-.1-.477-.152-.68.151-.2.303-.779.984-.955 1.185-.176.202-.352.228-.654.076-.302-.152-1.276-.47-2.43-1.5-.899-.802-1.506-1.793-1.682-2.096-.176-.302-.019-.465.132-.616.136-.135.302-.352.453-.528.151-.176.202-.302.302-.504.1-.202.05-.378-.025-.53-.076-.151-.68-1.637-.93-2.242-.245-.59-.494-.51-.68-.52-.175-.01-.378-.012-.58-.012-.201 0-.529.075-.806.378-.277.302-1.057 1.033-1.057 2.52 0 1.488 1.083 2.925 1.234 3.127.151.202 2.132 3.256 5.166 4.565.722.312 1.286.498 1.725.637.725.23 1.385.197 1.907.12.582-.087 1.79-.732 2.042-1.438.252-.706.252-1.31.176-1.437-.075-.127-.276-.202-.578-.354z" fill="#fff"/>
            </svg>
            <span class="header-title">Premium Bug WA</span>
        </div>
        <div class="nav-container">
            <a href="#plans" class="nav-link"><i class="fas fa-crown"></i> Plans</a>
            <a href="#about" class="nav-link"><i class="fas fa-info-circle"></i> About</a>
            <a href="#testimonials" class="nav-link"><i class="fas fa-comments"></i> Testimoni</a>
            <a href="#faq" class="nav-link"><i class="fas fa-question-circle"></i> FAQ</a>
            <a href="#contact" class="nav-link"><i class="fas fa-envelope"></i> Contact</a>
        </div>
    </header>

    <!-- MAIN CONTENT -->
    <main id="mainContent" style="display: none;">

        <!-- TRUST BADGES -->
        <section class="section">
            <h2 class="section-title"><i class="fas fa-shield-alt"></i> Kenapa Harus Percaya Kami?</h2>
            <p class="section-subtitle">Dipercaya oleh 10.000+ member di seluruh Indonesia</p>
            <div class="trust-badges">
                <div class="trust-badge">
                    <i class="fas fa-clock"></i>
                    <h4>Online 24/7</h4>
                    <p>Bot aktif tanpa henti</p>
                </div>
                <div class="trust-badge">
                    <i class="fas fa-shield-alt"></i>
                    <h4>100% Aman</h4>
                    <p>Tanpa risiko banned</p>
                </div>
                <div class="trust-badge">
                    <i class="fas fa-bolt"></i>
                    <h4>Aktivasi Instan</h4>
                    <p>Kurang dari 1 menit</p>
                </div>
                <div class="trust-badge">
                    <i class="fas fa-users"></i>
                    <h4>10.000+ Member</h4>
                    <p>Dipercaya banyak orang</p>
                </div>
                <div class="trust-badge">
                    <i class="fas fa-headset"></i>
                    <h4>Support Responsif</h4>
                    <p>Respon cepat 24 jam</p>
                </div>
                <div class="trust-badge">
                    <i class="fas fa-sync-alt"></i>
                    <h4>Update Teratur</h4>
                    <p>Fitur baru berkala</p>
                </div>
            </div>
        </section>

        <!-- FEATURES -->
        <section id="about" class="section">
            <h2 class="section-title"><i class="fas fa-star"></i> Fitur Unggulan</h2>
            <p class="section-subtitle">Layanan premium dengan teknologi terbaru untuk pengalaman terbaik</p>
            <div class="features-grid">
                <div class="feature-card">
                    <i class="fas fa-bug"></i>
                    <h4>Advanced Bug Detection</h4>
                    <p>Deteksi bug dengan algoritma terbaru dan akurasi tinggi</p>
                </div>
                <div class="feature-card">
                    <i class="fas fa-shield-alt"></i>
                    <h4>Vulnerability Scanning</h4>
                    <p>Scanning kerentanan real-time untuk keamanan maksimal</p>
                </div>
                <div class="feature-card">
                    <i class="fas fa-bolt"></i>
                    <h4>High-Performance API</h4>
                    <p>API cepat yang menangani request tanpa lag</p>
                </div>
                <div class="feature-card">
                    <i class="fas fa-code"></i>
                    <h4>Multi-Language</h4>
                    <p>Dukungan berbagai bahasa pemrograman</p>
                </div>
                <div class="feature-card">
                    <i class="fas fa-mobile-alt"></i>
                    <h4>Responsive Design</h4>
                    <p>Akses dari HP, tablet, laptop, dan PC</p>
                </div>
                <div class="feature-card">
                    <i class="fas fa-cloud"></i>
                    <h4>Cloud Infrastructure</h4>
                    <p>Uptime 99.9% dengan server handal</p>
                </div>
                <div class="feature-card">
                    <i class="fas fa-lock"></i>
                    <h4>End-to-End Encryption</h4>
                    <p>Data terenkripsi dengan protokol terbaru</p>
                </div>
                <div class="feature-card">
                    <i class="fas fa-chart-line"></i>
                    <h4>Analytics Dashboard</h4>
                    <p>Pantau statistik penggunaan Anda</p>
                </div>
            </div>
        </section>

        <!-- TESTIMONIALS -->
        <section id="testimonials" class="section">
            <h2 class="section-title"><i class="fas fa-comments"></i> Testimoni Member</h2>
            <p class="section-subtitle">Ribuan member telah merasakan manfaatnya</p>
            <div class="testimonial-stats">
                <div class="testimonial-stat">
                    <div class="number">10.000+</div>
                    <div class="label">MEMBER AKTIF</div>
                </div>
                <div class="testimonial-stat">
                    <div class="number">4.9/5</div>
                    <div class="label">RATING RATA-RATA</div>
                </div>
                <div class="testimonial-stat">
                    <div class="number">98%</div>
                    <div class="label">REKOMENDASI</div>
                </div>
            </div>
            <div class="testimonials-grid" id="testimonialsGrid">
                <!-- Testimoni di-generate oleh JavaScript -->
            </div>
        </section>

        <!-- FAQ -->
        <section id="faq" class="section">
            <h2 class="section-title"><i class="fas fa-question-circle"></i> Pertanyaan Umum</h2>
            <p class="section-subtitle">Semua yang perlu Anda ketahui</p>
            <div id="faqContainer">
                <!-- FAQ di-generate oleh JavaScript -->
            </div>
        </section>

        <!-- PLANS -->
        <section id="plans" class="section">
            <h2 class="section-title"><i class="fas fa-crown"></i> Pilih Durasi Akses</h2>
            <p class="section-subtitle">Harga terjangkau dengan kualitas premium</p>
            
            <div class="duration-slider-area">
                <div class="quick-pick">
                    <button onclick="setDays(3)">3 Hari</button>
                    <button onclick="setDays(7)" class="active">7 Hari</button>
                    <button onclick="setDays(14)">14 Hari</button>
                    <button onclick="setDays(30)">30 Hari</button>
                </div>
                <div class="selected-days" id="selectedDaysDisplay">7</div>
                <input type="range" id="durationSlider" min="1" max="30" value="7" oninput="updatePriceAndDays()">
                <div style="margin-top: 10px;">
                    <span class="price-display" id="totalPriceDisplay">Rp 49.000</span>
                    <span style="color: #999; font-size: 0.8rem;">(Rp 7.000/hari)</span>
                </div>
                <div style="margin-top: 20px;">
                    <button class="btn" onclick="mulaiVerifikasi('harian')">
                        <i class="fas fa-shopping-cart"></i> Beli via Admin
                    </button>
                </div>
            </div>

            <div class="permanent-card">
                <h3><i class="fas fa-crown"></i> AKSES PERMANEN</h3>
                <div class="permanent-price">
                    <span class="old-price">Rp 217.000</span>
                    <span class="new-price">Rp 211.000</span>
                </div>
                <div class="discount-badge">
                    <i class="fas fa-fire"></i> DISKON s/d 26 Nov 2026
                </div>
                <div style="margin-top: 20px;">
                    <button class="btn" onclick="mulaiVerifikasi('permanen')">
                        <i class="fas fa-gem"></i> Beli Permanen
                    </button>
                </div>
            </div>
        </section>

        <!-- CONTACT -->
        <section id="contact" class="section">
            <h2 class="section-title"><i class="fas fa-envelope"></i> Hubungi Admin</h2>
            <p class="section-subtitle">Kami siap membantu Anda 24/7</p>
            <div style="text-align: center;">
                <a href="https://t.me/ARKAUSERV2" target="_blank" class="btn">
                    <i class="fab fa-telegram"></i> @ARKAUSERV2
                </a>
            </div>
            <div class="footer-credit">
                <a href="https://t.me/BugVipFazaxBot" target="_blank"><i class="fab fa-telegram"></i> Cek Bot</a>
                <a href="https://t.me/ARKAUSERV2" target="_blank"><i class="fas fa-user"></i> Admin</a>
                <a href="https://t.me/LimitFazxBot" target="_blank"><i class="fas fa-robot"></i> Bot Limit</a>
            </div>
        </section>
    </main>

    <!-- FOOTER -->
    <footer style="display: none; text-align: center; padding: 20px; border-top: 1px solid rgba(37,211,102,0.2); position: relative; z-index: 2; background: rgba(10,10,10,0.8);" id="footer">
        <p style="font-size: 0.75rem; color: #777;">© 2026 Premium Bug WA. All rights reserved.</p>
    </footer>

    <!-- MODALS -->
    <div class="modal-overlay" id="modalLimit">
        <div class="modal-content">
            <h3 style="color: #4AE381; font-size: 1rem;">
                <i class="fas fa-exclamation-triangle" style="color: #f59e0b;"></i> CEK LIMIT TELEGRAM
            </h3>
            <p style="margin-top: 10px; font-size: 0.8rem;">Apakah akun Telegram Anda <strong>terkena LIMIT</strong>?</p>
            <div class="modal-options">
                <button class="modal-btn modal-btn-limit" onclick="pilihLimit(true)">⚠️ YA, Limit</button>
                <button class="modal-btn modal-btn-normal" onclick="pilihLimit(false)">✅ TIDAK</button>
            </div>
            <button class="modal-close" onclick="tutupModal()">✕ Tutup</button>
        </div>
    </div>

    <div class="verify-modal" id="verifyModal">
        <div class="verify-content">
            <h3 style="color: #4AE381; font-size: 1rem;">
                <i class="fas fa-shield-alt"></i> VERIFIKASI ANTI-BOT
            </h3>
            <p style="font-size: 0.8rem; color: #999; margin: 8px 0;">Memastikan Anda manusia (10 detik)</p>
            <div class="verify-progress-container">
                <div class="verify-progress-bar" id="verifyProgressBar"></div>
            </div>
            <div style="font-size: 1.5rem; font-weight: 700; color: #25D366;" id="verifyPercentage">0%</div>
            <div style="font-size: 0.8rem; color: #a8e6c1; margin: 8px 0;" id="verifyStatus">🔄 Memeriksa...</div>
            <div style="font-size: 2rem; color: #22c55e; display: none;" id="verifyCheckmark">✅</div>
        </div>
    </div>

    <!-- SCRIPTS -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdn.jsdelivr.net/gh/jnicol/particleground/jquery.particleground.min.js"></script>
    <script>
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

        // ============ DATA TESTIMONI ============
        const testimonialData = [
            { name: "Rizky", duration: "Member 3 Bulan", text: "Awalnya ragu, tapi setelah coba ternyata bot-nya gacor banget. Aktivasi cepat dan admin-nya responsif. Recommended!" },
            { name: "Dimas", duration: "Member Permanen", text: "Worth it banget! Fiturnya lengkap dan update terus. Udah 6 bulan pakai dan nggak pernah ada masalah." },
            { name: "Andi", duration: "Member 1 Bulan", text: "Pelayanan cepat, bot langsung aktif setelah bayar. Fitur bug detection-nya akurat. Mantap!" },
            { name: "Budi", duration: "Member 2 Bulan", text: "Bot-nya stabil dan jarang error. Support-nya juga fast response. Puas banget!" },
            { name: "Citra", duration: "Member Permanen", text: "Harga terjangkau tapi kualitas premium. Fitur lengkap dan mudah digunakan." },
            { name: "Dewi", duration: "Member 1 Bulan", text: "Baru pertama kali beli dan langsung jatuh cinta. Aktivasi instan, bot langsung jalan." },
            { name: "Eko", duration: "Member 3 Bulan", text: "Sudah coba beberapa bot sejenis, tapi ini yang paling bagus. Fiturnya paling lengkap." },
            { name: "Fajar", duration: "Member 7 Hari", text: "Murah dan berkualitas. Cocok buat yang baru mulai. Admin-nya juga ramah." },
            { name: "Gilang", duration: "Member Permanen", text: "Investasi terbaik! Sekali bayar, selamanya bisa pakai. Fitur terus update." },
            { name: "Hana", duration: "Member 2 Bulan", text: "Bot-nya gampang dipakai, bahkan untuk pemula. Dokumentasi lengkap dan jelas." },
            { name: "Irfan", duration: "Member 1 Bulan", text: "Aktivasi super cepat, nggak sampai 1 menit. Langsung bisa dipakai. Mantap!" },
            { name: "Joko", duration: "Member 14 Hari", text: "Harganya bersaing tapi kualitasnya juara. Nggak nyesel beli di sini." },
            { name: "Kartika", duration: "Member Permanen", text: "Sudah 1 tahun pakai dan nggak pernah kecewa. Fitur terus bertambah." },
            { name: "Lukman", duration: "Member 3 Bulan", text: "Support-nya luar biasa! Pernah ada masalah, langsung dibantu sampai selesai." },
            { name: "Maya", duration: "Member 1 Bulan", text: "Bot-nya ringan dan cepat. Nggak bikin HP lemot. Recommended banget!" },
            { name: "Nanda", duration: "Member 7 Hari", text: "Cocok buat pemula. Mudah dipahami dan langsung bisa dipakai." },
            { name: "Oscar", duration: "Member Permanen", text: "Fitur bug detection-nya paling akurat. Sudah bandingkan dengan yang lain." },
            { name: "Putri", duration: "Member 2 Bulan", text: "Admin-nya fast response. Kapanpun butuh bantuan, selalu siap membantu." },
            { name: "Qori", duration: "Member 1 Bulan", text: "Awalnya coba yang 7 hari, langsung upgrade ke permanen. Worth it!" },
            { name: "Rama", duration: "Member 14 Hari", text: "Bot-nya stabil dan nggak pernah down. Jarang banget nemu yang sebagus ini." },
            { name: "Sari", duration: "Member Permanen", text: "Fitur terus diupdate, nggak pernah merasa rugi. Harga sepadan dengan kualitas." },
            { name: "Tono", duration: "Member 3 Bulan", text: "Sudah rekomendasiin ke teman-teman. Semua puas dengan layanannya." },
            { name: "Umar", duration: "Member 1 Bulan", text: "Mudah dipakai dan hasilnya memuaskan. Nggak perlu pikir panjang lagi." },
            { name: "Vina", duration: "Member 2 Bulan", text: "Bot-nya aman dipakai, nggak ada masalah banned. Tenang pakainya." },
            { name: "Wawan", duration: "Member Permanen", text: "Fitur terlengkap yang pernah saya temui. Nggak perlu cari bot lain lagi." },
            { name: "Yuni", duration: "Member 7 Hari", text: "Murah meriah tapi kualitas premium. Cocok buat yang mau coba-coba dulu." },
            { name: "Zaki", duration: "Member 1 Bulan", text: "Aktivasi instan, support cepat, fitur lengkap. Semua yang saya butuhkan ada di sini." },
            { name: "Alya", duration: "Member 14 Hari", text: "Sangat puas dengan layanannya. Bot-nya gacor dan jarang error." },
            { name: "Bima", duration: "Member Permanen", text: "Sudah 8 bulan pakai. Nggak pernah ada masalah. Update terus setiap bulan." },
            { name: "Cindy", duration: "Member 3 Bulan", text: "Admin-nya sangat membantu. Dijelaskan dengan sabar sampai paham." },
            { name: "Doni", duration: "Member 1 Bulan", text: "Bot-nya user-friendly. Bahkan yang nggak ngerti teknis pun bisa pakai." },
            { name: "Ella", duration: "Member 2 Bulan", text: "Fitur bug detection-nya detail banget. Bisa lihat semua info yang dibutuhkan." },
            { name: "Fikri", duration: "Member Permanen", text: "Nggak nyesel ambil yang permanen. Sekali bayar, selamanya tenang." },
            { name: "Gita", duration: "Member 7 Hari", text: "Cocok buat pemula yang mau belajar. Harganya sangat terjangkau." },
            { name: "Hadi", duration: "Member 1 Bulan", text: "Pelayanan cepat dan ramah. Bot langsung aktif setelah konfirmasi." },
            { name: "Intan", duration: "Member 14 Hari", text: "Aman dan terpercaya. Sudah pakai 2 minggu dan nggak ada masalah." },
            { name: "Jaka", duration: "Member 3 Bulan", text: "Fitur terus bertambah setiap update. Nggak pernah bosan pakainya." },
            { name: "Kiki", duration: "Member Permanen", text: "Bot terbaik yang pernah saya gunakan. Nggak ada tandingannya." },
            { name: "Lina", duration: "Member 1 Bulan", text: "Support 24/7 benar-benar nyata. Pernah chat jam 2 pagi dan dibalas." },
            { name: "Miko", duration: "Member 2 Bulan", text: "Harganya murah tapi fiturnya banyak. Nggak ada alasan buat nggak beli." },
            { name: "Nia", duration: "Member 7 Hari", text: "Baru coba dan langsung suka. Bot-nya ringan dan cepat." },
            { name: "Oki", duration: "Member Permanen", text: "Investasi jangka panjang yang menguntungkan. Fitur terus diupdate." },
            { name: "Prita", duration: "Member 1 Bulan", text: "Admin-nya fast response dan sangat membantu. Recommended!" },
            { name: "Raka", duration: "Member 14 Hari", text: "Bot-nya stabil dan akurat. Nggak pernah dapat info yang salah." },
            { name: "Sinta", duration: "Member 3 Bulan", text: "Sudah rekomendasiin ke banyak teman. Semua puas." },
            { name: "Tomi", duration: "Member Permanen", text: "Fitur paling lengkap dan terus berkembang. Worth every penny!" },
            { name: "Uci", duration: "Member 1 Bulan", text: "Gampang dipakai dan hasilnya memuaskan. Nggak perlu mikir dua kali." },
            { name: "Vito", duration: "Member 2 Bulan", text: "Bot-nya aman dan terpercaya. Nggak perlu khawatir akun kena banned." },
            { name: "Winda", duration: "Member 7 Hari", text: "Harga sangat terjangkau untuk kualitas yang diberikan." },
            { name: "Yoga", duration: "Member Permanen", text: "Sudah pakai setahun lebih. Selalu dapat update terbaru. Mantap!" },
            { name: "Zara", duration: "Member 1 Bulan", text: "Pelayanan terbaik! Admin-nya sabar dan sangat membantu." },
            { name: "Adit", duration: "Member 14 Hari", text: "Bot-nya cepat dan akurat. Nggak ada buffering atau lag." },
            { name: "Bella", duration: "Member 3 Bulan", text: "Fitur lengkap dan mudah dipahami. Cocok untuk semua level." },
            { name: "Candra", duration: "Member Permanen", text: "Nggak nyesel beli permanen. Fitur terus bertambah setiap bulan." },
            { name: "Dina", duration: "Member 1 Bulan", text: "Support-nya luar biasa! Langsung dibantu sampai masalah selesai." },
            { name: "Evan", duration: "Member 2 Bulan", text: "Bot-nya stabil dan jarang maintenance. Nggak pernah kecewa." },
            { name: "Fitri", duration: "Member 7 Hari", text: "Murah dan berkualitas. Cocok buat yang baru mau coba." },
            { name: "Gani", duration: "Member Permanen", text: "Fitur bug detection paling akurat yang pernah saya pakai." },
            { name: "Hesti", duration: "Member 1 Bulan", text: "Aktivasi super cepat. Bayar langsung bisa dipakai. Mantap!" },
            { name: "Imam", duration: "Member 14 Hari", text: "Bot-nya aman dan nggak bikin akun bermasalah." },
            { name: "Jihan", duration: "Member 3 Bulan", text: "Fitur terus diupdate. Nggak pernah merasa bosan pakainya." },
            { name: "Kris", duration: "Member Permanen", text: "Bot terbaik di kelasnya. Nggak ada yang bisa nandingin." },
            { name: "Lala", duration: "Member 1 Bulan", text: "Admin-nya ramah dan fast response. Sangat membantu." },
            { name: "Maman", duration: "Member 2 Bulan", text: "Harganya bersaing tapi kualitasnya juara. Recommended!" },
            { name: "Nina", duration: "Member 7 Hari", text: "Cocok buat pemula. Gampang dipahami dan langsung bisa dipakai." },
            { name: "Omar", duration: "Member Permanen", text: "Investasi terbaik. Fitur terus berkembang dan update." },
            { name: "Putu", duration: "Member 1 Bulan", text: "Bot-nya ringan dan cepat. Nggak bikin HP lemot." },
            { name: "Rani", duration: "Member 14 Hari", text: "Aman dipakai dan hasilnya akurat. Puas banget!" },
            { name: "Surya", duration: "Member 3 Bulan", text: "Fitur paling lengkap yang pernah saya temui." },
            { name: "Tari", duration: "Member Permanen", text: "Nggak perlu cari bot lain lagi. Ini yang terbaik." },
            { name: "Udin", duration: "Member 1 Bulan", text: "Support-nya fast response. Pernah dibantu jam 3 pagi." },
            { name: "Vania", duration: "Member 2 Bulan", text: "Bot-nya stabil dan akurat. Nggak pernah dapat info salah." },
            { name: "Wahyu", duration: "Member 7 Hari", text: "Murah tapi kualitas premium. Nggak nyesel beli." },
            { name: "Yanti", duration: "Member Permanen", text: "Sudah pakai 1 tahun. Selalu puas dengan layanannya." },
            { name: "Zidan", duration: "Member 1 Bulan", text: "Aktivasi instan dan bot langsung aktif. Mantap!" },
            { name: "Ayu", duration: "Member 14 Hari", text: "Bot-nya aman dan nggak bikin akun bermasalah." },
            { name: "Bagas", duration: "Member 3 Bulan", text: "Fitur terus diupdate. Nggak pernah bosan." },
            { name: "Caca", duration: "Member Permanen", text: "Worth it banget! Sekali bayar, selamanya bisa pakai." },
            { name: "Dika", duration: "Member 1 Bulan", text: "Admin-nya sabar dan sangat membantu pemula." },
            { name: "Elsa", duration: "Member 2 Bulan", text: "Bot-nya cepat dan nggak pernah lag. Recommended!" },
            { name: "Fahmi", duration: "Member 7 Hari", text: "Cocok buat yang mau coba dulu. Harganya terjangkau." },
            { name: "Gina", duration: "Member Permanen", text: "Fitur bug detection-nya paling detail dan akurat." },
            { name: "Hendra", duration: "Member 1 Bulan", text: "Pelayanan cepat dan ramah. Bot langsung aktif." },
            { name: "Ika", duration: "Member 14 Hari", text: "Bot-nya stabil dan jarang error. Puas!" },
            { name: "Jamil", duration: "Member 3 Bulan", text: "Sudah rekomendasiin ke banyak teman. Semua puas." },
            { name: "Karin", duration: "Member Permanen", text: "Fitur terlengkap dan terus berkembang." },
            { name: "Lutfi", duration: "Member 1 Bulan", text: "Bot-nya aman dipakai. Nggak perlu khawatir." },
            { name: "Mira", duration: "Member 2 Bulan", text: "Support-nya luar biasa! Selalu siap membantu." },
            { name: "Naufal", duration: "Member 7 Hari", text: "Murah meriah tapi kualitasnya nggak murahan." },
            { name: "Olga", duration: "Member Permanen", text: "Investasi terbaik yang pernah saya lakukan." },
            { name: "Pandu", duration: "Member 1 Bulan", text: "Bot-nya user-friendly. Gampang banget dipakai." },
            { name: "Qonita", duration: "Member 14 Hari", text: "Aman dan terpercaya. Nggak ada masalah sama sekali." },
            { name: "Rian", duration: "Member 3 Bulan", text: "Fitur terus bertambah. Nggak pernah merasa rugi." },
            { name: "Silvi", duration: "Member Permanen", text: "Bot terbaik! Nggak ada yang bisa nandingin." },
            { name: "Taufik", duration: "Member 1 Bulan", text: "Aktivasi super cepat. Bayar langsung aktif." },
            { name: "Ulya", duration: "Member 2 Bulan", text: "Bot-nya stabil dan akurat. Recommended!" },
            { name: "Vino", duration: "Member 7 Hari", text: "Cocok buat pemula. Gampang dipahami." },
            { name: "Wulan", duration: "Member Permanen", text: "Sudah setahun pakai. Selalu puas dengan layanan." }
        ];

        // ============ GENERATE TESTIMONIALS ============
        function generateTestimonials() {
            const grid = document.getElementById('testimonialsGrid');
            let html = '';
            for (let i = 0; i < 100; i++) {
                const data = testimonialData[i % testimonialData.length];
                const randomStar = Math.random() > 0.2 ? '★★★★★' : '★★★★☆';
                html += `
                    <div class="testimonial-card">
                        <div class="testimonial-header">
                            <div class="testimonial-avatar">${data.name.charAt(0)}</div>
                            <div class="testimonial-info">
                                <h5>${data.name} ${i >= testimonialData.length ? '#' + (i + 1) : ''}</h5>
                                <span>${data.duration}</span>
                            </div>
                        </div>
                        <div class="testimonial-stars">${randomStar}</div>
                        <p class="testimonial-text">"${data.text}"</p>
                    </div>
                `;
            }
            grid.innerHTML = html;
        }

        // ============ GENERATE FAQ ============
        function generateFAQ() {
            const faqData = [
                { q: "Bagaimana cara membeli akses?", a: "Klik tombol 'Beli via Admin' atau 'Beli Permanen', lalu Anda akan diarahkan ke Telegram Admin. Setelah pembayaran dikonfirmasi, akses akan langsung diaktifkan." },
                { q: "Berapa lama proses aktivasi?", a: "Proses aktivasi sangat cepat, biasanya kurang dari 1 menit setelah pembayaran dikonfirmasi oleh Admin." },
                { q: "Apakah aman digunakan?", a: "Ya, 100% aman. Bot kami dirancang dengan sistem keamanan terbaik untuk melindungi akun Anda dari banned." },
                { q: "Metode pembayaran apa saja yang tersedia?", a: "Kami menerima pembayaran via Dana, OVO, GoPay, dan transfer bank. Hubungi Admin untuk detail lebih lanjut." },
                { q: "Apakah bisa perpanjang akses?", a: "Tentu bisa! Anda dapat memperpanjang akses kapan saja dengan menghubungi Admin." },
                { q: "Apakah ada garansi?", a: "Ya, jika bot mengalami gangguan dalam masa aktif, kami akan mengganti atau memperpanjang akses Anda secara gratis." },
                { q: "Apakah bot bisa dipakai di semua device?", a: "Ya, bot kami bisa diakses dari HP, tablet, laptop, PC, dan monitor dengan tampilan yang responsif." },
                { q: "Apakah ada diskon untuk pembelian banyak?", a: "Hubungi Admin untuk penawaran khusus jika Anda ingin membeli dalam jumlah banyak." }
            ];
            const container = document.getElementById('faqContainer');
            let html = '';
            faqData.forEach(faq => {
                html += `
                    <div class="faq-item">
                        <div class="faq-question" onclick="toggleFAQ(this)">
                            <span>${faq.q}</span>
                            <i class="fas fa-chevron-down"></i>
                        </div>
                        <div class="faq-answer">
                            <p>${faq.a}</p>
                        </div>
                    </div>
                `;
            });
            container.innerHTML = html;
        }

        // ============ TOGGLE FAQ ============
        function toggleFAQ(element) {
            const answer = element.nextElementSibling;
            element.classList.toggle('active');
            answer.classList.toggle('active');
        }

        // ============ LOADING SCREEN ============
        function startLoading() {
            const loadingScreen = document.getElementById('loadingScreen');
            const progressBar = document.getElementById('loadingProgressBar');
            const percentage = document.getElementById('loadingPercentage');
            const status = document.getElementById('loadingStatus');
            const mainContent = document.getElementById('mainContent');
            const footer = document.getElementById('footer');
            
            let progress = 0;
            const totalDuration = 15000;
            const interval = 100;
            const steps = totalDuration / interval;
            const increment = 100 / steps;
            
            const loadInterval = setInterval(() => {
                progress += increment;
                if (progress >= 100) {
                    progress = 100;
                    clearInterval(loadInterval);
                    status.textContent = '✅ Selesai!';
                    setTimeout(() => {
                        loadingScreen.classList.add('hidden');
                        mainContent.style.display = 'block';
                        footer.style.display = 'block';
                    }, 400);
                }
                progressBar.style.width = progress + '%';
                percentage.textContent = Math.floor(progress) + '%';
                if (progress < 30) status.textContent = '🔄 Menginisialisasi...';
                else if (progress < 60) status.textContent = '📡 Menghubungkan...';
                else if (progress < 85) status.textContent = '⚙️ Memuat komponen...';
                else status.textContent = '🎨 Menyelesaikan...';
            }, interval);
        }

        // ============ VERIFIKASI ============
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
            status.textContent = '🔄 Memeriksa...';
            checkmark.style.display = 'none';
            
            let progress = 0;
            const totalDuration = 10000;
            const interval = 100;
            const steps = totalDuration / interval;
            const increment = 100 / steps;
            
            const verifyInterval = setInterval(() => {
                progress += increment;
                if (progress >= 100) {
                    progress = 100;
                    clearInterval(verifyInterval);
                    status.textContent = '✅ Berhasil!';
                    checkmark.style.display = 'block';
                    setTimeout(() => {
                        verifyModal.classList.remove('active');
                        bukaModalLimit();
                    }, 700);
                }
                progressBar.style.width = progress + '%';
                percentage.textContent = Math.floor(progress) + '%';
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
            const LIMIT_BOT_USERNAME = 'LimitFazxBot';
            const ADMIN_USERNAME = 'ARKAUSERV2';
            if (isLimit) {
                const pesan = pendingPurchaseType === 'harian' 
                    ? `Halo @${LIMIT_BOT_USERNAME}, saya LIMIT. Ingin beli akses ${window.currentSelectedDays || 7} hari.` 
                    : `Halo @${LIMIT_BOT_USERNAME}, saya LIMIT. Ingin beli akses PERMANEN.`;
                window.open(`https://t.me/${LIMIT_BOT_USERNAME}?text=${encodeURIComponent(pesan)}`, '_blank');
            } else {
                const days = window.currentSelectedDays || 7;
                if (pendingPurchaseType === 'harian') {
                    const total = days * 7000;
                    const pesan = `Halo Admin @${ADMIN_USERNAME}, ingin beli akses ${days} hari (Rp ${total.toLocaleString('id-ID')}).`;
                    window.open(`https://t.me/${ADMIN_USERNAME}?text=${encodeURIComponent(pesan)}`, '_blank');
                } else {
                    const pesan = `Halo Admin @${ADMIN_USERNAME}, ingin beli akses PERMANEN (Rp 211.000).`;
                    window.open(`https://t.me/${ADMIN_USERNAME}?text=${encodeURIComponent(pesan)}`, '_blank');
                }
            }
        }

        // ============ HARGA ============
        function updatePriceAndDays() {
            const slider = document.getElementById('durationSlider');
            let days = parseInt(slider.value);
            if (isNaN(days) || days < 1) days = 1;
            if (days > 30) days = 30;
            const total = days * 7000;
            document.getElementById('selectedDaysDisplay').textContent = days;
            document.getElementById('totalPriceDisplay').textContent = 'Rp ' + total.toLocaleString('id-ID');
            window.currentSelectedDays = days;
            document.querySelectorAll('.quick-pick button').forEach(btn => {
                btn.classList.remove('active');
                if (btn.textContent.includes(days + ' ')) btn.classList.add('active');
            });
        }
        function setDays(days) {
            document.getElementById('durationSlider').value = days;
            updatePriceAndDays();
        }

        // ============ INIT ============
        window.addEventListener('load', () => {
            generateTestimonials();
            generateFAQ();
            startLoading();
        });
        window.currentSelectedDays = 7;
        let pendingPurchaseType = 'harian';
    </script>
</body>
</html>
