# ADMFX<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>ADMFX | Professional Forex Account Management</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&family=DM+Mono:wght@300;400&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --gold: #D4A843; --gold2: #F0C96A; --green: #00E676; --red: #FF3D57;
      --dark: #050508; --dark2: #0C0C12; --dark3: #121219; --dark4: #1A1A24;
      --panel: rgba(20,20,30,0.85); --text: #EAE6DC; --muted: #5A5670;
      --border: rgba(212,168,67,0.18); --border2: rgba(255,255,255,0.05);
    }
    html { scroll-behavior: smooth; }
    body { font-family: 'DM Mono', monospace; background: var(--dark); color: var(--text); overflow-x: hidden; cursor: crosshair; }

    /* WHATSAPP FLOAT */
    .wa-float {
      position: fixed; bottom: 2rem; right: 2rem; z-index: 999;
      display: flex; align-items: center; gap: 0.8rem;
      background: #25D366; color: #fff; padding: 0.8rem 1.4rem 0.8rem 1rem;
      border-radius: 50px; text-decoration: none;
      font-family: 'DM Mono', monospace; font-size: 0.72rem; letter-spacing: 1px;
      box-shadow: 0 4px 24px rgba(37,211,102,0.45);
      animation: waPulse 2.5s ease-in-out infinite; transition: transform 0.2s;
    }
    .wa-float:hover { transform: scale(1.05); }
    .wa-float svg { width: 22px; height: 22px; flex-shrink: 0; }
    @keyframes waPulse { 0%,100%{box-shadow:0 4px 24px rgba(37,211,102,0.4)} 50%{box-shadow:0 4px 40px rgba(37,211,102,0.75)} }

    /* TICKER */
    .ticker-wrap { position: fixed; top: 0; left: 0; right: 0; z-index: 200; background: var(--dark2); border-bottom: 1px solid var(--border); overflow: hidden; height: 32px; display: flex; align-items: center; }
    .ticker-track { display: flex; animation: ticker 30s linear infinite; white-space: nowrap; }
    .tick-item { display: inline-flex; align-items: center; gap: 0.5rem; padding: 0 2rem; font-size: 0.65rem; letter-spacing: 1.5px; border-right: 1px solid var(--border2); }
    .tick-pair { color: var(--muted); } .tick-price { color: var(--text); }
    .tick-chg.up { color: var(--green); } .tick-chg.dn { color: var(--red); }
    @keyframes ticker { 0%{transform:translateX(0)} 100%{transform:translateX(-50%)} }

    /* NAV */
    nav { position: fixed; top: 32px; left: 0; right: 0; z-index: 100; padding: 1rem 2.5rem; display: flex; justify-content: space-between; align-items: center; background: rgba(5,5,8,0.92); backdrop-filter: blur(16px); border-bottom: 1px solid var(--border); }
    .nav-logo { font-family: 'Bebas Neue', sans-serif; font-size: 2rem; letter-spacing: 4px; color: var(--gold); text-shadow: 0 0 30px rgba(212,168,67,0.4); }
    .nav-logo span { color: var(--text); }
    .nav-links { display: flex; gap: 2.5rem; list-style: none; }
    .nav-links a { text-decoration: none; color: var(--muted); font-size: 0.65rem; letter-spacing: 2px; text-transform: uppercase; transition: color 0.3s; }
    .nav-links a:hover { color: var(--gold); }
    .nav-cta { background: var(--gold); color: var(--dark); padding: 0.5rem 1.5rem; font-family: 'DM Mono', monospace; font-size: 0.65rem; letter-spacing: 2px; text-transform: uppercase; border: none; cursor: crosshair; text-decoration: none; transition: background 0.3s; }
    .nav-cta:hover { background: var(--gold2); }

    /* HERO */
    .hero { min-height: 100vh; padding: 10rem 2.5rem 4rem; position: relative; overflow: hidden; display: grid; grid-template-columns: 1fr 420px; gap: 4rem; align-items: center; }
    .chart-bg { position: absolute; inset: 0; opacity: 0.06; background-image: linear-gradient(180deg,transparent 49%,rgba(212,168,67,0.5) 50%,transparent 51%),linear-gradient(90deg,transparent 24px,rgba(212,168,67,0.3) 25px,transparent 26px); background-size: 80px 40px,25px 100%; }
    .candlestick-bg { position: absolute; inset: 0; opacity: 0.04; background: repeating-linear-gradient(90deg,transparent,transparent 30px,rgba(212,168,67,0.8) 30px,rgba(212,168,67,0.8) 32px); }
    .hero-left { position: relative; }
    .hero-eyebrow { display: flex; align-items: center; gap: 1rem; margin-bottom: 1.5rem; animation: fadeUp 0.7s ease both; }
    .eyebrow-dot { width: 6px; height: 6px; background: var(--green); border-radius: 50%; animation: pulse 2s infinite; }
    .eyebrow-text { font-size: 0.65rem; letter-spacing: 3px; text-transform: uppercase; color: var(--green); }
    @keyframes pulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:0.4;transform:scale(0.8)} }
    .hero h1 { font-family: 'Bebas Neue', sans-serif; font-size: clamp(4rem,9vw,8rem); line-height: 0.9; letter-spacing: 2px; margin-bottom: 1.5rem; animation: fadeUp 0.7s 0.1s ease both; }
    .hero h1 .line1 { display: block; color: var(--text); }
    .hero h1 .line2 { display: block; color: var(--gold); }
    .hero h1 .line3 { display: block; color: transparent; -webkit-text-stroke: 1px rgba(212,168,67,0.4); }
    .hero-sub { font-family: 'Cormorant Garamond', serif; font-size: 1.05rem; line-height: 2; color: var(--muted); max-width: 480px; margin-bottom: 2.5rem; animation: fadeUp 0.7s 0.2s ease both; }
    .hero-actions { display: flex; gap: 1rem; animation: fadeUp 0.7s 0.3s ease both; }
    .btn-gold { background: var(--gold); color: var(--dark); padding: 0.8rem 2rem; border: none; cursor: crosshair; font-family: 'DM Mono', monospace; font-size: 0.65rem; letter-spacing: 2px; text-transform: uppercase; text-decoration: none; transition: background 0.3s, transform 0.2s; }
    .btn-gold:hover { background: var(--gold2); transform: translateY(-2px); }
    .btn-ghost { background: transparent; color: var(--text); padding: 0.8rem 2rem; border: 1px solid var(--border); cursor: crosshair; font-family: 'DM Mono', monospace; font-size: 0.65rem; letter-spacing: 2px; text-transform: uppercase; text-decoration: none; transition: border-color 0.3s, color 0.3s; }
    .btn-ghost:hover { border-color: var(--gold); color: var(--gold); }

    /* LIVE PANEL */
    .hero-panel { background: var(--panel); border: 1px solid var(--border); padding: 1.5rem; animation: fadeIn 1s 0.4s ease both; position: relative; }
    .hero-panel::before { content: 'LIVE ACCOUNT MONITOR'; position: absolute; top: -1px; left: 1.5rem; font-size: 0.55rem; letter-spacing: 2px; background: var(--gold); color: var(--dark); padding: 0.25rem 0.6rem; }
    .panel-header { display: flex; justify-content: space-between; align-items: center; margin: 0.5rem 0 1.5rem; padding-bottom: 1rem; border-bottom: 1px solid var(--border2); }
    .panel-title { font-size: 0.65rem; letter-spacing: 2px; color: var(--muted); text-transform: uppercase; }
    .panel-live { display: flex; align-items: center; gap: 0.4rem; font-size: 0.6rem; color: var(--green); }
    .panel-live-dot { width: 5px; height: 5px; background: var(--green); border-radius: 50%; animation: pulse 1.5s infinite; }
    .equity-display { text-align: center; padding: 1.5rem 0; margin-bottom: 1.5rem; border: 1px solid var(--border2); background: rgba(0,0,0,0.3); position: relative; overflow: hidden; }
    .equity-label { font-size: 0.58rem; letter-spacing: 2px; color: var(--muted); margin-bottom: 0.5rem; }
    .equity-num { font-family: 'Bebas Neue', sans-serif; font-size: 2.8rem; color: var(--gold); letter-spacing: 2px; }
    .equity-change { font-size: 0.65rem; color: var(--green); margin-top: 0.3rem; }
    .equity-bar { position: absolute; bottom: 0; left: 0; height: 2px; background: var(--green); animation: barGrow 2s ease forwards; }
    .metrics-row { display: grid; grid-template-columns: 1fr 1fr; gap: 0.75rem; margin-bottom: 1rem; }
    .metric { background: rgba(0,0,0,0.3); padding: 0.8rem; border: 1px solid var(--border2); }
    .metric-label { font-size: 0.55rem; letter-spacing: 1.5px; color: var(--muted); text-transform: uppercase; margin-bottom: 0.3rem; }
    .metric-val { font-family: 'Bebas Neue', sans-serif; font-size: 1.4rem; letter-spacing: 1px; }
    .metric-val.up { color: var(--green); } .metric-val.gold { color: var(--gold); } .metric-val.dn { color: var(--red); }
    .mini-chart { margin-top: 1rem; }
    .mini-chart-label { font-size: 0.55rem; letter-spacing: 1.5px; color: var(--muted); margin-bottom: 0.5rem; }
    .mini-chart svg { width: 100%; height: 60px; }
    .pairs-list { margin-top: 1rem; }
    .pair-row { display: flex; justify-content: space-between; align-items: center; padding: 0.55rem 0; border-bottom: 1px solid var(--border2); font-size: 0.65rem; }
    .pair-name { color: var(--muted); letter-spacing: 1px; } .pair-price { color: var(--text); }
    .pair-dir { font-size: 0.6rem; padding: 0.15rem 0.4rem; }
    .pair-dir.up { color: var(--green); background: rgba(0,230,118,0.08); }
    .pair-dir.dn { color: var(--red); background: rgba(255,61,87,0.08); }

    /* STATS BAR */
    .stats-bar { background: var(--dark2); border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); padding: 2rem 2.5rem; display: grid; grid-template-columns: repeat(5,1fr); }
    .stat-item { text-align: center; padding: 0 2rem; border-right: 1px solid var(--border2); }
    .stat-item:last-child { border-right: none; }
    .stat-num { font-family: 'Bebas Neue', sans-serif; font-size: 2.5rem; color: var(--gold); letter-spacing: 2px; line-height: 1; }
    .stat-lbl { font-size: 0.58rem; letter-spacing: 2px; color: var(--muted); text-transform: uppercase; margin-top: 0.3rem; }

    /* SHARED */
    .section-tag { font-size: 0.6rem; letter-spacing: 3px; text-transform: uppercase; color: var(--gold); margin-bottom: 0.8rem; }
    .section-title { font-family: 'Cormorant Garamond', serif; font-size: clamp(2rem,4vw,3rem); font-weight: 600; line-height: 1.2; margin-bottom: 1rem; }
    .gold-line { width: 50px; height: 2px; background: var(--gold); margin-bottom: 2rem; }

    /* ABOUT */
    #about { background: var(--dark2); padding: 7rem 2.5rem; }
    .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 6rem; align-items: center; max-width: 1100px; margin: 0 auto; }
    .about-body p { font-family: 'Cormorant Garamond', serif; font-size: 1.05rem; line-height: 1.9; color: var(--muted); margin-bottom: 1rem; }
    .about-terminal { background: var(--dark3); border: 1px solid var(--border); padding: 1.5rem; font-size: 0.7rem; line-height: 2; position: relative; }
    .terminal-bar { position: absolute; top: 0; left: 0; right: 0; background: var(--dark4); padding: 0.4rem 1rem; display: flex; align-items: center; gap: 0.4rem; border-bottom: 1px solid var(--border2); }
    .t-dot { width: 8px; height: 8px; border-radius: 50%; }
    .t-dot.r{background:#FF5F57} .t-dot.y{background:#FEBC2E} .t-dot.g{background:#28C840}
    .t-title { font-size: 0.55rem; color: var(--muted); letter-spacing: 2px; margin-left: 0.5rem; }
    .terminal-body { margin-top: 1.8rem; }
    .t-line { display: flex; gap: 0.8rem; margin-bottom: 0.2rem; }
    .t-prompt{color:var(--gold)} .t-cmd{color:var(--text)} .t-out{color:var(--green)} .t-out2{color:var(--muted)}

    /* SKILLS */
    #skills { background: var(--dark); padding: 7rem 2.5rem; }
    .skills-wrap { max-width: 1100px; margin: 0 auto; }
    .skills-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 1px; background: var(--border2); margin-top: 3rem; }
    .skill-box { background: var(--dark2); padding: 2rem; transition: background 0.3s; position: relative; overflow: hidden; }
    .skill-box:hover { background: var(--dark3); }
    .skill-box::after { content:''; position: absolute; bottom:0; left:0; right:0; height:1px; background:var(--gold); transform:scaleX(0); transition:transform 0.4s; }
    .skill-box:hover::after { transform: scaleX(1); }
    .skill-num { font-family: 'Bebas Neue', sans-serif; font-size: 3rem; color: var(--border); line-height: 1; margin-bottom: 0.5rem; letter-spacing: 2px; }
    .skill-title { font-size: 0.75rem; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); margin-bottom: 0.8rem; }
    .skill-text { font-family: 'Cormorant Garamond', serif; font-size: 0.95rem; color: var(--muted); line-height: 1.8; }
    .skill-meter { margin-top: 1.2rem; }
    .skill-meter-track { height: 1px; background: var(--border2); position: relative; }
    .skill-meter-fill { position: absolute; top: 0; left: 0; height: 100%; background: var(--gold); }
    .skill-pct { font-size: 0.6rem; color: var(--gold); margin-top: 0.3rem; letter-spacing: 1px; }

    /* ACCOUNT */
    #account { background: var(--dark2); padding: 7rem 2.5rem; }
    .acct-wrap { max-width: 1100px; margin: 0 auto; }
    .acct-intro { font-family: 'Cormorant Garamond', serif; font-size: 1.05rem; color: var(--muted); line-height: 1.9; max-width: 600px; margin-bottom: 3rem; }
    .how-steps { display: grid; grid-template-columns: repeat(4,1fr); border: 1px solid var(--border); margin-bottom: 4rem; }
    .how-step { padding: 2rem 1.5rem; border-right: 1px solid var(--border); position: relative; }
    .how-step:last-child { border-right: none; }
    .how-step::before { content: attr(data-num); font-family: 'Bebas Neue', sans-serif; font-size: 4rem; color: var(--border); position: absolute; top: 0.5rem; right: 1rem; line-height: 1; }
    .step-icon { font-size: 1.5rem; margin-bottom: 0.8rem; }
    .step-title { font-size: 0.7rem; letter-spacing: 2px; text-transform: uppercase; color: var(--gold); margin-bottom: 0.5rem; }
    .step-text { font-family: 'Cormorant Garamond', serif; font-size: 0.9rem; color: var(--muted); line-height: 1.7; }
    .plans-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 1.5rem; }
    .plan { border: 1px solid var(--border); padding: 2.5rem 2rem; background: var(--dark3); position: relative; transition: transform 0.3s; }
    .plan:hover { transform: translateY(-4px); }
    .plan.featured { border-color: var(--gold); background: var(--dark4); }
    .plan-star { position: absolute; top: -1px; right: 1.5rem; background: var(--gold); color: var(--dark); font-size: 0.55rem; letter-spacing: 2px; text-transform: uppercase; padding: 0.25rem 0.8rem; }
    .plan-tier { font-size: 0.6rem; letter-spacing: 2px; color: var(--muted); text-transform: uppercase; margin-bottom: 0.5rem; }
    .plan-name { font-family: 'Bebas Neue', sans-serif; font-size: 2rem; letter-spacing: 2px; color: var(--text); margin-bottom: 0.3rem; }
    .plan-min { color: var(--gold); font-size: 0.75rem; margin-bottom: 1.5rem; }
    .plan-split { font-family: 'Bebas Neue', sans-serif; font-size: 1.5rem; color: var(--gold); letter-spacing: 2px; margin-bottom: 0.3rem; }
    .plan-split-lbl { font-size: 0.58rem; color: var(--muted); letter-spacing: 1px; margin-bottom: 1.5rem; }
    .plan-feats { list-style: none; border-top: 1px solid var(--border2); padding-top: 1.2rem; }
    .plan-feats li { font-size: 0.72rem; color: var(--muted); padding: 0.45rem 0; border-bottom: 1px solid rgba(255,255,255,0.03); display: flex; gap: 0.6rem; align-items: flex-start; }
    .plan-feats li::before { content:'›'; color:var(--gold); flex-shrink:0; }

    /* PROJECTS */
    #projects { background: var(--dark); padding: 7rem 2.5rem; }
    .proj-wrap { max-width: 1100px; margin: 0 auto; }
    .trades-table { width: 100%; border-collapse: collapse; margin-bottom: 3rem; font-size: 0.68rem; }
    .trades-table th { text-align: left; padding: 0.8rem 1rem; border-bottom: 1px solid var(--border); color: var(--muted); letter-spacing: 2px; font-weight: 400; }
    .trades-table td { padding: 0.9rem 1rem; border-bottom: 1px solid var(--border2); }
    .trades-table tr:hover td { background: var(--dark2); }
    .td-pair{color:var(--text);letter-spacing:1px} .td-dir{padding:0.2rem 0.5rem;font-size:0.6rem}
    .td-dir.buy{background:rgba(0,230,118,0.1);color:var(--green)} .td-dir.sell{background:rgba(255,61,87,0.1);color:var(--red)}
    .td-profit.pos{color:var(--green)} .td-profit.neg{color:var(--red)} .td-rr{color:var(--gold)}
    .results-cards { display: grid; grid-template-columns: repeat(2,1fr); gap: 1.5rem; }
    .result-card { border: 1px solid var(--border); padding: 2rem; background: var(--dark2); position: relative; overflow: hidden; transition: border-color 0.3s; }
    .result-card:hover { border-color: rgba(212,168,67,0.4); }
    .result-pair-tag { font-size: 0.58rem; letter-spacing: 2px; color: var(--gold); text-transform: uppercase; margin-bottom: 0.6rem; }
    .result-title { font-family: 'Cormorant Garamond', serif; font-size: 1.4rem; margin-bottom: 0.5rem; }
    .result-desc { font-family: 'Cormorant Garamond', serif; font-size: 0.9rem; color: var(--muted); line-height: 1.8; margin-bottom: 1.5rem; }
    .result-nums { display: flex; gap: 2rem; }
    .rn-num { font-family: 'Bebas Neue', sans-serif; font-size: 1.8rem; color: var(--gold); letter-spacing: 1px; }
    .rn-lbl { font-size: 0.55rem; color: var(--muted); letter-spacing: 1.5px; text-transform: uppercase; }
    .result-stripe { position: absolute; bottom: 0; left: 0; right: 0; height: 2px; background: linear-gradient(90deg,var(--gold),transparent); }

    /* CONTACT */
    #contact { background: var(--dark2); padding: 7rem 2.5rem; }
    .contact-wrap { max-width: 900px; margin: 0 auto; }
    .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; }
    .ci-label { font-size: 0.58rem; letter-spacing: 2px; color: var(--muted); text-transform: uppercase; margin-bottom: 0.4rem; }
    .ci-val { font-family: 'Cormorant Garamond', serif; font-size: 1.1rem; color: var(--text); margin-bottom: 1.5rem; }
    .contact-channels { display: flex; flex-direction: column; gap: 0.8rem; margin-top: 1rem; }
    .channel { display: flex; align-items: center; gap: 1rem; padding: 0.8rem 1rem; border: 1px solid var(--border); text-decoration: none; color: var(--text); font-size: 0.7rem; letter-spacing: 1px; transition: border-color 0.3s, background 0.3s; }
    .channel:hover { border-color: var(--gold); background: rgba(212,168,67,0.05); }
    .channel-icon { font-size: 1.2rem; }
    .channel-name { color: var(--muted); font-size: 0.6rem; letter-spacing: 2px; text-transform: uppercase; }
    .form-group { margin-bottom: 1rem; }
    .form-group label { display: block; font-size: 0.58rem; letter-spacing: 2px; text-transform: uppercase; color: var(--muted); margin-bottom: 0.4rem; }
    .form-group input, .form-group textarea, .form-group select { width: 100%; background: var(--dark3); border: 1px solid var(--border2); color: var(--text); padding: 0.75rem 1rem; font-family: 'DM Mono', monospace; font-size: 0.72rem; outline: none; transition: border-color 0.3s; appearance: none; }
    .form-group input:focus, .form-group textarea:focus, .form-group select:focus { border-color: var(--gold); }
    .form-group textarea { resize: vertical; min-height: 100px; }
    .form-row2 { display: grid; grid-template-columns: 1fr 1fr; gap: 0.75rem; }

    /* FOOTER */
    footer { background: var(--dark); padding: 3rem 2.5rem; border-top: 1px solid var(--border); }
    .footer-inner { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 2rem; }
    .footer-logo { font-family: 'Bebas Neue', sans-serif; font-size: 2rem; letter-spacing: 4px; color: var(--gold); }
    .footer-tagline { font-size: 0.6rem; color: var(--muted); letter-spacing: 2px; margin-top: 0.2rem; }
    .footer-links { display: flex; gap: 2rem; }
    .footer-links a { font-size: 0.6rem; letter-spacing: 1.5px; color: var(--muted); text-decoration: none; text-transform: uppercase; transition: color 0.3s; }
    .footer-links a:hover { color: var(--gold); }
    .footer-disc { font-size: 0.58rem; color: rgba(90,86,112,0.5); max-width: 400px; line-height: 1.6; }

    /* ANIMATIONS */
    @keyframes fadeUp { from{opacity:0;transform:translateY(20px)} to{opacity:1;transform:none} }
    @keyframes fadeIn { from{opacity:0} to{opacity:1} }
    @keyframes barGrow { from{width:0} to{width:87%} }
    .reveal { opacity: 0; transform: translateY(24px); transition: opacity 0.7s, transform 0.7s; }
    .reveal.visible { opacity: 1; transform: none; }

    /* RESPONSIVE */
    @media (max-width: 960px) {
      .hero { grid-template-columns: 1fr; } .hero-panel { display: none; }
      .stats-bar { grid-template-columns: repeat(3,1fr); }
      .about-grid, .contact-grid { grid-template-columns: 1fr; gap: 3rem; }
      .skills-grid { grid-template-columns: 1fr 1fr; }
      .how-steps { grid-template-columns: 1fr 1fr; }
      .plans-grid, .results-cards { grid-template-columns: 1fr; }
      nav { padding: 0.8rem 1.5rem; } .nav-links { display: none; }
      #about, #skills, #account, #projects, #contact { padding: 5rem 1.5rem; }
      .hero { padding: 8rem 1.5rem 4rem; }
    }
    @media (max-width: 600px) {
      .skills-grid, .how-steps { grid-template-columns: 1fr; }
      .form-row2 { grid-template-columns: 1fr; }
      .stats-bar { grid-template-columns: repeat(2,1fr); }
      .wa-float span { display: none; }
    }
  </style>
