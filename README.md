<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ORION App - Motorista</title>
    <style>
        :root {
            --bg-color: #f3f4f6;
            --card-bg: #ffffff;
            --primary: #2563eb;
            --success: #16a34a;
            --danger: #dc2626;
            --text-main: #1f2937;
            --text-light: #6b7280;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background-color: #d1d5db;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        /* Simulação da tela do celular */
        .mobile-container {
            width: 375px;
            height: 812px;
            background-color: var(--bg-color);
            border-radius: 30px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            position: relative;
            border: 8px solid #1f2937;
        }

        /* Cabeçalho */
        .header {
            background-color: #1f2937;
            color: white;
            padding: 20px;
            text-align: center;
        }

        .driver-info {
            font-size: 1.2rem;
            font-weight: bold;
        }

        .truck-info {
            font-size: 0.85rem;
            color: #9ca3af;
            margin-top: 5px;
        }

        .status-badge {
            display: inline-block;
            margin-top: 10px;
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 0.8rem;
            font-weight: bold;
            background-color: var(--primary);
        }

        /* Conteúdo Principal */
        .content {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
        }

        /* Cartão de Próxima Parada */
        .card {
            background-color: var(--card-bg);
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }

        .card-title {
            font-size: 0.9rem;
            color: var(--text-light);
            text-transform: uppercase;
            margin-bottom: 10px;
        }

        .destination {
            font-size: 1.3rem;
            font-weight: bold;
            color: var(--text-main);
            margin-bottom: 5px;
        }

        .metrics {
            display: flex;
            justify-content: space-between;
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px solid #e5e7eb;
        }

        .metric-item strong {
            display: block;
            font-size: 1.1rem;
            color: var(--text-main);
        }

        .metric-item span {
            font-size: 0.8rem;
            color: var(--text-light);
        }

        /* Mapa Simulado */
        .map-placeholder {
            height: 200px;
            background-color: #e5e7eb;
            border-radius: 12px;
            display: flex;
            justify-content: center;
            align-items: center;
            color: var(--text-light);
            margin-bottom: 15px;
            border: 2px dashed #9ca3af;
            font-weight: bold;
        }

        /* Botões de Ação */
        .btn {
            width: 100%;
            padding: 15px;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: bold;
            color: white;
            margin-bottom: 10px;
            cursor: pointer;
            transition: opacity 0.2s;
        }

        .btn:active {
            opacity: 0.8;
        }

        .btn-success { background-color: var(--success); }
        .btn-danger { background-color: var(--danger); }
        .btn-primary { background-color: var(--primary); }

        /* Barra de Navegação Inferior */
        .bottom-nav {
            background-color: white;
            display: flex;
            justify-content: space-around;
            padding: 15px 0;
            border-top: 1px solid #e5e7eb;
        }

        .nav-item {
            text-align: center;
            color: var(--text-light);
            font-size: 0.8rem;
            font-weight: bold;
            cursor: pointer;
        }

        .nav-item.active {
            color: var(--primary);
        }
    </style>
</head>
<body>

    <div class="mobile-container">
        <div class="header">
            <div class="driver-info">Christian Sampaio</div>
            <div class="truck-info">Placa: ABC-1234 | Veículo Pesado</div>
            <div id="statusBadge" class="status-badge">EM TRÂNSITO</div>
        </div>

        <div class="content">
            
            <div class="map-placeholder">
                [Navegação GPS Ativa]
            </div>

            <div class="card">
                <div class="card-title">Próxima Entrega (Carga #4092)</div>
                <div class="destination" id="currentDestination">Centro de Distribuição - SP</div>
                <p style="font-size: 0.9rem; color: var(--text-light);">Av. Paulista, 1000</p>
                
                <div class="metrics">
                    <div class="metric-item">
                        <strong id="distance">45 km</strong>
                        <span>Distância</span>
                    </div>
                    <div class="metric-item">
                        <strong id="time">50 min</strong>
                        <span>Tempo Est.</span>
                    </div>
                </div>
            </div>

            <button class="btn btn-success" onclick="confirmDelivery()">Confirmar Entrega</button>
            <button class="btn btn-primary" onclick="registerPause()">Registrar Pausa (Jornada)</button>
            <button class="btn btn-danger" onclick="reportIssue()">Reportar Ocorrência</button>

        </div>

        <div class="bottom-nav">
            <div class="nav-item active">Rota</div>
            <div class="nav-item">Cargas</div>
            <div class="nav-item">Chat</div>
            <div class="nav-item">Perfil</div>
        </div>
    </div>

    <script>
        function confirmDelivery() {
            const confirm = window.confirm("Confirmar a entrega da Carga #4092?");
            if (confirm) {
                alert("Entrega confirmada. O PLIM calculará a rota para o próximo destino.");
                document.getElementById('currentDestination').innerText = "Filial Campinas - SP";
                document.getElementById('distance').innerText = "90 km";
                document.getElementById('time').innerText = "1h 20m";
            }
        }

        function registerPause() {
            const badge = document.getElementById('statusBadge');
            if (badge.innerText === "EM TRÂNSITO") {
                badge.innerText = "EM PAUSA";
                badge.style.backgroundColor = "#f59e0b"; // Amarelo
                alert("Pausa registrada com sucesso no sistema. (Requisito RF-04 cumprido)");
            } else {
                badge.innerText = "EM TRÂNSITO";
                badge.style.backgroundColor = "var(--primary)";
                alert("Jornada retomada.");
            }
        }

        function reportIssue() {
            const issue = window.prompt("Descreva a ocorrência (Ex: Pneu furado, Trânsito severo):");
            if (issue) {
                alert("Ocorrência enviada ao Gerente. A Meta-Heurística irá recalcular a rota se necessário.");
                document.getElementById('statusBadge').innerText = "ALERTA ENVIADO";
                document.getElementById('statusBadge').style.backgroundColor = "var(--danger)";
            }
        }
    </script>
</body>
</html>
