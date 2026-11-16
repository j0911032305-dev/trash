# trash
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <meta name="theme-color" content="#F59E0B" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
  <meta name="apple-mobile-web-app-title" content="丟垃圾大作戰" />
  <link rel="manifest" href="manifest.json" />
  <link rel="apple-touch-icon" href="icon-192.png" />
  <title>丟垃圾大作戰 - 長輩友善版</title>
  <style>
    :root {
      --bg-warm: #FFFBEB;
      --card-bg: #FFFFFF;
      --primary: #D97706;
      --primary-dark: #B45309;
      --success: #059669;
      --success-dark: #047857;
      --info: #2563EB;
      --info-dark: #1D4ED8;
      --text-main: #1E293B;
      --text-sub: #475569;
      --border: #FDE68A;
    }

    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
      font-family: "Noto Sans TC", "PingFang TC", "Microsoft JhengHei", sans-serif;
    }

    body {
      margin: 0;
      padding: 0;
      background-color: var(--bg-warm);
      color: var(--text-main);
      padding-bottom: 100px;
      user-select: none;
    }

    /* 頂部標題列 */
    header {
      background: linear-gradient(135deg, #F59E0B, #D97706);
      color: white;
      padding: 16px 18px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 4px 10px rgba(217, 119, 6, 0.25);
      position: sticky;
      top: 0;
      z-index: 50;
    }

    header h1 {
      margin: 0;
      font-size: 24px;
      font-weight: 900;
      letter-spacing: 1px;
    }

    .speak-btn {
      background: #FEF3C7;
      color: #92400E;
      border: 3px solid #FFFFFF;
      border-radius: 50px;
      padding: 10px 16px;
      font-size: 20px;
      font-weight: 800;
      cursor: pointer;
      box-shadow: 0 4px 0 #B45309;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .speak-btn:active {
      transform: translateY(3px);
      box-shadow: 0 1px 0 #B45309;
    }

    /* 安裝提示橫幅 */
    #installBanner {
      display: none;
      background: #EFF6FF;
      border-bottom: 3px solid #93C5FD;
      padding: 14px 16px;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
    }

    #installBanner span {
      font-size: 18px;
      font-weight: 700;
      color: #1E3A8A;
    }

    #installBtn {
      background: #2563EB;
      color: white;
      border: none;
      border-radius: 14px;
      padding: 10px 16px;
      font-size: 18px;
      font-weight: 800;
      white-space: nowrap;
      cursor: pointer;
    }

    .container {
      max-width: 540px;
      margin: 0 auto;
      padding: 16px;
    }

    /* 卡片樣式 */
    .card {
      background: var(--card-bg);
      border: 3px solid var(--border);
      border-radius: 24px;
      padding: 20px;
      margin-bottom: 18px;
      box-shadow: 0 6px 16px rgba(0, 0, 0, 0.06);
    }

    .date-badge {
      display: inline-block;
      background: #FEF3C7;
      color: #92400E;
      font-size: 20px;
      font-weight: 800;
      padding: 6px 16px;
      border-radius: 99px;
      margin-bottom: 12px;
    }

    /* 今日主角區 */
    .hero-box {
      text-align: center;
      padding: 10px 0;
    }

    .hero-label {
      font-size: 22px;
      color: var(--text-sub);
      font-weight: 700;
      margin-bottom: 8px;
    }

    .hero-avatar {
      font-size: 72px;
      line-height: 1.1;
      margin: 6px 0;
    }

    .hero-name {
      font-size: 38px;
      font-weight: 900;
      color: #B45309;
      margin: 4px 0;
    }

    .hero-title {
      display: inline-block;
      background: #DCFCE7;
      color: #166534;
      font-size: 20px;
      font-weight: 800;
      padding: 6px 16px;
      border-radius: 12px;
      margin-top: 6px;
    }

    /* 上次與下次資訊列 */
    .relay-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      margin-top: 16px;
    }

    .relay-item {
      background: #F8FAFC;
      border: 2px solid #E2E8F0;
      border-radius: 18px;
      padding: 14px;
      text-align: center;
    }

    .relay-tag {
      font-size: 18px;
      color: #64748B;
      font-weight: 700;
    }

    .relay-person {
      font-size: 24px;
      font-weight: 900;
      color: #0F172A;
      margin-top: 6px;
    }

    /* 超大操作按鈕 */
    .big-btn {
      width: 100%;
      min-height: 72px;
      border: none;
      border-radius: 20px;
      font-size: 25px;
      font-weight: 900;
      color: white;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      margin-bottom: 14px;
      transition: transform 0.1s;
    }

    .btn-complete {
      background: var(--success);
      box-shadow: 0 6px 0 var(--success-dark);
    }

    .btn-complete:active {
      transform: translateY(4px);
      box-shadow: 0 2px 0 var(--success-dark);
    }

    .btn-dispatch {
      background: var(--info);
      box-shadow: 0 6px 0 var(--info-dark);
    }

    .btn-dispatch:active {
      transform: translateY(4px);
      box-shadow: 0 2px 0 var(--info-dark);
    }

    /* 底部導覽列 */
    .bottom-nav {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      background: white;
      border-top: 3px solid #E2E8F0;
      display: flex;
      height: 82px;
      z-index: 50;
    }

    .nav-item {
      flex: 1;
      border: none;
      background: none;
      font-size: 20px;
      font-weight: 800;
      color: #64748B;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 4px;
      cursor: pointer;
    }

    .nav-item.active {
      color: #D97706;
      background: #FFFBEB;
    }

    /* 分頁切換 */
    .tab-page {
      display: none;
    }

    .tab-page.active {
      display: block;
    }

    /* 家人列表 */
    .member-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 14px;
      border: 2px solid #E2E8F0;
      border-radius: 18px;
      margin-bottom: 12px;
      background: #FFFFFF;
    }

    .member-info {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .member-name {
      font-size: 24px;
      font-weight: 900;
    }

    .member-score {
      font-size: 18px;
      color: #059669;
      font-weight: 700;
    }

    .small-action-btn {
      background: #FEF3C7;
      color: #92400E;
      border: 2px solid #F59E0B;
      border-radius: 14px;
      padding: 10px 14px;
      font-size: 18px;
      font-weight: 800;
      cursor: pointer;
    }

    .add-box {
      display: flex;
      gap: 10px;
      margin-top: 14px;
    }

    .add-box input {
      flex: 1;
      font-size: 22px;
      padding: 14px;
      border: 3px solid #CBD5E1;
      border-radius: 16px;
    }

    .add-box button {
      background: #D97706;
      color: white;
      border: none;
      border-radius: 16px;
      padding: 0 20px;
      font-size: 22px;
      font-weight: 800;
      cursor: pointer;
    }

    /* 任務捲軸彈窗 */
    .modal-overlay {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(15, 23, 42, 0.7);
      z-index: 100;
      align-items: center;
      justify-content: center;
      padding: 18px;
    }

    .modal-card {
      background: #FFFBEB;
      border: 4px solid #F59E0B;
      border-radius: 28px;
      padding: 24px;
      max-width: 480px;
      width: 100%;
      text-align: center;
    }

    .scroll-text {
      background: white;
      border: 2px dashed #D97706;
      border-radius: 18px;
      padding: 16px;
      font-size: 22px;
      line-height: 1.6;
      text-align: left;
      margin: 16px 0;
      color: #1E293B;
      font-weight: 700;
    }

    /* 紀錄列表 */
    .log-item {
      padding: 12px 0;
      border-bottom: 2px solid #F1F5F9;
      font-size: 20px;
      font-weight: 700;
    }

    canvas#confetti {
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 200;
    }
  </style>
