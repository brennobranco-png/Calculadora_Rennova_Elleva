# Calculadora_Rennova_Elleva
Calculadora de rentabilidade Rennova Elleva
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Rentabilidade - Linha Elleva</title>
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
            max-width: 250px;
            height: auto;
        }

        h1 {
            color: var(--primary-blue);
            font-size: 1.4rem;
            margin-top: 10px;
        }

        /* Seção de Entrada do Concorrente */
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

        /* Grid de Produtos */
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
            height: 180px;
            object-fit: contain;
            margin-bottom: 15px;
        }

        .product-name {
            font-size: 1.2rem;
            font-weight: bold;
            color: var(--primary-blue);
            text-align: center;
            margin-bottom: 15px;
            min-height: 50px;
        }

        .info-row {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px solid #EEE;
            font-size: 0.95rem;
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

        /* Parte 2: Simulação Azul */
        .simulation-section {
            background-color: var(--primary-blue);
            color: var(--white);
            padding: 30px;
            border-radius: 15px;
            margin-top: 20px;
        }

        .simulation-section h2 {
            margin-top: 0;
            text-align: center;
            font-size: 1.3rem;
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
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
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
            font-size: 0.8rem;
        }

    </style>
</head>
<body>

<div class="container">
    <header>
        <img src="https://equilibriumdistribuidora.sharepoint.com/sites/MarketingProdutosRennova/Shared%20Documents/Marketing%20Produtos%20Rennova/01.%20Marcas,%20logo,%20KV/LOGOS%20PRODUTOS/LOGOS_RENNOVA_Elleva-210.png" alt="Rennova" class="logo">
        <h1>Calculadora de Rentabilidade Elleva</h1>
    </header>

    <div class="card-concorrente">
        <label>Preço de compra do Concorrente (150mg):</label>
        <input type="number" id="inputConcorrente" placeholder="R$ 0,00" oninput="calcular()">
    </div>

    <div class="products-grid">
        
        <div class="product-card">
            <img src="https://equilibriumdistribuidora.sharepoint.com/sites/MarketingProdutosRennova/Shared%20Documents/Marketing%20Produtos%20Rennova/01.%20Marcas,%20logo,%20KV/Bioestimuladores/Elleva%20e%20Elleva%20X/MOCKUPS%20ELLEVA/03_frasco_caixa%20(1).png" class="product-img">
            <div class="product-name">Rennova Elleva <span class="badge-mg">210mg</span></div>
            
            <label>Preço Elleva:</label>
            <input type="number" id="inputElleva" placeholder="R$ 0,00" oninput="calcular()">
            
            <div class="info-row" style="margin-top:15px;">
                <span>Equivalência:</span>
                <span><strong>1,4 frascos</strong> (40% a mais)</span>
            </div>
            <div class="info-row">
                <span>Custo Concorrente p/ 210mg:</span>
                <span id="custoFinalConcElleva">R$ 0,00</span>
            </div>
            <div class="highlight-box">
                <div>Vantagem Financeira p/ Frasco:</div>
                <div class="savings" id="vantagemElleva">R$ 0,00</div>
            </div>
        </div>

        <div class="product-card">
            <img src="https://equilibriumdistribuidora.sharepoint.com/sites/MarketingProdutosRennova/Shared%20Documents/Marketing%20Produtos%20Rennova/01.%20Marcas,%20logo,%20KV/Bioestimuladores/Elleva%20e%20Elleva%20X/MOCKUPS%20ELLEVA%20X/MOCKUP_3D_CARTUCHO_SECUND_E_AMPOLA_RENNOVA_ELLEVA_PROPOSTAS03_CENA_01-Exibi%C3%A7%C3%A3o%20atual.png" class="product-img">
            <div class="product-name">Rennova Elleva X <span class="badge-mg">630mg</span></div>
            
            <label>Preço Elleva X:</label>
            <input type="number" id="inputEllevaX" placeholder="R$ 0,00" oninput="calcular()">
            
            <div class="info-row" style="margin-top:15px;">
                <span>Equivalência:</span>
                <span><strong>4,2 frascos</strong> (320% a mais)</span>
            </div>
            <div class="info-row">
                <span>Custo Concorrente p/ 630mg:</span>
                <span id="custoFinalConcEllevaX">R$ 0,00</span>
            </div>
            <div class="highlight-box">
                <div>Vantagem Financeira p/ Frasco:</div>
                <div class="savings" id="vantagemEllevaX">R$ 0,00</div>
            </div>
        </div>

        <div class="product-card">
            <img src="https://equilibriumdistribuidora.sharepoint.com/sites/MarketingProdutosRennova/Shared%20Documents/Marketing%20Produtos%20Rennova/Projetos%20-%20Bioestimuladores/01.%20Produtos/1.%20Rennova%20Elleva/KV/MOCKUP_ELLEVA150/cxa%20e%20ampola%20com%20chao%20-%20cx%20lado.png" class="product-img">
            <div class="product-name">Rennova Elleva 150 <span class="badge-mg">150mg</span></div>
            
            <label>Preço Elleva 150:</label>
            <input type="number" id="inputElleva150" placeholder="R$ 0,00" oninput="calcular()">
            
            <div class="info-row" style="margin-top:15px;">
                <span>Equivalência:</span>
                <span><strong>1,0 frasco</strong> (Igual)</span>
            </div>
            <div class="info-row">
                <span>Custo Concorrente p/ 150mg:</span>
                <span id="custoFinalConcElleva150">R$ 0,00</span>
            </div>
            <div class="highlight-box">
                <div>Vantagem Financeira p/ Frasco:</div>
                <div class="savings" id="vantagemElleva150">R$ 0,00</div>
            </div>
        </div>

    </div>

    <div class="simulation-section">
        <h2>Simulação de Consumo Mensal</h2>
        
        <div class="input-monthly">
            <label style="color: white; text-align: center;">Quantidade de frascos comprados/mês:</label>
            <input type="number" id="qtdMes" placeholder="0" oninput="calcular()">
        </div>

        <div class="sim-grid">
            <div class="sim-item">
                Elleva (210mg)
                <span style="display:block; font-size: 0.8rem;">Economia Mensal</span>
                <strong id="ecoMesElleva">R$ 0,00</strong>
                <span style="display:block; font-size: 0.8rem; margin-top:5px;">Economia Anual</span>
                <strong id="ecoAnoElleva">R$ 0,00</strong>
            </div>
            <div class="sim-item">
                Elleva X (630mg)
                <span style="display:block; font-size: 0.8rem;">Economia Mensal</span>
                <strong id="ecoMesEllevaX">R$ 0,00</strong>
                <span style="display:block; font-size: 0.8rem; margin-top:5px;">Economia Anual</span>
                <strong id="ecoAnoEllevaX">R$ 0,00</strong>
            </div>
            <div class="sim-item">
                Elleva 150 (150mg)
                <span style="display:block; font-size: 0.8rem;">Economia Mensal</span>
                <strong id="ecoMesElleva150">R$ 0,00</strong>
                <span style="display:block; font-size: 0.8rem; margin-top:5px;">Economia Anual</span>
                <strong id="ecoAnoElleva150">R$ 0,00</strong>
            </div>
        </div>
    </div>
</div>

<script>
    function format(val) {
        return val.toLocaleString('pt-br', { style: 'currency', currency: 'BRL' });
    }

    function calcular() {
        // Inputs
        const pConc = parseFloat(document.getElementById('inputConcorrente').value) || 0;
        const pE210 = parseFloat(document.getElementById('inputElleva').value) || 0;
        const pEX = parseFloat(document.getElementById('inputEllevaX').value) || 0;
        const pE150 = parseFloat(document.getElementById('inputElleva150').value) || 0;
        const qtd = parseFloat(document.getElementById('qtdMes').value) || 0;

        // Cálculos de Equivalência (Valor Final Custo Concorrente)
        const vConcE210 = pConc * 1.4;
        const vConcEX = pConc * 4.2;
        const vConcE150 = pConc * 1.0;

        document.getElementById('custoFinalConcElleva').innerText = format(vConcE210);
        document.getElementById('custoFinalConcEllevaX').innerText = format(vConcEX);
        document.getElementById('custoFinalConcElleva150').innerText = format(vConcE150);

        // Vantagem Financeira por Frasco
        const vanteE210 = vConcE210 - pE210;
        const vanteEX = vConcEX - pEX;
        const vanteE150 = vConcE150 - pE150;

        document.getElementById('vantagemElleva').innerText = format(vanteE210);
        document.getElementById('vantagemEllevaX').innerText = format(vanteEX);
        document.getElementById('vantagemElleva150').innerText = format(vanteE150);

        // Simulação Mensal (Fórmula pedida)
        // (Valor Final Custo Concorrente x Média Qtd) - (Preço Unidade Elleva x Média Qtd)
        
        const ecoME210 = (vConcE210 * qtd) - (pE210 * qtd);
        const ecoMEX = (vConcEX * qtd) - (pEX * qtd);
        const ecoME150 = (vConcE150 * qtd) - (pE150 * qtd);

        document.getElementById('ecoMesElleva').innerText = format(ecoME210);
        document.getElementById('ecoAnoElleva').innerText = format(ecoME210 * 12);

        document.getElementById('ecoMesEllevaX').innerText = format(ecoMEX);
        document.getElementById('ecoAnoEllevaX').innerText = format(ecoMEX * 12);

        document.getElementById('ecoMesElleva150').innerText = format(ecoME150);
        document.getElementById('ecoAnoElleva150').innerText = format(ecoME150 * 12);
    }
</script>

</body>
</html>
