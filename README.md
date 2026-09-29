# math-quiz

<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>115年度教師檢定數學科複習 - 練功房</title>
<style>
/* ── 宮崎駿暖色系與微動畫背景設定 ── */
*{box-sizing:border-box;margin:0;padding:0;}
:root {
  --bg-color: #fcf8f2;
  --card-bg: #ffffff;
  --primary: #5c6f58;        /* 森林綠 */
  --primary-dark: #3f4c3b;
  --accent: #d97757;         /* 暖夕陽橘 */
  --accent-light: #f4e8e1;
  --text-main: #3a3532;
  --text-muted: #7c736e;
  --border-color: #e6ded5;
}
body {
  font-family:'Microsoft JhengHei','微軟正黑體',sans-serif;
  background: var(--bg-color); color: var(--text-main);
  line-height:1.8; font-size:15px; position: relative; min-height: 100vh; overflow-x: hidden;
}
.ambient-bg {
  position: fixed; bottom: 0; left: 0; width: 100%; height: 220px; z-index: 0; pointer-events: none; opacity: 0.25; overflow: hidden;
}
.ambient-mountain {
  position: absolute; bottom: 0; left: 0; width: 200%; height: 140px;
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1200 120'%3E%3Cpath fill='%23a3b19b' d='M0,60 C150,20 350,100 600,40 C850,-20 1050,80 1200,50 L1200,120 L0,120 Z'/%3E%3C/svg%3E") repeat-x;
  animation: mountainSway 45s linear infinite;
}
@keyframes mountainSway { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }
.ambient-trees {
  position: absolute; bottom: 0; left: 0; width: 200%; height: 90px;
  background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1200 90'%3E%3Cpath fill='%23588157' d='M0,50 Q30,10 60,50 Q90,20 120,50 Q150,5 180,50 Q210,15 240,50 Q270,10 300,50 Q330,20 360,50 Q390,5 420,50 Q450,15 480,50 Q510,10 540,50 Q570,20 600,50 Q630,5 660,50 Q690,15 720,50 Q750,10 780,50 Q810,20 840,50 Q870,5 900,50 Q930,15 960,50 Q990,10 1020,50 Q1050,20 1080,50 Q1110,5 1140,50 Q1170,15 1200,50 L1200,90 L0,90 Z'/%3E%3C/svg%3E") repeat-x;
  animation: treeSway 18s ease-in-out infinite alternate;
}
@keyframes treeSway { 0% { transform: translateX(0) skewX(0deg); } 100% { transform: translateX(-2%) skewX(-1.5deg); } }

