[mis-finanzas (1).html](https://github.com/user-attachments/files/28623471/mis-finanzas.1.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<title>Mis Finanzas</title>
<style>
* { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; -webkit-text-size-adjust: 100%; }
html, body { width: 100%; min-height: 100%; background: #0e0f13; color: #f0f0f2; font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', sans-serif; }
a, button { -webkit-appearance: none; }

:root {
  --bg: #0e0f13; --bg2: #16181f; --bg3: #1e2029; --card: #1a1c24;
  --border: rgba(255,255,255,0.08);
  --text: #f0f0f2; --muted: #7a7d8a;
  --green: #22c87a; --green-bg: rgba(34,200,122,0.12);
  --red: #f04f4f; --red-bg: rgba(240,79,79,0.12);
  --amber: #f0a030; --amber-bg: rgba(240,160,48,0.12);
  --blue: #4fa8f0; --blue-bg: rgba(79,168,240,0.12);
  --accent: #7c6af7; --accent-bg: rgba(124,106,247,0.14);
  --radius: 14px; --rsm: 10px;
}

/* LAYOUT */
#app { display: -webkit-flex; display: flex; -webkit-flex-direction: column; flex-direction: column; min-height: 100vh; }
.pages { -webkit-flex: 1; flex: 1; padding-bottom: 75px; overflow-y: auto; -webkit-overflow-scrolling: touch; }
.page { display: none; }
.page.active { display: block; }

/* BOTTOM NAV */
.bnav {
  position: fixed; bottom: 0; left: 0; right: 0; z-index: 999;
  background: #16181f; border-top: 1px solid rgba(255,255,255,0.1);
  display: -webkit-flex; display: flex;
  padding-bottom: env(safe-area-inset-bottom, 0px);
}
.nitem {
  -webkit-flex: 1; flex: 1;
  display: -webkit-flex; display: flex;
  -webkit-flex-direction: column; flex-direction: column;
  -webkit-align-items: center; align-items: center;
  padding: 8px 2px 6px; font-size: 10px; color: #7a7d8a;
  background: none; border: none; cursor: pointer;
  position: relative; -webkit-user-select: none; user-select: none;
}
.nitem.active { color: #7c6af7; }
.nitem svg { width: 22px; height: 22px; margin-bottom: 3px; fill: none; stroke: currentColor; stroke-width: 1.8; stroke-linecap: round; stroke-linejoin: round; }
.ndot { position: absolute; top: 6px; right: 14px; width: 7px; height: 7px; background: #f04f4f; border-radius: 50%; border: 1.5px solid #16181f; display: none; }
.ndot.on { display: block; }

/* HEADER */
.ph { padding: 20px 16px 10px; display: -webkit-flex; display: flex; -webkit-align-items: center; align-items: center; -webkit-justify-content: space-between; justify-content: space-between; }
.ph h2 { font-size: 22px; font-weight: 600; }
.ph .sub { font-size: 12px; color: #7a7d8a; margin-top: 2px; }
.btn-add {
  width: 38px; height: 38px; border-radius: 50%;
  background: #7c6af7; color: #fff; font-size: 24px; line-height: 38px; text-align: center;
  border: none; cursor: pointer; -webkit-flex-shrink: 0; flex-shrink: 0;
}

/* KPI STRIP */
.kstrip { display: -webkit-flex; display: flex; gap: 10px; padding: 4px 16px 14px; overflow-x: auto; -webkit-overflow-scrolling: touch; }
.kstrip::-webkit-scrollbar { display: none; }
.kcard { -webkit-flex-shrink: 0; flex-shrink: 0; min-width: 130px; background: #1a1c24; border: 1px solid rgba(255,255,255,0.08); border-radius: 14px; padding: 13px 14px; }
.kcard .kl { font-size: 11px; color: #7a7d8a; margin-bottom: 5px; }
.kcard .kv { font-size: 17px; font-weight: 600; font-variant-numeric: tabular-nums; }
.kv.g { color: #22c87a; } .kv.r { color: #f04f4f; } .kv.a { color: #f0a030; } .kv.b { color: #4fa8f0; }

/* SECTION */
.sec { padding: 2px 16px 16px; }
.stitle { font-size: 11px; font-weight: 600; color: #7a7d8a; text-transform: uppercase; letter-spacing: 0.09em; margin-bottom: 10px; }

/* ITEMS */
.ilist { display: -webkit-flex; display: flex; -webkit-flex-direction: column; flex-direction: column; gap: 8px; }
.item {
  background: #1a1c24; border: 1px solid rgba(255,255,255,0.08);
  border-radius: 12px; padding: 13px 14px;
  display: -webkit-flex; display: flex;
  -webkit-align-items: center; align-items: center; gap: 11px;
  cursor: pointer; position: relative;
}
.iico { width: 38px; height: 38px; border-radius: 10px; display: -webkit-flex; display: flex; -webkit-align-items: center; align-items: center; -webkit-justify-content: center; justify-content: center; font-size: 18px; -webkit-flex-shrink: 0; flex-shrink: 0; }
.iico.g { background: rgba(34,200,122,0.12); }
.iico.r { background: rgba(240,79,79,0.12); }
.iico.a { background: rgba(240,160,48,0.12); }
.iico.b { background: rgba(79,168,240,0.12); }
.iico.p { background: rgba(124,106,247,0.14); }
.ibody { -webkit-flex: 1; flex: 1; min-width: 0; }
.iname { font-size: 14px; font-weight: 500; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.isub { font-size: 12px; color: #7a7d8a; margin-top: 2px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.iright { text-align: right; -webkit-flex-shrink: 0; flex-shrink: 0; }
.iamt { font-size: 15px; font-weight: 600; font-variant-numeric: tabular-nums; }
.iamt.g { color: #22c87a; } .iamt.r { color: #f04f4f; } .iamt.a { color: #f0a030; } .iamt.b { color: #4fa8f0; }
.ibadge { display: inline-block; font-size: 10px; font-weight: 600; padding: 2px 7px; border-radius: 20px; margin-top: 4px; }
.br { background: rgba(240,79,79,0.12); color: #f04f4f; }
.ba { background: rgba(240,160,48,0.12); color: #f0a030; }
.bg { background: rgba(34,200,122,0.12); color: #22c87a; }
.bb { background: rgba(79,168,240,0.12); color: #4fa8f0; }
.bp { background: rgba(124,106,247,0.14); color: #7c6af7; }
.idel { position: absolute; right: 10px; top: 50%; -webkit-transform: translateY(-50%); transform: translateY(-50%); background: rgba(240,79,79,0.14); color: #f04f4f; width: 28px; height: 28px; border-radius: 7px; display: none; -webkit-align-items: center; align-items: center; -webkit-justify-content: center; justify-content: center; font-size: 14px; border: none; cursor: pointer; }

/* DEUDA PROGRESS */
.dprog { width: 100%; padding: 8px 0 0; }
.dprow { display: -webkit-flex; display: flex; -webkit-justify-content: space-between; justify-content: space-between; font-size: 11px; color: #7a7d8a; margin-bottom: 5px; }
.dpbar { height: 4px; background: rgba(255,255,255,0.07); border-radius: 4px; overflow: hidden; }
.dpfill { height: 100%; background: #7c6af7; border-radius: 4px; }

/* BALANCE */
.bwrap { background: #1a1c24; border: 1px solid rgba(255,255,255,0.08); border-radius: 14px; padding: 15px; margin: 0 16px 14px; }
.brow { display: -webkit-flex; display: flex; -webkit-justify-content: space-between; justify-content: space-between; font-size: 12px; margin-bottom: 5px; }
.bbar { height: 5px; background: rgba(255,255,255,0.07); border-radius: 4px; overflow: hidden; margin-bottom: 12px; }
.bfill { height: 100%; background: #f04f4f; border-radius: 4px; }
.bnet { display: -webkit-flex; display: flex; -webkit-justify-content: space-between; justify-content: space-between; -webkit-align-items: center; align-items: center; padding-top: 11px; border-top: 1px solid rgba(255,255,255,0.07); }
.bnet .nl { font-size: 12px; color: #7a7d8a; }
.bnet .nv { font-size: 18px; font-weight: 600; font-variant-numeric: tabular-nums; }

/* ALERT */
.alert { margin: 0 16px 12px; background: rgba(240,79,79,0.1); border: 1px solid rgba(240,79,79,0.22); border-radius: 10px; padding: 10px 14px; font-size: 13px; color: #f04f4f; display: none; }
.alert.on { display: block; }

/* GREETING */
.greet { padding: 22px 16px 10px; }
.greet .hi { font-size: 22px; font-weight: 600; }
.greet .dt { font-size: 13px; color: #7a7d8a; margin-top: 3px; }

/* EMPTY */
.empty { text-align: center; padding: 32px 20px; color: #7a7d8a; font-size: 14px; }
.empty .emo { font-size: 34px; margin-bottom: 8px; }

/* MODAL */
.overlay { position: fixed; inset: 0; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.72); display: none; -webkit-align-items: flex-end; align-items: flex-end; -webkit-justify-content: center; justify-content: center; z-index: 9999; -webkit-backdrop-filter: blur(3px); backdrop-filter: blur(3px); }
.overlay.on { display: -webkit-flex; display: flex; }
.modal { background: #16181f; border-radius: 22px 22px 0 0; border: 1px solid rgba(255,255,255,0.1); width: 100%; max-width: 500px; padding: 18px 18px 30px; max-height: 90vh; overflow-y: auto; -webkit-overflow-scrolling: touch; }
.mhandle { width: 36px; height: 4px; background: rgba(255,255,255,0.15); border-radius: 4px; margin: 0 auto 16px; }
.modal h3 { font-size: 18px; font-weight: 600; margin-bottom: 16px; }
.fg { margin-bottom: 13px; }
.fg label { font-size: 11px; font-weight: 600; color: #7a7d8a; letter-spacing: 0.06em; text-transform: uppercase; margin-bottom: 6px; display: block; }
.fg input, .fg select, .fg textarea {
  width: 100%; background: #1e2029; border: 1px solid rgba(255,255,255,0.1);
  border-radius: 10px; padding: 12px 13px; color: #f0f0f2;
  font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', sans-serif;
  font-size: 16px; -webkit-appearance: none; appearance: none;
  outline: none;
}
.fg input:focus, .fg select:focus, .fg textarea:focus { border-color: #7c6af7; }
.fg select { background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%237a7d8a' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right 13px center; padding-right: 36px; }
.frow { display: -webkit-flex; display: flex; gap: 10px; }
.frow .fg { -webkit-flex: 1; flex: 1; }
.fg textarea { resize: none; }
.bsave { width: 100%; padding: 15px; background: #7c6af7; color: #fff; border-radius: 11px; font-size: 16px; font-weight: 600; margin-top: 6px; border: none; cursor: pointer; }
.bcancel { width: 100%; padding: 12px; color: #7a7d8a; font-size: 14px; margin-top: 4px; background: none; border: none; cursor: pointer; }
</style>
</head>
<body>
<div id="app">
<div class="pages" id="pages">

  <!-- RESUMEN -->
  <div class="page active" id="pg-resumen">
    <div class="greet">
      <div class="hi" id="ghi">Cargando...</div>
      <div class="dt" id="gdt"></div>
    </div>
    <div class="alert" id="alerta"></div>
    <div class="kstrip" id="kstrip"></div>
    <div id="bwrap" style="display:none">
      <div class="bwrap">
        <div class="brow"><span style="color:#7a7d8a">Ingresos del mes</span><span id="bing" style="color:#22c87a;font-weight:600"></span></div>
        <div class="bbar"><div class="bfill" id="bfill" style="width:0%"></div></div>
        <div class="brow"><span style="color:#7a7d8a">Gastos y pagos</span><span id="bgasto" style="color:#f04f4f;font-weight:600"></span></div>
        <div class="bnet"><span class="nl">Flujo neto</span><span class="nv" id="bnet"></span></div>
      </div>
    </div>
    <div class="sec"><div class="stitle">Proximos vencimientos</div><div class="ilist" id="r-prox"></div></div>
    <div class="sec"><div class="stitle">Compromisos fijos</div><div class="ilist" id="r-comp"></div></div>
  </div>

  <!-- INGRESOS -->
  <div class="page" id="pg-ingresos">
    <div class="ph">
      <div><h2>Ingresos</h2><div class="sub" id="s-ing"></div></div>
      <button class="btn-add" onclick="abrirModal('ingreso')">+</button>
    </div>
    <div class="sec"><div class="ilist" id="l-ing"><div class="empty"><div class="emo">💰</div>Sin ingresos aun</div></div></div>
  </div>

  <!-- DEUDAS -->
  <div class="page" id="pg-deudas">
    <div class="ph">
      <div><h2>Deudas</h2><div class="sub" id="s-deu"></div></div>
      <button class="btn-add" onclick="abrirModal('deuda')">+</button>
    </div>
    <div class="sec"><div class="ilist" id="l-deu"><div class="empty"><div class="emo">🏦</div>Sin deudas registradas</div></div></div>
  </div>

  <!-- COBRAR -->
  <div class="page" id="pg-cobrar">
    <div class="ph">
      <div><h2>Por cobrar</h2><div class="sub" id="s-cob"></div></div>
      <button class="btn-add" onclick="abrirModal('cobrar')">+</button>
    </div>
    <div class="sec"><div class="ilist" id="l-cob"><div class="empty"><div class="emo">📥</div>Sin cuentas por cobrar</div></div></div>
  </div>

  <!-- PAGAR -->
  <div class="page" id="pg-pagar">
    <div class="ph">
      <div><h2>Por pagar</h2><div class="sub" id="s-pag"></div></div>
      <button class="btn-add" onclick="abrirModal('pagar')">+</button>
    </div>
    <div class="sec"><div class="ilist" id="l-pag"><div class="empty"><div class="emo">📤</div>Sin cuentas por pagar</div></div></div>
  </div>

  <!-- COMPROMISOS -->
  <div class="page" id="pg-compromisos">
    <div class="ph">
      <div><h2>Compromisos</h2><div class="sub">Pagos fijos recurrentes</div></div>
      <button class="btn-add" onclick="abrirModal('compromiso')">+</button>
    </div>
    <div class="sec"><div class="ilist" id="l-com"><div class="empty"><div class="emo">🔔</div>Sin compromisos</div></div></div>
  </div>

</div><!-- /pages -->

<!-- NAV -->
<nav class="bnav">
  <button class="nitem active" id="n-resumen" onclick="irPag('resumen',this)">
    <svg viewBox="0 0 24 24"><rect x="3" y="3" width="7" height="7" rx="1.5"/><rect x="14" y="3" width="7" height="7" rx="1.5"/><rect x="3" y="14" width="7" height="7" rx="1.5"/><rect x="14" y="14" width="7" height="7" rx="1.5"/></svg>
    Inicio
  </button>
  <button class="nitem" id="n-ingresos" onclick="irPag('ingresos',this)">
    <svg viewBox="0 0 24 24"><polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/><polyline points="17 6 23 6 23 12"/></svg>
    Ingresos
  </button>
  <button class="nitem" id="n-deudas" onclick="irPag('deudas',this)">
    <svg viewBox="0 0 24 24"><rect x="2" y="5" width="20" height="14" rx="2"/><line x1="2" y1="10" x2="22" y2="10"/></svg>
    Deudas
    <div class="ndot" id="nd-deu"></div>
  </button>
  <button class="nitem" id="n-cobrar" onclick="irPag('cobrar',this)">
    <svg viewBox="0 0 24 24"><line x1="12" y1="5" x2="12" y2="19"/><polyline points="19 12 12 19 5 12"/></svg>
    Cobrar
    <div class="ndot" id="nd-cob"></div>
  </button>
  <button class="nitem" id="n-pagar" onclick="irPag('pagar',this)">
    <svg viewBox="0 0 24 24"><line x1="12" y1="19" x2="12" y2="5"/><polyline points="5 12 12 5 19 12"/></svg>
    Pagar
    <div class="ndot" id="nd-pag"></div>
  </button>
  <button class="nitem" id="n-compromisos" onclick="irPag('compromisos',this)">
    <svg viewBox="0 0 24 24"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"/><path d="M13.73 21a2 2 0 0 1-3.46 0"/></svg>
    Fijar
  </button>
</nav>
</div><!-- /app -->

<!-- MODAL -->
<div class="overlay" id="overlay" onclick="cerrarFuera(event)">
  <div class="modal" id="modal">
    <div class="mhandle"></div>
    <h3 id="mtitle"></h3>
    <div id="mbody"></div>
  </div>
</div>

<script>
var D = {ing:[],deu:[],cob:[],pag:[],com:[]};
var KEY = 'mf3';
var mTipo = null, mIdx = null;

function cargar(){ try{ var s=localStorage.getItem(KEY); if(s) D=JSON.parse(s); }catch(e){} }
function guardar(){ try{ localStorage.setItem(KEY,JSON.stringify(D)); }catch(e){} }
cargar();

function fmt(n){ return 'RD$ '+Math.round(Number(n)||0).toLocaleString('es-DO'); }
function fecStr(s){ if(!s) return ''; var d=new Date(s+'T12:00:00'); return d.toLocaleDateString('es-DO',{day:'numeric',month:'short',year:'numeric'}); }
function dias(s){ if(!s) return null; var hoy=new Date(); hoy.setHours(0,0,0,0); var d=new Date(s+'T12:00:00'); return Math.round((d-hoy)/86400000); }
function badge(d){
  if(d===null) return '';
  if(d<0) return '<span class="ibadge br">Vencida</span>';
  if(d===0) return '<span class="ibadge br">Vence hoy</span>';
  if(d<=5) return '<span class="ibadge ba">'+d+'d</span>';
  return '<span class="ibadge bb">'+fecStr('')+'</span>';
}
var EMO={salario:'💼',freelance:'💻',negocio:'🏪','inversion':'📈',alquiler:'🏠',otro:'💰',
  'tarjeta':'💳','prestamo banco':'🏦',hipoteca:'🏠',familiar:'👨‍👩‍👧',otro_deu:'📋',
  prestado:'🤝',servicio:'🔧',proyecto:'📁',otro_cob:'📥',
  renta:'🏠',luz:'💡',agua:'💧',internet:'📶',telefono:'📱',seguros:'🛡️',
  suscripcion:'📺',tarjeta_pag:'💳',otro_pag:'📤',
  mensual:'🔄',anual:'📅',semanal:'📆',otros:'🔔'};
function emo(c,def){ return EMO[c]||def||'💰'; }

function irPag(id,btn){
  document.querySelectorAll('.page').forEach(function(p){p.classList.remove('active');});
  document.querySelectorAll('.nitem').forEach(function(n){n.classList.remove('active');});
  document.getElementById('pg-'+id).classList.add('active');
  btn.classList.add('active');
  renderTodo();
}

/* ---- MODALES ---- */
var FORMS = {
  ingreso:{
    titulo:'Nuevo ingreso',
    html:function(){return '<div class="fg"><label>Descripcion</label><input id="fd" placeholder="Ej: Salario, cliente..."></div>'+
      '<div class="frow"><div class="fg"><label>Monto RD$</label><input id="fm" type="number" inputmode="numeric" placeholder="0"></div>'+
      '<div class="fg"><label>Fecha</label><input id="ff" type="date"></div></div>'+
      '<div class="fg"><label>Tipo</label><select id="fc"><option value="salario">💼 Salario</option><option value="freelance">💻 Freelance</option><option value="negocio">🏪 Negocio</option><option value="inversion">📈 Inversion</option><option value="alquiler">🏠 Alquiler</option><option value="otro">💰 Otro</option></select></div>'+
      '<div class="fg"><label>Nota (opcional)</label><textarea id="fn" rows="2" placeholder="Detalles..."></textarea></div>';},
    guardar:function(){
      var d=gf(['d','m','f','c','n']); if(!d.d||!d.m){alert('Pon descripcion y monto');return;}
      var o={d:d.d,m:parseFloat(d.m),f:d.f,c:d.c,n:d.n};
      if(mIdx!==null) D.ing[mIdx]=o; else D.ing.push(o);
      guardar();cerrarModal();renderTodo();
    }
  },
  deuda:{
    titulo:'Nueva deuda',
    html:function(){return '<div class="fg"><label>Quien / Descripcion</label><input id="fd" placeholder="Ej: Banco BHD..."></div>'+
      '<div class="frow"><div class="fg"><label>Total RD$</label><input id="fm" type="number" inputmode="numeric" placeholder="0"></div>'+
      '<div class="fg"><label>Ya pagado</label><input id="fp" type="number" inputmode="numeric" placeholder="0"></div></div>'+
      '<div class="frow"><div class="fg"><label>Interes %</label><input id="fi" type="number" inputmode="decimal" placeholder="0"></div>'+
      '<div class="fg"><label>Prox. pago</label><input id="ff" type="date"></div></div>'+
      '<div class="fg"><label>Tipo</label><select id="fc"><option value="tarjeta">💳 Tarjeta credito</option><option value="prestamo banco">🏦 Prestamo banco</option><option value="hipoteca">🏠 Hipoteca</option><option value="familiar">👨‍👩‍👧 Familiar</option><option value="otro_deu">📋 Otro</option></select></div>'+
      '<div class="fg"><label>Nota</label><textarea id="fn" rows="2"></textarea></div>';},
    guardar:function(){
      var d=gf(['d','m','p','i','f','c','n']); if(!d.d||!d.m){alert('Pon descripcion y monto');return;}
      var o={d:d.d,m:parseFloat(d.m),p:parseFloat(d.p||0),i:parseFloat(d.i||0),f:d.f,c:d.c,n:d.n};
      if(mIdx!==null) D.deu[mIdx]=o; else D.deu.push(o);
      guardar();cerrarModal();renderTodo();
    }
  },
  cobrar:{
    titulo:'Cuenta por cobrar',
    html:function(){return '<div class="fg"><label>Quien te debe</label><input id="fd" placeholder="Nombre o empresa..."></div>'+
      '<div class="frow"><div class="fg"><label>Monto RD$</label><input id="fm" type="number" inputmode="numeric" placeholder="0"></div>'+
      '<div class="fg"><label>Fecha limite</label><input id="ff" type="date"></div></div>'+
      '<div class="fg"><label>Tipo</label><select id="fc"><option value="prestado">🤝 Dinero prestado</option><option value="servicio">🔧 Servicio prestado</option><option value="proyecto">📁 Proyecto</option><option value="otro_cob">📥 Otro</option></select></div>'+
      '<div class="fg"><label>Nota</label><textarea id="fn" rows="2"></textarea></div>';},
    guardar:function(){
      var d=gf(['d','m','f','c','n']); if(!d.d||!d.m){alert('Pon descripcion y monto');return;}
      var o={d:d.d,m:parseFloat(d.m),f:d.f,c:d.c,n:d.n};
      if(mIdx!==null) D.cob[mIdx]=o; else D.cob.push(o);
      guardar();cerrarModal();renderTodo();
    }
  },
  pagar:{
    titulo:'Cuenta por pagar',
    html:function(){return '<div class="fg"><label>A quien le pagas</label><input id="fd" placeholder="Empresa, persona..."></div>'+
      '<div class="frow"><div class="fg"><label>Monto RD$</label><input id="fm" type="number" inputmode="numeric" placeholder="0"></div>'+
      '<div class="fg"><label>Fecha limite</label><input id="ff" type="date"></div></div>'+
      '<div class="fg"><label>Tipo</label><select id="fc"><option value="renta">🏠 Renta</option><option value="luz">💡 Electricidad</option><option value="agua">💧 Agua</option><option value="internet">📶 Internet</option><option value="telefono">📱 Telefono</option><option value="seguros">🛡️ Seguros</option><option value="suscripcion">📺 Suscripcion</option><option value="tarjeta_pag">💳 Tarjeta</option><option value="otro_pag">📤 Otro</option></select></div>'+
      '<div class="fg"><label>Nota</label><textarea id="fn" rows="2"></textarea></div>';},
    guardar:function(){
      var d=gf(['d','m','f','c','n']); if(!d.d||!d.m){alert('Pon descripcion y monto');return;}
      var o={d:d.d,m:parseFloat(d.m),f:d.f,c:d.c,n:d.n};
      if(mIdx!==null) D.pag[mIdx]=o; else D.pag.push(o);
      guardar();cerrarModal();renderTodo();
    }
  },
  compromiso:{
    titulo:'Compromiso fijo',
    html:function(){return '<div class="fg"><label>Descripcion</label><input id="fd" placeholder="Ej: Renta, Gimnasio..."></div>'+
      '<div class="frow"><div class="fg"><label>Monto RD$</label><input id="fm" type="number" inputmode="numeric" placeholder="0"></div>'+
      '<div class="fg"><label>Dia del mes</label><input id="fdia" type="number" inputmode="numeric" min="1" max="31" placeholder="1-31"></div></div>'+
      '<div class="fg"><label>Frecuencia</label><select id="fc"><option value="mensual">🔄 Mensual</option><option value="anual">📅 Anual</option><option value="semanal">📆 Semanal</option><option value="otros">🔔 Otro</option></select></div>'+
      '<div class="fg"><label>Nota</label><textarea id="fn" rows="2"></textarea></div>';},
    guardar:function(){
      var d=gf(['d','m','dia','c','n']); if(!d.d||!d.m){alert('Pon descripcion y monto');return;}
      var o={d:d.d,m:parseFloat(d.m),dia:parseInt(d.dia||1),c:d.c,n:d.n};
      if(mIdx!==null) D.com[mIdx]=o; else D.com.push(o);
      guardar();cerrarModal();renderTodo();
    }
  }
};

function gf(arr){
  var r={};
  arr.forEach(function(k){
    var el=document.getElementById('f'+k);
    if(el) r[k]=el.value.trim();
  });
  return r;
}

function abrirModal(tipo,idx){
  mTipo=tipo; mIdx=(idx!==undefined)?idx:null;
  var cfg=FORMS[tipo];
  document.getElementById('mtitle').textContent=cfg.titulo;
  document.getElementById('mbody').innerHTML=cfg.html()+
    '<button class="bsave" onclick="FORMS[\''+tipo+'\'].guardar()">Guardar</button>'+
    '<button class="bcancel" onclick="cerrarModal()">Cancelar</button>';
  var hoy=new Date().toISOString().split('T')[0];
  var ff=document.getElementById('ff'); if(ff) ff.value=hoy;
  if(mIdx!==null){
    var arr={ingreso:'ing',deuda:'deu',cobrar:'cob',pagar:'pag',compromiso:'com'}[tipo];
    var obj=D[arr][mIdx];
    if(obj){
      var map={d:'fd',m:'fm',f:'ff',c:'fc',n:'fn',p:'fp',i:'fi',dia:'fdia'};
      Object.keys(map).forEach(function(k){
        var el=document.getElementById(map[k]);
        if(el&&obj[k]!==undefined) el.value=obj[k];
      });
    }
  }
  document.getElementById('overlay').classList.add('on');
}
function cerrarModal(){ document.getElementById('overlay').classList.remove('on'); mTipo=null; mIdx=null; }
function cerrarFuera(e){ if(e.target===document.getElementById('overlay')) cerrarModal(); }

function borrar(arr,idx){ if(confirm('Eliminar este registro?')){ D[arr].splice(idx,1); guardar(); renderTodo(); } }

/* ---- RENDER ---- */
function renderTodo(){
  renderResumen(); renderIng(); renderDeu(); renderCob(); renderPag(); renderCom(); puntos();
}

function renderResumen(){
  var h=new Date().getHours();
  document.getElementById('ghi').textContent= h<12?'Buenos dias 👋': h<18?'Buenas tardes 👋':'Buenas noches 👋';
  document.getElementById('gdt').textContent=new Date().toLocaleDateString('es-DO',{weekday:'long',day:'numeric',month:'long'});

  var ti=D.ing.reduce(function(a,x){return a+x.m;},0);
  var td=D.deu.reduce(function(a,x){return a+(x.m-x.p);},0);
  var tc=D.cob.reduce(function(a,x){return a+x.m;},0);
  var tp=D.pag.reduce(function(a,x){return a+x.m;},0);
  var tco=D.com.reduce(function(a,x){return a+x.m;},0);
  var gas=tp+tco;
  var net=ti-gas;

  document.getElementById('kstrip').innerHTML=
    kc('📈','Ingresos',ti,'g')+kc('🏦','Deudas',td,'r')+kc('📥','Por cobrar',tc,'b')+kc('📤','Por pagar',tp,'a');

  var bw=document.getElementById('bwrap');
  if(ti>0||gas>0){
    bw.style.display='block';
    var pct=ti>0?Math.min(100,Math.round(gas/ti*100)):100;
    document.getElementById('bing').textContent=fmt(ti);
    document.getElementById('bfill').style.width=pct+'%';
    document.getElementById('bgasto').textContent=fmt(gas);
    var ne=document.getElementById('bnet');
    ne.textContent=(net<0?'-':'')+fmt(Math.abs(net));
    ne.style.color=net>=0?'#22c87a':'#f04f4f';
  } else { bw.style.display='none'; }

  // Alerta
  var venc=D.pag.filter(function(p){var d=dias(p.f);return d!==null&&d<=0;});
  var pron=D.pag.filter(function(p){var d=dias(p.f);return d!==null&&d>0&&d<=3;});
  var al=document.getElementById('alerta');
  if(venc.length){ al.className='alert on'; al.textContent='⚠️ Tienes '+venc.length+' pago(s) vencido(s)'; }
  else if(pron.length){ al.className='alert on'; al.style.background='rgba(240,160,48,0.1)'; al.style.borderColor='rgba(240,160,48,0.22)'; al.style.color='#f0a030'; al.textContent='⏰ '+pron.length+' pago(s) vencen en 3 dias'; }
  else { al.className='alert'; }

  // Proximos
  var todo=[]; 
  D.pag.forEach(function(x,i){ todo.push({x:x,tipo:'pag',i:i}); });
  D.cob.forEach(function(x,i){ todo.push({x:x,tipo:'cob',i:i}); });
  todo=todo.filter(function(t){return t.x.f;}).sort(function(a,b){return dias(a.x.f)-dias(b.x.f);}).slice(0,4);
  var rp=document.getElementById('r-prox');
  if(!todo.length){ rp.innerHTML='<div class="empty" style="padding:14px"><div class="emo" style="font-size:26px">📅</div>Sin vencimientos proximos</div>'; }
  else { rp.innerHTML=todo.map(function(t){
    var col=t.tipo==='pag'?'r':'b'; var amtcol=t.tipo==='pag'?'r':'b';
    var d=dias(t.x.f);
    var b=badge(d);
    return '<div class="item"><div class="iico '+col+'">'+emo(t.x.c,t.tipo==='pag'?'📤':'📥')+'</div>'+
      '<div class="ibody"><div class="iname">'+t.x.d+'</div><div class="isub">'+fecStr(t.x.f)+'</div></div>'+
      '<div class="iright"><div class="iamt '+amtcol+'">'+fmt(t.x.m)+'</div>'+b+'</div></div>';
  }).join('');}

  // Compromisos
  var hoyN=new Date().getDate();
  var rc=document.getElementById('r-comp');
  if(!D.com.length){ rc.innerHTML='<div class="empty" style="padding:14px"><div class="emo" style="font-size:26px">🔔</div>Sin compromisos fijos</div>'; }
  else { rc.innerHTML=D.com.slice(0,4).map(function(c){
    var diff=c.dia-hoyN;
    var b=diff<=0?'<span class="ibadge bg">Pagado este mes</span>':diff<=5?'<span class="ibadge ba">En '+diff+'d</span>':'<span class="ibadge bb">Dia '+c.dia+'</span>';
    return '<div class="item"><div class="iico p">'+emo(c.c,'🔔')+'</div>'+
      '<div class="ibody"><div class="iname">'+c.d+'</div><div class="isub">'+c.c+' · Dia '+c.dia+'</div></div>'+
      '<div class="iright"><div class="iamt a">'+fmt(c.m)+'</div>'+b+'</div></div>';
  }).join('');}
}

function kc(e,l,v,cls){
  return '<div class="kcard"><div class="kl">'+e+' '+l+'</div><div class="kv '+cls+'">'+fmt(v)+'</div></div>';
}

function renderIng(){
  var el=document.getElementById('l-ing');
  var t=D.ing.reduce(function(a,x){return a+x.m;},0);
  document.getElementById('s-ing').textContent=D.ing.length?'Total: '+fmt(t):'';
  if(!D.ing.length){el.innerHTML='<div class="empty"><div class="emo">💰</div>Sin ingresos aun</div>';return;}
  el.innerHTML=D.ing.slice().reverse().map(function(it,ri){
    var idx=D.ing.length-1-ri;
    return '<div class="item" onclick="abrirModal(\'ingreso\','+idx+')">'+
      '<div class="iico g">'+emo(it.c,'💰')+'</div>'+
      '<div class="ibody"><div class="iname">'+it.d+'</div><div class="isub">'+fecStr(it.f)+(it.n?' · '+it.n:'')+'</div></div>'+
      '<div class="iright"><div class="iamt g">+'+fmt(it.m)+'</div><span class="ibadge bg">'+it.c+'</span></div>'+
      '<button class="idel" onclick="event.stopPropagation();borrar(\'ing\','+idx+')">✕</button></div>';
  }).join('');
}

function renderDeu(){
  var el=document.getElementById('l-deu');
  var t=D.deu.reduce(function(a,x){return a+(x.m-x.p);},0);
  document.getElementById('s-deu').textContent=D.deu.length?'Pendiente: '+fmt(t):'';
  if(!D.deu.length){el.innerHTML='<div class="empty"><div class="emo">🏦</div>Sin deudas</div>';return;}
  el.innerHTML=D.deu.map(function(it,idx){
    var pend=it.m-it.p;
    var pct=it.m>0?Math.round(it.p/it.m*100):0;
    var b=it.f?badge(dias(it.f)):'';
    return '<div class="item" style="display:block;cursor:pointer" onclick="abrirModal(\'deuda\','+idx+')">'+
      '<div style="display:-webkit-flex;display:flex;-webkit-align-items:center;align-items:center;gap:11px">'+
      '<div class="iico r">'+emo(it.c,'🏦')+'</div>'+
      '<div class="ibody"><div class="iname">'+it.d+'</div><div class="isub">'+(it.i>0?'Interes '+it.i+'%':'')+(it.n?' · '+it.n:'')+'</div></div>'+
      '<div class="iright"><div class="iamt r">-'+fmt(pend)+'</div>'+b+'</div>'+
      '<button class="idel" onclick="event.stopPropagation();borrar(\'deu\','+idx+')" style="display:-webkit-flex;display:flex">✕</button></div>'+
      '<div class="dprog"><div class="dprow"><span>Pagado '+fmt(it.p)+' ('+pct+'%)</span><span>Total '+fmt(it.m)+'</span></div>'+
      '<div class="dpbar"><div class="dpfill" style="width:'+pct+'%"></div></div></div></div>';
  }).join('');
}

function renderCob(){
  var el=document.getElementById('l-cob');
  var t=D.cob.reduce(function(a,x){return a+x.m;},0);
  document.getElementById('s-cob').textContent=D.cob.length?'Por cobrar: '+fmt(t):'';
  if(!D.cob.length){el.innerHTML='<div class="empty"><div class="emo">📥</div>Sin cuentas por cobrar</div>';return;}
  el.innerHTML=D.cob.map(function(it,idx){
    var b=it.f?badge(dias(it.f)):'<span class="ibadge bb">Sin fecha</span>';
    return '<div class="item" onclick="abrirModal(\'cobrar\','+idx+')">'+
      '<div class="iico b">'+emo(it.c,'📥')+'</div>'+
      '<div class="ibody"><div class="iname">'+it.d+'</div><div class="isub">'+fecStr(it.f)+(it.n?' · '+it.n:'')+'</div></div>'+
      '<div class="iright"><div class="iamt b">+'+fmt(it.m)+'</div>'+b+'</div>'+
      '<button class="idel" onclick="event.stopPropagation();borrar(\'cob\','+idx+')">✕</button></div>';
  }).join('');
}

function renderPag(){
  var el=document.getElementById('l-pag');
  var t=D.pag.reduce(function(a,x){return a+x.m;},0);
  document.getElementById('s-pag').textContent=D.pag.length?'Por pagar: '+fmt(t):'';
  if(!D.pag.length){el.innerHTML='<div class="empty"><div class="emo">📤</div>Sin cuentas por pagar</div>';return;}
  el.innerHTML=D.pag.map(function(it,idx){
    var b=it.f?badge(dias(it.f)):'';
    return '<div class="item" onclick="abrirModal(\'pagar\','+idx+')">'+
      '<div class="iico a">'+emo(it.c,'📤')+'</div>'+
      '<div class="ibody"><div class="iname">'+it.d+'</div><div class="isub">'+fecStr(it.f)+(it.n?' · '+it.n:'')+'</div></div>'+
      '<div class="iright"><div class="iamt r">-'+fmt(it.m)+'</div>'+b+'</div>'+
      '<button class="idel" onclick="event.stopPropagation();borrar(\'pag\','+idx+')">✕</button></div>';
  }).join('');
}

function renderCom(){
  var el=document.getElementById('l-com');
  if(!D.com.length){el.innerHTML='<div class="empty"><div class="emo">🔔</div>Sin compromisos</div>';return;}
  var hoy=new Date().getDate();
  el.innerHTML=D.com.slice().sort(function(a,b){return a.dia-b.dia;}).map(function(it,si){
    var idx=D.com.indexOf(it);
    var diff=it.dia-hoy;
    var b=diff<0?'<span class="ibadge bg">Este mes ✓</span>':diff===0?'<span class="ibadge br">Hoy</span>':diff<=5?'<span class="ibadge ba">En '+diff+'d</span>':'<span class="ibadge bb">Dia '+it.dia+'</span>';
    return '<div class="item" onclick="abrirModal(\'compromiso\','+idx+')">'+
      '<div class="iico p">'+emo(it.c,'🔔')+'</div>'+
      '<div class="ibody"><div class="iname">'+it.d+'</div><div class="isub">'+it.c+' · Cada dia '+it.dia+(it.n?' · '+it.n:'')+'</div></div>'+
      '<div class="iright"><div class="iamt a">'+fmt(it.m)+'</div>'+b+'</div>'+
      '<button class="idel" onclick="event.stopPropagation();borrar(\'com\','+idx+')">✕</button></div>';
  }).join('');
}

function puntos(){
  var dv=D.deu.some(function(x){return x.f&&dias(x.f)!==null&&dias(x.f)<=0;});
  document.getElementById('nd-deu').className='ndot'+(dv?' on':'');
  var cv=D.cob.some(function(x){return x.f&&dias(x.f)!==null&&dias(x.f)<=0;});
  document.getElementById('nd-cob').className='ndot'+(cv?' on':'');
  var pv=D.pag.some(function(x){return x.f&&dias(x.f)!==null&&dias(x.f)<=3;});
  document.getElementById('nd-pag').className='ndot'+(pv?' on':'');
}

renderTodo();
</script>
</body>
</html>
