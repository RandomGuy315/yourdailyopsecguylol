<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Terminal-style Black Page</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      background:#0b0710;
      color:#e6e6e6;
      font-family: 'Inter', ui-sans-serif, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      text-rendering:optimizeLegibility;
      display:flex;
      flex-direction:column;
      min-height:100vh;
    }

    .topbar{
      height:46px;
      display:flex;
      align-items:center;
      justify-content:center;
      position:relative;
      padding:0 20px;
    }
    .top-title{
      font-size:12px;
      letter-spacing:2px;
      color:#cfc6d8;
      opacity:0.95;
      font-weight:600;
    }

    /* Animated RGB-like shining bar */
    .accent-line{
      height:6px;
      width:100vw; /* always span full device width */
      margin-left:calc(-50vw + 50%); /* center and stretch */
      background:linear-gradient(90deg, red, orange, yellow, lime, cyan, blue, magenta, red);
      background-size:400% 100%;
      animation: shine 6s linear infinite;
    }

    @keyframes shine {
      0%{background-position:0% 50%}
      100%{background-position:100% 50%}
    }

    /* Credits under the RGB line */
    .top-credits{
      text-align:center;
      font-size:12px;
      color:rgba(207,200,216,0.55);
      margin-top:6px; /* small separation from the accent */
      padding:6px 16px 0;
      line-height:1.3;
      z-index:2;
      position:relative;
      max-width:100%;
      overflow-wrap:break-word;
      font-weight:300;
    }

    /* Make the important links subtle rainbow-matched and animated with same shine */
    .top-credits a{
      text-decoration:underline;
      color:inherit;
    }
    .rainbow-link{
      background:linear-gradient(90deg, red, orange, yellow, lime, cyan, blue, magenta, red);
      background-size:400% 100%;
      -webkit-background-clip:text;
      -webkit-text-fill-color:transparent;
      animation: shine 6s linear infinite;
      font-weight:600;
    }

    .stage{
      flex:1;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:36px 20px;
    }

    .terminal{
      width:min(980px,96%);
      border-radius:10px;
      padding:28px 32px;
      background:rgba(0,0,0,0.45);
      border:1px solid rgba(255,255,255,0.03);
      position:relative;
      box-shadow:0 8px 30px rgba(2,1,8,0.6);
    }

    .terminal::after{
      content:"";
      position:absolute;
      inset:-8px;
      border-radius:12px;
      pointer-events:none;
      background:linear-gradient(90deg, rgba(255,0,0,0.4), rgba(255,120,120,0.4), rgba(255,0,0,0.4));
      background-size:300% 100%;
      animation: glow 5s linear infinite;
      -webkit-mask: linear-gradient(#fff,#fff) content-box, linear-gradient(#fff,#fff);
      -webkit-mask-composite: xor;
      mask-composite: exclude;
      padding:1px;
    }

    @keyframes glow {
      0%{background-position:0% 50%}
      100%{background-position:100% 50%}
    }

    #content{
      color:#dcd6e6;
      font-size:15px;
      line-height:1.6;
      white-space:pre-wrap;
      min-height:260px;
      max-height:72vh;
      overflow:auto;
      letter-spacing:0.2px;
      font-weight:300;
    }

    #content code, #content pre{
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, 'Roboto Mono', monospace;
      background:transparent;
      color:inherit;
    }

    .muted{
      color:rgba(207,200,216,0.55);
      font-size:12px;
    }

    .hint{
      margin-top:12px;
      font-size:12px;
      color:rgba(207,200,216,0.45);
    }

    @media (max-width:600px){
      .terminal{padding:18px}
      #content{font-size:15px}
      .top-credits{font-size:11px}
    }
  </style>
</head>
<body>
  <div class="topbar">
    <div class="top-title">TERMINAL</div>
  </div>

  <div class="accent-line" aria-hidden="true"></div>

  <!-- ADDED: credits under the top RGB outline -->
  <div class="top-credits" aria-hidden="false">
    All Credits to <strong>shadowhvh</strong> — I have simply taken heavy inspiration and thought to copy his website. Ensure to go look at his guide as he is the best you can find: 
    <a class="rainbow-link" href="https://bigtime.bio/opsec/" target="_blank" rel="noopener noreferrer">GUIDE here</a>.<br>
    Or you can go join his DISCORD server at: 
    <a class="rainbow-link" href="https://discord.gg/zu9Dc2Hn" target="_blank" rel="noopener noreferrer">https://discord.gg/zu9Dc2Hn</a>
  </div>

  <main class="stage">
    <article class="terminal" role="main" aria-label="Read-only content area">
      <div id="content">
&gt; Welcome — this text area is now read-only.

&gt; Replace this placeholder text in the HTML file with your own content.

&gt; It will display here but cannot be edited directly in the browser.
      </div>
      <div class="hint">Edit the file source to change the text. The display is read-only in the browser.</div>
    </article>
  </main>
</body>
</html>
