
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema ORION | Painel Gerencial</title>
    <style>
        :root {
            --primary-bg: #f4f7f6;
            --sidebar-bg: #111827;
            --card-bg: #ffffff;
            --accent-color: #3b82f6;
            --text-main: #1f2937;
            --text-light: #9ca3af;
            --success: #10b981;
            --danger: #ef4444;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            display: flex;
            height: 100vh;
            background-color: var(--primary-bg);
            color: var(--text-main);
        }

        /* Sidebar */
        .sidebar {
            width: 250px;
            background-color: var(--sidebar-bg);
            color: white;
            display: flex;
            flex-direction: column;
        }

        .sidebar-header {
            padding: 20px;
            font-size: 1.5rem;
            font-weight: bold;
            border-bottom: 1px solid #374151;
            text-align: center;
            letter-spacing: 2px;
        }

        .sidebar-header span {
            color: var(--accent-color);
        }

        .nav-links {
            list-style: none;
            padding: 20px 0;
        }

        .nav-links li {
            padding: 15px 20px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .nav-links li:hover, .nav-links li.active {
            background-color: #1f2937;
            border-left: 4px solid var(--accent-color);
        }

        /* Main Content */
        .main-content {
            flex: 1;
            padding: 30px;
            overflow-y: auto;
        }

        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }

        .header h1 {
            font-size: 1.8rem;
        }

        .user-info {
            font-weight: 600;
        }

        /* KPI Cards */
        .kpi-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .card {
            background-color: var(--card-bg);
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
        }

        .card h3 {
            font-size: 0.9rem;
            color: var(--text-light);
            margin-bottom: 10px;
            text-transform: uppercase;
        }

        .card .value {
            font-size: 1.8rem;
            font-weight: bold;
        }

        .card .positive { color: var(--success); }
        .card .negative { color: var(--danger); }

        /* Map & Controls Area */
        .dashboard-grid {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 20px;
        }

        .map-container, .action-container {
            background-color: var(--card-bg);
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
        }

        .map-placeholder {
            width: 100%;
            height: 300px;
            background-color: #e5e7eb;
            border: 2px dashed #9ca3af;
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-light);
            font-weight: bold;
            margin-top: 15px;
        }

        .btn {
            display: block;
            width: 100%;
            padding: 12px;
            background-color: var(--accent-color);
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            margin-top: 15px;
            transition: background 0.3s;
        }

        .btn:hover {
            background-color: #2563eb;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }

        th, td {
            text-align: left;
            padding: 10px;
            border-bottom: 1px solid #e5e7eb;
        }

        th {
            color: var(--text-light);
            font-size: 0.85rem;
            text-transform: uppercase;
        }

        .status-badge {
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 0.8rem;
            font-weight: bold;
        }

        .status-ok { background-color: #d1fae5; color: #065f46; }
        .status-alert { background-color: #fee2e2; color: #991b1b; }
    </style>
</head>
<body>

    <aside class="sidebar">
        <div class="sidebar-header">
            SISTEMA <span>ORION</span>
        </div>
        <ul class="nav-links">
            <li class="active">Painel Gerencial</li>
            <li>Otimizador de Rotas (IA)</li>
            <li>Gestão de Cargas</li>
            <li>Monitoramento de Frota</li>
            <li>Relatórios e BI</li>
        </ul>
    </aside>

    <main class="main-content">
        <header class="header">
            <h1>Visão Geral da Operação</h1>
            <div class="user-info">
                Gerente de Logística | Transportadora Flávio
            </div>
        </header>

        <section class="kpi-grid">
            <div class="card">
                <h3>Rotas Ativas</h3>
                <div class="value">24</div>
            </div>
            <div class="card">
                <h3>Economia Estimada (Mês)</h3>
                <div class="value positive">R$ 120.400,00</div>
            </div>
            <div class="card">
                <h3>Eficiência Algorítmica (PLIM)</h3>
                <div class="value">98.5%</div>
            </div>
            <div class="card">
                <h3>Alertas de Risco</h3>
                <div class="value negative">1</div>
            </div>
        </section>

        <section class="dashboard-grid">
            <div class="map-container">
                <h2>Rastreamento e Rotas (Tempo Real)</h2>
                
                <div class="map-placeholder">
                    Integração com API de Mapas / Meta-Heurística Ativa
                </div>
            </div>

            <div class="action-container">
                <h2>Painel de Otimização</h2>
                <p style="color: var(--text-light); font-size: 0.9rem; margin-top: 10px;">
                    O motor de Inteligência Artificial está pronto para processar novas variáveis de tráfego e peso.
                </p>
                <button class="btn" onclick="alert('Iniciando processamento via PLIM e Meta-Heurísticas. Aguarde o cálculo do Ótimo Local...')">Executar Otimização (RF-01)</button>
                
                <h3 style="margin-top: 30px; font-size: 1rem;">Veículos em Destaque</h3>
                <table>
                    <tr>
                        <th>Placa</th>
                        <th>Destino</th>
                        <th>Status</th>
                    </tr>
                    <tr>
                        <td>ABC-1234</td>
                        <td>São Paulo, SP</td>
                        <td><span class="status-badge status-ok">No Prazo</span></td>
                    </tr>
                    <tr>
                        <td>XYZ-9876</td>
                        <td>Belo Horizonte, MG</td>
                        <td><span class="status-badge status-alert">Re-roteando</span></td>
                    </tr>
                </table>
            </div>
        </section>
    </main>

</body>
</html>