</head>
<body>

<!-- FLOATING WHATSAPP -->
<a href="https://wa.me/2349164564955" target="_blank" class="wa-float">
  <svg viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.096.544 4.066 1.497 5.783L0 24l6.395-1.677A11.952 11.952 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.818a9.818 9.818 0 01-5.007-1.367l-.36-.213-3.717.975.992-3.625-.234-.373A9.818 9.818 0 1112 21.818z"/></svg>
  <span>Chat on WhatsApp</span>
</a>

<!-- TICKER -->
<div class="ticker-wrap"><div class="ticker-track" id="ticker"></div></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">ADM<span>FX</span></div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Expertise</a></li>
    <li><a href="#account">Management</a></li>
    <li><a href="#projects">Results</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="https://wa.me/2349164564955" target="_blank" class="nav-cta">Start Investing</a>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="chart-bg"></div>
  <div class="candlestick-bg"></div>
  <div class="hero-left">
    <div class="hero-eyebrow">
      <div class="eyebrow-dot"></div>
      <div class="eyebrow-text">Markets Open · Live Trading Active</div>
    </div>
    <h1>
      <span class="line1">PROFESSIONAL</span>
      <span class="line2">FOREX</span>
      <span class="line3">MANAGEMENT</span>
    </h1>
    <p class="hero-sub">ADMFX delivers institutional-grade forex account management. Disciplined strategy, proven returns, and full transparency — your capital, expertly managed.</p>
    <div class="hero-actions">
      <a href="https://wa.me/2349164564955" target="_blank" class="btn-gold">Manage My Account</a>
      <a href="#projects" class="btn-ghost">View Track Record</a>
    </div>
  </div>
  <div class="hero-panel">
    <div class="panel-header">
      <div class="panel-title">ADMFX Portfolio</div>
      <div class="panel-live"><div class="panel-live-dot"></div>LIVE</div>
    </div>
    <div class="equity-display">
      <div class="equity-label">TOTAL EQUITY</div>
      <div class="equity-num">$124,850.40</div>
      <div class="equity-change">▲ +$3,204.60 today (+2.63%)</div>
      <div class="equity-bar"></div>
    </div>
    <div class="metrics-row">
      <div class="metric"><div class="metric-label">Win Rate</div><div class="metric-val gold">94.2%</div></div>
      <div class="metric"><div class="metric-label">Monthly ROI</div><div class="metric-val up">+18.7%</div></div>
      <div class="metric"><div class="metric-label">Max Drawdown</div><div class="metric-val dn">3.8%</div></div>
      <div class="metric"><div class="metric-label">Open Trades</div><div class="metric-val gold">5</div></div>
    </div>
    <div class="mini-chart">
      <div class="mini-chart-label">EQUITY CURVE — 30 DAYS</div>
      <svg viewBox="0 0 300 60" preserveAspectRatio="none">
        <defs><linearGradient id="cg" x1="0" y1="0" x2="0" y2="1"><stop offset="0%" stop-color="#D4A843" stop-opacity="0.3"/><stop offset="100%" stop-color="#D4A843" stop-opacity="0"/></linearGradient></defs>
        <path d="M0,55 L20,50 L40,48 L60,42 L80,38 L100,35 L120,28 L140,30 L160,22 L180,18 L200,15 L220,12 L240,8 L260,5 L280,3 L300,1" fill="none" stroke="#D4A843" stroke-width="1.5"/>
        <path d="M0,55 L20,50 L40,48 L60,42 L80,38 L100,35 L120,28 L140,30 L160,22 L180,18 L200,15 L220,12 L240,8 L260,5 L280,3 L300,1 L300,60 L0,60 Z" fill="url(#cg)"/>
      </svg>
    </div>
    <div class="pairs-list">
      <div class="pair-row"><span class="pair-name">EUR/USD</span><span class="pair-price">1.08432</span><span class="pair-dir up">▲ +0.42%</span></div>
      <div class="pair-row"><span class="pair-name">XAU/USD</span><span class="pair-price">2,341.50</span><span class="pair-dir up">▲ +1.18%</span></div>
      <div class="pair-row"><span class="pair-name">GBP/USD</span><span class="pair-price">1.26788</span><span class="pair-dir dn">▼ -0.23%</span></div>
      <div class="pair-row"><span class="pair-name">NAS100</span><span class="pair-price">18,204</span><span class="pair-dir up">▲ +0.87%</span></div>
    </div>
  </div>
