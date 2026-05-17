# SpeakUp
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>SpeakUp — Горячая линия комплаенса университета</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body {
    font-family: -apple-system, 'Segoe UI', Roboto, sans-serif;
    background: #f5f7fa;
    color: #1a2332;
    line-height: 1.6;
  }
  
  /* Навигация */
  nav {
    background: #fff;
    border-bottom: 1px solid #e5e9f0;
    padding: 16px 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .logo {
    display: flex;
    align-items: center;
    gap: 10px;
    font-weight: 700;
    font-size: 20px;
    color: #2c3e7b;
  }
  .logo-icon {
    width: 36px; height: 36px;
    background: linear-gradient(135deg, #2c3e7b, #4a6fc4);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    color: white; font-size: 18px;
  }
  .nav-tabs { display: flex; gap: 8px; }
  .nav-tab {
    padding: 8px 18px;
    border-radius: 8px;
    cursor: pointer;
    font-weight: 500;
    color: #5a6a85;
    transition: all 0.2s;
    border: none;
    background: transparent;
    font-size: 14px;
  }
  .nav-tab:hover { background: #f0f4fa; }
  .nav-tab.active { background: #2c3e7b; color: white; }

  /* Экраны */
  .screen { display: none; padding: 40px; max-width: 1280px; margin: 0 auto; }
  .screen.active { display: block; }

  /* HERO */
  .hero {
    background: linear-gradient(135deg, #2c3e7b 0%, #4a6fc4 100%);
    color: white;
    padding: 60px 50px;
    border-radius: 16px;
    margin-bottom: 32px;
    position: relative;
    overflow: hidden;
  }
  .hero::after {
    content: '🛡️';
    position: absolute;
    right: -20px; top: -20px;
    font-size: 280px;
    opacity: 0.08;
  }
  .hero h1 { font-size: 42px; margin-bottom: 16px; max-width: 700px; line-height: 1.2; }
  .hero p { font-size: 18px; opacity: 0.92; max-width: 600px; margin-bottom: 32px; }
  .hero-badges { display: flex; gap: 12px; flex-wrap: wrap; margin-bottom: 32px; }
  .badge {
    background: rgba(255,255,255,0.15);
    padding: 8px 16px;
    border-radius: 20px;
    font-size: 14px;
    backdrop-filter: blur(10px);
  }
  .hero-buttons { display: flex; gap: 12px; flex-wrap: wrap; }
  .btn {
    padding: 14px 28px;
    border-radius: 10px;
    border: none;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 8px;
  }
  .btn-primary { background: #ff6b6b; color: white; }
  .btn-primary:hover { background: #ff5252; transform: translateY(-1px); }
  .btn-secondary { background: rgba(255,255,255,0.2); color: white; border: 1px solid rgba(255,255,255,0.3); }
  .btn-secondary:hover { background: rgba(255,255,255,0.3); }
  .btn-outline { background: white; color: #2c3e7b; border: 2px solid #2c3e7b; }
  .btn-outline:hover { background: #f0f4fa; }

  /* Карточки преимуществ */
  .features-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
    margin-bottom: 40px;
  }
  .feature-card {
    background: white;
    padding: 28px 24px;
    border-radius: 12px;
    border: 1px solid #e5e9f0;
  }
  .feature-icon {
    width: 48px; height: 48px;
    background: #eef2fb;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 24px;
    margin-bottom: 16px;
  }
  .feature-card h3 { font-size: 16px; margin-bottom: 8px; color: #1a2332; }
  .feature-card p { font-size: 14px; color: #5a6a85; }

  /* Категории */
  .section-title {
    font-size: 24px;
    margin-bottom: 8px;
    color: #1a2332;
  }
  .section-subtitle {
    color: #5a6a85;
    margin-bottom: 24px;
  }
  .categories-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    margin-bottom: 40px;
  }
  .category-card {
    background: white;
    padding: 24px;
    border-radius: 12px;
    border: 1px solid #e5e9f0;
    cursor: pointer;
    transition: all 0.2s;
    display: flex;
    gap: 16px;
    align-items: flex-start;
  }
  .category-card:hover {
    border-color: #4a6fc4;
    box-shadow: 0 4px 16px rgba(44, 62, 123, 0.1);
    transform: translateY(-2px);
  }
  .cat-icon {
    width: 44px; height: 44px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 22px;
    flex-shrink: 0;
  }
  .cat-icon.red { background: #ffe5e5; }
  .cat-icon.orange { background: #fff0e0; }
  .cat-icon.blue { background: #e5edff; }
  .cat-icon.purple { background: #f0e5ff; }
  .cat-icon.green { background: #e0f5e9; }
  .cat-icon.yellow { background: #fff8e0; }
  .category-card h4 { font-size: 15px; margin-bottom: 4px; }
  .category-card p { font-size: 13px; color: #5a6a85; }

  /* Как это работает */
  .steps {
    background: white;
    padding: 40px;
    border-radius: 16px;
    border: 1px solid #e5e9f0;
    margin-bottom: 40px;
  }
  .steps-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 24px;
    margin-top: 24px;
  }
  .step {
    position: relative;
    padding-left: 0;
  }
  .step-number {
    width: 40px; height: 40px;
    background: linear-gradient(135deg, #2c3e7b, #4a6fc4);
    color: white;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-weight: 700;
    margin-bottom: 12px;
  }
  .step h4 { font-size: 16px; margin-bottom: 6px; }
  .step p { font-size: 14px; color: #5a6a85; }

  /* Форма */
  .form-container {
    background: white;
    padding: 40px;
    border-radius: 16px;
    border: 1px solid #e5e9f0;
    max-width: 900px;
    margin: 0 auto;
  }
  .form-header { margin-bottom: 32px; }
  .form-header h2 { font-size: 28px; margin-bottom: 8px; }
  .form-header p { color: #5a6a85; }

  .progress-bar {
    display: flex;
    justify-content: space-between;
    margin-bottom: 32px;
    position: relative;
  }
  .progress-bar::before {
    content: '';
    position: absolute;
    top: 18px;
    left: 5%; right: 5%;
    height: 2px;
    background: #e5e9f0;
    z-index: 0;
  }
  .progress-step {
    position: relative;
    z-index: 1;
    text-align: center;
    flex: 1;
  }
  .progress-circle {
    width: 36px; height: 36px;
    background: #e5e9f0;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    margin: 0 auto 6px;
    font-weight: 600;
    color: #5a6a85;
    border: 3px solid #f5f7fa;
  }
  .progress-step.active .progress-circle { background: #2c3e7b; color: white; }
  .progress-step.done .progress-circle { background: #4caf50; color: white; }
  .progress-step span { font-size: 12px; color: #5a6a85; }
  .progress-step.active span { color: #2c3e7b; font-weight: 600; }

  .form-group { margin-bottom: 20px; }
  .form-group label {
    display: block;
    font-weight: 500;
    margin-bottom: 8px;
    font-size: 14px;
    color: #1a2332;
  }
  .form-group input, .form-group select, .form-group textarea {
    width: 100%;
    padding: 12px 14px;
    border: 1px solid #d5dce6;
    border-radius: 8px;
    font-size: 15px;
    font-family: inherit;
    transition: border-color 0.2s;
  }
  .form-group input:focus, .form-group textarea:focus, .form-group select:focus {
    outline: none;
    border-color: #4a6fc4;
  }
  .form-group textarea { resize: vertical; min-height: 140px; }
  .helper { font-size: 12px; color: #5a6a85; margin-top: 6px; }

  /* AI помощник */
  .ai-helper {
    background: linear-gradient(135deg, #f0f4fa, #e8eef9);
    border-left: 4px solid #4a6fc4;
    padding: 16px 20px;
    border-radius: 8px;
    margin-bottom: 20px;
  }
  .ai-helper-header {
    display: flex;
    align-items: center;
    gap: 8px;
    font-weight: 600;
    color: #2c3e7b;
    margin-bottom: 8px;
    font-size: 14px;
  }
  .ai-icon {
    width: 24px; height: 24px;
    background: linear-gradient(135deg, #4a6fc4, #8a5dd6);
    border-radius: 6px;
    display: flex; align-items: center; justify-content: center;
    color: white;
    font-size: 12px;
  }
  .ai-helper p { font-size: 13px; color: #3a4a6a; margin-bottom: 8px; }
  .ai-suggestions { display: flex; gap: 8px; flex-wrap: wrap; }
  .ai-suggestion {
    background: white;
    padding: 6px 12px;
    border-radius: 16px;
    font-size: 12px;
    cursor: pointer;
    border: 1px solid #d5dce6;
    color: #2c3e7b;
  }
  .ai-suggestion:hover { background: #4a6fc4; color: white; border-color: #4a6fc4; }

  /* Файлы */
  .file-upload {
    border: 2px dashed #d5dce6;
    border-radius: 10px;
    padding: 32px;
    text-align: center;
    cursor: pointer;
    transition: all 0.2s;
  }
  .file-upload:hover { border-color: #4a6fc4; background: #f8faff; }
  .file-upload-icon { font-size: 32px; margin-bottom: 8px; }

  .form-actions {
    display: flex;
    justify-content: space-between;
    margin-top: 32px;
    padding-top: 24px;
    border-top: 1px solid #e5e9f0;
  }

  /* Код обращения - модалка */
  .success-screen {
    text-align: center;
    padding: 40px;
  }
  .success-icon {
    width: 80px; height: 80px;
    background: linear-gradient(135deg, #4caf50, #66bb6a);
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 40px;
    color: white;
    margin: 0 auto 24px;
  }
  .ticket-code {
    background: linear-gradient(135deg, #f0f4fa, #e8eef9);
    padding: 24px;
    border-radius: 12px;
    margin: 24px 0;
    font-family: 'Courier New', monospace;
    font-size: 28px;
    font-weight: 700;
    color: #2c3e7b;
    letter-spacing: 2px;
    border: 2px dashed #4a6fc4;
  }

  /* Дашборд */
  .dashboard-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 24px;
  }
  .dashboard-header h2 { font-size: 28px; }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
    margin-bottom: 32px;
  }
  .stat-card {
    background: white;
    padding: 24px;
    border-radius: 12px;
    border: 1px solid #e5e9f0;
  }
  .stat-label {
    font-size: 13px;
    color: #5a6a85;
    margin-bottom: 8px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  .stat-value {
    font-size: 32px;
    font-weight: 700;
    color: #1a2332;
    margin-bottom: 4px;
  }
  .stat-trend { font-size: 13px; }
  .trend-up { color: #4caf50; }
  .trend-down { color: #ff6b6b; }

  .dashboard-grid {
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: 24px;
  }

  .panel {
    background: white;
    border-radius: 12px;
    border: 1px solid #e5e9f0;
    overflow: hidden;
  }
  .panel-header {
    padding: 20px 24px;
    border-bottom: 1px solid #e5e9f0;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .panel-header h3 { font-size: 17px; }
  .filters { display: flex; gap: 8px; }
  .filter-chip {
    padding: 6px 14px;
    border-radius: 16px;
    background: #f0f4fa;
    font-size: 13px;
    cursor: pointer;
    color: #5a6a85;
    border: none;
  }
  .filter-chip.active { background: #2c3e7b; color: white; }

  /* Таблица обращений */
  .ticket-list { padding: 0; }
  .ticket-row {
    padding: 16px 24px;
    border-bottom: 1px solid #f0f4fa;
    display: grid;
    grid-template-columns: 100px 1fr 130px 110px 90px;
    gap: 16px;
    align-items: center;
    cursor: pointer;
    transition: background 0.15s;
  }
  .ticket-row:hover { background: #f8faff; }
  .ticket-row:last-child { border-bottom: none; }
  .ticket-id {
    font-family: 'Courier New', monospace;
    font-weight: 600;
    color: #2c3e7b;
    font-size: 13px;
  }
  .ticket-title {
    font-weight: 500;
    font-size: 14px;
    color: #1a2332;
    margin-bottom: 4px;
  }
  .ticket-meta { font-size: 12px; color: #5a6a85; }
  .tag {
    display: inline-block;
    padding: 4px 10px;
    border-radius: 12px;
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
  }
  .tag-red { background: #ffe5e5; color: #c62828; }
  .tag-orange { background: #fff0e0; color: #e65100; }
  .tag-blue { background: #e5edff; color: #1565c0; }
  .tag-green { background: #e0f5e9; color: #2e7d32; }
  .tag-purple { background: #f0e5ff; color: #6a1b9a; }
  .priority {
    width: 8px; height: 8px;
    border-radius: 50%;
    display: inline-block;
    margin-right: 6px;
  }
  .priority.high { background: #ff6b6b; }
  .priority.medium { background: #ffa726; }
  .priority.low { background: #66bb6a; }

  /* Категории на дашборде */
  .cat-stats { padding: 20px 24px; }
  .cat-row {
    margin-bottom: 16px;
  }
  .cat-row-top {
    display: flex;
    justify-content: space-between;
    margin-bottom: 6px;
    font-size: 14px;
  }
  .cat-bar {
    height: 8px;
    background: #f0f4fa;
    border-radius: 4px;
    overflow: hidden;
  }
  .cat-bar-fill {
    height: 100%;
    background: linear-gradient(90deg, #4a6fc4, #8a5dd6);
    border-radius: 4px;
  }

  /* AI вставка в дашборде */
  .ai-insight {
    background: linear-gradient(135deg, #f0e5ff, #e5edff);
    padding: 16px;
    border-radius: 10px;
    margin-top: 16px;
  }
  .ai-insight-title {
    display: flex;
    align-items: center;
    gap: 8px;
    font-weight: 600;
    font-size: 13px;
    color: #6a1b9a;
    margin-bottom: 8px;
  }
  .ai-insight p { font-size: 13px; color: #3a4a6a; }

  /* Чат */
  .chat-screen {
    max-width: 800px;
    margin: 0 auto;
    background: white;
    border-radius: 16px;
    border: 1px solid #e5e9f0;
    overflow: hidden;
  }
  .chat-header {
    padding: 20px 24px;
    border-bottom: 1px solid #e5e9f0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: linear-gradient(135deg, #2c3e7b, #4a6fc4);
    color: white;
  }
  .chat-header h3 { font-size: 18px; }
  .chat-header .status {
    background: rgba(255,255,255,0.2);
    padding: 4px 12px;
    border-radius: 12px;
    font-size: 12px;
  }
  .chat-messages {
    padding: 24px;
    height: 400px;
    overflow-y: auto;
    background: #f8faff;
  }
  .msg {
    margin-bottom: 16px;
    max-width: 70%;
    padding: 12px 16px;
    border-radius: 12px;
    font-size: 14px;
  }
  .msg.them {
    background: white;
    border: 1px solid #e5e9f0;
  }
  .msg.you {
    background: #2c3e7b;
    color: white;
    margin-left: auto;
  }
  .msg-time {
    font-size: 11px;
    opacity: 0.7;
    margin-top: 4px;
  }
  .chat-input {
    display: flex;
    gap: 10px;
    padding: 16px 24px;
    border-top: 1px solid #e5e9f0;
  }
  .chat-input input {
    flex: 1;
    padding: 12px 16px;
    border: 1px solid #d5dce6;
    border-radius: 24px;
    outline: none;
  }
  .chat-input button {
    background: #2c3e7b;
    color: white;
    border: none;
    width: 44px; height: 44px;
    border-radius: 50%;
    cursor: pointer;
    font-size: 18px;
  }

  /* Футер */
  footer {
    text-align: center;
    padding: 30px;
    color: #5a6a85;
    font-size: 13px;
    border-top: 1px solid #e5e9f0;
    margin-top: 40px;
  }

  @media (max-width: 768px) {
    .features-grid, .categories-grid, .stats-grid, .steps-grid { grid-template-columns: 1fr 1fr; }
    .dashboard-grid { grid-template-columns: 1fr; }
    .hero h1 { font-size: 28px; }
    nav { padding: 12px 16px; flex-wrap: wrap; gap: 10px; }
    .screen { padding: 20px; }
  }
</style>
</head>
<body>

<nav>
  <div class="logo">
    <div class="logo-icon">🛡️</div>
    <div>SpeakUp <span style="font-weight:400; color:#5a6a85; font-size:13px;">| Университет</span></div>
  </div>
  <div class="nav-tabs">
    <button class="nav-tab active" onclick="showScreen('home', this)">Главная</button>
    <button class="nav-tab" onclick="showScreen('form', this)">Подать обращение</button>
    <button class="nav-tab" onclick="showScreen('track', this)">Отследить статус</button>
    <button class="nav-tab" onclick="showScreen('chat', this)">Чат</button>
    <button class="nav-tab" onclick="showScreen('dashboard', this)">Дашборд комплаенса</button>
  </div>
</nav>

<!-- ГЛАВНАЯ -->
<div class="screen active" id="home">
  <section class="hero">
    <h1>Безопасный канал сообщения о нарушениях</h1>
    <p>Анонимная горячая линия для студентов, преподавателей и сотрудников университета. Сообщите о коррупции, давлении или нарушениях этики — мы гарантируем вашу защиту.</p>
    <div class="hero-badges">
      <div class="badge">🔒 Полная анонимность</div>
      <div class="badge">⚡ Ответ до 5 рабочих дней</div>
      <div class="badge">🤖 ИИ-помощник</div>
      <div class="badge">📋 Соответствие 152-ФЗ</div>
    </div>
    <div class="hero-buttons">
      <button class="btn btn-primary" onclick="showScreen('form', document.querySelectorAll('.nav-tab')[1])">
        ✍️ Подать обращение
      </button>
      <button class="btn btn-secondary" onclick="showScreen('track', document.querySelectorAll('.nav-tab')[2])">
        🔍 Отследить статус по коду
      </button>
    </div>
  </section>

  <h2 class="section-title">Почему вы можете доверять SpeakUp</h2>
  <p class="section-subtitle">Принципы работы горячей линии</p>
  <div class="features-grid">
    <div class="feature-card">
      <div class="feature-icon">🔒</div>
      <h3>Без регистрации</h3>
      <p>Ваша личность защищена. Мы не собираем персональные данные и не отслеживаем IP-адрес.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">🤖</div>
      <h3>ИИ-помощник</h3>
      <p>Поможет грамотно сформулировать обращение и подскажет нужную категорию.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">📊</div>
      <h3>Прозрачный трекинг</h3>
      <p>Получите уникальный код и отслеживайте статус рассмотрения в реальном времени.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">💬</div>
      <h3>Анонимный диалог</h3>
      <p>Общайтесь с сотрудником комплаенса через защищённый чат по коду обращения.</p>
    </div>
  </div>

  <h2 class="section-title">О каких нарушениях можно сообщить</h2>
  <p class="section-subtitle">Выберите категорию, чтобы начать подачу обращения</p>
  <div class="categories-grid">
    <div class="category-card" onclick="showScreen('form', document.querySelectorAll('.nav-tab')[1])">
      <div class="cat-icon red">💰</div>
      <div>
        <h4>Вымогательство / взятка</h4>
        <p>Преподаватель или сотрудник требует деньги, услуги, подарки за оценки или зачёты</p>
      </div>
    </div>
    <div class="category-card" onclick="showScreen('form', document.querySelectorAll('.nav-tab')[1])">
      <div class="cat-icon orange">⚠️</div>
      <div>
        <h4>Давление и угрозы</h4>
        <p>Психологическое давление, угрозы отчисления, преследование за активную позицию</p>
      </div>
    </div>
    <div class="category-card" onclick="showScreen('form', document.querySelectorAll('.nav-tab')[1])">
      <div class="cat-icon purple">⚖️</div>
      <div>
        <h4>Конфликт интересов</h4>
        <p>Кумовство, протекционизм, использование служебного положения в личных целях</p>
      </div>
    </div>
    <div class="category-card" onclick="showScreen('form', document.querySelectorAll('.nav-tab')[1])">
      <div class="cat-icon blue">📚</div>
      <div>
        <h4>Академическая этика</h4>
        <p>Плагиат, фальсификация исследований, нарушения при защите работ</p>
      </div>
    </div>
    <div class="category-card" onclick="showScreen('form', document.querySelectorAll('.nav-tab')[1])">
      <div class="cat-icon yellow">😡</div>
      <div>
        <h4>Дискриминация / оскорбления</h4>
        <p>Унижение, харассмент, дискриминация по любым признакам</p>
      </div>
    </div>
    <div class="category-card" onclick="showScreen('form', document.querySelectorAll('.nav-tab')[1])">
      <div class="cat-icon green">💼</div>
      <div>
        <h4>Финансовые нарушения</h4>
        <p>Нецелевое использование средств, нарушения при распределении грантов и стипендий</p>
      </div>
    </div>
  </div>

  <div class="steps">
    <h2 class="section-title">Как это работает</h2>
    <p class="section-subtitle">Четыре простых шага</p>
    <div class="steps-grid">
      <div class="step">
        <div class="step-number">1</div>
        <h4>Заполните форму</h4>
        <p>Опишите ситуацию. ИИ-помощник подскажет, как это сделать понятно и полно.</p>
      </div>
      <div class="step">
        <div class="step-number">2</div>
        <h4>Получите код</h4>
        <p>Уникальный 8-значный код для отслеживания статуса. Сохраните его в безопасном месте.</p>
      </div>
      <div class="step">
        <div class="step-number">3</div>
        <h4>Рассмотрение</h4>
        <p>Сотрудник комплаенса изучит обращение. При необходимости — анонимный чат для уточнений.</p>
      </div>
      <div class="step">
        <div class="step-number">4</div>
        <h4>Результат</h4>
        <p>В течение 10 рабочих дней — официальный ответ с описанием принятых мер.</p>
      </div>
    </div>
  </div>
</div>

<!-- ФОРМА ПОДАЧИ -->
<div class="screen" id="form">
  <div class="form-container">
    <div class="form-header">
      <h2>Подача анонимного обращения</h2>
      <p>Заполните форму. Все поля защищены и не передаются третьим лицам.</p>
    </div>

    <div class="progress-bar">
      <div class="progress-step active">
        <div class="progress-circle">1</div>
        <span>Категория</span>
      </div>
      <div class="progress-step active">
        <div class="progress-circle">2</div>
        <span>Описание</span>
      </div>
      <div class="progress-step">
        <div class="progress-circle">3</div>
        <span>Доказательства</span>
      </div>
      <div class="progress-step">
        <div class="progress-circle">4</div>
        <span>Отправка</span>
      </div>
    </div>

    <div class="form-group">
      <label>Кто вы? (опционально, не раскрывает личность)</label>
      <select>
        <option>Студент</option>
        <option>Преподаватель</option>
        <option>Сотрудник университета</option>
        <option>Внешний партнёр / подрядчик</option>
        <option>Предпочитаю не указывать</option>
      </select>
    </div>

    <div class="form-group">
      <label>Категория нарушения *</label>
      <select>
        <option>— Выберите категорию —</option>
        <option selected>💰 Вымогательство / взятка</option>
        <option>⚠️ Давление и угрозы</option>
        <option>⚖️ Конфликт интересов</option>
        <option>📚 Академическая этика</option>
        <option>😡 Дискриминация / оскорбления</option>
        <option>💼 Финансовые нарушения</option>
        <option>❓ Другое</option>
      </select>
    </div>

    <div class="form-group">
      <label>Факультет / кафедра (опционально)</label>
      <input type="text" placeholder="Например: ФИТ, кафедра программной инженерии">
    </div>

    <div class="ai-helper">
      <div class="ai-helper-header">
        <div class="ai-icon">✨</div>
        ИИ-помощник: подсказки для описания
      </div>
      <p>Чтобы обращение было обработано быстрее, постарайтесь указать: <b>когда</b> произошло событие, <b>где</b>, <b>что именно</b> требовали / делали, есть ли <b>свидетели</b>.</p>
      <div class="ai-suggestions">
        <div class="ai-suggestion">📝 Помоги составить</div>
        <div class="ai-suggestion">🔍 Уточнить детали</div>
        <div class="ai-suggestion">⚖️ Что грозит нарушителю?</div>
      </div>
    </div>

    <div class="form-group">
      <label>Опишите ситуацию *</label>
      <textarea placeholder="Опишите подробно: когда, где, кто, что произошло. Постарайтесь придерживаться фактов..."></textarea>
      <div class="helper">Минимум 50 символов. Не указывайте свои данные.</div>
    </div>

    <div class="form-group">
      <label>Прикрепить доказательства (опционально)</label>
      <div class="file-upload">
        <div class="file-upload-icon">📎</div>
        <div><b>Нажмите или перетащите файлы</b></div>
        <div class="helper">Скриншоты, документы, аудио. До 10 файлов, макс. 20 МБ каждый.<br>Метаданные автоматически удаляются для защиты анонимности.</div>
      </div>
    </div>

    <div class="form-group">
      <label>Согласие</label>
      <div style="display:flex; gap:10px; align-items:flex-start; padding:14px; background:#f8faff; border-radius:8px;">
        <input type="checkbox" checked style="width:auto; margin-top:4px;">
        <div style="font-size:13px; color:#3a4a6a;">
          Я подтверждаю, что сведения в обращении достоверны. Я ознакомлен(а) с тем, что подача заведомо ложных обращений может повлечь ответственность согласно законодательству РФ.
        </div>
      </div>
    </div>

    <div class="form-actions">
      <button class="btn btn-outline">← Назад</button>
      <button class="btn btn-primary" onclick="showSuccess()">Отправить обращение →</button>
    </div>
  </div>

  <div id="success-modal" style="display:none; margin-top:24px;">
    <div class="form-container success-screen">
      <div class="success-icon">✓</div>
      <h2 style="font-size:24px; margin-bottom:8px;">Обращение успешно отправлено</h2>
      <p style="color:#5a6a85;">Сохраните этот код — он понадобится для отслеживания статуса и общения через чат.</p>
      <div class="ticket-code">SU-2024-A7F3K9</div>
      <p style="font-size:13px; color:#5a6a85;">⏱️ Срок рассмотрения: до 10 рабочих дней<br>📧 Первый ответ ожидается в течение 5 рабочих дней</p>
      <div style="margin-top:24px; display:flex; gap:10px; justify-content:center;">
        <button class="btn btn-outline" onclick="copyCode()">📋 Скопировать код</button>
        <button class="btn btn-primary" onclick="showScreen('track', document.querySelectorAll('.nav-tab')[2])">Перейти к отслеживанию</button>
      </div>
    </div>
  </div>
</div>

<!-- ОТСЛЕЖИВАНИЕ -->
<div class="screen" id="track">
  <div class="form-container">
    <div class="form-header">
      <h2>Отслеживание статуса обращения</h2>
      <p>Введите уникальный код, который вы получили при подаче обращения.</p>
    </div>

    <div class="form-group">
      <label>Код обращения</label>
      <input type="text" value="SU-2024-A7F3K9" style="font-family:monospace; font-size:18px; letter-spacing:2px;">
    </div>

    <div style="background:#f8faff; padding:24px; border-radius:12px; margin-top:24px;">
      <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:20px;">
        <div>
          <div style="font-size:13px; color:#5a6a85;">Обращение</div>
          <div style="font-weight:600; font-family:monospace;">SU-2024-A7F3K9</div>
        </div>
        <span class="tag tag-orange">В работе</span>
      </div>

      <div style="margin-bottom:8px; font-weight:500;">📍 Хронология обработки</div>

      <div style="border-left: 2px solid #4a6fc4; padding-left:20px; margin-left:8px;">
        <div style="margin-bottom:20px; position:relative;">
          <div style="position:absolute; left:-26px; top:2px; width:12px; height:12px; background:#4caf50; border-radius:50%; border:3px solid white; box-shadow:0 0 0 2px #4caf50;"></div>
          <div style="font-weight:600; font-size:14px;">Обращение принято</div>
          <div style="font-size:13px; color:#5a6a85;">15 марта 2024, 14:32</div>
        </div>
        <div style="margin-bottom:20px; position:relative;">
          <div style="position:absolute; left:-26px; top:2px; width:12px; height:12px; background:#4caf50; border-radius:50%; border:3px solid white; box-shadow:0 0 0 2px #4caf50;"></div>
          <div style="font-weight:600; font-size:14px;">Категоризировано ИИ</div>
          <div style="font-size:13px; color:#5a6a85;">15 марта 2024, 14:35 · Категория: Вымогательство</div>
        </div>
        <div style="margin-bottom:20px; position:relative;">
          <div style="position:absolute; left:-26px; top:2px; width:12px; height:12px; background:#4caf50; border-radius:50%; border:3px solid white; box-shadow:0 0 0 2px #4caf50;"></div>
          <div style="font-weight:600; font-size:14px;">Назначен ответственный</div>
          <div style="font-size:13px; color:#5a6a85;">16 марта 2024, 10:14 · Сотрудник комплаенса №3</div>
        </div>
        <div style="margin-bottom:20px; position:relative;">
          <div style="position:absolute; left:-26px; top:2px; width:12px; height:12px; background:#ffa726; border-radius:50%; border:3px solid white; box-shadow:0 0 0 2px #ffa726;"></div>
          <div style="font-weight:600; font-size:14px;">Запрос уточнений</div>
          <div style="font-size:13px; color:#5a6a85;">18 марта 2024, 11:00 · <a href="#" onclick="showScreen('chat', document.querySelectorAll('.nav-tab')[3]); return false;" style="color:#4a6fc4;">Перейти в чат →</a></div>
        </div>
        <div style="opacity:0.5; position:relative;">
          <div style="position:absolute; left:-26px; top:2px; width:12px; height:12px; background:#d5dce6; border-radius:50%; border:3px solid white; box-shadow:0 0 0 2px #d5dce6;"></div>
          <div style="font-weight:600; font-size:14px;">Финальный ответ</div>
          <div style="font-size:13px; color:#5a6a85;">Ожидается до 29 марта 2024</div>
        </div>
      </div>
    </div>

    <div style="margin-top:24px; padding:16px; background:#fff8e0; border-radius:8px; font-size:14px;">
      💡 <b>Совет:</b> Сотрудник комплаенса задал вам уточняющие вопросы в чате. Ваш ответ ускорит рассмотрение.
    </div>
  </div>
</div>

<!-- ЧАТ -->
<div class="screen" id="chat">
  <div class="chat-screen">
    <div class="chat-header">
      <div>
        <h3>Анонимный диалог</h3>
        <div style="font-size:13px; opacity:0.85; margin-top:4px;">Обращение SU-2024-A7F3K9</div>
      </div>
      <div class="status">🟢 Сотрудник на связи</div>
    </div>
    <div class="chat-messages">
      <div style="text-align:center; font-size:12px; color:#5a6a85; margin-bottom:16px;">— 18 марта 2024 —</div>
      
      <div class="msg them">
        Здравствуйте. Я сотрудник комплаенса, ваше обращение получено. Все наше общение защищено и анонимно — мы не видим ваши данные.
        <div class="msg-time">11:00</div>
      </div>
      <div class="msg them">
        Чтобы продолжить разбирательство, уточните пожалуйста: помните ли вы точную дату и время инцидента? Были ли свидетели?
        <div class="msg-time">11:01</div>
      </div>
      <div class="msg you">
        Здравствуйте. Это произошло 12 марта примерно в 15:30, после консультации. Свидетелей не было, мы были вдвоём в аудитории.
        <div class="msg-time">14:23</div>
      </div>
      <div class="msg you">
        У меня есть аудиозапись разговора. Могу приложить.
        <div class="msg-time">14:24</div>
      </div>
      <div class="msg them">
        Да, приложите, пожалуйста. Используйте кнопку «скрепка» — метаданные файла будут автоматически удалены.
        <div class="msg-time">14:30</div>
      </div>
      <div class="msg them">
        ✨ <b>ИИ-помощник:</b> рекомендуем также описать поведение преподавателя — было ли это разовое требование или система.
        <div class="msg-time">14:30</div>
      </div>
    </div>
    <div class="chat-input">
      <button style="background:#f0f4fa; color:#5a6a85;">📎</button>
      <input type="text" placeholder="Введите сообщение...">
      <button>➤</button>
    </div>
  </div>
</div>

<!-- ДАШБОРД КОМПЛАЕНСА -->
<div class="screen" id="dashboard">
  <div class="dashboard-header">
    <div>
      <h2>Дашборд комплаенс-офицера</h2>
      <p style="color:#5a6a85; margin-top:4px;">Обзор обращений и аналитика за период</p>
    </div>
    <div style="display:flex; gap:10px;">
      <button class="btn btn-outline" style="padding:10px 18px;">📥 Экспорт</button>
      <button class="btn btn-primary" style="padding:10px 18px;">+ Добавить вручную</button>
    </div>
  </div>

  <div class="stats-grid">
    <div class="stat-card">
      <div class="stat-label">Новых обращений</div>
      <div class="stat-value">12</div>
      <div class="stat-trend trend-up">↑ 3 за неделю</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">В работе</div>
      <div class="stat-value">28</div>
      <div class="stat-trend" style="color:#5a6a85;">⏱ Среднее время: 3.2 дня</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">Закрыто за месяц</div>
      <div class="stat-value">47</div>
      <div class="stat-trend trend-up">↑ 18% к прошлому</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">Удовлетворённость</div>
      <div class="stat-value">4.2 <span style="font-size:16px; color:#5a6a85;">/ 5</span></div>
      <div class="stat-trend trend-up">↑ 0.3 за квартал</div>
    </div>
  </div>

  <div class="dashboard-grid">
    <div class="panel">
      <div class="panel-header">
        <h3>Очередь обращений</h3>
        <div class="filters">
          <button class="filter-chip active">Все (40)</button>
          <button class="filter-chip">🔴 Высокий</button>
          <button class="filter-chip">⏰ Просрочены</button>
        </div>
      </div>
      <div class="ticket-list">
        <div class="ticket-row">
          <div class="ticket-id">SU-2024-A7F3K9</div>
          <div>
            <div class="ticket-title"><span class="priority high"></span>Требование оплаты за зачёт</div>
            <div class="ticket-meta">Студент · ФИТ · ИИ-категоризация: 96%</div>
          </div>
          <div><span class="tag tag-red">Вымогательство</span></div>
          <div><span class="tag tag-orange">В работе</span></div>
          <div class="ticket-meta">2 дня</div>
        </div>
        <div class="ticket-row">
          <div class="ticket-id">SU-2024-B2M8L4</div>
          <div>
            <div class="ticket-title"><span class="priority high"></span>Давление при защите диплома</div>
            <div class="ticket-meta">Студент · Экономика · 3 файла приложено</div>
          </div>
          <div><span class="tag tag-orange">Давление</span></div>
          <div><span class="tag tag-blue">Новое</span></div>
          <div class="ticket-meta">5 ч.</div>
        </div>
        <div class="ticket-row">
          <div class="ticket-id">SU-2024-C9Q1X2</div>
          <div>
            <div class="ticket-title"><span class="priority medium"></span>Неравное распределение премии</div>
            <div class="ticket-meta">Преподаватель · Физмат · Аудиозапись</div>
          </div>
          <div><span class="tag tag-purple">Конфликт интер.</span></div>
          <div><span class="tag tag-orange">В работе</span></div>
          <div class="ticket-meta">4 дня</div>
        </div>
        <div class="ticket-row">
          <div class="ticket-id">SU-2024-D5R7T1</div>
          <div>
            <div class="ticket-title"><span class="priority medium"></span>Оскорбления на ��екции</div>
            <div class="ticket-meta">Студент · Гуманитарный · Скриншоты</div>
          </div>
          <div><span class="tag tag-orange">Дискриминация</span></div>
          <div><span class="tag tag-blue">Новое</span></div>
          <div class="ticket-meta">1 день</div>
        </div>
        <div class="ticket-row">
          <div class="ticket-id">SU-2024-E4P6N8</div>
          <div>
            <div class="ticket-title"><span class="priority low"></span>Подозрение в плагиате научной работы</div>
            <div class="ticket-meta">Преподаватель · Аспирантура</div>
          </div>
          <div><span class="tag tag-blue">Академ. этика</span></div>
          <div><span class="tag tag-green">Закрыто</span></div>
          <div class="ticket-meta">7 дней</div>
        </div>
        <div class="ticket-row">
          <div class="ticket-id">SU-2024-F1S3W5</div>
          <div>
            <div class="ticket-title"><span class="priority high"></span>Нецелевое использование гранта</div>
            <div class="ticket-meta">Анонимно · Документы приложены</div>
          </div>
          <div><span class="tag tag-green">Финансы</span></div>
          <div><span class="tag tag-orange">В работе</span></div>
          <div class="ticket-meta">3 дня</div>
        </div>
      </div>
    </div>

    <div>
      <div class="panel">
        <div class="panel-header">
          <h3>Топ категорий за месяц</h3>
        </div>
        <div class="cat-stats">
          <div class="cat-row">
            <div class="cat-row-top">
              <span>💰 Вымогательство</span>
              <b>18</b>
            </div>
            <div class="cat-bar"><div class="cat-bar-fill" style="width:85%"></div></div>
          </div>
          <div class="cat-row">
            <div class="cat-row-top">
              <span>⚠️ Давление</span>
              <b>12</b>
            </div>
            <div class="cat-bar"><div class="cat-bar-fill" style="width:60%"></div></div>
          </div>
          <div class="cat-row">
            <div class="cat-row-top">
              <span>⚖️ Конфликт интересов</span>
              <b>8</b>
            </div>
            <div class="cat-bar"><div class="cat-bar-fill" style="width:40%"></div></div>
          </div>
          <div class="cat-row">
            <div class="cat-row-top">
              <span>😡 Дискриминация</span>
              <b>5</b>
            </div>
            <div class="cat-bar"><div class="cat-bar-fill" style="width:25%"></div></div>
          </div>
          <div class="cat-row">
            <div class="cat-row-top">
              <span>📚 Академ. этика</span>
              <b>4</b>
            </div>
            <div class="cat-bar"><div class="cat-bar-fill" style="width:20%"></div></div>
          </div>

          <div class="ai-insight">
            <div class="ai-insight-title">
              <span>✨</span> ИИ-аналитика: важное
            </div>
            <p>Замечен <b>рост обращений на ФИТ</b> по категории «вымогательство» — 5 случаев за 2 недели. Рекомендуется системная проверка кафедры.</p>
          </div>
        </div>
      </div>

      <div class="panel" style="margin-top:20px;">
        <div class="panel-header">
          <h3>SLA-метрики</h3>
        </div>
        <div style="padding:20px 24px;">
          <div style="margin-bottom:14px;">
            <div style="display:flex; justify-content:space-between; font-size:14px; margin-bottom:4px;">
              <span>Среднее время первого ответа</span>
              <b style="color:#4caf50;">3.2 дня</b>
            </div>
            <div class="helper">Цель: ≤ 5 дней</div>
          </div>
          <div style="margin-bottom:14px;">
            <div style="display:flex; justify-content:space-between; font-size:14px; margin-bottom:4px;">
              <span>Доля закрытых обращений</span>
              <b style="color:#4caf50;">73%</b>
            </div>
            <div class="helper">Цель: ≥ 60%</div>
          </div>
          <div>
            <div style="display:flex; justify-content:space-between; font-size:14px; margin-bottom:4px;">
              <span>Доля анонимных обращений</span>
              <b style="color:#4caf50;">82%</b>
            </div>
            <div class="helper">Цель: ≥ 70%</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<footer>
  <p><b>SpeakUp</b> · Горячая линия комплаенса университета</p>
  <p style="margin-top:6px;">© 2024 · Соответствует 152-ФЗ · Шифрование AES-256 · No-log политика</p>
  <p style="margin-top:6px;">📞 8 (800) 000-00-00 (бесплатно по России) · ✉️ compliance@university.ru</p>
</footer>

<script>
  function showScreen(id, tab) {
    document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
    if (tab) tab.classList.add('active');
    window.scrollTo({top: 0, behavior: 'smooth'});
  }
  function showSuccess() {
    document.getElementById('success-modal').style.display = 'block';
    document.getElementById('success-modal').scrollIntoView({behavior: 'smooth'});
  }
  function copyCode() {
    navigator.clipboard?.writeText('SU-2024-A7F3K9');
    alert('Код скопирован: SU-2024-A7F3K9');
  }
</script>

</body>
</html>
