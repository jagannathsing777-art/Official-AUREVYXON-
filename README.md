<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="AUREVYXON - The Future of Digital Intelligence. Experience the next generation of AI-driven application architecture.">
    <title>AUREVYXON | Transcending Digital Boundaries</title>
    <style>
        /* =========================================
           1. CORE VARIABLES & RESET
           ========================================= */
        :root {
            --bg-deep: #050505;
            --bg-dark: #0a0f1e;
            --primary: #00f3ff; /* Electric Cyan */
            --primary-dim: rgba(0, 243, 255, 0.15);
            --primary-glow: rgba(0, 243, 255, 0.6);
            --silver: #e0e6ed;
            --silver-dim: #8b9bb4;
            --glass: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.08);
            --font-main: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            --transition: all 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-deep);
            color: var(--silver);
            font-family: var(--font-main);
            overflow-x: hidden;
            line-height: 1.6;
            -webkit-font-smoothing: antialiased;
        }

        /* =========================================
           2. BACKGROUND ENGINE (CANVAS)
           ========================================= */
        #galaxyCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
        }

        .overlay-vignette {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at center, transparent 0%, #050505 90%);
            z-index: -1;
            pointer-events: none;
        }

        /* =========================================
           3. TYPOGRAPHY & UTILITIES
           ========================================= */
        h1, h2, h3 {
            color: #fff;
            text-transform: uppercase;
            letter-spacing: 3px;
        }

        h1 {
            font-size: clamp(2.5rem, 5vw, 5rem);
            font-weight: 800;
            background: linear-gradient(135deg, #fff 0%, var(--primary) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 1rem;
            text-shadow: 0 0 30px var(--primary-dim);
        }

        h2 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        p {
            color: var(--silver-dim);
            font-size: 1.1rem;
            margin-bottom: 1.5rem;
            font-weight: 300;
        }

        .section-subtitle {
            display: block;
            color: var(--primary);
            font-size: 0.85rem;
            letter-spacing: 6px;
            margin-bottom: 1.5rem;
            font-weight: 700;
            text-transform: uppercase;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .section-padding {
            padding: 10rem 0;
        }

        .text-center { text-align: center; }

        .glass-panel {
            background: var(--glass);
            border: 1px solid var(--glass-border);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            padding: 2.5rem;
            border-radius: 4px;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .glass-panel:hover {
            border-color: var(--primary);
            transform: translateY(-5px);
            box-shadow: 0 20px 40px -10px rgba(0, 0, 0, 0.8);
        }

        .divider {
            height: 2px;
            width: 80px;
            background: var(--primary);
            margin: 1rem auto;
            box-shadow: 0 0 15px var(--primary);
            border-radius: 2px;
        }

        /* =========================================
           4. NAVIGATION
           ========================================= */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 1.5rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            background: rgba(5, 5, 5, 0.0);
            transition: all 0.4s ease;
            border-bottom: 1px solid transparent;
        }

        .navbar.scrolled {
            background: rgba(5, 5, 5, 0.9);
            backdrop-filter: blur(15px);
            padding: 1rem 5%;
            border-bottom: 1px solid var(--glass-border);
        }

        .logo-text {
            font-weight: 900;
            font-size: 1.5rem;
            letter-spacing: 2px;
            color: #fff;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo-icon-small {
            width: 30px;
            height: 30px;
            border: 2px solid var(--primary);
            transform: rotate(45deg);
            position: relative;
        }
        .logo-icon-small::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            border: 1px solid #fff;
            top: -4px;
            left: -4px;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 3rem;
        }

        .nav-links a {
            text-decoration: none;
            color: #fff;
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            transition: 0.3s;
            opacity: 0.7;
            position: relative;
        }

        .nav-links a:hover {
            opacity: 1;
            color: var(--primary);
            text-shadow: 0 0 10px var(--primary-glow);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 1px;
            bottom: -5px;
            left: 0;
            background: var(--primary);
            transition: 0.3s;
        }

        .nav-links a:hover::after { width: 100%; }

        .nav-cta {
            border: 1px solid var(--primary);
            padding: 0.6rem 1.8rem;
            border-radius: 0;
            opacity: 1 !important;
        }

        .nav-cta:hover {
            background: var(--primary-dim);
            box-shadow: 0 0 15px var(--primary-dim);
        }

        /* Mobile Menu */
        .mobile-toggle {
            display: none;
            cursor: pointer;
            z-index: 1001;
        }
        .bar {
            width: 30px;
            height: 2px;
            background: #fff;
            margin: 6px 0;
            transition: 0.4s;
        }

        /* =========================================
           5. HERO SECTION & 3D LOGO
           ========================================= */
        .hero-section {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            perspective: 1000px;
        }

        .hero-content {
            z-index: 2;
            max-width: 900px;
            padding: 0 1rem;
        }

        /* Pure CSS 3D Logo */
        .aurevyxon-emblem {
            width: 140px;
            height: 140px;
            margin: 0 auto 3rem;
            position: relative;
            transform-style: preserve-3d;
            animation: floatLogo 6s ease-in-out infinite;
        }

        @keyframes floatLogo {
            0%, 100% { transform: translateY(0) rotateX(0); }
            50% { transform: translateY(-20px) rotateX(10deg); }
        }

        .logo-pyramid {
            width: 0;
            height: 0;
            border-left: 60px solid transparent;
            border-right: 60px solid transparent;
            border-bottom: 110px solid linear-gradient(to bottom, #fff, #aaa);
            position: absolute;
            top: 15px;
            left: 10px;
            filter: drop-shadow(0 0 15px rgba(255,255,255,0.4));
            z-index: 2;
        }
        
        .logo-pyramid::after {
            content:'';
            position: absolute;
            top: 30px;
            left: -40px;
            width: 0;
            height: 0;
            border-left: 40px solid transparent;
            border-right: 40px solid transparent;
            border-bottom: 80px solid var(--bg-deep);
        }

        .logo-ring {
            position: absolute;
            width: 100%;
            height: 100%;
            border: 4px solid var(--primary);
            border-radius: 50%;
            top: 0;
            left: 0;
            transform: rotateX(75deg);
            box-shadow: 0 0 25px var(--primary), inset 0 0 15px var(--primary);
            animation: spinRing 8s linear infinite;
        }

        @keyframes spinRing {
            0% { transform: rotateX(75deg) rotateZ(0deg); }
            100% { transform: rotateX(75deg) rotateZ(360deg); }
        }

        .cta-group {
            margin-top: 3rem;
            display: flex;
            justify-content: center;
            gap: 1.5rem;
        }

        /* Buttons */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            padding: 1.2rem 3rem;
            font-size: 0.9rem;
            text-transform: uppercase;
            text-decoration: none;
            letter-spacing: 2px;
            font-weight: 700;
            position: relative;
            overflow: hidden;
            transition: var(--transition);
            clip-path: polygon(15px 0, 100% 0, 100% calc(100% - 15px), calc(100% - 15px) 100%, 0 100%, 0 15px);
            cursor: pointer;
            border: none;
            color: #fff;
        }

        .btn-primary {
            background: var(--primary);
            color: #000;
            box-shadow: 0 0 30px var(--primary-dim);
        }

        .btn-primary:hover {
            box-shadow: 0 0 50px var(--primary-glow);
            transform: translateY(-3px);
            background: #fff;
        }

        .btn-secondary {
            background: transparent;
            border: 1px solid rgba(255,255,255,0.2);
            color: #fff;
        }

        .btn-secondary:hover {
            border-color: var(--primary);
            background: rgba(0, 243, 255, 0.05);
            text-shadow: 0 0 8px var(--primary);
        }

        /* Button Ripple & Glare */
        .btn .glare {
            position: absolute;
            top: 0;
            left: -150%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.8), transparent);
            transform: skewX(-25deg);
            transition: 0.5s;
        }
        .btn:hover .glare {
            left: 150%;
            transition: 0.7s;
        }

        /* =========================================
           6. FEATURES (GRID)
           ========================================= */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 2rem;
            margin-top: 4rem;
        }

        .icon-box {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #151a25, #0a0f1e);
            border: 1px solid var(--glass-border);
            margin-bottom: 2rem;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 8px;
            position: relative;
        }
        
        .icon-box::before {
            content:'';
            position: absolute;
            inset: -1px;
            background: linear-gradient(45deg, transparent, var(--primary), transparent);
            z-index: -1;
            opacity: 0;
            transition: 0.5s;
            border-radius: 9px;
        }
        
        .glass-panel:hover .icon-box::before { opacity: 1; }

        .feature-icon-svg {
            width: 30px;
            height: 30px;
            fill: #fff;
        }

        /* =========================================
           7. APP SHOWCASE (CSS MOCKUP)
           ========================================= */
        .showcase-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .phone-wrapper {
            position: relative;
            perspective: 2000px;
            display: flex;
            justify-content: center;
        }

        .phone-frame {
            width: 320px;
            height: 650px;
            background: #000;
            border-radius: 50px;
            border: 6px solid #2a2a2a;
            box-shadow: 
                0 0 0 2px #111,
                inset 0 0 20px rgba(0,0,0,1),
                20px 20px 60px rgba(0,0,0,0.6);
            position: relative;
            overflow: hidden;
            transform: rotateY(-20deg) rotateX(5deg);
            transition: transform 0.8s ease;
        }

        .phone-wrapper:hover .phone-frame {
            transform: rotateY(0deg) rotateX(0deg);
        }

        .phone-screen {
            width: 100%;
            height: 100%;
            background: linear-gradient(180deg, #050505 0%, #0d1424 100%);
            padding: 40px 20px;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        /* Mock UI */
        .app-header { display: flex; justify-content: space-between; align-items: center; }
        .app-menu { width: 20px; height: 2px; background: #fff; box-shadow: 0 6px 0 #fff; }
        .app-widgets {
            height: 180px;
            background: rgba(255,255,255,0.05);
            border-radius: 20px;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255,255,255,0.1);
        }
        .graph-line {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100px;
            background: linear-gradient(to top, rgba(0,243,255,0.2), transparent);
            clip-path: polygon(0 100%, 10% 80%, 25% 60%, 40% 70%, 55% 40%, 70% 50%, 85% 20%, 100% 40%, 100% 100%);
        }
        .graph-line-top {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100px;
            border-top: 2px solid var(--primary);
            clip-path: polygon(0 100%, 10% 80%, 25% 60%, 40% 70%, 55% 40%, 70% 50%, 85% 20%, 100% 40%, 100% 100%, 100% 102%, 0 102%);
            filter: drop-shadow(0 0 5px var(--primary));
        }

        .app-row { display: flex; gap: 10px; }
        .app-card { flex: 1; height: 100px; background: rgba(255,255,255,0.03); border-radius: 15px; }

        /* =========================================
           8. TECH STACK
           ========================================= */
        .tech-item {
            margin-bottom: 2.5rem;
        }
        .tech-meta {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.8rem;
            font-family: monospace;
            color: var(--primary);
        }
        .progress-track {
            width: 100%;
            height: 4px;
            background: rgba(255,255,255,0.1);
            position: relative;
        }
        .progress-fill {
            height: 100%;
            background: var(--primary);
            width: 0;
            box-shadow: 0 0 20px var(--primary);
            position: absolute;
            top: 0;
            left: 0;
            transition: width 2s cubic-bezier(0.22, 1, 0.36, 1);
        }

        /* =========================================
           9. FOOTER & CTA
           ========================================= */
        .cta-section {
            position: relative;
            overflow: hidden;
            background: linear-gradient(to top, #000, #0a0f1e);
        }

        .store-buttons {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            margin-top: 3rem;
            flex-wrap: wrap;
        }

        .store-btn {
            background: #000;
            border: 1px solid #333;
            padding: 0.8rem 2rem;
            border-radius: 8px;
            display: flex;
            align-items: center;
            gap: 12px;
            cursor: pointer;
            transition: var(--transition);
            color: #fff;
            min-width: 180px;
        }

        .store-btn:hover {
            border-color: var(--primary);
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 243, 255, 0.15);
        }

        .store-icon { width: 28px; height: 28px; background: #fff; }
        .apple-icon { -webkit-mask: url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M18.71 19.5c-.83 1.24-1.71 2.45-3.05 2.47-1.34.03-1.77-.79-3.29-.79-1.53 0-2 .77-3.27.8-1.31.05-2.3-1.32-3.14-2.53C4.25 17 2.94 12.45 4.7 9.39c.87-1.52 2.43-2.48 4.12-2.51 1.28-.02 2.5.87 3.29.87.78 0 2.26-1.07 3.81-.91.65.03 2.47.26 3.64 1.98-.09.06-2.17 1.28-2.15 3.81.03 3.02 2.65 4.03 2.68 4.04-.03.07-.42 1.44-1.38 2.83M13 3.5c.68-.83 1.14-1.99.94-3.14-1.02.04-2.26.68-3 1.54-.64.74-1.2 1.95-1.05 3.08 1.13.09 2.29-.64 3.11-1.48z'/%3E%3C/svg%3E") no-repeat center; mask: url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M18.71 19.5c-.83 1.24-1.71 2.45-3.05 2.47-1.34.03-1.77-.79-3.29-.79-1.53 0-2 .77-3.27.8-1.31.05-2.3-1.32-3.14-2.53C4.25 17 2.94 12.45 4.7 9.39c.87-1.52 2.43-2.48 4.12-2.51 1.28-.02 2.5.87 3.29.87.78 0 2.26-1.07 3.81-.91.65.03 2.47.26 3.64 1.98-.09.06-2.17 1.28-2.15 3.81.03 3.02 2.65 4.03 2.68 4.04-.03.07-.42 1.44-1.38 2.83M13 3.5c.68-.83 1.14-1.99.94-3.14-1.02.04-2.26.68-3 1.54-.64.74-1.2 1.95-1.05 3.08 1.13.09 2.29-.64 3.11-1.48z'/%3E%3C/svg%3E") no-repeat center; }
        .play-icon { -webkit-mask: url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M17.523 15.3414c-.5511 0-.9993-.4486-.9993-.9997s.4482-.9993.9993-.9993c.5511 0 .9993.4482.9993.9993.0001.5511-.4482.9997-.9993.9997m-11.046 0c-.5511 0-.9993-.4486-.9993-.9997s.4482-.9993.9993-.9993c.5511 0 .9993.4482.9993.9993 0 .5511-.4482.9997-.9993.9997m11.4045-6.02l1.9973-3.4592a.416.416 0 00-.1527-.5676.416.416 0 00-.5676.1527l-2.0225 3.503c-1.6366-.7492-3.4832-1.168-5.4542-1.168-1.9566 0-3.7915.4137-5.4194 1.153L4.2393 5.4326a.4161.4161 0 00-.5676-.1527.4159.4159 0 00-.1527.5676l2.0094 3.4796C2.2605 10.9754.7969 13.9113.75 17.25h22.5c-.0469-3.3524-1.5199-6.3013-4.3685-7.9286'/%3E%3C/svg%3E") no-repeat center; mask: url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M17.523 15.3414c-.5511 0-.9993-.4486-.9993-.9997s.4482-.9993.9993-.9993c.5511 0 .9993.4482.9993.9993.0001.5511-.4482.9997-.9993.9997m-11.046 0c-.5511 0-.9993-.4486-.9993-.9997s.4482-.9993.9993-.9993c.5511 0 .9993.4482.9993.9993 0 .5511-.4482.9997-.9993.9997m11.4045-6.02l1.9973-3.4592a.416.416 0 00-.1527-.5676.416.416 0 00-.5676.1527l-2.0225 3.503c-1.6366-.7492-3.4832-1.168-5.4542-1.168-1.9566 0-3.7915.4137-5.4194 1.153L4.2393 5.4326a.4161.4161 0 00-.5676-.1527.4159.4159 0 00-.1527.5676l2.0094 3.4796C2.2605 10.9754.7969 13.9113.75 17.25h22.5c-.0469-3.3524-1.5199-6.3013-4.3685-7.9286'/%3E%3C/svg%3E") no-repeat center; }

        footer {
            background: #000;
            border-top: 1px solid #111;
            padding: 4rem 0 2rem;
            color: #555;
            font-size: 0.9rem;
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 2rem;
        }

        .footer-links a { color: #666; text-decoration: none; margin-left: 1.5rem; transition: 0.3s; }
        .footer-links a:hover { color: var(--primary); }

        /* =========================================
           10. ANIMATION CLASSES
           ========================================= */
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 1s cubic-bezier(0.165, 0.84, 0.44, 1);
        }
        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }
        
        /* Delays */
        .d-1 { transition-delay: 0.1s; }
        .d-2 { transition-delay: 0.2s; }
        .d-3 { transition-delay: 0.3s; }

        /* Mobile */
        @media (max-width: 768px) {
            .mobile-toggle { display: block; }
            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 80%;
                height: 100vh;
                background: #050505;
                flex-direction: column;
                justify-content: center;
                align-items: center;
                transition: 0.5s;
                border-left: 1px solid #222;
            }
            .nav-links.active { right: 0; }
            .showcase-grid { grid-template-columns: 1fr; }
            .phone-frame { width: 90%; height: 500px; margin: 0 auto; transform: none !important; }
            .footer-content { flex-direction: column; text-align: center; }
            .footer-links a { margin: 0 10px; }
            .cta-group { flex-direction: column; }
            .btn { width: 100%; }
        }
    </style>
</head>
<body>

    <!-- Background Engine -->
    <canvas id="galaxyCanvas"></canvas>
    <div class="overlay-vignette"></div>

    <!-- Navbar -->
    <nav class="navbar">
        <div class="logo-container">
            <span class="logo-text">
                <div class="logo-icon-small"></div>
                AUREVYXON
            </span>
        </div>
        <ul class="nav-links">
            <li><a href="#about">Philosophy</a></li>
            <li><a href="#features">Capabilities</a></li>
            <li><a href="#technology">Tech Stack</a></li>
            <li><a href="#download" class="nav-cta">Access Node</a></li>
        </ul>
        <div class="mobile-toggle" onclick="toggleMenu()">
            <div class="bar"></div>
            <div class="bar"></div>
            <div class="bar"></div>
        </div>
    </nav>

    <!-- Hero Section -->
    <header class="hero-section">
        <div class="hero-content">
            <div class="logo-wrapper reveal">
                <!-- CSS Constructed 3D Logo -->
                <div class="aurevyxon-emblem">
                    <div class="logo-pyramid"></div>
                    <div class="logo-ring"></div>
                </div>
            </div>
            <h1 class="reveal d-1">AUREVYXON</h1>
            <p class="reveal d-2">ARCHITECTING THE INFINITE. THE NEXUS OF INTELLIGENCE.</p>
            
            <div class="cta-group reveal d-3">
                <a href="#download" class="btn btn-primary">
                    <span class="btn-text">Initialize Core</span>
                    <div class="glare"></div>
                </a>
                <a href="#features" class="btn btn-secondary">
                    <span class="btn-text">Explore System</span>
                </a>
            </div>
        </div>
    </header>

    <!-- About Section -->
    <section id="about" class="section-padding">
        <div class="container">
            <div class="text-center reveal">
                <span class="section-subtitle">IDENTITY</span>
                <h2>Beyond Software</h2>
                <div class="divider"></div>
                <p style="max-width: 700px; margin: 0 auto;">
                    AUREVYXON is not merely an application; it is a meticulously crafted ecosystem designed for the elite. 
                    Born from the convergence of aerospace aesthetics and advanced neural computing, we bridge the gap between complex algorithms and human intuition.
                </p>
            </div>
        </div>
    </section>

    <!-- Features Grid -->
    <section id="features" class="section-padding">
        <div class="container">
            <div class="reveal">
                <span class="section-subtitle">CAPABILITIES</span>
                <h2>System Modules</h2>
            </div>
            
            <div class="features-grid">
                <!-- Feature 1 -->
                <div class="glass-panel reveal d-1">
                    <div class="icon-box">
                        <svg class="feature-icon-svg" viewBox="0 0 24 24"><path d="M12 2L2 19h20L12 2zm0 3.8L18.8 17H5.2L12 5.8z"/></svg>
                    </div>
                    <h3>Neural Sync</h3>
                    <p>Adaptive algorithms that learn your usage patterns to predict and preload necessary data streams instantly.</p>
                </div>
                <!-- Feature 2 -->
                <div class="glass-panel reveal d-2">
                    <div class="icon-box">
                        <svg class="feature-icon-svg" viewBox="0 0 24 24"><path d="M12 1L3 5v6c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V5l-9-4zm0 10.99h7c-.53 4.12-3.28 7.79-7 8.94V12H5V6.3l7-3.11v8.8z"/></svg>
                    </div>
                    <h3>Titanium Security</h3>
                    <p>Military-grade end-to-end encryption ensures your digital footprint remains absolute zero. Trustless architecture.</p>
                </div>
                <!-- Feature 3 -->
                <div class="glass-panel reveal d-3">
                    <div class="icon-box">
                        <svg class="feature-icon-svg" viewBox="0 0 24 24"><path d="M19.35 10.04C18.67 6.59 15.64 4 12 4 9.11 4 6.6 5.64 5.35 8.04 2.34 8.36 0 10.91 0 14c0 3.31 2.69 6 6 6h13c2.76 0 5-2.24 5-5 0-2.64-2.05-4.78-4.65-4.96z"/></svg>
                    </div>
                    <h3>Hyper-Scale</h3>
                    <p>Built on a proprietary serverless grid allowing infinite scaling without compromising microsecond latency.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- App Showcase -->
    <section class="section-padding">
        <div class="container">
            <div class="showcase-grid">
                <div class="phone-wrapper reveal">
                    <div class="phone-frame">
                        <div class="phone-screen">
                            <div class="app-header">
                                <span style="font-weight:bold; color:#fff;">AUREVYXON</span>
                                <div class="app-menu"></div>
                            </div>
                            <div style="margin-top:20px; color:#aaa; font-size:0.8rem;">SYSTEM STATUS: ONLINE</div>
                            <div class="app-widgets">
                                <div class="graph-line"></div>
                                <div class="graph-line-top"></div>
                            </div>
                            <div class="app-row">
                                <div class="app-card"></div>
                                <div class="app-card"></div>
                            </div>
                            <div class="app-card" style="height: 150px; background: rgba(0,243,255,0.05); border: 1px solid rgba(0,243,255,0.2);"></div>
                        </div>
                    </div>
                </div>
                <div class="reveal d-1">
                    <span class="section-subtitle">INTERFACE</span>
                    <h2>Fluidity in Motion</h2>
                    <p>The interface utilizes our "Liquid Glass" engine. Every touch prompts a calculated, physics-based reaction.</p>
                    
                    <div style="margin-top: 2rem;">
                        <div class="tech-item">
                            <div class="tech-meta"><span>Response Time</span><span>0.02ms</span></div>
                            <div class="progress-track"><div class="progress-fill" style="width:99%"></div></div>
                        </div>
                        <div class="tech-item">
                            <div class="tech-meta"><span>Encryption</span><span>256-bit</span></div>
                            <div class="progress-track"><div class="progress-fill" style="width:100%"></div></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Tech Stack -->
    <section id="technology" class="section-padding" style="background: rgba(255,255,255,0.02);">
        <div class="container text-center reveal">
            <span class="section-subtitle">CORE ENGINE</span>
            <h2>Architectural Superiority</h2>
            <div class="divider"></div>
            <p style="max-width:600px; margin: 0 auto 3rem;">
                No libraries. No bloat. Pure, hand-written code designed for performance.
                Optimized for the next generation of hardware.
            </p>
            <div style="display: flex; justify-content: center; gap: 2rem; flex-wrap: wrap;">
                <div class="glass-panel" style="padding: 1rem 2rem;">HTML5 Core</div>
                <div class="glass-panel" style="padding: 1rem 2rem; border-color: var(--primary);">WebGL Rendering</div>
                <div class="glass-panel" style="padding: 1rem 2rem;">Neural Net API</div>
            </div>
        </div>
    </section>

    <!-- CTA / Download -->
    <section id="download" class="section-padding cta-section text-center">
        <div class="container reveal">
            <h2>The Future Awaits</h2>
            <p>Join the closed beta. Experience the pinnacle of mobile technology.</p>
            
            <div class="store-buttons">
                <button class="store-btn">
                    <div class="store-icon apple-icon"></div>
                    <div style="text-align:left; line-height: 1.2;">
                        <div style="font-size:0.6rem; text-transform:uppercase;">Download on the</div>
                        <div style="font-size:1.1rem; font-weight:bold;">App Store</div>
                    </div>
                </button>
                <button class="store-btn">
                    <div class="store-icon play-icon"></div>
                    <div style="text-align:left; line-height: 1.2;">
                        <div style="font-size:0.6rem; text-transform:uppercase;">Get it on</div>
                        <div style="font-size:1.1rem; font-weight:bold;">Google Play</div>
                    </div>
                </button>
            </div>
            <p style="margin-top: 2rem; font-size: 0.8rem; opacity: 0.5;">
                System Requirements: iOS 17+ or Android 14+. Optimized for high-performance devices.
            </p>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div>
                    <h3 style="color:#fff; margin-bottom:0.5rem;">AUREVYXON</h3>
                    <p style="margin:0; font-size:0.8rem;">&copy; 2025 Aurevyxon Technologies.</p>
                </div>
                <div class="footer-links">
                    <a href="#">Privacy Protocol</a>
                    <a href="#">Terms of Service</a>
                    <a href="#">System Status</a>
                </div>
            </div>
        </div>
    </footer>

    <!-- JavaScript Logic -->
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            // --- 1. PARTICLE GALAXY ENGINE ---
            const canvas = document.getElementById('galaxyCanvas');
            const ctx = canvas.getContext('2d');
            
            let width, height;
            let particles = [];
            const particleCount = window.innerWidth < 768 ? 50 : 100; 
            const connectionDistance = 140;

            function resize() {
                width = canvas.width = window.innerWidth;
                height = canvas.height = window.innerHeight;
            }
            window.addEventListener('resize', resize);
            resize();

            class Particle {
                constructor() {
                    this.x = Math.random() * width;
                    this.y = Math.random() * height;
                    this.vx = (Math.random() - 0.5) * 0.4;
                    this.vy = (Math.random() - 0.5) * 0.4;
                    this.size = Math.random() * 2;
                    this.color = Math.random() > 0.95 ? '#00f3ff' : '#666'; 
                }
                update() {
                    this.x += this.vx;
                    this.y += this.vy;
                    if (this.x < 0) this.x = width;
                    else if (this.x > width) this.x = 0;
                    if (this.y < 0) this.y = height;
                    else if (this.y > height) this.y = 0;
                }
                draw() {
                    ctx.beginPath();
                    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                    ctx.fillStyle = this.color;
                    ctx.fill();
                    // Glow for blue particles
                    if (this.color === '#00f3ff') {
                        ctx.shadowBlur = 10;
                        ctx.shadowColor = '#00f3ff';
                    } else {
                        ctx.shadowBlur = 0;
                    }
                }
            }

            for (let i = 0; i < particleCount; i++) particles.push(new Particle());

            function animateParticles() {
                ctx.clearRect(0, 0, width, height);
                
                for (let i = 0; i < particles.length; i++) {
                    const p = particles[i];
                    p.update();
                    p.draw();

                    for (let j = i + 1; j < particles.length; j++) {
                        const p2 = particles[j];
                        const dx = p.x - p2.x;
                        const dy = p.y - p2.y;
                        const dist = Math.sqrt(dx*dx + dy*dy);

                        if (dist < connectionDistance) {
                            ctx.beginPath();
                            ctx.strokeStyle = `rgba(100, 150, 255, ${1 - dist/connectionDistance})`;
                            ctx.lineWidth = 0.5;
                            ctx.moveTo(p.x, p.y);
                            ctx.lineTo(p2.x, p2.y);
                            ctx.stroke();
                        }
                    }
                }
                requestAnimationFrame(animateParticles);
            }
            animateParticles();

            // --- 2. SCROLL REVEAL & NAVBAR ---
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('active');
                        // Animate progress bars if inside
                        const bars = entry.target.querySelectorAll('.progress-fill');
                        bars.forEach(bar => {
                            // Trigger reflow or simple width set logic if needed
                            // CSS transition handles it automatically if width is set inline
                        });
                    }
                });
            }, { threshold: 0.1 });

            document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

            const navbar = document.querySelector('.navbar');
            window.addEventListener('scroll', () => {
                if (window.scrollY > 50) navbar.classList.add('scrolled');
                else navbar.classList.remove('scrolled');
            });

            // --- 3. MOBILE MENU ---
            window.toggleMenu = function() {
                const navLinks = document.querySelector('.nav-links');
                navLinks.classList.toggle('active');
            };

            // --- 4. BUTTON RIPPLE EFFECT ---
            document.querySelectorAll('.btn').forEach(btn => {
                btn.addEventListener('click', function(e) {
                    let rect = this.getBoundingClientRect();
                    let x = e.clientX - rect.left;
                    let y = e.clientY - rect.top;
                    
                    let ripple = document.createElement('span');
                    ripple.style.position = 'absolute';
                    ripple.style.left = x + 'px';
                    ripple.style.top = y + 'px';
                    ripple.style.transform = 'translate(-50%, -50%)';
                    ripple.style.width = '0px';
                    ripple.style.height = '0px';
                    ripple.style.background = 'rgba(255,255,255,0.4)';
                    ripple.style.borderRadius = '50%';
                    ripple.style.pointerEvents = 'none';
                    ripple.style.transition = 'width 0.6s ease-out, height 0.6s ease-out, opacity 0.6s ease-out';
                    
                    this.appendChild(ripple);
                    
                    setTimeout(() => {
                        ripple.style.width = '300px';
                        ripple.style.height = '300px';
                        ripple.style.opacity = '0';
                    }, 10);
                    
                    setTimeout(() => ripple.remove(), 600);
                });
            });
        });
    </script>
</body>
</html>
