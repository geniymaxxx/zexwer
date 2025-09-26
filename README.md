<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Zexwer Network</title>
    <style>
        :root {
            --primary-color: #00ff88;
            --secondary-color: #0088ff;
            --bg-color: #0a0a0a;
            --text-size: 6rem;
            --accent-color: #ff0088;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: var(--bg-color);
            color: white;
            font-family: 'Arial', sans-serif;
            overflow-x: hidden;
            min-height: 100vh;
        }
        
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(10, 10, 10, 0.9);
            backdrop-filter: blur(10px);
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            border-bottom: 2px solid var(--primary-color);
        }
        
        .logo {
            font-size: 2rem;
            font-weight: bold;
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .nav-links {
            display: flex;
            gap: 2rem;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
            transition: color 0.3s ease;
            font-weight: 500;
            padding: 0.5rem 1rem;
            border-radius: 5px;
        }
        
        .nav-links a:hover, .nav-links a.active {
            color: var(--primary-color);
            background: rgba(0, 255, 136, 0.1);
        }
        
        .tab-content {
            display: none;
            padding: 100px 2rem 2rem 2rem;
            min-height: 100vh;
        }
        
        .tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            padding: 0 2rem;
        }
        
        .main-title {
            font-size: var(--text-size);
            font-weight: 900;
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color), var(--accent-color));
            background-size: 200% 200%;
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: gradientShift 3s ease-in-out infinite;
            margin-bottom: 1rem;
            text-shadow: 0 0 30px rgba(0, 255, 136, 0.5);
        }
        
        .subtitle {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            opacity: 0.8;
        }
        
        .cta-button {
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
            color: black;
            border: none;
            padding: 1rem 2rem;
            font-size: 1.2rem;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }
        
        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(0, 255, 136, 0.3);
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .feature-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 2rem;
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: transform 0.3s ease, border-color 0.3s ease;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
            border-color: var(--primary-color);
        }
        
        .feature-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .proxies-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .proxy-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 2rem;
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: transform 0.3s ease, border-color 0.3s ease;
        }
        
        .proxy-card:hover {
            transform: translateY(-5px);
            border-color: var(--primary-color);
        }
        
        .proxy-header {
            display: flex;
            align-items: center;
            margin-bottom: 1rem;
        }
        
        .proxy-icon {
            font-size: 2.5rem;
            margin-right: 1rem;
        }
        
        .proxy-link {
            display: inline-block;
            background: var(--primary-color);
            color: black;
            padding: 0.5rem 1rem;
            border-radius: 5px;
            text-decoration: none;
            font-weight: bold;
            margin-top: 1rem;
            transition: transform 0.3s ease;
        }
        
        .proxy-link:hover {
            transform: translateX(5px);
        }
        
        .proxy-stats {
            display: flex;
            justify-content: space-between;
            margin-top: 1rem;
            font-size: 0.9rem;
            opacity: 0.8;
        }
        
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
        
        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: var(--primary-color);
            border-radius: 50%;
            filter: blur(1px);
            animation: float linear infinite;
        }
        
        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        @keyframes float {
            to { transform: translateY(-100vh) rotate(360deg); }
        }
        
        .controls {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: rgba(0, 0, 0, 0.8);
            padding: 15px;
            border-radius: 10px;
            border: 1px solid var(--primary-color);
            z-index: 1000;
        }
        
        .color-options {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }
        
        .color-option {
            width: 25px;
            height: 25px;
            border-radius: 50%;
            cursor: pointer;
            border: 2px solid transparent;
        }
        
        .color-option.active {
            border-color: white;
        }
        
        .toggle-controls {
            background: var(--primary-color);
            color: black;
            border: none;
            padding: 5px 10px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            margin-bottom: 10px;
        }
        
        footer {
            background: rgba(0, 0, 0, 0.9);
            padding: 2rem;
            text-align: center;
            border-top: 1px solid var(--primary-color);
        }
        
        /* Адаптивность */
        @media (max-width: 768px) {
            .main-title {
                font-size: 3rem;
            }
            
            .nav-links {
                display: none;
            }
            
            .features-grid, .proxies-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Навигация -->
    <nav class="navbar">
        <div class="logo">Zexwer Network</div>
        <div class="nav-links">
            <a href="#home" class="nav-tab active" data-tab="home">Home</a>
            <a href="#features" class="nav-tab" data-tab="features">Features</a>
            <a href="#proxies" class="nav-tab" data-tab="proxies">Proxies</a>
            <a href="#about" class="nav-tab" data-tab="about">About</a>
        </div>
    </nav>

    <!-- Вкладка Home -->
    <section id="home" class="tab-content active">
        <div class="hero">
            <h1 class="main-title">Zexwer Network</h1>
            <p class="subtitle">Innovative Solutions for the Digital World</p>
            <a href="#features" class="cta-button tab-switch" data-tab="features">Learn More</a>
        </div>
    </section>

    <!-- Вкладка Features -->
    <section id="features" class="tab-content">
        <div style="padding: 100px 2rem 2rem 2rem;">
            <h2 style="text-align: center; margin-bottom: 3rem; font-size: 3rem;">Our Features</h2>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">⚡</div>
                    <h3>High Speed</h3>
                    <p>Maximum performance and responsiveness for all your needs</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🔒</div>
                    <h3>Security</h3>
                    <p>Advanced data protection and privacy features</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🌐</div>
                    <h3>Availability</h3>
                    <p>Worldwide service available 24/7</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Вкладка Proxies -->
    <section id="proxies" class="tab-content">
        <div style="padding: 100px 2rem 2rem 2rem;">
            <h2 style="text-align: center; margin-bottom: 3rem; font-size: 3rem;">Premium Proxy Services</h2>
            <div class="proxies-grid">
                <div class="proxy-card">
                    <div class="proxy-header">
                        <div class="proxy-icon">🌌</div>
                        <div>
                            <h3>Space Proxy</h3>
                            <p>High-speed anonymous browsing</p>
                        </div>
                    </div>
                    <p>Space Proxy offers lightning-fast connection speeds with military-grade encryption. Perfect for streaming and gaming.</p>
                    <div class="proxy-stats">
                        <span>Speed: 1.2 Gbps</span>
                        <span>Servers: 250+</span>
                    </div>
                    <a href="https://gointospace.app" class="proxy-link" target="_blank">Visit Space Proxy</a>
                </div>
                
                <div class="proxy-card">
                    <div class="proxy-header">
                        <div class="proxy-icon">👻</div>
                        <div>
                            <h3>Ghost Proxy</h3>
                            <p>Complete anonymity solution</p>
                        </div>
                    </div>
                    <p>Ghost Proxy ensures your online activities remain completely untraceable with advanced stealth technology.</p>
                    <div class="proxy-stats">
                        <span>Speed: 980 Mbps</span>
                        <span>Servers: 180+</span>
                    </div>
                    <a href="https://earthmowers.gabrielamelopropiedades.cl/" class="proxy-link" target="_blank">Visit Ghost Proxy</a>
                </div>
                
                <div class="proxy-card">
                    <div class="proxy-header">
                        <div class="proxy-icon">🔰</div>
                        <div>
                            <h3>Utopia Proxy</h3>
                            <p>Ultimate freedom network</p>
                        </div>
                    </div>
                    <p>Utopia Proxy provides unrestricted access to content worldwide with zero logging policy.</p>
                    <div class="proxy-stats">
                        <span>Speed: 1.5 Gbps</span>
                        <span>Servers: 300+</span>
                    </div>
                    <a href="https://recap.grade.kredytlinia.pl/" class="proxy-link" target="_blank">Visit Utopia Proxy</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Вкладка About -->
    <section id="about" class="tab-content">
        <div style="padding: 100px 2rem 2rem 2rem; max-width: 800px; margin: 0 auto;">
            <h2 style="text-align: center; margin-bottom: 3rem; font-size: 3rem;">About Zexwer Network</h2>
            <div class="feature-card">
                <h3>Our Mission</h3>
                <p>Zexwer Network is dedicated to providing cutting-edge digital solutions that empower users worldwide. We believe in internet freedom, privacy, and accessibility for all.</p>
                
                <h3 style="margin-top: 2rem;">Why Choose Us?</h3>
                <ul style="margin-left: 1.5rem; margin-top: 1rem;">
                    <li>Advanced security protocols</li>
                    <li>24/7 customer support</li>
                    <li>Global server network</li>
                    <li>User-friendly interfaces</li>
                    <li>Regular updates and improvements</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Футер -->
    <footer>
        <p>© 2024 Zexwer Network. All rights reserved.</p>
        <p>Contact: contact@zexwer.network</p>
    </footer>

    <!-- Частицы -->
    <div class="particles" id="particles"></div>

    <!-- Панель управления -->
    <div class="controls">
        <button class="toggle-controls" id="toggleParticles">Particles: On</button>
        <div class="color-options">
            <div class="color-option active" style="background: linear-gradient(45deg, #00ff88, #0088ff);" data-primary="#00ff88" data-secondary="#0088ff" data-accent="#ff0088"></div>
            <div class="color-option" style="background: linear-gradient(45deg, #ff0088, #8800ff);" data-primary="#ff0088" data-secondary="#8800ff" data-accent="#00ff88"></div>
            <div class="color-option" style="background: linear-gradient(45deg, #0088ff, #ff8800);" data-primary="#0088ff" data-secondary="#ff8800" data-accent="#88ff00"></div>
            <div class="color-option" style="background: linear-gradient(45deg, #88ff00, #ff0088);" data-primary="#88ff00" data-secondary="#ff0088" data-accent="#0088ff"></div>
        </div>
    </div>

    <script>
        // Создание частиц
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 100;
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.classList.add('particle');
                
                const startX = Math.random() * 100;
                const duration = 20 + Math.random() * 30;
                const delay = Math.random() * 5;
                const size = 2 + Math.random() * 3;
                
                particle.style.left = `${startX}vw`;
                particle.style.bottom = `-10px`;
                particle.style.animationDuration = `${duration}s`;
                particle.style.animationDelay = `${delay}s`;
                particle.style.width = `${size}px`;
                particle.style.height = `${size}px`;
                
                particlesContainer.appendChild(particle);
            }
        }

        // Управление вкладками
        function setupTabs() {
            const tabs = document.querySelectorAll('.nav-tab');
            const tabContents = document.querySelectorAll('.tab-content');
            
            tabs.forEach(tab => {
                tab.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    // Убираем активный класс у всех вкладок
                    tabs.forEach(t => t.classList.remove('active'));
                    tabContents.forEach(content => content.classList.remove('active'));
                    
                    // Добавляем активный класс к текущей вкладке
                    this.classList.add('active');
                    const tabId = this.getAttribute('data-tab');
                    document.getElementById(tabId).classList.add('active');
                    
                    // Прокрутка к верху страницы
                    window.scrollTo(0, 0);
                });
            });
            
            // Обработка кнопок переключения вкладок
            document.querySelectorAll('.tab-switch').forEach(button => {
                button.addEventListener('click', function(e) {
                    e.preventDefault();
                    const tabId = this.getAttribute('data-tab');
                    
                    tabs.forEach(t => t.classList.remove('active'));
                    tabContents.forEach(content => content.classList.remove('active'));
                    
                    document.querySelector(`[data-tab="${tabId}"]`).classList.add('active');
                    document.getElementById(tabId).classList.add('active');
                    
                    window.scrollTo(0, 0);
                });
            });
        }

        // Обновление цветов частиц
        function updateParticlesColor() {
            const particles = document.querySelectorAll('.particle');
            const primaryColor = getComputedStyle(document.documentElement).getPropertyValue('--primary-color').trim();
            
            particles.forEach(particle => {
                particle.style.background = primaryColor;
            });
        }

        // Управление настройками
        document.addEventListener('DOMContentLoaded', function() {
            createParticles();
            setupTabs();
            
            const toggleBtn = document.getElementById('toggleParticles');
            const colorOptions = document.querySelectorAll('.color-option');
            const particlesContainer = document.getElementById('particles');
            
            // Переключение частиц
            toggleBtn.addEventListener('click', function() {
                if (particlesContainer.style.display !== 'none') {
                    particlesContainer.style.display = 'none';
                    this.textContent = 'Particles: Off';
                } else {
                    particlesContainer.style.display = 'block';
                    this.textContent = 'Particles: On';
                }
            });
            
            // Смена цветовой схемы
            colorOptions.forEach(option => {
                option.addEventListener('click', function() {
                    colorOptions.forEach(opt => opt.classList.remove('active'));
                    this.classList.add('active');
                    
                    const primary = this.getAttribute('data-primary');
                    const secondary = this.getAttribute('data-secondary');
                    const accent = this.getAttribute('data-accent');
                    
                    document.documentElement.style.setProperty('--primary-color', primary);
                    document.documentElement.style.setProperty('--secondary-color', secondary);
                    document.documentElement.style.setProperty('--accent-color', accent);
                    
                    updateParticlesColor();
                });
            });
        });

        // Анимация появления при скролле
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Наблюдаем за карточками
        document.querySelectorAll('.feature-card, .proxy-card').forEach(card => {
            card.style.opacity = '0';
            card.style.transform = 'translateY(50px)';
            card.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
            observer.observe(card);
        });
    </script>
</body>
</html>
