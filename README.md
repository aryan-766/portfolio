<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Aryan Jain | Futuristic Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&family=Roboto:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-bg: #181818;
            --primary-text: #fff;
            --accent: #00ffe7;
            --nav-bg: #222;
            --card-bg: #23272f;
            --footer-bg: #181818;
            --transition: 0.4s cubic-bezier(.4,0,.2,1);
        }
        body {
            margin: 0;
            font-family: 'Roboto', Arial, sans-serif;
            background: var(--primary-bg);
            color: var(--primary-text);
            transition: background var(--transition), color var(--transition);
            scroll-behavior: smooth;
        }
        .theme-dark {
            --primary-bg: #181818;
            --primary-text: #fff;
            --accent: #00ffe7;
            --nav-bg: #222;
            --card-bg: #23272f;
            --footer-bg: #181818;
        }
        .theme-light {
            --primary-bg: #f5f7fa;
            --primary-text: #181818;
            --accent: #0077ff;
            --nav-bg: #fff;
            --card-bg: #e3e9f0;
            --footer-bg: #e3e9f0;
        }
        .theme-futuristic {
            --primary-bg: #0a0f1a;
            --primary-text: #00ffe7;
            --accent: #00ffe7;
            --nav-bg: #10172b;
            --card-bg: #131a2e;
            --footer-bg: #0a0f1a;
        }
        header {
            background: var(--nav-bg);
            box-shadow: 0 2px 16px rgba(0,0,0,0.08);
            position: sticky;
            top: 0;
            z-index: 100;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0.5rem 2rem;
            transition: background var(--transition);
        }
        .logo {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.7rem;
            letter-spacing: 2px;
            color: var(--accent);
            font-weight: 700;
            text-shadow: 0 0 8px var(--accent), 0 0 2px #fff;
        }
        nav {
            display: flex;
            gap: 2rem;
        }
        nav a {
            color: var(--primary-text);
            text-decoration: none;
            font-weight: 500;
            font-size: 1rem;
            position: relative;
            transition: color var(--transition);
        }
        nav a::after {
            content: '';
            display: block;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: width 0.3s;
            position: absolute;
            left: 0;
            bottom: -4px;
        }
        nav a:hover::after {
            width: 100%;
        }
        .theme-toggle {
            display: flex;
            gap: 0.5rem;
            align-items: center;
        }
        .toggle-btn {
            background: var(--card-bg);
            border: none;
            border-radius: 50%;
            width: 32px;
            height: 32px;
            cursor: pointer;
            margin: 0 2px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background var(--transition), box-shadow var(--transition);
            box-shadow: 0 2px 8px rgba(0,255,231,0.08);
        }
        .toggle-btn.selected {
            box-shadow: 0 0 0 2px var(--accent);
        }
        main {
            max-width: 1000px;
            margin: 2rem auto;
            padding: 0 1rem;
        }
        section {
            margin-bottom: 3rem;
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 0.8s cubic-bezier(.4,0,.2,1), transform 0.8s cubic-bezier(.4,0,.2,1);
        }
        section.visible {
            opacity: 1;
            transform: translateY(0);
        }
        .about {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            gap: 2rem;
            background: var(--card-bg);
            border-radius: 18px;
            padding: 2rem;
            box-shadow: 0 4px 32px rgba(0,255,231,0.07);
        }
        .about-img {
            flex: 0 0 140px;
            width: 140px;
            height: 140px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent) 30%, #222 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            box-shadow: 0 0 24px var(--accent);
        }
        .about-img img {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--accent);
        }
        .about-text {
            flex: 1;
            min-width: 220px;
        }
        .about-text h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.2rem;
            margin: 0 0 0.5rem 0;
            color: var(--accent);
            letter-spacing: 1px;
        }
        .about-text p {
            font-size: 1.1rem;
            line-height: 1.6;
            margin: 0;
        }
        .skills {
            background: var(--card-bg);
            border-radius: 18px;
            padding: 2rem;
            box-shadow: 0 4px 32px rgba(0,255,231,0.07);
        }
        .skills h2 {
            font-family: 'Orbitron', sans-serif;
            color: var(--accent);
            margin-bottom: 1rem;
        }
        .skills-list {
            display: flex;
            flex-wrap: wrap;
            gap: 1.2rem;
        }
        .skill {
            background: linear-gradient(135deg, var(--accent) 10%, transparent 100%);
            color: var(--primary-bg);
            padding: 0.7rem 1.3rem;
            border-radius: 12px;
            font-weight: 600;
            font-size: 1rem;
            box-shadow: 0 2px 8px rgba(0,255,231,0.09);
            transition: transform 0.2s;
            cursor: pointer;
        }
        .skill:hover {
            transform: scale(1.08) rotate(-2deg);
        }
        .contact {
            background: var(--card-bg);
            border-radius: 18px;
            padding: 2rem;
            box-shadow: 0 4px 32px rgba(0,255,231,0.07);
        }
        .contact h2 {
            font-family: 'Orbitron', sans-serif;
            color: var(--accent);
            margin-bottom: 1rem;
        }
        .contact-form {
            display: flex;
            flex-direction: column;
            gap: 1rem;
            max-width: 400px;
        }
        .contact-form input, .contact-form textarea {
            padding: 0.7rem 1rem;
            border-radius: 8px;
            border: 1px solid #ccc;
            font-size: 1rem;
            background: var(--primary-bg);
            color: var(--primary-text);
            transition: border var(--transition), background var(--transition), color var(--transition);
        }
        .contact-form input:focus, .contact-form textarea:focus {
            border: 1.5px solid var(--accent);
            outline: none;
        }
        .contact-form button {
            background: var(--accent);
            color: var(--primary-bg);
            border: none;
            border-radius: 8px;
            padding: 0.8rem 1.2rem;
            font-size: 1.1rem;
            font-family: 'Orbitron', sans-serif;
            font-weight: 700;
            cursor: pointer;
            transition: background var(--transition), color var(--transition);
            box-shadow: 0 2px 8px rgba(0,255,231,0.13);
        }
        .contact-form button:hover {
            background: #fff;
            color: var(--accent);
        }
        .cv-links {
            margin-top: 1.5rem;
            display: flex;
            gap: 1.2rem;
            flex-wrap: wrap;
        }
        .cv-link {
            background: var(--accent);
            color: var(--primary-bg);
            padding: 0.7rem 1.3rem;
            border-radius: 12px;
            font-family: 'Orbitron', sans-serif;
            font-weight: 700;
            text-decoration: none;
            transition: background var(--transition), color var(--transition), box-shadow var(--transition);
            box-shadow: 0 2px 8px rgba(0,255,231,0.13);
        }
        .cv-link:hover {
            background: #fff;
            color: var(--accent);
        }
        footer {
            background: var(--footer-bg);
            color: var(--primary-text);
            text-align: center;
            padding: 2rem 1rem 1rem 1rem;
            border-top: 1px solid #222;
            font-size: 1.1rem;
            margin-top: 3rem;
            box-shadow: 0 -2px 16px rgba(0,255,231,0.04);
        }
        .footer-contact {
            margin-top: 0.7rem;
            font-size: 1rem;
            color: var(--accent);
            font-family: 'Orbitron', sans-serif;
        }
        @media (max-width: 700px) {
            header {
                flex-direction: column;
                gap: 0.7rem;
                padding: 0.7rem 1rem;
            }
            .about {
                flex-direction: column;
                align-items: flex-start;
                padding: 1.2rem;
            }
            .about-img {
                margin-bottom: 1rem;
            }
            main {
                padding: 0 0.3rem;
            }
        }
    </style>
