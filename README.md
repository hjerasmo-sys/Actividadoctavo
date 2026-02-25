<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🎮 Presentaciones Digitales - Grado 801</title>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<style>
:root {
  --mario-red: #e52521;
  --mario-blue: #4a90e2;
  --mario-yellow: #fbd000;
  --mario-green: #43b047;
  --mario-brown: #8b4513;
  --sky: #5c94fc;
  --cloud: #fff;
  --ground: #e8a000;
  --brick: #c84b0c;
  --pipe: #00a800;
  --sena-primary: #3dae2b;
  --sena-dark: #1a5c14;
  --bg-dark: #1a1a2e;
  --panel-bg: #16213e;
  --card-bg: #0f3460;
  --accent: #fbd000;
  --text-light: #e8f4fd;
  --locked: #555;
  --star: #ffd700;
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  font-family: 'Nunito', sans-serif;
  background: var(--bg-dark);
  color: var(--text-light);
  min-height: 100vh;
  overflow-x: hidden;
}

/* ===== SCREEN SYSTEM ===== */
.screen { display: none; min-height: 100vh; }
.screen.active { display: flex; }

/* ===== INTRO SCREEN ===== */
#screen-intro {
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: linear-gradient(180deg, #5c94fc 0%, #5c94fc 60%, #43b047 60%, #43b047 80%, #8b4513 80%);
  position: relative;
  overflow: hidden;
}

.clouds-container {
  position: absolute; top: 5%; width: 100%;
  display: flex; justify-content: space-around;
}
.cloud {
  background: white; border-radius: 50px;
  padding: 15px 30px; opacity: 0.9;
  animation: cloudFloat 4s ease-in-out infinite;
}
.cloud:nth-child(2) { animation-delay: -2s; }
.cloud span { font-size: 2rem; }

@keyframes cloudFloat { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-10px)} }

.intro-content {
  text-align: center; z-index: 10;
  padding: 20px;
}
.game-title {
  font-family: 'Press Start 2P', monospace;
  font-size: clamp(14px, 3vw, 24px);
  color: var(--mario-yellow);
  text-shadow: 4px 4px 0 var(--mario-red), 8px 8px 0 #000;
  line-height: 1.6;
  margin-bottom: 20px;
  animation: titlePop 0.5s ease-out;
}
@keyframes titlePop { 0%{transform:scale(0)} 70%{transform:scale(1.1)} 100%{transform:scale(1)} }

.subtitle-intro {
  font-size: 1.2rem;
  color: white;
  margin-bottom: 10px;
  font-weight: 700;
  text-shadow: 2px 2px 0 rgba(0,0,0,0.5);
}

.mario-character {
  font-size: 6rem;
  animation: marioJump 1s ease-in-out infinite;
  margin: 20px 0;
  cursor: pointer;
}
@keyframes marioJump { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-20px)} }

.btn-start {
  font-family: 'Press Start 2P', monospace;
  font-size: 14px;
  background: var(--mario-yellow);
  color: #000;
  border: 4px solid #000;
  padding: 15px 30px;
  cursor: pointer;
  border-radius: 8px;
  box-shadow: 6px 6px 0 #000;
  transition: all 0.1s;
  margin-top: 20px;
  animation: blink 1s step-end infinite;
}
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.4} }
.btn-start:hover { transform: translate(3px,3px); box-shadow: 3px 3px 0 #000; }

.ground-row {
  position: absolute; bottom: 0; width: 100%;
  height: 80px;
  background: repeating-linear-gradient(90deg, #c84b0c 0px, #c84b0c 40px, #a33a09 40px, #a33a09 80px);
  border-top: 4px solid #000;
  display: flex; align-items: center; justify-content: space-around; padding: 10px;
}
.coin { font-size: 1.5rem; animation: coinSpin 1s linear infinite; }
@keyframes coinSpin { 0%{transform:scaleX(1)} 50%{transform:scaleX(0.1)} 100%{transform:scaleX(1)} }

/* ===== NAME SCREEN ===== */
#screen-name {
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, var(--bg-dark), var(--panel-bg));
}

.name-card {
  background: var(--card-bg);
  border: 3px solid var(--mario-yellow);
  border-radius: 20px;
  padding: 40px;
  max-width: 500px;
  width: 90%;
  text-align: center;
  box-shadow: 0 0 40px rgba(251,208,0,0.3);
}
.name-card h2 {
  font-family: 'Press Start 2P', monospace;
  font-size: 14px;
  color: var(--mario-yellow);
  margin-bottom: 10px;
}
.name-card p { color: #aaa; margin-bottom: 25px; }
.name-input {
  width: 100%;
  padding: 15px;
  font-size: 1.1rem;
  font-family: 'Nunito', sans-serif;
  border-radius: 10px;
  border: 3px solid var(--mario-blue);
  background: var(--bg-dark);
  color: white;
  margin-bottom: 20px;
  outline: none;
}
.name-input:focus { border-color: var(--mario-yellow); }

/* ===== MAIN DASHBOARD ===== */
#screen-main {
  flex-direction: row;
}

/* SIDEBAR */
.sidebar {
  width: 260px;
  min-height: 100vh;
  background: linear-gradient(180deg, #0a0e1a 0%, #1a1a2e 100%);
  border-right: 3px solid var(--mario-yellow);
  display: flex;
  flex-direction: column;
  padding: 20px 0;
  flex-shrink: 0;
}

.sidebar-logo {
  text-align: center;
  padding: 0 20px 20px;
  border-bottom: 2px solid rgba(251,208,0,0.3);
  margin-bottom: 20px;
}
.sena-badge {
  background: var(--sena-primary);
  color: white;
  font-size: 10px;
  font-weight: 900;
  padding: 4px 10px;
  border-radius: 20px;
  letter-spacing: 2px;
  display: inline-block;
  margin-bottom: 8px;
}
.sidebar-title {
  font-family: 'Press Start 2P', monospace;
  font-size: 9px;
  color: var(--mario-yellow);
  line-height: 1.8;
}

.sidebar-player {
  padding: 15px 20px;
  background: rgba(255,255,255,0.05);
  margin: 0 10px 20px;
  border-radius: 12px;
  border: 1px solid rgba(255,255,255,0.1);
}
.player-avatar { font-size: 2.5rem; text-align: center; }
.player-name {
  font-size: 0.85rem; font-weight: 800;
  text-align: center; color: white;
  margin-top: 5px;
  word-break: break-word;
}
.player-score {
  font-family: 'Press Start 2P', monospace;
  font-size: 9px;
  color: var(--mario-yellow);
  text-align: center;
  margin-top: 5px;
}

.sidebar-nav { flex: 1; padding: 0 10px; }
.nav-label {
  font-size: 9px;
  letter-spacing: 2px;
  color: rgba(255,255,255,0.4);
  text-transform: uppercase;
  padding: 0 10px;
  margin-bottom: 8px;
}

.station-nav-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 12px;
  border-radius: 10px;
  cursor: pointer;
  margin-bottom: 5px;
  transition: all 0.2s;
  position: relative;
}
.station-nav-item.completed { background: rgba(67,176,71,0.2); }
.station-nav-item.active { background: rgba(251,208,0,0.2); border: 1px solid var(--mario-yellow); }
.station-nav-item.locked { opacity: 0.4; cursor: not-allowed; }
.station-nav-item:hover:not(.locked) { background: rgba(255,255,255,0.1); }

.nav-icon { font-size: 1.4rem; flex-shrink: 0; }
.nav-text { font-size: 0.7rem; font-weight: 700; color: white; line-height: 1.3; }
.nav-status { margin-left: auto; font-size: 0.8rem; flex-shrink: 0; }

.progress-bar-wrap {
  padding: 15px 20px;
  border-top: 2px solid rgba(255,255,255,0.1);
  margin-top: 10px;
}
.progress-label {
  display: flex; justify-content: space-between;
  font-size: 0.7rem; color: rgba(255,255,255,0.6);
  margin-bottom: 8px;
}
.progress-track {
  height: 10px;
  background: rgba(255,255,255,0.1);
  border-radius: 10px;
  overflow: hidden;
}
.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--sena-primary), var(--mario-yellow));
  border-radius: 10px;
  transition: width 0.5s ease;
}

/* MAIN CONTENT */
.main-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  overflow-y: auto;
  background: var(--bg-dark);
}

