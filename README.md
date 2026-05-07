<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
  <title>Theta | Futuristic Creative Agency</title>
  <!-- Google Fonts: Cinematic & Modern -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
  <!-- Font Awesome 6 (Free) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <!-- Swiper JS (for testimonials slider) -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
  <!-- AOS Library (scroll animations) -->
  <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: #0A0F1A;
      color: #ffffff;
      overflow-x: hidden;
      scroll-behavior: smooth;
    }

    /* Custom Scroll */
    ::-webkit-scrollbar {
      width: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #0A0F1A;
    }
    ::-webkit-scrollbar-thumb {
      background: #2C6EFF;
      border-radius: 10px;
    }

    /* Typography */
    h1, h2, h3, h4 {
      font-weight: 600;
      letter-spacing: -0.02em;
    }

    /* Glowing & Glassmorphism */
    .glass-card {
      background: rgba(15, 25, 45, 0.55);
      backdrop-filter: blur(12px);
      border-radius: 32px;
      border: 1px solid rgba(44, 110, 255, 0.25);
      box-shadow: 0 20px 40px -12px rgba(0, 0, 0, 0.4);
      transition: all 0.3s ease;
    }

    .glass-card:hover {
      border-color: rgba(44, 110, 255, 0.7);
      box-shadow: 0 25px 45px -12px rgba(44, 110, 255, 0.3);
      transform: translateY(-5px);
    }

    /* Navbar */
    .navbar {
      position: fixed;
      top: 0;
      width: 100%;
      z-index: 1000;
      padding: 1.2rem 5%;
      background: rgba(10, 15, 26, 0.85);
      backdrop-filter: blur(16px);
      border-bottom: 1px solid rgba(44, 110, 255, 0.2);
      transition: 0.3s;
    }

    .nav-container {
      max-width: 1400px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .logo {
      font-size: 1.8rem;
      font-weight: 800;
      background: linear-gradient(135deg, #FFFFFF, #2C6EFF);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      letter-spacing: -0.02em;
    }

    .nav-links {
      display: flex;
      gap: 2rem;
      list-style: none;
    }

    .nav-links a {
      color: #e0e6ff;
      text-decoration: none;
      font-weight: 500;
      transition: 0.2s;
      font-size: 0.95rem;
    }

    .nav-links a:hover {
      color: #2C6EFF;
      text-shadow: 0 0 6px rgba(44,110,255,0.5);
    }

    .mobile-menu {
      display: none;
      font-size: 1.5rem;
      cursor: pointer;
      color: white;
    }

    /* Hero Section with animated bg + glowing */
    .hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      overflow: hidden;
      padding: 0 5%;
      text-align: center;
    }

    .animated-bg {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -2;
      background: radial-gradient(circle at 20% 30%, #0a1a3a, #020617);
    }

    .animated-bg::before {
      content: "";
      position: absolute;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, rgba(44,110,255,0.2) 0%, rgba(0,0,0,0) 60%);
      animation: rotateGlow 20s infinite linear;
      top: -50%;
      left: -50%;
    }

    @keyframes rotateGlow {
      0% { transform: rotate(0deg);}
      100% { transform: rotate(360deg);}
    }

    .glow-text {
      text-shadow: 0 0 30px rgba(44,110,255,0.5);
    }

    .hero-content {
      max-width: 900px;
      z-index: 2;
    }

    .hero h1 {
      font-size: 4.5rem;
      font-weight: 800;
      background: linear-gradient(135deg, #FFFFFF, #80B3FF, #2C6EFF);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      margin-bottom: 1rem;
    }

    .hero p {
      font-size: 1.25rem;
      color: #ccd9ff;
      margin-bottom: 2rem;
    }

    .btn-primary {
      background: linear-gradient(95deg, #2C6EFF, #00c6ff);
      padding: 1rem 2.4rem;
      border-radius: 48px;
      font-weight: 600;
      border: none;
      color: white;
      font-size: 1rem;
      cursor: pointer;
      transition: 0.25s;
      box-shadow: 0 8px 20px rgba(44,110,255,0.4);
    }

    .btn-primary:hover {
      transform: scale(1.05);
      box-shadow: 0 12px 28px rgba(44,110,255,0.6);
    }

    /* Common Sections */
    section {
      padding: 100px 5%;
      max-width: 1400px;
      margin: 0 auto;
    }

    .section-title {
      font-size: 2.8rem;
      margin-bottom: 3rem;
      text-align: center;
      background: linear-gradient(120deg, #FFF, #5F9EFF);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    /* Services Grid */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 2rem;
    }

    .service-card {
      background: rgba(12, 20, 35, 0.6);
      backdrop-filter: blur(8px);
      border-radius: 28px;
      padding: 2rem;
      transition: all 0.35s cubic-bezier(0.2, 0.9, 0.4, 1.1);
      border: 1px solid rgba(44,110,255,0.2);
    }

    .service-card i {
      font-size: 2.8rem;
      background: linear-gradient(135deg, #2C6EFF, #00e0ff);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      margin-bottom: 1rem;
    }

    .service-card h3 {
      font-size: 1.5rem;
      margin-bottom: 0.75rem;
    }

    .service-card p {
      color: #b0c4ff;
      font-size: 0.9rem;
    }

    /* Portfolio Hover Cinematic */
    .portfolio-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 2rem;
    }

    .portfolio-item {
      position: relative;
      border-radius: 28px;
      overflow: hidden;
      aspect-ratio: 4/3;
      cursor: pointer;
    }

    .portfolio-item img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.6s ease;
    }

    .portfolio-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(0,0,0,0.7), rgba(44,110,255,0.8));
      backdrop-filter: blur(8px);
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      padding: 1.5rem;
      opacity: 0;
      transition: 0.4s;
      transform: translateY(10px);
    }

    .portfolio-item:hover .portfolio-overlay {
      opacity: 1;
      transform: translateY(0);
    }

    .portfolio-item:hover img {
      transform: scale(1.1);
    }

    /* Statistics */
    .stats-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
      gap: 2rem;
      text-align: center;
    }
    .stat-item h3 {
      font-size: 3rem;
      color: #2C6EFF;
    }
    .counter {
      font-size: 3rem;
      font-weight: 800;
      color: #fff;
    }

    /* Team */
    .team-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 2rem;
    }
    .team-card {
      background: rgba(15, 25, 45, 0.6);
      backdrop-filter: blur(12px);
      border-radius: 32px;
      padding: 2rem 1rem;
      text-align: center;
      transition: 0.3s;
    }
    .team-card img {
      width: 130px;
      height: 130px;
      border-radius: 50%;
      object-fit: cover;
      border: 3px solid #2C6EFF;
      margin-bottom: 1rem;
    }
    .social-icons a {
      color: #b0c4ff;
      margin: 0 8px;
      font-size: 1.2rem;
      transition: 0.2s;
    }
    .social-icons a:hover { color: #2C6EFF; }

    /* Testimonial Slider */
    .testimonial-slider {
      padding: 1rem 0;
    }
    .testimonial-card {
      background: rgba(20, 30, 55, 0.65);
      backdrop-filter: blur(12px);
      border-radius: 32px;
      padding: 2rem;
      text-align: center;
    }

    /* Contact */
    .contact-wrapper {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 3rem;
    }
    .contact-form input, .contact-form textarea {
      width: 100%;
      background: rgba(20, 30, 55, 0.7);
      border: 1px solid rgba(44,110,255,0.3);
      padding: 1rem;
      border-radius: 24px;
      color: white;
      margin-bottom: 1rem;
    }
    .map-placeholder {
      background: rgba(0,0,0,0.3);
      border-radius: 32px;
      height: 300px;
      display: flex;
      align-items: center;
      justify-content: center;
      background-image: url('https://placehold.co/600x400/0A1120/2C6EFF?text=Interactive+Map');
      background-size: cover;
    }
    /* Footer */
    footer {
      background: #020617cc;
      backdrop-filter: blur(12px);
      padding: 2rem 5%;
      border-top: 1px solid rgba(44,110,255,0.3);
      text-align: center;
    }

    @media (max-width: 900px) {
      .nav-links {
        display: none;
      }
      .mobile-menu {
        display: block;
      }
      .hero h1 { font-size: 2.6rem; }
      .section-title { font-size: 2rem; }
      .contact-wrapper { grid-template-columns: 1fr; }
      .stats-grid { flex-direction: column; align-items: center; }
    }

    /* Mobile nav open */
    .nav-links.active {
      display: flex;
      flex-direction: column;
      position: absolute;
      top: 80px;
      left: 0;
      width: 100%;
      background: rgba(10, 15, 26, 0.98);
      backdrop-filter: blur(20px);
      padding: 2rem;
      gap: 1.5rem;
      text-align: center;
      border-bottom: 1px solid #2C6EFF;
    }
  </style>
</head>
<body>
  <nav class="navbar">
    <div class="nav-container">
      <div class="logo">THETA</div>
      <div class="mobile-menu" id="mobileMenuBtn"><i class="fas fa-bars"></i></div>
      <ul class="nav-links" id="navLinks">
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#services">Services</a></li>
        <li><a href="#portfolio">Portfolio</a></li>
        <li><a href="#team">Team</a></li>
        <li><a href="#testimonials">Testimonials</a></li>
        <li><a href="#pricing">Pricing</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </div>
  </nav>

  <!-- Hero Section -->
  <section id="home" class="hero">
    <div class="animated-bg"></div>
    <div class="hero-content" data-aos="fade-up" data-aos-duration="1000">
      <h1 class="glow-text">Beyond Reality, <br>Into <span style="color:#2C6EFF;">Theta</span> Creative</h1>
      <p>High-end advertising & digital marketing. We craft cinematic brand stories that dominate the future.</p>
      <button class="btn-primary" onclick="alert('Launch your project — contact us!')">Launch Campaign <i class="fas fa-arrow-right"></i></button>
    </div>
  </section>

  <!-- About Section -->
  <section id="about" data-aos="fade-up">
    <h2 class="section-title">The Theta Ethos</h2>
    <div class="glass-card" style="padding: 3rem; text-align: center; max-width: 1000px; margin: 0 auto;">
      <p style="font-size:1.2rem; line-height:1.5;">Theta is a creative advertising & digital marketing agency specializing in branding, graphic design, video production, social media management, and media buying. We fuse futuristic aesthetics with data-driven strategies, delivering global recognition for disruptive brands.</p>
    </div>
  </section>

  <!-- Services Section -->
  <section id="services">
    <h2 class="section-title">Core Capabilities</h2>
    <div class="services-grid">
      <div class="service-card" data-aos="zoom-in"><i class="fas fa-bezier-curve"></i><h3>Branding & Visual Identity</h3><p>Memorable brand DNA & visual systems.</p></div>
      <div class="service-card" data-aos="zoom-in"><i class="fas fa-pen-nib"></i><h3>Graphic Design</h3><p>Striking digital & print design assets.</p></div>
      <div class="service-card" data-aos="zoom-in"><i class="fas fa-video"></i><h3>Photography & Video Production</h3><p>Cinematic storytelling & high-end production.</p></div>
      <div class="service-card" data-aos="zoom-in"><i class="fas fa-film"></i><h3>Video Editing & Motion Graphics</h3><p>Dynamic edits & immersive motion design.</p></div>
      <div class="service-card" data-aos="zoom-in"><i class="fab fa-instagram"></i><h3>Social Media Management</h3><p>Growth-driven content & community engagement.</p></div>
      <div class="service-card" data-aos="zoom-in"><i class="fas fa-chart-line"></i><h3>Media Buying</h3><p>Paid ads with precision & ROI focus.</p></div>
      <div class="service-card" data-aos="zoom-in"><i class="fas fa-chart-simple"></i><h3>Digital Marketing</h3><p>SEO, PPC & performance strategies.</p></div>
      <div class="service-card" data-aos="zoom-in"><i class="fas fa-code"></i><h3>Web Design</h3><p>Futuristic, responsive & high-conversion websites.</p></div>
    </div>
  </section>

  <!-- Portfolio Section (Cinematic) -->
  <section id="portfolio">
    <h2 class="section-title">Cinematic Showcases</h2>
    <div class="portfolio-grid">
      <div class="portfolio-item" data-aos="flip-left"><img src="https://placehold.co/600x400/0F1A2F/2C6EFF?text=Brand+Identity" alt="work1"><div class="portfolio-overlay"><h3>LUXE Identity</h3><p>Full brand transformation</p></div></div>
      <div class="portfolio-item" data-aos="flip-left"><img src="https://placehold.co/600x400/112236/00B4FF?text=Video+Production" alt="work2"><div class="portfolio-overlay"><h3>Neo Genesis Film</h3><p>Award-winning commercial</p></div></div>
      <div class="portfolio-item" data-aos="flip-left"><img src="https://placehold.co/600x400/0A1C32/2C6EFF?text=Social+Campaign" alt="work3"><div class="portfolio-overlay"><h3>#BeyondReach</h3><p>Viral social campaign</p></div></div>
    </div>
  </section>

  <!-- Statistics Section with Counters -->
  <section id="statistics">
    <h2 class="section-title">Metrics That Matter</h2>
    <div class="stats-grid">
      <div class="stat-item"><div class="counter" data-target="128">0</div><p>Global Awards</p></div>
      <div class="stat-item"><div class="counter" data-target="345">0</div><p>Happy Clients</p></div>
      <div class="stat-item"><div class="counter" data-target="987">0</div><p>Projects Delivered</p></div>
      <div class="stat-item"><div class="counter" data-target="2.8">0</div><p>Billion+ Impressions</p></div>
    </div>
  </section>

  <!-- Team Section -->
  <section id="team">
    <h2 class="section-title">Visionaries</h2>
    <div class="team-grid">
      <div class="team-card" data-aos="fade-right"><img src="https://randomuser.me/api/portraits/women/68.jpg" alt="team"><h3>Alina Chen</h3><p>Creative Director</p><div class="social-icons"><a href="#"><i class="fab fa-linkedin-in"></i></a><a href="#"><i class="fab fa-twitter"></i></a></div></div>
      <div class="team-card" data-aos="fade-right"><img src="https://randomuser.me/api/portraits/men/32.jpg" alt="team"><h3>Marcus Velez</h3><p>Head of Strategy</p><div class="social-icons"><a href="#"><i class="fab fa-linkedin-in"></i></a><a href="#"><i class="fab fa-instagram"></i></a></div></div>
      <div class="team-card" data-aos="fade-right"><img src="https://randomuser.me/api/portraits/women/44.jpg" alt="team"><h3>Sophia Laurent</h3><p>Lead Producer</p><div class="social-icons"><a href="#"><i class="fab fa-dribbble"></i></a><a href="#"><i class="fab fa-behance"></i></a></div></div>
    </div>
  </section>

  <!-- Testimonials Slider -->
  <section id="testimonials">
    <h2 class="section-title">Client Chronicles</h2>
    <div class="swiper testimonial-slider">
      <div class="swiper-wrapper">
        <div class="swiper-slide"><div class="testimonial-card"><i class="fas fa-star" style="color:#FFD966;"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><p style="margin:1rem 0">“Theta transformed our brand into an icon. Their creative vision is unmatched.”</p><h4>— Elena R., Global Brand Lead</h4></div></div>
        <div class="swiper-slide"><div class="testimonial-card"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><p>“Cinematic quality & data-driven campaigns. Best agency collaboration.”</p><h4>— David K., Co-Founder Orbital</h4></div></div>
        <div class="swiper-slide"><div class="testimonial-card"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><p>“Professional, futuristic, and results-oriented. Highly recommend Theta.”</p><h4>— Nina S., CMO Aether</h4></div></div>
      </div>
      <div class="swiper-pagination"></div>
    </div>
  </section>

  <!-- Pricing Section -->
  <section id="pricing">
    <h2 class="section-title">Premium Packages</h2>
    <div class="services-grid" style="grid-template-columns: repeat(auto-fit, minmax(280px,1fr));">
      <div class="glass-card" style="padding:2rem; text-align:center;"><h3>Starter Ignite</h3><p class="counter" style="font-size:2rem;">$2.8k</p><p>Brand Strategy + Social Management</p><button class="btn-primary" style="margin-top:1rem; padding:0.6rem 1.5rem;">Select</button></div>
      <div class="glass-card" style="padding:2rem; text-align:center; border:1px solid #2C6EFF;"><h3>Pro Lumina</h3><p class="counter" style="font-size:2rem;">$6.5k</p><p>Video Prod + Media Buying + Web Design</p><button class="btn-primary" style="margin-top:1rem;">Get Started</button></div>
      <div class="glass-card" style="padding:2rem; text-align:center;"><h3>Enterprise Theta</h3><p class="counter" style="font-size:2rem;">Custom</p><p>Full-scale 360° global domination</p><button class="btn-primary" style="margin-top:1rem;">Contact Us</button></div>
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact">
    <h2 class="section-title">Ignite Your Vision</h2>
    <div class="contact-wrapper">
      <div class="glass-card" style="padding:2rem;">
        <form id="contactForm">
          <input type="text" placeholder="Full Name" required>
          <input type="email" placeholder="Email Address" required>
          <textarea rows="4" placeholder="Your message..."></textarea>
          <button type="submit" class="btn-primary" style="width:100%">Send Message <i class="fas fa-paper-plane"></i></button>
        </form>
        <div style="margin-top: 1.5rem; text-align:center;"><i class="fab fa-instagram"></i> <i class="fab fa-twitter"></i> <i class="fab fa-linkedin-in"></i> <i class="fab fa-behance"></i></div>
      </div>
      <div class="glass-card" style="padding:0; overflow:hidden;">
        <div class="map-placeholder"><i class="fas fa-map-marker-alt" style="font-size:2rem; color:#2C6EFF;"></i> Theta HQ: Digital District, NY</div>
      </div>
    </div>
  </section>

  <footer>
    <p>© 2025 Theta Creative — Beyond the Horizon. <i class="fas fa-gem" style="color:#2C6EFF;"></i> Futuristic Advertising & Digital Agency</p>
  </footer>

  <script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
  <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
  <script>
    AOS.init({ duration: 800, once: true, offset: 100, easing: 'ease-out' });

    // Mobile menu toggle
    const mobileBtn = document.getElementById('mobileMenuBtn');
    const navLinks = document.getElementById('navLinks');
    mobileBtn.addEventListener('click', () => {
      navLinks.classList.toggle('active');
    });
    document.querySelectorAll('.nav-links a').forEach(link => {
      link.addEventListener('click', () => navLinks.classList.remove('active'));
    });

    // Counter animation with observer
    const counters = document.querySelectorAll('.counter');
    const speed = 150;
    const animateCounter = (el) => {
      const target = parseFloat(el.getAttribute('data-target'));
      let current = 0;
      const updateCounter = () => {
        let increment = target / 50;
        if (target < 100) increment = target / 30;
        if (current < target) {
          current += increment;
          if (current > target) current = target;
          el.innerText = target % 1 !== 0 ? current.toFixed(1) : Math.floor(current);
          setTimeout(updateCounter, 20);
        } else {
          el.innerText = target % 1 !== 0 ? target.toFixed(1) : target;
        }
      };
      updateCounter();
    };
    const observerOptions = { threshold: 0.5 };
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const counter = entry.target;
          if (!counter.classList.contains('animated')) {
            counter.classList.add('animated');
            animateCounter(counter);
          }
        }
      });
    }, observerOptions);
    counters.forEach(c => observer.observe(c));

    // Swiper Testimonials
    new Swiper('.testimonial-slider', {
      loop: true,
      autoplay: { delay: 4000, disableOnInteraction: false },
      pagination: { el: '.swiper-pagination', clickable: true },
      slidesPerView: 1,
      spaceBetween: 30,
      breakpoints: { 768: { slidesPerView: 2 }, 1024: { slidesPerView: 2.5 } }
    });

    // Contact form simple alert
    document.getElementById('contactForm').addEventListener('submit', (e) => {
      e.preventDefault();
      alert('Thank you! Theta will contact you within 24h with cosmic energy.');
      e.target.reset();
    });

    // smooth scroll for anchor links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function(e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if(target) target.scrollIntoView({ behavior: 'smooth', block: 'start' });
      });
    });

    // dynamic navbar background on scroll
    window.addEventListener('scroll', () => {
      const navbar = document.querySelector('.navbar');
      if(window.scrollY > 50) navbar.style.background = 'rgba(10, 15, 26, 0.98)';
      else navbar.style.background = 'rgba(10, 15, 26, 0.85)';
    });
  </script>
</body>
</html>