</section>

<!-- STATS BAR -->
<div class="stats-bar">
  <div class="stat-item"><div class="stat-num">94%</div><div class="stat-lbl">Win Rate</div></div>
  <div class="stat-item"><div class="stat-num">5+</div><div class="stat-lbl">Years Trading</div></div>
  <div class="stat-item"><div class="stat-num">$2M+</div><div class="stat-lbl">Capital Managed</div></div>
  <div class="stat-item"><div class="stat-num">1:3.8</div><div class="stat-lbl">Avg Risk:Reward</div></div>
  <div class="stat-item"><div class="stat-num">50+</div><div class="stat-lbl">Active Investors</div></div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="about-grid">
    <div class="about-body reveal">
      <div class="section-tag">// About ADMFX</div>
      <h2 class="section-title">Where Precision Meets Profit</h2>
      <div class="gold-line"></div>
      <p>ADMFX is a professional forex account management service built on years of live market experience. We operate across major and minor currency pairs, metals, and indices — always with capital preservation as priority one.</p>
      <p>Our edge is a disciplined fusion of technical confluence, macroeconomic awareness, and iron risk management. Every position is planned. Every risk is defined. Every client is treated as a partner.</p>
      <p>We provide weekly performance reports, full trade transparency, and open communication — because your trust is the foundation of everything we do.</p>
    </div>
    <div class="about-terminal reveal">
      <div class="terminal-bar">
        <div class="t-dot r"></div><div class="t-dot y"></div><div class="t-dot g"></div>
        <div class="t-title">ADMFX — SYSTEM OVERVIEW</div>
      </div>
      <div class="terminal-body">
        <div class="t-line"><span class="t-prompt">›</span><span class="t-cmd">admfx --status</span></div>
        <div class="t-line"><span class="t-out">✓ System: ACTIVE</span></div>
        <div class="t-line"><span class="t-prompt">›</span><span class="t-cmd">admfx --metrics</span></div>
        <div class="t-line"><span class="t-out">WIN_RATE: 94.2%</span></div>
        <div class="t-line"><span class="t-out">AVG_RR: 1:3.8</span></div>
        <div class="t-line"><span class="t-out">MAX_DD: &lt; 5%</span></div>
        <div class="t-line"><span class="t-prompt">›</span><span class="t-cmd">admfx --strategy</span></div>
        <div class="t-line"><span class="t-out2">Mode: Price Action + Macro</span></div>
        <div class="t-line"><span class="t-out2">Pairs: EUR GBP JPY XAU NAS</span></div>
        <div class="t-line"><span class="t-out2">TF: M15 / H1 / H4 / D1</span></div>
        <div class="t-line"><span class="t-prompt">›</span><span class="t-cmd">admfx --investors</span></div>
        <div class="t-line"><span class="t-out">50+ active portfolios</span></div>
        <div class="t-line"><span class="t-out">$2M+ assets under management</span></div>
        <div class="t-line"><span class="t-prompt">›</span><span class="t-out">█</span></div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="skills-wrap">
    <div class="reveal">
      <div class="section-tag">// Expertise</div>
      <h2 class="section-title">Core Trading Skills</h2>
      <div class="gold-line"></div>
    </div>
    <div class="skills-grid">
      <div class="skill-box reveal"><div class="skill-num">01</div><div class="skill-title">Technical Analysis</div><div class="skill-text">Price action, S/R zones, Fibonacci retracements, candlestick patterns, and multi-timeframe confluence strategies.</div><div class="skill-meter"><div class="skill-meter-track"><div class="skill-meter-fill" style="width:95%"></div></div><div class="skill-pct">95% PROFICIENCY</div></div></div>
      <div class="skill-box reveal"><div class="skill-num">02</div><div class="skill-title">Fundamental Analysis</div><div class="skill-text">Central bank decisions, CPI, NFP, interest rate differentials, geopolitical events and their currency impacts.</div><div class="skill-meter"><div class="skill-meter-track"><div class="skill-meter-fill" style="width:88%"></div></div><div class="skill-pct">88% PROFICIENCY</div></div></div>
      <div class="skill-box reveal"><div class="skill-num">03</div><div class="skill-title">Risk Management</div><div class="skill-text">Strict position sizing, correlated-pair exposure control, dynamic stop-loss placement, and drawdown limits.</div><div class="skill-meter"><div class="skill-meter-track"><div class="skill-meter-fill" style="width:98%"></div></div><div class="skill-pct">98% PROFICIENCY</div></div></div>
      <div class="skill-box reveal"><div class="skill-num">04</div><div class="skill-title">Scalping &amp; Swing</div><div class="skill-text">Adaptive across all timeframes — M5 precision scalps to D1 swing setups based on session and volatility conditions.</div><div class="skill-meter"><div class="skill-meter-track"><div class="skill-meter-fill" style="width:91%"></div></div><div class="skill-pct">91% PROFICIENCY</div></div></div>
      <div class="skill-box reveal"><div class="skill-num">05</div><div class="skill-title">Pairs &amp; Instruments</div><div class="skill-text">EUR/USD, GBP/USD, USD/JPY, USD/CHF, XAU/USD (Gold), NAS100, US30, and emerging market currencies.</div><div class="skill-meter"><div class="skill-meter-track"><div class="skill-meter-fill" style="width:85%"></div></div><div class="skill-pct">85% COVERAGE</div></div></div>
      <div class="skill-box reveal"><div class="skill-num">06</div><div class="skill-title">Client Reporting</div><div class="skill-text">Real-time trade alerts, weekly equity reports, monthly performance summaries, and full trade log transparency.</div><div class="skill-meter"><div class="skill-meter-track"><div class="skill-meter-fill" style="width:96%"></div></div><div class="skill-pct">96% PROFICIENCY</div></div></div>
    </div>
  </div>
