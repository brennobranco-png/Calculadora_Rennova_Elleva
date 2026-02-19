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
        .app-container { max-width: 500px; margin: 0 auto; }
        header { text-align: center; background: #fff; padding: 15px; border-radius: 15px; margin-bottom: 15px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
        .card { background: #fff; padding: 15px; border-radius: 15px; margin-bottom: 15px; box-shadow: 0 2px 8px rgba(0,0,0,0.05); }
        label { display: block; font-weight: 700; margin-bottom: 8px; font-size: 0.9rem; color: var(--primary); }
        input { width: 100%; padding: 12px; border: 2px solid #ddd; border-radius: 10px; font-size: 1rem; box-sizing: border-box; outline: none; }
        .product-card { border-top: 5px solid var(--secondary); text-align: center; }
        .product-img { height: 110px; object-fit: contain; margin: 10px 0; background: #f9f9f9; border-radius: 10px; padding: 5px; }
        .product-name { font-weight: 800; color: var(--primary); margin: 5px 0; }
        .highlight-gain { background: #e8f5e9; color: var(--success); padding: 12px; border-radius: 10px; margin-top: 10px; font-weight: 800; font-size: 1.1rem; }
        .simulacao-blue { background: var(--primary); color: #fff; padding: 20px; border-radius: 20px; margin-bottom: 40px; }
        .sim-item { background: rgba(255,255,255,0.1); padding: 12px; border-radius: 10px; margin-top: 10px; display: flex; justify-content: space-between; }
    </style>
</head>
<body>

<div class="app-container">
    <header>
        <h2 style="color:var(--primary); margin:0;">RENNOVA ELLEVA</h2>
    </header>

    <div class="card" style="border-left: 5px solid #666;">
        <label>Preço Pago no Concorrente (150mg):</label>
        <input type="number" id="pConc" placeholder="R$ 0,00" oninput="calc()">
    </div>

    <div class="card product-card">
        <div class="product-name">Elleva 210mg</div>
        <p style="font-size:0.8rem; color:#666">Equivale a 1,4 frascos</p>
        <label>Preço Elleva:</label>
        <input type="number" id="pE210" placeholder="R$ 0,00" oninput="calc()">
        <div class="highlight-gain">Lucro: <span id="v210">R$ 0,00</span></div>
    </div>

    <div class="card product-card">
        <div class="product-name">Elleva X 630mg</div>
        <p style="font-size:0.8rem; color:#666">Equivale a 4,2 frascos</p>
        <label>Preço Elleva X:</label>
        <input type="number" id="pEX" placeholder="R$ 0,00" oninput="calc()">
        <div class="highlight-gain">Lucro: <span id="vEX">R$ 0,00</span></div>
    </div>

    <div class="card product-card">
        <div class="product-name">Elleva 150mg</div>
        <p style="font-size:0.8rem; color:#666">Equivale a 1,0 frasco</p>
        <label>Preço Elleva 150:</label>
        <input type="number" id="pE150" placeholder="R$ 0,00" oninput="calc()">
        <div class="highlight-gain">Lucro: <span id="v150">R$ 0,00</span></div>
    </div>

    <div class="simulacao-blue">
        <h3 style="text-align:center; margin:0 0 15px 0;">Simulação Mensal</h3>
        <label style="color:#fff">Qtd de Frascos/mês:</label>
        <input type="number" id="qtd" placeholder="0" oninput="calc()">
        <div class="sim-item"><span>Elleva 210</span><strong id="m210">R$ 0,00</strong></div>
        <div class="sim-item"><span>Elleva X</span><strong id="mEX">R$ 0,00</strong></div>
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

        const v210 = (pc * 1.4) - e210;
        const vex = (pc * 4.2) - ex;
        const v150 = (pc * 1.0) - e150;

        document.getElementById('v210').innerText = f(v210);
        document.getElementById('vEX').innerText = f(vex);
        document.getElementById('v150').innerText = f(v150);
        document.getElementById('m210').innerText = f(v210 * q);
        document.getElementById('mEX').innerText = f(vex * q);
    }
</script>
</body>
</html>
