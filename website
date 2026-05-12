
<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>KI-Reifegradmodell · ARCMM</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}

:root{
  --blue-50:#EFF6FF;
  --blue-100:#DBEAFE;
  --blue-200:#BFDBFE;
  --blue-300:#93C5FD;
  --blue-400:#60A5FA;
  --blue-500:#3B82F6;
  --blue-600:#2563EB;
  --blue-700:#1D4ED8;
  --blue-800:#1E40AF;
  --blue-900:#1E3A8A;
  --slate-50:#F8FAFC;
  --slate-100:#F1F5F9;
  --slate-200:#E2E8F0;
  --slate-300:#CBD5E1;
  --slate-400:#94A3B8;
  --slate-500:#64748B;
  --slate-600:#475569;
  --slate-700:#334155;
  --slate-800:#1E293B;
  --slate-900:#0F172A;
  --green-50:#F0FDF4;
  --green-100:#DCFCE7;
  --green-600:#16A34A;
  --green-700:#15803D;
  --amber-50:#FFFBEB;
  --amber-100:#FEF3C7;
  --amber-600:#D97706;
  --red-50:#FEF2F2;
  --red-100:#FEE2E2;
  --red-600:#DC2626;

  --bg:#F8FAFC;
  --surface:#FFFFFF;
  --surface-raised:#FFFFFF;
  --text:#1E293B;
  --text-muted:#64748B;
  --text-faint:#94A3B8;
  --border:#E2E8F0;
  --border-focus:#2563EB;
  --accent:#2563EB;
  --accent-light:#DBEAFE;
  --radius-sm:6px;
  --radius-md:10px;
  --radius-lg:14px;
  --radius-xl:20px;
  --font:'Inter',-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;
  --shadow-sm:0 1px 3px rgba(15,23,42,.06),0 1px 2px rgba(15,23,42,.04);
  --shadow-md:0 4px 6px rgba(15,23,42,.07),0 2px 4px rgba(15,23,42,.05);
}

@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

@media(prefers-color-scheme:dark){
  :root{
    --bg:#0F172A;
    --surface:#1E293B;
    --surface-raised:#253348;
    --text:#E2E8F0;
    --text-muted:#94A3B8;
    --text-faint:#475569;
    --border:#2D3F55;
    --border-focus:#3B82F6;
    --accent:#3B82F6;
    --accent-light:#1E3A8A;
    --shadow-sm:0 1px 3px rgba(0,0,0,.3);
    --shadow-md:0 4px 6px rgba(0,0,0,.4);
  }
}

html,body{height:100%;background:var(--bg);color:var(--text);font-family:var(--font);font-size:15px;line-height:1.6;-webkit-font-smoothing:antialiased}

.app{max-width:960px;margin:0 auto;padding:2rem 1.25rem 5rem}
.screen{display:none}
.screen.active{display:block}

.topnav{display:flex;align-items:center;justify-content:space-between;margin-bottom:2.5rem;padding-bottom:1.25rem;border-bottom:1px solid var(--border)}
.topnav-brand{display:flex;align-items:center;gap:10px}
.brand-mark{width:32px;height:32px;background:var(--accent);border-radius:var(--radius-sm);display:flex;align-items:center;justify-content:center}
.brand-mark svg{width:18px;height:18px;fill:none;stroke:#fff;stroke-width:2;stroke-linecap:round;stroke-linejoin:round}
.brand-name{font-size:15px;font-weight:700;letter-spacing:-.2px;color:var(--text)}
.brand-sub{font-size:11px;color:var(--text-muted);margin-top:-1px}
.lang-toggle{display:flex;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-md);overflow:hidden;box-shadow:var(--shadow-sm)}
.lang-btn{padding:6px 14px;font-size:12px;font-weight:600;cursor:pointer;border:none;background:transparent;color:var(--text-muted);font-family:var(--font);letter-spacing:.3px;transition:all .15s}
.lang-btn.active{background:var(--accent);color:#fff}

.page-header{margin-bottom:2rem}
.page-header h1{font-size:26px;font-weight:700;letter-spacing:-.4px;line-height:1.25;color:var(--text)}
.page-header p{font-size:13px;color:var(--text-muted);margin-top:6px}
.intro-text{font-size:13px;color:var(--text-muted);line-height:1.75;margin-bottom:2rem;max-width:680px;padding:1rem 1.25rem;background:var(--accent-light);border-radius:var(--radius-md);border-left:3px solid var(--accent)}

.section-label{font-size:11px;font-weight:700;letter-spacing:.8px;text-transform:uppercase;color:var(--text-faint);margin-bottom:.75rem;margin-top:2rem}

.orgs-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:12px;margin-bottom:1.5rem}
.org-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:1.1rem 1.25rem;cursor:pointer;transition:border-color .15s,box-shadow .15s;box-shadow:var(--shadow-sm)}
.org-card:hover{border-color:var(--blue-300);box-shadow:var(--shadow-md)}
.org-card.selected{border-color:var(--accent);box-shadow:0 0 0 3px var(--accent-light)}
.org-card.add-new{border-style:dashed;display:flex;align-items:center;justify-content:center;gap:8px;color:var(--text-faint);font-size:13px;min-height:90px;cursor:pointer}
.org-card.add-new:hover{border-color:var(--accent);color:var(--accent)}
.org-name{font-size:14px;font-weight:600;color:var(--text);margin-bottom:2px}
.org-meta{font-size:12px;color:var(--text-muted);margin-bottom:10px}

.profiles-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(210px,1fr));gap:10px;margin-bottom:1.5rem}
.profile-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:1rem 1.1rem;cursor:pointer;transition:border-color .15s,box-shadow .15s;box-shadow:var(--shadow-sm)}
.profile-card:hover{border-color:var(--blue-300);box-shadow:var(--shadow-md)}
.profile-card.completed{border-color:var(--green-600)}
.profile-card.add-new{border-style:dashed;display:flex;align-items:center;justify-content:center;gap:8px;color:var(--text-faint);font-size:13px;min-height:88px}
.profile-card.add-new:hover{border-color:var(--accent);color:var(--accent)}
.profile-name{font-size:13px;font-weight:600;color:var(--text)}
.profile-role{font-size:11px;color:var(--text-muted);margin-top:1px;margin-bottom:8px}
.profile-avatar{width:34px;height:34px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;flex-shrink:0}

.badge{font-size:10px;padding:2px 8px;border-radius:20px;display:inline-flex;align-items:center;gap:3px;font-weight:600;letter-spacing:.1px}
.badge-done{background:var(--green-100);color:var(--green-700)}
.badge-partial{background:var(--amber-100);color:var(--amber-600)}
.badge-empty{background:var(--slate-100);color:var(--slate-500)}

.btn{display:inline-flex;align-items:center;gap:6px;padding:9px 18px;border-radius:var(--radius-md);border:1px solid var(--border);background:var(--surface);font-size:13px;font-weight:500;cursor:pointer;color:var(--text);font-family:var(--font);transition:all .12s;box-shadow:var(--shadow-sm);white-space:nowrap}
.btn:hover{border-color:var(--blue-300);background:var(--blue-50)}
.btn-primary{background:var(--accent);color:#fff;border-color:transparent;box-shadow:0 2px 4px rgba(37,99,235,.3)}
.btn-primary:hover{background:var(--blue-700);border-color:transparent}
.btn-sm{padding:6px 13px;font-size:12px}
.btn-ghost{border-color:transparent;box-shadow:none;background:transparent;color:var(--text-muted)}
.btn-ghost:hover{background:var(--surface);border-color:var(--border)}
.btn-danger{color:var(--red-600);border-color:var(--red-100)}
.btn-danger:hover{background:var(--red-50)}
.btn-group{display:flex;gap:8px;flex-wrap:wrap;align-items:center}

.modal-overlay{position:fixed;inset:0;background:rgba(15,23,42,.55);backdrop-filter:blur(2px);display:flex;align-items:center;justify-content:center;z-index:300;padding:1rem}
.modal{background:var(--surface);border-radius:var(--radius-xl);padding:2rem;max-width:440px;width:100%;border:1px solid var(--border);box-shadow:0 20px 40px rgba(15,23,42,.15)}
.modal h2{font-size:18px;font-weight:700;margin-bottom:1.5rem;letter-spacing:-.2px}
.form-group{margin-bottom:1.1rem}
.form-group label{display:block;font-size:11px;font-weight:700;letter-spacing:.5px;text-transform:uppercase;color:var(--text-muted);margin-bottom:5px}
.form-group input,.form-group select{width:100%;padding:10px 13px;border-radius:var(--radius-md);border:1px solid var(--border);background:var(--bg);color:var(--text);font-size:14px;font-family:var(--font);outline:none;transition:border-color .15s}
.form-group input:focus,.form-group select:focus{border-color:var(--border-focus);box-shadow:0 0 0 3px rgba(37,99,235,.12)}
.modal-actions{display:flex;justify-content:flex-end;gap:8px;margin-top:1.75rem}

.survey-topbar{display:flex;align-items:center;gap:12px;margin-bottom:1.75rem}
.survey-who{font-size:14px;font-weight:600;color:var(--text)}
.survey-org-tag{font-size:11px;padding:2px 8px;background:var(--accent-light);color:var(--accent);border-radius:20px;font-weight:600}

.progress-wrap{display:flex;align-items:center;gap:12px;margin-bottom:2rem}
.progress-track{flex:1;height:4px;background:var(--slate-200);border-radius:2px;overflow:hidden}
.progress-fill{height:100%;background:var(--accent);border-radius:2px;transition:width .4s ease}
.progress-label{font-size:12px;color:var(--text-faint);min-width:50px;text-align:right;font-weight:500}

.cap-section{margin-bottom:2.5rem}
.cap-header{display:flex;align-items:center;gap:10px;font-size:14px;font-weight:700;padding:10px 16px;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-md);margin-bottom:1.1rem;box-shadow:var(--shadow-sm)}
.cap-dot{width:10px;height:10px;border-radius:50%;flex-shrink:0}

