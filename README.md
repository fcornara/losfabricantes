<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Los Fabricantes</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Crimson+Pro:ital,wght@0,400;0,600;1,400&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --green: #CDFF00;
            --black: #000000;
            --dark-gray: #0a0a0a;
            --mid-gray: #1a1a1a;
            --light-gray: #333;
            --white: #ffffff;
            --altman: #FF6B9D;
            --amodei: #4ECDC4;
            --musk: #FFE66D;
        }

        body {
            font-family: 'Space Grotesk', sans-serif;
            background: var(--black);
            color: var(--white);
            overflow-x: hidden;
            line-height: 1.5;
        }

        .serif {
            font-family: 'Crimson Pro', serif;
        }

        /* Noise overlay */
        .noise {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            opacity: 0.04;
            z-index: 9999;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 400 400' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
            animation: noise 8s steps(10) infinite;
        }

        @keyframes noise {
            0%, 100% { transform: translate(0, 0); }
            10% { transform: translate(-5%, -5%); }
            20% { transform: translate(-10%, 5%); }
            30% { transform: translate(5%, -10%); }
            40% { transform: translate(-5%, 15%); }
            50% { transform: translate(-10%, 5%); }
            60% { transform: translate(15%, 0); }
            70% { transform: translate(0, 10%); }
            80% { transform: translate(-15%, 0); }
            90% { transform: translate(10%, 5%); }
        }

        /* HERO SECTION */
        .hero {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 3rem;
            max-width: 1400px;
            margin: 0 auto;
            position: relative;
        }

        .hero-visual {
            display: flex;
            gap: 2rem;
            margin-bottom: 4rem;
            align-items: center;
        }

        .actor-mark {
            width: 80px;
            height: 80px;
            position: relative;
            overflow: hidden;
        }

        .actor-mark::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent 30%, var(--green) 50%, transparent 70%);
            animation: scan 3s linear infinite;
        }

        .actor-mark:nth-child(1) { clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%); }
        .actor-mark:nth-child(2) { clip-path: polygon(30% 0%, 70% 0%, 100% 30%, 100% 70%, 70% 100%, 30% 100%, 0% 70%, 0% 30%); }
        .actor-mark:nth-child(3) { clip-path: circle(50% at 50% 50%); }

        @keyframes scan {
            0% { transform: translateX(-100%) rotate(0deg); }
            100% { transform: translateX(200%) rotate(360deg); }
        }

        .hero h1 {
            font-size: clamp(4rem, 12vw, 10rem);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: -0.04em;
            line-height: 0.85;
            margin-bottom: 3rem;
            position: relative;
        }

        .glitch-text {
            position: relative;
            display: inline-block;
        }

        .glitch-text::before,
        .glitch-text::after {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        .glitch-text::before {
            animation: glitch-1 2.5s infinite;
            color: var(--altman);
            z-index: -1;
        }

        .glitch-text::after {
            animation: glitch-2 2.5s infinite;
            color: var(--amodei);
            z-index: -2;
        }

        @keyframes glitch-1 {
            0%, 100% { transform: translate(0); opacity: 0; }
            1% { transform: translate(-3px, 3px); opacity: 0.8; }
            2% { transform: translate(0); opacity: 0; }
            10% { transform: translate(0); opacity: 0; }
            11% { transform: translate(3px, -3px); opacity: 0.8; }
            12% { transform: translate(0); opacity: 0; }
        }

        @keyframes glitch-2 {
            0%, 100% { transform: translate(0); opacity: 0; }
            1.5% { transform: translate(3px, -3px); opacity: 0.7; }
            2.5% { transform: translate(0); opacity: 0; }
            10.5% { transform: translate(0); opacity: 0; }
            11.5% { transform: translate(-3px, 3px); opacity: 0.7; }
            12.5% { transform: translate(0); opacity: 0; }
        }

        .hero-tagline {
            font-size: clamp(1.5rem, 3.5vw, 2.5rem);
            color: var(--green);
            margin-bottom: 4rem;
            max-width: 1000px;
            line-height: 1.3;
            font-weight: 500;
        }

        .hero-intro {
            max-width: 900px;
        }

        .hero-intro p {
            font-size: clamp(1.1rem, 2vw, 1.4rem);
            line-height: 1.7;
            margin-bottom: 1.8rem;
            color: #ccc;
        }

        .hero-intro p:first-child {
            color: var(--white);
            font-weight: 600;
            font-size: clamp(1.3rem, 2.5vw, 1.8rem);
        }

        /* SECTION HEADERS */
        .section {
            padding: 8rem 3rem;
            max-width: 1600px;
            margin: 0 auto;
        }

        .section-header {
            margin-bottom: 5rem;
        }

        .section-title {
            font-size: clamp(3rem, 8vw, 6rem);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: -0.03em;
            margin-bottom: 2rem;
            background: linear-gradient(to right, var(--white) 0%, var(--green) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* FILTERS */
        .filters {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            margin-bottom: 4rem;
        }

        .filter-group {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
        }

        .filter-label {
            font-size: 0.85rem;
            color: #666;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            margin-right: 0.5rem;
            display: flex;
            align-items: center;
        }

        .filter-btn {
            padding: 0.6rem 1.2rem;
            background: var(--mid-gray);
            border: 1px solid var(--light-gray);
            color: var(--white);
            font-size: 0.9rem;
            cursor: pointer;
            transition: all 0.3s;
            font-family: 'Space Grotesk', sans-serif;
            text-transform: uppercase;
            letter-spacing: 0.03em;
            font-weight: 500;
        }

        .filter-btn:hover {
            background: var(--light-gray);
            border-color: var(--green);
        }

        .filter-btn.active {
            background: var(--green);
            color: var(--black);
            border-color: var(--green);
        }

        .filter-btn.actor-altman.active { background: var(--altman); border-color: var(--altman); }
        .filter-btn.actor-amodei.active { background: var(--amodei); border-color: var(--amodei); color: var(--black); }
        .filter-btn.actor-musk.active { background: var(--musk); border-color: var(--musk); color: var(--black); }

        /* TIMELINE */
        .timeline {
            position: relative;
            padding: 2rem 0;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            top: 0;
            bottom: 0;
            width: 3px;
            background: linear-gradient(to bottom, var(--mid-gray), var(--green), var(--mid-gray));
            transform: translateX(-50%);
        }

        .timeline-year {
            text-align: center;
            font-size: 4rem;
            font-weight: 700;
            color: var(--mid-gray);
            margin: 3rem 0 1.5rem;
            position: relative;
            z-index: 10;
        }

        .timeline-year span {
            background: var(--black);
            padding: 0 2rem;
        }

        .timeline-item {
            position: relative;
            margin-bottom: 1.5rem;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 0.6s forwards;
        }

        .timeline-item.hidden {
            display: none;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .timeline-item.left {
            text-align: right;
            padding-right: calc(50% + 4rem);
        }

        .timeline-item.right {
            text-align: left;
            padding-left: calc(50% + 4rem);
        }

        .timeline-dot {
            position: absolute;
            top: 1rem;
            width: 16px;
            height: 16px;
            background: var(--green);
            border-radius: 50%;
            z-index: 5;
            box-shadow: 0 0 0 4px var(--black), 0 0 0 6px var(--mid-gray);
            transition: all 0.3s;
        }

        .timeline-item.left .timeline-dot {
            right: calc(50% - 8px);
        }

        .timeline-item.right .timeline-dot {
            left: calc(50% - 8px);
        }

        .timeline-item:hover .timeline-dot {
            transform: scale(1.5);
            box-shadow: 0 0 0 4px var(--black), 0 0 0 6px var(--green), 0 0 20px var(--green);
        }

        .timeline-content {
            display: inline-block;
            max-width: 550px;
            padding: 1.5rem;
            background: #0d0d0d;
            border-left: 4px solid var(--green);
            transition: all 0.4s;
        }

        .timeline-item.right .timeline-content {
            border-left: none;
            border-right: 4px solid var(--green);
        }

        .timeline-content:hover {
            background: #000;
            transform: translateY(-4px);
            box-shadow: 0 8px 30px rgba(205, 255, 0, 0.2);
        }

        .timeline-item.size-large .timeline-content {
            max-width: 650px;
            padding: 2rem;
        }

        .timeline-item.size-small .timeline-content {
            max-width: 400px;
            padding: 1.2rem;
        }

        .timeline-date {
            font-size: 0.85rem;
            color: var(--green);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            margin-bottom: 0.8rem;
        }

        .timeline-title {
            font-size: 1.4rem;
            font-weight: 700;
            margin-bottom: 0.8rem;
            line-height: 1.2;
            color: #fff;
        }

        .timeline-item.size-large .timeline-title {
            font-size: 1.8rem;
        }

        .timeline-subtitle {
            font-size: 1rem;
            color: #e0e0e0;
            line-height: 1.6;
        }

        .timeline-actors {
            margin-top: 1rem;
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
        }

        .timeline-item.left .timeline-actors {
            justify-content: flex-end;
        }

        .actor-tag {
            font-size: 0.75rem;
            padding: 0.3rem 0.8rem;
            border-radius: 12px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        .actor-tag.altman { background: rgba(255, 107, 157, 0.2); color: var(--altman); }
        .actor-tag.amodei { background: rgba(78, 205, 196, 0.2); color: var(--amodei); }
        .actor-tag.musk { background: rgba(255, 230, 109, 0.2); color: var(--musk); }
        .actor-tag.other { background: rgba(255, 255, 255, 0.1); color: #999; }

        /* PLOT TWISTS SECTION */
        .twists-section {
            background: var(--dark-gray);
            padding: 8rem 3rem;
        }

        .twists-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(450px, 1fr));
            gap: 3rem;
            margin-top: 4rem;
        }

        .twist-card {
            background: #0d0d0d;
            padding: 2.5rem;
            border: 2px solid var(--green);
            position: relative;
            overflow: hidden;
            transition: all 0.4s;
            opacity: 0;
            transform: scale(0.95);
            animation: twistReveal 0.6s forwards;
        }

        .twist-card.hidden {
            display: none;
        }

        @keyframes twistReveal {
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        .twist-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(205, 255, 0, 0.1), transparent);
            transition: left 0.6s;
        }

        .twist-card:hover::before {
            left: 100%;
        }

        .twist-card:hover {
            border-color: var(--green);
            transform: translateY(-8px);
            box-shadow: 0 12px 40px rgba(205, 255, 0, 0.3);
        }

        .twist-date {
            font-size: 3rem;
            font-weight: 700;
            color: var(--green);
            line-height: 1;
            margin-bottom: 1.5rem;
            opacity: 0.4;
        }

        .twist-title {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 1rem;
            line-height: 1.1;
            color: #fff;
        }

        .twist-subtitle {
            font-size: 1.1rem;
            color: var(--green);
            font-weight: 500;
            margin-bottom: 2rem;
            font-style: italic;
        }

        .twist-scene {
            font-size: 1.1rem;
            line-height: 1.7;
            color: #e0e0e0;
            margin-bottom: 2rem;
        }

        .twist-tags {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
            margin-top: 2rem;
        }

        .twist-tag {
            font-size: 0.75rem;
            padding: 0.4rem 1rem;
            background: var(--light-gray);
            color: #999;
            border-radius: 20px;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .twist-tag:hover,
        .twist-tag.active {
            background: var(--green);
            color: var(--black);
        }

        /* POSTURAS SECTION */
        .posturas-section {
            padding: 8rem 3rem;
        }

        .posturas-grid {
            display: grid;
            gap: 3rem;
        }

        .postura-item {
            background: #0d0d0d;
            border: 1px solid var(--green);
            overflow: hidden;
            transition: all 0.4s;
        }

        .postura-header {
            padding: 2rem;
            cursor: pointer;
            background: #000;
            transition: all 0.3s;
        }

        .postura-header:hover {
            background: #0d0d0d;
        }

        .postura-title {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            color: #fff;
        }

        .postura-hint {
            font-size: 0.9rem;
            color: #888;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        .postura-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.6s ease;
        }

        .postura-content.expanded {
            max-height: 2000px;
        }

        .postura-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1px;
            background: var(--black);
        }

        .postura-card {
            background: #0d0d0d;
            padding: 2.5rem;
            transition: all 0.4s;
        }

        .postura-card:hover {
            background: #000;
        }

        .postura-name {
            font-size: 0.9rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            margin-bottom: 1.5rem;
        }

        .postura-card:nth-child(1) .postura-name { color: var(--altman); }
        .postura-card:nth-child(2) .postura-name { color: var(--amodei); }
        .postura-card:nth-child(3) .postura-name { color: var(--musk); }

        .postura-quote {
            font-family: 'Crimson Pro', serif;
            font-size: 1.3rem;
            line-height: 1.6;
            font-style: italic;
            margin-bottom: 1.5rem;
            color: #fff;
        }

        .postura-source {
            font-size: 0.85rem;
            color: #888;
        }

        /* CIERRE */
        .cierre-section {
            min-height: 80vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 8rem 3rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .cierre-text {
            font-size: clamp(1.8rem, 4vw, 3rem);
            line-height: 1.4;
            font-weight: 500;
        }

        .cierre-text p {
            margin-bottom: 2rem;
        }

        .cierre-question {
            color: var(--green);
            font-weight: 700;
            margin-top: 4rem;
        }

        /* RESPONSIVE */
        @media (max-width: 1024px) {
            .timeline::before {
                left: 3rem;
            }

            .timeline-item.left,
            .timeline-item.right {
                text-align: left;
                padding-left: 6rem;
                padding-right: 1rem;
            }

            .timeline-item.left .timeline-dot,
            .timeline-item.right .timeline-dot {
                left: calc(3rem - 8px);
            }

            .timeline-item.left .timeline-actors {
                justify-content: flex-start;
            }

            .timeline-item.right .timeline-content {
                border-right: none;
                border-left: 4px solid var(--light-gray);
            }

            .twists-grid {
                grid-template-columns: 1fr;
            }

            .postura-grid {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 768px) {
            .hero {
                padding: 2rem 1.5rem;
            }

            .section {
                padding: 4rem 1.5rem;
            }

            .filters {
                gap: 0.5rem;
            }

            .filter-btn {
                padding: 0.5rem 0.8rem;
                font-size: 0.8rem;
            }

            .timeline-content {
                max-width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="noise"></div>

    <!-- HERO -->
    <section class="hero">
        <div class="hero-visual">
            <div class="actor-mark"></div>
            <div class="actor-mark"></div>
            <div class="actor-mark"></div>
        </div>

        <h1>
            <span class="glitch-text" data-text="LOS">LOS</span><br>
            <span class="glitch-text" data-text="FABRICANTES">FABRICANTES</span>
        </h1>

        <div class="hero-tagline">
            Tres hombres prometieron construir inteligencia artificial para el bien de la humanidad. Hoy compiten en vivo por el control del futuro.
        </div>

        <div class="hero-intro">
            <p>Todo empieza antes de OpenAI.</p>
            <p>En 2014, Google compra DeepMind es una señal. La inteligencia artificial deja de ser una línea de investigación académica y pasa a ser un activo estratégico. En Silicon Valley aparece una preocupación concreta: si alguien llega primero, define las reglas.</p>
            <p>En diciembre de 2015, OpenAI nace como respuesta a ese escenario. La promesa es clara: desarrollar inteligencia artificial para el beneficio de todos.</p>
        </div>
    </section>

    <!-- TIMELINE -->
    <section class="section timeline-section">
        <div class="section-header">
            <h2 class="section-title">CRONOLOGÍA</h2>
            
            <div class="filters">
                <div class="filter-group">
                    <span class="filter-label">Protagonista:</span>
                    <button class="filter-btn filter-actor active" data-actor="all">Todos</button>
                    <button class="filter-btn filter-actor actor-altman" data-actor="altman">Altman</button>
                    <button class="filter-btn filter-actor actor-amodei" data-actor="amodei">Amodei</button>
                    <button class="filter-btn filter-actor actor-musk" data-actor="musk">Musk</button>
                </div>
                
                <div class="filter-group">
                    <span class="filter-label">Tipo:</span>
                    <button class="filter-btn filter-type active" data-type="all">Todos</button>
                    <button class="filter-btn filter-type" data-type="fundacion">Fundaciones</button>
                    <button class="filter-btn filter-type" data-type="ruptura">Rupturas</button>
                    <button class="filter-btn filter-type" data-type="producto">Productos</button>
                    <button class="filter-btn filter-type" data-type="conflicto">Conflictos</button>
                </div>
            </div>
        </div>

        <div class="timeline" id="timeline"></div>
    </section>

    <!-- PLOT TWISTS -->
    <section class="section twists-section">
        <div class="section-header">
            <h2 class="section-title">QUIEBRES</h2>
            
            <div class="filters">
                <div class="filter-group">
                    <span class="filter-label">Protagonista:</span>
                    <button class="filter-btn filter-twist-actor active" data-actor="all">Todos</button>
                    <button class="filter-btn filter-twist-actor actor-altman" data-actor="altman">Altman</button>
                    <button class="filter-btn filter-twist-actor actor-amodei" data-actor="amodei">Amodei</button>
                    <button class="filter-btn filter-twist-actor actor-musk" data-actor="musk">Musk</button>
                </div>
                
                <div class="filter-group">
                    <span class="filter-label">Etiqueta:</span>
                    <button class="filter-btn filter-twist-tag active" data-tag="all">Todos</button>
                    <button class="filter-btn filter-twist-tag" data-tag="ruptura">Ruptura</button>
                    <button class="filter-btn filter-twist-tag" data-tag="poder">Poder</button>
                    <button class="filter-btn filter-twist-tag" data-tag="decisión">Decisión</button>
                    <button class="filter-btn filter-twist-tag" data-tag="conflicto">Conflicto</button>
                    <button class="filter-btn filter-twist-tag" data-tag="visión">Visión</button>
                </div>
            </div>
        </div>

        <div class="twists-grid" id="twists-grid"></div>
    </section>

    <!-- POSTURAS -->
    <section class="section posturas-section">
        <div class="section-header">
            <h2 class="section-title">POSICIONES</h2>
        </div>

        <div class="posturas-grid" id="posturas-grid"></div>
    </section>

    <!-- CIERRE -->
    <section class="cierre-section">
        <div class="cierre-text">
            <p>La inteligencia artificial funciona como una excusa para rediseñarlo todo:</p>
            <p>Para reorganizar el poder.<br>
            Para redefinir el trabajo.<br>
            Para instalar quiénes toman las decisiones y cómo.</p>
            <p>Mientras discuten modelos, contratos y riesgos, están escribiendo las reglas de un mundo que todavía no existe.</p>
            <p class="cierre-question">Y la pregunta no es si va a pasar sino quién decide cómo.</p>
        </div>
    </section>

    <script>
        // DATA
        const timelineData = [
            { year: "2014", date: "Ene 2014", title: "Google compra DeepMind", subtitle: "La compra activa alarma en Silicon Valley: riesgo de monopolio de IA avanzada. Esto dispara la idea de OpenAI como contrapeso.", actors: ["other"], type: "fundacion", size: "large" },
            { year: "2015", date: "Dic 2015", title: "Fundación de OpenAI", subtitle: "Se funda como non-profit. Participan Sam Altman, Elon Musk, Greg Brockman, Ilya Sutskever, Wojciech Zaremba, John Schulman. Musk promete hasta $1B.", actors: ["altman", "musk"], type: "fundacion", size: "large" },
            { year: "2016", date: "Ene 2016", title: "Ilya Sutskever lidera investigación", subtitle: "Ex Google Brain, se convierte en figura central técnica. OpenAI empieza a atraer talento top en IA.", actors: ["altman"], type: "producto", size: "small" },
            { year: "2017", date: "2017", title: "Tensiones internas iniciales", subtitle: "Musk presiona por acelerar y competir con Google. Internamente ya hay fricción sobre control y velocidad.", actors: ["musk", "altman"], type: "conflicto", size: "regular" },
            { year: "2018", date: "Feb 2018", title: "Musk intenta tomar control", subtitle: "Propone liderar OpenAI y fusionarla con Tesla. La propuesta es rechazada por la junta.", actors: ["musk", "altman"], type: "ruptura", size: "large" },
            { year: "2018", date: "Feb 2018", title: "Musk renuncia a OpenAI", subtitle: "Se retira formalmente. Versión pública: conflicto de intereses. Versión real: disputa de poder. Corta financiamiento.", actors: ["musk"], type: "ruptura", size: "large" },
            { year: "2018", date: "Feb 2018", title: "Lanzamiento GPT-2 (base)", subtitle: "OpenAI empieza a mostrar avances que indican potencial real de modelos de lenguaje.", actors: ["altman"], type: "producto", size: "small" },
            { year: "2019", date: "Mar 2019", title: "OpenAI crea estructura 'capped-profit'", subtitle: "Se abandona el modelo puramente non-profit para poder captar inversión. Se justifica por costos de cómputo.", actors: ["altman"], type: "fundacion", size: "large" },
            { year: "2019", date: "Jul 2019", title: "Microsoft invierte $1B", subtitle: "Acuerdo estratégico. Azure pasa a ser infraestructura base. Microsoft obtiene acceso privilegiado a modelos.", actors: ["altman"], type: "fundacion", size: "regular" },
            { year: "2019", date: "2019", title: "Musk empieza a criticar públicamente", subtitle: "Señala que OpenAI dejó de ser abierta y se volvió dependiente de Microsoft.", actors: ["musk"], type: "conflicto", size: "regular" },
            { year: "2020", date: "Jun 2020", title: "Lanzamiento GPT-3", subtitle: "Primer modelo que muestra capacidades masivas. Se instala hype global en IA.", actors: ["altman"], type: "producto", size: "large" },
            { year: "2020", date: "Dic 2020", title: "Renuncia Dario Amodei + equipo", subtitle: "Se va junto a investigadores clave (incluyendo Daniela Amodei). Desacuerdo con dirección comercial, seguridad y pérdida de control científico.", actors: ["amodei"], type: "ruptura", size: "large" },
            { year: "2021", date: "Ene 2021", title: "Fundación de Anthropic", subtitle: "Nueva empresa con foco en seguridad, alineación y control de riesgos. Se lleva parte del equipo clave de OpenAI.", actors: ["amodei"], type: "fundacion", size: "large" },
            { year: "2021", date: "2021", title: "Anthropic adopta estructura PBC", subtitle: "Se organiza como Public Benefit Corporation para priorizar impacto social y gobernanza de largo plazo.", actors: ["amodei"], type: "fundacion", size: "small" },
            { year: "2021", date: "Abr 2021", title: "Altman deja Y Combinator", subtitle: "Se dedica full-time a OpenAI. Consolidación de liderazgo total.", actors: ["altman"], type: "fundacion", size: "regular" },
            { year: "2022", date: "Nov 2022", title: "OpenAI lanza ChatGPT", subtitle: "Se vuelve viral. Primer contacto masivo del público con IA generativa.", actors: ["altman"], type: "producto", size: "large" },
            { year: "2022", date: "2022", title: "Anthropic lanza Claude (primeros modelos)", subtitle: "Aparece como alternativa a GPT con foco en seguridad y control.", actors: ["amodei"], type: "producto", size: "regular" },
            { year: "2022", date: "Oct 2022", title: "Musk compra Twitter (X)", subtitle: "Empieza a construir infraestructura propia de datos y distribución para IA.", actors: ["musk"], type: "fundacion", size: "regular" },
            { year: "2023", date: "Jul 2023", title: "Musk funda xAI", subtitle: "Respuesta directa a OpenAI. Recluta talento de DeepMind y OpenAI.", actors: ["musk"], type: "fundacion", size: "large" },
            { year: "2023", date: "2023", title: "Anthropic recibe inversión masiva", subtitle: "Google y Amazon invierten miles de millones. Se posiciona como principal rival técnico de OpenAI.", actors: ["amodei"], type: "fundacion", size: "regular" },
            { year: "2023", date: "Nov 17 2023", title: "Altman es despedido", subtitle: "La junta (incluyendo Ilya Sutskever) lo remueve por 'falta de sinceridad'. Crisis interna sin precedentes.", actors: ["altman"], type: "ruptura", size: "large" },
            { year: "2023", date: "Nov 18-21 2023", title: "Rebelión interna", subtitle: "Más del 90% de empleados amenaza con renunciar. Microsoft ofrece absorberlos.", actors: ["altman"], type: "conflicto", size: "large" },
            { year: "2023", date: "Nov 22 2023", title: "Altman es reinstalado", subtitle: "Vuelve como CEO con nueva junta alineada. Sale fortalecido.", actors: ["altman"], type: "ruptura", size: "large" },
            { year: "2023", date: "Nov 2023", title: "Sutskever pierde poder", subtitle: "Tras la crisis queda desplazado internamente dentro de OpenAI.", actors: ["altman"], type: "conflicto", size: "small" },
            { year: "2023", date: "Feb 2023", title: "Google lanza Bard (fallido)", subtitle: "Error en demo genera pérdida de ~$100B en mercado. Refuerza liderazgo de OpenAI.", actors: ["other"], type: "producto", size: "regular" },
            { year: "2024", date: "Mar 2024", title: "Musk demanda a OpenAI", subtitle: "Acusa a Altman de traicionar la misión original y convertir la empresa en subsidiaria de Microsoft.", actors: ["musk", "altman"], type: "conflicto", size: "large" },
            { year: "2024", date: "Mar 2024", title: "OpenAI responde públicamente", subtitle: "Publica emails internos que muestran que Musk conocía la necesidad de modelo comercial.", actors: ["altman"], type: "conflicto", size: "regular" },
            { year: "2024", date: "2024", title: "Conflicto Altman vs Amodei escala", subtitle: "Amodei acusa a OpenAI de imprudente; Altman lo considera obstructivo. Ruptura total.", actors: ["altman", "amodei"], type: "conflicto", size: "large" },
            { year: "2024", date: "Oct 2024", title: "'Machines of Loving Grace'", subtitle: "Amodei publica ensayo donde plantea futuro utópico con IA bajo condiciones de control estricto.", actors: ["amodei"], type: "producto", size: "regular" },
            { year: "2025", date: "2025", title: "Anthropic lanza Claude Code", subtitle: "Introduce herramientas para programación autónoma y agentes que escriben código.", actors: ["amodei"], type: "producto", size: "regular" },
            { year: "2025", date: "2025", title: "Claude Code se vuelve producto central", subtitle: "Empresas empiezan a usarlo para automatizar desarrollo completo.", actors: ["amodei"], type: "producto", size: "small" },
            { year: "2025", date: "2025", title: "Debate interno en OpenAI", subtitle: "Críticas por seguridad, renuncias y tensiones internas tras crecimiento acelerado.", actors: ["altman"], type: "conflicto", size: "regular" },
            { year: "2025", date: "2025", title: "Anthropic crece en mercado enterprise", subtitle: "Gana terreno frente a OpenAI en uso corporativo y APIs.", actors: ["amodei"], type: "producto", size: "small" },
            { year: "2025", date: "2025", title: "Intensificación carrera AGI", subtitle: "Musk dice 2-3 años, Altman 5, Amodei 5-10. Se instala narrativa de inevitabilidad.", actors: ["musk", "altman", "amodei"], type: "conflicto", size: "regular" },
            { year: "2026", date: "Ene 2026", title: "OpenAI se reestructura como PBC", subtitle: "Formaliza transición hacia modelo comercial pleno manteniendo misión pública.", actors: ["altman"], type: "fundacion", size: "regular" },
            { year: "2026", date: "Feb 2026", title: "OpenAI alcanza valuación extrema", subtitle: "Rondas de inversión la posicionan como una de las empresas más valiosas del mundo.", actors: ["altman"], type: "fundacion", size: "small" },
            { year: "2026", date: "Feb 2026", title: "Explosión de Claude y Claude Code", subtitle: "Nuevos modelos y capacidades agénticas. Se vuelve central en desarrollo de software.", actors: ["amodei"], type: "producto", size: "regular" },
            { year: "2026", date: "Feb 2026", title: "Uso masivo y límites de Claude", subtitle: "Alta demanda obliga a imponer restricciones de uso por capacidad de cómputo.", actors: ["amodei"], type: "producto", size: "small" },
            { year: "2026", date: "Feb 2026", title: "IA escribe su propio código", subtitle: "Claude empieza a generar gran parte de su propio código, cambio estructural en desarrollo.", actors: ["amodei"], type: "producto", size: "small" },
            { year: "2026", date: "Ene 2026", title: "Pentágono exige acceso irrestricto", subtitle: "Gobierno de EE.UU. pide eliminar límites para uso militar de IA.", actors: ["amodei"], type: "conflicto", size: "large" },
            { year: "2026", date: "Ene 2026", title: "Amodei rechaza ultimátum", subtitle: "Se niega a permitir uso sin restricciones (armas autónomas, vigilancia masiva).", actors: ["amodei"], type: "ruptura", size: "large" },
            { year: "2026", date: "Feb 2026", title: "Anthropic etiquetada como riesgo", subtitle: "Es clasificada como 'riesgo para la cadena de suministro' por el gobierno.", actors: ["amodei"], type: "conflicto", size: "regular" },
            { year: "2026", date: "Feb 2026", title: "Filtración de memos internos", subtitle: "Se filtran críticas internas de Amodei hacia el gobierno y decisiones políticas.", actors: ["amodei"], type: "conflicto", size: "small" },
            { year: "2026", date: "Feb 2026", title: "Altman acepta contrato militar", subtitle: "OpenAI toma el contrato que Anthropic rechaza.", actors: ["altman"], type: "ruptura", size: "large" },
            { year: "2026", date: "Feb 2026", title: "Musk apoya uso militar", subtitle: "xAI se alinea con defensa y aplicaciones estratégicas.", actors: ["musk"], type: "conflicto", size: "regular" },
            { year: "2026", date: "Feb 2026", title: "Guerra discursiva total", subtitle: "Musk acusa a OpenAI de 'mentira' y a Anthropic de 'woke'; Amodei acusa a Altman de mentir; conflicto público.", actors: ["musk", "altman", "amodei"], type: "conflicto", size: "large" },
            { year: "2026", date: "Feb 2026", title: "Fusión xAI + SpaceX", subtitle: "Integración vertical: IA + satélites + infraestructura global.", actors: ["musk"], type: "fundacion", size: "regular" },
            { year: "2026", date: "Feb 2026", title: "Redada en oficinas de X (París)", subtitle: "Investigación por deepfakes y contenido ilegal generado por IA.", actors: ["musk"], type: "conflicto", size: "small" },
            { year: "2026", date: "Feb 2026", title: "Anthropic evoluciona Claude Code a agentes", subtitle: "Se habilitan modos autónomos con ejecución directa y permisos extendidos.", actors: ["amodei"], type: "producto", size: "small" },
            { year: "2026", date: "Mar 2026", title: "'La adolescencia de la tecnología'", subtitle: "Amodei publica su segundo ensayo: describe la IA como sistema inmaduro, potente e inestable que requiere límites estructurales urgentes.", actors: ["amodei"], type: "producto", size: "regular" }
        ];

        const twistsData = [
            { date: "Ene 2018", title: "Musk quiere quedarse con todo", subtitle: "El equilibrio se rompe antes de que la historia empiece de verdad.", scene: "Musk propone tomar el control total de OpenAI y llevarla a Tesla. No plantea una discusión técnica, plantea una conducción única. La junta se niega. A los pocos días se va. Con él se va también el dinero.", tags: ["ruptura", "poder", "fundación"], actors: ["musk", "altman"] },
            { date: "Feb 2018", title: "Musk se va y empieza a hablar", subtitle: "El silencio dura poco. La narrativa arranca años después.", scene: "Musk se retira formalmente. Durante un tiempo parece correrse. Después empieza a construir otra versión de la historia: OpenAI como proyecto desviado, capturado, traicionado.", tags: ["declaración", "conflicto", "narrativa"], actors: ["musk"] },
            { date: "Mar 2019", title: "OpenAI cambia de naturaleza", subtitle: "La misión necesita dinero y el dinero cambia la misión.", scene: "Altman redefine la estructura. OpenAI deja de ser solo non-profit. Entra Microsoft. La infraestructura, la escala, la velocidad. Todo empieza a alinearse con eso.", tags: ["empresa", "decisión", "estructura"], actors: ["altman"] },
            { date: "Dic 2020", title: "Amodei se lleva el corazón técnico", subtitle: "No es una renuncia. Es una migración.", scene: "Dario Amodei y un grupo de investigadores clave se van. No hay pelea pública. Hay un corte silencioso. Se llevan conocimiento, relaciones, credibilidad.", tags: ["ruptura", "investigación", "exodus"], actors: ["amodei"] },
            { date: "Nov 18-21 2023", title: "La guerra se vuelve interna", subtitle: "No hay neutrales.", scene: "Más del 90% de empleados amenaza con renunciar. Microsoft ofrece absorberlos. La presión se vuelve insostenible.", tags: ["crisis", "lealtad", "poder"], actors: ["altman"] },
            { date: "Nov 22 2023", title: "Altman vuelve más fuerte", subtitle: "El golpe fracasa.", scene: "Regresa como CEO. Nueva junta alineada. Sale con más poder que antes. La estructura de control cambia definitivamente.", tags: ["retorno", "poder", "reestructura"], actors: ["altman"] },
            { date: "Oct 2024", title: "Amodei escribe el futuro", subtitle: "Pero con condiciones.", scene: "Publica 'Machines of Loving Grace'. Describe un futuro utópico con IA. Pero advierte: solo bajo condiciones de control estricto.", tags: ["ensayo", "visión", "utopía"], actors: ["amodei"] },
            { date: "Ene 2026", title: "El Pentágono pone condiciones", subtitle: "El poder político entra sin matices.", scene: "Exigen acceso sin restricciones. Uso militar abierto. La negociación no es técnica. Es directa.", tags: ["estado", "presión", "poder"], actors: ["amodei"] },
            { date: "Ene 2026", title: "Anthropic dice que no", subtitle: "Una decisión que corta el flujo.", scene: "Amodei rechaza el contrato. No acepta eliminar límites. La empresa queda expuesta.", tags: ["decisión", "ética", "conflicto"], actors: ["amodei"] },
            { date: "Feb 2026", title: "OpenAI ocupa el lugar", subtitle: "El espacio no queda vacío.", scene: "Horas después, OpenAI firma. Altman entra donde Anthropic se retiró. Sin pausa.", tags: ["decisión", "poder", "oportunidad"], actors: ["altman"] },
            { date: "Feb 2026", title: "Musk dispara contra todos", subtitle: "La discusión se vuelve ideológica.", scene: "Habla de IA woke. Ataca a Anthropic. Llama a OpenAI una mentira. Se posiciona como alternativa sin filtros.", tags: ["declaración", "conflicto", "ideología"], actors: ["musk"] },
            { date: "Mar 2026", title: "La adolescencia de la tecnología", subtitle: "La IA ya no es una herramienta. Es un sistema inestable.", scene: "Amodei publica su ensayo. Habla de una tecnología poderosa y todavía inmadura. De riesgos que no se pueden corregir después.", tags: ["ensayo", "visión", "riesgo"], actors: ["amodei"] },
            { date: "2026", title: "Nadie está de acuerdo en nada", subtitle: "Comparten el diagnóstico. No el camino.", scene: "Todos dicen que la IA va a cambiar todo. Ninguno propone lo mismo. Las diferencias ya no se pueden disimular.", tags: ["visión", "conflicto", "futuro"], actors: ["altman", "amodei", "musk"] }
        ];

        const posturasData = [
            { tema: "Rol de la IA en el corto plazo", altman: { quote: "En 2025 veremos a los primeros agentes de IA unirse a la fuerza laboral y cambiar materialmente la producción de las empresas.", source: "Blog 'Reflections'", date: "2024" }, amodei: { quote: "Estamos en una adolescencia tecnológica que pondrá a prueba nuestra madurez.", source: "'The Adolescence of Technology'", date: "2024" }, musk: { quote: "La IA es potencialmente más peligrosa que las armas nucleares.", source: "IBTimes", date: "2025" } },
            { tema: "Riesgo existencial", altman: { quote: "La IA probablemente conducirá al fin del mundo, pero mientras tanto habrá grandes empresas.", source: "The Economic Times", date: "2024" }, amodei: { quote: "Riesgos serios fuera de proporción… como permitir a alguien sin experiencia crear armas químicas.", source: "CFR (charla)", date: "2024" }, musk: { quote: "La IA es una amenaza fundamental para la civilización.", source: "declaraciones públicas", date: "2025" } },
            { tema: "Filosofía de desarrollo", altman: { quote: "Implementación gradual e iterativa para que la sociedad se adapte y evolucione.", source: "Blog de Sam Altman", date: "2024" }, amodei: { quote: "Entrenar sistemas de IA para seguir un conjunto de principios explícitos.", source: "Anthropic / CFR", date: "2024" }, musk: { quote: "Crear una IA que busque la verdad máxima y comprenda el universo.", source: "Fox Business", date: "2025" } },
            { tema: "Velocidad vs. seguridad", altman: { quote: "Es mejor desplegar y aprender del uso en el mundo real que esperar en el laboratorio.", source: "LessWrong ('Planning for AGI')", date: "2023" }, amodei: { quote: "Hemos retrasado lanzamientos por preocupaciones de seguridad.", source: "declaraciones públicas Anthropic", date: "2024" }, musk: { quote: "La regulación no debe frenar la innovación ni favorecer monopolios.", source: "declaraciones públicas", date: "2025" } },
            { tema: "Economía de la IA", altman: { quote: "El costo de usar IA cae aproximadamente 10 veces cada 12 meses.", source: "Blog de Sam Altman", date: "2024" }, amodei: { quote: "Un país de genios en un centro de datos puede acelerar el descubrimiento científico.", source: "'Machines of Loving Grace'", date: "2024" }, musk: { quote: "Habrá una explosión en la economía global impulsada por IA y robots.", source: "IBTimes", date: "2025" } },
            { tema: "Trabajo y empleo", altman: { quote: "Los agentes de IA cambiarán materialmente la producción de las empresas.", source: "Blog 'Reflections'", date: "2024" }, amodei: { quote: "La productividad puede crecer mientras la participación laboral se estanca.", source: "análisis y entrevistas", date: "2024" }, musk: { quote: "Sin una renta básica, mucha gente quedará desplazada.", source: "declaraciones públicas", date: "2025" } },
            { tema: "Ética y sesgo", altman: { quote: "Buscamos mitigar riesgos mientras mantenemos utilidad en el mundo real.", source: "TIME", date: "2025" }, amodei: { quote: "Podemos explicar bajo qué principios entrenamos nuestros modelos.", source: "Anthropic (statement)", date: "2024" }, musk: { quote: "Los modelos actuales están entrenados para mentir (sesgo ideológico).", source: "Times of India", date: "2025" } },
            { tema: "Modelo de gobernanza", altman: { quote: "Necesitamos regulación para riesgos catastróficos, pero flexible.", source: "TIME / Davos", date: "2024–2025" }, amodei: { quote: "Se necesitan estándares claros y transparencia obligatoria.", source: "Anthropic statement", date: "2024" }, musk: { quote: "Debe haber un árbitro externo, no control corporativo cerrado.", source: "Fox Business", date: "2025" } },
            { tema: "Código abierto vs cerrado", altman: { quote: "Desarrollar AGI beneficiosa para toda la humanidad.", source: "OpenAI mission", date: "vigente" }, amodei: { quote: "La seguridad puede requerir limitar acceso a modelos avanzados.", source: "Anthropic", date: "2024" }, musk: { quote: "OpenAI se convirtió en código cerrado para maximizar beneficios.", source: "declaraciones públicas / demanda", date: "2025" } },
            { tema: "Relación con el Estado", altman: { quote: "Colaboración con gobiernos para gestionar riesgos.", source: "entrevistas y TIME", date: "2025" }, amodei: { quote: "No trabajaremos en vigilancia masiva ni armas autónomas.", source: "statement Anthropic", date: "2024" }, musk: { quote: "La IA debe servir a la civilización y la seguridad nacional.", source: "declaraciones públicas", date: "2025" } },
            { tema: "Visión de largo plazo", altman: { quote: "La inteligencia será abundante y podría eliminar la escasez.", source: "Blog de Sam Altman", date: "2024" }, amodei: { quote: "Podríamos vivir hasta 120 años con avances en biología impulsados por IA.", source: "entrevistas / ensayos", date: "2024" }, musk: { quote: "La IA superará a cualquier humano individual muy pronto.", source: "IBTimes", date: "2025" } }
        ];

        // STATE
        let currentActorFilter = 'all';
        let currentTypeFilter = 'all';
        let currentTwistActorFilter = 'all';
        let currentTwistTagFilter = 'all';

        // RENDER FUNCTIONS
        function renderTimeline() {
            const timeline = document.getElementById('timeline');
            timeline.innerHTML = '';
            
            let currentYear = '';
            let isLeft = true;
            
            const filteredData = timelineData.filter(item => {
                const actorMatch = currentActorFilter === 'all' || item.actors.includes(currentActorFilter);
                const typeMatch = currentTypeFilter === 'all' || item.type === currentTypeFilter;
                return actorMatch && typeMatch;
            });
            
            filteredData.forEach((item, index) => {
                if (item.year !== currentYear) {
                    currentYear = item.year;
                    const yearDiv = document.createElement('div');
                    yearDiv.className = 'timeline-year';
                    yearDiv.innerHTML = `<span>${currentYear}</span>`;
                    timeline.appendChild(yearDiv);
                }
                
                const itemDiv = document.createElement('div');
                itemDiv.className = `timeline-item ${isLeft ? 'left' : 'right'} size-${item.size || 'regular'}`;
                itemDiv.style.animationDelay = `${index * 0.1}s`;
                
                const actorTags = item.actors.map(actor => 
                    `<span class="actor-tag ${actor}">${actor === 'altman' ? 'Altman' : actor === 'amodei' ? 'Amodei' : actor === 'musk' ? 'Musk' : 'Otros'}</span>`
                ).join('');
                
                itemDiv.innerHTML = `
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-date">${item.date}</div>
                        <div class="timeline-title">${item.title}</div>
                        <div class="timeline-subtitle">${item.subtitle}</div>
                        <div class="timeline-actors">${actorTags}</div>
                    </div>
                `;
                
                timeline.appendChild(itemDiv);
                isLeft = !isLeft;
            });
        }

        function renderTwists() {
            const grid = document.getElementById('twists-grid');
            grid.innerHTML = '';
            
            const filteredData = twistsData.filter(item => {
                const actorMatch = currentTwistActorFilter === 'all' || item.actors.some(actor => actor === currentTwistActorFilter);
                const tagMatch = currentTwistTagFilter === 'all' || item.tags.includes(currentTwistTagFilter);
                return actorMatch && tagMatch;
            });
            
            filteredData.forEach((item, index) => {
                const card = document.createElement('div');
                card.className = 'twist-card';
                card.style.animationDelay = `${index * 0.15}s`;
                
                const tagsHtml = item.tags.map(tag => 
                    `<span class="twist-tag" data-tag="${tag}">${tag}</span>`
                ).join('');
                
                card.innerHTML = `
                    <div class="twist-date">${item.date}</div>
                    <div class="twist-title">${item.title}</div>
                    <div class="twist-subtitle">${item.subtitle}</div>
                    <div class="twist-scene">${item.scene}</div>
                    <div class="twist-tags">${tagsHtml}</div>
                `;
                
                grid.appendChild(card);
            });
            
            // Add click handlers for tags
            document.querySelectorAll('.twist-tag').forEach(tag => {
                tag.addEventListener('click', (e) => {
                    e.stopPropagation();
                    const tagValue = tag.dataset.tag;
                    currentTwistTagFilter = tagValue;
                    document.querySelectorAll('.filter-twist-tag').forEach(b => b.classList.remove('active'));
                    document.querySelector(`.filter-twist-tag[data-tag="${tagValue}"]`).classList.add('active');
                    renderTwists();
                });
            });
        }

        function renderPosturas() {
            const grid = document.getElementById('posturas-grid');
            grid.innerHTML = '';
            
            posturasData.forEach((item, index) => {
                const postura = document.createElement('div');
                postura.className = 'postura-item';
                
                postura.innerHTML = `
                    <div class="postura-header" onclick="togglePostura(${index})">
                        <div class="postura-title">${item.tema}</div>
                        <div class="postura-hint">Click para ver las tres posturas →</div>
                    </div>
                    <div class="postura-content" id="postura-${index}">
                        <div class="postura-grid">
                            <div class="postura-card">
                                <div class="postura-name">Sam Altman</div>
                                <div class="postura-quote">"${item.altman.quote}"</div>
                                <div class="postura-source">Fuente: ${item.altman.source} (${item.altman.date})</div>
                            </div>
                            <div class="postura-card">
                                <div class="postura-name">Dario Amodei</div>
                                <div class="postura-quote">"${item.amodei.quote}"</div>
                                <div class="postura-source">Fuente: ${item.amodei.source} (${item.amodei.date})</div>
                            </div>
                            <div class="postura-card">
                                <div class="postura-name">Elon Musk</div>
                                <div class="postura-quote">"${item.musk.quote}"</div>
                                <div class="postura-source">Fuente: ${item.musk.source} (${item.musk.date})</div>
                            </div>
                        </div>
                    </div>
                `;
                
                grid.appendChild(postura);
            });
        }

        // FILTER FUNCTIONS
        function togglePostura(index) {
            const content = document.getElementById(`postura-${index}`);
            content.classList.toggle('expanded');
        }

        // EVENT LISTENERS
        document.querySelectorAll('.filter-actor').forEach(btn => {
            btn.addEventListener('click', (e) => {
                currentActorFilter = btn.dataset.actor;
                document.querySelectorAll('.filter-actor').forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                renderTimeline();
            });
        });

        document.querySelectorAll('.filter-type').forEach(btn => {
            btn.addEventListener('click', (e) => {
                currentTypeFilter = btn.dataset.type;
                document.querySelectorAll('.filter-type').forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                renderTimeline();
            });
        });

        document.querySelectorAll('.filter-twist-actor').forEach(btn => {
            btn.addEventListener('click', (e) => {
                currentTwistActorFilter = btn.dataset.actor;
                document.querySelectorAll('.filter-twist-actor').forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                renderTwists();
            });
        });

        document.querySelectorAll('.filter-twist-tag').forEach(btn => {
            btn.addEventListener('click', (e) => {
                currentTwistTagFilter = btn.dataset.tag;
                document.querySelectorAll('.filter-twist-tag').forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                renderTwists();
            });
        });

        // INITIALIZE
        renderTimeline();
        renderTwists();
        renderPosturas();

        // SCROLL ANIMATIONS
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Re-observe when content changes
        function observeElements() {
            document.querySelectorAll('.timeline-item, .twist-card').forEach(el => {
                observer.observe(el);
            });
        }

        observeElements();
    </script>
</body>
</html>
