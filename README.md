<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>DINESHKUMAR.S — Aizen Edition</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700;900&family=Share+Tech+Mono&family=Noto+Serif+JP:wght@300;400;700&display=swap');

  :root {
    --void:    #03010a;
    --panel:   #07030f;
    --spirit:  #9b59f5;
    --ghost:   #c49aff;
    --pale:    #e8d8ff;
    --deep:    #4a1a8c;
    --abyss:   #1a063a;
    --blood:   #6b0f8c;
    --silver:  #d4c8f0;
    --mist:    rgba(155,89,245,0.08);
    --glow-s:  0 0 12px #9b59f5, 0 0 30px #9b59f540, 0 0 60px #9b59f520;
    --glow-g:  0 0 8px #c49aff, 0 0 20px #c49aff50;
    --glow-p:  0 0 6px #e8d8ff60;
  }

  * { margin:0; padding:0; box-sizing:border-box; }

  body {
    background: var(--void);
    color: var(--ghost);
    font-family: 'Share Tech Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
    cursor: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 20 20'%3E%3Ccircle cx='10' cy='10' r='3' fill='none' stroke='%239b59f5' stroke-width='1.5'/%3E%3Cline x1='10' y1='0' x2='10' y2='6' stroke='%239b59f5' stroke-width='1'/%3E%3Cline x1='10' y1='14' x2='10' y2='20' stroke='%239b59f5' stroke-width='1'/%3E%3Cline x1='0' y1='10' x2='6' y2='10' stroke='%239b59f5' stroke-width='1'/%3E%3Cline x1='14' y1='10' x2='20' y2='10' stroke='%239b59f5' stroke-width='1'/%3E%3C/svg%3E") 10 10, crosshair;
  }

  /* NOISE TEXTURE via SVG filter approach using pseudo-element */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.05'/%3E%3C/svg%3E");
    opacity: 0.4;
    pointer-events: none;
    z-index: 999;
  }

  /* REIATSU GRID - subtle spiritual pressure lattice */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(155,89,245,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(155,89,245,0.04) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
    animation: gridDrift 20s linear infinite;
  }

  @keyframes gridDrift {
    0% { transform: translate(0,0); }
    100% { transform: translate(60px,60px); }
  }

  /* ══════════════════════════════════════
     CANVAS LAYERS
  ══════════════════════════════════════ */
  #reiatsu-canvas, #kido-canvas {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 1;
  }

  #kido-canvas { z-index: 2; opacity: 0.6; }

  /* ══════════════════════════════════════
     LAYOUT
  ══════════════════════════════════════ */
  .wrapper {
    position: relative;
    z-index: 10;
    max-width: 980px;
    margin: 0 auto;
    padding: 60px 28px 80px;
  }

  /* ══════════════════════════════════════
     HERO - AIZEN ENTRANCE
  ══════════════════════════════════════ */
  .hero {
    text-align: center;
    margin-bottom: 80px;
    position: relative;
  }

  /* Vertical kanji stripe on the left */
  .kanji-strip {
    position: absolute;
    left: -10px;
    top: 0;
    height: 100%;
    display: flex;
    flex-direction: column;
    gap: 12px;
    align-items: center;
    opacity: 0.12;
    font-family: 'Noto Serif JP', serif;
    font-size: 13px;
    color: var(--spirit);
    writing-mode: vertical-rl;
    letter-spacing: 6px;
    user-select: none;
    animation: kanjiFade 6s ease-in-out infinite;
  }

  @keyframes kanjiFade {
    0%, 100% { opacity: 0.12; }
    50% { opacity: 0.22; }
  }

  .eyecatch {
    font-family: 'Noto Serif JP', serif;
    font-size: 11px;
    letter-spacing: 8px;
    color: rgba(155,89,245,0.4);
    margin-bottom: 20px;
    animation: breathe 4s ease-in-out infinite;
  }

  @keyframes breathe {
    0%, 100% { opacity: 0.4; letter-spacing: 8px; }
    50% { opacity: 0.7; letter-spacing: 10px; }
  }

  /* MAIN NAME - Kyoka Suigetsu style */
  .hero-name {
    font-family: 'Cinzel', serif;
    font-size: clamp(38px, 7vw, 72px);
    font-weight: 900;
    letter-spacing: 8px;
    color: transparent;
    background: linear-gradient(180deg, var(--pale) 0%, var(--ghost) 40%, var(--spirit) 80%, var(--deep) 100%);
    -webkit-background-clip: text;
    background-clip: text;
    text-shadow: none;
    position: relative;
    display: inline-block;
    animation: nameReveal 2s cubic-bezier(0.16,1,0.3,1) forwards;
    filter: drop-shadow(0 0 18px rgba(155,89,245,0.6)) drop-shadow(0 0 40px rgba(155,89,245,0.3));
  }

  @keyframes nameReveal {
    0% { opacity: 0; transform: translateY(10px); letter-spacing: 20px; }
    100% { opacity: 1; transform: translateY(0); letter-spacing: 8px; }
  }

  /* SHATTER EFFECT on hover */
  .hero-name:hover {
    animation: kyokasuigetsu 0.6s steps(3) forwards;
  }

  @keyframes kyokasuigetsu {
    0%  { filter: drop-shadow(0 0 18px rgba(155,89,245,0.6)) drop-shadow(8px 0 0 rgba(196,154,255,0.8)) drop-shadow(-8px 0 0 rgba(74,26,140,0.8)); }
    33% { filter: drop-shadow(0 0 40px rgba(155,89,245,1)) drop-shadow(15px -5px 0 rgba(196,154,255,0.6)) drop-shadow(-12px 8px 0 rgba(74,26,140,0.6)); clip-path: polygon(0 0, 45% 0, 40% 100%, 0 100%); transform: translateX(-4px) skewX(-2deg); }
    66% { filter: drop-shadow(0 0 60px rgba(155,89,245,0.8)); clip-path: none; transform: translateX(3px); }
    100% { filter: drop-shadow(0 0 18px rgba(155,89,245,0.6)) drop-shadow(0 0 40px rgba(155,89,245,0.3)); transform: none; }
  }

  /* Zanpakuto kanji subtitle */
  .hero-zanpakuto {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 16px;
    margin: 18px 0 14px;
    font-family: 'Noto Serif JP', serif;
    font-size: 13px;
    color: rgba(155,89,245,0.5);
    letter-spacing: 3px;
  }

  .zanp-line {
    flex: 1;
    max-width: 120px;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(155,89,245,0.4));
  }
  .zanp-line.r { background: linear-gradient(90deg, rgba(155,89,245,0.4), transparent); }

  /* TITLE CHIPS - spiritual pressure style */
  .spirit-chips {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 8px;
    margin: 24px 0 20px;
  }

  .s-chip {
    font-family: 'Cinzel', serif;
    font-size: 9px;
    font-weight: 700;
    letter-spacing: 3px;
    padding: 7px 16px;
    border: 1px solid rgba(155,89,245,0.3);
    color: rgba(196,154,255,0.8);
    background: rgba(155,89,245,0.05);
    position: relative;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .s-chip::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(155,89,245,0.15), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .s-chip:hover { color: var(--pale); border-color: rgba(155,89,245,0.8); box-shadow: var(--glow-s); }
  .s-chip:hover::before { opacity: 1; }

  /* STATUS REIATSU */
  .reiatsu-status {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;
    margin-top: 22px;
  }

  .r-item {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 10px;
    letter-spacing: 2px;
    color: rgba(155,89,245,0.55);
  }

  .r-orb {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--spirit);
    box-shadow: var(--glow-s);
    animation: orbPulse 3s ease-in-out infinite;
    position: relative;
  }

  .r-orb::after {
    content: '';
    position: absolute;
    inset: -3px;
    border-radius: 50%;
    border: 1px solid rgba(155,89,245,0.3);
    animation: orbRing 3s ease-in-out infinite;
  }

  @keyframes orbPulse {
    0%,100% { transform: scale(1); opacity: 0.8; }
    50% { transform: scale(1.5); opacity: 1; }
  }
  @keyframes orbRing {
    0%,100% { transform: scale(1); opacity: 0.4; }
    50% { transform: scale(2.5); opacity: 0; }
  }

  .r-orb.pale { background: var(--pale); box-shadow: var(--glow-p); animation-delay: 1s; }
  .r-orb.deep { background: var(--blood); box-shadow: 0 0 8px var(--blood); animation-delay: 2s; }

  /* ══════════════════════════════════════
     KYOKA SUIGETSU PANEL
  ══════════════════════════════════════ */
  .suigetsu-panel {
    background: linear-gradient(135deg, rgba(26,6,58,0.95), rgba(7,3,15,0.98));
    border: 1px solid rgba(155,89,245,0.2);
    border-left: 2px solid var(--spirit);
    margin-bottom: 48px;
    overflow: hidden;
    position: relative;
    box-shadow: 0 0 40px rgba(155,89,245,0.08), inset 0 0 60px rgba(155,89,245,0.03);
  }

  /* Corner ornaments */
  .suigetsu-panel::before {
    content: '鏡花水月';
    position: absolute;
    top: 12px; right: 16px;
    font-family: 'Noto Serif JP', serif;
    font-size: 11px;
    letter-spacing: 4px;
    color: rgba(155,89,245,0.18);
    pointer-events: none;
  }

  .panel-bar {
    background: rgba(155,89,245,0.08);
    border-bottom: 1px solid rgba(155,89,245,0.15);
    padding: 11px 18px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .p-circle { width: 10px; height: 10px; border-radius: 50%; }
  .pc1 { background: #5b2d8a; }
  .pc2 { background: #7b3db8; }
  .pc3 { background: #9b59f5; box-shadow: 0 0 6px var(--spirit); }

  .panel-title {
    font-size: 10px;
    letter-spacing: 3px;
    color: rgba(155,89,245,0.45);
    margin-left: 6px;
    font-family: 'Cinzel', serif;
  }

  .panel-body {
    padding: 28px 28px 32px;
    font-size: 13px;
    line-height: 2.1;
  }

  .p-line { display: flex; align-items: flex-start; gap: 12px; }
  .p-prompt { color: rgba(155,89,245,0.6); flex-shrink: 0; }
  .p-cmd { color: var(--pale); }
  .p-out { color: rgba(155,89,245,0.65); padding-left: 22px; line-height: 1.9; }
  .p-k { color: var(--ghost); }
  .p-v { color: var(--pale); }
  .p-c { color: rgba(155,89,245,0.3); }
  .p-acc { color: var(--spirit); }
  .p-blank { height: 10px; }

  /* Animated typing line */
  #live-cmd { color: var(--pale); }
  #live-cmd::after { content: '█'; animation: blink 1s step-end infinite; color: var(--spirit); }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  /* ══════════════════════════════════════
     SPIRITUAL PRESSURE STATS
  ══════════════════════════════════════ */
  .section-title-wrap {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 24px;
  }

  .s-title {
    font-family: 'Cinzel', serif;
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 5px;
    color: rgba(155,89,245,0.7);
    text-shadow: var(--glow-s);
    flex-shrink: 0;
  }

  .s-rule {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, rgba(155,89,245,0.5), transparent);
  }

  .s-rule.r { background: linear-gradient(90deg, transparent, rgba(155,89,245,0.5)); }

  .spirit-kanji {
    font-family: 'Noto Serif JP', serif;
    font-size: 10px;
    color: rgba(155,89,245,0.25);
    flex-shrink: 0;
  }

  /* STAT CARDS */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
    gap: 14px;
    margin-bottom: 48px;
  }

  .stat-card {
    background: rgba(26,6,58,0.5);
    border: 1px solid rgba(155,89,245,0.12);
    padding: 22px 20px;
    position: relative;
    overflow: hidden;
    transition: all 0.35s cubic-bezier(0.16,1,0.3,1);
    cursor: pointer;
  }

  .stat-card::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    width: 100%; height: 2px;
    background: linear-gradient(90deg, var(--spirit), transparent);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.4s ease;
  }

  /* Floating kanji watermark */
  .stat-card::after {
    font-family: 'Noto Serif JP', serif;
    font-size: 48px;
    position: absolute;
    right: 12px; bottom: -4px;
    opacity: 0.04;
    transition: opacity 0.3s;
    color: var(--spirit);
    pointer-events: none;
  }

  .stat-card:nth-child(1)::after { content: '年'; }
  .stat-card:nth-child(2)::after { content: '成'; }
  .stat-card:nth-child(3)::after { content: '技'; }
  .stat-card:nth-child(4)::after { content: '魂'; }

  .stat-card:hover { border-color: rgba(155,89,245,0.35); background: rgba(155,89,245,0.06); transform: translateY(-3px); box-shadow: 0 8px 32px rgba(155,89,245,0.15); }
  .stat-card:hover::before { transform: scaleX(1); }
  .stat-card:hover::after { opacity: 0.09; }

  .stat-label {
    font-size: 9px;
    letter-spacing: 4px;
    color: rgba(155,89,245,0.4);
    margin-bottom: 10px;
    font-family: 'Cinzel', serif;
  }

  .stat-value {
    font-family: 'Cinzel', serif;
    font-size: 32px;
    font-weight: 900;
    color: var(--ghost);
    text-shadow: var(--glow-g);
    line-height: 1;
    margin-bottom: 8px;
  }

  .stat-sub {
    font-size: 10px;
    color: rgba(155,89,245,0.35);
    letter-spacing: 2px;
  }

  /* ══════════════════════════════════════
     SKILL MATRIX - Zanpakuto style
  ══════════════════════════════════════ */
  .skill-section { margin-bottom: 48px; }

  .skill-row {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 14px;
    position: relative;
  }

  .skill-name {
    font-family: 'Cinzel', serif;
    font-size: 10px;
    letter-spacing: 2px;
    width: 130px;
    flex-shrink: 0;
    color: rgba(196,154,255,0.7);
  }

  .skill-track {
    flex: 1;
    height: 3px;
    background: rgba(155,89,245,0.1);
    position: relative;
    overflow: visible;
  }

  /* Spiritual pressure fill */
  .skill-fill {
    height: 100%;
    background: linear-gradient(90deg, rgba(74,26,140,0.6), var(--spirit));
    position: relative;
    transition: width 1.8s cubic-bezier(0.16, 1, 0.3, 1);
    box-shadow: 0 0 8px rgba(155,89,245,0.4);
  }

  /* Glowing tip */
  .skill-fill::after {
    content: '';
    position: absolute;
    right: -1px; top: -4px;
    width: 11px; height: 11px;
    border-radius: 50%;
    background: var(--ghost);
    box-shadow: var(--glow-g);
    animation: tipFloat 2s ease-in-out infinite;
  }

  @keyframes tipFloat {
    0%,100% { transform: scale(1); opacity: 1; }
    50% { transform: scale(1.4); opacity: 0.7; }
  }

  .skill-pct {
    font-size: 10px;
    color: rgba(155,89,245,0.45);
    width: 36px;
    text-align: right;
    flex-shrink: 0;
    font-family: 'Cinzel', serif;
  }

  /* ══════════════════════════════════════
     TECH STACK - Spirit Orbs
  ══════════════════════════════════════ */
  .orb-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    gap: 12px;
    margin-bottom: 48px;
  }

  .orb-item {
    background: rgba(26,6,58,0.6);
    border: 1px solid rgba(155,89,245,0.1);
    padding: 16px 10px;
    text-align: center;
    font-size: 10px;
    letter-spacing: 2px;
    color: rgba(155,89,245,0.55);
    font-family: 'Cinzel', serif;
    transition: all 0.25s ease;
    cursor: default;
    position: relative;
    overflow: hidden;
  }

  .orb-item::before {
    content: '';
    position: absolute;
    top: 50%; left: 50%;
    width: 0; height: 0;
    background: radial-gradient(circle, rgba(155,89,245,0.2), transparent 70%);
    transform: translate(-50%,-50%);
    transition: width 0.4s, height 0.4s;
    border-radius: 50%;
  }

  .orb-item:hover { border-color: rgba(155,89,245,0.5); color: var(--pale); transform: scale(1.05); box-shadow: var(--glow-s); }
  .orb-item:hover::before { width: 150px; height: 150px; }

  .orb-icon { font-size: 20px; display: block; margin-bottom: 8px; }

  /* ══════════════════════════════════════
     ZANPAKUTO QUOTE
  ══════════════════════════════════════ */
  .bankai-quote {
    position: relative;
    margin-bottom: 48px;
    padding: 28px 32px;
    background: rgba(26,6,58,0.4);
    border-left: 2px solid var(--spirit);
    box-shadow: var(--glow-s);
    overflow: hidden;
  }

  /* Mirror water effect */
  .bankai-quote::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(180deg, rgba(155,89,245,0.04) 0%, transparent 60%);
    pointer-events: none;
  }

  /* Vertical JP text on right */
  .bankai-quote::after {
    content: '万象一切';
    position: absolute;
    right: 16px; top: 50%;
    transform: translateY(-50%);
    font-family: 'Noto Serif JP', serif;
    font-size: 10px;
    writing-mode: vertical-rl;
    letter-spacing: 6px;
    color: rgba(155,89,245,0.12);
    pointer-events: none;
  }

  .quote-jp {
    font-family: 'Noto Serif JP', serif;
    font-size: 11px;
    letter-spacing: 4px;
    color: rgba(155,89,245,0.35);
    margin-bottom: 12px;
  }

  .quote-text {
    font-family: 'Cinzel', serif;
    font-size: 17px;
    font-weight: 400;
    color: var(--ghost);
    line-height: 1.7;
    text-shadow: var(--glow-g);
    margin-bottom: 14px;
  }

  .quote-attr {
    font-size: 10px;
    letter-spacing: 3px;
    color: rgba(155,89,245,0.3);
    font-family: 'Cinzel', serif;
  }

  /* ══════════════════════════════════════
     CONNECTION RITUAL
  ══════════════════════════════════════ */
  .connect-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-bottom: 48px;
  }

  .connect-item {
    display: flex;
    align-items: center;
    gap: 16px;
    background: rgba(26,6,58,0.5);
    border: 1px solid rgba(155,89,245,0.1);
    padding: 18px 20px;
    text-decoration: none;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
  }

  .connect-item::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(155,89,245,0.08), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .connect-item::after {
    content: '→';
    position: absolute;
    right: 18px;
    color: rgba(155,89,245,0.25);
    transition: all 0.3s;
    font-size: 16px;
    font-family: 'Share Tech Mono', monospace;
  }

  .connect-item:hover { border-color: rgba(155,89,245,0.4); box-shadow: 0 4px 24px rgba(155,89,245,0.12); }
  .connect-item:hover::before { opacity: 1; }
  .connect-item:hover::after { right: 14px; color: var(--spirit); text-shadow: var(--glow-s); }

  .c-icon { font-size: 20px; flex-shrink: 0; }
  .c-label { font-size: 8px; letter-spacing: 4px; color: rgba(155,89,245,0.35); display: block; margin-bottom: 3px; font-family: 'Cinzel', serif; }
  .c-val { font-size: 12px; color: rgba(196,154,255,0.8); }

  /* ══════════════════════════════════════
     FOOTER
  ══════════════════════════════════════ */
  .footer-seal {
    text-align: center;
    padding-top: 40px;
    border-top: 1px solid rgba(155,89,245,0.1);
  }

  .seal-text {
    font-family: 'Noto Serif JP', serif;
    font-size: 20px;
    letter-spacing: 8px;
    color: rgba(155,89,245,0.15);
    margin-bottom: 10px;
    animation: sealPulse 5s ease-in-out infinite;
  }

  @keyframes sealPulse {
    0%,100% { opacity: 0.15; }
    50% { opacity: 0.3; }
  }

  .footer-text {
    font-size: 9px;
    letter-spacing: 4px;
    color: rgba(155,89,245,0.25);
    font-family: 'Cinzel', serif;
  }

  /* ══════════════════════════════════════
     GHOST SHATTER PARTICLES (JS-driven)
  ══════════════════════════════════════ */
  .shard {
    position: fixed;
    pointer-events: none;
    z-index: 500;
    border: 1px solid rgba(155,89,245,0.6);
    background: rgba(155,89,245,0.15);
    animation: shardFall linear forwards;
  }

  @keyframes shardFall {
    0%   { opacity: 1; transform: rotate(0deg) scale(1); }
    100% { opacity: 0; transform: rotate(var(--r)) scale(0.2) translate(var(--tx), var(--ty)); }
  }

  @media (max-width: 600px) {
    .connect-grid { grid-template-columns: 1fr; }
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .hero-name { font-size: 32px; letter-spacing: 4px; }
  }
