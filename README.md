<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ABISHEK K.S - Visiting Card</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link
        href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Orbitron:wght@500;700;900&family=JetBrains+Mono:wght@400;500;600&display=swap"
        rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            flex-direction: column;
            gap: 30px;
        }

        .card-container {
            perspective: 2000px;
            width: 1050px;
            height: 600px;
            position: relative;
        }

        .card-flipper {
            width: 100%;
            height: 100%;
            position: relative;
            transform-style: preserve-3d;
            transition: transform 0.8s cubic-bezier(0.4, 0.0, 0.2, 1);
        }

        .card-container.flipped .card-flipper {
            transform: rotateY(180deg);
        }

        .card-face {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            -webkit-backface-visibility: hidden;
        }

        .card-back {
            transform: rotateY(180deg);
        }

        .visiting-card {
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #0a0e27 0%, #1a1d3a 100%);
            border-radius: 24px;
            position: relative;
            overflow: hidden;
            box-shadow:
                0 25px 50px -12px rgba(0, 0, 0, 0.8),
                0 0 0 1px rgba(59, 130, 246, 0.1),
                inset 0 0 0 1px rgba(59, 130, 246, 0.05);
        }

        /* Subtle circuit pattern background */
        .card-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0.03;
            background-image:
                repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(59, 130, 246, 0.3) 2px, rgba(59, 130, 246, 0.3) 4px),
                repeating-linear-gradient(90deg, transparent, transparent 2px, rgba(59, 130, 246, 0.3) 2px, rgba(59, 130, 246, 0.3) 4px);
            background-size: 40px 40px;
        }

        /* Accent line */
        .accent-top {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg,
                    transparent 0%,
                    #3b82f6 20%,
                    #06b6d4 50%,
                    #3b82f6 80%,
                    transparent 100%);
            box-shadow: 0 0 20px rgba(59, 130, 246, 0.5);
        }

        .accent-bottom {
            position: absolute;
            bottom: 0;
            right: 0;
            width: 60%;
            height: 2px;
            background: linear-gradient(90deg,
                    transparent 0%,
                    #3b82f6 50%,
                    transparent 100%);
            opacity: 0.3;
        }

        /* Content container */
        .card-content {
            position: relative;
            z-index: 10;
            padding: 60px 80px;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        /* FRONT SIDE STYLES */
        .header {
            border-bottom: 1px solid rgba(59, 130, 246, 0.1);
            padding-bottom: 30px;
        }

        .name {
            font-family: 'Orbitron', sans-serif;
            font-size: 56px;
            font-weight: 900;
            color: #ffffff;
            letter-spacing: 2px;
            margin-bottom: 12px;
            text-shadow: 0 0 30px rgba(59, 130, 246, 0.3);
            background: linear-gradient(135deg, #ffffff 0%, #e0f2fe 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .title {
            font-size: 22px;
            font-weight: 500;
            color: #3b82f6;
            letter-spacing: 1px;
            margin-bottom: 8px;
        }

        .college {
            font-size: 16px;
            font-weight: 400;
            color: #94a3b8;
            letter-spacing: 0.5px;
        }

        .contact-section {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 24px;
            margin-top: 20px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 16px;
            padding: 16px 20px;
            background: rgba(59, 130, 246, 0.03);
            border-radius: 12px;
            border: 1px solid rgba(59, 130, 246, 0.1);
            transition: all 0.3s ease;
        }

        .contact-item:hover {
            background: rgba(59, 130, 246, 0.08);
            border-color: rgba(59, 130, 246, 0.3);
            transform: translateX(5px);
        }

        .icon {
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #3b82f6;
            font-size: 20px;
        }

        .contact-label {
            font-size: 11px;
            font-weight: 600;
            color: #64748b;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 4px;
        }

        .contact-value {
            font-size: 15px;
            font-weight: 500;
            color: #e2e8f0;
            letter-spacing: 0.3px;
        }

        /* BACK SIDE STYLES */
        .back-header {
            text-align: center;
            border-bottom: 1px solid rgba(59, 130, 246, 0.15);
            padding-bottom: 25px;
            margin-bottom: 30px;
        }

        .back-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 28px;
            font-weight: 700;
            color: #ffffff;
            letter-spacing: 1.5px;
            margin-bottom: 8px;
            text-shadow: 0 0 20px rgba(59, 130, 246, 0.3);
        }

        .back-subtitle {
            font-size: 14px;
            font-weight: 500;
            color: #64748b;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .info-section {
            margin-bottom: 30px;
        }

        .section-title {
            font-size: 13px;
            font-weight: 700;
            color: #3b82f6;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .section-title::before {
            content: '';
            width: 4px;
            height: 16px;
            background: linear-gradient(135deg, #3b82f6, #06b6d4);
            border-radius: 2px;
            box-shadow: 0 0 10px rgba(59, 130, 246, 0.5);
        }

        .info-card {
            background: rgba(59, 130, 246, 0.04);
            border: 1px solid rgba(59, 130, 246, 0.12);
            border-radius: 12px;
            padding: 20px 24px;
            margin-bottom: 12px;
            transition: all 0.3s ease;
        }

        .info-card:hover {
            background: rgba(59, 130, 246, 0.08);
            border-color: rgba(59, 130, 246, 0.25);
            transform: translateX(5px);
        }

        .info-card-title {
            font-size: 17px;
            font-weight: 700;
            color: #e2e8f0;
            margin-bottom: 6px;
            letter-spacing: 0.5px;
        }

        .info-card-subtitle {
            font-size: 14px;
            font-weight: 500;
            color: #94a3b8;
            letter-spacing: 0.3px;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 12px;
            margin-top: 10px;
        }

        .skill-badge {
            background: rgba(59, 130, 246, 0.08);
            border: 1px solid rgba(59, 130, 246, 0.2);
            border-radius: 8px;
            padding: 12px 8px;
            text-align: center;
            transition: all 0.3s ease;
            cursor: default;
        }

        .skill-badge:hover {
            background: rgba(59, 130, 246, 0.15);
            border-color: rgba(59, 130, 246, 0.4);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(59, 130, 246, 0.2);
        }

        .skill-name {
            font-family: 'JetBrains Mono', monospace;
            font-size: 13px;
            font-weight: 600;
            color: #3b82f6;
            letter-spacing: 0.5px;
        }

        /* Decorative corner */
        .corner-decoration {
            position: absolute;
            bottom: 60px;
            right: 80px;
            width: 120px;
            height: 120px;
            opacity: 0.08;
        }

        .corner-decoration::before,
        .corner-decoration::after {
            content: '';
            position: absolute;
            border: 2px solid #3b82f6;
        }

        .corner-decoration::before {
            top: 0;
            right: 0;
            width: 80px;
            height: 80px;
            border-left: none;
            border-bottom: none;
        }

        .corner-decoration::after {
            bottom: 0;
            left: 0;
            width: 60px;
            height: 60px;
            border-right: none;
            border-top: none;
        }

        /* Flip button */
        .flip-btn {
            padding: 14px 32px;
            background: linear-gradient(135deg, #3b82f6 0%, #2563eb 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-family: 'Inter', sans-serif;
            font-size: 15px;
            font-weight: 600;
            cursor: pointer;
            box-shadow: 0 10px 25px -5px rgba(59, 130, 246, 0.4);
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .flip-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 30px -5px rgba(59, 130, 246, 0.6);
        }

        .flip-btn:active {
            transform: translateY(0);
        }

        /* Control buttons */
        .controls {
            display: flex;
            gap: 15px;
            align-items: center;
        }

        .download-btn {
            padding: 14px 28px;
            background: linear-gradient(135deg, #059669 0%, #047857 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-family: 'Inter', sans-serif;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            box-shadow: 0 10px 25px -5px rgba(5, 150, 105, 0.4);
            transition: all 0.3s ease;
        }

        .download-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 30px -5px rgba(5, 150, 105, 0.6);
        }

        /* Print styles */
        @media print {
            body {
                background: white;
                padding: 0;
                gap: 50px;
            }

            .visiting-card {
                box-shadow: none;
                page-break-inside: avoid;
            }

            .controls {
                display: none;
            }

            .card-container {
                page-break-after: always;
            }

            .card-flipper {
                transform: none !important;
            }

            .card-back {
                transform: none;
                page-break-before: always;
            }
        }

        /* Responsive design */
        @media (max-width: 1100px) {
            .card-container {
                width: 90vw;
                height: calc(90vw * 0.57);
            }

            .card-content {
                padding: 40px 50px;
            }

            .name {
                font-size: 42px;
            }

            .title {
                font-size: 18px;
            }

            .contact-section {
                grid-template-columns: 1fr;
            }

            .skills-grid {
                grid-template-columns: repeat(3, 1fr);
            }
        }
    </style>
</head>

<body>
    <div class="card-container" id="cardContainer">
        <div class="card-flipper">
            <!-- FRONT SIDE -->
            <div class="card-face card-front">
                <div class="visiting-card">
                    <div class="card-bg"></div>
                    <div class="accent-top"></div>
                    <div class="accent-bottom"></div>

                    <div class="card-content">
                        <div class="header">
                            <h1 class="name">ABISHEK K.S</h1>
                            <div class="title">B.Tech – Information Technology</div>
                            <div class="college">Panimalar Engineering College (2024–2028)</div>
                        </div>

                        <div class="contact-section">
                            <div class="contact-item">
                                <div class="icon">📞</div>
                                <div>
                                    <div class="contact-label">Phone</div>
                                    <div class="contact-value">+91 9043052875</div>
                                </div>
                            </div>

                            <div class="contact-item">
                                <div class="icon">📧</div>
                                <div>
                                    <div class="contact-label">Email</div>
                                    <div class="contact-value">abishekks9207@gmai.com</div>
                                </div>
                            </div>

                            <div class="contact-item">
                                <div class="icon">📍</div>
                                <div>
                                    <div class="contact-label">Location</div>
                                    <div class="contact-value">Tiruvallur, Tamil Nadu</div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="corner-decoration"></div>
                </div>
            </div>

            <!-- BACK SIDE -->
            <div class="card-face card-back">
                <div class="visiting-card">
                    <div class="card-bg"></div>
                    <div class="accent-top"></div>
                    <div class="accent-bottom"></div>

                    <div class="card-content">
                        <div class="back-header">
                            <div class="back-title">PROFESSIONAL PROFILE</div>
                            <div class="back-subtitle">Tech Identity & Expertise</div>
                        </div>

                        <div class="info-section">
                            <div class="section-title">🎓 Education</div>
                            <div class="info-card">
                                <div class="info-card-title">Panimalar Engineering College</div>
                                <div class="info-card-subtitle">B.Tech – Information Technology (2024 – 2028)</div>
                            </div>
                        </div>

                        <div class="info-section">
                            <div class="section-title">💼 Experience</div>
                            <div class="info-card">
                                <div class="info-card-title">Java Full Stack Intern</div>
                                <div class="info-card-subtitle">Career School & HR Guidance, Chennai</div>
                            </div>
                        </div>

                        <div class="info-section">
                            <div class="section-title">⚡ Technical Skills</div>
                            <div class="skills-grid">
                                <div class="skill-badge">
                                    <div class="skill-name">Python</div>
                                </div>
                                <div class="skill-badge">
                                    <div class="skill-name">Java</div>
                                </div>
                                <div class="skill-badge">
                                    <div class="skill-name">HTML</div>
                                </div>
                                <div class="skill-badge">
                                    <div class="skill-name">React.js</div>
                                </div>
                                <div class="skill-badge">
                                    <div class="skill-name">MongoDB</div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="corner-decoration"></div>
                </div>
            </div>
        </div>
    </div>

    <div class="controls">
        <button class="flip-btn" id="flipBtn">
            <span id="flipIcon">🔄</span>
            <span id="flipText">Flip to Back</span>
        </button>
        <button class="download-btn" onclick="window.print()">🖨️ Print Both Sides</button>
    </div>

    <script>
        const cardContainer = document.getElementById('cardContainer');
        const flipBtn = document.getElementById('flipBtn');
        const flipText = document.getElementById('flipText');
        let isFlipped = false;

        flipBtn.addEventListener('click', () => {
            isFlipped = !isFlipped;
            cardContainer.classList.toggle('flipped');
            flipText.textContent = isFlipped ? 'Flip to Front' : 'Flip to Back';
        });

        // Add subtle hover glow effect to both cards
        const cards = document.querySelectorAll('.visiting-card');
        cards.forEach(card => {
            card.addEventListener('mousemove', (e) => {
                const rect = card.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;

                card.style.background = `
                    radial-gradient(circle at ${x}px ${y}px, rgba(59, 130, 246, 0.08) 0%, transparent 50%),
                    linear-gradient(135deg, #0a0e27 0%, #1a1d3a 100%)
                `;
            });

            card.addEventListener('mouseleave', () => {
                card.style.background = 'linear-gradient(135deg, #0a0e27 0%, #1a1d3a 100%)';
            });
        });
    </script>
</body>

</html>
