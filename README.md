UNDIPOLL
<!doctype html>
<html lang="ms" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sistem Undian Sekolah</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      box-sizing: border-box;
    }
    
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
    
    * {
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    }
    
    .custom-container {
      background: #000000;
      min-height: 100%;
    }
    
    .card {
      background: #1a1a1a;
      border-radius: 20px;
      padding: 24px;
      margin-bottom: 16px;
      border: 1px solid #2a2a2a;
    }
    
    .btn-primary {
      background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
      color: #000000;
      font-weight: 600;
      padding: 16px 32px;
      border-radius: 12px;
      border: none;
      width: 100%;
      font-size: 16px;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    
    .btn-primary:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 20px rgba(255, 215, 0, 0.3);
    }
    
    .btn-primary:disabled {
      opacity: 0.5;
      cursor: not-allowed;
      transform: none;
    }
    
    .btn-secondary {
      background: #2a2a2a;
      color: #ffffff;
      font-weight: 500;
      padding: 16px 32px;
      border-radius: 12px;
      border: 1px solid #3a3a3a;
      width: 100%;
      font-size: 16px;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    
    .btn-secondary:hover {
      background: #3a3a3a;
    }
    
    .btn-candidate {
      background: #1a1a1a;
      color: #ffffff;
      padding: 20px;
      border-radius: 12px;
      border: 2px solid #2a2a2a;
      width: 100%;
      text-align: left;
      font-size: 16px;
      cursor: pointer;
      transition: all 0.3s ease;
      margin-bottom: 12px;
    }
    
    .btn-candidate:hover {
      border-color: #FFD700;
      background: #2a2a2a;
    }
    
    .input-field {
      background: #1a1a1a;
      border: 2px solid #2a2a2a;
      color: #ffffff;
      padding: 16px;
      border-radius: 12px;
      width: 100%;
      font-size: 16px;
      transition: all 0.3s ease;
    }
    
    .input-field:focus {
      outline: none;
      border-color: #FFD700;
    }
    
    .badge {
      display: inline-block;
      padding: 6px 12px;
      border-radius: 8px;
      font-size: 12px;
      font-weight: 600;
    }
    
    .badge-private {
      background: #8B0000;
      color: #ffffff;
    }
    
    .badge-public {
      background: #FFD700;
      color: #000000;
    }
    
    .badge-draft {
      background: #696969;
      color: #ffffff;
    }
    
    .badge-open {
      background: #228B22;
      color: #ffffff;
    }
    
    .badge-closed {
      background: #696969;
      color: #ffffff;
    }
    
    .countdown {
      color: #FF4444;
      font-size: 24px;
      font-weight: 700;
    }
    
    .toast {
      position: fixed;
      bottom: 24px;
      left: 50%;
      transform: translateX(-50%);
      padding: 16px 24px;
      border-radius: 12px;
      color: #ffffff;
      font-weight: 500;
      z-index: 1000;
      opacity: 0;
      transition: opacity 0.3s ease;
      max-width: 90%;
    }
    
    .toast.show {
      opacity: 1;
    }
    
    .toast-success {
      background: linear-gradient(135deg, #228B22 0%, #32CD32 100%);
    }
    
    .toast-error {
      background: linear-gradient(135deg, #8B0000 0%, #FF4444 100%);
    }
    
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(0, 0, 0, 0.8);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 999;
      padding: 20px;
    }
    
    .modal-content {
      background: #1a1a1a;
      border-radius: 20px;
      padding: 32px;
      max-width: 500px;
      width: 100%;
      max-height: 90vh;
      overflow-y: auto;
    }
    
    .code-input {
      display: flex;
      justify-content: center;
      gap: 8px;
      margin: 24px 0;
    }
    
    .code-digit {
      width: 48px;
      height: 56px;
      background: #1a1a1a;
      border: 2px solid #2a2a2a;
      border-radius: 12px;
      color: #FFD700;
      font-size: 24px;
      font-weight: 700;
      text-align: center;
      transition: all 0.3s ease;
    }
    
    .code-digit:focus {
      outline: none;
      border-color: #FFD700;
    }
    
    .ic-digit {
      width: 48px;
      height: 56px;
      background: #1a1a1a;
      border: 2px solid #2a2a2a;
      border-radius: 12px;
      color: #FFD700;
      font-size: 24px;
      font-weight: 700;
      text-align: center;
      letter-spacing: 8px;
      transition: all 0.3s ease;
    }
    
    .ic-digit:focus {
      outline: none;
      border-color: #FFD700;
    }
    
    .top-candidates {
      margin-top: 24px;
    }
    
    .candidate-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 16px;
      background: #1a1a1a;
      border-radius: 12px;
      margin-bottom: 12px;
      border-left: 4px solid #FFD700;
    }
    
    .candidate-rank {
      font-size: 24px;
      font-weight: 700;
      color: #FFD700;
      width: 40px;
    }
    
    .candidate-info {
      flex: 1;
      margin: 0 16px;
    }
    
    .candidate-votes {
      font-size: 20px;
      font-weight: 700;
      color: #FFD700;
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
 </head>
 <body class="h-full">
  <div class="custom-container h-full w-full">
   <div style="max-width: 600px; margin: 0 auto; padding: 20px;"><!-- Header -->
    <div style="text-align: center; margin-bottom: 32px; padding-top: 20px;"><img src="https://i.postimg.cc/yd2wK7fY/LOGO-SEKOLAH-TIADA-BG.png" alt="Logo Sekolah" style="width: 120px; height: 120px; margin: 0 auto 20px auto; display: block; object-fit: contain;" onerror="this.style.display='none';">
     <h1 id="app-title" style="color: #FFD700; font-size: 28px; font-weight: 700; margin-bottom: 8px;">Sistem Undian Sekolah</h1>
     <p id="school-name" style="color: #ffffff; font-size: 16px; opacity: 0.8;">SK PENDIDIKAN KHAS KUANTAN</p>
    </div><!-- Main Content -->
    <div id="main-content"></div><!-- Admin Button (Floating) --> <button onclick="showAdminLogin()" style="position: fixed; bottom: 24px; right: 24px; background: #2a2a2a; color: #FFD700; width: 56px; height: 56px; border-radius: 50%; border: 2px solid #FFD700; font-size: 20px; cursor: pointer; box-shadow: 0 4px 12px rgba(0,0,0,0.3);">⚙️</button>
   </div><!-- Toast Container -->
   <div id="toast-container"></div>
  </div>
  <script>
    const defaultConfig = {
      app_title: 'Sistem Undian Sekolah',
      school_name: 'SK PENDIDIKAN KHAS KUANTAN',
      primary_color: '#FFD700',
      background_color: '#000000',
      card_color: '#1a1a1a',
      text_color: '#ffffff'
    };
    
    let allData = [];
    let currentUser = null;
    let currentView = 'positions';
    let selectedPosition = null;
    let countdownIntervals = {};

    // 1. TAMPAL URL GOOGLE SCRIPT ANDA DI SINI
    const SCRIPT_URL = "https://script.google.com/macros/s/AKfycby7jeqiwxh0TxAqPs6pVqA_qPFBb7x0FvNZ75jGvMgarZ3gaR9r62_5AeolcdS-ljYWvw/exec";

    // 2. FUNGSI AMBIL DATA DARI GOOGLE SHEETS
    async function fetchData() {
        const tables = ['positions', 'members', 'votes'];
        let combinedData = [];
        for (const table of tables) {
            try {
                const res = await fetch(`${SCRIPT_URL}?table=${table}`);
                const json = await res.json();
                const dataWithType = json.map(item => ({ ...item, type: table.replace(/s$/, '') }));
                combinedData = [...combinedData, ...dataWithType];
            } catch (e) { console.log("Tiada data di table: " + table); }
        }
        allData = combinedData;
        renderCurrentView();
    }

    // 3. GANTI SDK CANVA KEPADA SDK GOOGLE SHEETS
    window.dataSdk = {
        create: async (payload) => {
            const table = payload.type + 's';
            await fetch(SCRIPT_URL, {
                method: 'POST',
                mode: 'no-cors', 
                body: JSON.stringify({ action: 'create', table: table, data: payload })
            });
            setTimeout(fetchData, 1500); // Tunggu 1.5 saat baru refresh
            return { isOk: true };
        },
        update: async (payload) => {
            const table = payload.type + 's';
            await fetch(SCRIPT_URL, {
                method: 'POST',
                mode: 'no-cors',
                body: JSON.stringify({ action: 'update', table: table, data: payload })
            });
            setTimeout(fetchData, 1500);
            return { isOk: true };
        },
        init: async () => {
            await fetchData();
            return { isOk: true };
        }
    };
    
    function renderCurrentView() {
      const container = document.getElementById('main-content');
      
      switch(currentView) {
        case 'positions':
          renderPositionsList(container);
          break;
        case 'enter-code':
          renderEnterCode(container);
          break;
        case 'select-candidate':
          renderSelectCandidate(container);
          break;
        case 'admin':
          renderAdminPanel(container);
          break;
        case 'create-position':
          renderCreatePosition(container);
          break;
        case 'results':
          renderResults(container);
          break;
        case 'import-members':
          renderImportMembers(container);
          break;
      }
    }
    
    function renderPositionsList(container) {
      const positions = allData.filter(d => d.type === 'position');
      const openPositions = positions.filter(p => p.status === 'OPEN');
      
      let html = '<div>';
      
      if (openPositions.length === 0) {
        html += `
          <div class="card" style="text-align: center; padding: 48px 24px;">
            <div style="font-size: 48px; margin-bottom: 16px;">🗳️</div>
            <h3 style="color: #ffffff; font-size: 20px; font-weight: 600; margin-bottom: 8px;">Tiada Undian Dibuka</h3>
            <p style="color: #ffffff; opacity: 0.6;">Tunggu admin membuka sesi undian</p>
          </div>
        `;
      } else {
        openPositions.forEach(position => {
          const timeLeft = getTimeLeft(position.endTime);
          const isExpired = timeLeft <= 0;
          
          html += `
            <div class="card">
              <div style="display: flex; justify-content: space-between; align-items: start; margin-bottom: 16px;">
                <div style="flex: 1;">
                  <h3 style="color: #ffffff; font-size: 20px; font-weight: 600; margin-bottom: 8px;">${position.positionName}</h3>
                  <div style="display: flex; gap: 8px; flex-wrap: wrap;">
                    <span class="badge ${position.mode === 'PRIVATE' ? 'badge-private' : 'badge-public'}">${position.mode}</span>
                    <span class="badge badge-open">DIBUKA</span>
                  </div>
                </div>
              </div>
              ${!isExpired ? `
                <div style="text-align: center; margin: 20px 0;">
                  <div class="countdown" id="countdown-${position.positionId}">${formatTime(timeLeft)}</div>
                  <p style="color: #ffffff; opacity: 0.6; font-size: 14px; margin-top: 4px;">Masa Berbaki</p>
                </div>
              ` : `
                <div style="text-align: center; margin: 20px 0; color: #FF4444; font-weight: 600;">
                  Masa Tamat
                </div>
              `}
              <button class="btn-primary" onclick="startVoting('${position.positionId}')" ${isExpired ? 'disabled' : ''}>
                ${isExpired ? 'Undian Ditutup' : 'Masuk Undian'}
              </button>
            </div>
          `;
        });
      }
      
      html += '</div>';
      container.innerHTML = html;
      
      openPositions.forEach(position => {
        startCountdown(position.positionId, position.endTime);
      });
    }
    
    function renderEnterCode(container) {
      const position = allData.find(d => d.positionId === selectedPosition);
      
      container.innerHTML = `
        <div>
          <button class="btn-secondary" onclick="backToPositions()" style="margin-bottom: 24px;">← Kembali</button>
          
          <div class="card">
            <h2 style="color: #ffffff; font-size: 24px; font-weight: 700; margin-bottom: 8px; text-align: center;">${position.positionName}</h2>
            <p style="color: #ffffff; opacity: 0.6; text-align: center; margin-bottom: 32px;">Masukkan kod undian</p>
            
            <div class="code-input">
              <input type="text" maxlength="1" class="code-digit" id="code-0" onkeyup="moveToNext(0)" oninput="this.value = this.value.replace(/[^0-9]/g, '')">
              <input type="text" maxlength="1" class="code-digit" id="code-1" onkeyup="moveToNext(1)" oninput="this.value = this.value.replace(/[^0-9]/g, '')">
              <input type="text" maxlength="1" class="code-digit" id="code-2" onkeyup="moveToNext(2)" oninput="this.value = this.value.replace(/[^0-9]/g, '')">
              <input type="text" maxlength="1" class="code-digit" id="code-3" onkeyup="moveToNext(3)" oninput="this.value = this.value.replace(/[^0-9]/g, '')">
              <input type="text" maxlength="1" class="code-digit" id="code-4" onkeyup="moveToNext(4)" oninput="this.value = this.value.replace(/[^0-9]/g, '')">
              <input type="text" maxlength="1" class="code-digit" id="code-5" onkeyup="moveToNext(5)" oninput="this.value = this.value.replace(/[^0-9]/g, '')">
            </div>
            
            <button class="btn-primary" onclick="verifyCode()" id="verify-btn">Sahkan Kod</button>
          </div>
        </div>
      `;
      
      document.getElementById('code-0').focus();
    }
    
    function renderSelectCandidate(container) {
      const position = allData.find(d => d.positionId === selectedPosition);
      const members = allData.filter(d => d.type === 'member');
      const votes = allData.filter(d => d.type === 'vote' && d.positionId === selectedPosition);
      
      const hasVoted = votes.some(v => v.voterId === currentUser);
      
      if (hasVoted) {
        container.innerHTML = `
          <div>
            <button class="btn-secondary" onclick="backToPositions()" style="margin-bottom: 24px;">← Kembali</button>
            
            <div class="card" style="text-align: center; padding: 48px 24px;">
              <div style="font-size: 64px; margin-bottom: 16px;">✅</div>
              <h3 style="color: #FFD700; font-size: 24px; font-weight: 700; margin-bottom: 8px;">Terima Kasih!</h3>
              <p style="color: #ffffff; opacity: 0.8; font-size: 16px;">Undi anda telah direkodkan</p>
            </div>
          </div>
        `;
        return;
      }
      
      let html = `
        <div>
          <button class="btn-secondary" onclick="backToPositions()" style="margin-bottom: 24px;">← Kembali</button>
          
          <div class="card">
            <h2 style="color: #ffffff; font-size: 24px; font-weight: 700; margin-bottom: 8px; text-align: center;">${position.positionName}</h2>
            <p style="color: #ffffff; opacity: 0.6; text-align: center; margin-bottom: 24px;">Pilih satu calon</p>
            
            <div id="candidates-list">
      `;
      
      members.forEach(member => {
        html += `
          <button class="btn-candidate" onclick="confirmVote('${member.idNumber}', '${member.name}')">
            <div style="font-weight: 600; margin-bottom: 4px;">${member.name}</div>
            <div style="opacity: 0.6; font-size: 14px;">No. KP: ${member.idNumber}</div>
          </button>
        `;
      });
      
      html += `
            </div>
          </div>
        </div>
      `;
      
      container.innerHTML = html;
    }
    
    function renderImportMembers(container) {
      const members = allData.filter(d => d.type === 'member');
      
      let html = `
        <div>
          <button class="btn-secondary" onclick="backToAdmin()" style="margin-bottom: 24px;">← Kembali</button>
          
          <div class="card">
            <h2 style="color: #FFD700; font-size: 24px; font-weight: 700; margin-bottom: 16px;">Import Ahli</h2>
            <p style="color: #ffffff; opacity: 0.8; margin-bottom: 24px;">Pilih fail CSV atau paste data manual</p>
            
            <!-- CSV File Upload -->
            <div style="margin-bottom: 24px; padding: 20px; background: #2a2a2a; border-radius: 12px; border: 2px dashed #FFD700;">
              <div style="text-align: center;">
                <div style="font-size: 48px; margin-bottom: 12px;">���</div>
                <label style="color: #FFD700; display: block; margin-bottom: 12px; font-weight: 600; font-size: 16px;">Upload Fail CSV</label>
                <input type="file" id="csv-file" accept=".csv,.txt" onchange="handleCSVUpload(event)" style="display: none;">
                <button onclick="document.getElementById('csv-file').click()" class="btn-primary" style="max-width: 300px; margin: 0 auto;">
                  📤 Pilih Fail CSV
                </button>
                <p style="color: #ffffff; opacity: 0.6; font-size: 12px; margin-top: 12px;">Format: No. KP,Nama (tanpa header)</p>
              </div>
            </div>
            
            <div style="text-align: center; margin: 24px 0;">
              <span style="color: #ffffff; opacity: 0.4; font-weight: 600;">── ATAU ──</span>
            </div>
            
            <!-- Manual Paste -->
            <div style="background: #2a2a2a; padding: 16px; border-radius: 12px; margin-bottom: 16px;">
              <p style="color: #FFD700; font-size: 14px; font-weight: 600; margin-bottom: 8px;">💡 Contoh Format:</p>
              <pre style="color: #ffffff; font-size: 12px; opacity: 0.8; white-space: pre-wrap; word-break: break-all;">850123-10-5678,Ahmad bin Ali
920315-08-4321,Siti binti Amin
780605-14-9876,Razak bin Omar</pre>
            </div>
            
            <form onsubmit="importMembers(event)">
              <div style="margin-bottom: 20px;">
                <label style="color: #ffffff; display: block; margin-bottom: 8px; font-weight: 500;">✏️ Paste Data Manual</label>
                <textarea id="import-data" class="input-field" rows="8" placeholder="No. KP,Nama&#10;850123-10-5678,Ahmad bin Ali&#10;920315-08-4321,Siti binti Amin" style="resize: vertical; font-family: monospace; font-size: 14px;"></textarea>
              </div>
              
              <button type="submit" class="btn-primary" id="import-btn" style="margin-bottom: 12px;">�� Import Data</button>
              <button type="button" class="btn-secondary" onclick="clearAllMembers()">🗑️ Padam Semua Ahli</button>
            </form>
          </div>
          
          <div style="margin-top: 24px;">
            <h3 style="color: #ffffff; font-size: 20px; font-weight: 600; margin-bottom: 16px;">📋 Senarai Ahli Semasa (${members.length})</h3>
      `;
      
      if (members.length === 0) {
        html += `
          <div class="card" style="text-align: center; padding: 32px 24px;">
            <p style="color: #ffffff; opacity: 0.6;">Tiada ahli dijumpai</p>
          </div>
        `;
      } else {
        members.forEach(member => {
          html += `
            <div class="card" style="padding: 16px;">
              <div style="display: flex; justify-content: space-between; align-items: center;">
                <div>
                  <div style="font-weight: 600; color: #ffffff; margin-bottom: 4px;">${member.name}</div>
                  <div style="opacity: 0.6; font-size: 14px; color: #ffffff;">No. KP: ${member.idNumber}</div>
                </div>
                <button onclick="deleteMember('${member.__backendId}')" style="background: #8B0000; color: #ffffff; padding: 8px 16px; border-radius: 8px; border: none; cursor: pointer; font-size: 14px;">Padam</button>
              </div>
            </div>
          `;
        });
      }
      
      html += `
          </div>
        </div>
      `;
      
      container.innerHTML = html;
    }
    
    function renderAdminPanel(container) {
      const positions = allData.filter(d => d.type === 'position');
      const members = allData.filter(d => d.type === 'member');
      const isSuperAdmin = currentUser === 'SUPER';
      
      let html = `
        <div>
          <button class="btn-secondary" onclick="logout()" style="margin-bottom: 24px;">← Keluar Admin</button>
          
          <div class="card">
            <h2 style="color: #FFD700; font-size: 24px; font-weight: 700; margin-bottom: 16px;">Panel Admin</h2>
            <p style="color: #ffffff; opacity: 0.6; margin-bottom: 24px;">
              ${isSuperAdmin ? '🌟 Super Admin' : '👤 Admin Biasa'}
            </p>
            
            <button class="btn-primary" onclick="showCreatePosition()" style="margin-bottom: 12px;">+ Cipta Jawatan Baru</button>
            <button class="btn-secondary" onclick="showImportMembers()" style="margin-bottom: 12px;">📥 Import Ahli (${members.length})</button>
            ${isSuperAdmin ? `<button class="btn-secondary" onclick="generatePDFReport()" style="background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%); color: #000000; font-weight: 600;">📊 Analisis & Print PDF</button>` : ''}
          </div>
          
          <div style="margin-top: 24px;">
            <h3 style="color: #ffffff; font-size: 20px; font-weight: 600; margin-bottom: 16px;">Senarai Jawatan</h3>
      `;
      
      if (positions.length === 0) {
        html += `
          <div class="card" style="text-align: center; padding: 32px 24px;">
            <p style="color: #ffffff; opacity: 0.6;">Tiada jawatan dijumpai</p>
          </div>
        `;
      } else {
        positions.forEach(position => {
          const votes = allData.filter(d => d.type === 'vote' && d.positionId === position.positionId);
          const timeLeft = getTimeLeft(position.endTime);
          
          html += `
            <div class="card">
              <div style="display: flex; justify-content: space-between; align-items: start; margin-bottom: 16px;">
                <div style="flex: 1;">
                  <h4 style="color: #ffffff; font-size: 18px; font-weight: 600; margin-bottom: 8px;">${position.positionName}</h4>
                  <div style="display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 8px;">
                    <span class="badge ${position.mode === 'PRIVATE' ? 'badge-private' : 'badge-public'}">${position.mode}</span>
                    <span class="badge ${position.status === 'OPEN' ? 'badge-open' : position.status === 'DRAFT' ? 'badge-draft' : 'badge-closed'}">${position.status}</span>
                  </div>
                  <p style="color: #ffffff; opacity: 0.6; font-size: 14px;">Kod: ${position.code}</p>
                  <p style="color: #ffffff; opacity: 0.6; font-size: 14px;">Durasi: ${position.durationMin} minit</p>
                  ${position.status !== 'DRAFT' ? `<p style="color: #ffffff; opacity: 0.6; font-size: 14px;">Undi: ${votes.length}</p>` : ''}
                  ${position.status === 'OPEN' && timeLeft > 0 ? `
                    <p style="color: #FF4444; font-size: 14px; margin-top: 8px;">⏱️ ${formatTime(timeLeft)}</p>
                  ` : ''}
                </div>
              </div>
              
              ${position.status === 'DRAFT' ? `
                <button class="btn-primary" onclick="showActivatePositionModal('${position.positionId}')">▶️ Buka Undian</button>
              ` : position.status === 'CLOSED' ? `
                <button class="btn-primary" onclick="openPosition('${position.positionId}')">Buka Semula</button>
              ` : `
                <button class="btn-secondary" onclick="closePosition('${position.positionId}')">Tutup Undian</button>
              `}
              
              ${isSuperAdmin && position.status !== 'DRAFT' ? `
                <button class="btn-secondary" onclick="showResults('${position.positionId}')" style="margin-top: 12px;">📊 Lihat Keputusan</button>
              ` : ''}
            </div>
          `;
        });
      }
      
      html += `
          </div>
        </div>
      `;
      
      container.innerHTML = html;
    }
    
    function renderCreatePosition(container) {
      container.innerHTML = `
        <div>
          <button class="btn-secondary" onclick="backToAdmin()" style="margin-bottom: 24px;">← Kembali</button>
          
          <div class="card">
            <h2 style="color: #FFD700; font-size: 24px; font-weight: 700; margin-bottom: 24px;">Cipta Jawatan Baru</h2>
            
            <form onsubmit="createPosition(event)">
              <div style="margin-bottom: 20px;">
                <label style="color: #ffffff; display: block; margin-bottom: 8px; font-weight: 500;">Nama Jawatan</label>
                <input type="text" id="position-name" class="input-field" placeholder="Contoh: Pengerusi" required>
              </div>
              
              <div style="margin-bottom: 20px;">
                <label style="color: #ffffff; display: block; margin-bottom: 8px; font-weight: 500;">Kod Unik (6 Digit)</label>
                <input type="text" id="position-code" class="input-field" placeholder="Contoh: 123456" maxlength="6" pattern="[0-9]{6}" required oninput="this.value = this.value.replace(/[^0-9]/g, '')">
              </div>
              
              <div style="margin-bottom: 20px;">
                <label style="color: #ffffff; display: block; margin-bottom: 8px; font-weight: 500;">Durasi (Minit)</label>
                <input type="number" id="position-duration" class="input-field" placeholder="10" min="1" required>
              </div>
              
              <div style="margin-bottom: 24px;">
                <label style="color: #ffffff; display: block; margin-bottom: 8px; font-weight: 500;">Mode Undian</label>
                <select id="position-mode" class="input-field" required>
                  <option value="PRIVATE">PRIVATE (Whitelist No. KP)</option>
                  <option value="UMUM">UMUM (Tanpa Whitelist)</option>
                </select>
              </div>
              
              <button type="submit" class="btn-primary" id="create-btn">Semak Maklumat</button>
            </form>
          </div>
        </div>
      `;
    }
    
    function renderResults(container) {
      const position = allData.find(d => d.positionId === selectedPosition);
      const votes = allData.filter(d => d.type === 'vote' && d.positionId === selectedPosition);
      
      const voteCounts = {};
      votes.forEach(vote => {
        voteCounts[vote.votedIdNumber] = (voteCounts[vote.votedIdNumber] || 0) + 1;
      });
      
      const sortedCandidates = Object.entries(voteCounts)
        .sort((a, b) => b[1] - a[1])
        .slice(0, 5);
      
      const members = allData.filter(d => d.type === 'member');
      
      let html = `
        <div>
          <button class="btn-secondary" onclick="backToAdmin()" style="margin-bottom: 24px;">← Kembali</button>
          
          <div class="card">
            <h2 style="color: #FFD700; font-size: 24px; font-weight: 700; margin-bottom: 8px; text-align: center;">${position.positionName}</h2>
            <p style="color: #ffffff; opacity: 0.6; text-align: center; margin-bottom: 8px;">Top 5 Calon</p>
            <p style="color: #ffffff; opacity: 0.8; text-align: center; margin-bottom: 24px;">Jumlah Undi: ${votes.length}</p>
            
            <div class="top-candidates">
      `;
      
      if (sortedCandidates.length === 0) {
        html += `
          <div style="text-align: center; padding: 32px; color: #ffffff; opacity: 0.6;">
            Tiada undi lagi
          </div>
        `;
      } else {
        sortedCandidates.forEach((candidate, index) => {
          const member = members.find(m => m.idNumber === candidate[0]);
          const name = member ? member.name : candidate[0];
          
          html += `
            <div class="candidate-item">
              <div class="candidate-rank">#${index + 1}</div>
              <div class="candidate-info">
                <div style="font-weight: 600; color: #ffffff; margin-bottom: 4px;">${name}</div>
                <div style="opacity: 0.6; font-size: 14px; color: #ffffff;">No. KP: ${candidate[0]}</div>
              </div>
              <div class="candidate-votes">${candidate[1]}</div>
            </div>
          `;
        });
      }
      
      html += `
            </div>
          </div>
        </div>
      `;
      
      container.innerHTML = html;
    }
    
    // Helper Functions
    function getTimeLeft(endTime) {
      return Math.max(0, Math.floor((endTime - Date.now()) / 1000));
    }
    
    function formatTime(seconds) {
      const mins = Math.floor(seconds / 60);
      const secs = seconds % 60;
      return `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
    }
    
    function startCountdown(positionId, endTime) {
      if (countdownIntervals[positionId]) {
        clearInterval(countdownIntervals[positionId]);
      }
      
      countdownIntervals[positionId] = setInterval(() => {
        const timeLeft = getTimeLeft(endTime);
        const element = document.getElementById(`countdown-${positionId}`);
        
        if (element) {
          element.textContent = formatTime(timeLeft);
        }
        
        if (timeLeft <= 0) {
          clearInterval(countdownIntervals[positionId]);
          delete countdownIntervals[positionId];
          
          const position = allData.find(d => d.positionId === positionId);
          if (position && position.status === 'OPEN') {
            closePositionAuto(positionId);
          }
        }
      }, 1000);
    }
    
    function showToast(message, type = 'success') {
      const toast = document.createElement('div');
      toast.className = `toast toast-${type} show`;
      toast.textContent = message;
      
      document.getElementById('toast-container').appendChild(toast);
      
      setTimeout(() => {
        toast.classList.remove('show');
        setTimeout(() => toast.remove(), 300);
      }, 3000);
    }
    
    // Navigation Functions
    function startVoting(positionId) {
      selectedPosition = positionId;
      currentView = 'enter-code';
      renderCurrentView();
    }
    
    function backToPositions() {
      currentView = 'positions';
      selectedPosition = null;
      currentUser = null;
      renderCurrentView();
    }
    
    function backToAdmin() {
      currentView = 'admin';
      selectedPosition = null;
      renderCurrentView();
    }
    
    function logout() {
      currentUser = null;
      currentView = 'positions';
      renderCurrentView();
    }
    
    function showCreatePosition() {
      currentView = 'create-position';
      renderCurrentView();
    }
    
    function showResults(positionId) {
      selectedPosition = positionId;
      currentView = 'results';
      renderCurrentView();
    }
    
    function showImportMembers() {
      currentView = 'import-members';
      renderCurrentView();
    }
    
    // Code Input Functions
    function moveToNext(index) {
      const current = document.getElementById(`code-${index}`);
      
      if (current.value.length === 1 && index < 5) {
        document.getElementById(`code-${index + 1}`).focus();
      } else if (index === 5 && current.value.length === 1) {
        verifyCode();
      }
    }
    
    function moveToNextIC(index) {
      const current = document.getElementById(`ic-${index}`);
      
      if (current.value.length === 1 && index < 3) {
        document.getElementById(`ic-${index + 1}`).focus();
      }
    }
    
    async function verifyCode() {
      const code = Array.from({length: 6}, (_, i) => 
        document.getElementById(`code-${i}`).value
      ).join('');
      
      if (code.length !== 6 || !/^\d{6}$/.test(code)) {
        showToast('Sila masukkan 6 digit nombor', 'error');
        return;
      }
      
      const position = allData.find(d => d.positionId === selectedPosition);
      
      if (!position) {
        showToast('Jawatan tidak dijumpai', 'error');
        return;
      }
      
      if (position.code !== code) {
        showToast('Kod tidak sah', 'error');
        return;
      }
      
      // Check if voting period has expired
      const timeLeft = getTimeLeft(position.endTime);
      if (timeLeft <= 0) {
        showToast('Masa undian telah tamat', 'error');
        backToPositions();
        return;
      }
      
      if (position.mode === 'UMUM') {
        currentUser = `PUBLIC-${Date.now()}`;
        currentView = 'select-candidate';
        renderCurrentView();
      } else {
        // Show IC input modal for PRIVATE mode
        showICInputModal();
      }
    }
    
    function showICInputModal() {
      const modal = document.createElement('div');
      modal.className = 'modal-overlay';
      modal.innerHTML = `
        <div class="modal-content">
          <h3 style="color: #FFD700; font-size: 24px; font-weight: 700; margin-bottom: 16px; text-align: center;">Pengesahan No. KP</h3>
          <p style="color: #ffffff; opacity: 0.8; text-align: center; margin-bottom: 24px;">Masukkan <strong>4 digit terakhir</strong> No. KP anda</p>
          
          <form onsubmit="verifyIC(event)">
            <div class="code-input" style="margin-bottom: 24px;">
              <input type="text" maxlength="1" class="ic-digit" id="ic-0" onkeyup="moveToNextIC(0)" oninput="this.value = this.value.replace(/[^0-9]/g, '')" style="letter-spacing: 0;">
              <input type="text" maxlength="1" class="ic-digit" id="ic-1" onkeyup="moveToNextIC(1)" oninput="this.value = this.value.replace(/[^0-9]/g, '')" style="letter-spacing: 0;">
              <input type="text" maxlength="1" class="ic-digit" id="ic-2" onkeyup="moveToNextIC(2)" oninput="this.value = this.value.replace(/[^0-9]/g, '')" style="letter-spacing: 0;">
              <input type="text" maxlength="1" class="ic-digit" id="ic-3" oninput="this.value = this.value.replace(/[^0-9]/g, '')" style="letter-spacing: 0;">
            </div>
            
            <div style="background: #2a2a2a; padding: 12px; border-radius: 8px; margin-bottom: 20px;">
              <p style="color: #ffffff; opacity: 0.7; font-size: 13px; text-align: center;">
                💡 Contoh: No. KP <strong>850123-10-5678</strong><br>
                Taip: <strong style="color: #FFD700;">5678</strong>
              </p>
            </div>
            
            <button type="submit" class="btn-primary" style="margin-bottom: 12px;">Sahkan</button>
            <button type="button" class="btn-secondary" onclick="this.closest('.modal-overlay').remove()">Batal</button>
          </form>
        </div>
      `;
      
      document.body.appendChild(modal);
      setTimeout(() => document.getElementById('ic-0').focus(), 100);
    }
    
    function verifyIC(event) {
      event.preventDefault();
      
      const last4Digits = Array.from({length: 4}, (_, i) => 
        document.getElementById(`ic-${i}`).value
      ).join('');
      
      if (last4Digits.length !== 4 || !/^\d{4}$/.test(last4Digits)) {
        showToast('Sila masukkan 4 digit nombor', 'error');
        return;
      }
      
      // Find member with matching last 4 digits
      const member = allData.find(d => 
        d.type === 'member' && d.idNumber && d.idNumber.slice(-4) === last4Digits
      );
      
      if (!member) {
        showToast('No. KP tidak dalam senarai', 'error');
        return;
      }
      
      currentUser = member.idNumber;
      document.querySelector('.modal-overlay')?.remove();
      currentView = 'select-candidate';
      renderCurrentView();
    }
    
    // Voting Functions
    function confirmVote(idNumber, name) {
      const confirmDiv = document.createElement('div');
      confirmDiv.className = 'modal-overlay';
      confirmDiv.innerHTML = `
        <div class="modal-content">
          <h3 style="color: #ffffff; font-size: 20px; font-weight: 600; margin-bottom: 16px; text-align: center;">Sahkan Pilihan</h3>
          <p style="color: #ffffff; opacity: 0.8; text-align: center; margin-bottom: 24px;">Anda memilih:</p>
          <div style="background: #2a2a2a; padding: 20px; border-radius: 12px; margin-bottom: 24px; text-align: center;">
            <div style="font-size: 18px; font-weight: 600; color: #FFD700; margin-bottom: 8px;">${name}</div>
            <div style="font-size: 14px; opacity: 0.6; color: #ffffff;">No. KP: ${idNumber}</div>
          </div>
          <button class="btn-primary" onclick="submitVote('${idNumber}')" style="margin-bottom: 12px;">✓ Sahkan Undi</button>
          <button class="btn-secondary" onclick="this.closest('.modal-overlay').remove()">Batal</button>
        </div>
      `;
      
      document.body.appendChild(confirmDiv);
    }
    
    async function submitVote(votedIdNumber) {
      document.querySelector('.modal-overlay')?.remove();
      
      const btn = document.querySelector('.btn-primary');
      if (btn) {
        btn.disabled = true;
        btn.textContent = 'Menghantar...';
      }
      
      const voteData = {
        type: 'vote',
        timestamp: Date.now(),
        voterId: currentUser,
        positionId: selectedPosition,
        votedIdNumber: votedIdNumber
      };
      
      const result = await window.dataSdk.create(voteData);
      
      if (result.isOk) {
        showToast('Undi berjaya direkodkan!', 'success');
        renderCurrentView();
      } else {
        showToast('Gagal menghantar undi', 'error');
        if (btn) {
          btn.disabled = false;
          btn.textContent = 'Cuba Lagi';
        }
      }
    }
    
    // Admin Functions
    function showAdminLogin() {
      const modal = document.createElement('div');
      modal.className = 'modal-overlay';
      modal.innerHTML = `
        <div class="modal-content">
          <h3 style="color: #FFD700; font-size: 24px; font-weight: 700; margin-bottom: 24px; text-align: center;">Admin Login</h3>
          <form onsubmit="adminLogin(event)">
            <div style="margin-bottom: 24px;">
              <label style="color: #ffffff; display: block; margin-bottom: 8px; font-weight: 500;">Password</label>
              <input type="password" id="admin-password" class="input-field" placeholder="Masukkan password" required>
            </div>
            <button type="submit" class="btn-primary" style="margin-bottom: 12px;">Masuk</button>
            <button type="button" class="btn-secondary" onclick="this.closest('.modal-overlay').remove()">Batal</button>
          </form>

        </div>
      `;
      
      document.body.appendChild(modal);
    }
    
    function adminLogin(event) {
      event.preventDefault();
      
      const password = document.getElementById('admin-password').value;
      
      if (password === '098765432-1') {
        currentUser = 'SUPER';
        currentView = 'admin';
        document.querySelector('.modal-overlay').remove();
        renderCurrentView();
        showToast('Selamat datang Super Admin!', 'success');
      } else if (password === 'cba4082') {
        currentUser = 'ADMIN';
        currentView = 'admin';
        document.querySelector('.modal-overlay').remove();
        renderCurrentView();
        showToast('Selamat datang Admin!', 'success');
      } else {
        showToast('Password salah', 'error');
      }
    }
    
    async function createPosition(event) {
      event.preventDefault();
      
      const name = document.getElementById('position-name').value;
      const code = document.getElementById('position-code').value;
      const duration = parseInt(document.getElementById('position-duration').value);
      const mode = document.getElementById('position-mode').value;
      
      const existingCode = allData.find(d => d.type === 'position' && d.code === code);
      if (existingCode) {
        showToast('Kod sudah digunakan', 'error');
        return;
      }
      
      // Show preview modal before creating
      showPreviewModal(name, code, duration, mode);
    }
    
    function showPreviewModal(name, code, duration, mode) {
      const modal = document.createElement('div');
      modal.className = 'modal-overlay';
      modal.innerHTML = `
        <div class="modal-content">
          <h3 style="color: #FFD700; font-size: 24px; font-weight: 700; margin-bottom: 24px; text-align: center;">📋 Semak Maklumat Jawatan</h3>
          
          <div style="background: #2a2a2a; padding: 24px; border-radius: 12px; margin-bottom: 24px;">
            <div style="margin-bottom: 20px;">
              <p style="color: #ffffff; opacity: 0.6; font-size: 14px; margin-bottom: 4px;">Nama Jawatan:</p>
              <p style="color: #ffffff; font-size: 18px; font-weight: 600;">${name}</p>
            </div>
            
            <div style="margin-bottom: 20px; padding: 20px; background: #1a1a1a; border-radius: 12px; border: 2px solid #FFD700;">
              <p style="color: #FFD700; opacity: 0.8; font-size: 14px; margin-bottom: 8px; text-align: center;">🔑 Kod Undian</p>
              <p style="color: #FFD700; font-size: 36px; font-weight: 700; text-align: center; letter-spacing: 8px;">${code}</p>
            </div>
            
            <div style="margin-bottom: 20px;">
              <p style="color: #ffffff; opacity: 0.6; font-size: 14px; margin-bottom: 4px;">Durasi:</p>
              <p style="color: #ffffff; font-size: 18px; font-weight: 600;">${duration} Minit</p>
            </div>
            
            <div>
              <p style="color: #ffffff; opacity: 0.6; font-size: 14px; margin-bottom: 4px;">Mode:</p>
              <p style="color: #ffffff; font-size: 18px; font-weight: 600;">${mode}</p>
            </div>
          </div>
          
          <div style="background: #FFD700; padding: 16px; border-radius: 12px; margin-bottom: 24px;">
            <p style="color: #000000; font-size: 14px; font-weight: 600; text-align: center;">
              ⚠️ Pastikan ahli masukkan kod: <span style="font-size: 18px;">${code}</span>
            </p>
          </div>
          
          <button class="btn-primary" onclick="confirmCreatePosition('${name}', '${code}', ${duration}, '${mode}')" id="confirm-create-btn" style="margin-bottom: 12px;">
            ✓ Simpan Jawatan
          </button>
          <button class="btn-secondary" onclick="this.closest('.modal-overlay').remove()">Batal</button>
        </div>
      `;
      
      document.body.appendChild(modal);
    }
    
    async function confirmCreatePosition(name, code, duration, mode) {
      const btn = document.getElementById('confirm-create-btn');
      btn.disabled = true;
      btn.textContent = 'Membuka...';
      
      const startTime = Date.now();
      const endTime = startTime + (duration * 60 * 1000);
      
      const positionData = {
        type: 'position',
        positionId: `P${Date.now()}`,
        positionName: name,
        code: code,
        durationMin: duration,
        mode: mode,
        startTime: 0,
        endTime: 0,
        status: 'DRAFT'
      };
      
      const result = await window.dataSdk.create(positionData);
      
      if (result.isOk) {
        document.querySelector('.modal-overlay')?.remove();
        showToast('Jawatan berjaya disimpan sebagai draft!', 'success');
        currentView = 'admin';
        renderCurrentView();
      } else {
        showToast('Gagal menyimpan jawatan', 'error');
        btn.disabled = false;
        btn.textContent = '✓ Simpan Jawatan';
      }
    }
    
    async function openPosition(positionId) {
      const position = allData.find(d => d.positionId === positionId);
      if (!position) return;
      
      const duration = position.durationMin;
      const startTime = Date.now();
      const endTime = startTime + (duration * 60 * 1000);
      
      const updatedPosition = {
        ...position,
        startTime: startTime,
        endTime: endTime,
        status: 'OPEN'
      };
      
      const result = await window.dataSdk.update(updatedPosition);
      
      if (result.isOk) {
        showToast('Jawatan dibuka semula', 'success');
      } else {
        showToast('Gagal membuka jawatan', 'error');
      }
    }
    
    function showActivatePositionModal(positionId) {
      const position = allData.find(d => d.positionId === positionId);
      if (!position) return;
      
      const modal = document.createElement('div');
      modal.className = 'modal-overlay';
      modal.innerHTML = `
        <div class="modal-content">
          <h3 style="color: #FFD700; font-size: 24px; font-weight: 700; margin-bottom: 24px; text-align: center;">🚀 Buka Undian</h3>
          
          <div style="background: #2a2a2a; padding: 24px; border-radius: 12px; margin-bottom: 24px;">
            <div style="margin-bottom: 20px;">
              <p style="color: #ffffff; opacity: 0.6; font-size: 14px; margin-bottom: 4px;">Jawatan:</p>
              <p style="color: #ffffff; font-size: 20px; font-weight: 600;">${position.positionName}</p>
            </div>
            
            <div style="margin-bottom: 20px; padding: 20px; background: #1a1a1a; border-radius: 12px; border: 2px solid #FFD700;">
              <p style="color: #FFD700; opacity: 0.8; font-size: 14px; margin-bottom: 8px; text-align: center;">🔑 Kod Undian</p>
              <p style="color: #FFD700; font-size: 42px; font-weight: 700; text-align: center; letter-spacing: 12px;">${position.code}</p>
            </div>
            
            <div style="margin-bottom: 20px;">
              <p style="color: #ffffff; opacity: 0.6; font-size: 14px; margin-bottom: 4px;">Durasi:</p>
              <p style="color: #ffffff; font-size: 18px; font-weight: 600;">${position.durationMin} Minit</p>
            </div>
            
            <div>
              <p style="color: #ffffff; opacity: 0.6; font-size: 14px; margin-bottom: 4px;">Mode:</p>
              <p style="color: #ffffff; font-size: 18px; font-weight: 600;">${position.mode}</p>
            </div>
          </div>
          
          <div style="background: #FFD700; padding: 16px; border-radius: 12px; margin-bottom: 24px;">
            <p style="color: #000000; font-size: 14px; font-weight: 600; text-align: center;">
              ⚠️ Masa akan bermula selepas anda klik buka undian
            </p>
          </div>
          
          <button class="btn-primary" onclick="activatePosition('${position.positionId}')" id="activate-btn" style="margin-bottom: 12px;">
            ▶️ Buka Undian Sekarang
          </button>
          <button class="btn-secondary" onclick="this.closest('.modal-overlay').remove()">Batal</button>
        </div>
      `;
      
      document.body.appendChild(modal);
    }
    
    async function activatePosition(positionId) {
      const btn = document.getElementById('activate-btn');
      btn.disabled = true;
      btn.textContent = 'Membuka...';
      
      const position = allData.find(d => d.positionId === positionId);
      if (!position) return;
      
      const duration = position.durationMin;
      const startTime = Date.now();
      const endTime = startTime + (duration * 60 * 1000);
      
      const updatedPosition = {
        ...position,
        startTime: startTime,
        endTime: endTime,
        status: 'OPEN'
      };
      
      const result = await window.dataSdk.update(updatedPosition);
      
      if (result.isOk) {
        document.querySelector('.modal-overlay')?.remove();
        showToast('Undian berjaya dibuka!', 'success');
      } else {
        showToast('Gagal membuka undian', 'error');
        btn.disabled = false;
        btn.textContent = '▶️ Buka Undian Sekarang';
      }
    }
    
    async function closePosition(positionId) {
      const position = allData.find(d => d.positionId === positionId);
      if (!position) return;
      
      const updatedPosition = {
        ...position,
        status: 'CLOSED'
      };
      
      const result = await window.dataSdk.update(updatedPosition);
      
      if (result.isOk) {
        showToast('Jawatan ditutup', 'success');
        if (countdownIntervals[positionId]) {
          clearInterval(countdownIntervals[positionId]);
          delete countdownIntervals[positionId];
        }
      } else {
        showToast('Gagal menutup jawatan', 'error');
      }
    }
    
    async function closePositionAuto(positionId) {
      const position = allData.find(d => d.positionId === positionId);
      if (!position) return;
      
      const updatedPosition = {
        ...position,
        status: 'CLOSED'
      };
      
      await window.dataSdk.update(updatedPosition);
    }
    
    // CSV Upload Function
    function handleCSVUpload(event) {
      const file = event.target.files[0];
      if (!file) return;
      
      const reader = new FileReader();
      reader.onload = function(e) {
        const csvText = e.target.result;
        document.getElementById('import-data').value = csvText;
        showToast('Fail CSV berjaya dimuatkan! Klik "Import Data"', 'success');
      };
      reader.onerror = function() {
        showToast('Gagal membaca fail CSV', 'error');
      };
      reader.readAsText(file);
      
      // Reset file input
      event.target.value = '';
    }
    
    // Seed Initial Data (Members)
    async function seedInitialMembers() {
      const members = allData.filter(d => d.type === 'member');
      
      if (members.length === 0) {
        const initialMembers = [
          { type: 'member', idNumber: '850123-10-5678', name: 'Ahmad bin Ali' },
          { type: 'member', idNumber: '920315-08-4321', name: 'Siti binti Amin' },
          { type: 'member', idNumber: '780605-14-9876', name: 'Razak bin Omar' },
          { type: 'member', idNumber: '991020-05-1234', name: 'Fatimah binti Hassan' },
          { type: 'member', idNumber: '870815-12-5555', name: 'Ismail bin Ibrahim' }
        ];
        
        for (const member of initialMembers) {
          await window.dataSdk.create(member);
        }
      }
    }
    
    async function importMembers(event) {
      event.preventDefault();
      
      const data = document.getElementById('import-data').value;
      if (!data.trim()) {
        showToast('Sila masukkan data atau pilih fail CSV', 'error');
        return;
      }
      
      const btn = document.getElementById('import-btn');
      btn.disabled = true;
      btn.textContent = 'Memproses...';
      
      const lines = data.trim().split('\n');
      
      let successCount = 0;
      let errorCount = 0;
      let duplicateCount = 0;
      
      for (const line of lines) {
        const trimmedLine = line.trim();
        if (!trimmedLine) continue;
        
        const parts = trimmedLine.split(',');
        if (parts.length < 2) {
          errorCount++;
          continue;
        }
        
        const idNumber = parts[0].trim();
        const name = parts.slice(1).join(',').trim();
        
        if (!idNumber || !name) {
          errorCount++;
          continue;
        }
        
        const existingMember = allData.find(d => d.type === 'member' && d.idNumber === idNumber);
        if (existingMember) {
          duplicateCount++;
          continue;
        }
        
        const memberData = {
          type: 'member',
          idNumber: idNumber,
          name: name
        };
        
        const result = await window.dataSdk.create(memberData);
        
        if (result.isOk) {
          successCount++;
        } else {
          errorCount++;
        }
      }
      
      btn.disabled = false;
      btn.textContent = '📥 Import Data';
      
      if (successCount > 0) {
        showToast(`✅ ${successCount} ahli berjaya diimport!`, 'success');
        document.getElementById('import-data').value = '';
      }
      
      if (duplicateCount > 0) {
        showToast(`⚠️ ${duplicateCount} duplicate diabaikan`, 'error');
      }
      
      if (errorCount > 0) {
        showToast(`❌ ${errorCount} baris gagal`, 'error');
      }
      
      // Reset file input if exists
      const fileInput = document.getElementById('csv-file');
      if (fileInput) fileInput.value = '';
    }
    
    async function deleteMember(backendId) {
      const member = allData.find(d => d.__backendId === backendId);
      if (!member) return;
      
      const result = await window.dataSdk.delete(member);
      
      if (result.isOk) {
        showToast('Ahli berjaya dipadam', 'success');
      } else {
        showToast('Gagal memadam ahli', 'error');
      }
    }
    
    async function clearAllMembers() {
      const confirmModal = document.createElement('div');
      confirmModal.className = 'modal-overlay';
      confirmModal.innerHTML = `
        <div class="modal-content">
          <h3 style="color: #FF4444; font-size: 20px; font-weight: 600; margin-bottom: 16px; text-align: center;">⚠️ Amaran</h3>
          <p style="color: #ffffff; opacity: 0.8; text-align: center; margin-bottom: 24px;">Adakah anda pasti mahu memadam SEMUA ahli? Tindakan ini tidak boleh dibatalkan.</p>
          <button class="btn-secondary" onclick="executeClearAllMembers()" style="margin-bottom: 12px; background: #8B0000;">Ya, Padam Semua</button>
          <button class="btn-secondary" onclick="this.closest('.modal-overlay').remove()">Batal</button>
        </div>
      `;
      
      document.body.appendChild(confirmModal);
    }
    
    async function executeClearAllMembers() {
      document.querySelector('.modal-overlay')?.remove();
      
      const members = allData.filter(d => d.type === 'member');
      
      let count = 0;
      for (const member of members) {
        const result = await window.dataSdk.delete(member);
        if (result.isOk) count++;
      }
      
      showToast(`${count} ahli berjaya dipadam`, 'success');
      renderCurrentView();
    }
    
    // PDF Report Generation
    function generatePDFReport() {
      const positions = allData.filter(d => d.type === 'position' && d.status !== 'DRAFT');
      
      if (positions.length === 0) {
        showToast('Tiada jawatan untuk dijana laporan', 'error');
        return;
      }
      
      // Create print-friendly HTML
      let reportHTML = `
        <!DOCTYPE html>
        <html>
        <head>
          <meta charset="UTF-8">
          <title>Laporan Analisis Undian</title>
          <style>
            @page {
              size: A4;
              margin: 20mm;
            }
            
            body {
              font-family: Arial, sans-serif;
              color: #000;
              line-height: 1.6;
            }
            
            .header {
              text-align: center;
              margin-bottom: 30px;
              padding-bottom: 20px;
              border-bottom: 3px solid #FFD700;
            }
            
            .logo {
              width: 80px;
              height: 80px;
              margin: 0 auto 15px auto;
            }
            
            h1 {
              color: #000;
              font-size: 24px;
              margin: 10px 0;
            }
            
            .school-name {
              font-size: 16px;
              color: #666;
              margin: 5px 0;
            }
            
            .report-date {
              font-size: 12px;
              color: #999;
              margin-top: 10px;
            }
            
            .position-section {
              margin-bottom: 40px;
              page-break-inside: avoid;
            }
            
            .position-header {
              background: #FFD700;
              padding: 15px;
              margin-bottom: 20px;
              border-radius: 8px;
            }
            
            .position-title {
              font-size: 20px;
              font-weight: bold;
              margin: 0 0 10px 0;
            }
            
            .position-info {
              font-size: 14px;
              margin: 5px 0;
            }
            
            .candidates-table {
              width: 100%;
              border-collapse: collapse;
              margin-top: 15px;
            }
            
            .candidates-table th {
              background: #f5f5f5;
              padding: 12px;
              text-align: left;
              border: 1px solid #ddd;
              font-weight: bold;
            }
            
            .candidates-table td {
              padding: 12px;
              border: 1px solid #ddd;
            }
            
            .candidates-table tr:nth-child(even) {
              background: #f9f9f9;
            }
            
            .rank-1 {
              background: #FFD700 !important;
              font-weight: bold;
            }
            
            .rank-2 {
              background: #C0C0C0 !important;
            }
            
            .rank-3 {
              background: #CD7F32 !important;
              color: #fff;
            }
            
            .summary-box {
              background: #f5f5f5;
              padding: 15px;
              border-radius: 8px;
              margin-top: 15px;
            }
            
            .no-votes {
              text-align: center;
              padding: 20px;
              color: #999;
              font-style: italic;
            }
            
            .footer {
              margin-top: 40px;
              padding-top: 20px;
              border-top: 2px solid #ddd;
              text-align: center;
              font-size: 12px;
              color: #999;
            }
            
            @media print {
              .no-print {
                display: none !important;
              }
            }
          </style>
        </head>
        <body>
          <div class="header">
            <div class="logo">
              <img src="https://i.postimg.cc/yd2wK7fY/LOGO-SEKOLAH-TIADA-BG.png" alt="Logo" style="width: 100%; height: 100%; object-fit: contain;">
            </div>
            <h1>📊 LAPORAN ANALISIS KEPUTUSAN UNDIAN</h1>
            <div class="school-name">${defaultConfig.school_name}</div>
            <div class="report-date">Tarikh: ${new Date().toLocaleDateString('ms-MY', { 
              day: 'numeric', 
              month: 'long', 
              year: 'numeric',
              hour: '2-digit',
              minute: '2-digit'
            })}</div>
          </div>
      `;
      
      // Process each position
      positions.forEach((position, index) => {
        const votes = allData.filter(d => d.type === 'vote' && d.positionId === position.positionId);
        const members = allData.filter(d => d.type === 'member');
        
        // Count votes
        const voteCounts = {};
        votes.forEach(vote => {
          voteCounts[vote.votedIdNumber] = (voteCounts[vote.votedIdNumber] || 0) + 1;
        });
        
        // Sort and get top 5
        const sortedCandidates = Object.entries(voteCounts)
          .sort((a, b) => b[1] - a[1])
          .slice(0, 5);
        
        const totalVotes = votes.length;
        const statusText = position.status === 'OPEN' ? '🟢 DIBUKA' : '🔴 DITUTUP';
        const modeText = position.mode === 'PRIVATE' ? '🔒 PRIVATE' : '🌐 UMUM';
        
        reportHTML += `
          <div class="position-section">
            <div class="position-header">
              <div class="position-title">${index + 1}. ${position.positionName}</div>
              <div class="position-info">Status: ${statusText} | Mode: ${modeText}</div>
              <div class="position-info">Kod: ${position.code} | Durasi: ${position.durationMin} minit</div>
            </div>
            
            <div class="summary-box">
              <strong>📈 Ringkasan:</strong> Jumlah Undi = ${totalVotes} | Jumlah Calon = ${sortedCandidates.length}
            </div>
        `;
        
        if (sortedCandidates.length === 0) {
          reportHTML += `<div class="no-votes">Tiada undi diterima bagi jawatan ini</div>`;
        } else {
          reportHTML += `
            <table class="candidates-table">
              <thead>
                <tr>
                  <th style="width: 10%;">Kedudukan</th>
                  <th style="width: 40%;">Nama Calon</th>
                  <th style="width: 30%;">No. Kad Pengenalan</th>
                  <th style="width: 10%;">Undi</th>
                  <th style="width: 10%;">Peratusan</th>
                </tr>
              </thead>
              <tbody>
          `;
          
          sortedCandidates.forEach((candidate, idx) => {
            const member = members.find(m => m.idNumber === candidate[0]);
            const name = member ? member.name : candidate[0];
            const votes = candidate[1];
            const percentage = ((votes / totalVotes) * 100).toFixed(1);
            
            let rankClass = '';
            let medal = '';
            if (idx === 0) {
              rankClass = 'rank-1';
              medal = '🥇';
            } else if (idx === 1) {
              rankClass = 'rank-2';
              medal = '🥈';
            } else if (idx === 2) {
              rankClass = 'rank-3';
              medal = '🥉';
            }
            
            reportHTML += `
              <tr class="${rankClass}">
                <td style="text-align: center; font-weight: bold;">${medal} #${idx + 1}</td>
                <td><strong>${name}</strong></td>
                <td>${candidate[0]}</td>
                <td style="text-align: center; font-weight: bold;">${votes}</td>
                <td style="text-align: center;">${percentage}%</td>
              </tr>
            `;
          });
          
          reportHTML += `
              </tbody>
            </table>
          `;
        }
        
        reportHTML += `</div>`;
      });
      
      reportHTML += `
          <div class="footer">
            <p>Laporan dijana secara automatik oleh Sistem Undian Sekolah</p>
            <p>© ${new Date().getFullYear()} ${defaultConfig.school_name}</p>
          </div>
          
          <div class="no-print" style="position: fixed; top: 20px; right: 20px; z-index: 1000;">
            <button onclick="window.print()" style="background: #FFD700; color: #000; padding: 15px 30px; border: none; border-radius: 8px; font-size: 16px; font-weight: bold; cursor: pointer; box-shadow: 0 4px 8px rgba(0,0,0,0.2);">
              🖨️ Print / Simpan PDF
            </button>
            <button onclick="window.close()" style="background: #666; color: #fff; padding: 15px 30px; border: none; border-radius: 8px; font-size: 16px; font-weight: bold; cursor: pointer; margin-left: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.2);">
              ✖️ Tutup
            </button>
          </div>
        </body>
        </html>
      `;
      
      // Open in new window for printing
      const printWindow = window.open('', '_blank');
      printWindow.document.write(reportHTML);
      printWindow.document.close();
      
      showToast('Laporan PDF berjaya dijana!', 'success');
    }
    
    // Initialize on page load
   // Sistem akan mula ambil data dari Google Sheets sebaik sahaja web dibuka
    document.addEventListener('DOMContentLoaded', async () => {
      await window.dataSdk.init(); 
    });
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9b83bf9f01e716ee',t:'MTc2NzQ1NjQ0MC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