</style>
</head>
<body>

<!-- REIATSU PARTICLE FIELD -->
<canvas id="reiatsu-canvas"></canvas>
<!-- KIDO LIGHT STREAMS -->
<canvas id="kido-canvas"></canvas>

<div class="wrapper">

  <!-- ══════════════════════════════════════
       HERO
  ══════════════════════════════════════ -->
  <div class="hero">
    <div class="kanji-strip" aria-hidden="true">霊圧技術創造</div>

    <div class="eyecatch">  SPIRITUAL PRESSURE :: MANIFEST</div>

    <div class="hero-name" id="hero-name">DINESHKUMAR.S</div>

    <div class="hero-zanpakuto">
      <div class="zanp-line"></div>
      <span>鏡花水月 — Kyoka Suigetsu</span>
      <div class="zanp-line r"></div>
    </div>

    <div class="spirit-chips">
      <div class="s-chip">FULL-STACK DEVELOPER</div>
      <div class="s-chip">CLOUD ARCHITECT</div>
      <div class="s-chip">DATA ANALYST</div>
      <div class="s-chip">OPEN SOURCE</div>
    </div>

    <div class="reiatsu-status">
      <div class="r-item"><div class="r-orb"></div>REIATSU: ACTIVE</div>
      <div class="r-item"><div class="r-orb pale"></div>CARDIFF, WALES</div>
      <div class="r-item"><div class="r-orb deep"></div>COFFEE: DEPLETED</div>
      <div class="r-item"><div class="r-orb"></div>BUILD: RUNNING</div>
    </div>
  </div>

  <!-- ══════════════════════════════════════
       SUIGETSU PANEL (Terminal)
  ══════════════════════════════════════ -->
  <div class="suigetsu-panel">
    <div class="panel-bar">
      <div class="p-circle pc1"></div>
      <div class="p-circle pc2"></div>
      <div class="p-circle pc3"></div>
      <span class="panel-title">SOUL — dinesh@seireitei ~</span>
    </div>
    <div class="panel-body">
      <div class="p-line">
        <span class="p-prompt">dinesh@dev:~$</span>
        <span class="p-cmd">cat identity.soul</span>
      </div>
      <div class="p-blank"></div>
      <div class="p-out">
        {<br>
        &nbsp;&nbsp;<span class="p-k">"name"</span>&nbsp;:&nbsp;<span class="p-v">"Dineshkumar S"</span>,<br>
        &nbsp;&nbsp;<span class="p-k">"class"</span>&nbsp;:&nbsp;<span class="p-v">"Full-Stack Web &amp; App Developer"</span>,<br>
        &nbsp;&nbsp;<span class="p-k">"zanpakuto"</span>&nbsp;:&nbsp;<span class="p-v">"React · Node.js · Python · Flutter"</span>,<br>
        &nbsp;&nbsp;<span class="p-k">"shikai"</span>&nbsp;:&nbsp;[<span class="p-v">"GCP"</span>, <span class="p-v">"AWS"</span>, <span class="p-v">"Firebase"</span>],<br>
        &nbsp;&nbsp;<span class="p-k">"bankai"</span>&nbsp;:&nbsp;<span class="p-v">"Scalable · Impactful · Production"</span>,<br>
        &nbsp;&nbsp;<span class="p-k">"reiatsu"</span>&nbsp;:&nbsp;<span class="p-v">"Cardiff, Wales 🏴󠁧󠁢󠁷󠁬󠁳󠁿"</span>,<br>
        &nbsp;&nbsp;<span class="p-k">"mission"</span>&nbsp;:&nbsp;<span class="p-v">"Building what others only imagine"</span>,<br>
        &nbsp;&nbsp;<span class="p-k">"status"</span>&nbsp;:&nbsp;<span class="p-acc">"BANKAI_RELEASED"</span>&nbsp;<span class="p-c">// 万象一切</span><br>
        }
      </div>
      <div class="p-blank"></div>
      <div class="p-line">
        <span class="p-prompt">dinesh@dev:~$</span>
        <span id="live-cmd"></span>
      </div>
    </div>
  </div>

  <!-- ══════════════════════════════════════
       STATS
  ══════════════════════════════════════ -->
  <div class="section-title-wrap">
    <div class="s-rule r"></div>
    <span class="spirit-kanji">霊</span>
    <span class="s-title">SPIRITUAL PRESSURE</span>
    <span class="spirit-kanji">圧</span>
    <div class="s-rule"></div>
  </div>

  <div class="stats-grid">
    <div class="stat-card">
      <div class="stat-label">SHINIGAMI RANK</div>
      <div class="stat-value" data-target="4">0</div>
      <div class="stat-sub">YEARS IN BATTLE</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">MISSIONS COMPLETE</div>
      <div class="stat-value" data-target="40">0</div>
      <div class="stat-sub">PROJECTS SHIPPED</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">ABILITY COUNT</div>
      <div class="stat-value" data-target="20">0</div>
      <div class="stat-sub">TECHNOLOGIES MASTERED</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">SOUL FREQUENCY</div>
      <div class="stat-value">99%</div>
      <div class="stat-sub">COMMIT RESONANCE</div>
    </div>
  </div>

  <!-- ══════════════════════════════════════
       SKILL MATRIX
  ══════════════════════════════════════ -->
  <div class="skill-section">
    <div class="section-title-wrap">
      <div class="s-rule r"></div>
      <span class="spirit-kanji">技</span>
      <span class="s-title">ABILITY MATRIX</span>
      <span class="spirit-kanji">術</span>
      <div class="s-rule"></div>
    </div>

    <div class="skill-row">
      <span class="skill-name">React / JS</span>
      <div class="skill-track"><div class="skill-fill" style="width:0%" data-w="95%"></div></div>
      <span class="skill-pct">95%</span>
    </div>
    <div class="skill-row">
      <span class="skill-name">Node.js</span>
      <div class="skill-track"><div class="skill-fill" style="width:0%" data-w="90%"></div></div>
      <span class="skill-pct">90%</span>
    </div>
    <div class="skill-row">
      <span class="skill-name">Python</span>
      <div class="skill-track"><div class="skill-fill" style="width:0%" data-w="88%"></div></div>
      <span class="skill-pct">88%</span>
    </div>
    <div class="skill-row">
      <span class="skill-name">Cloud GCP / AWS</span>
      <div class="skill-track"><div class="skill-fill" style="width:0%" data-w="82%"></div></div>
      <span class="skill-pct">82%</span>
    </div>
    <div class="skill-row">
      <span class="skill-name">Flutter / Dart</span>
      <div class="skill-track"><div class="skill-fill" style="width:0%" data-w="78%"></div></div>
      <span class="skill-pct">90%</span>
    </div>
    <div class="skill-row">
      <span class="skill-name">SQL / NoSQL</span>
      <div class="skill-track"><div class="skill-fill" style="width:0%" data-w="85%"></div></div>
      <span class="skill-pct">85%</span>
    </div>
  </div>

  <!-- ══════════════════════════════════════
       TECH STACK ORBS
  ══════════════════════════════════════ -->
  <div class="section-title-wrap">
    <div class="s-rule r"></div>
    <span class="spirit-kanji">魂</span>
    <span class="s-title">SOUL ARSENAL</span>
    <span class="spirit-kanji">器</span>
    <div class="s-rule"></div>
  </div>

  <div class="orb-grid">
    <div class="orb-item"><span class="orb-icon">⚛️</span>React</div>
    <div class="orb-item"><span class="orb-icon">🟩</span>Node.js</div>
    <div class="orb-item"><span class="orb-icon">🐍</span>Python</div>
    <div class="orb-item"><span class="orb-icon">🎯</span>Flutter</div>
    <div class="orb-item"><span class="orb-icon">🗄️</span>MySQL</div>
    <div class="orb-item"><span class="orb-icon">🍃</span>MongoDB</div>
    <div class="orb-item"><span class="orb-icon">🔥</span>Firebase</div>
    <div class="orb-item"><span class="orb-icon">☁️</span>GCP</div>
    <div class="orb-item"><span class="orb-icon">🌩️</span>AWS</div>
    <div class="orb-item"><span class="orb-icon">🐳</span>Docker</div>
    <div class="orb-item"><span class="orb-icon">🔧</span>Express</div>
    <div class="orb-item"><span class="orb-icon">💅</span>Sass</div>
    <div class="orb-item"><span class="orb-icon">📮</span>Postman</div>
    <div class="orb-item"><span class="orb-icon">🔀</span>Git</div>
    <div class="orb-item"><span class="orb-icon">🎨</span>Bootstrap</div>
    <div class="orb-item"><span class="orb-icon">🚀</span>Vercel</div>
  </div>

  <!-- ══════════════════════════════════════
       BANKAI QUOTE
  ══════════════════════════════════════ -->
  <div class="bankai-quote">
    <div class="quote-jp">万象一切 — Bankai · Kyoka Suigetsu</div>
    <div class="quote-text">"The best code is written when you understand the problem deeply — not when you know the solution quickly."</div>
    <div class="quote-attr">  RUNTIME PHILOSOPHY :: SOUL INSCRIPTION</div>
  </div>

  <!-- ══════════════════════════════════════
       CONNECT
  ══════════════════════════════════════ -->
  <div class="section-title-wrap">
    <div class="s-rule r"></div>
    <span class="spirit-kanji">通</span>
    <span class="s-title">ESTABLISH CONTACT</span>
    <span class="spirit-kanji">信</span>
    <div class="s-rule"></div>
  </div>

  <div class="connect-grid">
    <a class="connect-item" href="mailto:dineshkumar04workspace@gmail.com">
      <span class="c-icon">📧</span>
      <div><span class="c-label">SOUL MAIL</span><span class="c-val">dineshkumar04workspace@gmail.com</span></div>
    </a>
    <a class="connect-item" href="https://www.linkedin.com/in/dinesh-kumar-429968200/">
      <span class="c-icon">💼</span>
      <div><span class="c-label">SHINIGAMI RECORDS</span><span class="c-val">linkedin / dinesh-kumar</span></div>
    </a>
    <a class="connect-item" href="https://dinesh-personal-portfolioed.netlify.app/">
      <span class="c-icon">🌐</span>
      <div><span class="c-label">SPIRIT REALM</span><span class="c-val">dinesh-personal-portfolioed.netlify.app</span></div>
    </a>
    <a class="connect-item" href="tel:9600052851">
      <span class="c-icon">📱</span>
      <div><span class="c-label">REIATSU SIGNAL</span><span class="c-val">+91 96000 52851</span></div>
    </a>
  </div>

  <!-- ══════════════════════════════════════
       FOOTER
  ══════════════════════════════════════ -->
  <div class="footer-seal">
    <div class="seal-text">一 護 心 力 創</div>
    <div class="footer-text">RESPONSE TIME &lt; 24H · OPEN TO COLLABS · SOUL ALWAYS ONLINE</div>
  </div>

