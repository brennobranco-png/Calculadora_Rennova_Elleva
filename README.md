<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Calculadora Rennova</title>
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <style>
        :root { --primary: #002D5E; --secondary: #00A3E0; --success: #2E7D32; --bg: #F0F2F5; }
        body { font-family: -apple-system, sans-serif; background-color: var(--bg); margin: 0; padding: 10px; }
        .app-container { max-width: 450px; margin: 0 auto; }
        
        header { text-align: center; background: #fff; padding: 15px; border-radius: 15px; margin-bottom: 15px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
        
        .card { background: #fff; padding: 15px; border-radius: 15px; margin-bottom: 15px; box-shadow: 0 2px 8px rgba(0,0,0,0.05); }
        .concorrente-header { border-left: 6px solid #666; }
        
        label { display: block; font-weight: 700; margin-bottom: 8px; font-size: 0.9rem; color: var(--primary); }
        input { width: 100%; padding: 12px; border: 2px solid #ddd; border-radius: 10px; font-size: 1.1rem; box-sizing: border-box; outline: none; transition: 0.3s; }
        input:focus { border-color: var(--secondary); background: #fff; }

        .product-card { border-top: 5px solid var(--secondary); text-align: center; position: relative; }
        
        /* Ícones Desenhados em SVG (Substituem as Fotos) */
        .icon-box { width: 80px; height: 80px; margin: 0 auto 10px; background: #f8f9fa; border-radius: 50%; display: flex; align-items: center; justify-content: center; }
        .icon-svg { width: 45px; height: 45px; fill: var(--primary); }

        .product-name { font-weight: 800; color: var(--primary); margin: 5px 0; font-size: 1.2rem; }
        .badge { background: var(--secondary); color: white; padding: 3px 10px; border-radius: 20px; font-size: 0.75rem; font-weight: bold; }
        
        .result-row { display: flex; justify-content: space-between; font-size: 0.85rem; padding: 8px 0; border-bottom: 1px solid #eee; }
        .highlight-gain { background: #e8f5e9; color: var(--success); padding: 12px; border-radius: 10px; margin-top: 10px; font-weight: 800; font-size: 1.2rem; }
        
        .simulacao-blue { background: var(--primary); color: #fff; padding: 20px; border-radius: 20px; margin-bottom: 40px; }
        .sim-item { background: rgba(255,255,255,0.1); padding: 12px; border-radius: 10px; margin-top: 10px; display: flex; justify-content: space-between; align-items: center; }
        .val-eco { color: #4CAF50; font-weight: 800; }
    </style>
</head>
<body>

<div class="app-container">
    <header>
        <svg viewBox="0 0 200 50" style="width:180px;"><text x="10" y="35" font-family="Arial" font-weight="bold" font-size="28" fill="#002D5E">RENNOVA</text></svg>
        <div style="color: var(--secondary); font-weight: bold; font-size: 0.8rem; letter-spacing: 2px;">ELLEVA LINE</div>
    </header>

    <div class="card concorrente-header">
        <label>Preço Pago no Concorrente (150mg):</label>
        <input type="number" id="pConc" placeholder="R$ 0,00" oninput="calc()">
    </div>

    <div class="card product-card">
        <div class="icon-box">
            <svg class="icon-svg" viewBox="0 0 24 24"><path d="M19,2H5C3.9,2,3,2.9,3,4v16c0,1.1,0.9,2,2,2h14c1.1,0,2-0.9,2-2V4C21,2.9,20.1,2,19,2z M17,19H7v-2h10V19z M17,15H7v-2h10V15z M17,11H7V9h10V11z M17,7H7V5h10V7z"/></svg>
        </div>
        <div class="product-name">Elleva <span class="badge">210mg</span></div>
        <p style="font-size:0.8rem; color:#666; margin-bottom:15px;">Equivale a 1,4 frascos</p>
        <label>Preço Elleva:</label>
        <input type="number" id="pE210" placeholder="R$ 0,00" oninput="calc()">
        <div class="result-row" style="margin-top:10px;">
            <span>Custo Conc. p/ 210mg:</span>
            <span id="rC210">R$ 0,00</span>
        </div>
        <div class="highlight-gain">Lucro: <span id="v210">R$ 0,00</span></div>
    </div>

    <div class="card product-card">
        <div class="icon-box" style="background: #e3f2fd;">
            <svg class="icon-svg" style="fill:var(--secondary)" viewBox="0 0 24 24"><path d="M19,2H5C3.9,2,3,2.9,3,4v16c0,1.1,0.9,2,2,2h14c1.1,0,2-0.9,2-2V4C21,2.9,20.1,2,19,2z M17,19H7v-2h10V19z M17,15H7v-2h10V15z M17,11H7V9h10V11z M17,7H7V5h10V7z"/></svg>
        </div>
        <div class="product-name">Elleva X <span class="badge" style="background:var(--primary)">630mg</span></div>
        <p style="font-size:0.8rem; color:#666; margin-bottom:15px;">Equivale a 4,2 frascos</p>
        <label>Preço Elleva X:</label>
        <input type="number" id="pEX" placeholder="R$ 0,00" oninput="calc()">
        <div class="result-row" style="margin-top:10px;">
            <span>Custo Conc. p/ 630mg:</span>
            <span id="rCEX">R$ 0,00</span>
        </div>
        <div class="highlight-gain">Lucro: <span id="vEX">R$ 0,00</span></div>
    </div>

    <div class="card product-card">
        <div class="icon-box">
            <svg class="icon-svg" viewBox="0 0 24 24"><path d="M12,2L4,5v6.09c0,5.05,3.41,9.76,8,10.91c4.59-1.15,8-5.86,8-10.91V5L12,2z"/></svg>
        </div>
        <div class="product-name">Elleva 150 <span class="badge" style="background:#666">150mg</span></div>
        <p style="font-size:0.8rem; color:#666; margin-bottom:15px;">Equivale a 1,0 frasco</p>
        <label>Preço Elleva 150:</label>
        <input type="number" id="pE150" placeholder="R$ 0,00" oninput="calc()">
        <div class="result-row" style="margin-top:10px;">
            <span>Custo Conc. p/ 150mg:</span>
            <span id="rCE150">R$ 0,00</span>
        </div>
        <div class="highlight-gain">Lucro: <span id="v150">R$ 0,00</span></div>
    </div>

    <div class="simulacao-blue">
        <h3 style="text-align:center; margin:0 0 15px 0;">Projeção Mensal</h3>
        <label style="color:#fff">Volume de Vendas (Frascos):</label>
        <input type="number" id="qtd" placeholder="0" oninput="calc()">
        <div class="sim-item"><span>Ganho Elleva 210:</span><strong class="val-eco" id="m210">R$ 0,00</strong></div>
        <div class="sim-item"><span>Ganho Elleva X:</span><strong class="val-eco" id="mEX">R$ 0,00</strong></div>
    </div>
</div>

<script>
    const f = v => v.toLocaleString('pt-br',{style:'currency',currency:'BRL'});
    function calc() {
        const pc = parseFloat(document.getElementById('pConc').value) || 0;
        const e210 = parseFloat(document.getElementById('pE210').value) || 0;
        const ex = parseFloat(document.getElementById('pEX').value) || 0;
        const e150 = parseFloat(document.getElementById('pE150').value) || 0;
        const q = parseFloat(document.getElementById('qtd').value) || 0;

        const c210 = pc * 1.4; const cex = pc * 4.2; const c150 = pc * 1.0;
        document.getElementById('rC210').innerText = f(c210);
        document.getElementById('rCEX').innerText = f(cex);
        document.getElementById('rCE150').innerText = f(c150);

        const v210 = c210 - e210; const vex = cex - ex; const v150 = c150 - e150;
        document.getElementById('v210').innerText = f(v210);
        document.getElementById('vEX').innerText = f(vex);
        document.getElementById('v150').innerText = f(v150);

        document.getElementById('m210').innerText = f(v210 * q);
        document.getElementById('mEX').innerText = f(vex * q);
    }
</script>
</body>
</html>
