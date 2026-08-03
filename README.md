<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, viewport-fit=cover">
<title>Pucón 2026</title>

<!-- iOS: abrir en modo standalone (sin barra de Safari) al agregar a pantalla de inicio -->
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="Pucón 2026">
<link rel="apple-touch-icon" href="apple-touch-icon.png">

<!-- Android/Chrome equivalent -->
<meta name="mobile-web-app-capable" content="yes">
<meta name="theme-color" content="#0f1618">
<style>
@import url('https://fonts.googleapis.com/css2?family=Fjalla+One&family=Inter:wght@400;500;600;700&display=swap');

:root{
  --bg:#0f1618;
  --bg-elev:#182225;
  --bg-elev-2:#1f2b2e;
  --line:#2a3b3d;
  --ember:#e2572a;
  --ember-soft:rgba(226,87,42,0.14);
  --glacial:#4fb3a6;
  --glacial-soft:rgba(79,179,166,0.14);
  --gold:#d9a441;
  --gold-soft:rgba(217,164,65,0.14);
  --text:#f3efe6;
  --text-dim:#93a4a3;
  --text-faint:#5f7274;
}

*{box-sizing:border-box; -webkit-tap-highlight-color:transparent;}
html,body{margin:0;padding:0;}
body{
  background:var(--bg);
  color:var(--text);
  font-family:'Inter',sans-serif;
  min-height:100vh;
  padding-bottom:calc(40px + env(safe-area-inset-bottom));
}

/* HERO */
.hero{
  position:relative;
  padding:calc(28px + env(safe-area-inset-top)) 20px 22px;
  overflow:hidden;
  border-bottom:1px solid var(--line);
  background:
    radial-gradient(ellipse at 20% 0%, rgba(226,87,42,0.10), transparent 55%),
    radial-gradient(ellipse at 85% 10%, rgba(79,179,166,0.10), transparent 50%),
    var(--bg);
}
.hero svg.range{
  position:absolute;
  left:0; right:0; bottom:-2px;
  width:100%; height:64px;
  opacity:0.9;
}
.eyebrow{
  font-size:11px;
  letter-spacing:0.16em;
  text-transform:uppercase;
  color:var(--glacial);
  font-weight:600;
  margin:0 0 6px;
}
h1.title{
  font-family:'Fjalla One',sans-serif;
  font-weight:400;
  font-size:44px;
  letter-spacing:0.01em;
  line-height:0.95;
  margin:0 0 8px;
  color:var(--text);
}
h1.title span{color:var(--ember);}
.hero-cta{
  display:inline-flex;
  align-items:center;
  gap:6px;
  font-size:12.5px;
  font-weight:600;
  color:var(--text);
  background:var(--bg-elev);
  border:1px solid var(--line);
  padding:7px 12px;
  border-radius:20px;
  cursor:pointer;
  position:relative;
  z-index:2;
}
.hero-cta:active{background:var(--bg-elev-2);}
.hero-ctas{
  display:flex;
  flex-wrap:wrap;
  gap:8px;
  position:relative;
  z-index:2;
}

/* DAY RAIL */
.rail-wrap{
  position:sticky; top:0; z-index:20;
  padding-top:env(safe-area-inset-top);
  background:rgba(15,22,24,0.94);
  backdrop-filter:blur(8px);
  border-bottom:1px solid var(--line);
}
.rail{
  display:flex;
  gap:8px;
  overflow-x:auto;
  padding:12px 16px;
  scrollbar-width:none;
}
.rail::-webkit-scrollbar{display:none;}
.day-pill{
  flex:0 0 auto;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  width:58px;
  padding:8px 4px 7px;
  border-radius:12px;
  border:1px solid var(--line);
  background:var(--bg-elev);
  cursor:pointer;
  transition:border-color .15s, background .15s, transform .1s;
  user-select:none;
}
.day-pill:active{transform:scale(0.96);}
.day-pill .num{
  font-family:'Fjalla One',sans-serif;
  font-size:20px;
  line-height:1;
  color:var(--text);
}
.day-pill .dow{
  font-size:9px;
  text-transform:uppercase;
  letter-spacing:0.05em;
  color:var(--text-faint);
  margin-top:3px;
}
.day-pill .dot{
  width:5px;height:5px;border-radius:50%;
  background:var(--text-faint);
  margin-top:5px;
}
.day-pill.active{
  background:var(--ember-soft);
  border-color:var(--ember);
}
.day-pill.active .num{color:var(--ember);}
.day-pill.active .dot{background:var(--ember);}

/* DAY HEADER */
.day-panel{display:none; padding:22px 18px 8px;}
.day-panel.active{display:block; animation:fade .25s ease;}
@keyframes fade{from{opacity:0; transform:translateY(4px);} to{opacity:1; transform:translateY(0);}}

.day-head{
  display:flex;
  align-items:baseline;
  justify-content:space-between;
  margin-bottom:4px;
}
.day-head h2{
  font-family:'Fjalla One',sans-serif;
  font-weight:400;
  font-size:24px;
  margin:0;
  color:var(--text);
}
.day-tag{
  font-size:10.5px;
  text-transform:uppercase;
  letter-spacing:0.08em;
  font-weight:600;
  color:var(--bg);
  background:var(--glacial);
  padding:4px 9px;
  border-radius:20px;
  white-space:nowrap;
}
.day-tag.ember{background:var(--ember);}
.day-loc{
  font-size:13px;
  color:var(--text-dim);
  margin:2px 0 22px;
}