</div>

<script>
/* ══════════════════════════════════════
   REIATSU PARTICLE FIELD
══════════════════════════════════════ */
const rc = document.getElementById('reiatsu-canvas');
const rctx = rc.getContext('2d');
rc.width = window.innerWidth;
rc.height = window.innerHeight;

const particles = [];
for (let i = 0; i < 80; i++) {
  particles.push({
    x: Math.random() * rc.width,
    y: Math.random() * rc.height,
    r: Math.random() * 1.5 + 0.3,
    vx: (Math.random() - 0.5) * 0.3,
    vy: -Math.random() * 0.6 - 0.1,
    alpha: Math.random() * 0.5 + 0.1,
    life: Math.random(),
  });
}

function drawParticles() {
  rctx.clearRect(0, 0, rc.width, rc.height);
  particles.forEach(p => {
    p.x += p.vx;
    p.y += p.vy;
    p.life -= 0.003;
    if (p.life <= 0 || p.y < -10) {
      p.x = Math.random() * rc.width;
      p.y = rc.height + 10;
      p.life = Math.random() * 0.8 + 0.2;
    }
    const a = p.alpha * p.life;
    rctx.beginPath();
    rctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
    rctx.fillStyle = `rgba(155,89,245,${a})`;
    rctx.shadowBlur = 6;
    rctx.shadowColor = '#9b59f5';
    rctx.fill();
    rctx.shadowBlur = 0;
  });
  requestAnimationFrame(drawParticles);
}
drawParticles();

