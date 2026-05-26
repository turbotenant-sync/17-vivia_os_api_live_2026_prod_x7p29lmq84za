cat > /mnt/user-data/outputs/index.html << 'HTMLEOF'
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>VIVIA — Property Management Platform</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,600;0,9..144,700;1,9..144,400;1,9..144,600&family=DM+Mono:wght@300;400;500&family=Geist:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
:root{--navy:#033A6D;--navy2:#022850;--ink:#0D1117;--paper:#F5F3EE;--cream:#FAF8F3;--gold:#B8972A;--gold2:#E2C96A;--slate:#49637E;--mist:#E4EBF3;--rule:rgba(3,58,109,0.1);--green:#16A34A;}
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{font-family:'Geist',sans-serif;background:var(--paper);color:var(--ink);overflow-x:hidden;}
nav{position:fixed;top:0;left:0;right:0;z-index:200;height:64px;display:flex;align-items:center;justify-content:space-between;padding:0 40px;background:rgba(245,243,238,0.94);backdrop-filter:blur(14px);border-bottom:1px solid var(--rule);}
.brand{font-family:'Fraunces',serif;font-size:24px;font-weight:700;color:var(--navy);letter-spacing:.5px;cursor:pointer;}
.brand span{color:var(--gold);}
.nav-tabs{display:flex;gap:4px;}
.nav-tab{padding:7px 16px;border-radius:6px;border:none;cursor:pointer;font-family:'Geist',sans-serif;font-size:13px;font-weight:500;background:none;color:var(--slate);transition:all .2s;}
.nav-tab:hover{color:var(--navy);background:var(--mist);}
.nav-tab.active{background:var(--navy);color:white;}
.nav-right{display:flex;align-items:center;gap:10px;}
.btn-sm{padding:8px 18px;border-radius:6px;font-size:13px;font-weight:600;cursor:pointer;border:none;transition:all .2s;font-family:'Geist',sans-serif;}
.btn-gold{background:var(--gold);color:white;}.btn-gold:hover{background:#9a7d24;}
.btn-navy{background:var(--navy);color:white;}.btn-navy:hover{background:var(--navy2);}
.btn-outline{background:none;border:1.5px solid var(--rule);color:var(--slate);}.btn-outline:hover{border-color:var(--navy);color:var(--navy);}
.hamburger{display:none;flex-direction:column;gap:5px;background:none;border:none;cursor:pointer;padding:4px;}
.hamburger span{display:block;width:20px;height:2px;background:var(--navy);border-radius:2px;}
.page{display:none;padding-top:64px;min-height:100vh;}
.page.active{display:block;}
/* HERO */
.hero{min-height:calc(100vh - 64px);display:grid;grid-template-columns:1fr 1fr;position:relative;overflow:hidden;}
.hero-bg{position:absolute;inset:0;background:linear-gradient(135deg,transparent 50%,var(--navy) 50%);pointer-events:none;}
.hero-left{padding:80px 60px 80px 80px;display:flex;flex-direction:column;justify-content:center;position:relative;z-index:1;}
.eyebrow{font-family:'DM Mono',monospace;font-size:11px;color:var(--gold);letter-spacing:2.5px;text-transform:uppercase;margin-bottom:20px;display:flex;align-items:center;gap:10px;}
.eyebrow::before{content:'';width:24px;height:1px;background:var(--gold);}
h1{font-family:'Fraunces',serif;font-size:clamp(44px,5vw,68px);font-weight:600;line-height:1.08;color:var(--navy);margin-bottom:22px;}
h1 em{font-style:italic;color:var(--gold);}
.hero-body{font-size:16px;color:var(--slate);line-height:1.8;max-width:440px;margin-bottom:36px;}
.hero-btns{display:flex;gap:12px;flex-wrap:wrap;}
.hero-stats{display:flex;gap:36px;margin-top:52px;padding-top:40px;border-top:1px solid var(--rule);}
.stat-n{font-family:'Fraunces',serif;font-size:36px;font-weight:700;color:var(--navy);}
.stat-l{font-size:11px;color:var(--slate);margin-top:3px;font-family:'DM Mono',monospace;letter-spacing:.5px;}
.hero-right{padding:80px 80px 80px 60px;display:flex;flex-direction:column;justify-content:center;position:relative;z-index:1;}
.role-switch{display:flex;gap:4px;background:rgba(255,255,255,.08);border-radius:10px;padding:4px;margin-bottom:24px;}
.role-btn{flex:1;padding:10px;border:none;cursor:pointer;border-radius:8px;font-family:'Geist',sans-serif;font-size:13px;font-weight:500;color:rgba(255,255,255,.5);background:none;transition:all .2s;}
.role-btn.active{background:rgba(255,255,255,.13);color:white;}
.info-card{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.12);border-radius:16px;padding:28px;display:none;}
.info-card.active{display:block;}
.card-tag{font-family:'DM Mono',monospace;font-size:10px;color:var(--gold2);letter-spacing:2px;text-transform:uppercase;margin-bottom:14px;}
.card-h{font-family:'Fraunces',serif;font-size:26px;font-weight:600;color:white;line-height:1.2;margin-bottom:18px;}
.card-li{display:flex;align-items:flex-start;gap:9px;margin-bottom:12px;font-size:13.5px;color:rgba(255,255,255,.7);}
.card-li::before{content:'✓';color:var(--gold2);font-weight:700;flex-shrink:0;margin-top:1px;}
.card-action{display:block;margin-top:22px;background:var(--gold);color:white;border:none;border-radius:8px;padding:13px;font-family:'Geist',sans-serif;font-size:14px;font-weight:600;cursor:pointer;text-align:center;text-decoration:none;transition:all .2s;width:100%;}
.card-action:hover{background:#9a7d24;}
/* SECTIONS */
.wrap{max-width:1200px;margin:0 auto;padding:52px 32px;}
.page-hdr{margin-bottom:40px;}
.page-hdr h2{font-family:'Fraunces',serif;font-size:38px;color:var(--navy);font-weight:600;}
.page-hdr p{color:var(--slate);font-size:15px;margin-top:8px;}
/* TT embed */
.tt-wrap{background:white;border-radius:16px;border:1px solid var(--rule);overflow:hidden;margin-bottom:40px;box-shadow:0 4px 24px rgba(3,58,109,.07);}
.tt-hdr{padding:18px 24px;border-bottom:1px solid var(--rule);display:flex;align-items:center;justify-content:space-between;}
.tt-label{font-family:'DM Mono',monospace;font-size:11px;color:var(--slate);letter-spacing:1.5px;text-transform:uppercase;display:flex;align-items:center;gap:8px;}
.live-dot{width:8px;height:8px;border-radius:50%;background:var(--green);animation:pulse 2s infinite;}
@keyframes pulse{0%,100%{opacity:1;}50%{opacity:.4;}}
/* Prop cards */
.prop-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:20px;margin-top:28px;}
.prop-card{background:white;border:1px solid var(--rule);border-radius:14px;overflow:hidden;transition:all .25s;cursor:pointer;}
.prop-card:hover{transform:translateY(-3px);box-shadow:0 12px 36px rgba(3,58,109,.1);border-color:var(--navy);}
.prop-img{height:160px;display:flex;align-items:center;justify-content:center;font-size:46px;background:var(--mist);}
.prop-body{padding:18px;}
.prop-price{font-family:'Fraunces',serif;font-size:22px;font-weight:700;color:var(--navy);}
.prop-price span{font-size:12px;font-weight:400;color:var(--slate);}
.prop-addr{font-size:13px;color:var(--slate);margin:5px 0 12px;line-height:1.4;}
.prop-tags{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:14px;}
.tag{font-family:'DM Mono',monospace;font-size:10px;padding:2px 7px;border-radius:4px;}
.tag-green{background:#DCFCE7;color:#166534;}.tag-navy{background:var(--mist);color:var(--navy);}
.prop-btn{width:100%;padding:10px;border-radius:8px;border:none;cursor:pointer;font-family:'Geist',sans-serif;font-size:13px;font-weight:600;background:var(--navy);color:white;transition:all .2s;}
.prop-btn:hover{background:var(--navy2);}
/* MODAL */
.modal-bg{position:fixed;inset:0;z-index:500;background:rgba(13,17,23,.8);backdrop-filter:blur(6px);display:none;align-items:flex-start;justify-content:center;padding:80px 20px 20px;overflow-y:auto;}
.modal-bg.open{display:flex;}
.modal-box{background:white;border-radius:20px;width:100%;max-width:660px;position:relative;animation:mIn .3s ease;margin-bottom:40px;}
@keyframes mIn{from{opacity:0;transform:translateY(14px);}to{opacity:1;transform:translateY(0);}}
.modal-close{position:absolute;top:14px;right:14px;background:var(--mist);border:none;cursor:pointer;width:30px;height:30px;border-radius:50%;font-size:16px;color:var(--slate);display:flex;align-items:center;justify-content:center;}
.modal-hero-bar{background:var(--navy);padding:28px 32px;border-radius:20px 20px 0 0;}
.modal-hero-bar .eyebrow{color:var(--gold2);}.modal-hero-bar .eyebrow::before{background:var(--gold2);}
.modal-hero-bar h3{font-family:'Fraunces',serif;font-size:26px;font-weight:600;color:white;margin-bottom:4px;}
.modal-hero-bar p{font-size:13px;color:rgba(255,255,255,.5);}
.modal-body{padding:28px 32px;}
.clone-box{background:var(--cream);border:1.5px solid var(--rule);border-radius:10px;padding:16px;margin:12px 0;}
.clone-lbl{font-family:'DM Mono',monospace;font-size:10px;color:var(--slate);letter-spacing:1.5px;text-transform:uppercase;margin-bottom:10px;}
.clone-row{display:flex;justify-content:space-between;padding:6px 0;border-bottom:1px solid var(--rule);font-size:13px;}
.clone-row:last-child{border-bottom:none;}
.ck{color:var(--slate);}.cv{color:var(--navy);font-weight:600;font-family:'DM Mono',monospace;font-size:11px;}
.f-row{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:10px;}
.f-row.one{grid-template-columns:1fr;}
.f-row.three{grid-template-columns:1fr 1fr 1fr;}
.f-grp{display:flex;flex-direction:column;gap:5px;}
.f-lbl{font-size:12px;color:var(--slate);font-weight:500;}
.f-inp{padding:10px 12px;border:1.5px solid var(--rule);border-radius:8px;font-family:'Geist',sans-serif;font-size:14px;color:var(--ink);outline:none;transition:border-color .2s;}
.f-inp:focus{border-color:var(--navy);}
.f-sel{padding:10px 12px;border:1.5px solid var(--rule);border-radius:8px;font-family:'Geist',sans-serif;font-size:14px;color:var(--ink);background:white;outline:none;cursor:pointer;}
.f-sec-lbl{font-family:'DM Mono',monospace;font-size:10px;color:var(--slate);letter-spacing:2px;text-transform:uppercase;margin:20px 0 12px;padding-bottom:8px;border-bottom:1px solid var(--rule);}
.modal-footer{padding:0 32px 28px;display:flex;gap:10px;}
/* APPLY */
.apply-wrap{max-width:740px;margin:0 auto;padding:48px 24px;}
.a-prog{display:flex;gap:0;margin-bottom:36px;background:white;border:1px solid var(--rule);border-radius:10px;overflow:hidden;}
.a-step{flex:1;padding:13px 8px;text-align:center;font-size:12px;font-weight:500;color:var(--slate);background:var(--cream);border-right:1px solid var(--rule);transition:all .3s;cursor:pointer;}
.a-step:last-child{border-right:none;}
.a-step.done{background:#DCFCE7;color:#166534;}
.a-step.cur{background:var(--navy);color:white;}
.a-step-n{display:block;font-family:'Fraunces',serif;font-size:20px;font-weight:700;margin-bottom:2px;}
.a-panel{display:none;}
.a-panel.active{display:block;}
.step-card{background:white;border:1px solid var(--rule);border-radius:16px;padding:28px;margin-bottom:16px;}
.step-card-h{font-family:'Fraunces',serif;font-size:22px;color:var(--navy);margin-bottom:6px;}
.step-card-sub{font-size:13.5px;color:var(--slate);margin-bottom:20px;}
/* Prop selector */
.prop-sel{background:var(--cream);border:1.5px solid var(--rule);border-radius:10px;overflow:hidden;}
.psel-hdr{padding:12px 16px;font-size:13px;font-weight:600;color:var(--navy);border-bottom:1px solid var(--rule);background:white;display:flex;justify-content:space-between;align-items:center;}
.psel-opt{display:flex;align-items:center;gap:12px;padding:11px 16px;border-bottom:1px solid var(--rule);cursor:pointer;transition:background .15s;}
.psel-opt:last-child{border-bottom:none;}
.psel-opt:hover{background:var(--mist);}
.psel-opt.sel{background:#EBF2FF;}
.p-radio{width:18px;height:18px;border-radius:50%;border:2px solid var(--rule);display:flex;align-items:center;justify-content:center;flex-shrink:0;transition:all .2s;}
.psel-opt.sel .p-radio{border-color:var(--navy);}
.p-radio-in{width:8px;height:8px;border-radius:50%;background:var(--navy);display:none;}
.psel-opt.sel .p-radio-in{display:block;}
.autofill-note{display:flex;align-items:center;gap:6px;font-size:11.5px;color:#166534;margin:8px 0 0;}
.autofill-note::before{content:'⚡';}
/* ID flow */
.id-prog{display:flex;gap:0;margin-bottom:20px;overflow:hidden;border-radius:10px;border:1px solid var(--rule);}
.id-stp{flex:1;padding:10px;text-align:center;font-size:12px;font-weight:500;color:var(--slate);background:var(--cream);border-right:1px solid var(--rule);transition:all .3s;}
.id-stp:last-child{border-right:none;}
.id-stp.done{background:#DCFCE7;color:#166534;}
.id-stp.cur{background:var(--navy);color:white;}
.id-stp-i{display:block;font-size:16px;margin-bottom:2px;}
.upload-zone{border:2px dashed var(--rule);border-radius:10px;padding:28px;text-align:center;cursor:pointer;transition:all .2s;background:var(--cream);}
.upload-zone:hover{border-color:var(--navy);background:var(--mist);}
.upload-zone input{display:none;}
.upload-icon-big{font-size:28px;margin-bottom:8px;}
.upload-lbl{font-size:14px;color:var(--slate);}
.upload-sub{font-size:12px;color:#aaa;margin-top:3px;}
.id-file-preview{display:none;background:var(--cream);border:1.5px solid var(--green);border-radius:10px;padding:14px;flex-direction:row;align-items:center;gap:12px;margin-top:10px;}
.id-file-preview.show{display:flex;}
.verified-badge{display:none;background:#DCFCE7;border:1px solid #A7F3D0;border-radius:8px;padding:10px 14px;font-size:13px;color:#166534;font-weight:500;align-items:center;gap:8px;margin-top:12px;}
.verified-badge.show{display:flex;}
/* Payment */
.pay-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:12px;}
.pay-m{border:1.5px solid var(--rule);border-radius:8px;padding:11px 6px;text-align:center;cursor:pointer;transition:all .2s;background:white;}
.pay-m:hover{border-color:var(--navy);}
.pay-m.sel{border-color:var(--navy);background:#EBF2FF;}
.pay-ico{font-size:20px;margin-bottom:3px;}
.pay-nm{font-size:11px;font-weight:600;color:var(--navy);}
.pay-instr{display:none;background:var(--cream);border:1.5px solid var(--rule);border-radius:10px;padding:16px;}
.pay-instr.show{display:block;}
/* Submit btn */
.sub-btn{width:100%;padding:14px;border-radius:10px;border:none;background:var(--navy);color:white;font-family:'Geist',sans-serif;font-size:15px;font-weight:600;cursor:pointer;transition:all .2s;margin-top:8px;}
.sub-btn:hover{background:var(--navy2);transform:translateY(-1px);}
/* TRACKING */
.track-wrap{max-width:1100px;margin:0 auto;padding:52px 32px;}
.kpi-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;margin-bottom:28px;}
.kpi{background:white;border:1px solid var(--rule);border-radius:12px;padding:20px;}
.kpi-lbl{font-family:'DM Mono',monospace;font-size:10px;color:var(--slate);letter-spacing:1.5px;text-transform:uppercase;margin-bottom:8px;}
.kpi-n{font-family:'Fraunces',serif;font-size:34px;font-weight:700;color:var(--navy);line-height:1;}
.kpi-sub{font-size:12px;color:var(--slate);margin-top:4px;}
.kpi-badge{display:inline-flex;align-items:center;gap:4px;font-size:11px;font-weight:600;padding:3px 8px;border-radius:20px;margin-top:7px;}
.bg-g{background:#DCFCE7;color:#166534;}.bg-a{background:#FEF3C7;color:#92400E;}
.tbl-wrap{background:white;border:1px solid var(--rule);border-radius:14px;overflow:hidden;}
.tbl-hdr{padding:16px 24px;border-bottom:1px solid var(--rule);display:flex;align-items:center;justify-content:space-between;}
.tbl-title{font-size:16px;font-weight:600;color:var(--navy);}
.tbl-scroll{overflow-x:auto;}
table{width:100%;border-collapse:collapse;}
th{background:var(--cream);font-family:'DM Mono',monospace;font-size:10px;letter-spacing:1.5px;text-transform:uppercase;color:var(--slate);padding:10px 18px;text-align:left;border-bottom:1px solid var(--rule);white-space:nowrap;}
td{padding:13px 18px;font-size:13.5px;border-bottom:1px solid #F5F5F5;vertical-align:middle;}
tr:last-child td{border-bottom:none;}
tr:hover td{background:#FAFBFD;}
.pill{display:inline-flex;align-items:center;gap:5px;padding:4px 10px;border-radius:20px;font-size:11px;font-weight:600;}
.pill-live{background:#DCFCE7;color:#166534;}.pill-pend{background:#FEF3C7;color:#92400E;}.pill-rev{background:#DBEAFE;color:#1E40AF;}
.pdot{width:6px;height:6px;border-radius:50%;}
.pill-live .pdot{background:#16A34A;}.pill-pend .pdot{background:#D97706;}.pill-rev .pdot{background:#2563EB;}
.mono{font-family:'DM Mono',monospace;font-size:12px;color:var(--slate);}
.act-link{font-size:12px;font-weight:600;color:var(--navy);background:none;border:none;cursor:pointer;text-decoration:underline;}
.feed-wrap{background:white;border:1px solid var(--rule);border-radius:14px;overflow:hidden;margin-top:20px;}
.feed-item{display:flex;align-items:flex-start;gap:14px;padding:14px 24px;border-bottom:1px solid #F5F5F5;}
.feed-item:last-child{border-bottom:none;}
.feed-dot{width:32px;height:32px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:14px;flex-shrink:0;}
.feed-title{font-size:13.5px;font-weight:500;color:var(--ink);}
.feed-sub{font-size:12px;color:var(--slate);margin-top:2px;}
.feed-time{font-family:'DM Mono',monospace;font-size:11px;color:#bbb;white-space:nowrap;margin-left:auto;}
/* FOOTER */
footer{background:var(--ink);padding:56px 80px 28px;border-top:1px solid rgba(255,255,255,.05);}
.ft-grid{display:grid;grid-template-columns:2fr 1fr 1fr 1fr;gap:48px;margin-bottom:40px;}
.ft-brand{font-family:'Fraunces',serif;font-size:26px;font-weight:700;color:white;margin-bottom:12px;}
.ft-brand span{color:var(--gold);}
.ft-tagline{font-size:13px;color:rgba(255,255,255,.4);line-height:1.8;max-width:260px;margin-bottom:18px;}
.ft-contact{font-size:13px;color:rgba(255,255,255,.45);line-height:2.2;}
.ft-contact a{color:rgba(255,255,255,.45);text-decoration:none;}
.ft-col-h{font-size:11px;font-weight:600;color:white;letter-spacing:1px;text-transform:uppercase;margin-bottom:14px;}
.ft-links{list-style:none;}
.ft-links li{margin-bottom:9px;}
.ft-links a{font-size:13.5px;color:rgba(255,255,255,.4);text-decoration:none;transition:color .2s;}
.ft-links a:hover{color:var(--gold2);}
.ft-btm{padding-top:18px;border-top:1px solid rgba(255,255,255,.06);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:10px;}
.ft-legal{font-family:'DM Mono',monospace;font-size:10.5px;color:rgba(255,255,255,.2);}
.toast{position:fixed;bottom:28px;right:28px;z-index:9999;background:var(--navy);color:white;padding:13px 22px;border-radius:10px;font-size:13.5px;font-weight:500;display:none;align-items:center;gap:9px;box-shadow:0 8px 28px rgba(0,0,0,.25);animation:tIn .3s ease;}
.toast.show{display:flex;}
@keyframes tIn{from{opacity:0;transform:translateY(8px);}to{opacity:1;transform:translateY(0);}}
@media(max-width:900px){
  nav{padding:0 16px;}.nav-tabs{display:none;}.hamburger{display:flex;}
  .mobile-nav{display:none;position:fixed;top:64px;left:0;right:0;z-index:190;background:var(--paper);border-bottom:1px solid var(--rule);padding:10px 16px 16px;}
  .mobile-nav.open{display:block;}
  .mobile-nav button{display:block;width:100%;padding:12px 14px;text-align:left;background:none;border:none;cursor:pointer;font-family:'Geist',sans-serif;font-size:15px;color:var(--navy);border-bottom:1px solid var(--rule);}
  .hero{grid-template-columns:1fr;}.hero-bg{background:none;}.hero-right{background:var(--navy);}
  .hero-left{padding:48px 20px;}.hero-right{padding:40px 20px;}
  .hero-stats{gap:20px;flex-wrap:wrap;}
  .kpi-grid{grid-template-columns:1fr 1fr;}
  .ft-grid{grid-template-columns:1fr 1fr;gap:28px;}
  .ft-btm{flex-direction:column;text-align:center;}
  .pay-grid{grid-template-columns:repeat(4,1fr);}
  footer{padding:40px 20px 20px;}
  .wrap,.track-wrap,.apply-wrap{padding:32px 16px;}
  .prop-grid{grid-template-columns:1fr;}
  .f-row{grid-template-columns:1fr;}.f-row.three{grid-template-columns:1fr;}
  th,td{padding:9px 12px;}
  .modal-hero-bar,.modal-body,.modal-footer{padding-left:20px;padding-right:20px;}
}
</style>
</head>
<body>

<nav id="mainNav">
  <div class="brand" onclick="showPage('home')">VIVIA<span>.</span></div>
  <div class="nav-tabs" id="navTabs">
    <button class="nav-tab active" onclick="showPage('home')">Home</button>
    <button class="nav-tab" onclick="showPage('listings')">Listings</button>
    <button class="nav-tab" onclick="showPage('apply')">Apply</button>
    <button class="nav-tab" onclick="showPage('tracking')">Live Tracking</button>
    <button class="nav-tab" onclick="showPage('landlord')">Landlords</button>
  </div>
  <div class="nav-right">
    <button class="btn-sm btn-navy" onclick="showPage('apply')">Apply Now</button>
    <button class="hamburger" onclick="toggleMobile()"><span></span><span></span><span></span></button>
  </div>
</nav>

<div class="mobile-nav" id="mobileNav">
  <button onclick="showPage('home');toggleMobile()">Home</button>
  <button onclick="showPage('listings');toggleMobile()">Listings</button>
  <button onclick="showPage('apply');toggleMobile()">Apply Now</button>
  <button onclick="showPage('tracking');toggleMobile()">Live Tracking</button>
  <button onclick="showPage('landlord');toggleMobile()">For Landlords</button>
</div>

<!-- HOME -->
<div class="page active" id="page-home">
  <section class="hero">
    <div class="hero-bg"></div>
    <div class="hero-left">
      <div class="eyebrow">Illinois & Texas Markets</div>
      <h1>Find your<br><em>perfect home</em><br>with VIVIA</h1>
      <p class="hero-body">Premium residential property management connecting quality renters with exceptional homes — and helping landlords maximize returns.</p>
      <div class="hero-btns">
        <button class="btn-sm btn-navy" style="padding:13px 26px;font-size:14px;" onclick="showPage('listings')">Browse Listings</button>
        <button class="btn-sm btn-gold" style="padding:13px 26px;font-size:14px;" onclick="showPage('apply')">Apply Now</button>
      </div>
      <div class="hero-stats">
        <div><div class="stat-n">28+</div><div class="stat-l">Leads/listing</div></div>
        <div><div class="stat-n">48h</div><div class="stat-l">Time to market</div></div>
        <div><div class="stat-n">40+</div><div class="stat-l">Platforms</div></div>
        <div><div class="stat-n">4</div><div class="stat-l">Markets</div></div>
      </div>
    </div>
    <div class="hero-right">
      <div class="role-switch">
        <button class="role-btn active" onclick="switchRole('renter',this)">I'm a Renter</button>
        <button class="role-btn" onclick="switchRole('landlord',this)">I'm a Landlord</button>
      </div>
      <div class="info-card active" id="ic-renter">
        <div class="card-tag">Renter Portal</div>
        <div class="card-h">Find your home. Apply today.</div>
        <div class="card-li">Verified listings in IL &amp; TX</div>
        <div class="card-li">Secure online application — no paper needed</div>
        <div class="card-li">Credit &amp; background screening — free for you</div>
        <div class="card-li">8 flexible payment options for app fee &amp; rent</div>
        <button class="card-action" onclick="showPage('apply')">Start My Application →</button>
      </div>
      <div class="info-card" id="ic-landlord">
        <div class="card-tag">Landlord Portal</div>
        <div class="card-h">List once. Reach thousands.</div>
        <div class="card-li">One-click syndication to 40+ rental platforms</div>
        <div class="card-li">Average 28 qualified leads per property</div>
        <div class="card-li">Full tenant screening, leasing &amp; rent collection</div>
        <div class="card-li">Fully remote — manage from anywhere</div>
        <button class="card-action" onclick="showPage('landlord')">List My Property →</button>
      </div>
    </div>
  </section>
</div>

<!-- LISTINGS -->
<div class="page" id="page-listings">
  <div class="wrap">
    <div class="page-hdr">
      <h2>Active Listings</h2>
      <p>All properties managed by VIVIA Rentals &amp; Property Services · AP Illinois Management LLC</p>
    </div>
    <div class="tt-wrap">
      <div class="tt-hdr">
        <div class="tt-label"><span class="live-dot"></span>Live TurboTenant Feed — VIVIA Portfolio</div>
        <span style="font-family:'DM Mono',monospace;font-size:11px;color:#aaa;">rental.turbotenant.com</span>
      </div>
      <iframe style="border:none;display:block;" src="https://rental.turbotenant.com/embedpropertylist.html#/QmFzaWNVc2VyUHJvZmlsZToxMTA2NTAy" height="580" width="100%" title="VIVIA Live Listings" loading="lazy"></iframe>
    </div>
    <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;">
      <h3 style="font-family:'Fraunces',serif;font-size:22px;color:var(--navy);">Featured Properties</h3>
      <span style="font-family:'DM Mono',monospace;font-size:11px;color:var(--slate);">4 ACTIVE</span>
    </div>
    <div class="prop-grid" id="propGrid"></div>
  </div>
</div>

<!-- APPLY -->
<div class="page" id="page-apply">
  <div class="apply-wrap">
    <div class="page-hdr">
      <h2>Rental Application</h2>
      <p>Secure · Takes ~10 minutes · $75 application fee</p>
    </div>
    <div class="a-prog" id="aProg">
      <div class="a-step cur"><span class="a-step-n">1</span>Property</div>
      <div class="a-step"><span class="a-step-n">2</span>Personal</div>
      <div class="a-step"><span class="a-step-n">3</span>Verify ID</div>
      <div class="a-step"><span class="a-step-n">4</span>Payment</div>
      <div class="a-step"><span class="a-step-n">5</span>Submit</div>
    </div>

    <!-- Step 1 -->
    <div class="a-panel active" id="ap1">
      <div class="step-card">
        <div class="step-card-h">Select a Property</div>
        <div class="step-card-sub">Choose your desired property — form fields auto-populate from our listing database.</div>
        <div class="prop-sel" id="propSel"></div>
        <div id="clonePreview" style="display:none;margin-top:12px;">
          <div class="autofill-note">Property data auto-cloned from listing</div>
          <div class="clone-box" style="margin-top:8px;">
            <div class="clone-lbl">Cloned Listing Data</div>
            <div class="clone-row"><span class="ck">Property</span><span class="cv" id="cpAddr">—</span></div>
            <div class="clone-row"><span class="ck">Monthly Rent</span><span class="cv" id="cpRent">—</span></div>
            <div class="clone-row"><span class="ck">Deposit</span><span class="cv" id="cpDep">—</span></div>
            <div class="clone-row"><span class="ck">Lease Term</span><span class="cv" id="cpLease">—</span></div>
            <div class="clone-row"><span class="ck">App Fee</span><span class="cv">$75.00</span></div>
            <div class="clone-row"><span class="ck">TurboTenant ID</span><span class="cv" id="cpTTID">—</span></div>
          </div>
        </div>
      </div>
      <button class="sub-btn" onclick="nextApply(2)">Continue →</button>
    </div>

    <!-- Step 2 -->
    <div class="a-panel" id="ap2">
      <div class="step-card">
        <div class="step-card-h">Personal Information</div>
        <div class="step-card-sub">Details must match your government-issued ID exactly.</div>
        <div class="f-sec-lbl">Applicant</div>
        <div class="f-row"><div class="f-grp"><label class="f-lbl">First Name</label><input class="f-inp" id="aFirst" placeholder="Mercedaes"></div><div class="f-grp"><label class="f-lbl">Last Name</label><input class="f-inp" id="aLast" placeholder="Ellis"></div></div>
        <div class="f-row"><div class="f-grp"><label class="f-lbl">Email</label><input class="f-inp" id="aEmail" type="email" placeholder="you@email.com"></div><div class="f-grp"><label class="f-lbl">Phone</label><input class="f-inp" id="aPhone" placeholder="(815) 000-0000"></div></div>
        <div class="f-row"><div class="f-grp"><label class="f-lbl">Date of Birth</label><input class="f-inp" id="aDOB" type="date"></div><div class="f-grp"><label class="f-lbl">SSN (last 4)</label><input class="f-inp" id="aSSN" placeholder="****" maxlength="4"></div></div>
        <div class="f-sec-lbl">Current Address</div>
        <div class="f-row one"><div class="f-grp"><label class="f-lbl">Street Address</label><input class="f-inp" id="aAddr" placeholder="773 N Edgemere Dr, Apt A"></div></div>
        <div class="f-row three">
          <div class="f-grp"><label class="f-lbl">City</label><input class="f-inp" id="aCity" placeholder="Bourbonnais"></div>
          <div class="f-grp"><label class="f-lbl">State</label><select class="f-sel" id="aState"><option>IL</option><option>TX</option><option>FL</option><option>Other</option></select></div>
          <div class="f-grp"><label class="f-lbl">Zip</label><input class="f-inp" id="aZip" placeholder="60914"></div>
        </div>
        <div class="f-sec-lbl">Employment</div>
        <div class="f-row"><div class="f-grp"><label class="f-lbl">Occupation</label><input class="f-inp" id="aOcc" placeholder="Security Officer"></div><div class="f-grp"><label class="f-lbl">Monthly Income</label><input class="f-inp" id="aIncome" placeholder="$2,700"></div></div>
        <div class="f-row"><div class="f-grp"><label class="f-lbl">Adults</label><input class="f-inp" id="aAdults" type="number" min="1" placeholder="2"></div><div class="f-grp"><label class="f-lbl">Children</label><input class="f-inp" id="aKids" type="number" min="0" placeholder="0"></div></div>
        <div class="f-row"><div class="f-grp"><label class="f-lbl">Pets</label><select class="f-sel" id="aPets"><option>No</option><option>Yes — dog</option><option>Yes — cat</option><option>Yes — other</option></select></div><div class="f-grp"><label class="f-lbl">Desired Move-In</label><input class="f-inp" id="aMoveIn" type="date"></div></div>
      </div>
      <div style="display:flex;gap:10px;"><button class="sub-btn" style="background:var(--mist);color:var(--navy);flex:0 0 100px;margin:0;" onclick="nextApply(1)">← Back</button><button class="sub-btn" style="margin:0;" onclick="nextApply(3)">Continue →</button></div>
    </div>

    <!-- Step 3 ID -->
    <div class="a-panel" id="ap3">
      <div class="step-card">
        <div class="step-card-h">Identity Verification</div>
        <div class="step-card-sub">Upload government-issued ID. Required for all applications.</div>
        <div class="id-prog">
          <div class="id-stp cur" id="ids1"><span class="id-stp-i">📄</span>ID Front</div>
          <div class="id-stp" id="ids2"><span class="id-stp-i">🔄</span>ID Back</div>
          <div class="id-stp" id="ids3"><span class="id-stp-i">🤳</span>Selfie</div>
          <div class="id-stp" id="ids4"><span class="id-stp-i">✅</span>Done</div>
        </div>
        <div id="idFrontZone">
          <p style="font-size:13px;font-weight:600;color:var(--navy);margin-bottom:10px;">Step 1 — Front of ID (Driver's License or Passport)</p>
          <div class="upload-zone" onclick="document.getElementById('idF').click()">
            <input type="file" id="idF" accept="image/*" onchange="handleID('front',this)">
            <div class="upload-icon-big">🪪</div>
            <div class="upload-lbl">Click to upload front of ID</div>
            <div class="upload-sub">JPG, PNG or HEIC · Max 20MB</div>
          </div>
          <div class="id-file-preview" id="idFPrev"><span style="font-size:22px;">✅</span><div><div style="font-size:13px;font-weight:600;color:var(--navy);" id="idFN">—</div><div style="font-size:12px;color:var(--slate);" id="idFS">—</div></div></div>
        </div>
        <div id="idBackZone" style="display:none;margin-top:18px;">
          <p style="font-size:13px;font-weight:600;color:var(--navy);margin-bottom:10px;">Step 2 — Back of ID</p>
          <div class="upload-zone" onclick="document.getElementById('idB').click()">
            <input type="file" id="idB" accept="image/*" onchange="handleID('back',this)">
            <div class="upload-icon-big">🔄</div>
            <div class="upload-lbl">Upload back of ID</div>
            <div class="upload-sub">JPG, PNG or HEIC · Max 20MB</div>
          </div>
          <div class="id-file-preview" id="idBPrev"><span style="font-size:22px;">✅</span><div><div style="font-size:13px;font-weight:600;color:var(--navy);" id="idBN">—</div><div style="font-size:12px;color:var(--slate);" id="idBS">—</div></div></div>
        </div>
        <div id="idSelfieZone" style="display:none;margin-top:18px;">
          <p style="font-size:13px;font-weight:600;color:var(--navy);margin-bottom:10px;">Step 3 — Selfie holding your ID</p>
          <div class="upload-zone" onclick="document.getElementById('idS').click()">
            <input type="file" id="idS" accept="image/*" capture="user" onchange="handleID('selfie',this)">
            <div class="upload-icon-big">🤳</div>
            <div class="upload-lbl">Take or upload selfie with ID</div>
            <div class="upload-sub">Hold ID clearly visible next to your face</div>
          </div>
          <div class="id-file-preview" id="idSPrev"><span style="font-size:22px;">✅</span><div><div style="font-size:13px;font-weight:600;color:var(--navy);" id="idSN">—</div><div style="font-size:12px;color:var(--slate);" id="idSS">—</div></div></div>
        </div>
        <div class="verified-badge" id="idVerified">✅ All identity documents uploaded — pending review</div>
      </div>
      <div style="display:flex;gap:10px;"><button class="sub-btn" style="background:var(--mist);color:var(--navy);flex:0 0 100px;margin:0;" onclick="nextApply(2)">← Back</button><button class="sub-btn" style="margin:0;opacity:.5;cursor:not-allowed;" id="idNext" disabled onclick="nextApply(4)">Continue →</button></div>
    </div>

    <!-- Step 4 Payment -->
    <div class="a-panel" id="ap4">
      <div class="step-card">
        <div class="step-card-h">Application Fee — $75</div>
        <div class="step-card-sub">Non-refundable. Select your payment method below.</div>
        <div class="pay-grid">
          <div class="pay-m" onclick="choosePay(this,'Zelle')"><div class="pay-ico">💸</div><div class="pay-nm">Zelle</div></div>
          <div class="pay-m" onclick="choosePay(this,'Cash App')"><div class="pay-ico">💚</div><div class="pay-nm">Cash App</div></div>
          <div class="pay-m" onclick="choosePay(this,'PayPal')"><div class="pay-ico">🅿️</div><div class="pay-nm">PayPal</div></div>
          <div class="pay-m" onclick="choosePay(this,'Apple Pay')"><div class="pay-ico">🍎</div><div class="pay-nm">Apple Pay</div></div>
          <div class="pay-m" onclick="choosePay(this,'Chime')"><div class="pay-ico">🟢</div><div class="pay-nm">Chime</div></div>
          <div class="pay-m" onclick="choosePay(this,'ACH')"><div class="pay-ico">🏦</div><div class="pay-nm">ACH</div></div>
          <div class="pay-m" onclick="choosePay(this,'USDC')"><div class="pay-ico">🪙</div><div class="pay-nm">USDC</div></div>
          <div class="pay-m" onclick="choosePay(this,'Store')"><div class="pay-ico">🏪</div><div class="pay-nm">Store</div></div>
        </div>
        <div class="pay-instr" id="payInstr"><div style="font-family:'DM Mono',monospace;font-size:10px;color:var(--slate);letter-spacing:1.5px;text-transform:uppercase;margin-bottom:10px;">Instructions</div><div id="payText" style="font-size:13.5px;color:var(--ink);line-height:1.8;"></div></div>
      </div>
      <div style="display:flex;gap:10px;"><button class="sub-btn" style="background:var(--mist);color:var(--navy);flex:0 0 100px;margin:0;" onclick="nextApply(3)">← Back</button><button class="sub-btn" style="margin:0;" onclick="nextApply(5)">I've Paid →</button></div>
    </div>

    <!-- Step 5 Review -->
    <div class="a-panel" id="ap5">
      <div class="step-card">
        <div class="step-card-h">Review &amp; Submit</div>
        <div class="step-card-sub">Confirm your application details.</div>
        <div id="reviewBox"></div>
        <div style="margin-top:16px;padding:14px;background:#FEF3C7;border:1px solid #FDE68A;border-radius:10px;font-size:13px;color:#92400E;line-height:1.6;">⚠️ By submitting you authorize VIVIA Rentals to conduct background, credit, and identity checks per Fair Housing Act guidelines.</div>
      </div>
      <button class="sub-btn" style="background:var(--green);" onclick="submitApp()">Submit Application ✓</button>
    </div>
  </div>
</div>

<!-- TRACKING -->
<div class="page" id="page-tracking">
  <div class="track-wrap">
    <div class="page-hdr"><h2>Live Property Tracking</h2><p>Real-time portfolio status · VIVIA Rentals &amp; Property Services</p></div>
    <div class="kpi-grid">
      <div class="kpi"><div class="kpi-lbl">Active Listings</div><div class="kpi-n">4</div><div class="kpi-sub">IL &amp; TX markets</div><div class="kpi-badge bg-g">All Live</div></div>
      <div class="kpi"><div class="kpi-lbl">Total Leads</div><div class="kpi-n" id="kLeads">55</div><div class="kpi-sub">Across all properties</div><div class="kpi-badge bg-g">+12 this week</div></div>
      <div class="kpi"><div class="kpi-lbl">Applications</div><div class="kpi-n">3</div><div class="kpi-sub">Pending review</div><div class="kpi-badge bg-a">2 In Review</div></div>
      <div class="kpi"><div class="kpi-lbl">Revenue/Mo</div><div class="kpi-n">$7,275</div><div class="kpi-sub">Combined rent</div><div class="kpi-badge bg-g">On Track</div></div>
    </div>
    <div class="tbl-wrap">
      <div class="tbl-hdr"><div class="tbl-title">Portfolio — Live Status</div><button class="btn-sm btn-outline" style="font-size:12px;padding:6px 14px;" onclick="refreshKPI()">↻ Refresh</button></div>
      <div class="tbl-scroll"><table><thead><tr><th>Property</th><th>Rent</th><th>Status</th><th>Leads</th><th>Applications</th><th>Platform</th><th>TT Listing ID</th><th>Action</th></tr></thead><tbody id="trackBody"></tbody></table></div>
    </div>
    <div class="feed-wrap"><div class="tbl-hdr" style="border-bottom:1px solid var(--rule);"><div class="tbl-title">Recent Activity</div><span class="live-dot"></span></div><div id="actFeed"></div></div>
  </div>
</div>

<!-- LANDLORD -->
<div class="page" id="page-landlord">
  <div class="wrap">
    <div class="page-hdr"><h2>List Your Property</h2><p>VIVIA handles the entire tenant acquisition process — you just collect rent.</p></div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:24px;margin-bottom:36px;">
      <div style="background:white;border:1px solid var(--rule);border-radius:16px;padding:28px;">
        <div style="font-family:'Fraunces',serif;font-size:22px;color:var(--navy);margin-bottom:18px;">Property Submission</div>
        <div class="f-row"><div class="f-grp"><label class="f-lbl">Your Name</label><input class="f-inp" id="llN" placeholder="Full name"></div><div class="f-grp"><label class="f-lbl">Phone</label><input class="f-inp" id="llP" placeholder="(815) 000-0000"></div></div>
        <div class="f-row one"><div class="f-grp"><label class="f-lbl">Email</label><input class="f-inp" id="llE" placeholder="you@email.com"></div></div>
        <div class="f-row one"><div class="f-grp"><label class="f-lbl">Property Address</label><input class="f-inp" id="llA" placeholder="123 Main St, Chicago IL 60601" oninput="llPreview()"></div></div>
        <div class="f-row"><div class="f-grp"><label class="f-lbl">Monthly Rent</label><input class="f-inp" id="llR" placeholder="$1,500" oninput="llPreview()"></div><div class="f-grp"><label class="f-lbl">Beds/Baths</label><input class="f-inp" id="llB" placeholder="3 bd / 2 ba"></div></div>
        <div class="f-row"><div class="f-grp"><label class="f-lbl">Lease Term</label><select class="f-sel" id="llL"><option>12 months</option><option>Rent to Own</option><option>Monthly</option><option>6 months</option></select></div><div class="f-grp"><label class="f-lbl">Property Type</label><select class="f-sel" id="llT"><option>Single Family</option><option>Townhouse</option><option>Condo</option><option>Multi-Family</option></select></div></div>
        <button class="sub-btn" onclick="submitLL()">Submit Property →</button>
      </div>
      <div style="background:var(--navy);border-radius:16px;padding:28px;">
        <div style="font-family:'DM Mono',monospace;font-size:10px;color:rgba(255,255,255,.35);letter-spacing:2px;text-transform:uppercase;margin-bottom:12px;">Listing Preview</div>
        <div id="llPrev"><div style="background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.1);border-radius:10px;padding:18px;font-size:13.5px;color:rgba(255,255,255,.4);text-align:center;">Fill in details to preview</div></div>
        <div style="margin-top:22px;padding:16px;background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.1);border-radius:10px;">
          <div style="font-size:11px;color:rgba(255,255,255,.3);font-family:'DM Mono',monospace;letter-spacing:1px;margin-bottom:8px;">POWERED BY</div>
          <div style="font-size:16px;font-weight:600;color:white;margin-bottom:5px;">TurboTenant</div>
          <div style="font-size:12.5px;color:rgba(255,255,255,.45);line-height:1.7;">Free for landlords. 40+ platforms. 15M+ renters.</div>
          <a href="https://turbotenant.com/r/T3duZXI6MTEwNjUwMg==" target="_blank" style="display:inline-block;margin-top:12px;background:var(--gold);color:white;padding:8px 16px;border-radius:6px;font-size:13px;font-weight:600;text-decoration:none;">Open TurboTenant →</a>
        </div>
      </div>
    </div>
    <div style="background:white;border:1px solid var(--rule);border-radius:14px;padding:24px;">
      <div style="font-family:'DM Mono',monospace;font-size:10px;color:var(--slate);letter-spacing:2px;text-transform:uppercase;margin-bottom:16px;">Syndication Network</div>
      <div style="display:flex;gap:8px;flex-wrap:wrap;">
        <span style="background:var(--mist);color:var(--navy);padding:5px 12px;border-radius:6px;font-size:13px;font-weight:500;">Apartments.com</span>
        <span style="background:var(--mist);color:var(--navy);padding:5px 12px;border-radius:6px;font-size:13px;font-weight:500;">Rent.com</span>
        <span style="background:var(--mist);color:var(--navy);padding:5px 12px;border-radius:6px;font-size:13px;font-weight:500;">Realtor.com</span>
        <span style="background:var(--mist);color:var(--navy);padding:5px 12px;border-radius:6px;font-size:13px;font-weight:500;">Redfin</span>
        <span style="background:var(--mist);color:var(--navy);padding:5px 12px;border-radius:6px;font-size:13px;font-weight:500;">Zillow</span>
        <span style="background:var(--mist);color:var(--navy);padding:5px 12px;border-radius:6px;font-size:13px;font-weight:500;">Homes.com</span>
        <span style="background:var(--mist);color:var(--navy);padding:5px 12px;border-radius:6px;font-size:13px;font-weight:500;">Zumper</span>
        <span style="background:var(--mist);color:var(--navy);padding:5px 12px;border-radius:6px;font-size:13px;font-weight:500;">ApartmentList</span>
        <span style="background:var(--mist);color:var(--slate);padding:5px 12px;border-radius:6px;font-size:13px;">+ 30 more</span>
      </div>
    </div>
  </div>
</div>

<!-- PROP MODAL -->
<div class="modal-bg" id="propModal">
  <div class="modal-box">
    <button class="modal-close" onclick="closeModal()">✕</button>
    <div class="modal-hero-bar">
      <div class="eyebrow" id="mCity">Active Listing</div>
      <h3 id="mAddr">Property</h3>
      <p id="mSub">Apply now</p>
    </div>
    <div class="modal-body">
      <div class="f-sec-lbl">Listing Data — Auto Cloned</div>
      <div class="clone-box">
        <div class="clone-lbl">Property Details</div>
        <div class="clone-row"><span class="ck">Address</span><span class="cv" id="mcAddr">—</span></div>
        <div class="clone-row"><span class="ck">Rent</span><span class="cv" id="mcRent">—</span></div>
        <div class="clone-row"><span class="ck">Deposit</span><span class="cv" id="mcDep">—</span></div>
        <div class="clone-row"><span class="ck">Lease</span><span class="cv" id="mcLease">—</span></div>
        <div class="clone-row"><span class="ck">Beds / Baths</span><span class="cv" id="mcBeds">—</span></div>
        <div class="clone-row"><span class="ck">TT Listing ID</span><span class="cv" id="mcTTID">—</span></div>
      </div>
      <div class="f-sec-lbl">Your Info (Optional)</div>
      <div class="f-row"><div class="f-grp"><label class="f-lbl">First Name</label><input class="f-inp" id="qF" placeholder="Angela"></div><div class="f-grp"><label class="f-lbl">Last Name</label><input class="f-inp" id="qL" placeholder="Wilson"></div></div>
      <div class="f-row"><div class="f-grp"><label class="f-lbl">Email</label><input class="f-inp" id="qE" type="email" placeholder="you@email.com"></div><div class="f-grp"><label class="f-lbl">Phone</label><input class="f-inp" id="qPh" placeholder="(815) 000-0000"></div></div>
    </div>
    <div class="modal-footer"><button class="sub-btn" style="margin:0;" onclick="goApplyFromModal()">Start Full Application →</button></div>
  </div>
</div>

<footer>
  <div class="ft-grid">
    <div>
      <div class="ft-brand">VIVIA<span>.</span></div>
      <div class="ft-tagline">Premium residential property management in Illinois and Texas, operated by AP Illinois Management LLC.</div>
      <div class="ft-contact">
        <div>📞 <a href="tel:8155923232">(815) 592-3232</a></div>
        <div>✉️ <a href="mailto:kristinbittnerproperties@viviaproperty.com">kristinbittnerproperties@viviaproperty.com</a></div>
        <div>✉️ <a href="mailto:ops@viviaproperty.com">ops@viviaproperty.com</a></div>
        <div>💚 Cash App: $VIVIARentals</div>
      </div>
    </div>
    <div><div class="ft-col-h">Renters</div><ul class="ft-links"><li><a href="#" onclick="showPage('listings')">Active Listings</a></li><li><a href="#" onclick="showPage('apply')">Apply Online</a></li><li><a href="https://vivia-rentals.fillout.com/apply-now" target="_blank">Fillout Form</a></li></ul></div>
    <div><div class="ft-col-h">Landlords</div><ul class="ft-links"><li><a href="#" onclick="showPage('landlord')">List Property</a></li><li><a href="https://turbotenant.com/r/T3duZXI6MTEwNjUwMg==" target="_blank">TurboTenant</a></li><li><a href="#" onclick="showPage('tracking')">Live Tracking</a></li></ul></div>
    <div><div class="ft-col-h">Company</div><ul class="ft-links"><li><a href="#">About VIVIA</a></li><li><a href="#">Fair Housing</a></li><li><a href="#">Privacy Policy</a></li></ul></div>
  </div>
  <div class="ft-btm"><div class="ft-legal">© 2026 VIVIA Rentals & Property Services · AP Illinois Management LLC</div><div class="ft-legal">Equal Housing Opportunity 🏠</div></div>
</footer>

<div class="toast" id="toast"><span id="toastMsg"></span></div>

<script>
const PROPS=[
  {id:'TT-2905',addr:'10115 S California Ave',city:'Chicago, IL',rent:2905,dep:2905,lease:'Rent to Own (33 mo)',beds:'3 bd / 2 ba',leads:28,apps:2,ttid:'2295589',emoji:'🏡',tags:['Rent to Own','Chicago']},
  {id:'TT-1300',addr:'7505 Emerson St',city:'Morton Grove, IL',rent:1300,dep:1300,lease:'12 Months',beds:'3 bd / 2 ba',leads:12,apps:1,ttid:'2511949',emoji:'🏠',tags:['12 Months','Morton Grove']},
  {id:'TT-1150',addr:'606 Cochise Cir',city:'Bolingbrook, IL',rent:1150,dep:1150,lease:'12 Months',beds:'3 bd / 1 ba',leads:7,apps:0,ttid:'2295591',emoji:'🏘',tags:['12 Months','Bolingbrook']},
  {id:'TT-1920',addr:'1920 Cherry Bark Ln',city:'Forney, TX',rent:1920,dep:1920,lease:'12 Months',beds:'4 bd / 2 ba',leads:8,apps:1,ttid:'2295590',emoji:'☀️',tags:['12 Months','Texas']},
];
const PAY={
  'Zelle':'Open bank app → Send with Zelle → Phone: <strong>(815) 592-3232</strong> → $75 → memo: name + property',
  'Cash App':'Open Cash App → Search <strong>$VIVIARentals</strong> → $75 → add name + property in note',
  'PayPal':'Go to <strong>paypal.me/viviarentals</strong> → $75 → "Sending to a friend" → add property in note',
  'Apple Pay':'Messages → text (815) 592-3232 → Apple Pay icon → $75 → include name + property',
  'Chime':'Chime → Pay Anyone → <strong>kristinbittnerproperties@viviaproperty.com</strong> → $75',
  'ACH':'Email <strong>ops@viviaproperty.com</strong> to receive Stripe ACH link. Include name and property.',
  'USDC':'Call <strong>(815) 592-3232</strong> for wallet address. Send $75 USDC. Include your name in memo.',
  'Store':'MoneyGram or Western Union → VIVIA Rentals → $75 → call (815) 592-3232 with confirmation #'
};
const ACTIVITY=[
  {ico:'🏠',bg:'#DBEAFE',title:'Sophia Anderson sent tour request — 7505 Emerson St',sub:'Via Apartments.com',time:'2h ago'},
  {ico:'📋',bg:'#DCFCE7',title:'Mercedaes Ellis application approved — $75 paid',sub:'Via Fillout · Jacksonville FL',time:'4h ago'},
  {ico:'🔔',bg:'#FEF3C7',title:'New lead: Shawn Jones — 7505 Emerson St',sub:'Asking about monthly pricing',time:'5h ago'},
  {ico:'✅',bg:'#DCFCE7',title:'Marketing activated — 1222 S 4th St Aurora IL',sub:'Live on 40+ platforms',time:'1d ago'},
  {ico:'💳',bg:'#EDE9FF',title:'Rent payment received — 10115 S California Ave',sub:'$2,905 via ACH',time:'2d ago'},
];

let selProp=null,idDone={front:false,back:false,selfie:false};

function showPage(id){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-tab').forEach(t=>t.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  const map={home:0,listings:1,apply:2,tracking:3,landlord:4};
  if(map[id]!==undefined) document.querySelectorAll('.nav-tab')[map[id]].classList.add('active');
  window.scrollTo(0,0);
  if(id==='listings') renderProps();
  if(id==='tracking') renderTracking();
  if(id==='apply') renderPropSel();
}
function toggleMobile(){document.getElementById('mobileNav').classList.toggle('open');}
function switchRole(t,btn){
  document.querySelectorAll('.role-btn').forEach(b=>b.classList.remove('active'));
  document.querySelectorAll('.info-card').forEach(c=>c.classList.remove('active'));
  btn.classList.add('active');
  document.getElementById('ic-'+t).classList.add('active');
}
function renderProps(){
  document.getElementById('propGrid').innerHTML=PROPS.map(p=>`
    <div class="prop-card" onclick="openModal('${p.id}')">
      <div class="prop-img">${p.emoji}</div>
      <div class="prop-body">
        <div class="prop-price">$${p.rent.toLocaleString()}<span>/mo</span></div>
        <div class="prop-addr">${p.addr}<br>${p.city}</div>
        <div class="prop-tags"><span class="tag tag-green">Live</span>${p.tags.map(t=>`<span class="tag tag-navy">${t}</span>`).join('')}</div>
        <button class="prop-btn">View Details & Apply</button>
      </div>
    </div>`).join('');
}
function openModal(id){
  const p=PROPS.find(x=>x.id===id);if(!p)return;
  selProp=p;
  document.getElementById('mCity').textContent=p.city;
  document.getElementById('mAddr').textContent=p.addr;
  document.getElementById('mSub').textContent=`${p.beds} · ${p.lease} · Available Now`;
  document.getElementById('mcAddr').textContent=`${p.addr}, ${p.city}`;
  document.getElementById('mcRent').textContent=`$${p.rent.toLocaleString()}/mo`;
  document.getElementById('mcDep').textContent=`$${p.dep.toLocaleString()}`;
  document.getElementById('mcLease').textContent=p.lease;
  document.getElementById('mcBeds').textContent=p.beds;
  document.getElementById('mcTTID').textContent=p.ttid;
  document.getElementById('propModal').classList.add('open');
  document.body.style.overflow='hidden';
}
function closeModal(){document.getElementById('propModal').classList.remove('open');document.body.style.overflow='';}
function goApplyFromModal(){closeModal();showPage('apply');if(selProp)setTimeout(()=>pickProp(selProp.id),100);}
function renderPropSel(){
  document.getElementById('propSel').innerHTML=`
    <div class="psel-hdr"><span>Choose a property</span><span style="font-family:'DM Mono',monospace;font-size:10px;color:var(--slate);">AUTO-FILLS FORM</span></div>
    ${PROPS.map(p=>`
    <div class="psel-opt" id="pso-${p.id}" onclick="pickProp('${p.id}')">
      <div class="p-radio"><div class="p-radio-in"></div></div>
      <div style="flex:1;"><div style="font-size:13.5px;font-weight:500;color:var(--navy);">${p.addr}, ${p.city}</div><div style="font-size:12px;color:var(--slate);">$${p.rent.toLocaleString()}/mo · ${p.lease} · ${p.beds}</div></div>
      <span style="font-family:'DM Mono',monospace;font-size:10px;background:var(--mist);color:var(--navy);padding:2px 7px;border-radius:4px;">${p.id}</span>
    </div>`).join('')}`;
}
function pickProp(id){
  document.querySelectorAll('.psel-opt').forEach(o=>o.classList.remove('sel'));
  const opt=document.getElementById('pso-'+id);if(opt)opt.classList.add('sel');
  const p=PROPS.find(x=>x.id===id);if(!p)return;
  selProp=p;
  document.getElementById('cpAddr').textContent=`${p.addr}, ${p.city}`;
  document.getElementById('cpRent').textContent=`$${p.rent.toLocaleString()}/mo`;
  document.getElementById('cpDep').textContent=`$${p.dep.toLocaleString()}`;
  document.getElementById('cpLease').textContent=p.lease;
  document.getElementById('cpTTID').textContent=p.ttid;
  document.getElementById('clonePreview').style.display='block';
}
function nextApply(n){
  if(n===2&&!selProp){showToast('⚠️ Please select a property.');return;}
  document.querySelectorAll('.a-panel').forEach(p=>p.classList.remove('active'));
  document.getElementById('ap'+n).classList.add('active');
  const steps=document.querySelectorAll('.a-step');
  steps.forEach((s,i)=>{s.classList.remove('cur','done');if(i+1<n)s.classList.add('done');if(i+1===n)s.classList.add('cur');});
  if(n===5)buildReview();
  window.scrollTo(0,64);
}
function handleID(type,input){
  const f=input.files[0];if(!f)return;
  const map={front:{n:'idFN',s:'idFS',p:'idFPrev',next:'idBackZone',s1:'ids1',s2:'ids2'},
             back:{n:'idBN',s:'idBS',p:'idBPrev',next:'idSelfieZone',s1:'ids2',s2:'ids3'},
             selfie:{n:'idSN',s:'idSS',p:'idSPrev',next:null,s1:'ids3',s2:'ids4'}};
  const m=map[type];
  document.getElementById(m.n).textContent=f.name;
  document.getElementById(m.s).textContent=(f.size/1024/1024).toFixed(2)+' MB';
  document.getElementById(m.p).classList.add('show');
  idDone[type]=true;
  document.getElementById(m.s1).classList.remove('cur');document.getElementById(m.s1).classList.add('done');
  document.getElementById(m.s2).classList.add('cur');
  if(m.next)document.getElementById(m.next).style.display='block';
  if(type==='selfie'){
    document.getElementById('idVerified').classList.add('show');
    const btn=document.getElementById('idNext');btn.removeAttribute('disabled');btn.style.opacity='1';btn.style.cursor='pointer';
    showToast('✅ All ID documents uploaded!');
  }
}
function choosePay(el,m){
  document.querySelectorAll('.pay-m').forEach(x=>x.classList.remove('sel'));el.classList.add('sel');
  const d=document.getElementById('payInstr');d.classList.add('show');
  document.getElementById('payText').innerHTML=PAY[m]||'Contact us for instructions.';
}
function buildReview(){
  const p=selProp;
  document.getElementById('reviewBox').innerHTML=`
    <div class="clone-box"><div class="clone-lbl">Property</div>
    <div class="clone-row"><span class="ck">Address</span><span class="cv">${p?p.addr+', '+p.city:'—'}</span></div>
    <div class="clone-row"><span class="ck">Rent</span><span class="cv">${p?'$'+p.rent.toLocaleString()+'/mo':'—'}</span></div>
    <div class="clone-row"><span class="ck">Lease</span><span class="cv">${p?p.lease:'—'}</span></div></div>
    <div class="clone-box" style="margin-top:12px;"><div class="clone-lbl">Applicant</div>
    <div class="clone-row"><span class="ck">Name</span><span class="cv">${(document.getElementById('aFirst').value||'—')+' '+(document.getElementById('aLast').value||'')}</span></div>
    <div class="clone-row"><span class="ck">Email</span><span class="cv">${document.getElementById('aEmail').value||'—'}</span></div>
    <div class="clone-row"><span class="ck">Phone</span><span class="cv">${document.getElementById('aPhone').value||'—'}</span></div>
    <div class="clone-row"><span class="ck">Move-In</span><span class="cv">${document.getElementById('aMoveIn').value||'—'}</span></div>
    <div class="clone-row"><span class="ck">ID Verified</span><span class="cv" style="color:${idDone.front&&idDone.selfie?'#166534':'#DC2626'}">${idDone.front&&idDone.selfie?'✓ Uploaded':'⚠ Missing'}</span></div></div>`;
}
function submitApp(){showToast('🎉 Application submitted! We\'ll contact you within 48 hours.');setTimeout(()=>showPage('home'),2500);}
function renderTracking(){
  document.getElementById('trackBody').innerHTML=PROPS.map(p=>`
    <tr>
      <td><strong style="color:var(--navy);">${p.addr}</strong><br><span class="mono">${p.city}</span></td>
      <td><strong>$${p.rent.toLocaleString()}</strong><span class="mono">/mo</span></td>
      <td><span class="pill pill-live"><span class="pdot"></span>Live</span></td>
      <td><strong>${p.leads}</strong></td>
      <td>${p.apps>0?`<span class="pill pill-rev"><span class="pdot"></span>${p.apps} pending</span>`:'<span style="color:#aaa;font-size:12px;">None</span>'}</td>
      <td><span class="mono">TurboTenant</span></td>
      <td><span class="mono">${p.ttid}</span></td>
      <td><button class="act-link" onclick="openModal('${p.id}')">View →</button></td>
    </tr>`).join('');
  document.getElementById('actFeed').innerHTML=ACTIVITY.map(a=>`
    <div class="feed-item">
      <div class="feed-dot" style="background:${a.bg};">${a.ico}</div>
      <div style="flex:1;"><div class="feed-title">${a.title}</div><div class="feed-sub">${a.sub}</div></div>
      <div class="feed-time">${a.time}</div>
    </div>`).join('');
}
function refreshKPI(){
  const k=document.getElementById('kLeads');k.textContent=parseInt(k.textContent)+1;
  showToast('↻ Data refreshed');
}
function llPreview(){
  const a=document.getElementById('llA').value,r=document.getElementById('llR').value;
  if(!a&&!r)return;
  document.getElementById('llPrev').innerHTML=`
    <div style="background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.12);border-radius:10px;padding:16px;">
      <div style="font-family:'Fraunces',serif;font-size:22px;color:white;margin-bottom:5px;">${r||'$—'}<span style="font-size:13px;font-weight:400;color:rgba(255,255,255,.4);">/mo</span></div>
      <div style="font-size:13px;color:rgba(255,255,255,.65);">${a||'Enter address above'}</div>
      <div style="margin-top:12px;font-size:11px;background:rgba(22,163,74,.15);color:#6EE7B7;padding:4px 10px;border-radius:4px;display:inline-block;">Ready to list on TurboTenant</div>
    </div>`;
}
function submitLL(){
  const n=document.getElementById('llN').value.trim(),e=document.getElementById('llE').value.trim(),a=document.getElementById('llA').value.trim();
  if(!n||!e||!a){showToast('⚠️ Name, email and address required.');return;}
  showToast('🏠 Property submitted! We\'ll contact you within 1 business day.');
  ['llN','llE','llP','llA','llR','llB'].forEach(id=>{const el=document.getElementById(id);if(el)el.value='';});
}
function showToast(msg){const t=document.getElementById('toast');document.getElementById('toastMsg').textContent=msg;t.classList.add('show');setTimeout(()=>t.classList.remove('show'),3800);}

document.addEventListener('DOMContentLoaded',()=>{renderProps();renderTracking();renderPropSel();});
document.getElementById('propModal').addEventListener('click',e=>{if(e.target===document.getElementById('propModal'))closeModal();});
window.addEventListener('scroll',()=>{document.getElementById('mainNav').style.boxShadow=window.scrollY>10?'0 2px 20px rgba(0,0,0,.07)':'none';});
</script>
</body>
</html>
HTMLEOF
echo "Done"
