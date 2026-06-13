<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>Salary Tax Calculator 2026–27</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Inter:wght@400;500;600&display=swap');

  * { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --emerald:   #1B6B4A;
    --emerald-light: #2E8B6A;
    --gold:      #C8922A;
    --gold-light:#F0B94A;
    --cream:     #FDF8F0;
    --card:      #FFFFFF;
    --text:      #1A1A2E;
    --muted:     #6B7280;
    --result-bg: #F0F7F4;
    --border:    #D1E8DF;
    --red:       #C0392B;
    --shadow:    0 2px 12px rgba(27,107,74,0.10);
  }

  body {
    font-family: 'Inter', sans-serif;
    background: linear-gradient(160deg, #0f3d28 0%, #1B6B4A 40%, #145c3c 100%);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    padding: 0 0 40px 0;
  }

  .phone-wrap {
    width: 100%;
    max-width: 430px;
    min-height: 100vh;
    background: var(--cream);
    display: flex;
    flex-direction: column;
    overflow: hidden;
    position: relative;
  }

  /* HEADER */
  .header {
    background: linear-gradient(135deg, #0f3d28 0%, #1B6B4A 60%, #2E8B6A 100%);
    padding: 36px 24px 28px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .header::before {
    content: '';
    position: absolute;
    top: -40px; right: -40px;
    width: 160px; height: 160px;
    border-radius: 50%;
    background: rgba(200,146,42,0.15);
  }
  .header::after {
    content: '';
    position: absolute;
    bottom: -30px; left: -30px;
    width: 120px; height: 120px;
    border-radius: 50%;
    background: rgba(200,146,42,0.10);
  }
  .flag-stripe {
    display: flex;
    justify-content: center;
    gap: 6px;
    margin-bottom: 14px;
  }
  .flag-stripe span {
    display: block;
    height: 4px;
    border-radius: 2px;
  }
  .flag-stripe .s1 { width: 28px; background: #fff; }
  .flag-stripe .s2 { width: 60px; background: var(--gold); }
  .flag-stripe .s3 { width: 28px; background: #fff; }

  .header-icon {
    font-size: 36px;
    margin-bottom: 8px;
    display: block;
    filter: drop-shadow(0 2px 4px rgba(0,0,0,0.3));
  }
  .header h1 {
    font-family: 'Playfair Display', serif;
    color: #fff;
    font-size: 20px;
    line-height: 1.25;
    letter-spacing: 0.3px;
    position: relative; z-index: 1;
  }
  .header h1 span {
    color: var(--gold-light);
  }
  .year-badge {
    display: inline-block;
    background: var(--gold);
    color: #fff;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    padding: 4px 14px;
    border-radius: 20px;
    margin-top: 10px;
    position: relative; z-index: 1;
  }

  /* BODY */
  .body {
    flex: 1;
    padding: 24px 20px 20px;
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  /* INPUT SECTION */
  .input-section {
    background: var(--card);
    border-radius: 16px;
    padding: 20px;
    box-shadow: var(--shadow);
    border: 1px solid var(--border);
  }
  .section-label {
    font-size: 11px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1.2px;
    color: var(--emerald);
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .input-wrapper {
    position: relative;
  }
  .currency-prefix {
    position: absolute;
    left: 14px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 15px;
    font-weight: 700;
    color: var(--emerald);
  }
  .salary-input {
    width: 100%;
    background: linear-gradient(135deg, #F0F7F4, #E8F5EF);
    border: 2px solid var(--emerald);
    border-radius: 12px;
    padding: 16px 16px 16px 44px;
    font-size: 24px;
    font-weight: 700;
    color: var(--text);
    font-family: 'Inter', sans-serif;
    outline: none;
    transition: border-color 0.2s, box-shadow 0.2s;
  }
  .salary-input:focus {
    border-color: var(--gold);
    box-shadow: 0 0 0 4px rgba(200,146,42,0.15);
  }
  .salary-input::placeholder { color: #bbb; font-weight: 400; font-size: 16px; }

  .slab-indicator {
    margin-top: 10px;
    padding: 8px 12px;
    border-radius: 8px;
    font-size: 12px;
    font-weight: 600;
    background: #FFF8E6;
    color: var(--gold);
    border-left: 3px solid var(--gold);
    display: none;
  }
  .slab-indicator.visible { display: block; }

  /* RESULTS */
  .results-section {
    background: var(--card);
    border-radius: 16px;
    padding: 20px;
    box-shadow: var(--shadow);
    border: 1px solid var(--border);
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .result-row {
    display: flex;
    flex-direction: column;
    gap: 4px;
  }
  .result-label {
    font-size: 12px;
    font-weight: 600;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.8px;
  }
  .result-value {
    background: var(--result-bg);
    border: 1.5px solid var(--border);
    border-radius: 10px;
    padding: 13px 16px;
    font-size: 18px;
    font-weight: 700;
    color: var(--text);
    font-family: 'Inter', sans-serif;
    min-height: 50px;
    display: flex;
    align-items: center;
    transition: all 0.3s;
  }
  .result-value.tax { color: var(--red); background: #FFF5F5; border-color: #FECACA; }
  .result-value.net { color: var(--emerald); background: #F0F7F4; border-color: var(--border); }
  .result-value.highlight {
    background: linear-gradient(135deg, #0f3d28, #1B6B4A);
    color: #fff;
    border-color: transparent;
    font-size: 20px;
  }
  .result-value.placeholder { color: #ccc; font-size: 15px; font-weight: 400; }

  .divider {
    height: 1px;
    background: var(--border);
    margin: 4px 0;
  }

  .section-title-small {
    font-size: 11px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: var(--muted);
    padding: 4px 0 0;
  }

  /* SLAB TABLE */
  .slab-section {
    background: var(--card);
    border-radius: 16px;
    padding: 20px;
    box-shadow: var(--shadow);
    border: 1px solid var(--border);
  }
  .slab-table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 12px;
    font-size: 12px;
  }
  .slab-table th {
    background: var(--emerald);
    color: #fff;
    padding: 8px 10px;
    text-align: left;
    font-size: 10px;
    text-transform: uppercase;
    letter-spacing: 0.8px;
  }
  .slab-table th:first-child { border-radius: 8px 0 0 0; }
  .slab-table th:last-child { border-radius: 0 8px 0 0; }
  .slab-table td {
    padding: 8px 10px;
    border-bottom: 1px solid #E8F5EF;
    color: var(--text);
    font-weight: 500;
  }
  .slab-table tr:last-child td { border-bottom: none; }
  .slab-table tr:nth-child(even) td { background: #F9FFFE; }
  .slab-table tr.active-slab td {
    background: #FFF8E6 !important;
    color: var(--gold);
    font-weight: 700;
  }
  .slab-rate { color: var(--red); font-weight: 700; }

  /* FOOTER */
  .footer {
    background: linear-gradient(135deg, #0f3d28, #1B6B4A);
    padding: 20px 24px;
    text-align: center;
  }
  .footer-dev {
    font-size: 11px;
    color: rgba(255,255,255,0.6);
    letter-spacing: 0.5px;
    margin-bottom: 2px;
  }
  .footer-name {
    font-family: 'Playfair Display', serif;
    font-size: 15px;
    color: var(--gold-light);
    letter-spacing: 1px;
  }
  .footer-year {
    font-size: 10px;
    color: rgba(255,255,255,0.4);
    margin-top: 6px;
    letter-spacing: 1px;
  }

  /* Animate number */
  @keyframes pop {
    0% { transform: scale(1); }
    50% { transform: scale(1.03); }
    100% { transform: scale(1); }
  }
  .pop { animation: pop 0.25s ease; }
</style>
</head>
<body>
<div class="phone-wrap">

  <!-- HEADER -->
  <div class="header">
    <div class="flag-stripe">
      <span class="s1"></span>
      <span class="s2"></span>
      <span class="s3"></span>
    </div>
    <span class="header-icon">🧮</span>
    <h1>Pakistan Salary<br><span>Tax Calculator</span></h1>
    <div class="year-badge">FY 2026 – 2027</div>
  </div>

  <div class="body">

    <!-- INPUT -->
    <div class="input-section">
      <div class="section-label">Enter Monthly Salary</div>
      <div class="input-wrapper">
        <span class="currency-prefix">Rs</span>
        <input
          type="number"
          class="salary-input"
          id="salaryInput"
          placeholder="e.g. 387200"
          oninput="calculate()"
          min="0"
        />
      </div>
      <div class="slab-indicator" id="slabIndicator"></div>
    </div>

    <!-- MONTHLY RESULTS -->
    <div class="results-section">
      <div class="section-title-small">📅 Monthly Breakdown</div>

      <div class="result-row">
        <div class="result-label">Monthly Salary</div>
        <div class="result-value" id="monthlySalary"><span class="placeholder-text" style="color:#ccc;font-size:15px;font-weight:400">—</span></div>
      </div>
      <div class="result-row">
        <div class="result-label">Monthly Tax</div>
        <div class="result-value tax" id="monthlyTax"><span class="placeholder-text" style="color:#ccc;font-size:15px;font-weight:400">—</span></div>
      </div>
      <div class="result-row">
        <div class="result-label">Monthly Salary After Tax</div>
        <div class="result-value net" id="monthlyNet"><span class="placeholder-text" style="color:#ccc;font-size:15px;font-weight:400">—</span></div>
      </div>

      <div class="divider"></div>
      <div class="section-title-small">📆 Annual Breakdown</div>

      <div class="result-row">
        <div class="result-label">Yearly Salary</div>
        <div class="result-value" id="yearlySalary"><span class="placeholder-text" style="color:#ccc;font-size:15px;font-weight:400">—</span></div>
      </div>
      <div class="result-row">
        <div class="result-label">Yearly Tax</div>
        <div class="result-value tax" id="yearlyTax"><span class="placeholder-text" style="color:#ccc;font-size:15px;font-weight:400">—</span></div>
      </div>
      <div class="result-row">
        <div class="result-label">Yearly Salary After Tax</div>
        <div class="result-value highlight" id="yearlyNet"><span class="placeholder-text" style="color:rgba(255,255,255,0.4);font-size:15px;font-weight:400">—</span></div>
      </div>

    </div>

    <!-- SLAB TABLE -->
    <div class="slab-section">
      <div class="section-label">Tax Slabs 2026–27</div>
      <table class="slab-table" id="slabTable">
        <thead>
          <tr>
            <th>Annual Income (Rs)</th>
            <th>Rate</th>
          </tr>
        </thead>
        <tbody>
          <tr data-slab="0"><td>Up to 600,000</td><td class="slab-rate">0%</td></tr>
          <tr data-slab="1"><td>600,001 – 1,200,000</td><td class="slab-rate">1%</td></tr>
          <tr data-slab="2"><td>1,200,001 – 2,200,000</td><td class="slab-rate">11%</td></tr>
          <tr data-slab="3"><td>2,200,001 – 3,200,000</td><td class="slab-rate">20%</td></tr>
          <tr data-slab="4"><td>3,200,001 – 4,100,000</td><td class="slab-rate">25%</td></tr>
          <tr data-slab="5"><td>4,100,001 – 5,600,000</td><td class="slab-rate">29%</td></tr>
          <tr data-slab="6"><td>5,600,001 – 7,000,000</td><td class="slab-rate">32%</td></tr>
          <tr data-slab="7"><td>Above 7,000,000</td><td class="slab-rate">35%</td></tr>
        </tbody>
      </table>
    </div>

  </div><!-- /body -->

  <!-- FOOTER -->
  <div class="footer">
    <div class="footer-dev">Developed by</div>
    <div class="footer-name">Zafar Mehmood Malik</div>
    <div class="footer-year">PAKISTAN TAX CALCULATOR · FY 2026–2027</div>
  </div>

</div><!-- /phone-wrap -->

<script>
  function fmt(n) {
    return 'Rs ' + Math.round(n).toLocaleString('en-PK');
  }

  function calcAnnualTax(annual) {
    // Slabs with fixed amounts
    if (annual <= 600000)      return { tax: 0, slab: 0 };
    if (annual <= 1200000)     return { tax: (annual - 600000) * 0.01, slab: 1 };
    if (annual <= 2200000)     return { tax: 6000 + (annual - 1200000) * 0.11, slab: 2 };
    if (annual <= 3200000)     return { tax: 6000 + 110000 + (annual - 2200000) * 0.20, slab: 3 };
    if (annual <= 4100000)     return { tax: 6000 + 110000 + 200000 + (annual - 3200000) * 0.25, slab: 4 };
    if (annual <= 5600000)     return { tax: 6000 + 110000 + 200000 + 225000 + (annual - 4100000) * 0.29, slab: 5 };
    if (annual <= 7000000)     return { tax: 6000 + 110000 + 200000 + 225000 + 435000 + (annual - 5600000) * 0.32, slab: 6 };
    return { tax: 6000 + 110000 + 200000 + 225000 + 435000 + 448000 + (annual - 7000000) * 0.35, slab: 7 };
  }

  const slabNames = [
    'Slab 1 · 0% — Tax Exempt',
    'Slab 2 · 1% on amount exceeding Rs 600,000',
    'Slab 3 · Rs 6,000 + 11% on amount exceeding Rs 1,200,000',
    'Slab 4 · Rs 116,000 + 20% on amount exceeding Rs 2,200,000',
    'Slab 5 · Rs 316,000 + 25% on amount exceeding Rs 3,200,000',
    'Slab 6 · Rs 541,000 + 29% on amount exceeding Rs 4,100,000',
    'Slab 7 · Rs 976,000 + 32% on amount exceeding Rs 5,600,000',
    'Slab 8 · Rs 1,424,000 + 35% on amount exceeding Rs 7,000,000',
  ];

  function setVal(id, value, animate=true) {
    const el = document.getElementById(id);
    el.textContent = value;
    if (animate) {
      el.classList.remove('pop');
      void el.offsetWidth;
      el.classList.add('pop');
    }
  }

  function clearAll() {
    const ids = ['monthlySalary','monthlyTax','monthlyNet','yearlySalary','yearlyTax','yearlyNet'];
    ids.forEach(id => {
      document.getElementById(id).innerHTML = '<span style="color:#ccc;font-size:15px;font-weight:400">—</span>';
    });
    document.getElementById('slabIndicator').classList.remove('visible');
    document.querySelectorAll('#slabTable tr.active-slab').forEach(r => r.classList.remove('active-slab'));
  }

  function calculate() {
    const raw = document.getElementById('salaryInput').value;
    const monthly = parseFloat(raw);

    if (!raw || isNaN(monthly) || monthly <= 0) {
      clearAll();
      return;
    }

    const annual = monthly * 12;
    const { tax: annualTax, slab } = calcAnnualTax(annual);
    const monthlyTax = annualTax / 12;
    const monthlyNet = monthly - monthlyTax;
    const yearlyNet = annual - annualTax;

    setVal('monthlySalary', fmt(monthly));
    setVal('monthlyTax', fmt(monthlyTax));
    setVal('monthlyNet', fmt(monthlyNet));
    setVal('yearlySalary', fmt(annual));
    setVal('yearlyTax', fmt(annualTax));
    setVal('yearlyNet', fmt(yearlyNet));

    // Slab indicator
    const ind = document.getElementById('slabIndicator');
    ind.textContent = '📊 ' + slabNames[slab];
    ind.classList.add('visible');

    // Highlight active slab row
    document.querySelectorAll('#slabTable tbody tr').forEach(r => r.classList.remove('active-slab'));
    const activeRow = document.querySelector(#slabTable tbody tr[data-slab="${slab}"]);
    if (activeRow) activeRow.classList.add('active-slab');
  }
</script>
</body>
</html>
