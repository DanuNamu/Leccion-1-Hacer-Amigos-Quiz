<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🏴‍☠️ El Tesoro de la Amistad - Quiz Lección 1 | Español Para Hacer Amigos</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Nunito:wght@600;700;800&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Nunito', sans-serif;
      background-color: #f3e5ab;
      background-image: 
        radial-gradient(circle at 20% 20%, rgba(212, 163, 89, 0.25) 0%, transparent 40%),
        radial-gradient(circle at 80% 80%, rgba(180, 120, 50, 0.25) 0%, transparent 40%),
        repeating-linear-gradient(45deg, rgba(168, 126, 70, 0.05) 0px, rgba(168, 126, 70, 0.05) 2px, transparent 2px, transparent 10px);
      min-height: 100vh;
      overflow-x: hidden;
    }

    h1, h2, h3, .font-fredoka {
      font-family: 'Fredoka', sans-serif;
    }

    /* Pergamino y Mapa */
    .parchment-card {
      background: linear-gradient(135deg, #fff9e6 0%, #f7e7c4 100%);
      border: 4px solid #8b5a2b;
      box-shadow: 0 12px 0 #5c3a18, 0 18px 25px rgba(0,0,0,0.25);
      border-radius: 28px;
      position: relative;
    }

    .wood-bar {
      background: linear-gradient(180deg, #8b5a2b 0%, #6b421c 100%);
      border-bottom: 4px solid #4a2c11;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }

    .btn-pirate {
      transition: all 0.15s cubic-bezier(0.34, 1.56, 0.64, 1);
      box-shadow: 0 6px 0 #b45309;
    }
    .btn-pirate:hover:not(:disabled) {
      transform: translateY(-2px);
      box-shadow: 0 8px 0 #b45309;
    }
    .btn-pirate:active:not(:disabled) {
      transform: translateY(4px);
      box-shadow: 0 2px 0 #b45309;
    }

    .option-card {
      background: #ffffff;
      border: 3px solid #d4a373;
      box-shadow: 0 6px 0 #c9935b;
      transition: all 0.2s cubic-bezier(0.34, 1.56, 0.64, 1);
    }
    .option-card:hover:not(:disabled) {
      transform: translateY(-3px) scale(1.01);
      border-color: #f59e0b;
      background: #fffbeb;
    }
    .option-card:active:not(:disabled) {
      transform: translateY(3px);
      box-shadow: 0 2px 0 #c9935b;
    }

    .option-correct {
      background: #dcfce7 !important;
      border-color: #22c55e !important;
      box-shadow: 0 6px 0 #16a34a !important;
      animation: bounceShort 0.5s ease;
    }

    .option-wrong {
      background: #fee2e2 !important;
      border-color: #ef4444 !important;
      box-shadow: 0 6px 0 #dc2626 !important;
      animation: shake 0.4s ease;
    }

    @keyframes bounceShort {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.04); }
    }

    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-8px); }
      75% { transform: translateX(8px); }
    }

    @keyframes floatBear {
      0%, 100% { transform: translateY(0px) rotate(0deg); }
      50% { transform: translateY(-7px) rotate(1.5deg); }
    }

    .chibi-bear {
      animation: floatBear 3s ease-in-out infinite;
    }

    @keyframes heartPop {
      0% { transform: scale(0.5); opacity: 0; }
      70% { transform: scale(1.3); }
      100% { transform: scale(1); opacity: 1; }
    }

    .heart-anim {
      animation: heartPop 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
    }

    /* Ruta punteada del mapa */
    .map-path {
      stroke-dasharray: 8, 8;
      animation: dashMove 20s linear infinite;
    }

    @keyframes dashMove {
      to { stroke-dashoffset: -200; }
    }

    .confetti {
      position: fixed;
      width: 10px;
      height: 10px;
      top: -10px;
      z-index: 50;
      animation: fall linear forwards;
    }

    @keyframes fall {
      to {
        transform: translateY(105vh) rotate(720deg);
      }
    }
  </style>