/* TIMELINE */
.timeline{
  position:relative;
  padding-left:26px;
}
.timeline::before{
  content:"";
  position:absolute;
  left:7px; top:6px; bottom:6px;
  width:2px;
  background:repeating-linear-gradient(to bottom, var(--line) 0 6px, transparent 6px 11px);
}
.item{
  position:relative;
  margin-bottom:18px;
}
.item::before{
  content:"";
  position:absolute;
  left:-26px; top:3px;
  width:14px; height:14px;
  border-radius:50%;
  background:var(--bg-elev-2);
  border:2px solid var(--glacial);
}
.item.ember::before{border-color:var(--ember);}
.item-card{
  background:var(--bg-elev);
  border:1px solid var(--line);
  border-radius:12px;
  padding:12px 14px;
  cursor:pointer;
  transition:border-color .15s, background .15s;
}
.item-card:active{background:var(--bg-elev-2);}
.item-card:hover{border-color:var(--text-faint);}
.item-top{
  display:flex;
  align-items:flex-start;
  gap:10px;
}
.item-icon{font-size:18px; line-height:1.3;}
.item-body{flex:1; min-width:0;}
.item-title-row{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:8px;
}
.item-title{
  font-size:14.5px;
  font-weight:600;
  color:var(--text);
  margin:0 0 2px;
}
.info-chip{
  flex:0 0 auto;
  width:19px;height:19px;
  border-radius:50%;
  border:1px solid var(--text-faint);
  color:var(--text-faint);
  font-size:11px;
  font-weight:700;
  display:flex;
  align-items:center;
  justify-content:center;
}
.item-meta{
  font-size:12px;
  color:var(--gold);
  font-weight:500;
  margin:0 0 2px;
}
.item-note{
  font-size:12.5px;
  color:var(--text-dim);
  margin:2px 0 0;
  line-height:1.4;
}
.maps-link{
  display:inline-flex;
  align-items:center;
  gap:4px;
  font-size:11px;
  font-weight:600;
  color:var(--glacial);
  text-decoration:none;
  background:var(--glacial-soft);
  border:1px solid rgba(79,179,166,0.35);
  padding:4px 9px;
  border-radius:20px;
  margin-top:8px;
  position:relative;
  z-index:2;
}
.maps-link:active{background:rgba(79,179,166,0.28);}
.sublist{
  list-style:none;
  margin:8px 0 0;
  padding:0 0 0 4px;
  border-top:1px dashed var(--line);
  padding-top:8px;
  position:relative;
  z-index:2;
}
.sublist li{
  font-size:12.5px;
  color:var(--text-dim);
  padding:2px 0 2px 14px;
  position:relative;
  display:flex;
  align-items:center;
  gap:6px;
  justify-content:space-between;
}
.sublist li::before{
  content:"";
  position:absolute;
  left:0; top:9px;
  width:5px; height:5px;
  border-radius:50%;
  background:var(--glacial);
}
.sublist li span.sub-name{flex:1;}
.sub-pin{
  flex:0 0 auto;
  font-size:13px;
  text-decoration:none;
  opacity:0.85;
  padding:3px 6px;
}

.group-row{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:10px;
  margin-top:2px;
}
.group-box{
  background:var(--bg-elev);
  border:1px solid var(--line);
  border-radius:12px;
  padding:11px 12px;
  cursor:pointer;
  transition:border-color .15s, background .15s;
}
.group-box:active{background:var(--bg-elev-2);}
.group-label{
  font-size:10px;
  text-transform:uppercase;
  letter-spacing:0.06em;
  color:var(--text-faint);
  font-weight:700;
  margin:0 0 6px;
}
.group-box .item-title{font-size:13.5px;}

.day-nav{
  display:flex;
  justify-content:space-between;
  gap:10px;
  margin:26px 0 4px;
}
.nav-btn{
  flex:1;
  text-align:center;
  padding:12px;
  border-radius:12px;
  background:var(--bg-elev);
  border:1px solid var(--line);
  color:var(--text-dim);
  font-size:13px;
  font-weight:600;
  cursor:pointer;
}
.nav-btn:active{background:var(--bg-elev-2);}
.nav-btn.disabled{opacity:0.35; pointer-events:none;}

