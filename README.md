<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>CONEJO — Agiliza tu labor docente</title>
 
    <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>🐇</text></svg>">
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@200;300;400;500;600;700;800;900&family=Playfair+Display:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
 
    <style>
        :root {
            --bg: #f0ece6;
            --fg: #1a1a2e;
            --muted: #8a8698;
            --accent: #7c3aed;
            --accent-light: #a78bfa;
            --accent-dark: #4c1d95;
            --glass-bg: rgba(255, 255, 255, 0.5);
            --glass-border: rgba(255, 255, 255, 0.75);
            --glass-shine: rgba(255, 255, 255, 0.8);
        }
 
        * { margin: 0; padding: 0; box-sizing: border-box; }
 
        html { scroll-behavior: smooth; }
 
        body {
            font-family: 'Outfit', sans-serif;
            background: var(--bg);
            color: var(--fg);
            line-height: 1.6;
            overflow-x: hidden;
        }
 
        /* ===== FONDO ===== */
        .bg-scene {
            position: fixed; inset: 0; z-index: 0; overflow: hidden;
            background: linear-gradient(160deg, #f5f1eb 0%, #ede7f0 40%, #e8e0f0 70%, #f0ece6 100%);
        }
        .blob { position: absolute; border-radius: 50%; filter: blur(90px); opacity: 0.45; will-change: transform; }
        .blob-1 { width: 550px; height: 550px; background: radial-gradient(circle, rgba(124,58,237,0.35), transparent 70%); top: -15%; left: -8%; animation: f1 20s ease-in-out infinite; }
        .blob-2 { width: 500px; height: 500px; background: radial-gradient(circle, rgba(192,132,252,0.3), transparent 70%); top: 20%; right: -12%; animation: f2 24s ease-in-out infinite; }
        .blob-3 { width: 420px; height: 420px; background: radial-gradient(circle, rgba(167,139,250,0.22), transparent 70%); top: 65%; left: 50%; animation: f3 22s ease-in-out infinite; }
        .blob-4 { width: 380px; height: 380px; background: radial-gradient(circle, rgba(236,72,153,0.10), transparent 70%); bottom: -10%; left: -5%; animation: f4 26s ease-in-out infinite; }
 
        @keyframes f1 { 0%,100%{transform:translate(0,0) scale(1)} 25%{transform:translate(70px,50px) scale(1.08)} 50%{transform:translate(30px,100px) scale(.95)} 75%{transform:translate(-20px,40px) scale(1.04)} }
        @keyframes f2 { 0%,100%{transform:translate(0,0) scale(1)} 30%{transform:translate(-60px,-70px) scale(1.12)} 60%{transform:translate(-30px,-30px) scale(.92)} }
        @keyframes f3 { 0%,100%{transform:translate(0,0) scale(1)} 33%{transform:translate(-80px,40px) scale(1.08)} 66%{transform:translate(40px,-50px) scale(.96)} }
        @keyframes f4 { 0%,100%{transform:translate(0,0)} 50%{transform:translate(60px,-50px)} }
 
        .bg-grid {
            position: fixed; inset: 0; z-index: 1; pointer-events: none;
            background-image: linear-gradient(rgba(124,58,237,0.025) 1px, transparent 1px), linear-gradient(90deg, rgba(124,58,237,0.025) 1px, transparent 1px);
            background-size: 50px 50px;
        }
 
        /* ===== GLASS ===== */
        .liquid-glass {
            background: var(--glass-bg);
            backdrop-filter: blur(50px) saturate(1.6);
            -webkit-backdrop-filter: blur(50px) saturate(1.6);
            border: 1px solid var(--glass-border);
            border-radius: 28px;
            position: relative; overflow: hidden;
            box-shadow: 0 8px 32px rgba(0,0,0,0.04), 0 2px 8px rgba(124,58,237,0.04), inset 0 1px 0 rgba(255,255,255,0.6);
        }
        .liquid-glass::before {
            content: ''; position: absolute; top: 0; left: 0; right: 0; height: 55%;
            background: linear-gradient(180deg, var(--glass-shine) 0%, transparent 100%);
            border-radius: 28px 28px 0 0; pointer-events: none; opacity: 0.4;
        }
        .liquid-glass::after {
            content: ''; position: absolute; top: -1px; left: 15%; right: 15%; height: 1px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.9), transparent);
            pointer-events: none;
        }
 
        main { position: relative; z-index: 2; max-width: 980px; margin: 0 auto; padding: 0 24px; }
 
        /* ===== HERO ===== */
        .hero { min-height: 100vh; display: flex; flex-direction: column; align-items: center; justify-content: center; text-align: center; padding: 60px 0 40px; }
        .mascot-wrapper { width: 200px; height: 200px; margin: 0 auto 8px; position: relative; display: flex; align-items: flex-end; justify-content: center; }
        .mascot-rabbit { position: absolute; bottom: 0; width: 100%; height: auto; filter: drop-shadow(0 10px 15px rgba(124,58,237,0.25)); animation: realisticJump 2.2s cubic-bezier(0.25, 0.46, 0.45, 0.94) infinite; }
        .mascot-shadow { position: absolute; bottom: 0; width: 100px; height: 13px; background: rgba(124,58,237,0.15); border-radius: 50%; filter: blur(5px); animation: realisticShadow 2.2s cubic-bezier(0.25, 0.46, 0.45, 0.94) infinite; }
        @keyframes realisticJump { 0%, 100% { transform: translateY(0) scale(1, 1); } 10% { transform: translateY(2px) scale(1.02, 0.95); } 40% { transform: translateY(-22px) scale(0.98, 1.04); } 60% { transform: translateY(-22px) scale(0.98, 1.04); } 85% { transform: translateY(0) scale(1.02, 0.95); } }
        @keyframes realisticShadow { 0%, 100% { transform: scale(1); opacity: 0.5; } 10% { transform: scale(1.1); opacity: 0.6; } 40% { transform: scale(0.5); opacity: 0.2; } 60% { transform: scale(0.5); opacity: 0.2; } 85% { transform: scale(1.1); opacity: 0.6; } }
 
        .logo-text { font-weight: 900; font-size: 4rem; letter-spacing: 0.15em; text-transform: uppercase; line-height: 1; color: var(--fg); }
        .logo-sub { font-weight: 300; font-size: 1.05rem; color: var(--muted); margin-top: 14px; letter-spacing: 0.04em; }
        .lede {
            font-family: 'Playfair Display', serif; font-style: italic; font-weight: 400;
            font-size: 1.35rem; color: var(--accent-dark); max-width: 560px; margin: 26px auto 0; line-height: 1.5;
        }
 
        .hero-actions { display: flex; gap: 14px; margin-top: 36px; flex-wrap: wrap; justify-content: center; }
        .btn {
            display: inline-flex; align-items: center; gap: 9px; padding: 13px 28px; border-radius: 50px;
            font-weight: 600; font-size: 0.92rem; text-decoration: none; cursor: pointer; border: none;
            transition: transform 0.25s cubic-bezier(0.23,1,0.32,1), box-shadow 0.25s ease;
        }
        .btn-primary { background: linear-gradient(135deg, #7c3aed, #4c1d95); color: #fff; box-shadow: 0 8px 24px rgba(124,58,237,0.3); }
        .btn-primary:hover { transform: translateY(-3px); box-shadow: 0 12px 32px rgba(124,58,237,0.4); }
        .btn-ghost { background: var(--glass-bg); color: var(--fg); border: 1px solid var(--glass-border); backdrop-filter: blur(20px); }
        .btn-ghost:hover { transform: translateY(-3px); border-color: rgba(124,58,237,0.3); }
 
        .scroll-hint { position: absolute; bottom: 28px; left: 50%; transform: translateX(-50%); color: var(--muted); font-size: 0.75rem; letter-spacing: 0.1em; text-transform: uppercase; display: flex; flex-direction: column; align-items: center; gap: 6px; opacity: 0.7; }
        .scroll-hint i { animation: bounce 1.8s ease-in-out infinite; }
        @keyframes bounce { 0%,100%{transform:translateY(0)} 50%{transform:translateY(6px)} }
 
        /* ===== SECTIONS ===== */
        .section { padding: 70px 0; }
        .eyebrow { font-size: 0.78rem; font-weight: 700; letter-spacing: 0.14em; text-transform: uppercase; color: var(--accent); margin-bottom: 10px; display: block; }
        .section h2 { font-size: 2.1rem; font-weight: 800; letter-spacing: -0.02em; margin-bottom: 30px; }
 
        .panel { padding: 38px 40px; }
        .panel p { font-size: 1.02rem; color: var(--fg); max-width: 680px; }
        .panel p + p { margin-top: 16px; }
        .panel strong { color: var(--accent-dark); font-weight: 700; }
 
        /* ===== APPS ===== */
        .apps-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
        .app-card { padding: 32px 26px; transition: transform 0.4s cubic-bezier(0.23,1,0.32,1), box-shadow 0.4s ease; }
        .app-card:hover { transform: translateY(-8px); box-shadow: 0 25px 60px rgba(124,58,237,0.1), 0 8px 24px rgba(0,0,0,0.04); }
        .app-icon-wrap { width: 66px; height: 66px; position: relative; z-index: 2; margin-bottom: 18px; }
        .app-icon-wrap svg { width: 100%; height: 100%; filter: drop-shadow(0 4px 8px rgba(124,58,237,0.15)); }
        .app-card h3 { font-size: 1.2rem; font-weight: 700; position: relative; z-index: 2; margin-bottom: 4px; }
        .app-tag { font-size: 0.76rem; font-weight: 600; color: var(--accent); text-transform: uppercase; letter-spacing: 0.05em; position: relative; z-index: 2; display: block; margin-bottom: 12px; }
        .app-card p { font-size: 0.9rem; color: var(--muted); position: relative; z-index: 2; line-height: 1.55; }
 
        /* ===== FEATURES ===== */
        .features-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
        .feature { padding: 26px; display: flex; gap: 16px; align-items: flex-start; }
        .feature-icon {
            flex-shrink: 0; width: 42px; height: 42px; border-radius: 13px;
            background: linear-gradient(135deg, #c4b5fd, #8b5cf6); color: #fff;
            display: flex; align-items: center; justify-content: center; font-size: 1rem;
            box-shadow: 0 6px 16px rgba(139,92,246,0.25); position: relative; z-index: 2;
        }
        .feature-text { position: relative; z-index: 2; }
        .feature-text h4 { font-size: 0.96rem; font-weight: 700; margin-bottom: 4px; }
        .feature-text p { font-size: 0.85rem; color: var(--muted); line-height: 1.5; }
 
        /* ===== FOOTER ===== */
        footer { padding: 50px 0 70px; text-align: center; }
        .footer-panel { padding: 34px 30px; max-width: 480px; margin: 0 auto; }
        .footer-panel p { font-size: 0.88rem; color: var(--fg); line-height: 1.6; position: relative; z-index: 2; }
        .footer-panel a { color: var(--accent); font-weight: 600; text-decoration: underline; }
        .footer-links { display: flex; gap: 12px; justify-content: center; margin-top: 20px; position: relative; z-index: 2; flex-wrap: wrap; }
        .paypal-btn {
            display: inline-flex; align-items: center; gap: 8px; padding: 10px 22px; background: #0070ba; color: white;
            border-radius: 50px; text-decoration: none; font-weight: 600; font-size: 0.85rem;
            box-shadow: 0 4px 12px rgba(0, 112, 186, 0.3); transition: transform 0.2s ease;
        }
        .paypal-btn:hover { transform: translateY(-2px); }
        .github-btn {
            display: inline-flex; align-items: center; gap: 8px; padding: 10px 22px; background: var(--fg); color: white;
            border-radius: 50px; text-decoration: none; font-weight: 600; font-size: 0.85rem; transition: transform 0.2s ease;
        }
        .github-btn:hover { transform: translateY(-2px); }
        .made-with { margin-top: 30px; font-size: 0.72rem; color: var(--muted); opacity: 0.7; }
 
        /* ===== RESPONSIVE ===== */
        @media (max-width: 820px) {
            .logo-text { font-size: 2.6rem; }
            .lede { font-size: 1.1rem; }
            .apps-grid { grid-template-columns: 1fr; }
            .features-grid { grid-template-columns: 1fr 1fr; }
            .section h2 { font-size: 1.7rem; }
            .panel { padding: 28px 24px; }
        }
        @media (max-width: 480px) {
            .mascot-wrapper { width: 130px; height: 130px; }
            .logo-text { font-size: 2rem; letter-spacing: 0.1em; }
            .features-grid { grid-template-columns: 1fr; }
            .hero-actions { flex-direction: column; width: 100%; }
            .btn { justify-content: center; }
        }
 
        :focus-visible { outline: 2px solid var(--accent); outline-offset: 3px; }
        @media (prefers-reduced-motion: reduce) {
            .mascot-rabbit, .mascot-shadow, .blob, .scroll-hint i { animation: none !important; }
        }
    </style>
</head>
<body>
 
    <div class="bg-scene">
        <div class="blob blob-1"></div>
        <div class="blob blob-2"></div>
        <div class="blob blob-3"></div>
        <div class="blob blob-4"></div>
    </div>
    <div class="bg-grid"></div>
 
    <main>
 
        <!-- HERO -->
        <section class="hero">
            <div class="mascot-wrapper">
                <svg class="mascot-rabbit" viewBox="0 0 459.469 459.469" xmlns="http://www.w3.org/2000/svg">
                    <defs>
                        <linearGradient id="rabbitDark3" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#7c3aed"/><stop offset="100%" stop-color="#4c1d95"/></linearGradient>
                    </defs>
                    <path d="M390.052,183.518c-14.224-6.208-34.583-11.552-58.878-15.455c-4.906-0.789-9.525,2.55-10.314,7.459c-0.788,4.907,2.551,9.525,7.458,10.313c22.821,3.666,41.679,8.569,54.534,14.18c13.098,5.717,15.967,10.42,15.967,11.75c0,2.177-7.676,12.119-45.229,20.991c-4.855,1.147-15.772,3.295-16.027,3.354c-30.598,5.659-68.175,8.727-107.828,8.727c-39.653,0-77.23-3.069-107.829-8.728c-0.254-0.059-11.171-2.207-16.026-3.354c-37.553-8.872-45.229-18.814-45.229-20.991c0-1.33,2.869-6.033,15.967-11.75c12.854-5.61,31.711-10.514,54.532-14.18c4.907-0.789,8.247-5.406,7.458-10.314c-0.789-4.908-5.406-8.247-10.313-7.458c-24.295,3.903-44.655,9.248-58.877,15.455c-17.761,7.752-26.767,17.256-26.767,28.247c0,16.289,19.881,29.245,59.091,38.508c2.959,0.699,6.002,1.372,9.123,2.016v172.224c0,33.975,106.703,34.956,118.87,34.956s118.871-0.981,118.871-34.956V252.289c3.121-0.645,6.164-1.317,9.124-2.016c39.21-9.263,59.091-22.219,59.091-38.508C416.819,200.773,407.813,191.27,390.052,183.518z M330.604,423.834c-1.52,1.932-9.119,6.972-30.019,11.332c-19.485,4.064-44.647,6.303-70.852,6.303s-51.367-2.238-70.852-6.303c-20.9-4.36-28.499-9.4-30.019-11.332v-168.27c29.636,4.73,64.458,7.272,100.87,7.272s71.235-2.542,100.871-7.271V423.834z M153.749,205.151c-2.498-0.866-4.404-1.75-5.664-2.625c-4.081-2.837-9.69-1.828-12.527,2.254c-2.836,4.082-1.827,9.69,2.254,12.527c15.001,10.425,58.893,14.125,91.921,14.125s76.92-3.699,91.922-14.125c4.082-2.836,5.091-8.445,2.254-12.526c-2.837-4.083-8.445-5.091-12.526-2.255c-1.26,0.875-3.165,1.759-5.663,2.625l19.203-167.66c1.137-9.923-1.75-19.327-8.129-26.477C310.46,3.911,301.535,0,291.662,0c-19.573,0-37.317,15.9-39.555,35.442L231.72,213.427c-1.317,0.005-2.654,0.005-3.971,0L207.362,35.443C205.124,15.899,187.379,0,167.807,0c-9.872,0-18.797,3.911-25.132,11.012c-6.378,7.15-9.266,16.554-8.13,26.479L153.749,205.151z M269.99,37.491C271.2,26.926,281.125,18,291.663,18c4.672,0,8.827,1.774,11.701,4.995c2.917,3.27,4.223,7.691,3.679,12.448l-19.93,174.003c-3.123,0.506-6.49,0.979-10.087,1.41l14.374-125.49c0.566-4.938-2.979-9.4-7.917-9.965c-4.929-0.567-9.4,2.979-9.965,7.917l-14.799,129.204c-2.857,0.187-5.8,0.347-8.83,0.479L269.99,37.491z M156.107,22.994c2.873-3.22,7.028-4.994,11.701-4.994c10.537,0,20.462,8.926,21.672,19.491L209.582,213c-3.029-0.132-5.971-0.292-8.828-0.479L185.955,83.317c-0.566-4.938-5.029-8.484-9.965-7.917c-4.938,0.565-8.483,5.027-7.917,9.965l14.374,125.49c-3.595-0.431-6.965-0.904-10.087-1.41l-19.93-174.003C151.883,30.686,153.19,26.264,156.107,22.994z" fill="url(#rabbitDark3)"/>
                </svg>
                <div class="mascot-shadow"></div>
            </div>
 
            <h1 class="logo-text">CONEJO</h1>
            <p class="logo-sub">Agiliza tu labor docente</p>
            <p class="lede">Una puerta de entrada a las herramientas que te quitan tiempo de la burocracia, para dártelo de vuelta en el aula.</p>
 
            <div class="hero-actions">
                <a href="index.html" class="btn btn-primary"><i class="fa-solid fa-arrow-right"></i> Abrir CONEJO</a>
                <a href="https://github.com/conejoapps/conejoapps.github.io" target="_blank" class="btn btn-ghost"><i class="fa-brands fa-github"></i> Ver en GitHub</a>
            </div>
 
            <div class="scroll-hint"><span>Descubre más</span><i class="fa-solid fa-chevron-down"></i></div>
        </section>
 
        <!-- QUÉ ES -->
        <section class="section" id="que-es">
            <span class="eyebrow">El proyecto</span>
            <h2>¿Qué es CONEJO?</h2>
            <div class="liquid-glass panel">
                <p><strong>CONEJO no es una aplicación con funciones propias: es un lanzador.</strong> Reúne varias herramientas pensadas para el día a día docente bajo una misma puerta de entrada, para que no tengas que recordar direcciones sueltas ni acostumbrarte a interfaces distintas cada vez.</p>
                <p>Cada aplicación se abre dentro de CONEJO con un solo toque, y puedes volver al inicio en cualquier momento — con el gesto nativo de "atrás" en el móvil o con el botón flotante en el escritorio.</p>
            </div>
        </section>
 
        <!-- APLICACIONES -->
        <section class="section" id="apps">
            <span class="eyebrow">Dentro de CONEJO</span>
            <h2>Aplicaciones</h2>
            <div class="apps-grid">
 
                <div class="liquid-glass app-card">
                    <div class="app-icon-wrap">
                        <svg viewBox="0 0 400 400" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <defs>
                                <linearGradient id="rubricaGradR" x1="0%" y1="0%" x2="100%" y2="100%">
                                    <stop offset="0%" stop-color="#7c3aed"/>
                                    <stop offset="100%" stop-color="#4c1d95"/>
                                </linearGradient>
                            </defs>
                            <path d="M209.202 314C295.069 302.118 353.793 218.418 308.045 135.024C251.513 31.9842 61.8269 106.438 76.8437 219.371C86.6957 293.444 213.097 315.568 234.512 236.857C238.297 222.936 236.714 157.821 218.141 153.168C216.406 152.73 194.202 175.825 184.417 175.825C176.731 175.825 159.616 137.959 141.484 175.825" stroke="url(#rubricaGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                    </div>
                    <h3>Rubricat</h3>
                    <span class="app-tag">Evaluación flexible y rápida</span>
                    <p>Diseña y aplica rúbricas de evaluación sin fricción, pensadas para agilizar la corrección y dar un feedback claro al alumnado.</p>
                </div>
 
                <div class="liquid-glass app-card">
                    <div class="app-icon-wrap">
                        <svg viewBox="0 0 400 400" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <defs>
                                <linearGradient id="autoemilioGradR" x1="0%" y1="0%" x2="100%" y2="100%">
                                    <stop offset="0%" stop-color="#7c3aed"/>
                                    <stop offset="100%" stop-color="#4c1d95"/>
                                </linearGradient>
                            </defs>
                            <path d="M183.967 86.9455C252.62 12.0977 244.517 75.8891 263.023 85.1447C268.275 87.7725 275.324 85.0069 279.193 83.347" stroke="url(#autoemilioGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M219.968 106.121C241.931 80.0587 278.638 143.309 281.516 119.913" stroke="url(#autoemilioGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M157.258 63.7549C121.516 74.7106 105.852 117.17 121.513 148.401" stroke="url(#autoemilioGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M110.544 171.591C97.2219 190.533 110.121 194.598 125.903 188.961" stroke="url(#autoemilioGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M125.988 193.171C121.915 260.485 266.13 345.452 275.71 186.666" stroke="url(#autoemilioGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M176.84 149.305C192.345 148.711 256.228 140.836 268.06 147.641C290.76 160.692 276.999 199.124 249.499 202.832C225.999 206 214.898 146.506 217.717 146.902C224.482 147.853 222.319 190.253 209.856 202.832C182.676 230.265 152.592 179.295 168.142 153.514" stroke="url(#autoemilioGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M79 346.16C109.376 314.794 132.649 289 175.228 289C180.405 298.068 196.368 316.205 218.81 316.205C241.252 316.205 246.862 298.068 246.862 289C302.967 289 307.115 331.849 321 349" stroke="url(#autoemilioGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                    </div>
                    <h3>Autoemilio</h3>
                    <span class="app-tag">Correos automáticos personalizados</span>
                    <p>Genera comunicaciones para familias o alumnado a partir de lo que ya tienes, en vez de escribir el mismo correo una y otra vez.</p>
                </div>
 
                <div class="liquid-glass app-card">
                    <div class="app-icon-wrap">
                        <svg viewBox="0 0 400 400" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <defs>
                                <linearGradient id="dogGradR" x1="74" y1="211.658" x2="325" y2="176" gradientUnits="userSpaceOnUse">
                                    <stop offset="0%" stop-color="#7c3aed"/>
                                    <stop offset="1" stop-color="#4c1d95"/>
                                </linearGradient>
                            </defs>
                            <path d="M74 211.658C99.0457 142.251 155.836 87.1314 226.717 108.765C276.177 123.861 255.428 151.992 274.648 170.486C285.492 178.829 314.933 167.631 322.548 178.047C329.28 187.259 324.416 204.065 322.548 215.097C315.179 258.597 265.313 265 223.065 265" stroke="url(#dogGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M325 194C321.518 187.392 313.572 181.214 304 176" stroke="url(#dogGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M132.242 181.22C129.728 194.908 90.9731 288.143 131.095 296.086C205.608 306.73 196.665 221.971 196.665 169" stroke="url(#dogGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                            <path d="M234 168V173" stroke="url(#dogGradR)" stroke-width="16" stroke-linecap="round" stroke-linejoin="round"/>
                        </svg>
                    </div>
                    <h3>Programadog</h3>
                    <span class="app-tag">Creación de programaciones didácticas</span>
                    <p>Da estructura a tus programaciones docentes con menos trabajo de formato, para dedicar ese tiempo a lo que importa: el aula.</p>
                </div>
 
            </div>
        </section>
 
        <!-- CARACTERÍSTICAS -->
        <section class="section" id="caracteristicas">
            <span class="eyebrow">Por qué usarlo</span>
            <h2>Características</h2>
            <div class="features-grid">
 
                <div class="liquid-glass feature">
                    <div class="feature-icon"><i class="fa-solid fa-shield-halved"></i></div>
                    <div class="feature-text"><h4>No guarda tus datos</h4><p>Cada app funciona en tu propio navegador, sin cuentas ni servidores intermedios.</p></div>
                </div>
 
                <div class="liquid-glass feature">
                    <div class="feature-icon"><i class="fa-brands fa-github"></i></div>
                    <div class="feature-text"><h4>Código abierto</h4><p>Puedes revisar, modificar o descargar todo el proyecto libremente.</p></div>
                </div>
 
                <div class="liquid-glass feature">
                    <div class="feature-icon"><i class="fa-solid fa-download"></i></div>
                    <div class="feature-text"><h4>Funciona en local</h4><p>Descárgalo y ábrelo sin conexión, sin instalación ni dependencias.</p></div>
                </div>
 
                <div class="liquid-glass feature">
                    <div class="feature-icon"><i class="fa-solid fa-mobile-screen"></i></div>
                    <div class="feature-text"><h4>Se adapta a tu pantalla</h4><p>Pensado para usarse igual de bien en el móvil que en el ordenador.</p></div>
                </div>
 
                <div class="liquid-glass feature">
                    <div class="feature-icon"><i class="fa-solid fa-heart"></i></div>
                    <div class="feature-text"><h4>Gratis, sin anuncios</h4><p>Hecho para ahorrarte tiempo, no para venderte nada.</p></div>
                </div>
 
                <div class="liquid-glass feature">
                    <div class="feature-icon"><i class="fa-solid fa-layer-group"></i></div>
                    <div class="feature-text"><h4>Todo en un mismo sitio</h4><p>Varias herramientas, una sola puerta de entrada.</p></div>
                </div>
 
            </div>
        </section>
 
        <!-- FOOTER -->
        <footer>
            <div class="liquid-glass footer-panel">
                <p>Creado por Alberto Benavides y multitud de IAs. ¿Algún error, duda o sugerencia? Escribe a <a href="mailto:zulykat@gmail.com">zulykat@gmail.com</a>.</p>
                <div class="footer-links">
                    <a href="https://github.com/conejoapps/conejoapps.github.io" target="_blank" class="github-btn"><i class="fa-brands fa-github"></i> GitHub</a>
                    <a href="https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=zulykat@gmail.com&currency_code=EUR" target="_blank" class="paypal-btn"><i class="fa-brands fa-paypal"></i> Donar</a>
                </div>
            </div>
            <p class="made-with">CONEJO no almacena datos de usuario y es totalmente libre.</p>
        </footer>
 
    </main>
 
</body>
</html>
