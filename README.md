<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Calculadora Rennova</title>
    
    <meta name="mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="RennovaCalc">

    <style>
        :root {
            --primary: #002D5E;
            --secondary: #00A3E0;
            --success: #2E7D32;
            --bg: #F0F2F5;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            background-color: var(--bg);
            margin: 0;
            padding: 10px;
            color: #333;
        }

        .app-container { max-width: 500px; margin: 0 auto; }

        header {
            text-align: center;
            background: #fff;
            padding: 15px;
            border-radius: 15px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            margin-bottom: 15px;
        }

        .logo { width: 160px; height: auto; }

        .card {
            background: #fff;
            padding: 15px;
            border-radius: 15px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
            margin-bottom: 15px;
        }

        label { display: block; font-weight: 700; margin-bottom: 8px; font-size: 0.9rem; color: var(--primary); }

        input {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 1rem;
            box-sizing: border-box;
            background: #f9f9f9;
            outline: none;
        }

        input:focus { border-color: var(--secondary); }

        .product-card { border-top: 5px solid var(--secondary); text-align: center; }
        
        .product-img { height: 130px; object-fit: contain; margin: 10px 0; }

        .product-name { font-weight: 800; color: var(--primary); margin: 5px 0; font-size: 1.1rem; }

        .equivalencia { font-size: 0.8rem; color: #666; margin-bottom: 10px; }

        .result-row {
            display: flex;
            justify-content: space-between;
            font-size: 0.9rem;
            padding: 8px 0;
            border-bottom: 1px solid #eee;
        }

        .highlight-gain {
            background: #e8f5e9;
            color: var(--success);
            padding: 12px;
            border-radius: 10px;
            margin-top: 10px;
            font-weight: 800;
            font-size: 1.1rem;
        }

        .simulacao-blue {
            background: var(--primary);
            color: #fff;
            padding: 20px;
            border-radius: 20px;
            margin-top: 20px;
            margin-bottom: 40px;
        }

        .sim-item {
            background: rgba(255,255,255,0.1);
            padding: 12px;
            border-radius: 10px;
            margin-top: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .val-eco { color: #4CAF50; font-weight: 800; font-size: 1rem; }
    </style>
</head>
<body>

<div class="app-container">
    <header>
        <img src="https://i.ibb.co/LzNfX6W/logo-rennova.png" alt="Rennova" class="logo">
    </header>

    <div class="card" style="border-left: 5px solid #666;">
        <label>Preço Pago no Concorrente (150mg):</label>
        <input type="number" id="pConc" placeholder="R$ 0,00" oninput="calc()">
    </div>

    <div class="card product-card">
        <img src="https://i.ibb.co/V9mD5M8/elleva-210.png" class="product-img">
        <div class="product-name">Elleva 210mg</div>
        <div class="equivalencia">Rende 1,4x mais que o concorrente</div>
        <label>Preço Elleva:</label>
        <input type="number" id="pE210" placeholder="R$ 0,00" oninput="calc()">
        <div class="result-row" style="margin-top:10px;">
            <span>Custo Conc. p/ 210mg:</span>
            <span id="rC210">R$ 0,00</span>
        </div>
        <div class="highlight-gain">
            Lucro p/ Frasco: <span id="v210">R$ 0,00</span>
        </div>
    </div>

    <div class="card product-card">
        <img src="https://i.ibb.co/M9YhK0P/elleva-x.png" class="product-img">
        <div class="product-name">Elleva X 630mg</div>
        <div class="equivalencia">Rende 4,2x mais que o concorrente</div>
        <label>Preço Elleva X:</label>
        <input type="number" id="pEX" placeholder="R$ 0,00" oninput="calc()">
        <div class="result-row" style="margin-top:10px;">
            <span>Custo Conc. p/ 630mg:</span>
            <span id="rCEX">R$ 0,00</span>
        </div>
        <div class="highlight-gain">
            Lucro p/ Frasco: <span id="vEX">R$ 0,00</span>
        </div>
    </div>

    <div class="card product-card">
        <img src="https://i.ibb.co/mS7S6mX/elleva-150.png" class="product-img">
        <div class="product-name">Elleva 150mg</div>
        <div class="equivalencia">Mesma volumetria do concorrente</div>
        <label>Preço Elleva 150:</label>
        <input type="number" id="pE150" placeholder="R$ 0,00" oninput="calc()">
        <div class="result-row" style="margin-top:10px;">
            <span>Custo Conc. p/ 150mg:</span>
            <span id="rCE150">R$ 0,00</span>
        </div>
        <div class="highlight-gain">
            Lucro p/ Frasco: <span id="v150">R$ 0,00</span>
        </div>
    </div>

    <div class="simulacao-blue">
        <h3 style="margin-top:0; text-align:center;">Simulação de Ganho Mensal</h3>
        <label style="color:#fff">Qtd de Frascos comprados/mês:</label>
        <input type="number" id="qtd" placeholder="0" oninput="calc()">
        
        <div class="sim-item">
            <span>Elleva 210</span>
            <div style="text-align:right">
                <div class="val-eco" id="m210">R$ 0,00</div>
                <div style="font-size:0.7rem; color: #ddd" id="a210">Anual: R$ 0,00</div>
            </div>
        </div>
        <div class="sim-item">
            <span>Elleva X</span>
            <div style="text-align:right">
                <div class="val-eco" id="mEX">R$ 0,00</div>
                <div style="font-size:0.7rem; color: #ddd" id="aEX">Anual: R$ 0,00</div>
            </div>
        </div>
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

        const c210 = pc * 1.4;
        const cex = pc * 4.2;
        const c150 = pc * 1.0;

        document.getElementById('rC210').innerText = f(c210);
        document.getElementById('rCEX').innerText = f(cex);
        document.getElementById('rCE150').innerText = f(c150);

        const v210 = c210 - e210;
        const vex = cex - ex;
        const v150 = c150 - e150;

        document.getElementById('v210').innerText = f(v210);
        document.getElementById('vEX').innerText = f(vex);
        document.getElementById('v150').innerText = f(v150);

        document.getElementById('m210').innerText = f(v210 * q);
        document.getElementById('a210').innerText = "Anual: " + f(v210 * q * 12);
        document.getElementById('mEX').innerText = f(vex * q);
        document.getElementById('aEX').innerText = "Anual: " + f(vex * q * 12);
    }
</script>

</body>
</html>