</head>
<body class="text-amber-950 select-none flex flex-col">

  <!-- BARRA SUPERIOR DE NAVEGACIÓN Y VIDAS -->
  <header class="wood-bar text-amber-50 px-4 py-3 sticky top-0 z-40">
    <div class="max-w-5xl mx-auto flex flex-wrap items-center justify-between gap-3">
      
      <!-- Título del Curso -->
      <div class="flex items-center gap-2">
        <span class="text-2xl sm:text-3xl">🏴‍☠️</span>
        <div>
          <h1 class="font-fredoka text-lg sm:text-xl font-bold leading-tight text-amber-200">
            Español Para Hacer Amigos
          </h1>
          <p class="text-xs text-amber-100/80 font-semibold">Nivel 1 · Lección 1: El Mapa de la Amistad</p>
        </div>
      </div>

      <!-- Contador de Vidas Dinámico -->
      <div class="flex items-center gap-3 bg-amber-950/60 px-4 py-1.5 rounded-full border-2 border-amber-500/50">
        <span class="text-xs sm:text-sm font-bold uppercase tracking-wider text-amber-200">Vidas:</span>
        <div id="lives-container" class="flex items-center gap-1 text-xl sm:text-2xl">
          <!-- Corazones renderizados por JS -->
        </div>
        <span id="life-bonus-badge" class="hidden text-xs bg-emerald-500 text-white font-bold px-2 py-0.5 rounded-full animate-bounce">
          +1 Vida!
        </span>
      </div>

      <!-- Progreso y Botón de Audio Global -->
      <div class="flex items-center gap-3">
        <div class="bg-amber-900/80 px-3 py-1 rounded-xl border border-amber-400/40 text-sm font-bold">
          🪙 <span id="score-display">0</span> / 10
        </div>
        <button id="toggle-sound-btn" onclick="toggleMute()" title="Activar/Silenciar efectos" class="bg-amber-500 hover:bg-amber-400 text-amber-950 font-bold p-2 rounded-xl shadow transition">
          🔊
        </button>
      </div>
    </div>
  </header>

  <!-- CONTENIDO PRINCIPAL -->
  <main class="flex-1 max-w-5xl w-full mx-auto px-4 py-6 flex flex-col gap-6">

    <!-- MAPA DE AVENTURA VISUAL (PROGRESO DE 10 ISLAS / PARADAS) -->
    <section class="parchment-card p-4 sm:p-5">
      <div class="flex items-center justify-between mb-2">
        <span class="font-fredoka font-bold text-amber-900 text-sm sm:text-base flex items-center gap-1.5">
          🗺️ Ruta del Tesoro de la Amistad
        </span>
        <span id="step-indicator" class="text-xs sm:text-sm font-extrabold bg-amber-200 text-amber-900 px-3 py-1 rounded-full border border-amber-400">
          Parada 1 de 10
        </span>
      </div>

      <!-- Mapa SVG Interactivo con Islas -->
      <div class="relative w-full overflow-x-auto pb-2">
        <div class="min-w-[620px] relative h-20 flex items-center justify-between px-4">
          <!-- Línea punteada de ruta -->
          <svg class="absolute inset-0 w-full h-full pointer-events-none" preserveAspectRatio="none">
            <path d="M 35 45 Q 150 15, 280 45 T 585 45" fill="none" stroke="#b45309" stroke-width="4" class="map-path" />
          </svg>
          
          <!-- Nodos de las 10 paradas -->
          <div id="map-nodes" class="relative z-10 w-full flex justify-between items-center">
            <!-- Generado por JS -->
          </div>
        </div>
      </div>
    </section>

    <!-- PANTALLA DE INICIO (BIENVENIDA DEL OSITO PIRATA) -->
    <section id="start-screen" class="parchment-card p-6 sm:p-10 text-center flex flex-col items-center">
      <!-- Mascota Chibi Osito Pirata SVG -->
      <div class="chibi-bear mb-4">
        <svg width="160" height="160" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
          <!-- Sombrero Pirata -->
          <path d="M35 72 Q100 20 165 72 Q155 88 100 84 Q45 88 35 72 Z" fill="#292524" stroke="#1c1917" stroke-width="4"/>
          <path d="M42 70 Q100 58 158 70" fill="none" stroke="#f59e0b" stroke-width="4"/>
          <!-- Calavera chibi en el sombrero -->
          <circle cx="100" cy="52" r="9" fill="#fef3c7"/>
          <circle cx="97" cy="51" r="2" fill="#292524"/>
          <circle cx="103" cy="51" r="2" fill="#292524"/>
          <rect x="96" y="59" width="8" height="4" rx="1" fill="#fef3c7"/>
          <!-- Pluma roja en el sombrero -->
          <path d="M142 54 Q172 30 176 48 Q165 62 145 62 Z" fill="#ef4444" stroke="#b91c1c" stroke-width="2"/>

          <!-- Orejas de osito -->
          <circle cx="58" cy="78" r="18" fill="#60a5fa" stroke="#1d4ed8" stroke-width="4"/>
          <circle cx="58" cy="78" r="9" fill="#bfdbfe"/>
          <circle cx="142" cy="78" r="18" fill="#60a5fa" stroke="#1d4ed8" stroke-width="4"/>
          <circle cx="142" cy="78" r="9" fill="#bfdbfe"/>

          <!-- Cabeza Chibi -->
          <ellipse cx="100" cy="112" rx="52" ry="44" fill="#60a5fa" stroke="#1d4ed8" stroke-width="4"/>
          
          <!-- Ojo Izquierdo (Brillante Chibi) -->
          <circle cx="78" cy="106" r="9" fill="#1e293b"/>
          <circle cx="75" cy="103" r="3.5" fill="#ffffff"/>
          <circle cx="81" cy="109" r="1.5" fill="#ffffff"/>

          <!-- Parche Pirata en Ojo Derecho -->
          <path d="M62 86 L142 114" stroke="#1c1917" stroke-width="3.5"/>
          <path d="M112 96 Q126 94 134 104 Q132 120 120 120 Q108 118 112 96 Z" fill="#1c1917"/>

          <!-- Mejillas rosadas -->
          <ellipse cx="64" cy="120" rx="7" ry="4" fill="#f472b6" opacity="0.7"/>
          <ellipse cx="136" cy="120" rx="7" ry="4" fill="#f472b6" opacity="0.7"/>

          <!-- Hocico y Sonrisa -->
          <ellipse cx="100" cy="124" rx="18" ry="13" fill="#eff6ff"/>
          <ellipse cx="100" cy="119" rx="6" ry="4" fill="#1e3a8a"/>
          <path d="M91 128 Q100 136 109 128" fill="none" stroke="#1e3a8a" stroke-width="3" stroke-linecap="round"/>

          <!-- Pañuelo pirata en el cuello -->
          <path d="M66 150 Q100 162 134 150 L126 168 Q100 174 74 168 Z" fill="#ef4444" stroke="#991b1b" stroke-width="3"/>
          <circle cx="100" cy="160" r="5" fill="#f59e0b"/>

          <!-- Cuerpo y Chaleco Pirata -->
          <path d="M65 162 Q100 156 135 162 L142 192 L58 192 Z" fill="#3b82f6" stroke="#1d4ed8" stroke-width="4"/>
          <path d="M72 162 L85 192 L62 192 Z" fill="#f59e0b"/>
          <path d="M128 162 L115 192 L138 192 Z" fill="#f59e0b"/>
        </svg>
      </div>

      <span class="bg-amber-200 text-amber-900 font-extrabold text-xs uppercase tracking-widest px-4 py-1 rounded-full border border-amber-400 mb-2">
        Capitán Milo te da la bienvenida
      </span>
      <h2 class="font-fredoka text-3xl sm:text-4xl font-bold text-amber-950 mb-3">
        ¡Ahoy, Explorador! ¿Listo para el Reto Final?
      </h2>
      <p class="max-w-xl text-base sm:text-lg text-amber-900 mb-6 leading-relaxed">
        Soy el <strong>Capitán Milo</strong> y conozco todos los secretos del español. Escucha mis pistas de audio, elige la respuesta correcta y cruza las <strong>10 islas del mapa</strong>.
      </p>

      <!-- Reglas de Vidas -->
      <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 w-full max-w-2xl mb-8 text-left">
        <div class="bg-white/80 p-3.5 rounded-2xl border-2 border-amber-300 flex items-center gap-3">
          <span class="text-2xl">❤️❤️❤️</span>
          <div class="text-xs sm:text-sm">
            <strong class="block text-amber-950">Empiezas con 3 vidas</strong>
            <span class="text-amber-800">¡Cuídalas en tu viaje!</span>
          </div>
        </div>
        <div class="bg-emerald-50 p-3.5 rounded-2xl border-2 border-emerald-300 flex items-center gap-3">
          <span class="text-2xl">💖✨</span>
          <div class="text-xs sm:text-sm">
            <strong class="block text-emerald-900">+1 Vida al acertar</strong>
            <span class="text-emerald-800">Cada acierto suma una vida extra.</span>
          </div>
        </div>
        <div class="bg-sky-50 p-3.5 rounded-2xl border-2 border-sky-300 flex items-center gap-3">
          <span class="text-2xl">🔊🎧</span>
          <div class="text-xs sm:text-sm">
            <strong class="block text-sky-900">Audios en Español</strong>
            <span class="text-sky-800">Escucha y aprende pronunciación.</span>
          </div>
        </div>
      </div>

      <button onclick="startQuiz()" class="btn-pirate bg-amber-500 hover:bg-amber-400 text-amber-950 font-fredoka text-xl sm:text-2xl font-bold px-8 py-4 rounded-2xl flex items-center gap-3 cursor-pointer">
        <span>⛵ ¡Zarpar hacia la Aventura!</span>
      </button>
    </section>

    <!-- PANTALLA DEL QUIZ ACTIVO -->
    <section id="quiz-screen" class="hidden parchment-card p-5 sm:p-8">
      <div class="flex flex-col md:flex-row gap-6 items-center md:items-start">
        
        <!-- Columna Izquierda: Capitán Milo Chibi + Botón de Audio -->
        <div class="w-full md:w-1/3 flex flex-col items-center bg-amber-100/70 p-4 rounded-3xl border-2 border-amber-300/80">
          <!-- Mini Chibi Milo -->
          <div id="milo-avatar" class="chibi-bear mb-2">
            <svg width="115" height="115" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
              <path d="M35 72 Q100 20 165 72 Q155 88 100 84 Q45 88 35 72 Z" fill="#292524" stroke="#1c1917" stroke-width="4"/>
              <path d="M42 70 Q100 58 158 70" fill="none" stroke="#f59e0b" stroke-width="4"/>
              <circle cx="100" cy="52" r="8" fill="#fef3c7"/>
              <path d="M142 54 Q172 30 176 48 Q165 62 145 62 Z" fill="#ef4444"/>
              <circle cx="58" cy="78" r="18" fill="#60a5fa" stroke="#1d4ed8" stroke-width="4"/>
              <circle cx="142" cy="78" r="18" fill="#60a5fa" stroke="#1d4ed8" stroke-width="4"/>
              <ellipse cx="100" cy="112" rx="52" ry="44" fill="#60a5fa" stroke="#1d4ed8" stroke-width="4"/>
              <circle cx="78" cy="106" r="9" fill="#1e293b"/>
              <circle cx="75" cy="103" r="3.5" fill="#ffffff"/>
              <path d="M62 86 L142 114" stroke="#1c1917" stroke-width="3.5"/>
              <path d="M112 96 Q126 94 134 104 Q132 120 120 120 Q108 118 112 96 Z" fill="#1c1917"/>
              <ellipse cx="64" cy="120" rx="7" ry="4" fill="#f472b6" opacity="0.7"/>
              <ellipse cx="136" cy="120" rx="7" ry="4" fill="#f472b6" opacity="0.7"/>
              <ellipse cx="100" cy="124" rx="18" ry="13" fill="#eff6ff"/>
              <ellipse cx="100" cy="119" rx="6" ry="4" fill="#1e3a8a"/>
              <path id="milo-mouth" d="M91 128 Q100 136 109 128" fill="none" stroke="#1e3a8a" stroke-width="3" stroke-linecap="round"/>
              <path d="M66 150 Q100 162 134 150 L126 168 Q100 174 74 168 Z" fill="#ef4444" stroke="#991b1b" stroke-width="3"/>
              <circle cx="100" cy="160" r="5" fill="#f59e0b"/>
            </svg>
          </div>

          <!-- Globo de diálogo del Capitán Milo -->
          <div class="bg-white p-3 rounded-2xl border-2 border-amber-400 text-center w-full shadow-sm mb-3">
            <p id="milo-speech" class="text-xs sm:text-sm font-bold text-amber-900">
              "¡Escucha con atención la pista en español!"
            </p>
          </div>

          <!-- Controles de Audio de la Pregunta -->
          <div class="flex flex-col gap-2 w-full">
            <button onclick="playQuestionAudio(1.0)" class="w-full bg-sky-500 hover:bg-sky-400 text-white font-fredoka font-bold py-2.5 px-4 rounded-xl shadow-[0_4px_0_#0369a1] active:translate-y-1 transition flex items-center justify-center gap-2 cursor-pointer">
              <span class="text-lg">🔊</span> Escuchar Audio
            </button>
            <button onclick="playQuestionAudio(0.65)" class="w-full bg-teal-500 hover:bg-teal-400 text-white font-fredoka text-sm font-bold py-2 px-3 rounded-xl shadow-[0_4px_0_#0f766e] active:translate-y-1 transition flex items-center justify-center gap-2 cursor-pointer">
              <span>🐢</span> Escuchar Lento
            </button>
          </div>
        </div>

        <!-- Columna Derecha: Pregunta y Opciones -->
        <div class="w-full md:w-2/3 flex flex-col justify-between">
          <div>
            <div class="flex items-center gap-2 mb-2">
              <span id="question-topic" class="bg-amber-500/20 text-amber-900 border border-amber-500/40 text-xs font-extrabold px-3 py-1 rounded-full">
                Tema: Saludos
              </span>
            </div>

            <h3 id="question-text" class="font-fredoka text-2xl sm:text-3xl font-bold text-amber-950 mb-2">
              Cargando pregunta...
            </h3>
            <p id="question-subtext" class="text-sm text-amber-800 font-semibold mb-5">
              Selecciona la opción correcta o toca el altavoz en cada tarjeta para escucharla.
            </p>

            <!-- Opciones de Respuesta -->
            <div id="options-container" class="grid grid-cols-1 gap-3.5">
              <!-- Opciones renderizadas por JS -->
            </div>
          </div>

          <!-- Retroalimentación Inmediata y Botón Siguiente -->
          <div id="feedback-box" class="hidden mt-6 p-4 rounded-2xl border-2 flex flex-col sm:flex-row items-center justify-between gap-4">
            <div class="flex items-center gap-3">
              <span id="feedback-icon" class="text-3xl">🎉</span>
              <div>
                <h4 id="feedback-title" class="font-fredoka font-bold text-lg">¡Excelente!</h4>
                <p id="feedback-desc" class="text-sm font-semibold">Explicación aquí</p>
              </div>
            </div>
            <button id="next-btn" onclick="nextQuestion()" class="btn-pirate bg-amber-500 hover:bg-amber-400 text-amber-950 font-fredoka font-bold px-6 py-3 rounded-xl whitespace-nowrap cursor-pointer">
              Siguiente Isla ➡️
            </button>
          </div>
        </div>

      </div>
    </section>

    <!-- PANTALLA DE GAME OVER (SIN VIDAS) -->
    <section id="gameover-screen" class="hidden parchment-card p-6 sm:p-10 text-center flex flex-col items-center">
      <div class="text-6xl mb-3">🌊⛵</div>
      <h2 class="font-fredoka text-3xl sm:text-4xl font-bold text-rose-700 mb-2">
        ¡Oh no! Nuestro barco encalló
      </h2>
      <p class="max-w-md text-amber-900 text-base sm:text-lg mb-6">
        Nos quedamos sin vidas en el mapa, pero un buen pirata nunca se rinde. ¡El Capitán Milo te ayuda a intentarlo de nuevo!
      </p>
      <button onclick="restartQuiz()" class="btn-pirate bg-amber-500 hover:bg-amber-400 text-amber-950 font-fredoka text-xl font-bold px-8 py-4 rounded-2xl cursor-pointer">
        🔄 Intentar la Aventura de Nuevo
      </button>
    </section>

    <!-- PANTALLA FINAL DE VICTORIA (TESORO E INSIGNIA) -->
    <section id="victory-screen" class="hidden parchment-card p-6 sm:p-10 text-center flex flex-col items-center">
      <div class="text-6xl sm:text-7xl mb-3 animate-bounce">🏆👑</div>
      <span class="bg-emerald-100 text-emerald-800 border border-emerald-400 font-extrabold text-xs uppercase tracking-wider px-4 py-1 rounded-full mb-2">
        ¡Misión Cumplida · Lección 1 Aprobada!
      </span>
      <h2 class="font-fredoka text-3xl sm:text-4xl font-bold text-amber-950 mb-2">
        ¡Encontraste el Tesoro de la Amistad!
      </h2>
      <p class="max-w-xl text-amber-900 text-base sm:text-lg mb-6">
        ¡Felicidades, grumete! El Capitán Milo está muy orgulloso de ti. Ahora ya sabes saludar, decir tu nombre, tu edad, tus gustos y usar palabras mágicas en español.
      </p>

      <!-- Resumen de Estadísticas -->
      <div class="grid grid-cols-2 sm:grid-cols-3 gap-4 w-full max-w-lg mb-6">
        <div class="bg-white p-4 rounded-2xl border-2 border-amber-300">
          <div class="text-2xl font-fredoka font-bold text-amber-600" id="final-score">10/10</div>
          <div class="text-xs font-bold text-amber-800 uppercase">Aciertos</div>
        </div>
        <div class="bg-white p-4 rounded-2xl border-2 border-rose-300">
          <div class="text-2xl font-fredoka font-bold text-rose-600" id="final-lives">❤️ 13</div>
          <div class="text-xs font-bold text-amber-800 uppercase">Vidas Finales</div>
        </div>
        <div class="col-span-2 sm:col-span-1 bg-amber-100 p-4 rounded-2xl border-2 border-amber-400">
          <div class="text-2xl">🏅</div>
          <div class="text-xs font-extrabold text-amber-950 uppercase">Amigo Nivel 1</div>
        </div>
      </div>

      <!-- Insignia Desbloqueada -->
      <div class="bg-gradient-to-r from-amber-200 via-yellow-100 to-amber-200 p-5 rounded-3xl border-4 border-amber-500 max-w-md w-full mb-6 shadow-md">
        <p class="font-fredoka font-bold text-lg text-amber-950 mb-1">🎖️ Insignia Desbloqueada</p>
        <p class="text-sm text-amber-900 font-semibold">"Explorador Oficial de Español Para Hacer Amigos — Nivel 1 · Lección 1"</p>
      </div>

      <div class="flex flex-wrap justify-center gap-4">
        <button onclick="restartQuiz()" class="btn-pirate bg-amber-500 hover:bg-amber-400 text-amber-950 font-fredoka text-lg font-bold px-6 py-3 rounded-2xl cursor-pointer">
          🔁 Volver a Jugar
        </button>
      </div>
    </section>

  </main>

  <script>
    // BANCO DE 10 PREGUNTAS DE LA LECCIÓN 1 ("UN NUEVO AMIGO")
    const questions = [
      {
        topic: "1. Saludos del día",
        icon: "☀️",
        question: "Escucha al Capitán Milo. ¿Qué dices cuando sale el sol por la mañana?",
        audioPrompt: "¡Buenos días! ¿Cómo estás?",
        options: [
          { text: "¡Buenos días!", audio: "¡Buenos días!", emoji: "☀️", correct: true },
          { text: "¡Buenas noches!", audio: "¡Buenas noches!", emoji: "🌙", correct: false },
          { text: "¡Hasta pronto!", audio: "¡Hasta pronto!", emoji: "👋", correct: false }
        ],
        explanation: "¡Exacto! Decimos '¡Buenos días!' por la mañana cuando sale el sol."
      },
      {
        topic: "2. Presentarse",
        icon: "🐻",
        question: "Milo te pregunta: '¿Cómo te llamas?'. ¿Cómo respondes correctamente?",
        audioPrompt: "¡Hola! ¿Cómo te llamas?",
        options: [
          { text: "Tengo ocho años.", audio: "Tengo ocho años.", emoji: "🎂", correct: false },
          { text: "Me llamo Sofía.", audio: "Me llamo Sofía.", emoji: "👧", correct: true },
          { text: "Muchas gracias.", audio: "Muchas gracias.", emoji: "💖", correct: false }
        ],
        explanation: "¡Muy bien! Para decir tu nombre en español usas 'Me llamo...'."
      },
      {
        topic: "3. Palabras Mágicas",
        icon: "🙏",
        question: "Luna te regala un dibujo muy bonito. ¿Qué palabra mágica le dices?",
        audioPrompt: "Toma este dibujo para ti.",
        options: [
          { text: "Muchas gracias", audio: "Muchas gracias", emoji: "💖", correct: true },
          { text: "Por favor", audio: "Por favor", emoji: "🙏", correct: false },
          { text: "¿Cómo estás?", audio: "¿Cómo estás?", emoji: "❓", correct: false }
        ],
        explanation: "¡Genial! Cuando recibes un regalo o ayuda, siempre dices 'Muchas gracias'."
      },
      {
        topic: "4. Decir tu Edad",
        icon: "🎂",
        question: "Escucha la pregunta de Leo y elige la respuesta correcta sobre tu edad:",
        audioPrompt: "¿Cuántos años tienes?",
        options: [
          { text: "Soy de Canadá.", audio: "Soy de Canadá.", emoji: "🍁", correct: false },
          { text: "Estoy muy feliz.", audio: "Estoy muy feliz.", emoji: "😄", correct: false },
          { text: "Tengo nueve años.", audio: "Tengo nueve años.", emoji: "9️⃣", correct: true }
        ],
        explanation: "¡Brillante! En español usamos 'Tengo [número] años' para decir nuestra edad."
      },
      {
        topic: "5. Emociones",
        icon: "😄",
        question: "Escucha cómo se siente Coral hoy y elige la carita correcta:",
        audioPrompt: "¡Hola amigo! Hoy estoy muy feliz.",
        options: [
          { text: "Estoy muy feliz", audio: "Estoy muy feliz", emoji: "😄", correct: true },
          { text: "Tengo sueño", audio: "Tengo sueño", emoji: "😴", correct: false },
          { text: "¡Adiós!", audio: "¡Adiós!", emoji: "👋", correct: false }
        ],
        explanation: "¡Así se hace! 'Estoy muy feliz' significa que estás muy contento."
      },
      {
        topic: "6. Gustos y Pasatiempos",
        icon: "⚽",
        question: "Milo quiere jugar contigo. Escucha lo que le gusta hacer:",
        audioPrompt: "Me gusta jugar al fútbol y dibujar.",
        options: [
          { text: "Me gusta leer", audio: "Me gusta leer", emoji: "📚", correct: false },
          { text: "Me gusta jugar al fútbol", audio: "Me gusta jugar al fútbol", emoji: "⚽", correct: true },
          { text: "Mucho gusto", audio: "Mucho gusto", emoji: "🤝", correct: false }
        ],
        explanation: "¡Golazo! 'Me gusta jugar al fútbol' expresa tu pasatiempo favorito."
      },
      {
        topic: "7. Cortesía al Conocer a Alguien",
        icon: "🤝",
        question: "Acabas de conocer a un nuevo amigo en el parque. ¿Qué dices al darle la mano?",
        audioPrompt: "Hola, me llamo Leo. ¡Mucho gusto!",
        options: [
          { text: "¡Mucho gusto!", audio: "¡Mucho gusto!", emoji: "🤝", correct: true },
          { text: "¡Buenas noches!", audio: "¡Buenas noches!", emoji: "🛌", correct: false },
          { text: "De nada", audio: "De nada", emoji: "😊", correct: false }
        ],
        explanation: "¡Excelente educación! '¡Mucho gusto!' se dice cuando conoces a alguien por primera vez."
      },
      {
        topic: "8. Pedir con Amabilidad",
        icon: "🖍️",
        question: "Quieres pedirle un lápiz a Sofía. ¿Qué palabras mágicas debes usar?",
        audioPrompt: "¿Me prestas un lápiz, por favor?",
        options: [
          { text: "¡Hasta pronto!", audio: "¡Hasta pronto!", emoji: "👋", correct: false },
          { text: "Por favor", audio: "Por favor", emoji: "🙏", correct: true },
          { text: "Me llamo Milo", audio: "Me llamo Milo", emoji: "🐻", correct: false }
        ],
        explanation: "¡Perfecto! Siempre añadimos 'por favor' cuando pedimos algo."
      },
      {
        topic: "9. Despedidas",
        icon: "👋",
        question: "Ya es hora de volver a casa en el barco pirata. ¿Cómo te despides de tus amigos?",
        audioPrompt: "¡Adiós amigos! ¡Hasta pronto!",
        options: [
          { text: "¡Buenos días!", audio: "¡Buenos días!", emoji: "🌅", correct: false },
          { text: "¡Adiós! ¡Hasta pronto!", audio: "¡Adiós! ¡Hasta pronto!", emoji: "👋", correct: true },
          { text: "¿Cómo te llamas?", audio: "¿Cómo te llamas?", emoji: "🤔", correct: false }
        ],
        explanation: "¡Muy bien! '¡Adiós!' y '¡Hasta pronto!' sirven para despedirnos amigablemente."
      },
      {
        topic: "10. Gran Misión Final",
        icon: "👑",
        question: "Escucha el saludo completo del Capitán Milo. ¿Cuál frase significa 'I am 8 years old'?",
        audioPrompt: "¡Hola! Me llamo Milo, tengo ocho años y me gusta jugar.",
        options: [
          { text: "Me llamo Milo", audio: "Me llamo Milo", emoji: "🐻", correct: false },
          { text: "Me gusta jugar", audio: "Me gusta jugar", emoji: "🎮", correct: false },
          { text: "Tengo ocho años", audio: "Tengo ocho años", emoji: "8️⃣", correct: true }
        ],
        explanation: "¡TESORO DESBLOQUEADO! Dominas todas las expresiones de la Lección 1."
      }
    ];

    // ESTADO DEL JUEGO
    let currentQuestionIndex = 0;
    let lives = 3;
    let score = 0;
    let answeredCurrent = false;
    let isMuted = false;

    // SÍNTESIS DE VOZ (TTS EN ESPAÑOL) + EFECTOS DE SONIDO WEB AUDIO
    const audioCtx = new (window.AudioContext || window.webkitAudioContext)();

    function playTone(freq, type, duration, delay = 0) {
      if (isMuted) return;
      try {
        if (audioCtx.state === 'suspended') audioCtx.resume();
        const osc = audioCtx.createOscillator();
        const gain = audioCtx.createGain();
        osc.type = type;
        osc.frequency.setValueAtTime(freq, audioCtx.currentTime + delay);
        gain.gain.setValueAtTime(0.15, audioCtx.currentTime + delay);
        gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + delay + duration);
        osc.connect(gain);
        gain.connect(audioCtx.destination);
        osc.start(audioCtx.currentTime + delay);
        osc.stop(audioCtx.currentTime + delay + duration);
      } catch (e) {}
    }

    function playSuccessSound() {
      playTone(523.25, 'triangle', 0.15, 0);     // Do
      playTone(659.25, 'triangle', 0.15, 0.1);   // Mi
      playTone(783.99, 'triangle', 0.15, 0.2);   // Sol
      playTone(1046.50, 'triangle', 0.35, 0.3);  // Do alto
    }

    function playErrorSound() {
      playTone(300, 'sawtooth', 0.2, 0);
      playTone(220, 'sawtooth', 0.35, 0.18);
    }

    function speakSpanish(text, rate = 0.95) {
      if (isMuted) return;
      if ('speechSynthesis' in window) {
        window.speechSynthesis.cancel();
        const utterance = new SpeechSynthesisUtterance(text);
        utterance.lang = 'es-ES';
        utterance.rate = rate;
        utterance.pitch = 1.15; // Tono amigable para niños

        // Intentar buscar una voz en español natural
        const voices = window.speechSynthesis.getVoices();
        const esVoice = voices.find(v => v.lang.includes('es-MX') || v.lang.includes('es-US') || v.lang.includes('es-ES'));
        if (esVoice) utterance.voice = esVoice;

        // Animación visual del osito hablando
        const miloSpeech = document.getElementById('milo-speech');
        if (miloSpeech) {
          miloSpeech.innerHTML = `🗣️ <em>"${text}"</em>`;
        }
        window.speechSynthesis.speak(utterance);
      }
    }

    function toggleMute() {
      isMuted = !isMuted;
      const btn = document.getElementById('toggle-sound-btn');
      btn.textContent = isMuted ? '🔇' : '🔊';
      if (isMuted && 'speechSynthesis' in window) {
        window.speechSynthesis.cancel();
      }
    }

    // RENDERIZAR VIDAS EN LA PARTE SUPERIOR
    function renderLives(addedLife = false) {
      const container = document.getElementById('lives-container');
      container.innerHTML = '';
      for (let i = 0; i < lives; i++) {
        const span = document.createElement('span');
        span.textContent = '❤️';
        if (addedLife && i === lives - 1) {
          span.className = 'heart-anim inline-block';
        }
        container.appendChild(span);
      }
      if (lives === 0) {
        container.innerHTML = '<span class="text-sm text-rose-300 font-bold">0 vidas</span>';
      }

      if (addedLife) {
        const badge = document.getElementById('life-bonus-badge');
        badge.classList.remove('hidden');
        setTimeout(() => badge.classList.add('hidden'), 1800);
      }
    }

    // RENDERIZAR MAPA DE 10 ISLAS
    function renderMap() {
      const mapContainer = document.getElementById('map-nodes');
      mapContainer.innerHTML = '';

      questions.forEach((q, idx) => {
        const node = document.createElement('div');
        let bgClass = 'bg-amber-100 border-amber-400 text-amber-800';
        let content = idx + 1;

        if (idx < currentQuestionIndex) {
          bgClass = 'bg-emerald-500 border-emerald-700 text-white shadow-md';
          content = '⭐';
        } else if (idx === currentQuestionIndex) {
          bgClass = 'bg-amber-400 border-amber-700 text-amber-950 scale-125 ring-4 ring-amber-300 shadow-lg';
          content = '🐻';
        } else if (idx === questions.length - 1) {
          content = '🏆';
        }

        node.className = `w-9 h-9 sm:w-10 sm:h-10 rounded-full border-2 flex items-center justify-center font-fredoka font-bold text-sm transition-all duration-300 ${bgClass}`;
        node.textContent = content;
        mapContainer.appendChild(node);
      });

      document.getElementById('step-indicator').textContent = `Parada ${Math.min(currentQuestionIndex + 1, 10)} de 10`;
    }

    // INICIAR EL QUIZ
    function startQuiz() {
      currentQuestionIndex = 0;
      lives = 3;
      score = 0;
      document.getElementById('score-display').textContent = score;
      renderLives();
      renderMap();

      document.getElementById('start-screen').classList.add('hidden');
      document.getElementById('gameover-screen').classList.add('hidden');
      document.getElementById('victory-screen').classList.add('hidden');
      document.getElementById('quiz-screen').classList.remove('hidden');

      loadQuestion();
    }

    function restartQuiz() {
      startQuiz();
    }

    // CARGAR PREGUNTA ACTUAL
    function loadQuestion() {
      answeredCurrent = false;
      const q = questions[currentQuestionIndex];

      renderMap();
      document.getElementById('question-topic').textContent = `${q.icon} ${q.topic}`;
      document.getElementById('question-text').textContent = q.question;
      document.getElementById('feedback-box').classList.add('hidden');

      const optionsContainer = document.getElementById('options-container');
      optionsContainer.innerHTML = '';

      q.options.forEach((opt, index) => {
        const row = document.createElement('div');
        row.className = 'flex items-center gap-2';

        // Botón principal de opción
        const btn = document.createElement('button');
        btn.id = `opt-btn-${index}`;
        btn.className = 'option-card flex-1 p-4 rounded-2xl text-left flex items-center justify-between gap-3 cursor-pointer';
        btn.onclick = () => selectOption(index);

        btn.innerHTML = `
          <div class="flex items-center gap-3">
            <span class="text-2xl sm:text-3xl bg-amber-100 w-11 h-11 rounded-xl flex items-center justify-center border border-amber-300">${opt.emoji}</span>
            <span class="font-fredoka text-lg sm:text-xl font-bold text-amber-950">${opt.text}</span>
          </div>
          <span class="text-xs font-extrabold uppercase tracking-wider text-amber-600 bg-amber-50 px-2.5 py-1 rounded-lg border border-amber-200">Elegir</span>
        `;

        // Botón pequeño para escuchar cada opción en español
        const audioBtn = document.createElement('button');
        audioBtn.type = 'button';
        audioBtn.title = 'Escuchar esta opción en español';
        audioBtn.className = 'bg-sky-100 hover:bg-sky-200 text-sky-800 border-2 border-sky-300 p-3.5 rounded-2xl font-bold text-lg shadow-sm active:scale-95 transition cursor-pointer';
        audioBtn.innerHTML = '🔊';
        audioBtn.onclick = (e) => {
          e.stopPropagation();
          speakSpanish(opt.audio, 0.95);
        };

        row.appendChild(btn);
        row.appendChild(audioBtn);
        optionsContainer.appendChild(row);
      });

      // Reproducir automáticamente el audio de la pregunta tras un instante
      setTimeout(() => {
        playQuestionAudio(0.95);
      }, 350);
    }

    function playQuestionAudio(rate = 0.95) {
      const q = questions[currentQuestionIndex];
      speakSpanish(q.audioPrompt, rate);
    }

    // SELECCIONAR RESPUESTA
    function selectOption(selectedIndex) {
      if (answeredCurrent) return;
      answeredCurrent = true;

      const q = questions[currentQuestionIndex];
      const chosen = q.options[selectedIndex];
      const chosenBtn = document.getElementById(`opt-btn-${selectedIndex}`);

      // Deshabilitar todos los botones
      q.options.forEach((_, idx) => {
        document.getElementById(`opt-btn-${idx}`).disabled = true;
      });

      const feedbackBox = document.getElementById('feedback-box');
      const feedbackIcon = document.getElementById('feedback-icon');
      const feedbackTitle = document.getElementById('feedback-title');
      const feedbackDesc = document.getElementById('feedback-desc');
      const nextBtn = document.getElementById('next-btn');

      feedbackBox.classList.remove('hidden', 'bg-emerald-50', 'border-emerald-400', 'bg-rose-50', 'border-rose-400');

      if (chosen.correct) {
        // ACIERTO: +1 Punto y +1 Vida
        chosenBtn.classList.add('option-correct');
        score++;
        lives++;
        document.getElementById('score-display').textContent = score;
        renderLives(true);
        playSuccessSound();
        speakSpanish(chosen.audio, 1.0);

        feedbackBox.classList.add('bg-emerald-50', 'border-emerald-400');
        feedbackIcon.textContent = '💖';
        feedbackTitle.textContent = '¡¡Correcto! Ganaste +1 Vida extra!!';
        feedbackTitle.className = 'font-fredoka font-bold text-lg text-emerald-800';
        feedbackDesc.textContent = q.explanation;
        feedbackDesc.className = 'text-sm font-semibold text-emerald-700';
      } else {
        // ERROR: -1 Vida
        chosenBtn.classList.add('option-wrong');
        // Resaltar la correcta
        q.options.forEach((opt, idx) => {
          if (opt.correct) {
            document.getElementById(`opt-btn-${idx}`).classList.add('option-correct');
          }
        });

        lives = Math.max(0, lives - 1);
        renderLives(false);
        playErrorSound();

        feedbackBox.classList.add('bg-rose-50', 'border-rose-400');
        feedbackIcon.textContent = '💔';
        feedbackTitle.textContent = '¡Casi! Perdiste 1 vida';
        feedbackTitle.className = 'font-fredoka font-bold text-lg text-rose-800';
        feedbackDesc.textContent = q.explanation;
        feedbackDesc.className = 'text-sm font-semibold text-rose-700';
      }

      if (lives === 0) {
        nextBtn.textContent = 'Ver Resultado ⛵';
      } else if (currentQuestionIndex === questions.length - 1) {
        nextBtn.textContent = '¡Abrir el Tesoro! 🏆';
      } else {
        nextBtn.textContent = 'Siguiente Isla ➡️';
      }
    }

    // AVANZAR A LA SIGUIENTE PREGUNTA O FINALIZAR
    function nextQuestion() {
      if (lives <= 0) {
        document.getElementById('quiz-screen').classList.add('hidden');
        document.getElementById('gameover-screen').classList.remove('hidden');
        return;
      }

      currentQuestionIndex++;
      if (currentQuestionIndex < questions.length) {
        loadQuestion();
      } else {
        showVictory();
      }
    }

    // PANTALLA DE VICTORIA CON CONFETI
    function showVictory() {
      document.getElementById('quiz-screen').classList.add('hidden');
      document.getElementById('victory-screen').classList.remove('hidden');
      document.getElementById('final-score').textContent = `${score} / ${questions.length}`;
      document.getElementById('final-lives').textContent = `❤️ ${lives}`;

      playSuccessSound();
      speakSpanish("¡Felicidades explorador! Encontraste el tesoro de la amistad.", 0.95);
      launchConfetti();
    }

    function launchConfetti() {
      const colors = ['#f59e0b', '#ef4444', '#10b981', '#3b82f6', '#ec4899'];
      for (let i = 0; i < 65; i++) {
        const conf = document.createElement('div');
        conf.className = 'confetti rounded-sm';
        conf.style.left = Math.random() * 100 + 'vw';
        conf.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
        conf.style.animationDuration = (Math.random() * 2 + 2) + 's';
        conf.style.animationDelay = (Math.random() * 0.5) + 's';
        document.body.appendChild(conf);
        setTimeout(() => conf.remove(), 4500);
      }
    }

    // Inicializar vista de vidas y mapa al cargar
    renderLives();
    renderMap();
    if ('speechSynthesis' in window) {
      window.speechSynthesis.getVoices();
    }
  </script>
</body>
</html>
```
n las frases d la Lección 1 (*saludos, presentarse, edad, emociones, gustos y palabras mágicas*).

¿Te gustaría que agregue algún otro tema de la lección o que lo conectemos con el resto de las pantallas de la web?