/* TOP BAR */
.topbar {
  background: var(--panel-bg);
  border-bottom: 2px solid var(--mario-yellow);
  padding: 12px 25px;
  display: flex;
  align-items: center;
  gap: 15px;
  flex-shrink: 0;
}
.topbar-station {
  font-family: 'Press Start 2P', monospace;
  font-size: 10px;
  color: var(--mario-yellow);
}
.lives-display { display: flex; gap: 5px; align-items: center; margin-left: auto; }
.life { font-size: 1.2rem; }
.coins-display {
  font-family: 'Press Start 2P', monospace;
  font-size: 9px;
  color: var(--mario-yellow);
  background: rgba(251,208,0,0.1);
  padding: 6px 12px;
  border-radius: 20px;
  border: 1px solid rgba(251,208,0,0.3);
}

/* STATION CONTENT */
.station-area {
  flex: 1;
  padding: 30px;
  max-width: 900px;
  width: 100%;
  margin: 0 auto;
}

.station-header {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-bottom: 30px;
  padding: 25px;
  background: var(--panel-bg);
  border-radius: 20px;
  border-left: 6px solid var(--mario-yellow);
  position: relative;
  overflow: hidden;
}
.station-header::before {
  content: '';
  position: absolute; top: 0; right: 0;
  width: 200px; height: 100%;
  background: linear-gradient(90deg, transparent, rgba(251,208,0,0.05));
}
.station-number {
  font-family: 'Press Start 2P', monospace;
  font-size: 2rem;
  color: var(--mario-yellow);
  text-shadow: 3px 3px 0 rgba(0,0,0,0.5);
  flex-shrink: 0;
}
.station-emoji { font-size: 3rem; flex-shrink: 0; }
.station-info h1 {
  font-size: 1.5rem;
  font-weight: 900;
  color: white;
  margin-bottom: 5px;
}
.station-info p { font-size: 0.85rem; color: rgba(255,255,255,0.6); }

.content-card {
  background: var(--panel-bg);
  border-radius: 16px;
  padding: 25px;
  margin-bottom: 20px;
  border: 1px solid rgba(255,255,255,0.08);
  line-height: 1.8;
}
.content-card h3 {
  font-size: 1.1rem;
  font-weight: 800;
  color: var(--mario-yellow);
  margin-bottom: 15px;
  display: flex; align-items: center; gap: 8px;
}
.content-card p { font-size: 0.95rem; color: rgba(255,255,255,0.85); margin-bottom: 12px; }
.content-card ul { padding-left: 20px; }
.content-card li { font-size: 0.9rem; color: rgba(255,255,255,0.8); margin-bottom: 8px; }

.highlight-box {
  background: linear-gradient(135deg, rgba(251,208,0,0.1), rgba(251,208,0,0.05));
  border: 2px solid rgba(251,208,0,0.4);
  border-radius: 12px;
  padding: 15px 20px;
  margin: 15px 0;
  font-size: 0.9rem;
  color: var(--mario-yellow);
  font-weight: 700;
}
.tip-box {
  background: rgba(67,176,71,0.1);
  border-left: 4px solid var(--mario-green);
  border-radius: 0 12px 12px 0;
  padding: 15px 20px;
  margin: 15px 0;
  font-size: 0.9rem;
  color: rgba(255,255,255,0.9);
}
.tip-box strong { color: var(--mario-green); }

.btn-example {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--mario-blue);
  color: white;
  padding: 10px 20px;
  border-radius: 30px;
  text-decoration: none;
  font-weight: 800;
  font-size: 0.85rem;
  border: none;
  cursor: pointer;
  transition: all 0.2s;
  box-shadow: 0 4px 0 rgba(0,0,0,0.3);
  margin: 5px;
}
.btn-example:hover { transform: translateY(-2px); box-shadow: 0 6px 0 rgba(0,0,0,0.3); }
.btn-example.yellow { background: var(--mario-yellow); color: #000; }
.btn-example.green { background: var(--mario-green); }

/* TOOLS SELECTOR (Station 3) */
.tools-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 15px;
  margin: 20px 0;
}
.tool-card {
  background: var(--card-bg);
  border: 3px solid transparent;
  border-radius: 16px;
  padding: 20px 15px;
  text-align: center;
  cursor: pointer;
  transition: all 0.3s;
}
.tool-card:hover { transform: translateY(-5px); border-color: var(--mario-yellow); }
.tool-card.selected { border-color: var(--mario-green); background: rgba(67,176,71,0.15); }
.tool-emoji { font-size: 2.5rem; margin-bottom: 10px; }
.tool-name { font-weight: 900; font-size: 0.9rem; color: white; margin-bottom: 5px; }
.tool-desc { font-size: 0.7rem; color: rgba(255,255,255,0.5); }