/* MODAL */
.overlay{
  position:fixed; inset:0;
  background:rgba(6,10,11,0.72);
  backdrop-filter:blur(2px);
  display:none;
  align-items:flex-end;
  justify-content:center;
  z-index:100;
}
.overlay.open{display:flex; animation:fadeBg .18s ease;}
@keyframes fadeBg{from{opacity:0;} to{opacity:1;}}
.sheet{
  width:100%;
  max-width:480px;
  max-height:82vh;
  overflow-y:auto;
  background:var(--bg-elev);
  border:1px solid var(--line);
  border-bottom:none;
  border-radius:20px 20px 0 0;
  padding:10px 20px calc(28px + env(safe-area-inset-bottom));
  animation:slideUp .22s ease;
}
@media (min-width:520px){
  .overlay{align-items:center;}
  .sheet{border-radius:18px; border-bottom:1px solid var(--line); max-height:80vh;}
}
@keyframes slideUp{from{transform:translateY(24px); opacity:0;} to{transform:translateY(0); opacity:1;}}
.sheet-handle{
  width:36px; height:4px; border-radius:3px;
  background:var(--line);
  margin:6px auto 14px;
}
.sheet-head{
  display:flex; align-items:flex-start; gap:12px;
  margin-bottom:6px;
}
.sheet-icon{
  font-size:26px;
  flex:0 0 auto;
}
.sheet-title{
  font-family:'Fjalla One',sans-serif;
  font-weight:400;
  font-size:21px;
  margin:0 0 3px;
  color:var(--text);
}
.sheet-meta{
  font-size:12.5px;
  color:var(--gold);
  font-weight:600;
  margin:0;
}
.sheet-close{
  flex:0 0 auto;
  width:28px; height:28px;
  border-radius:50%;
  background:var(--bg-elev-2);
  border:1px solid var(--line);
  color:var(--text-dim);
  font-size:14px;
  display:flex; align-items:center; justify-content:center;
  cursor:pointer;
}
.sheet-note{
  font-size:13px;
  color:var(--text-dim);
  margin:10px 0 0;
  line-height:1.5;
}
.sheet-maps{
  display:inline-flex;
  align-items:center;
  gap:6px;
  font-size:12.5px;
  font-weight:600;
  color:var(--bg);
  background:var(--glacial);
  text-decoration:none;
  padding:8px 14px;
  border-radius:20px;
  margin-top:12px;
}
.sheet-section{margin-top:18px;}
.sheet-section-title{
  font-size:10.5px;
  text-transform:uppercase;
  letter-spacing:0.08em;
  font-weight:700;
  color:var(--glacial);
  margin:0 0 8px;
}
.sheet-section-title.warn{color:var(--ember);}
.sheet-section-title.outfit{color:var(--gold);}
.tip-list{list-style:none; margin:0; padding:0;}
.tip-list li{
  font-size:13.5px;
  color:var(--text);
  line-height:1.45;
  padding:6px 0 6px 20px;
  position:relative;
  border-bottom:1px solid var(--line);
}
.tip-list li:last-child{border-bottom:none;}
.tip-list li::before{
  content:"›";
  position:absolute; left:2px; top:6px;
  color:var(--glacial);
  font-weight:700;
}
.steps-list{list-style:none; counter-reset:step; margin:0; padding:0;}
.steps-list li{
  font-size:13.5px;
  color:var(--text);
  line-height:1.45;
  padding:5px 0 15px 30px;
  position:relative;
  counter-increment:step;
}
.steps-list li::before{
  content:counter(step);
  position:absolute; left:0; top:3px;
  width:20px; height:20px;
  border-radius:50%;
  background:var(--glacial-soft);
  color:var(--glacial);
  font-size:11px;
  font-weight:700;
  display:flex; align-items:center; justify-content:center;
}
.pack-list{list-style:none; margin:0; padding:0; display:flex; flex-wrap:wrap; gap:7px;}
.pack-list li{
  font-size:12.5px;
  color:var(--text);
  background:var(--glacial-soft);
  border:1px solid rgba(79,179,166,0.35);
  padding:5px 10px;
  border-radius:20px;
}
.outfit-list{list-style:none; margin:0; padding:0; display:flex; flex-wrap:wrap; gap:7px;}
.outfit-list li{
  font-size:12.5px;
  color:var(--text);
  background:var(--gold-soft);
  border:1px solid rgba(217,164,65,0.4);
  padding:5px 10px;
  border-radius:20px;
}
.place-list{list-style:none; margin:0; padding:0;}
.place-list li{
  display:flex; align-items:center; justify-content:space-between;
  font-size:13px; color:var(--text);
  padding:7px 0;
  border-bottom:1px solid var(--line);
}
.place-list li:last-child{border-bottom:none;}
.place-pin{
  font-size:12px; color:var(--glacial); text-decoration:none; font-weight:600;
  white-space:nowrap;
}
.no-info{
  font-size:13px;
  color:var(--text-faint);
  padding:14px 0 4px;
}
.notes-list{list-style:none; margin:0; padding:0; display:flex; flex-direction:column; gap:8px;}
.notes-row{
  display:flex;
  align-items:center;
  gap:10px;
  background:var(--bg-elev-2);
  border:1px solid var(--line);
  border-radius:12px;
  padding:11px 12px;
  text-decoration:none;
  color:var(--text);
}
.notes-row:active{border-color:var(--text-faint);}
.notes-icon{font-size:18px; flex:0 0 auto;}
.notes-title{flex:1; min-width:0; font-size:13.5px; font-weight:600;}
.notes-arrow{flex:0 0 auto; color:var(--glacial); font-size:14px;}
</style>
</head>
<body>

<div class="hero">
  <p class="eyebrow">7 – 16 de agosto</p>
  <h1 class="title">Puc<span>ó</span>n 2026</h1>
  <div class="hero-ctas">
    <button class="hero-cta" onclick="openGeneralInfo()">🎒 Esenciales del viaje</button>
    <button class="hero-cta" onclick="openNotesInfo()">📎 Notas y documentos</button>
    <button class="hero-cta" onclick="openInstallInfo()">📲 Cómo instalar</button>
  </div>
  <svg class="range" viewBox="0 0 400 64" preserveAspectRatio="none">
    <polyline points="0,64 30,64 55,30 75,50 100,15 125,45 150,25 175,55 200,20 225,48 250,10 275,40 300,55 325,35 350,58 400,64"
      fill="none" stroke="#2a3b3d" stroke-width="2"/>
    <polyline points="0,64 55,30 100,15 150,25 200,20 250,10 300,55 400,64" fill="none" stroke="#e2572a" stroke-width="1.5" opacity="0.55"/>
  </svg>
</div>

<div class="rail-wrap">
  <div class="rail" id="rail"></div>
</div>

<div id="panels"></div>

<div class="overlay" id="overlay">
  <div class="sheet" id="sheet"></div>
</div>

