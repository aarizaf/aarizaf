<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Perfil de GitHub</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'SF Pro Display', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #0d1117 0%, #161b22 50%, #21262d 100%);
            color: #e6edf3;
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        .header {
            text-align: center;
            margin-bottom: 4rem;
            position: relative;
        }

        .profile-image {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 4px solid #58a6ff;
            margin: 0 auto 2rem;
            background: linear-gradient(45deg, #58a6ff, #7c3aed);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            animation: float 3s ease-in-out infinite;
            box-shadow: 0 20px 40px rgba(88, 166, 255, 0.3);
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        .name {
            font-size: 3rem;
            font-weight: 800;
            background: linear-gradient(45deg, #58a6ff, #7c3aed, #f472b6);
            background-size: 200% 200%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradient 3s ease infinite;
            margin-bottom: 1rem;
        }

        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .title {
            font-size: 1.5rem;
            color: #7d8590;
            margin-bottom: 1rem;
        }

        .bio {
            font-size: 1.2rem;
            max-width: 600px;
            margin: 0 auto 2rem;
            color: #c9d1d9;
        }

        .section {
            margin-bottom: 4rem;
            opacity: 0;
            transform: translateY(50px);
            animation: fadeInUp 0.8s ease forwards;
        }

        .section:nth-child(2) { animation-delay: 0.2s; }
        .section:nth-child(3) { animation-delay: 0.4s; }
        .section:nth-child(4) { animation-delay: 0.6s; }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .section-title {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 2rem;
            text-align: center;
            position: relative;
        }

        .section-title::after {
            content: '';
            width: 80px;
            height: 4px;
            background: linear-gradient(45deg, #58a6ff, #7c3aed);
            display: block;
            margin: 1rem auto;
            border-radius: 2px;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .skill-category {
            background: rgba(48, 54, 61, 0.8);
            padding: 2rem;
            border-radius: 20px;
            border: 1px solid rgba(88, 166, 255, 0.2);
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .skill-category::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(88, 166, 255, 0.1), transparent);
            transition: left 0.5s ease;
        }

        .skill-category:hover::before {
            left: 100%;
        }

        .skill-category:hover {
            transform: translateY(-10px);
            border-color: #58a6ff;
            box-shadow: 0 20px 40px rgba(88, 166, 255, 0.2);
        }

        .skill-category h3 {
            font-size: 1.5rem;
            margin-bottom: 1.5rem;
            color: #58a6ff;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .skill-category .icon {
            font-size: 1.8rem;
        }

        .skills {
            display: flex;
            flex-wrap: wrap;
            gap: 0.8rem;
        }

        .skill {
            background: linear-gradient(45deg, #238636, #2ea043);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 25px;
            font-size: 0.9rem;
            font-weight: 600;
            transition: all 0.3s ease;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .skill-icon {
            width: 20px;
            height: 20px;
            filter: brightness(0) invert(1);
        }

        .skill:hover {
            transform: scale(1.1);
            box-shadow: 0 5px 15px rgba(46, 160, 67, 0.4);
        }

        .backend-skill {
            background: linear-gradient(45deg, #7c3aed, #8b5cf6);
        }

        .backend-skill .skill-icon {
            filter: brightness(0) invert(1);
        }

        .skill:hover .skill-icon {
            transform: rotate(360deg);
            transition: transform 0.5s ease;
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .stat-card {
            background: rgba(48, 54, 61, 0.6);
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            border: 1px solid rgba(88, 166, 255, 0.3);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(45deg, #58a6ff, #7c3aed, #f472b6);
            background-size: 200% 200%;
            animation: gradient 3s ease infinite;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            border-color: #58a6ff;
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: 800;
            color: #58a6ff;
            margin-bottom: 0.5rem;
        }

        .stat-label {
            color: #7d8590;
            font-weight: 500;
        }

        .contact {
            text-align: center;
            background: rgba(48, 54, 61, 0.6);
            padding: 3rem;
            border-radius: 20px;
            border: 1px solid rgba(88, 166, 255, 0.3);
            margin-top: 3rem;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 2rem;
        }

        .social-link {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 60px;
            height: 60px;
            background: linear-gradient(45deg, #58a6ff, #7c3aed);
            border-radius: 50%;
            color: white;
            text-decoration: none;
            font-size: 1.5rem;
            transition: all 0.3s ease;
        }

        .social-link:hover {
            transform: scale(1.2) rotate(10deg);
            box-shadow: 0 10px 25px rgba(88, 166, 255, 0.4);
        }

        .typing-animation {
            border-right: 2px solid #58a6ff;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 50% { border-color: #58a6ff; }
            51%, 100% { border-color: transparent; }
        }

        @media (max-width: 768px) {
            .name { font-size: 2rem; }
            .section-title { font-size: 2rem; }
            .skills-grid { grid-template-columns: 1fr; }
            .social-links { flex-wrap: wrap; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header Section -->
        <header class="header">
            <div class="profile-image">
                👨‍💻
            </div>
            <h1 class="name">Tu Nombre</h1>
            <p class="title typing-animation">Desarrollador Full Stack</p>
            <p class="bio">
                Apasionado por crear soluciones innovadoras y escalables. 
                Especializado en desarrollo web moderno y arquitecturas backend robustas.
            </p>
        </header>

        <!-- Skills Section -->
        <section class="section">
            <h2 class="section-title">🚀 Tecnologías & Habilidades</h2>
            
            <div class="skills-grid">
                <div class="skill-category">
                    <h3><span class="icon">💻</span> Lenguajes de Programación</h3>
                    <div class="skills">
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg" class="skill-icon" alt="Python" />
                            Python
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original.svg" class="skill-icon" alt="Java" />
                            Java
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg" class="skill-icon" alt="JavaScript" />
                            JavaScript
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/csharp/csharp-original.svg" class="skill-icon" alt="C#" />
                            C#
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/typescript/typescript-original.svg" class="skill-icon" alt="TypeScript" />
                            TypeScript
                        </span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3><span class="icon">⚛️</span> Frontend Frameworks</h3>
                    <div class="skills">
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/react/react-original.svg" class="skill-icon" alt="React" />
                            React
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/angularjs/angularjs-original.svg" class="skill-icon" alt="Angular" />
                            Angular
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/vuejs/vuejs-original.svg" class="skill-icon" alt="Vue.js" />
                            Vue.js
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg" class="skill-icon" alt="HTML5" />
                            HTML5
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg" class="skill-icon" alt="CSS3" />
                            CSS3
                        </span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3><span class="icon">🔧</span> Backend & APIs</h3>
                    <div class="skills">
                        <span class="skill backend-skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/fastapi/fastapi-original.svg" class="skill-icon" alt="FastAPI" />
                            FastAPI
                        </span>
                        <span class="skill backend-skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/django/django-plain.svg" class="skill-icon" alt="Django" />
                            Django
                        </span>
                        <span class="skill backend-skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/djangorest/djangorest-original.svg" class="skill-icon" alt="Django REST" />
                            Django REST
                        </span>
                        <span class="skill backend-skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/nodejs/nodejs-original.svg" class="skill-icon" alt="Node.js" />
                            Node.js
                        </span>
                        <span class="skill backend-skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/express/express-original.svg" class="skill-icon" alt="Express" />
                            Express
                        </span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3><span class="icon">🗄️</span> Bases de Datos & Herramientas</h3>
                    <div class="skills">
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postgresql/postgresql-original.svg" class="skill-icon" alt="PostgreSQL" />
                            PostgreSQL
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mongodb/mongodb-original.svg" class="skill-icon" alt="MongoDB" />
                            MongoDB
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original.svg" class="skill-icon" alt="MySQL" />
                            MySQL
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/redis/redis-original.svg" class="skill-icon" alt="Redis" />
                            Redis
                        </span>
                        <span class="skill">
                            <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/docker/docker-original.svg" class="skill-icon" alt="Docker" />
                            Docker
                        </span>
                    </div>
                </div>
            </div>
        </section>

        <!-- Stats Section -->
        <section class="section">
            <h2 class="section-title">📊 Estadísticas</h2>
            <div class="stats">
                <div class="stat-card">
                    <div class="stat-number">3+</div>
                    <div class="stat-label">Años de Experiencia</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">50+</div>
                    <div class="stat-label">Proyectos Completados</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">10+</div>
                    <div class="stat-label">Tecnologías Dominadas</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">∞</div>
                    <div class="stat-label">Ganas de Aprender</div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section class="section contact">
            <h2 class="section-title">🤝 ¡Conectemos!</h2>
            <p>¿Tienes un proyecto interesante? ¡Me encantaría colaborar contigo!</p>
            <div class="social-links">
                <a href="#" class="social-link" title="GitHub">🐙</a>
                <a href="#" class="social-link" title="LinkedIn">💼</a>
                <a href="#" class="social-link" title="Email">📧</a>
                <a href="#" class="social-link" title="Twitter">🐦</a>
            </div>
        </section>
    </div>

    <script>
        // Typing animation effect
        const title = document.querySelector('.title');
        const titles = [
            'Desarrollador Full Stack',
            'Backend Developer',
            'Frontend Enthusiast',
            'API Architect',
            'Tech Explorer'
        ];
        
        let currentTitle = 0;
        let currentChar = 0;
        let isDeleting = false;
        
        function typeTitle() {
            const current = titles[currentTitle];
            
            if (isDeleting) {
                title.textContent = current.substring(0, currentChar - 1);
                currentChar--;
            } else {
                title.textContent = current.substring(0, currentChar + 1);
                currentChar++;
            }
            
            if (!isDeleting && currentChar === current.length) {
                setTimeout(() => isDeleting = true, 2000);
            } else if (isDeleting && currentChar === 0) {
                isDeleting = false;
                currentTitle = (currentTitle + 1) % titles.length;
            }
            
            const speed = isDeleting ? 50 : 100;
            setTimeout(typeTitle, speed);
        }
        
        // Start typing animation after a delay
        setTimeout(typeTitle, 1000);
        
        // Smooth scrolling for any internal links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
        
        // Add hover effect to skill cards
        document.querySelectorAll('.skill').forEach(skill => {
            skill.addEventListener('mouseenter', function() {
                this.style.transform = 'scale(1.1) rotate(2deg)';
            });
            
            skill.addEventListener('mouseleave', function() {
                this.style.transform = 'scale(1) rotate(0deg)';
            });
        });
    </script>
</body>
</html>