/* CHALLENGE SECTION */
.challenge-section {
  background: linear-gradient(135deg, #1a0a2e, #2d1b69);
  border: 2px solid #7c3aed;
  border-radius: 20px;
  padding: 25px;
  margin-top: 20px;
}
.challenge-header {
  font-family: 'Press Start 2P', monospace;
  font-size: 11px;
  color: #a78bfa;
  margin-bottom: 20px;
  display: flex; align-items: center; gap: 10px;
}
.challenge-question {
  font-size: 1rem;
  font-weight: 700;
  color: white;
  margin-bottom: 20px;
  line-height: 1.6;
}
.options-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  margin-bottom: 20px;
}
.option-btn {
  background: rgba(255,255,255,0.05);
  border: 2px solid rgba(255,255,255,0.15);
  border-radius: 12px;
  padding: 12px 15px;
  color: white;
  font-size: 0.85rem;
  font-family: 'Nunito', sans-serif;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s;
  text-align: left;
}
.option-btn:hover { border-color: #a78bfa; background: rgba(167,139,250,0.1); }
.option-btn.correct { border-color: var(--mario-green); background: rgba(67,176,71,0.2); color: var(--mario-green); }
.option-btn.wrong { border-color: var(--mario-red); background: rgba(229,37,33,0.2); color: #ff6b6b; }
.option-btn:disabled { cursor: not-allowed; }

.input-challenge {
  width: 100%;
  padding: 12px 15px;
  font-size: 0.95rem;
  font-family: 'Nunito', sans-serif;
  border-radius: 10px;
  border: 2px solid rgba(167,139,250,0.4);
  background: rgba(0,0,0,0.3);
  color: white;
  margin-bottom: 15px;
  outline: none;
  resize: vertical;
  min-height: 80px;
}
.input-challenge:focus { border-color: #a78bfa; }

.btn-submit {
  font-family: 'Press Start 2P', monospace;
  font-size: 10px;
  background: var(--mario-yellow);
  color: #000;
  border: 3px solid #000;
  padding: 12px 25px;
  cursor: pointer;
  border-radius: 8px;
  box-shadow: 4px 4px 0 #000;
  transition: all 0.1s;
}
.btn-submit:hover { transform: translate(2px,2px); box-shadow: 2px 2px 0 #000; }
.btn-submit:disabled { opacity: 0.5; cursor: not-allowed; }

/* FEEDBACK */
.feedback-popup {
  display: none;
  position: fixed;
  top: 50%; left: 50%;
  transform: translate(-50%,-50%) scale(0);
  background: var(--panel-bg);
  border: 4px solid var(--mario-yellow);
  border-radius: 20px;
  padding: 30px 40px;
  text-align: center;
  z-index: 1000;
  max-width: 450px;
  width: 90%;
  box-shadow: 0 20px 60px rgba(0,0,0,0.8);
  transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1);
}
.feedback-popup.show {
  display: block;
  transform: translate(-50%,-50%) scale(1);
}
.feedback-emoji { font-size: 4rem; margin-bottom: 15px; }
.feedback-title {
  font-family: 'Press Start 2P', monospace;
  font-size: 14px;
  margin-bottom: 10px;
}
.feedback-title.success { color: var(--mario-green); }
.feedback-title.fail { color: var(--mario-red); }
.feedback-msg { font-size: 1rem; color: rgba(255,255,255,0.85); line-height: 1.6; margin-bottom: 20px; }
.feedback-coins { color: var(--mario-yellow); font-weight: 900; font-size: 1.1rem; }

.overlay {
  display: none;
  position: fixed; top:0; left:0; right:0; bottom:0;
  background: rgba(0,0,0,0.7);
  z-index: 999;
}
.overlay.show { display: block; }

/* FINAL REPORT */
#screen-report {
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, var(--bg-dark), #0d2137);
  padding: 30px;
}

.report-card {
  background: var(--panel-bg);
  border: 3px solid var(--mario-yellow);
  border-radius: 25px;
  padding: 40px;
  max-width: 700px;
  width: 100%;
  box-shadow: 0 0 60px rgba(251,208,0,0.2);
}
.report-title {
  font-family: 'Press Start 2P', monospace;
  font-size: 14px;
  color: var(--mario-yellow);
  text-align: center;
  margin-bottom: 25px;
  line-height: 1.8;
}
.report-player {
  text-align: center;
  margin-bottom: 25px;
}
.report-player .avatar { font-size: 4rem; }
.report-player .rname { font-size: 1.5rem; font-weight: 900; color: white; margin-top: 10px; }
.report-player .rscore {
  font-family: 'Press Start 2P', monospace;
  font-size: 11px;
  color: var(--mario-yellow);
  margin-top: 8px;
}

.report-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15px;
  margin: 20px 0;
}
.report-stat {
  background: rgba(0,0,0,0.3);
  border-radius: 12px;
  padding: 15px;
  text-align: center;
  border: 1px solid rgba(255,255,255,0.1);
}
.stat-val {
  font-family: 'Press Start 2P', monospace;
  font-size: 18px;
  color: var(--mario-yellow);
}
.stat-label { font-size: 0.75rem; color: rgba(255,255,255,0.5); margin-top: 5px; }

.stations-summary { margin: 20px 0; }
.station-summary-item {
  display: flex; align-items: center; gap: 12px;
  padding: 10px 15px;
  border-radius: 10px;
  margin-bottom: 8px;
  background: rgba(0,0,0,0.2);
}
.station-summary-item.done { border-left: 3px solid var(--mario-green); }
.ssi-icon { font-size: 1.3rem; }
.ssi-name { font-size: 0.85rem; font-weight: 700; flex: 1; }
.ssi-status { font-size: 0.75rem; color: var(--mario-green); font-weight: 800; }

.teacher-section {
  background: rgba(61,174,43,0.1);
  border: 2px solid rgba(61,174,43,0.4);
  border-radius: 12px;
  padding: 20px;
  margin-top: 20px;
}
.teacher-section h4 {
  color: var(--sena-primary);
  font-weight: 900;
  margin-bottom: 10px;
  font-size: 0.9rem;
}
.teacher-section p { font-size: 0.8rem; color: rgba(255,255,255,0.7); line-height: 1.7; }

.btn-print {
  width: 100%;
  padding: 15px;
  font-family: 'Press Start 2P', monospace;
  font-size: 10px;
  background: var(--sena-primary);
  color: white;
  border: 3px solid #000;
  border-radius: 10px;
  cursor: pointer;
  margin-top: 20px;
  box-shadow: 4px 4px 0 #000;
  transition: all 0.1s;
}
.btn-print:hover { transform: translate(2px,2px); box-shadow: 2px 2px 0 #000; }

/* Floating coins animation */
.float-coin {
  position: fixed;
  font-size: 1.5rem;
  pointer-events: none;
  animation: floatUp 1s ease-out forwards;
  z-index: 2000;
}
@keyframes floatUp { 0%{opacity:1;transform:translateY(0)} 100%{opacity:0;transform:translateY(-100px)} }

/* Responsive */
@media(max-width:768px) {
  .sidebar { width: 200px; }
  .options-grid { grid-template-columns: 1fr; }
  .report-grid { grid-template-columns: 1fr 1fr; }
}
@media(max-width:600px) {
  #screen-main { flex-direction: column; }
  .sidebar { width: 100%; min-height: auto; flex-direction: row; flex-wrap: wrap; }
  .sidebar-nav { display: none; }
}

.badge {
  display: inline-block;
  font-size: 0.7rem;
  padding: 3px 10px;
  border-radius: 20px;
  font-weight: 800;
  letter-spacing: 1px;
}
.badge-blue { background: rgba(74,144,226,0.2); color: #4a90e2; border: 1px solid #4a90e2; }
.badge-yellow { background: rgba(251,208,0,0.2); color: var(--mario-yellow); border: 1px solid var(--mario-yellow); }
.badge-green { background: rgba(67,176,71,0.2); color: var(--mario-green); border: 1px solid var(--mario-green); }

.section-divider {
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
  margin: 20px 0;
}

/* Map visual */
.map-mini {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  padding: 15px;
  background: rgba(0,0,0,0.2);
  border-radius: 12px;
  margin: 15px 0;
}
.map-dot {
  width: 35px; height: 35px;
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 1.1rem;
  border: 2px solid rgba(255,255,255,0.2);
  cursor: pointer;
  transition: all 0.2s;
}
.map-dot.done { background: var(--mario-green); border-color: var(--mario-green); }
.map-dot.active { background: var(--mario-yellow); border-color: var(--mario-yellow); animation: pulse 1.5s infinite; }
.map-dot.locked { background: rgba(255,255,255,0.05); opacity: 0.4; }
@keyframes pulse { 0%,100%{box-shadow:0 0 0 0 rgba(251,208,0,0.4)} 50%{box-shadow:0 0 0 8px rgba(251,208,0,0)} }
</style>
</head>
<body>

<!-- ===== INTRO SCREEN ===== -->
<div id="screen-intro" class="screen active">
  <div class="clouds-container">
    <div class="cloud"><span>☁️</span></div>
    <div class="cloud"><span>☁️</span></div>
    <div class="cloud"><span>☁️</span></div>
  </div>
  <div class="intro-content">
    <div class="game-title">🎮 PRESENTACIONES<br>DIGITALES</div>
    <div class="subtitle-intro">Grado 801 — Tecnología e Informática</div>
    <div class="mario-character" onclick="document.getElementById('screen-intro').classList.remove('active'); document.getElementById('screen-name').classList.add('active')">🧑‍🦱</div>
    <p style="color:rgba(255,255,255,0.7); margin-bottom: 15px; font-size:0.9rem;">8 Estaciones • Retos • Monedas • ¡Aventura!</p>
    <button class="btn-start" onclick="document.getElementById('screen-intro').classList.remove('active'); document.getElementById('screen-name').classList.add('active')">
      ▶ PRESIONA START
    </button>
  </div>
  <div class="ground-row">
    <span class="coin">🪙</span><span>🍄</span><span class="coin">🪙</span>
    <span>⭐</span><span class="coin">🪙</span><span>🍄</span><span class="coin">🪙</span>
  </div>
</div>

<!-- ===== NAME SCREEN ===== -->
<div id="screen-name" class="screen" style="flex-direction:column;align-items:center;justify-content:center;background:linear-gradient(135deg,#1a1a2e,#0f3460)">
  <div class="name-card">
    <div style="font-size:3rem;margin-bottom:15px">🎮</div>
    <h2>¡BIENVENIDO/A!</h2>
    <p>Ingresa tu nombre completo para comenzar la aventura</p>
    <input type="text" class="name-input" id="studentName" placeholder="Tu nombre completo..." maxlength="60">
    <button class="btn-start" style="animation:none;width:100%" onclick="startGame()">¡COMENZAR AVENTURA! 🚀</button>
  </div>
</div>

<!-- ===== MAIN DASHBOARD ===== -->
<div id="screen-main" class="screen">
  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="sidebar-logo">
      <div class="sena-badge">SENA</div>
      <div class="sidebar-title">PRESENTACIONES<br>DIGITALES<br>🎮 801</div>
    </div>
    <div class="sidebar-player">
      <div class="player-avatar">🧑‍🦱</div>
      <div class="player-name" id="sidebarName">Jugador</div>
      <div class="player-score" id="sidebarScore">🪙 0 MONEDAS</div>
    </div>
    <div class="sidebar-nav">
      <div class="nav-label">Mapa de Estaciones</div>
      <div id="navItems"></div>
    </div>
    <div class="progress-bar-wrap">
      <div class="progress-label">
        <span>Progreso</span>
        <span id="progressPct">0%</span>
      </div>
      <div class="progress-track">
        <div class="progress-fill" id="progressFill" style="width:0%"></div>
      </div>
    </div>
  </aside>

  <!-- MAIN AREA -->
  <main class="main-content">
    <div class="topbar">
      <div class="topbar-station" id="topbarStation">ESTACIÓN 1</div>
      <div class="lives-display">
        <span class="life">❤️</span><span class="life">❤️</span><span class="life">❤️</span>
      </div>
      <div class="coins-display" id="topbarCoins">🪙 0</div>
    </div>
    <div class="station-area" id="stationArea">
      <!-- content injected here -->
    </div>
  </main>
</div>

<!-- ===== REPORT SCREEN ===== -->
<div id="screen-report" class="screen">
  <div class="report-card">
    <div class="report-title">🏆 MISIÓN<br>COMPLETADA!</div>
    <div class="report-player">
      <div class="avatar">🧑‍🦱⭐</div>
      <div class="rname" id="reportName">Estudiante</div>
      <div class="rscore" id="reportScore">🪙 0 MONEDAS RECOLECTADAS</div>
    </div>
    <div class="report-grid">
      <div class="report-stat">
        <div class="stat-val" id="repStations">8/8</div>
        <div class="stat-label">Estaciones Completadas</div>
      </div>
      <div class="report-stat">
        <div class="stat-val" id="repCoins">0</div>
        <div class="stat-label">🪙 Monedas</div>
      </div>
      <div class="report-stat">
        <div class="stat-val" id="repTime">--</div>
        <div class="stat-label">Tiempo Total</div>
      </div>
      <div class="report-stat">
        <div class="stat-val" id="repGrade">A+</div>
        <div class="stat-label">Calificación</div>
      </div>
    </div>
    <div class="stations-summary" id="stationsSummary"></div>
    <div class="teacher-section">
      <h4>📋 REPORTE PARA EL DOCENTE</h4>
      <p id="teacherReport"></p>
    </div>
    <button class="btn-print" onclick="window.print()">🖨️ IMPRIMIR REPORTE PARA EL DOCENTE</button>
    <button class="btn-print" style="background:var(--mario-blue);margin-top:10px" onclick="restartGame()">🔄 JUGAR DE NUEVO</button>
  </div>
</div>

<!-- OVERLAY + FEEDBACK -->
<div class="overlay" id="overlay"></div>
<div class="feedback-popup" id="feedbackPopup">
  <div class="feedback-emoji" id="feedbackEmoji"></div>
  <div class="feedback-title" id="feedbackTitle"></div>
  <div class="feedback-msg" id="feedbackMsg"></div>
  <div class="feedback-coins" id="feedbackCoins"></div>
  <button class="btn-submit" style="margin-top:15px" onclick="closeFeedback()" id="feedbackBtn">CONTINUAR ▶</button>
</div>

<script>
// ============================================================
// DATA
// ============================================================
const stations = [
  {
    id: 1, emoji: '🏰', name: 'Castillo de Inicio',
    subtitle: 'Objetivo del Taller',
    color: '#e52521',
    content: `
      <div class="content-card">
        <h3>🎯 Objetivo del Taller</h3>
        <p>¡Bienvenido, valiente aventurero digital! En este taller aprenderás a crear presentaciones digitales impactantes que comuniquen tus ideas con claridad, creatividad y profesionalismo.</p>
        <div class="highlight-box">
          🏆 Al completar este taller, serás capaz de diseñar presentaciones digitales estructuradas, visualmente atractivas y comunicativamente efectivas.
        </div>
        <h3 style="margin-top:20px">🎮 Capacidades que Desarrollarás</h3>
        <ul>
          <li>🖼️ <strong>Diseño visual:</strong> Elegir colores, tipografías e imágenes que comuniquen.</li>
          <li>📝 <strong>Redacción clara:</strong> Estructurar ideas de forma concisa y ordenada.</li>
          <li>🗣️ <strong>Exposición oral:</strong> Presentar frente a un público con seguridad.</li>
          <li>💻 <strong>Dominio de herramientas digitales:</strong> PowerPoint, Google Slides, Canva y más.</li>
          <li>🧠 <strong>Pensamiento crítico:</strong> Seleccionar información relevante y organizarla lógicamente.</li>
        </ul>
        <div class="tip-box">
          <strong>💡 Dato Mario Bros:</strong> Así como Mario recolecta monedas en cada nivel, tú recolectarás conocimiento en cada estación. ¡Cada habilidad que aprendes es una estrella más para tu inventario!
        </div>
      </div>
      <div class="content-card">
        <h3>🗺️ Tu Misión</h3>
        <p>Deberás recorrer <strong>8 estaciones</strong> superando retos de conocimiento. Al completar cada reto, desbloquearás la siguiente estación y ganarás monedas.</p>
        <div class="map-mini" id="miniMap"></div>
      </div>
    `,
    challenge: {
      type: 'mc',
      question: '¿Cuál de las siguientes es una capacidad que desarrollarás en este taller?',
      options: ['Programar videojuegos', 'Diseñar presentaciones digitales efectivas', 'Crear páginas web', 'Editar videos profesionales'],
      correct: 1,
      coins: 10
    }
  },
  {
    id: 2, emoji: '🌍', name: 'El Mundo de la Información',
    subtitle: 'Importancia de las Presentaciones',
    color: '#4a90e2',
    content: `
      <div class="content-card">
        <h3>📡 ¿Por qué importan las Presentaciones Digitales?</h3>
        <p>Vivimos en la <strong>Era de la Información</strong>. Cada día, millones de personas comparten ideas a través de presentaciones digitales en escuelas, empresas, eventos y redes sociales.</p>
        <p>Una presentación digital bien diseñada puede:</p>
        <ul>
          <li>✅ Convencer a una audiencia de apoyar tu idea o proyecto.</li>
          <li>✅ Explicar conceptos complejos de forma sencilla y visual.</li>
          <li>✅ Demostrar tu nivel de conocimiento y preparación.</li>
          <li>✅ Diferenciarte de otros estudiantes o profesionales.</li>
          <li>✅ Quedarse en la memoria de quien la ve.</li>
        </ul>
        <div class="highlight-box">
          📊 Según estudios, el 65% de las personas son <strong>aprendices visuales</strong>. Una imagen o gráfico comunica hasta 3 veces más rápido que solo texto.
        </div>
      </div>
      <div class="content-card">
        <h3>🔑 Características de una Buena Presentación</h3>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-top:10px">
          <div style="background:rgba(74,144,226,0.1);border-radius:10px;padding:12px;border:1px solid rgba(74,144,226,0.3)">
            <strong style="color:#4a90e2">✔️ TIENE</strong><br>
            <small>• Texto breve y claro<br>• Imágenes relevantes<br>• Estructura lógica<br>• Colores armónicos</small>
          </div>
          <div style="background:rgba(229,37,33,0.1);border-radius:10px;padding:12px;border:1px solid rgba(229,37,33,0.3)">
            <strong style="color:#ff6b6b">❌ NO TIENE</strong><br>
            <small>• Párrafos enormes<br>• Muchas fuentes distintas<br>• Imágenes de baja calidad<br>• Colores que cansan</small>
          </div>
        </div>
        <div class="tip-box" style="margin-top:15px">
          <strong>🎮 Regla de Oro:</strong> "Una diapositiva = Una idea principal". Igual que en Mario Bros: ¡un nivel a la vez!
        </div>
      </div>
    `,
    challenge: {
      type: 'mc',
      question: '¿Qué porcentaje de personas son aprendices visuales según los estudios mencionados?',
      options: ['35%', '50%', '65%', '80%'],
      correct: 2,
      coins: 10
    }
  },
  {
    id: 3, emoji: '⚡', name: 'Selector de Poder',
    subtitle: 'Elige tu Herramienta Digital',
    color: '#fbd000',
    content: `
      <div class="content-card">
        <h3>🛠️ Elige tu Herramienta</h3>
        <p>¡Así como Mario elige su power-up, tú debes elegir la herramienta perfecta para crear tu presentación! Cada una tiene superpoderes únicos.</p>
        <div class="tools-grid" id="toolsGrid">
          <div class="tool-card" onclick="selectTool(this,'PowerPoint')">
            <div class="tool-emoji">📊</div>
            <div class="tool-name">PowerPoint</div>
            <div class="tool-desc">El clásico de Microsoft. Potente y profesional.</div>
          </div>
          <div class="tool-card" onclick="selectTool(this,'Google Slides')">
            <div class="tool-emoji">🎨</div>
            <div class="tool-name">Google Slides</div>
            <div class="tool-desc">Gratuito, online y colaborativo en tiempo real.</div>
          </div>
          <div class="tool-card" onclick="selectTool(this,'Canva')">
            <div class="tool-emoji">✨</div>
            <div class="tool-name">Canva</div>
            <div class="tool-desc">Diseños increíbles con plantillas modernas.</div>
          </div>
          <div class="tool-card" onclick="selectTool(this,'Prezi')">
            <div class="tool-emoji">🌀</div>
            <div class="tool-name">Prezi</div>
            <div class="tool-desc">Presentaciones dinámicas y con zoom visual.</div>
          </div>
          <div class="tool-card" onclick="selectTool(this,'LibreOffice')">
            <div class="tool-emoji">🆓</div>
            <div class="tool-name">LibreOffice</div>
            <div class="tool-desc">Gratuito y sin internet. Ideal para cualquier PC.</div>
          </div>
        </div>
        <div id="toolInfo" style="display:none" class="highlight-box">
          Has seleccionado: <span id="toolSelected">-</span> ¡Excelente elección!
        </div>
      </div>
      <div class="content-card">
        <h3>📊 Comparativa de Herramientas</h3>
        <table style="width:100%;border-collapse:collapse;font-size:0.8rem">
          <tr style="background:rgba(251,208,0,0.1)">
            <th style="padding:10px;text-align:left;border-bottom:1px solid rgba(255,255,255,0.1)">Herramienta</th>
            <th style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.1)">Gratuita</th>
            <th style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.1)">Online</th>
            <th style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.1)">Colaborativa</th>
            <th style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.1)">Dificultad</th>
          </tr>
          <tr>
            <td style="padding:10px;border-bottom:1px solid rgba(255,255,255,0.05)">📊 PowerPoint</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">❌</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">✅</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">✅</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">⭐⭐⭐</td>
          </tr>
          <tr>
            <td style="padding:10px;border-bottom:1px solid rgba(255,255,255,0.05)">🎨 Google Slides</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">✅</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">✅</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">✅</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">⭐⭐</td>
          </tr>
          <tr>
            <td style="padding:10px;border-bottom:1px solid rgba(255,255,255,0.05)">✨ Canva</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">✅</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">✅</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">✅</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">⭐</td>
          </tr>
          <tr>
            <td style="padding:10px;border-bottom:1px solid rgba(255,255,255,0.05)">🌀 Prezi</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">⚠️</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">✅</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">✅</td>
            <td style="padding:10px;text-align:center;border-bottom:1px solid rgba(255,255,255,0.05)">⭐⭐⭐⭐</td>
          </tr>
          <tr>
            <td style="padding:10px">🆓 LibreOffice</td>
            <td style="padding:10px;text-align:center">✅</td>
            <td style="padding:10px;text-align:center">❌</td>
            <td style="padding:10px;text-align:center">❌</td>
            <td style="padding:10px;text-align:center">⭐⭐</td>
          </tr>
        </table>
      </div>
    `,
    challenge: {
      type: 'tool',
      question: '¿Cuál herramienta seleccionas para crear tu presentación? (Elige una de las tarjetas de arriba y explica por qué la elegiste)',
      coins: 15
    }
  },
  {
    id: 4, emoji: '📄', name: 'La Portada',
    subtitle: 'Primera impresión que impacta',
    color: '#43b047',
    content: `
      <div class="content-card">
        <h3>🎭 ¿Qué es una Portada?</h3>
        <p>La portada es la <strong>primera diapositiva</strong> de tu presentación. Es como la portada de un libro o el menú principal de un videojuego: debe ser atractiva, clara y dar ganas de seguir viendo.</p>
        <p>Una buena portada comunica en segundos:</p>
        <ul>
          <li>📌 El <strong>título del tema</strong> (grande y claro)</li>
          <li>👤 El <strong>nombre del autor/autores</strong></li>
          <li>🏫 La <strong>institución, grado y grupo</strong></li>
          <li>📅 La <strong>fecha</strong> de presentación</li>
          <li>🖼️ Una <strong>imagen o elemento visual</strong> relacionado con el tema</li>
        </ul>
        <div class="highlight-box">
          ⚠️ La portada NO debe tener demasiado texto. Recuerda: <strong>¡menos es más!</strong>
        </div>
      </div>
      <div class="content-card">
        <h3>🎨 Consejos de Diseño para tu Portada</h3>
        <ul>
          <li>🎨 Usa colores que vayan con el tema de tu presentación.</li>
          <li>✏️ Elige máximo 2 fuentes tipográficas diferentes.</li>
          <li>🖼️ Usa una imagen de alta calidad (sin pixeles).</li>
          <li>📐 Respeta los márgenes y no llenes todos los espacios.</li>
          <li>🎯 El título debe ser lo más grande y visible de la diapositiva.</li>
        </ul>
        <div class="tip-box">
          <strong>🎮 Truco Pro:</strong> Busca la plantilla de tu herramienta que más te guste como base. ¡No tienes que diseñar desde cero!
        </div>
        <div style="margin-top:15px;display:flex;flex-wrap:wrap;gap:10px">
          <a href="https://www.canva.com/presentations/templates/" target="_blank" class="btn-example">🔗 Ver ejemplo en Canva</a>
          <a href="https://slidesgo.com/es/tema/presentaciones-de-cole-para-estudiantes" target="_blank" class="btn-example yellow">🔗 Ver ejemplos Slidesgo</a>
        </div>
      </div>
    `,
    challenge: {
      type: 'mc',
      question: '¿Cuáles son los elementos ESENCIALES que debe tener una portada? Selecciona la opción más completa:',
      options: [
        'Título, logos de redes sociales y memes',
        'Título, nombre del autor, institución, grado y fecha',
        'Solo el título con letra grande y colorida',
        'El nombre del docente, el logo del colegio y muchas imágenes'
      ],
      correct: 1,
      coins: 10
    }
  },
  {
    id: 5, emoji: '📝', name: 'La Introducción',
    subtitle: 'Presenta tu tema y a ti mismo',
    color: '#9b59b6',
    content: `
      <div class="content-card">
        <h3>👋 ¿Qué es la Introducción?</h3>
        <p>La introducción es donde <strong>conectas con tu audiencia</strong> antes de entrar al tema. Es tu momento para presentarte, generar interés y anticipar lo que van a aprender.</p>
        <p>Una buena introducción tiene dos partes:</p>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:15px;margin:15px 0">
          <div style="background:rgba(155,89,182,0.15);border-radius:12px;padding:15px;border:1px solid rgba(155,89,182,0.4)">
            <strong style="color:#c39bd3">👤 Presentación Personal</strong>
            <ul style="margin-top:10px;font-size:0.85rem">
              <li>Tu nombre completo</li>
              <li>Tu grado y colegio</li>
              <li>Por qué elegiste el tema</li>
              <li>Algo que te conecte con el tema</li>
            </ul>
          </div>
          <div style="background:rgba(155,89,182,0.15);border-radius:12px;padding:15px;border:1px solid rgba(155,89,182,0.4)">
            <strong style="color:#c39bd3">📚 Introducción al Tema</strong>
            <ul style="margin-top:10px;font-size:0.85rem">
              <li>¿De qué trata tu tema?</li>
              <li>¿Por qué es importante?</li>
              <li>¿Qué van a aprender?</li>
              <li>Pregunta o dato curioso</li>
            </ul>
          </div>
        </div>
      </div>
      <div class="content-card">
        <h3>✍️ Ejemplo de Introducción</h3>
        <div style="background:rgba(0,0,0,0.3);border-radius:10px;padding:20px;border-left:4px solid #9b59b6;font-style:italic;font-size:0.9rem;color:rgba(255,255,255,0.85);line-height:1.8">
          "Buenos días. Mi nombre es <strong>[Tu Nombre]</strong>, soy estudiante de grado 801. Elegí hablar sobre <strong>[Tu Tema]</strong> porque me parece fascinante y muy útil en la vida diaria. Hoy les mostraré los aspectos más importantes, y al final serán capaces de comprender por qué <strong>[Tu Tema]</strong> es relevante para todos nosotros. ¿Sabían que...? <em>[Dato curioso]</em>"
        </div>
        <div class="tip-box" style="margin-top:15px">
          <strong>🎮 Combo de Inicio:</strong> Empieza con una pregunta o un dato sorprendente. ¡Así atraparás la atención de tu audiencia como Mario atrapa una estrella!
        </div>
        <div style="margin-top:15px;display:flex;flex-wrap:wrap;gap:10px">
          <a href="https://www.ejemplos.co/20-ejemplos-de-introduccion-para-una-presentacion/" target="_blank" class="btn-example">🔗 Ver ejemplos de introducción</a>
          <a href="https://www.toastmasters.org/resources/public-speaking-tips/how-to-start-a-speech" target="_blank" class="btn-example yellow">🔗 Tips de presentación oral</a>
        </div>
      </div>
    `,
    challenge: {
      type: 'mc',
      question: '¿Cuál es el mejor inicio para una presentación ante tu clase?',
      options: [
        '"Hola, buenas, yo soy el que va a hablar de... esto."',
        '"Buenos días. Mi nombre es [Nombre], hoy les hablaré sobre [Tema] y al finalizar comprenderán por qué..."',
        'Leer todo el texto de la diapositiva sin mirar al público.',
        'Empezar directamente con los datos sin presentarse.'
      ],
      correct: 1,
      coins: 10
    }
  },
  {
    id: 6, emoji: '📚', name: 'Marco Teórico',
    subtitle: 'El corazón de tu presentación',
    color: '#e67e22',
    content: `
      <div class="content-card">
        <h3>🧱 ¿Qué es el Marco Teórico?</h3>
        <p>El marco teórico es el <strong>núcleo de tu presentación</strong>. Aquí desarrollas el contenido central: conceptos, datos, explicaciones e información que respaldan tu tema con bases concretas.</p>
        <p>Debe estar estructurado de forma lógica, de lo más general a lo más específico:</p>
        <div style="display:flex;flex-direction:column;gap:10px;margin:15px 0">
          <div style="background:rgba(230,126,34,0.15);border-radius:10px;padding:12px 18px;border-left:4px solid #e67e22;display:flex;align-items:center;gap:12px">
            <span style="font-size:1.5rem">1️⃣</span>
            <div><strong>Contexto General</strong><br><small style="color:rgba(255,255,255,0.6)">¿Cuál es el panorama global del tema?</small></div>
          </div>
          <div style="background:rgba(230,126,34,0.15);border-radius:10px;padding:12px 18px;border-left:4px solid #e67e22;display:flex;align-items:center;gap:12px">
            <span style="font-size:1.5rem">2️⃣</span>
            <div><strong>Conceptos Clave</strong><br><small style="color:rgba(255,255,255,0.6)">Definiciones importantes con tus propias palabras</small></div>
          </div>
          <div style="background:rgba(230,126,34,0.15);border-radius:10px;padding:12px 18px;border-left:4px solid #e67e22;display:flex;align-items:center;gap:12px">
            <span style="font-size:1.5rem">3️⃣</span>
            <div><strong>Desarrollo del Tema</strong><br><small style="color:rgba(255,255,255,0.6)">Datos, ejemplos, subtemas específicos</small></div>
          </div>
          <div style="background:rgba(230,126,34,0.15);border-radius:10px;padding:12px 18px;border-left:4px solid #e67e22;display:flex;align-items:center;gap:12px">
            <span style="font-size:1.5rem">4️⃣</span>
            <div><strong>Análisis o Reflexión</strong><br><small style="color:rgba(255,255,255,0.6)">Tu opinión fundamentada o análisis del tema</small></div>
          </div>
        </div>
      </div>
      <div class="content-card">
        <h3>📏 Reglas de Oro para las Diapositivas</h3>
        <div class="highlight-box">🎮 Regla 6×6: Máximo <strong>6 líneas por diapositiva</strong> y máximo <strong>6 palabras por línea</strong>. ¡Las diapositivas son un apoyo, no un libro!</div>
        <ul style="margin-top:15px">
          <li>📌 Usa <strong>viñetas o numeración</strong> para organizar las ideas.</li>
          <li>🖼️ Acompaña cada concepto con una imagen o gráfico relacionado.</li>
          <li>🔗 Cita tus fuentes al pie de cada diapositiva con texto pequeño.</li>
          <li>🎨 Mantén el mismo estilo visual en todas las diapositivas.</li>
          <li>📊 Usa gráficos o tablas cuando tengas datos estadísticos.</li>
        </ul>
        <div style="margin-top:15px;display:flex;flex-wrap:wrap;gap:10px">
          <a href="https://support.microsoft.com/es-es/office/crear-una-presentaci%C3%B3n-en-powerpoint-422250f8-5721-4cea-92cc-202fa7b89617" target="_blank" class="btn-example">🔗 Tutorial PowerPoint Oficial</a>
          <a href="https://support.google.com/docs/answer/1696861?hl=es" target="_blank" class="btn-example yellow">🔗 Tutorial Google Slides</a>
        </div>
      </div>
    `,
    challenge: {
      type: 'mc',
      question: 'Según la "Regla 6×6", ¿cuántas palabras máximo debe tener cada línea de texto en una diapositiva?',
      options: ['3 palabras', '6 palabras', '10 palabras', 'Sin límite'],
      correct: 1,
      coins: 10
    }
  },
  {
    id: 7, emoji: '🖼️', name: 'Poderes Visuales',
    subtitle: 'Imágenes y Gráficos que Impactan',
    color: '#e91e63',
    content: `
      <div class="content-card">
        <h3>⚡ ¿Por qué usar Imágenes y Gráficos?</h3>
        <p>Las imágenes son el <strong>superpoder</strong> de las presentaciones. Una buena imagen puede comunicar en 3 segundos lo que un párrafo tarda 3 minutos en explicar.</p>
        <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:12px;margin:15px 0">
          <div style="text-align:center;background:rgba(233,30,99,0.1);border-radius:12px;padding:15px;border:1px solid rgba(233,30,99,0.3)">
            <div style="font-size:2rem">📷</div>
            <strong style="font-size:0.85rem;color:#f48fb1">Fotografías</strong>
            <p style="font-size:0.75rem;color:rgba(255,255,255,0.5);margin-top:5px">Evidencias reales y contexto visual</p>
          </div>
          <div style="text-align:center;background:rgba(233,30,99,0.1);border-radius:12px;padding:15px;border:1px solid rgba(233,30,99,0.3)">
            <div style="font-size:2rem">📊</div>
            <strong style="font-size:0.85rem;color:#f48fb1">Gráficos</strong>
            <p style="font-size:0.75rem;color:rgba(255,255,255,0.5);margin-top:5px">Datos estadísticos de forma visual</p>
          </div>
          <div style="text-align:center;background:rgba(233,30,99,0.1);border-radius:12px;padding:15px;border:1px solid rgba(233,30,99,0.3)">
            <div style="font-size:2rem">🗺️</div>
            <strong style="font-size:0.85rem;color:#f48fb1">Infografías</strong>
            <p style="font-size:0.75rem;color:rgba(255,255,255,0.5);margin-top:5px">Resumen visual completo</p>
          </div>
          <div style="text-align:center;background:rgba(233,30,99,0.1);border-radius:12px;padding:15px;border:1px solid rgba(233,30,99,0.3)">
            <div style="font-size:2rem">🎬</div>
            <strong style="font-size:0.85rem;color:#f48fb1">GIFs / Videos</strong>
            <p style="font-size:0.75rem;color:rgba(255,255,255,0.5);margin-top:5px">Animación que capta atención</p>
          </div>
        </div>
      </div>
      <div class="content-card">
        <h3>🔍 ¿Dónde conseguir imágenes LEGALES y GRATIS?</h3>
        <ul>
          <li>🖼️ <strong>Unsplash.com</strong> — Fotografías de alta calidad, sin copyright.</li>
          <li>🎨 <strong>Flaticon.com</strong> — Íconos y vectores gratuitos.</li>
          <li>🌐 <strong>Pixabay.com</strong> — Imágenes, vectores y videos libres.</li>
          <li>🔍 <strong>Google Imágenes</strong> (filtro: Uso libre) — Filtra por licencia.</li>
          <li>✨ <strong>Canva</strong> — Librería interna de imágenes gratuitas.</li>
        </ul>
        <div class="highlight-box" style="margin-top:15px">
          🚫 <strong>Nunca uses imágenes sin verificar la licencia.</strong> El plagio de imágenes es una falta ética y puede tener consecuencias legales.
        </div>
        <div class="tip-box">
          <strong>🎮 Truco de Diseño:</strong> Cuando insertes una imagen, asegúrate de que tenga fondo transparente (PNG) cuando quieras que se integre bien con el diseño de tu diapositiva.
        </div>
        <div style="margin-top:15px;display:flex;flex-wrap:wrap;gap:10px">
          <a href="https://unsplash.com" target="_blank" class="btn-example">🖼️ Ir a Unsplash</a>
          <a href="https://www.canva.com/graphs/" target="_blank" class="btn-example yellow">📊 Crear gráficos en Canva</a>
          <a href="https://pixabay.com/es/" target="_blank" class="btn-example green">🎨 Ir a Pixabay</a>
        </div>
      </div>
    `,
    challenge: {
      type: 'mc',
      question: '¿Qué sitio web ofrece fotografías de alta calidad totalmente gratuitas y sin problemas de copyright?',
      options: ['Google Imágenes (sin filtros)', 'Unsplash.com', 'Pinterest.com', 'Instagram.com'],
      correct: 1,
      coins: 10
    }
  },
  {
    id: 8, emoji: '🏁', name: 'Bandera Final',
    subtitle: 'Conclusiones que perduran',
    color: '#fbd000',
    content: `
      <div class="content-card">
        <h3>🏆 ¿Qué son las Conclusiones?</h3>
        <p>Las conclusiones son el <strong>final poderoso</strong> de tu presentación. Es tu última oportunidad de dejar una huella en la audiencia, reforzar tu mensaje y demostrar lo que aprendiste.</p>
        <p>Una conclusión efectiva NO es repetir lo que ya dijiste. Es <strong>sintetizar, reflexionar e impactar</strong>.</p>
        <div style="background:linear-gradient(135deg,rgba(251,208,0,0.1),rgba(251,208,0,0.05));border:2px solid rgba(251,208,0,0.3);border-radius:15px;padding:20px;margin:15px 0">
          <strong style="color:var(--mario-yellow)">🎯 Estructura de una Conclusión Perfecta:</strong>
          <ol style="margin-top:12px;padding-left:20px">
            <li style="margin-bottom:8px;font-size:0.9rem"><strong>Síntesis:</strong> Resume las 3 ideas principales en máximo 2 oraciones.</li>
            <li style="margin-bottom:8px;font-size:0.9rem"><strong>Reflexión personal:</strong> ¿Qué aprendiste tú? ¿Qué cambió en tu forma de ver el tema?</li>
            <li style="margin-bottom:8px;font-size:0.9rem"><strong>Llamado a la acción:</strong> ¿Qué quieres que haga o piense tu audiencia?</li>
            <li style="margin-bottom:8px;font-size:0.9rem"><strong>Cierre memorable:</strong> Una frase potente, una pregunta o un dato impactante.</li>
          </ol>
        </div>
      </div>
      <div class="content-card">
        <h3>✍️ Ejemplo de Conclusión</h3>
        <div style="background:rgba(0,0,0,0.3);border-radius:10px;padding:20px;border-left:4px solid var(--mario-yellow);font-size:0.9rem;color:rgba(255,255,255,0.85);line-height:1.8;font-style:italic">
          "En conclusión, hemos aprendido que <strong>[Idea 1]</strong>, <strong>[Idea 2]</strong> y <strong>[Idea 3]</strong> son los pilares fundamentales de <strong>[Tu Tema]</strong>. Personalmente, este trabajo me hizo reflexionar sobre <strong>[reflexión]</strong>. Los invito a <strong>[llamado a la acción]</strong>. Recuerden: <strong>[Frase poderosa o cita]</strong>. ¡Muchas gracias por su atención!"
        </div>
        <div class="tip-box" style="margin-top:15px">
          <strong>🎮 Boss Final:</strong> ¡Tu conclusión es el jefe final del juego! Prepárala bien, practica en voz alta y termina con confianza. Un final poderoso se recuerda siempre.
        </div>
        <div class="highlight-box">
          ⭐ Las mejores conclusiones duran entre <strong>1 y 2 minutos</strong> cuando las presentas oralmente. ¡Ni muy cortas ni muy largas!
        </div>
        <div style="margin-top:15px;display:flex;flex-wrap:wrap;gap:10px">
          <a href="https://www.ejemplos.co/ejemplos-de-conclusion/" target="_blank" class="btn-example">🔗 Ejemplos de conclusiones</a>
          <a href="https://www.ted.com/talks?language=es" target="_blank" class="btn-example yellow">🎤 Ver presentaciones TED en español</a>
        </div>
      </div>
    `,
    challenge: {
      type: 'open',
      question: '¡RETO FINAL! 🏆 Escribe una conclusión breve (3-4 oraciones) para una presentación imaginaria sobre "El impacto de las redes sociales en los jóvenes". Usa la estructura que aprendiste.',
      coins: 20
    }
  }
];

// ============================================================
// GAME STATE
// ============================================================
let gameState = {
  playerName: '',
  currentStation: 0,
  completedStations: [],
  coins: 0,
  selectedTool: '',
  startTime: null,
  answers: {}
};

const feedbackMessages = {
  correct: [
    { title: '¡SÚPER!', emoji: '⭐', msg: '¡Correcto! Eres más inteligente que el rey Koopa. ¡Sigues adelante!' },
    { title: '¡GENIAL!', emoji: '🍄', msg: '¡Power-up activado! Respuesta perfecta. ¡Nivel desbloqueado!' },
    { title: '¡PERFECTO!', emoji: '🌟', msg: '¡Estrella conseguida! Esa era la respuesta exacta. ¡Eres increíble!' },
    { title: '¡EXCELENTE!', emoji: '🏆', msg: '¡Golpeaste el bloque correcto! Tu mente es más rápida que Mario.' }
  ],
  wrong: [
    { title: '¡OOPS!', emoji: '💀', msg: 'Caíste en el hoyo, pero Mario siempre vuelve a empezar. ¡Inténtalo de nuevo!' },
    { title: '¡UY!', emoji: '🐢', msg: 'Un Goomba te atrapó esta vez. ¡Lee de nuevo el contenido y lo lograrás!' },
    { title: '¡CASI!', emoji: '🔴', msg: 'Esta vez no fue. Pero recuerda: ¡Mario nunca se rinde!' }
  ],
  open: [
    { title: '¡MISIÓN CUMPLIDA!', emoji: '🎯', msg: '¡Respuesta enviada! El docente revisará tu trabajo. ¡Sigue así!' }
  ]
};

// ============================================================
// INIT
// ============================================================
function startGame() {
  const name = document.getElementById('studentName').value.trim();
  if (!name || name.length < 3) {
    alert('Por favor ingresa tu nombre completo (mínimo 3 caracteres)');
    return;
  }
  gameState.playerName = name;
  gameState.startTime = new Date();
  gameState.currentStation = 0;

  document.getElementById('sidebarName').textContent = name;
  document.getElementById('screen-name').classList.remove('active');
  document.getElementById('screen-main').classList.add('active');

  buildNav();
  loadStation(0);
}

function buildNav() {
  const container = document.getElementById('navItems');
  container.innerHTML = '';
  stations.forEach((s, i) => {
    const done = gameState.completedStations.includes(i);
    const active = i === gameState.currentStation;
    const locked = !done && i !== gameState.currentStation;
    const div = document.createElement('div');
    div.className = `station-nav-item ${done ? 'completed' : ''} ${active ? 'active' : ''} ${locked ? 'locked' : ''}`;
    div.innerHTML = `
      <span class="nav-icon">${s.emoji}</span>
      <span class="nav-text">Est. ${s.id}<br>${s.name}</span>
      <span class="nav-status">${done ? '✅' : active ? '▶️' : '🔒'}</span>
    `;
    if (!locked) div.onclick = () => loadStation(i);
    container.appendChild(div);
  });
  updateProgress();
}

function updateProgress() {
  const pct = Math.round((gameState.completedStations.length / stations.length) * 100);
  document.getElementById('progressFill').style.width = pct + '%';
  document.getElementById('progressPct').textContent = pct + '%';
  document.getElementById('sidebarScore').textContent = `🪙 ${gameState.coins} MONEDAS`;
  document.getElementById('topbarCoins').textContent = `🪙 ${gameState.coins}`;
}

function loadStation(index) {
  gameState.currentStation = index;
  const s = stations[index];
  document.getElementById('topbarStation').textContent = `ESTACIÓN ${s.id} — ${s.name.toUpperCase()}`;

  const area = document.getElementById('stationArea');
  area.innerHTML = `
    <div class="station-header">
      <div class="station-number">${String(s.id).padStart(2,'0')}</div>
      <div class="station-emoji">${s.emoji}</div>
      <div class="station-info">
        <h1>${s.name}</h1>
        <p>${s.subtitle}</p>
        <div style="margin-top:8px">
          <span class="badge badge-yellow">🪙 +${s.challenge.coins} monedas</span>
          ${gameState.completedStations.includes(index) ? '<span class="badge badge-green" style="margin-left:8px">✅ Completada</span>' : ''}
        </div>
      </div>
    </div>
    ${s.content}
    ${renderChallenge(s, index)}
  `;

  // Build mini map if station 1
  if (index === 0) {
    const mm = document.getElementById('miniMap');
    if (mm) {
      stations.forEach((st, i) => {
        const dot = document.createElement('div');
        const done = gameState.completedStations.includes(i);
        const active = i === gameState.currentStation;
        dot.className = `map-dot ${done ? 'done' : active ? 'active' : 'locked'}`;
        dot.title = st.name;
        dot.textContent = st.emoji;
        mm.appendChild(dot);
      });
    }
  }

  buildNav();
  area.scrollTop = 0;
  window.scrollTo(0, 0);
}

function renderChallenge(s, index) {
  const done = gameState.completedStations.includes(index);
  const ch = s.challenge;

  if (ch.type === 'mc') {
    const opts = ch.options.map((o, i) =>
      `<button class="option-btn" onclick="answerMC(${index},${i})" ${done ? 'disabled' : ''}>${['A','B','C','D'][i]}) ${o}</button>`
    ).join('');
    return `
      <div class="challenge-section">
        <div class="challenge-header">🎮 RETO DE CONOCIMIENTO — Gana ${ch.coins} monedas</div>
        <div class="challenge-question">${ch.question}</div>
        <div class="options-grid">${opts}</div>
        ${done ? '<div style="color:var(--mario-green);font-weight:800;text-align:center">✅ ¡Reto Completado!</div>' : ''}
      </div>`;
  }

  if (ch.type === 'tool') {
    return `
      <div class="challenge-section">
        <div class="challenge-header">🎮 RETO DE ELECCIÓN — Gana ${ch.coins} monedas</div>
        <div class="challenge-question">${ch.question}</div>
        <textarea class="input-challenge" id="toolReason" placeholder="Escribe aquí por qué elegiste esa herramienta..." ${done ? 'disabled' : ''}>${gameState.answers[index] || ''}</textarea>
        <button class="btn-submit" onclick="answerTool(${index})" ${done ? 'disabled' : ''}>
          ${done ? '✅ ENVIADO' : '▶ ENVIAR RESPUESTA'}
        </button>
      </div>`;
  }

  if (ch.type === 'open') {
    return `
      <div class="challenge-section">
        <div class="challenge-header">🏆 RETO FINAL — Gana ${ch.coins} monedas</div>
        <div class="challenge-question">${ch.question}</div>
        <textarea class="input-challenge" id="openAnswer" placeholder="Escribe tu conclusión aquí..." rows="5" ${done ? 'disabled' : ''}>${gameState.answers[index] || ''}</textarea>
        <button class="btn-submit" onclick="answerOpen(${index})" ${done ? 'disabled' : ''}>
          ${done ? '✅ ENVIADO' : '▶ ENVIAR CONCLUSIÓN'}
        </button>
      </div>`;
  }

  return '';
}

// ============================================================
// ANSWER HANDLERS
// ============================================================
function selectTool(el, name) {
  document.querySelectorAll('.tool-card').forEach(c => c.classList.remove('selected'));
  el.classList.add('selected');
  gameState.selectedTool = name;
  document.getElementById('toolInfo').style.display = 'block';
  document.getElementById('toolSelected').textContent = name;
}

function answerMC(stationIndex, chosen) {
  if (gameState.completedStations.includes(stationIndex)) return;
  const ch = stations[stationIndex].challenge;
  const correct = chosen === ch.correct;

  document.querySelectorAll('.option-btn').forEach((btn, i) => {
    btn.disabled = true;
    if (i === ch.correct) btn.classList.add('correct');
    else if (i === chosen && !correct) btn.classList.add('wrong');
  });

  if (correct) {
    completeStation(stationIndex, ch.coins);
    const fb = feedbackMessages.correct[Math.floor(Math.random() * feedbackMessages.correct.length)];
    showFeedback(true, fb.emoji, fb.title, fb.msg, ch.coins, stationIndex);
  } else {
    const fb = feedbackMessages.wrong[Math.floor(Math.random() * feedbackMessages.wrong.length)];
    showFeedback(false, fb.emoji, fb.title, fb.msg, 0, stationIndex);
  }
}

function answerTool(stationIndex) {
  const reason = document.getElementById('toolReason')?.value?.trim();
  if (!gameState.selectedTool) { alert('¡Debes elegir una herramienta primero! Haz clic en una de las tarjetas.'); return; }
  if (!reason || reason.length < 15) { alert('Explica un poco más por qué elegiste esa herramienta (mínimo 15 caracteres).'); return; }
  gameState.answers[stationIndex] = reason;
  completeStation(stationIndex, stations[stationIndex].challenge.coins);
  const fb = feedbackMessages.correct[1];
  showFeedback(true, '⚡', '¡POWER SELECCIONADO!', `Elegiste ${gameState.selectedTool}. ¡Excelente elección de herramienta! Eres un verdadero jugador digital.`, stations[stationIndex].challenge.coins, stationIndex);
}

function answerOpen(stationIndex) {
  const answer = document.getElementById('openAnswer')?.value?.trim();
  if (!answer || answer.length < 30) { alert('Escribe una conclusión más completa (mínimo 30 caracteres).'); return; }
  gameState.answers[stationIndex] = answer;
  completeStation(stationIndex, stations[stationIndex].challenge.coins);
  const fb = feedbackMessages.open[0];
  showFeedback(true, fb.emoji, fb.title, fb.msg + ' ¡Llegaste a la BANDERA FINAL! 🏁🎉', stations[stationIndex].challenge.coins, stationIndex, true);
}

function completeStation(index, coins) {
  if (!gameState.completedStations.includes(index)) {
    gameState.completedStations.push(index);
    gameState.coins += coins;
    spawnCoins(coins);
  }
  buildNav();
  updateProgress();
}

function showFeedback(success, emoji, title, msg, coins, stationIndex, isFinal = false) {
  const popup = document.getElementById('feedbackPopup');
  const overlay = document.getElementById('overlay');
  document.getElementById('feedbackEmoji').textContent = emoji;
  document.getElementById('feedbackTitle').textContent = title;
  document.getElementById('feedbackTitle').className = `feedback-title ${success ? 'success' : 'fail'}`;
  document.getElementById('feedbackMsg').textContent = msg;
  document.getElementById('feedbackCoins').textContent = coins > 0 ? `+${coins} 🪙 monedas ganadas!` : '';

  const nextIndex = stationIndex + 1;
  const hasNext = nextIndex < stations.length;

  document.getElementById('feedbackBtn').textContent = isFinal ? 'VER REPORTE FINAL 🏆' : (success && hasNext ? 'SIGUIENTE ESTACIÓN ▶' : 'CERRAR ✕');
  document.getElementById('feedbackBtn').onclick = () => {
    closeFeedback();
    if (isFinal) showReport();
    else if (success && hasNext) loadStation(nextIndex);
    else if (!success) { /* stay */ }
  };

  popup.classList.add('show');
  overlay.classList.add('show');
}

function closeFeedback() {
  document.getElementById('feedbackPopup').classList.remove('show');
  document.getElementById('overlay').classList.remove('show');
}

function spawnCoins(count) {
  for (let i = 0; i < Math.min(count, 5); i++) {
    const coin = document.createElement('div');
    coin.className = 'float-coin';
    coin.textContent = '🪙';
    coin.style.left = (20 + Math.random() * 60) + 'vw';
    coin.style.top = (30 + Math.random() * 40) + 'vh';
    document.body.appendChild(coin);
    setTimeout(() => coin.remove(), 1000);
  }
}

// ============================================================
// REPORT
// ============================================================
function showReport() {
  const elapsed = Math.round((new Date() - gameState.startTime) / 60000);
  const grade = gameState.coins >= 80 ? 'A+' : gameState.coins >= 60 ? 'A' : gameState.coins >= 40 ? 'B' : 'C';

  document.getElementById('reportName').textContent = gameState.playerName;
  document.getElementById('reportScore').textContent = `🪙 ${gameState.coins} MONEDAS RECOLECTADAS`;
  document.getElementById('repStations').textContent = `${gameState.completedStations.length}/8`;
  document.getElementById('repCoins').textContent = gameState.coins;
  document.getElementById('repTime').textContent = elapsed + ' min';
  document.getElementById('repGrade').textContent = grade;

  const summary = document.getElementById('stationsSummary');
  summary.innerHTML = '<h4 style="font-weight:900;margin-bottom:12px;color:rgba(255,255,255,0.8)">📊 Detalle por Estación</h4>';
  stations.forEach((s, i) => {
    const done = gameState.completedStations.includes(i);
    summary.innerHTML += `
      <div class="station-summary-item ${done ? 'done' : ''}">
        <span class="ssi-icon">${s.emoji}</span>
        <span class="ssi-name">Estación ${s.id}: ${s.name}</span>
        <span class="ssi-status">${done ? `✅ +${s.challenge.coins}🪙` : '⏳ Pendiente'}</span>
      </div>`;
  });

  const openAnswers = gameState.answers[2] ? `Herramienta seleccionada: ${gameState.selectedTool}. ` : '';
  document.getElementById('teacherReport').textContent =
    `Estudiante: ${gameState.playerName} | Grado: 801 | ` +
    `Fecha: ${new Date().toLocaleDateString('es-CO')} | Tiempo: ${elapsed} min | ` +
    `Estaciones completadas: ${gameState.completedStations.length}/8 | ` +
    `Monedas: ${gameState.coins}/85 | Calificación: ${grade} | ` +
    openAnswers +
    `Taller: Presentaciones Digitales — Tecnología e Informática SENA.`;

  document.getElementById('screen-main').classList.remove('active');
  document.getElementById('screen-report').classList.add('active');
}

function restartGame() {
  gameState = { playerName: '', currentStation: 0, completedStations: [], coins: 0, selectedTool: '', startTime: null, answers: {} };
  document.getElementById('screen-report').classList.remove('active');
  document.getElementById('screen-intro').classList.add('active');
}
</script>
</body>
</html>
