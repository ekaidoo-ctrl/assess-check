<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ASP122A · Student Results Portal | UCC Nyakrom</title>
<style>
/* ═══════════════════════════════════════════
   DESIGN TOKENS
═══════════════════════════════════════════ */
:root {
  /* UCC Brand */
  --ucc-navy:   #003580;
  --ucc-gold:   #F0A500;
  --ucc-gold-l: #FFD166;

/* Page & Card Surfaces */
–bg:         #1A2744;
–surface:    #FFFFFF;
–surface-2:  #EBF0FA;
–border:     #C0CCDE;
–border-2:   #8FA0BC;

/* Text — always on white cards */
–text-h:     #080F1E;
–text-b:     #111C2E;
–text-m:     #2E4060;
–text-lt:    #4E6280;

/* Accent */
–blue:       #1559CC;
–blue-l:     #E0EAFF;
–blue-d:     #0E429E;
–green:      #0E7040;
–green-l:    #D8F5E8;
–amber:      #A85000;
–amber-l:    #FFF0D6;
–red:        #B02020;
–red-l:      #FDECEC;

/* Grades */
–ga:   #0A5C28; –ga-bg:   #D6F0E0;
–gbp:  #0E429E; –gbp-bg:  #D6E8FF;
–gb:   #0E429E; –gb-bg:   #E0EDFF;
–gcp:  #7A4500; –gcp-bg:  #FFEACC;
–gc:   #7A4500; –gc-bg:   #FFF3DC;
–gdp:  #A04000; –gdp-bg:  #FFE5CC;
–gd:   #A04000; –gd-bg:   #FFEEDD;
–ge:   #8B1A1A; –ge-bg:   #FDDADA;
–gic:  #3A5068; –gic-bg:  #E4ECF4;

–radius: 10px;
–shadow-sm: 0 2px 6px rgba(0,0,0,.12);
–shadow:    0 6px 20px rgba(0,0,0,.16);
–shadow-lg: 0 12px 36px rgba(0,0,0,.20);
}

/* ═══════════════════════════════════════════
RESET & BASE
═══════════════════════════════════════════ */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

body {
font-family: -apple-system, BlinkMacSystemFont, ‘Segoe UI’, Roboto, Arial, sans-serif;
background: var(–bg);
color: var(–text-b);
font-size: 15px;
line-height: 1.5;
min-height: 100vh;
}

/* ═══════════════════════════════════════════
HEADER
═══════════════════════════════════════════ */
.site-header {
background: linear-gradient(90deg, #001A4E 0%, #003080 100%);
color: #fff;
position: sticky;
top: 0;
z-index: 200;
box-shadow: 0 3px 12px rgba(0,0,0,.35);
border-bottom: 3px solid #F0A500;
}

.header-inner {
max-width: 960px;
margin: 0 auto;
padding: 0 20px;
height: 60px;
display: flex;
align-items: center;
justify-content: space-between;
gap: 16px;
}

.header-brand {
display: flex;
align-items: center;
gap: 12px;
}

.brand-crest {
width: 36px; height: 36px;
background: var(–ucc-gold);
border-radius: 6px;
display: flex; align-items: center; justify-content: center;
font-weight: 900; font-size: 13px;
color: var(–ucc-navy);
letter-spacing: .3px;
flex-shrink: 0;
}

.brand-text { line-height: 1.25; }
.brand-text .brand-name {
font-size: .95rem;
font-weight: 700;
color: #fff;
display: block;
}
.brand-text .brand-sub {
font-size: .7rem;
color: rgba(255,255,255,.6);
display: block;
}

.header-right { display: flex; align-items: center; gap: 10px; }

.live-badge {
display: flex; align-items: center; gap: 6px;
background: rgba(255,255,255,.1);
border: 1px solid rgba(255,255,255,.2);
border-radius: 99px;
padding: 4px 12px;
font-size: .72rem;
color: rgba(255,255,255,.85);
}
.live-dot {
width: 7px; height: 7px;
border-radius: 50%;
background: #4CAF50;
box-shadow: 0 0 0 2px rgba(76,175,80,.3);
animation: blink 2s ease infinite;
}
@keyframes blink { 0%,100%{opacity:1} 50%{opacity:.4} }

#btn-signout {
display: none;
background: rgba(255,255,255,.12);
border: 1px solid rgba(255,255,255,.25);
border-radius: var(–radius);
color: #fff;
padding: 6px 14px;
font-size: .8rem;
font-weight: 600;
cursor: pointer;
transition: background .15s;
}
#btn-signout:hover { background: rgba(255,255,255,.22); }

/* ═══════════════════════════════════════════
MAIN WRAPPER
═══════════════════════════════════════════ */
main {
max-width: 960px;
margin: 0 auto;
padding: 32px 20px 60px;
}

/* ═══════════════════════════════════════════
SCREENS
═══════════════════════════════════════════ */
.screen { display: none; }
.screen.active { display: block; }

/* ═══════════════════════════════════════════
LOGIN SCREEN
═══════════════════════════════════════════ */
#screen-login {
max-width: 440px;
margin: 0 auto;
}

.login-hero {
text-align: center;
margin-bottom: 28px;
}

