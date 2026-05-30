# mohamedlotfy95.github.io

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Monthly Financial Entry — Thndr Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Sora:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0e0f11;
    --surface: #16181c;
    --surface2: #1e2026;
    --border: rgba(255,255,255,0.07);
    --border-hover: rgba(255,255,255,0.14);
    --text: #f0efe8;
    --muted: #7a7a72;
    --hint: #4a4a44;
    --green: #1fc67a;
    --green-dim: rgba(31,198,122,0.12);
    --amber: #f5a623;
    --amber-dim: rgba(245,166,35,0.12);
    --red: #f05252;
    --red-dim: rgba(240,82,82,0.12);
    --blue: #4f8ef7;
    --blue-dim: rgba(79,142,247,0.1);
    --radius: 12px;
    --radius-sm: 8px;
  }

  body {
    font-family: 'Sora', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    padding: 2rem 1.5rem 4rem;
    font-size: 14px;
    line-height: 1.6;
  }

  .page { max-width: 780px; margin: 0 auto; }

  /* Header */
  .header {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    margin-bottom: 2rem;
    padding-bottom: 1.5rem;
    border-bottom: 0.5px solid var(--border);
  }
  .header h1 {
    font-size: 22px;
    font-weight: 600;
    letter-spacing: -0.4px;
    margin-bottom: 4px;
  }
  .header p { font-size: 13px; color: var(--muted); }
  .month-badge {
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    background: var(--surface2);
    border: 0.5px solid var(--border-hover);
    border-radius: 20px;
    padding: 6px 14px;
    color: var(--text);
    white-space: nowrap;
  }

  /* KPI row */
  .kpi-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    margin-bottom: 1.5rem;
  }
  .kpi {
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: var(--radius);
    padding: 14px 16px;
    transition: border-color .2s;
  }
  .kpi:hover { border-color: var(--border-hover); }
  .kpi-label {
    font-size: 11px;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: .06em;
    margin-bottom: 6px;
  }
  .kpi-value {
    font-family: 'DM Mono', monospace;
    font-size: 18px;
    font-weight: 500;
    color: var(--text);
    transition: color .3s;
  }
  .kpi-sub { font-size: 11px; color: var(--hint); margin-top: 3px; }
  .pos { color: var(--green) !important; }
  .neg { color: var(--red) !important; }
  .neu { color: var(--muted) !important; }

  /* Cards */
  .card {
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: var(--radius);
    padding: 1.25rem;
    margin-bottom: 10px;
    transition: border-color .2s;
  }
  .card:hover { border-color: var(--border-hover); }
  .card-hdr {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 14px;
  }
  .card-title {
    font-size: 13px;
    font-weight: 500;
    display: flex;
    align-items: center;
    gap: 8px;
    color: var(--text);
  }
  .card-icon {
    width: 28px; height: 28px;
    background: var(--surface2);
    border-radius: 7px;
    display: flex; align-items: center; justify-content: center;
    font-size: 14px;
  }

  /* Add button */
  .add-btn {
    font-family: 'Sora', sans-serif;
    font-size: 12px;
    color: var(--muted);
    background: var(--surface2);
    border: 0.5px solid var(--border-hover);
    border-radius: 20px;
    padding: 5px 12px;
    cursor: pointer;
    display: flex; align-items: center; gap: 5px;
    transition: all .15s;
  }
  .add-btn:hover { color: var(--text); border-color: rgba(255,255,255,0.2); }

  /* Form grid */
  .row3 { display: grid; grid-template-columns: 1.4fr 1fr 1fr; gap: 8px; margin-bottom: 8px; align-items: end; }
  .row2 { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 10px; }
  .field { display: flex; flex-direction: column; gap: 5px; }
  .field label { font-size: 11px; color: var(--muted); text-transform: uppercase; letter-spacing: .05em; }

  input[type=text], input[type=number], select {
    font-family: 'Sora', sans-serif;
    font-size: 13px;
    background: var(--surface2);
    border: 0.5px solid var(--border);
    border-radius: var(--radius-sm);
    color: var(--text);
    padding: 8px 10px;
    width: 100%;
    outline: none;
    transition: border-color .15s;
    -webkit-appearance: none;
    appearance: none;
  }
  input[type=text]:focus, input[type=number]:focus, select:focus {
    border-color: var(--blue);
  }
  input::placeholder { color: var(--hint); }
  select option { background: #1e2026; }

  /* Divider row */
  .entry-divider {
    height: 0.5px;
    background: var(--border);
    margin: 6px 0 10px;
  }

  /* Progress bar */
  .bar-wrap { margin-top: 12px; }
  .bar-meta { display: flex; justify-content: space-between; font-size: 11px; color: var(--hint); margin-bottom: 5px; }
  .bar-bg { height: 5px; background: var(--surface2); border-radius: 3px; overflow: hidden; }
  .bar-fill { height: 100%; border-radius: 3px; transition: width .4s, background .3s; }

  /* Split card row */
  .split { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 10px; }
  .split .card { margin-bottom: 0; }

  /* Tag */
  .tag {
    font-size: 10px;
    font-weight: 500;
    padding: 2px 8px;
    border-radius: 20px;
    letter-spacing: .04em;
  }
  .tag-blue { background: var(--blue-dim); color: var(--blue); }
  .tag-green { background: var(--green-dim); color: var(--green); }
  .tag-amber { background: var(--amber-dim); color: var(--amber); }
  .tag-red { background: var(--red-dim); color: var(--red); }

  /* Note */
  .note {
    font-size: 11px;
    color: var(--hint);
    display: flex;
    align-items: flex-start;
    gap: 5px;
    margin-top: 8px;
    line-height: 1.5;
  }

  /* Freedom card */
  .freedom-card {
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: var(--radius);
    padding: 1.25rem;
    margin-bottom: 10px;
  }
  .freedom-hdr {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 14px;
  }
  .freedom-title { font-size: 13px; font-weight: 500; margin-bottom: 3px; }
  .freedom-sub { font-size: 11px; color: var(--muted); }
  .freedom-pct {
    font-family: 'DM Mono', monospace;
    font-size: 28px;
    font-weight: 500;
    color: var(--muted);
    transition: color .3s;
  }
  .freedom-bar-bg {
    height: 8px;
    background: var(--surface2);
    border-radius: 4px;
    overflow: hidden;
    margin-bottom: 8px;
  }
  .freedom-bar-fill {
    height: 100%;
    border-radius: 4px;
    background: var(--green);
    transition: width .5s, background .3s;
  }
  .freedom-stats {
    display: flex;
    justify-content: space-between;
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--hint);
    margin-bottom: 10px;
  }
  .freedom-msg {
    font-size: 12px;
    color: var(--muted);
    padding: 10px 12px;
    background: var(--surface2);
    border-radius: var(--radius-sm);
    border-left: 2px solid var(--green);
    line-height: 1.6;
  }

  /* Summary bar */
  .summary-bar {
    background: var(--surface2);
    border: 0.5px solid var(--border-hover);
    border-radius: var(--radius);
    padding: 1rem 1.25rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 12px;
  }
  .summary-nw { font-family: 'DM Mono', monospace; font-size: 22px; font-weight: 500; }
  .summary-label { font-size: 11px; color: var(--muted); margin-bottom: 4px; }

  /* Save button */
  .save-btn {
    font-family: 'Sora', sans-serif;
    font-size: 14px;
    font-weight: 500;
    width: 100%;
    padding: 13px;
    border-radius: var(--radius);
    border: 0.5px solid rgba(255,255,255,0.15);
    background: rgba(255,255,255,0.04);
    color: var(--text);
    cursor: pointer;
    transition: all .15s;
    letter-spacing: .01em;
  }
  .save-btn:hover { background: rgba(255,255,255,0.08); border-color: rgba(255,255,255,0.22); }
  .save-btn:active { transform: scale(0.99); }

  /* Confirmation toast */
  .toast {
    position: fixed;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%) translateY(80px);
    background: var(--surface2);
    border: 0.5px solid var(--green);
    color: var(--green);
    font-size: 13px;
    padding: 10px 20px;
    border-radius: 20px;
    transition: transform .3s ease;
    z-index: 999;
    white-space: nowrap;
  }
  .toast.show { transform: translateX(-50%) translateY(0); }

  /* Section separator */
  .sep {
    font-size: 10px;
    text-transform: uppercase;
    letter-spacing: .1em;
    color: var(--hint);
    margin: 1.5rem 0 .75rem;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .sep::after { content:''; flex:1; height:0.5px; background:var(--border); }

  @media (max-width: 600px) {
    .kpi-row { grid-template-columns: 1fr 1fr; }
    .row3 { grid-template-columns: 1fr; }
    .split { grid-template-columns: 1fr; }
    .row2 { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>
<div class="page">

  <div class="header">
    <div>
      <h1>Monthly entry</h1>
      <p>One page. Fill once a month. Everything auto-calculates.</p>
    </div>
    <div class="month-badge" id="month-badge">— 2026</div>
  </div>

  <div class="kpi-row">
    <div class="kpi">
      <div class="kpi-label">Total income</div>
      <div class="kpi-value" id="k-inc">EGP 0</div>
      <div class="kpi-sub" id="k-inc-sub">0 sources</div>
    </div>
    <div class="kpi">
      <div class="kpi-label">Total expenses</div>
      <div class="kpi-value" id="k-exp">EGP 0</div>
      <div class="kpi-sub" id="k-exp-sub">0 items</div>
    </div>
    <div class="kpi">
      <div class="kpi-label">Net cash flow</div>
      <div class="kpi-value neu" id="k-ncf">EGP 0</div>
      <div class="kpi-sub" id="k-sav">Savings rate: 0%</div>
    </div>
    <div class="kpi">
      <div class="kpi-label">Net worth</div>
      <div class="kpi-value neu" id="k-nw">EGP 0</div>
      <div class="kpi-sub" id="k-status-wrap"><span class="tag tag-amber">enter data</span></div>
    </div>
  </div>

  <div class="sep">Income</div>

  <div class="card">
    <div class="card-hdr">
      <div class="card-title">
        <div class="card-icon">↑</div>
        Income sources
      </div>
      <button class="add-btn" onclick="addRow('income-rows','income')">+ Add source</button>
    </div>
    <div id="income-rows">
      <div class="row3">
        <div class="field"><label>Source</label><input type="text" value="Monthly salary" oninput="recalc()"></div>
        <div class="field"><label>Type</label>
          <select onchange="recalc()">
            <option>Salary</option><option>Freelance</option><option>Dividend</option><option>Rental</option><option>Interest</option><option>Other</option>
          </select>
        </div>
        <div class="field"><label>Amount (EGP)</label><input type="number" placeholder="0" oninput="recalc()"></div>
      </div>
    </div>
  </div>

  <div class="sep">Expenses</div>

  <div class="card">
    <div class="card-hdr">
      <div class="card-title">
        <div class="card-icon">↓</div>
        Expenses
      </div>
      <button class="add-btn" onclick="addRow('expense-rows','expense')">+ Add expense</button>
    </div>
    <div id="expense-rows">
      <div class="row3">
        <div class="field"><label>Item</label><input type="text" placeholder="e.g. Rent" oninput="recalc()"></div>
        <div class="field"><label>Category</label>
          <select onchange="recalc()">
            <option>Housing</option><option>Food</option><option>Transport</option><option>Utilities</option><option>Subscriptions</option><option>Healthcare</option><option>Education</option><option>Entertainment</option><option>Other</option>
          </select>
        </div>
        <div class="field"><label>Amount (EGP)</label><input type="number" placeholder="0" oninput="recalc()"></div>
      </div>
    </div>
    <div class="bar-wrap">
      <div class="bar-meta"><span>Expense ratio</span><span id="ratio-lbl">0% of income</span></div>
      <div class="bar-bg"><div class="bar-fill" id="ratio-bar" style="width:0%;background:var(--green)"></div></div>
    </div>
  </div>

  <div class="sep">Balance sheet</div>

  <div class="split">
    <div class="card">
      <div class="card-hdr">
        <div class="card-title"><div class="card-icon">▲</div> Assets</div>
        <span class="tag tag-blue">auto-synced</span>
      </div>
      <div class="field" style="margin-bottom:8px">
        <label>Total invested capital (EGP)</label>
        <input type="number" placeholder="from Asset Inventory rollup" id="a-capital" oninput="recalc()">
      </div>
      <div class="field" style="margin-bottom:8px">
        <label>Passive income this month (EGP)</label>
        <input type="number" placeholder="dividends + interest" id="a-passive" oninput="recalc()">
      </div>
      <div class="field">
        <label>New investment this month (EGP)</label>
        <input type="number" placeholder="e.g. 450" id="a-new" oninput="recalc()">
      </div>
      <p class="note">ℹ Copy Total Invested Capital from your Asset Inventory rollup in Notion</p>
    </div>
    <div class="card">
      <div class="card-hdr">
        <div class="card-title"><div class="card-icon">▼</div> Liabilities</div>
      </div>
      <div class="field" style="margin-bottom:8px">
        <label>Total outstanding balance (EGP)</label>
        <input type="number" placeholder="sum of all debts" id="l-balance" oninput="recalc()">
      </div>
      <div class="field" style="margin-bottom:8px">
        <label>Monthly debt payments (EGP)</label>
        <input type="number" placeholder="e.g. 1,500" id="l-payment" oninput="recalc()">
      </div>
      <div class="field">
        <label>Interest paid this month (EGP)</label>
        <input type="number" placeholder="e.g. 200" id="l-interest" oninput="recalc()">
      </div>
      <p class="note">ℹ Update balance after each monthly payment</p>
    </div>
  </div>

  <div class="sep">Financial freedom</div>

  <div class="freedom-card">
    <div class="freedom-hdr">
      <div>
        <div class="freedom-title">Financial freedom progress</div>
        <div class="freedom-sub">Passive income ÷ monthly expenses — target: 100%</div>
      </div>
      <div class="freedom-pct" id="freedom-pct">0%</div>
    </div>
    <div class="freedom-bar-bg">
      <div class="freedom-bar-fill" id="freedom-bar" style="width:0%"></div>
    </div>
    <div class="freedom-stats">
      <span id="freedom-passive">Passive: EGP 0 / mo</span>
      <span id="freedom-gap">Gap: EGP 0 / mo</span>
      <span id="freedom-target">Target: EGP 0 / mo</span>
    </div>
    <div class="freedom-msg" id="freedom-msg">Enter your passive income and monthly expenses above to see your RDPD freedom progress.</div>
  </div>

  <div class="sep">Summary</div>

  <div class="summary-bar">
    <div>
      <div class="summary-label">Net worth this month</div>
      <div class="summary-nw neu" id="summary-nw">EGP 0</div>
    </div>
    <div style="text-align:right">
      <div class="summary-label">Status</div>
      <div id="summary-status"><span class="tag tag-amber">enter data</span></div>
    </div>
  </div>

  <button class="save-btn" onclick="copySnapshot()">
    Copy snapshot to clipboard — paste into Notion Monthly Snapshot ↗
  </button>

</div>

<div class="toast" id="toast">✓ Snapshot copied — paste into Notion</div>

<script>
  const MONTHS = ['January','February','March','April','May','June','July','August','September','October','November','December'];
  const now = new Date();
  document.getElementById('month-badge').textContent = MONTHS[now.getMonth()] + ' ' + now.getFullYear();

  function fmt(v){ return 'EGP ' + Math.round(v).toLocaleString('en-EG'); }

  function addRow(containerId, type){
    const c = document.getElementById(containerId);
    const d = document.createElement('div');
    d.className = 'row3';
    if(type === 'income'){
      d.innerHTML = `<div class="entry-divider" style="grid-column:1/-1"></div>
        <div class="field"><label>Source</label><input type="text" placeholder="e.g. Freelance" oninput="recalc()"></div>
        <div class="field"><label>Type</label><select onchange="recalc()"><option>Salary</option><option>Freelance</option><option>Dividend</option><option>Rental</option><option>Interest</option><option>Other</option></select></div>
        <div class="field"><label>Amount (EGP)</label><input type="number" placeholder="0" oninput="recalc()"></div>`;
    } else {
      d.innerHTML = `<div class="entry-divider" style="grid-column:1/-1"></div>
        <div class="field"><label>Item</label><input type="text" placeholder="e.g. Food" oninput="recalc()"></div>
        <div class="field"><label>Category</label><select onchange="recalc()"><option>Housing</option><option>Food</option><option>Transport</option><option>Utilities</option><option>Subscriptions</option><option>Healthcare</option><option>Education</option><option>Entertainment</option><option>Other</option></select></div>
        <div class="field"><label>Amount (EGP)</label><input type="number" placeholder="0" oninput="recalc()"></div>`;
    }
    c.appendChild(d);
  }

  function recalc(){
    let inc = 0, exp = 0, incCount = 0, expCount = 0;
    document.querySelectorAll('#income-rows input[type=number]').forEach(i => { const v = parseFloat(i.value)||0; inc += v; if(v>0) incCount++; });
    document.querySelectorAll('#expense-rows input[type=number]').forEach(i => { const v = parseFloat(i.value)||0; exp += v; if(v>0) expCount++; });

    const passive  = parseFloat(document.getElementById('a-passive').value)||0;
    const capital  = parseFloat(document.getElementById('a-capital').value)||0;
    const liab     = parseFloat(document.getElementById('l-balance').value)||0;

    const ncf = inc - exp;
    const sav = inc > 0 ? Math.round((ncf / inc) * 100) : 0;
    const nw  = capital - liab;

    document.getElementById('k-inc').textContent = fmt(inc);
    document.getElementById('k-inc-sub').textContent = incCount + ' source' + (incCount !== 1 ? 's' : '');
    document.getElementById('k-exp').textContent = fmt(exp);
    document.getElementById('k-exp-sub').textContent = expCount + ' item' + (expCount !== 1 ? 's' : '');

    const ncfEl = document.getElementById('k-ncf');
    ncfEl.textContent = fmt(ncf);
    ncfEl.className = 'kpi-value ' + (ncf > 0 ? 'pos' : ncf < 0 ? 'neg' : 'neu');
    document.getElementById('k-sav').textContent = 'Savings rate: ' + sav + '%';

    const nwEl = document.getElementById('k-nw');
    nwEl.textContent = fmt(nw);
    nwEl.className = 'kpi-value ' + (nw > 0 ? 'pos' : nw < 0 ? 'neg' : 'neu');

    const ratio = inc > 0 ? Math.min(Math.round((exp / inc) * 100), 100) : 0;
    document.getElementById('ratio-lbl').textContent = ratio + '% of income';
    const rb = document.getElementById('ratio-bar');
    rb.style.width = ratio + '%';
    rb.style.background = ratio > 80 ? 'var(--red)' : ratio > 60 ? 'var(--amber)' : 'var(--green)';

    let statusTag, statusClass;
    if(inc === 0 && exp === 0){ statusTag = 'enter data'; statusClass = 'tag-amber'; }
    else if(ncf >= 0 && sav >= 20){ statusTag = '✓ On track'; statusClass = 'tag-green'; }
    else if(ncf >= 0){ statusTag = '⚠ Warning'; statusClass = 'tag-amber'; }
    else { statusTag = '✗ Deficit'; statusClass = 'tag-red'; }

    document.getElementById('k-status-wrap').innerHTML = `<span class="tag ${statusClass}">${statusTag}</span>`;
    document.getElementById('summary-status').innerHTML = `<span class="tag ${statusClass}">${statusTag}</span>`;
    const snwEl = document.getElementById('summary-nw');
    snwEl.textContent = fmt(nw);
    snwEl.className = 'summary-nw ' + (nw > 0 ? 'pos' : nw < 0 ? 'neg' : 'neu');

    const freedomPct = exp > 0 ? Math.min(Math.round((passive / exp) * 100), 100) : 0;
    const gap = Math.max(exp - passive, 0);
    document.getElementById('freedom-pct').textContent = freedomPct + '%';
    document.getElementById('freedom-pct').style.color = freedomPct >= 100 ? 'var(--green)' : freedomPct >= 50 ? 'var(--amber)' : 'var(--muted)';
    const fb = document.getElementById('freedom-bar');
    fb.style.width = freedomPct + '%';
    fb.style.background = freedomPct >= 100 ? 'var(--green)' : freedomPct >= 50 ? 'var(--amber)' : 'var(--red)';
    document.getElementById('freedom-passive').textContent = 'Passive: ' + fmt(passive) + ' / mo';
    document.getElementById('freedom-gap').textContent = 'Gap: ' + fmt(gap) + ' / mo';
    document.getElementById('freedom-target').textContent = 'Target: ' + fmt(exp) + ' / mo';

    let msg = '';
    if(passive === 0 && exp === 0){ msg = 'Enter your passive income and monthly expenses to see your RDPD freedom progress.'; }
    else if(freedomPct >= 100){ msg = '🎯 Financial freedom achieved — your passive income fully covers monthly expenses. Rich Dad would be proud.'; }
    else if(freedomPct >= 75){ msg = 'Almost there. You need ' + fmt(gap) + '/mo more in passive income to reach freedom. Consider increasing your COMI position or adding a second asset.'; }
    else if(freedomPct >= 50){ msg = 'Halfway to freedom. You need ' + fmt(gap) + '/mo more in passive income. At a 5% dividend yield, that requires EGP ' + Math.round(gap * 12 / 0.05).toLocaleString() + ' more in assets.'; }
    else if(freedomPct > 0){ msg = 'Building momentum. You need ' + fmt(gap) + '/mo more in passive income. Keep investing your net cash flow surplus into assets.'; }
    else { msg = 'No passive income yet. Start logging dividends and interest as you build your asset base. Every EGP counts.'; }
    document.getElementById('freedom-msg').textContent = msg;
    document.getElementById('freedom-msg').style.borderLeftColor = freedomPct >= 100 ? 'var(--green)' : freedomPct >= 50 ? 'var(--amber)' : 'var(--red)';
  }

  function copySnapshot(){
    let inc = 0, exp = 0;
    document.querySelectorAll('#income-rows input[type=number]').forEach(i => inc += parseFloat(i.value)||0);
    document.querySelectorAll('#expense-rows input[type=number]').forEach(i => exp += parseFloat(i.value)||0);
    const passive  = parseFloat(document.getElementById('a-passive').value)||0;
    const capital  = parseFloat(document.getElementById('a-capital').value)||0;
    const newInv   = parseFloat(document.getElementById('a-new').value)||0;
    const liab     = parseFloat(document.getElementById('l-balance').value)||0;
    const payment  = parseFloat(document.getElementById('l-payment').value)||0;
    const ncf = inc - exp;
    const sav = inc > 0 ? (ncf / inc * 100).toFixed(1) : '0';
    const nw  = capital - liab;
    const freedomPct = exp > 0 ? (passive / exp * 100).toFixed(1) : '0';
    const month = document.getElementById('month-badge').textContent;

    const snap = `MONTHLY SNAPSHOT — ${month}
━━━━━━━━━━━━━━━━━━━━━━━━
Salary (EGP):              ${Math.round(inc).toLocaleString()}
Total Income (EGP):        ${Math.round(inc).toLocaleString()}
Total Expenses (EGP):      ${Math.round(exp).toLocaleString()}
Net Cash Flow (EGP):       ${Math.round(ncf).toLocaleString()}
Savings Rate (%):          ${sav}%
━━━━━━━━━━━━━━━━━━━━━━━━
Total Assets (EGP):        ${Math.round(capital).toLocaleString()}
New Investment (EGP):      ${Math.round(newInv).toLocaleString()}
Passive Income (EGP):      ${Math.round(passive).toLocaleString()}
Total Liabilities (EGP):   ${Math.round(liab).toLocaleString()}
Monthly Payment (EGP):     ${Math.round(payment).toLocaleString()}
Net Worth (EGP):           ${Math.round(nw).toLocaleString()}
━━━━━━━━━━━━━━━━━━━━━━━━
Freedom Progress:          ${freedomPct}%
Status:                    ${ncf >= 0 && parseFloat(sav) >= 20 ? 'On Track' : ncf >= 0 ? 'Warning' : 'Deficit'}`;

    navigator.clipboard.writeText(snap).then(() => {
      const t = document.getElementById('toast');
      t.classList.add('show');
      setTimeout(() => t.classList.remove('show'), 3000);
    });
  }
</script>
</body>
</html>
