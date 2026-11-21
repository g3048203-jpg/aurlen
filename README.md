<!DOCTYPE html>
<html lang="ru" data-theme="graphite" data-font="onest-plex">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover" />
  <meta name="theme-color" content="#0d0e10" />
  <title>AURLEN COMMUNITY</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cormorant:ital,wght@0,500;0,600;0,700;1,500&family=IBM+Plex+Sans:wght@300;400;500;600&family=Inter:wght@300;400;500;600&family=Nunito+Sans:opsz,wght@6..12,400;6..12,600;6..12,700&family=Onest:wght@400;500;600;700&display=swap" rel="stylesheet" />
  <style>
    /* ==========================================================================
       1. ЦВЕТОВЫЕ ПАЛИТРЫ СО СЛАЙДОВ
       ========================================================================== */
    :root {
      --font-heading: 'Onest', sans-serif;
      --font-body: 'IBM Plex Sans', sans-serif;
      --ease-out-expo: cubic-bezier(0.16, 1, 0.3, 1);
      --transition-theme: background-color 0.35s ease, color 0.35s ease, border-color 0.35s ease;
    }

    /* Тема 1: Графит (Слайд 12/18) */
    [data-theme="graphite"] {
      --bg-primary: #0d0e10;
      --bg-secondary: #15171a;
      --bg-card: rgba(255, 255, 255, 0.03);
      --bg-card-hover: rgba(255, 255, 255, 0.06);
      --text-primary: #f2f1ed;
      --text-secondary: #9d9c98;
      --text-muted: #666562;
      --accent: #d8d4ca;
      --accent-contrast: #0d0e10;
      --border: rgba(216, 212, 202, 0.14);
      --border-strong: rgba(216, 212, 202, 0.32);
      --glow: rgba(216, 212, 202, 0.08);
    }

    /* Тема 2: Обсидиан (Слайд 03/06) */
    [data-theme="obsidian"] {
      --bg-primary: #09080c;
      --bg-secondary: #121018;
      --bg-card: rgba(214, 210, 224, 0.03);
      --bg-card-hover: rgba(214, 210, 224, 0.07);
      --text-primary: #f5f4f8;
      --text-secondary: #a5a1b0;
      --text-muted: #696475;
      --accent: #e0dce8;
      --accent-contrast: #09080c;
      --border: rgba(224, 220, 232, 0.14);
      --border-strong: rgba(224, 220, 232, 0.34);
      --glow: rgba(188, 178, 214, 0.1);
    }

    /* Тема 3: Шалфей (Слайд 11/18) */
    [data-theme="sage"] {
      --bg-primary: #0c100e;
      --bg-secondary: #131916;
      --bg-card: rgba(163, 184, 172, 0.035);
      --bg-card-hover: rgba(163, 184, 172, 0.075);
      --text-primary: #eef2ef;
      --text-secondary: #98a89f;
      --text-muted: #5f6e66;
      --accent: #a6b9ae;
      --accent-contrast: #0c100e;
      --border: rgba(166, 185, 174, 0.15);
      --border-strong: rgba(166, 185, 174, 0.35);
      --glow: rgba(166, 185, 174, 0.09);
    }

    /* ==========================================================================
       2. ШРИФТОВЫЕ ПАРЫ
       ========================================================================== */
    [data-font="onest-plex"] {
      --font-heading: 'Onest', sans-serif;
      --font-body: 'IBM Plex Sans', sans-serif;
      --heading-weight: 700;
      --heading-tracking: -0.02em;
    }

    [data-font="cormorant-inter"] {
      --font-heading: 'Cormorant', serif;
      --font-body: 'Inter', sans-serif;
      --heading-weight: 600;
      --heading-tracking: 0.01em;
    }

    [data-font="nunito-inter"] {
      --font-heading: 'Nunito Sans', sans-serif;
      --font-body: 'Inter', sans-serif;
      --heading-weight: 700;
      --heading-tracking: -0.015em;
    }

    /* ==========================================================================
       3. БАЗОВЫЕ СТИЛИ И АДАПТИВНОСТЬ
       ========================================================================== */
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      scroll-behavior: smooth;
      -webkit-text-size-adjust: 100%;
    }

    body {
      background-color: var(--bg-primary);
      color: var(--text-primary);
      font-family: var(--font-body);
      font-size: 16px;
      line-height: 1.6;
      overflow-x: hidden;
      transition: var(--transition-theme);
      -webkit-font-smoothing: antialiased;
    }

    /* Тонкий фоновый градиент без нагрузки на GPU */
    .ambient-bg {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 0;
      background:
        radial-gradient(circle at 50% 0%, var(--glow) 0%, transparent 55%),
        radial-gradient(circle at 85% 45%, var(--glow) 0%, transparent 45%);
      transition: background 0.5s ease;
    }

    .container {
      position: relative;
      z-index: 1;
      width: 100%;
      max-width: 1140px;
      margin: 0 auto;
      padding: 0 24px;
    }

    h1, h2, h3, .font-heading {
      font-family: var(--font-heading);
      font-weight: var(--heading-weight);
      letter-spacing: var(--heading-tracking);
      line-height: 1.15;
    }

    /* ==========================================================================
       4. ПАНЕЛЬ ВЫБОРА ЦВЕТА И ШРИФТА (ДЛЯ ТЕСТИРОВАНИЯ)
       ========================================================================== */
    .customizer-bar {
      position: sticky;
      top: 12px;
      z-index: 100;
      max-width: 1140px;
      margin: 12px auto 0;
      padding: 0 16px;
    }

    .customizer-inner {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 10px 16px;
      padding: 10px 16px;
      background: rgba(15, 16, 19, 0.82);
      backdrop-filter: blur(14px);
      -webkit-backdrop-filter: blur(14px);
      border: 1px solid var(--border-strong);
      border-radius: 14px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.45);
    }

    .customizer-group {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 6px;
    }

    .customizer-label {
      font-size: 12px;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: var(--text-secondary);
      margin-right: 4px;
      font-weight: 500;
    }

    .chip-btn {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 6px 12px;
      border-radius: 8px;
      border: 1px solid var(--border);
      background: transparent;
      color: var(--text-secondary);
      font-family: var(--font-body);
      font-size: 13px;
      cursor: pointer;
      transition: all 0.25s ease;
      white-space: nowrap;
    }

    .chip-btn:hover {
      color: var(--text-primary);
      border-color: var(--border-strong);
    }

    .chip-btn.active {
      background: var(--accent);
      color: var(--accent-contrast);
      border-color: var(--accent);
      font-weight: 500;
    }

    .swatch {
      width: 10px;
      height: 10px;
      border-radius: 50%;
      border: 1px solid rgba(255,255,255,0.25);
      flex-shrink: 0;
    }

    /* ==========================================================================
       5. АНИМАЦИИ ПОЯВЛЕНИЯ И HOVER-ЭФФЕКТЫ
       ========================================================================== */
    @keyframes heroFadeUp {
      from {
        opacity: 0;
        transform: translateY(22px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes subtleFloat {
      0%, 100% {
        transform: translateY(0px);
      }
      50% {
        transform: translateY(-6px);
      }
    }

    .hero-animate {
      opacity: 0;
      animation: heroFadeUp 0.85s var(--ease-out-expo) forwards;
    }

    .delay-1 { animation-delay: 0.1s; }
    .delay-2 { animation-delay: 0.22s; }
    .delay-3 { animation-delay: 0.34s; }

    /* Плавное появление секций при скролле */
    .reveal {
      opacity: 0;
      transform: translateY(26px);
      transition: opacity 0.75s var(--ease-out-expo), transform 0.75s var(--ease-out-expo);
      will-change: opacity, transform;
    }

    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    @media (prefers-reduced-motion: reduce) {
      .hero-animate, .reveal {
        opacity: 1 !important;
        transform: none !important;
        animation: none !important;
        transition: none !important;
      }
    }

    /* ==========================================================================
       6. ПЕРВЫЙ ЭКРАН (HERO) — ЦЕНТРИРОВАННЫЙ
       ========================================================================== */
    .hero {
      padding: 84px 0 72px;
      text-align: center;
      border-bottom: 1px solid var(--border);
    }

    .hero-badge {
      display: inline-block;
      padding: 6px 14px;
      border-radius: 999px;
      border: 1px solid var(--border-strong);
      background: var(--bg-card);
      color: var(--accent);
      font-size: 12px;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      margin-bottom: 24px;
    }

    .hero-title {
      font-size: clamp(2.5rem, 6.5vw, 4.75rem);
      text-transform: uppercase;
      letter-spacing: 0.04em;
      margin-bottom: 22px;
      color: var(--text-primary);
    }

    .hero-title span {
      display: block;
      font-size: clamp(1.1rem, 2.5vw, 1.65rem);
      letter-spacing: 0.28em;
      color: var(--accent);
      margin-top: 8px;
      font-weight: 500;
    }

    .hero-subtitle {
      max-width: 680px;
      margin: 0 auto;
      font-size: clamp(1rem, 1.8vw, 1.15rem);
      color: var(--text-secondary);
      line-height: 1.7;
    }

    /* ==========================================================================
       7. БЛОК О СООБЩЕСТВЕ / ТГК (СЛЕВА ТЕКСТ, СПРАВА ФОТО БЕЗ ОБРЕЗКИ)
       ========================================================================== */
    .section {
      padding: 76px 0;
      border-bottom: 1px solid var(--border);
    }

    .tgk-grid {
      display: grid;
      grid-template-columns: 1.15fr 0.85fr;
      gap: 48px;
      align-items: center;
    }

    .section-kicker {
      font-size: 12px;
      text-transform: uppercase;
      letter-spacing: 0.14em;
      color: var(--accent);
      margin-bottom: 12px;
      display: block;
    }

    .section-title {
      font-size: clamp(1.75rem, 3.6vw, 2.6rem);
      margin-bottom: 18px;
    }

    .tgk-text {
      color: var(--text-secondary);
      margin-bottom: 16px;
      font-size: 1.02rem;
    }

    .tgk-link-card {
      margin-top: 24px;
      padding: 18px 20px;
      border-radius: 14px;
      background: var(--bg-card);
      border: 1px solid var(--border-strong);
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .tgk-link-desc {
      font-size: 0.95rem;
      color: var(--text-primary);
    }

    .btn-primary {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      align-self: flex-start;
      padding: 12px 22px;
      border-radius: 10px;
      background: var(--accent);
      color: var(--accent-contrast);
      text-decoration: none;
      font-weight: 600;
      font-size: 0.95rem;
      transition: transform 0.25s ease, box-shadow 0.25s ease, opacity 0.25s ease;
    }

    .btn-primary:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 24px rgba(0, 0, 0, 0.35);
      opacity: 0.94;
    }

    /* Аккуратный контейнер для квадратного изображения 1:1 */
    .tgk-media {
      width: 100%;
      max-width: 420px;
      margin: 0 auto;
    }

    .tgk-image-frame {
      position: relative;
      width: 100%;
      aspect-ratio: 1 / 1;
      border-radius: 20px;
      overflow: hidden;
      background: #000000;
      border: 1px solid var(--border-strong);
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.55);
      animation: subtleFloat 7s ease-in-out infinite;
    }

    .tgk-image-frame img {
      display: block;
      width: 100%;
      height: 100%;
      object-fit: contain;
      object-position: center;
    }

    /* ==========================================================================
       8. НАШИ ПРОДУКТЫ (БЕЗ ЦЕН + СЛОТЫ ДЛЯ РАСШИРЕНИЯ)
       ========================================================================== */
    .section-header {
      margin-bottom: 40px;
    }

    .products-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
    }

    .card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 18px;
      padding: 28px;
      transition: transform 0.3s var(--ease-out-expo), border-color 0.3s ease, background-color 0.3s ease;
    }

    .card:hover {
      transform: translateY(-4px);
      border-color: var(--border-strong);
      background: var(--bg-card-hover);
    }

    .card-title {
      font-size: 1.35rem;
      margin-bottom: 18px;
      color: var(--text-primary);
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
    }

    .card-tag {
      font-family: var(--font-body);
      font-size: 11px;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      padding: 4px 10px;
      border-radius: 6px;
      border: 1px solid var(--border-strong);
      color: var(--accent);
      font-weight: 500;
    }

    .service-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .service-list li {
      position: relative;
      padding-left: 18px;
      color: var(--text-secondary);
      font-size: 0.98rem;
    }

    .service-list li::before {
      content: "";
      position: absolute;
      left: 0;
      top: 0.62em;
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: var(--accent);
    }

    .service-list strong {
      color: var(--text-primary);
      font-weight: 500;
    }

    .card-slot {
      border-style: dashed;
      border-color: var(--border-strong);
      display: flex;
      flex-direction: column;
      justify-content: center;
      min-height: 180px;
    }

    .slot-hint {
      color: var(--text-muted);
      font-size: 0.92rem;
    }

    /* ==========================================================================
       9. КЕЙСЫ И ПОРТФОЛИО (БЕЗ ССЫЛКИ НА ТГК ВНИЗУ)
       ========================================================================== */
    .cases-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 18px;
      margin-bottom: 36px;
    }

    .case-placeholder {
      padding: 24px;
      border-radius: 16px;
      border: 1px dashed var(--border-strong);
      background: var(--bg-card);
      min-height: 150px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .case-num {
      font-size: 12px;
      letter-spacing: 0.12em;
      color: var(--accent);
      text-transform: uppercase;
    }

    .case-label {
      color: var(--text-muted);
      font-size: 0.95rem;
    }

    .portfolio-box {
      padding: 32px;
      border-radius: 20px;
      background: var(--bg-secondary);
      border: 1px solid var(--border-strong);
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
    }

    .portfolio-info h3 {
      font-size: 1.6rem;
      margin-bottom: 6px;
    }

    .portfolio-info p {
      color: var(--text-secondary);
      font-size: 0.96rem;
    }

    .btn-outline {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 12px 22px;
      border-radius: 10px;
      border: 1px solid var(--border-strong);
      color: var(--text-primary);
      text-decoration: none;
      font-size: 0.95rem;
      font-weight: 500;
      transition: background-color 0.25s ease, color 0.25s ease;
    }

    .btn-outline:hover {
      background: var(--accent);
      color: var(--accent-contrast);
      border-color: var(--accent);
    }

    /* ==========================================================================
       10. ПОДВАЛ (ТОЛЬКО БРЕНД И ГОД, БЕЗ ТГК ССЫЛКИ)
       ========================================================================== */
    .footer {
      padding: 32px 0 44px;
      text-align: center;
      color: var(--text-muted);
      font-size: 0.88rem;
    }

    /* ==========================================================================
       11. АДАПТАЦИЯ ПОД ТЕЛЕФОНЫ И ПЛАНШЕТЫ
       ========================================================================== */
    @media (max-width: 900px) {
      .tgk-grid {
        grid-template-columns: 1fr;
        gap: 32px;
      }

      .tgk-media {
        max-width: 340px;
      }

      .cases-grid {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 640px) {
      .container {
        padding: 0 18px;
      }

      .customizer-bar {
        top: 8px;
        padding: 0 10px;
      }

      .customizer-inner {
        padding: 10px 12px;
        gap: 8px;
      }

      .chip-btn {
        padding: 5px 9px;
        font-size: 12px;
      }

      .hero {
        padding: 56px 0 52px;
      }

      .section {
        padding: 54px 0;
      }

      .products-grid {
        grid-template-columns: 1fr;
        gap: 16px;
      }

      .card {
        padding: 22px 20px;
      }

      .btn-primary, .btn-outline {
        width: 100%;
        justify-content: center;
      }

      .portfolio-box {
        padding: 24px 20px;
      }
    }
  </style>
</head>
<body>
  <div class="ambient-bg" aria-hidden="true"></div>

  <!-- Панель переключения палитры и шрифта -->
  <div class="customizer-bar" role="region" aria-label="Настройка оформления">
    <div class="customizer-inner">
      <div class="customizer-group">
        <span class="customizer-label">Цвет:</span>
        <button type="button" class="chip-btn active" data-set-theme="graphite">
          <span class="swatch" style="background:#d8d4ca;"></span>1. Графит
        </button>
        <button type="button" class="chip-btn" data-set-theme="obsidian">
          <span class="swatch" style="background:#e0dce8;"></span>2. Обсидиан
        </button>
        <button type="button" class="chip-btn" data-set-theme="sage">
          <span class="swatch" style="background:#a6b9ae;"></span>3. Шалфей
        </button>
      </div>

      <div class="customizer-group">
        <span class="customizer-label">Шрифт:</span>
        <button type="button" class="chip-btn active" data-set-font="onest-plex">Onest + IBM Plex</button>
        <button type="button" class="chip-btn" data-set-font="cormorant-inter">Cormorant + Inter</button>
        <button type="button" class="chip-btn" data-set-font="nunito-inter">Nunito + Inter</button>
      </div>
    </div>
  </div>

  <main>
    <!-- ПЕРВЫЙ ЭКРАН -->
    <section class="hero">
      <div class="container">
        <span class="hero-badge hero-animate">Digital &amp; Visual Studio</span>
        <h1 class="hero-title hero-animate delay-1">
          AURLEN
          <span>COMMUNITY</span>
        </h1>
        <p class="hero-subtitle hero-animate delay-2">
          Создаём цельную цифровую упаковку для экспертов, брендов и локальных заведений: разрабатываем современные сайты, функциональных Telegram-ботов и выразительное визуальное оформление каналов под ключ.
        </p>
      </div>
    </section>

    <!-- БЛОК ТГК + ФОТО СПРАВА -->
    <section class="section" id="community">
      <div class="container">
        <div class="tgk-grid">
          <div class="reveal">
            <span class="section-kicker">Экосистема и комьюнити</span>
            <h2 class="section-title">AURLEN PRIVATE</h2>
            <p class="tgk-text">
              В нашем закрытом Telegram-канале мы делимся рабочими процессами, показываем свежие релизы дизайна, разбираем архитектуру ботов и публикуем актуальные условия для запуска проектов.
            </p>
            <p class="tgk-text">
              Присоединяйтесь к сообществу, чтобы следить за обновлениями студии и напрямую обсудить задачу под ваш проект.
            </p>

            <div class="tgk-link-card">
              <span class="tgk-link-desc">Вход в официальный Telegram-канал сообщества:</span>
              <a href="https://t.me/+ccVZIC5RgEI5MDdi" target="_blank" rel="noopener noreferrer" class="btn-primary">
                Перейти в Telegram-канал
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
                  <path d="M7 17L17 7"></path>
                  <path d="M7 7h10v10"></path>
                </svg>
              </a>
            </div>
          </div>

          <div class="tgk-media reveal">
            <div class="tgk-image-frame">
              <img src="image_e5dc27.jpg" alt="AURLEN PRIVATE" loading="eager" />
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- НАШИ ПРОДУКТЫ (БЕЗ ЦЕН) -->
    <section class="section" id="products">
      <div class="container">
        <div class="section-header reveal">
          <span class="section-kicker">Направления работы</span>
          <h2 class="section-title">Наши Продукты</h2>
        </div>

        <div class="products-grid">
          <!-- Карточка 1 -->
          <article class="card reveal">
            <h3 class="card-title">
              Отдельные заказы
              <span class="card-tag">Single</span>
            </h3>
            <ul class="service-list">
              <li>Создание аватарки</li>
              <li>Создание обоев</li>
              <li>Создание превью</li>
              <li>Создание баннера</li>
              <li>Любая другая графическая и цифровая задача под ваш запрос</li>
            </ul>
          </article>

          <!-- Карточка 2 -->
          <article class="card reveal">
            <h3 class="card-title">
              Комплекты работ
              <span class="card-tag">Packs</span>
            </h3>
            <ul class="service-list">
              <li><strong>Полное оформление:</strong> аватарка, аватарка для адаптера, баннер, обои для ТГК</li>
              <li><strong>Оформление ТГК:</strong> аватарка канала и фирменные обои</li>
              <li><strong>Оформление профиля:</strong> аватарка, аватарка адаптера и баннер</li>
            </ul>
          </article>

          <!-- Карточка 3 -->
          <article class="card reveal">
            <h3 class="card-title">
              Сформируй свой комплект
              <span class="card-tag">Custom</span>
            </h3>
            <ul class="service-list">
              <li>Выбор двух задач в одном заказе — <strong>скидка 20%</strong></li>
              <li>Выбор трёх задач в одном заказе — <strong>скидка 30%</strong></li>
              <li>Четыре и более задачи — <strong>персональная скидка</strong></li>
            </ul>
          </article>

          <!-- Карточка 4 -->
          <article class="card reveal">
            <h3 class="card-title">
              Комплексный запуск
              <span class="card-tag">Synergy</span>
            </h3>
            <ul class="service-list">
              <li>При заказе дизайна ТГК параллельно с разработкой бота или сайта</li>
              <li>При подключении одного смежного эксперта — <strong>скидка 20%</strong></li>
              <li>При подключении двух экспертов — <strong>скидка 30%</strong></li>
              <li><strong>Все скидки суммируются</strong></li>
            </ul>
          </article>

          <!-- Пустой слот для будущих продуктов -->
          <article class="card card-slot reveal">
            <h3 class="card-title">
              Разработка сайтов и Telegram-ботов
              <span class="card-tag">Скоро</span>
            </h3>
            <p class="slot-hint">Место зарезервировано под подробное описание web-разработки и автоматизации.</p>
          </article>

          <article class="card card-slot reveal">
            <h3 class="card-title">
              Дополнительный продукт
              <span class="card-tag">Слот</span>
            </h3>
            <p class="slot-hint">Свободный блок для добавления новых услуг и форматов работы.</p>
          </article>
        </div>
      </div>
    </section>

    <!-- КЕЙСЫ И ПОРТФОЛИО -->
    <section class="section" id="portfolio">
      <div class="container">
        <div class="section-header reveal">
          <span class="section-kicker">Практика и результаты</span>
          <h2 class="section-title">Кейсы и Портфолио</h2>
        </div>

        <div class="cases-grid">
          <div class="case-placeholder reveal">
            <span class="case-num">Кейс 01</span>
            <p class="case-label">Место под разбор проекта: упаковка Telegram-канала</p>
          </div>
          <div class="case-placeholder reveal">
            <span class="case-num">Кейс 02</span>
            <p class="case-label">Место под разбор проекта: разработка сайта</p>
          </div>
          <div class="case-placeholder reveal">
            <span class="case-num">Кейс 03</span>
            <p class="case-label">Место под разбор проекта: внедрение Telegram-бота</p>
          </div>
        </div>

        <div class="portfolio-box reveal">
          <div class="portfolio-info">
            <h3>Портфолио</h3>
            <p>Подборка выполненных работ по оформлению каналов, ботам и сайтам.</p>
          </div>
          <a href="#portfolio-link" class="btn-outline" onclick="event.preventDefault();">
            Ссылка на портфолио (добавим позже)
          </a>
        </div>
      </div>
    </section>
  </main>

  <footer class="footer">
    <div class="container">
      AURLEN COMMUNITY &copy; 2026
    </div>
  </footer>

  <script>
    (function () {
      const root = document.documentElement;
      const themeButtons = document.querySelectorAll('[data-set-theme]');
      const fontButtons = document.querySelectorAll('[data-set-font]');

      themeButtons.forEach((btn) => {
        btn.addEventListener('click', () => {
          const theme = btn.getAttribute('data-set-theme');
          root.setAttribute('data-theme', theme);
          themeButtons.forEach((b) => b.classList.remove('active'));
          btn.classList.add('active');
        });
      });

      fontButtons.forEach((btn) => {
        btn.addEventListener('click', () => {
          const font = btn.getAttribute('data-set-font');
          root.setAttribute('data-font', font);
          fontButtons.forEach((b) => b.classList.remove('active'));
          btn.classList.add('active');
        });
      });

      // Лёгкий IntersectionObserver для плавного появления секций без нагрузки на CPU
      const revealEls = document.querySelectorAll('.reveal');
      if ('IntersectionObserver' in window) {
        const observer = new IntersectionObserver(
          (entries, obs) => {
            entries.forEach((entry) => {
              if (entry.isIntersecting) {
                entry.target.classList.add('visible');
                obs.unobserve(entry.target);
              }
            });
          },
          { threshold: 0.12, rootMargin: '0px 0px -30px 0px' }
        );
        revealEls.forEach((el) => observer.observe(el));
      } else {
        revealEls.forEach((el) => el.classList.add('visible'));
      }
    })();
  </script>
</body>
</html>
