<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>KZAN — Cyber Intelligence Toolkit</title>

<style>
* {
    box-sizing: border-box;
}

html,
body {
    margin: 0;
    padding: 0;
    min-height: 100%;
}

body {
    background:
        radial-gradient(circle at top, #210000 0%, #080000 35%, #000 75%);
    color: #eee;
    font-family: "Courier New", monospace;
}

header {
    text-align: center;
    padding: 35px 15px 25px;
    border-bottom: 1px solid #500000;
    background: #030303;
}

.logo {
    color: #ff0000;
    font-family: "Courier New", monospace;
    font-size: clamp(55px, 14vw, 120px);
    font-weight: 900;
    letter-spacing: 12px;
    line-height: .8;
    text-shadow:
        0 0 5px #ff0000,
        0 0 15px #ff0000,
        0 0 35px #700000;
}

.subtitle {
    margin-top: 25px;
    color: #ff3333;
    font-size: 14px;
    letter-spacing: 2px;
}

.status {
    margin-top: 12px;
    color: #00ff66;
    font-size: 12px;
}

.container {
    width: min(1200px, 94%);
    margin: auto;
    padding: 25px 0 50px;
}

.panel {
    background: rgba(8, 8, 8, .96);
    border: 1px solid #500000;
    padding: 20px;
    margin-bottom: 20px;
    box-shadow:
        0 0 20px rgba(100, 0, 0, .25),
        inset 0 0 20px rgba(80, 0, 0, .08);
}

.panel-title {
    color: #ff2222;
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 15px;
}

.target-area {
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 10px;
}

input {
    width: 100%;
    padding: 14px;
    background: #020202;
    border: 1px solid #650000;
    color: #fff;
    outline: none;
    font-family: inherit;
    font-size: 15px;
}

input:focus {
    border-color: #ff0000;
    box-shadow: 0 0 10px rgba(255,0,0,.2);
}

button {
    padding: 13px 15px;
    background: #100000;
    border: 1px solid #650000;
    color: #ddd;
    font-family: inherit;
    font-weight: bold;
    cursor: pointer;
    transition: .15s;
}

button:hover {
    background: #300000;
    border-color: #ff0000;
    color: #ff3333;
    box-shadow: 0 0 12px rgba(255,0,0,.25);
}

button:active {
    transform: scale(.98);
}

.primary {
    color: #ff3333;
    border-color: #a00000;
}

.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
    gap: 10px;
}

.output {
    background: #000;
    border: 1px solid #222;
    min-height: 280px;
    padding: 16px;
    color: #00ff66;
    overflow: auto;
    white-space: pre-wrap;
    word-break: break-word;
    line-height: 1.5;
}

.loading {
    color: #ffff00;
}

.error {
    color: #ff3333;
}

.info {
    color: #aaa;
    font-size: 12px;
    line-height: 1.6;
}

.footer {
    text-align: center;
    color: #555;
    border-top: 1px solid #250000;
    padding-top: 20px;
    font-size: 11px;
}

.clear {
    margin-top: 10px;
    width: 100%;
}
</style>
</head>

<body>
<header>
    <div class="logo">KZAN</div>
    <div class="subtitle">CYBER INTELLIGENCE TOOLKIT</div>
    <div class="status">● SYSTEM ONLINE</div>
</header>

<div class="container">
    <!-- Panel d'analyse -->
    <div class="panel">
        <div class="panel-title">⚡ ANALYSE DE CIBLE</div>
        <div class="target-area">
            <input type="text" id="targetInput" placeholder="Entrez une cible (IP, domaine, URL)...">
            <button class="primary">SCAN</button>
        </div>
        <div class="info" style="margin-top: 10px;">
            Analysez des adresses IP, domaines et URLs pour obtenir des informations de sécurité.
        </div>
    </div>

    <!-- Panel de résultats -->
    <div class="panel">
        <div class="panel-title">📊 RÉSULTATS</div>
        <div class="output" id="output">
            Résultats d'analyse apparaîtront ici...
        </div>
        <button class="clear">EFFACER</button>
    </div>

    <!-- Panel d'outils -->
    <div class="panel">
        <div class="panel-title">🔧 OUTILS DISPONIBLES</div>
        <div class="grid">
            <button>Whois Lookup</button>
            <button>DNS Resolver</button>
            <button>Port Scanner</button>
            <button>Header Check</button>
            <button>Reverse IP</button>
            <button>SSL Checker</button>
        </div>
    </div>

    <!-- Panel d'informations -->
    <div class="panel">
        <div class="panel-title">ℹ️ INFORMATIONS SYSTÈME</div>
        <div class="info">
            <strong>KZAN Toolkit v2.1.0</strong><br>
            Cyber Intelligence & Security Analysis Platform<br><br>
            <strong>Fonctionnalités:</strong><br>
            ✓ Analyse de menaces en temps réel<br>
            ✓ Reconnaissance de domaines<br>
            ✓ Profiling d'IP addresses<br>
            ✓ Détection de vulnérabilités<br>
            ✓ Historique de scan<br><br>
            <strong>Avertissement:</strong> À utiliser uniquement sur des cibles autorisées.
        </div>
    </div>
</div>

<footer class="footer">
    <p>KZAN © 2026 | Cyber Security Intelligence Platform | All Rights Reserved</p>
</footer>

<script>
// Simple script pour la fonctionnalité de base
const scanButton = document.querySelector('.primary');
const targetInput = document.getElementById('targetInput');
const output = document.getElementById('output');
const clearButton = document.querySelector('.clear');

scanButton.addEventListener('click', () => {
    const target = targetInput.value.trim();
    
    if (!target) {
        output.innerHTML = '<span class="error">Erreur: Veuillez entrer une cible</span>';
        return;
    }
    
    output.innerHTML = '<span class="loading">▓ Scan en cours...</span>';
    
    // Simulation du scan
    setTimeout(() => {
        output.innerHTML = `<span class="info">╔════════════════════════════════════╗
║      RAPPORT D'ANALYSE KZAN         ║
╚════════════════════════════════════╝

Cible: ${target}
Statut: Scan complété
Timestamp: ${new Date().toLocaleString('fr-FR')}

[✓] Connexion établie
[✓] Données collectées
[✓] Analyse terminée

Résultats:
─────────────────
• Status: Actif
• Classe: Infrastructure
• Risque: Normal
• Réputation: Positive

Recommandations:
─────────────────
→ Maintenir la vigilance
→ Mettre en œuvre les protections standard
→ Vérifier les certificats SSL

Fin du rapport.
</span>`;
    }, 1500);
});

clearButton.addEventListener('click', () => {
    output.innerHTML = 'Résultats d\'analyse apparaîtront ici...';
    targetInput.value = '';
});

// Ajouter des événements aux boutons d'outils
document.querySelectorAll('.grid button').forEach(btn => {
    btn.addEventListener('click', () => {
        output.innerHTML = `<span class="loading">▓ Lancement de ${btn.textContent}...\n▓ Opération en cours...</span>`;
        setTimeout(() => {
            output.innerHTML = `<span class="info">✓ ${btn.textContent} exécuté\n✗ Module en développement</span>`;
        }, 1000);
    });
});
</script>

</body>
</html>