<script>
const DAYS = [
  {
    dow:"Viernes", num:7, loc:"Vuelo Montevideo → Santiago", tag:"Vuelo", tagClass:"ember",
    items:[
      {icon:"✈️", title:"Vuelo Montevideo → Santiago", meta:"19:15 – 20:55 hs", ember:true,
        maps:"Aeropuerto Internacional Arturo Merino Benítez, Santiago, Chile",
        tips:["Check-in online y descargar el boarding pass con anticipación.","Llegar al aeropuerto con margen (vuelo internacional).","Tener a mano cédula/pasaporte vigente."],
        pack:["Documento de identidad","Cargador y power bank"],
        outfit:["Ropa cómoda y en capas para el avión"]},
      {icon:"🚗", title:"Retirar auto", note:"Rent a car en el aeropuerto de Santiago",
        maps:"Arriendo de autos Aeropuerto Arturo Merino Benítez, Santiago, Chile",
        tips:["Llevar la reserva (impresa o en el celular), la licencia de conducir y la tarjeta con la que se pagó.","Revisar el auto y sacar fotos del estado antes de salir del estacionamiento.","Confirmar tipo de combustible y política de devolución del tanque."],
        pack:["Licencia de conducir","Tarjeta de la reserva","Reserva del auto (impresa o digital)"]},
      {icon:"🏠", title:"Check-in apartamento", ember:true,
        note:"Av. Pedro de Valdivia 150, 7500000 Santiago, Chile · Tel: +56 9 6606 1427",
        maps:"Av. Pedro de Valdivia 150, Santiago, Chile",
        tips:["Coordinar el horario de llegada con anticipación, sobre todo si es de noche.","Guardar el contacto y la dirección descargados por si no hay señal.","Confirmar el método de entrega de llaves (portero, caja de seguridad, etc.)."]},
      {icon:"🍽️", title:"Comer y tomar algo", note:"VIP del aeropuerto",
        tips:["Confirmar si el acceso al VIP es por tarjeta, membresía o pase pago.","Suele cerrar el ingreso un rato antes del embarque, no quedarse mucho tiempo."]},
      {icon:"🍸", title:"Restaurant o bar",
        tips:["Ya en Santiago, un viernes de noche puede tener espera — conviene reservar si se puede."]}
    ]
  },
  {
    dow:"Sábado", num:8, loc:"Santiago", tag:"Ciudad",
    items:[
      {icon:"🥐", title:"Desayuno express",
        tips:["Día con varias paradas — arrancar liviano y con tiempo para no atrasar el resto."]},
      {icon:"🕌", title:"Templo Bahá'í", meta:"09:00 hs",
        maps:"Templo Bahá'í de Santiago, Chile",
        tips:["Queda alejado del centro, en la precordillera — sumar tiempo de traslado.","Es un espacio de silencio y contemplación: hablar bajo, sin comida ni bebida adentro.","Entrada gratuita."],
        outfit:["Hombros y rodillas cubiertos","Calzado cómodo (hay caminata desde el estacionamiento)"]},
      {icon:"🍽️", title:"Barrio Lastarria", note:"Almuerzo",
        maps:"Barrio Lastarria, Santiago, Chile",
        tips:["Zona linda para caminar antes o después de comer.","Fin de semana al mediodía puede tener espera en los lugares más pedidos."]},
      {icon:"🚡", title:"Teleférico San Cristóbal",
        maps:"Teleférico Metropolitano de Santiago, San Cristóbal, Chile",
        tips:["Comprar entrada online para evitar filas largas.","Arriba refresca y hay viento, aunque abajo haga calor."],
        outfit:["Campera liviana"],
        pack:["Cámara / celular cargado para las vistas"]},
      {icon:"🛍️", title:"Shopping Costanera",
        maps:"Costanera Center, Santiago, Chile",
        tips:["Si van a comprar algo grande, dejarlo para el final del día por el peso."]},
      {icon:"🌇", title:"Sunset Sky Costanera",
        maps:"Sky Costanera, Santiago, Chile",
        tips:["El mirador del atardecer suele tener costo aparte y horario limitado — chequear apertura y última entrada.","Arriba hace bastante más frío que a nivel calle."],
        outfit:["Abrigo (hace frío al atardecer en altura)"]}
    ]
  },
  {
    dow:"Domingo", num:9, loc:"Ruta Santiago → Pucón", tag:"Ruta", tagClass:"ember",
    items:[
      {icon:"🏠", title:"Checkout de la casa",
        tips:["Revisar cajones, cargadores y el baño antes de salir.","Sacar unas fotos del estado de la casa al entregarla."]},
      {icon:"🚗", title:"Ruta a Pucón", meta:"~780 km", note:"Salida recomendada 8:00 – 9:00 hs", ember:true,
        tips:["Es un viaje largo (≈8-9 hs con paradas) — salir temprano es clave.","Cargar combustible antes de salir y no dejar el tanque bajar de la mitad en ruta.","Llevar TAG o efectivo para los peajes.","Descargar el mapa de la ruta offline por si hay tramos sin señal."],
        pack:["Documentos del auto y de conductor","Snacks y agua para el viaje","Cargador de auto"]},
      {icon:"☕", title:"Café / descanso",
        tips:["Buen momento para estirar las piernas antes de seguir manejando."]},
      {icon:"🅿️", title:"Posible parada en Curicó", note:"~2 horas de viaje",
        maps:"Curicó, Chile",
        tips:["Parada corta, útil para ir al baño y cargar combustible."]},
      {icon:"🍽️", title:"Almuerzo",
        tips:["Conviene algo rápido para no atrasar la llegada a Pucón, que es de noche igual."]},
      {icon:"💦", title:"Salto del Laja",
        maps:"Salto del Laja, Chile",
        tips:["Mirador accesible desde el estacionamiento, no exige mucho tiempo.","Piso puede estar húmedo cerca de las barandas."],
        outfit:["Calzado con buen agarre"]},
      {icon:"🛒", title:"Surtido en Temuco", note:"Supermercado: Jumbo o Líder",
        maps:"Supermercado Jumbo, Temuco, Chile",
        tips:["Es la última ciudad grande antes de Pucón — conviene comprar acá lo de varios días (carne, verdura, vino, snacks).","En Pucón los precios y la variedad son más limitados."]},
      {icon:"🍽️", title:"Comer de pasada en Villarrica y recorrer",
        maps:"Villarrica, Chile",
        tips:["Ya cerca del destino — buen lugar para una parada corta antes del tramo final."]},
      {icon:"🏡", title:"Check-in casa Pucón", ember:true,
        note:"Aldea Molco, Villarrica, Araucanía 4930000, Chile",
        maps:"Aldea Molco, Villarrica, Araucanía, Chile",
        tips:["Coordinar horario aproximado de llegada con el anfitrión, sobre todo si es de noche.","Guardar el contacto y la dirección exacta descargados (puede no haber señal en el camino)."]}
    ]
  },
  {
    dow:"Lunes", num:10, loc:"Pucón", tag:"Pucón",
    items:[
      {icon:"🏖️", title:"Recorrer Playa Grande", meta:"10:00 hs",
        maps:"Playa Grande, Pucón, Chile",
        tips:["Es playa de lago, el agua suele estar fría incluso en verano/temporada alta."],
        outfit:["Traje de baño","Calzado para caminar en arena/piedras"],
        pack:["Toalla","Protector solar"]},
      {icon:"🕳️", title:"Cuevas volcánicas", meta:"11:00 hs · ~5 hs de duración",
        maps:"Cuevas Volcánicas de Pucón, Chile",
        tips:["Adentro la temperatura baja bastante respecto al exterior.","Conviene reservar la entrada con anticipación, sobre todo en temporada alta."],
        outfit:["Campera de abrigo","Calzado cerrado con buen agarre"],
        pack:["Linterna de celular cargada"]}
    ]
  },
  {
    dow:"Martes", num:11, loc:"Pucón", tag:"Pucón",
    items:[
      {icon:"🌋", title:"Ascenso Volcán Villarrica", meta:"Día completo", ember:true,
        maps:"Volcán Villarrica, Chile",
        tips:["Se hace con agencia autorizada por CONAF, con guía obligatorio — reservar con anticipación.","Es una exigencia física alta (jornada larga, terreno de nieve/ceniza en pendiente).","El clima arriba puede cambiar rápido, aunque abajo esté despejado.","La agencia suele proveer crampones, piolet y casco — confirmar qué incluye la reserva.","Ir con buen descanso la noche anterior."],
        outfit:["Ropa técnica en capas (térmica + abrigo + cortaviento)","Guantes y gorro","Gafas de sol/nieve","Botas de trekking (o las que provea la agencia)"],
        pack:["Protector solar alto (la nieve refleja mucho)","Mochila pequeña con agua y comida energética"]},
      {icon:"🍺", title:"Nochecita: cervecería",
        maps:"Cervecería artesanal, Pucón, Chile",
        tips:["Después del volcán, buena opción cerca de la casa para no trasladarse mucho."]}
    ]
  },
  {
    dow:"Miércoles", num:12, loc:"Pucón", tag:"Pucón",
    items:[
      {icon:"🚗", title:"Salida de la casa", meta:"07:00 hs",
        tips:["Dejar la mochila del día armada la noche anterior para no atrasar la salida."]},
      {icon:"🌲", title:"Parque Nacional Huerquehue", note:"Abre 8:30 hs — ir temprano",
        maps:"Parque Nacional Huerquehue, Chile",
        tips:["Entrada paga en el acceso (CONAF) — llevar efectivo.","Estacionamiento limitado, por eso conviene llegar apenas abre."],
        pack:["Efectivo para la entrada"]},
      {icon:"🥾", title:"Sendero Los Lagos", ember:true,
        maps:"Sendero Los Lagos, Parque Nacional Huerquehue, Chile",
        sub:[
          {name:"Laguna Verde", maps:"Laguna Verde, Parque Nacional Huerquehue, Chile"},
          {name:"Laguna Toro", maps:"Laguna Toro, Parque Nacional Huerquehue, Chile"},
          {name:"Laguna Chica", maps:"Laguna Chica, Parque Nacional Huerquehue, Chile"},
          {name:"Miradores"}
        ],
        tips:["Es una caminata larga (varias horas, terreno con subidas) — calcular tiempo para volver antes de que oscurezca.","Llevar comida y agua, no hay dónde comprar en el sendero."],
        outfit:["Calzado de trekking","Campera cortaviento (cambia el clima en el bosque/altura)","Gorro"],
        pack:["Agua y snacks para todo el día","Protector solar"]}
    ]
  },
  {
    dow:"Jueves", num:13, loc:"Pucón", tag:"Pucón · grupos",
    items:[
      {group:true, boxes:[
        {label:"Grupo 1", icon:"⛷️", title:"Ski",
          maps:"Centro de Ski Pucón, Chile",
          tips:["Confirmar que el centro de ski esté operando (depende de nieve/temporada).","Si no tienen equipo propio, se puede alquilar en el centro o en Pucón."],
          outfit:["Ropa térmica e impermeable","Guantes, gorro y gafas de sol/nieve"],
          pack:["Protector solar alto"]},
        {label:"Grupo 2", icon:"🏔️", title:"Lagunas andinas y La China",
          maps:"Lagunas Andinas, Pucón, Chile",
          tips:["Caminata de altura — llevar capas porque cambia la temperatura."],
          outfit:["Calzado de trekking","Campera de abrigo"],
          pack:["Agua y snacks"]}
      ]},
      {icon:"🧖", title:"Salida a Termas Botánicas", meta:"14:00 hs",
        maps:"Termas Botánicas de Pucón, Chile",
        tips:["Conviene reservar entrada con anticipación, sobre todo en temporada alta.","Buen cierre de día después de la actividad de la mañana."],
        outfit:["Traje de baño","Ojotas o sandalias"],
        pack:["Toalla","Muda de ropa seca"]}
    ]
  },
  {
    dow:"Viernes", num:14, loc:"Pucón", tag:"Pucón",
    items:[
      {icon:"🚣", title:"Rafting", meta:"Mañana",
        maps:"Rafting Río Trancura, Pucón, Chile",
        tips:["La agencia suele dar traje de neopreno, casco y chaleco — confirmar qué incluye.","Dejar objetos de valor (celular, billetera) guardados, no llevarlos sueltos en la balsa.","Van a mojarse por completo, aunque no se caigan del bote."],
        outfit:["Ropa que se pueda mojar por debajo del neopreno","Calzado que se pueda mojar (no ojotas sueltas)"],
        pack:["Muda seca y toalla para después"]},
      {icon:"💦", title:"Tour de los saltos", meta:"Tarde", ember:true,
        sub:[
          {name:"Mirador Laguna El León", maps:"Mirador Laguna El León, Pucón, Chile"},
          {name:"Salto El León", maps:"Salto El León, Pucón, Chile"},
          {name:"Salto Los Mellizos", maps:"Salto Los Mellizos, Pucón, Chile"}
        ],
        tips:["Senderos cerca de agua suelen tener piedras húmedas y resbaladizas."],
        outfit:["Calzado con buen agarre (antideslizante)","Campera o poncho impermeable"],
        pack:["Cámara"]}
    ]
  },
  {
    dow:"Sábado", num:15, loc:"Ruta Pucón → Santiago", tag:"Ruta", tagClass:"ember",
    items:[
      {icon:"🚗", title:"Entrega de la casa", note:"Aldea Molco, Villarrica, Araucanía 4930000, Chile",
        maps:"Aldea Molco, Villarrica, Araucanía, Chile",
        tips:["Revisar bien que no quede nada olvidado (cargadores, ropa colgada, cosas en la heladera).","Sacar fotos del estado de la casa al entregarla."]},
      {icon:"🔑", title:"Entrega de auto", meta:"22:00 hs", ember:true,
        maps:"Arriendo de autos Aeropuerto Arturo Merino Benítez, Santiago, Chile",
        tips:["Llegar a Santiago con margen — el viaje de vuelta también es largo.","Devolver el auto con el tanque como lo pide el contrato (normalmente lleno).","Sacar fotos del auto al entregarlo y guardar el comprobante de devolución."],
        pack:["Documentos del auto y comprobante de alquiler"]}
    ]
  },
  {
    dow:"Domingo", num:16, loc:"Vuelo Santiago → Montevideo", tag:"Vuelo", tagClass:"ember",
    items:[
      {icon:"✈️", title:"Vuelo Santiago → Montevideo", meta:"06:50 – 10:00 hs", ember:true,
        maps:"Aeropuerto Internacional Arturo Merino Benítez, Santiago, Chile",
        tips:["Vuelo temprano — calcular traslado al aeropuerto con margen.","Check-in online la noche anterior.","Revisar límites de equipaje de mano antes de armar valijas."],
        pack:["Documento de identidad","Boarding pass descargado"]}
    ]
  }
];