/* ══════════════════════════════════════
   KIDO LIGHT STREAMS
══════════════════════════════════════ */
const kc = document.getElementById('kido-canvas');
const kctx = kc.getContext('2d');
kc.width = window.innerWidth;
kc.height = window.innerHeight;

const streams = [];
function spawnStream() {
  streams.push({
    x: Math.random() * kc.width,
    y: kc.height + 20,
    targetX: Math.random() * kc.width,
    targetY: -20,
    speed: Math.random() * 2 + 1,
    alpha: Math.random() * 0.3 + 0.05,
    width: Math.random() * 1.5 + 0.5,
    progress: 0,
    length: Math.random() * 0.3 + 0.05,
  });
}

for (let i = 0; i < 6; i++) spawnStream();
setInterval(spawnStream, 1200);

function drawStreams() {
  kctx.clearRect(0, 0, kc.width, kc.height);
  streams.forEach((s, i) => {
    s.progress += s.speed / kc.height;
    const tail = Math.max(0, s.progress - s.length);
    const headX = s.x + (s.targetX - s.x) * s.progress;
    const headY = s.y + (s.targetY - s.y) * s.progress;
    const tailX = s.x + (s.targetX - s.x) * tail;
    const tailY = s.y + (s.targetY - s.y) * tail;

    const grad = kctx.createLinearGradient(tailX, tailY, headX, headY);
    grad.addColorStop(0, `rgba(155,89,245,0)`);
    grad.addColorStop(0.5, `rgba(196,154,255,${s.alpha})`);
    grad.addColorStop(1, `rgba(232,216,255,${s.alpha * 1.5})`);

    kctx.beginPath();
    kctx.moveTo(tailX, tailY);
    kctx.lineTo(headX, headY);
    kctx.strokeStyle = grad;
    kctx.lineWidth = s.width;
    kctx.stroke();

    if (s.progress >= 1 + s.length) streams.splice(i, 1);
  });
  requestAnimationFrame(drawStreams);
}
drawStreams();