.login-hero .hero-icon {
width: 72px; height: 72px;
background: linear-gradient(135deg, #0A5EC0, #F0A500);
border-radius: 18px;
display: flex; align-items: center; justify-content: center;
margin: 0 auto 16px;
font-size: 30px;
box-shadow: var(–shadow);
}

.login-hero h1 {
font-size: 1.5rem;
font-weight: 800;
color: var(–text-h);
margin-bottom: 6px;
}

.login-hero p {
font-size: .875rem;
color: var(–text-m);
line-height: 1.6;
}

.login-hero p strong { color: var(–ucc-navy); }

/* Card */
.card {
background: #FFFFFF;
border: 1px solid #C0CCDE;
border-radius: var(–radius);
box-shadow: 0 6px 24px rgba(0,0,0,.18);
border-top: 5px solid #F0A500;
}

.card-body { padding: 28px; }

/* Form */
.form-group { margin-bottom: 18px; }

.form-group label {
display: block;
font-size: .8rem;
font-weight: 700;
color: var(–text-m);
text-transform: uppercase;
letter-spacing: .6px;
margin-bottom: 7px;
}

.input-wrap { position: relative; }

.form-control {
display: block;
width: 100%;
padding: 11px 14px;
font-size: .95rem;
font-family: inherit;
color: var(–text-h);
background: var(–surface);
border: 1.5px solid var(–border-2);
border-radius: var(–radius);
outline: none;
transition: border-color .15s, box-shadow .15s;
}

.form-control::placeholder { color: var(–text-lt); }

.form-control:focus {
border-color: var(–ucc-navy);
box-shadow: 0 0 0 3px rgba(0,33,71,.1);
}

.toggle-pw {
position: absolute;
right: 12px; top: 50%;
transform: translateY(-50%);
background: none; border: none;
cursor: pointer;
color: var(–text-lt);
font-size: 15px;
padding: 4px;
line-height: 1;
transition: color .15s;
}
.toggle-pw:hover { color: var(–text-m); }

/* Alert */
.alert {
display: none;
align-items: flex-start;
gap: 10px;
padding: 11px 14px;
border-radius: var(–radius);
font-size: .855rem;
margin-bottom: 16px;
}
.alert.show { display: flex; }
.alert-error {
background: var(–red-l);
border: 1px solid #f5c0bb;
color: var(–red);
}
.alert-icon { font-size: 16px; flex-shrink: 0; margin-top: 1px; }

/* Buttons */
.btn {
display: inline-flex;
align-items: center;
justify-content: center;
gap: 8px;
padding: 12px 22px;
border: none;
border-radius: var(–radius);
font-family: inherit;
font-size: .93rem;
font-weight: 700;
cursor: pointer;
transition: background .15s, transform .1s, box-shadow .15s;
text-decoration: none;
}
.btn:active { transform: scale(.98); }

.btn-primary {
background: var(–ucc-navy);
color: #fff;
width: 100%;
font-size: 1rem;
padding: 13px;
box-shadow: 0 3px 10px rgba(0,33,71,.25);
}
.btn-primary:hover { background: #00316B; box-shadow: 0 5px 14px rgba(0,33,71,.3); }

.btn-danger {
background: var(–red-l);
color: var(–red);
border: 1px solid #f5c0bb;
padding: 8px 16px;
font-size: .83rem;
}
.btn-danger:hover { background: #fce8e6; }

.btn-outline {
background: var(–surface);
color: var(–ucc-navy);
border: 1.5px solid var(–ucc-navy);
padding: 8px 16px;
font-size: .83rem;
}
.btn-outline:hover { background: var(–blue-l); }

/* Hint box */
.hint-box {
background: #E8F0FF;
border: 1.5px solid #9BBCF0;
border-radius: var(–radius);
padding: 14px 16px;
margin-top: 18px;
}
.hint-box .hint-title {
font-size: .78rem;
font-weight: 700;
color: var(–blue-d);
text-transform: uppercase;
letter-spacing: .5px;
margin-bottom: 6px;
display: flex; align-items: center; gap: 6px;
}
.hint-box .hint-body {
font-size: .83rem;
color: var(–text-m);
line-height: 1.7;
}
.hint-box code {
background: rgba(26,111,191,.12);
color: var(–blue-d);
padding: 1px 6px;
border-radius: 4px;
font-size: .82rem;
font-family: ‘Courier New’, monospace;
font-weight: 600;
}

/* ═══════════════════════════════════════════
DASHBOARD SCREEN
═══════════════════════════════════════════ */

/* Top banner */
.student-banner {
background: linear-gradient(135deg, #0A5EC0 0%, #0D3A7A 60%, #001F55 100%);
border-radius: var(–radius);
padding: 22px 26px;
color: #fff;
margin-bottom: 24px;
box-shadow: 0 6px 24px rgba(0,0,0,.22);
display: flex;
align-items: flex-start;
justify-content: space-between;
gap: 16px;
flex-wrap: wrap;
}

.student-banner .s-label {
font-size: .72rem;
font-weight: 600;
text-transform: uppercase;
letter-spacing: .7px;
color: rgba(255,255,255,.55);
margin-bottom: 4px;
}

.student-banner .s-name {
font-size: 1.35rem;
font-weight: 800;
color: #fff;
line-height: 1.2;
margin-bottom: 4px;
}

.student-banner .s-meta {
font-size: .82rem;
color: rgba(255,255,255,.65);
}

.s-group-badge {
display: inline-flex;
align-items: center;
background: var(–ucc-gold);
color: var(–ucc-navy);
border-radius: 99px;
padding: 4px 12px;
font-size: .72rem;
font-weight: 800;
letter-spacing: .4px;
margin-top: 8px;
white-space: nowrap;
}

/* Stats row */
.stats-row {
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 14px;
margin-bottom: 24px;
}

.stat-card {
background: #FFFFFF;
border: 2px solid #C0CCDE;
border-radius: var(–radius);
padding: 16px 18px;
box-shadow: 0 3px 10px rgba(0,0,0,.12);
transition: box-shadow .15s, transform .15s;
}
.stat-card:hover { box-shadow: var(–shadow); }

.stat-card .sc-label {
font-size: .72rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .6px;
color: #2E4060;
margin-bottom: 6px;
}

.stat-card .sc-value {
font-size: 1.7rem;
font-weight: 800;
color: #080F1E;
line-height: 1;
}

.stat-card .sc-sub {
font-size: .72rem;
color: var(–text-lt);
margin-top: 3px;
}

.stat-card.sc-primary { border-color: #1559CC; border-top: 4px solid #1559CC; }
.stat-card.sc-primary .sc-value { color: #1559CC; }
.stat-card.sc-grade { border-top: 4px solid #F0A500; }
.stat-card.sc-green   .sc-value { color: var(–green); }
.stat-card.sc-grade   .sc-value { font-size: 1.5rem; }

/* Tabs */
.tab-bar {
display: flex;
background: #FFFFFF;
border: 1.5px solid #C0CCDE;
border-radius: var(–radius);
padding: 5px;
gap: 4px;
margin-bottom: 20px;
box-shadow: var(–shadow-sm);
}

.tab-btn {
flex: 1;
padding: 9px 14px;
border: none;
border-radius: 7px;
background: transparent;
color: var(–text-m);
font-family: inherit;
font-size: .85rem;
font-weight: 600;
cursor: pointer;
transition: all .15s;
white-space: nowrap;
}
.tab-btn:hover { background: var(–surface-2); color: var(–text-h); }
.tab-btn.active {
background: linear-gradient(135deg, #1559CC, #003080);
color: #fff;
box-shadow: 0 3px 10px rgba(21,89,204,.3);
}

/* Panel */
.tab-panel { display: none; }
.tab-panel.active { display: block; }

/* ─── SCORES PANEL ──────────────────────────────── */

/* Component breakdown */
.comp-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 14px;
margin-bottom: 20px;
}

.comp-card {
background: #FFFFFF;
border: 1px solid #C0CCDE;
border-radius: var(–radius);
padding: 18px 16px;
box-shadow: var(–shadow-sm);
position: relative;
overflow: hidden;
}

.comp-card::before {
content: ‘’;
position: absolute;
top: 0; left: 0; right: 0;
height: 3px;
}
.comp-cat::before  { background: #1559CC; }
.comp-cat  { background: linear-gradient(160deg,#EEF4FF 0%,#FFFFFF 60%); }
.comp-q1::before   { background: #7B2D8B; }
.comp-q1   { background: linear-gradient(160deg,#F7EEFF 0%,#FFFFFF 60%); }
.comp-q2::before   { background: #D4840A; }
.comp-q2   { background: linear-gradient(160deg,#FFF8E6 0%,#FFFFFF 60%); }

.comp-label {
font-size: .72rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .6px;
margin-bottom: 10px;
}
.comp-cat  .comp-label { color: #1A6FBF; }
.comp-q1   .comp-label { color: #7B2D8B; }
.comp-q2   .comp-label { color: #C49A00; }

.comp-score {
font-size: 2.1rem;
font-weight: 800;
color: var(–text-h);
line-height: 1;
}
.comp-max {
font-size: .75rem;
color: var(–text-lt);
margin-top: 4px;
}

.comp-bar {
height: 5px;
background: var(–border);
border-radius: 99px;
margin-top: 12px;
overflow: hidden;
}
.comp-bar-fill {
height: 100%;
border-radius: 99px;
transition: width .7s ease;
}
.comp-cat  .comp-bar-fill { background: #1A6FBF; }
.comp-q1   .comp-bar-fill { background: #7B2D8B; }
.comp-q2   .comp-bar-fill { background: #C49A00; }

/* Summary card */
.summary-card {
background: var(–surface);
border: 1px solid var(–border);
border-radius: var(–radius);
box-shadow: var(–shadow-sm);
overflow: hidden;
margin-bottom: 20px;
}

.summary-header {
background: linear-gradient(90deg, #EBF0FA, #F5F8FF);
border-bottom: 1.5px solid #C0CCDE;
padding: 14px 20px;
display: flex;
align-items: center;
justify-content: space-between;
}

.summary-header .sh-title {
font-size: .8rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .6px;
color: var(–text-m);
}

.summary-body {
padding: 20px;
display: flex;
align-items: center;
gap: 24px;
}

.grade-ring {
width: 80px; height: 80px;
flex-shrink: 0;
border-radius: 50%;
display: flex; align-items: center; justify-content: center;
font-size: 1.6rem; font-weight: 900;
border: 4px solid transparent;
}

.grade-A   { background:var(–ga-bg);  color:var(–ga);  border-color:var(–ga); }
.grade-Bplus,.grade-B  { background:var(–gbp-bg); color:var(–gbp); border-color:var(–gbp); }
.grade-Cplus,.grade-C  { background:var(–gcp-bg); color:var(–gcp); border-color:var(–gcp); }
.grade-Dplus,.grade-D  { background:var(–gdp-bg); color:var(–gdp); border-color:var(–gdp); }
.grade-E   { background:var(–ge-bg);  color:var(–ge);  border-color:var(–ge); }
.grade-IC  { background:var(–gic-bg); color:var(–gic); border-color:var(–border-2); border-style:dashed; font-size:1.1rem; }

.summary-scores { flex: 1; }

.score-row {
display: flex;
align-items: center;
margin-bottom: 10px;
}
.score-row:last-child { margin-bottom: 0; }

.score-row-label {
font-size: .78rem;
color: var(–text-m);
font-weight: 600;
width: 120px;
flex-shrink: 0;
}
.score-row-bar {
flex: 1;
height: 8px;
background: var(–border);
border-radius: 99px;
overflow: hidden;
margin: 0 12px;
}
.score-row-fill {
height: 100%;
border-radius: 99px;
background: var(–ucc-navy);
transition: width .7s ease;
}
.score-row-val {
font-size: .83rem;
font-weight: 700;
color: var(–text-h);
width: 55px;
text-align: right;
flex-shrink: 0;
}

.ic-notice {
background: var(–amber-l);
border: 1px solid #F5D5A5;
border-radius: var(–radius);
padding: 13px 16px;
font-size: .855rem;
color: var(–amber);
line-height: 1.6;
margin-bottom: 20px;
display: flex;
gap: 10px;
align-items: flex-start;
}
.ic-notice .ic-icon { font-size: 18px; flex-shrink: 0; }

/* Grade key */
.grade-key-card {
background: var(–surface);
border: 1px solid var(–border);
border-radius: var(–radius);
box-shadow: var(–shadow-sm);
overflow: hidden;
}

.grade-key-header {
background: linear-gradient(90deg, #FFF8E0, #FFFBF0);
border-bottom: 1.5px solid #E0C060;
padding: 12px 20px;
font-size: .78rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: .6px;
color: var(–text-m);
}

.grade-key-body {
padding: 16px 20px;
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 10px;
}

.gk-item {
text-align: center;
padding: 10px 8px;
border-radius: 8px;
border: 1px solid var(–border);
}
.gk-grade { font-size: 1.1rem; font-weight: 800; margin-bottom: 3px; }
.gk-range { font-size: .68rem; color: var(–text-lt); }

.gk-A     { background:var(–ga-bg);  color:var(–ga); }
.gk-Bplus { background:var(–gbp-bg); color:var(–gbp); }
.gk-B     { background:var(–gb-bg);  color:var(–gb); }
.gk-Cplus { background:var(–gcp-bg); color:var(–gcp); }
.gk-C     { background:var(–gc-bg);  color:var(–gc); }
.gk-Dplus { background:var(–gdp-bg); color:var(–gdp); }
.gk-D     { background:var(–gd-bg);  color:var(–gd); }
.gk-E     { background:var(–ge-bg);  color:var(–ge); }

/* ─── COMPLAINT PANEL ───────────────────────────── */
.section-notice {
background: var(–amber-l);
border: 1px solid #F5D5A5;
border-radius: var(–radius);
padding: 14px 16px;
font-size: .855rem;
color: var(–text-b);
line-height: 1.65;
margin-bottom: 20px;
}
.section-notice strong { color: var(–amber); }

.complaint-form-card {
background: var(–surface);
border: 1px solid var(–border);
border-radius: var(–radius);
box-shadow: var(–shadow-sm);
padding: 28px;
}

.row-2 {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 16px;
}

.form-divider {
height: 1px;
background: var(–border);
margin: 20px 0;
}

.upload-zone {
border: 2px dashed var(–border-2);
border-radius: var(–radius);
padding: 24px;
text-align: center;
cursor: pointer;
background: var(–surface-2);
position: relative;
transition: border-color .15s, background .15s;
}
.upload-zone:hover { border-color: var(–ucc-navy); background: var(–blue-l); }
.upload-zone input[type=“file”] { position: absolute; inset: 0; opacity: 0; cursor: pointer; width: 100%; height: 100%; }
.upload-icon { font-size: 2rem; margin-bottom: 8px; }
.upload-text { font-size: .845rem; color: var(–text-m); }
.upload-text strong { color: var(–ucc-navy); }
.upload-filename { font-size: .8rem; color: var(–green); font-weight: 600; margin-top: 8px; display: none; }

.success-alert {
display: none;
background: var(–green-l);
border: 1px solid #A8DFC0;
border-radius: var(–radius);
padding: 16px 18px;
margin-top: 18px;
font-size: .875rem;
color: var(–green);
line-height: 1.6;
}
.success-alert .sa-title { font-weight: 700; font-size: .95rem; margin-bottom: 4px; }

/* ═══════════════════════════════════════════
FOOTER
═══════════════════════════════════════════ */
.site-footer {
background: var(–ucc-navy);
color: rgba(255,255,255,.55);
text-align: center;
padding: 20px 24px;
font-size: .75rem;
line-height: 1.9;
margin-top: auto;
}
.site-footer strong { color: rgba(255,255,255,.9); }

/* ═══════════════════════════════════════════
RESPONSIVE
═══════════════════════════════════════════ */
@media (max-width: 640px) {
main { padding: 20px 14px 40px; }
.stats-row { grid-template-columns: 1fr 1fr; }
.comp-grid  { grid-template-columns: 1fr; }
.row-2      { grid-template-columns: 1fr; }
.grade-key-body { grid-template-columns: repeat(4, 1fr); gap: 6px; }
.summary-body { flex-direction: column; align-items: flex-start; }
.grade-ring { width: 64px; height: 64px; font-size: 1.3rem; }
.student-banner { padding: 16px 18px; }
.student-banner .s-name { font-size: 1.1rem; }
.tab-btn { font-size: .78rem; padding: 8px 10px; }
.card-body { padding: 20px; }
.complaint-form-card { padding: 18px; }
}

@media (max-width: 400px) {
.grade-key-body { grid-template-columns: repeat(4,1fr); gap: 4px; }
.gk-grade { font-size: .95rem; }
}

/* Select element fix */
select.form-control {
appearance: none;
background-image: url(“data:image/svg+xml,%3Csvg xmlns=‘http://www.w3.org/2000/svg’ width=‘12’ height=‘8’ viewBox=‘0 0 12 8’%3E%3Cpath d=‘M1 1l5 5 5-5’ stroke=’%234A5D73’ stroke-width=‘1.5’ fill=‘none’ stroke-linecap=‘round’/%3E%3C/svg%3E”);
background-repeat: no-repeat;
background-position: right 14px center;
padding-right: 36px;
}

/* Textarea */
textarea.form-control {
resize: vertical;
min-height: 100px;
}

/* Readonly muted */
.form-control[readonly] {
background: var(–surface-2);
color: var(–text-m);
cursor: default;
}
</style>

</head>
<body>

<!-- ══════════════════════════════════════════════
     HEADER
══════════════════════════════════════════════════ -->

<header class="site-header">
  <div class="header-inner">
    <div class="header-brand">
      <div class="brand-crest">UCC</div>
      <div class="brand-text">
        <span class="brand-name">Nyakrom Results Portal</span>
        <span class="brand-sub">ASP122A · 2025/2026 First Semester</span>
      </div>
    </div>
    <div class="header-right">
      <div class="live-badge"><div class="live-dot"></div> Results Live</div>
      <button id="btn-signout" onclick="signOut()">Sign Out</button>
    </div>
  </div>
</header>

<!-- ══════════════════════════════════════════════
     MAIN
══════════════════════════════════════════════════ -->

<main>

  <!-- ── LOGIN ─────────────────────────────────── -->

  <div class="screen active" id="screen-login">

```
<div class="login-hero">
  <div class="hero-icon">🎓</div>
  <h1>Student Login</h1>
  <p>Access your Continuous Assessment scores for<br>
     <strong>ASP122A: Comparative Analysis of Economic Development<br>in Africa &amp; the Caribbean</strong></p>
</div>

<div class="card">
  <div class="card-body">

    <div class="alert alert-error" id="login-alert" role="alert">
      <span class="alert-icon">⚠️</span>
      <span id="login-alert-msg">Incorrect index number or password. Please check and try again.</span>
    </div>

    <div class="form-group">
      <label for="inp-index">Index Number</label>
      <input
        class="form-control"
        type="text"
        id="inp-index"
        placeholder="e.g. SN/NSU/25/0042"
        autocomplete="off"
        autocapitalize="characters"
        spellcheck="false"
        onkeydown="if(event.key==='Enter')doLogin()"
      >
    </div>

    <div class="form-group">
      <label for="inp-pw">Password</label>
      <div class="input-wrap">
        <input
          class="form-control"
          type="password"
          id="inp-pw"
          placeholder="e.g. SN0042"
          autocomplete="off"
          onkeydown="if(event.key==='Enter')doLogin()"
        >
        <button class="toggle-pw" type="button" onclick="togglePw()" aria-label="Show/hide password">👁</button>
      </div>
    </div>

    <button class="btn btn-primary" onclick="doLogin()">
      Sign In &rarr;
    </button>

  </div>
</div>

<div class="hint-box" style="margin-top:16px;">
  <div class="hint-title">ℹ️ &nbsp;Login Instructions</div>
  <div class="hint-body">
    <strong>Username:</strong> Your full index number exactly as shown on your student ID<br>
    <strong>Password:</strong> First 2 letters of your index + last 4 digits<br><br>
    Examples:<br>
    &nbsp;Index <code>SN/NSU/25/0001</code> → Password <code>SN0001</code><br>
    &nbsp;Index <code>AH/NRT/25/0015</code> → Password <code>AH0015</code><br>
    &nbsp;Index <code>SN/NSU/25/0141</code> → Password <code>SN0141</code>
  </div>
</div>
```

  </div><!-- /screen-login -->

  <!-- ── DASHBOARD ──────────────────────────────── -->

  <div class="screen" id="screen-dash">

```
<!-- Student banner -->
<div class="student-banner">
  <div>
    <div class="s-label">Logged in as</div>
    <div class="s-name" id="d-name">—</div>
    <div class="s-meta"><span id="d-index">—</span> &nbsp;·&nbsp; ASP122A &nbsp;·&nbsp; 2025/2026 First Semester</div>
    <div class="s-group-badge" id="d-group">—</div>
  </div>
  <div style="text-align:right;">
    <div class="s-label" style="margin-bottom:8px;">Course Lecturer</div>
    <div style="font-size:.9rem;color:#fff;font-weight:600;">Emmanuel Aidoo</div>
    <div style="font-size:.75rem;color:rgba(255,255,255,.55);margin-top:2px;">Centre for African &amp; International Studies</div>
  </div>
</div>

<!-- Stats -->
<div class="stats-row">
  <div class="stat-card sc-primary">
    <div class="sc-label">CA Sub Total</div>
    <div class="sc-value" id="st-sub">—</div>
    <div class="sc-sub">Scaled to / 40</div>
  </div>
  <div class="stat-card">
    <div class="sc-label">Raw CA Total</div>
    <div class="sc-value" id="st-raw">—</div>
    <div class="sc-sub">Out of / 55</div>
  </div>
  <div class="stat-card sc-grade">
    <div class="sc-label">Current Grade</div>
    <div class="sc-value" id="st-grade">IC</div>
    <div class="sc-sub">Awaiting exam</div>
  </div>
  <div class="stat-card">
    <div class="sc-label">Complaints Filed</div>
    <div class="sc-value" id="st-complaints">0</div>
    <div class="sc-sub">This session</div>
  </div>
</div>

<!-- Tab bar -->
<div class="tab-bar" role="tablist">
  <button class="tab-btn active" onclick="switchTab('scores')" role="tab">📊 &nbsp;My CA Scores</button>
  <button class="tab-btn" onclick="switchTab('complaint')" role="tab">📝 &nbsp;Lodge Complaint</button>
</div>

<!-- ─── SCORES PANEL ─────────────────────────── -->
<div class="tab-panel active" id="panel-scores">

  <!-- Component cards -->
  <div class="comp-grid">
    <div class="comp-card comp-cat">
      <div class="comp-label">Class Test (CAT)</div>
      <div class="comp-score" id="sc-cat">—</div>
      <div class="comp-max">out of 5</div>
      <div class="comp-bar"><div class="comp-bar-fill" id="bar-cat" style="width:0%"></div></div>
    </div>
    <div class="comp-card comp-q1">
      <div class="comp-label">Quiz 1 (CA 2)</div>
      <div class="comp-score" id="sc-q1">—</div>
      <div class="comp-max">out of 20</div>
      <div class="comp-bar"><div class="comp-bar-fill" id="bar-q1" style="width:0%"></div></div>
    </div>
    <div class="comp-card comp-q2">
      <div class="comp-label">Quiz 2 (CA 3)</div>
      <div class="comp-score" id="sc-q2">—</div>
      <div class="comp-max">out of 30</div>
      <div class="comp-bar"><div class="comp-bar-fill" id="bar-q2" style="width:0%"></div></div>
    </div>
  </div>

  <!-- IC notice -->
  <div class="ic-notice">
    <span class="ic-icon">ℹ️</span>
    <span>Your CA Sub Total of <strong id="note-sub">—</strong> out of 40 represents your Continuous Assessment contribution (<strong>40%</strong> of final grade). Your grade currently shows <strong>IC (Incomplete)</strong> because the End-of-Semester Examination score (<strong>60%</strong>) has not yet been recorded. Your final grade will be computed once examination marks are entered.</span>
  </div>

  <!-- Summary card -->
  <div class="summary-card">
    <div class="summary-header">
      <span class="sh-title">Assessment Summary</span>
      <span style="font-size:.8rem;color:var(--text-lt)">2025/2026 First Semester CA</span>
    </div>
    <div class="summary-body">
      <div class="grade-ring grade-IC" id="grade-ring">IC</div>
      <div class="summary-scores" style="flex:1;">
        <div class="score-row">
          <div class="score-row-label">CA Total (/ 55)</div>
          <div class="score-row-bar"><div class="score-row-fill" id="fill-raw" style="width:0%;background:#1A6FBF"></div></div>
          <div class="score-row-val" id="val-raw">—</div>
        </div>
        <div class="score-row">
          <div class="score-row-label">CA Score (/ 40)</div>
          <div class="score-row-bar"><div class="score-row-fill" id="fill-sub" style="width:0%;background:var(--ucc-navy)"></div></div>
          <div class="score-row-val" id="val-sub">—</div>
        </div>
        <div class="score-row">
          <div class="score-row-label">Final Score (/ 100)</div>
          <div class="score-row-bar"><div class="score-row-fill" id="fill-total" style="width:0%;background:#888;opacity:.4"></div></div>
          <div class="score-row-val" style="color:var(--text-lt)">Pending</div>
        </div>
      </div>
    </div>
  </div>

  <!-- Grade key -->
  <div class="grade-key-card">
    <div class="grade-key-header">UCC Grading System</div>
    <div class="grade-key-body">
      <div class="gk-item gk-A">    <div class="gk-grade">A</div>   <div class="gk-range">80 – 100</div></div>
      <div class="gk-item gk-Bplus"><div class="gk-grade">B+</div>  <div class="gk-range">75 – 79</div></div>
      <div class="gk-item gk-B">    <div class="gk-grade">B</div>   <div class="gk-range">70 – 74</div></div>
      <div class="gk-item gk-Cplus"><div class="gk-grade">C+</div>  <div class="gk-range">65 – 69</div></div>
      <div class="gk-item gk-C">    <div class="gk-grade">C</div>   <div class="gk-range">60 – 64</div></div>
      <div class="gk-item gk-Dplus"><div class="gk-grade">D+</div>  <div class="gk-range">55 – 59</div></div>
      <div class="gk-item gk-D">    <div class="gk-grade">D</div>   <div class="gk-range">50 – 54</div></div>
      <div class="gk-item gk-E">    <div class="gk-grade">E</div>   <div class="gk-range">&lt; 50</div></div>
    </div>
  </div>

</div><!-- /panel-scores -->


<!-- ─── COMPLAINT PANEL ──────────────────────── -->
<div class="tab-panel" id="panel-complaint">

  <div class="section-notice">
    <strong>Please read before submitting:</strong> First verify your scores on the <em>My CA Scores</em> tab. Identify the specific component you are disputing. The <strong>ASP122A course lecturer</strong> will review all complaints within <strong>5 working days</strong>. Note that a re-mark may result in a score adjustment in either direction. Attach your marked script where a score has been omitted or appears incorrectly recorded.
  </div>

  <div class="complaint-form-card">

    <div class="row-2">
      <div class="form-group">
        <label>Full Name</label>
        <input class="form-control" type="text" id="c-name" placeholder="Your full name">
      </div>
      <div class="form-group">
        <label>Index Number</label>
        <input class="form-control" type="text" id="c-index" readonly>
      </div>
    </div>

    <div class="row-2">
      <div class="form-group">
        <label>Programme</label>
        <input class="form-control" type="text" id="c-prog" readonly>
      </div>
      <div class="form-group">
        <label>Email Address (optional)</label>
        <input class="form-control" type="email" id="c-email" placeholder="your@email.com">
      </div>
    </div>

    <div class="form-group">
      <label>Component in Dispute</label>
      <select class="form-control" id="c-component">
        <option value="">— Select the affected component —</option>
        <option>Class Test / CAT (CA 1) — out of 5</option>
        <option>Quiz 1 (CA 2) — out of 20</option>
        <option>Quiz 2 (CA 3) — out of 30</option>
        <option>CA Sub Total (scaled to 40)</option>
        <option>Score not recorded — complete omission</option>
      </select>
    </div>

    <div class="row-2">
      <div class="form-group">
        <label>Score Displayed</label>
        <input class="form-control" type="text" id="c-shown" placeholder="Score currently showing">
      </div>
      <div class="form-group">
        <label>Expected Score</label>
        <input class="form-control" type="text" id="c-expected" placeholder="Score you believe is correct">
      </div>
    </div>

    <div class="form-group">
      <label>Details of Complaint</label>
      <textarea class="form-control" id="c-detail" placeholder="Describe clearly: what score is shown, what score you expect, and why — e.g. a question was marked correct on your script but the mark was not counted, or your script was submitted but your score was not recorded."></textarea>
    </div>

    <div class="form-divider"></div>

    <div class="form-group">
      <label>Attach Marked Script <span style="font-weight:400;text-transform:none;letter-spacing:0">(strongly recommended for omissions)</span></label>
      <div class="upload-zone">
        <input type="file" id="c-file" accept=".pdf,.jpg,.jpeg,.png" onchange="handleFile(this)">
        <div class="upload-icon">📎</div>
        <p class="upload-text">Drag &amp; drop your file here, or <strong>click to browse</strong></p>
        <p class="upload-text" style="margin-top:4px;font-size:.78rem;">Accepted: PDF, JPG, PNG &nbsp;·&nbsp; Max 10 MB</p>
        <p class="upload-filename" id="fname"></p>
      </div>
    </div>

    <button class="btn btn-primary" onclick="submitComplaint()">
      Submit Complaint &rarr;
    </button>

    <div class="success-alert" id="success-alert">
      <div class="sa-title">✅ Complaint Submitted Successfully</div>
      Your ASP122A complaint has been recorded and forwarded to the course lecturer for review. You should receive a response within <strong>5 working days</strong>. Please retain your original marked script until the matter is formally resolved.
    </div>

  </div>
</div><!-- /panel-complaint -->
```

  </div><!-- /screen-dash -->

</main>

<!-- ══════════════════════════════════════════════
     FOOTER
══════════════════════════════════════════════════ -->

<footer class="site-footer">
  <strong>ASP122A: Comparative Analysis of Economic Development in Africa and the Caribbean</strong><br>
  Centre for African &amp; International Studies &nbsp;·&nbsp; Faculty of Arts &nbsp;·&nbsp; University of Cape Coast, Nyakrom<br>
  2025/2026 First Semester &nbsp;·&nbsp; Continuous Assessment Records &nbsp;·&nbsp; Lecturer: Emmanuel Aidoo
</footer>

<!-- ══════════════════════════════════════════════
     JAVASCRIPT
══════════════════════════════════════════════════ -->

<script>
/* ─────────────────────────────────────────────────────────────
   STUDENT DATA
   Source: UCC_ASP122A_Assessment_Sheet_2025_2026.xlsx
   Fields: no, name, cat(/5), quiz1(/20), quiz2(/30), sub(/40), group
───────────────────────────────────────────────────────────── */
const STUDENTS = {"SN/NSU/25/0001":{"no":1,"name":"MISHIWO, ALEXANDRA","cat":5.0,"quiz1":19.0,"quiz2":18.0,"sub":30.5,"group":"BSc Nursing"},"SN/NSU/25/0002":{"no":2,"name":"YAMOAH, MILLICENT","cat":2.0,"quiz1":7.0,"quiz2":5.0,"sub":10.2,"group":"BSc Nursing"},"SN/NSU/25/0003":{"no":3,"name":"VIGLO, HELENA","cat":5.0,"quiz1":8.5,"quiz2":8.0,"sub":15.6,"group":"BSc Nursing"},"SN/NSU/25/0004":{"no":4,"name":"ADU, MERCY AKOMABEA","cat":3.0,"quiz1":19.0,"quiz2":10.0,"sub":23.3,"group":"BSc Nursing"},"SN/NSU/25/0005":{"no":5,"name":"AGBAKPOE, MARVEL NUSIMEBIA","cat":5.0,"quiz1":6.5,"quiz2":12.5,"sub":17.5,"group":"BSc Nursing"},"SN/NSU/25/0006":{"no":6,"name":"OSEI, MABEL","cat":2.5,"quiz1":17.0,"quiz2":6.5,"sub":18.9,"group":"BSc Nursing"},"SN/NSU/25/0007":{"no":7,"name":"MINTAH, EKUA KUMIWAA","cat":5.0,"quiz1":15.5,"quiz2":11.0,"sub":22.9,"group":"BSc Nursing"},"SN/NSU/25/0008":{"no":8,"name":"KORKOR, OLIVIA","cat":5.0,"quiz1":16.0,"quiz2":11.5,"sub":23.6,"group":"BSc Nursing"},"SN/NSU/25/0009":{"no":9,"name":"KUSI-NKRUMAH, AKUA","cat":3.5,"quiz1":18.0,"quiz2":7.5,"sub":21.1,"group":"BSc Nursing"},"SN/NSU/25/0010":{"no":10,"name":"ACHEAMPONG, OBED OWOAHENE","cat":1.0,"quiz1":18.5,"quiz2":7.5,"sub":19.6,"group":"BSc Nursing"},"SN/NSU/25/0011":{"no":11,"name":"KYEREWAA, MARY ADWOA","cat":1.5,"quiz1":12.0,"quiz2":7.0,"sub":14.9,"group":"BSc Nursing"},"SN/NSU/25/0012":{"no":12,"name":"BOATENG, GRACE AMPOMAH","cat":5.0,"quiz1":16.0,"quiz2":14.0,"sub":25.5,"group":"BSc Nursing"},"SN/NSU/25/0013":{"no":13,"name":"OWUSU, OPHELIA ANSAH","cat":2.0,"quiz1":14.0,"quiz2":8.5,"sub":17.8,"group":"BSc Nursing"},"SN/NSU/25/0014":{"no":14,"name":"MENSAH, FRANCIS","cat":3.5,"quiz1":18.5,"quiz2":3.0,"sub":18.2,"group":"BSc Nursing"},"SN/NSU/25/0015":{"no":15,"name":"TEYE, RHODLINE DAIKIE","cat":2.5,"quiz1":13.0,"quiz2":8.0,"sub":17.1,"group":"BSc Nursing"},"SN/NSU/25/0016":{"no":16,"name":"ODURO, DANIEL","cat":2.0,"quiz1":12.0,"quiz2":13.5,"sub":20.0,"group":"BSc Nursing"},"SN/NSU/25/0017":{"no":17,"name":"SENYEGAH, KINGSELY","cat":1.5,"quiz1":12.0,"quiz2":7.0,"sub":14.9,"group":"BSc Nursing"},"SN/NSU/25/0018":{"no":18,"name":"TETTEH, CHRISTABEL KORLEKIE","cat":1.5,"quiz1":13.0,"quiz2":9.5,"sub":17.5,"group":"BSc Nursing"},"SN/NSU/25/0019":{"no":20,"name":"KAKRABA, YVONNE WULUG","cat":1.0,"quiz1":13.0,"quiz2":5.5,"sub":14.2,"group":"BSc Nursing"},"SN/NSU/25/0020":{"no":21,"name":"FRIMPONG, CHRISTIAN","cat":2.0,"quiz1":16.5,"quiz2":8.5,"sub":19.6,"group":"BSc Nursing"},"SN/NSU/25/0021":{"no":22,"name":"ODURO, LUCY","cat":2.5,"quiz1":16.0,"quiz2":3.0,"sub":15.6,"group":"BSc Nursing"},"SN/NSU/25/0022":{"no":23,"name":"BUADUWA, MAAME EFUA","cat":5.0,"quiz1":14.0,"quiz2":7.5,"sub":19.3,"group":"BSc Nursing"},"SN/NSU/25/0023":{"no":24,"name":"ARTHUR, JOYCE","cat":3.0,"quiz1":16.0,"quiz2":4.0,"sub":16.7,"group":"BSc Nursing"},"SN/NSU/25/0024":{"no":25,"name":"ESSARWA-DADZIE, HAZEL EKUA","cat":3.0,"quiz1":8.0,"quiz2":9.0,"sub":14.5,"group":"BSc Nursing"},"SN/NSU/25/0025":{"no":26,"name":"COBBINAH, JONATHAN","cat":2.5,"quiz1":18.5,"quiz2":9.0,"sub":21.8,"group":"BSc Nursing"},"SN/NSU/25/0026":{"no":27,"name":"JAGGREY, JOYCELYN NANA ADWOA","cat":1.0,"quiz1":16.0,"quiz2":6.0,"sub":16.7,"group":"BSc Nursing"},"SN/NSU/25/0027":{"no":28,"name":"YUSSIF, HAWA","cat":4.0,"quiz1":9.0,"quiz2":6.0,"sub":13.8,"group":"BSc Nursing"},"SN/NSU/25/0028":{"no":29,"name":"SAAH, MAJORINE BRAINS","cat":1.0,"quiz1":17.0,"quiz2":11.0,"sub":21.1,"group":"BSc Nursing"},"SN/NSU/25/0029":{"no":30,"name":"ABAKA-HAGAN, DORIS","cat":4.0,"quiz1":9.0,"quiz2":6.0,"sub":13.8,"group":"BSc Nursing"},"SN/NSU/25/0030":{"no":31,"name":"TEKPER, JOYCELYN AKUA","cat":5.0,"quiz1":17.0,"quiz2":15.5,"sub":27.3,"group":"BSc Nursing"},"SN/NSU/25/0031":{"no":32,"name":"AGYEI DUFFOUR, SAMUEL KWAW","cat":3.0,"quiz1":13.0,"quiz2":10.5,"sub":19.3,"group":"BSc Nursing"},"SN/NSU/25/0032":{"no":33,"name":"OPPONG, BRIGHT AMOAH","cat":5.0,"quiz1":17.5,"quiz2":13.5,"sub":26.2,"group":"BSc Nursing"},"SN/NSU/25/0033":{"no":34,"name":"OSMAN, KRISTODIA AMAMA","cat":4.0,"quiz1":14.0,"quiz2":5.0,"sub":16.7,"group":"BSc Nursing"},"SN/NSU/25/0034":{"no":35,"name":"APPIAH, MARY ARABA KWANSIMAA","cat":3.0,"quiz1":9.0,"quiz2":12.0,"sub":17.5,"group":"BSc Nursing"},"SN/NSU/25/0035":{"no":36,"name":"OPOKU, YVONNE SERWAA","cat":3.0,"quiz1":9.0,"quiz2":6.0,"sub":13.1,"group":"BSc Nursing"},"SN/NSU/25/0036":{"no":37,"name":"ODAMTTEN, BENEDICTA NAA ATSWEI","cat":1.5,"quiz1":17.5,"quiz2":10.0,"sub":21.1,"group":"BSc Nursing"},"SN/NSU/25/0037":{"no":38,"name":"DWOMOH, PHYLLIS ABENA","cat":4.0,"quiz1":18.0,"quiz2":9.0,"sub":22.5,"group":"BSc Nursing"},"SN/NSU/25/0038":{"no":39,"name":"OFORI, GLORIA NARKIH","cat":1.0,"quiz1":12.0,"quiz2":12.0,"sub":18.2,"group":"BSc Nursing"},"SN/NSU/25/0039":{"no":40,"name":"OKYERE, BOAKYEWAA NANA","cat":4.0,"quiz1":17.5,"quiz2":10.5,"sub":23.3,"group":"BSc Nursing"},"SN/NSU/25/0040":{"no":41,"name":"TAWIAH, RITA","cat":3.0,"quiz1":9.0,"quiz2":8.0,"sub":14.5,"group":"BSc Nursing"},"SN/NSU/25/0041":{"no":42,"name":"ARTHUR, FELICIA","cat":3.0,"quiz1":16.0,"quiz2":10.0,"sub":21.1,"group":"BSc Nursing"},"SN/NSU/25/0042":{"no":43,"name":"BOATENG, BRUNO NANA","cat":1.0,"quiz1":18.0,"quiz2":13.5,"sub":23.6,"group":"BSc Nursing"},"SN/NSU/25/0043":{"no":44,"name":"OWUSU, MARIAM","cat":5.0,"quiz1":15.0,"quiz2":8.5,"sub":20.7,"group":"BSc Nursing"},"SN/NSU/25/0044":{"no":45,"name":"ANDERSON, MIRACLE ESTHER","cat":0.0,"quiz1":17.0,"quiz2":8.5,"sub":18.5,"group":"BSc Nursing"},"SN/NSU/25/0045":{"no":46,"name":"YEBOAH, MICHEL AKUA","cat":2.5,"quiz1":14.0,"quiz2":8.0,"sub":17.8,"group":"BSc Nursing"},"SN/NSU/25/0046":{"no":47,"name":"OWUSU, RICHLOVE","cat":5.0,"quiz1":15.5,"quiz2":11.5,"sub":23.3,"group":"BSc Nursing"},"SN/NSU/25/0047":{"no":48,"name":"BOTWE, STEPHANIE","cat":4.0,"quiz1":12.0,"quiz2":7.5,"sub":17.1,"group":"BSc Nursing"},"SN/NSU/25/0048":{"no":49,"name":"AIDOO, GRAHAM","cat":0.0,"quiz1":19.5,"quiz2":14.0,"sub":24.4,"group":"BSc Nursing"},"SN/NSU/25/0049":{"no":50,"name":"ABUGRE, DERRICK YINENUUSI","cat":1.0,"quiz1":19.5,"quiz2":10.0,"sub":22.2,"group":"BSc Nursing"},"SN/NSU/25/0050":{"no":51,"name":"ASARE, LORD","cat":1.5,"quiz1":10.0,"quiz2":3.0,"sub":10.5,"group":"BSc Nursing"},"SN/NSU/25/0051":{"no":52,"name":"BAIDEN, ANSAH BRIGHT","cat":4.0,"quiz1":17.5,"quiz2":9.5,"sub":22.5,"group":"BSc Nursing"},"SN/NSU/25/0052":{"no":53,"name":"BOADI-SAKYI, ERICA","cat":1.0,"quiz1":16.0,"quiz2":6.5,"sub":17.1,"group":"BSc Nursing"},"SN/NSU/25/0053":{"no":54,"name":"ENNIN, POLEEN BAAH","cat":4.0,"quiz1":13.0,"quiz2":11.0,"sub":20.4,"group":"BSc Nursing"},"SN/NSU/25/0054":{"no":55,"name":"KWAKYE, GEORGINA BAMFO","cat":3.0,"quiz1":12.5,"quiz2":9.0,"sub":17.8,"group":"BSc Nursing"},"SN/NSU/25/0055":{"no":56,"name":"OWUSU-AFRIYIE, PATRICIA","cat":3.0,"quiz1":12.0,"quiz2":4.0,"sub":13.8,"group":"BSc Nursing"},"SN/NSU/25/0056":{"no":57,"name":"TSORTORME, SOPHIA ELORM","cat":4.0,"quiz1":14.0,"quiz2":13.0,"sub":22.5,"group":"BSc Nursing"},"SN/NSU/25/0057":{"no":58,"name":"KANCHONO, MABEL","cat":4.0,"quiz1":17.0,"quiz2":6.0,"sub":19.6,"group":"BSc Nursing"},"SN/NSU/25/0058":{"no":59,"name":"OWUSU, ANASTASIA","cat":5.0,"quiz1":17.0,"quiz2":15.5,"sub":27.3,"group":"BSc Nursing"},"SN/NSU/25/0059":{"no":60,"name":"ATTA, EMMANUEL","cat":1.0,"quiz1":15.0,"quiz2":11.0,"sub":19.6,"group":"BSc Nursing"},"SN/NSU/25/0060":{"no":61,"name":"YEBOAH, DANIELLA ADU","cat":5.0,"quiz1":14.5,"quiz2":11.5,"sub":22.5,"group":"BSc Nursing"},"SN/NSU/25/0061":{"no":62,"name":"BOAKYE, GIDEON ACHEAMPONG","cat":2.5,"quiz1":19.5,"quiz2":13.0,"sub":25.5,"group":"BSc Nursing"},"SN/NSU/25/0062":{"no":63,"name":"","cat":0.0,"quiz1":0.0,"quiz2":0.0,"sub":0.0,"group":"BSc Nursing"},"SN/NSU/25/0063":{"no":64,"name":"COMMODORE, DEBORAH","cat":2.0,"quiz1":12.0,"quiz2":13.5,"sub":20.0,"group":"BSc Nursing"},"SN/NSU/25/0064":{"no":65,"name":"ASAMOAH, JOANNA KOOMSON","cat":5.0,"quiz1":19.0,"quiz2":11.5,"sub":25.8,"group":"BSc Nursing"},"SN/NSU/25/0065":{"no":66,"name":"AMISSAH, MATTHEW","cat":1.0,"quiz1":19.0,"quiz2":10.0,"sub":21.8,"group":"BSc Nursing"},"SN/NSU/25/0066":{"no":67,"name":"BOATENG, AYESHA","cat":1.0,"quiz1":12.0,"quiz2":12.5,"sub":18.5,"group":"BSc Nursing"},"SN/NSU/25/0067":{"no":68,"name":"MOTTEY, BERNARD YAYRA","cat":2.0,"quiz1":18.0,"quiz2":13.0,"sub":24.0,"group":"BSc Nursing"},"SN/NSU/25/0068":{"no":69,"name":"NKETSIAH, BELICIA","cat":4.0,"quiz1":10.0,"quiz2":13.0,"sub":19.6,"group":"BSc Nursing"},"SN/NSU/25/0069":{"no":70,"name":"OWUSU, PRISCILLA","cat":1.5,"quiz1":16.5,"quiz2":6.0,"sub":17.5,"group":"BSc Nursing"},"SN/NSU/25/0070":{"no":71,"name":"SIBOR, JOANA","cat":4.0,"quiz1":5.5,"quiz2":8.5,"sub":13.1,"group":"BSc Nursing"},"SN/NSU/25/0071":{"no":72,"name":"AMISSAH, NANCY","cat":1.5,"quiz1":10.0,"quiz2":10.0,"sub":15.6,"group":"BSc Nursing"},"SN/NSU/25/0072":{"no":73,"name":"KOOMSON, PHILIPPA","cat":3.0,"quiz1":11.0,"quiz2":9.0,"sub":16.7,"group":"BSc Nursing"},"SN/NSU/25/0073":{"no":75,"name":"MENSAH, PRISCILLA ABA","cat":1.5,"quiz1":11.0,"quiz2":13.0,"sub":18.5,"group":"BSc Nursing"},"SN/NSU/25/0074":{"no":76,"name":"OWUSU, JESSICA AMPONSAH","cat":3.5,"quiz1":18.0,"quiz2":8.5,"sub":21.8,"group":"BSc Nursing"},"SN/NSU/25/0075":{"no":77,"name":"AGYAPONG, ALEX AYEH","cat":1.5,"quiz1":18.5,"quiz2":12.5,"sub":23.6,"group":"BSc Nursing"},"SN/NSU/25/0076":{"no":78,"name":"ARHIN, PATRICK","cat":0.0,"quiz1":19.5,"quiz2":13.5,"sub":24.0,"group":"BSc Nursing"},"SN/NSU/25/0077":{"no":80,"name":"GYAN, CHRISTABEL","cat":3.0,"quiz1":18.0,"quiz2":5.5,"sub":19.3,"group":"BSc Nursing"},"SN/NSU/25/0078":{"no":81,"name":"SARFO, LAWRENDA KONAMAH","cat":3.0,"quiz1":9.0,"quiz2":8.5,"sub":14.9,"group":"BSc Nursing"},"SN/NSU/25/0079":{"no":82,"name":"AWADEY, EDEM ABLA","cat":2.5,"quiz1":9.0,"quiz2":7.0,"sub":13.5,"group":"BSc Nursing"},"SN/NSU/25/0080":{"no":83,"name":"TEPRE, CORNELIA","cat":3.0,"quiz1":13.0,"quiz2":7.5,"sub":17.1,"group":"BSc Nursing"},"SN/NSU/25/0081":{"no":84,"name":"EFFAH, GODFRED","cat":1.5,"quiz1":16.0,"quiz2":6.0,"sub":17.1,"group":"BSc Nursing"},"SN/NSU/25/0082":{"no":85,"name":"BOGOBLEY, FILDAUS","cat":5.0,"quiz1":0.0,"quiz2":7.5,"sub":9.1,"group":"BSc Nursing"},"SN/NSU/25/0083":{"no":86,"name":"MARK, TWENEBOA KODUA","cat":2.5,"quiz1":16.5,"quiz2":7.0,"sub":18.9,"group":"BSc Nursing"},"SN/NSU/25/0084":{"no":87,"name":"ANOFI, BLESSING ADUTWUMWAA","cat":2.0,"quiz1":16.0,"quiz2":11.0,"sub":21.1,"group":"BSc Nursing"},"SN/NSU/25/0085":{"no":89,"name":"NYAXO, LINDA","cat":2.0,"quiz1":20.0,"quiz2":5.0,"sub":19.6,"group":"BSc Nursing"},"SN/NSU/25/0086":{"no":90,"name":"OPOKU, FRANK GYIMAH","cat":4.0,"quiz1":19.0,"quiz2":6.0,"sub":21.1,"group":"BSc Nursing"},"SN/NSU/25/0087":{"no":91,"name":"SEKYIWA, KEZIA NANA YAA","cat":1.0,"quiz1":5.0,"quiz2":8.5,"sub":10.5,"group":"BSc Nursing"},"SN/NSU/25/0088":{"no":92,"name":"LAMPTEY, JESSICA","cat":3.0,"quiz1":16.0,"quiz2":10.5,"sub":21.5,"group":"BSc Nursing"},"SN/NSU/25/0089":{"no":93,"name":"GYAMFI, MABEL","cat":1.5,"quiz1":9.0,"quiz2":7.5,"sub":13.1,"group":"BSc Nursing"},"SN/NSU/25/0090":{"no":94,"name":"KUMI, PERPETUAL YEBOAH","cat":2.0,"quiz1":15.5,"quiz2":8.0,"sub":18.5,"group":"BSc Nursing"},"SN/NSU/25/0091":{"no":95,"name":"ASANO, NAOMI","cat":4.0,"quiz1":11.0,"quiz2":6.0,"sub":15.3,"group":"BSc Nursing"},"SN/NSU/25/0092":{"no":96,"name":"BERKO, EUNICE","cat":3.0,"quiz1":15.5,"quiz2":8.0,"sub":19.3,"group":"BSc Nursing"},"SN/NSU/25/0093":{"no":97,"name":"NARTEY, PRISCILLA SIAW SOYO","cat":3.0,"quiz1":12.0,"quiz2":11.5,"sub":19.3,"group":"BSc Nursing"},"SN/NSU/25/0094":{"no":98,"name":"ABBAN, ALEXANDER","cat":1.0,"quiz1":16.0,"quiz2":3.0,"sub":14.5,"group":"BSc Nursing"},"SN/NSU/25/0095":{"no":99,"name":"EDOUKOUN, EVORA","cat":2.5,"quiz1":17.0,"quiz2":11.0,"sub":22.2,"group":"BSc Nursing"},"SN/NSU/25/0096":{"no":100,"name":"ASANTE, RAYMOND KOFI JUNIOR","cat":4.0,"quiz1":15.0,"quiz2":15.5,"sub":25.1,"group":"BSc Nursing"},"SN/NSU/25/0097":{"no":101,"name":"MBROH, REBECCA YAMOABA","cat":2.0,"quiz1":17.0,"quiz2":6.0,"sub":18.2,"group":"BSc Nursing"},"SN/NSU/25/0098":{"no":102,"name":"SARPONG, BENRICE NYANTAKYIWAA","cat":4.0,"quiz1":15.5,"quiz2":5.5,"sub":18.2,"group":"BSc Nursing"},"SN/NSU/25/0099":{"no":103,"name":"OWUSUAA, CHARLOTTE","cat":5.0,"quiz1":17.0,"quiz2":7.5,"sub":21.5,"group":"BSc Nursing"},"SN/NSU/25/0100":{"no":104,"name":"OWIREDU, ABIGAIL AGYEIWAA","cat":5.0,"quiz1":15.0,"quiz2":12.0,"sub":23.3,"group":"BSc Nursing"},"SN/NSU/25/0101":{"no":105,"name":"AMANKWATIA, ABENA POKUAA GYAWU","cat":1.0,"quiz1":13.5,"quiz2":8.5,"sub":16.7,"group":"BSc Nursing"},"SN/NSU/25/0102":{"no":106,"name":"ADU, FRANCIS ADONTENG","cat":2.5,"quiz1":17.5,"quiz2":13.0,"sub":24.0,"group":"BSc Nursing"},"SN/NSU/25/0103":{"no":107,"name":"LEMOHA, VICTORIA ADA","cat":5.0,"quiz1":17.0,"quiz2":10.5,"sub":23.6,"group":"BSc Nursing"},"SN/NSU/25/0104":{"no":108,"name":"ANNAN, JUSTINA AMENU","cat":1.5,"quiz1":19.0,"quiz2":9.0,"sub":21.5,"group":"BSc Nursing"},"SN/NSU/25/0105":{"no":109,"name":"ADWETOAH, ANNABELLA","cat":1.0,"quiz1":7.0,"quiz2":11.0,"sub":13.8,"group":"BSc Nursing"},"SN/NSU/25/0106":{"no":110,"name":"ACKAH, NANA ABA","cat":5.0,"quiz1":13.0,"quiz2":7.5,"sub":18.5,"group":"BSc Nursing"},"SN/NSU/25/0107":{"no":111,"name":"YANKAH, EWURABENA","cat":3.5,"quiz1":19.5,"quiz2":7.5,"sub":22.2,"group":"BSc Nursing"},"SN/NSU/25/0108":{"no":112,"name":"ANDOH, HARRIET MENSAH","cat":4.0,"quiz1":17.0,"quiz2":10.5,"sub":22.9,"group":"BSc Nursing"},"SN/NSU/25/0109":{"no":113,"name":"BASSAW, PRISCILLA ADJOA","cat":2.5,"quiz1":12.0,"quiz2":4.0,"sub":13.5,"group":"BSc Nursing"},"SN/NSU/25/0110":{"no":114,"name":"ATTUQUAYEFIO, KIMBERLY NAA KORDEY","cat":0.0,"quiz1":19.5,"quiz2":12.0,"sub":22.9,"group":"BSc Nursing"},"SN/NSU/25/0111":{"no":115,"name":"ADUSEI, BENEDICTA","cat":5.0,"quiz1":16.5,"quiz2":13.0,"sub":25.1,"group":"BSc Nursing"},"SN/NSU/25/0112":{"no":116,"name":"AKWAA, RHODA AKYAA","cat":4.0,"quiz1":17.0,"quiz2":11.0,"sub":23.3,"group":"BSc Nursing"},"SN/NSU/25/0113":{"no":117,"name":"ISSAH, HAWA","cat":4.0,"quiz1":17.0,"quiz2":8.0,"sub":21.1,"group":"BSc Nursing"},"SN/NSU/25/0114":{"no":118,"name":"BINEY, MARGARITA","cat":2.5,"quiz1":14.0,"quiz2":3.0,"sub":14.2,"group":"BSc Nursing"},"SN/NSU/25/0115":{"no":119,"name":"OPOKU, BISMARK KWADWO BIMPONG","cat":2.0,"quiz1":9.0,"quiz2":10.0,"sub":15.3,"group":"BSc Nursing"},"SN/NSU/25/0116":{"no":120,"name":"OTOO, MAAME ESI TSIMA","cat":2.0,"quiz1":13.0,"quiz2":8.0,"sub":16.7,"group":"BSc Nursing"},"SN/NSU/25/0117":{"no":121,"name":"ABUBAKAR SIDDIQUE, LUKMAN","cat":3.0,"quiz1":15.0,"quiz2":8.5,"sub":19.3,"group":"BSc Nursing"},"SN/NSU/25/0118":{"no":122,"name":"DONKOR, EMLYN KWAME OKAI","cat":4.0,"quiz1":15.0,"quiz2":7.0,"sub":18.9,"group":"BSc Nursing"},"SN/NSU/25/0119":{"no":123,"name":"ANING, VERA NHYIRA","cat":5.0,"quiz1":14.0,"quiz2":8.5,"sub":20.0,"group":"BSc Nursing"},"SN/NSU/25/0120":{"no":124,"name":"AYISI, SOLOMON","cat":4.0,"quiz1":15.0,"quiz2":11.0,"sub":21.8,"group":"BSc Nursing"},"SN/NSU/25/0121":{"no":125,"name":"ATSU-OFORI, VICTORIA ETORNAM","cat":5.0,"quiz1":15.0,"quiz2":9.0,"sub":21.1,"group":"BSc Nursing"},"SN/NSU/25/0122":{"no":126,"name":"YEBOAH, MAAME NYARKO NHYIRA","cat":3.0,"quiz1":13.0,"quiz2":4.0,"sub":14.5,"group":"BSc Nursing"},"SN/NSU/25/0123":{"no":127,"name":"TENNYSON, KRISTODIA SOSU","cat":2.5,"quiz1":18.0,"quiz2":14.5,"sub":25.5,"group":"BSc Nursing"},"SN/NSU/25/0124":{"no":129,"name":"NKRUMAH, BLESSING","cat":4.0,"quiz1":16.0,"quiz2":8.5,"sub":20.7,"group":"BSc Nursing"},"SN/NSU/25/0125":{"no":130,"name":"ABOAGYE, YAA AWUAH","cat":2.0,"quiz1":14.0,"quiz2":12.0,"sub":20.4,"group":"BSc Nursing"},"SN/NSU/25/0126":{"no":131,"name":"ANYIDOHO, MOSES DZILANYO","cat":3.0,"quiz1":15.0,"quiz2":13.5,"sub":22.9,"group":"BSc Nursing"},"SN/NSU/25/0127":{"no":132,"name":"GOSU, JOCELYN AKORFA","cat":5.0,"quiz1":8.0,"quiz2":4.0,"sub":12.4,"group":"BSc Nursing"},"SN/NSU/25/0128":{"no":133,"name":"BLAY, CHARMAINE AFIBA","cat":4.0,"quiz1":14.0,"quiz2":4.0,"sub":16.0,"group":"BSc Nursing"},"SN/NSU/25/0129":{"no":134,"name":"ARYEE, REBECCA CLAIRE NAA AYALEY","cat":2.0,"quiz1":10.0,"quiz2":5.0,"sub":12.4,"group":"BSc Nursing"},"SN/NSU/25/0130":{"no":135,"name":"MAJOBONI, GODWIN NGEYAAN","cat":4.0,"quiz1":16.5,"quiz2":5.5,"sub":18.9,"group":"BSc Nursing"},"SN/NSU/25/0131":{"no":136,"name":"ONNY, SHINE CONSOLATA","cat":3.0,"quiz1":15.0,"quiz2":11.5,"sub":21.5,"group":"BSc Nursing"},"SN/NSU/25/0132":{"no":137,"name":"AFORNOAFE, CORNELIUS","cat":3.0,"quiz1":16.5,"quiz2":7.0,"sub":19.3,"group":"BSc Nursing"},"SN/NSU/25/0133":{"no":138,"name":"AYESU ASIAMAH, AKUA ASANTEWAA","cat":5.0,"quiz1":17.0,"quiz2":16.0,"sub":27.6,"group":"BSc Nursing"},"SN/NSU/25/0134":{"no":139,"name":"WILLIAMS, ELLA NANA YAA","cat":1.5,"quiz1":19.5,"quiz2":14.0,"sub":25.5,"group":"BSc Nursing"},"SN/NSU/25/0135":{"no":140,"name":"WUMANYO, VANESSA ETORNAM","cat":0.0,"quiz1":16.5,"quiz2":6.0,"sub":16.4,"group":"BSc Nursing"},"SN/NSU/25/0136":{"no":141,"name":"OWUSU-ANSAH, ERICA ACHEAMPOMAA","cat":4.0,"quiz1":17.0,"quiz2":10.0,"sub":22.5,"group":"BSc Nursing"},"SN/NSU/25/0137":{"no":142,"name":"ABDUL AMIN, ADIZATU","cat":1.0,"quiz1":16.0,"quiz2":8.5,"sub":18.5,"group":"BSc Nursing"},"SN/NSU/25/0138":{"no":143,"name":"IMPRAIM, CHRISTABEL NKRUMAH","cat":4.0,"quiz1":14.0,"quiz2":8.0,"sub":18.9,"group":"BSc Nursing"},"SN/NSU/25/0139":{"no":144,"name":"BINEY, MELODY ATTA","cat":3.0,"quiz1":17.0,"quiz2":6.5,"sub":19.3,"group":"BSc Nursing"},"SN/NSU/25/0140":{"no":145,"name":"BINEY, MANDY ATTA","cat":4.0,"quiz1":16.5,"quiz2":6.5,"sub":19.6,"group":"BSc Nursing"},"SN/NSU/25/0141":{"no":146,"name":"KASSIM, FATIMAH","cat":3.0,"quiz1":12.5,"quiz2":3.0,"sub":13.5,"group":"BSc Nursing"},"AH/NRT/25/0001":{"no":1,"name":"MOHAMMED, MUKARAMA AYAAGO","cat":0.0,"quiz1":11.0,"quiz2":8.5,"sub":14.2,"group":"BSc Nutrition"},"AH/NRT/25/0002":{"no":2,"name":"ADDO, MARGARET","cat":2.5,"quiz1":18.5,"quiz2":3.0,"sub":17.5,"group":"BSc Nutrition"},"AH/NRT/25/0003":{"no":3,"name":"BIRAGO, DOROTHY","cat":2.5,"quiz1":19.0,"quiz2":3.0,"sub":17.8,"group":"BSc Nutrition"},"AH/NRT/25/0004":{"no":4,"name":"FIANKO AFOA, MARIAM NAANA AKYERE","cat":3.0,"quiz1":17.5,"quiz2":1.0,"sub":15.6,"group":"BSc Nutrition"},"AH/NRT/25/0005":{"no":5,"name":"YEBOAH, EUNICE OWUSUA","cat":5.0,"quiz1":18.0,"quiz2":6.0,"sub":21.1,"group":"BSc Nutrition"},"AH/NRT/25/0006":{"no":6,"name":"SANI, NAAYIMA","cat":0.0,"quiz1":13.0,"quiz2":8.0,"sub":15.3,"group":"BSc Nutrition"},"AH/NRT/25/0007":{"no":7,"name":"OSEI, ROSINA ABENA OWUSUA","cat":0.0,"quiz1":18.0,"quiz2":4.0,"sub":16.0,"group":"BSc Nutrition"},"AH/NRT/25/0008":{"no":8,"name":"OBOH, SARAH","cat":4.0,"quiz1":16.0,"quiz2":4.5,"sub":17.8,"group":"BSc Nutrition"},"AH/NRT/25/0009":{"no":9,"name":"BEHE, PRINCESS","cat":5.0,"quiz1":19.0,"quiz2":5.0,"sub":21.1,"group":"BSc Nutrition"},"AH/NRT/25/0010":{"no":10,"name":"HARUNA, SAMIRA","cat":1.0,"quiz1":16.0,"quiz2":8.0,"sub":18.2,"group":"BSc Nutrition"},"AH/NRT/25/0011":{"no":11,"name":"YUSSIF, RUMAISATU","cat":2.5,"quiz1":19.5,"quiz2":3.5,"sub":18.5,"group":"BSc Nutrition"},"AH/NRT/25/0012":{"no":12,"name":"YAWSON, DORCAS","cat":5.0,"quiz1":17.5,"quiz2":3.0,"sub":18.5,"group":"BSc Nutrition"},"AH/NRT/25/0013":{"no":13,"name":"GYABEA, EMMANUELLA","cat":1.0,"quiz1":17.5,"quiz2":5.0,"sub":17.1,"group":"BSc Nutrition"},"AH/NRT/25/0014":{"no":14,"name":"ATINGUME, ANGELA AWONPOAK","cat":2.0,"quiz1":12.0,"quiz2":7.0,"sub":15.3,"group":"BSc Nutrition"},"AH/NRT/25/0015":{"no":15,"name":"AHATSE, BELINDA","cat":4.0,"quiz1":15.0,"quiz2":6.5,"sub":18.5,"group":"BSc Nutrition"},"AH/NRT/25/0016":{"no":16,"name":"HAGAN, BENEDICTA OBOUR","cat":5.0,"quiz1":17.5,"quiz2":7.0,"sub":21.5,"group":"BSc Nutrition"},"AH/NRT/25/0017":{"no":17,"name":"AFADZI, JUSTICIA HAPPY","cat":5.0,"quiz1":18.0,"quiz2":12.0,"sub":25.5,"group":"BSc Nutrition"},"AH/NRT/25/0018":{"no":18,"name":"","cat":0.0,"quiz1":0.0,"quiz2":0.0,"sub":0.0,"group":"BSc Nutrition"},"AH/NRT/25/0019":{"no":19,"name":"YEBOAH, ANABEL ODOFULEY","cat":5.0,"quiz1":16.5,"quiz2":4.5,"sub":18.9,"group":"BSc Nutrition"},"AH/NRT/25/0020":{"no":20,"name":"KWOFIE, AGNES","cat":1.0,"quiz1":16.0,"quiz2":6.5,"sub":17.1,"group":"BSc Nutrition"},"AH/NRT/25/0021":{"no":21,"name":"PANTSIL, ISABELLA","cat":1.0,"quiz1":18.5,"quiz2":5.0,"sub":17.8,"group":"BSc Nutrition"},"AH/NRT/25/0022":{"no":22,"name":"NTOSO, PERPETUAL BAGYINA","cat":0.0,"quiz1":11.0,"quiz2":5.5,"sub":12.0,"group":"BSc Nutrition"},"AH/NRT/25/0023":{"no":23,"name":"AGBENORHEVI, PEACE AFI","cat":5.0,"quiz1":13.0,"quiz2":3.5,"sub":15.6,"group":"BSc Nutrition"},"AH/NRT/25/0024":{"no":24,"name":"NASIRU, GANIW","cat":4.5,"quiz1":16.0,"quiz2":9.5,"sub":21.8,"group":"BSc Nutrition"},"AH/NRT/25/0025":{"no":25,"name":"LARTEY, PASCALINE AKUSIKA SIKA","cat":2.0,"quiz1":11.5,"quiz2":6.0,"sub":14.2,"group":"BSc Nutrition"},"AH/NRT/25/0026":{"no":26,"name":"TAWIAH, EDITH ESI","cat":5.0,"quiz1":17.5,"quiz2":7.0,"sub":21.5,"group":"BSc Nutrition"},"AH/NRT/25/0027":{"no":27,"name":"BEDU, ISABELLA KORKOR","cat":5.0,"quiz1":16.5,"quiz2":8.0,"sub":21.5,"group":"BSc Nutrition"},"AH/NRT/25/0028":{"no":28,"name":"EDUAFO, EDITH","cat":3.0,"quiz1":18.0,"quiz2":5.5,"sub":19.3,"group":"BSc Nutrition"},"AH/NRT/25/0029":{"no":29,"name":"ACHEAMPONG, JENNIFER","cat":2.5,"quiz1":15.5,"quiz2":7.5,"sub":18.5,"group":"BSc Nutrition"},"AH/NRT/25/0030":{"no":30,"name":"ADDO, LYDIA TETTEKIE","cat":2.5,"quiz1":16.5,"quiz2":11.5,"sub":22.2,"group":"BSc Nutrition"},"AH/NRT/25/0031":{"no":31,"name":"OWUSU, NANA AMA KORANTEMA","cat":3.0,"quiz1":18.5,"quiz2":5.5,"sub":19.6,"group":"BSc Nutrition"},"AH/NRT/25/0032":{"no":32,"name":"CRENTSIL, OLIVIA AMA","cat":4.0,"quiz1":13.0,"quiz2":4.0,"sub":15.3,"group":"BSc Nutrition"},"AH/NRT/25/0033":{"no":33,"name":"LARBI, EDITH","cat":2.5,"quiz1":16.0,"quiz2":4.0,"sub":16.4,"group":"BSc Nutrition"},"AH/NRT/25/0034":{"no":34,"name":"KYERE, SETHINA NHYIRA","cat":5.0,"quiz1":0.0,"quiz2":6.0,"sub":8.0,"group":"BSc Nutrition"},"AH/NRT/25/0035":{"no":35,"name":"ACHEAMPONG, RONI MENSAH","cat":0.0,"quiz1":13.0,"quiz2":5.5,"sub":13.5,"group":"BSc Nutrition"},"AH/NRT/25/0036":{"no":36,"name":"AMOAKO, ELIZABETH","cat":5.0,"quiz1":19.0,"quiz2":3.5,"sub":20.0,"group":"BSc Nutrition"},"AH/NRT/25/0037":{"no":37,"name":"AYIGEB, SANDRA ALIMISIWENA","cat":1.5,"quiz1":10.0,"quiz2":3.5,"sub":10.9,"group":"BSc Nutrition"},"AH/NRT/25/0038":{"no":38,"name":"MOFFATT, VICENTIA NAA ADOLEY","cat":0.0,"quiz1":0.0,"quiz2":4.0,"sub":2.9,"group":"BSc Nutrition"},"AH/NRT/25/0039":{"no":39,"name":"AMPONSAH, SARAH","cat":4.0,"quiz1":19.0,"quiz2":7.0,"sub":21.8,"group":"BSc Nutrition"},"AH/NRT/25/0040":{"no":40,"name":"KADRI, RAMZIYA","cat":1.5,"quiz1":19.5,"quiz2":4.5,"sub":18.5,"group":"BSc Nutrition"},"AH/NRT/25/0041":{"no":41,"name":"CONDUAH, EMMANUELLA","cat":2.5,"quiz1":14.0,"quiz2":3.0,"sub":14.2,"group":"BSc Nutrition"},"AH/NRT/25/0042":{"no":42,"name":"GAFA, JUDITH ELLOM","cat":4.0,"quiz1":17.0,"quiz2":2.5,"sub":17.1,"group":"BSc Nutrition"}};

/* ─────────────────────────────────────────────────────────────
   AUTH — bulletproof password generation
   Rule: first 2 alpha chars (uppercase) + last 4 numeric digits
   e.g.  SN/NSU/25/0001  →  SN0001
         AH/NRT/25/0015  →  AH0015
───────────────────────────────────────────────────────────── */
function makePassword(idx) {
  const clean   = idx.toUpperCase();
  const letters = clean.replace(/[^A-Z]/g, '').substring(0, 2);
  const digits  = clean.replace(/[^0-9]/g, '');
  const last4   = digits.slice(-4).padStart(4, '0');
  return letters + last4;
}

/* Normalise whatever the user types */
function normaliseIndex(raw) {
  return raw.trim().toUpperCase().replace(/\s+/g, '');
}

/* ─────────────────────────────────────────────────────────────
   STATE
───────────────────────────────────────────────────────────── */
let current       = null;
let complaintCount = 0;

/* ─────────────────────────────────────────────────────────────
   LOGIN
───────────────────────────────────────────────────────────── */
function doLogin() {
  const rawIdx = document.getElementById('inp-index').value;
  const rawPw  = document.getElementById('inp-pw').value.trim();
  const idx    = normaliseIndex(rawIdx);
  const alert  = document.getElementById('login-alert');

  // Clear previous error
  alert.classList.remove('show');
  document.getElementById('inp-index').style.borderColor = '';
  document.getElementById('inp-pw').style.borderColor    = '';

  if (!idx) {
    showLoginError('Please enter your index number.');
    return;
  }

  const data = STUDENTS[idx];

  if (!data) {
    showLoginError('Index number not found. Please check and try again. (Example: SN/NSU/25/0042)');
    return;
  }

  const expected = makePassword(idx);

  if (rawPw !== expected) {
    showLoginError('Incorrect password. Password = first 2 letters + last 4 digits of your index. (e.g. SN/NSU/25/0001 → SN0001)');
    document.getElementById('inp-pw').style.borderColor = '#C0392B';
    return;
  }

  // ✅ Authenticated
  current = { idx, ...data };
  renderDashboard();
}

function showLoginError(msg) {
  const al = document.getElementById('login-alert');
  document.getElementById('login-alert-msg').textContent = msg;
  al.classList.add('show');
  document.getElementById('inp-index').style.borderColor = '#C0392B';
}

function togglePw() {
  const el = document.getElementById('inp-pw');
  el.type = el.type === 'password' ? 'text' : 'password';
}

/* ─────────────────────────────────────────────────────────────
   DASHBOARD RENDER
───────────────────────────────────────────────────────────── */
function renderDashboard() {
  const d   = current;
  const raw = +(d.cat + d.quiz1 + d.quiz2).toFixed(1);
  const sub = d.sub;
  const pctRaw = Math.round((raw / 55)  * 100);
  const pctSub = Math.round((sub / 40)  * 100);

  // Banner
  document.getElementById('d-name').textContent  = d.name || '(Name pending)';
  document.getElementById('d-index').textContent = d.idx;
  document.getElementById('d-group').textContent = d.group;

  // Stat pills
  document.getElementById('st-sub').textContent = sub;
  document.getElementById('st-raw').textContent = raw;
  document.getElementById('st-grade').textContent = 'IC';
  document.getElementById('st-complaints').textContent = complaintCount;

  // Component cards
  set('sc-cat', d.cat);
  set('sc-q1',  d.quiz1);
  set('sc-q2',  d.quiz2);
  document.getElementById('note-sub').textContent = sub + ' / 40';

  // Summary bars (animated via setTimeout)
  setTimeout(() => {
    setBar('bar-cat',  (d.cat   / 5)  * 100);
    setBar('bar-q1',   (d.quiz1 / 20) * 100);
    setBar('bar-q2',   (d.quiz2 / 30) * 100);
    setBar('fill-raw', pctRaw);
    setBar('fill-sub', pctSub);
  }, 200);

  // Summary values
  set('val-raw', raw + ' / 55');
  set('val-sub', sub + ' / 40');

  // Grade ring — IC until exam
  const ring = document.getElementById('grade-ring');
  ring.textContent  = 'IC';
  ring.className    = 'grade-ring grade-IC';

  // Pre-fill complaint form
  document.getElementById('c-index').value = d.idx;
  document.getElementById('c-prog').value  = d.group;

  // Switch screens
  document.getElementById('screen-login').classList.remove('active');
  document.getElementById('screen-dash').classList.add('active');
  document.getElementById('btn-signout').style.display = 'block';

  // Default to scores tab
  switchTab('scores');
}

function set(id, val) {
  const el = document.getElementById(id);
  if (el) el.textContent = val;
}

function setBar(id, pct) {
  const el = document.getElementById(id);
  if (el) el.style.width = Math.min(100, Math.max(0, pct)) + '%';
}

/* ─────────────────────────────────────────────────────────────
   SIGN OUT
───────────────────────────────────────────────────────────── */
function signOut() {
  current = null;
  document.getElementById('screen-dash').classList.remove('active');
  document.getElementById('screen-login').classList.add('active');
  document.getElementById('btn-signout').style.display = 'none';
  document.getElementById('inp-index').value = '';
  document.getElementById('inp-pw').value    = '';
  document.getElementById('inp-index').style.borderColor = '';
  document.getElementById('inp-pw').style.borderColor    = '';
  document.getElementById('login-alert').classList.remove('show');
  document.getElementById('success-alert').style.display = 'none';
  // Reset bars
  ['bar-cat','bar-q1','bar-q2','fill-raw','fill-sub'].forEach(id => setBar(id, 0));
}

/* ─────────────────────────────────────────────────────────────
   TABS
───────────────────────────────────────────────────────────── */
function switchTab(tab) {
  document.querySelectorAll('.tab-btn').forEach((b, i) => {
    b.classList.toggle('active',
      (tab === 'scores'    && i === 0) ||
      (tab === 'complaint' && i === 1)
    );
  });
  document.getElementById('panel-scores').classList.toggle('active',    tab === 'scores');
  document.getElementById('panel-complaint').classList.toggle('active', tab === 'complaint');
}

/* ─────────────────────────────────────────────────────────────
   COMPLAINT
───────────────────────────────────────────────────────────── */
function handleFile(input) {
  const el = document.getElementById('fname');
  if (input.files && input.files[0]) {
    el.textContent = '✓ ' + input.files[0].name;
    el.style.display = 'block';
  }
}

function submitComplaint() {
  const name      = document.getElementById('c-name').value.trim();
  const component = document.getElementById('c-component').value;
  const detail    = document.getElementById('c-detail').value.trim();

  if (!name) {
    alert('Please enter your full name before submitting.');
    document.getElementById('c-name').focus();
    return;
  }
  if (!component) {
    alert('Please select the component you are disputing.');
    document.getElementById('c-component').focus();
    return;
  }
  if (!detail) {
    alert('Please provide details of your complaint.');
    document.getElementById('c-detail').focus();
    return;
  }

  // Record
  complaintCount++;
  document.getElementById('st-complaints').textContent = complaintCount;

  // Show success
  const sa = document.getElementById('success-alert');
  sa.style.display = 'block';
  sa.scrollIntoView({ behavior: 'smooth', block: 'nearest' });

  // Reset form fields
  ['c-name', 'c-email', 'c-shown', 'c-expected', 'c-detail'].forEach(id => {
    document.getElementById(id).value = '';
  });
  document.getElementById('c-component').value = '';
  document.getElementById('c-file').value       = '';
  document.getElementById('fname').style.display = 'none';
}
</script>

</body>
</html>
