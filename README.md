<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>DompetKu 💸</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=DM+Mono:wght@400;500&display=swap');

  :root {
    --bg: #0f0f14;
    --card: #17171f;
    --card2: #1e1e28;
    --border: #2a2a38;
    --accent: #7c6af7;
    --accent2: #a78bfa;
    --green: #34d399;
    --red: #f87171;
    --yellow: #fbbf24;
    --text: #f1f0ff;
    --muted: #8b8aa8;
    --dana: #118EEA;
    --gopay: #00AED6;
    --ovo: #4c3494;
    --bca: #005CA9;
    --bri: #003F8A;
    --tunai: #34d399;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Plus Jakarta Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100dvh;
    max-width: 430px;
    margin: 0 auto;
    padding-bottom: 90px;
    position: relative;
  }

  /* HEADER */
  .header {
    padding: 20px 20px 12px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: sticky;
    top: 0;
    background: var(--bg);
    z-index: 10;
    border-bottom: 1px solid var(--border);
  }
  .header-logo { font-size: 18px; font-weight: 800; letter-spacing: -0.5px; }
  .header-logo span { color: var(--accent2); }
  .header-date { font-size: 12px; color: var(--muted); font-family: 'DM Mono', monospace; }

  /* HERO BALANCE */
  .balance-card {
    margin: 16px;
    background: linear-gradient(135deg, #2d1b69 0%, #1a1433 50%, #0f1628 100%);
    border-radius: 20px;
    padding: 22px;
    border: 1px solid #3d2d8a;
    position: relative;
    overflow: hidden;
  }
  .balance-card::before {
    content: '';
    position: absolute;
    top: -30px; right: -30px;
    width: 120px; height: 120px;
    background: radial-gradient(circle, rgba(124,106,247,0.25) 0%, transparent 70%);
  }
  .balance-label { font-size: 11px; color: #a78bfa99; text-transform: uppercase; letter-spacing: 1.5px; font-weight: 600; }
  .balance-amount {
    font-size: 34px;
    font-weight: 800;
    color: #fff;
    margin: 6px 0 4px;
    font-family: 'DM Mono', monospace;
    letter-spacing: -1px;
  }
  .balance-sub { font-size: 12px; color: var(--muted); }
  .balance-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-top: 18px;
  }
  .balance-stat {
    background: rgba(255,255,255,0.05);
    border-radius: 12px;
    padding: 10px 12px;
  }
  .balance-stat-label { font-size: 10px; color: var(--muted); text-transform: uppercase; letter-spacing: 1px; }
  .balance-stat-value { font-size: 16px; font-weight: 700; margin-top: 3px; font-family: 'DM Mono', monospace; }
  .income-val { color: var(--green); }
  .expense-val { color: var(--red); }

  /* WALLETS */
  .section-title {
    font-size: 13px;
    font-weight: 700;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 1.2px;
    padding: 0 20px;
    margin: 20px 0 10px;
  }
  .wallets-scroll {
    display: flex;
    gap: 10px;
    padding: 0 20px;
    overflow-x: auto;
    scrollbar-width: none;
  }
  .wallets-scroll::-webkit-scrollbar { display: none; }
  .wallet-chip {
    flex-shrink: 0;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 12px 16px;
    min-width: 130px;
    cursor: pointer;
    transition: all 0.2s;
  }
  .wallet-chip:hover { transform: translateY(-2px); border-color: var(--accent); }
  .wallet-chip.active { border-color: var(--accent); background: rgba(124,106,247,0.1); }
  .wallet-dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    display: inline-block;
    margin-right: 6px;
  }
  .wallet-name { font-size: 12px; font-weight: 600; display: flex; align-items: center; }
  .wallet-bal { font-size: 15px; font-weight: 700; margin-top: 4px; font-family: 'DM Mono', monospace; }

  /* QUICK ACTIONS */
  .quick-actions {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    padding: 0 20px;
    margin: 6px 0;
  }
  .qa-btn {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 6px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 14px 6px;
    cursor: pointer;
    transition: all 0.2s;
    font-size: 11px;
    font-weight: 600;
    color: var(--text);
  }
  .qa-btn:hover { border-color: var(--accent); background: rgba(124,106,247,0.08); }
  .qa-icon { font-size: 22px; }

  /* TRANSACTIONS */
  .tx-list { padding: 0 16px; }
  .tx-item {
    display: flex;
    align-items: center;
    gap: 12px;
    background: var(--card);
    border-radius: 14px;
    padding: 12px 14px;
    margin-bottom: 8px;
    border: 1px solid var(--border);
    cursor: pointer;
    transition: all 0.2s;
  }
  .tx-item:hover { border-color: var(--border); background: var(--card2); }
  .tx-icon {
    width: 40px; height: 40px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
    flex-shrink: 0;
  }
  .tx-info { flex: 1; }
  .tx-name { font-size: 14px; font-weight: 600; }
  .tx-meta { font-size: 11px; color: var(--muted); margin-top: 2px; display: flex; gap: 6px; }
  .tx-source {
    background: rgba(255,255,255,0.08);
    padding: 2px 7px;
    border-radius: 20px;
    font-size: 10px;
    font-weight: 600;
  }
  .tx-amount { font-size: 15px; font-weight: 700; font-family: 'DM Mono', monospace; }
  .tx-amount.income { color: var(--green); }
  .tx-amount.expense { color: var(--red); }

  /* BOTTOM NAV */
  .bottom-nav {
    position: fixed;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 100%;
    max-width: 430px;
    background: rgba(15,15,20,0.95);
    backdrop-filter: blur(20px);
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-around;
    padding: 10px 0 max(10px, env(safe-area-inset-bottom));
    z-index: 100;
  }
  .nav-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 3px;
    font-size: 10px;
    font-weight: 600;
    color: var(--muted);
    cursor: pointer;
    padding: 4px 16px;
    border-radius: 10px;
    transition: all 0.2s;
  }
  .nav-item.active { color: var(--accent2); }
  .nav-icon { font-size: 22px; }
  .nav-add {
    width: 48px; height: 48px;
    background: linear-gradient(135deg, var(--accent), #9d4edd);
    border-radius: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 26px;
    color: white;
    cursor: pointer;
    margin-top: -14px;
    box-shadow: 0 4px 20px rgba(124,106,247,0.5);
    transition: all 0.2s;
  }
  .nav-add:hover { transform: scale(1.08); }

  /* MODAL */
  .modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.7);
    z-index: 200;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.3s;
  }
  .modal-overlay.open {
    opacity: 1;
    pointer-events: all;
  }
  .modal {
    background: var(--card);
    border-radius: 24px 24px 0 0;
    padding: 24px 20px 40px;
    width: 100%;
    max-width: 430px;
    max-height: 90dvh;
    overflow-y: auto;
    transform: translateY(100%);
    transition: transform 0.35s cubic-bezier(0.34, 1.56, 0.64, 1);
    border-top: 1px solid var(--border);
  }
  .modal-overlay.open .modal {
    transform: translateY(0);
  }
  .modal-handle {
    width: 40px; height: 4px;
    background: var(--border);
    border-radius: 2px;
    margin: 0 auto 20px;
  }
  .modal-title { font-size: 18px; font-weight: 800; margin-bottom: 20px; }

  .type-tabs {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
    margin-bottom: 18px;
  }
  .type-tab {
    padding: 10px;
    border-radius: 12px;
    border: 1px solid var(--border);
    text-align: center;
    font-size: 13px;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.2s;
  }
  .type-tab.income.active { background: rgba(52,211,153,0.15); border-color: var(--green); color: var(--green); }
  .type-tab.expense.active { background: rgba(248,113,113,0.15); border-color: var(--red); color: var(--red); }
  .type-tab:not(.active) { color: var(--muted); }

  .form-group { margin-bottom: 14px; }
  .form-label { font-size: 11px; font-weight: 700; color: var(--muted); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 6px; display: block; }
  .form-input {
    width: 100%;
    background: var(--bg);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 12px 14px;
    font-size: 15px;
    color: var(--text);
    font-family: 'Plus Jakarta Sans', sans-serif;
    outline: none;
    transition: border-color 0.2s;
  }
  .form-input:focus { border-color: var(--accent); }
  .form-input::placeholder { color: var(--muted); }

  .amount-input-wrap { position: relative; }
  .amount-prefix {
    position: absolute;
    left: 14px; top: 50%;
    transform: translateY(-50%);
    font-size: 15px; font-weight: 700;
    color: var(--muted);
    font-family: 'DM Mono', monospace;
  }
  .amount-input-wrap .form-input { padding-left: 42px; font-family: 'DM Mono', monospace; font-size: 20px; font-weight: 700; }

  .source-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 8px;
  }
  .source-btn {
    padding: 10px 8px;
    border-radius: 12px;
    border: 1px solid var(--border);
    text-align: center;
    cursor: pointer;
    font-size: 11px;
    font-weight: 700;
    color: var(--muted);
    transition: all 0.2s;
  }
  .source-btn.active { color: var(--text); border-color: currentColor; }
  .source-btn[data-src="Dana"].active { color: var(--dana); background: rgba(17,142,234,0.1); }
  .source-btn[data-src="GoPay"].active { color: var(--gopay); background: rgba(0,174,214,0.1); }
  .source-btn[data-src="OVO"].active { color: #a78bfa; background: rgba(76,52,148,0.2); }
  .source-btn[data-src="BCA"].active { color: #60a5fa; background: rgba(0,92,169,0.15); }
  .source-btn[data-src="BRI"].active { color: #93c5fd; background: rgba(0,63,138,0.15); }
  .source-btn[data-src="Tunai"].active { color: var(--tunai); background: rgba(52,211,153,0.1); }
  .source-btn[data-src="Gajian"].active { color: var(--yellow); background: rgba(251,191,36,0.1); }
  .source-btn[data-src="Transfer"].active { color: var(--accent2); background: rgba(124,106,247,0.1); }
  .source-btn[data-src="Lainnya"].active { color: var(--muted); background: rgba(255,255,255,0.05); }

  .submit-btn {
    width: 100%;
    padding: 16px;
    background: linear-gradient(135deg, var(--accent), #9d4edd);
    border: none;
    border-radius: 14px;
    color: white;
    font-size: 15px;
    font-weight: 800;
    cursor: pointer;
    margin-top: 20px;
    font-family: 'Plus Jakarta Sans', sans-serif;
    transition: all 0.2s;
  }
  .submit-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(124,106,247,0.4); }

  /* AI CHAT PAGE */
  .page { display: none; padding-bottom: 80px; }
  .page.active { display: block; }

  .chat-messages {
    padding: 16px;
    display: flex;
    flex-direction: column;
    gap: 12px;
    min-height: calc(100dvh - 200px);
  }
  .msg {
    max-width: 85%;
    padding: 12px 15px;
    border-radius: 18px;
    font-size: 14px;
    line-height: 1.5;
  }
  .msg.bot {
    background: var(--card2);
    border: 1px solid var(--border);
    border-radius: 18px 18px 18px 4px;
    align-self: flex-start;
  }
  .msg.user {
    background: linear-gradient(135deg, var(--accent), #9d4edd);
    border-radius: 18px 18px 4px 18px;
    align-self: flex-end;
    color: white;
  }
  .msg-time { font-size: 10px; color: var(--muted); margin-top: 4px; }

  .chat-input-area {
    position: fixed;
    bottom: 65px;
    left: 50%;
    transform: translateX(-50%);
    width: 100%;
    max-width: 430px;
    padding: 10px 16px;
    background: rgba(15,15,20,0.95);
    backdrop-filter: blur(20px);
    border-top: 1px solid var(--border);
    display: flex;
    gap: 10px;
  }
  .chat-input {
    flex: 1;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 22px;
    padding: 10px 16px;
    font-size: 14px;
    color: var(--text);
    outline: none;
    font-family: 'Plus Jakarta Sans', sans-serif;
  }
  .chat-input:focus { border-color: var(--accent); }
  .chat-send {
    width: 42px; height: 42px;
    background: linear-gradient(135deg, var(--accent), #9d4edd);
    border: none;
    border-radius: 50%;
    color: white;
    font-size: 18px;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    transition: all 0.2s;
  }
  .chat-send:hover { transform: scale(1.08); }

  /* REPORT PAGE */
  .report-period {
    display: flex;
    gap: 8px;
    padding: 0 16px;
    margin: 12px 0;
    overflow-x: auto;
    scrollbar-width: none;
  }
  .period-btn {
    flex-shrink: 0;
    padding: 7px 16px;
    border-radius: 20px;
    border: 1px solid var(--border);
    font-size: 12px;
    font-weight: 700;
    color: var(--muted);
    cursor: pointer;
    transition: all 0.2s;
  }
  .period-btn.active { background: rgba(124,106,247,0.15); border-color: var(--accent); color: var(--accent2); }

  .chart-bar-wrap {
    padding: 16px;
    background: var(--card);
    border-radius: 16px;
    margin: 0 16px 16px;
    border: 1px solid var(--border);
  }
  .chart-title { font-size: 13px; font-weight: 700; margin-bottom: 14px; color: var(--muted); }
  .bar-group { display: flex; align-items: flex-end; gap: 6px; height: 100px; margin-bottom: 8px; }
  .bar-col { flex: 1; display: flex; flex-direction: column; align-items: center; gap: 4px; height: 100%; justify-content: flex-end; }
  .bar {
    width: 100%;
    border-radius: 6px 6px 0 0;
    transition: height 0.5s ease;
    min-height: 4px;
  }
  .bar.income-bar { background: linear-gradient(to top, #059669, #34d399); }
  .bar.expense-bar { background: linear-gradient(to top, #dc2626, #f87171); }
  .bar-label { font-size: 9px; color: var(--muted); font-weight: 600; }

  .category-list { padding: 0 16px; }
  .cat-item {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 12px;
  }
  .cat-icon-wrap {
    width: 36px; height: 36px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 16px;
    flex-shrink: 0;
  }
  .cat-info { flex: 1; }
  .cat-name { font-size: 13px; font-weight: 600; }
  .cat-bar-bg {
    height: 4px;
    background: var(--border);
    border-radius: 2px;
    margin-top: 4px;
    overflow: hidden;
  }
  .cat-bar-fill { height: 100%; border-radius: 2px; }
  .cat-amount { font-size: 13px; font-weight: 700; font-family: 'DM Mono', monospace; color: var(--red); }

  /* Loading dot */
  .loading-dots { display: flex; gap: 4px; align-items: center; padding: 4px 0; }
  .loading-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--accent2);
    animation: pulse 1.2s infinite;
  }
  .loading-dot:nth-child(2) { animation-delay: 0.2s; }
  .loading-dot:nth-child(3) { animation-delay: 0.4s; }
  @keyframes pulse {
    0%, 100% { opacity: 0.3; transform: scale(0.8); }
    50% { opacity: 1; transform: scale(1); }
  }

  .empty-state {
    text-align: center;
    padding: 40px 20px;
    color: var(--muted);
  }
  .empty-state .empty-icon { font-size: 48px; margin-bottom: 12px; }
  .empty-state p { font-size: 14px; line-height: 1.6; }
</style>
</head>
<body>

<!-- HEADER -->
<div class="header">
  <div class="header-logo">Dompet<span>Ku</span> 💸</div>
  <div class="header-date" id="headerDate"></div>
</div>

<!-- HOME PAGE -->
<div class="page active" id="page-home">

  <!-- Balance Card -->
  <div class="balance-card">
    <div class="balance-label">Total Saldo</div>
    <div class="balance-amount" id="totalBalance">Rp 0</div>
    <div class="balance-sub">Semua dompet & rekening</div>
    <div class="balance-grid">
      <div class="balance-stat">
        <div class="balance-stat-label">Pemasukan</div>
        <div class="balance-stat-value income-val" id="totalIncome">Rp 0</div>
      </div>
      <div class="balance-stat">
        <div class="balance-stat-label">Pengeluaran</div>
        <div class="balance-stat-value expense-val" id="totalExpense">Rp 0</div>
      </div>
    </div>
  </div>

  <!-- Wallets -->
  <div class="section-title">Dompet & Rekening</div>
  <div class="wallets-scroll" id="walletsList"></div>

  <!-- Quick Actions -->
  <div class="section-title" style="margin-top:20px">Aksi Cepat</div>
  <div class="quick-actions">
    <div class="qa-btn" onclick="openModal('expense')"><span class="qa-icon">💸</span>Keluar</div>
    <div class="qa-btn" onclick="openModal('income')"><span class="qa-icon">💰</span>Masuk</div>
    <div class="qa-btn" onclick="switchPage('laporan')"><span class="qa-icon">📊</span>Laporan</div>
    <div class="qa-btn" onclick="switchPage('ai')"><span class="qa-icon">🤖</span>Tanya AI</div>
  </div>

  <!-- Transactions -->
  <div class="section-title" style="margin-top:20px">Transaksi Terbaru</div>
  <div class="tx-list" id="txList">
    <div class="empty-state">
      <div class="empty-icon">📝</div>
      <p>Belum ada transaksi.<br>Tap <strong>+</strong> untuk tambah transaksi.</p>
    </div>
  </div>

  <!-- Settings -->
  <div class="section-title" style="margin-top:20px">Pengaturan</div>
  <div style="padding: 0 16px;">
    <div class="tx-item" onclick="resetBalance()" style="cursor:pointer;">
      <div class="tx-icon" style="background:#fbbf2422;">🔄</div>
      <div class="tx-info">
        <div class="tx-name">Reset Saldo ke Rp 0</div>
        <div class="tx-meta"><span>Hapus semua transaksi, mulai dari nol lagi</span></div>
      </div>
    </div>
    <div class="tx-item" onclick="exportData()" style="cursor:pointer;">
      <div class="tx-icon" style="background:#34d39922;">⬇️</div>
      <div class="tx-info">
        <div class="tx-name">Export Data (Backup)</div>
        <div class="tx-meta"><span>Simpan data transaksi sebagai file</span></div>
      </div>
    </div>
  </div>
</div>

<!-- LAPORAN PAGE -->
<div class="page" id="page-laporan">
  <div style="padding: 16px 20px 0; font-size:20px; font-weight:800;">Laporan 📊</div>
  
  <div class="report-period">
    <div class="period-btn active" onclick="setPeriod('minggu',this)">Minggu Ini</div>
    <div class="period-btn" onclick="setPeriod('bulan',this)">Bulan Ini</div>
    <div class="period-btn" onclick="setPeriod('semua',this)">Semua</div>
  </div>

  <div class="chart-bar-wrap">
    <div class="chart-title">Pemasukan vs Pengeluaran (7 hari)</div>
    <div class="bar-group" id="barChart"></div>
    <div style="display:flex;gap:16px;font-size:11px;font-weight:600;">
      <span style="color:var(--green);">▮ Pemasukan</span>
      <span style="color:var(--red);">▮ Pengeluaran</span>
    </div>
  </div>

  <div class="section-title">Kategori Terbesar</div>
  <div class="category-list" id="categoryList"></div>
</div>

<!-- AI PAGE -->
<div class="page" id="page-ai">
  <div style="padding: 16px 20px 0; display:flex; justify-content:space-between; align-items:center;">
    <div style="font-size:20px; font-weight:800;">AI Finance 🤖</div>
    <div onclick="openApiKeyModal()" style="font-size:20px; cursor:pointer; padding:4px 8px;">⚙️</div>
  </div>
  <div style="padding: 4px 20px 8px; font-size:12px; color:var(--muted);">Tanya soal keuanganmu, minta saran, atau minta ringkasan.</div>

  <div id="apiKeyBanner" style="display:none; margin:0 16px 12px; padding:12px 14px; background:rgba(251,191,36,0.1); border:1px solid var(--yellow); border-radius:12px; font-size:12px; color:var(--yellow);">
    ⚠️ Belum ada API Key. Tap ⚙️ di atas untuk mengisinya supaya AI Chat bisa jalan.
  </div>

  <div class="chat-messages" id="chatMessages">
    <div class="msg bot">
      Halo! Aku asisten keuangan pribadimu 💜<br><br>
      Kamu bisa tanya:<br>
      • "Berapa total pengeluaranku bulan ini?"<br>
      • "Kasih saran hemat dong"<br>
      • "Analisis keuanganku"<br>
      • Atau pertanyaan finansial lainnya!
      <div class="msg-time">Sekarang</div>
    </div>
  </div>

  <div class="chat-input-area">
    <input class="chat-input" id="chatInput" placeholder="Tanya soal keuanganmu..." onkeydown="if(event.key==='Enter')sendChat()">
    <button class="chat-send" onclick="sendChat()">➤</button>
  </div>
</div>

<!-- API KEY MODAL -->
<div class="modal-overlay" id="apiKeyOverlay" onclick="if(event.target===this)closeApiKeyModal()">
  <div class="modal">
    <div class="modal-handle"></div>
    <div class="modal-title">🔑 Atur API Key</div>
    <div style="font-size:13px; color:var(--muted); margin-bottom:16px; line-height:1.6;">
      Masukkan API Key dari <strong>console.anthropic.com</strong> agar AI Chat bisa berfungsi. Key kamu hanya disimpan di browser HP ini, tidak dikirim ke mana pun selain ke server Anthropic langsung.
    </div>
    <div class="form-group">
      <label class="form-label">API Key</label>
      <input class="form-input" id="apiKeyInput" type="password" placeholder="sk-ant-...">
    </div>
    <button class="submit-btn" onclick="saveApiKey()">Simpan API Key</button>
    <div style="text-align:center; margin-top:12px; font-size:12px; color:var(--muted); cursor:pointer;" onclick="clearApiKey()">Hapus API Key</div>
  </div>
</div>

<!-- BOTTOM NAV -->
<div class="bottom-nav">
  <div class="nav-item active" id="nav-home" onclick="switchPage('home')">
    <span class="nav-icon">🏠</span>Beranda
  </div>
  <div class="nav-item" id="nav-laporan" onclick="switchPage('laporan')">
    <span class="nav-icon">📊</span>Laporan
  </div>
  <div class="nav-add" onclick="openModal('expense')">+</div>
  <div class="nav-item" id="nav-ai" onclick="switchPage('ai')">
    <span class="nav-icon">🤖</span>AI Chat
  </div>
  <div class="nav-item" id="nav-dompet" onclick="switchPage('dompet')">
    <span class="nav-icon">💳</span>Dompet
  </div>
</div>

<!-- DOMPET PAGE (hidden, triggered from nav) -->
<div class="page" id="page-dompet">
  <div style="padding: 16px 20px 0; font-size:20px; font-weight:800;">Kelola Dompet 💳</div>
  <div id="walletDetail" style="padding:16px;"></div>
  <div style="padding:0 16px;">
    <button class="submit-btn" style="background:linear-gradient(135deg,#dc2626,#f87171);" onclick="resetAllData()">🗑️ Reset Semua Data</button>
  </div>
</div>

<!-- MODAL ADD TRANSACTION -->
<div class="modal-overlay" id="modalOverlay" onclick="closeModal(event)">
  <div class="modal">
    <div class="modal-handle"></div>
    <div class="modal-title">Tambah Transaksi</div>

    <div class="type-tabs">
      <div class="type-tab expense active" id="tabExpense" onclick="setType('expense')">💸 Pengeluaran</div>
      <div class="type-tab income" id="tabIncome" onclick="setType('income')">💰 Pemasukan</div>
    </div>

    <div class="form-group">
      <label class="form-label">Nominal</label>
      <div class="amount-input-wrap">
        <span class="amount-prefix">Rp</span>
        <input class="form-input" id="inputAmount" type="number" placeholder="0" inputmode="numeric">
      </div>
    </div>

    <div class="form-group">
      <label class="form-label">Keterangan</label>
      <input class="form-input" id="inputNote" type="text" placeholder="Contoh: Makan siang, Gajian, dll">
    </div>

    <div class="form-group">
      <label class="form-label">Sumber / Dompet</label>
      <div class="source-grid" id="sourceGrid">
        <div class="source-btn" data-src="Dana" onclick="selectSource(this)">🔵 Dana</div>
        <div class="source-btn" data-src="GoPay" onclick="selectSource(this)">💙 GoPay</div>
        <div class="source-btn" data-src="OVO" onclick="selectSource(this)">💜 OVO</div>
        <div class="source-btn" data-src="BCA" onclick="selectSource(this)">🏦 BCA</div>
        <div class="source-btn" data-src="BRI" onclick="selectSource(this)">🏦 BRI</div>
        <div class="source-btn" data-src="Tunai" onclick="selectSource(this)">💵 Tunai</div>
        <div class="source-btn" data-src="Gajian" onclick="selectSource(this)">💼 Gajian</div>
        <div class="source-btn" data-src="Transfer" onclick="selectSource(this)">↔️ Transfer</div>
        <div class="source-btn" data-src="Lainnya" onclick="selectSource(this)">➕ Lainnya</div>
      </div>
    </div>

    <div class="form-group">
      <label class="form-label">Kategori</label>
      <input class="form-input" id="inputCategory" type="text" placeholder="Makan, Transport, Hiburan, dll">
    </div>

    <button class="submit-btn" onclick="saveTransaction()">Simpan Transaksi</button>
  </div>
</div>

<!-- CONFIRM MODAL -->
<div class="modal-overlay" id="confirmOverlay">
  <div class="modal" style="padding-bottom:24px;">
    <div class="modal-handle"></div>
    <div class="modal-title" id="confirmTitle">Konfirmasi</div>
    <div style="font-size:14px;color:var(--muted);margin-bottom:20px;" id="confirmMsg"></div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;">
      <button class="submit-btn" style="margin-top:0;background:var(--card2);border:1px solid var(--border);" onclick="closeConfirm()">Tutup</button>
      <button class="submit-btn" style="margin-top:0;background:linear-gradient(135deg,#dc2626,#f87171);" id="confirmYesBtn">Ya, Lanjut</button>
    </div>
  </div>
</div>

<script>
function showConfirm(title, msg, onYes) {
  document.getElementById('confirmTitle').textContent = title;
  document.getElementById('confirmMsg').textContent = msg;
  const yesBtn = document.getElementById('confirmYesBtn');
  yesBtn.style.display = '';
  yesBtn.textContent = 'Ya, Lanjut';
  yesBtn.style.background = 'linear-gradient(135deg,#dc2626,#f87171)';
  yesBtn.onclick = () => { closeConfirm(); onYes(); };
  document.getElementById('confirmOverlay').classList.add('open');
}
function showInfo(title, msg) {
  document.getElementById('confirmTitle').textContent = title;
  document.getElementById('confirmMsg').textContent = msg;
  const yesBtn = document.getElementById('confirmYesBtn');
  yesBtn.style.display = 'none';
  document.getElementById('confirmOverlay').classList.add('open');
}
function closeConfirm() {
  document.getElementById('confirmOverlay').classList.remove('open');
}
</script>

<script>
// ==================== STATE ====================
let transactions = JSON.parse(localStorage.getItem('dompetku_tx') || '[]');
let currentType = 'expense';
let selectedSource = null;
let currentPeriod = 'minggu';

const WALLET_COLORS = {
  Dana: '#118EEA', GoPay: '#00AED6', OVO: '#a78bfa',
  BCA: '#60a5fa', BRI: '#93c5fd', Tunai: '#34d399',
  Gajian: '#fbbf24', Transfer: '#c084fc', Lainnya: '#9ca3af'
};
const WALLET_EMOJI = {
  Dana: '🔵', GoPay: '💙', OVO: '💜',
  BCA: '🏦', BRI: '🏦', Tunai: '💵',
  Gajian: '💼', Transfer: '↔️', Lainnya: '➕'
};
const CAT_EMOJI = {
  Makan: '🍜', Transport: '🚌', Belanja: '🛍️', Hiburan: '🎮',
  Kesehatan: '💊', Tagihan: '📱', Kopi: '☕', Bensin: '⛽',
  Gajian: '💰', Bonus: '🎁', Freelance: '💻', default: '💰'
};

// ==================== INIT ====================
function init() {
  const now = new Date();
  document.getElementById('headerDate').textContent =
    now.toLocaleDateString('id-ID', { weekday:'short', day:'numeric', month:'short' });
  renderAll();
  updateApiKeyBanner();
}

function renderAll() {
  renderBalance();
  renderWallets();
  renderTransactions();
  renderReport();
  renderWalletDetail();
}

// ==================== BALANCE ====================
function renderBalance() {
  const totalIncome = transactions.filter(t => t.type === 'income').reduce((s,t) => s + t.amount, 0);
  const totalExpense = transactions.filter(t => t.type === 'expense').reduce((s,t) => s + t.amount, 0);
  const balance = totalIncome - totalExpense;
  const balEl = document.getElementById('totalBalance');
  balEl.textContent = formatRp(balance);
  balEl.style.color = balance < 0 ? 'var(--red)' : '#fff';
  document.getElementById('totalIncome').textContent = formatRp(totalIncome);
  document.getElementById('totalExpense').textContent = formatRp(totalExpense);
}

// ==================== WALLETS ====================
function getWallets() {
  const map = {};
  transactions.forEach(t => {
    const src = t.source || 'Lainnya';
    if (!map[src]) map[src] = 0;
    if (t.type === 'income') map[src] += t.amount;
    else map[src] -= t.amount;
  });
  return map;
}

function renderWallets() {
  const wallets = getWallets();
  const el = document.getElementById('walletsList');
  if (Object.keys(wallets).length === 0) {
    el.innerHTML = `<div style="color:var(--muted);font-size:13px;padding:4px 0;">Belum ada data dompet.</div>`;
    return;
  }
  el.innerHTML = Object.entries(wallets).map(([name, bal]) => `
    <div class="wallet-chip">
      <div class="wallet-name">
        <span class="wallet-dot" style="background:${WALLET_COLORS[name]||'#9ca3af'}"></span>
        ${WALLET_EMOJI[name]||'💰'} ${name}
      </div>
      <div class="wallet-bal" style="color:${bal>=0?'var(--green)':'var(--red)'}">${formatRp(bal)}</div>
    </div>
  `).join('');
}

function renderWalletDetail() {
  const wallets = getWallets();
  const el = document.getElementById('walletDetail');
  if (Object.keys(wallets).length === 0) {
    el.innerHTML = `<div class="empty-state"><div class="empty-icon">💳</div><p>Belum ada data dompet atau rekening.</p></div>`;
    return;
  }
  el.innerHTML = Object.entries(wallets).map(([name, bal]) => `
    <div class="tx-item">
      <div class="tx-icon" style="background:${WALLET_COLORS[name]||'#1e1e28'}22;font-size:22px;">${WALLET_EMOJI[name]||'💳'}</div>
      <div class="tx-info">
        <div class="tx-name">${name}</div>
        <div class="tx-meta">${transactions.filter(t=>t.source===name).length} transaksi</div>
      </div>
      <div class="tx-amount ${bal>=0?'income':'expense'}">${formatRp(bal)}</div>
    </div>
  `).join('');
}

// ==================== TRANSACTIONS ====================
function renderTransactions() {
  const el = document.getElementById('txList');
  const sorted = [...transactions].sort((a,b) => b.id - a.id).slice(0, 30);
  if (sorted.length === 0) {
    el.innerHTML = `<div class="empty-state"><div class="empty-icon">📝</div><p>Belum ada transaksi.<br>Tap <strong>+</strong> untuk tambah transaksi.</p></div>`;
    return;
  }
  el.innerHTML = sorted.map(t => {
    const cat = t.category || (t.type === 'income' ? 'Pemasukan' : 'Pengeluaran');
    const emoji = CAT_EMOJI[cat] || (t.type === 'income' ? '💰' : '💸');
    const color = t.type === 'income' ? '#34d39322' : '#f8717122';
    const d = new Date(t.id);
    const dateStr = d.toLocaleDateString('id-ID', {day:'numeric',month:'short'}) + ' ' +
                    d.toLocaleTimeString('id-ID',{hour:'2-digit',minute:'2-digit'});
    return `
      <div class="tx-item">
        <div class="tx-icon" style="background:${color}">${emoji}</div>
        <div class="tx-info">
          <div class="tx-name">${t.note || cat}</div>
          <div class="tx-meta">
            <span class="tx-source" style="color:${WALLET_COLORS[t.source]||'#9ca3af'}">${t.source||'Lainnya'}</span>
            <span>${dateStr}</span>
          </div>
        </div>
        <div class="tx-amount ${t.type}">${t.type==='income'?'+':'-'}${formatRp(t.amount)}</div>
        <div onclick="deleteTx(${t.id})" style="font-size:16px;color:var(--muted);padding:4px 6px;cursor:pointer;">✕</div>
      </div>
    `;
  }).join('');
}

function deleteTx(id) {
  showConfirm('Hapus Transaksi', 'Transaksi ini akan dihapus secara permanen.', () => {
    transactions = transactions.filter(t => t.id !== id);
    localStorage.setItem('dompetku_tx', JSON.stringify(transactions));
    renderAll();
  });
}

// ==================== REPORT ====================
function renderReport() {
  renderBarChart();
  renderCategories();
}

function getFilteredTx() {
  const now = new Date();
  return transactions.filter(t => {
    const d = new Date(t.id);
    if (currentPeriod === 'minggu') {
      const diff = (now - d) / (1000*60*60*24);
      return diff <= 7;
    } else if (currentPeriod === 'bulan') {
      return d.getMonth() === now.getMonth() && d.getFullYear() === now.getFullYear();
    }
    return true;
  });
}

function renderBarChart() {
  const days = [];
  const now = new Date();
  for (let i = 6; i >= 0; i--) {
    const d = new Date(now);
    d.setDate(d.getDate() - i);
    const key = d.toDateString();
    const dayTx = transactions.filter(t => new Date(t.id).toDateString() === key);
    days.push({
      label: d.toLocaleDateString('id-ID',{weekday:'short'}),
      income: dayTx.filter(t=>t.type==='income').reduce((s,t)=>s+t.amount,0),
      expense: dayTx.filter(t=>t.type==='expense').reduce((s,t)=>s+t.amount,0)
    });
  }
  const maxVal = Math.max(...days.map(d => Math.max(d.income, d.expense)), 1);
  document.getElementById('barChart').innerHTML = days.map(d => {
    const ih = Math.round((d.income/maxVal)*90);
    const eh = Math.round((d.expense/maxVal)*90);
    return `
      <div class="bar-col">
        <div style="display:flex;gap:2px;align-items:flex-end;height:90px;">
          <div class="bar income-bar" style="height:${ih}px;width:12px;"></div>
          <div class="bar expense-bar" style="height:${eh}px;width:12px;"></div>
        </div>
        <div class="bar-label">${d.label}</div>
      </div>
    `;
  }).join('');
}

function renderCategories() {
  const filtered = getFilteredTx().filter(t => t.type === 'expense');
  const catMap = {};
  filtered.forEach(t => {
    const c = t.category || 'Lainnya';
    catMap[c] = (catMap[c] || 0) + t.amount;
  });
  const sorted = Object.entries(catMap).sort((a,b) => b[1]-a[1]).slice(0, 6);
  const maxCat = sorted[0]?.[1] || 1;
  const el = document.getElementById('categoryList');
  if (sorted.length === 0) {
    el.innerHTML = `<div class="empty-state"><div class="empty-icon">📊</div><p>Belum ada data pengeluaran.</p></div>`;
    return;
  }
  el.innerHTML = sorted.map(([name, amt]) => {
    const pct = Math.round((amt/maxCat)*100);
    const emoji = CAT_EMOJI[name] || '📦';
    return `
      <div class="cat-item">
        <div class="cat-icon-wrap" style="background:#f8717118;">${emoji}</div>
        <div class="cat-info">
          <div class="cat-name">${name}</div>
          <div class="cat-bar-bg">
            <div class="cat-bar-fill" style="width:${pct}%;background:linear-gradient(to right,#dc2626,#f87171);"></div>
          </div>
        </div>
        <div class="cat-amount">${formatRp(amt)}</div>
      </div>
    `;
  }).join('');
}

// ==================== MODAL ====================
function openModal(type) {
  currentType = type;
  setType(type);
  document.getElementById('modalOverlay').classList.add('open');
  document.getElementById('inputAmount').focus();
}

function closeModal(e) {
  if (e.target === document.getElementById('modalOverlay')) {
    document.getElementById('modalOverlay').classList.remove('open');
    resetForm();
  }
}

function setType(type) {
  currentType = type;
  document.getElementById('tabExpense').classList.toggle('active', type === 'expense');
  document.getElementById('tabIncome').classList.toggle('active', type === 'income');
}

function selectSource(el) {
  document.querySelectorAll('.source-btn').forEach(b => b.classList.remove('active'));
  el.classList.add('active');
  selectedSource = el.dataset.src;
}

function resetForm() {
  document.getElementById('inputAmount').value = '';
  document.getElementById('inputNote').value = '';
  document.getElementById('inputCategory').value = '';
  document.querySelectorAll('.source-btn').forEach(b => b.classList.remove('active'));
  selectedSource = null;
}

function saveTransaction() {
  const amount = parseFloat(document.getElementById('inputAmount').value);
  const note = document.getElementById('inputNote').value.trim();
  const category = document.getElementById('inputCategory').value.trim();

  if (!amount || amount <= 0) {
    document.getElementById('inputAmount').focus();
    document.getElementById('inputAmount').style.borderColor = 'var(--red)';
    setTimeout(() => document.getElementById('inputAmount').style.borderColor = '', 1000);
    return;
  }

  const tx = {
    id: Date.now(),
    type: currentType,
    amount,
    note: note || (currentType === 'income' ? 'Pemasukan' : 'Pengeluaran'),
    source: selectedSource || 'Lainnya',
    category: category || (currentType === 'income' ? 'Pemasukan' : 'Pengeluaran')
  };

  transactions.unshift(tx);
  localStorage.setItem('dompetku_tx', JSON.stringify(transactions));

  document.getElementById('modalOverlay').classList.remove('open');
  resetForm();
  renderAll();
}

// ==================== NAVIGATION ====================
function switchPage(page) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  document.getElementById('page-' + page).classList.add('active');
  const navEl = document.getElementById('nav-' + page);
  if (navEl) navEl.classList.add('active');
  if (page === 'laporan') renderReport();
  if (page === 'dompet') renderWalletDetail();
}

function setPeriod(p, el) {
  currentPeriod = p;
  document.querySelectorAll('.period-btn').forEach(b => b.classList.remove('active'));
  el.classList.add('active');
  renderReport();
}

// ==================== API KEY ====================
function openApiKeyModal() {
  const existing = localStorage.getItem('dompetku_apikey');
  document.getElementById('apiKeyInput').value = existing || '';
  document.getElementById('apiKeyOverlay').classList.add('open');
}

function closeApiKeyModal() {
  document.getElementById('apiKeyOverlay').classList.remove('open');
}

function saveApiKey() {
  const key = document.getElementById('apiKeyInput').value.trim();
  if (!key) {
    closeApiKeyModal();
    return;
  }
  localStorage.setItem('dompetku_apikey', key);
  closeApiKeyModal();
  updateApiKeyBanner();
}

function clearApiKey() {
  localStorage.removeItem('dompetku_apikey');
  document.getElementById('apiKeyInput').value = '';
  closeApiKeyModal();
  updateApiKeyBanner();
}

function updateApiKeyBanner() {
  const hasKey = !!localStorage.getItem('dompetku_apikey');
  document.getElementById('apiKeyBanner').style.display = hasKey ? 'none' : 'block';
}

// ==================== AI CHAT ====================
async function sendChat() {
  const apiKey = localStorage.getItem('dompetku_apikey');
  if (!apiKey) {
    openApiKeyModal();
    return;
  }

  const input = document.getElementById('chatInput');
  const msg = input.value.trim();
  if (!msg) return;
  input.value = '';

  appendMsg(msg, 'user');

  // Loading
  const loadingId = 'loading-' + Date.now();
  const loadEl = document.createElement('div');
  loadEl.className = 'msg bot';
  loadEl.id = loadingId;
  loadEl.innerHTML = '<div class="loading-dots"><div class="loading-dot"></div><div class="loading-dot"></div><div class="loading-dot"></div></div>';
  document.getElementById('chatMessages').appendChild(loadEl);
  scrollChat();

  // Build financial context
  const totalIncome = transactions.filter(t=>t.type==='income').reduce((s,t)=>s+t.amount,0);
  const totalExpense = transactions.filter(t=>t.type==='expense').reduce((s,t)=>s+t.amount,0);
  const balance = totalIncome - totalExpense;

  const catMap = {};
  transactions.filter(t=>t.type==='expense').forEach(t => {
    const c = t.category||'Lainnya';
    catMap[c] = (catMap[c]||0) + t.amount;
  });

  const recentTx = transactions.slice(0, 10).map(t =>
    `${t.type==='income'?'+':'-'}Rp${t.amount.toLocaleString('id-ID')} (${t.note}, ${t.source})`
  ).join('\n');

  const systemPrompt = `Kamu adalah asisten keuangan pribadi bernama DompetKu AI. 
Kamu berbicara dalam Bahasa Indonesia yang santai, ramah, dan informatif.
Kamu memberikan saran finansial yang praktis dan relevan.

DATA KEUANGAN USER SAAT INI:
- Total Saldo: Rp${balance.toLocaleString('id-ID')}
- Total Pemasukan: Rp${totalIncome.toLocaleString('id-ID')}
- Total Pengeluaran: Rp${totalExpense.toLocaleString('id-ID')}
- Kategori pengeluaran: ${JSON.stringify(catMap)}
- Transaksi terbaru:
${recentTx || '(Belum ada transaksi)'}

Berikan jawaban yang ringkas, pakai emoji yang relevan, dan saran yang actionable.`;

  try {
    const resp = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'x-api-key': apiKey,
        'anthropic-version': '2023-06-01',
        'anthropic-dangerous-direct-browser-access': 'true'
      },
      body: JSON.stringify({
        model: 'claude-sonnet-4-6',
        max_tokens: 1000,
        system: systemPrompt,
        messages: [{ role: 'user', content: msg }]
      })
    });
    const data = await resp.json();
    document.getElementById(loadingId)?.remove();
    if (data.error) {
      appendMsg('⚠️ Error: ' + (data.error.message || 'API Key sepertinya salah atau bermasalah. Coba cek lagi di ⚙️.'), 'bot');
      return;
    }
    const reply = data.content?.[0]?.text || 'Maaf, ada error. Coba lagi ya!';
    appendMsg(reply, 'bot');
  } catch (e) {
    document.getElementById(loadingId)?.remove();
    appendMsg('Maaf, ada gangguan koneksi. Coba lagi ya! 🙏', 'bot');
  }
}

function appendMsg(text, role) {
  const now = new Date().toLocaleTimeString('id-ID',{hour:'2-digit',minute:'2-digit'});
  const div = document.createElement('div');
  div.className = `msg ${role}`;
  div.innerHTML = text.replace(/\n/g, '<br>') + `<div class="msg-time">${now}</div>`;
  document.getElementById('chatMessages').appendChild(div);
  scrollChat();
}

function scrollChat() {
  const el = document.getElementById('chatMessages');
  el.scrollTop = el.scrollHeight;
}

// ==================== UTILS ====================
function formatRp(n) {
  const sign = n < 0 ? '-' : '';
  const abs = Math.abs(n);
  if (abs >= 1000000) return sign + 'Rp ' + (abs/1000000).toFixed(1) + 'jt';
  if (abs >= 1000) return sign + 'Rp ' + (abs/1000).toFixed(0) + 'rb';
  return sign + 'Rp ' + abs.toLocaleString('id-ID');
}

function resetAllData() {
  showConfirm('Reset Semua Data', 'Yakin mau hapus SEMUA data transaksi? Tidak bisa dibatalkan.', () => {
    transactions = [];
    localStorage.removeItem('dompetku_tx');
    renderAll();
    switchPage('home');
  });
}

function resetBalance() {
  showConfirm('Reset Saldo ke Rp 0', 'Semua riwayat transaksi akan terhapus dan tidak bisa dikembalikan.', () => {
    transactions = [];
    localStorage.removeItem('dompetku_tx');
    renderAll();
  });
}

function exportData() {
  if (transactions.length === 0) {
    showInfo('Belum Ada Data', 'Belum ada transaksi untuk di-export.');
    return;
  }
  const blob = new Blob([JSON.stringify(transactions, null, 2)], { type: 'application/json' });
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = 'dompetku-backup-' + new Date().toISOString().slice(0,10) + '.json';
  a.click();
  URL.revokeObjectURL(url);
}

// Run
init();
</script>
</body>
</html>