</section>

<!-- ACCOUNT MANAGEMENT -->
<section id="account">
  <div class="acct-wrap">
    <div class="reveal">
      <div class="section-tag">// Services</div>
      <h2 class="section-title">Forex Account Management</h2>
      <div class="gold-line"></div>
    </div>
    <p class="acct-intro reveal">ADMFX manages your forex account on your behalf using a transparent profit-sharing model. You retain full broker access and ownership. We trade — you earn.</p>
    <div class="how-steps reveal">
      <div class="how-step" data-num="01"><div class="step-icon">🔐</div><div class="step-title">You Fund</div><div class="step-text">Deposit into your own broker account. You keep full control and access at all times.</div></div>
      <div class="how-step" data-num="02"><div class="step-icon">📋</div><div class="step-title">We Agree</div><div class="step-text">Sign a clear profit-sharing agreement. Risk limits and strategy are defined upfront.</div></div>
      <div class="how-step" data-num="03"><div class="step-icon">📈</div><div class="step-title">ADMFX Trades</div><div class="step-text">We execute trades with strict discipline. You receive real-time alerts and weekly reports.</div></div>
      <div class="how-step" data-num="04"><div class="step-icon">💰</div><div class="step-title">Split Profits</div><div class="step-text">At month-end, profits are split per agreement. No base fee — we only earn when you earn.</div></div>
    </div>
    <div class="plans-grid">
      <div class="plan reveal">
        <div class="plan-tier">Starter Tier</div><div class="plan-name">BASIC</div><div class="plan-min">From $500 — $4,999</div>
        <div class="plan-split">30 / 70</div><div class="plan-split-lbl">Investor / Manager profit split</div>
        <ul class="plan-feats"><li>Conservative risk profile (max 3% DD)</li><li>Weekly performance report</li><li>WhatsApp trade alerts</li><li>EUR/USD, GBP/USD focus</li><li>Monthly withdrawal flexibility</li></ul>
      </div>
      <div class="plan featured reveal">
        <div class="plan-star">★ Most Popular</div>
        <div class="plan-tier">Growth Tier</div><div class="plan-name">GROWTH</div><div class="plan-min">From $5,000 — $24,999</div>
        <div class="plan-split">40 / 60</div><div class="plan-split-lbl">Investor / Manager profit split</div>
        <ul class="plan-feats"><li>Moderate–aggressive risk (max 8% DD)</li><li>Bi-weekly video review</li><li>WhatsApp + Telegram alerts</li><li>Multi-pair + Gold trading</li><li>Priority support response</li></ul>
      </div>
      <div class="plan reveal">
        <div class="plan-tier">Premium Tier</div><div class="plan-name">ELITE</div><div class="plan-min">From $25,000+</div>
        <div class="plan-split">50 / 50</div><div class="plan-split-lbl">Investor / Manager profit split</div>
        <ul class="plan-feats"><li>Custom risk parameters</li><li>Daily reporting + calls</li><li>Dedicated account line 24/7</li><li>All pairs + indices</li><li>Quarterly strategy review</li></ul>
      </div>
    </div>
  </div>
