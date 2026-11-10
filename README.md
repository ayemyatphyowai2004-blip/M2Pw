<!DOCTYPE html>
<html lang="my">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>Our Shared Pet</title>
  
  <!-- Telegram WebApp SDK -->
  <script src="https://telegram.org/js/telegram-web-app.js"></script>
  
  <!-- Firebase SDKs -->
  <script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-database-compat.js"></script>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      user-select: none;
      -webkit-tap-highlight-color: transparent;
    }
    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
      background: #181926;
      color: #cad3f5;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      padding: 16px;
    }
    .game-card {
      background: #24273a;
      width: 100%;
      max-width: 380px;
      border-radius: 28px;
      padding: 20px;
      box-shadow: 0 12px 32px rgba(0,0,0,0.45);
      text-align: center;
      border: 1px solid #363a4f;
    }
    .header-info {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 12px;
    }
    .streak-badge {
      background: #f5a97f22;
      color: #f5a97f;
      border: 1px solid #f5a97f55;
      padding: 6px 14px;
      border-radius: 16px;
      font-size: 13px;
      font-weight: bold;
    }
    .level-badge {
      background: #c6a0f622;
      color: #c6a0f6;
      border: 1px solid #c6a0f655;
      padding: 6px 14px;
      border-radius: 16px;
      font-size: 13px;
      font-weight: bold;
    }
    .pet-avatar {
      font-size: 85px;
      margin: 12px 0;
      cursor: pointer;
      transition: transform 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
      display: inline-block;
    }
    .pet-avatar:active {
      transform: scale(1.18) rotate(5deg);
    }
    .pet-name-container {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      margin-bottom: 6px;
    }
    .pet-name {
      font-size: 22px;
      font-weight: bold;
      color: #8aadf4;
    }
    .btn-edit {
      background: #363a4f;
      border: 1px solid #494d64;
      color: #cad3f5;
      font-size: 13px;
      cursor: pointer;
      border-radius: 8px;
      padding: 3px 8px;
    }
    .user-tag {
      font-size: 12px;
      color: #a5adcb;
      margin-bottom: 14px;
    }

    /* Activity Box */
    .activity-box {
      background: #1e2030;
      border-radius: 14px;
      padding: 10px 14px;
      font-size: 12px;
      color: #b8c0e0;
      text-align: left;
      border-left: 4px solid #8aadf4;
      margin-bottom: 16px;
      min-height: 48px;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }
    .activity-title {
      font-size: 10px;
      color: #8087a2;
      margin-bottom: 3px;
      text-transform: uppercase;
      font-weight: bold;
      letter-spacing: 0.5px;
    }

    /* Stats Progress */
    .stats-group {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 18px;
    }
    .stat-row {
      display: flex;
      flex-direction: column;
      gap: 4px;
      text-align: left;
      font-size: 12px;
    }
    .stat-header {
      display: flex;
      justify-content: space-between;
      color: #a5adcb;
      font-weight: 500;
    }
    .progress-track {
      background: #363a4f;
      border-radius: 10px;
      height: 9px;
      width: 100%;
      overflow: hidden;
    }
    .progress-bar {
      height: 100%;
      border-radius: 10px;
      transition: width 0.3s ease;
    }
    .bar-hunger { background: #ed8796; }
    .bar-growth { background: #a6da95; }

    /* Action Buttons */
    .actions-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      margin-bottom: 16px;
    }
    button.action-btn {
      background: #363a4f;
      color: #cad3f5;
      border: 1px solid #494d64;
      padding: 12px;
      border-radius:
