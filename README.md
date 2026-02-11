<!doctype html>
<html lang="zh-Hant">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<meta name="theme-color" content="#ff6b9e">
<title>過年親戚問題｜報價單</title>

<style>
*{box-sizing:border-box;margin:0;padding:0;}

body{
  font-family:system-ui,-apple-system,"Segoe UI","Noto Sans TC",sans-serif;
  min-height:100svh;
  background:linear-gradient(135deg,#ff6b9e,#7b61ff);
  display:flex;
  justify-content:center;
  align-items:flex-start;
  overflow:auto;
  padding:24px 18px 40px;
}

.container{
  width:100%;
  max-width:520px;
  background:rgba(255,255,255,.85);
  backdrop-filter:blur(10px);
  border-radius:20px;
  padding:26px 20px 30px;
  box-shadow:0 20px 50px rgba(0,0,0,.25);
}

h1{
  font-size:22px;
  margin-bottom:14px;
}

p{
  font-size:16px;
  line-height:1.6;
  margin-bottom:24px;
}

.buttons{
  position:relative;
  height:180px;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  gap:16px;
}

button{
  width:100%;
  padding:16px;
  border:none;
  border-radius:999px;
  font-size:16px;
  font-weight:700;
  cursor:pointer;
  transition:.1s ease;
}

button:active{transform:scale(.98);}

#yes{
  background:linear-gradient(135deg,#00c853,#00b0ff);
  color:white;
}

#no{
  background:#eee;
  color:#333;
  position:absolute;
}

.result{
  display:none;
  margin-top:24px;
  padding:18px;
  border-radius:16px;
  background:white;
  animation:fade .3s ease;
}

@keyframes fade{
  from{opacity:0;transform:translateY(10px);}
  to{opacity:1;transform:translateY(0);}
}

.price{
  margin-top:12px;
  font-weight:600;
  line-height:1.8;
}

.deal{
  margin-top:18px;
  padding:14px;
  border-radius:14px;
  background:linear-gradient(135deg,#ffe4ec,#e7e0ff);
  font-weight:700;
}
</style>
</head>

<body>

<div class="container">

<h1>過年親戚問題｜應對模式</h1>

<p>
過年回家，總有幾位很關心人生進度的長輩。<br>
「啊你什麼時候結婚？」<br>
請選擇你的應對方式。
</p>

<div class="buttons">
  <button id="yes">掏出「報價單」</button>
  <button id="no">免費聊天</button>
</div>

<div class="result" id="result">
  <strong>✅ 已進入付費諮詢流程（不接受議價）</strong>

  <div class="price">
  感情問題（結婚/生小孩） $5,500 / 題<br>
  工作問題（薪水/升遷） $3,500 / 題<br>
  * 超過三題視為方案，請先匯款再開口。
  </div>

  <div class="deal">
  過年限定<br>
  沐光妍選 日本高人氣指定商品 三件 8 折（把話題轉去購物最安全）
  </div>
</div>

</div>

<script>
const noBtn=document.getElementById('no');
const yesBtn=document.getElementById('yes');
const result=document.getElementById('result');
const buttons=document.querySelector('.buttons');

function moveNo(){
  const area=buttons.getBoundingClientRect();
  const btn=noBtn.getBoundingClientRect();

  const maxX=area.width-btn.width;
  const maxY=area.height-btn.height;

  const x=Math.random()*maxX;
  const y=Math.random()*maxY;

  noBtn.style.left=x+"px";
  noBtn.style.top=y+"px";
}

noBtn.addEventListener('mouseenter',moveNo);
noBtn.addEventListener('touchstart',moveNo);
noBtn.addEventListener('click',moveNo);

yesBtn.addEventListener('click',()=>{
  result.style.display="block";
  yesBtn.style.display="none";
  noBtn.style.display="none";
});
</script>

</body>
</html>
