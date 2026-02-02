<!DOCTYPE html>
<html lang="fr" dir="ltr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculateur de Moteur Électrique | حاسبة المحركات الكهربائية | Motor Calculator</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --accent-color: #e74c3c;
            --light-color: #ecf0f1;
            --dark-color: #2c3e50;
            --success-color: #2ecc71;
            --warning-color: #f39c12;
            --border-radius: 8px;
            --box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
            transition: all 0.3s ease;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Header Styles */
        header {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 20px 0;
            border-radius: var(--border-radius);
            margin-bottom: 30px;
            box-shadow: var(--box-shadow);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 20px;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo i {
            font-size: 2.5rem;
            color: #fff;
        }

        .logo h1 {
            font-size: 1.8rem;
            font-weight: 700;
        }

        /* Language Selector */
        .language-selector {
            display: flex;
            gap: 10px;
        }

        .lang-btn {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 1px solid rgba(255, 255, 255, 0.3);
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: 600;
        }

        .lang-btn.active {
            background: white;
            color: var(--primary-color);
        }

        .lang-btn:hover {
            background: rgba(255, 255, 255, 0.3);
        }

        /* Main Content */
        .app-description {
            background-color: white;
            padding: 20px;
            border-radius: var(--border-radius);
            margin-bottom: 25px;
            box-shadow: var(--box-shadow);
            text-align: center;
            border-left: 5px solid var(--secondary-color);
        }

        .app-description h2 {
            color: var(--primary-color);
            margin-bottom: 10px;
        }

        .app-description p {
            color: #555;
        }

        .main-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
        }

        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }

        /* Input and Output Sections */
        .section {
            background-color: white;
            border-radius: var(--border-radius);
            padding: 25px;
            box-shadow: var(--box-shadow);
            height: fit-content;
        }

        .section-title {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--light-color);
            color: var(--primary-color);
        }

        .section-title i {
            color: var(--secondary-color);
        }

        .section-title h3 {
            font-size: 1.4rem;
        }

        /* Input Groups */
        .input-group {
            margin-bottom: 20px;
        }

        .input-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--dark-color);
        }

        .input-group input, 
        .input-group select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: var(--border-radius);
            font-size: 1rem;
            transition: border 0.3s;
        }

        .input-group input:focus, 
        .input-group select:focus {
            border-color: var(--secondary-color);
            outline: none;
        }

        .unit-selector {
            display: flex;
            margin-bottom: 10px;
            border-radius: var(--border-radius);
            overflow: hidden;
            width: fit-content;
        }

        .unit-btn {
            padding: 8px 15px;
            background-color: #f1f1f1;
            border: 1px solid #ddd;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
        }

        .unit-btn.active {
            background-color: var(--secondary-color);
            color: white;
            border-color: var(--secondary-color);
        }

        .unit-btn:first-child {
            border-radius: var(--border-radius) 0 0 var(--border-radius);
        }

        .unit-btn:last-child {
            border-radius: 0 var(--border-radius) var(--border-radius) 0;
        }

        .input-with-unit {
            display: flex;
            align-items: center;
        }

        .input-with-unit input {
            flex: 1;
            border-radius: var(--border-radius) 0 0 var(--border-radius);
        }

        .unit-display {
            background-color: #f1f1f1;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-left: none;
            border-radius: 0 var(--border-radius) var(--border-radius) 0;
            font-weight: 600;
            min-width: 60px;
            text-align: center;
        }

        /* Results */
        .result-item {
            background-color: #f9f9f9;
            padding: 15px;
            border-radius: var(--border-radius);
            margin-bottom: 15px;
            border-left: 4px solid var(--secondary-color);
        }

        .result-title {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 5px;
        }

        .result-title h4 {
            font-size: 1.1rem;
            color: var(--primary-color);
        }

        .result-value {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--secondary-color);
            text-align: right;
        }

        .result-unit {
            font-size: 0.9rem;
            color: #777;
            font-weight: 600;
        }

        .result-note {
            font-size: 0.85rem;
            color: #666;
            margin-top: 5px;
            font-style: italic;
        }

        /* Special Features */
        .features-section {
            grid-column: 1 / -1;
            margin-top: 20px;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .feature-card {
            background-color: white;
            border-radius: var(--border-radius);
            padding: 20px;
            box-shadow: var(--box-shadow);
            transition: transform 0.3s;
        }

        .feature-card:hover {
            transform: translateY(-5px);
        }

        .feature-card h4 {
            color: var(--primary-color);
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .feature-card h4 i {
            color: var(--accent-color);
        }

        /* Buttons */
        .calculate-btn {
            background: linear-gradient(to right, var(--secondary-color), #2980b9);
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.1rem;
            font-weight: 600;
            border-radius: var(--border-radius);
            cursor: pointer;
            transition: all 0.3s;
            width: 100%;
            margin-top: 10px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
        }

        .calculate-btn:hover {
            background: linear-gradient(to right, #2980b9, var(--secondary-color));
            box-shadow: 0 5px 15px rgba(52, 152, 219, 0.3);
        }

        .action-buttons {
            display: flex;
            gap: 15px;
            margin-top: 25px;
        }

        .action-btn {
            flex: 1;
            padding: 12px;
            border-radius: var(--border-radius);
            border: none;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
        }

        .export-btn {
            background-color: var(--success-color);
            color: white;
        }

        .export-btn:hover {
            background-color: #27ae60;
        }

        .reset-btn {
            background-color: var(--warning-color);
            color: white;
        }

        .reset-btn:hover {
            background-color: #e67e22;
        }

        /* Connection Diagram */
        .diagram-container {
            background-color: white;
            border-radius: var(--border-radius);
            padding: 20px;
            margin-top: 30px;
            box-shadow: var(--box-shadow);
            text-align: center;
        }

        .diagram-title {
            color: var(--primary-color);
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .diagram {
            width: 100%;
            max-width: 400px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f9f9f9;
            border-radius: var(--border-radius);
        }

        .motor-terminal {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--accent-color);
        }

        /* Footer */
        footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            color: #666;
            font-size: 0.9rem;
            border-top: 1px solid #ddd;
        }

        .highlight {
            color: var(--secondary-color);
            font-weight: 600;
        }

        /* Responsive adjustments */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
                text-align: center;
            }
            
            .features-grid {
                grid-template-columns: 1fr;
            }
            
            .action-buttons {
                flex-direction: column;
            }
        }

        /* Animation for results */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .result-item {
            animation: fadeIn 0.5s ease-out;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="header-content">
                <div class="logo">
                    <i class="fas fa-cogs"></i>
                    <h1 id="app-title">Calculateur de Moteur Électrique</h1>
                </div>
                <div class="language-selector">
                    <button class="lang-btn active" data-lang="fr">FR</button>
                    <button class="lang-btn" data-lang="ar">العربية</button>
                    <button class="lang-btn" data-lang="en">EN</button>
                </div>
            </div>
        </header>

        <div class="app-description">
            <h2 id="description-title">Calculateur professionnel pour la sélection des composants de commande de moteur</h2>
            <p id="description-text">Cet outil calcule les paramètres électriques, les courants de démarrage et sélectionne les composants appropriés (disjoncteurs, contacteurs, relais de surcharge) en fonction des données de la plaque signalétique du moteur et des conditions de fonctionnement.</p>
        </div>

        <div class="main-content">
            <!-- Input Section -->
            <section class="section">
                <div class="section-title">
                    <i class="fas fa-keyboard"></i>
                    <h3 id="input-title">Données d'entrée</h3>
                </div>

                <!-- Motor Nameplate Data -->
                <h4 id="nameplate-title" style="margin-bottom: 15px; color: var(--primary-color);"><i class="fas fa-plate"></i> Données de la plaque signalétique</h4>
                
                <!-- Power Input -->
                <div class="input-group">
                    <label id="power-label">Puissance mécanique nominale</label>
                    <div class="unit-selector">
                        <button class="unit-btn active" data-unit="kW">kW</button>
                        <button class="unit-btn" data-unit="HP">HP</button>
                    </div>
                    <div class="input-with-unit">
                        <input type="number" id="power-input" min="0" step="0.1" value="15">
                        <div class="unit-display" id="power-unit">kW</div>
                    </div>
                </div>

                <!-- Voltage Input -->
                <div class="input-group">
                    <label id="voltage-label">Tension nominale (V)</label>
                    <input type="number" id="voltage-input" min="0" value="400">
                </div>

                <!-- Power Factor Input -->
                <div class="input-group">
                    <label id="pf-label">Facteur de puissance (cos φ)</label>
                    <input type="number" id="pf-input" min="0.1" max="1" step="0.01" value="0.85">
                </div>

                <!-- Efficiency Input -->
                <div class="input-group">
                    <label id="efficiency-label">Rendement (η)</label>
                    <input type="number" id="efficiency-input" min="0.1" max="1" step="0.01" value="0.92">
                </div>

                <!-- Frequency Input -->
                <div class="input-group">
                    <label id="frequency-label">Fréquence (Hz)</label>
                    <select id="frequency-select">
                        <option value="50">50 Hz</option>
                        <option value="60">60 Hz</option>
                    </select>
                </div>

                <!-- Poles/Speed Input -->
                <div class="input-group">
                    <label id="poles-label">Nombre de pôles</label>
                    <select id="poles-select">
                        <option value="2">2 pôles (~3000 RPM)</option>
                        <option value="4" selected>4 pôles (~1500 RPM)</option>
                        <option value="6">6 pôles (~1000 RPM)</option>
                        <option value="8">8 pôles (~750 RPM)</option>
                    </select>
                </div>

                <!-- Operating Conditions -->
                <h4 id="conditions-title" style="margin: 25px 0 15px; color: var(--primary-color);"><i class="fas fa-industry"></i> Conditions de fonctionnement</h4>
                
                <!-- Load Type -->
                <div class="input-group">
                    <label id="load-label">Type de charge</label>
                    <select id="load-select">
                        <option value="light" id="load-light">Légère (ventilateurs, pompes)</option>
                        <option value="medium" selected id="load-medium">Moyenne (convoyeurs, compresseurs)</option>
                        <option value="heavy" id="load-heavy">Lourde (broyeurs, concasseurs)</option>
                    </select>
                </div>

                <!-- Cable Length -->
                <div class="input-group">
                    <label id="cable-label">Longueur du câble (m)</label>
                    <input type="number" id="cable-length" min="0" value="50">
                </div>

                <!-- Starting Method -->
                <div class="input-group">
                    <label id="start-method-label">Méthode de démarrage</label>
                    <select id="start-method">
                        <option value="DOL" id="start-dol">DOL (Direct-On-Line)</option>
                        <option value="star-delta" selected id="start-star">Démarrage étoile-triangle</option>
                        <option value="soft" id="start-soft">Démarreur progressif</option>
                        <option value="vfd" id="start-vfd">Variateur de fréquence (VFD)</option>
                    </select>
                </div>

                <!-- Temperature -->
                <div class="input-group">
                    <label id="temp-label">Température ambiante (°C)</label>
                    <input type="number" id="temperature" min="-10" max="50" value="30">
                </div>

                <!-- Power Factor Correction -->
                <div class="input-group">
                    <label id="pf-target-label">Facteur de puissance cible</label>
                    <input type="number" id="pf-target" min="0.8" max="1" step="0.01" value="0.95">
                </div>

                <button class="calculate-btn" id="calculate-btn">
                    <i class="fas fa-calculator"></i>
                    <span id="calculate-text">Calculer les paramètres</span>
                </button>
            </section>

            <!-- Output Section -->
            <section class="section">
                <div class="section-title">
                    <i class="fas fa-chart-line"></i>
                    <h3 id="output-title">Résultats de calcul</h3>
                </div>

                <!-- Electrical Analysis Results -->
                <h4 id="analysis-title" style="margin-bottom: 15px; color: var(--primary-color);"><i class="fas fa-bolt"></i> Analyse électrique</h4>
                
                <div class="result-item">
                    <div class="result-title">
                        <h4 id="current-label">Courant nominal (pleine charge)</h4>
                        <div class="result-value" id="full-load-current">27.36</div>
                    </div>
                    <div class="result-unit">A</div>
                    <div class="result-note" id="current-note">Courant à pleine charge basé sur la puissance nominale</div>
                </div>

                <div class="result-item">
                    <div class="result-title">
                        <h4 id="apparent-power-label">Puissance apparente</h4>
                        <div class="result-value" id="apparent-power">18.95</div>
                    </div>
                    <div class="result-unit">kVA</div>
                </div>

                <div class="result-item">
                    <div class="result-title">
                        <h4 id="reactive-power-label">Puissance réactive</h4>
                        <div class="result-value" id="reactive-power">9.81</div>
                    </div>
                    <div class="result-unit">kVAR</div>
                </div>

                <div class="result-item">
                    <div class="result-title">
                        <h4 id="start-current-label">Courant de démarrage</h4>
                        <div class="result-value" id="starting-current">95.76</div>
                    </div>
                    <div class="result-unit">A</div>
                    <div class="result-note" id="start-current-note">Basé sur la méthode de démarrage sélectionnée</div>
                </div>

                <!-- Component Selection Results -->
                <h4 id="components-title" style="margin: 25px 0 15px; color: var(--primary-color);"><i class="fas fa-tools"></i> Sélection des composants</h4>
                
                <div class="result-item">
                    <div class="result-title">
                        <h4 id="breaker-label">Disjoncteur (Courbe D)</h4>
                        <div class="result-value" id="breaker-size">40</div>
                    </div>
                    <div class="result-unit">A</div>
                    <div class="result-note" id="breaker-note">Capacité nominale recommandée</div>
                </div>

                <div class="result-item">
                    <div class="result-title">
                        <h4 id="contactor-label">Contacteur (AC-3)</h4>
                        <div class="result-value" id="contactor-size">32</div>
                    </div>
                    <div class="result-unit">A</div>
                </div>

                <div class="result-item">
                    <div class="result-title">
                        <h4 id="overload-label">Relais de surcharge</h4>
                        <div class="result-value" id="overload-range">25 - 32</div>
                    </div>
                    <div class="result-unit">A</div>
                    <div class="result-note" id="overload-note">Réglage recommandé: 1.15 × I<sub>fl</sub></div>
                </div>

                <div class="result-item">
                    <div class="result-title">
                        <h4 id="cable-label-output">Section du câble Cu</h4>
                        <div class="result-value" id="cable-size">6</div>
                    </div>
                    <div class="result-unit">mm²</div>
                    <div class="result-note" id="cable-note">Basé sur 50m de longueur et chute de tension &lt;3%</div>
                </div>

                <div class="result-item">
                    <div class="result-title">
                        <h4 id="voltage-drop-label">Chute de tension</h4>
                        <div class="result-value" id="voltage-drop">2.14</div>
                    </div>
                    <div class="result-unit">%</div>
                </div>

                <div class="result-item">
                    <div class="result-title">
                        <h4 id="capacitor-label">Condensateur de correction</h4>
                        <div class="result-value" id="capacitor-value">4.2</div>
                    </div>
                    <div class="result-unit">kVAR</div>
                    <div class="result-note" id="capacitor-note">Pour améliorer le facteur de puissance à 0.95</div>
                </div>

                <div class="action-buttons">
                    <button class="action-btn export-btn" id="export-btn">
                        <i class="fas fa-file-pdf"></i>
                        <span id="export-text">Exporter PDF</span>
                    </button>
                    <button class="action-btn reset-btn" id="reset-btn">
                        <i class="fas fa-redo"></i>
                        <span id="reset-text">Réinitialiser</span>
                    </button>
                </div>
            </section>

            <!-- Advanced Features Section -->
            <section class="section features-section">
                <div class="section-title">
                    <i class="fas fa-star"></i>
                    <h3 id="features-title">Fonctionnalités avancées</h3>
                </div>

                <div class="features-grid">
                    <div class="feature-card">
                        <h4><i class="fas fa-exchange-alt"></i> <span id="conversion-title">Conversion d'unités</span></h4>
                        <p id="conversion-text">Conversion automatique entre kW et HP avec un seul clic. Prend en charge les unités métriques et impériales.</p>
                        <div style="margin-top: 15px; display: flex; gap: 10px;">
                            <input type="number" id="conversion-input" style="flex: 1; padding: 8px;" value="15">
                            <select id="conversion-from" style="padding: 8px;">
                                <option value="kW">kW</option>
                                <option value="HP">HP</option>
                            </select>
                            <button id="convert-btn" style="padding: 8px 15px; background-color: var(--secondary-color); color: white; border: none; border-radius: var(--border-radius); cursor: pointer;">
                                <i class="fas fa-sync-alt"></i>
                            </button>
                            <div id="conversion-result" style="padding: 8px 15px; background-color: #f1f1f1; border-radius: var(--border-radius); min-width: 100px; text-align: center; font-weight: bold;">
                                20.13 HP
                            </div>
                        </div>
                    </div>

                    <div class="feature-card">
                        <h4><i class="fas fa-project-diagram"></i> <span id="connection-title">Connexion du bornier</span></h4>
                        <p id="connection-text">Diagramme de connexion basé sur la tension et la configuration du moteur (étoile ou triangle).</p>
                        <div class="diagram" id="connection-diagram">
                            <div style="font-size: 1.2rem; font-weight: bold; margin-bottom: 10px;" id="diagram-title">Connexion Étoile (Y)</div>
                            <div style="display: flex; justify-content: center; align-items: center; gap: 20px; margin: 15px 0;">
                                <div>
                                    <div class="motor-terminal">U1</div>
                                    <div class="motor-terminal">V1</div>
                                    <div class="motor-terminal">W1</div>
                                </div>
                                <div style="font-size: 2rem;">⟷</div>
                                <div>
                                    <div>L1</div>
                                    <div>L2</div>
                                    <div>L3</div>
                                </div>
                            </div>
                            <div style="margin-top: 10px; font-size: 0.9rem; color: #666;" id="diagram-note">
                                U2, V2, W1 connectés ensemble pour la configuration étoile
                            </div>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <!-- Connection Diagram Section -->
        <div class="diagram-container">
            <div class="diagram-title">
                <i class="fas fa-plug"></i>
                <h3 id="wiring-title">Configuration de câblage recommandée</h3>
            </div>
            <div style="display: flex; justify-content: center; gap: 30px; flex-wrap: wrap;">
                <div style="text-align: center;">
                    <div style="font-weight: bold; margin-bottom: 10px;" id="breaker-diagram-title">Disjoncteur</div>
                    <div style="padding: 15px; background-color: #f9f9f9; border-radius: var(--border-radius); width: 200px;">
                        <div style="font-size: 1.5rem; color: var(--accent-color);">40A</div>
                        <div style="font-size: 0.9rem; color: #666;">Courbe D</div>
                    </div>
                </div>
                <div style="text-align: center;">
                    <div style="font-weight: bold; margin-bottom: 10px;" id="contactor-diagram-title">Contacteur</div>
                    <div style="padding: 15px; background-color: #f9f9f9; border-radius: var(--border-radius); width: 200px;">
                        <div style="font-size: 1.5rem; color: var(--accent-color);">32A</div>
                        <div style="font-size: 0.9rem; color: #666;">AC-3, 400V</div>
                    </div>
                </div>
                <div style="text-align: center;">
                    <div style="font-weight: bold; margin-bottom: 10px;" id="overload-diagram-title">Relais de surcharge</div>
                    <div style="padding: 15px; background-color: #f9f9f9; border-radius: var(--border-radius); width: 200px;">
                        <div style="font-size: 1.5rem; color: var(--accent-color);">25-32A</div>
                        <div style="font-size: 0.9rem; color: #666;">Réglable</div>
                    </div>
                </div>
            </div>
        </div>

        <footer>
            <p id="footer-text">Outil de calcul pour ingénieurs électriciens & contrôle | Conçu avec <i class="fas fa-heart" style="color: var(--accent-color);"></i> par <span class="highlight">DeepSeek AI</span></p>
            <p style="margin-top: 10px; font-size: 0.8rem;" id="disclaimer">Les résultats sont indicatifs. Toujours vérifier avec les normes locales et les spécifications du fabricant.</p>
        </footer>
    </div>

    <script>
        // Multi-language support
        const translations = {
            fr: {
                // Titles
                "app-title": "Calculateur de Moteur Électrique",
                "description-title": "Calculateur professionnel pour la sélection des composants de commande de moteur",
                "description-text": "Cet outil calcule les paramètres électriques, les courants de démarrage et sélectionne les composants appropriés (disjoncteurs, contacteurs, relais de surcharge) en fonction des données de la plaque signalétique du moteur et des conditions de fonctionnement.",
                "input-title": "Données d'entrée",
                "output-title": "Résultats de calcul",
                "features-title": "Fonctionnalités avancées",
                "wiring-title": "Configuration de câblage recommandée",
                
                // Input labels
                "nameplate-title": "Données de la plaque signalétique",
                "power-label": "Puissance mécanique nominale",
                "voltage-label": "Tension nominale (V)",
                "pf-label": "Facteur de puissance (cos φ)",
                "efficiency-label": "Rendement (η)",
                "frequency-label": "Fréquence (Hz)",
                "poles-label": "Nombre de pôles",
                "conditions-title": "Conditions de fonctionnement",
                "load-label": "Type de charge",
                "load-light": "Légère (ventilateurs, pompes)",
                "load-medium": "Moyenne (convoyeurs, compresseurs)",
                "load-heavy": "Lourde (broyeurs, concasseurs)",
                "cable-label": "Longueur du câble (m)",
                "start-method-label": "Méthode de démarrage",
                "start-dol": "DOL (Direct-On-Line)",
                "start-star": "Démarrage étoile-triangle",
                "start-soft": "Démarreur progressif",
                "start-vfd": "Variateur de fréquence (VFD)",
                "temp-label": "Température ambiante (°C)",
                "pf-target-label": "Facteur de puissance cible",
                
                // Output labels
                "analysis-title": "Analyse électrique",
                "current-label": "Courant nominal (pleine charge)",
                "current-note": "Courant à pleine charge basé sur la puissance nominale",
                "apparent-power-label": "Puissance apparente",
                "reactive-power-label": "Puissance réactive",
                "start-current-label": "Courant de démarrage",
                "start-current-note": "Basé sur la méthode de démarrage sélectionnée",
                "components-title": "Sélection des composants",
                "breaker-label": "Disjoncteur (Courbe D)",
                "breaker-note": "Capacité nominale recommandée",
                "contactor-label": "Contacteur (AC-3)",
                "overload-label": "Relais de surcharge",
                "overload-note": "Réglage recommandé: 1.15 × I<sub>fl</sub>",
                "cable-label-output": "Section du câble Cu",
                "cable-note": "Basé sur 50m de longueur et chute de tension &lt;3%",
                "voltage-drop-label": "Chute de tension",
                "capacitor-label": "Condensateur de correction",
                "capacitor-note": "Pour améliorer le facteur de puissance à 0.95",
                
                // Features
                "conversion-title": "Conversion d'unités",
                "conversion-text": "Conversion automatique entre kW et HP avec un seul clic. Prend en charge les unités métriques et impériales.",
                "connection-title": "Connexion du bornier",
                "connection-text": "Diagramme de connexion basé sur la tension et la configuration du moteur (étoile ou triangle).",
                "diagram-title": "Connexion Étoile (Y)",
                "diagram-note": "U2, V2, W1 connectés ensemble pour la configuration étoile",
                "breaker-diagram-title": "Disjoncteur",
                "contactor-diagram-title": "Contacteur",
                "overload-diagram-title": "Relais de surcharge",
                
                // Buttons
                "calculate-text": "Calculer les paramètres",
                "export-text": "Exporter PDF",
                "reset-text": "Réinitialiser",
                
                // Footer
                "footer-text": "Outil de calcul pour ingénieurs électriciens & contrôle | Conçu avec ♥ par DeepSeek AI",
                "disclaimer": "Les résultats sont indicatifs. Toujours vérifier avec les normes locales et les spécifications du fabricant."
            },
            ar: {
                // Titles
                "app-title": "حاسبة المحركات الكهربائية",
                "description-title": "آلة حاسبة احترافية لاختيار مكونات التحكم بالمحركات",
                "description-text": "تحسب هذه الأداة المعاملات الكهربائية، وتيارات البدء، وتختار المكونات المناسبة (القواطع، الكونتاكتورات، مرحلات التحميل الزائد) بناءً على بيانات لوحة المحرك وظروف التشغيل.",
                "input-title": "بيانات الإدخال",
                "output-title": "نتائج الحساب",
                "features-title": "ميزات متقدمة",
                "wiring-title": "توصيلة التوصيل الموصى بها",
                
                // Input labels
                "nameplate-title": "بيانات اللوحة الإسمية",
                "power-label": "القدرة الميكانيكية المقننة",
                "voltage-label": "الجهد المقنن (فولت)",
                "pf-label": "معامل القدرة (جتا φ)",
                "efficiency-label": "الكفاءة (η)",
                "frequency-label": "التردد (هرتز)",
                "poles-label": "عدد الأقطاب",
                "conditions-title": "ظروف التشغيل",
                "load-label": "نوع الحمل",
                "load-light": "خفيف (مراوح، مضخات)",
                "load-medium": "متوسط (سيور ناقلة، ضواغط)",
                "load-heavy": "ثقيل (كسارات، طواحين)",
                "cable-label": "طول الكابل (متر)",
                "start-method-label": "طريقة البدء",
                "start-dol": "بدء مباشر (DOL)",
                "start-star": "بدء نجم-مثلث",
                "start-soft": "بادئ لين",
                "start-vfd": "مغير التردد (VFD)",
                "temp-label": "درجة الحرارة المحيطة (°م)",
                "pf-target-label": "معامل القدرة المستهدف",
                
                // Output labels
                "analysis-title": "التحليل الكهربائي",
                "current-label": "التيار المقنن (حمولة كاملة)",
                "current-note": "تيار الحمل الكامل بناءً على القدرة المقننة",
                "apparent-power-label": "القدرة الظاهرية",
                "reactive-power-label": "القدرة غير الفعالة",
                "start-current-label": "تيار البدء",
                "start-current-note": "بناءً على طريقة البدء المختارة",
                "components-title": "اختيار المكونات",
                "breaker-label": "القاطع (منحنى D)",
                "breaker-note": "السعة المقننة الموصى بها",
                "contactor-label": "الكونتاكتور (AC-3)",
                "overload-label": "مرحل الحماية من التحميل الزائد",
                "overload-note": "الضبط الموصى به: 1.15 × ت.ح.ك",
                "cable-label-output": "مقطع الكابل نحاس",
                "cable-note": "بناءً على طول 50م وانخفاض جهد &lt;3%",
                "voltage-drop-label": "انخفاض الجهد",
                "capacitor-label": "مكثف تصحيح معامل القدرة",
                "capacitor-note": "لتحسين معامل القدرة إلى 0.95",
                
                // Features
                "conversion-title": "تحويل الوحدات",
                "conversion-text": "تحويل تلقائي بين كيلوواط وحصان بنقرة واحدة. يدعم الوحدات المترية والإمبراطورية.",
                "connection-title": "توصيلة الروزيتا",
                "connection-text": "مخطط التوصيل بناءً على الجهد وتكوين المحرك (نجم أو مثلث).",
                "diagram-title": "توصيلة النجمة (Y)",
                "diagram-note": "U2, V2, W1 متصلة معًا لتكوين النجمة",
                "breaker-diagram-title": "القاطع",
                "contactor-diagram-title": "الكونتاكتور",
                "overload-diagram-title": "مرحل التحميل الزائد",
                
                // Buttons
                "calculate-text": "حساب المعاملات",
                "export-text": "تصدير PDF",
                "reset-text": "إعادة التعيين",
                
                // Footer
                "footer-text": "أداة حساب لمهندسي الكهرباء والتحكم | مصمم ب♥ من DeepSeek AI",
                "disclaimer": "النتائج استرشادية. دائمًا تحقق من المعايير المحلية ومواصفات الشركة المصنعة."
            },
            en: {
                // Titles
                "app-title": "Electric Motor Calculator",
                "description-title": "Professional calculator for motor control component selection",
                "description-text": "This tool calculates electrical parameters, starting currents, and selects appropriate components (breakers, contactors, overload relays) based on motor nameplate data and operating conditions.",
                "input-title": "Input Data",
                "output-title": "Calculation Results",
                "features-title": "Advanced Features",
                "wiring-title": "Recommended Wiring Configuration",
                
                // Input labels
                "nameplate-title": "Nameplate Data",
                "power-label": "Rated Mechanical Power",
                "voltage-label": "Rated Voltage (V)",
                "pf-label": "Power Factor (cos φ)",
                "efficiency-label": "Efficiency (η)",
                "frequency-label": "Frequency (Hz)",
                "poles-label": "Number of Poles",
                "conditions-title": "Operating Conditions",
                "load-label": "Load Type",
                "load-light": "Light (fans, pumps)",
                "load-medium": "Medium (conveyors, compressors)",
                "load-heavy": "Heavy (crushers, grinders)",
                "cable-label": "Cable Length (m)",
                "start-method-label": "Starting Method",
                "start-dol": "DOL (Direct-On-Line)",
                "start-star": "Star-Delta Start",
                "start-soft": "Soft Starter",
                "start-vfd": "Variable Frequency Drive (VFD)",
                "temp-label": "Ambient Temperature (°C)",
                "pf-target-label": "Target Power Factor",
                
                // Output labels
                "analysis-title": "Electrical Analysis",
                "current-label": "Rated Current (Full Load)",
                "current-note": "Full load current based on rated power",
                "apparent-power-label": "Apparent Power",
                "reactive-power-label": "Reactive Power",
                "start-current-label": "Starting Current",
                "start-current-note": "Based on selected starting method",
                "components-title": "Component Selection",
                "breaker-label": "Circuit Breaker (Curve D)",
                "breaker-note": "Recommended rated capacity",
                "contactor-label": "Contactor (AC-3)",
                "overload-label": "Overload Relay",
                "overload-note": "Recommended setting: 1.15 × I<sub>fl</sub>",
                "cable-label-output": "Copper Cable Size",
                "cable-note": "Based on 50m length and voltage drop &lt;3%",
                "voltage-drop-label": "Voltage Drop",
                "capacitor-label": "Power Factor Correction Capacitor",
                "capacitor-note": "To improve power factor to 0.95",
                
                // Features
                "conversion-title": "Unit Conversion",
                "conversion-text": "Automatic conversion between kW and HP with a single click. Supports metric and imperial units.",
                "connection-title": "Terminal Connection",
                "connection-text": "Connection diagram based on voltage and motor configuration (star or delta).",
                "diagram-title": "Star Connection (Y)",
                "diagram-note": "U2, V2, W1 connected together for star configuration",
                "breaker-diagram-title": "Circuit Breaker",
                "contactor-diagram-title": "Contactor",
                "overload-diagram-title": "Overload Relay",
                
                // Buttons
                "calculate-text": "Calculate Parameters",
                "export-text": "Export PDF",
                "reset-text": "Reset",
                
                // Footer
                "footer-text": "Calculation tool for electrical & control engineers | Designed with ♥ by DeepSeek AI",
                "disclaimer": "Results are indicative. Always verify with local codes and manufacturer specifications."
            }
        };

        // Current language
        let currentLang = 'fr';

        // Function to change language
        function changeLanguage(lang) {
            currentLang = lang;
            
            // Update language buttons
            document.querySelectorAll('.lang-btn').forEach(btn => {
                if (btn.getAttribute('data-lang') === lang) {
                    btn.classList.add('active');
                } else {
                    btn.classList.remove('active');
                }
            });
            
            // Update all translatable elements
            Object.keys(translations[lang]).forEach(key => {
                const elements = document.querySelectorAll(`[id="${key}"]`);
                elements.forEach(element => {
                    if (element.tagName === 'INPUT' || element.tagName === 'OPTION') {
                        element.textContent = translations[lang][key];
                    } else {
                        element.innerHTML = translations[lang][key];
                    }
                });
            });
            
            // Update direction for Arabic
            if (lang === 'ar') {
                document.documentElement.dir = 'rtl';
                document.documentElement.lang = 'ar';
            } else {
                document.documentElement.dir = 'ltr';
                document.documentElement.lang = lang;
            }
            
            // Recalculate to update all notes and labels
            calculateAll();
        }

        // Function to calculate all parameters
        function calculateAll() {
            // Get input values
            const power = parseFloat(document.getElementById('power-input').value);
            const isPowerInKW = document.querySelector('.unit-btn.active').getAttribute('data-unit') === 'kW';
            const powerInKW = isPowerInKW ? power : power * 0.746; // Convert HP to kW
            
            const voltage = parseFloat(document.getElementById('voltage-input').value);
            const powerFactor = parseFloat(document.getElementById('pf-input').value);
            const efficiency = parseFloat(document.getElementById('efficiency-input').value);
            const frequency = parseInt(document.getElementById('frequency-select').value);
            const poles = parseInt(document.getElementById('poles-select').value);
            const cableLength = parseFloat(document.getElementById('cable-length').value);
            const startMethod = document.getElementById('start-method').value;
            const pfTarget = parseFloat(document.getElementById('pf-target').value);
            
            // Calculate full load current for 3-phase motor
            // I = P / (√3 * V * cosφ * η)
            const fullLoadCurrent = (powerInKW * 1000) / (Math.sqrt(3) * voltage * powerFactor * efficiency);
            
            // Calculate apparent power
            const apparentPower = (powerInKW * 1000) / (efficiency * powerFactor) / 1000; // in kVA
            
            // Calculate reactive power
            const reactivePower = apparentPower * Math.sqrt(1 - Math.pow(powerFactor, 2));
            
            // Calculate starting current based on method
            let startingCurrentMultiplier;
            switch(startMethod) {
                case 'DOL': startingCurrentMultiplier = 6; break;
                case 'star-delta': startingCurrentMultiplier = 2.5; break;
                case 'soft': startingCurrentMultiplier = 3; break;
                case 'vfd': startingCurrentMultiplier = 1.5; break;
                default: startingCurrentMultiplier = 6;
            }
            const startingCurrent = fullLoadCurrent * startingCurrentMultiplier;
            
            // Calculate component sizes
            const breakerSize = Math.ceil(fullLoadCurrent * 1.25 / 10) * 10; // Round up to nearest 10A
            const contactorSize = Math.ceil(fullLoadCurrent / 10) * 10; // Round up to nearest 10A
            const overloadMin = Math.round(fullLoadCurrent * 1.1);
            const overloadMax = Math.round(fullLoadCurrent * 1.25);
            
            // Calculate cable size based on current and length
            let cableSize;
            if (fullLoadCurrent <= 20) cableSize = 2.5;
            else if (fullLoadCurrent <= 30) cableSize = 4;
            else if (fullLoadCurrent <= 40) cableSize = 6;
            else if (fullLoadCurrent <= 55) cableSize = 10;
            else if (fullLoadCurrent <= 75) cableSize = 16;
            else cableSize = 25;
            
            // Calculate voltage drop (simplified)
            const voltageDropPercent = (fullLoadCurrent * cableLength * 0.0175 * 1.732 * 100) / (cableSize * voltage);
            
            // Calculate capacitor value for power factor correction
            const Qc = powerInKW * (Math.tan(Math.acos(powerFactor)) - Math.tan(Math.acos(pfTarget)));
            
            // Update results in the UI
            document.getElementById('full-load-current').textContent = fullLoadCurrent.toFixed(2);
            document.getElementById('apparent-power').textContent = apparentPower.toFixed(2);
            document.getElementById('reactive-power').textContent = reactivePower.toFixed(2);
            document.getElementById('starting-current').textContent = startingCurrent.toFixed(2);
            document.getElementById('breaker-size').textContent = breakerSize;
            document.getElementById('contactor-size').textContent = contactorSize;
            document.getElementById('overload-range').textContent = `${overloadMin} - ${overloadMax}`;
            document.getElementById('cable-size').textContent = cableSize;
            document.getElementById('voltage-drop').textContent = voltageDropPercent.toFixed(2);
            document.getElementById('capacitor-value').textContent = Qc.toFixed(2);
            
            // Update unit conversion
            updateUnitConversion();
            
            // Update connection diagram based on voltage
            updateConnectionDiagram(voltage);
        }

        // Function to update unit conversion
        function updateUnitConversion() {
            const power = parseFloat(document.getElementById('power-input').value);
            const isPowerInKW = document.querySelector('.unit-btn.active').getAttribute('data-unit') === 'kW';
            
            let fromUnit = document.getElementById('conversion-from').value;
            let value = parseFloat(document.getElementById('conversion-input').value);
            
            let result;
            if (fromUnit === 'kW') {
                result = value * 1.34102; // kW to HP
                document.getElementById('conversion-result').textContent = `${result.toFixed(2)} HP`;
            } else {
                result = value * 0.7457; // HP to kW
                document.getElementById('conversion-result').textContent = `${result.toFixed(2)} kW`;
            }
        }

        // Function to update connection diagram
        function updateConnectionDiagram(voltage) {
            const diagramTitle = document.getElementById('diagram-title');
            const diagramNote = document.getElementById('diagram-note');
            
            if (voltage >= 400) {
                // High voltage -> Star connection
                diagramTitle.textContent = currentLang === 'fr' ? 'Connexion Étoile (Y)' : 
                                          currentLang === 'ar' ? 'توصيلة النجمة (Y)' : 
                                          'Star Connection (Y)';
                diagramNote.textContent = currentLang === 'fr' ? 'U2, V2, W1 connectés ensemble pour la configuration étoile' :
                                         currentLang === 'ar' ? 'U2, V2, W1 متصلة معًا لتكوين النجمة' :
                                         'U2, V2, W1 connected together for star configuration';
            } else {
                // Low voltage -> Delta connection
                diagramTitle.textContent = currentLang === 'fr' ? 'Connexion Triangle (Δ)' : 
                                          currentLang === 'ar' ? 'توصيلة المثلث (Δ)' : 
                                          'Delta Connection (Δ)';
                diagramNote.textContent = currentLang === 'fr' ? 'U1-W2, V1-U2, W1-V2 connectés pour la configuration triangle' :
                                         currentLang === 'ar' ? 'U1-W2, V1-U2, W1-V2 متصلة لتكوين المثلث' :
                                         'U1-W2, V1-U2, W1-V2 connected for delta configuration';
            }
        }

        // Event listeners for language buttons
        document.querySelectorAll('.lang-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                const lang = btn.getAttribute('data-lang');
                changeLanguage(lang);
            });
        });

        // Event listener for unit buttons
        document.querySelectorAll('.unit-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                document.querySelectorAll('.unit-btn').forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                
                const unit = btn.getAttribute('data-unit');
                document.getElementById('power-unit').textContent = unit;
                
                // Convert value if needed
                const powerInput = document.getElementById('power-input');
                const currentValue = parseFloat(powerInput.value);
                
                if (unit === 'kW' && btn.getAttribute('data-converted') === 'true') {
                    // Convert from HP to kW
                    powerInput.value = (currentValue * 0.746).toFixed(2);
                    btn.removeAttribute('data-converted');
                } else if (unit === 'HP' && !btn.hasAttribute('data-converted')) {
                    // Convert from kW to HP
                    powerInput.value = (currentValue / 0.746).toFixed(2);
                    btn.setAttribute('data-converted', 'true');
                }
                
                calculateAll();
            });
        });

        // Event listener for calculate button
        document.getElementById('calculate-btn').addEventListener('click', calculateAll);

        // Event listener for reset button
        document.getElementById('reset-btn').addEventListener('click', () => {
            // Reset all inputs to default values
            document.getElementById('power-input').value = 15;
            document.querySelector('.unit-btn[data-unit="kW"]').click();
            document.getElementById('voltage-input').value = 400;
            document.getElementById('pf-input').value = 0.85;
            document.getElementById('efficiency-input').value = 0.92;
            document.getElementById('frequency-select').value = 50;
            document.getElementById('poles-select').value = 4;
            document.getElementById('load-select').value = 'medium';
            document.getElementById('cable-length').value = 50;
            document.getElementById('start-method').value = 'star-delta';
            document.getElementById('temperature').value = 30;
            document.getElementById('pf-target').value = 0.95;
            
            // Recalculate
            calculateAll();
        });

        // Event listener for export button (simulated)
        document.getElementById('export-btn').addEventListener('click', () => {
            alert(currentLang === 'fr' ? 'Fonction d\'exportation PDF simulée. Dans une application réelle, cela générerait un rapport PDF.' :
                  currentLang === 'ar' ? 'وظيفة تصدير PDF محاكاة. في التطبيق الفعلي، سيتم إنشاء تقرير PDF.' :
                  'PDF export function simulated. In a real app, this would generate a PDF report.');
        });

        // Event listener for convert button
        document.getElementById('convert-btn').addEventListener('click', updateUnitConversion);
        document.getElementById('conversion-from').addEventListener('change', updateUnitConversion);
        document.getElementById('conversion-input').addEventListener('input', updateUnitConversion);

        // Event listeners for input changes to auto-recalculate
        const inputsToWatch = [
            'power-input', 'voltage-input', 'pf-input', 'efficiency-input',
            'frequency-select', 'poles-select', 'load-select', 'cable-length',
            'start-method', 'temperature', 'pf-target'
        ];
        
        inputsToWatch.forEach(id => {
            document.getElementById(id).addEventListener('change', calculateAll);
            document.getElementById(id).addEventListener('input', calculateAll);
        });

        // Initialize the application
        document.addEventListener('DOMContentLoaded', () => {
            calculateAll();
            updateUnitConversion();
        });
    </script>
</body>
</html>
