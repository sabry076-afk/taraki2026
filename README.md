
<!DOCTYPE html>
<html dir="rtl" lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>إدارة إيجار التراكي</title>
<style>
:root{--navy:#0a1628;--sea:#1a3a5c;--teal:#0e7490;--aqua:#06b6d4;--gold:#f59e0b;--red:#ef4444;--green:#10b981;--white:#f8fafc;--gray:#64748b;--light:#e2e8f0;--card:#132238}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
body{background:var(--navy);color:var(--white);font-family:'Segoe UI',Tahoma,Arial,sans-serif;min-height:100vh}
#loginScreen{display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:100vh;padding:2rem 1.5rem}
.login-card{background:var(--card);border:1px solid var(--teal);border-radius:20px;padding:2.5rem 2rem;width:100%;max-width:420px;text-align:center}
.login-logo{font-size:3.5rem;margin-bottom:.5rem}
.login-title{font-size:1.5rem;color:var(--aqua);font-weight:700;margin-bottom:.3rem}
.login-sub{color:var(--gray);font-size:.9rem;margin-bottom:2rem}
input[type=text],input[type=password],input[type=number],input[type=date],select,textarea{width:100%;background:rgba(255,255,255,.07);border:1.5px solid var(--sea);border-radius:10px;color:var(--white);padding:.9rem 1rem;font-size:1rem;font-family:inherit;outline:none;transition:border-color .2s;direction:rtl}
input:focus,select:focus,textarea:focus{border-color:var(--aqua)}
select option{background:var(--navy)}
.btn{width:100%;background:var(--teal);color:#fff;border:none;border-radius:10px;padding:.9rem;font-size:1rem;font-weight:700;cursor:pointer;transition:background .2s;font-family:inherit}
.btn:active{opacity:.85}
.btn-danger{background:var(--red)}
.btn-success{background:var(--green)}
.btn-gold{background:var(--gold);color:var(--navy)}
.btn-sm{width:auto;padding:.5rem 1.2rem;font-size:.85rem;border-radius:8px}
label{display:block;text-align:right;margin-bottom:.4rem;font-size:.9rem;color:var(--light)}
.form-group{margin-bottom:1.2rem}
.error-msg{color:var(--red);font-size:.85rem;margin-top:.5rem}
#app{display:none}
.topbar{background:var(--sea);padding:1rem 1.2rem;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:100;border-bottom:2px solid var(--teal)}
.topbar-title{font-size:1.05rem;font-weight:700;color:var(--aqua)}
.topbar-user{font-size:.78rem;color:var(--gray)}
.logout-btn{background:none;border:1px solid var(--gray);color:var(--gray);border-radius:8px;padding:.3rem .8rem;font-size:.78rem;cursor:pointer}
.nav-tabs{display:flex;background:var(--sea);overflow-x:auto;border-bottom:1px solid var(--teal);padding:0 .5rem;scrollbar-width:none}
.nav-tabs::-webkit-scrollbar{display:none}
.nav-tab{flex-shrink:0;padding:.9rem 1rem;font-size:.85rem;cursor:pointer;color:var(--gray);border-bottom:3px solid transparent;white-space:nowrap;transition:color .2s,border-color .2s}
.nav-tab.active{color:var(--aqua);border-bottom-color:var(--aqua);font-weight:700}
.section{display:none;padding:1rem}
.section.active{display:block}
.card{background:var(--card);border-radius:14px;padding:1.2rem;margin-bottom:1rem;border:1px solid rgba(14,116,144,.3)}
.card-title{font-size:1rem;font-weight:700;color:var(--aqua);margin-bottom:.8rem}
.stats-grid{display:grid;grid-template-columns:1fr 1fr;gap:.8rem;margin-bottom:1rem}
.stat-card{background:var(--card);border-radius:12px;padding:1rem;text-align:center;border:1px solid rgba(14,116,144,.3)}
.stat-label{font-size:.75rem;color:var(--gray);margin-bottom:.3rem}
.stat-val{font-size:1.3rem;font-weight:800}
.tbl-wrap{overflow-x:auto;-webkit-overflow-scrolling:touch}
table{width:100%;border-collapse:collapse;font-size:.82rem;min-width:580px}
th{background:var(--sea);color:var(--aqua);padding:.7rem .8rem;text-align:right;font-weight:700;white-space:nowrap}
td{padding:.65rem .8rem;border-bottom:1px solid rgba(255,255,255,.05)}
tr:hover td{background:rgba(255,255,255,.03)}
.badge{display:inline-block;padding:.2rem .6rem;border-radius:20px;font-size:.72rem;font-weight:700}
.badge-green{background:rgba(16,185,129,.15);color:var(--green)}
.badge-red{background:rgba(239,68,68,.15);color:var(--red)}
.badge-gold{background:rgba(245,158,11,.15);color:var(--gold)}
.badge-blue{background:rgba(6,182,212,.15);color:var(--aqua)}
.search-box{position:relative;margin-bottom:1rem}
.search-box input{padding-right:2.5rem}
.search-icon{position:absolute;right:.8rem;top:50%;transform:translateY(-50%);color:var(--gray);pointer-events:none}
.boat-card{background:var(--card);border-radius:12px;padding:1rem;margin-bottom:.7rem;border:1px solid rgba(14,116,144,.25);cursor:pointer;transition:border-color .2s}
.boat-card:active{border-color:var(--aqua)}
.boat-name{font-weight:700;font-size:1rem}
.boat-owner{font-size:.8rem;color:var(--gray);margin:.2rem 0}
.boat-stats{display:flex;gap:.8rem;margin-top:.5rem;font-size:.78rem;flex-wrap:wrap}
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.7);z-index:200;align-items:flex-end}
.modal-overlay.open{display:flex}
.modal{background:var(--navy);border-radius:20px 20px 0 0;border-top:2px solid var(--teal);padding:1.5rem;width:100%;max-height:90vh;overflow-y:auto;position:relative}
.modal-title{font-size:1.1rem;font-weight:700;color:var(--aqua);margin-bottom:1.2rem;text-align:center}
.modal-close{position:absolute;left:1.2rem;top:1.5rem;background:none;border:none;color:var(--gray);font-size:1.5rem;cursor:pointer;line-height:1}
.tx-item{display:flex;justify-content:space-between;align-items:flex-start;padding:.7rem;background:rgba(255,255,255,.03);border-radius:8px;margin-bottom:.5rem;border-right:3px solid}
.tx-item.charge{border-color:var(--red)}
.tx-item.payment{border-color:var(--green)}
.tx-label{font-size:.82rem;font-weight:600}
.tx-date{font-size:.72rem;color:var(--gray);margin-top:.15rem}
.tx-amount{font-weight:700;font-size:.95rem}
.balance-bar{display:flex;justify-content:space-between;background:var(--sea);border-radius:10px;padding:.8rem 1rem;margin-bottom:1rem}
.balance-item{text-align:center}
.balance-label{font-size:.7rem;color:var(--gray);margin-bottom:.2rem}
.balance-amount{font-weight:800;font-size:.95rem}
#toast{position:fixed;bottom:1.5rem;left:50%;transform:translateX(-50%);background:var(--sea);color:#fff;padding:.8rem 1.5rem;border-radius:30px;font-size:.9rem;z-index:999;display:none;border:1px solid var(--teal);max-width:90vw;text-align:center}
.filter-row{display:flex;gap:.5rem;margin-bottom:.8rem;overflow-x:auto;padding-bottom:.3rem;scrollbar-width:none}
.filter-btn{flex-shrink:0;background:var(--sea);border:1px solid var(--teal);color:var(--gray);border-radius:20px;padding:.35rem .9rem;font-size:.78rem;cursor:pointer;white-space:nowrap}
.filter-btn.active{background:var(--teal);color:#fff;border-color:var(--teal)}
.two-col{display:grid;grid-template-columns:1fr 1fr;gap:.8rem}
.auto-banner{background:linear-gradient(135deg,rgba(16,185,129,.12),rgba(6,182,212,.08));border:1px solid rgba(16,185,129,.35);border-radius:12px;padding:1rem;margin-bottom:1rem;display:flex;align-items:flex-start;gap:.8rem}
</style>
</head>
<body>

<div id="loginScreen">
  <div class="login-card">
    <div class="login-logo">&#x2693;</div>
    <div class="login-title">الميناء السياحي - التراكي</div>
    <div class="login-sub">إدارة إيجار أماكن وقوف المراكب</div>
    <br>
    <div class="form-group">
      <label>اسم المستخدم</label>
      <input type="text" id="loginUser" placeholder="أدخل اسم المستخدم" autocomplete="username">
    </div>
    <div class="form-group">
      <label>كلمة المرور</label>
      <input type="password" id="loginPass" placeholder="أدخل كلمة المرور" autocomplete="current-password">
    </div>
    <div id="loginError" class="error-msg"></div>
    <br>
    <button class="btn" onclick="doLogin()">دخول</button>
    <div style="margin-top:1.5rem;border-top:1px solid rgba(255,255,255,.08);padding-top:1rem">
      <div style="font-size:.75rem;color:var(--gray);margin-bottom:.5rem">في حال وجود مشكلة في الدخول:</div>
      <button onclick="hardReset()" style="background:none;border:1px solid var(--red);color:var(--red);border-radius:8px;padding:.4rem 1rem;font-size:.78rem;cursor:pointer;width:100%">إعادة تهيئة التطبيق</button>
    </div>
  </div>
</div>

<div id="app">
  <div class="topbar">
    <div>
      <div class="topbar-title">&#x2693; التراكي</div>
      <div class="topbar-user" id="topbarUser"></div>
    </div>
    <button class="logout-btn" onclick="doLogout()">خروج</button>
  </div>
  <div class="nav-tabs">
    <div class="nav-tab active" data-tab="dashboard" onclick="showTab('dashboard')">لوحة التحكم</div>
    <div class="nav-tab" data-tab="boats" onclick="showTab('boats')">المراكب</div>
    <div class="nav-tab" data-tab="payments" onclick="showTab('payments')">المدفوعات</div>
    <div class="nav-tab" data-tab="reports" onclick="showTab('reports')">التقارير</div>
    <div class="nav-tab admin-only" data-tab="admin" onclick="showTab('admin')" style="display:none">الإدارة</div>
  </div>

  <div class="section active" id="secDashboard">
    <div id="autoBanner"></div>
    <div class="stats-grid">
      <div class="stat-card"><div class="stat-label">إجمالي المراكب</div><div class="stat-val" style="color:var(--aqua)" id="stTotal">-</div></div>
      <div class="stat-card"><div class="stat-label">مراكب متأخرة</div><div class="stat-val" style="color:var(--red)" id="stLate">-</div></div>
      <div class="stat-card"><div class="stat-label">إجمالي المستحق</div><div class="stat-val" style="color:var(--gold)" id="stDue">-</div></div>
      <div class="stat-card"><div class="stat-label">إجمالي المسدد</div><div class="stat-val" style="color:var(--green)" id="stPaid">-</div></div>
    </div>
    <div class="stat-card" style="margin-bottom:1rem;text-align:center">
      <div class="stat-label">صافي المديونية المتبقية</div>
      <div class="stat-val" style="color:var(--red);font-size:1.7rem" id="stRem">-</div>
    </div>
    <div class="card"><div class="card-title">مراكب متأخرة في السداد</div><div id="lateList"></div></div>
    <div class="card"><div class="card-title">آخر العمليات</div><div id="recentList"></div></div>
  </div>

  <div class="section" id="secBoats">
    <div class="search-box">
      <input type="text" id="boatSearch" placeholder="بحث عن مركب أو مستثمر..." oninput="renderBoats()">
      <span class="search-icon">&#x1F50D;</span>
    </div>
    <div class="filter-row">
      <button class="filter-btn active" onclick="setFilter('all',this)">الكل</button>
      <button class="filter-btn" onclick="setFilter('late',this)">متأخر</button>
      <button class="filter-btn" onclick="setFilter('paid',this)">مسدد</button>
      <button class="filter-btn" onclick="setFilter('advance',this)">مقدم</button>
    </div>
    <div id="boatList"></div>
    <div class="admin-only" style="display:none;margin-top:1rem" id="addBoatWrap">
      <button class="btn btn-success" onclick="openModal('addBoatModal')">+ إضافة مركب جديد</button>
    </div>
  </div>

  <div class="section" id="secPayments">
    <button class="btn btn-success" style="margin-bottom:1rem" onclick="openAddTx(0)">+ تسجيل عملية جديدة</button>
    <div class="search-box">
      <input type="text" id="paySearch" placeholder="بحث في المعاملات..." oninput="renderPayments()">
      <span class="search-icon">&#x1F50D;</span>
    </div>
    <div class="tbl-wrap">
      <table><thead><tr><th>التاريخ</th><th>المركب</th><th>البيان</th><th>المبلغ</th><th>النوع</th></tr></thead>
      <tbody id="payTable"></tbody></table>
    </div>
  </div>

  <div class="section" id="secReports">
    <div class="card">
      <div class="card-title">تقرير شامل</div>
      <div class="form-group"><label>اختر مركب</label><select id="rptBoat"><option value="all">جميع المراكب</option></select></div>
      <button class="btn" onclick="generateReport()">عرض التقرير</button>
    </div>
    <div id="rptResult"></div>
    <div class="card" style="margin-top:1rem">
      <div class="card-title">كشف حساب مركب</div>
      <div class="form-group"><label>المركب</label><select id="stmtBoat"><option value="">اختر مركب...</option></select></div>
      <button class="btn btn-gold" onclick="showStatement()">عرض كشف الحساب</button>
    </div>
    <div id="stmtResult"></div>
  </div>

  <div class="section" id="secAdmin">
    <div class="card">
      <div class="card-title">الاستحقاق التلقائي</div>
      <p style="font-size:.85rem;color:var(--gray);margin-bottom:1rem">يُضاف إيجار كل مركب تلقائياً في أول كل شهر بمجرد فتح التطبيق. كل شهر يُحتسب مرة واحدة فقط ولا تكرار.</p>
      <button class="btn" style="margin-bottom:.6rem" onclick="showAutoLog()">عرض سجل الاستحقاق</button>
      <button class="btn btn-danger" style="margin-top:.4rem" onclick="resetAutoLog()">إعادة تعيين السجل</button>
      <div id="autoLogPanel" style="margin-top:1rem"></div>
    </div>
    <div class="card">
      <div class="card-title">إدارة المستخدمين</div>
      <div id="userList"></div>
      <br><button class="btn btn-success" onclick="openModal('addUserModal')">+ إضافة مستخدم</button>
      <div style="color:var(--gray);font-size:.78rem;margin-top:.5rem" id="userCount"></div>
    </div>
    <div class="card">
      <div class="card-title">النسخ الاحتياطي</div>
      <button class="btn" onclick="exportData()">تصدير البيانات (JSON)</button>
      <br><br>
      <label>استيراد بيانات</label>
      <input type="file" id="importFile" accept=".json" onchange="importData(event)" style="padding:.5rem">
    </div>
  </div>
</div>

<!-- MODALS -->
<div class="modal-overlay" id="boatDetailModal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('boatDetailModal')">&#x2715;</button>
    <div class="modal-title" id="bdTitle"></div>
    <div id="bdContent"></div>
  </div>
</div>

<div class="modal-overlay" id="addTxModal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('addTxModal')">&#x2715;</button>
    <div class="modal-title">تسجيل عملية</div>
    <div class="form-group"><label>المركب</label><select id="txBoat"></select></div>
    <div class="form-group"><label>نوع العملية</label>
      <select id="txType"><option value="charge">استحقاق إيجار</option><option value="payment">دفع / تحصيل</option></select>
    </div>
    <div class="form-group"><label>البيان</label><input type="text" id="txDesc" placeholder="مثال: إيجار شهر أبريل"></div>
    <div class="two-col">
      <div class="form-group"><label>المبلغ (جنيه)</label><input type="number" id="txAmount" min="0.01" step="0.01" placeholder="0.00"></div>
      <div class="form-group"><label>التاريخ</label><input type="date" id="txDate"></div>
    </div>
    <div class="form-group"><label>ملاحظات (اختياري)</label><textarea id="txNote" rows="2"></textarea></div>
    <div id="txErr" class="error-msg"></div>
    <button class="btn btn-success" onclick="saveTx()">حفظ العملية</button>
  </div>
</div>

<div class="modal-overlay" id="addBoatModal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('addBoatModal')">&#x2715;</button>
    <div class="modal-title">إضافة مركب جديد</div>
    <div class="form-group"><label>اسم المركب</label><input type="text" id="nb_name" placeholder="اسم اللنش"></div>
    <div class="form-group"><label>اسم المستثمر / المالك</label><input type="text" id="nb_owner"></div>
    <div class="form-group"><label>رقم الهاتف</label><input type="text" id="nb_phone"></div>
    <div class="two-col">
      <div class="form-group"><label>المساحة (م)</label><input type="number" id="nb_area" step="0.01" placeholder="12"></div>
      <div class="form-group"><label>سعر المتر (جنيه)</label><input type="number" id="nb_price" placeholder="350"></div>
    </div>
    <div class="two-col">
      <div class="form-group"><label>تاريخ البداية</label><input type="date" id="nb_start"></div>
      <div class="form-group"><label>تاريخ النهاية (اختياري)</label><input type="date" id="nb_end"></div>
    </div>
    <div class="form-group"><label>التأمين (اختياري)</label><input type="number" id="nb_deposit" step="0.01" placeholder="0.00"></div>
    <div id="nbErr" class="error-msg"></div>
    <button class="btn btn-success" onclick="saveNewBoat()">إضافة المركب</button>
  </div>
</div>

<div class="modal-overlay" id="addUserModal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('addUserModal')">&#x2715;</button>
    <div class="modal-title">إضافة مستخدم جديد</div>
    <div class="form-group"><label>اسم المستخدم</label><input type="text" id="nu_user" placeholder="username"></div>
    <div class="form-group"><label>كلمة المرور</label><input type="password" id="nu_pass" placeholder="كلمة المرور"></div>
    <div class="form-group"><label>الاسم الكامل</label><input type="text" id="nu_name" placeholder="الاسم"></div>
    <div class="form-group"><label>الصلاحية</label>
      <select id="nu_role">
        <option value="viewer">مشاهدة فقط</option>
        <option value="user">مستخدم</option>
        <option value="admin">مدير</option>
      </select>
    </div>
    <div id="nuErr" class="error-msg"></div>
    <button class="btn btn-success" onclick="saveNewUser()">إضافة المستخدم</button>
  </div>
</div>

<div id="toast"></div>

<script>
// Global Variables
var SK = 'taraki_v3';
var MAX_USERS = 8;
var AR_MONTHS = ['يناير','فبراير','مارس','أبريل','مايو','يونيو','يوليو','أغسطس','سبتمبر','أكتوبر','نوفمبر','ديسمبر'];
var db, cu, filterMode = 'all';

// Helper Functions
function r2(n) { return Math.round(n * 100) / 100; }
function mkey(y, m) { return y + '-' + (m < 10 ? '0' + m : '' + m); }
function fmtDate(d) {
  if (!d) return '-';
  try { return new Date(d).toLocaleDateString('ar-EG', {year:'numeric',month:'short',day:'numeric'}); }
  catch(e) { return d; }
}
function fmtMoney(n) {
  var a = Math.abs(n);
  var s = a.toLocaleString('ar-EG', {minimumFractionDigits: (a % 1) ? 2 : 0, maximumFractionDigits: 2});
  return (n < 0 ? '(' + s + ')' : s) + ' ج.م';
}

var SEED = [
  {n:'يارا',o:'مصباح مصباح عبدالمنعم',p:'1222227998',a:12,r:350,s:'2026-01-01',e:'2026-03-31',d:4200},
  {n:'إياد',o:'مصباح مصباح عبدالمنعم',p:'1222227998',a:12,r:350,s:'2026-01-01',e:'2026-03-31',d:4200},
  {n:'يمني',o:'مصباح مصباح عبدالمنعم',p:'1222227998',a:12,r:350,s:'2026-01-01',e:'2026-03-31',d:4200},
  {n:'بريما دايفنج',o:'ابراهيم الدسوقي فتحي',p:'1094471993',a:21,r:500,s:'2026-01-01',e:'2026-03-31',d:10500},
  {n:'بريما',o:'ابراهيم الدسوقي فتحي',p:'1094471993',a:15,r:350,s:'2026-01-01',e:'2026-03-31',d:5250},
  {n:'مير ميد',o:'موسي ابوالحسن عبده',p:'1003959291',a:18,r:350,s:'2026-01-01',e:'2026-03-31',d:6300},
  {n:'ملو يلو',o:'محمد انور رمضان',p:'1117000046',a:23,r:500,s:'2026-01-01',e:'2026-03-31',d:11500},
  {n:'الحوت الابيض',o:'فتحي محي عبده محسن',p:'1003987224',a:25,r:500,s:'2026-01-01',e:'2026-03-31',d:12500},
  {n:'سويت مايا',o:'محمود عيد عبداللطيف',p:'1061295011',a:26,r:600,s:'2026-01-01',e:'2026-03-31',d:15600},
  {n:'البرنس ادم',o:'احمد العزب ابراهيم',p:'1223245296',a:25,r:500,s:'2026-01-01',e:'2026-03-31',d:12500},
  {n:'فان دايفيد',o:'ناصر ماهر حماده',p:'1224194582',a:25,r:500,s:'2026-01-01',e:'2026-03-31',d:12500},
  {n:'دايموند ايزابيلا',o:'النجار فراج حسين',p:'1003517051',a:26,r:600,s:'2026-01-01',e:'2026-03-31',d:15600},
  {n:'لينا',o:'محمد محسن محمد',p:'1019700089',a:17.85,r:350,s:'2026-01-01',e:'2026-03-31',d:0},
  {n:'اميره',o:'احمد رفعت محمد حسن',p:'1227743768',a:24,r:500,s:'2026-01-01',e:'2026-03-31',d:12000},
  {n:'ماروسكا',o:'جيمي ميخائيل بلاجون',p:'1100848173',a:16,r:350,s:'2026-01-01',e:'2026-03-31',d:5600},
  {n:'حورس ستار N',o:'اسلام ابو اليزيد',p:'1007248875',a:24,r:500,s:'2026-01-01',e:'2026-03-31',d:12000},
  {n:'فيش هانتر',o:'رامي فايز جورج',p:'1114469184',a:10,r:350,s:'2026-01-01',e:'2026-03-31',d:3500},
  {n:'سي ستار',o:'احمد محمد طه سالم',p:'1010577777',a:8,r:350,s:'2026-01-01',e:'2026-03-31',d:2800},
  {n:'رخاء',o:'رخاء علاء الدين سعد',p:'1007599896',a:10,r:350,s:'2026-01-01',e:'2026-03-31',d:3500},
  {n:'براون شوجر',o:'ماجد محمد حسني احمد',p:'1001910216',a:7,r:350,s:'2026-01-01',e:'2026-03-31',d:2450},
  {n:'سبايدر',o:'صبري مصطفي فهمي',p:'1227742206',a:12,r:350,s:'2026-01-01',e:'2026-03-31',d:4200},
  {n:'نور الله',o:'محمد حمدنا الله عبدالله',p:'1113556619',a:11,r:350,s:'2026-01-01',e:'2026-03-31',d:3850},
  {n:'سيلا',o:'محمود محمد عبدالامام',p:'1096655660',a:9,r:350,s:'2026-01-01',e:'2026-03-31',d:3150},
  {n:'د/ نور',o:'عصام عبد الهادي',p:'1145343432',a:18,r:350,s:'2026-01-01',e:'2026-03-31',d:6300},
  {n:'شهاب علاء الدين',o:'غادة حسين علي',p:'1098796474',a:26,r:600,s:'2026-01-01',e:'2026-03-31',d:0},
  {n:'بخيتة',o:'ايمن عمران',p:'1115863359',a:7,r:350,s:'2026-01-01',e:'2026-03-31',d:2450},
  {n:'يونا',o:'زكي شحات زكي',p:'1201009179',a:7,r:350,s:'2026-01-01',e:'2026-03-31',d:2450},
  {n:'روني 610',o:'محمد احمد حسنين',p:'1223257089',a:6,r:350,s:'2026-01-01',e:'2026-03-31',d:2100},
  {n:'ويفز',o:'مينا أفريم',p:'1583050442',a:11,r:350,s:'2026-01-01',e:'2026-03-31',d:3850},
  {n:'فرج الله 2',o:'عصام محمد فرج الله',p:'1227741400',a:8,r:350,s:'2026-01-01',e:'2026-03-31',d:2800},
  {n:'روزيتا',o:'ابو الحمد محمد سيد',p:'1222740268',a:30,r:600,s:'2026-01-01',e:'2026-03-31',d:18000},
  {n:'صن شاين',o:'ابو الحمد محمد سيد',p:'1222740268',a:29,r:600,s:'2026-01-01',e:'2026-03-31',d:17400},
  {n:'اسبرنج لاند',o:'ابو الحمد محمد سيد',p:'1222740268',a:29,r:600,s:'2026-01-01',e:'2026-03-31',d:17400},
  {n:'عمار',o:'شهدي مغربي عسران',p:'1127333276',a:10,r:350,s:'2026-01-01',e:'2026-03-31',d:3500},
  {n:'نور العين',o:'محمد مصطفى قاسم',p:'1003031730',a:18,r:350,s:'2026-01-01',e:'2026-03-31',d:6300},
  {n:'بولا 1',o:'بطرس صموئيل ايوب',p:'1227083300',a:11,r:350,s:'2026-01-01',e:'2026-03-31',d:3850},
  {n:'كيمو',o:'ماريان قاسم',p:'1223023061',a:12,r:350,s:'2026-01-01',e:'2026-03-31',d:4200},
  {n:'كوين اوف لايف',o:'مارك فورجيا',p:'1004982078',a:19,r:350,s:'2026-01-01',e:'2026-03-31',d:6650},
  {n:'رمسيس',o:'بركات عازر رمسيس',p:'1200788829',a:11,r:350,s:'2026-01-01',e:'2026-03-31',d:3850},
  {n:'الامير علاء الدين',o:'محمد احمد حندقها',p:'1143187283',a:22,r:500,s:'2026-01-01',e:'2026-12-31',d:11000},
  {n:'مو',o:'محمد احمد حندقها',p:'1143187283',a:17,r:350,s:'2026-01-01',e:'2026-03-31',d:5950},
  {n:'FD',o:'غريب اسماعيل احمد صالح',p:'1019470079',a:12,r:350,s:'2026-01-01',e:'2026-03-31',d:4200},
  {n:'HD',o:'غريب اسماعيل احمد صالح',p:'1019470079',a:12,r:350,s:'2026-01-01',e:'2026-03-31',d:4200},
  {n:'ماى ياسمين',o:'محمد مصطفى قاسم',p:'',a:24,r:500,s:'2026-01-01',e:'2026-03-31',d:12000},
  {n:'وايت دوليفن',o:'محمد مصطفى قاسم',p:'',a:26,r:600,s:'2026-01-01',e:'2026-03-31',d:15600},
  {n:'سترا 1',o:'محمد احمد على',p:'1005882235',a:13,r:350,s:'2026-01-01',e:'2026-03-31',d:4550},
  {n:'دويكن هورجادا',o:'هيثم حماده عبد الحكيم',p:'1063526787',a:24,r:500,s:'2026-01-01',e:'2026-03-31',d:12000},
  {n:'توخن هورجادا',o:'هيثم حماده عبد الحكيم',p:'1063526787',a:24,r:500,s:'2026-01-01',e:'2026-03-31',d:12000},
  {n:'توخ فريندوا هورجادا',o:'هيثم حماده عبد الحكيم',p:'1063526787',a:23,r:500,s:'2026-01-01',e:'2026-03-31',d:11500},
  {n:'مارجريت',o:'محمد مصطفى قاسم',p:'1006853079',a:22,r:500,s:'2026-01-01',e:'2026-03-31',d:11000},
  {n:'ريلاكس',o:'محمد مصطفى قاسم',p:'1006853079',a:23,r:500,s:'2026-01-01',e:'2026-03-31',d:11500},
  {n:'ابو صالح الجديد',o:'غريب احمد صالح',p:'1222242210',a:21,r:500,s:'2026-01-01',e:'2026-03-31',d:10500},
  {n:'مجاويش 2',o:'حسام الدين عيد محمد',p:'1065887293',a:14,r:350,s:'2026-01-01',e:'2026-03-31',d:4900},
  {n:'ترك',o:'عمر خالد محمود ترك',p:'1000830070',a:7,r:350,s:'2026-01-01',e:'2026-03-31',d:2450},
  {n:'بارادايس 9',o:'شركة كوين ماجي',p:'1100020720',a:26,r:600,s:'2026-01-01',e:'2026-03-31',d:15600},
  {n:'باراديس 2',o:'شركة كوين ماجي',p:'1100020720',a:21,r:500,s:'2026-01-01',e:'2026-03-31',d:10500},
  {n:'بارادايس 5',o:'شركة كوين ماجي',p:'1100020720',a:24,r:500,s:'2026-01-01',e:'2026-03-31',d:12000},
  {n:'بارادايس 1',o:'شركة كوين ماجي',p:'1100020720',a:22,r:500,s:'2026-01-01',e:'2026-03-31',d:11000},
  {n:'بارادايس 7',o:'شركة كوين ماجي',p:'1100020720',a:25,r:500,s:'2026-01-01',e:'2026-03-31',d:12500},
  {n:'بارادايس 8',o:'شركة كوين ماجي',p:'1100020720',a:23,r:500,s:'2026-01-01',e:'2026-03-31',d:11500},
  {n:'بارادايس 10',o:'شركة كوين ماجي',p:'1100020720',a:24,r:500,s:'2026-01-01',e:'2026-03-31',d:12000},
  {n:'بارادايس 4',o:'شركة كوين ماجي',p:'1100020720',a:18,r:350,s:'2026-01-01',e:'2026-03-31',d:6300},
  {n:'قطقوطة',o:'شركة كوين ماجي',p:'1100020720',a:7,r:350,s:'2026-01-01',e:'2026-03-31',d:2450},
  {n:'زين',o:'شركة كوين ماجي',p:'1100020720',a:8,r:350,s:'2026-01-01',e:'2026-03-31',d:2800},
  {n:'موكا',o:'شركة كوين ماجي',p:'1100020720',a:9,r:350,s:'2026-01-01',e:'2026-03-31',d:3150},
  {n:'اسكيبر 2',o:'شركة كوين ماجي',p:'1100020720',a:10,r:350,s:'2026-01-01',e:'2026-03-31',d:3500},
  {n:'كريم وان',o:'شركة كوين ماجي',p:'1100020720',a:10,r:350,s:'2026-01-01',e:'2026-03-31',d:3500},
  {n:'النحاس',o:'شركة كوين ماجي',p:'1100020720',a:9,r:350,s:'2026-01-01',e:'2026-03-31',d:3150},
  {n:'سوزانا',o:'شركة كوين ماجي',p:'1100020720',a:10,r:350,s:'2026-01-01',e:'2026-03-31',d:3500},
  {n:'بارادايس كونكويست 1',o:'شركة كوين ماجي',p:'1100020720',a:9,r:350,s:'2026-01-01',e:'2026-03-31',d:3150},
  {n:'باراديس كونكويست 2',o:'شركة كوين ماجي',p:'1100020720',a:9,r:350,s:'2026-01-01',e:'2026-03-31',d:3150},
  {n:'باركو',o:'شركة كوين ماجي',p:'1100020720',a:6,r:350,s:'2026-01-01',e:'2026-03-31',d:2100},
  {n:'اوركا براديس',o:'شركة كوين ماجي',p:'1100020720',a:8,r:350,s:'2026-01-01',e:'2026-03-31',d:2800},
  {n:'الخسار',o:'محمد محمدين عبدالجليل',p:'',a:16,r:350,s:'2026-01-01',e:'2026-03-31',d:5600},
  {n:'الهلب',o:'الدغيمي محمد احمد',p:'1004479118',a:8,r:350,s:'2026-01-01',e:'2026-03-31',d:2800},
  {n:'ريتاج',o:'الدغيمي محمد احمد',p:'1004479118',a:8,r:350,s:'2026-01-01',e:'2026-03-31',d:2800},
  {n:'اوركا',o:'الدغيمي محمد احمد',p:'1004479118',a:8,r:350,s:'2026-01-01',e:'2026-03-31',d:2800},
  {n:'صن سباير',o:'الدغيمي محمد احمد',p:'1004479118',a:9,r:350,s:'2026-01-01',e:'2026-03-31',d:3150},
  {n:'تونه العشق',o:'الدغيمي محمد احمد',p:'1004479118',a:7,r:350,s:'2026-01-01',e:'2026-03-31',d:2450},
  {n:'علي بابا',o:'الدغيمي محمد احمد',p:'1004479118',a:8,r:350,s:'2026-03-01',e:'2026-03-31',d:2800},
  {n:'باركودا',o:'الدغيمي محمد احمد',p:'1004479118',a:9,r:350,s:'2026-03-01',e:'2026-03-31',d:3150},
  {n:'نينو',o:'محمد احمد حسنين',p:'1223257089',a:8,r:350,s:'2026-01-01',e:'2026-03-31',d:2800},
  {n:'سوفي',o:'احمد احمد احمد زياده',p:'1204333366',a:9,r:350,s:'2026-01-01',e:'2026-03-31',d:0},
  {n:'تيا',o:'احمد احمد احمد زياده',p:'1204333366',a:11,r:350,s:'2026-01-01',e:'2026-03-31',d:3850}
];

// Core Functions
function freshDB() {
  return {
    users: [
      {id:1, username:'admin',   password:'taraki2026', name:'المدير',   role:'admin'},
      {id:2, username:'محاسب', password:'1234', name:'المحاسب', role:'user'}
    ],
    boats: SEED.map(function(b, i) {
      return {
        id: i+1, name: b.n, owner: b.o, phone: b.p,
        area: b.a, pricePerM: b.r, monthlyRent: r2(b.a * b.r),
        start: b.s, end: b.e, deposit: b.d, active: true, notes: ''
      };
    }),
    transactions: [],
    autoLog: {},
    nextTxId: 1,
    nextBoatId: SEED.length + 1
  };
}

function initDB() {
  try {
    ['taraki_marina_v2','taraki_marina_v1','taraki_v1','taraki_v2'].forEach(function(k) {
      localStorage.removeItem(k);
    });
  } catch(e) {}

  var saved = null;
  try { saved = localStorage.getItem(SK); } catch(e) {}

  db = null;
  if (saved) {
    try {
      var parsed = JSON.parse(saved);
      if (parsed && Array.isArray(parsed.boats) && Array.isArray(parsed.users) &&
          Array.isArray(parsed.transactions) && parsed.boats.length > 0) {
        db = parsed;
      }
    } catch(e) { db = null; }
  }

  if (!db) {
    db = freshDB();
    saveDB();
  }

  var hasAdmin = false;
  db.users.forEach(function(u) { if (u.username === 'admin') hasAdmin = true; });
  if (!hasAdmin) {
    db.users.unshift({id:1, username:'admin', password:'taraki2026', name:'المدير', role:'admin'});
    saveDB();
  }

  if (!db.autoLog)    db.autoLog    = {};
  if (!db.nextTxId)   db.nextTxId   = db.transactions.length + 1;
  if (!db.nextBoatId) db.nextBoatId = db.boats.length + 1;
}

function saveDB() {
  try { localStorage.setItem(SK, JSON.stringify(db)); } catch(e) {}
}

function runAutoCharge() {
  var now = new Date();
  var nowY = now.getFullYear();
  var nowM = now.getMonth() + 1;
  var added = [];

  db.boats.forEach(function(boat) {
    if (!boat.active || !(boat.monthlyRent > 0)) return;
    if (!db.autoLog[boat.id]) db.autoLog[boat.id] = [];
    var charged = db.autoLog[boat.id];

    var sd = new Date(boat.start + 'T00:00:00');
    var cy = sd.getFullYear();
    var cm = sd.getMonth() + 1;

    var ey = nowY, em = nowM;
    if (boat.end) {
      var ed = new Date(boat.end + 'T00:00:00');
      var edY = ed.getFullYear(), edM = ed.getMonth() + 1;
      if (edY < ey || (edY === ey && edM < em)) { ey = edY; em = edM; }
    }

    var safety = 0;
    while ((cy < ey || (cy === ey && cm <= em)) && safety < 120) {
      safety++;
      var key = mkey(cy, cm);
      if (charged.indexOf(key) === -1) {
        var dateStr = cy + '-' + (cm < 10 ? '0' + cm : '' + cm) + '-01';
        db.transactions.push({
          id: db.nextTxId++,
          boatId: boat.id,
          type: 'charge',
          desc: 'إيجار شهر ' + AR_MONTHS[cm - 1] + ' ' + cy,
          amount: r2(boat.monthlyRent),
          date: dateStr,
          notes: 'تلقائي',
          auto: true
        });
        charged.push(key);
        added.push(boat.name + ' - ' + AR_MONTHS[cm - 1] + ' ' + cy);
      }
      cm++;
      if (cm > 12) { cm = 1; cy++; }
    }
  });

  if (added.length > 0) saveDB();
  return added;
}

function showAutoBanner(log) {
  var el = document.getElementById('autoBanner');
  if (!el || !log.length) return;
  var sample = log.slice(0, 4).join('، ');
  var more = log.length > 4 ? ' وأخرى (' + (log.length - 4) + '+)' : '';
  el.innerHTML = '<div class="auto-banner"><div style="font-size:1.3rem">⚙</div><div><div style="font-weight:700;color:var(--green)">تم إضافة ' + log.length + ' استحقاق تلقائي</div><div style="font-size:.78rem;color:var(--gray);margin-top:.2rem">' + sample + more + '</div></div></div>';
  setTimeout(function() { el.innerHTML = ''; }, 9000);
}

function doLogin() {
  var u = document.getElementById('loginUser').value.trim();
  var p = document.getElementById('loginPass').value;
  var user = null;
  db.users.forEach(function(x) { if (x.username === u && x.password === p) user = x; });
  if (!user) { document.getElementById('loginError').textContent = 'اسم المستخدم أو كلمة المرور غير صحيحة'; return; }
  cu = user;
  document.getElementById('loginScreen').style.display = 'none';
  document.getElementById('app').style.display = 'block';
  document.getElementById('topbarUser').textContent = user.name + (user.role === 'admin' ? ' (مدير)' : '');
  if (user.role === 'admin') {
    document.querySelectorAll('.admin-only').forEach(function(el) { el.style.display = ''; });
  }
  var autoResult = runAutoCharge();
  populateSelects();
  renderDashboard();
  if (autoResult.length > 0) { setTimeout(function() { showAutoBanner(autoResult); }, 300); }
}

function doLogout() {
  cu = null;
  document.getElementById('loginScreen').style.display = 'flex';
  document.getElementById('app').style.display = 'none';
  document.getElementById('loginUser').value = '';
  document.getElementById('loginPass').value = '';
  document.getElementById('loginError').textContent = '';
  document.querySelectorAll('.admin-only').forEach(function(el) { el.style.display = 'none'; });
}

function showTab(tab) {
  document.querySelectorAll('.nav-tab').forEach(function(el) {
    el.classList.toggle('active', el.getAttribute('data-tab') === tab);
  });
  document.querySelectorAll('.section').forEach(function(s) { s.classList.remove('active'); });
  var map = {dashboard:'secDashboard',boats:'secBoats',payments:'secPayments',reports:'secReports',admin:'secAdmin'};
  var secEl = document.getElementById(map[tab]);
  if (secEl) secEl.classList.add('active');
  if (tab === 'dashboard') renderDashboard();
  else if (tab === 'boats') renderBoats();
  else if (tab === 'payments') renderPayments();
  else if (tab === 'reports') populateReportSelects();
  else if (tab === 'admin') renderAdmin();
}

function getBalance(boatId) {
  var charged = 0, paid = 0;
  db.transactions.forEach(function(t) {
    if (t.boatId !== boatId) return;
    if (t.type === 'charge') charged += t.amount;
    else paid += t.amount;
  });
  return { charged: r2(charged), paid: r2(paid), remaining: r2(charged - paid) };
}

function renderDashboard() {
  var boats = db.boats.filter(function(b) { return b.active; });
  var totC = 0, totP = 0, late = [];
  boats.forEach(function(b) {
    var bal = getBalance(b.id);
    totC += bal.charged; totP += bal.paid;
    if (bal.remaining > 0.005) late.push({b: b, bal: bal});
  });
  document.getElementById('stTotal').textContent = boats.length;
  document.getElementById('stLate').textContent = late.length;
  document.getElementById('stDue').textContent = fmtMoney(r2(totC));
  document.getElementById('stPaid').textContent = fmtMoney(r2(totP));
  document.getElementById('stRem').textContent = fmtMoney(r2(totC - totP));

  var le = document.getElementById('lateList');
  if (!late.length) {
    le.innerHTML = '<p style="color:var(--green);text-align:center;padding:.8rem">جميع المراكب في الوضع الجيد</p>';
  } else {
    late.sort(function(a, b) { return b.bal.remaining - a.bal.remaining; });
    le.innerHTML = late.slice(0, 10).map(function(item) {
      return '<div class="boat-card" onclick="openDetail(' + item.b.id + ')">' +
        '<div style="display:flex;justify-content:space-between;align-items:center">' +
        '<div><div class="boat-name">' + item.b.name + '</div><div class="boat-owner">' + item.b.owner + '</div></div>' +
        '<div class="badge badge-red">' + fmtMoney(item.bal.remaining) + '</div>' +
        '</div></div>';
    }).join('');
    if (late.length > 10) le.innerHTML += '<p style="color:var(--gray);text-align:center;font-size:.8rem">+ ' + (late.length - 10) + ' مركب اخرى</p>';
  }

  var rec = db.transactions.slice().sort(function(a, b) { return new Date(b.date) - new Date(a.date); }).slice(0, 8);
  var re = document.getElementById('recentList');
  re.innerHTML = rec.length ? rec.map(function(t) {
    var bn = '?';
    db.boats.forEach(function(b) { if (b.id === t.boatId) bn = b.name; });
    return '<div class="tx-item ' + t.type + '">' +
      '<div><div class="tx-label">' + bn + ' - ' + t.desc + '</div><div class="tx-date">' + fmtDate(t.date) + '</div></div>' +
      '<div class="tx-amount" style="color:' + (t.type === 'charge' ? 'var(--red)' : 'var(--green)') + '">' + fmtMoney(t.amount) + '</div>' +
      '</div>';
  }).join('') : '<p style="color:var(--gray);text-align:center">لا توجد معاملات</p>';
}

function setFilter(f, el) {
  filterMode = f;
  document.querySelectorAll('.filter-btn').forEach(function(b) { b.classList.remove('active'); });
  el.classList.add('active');
  renderBoats();
}

function renderBoats() {
  var q = (document.getElementById('boatSearch').value || '').toLowerCase();
  var boats = db.boats.filter(function(b) {
    if (!b.active) return false;
    if (q && b.name.toLowerCase().indexOf(q) === -1 && b.owner.toLowerCase().indexOf(q) === -1) return false;
    if (filterMode !== 'all') {
      var rem = getBalance(b.id).remaining;
      if (filterMode === 'late' && !(rem > 0.005)) return false;
      if (filterMode === 'paid' && !(Math.abs(rem) < 0.005)) return false;
      if (filterMode === 'advance' && !(rem < -0.005)) return false;
    }
    return true;
  });
  boats.sort(function(a, b) { return a.name.localeCompare(b.name, 'ar'); });
  var el = document.getElementById('boatList');
  if (!boats.length) { el.innerHTML = '<p style="color:var(--gray);text-align:center;padding:2rem">لا توجد نتائج</p>'; return; }
  el.innerHTML = boats.map(function(b) {
    var bal = getBalance(b.id);
    var sc = bal.remaining > 0.005 ? 'badge-red' : bal.remaining < -0.005 ? 'badge-blue' : 'badge-green';
    var st = bal.remaining > 0.005 ? 'متأخر' : bal.remaining < -0.005 ? 'مقدم' : 'مسدد';
    return '<div class="boat-card" onclick="openDetail(' + b.id + ')">' +
      '<div style="display:flex;justify-content:space-between;align-items:flex-start">' +
      '<div><div class="boat-name">' + b.name + '</div><div class="boat-owner">' + b.owner + (b.phone ? ' · ' + b.phone : '') + '</div></div>' +
      '<span class="badge ' + sc + '">' + st + '</span></div>' +
      '<div class="boat-stats"><span style="color:var(--gray)">المساحة: ' + b.area + 'م</span>' +
      '<span style="color:var(--gold)">' + fmtMoney(b.monthlyRent) + '/شهر</span>' +
      (Math.abs(bal.remaining) > 0.005 ? '<span style="color:' + (bal.remaining > 0 ? 'var(--red)' : 'var(--green)') + '">' + fmtMoney(Math.abs(bal.remaining)) + '</span>' : '') +
      '</div></div>';
  }).join('');
}

function openDetail(id) {
  var b = null;
  db.boats.forEach(function(x) { if (x.id === id) b = x; });
  if (!b) return;
  var bal = getBalance(id);
  var txs = db.transactions.filter(function(t) { return t.boatId === id; });
  txs.sort(function(a, x) { return new Date(a.date) - new Date(x.date); });
  var canEdit = cu && cu.role !== 'viewer';
  var isAdmin = cu && cu.role === 'admin';

  document.getElementById('bdTitle').textContent = b.name;
  var html = '<div class="balance-bar">' +
    '<div class="balance-item"><div class="balance-label">المستحق</div><div class="balance-amount" style="color:var(--red)">' + fmtMoney(bal.charged) + '</div></div>' +
    '<div class="balance-item"><div class="balance-label">المسدد</div><div class="balance-amount" style="color:var(--green)">' + fmtMoney(bal.paid) + '</div></div>' +
    '<div class="balance-item"><div class="balance-label">الرصيد</div><div class="balance-amount" style="color:' + (bal.remaining > 0 ? 'var(--red)' : 'var(--green)') + '">' + fmtMoney(Math.abs(bal.remaining)) + '</div></div>' +
    '</div>';
  html += '<div style="font-size:.82rem;color:var(--gray);margin-bottom:1rem;line-height:1.8">';
  html += '<div>' + b.owner + (b.phone ? ' · ' + b.phone : '') + '</div>';
  html += '<div>' + b.area + 'م x ' + b.pricePerM + ' = <strong style="color:var(--gold)">' + fmtMoney(b.monthlyRent) + '/شهر</strong></div>';
  html += '<div>' + fmtDate(b.start) + ' حتى ' + fmtDate(b.end) + '</div>';
  if (b.deposit) html += '<div>تأمين: ' + fmtMoney(b.deposit) + '</div>';
  html += '</div>';

  if (canEdit) html += '<button class="btn btn-success" style="margin-bottom:1rem" onclick="closeModal(\'boatDetailModal\');openAddTx(' + id + ')">+ تسجيل عملية</button>';

  html += '<div style="font-weight:700;color:var(--aqua);margin-bottom:.6rem">المعاملات (' + txs.length + ')</div>';
  if (!txs.length) {
    html += '<p style="color:var(--gray);text-align:center">لا توجد معاملات بعد</p>';
  } else {
    var run = 0;
    txs.forEach(function(t) {
      run = r2(run + (t.type === 'charge' ? t.amount : -t.amount));
      html += '<div class="tx-item ' + t.type + '">' +
        '<div style="flex:1"><div class="tx-label">' + t.desc + (t.auto ? ' <small style="color:var(--gray)">⚙</small>' : '') + '</div>' +
        '<div class="tx-date">' + fmtDate(t.date) + (t.notes && !t.auto ? ' · ' + t.notes : '') + '</div>' +
        '<div style="font-size:.7rem;color:var(--gray)">رصيد: ' + fmtMoney(run) + '</div></div>' +
        '<div style="display:flex;align-items:center;gap:.4rem">' +
        '<span style="color:' + (t.type === 'charge' ? 'var(--red)' : 'var(--green)') + ';font-weight:700">' + fmtMoney(t.amount) + '</span>' +
        (isAdmin ? '<button onclick="deleteTx(' + t.id + ',' + id + ')" style="background:none;border:none;color:var(--red);font-size:1rem;cursor:pointer;padding:.2rem">X</button>' : '') +
        '</div></div>';
    });
  }

  document.getElementById('bdContent').innerHTML = html;
  openModal('boatDetailModal');
}

function deleteTx(txId, boatId) {
  if (!confirm('حذف هذه المعاملة؟')) return;
  var tx = null;
  db.transactions.forEach(function(t) { if (t.id === txId) tx = t; });
  if (tx && tx.auto && db.autoLog[boatId]) {
    var key = tx.date.slice(0, 7);
    db.autoLog[boatId] = db.autoLog[boatId].filter(function(k) { return k !== key; });
  }
  db.transactions = db.transactions.filter(function(t) { return t.id !== txId; });
  saveDB();
  toast('تم الحذف');
  openDetail(boatId);
  renderDashboard();
}

function openAddTx(preBoatId) {
  if (!cu || cu.role === 'viewer') { toast('ليس لديك صلاحية'); return; }
  document.getElementById('txDate').value = new Date().toISOString().slice(0, 10);
  document.getElementById('txDesc').value = '';
  document.getElementById('txAmount').value = '';
  document.getElementById('txNote').value = '';
  document.getElementById('txErr').textContent = '';
  if (preBoatId) document.getElementById('txBoat').value = preBoatId;
  openModal('addTxModal');
}

function saveTx() {
  var boatId = parseInt(document.getElementById('txBoat').value);
  var type = document.getElementById('txType').value;
  var desc = document.getElementById('txDesc').value.trim();
  var amt = parseFloat(document.getElementById('txAmount').value);
  var date = document.getElementById('txDate').value;
  var note = document.getElementById('txNote').value.trim();
  var err = document.getElementById('txErr');
  if (!boatId)                   { err.textContent = 'اختر المركب'; return; }
  if (!desc)                     { err.textContent = 'أدخل البيان'; return; }
  if (!amt || amt <= 0)          { err.textContent = 'أدخل مبلغاً صحيحاً'; return; }
  if (!date)                     { err.textContent = 'اختر التاريخ'; return; }
  db.transactions.push({id: db.nextTxId++, boatId: boatId, type: type, desc: desc, amount: r2(amt), date: date, notes: note, auto: false});
  saveDB();
  closeModal('addTxModal');
  toast('تم حفظ العملية');
  renderDashboard();
  renderPayments();
}

function renderPayments() {
  var q = (document.getElementById('paySearch').value || '').toLowerCase();
  var txs = db.transactions.slice().sort(function(a, b) { return new Date(b.date) - new Date(a.date); });
  if (q) txs = txs.filter(function(t) {
    var bn = '';
    db.boats.forEach(function(b) { if (b.id === t.boatId) bn = b.name.toLowerCase(); });
    return bn.indexOf(q) !== -1 || t.desc.toLowerCase().indexOf(q) !== -1;
  });
  var tb = document.getElementById('payTable');
  tb.innerHTML = txs.length ? txs.map(function(t) {
    var bn = '?';
    db.boats.forEach(function(b) { if (b.id === t.boatId) bn = b.name; });
    return '<tr><td>' + fmtDate(t.date) + '</td><td>' + bn + '</td><td>' + t.desc + '</td>' +
      '<td style="color:' + (t.type === 'charge' ? 'var(--red)' : 'var(--green)') + ';font-weight:700">' + fmtMoney(t.amount) + '</td>' +
      '<td><span class="badge ' + (t.type === 'charge' ? 'badge-red' : 'badge-green') + '">' + (t.type === 'charge' ? 'استحقاق' : 'تحصيل') + '</span></td></tr>';
  }).join('') : '<tr><td colspan="5" style="text-align:center;color:var(--gray)">لا توجد معاملات</td></tr>';
}

function populateSelects() {
  var boats = db.boats.filter(function(b) { return b.active; }).sort(function(a, b) { return a.name.localeCompare(b.name, 'ar'); });
  var opts = boats.map(function(b) { return '<option value="' + b.id + '">' + b.name + ' - ' + b.owner + '</option>'; }).join('');
  var tx = document.getElementById('txBoat');
  if (tx) tx.innerHTML = '<option value="">اختر مركب...</option>' + opts;
}

function populateReportSelects() {
  var boats = db.boats.filter(function(b) { return b.active; }).sort(function(a, b) { return a.name.localeCompare(b.name, 'ar'); });
  var opts = boats.map(function(b) { return '<option value="' + b.id + '">' + b.name + ' - ' + b.owner + '</option>'; }).join('');
  document.getElementById('rptBoat').innerHTML = '<option value="all">جميع المراكب</option>' + opts;
  document.getElementById('stmtBoat').innerHTML = '<option value="">اختر مركب...</option>' + opts;
  populateSelects();
}

function generateReport() {
  var val = document.getElementById('rptBoat').value;
  var boats = val === 'all' ? db.boats.filter(function(b) { return b.active; }) : db.boats.filter(function(b) { return b.id === parseInt(val); });
  var totC = 0, totP = 0;
  var rows = boats.map(function(b) {
    var bal = getBalance(b.id);
    totC += bal.charged; totP += bal.paid;
    var sc = bal.remaining > 0.005 ? 'badge-red' : bal.remaining < -0.005 ? 'badge-blue' : 'badge-green';
    var st = bal.remaining > 0.005 ? 'متأخر' : bal.remaining < -0.005 ? 'مقدم' : 'مسدد';
    return '<tr><td>' + b.name + '</td><td style="font-size:.78rem">' + b.owner + '</td><td>' + fmtMoney(b.monthlyRent) + '</td>' +
      '<td style="color:var(--red)">' + fmtMoney(bal.charged) + '</td>' +
      '<td style="color:var(--green)">' + fmtMoney(bal.paid) + '</td>' +
      '<td style="color:' + (bal.remaining > 0 ? 'var(--red)' : bal.remaining < 0 ? 'var(--aqua)' : 'var(--green)') + '">' + fmtMoney(Math.abs(bal.remaining)) + '</td>' +
      '<td><span class="badge ' + sc + '">' + st + '</span></td></tr>';
  }).join('');
  document.getElementById('rptResult').innerHTML = '<div class="card"><div class="tbl-wrap"><table>' +
    '<thead><tr><th>المركب</th><th>المالك</th><th>إيجار/شهر</th><th>المستحق</th><th>المسدد</th><th>الرصيد</th><th>الحالة</th></tr></thead>' +
    '<tbody>' + rows + '<tr style="font-weight:700;background:rgba(255,255,255,.05)">' +
    '<td colspan="3">الإجمالي (' + boats.length + ' مركب)</td>' +
    '<td style="color:var(--red)">' + fmtMoney(r2(totC)) + '</td>' +
    '<td style="color:var(--green)">' + fmtMoney(r2(totP)) + '</td>' +
    '<td style="color:' + (totC - totP > 0 ? 'var(--red)' : 'var(--green)') + '">' + fmtMoney(Math.abs(r2(totC - totP))) + '</td>' +
    '<td></td></tr></tbody></table></div></div>';
}

function showStatement() {
  var id = parseInt(document.getElementById('stmtBoat').value);
  if (!id) { toast('اختر مركباً أولاً'); return; }
  var b = null; db.boats.forEach(function(x) { if (x.id === id) b = x; });
  var bal = getBalance(id);
  var txs = db.transactions.filter(function(t) { return t.boatId === id; }).sort(function(a, x) { return new Date(a.date) - new Date(x.date); });
  var run = 0;
  var rows = txs.map(function(t, i) {
    run = r2(run + (t.type === 'charge' ? t.amount : -t.amount));
    return '<tr><td>' + (i + 1) + '</td><td>' + fmtDate(t.date) + '</td><td>' + t.desc + (t.auto ? ' ⚙' : '') + '</td>' +
      '<td style="color:var(--red)">' + (t.type === 'charge' ? fmtMoney(t.amount) : '-') + '</td>' +
      '<td style="color:var(--green)">' + (t.type === 'payment' ? fmtMoney(t.amount) : '-') + '</td>' +
      '<td style="color:' + (run > 0 ? 'var(--red)' : 'var(--green)') + ';font-weight:700">' + fmtMoney(run) + '</td></tr>';
  }).join('');
  document.getElementById('stmtResult').innerHTML = '<div class="card">' +
    '<div style="text-align:center;margin-bottom:1rem"><div style="font-size:1.1rem;font-weight:800;color:var(--aqua)">الميناء السياحي - التراكي</div><div style="font-size:.82rem;color:var(--gray)">كشف حساب</div></div>' +
    '<div style="background:var(--sea);border-radius:10px;padding:.8rem;font-size:.82rem;margin-bottom:1rem;line-height:1.8">' +
    '<div><strong>المركب:</strong> ' + b.name + ' &nbsp; <strong>المالك:</strong> ' + b.owner + '</div>' +
    (b.phone ? '<div><strong>الهاتف:</strong> ' + b.phone + '</div>' : '') +
    '<div><strong>الإيجار الشهري:</strong> <span style="color:var(--gold)">' + fmtMoney(b.monthlyRent) + '</span></div>' +
    '<div>' + fmtDate(b.start) + ' حتى ' + fmtDate(b.end) + '</div></div>' +
    '<div class="tbl-wrap"><table><thead><tr><th>#</th><th>التاريخ</th><th>البيان</th><th>مدين</th><th>دائن</th><th>الرصيد</th></tr></thead><tbody>' + rows + '</tbody></table></div>' +
    '<div style="background:var(--sea);border-radius:10px;padding:.8rem;margin-top:1rem;font-size:.88rem">' +
    '<div style="display:flex;justify-content:space-between"><span>المستحق</span><strong style="color:var(--red)">' + fmtMoney(bal.charged) + '</strong></div>' +
    '<div style="display:flex;justify-content:space-between"><span>المسدد</span><strong style="color:var(--green)">' + fmtMoney(bal.paid) + '</strong></div>' +
    '<div style="border-top:1px solid rgba(255,255,255,.1);margin:.5rem 0"></div>' +
    '<div style="display:flex;justify-content:space-between;font-size:1rem"><strong>' + (bal.remaining > 0 ? 'المطلوب' : bal.remaining < 0 ? 'رصيد مقدم' : 'الرصيد') + '</strong>' +
    '<strong style="color:' + (bal.remaining > 0 ? 'var(--red)' : 'var(--green)') + '">' + fmtMoney(Math.abs(bal.remaining)) + '</strong></div></div></div>';
}

function saveNewBoat() {
  var name  = document.getElementById('nb_name').value.trim();
  var owner = document.getElementById('nb_owner').value.trim();
  var phone = document.getElementById('nb_phone').value.trim();
  var area  = parseFloat(document.getElementById('nb_area').value);
  var price = parseFloat(document.getElementById('nb_price').value);
  var start = document.getElementById('nb_start').value;
  var end   = document.getElementById('nb_end').value;
  var dep   = parseFloat(document.getElementById('nb_deposit').value || 0);
  var err   = document.getElementById('nbErr');
  if (!name)      { err.textContent = 'أدخل اسم المركب'; return; }
  if (!owner)     { err.textContent = 'أدخل اسم المالك'; return; }
  if (!(area>0))  { err.textContent = 'أدخل المساحة'; return; }
  if (!(price>0)) { err.textContent = 'أدخل سعر المتر'; return; }
  if (!start)     { err.textContent = 'أدخل تاريخ البداية'; return; }
  var dup = false; db.boats.forEach(function(b) { if (b.name === name) dup = true; });
  if (dup) { err.textContent = 'هذا الاسم موجود مسبقاً'; return; }
  db.boats.push({id: db.nextBoatId++, name: name, owner: owner, phone: phone, area: r2(area), pricePerM: price, monthlyRent: r2(area * price), start: start, end: end || '', deposit: r2(dep || 0), active: true, notes: ''});
  saveDB();
  closeModal('addBoatModal');
  toast('تمت إضافة المركب');
  populateSelects();
  renderBoats();
}

function renderAdmin() {
  var ul = document.getElementById('userList');
  ul.innerHTML = db.users.map(function(u) {
    var roleL = u.role === 'admin' ? 'مدير' : u.role === 'user' ? 'مستخدم' : 'مشاهدة فقط';
    return '<div style="display:flex;justify-content:space-between;align-items:center;padding:.65rem;background:rgba(255,255,255,.03);border-radius:8px;margin-bottom:.4rem">' +
      '<div><div style="font-weight:700">' + u.name + '</div><div style="font-size:.78rem;color:var(--gray)">' + u.username + ' · ' + roleL + '</div></div>' +
      (u.id !== cu.id ? '<button onclick="delUser(' + u.id + ')" style="background:none;border:none;color:var(--red);cursor:pointer;font-size:1rem;padding:.2rem">X</button>' : '<span style="font-size:.7rem;color:var(--gold)">أنت</span>') +
      '</div>';
  }).join('');
  document.getElementById('userCount').textContent = db.users.length + ' / ' + MAX_USERS + ' مستخدمين';
}

function delUser(id) {
  if (!confirm('حذف هذا المستخدم؟')) return;
  db.users = db.users.filter(function(u) { return u.id !== id; });
  saveDB(); renderAdmin(); toast('تم الحذف');
}

function saveNewUser() {
  var uname = document.getElementById('nu_user').value.trim();
  var pass  = document.getElementById('nu_pass').value;
  var name  = document.getElementById('nu_name').value.trim();
  var role  = document.getElementById('nu_role').value;
  var err   = document.getElementById('nuErr');
  if (!uname)         { err.textContent = 'أدخل اسم المستخدم'; return; }
  if (pass.length<3)  { err.textContent = 'كلمة المرور قصيرة'; return; }
  if (!name)          { err.textContent = 'أدخل الاسم'; return; }
  var dup = false; db.users.forEach(function(u) { if (u.username === uname) dup = true; });
  if (dup) { err.textContent = 'اسم المستخدم مستخدم'; return; }
  if (db.users.length >= MAX_USERS) { err.textContent = 'الحد الأقصى ' + MAX_USERS; return; }
  var maxId = 0; db.users.forEach(function(u) { if (u.id > maxId) maxId = u.id; });
  db.users.push({id: maxId + 1, username: uname, password: pass, name: name, role: role});
  saveDB(); closeModal('addUserModal'); toast('تمت إضافة المستخدم'); renderAdmin();
}

function showAutoLog() {
  var panel = document.getElementById('autoLogPanel');
  var boats = db.boats.filter(function(b) { return b.active && db.autoLog[b.id] && db.autoLog[b.id].length; });
  if (!boats.length) { panel.innerHTML = '<p style="color:var(--gray);font-size:.85rem">لا يوجد سجل بعد.</p>'; return; }
  var html = '<div style="max-height:300px;overflow-y:auto">';
  boats.sort(function(a, b) { return a.name.localeCompare(b.name, 'ar'); }).forEach(function(b) {
    var months = db.autoLog[b.id];
    html += '<div style="margin-bottom:.7rem;background:rgba(255,255,255,.03);border-radius:8px;padding:.65rem">' +
      '<div style="font-weight:700;font-size:.85rem;color:var(--aqua);margin-bottom:.35rem">' + b.name + '</div>' +
      '<div style="display:flex;flex-wrap:wrap;gap:.3rem">' +
      months.map(function(k) {
        var parts = k.split('-'); var m = parseInt(parts[1]); var y = parts[0];
        return '<span class="badge badge-blue">' + AR_MONTHS[m - 1] + ' ' + y + '</span>';
      }).join('') + '</div></div>';
  });
  html += '</div>';
  panel.innerHTML = html;
}

function resetAutoLog() {
  if (!confirm('سيتم حذف سجل الأشهر المحتسبة وإعادة احتسابها.\nهل أنت متأكد؟')) return;
  db.autoLog = {}; saveDB(); toast('تم إعادة التعيين');
  document.getElementById('autoLogPanel').innerHTML = '';
}

function exportData() {
  var blob = new Blob([JSON.stringify(db, null, 2)], {type: 'application/json'});
  var a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = 'taraki_' + new Date().toISOString().slice(0, 10) + '.json';
  a.click(); URL.revokeObjectURL(a.href);
  toast('تم تصدير البيانات');
}

function importData(e) {
  var f = e.target.files[0]; if (!f) return;
  var reader = new FileReader();
  reader.onload = function(ev) {
    try {
      var imp = JSON.parse(ev.target.result);
      if (!imp.boats || !imp.users || !imp.transactions) throw new Error('ملف غير صالح');
      if (!confirm('سيتم استبدال جميع البيانات. هل أنت متأكد؟')) return;
      db = imp; if (!db.autoLog) db.autoLog = {};
      saveDB(); toast('تم الاستيراد'); populateSelects(); renderDashboard();
    } catch(err) { toast('خطأ: ' + err.message); }
  };
  reader.readAsText(f);
}

function openModal(id)  { document.getElementById(id).classList.add('open'); }
function closeModal(id) { document.getElementById(id).classList.remove('open'); }

function toast(msg) {
  var el = document.getElementById('toast');
  el.textContent = msg; el.style.display = 'block';
  setTimeout(function() { el.style.display = 'none'; }, 3000);
}

function hardReset() {
  if (!confirm('سيتم حذف جميع البيانات المحفوظة وإعادة التهيئة من الصفر.\nهل أنت متأكد تماماً؟')) return;
  try {
    var keys = ['taraki_v3','taraki_v2','taraki_v1','taraki_marina_v2','taraki_marina_v1'];
    keys.forEach(function(k) { localStorage.removeItem(k); });
    localStorage.clear();
  } catch(e) {}
  location.reload();
}

// Event Listeners
document.addEventListener('DOMContentLoaded', function() {
  initDB();
  document.getElementById('loginPass').addEventListener('keyup', function(e) { if (e.key === 'Enter') doLogin(); });
  document.querySelectorAll('.modal-overlay').forEach(function(el) {
    el.addEventListener('click', function(e) { if (e.target === el) el.classList.remove('open'); });
  });
});
</script>
</body>
</html>l 