/* ══════════════════════════════════════
   RESIZE
══════════════════════════════════════ */
window.addEventListener('resize', () => {
  rc.width = kc.width = window.innerWidth;
  rc.height = kc.height = window.innerHeight;
});

/* ══════════════════════════════════════
   TYPING ANIMATION
══════════════════════════════════════ */
const cmds = [
  'git commit -m "bankai released 🔮"',
  'deploy --realm=production --reiatsu=max',
  'python soul_analytics.py --mode=bankai',
  'SELECT spirit FROM shinigami WHERE rank > 9000',
  'npm run build:zanpakuto && release',
];
let ci = 0, ch = 0, del = false;
const tel = document.getElementById('live-cmd');
function type() {
  const cur = cmds[ci];
  if (!del) {
    tel.textContent = cur.slice(0, ++ch);
    if (ch === cur.length) { del = true; setTimeout(type, 2200); return; }
  } else {
    tel.textContent = cur.slice(0, --ch);
    if (ch === 0) { del = false; ci = (ci + 1) % cmds.length; }
  }
  setTimeout(type, del ? 38 : 75);
}
type();

/* ══════════════════════════════════════
   COUNTER ANIMATION
══════════════════════════════════════ */
function animCount(el, target, dur = 1800) {
  let start = null;
  (function step(ts) {
    if (!start) start = ts;
    const p = Math.min((ts - start) / dur, 1);
    const ease = 1 - Math.pow(1 - p, 4);
    el.textContent = Math.floor(ease * target) + '+';
    if (p < 1) requestAnimationFrame(step);
    else el.textContent = target + '+';
  })(performance.now());
}

