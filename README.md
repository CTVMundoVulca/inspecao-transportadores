[FORMUL~1.HTM](https://github.com/user-attachments/files/29778953/FORMUL.1.HTM)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
<meta name="theme-color" content="#1a3a5c">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-title" content="Inspeção CTV">
<title>Inspeção — CTV Mundovulca</title>
<style>
/* ── Reset & Base ──────────────────────────────────────────────── */
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
:root{
  --primary:#1a3a5c;--primary-light:#2e5f8a;--accent:#e67e22;
  --bg:#f0f2f5;--card:#fff;--border:#dde1e7;--text:#1e293b;
  --muted:#64748b;--red:#dc2626;--green:#16a34a;--yellow:#ca8a04;
  --radius:12px;--shadow:0 2px 8px rgba(0,0,0,.1);
}
body{font-family:'Segoe UI',Arial,sans-serif;background:var(--bg);color:var(--text);min-height:100vh;padding-bottom:100px}
input,select,textarea{font-family:inherit;font-size:16px}/* 16px prevents iOS zoom */
button{font-family:inherit;cursor:pointer}

/* ── Header ────────────────────────────────────────────────────── */
.app-header{
  background:var(--primary);color:#fff;
  padding:14px 16px 12px;
  position:sticky;top:0;z-index:100;
  box-shadow:0 2px 8px rgba(0,0,0,.3);
}
.app-header h1{font-size:1.05rem;font-weight:700;line-height:1.2}
.app-header .sub{font-size:.72rem;opacity:.7;margin-top:2px}
.header-row{display:flex;justify-content:space-between;align-items:flex-start;gap:8px}
.btn-report{
  background:var(--accent);color:#fff;border:none;
  padding:8px 14px;border-radius:8px;font-size:.8rem;font-weight:700;
  white-space:nowrap;flex-shrink:0;
}
.btn-report:active{opacity:.8}

/* ── Visita Header ─────────────────────────────────────────────── */
.visita-section{
  background:var(--card);margin:12px;border-radius:var(--radius);
  box-shadow:var(--shadow);overflow:hidden;
}
.visita-section summary{
  padding:12px 16px;font-weight:700;font-size:.9rem;
  color:var(--primary);list-style:none;cursor:pointer;
  display:flex;justify-content:space-between;align-items:center;
  background:#f8fafc;
}
.visita-section summary::after{content:'▾';font-size:.8rem;color:var(--muted)}
.visita-section[open] summary::after{content:'▴'}
.visita-fields{padding:12px 16px 16px;display:grid;gap:10px}

/* ── Form Controls ─────────────────────────────────────────────── */
.field{display:flex;flex-direction:column;gap:4px}
.field label{font-size:.75rem;font-weight:600;color:var(--muted);text-transform:uppercase;letter-spacing:.4px}
.field input,.field select,.field textarea{
  border:1.5px solid var(--border);border-radius:8px;padding:10px 12px;
  font-size:.95rem;background:#fff;color:var(--text);width:100%;
  transition:border-color .15s;
}
.field input:focus,.field select:focus,.field textarea:focus{
  outline:none;border-color:var(--primary-light);
}
.field textarea{resize:vertical;min-height:72px}
.field-row{display:grid;grid-template-columns:1fr 1fr;gap:10px}

/* ── OS Cards ──────────────────────────────────────────────────── */
.os-list{margin:0 12px;display:flex;flex-direction:column;gap:10px}
.os-card{
  background:var(--card);border-radius:var(--radius);
  box-shadow:var(--shadow);overflow:hidden;
  border-left:4px solid var(--border);
}
.os-card.prio-alta{border-left-color:var(--red)}
.os-card.prio-media{border-left-color:var(--yellow)}
.os-card.prio-baixa{border-left-color:var(--green)}

.os-header{
  padding:12px 14px;cursor:pointer;
  display:flex;align-items:center;gap:10px;
  background:#fafbfc;
}
.os-header-info{flex:1;min-width:0}
.os-tag{font-size:.82rem;font-weight:700;color:var(--primary);font-family:monospace}
.os-desc-preview{font-size:.75rem;color:var(--muted);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;margin-top:2px}
.os-badges{display:flex;gap:4px;flex-shrink:0}
.badge{padding:2px 7px;border-radius:10px;font-size:.65rem;font-weight:700;text-transform:uppercase}
.badge-pend{background:#fef9c3;color:#854d0e}
.badge-and{background:#dbeafe;color:#1e40af}
.badge-conc{background:#dcfce7;color:#15803d}
.badge-foto{background:#f1f5f9;color:#475569}
.os-toggle{font-size:1.1rem;color:var(--muted);flex-shrink:0}

.os-body{padding:14px;display:none;border-top:1px solid var(--border)}
.os-body.open{display:block}
.os-body .field{margin-bottom:10px}
.os-body .field-row{margin-bottom:10px}

/* ── Delete button ─────────────────────────────────────────────── */
.btn-delete{
  background:none;border:1.5px solid #fca5a5;color:var(--red);
  border-radius:8px;padding:8px;font-size:.8rem;font-weight:600;
  width:100%;margin-top:10px;
}
.btn-delete:active{background:#fee2e2}

/* ── Photo Area ────────────────────────────────────────────────── */
.photo-section{margin-top:4px}
.photo-section label.section-lbl{
  font-size:.75rem;font-weight:600;color:var(--muted);
  text-transform:uppercase;letter-spacing:.4px;display:block;margin-bottom:8px;
}
.photo-grid-small{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(90px,1fr));gap:8px;
  margin-bottom:10px;
}
.photo-thumb-wrap{position:relative;aspect-ratio:1;border-radius:8px;overflow:hidden}
.photo-thumb-wrap img{width:100%;height:100%;object-fit:cover}
.photo-remove{
  position:absolute;top:3px;right:3px;
  background:rgba(0,0,0,.6);color:#fff;
  border:none;border-radius:50%;width:22px;height:22px;
  font-size:.75rem;line-height:22px;text-align:center;padding:0;
}
.photo-remove:active{background:var(--red)}

.btn-camera{
  display:flex;align-items:center;justify-content:center;gap:8px;
  background:var(--primary);color:#fff;border:none;
  border-radius:10px;padding:12px;width:100%;font-size:.9rem;font-weight:600;
}
.btn-camera:active{opacity:.8}
.camera-input{display:none}

/* ── Add OS button ─────────────────────────────────────────────── */
.btn-add-os{
  display:flex;align-items:center;justify-content:center;gap:8px;
  margin:14px 12px;background:#fff;color:var(--primary);
  border:2px dashed var(--primary-light);border-radius:var(--radius);
  padding:14px;font-size:.95rem;font-weight:700;
}
.btn-add-os:active{background:#f0f6ff}

/* ── Footer stats ──────────────────────────────────────────────── */
.footer-bar{
  position:fixed;bottom:0;left:0;right:0;
  background:var(--primary);color:#fff;
  display:flex;justify-content:space-around;padding:8px 0 10px;
  box-shadow:0 -2px 8px rgba(0,0,0,.2);font-size:.72rem;text-align:center;
}
.footer-stat strong{display:block;font-size:1.05rem;color:var(--accent)}

/* ── Modal de relatório ────────────────────────────────────────── */
.overlay{
  display:none;position:fixed;inset:0;background:rgba(0,0,0,.5);
  z-index:200;align-items:flex-end;
}
.overlay.open{display:flex}
.bottom-sheet{
  background:#fff;border-radius:18px 18px 0 0;
  padding:20px;width:100%;
}
.bottom-sheet h2{font-size:1rem;margin-bottom:12px;color:var(--primary)}
.btn-sheet{
  display:block;width:100%;padding:13px;border-radius:10px;
  font-size:.92rem;font-weight:700;margin-bottom:10px;border:none;
}
.btn-download{background:var(--primary);color:#fff}
.btn-download:active{opacity:.8}
.btn-share{background:#25D366;color:#fff}
.btn-share:active{opacity:.8}
.btn-cancel{background:#f1f5f9;color:var(--muted)}
.btn-cancel:active{background:#e2e8f0}
.btn-clear{background:#fee2e2;color:var(--red)}
.btn-clear:active{background:#fecaca}

/* ── Empty state ───────────────────────────────────────────────── */
.empty-state{
  text-align:center;padding:40px 20px;color:var(--muted);
}
.empty-state .icon{font-size:3rem;margin-bottom:12px}
.empty-state p{font-size:.9rem}

/* ── Toast ─────────────────────────────────────────────────────── */
.toast{
  position:fixed;bottom:80px;left:50%;transform:translateX(-50%);
  background:#1e293b;color:#fff;padding:10px 20px;border-radius:20px;
  font-size:.82rem;z-index:300;opacity:0;transition:opacity .2s;
  pointer-events:none;white-space:nowrap;
}
.toast.show{opacity:1}
</style>
</head>
<body>

<!-- ── APP HEADER ─────────────────────────────────────────────── -->
<div class="app-header">
  <div class="header-row">
    <div>
      <h1>📋 Inspeção de Transportadores</h1>
      <div class="sub">CTV Mundovulca — toque em + para adicionar OS</div>
    </div>
    <button class="btn-report" onclick="showReportSheet()">📄 Relatório</button>
  </div>
</div>

<!-- ── DADOS DA VISITA ─────────────────────────────────────────── -->
<details class="visita-section" id="visita-details" open>
  <summary>📍 Dados da Visita</summary>
  <div class="visita-fields">
    <div class="field">
      <label>Cliente / Empresa</label>
      <input type="text" id="v-cliente" placeholder="Ex: Suzano Aracruz" oninput="save()">
    </div>
    <div class="field-row">
      <div class="field">
        <label>Data da Visita</label>
        <input type="date" id="v-data" oninput="save()">
      </div>
      <div class="field">
        <label>Inspetor</label>
        <input type="text" id="v-inspetor" placeholder="Seu nome" oninput="save()">
      </div>
    </div>
    <div class="field">
      <label>Observações Gerais</label>
      <textarea id="v-obs" rows="2" placeholder="Condições gerais, acesso, etc." oninput="save()"></textarea>
    </div>
  </div>
</details>

<!-- ── LISTA DE OS ─────────────────────────────────────────────── -->
<div class="os-list" id="os-list">
  <div class="empty-state" id="empty-state">
    <div class="icon">🏭</div>
    <p>Nenhuma OS registrada.<br>Toque em <strong>+ Nova OS</strong> para começar.</p>
  </div>
</div>

<!-- ── BOTÃO ADICIONAR ─────────────────────────────────────────── -->
<button class="btn-add-os" onclick="addOS()">
  ＋ Nova Ordem de Serviço
</button>

<!-- ── RODAPÉ DE ESTATÍSTICAS ──────────────────────────────────── -->
<div class="footer-bar" id="footer-bar">
  <div class="footer-stat"><strong id="stat-os">0</strong>OS</div>
  <div class="footer-stat"><strong id="stat-fotos">0</strong>Fotos</div>
  <div class="footer-stat"><strong id="stat-pend">0</strong>Pendentes</div>
  <div class="footer-stat"><strong id="stat-conc">0</strong>Concluídas</div>
</div>

<!-- ── BOTTOM SHEET ────────────────────────────────────────────── -->
<div class="overlay" id="overlay" onclick="hideOverlay(event)">
  <div class="bottom-sheet">
    <h2>📄 Gerar Relatório</h2>
    <button class="btn-sheet btn-download" onclick="gerarRelatorio()">
      ⬇ Baixar Relatório HTML
    </button>
    <button class="btn-sheet btn-share" onclick="compartilharRelatorio()">
      📤 Compartilhar (WhatsApp / E-mail)
    </button>
    <button class="btn-sheet btn-download" onclick="exportarJSON()" style="background:#475569">
      💾 Fazer Backup (JSON)
    </button>
    <button class="btn-sheet btn-clear" onclick="confirmarLimpar()">
      🗑 Limpar — Nova Visita
    </button>
    <button class="btn-sheet btn-cancel" onclick="hideSheet()">Cancelar</button>
  </div>
</div>

<!-- ── TOAST ──────────────────────────────────────────────────── -->
<div class="toast" id="toast"></div>

<script>
// ═══════════════════════════════════════════════════════════════
// ESTADO
// ═══════════════════════════════════════════════════════════════
let state = {
  visita: { cliente:'', data:'', inspetor:'', obs:'' },
  ordens: []   // { id, tag, desc, tipo, prioridade, status, responsavel, dataPrev, obs, fotos:[] }
};
let nextId = 1;

const STORAGE_KEY = 'ctv_inspecao_v2';

// ═══════════════════════════════════════════════════════════════
// PERSISTÊNCIA
// ═══════════════════════════════════════════════════════════════
function save() {
  readVisitaFields();
  try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); }
  catch(e) { showToast('Aviso: armazenamento cheio — fotos podem não salvar.'); }
}

function load() {
  try {
    const raw = localStorage.getItem(STORAGE_KEY);
    if (!raw) return;
    const s = JSON.parse(raw);
    state = s;
    if (!state.ordens) state.ordens = [];
    // Find max id
    nextId = Math.max(0, ...state.ordens.map(o => o.id || 0)) + 1;
  } catch(e) {}
}

function readVisitaFields() {
  state.visita.cliente  = document.getElementById('v-cliente').value;
  state.visita.data     = document.getElementById('v-data').value;
  state.visita.inspetor = document.getElementById('v-inspetor').value;
  state.visita.obs      = document.getElementById('v-obs').value;
}

function fillVisitaFields() {
  document.getElementById('v-cliente').value  = state.visita.cliente  || '';
  document.getElementById('v-data').value     = state.visita.data     || new Date().toISOString().split('T')[0];
  document.getElementById('v-inspetor').value = state.visita.inspetor || '';
  document.getElementById('v-obs').value      = state.visita.obs      || '';
}

// ═══════════════════════════════════════════════════════════════
// OS CRUD
// ═══════════════════════════════════════════════════════════════
function addOS() {
  const ordem = {
    id: nextId++,
    tag:'', desc:'', tipo:'', prioridade:'Alta',
    status:'Pendente', responsavel:'', dataPrev:'', obs:'',
    fotos:[]
  };
  state.ordens.push(ordem);
  renderOS(ordem, true);  // open=true
  updateStats();
  save();
  // Scroll to new card
  setTimeout(() => {
    const card = document.getElementById('os-'+ordem.id);
    if (card) card.scrollIntoView({ behavior:'smooth', block:'start' });
  }, 100);
}

function deleteOS(id) {
  if (!confirm('Excluir esta OS e todas as suas fotos?')) return;
  state.ordens = state.ordens.filter(o => o.id !== id);
  const card = document.getElementById('os-'+id);
  if (card) card.remove();
  updateStats();
  save();
  checkEmpty();
}

function getOrdem(id) {
  return state.ordens.find(o => o.id === id);
}

function readOSFields(id) {
  const o = getOrdem(id);
  if (!o) return;
  o.tag          = val('os-tag-'+id);
  o.desc         = val('os-desc-'+id);
  o.tipo         = val('os-tipo-'+id);
  o.prioridade   = val('os-prio-'+id);
  o.status       = val('os-status-'+id);
  o.responsavel  = val('os-resp-'+id);
  o.dataPrev     = val('os-dataprev-'+id);
  o.obs          = val('os-obs-'+id);
  updateCardHeader(id);
  updateStats();
}

function val(id) {
  const el = document.getElementById(id);
  return el ? el.value : '';
}

// ═══════════════════════════════════════════════════════════════
// RENDER
// ═══════════════════════════════════════════════════════════════
function renderAll() {
  const list = document.getElementById('os-list');
  // Remove existing cards (not empty state)
  list.querySelectorAll('.os-card').forEach(c => c.remove());
  state.ordens.forEach(o => renderOS(o, false));
  fillVisitaFields();
  updateStats();
  checkEmpty();
}

function renderOS(ordem, openBody) {
  checkEmpty(true); // hide empty state
  const list = document.getElementById('os-list');
  const id = ordem.id;

  const badgeClass = {
    'Pendente':'badge-pend','Em andamento':'badge-and','Concluído':'badge-conc'
  }[ordem.status] || 'badge-pend';

  const prioClass = {
    'Alta':'prio-alta','Média':'prio-media','Baixa':'prio-baixa'
  }[ordem.prioridade] || '';

  const card = document.createElement('div');
  card.className = `os-card ${prioClass}`;
  card.id = 'os-'+id;

  const nFotos = (ordem.fotos||[]).length;
  const descPreview = ordem.desc || ordem.tipo || 'Toque para preencher';

  card.innerHTML = `
    <div class="os-header" onclick="toggleOS(${id})">
      <div class="os-header-info">
        <div class="os-tag" id="os-tag-preview-${id}">${ordem.tag || 'TAG / OS'}</div>
        <div class="os-desc-preview" id="os-desc-preview-${id}">${descPreview}</div>
      </div>
      <div class="os-badges">
        <span class="badge ${badgeClass}" id="os-status-badge-${id}">${ordem.status||'Pendente'}</span>
        ${nFotos > 0 ? `<span class="badge badge-foto" id="os-foto-badge-${id}">📷${nFotos}</span>` : `<span class="badge badge-foto" id="os-foto-badge-${id}" style="display:none">📷0</span>`}
      </div>
      <span class="os-toggle" id="os-toggle-${id}">›</span>
    </div>
    <div class="os-body" id="os-body-${id}">
      <div class="field">
        <label>TAG / Nº da OS</label>
        <input type="text" id="os-tag-${id}" value="${esc(ordem.tag)}"
               placeholder="Ex: 3070-23-3172-2" oninput="readOSFields(${id});save()">
      </div>
      <div class="field">
        <label>Descrição do Serviço</label>
        <textarea id="os-desc-${id}" rows="2"
                  placeholder="Descreva o serviço necessário..." oninput="readOSFields(${id});save()">${esc(ordem.desc)}</textarea>
      </div>
      <div class="field">
        <label>Tipo de Serviço</label>
        <select id="os-tipo-${id}" onchange="readOSFields(${id});save()">
          ${['','Troca emenda quente','Troca emenda frio','Subst. revestimento tambor','Subst. correia','Reparo de emenda','Vulcanização a quente','Vulcanização a frio','Alinhamento de correia','Troca de roletes','Inspeção geral','Outro'].map(t =>
            `<option value="${t}" ${ordem.tipo===t?'selected':''}>${t||'— selecione —'}</option>`
          ).join('')}
        </select>
      </div>
      <div class="field-row">
        <div class="field">
          <label>Prioridade</label>
          <select id="os-prio-${id}" onchange="readOSFields(${id});save()">
            ${['Alta','Média','Baixa'].map(p =>
              `<option value="${p}" ${ordem.prioridade===p?'selected':''}>${p}</option>`
            ).join('')}
          </select>
        </div>
        <div class="field">
          <label>Status</label>
          <select id="os-status-${id}" onchange="readOSFields(${id});save()">
            ${['Pendente','Em andamento','Concluído'].map(s =>
              `<option value="${s}" ${ordem.status===s?'selected':''}>${s}</option>`
            ).join('')}
          </select>
        </div>
      </div>
      <div class="field-row">
        <div class="field">
          <label>Responsável</label>
          <input type="text" id="os-resp-${id}" value="${esc(ordem.responsavel)}"
                 placeholder="Nome" oninput="readOSFields(${id});save()">
        </div>
        <div class="field">
          <label>Data Prevista</label>
          <input type="date" id="os-dataprev-${id}" value="${esc(ordem.dataPrev)}"
                 oninput="readOSFields(${id});save()">
        </div>
      </div>
      <div class="field">
        <label>Observações</label>
        <textarea id="os-obs-${id}" rows="2"
                  placeholder="Anotações, condições, recomendações..." oninput="readOSFields(${id});save()">${esc(ordem.obs)}</textarea>
      </div>

      <!-- FOTOS -->
      <div class="photo-section">
        <label class="section-lbl">📷 Fotos (${nFotos})</label>
        <div class="photo-grid-small" id="photo-grid-${id}"></div>
        <button class="btn-camera" onclick="document.getElementById('cam-${id}').click()">
          📷 Tirar / Adicionar Foto
        </button>
        <input class="camera-input" type="file" id="cam-${id}"
               accept="image/*" capture="environment" multiple
               onchange="addFotos(${id}, this)">
      </div>

      <button class="btn-delete" onclick="deleteOS(${id})">🗑 Excluir esta OS</button>
    </div>
  `;

  list.appendChild(card);

  // Render existing photos
  renderPhotos(id);

  if (openBody) {
    document.getElementById('os-body-'+id).classList.add('open');
    document.getElementById('os-toggle-'+id).textContent = '⌄';
  }
}

function renderPhotos(id) {
  const ordem = getOrdem(id);
  if (!ordem) return;
  const grid = document.getElementById('photo-grid-'+id);
  if (!grid) return;
  grid.innerHTML = '';
  (ordem.fotos||[]).forEach((src, idx) => {
    const wrap = document.createElement('div');
    wrap.className = 'photo-thumb-wrap';
    wrap.innerHTML = `
      <img src="${src}" alt="Foto ${idx+1}" onclick="viewPhoto('${src}')">
      <button class="photo-remove" onclick="removePhoto(${id},${idx})">✕</button>
    `;
    grid.appendChild(wrap);
  });

  // Update photo count label
  const lbl = grid.previousElementSibling;
  if (lbl) lbl.textContent = `📷 Fotos (${ordem.fotos.length})`;

  // Update badge
  const badge = document.getElementById('os-foto-badge-'+id);
  if (badge) {
    const n = ordem.fotos.length;
    badge.textContent = `📷${n}`;
    badge.style.display = n > 0 ? '' : 'none';
  }
}

function toggleOS(id) {
  const body = document.getElementById('os-body-'+id);
  const toggle = document.getElementById('os-toggle-'+id);
  if (body.classList.contains('open')) {
    body.classList.remove('open');
    toggle.textContent = '›';
  } else {
    body.classList.add('open');
    toggle.textContent = '⌄';
  }
}

function updateCardHeader(id) {
  const o = getOrdem(id);
  if (!o) return;
  const tagPrev  = document.getElementById('os-tag-preview-'+id);
  const descPrev = document.getElementById('os-desc-preview-'+id);
  const badge    = document.getElementById('os-status-badge-'+id);
  const card     = document.getElementById('os-'+id);

  if (tagPrev)  tagPrev.textContent  = o.tag  || 'TAG / OS';
  if (descPrev) descPrev.textContent = o.desc || o.tipo || 'Toque para preencher';
  if (badge) {
    const cls = {'Pendente':'badge-pend','Em andamento':'badge-and','Concluído':'badge-conc'};
    badge.className = 'badge ' + (cls[o.status]||'badge-pend');
    badge.textContent = o.status||'Pendente';
  }
  if (card) {
    card.className = 'os-card ' + ({'Alta':'prio-alta','Média':'prio-media','Baixa':'prio-baixa'}[o.prioridade]||'');
  }
}

function checkEmpty(force_hide) {
  const empty = document.getElementById('empty-state');
  if (!empty) return;
  if (force_hide || state.ordens.length > 0) {
    empty.style.display = 'none';
  } else {
    empty.style.display = '';
  }
}

function updateStats() {
  const os = state.ordens;
  document.getElementById('stat-os').textContent    = os.length;
  document.getElementById('stat-fotos').textContent = os.reduce((a,o)=>a+(o.fotos||[]).length,0);
  document.getElementById('stat-pend').textContent  = os.filter(o=>o.status==='Pendente').length;
  document.getElementById('stat-conc').textContent  = os.filter(o=>o.status==='Concluído').length;
}

// ═══════════════════════════════════════════════════════════════
// FOTOS
// ═══════════════════════════════════════════════════════════════
async function addFotos(id, input) {
  const files = Array.from(input.files);
  if (!files.length) return;
  showToast('Comprimindo ' + files.length + ' foto(s)...');
  const ordem = getOrdem(id);
  if (!ordem) return;

  for (const file of files) {
    try {
      const b64 = await compressImage(file, 1200, 0.72);
      ordem.fotos.push(b64);
    } catch(e) {
      showToast('Erro ao processar foto: ' + e.message);
    }
  }
  renderPhotos(id);
  updateStats();
  save();
  input.value = '';
  showToast('✔ ' + files.length + ' foto(s) adicionada(s)');
}

function removePhoto(id, idx) {
  if (!confirm('Remover esta foto?')) return;
  const o = getOrdem(id);
  if (!o) return;
  o.fotos.splice(idx, 1);
  renderPhotos(id);
  updateStats();
  save();
}

function viewPhoto(src) {
  const w = window.open();
  w.document.write(`<body style="margin:0;background:#000;display:flex;justify-content:center;align-items:center;min-height:100vh">
    <img src="${src}" style="max-width:100vw;max-height:100vh;object-fit:contain"></body>`);
}

function compressImage(file, maxPx, quality) {
  return new Promise((resolve, reject) => {
    const img = new Image();
    const url = URL.createObjectURL(file);
    img.onload = () => {
      URL.revokeObjectURL(url);
      let w = img.width, h = img.height;
      if (w > maxPx || h > maxPx) {
        const r = Math.min(maxPx/w, maxPx/h);
        w = Math.round(w*r); h = Math.round(h*r);
      }
      const canvas = document.createElement('canvas');
      canvas.width = w; canvas.height = h;
      canvas.getContext('2d').drawImage(img, 0, 0, w, h);
      resolve(canvas.toDataURL('image/jpeg', quality));
    };
    img.onerror = () => { URL.revokeObjectURL(url); reject(new Error('Imagem inválida')); };
    img.src = url;
  });
}

// ═══════════════════════════════════════════════════════════════
// RELATÓRIO HTML
// ═══════════════════════════════════════════════════════════════
function gerarRelatorio() {
  hideSheet();
  const { cliente, data, inspetor, obs: obsGeral } = state.visita;
  const ordens = state.ordens;
  const hoje   = new Date().toLocaleDateString('pt-BR');
  const dataFmt = data ? new Date(data+'T12:00:00').toLocaleDateString('pt-BR') : '—';

  const totalFotos = ordens.reduce((a,o)=>a+(o.fotos||[]).length,0);
  const concluidas = ordens.filter(o=>o.status==='Concluído').length;
  const pendentes  = ordens.filter(o=>o.status==='Pendente').length;
  const andamento  = ordens.filter(o=>o.status==='Em andamento').length;

  const corStatus = s => ({'Pendente':'#fef9c3;color:#854d0e','Em andamento':'#dbeafe;color:#1e40af','Concluído':'#dcfce7;color:#15803d'}[s]||'#f3f4f6;color:#374151');
  const corPrio   = p => ({'Alta':'#fee2e2;color:#991b1b','Média':'#fef9c3;color:#854d0e','Baixa':'#dcfce7;color:#15803d'}[p]||'#f3f4f6;color:#374151');

  const cards = ordens.map((o, idx) => {
    const nFotos = (o.fotos||[]).length;
    const fmtData = o.dataPrev ? new Date(o.dataPrev+'T12:00:00').toLocaleDateString('pt-BR') : '';
    const chips = [
      o.tipo        ? `<span style="background:#f1f5f9;color:#475569;padding:2px 8px;border-radius:10px;font-size:.73rem">${o.tipo}</span>` : '',
      o.responsavel ? `<span style="background:#f1f5f9;color:#475569;padding:2px 8px;border-radius:10px;font-size:.73rem">👤 ${o.responsavel}</span>` : '',
      fmtData       ? `<span style="background:#f1f5f9;color:#475569;padding:2px 8px;border-radius:10px;font-size:.73rem">📅 Prev: ${fmtData}</span>` : '',
    ].filter(Boolean).join('');

    const obsHtml = o.obs ? `<div style="margin-top:8px;font-size:.82rem;color:#64748b;background:#fffbeb;border-left:3px solid #e67e22;padding:5px 10px;border-radius:0 4px 4px 0"><strong style="color:#e67e22">Obs:</strong> ${o.obs}</div>` : '';

    const thumbs = (o.fotos||[]).map((src, fi) =>
      `<img style="width:100%;aspect-ratio:4/3;object-fit:cover;border-radius:6px;cursor:pointer;border:2px solid transparent;transition:border-color .15s,transform .15s"
        src="${src}" onclick="openModal(${idx},${fi})" onmouseover="this.style.borderColor='#e67e22';this.style.transform='scale(1.04)'" onmouseout="this.style.borderColor='transparent';this.style.transform='scale(1)'">`
    ).join('');

    const photoSection = nFotos > 0
      ? `<div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(150px,1fr));gap:8px">${thumbs}</div>`
      : `<p style="color:#94a3b8;font-style:italic;font-size:.83rem">📷 Nenhuma foto registrada.</p>`;

    return `
<div style="background:#fff;border-radius:10px;border:1px solid #e2e8f0;margin-bottom:20px;overflow:hidden;box-shadow:0 1px 4px rgba(0,0,0,.07)">
  <div style="padding:14px 18px;background:#fafbfc;border-bottom:1px solid #e2e8f0">
    <div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap;margin-bottom:8px">
      <span style="background:#1a3a5c;color:#fff;padding:3px 10px;border-radius:4px;font-size:.77rem;font-weight:700;font-family:monospace">${o.tag||'—'}</span>
      <span style="padding:2px 9px;border-radius:12px;font-size:.71rem;font-weight:700;background:${corStatus(o.status)}">${o.status||'Pendente'}</span>
      <span style="padding:2px 9px;border-radius:12px;font-size:.71rem;font-weight:700;background:${corPrio(o.prioridade)}">${o.prioridade||'—'}</span>
      <span style="padding:2px 9px;border-radius:12px;font-size:.71rem;font-weight:700;background:#eff6ff;color:#1d4ed8">📷 ${nFotos} foto${nFotos!==1?'s':''}</span>
    </div>
    <p style="font-size:.88rem;line-height:1.55">${o.desc||'—'}</p>
    ${chips ? `<div style="display:flex;gap:6px;flex-wrap:wrap;margin-top:8px">${chips}</div>` : ''}
    ${obsHtml}
  </div>
  <div style="padding:14px 18px">${photoSection}</div>
</div>`;
  }).join('');

  const modalData = JSON.stringify(ordens.map(o => (o.fotos||[])));
  const tagsJson  = JSON.stringify(ordens.map(o => o.tag||'—'));

  const obsGeralHtml = obsGeral
    ? `<div style="background:#fff;border-radius:10px;border:1px solid #e2e8f0;padding:14px 18px;margin-bottom:20px;box-shadow:0 1px 4px rgba(0,0,0,.07)">
        <div style="font-weight:700;color:#1a3a5c;margin-bottom:6px">📝 Observações Gerais</div>
        <p style="font-size:.9rem;color:#334155;line-height:1.6">${obsGeral}</p>
       </div>` : '';

  const html = `<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Inspeção — ${cliente||'Transportadores'}</title>
</head>
<body style="font-family:'Segoe UI',Arial,sans-serif;background:#f0f2f5;color:#1e293b;margin:0;padding-bottom:20px">
<div style="background:#1a3a5c;color:#fff;padding:18px 24px;display:flex;justify-content:space-between;align-items:center;box-shadow:0 2px 8px rgba(0,0,0,.3)">
  <div>
    <div style="font-size:1.25rem;font-weight:700">📋 Relatório de Inspeção — ${cliente||'Transportadores'}</div>
    <div style="font-size:.78rem;opacity:.7;margin-top:3px">Data: ${dataFmt} &nbsp;|&nbsp; Inspetor: ${inspetor||'—'} &nbsp;|&nbsp; Gerado em: ${hoje}</div>
  </div>
  <div style="font-size:2rem">🏭</div>
</div>
<div style="background:#122a42;padding:10px 24px;display:flex;gap:28px;flex-wrap:wrap">
  <div style="color:rgba(255,255,255,.8);font-size:.8rem"><strong style="color:#e67e22;font-size:1rem">${ordens.length}</strong> OS</div>
  <div style="color:rgba(255,255,255,.8);font-size:.8rem"><strong style="color:#e67e22;font-size:1rem">${totalFotos}</strong> Fotos</div>
  <div style="color:rgba(255,255,255,.8);font-size:.8rem"><strong style="color:#e67e22;font-size:1rem">${concluidas}</strong> Concluídas</div>
  <div style="color:rgba(255,255,255,.8);font-size:.8rem"><strong style="color:#e67e22;font-size:1rem">${andamento}</strong> Em andamento</div>
  <div style="color:rgba(255,255,255,.8);font-size:.8rem"><strong style="color:#e67e22;font-size:1rem">${pendentes}</strong> Pendentes</div>
</div>
<div style="max-width:1000px;margin:24px auto;padding:0 16px">
  ${obsGeralHtml}
  ${cards}
</div>
<div style="text-align:center;padding:20px;color:#94a3b8;font-size:.75rem;background:#fff;border-top:1px solid #e2e8f0;margin-top:8px">
  Relatório gerado pelo formulário CTV Mundovulca — Manutenção de Correias Transportadoras
</div>
<div id="modal" onclick="if(event.target===this)closeModal()" style="display:none;position:fixed;inset:0;background:rgba(0,0,0,.92);z-index:999;justify-content:center;align-items:center;flex-direction:column">
  <button onclick="closeModal()" style="position:fixed;top:14px;right:18px;background:none;border:none;color:#fff;font-size:1.8rem;cursor:pointer;opacity:.7">✕</button>
  <img id="mimg" style="max-width:90vw;max-height:78vh;object-fit:contain;border-radius:6px">
  <div id="mtag" style="color:rgba(255,255,255,.55);font-size:.78rem;margin-top:8px"></div>
  <div style="display:flex;align-items:center;gap:18px;margin-top:12px">
    <button onclick="nav(-1)" style="background:rgba(255,255,255,.14);color:#fff;border:1px solid rgba(255,255,255,.3);border-radius:6px;padding:7px 18px;font-size:.88rem;cursor:pointer">← Anterior</button>
    <span id="mcnt" style="color:rgba(255,255,255,.65);font-size:.82rem;min-width:56px;text-align:center"></span>
    <button onclick="nav(1)" style="background:rgba(255,255,255,.14);color:#fff;border:1px solid rgba(255,255,255,.3);border-radius:6px;padding:7px 18px;font-size:.88rem;cursor:pointer">Próxima →</button>
  </div>
</div>
<script>
const D=${modalData},T=${tagsJson};
let cc=0,cp=0;
function openModal(c,p){cc=c;cp=p;render();document.getElementById('modal').style.display='flex'}
function render(){const l=D[cc];document.getElementById('mimg').src=l[cp];document.getElementById('mcnt').textContent=(cp+1)+' / '+l.length;document.getElementById('mtag').textContent=T[cc]+' — Foto '+(cp+1)}
function nav(d){const l=D[cc];cp=(cp+d+l.length)%l.length;render()}
function closeModal(){document.getElementById('modal').style.display='none'}
document.addEventListener('keydown',e=>{if(document.getElementById('modal').style.display!=='flex')return;if(e.key==='ArrowRight')nav(1);if(e.key==='ArrowLeft')nav(-1);if(e.key==='Escape')closeModal()});
<\/script>
</body></html>`;

  const blob = new Blob([html], {type:'text/html'});
  const url  = URL.createObjectURL(blob);
  const a    = document.createElement('a');
  a.href     = url;
  a.download = `Relatorio_${(cliente||'Inspecao').replace(/\s+/g,'_')}_${data||hoje.replace(/\//g,'-')}.html`;
  a.click();
  URL.revokeObjectURL(url);
  showToast('✔ Relatório baixado!');
}

async function compartilharRelatorio() {
  if (!navigator.share) {
    gerarRelatorio();
    return;
  }
  hideSheet();
  // Generate HTML blob for sharing
  const { cliente, data } = state.visita;
  showToast('Preparando para compartilhar...');
  // Build HTML (re-use generator but return as file)
  const tempA = document.createElement('a');
  const blob = new Blob(['<!-- relatório -->'], {type:'text/html'});
  try {
    // On mobile, easiest is to download then share
    gerarRelatorio();
    showToast('Baixe o arquivo e compartilhe via WhatsApp 📤');
  } catch(e) {
    showToast('Erro: ' + e.message);
  }
}

// ═══════════════════════════════════════════════════════════════
// BACKUP JSON
// ═══════════════════════════════════════════════════════════════
function exportarJSON() {
  hideSheet();
  const json = JSON.stringify(state, null, 2);
  const blob = new Blob([json], {type:'application/json'});
  const url  = URL.createObjectURL(blob);
  const a    = document.createElement('a');
  a.href     = url;
  a.download = `backup_inspecao_${new Date().toISOString().split('T')[0]}.json`;
  a.click();
  URL.revokeObjectURL(url);
  showToast('✔ Backup salvo!');
}

// ═══════════════════════════════════════════════════════════════
// LIMPAR
// ═══════════════════════════════════════════════════════════════
function confirmarLimpar() {
  hideSheet();
  if (!confirm('Tem certeza? Isso vai apagar TODOS os dados e fotos desta inspeção. Faça backup antes!')) return;
  localStorage.removeItem(STORAGE_KEY);
  state = { visita:{cliente:'',data:'',inspetor:'',obs:''}, ordens:[] };
  nextId = 1;
  document.getElementById('os-list').querySelectorAll('.os-card').forEach(c=>c.remove());
  fillVisitaFields();
  updateStats();
  checkEmpty();
  showToast('✔ Dados limpos — pronto para nova visita');
}

// ═══════════════════════════════════════════════════════════════
// UI HELPERS
// ═══════════════════════════════════════════════════════════════
function showReportSheet() { document.getElementById('overlay').classList.add('open'); }
function hideSheet() { document.getElementById('overlay').classList.remove('open'); }
function hideOverlay(e) { if (e.target===document.getElementById('overlay')) hideSheet(); }

function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(t._timer);
  t._timer = setTimeout(() => t.classList.remove('show'), 2800);
}

function esc(s) {
  if (!s) return '';
  return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

// ═══════════════════════════════════════════════════════════════
// INIT
// ═══════════════════════════════════════════════════════════════
load();
renderAll();

// Set today's date if empty
if (!state.visita.data) {
  document.getElementById('v-data').value = new Date().toISOString().split('T')[0];
}
</script>
</body>
</html>
