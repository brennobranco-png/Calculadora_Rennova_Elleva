<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Rentabilidade - Linha Elleva</title>
    
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="Elleva Calc">
    <link rel="apple-touch-icon" href="logo.png">

    <style>
        :root {
            --primary-blue: #002D5E;
            --secondary-blue: #00A3E0;
            --light-blue: #E3F2FD;
            --success-green: #2E7D32;
            --bg-gray: #F8F9FA;
            --white: #FFFFFF;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-gray);
            margin: 0;
            padding: 0;
            color: #333;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            text-align: center;
            padding: 20px 0;
            background: var(--white);
            border-bottom: 4px solid var(--secondary-blue);
            margin-bottom: 25px;
            border-radius: 0 0 15px 15px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
        }

        .logo {
            max-width: 200px;
            height: auto;
        }

        h1 {
            color: var(--primary-blue);
            font-size: 1.2rem;
            margin-top: 10px;
            text-transform: uppercase;
        }

        .card-concorrente {
            background: var(--white);
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            margin-bottom: 25px;
            border-left: 6px solid #666;
        }

        label {
            display: block;
            font-weight: bold;
            margin-bottom: 8px;
            color: #444;
        }

        input[type="number"] {
            width: 100%;
            padding: 12px;
            border: 2px solid #DDD;
            border-radius: 8px;
            font-size: 1.1rem;
            box-sizing: border-box;
            outline: none;
            transition: border 0.3s;
        }

        input[type="number"]:focus {
            border-color: var(--secondary-blue);
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .product-card {
            background: var(--white);
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.08);
            display: flex;
            flex-direction: column;
            border-top: 5px solid var(--secondary-blue);
        }

        .product-img {
            width: 100%;
            height: 150px;
            object-fit: contain;
            margin-bottom: 15px;
        }

        .product-name {
            font-size: 1.1rem;
            font-weight: bold;
            color: var(--primary-blue);
            text-align: center;
            margin-bottom: 15px;
            min-height: 40px;
        }

        .info-row {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px solid #EEE;
            font-size: 0.9rem;
        }

        .highlight-box {
            background: var(--light-blue);
            padding: 10px;
            border-radius: 8px;
            margin: 10px 0;
            text-align: center;
        }

        .savings {
            color: var(--success-green);
            font-weight: bold;
            font-size: 1.2rem;
        }

        .simulation-section {
            background-color: var(--primary-blue);
            color: var(--white);
            padding: 25px;
            border-radius: 15px;
            margin-top: 20px;
            margin-bottom: 40px;
        }

        .simulation-section h2 {
            margin-top: 0;
            text-align: center;
            font-size: 1.2rem;
            border-bottom: 1px solid rgba(255,255,255,0.2);
            padding-bottom: 15px;
        }

        .input-monthly {
            max-width: 400px;
            margin: 20px auto;
            background: rgba(255,255,255,0.1);
            padding: 15px;
            border-radius: 10px;
        }

        .sim-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .sim-item {
            background: var(--white);
            color: #333;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
        }

        .sim-item strong {
            display: block;
            font-size: 1.1rem;
            color: var(--success-green);
            margin-top: 5px;
        }

        .badge-mg {
            background: var(--secondary-blue);
            color: white;
            padding: 2px 8px;
            border-radius: 5px;
            font-size: 0.75rem;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <img src="logo.png" alt="Rennova" class="logo">
        <h1>Rentabilidade Elleva</h1>
    </header>

    <div class="card-concorrente">
        <label>Preço de compra do Concorrente (150mg):</label>
        <input type="number" id="inputConcorrente" placeholder="R$ 0,00" oninput="calcular()">
    </div>

    <div class="products-grid">
        <div class="product-card">
            <img src="elleva.png" alt="Elleva 210mg" class="product-img">
            <div class="product-name">Elleva <span class="badge-mg">210mg</span></div>
            <label>Preço Elleva:</label>
            <input type="number" id="inputElleva" placeholder="R$ 0,00" oninput="calcular()">
            <div class="info-row" style="margin-top:10px;">
                <span>Equivalência:</span>
                <span><strong>1,4 frascos</strong></span>
            </div>
            <div class="info-row">
                <span>Custo Conc. p/ 210mg:</span>
                <span id="custoFinalConcElleva">R$ 0,00</span>
            </div>
            <div class="highlight-box">
                <div>Vantagem p/ Frasco:</div>
                <div class="savings" id="vantagemElleva">R$ 0,00</div>
            </div>
        </div>

        <div class="product-card">
            <img src="ellevax.png" alt="Elleva X 630mg" class="product-img">
            <div class="product-name">Elleva X <span class="badge-mg">630mg</span></div>
            <label>Preço Elleva X:</label>
            <input type="number" id="inputEllevaX" placeholder="R$ 0,00" oninput="calcular()">
            <div class="info-row" style="margin-top:10px;">
                <span>Equivalência:</span>
                <span><strong>4,2 frascos</strong></span>
            </div>
            <div class="info-row">
                <span>Custo Conc. p/ 630mg:</span>
                <span id="custoFinalConcEllevaX">R$ 0,00</span>
            </div>
            <div class="highlight-box">
                <div>Vantagem p/ Frasco:</div>
                <div class="savings" id="vantagemEllevaX">R$ 0,00</div>
            </div>
        </div>

        <div class="product-card">
            <img src="elleva150.png" alt="Elleva 150mg" class="product-img">
            <div class="product-name">Elleva 150 <span class="badge-mg">150mg</span></div>
            <label>Preço Elleva 150:</label>
            <input type="number" id="inputElleva150" placeholder="R$ 0,00" oninput="calcular()">
            <div class="info-row" style="margin-top:10px;">
                <span>Equivalência:</span>
                <span><strong>1,0 frasco</strong></span>
            </div>
            <div class="info-row">
                <span>Custo Conc. p/ 150mg:</span>
                <span id="custoFinalConcElleva150">R$ 0,00</span>
            </div>
            <div class="highlight-box">
                <div>Vantagem p/ Frasco:</div>
                <div class="savings" id="vantagemElleva150">R$ 0,00</div>
            </div>
        </div>
    </div>

    <div class="simulation-section">
        <h2>Simulação de Consumo Mensal</h2>
        <div class="input-monthly">
            <label style="color: white; text-align: center;">Qtd de frascos comprados/mês:</label>
            <input type="number" id="qtdMes" placeholder="0" oninput="calcular()">
        </div>
        <div class="sim-grid">
            <div class="sim-item">
                Elleva (210mg)
                <strong id="ecoMesElleva">R$ 0,00</strong>
                <span style="font-size: 0.7rem; display: block; margin-top:5px;">Economia Anual: <span id="ecoAnoElleva">R$ 0,00</span></span>
            </div>
            <div class="sim-item">
                Elleva X (630mg)
                <strong id="ecoMesEllevaX">R$ 0,00</strong>
                <span style="font-size: 0.7rem; display: block; margin-top:5px;">Economia Anual: <span id="ecoAnoEllevaX">R$ 0,00</span></span>
            </div>
            <div class="sim-item">
                Elleva 150 (150mg)
                <strong id="ecoMesElleva150">R$ 0,00</strong>
                <span style="font-size: 0.7rem; display: block; margin-top:5px;">Economia Anual: <span id="ecoAnoElleva150">R$ 0,00</span></span>
            </div>
        </div>
    </div>
</div>

<script>
    function format(val) {
        return val.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' });
    }

    function calcular() {
        const pConc = parseFloat(document.getElementById('inputConcorrente').value) || 0;
        const pE210 = parseFloat(document.getElementById('inputElleva').value) || 0;
        const pEX = parseFloat(document.getElementById('inputEllevaX').value) || 0;
        const pE150 = parseFloat(document.getElementById('inputElleva150').value) || 0;
        const qtd = parseFloat(document.getElementById('qtdMes').value) || 0;

        // Custos equivalentes baseados na volumetria
        const vConcE210 = pConc * 1.4;
        const vConcEX = pConc * 4.2;
        const vConcE150 = pConc * 1.0;

        document.getElementById('custoFinalConcElleva').innerText = format(vConcE210);
        document.getElementById('custoFinalConcEllevaX').innerText = format(vConcEX);
        document.getElementById('custoFinalConcElleva150').innerText = format(vConcE150);

        // Vantagem por frasco
        const vanteE210 = vConcE210 - pE210;
        const vanteEX = vConcEX - pEX;
        const vanteE150 = vConcE150 - pE150;

        document.getElementById('vantagemElleva').innerText = format(vanteE210);
        document.getElementById('vantagemEllevaX').innerText = format(vanteEX);
        document.getElementById('vantagemElleva150').innerText = format(vanteE150);

        // Economia Mensal e Anual
        document.getElementById('ecoMesElleva').innerText = format(vanteE210 * qtd);
        document.getElementById('ecoAnoElleva').innerText = format(vanteE210 * qtd * 12);
        document.getElementById('ecoMesEllevaX').innerText = format(vanteEX * qtd);
        document.getElementById('ecoAnoEllevaX').innerText = format(vanteEX * qtd * 12);
        document.getElementById('ecoMesElleva150').innerText = format(vanteE150 * qtd);
        document.getElementById('ecoAnoElleva150').innerText = format(vanteE150 * qtd * 12);
    }
</script>

</body>
</html>