const GENERAL = {
  tips:[
    "Cédula/pasaporte vigente para cruzar la frontera y hacer el check-in de los vuelos.",
    "Efectivo en pesos chilenos: útil para peajes, entradas a parques nacionales (CONAF) y lugares sin POS.",
    "Licencia de conducir y reserva del auto a mano (impresa o en el celular).",
    "Descargar direcciones y mapas offline por si hay tramos de ruta sin señal."
  ],
  outfit:[
    "Ropa en capas: hay tramos de calor (Santiago) y de frío intenso (volcán, termas de noche).",
    "Calzado de trekking + algo cómodo para ciudad.",
    "Traje de baño (termas, playa del lago)."
  ],
  pack:[
    "Cargadores y power bank",
    "Protector solar (la nieve y la altura reflejan mucho)",
    "Medicamentos personales / botiquín básico",
    "Toalla y muda de ropa seca"
  ]
};

// Agregar acá nuevas notas/documentos del viaje: {icon, title, url} para links, {icon, title, phone} para teléfonos.
const NOTES = [
  {icon:"🎫", title:"Drive pasajes", url:"https://drive.google.com/drive/folders/1QD5QM0mE8MG6ajhYZZkGjUYXZobx6fDc?usp=sharing"},
  {icon:"📊", title:"Excel con datos", url:"https://docs.google.com/spreadsheets/d/1YAEMTC7cLQMOfmJaqUcvubC7MVc2A8_gD5AJjxEp-Eo/edit?usp=sharing"},
  {icon:"🌶️", title:"Casa Santiago", url:"https://www.booking.com/hotel/cl/providencia-suites-santiago.es.html?aid=383259&label=santiago%2Fprovidencia-ydjRImlBHxLCGOIqNdDJ1gSM553196594526%3Apl%3Ata%3Ap1%3Ap2%3Aac%3Aap%3Aneg%3Afi%3Atikwd-494200121432%3Alp9069680%3Ali%3Adem%3Adm%3Appccp%3DUmFuZG9tSVYkc2RlIyh9YRlijhKLEMjJLyONwTyX95c&sid=ffb55aeced5956569622ba43e0c92f50&all_sr_blocks=1670187703_438813171_7_0_0&checkin=2026-08-07&checkout=2026-08-09&dest_id=1990&dest_type=district&dist=0&group_adults=7&group_children=0&hapos=1&highlighted_blocks=1670187703_438813171_7_0_0&hpos=1&matching_block_id=1670187703_438813171_7_0_0&no_rooms=1&req_adults=7&req_children=0&room1=A%2CA%2CA%2CA%2CA%2CA%2CA&sb_price_type=total&sr_order=popularity&sr_pri_blocks=1670187703_438813171_7_0_0__20710&srepoch=1782008951&srpvid=cbb7117570d8037f&type=total&ucfs=1&"},
  {icon:"🏔️", title:"Casa Pucón", url:"https://es-l.airbnb.com/rooms/1296985412382637978?unique_share_id=dba1287a-fce8-4734-bac2-da612cbcfd82&viralityEntryPoint=1&s=76"},
  {icon:"🚑", title:"Seguro Chile", phone:"188800200668"}
];

