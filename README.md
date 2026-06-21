<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Dashboard — Optimización Farmacia</title>
<style>
/* ─── TOKENS ─── */
:root {
  --navy:       #0F2440;
  --blue:       #1B4F8A;
  --blue-mid:   #2563AB;
  --blue-light: #EBF2FC;
  --cyan:       #0EA5E9;
  --green:      #059669;
  --green-mid:  #10B981;
  --green-light:#D1FAE5;
  --red:        #DC2626;
  --red-light:  #FEE2E2;
  --orange:     #EA580C;
  --orange-light:#FFF0E6;
  --amber:      #D97706;
  --amber-light:#FEF3C7;
  --purple:     #7C3AED;
  --purple-light:#EDE9FE;
  --grey-50:    #F8FAFC;
  --grey-100:   #F1F5F9;
  --grey-200:   #E2E8F0;
  --grey-400:   #94A3B8;
  --grey-600:   #475569;
  --grey-800:   #1E293B;
  --white:      #FFFFFF;
  --shadow-sm:  0 1px 3px rgba(0,0,0,.08), 0 1px 2px rgba(0,0,0,.05);
  --shadow:     0 4px 16px rgba(15,36,64,.10);
  --shadow-lg:  0 10px 32px rgba(15,36,64,.14);
  --r:          12px;
  --r-sm:       8px;
  --font:       'Segoe UI', system-ui, -apple-system, sans-serif;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:var(--font);background:var(--grey-100);color:var(--grey-800);font-size:14px;line-height:1.6}

