<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Para Maria Eduarda Savioti meu amor 💖</title>
  <style>
    :root{
      --bg:#ff0080;
      --card:#ffffff;
      --accent:#ff6b9a;
      --muted:#666;
      --success:#2e8b57;
      --danger:#c0392b;
      font-family: "Segoe UI", Roboto, Arial, sans-serif;
    }
    body{
      background: linear-gradient(135deg,var(--bg), #fff);
      margin:0;
      min-height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:24px;
    }
    .card{
      width:100%;
      max-width:520px;
      background:var(--card);
      box-shadow:0 10px 30px rgba(0,0,0,0.08);
      border-radius:12px;
      padding:28px;
      text-align:center;
    }
    h1{ margin:0 0 6px; font-size:22px; color:#222; }
    p.lead{ margin:0 0 18px; color:var(--muted); }
    input[type="text"], input[type="password"]{
      width:100%;
      padding:12px 14px;
      border-radius:8px;
      border:1px solid #e6e6e6;
      margin-bottom:12px;
      font-size:16px;
    }
    button{
      padding:10px 14px;
      border:0;
      border-radius:8px;
      background:var(--accent);
      color:white;
      font-weight:600;
      cursor:pointer;
      font-size:15px;
    }
    button.secondary{
      background:transparent;
      color:var(--accent);
      border:2px solid rgba(255,107,154,0.12);
    }
    .msg{ margin-top:14px; font-weight:700; }
    .msg.ok{ color:var(--success); }
    .msg.err{ color:var(--danger); }
    .love-btns{ display:flex; gap:12px; justify-content:center; margin-top:14px; }
    .big{
      font-size:28px;
      margin-top:10px;
      font-weight:800;
      letter-spacing:0.5px;
    }
    .hearts{
      font-size:40px;
      margin-top:6px;
      color:var(--accent);
      animation:pop 900ms ease infinite;
      display:inline-block;
    }
    @keyframes pop{
      0% { transform: translateY(0) scale(1); opacity:1; }
      50% { transform: translateY(-6px) scale(1.03); opacity:0.9; }
      100% { transform: translateY(0) scale(1); opacity:1; }
    }
    footer{ margin-top:18px; font-size:12px; color:var(--muted);}
    @media (max-width:420px){ .card{ padding:18px; } }
  </style>
</head>
<body>
  <main class="card" role="main" aria-labelledby="title">
    <h1 id="title">Para Maria Eduarda 💖</h1>
    <p class="lead">As duas partes do site estão aqui, caso não saiba alguma descubra! 💌</p>

    <div id="step-name">
      <label for="nameInput" style="display:block;text-align:left;margin-bottom:8px;font-weight:600">Digite o nome do meu amorzão</label>
      <input id="nameInput" type="text" placeholder="Seu nome completo" autocomplete="off" />
      <button id="checkNameBtn">Verificar nome</button>
      <div id="nameMsg" class="msg" aria-live="polite"></div>
    </div>

    <div id="step-question" style="display:none;margin-top:20px">
      <div style="font-weight:700;margin-bottom:8px;font-size:18px;">VOCÊ ME AMA?</div>
      <div class="love-btns">
        <button id="btnYes">SIM</button>
        <button id="btnNo" class="secondary">NÃO</button>
      </div>
      <div id="answerBox" style="margin-top:18px"></div>
    </div>

    <div id="step-password" style="display:none;margin-top:20px">
      <label for="pwd" style="display:block;text-align:left;margin-bottom:8px;font-weight:600">Agora digite a senha</label>
      <input id="pwd" type="password" placeholder="Digite aqui..." />
      <a href="segredo.html"> <button id="checkPwdBtn">Enviar senha</button> </a>
      <div id="pwdMsg" class="msg" aria-live="polite"></div>
    </div>
  </main>

  <script>
    // Nome correto
    const expectedName = "Maria Eduarda Savioti";
    // Senha correta
    const correctPassword = "DIGITE A SENHA AQUI (suguestao: VOCE QUER NAMORAR CMG?)";

    const normalize = s => s.trim().replace(/\s+/g,' ').toLowerCase();

    const nameInput = document.getElementById('nameInput');
    const checkNameBtn = document.getElementById('checkNameBtn');
    const nameMsg = document.getElementById('nameMsg');
    const stepQuestion = document.getElementById('step-question');
    const btnYes = document.getElementById('btnYes');
    const btnNo = document.getElementById('btnNo');
    const answerBox = document.getElementById('answerBox');
    const stepPassword = document.getElementById('step-password');
    const pwdInput = document.getElementById('pwd');
    const checkPwdBtn = document.getElementById('checkPwdBtn');
    const pwdMsg = document.getElementById('pwdMsg');

    function show(el){ el.style.display = ''; }
    function hide(el){ el.style.display = 'none'; }

    checkNameBtn.addEventListener('click', ()=>{
      const given = normalize(nameInput.value || '');
      const expected = normalize(expectedName);
      if(!given){
        nameMsg.textContent = 'Por favor, digite o nome.';
        nameMsg.className = 'msg err';
        hide(stepQuestion);
        hide(stepPassword);
        return;
      }
      if(given === expected){
        nameMsg.textContent = 'Acertou o seu nome meu amor! 💖';
        nameMsg.className = 'msg ok';
        show(stepQuestion);
        hide(stepPassword);
      } else {
        nameMsg.textContent = 'Pq vc colocou isso?';
        nameMsg.className = 'msg err';
        hide(stepQuestion);
        hide(stepPassword);
      }
    });

    btnYes.addEventListener('click', ()=>{
      answerBox.innerHTML = `
        <div class="big" style="color:var(--accent)">QUE BOM QUE VOCÊ ME AMA! ❤️</div>
        <div class="hearts">💖💞</div>
      `;
      show(stepPassword);
    });

    btnNo.addEventListener('click', ()=>{
      answerBox.innerHTML = `
        <div class="big" style="color:var(--danger)">OXI? TA FICANDO DOIDA?</div>
      `;
      hide(stepPassword);
    });

    checkPwdBtn.addEventListener('click', ()=>{
      const pwd = normalize(pwdInput.value || '');
      const good = normalize(correctPassword);
      if(pwd === good){
        pwdMsg.textContent = 'AGUARDE... ❤️';
        pwdMsg.className = 'msg ok';
      } else {
        pwdMsg.textContent = 'Senha incorreta tente denovo 😅';
        pwdMsg.className = 'msg err';
      }
    });

    nameInput.addEventListener('keydown', e => { if(e.key === 'Enter') checkNameBtn.click(); });
    pwdInput.addEventListener('keydown', e => { if(e.key === 'Enter') checkPwdBtn.click(); });
  </script>
</body>
</html>
