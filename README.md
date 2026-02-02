<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculateur d'Équipements de Commande pour Moteurs Triphasés</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --success: #27ae60;
            --warning: #f39c12;
            --gray: #95a5a6;
        }

        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 20px 0;
            border-radius: 0 0 10px 10px;
            margin-bottom: 30px;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 10px;
        }

        .logo i {
            font-size: 2rem;
        }

        .logo h1 {
            font-size: 1.5rem;
        }

        main {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }

        @media (max-width: 992px) {
            main {
                grid-template-columns: 1fr;
            }
        }

        .card {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
        }

        .card-header {
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid var(--light);
        }

        .card-header h2 {
            color: var(--primary);
            font-size: 1.3rem;
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            color: var(--dark);
        }

        input, select {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 0.95rem;
        }

        input:focus, select:focus {
            outline: none;
            border-color: var(--secondary);
        }

        .input-with-unit {
            display: flex;
            align-items: center;
        }

        .input-with-unit input {
            flex: 1;
        }

        .unit {
            margin-left: 10px;
            color: var(--gray);
        }

        .btn {
            background-color: var(--secondary);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 5px;
            font-size: 1rem;
            cursor: pointer;
            width: 100%;
            margin-top: 10px;
        }

        .btn:hover {
            background-color: #2980b9;
        }

        .btn-calculate {
            background-color: var(--success);
        }

        .btn-reset {
            background-color: var(--gray);
            margin-top: 10px;
        }

        .results-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }

        .result-card {
            background-color: #f8f9fa;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid var(--secondary);
        }

        .result-label {
            font-weight: 600;
            color: var(--dark);
            font-size: 0.9rem;
        }

        .result-value {
            font-weight: 700;
            color: var(--primary);
            font-size: 1.1rem;
            margin-top: 5px;
        }

        .equipment-section {
            margin-top: 25px;
        }

        .equipment-card {
            background-color: #f0f7ff;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            border: 1px solid #ddd;
        }

        .equipment-card h4 {
            color: var(--secondary);
            margin-bottom: 10px;
            font-size: 1rem;
        }

        .equipment-details {
            margin-top: 10px;
            padding: 10px;
            background-color: #e8f4fc;
            border-radius: 5px;
            font-size: 0.85rem;
        }

        .warning {
            background-color: #fff3cd;
            padding: 12px;
            border-radius: 5px;
            margin-top: 20px;
            font-size: 0.85rem;
            color: #856404;
        }

        footer {
            text-align: center;
            padding: 15px;
            color: var(--gray);
            font-size: 0.85rem;
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="logo">
                <i class="fas fa-bolt"></i>
                <h1>Calculateur d'Équipements pour Moteurs Triphasés</h1>
            </div>
            <p style="opacity: 0.9; font-size: 0.95rem;">Outil professionnel pour les techniciens électriciens</p>
        </div>
    </header>

    <div class="container">
        <main>
            <!-- Section Saisie -->
            <section class="card">
                <div class="card-header">
                    <h2><i class="fas fa-cog"></i> Données du Moteur</h2>
                </div>
                
                <div class="form-group">
                    <label for="power">Puissance nominale (P)</label>
                    <div class="input-with-unit">
                        <input type="number" id="power" min="0.1" step="0.1" value="7.5">
                        <span class="unit">kW</span>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="voltage">Tension (U)</label>
                    <div class="input-with-unit">
                        <input type="number" id="voltage" min="100" step="10" value="400">
                        <span class="unit">V</span>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="current">Courant nominal (I<sub>n</sub>) - Optionnel</label>
                    <div class="input-with-unit">
                        <input type="number" id="current" min="0.1" step="0.1" value="14.8">
                        <span class="unit">A</span>
                    </div>
                    <small style="color: var(--gray);">Laissez vide pour calcul automatique</small>
                </div>
                
                <div class="form-group">
                    <label for="powerFactor">Facteur de puissance (cos φ)</label>
                    <div class="input-with-unit">
                        <input type="number" id="powerFactor" min="0.1" max="1" step="0.01" value="0.82">
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="startMethod">Méthode de démarrage</label>
                    <select id="startMethod">
                        <option value="DOL">Direct (DOL)</option>
                        <option value="star-delta">Étoile-Triangle</option>
                        <option value="soft">Démarreur progressif</option>
                        <option value="inverter">Variateur</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="efficiency">Rendement (η) - Optionnel</label>
                    <div class="input-with-unit">
                        <input type="number" id="efficiency" min="0.5" max="1" step="0.01" value="0.88">
                        <span class="unit">%</span>
                    </div>
                </div>
                
                <button class="btn btn-calculate" id="calculateBtn">
                    <i class="fas fa-calculator"></i> Calculer les équipements
                </button>
                
                <button class="btn btn-reset" id="resetBtn">
                    <i class="fas fa-redo"></i> Réinitialiser
                </button>
            </section>
            
            <!-- Section Résultats -->
            <section class="card">
                <div class="card-header">
                    <h2><i class="fas fa-clipboard-list"></i> Résultats et Sélection</h2>
                </div>
                
                <div class="results-grid">
                    <div class="result-card">
                        <div class="result-label">Puissance apparente (S)</div>
                        <div class="result-value" id="apparentPower">9.15 kVA</div>
                    </div>
                    
                    <div class="result-card">
                        <div class="result-label">Courant calculé (I)</div>
                        <div class="result-value" id="calculatedCurrent">14.8 A</div>
                    </div>
                    
                    <div class="result-card">
                        <div class="result-label">Méthode démarrage</div>
                        <div class="result-value" id="startMethodResult">DOL</div>
                    </div>
                    
                    <div class="result-card">
                        <div class="result-label">Courant démarrage</div>
                        <div class="result-value" id="startingCurrent">88.8 A</div>
                    </div>
                </div>
                
                <div class="equipment-section">
                    <h3 style="margin-bottom: 15px; color: var(--primary);">Équipements recommandés</h3>
                    
                    <div class="equipment-card">
                        <h4><i class="fas fa-plug"></i> Disjoncteur</h4>
                        <div><strong>Sélection:</strong> <span id="circuitBreaker">20 A triphasé</span></div>
                        <div class="equipment-details">
                            <strong>Justification:</strong> Protection du câble contre les courts-circuits<br>
                            <strong>Calcul:</strong> I<sub>disj</sub> = 1.3 × I<sub>n</sub> = 1.3 × 14.8 = 19.24 A → Choix 20A
                        </div>
                    </div>
                    
                    <div class="equipment-card">
                        <h4><i class="fas fa-exchange-alt"></i> Contacteur</h4>
                        <div><strong>Sélection:</strong> <span id="contactor">LC1D25 (25A)</span></div>
                        <div class="equipment-details">
                            <strong>Justification:</strong> Doit supporter le courant de démarrage (6×I pour DOL)<br>
                            <strong>Catégorie:</strong> AC-3 - utilisation moteur
                        </div>
                    </div>
                    
                    <div class="equipment-card">
                        <h4><i class="fas fa-thermometer-half"></i> Relais thermique</h4>
                        <div><strong>Sélection:</strong> <span id="thermalRelay">LRD14 (14-18A)</span></div>
                        <div class="equipment-details">
                            <strong>Justification:</strong> Protection contre les surcharges<br>
                            <strong>Réglage:</strong> 14.8 A ±10% (13.3A - 16.3A)
                        </div>
                    </div>
                    
                    <div class="equipment-card">
                        <h4><i class="fas fa-bolt"></i> Câble électrique</h4>
                        <div><strong>Sélection:</strong> <span id="cable">4mm² cuivre (3G4)</span></div>
                        <div class="equipment-details">
                            <strong>Justification:</strong> Capacité de courant: 27A (posé sur chemin)<br>
                            <strong>Section:</strong> Basée sur I<sub>z</sub> ≥ I<sub>n</sub> = 14.8A
                        </div>
                    </div>
                </div>
                
                <div class="warning">
                    <strong><i class="fas fa-exclamation-triangle"></i> Notes importantes:</strong>
                    <p>• Ces calculs sont indicatifs. Vérifier avec les normes locales.</p>
                    <p>• Considérer les conditions d'installation pour le câble.</p>
                    <p>• Consulter un ingénieur pour les projets importants.</p>
                </div>
            </section>
        </main>
        
        <footer>
            <p>© 2023 - Calculateur d'équipements pour moteurs triphasés</p>
        </footer>
    </div>

    <script>
        // Éléments DOM
        const powerInput = document.getElementById('power');
        const voltageInput = document.getElementById('voltage');
        const currentInput = document.getElementById('current');
        const powerFactorInput = document.getElementById('powerFactor');
        const startMethodInput = document.getElementById('startMethod');
        const efficiencyInput = document.getElementById('efficiency');
        const calculateBtn = document.getElementById('calculateBtn');
        const resetBtn = document.getElementById('resetBtn');
        
        // Éléments résultats
        const apparentPowerEl = document.getElementById('apparentPower');
        const calculatedCurrentEl = document.getElementById('calculatedCurrent');
        const startMethodResultEl = document.getElementById('startMethodResult');
        const circuitBreakerEl = document.getElementById('circuitBreaker');
        const contactorEl = document.getElementById('contactor');
        const thermalRelayEl = document.getElementById('thermalRelay');
        const cableEl = document.getElementById('cable');
        const startingCurrentEl = document.getElementById('startingCurrent');
        
        // Valeurs par défaut
        const defaultValues = {
            power: 7.5,
            voltage: 400,
            current: 14.8,
            powerFactor: 0.82,
            startMethod: 'DOL',
            efficiency: 0.88
        };
        
        // Base de données des équipements
        const equipmentDatabase = {
            disjoncteurs: [
                { current: 10, reference: "C10" },
                { current: 16, reference: "C16" },
                { current: 20, reference: "C20" },
                { current: 25, reference: "C25" },
                { current: 32, reference: "C32" },
                { current: 40, reference: "C40" },
                { current: 50, reference: "C50" },
                { current: 63, reference: "C63" }
            ],
            contacteurs: [
                { current: 9, reference: "LC1D09", power: "4kW" },
                { current: 12, reference: "LC1D12", power: "5.5kW" },
                { current: 18, reference: "LC1D18", power: "7.5kW" },
                { current: 25, reference: "LC1D25", power: "11kW" },
                { current: 32, reference: "LC1D32", power: "15kW" },
                { current: 40, reference: "LC1D40", power: "18.5kW" },
                { current: 50, reference: "LC1D50", power: "22kW" },
                { current: 65, reference: "LC1D65", power: "30kW" }
            ],
            relaisThermiques: [
                { range: "0.1-0.16A", reference: "LRD01" },
                { range: "0.16-0.25A", reference: "LRD02" },
                { range: "0.25-0.4A", reference: "LRD03" },
                { range: "0.4-0.63A", reference: "LRD04" },
                { range: "0.63-1A", reference: "LRD05" },
                { range: "1-1.6A", reference: "LRD06" },
                { range: "1.6-2.5A", reference: "LRD07" },
                { range: "2.5-4A", reference: "LRD08" },
                { range: "4-6A", reference: "LRD10" },
                { range: "5.5-8A", reference: "LRD12" },
                { range: "7-10A", reference: "LRD14" },
                { range: "9-13A", reference: "LRD16" },
                { range: "12-18A", reference: "LRD21" },
                { range: "17-25A", reference: "LRD22" },
                { range: "23-32A", reference: "LRD32" },
                { range: "30-40A", reference: "LRD35" }
            ],
            cables: [
                { section: 1.5, current: 14.5, reference: "3G1.5" },
                { section: 2.5, current: 19.5, reference: "3G2.5" },
                { section: 4, current: 27, reference: "3G4" },
                { section: 6, current: 34, reference: "3G6" },
                { section: 10, current: 46, reference: "3G10" },
                { section: 16, current: 61, reference: "3G16" },
                { section: 25, current: 80, reference: "3G25" },
                { section: 35, current: 99, reference: "3G35" }
            ]
        };
        
        function findDisjoncteur(current) {
            const needed = current * 1.3;
            return equipmentDatabase.disjoncteurs.find(d => d.current >= needed) || 
                   equipmentDatabase.disjoncteurs[equipmentDatabase.disjoncteurs.length - 1];
        }
        
        function findContacteur(current) {
            return equipmentDatabase.contacteurs.find(c => c.current >= current) || 
                   equipmentDatabase.contacteurs[equipmentDatabase.contacteurs.length - 1];
        }
        
        function findRelaisThermique(current) {
            // Conversion des plages de courant pour comparaison
            for (let relais of equipmentDatabase.relaisThermiques) {
                const range = relais.range.split('-');
                const min = parseFloat(range[0]);
                const max = parseFloat(range[1].replace('A', ''));
                
                if (current >= min && current <= max) {
                    return {
                        reference: relais.reference,
                        range: relais.range,
                        min: min,
                        max: max
                    };
                }
            }
            
            // Si non trouvé, retourne le dernier
            const last = equipmentDatabase.relaisThermiques[equipmentDatabase.relaisThermiques.length - 1];
            return {
                reference: last.reference,
                range: last.range,
                min: 30,
                max: 40
            };
        }
        
        function findCable(current) {
            const needed = current * 1.25; // Coefficient de sécurité
            return equipmentDatabase.cables.find(c => c.current >= needed) || 
                   equipmentDatabase.cables[equipmentDatabase.cables.length - 1];
        }
        
        function calculate() {
            // Lecture des valeurs
            const power = parseFloat(powerInput.value) || defaultValues.power;
            const voltage = parseFloat(voltageInput.value) || defaultValues.voltage;
            const current = parseFloat(currentInput.value);
            const powerFactor = parseFloat(powerFactorInput.value) || defaultValues.powerFactor;
            const startMethod = startMethodInput.value;
            const efficiency = parseFloat(efficiencyInput.value) || defaultValues.efficiency;
            
            // 1. Calcul puissance apparente
            let apparentPower;
            if (efficiency && efficiency < 1) {
                apparentPower = power / (powerFactor * efficiency);
            } else {
                apparentPower = power / powerFactor;
            }
            
            // 2. Calcul du courant
            let calculatedCurrent;
            if (current && current > 0) {
                calculatedCurrent = current;
            } else {
                calculatedCurrent = (apparentPower * 1000) / (Math.sqrt(3) * voltage);
            }
            
            // 3. Multiplicateur démarrage
            let startMultiplier;
            let startMethodName;
            switch(startMethod) {
                case 'DOL':
                    startMultiplier = 6;
                    startMethodName = 'DOL';
                    break;
                case 'star-delta':
                    startMultiplier = 3;
                    startMethodName = 'Étoile-Triangle';
                    break;
                case 'soft':
                    startMultiplier = 2;
                    startMethodName = 'Démarreur progressif';
                    break;
                case 'inverter':
                    startMultiplier = 1.5;
                    startMethodName = 'Variateur';
                    break;
                default:
                    startMultiplier = 6;
                    startMethodName = 'DOL';
            }
            
            // 4. Courant de démarrage
            const startingCurrent = calculatedCurrent * startMultiplier;
            
            // 5. Sélection des équipements
            const disjoncteur = findDisjoncteur(calculatedCurrent);
            const contacteur = findContacteur(calculatedCurrent);
            const relaisThermique = findRelaisThermique(calculatedCurrent);
            const cable = findCable(calculatedCurrent);
            
            // 6. Mise à jour de l'interface
            apparentPowerEl.textContent = `${apparentPower.toFixed(2)} kVA`;
            calculatedCurrentEl.textContent = `${calculatedCurrent.toFixed(2)} A`;
            startMethodResultEl.textContent = startMethodName;
            startingCurrentEl.textContent = `${startingCurrent.toFixed(1)} A`;
            
            circuitBreakerEl.textContent = `${disjoncteur.current}A (${disjoncteur.reference})`;
            contactorEl.textContent = `${contacteur.reference} - ${contacteur.current}A (jusqu'à ${contacteur.power})`;
            thermalRelayEl.textContent = `${relaisThermique.reference} (${relaisThermique.range})`;
            cableEl.textContent = `${cable.reference} - ${cable.section}mm² (${cable.current}A)`;
            
            // Mise à jour des détails
            document.querySelectorAll('.equipment-details').forEach((el, index) => {
                switch(index) {
                    case 0: // Disjoncteur
                        el.innerHTML = `
                            <strong>Justification:</strong> Protection du câble (1.3×I<sub>n</sub>)<br>
                            <strong>Calcul:</strong> 1.3 × ${calculatedCurrent.toFixed(2)} = ${(calculatedCurrent * 1.3).toFixed(2)}A → Choix ${disjoncteur.current}A
                        `;
                        break;
                    case 1: // Contacteur
                        el.innerHTML = `
                            <strong>Justification:</strong> Courant démarrage: ${startingCurrent.toFixed(1)}A (${startMultiplier}×I)<br>
                            <strong>Catégorie:</strong> AC-3 - utilisation moteur
                        `;
                        break;
                    case 2: // Relais thermique
                        el.innerHTML = `
                            <strong>Justification:</strong> Protection surcharge moteur<br>
                            <strong>Réglage:</strong> ${calculatedCurrent.toFixed(2)}A (plage: ${relaisThermique.min}-${relaisThermique.max}A)
                        `;
                        break;
                    case 3: // Câble
                        el.innerHTML = `
                            <strong>Justification:</strong> I<sub>z</sub> = ${cable.current}A ≥ I<sub>n</sub> = ${calculatedCurrent.toFixed(2)}A<br>
                            <strong>Note:</strong> Valable pour câble posé sur chemin, 40°C ambiant
                        `;
                        break;
                }
            });
        }
        
        function resetForm() {
            powerInput.value = defaultValues.power;
            voltageInput.value = defaultValues.voltage;
            currentInput.value = defaultValues.current;
            powerFactorInput.value = defaultValues.powerFactor;
            startMethodInput.value = defaultValues.startMethod;
            efficiencyInput.value = defaultValues.efficiency;
            
            calculate();
        }
        
        // Événements
        calculateBtn.addEventListener('click', calculate);
        resetBtn.addEventListener('click', resetForm);
        
        // Calcul automatique
        const inputs = document.querySelectorAll('input, select');
        inputs.forEach(input => {
            input.addEventListener('change', calculate);
            input.addEventListener('input', calculate);
        });
        
        // Initialisation
        window.addEventListener('DOMContentLoaded', calculate);
    </script>
</body>
</html>
