<!doctype html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Daily Routine - Gia Hưng &amp; Uy Vũ</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@400;600;700;800;900&display=swap" rel="stylesheet">
  <script src="https://unpkg.com/lucide@latest"></script>
  <style>
    :root {
      --cream: #fbf5e9;
      --paper: #fffdf8;
      --ink: #263b52;
      --muted: #6d766f;
      --me: #314d6c;
      --me-soft: #e2edf5;
      --mo: #557744;
      --mo-soft: #edf2e4;
      --orange: #e59b61;
      --line: #e9d9bf;
      --green-done: #4f833f;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: "Nunito Sans", sans-serif;
      color: var(--ink);
      background-color: var(--cream);
      background-image: radial-gradient(rgba(119,94,58,0.08) 1px, transparent 1px);
      background-size: 10px 10px;
      min-height: 100vh;
      padding: 24px 16px 48px;
    }
    button, input { font: inherit; }
    button { cursor: pointer; border: none; }
    .routine-wrap { max-width: 880px; margin: 0 auto; }
    
    .paper-card {
      background: var(--paper);
      border: 1px solid var(--line);
      border-radius: 24px;
      box-shadow: 0 10px 24px rgba(79,61,35,0.06);
    }
    
    /* Hero */
    .hero {
      position: relative;
      overflow: hidden;
      padding: 32px 28px;
      margin-bottom: 20px;
      background: linear-gradient(135deg, #fffaf1 0%, #f6ecdb 100%);
    }
    .hero-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
      flex-wrap: wrap;
    }
    .hero-eyebrow {
      font-size: 0.82rem;
      font-weight: 800;
      letter-spacing: 0.08em;
      color: var(--orange);
      text-transform: uppercase;
      margin-bottom: 6px;
    }
    .hero-title {
      font-size: clamp(1.6rem, 4vw, 2rem);
      font-weight: 900;
      color: var(--ink);
      line-height: 1.25;
    }
    .hero-sub {
      color: var(--muted);
      margin-top: 6px;
      font-size: 1rem;
      font-weight: 600;
    }
    .date-pill {
      border: 1px dashed #c4a983;
      background: #fff9ed;
      border-radius: 999px;
      padding: 8px 16px;
      color: #6a573d;
      font-size: 0.88rem;
      font-weight: 800;
      white-space: nowrap;
    }

    /* Kid Switcher Tabs */
    .tabs {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      margin-bottom: 20px;
    }
    .kid-tab {
      min-height: 68px;
      border-radius: 20px;
      background: #fffaf1;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 12px;
      font-weight: 800;
      font-size: 1.15rem;
      color: #796a53;
      border: 2px solid transparent;
      transition: 0.2s all ease;
    }
    .kid-tab.active-me {
      background: var(--me-soft);
      border-color: var(--me);
      color: var(--me);
      box-shadow: 0 4px 14px rgba(49,77,108,0.12);
      transform: translateY(-2px);
    }
    .kid-tab.active-mo {
      background: var(--mo-soft);
      border-color: var(--mo);
      color: var(--mo);
      box-shadow: 0 4px 14px rgba(85,119,68,0.12);
      transform: translateY(-2px);
    }
    .avatar-dot {
      width: 36px;
      height: 36px;
      border-radius: 50%;
      display: grid;
      place-items: center;
      color: #fff;
    }

    /* Overall Progress Bar */
    .progress-card {
      padding: 20px 24px;
      margin-bottom: 24px;
    }
    .progress-head {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      margin-bottom: 12px;
    }
    .progress-title {
      font-size: 0.8rem;
      font-weight: 800;
      letter-spacing: 0.05em;
      text-transform: uppercase;
      color: #8c7657;
    }
    .progress-encouragement {
      font-size: 1.1rem;
      font-weight: 800;
      margin-top: 4px;
    }
    .progress-stat {
      font-size: 1.15rem;
      font-weight: 900;
    }
    .progress-track {
      height: 14px;
      background: #ece3d2;
      border-radius: 999px;
      overflow: hidden;
    }
    .progress-fill {
      height: 100%;
      width: 0%;
      border-radius: 999px;
      transition: width 0.4s ease, background 0.3s ease;
    }

    /* Sections */
    .routine-panel { display: none; }
    .routine-panel.active { display: block; }
    .routine-section {
      padding: 22px;
      margin-bottom: 22px;
    }
    .section-head {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 18px;
    }
    .section-meta {
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .section-icon {
      width: 44px;
      height: 44px;
      border-radius: 14px;
      display: grid;
      place-items: center;
    }
    .section-title {
      font-size: 1.25rem;
      font-weight: 800;
      color: var(--ink);
    }
    .section-desc {
      font-size: 0.85rem;
      color: var(--muted);
      font-weight: 600;
    }
    .section-counter {
      font-size: 0.95rem;
      font-weight: 800;
      color: #79664f;
      background: #f7eedf;
      padding: 4px 12px;
      border-radius: 999px;
    }

    /* Grid */
    .photo-strip {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 14px;
    }
    @media (max-width: 768px) {
      .photo-strip { grid-template-columns: repeat(3, 1fr); gap: 10px; }
    }
    @media (max-width: 520px) {
      .photo-strip { grid-template-columns: repeat(2, 1fr); gap: 10px; }
    }

    /* Card Frame */
    .routine-frame {
      position: relative;
      aspect-ratio: 1;
      border-radius: 18px;
      background: #f9f2e7;
      border: 2px solid var(--line);
      overflow: hidden;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      transition: transform 0.15s, border-color 0.2s, box-shadow 0.2s;
    }
    .routine-frame:hover {
      transform: translateY(-2px);
      border-color: #cbaf80;
      box-shadow: 0 6px 16px rgba(0,0,0,0.06);
    }
    .routine-frame.done {
      border-color: var(--green-done);
      background: #f1f7ed;
    }

    .frame-visual {
      position: absolute;
      inset: 0;
      overflow: hidden;
      background: #fdf8ee;
    }
    .frame-image {
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      user-select: none;
      pointer-events: none;
      display: none;
    }
    .routine-frame.has-image .frame-image { display: block; }
    
    .frame-placeholder {
      position: absolute;
      inset: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: #b7a389;
      gap: 6px;
      padding: 12px;
      text-align: center;
    }
    .routine-frame.has-image .frame-placeholder { display: none; }

    /* Label banner at bottom */
    .frame-label-banner {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      padding: 18px 8px 8px;
      background: linear-gradient(to top, rgba(20,28,38,0.85) 0%, rgba(20,28,38,0.5) 75%, transparent 100%);
      color: #fff;
      font-size: 0.8rem;
      font-weight: 800;
      text-align: center;
      line-height: 1.25;
      z-index: 4;
      text-shadow: 0 1px 3px rgba(0,0,0,0.5);
      pointer-events: none;
    }

    /* Actions */
    .frame-actions {
      position: absolute;
      top: 8px;
      left: 8px;
      z-index: 5;
      display: none;
      gap: 5px;
    }
    .routine-frame.has-image .frame-actions { display: flex; }
    .frame-btn {
      width: 28px;
      height: 28px;
      border-radius: 50%;
      background: rgba(38,59,82,0.85);
      color: #fff;
      display: grid;
      place-items: center;
      transition: background 0.15s;
    }
    .frame-btn:hover { background: rgba(38,59,82,1); }
    .frame-btn.delete:hover { background: #b13737; }

    /* Check Button */
    .frame-check {
      position: absolute;
      right: 8px;
      top: 8px;
      z-index: 6;
      width: 36px;
      height: 36px;
      border-radius: 50%;
      background: rgba(255,255,255,0.92);
      border: 2px solid #bba990;
      color: transparent;
      display: grid;
      place-items: center;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
      transition: all 0.2s ease;
    }
    .routine-frame.done .frame-check {
      background: var(--green-done);
      border-color: var(--green-done);
      color: #fff;
      transform: scale(1.05);
    }

    /* Completion chip */
    .completion-chip {
      display: none;
      margin-top: 14px;
      border-radius: 14px;
      padding: 10px 14px;
      background: #eef7e6;
      border: 1px solid #c7e2b6;
      color: #456930;
      font-weight: 800;
      font-size: 0.92rem;
      align-items: center;
      gap: 8px;
    }
    .completion-chip.show { display: flex; }

    /* Reset button */
    .reset-bar { text-align: center; margin-top: 12px; }
    .reset-btn {
      background: #fff8eb;
      border: 1px dashed #cbab7d;
      color: #7b5d38;
      border-radius: 999px;
      padding: 12px 24px;
      font-weight: 800;
      font-size: 0.95rem;
      transition: background 0.15s;
    }
    .reset-btn:hover { background: #faecd3; }

    /* Toast */
    .toast {
      position: fixed;
      top: 20px;
      left: 50%;
      transform: translate(-50%, -100px);
      background: #25394d;
      color: #fff;
      padding: 10px 22px;
      border-radius: 999px;
      font-weight: 800;
      font-size: 0.92rem;
      box-shadow: 0 8px 24px rgba(0,0,0,0.2);
      transition: transform 0.3s cubic-bezier(0.2, 0.8, 0.3, 1), opacity 0.3s;
      opacity: 0;
      z-index: 1000;
      pointer-events: none;
    }
    .toast.show {
      transform: translate(-50%, 0);
      opacity: 1;
    }

    /* Modal Backdrop */
    .modal-backdrop {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(22, 34, 46, 0.55);
      z-index: 900;
      place-items: center;
      padding: 16px;
    }
    .modal-backdrop.show { display: grid; }
    .modal-box {
      width: 100%;
      max-width: 440px;
      background: #fffefb;
      border-radius: 24px;
      padding: 26px;
      text-align: center;
      box-shadow: 0 16px 40px rgba(0,0,0,0.25);
    }
    .modal-btn-row {
      display: flex;
      gap: 10px;
      justify-content: center;
      margin-top: 20px;
    }
    .btn-action {
      border-radius: 14px;
      padding: 11px 20px;
      font-weight: 800;
      font-size: 0.95rem;
    }
    .btn-primary { background: #314d6c; color: #fff; }
    .btn-secondary { background: #f0e6d6; color: #625340; }

    /* Crop Dialog */
    .crop-modal-box {
      width: 100%;
      max-width: 580px;
      background: #fffefb;
      border-radius: 24px;
      padding: 24px;
    }
    .crop-stage {
      position: relative;
      width: 100%;
      aspect-ratio: 1;
      max-height: 360px;
      margin: 16px auto 0;
      overflow: hidden;
      border-radius: 18px;
      background: #f4ecde;
      border: 2px dashed #cdb898;
      cursor: grab;
      touch-action: none;
    }
    .crop-stage.dragging { cursor: grabbing; }
    .crop-grid {
      position: absolute;
      inset: 0;
      pointer-events: none;
      background-image: 
        linear-gradient(to right, rgba(255,255,255,0.7) 1px, transparent 1px),
        linear-gradient(to bottom, rgba(255,255,255,0.7) 1px, transparent 1px);
      background-size: 33.33% 33.33%;
    }
    .crop-controls {
      display: flex;
      gap: 10px;
      justify-content: center;
      margin-top: 14px;
    }
    .crop-btn {
      background: #fbf3e5;
      border: 1px solid #e1d3bd;
      color: #3b536b;
      padding: 8px 14px;
      border-radius: 10px;
      font-weight: 800;
      font-size: 0.88rem;
    }

    /* Fireworks */
    .routine-fireworks {
      position: absolute;
      inset: 0;
      pointer-events: none;
      overflow: hidden;
      z-index: 20;
    }
    .routine-firework {
      position: absolute;
      left: 50%;
      top: 50%;
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: var(--spark-color, #e59b61);
      box-shadow: 0 0 6px rgba(255,255,255,0.8);
      animation: pop 0.7s cubic-bezier(0.2, 0.8, 0.3, 1) forwards;
    }
    @keyframes pop {
      0% { transform: translate(-50%, -50%) rotate(var(--spark-angle)) translateY(0) scale(0.6); opacity: 1; }
      80% { transform: translate(-50%, -50%) rotate(var(--spark-angle)) translateY(-55px) scale(1); opacity: 0.9; }
      100% { transform: translate(-50%, -50%) rotate(var(--spark-angle)) translateY(-70px) scale(0.2); opacity: 0; }
    }
  </style>
</head>
<body>

  <div id="toast" class="toast" role="status"></div>

  <div class="routine-wrap">
    <!-- Header Hero -->
    <header class="hero paper-card">
      <div class="hero-inner">
        <div>
          <div class="hero-eyebrow">Daily Routine Trẻ Nhỏ</div>
          <h1 class="hero-title">Cùng nhau lớn lên mỗi ngày</h1>
          <p class="hero-sub">Tự giác hoàn thành từng việc nhỏ để xây dựng thói quen tốt!</p>
        </div>
        <div id="date-label" class="date-pill"></div>
      </div>
    </header>

    <!-- Switch Bé -->
    <nav class="tabs" role="tablist">
      <button id="tab-me" class="kid-tab active-me" type="button" role="tab" aria-selected="true">
        <span class="avatar-dot" style="background:#314d6c">🌟</span>
        <span>GIA HƯNG</span>
      </button>
      <button id="tab-mo" class="kid-tab" type="button" role="tab" aria-selected="false">
        <span class="avatar-dot" style="background:#557744">🌱</span>
        <span>UY VŨ</span>
      </button>
    </nav>

    <!-- Progress Card -->
    <section class="progress-card paper-card">
      <div class="progress-head">
        <div>
          <div class="progress-title">Tiến độ ngày hôm nay</div>
          <div id="encouragement" class="progress-encouragement"></div>
        </div>
        <div id="progress-stat" class="progress-stat">0/20 · 0%</div>
      </div>
      <div class="progress-track">
        <div id="progress-fill" class="progress-fill"></div>
      </div>
    </section>

    <!-- Panel Gia Hưng -->
    <div id="panel-me" class="routine-panel active">
      <!-- Morning -->
      <section class="routine-section paper-card">
        <div class="section-head">
          <div class="section-meta">
            <div class="section-icon" style="background:#e2edf5; color:#314d6c">
              <i data-lucide="sun"></i>
            </div>
            <div>
              <h2 class="section-title">Chu trình buổi sáng</h2>
              <p class="section-desc">Khởi đầu ngày mới năng động &amp; đúng giờ</p>
            </div>
          </div>
          <span id="me-morning-count" class="section-counter">0/12</span>
        </div>
        <div id="me-morning-strip" class="photo-strip"></div>
        <div id="me-morning-complete" class="completion-chip">
          <i data-lucide="award"></i> Buổi sáng của Gia Hưng đã hoàn thành xuất sắc!
        </div>
      </section>

      <!-- Evening -->
      <section class="routine-section paper-card">
        <div class="section-head">
          <div class="section-meta">
            <div class="section-icon" style="background:#e2edf5; color:#314d6c">
              <i data-lucide="moon"></i>
            </div>
            <div>
              <h2 class="section-title">Chu trình buổi tối</h2>
              <p class="section-desc">Thư giãn và sẵn sàng cho giấc ngủ say</p>
            </div>
          </div>
          <span id="me-evening-count" class="section-counter">0/8</span>
        </div>
        <div id="me-evening-strip" class="photo-strip"></div>
        <div id="me-evening-complete" class="completion-chip">
          <i data-lucide="award"></i> Chu trình buổi tối đã hoàn tất, chúc Gia Hưng ngủ thật ngoan!
        </div>
      </section>
    </div>

    <!-- Panel Uy Vũ -->
    <div id="panel-mo" class="routine-panel">
      <!-- Morning -->
      <section class="routine-section paper-card">
        <div class="section-head">
          <div class="section-meta">
            <div class="section-icon" style="background:#edf2e4; color:#557744">
              <i data-lucide="sun"></i>
            </div>
            <div>
              <h2 class="section-title">Chu trình buổi sáng</h2>
              <p class="section-desc">Khởi đầu ngày mới năng động &amp; đúng giờ</p>
            </div>
          </div>
          <span id="mo-morning-count" class="section-counter">0/12</span>
        </div>
        <div id="mo-morning-strip" class="photo-strip"></div>
        <div id="mo-morning-complete" class="completion-chip">
          <i data-lucide="award"></i> Buổi sáng của Uy Vũ đã hoàn thành xuất sắc!
        </div>
      </section>

      <!-- Evening -->
      <section class="routine-section paper-card">
        <div class="section-head">
          <div class="section-meta">
            <div class="section-icon" style="background:#edf2e4; color:#557744">
              <i data-lucide="moon"></i>
            </div>
            <div>
              <h2 class="section-title">Chu trình buổi tối</h2>
              <p class="section-desc">Thư giãn và sẵn sàng cho giấc ngủ say</p>
            </div>
          </div>
          <span id="mo-evening-count" class="section-counter">0/8</span>
        </div>
        <div id="mo-evening-strip" class="photo-strip"></div>
        <div id="mo-evening-complete" class="completion-chip">
          <i data-lucide="award"></i> Chu trình buổi tối đã hoàn tất, chúc Uy Vũ ngủ thật ngoan!
        </div>
      </section>
    </div>

    <!-- Reset Trigger -->
    <div class="reset-bar">
      <button id="reset-button" class="reset-btn" type="button">↻ Đặt lại tiến độ ngày mới</button>
    </div>
  </div>

  <!-- Confirm Reset Modal -->
  <div id="reset-modal" class="modal-backdrop" role="dialog" aria-modal="true">
    <div class="modal-box">
      <div style="font-size: 2.5rem; margin-bottom: 8px;">🌅</div>
      <h3 style="font-size: 1.3rem; font-weight: 800; color: #263b52;">Bắt đầu lại hôm nay?</h3>
      <p style="color: #6d766f; margin-top: 6px; font-size: 0.95rem;">
        Tiến độ đã đánh dấu của bé đang xem sẽ được làm mới để bắt đầu một ngày học tập, rèn luyện mới.
      </p>
      <div class="modal-btn-row">
        <button id="cancel-reset" class="btn-action btn-secondary" type="button">Chưa, để lại</button>
        <button id="confirm-reset" class="btn-action btn-primary" type="button">Đồng ý đặt lại</button>
      </div>
    </div>
  </div>

  <!-- Crop Modal -->
  <div id="crop-modal" class="modal-backdrop" role="dialog" aria-modal="true">
    <div class="crop-modal-box">
      <h3 style="font-size: 1.25rem; font-weight: 800; color: #263b52;">Căn chỉnh ảnh trong khung</h3>
      <p style="color: #6d766f; font-size: 0.9rem; margin-top: 4px;">Kéo hoặc phóng to để chọn góc ảnh đẹp nhất.</p>
      
      <div id="crop-stage" class="crop-stage">
        <img id="crop-image" class="frame-image" alt="">
        <div class="crop-grid"></div>
      </div>

      <div class="crop-controls">
        <button id="crop-zoom-out" class="crop-btn" type="button">− Thu nhỏ</button>
        <button id="crop-zoom-in" class="crop-btn" type="button">＋ Phóng to</button>
        <button id="crop-reset" class="crop-btn" type="button">Căn giữa</button>
      </div>

      <div class="modal-btn-row" style="margin-top: 18px;">
        <button id="crop-cancel" class="btn-action btn-secondary" type="button">Hủy bỏ</button>
        <button id="crop-confirm" class="btn-action btn-primary" type="button">Áp dụng ảnh</button>
      </div>
    </div>
  </div>

  <script>
    const STORAGE_KEY = "kids_daily_routine_storage_v1";

    const routines = {
      me: {
        name: "Gia Hưng",
        color: "#314d6c",
        morning: [
          "Thức dậy", "Dọn mền gối", "Đi vệ sinh", "Đánh răng",
          "Thay quần áo","Đeo kính","Lời yêu thương","Uống nước & vitamin",
          "Mang giày", "Mang khẩu trang", "Mặc áo khoác", "Đội nón",
        ],
        evening: [
          "Tắm sạch sẽ", "Dọn dẹp đồ chơi", "Đánh răng",
         "Soạn balo đi học", "Đọc sách", "Đi ngủ"
        ]
      },
      mo: {
        name: "Uy Vũ",
        color: "#557744",
        morning: [
          "Thức dậy", "Dọn mền gối", "Đi vệ sinh", "Đánh răng",
          "Thay quần áo", "Uống nước & vitamin",
          "Mang giày", "Mang áo khoác", "Mặc khẩu trang", "Đội nón"
        ],
        evening: [
          "Tắm sạch sẽ", "Dọn dẹp đồ chơi", "Đánh răng",
          "Soạn balo đi học", "Đọc sách", "Đi ngủ"
        ]
      }
    };

    let activeKid = "me";
    let appState = { completed: {}, images: {} };

    // Audio synthesizer for pleasant kid-friendly feedback
    const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    function playChime(success = false) {
      if (!audioCtx) return;
      if (audioCtx.state === 'suspended') audioCtx.resume();
      
      const osc = audioCtx.createOscillator();
      const gain = audioCtx.createGain();
      osc.connect(gain);
      gain.connect(audioCtx.destination);

      if (success) {
        // High playful chord
        osc.frequency.setValueAtTime(523.25, audioCtx.currentTime); // C5
        osc.frequency.exponentialRampToValueAtTime(783.99, audioCtx.currentTime + 0.15); // G5
        gain.gain.setValueAtTime(0.18, audioCtx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + 0.4);
        osc.start();
        osc.stop(audioCtx.currentTime + 0.45);
      } else {
        // Soft pop
        osc.frequency.setValueAtTime(320, audioCtx.currentTime);
        osc.frequency.exponentialRampToValueAtTime(220, audioCtx.currentTime + 0.08);
        gain.gain.setValueAtTime(0.12, audioCtx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + 0.1);
        osc.start();
        osc.stop(audioCtx.currentTime + 0.12);
      }
    }

    function createSlug(text) {
      return text.normalize("NFD").replace(/[\u0300-\u036f]/g, "").toLowerCase()
        .replace(/[^a-z0-9]+/g, "-").replace(/^-|-$/g, "");
    }

    function taskId(kid, section, label) {
      return `${kid}:${section}:${createSlug(label)}`;
    }

    function loadState() {
      try {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (raw) appState = JSON.parse(raw);
      } catch (e) {
        console.error("Local storage error:", e);
      }
      appState.completed = appState.completed || {};
      appState.images = appState.images || {};
    }

    function saveState() {
      try {
        localStorage.setItem(STORAGE_KEY, JSON.stringify(appState));
      } catch (e) {
        showToast("Bộ nhớ ảnh đầy, hãy chọn ảnh dung lượng nhỏ hơn.");
      }
    }

    function showToast(msg) {
      const toast = document.getElementById("toast");
      toast.textContent = msg;
      toast.classList.add("show");
      clearTimeout(window.toastTimer);
      window.toastTimer = setTimeout(() => toast.classList.remove("show"), 2000);
    }

    function triggerFireworks(container) {
      const wrapper = document.createElement("div");
      wrapper.className = "routine-fireworks";
      const colors = ["#e59b61", "#e7bd62", "#9cb47c", "#74845a", "#d97d59", "#8aa8c0"];
      for (let i = 0; i < 16; i++) {
        const spark = document.createElement("span");
        spark.className = "routine-firework";
        spark.style.setProperty("--spark-angle", `${i * 22.5}deg`);
        spark.style.setProperty("--spark-color", colors[i % colors.length]);
        spark.style.animationDelay = `${(i % 3) * 30}ms`;
        wrapper.appendChild(spark);
      }
      container.appendChild(wrapper);
      setTimeout(() => wrapper.remove(), 800);
    }

    // Image Positioning & Rendering
    function paintImageInBox(imgEl, boxEl, imgData) {
      if (!imgData || !imgEl || !boxEl) return;
      const bW = boxEl.clientWidth, bH = boxEl.clientHeight;
      if (!bW || !bH || !imgData.width || !imgData.height) return;

      const scale = Math.max(bW / imgData.width, bH / imgData.height) * (imgData.zoom || 1);
      const w = imgData.width * scale;
      const h = imgData.height * scale;
      const maxX = Math.max(0, (w - bW) / 2);
      const maxY = Math.max(0, (h - bH) / 2);

      imgEl.style.width = `${w}px`;
      imgEl.style.height = `${h}px`;
      imgEl.style.marginLeft = `${(imgData.panX || 0) * maxX}px`;
      imgEl.style.marginTop = `${(imgData.panY || 0) * maxY}px`;
      imgEl.style.display = "block";
    }

    function applyCardImage(frame, imgData) {
      const img = frame.querySelector(".frame-image");
      if (!imgData) {
        frame.classList.remove("has-image");
        img.removeAttribute("src");
        img.style.display = "none";
        return;
      }
      frame.classList.add("has-image");
      img.onload = () => paintImageInBox(img, frame, imgData);
      img.src = imgData.source;
      if (img.complete) paintImageInBox(img, frame, imgData);
    }

    // Build each routine frame
    function createRoutineCard(kid, section, label) {
      const id = taskId(kid, section, label);
      const isDone = Boolean(appState.completed[id]);
      const card = document.createElement("div");
      card.className = `routine-frame ${isDone ? "done" : ""}`;
      card.dataset.id = id;

      card.innerHTML = `
        <div class="frame-visual">
          <img class="frame-image" alt="" draggable="false">
          <div class="frame-placeholder">
            <i data-lucide="camera" style="width: 28px; height: 28px;"></i>
            <span style="font-size: 0.75rem; font-weight: 700;">Thêm ảnh</span>
          </div>
        </div>

        <div class="frame-actions">
          <button class="frame-btn crop" title="Cắt ảnh" type="button"><i data-lucide="crop" style="width: 15px; height: 15px;"></i></button>
          <button class="frame-btn delete" title="Xóa ảnh" type="button"><i data-lucide="trash-2" style="width: 15px; height: 15px;"></i></button>
        </div>

        <button class="frame-check" type="button" aria-label="Hoàn thành">
          <i data-lucide="check" style="width: 20px; height: 20px;"></i>
        </button>

        <div class="frame-label-banner">${label}</div>
        <input type="file" accept="image/*" style="display:none;" class="file-input">
      `;

      const fileInput = card.querySelector(".file-input");
      const visual = card.querySelector(".frame-visual");

      visual.addEventListener("click", () => {
        if (appState.images[id]) {
          openCropModal(id);
        } else {
          fileInput.click();
        }
      });

      fileInput.addEventListener("change", (e) => {
        const file = e.target.files[0];
        if (!file) return;
        const reader = new FileReader();
        reader.onload = (evt) => {
          const probe = new Image();
          probe.onload = () => {
            // Compress down to maximum 1000px dimension
            const maxDim = 1000;
            const factor = Math.min(1, maxDim / Math.max(probe.width, probe.height));
            const canvas = document.createElement("canvas");
            canvas.width = probe.width * factor;
            canvas.height = probe.height * factor;
            const ctx = canvas.getContext("2d");
            ctx.drawImage(probe, 0, 0, canvas.width, canvas.height);
            const dataUrl = canvas.toDataURL("image/jpeg", 0.82);

            appState.images[id] = {
              source: dataUrl,
              width: canvas.width,
              height: canvas.height,
              zoom: 1,
              panX: 0,
              panY: 0
            };
            saveState();
            applyCardImage(card, appState.images[id]);
            showToast("Đã thêm ảnh! Bấm vào để chỉnh khung.");
          };
          probe.src = evt.target.result;
        };
        reader.readAsDataURL(file);
      });

      card.querySelector(".crop").addEventListener("click", (e) => {
        e.stopPropagation();
        openCropModal(id);
      });

      card.querySelector(".delete").addEventListener("click", (e) => {
        e.stopPropagation();
        delete appState.images[id];
        saveState();
        applyCardImage(card, null);
        showToast("Đã xóa ảnh.");
      });

      card.querySelector(".frame-check").addEventListener("click", (e) => {
        e.stopPropagation();
        appState.completed[id] = !appState.completed[id];
        saveState();
        
        if (appState.completed[id]) {
          card.classList.add("done");
          triggerFireworks(card);
          playChime(true);
        } else {
          card.classList.remove("done");
          playChime(false);
        }
        updateAllStats();
      });

      applyCardImage(card, appState.images[id]);
      return card;
    }

    // Render Section Routine Cards
    function renderKidSections(kid) {
      ["morning", "evening"].forEach((period) => {
        const container = document.getElementById(`${kid}-${period}-strip`);
        container.innerHTML = "";
        routines[kid][period].forEach((task) => {
          container.appendChild(createRoutineCard(kid, period, task));
        });
      });
      lucide.createIcons();
    }

    // Calculate Counts & Progress
    function updateAllStats() {
      const kid = activeKid;
      const data = routines[kid];
      let morningDone = 0, eveningDone = 0;

      data.morning.forEach(t => {
        if (appState.completed[taskId(kid, "morning", t)]) morningDone++;
      });
      data.evening.forEach(t => {
        if (appState.completed[taskId(kid, "evening", t)]) eveningDone++;
      });

      const morningTotal = data.morning.length;
      const eveningTotal = data.evening.length;
      const totalDone = morningDone + eveningDone;
      const grandTotal = morningTotal + eveningTotal;
      const percent = Math.round((totalDone / grandTotal) * 100);

      document.getElementById(`${kid}-morning-count`).textContent = `${morningDone}/${morningTotal}`;
      document.getElementById(`${kid}-evening-count`).textContent = `${eveningDone}/${eveningTotal}`;
      document.getElementById(`${kid}-morning-complete`).classList.toggle("show", morningDone === morningTotal);
      document.getElementById(`${kid}-evening-complete`).classList.toggle("show", eveningDone === eveningTotal);

      document.getElementById("progress-stat").textContent = `${totalDone}/${grandTotal} · ${percent}%`;
      const fill = document.getElementById("progress-fill");
      fill.style.width = `${percent}%`;
      fill.style.background = data.color;

      const praise = document.getElementById("encouragement");
      praise.style.color = data.color;
      if (percent === 100) {
        praise.textContent = `🎉 Hoan hô ${data.name}! Hôm nay con hoàn thành tất cả!`;
      } else if (percent >= 50) {
        praise.textContent = `💪 Giỏi lắm ${data.name}, đã hơn một nửa rồi!`;
      } else {
        praise.textContent = `🌱 Cùng bắt đầu ngày mới thật vui nhé ${data.name}!`;
      }
    }

    function selectKid(kid) {
      activeKid = kid;
      const isMe = kid === "me";
      document.getElementById("tab-me").classList.toggle("active-me", isMe);
      document.getElementById("tab-me").setAttribute("aria-selected", isMe);
      document.getElementById("tab-mo").classList.toggle("active-mo", !isMe);
      document.getElementById("tab-mo").setAttribute("aria-selected", !isMe);

      document.getElementById("panel-me").classList.toggle("active", isMe);
      document.getElementById("panel-mo").classList.toggle("active", !isMe);

      updateAllStats();
    }

    // Crop Modal Logic
    let currentCropId = null;
    let cropDraft = null;
    let isDragging = false;
    let startPoint = null;

    const cropModal = document.getElementById("crop-modal");
    const cropStage = document.getElementById("crop-stage");
    const cropImg = document.getElementById("crop-image");

    function renderCropDraft() {
      if (!cropDraft) return;
      paintImageInBox(cropImg, cropStage, cropDraft);
    }

    function openCropModal(id) {
      const imgData = appState.images[id];
      if (!imgData) return;
      currentCropId = id;
      cropDraft = { ...imgData };
      cropImg.src = cropDraft.source;
      cropImg.onload = () => {
        cropModal.classList.add("show");
        renderCropDraft();
      };
    }

    function closeCropModal() {
      cropModal.classList.remove("show");
      currentCropId = null;
      cropDraft = null;
    }

    cropStage.addEventListener("pointerdown", (e) => {
      if (!cropDraft) return;
      isDragging = true;
      startPoint = { x: e.clientX, y: e.clientY };
      cropStage.classList.add("dragging");
      cropStage.setPointerCapture(e.pointerId);
    });

    cropStage.addEventListener("pointermove", (e) => {
      if (!isDragging || !cropDraft) return;
      const dx = e.clientX - startPoint.x;
      const dy = e.clientY - startPoint.y;
      startPoint = { x: e.clientX, y: e.clientY };

      const bW = cropStage.clientWidth, bH = cropStage.clientHeight;
      const scale = Math.max(bW / cropDraft.width, bH / cropDraft.height) * (cropDraft.zoom || 1);
      const maxX = Math.max(1, ((cropDraft.width * scale) - bW) / 2);
      const maxY = Math.max(1, ((cropDraft.height * scale) - bH) / 2);

      cropDraft.panX = Math.max(-1, Math.min(1, (cropDraft.panX || 0) + (dx / maxX)));
      cropDraft.panY = Math.max(-1, Math.min(1, (cropDraft.panY || 0) + (dy / maxY)));
      renderCropDraft();
    });

    const stopDrag = () => {
      isDragging = false;
      cropStage.classList.remove("dragging");
    };
    ["pointerup", "pointercancel"].forEach(evt => cropStage.addEventListener(evt, stopDrag));

    document.getElementById("crop-zoom-in").onclick = () => {
      if (!cropDraft) return;
      cropDraft.zoom = Math.min(3.5, (cropDraft.zoom || 1) + 0.2);
      renderCropDraft();
    };
    document.getElementById("crop-zoom-out").onclick = () => {
      if (!cropDraft) return;
      cropDraft.zoom = Math.max(1, (cropDraft.zoom || 1) - 0.2);
      renderCropDraft();
    };
    document.getElementById("crop-reset").onclick = () => {
      if (!cropDraft) return;
      cropDraft.zoom = 1;
      cropDraft.panX = 0;
      cropDraft.panY = 0;
      renderCropDraft();
    };
    document.getElementById("crop-cancel").onclick = closeCropModal;
    document.getElementById("crop-confirm").onclick = () => {
      if (!currentCropId || !cropDraft) return;
      appState.images[currentCropId] = { ...cropDraft };
      saveState();
      const card = document.querySelector(`[data-id="${CSS.escape(currentCropId)}"]`);
      if (card) applyCardImage(card, appState.images[currentCropId]);
      closeCropModal();
      showToast("Đã lưu vị trí ảnh.");
    };

    // Reset Modal
    const resetModal = document.getElementById("reset-modal");
    document.getElementById("reset-button").onclick = () => resetModal.classList.add("show");
    document.getElementById("cancel-reset").onclick = () => resetModal.classList.remove("show");
    document.getElementById("confirm-reset").onclick = () => {
      const prefix = `${activeKid}:`;
      Object.keys(appState.completed).forEach(key => {
        if (key.startsWith(prefix)) delete appState.completed[key];
      });
      saveState();
      renderKidSections(activeKid);
      updateAllStats();
      resetModal.classList.remove("show");
      showToast(`Đã làm mới ngày hôm nay của ${routines[activeKid].name}!`);
    };

    // Tabs Listener
    document.getElementById("tab-me").onclick = () => selectKid("me");
    document.getElementById("tab-mo").onclick = () => selectKid("mo");

    // Init App
    document.getElementById("date-label").textContent = new Intl.DateTimeFormat("vi-VN", {
      weekday: "long",
      day: "numeric",
      month: "long"
    }).format(new Date());

    loadState();
    renderKidSections("me");
    renderKidSections("mo");
    selectKid("me");
  </script>
</body>
</html>