</head>
<body class="theme-futuristic">
    <header>
        <div class="logo">Aryan Jain</div>
        <nav>
            <a href="#about">About</a>
            <a href="#skills">Skills</a>
            <a href="#contact">Contact</a>
            <a href="#cv">CV</a>
        </nav>
        <div class="theme-toggle">
            <button class="toggle-btn" id="dark-theme" title="Dark Theme">
                <span style="display:inline-block;width:18px;height:18px;background:#181818;border-radius:50%;border:2px solid #00ffe7;"></span>
            </button>
            <button class="toggle-btn" id="light-theme" title="Light Theme">
                <span style="display:inline-block;width:18px;height:18px;background:#fff;border-radius:50%;border:2px solid #0077ff;"></span>
            </button>
            <button class="toggle-btn selected" id="futuristic-theme" title="Futuristic Blue">
                <span style="display:inline-block;width:18px;height:18px;background:linear-gradient(135deg,#00ffe7 60%,#0a0f1a 100%);border-radius:50%;border:2px solid #00ffe7;"></span>
            </button>
        </div>
    </header>
    <main>
        <section id="about" class="about">
            <div class="about-img">
                <!-- Replace src with your image -->
                <img src="https://avatars.githubusercontent.com/u/9919?s=200&v=4" alt="Aryan Jain">
            </div>
            <div class="about-text">
                <h1>Hi, I'm Aryan Jain</h1>
                <p>
                    A passionate frontend developer with a futuristic vision. I love crafting interactive, visually stunning, and responsive web experiences. My work blends creativity with technology, always pushing the boundaries of what's possible on the web. Let's build the future together!
                </p>
            </div>
        </section>
        <section id="skills" class="skills">
            <h2>Skills</h2>
            <div class="skills-list">
                <div class="skill">HTML5</div>
                <div class="skill">CSS</div>
                <div class="skill">JavaScript (ES6+)</div>
                <div class="skill">React.js</div>
                <div class="skill">Tailwind CSS</div>
                <div class="skill">UI/UX Design</div>
                <div class="skill">Python</div>
                <div class="skill">Responsive Design</div>
                <div class="skill">SQL</div>
                <div class="skill">Git & GitHub</div>
            </div>
        </section>
        <section id="contact" class="contact">
            <h2>Contact</h2>
            <form class="contact-form" onsubmit="event.preventDefault();alert('Thank you for reaching out!');">
                <input type="text" placeholder="Your Name" required>
                <input type="email" placeholder="Your Email" required>
                <textarea rows="4" placeholder="Your Message" required></textarea>
                <button type="submit">Send Message</button>
            </form>
        </section>
        <section id="cv">
            <h2 style="font-family:'Orbitron',sans-serif;color:var(--accent);margin-bottom:1rem;">CV & Links</h2>
            <div class="cv-links">
                <a class="cv-link" href="https://github.com/aryanjain766" target="_blank">GitHub</a>
                <a class="cv-link" href="https://www.linkedin.com/in/aryan-jain-a993a1309\" target="_blank">LinkedIn</a>
                <a class="cv-link" href="https://drive.google.com/file/d/your-cv-link/view" target="_blank">Download CV</a>
            </div>
        </section>
    </main>
    <footer>
        <div>Get in touch with <span style="color:var(--accent);font-weight:700;">Aryan Jain</span></div>
        <div class="footer-contact">
            <span>Email: aryanjain8846@gmail.com</span> | 
            <span>LinkedIn: <a href="https://www.linkedin.com/in/aryan-jain-a993a1309" style="color:var(--accent);text-decoration:none;" target="_blank">aryanjain766</a></span>
        </div>
    </footer>
    <script>
        // Theme toggle logic
        const themes = {
            'dark-theme': 'theme-dark',
            'light-theme': 'theme-light',
            'futuristic-theme': 'theme-futuristic'
        };
        const btns = document.querySelectorAll('.toggle-btn');
        btns.forEach(btn => {
            btn.addEventListener('click', () => {
                document.body.className = themes[btn.id];
                btns.forEach(b => b.classList.remove('selected'));
                btn.classList.add('selected');
            });
        });

        // Smooth scroll animation on section reveal
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.15 });
        document.querySelectorAll('section').forEach(section => observer.observe(section));
    </script>
</body>
</html>