.header{ background: linear-gradient(135deg, #5c6f58, #3a4a37); color: #fff; padding: 24px 30px; text-align: center; position: relative; z-index: 10; box-shadow: 0 4px 12px rgba(92,111,88,0.15); }
.header h1{font-size: 21px; letter-spacing: 1px; margin-bottom: 6px;}
.header p{font-size: 13.5px; opacity: .9;}

.sticky-bar{
  position: sticky; top: 0; z-index: 200; background: rgba(252, 248, 242, 0.92); backdrop-filter: blur(8px);
  color: var(--text-main); display: flex; align-items: center; justify-content: space-between; padding: 10px 28px;
  border-bottom: 1px solid var(--border-color); box-shadow: 0 2px 10px rgba(0,0,0,.04);
}
.timer-label{font-size: 13px; color: var(--text-muted);}
#timer{font-size: 20px; font-weight: 700; letter-spacing: 1px; color: var(--primary-dark);}
#timer.warn{color: #d97757;}
#timer.danger{color: #bc4749; animation: pulse 1s infinite;}
@keyframes pulse { 50%{opacity:.5;} }

.container{max-width: 880px; margin: 0 auto; padding: 24px 16px 60px; position: relative; z-index: 10;}
.card{ background: var(--card-bg); border-radius: 12px; padding: 24px 28px; margin-bottom: 20px; box-shadow: 0 4px 16px rgba(58,53,50,.04); border: 1px solid var(--border-color); }
.card h2{font-size: 16px; color: var(--primary-dark); border-bottom: 2px solid var(--accent-light); padding-bottom: 8px; margin-bottom: 16px;}
.form-row{display: flex; gap: 16px; flex-wrap: wrap;}
.form-group{flex: 1; min-width: 180px;}
.form-group label{display: block; font-size: 13px; color: var(--text-muted); margin-bottom: 5px;}
.form-group input{width: 100%; padding: 10px 14px; border: 1.5px solid var(--border-color); border-radius: 8px; font-size: 14px; font-family: inherit; outline: none; background: #fff;}
.instructions{ background: var(--accent-light); border-left: 4px solid var(--accent); border-radius: 0 10px 10px 0; padding: 14px 20px; font-size: 14px; margin-bottom: 22px; color: #59392e; }
.sec-header{background: var(--primary); color: #fff; border-radius: 10px 10px 0 0; padding: 12px 22px; font-size: 15px; font-weight: 700;}
.sec-desc{background: #f4f1ea; padding: 10px 22px; font-size: 13.5px; color: var(--text-muted); border-left: 1px solid var(--border-color); border-right: 1px solid var(--border-color);}
.q-wrap{background: var(--card-bg); border-left: 1px solid var(--border-color); border-right: 1px solid var(--border-color); border-bottom: 1px solid var(--border-color); padding: 22px 26px;}
.q-title{margin-bottom: 14px; font-size: 15px; color: var(--text-main);}
.q-num{display: inline-block; background: var(--primary); color: #fff; border-radius: 6px; font-size: 12px; font-weight: 700; padding: 2px 8px; margin-right: 8px;}
.options{display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 10px;}
.opt{ display: flex; align-items: flex-start; gap: 10px; padding: 10px 14px; border: 1.5px solid var(--border-color); border-radius: 8px; cursor: pointer; background: #faf8f5; }
.opt:hover{background: #f0ebe1; border-color: var(--primary);}
.opt.selected{background: var(--accent-light); border-color: var(--accent); color: #59392e; font-weight: 500;}
.q-status{float: right; font-size: 12px; color: #b5a99f;}
.q-status.done{color: var(--primary); font-weight: bold;}
.submit-area{text-align: center; margin-top: 24px;}
.btn-submit{ background: var(--primary); color: #fff; border: none; padding: 14px 52px; border-radius: 10px; font-size: 17px; cursor: pointer; box-shadow: 0 6px 16px rgba(92,111,88,0.25); }
.modal-bg{display:none; position:fixed; inset:0; background:rgba(58,53,50,0.6); z-index:500; align-items:center; justify-content:center; backdrop-filter: blur(4px);}
.modal-bg.show{display:flex;}
.modal{background:#fff; border-radius:16px; padding:38px 32px 32px; max-width:480px; width:92%; text-align:center; box-shadow:0 16px 40px rgba(0,0,0,.15);}
.score-ring{width:120px; height:120px; border-radius:50%; background:linear-gradient(135deg, var(--primary), var(--accent)); display:flex; flex-direction:column; align-items:center; justify-content:center; margin:0 auto 18px;}
.score-ring .snum{font-size:38px; font-weight:900; color:#fff;}
.score-ring .stot{font-size:13px; color:rgba(255,255,255,0.85);}
.stat-row{display:flex; justify-content:space-between; padding:8px 0; border-bottom:1px solid var(--border-color); font-size:14px;}
.stat-val{font-weight:700; color:var(--primary-dark);}
.btn-close{margin-top:22px; background:var(--primary); color:#fff; border:none; padding:11px 32px; border-radius:8px; cursor:pointer;}
.loading-box { text-align: center; padding: 40px; color: var(--text-muted); }
</style>
</head>
<body>

<div class="ambient-bg" aria-hidden="true">
  <div class="ambient-mountain"></div>
  <div class="ambient-trees"></div>
</div>

<div class="header">
  <h1>🌱 115年度高級中等以下學校及幼兒園教師資格考試</h1>
  <p>類科：國民小學 | 科目：數學能力測驗練功房</p>
</div>

<div class="sticky-bar">
  <div class="timer-label">⏱ 剩餘時間</div>
  <div id="timer">80:00</div>
  <div class="answered-label">已作答 <span id="ans-count">0</span> / <span id="total-count">0</span> 題</div>
</div>

<div class="container">
<div class="card">
  <h2>📋 應試基本資料</h2>
  <div class="form-row">
    <div class="form-group">
      <label for="sName">姓名</label>
      <input type="text" id="sName" placeholder="請輸入您的姓名">
    </div>
    <div class="form-group">
      <label for="sId">學號 / 准考證號</label>
      <input type="text" id="sId" placeholder="請輸入您的學號">
    </div>
  </div>
</div>

<div class="instructions">
  <strong>🌿 作答小叮嚀：</strong>深呼吸，保持輕鬆的心情。完成作答後點擊下方按鈕即可計算成績並同步至雲端記錄！
</div>

<div id="quiz-container">
  <div class="card loading-box">正在從雲端題庫載入試題，請稍候...</div>
</div>

<div class="submit-area" id="submit-area-wrap" style="display:none;">
  <button class="btn-submit" id="submitBtn" onclick="submitQuiz()">交卷看成績與分析</button>
</div>
</div>

<div class="modal-bg" id="resultModal">
  <div class="modal">
    <div class="score-ring">
      <div class="snum" id="scoreNum">0</div>
      <div class="stot">/ 100 分</div>
    </div>
    <h2 id="resultTitle">測驗完成！</h2>
    <p class="sub" id="resultSub"></p>
    <div class="result-details" id="resultDetails"></div>
    <div style="margin-top:12px; font-size:13px; color:var(--text-muted); background:#f4f1ea; border-radius:8px; padding:10px;" id="sheetMsg">
      📡 正在傳送成績至雲端資料庫...
    </div>
    <button class="btn-close" onclick="closeModal()">確認並關閉</button>
  </div>
</div>

<script>
const urlParams = new URLSearchParams(window.location.search);
const quizMode = urlParams.get('mode') || 'year';
const quizVal = urlParams.get('val') || '115';
const quizLimit = urlParams.get('limit') || '10';

// ⚠️ 【請將下方引號內的網址，換成你剛剛部署好的 Google Apps Script 網址】
const GAS_API_URL = "https://script.google.com/macros/s/AKfycbxRgkjMYYuZntOeeQaTgzU_E9K5gc5KznLniaGgfyre5yeZK7vH_GKbA0t1RyW2O6R4OQ/exec";

let questionsData = [];
let userAnswers = {};
let timeLeft = 80 * 60;
let timerInterval = null;

window.addEventListener('DOMContentLoaded', () => { fetchQuizData(); });

function fetchQuizData() {
  const targetUrl = `${GAS_API_URL}?mode=${quizMode}&val=${quizVal}&limit=${quizLimit}`;
  fetch(targetUrl)
    .then(res => res.json())
    .then(data => {
      if (!data || data.length === 0) {
        document.getElementById('quiz-container').innerHTML = '<div class="card loading-box">找不到符合條件的試題！</div>';
        return;
      }
      questionsData = data;
      document.getElementById('total-count').textContent = questionsData.length;
      renderQuiz(questionsData);
      startTimer();
      document.getElementById('submit-area-wrap').style.display = 'block';
    })
    .catch(err => {
      console.error('載入失敗:', err);
      document.getElementById('quiz-container').innerHTML = '<div class="card loading-box">載入題庫發生錯誤，請檢查 GAS 網址。</div>';
    });
}

function renderQuiz(questions) {
  let html = `<div class="sec-header">數學能力測驗（共 ${questions.length} 題）</div>`;
  questions.forEach((q, index) => {
    const qNum = index + 1;
    html += `
      <div class="q-wrap">
        <div class="q-title">
          <span class="q-num">${qNum}</span>
          <span class="q-status" id="s${qNum}">未作答</span>
          ${q.stem || ''}
        </div>`;
    if (q.svg_code) html += `<div style="text-align:center; margin:12px 0;">${q.svg_code}</div>`;
    html += `<div class="options" data-qindex="${index}">`;
    ['A', 'B', 'C', 'D'].forEach(optKey => {
      const optVal = q['opt_' + optKey.toLowerCase()];
      if (optVal) {
        html += `
          <label class="opt">
            <input type="radio" name="q_${index}" value="${optKey}" onchange="handleSelect(${index}, '${optKey}')">
            <span>(${optKey}) ${optVal}</span>
          </label>`;
      }
    });
    html += `</div></div>`;
  });
  document.getElementById('quiz-container').innerHTML = html;
}

function handleSelect(qIndex, optKey) {
  userAnswers[qIndex] = optKey;
  const qNum = qIndex + 1;
  document.getElementById(`s${qNum}`).textContent = '已作答';
  document.getElementById(`s${qNum}`).className = 'q-status done';
  
  document.querySelectorAll(`.options[data-qindex="${qIndex}"] .opt`).forEach(label => {
    const radio = label.querySelector('input');
    if (radio.value === optKey) label.classList.add('selected');
    else label.classList.remove('selected');
  });
  document.getElementById('ans-count').textContent = Object.keys(userAnswers).length;
}

function startTimer() {
  timerInterval = setInterval(() => {
    timeLeft--;
    const m = Math.floor(timeLeft / 60), s = timeLeft % 60;
    const el = document.getElementById('timer');
    el.textContent = String(m).padStart(2,'0') + ':' + String(s).padStart(2,'0');
    if (timeLeft <= 0) { clearInterval(timerInterval); submitQuiz(true); }
  }, 1000);
}

function submitQuiz(isAuto = false) {
  const name = document.getElementById('sName').value.trim();
  const sid = document.getElementById('sId').value.trim();
  if (!isAuto && !name) { alert('請輸入您的姓名！'); return; }
  if (timerInterval) clearInterval(timerInterval);

  let correctCount = 0;
  const pointsPerQ = 100 / questionsData.length;
  questionsData.forEach((q, index) => {
    if (userAnswers[index] === q.answer) correctCount++;
  });
  const finalScore = Math.round((correctCount * pointsPerQ) * 100) / 100;

  document.getElementById('scoreNum').textContent = finalScore;
  document.getElementById('resultSub').textContent = `${name || '同學'} 的複習成果：`;
  document.getElementById('resultDetails').innerHTML = `
    <div class="stat-row"><span class="stat-label">作答題數</span><span class="stat-val">${Object.keys(userAnswers).length} / ${questionsData.length} 題</span></div>
    <div class="stat-row"><span class="stat-label">答對題數</span><span class="stat-val">${correctCount} 題</span></div>
    <div class="stat-row"><span class="stat-label">最終得分</span><span class="stat-val">${finalScore} 分</span></div>`;
  document.getElementById('resultModal').classList.add('show');

  fetch(GAS_API_URL, {
    method: 'POST',
    body: JSON.stringify({ studentName: name, studentId: sid, mode: quizMode, score: finalScore, totalCorrect: correctCount, details: userAnswers })
  })
  .then(res => res.json())
  .then(() => { document.getElementById('sheetMsg').textContent = '✅ 成績已成功同步至雲端資料庫！'; })
  .catch(() => { document.getElementById('sheetMsg').textContent = '⚠️ 雲端同步失敗，但成績已計算完成。'; });
}

function closeModal() { document.getElementById('resultModal').classList.remove('show'); }
</script>
</body>
</html>
