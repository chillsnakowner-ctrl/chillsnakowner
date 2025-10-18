<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Education Pulse — Quick Survey</title>

  <style>
    :root{
      --bg1: linear-gradient(135deg,#0f172a 0%, #0b1220 50%);
      --accent: linear-gradient(90deg,#7c3aed,#06b6d4);
      --card: rgba(255,255,255,0.04);
      --muted: rgba(255,255,255,0.7);
      --glass: rgba(255,255,255,0.04);
      --shadow: 0 10px 30px rgba(2,6,23,0.6);
      --glass-border: rgba(255,255,255,0.06);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      min-height:100%;
      background: var(--bg1);
      color:#e6eef8;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:28px;
    }

    .container{
      width:100%;
      max-width:1100px;
      display:grid;
      grid-template-columns: 1fr 460px;
      gap:28px;
      align-items:stretch;
    }

    @media (max-width:980px){
      .container{grid-template-columns:1fr;max-width:920px}
      .hero {order:2}
      .panel {order:1}
    }

    .hero{
      background: linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
      border-radius:20px;
      padding:40px;
      box-shadow: var(--shadow);
      border: 1px solid var(--glass-border);
      position:relative;
      overflow:hidden;
      min-height:420px;
      display:flex;
      flex-direction:column;
      justify-content:center;
    }

    .logo{display:inline-flex;align-items:center;gap:12px;margin-bottom:18px;}
    .logo .mark{
      width:56px;height:56px;border-radius:12px;
      background:var(--accent);
      display:flex;align-items:center;justify-content:center;
      font-weight:700;color:white;font-size:20px;
      box-shadow:0 6px 18px rgba(124,58,237,0.25);
    }
    .logo h1{font-size:20px;letter-spacing:0.2px}
    .subtitle{color:var(--muted);margin-bottom:18px}
    h2{
      font-size:34px;
      line-height:1.1;
      margin-bottom:12px;
      background: linear-gradient(90deg,#fff, #a8e9ff);
      -webkit-background-clip:text;
      color:transparent;
    }
    p.lead{color:var(--muted);max-width:56ch;margin-bottom:22px}
    .features{display:flex;gap:14px;flex-wrap:wrap;margin-top:auto;}
    .chip{
      background: linear-gradient(90deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));
      padding:10px 14px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);
      display:inline-flex;gap:10px;align-items:center;font-weight:600;color:var(--muted);
      box-shadow:0 6px 20px rgba(2,6,23,0.45);
    }
    .chip svg{opacity:0.9}

    .hero::before, .hero::after{
      content:"";
      position:absolute;
      border-radius:50%;
      filter:blur(36px);
      opacity:0.5;
      transform:translateZ(0);
    }
    .hero::before{
      width:360px;height:360px;background:radial-gradient(circle at 30% 30%, rgba(124,58,237,0.28), transparent 35%);
      right:-120px;top:-80px;
    }
    .hero::after{
      width:260px;height:260px;background:radial-gradient(circle at 70% 70%, rgba(6,182,212,0.16), transparent 35%);
      left:-90px;bottom:-70px;
    }

    .panel{
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius:18px;
      padding:26px;
      min-height:420px;
      box-shadow: var(--shadow);
      border:1px solid var(--glass-border);
      display:flex;
      flex-direction:column;
      gap:14px;
    }

    .panel header{display:flex;align-items:center;justify-content:space-between;gap:12px;margin-bottom:6px;flex-wrap:wrap;}
    .panel header h3{font-size:18px}
    .panel header p{color:var(--muted);font-size:13px}

    form{display:flex;flex-direction:column;gap:14px;width:100%}
    .field{background:var(--card);padding:12px;border-radius:12px;border:1px solid rgba(255,255,255,0.02);display:flex;flex-direction:column;gap:8px;width:100%}
    label{font-size:13px;font-weight:700;color:#f2f8ff}
    .muted{font-size:13px;color:var(--muted)}
    .options{display:flex;gap:8px;flex-wrap:wrap}
    .options input[type="radio"]{display:none}
    .radio{
      padding:8px 12px;border-radius:10px;background:transparent;border:1px solid rgba(255,255,255,0.03);
      cursor:pointer;user-select:none;font-weight:600;color:var(--muted);
      transition:all .18s ease;
    }
    .radio:hover{transform:translateY(-3px)}
    .options input[type="radio"]:checked + .radio{
      background:var(--accent);color:white;
      box-shadow:0 8px 20px rgba(7,17,27,0.5), inset 0 -3px 12px rgba(0,0,0,0.18);
      border:none;
    }
    select, textarea, input[type="text"]{
      background:transparent;border:1px solid rgba(255,255,255,0.04);padding:10px;border-radius:8px;color:inherit;font-size:14px;
      outline:none;resize:vertical;width:100%;
    }
    select:focus, textarea:focus, input[type="text"]:focus{
      border:1px solid rgba(255,255,255,0.08);box-shadow:0 6px 18px rgba(2,6,23,0.5);
    }

    .btn{
      display:inline-flex;align-items:center;justify-content:center;gap:10px;padding:12px 16px;border-radius:12px;
      border:0;cursor:pointer;font-weight:700;background:linear-gradient(90deg,#06b6d4,#7c3aed);color:white;
      box-shadow:0 12px 30px rgba(9,10,20,0.6);transition:transform .14s ease;
      width:100%;
    }
    .btn:hover{transform:translateY(-4px)}
    .small{font-size:12px;color:var(--muted);text-align:center;margin-top:6px}
    .note{margin-top:8px;padding:12px;border-radius:10px;background:linear-gradient(180deg, rgba(7,20,40,0.35), rgba(7,20,40,0.25));border:1px solid rgba(255,255,255,0.03);color:var(--muted);font-size:13px;}
    footer.foot{margin-top:auto;text-align:center;color:var(--muted);font-size:13px;padding-top:10px}
    a.brandlink{color:inherit;text-decoration:none;font-weight:700}
    .hero, .panel{transform:translateY(8px);opacity:0;animation:enter .6s cubic-bezier(.2,.9,.26,1) forwards}
    .panel{animation-delay:.09s}
    @keyframes enter{to{transform:none;opacity:1}}

    /* Small device adjustments */
    @media (max-width:700px){
      body{padding:16px}
      .container{gap:18px}
      .hero,.panel{padding:18px;min-height:auto}
      h2{font-size:24px}
      .logo .mark{width:46px;height:46px;font-size:18px}
      .chip{padding:8px 10px;font-size:12px}
      .btn{padding:10px 14px;font-size:15px}
    }
    @media (max-width:480px){
      h2{font-size:20px}
      .panel header{flex-direction:column;align-items:flex-start;gap:4px}
      select,textarea,input[type="text"]{font-size:13px}
    }
  </style>
</head>
<body>
  <!-- same HTML content as your file -->
</body>
</html>