</head>
<body>
  <canvas id="confetti"></canvas>

  <header>
    <h1>🗑️ 丟垃圾大作戰</h1>
    <button class="speak-btn" onclick="speakStatus()">🔊 唸給我聽</button>
  </header>

  <div id="installBanner">
    <span>📲 可把此 App 加到手機桌面！</span>
    <button id="installBtn">一鍵安裝</button>
  </div>

  <div class="container">
    <!-- 分頁 1：今日任務 -->
    <div id="tab-home" class="tab-page active">
      <div class="card">
        <div class="date-badge" id="todayDate">載入日期中...</div>
        <div class="hero-box">
          <div class="hero-label">🎯 今天輪到這位英雄出任務</div>
          <div class="hero-avatar" id="heroAvatar">👴</div>
          <div class="hero-name" id="heroName">阿公</div>
          <div class="hero-title" id="heroTitle">⭐ 環保新手 (0 分)</div>
        </div>

        <div class="relay-grid">
          <div class="relay-item">
            <div class="relay-tag">⬅️ 上次誰丟的</div>
            <div class="relay-person" id="lastPerson">尚無紀錄</div>
          </div>
          <div class="relay-item">
            <div class="relay-tag">➡️ 下次輪到誰</div>
            <div class="relay-person" id="nextPerson">阿嬤</div>
          </div>
        </div>
      </div>

      <button class="big-btn btn-complete" onclick="completeMission()">
        ✅ 我丟好垃圾了！(加 10 分)
      </button>

      <button class="big-btn btn-dispatch" onclick="openDispatchModal()">
        📣 派發任務給他 (傳 LINE)
      </button>

      <div class="card">
        <div style="font-size: 22px; font-weight: 900; margin-bottom: 10px;">📜 最近完成紀錄</div>
        <div id="historyList">
          <div class="log-item" style="color:#64748B;">還沒開始紀錄喔，快按下綠色按鈕吧！</div>
        </div>
      </div>
    </div>

    <!-- 分頁 2：家人管理 -->
    <div id="tab-family" class="tab-page">
      <div class="card">
        <div style="font-size: 24px; font-weight: 900; margin-bottom: 6px;">👨‍👩‍👧‍👦 輪值順序與積分榜</div>
        <div style="font-size: 18px; color: #475569; margin-bottom: 16px;">可隨時幫家人代班，或新增家庭成員</div>
        <div id="memberList"></div>

        <div class="add-box">
          <input type="text" id="newMemberName" placeholder="輸入家人名字 (如: 小明)" />
          <button onclick="addMember()">＋新增</button>
        </div>
      </div>

      <div class="card" style="background:#EFF6FF; border-color:#93C5FD;">
        <div style="font-size: 22px; font-weight: 900; color:#1E3A8A; margin-bottom: 8px;">📱 如何變成手機桌面 App？</div>
        <div style="font-size: 19px; line-height: 1.6; color:#1E40AF;">
          • <b>iPhone (Safari)</b>：點下方「分享」按鈕 ⬆️ → 選<b>「加入主畫面」</b>。<br/>
          • <b>Android (Chrome)</b>：點右上角「⋮」→ 選<b>「安裝應用程式」</b>或<b>「加到主畫面」</b>。
        </div>
      </div>
    </div>
  </div>

  <!-- 任務派發彈窗 -->
  <div class="modal-overlay" id="dispatchModal">
    <div class="modal-card">
      <div style="font-size: 28px; font-weight: 900; color: #B45309;">📜 緊急任務捲軸</div>
      <div class="scroll-text" id="missionText"></div>
      <button class="big-btn btn-complete" onclick="copyMission()">📋 複製文字 (貼給家人)</button>
      <button class="big-btn btn-dispatch" onclick="ringBell()">🔔 響鈴呼叫本人</button>
      <button class="small-action-btn" style="width:100%; font-size:22px; padding:14px;" onclick="closeDispatchModal()">關閉視窗</button>
    </div>
  </div>

  <!-- 底部導覽 -->
  <nav class="bottom-nav">
    <button class="nav-item active" id="nav-home" onclick="switchTab('home')">
      <span style="font-size:28px;">🏠</span>
      <span>今日任務</span>
    </button>
    <button class="nav-item" id="nav-family" onclick="switchTab('family')">
      <span style="font-size:28px;">👨‍👩‍👧‍👦</span>
      <span>家人與積分</span>
    </button>
  </nav>

  <script>
    const AVATARS = ["👴", "👵", "👨", "👩", "🧑", "👧", "👦"];
    const DEFAULT_STATE = {
      members: [
        { id: 1, name: "阿公", avatar: "👴", score: 20 },
        { id: 2, name: "阿嬤", avatar: "👵", score: 30 },
        { id: 3, name: "爸爸", avatar: "👨", score: 10 },
        { id: 4, name: "媽媽", avatar: "👩", score: 10 }
      ],
      currentIndex: 0,
      lastRecord: null,
      history: []
    };

    let state = JSON.parse(localStorage.getItem("trashHeroState")) || DEFAULT_STATE;

    function saveState() {
      localStorage.setItem("trashHeroState", JSON.stringify(state));
      render();
    }

    function getTitle(score) {
      if (score >= 100) return "👑 傳奇環保英雄";
      if (score >= 50) return "🏆 垃圾分類大師";
      if (score >= 20) return "🌟 環保小尖兵";
      return "🌱 環保新手";
    }

    function formatToday() {
      const days = ["日", "一", "二", "三", "四", "五", "六"];
      const now = new Date();
      return `${now.getMonth() + 1}月${now.getDate()}日 (星期${days[now.getDay()]})`;
    }

    function render() {
      document.getElementById("todayDate").innerText = "📅 " + formatToday();
      const total = state.members.length;
      if (total === 0) return;
      if (state.currentIndex >= total) state.currentIndex = 0;

      const current = state.members[state.currentIndex];
      const next = state.members[(state.currentIndex + 1) % total];

      document.getElementById("heroAvatar").innerText = current.avatar;
      document.getElementById("heroName").innerText = current.name;
      document.getElementById("heroTitle").innerText = `${getTitle(current.score)} (${current.score} 分)`;
      document.getElementById("lastPerson").innerText = state.lastRecord ? `${state.lastRecord.name} (${state.lastRecord.date})` : "尚無紀錄";
      document.getElementById("nextPerson").innerText = next.name;

      // 歷史紀錄
      const historyEl = document.getElementById("historyList");
      if (state.history.length === 0) {
        historyEl.innerHTML = `<div class="log-item" style="color:#64748B;">還沒開始紀錄喔，快按下綠色按鈕吧！</div>`;
      } else {
        historyEl.innerHTML = state.history.slice(0, 5).map(h =>
          `<div class="log-item">✅ <b>${h.name}</b> 完成了任務 <span style="color:#64748B; font-size:17px;">(${h.time})</span></div>`
        ).join("");
      }

      // 家人列表
      const memberListEl = document.getElementById("memberList");
      memberListEl.innerHTML = state.members.map((m, idx) => `
        <div class="member-row" style="${idx === state.currentIndex ? 'border-color:#F59E0B; background:#FFFBEB;' : ''}">
          <div class="member-info">
            <span style="font-size:40px;">${m.avatar}</span>
            <div>
              <div class="member-name">${m.name} ${idx === state.currentIndex ? '🚩' : ''}</div>
              <div class="member-score">${getTitle(m.score)} · ${m.score} 分</div>
            </div>
          </div>
          <div style="display:flex; gap:8px;">
            <button class="small-action-btn" onclick="setTurn(${idx})">👉 換他丟</button>
            ${state.members.length > 1 ? `<button class="small-action-btn" style="background:#FEE2E2; border-color:#EF4444; color:#991B1B;" onclick="removeMember(${idx})">刪</button>` : ''}
          </div>
        </div>
      `).join("");
    }

    function playVictorySound() {
      try {
        const ctx = new (window.AudioContext || window.webkitAudioContext)();
        const notes = [523.25, 659.25, 783.99, 1046.50];
        notes.forEach((freq, i) => {
          const osc = ctx.createOscillator();
          const gain = ctx.createGain();
          osc.type = "triangle";
          osc.frequency.setValueAtTime(freq, ctx.currentTime + i * 0.12);
          gain.gain.setValueAtTime(0.25, ctx.currentTime + i * 0.12);
          gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + i * 0.12 + 0.35);
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.start(ctx.currentTime + i * 0.12);
          osc.stop(ctx.currentTime + i * 0.12 + 0.35);
        });
      } catch (e) {}
    }

    function launchConfetti() {
      const canvas = document.getElementById("confetti");
      const ctx = canvas.getContext("2d");
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      const pieces = Array.from({ length: 90 }, () => ({
        x: Math.random() * canvas.width,
        y: Math.random() * -canvas.height,
        w: 12,
        h: 12,
        color: ["#F59E0B", "#10B981", "#3B82F6", "#EF4444", "#8B5CF6"][Math.floor(Math.random() * 5)],
        vy: 4 + Math.random() * 5,
        vx: -2 + Math.random() * 4
      }));
      let frames = 0;
      function draw() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        pieces.forEach(p => {
          p.x += p.vx;
          p.y += p.vy;
          ctx.fillStyle = p.color;
          ctx.fillRect(p.x, p.y, p.w, p.h);
        });
        frames++;
        if (frames < 110) requestAnimationFrame(draw);
        else ctx.clearRect(0, 0, canvas.width, canvas.height);
      }
      draw();
    }

    function speakText(text) {
      if ("speechSynthesis" in window) {
        window.speechSynthesis.cancel();
        const msg = new SpeechSynthesisUtterance(text);
        msg.lang = "zh-TW";
        msg.rate = 0.88;
        window.speechSynthesis.speak(msg);
      }
    }

    function speakStatus() {
      const current = state.members[state.currentIndex];
      const next = state.members[(state.currentIndex + 1) % state.members.length];
      const lastText = state.lastRecord ? `上次是${state.lastRecord.name}丟的。` : "";
      speakText(`今天是${formatToday()}。輪到${current.name}丟垃圾，${lastText}下次輪到${next.name}。`);
    }

    function completeMission() {
      const current = state.members[state.currentIndex];
      const now = new Date();
      const shortDate = `${now.getMonth() + 1}/${now.getDate()}`;
      const timeStr = `${shortDate} ${String(now.getHours()).padStart(2, "0")}:${String(now.getMinutes()).padStart(2, "0")}`;

      current.score += 10;
      state.lastRecord = { name: current.name, date: shortDate };
      state.history.unshift({ name: current.name, time: timeStr });
      state.currentIndex = (state.currentIndex + 1) % state.members.length;

      const nextHero = state.members[state.currentIndex];
      playVictorySound();
      launchConfetti();
      speakText(`太棒了！${current.name}完成任務加十分！下次輪到${nextHero.name}喔！`);
      saveState();
    }

    function openDispatchModal() {
      const current = state.members[state.currentIndex];
      const next = state.members[(state.currentIndex + 1) % state.members.length];
      const msg = `📣【丟垃圾英雄召集令】
📅 日期：${formatToday()}
🦸‍♂️ 今日值日生：${current.name}
🗑️ 任務內容：請幫忙把家裡的垃圾與資源回收拿去丟喔！完成可獲得 +10 積分！
➡️ 下一棒預告：${next.name}`;
      document.getElementById("missionText").innerText = msg;
      document.getElementById("dispatchModal").style.display = "flex";
    }

    function closeDispatchModal() {
      document.getElementById("dispatchModal").style.display = "none";
    }

    function copyMission() {
      const text = document.getElementById("missionText").innerText;
      navigator.clipboard.writeText(text).then(() => {
        alert("✅ 任務內容已複製！快去家庭 LINE 群組貼上吧！");
      }).catch(() => {
        alert("請長按上方文字複製喔！");
      });
    }

    function ringBell() {
      const current = state.members[state.currentIndex];
      playVictorySound();
      speakText(`叮咚叮咚！${current.name}，今天輪到你丟垃圾囉！`);
    }

    function setTurn(idx) {
      state.currentIndex = idx;
      saveState();
      switchTab("home");
    }

    function addMember() {
      const input = document.getElementById("newMemberName");
      const name = input.value.trim();
      if (!name) return;
      const avatar = AVATARS[state.members.length % AVATARS.length];
      state.members.push({ id: Date.now(), name, avatar, score: 0 });
      input.value = "";
      saveState();
    }

    function removeMember(idx) {
      if (confirm(`確定要移除「${state.members[idx].name}」嗎？`)) {
        state.members.splice(idx, 1);
        if (state.currentIndex >= state.members.length) state.currentIndex = 0;
        saveState();
      }
    }

    function switchTab(tab) {
      document.querySelectorAll(".tab-page").forEach(el => el.classList.remove("active"));
      document.querySelectorAll(".nav-item").forEach(el => el.classList.remove("active"));
      document.getElementById("tab-" + tab).classList.add("active");
      document.getElementById("nav-" + tab).classList.add("active");
    }

    // PWA Service Worker & 安裝提示
    if ("serviceWorker" in navigator) {
      navigator.serviceWorker.register("sw.js").catch(() => {});
    }

    let deferredPrompt;
    window.addEventListener("beforeinstallprompt", (e) => {
      e.preventDefault();
      deferredPrompt = e;
      const banner = document.getElementById("installBanner");
      banner.style.display = "flex";
      document.getElementById("installBtn").onclick = () => {
        deferredPrompt.prompt();
        deferredPrompt.userChoice.then(() => {
          banner.style.display = "none";
          deferredPrompt = null;
        });
      };
    });

    render();
  </script>
</body>
</html>  