.q-block{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:1.25rem 1.4rem;margin-bottom:.9rem;box-shadow:var(--shadow-sm);transition:border-color .15s}
.q-block:hover{border-color:var(--slate-300)}
.lens-tag{display:inline-flex;font-size:10px;font-weight:700;padding:3px 9px;border-radius:20px;margin-bottom:9px;letter-spacing:.3px;text-transform:uppercase}
.q-text{font-size:14px;font-weight:600;color:var(--text);margin-bottom:5px;line-height:1.45}
.q-desc{font-size:12px;color:var(--text-muted);margin-bottom:14px;line-height:1.65}
.opts-row{display:flex;flex-wrap:wrap;gap:7px}
.opt{padding:6px 14px;border-radius:var(--radius-md);border:1px solid var(--border);background:var(--bg);font-size:12px;cursor:pointer;color:var(--text-muted);font-family:var(--font);font-weight:500;transition:all .12s;white-space:nowrap}
.opt:hover{border-color:var(--blue-300);color:var(--blue-700);background:var(--blue-50)}
.opt.selected{background:var(--accent);color:#fff;border-color:transparent;box-shadow:0 2px 4px rgba(37,99,235,.25)}
.opt.unable.selected{background:var(--slate-200);color:var(--slate-500);border-color:var(--slate-300);box-shadow:none}

.r-block{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:1.25rem 1.4rem;margin-bottom:.9rem;box-shadow:var(--shadow-sm)}
.r-label{font-size:14px;font-weight:600;margin-bottom:10px;line-height:1.4}
.r-block textarea{width:100%;min-height:85px;padding:10px 13px;font-size:13px;font-family:var(--font);border:1px solid var(--border);border-radius:var(--radius-md);background:var(--bg);color:var(--text);resize:vertical;outline:none;line-height:1.6}
.r-block textarea:focus{border-color:var(--border-focus)}
.rating-row{display:flex;align-items:center;gap:12px;margin-top:10px}
.rating-row input[type=range]{flex:1;accent-color:var(--accent)}
.rating-val{font-size:20px;font-weight:700;min-width:26px;color:var(--accent)}

.survey-footer{display:flex;justify-content:space-between;align-items:center;margin-top:2.5rem;padding-top:1.5rem;border-top:1px solid var(--border)}
.footer-note{font-size:12px;color:var(--text-faint)}

.tab-bar{display:flex;gap:4px;background:var(--surface);border:1px solid var(--border);padding:4px;border-radius:var(--radius-lg);margin-bottom:1.75rem;overflow-x:auto;box-shadow:var(--shadow-sm);flex-wrap:wrap}
.tab{padding:7px 16px;border-radius:var(--radius-md);font-size:12px;font-weight:600;cursor:pointer;border:none;background:transparent;color:var(--text-muted);font-family:var(--font);white-space:nowrap;transition:all .12s;letter-spacing:.1px}
.tab.active{background:var(--accent);color:#fff;box-shadow:0 2px 4px rgba(37,99,235,.25)}
.tab.org-tab{font-size:11px;padding:6px 12px}

.metric-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(170px,1fr));gap:10px;margin-bottom:1.5rem}
.metric-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:1.1rem 1.25rem;box-shadow:var(--shadow-sm)}
.metric-cap{font-size:10px;font-weight:700;letter-spacing:.4px;text-transform:uppercase;color:var(--text-muted);margin-bottom:5px}
.metric-score{font-size:28px;font-weight:700;line-height:1;letter-spacing:-.5px}
.metric-denom{font-size:13px;color:var(--text-faint);font-weight:400}

.chart-grid{display:grid;grid-template-columns:1fr 1fr;gap:1.25rem;margin-bottom:1.5rem}
@media(max-width:620px){.chart-grid{grid-template-columns:1fr}}
.chart-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:1.25rem;box-shadow:var(--shadow-sm)}
.chart-title{font-size:12px;font-weight:700;letter-spacing:.2px;text-transform:uppercase;color:var(--text-muted);margin-bottom:1rem}
.chart-wrap{position:relative;height:270px}

.score-table{width:100%;border-collapse:collapse;font-size:12px;margin-bottom:1.5rem}
.score-table th{text-align:left;padding:8px 12px;color:var(--text-faint);font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.5px;border-bottom:1px solid var(--border)}
.score-table td{padding:10px 12px;border-bottom:1px solid var(--border);color:var(--text)}
.score-table tr:last-child td{border-bottom:none}
.mini-bar{height:5px;background:var(--slate-100);border-radius:3px;overflow:hidden;width:70px;display:inline-block;vertical-align:middle;margin-left:6px}
.mini-fill{height:100%;border-radius:3px}

.locked-box{display:flex;flex-direction:column;align-items:center;justify-content:center;padding:4.5rem 2rem;text-align:center;background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-xl);box-shadow:var(--shadow-sm)}
.locked-icon{width:52px;height:52px;background:var(--slate-100);border-radius:50%;display:flex;align-items:center;justify-content:center;margin-bottom:1.25rem;font-size:22px}
.locked-box h3{font-size:17px;font-weight:700;margin-bottom:6px;letter-spacing:-.2px}
.locked-box p{font-size:13px;color:var(--text-muted);line-height:1.7;max-width:360px}