new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      const t = parseInt(e.target.dataset.target);
      if (t) animCount(e.target, t);
    }
  });
}, { threshold: 0.5 }).observe(document.querySelector('.stats-grid'));

/* ══════════════════════════════════════
   SKILL BARS
══════════════════════════════════════ */
new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      document.querySelectorAll('.skill-fill').forEach(b => b.style.width = b.dataset.w);
    }
  });
}, { threshold: 0.3 }).observe(document.querySelector('.skill-section'));

/* ══════════════════════════════════════
   KYOKA SUIGETSU SHATTER — click shards
══════════════════════════════════════ */
document.getElementById('hero-name').addEventListener('click', function(e) {
  for (let i = 0; i < 18; i++) {
    const s = document.createElement('div');
    s.className = 'shard';
    const size = Math.random() * 12 + 4;
    const angle = Math.random() * 360;
    const dist = Math.random() * 180 + 60;
    const tx = Math.cos(angle * Math.PI / 180) * dist + 'px';
    const ty = Math.sin(angle * Math.PI / 180) * dist + 'px';
    const rot = (Math.random() - 0.5) * 540 + 'deg';
    s.style.cssText = `
      left:${e.clientX + (Math.random()-0.5)*30}px;
      top:${e.clientY + (Math.random()-0.5)*10}px;
      width:${size}px;
      height:${size * (Math.random()*1.5+0.5)}px;
      --tx:${tx}; --ty:${ty}; --r:${rot};
      animation-duration:${Math.random()*0.8+0.6}s;
      opacity:0.85;
      clip-path: polygon(${Math.random()*30}% 0%, 100% ${Math.random()*30}%, ${70+Math.random()*30}% 100%, 0% ${70+Math.random()*30}%);
    `;
    document.body.appendChild(s);
    setTimeout(() => s.remove(), 1400);
  }
});
</script>
</body>
</html>
