<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>TikSnap.io - Maintenance</title>
    <meta name="theme-color" content="#0a0f0d">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg: #0a0f0d;
            --bg-card: #0d1411;
            --border: #1e2d27;
            --text: #f0f5f2;
            --text-muted: #7a9a8a;
            --accent: #10b981;
            --accent-light: #34d399;
            --gold: #d4af37;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: 'Outfit', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--bg);
            color: var(--text);
            min-height: 100vh;
            min-height: 100dvh; /* Dynamic viewport height for mobile */
            overflow-x: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 16px;
        }

        /* Background Grid */
        .bg-grid {
            position: fixed;
            inset: 0;
            background-image: 
                linear-gradient(rgba(16, 185, 129, 0.04) 1px, transparent 1px),
                linear-gradient(90deg, rgba(16, 185, 129, 0.04) 1px, transparent 1px);
            background-size: 40px 40px;
            z-index: 0;
            mask-image: radial-gradient(circle at 50% 50%, black 30%, transparent 80%);
        }

        /* Glows - Positioned to look good on mobile */
        .bg-glow {
            position: fixed;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.3;
            z-index: 0;
            pointer-events: none;
        }
        .glow-1 {
            width: 300px;
            height: 300px;
            background: var(--accent);
            top: -100px;
            right: -50px;
        }
        .glow-2 {
            width: 250px;
            height: 250px;
            background: var(--gold);
            bottom: -50px;
            left: -50px;
        }

        /* Particles Container */
        .particles { position: fixed; inset: 0; z-index: 1; pointer-events: none; overflow: hidden; }
        .particle {
            position: absolute;
            background: var(--accent);
            border-radius: 50%;
            opacity: 0;
            animation: floatUp 10s linear infinite;
        }
        @keyframes floatUp {
            0% { transform: translateY(100vh) scale(0); opacity: 0; }
            20% { opacity: 0.8; }
            100% { transform: translateY(-20px) scale(1); opacity: 0; }
        }

        /* Main Container */
        .container {
            position: relative;
            z-index: 10;
            width: 100%;
            max-width: 400px;
        }

        /* Header */
        .header {
            text-align: center;
            margin-bottom: 20px;
        }

        .logo {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, var(--accent), var(--gold));
            border-radius: 22px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 16px;
            box-shadow: 0 10px 30px -5px rgba(16, 185, 129, 0.4);
            animation: logoFloat 4s ease-in-out infinite;
        }
        @keyframes logoFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }
        .logo svg { width: 36px; height: 36px; stroke: white; stroke-width: 2.5; }

        .title {
            font-size: 1.8rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--text) 0%, var(--accent-light) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            line-height: 1.2;
        }

        .subtitle {
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-top: 4px;
        }

        /* Status Badge */
        .status-badge {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background: rgba(212, 175, 55, 0.1);
            border: 1px solid rgba(212, 175, 55, 0.2);
            padding: 8px 16px;
            border-radius: 100px;
            margin-top: 14px;
            font-size: 0.75rem;
            font-weight: 600;
            color: var(--gold-light);
        }
        .status-dot {
            width: 8px;
            height: 8px;
            background: var(--gold);
            border-radius: 50%;
            animation: pulse 1.5s ease-in-out infinite;
            box-shadow: 0 0 0 0 rgba(212, 175, 55, 0.4);
        }
        @keyframes pulse {
            0%, 100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(212, 175, 55, 0.4); }
            50% { transform: scale(1.2); box-shadow: 0 0 0 4px rgba(212, 175, 55, 0); }
        }

        /* Card */
        .card {
            background: linear-gradient(180deg, rgba(17, 25, 22, 0.95), rgba(10, 15, 13, 0.98));
            border: 1px solid var(--border);
            border-radius: 24px;
            padding: 24px 20px;
            backdrop-filter: blur(10px);
            box-shadow: 0 20px 50px -10px rgba(0, 0, 0, 0.5);
        }

        /* Message Content */
        .message-header {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 16px;
            padding-bottom: 12px;
            border-bottom: 1px solid var(--border);
        }
        .message-icon {
            width: 36px;
            height: 36px;
            background: rgba(16, 185, 129, 0.1);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
        }
        .message-title {
            font-size: 1rem;
            font-weight: 700;
            color: var(--accent-light);
        }

        .message-text {
            font-size: 0.9rem;
            color: var(--text-muted);
            line-height: 1.6;
            margin-bottom: 20px;
        }
        .message-text strong { color: var(--text); }
        .highlight { color: var(--gold); font-weight: 600; }

        /* Progress Bar */
        .progress-box {
            background: var(--bg);
            border-radius: 12px;
            padding: 14px;
            margin-bottom: 20px;
        }
        .progress-top {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            font-size: 0.8rem;
            font-weight: 500;
        }
        .progress-track {
            height: 6px;
            background: var(--border);
            border-radius: 10px;
            overflow: hidden;
        }
        .progress-fill {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, var(--accent), var(--gold));
            border-radius: 10px;
            animation: loadProgress 2.5s ease-out forwards;
        }
        @keyframes loadProgress { to { width: 75%; } }

        /* Features List (Stacked Vertically for Mobile) */
        .features-list {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-bottom: 20px;
        }
        .feature-item {
            display: flex;
            align-items: center;
            gap: 12px;
            background: var(--bg);
            padding: 12px;
            border-radius: 12px;
            border: 1px solid var(--border);
        }
        .feature-icon {
            width: 32px;
            height: 32px;
            background: linear-gradient(135deg, rgba(16, 185, 129, 0.1), rgba(212, 175, 55, 0.1));
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1rem;
            flex-shrink: 0;
        }
        .feature-text {
            font-size: 0.85rem;
            font-weight: 500;
        }
        .feature-status {
            margin-left: auto;
            font-size: 0.7rem;
            color: var(--gold);
            background: rgba(212, 175, 55, 0.1);
            padding: 4px 8px;
            border-radius: 6px;
        }

        /* Admin Card */
        .admin-box {
            background: linear-gradient(135deg, rgba(16, 185, 129, 0.05), rgba(212, 175, 55, 0.05));
            border: 1px solid var(--border);
            border-radius: 16px;
            padding: 14px;
            text-align: center;
        }
        .admin-label {
            font-size: 0.7rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 10px;
        }
        .admin-profile {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
        }
        .admin-avatar {
            width: 42px;
            height: 42px;
            background: linear-gradient(135deg, var(--accent), var(--gold));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 0.9rem;
            box-shadow: 0 4px 15px -3px rgba(16, 185, 129, 0.3);
        }
        .admin-info { text-align: left; }
        .admin-name { font-weight: 700; font-size: 0.9rem; line-height: 1.2; }
        .admin-role { font-size: 0.7rem; color: var(--text-muted); }

        /* Footer */
        .footer {
            text-align: center;
            margin-top: 20px;
            font-size: 0.75rem;
            color: var(--text-muted);
        }
        .footer a {
            color: var(--accent);
            text-decoration: none;
            font-weight: 600;
        }

        /* Desktop Optimization */
        @media (min-width: 768px) {
            .logo { width: 90px; height: 90px; margin-bottom: 20px; }
            .title { font-size: 2.5rem; }
            .subtitle { font-size: 1rem; }
            .card { padding: 30px; }
            .features-list { flex-direction: row; }
            .feature-item { flex-direction: column; text-align: center; justify-content: center; }
            .feature-status { margin-left: 0; margin-top: 5px; }
        }
    </style>
