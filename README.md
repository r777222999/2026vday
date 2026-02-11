<!doctype html>
<html lang="zh-Hant">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />
  <meta name="theme-color" content="#ff6b9e" />
  <title>過年親戚問題｜報價單</title>

  <style>
    :root { --card: rgba(255,255,255,.78); }
    * { box-sizing: border-box; }

    body{
      margin:0;
      min-height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      font-family: system-ui, -apple-system, "Segoe UI", "Noto Sans TC", sans-serif;
      background:
        radial-gradient(circle at 20% 20%, #ffd1dc 0%, transparent 35%),
        radial-gradient(circle at 80% 30%, #ffe8a3 0%, transparent 40%),
        radial-gradient(circle at 50% 80%, #c7f0ff 0%, transparent 45%),
        linear-gradient(135deg, #ff6b9e, #7b61ff);
      overflow:hidden;
    }

    .hearts{
      position:fixed; inset:0; pointer-events:none; opacity:.22;
      background-image:
        radial-gradient(circle at 10% 20%, #fff 0 2px, transparent 3px),
        radial-gradient(circle at 70% 30%, #fff 0 2px, transparent 3px),
        radial-gradient(circle at 30% 80%, #fff 0 2px, transparent 3px);
      background-size: 220px 220px;
      animation: float 10s linear infinite;
    }
    @keyframes float { from{ transform:translateY(0)} to{ transform:translateY(-30px)} }

    .card{
      width:min(760px, 92vw);
      background:var(--card);
      border:1px solid rgba(255,255,255,.6);
      backdrop-filter: blur(10px);
      border-radius:24px;
      padding:28px 22px;
      box-shadow: 0 20px 60px rgba(0,0,0,.25);
      text-align:center;
      position:relative;
    }

    h1{ margin:0 0 10px; font-size:clamp(24px, 4vw, 40px); }
    p{ margin:0 0 18px; font-size:clamp(15px, 2.2vw, 18px); line-height:1.65; }

    .buttons{
      position:relative;
      height:120px;
      display:flex;
      align-items:center;
      justify-content:center;
      gap:14px;
      margin-top:6px;
    }

    button{
      border:0;
      padding:14px 18px;
      border-radius:999px;
      font-size:16px;
      cursor:pointer;
      box-shadow: 0 10px 25px rgba(0,0,0,.15);
      transition: transform .08s ease;
      user-select:none;
      min-width:170px;
      font-weight:800;
      white-space:nowrap;
    }
    button:active{ transform: scale(.98); }

    #yes{
      background: linear-gradient(135deg, #00c853, #00b0ff);
      color:white;
    }
    #no{
      background: rgba(255,255,255,.92);
      color:#222;
      position:absolute;
      left:50%;
      top:50%;
      transform: translate(120px, -50%);
      font-weight:800;
    }

    .result{
      display:none;
      margin-top:16px;
      padding:16px 16px;
      border-radius:16px;
      background: rgba(255,255,255,.92);
      text-align:left;
      max-width:640px;
      margin-left:auto;
      margin-right:auto;
      animation: pop .35s ease;
      line-height:1.7;
      font-size:clamp(15px, 2.2vw, 18px);
    }
    .result h2{
      margin:0 0 10px;
      font-size:18px;
      letter-spacing:.2px;
    }
    .price{
      border:1px dashed rgba(0,0,0,.18);
      border-radius:14px;
      padding:12px 12px;
      margin:10px 0 12px;
      background: rgba(255,255,255,.7);
    }
    .price .row{
      display:flex;
      justify-content:space-between;
      gap:10px;
      padding:6px 2px;
      font-weight:700;
    }
    .price .muted{
      opacity:.75;
      font-weight:650;
      font-size:14px;
      margin-top:6px;
    }
    .deal{
      margin-top:10px;
      padding:12px 12px;
      border-radius:14px;
      background: linear-gradient(135deg, rgba(255,107,158,.18), rgba(123,97,255,.15));
      border:1px solid rgba(0,0,0,.08);
    }
    .deal strong{ font-weight:900; }

    @keyframes pop{
      from{ transform:scale(.98); opacity:0 }
      to{ transform:scale(1); opacity:1 }
    }

    .tiny{
      margin-top:10px;
      opacity:.68;
      font-size:13px;
    }

    /* ✅ 手機全屏顯示：消掉「中間卡片感」 */
    @media (max-width: 768px){
      body{
        align-items:flex-start;
        justify-content:flex-start;
        overflow:auto;
      }
      .hearts{
        position:fixed;
      }
      .card{
        width:100vw;
        min-height:100svh; /* iOS 新單位，比 100vh 更準 */
        border-radius:0;
        padding:22px 18px 40px;
        box-shadow:none;
        border-left:0;
        border-right:0;
      }
      .result{
        max-width:100%;
      }
      .buttons{
        height:130px;
      }
      button{
        min-width:160px;
      }
    }
  </style>
</head>

<body>
  <div class="hearts"></div>

  <div class="card">
    <h1>過年親戚問題｜應對模式</h1>
    <p>
      過年回家，總有幾位很關心人生進度的長輩。<br/>
      「啊你什麼時候結婚？」<br/>
      請選擇你的應對方式。
    </p>

    <div class="buttons">
      <button id="yes">掏出「報價單」</button>
      <button id="no">免費聊天</button>
    </div>

    <div class="result" id="result">
      <h2>✅ 已進入付費諮詢流程（不接受議價）</h2>

      <div class="price" role="group" aria-label="親戚提問報價單">
        <div class="row"><span>感情問題（結婚/生小孩）</span><span>$5,500 / 題</span></div>
        <div class="row"><span>工作問題（薪水/升遷）</span><span>$3,500 / 題</span></div>
        <div class="muted">* 超過三題視為方案，請先匯款再開口。</div>
      </div>

      <div class="deal">
        <div>順便提醒：過年限定</div>
        <div><strong>沐光妍選 日本高人氣指定商品 三件 8 折</strong>（把話題轉去購物最安全）</div>
      </div>

      <div class="tiny">（放心，「免費聊天」那個按鈕本來就很難按到。）</div>
    </div>
  </div>

  <script>
    const noBtn = document.getElementById('no');
    const yesBtn = document.getElementById('yes');
    const result = document.getElementById('result');
    const buttons = document.querySelector('.buttons');

    function moveNo(){
      const area = buttons.getBoundingClientRect();
      const btn = noBtn.getBoundingClientRect();

      const maxX = Math.max(0, area.width - btn.width);
      const maxY = Math.max(0, area.height - btn.height);

      const x = Math.random() * maxX;
      const y = Math.random() * maxY;

      noBtn.style.left = x + 'px';
      noBtn.style.top = y + 'px';
      noBtn.style.transform = 'translate(0, 0)';
    }

    // 讓「免費聊天」更難按到：靠近就跑 + 點到也跑（含手機）
    noBtn.addEventListener('mouseenter', moveNo);
    noBtn.addEventListener('touchstart', (e) => { e.preventDefault(); moveNo(); }, {passive:false});
    noBtn.addEventListener('click', (e) => { e.preventDefault(); moveNo(); });

    yesBtn.addEventListener('click', () => {
      result.style.display = 'block';
      yesBtn.style.display = 'none';
      noBtn.style.display = 'none';
    });
  </script>
</body>
</html>
