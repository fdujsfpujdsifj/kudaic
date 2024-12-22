# kudaic
<!DOCTYPE html>
<html lang="es">
<head>
    <base href="/" />
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Neeport - Red Social de Películas y Series</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            background: #141414;
            color: white;
        }

        .header {
            background: linear-gradient(180deg, rgba(0,0,0,0.7) 0%, rgba(0,0,0,0) 100%);
            padding: 20px 50px;
            position: fixed;
            width: 100%;
            z-index: 100;
            transition: background 0.3s;
        }

        .header.scrolled {
            background: #141414;
        }

        .nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            background: linear-gradient(to right, #00ff00, #004400, #ffffff, #00ff00);
            background-size: 300% 100%;
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-size: 2.5rem;
            font-weight: bold;
            text-decoration: none;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            position: relative;
            animation: reptileShift 6s linear infinite;
        }

        @keyframes reptileShift {
            0% {
                background-position: 0% 50%;
            }
            100% {
                background-position: 100% 50%;
            }
        }

        .logo:hover {
            animation: reptileShift 2s linear infinite;
        }

        .nav-links {
            display: flex;
            gap: 20px;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            font-size: 0.9rem;
        }

        .hero {
            height: 90vh;
            background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)),
                        url('https://assets.nflxext.com/ffe/siteui/vlv3/f841d4c7-10e1-40af-bcae-07a3f8dc141a/f6d7434e-d6de-4185-a6d4-c77a2d08737b/US-en-20220502-popsignuptwoweeks-perspective_alpha_website_medium.jpg');
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
        }

        .hero-content {
            max-width: 800px;
            padding: 20px;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 20px;
        }

        .hero p {
            font-size: 1.5rem;
            margin-bottom: 30px;
        }

        .cta-button {
            background: #e50914;
            color: white;
            padding: 15px 30px;
            border-radius: 5px;
            text-decoration: none;
            font-size: 1.2rem;
            transition: background 0.3s;
        }

        .cta-button:hover {
            background: #f40612;
        }

        .main-content {
            display: flex;
            margin-top: 90vh; /* Space for hero section */
        }

        .movies-section {
            flex: 1;
            padding-right: 20px;
        }

        .blog-section {
            width: 400px;
            position: fixed;
            right: 0;
            top: 90vh; /* Start after hero section */
            bottom: 0;
            overflow-y: auto;
            padding: 20px;
            background: #141414;
            border-left: 1px solid #2f2f2f;
        }

        .row-title {
            font-size: 1.5rem;
            margin: 30px 20px 20px;
        }

        .row {
            display: flex;
            overflow-x: auto;
            padding: 20px;
            gap: 10px;
        }

        .movie-card {
            min-width: 200px;
            height: 300px;
            background: #2f2f2f;
            border-radius: 5px;
            transition: transform 0.3s;
            cursor: pointer;
        }

        .movie-card:hover {
            transform: scale(1.05);
        }

        .movie-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 5px;
        }

        /* Estilos para la sección de blog */
        .post {
            background: #2f2f2f;
            border-radius: 10px;
            margin-bottom: 20px;
            padding: 20px;
            max-width: 360px;
        }

        .post-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .post-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            margin-right: 10px;
        }

        .post-info {
            flex-grow: 1;
        }

        .post-author {
            font-weight: bold;
            margin-bottom: 3px;
        }

        .post-date {
            font-size: 0.8rem;
            color: #888;
        }

        .post-content {
            margin-bottom: 15px;
        }

        .post-actions {
            display: flex;
            gap: 20px;
            color: #888;
            font-size: 0.9rem;
        }

        .action-button {
            display: flex;
            align-items: center;
            gap: 5px;
            cursor: pointer;
            transition: color 0.3s;
        }

        .action-button:hover {
            color: #e50914;
        }

        .new-post-form {
            background: #2f2f2f;
            padding: 20px;
            border-radius: 10px;
            max-width: 360px;
            margin: 0 auto 30px;
        }

        .new-post-input {
            width: 100%;
            background: #404040;
            border: none;
            border-radius: 5px;
            padding: 15px;
            color: white;
            margin-bottom: 10px;
            resize: none;
        }

        .upload-button {
            background: #404040;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .upload-button:hover {
            background: #505050;
        }

        .media-preview {
            max-width: 100%;
            margin: 10px 0;
            border-radius: 5px;
            display: none;
        }

        .video-preview {
            max-width: 100%;
            max-height: 400px;
            margin: 10px 0;
            border-radius: 5px;
            display: none;
        }

        .post-media {
            max-width: 100%;
            border-radius: 5px;
            margin: 10px 0;
        }

        .post-video {
            width: 100%;
            max-height: 400px;
            border-radius: 5px;
            margin: 10px 0;
        }

        .user-stats {
            display: flex;
            gap: 15px;
            font-size: 0.9rem;
            color: #888;
            margin-top: 5px;
        }

        .profile-link {
            color: #e50914;
            text-decoration: none;
            font-weight: bold;
        }

        .profile-link:hover {
            text-decoration: underline;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .fade-in {
            animation: fadeIn 1s ease-in;
        }

        /* Pricing Section Styles */
        .pricing-section {
            padding: 80px 20px;
            text-align: center;
            background: #141414;
        }

        .pricing-section h2 {
            font-size: 2.5rem;
            margin-bottom: 50px;
        }

        .pricing-container {
            display: flex;
            justify-content: center;
            gap: 30px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .pricing-card {
            background: #2f2f2f;
            border-radius: 15px;
            padding: 30px;
            width: 300px;
            position: relative;
            transition: transform 0.3s;
        }

        .pricing-card:hover {
            transform: translateY(-10px);
        }

        .pricing-card.featured {
            background: #1f1f1f;
            border: 2px solid #e50914;
        }

        .popular-tag {
            position: absolute;
            top: -15px;
            right: 20px;
            background: #e50914;
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.8rem;
        }

        .pricing-card h3 {
            font-size: 1.8rem;
            margin-bottom: 20px;
        }

        .price {
            font-size: 2.5rem;
            margin-bottom: 30px;
        }

        .price span {
            font-size: 1rem;
            color: #888;
        }

        .features {
            list-style: none;
            margin-bottom: 30px;
            text-align: left;
        }

        .features li {
            margin-bottom: 15px;
            position: relative;
            padding-left: 25px;
        }

        .features li::before {
            content: "✓";
            color: #e50914;
            position: absolute;
            left: 0;
        }

        .payment-button {
            background: #e50914;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 5px;
            font-size: 1rem;
            cursor: pointer;
            transition: background 0.3s;
            width: 100%;
        }

        .payment-button:hover {
            background: #f40612;
        }

        /* Payment Modal Styles */
        .payment-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1000;
        }

        .modal-content {
            background: #2f2f2f;
            padding: 40px;
            border-radius: 15px;
            max-width: 500px;
            margin: 50px auto;
            position: relative;
        }

        .close-modal {
            position: absolute;
            right: 20px;
            top: 20px;
            font-size: 24px;
            cursor: pointer;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
        }

        .form-group input {
            width: 100%;
            padding: 12px;
            border: 1px solid #404040;
            border-radius: 5px;
            background: #404040;
            color: white;
        }

        .form-row {
            display: flex;
            gap: 20px;
        }

        .submit-payment {
            background: #e50914;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 5px;
            font-size: 1rem;
            cursor: pointer;
            width: 100%;
            margin-top: 20px;
        }

        .submit-payment:hover {
            background: #f40612;
        }
        
        /* Testimonial Styles */
        .testimonials {
            padding: 50px 20px;
            background: #1f1f1f;
            text-align: center;
        }

        .testimonials h2 {
            font-size: 2rem;
            margin-bottom: 40px;
        }

        .testimonial-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }

        .testimonial {
            background: #2f2f2f;
            padding: 20px;
            border-radius: 10px;
            width: 300px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            text-align: left;
        }

        .testimonial img {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            margin-bottom: 15px;
        }

        .testimonial p {
            font-size: 1rem;
            margin-bottom: 15px;
        }

        .testimonial .author {
            font-weight: bold;
        }

        /* Contact Form Styles */
        .contact-section {
            padding: 50px 20px;
            background: #141414;
        }

        .contact-section h2 {
            font-size: 2rem;
            margin-bottom: 40px;
            text-align: center;
        }

        .contact-form {
            max-width: 600px;
            margin: 0 auto;
            background: #2f2f2f;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .contact-form .form-group {
            margin-bottom: 20px;
        }

        .contact-form .form-group label {
            display: block;
            margin-bottom: 8px;
        }

        .contact-form .form-group input,
        .contact-form .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #404040;
            border-radius: 5px;
            background: #404040;
            color: white;
        }

        .contact-form .form-group textarea {
            resize: vertical;
            height: 100px;
        }

        .contact-form button {
            background: #e50914;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 5px;
            font-size: 1rem;
            cursor: pointer;
            width: 100%;
            margin-top: 20px;
        }

        .contact-form button:hover {
            background: #f40612;
        }

        /* Footer Styles */
        .footer {
            padding: 20px 0;
            background: #1f1f1f;
            text-align: center;
            color: #888;
        }

        .footer a {
            color: #e50914;
            text-decoration: none;
        }

        .footer a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <header class="header">
        <nav class="nav">
            <a href="https://www.neeport.com" class="logo">NEEPORT</a>
            <div class="nav-links">
                <a href="https://www.neeport.com/browse">Inicio</a>
                <a href="https://www.neeport.com/series">Series</a>
                <a href="https://www.neeport.com/movies">Películas</a>
                <a href="https://www.neeport.com/latest">Novedades</a>
                <a href="https://www.neeport.com/mylist">Mi Lista</a>
                <a href="https://www.neeport.com/blog">Blog</a>
            </div>
        </nav>
    </header>

    <section class="hero fade-in">
        <div class="hero-content">
            <h1>Películas y series ilimitadas y mucho más</h1>
            <p>Disfruta donde quieras. Cancela cuando quieras.</p>
            <a href="https://www.neeport.com/signup" class="cta-button">Comenzar ></a>
        </div>
    </section>

    <section class="pricing-section fade-in">
        <h2>Planes de Suscripción</h2>
        <div class="pricing-container">
            <div class="pricing-card">
                <h3>Básico</h3>
                <div class="price">$8.99<span>/mes</span></div>
                <ul class="features">
                    <li>Calidad HD</li>
                    <li>1 dispositivo</li>
                    <li>Sin anuncios</li>
                    <li>Catálogo básico</li>
                </ul>
                <button class="payment-button" data-plan="basic">Elegir Plan</button>
            </div>
            <div class="pricing-card featured">
                <div class="popular-tag">Más Popular</div>
                <h3>Estándar</h3>
                <div class="price">$13.99<span>/mes</span></div>
                <ul class="features">
                    <li>Calidad Full HD</li>
                    <li>2 dispositivos</li>
                    <li>Sin anuncios</li>
                    <li>Catálogo completo</li>
                </ul>
                <button class="payment-button" data-plan="standard">Elegir Plan</button>
            </div>
            <div class="pricing-card">
                <h3>Premium</h3>
                <div class="price">$17.99<span>/mes</span></div>
                <ul class="features">
                    <li>Calidad 4K+HDR</li>
                    <li>4 dispositivos</li>
                    <li>Sin anuncios</li>
                    <li>Catálogo completo</li>
                    <li>Estrenos exclusivos</li>
                </