</head>
<body>
    <div class="bg-grid"></div>
    <div class="bg-glow glow-1"></div>
    <div class="bg-glow glow-2"></div>
    <div class="particles" id="particles"></div>

    <div class="container">
        <!-- Header -->
        <div class="header">
            <div class="logo">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor">
                    <polygon points="5 3 19 12 5 21 5 3"></polygon>
                </svg>
            </div>
            <h1 class="title">TikSnap.io</h1>
            <p class="subtitle">TikTok Downloader</p>
            <div class="status-badge">
                <span class="status-dot"></span>
                SEDANG PERBAIKAN
            </div>
        </div>

        <!-- Main Card -->
        <div class="card">
            <div class="message-header">
                <div class="message-icon">📢</div>
                <div class="message-title">Pengumuman Admin</div>
            </div>

            <p class="message-text">
                Website sedang mengalami <span class="highlight">kendala teknis</span>. Tim kami sedang bekerja untuk memperbaikinya secepat mungkin.
            </p>

            <!-- Progress -->
            <div class="progress-box">
                <div class="progress-top">
                    <span>Progress Perbaikan</span>
                    <span id="progressNum">75%</span>
                </div>
                <div class="progress-track">
                    <div class="progress-fill"></div>
                </div>
            </div>

            <!-- Features Status -->
            <div class="features-list">
                <div class="feature-item">
                    <div class="feature-icon">🔧</div>
                    <div class="feature-text">Server</div>
                    <span class="feature-status">Proses</span>
                </div>
                <div class="feature-item">
                    <div class="feature-icon">🔐</div>
                    <div class="feature-text">Keamanan</div>
                    <span class="feature-status">Proses</span>
                </div>
                <div class="feature-item">
                    <div class="feature-icon">⚡</div>
                    <div class="feature-text">API</div>
                    <span class="feature-status">Proses</span>
                </div>
            </div>

            <!-- Admin -->
            <div class="admin-box">
                <p class="admin-label">Disampaikan oleh</p>
                <div class="admin-profile">
                    <div class="admin-avatar">Z&F</div>
                    <div class="admin-info">
                        <p class="admin-name">Admin TikSnap</p>
                        <p class="admin-role">ZAI & FRENDY</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="footer">
            <a href="https://github.com/rensiiw" target="_blank">@rensiiw</a> • © 2024 TikSnap.io
        </div>
    </div>

    <script>
        // Mobile-Optimized Particles
        const particlesContainer = document.getElementById('particles');
        const particleCount = window.innerWidth < 768 ? 15 : 25;

        for (let i = 0; i < particleCount; i++) {
            const p = document.createElement('div');
            p.className = 'particle';
            const size = Math.random() * 3 + 1;
            p.style.width = `${size}px`;
            p.style.height = `${size}px`;
            p.style.left = `${Math.random() * 100}%`;
            p.style.animationDelay = `${Math.random() * 10}s`;
            p.style.background = Math.random() > 0.5 ? '#10b981' : '#d4af37';
            particlesContainer.appendChild(p);
        }

        // Animate Progress Number
        let p = 0;
        const el = document.getElementById('progressNum');
        const timer = setInterval(() => {
            p += 1;
            if(p >= 75) clearInterval(timer);
            el.textContent = p + '%';
        }, 25);
    </script>
</body>
</html>
