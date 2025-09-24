<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Lora:ital,wght@1,400&family=Parisienne&display=swap" rel="stylesheet">
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>💌</text></svg>">

    <title>Un Mensaje Especial para ti Damaris</title>

    <style>
        :root {
            --color-fondo-gradiente-1: #e0c3fc;
            --color-fondo-gradiente-2: #8ec5fc;
            --color-sobre-cuerpo: #ffdde1;
            --color-sobre-solapa: #eeb7c2;
            --color-sobre-solapa-superior: #fbe2e7;
            --color-carta: #fdfbfb;
            --color-sello: #cf425c;
            --color-sombra-fuerte: rgba(0, 0, 0, 0.25);
            --color-sombra-suave: rgba(0, 0, 0, 0.1);
            --color-texto: #3a3a3a;
            --color-firma: #c91515;
            --fuente-titulo: 'Great Vibes', cursive;
            --fuente-fecha: 'Lora', serif;
            --fuente-carta: 'Parisienne', cursive;
            --duracion-apertura: 1.7s;
        }

        /* --- PANTALLA DE CARGA --- */
        #loader {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: #f0f0f0; display: flex; justify-content: center; align-items: center;
            flex-direction: column; z-index: 1000; transition: opacity 0.7s ease, visibility 0.7s ease;
        }
        #loader.hidden { opacity: 0; visibility: hidden; }
        .loader-icon { font-size: 80px; color: var(--color-sello); }
        .progress-bar-container {
            width: 250px; height: 15px; background-color: #e0e0e0;
            border-radius: 10px; overflow: hidden; margin-top: 20px;
            box-shadow: inset 0 1px 3px rgba(0,0,0,0.1);
        }
        .progress-bar {
            width: 0%; height: 100%; background-color: var(--color-sello);
            border-radius: 10px; transition: width 0.3s ease;
        }
        #progress-percentage {
            margin-top: 10px; font-family: 'Lora', serif;
            font-size: 1rem; color: #555;
        }

        body {
            margin: 0; padding: 20px; box-sizing: border-box;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, var(--color-fondo-gradiente-1) 0%, var(--color-fondo-gradiente-2) 100%), 
                url('https://drive.google.com/uc?id=1uv9wOVYu8h8PbX4EDBPl4YUm0ZMYNOj1&sz=w1000');
            background-size: cover; background-position: center;
            background-blend-mode: screen; overflow: hidden;
            font-family: 'Parisienne', cursive;
            -webkit-user-select: none; /* Safari */
            -moz-user-select: none;    /* Firefox */
            -ms-user-select: none;     /* Internet Explorer/Edge */
            user-select: none;         /* Estándar */
            -webkit-tap-highlight-color: transparent;
        }
        
        .main-content { /* Contenedor para mover título y sobre juntos */
            display: flex; flex-direction: column; align-items: center;
            transition: transform 0.5s ease;
        }

        h1 {
            font-family: var(--fuente-titulo); font-size: clamp(2.5rem, 10vw, 5rem);
            color: #f63afd93; text-shadow: 3px 3px 10px var(--color-sombra-fuerte);
            text-align: center; margin-bottom: 40px; line-height: 1.1;
        }

        .contenedor { perspective: 1500px; }

        .envoltura-sobre {
            position: relative; width: 320px; height: 220px;
            cursor: pointer;
            filter: drop-shadow(0px 20px 25px var(--color-sombra-fuerte));
            animation: latido 2.5s cubic-bezier(0.4, 0, 0.2, 1) infinite;
        }
        
        .envoltura-sobre.abierto, .envoltura-sobre.cerrando { animation: none; }

        /* --- LATIDO DE CARTA INCREMENTADO (MODIFICADO) --- */
        @keyframes latido {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.07); } /* Aumentado de 1.05 a 1.07 */
        }

        .sobre {
            position: absolute; width: 100%; height: 100%;
            background-color: var(--color-sobre-cuerpo);
            border-radius: 15px; box-shadow: inset 0 0 30px var(--color-sombra-suave);
        }

        .carta {
            position: fixed; top: 50%; left: 50%;
            width: 320px; height: 220px;
            transform: translate(-50%, -40%) scale(1);
            opacity: 0; z-index: 1; pointer-events: none;
            background: var(--color-carta);
            border-radius: 10px; padding: 25px; box-sizing: border-box;
            background-image: url('https://drive.google.com/uc?id=1MD6SmwkJ_5hhSCON1E9oUV6CJqL2BTKb&sz=w1000');
            background-size: cover; background-position: center;
            background-blend-mode: screen; background-color: rgba(255, 255, 255, 0.6);
        }

        /* --- MEDIOS --- */
        @media (max-width: 768px) {
            .main-content { transform: translateY(-5vh); }
            h1 { font-size: 2.9rem; }
            .envoltura-sobre { width: 280px; height: 193px; }
            .contenido { padding-right: 5px;}
            .contenido .saludo { font-size: 1.5rem; }
            .contenido .cuerpo { font-size: 1.0rem; }
            .contenido .firma { font-size: 1.5rem; text-align: center; }

            .bloque-firma {
                flex-direction: column;
                align-items: center;
                gap: 20px;
            }
            .imagen-recuerdo {
                width: 70%;
                max-width: 100px;
            }
        }
    </style>