const INSTALL_STEPS = [
  "Si el link se abrió en otro navegador (Chrome, etc.), tocá el ícono de compartir o los tres puntos y elegí “Abrir en Safari”.",
  "En Safari, tocá el ícono de Compartir (el cuadrado con la flecha hacia arriba) en la barra de abajo.",
  "Deslizá el menú hacia abajo y elegí “Agregar a Pantalla de Inicio”.",
  "Confirmá el nombre y tocá “Agregar”, arriba a la derecha."
];

function mapsUrl(q){
  return 'https://www.google.com/maps/search/?api=1&query=' + encodeURIComponent(q);
}

const rail = document.getElementById('rail');
const panels = document.getElementById('panels');
const overlay = document.getElementById('overlay');
const sheet = document.getElementById('sheet');

const TRIP_YEAR = 2026, TRIP_MONTH = 7; // agosto (0-indexed)
const today = new Date();
const todayIdx = DAYS.findIndex(d => today.getFullYear()===TRIP_YEAR && today.getMonth()===TRIP_MONTH && today.getDate()===d.num);
const initialDayIndex = todayIdx !== -1 ? todayIdx : 0;

DAYS.forEach((d,i)=>{
  const pill = document.createElement('div');
  pill.className = 'day-pill' + (i===initialDayIndex?' active':'');
  pill.id = 'pill-'+i;
  pill.innerHTML = `<div class="num">${d.num}</div><div class="dow">${d.dow.slice(0,3)}</div><div class="dot"></div>`;
  pill.onclick = ()=>showDay(i);
  rail.appendChild(pill);

  const panel = document.createElement('div');
  panel.className = 'day-panel' + (i===initialDayIndex?' active':'');
  panel.id = 'panel-'+i;

  let itemsHtml = '';
  d.items.forEach((it,j)=>{
    if(it.group){
      itemsHtml += `<div class="item"><div class="group-row">`;
      it.boxes.forEach((b,k)=>{
        itemsHtml += `<div class="group-box" onclick="openGroupDetail(${i},${j},${k})">
          <p class="group-label">${b.label}</p>
          <div class="item-top"><span class="item-icon">${b.icon}</span>
            <div class="item-body"><div class="item-title-row"><p class="item-title">${b.title}</p><span class="info-chip">i</span></div></div>
          </div></div>`;
      });
      itemsHtml += `</div></div>`;
      return;
    }
    const subHtml = it.sub ? `<ul class="sublist">${it.sub.map(s=>`
      <li><span class="sub-name">${s.name}</span>${s.maps?`<a class="sub-pin" href="${mapsUrl(s.maps)}" target="_blank" rel="noopener">📍</a>`:''}</li>`).join('')}</ul>` : '';
    const mapsBtn = it.maps ? `<a class="maps-link" href="${mapsUrl(it.maps)}" target="_blank" rel="noopener">📍 Ver en Maps</a>` : '';

    itemsHtml += `<div class="item${it.ember?' ember':''}">
      <div class="item-card" onclick="handleCardClick(event, ${i}, ${j})">
        <div class="item-top">
          <span class="item-icon">${it.icon||'📍'}</span>
          <div class="item-body">
            <div class="item-title-row">
              <p class="item-title">${it.title}</p>
              <span class="info-chip">i</span>
            </div>
            ${it.meta?`<p class="item-meta">${it.meta}</p>`:''}
            ${it.note?`<p class="item-note">${it.note}</p>`:''}
            ${mapsBtn}
          </div>
        </div>
        ${subHtml}
      </div>
    </div>`;
  });

  panel.innerHTML = `
    <div class="day-head">
      <h2>${d.dow} ${d.num}</h2>
      <span class="day-tag${d.tagClass==='ember'?' ember':''}">${d.tag}</span>
    </div>
    <p class="day-loc">${d.loc}</p>
    <div class="timeline">${itemsHtml}</div>
    <div class="day-nav">
      <div class="nav-btn${i===0?' disabled':''}" onclick="showDay(${i-1})">← Día anterior</div>
      <div class="nav-btn${i===DAYS.length-1?' disabled':''}" onclick="showDay(${i+1})">Día siguiente →</div>
    </div>
  `;
  panels.appendChild(panel);
});