.comp-block{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-lg);padding:1.1rem 1.25rem;margin-bottom:1rem;box-shadow:var(--shadow-sm)}
.comp-cap-title{font-size:11px;font-weight:700;letter-spacing:.3px;text-transform:uppercase;color:var(--text-muted);margin-bottom:12px}
.comp-row{display:flex;align-items:center;gap:10px;margin-bottom:8px}
.comp-name{font-size:12px;color:var(--text-muted);min-width:140px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.comp-bar-track{flex:1;height:5px;background:var(--slate-100);border-radius:3px;overflow:hidden}
.comp-bar-fill{height:100%;border-radius:3px}
.comp-val{font-size:12px;font-weight:600;min-width:32px;text-align:right}

.section-title{font-size:11px;font-weight:700;letter-spacing:.6px;text-transform:uppercase;color:var(--text-faint);margin-bottom:.75rem;margin-top:2rem}

.org-section-header{display:flex;align-items:center;gap:10px;padding:12px 16px;background:var(--accent-light);border:1px solid var(--blue-200);border-radius:var(--radius-md);margin-bottom:1rem;margin-top:1.5rem}
.org-section-icon{width:28px;height:28px;background:var(--accent);border-radius:var(--radius-sm);display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700;color:#fff;flex-shrink:0}
.org-section-name{font-size:13px;font-weight:700;color:var(--accent)}
.org-section-meta{font-size:11px;color:var(--blue-600);margin-left:auto}

footer{text-align:center;padding:2rem;font-size:11px;color:var(--text-faint);border-top:1px solid var(--border);margin-top:3rem;letter-spacing:.3px}

::-webkit-scrollbar{width:6px;height:6px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:var(--slate-300);border-radius:3px}

.login-screen{
  position:fixed;
  inset:0;
  background:rgba(248,250,252,.96);
  display:flex;
  align-items:center;
  justify-content:center;
  z-index:9999;
  padding:1rem;
}
@media(prefers-color-scheme:dark){
  .login-screen{
    background:rgba(15,23,42,.96);
  }
}
.login-card{
  width:100%;
  max-width:420px;
  background:var(--surface);
  border:1px solid var(--border);
  border-radius:var(--radius-xl);
  box-shadow:0 20px 40px rgba(15,23,42,.15);
  padding:2rem;
}
.login-card h2{
  font-size:22px;
  font-weight:700;
  margin-bottom:.5rem;
  letter-spacing:-.3px;
}
.login-card p{
  font-size:13px;
  color:var(--text-muted);
  margin-bottom:1.5rem;
  line-height:1.6;
}
.login-error{
  display:none;
  margin-top:.85rem;
  font-size:12px;
  color:var(--red-600);
}
.login-error.show{
  display:block;
}
.hidden-app{
  display:none;
}
</style>
</head>
<body>

<div id="login-screen" class="login-screen">
  <div class="login-card">
    <h2>Anmeldung</h2>
    <p>Bitte melden Sie sich an, um auf die Ai readinesssbewertung zuzugreifen.</p>

    <div class="form-group">
      <label for="login-user">Benutzername</label>
      <input type="text" id="login-user" autocomplete="username" />
    </div>

    <div class="form-group">
      <label for="login-pass">Passwort</label>
      <input type="password" id="login-pass" autocomplete="current-password" />
    </div>

    <div class="modal-actions" style="margin-top:1.25rem;">
      <button class="btn btn-primary" onclick="handleLogin()">Login</button>
    </div>

    <div id="login-error" class="login-error">
      Benutzername oder Passwort ist falsch.
    </div>
  </div>
</div>

<div class="app hidden-app" id="app-root">

<div id="screen-home" class="screen active">
  <nav class="topnav">
    <div class="topnav-brand">
      <div class="brand-mark">
        <svg viewBox="0 0 24 24"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
      </div>
      <div>
        <div class="brand-name">ARCMM</div>
        <div class="brand-sub" data-de="KI-Reifegradmodell" data-en="AI Readiness Maturity Model">KI-Reifegradmodell</div>
      </div>
    </div>
    <div style="display:flex;align-items:center;gap:12px;">
      <div class="lang-toggle">
        <button class="lang-btn active" id="btn-de" onclick="setLang('de')">DE</button>
        <button class="lang-btn" id="btn-en" onclick="setLang('en')">EN</button>
      </div>
    </div>
  </nav>

  <div class="page-header">
    <h1 data-de="Ai readiness assessment" data-en="AI Readiness Assessment">Ai readiness assessment</h1>
    <p data-de="Organizational AI Readiness Capability Maturity Model (ARCMM) · März 2026" data-en="Organizational AI Readiness Capability Maturity Model (ARCMM) · March 2026">Organizational AI Readiness Capability Maturity Model (ARCMM) · März 2026</p>
  </div>

  <p class="intro-text" data-de="Diese Erhebung bewertet die Ai readiness Ihrer Organisation in fünf Fähigkeitsbereichen, betrachtet durch drei Linsen: individuelle Akteure, digitale Technologien und Interaktionsmuster. Organisationen können bis zu 6 Befragte haben. Das aggregierte Radar wird erst sichtbar, wenn alle Befragten einer Organisation die Erhebung abgeschlossen haben." data-en="This survey assesses your organization's AI readiness across five capability areas, viewed through three lenses: individual actors, digital technologies, and interactional patterns. Organizations can have up to 6 respondents. The aggregate radar becomes visible once all respondents within an organization have completed the survey.">Diese Erhebung bewertet die Ai readiness Ihrer Organisation in fünf Fähigkeitsbereichen, betrachtet durch drei Linsen: individuelle Akteure, digitale Technologien und Interaktionsmuster. Organisationen können bis zu 6 Befragte haben. Das aggregierte Radar wird erst sichtbar, wenn alle Befragten einer Organisation die Erhebung abgeschlossen haben.</p>

  <p class="section-label" data-de="Organisationen" data-en="Organizations">Organisationen</p>
  <div class="orgs-grid" id="orgs-grid"></div>

  <div id="org-detail" style="display:none;">
    <div id="org-detail-header"></div>
    <p class="section-label" data-de="Befragte" data-en="Respondents">Befragte</p>
    <div class="profiles-grid" id="profiles-grid"></div>
  </div>

  <div class="btn-group" style="margin-top:.5rem">
    <button class="btn btn-primary" onclick="showResults()" data-de="Ergebnisse anzeigen" data-en="View results">Ergebnisse anzeigen</button>
    <button class="btn" onclick="exportData()" data-de="JSON exportieren" data-en="Export JSON">JSON exportieren</button>
    <button class="btn btn-ghost" onclick="resetAll()" data-de="Alles zurücksetzen" data-en="Reset all">Alles zurücksetzen</button>
  </div>
</div>

<div id="screen-survey" class="screen">
  <div class="survey-topbar">
    <button class="btn btn-sm btn-ghost" onclick="goHome()">← <span data-de="Zurück" data-en="Back">Zurück</span></button>
    <span class="survey-who" id="survey-who"></span>
    <span class="survey-org-tag" id="survey-org-tag"></span>
  </div>
  <div class="progress-wrap">
    <div class="progress-track"><div class="progress-fill" id="prog-fill" style="width:0%"></div></div>
    <span class="progress-label" id="prog-label">0 / 25</span>
  </div>
  <div id="survey-body"></div>
  <div class="survey-footer">
    <span class="footer-note" id="footer-note"></span>
    <button class="btn btn-primary" onclick="completeSurvey()" data-de="Antworten speichern" data-en="Save responses">Antworten speichern</button>
  </div>
</div>

<div id="screen-results" class="screen">
  <div class="survey-topbar">
    <button class="btn btn-sm btn-ghost" onclick="goHome()">← <span data-de="Zurück" data-en="Back">Zurück</span></button>
    <span style="font-size:18px;font-weight:700;" data-de="Ergebnisse" data-en="Results">Ergebnisse</span>
    <div class="lang-toggle" style="margin-left:auto">
      <button class="lang-btn active" id="rbtn-de" onclick="setLang('de')">DE</button>
      <button class="lang-btn" id="rbtn-en" onclick="setLang('en')">EN</button>
    </div>
  </div>
  <div class="tab-bar" id="results-tabs"></div>
  <div id="results-body"></div>
</div>

</div>

<div id="modal-org" class="modal-overlay" style="display:none;" onclick="if(event.target===this)closeModal('org')">
  <div class="modal">
    <h2 data-de="Organisation hinzufügen" data-en="Add organization">Organisation hinzufügen</h2>
    <div class="form-group">
      <label data-de="Name der Organisation" data-en="Organization name">Name der Organisation</label>
      <input type="text" id="inp-org-name" autocomplete="off"/>
    </div>
    <div class="form-group">
      <label data-de="Branche / Beschreibung" data-en="Industry / description">Branche / Beschreibung</label>
      <input type="text" id="inp-org-desc" autocomplete="off"/>
    </div>
    <div class="modal-actions">
      <button class="btn btn-ghost" onclick="closeModal('org')" data-de="Abbrechen" data-en="Cancel">Abbrechen</button>
      <button class="btn btn-primary" onclick="createOrg()" data-de="Erstellen →" data-en="Create →">Erstellen →</button>
    </div>
  </div>
</div>

<div id="modal-profile" class="modal-overlay" style="display:none;" onclick="if(event.target===this)closeModal('profile')">
  <div class="modal">
    <h2 data-de="Befragten hinzufügen" data-en="Add respondent">Befragten hinzufügen</h2>
    <div class="form-group">
      <label data-de="Vollständiger Name" data-en="Full name">Vollständiger Name</label>
      <input type="text" id="inp-name" autocomplete="off"/>
    </div>
    <div class="form-group">
      <label data-de="Funktion / Titel" data-en="Role / title">Funktion / Titel</label>
      <input type="text" id="inp-role" autocomplete="off"/>
    </div>
    <div class="modal-actions">
      <button class="btn btn-ghost" onclick="closeModal('profile')" data-de="Abbrechen" data-en="Cancel">Abbrechen</button>
      <button class="btn btn-primary" onclick="createProfile()" data-de="Befragung starten →" data-en="Start survey →">Befragung starten →</button>
    </div>
  </div>
</div>

<footer>ARCMM · AI Readiness Capability Maturity Model · Copenhagen Business School · 2026</footer>

<script>
let lang = 'de';

const AUTH_USER = 'AnjaLukas';
const AUTH_PASS = 'Copenhagen1!';

function removeVisibleDoctype() {
  const walker = document.createTreeWalker(document.body, NodeFilter.SHOW_TEXT, null);
  const textNodes = [];
  while (walker.nextNode()) {
    textNodes.push(walker.currentNode);
  }
  textNodes.forEach(node => {
    if (node.nodeValue && node.nodeValue.includes('<!DOCTYPE html>')) {
      node.nodeValue = node.nodeValue.replace('<!DOCTYPE html>', '').trim();
    }
  });
}

function unlockApp() {
  const login = document.getElementById('login-screen');
  const app = document.getElementById('app-root');
  if (login) login.style.display = 'none';
  if (app) app.classList.remove('hidden-app');
  removeVisibleDoctype();
}

function handleLogin() {
  const user = document.getElementById('login-user').value;
  const pass = document.getElementById('login-pass').value;
  const error = document.getElementById('login-error');

  if (user === AUTH_USER && pass === AUTH_PASS) {
    sessionStorage.setItem('arcmm_auth', '1');
    if (error) error.classList.remove('show');
    unlockApp();
  } else {
    if (error) error.classList.add('show');
  }
}

function initAuth() {
  removeVisibleDoctype();

  if (sessionStorage.getItem('arcmm_auth') === '1') {
    unlockApp();
  } else {
    const loginUser = document.getElementById('login-user');
    const loginPass = document.getElementById('login-pass');

    if (loginUser) {
      setTimeout(() => loginUser.focus(), 50);
    }

    if (loginUser) {
      loginUser.addEventListener('keydown', e => {
        if (e.key === 'Enter') handleLogin();
      });
    }

    if (loginPass) {
      loginPass.addEventListener('keydown', e => {
        if (e.key === 'Enter') handleLogin();
      });
    }
  }
}

const T = {
  orgSection: { de:'Organisationen', en:'Organizations' },
  respondents: { de:'Befragte', en:'Respondents' },
  addOrg: { de:'Organisation hinzufügen', en:'Add organization' },
  addRespondent: { de:'Befragten hinzufügen', en:'Add respondent' },
  complete: { de:'✓ Vollständig', en:'✓ Complete' },
  notStarted: { de:'Nicht begonnen', en:'Not started' },
  questionsLeft: { de:'Fragen verbleibend', en:'questions remaining' },
  allAnswered: { de:'Alle Fragen beantwortet.', en:'All questions answered.' },
  unable: { de:'Kann nicht beantworten', en:'Unable to answer' },
  aggregate: { de:'Aggregat', en:'Aggregate' },
  aggregateLocked: { de:'Aggregat gesperrt', en:'Aggregate locked' },
  aggregateLockedMsg: { de:'Das aggregierte Radar wird sichtbar, sobald alle Befragten die Erhebung abgeschlossen haben.', en:'The aggregate radar becomes visible once all respondents have completed the survey.' },
  of: { de:'von', en:'of' },
  profilesComplete: { de:'Profile vollständig', en:'profiles complete' },
  addRespondentsFirst: { de:'Fügen Sie zuerst Befragte auf dem Startbildschirm hinzu.', en:'Add respondents on the home screen first.' },
  editResponses: { de:'Antworten bearbeiten', en:'Edit responses' },
  remove: { de:'Entfernen', en:'Remove' },
  removeConfirm: { de:'Diesen Befragten und alle Antworten entfernen?', en:'Remove this respondent and all their responses?' },
  resetConfirm: { de:'Alle Profile und Antworten zurücksetzen?', en:'Reset all profiles and responses?' },
  capOverall: { de:'Gesamtpunkte nach Fähigkeit', en:'Overall capability scores' },
  lensOverall: { de:'Punkte nach Linse', en:'Scores by lens' },
  breakdownTitle: { de:'Aufschlüsselung nach Fähigkeit und Linse', en:'Breakdown by capability and lens' },
  respondentComp: { de:'Vergleich der Befragten nach Fähigkeit', en:'Respondent comparison by capability' },
  overall: { de:'Gesamt', en:'Overall' },
  reflections: { de:'Reflexionen', en:'Reflections' },
  noRoleSpec: { de:'Keine Funktion angegeben', en:'No role specified' },
};

function t(key) { return T[key] ? T[key][lang] : key; }
function l(obj) { return obj[lang] || obj['de'] || ''; }

const CAP = [
  { id:'c1', name:{ de:'KI-Portfoliomanagement', en:'AI Portfolio Management' }, short:{ de:'Portfolio Management', en:'Portfolio Management' }, color:'#2563EB', bg:'#DBEAFE' },
  { id:'c2', name:{ de:'KI-Bereitstellung & Technologiearchitektur', en:'AI Delivery & Technical Architecture' }, short:{ de:'Bereitstellung & Architektur', en:'Delivery & Architecture' }, color:'#0891B2', bg:'#CFFAFE' },
  { id:'c3', name:{ de:'KI-Koordination & Governance', en:'AI Coordination & Governance' }, short:{ de:'Koordination & Governance', en:'Coordination & Governance' }, color:'#0D9488', bg:'#CCFBF1' },
  { id:'c4', name:{ de:'KI-Datenzugang & -management', en:'AI Data Accessibility & Management' }, short:{ de:'Datenzugang', en:'Data Accessibility' }, color:'#7C3AED', bg:'#EDE9FE' },
  { id:'c5', name:{ de:'KI-Ethik & Risiken', en:'AI Ethics & Risks' }, short:{ de:'Ethik & Risiken', en:'Ethics & Risks' }, color:'#B45309', bg:'#FEF3C7' },
];

const LENS = [
  { id:'ia', name:{ de:'Individuelle Akteure', en:'Individual Actors' }, color:'#4F46E5', bg:'#EEF2FF' },
  { id:'dt', name:{ de:'Digitale Technologien', en:'Digital Technologies' }, color:'#0369A1', bg:'#E0F2FE' },
  { id:'ip', name:{ de:'Interaktionsmuster', en:'Interactional Patterns' }, color:'#047857', bg:'#D1FAE5' },
];



const QS = [
  { id:'q01', c:'c1', l:'ia', text:{ de:'Q1 Inwieweit verstehen einzelne Akteure* die Chancen von KI?', en:'Q1 To what extent do individual actors understand AI opportunities?' }, desc:{ de:'*Die Fähigkeit, die aktuellen Möglichkeiten und Grenzen von KI-Anwendungen zu verstehen und zu erkennen, welche Geschäftsprobleme sich für KI-Lösungen eignen.', en:'The ability to understand the current capabilities and limitations of AI technology and recognize which business problems are suitable for AI solutions.' }, opts:{ de:['Wenig','Grundlegend','Solide','Fortgeschritten','Ausgereift'], en:['Little','Basic','Solid','Advanced','Mature'] } },

  { id:'q02', c:'c1', l:'ia', text:{ de:'Q2 Inwieweit tragen einzelne Akteure* zur Priorisierung bei?', en:'Q2 To what extent do individual actors contribute to prioritization?' }, desc:{ de:'*Das Maß, in dem relevante Akteure (z. B. Geschäftsbereichsleiter, Führungskräfte, Product Owner) aktiv Input zur Bewertung und Rangfolge von KI-Initiativen liefern.', en:'The extent to which relevant actors actively provide input for evaluating and ranking AI initiatives.' }, opts:{ de:['Begrenzt','Gelegentlich','Regelmäßig','Konsistent','Proaktiv'], en:['Limited','Occasional','Regular','Consistent','Proactive'] } },

  { id:'q03', c:'c1', l:'ip', text:{ de:'Q3 Inwieweit sind Routinen für Portfolioentscheidungen* etabliert?', en:'Q3 To what extent are portfolio decision routines established?' }, desc:{ de:'*Die organisatorischen Verfahren und Governance-Prozesse, durch die KI-Initiativen genehmigt, abgelehnt, pausiert, skaliert oder eingestellt werden.', en:'The organizational procedures and governance processes through which AI initiatives are approved, rejected, paused, scaled, or discontinued.' }, opts:{ de:['Nicht vorhanden','Ad hoc','Formalisiert','Strukturiert','Kontinuierlich'], en:['Absent','Ad hoc','Formalized','Structured','Continuous'] } },

  { id:'q04', c:'c1', l:'ip', text:{ de:'Q4 Inwieweit ist das KI-Portfolio mit den strategischen Zielen verknüpft?', en:'Q4 To what extent is the AI portfolio linked to strategic goals?' }, desc:{ de:'*Der Grad, in dem die Auswahl, Steuerung und Fortführung von KI-Initiativen mit den übergeordneten strategischen Zielen und Prioritäten der Organisation abgestimmt sind.', en:'The degree to which the selection, steering, and continuation of AI initiatives are aligned with the organization\'s overarching strategic objectives and priorities.' }, opts:{ de:['Nicht vorhanden','Implizit','Teilweise','Konsistent','Nahtlos'], en:['Absent','Implicit','Partial','Consistent','Seamless'] } },

  { id:'q05', c:'c2', l:'ia', text:{ de:'Q5 Inwieweit verfügen technische Rollen über Fähigkeiten zum Aufbau von KI-Lösungen*?', en:'Q5 To what extent do technical roles have AI solution-building skills?' }, desc:{ de:'*Die technischen Kompetenzen zur Entwicklung von KI Use-Cases, einschließlich Datenvorbereitung, Auswahl von Algorithmen/Modellen, Entwicklung von Anwendungsfällen, Testen und Validierung.', en:'The technical competencies required to develop AI models, including data preparation, algorithm/model selection, use-case development, testing, and validation.' }, opts:{ de:['Nicht vorhanden','Entstehend','Vorhanden','Konsistent','Wertschöpfend'], en:['Absent','Emerging','Present','Consistent','Value-delivering'] } },

  { id:'q06', c:'c2', l:'ia', text:{ de:'Q6 Inwieweit verfügen technische Rollen über Fähigkeiten zur Operationalisierung*?', en:'Q6 To what extent do technical roles have operationalization skills?' }, desc:{ de:'*Die technischen Kompetenzen, die erforderlich sind, um KI-Anwendungsfälle von der Entwicklung in den produktiven Einsatz zu überführen, einschließlich Bereitstellung und Integration.', en:'The technical competencies required to transition AI use cases from development into production use, including deployment and integration.' }, opts:{ de:['Nicht vorhanden','Entstehend','Vorhanden','Konsistent','Wertschöpfend'], en:['Absent','Emerging','Present','Consistent','Value-delivering'] } },

  { id:'q07', c:'c2', l:'dt', text:{ de:'Q7 Inwieweit sind Versionskontrolle und Deployment-Pipelines* etabliert?', en:'Q7 To what extent are version control & deployment pipelines established?' }, desc:{ de:'*Die technischen Systeme und Prozesse zur Verwaltung von Code-Versionen, Nachverfolgung von Änderungen und Automatisierung der Bereitstellung von KI-Modellen in Produktionsumgebungen.', en:'The technical systems and processes for managing code versions, tracking changes, and automating the deployment of AI models into production environments.' }, opts:{ de:['Nicht vorhanden','Grundlegend','Funktional','Standardisiert','Automatisiert'], en:['Absent','Basic','Functional','Standardized','Automated'] } },

  { id:'q08', c:'c2', l:'dt', text:{ de:'Q8 Inwieweit sind Monitoring-Tools* für KI-Lösungen etabliert?', en:'Q8 To what extent are solution monitoring tools established?' }, desc:{ de:'*Die technischen Systeme und Prozesse zur Überwachung der Leistung von KI-Modellen, zur Erkennung von Problemen wie Modell-Drift und zur Sicherstellung der kontinuierlichen Zuverlässigkeit im produktiven Einsatz.', en:'The technical systems and processes for tracking AI model performance, detecting issues such as model drift, and ensuring continuous reliability in production.' }, opts:{ de:['Nicht vorhanden','Informell','Funktional','Standardisiert','Automatisiert'], en:['Absent','Informal','Functional','Standardized','Automated'] } },

  { id:'q09', c:'c2', l:'ip', text:{ de:'Q9 Inwieweit sind KI delivery practices* etabliert?', en:'Q9 To what extent are AI delivery practices established?' }, desc:{ de:'*Die standardisierten organisatorischen Prozesse und Arbeitsabläufe zur Entwicklung, zum Testen, zur Bereitstellung und zur Wartung von KI-Lösungen.', en:'The standardized organizational processes and workflows for moving AI solutions through development, testing, deployment, and maintenance stages.' }, opts:{ de:['Nicht vorhanden','Grundlegend','Strukturiert','Standardisiert','Kontinuierlich verbessert'], en:['Absent','Basic','Structured','Standardized','Continuously improved'] } },

  { id:'q10', c:'c2', l:'ip', text:{ de:'Q10 Inwieweit sind IT- und Business bei der Umsetzung von KI abgestimmt*?', en:'Q10 To what extent are IT & business functions coordinated in AI delivery?' }, desc:{ de:'*Die Zusammenarbeit und Abstimmung zwischen IT-Teams und Business während des gesamten KI-Umsetzungsprozesses, von der Anforderungsaufnahme bis zur Bereitstellung und Wartung.', en:'The collaboration and alignment between IT teams and business throughout the AI delivery lifecycle, from requirements gathering to deployment and maintenance.' }, opts:{ de:['Nicht vorhanden','Reaktiv','Konsistent','Etabliert','Proaktiv'], en:['Absent','Reactive','Consistent','Embedded','Proactive'] } },

  { id:'q11', c:'c3', l:'ia', text:{ de:'Q11 Inwieweit sind einzelnen Akteuren die Rollen und Verantwortlichkeiten* für KI-Projekte klar?', en:'Q11 To what extent are roles & responsibilities for AI projects clear to individual actors?' }, desc:{ de:'*Das Maß, in dem klar definiert ist, wer für projektbezogene Aufgaben verantwortlich ist, einschließlich strategischer Aufsicht, Projektumsetzung, Datenverwaltung und operativer Verantwortlichkeiten.', en:'The extent to which it is clearly defined who is accountable for AI-related tasks, including strategic oversight, project delivery, data governance, and operational responsibilities.' }, opts:{ de:['Nicht vorhanden','Grundlegend','Etabliert','Konsistent','Verankert'], en:['Absent','Basic','Established','Consistent','Embedded'] } },

  { id:'q12', c:'c3', l:'ia', text:{ de:'Q12 Inwieweit sind Entscheidungsrechte für KI für einzelne Akteure* klar?', en:'Q12 To what extent are decision rights for AI clear to individual actors?' }, desc:{ de:'*Das Maß, in dem klar definiert ist, wer die Befugnis hat, Entscheidungen über KI-Initiativen zu treffen, einschließlich Genehmigungen, Ressourcenzuteilung, Priorisierung und Fortführung oder Beendigung von Projekten.', en:'The extent to which it is clearly defined who has the authority to make decisions about AI initiatives, including approvals, resource allocation, prioritization, and project continuation or termination.' }, opts:{ de:['Nicht vorhanden','Grundlegend','Etabliert','Konsistent','Verankert'], en:['Absent','Basic','Established','Consistent','Embedded'] } },

  { id:'q13', c:'c3', l:'ip', text:{ de:'Q13 Inwieweit sind Entscheidungsrechte und Prozesse* für KI-Projekte etabliert?', en:'Q13 To what extent are decision rights & processes for AI established?' }, desc:{ de:'*Die Governance-Strukturen und Genehmigungsmechanismen, durch die Entscheidungen zu KI-Projekten getroffen, eskaliert und organisationsweit dokumentiert werden.', en:'The governance structures and approval mechanisms through which AI project decisions are made, escalated, and documented across the organization.' }, opts:{ de:['Nicht vorhanden','Informell','Definiert','Konsistent angewendet','Kontinuierlich verbessert'], en:['Absent','Informal','Defined','Consistently applied','Continuously improved'] } },

  { id:'q14', c:'c3', l:'ip', text:{ de:'Q14 Inwieweit sind relevante Stakeholder* in KI-bezogene Entscheidungen und Aktivitäten eingebunden?', en:'Q14 To what extent are relevant stakeholders involved in AI-related decisions and activities?' }, desc:{ de:'*Das Maß, in dem relevante Akteure der Organisation, einschließlich Geschäftsbereiche, IT, Daten-Teams, Compliance und Endnutzer, während des gesamten Lebenszyklus von KI-Projekten eingebunden sind.', en:'The extent to which relevant organizational actors, including business units, IT, data teams, compliance, and end users, are engaged throughout AI project lifecycles.' }, opts:{ de:['Nicht vorhanden','Grundlegend','Strukturiert','Konsistent','Kontinuierlich'], en:['Absent','Basic','Structured','Consistent','Continuous'] } },

  { id:'q15', c:'c4', l:'ia', text:{ de:'Q15 Inwieweit sind sich Business Rollen der Datenanforderungen* für KI bewusst?', en:'Q15 To what extent are business roles aware of data requirements and opportunities for AI?' }, desc:{ de:'*Das Ausmaß, in dem Geschäftsrollen die Datenanforderungen für KI verstehen und aktiv an der Datenerhebung und -verbesserung teilnehmen.', en:'The extent to which business roles understand data requirements for AI and actively participate in data collection and improvement.' }, opts:{ de:['Nicht vorhanden','Grundlegend','Etabliert','Proaktiv','Fördernd'], en:['Absent','Basic','Established','Proactive','Advocacy-driven'] } },

  { id:'q16', c:'c4', l:'ia', text:{ de:'Q16 Inwieweit unterstützen und steuern technische Rollen* Datenpraktiken für KI?', en:'Q16 To what extent do technical roles support and govern data practices for AI?' }, desc:{ de:'*Die Kompetenzen und Routinen technischer Teams zur Sammlung, Strukturierung, Integration, Kuration und Pflege von Daten, um Qualitäts- und Zugänglichkeitsstandards für KI zu erfüllen.', en:'The competencies and routines of technical teams to collect, structure, integrate, curate, and maintain data to meet AI quality and accessibility standards.' }, opts:{ de:['Reaktiv','Unterstützend','Standardisierend','Proaktiv','Kontinuierlich verbessernd'], en:['Reactive','Supportive','Standards-enforcing','Governance-leading','Continuously refining'] } },

  { id:'q17', c:'c4', l:'dt', text:{ de:'Q17 Inwieweit ist die Dateninfrastruktur* für den KI-Einsatz strukturiert und skalierbar?', en:'Q17 To what extent is the data infrastructure structured and scalable for AI use?' }, desc:{ de:'*Die technischen Systeme und Plattformen zur Speicherung, Verarbeitung und Bereitstellung von Daten, die für die Entwicklung, Bereitstellung und den Betrieb von KI-Systemen erforderlich sind.', en:'The technical systems and platforms for storing, processing, and providing access to data required for AI model development, deployment, and operation.' }, opts:{ de:['Begrenzt','Grundlegend','Strukturiert','Skalierbar','Elastisch'], en:['Limited','Basic','Structured','Scalable','Elastic'] } },

  { id:'q18', c:'c4', l:'dt', text:{ de:'Q18 Inwieweit sind Daten organisationsweit für KI-Nutzung* zugänglich?', en:'Q18 To what extent is data accessible across systems and stakeholders for AI use?' }, desc:{ de:'*Das Ausmaß, in dem relevante Daten von autorisierten Nutzern und Systemen organisationsweit für KI-Zwecke gefunden, abgerufen und genutzt werden können.', en:'The extent to which relevant data can be discovered, retrieved, and used by authorized teams and stakeholders across the organization for AI purposes.' }, opts:{ de:['Begrenzt','Isoliert','Teilweise','Konsistent','Interoperabel'], en:['Limited','Siloed','Partial','Consistent','Interoperable'] } },

  { id:'q19', c:'c4', l:'ip', text:{ de:'Q19 Inwieweit sind Zugriffsrechte* für Daten definiert?', en:'Q19 To what extent are data access & editing rights defined for data?' }, desc:{ de:'*Die formalen Richtlinien und Berechtigungen, die festlegen, wer und welche Systeme auf bestimmte Datenbestände für die Entwicklung und Bereitstellung von KI zugreifen, sie nutzen, verändern und teilen darf.', en:'The formal policies and permissions that define who and which systems can access, use, modify, and share specific data assets for AI development and deployment.' }, opts:{ de:['Nicht definiert','Informell','Definiert','Durchgesetzt','Kontinuierlich verfeinert'], en:['Undefined','Informal','Defined','Enforced','Continuously refined'] } },

  { id:'q20', c:'c4', l:'ip', text:{ de:'Q20 Inwieweit sind Prozesse zur Sicherstellung der Datenqualität* etabliert, um zuverlässige Daten für den KI-Einsatz zu gewährleisten?', en:'Q20 To what extent are data quality processes established to ensure reliable data for AI use?' }, desc:{ de:'*Die organisatorischen Routinen und Standards zur Sicherstellung von Datenkorrektheit, Vollständigkeit, Konsistenz und Zuverlässigkeit.', en:'The organizational routines and standards for ensuring data accuracy, completeness, consistency, and reliability across the AI lifecycle.' }, opts:{ de:['Nicht vorhanden','Inkonsistent','Grundlegend','Zuverlässig','Kontinuierlich verbessert'], en:['Absent','Inconsistent','Basic','Reliability-driven','Continuously improved'] } },
  
  { id:'q21', c:'c5', l:'ia', text:{ de:'Q21 Inwieweit sind Business Rollen der KI-bezogenen Risiken und ethischen Bedenken bewusst und dafür verantwortlich*?', en:'Q21 To what extent are business roles aware of and responsible for AI-related risks & ethical concerns?' }, desc:{ de:'*Das Ausmaß, in dem Geschäftsbereiche ethische, rechtliche, Sicherheits-, Datenschutz- und Qualitätsrisiken im Zusammenhang mit KI verstehen und Verantwortung für deren Identifizierung und Eskalation übernehmen.', en:'The extent to which business stakeholders understand ethical, legal, security, privacy, and quality risks associated with AI and take responsibility for identifying and escalating them.' }, opts:{ de:['Abwesend','Grundlegend','Etabliert','Konsistent','Proaktiv'], en:['Absent','Basic','Established','Consistent','Proactive'] } },

  { id:'q22', c:'c5', l:'ia', text:{ de:'Q22 Inwieweit identifizieren, bewerten und adressieren technische Rollen* KI-bezogene Risiken und ethische Fragestellungen in der Praxis?', en:'Q22 To what extent do technical roles identify, assess, and address AI-related risks & ethical concerns in practice?' }, desc:{ de:'*Die Kompetenzen und Routinen technischer Teams zur Identifizierung, Bewertung, Dokumentation und Minderung ethischer, rechtlicher, sicherheitsbezogener, datenschutzbezogener und qualitätsbezogener Risiken über den gesamten KI-Lebenszyklus.', en:'The competencies and routines of technical teams to identify, assess, document, and mitigate ethical, legal, security, privacy, and quality risks throughout the AI lifecycle.' }, opts:{ de:['Abwesend','Entstehend','Definiert','Durchgesetzt','Kontinuierlich verbessert'], en:['Absent','Emerging','Defined','Enforced','Continuously refined'] } },

  { id:'q23', c:'c5', l:'dt', text:{ de:'Q23 Inwieweit sind Tools für das Monitoring von ethischem Einsatz und zur Risikobewertung* von KI-Tools etabliert?', en:'Q23 To what extent is AI ethics & risk assessment tooling established?' }, desc:{ de:'*Die technischen Systeme und Methoden zur systematischen Bewertung von KI-bezogenen Risiken, einschließlich Modelltests, Erkennung von Verzerrungen, Sicherheitsüberprüfungen und Compliance-Prüfungen.', en:'The technical systems and methods for systematically evaluating AI-related risks, including model testing, bias detection, security scanning, and compliance checking.' }, opts:{ de:['Abwesend','Grundlegend','Standard','Systematisch','Automatisiert'], en:['Absent','Basic','Standard','Systematic','Automated'] } },

  { id:'q24', c:'c5', l:'ip', text:{ de:'Q24 Inwieweit sind Routinen zur Überprüfung von ethisch vertretbarem Einsatz und von Risiken* etabliert?', en:'Q24 To what extent are AI ethics & risk review routines established?' }, desc:{ de:'*Die organisatorischen Prozesse zur regelmäßigen Überprüfung von KI-Systemen und Projekten, um neue Risiken zu identifizieren und zu bewerten, ob bestehende Maßnahmen weiterhin wirksam sind.', en:'The organizational processes for regularly reviewing AI systems and projects to identify emerging risks and assess whether mitigation measures remain effective.' }, opts:{ de:['Abwesend','Vereinzelt','Definiert','Konsistent','Wiederkehrend'], en:['Absent','Scattered','Defined','Consistent','Recurring'] } },

  { id:'q25', c:'c5', l:'ip', text:{ de:'Q25 Inwieweit sind Eskalationswege für KI-bezogene Risiken und ethische Fragestellungen* etabliert?', en:'Q25 To what extent are escalation paths for AI-related risks and ethical issues established?' }, desc:{ de:'*Die Verfahren und Berichtsstrukturen, durch die identifizierte KI-Risiken an die entsprechenden Entscheidungsträger zur Lösung oder zur Einleitung von Gegenmaßnahmen kommuniziert werden.', en:'The procedures and reporting structures through which identified AI risks are communicated to appropriate decision-makers for resolution or mitigation action.' }, opts:{ de:['Abwesend','Inkonsistent','Definiert','Durchgesetzt','Etabliert'], en:['Absent','Inconsistent','Defined','Enforced','Embedded'] } },
];
const OQS = [
  { id:'oq1', text:{ de:'Gibt es Ihrer Meinung nach wichtige Aspekte für AI-Readiness, die in dieser Bewertung fehlen?', en:'In your opinion, are there any important aspects of AI readiness that are missing from this assessment?' }, type:'text' },
  { id:'oq2', text:{ de:'Wie gut ist Ihre Organisation Ihrer Meinung nach in der Lage, KI erfolgreich zu implementieren? Bitte bewerten Sie auf einer Skala von 1 bis 5.', en:'In your opinion, how well is your organization able to successfully implement AI? Please rate it on a scale from 1 to 5.' }, type:'rating' },
  { id:'oq3', text:{ de:'Hat sich Ihre Einschätzung zur Fähigkeit Ihrer Organisation, KI erfolgreich zu implementieren, nach Abschluss dieser Umfrage im Vergleich zu Ihrer ursprünglichen Wahrnehmung verändert?', en:'Has your assessment of your organization’s ability to successfully implement AI changed after completing this survey compared to your initial perception?' }, type:'select', opts:{ de:['Nein, sie ist etwa gleich geblieben','Ja, etwas verändert','Ja, deutlich verändert','Nicht sicher'], en:['No, it was about the same','Yes, somewhat','Yes, significantly','Not sure'] } },
  { id:'oq4', text:{ de:'Wie hat sich Ihre Wahrnehmung verändert?', en:'How did your perception change?' }, type:'text' },
];

const AVATAR_PALETTES = [
  { bg:'#DBEAFE', fg:'#1D4ED8' },{ bg:'#CCFBF1', fg:'#0F766E' },{ bg:'#EDE9FE', fg:'#6D28D9' },
  { bg:'#FEF3C7', fg:'#92400E' },{ bg:'#D1FAE5', fg:'#065F46' },{ bg:'#FCE7F3', fg:'#9D174D' },
];

let state = { orgs:[] };
let activeOrgId = null;
let activeProfileId = null;
let currentTab = 'aggregate';
let currentOrgTab = null;
const charts = {};

function save() { try { localStorage.setItem('arcmm_v3', JSON.stringify(state)); } catch(e){} }
function load() { try { const s = localStorage.getItem('arcmm_v3'); if(s) state = JSON.parse(s); } catch(e){} }

function setLang(l) {
  lang = l;
  document.querySelectorAll('[data-de]').forEach(el => {
    el.textContent = l === 'de' ? el.dataset.de : el.dataset.en;
  });
  ['btn-de','btn-en','rbtn-de','rbtn-en'].forEach(id => {
    const el = document.getElementById(id);
    if (el) el.classList.toggle('active', id.includes(l));
  });
  const surveyActive = document.getElementById('screen-survey').classList.contains('active');
  const resultsActive = document.getElementById('screen-results').classList.contains('active');
  if (surveyActive) {
    const p = state.orgs.flatMap(o=>o.profiles).find(p=>p.id===activeProfileId);
    if (p) renderSurvey(p);
  }
  if (resultsActive) renderResults();
  renderHome();
}

function ini(n) { return (n||'?').split(' ').filter(Boolean).map(w=>w[0]).join('').toUpperCase().slice(0,2); }
function pal(i) { return AVATAR_PALETTES[i % AVATAR_PALETTES.length]; }

function score(r, qid) {
  const v = r[qid]; if (!v || v==='unable') return null;
  const q = QS.find(q=>q.id===qid); if(!q) return null;
  const opts = q.opts[lang] || q.opts['de'];
  let idx = opts.indexOf(v);
  if (idx < 0) { const other = q.opts[lang==='de'?'en':'de']; idx = other.indexOf(v); }
  return idx < 0 ? null : idx + 1;
}

function capLensScore(r, cid, lid) {
  const qs = QS.filter(q=>q.c===cid && q.l===lid);
  const ss = qs.map(q=>score(r,q.id)).filter(s=>s!==null);
  return ss.length ? ss.reduce((a,b)=>a+b,0)/ss.length : null;
}
function capScore(r, cid) {
  const ss = QS.filter(q=>q.c===cid).map(q=>score(r,q.id)).filter(s=>s!==null);
  return ss.length ? ss.reduce((a,b)=>a+b,0)/ss.length : null;
}
function answered(p) { return QS.filter(q=>p.responses&&p.responses[q.id]).length; }
function isComplete(p) { return QS.every(q=>p.responses&&p.responses[q.id]); }
function orgAllDone(org) { return org.profiles.length > 0 && org.profiles.every(isComplete); }
function allOrgsAllDone() { return state.orgs.length > 0 && state.orgs.every(orgAllDone); }
function findProfile(pid) { return state.orgs.flatMap(o=>o.profiles).find(p=>p.id===pid); }
function findOrgOfProfile(pid) { return state.orgs.find(o=>o.profiles.some(p=>p.id===pid)); }

function showScreen(id) { document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active')); document.getElementById('screen-'+id).classList.add('active'); }
function goHome() { renderHome(); showScreen('home'); }
function showResults() { currentTab='aggregate'; currentOrgTab=state.orgs[0]?.id||null; renderResults(); showScreen('results'); }
function openModal(type) {
  document.getElementById('modal-'+type).style.display='flex';
  setTimeout(()=>{ const el=document.getElementById(type==='org'?'inp-org-name':'inp-name'); if(el) el.focus(); },60);
}
function closeModal(type) {
  document.getElementById('modal-'+type).style.display='none';
  if(type==='org'){ document.getElementById('inp-org-name').value=''; document.getElementById('inp-org-desc').value=''; }
  else { document.getElementById('inp-name').value=''; document.getElementById('inp-role').value=''; }
}

function renderHome() {
  const og = document.getElementById('orgs-grid');
  og.innerHTML = '';
  state.orgs.forEach((org,i) => {
    const allDone = orgAllDone(org);
    const card = document.createElement('div');
    const isSelected = activeOrgId === org.id;
    card.className = 'org-card'+(isSelected?' selected':'');
    const completedCount = org.profiles.filter(isComplete).length;
    card.innerHTML = `<div class="org-name">${org.name}</div><div class="org-meta">${org.desc||''}</div>
      <span class="badge ${allDone?'badge-done':completedCount>0?'badge-partial':'badge-empty'}">
        ${allDone ? t('complete') : completedCount+' / '+org.profiles.length+' '+t('profilesComplete')}</span>`;
    card.onclick = () => selectOrg(org.id);
    og.appendChild(card);
  });
  const addOrg = document.createElement('div');
  addOrg.className = 'org-card add-new';
  addOrg.innerHTML = '<span style="font-size:20px;font-weight:300;line-height:1">+</span> '+(lang==='de'?'Organisation hinzufügen':'Add organization');
  addOrg.onclick = () => openModal('org');
  og.appendChild(addOrg);
  if (activeOrgId) {
    const org = state.orgs.find(o=>o.id===activeOrgId);
    if (org) renderOrgDetail(org);
    document.getElementById('org-detail').style.display = 'block';
  } else {
    document.getElementById('org-detail').style.display = 'none';
  }
}

function selectOrg(orgId) { activeOrgId = activeOrgId === orgId ? null : orgId; renderHome(); }

function renderOrgDetail(org) {
  const hdr = document.getElementById('org-detail-header');
  hdr.innerHTML = `<div class="org-section-header">
    <div class="org-section-icon">${ini(org.name)}</div>
    <div><div class="org-section-name">${org.name}</div>${org.desc?`<div style="font-size:11px;color:var(--blue-600)">${org.desc}</div>`:''}</div>
    <span class="org-section-meta">${org.profiles.filter(isComplete).length} / ${org.profiles.length} ${lang==='de'?'vollständig':'complete'}</span>
    <button class="btn btn-sm btn-danger" style="margin-left:8px" onclick="deleteOrg('${org.id}')">${lang==='de'?'Entfernen':'Remove'}</button>
  </div>`;
  const pg = document.getElementById('profiles-grid');
  pg.innerHTML = '';
  org.profiles.forEach((p,i) => {
    const done = isComplete(p); const cnt = answered(p); const pl = pal(i);
    const card = document.createElement('div');
    card.className = 'profile-card'+(done?' completed':'');
    card.innerHTML = `<div style="display:flex;align-items:center;gap:8px;margin-bottom:8px;">
        <div class="profile-avatar" style="background:${pl.bg};color:${pl.fg};">${ini(p.name)}</div>
        <div><div class="profile-name">${p.name}</div><div class="profile-role">${p.role||t('noRoleSpec')}</div></div>
      </div>
      <span class="badge ${done?'badge-done':cnt>0?'badge-partial':'badge-empty'}">
        ${done ? t('complete') : cnt>0 ? cnt+'/25 '+(lang==='de'?'beantwortet':'answered') : t('notStarted')}</span>`;
    card.onclick = () => openSurvey(p.id);
    pg.appendChild(card);
  });
  if (org.profiles.length < 6) {
    const add = document.createElement('div');
    add.className = 'profile-card add-new';
    add.innerHTML = '<span style="font-size:20px;font-weight:300;line-height:1">+</span> '+t('addRespondent');
    add.onclick = () => openModal('profile');
    pg.appendChild(add);
  }
}

function createOrg() {
  const name = document.getElementById('inp-org-name').value.trim();
  const desc = document.getElementById('inp-org-desc').value.trim();
  if (!name) { document.getElementById('inp-org-name').focus(); return; }
  const id = 'org'+Date.now();
  state.orgs.push({ id, name, desc, profiles:[] });
  activeOrgId = id;
  save(); closeModal('org'); renderHome();
}

function deleteOrg(orgId) {
  if (!confirm(lang==='de'?'Diese Organisation und alle Befragten entfernen?':'Remove this organization and all respondents?')) return;
  state.orgs = state.orgs.filter(o=>o.id!==orgId);
  if (activeOrgId===orgId) activeOrgId=null;
  save(); renderHome();
}

function createProfile() {
  const name = document.getElementById('inp-name').value.trim();
  const role = document.getElementById('inp-role').value.trim();
  if (!name) { document.getElementById('inp-name').focus(); return; }
  if (!activeOrgId) return;
  const id = 'p'+Date.now();
  const org = state.orgs.find(o=>o.id===activeOrgId);
  org.profiles.push({ id, name, role, responses:{}, open:{} });
  save(); closeModal('profile');
  openSurvey(id);
}

function openSurvey(pid) {
  activeProfileId = pid;
  const p = findProfile(pid);
  const org = findOrgOfProfile(pid);
  document.getElementById('survey-who').textContent = p.name + (p.role ? ' · '+p.role : '');
  document.getElementById('survey-org-tag').textContent = org ? org.name : '';
  renderSurvey(p);
  showScreen('survey');
}

function renderSurvey(p) {
  const body = document.getElementById('survey-body');
  body.innerHTML = '';
  CAP.forEach(cap => {
    const sec = document.createElement('div');
    sec.className = 'cap-section';
    sec.innerHTML = `<div class="cap-header"><div class="cap-dot" style="background:${cap.color}"></div>${l(cap.name)}</div>`;
    QS.filter(q=>q.c===cap.id).forEach(q => {
      const ln = LENS.find(lns=>lns.id===q.l);
      const cur = p.responses[q.id]||null;
      const opts = q.opts[lang];
      const div = document.createElement('div');
      div.className = 'q-block';
      let optsHtml = opts.map(o => `<button class="opt${cur===o?' selected':''}" onclick="pick('${q.id}','${o.replace(/'/g,"\\'")}',this)" data-val="${o}">${o}</button>`).join('');
      optsHtml += `<button class="opt unable${cur==='unable'?' selected':''}" onclick="pick('${q.id}','unable',this)" data-val="unable">${t('unable')}</button>`;
      div.innerHTML = `<span class="lens-tag" style="background:${ln.bg};color:${ln.color};">${l(ln.name)}</span>
        <div class="q-text">${l(q.text)}</div>
        <div class="q-desc">${l(q.desc)}</div>
        <div class="opts-row" id="or_${q.id}">${optsHtml}</div>`;
      sec.appendChild(div);
    });
    body.appendChild(sec);
  });
  const rs = document.createElement('div');
  rs.innerHTML = `<div class="cap-header" style="background:var(--surface);">${t('reflections')}</div>`;
  OQS.forEach(oq => {
    const div = document.createElement('div');
    div.className = 'r-block';
    const cur = p.open[oq.id]||'';
    if (oq.type==='rating') {
      div.innerHTML = `<div class="r-label">${l(oq.text)}</div>
        <div class="rating-row">
          <span style="font-size:12px;color:var(--text-faint)">1</span>
          <input type="range" min="1" max="5" step="1" value="${cur||3}" oninput="saveOpen('${oq.id}',this.value);document.getElementById('rv_${oq.id}').textContent=this.value;">
          <span style="font-size:12px;color:var(--text-faint)">5</span>
          <span class="rating-val" id="rv_${oq.id}">${cur||3}</span>
        </div>`;
    } else if (oq.type==='select') {
      const opts = oq.opts[lang];
      const oph = opts.map(o=>`<button class="opt${cur===o?' selected':''}" onclick="selectOpen('${oq.id}','${o.replace(/'/g,"\\'")}',this)">${o}</button>`).join('');
      div.innerHTML = `<div class="r-label">${l(oq.text)}</div><div class="opts-row" style="margin-top:10px;" id="oo_${oq.id}">${oph}</div>`;
    } else {
      div.innerHTML = `<div class="r-label">${l(oq.text)}</div><textarea placeholder="${lang==='de'?'Ihre Antwort...':'Your response...'}" oninput="saveOpen('${oq.id}',this.value)">${cur}</textarea>`;
    }
    rs.appendChild(div);
  });
  body.appendChild(rs);
  updateProg(p);
}

function pick(qid, val, btn) {
  const p = findProfile(activeProfileId); if(!p) return;
  p.responses[qid] = val; save();
  const row = document.getElementById('or_'+qid);
  if (row) row.querySelectorAll('.opt').forEach(b => { b.classList.remove('selected'); if (b.dataset.val === val) b.classList.add('selected'); });
  updateProg(p);
}

function selectOpen(oqid, val, btn) {
  const p = findProfile(activeProfileId); if(!p) return;
  p.open[oqid] = val; save();
  const row = document.getElementById('oo_'+oqid);
  if (row) row.querySelectorAll('.opt').forEach(b=>{ b.classList.remove('selected'); if(b===btn) b.classList.add('selected'); });
}

function saveOpen(oqid, val) {
  const p = findProfile(activeProfileId); if(!p) return;
  p.open[oqid] = val; save();
}

function updateProg(p) {
  const cnt = answered(p); const total = QS.length;
  document.getElementById('prog-fill').style.width = Math.round(cnt/total*100)+'%';
  document.getElementById('prog-label').textContent = cnt+' / '+total;
  document.getElementById('footer-note').textContent = cnt===total ? t('allAnswered') : (total-cnt)+' '+t('questionsLeft');
}

function completeSurvey() { save(); renderHome(); goHome(); }

function renderResults() {
  const tb = document.getElementById('results-tabs');
  tb.innerHTML = '';
  const aggBtn = document.createElement('button');
  aggBtn.className = 'tab'+(currentTab==='aggregate'?' active':'');
  aggBtn.textContent = t('aggregate') + (lang==='de'?' (Alle)':' (All)');
  aggBtn.onclick = () => { currentTab='aggregate'; renderResults(); };
  tb.appendChild(aggBtn);
  state.orgs.forEach(org => {
    const orgTab = document.createElement('button');
    orgTab.className = 'tab org-tab'+(currentTab===org.id?' active':'');
    orgTab.textContent = org.name;
    orgTab.onclick = () => { currentTab=org.id; currentOrgTab=org.id; renderResults(); };
    tb.appendChild(orgTab);
    if (currentTab===org.id || org.profiles.some(p=>p.id===currentTab)) {
      org.profiles.forEach((p,i) => {
        const pt = document.createElement('button');
        pt.className = 'tab'+(currentTab===p.id?' active':'');
        pt.style = 'font-size:11px;padding:5px 11px;opacity:.85;margin-left:2px;';
        pt.textContent = '↳ '+p.name.split(' ')[0];
        pt.onclick = () => { currentTab=p.id; renderResults(); };
        tb.appendChild(pt);
      });
    }
  });
  const body = document.getElementById('results-body');
  body.innerHTML = '';
  if (currentTab==='aggregate') renderGlobalAggregate(body);
  else {
    const org = state.orgs.find(o=>o.id===currentTab);
    if (org) renderOrgAggregate(body, org);
    else { const p = findProfile(currentTab); if (p) renderProfile(body, p); }
  }
}

function renderGlobalAggregate(body) {
  if (!allOrgsAllDone()) {
    const doneOrgs = state.orgs.filter(orgAllDone).length;
    body.innerHTML = `<div class="locked-box"><div class="locked-icon">🔒</div>
      <h3>${t('aggregateLocked')}</h3>
      <p>${t('aggregateLockedMsg')}<br><br>${doneOrgs} ${t('of')} ${state.orgs.length} ${lang==='de'?'Organisationen vollständig':'organizations complete'}.
      ${state.orgs.length===0?'<br>'+t('addRespondentsFirst'):''}</p></div>`;
    return;
  }
  renderRadarAndTable(body, state.orgs.flatMap(o=>o.profiles), lang==='de'?'Globales Aggregat — alle Organisationen':'Global Aggregate — all organizations');
}

function renderOrgAggregate(body, org) {
  if (!orgAllDone(org)) {
    const done = org.profiles.filter(isComplete).length;
    body.innerHTML = `<div class="locked-box"><div class="locked-icon">🔒</div>
      <h3>${t('aggregateLocked')}</h3>
      <p>${t('aggregateLockedMsg')}<br><br>${done} ${t('of')} ${org.profiles.length} ${t('profilesComplete')}.</p></div>`;
    return;
  }
  renderRadarAndTable(body, org.profiles, org.name);
}

function renderRadarAndTable(body, profiles, title) {
  const capData = CAP.map(cap => {
    const ls = {}; LENS.forEach(ln => {
      const vals = profiles.map(p=>capLensScore(p.responses,cap.id,ln.id)).filter(s=>s!==null);
      ls[ln.id] = vals.length ? vals.reduce((a,b)=>a+b,0)/vals.length : 0;
    });
    const ov = profiles.map(p=>capScore(p.responses,cap.id)).filter(s=>s!==null);
    return { cap, ls, overall: ov.length ? ov.reduce((a,b)=>a+b,0)/ov.length : 0 };
  });
  const hdr = document.createElement('div');
  hdr.style = 'font-size:16px;font-weight:700;letter-spacing:-.2px;margin-bottom:1.25rem;';
  hdr.textContent = title;
  body.appendChild(hdr);
  const mg = document.createElement('div'); mg.className = 'metric-grid';
  capData.forEach(d => {
    mg.innerHTML += `<div class="metric-card"><div class="metric-cap">${l(d.cap.short)}</div>
      <div class="metric-score" style="color:${d.cap.color}">${d.overall.toFixed(1)}<span class="metric-denom">/5</span></div></div>`;
  });
  body.appendChild(mg);
  const chartId1 = 'ra-cap-'+Date.now();
  const chartId2 = 'ra-lens-'+(Date.now()+1);
  const cg = document.createElement('div'); cg.className = 'chart-grid';
  cg.innerHTML = `<div class="chart-card"><div class="chart-title">${t('capOverall')}</div><div class="chart-wrap"><canvas id="${chartId1}"></canvas></div></div>
    <div class="chart-card"><div class="chart-title">${t('lensOverall')}</div><div class="chart-wrap"><canvas id="${chartId2}"></canvas></div></div>`;
  body.appendChild(cg);
  const st = document.createElement('div');
  st.innerHTML = `<p class="section-title">${t('breakdownTitle')}</p>
    <table class="score-table"><thead><tr>
      <th>${lang==='de'?'Fähigkeit':'Capability'}</th>
      ${LENS.map(ln=>`<th>${ln.name[lang]}</th>`).join('')}
      <th>${t('overall')}</th>
    </tr></thead><tbody>${capData.map(d=>`<tr>
      <td><span style="display:inline-block;width:8px;height:8px;border-radius:50%;background:${d.cap.color};margin-right:6px;vertical-align:middle;"></span>${l(d.cap.short)}</td>
      ${LENS.map(ln=>`<td>${d.ls[ln.id]?d.ls[ln.id].toFixed(1):'—'}<span class="mini-bar"><span class="mini-fill" style="display:block;width:${((d.ls[ln.id]||0)/5*100).toFixed(0)}%;background:${ln.color};height:100%;border-radius:3px;"></span></span></td>`).join('')}
      <td style="font-weight:700">${d.overall.toFixed(1)}</td>
    </tr>`).join('')}</tbody></table>`;
  body.appendChild(st);
  if (profiles.length > 1) {
    const rc = document.createElement('div');
    rc.innerHTML = `<p class="section-title">${t('respondentComp')}</p>`;
    CAP.forEach(cap => {
      const blk = document.createElement('div'); blk.className = 'comp-block';
      let rows = `<div class="comp-cap-title">${l(cap.name)}</div>`;
      profiles.forEach((p,i) => {
        const sc = capScore(p.responses, cap.id); const pl = pal(i);
        const org = findOrgOfProfile(p.id);
        rows += `<div class="comp-row">
          <div class="profile-avatar" style="background:${pl.bg};color:${pl.fg};width:22px;height:22px;font-size:9px;flex-shrink:0;">${ini(p.name)}</div>
          <div class="comp-name">${p.name}${org?` <span style="font-size:10px;color:var(--text-faint)">(${org.name})</span>`:''}</div>
          <div class="comp-bar-track"><div class="comp-bar-fill" style="width:${sc?(sc/5*100).toFixed(0):0}%;background:${cap.color};"></div></div>
          <div class="comp-val">${sc?sc.toFixed(1):'—'}</div>
        </div>`;
      });
      blk.innerHTML = rows; rc.appendChild(blk);
    });
    body.appendChild(rc);
  }
  setTimeout(() => {
    const dark = matchMedia('(prefers-color-scheme: dark)').matches;
    const gc = dark ? 'rgba(255,255,255,0.08)' : 'rgba(30,41,59,0.08)';
    const tc = dark ? 'rgba(255,255,255,0.35)' : 'rgba(30,41,59,0.4)';
    const pc = dark ? 'rgba(255,255,255,0.6)' : 'rgba(30,41,59,0.65)';
    const mkRadar = (id, labels, data, color) => {
      const el = document.getElementById(id); if(!el) return;
      new Chart(el, { type:'radar', data:{ labels, datasets:[{ data, backgroundColor:color+'22', borderColor:color, borderWidth:2.5, pointBackgroundColor:color, pointRadius:4 }] },
        options:{ responsive:true, maintainAspectRatio:false, plugins:{ legend:{ display:false } },
          scales:{ r:{ min:0, max:5, ticks:{ stepSize:1, color:tc, font:{ size:9 }, backdropColor:'transparent' }, grid:{ color:gc }, angleLines:{ color:gc }, pointLabels:{ color:pc, font:{ size:10, weight:'500' } } } } } });
    };
    mkRadar(chartId1, CAP.map(c=>l(c.short)), capData.map(d=>+d.overall.toFixed(2)), '#2563EB');
    const lensAgg = LENS.map(ln => {
      const vals = profiles.flatMap(p=>CAP.map(cap=>capLensScore(p.responses,cap.id,ln.id)).filter(s=>s!==null));
      return vals.length ? +(vals.reduce((a,b)=>a+b,0)/vals.length).toFixed(2) : 0;
    });
    mkRadar(chartId2, LENS.map(ln=>l(ln.name)), lensAgg, '#0891B2');
  }, 80);
}

function renderProfile(body, p) {
  const idx = state.orgs.flatMap(o=>o.profiles).findIndex(q=>q.id===p.id);
  const pl = pal(idx < 0 ? 0 : idx);
  const org = findOrgOfProfile(p.id);
  const capData = CAP.map(cap => {
    const ls = {}; LENS.forEach(ln => { ls[ln.id] = capLensScore(p.responses, cap.id, ln.id); });
    return { cap, ls, overall: capScore(p.responses, cap.id) };
  });
  const hdr = document.createElement('div');
  hdr.style = 'display:flex;align-items:center;gap:12px;margin-bottom:1.5rem;flex-wrap:wrap;';
  hdr.innerHTML = `<div class="profile-avatar" style="background:${pl.bg};color:${pl.fg};width:44px;height:44px;">${ini(p.name)}</div>
    <div><div style="font-size:16px;font-weight:700;">${p.name}</div>
    <div style="font-size:12px;color:var(--text-muted);">${p.role||t('noRoleSpec')}${org?' · '+org.name:''}</div></div>
    <div style="margin-left:auto;display:flex;gap:8px;">
      <button class="btn btn-sm" onclick="openSurvey('${p.id}')">${t('editResponses')}</button>
      <button class="btn btn-sm btn-danger" onclick="deleteProfile('${p.id}')">${t('remove')}</button>
    </div>`;
  body.appendChild(hdr);
  const mg = document.createElement('div'); mg.className = 'metric-grid';
  capData.forEach(d => {
    mg.innerHTML += `<div class="metric-card"><div class="metric-cap">${l(d.cap.short)}</div>
      <div class="metric-score" style="color:${d.cap.color}">${d.overall!==null?d.overall.toFixed(1):'—'}<span class="metric-denom">/5</span></div></div>`;
  });
  body.appendChild(mg);
  const chartId = 'ra-prof-'+p.id+'-'+Date.now();
  const rc = document.createElement('div');
  rc.className = 'chart-card';
  rc.style = 'max-width:460px;margin:0 auto 1.5rem;';
  rc.innerHTML = `<div class="chart-title">${p.name}</div><div class="chart-wrap"><canvas id="${chartId}"></canvas></div>`;
  body.appendChild(rc);
  const st = document.createElement('div');
  st.innerHTML = `<p class="section-title">${t('breakdownTitle')}</p>
    <table class="score-table"><thead><tr>
      <th>${lang==='de'?'Fähigkeit':'Capability'}</th>
      ${LENS.map(ln=>`<th>${l(ln.name)}</th>`).join('')}
      <th>${t('overall')}</th>
    </tr></thead><tbody>${capData.map(d=>`<tr>
      <td><span style="display:inline-block;width:8px;height:8px;border-radius:50%;background:${d.cap.color};margin-right:6px;vertical-align:middle;"></span>${l(d.cap.short)}</td>
      ${LENS.map(ln=>`<td>${d.ls[ln.id]!==null?d.ls[ln.id].toFixed(1):'—'}</td>`).join('')}
      <td style="font-weight:700">${d.overall!==null?d.overall.toFixed(1):'—'}</td>
    </tr>`).join('')}</tbody></table>`;
  body.appendChild(st);
  setTimeout(() => {
    const dark = matchMedia('(prefers-color-scheme: dark)').matches;
    const gc = dark ? 'rgba(255,255,255,0.08)' : 'rgba(30,41,59,0.08)';
    const tc = dark ? 'rgba(255,255,255,0.35)' : 'rgba(30,41,59,0.4)';
    const pc = dark ? 'rgba(255,255,255,0.6)' : 'rgba(30,41,59,0.65)';
    const el = document.getElementById(chartId); if(!el) return;
    new Chart(el, { type:'radar', data:{ labels:CAP.map(c=>l(c.short)), datasets:[{
      data: capData.map(d=>d.overall!==null?+d.overall.toFixed(2):0),
      backgroundColor:pl.bg+'cc', borderColor:pl.fg, borderWidth:2.5, pointBackgroundColor:pl.fg, pointRadius:4
    }] }, options:{ responsive:true, maintainAspectRatio:false, plugins:{ legend:{ display:false } },
      scales:{ r:{ min:0, max:5, ticks:{ stepSize:1, color:tc, font:{ size:9 }, backdropColor:'transparent' }, grid:{ color:gc }, angleLines:{ color:gc }, pointLabels:{ color:pc, font:{ size:10 } } } } } });
  }, 80);
}

function deleteProfile(pid) {
  if (!confirm(t('removeConfirm'))) return;
  state.orgs.forEach(o => { o.profiles = o.profiles.filter(p=>p.id!==pid); });
  save(); currentTab='aggregate'; renderResults();
}

function exportData() {
  const blob = new Blob([JSON.stringify(state, null, 2)], { type:'application/json' });
  const a = document.createElement('a'); a.href = URL.createObjectURL(blob);
  a.download = 'arcmm_responses_'+new Date().toISOString().slice(0,10)+'.json'; a.click();
}

function resetAll() {
  if (!confirm(t('resetConfirm'))) return;
  state = { orgs:[] }; save(); activeOrgId=null; currentTab='aggregate';
  Object.keys(charts).forEach(k=>{ try{charts[k].destroy();}catch(e){} delete charts[k]; });
  goHome();
}

load();
renderHome();
initAuth();
</script>
</body>
</html>