</section>

<!-- RESULTS -->
<section id="projects">
  <div class="proj-wrap">
    <div class="reveal">
      <div class="section-tag">// Track Record</div>
      <h2 class="section-title">Selected Trade Results</h2>
      <div class="gold-line"></div>
    </div>
    <table class="trades-table reveal">
      <thead><tr><th>PAIR</th><th>DIR</th><th>ENTRY</th><th>EXIT</th><th>R:R</th><th>PROFIT</th><th>DATE</th></tr></thead>
      <tbody>
        <tr><td class="td-pair">XAU/USD</td><td><span class="td-dir buy">BUY</span></td><td>2,310.50</td><td>2,345.80</td><td class="td-rr">1:4.2</td><td class="td-profit pos">+$1,240</td><td>Mar 2025</td></tr>
        <tr><td class="td-pair">EUR/USD</td><td><span class="td-dir sell">SELL</span></td><td>1.09120</td><td>1.08440</td><td class="td-rr">1:3.8</td><td class="td-profit pos">+$680</td><td>Mar 2025</td></tr>
        <tr><td class="td-pair">GBP/USD</td><td><span class="td-dir buy">BUY</span></td><td>1.25500</td><td>1.27200</td><td class="td-rr">1:5.1</td><td class="td-profit pos">+$1,700</td><td>Feb 2025</td></tr>
        <tr><td class="td-pair">NAS100</td><td><span class="td-dir buy">BUY</span></td><td>17,800</td><td>18,150</td><td class="td-rr">1:3.5</td><td class="td-profit pos">+$2,100</td><td>Feb 2025</td></tr>
        <tr><td class="td-pair">USD/JPY</td><td><span class="td-dir sell">SELL</span></td><td>151.40</td><td>149.80</td><td class="td-rr">1:4.0</td><td class="td-profit pos">+$960</td><td>Jan 2025</td></tr>
        <tr><td class="td-pair">EUR/GBP</td><td><span class="td-dir sell">SELL</span></td><td>0.8640</td><td>0.8610</td><td class="td-rr">1:2.1</td><td class="td-profit neg">-$180</td><td>Jan 2025</td></tr>
      </tbody>
    </table>
    <div class="results-cards">
      <div class="result-card reveal"><div class="result-pair-tag">EUR/USD · Swing · Q3 2024</div><div class="result-title">ECB Divergence Campaign</div><div class="result-desc">Capitalised on ECB–Fed policy divergence. Structured short held 3 weeks with layered take-profits and near-zero drawdown throughout.</div><div class="result-nums"><div><div class="rn-num">+34%</div><div class="rn-lbl">Return</div></div><div><div class="rn-num">1:4.2</div><div class="rn-lbl">Risk:Reward</div></div><div><div class="rn-num">21d</div><div class="rn-lbl">Duration</div></div></div><div class="result-stripe"></div></div>
      <div class="result-card reveal"><div class="result-pair-tag">XAU/USD · Scalp · Q1 2025</div><div class="result-title">Gold Volatility Series</div><div class="result-desc">12 precision scalps on gold reacting to Fed commentary. Zero losing trades, disciplined lot sizing on each entry.</div><div class="result-nums"><div><div class="rn-num">+19%</div><div class="rn-lbl">Return</div></div><div><div class="rn-num">12/12</div><div class="rn-lbl">Win Rate</div></div><div><div class="rn-num">7d</div><div class="rn-lbl">Duration</div></div></div><div class="result-stripe"></div></div>
      <div class="result-card reveal"><div class="result-pair-tag">GBP/USD · Fundamental · Q4 2024</div><div class="result-title">BoE Rate Decision Trade</div><div class="result-desc">Pre-positioned ahead of Bank of England decision based on CPI data analysis. Clean entry, swift exit with minimal drawdown.</div><div class="result-nums"><div><div class="rn-num">+27%</div><div class="rn-lbl">Return</div></div><div><div class="rn-num">2.3%</div><div class="rn-lbl">Max DD</div></div><div><div class="rn-num">4d</div><div class="rn-lbl">Duration</div></div></div><div class="result-stripe"></div></div>
      <div class="result-card reveal"><div class="result-pair-tag">Multi-Pair · Q1 2025</div><div class="result-title">Full Portfolio Quarter</div><div class="result-desc">Managed 4-pair portfolio across 90 days. Correlation controls kept drawdown under 4% while generating 48% quarterly return.</div><div class="result-nums"><div><div class="rn-num">+48%</div><div class="rn-lbl">Quarter</div></div><div><div class="rn-num">3.8%</div><div class="rn-lbl">Max DD</div></div><div><div class="rn-num">90d</div><div class="rn-lbl">Duration</div></div></div><div class="result-stripe"></div></div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-wrap">
    <div class="reveal">
      <div class="section-tag">// Contact</div>
      <h2 class="section-title">Start Your Journey</h2>
      <div class="gold-line"></div>
    </div>
    <div class="contact-grid">
      <div class="reveal">
        <div class="ci-label">Company</div><div class="ci-val">ADMFX — Forex Account Management</div>
        <div class="ci-label">Response Time</div><div class="ci-val">Within 24 hours</div>
        <div class="ci-label">Minimum Investment</div><div class="ci-val">$500 USD</div>
        <div class="contact-channels">
          <a href="https://wa.me/2349164564955" target="_blank" class="channel">
            <div class="channel-icon">💬</div>
            <div><div class="channel-name">WhatsApp</div><div>+234 916 456 4955</div></div>
          </a>
          <a href="https://wa.me/2349164564955" target="_blank" class="channel">
            <div class="channel-icon">📱</div>
            <div><div class="channel-name">Telegram</div><div>@admfx</div></div>
          </a>
          <a href="mailto:contact@admfx.com" class="channel">
            <div class="channel-icon">✉️</div>
            <div><div class="channel-name">Email</div><div>contact@admfx.com</div></div>
          </a>
          <a href="https://wa.me/2349164564955" target="_blank" class="channel">
            <div class="channel-icon">📸</div>
            <div><div class="channel-name">Instagram</div><div>@admfx.official</div></div>
          </a>
        </div>
      </div>
      <div class="reveal">
        <div class="form-row2">
          <div class="form-group"><label>Full Name</label><input type="text" placeholder="Your name"/></div>
          <div class="form-group"><label>Email</label><input type="email" placeholder="your@email.com"/></div>
        </div>
        <div class="form-row2">
          <div class="form-group"><label>WhatsApp / Phone</label><input type="text" placeholder="+234 916 456 4955"/></div>
          <div class="form-group">
            <label>Capital Range</label>
            <select><option value="">Select range</option><option>$500 – $4,999 (Basic)</option><option>$5,000 – $24,999 (Growth)</option><option>$25,000+ (Elite)</option></select>
          </div>
        </div>
        <div class="form-group">
          <label>Trading Experience</label>
          <select><option value="">Select level</option><option>Beginner — new to forex</option><option>Intermediate — some experience</option><option>Advanced — experienced investor</option></select>
        </div>
        <div class="form-group"><label>Message</label><textarea placeholder="Tell me your investment goals and any questions you have..."></textarea></div>
        <a href="https://wa.me/2349164564955" target="_blank" class="btn-gold" style="display:block;text-align:center;padding:1rem;">Send via WhatsApp →</a>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div><div class="footer-logo">ADMFX</div><div class="footer-tagline">Professional Forex Account Management</div></div>
    <div class="footer-links">
      <a href="#about">About</a><a href="#skills">Expertise</a>
      <a href="#account">Management</a><a href="#projects">Results</a><a href="#contact">Contact</a>
    </div>
    <div class="footer-disc">Risk Disclaimer: Forex trading involves significant risk of loss. Past performance is not indicative of future results. Only invest capital you can afford to lose.</div>
  </div>