/* ─── SIDEBAR NAV ─── */
.layout{display:flex;min-height:100vh}
.sidebar{
  width:220px;flex-shrink:0;
  background:var(--navy);
  display:flex;flex-direction:column;
  position:sticky;top:0;height:100vh;overflow-y:auto;
}
.sidebar-logo{
  padding:28px 20px 20px;
  border-bottom:1px solid rgba(255,255,255,.08);
}
.sidebar-logo .logo-icon{
  width:36px;height:36px;border-radius:10px;
  background:linear-gradient(135deg,var(--blue-mid),var(--cyan));
  display:flex;align-items:center;justify-content:center;
  font-size:18px;margin-bottom:10px;
}
.sidebar-logo .logo-name{color:#fff;font-weight:700;font-size:14px;line-height:1.3}
.sidebar-logo .logo-sub{color:rgba(255,255,255,.4);font-size:11px;margin-top:2px}
.sidebar-nav{padding:16px 12px;flex:1}
.nav-group{margin-bottom:24px}
.nav-group-label{
  color:rgba(255,255,255,.35);font-size:10px;font-weight:700;
  letter-spacing:.12em;text-transform:uppercase;padding:0 8px;margin-bottom:8px;
}
.nav-item{
  display:flex;align-items:center;gap:10px;
  padding:9px 10px;border-radius:8px;
  color:rgba(255,255,255,.6);font-size:13px;font-weight:500;
  cursor:pointer;transition:all .2s;text-decoration:none;
  margin-bottom:2px;
}
.nav-item:hover{background:rgba(255,255,255,.08);color:#fff}
.nav-item.active{background:var(--blue-mid);color:#fff;font-weight:600}
.nav-dot{
  width:7px;height:7px;border-radius:50%;flex-shrink:0;
}
.sidebar-footer{
  padding:16px;border-top:1px solid rgba(255,255,255,.08);
  color:rgba(255,255,255,.3);font-size:11px;
}

/* ─── MAIN ─── */
.main{flex:1;overflow:hidden;min-width:0}

/* ─── TOPBAR ─── */
.topbar{
  background:var(--white);border-bottom:1px solid var(--grey-200);
  padding:0 32px;height:60px;display:flex;align-items:center;
  justify-content:space-between;position:sticky;top:0;z-index:10;
}
.topbar-title{font-size:15px;font-weight:700;color:var(--grey-800)}
.topbar-sub{font-size:12px;color:var(--grey-400);margin-top:1px}
.topbar-badges{display:flex;gap:8px}
.tbadge{
  padding:4px 12px;border-radius:20px;font-size:11px;font-weight:700;
  letter-spacing:.04em;
}
.tbadge.blue{background:var(--blue-light);color:var(--blue)}
.tbadge.green{background:var(--green-light);color:var(--green)}
.tbadge.purple{background:var(--purple-light);color:var(--purple)}

/* ─── CONTENT ─── */
.content{padding:28px 32px;max-width:1100px}

/* ─── SECTION HEADER ─── */
.section-hd{
  display:flex;align-items:center;gap:14px;margin-bottom:22px;padding-bottom:16px;
  border-bottom:2px solid var(--grey-200);
}
.section-num{
  width:36px;height:36px;border-radius:10px;
  display:flex;align-items:center;justify-content:center;
  font-size:14px;font-weight:800;color:#fff;flex-shrink:0;
}
.section-num.blue{background:linear-gradient(135deg,var(--blue),var(--blue-mid))}
.section-num.green{background:linear-gradient(135deg,var(--green),var(--green-mid))}
.section-num.orange{background:linear-gradient(135deg,var(--orange),var(--amber))}
.section-num.purple{background:linear-gradient(135deg,var(--purple),#A78BFA)}
.section-hd-text h2{font-size:17px;font-weight:700;color:var(--grey-800);line-height:1.2}
.section-hd-text p{font-size:12.5px;color:var(--grey-400);margin-top:2px}
.section-block{margin-bottom:48px}

/* ─── CARD ─── */
.card{
  background:var(--white);border-radius:var(--r);
  box-shadow:var(--shadow-sm);border:1px solid var(--grey-200);
  margin-bottom:18px;
}
.card-hd{
  padding:16px 20px 0;display:flex;align-items:center;justify-content:space-between;
}
.card-title{font-size:12px;font-weight:700;text-transform:uppercase;letter-spacing:.08em;color:var(--grey-400)}
.card-body{padding:16px 20px 20px}

/* ─── STATS ROW ─── */
.stats-row{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-bottom:18px}
.stats-row-3{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin-bottom:18px}
.stat-card{
  background:var(--white);border-radius:var(--r);
  border:1px solid var(--grey-200);box-shadow:var(--shadow-sm);
  padding:18px 20px;
}
.stat-label{font-size:11px;color:var(--grey-400);font-weight:600;text-transform:uppercase;letter-spacing:.07em;margin-bottom:6px}
.stat-value{font-size:28px;font-weight:800;line-height:1;margin-bottom:4px}
.stat-sub{font-size:11.5px;color:var(--grey-400)}
.stat-badge{
  display:inline-flex;align-items:center;gap:4px;
  padding:2px 8px;border-radius:12px;font-size:11px;font-weight:700;margin-top:6px;
}
.stat-badge.red{background:var(--red-light);color:var(--red)}
.stat-badge.green{background:var(--green-light);color:var(--green)}
.stat-badge.blue{background:var(--blue-light);color:var(--blue)}
.stat-badge.purple{background:var(--purple-light);color:var(--purple)}

/* ─── TABLE ─── */
.tbl-wrap{overflow-x:auto;border-radius:var(--r-sm)}
table{width:100%;border-collapse:collapse;font-size:13.5px}
thead tr{background:var(--grey-800)}
th{
  padding:10px 16px;color:#fff;font-size:11px;font-weight:700;
  text-transform:uppercase;letter-spacing:.07em;text-align:left;
}
th:first-child{border-radius:8px 0 0 0}th:last-child{border-radius:0 8px 0 0}
td{padding:11px 16px;border-bottom:1px solid var(--grey-200);vertical-align:middle}
tbody tr:last-child td{border-bottom:none}
tbody tr:hover td{background:var(--grey-50)}
.tr-total td{background:var(--grey-800)!important;color:#fff;font-weight:700}
.tr-total-green td{background:var(--green)!important;color:#fff;font-weight:700}
.tr-total-purple td{background:var(--purple)!important;color:#fff;font-weight:700}

/* badges */
.badge{display:inline-flex;align-items:center;gap:4px;padding:3px 10px;border-radius:20px;font-size:12px;font-weight:700}
.badge.blue{background:var(--blue-light);color:var(--blue-mid)}
.badge.red{background:var(--red-light);color:var(--red)}
.badge.green{background:var(--green-light);color:var(--green)}
.badge.orange{background:var(--orange-light);color:var(--orange)}
.badge.dark{background:var(--grey-800);color:#fff}
.badge.purple{background:var(--purple-light);color:var(--purple)}

/* ─── ALERT ROW ─── */
.alert-row{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin-bottom:16px}
.alert-card{
  border-radius:var(--r);padding:18px 18px 16px;
  background:var(--white);border:1px solid var(--orange-light);
  border-top:3px solid var(--orange);box-shadow:var(--shadow-sm);
}
.ac-num{font-size:32px;font-weight:900;color:var(--orange);line-height:1;margin-bottom:4px}
.ac-unit{font-size:13px;color:var(--grey-400);font-weight:500}
.ac-label{font-weight:700;font-size:13.5px;color:var(--grey-800);margin-bottom:4px}
.ac-reason{font-size:12px;color:var(--grey-400)}

.warn-strip{
  background:var(--amber-light);border:1px solid #FDE68A;border-radius:var(--r-sm);
  padding:13px 16px;font-size:13px;color:#92400E;display:flex;align-items:center;gap:10px;
}
.warn-strip strong{color:#78350F}

/* ─── DIAGNOSIS ─── */
.diag-row{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}
.diag-item{
  background:var(--blue-light);border:1px solid #BFDBFE;
  border-radius:var(--r);padding:16px 18px;
}
.diag-icon{font-size:22px;margin-bottom:8px}
.diag-title{font-weight:700;font-size:13px;color:var(--blue);margin-bottom:4px}
.diag-text{font-size:12.5px;color:var(--blue-mid)}

/* ─── ROLE CARD ─── */
.role-banner{
  background:linear-gradient(135deg,var(--navy) 0%,var(--blue) 100%);
  border-radius:var(--r);padding:24px 28px;color:#fff;
  display:grid;grid-template-columns:1fr auto;gap:20px;align-items:center;
  margin-bottom:18px;
}
.role-banner h3{font-size:17px;font-weight:800;margin-bottom:6px}
.role-banner p{font-size:13px;opacity:.75;margin-bottom:14px}
.func-chips{display:flex;flex-wrap:wrap;gap:8px}
.func-chip{
  background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.2);
  border-radius:20px;padding:5px 13px;font-size:12px;font-weight:600;
}
.role-badge-big{
  background:rgba(255,255,255,.1);border:2px solid rgba(255,255,255,.2);
  border-radius:50%;width:90px;height:90px;display:flex;
  align-items:center;justify-content:center;font-size:38px;flex-shrink:0;
}

/* ─── BENEFITS GRID ─── */
.benefits-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin-bottom:18px}
.benefit-card{
  background:var(--white);border:1px solid var(--grey-200);border-radius:var(--r);
  padding:18px;box-shadow:var(--shadow-sm);transition:all .2s;
  border-bottom:3px solid var(--green);
}
.benefit-card:hover{transform:translateY(-2px);box-shadow:var(--shadow)}
.benefit-icon{font-size:26px;margin-bottom:8px}
.benefit-title{font-size:13px;font-weight:700;color:var(--grey-800)}

/* ─── SIMULATOR ─── */
.sim-layout{display:grid;grid-template-columns:1fr 380px;gap:18px;align-items:start}
.sim-card{background:var(--white);border:1px solid var(--grey-200);border-radius:var(--r);box-shadow:var(--shadow-sm)}
.sim-card .card-body{padding:18px 20px}

input[type=range]{
  -webkit-appearance:none;appearance:none;
  width:90px;height:5px;background:var(--grey-200);border-radius:3px;outline:none;cursor:pointer;
}
input[type=range]::-webkit-slider-thumb{
  -webkit-appearance:none;width:16px;height:16px;
  background:var(--green);border-radius:50%;cursor:pointer;
  box-shadow:0 0 0 3px rgba(5,150,105,.15);transition:.2s;
}
input[type=range]:hover::-webkit-slider-thumb{box-shadow:0 0 0 6px rgba(5,150,105,.2)}
.slider-cell{display:flex;align-items:center;gap:8px}
.sv{font-weight:800;font-size:15px;color:var(--green);min-width:24px;text-align:center}

/* ─── BAR CHART (horizontal grouped) ─── */
.barchart-card{
  background:var(--white);border:1px solid var(--grey-200);border-radius:var(--r);
  box-shadow:var(--shadow-sm);padding:20px;
}
.barchart-title{font-size:12px;font-weight:700;color:var(--grey-400);text-transform:uppercase;letter-spacing:.07em;margin-bottom:18px}
.bar-group{margin-bottom:18px}
.bar-label{font-size:12px;font-weight:600;color:var(--grey-600);margin-bottom:6px;display:flex;justify-content:space-between}
.bar-track{background:var(--grey-100);border-radius:6px;height:28px;overflow:hidden;position:relative}
.bar-fill{
  height:100%;border-radius:6px;display:flex;align-items:center;
  padding:0 10px;font-size:12px;font-weight:700;color:#fff;
  transition:width .5s cubic-bezier(.4,0,.2,1);white-space:nowrap;
}
.bar-fill.navy{background:linear-gradient(90deg,var(--navy),var(--blue-mid))}
.bar-fill.green{background:linear-gradient(90deg,var(--green),var(--green-mid))}
.bar-fill.purple{background:linear-gradient(90deg,var(--purple),#A78BFA)}
.bar-scale{display:flex;justify-content:space-between;margin-top:6px}
.bar-scale span{font-size:10px;color:var(--grey-400)}

/* activity bars (breakdown) */
.breakdown{margin-top:16px}
.breakdown-title{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.08em;color:var(--grey-400);margin-bottom:10px}
.act-bar-row{display:flex;align-items:center;gap:10px;margin-bottom:8px}
.act-name{font-size:11.5px;color:var(--grey-600);min-width:130px;text-align:right;flex-shrink:0}
.act-track{flex:1;background:var(--grey-100);border-radius:4px;height:18px;overflow:hidden}
.act-fill{height:100%;border-radius:4px;display:flex;align-items:center;padding-left:7px;font-size:10px;font-weight:700;color:#fff}
.act-val{font-size:11px;font-weight:700;min-width:28px;color:var(--grey-600)}

/* ─── KPI SECTION ─── */
.kpi-compare{display:grid;grid-template-columns:1fr 1fr;gap:18px}
.kpi-panel{
  background:var(--white);border:1px solid var(--grey-200);
  border-radius:var(--r);box-shadow:var(--shadow-sm);overflow:hidden;
}
.kpi-panel-hd{
  padding:14px 20px;display:flex;align-items:center;gap:10px;
}
.kpi-panel-hd.blue{background:var(--blue);color:#fff}
.kpi-panel-hd.green{background:var(--green);color:#fff}
.kpi-panel-hd h3{font-size:13px;font-weight:700}
.kpi-panel-hd p{font-size:11px;opacity:.75;margin-top:1px}
.kpi-panel-body{padding:16px 20px 20px}

/* donut + kpi inline */
.donut-kpi-layout{display:flex;gap:16px;align-items:center}
.donut-side{flex-shrink:0}
.kpi-stack{flex:1;display:flex;flex-direction:column;gap:10px}

.kpi-row{background:var(--grey-50);border-radius:var(--r-sm);padding:12px 14px;border:1px solid var(--grey-200)}
.kpi-row.highlight{background:var(--green-light);border-color:#A7F3D0}
.kpi-row.highlight-purple{background:var(--purple-light);border-color:#C4B5FD}
.kpi-lbl{font-size:10.5px;font-weight:700;text-transform:uppercase;letter-spacing:.07em;color:var(--grey-400);margin-bottom:3px}
.kpi-val{font-size:26px;font-weight:900;line-height:1;transition:all .4s cubic-bezier(.4,0,.2,1)}
.kpi-val.blue{color:var(--blue-mid)}
.kpi-val.red{color:var(--red)}
.kpi-val.green{color:var(--green)}
.kpi-val.big{font-size:34px;color:var(--green)}
.kpi-val.purple{font-size:34px;color:var(--purple)}
.kpi-note{font-size:11px;color:var(--grey-400);margin-top:3px}

/* donut legend */
.d-legend{margin-top:10px;display:flex;flex-direction:column;gap:5px}
.d-leg-item{display:flex;align-items:center;gap:7px;font-size:11.5px;color:var(--grey-600)}
.d-leg-dot{width:9px;height:9px;border-radius:50%;flex-shrink:0}

/* ─── LEAN TABLE ─── */
.lean-intro{
  background:linear-gradient(135deg,var(--blue-light),#EDE9FE);
  border:1px solid #C7D2FE;border-radius:var(--r);
  padding:18px 20px;margin-bottom:18px;font-size:13.5px;color:#1E3A5F;line-height:1.7;
}
.lean-intro strong{color:var(--blue)}

/* ─── CLIENTS CAPACITY SECTION ─── */
.capacity-banner{
  background:linear-gradient(135deg,#4C1D95 0%,var(--purple) 50%,#A78BFA 100%);
  border-radius:var(--r);padding:22px 28px;color:#fff;margin-bottom:18px;
  display:flex;align-items:center;justify-content:space-between;gap:20px;
}
.capacity-banner-text h3{font-size:16px;font-weight:800;margin-bottom:6px}
.capacity-banner-text p{font-size:12.5px;opacity:.8;line-height:1.6}
.capacity-formula{
  background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.2);
  border-radius:10px;padding:14px 20px;text-align:center;flex-shrink:0;
  font-size:12px;min-width:220px;
}
.capacity-formula .formula-eq{font-size:15px;font-weight:800;margin-top:6px;opacity:.95}

.clients-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:14px;margin-bottom:18px}
.client-stat{
  background:var(--white);border-radius:var(--r);border:1px solid var(--grey-200);
  box-shadow:var(--shadow-sm);padding:20px;text-align:center;
  position:relative;overflow:hidden;
}
.client-stat::before{
  content:'';position:absolute;top:0;left:0;right:0;height:4px;
}
.client-stat.actual::before{background:var(--blue)}
.client-stat.mejorado::before{background:var(--green)}
.client-stat.incremento::before{background:var(--purple)}
.client-stat-icon{font-size:28px;margin-bottom:8px}
.client-stat-label{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.07em;color:var(--grey-400);margin-bottom:6px}
.client-stat-value{font-size:40px;font-weight:900;line-height:1;margin-bottom:4px;transition:all .4s cubic-bezier(.4,0,.2,1)}
.client-stat-value.blue{color:var(--blue)}
.client-stat-value.green{color:var(--green)}
.client-stat-value.purple{color:var(--purple)}
.client-stat-sub{font-size:12px;color:var(--grey-400)}

/* ─── CLIENTS CHART ─── */
.clients-chart-layout{display:grid;grid-template-columns:1fr 1fr;gap:18px;margin-bottom:18px}
.clients-chart-card{
  background:var(--white);border:1px solid var(--grey-200);border-radius:var(--r);
  box-shadow:var(--shadow-sm);padding:20px;
}
.clients-chart-title{font-size:12px;font-weight:700;color:var(--grey-400);text-transform:uppercase;letter-spacing:.07em;margin-bottom:16px}

/* Column chart */
.col-chart{display:flex;align-items:flex-end;justify-content:center;gap:24px;height:180px;padding-bottom:4px}
.col-group{display:flex;flex-direction:column;align-items:center;gap:6px;flex:1;max-width:100px}
.col-bar-wrap{flex:1;display:flex;align-items:flex-end;width:100%}
.col-bar{
  width:100%;border-radius:6px 6px 0 0;
  display:flex;align-items:flex-start;justify-content:center;
  padding-top:8px;font-size:13px;font-weight:800;color:#fff;
  transition:height .6s cubic-bezier(.4,0,.2,1);min-height:10px;
}
.col-bar.blue{background:linear-gradient(180deg,var(--blue-mid),var(--navy))}
.col-bar.green{background:linear-gradient(180deg,var(--green-mid),var(--green))}
.col-label{font-size:11px;font-weight:600;color:var(--grey-600);text-align:center}
.col-sublabel{font-size:10px;color:var(--grey-400);text-align:center}

/* People dots chart */
.people-chart{padding:4px 0}
.people-row{display:flex;align-items:center;gap:10px;margin-bottom:12px}
.people-row-label{font-size:12px;font-weight:600;color:var(--grey-600);min-width:70px}
.people-dots{display:flex;flex-wrap:wrap;gap:4px;flex:1}
.person-dot{
  width:16px;height:16px;border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  font-size:9px;transition:all .4s;
}
.person-dot.actual{background:var(--blue);opacity:.9}
.person-dot.extra{background:var(--green);opacity:.9}
.person-dot.placeholder{background:var(--grey-200);opacity:.5}
.people-row-count{font-size:20px;font-weight:900;min-width:36px;text-align:right}
.people-row-count.blue{color:var(--blue)}
.people-row-count.green{color:var(--green)}

.people-legend{display:flex;gap:16px;margin-top:12px;padding-top:12px;border-top:1px solid var(--grey-200)}
.pleg{display:flex;align-items:center;gap:6px;font-size:11.5px;color:var(--grey-600)}
.pleg-dot{width:10px;height:10px;border-radius:50%}

/* capacity gain strip */
.gain-strip{
  background:linear-gradient(135deg,var(--purple-light),var(--green-light));
  border:1px solid #C4B5FD;border-radius:var(--r);
  padding:16px 20px;display:flex;align-items:center;justify-content:space-between;
  gap:16px;margin-bottom:18px;
}
.gain-strip-text{font-size:13.5px;color:#3B0764;line-height:1.6}
.gain-strip-text strong{color:var(--purple)}
.gain-big{font-size:36px;font-weight:900;color:var(--purple);flex-shrink:0;line-height:1;transition:all .4s}

/* ─── CONCLUSION ─── */
.conclusion{
  background:linear-gradient(135deg,var(--navy),var(--blue));
  border-radius:var(--r);padding:24px 28px;color:#fff;margin-top:18px;
}
.conclusion h3{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.12em;opacity:.5;margin-bottom:10px}
.conclusion p{font-size:15px;line-height:1.8;opacity:.92;transition:all .4s}

/* ─── RESPONSIVE ─── */
@media(max-width:900px){
  .sidebar{display:none}
  .stats-row{grid-template-columns:repeat(2,1fr)}
  .stats-row-3{grid-template-columns:repeat(2,1fr)}
  .sim-layout{grid-template-columns:1fr}
  .kpi-compare{grid-template-columns:1fr}
  .alert-row{grid-template-columns:1fr}
  .diag-row{grid-template-columns:1fr}
  .benefits-grid{grid-template-columns:repeat(2,1fr)}
  .donut-kpi-layout{flex-direction:column}
  .role-banner{grid-template-columns:1fr}
  .role-badge-big{display:none}
  .clients-grid{grid-template-columns:1fr 1fr}
  .clients-chart-layout{grid-template-columns:1fr}
  .capacity-banner{flex-direction:column}
  .capacity-formula{width:100%}
  .gain-strip{flex-direction:column;text-align:center}
}
@media(max-width:600px){
  .content{padding:18px 16px}
  .topbar{padding:0 16px}
  .stats-row{grid-template-columns:1fr 1fr}
  .stats-row-3{grid-template-columns:1fr}
  .benefits-grid{grid-template-columns:1fr 1fr}
  .clients-grid{grid-template-columns:1fr}
}
</style>
</head>
<body>
<div class="layout">

<!-- ── SIDEBAR ── -->
<aside class="sidebar">
  <div class="sidebar-logo">
    <div class="logo-icon">💊</div>
    <div class="logo-name">FarmaCuenca</div>
    <div class="logo-sub">Panel de Optimización</div>
  </div>
  <nav class="sidebar-nav">
    <div class="nav-group">
      <div class="nav-group-label">Diagnóstico</div>
      <a class="nav-item active" href="#part1">
        <div class="nav-dot" style="background:#60A5FA"></div>Proceso Actual
      </a>
    </div>
    <div class="nav-group">
      <div class="nav-group-label">Mejora</div>
      <a class="nav-item" href="#part2">
        <div class="nav-dot" style="background:#34D399"></div>Reorganización
      </a>
      <a class="nav-item" href="#sim">
        <div class="nav-dot" style="background:#34D399"></div>Simulador
      </a>
    </div>
    <div class="nav-group">
      <div class="nav-group-label">Capacidad</div>
      <a class="nav-item" href="#part-capacity">
        <div class="nav-dot" style="background:#A78BFA"></div>Clientes / Día
      </a>
    </div>
    <div class="nav-group">
      <div class="nav-group-label">Lean</div>
      <a class="nav-item" href="#part3">
        <div class="nav-dot" style="background:#FB923C"></div>KPIs e Impacto
      </a>
    </div>
  </nav>
  <div class="sidebar-footer">Farmacia · Análisis Lean 2024</div>
</aside>

<!-- ── MAIN ── -->
<div class="main">

  <!-- topbar -->
  <div class="topbar">
    <div>
      <div class="topbar-title">Dashboard de Optimización de Procesos</div>
      <div class="topbar-sub">Diagnóstico · Reorganización · Capacidad · Impacto Lean</div>
    </div>
    <div class="topbar-badges">
      <span class="tbadge blue">Actual: 20 min · 40 clientes/día</span>
      <span class="tbadge green">Mejorado: <span id="tb-total">12</span> min · <span id="tb-clients">67</span> clientes/día</span>
    </div>
  </div>

  <div class="content">

<!-- ════════════════════════════════════════════
     PARTE 1 — DIAGNÓSTICO
════════════════════════════════════════════ -->
<div class="section-block" id="part1">
  <div class="section-hd">
    <div class="section-num blue">1</div>
    <div class="section-hd-text">
      <h2>Diagnóstico del Proceso Actual</h2>
      <p>Análisis del flujo de atención con dos empleados independientes sin supervisión integral</p>
    </div>
  </div>

  <div class="stats-row">
    <div class="stat-card">
      <div class="stat-label">Tiempo Total</div>
      <div class="stat-value" style="color:var(--blue)">20<span style="font-size:16px;color:var(--grey-400)"> min</span></div>
      <div class="stat-sub">Proceso sin optimizar</div>
      <span class="stat-badge blue">Estado actual</span>
    </div>
    <div class="stat-card">
      <div class="stat-label">Clientes / Día</div>
      <div class="stat-value" style="color:var(--blue)">40</div>
      <div class="stat-sub">Dato real observado (8 h)</div>
      <span class="stat-badge blue">Base real</span>
    </div>
    <div class="stat-card">
      <div class="stat-label">Tiempo en Esperas</div>
      <div class="stat-value" style="color:var(--red)">15<span style="font-size:16px;color:var(--grey-400)"> min</span></div>
      <div class="stat-sub">Del total del proceso</div>
      <span class="stat-badge red">75% del tiempo</span>
    </div>
    <div class="stat-card">
      <div class="stat-label">Valor Real Entregado</div>
      <div class="stat-value" style="color:var(--green)">5<span style="font-size:16px;color:var(--grey-400)"> min</span></div>
      <div class="stat-sub">Tiempo que agrega valor</div>
      <span class="stat-badge green">Solo 25%</span>
    </div>
  </div>

  <div style="display:grid;grid-template-columns:1fr 340px;gap:18px;margin-bottom:18px">
    <div class="card" style="margin-bottom:0">
      <div class="card-hd"><div class="card-title">¿Cómo funciona ahora?</div></div>
      <div class="card-body" style="padding-top:12px">
        <div class="tbl-wrap">
          <table>
            <thead><tr><th>#</th><th>Actividad</th><th>Responsable</th><th>Tiempo</th><th>Estado</th></tr></thead>
            <tbody>
              <tr><td style="color:var(--grey-400);font-weight:700">01</td><td>Recepción y solicitud</td><td style="color:var(--grey-400)">Empleado A</td><td><span class="badge blue">2 min</span></td><td><span class="badge green">✓ Valor</span></td></tr>
              <tr><td style="color:var(--grey-400);font-weight:700">02</td><td>Verificación de disponibilidad</td><td style="color:var(--grey-400)">Empleado A</td><td><span class="badge orange">4 min</span></td><td><span class="badge red">⚠ Espera</span></td></tr>
              <tr><td style="color:var(--grey-400);font-weight:700">03</td><td>Búsqueda del medicamento</td><td style="color:var(--grey-400)">Empleado B</td><td><span class="badge red">7 min</span></td><td><span class="badge red">⚠ Espera</span></td></tr>
              <tr><td style="color:var(--grey-400);font-weight:700">04</td><td>Registro de la venta</td><td style="color:var(--grey-400)">Empleado B</td><td><span class="badge orange">4 min</span></td><td><span class="badge red">⚠ Espera</span></td></tr>
              <tr><td style="color:var(--grey-400);font-weight:700">05</td><td>Cobro y entrega</td><td style="color:var(--grey-400)">Empleado A/B</td><td><span class="badge blue">3 min</span></td><td><span class="badge green">✓ Valor</span></td></tr>
              <tr class="tr-total"><td colspan="3">⏱ Tiempo Total del Proceso</td><td colspan="2"><span class="badge dark">20 min</span></td></tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <div class="barchart-card" style="margin-bottom:0">
      <div class="barchart-title">Distribución de Tiempos</div>
      <div class="breakdown">
        <div class="act-bar-row"><div class="act-name">Recepción</div><div class="act-track"><div class="act-fill" style="width:10%;background:var(--green)">2m</div></div><div class="act-val">2 min</div></div>
        <div class="act-bar-row"><div class="act-name">Verificación</div><div class="act-track"><div class="act-fill" style="width:20%;background:var(--orange)">4m</div></div><div class="act-val">4 min</div></div>
        <div class="act-bar-row"><div class="act-name">Búsqueda</div><div class="act-track"><div class="act-fill" style="width:35%;background:var(--red)">7m</div></div><div class="act-val">7 min</div></div>
        <div class="act-bar-row"><div class="act-name">Registro</div><div class="act-track"><div class="act-fill" style="width:20%;background:var(--orange)">4m</div></div><div class="act-val">4 min</div></div>
        <div class="act-bar-row"><div class="act-name">Cobro/Entrega</div><div class="act-track"><div class="act-fill" style="width:15%;background:var(--green)">3m</div></div><div class="act-val">3 min</div></div>
        <div style="margin-top:14px;padding-top:12px;border-top:1px solid var(--grey-200)">
          <div style="display:flex;gap:10px;flex-wrap:wrap">
            <span style="display:flex;align-items:center;gap:5px;font-size:11px;color:var(--grey-600)"><span style="width:10px;height:10px;background:var(--red);border-radius:3px;display:inline-block"></span>Crítico</span>
            <span style="display:flex;align-items:center;gap:5px;font-size:11px;color:var(--grey-600)"><span style="width:10px;height:10px;background:var(--orange);border-radius:3px;display:inline-block"></span>Moderado</span>
            <span style="display:flex;align-items:center;gap:5px;font-size:11px;color:var(--grey-600)"><span style="width:10px;height:10px;background:var(--green);border-radius:3px;display:inline-block"></span>Valor</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="alert-row">
    <div class="alert-card">
      <div class="ac-num">7<span style="font-size:16px;font-weight:600;color:var(--grey-400)"> min</span></div>
      <div class="ac-label">Búsqueda del medicamento</div>
      <div class="ac-reason">Productos mal organizados, sin sistema de ubicación por categoría ni mapeo de stock.</div>
    </div>
    <div class="alert-card">
      <div class="ac-num">4<span style="font-size:16px;font-weight:600;color:var(--grey-400)"> min</span></div>
      <div class="ac-label">Verificación de disponibilidad</div>
      <div class="ac-reason">Revisión manual del inventario físico sin apoyo de sistema digital o consulta rápida.</div>
    </div>
    <div class="alert-card">
      <div class="ac-num">4<span style="font-size:16px;font-weight:600;color:var(--grey-400)"> min</span></div>
      <div class="ac-label">Registro de la venta</div>
      <div class="ac-reason">Carga administrativa excesiva en el punto de atención que no aporta valor al cliente.</div>
    </div>
  </div>
  <div class="warn-strip" style="margin-bottom:18px">
    <span style="font-size:18px">⚠</span>
    <span><strong>Estas actividades representan 15 de los 20 minutos totales del proceso (75% del tiempo total).</strong> Tres pasos concentran casi todo el tiempo de espera del cliente sin entregar valor real.</span>
  </div>

  <div class="diag-row">
    <div class="diag-item"><div class="diag-icon">🚫</div><div class="diag-title">Sin dueño del proceso</div><div class="diag-text">No existe un responsable que supervise el flujo de atención completo de principio a fin.</div></div>
    <div class="diag-item"><div class="diag-icon">👥</div><div class="diag-title">Enfoque individual</div><div class="diag-text">Cada empleado atiende su tarea de forma aislada sin visibilidad del tiempo acumulado por el cliente.</div></div>
    <div class="diag-item"><div class="diag-icon">📉</div><div class="diag-title">Sin control del tiempo total</div><div class="diag-text">Nadie supervisa ni mide el tiempo desde la llegada del cliente hasta la entrega del medicamento.</div></div>
  </div>
</div>

<!-- ════════════════════════════════════════════
     PARTE 2 — REORGANIZACIÓN
════════════════════════════════════════════ -->
<div class="section-block" id="part2">
  <div class="section-hd">
    <div class="section-num green">2</div>
    <div class="section-hd-text">
      <h2>Propuesta de Reorganización por Procesos</h2>
      <p>Nuevo rol de coordinación, beneficios esperados y simulador interactivo de tiempos</p>
    </div>
  </div>

  <div class="role-banner">
    <div>
      <h3>Gerente del Proceso de Atención al Cliente</h3>
      <p>Responsable de coordinar todas las actividades de venta y garantizar la calidad del servicio al cliente.</p>
      <div class="func-chips">
        <span class="func-chip">🔍 Supervisar flujo completo</span>
        <span class="func-chip">⚡ Identificar cuellos de botella</span>
        <span class="func-chip">🤝 Coordinar empleados</span>
        <span class="func-chip">📊 Controlar KPIs de tiempo</span>
      </div>
      <div style="margin-top:14px;background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.15);border-radius:8px;padding:10px 14px;font-size:12.5px;opacity:.85">
        📋 <strong>Plan complementario:</strong> Reorganizar inventario por categoría terapéutica y simplificar el registro de ventas con sistema integrado.
      </div>
    </div>
    <div class="role-badge-big">👨‍💼</div>
  </div>

  <div class="benefits-grid">
    <div class="benefit-card"><div class="benefit-icon">🎯</div><div class="benefit-title">Mayor control del proceso completo</div></div>
    <div class="benefit-card"><div class="benefit-icon">⏱</div><div class="benefit-title">Reducción de tiempos de espera</div></div>
    <div class="benefit-card"><div class="benefit-icon">💊</div><div class="benefit-title">Mejor organización de medicamentos</div></div>
    <div class="benefit-card"><div class="benefit-icon">🚀</div><div class="benefit-title">Mayor productividad del personal</div></div>
    <div class="benefit-card"><div class="benefit-icon">😊</div><div class="benefit-title">Mejor experiencia para el cliente</div></div>
    <div class="benefit-card"><div class="benefit-icon">✅</div><div class="benefit-title">Responsabilidad clara sobre resultados</div></div>
  </div>

  <div id="sim" class="sim-layout">
    <div class="sim-card">
      <div class="card-hd" style="padding-bottom:12px">
        <div class="card-title">Simulador de Tiempos de Atención</div>
        <span class="badge green">Interactivo</span>
      </div>
      <div class="card-body" style="padding-top:0">
        <div class="tbl-wrap">
          <table>
            <thead><tr><th>Actividad</th><th>Actual</th><th>Mejorado</th></tr></thead>
            <tbody>
              <tr><td>Recepción del cliente</td><td><span class="badge blue">2 min</span></td><td><span style="font-size:12.5px;color:var(--grey-400)">2 min (fijo)</span></td></tr>
              <tr>
                <td>Verificación de disponibilidad</td>
                <td><span class="badge orange">4 min</span></td>
                <td><div class="slider-cell"><input type="range" id="s1" min="0" max="10" value="2"/><span class="sv" id="v1">2</span><span style="font-size:11px;color:var(--grey-400)">min</span></div></td>
              </tr>
              <tr>
                <td>Búsqueda del medicamento</td>
                <td><span class="badge red">7 min</span></td>
                <td><div class="slider-cell"><input type="range" id="s2" min="0" max="10" value="3"/><span class="sv" id="v2">3</span><span style="font-size:11px;color:var(--grey-400)">min</span></div></td>
              </tr>
              <tr>
                <td>Registro de la venta</td>
                <td><span class="badge orange">4 min</span></td>
                <td><div class="slider-cell"><input type="range" id="s3" min="0" max="10" value="2"/><span class="sv" id="v3">2</span><span style="font-size:11px;color:var(--grey-400)">min</span></div></td>
              </tr>
              <tr><td>Cobro y entrega</td><td><span class="badge blue">3 min</span></td><td><span style="font-size:12.5px;color:var(--grey-400)">3 min (fijo)</span></td></tr>
              <tr class="tr-total-green">
                <td colspan="2">⏱ Total Tiempo Mejorado</td>
                <td><span id="totalImproved" style="font-size:22px;font-weight:900;transition:all .3s">12</span><span style="font-size:14px;font-weight:700"> min</span></td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <div class="barchart-card">
      <div class="barchart-title">Comparativa de Tiempos Totales</div>
      <div class="bar-group">
        <div class="bar-label"><span>🔵 Proceso Actual</span><span style="font-weight:800;color:var(--blue)">20 min</span></div>
        <div class="bar-track"><div class="bar-fill navy" style="width:100%">20 min</div></div>
      </div>
      <div class="bar-group">
        <div class="bar-label"><span>🟢 Proceso Mejorado</span><span id="bar-val-label" style="font-weight:800;color:var(--green)">12 min</span></div>
        <div class="bar-track"><div class="bar-fill green" id="barImproved" style="width:60%">12 min</div></div>
      </div>
      <div class="bar-scale"><span>0</span><span>5</span><span>10</span><span>15</span><span>20 min</span></div>

      <div class="breakdown" style="margin-top:20px">
        <div class="breakdown-title">Desglose mejorado por actividad</div>
        <div class="act-bar-row"><div class="act-name">Recepción</div><div class="act-track"><div class="act-fill" style="width:10%;background:var(--green)">2m</div></div><div class="act-val">2 min</div></div>
        <div class="act-bar-row"><div class="act-name">Verificación</div><div class="act-track"><div class="act-fill" id="ab1" style="background:var(--cyan)"></div></div><div class="act-val" id="ab1v">2 min</div></div>
        <div class="act-bar-row"><div class="act-name">Búsqueda</div><div class="act-track"><div class="act-fill" id="ab2" style="background:var(--cyan)"></div></div><div class="act-val" id="ab2v">3 min</div></div>
        <div class="act-bar-row"><div class="act-name">Registro</div><div class="act-track"><div class="act-fill" id="ab3" style="background:var(--cyan)"></div></div><div class="act-val" id="ab3v">2 min</div></div>
        <div class="act-bar-row"><div class="act-name">Cobro/Entrega</div><div class="act-track"><div class="act-fill" style="width:15%;background:var(--green)">3m</div></div><div class="act-val">3 min</div></div>
      </div>
    </div>
  </div>
</div>

<!-- ════════════════════════════════════════════
     PARTE 2B — CAPACIDAD DE CLIENTES
════════════════════════════════════════════ -->
<div class="section-block" id="part-capacity">
  <div class="section-hd">
    <div class="section-num purple">3</div>
    <div class="section-hd-text">
      <h2>Impacto en Capacidad de Atención</h2>
      <p>Al reducir el tiempo por cliente, la farmacia puede atender más personas en las mismas 8 horas laborales</p>
    </div>
  </div>

  <div class="capacity-banner">
    <div class="capacity-banner-text">
      <h3>Cálculo de capacidad diaria</h3>
      <p>Con los mismos 2 empleados y la misma jornada de 8 horas, al reducir el tiempo por cliente el sistema procesa más atenciones. El dato base de <strong>40 clientes/día</strong> fue observado directamente en la farmacia.</p>
    </div>
    <div class="capacity-formula">
      <div style="font-size:11px;opacity:.8;letter-spacing:.05em;font-weight:700">FÓRMULA APLICADA</div>
      <div class="formula-eq">Clientes mejorado =<br>40 × (20 ÷ T<sub>nuevo</sub>)</div>
      <div style="font-size:11px;opacity:.7;margin-top:6px">T<sub>actual</sub> = 20 min · Clientes<sub>actual</sub> = 40</div>
    </div>
  </div>

  <!-- Big 3 stats -->
  <div class="clients-grid">
    <div class="client-stat actual">
      <div class="client-stat-icon">👥</div>
      <div class="client-stat-label">Clientes actuales / día</div>
      <div class="client-stat-value blue">40</div>
      <div class="client-stat-sub">Dato real observado · 8 h</div>
    </div>
    <div class="client-stat mejorado">
      <div class="client-stat-icon">🚀</div>
      <div class="client-stat-label">Clientes mejorados / día</div>
      <div class="client-stat-value green" id="clients-improved">67</div>
      <div class="client-stat-sub">Con <span id="clients-time-ref">12</span> min por atención</div>
    </div>
    <div class="client-stat incremento">
      <div class="client-stat-icon">📈</div>
      <div class="client-stat-label">Clientes adicionales / día</div>
      <div class="client-stat-value purple" id="clients-extra">+27</div>
      <div class="client-stat-sub"><span id="clients-pct">+66.7%</span> más clientes</div>
    </div>
  </div>

  <!-- Gain highlight -->
  <div class="gain-strip">
    <div class="gain-big" id="gain-big-pct">+66.7%</div>
    <div class="gain-strip-text">
      Reduciendo el tiempo de atención de <strong>20 min a <span id="gain-ref-time">12</span> min</strong>, la farmacia podría atender
      <strong><span id="gain-ref-clients">67</span> clientes por día</strong> en lugar de 40 — un incremento de
      <strong><span id="gain-ref-extra">27</span> personas adicionales</strong> con el mismo equipo y la misma jornada laboral.
    </div>
  </div>

  <!-- Charts -->
  <div class="clients-chart-layout">
    <!-- Column chart -->
    <div class="clients-chart-card">
      <div class="clients-chart-title">Clientes atendidos por día</div>
      <div class="col-chart">
        <div class="col-group">
          <div class="col-bar-wrap">
            <div class="col-bar blue" id="col-actual" style="height:120px">40</div>
          </div>
          <div class="col-label">Actual</div>
          <div class="col-sublabel">20 min/cliente</div>
        </div>
        <div class="col-group">
          <div class="col-bar-wrap">
            <div class="col-bar green" id="col-improved" style="height:168px"><span id="col-improved-label">67</span></div>
          </div>
          <div class="col-label">Mejorado</div>
          <div class="col-sublabel"><span id="col-improved-sub">12</span> min/cliente</div>
        </div>
      </div>
      <!-- Simple axis reference -->
      <div style="display:flex;justify-content:space-between;padding:0 8px;margin-top:4px">
        <div style="font-size:10px;color:var(--grey-400)">Referencia: 120 px = 40 clientes</div>
        <div style="font-size:11px;font-weight:700;color:var(--purple)" id="col-diff-label">+27 clientes</div>
      </div>
    </div>

    <!-- People dots chart -->
    <div class="clients-chart-card">
      <div class="clients-chart-title">Representación visual de clientes</div>
      <div class="people-chart">
        <div class="people-row">
          <div class="people-row-label" style="color:var(--blue);font-weight:700">Actual</div>
          <div class="people-dots" id="dots-actual"></div>
          <div class="people-row-count blue">40</div>
        </div>
        <div class="people-row" style="margin-top:8px">
          <div class="people-row-label" style="color:var(--green);font-weight:700">Mejorado</div>
          <div class="people-dots" id="dots-improved"></div>
          <div class="people-row-count green" id="dots-improved-count">67</div>
        </div>
      </div>
      <div class="people-legend">
        <div class="pleg"><div class="pleg-dot" style="background:var(--blue)"></div>Clientes actuales (40)</div>
        <div class="pleg"><div class="pleg-dot" style="background:var(--green)"></div>Clientes adicionales (<span id="legend-extra">27</span>)</div>
      </div>
    </div>
  </div>

  <!-- Capacity table -->
  <div class="card">
    <div class="card-hd"><div class="card-title">Tabla de Capacidad por Tiempo de Atención</div></div>
    <div class="card-body" style="padding-top:10px">
      <div class="tbl-wrap">
        <table>
          <thead><tr><th>Tiempo por cliente</th><th>Clientes / día</th><th>Incremento</th><th>Mejora %</th><th>Estado</th></tr></thead>
          <tbody>
            <tr style="background:var(--blue-light)">
              <td><strong>20 min</strong> (actual)</td><td><strong>40</strong></td><td>—</td><td>—</td><td><span class="badge blue">Base real</span></td>
            </tr>
            <tr><td>18 min</td><td>44</td><td>+4</td><td>+10%</td><td><span class="badge orange">Leve</span></td></tr>
            <tr><td>16 min</td><td>50</td><td>+10</td><td>+25%</td><td><span class="badge orange">Moderado</span></td></tr>
            <tr id="row-highlight-12" style="background:var(--green-light)">
              <td><strong>12 min</strong> (propuesto)</td><td><strong>67</strong></td><td><strong>+27</strong></td><td><strong>+66.7%</strong></td><td><span class="badge green">✓ Objetivo</span></td>
            </tr>
            <tr><td>10 min</td><td>80</td><td>+40</td><td>+100%</td><td><span class="badge purple">Óptimo</span></td></tr>
            <tr><td>8 min</td><td>100</td><td>+60</td><td>+150%</td><td><span class="badge purple">Máximo</span></td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</div>

<!-- ════════════════════════════════════════════
     PARTE 3 — LEAN + KPIs
════════════════════════════════════════════ -->
<div class="section-block" id="part3">
  <div class="section-hd">
    <div class="section-num orange">4</div>
    <div class="section-hd-text">
      <h2>Iniciativa Lean e Impacto en KPIs</h2>
      <p>Clasificación de valor, indicadores dinámicos y medición de la reducción de desperdicios</p>
    </div>
  </div>

  <div class="lean-intro">
    <strong>Lean</strong> es la metodología seleccionada porque busca <strong>eliminar de raíz las actividades que no agregan valor</strong> y reducir drásticamente los desperdicios del proceso. Aplicado a esta farmacia, Lean identifica cuáles pasos del flujo de atención son esenciales para el cliente y cuáles son fricciones internas que alargan la espera sin aportar beneficio real.
  </div>

  <div class="card" style="margin-bottom:18px">
    <div class="card-hd"><div class="card-title">Matriz de Clasificación de Valor (Lean)</div></div>
    <div class="card-body" style="padding-top:10px">
      <div class="tbl-wrap">
        <table>
          <thead><tr><th>Actividad</th><th>Tiempo</th><th>¿Agrega Valor?</th><th>Categoría Lean</th><th>Observación</th></tr></thead>
          <tbody>
            <tr><td>Recepción del cliente</td><td><span class="badge blue">2 min</span></td><td><span class="badge green">✓ Sí</span></td><td><span class="badge green">Valor</span></td><td style="color:var(--grey-400);font-size:12px">Contacto directo — esencial</td></tr>
            <tr><td>Verificación de disponibilidad</td><td><span class="badge orange">4 min</span></td><td><span class="badge red">✗ No</span></td><td><span class="badge red">Desperdicio</span></td><td style="color:var(--grey-400);font-size:12px">Eliminable con sistema digital</td></tr>
            <tr><td>Búsqueda del medicamento</td><td><span class="badge red">7 min</span></td><td><span class="badge red">✗ No</span></td><td><span class="badge red">Desperdicio</span></td><td style="color:var(--grey-400);font-size:12px">Mala organización de inventario</td></tr>
            <tr><td>Registro de la venta</td><td><span class="badge orange">4 min</span></td><td><span class="badge red">✗ No</span></td><td><span class="badge red">Desperdicio</span></td><td style="color:var(--grey-400);font-size:12px">Carga administrativa reducible</td></tr>
            <tr><td>Cobro y entrega</td><td><span class="badge blue">3 min</span></td><td><span class="badge green">✓ Sí</span></td><td><span class="badge green">Valor</span></td><td style="color:var(--grey-400);font-size:12px">Transacción de valor real</td></tr>
            <tr class="tr-total-green"><td colspan="2">Tiempo que Agrega Valor (fijo)</td><td colspan="3"><span class="badge dark">5 min — permanece fijo en el proceso</span></td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>

  <div class="kpi-compare">
    <div class="kpi-panel">
      <div class="kpi-panel-hd blue">
        <div><h3>📊 Proceso Actual</h3><p>Indicadores fijos — base 20 min</p></div>
      </div>
      <div class="kpi-panel-body">
        <div class="donut-kpi-layout">
          <div class="donut-side">
            <svg width="150" height="150" viewBox="0 0 150 150">
              <circle cx="75" cy="75" r="58" fill="none" stroke="#E2E8F0" stroke-width="20"/>
              <circle cx="75" cy="75" r="58" fill="none" stroke="#DC2626" stroke-width="20" opacity=".8"
                stroke-dasharray="273.3 364.42" stroke-dashoffset="273.3" transform="rotate(-90 75 75)"/>
              <circle cx="75" cy="75" r="58" fill="none" stroke="#059669" stroke-width="20"
                stroke-dasharray="91.1 364.42" stroke-dashoffset="0" transform="rotate(-90 75 75)"/>
              <text x="75" y="70" text-anchor="middle" font-size="20" font-weight="900" fill="#1B4F8A">25%</text>
              <text x="75" y="86" text-anchor="middle" font-size="10" fill="#94A3B8">Valor</text>
            </svg>
            <div class="d-legend">
              <div class="d-leg-item"><div class="d-leg-dot" style="background:var(--green)"></div>Valor (25%)</div>
              <div class="d-leg-item"><div class="d-leg-dot" style="background:var(--red)"></div>Desperdicio (75%)</div>
            </div>
          </div>
          <div class="kpi-stack">
            <div class="kpi-row"><div class="kpi-lbl">Ratio Valor Agregado</div><div class="kpi-val blue">25.0%</div><div class="kpi-note">5 min útiles / 20 min totales</div></div>
            <div class="kpi-row"><div class="kpi-lbl">Waste Index (Desperdicio)</div><div class="kpi-val red">75.0%</div><div class="kpi-note">15 min de desperdicio total</div></div>
            <div class="kpi-row"><div class="kpi-lbl">Clientes atendidos / día</div><div class="kpi-val blue" style="font-size:30px">40</div><div class="kpi-note">Dato real observado</div></div>
          </div>
        </div>
      </div>
    </div>

    <div class="kpi-panel">
      <div class="kpi-panel-hd green">
        <div><h3>🚀 Proceso Mejorado</h3><p>Indicadores dinámicos — ajusta los sliders</p></div>
      </div>
      <div class="kpi-panel-body">
        <div class="donut-kpi-layout">
          <div class="donut-side">
            <svg width="150" height="150" viewBox="0 0 150 150">
              <circle cx="75" cy="75" r="58" fill="none" stroke="#E2E8F0" stroke-width="20"/>
              <circle cx="75" cy="75" r="58" fill="none" stroke="#DC2626" stroke-width="20" opacity=".8"
                id="donutWaste" stroke-dasharray="212.4 364.42" stroke-dashoffset="152.0" transform="rotate(-90 75 75)"
                style="transition:stroke-dasharray .5s cubic-bezier(.4,0,.2,1),stroke-dashoffset .5s cubic-bezier(.4,0,.2,1)"/>
              <circle cx="75" cy="75" r="58" fill="none" stroke="#059669" stroke-width="20"
                id="donutValue" stroke-dasharray="152.0 364.42" stroke-dashoffset="0" transform="rotate(-90 75 75)"
                style="transition:stroke-dasharray .5s cubic-bezier(.4,0,.2,1)"/>
              <text x="75" y="70" text-anchor="middle" font-size="18" font-weight="900" fill="#059669" id="donutLabel">41.7%</text>
              <text x="75" y="86" text-anchor="middle" font-size="10" fill="#94A3B8">Valor</text>
            </svg>
            <div class="d-legend">
              <div class="d-leg-item"><div class="d-leg-dot" style="background:var(--green)"></div>Valor (<span id="donutLegendValue">41.7</span>%)</div>
              <div class="d-leg-item"><div class="d-leg-dot" style="background:var(--red)"></div>Desperdicio (<span id="donutLegendWaste">58.3</span>%)</div>
            </div>
          </div>
          <div class="kpi-stack">
            <div class="kpi-row"><div class="kpi-lbl">Ratio Valor Agregado</div><div class="kpi-val green" id="kpiValueRatio">41.7%</div><div class="kpi-note">5 min / <span id="kpiTotalRef">12</span> min totales</div></div>
            <div class="kpi-row"><div class="kpi-lbl">Waste Index Mejorado</div><div class="kpi-val" style="color:var(--orange);transition:all .4s" id="kpiWasteIndex">58.3%</div></div>
            <div class="kpi-row highlight"><div class="kpi-lbl">⚡ Reducción tiempo Lean</div><div class="kpi-val big" id="kpiLeanImpact">40.0%</div><div class="kpi-note">menos tiempo vs proceso actual</div></div>
            <div class="kpi-row highlight-purple"><div class="kpi-lbl">👥 Clientes / día (mejorado)</div><div class="kpi-val purple" id="kpiClients">67</div><div class="kpi-note">+<span id="kpiClientsExtra">27</span> clientes adicionales</div></div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="conclusion">
    <h3>📝 Conclusión Automática</h3>
    <p id="conclusionText">La aplicación de Lean permite identificar que el proceso mejorado eleva la eficiencia, reduciendo el desperdicio del 75% inicial a un 58.3% y acortando el tiempo de espera del cliente en un 40.0%, pasando de 20 minutos a 12 minutos de atención total. Esto incrementa la capacidad de la farmacia de 40 a 67 clientes por día (+27 clientes, +66.7%), representando una mejora sustancial que impacta directamente en la satisfacción del cliente, la productividad del equipo y los ingresos del negocio.</p>
  </div>
</div>

  </div><!-- /content -->
</div><!-- /main -->
</div><!-- /layout -->

<script>
const C = 2 * Math.PI * 58; // 364.424

const s1 = document.getElementById('s1');
const s2 = document.getElementById('s2');
const s3 = document.getElementById('s3');

const ACTUAL_CLIENTS = 40;
const ACTUAL_TIME = 20;
const MAX_DOTS = 100; // render at most 100 dots

function renderDots() {
  const improved = Math.round(ACTUAL_CLIENTS * (ACTUAL_TIME / (+s1.value + +s2.value + +s3.value + 5)));
  const extra = improved - ACTUAL_CLIENTS;

  // Actual row: 40 blue dots
  const da = document.getElementById('dots-actual');
  da.innerHTML = '';
  for (let i = 0; i < Math.min(ACTUAL_CLIENTS, MAX_DOTS); i++) {
    const d = document.createElement('div');
    d.className = 'person-dot actual';
    d.title = 'Cliente actual';
    d.textContent = '👤';
    da.appendChild(d);
  }

  // Improved row: 40 blue-tinted + extra green
  const di = document.getElementById('dots-improved');
  di.innerHTML = '';
  const totalShow = Math.min(improved, MAX_DOTS);
  for (let i = 0; i < totalShow; i++) {
    const d = document.createElement('div');
    d.className = i < ACTUAL_CLIENTS ? 'person-dot actual' : 'person-dot extra';
    d.title = i < ACTUAL_CLIENTS ? 'Cliente actual' : 'Cliente adicional';
    d.textContent = i < ACTUAL_CLIENTS ? '👤' : '🟢';
    di.appendChild(d);
  }
  if (improved > MAX_DOTS) {
    const more = document.createElement('div');
    more.style.cssText = 'font-size:11px;color:var(--grey-400);align-self:center;padding:2px 6px;background:var(--grey-100);border-radius:8px;font-weight:700;';
    more.textContent = `+${improved - MAX_DOTS} más`;
    di.appendChild(more);
  }
}

function update() {
  const v1 = +s1.value, v2 = +s2.value, v3 = +s3.value;

  // Slider labels
  document.getElementById('v1').textContent = v1;
  document.getElementById('v2').textContent = v2;
  document.getElementById('v3').textContent = v3;

  const total = 2 + v1 + v2 + v3 + 3;
  const improved = Math.round(ACTUAL_CLIENTS * (ACTUAL_TIME / total));
  const extra = improved - ACTUAL_CLIENTS;
  const pctIncrease = ((improved - ACTUAL_CLIENTS) / ACTUAL_CLIENTS * 100).toFixed(1);

  // ── Topbar
  document.getElementById('tb-total').textContent = total;
  document.getElementById('tb-clients').textContent = improved;

  // ── Time totals
  document.getElementById('totalImproved').textContent = total;
  document.getElementById('kpiTotalRef').textContent = total;

  // ── Main bar (time)
  const pct = Math.min((total / 20) * 100, 100);
  const bar = document.getElementById('barImproved');
  bar.style.width = pct + '%';
  bar.textContent = total + ' min';
  document.getElementById('bar-val-label').textContent = total + ' min';

  // ── Activity bars
  const ab1 = document.getElementById('ab1'); ab1.style.width = (v1/10*100)+'%'; ab1.textContent = v1>0?v1+'m':'';
  const ab2 = document.getElementById('ab2'); ab2.style.width = (v2/10*100)+'%'; ab2.textContent = v2>0?v2+'m':'';
  const ab3 = document.getElementById('ab3'); ab3.style.width = (v3/10*100)+'%'; ab3.textContent = v3>0?v3+'m':'';
  document.getElementById('ab1v').textContent = v1 + ' min';
  document.getElementById('ab2v').textContent = v2 + ' min';
  document.getElementById('ab3v').textContent = v3 + ' min';

  // ── KPI Lean
  const valueRatio = (5 / total) * 100;
  const wasteIndex = 100 - valueRatio;
  const leanImpact = ((20 - total) / 20) * 100;
  document.getElementById('kpiValueRatio').textContent = valueRatio.toFixed(1) + '%';
  document.getElementById('kpiWasteIndex').textContent = wasteIndex.toFixed(1) + '%';
  document.getElementById('kpiLeanImpact').textContent = leanImpact.toFixed(1) + '%';
  document.getElementById('kpiClients').textContent = improved;
  document.getElementById('kpiClientsExtra').textContent = extra;

  // ── Donut
  const valueDash = (valueRatio / 100) * C;
  const wasteDash = C - valueDash;
  document.getElementById('donutValue').setAttribute('stroke-dasharray', `${valueDash.toFixed(2)} ${C.toFixed(2)}`);
  document.getElementById('donutValue').setAttribute('stroke-dashoffset', '0');
  document.getElementById('donutWaste').setAttribute('stroke-dasharray', `${wasteDash.toFixed(2)} ${C.toFixed(2)}`);
  document.getElementById('donutWaste').setAttribute('stroke-dashoffset', `${(C - valueDash).toFixed(2)}`);
  document.getElementById('donutLabel').textContent = valueRatio.toFixed(1) + '%';
  document.getElementById('donutLegendValue').textContent = valueRatio.toFixed(1);
  document.getElementById('donutLegendWaste').textContent = wasteIndex.toFixed(1);

  // ── Capacity section
  document.getElementById('clients-improved').textContent = improved;
  document.getElementById('clients-time-ref').textContent = total;
  document.getElementById('clients-extra').textContent = '+' + extra;
  document.getElementById('clients-pct').textContent = '+' + pctIncrease + '%';

  document.getElementById('gain-big-pct').textContent = '+' + pctIncrease + '%';
  document.getElementById('gain-ref-time').textContent = total;
  document.getElementById('gain-ref-clients').textContent = improved;
  document.getElementById('gain-ref-extra').textContent = extra;

  // ── Column chart (max reference = 80 to give headroom; 120px = 40 clients)
  const colActualH = 120;
  const colImprovedH = Math.min(Math.round((improved / 40) * 120), 200);
  document.getElementById('col-actual').style.height = colActualH + 'px';
  document.getElementById('col-improved').style.height = colImprovedH + 'px';
  document.getElementById('col-improved-label').textContent = improved;
  document.getElementById('col-improved-sub').textContent = total;
  document.getElementById('col-diff-label').textContent = '+' + extra + ' clientes';

  // ── Dots
  renderDots();
  document.getElementById('dots-improved-count').textContent = improved;
  document.getElementById('legend-extra').textContent = extra;

  // ── Conclusion
  const msg = leanImpact >= 30
    ? `Esto incrementa la capacidad de la farmacia de 40 a ${improved} clientes por día (+${extra} clientes, +${pctIncrease}%), representando una mejora sustancial que impacta directamente en la satisfacción del cliente, la productividad del equipo y los ingresos del negocio.`
    : `Ajusta los sliders para explorar el mayor potencial de mejora disponible. Con mayor reducción se obtienen más clientes atendidos por día.`;

  document.getElementById('conclusionText').textContent =
    `La aplicación de Lean permite identificar que el proceso mejorado eleva la eficiencia, reduciendo el desperdicio del 75% inicial a un ${wasteIndex.toFixed(1)}% y acortando el tiempo de espera del cliente en un ${leanImpact.toFixed(1)}%, pasando de 20 minutos a ${total} minutos de atención total. ${msg}`;
}

s1.addEventListener('input', update);
s2.addEventListener('input', update);
s3.addEventListener('input', update);
update();

// Sidebar active link on scroll
const sections = ['part1','part2','part-capacity','part3'];
const navItems = document.querySelectorAll('.nav-item');
window.addEventListener('scroll', () => {
  let current = 'part1';
  sections.forEach(id => {
    const el = document.getElementById(id);
    if (el && el.getBoundingClientRect().top < 120) current = id;
  });
  navItems.forEach(n => {
    n.classList.toggle('active', n.getAttribute('href') === '#' + current);
  });
});
</script>
</body>
</html>
HTMLEOF
echo "done"
