<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FiveScore - Home</title>
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <style>
        :root {
            --primary: #2D3FE7;
            --secondary: #FF4B91;
            --accent: #00CFE8;
            --background: #0F172A;
            --card: rgba(255, 255, 255, 0.05);
            --text: #F8FAFC;
            --blur: blur(10px);
        }

        body {
            margin: 0;
            font-family: 'SF Pro Display', -apple-system, BlinkMacSystemFont, sans-serif;
            background: linear-gradient(125deg, #0F172A 0%, #1E293B 100%);
            color: var(--text);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* Animated Background */
        .background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            overflow: hidden;
        }

        .background-gradient {
            position: absolute;
            width: 150%;
            height: 150%;
            background: radial-gradient(circle at center, 
                rgba(45, 63, 231, 0.15) 0%,
                rgba(255, 75, 145, 0.15) 25%,
                rgba(0, 207, 232, 0.15) 50%);
            animation: rotate 20s linear infinite;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .hero-content {
            text-align: center;
            z-index: 1;
            max-width: 800px;
            padding: 2rem;
        }

        .hero-title {
            font-size: 5rem;
            font-weight: 800;
            margin: 0;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: titleSlide 1s ease forwards;
            opacity: 0;
        }

        .hero-subtitle {
            font-size: 1.5rem;
            margin: 1.5rem 0;
            opacity: 0;
            animation: fadeIn 1s ease 0.5s forwards;
        }

        /* Floating Sports Icons */
        .floating-icons {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .sport-icon {
            position: absolute;
            font-size: 2rem;
            opacity: 0;
            animation: float 20s linear infinite;
        }

        .sport-icon:nth-child(1) { top: 20%; left: 20%; animation-delay: 0s; }
        .sport-icon:nth-child(2) { top: 30%; right: 25%; animation-delay: 2s; }
        .sport-icon:nth-child(3) { bottom: 30%; left: 25%; animation-delay: 4s; }
        .sport-icon:nth-child(4) { bottom: 20%; right: 20%; animation-delay: 6s; }

        /* CTA Button */
        .cta-button {
            padding: 1.2rem 3rem;
            font-size: 1.2rem;
            font-weight: 600;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            border: none;
            border-radius: 50px;
            color: white;
            cursor: pointer;
            transition: all 0.3s ease;
            opacity: 0;
            animation: fadeIn 1s ease 1s forwards;
            position: relative;
            overflow: hidden;
        }

        .cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }

        .cta-button::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255,255,255,0.1), transparent);
            transform: rotate(45deg);
            animation: shimmer 3s infinite;
        }

        /* Animations */
        @keyframes titleSlide {
            from {
                transform: translateY(-20px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        @keyframes fadeIn {
            to { opacity: 1; }
        }

        @keyframes float {
            0% {
                transform: translate(0, 0) rotate(0deg);
                opacity: 0;
            }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% {
                transform: translate(var(--moveX, 100px), var(--moveY, 100px)) rotate(360deg);
                opacity: 0;
            }
        }

        @keyframes shimmer {
            0% { transform: translate(-50%, -50%) rotate(45deg); }
            100% { transform: translate(150%, 150%) rotate(45deg); }
        }

        @keyframes rotate {
            0% { transform: translate(-25%, -25%) rotate(0deg); }
            100% { transform: translate(-25%, -25%) rotate(360deg); }
        }

        /* Scroll Indicator */
        .scroll-indicator {
            position: absolute;
            bottom: 2rem;
            left: 50%;
            transform: translateX(-50%);
            opacity: 0;
            animation: fadeIn 1s ease 1.5s forwards;
        }

        .scroll-indicator::before {
            content: '';
            display: block;
            width: 20px;
            height: 20px;
            border-right: 2px solid var(--text);
            border-bottom: 2px solid var(--text);
            transform: rotate(45deg);
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0) rotate(45deg); }
            40% { transform: translateY(-10px) rotate(45deg); }
            60% { transform: translateY(-5px) rotate(45deg); }
        }
    </style>
</head>
<body>
    <!-- Animated Background -->
    <div class="background">
        <div class="background-gradient"></div>
    </div>

    <!-- Hero Section -->
    <section class="hero">
        <div class="floating-icons">
            <div class="sport-icon">🏏</div>
            <div class="sport-icon">🏎️</div>
            <div class="sport-icon">⚽</div>
            <div class="sport-icon">♟️</div>
        </div>

        <div class="hero-content">
            <h1 class="hero-title">FiveScore</h1>
            <p class="hero-subtitle">Your gateway to live scores, stats, and updates for Cricket, F1, Soccer, Basketball, and Chess</p>
            <button class="cta-button">Get Started</button>
        </div>

        <div class="scroll-indicator"></div>
    </section>

    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        // Initialize AOS
        AOS.init({
            duration: 1000,
            easing: 'ease-out-cubic'
        });

        // Random movement for floating icons
        document.querySelectorAll('.sport-icon').forEach(icon => {
            setInterval(() => {
                icon.style.setProperty('--moveX', `${Math.random() * 200 - 100}px`);
                icon.style.setProperty('--moveY', `${Math.random() * 200 - 100}px`);
            }, 20000);
        });

        // Smooth scroll for CTA button
        document.querySelector('.cta-button').addEventListener('click', () => {
            // Add your navigation logic here
        });
        
        <
    </script>
</body>
</html>