</footer>

<script>
const ticks = [
  {pair:'EUR/USD',price:'1.08432',chg:'+0.42%',up:true},{pair:'GBP/USD',price:'1.26788',chg:'-0.23%',up:false},
  {pair:'USD/JPY',price:'149.840',chg:'+0.31%',up:true},{pair:'XAU/USD',price:'2341.50',chg:'+1.18%',up:true},
  {pair:'NAS100',price:'18,204',chg:'+0.87%',up:true},{pair:'USD/CHF',price:'0.90412',chg:'-0.15%',up:false},
  {pair:'AUD/USD',price:'0.65321',chg:'+0.22%',up:true},{pair:'USD/CAD',price:'1.35644',chg:'-0.09%',up:false},
  {pair:'EUR/GBP',price:'0.85501',chg:'+0.11%',up:true},{pair:'US30',price:'38,920',chg:'+0.54%',up:true},
];
const track = document.getElementById('ticker');
const html = ticks.map(t=>`<div class="tick-item"><span class="tick-pair">${t.pair}</span><span class="tick-price">${t.price}</span><span class="tick-chg ${t.up?'up':'dn'}">${t.chg}</span></div>`).join('');
track.innerHTML = html + html;

const obs = new IntersectionObserver(entries=>{entries.forEach(e=>{if(e.isIntersecting)e.target.classList.add('visible')});},{threshold:0.1});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));
document.querySelectorAll('.skills-grid,.plans-grid,.results-cards').forEach(g=>{[...g.children].forEach((c,i)=>{c.style.transitionDelay=`${i*0.08}s`})});
</script>
</body>
</html>
