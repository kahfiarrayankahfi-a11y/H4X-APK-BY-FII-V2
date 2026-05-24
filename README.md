<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Personal Portfolio - FII`X!TERZ H4X</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* ROOT VARIABLES ACCORDING TO TIKTOK DESIGN */
        :root {
            --bg-color: #0b0b0b;
            --card-bg: #111111;
            --primary-color: #ff2a2a; /* Merah Neon */
            --text-main: #ffffff;
            --text-muted: #8e8e8e;
            --border-color: #1f1f1f;
            --success-color: #00ff66;
        }

        /* RESET STYLES */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color) !important;
            color: var(--text-main) !important;
            overflow-x: hidden;
            text-align: left !important;
        }

        /* LOGIN GATE SCREEN */
        #loginGate {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background-color: var(--bg-color);
            z-index: 9999;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            transition: opacity 0.5s ease, transform 0.5s ease;
        }

        .login-box {
            width: 100%;
            max-width: 400px;
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 40px 30px;
            text-align: center;
            box-shadow: 0 0 30px rgba(255, 42, 42, 0.1);
        }

        .login-box h2 {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 5px;
            letter-spacing: 1px;
        }

        .login-box h2 span {
            color: var(--primary-color);
            text-shadow: 0 0 10px rgba(255, 42, 42, 0.5);
        }

        .login-box p {
            font-size: 12px;
            color: var(--text-muted);
            margin-bottom: 30px;
        }

        .login-error {
            color: var(--primary-color);
            font-size: 12px;
            margin-bottom: 15px;
            display: none;
            font-weight: 500;
        }

        /* MAIN CONTENT (HIDDEN UNTIL LOGIN) */
        #mainContent {
            display: none;
            opacity: 0;
            transition: opacity 0.5s ease;
        }

        /* GLOBAL HEADINGS */
        .section-title {
            font-size: 36px;
            font-weight: 700;
            text-align: center;
            margin-bottom: 10px;
        }
        .section-title span {
            color: var(--primary-color);
        }
        .section-subtitle {
            color: var(--text-muted);
            text-align: center;
            font-size: 14px;
            margin-bottom: 50px;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        /* NAVBAR */
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 25px 8%;
            background-color: rgba(11, 11, 11, 0.85);
            backdrop-filter: blur(10px);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid var(--border-color);
        }

        .logo {
            font-size: 22px;
            font-weight: 700;
            letter-spacing: 0.5px;
        }

        .logo span {
            color: var(--primary-color);
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-muted);
            margin-left: 30px;
            font-size: 13px;
            font-weight: 600;
            letter-spacing: 1px;
            transition: 0.3s;
            cursor: pointer;
        }

        .nav-links a:hover, .nav-links a.active {
            color: var(--primary-color);
        }

        /* HERO SECTION */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 150px 8% 80px 8%;
            gap: 50px;
        }

        .hero-content {
            flex: 1;
            max-width: 600px;
        }

        .sub-title {
            color: var(--text-muted);
            font-size: 15px;
            margin-bottom: 8px;
            letter-spacing: 1.5px;
        }

        .hero-content h1 {
            font-size: 46px;
            font-weight: 700;
            line-height: 1.2;
            margin-bottom: 20px;
        }

        .hero-content h1 span {
            color: var(--primary-color);
            text-shadow: 0 0 10px rgba(255, 42, 42, 0.2);
        }

        .description {
            color: var(--text-muted);
            font-size: 14px;
            line-height: 1.6;
            margin-bottom: 40px;
        }

        /* STATS COUNTER */
        .stats-container {
            display: flex;
            gap: 20px;
            margin-bottom: 40px;
        }

        .stat-box {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 15px 20px;
            text-align: center;
            min-width: 110px;
            flex: 1;
        }

        .stat-box h2 {
            color: var(--primary-color);
            font-size: 26px;
            font-weight: 700;
        }

        .stat-box p {
            color: var(--text-muted);
            font-size: 11px;
            margin-top: 4px;
        }

        /* BUTTONS */
        .cta-buttons {
            display: flex;
            gap: 15px;
            margin-bottom: 40px;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 11px 26px;
            border-radius: 30px;
            text-decoration: none;
            font-size: 13px;
            font-weight: 600;
            transition: 0.3s;
        }

        .btn-primary {
            background-color: var(--primary-color);
            color: var(--text-main);
            box-shadow: 0 4px 12px rgba(255, 42, 42, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 18px rgba(255, 42, 42, 0.5);
        }

        .btn-secondary {
            background-color: transparent;
            color: var(--text-main);
            border: 1px solid #333;
        }

        .btn-secondary:hover {
            border-color: var(--text-main);
            transform: translateY(-2px);
        }

        /* SOCIAL ICONS */
        .social-icons {
            display: flex;
            gap: 20px;
        }

        .social-icons a {
            color: var(--text-muted);
            font-size: 20px;
            transition: 0.3s;
        }

        .social-icons a:hover {
            color: var(--primary-color);
            transform: scale(1.15);
        }

        /* FEATURES SECTION (MULTI-PAGE DASHBOARD DESIGN) */
        .features-section {
            padding: 100px 8%;
            background-color: var(--bg-color);
            border-top: 1px solid var(--border-color);
        }

        .cheat-panel {
            max-width: 800px;
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            margin: 0 auto;
            padding: 0;
            display: flex;
            overflow: hidden;
            box-shadow: 0 10px 40px rgba(255, 42, 42, 0.05);
            min-height: 480px;
        }

        /* Panel Sidebar Menu Navigation */
        .panel-sidebar {
            width: 220px;
            background-color: #0d0d0d;
            border-right: 1px solid var(--border-color);
            padding: 20px 10px;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .sidebar-title {
            font-size: 11px;
            font-weight: 700;
            color: var(--primary-color);
            letter-spacing: 2px;
            padding-left: 15px;
            margin-bottom: 15px;
            text-transform: uppercase;
        }

        .tab-btn {
            background: transparent;
            border: none;
            color: var(--text-muted);
            padding: 12px 15px;
            text-align: left;
            font-size: 13px;
            font-weight: 500;
            border-radius: 8px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 12px;
            transition: 0.3s;
        }

        .tab-btn i {
            font-size: 14px;
            width: 20px;
        }

        .tab-btn:hover {
            color: var(--text-main);
            background-color: #161616;
        }

        .tab-btn.active-tab {
            color: var(--text-main);
            background-color: rgba(255, 42, 42, 0.1);
            border: 1px solid rgba(255, 42, 42, 0.2);
            font-weight: 600;
        }

        /* Panel Content Area Screen */
        .panel-body {
            flex: 1;
            padding: 30px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            background-color: var(--card-bg);
        }

        .panel-header-sub {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 15px;
            margin-bottom: 25px;
        }

        /* Tab Content Pages (Hidden Default) */
        .tab-page {
            display: none;
            animation: fadeInPage 0.4s ease-in-out forwards;
        }

        .tab-page.active-page {
            display: block;
        }

        @keyframes fadeInPage {
            from { opacity: 0; transform: translateY(5px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .page-headline {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .page-headline i {
            color: var(--primary-color);
        }

        .page-desc {
            font-size: 12.5px;
            color: var(--text-muted);
            line-height: 1.6;
            margin-bottom: 25px;
        }

        /* Inner Content Row Design */
        .action-container {
            background-color: #070707;
            border: 1px solid var(--border-color);
            padding: 20px;
            border-radius: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 10px;
        }

        .action-detail h4 {
            font-size: 13.5px;
            font-weight: 600;
        }
        .action-detail p {
            font-size: 11px;
            color: var(--text-muted);
            margin-top: 2px;
        }

        /* CUSTOM TOGGLE SWITCH STYLE */
        .switch {
            position: relative;
            display: inline-block;
            width: 46px;
            height: 24px;
        }

        .switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #222;
            transition: .3s;
            border-radius: 24px;
            border: 1px solid #333;
        }

        .slider:before {
            position: absolute;
            content: "";
            height: 16px;
            width: 16px;
            left: 3px;
            bottom: 3px;
            background-color: var(--text-muted);
            transition: .3s;
            border-radius: 50%;
        }

        input:checked + .slider {
            background-color: rgba(255, 42, 42, 0.2);
            border-color: var(--primary-color);
        }

        input:checked + .slider:before {
            transform: translateX(22px);
            background-color: var(--primary-color);
            box-shadow: 0 0 8px var(--primary-color);
        }

        /* Console Output Mockup */
        .console-box {
            background-color: #060606;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 12px 15px;
            font-family: 'Courier New', Courier, monospace;
            font-size: 11px;
            color: #4a4a4a;
            max-height: 85px;
            overflow-y: auto;
            margin-top: 20px;
            text-align: left;
        }

        .console-box span {
            color: var(--primary-color);
        }

        .panel-status {
            font-size: 11px;
            background-color: rgba(0, 255, 102, 0.1);
            color: var(--success-color);
            padding: 3px 10px;
            border-radius: 20px;
            border: 1px solid rgba(0, 255, 102, 0.2);
            font-weight: bold;
        }

        /* SKILL SECTION */
        .skill-section {
            padding: 100px 8%;
            background-color: var(--card-bg);
            border-top: 1px solid var(--border-color);
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            max-width: 1000px;
            margin: 0 auto;
        }

        .skill-card {
            background-color: var(--bg-color);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 25px 20px;
            display: flex;
            align-items: center;
            gap: 15px;
            transition: 0.3s ease;
        }

        .skill-card:hover {
            border-color: var(--primary-color);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(255, 42, 42, 0.05);
        }

        .skill-card i {
            font-size: 28px;
            color: var(--text-muted);
            transition: 0.3s;
        }
        
        .skill-card:hover .fa-html5 { color: #e34f26; }
        .skill-card:hover .fa-css3-alt { color: #1572b6; }
        .skill-card:hover .fa-js { color: #f7df1e; }
        .skill-card:hover .fa-wordpress { color: #21759b; }
        .skill-card:hover .fa-elementor { color: #92003b; }
        .skill-card:hover .fa-python { color: #3776ab; }

        .skill-info h3 {
            font-size: 15px;
            font-weight: 600;
            color: var(--text-main);
        }

        /* CONTACT SECTION */
        .contact-section {
            padding: 100px 8%;
            background-color: var(--bg-color);
            border-top: 1px solid var(--border-color);
        }

        .contact-container {
            display: flex;
            max-width: 1000px;
            margin: 0 auto;
            gap: 50px;
            align-items: flex-start;
        }

        .contact-info {
            flex: 1;
        }

        .contact-info h2 {
            font-size: 32px;
            font-weight: 700;
            margin-bottom: 15px;
        }

        .contact-info h2 span {
            color: var(--primary-color);
        }

        .contact-info p {
            color: var(--text-muted);
            font-size: 13.5px;
            line-height: 1.6;
            margin-bottom: 30px;
        }

        .contact-card {
            background-color: #121212;
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 15px 20px;
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 15px;
            text-decoration: none;
            transition: 0.3s;
        }

        .contact-card:hover {
            border-color: var(--primary-color);
            background-color: #161616;
        }

        .contact-icon {
            width: 40px;
            height: 40px;
            background-color: rgba(255, 42, 42, 0.1);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .contact-icon i {
            color: var(--primary-color);
            font-size: 18px;
        }

        .contact-text h4 {
            font-size: 14px;
            font-weight: 600;
            color: var(--text-main);
        }

        .contact-text p {
            font-size: 11px;
            color: var(--text-muted);
            margin-bottom: 0;
        }

        /* FORM COMPONENT */
        .contact-form-container {
            flex: 1;
            width: 100%;
        }

        .contact-form-container h3 {
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 25px;
        }

        .contact-form-container h3 span {
            color: var(--primary-color);
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-control {
            width: 100%;
            background-color: #121212;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 14px 18px;
            color: var(--text-main);
            font-size: 13px;
            outline: none;
            transition: 0.3s;
        }

        .form-control:focus {
            border-color: var(--primary-color);
        }

        textarea.form-control {
            resize: none;
            min-height: 120px;
        }

        .btn-submit {
            width: 100%;
            background-color: var(--primary-color);
            color: var(--text-main);
            border: none;
            border-radius: 8px;
            padding: 14px;
            font-size: 13px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 4px 12px rgba(255, 42, 42, 0.2);
        }

        .btn-submit:hover {
            background-color: #e02222;
            box-shadow: 0 6px 18px rgba(255, 42, 42, 0.4);
        }

        /* RESPONSIVE DESIGN */
        @media (max-width: 968px) {
            .navbar { padding: 20px 5%; }
            .nav-links { display: none; }
            .hero {
                flex-direction: column;
                text-align: center;
                padding-top: 130px;
            }
            .hero-content h1, .description { text-align: center; }
            .stats-container, .cta-buttons, .social-icons { justify-content: center; }
            .contact-container { flex-direction: column; gap: 40px; }
            .skills-grid { grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); }
            
            /* Cheat Panel Responsive Stack */
            .cheat-panel { flex-direction: column; min-height: auto; }
            .panel-sidebar { width: 100%; border-right: none; border-bottom: 1px solid var(--border-color); flex-direction: row; overflow-x: auto; padding: 15px 10px; }
            .sidebar-title { display: none; }
            .tab-btn { white-space: nowrap; padding: 8px 14px; font-size: 12px; }
        }
    </style>
</head>
<body>

    <div id="loginGate">
        <div class="login-box">
            <h2><span>FII`X!TERZ</span> SYSTEM</h2>
            <p>Masukkan Kredensial untuk Mengakses Panel Utama</p>
            
            <div class="login-error" id="loginError">Username atau Password Salah!</div>
            
            <div>
                <div class="form-group">
                    <input type="text" id="usernameInput" class="form-control" placeholder="Username" autocomplete="off">
                </div>
                <div class="form-group">
                    <input type="password" id="passwordInput" class="form-control" placeholder="Password">
                </div>
                <button type="button" class="btn-submit" onclick="handleLogin()" style="margin-top: 10px;">LOGIN SYSTEM</button>
            </div>
        </div>
    </div>

    <div id="mainContent">
        <header class="navbar">
            <div class="logo">FII`X!TERZ<span>.</span></div>
            <nav class="nav-links">
                <a href="#home" class="active">HOME</a>
                <a href="#features">FEATURES</a> 
                <a href="#skill">SKILL</a>
                <a href="#contact">CONTACT</a>
            </nav>
        </header>

        <section class="hero" id="home">
            <div class="hero-content">
                <p class="sub-title">Welcome</p>
                <h1>Hello Everyone I'm <span>FII`X!TERZ</span></h1>
                <p class="description">
                    I am a web developer focused on building modern, responsive, and efficient websites. 
                    With a growing expertise in HTML, CSS, and JavaScript.
                </p>

                <div class="stats-container">
                    <div class="stat-box">
                        <h2>3+</h2> 
                        <p>Project Completed</p>
                    </div>
                    <div class="stat-box">
                        <h2>1+</h2>
                        <p>Years Experience</p>
                    </div>
                    <div class="stat-box">
                        <h2>0+</h2>
                        <p>Happy Clients</p>
                    </div>
                </div>

                <div class="cta-buttons">
                    <a href="https://wa.me/6285715933441" target="_blank" class="btn btn-primary">Hire me <i class="fas fa-arrow-right"></i></a>
                    <a href="#features" class="btn btn-secondary">Buka Mod Panel</a>
                </div>

                <div class="social-icons">
                    <a href="https://sociabuzz.com/kapi_tayerdd" target="_blank" title="SociaBuzz"><i class="fas fa-link"></i></a> 
                    <a href="https://instagram.com/kapiniceguyyy" target="_blank" title="Instagram"><i class="fab fa-instagram"></i></a> 
                    <a href="https://wa.me/6285715933441" target="_blank" title="WhatsApp"><i class="fab fa-whatsapp"></i></a> 
                </div>
            </div>
        </section>

        <section class="features-section" id="features">
            <h2 class="section-title">Mod <span>Panel</span></h2>
            <p class="section-subtitle">Navigasi menu dashboard internal. Klik setiap menu halaman untuk mengonfigurasi fungsionalitas script modding.</p>
            
            <div class="cheat-panel">
                
                <div class="panel-sidebar">
                    <div class="sidebar-title">Menu Halaman</div>
                    <button class="tab-btn active-tab" onclick="switchPage(event, 'pageEsp')"><i class="fas fa-eye"></i> ESP Wall</button>
                    <button class="tab-btn" onclick="switchPage(event, 'pageAimbot')"><i class="fas fa-crosshairs"></i> Aimbot</button>
                    <button class="tab-btn" onclick="switchPage(event, 'pageWeapon')"><i class="fas fa-gun"></i> Weapon Mod</button>
                    <button class="tab-btn" onclick="switchPage(event, 'pageLaunch')"><i class="fas fa-rocket"></i> Launch Game</button>
                </div>

                <div class="panel-body">
                    <div class="panel-header-sub">
                        <div class="logo" style="font-size: 14px; letter-spacing: 1px;"><i class="fas fa-terminal" style="color: var(--primary-color);"></i> FII`X!TERZ H4X v1.0.4</div>
                        <div class="panel-status">STATUS: UNDETECTED</div>
                    </div>

                    <div id="pageEsp" class="tab-page active-page">
                        <div class="page-headline"><i class="fas fa-eye"></i> Visual ESP Lines Configuration</div>
                        <p class="page-desc">Halaman khusus pengaturan render objek grafis menembus dinding (*Wallhack*). Modul memindai memori *driver* game real-time untuk memetakan koordinat musuh secara akurat.</p>
                        
                        <div class="action-container">
                            <div class="action-detail">
                                <h4>Aktifkan Wallhack (ESP Lines)</h4>
                                <p>Menampilkan garis lurus dan kotak kerangka posisi musuh di map.</p>
                            </div>
                            <label class="switch">
                                <input type="checkbox" class="cheat-toggle" data-name="Wallhack (ESP Lines)" onchange="consoleLog('Wallhack (ESP Lines)', this.checked)">
                                <span class="slider"></span>
                            </label>
                        </div>
                    </div>

                    <div id="pageAimbot" class="tab-page">
                        <div class="page-headline"><i class="fas fa-crosshairs"></i> Aimbot & Memory Lock System</div>
                        <p class="page-desc">Halaman enkripsi asistensi bidikan otomatis. Mengunci orientasi sudut kamera (*crosshair value*) game langsung mengarah tepat ke arah hitbox target tanpa guncangan.</p>
                        
                        <div class="action-container">
                            <div class="action-detail">
                                <h4>Aktifkan Aimbot (Silent Lock)</h4>
                                <p>Otomatis mengunci target tembakan langsung ke arah kepala (Headshot).</p>
                            </div>
                            <label class="switch">
                                <input type="checkbox" class="cheat-toggle" data-name="Aimbot (Silent Lock)" onchange="consoleLog('Aimbot (Silent Lock)', this.checked)">
                                <span class="slider"></span>
                            </label>
                        </div>
                    </div>

                    <div id="pageWeapon" class="tab-page">
                        <div class="page-headline"><i class="fas fa-gun"></i> Weapon No-Recoil Tweaks</div>
                        <p class="page-desc">Halaman optimasi performa akurasi senjata. Memodifikasi nilai sebaran peluru (*bullet spread data*) dan getaran balik pegangan senjata agar bernilai nol.</p>
                        
                        <div class="action-container">
                            <div class="action-detail">
                                <h4>No Recoil / Spread Tweak</h4>
                                <p>Menghilangkan guncangan senjata 100% membuat tembakan fokus lurus.</p>
                            </div>
                            <label class="switch">
                                <input type="checkbox" class="cheat-toggle" data-name="No Recoil / Spread" onchange="consoleLog('No Recoil / Spread', this.checked)">
                                <span class="slider"></span>
                            </label>
                        </div>
                    </div>

                    <div id="pageLaunch" class="tab-page">
                        <div class="page-headline"><i class="fas fa-rocket"></i> Android Native Intent Booster</div>
                        <p class="page-desc">Halaman eksekusi program. Ketika tombol diaktifkan, sistem web-view APK akan mengirimkan instruksi peluncuran package langsung ke inti sistem OS Android untuk menjalankan game.</p>
                        
                        <div class="action-container" style="border-color: #ff2a2a; background: linear-gradient(rgba(255,42,42,0.02), transparent);">
                            <div class="action-detail">
                                <h4 style="color: #ff2a2a;">Launch Free Fire App</h4>
                                <p>Bypass proteksi internal log dan langsung paksa jalankan Free Fire di HP.</p>
                            </div>
                            <label class="switch">
                                <input type="checkbox" id="launchToggle" onchange="launchFreeFire(this.checked)">
                                <span class="slider" style="border-color: #ff2a2a;"></span>
                            </label>
                        </div>
                    </div>

                    <div>
                        <div style="display: flex; justify-content: flex-end; margin-top: 20px;">
                            <button type="button" class="btn" onclick="resetAllCheats()" style="padding: 6px 18px; border-radius: 6px; font-size: 11px; background-color: #222; color: #fff; border: 1px solid #333;">
                                <i class="fas fa-undo"></i> Reset Memory
                            </button>
                        </div>
                        <div class="console-box" id="consoleBox">
                            $ FII-Console: Awaiting activation...<br>
                            $ System status secure. Dashboard navigation ready.
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <section class="skill-section" id="skill">
            <h2 class="section-title">My <span>Skill</span></h2>
            <p class="section-subtitle">Teknologi dan tools pengembangan website yang saya pelajari dan gunakan untuk membangun projek.</p>
            
            <div class="skills-grid">
                <div class="skill-card">
                    <i class="fab fa-html5"></i>
                    <div class="skill-info"><h3>HTML</h3></div>
                </div>
                <div class="skill-card">
                    <i class="fab fa-css3-alt"></i>
                    <div class="skill-info"><h3>CSS</h3></div>
                </div>
                <div class="skill-card">
                    <i class="fab fa-js"></i>
                    <div class="skill-info"><h3>JavaScript</h3></div>
                </div>
                <div class="skill-card">
                    <i class="fab fa-wordpress"></i>
                    <div class="skill-info"><h3>Wordpress</h3></div>
                </div>
                <div class="skill-card">
                    <i class="fab fa-elementor"></i>
                    <div class="skill-info"><h3>Elementor</h3></div>
                </div>
                <div class="skill-card">
                    <i class="fab fa-python"></i>
                    <div class="skill-info"><h3>Python</h3></div>
                </div>
            </div>
        </section>

        <section class="contact-section" id="contact">
            <div class="contact-container">
                
                <div class="contact-info">
                    <h2>Contact <span>Me</span></h2>
                    <p>Let's build something great together. Have a project in mind or just want to chat about the latest in web tech? I'm always open to discussing new opportunities, creative ideas, or ways to help your vision come to life. Drop me a message and I'll get back to you as soon as I can!</p>
                    
                    <a href="https://wa.me/6285715933441" target="_blank" class="contact-card">
                        <div class="contact-icon"><i class="fab fa-whatsapp"></i></div>
                        <div class="contact-text">
                            <h4>My Whatsapp</h4>
                            <p>need help? Contact me</p>
                        </div>
                    </a>

                    <a href="https://maps.google.com" target="_blank" class="contact-card">
                        <div class="contact-icon"><i class="fas fa-map-marker-alt"></i></div>
                        <div class="contact-text">
                            <h4>My Address</h4>
                            <p>View Google maps</p>
                        </div>
                    </a>
                </div>

                <div class="contact-form-container">
                    <h3>Send <span>Email</span></h3>
                    <form action="#" onsubmit="event.preventDefault(); alert('Pesan Anda berhasil terkirim!');">
                        <div class="form-group">
                            <input type="text" class="form-control" placeholder="Your name" required>
                        </div>
                        <div class="form-group">
                            <input type="email" class="form-control" placeholder="Your email" required>
                        </div>
                        <div class="form-group">
                            <textarea class="form-control" placeholder="whats up bro" required></textarea>
                        </div>
                        <button type="submit" class="btn-submit">Kirim</button>
                    </form>
                </div>

            </div>
        </section>
    </div>

    <script>
        // 1. LOGIN GATE LOGIC
        function handleLogin() {
            const userBox = document.getElementById('usernameInput').value;
            const passBox = document.getElementById('passwordInput').value;
            const errorMsg = document.getElementById('loginError');
            const loginGate = document.getElementById('loginGate');
            const mainContent = document.getElementById('mainContent');

            if (userBox === "FII" && passBox === "123") {
                errorMsg.style.display = "none";
                loginGate.style.opacity = "0";
                loginGate.style.transform = "scale(0.9)";
                
                setTimeout(() => {
                    loginGate.style.display = "none";
                    mainContent.style.display = "block";
                    setTimeout(() => { mainContent.style.opacity = "1"; }, 50);
                }, 500);
            } else {
                errorMsg.style.display = "block";
                document.getElementById('passwordInput').value = "";
            }
        }

        // 2. TABS PAGE NAVIGATION LOGIC
        function switchPage(event, pageId) {
            const pages = document.querySelectorAll('.tab-page');
            pages.forEach(page => { page.classList.remove('active-page'); });

            const buttons = document.querySelectorAll('.tab-btn');
            buttons.forEach(btn => { btn.classList.remove('active-tab'); });

            document.getElementById(pageId).classList.add('active-page');
            event.currentTarget.classList.add('active-tab');

            const consoleBox = document.getElementById('consoleBox');
            const menuName = event.currentTarget.innerText.trim();
            consoleBox.innerHTML += `<br>$ Navigated to [${menuName}] Section.`;
            consoleBox.scrollTop = consoleBox.scrollHeight;
        }

        // 3. FITUR LOG TOGGLE CHEAT
        function consoleLog(featureName, isChecked) {
            const consoleBox = document.getElementById('consoleBox');
            if(isChecked) {
                consoleBox.innerHTML += `<br><span>$ Injecting memory patch... [SUCCESS]</span><br>$ ${featureName} : ACTIVE`;
                alert(featureName + ' Berhasil Diaktifkan!');
            } else {
                consoleBox.innerHTML += `<br>$ ${featureName} : DISABLED`;
            }
            consoleBox.scrollTop = consoleBox.scrollHeight;
        }

        // 4. FITUR RESET TOTAL CHEAT
        function resetAllCheats() {
            const toggles = document.querySelectorAll('.cheat-toggle');
            const launchToggle = document.getElementById('launchToggle');
            const consoleBox = document.getElementById('consoleBox');
            
            toggles.forEach(toggle => { toggle.checked = false; });
            if(launchToggle) launchToggle.checked = false;
            
            consoleBox.innerHTML = `$ FII-Console: Memory cleared successfully.<br>$ All features over pages forced turned OFF.`;
            alert('Semua fitur di setiap halaman berhasil di-reset ke OFF!');
        }

        // 5. FITUR LAUNCH GAME NATIVE INTENT (IMPROVED)
        function launchFreeFire(isChecked) {
            const consoleBox = document.getElementById('consoleBox');
            if(isChecked) {
                consoleBox.innerHTML += `<br><span style="color: #ffcc00;">$ Preparing Android Intent System...</span><br>$ Target package: com.dts.freefireth`;
                consoleBox.scrollTop = consoleBox.scrollHeight;

                setTimeout(() => {
                    consoleBox.innerHTML += `<br><span style="color: #00ff66;">$ [SUCCESS] Intent launched successfully!</span><br>$ Free Fire should open in 3 seconds...`;
                    consoleBox.scrollTop = consoleBox.scrollHeight;
                    
                    // Multiple launch methods for Android compatibility
                    launchAppMultipleMethods();
                }, 800);
            } else {
                consoleBox.innerHTML += `<br>$ Launch sequence aborted.`;
                consoleBox.scrollTop = consoleBox.scrollHeight;
            }
        }

        // Multi-method app launcher for better compatibility
        function launchAppMultipleMethods() {
            // Method 1: Standard Android Intent URI
            window.location.href = "intent://com.dts.freefireth#Intent;package=com.dts.freefireth;scheme=package;action=android.intent.action.VIEW;end";
            
            // Method 2: Fallback after short delay
            setTimeout(() => {
                // Try direct package URL scheme
                window.location.href = "com.dts.freefireth://";
            }, 500);

            // Method 3: Market link fallback
            setTimeout(() => {
                window.location.href = "market://details?id=com.dts.freefireth";
            }, 1500);
        }

        // Allow enter key to login
        document.addEventListener('keypress', function(event) {
            if(event.key === 'Enter') {
                const loginGate = document.getElementById('loginGate');
                if(loginGate && loginGate.style.display !== 'none') {
                    handleLogin();
                }
            }
        });
    </script>
</body>
</html>
