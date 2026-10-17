<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Buku Kredit Usaha</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Tinos:ital,wght@0,400;0,700;1,400&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
<style>
  :root{
    --cover-green: #1F4D3D;
    --cover-green-dark: #142F26;
    --cover-green-light: #2E6B54;
    --paper: #F3EEDD;
    --paper-dark: #EAE2C8;
    --ink: #1B2A26;
    --ink-soft: #4B5A54;
    --brass: #A9812E;
    --brass-light: #C9A54A;
    --stamp-red: #A32F1F;
    --line: #CFC49E;
  }
  *{ box-sizing:border-box; }
  html,body{ margin:0; padding:0; }
  body{
    background: linear-gradient(180deg, #0F241D, #1B2A26 60%, #0F241D);
    font-family:'Inter', sans-serif;
    color: var(--ink);
    min-height:100vh;
    padding: 28px 14px 60px;
    display:flex;
    justify-content:center;
  }
  .app{ width:100%; max-width: 760px; }
  .masthead{ text-align:center; margin-bottom:18px; }
  .masthead .eyebrow{
    color: var(--brass-light);
    font-family:'JetBrains Mono', monospace;
    font-size:11px;
    letter-spacing:.28em;
    text-transform:uppercase;
    margin:0 0 6px;
  }
  .masthead h1{
    color: #F3EEDD;
    font-family:'Tinos', serif;
    font-weight:700;
    font-size: 28px;
    margin:0;
    letter-spacing:.01em;
  }
  .masthead p{ color:#9FB3AB; font-size:13px; margin:6px 0 0; }

  .passbook{
    background: var(--paper);
    border-radius: 6px;
    box-shadow: 0 30px 60px -20px rgba(0,0,0,.55), 0 2px 0 rgba(255,255,255,.03) inset;
    overflow:hidden;
    position:relative;
  }
  .cover{
    background:
      radial-gradient(circle at 85% -10%, var(--cover-green-light), transparent 55%),
      linear-gradient(160deg, var(--cover-green), var(--cover-green-dark));
    padding: 26px 26px 22px;
    color: var(--paper);
    position:relative;
    border-bottom: 6px solid var(--brass);
  }
  .cover::before{
    content:"";
    position:absolute; inset:10px;
    border: 1px solid rgba(243,238,221,.28);
    pointer-events:none;
  }
  .cover-row{
    display:flex; justify-content:space-between; align-items:flex-start;
    font-family:'JetBrains Mono', monospace;
    font-size:11px;
    letter-spacing:.14em;
    text-transform:uppercase;
    color: rgba(243,238,221,.75);
  }
  .cover-title{
    font-family:'Tinos', serif;
    font-size: 24px;
    font-weight:700;
    margin: 14px 0 4px;
    letter-spacing:.02em;
  }
  .cover-sub{
    font-size:12.5px;
    color: rgba(243,238,221,.8);
    max-width:480px;
    line-height:1.5;
  }

  .tabs{
    display:flex;
    gap:0;
    background: var(--cover-green-dark);
    padding: 0 26px;
  }
  .tab{
    flex:1;
    appearance:none;
    border:none;
    cursor:pointer;
    background: transparent;
    color: rgba(243,238,221,.55);
    font-family:'Inter', sans-serif;
    padding: 13px 8px 11px;
    text-align:center;
    border-bottom: 3px solid transparent;
    transition: color .15s ease, border-color .15s ease, background .15s ease;
  }
  .tab .t-main{ display:block; font-size:13.5px; font-weight:700; letter-spacing:.01em; }
  .tab .t-sub{ display:block; font-size:10.5px; margin-top:2px; font-family:'JetBrains Mono', monospace; letter-spacing:.05em; text-transform:uppercase; opacity:.85; }
  .tab.active{
    color: #F3EEDD;
    border-bottom-color: var(--brass);
    background: rgba(243,238,221,.05);
  }
  .tab:not(.active):hover{ color: rgba(243,238,221,.85); }

  .sheet{
    padding: 22px 26px 28px;
    background: repeating-linear-gradient(180deg, transparent, transparent 41px, var(--line) 42px);
    display:none;
  }
  .sheet.active{ display:block; }

  .sheet-label{
    font-family:'JetBrains Mono', monospace;
    font-size:10.5px;
    letter-spacing:.2em;
    text-transform:uppercase;
    color: var(--ink-soft);
    margin: 0 0 14px;
  }

  .field{ display:flex; align-items:baseline; gap:14px; padding: 9px 0; }
  .field label{ flex: 0 0 auto; font-size:13.5px; color: var(--ink-soft); font-weight:500; }
  .field .fill{ flex:1; }
  .input-wrap{
    display:flex; align-items:baseline; gap:6px;
    border-bottom: 1px dashed var(--brass);
    padding-bottom:2px;
  }
  .input-wrap .prefix{ font-family:'JetBrains Mono', monospace; font-size:14px; color: var(--ink-soft); }
  .input-wrap input{
    width:100%; border:none; background:transparent; outline:none;
    font-family:'JetBrains Mono', monospace; font-size:17px; font-weight:700;
    color: var(--ink); padding:2px 0;
  }
  .input-wrap input::placeholder{ color:#B7AF92; font-weight:400; }
  .input-wrap .suffix{ font-family:'JetBrains Mono', monospace; font-size:12.5px; color: var(--ink-soft); white-space:nowrap; }

  .rate-note{
    display:flex; justify-content:space-between; align-items:center;
    padding: 10px 12px; margin-top: 8px;
    background: rgba(169,129,46,.1);
    border: 1px solid rgba(169,129,46,.35);
    border-radius:4px;
    font-size:12.5px; color: var(--ink-soft);
  }
  .rate-note b{ color: var(--ink); font-family:'JetBrains Mono', monospace; }

  .divider{ border:none; border-top: 1px solid var(--line); margin: 20px 0 6px; }

  .ledger{ margin-top:6px; }
  .ledger-row{ display:flex; justify-content:space-between; gap:10px; padding: 9px 0; }
  .ledger-row .k{ font-size:13.5px; color: var(--ink-soft); }
  .ledger-row .v{
    font-family:'JetBrains Mono', monospace; font-weight:600; font-size:14.5px;
    color: var(--ink); text-align:right; white-space:nowrap;
  }
  .ledger-row.minus .v{ color: var(--stamp-red); }
  .ledger-row.total{ border-top: 2px solid var(--ink); margin-top: 6px; padding-top: 12px; }
  .ledger-row.total .k, .ledger-row.total .v{ font-size:16px; font-weight:700; }

  .result-wrap{
    position:relative; margin-top: 22px; padding: 18px 18px 20px;
    background: #fff; border: 1px solid var(--line); border-radius: 6px;
    box-shadow: 0 1px 0 rgba(0,0,0,.03) inset;
  }
  .result-label{
    font-family:'JetBrains Mono', monospace; font-size:10.5px; letter-spacing:.2em;
    text-transform:uppercase; color: var(--ink-soft); margin:0 0 4px;
  }
  .result-amount{
    font-family:'Tinos', serif; font-weight:700; font-size: 34px;
    color: var(--cover-green-dark); margin:0; line-height:1.15;
  }
  .result-amount small{
    font-family:'JetBrains Mono', monospace; font-size:15px; font-weight:500; color: var(--ink-soft);
  }
  .result-foot{ font-size:12px; color: var(--ink-soft); margin-top:8px; }

  .stamp{
    position:absolute; top: -14px; right: 16px; width: 96px; height:96px; border-radius:50%;
    border: 3px solid var(--stamp-red); color: var(--stamp-red);
    display:flex; align-items:center; justify-content:center; text-align:center;
    font-family:'JetBrains Mono', monospace; font-size:10px; font-weight:700;
    letter-spacing:.06em; text-transform:uppercase; line-height:1.25;
    transform: rotate(-11deg); opacity: 0; transition: opacity .25s ease, transform .25s ease;
    background: rgba(163,47,31,.03); mix-blend-mode: multiply;
  }
  .stamp::before{ content:""; position:absolute; inset:6px; border: 1px solid var(--stamp-red); border-radius:50%; }
  .stamp.show{ opacity:.88; transform: rotate(-11deg) scale(1); }

  .footnote{ font-size:11.5px; color: var(--ink-soft); text-align:center; margin: 16px 4px 0; line-height:1.6; }

  @media (max-width: 480px){
    .cover-title{ font-size:20px; }
    .result-amount{ font-size:26px; }
    .stamp{ width:78px; height:78px; font-size:9px; top:-10px; right:10px; }
    .field{ flex-direction:column; align-items:flex-start; gap:4px; }
    .tab .t-main{ font-size:12px; }
    .tab .t-sub{ font-size:9.5px; }
  }
</style>
</head>
<body>
<div class="app">

  <div class="masthead">
    <p class="eyebrow">Simulasi &mdash; bukan penawaran resmi</p>
    <h1>Kalkulator Kredit Usaha</h1>
    <p id="subheadline">Pinjaman mingguan · admin dipotong di depan · sekali bayar</p>
  </div>

  <div class="passbook">
    <div class="cover">
      <div class="cover-row">
        <span>Buku Pinjaman</span>
        <span id="todayLabel">--</span>
      </div>
      <div class="cover-title" id="coverTitle">Pinjaman Pintar</div>
      <div class="cover-sub" id="coverSub">Isi jumlah pinjaman dan jangka waktu di bawah. Potongan admin dihitung otomatis dan langsung dipotong dari dana yang cair.</div>
    </div>

    <div class="tabs">
      <button class="tab active" data-product="pintar" type="button">
        <span class="t-main">Pinjaman Pintar</span>
        <span class="t-sub">Mingguan</span>
      </button>
      <button class="tab" data-product="praktis" type="button">
        <span class="t-main">Pinjaman Praktis</span>
        <span class="t-sub">Bulanan · Anuitas</span>
      </button>
      <button class="tab" data-product="mc7" type="button">
        <span class="t-main">Praktis MC7</span>
        <span class="t-sub">Bulanan · 12% Flat</span>
      </button>
    </div>

    <!-- ===== PANEL PINTAR ===== -->
    <div class="sheet active" id="panel-pintar">
      <p class="sheet-label">Data Pinjaman</p>

      <div class="field">
        <label for="p_pokok">Jumlah Pinjaman</label>
        <div class="fill">
          <div class="input-wrap">
            <span class="prefix">Rp</span>
            <input id="p_pokok" type="text" inputmode="numeric" placeholder="0" value="5.000.000">
          </div>
        </div>
      </div>

      <div class="field">
        <label for="p_minggu">Jangka Waktu</label>
        <div class="fill">
          <div class="input-wrap">
            <input id="p_minggu" type="text" inputmode="numeric" placeholder="0" value="10">
            <span class="suffix">minggu</span>
          </div>
        </div>
      </div>

      <div class="rate-note">
        <span>Tarif admin tetap</span>
        <b>0,37% / minggu</b>
      </div>

      <hr class="divider">
      <p class="sheet-label">Rincian Potongan</p>

      <div class="ledger">
        <div class="ledger-row">
          <span class="k">Jumlah Pinjaman</span>
          <span class="v" id="p_outPokok">Rp 0</span>
        </div>
        <div class="ledger-row">
          <span class="k">Jangka Waktu</span>
          <span class="v" id="p_outMinggu">0 minggu</span>
        </div>
        <div class="ledger-row minus">
          <span class="k">Total Admin (0,37% × <span id="p_outMingguInline">0</span> minggu)</span>
          <span class="v" id="p_outAdminPersen">− 0,00%</span>
        </div>
        <div class="ledger-row minus">
          <span class="k">Potongan Admin</span>
          <span class="v" id="p_outAdminRp">− Rp 0</span>
        </div>
        <div class="ledger-row total">
          <span class="k">Dana Diterima (Pencairan)</span>
          <span class="v" id="p_outCair">Rp 0</span>
        </div>
      </div>

      <div class="result-wrap">
        <div class="stamp" id="p_stamp">Disetujui<br>Sekali Bayar</div>
        <p class="result-label">Total Wajib Dibayar (sekali bayar di akhir)</p>
        <p class="result-amount"><span id="p_outBayar">Rp 0</span> <small id="p_outBayarNote"></small></p>
        <p class="result-foot" id="p_outJatuhTempo">Jatuh tempo: —</p>
      </div>

      <p class="footnote">Admin dipotong satu kali di depan saat pencairan, bukan per minggu.<br>Nasabah membayar kembali pokok pinjaman secara penuh dalam satu kali pembayaran pada minggu jatuh tempo.</p>
    </div>

    <!-- ===== PANEL PRAKTIS ===== -->
    <div class="sheet" id="panel-praktis">
      <p class="sheet-label">Data Pinjaman</p>

      <div class="field">
        <label for="k_pokok">Jumlah Pinjaman</label>
        <div class="fill">
          <div class="input-wrap">
            <span class="prefix">Rp</span>
            <input id="k_pokok" type="text" inputmode="numeric" placeholder="0" value="5.000.000">
          </div>
        </div>
      </div>

      <div class="field">
        <label for="k_tenor">Tenor</label>
        <div class="fill">
          <div class="input-wrap">
            <input id="k_tenor" type="text" inputmode="numeric" placeholder="0" value="12">
            <span class="suffix">bulan</span>
          </div>
        </div>
      </div>

      <div class="rate-note">
        <span>Suku bunga anuitas tetap</span>
        <b>18,5% / tahun</b>
      </div>

      <hr class="divider">
      <p class="sheet-label">Rincian Angsuran</p>

      <div class="ledger">
        <div class="ledger-row">
          <span class="k">Jumlah Pinjaman (Pokok)</span>
          <span class="v" id="k_outPokok">Rp 0</span>
        </div>
        <div class="ledger-row">
          <span class="k">Tenor</span>
          <span class="v" id="k_outTenor">0 bulan</span>
        </div>
        <div class="ledger-row">
          <span class="k">Suku Bunga Anuitas</span>
          <span class="v">18,5% / tahun</span>
        </div>
        <div class="ledger-row minus">
          <span class="k">Total Bunga Selama Tenor</span>
          <span class="v" id="k_outBunga">− Rp 0</span>
        </div>
        <div class="ledger-row total">
          <span class="k">Total Pembayaran</span>
          <span class="v" id="k_outTotalBayar">Rp 0</span>
        </div>
      </div>

      <div class="result-wrap">
        <div class="stamp" id="k_stamp">Disetujui<br>Angsuran Bulanan</div>
        <p class="result-label">Angsuran per Bulan</p>
        <p class="result-amount"><span id="k_outAngsuran">Rp 0</span> <small id="k_outAngsuranNote"></small></p>
        <p class="result-foot" id="k_outJatuhTempo">Lunas pada: —</p>
      </div>

      <p class="footnote">Angsuran dihitung dengan metode anuitas, jumlah angsuran tetap setiap bulan namun komposisi pokok dan bunga di dalamnya berubah seiring waktu.<br>Dana cair penuh sesuai jumlah pinjaman, tanpa potongan admin di depan.</p>
    </div>

    <!-- ===== PANEL PRAKTIS MC7 ===== -->
    <div class="sheet" id="panel-mc7">
      <p class="sheet-label">Data Pinjaman</p>

      <div class="field">
        <label for="m_pokok">Jumlah Pinjaman</label>
        <div class="fill">
          <div class="input-wrap">
            <span class="prefix">Rp</span>
            <input id="m_pokok" type="text" inputmode="numeric" placeholder="0" value="5.000.000">
          </div>
        </div>
      </div>

      <div class="field">
        <label for="m_tenor">Tenor</label>
        <div class="fill">
          <div class="input-wrap">
            <input id="m_tenor" type="text" inputmode="numeric" placeholder="0" value="12">
            <span class="suffix">bulan</span>
          </div>
        </div>
      </div>

      <div class="rate-note">
        <span>Suku bunga flat tetap</span>
        <b>12,0% / tahun (1,0% / bulan)</b>
      </div>

      <hr class="divider">
      <p class="sheet-label">Rincian Angsuran</p>

      <div class="ledger">
        <div class="ledger-row">
          <span class="k">Jumlah Pinjaman (Pokok)</span>
          <span class="v" id="m_outPokok">Rp 0</span>
        </div>
        <div class="ledger-row">
          <span class="k">Tenor</span>
          <span class="v" id="m_outTenor">0 bulan</span>
        </div>
        <div class="ledger-row">
          <span class="k">Suku Bunga Flat</span>
          <span class="v">12,0% / tahun</span>
        </div>
        <div class="ledger-row minus">
          <span class="k">Total Bunga Selama Tenor</span>
          <span class="v" id="m_outBunga">− Rp 0</span>
        </div>
        <div class="ledger-row total">
          <span class="k">Total Pembayaran</span>
          <span class="v" id="m_outTotalBayar">Rp 0</span>
        </div>
      </div>

      <div class="result-wrap">
        <div class="stamp" id="m_stamp">Disetujui<br>Angsuran MC7</div>
        <p class="result-label">Angsuran per Bulan</p>
        <p class="result-amount"><span id="m_outAngsuran">Rp 0</span> <small id="m_outAngsuranNote"></small></p>
        <p class="result-foot" id="m_outJatuhTempo">Lunas pada: —</p>
      </div>

      <p class="footnote">Pinjaman Praktis MC7 menggunakan suku bunga flat 12% per tahun (1% per bulan).<br>Pokok dan bunga dibagi rata setiap bulan tanpa biaya admin tambahan di depan.</p>
    </div>

  </div>
</div>

<script>
  const ADMIN_RATE_PER_WEEK = 0.37; // percent, for Pintar
  const ANNUITY_RATE_PER_YEAR = 18.5; // percent, for Praktis
  const MC7_FLAT_RATE_PER_YEAR = 12.0; // percent flat, for MC7

  function parseNumber(str){
    if(!str) return 0;
    const cleaned = String(str).replace(/[^\d]/g, '');
    return cleaned ? parseInt(cleaned, 10) : 0;
  }
  function formatRupiah(n){
    n = Math.round(n);
    return 'Rp ' + n.toLocaleString('id-ID');
  }
  function formatNumberID(n){ return n.toLocaleString('id-ID'); }
  function formatInputThousands(el){
    const raw = parseNumber(el.value);
    el.value = raw ? formatNumberID(raw) : '';
  }
  function todayLabel(){
    const d = new Date();
    return d.toLocaleDateString('id-ID', { day:'2-digit', month:'short', year:'numeric' });
  }
  function addDays(days){
    const d = new Date();
    d.setDate(d.getDate() + days);
    return d;
  }
  function addMonths(months){
    const d = new Date();
    d.setMonth(d.getMonth() + months);
    return d;
  }
  function longDate(d){
    return d.toLocaleDateString('id-ID', { day:'2-digit', month:'long', year:'numeric' });
  }

  // ---------- PINTAR (weekly) ----------
  const p_pokokEl = document.getElementById('p_pokok');
  const p_mingguEl = document.getElementById('p_minggu');

  function recalcPintar(){
    const pokok = parseNumber(p_pokokEl.value);
    const minggu = Math.max(0, parseNumber(p_mingguEl.value));

    const adminPersenTotal = ADMIN_RATE_PER_WEEK * minggu;
    const adminRp = pokok * (adminPersenTotal / 100);
    const cair = Math.max(0, pokok - adminRp);
    const totalBayar = pokok;

    document.getElementById('p_outPokok').textContent = formatRupiah(pokok);
    document.getElementById('p_outMinggu').textContent = minggu + ' minggu';
    document.getElementById('p_outMingguInline').textContent = minggu;
    document.getElementById('p_outAdminPersen').textContent = '− ' + adminPersenTotal.toFixed(2).replace('.', ',') + '%';
    document.getElementById('p_outAdminRp').textContent = '− ' + formatRupiah(adminRp);
    document.getElementById('p_outCair').textContent = formatRupiah(cair);
    document.getElementById('p_outBayar').textContent = formatRupiah(totalBayar);
    document.getElementById('p_outBayarNote').textContent = minggu ? ('pada minggu ke-' + minggu) : '';

    const stamp = document.getElementById('p_stamp');
    if(pokok > 0 && minggu > 0){
      document.getElementById('p_outJatuhTempo').textContent = 'Jatuh tempo: ' + longDate(addDays(minggu * 7));
      stamp.classList.add('show');
    } else {
      document.getElementById('p_outJatuhTempo').textContent = 'Jatuh tempo: —';
      stamp.classList.remove('show');
    }
  }

  p_pokokEl.addEventListener('input', () => { formatInputThousands(p_pokokEl); recalcPintar(); });
  p_mingguEl.addEventListener('input', () => { p_mingguEl.value = p_mingguEl.value.replace(/[^\d]/g,''); recalcPintar(); });

  // ---------- PRAKTIS (monthly annuity) ----------
  const k_pokokEl = document.getElementById('k_pokok');
  const k_tenorEl = document.getElementById('k_tenor');

  function recalcPraktis(){
    const pokok = parseNumber(k_pokokEl.value);
    const tenor = Math.max(0, parseNumber(k_tenorEl.value));
    const iBulan = (ANNUITY_RATE_PER_YEAR / 100) / 12;

    let angsuran = 0;
    if(pokok > 0 && tenor > 0){
      angsuran = (pokok * iBulan) / (1 - Math.pow(1 + iBulan, -tenor));
    }
    const totalBayar = angsuran * tenor;
    const totalBunga = Math.max(0, totalBayar - pokok);

    document.getElementById('k_outPokok').textContent = formatRupiah(pokok);
    document.getElementById('k_outTenor').textContent = tenor + ' bulan';
    document.getElementById('k_outBunga').textContent = '− ' + formatRupiah(totalBunga);
    document.getElementById('k_outTotalBayar').textContent = formatRupiah(totalBayar);
    document.getElementById('k_outAngsuran').textContent = formatRupiah(angsuran);
    document.getElementById('k_outAngsuranNote').textContent = tenor ? ('/ bulan × ' + tenor + ' bulan') : '';

    const stamp = document.getElementById('k_stamp');
    if(pokok > 0 && tenor > 0){
      document.getElementById('k_outJatuhTempo').textContent = 'Lunas pada: ' + longDate(addMonths(tenor));
      stamp.classList.add('show');
    } else {
      document.getElementById('k_outJatuhTempo').textContent = 'Lunas pada: —';
      stamp.classList.remove('show');
    }
  }

  k_pokokEl.addEventListener('input', () => { formatInputThousands(k_pokokEl); recalcPraktis(); });
  k_tenorEl.addEventListener('input', () => { k_tenorEl.value = k_tenorEl.value.replace(/[^\d]/g,''); recalcPraktis(); });

  // ---------- PRAKTIS MC7 (12% Flat) ----------
  const m_pokokEl = document.getElementById('m_pokok');
  const m_tenorEl = document.getElementById('m_tenor');

  function recalcMC7(){
    const pokok = parseNumber(m_pokokEl.value);
    const tenor = Math.max(0, parseNumber(m_tenorEl.value));
    
    // Flat calculation: Total Bunga = Pokok * (Rate / 12) * Tenor
    const totalBunga = pokok * ((MC7_FLAT_RATE_PER_YEAR / 100) / 12) * tenor;
    const totalBayar = pokok + totalBunga;
    const angsuran = tenor > 0 ? (totalBayar / tenor) : 0;

    document.getElementById('m_outPokok').textContent = formatRupiah(pokok);
    document.getElementById('m_outTenor').textContent = tenor + ' bulan';
    document.getElementById('m_outBunga').textContent = '− ' + formatRupiah(totalBunga);
    document.getElementById('m_outTotalBayar').textContent = formatRupiah(totalBayar);
    document.getElementById('m_outAngsuran').textContent = formatRupiah(angsuran);
    document.getElementById('m_outAngsuranNote').textContent = tenor ? ('/ bulan × ' + tenor + ' bulan') : '';

    const stamp = document.getElementById('m_stamp');
    if(pokok > 0 && tenor > 0){
      document.getElementById('m_outJatuhTempo').textContent = 'Lunas pada: ' + longDate(addMonths(tenor));
      stamp.classList.add('show');
    } else {
      document.getElementById('m_outJatuhTempo').textContent = 'Lunas pada: —';
      stamp.classList.remove('show');
    }
  }

  m_pokokEl.addEventListener('input', () => { formatInputThousands(m_pokokEl); recalcMC7(); });
  m_tenorEl.addEventListener('input', () => { m_tenorEl.value = m_tenorEl.value.replace(/[^\d]/g,''); recalcMC7(); });

  // ---------- TABS ----------
  const tabs = document.querySelectorAll('.tab');
  const panels = {
    pintar: document.getElementById('panel-pintar'),
    praktis: document.getElementById('panel-praktis'),
    mc7: document.getElementById('panel-mc7')
  };
  const meta = {
    pintar: {
      title: 'Pinjaman Pintar',
      sub: 'Isi jumlah pinjaman dan jangka waktu di bawah. Potongan admin dihitung otomatis dan langsung dipotong dari dana yang cair.',
      headline: 'Pinjaman mingguan · admin dipotong di depan · sekali bayar'
    },
    praktis: {
      title: 'Pinjaman Praktis',
      sub: 'Isi jumlah pinjaman dan tenor di bawah. Angsuran bulanan dihitung otomatis dengan metode anuitas.',
      headline: 'Pinjaman bulanan · bunga anuitas 18,5%/tahun · angsuran tetap'
    },
    mc7: {
      title: 'Pinjaman Praktis MC7',
      sub: 'Isi jumlah pinjaman dan tenor di bawah. Angsuran bulanan dihitung dengan suku bunga flat 12% per tahun (1% per bulan).',
      headline: 'Pinjaman bulanan · bunga flat 12,0%/tahun · angsuran ringan'
    }
  };

  tabs.forEach(tab => {
    tab.addEventListener('click', () => {
      const product = tab.dataset.product;
      tabs.forEach(t => t.classList.toggle('active', t === tab));
      Object.keys(panels).forEach(key => panels[key].classList.toggle('active', key === product));
      document.getElementById('coverTitle').textContent = meta[product].title;
      document.getElementById('coverSub').textContent = meta[product].sub;
      document.getElementById('subheadline').textContent = meta[product].headline;
    });
  });

  // ---------- INIT ----------
  document.getElementById('todayLabel').textContent = todayLabel();
  formatInputThousands(p_pokokEl);
  formatInputThousands(k_pokokEl);
  formatInputThousands(m_pokokEl);
  recalcPintar();
  recalcPraktis();
  recalcMC7();
</script>
</body>
</html>
