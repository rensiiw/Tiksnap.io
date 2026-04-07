<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <meta name="theme-color" content="#0a0f0d">
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800;900&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg: #0a0f0d;
            --card: #111916;
            --border: #1e2d27;
            --text: #f0f5f2;
            --text-muted: #6b8f7d;
            --accent: #10b981;
            --accent-light: #34d399;
            --gold: #d4af37;
            --gold-light: #f4d03f;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Outfit', sans-serif;
            background: var(--bg);
            color: var(--text);
            min-height: 100vh;
            overflow-x: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* Background Effects */
        .bg-grid {
            position: fixed;
            inset: 0;
            background-image: 
                linear-gradient(rgba(16, 185, 129, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(16, 185, 129, 0.03) 1px, transparent 1px);
            background-size: 60px 60px;
            z-index: 0;
        }

        .bg-glow {
            position: fixed;
            width: 600px;
            height: 600px;
            border-radius: 50%;
            filter: blur(150px);
            opacity: 0.4;
            z-index: 0;
            animation: floatGlow 20s ease-in-out infinite;
        }

        .glow-1 {
            background: linear-gradient(135deg, var(--accent), var(--gold));
            top: -200px;
            right: -200px;
        }

        .glow-2 {
            background: var(--accent);
            bottom: -300px;
            left: -200px;
            animation-delay: -10s;
        }

        @keyframes floatGlow {
            0%, 100% { transform: translate(0, 0) scale(1); }
            50% { transform: translate(50px, -30px) scale(1.1); }
        }

        /* Particles */
        .particles {
            position: fixed;
            inset: 0;
            z-index: 1;
            pointer-events: none;
        }

        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: var(--accent);
            border-radius: 50%;
            opacity: 0;
            animation: particleFloat 8s ease-in-out infinite;
        }

        @keyframes particleFloat {
            0% { opacity: 0; transform: translateY(100vh) scale(0); }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { opacity: 0; transform: translateY(-100px) scale(1); }
        }

        /* Main Container */
        .container {
            position: relative;
            z-index: 10;
            text-align: center;
            padding: 20px;
            max-width: 600px;
        }

        /* Logo */
        .logo {
            width: 100px;
            height: 100px;
            background: linear-gradient(135deg, var(--accent), var(--gold));
            border-radius: 28px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 30px;
            box-shadow: 0 20px 60px -15px rgba(16, 185, 129, 0.5);
            animation: logoPulse 3s ease-in-out infinite;
        }

        @keyframes logoPulse {
            0%, 100% { transform: scale(1); box-shadow: 0 20px 60px -15px rgba(16, 185, 129, 0.5); }
            50% { transform: scale(1.05); box-shadow: 0 25px 70px -15px rgba(16, 185, 129, 0.7); }
        }

        .logo svg {
            width: 50px;
            height: 50px;
        }

        /* Title */
        .title {
            font-size: 3rem;
            font-weight: 900;
            margin-bottom: 10px;
            background: linear-gradient(135deg, var(--text), var(--accent-light));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .subtitle {
            font-size: 1.1rem;
            color: var(--text-muted);
            margin-bottom: 40px;
        }

        /* Status Badge */
        .status-badge {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: rgba(212, 175, 55, 0.1);
            border: 1px solid rgba(212, 175, 55, 0.3);
            padding: 12px 24px;
            border-radius: 50px;
            margin-bottom: 40px;
            font-weight: 600;
            color: var(--gold);
        }

        .status-dot {
            width: 10px;
            height: 10px;
            background: var(--gold);
            border-radius: 50%;
            animation: blink 1.5s ease-in-out infinite;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }

        /* Card */
        .card {
            background: linear-gradient(165deg, rgba(17, 25, 22, 0.9), rgba(13, 20, 17, 0.95));
            border: 1px solid var(--border);
            border-radius: 24px;
            padding: 40px 30px;
            backdrop-filter: blur(20px);
            box-shadow: 0 40px 80px -20px rgba(0, 0, 0, 0.5);
        }

        /* Message */
        .message-title {
            font-size: 1.3rem;
            font-weight: 700;
            margin-bottom: 20px;
            color: var(--accent-light);
        }

        .message-text {
            color: var(--text-muted);
            line-height: 1.8;
            margin-bottom: 30px;
        }

        /* Progress */
        .progress-container {
            background: var(--bg);
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 30px;
        }

        .progress-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 12px;
            font-size: 0.9rem;
        }

        .progress-bar {
            height: 8px;
            background: var(--border);
            border-radius: 4px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, var(--accent), var(--gold));
            border-radius: 4px;
            animation: progressAnim 3s ease-out forwards;
        }

        @keyframes progressAnim {
            0% { width: 0%; }
            100% { width: 75%; }
        }

        /* Feature List */
        .features {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
            margin-bottom: 30px;
        }

        .feature-item {
            background: var(--bg);
            border: 1px solid var(--border);
            border-radius: 14px;
            padding: 15px 10px;
            transition: all 0.3s ease;
        }

        .feature-item:hover {
            border-color: var(--accent);
            transform: translateY(-3px);
        }

        .feature-icon {
            font-size: 1.5rem;
            margin-bottom: 8px;
        }

        .feature-text {
            font-size: 0.75rem;
            color: var(--text-muted);
            font-weight: 500;
        }

        /* Admin Section */
        .admin-section {
            border-top: 1px solid var(--border);
            padding-top: 25px;
            margin-top: 10px;
        }

        .admin-label {
            font-size: 0.8rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 15px;
        }

        .admin-card {
            display: inline-flex;
            align-items: center;
            gap: 15px;
            background: linear-gradient(135deg, rgba(16, 185, 129, 0.1), rgba(212, 175, 55, 0.1));
            border: 1px solid var(--border);
            border-radius: 16px;
            padding: 15px 25px;
        }

        .admin-avatar {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, var(--accent), var(--gold));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1.1rem;
        }

        .admin-info {
            text-align: left;
        }

        .admin-name {
            font-weight: 700;
            font-size: 1rem;
        }

        .admin-role {
            font-size: 0.8rem;
            color: var(--text-muted);
        }

        /* Footer */
        .footer {
            margin-top: 40px;
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        .footer a {
            color: var(--accent);
            text-decoration: none;
            font-weight: 600;
        }

        .footer a:hover {
            text-decoration: underline;
        }

        /* Responsive */
        @media (max-width: 640px) {
            .title { font-size: 2rem; }
            .features { grid-template-columns: 1fr; }
            .card { padding: 30px 20px; }
        }

        /* Typing Animation */
        .typing-text {
            border-right: 2px solid var(--accent);
            animation: cursorBlink 0.8s step-end infinite;
            padding-right: 5px;
        }

        @keyframes cursorBlink {
            0%, 100% { border-color: var(--accent); }
            50% { border-color: transparent; }
        }
    </style>
</head>
<body>
    <!-- Background Effects -->
    <div class="bg-grid"></div>
    <div class="bg-glow glow-1"></div>
    <div class="bg-glow glow-2"></div>
    
    <!-- Particles -->
    <div class="particles" id="particles"></div>

    <!-- Main Content -->
    <div class="container">
        <!-- Logo -->
        <div class="logo">
            <svg viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2.5">
                <polygon points="5 3 19 12 5 21 5 3"></polygon>
            </svg>
        </div>

        <!-- Title -->
        <h1 class="title">TikSnap.io</h1>
        <p class="subtitle">TikTok Video, Sound & Photo Downloader</p>

        <!-- Status Badge -->
        <div class="status-badge">
            <span class="status-dot"></span>
            <span>SEDANG DALAM PERBAIKAN</span>
        </div>

        <!-- Main Card -->
        <div class="card">
            <h2 class="message-title">Pengumuman dari Admin</h2>
            
            <p class="message-text">
                Kepada seluruh pengguna <strong>TikSnap.io</strong> yang terhormat,<br><br>
                Website saat ini sedang mengalami <strong style="color: var(--gold);">kendala teknis</strong> dan berada dalam proses pemeliharaan. Tim kami sedang bekerja keras untuk memperbaiki sistem.
            </p>

            <!-- Progress -->
            <div class="progress-container">
                <div class="progress-label">
                    <span>Progress Perbaikan</span>
                    <span id="progressPercent">75%</span>
                </div>
                <div class="progress-bar">
                    <div class="progress-fill"></div>
                </div>
            </div>

            <!-- Features Being Fixed -->
            <div class="features">
                <div class="feature-item">
                    <div class="feature-icon">🔧</div>
                    <div class="feature-text">Server</div>
                </div>
                <div class="feature-item">
                    <div class="feature-icon">🔐</div>
                    <div class="feature-text">Keamanan</div>
                </div>
                <div class="feature-item">
                    <div class="feature-icon">⚡</div>
                    <div class="feature-text">API</div>
                </div>
            </div>

            <!-- Admin Section -->
            <div class="admin-section">
                <p class="admin-label">Disampaikan oleh</p>
                <div class="admin-card">
                    <div class="admin-avatar">Z&F</div>
                    <div class="admin-info">
                        <p class="admin-name">Admin TikSnap.io</p>
                        <p class="admin-role">Development Team - ZAI & FRENDY</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Footer -->
        <div class="footer">
            <p>Hubungi kami: <a href="https://github.com/rensiiw" target="_blank">@rensiiw</a></p>
            <p style="margin-top: 10px;">© 2024 TikSnap.io - All Rights Reserved</p>
        </div>
    </div>

    <script>
        // Create Particles
        function createParticles() {
            const container = document.getElementById('particles');
            const particleCount = 30;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 8 + 's';
                particle.style.animationDuration = (Math.random() * 4 + 6) + 's';
                
                // Random colors
                const colors = ['#10b981', '#d4af37', '#14b8a6'];
                particle.style.background = colors[Math.floor(Math.random() * colors.length)];
                particle.style.width = (Math.random() * 4 + 2) + 'px';
                particle.style.height = particle.style.width;
                
                container.appendChild(particle);
            }
        }

        // Typing Effect
        function typeWriter(element, text, speed = 50) {
            let i = 0;
            element.innerHTML = '';
            function type() {
                if (i < text.length) {
                    element.innerHTML += text.charAt(i);
                    i++;
                    setTimeout(type, speed);
                }
            }
            type();
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            createParticles();
            
            // Animate progress number
            const progressEl = document.getElementById('progressPercent');
            let progress = 0;
            const interval = setInterval(() => {
                progress += 1;
                if (progress >= 75) {
                    clearInterval(interval);
                    progress = 75;
                }
                progressEl.textContent = progress + '%';
            }, 30);
        });
    </script>
</body>
</html>
