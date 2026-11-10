<div class="pet-avatar" id="avatar" onclick="tapPet()">🐘</div>

<div class="pet-name-container">
  <div class="pet-name" id="pet-name">Baby animal</div>
  <button class="btn-edit" onclick="renamePet()">✏️</button>
</div>
<div class="user-tag" id="current-player">ကစားသူ: စစ်ဆေးနေပါသည်...</div>

<div class="activity-box">
  <div class="activity-title">နောက်ဆုံး လှုပ်ရှားမှု အသိပေးချက်</div>
  <div id="latest-action">လတ်တလော လှုပ်ရှားမှု မရှိသေးပါ</div>
</div>

<div class="stats-group">
  <div class="stat-row">
    <div class="stat-header">
      <span>🍗 ဗိုက်ပြည့်မှု</span>
      <span id="txt-hunger">100%</span>
    </div>
    <div class="progress-track">
      <div class="progress-bar bar-hunger" id="bar-hunger" style="width: 100%;"></div>
    </div>
  </div>

  <div class="stat-row">
    <div class="stat-header">
      <span>🌱 ကြီးထွားမှု အဆင့် (EXP)</span>
      <span id="txt-exp">0 / 5</span>
    </div>
    <div class="progress-track">
      <div class="progress-bar bar-growth" id="bar-growth" style="width: 0%;"></div>
    </div>
  </div>
</div>

<div class="actions-grid">
  <button class="action-btn btn-feed" onclick="feedPet()">🍗 အစာကျွေးမည်</button>
  <button class="action-btn btn-play" onclick="playPet()">🎾 ကစားမည်</button>
</div>

<div class="status-panel">
  <div class="status-dot" id="dot"></div>
  <span id="status-text">ဆာဗာသို့ ချိတ်ဆက်နေပါသည်...</span>
</div>