document.getElementById('pill-'+initialDayIndex).scrollIntoView({inline:'center', block:'nearest'});

// Only open the detail sheet if the click didn't land on a link (maps buttons/pins),
// so the map buttons keep the browser's native anchor behavior intact.
function handleCardClick(event, dayIdx, itemIdx){
  if(event.target.closest('a')) return;
  openDetail(dayIdx, itemIdx);
}

function showDay(i){
  if(i<0||i>=DAYS.length) return;
  document.querySelectorAll('.day-pill').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.day-panel').forEach(p=>p.classList.remove('active'));
  document.getElementById('pill-'+i).classList.add('active');
  document.getElementById('panel-'+i).classList.add('active');
  document.getElementById('pill-'+i).scrollIntoView({behavior:'smooth', inline:'center', block:'nearest'});
  window.scrollTo({top:0, behavior:'smooth'});
}

function renderSheet(icon, title, meta, note, tips, outfit, pack, maps, sub, links, steps){
  let html = `
    <div class="sheet-handle"></div>
    <div class="sheet-head">
      <span class="sheet-icon">${icon||'📍'}</span>
      <div class="item-body">
        <p class="sheet-title">${title}</p>
        ${meta?`<p class="sheet-meta">${meta}</p>`:''}
      </div>
      <div class="sheet-close" onclick="closeDetail()">✕</div>
    </div>
    ${note?`<p class="sheet-note">${note}</p>`:''}
    ${maps?`<a class="sheet-maps" href="${mapsUrl(maps)}" target="_blank" rel="noopener">📍 Ver en Google Maps</a>`:''}
  `;

  const hasTips = tips && tips.length;
  const hasOutfit = outfit && outfit.length;
  const hasPack = pack && pack.length;
  const hasSub = sub && sub.length;
  const hasLinks = links && links.length;
  const hasSteps = steps && steps.length;

  if(hasSteps){
    html += `<div class="sheet-section">
      <ol class="steps-list">${steps.map(s=>`<li>${s}</li>`).join('')}</ol>
    </div>`;
  }
  if(hasTips){
    html += `<div class="sheet-section">
      <p class="sheet-section-title warn">Tener en cuenta</p>
      <ul class="tip-list">${tips.map(t=>`<li>${t}</li>`).join('')}</ul>
    </div>`;
  }
  if(hasOutfit){
    html += `<div class="sheet-section">
      <p class="sheet-section-title outfit">Indumentaria recomendada</p>
      <ul class="outfit-list">${outfit.map(o=>`<li>${o}</li>`).join('')}</ul>
    </div>`;
  }
  if(hasPack){
    html += `<div class="sheet-section">
      <p class="sheet-section-title">Qué llevar</p>
      <ul class="pack-list">${pack.map(p=>`<li>${p}</li>`).join('')}</ul>
    </div>`;
  }
  if(hasSub){
    html += `<div class="sheet-section">
      <p class="sheet-section-title">Lugares de la etapa</p>
      <ul class="place-list">${sub.map(s=>`<li>${s.name}${s.maps?`<a class="place-pin" href="${mapsUrl(s.maps)}" target="_blank" rel="noopener">Ver en Maps</a>`:''}</li>`).join('')}</ul>
    </div>`;
  }
  if(hasLinks){
    html += `<div class="sheet-section">
      <ul class="notes-list">${links.map(n=>{
        const href = n.url ? n.url : (n.phone ? 'tel:'+n.phone : '#');
        const extAttrs = n.url ? ' target="_blank" rel="noopener"' : '';
        return `<li><a class="notes-row" href="${href}"${extAttrs}>
          <span class="notes-icon">${n.icon||'📎'}</span>
          <span class="notes-title">${n.title}</span>
          <span class="notes-arrow">${n.phone?'📞':'↗'}</span>
        </a></li>`;
      }).join('')}</ul>
    </div>`;
  }
  if(!hasTips && !hasOutfit && !hasPack && !hasSub && !hasLinks && !hasSteps && !maps){
    html += `<p class="no-info">Sin notas adicionales para esta actividad.</p>`;
  }

  sheet.innerHTML = html;
  overlay.classList.add('open');
}

function openDetail(dayIdx, itemIdx){
  const it = DAYS[dayIdx].items[itemIdx];
  renderSheet(it.icon, it.title, it.meta, it.note, it.tips, it.outfit, it.pack, it.maps, it.sub);
}

function openGroupDetail(dayIdx, itemIdx, boxIdx){
  const b = DAYS[dayIdx].items[itemIdx].boxes[boxIdx];
  renderSheet(b.icon, `${b.label}: ${b.title}`, null, null, b.tips, b.outfit, b.pack, b.maps, null);
}

function openGeneralInfo(){
  renderSheet("🎒", "Esenciales del viaje", null, null, GENERAL.tips, GENERAL.outfit, GENERAL.pack, null, null);
}

function openNotesInfo(){
  renderSheet("📎", "Notas y documentos", null, null, null, null, null, null, null, NOTES);
}

function openInstallInfo(){
  renderSheet("📲", "Cómo instalar en el iPhone", null, null, null, null, null, null, null, null, INSTALL_STEPS);
}

function closeDetail(){
  overlay.classList.remove('open');
}
overlay.addEventListener('click', (e)=>{ if(e.target===overlay) closeDetail(); });
</script>

</body>
</html>
