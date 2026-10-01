# Bricolaje
Una app con más de 100 tips de reparaciones caseras: "Hágalo usted mismo"
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>100 Tips de Bricolaje</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Archivo+Black&family=Archivo:wght@300;400;500;600&display=swap');

  :root {
    --bg: #f7f3ee;
    --surface: #ede8e0;
    --card: #fff;
    --border: #d8d0c4;
    --ink: #1c1814;
    --ink2: #4a4238;
    --ink3: #8a7f74;
    --plomeria: #1a6fa8;
    --plomeria-bg: rgba(26,111,168,0.07);
    --electricidad: #c8820a;
    --electricidad-bg: rgba(200,130,10,0.07);
    --carpinteria: #5a8a2a;
    --carpinteria-bg: rgba(90,138,42,0.07);
    --warn: #c0401a;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--ink);
    font-family: 'Archivo', sans-serif;
    font-size: 15px;
    line-height: 1.65;
  }

  /* diagonal stripe texture */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: repeating-linear-gradient(
      45deg,
      transparent,
      transparent 40px,
      rgba(0,0,0,0.012) 40px,
      rgba(0,0,0,0.012) 41px
    );
    pointer-events: none;
    z-index: 0;
  }

  /* ── HERO ── */
  .hero {
    background: var(--ink);
    color: var(--bg);
    padding: 56px 40px 48px;
    position: relative;
    overflow: hidden;
  }

  .hero::after {
    content: '100';
    position: absolute;
    right: -10px;
    bottom: -30px;
    font-family: 'Archivo Black', sans-serif;
    font-size: 220px;
    color: rgba(255,255,255,0.04);
    line-height: 1;
    pointer-events: none;
  }

  .hero-eyebrow {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    border: 1px solid rgba(255,255,255,0.2);
    color: rgba(255,255,255,0.6);
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 3px;
    text-transform: uppercase;
    padding: 5px 14px;
    border-radius: 3px;
    margin-bottom: 22px;
  }

  .hero h1 {
    font-family: 'Archivo Black', sans-serif;
    font-size: clamp(40px, 7vw, 88px);
    line-height: 0.93;
    letter-spacing: -2px;
    text-transform: uppercase;
    margin-bottom: 20px;
  }

  .hero h1 em { font-style: normal; color: var(--electricidad); }

  .hero-desc {
    color: rgba(255,255,255,0.55);
    font-size: 15px;
    max-width: 480px;
    line-height: 1.7;
  }

  .hero-tags {
    display: flex;
    gap: 10px;
    margin-top: 24px;
    flex-wrap: wrap;
  }

  .htag {
    font-size: 12px;
    font-weight: 600;
    padding: 5px 14px;
    border-radius: 100px;
    letter-spacing: 0.5px;
  }

  .htag-p { background: var(--plomeria); color: #fff; }
  .htag-e { background: var(--electricidad); color: #fff; }
  .htag-c { background: var(--carpinteria); color: #fff; }

  /* ── FILTER BAR ── */
  .filter-bar {
    background: var(--ink);
    border-bottom: 1px solid #333;
    padding: 0 40px;
    display: flex;
    gap: 0;
    overflow-x: auto;
    scrollbar-width: none;
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .filter-bar::-webkit-scrollbar { display: none; }

  .filter-btn {
    padding: 13px 20px;
    background: none;
    border: none;
    border-bottom: 2px solid transparent;
    color: rgba(255,255,255,0.4);
    font-family: 'Archivo', sans-serif;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    cursor: pointer;
    white-space: nowrap;
    transition: all .2s;
  }
  .filter-btn:hover { color: rgba(255,255,255,0.8); }
  .filter-btn.active-all { color: #fff; border-bottom-color: #fff; }
  .filter-btn.active-p { color: #5aaee8; border-bottom-color: #5aaee8; }
  .filter-btn.active-e { color: var(--electricidad); border-bottom-color: var(--electricidad); }
  .filter-btn.active-c { color: #8aba4a; border-bottom-color: #8aba4a; }

  /* ── MAIN ── */
  .main {
    max-width: 960px;
    margin: 0 auto;
    padding: 48px 36px 80px;
    position: relative;
    z-index: 1;
  }

  /* ── CATEGORY HEADER ── */
  .cat-section { margin-bottom: 60px; }

  .cat-header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 24px;
    padding-bottom: 16px;
    border-bottom: 2px solid var(--ink);
  }

  .cat-num {
    font-family: 'Archivo Black', sans-serif;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    opacity: .4;
  }

  .cat-title {
    font-family: 'Archivo Black', sans-serif;
    font-size: 28px;
    text-transform: uppercase;
    letter-spacing: -0.5px;
    flex: 1;
  }

  .cat-title.p { color: var(--plomeria); }
  .cat-title.e { color: var(--electricidad); }
  .cat-title.c { color: var(--carpinteria); }

  .cat-badge {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    padding: 4px 12px;
    border-radius: 3px;
  }

  .badge-p { background: var(--plomeria-bg); color: var(--plomeria); border: 1px solid rgba(26,111,168,.2); }
  .badge-e { background: var(--electricidad-bg); color: var(--electricidad); border: 1px solid rgba(200,130,10,.2); }
  .badge-c { background: var(--carpinteria-bg); color: var(--carpinteria); border: 1px solid rgba(90,138,42,.2); }

  /* ── TIP CARD ── */
  .tip-card {
    background: var(--card);
    border: 1.5px solid var(--border);
    border-radius: 10px;
    margin-bottom: 8px;
    overflow: hidden;
    transition: border-color .2s, box-shadow .2s;
    cursor: pointer;
  }

  .tip-card:hover { box-shadow: 0 2px 12px rgba(0,0,0,.08); }
  .tip-card.open { border-color: var(--ink); }
  .tip-card[data-cat="p"].open { border-color: var(--plomeria); }
  .tip-card[data-cat="e"].open { border-color: var(--electricidad); }
  .tip-card[data-cat="c"].open { border-color: var(--carpinteria); }

  .tip-header {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 14px 18px;
    user-select: none;
  }

  .tip-n {
    font-family: 'Archivo Black', sans-serif;
    font-size: 12px;
    letter-spacing: 1px;
    min-width: 28px;
    flex-shrink: 0;
  }
  .tip-card[data-cat="p"] .tip-n { color: var(--plomeria); }
  .tip-card[data-cat="e"] .tip-n { color: var(--electricidad); }
  .tip-card[data-cat="c"] .tip-n { color: var(--carpinteria); }

  .tip-title {
    font-family: 'Archivo Black', sans-serif;
    font-size: 15px;
    letter-spacing: 0.2px;
    flex: 1;
    line-height: 1.25;
  }

  .tip-arrow {
    color: var(--ink3);
    font-size: 18px;
    transition: transform .3s;
    flex-shrink: 0;
  }
  .tip-card.open .tip-arrow { transform: rotate(90deg); }

  /* ── TIP BODY ── */
  .tip-body {
    display: none;
    padding: 0 18px 18px 60px;
    animation: fadeIn .22s ease;
  }
  .tip-card.open .tip-body { display: block; }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(-4px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .tip-body p {
    font-size: 14px;
    color: var(--ink2);
    line-height: 1.75;
    margin-bottom: 10px;
  }

  .tip-body p:last-child { margin-bottom: 0; }
  .tip-body p strong { color: var(--ink); font-weight: 600; }

  .tip-steps {
    list-style: none;
    margin: 10px 0;
  }

  .tip-step {
    display: flex;
    gap: 10px;
    padding: 7px 0;
    border-bottom: 1px solid var(--surface);
    font-size: 14px;
    color: var(--ink2);
    line-height: 1.65;
    align-items: flex-start;
  }

  .tip-step:last-child { border-bottom: none; }

  .ts {
    font-family: 'Archivo Black', sans-serif;
    font-size: 11px;
    min-width: 22px;
    height: 22px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 4px;
    flex-shrink: 0;
    margin-top: 1px;
  }

  .tip-card[data-cat="p"] .ts { background: var(--plomeria-bg); color: var(--plomeria); }
  .tip-card[data-cat="e"] .ts { background: var(--electricidad-bg); color: var(--electricidad); }
  .tip-card[data-cat="c"] .ts { background: var(--carpinteria-bg); color: var(--carpinteria); }

  .alerta {
    display: flex;
    gap: 8px;
    background: rgba(192,64,26,.06);
    border: 1px solid rgba(192,64,26,.2);
    border-left: 3px solid var(--warn);
    color: #8a2a0a;
    font-size: 13px;
    padding: 9px 12px;
    border-radius: 0 6px 6px 0;
    margin-top: 10px;
    line-height: 1.55;
  }

  .materiales {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
    margin: 10px 0;
  }

  .mat {
    background: var(--surface);
    border: 1px solid var(--border);
    color: var(--ink2);
    font-size: 12px;
    padding: 2px 9px;
    border-radius: 3px;
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 600px) {
    .hero { padding: 36px 20px; }
    .main { padding: 28px 16px 60px; }
    .filter-bar { padding: 0 12px; }
    .tip-body { padding: 0 14px 16px 14px; }
  }
</style>
</head>
<body>

<div class="hero">
  <div class="hero-eyebrow">🔧 Guía práctica · México</div>
  <h1>100 Tips de<br><em>Bricolaje</em></h1>
  <p class="hero-desc">Plomería, electricidad y carpintería. Los problemas más comunes del hogar mexicano resueltos paso a paso, sin experiencia previa.</p>
  <div class="hero-tags">
    <span class="htag htag-p">💧 Plomería · 34 tips</span>
    <span class="htag htag-e">⚡ Electricidad · 33 tips</span>
    <span class="htag htag-c">🪵 Carpintería · 33 tips</span>
  </div>
</div>

<div class="filter-bar">
  <button class="filter-btn active-all" onclick="filtrar('all',this)">Todos (100)</button>
  <button class="filter-btn" onclick="filtrar('p',this)">💧 Plomería</button>
  <button class="filter-btn" onclick="filtrar('e',this)">⚡ Electricidad</button>
  <button class="filter-btn" onclick="filtrar('c',this)">🪵 Carpintería</button>
</div>

<div class="main">

<!-- ══════════════ PLOMERÍA ══════════════ -->
<div class="cat-section" data-sec="p">
  <div class="cat-header">
    <span class="cat-num">01</span>
    <span class="cat-title p">Plomería</span>
    <span class="cat-badge badge-p">34 tips · #001–#034</span>
  </div>

  <!-- #001 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#001</span>
      <span class="tip-title">Cómo cerrar el paso del agua en una emergencia</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>Antes de cualquier reparación de plomería debes saber dónde están tus llaves de paso. En México la distribución estándar tiene tres niveles de corte.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Llave individual del mueble:</strong> debajo del fregadero, del lavabo o detrás del WC. Gira a la derecha para cerrar.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Llave general del departamento o casa:</strong> generalmente en el cuarto de servicio, debajo del fregadero principal o en un nicho en la pared. Cierra toda el agua de tu vivienda.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Llave de la calle:</strong> en la banqueta frente a tu casa, bajo una tapadera metálica. Requiere llave especial o desarmador. Solo úsala en emergencias graves.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Ubica todas tus llaves de paso <em>antes</em> de que ocurra una emergencia y verifica que giren sin problema. En casas viejas suelen estar oxidadas o inoperantes.</div></li>
      </ul>
    </div>
  </div>

  <!-- #002 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#002</span>
      <span class="tip-title">Reparar una llave que gotea (de mariposa o esfera)</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>El goteo constante desperdicia hasta 30 litros de agua al día. Casi siempre es el empaque o cartucho gastado.</p>
      <div class="materiales">
        <span class="mat">Desarmadores plano y estrella</span><span class="mat">Llave ajustable</span><span class="mat">Empaque o cartucho nuevo</span><span class="mat">Teflón</span>
      </div>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra la llave de paso del mueble. Abre la llave para drenar el agua que queda en la tubería.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Llave de mariposa (dos manijas):</strong> retira el botón decorativo en la punta, destornilla la cabeza y saca el vástago. El empaque de hule está en la punta — cámbialo por uno del mismo tamaño.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Llave de esfera (una manija):</strong> retira el tornillo Allen bajo la manija, desmonta la tapa y extrae el cartucho. Lleva el cartucho viejo a la ferretería para conseguir el repuesto exacto.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Al reinstalar, aplica unas vueltas de teflón en las roscas. Abre lentamente la llave de paso para verificar que no haya fugas.</div></li>
      </ul>
    </div>
  </div>

  <!-- #003 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#003</span>
      <span class="tip-title">Destapar un lavabo o fregadero sin químicos</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>El tapón más común en México es la acumulación de grasa, jabón y cabello en el sifón (la curva en S bajo el lavabo).</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Método baking soda + vinagre:</strong> vierte media taza de bicarbonato seguida de media taza de vinagre blanco. Tapa el desagüe 5 minutos. La reacción disuelve la grasa. Enjuaga con agua caliente.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Con soplete de presión (émbolo):</strong> llena el lavabo con 5 cm de agua. Coloca el émbolo sobre el desagüe y bombea con fuerza 10–15 veces. La presión empuja el tapón.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Limpiar el sifón:</strong> coloca una cubeta debajo. Gira las tuercas del sifón plástico a mano (antihorario). Saca el sifón, limpia la acumulación con un cepillo viejo y reinstala.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Prevención: usa una rejilla atrapa-cabello en el desagüe y vierte agua caliente una vez a la semana para disolver la grasa acumulada.</div></li>
      </ul>
    </div>
  </div>

  <!-- #004 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#004</span>
      <span class="tip-title">Destapar el WC con émbolo y sonda</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>Nunca uses destapacaños químicos en WC — dañan el sello de cera y la porcelana. El émbolo es siempre el primer recurso.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Usa un émbolo de copa (no el plano de fregadero). Introduce la copa en el orificio del WC, forma un sello y bombea con fuerza vertical 10 veces. El vacío y la presión desatascan la mayoría de obstrucciones.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Si persiste, usa una sonda (serpiente) manual. Introduce el extremo flexible por el orificio y gira la manivela mientras avanzas. Al encontrar resistencia, gira en sentido contrario para enganchar o romper el tapón.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Nunca jales hacia atrás la sonda de golpe — puede rayar la porcelana. Extrae despacio girando.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Si el tapón persiste después de la sonda, el problema puede estar más profundo en la tubería — ese caso sí requiere plomero.</div></li>
      </ul>
      <div class="alerta">⚠️ Si varios muebles se tapan al mismo tiempo, el problema es en el tubo principal, no en cada mueble — requiere sonda motorizada.</div>
    </div>
  </div>

  <!-- #005 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#005</span>
      <span class="tip-title">Cambiar el mecanismo interno del WC (flapper y flotador)</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>Si el WC "corre" solo o llena y sigue llenando, el problema es el flapper (válvula de descarga) o el flotador.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra la llave de paso del WC. Jala la cadena para vaciar la cisterna. Retira la tapa de la cisterna.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Flapper gastado (agua que escurre al WC):</strong> el flapper es la pieza de hule en el fondo de la cisterna. Desengánchalo de sus pines, desconecta la cadena y lleva el viejo a la ferretería para conseguir el mismo modelo.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Flotador mal calibrado (cisterna que no llena o que rebosa):</strong> dobla ligeramente el brazo del flotador hacia abajo para que corte el agua antes. O ajusta la tuerca de calibración si tiene mecanismo de tornillo.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Abre la llave de paso, deja llenar y verifica que corte el agua al nivel correcto (2 cm abajo del tubo de rebose).</div></li>
      </ul>
    </div>
  </div>

  <!-- #006 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#006</span>
      <span class="tip-title">Sellar una fuga en tubería con teflón y cinta de reparación</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>Para fugas en uniones roscadas, el teflón es la solución estándar. Para fugas en el tubo mismo, existe la cinta de reparación de emergencia.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra el paso del agua y seca perfectamente la tubería donde hay fuga.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Fuga en unión roscada:</strong> desmonta la conexión. Limpia las roscas con un cepillo. Aplica 5–7 vueltas de teflón en el sentido de la rosca (horario al enrollar). Vuelve a armar y aprieta firme.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Fuga en el cuerpo del tubo:</strong> usa cinta de reparación de silicona (se vende en ferreterías). Estira la cinta al doble de su longitud y envuelve sobre sí misma con tensión, 5 cm en cada lado del punto de fuga. Se vulcaniza sola.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>La cinta de reparación es temporal. Planea cambiar la sección de tubo dañada pronto.</div></li>
      </ul>
    </div>
  </div>

  <!-- #007 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#007</span>
      <span class="tip-title">Instalar o cambiar una llave de paso de ángulo (bajo el mueble)</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>Las llaves de paso de ángulo son las pequeñas llaves cromadas que conectan la tubería de la pared con el mueble. Se gastan y gotean con el tiempo.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra la llave general. Abre el mueble para drenar.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Con llave ajustable, gira la tuerca de compresión en la pared (antihorario). La llave de paso vieja sale completa.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Aplica teflón en la rosca del tubo de la pared — 6 vueltas en sentido horario. Enrosca la llave nueva a mano y luego aprieta 1/4 de vuelta más con la llave ajustable. No sobre-aprietes — el tubo de cobre se puede doblar.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Conecta el tubo flexible (manguera del mueble) a la salida de la llave nueva. Abre el paso lentamente y verifica fugas.</div></li>
      </ul>
    </div>
  </div>

  <!-- #008 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#008</span>
      <span class="tip-title">Conectar tubo de PVC con pegamento (unión fría)</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>El PVC hidráulico (blanco o crema) usa pegamento especial para soldar en frío. Es la tubería más usada en México para agua fría y drenaje.</p>
      <div class="materiales">
        <span class="mat">Pegamento PVC (Tangit o similar)</span><span class="mat">Primer/limpiador PVC</span><span class="mat">Lija 80</span><span class="mat">Trapo limpio</span>
      </div>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Corta el tubo a escuadra con serrucho o cortador de PVC. Lija el borde cortado para eliminar rebabas.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Aplica primer/limpiador en el exterior del tubo y el interior del cople — esto abre los poros del PVC para mejor adhesión. Deja 30 segundos.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Aplica pegamento en ambas superficies con el pincel del frasco. Inserta el tubo girando 1/4 de vuelta mientras empujas a fondo. Mantén la presión 30 segundos.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>No apliques agua durante 2 horas. La unión alcanza resistencia total en 24 horas.</div></li>
      </ul>
      <div class="alerta">⚠️ No uses pegamento PVC en tuberías de agua caliente — para caliente se usa CPVC (amarillo) con su propio pegamento específico.</div>
    </div>
  </div>

  <!-- #009 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#009</span>
      <span class="tip-title">Reparar fuga en tubería de cobre</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>El cobre es común en instalaciones antiguas en México. Se puede reparar con soldadura o con coples de compresión sin soldar.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Con cople de compresión (sin soldar):</strong> corta la sección dañada con cortador de cobre. Desliza la tuerca y el anillo de compresión en cada extremo del tubo. Inserta el cople y aprieta las tuercas a mano + 1.5 vueltas con llave. No requiere herramienta especial.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Con soldadura de plata (método profesional):</strong> requiere soplete, flux y soldadura. Calienta la unión uniformemente hasta que la soldadura fluya por capilaridad. Requiere práctica — empieza con el cople de compresión.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Seca perfectamente el tubo antes de cualquier reparación — ni una gota de agua o la soldadura no fluye y el cople no sella bien.</div></li>
      </ul>
    </div>
  </div>

  <!-- #010 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#010</span>
      <span class="tip-title">Cómo leer el medidor de agua y detectar fugas ocultas</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra toda llave y aparato de agua en tu casa. Ve al medidor (en la banqueta o entrada de la casa).</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Observa el indicador pequeño o triangulito de flujo. Si gira con todo cerrado, tienes una fuga oculta.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Anota la lectura. Espera 1 hora sin usar agua. Si la lectura cambió, la fuga existe aunque no la veas.</div></li>
        <li class="tip-step"><div class="ts">4</div><div><strong>Para localizar la fuga:</strong> cierra la llave general dentro de casa y observa si el medidor para. Si para = la fuga está dentro. Si sigue = la fuga está entre el medidor y tu llave general (tubería enterrada).</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Las fugas más comunes no visibles: WC que "corre" (pon colorante en la cisterna — si llega al WC sin jalar, hay fuga), válvulas bajo el fregadero que gotean dentro del mueble.</div></li>
      </ul>
    </div>
  </div>

  <!-- #011 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#011</span>
      <span class="tip-title">Instalar un calentador de agua (boiler) de paso</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>Los calentadores de paso instantáneos (sin tinaco de agua caliente) son cada vez más comunes en México por su eficiencia.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Ubica el lugar de instalación: cerca de donde se usará más el agua caliente, con ventilación si es de gas, o con circuito eléctrico dedicado si es eléctrico.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Cierra el paso de agua general. Conecta la entrada de agua fría (generalmente tubo azul o entrada marcada "C") y la salida de agua caliente ("H") con mangueras flexibles apropiadas.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Para calentadores de gas: la conexión de gas siempre debe hacerla un instalador certificado. Lo que puedes hacer tú es la parte hidráulica.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Verifica que no haya fugas en las conexiones hidráulicas antes de encender. Purga el aire abriendo una llave de agua caliente hasta que salga flujo continuo.</div></li>
      </ul>
      <div class="alerta">⚠️ La conexión de gas siempre requiere técnico certificado (ANCE). No hagas conexiones de gas por tu cuenta.</div>
    </div>
  </div>

  <!-- #012 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#012</span>
      <span class="tip-title">Limpiar y desincrustrar la regadera y llaves con cal</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>El agua en México tiene alta concentración de minerales. La cal (sarro blanco) obstruye las salidas de agua y reduce la presión.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Regadera:</strong> llena una bolsa de plástico con vinagre blanco puro. Introduce la cabeza de la regadera en la bolsa y sujeta con una liga. Deja remojando 4–8 horas o toda la noche.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Si la regadera se puede desmontar (tuerca central), quítala y ponla directamente en un recipiente con vinagre. Usa un palillo para limpiar cada orificio.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Llaves y aireadores:</strong> el aireador es la malla en la punta de la llave. Desatornillalo (antihorario), remoja en vinagre 30 minutos, limpia con cepillo de dientes y reinstala.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Para prevenir: aplica vinagre mensualmente o usa un filtro descalcificador en la entrada de agua si el sarro es muy severo.</div></li>
      </ul>
    </div>
  </div>

  <!-- #013 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#013</span>
      <span class="tip-title">Mantenimiento del tinaco (limpieza y revisión)</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>El tinaco debe limpiarse mínimo una vez al año. Acumula sedimentos, algas y bacterias que contaminan el agua.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra la llave de entrada del tinaco (la que viene de la red municipal). Deja consumir el agua o conéctate a otra toma para el día.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Abre la llave de vaciado en la parte inferior del tinaco. Si no tiene, conecta una manguera a la salida de uso y llévala al drenaje.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Con el tinaco vacío, introduce un cepillo de mango largo y talla las paredes interiores. No uses jabón — solo agua y el cepillo.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Enjuaga con agua limpia y vacía nuevamente. Llena con agua limpia y agrega hipoclorito de sodio (cloro para agua) — 1 litro por cada 1,000 litros de capacidad del tinaco. Deja reposar 30 minutos antes de consumir.</div></li>
      </ul>
    </div>
  </div>

  <!-- #014 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#014</span>
      <span class="tip-title">Instalar un mueble de baño (lavabo empotrado)</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra el paso del agua. Coloca la llave del lavabo en el mueble antes de colocar el mueble en su lugar — es imposible hacerlo después.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Conecta las mangueras flexibles a la llave antes de subir el mueble. Mucho más fácil trabajar el mueble boca arriba.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Coloca el mueble y conecta las mangueras a las llaves de paso del muro. Conecta el desagüe al sifón en S.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Aplica silicón transparente en la unión entre el mueble y la pared para sellar y evitar humedad detrás.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Abre el paso lentamente. Verifica cada unión. Deja el silicón curar 24 horas antes de mojar la zona.</div></li>
      </ul>
    </div>
  </div>

  <!-- #015 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#015</span>
      <span class="tip-title">Cómo usar teflón correctamente</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>El teflón es la cinta más usada en plomería mexicana pero muchos la usan mal, lo que causa fugas.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Aplica siempre en <strong>sentido de la rosca</strong> (horario cuando ves la punta del tubo). Si lo enrollas al revés, la rosca lo desenrolla al armar.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Da un mínimo de 4 vueltas para roscas pequeñas (1/2") y 6–8 para roscas de 3/4" o mayores. Más capas = mejor sello.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Estira ligeramente la cinta mientras la enrollas — así entra en las crestas de la rosca y sella mejor.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Para conexiones de gas, usa teflón amarillo específico para gas o un sellador de hilo tipo Loctite 567. El teflón blanco normal NO es suficiente para gas.</div></li>
      </ul>
    </div>
  </div>

  <!-- #016 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#016</span>
      <span class="tip-title">Aumentar la presión de agua baja en casa</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Causa más común:</strong> aireador de la llave tapado con sarro. Limpia todos los aireadores (ver tip #012) — muchas veces esto solo resuelve el problema.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Segunda causa:</strong> llave de paso no completamente abierta. Revisa todas las llaves de paso — algunas quedan entreabiertas tras una reparación.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Problema de presión en toda la casa:</strong> puede ser que la presión municipal sea baja. La solución estándar en México es instalar una hidroneumática (bomba presurizadora) conectada al tinaco.</div></li>
        <li class="tip-step"><div class="ts">4</div><div><strong>Solo en una llave:</strong> revisa si la tubería tiene reducción o dobleces muy cerrados que restringen el flujo.</div></li>
      </ul>
    </div>
  </div>

  <!-- #017 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#017</span>
      <span class="tip-title">Instalar una regadera nueva</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra el paso del agua. Retira la regadera vieja: generalmente solo atornillada en el brazo de pared. Gira en antihorario.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Limpia la rosca del brazo con un cepillo. Aplica teflón (6 vueltas) en la rosca del brazo.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Enrosca la nueva regadera a mano hasta que toque, luego 1/2 vuelta más con llave ajustable. No sobre-aprietes — puedes romper el brazo de cobre.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Abre el paso y verifica que la unión no gotee. La regadera debe quedar apuntando ligeramente hacia adelante para que el agua caiga dentro de la tina o zona de baño.</div></li>
      </ul>
    </div>
  </div>

  <!-- #018 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#018</span>
      <span class="tip-title">Silicón para baño: cómo aplicarlo sin que quede horrible</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>El silicón sella uniones entre azulejo y muebles. Mal aplicado se ve manchado y feo; bien aplicado dura años.</p>
      <div class="materiales">
        <span class="mat">Silicón para baño (fungicida)</span><span class="mat">Pistola para silicón</span><span class="mat">Cinta de carrocero</span><span class="mat">Alcohol isopropílico</span>
      </div>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Limpia perfectamente la superficie con alcohol. El silicón no pega sobre superficies sucias, húmedas o con silicón viejo.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Pega cinta de carrocero 2 mm a cada lado de la línea donde irá el silicón — esto define bordes perfectos.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Aplica el silicón en un movimiento continuo y uniforme. Pasa el dedo mojado en agua jabonosa para alisar el cordón en un solo movimiento.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Retira la cinta de carrocero de inmediato antes de que el silicón seque. Deja curar 24 horas antes de mojar.</div></li>
      </ul>
    </div>
  </div>

  <!-- #019 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#019</span>
      <span class="tip-title">Cambiar el flotador y la válvula de entrada del WC</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra la llave de paso del WC. Jala la cadena para vaciar la cisterna. Desconecta la manguera de entrada de agua (tuerca de plástico abajo de la cisterna).</div></li>
        <li class="tip-step"><div class="ts">2</div><div>La válvula de entrada completa se retira quitando la tuerca inferior. Sale hacia abajo. Lleva la vieja a la ferretería para conseguir la misma.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Instala la nueva. Ajusta la altura del flotador para que el agua corte 2 cm abajo del tubo de rebose.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Abre el paso lentamente. Verifica que llene y corte correctamente. El llenado normal toma 1–2 minutos.</div></li>
      </ul>
    </div>
  </div>

  <!-- #020 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#020</span>
      <span class="tip-title">Instalar una llave de jardín o exterior</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra el paso del agua. Localiza el punto de la tubería donde harás la derivación.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Para derivar en PVC: corta el tubo, instala una tee (T) con pegamento PVC. La salida de la T irá a tu nueva llave.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Instala una llave de paso antes de la llave de jardín para poder cerrarla independientemente.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Aplica teflón en todas las roscas. La llave de jardín siempre lleva una canastilla (reducción) si la tubería es de 1/2".</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Si el tubo queda a la intemperie, protégelo con pintura o manga de foam para evitar que el sol lo degrade.</div></li>
      </ul>
    </div>
  </div>

  <!-- #021 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#021</span>
      <span class="tip-title">Reparar un tubo roto por helada o golpe (empalme)</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra el paso, seca la zona. Corta el tramo dañado con cortador o sierra dejando cortes a escuadra.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Mide la longitud que cortaste. Corta un tubo nuevo de la misma medida más 4 cm (2 cm para cada cople).</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Instala dos coples de unión (uno en cada extremo). Para PVC, usa pegamento. Para cobre, usa coples de compresión o soldadura.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Deja curar 2 horas antes de abrir el paso. Verifica con presión completa durante 5 minutos.</div></li>
      </ul>
    </div>
  </div>

  <!-- #022 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#022</span>
      <span class="tip-title">Instalar un filtro de agua bajo el fregadero</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra la llave de paso del fregadero. Desconecta la manguera que va de la llave de paso a la llave del fregadero.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>La mayoría de filtros de cartucho traen dos mangueras: entrada (desde la llave de paso) y salida (hacia la llave del fregadero o llave de agua purificada separada).</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Conecta respetando la dirección de flujo marcada en el filtro (flecha o indicación IN/OUT).</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Fija el filtro a la pared interior del mueble con los tornillos incluidos. Cambia el cartucho cada 6 meses o cuando note mal sabor.</div></li>
      </ul>
    </div>
  </div>

  <!-- #023 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#023</span>
      <span class="tip-title">Cómo identificar tipos de tubería en una casa antigua</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Galvanizado (gris metálico, roscado):</strong> común en casas pre-1980. Se oxida internamente y reduce el flujo. Material ya obsoleto — cuando falla, conviene reemplazar con PVC o cobre.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Cobre (color cobrizo):</strong> duradero, buena conductividad térmica. Se repara con soldadura o coples de compresión.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>PVC blanco/crema:</strong> agua fría y drenaje. Muy común desde los 90. Se une con pegamento PVC.</div></li>
        <li class="tip-step"><div class="ts">4</div><div><strong>CPVC amarillo:</strong> agua caliente. Se une con pegamento CPVC específico (no confundir con el blanco).</div></li>
        <li class="tip-step"><div class="ts">5</div><div><strong>Multicapa (aluminio-plástico, color blanco brillante):</strong> cada vez más común. Se conecta con coples de compresión o de prensado.</div></li>
      </ul>
    </div>
  </div>

  <!-- #024 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#024</span>
      <span class="tip-title">Instalar un boiler solar (calentador solar)</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <p>Muy rentable en México por la cantidad de sol disponible. La parte hidráulica la puedes hacer tú; solo la instalación eléctrica del respaldo requiere técnico.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>El boiler solar tiene: colectores en el techo, tinaco de agua caliente y conexiones de agua fría/caliente. Sigue las instrucciones del fabricante para la altura del tinaco respecto a los colectores.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Conecta el agua fría al tinaco (entrada marcada "agua fría"). La salida de agua caliente va hacia tu red de distribución interna.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Instala una válvula anti-retorno en la entrada de agua fría — evita que el agua caliente suba hacia la red fría.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Purga el sistema: abre todas las llaves de agua caliente hasta que salga flujo continuo sin burbujas de aire.</div></li>
      </ul>
    </div>
  </div>

  <!-- #025 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header">
      <span class="tip-n">#025</span>
      <span class="tip-title">Qué hacer cuando se rompe una tubería empotrada</span>
      <span class="tip-arrow">›</span>
    </div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra el paso general inmediatamente. El agua en paredes puede causar daño eléctrico además del estructural.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Localiza el punto mojado. Con un mazo y cincel, abre la pared 10 cm a cada lado de la mancha para encontrar el tramo roto.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Repara el tubo (ver tip #021). Antes de tapar, deja pasar agua 10 minutos verificando que no haya fugas.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Remendona la pared con mezcla de cemento blanco y arena fina. Deja secar 48 horas antes de pintar o colocar azulejo.</div></li>
      </ul>
      <div class="alerta">⚠️ Si la pared mojada tiene instalación eléctrica, apaga el circuito del tablero antes de tocar cualquier cosa.</div>
    </div>
  </div>

  <!-- #026 #027 #028 #029 #030 #031 #032 #033 #034 -->

  <!-- #026 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#026</span><span class="tip-title">Instalar una llave mezcladora de regadera</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra paso de agua fría y caliente. Retira la llave vieja desmontando el maneral (tornillo Allen bajo tapa decorativa) y las tuercas de las entradas.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Verifica la distancia entre centros de las entradas en el muro. La distancia estándar en México es 15 cm. Compra una mezcladora compatible.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Aplica teflón en los conectores. Instala primero los adaptadores del muro, luego el cuerpo de la mezcladora. Las entradas frío/caliente suelen marcarse C (azul) y H (rojo).</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Conecta el brazo de la regadera. Verifica sin fugas antes de instalar la placa decorativa.</div></li>
      </ul>
    </div>
  </div>

  <!-- #027 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#027</span><span class="tip-title">Cambiar la manguera del WC (flexible)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Cierra la llave de paso del WC. Vacía la cisterna. Desconecta la manguera vieja — tuerca abajo (hacia la llave de paso) y tuerca arriba (hacia la cisterna).</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Lleva la manguera vieja a la ferretería para conseguir la misma longitud. Las medidas estándar son 25, 30, 40 y 50 cm.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Instala la nueva apretando las tuercas a mano + 1/4 vuelta con llave. Aprietas demasiado = rompes la tuerca de plástico de la cisterna.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Abre la llave de paso lentamente y verifica ambos extremos.</div></li>
      </ul>
    </div>
  </div>

  <!-- #028 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#028</span><span class="tip-title">Desconectar y conectar el drenaje del fregadero</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>No necesitas cerrar el agua. Coloca una cubeta bajo el sifón. Gira las tuercas del sifón con la mano (antihorario). Si están muy duras, usa llave de plástico — no metal o aplanas las tuercas.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>El sifón completo sale en 2–3 piezas. Anota cómo estaba armado o fotografía antes de desarmar.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Al reinstalar, los empaques de goma van en la ranura correspondiente. No uses teflón en drenaje — solo en agua a presión.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Las tuercas del sifón deben quedar solo "firmes a mano" — apretar con llave puede romper el plástico.</div></li>
      </ul>
    </div>
  </div>

  <!-- #029 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#029</span><span class="tip-title">Instalar una trampa de grasa en el drenaje de la cocina</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>Obligatoria en cocinas comerciales en México, muy recomendable en casa. Previene tapones de grasa en la red municipal.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Instala entre el sifón del fregadero y la salida al drenaje general. El agua con grasa entra por arriba, la grasa flota y el agua limpia sale por debajo hacia el drenaje.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Conecta con tubo PVC de 2" (diámetro estándar del drenaje de cocina). Usa pegamento PVC en todas las uniones.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Limpia la trampa de grasa cada mes — destapa la tapa, extrae la grasa acumulada y tírala a la basura (nunca al drenaje).</div></li>
      </ul>
    </div>
  </div>

  <!-- #030 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#030</span><span class="tip-title">Cómo usar una sonda manual de plomería</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>La sonda (o serpiente) es un cable flexible de metal con una punta en espiral. Se introduce por el desagüe para alcanzar obstrucciones profundas.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Introduce la punta y gira la manivela en sentido horario mientras avanzas. La rotación ayuda a navegar las curvas del tubo.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Al sentir resistencia: gira hacia adelante para perforar el tapón o hacia atrás para engancharlo y jalarlo.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Retira lentamente. Enjuaga con agua caliente abundante. Limpia la sonda con un trapo mientras la retiras — evita esparcir la suciedad.</div></li>
      </ul>
    </div>
  </div>

  <!-- #031 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#031</span><span class="tip-title">Prevenir y tratar la humedad en muros por tubería</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Una mancha de humedad en la pared que no desaparece aunque no llueva suele ser una fuga de tubería empotrada. Toca la pared — si está caliente puede ser agua caliente; si está fría, es agua fría o drenaje.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Para confirmar sin abrir: cierra el paso general, lleva el indicador del medidor a cero y espera 2 horas. Si avanzó, hay fuga activa.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Una vez reparada la fuga, aplica impermeabilizante acrílico en la zona afectada antes de pintar. Solo impermeabilizante — sin reparar la fuga el impermeabilizante no sirve de nada.</div></li>
      </ul>
    </div>
  </div>

  <!-- #032 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#032</span><span class="tip-title">Instalar reductor de presión (si la presión es muy alta)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>La presión excesiva (más de 5 kg/cm²) desgasta llaves, mangueras y provoca golpe de ariete. En zonas altas de presión municipal, el reductor protege toda la instalación.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Instala después de la llave general de entrada, antes de toda la instalación. Se instala en línea en sentido del flujo.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Aplica teflón en ambas roscas de entrada y salida. La presión de salida se ajusta con el tornillo central — 2.5–3 kg/cm² es lo ideal para uso doméstico.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Instala también un manómetro aguas abajo del reductor para monitorear la presión regularmente.</div></li>
      </ul>
    </div>
  </div>

  <!-- #033 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#033</span><span class="tip-title">Reparar el desagüe de la tina o regadera</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>El desagüe lento de la tina suele ser pelo y jabón acumulado justo bajo la coladera. Retira la coladera (un tornillo central) y extrae la acumulación con un gancho improvisado.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Si no mejora, el tapón está más profundo. Usa el método de bicarbonato + vinagre (ver tip #003) o una sonda delgada.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Para cambiar la coladera: gira a la izquierda con un desarmador plano. Aplica silicón en el aro exterior antes de colocar la nueva. Aprieta desde abajo con la contratuerca.</div></li>
      </ul>
    </div>
  </div>

  <!-- #034 -->
  <div class="tip-card" data-cat="p" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#034</span><span class="tip-title">Mantenimiento del boiler de gas: limpieza y verificación anual</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>El boiler de depósito (cilindro grande) debe revisarse anualmente. Puedes hacer parte del mantenimiento tú mismo.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Lo que puedes hacer tú:</strong> purgar los sedimentos abriendo la válvula de purga en la parte inferior del boiler (con cubeta debajo). Sale agua café con sedimentos. Cierra cuando salga agua limpia.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Verificar la válvula de seguridad (alivio de presión): jala la palomita brevemente — debe salir agua y volver a cerrar sola. Si no funciona, cámbiala (conexión roscada simple).</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Lo que requiere técnico certificado:</strong> revisión del piloto, quemador, termostato y conexiones de gas. Hazlo al inicio del invierno.</div></li>
      </ul>
      <div class="alerta">⚠️ Nunca ignores olor a gas cerca del boiler. Apaga el gas, ventila el área y llama a un técnico antes de volver a encender.</div>
    </div>
  </div>
</div><!-- /plomeria -->

<!-- ══════════════ ELECTRICIDAD ══════════════ -->
<div class="cat-section" data-sec="e">
  <div class="cat-header">
    <span class="cat-num">02</span>
    <span class="cat-title e">Electricidad</span>
    <span class="cat-badge badge-e">33 tips · #035–#067</span>
  </div>

  <!-- #035 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#035</span><span class="tip-title">Regla de oro: desconecta siempre el circuito en el tablero</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>Nunca trabajes en instalaciones eléctricas con la corriente activa. En México la mayoría de instalaciones domésticas son 127V — suficiente para matar.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Identifica el circuito que alimenta la zona de trabajo. En el tablero (caja de breakers) apaga el breaker correspondiente.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Verifica con un detector de voltaje</strong> (apagador tipo pluma, $60–80 MXN en ferretería). Acerca al contacto o cable — si pita o enciende, hay corriente aunque el breaker esté apagado.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Si no sabes cuál breaker es, apaga el general. Pega un papel en el tablero: "Trabajando — no encender".</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Los cables en México: negro o rojo = fase (caliente), blanco = neutro, verde o desnudo = tierra. El negro/rojo es el peligroso.</div></li>
      </ul>
      <div class="alerta">⚠️ Si en tu casa los colores de cables no corresponden a ese estándar (instalaciones viejas o mal hechas), verifica con el detector antes de tocar cualquier cable.</div>
    </div>
  </div>

  <!-- #036 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#036</span><span class="tip-title">Cambiar un foco o lámpara (todos los tipos)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Foco de rosca (E27):</strong> apaga el interruptor. Gira antihorario para sacar, horario para poner. Si está caliente, espera 2 minutos — el vidrio caliente puede quemarte.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Foco de bayoneta (B22):</strong> presiona hacia adentro, gira antihorario 1/4 vuelta y jala. Para instalar: inserta, presiona y gira horario hasta encajar.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Foco pin (GU10, MR16):</strong> gira antihorario 1/4 vuelta y jala. No toques el vidrio con los dedos en los de halógeno — la grasa lo quema.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Al cambiar a LED: verifica que el wattaje sea compatible con el dimmer si tienes. No todos los LED son dimerizables. Los LED no necesitan esperar para encender como los ahorradores.</div></li>
      </ul>
    </div>
  </div>

  <!-- #037 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#037</span><span class="tip-title">Cambiar un contacto (tomacorriente) dañado</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <div class="materiales">
        <span class="mat">Desarmadores plano y estrella</span><span class="mat">Detector de voltaje</span><span class="mat">Contacto nuevo (mismo tipo)</span><span class="mat">Cinta aislante</span>
      </div>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Apaga el breaker del circuito. Verifica con detector de voltaje que no haya corriente en el contacto.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Retira la placa decorativa (1 tornillo central). Retira los 2 tornillos del contacto a la caja. El contacto sale con sus cables.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Fotografía la conexión de cables antes de desconectar. El cable negro va al tornillo dorado (fase), el blanco al tornillo plateado (neutro), el verde/desnudo al tornillo verde (tierra).</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Conecta los mismos cables al nuevo contacto en las mismas posiciones. Aprieta los tornillos firmemente — un cable suelto genera calor y puede causar incendio.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Dobla los cables con cuidado en acordeón para que quepan en la caja. Reinstala el contacto y la placa. Enciende el breaker y prueba.</div></li>
      </ul>
    </div>
  </div>

  <!-- #038 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#038</span><span class="tip-title">Cambiar un interruptor de luz sencillo</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Apaga el breaker. Verifica con detector. Retira la placa y los tornillos del interruptor.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Un interruptor sencillo tiene 2 cables negros (fase) conectados a sus 2 tornillos. No importa cuál va en cuál terminal — el interruptor solo abre o cierra el circuito de la fase.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Conecta los 2 cables al nuevo interruptor. Aprieta bien. Dobla los cables y mete el interruptor en la caja.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Instala placa y enciende el breaker. Si el foco no enciende, verifica que el interruptor no esté en posición OFF.</div></li>
      </ul>
    </div>
  </div>

  <!-- #039 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#039</span><span class="tip-title">Entender y resetear el tablero de breakers</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Un breaker "disparado" queda en posición intermedia (ni ON ni OFF completamente). Se ve diferente a los demás. Para resetear: mueve primero a OFF completamente, luego a ON.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Si el breaker dispara de nuevo al encender, hay una sobrecarga o cortocircuito activo. No forces el breaker — desconecta aparatos del circuito primero.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Etiqueta los breakers si no están identificados: apaga uno, ve qué circuito perdió luz, anota. Repite con cada uno — tarda 20 minutos pero ahorra mucho tiempo futuro.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Si un breaker dispara repetidamente sin causa aparente, puede estar dañado o haber una fuga a tierra. Ese caso sí requiere electricista.</div></li>
      </ul>
    </div>
  </div>

  <!-- #040 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#040</span><span class="tip-title">Instalar un contacto con toma de tierra (polarizado)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>Los contactos con tierra (3 orificios) protegen contra descargas eléctricas. En México muchas casas viejas solo tienen 2 cables — se puede agregar tierra física.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Verifica si en la caja hay cable verde o desnudo. Si sí: conéctalo al tornillo verde del nuevo contacto polarizado.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Si no hay cable de tierra: instala un contacto GFCI (con botones Test/Reset). Protege contra descarga aunque no tenga tierra física. Es la solución aceptada por la NOM para instalaciones sin tierra.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Para agregar tierra física: instala una varilla de tierra (electrodo de tierra) en el exterior, conectada con cable verde #10 al tornillo de tierra del tablero y de ahí a los contactos.</div></li>
      </ul>
    </div>
  </div>

  <!-- #041 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#041</span><span class="tip-title">Instalar un contacto GFCI (con protección de falla a tierra)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>Obligatorio por NOM en baños, cocinas y exteriores. Evita electrocución al detectar fugas de corriente.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Apaga el breaker. El GFCI tiene 4 terminales: LINE (lado de entrada, el que viene del tablero) y LOAD (el que va a otros contactos aguas abajo).</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Conecta los cables que vienen del tablero al lado LINE (marcado). Si hay cables que siguen a otros contactos, van al lado LOAD y esos contactos también quedan protegidos.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Si solo proteges ese contacto, solo usa las terminales LINE y deja las LOAD sin conectar con las tapas incluidas.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Enciende el breaker. Presiona el botón TEST — el GFCI debe disparar (quedar sin corriente). Presiona RESET para restablecer.</div></li>
      </ul>
    </div>
  </div>

  <!-- #042 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#042</span><span class="tip-title">Empatar y empalmar cables correctamente</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>Un empalme mal hecho es la principal causa de incendios eléctricos en hogares mexicanos.</p>
      <div class="materiales">
        <span class="mat">Conectores de tuerca (wire nuts)</span><span class="mat">Cinta aislante 3M</span><span class="mat">Pinzas pela-cables</span>
      </div>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Pela 2 cm de aislamiento de cada cable con las pinzas. Tuerce los conductores desnudos juntos en sentido horario mínimo 3 vueltas.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Coloca un conector de tuerca (wire nut) y gira horario hasta que quede firme. Jala cada cable — no debe soltarse.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Envuelve el conector con 3 capas de cinta aislante empezando por debajo del conector sobre el aislamiento. Nunca cables desnudos expuestos.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Los empalmes siempre deben quedar dentro de cajas de registro accesibles — nunca ocultos dentro de paredes sin caja.</div></li>
      </ul>
      <div class="alerta">⚠️ Nunca uses cinta aislante como único medio de empalme. Siempre usa wire nuts + cinta.</div>
    </div>
  </div>

  <!-- #043 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#043</span><span class="tip-title">Instalar un foco de sensor de movimiento exterior</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Apaga el circuito en el tablero. Retira la lámpara vieja. Los focos de sensor tienen 3 cables: negro (fase), blanco (neutro), verde (tierra).</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Conecta negro con negro, blanco con blanco, verde con tierra o envuelve con cinta si no hay tierra.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Ajusta el sensor: el ángulo de detección (generalmente 120–180°) y la sensibilidad de luz (para que solo encienda de noche).</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Asegura que el artefacto sea para exterior (clasificación IP65 mínimo) si queda expuesto a lluvia.</div></li>
      </ul>
    </div>
  </div>

  <!-- #044 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#044</span><span class="tip-title">Instalar un apagador de 3 vías (doble conmutador)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>Para controlar una misma lámpara desde dos puntos (entrada y recámara, por ejemplo). Requiere cable de 3 conductores entre los dos apagadores.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Un apagador de 3 vías tiene 3 terminales: uno COM (común, marcado) y dos travellers (viajeros). El COM del primer apagador recibe la fase. El COM del segundo va a la lámpara.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Los dos cables viajeros (generalmente rojo y negro) conectan los travellers de un apagador con los del otro.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Si al conectar la lámpara no funciona o no conmuta correctamente, intercambia los dos cables viajeros en uno de los apagadores — el orden sí importa.</div></li>
      </ul>
    </div>
  </div>

  <!-- #045 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#045</span><span class="tip-title">Extender un circuito para agregar un nuevo contacto</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>El método más sencillo es derivar desde un contacto existente cercano. Apaga el circuito. Saca el contacto existente de su caja.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Instala una caja nueva para el contacto adicional. Pasa el cable (calibre 12 para circuitos de 20A, calibre 14 para 15A) entre las dos cajas por dentro de la pared o en canaleta de superficie.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>En el contacto existente: conecta los cables nuevos a los mismos tornillos del contacto existente (negro con negro, blanco con blanco). Los tornillos de los contactos aceptan 2 cables.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Conecta el nuevo contacto en la nueva caja. Enciende el circuito y verifica ambos contactos.</div></li>
      </ul>
      <div class="alerta">⚠️ No agregues más de 3–4 contactos al mismo circuito sin verificar la carga total. Calcula: suma los watts de los aparatos conectados ÷ 127V = Amperes necesarios.</div>
    </div>
  </div>

  <!-- #046 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#046</span><span class="tip-title">Instalar un ventilador de techo</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>El ventilador debe montarse en una caja de techo especial para ventiladores (con soporte de palometa o barra transversal) — las cajas de luz normales no soportan el peso y movimiento.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Instala el soporte según instrucciones del ventilador. Cuelga el motor del gancho de seguridad (gancho en "J") durante la conexión eléctrica.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Conecta negro a negro, blanco a blanco, y tierra. Si el ventilador tiene luz integrada, hay un cable adicional (generalmente azul) para el circuito de la luz.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Instala las paletas siempre en posición escalonada en estrella para que queden a la misma altura. Una paleta desnivelada genera vibración y ruido.</div></li>
      </ul>
    </div>
  </div>

  <!-- #047 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#047</span><span class="tip-title">Instalar canaleta de PVC para cables en superficie</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>Cuando no puedes meter el cable dentro de la pared, la canaleta es la solución limpia y segura.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Planea el recorrido. La canaleta siempre va horizontal o vertical — nunca diagonal.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Fija la base de la canaleta con tornillos o cinta adhesiva doble cara (para superficies lisas). En concreto, usa taquetes.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Mete el cable, coloca la tapa presionando hasta escuchar el clic. No sobrecargas la canaleta — el cable debe entrar sin forzar.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Usa esquineros y accesorios específicos de la canaleta para los cambios de dirección — no dobles el cable en ángulos agudos.</div></li>
      </ul>
    </div>
  </div>

  <!-- #048 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#048</span><span class="tip-title">Usar el multímetro para diagnósticos eléctricos básicos</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Medir voltaje en el contacto:</strong> pon el multímetro en ACV (voltaje alterno) 200V. Las puntas en los orificios del contacto deben marcar ~127V. Si marca 0, no hay corriente.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Medir continuidad:</strong> modo 🔔 (continuidad). Con corriente apagada, toca ambas puntas a los extremos del cable. Si pita, el cable está continuo (sin corte).</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Verificar si un fusible está quemado:</strong> modo continuidad, puntas en ambos extremos del fusible. Pita = está bien. No pita = está quemado.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Un multímetro básico cuesta $150–250 MXN y es la herramienta más útil para diagnóstico eléctrico. Vale mucho la inversión.</div></li>
      </ul>
    </div>
  </div>

  <!-- #049 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#049</span><span class="tip-title">Instalar un timbre eléctrico</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Los timbres eléctricos funcionan a 12–24V AC (bajo voltaje). El transformador reduce los 127V de la pared a ese voltaje seguro.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Instala el transformador cerca del tablero o de un contacto — se conecta a 127V en el lado de alta y da 16V en el lado de baja.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Del transformador salen 2 cables delgados: uno va directamente a la campana del timbre y otro pasa por el botón del timbre en la puerta. El botón solo abre o cierra ese circuito.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>El cable del timbre puede ser de calibre 22 o 18 (cable fino) — no necesita ser cable eléctrico grueso. Para exteriores, usa cable para intemperie.</div></li>
      </ul>
    </div>
  </div>

  <!-- #050 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#050</span><span class="tip-title">Calcular el calibre de cable correcto</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>Un cable de calibre incorrecto (muy delgado para la carga) se calienta y puede causar incendio. En México los calibres más comunes son AWG.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Calibre 14 AWG:</strong> circuitos de iluminación, máximo 15A. Para recámaras y salas.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Calibre 12 AWG:</strong> contactos de cocina, baño y circuitos generales, máximo 20A. El más común en circuitos domésticos modernos.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Calibre 10 AWG:</strong> circuitos de 30A — secadoras, hornos, A/C de ventana grande.</div></li>
        <li class="tip-step"><div class="ts">4</div><div><strong>Calibre 8 AWG:</strong> circuitos de 40–50A — calentadores de agua eléctricos, A/C central.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Regla fácil: si dudas, sube un calibre. Un cable más grueso nunca causa problema; uno más delgado sí.</div></li>
      </ul>
    </div>
  </div>

  <!-- #051 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#051</span><span class="tip-title">Instalar tiras LED (decoración e iluminación)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Las tiras LED funcionan a 12V DC. Necesitas una fuente de poder (transformador 12V) proporcional a los watts totales de la tira + 20% de margen.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Las tiras tienen líneas de corte marcadas cada 3–5 cm. Solo corta en esas líneas, nunca en otro punto.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Para unir tiras: usa conectores específicos (clip-on connectors) o suelda con cautín. El + y − deben coincidir — al revés la tira no enciende.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Para instalar en esquinas o cornisas, usa perfil de aluminio con difusor — protege la tira, disipa el calor y da un acabado profesional sin líneas visibles de LED.</div></li>
      </ul>
    </div>
  </div>

  <!-- #052 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#052</span><span class="tip-title">Cómo pasar cable por dentro de la pared sin abrir</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Haz dos pequeños agujeros (3 cm) en la pared: uno donde sale el cable y otro donde entra — generalmente arriba y abajo de la misma pared.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Introduce una vara flexible (guía de cable o una percha de ropa doblada) por el agujero superior. Baja hasta que salga por el inferior.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Amarra el cable a la punta de la vara con cinta. Jala la vara hacia arriba — el cable sube con ella.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Si hay vigas o travesaños que bloquean el paso, necesitarás hacer un agujero intermedio o usar un taladro largo (broca de extensión) para hacer un canal desde un punto de acceso.</div></li>
      </ul>
    </div>
  </div>

  <!-- #053 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#053</span><span class="tip-title">Instalar un apagador inteligente WiFi</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Apaga el breaker. La mayoría de apagadores inteligentes requieren cable neutro (blanco) además de la fase. Verifica si en tu caja hay cable neutro antes de comprar.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Conecta: fase (negro) al terminal LINE, neutro (blanco) al terminal NEUTRAL, y la salida al terminal LOAD (hacia la lámpara). La tierra al terminal GND si la hay.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Muchos modelos son más profundos que los apagadores normales — verifica que los cables quepan al doblarlos dentro de la caja.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Enciende el breaker y sigue las instrucciones de la app para conectar a WiFi. La mayoría solo funciona en redes 2.4 GHz (no 5 GHz).</div></li>
      </ul>
    </div>
  </div>

  <!-- #054 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#054</span><span class="tip-title">Instalar un contacto para A/C (220V)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>Los A/C de ventana grandes y los minisplits requieren circuito dedicado de 220V en México.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Un circuito de 220V usa dos fases del tablero (2 breakers vinculados = breaker doble). Requiere cable con 3 conductores: dos fases + tierra.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>El trabajo del tablero (instalar el breaker doble y sacar los cables) requiere electricista certificado si no tienes experiencia — el tablero tiene partes que permanecen energizadas aunque apagues el general.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Lo que puedes hacer tú: instalar la caja y el contacto especial (NEMA 6-20 para 220V/20A o NEMA 14-30 para 220V/30A) una vez que el electricista haya pasado el cable.</div></li>
      </ul>
      <div class="alerta">⚠️ Nunca trabajes dentro de un tablero eléctrico sin desconectar la acometida. El tablero tiene partes energizadas incluso con el breaker general apagado.</div>
    </div>
  </div>

  <!-- #055 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#055</span><span class="tip-title">Cómo detectar un cortocircuito</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>El cortocircuito ocurre cuando el conductor fase toca al neutro o tierra sin pasar por una carga — el breaker dispara inmediatamente.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Para localizar: desconecta todos los aparatos y luminarias del circuito. Enciende el breaker. Si no dispara, el problema es en un aparato — reconéctalo de uno en uno hasta que dispare.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Si el breaker dispara incluso con todo desconectado, el cortocircuito está en el cable mismo — cable pelado que toca la pared metálica de la caja o cable mordido por roedores.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Revisa visualmente todas las cajas de registro accesibles buscando cable dañado, quemado o pelado.</div></li>
      </ul>
    </div>
  </div>

  <!-- #056 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#056</span><span class="tip-title">Instalar un regulador de voltaje para equipos sensibles</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>En México los apagones y variaciones de voltaje son comunes. Los reguladores protegen televisores, computadoras y refrigeradores.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>El regulador va entre el contacto y el aparato. Solo enchúfalo — no requiere instalación eléctrica.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Elige el regulador por VA (volt-amperes): necesitas al menos el doble de los watts del aparato a proteger. Refrigerador 200W → regulador mínimo 400 VA.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Para computadoras e impresoras: un UPS (no interrumpible) da mayor protección que un regulador simple — además mantiene el equipo encendido durante apagones cortos.</div></li>
      </ul>
    </div>
  </div>

  <!-- #057 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#057</span><span class="tip-title">Instalar iluminación bajo gabinetes de cocina</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>La opción más sencilla: tiras LED con adhesivo 3M en la parte inferior del gabinete. Conecta a transformador 12V y enchufa al contacto más cercano.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Para instalación fija: usa perfil de aluminio empotrado. Apaga el circuito y conecta un cable desde el contacto más cercano hasta la zona de los gabinetes, usando canaleta para un acabado limpio.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Instala un apagador pequeño o usa un contacto con interruptor para controlar la iluminación independientemente de la luz general.</div></li>
      </ul>
    </div>
  </div>

  <!-- #058 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#058</span><span class="tip-title">Cambiar el enchufe dañado de un aparato</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Desenchufa el aparato. Corta el cable 10 cm después del enchufe dañado. Pela 3 cm del exterior del cable y 1 cm de cada conductor interno.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>El enchufe nuevo se abre con un tornillo. Introduce los conductores: negro a la terminal marcada (+) o L, blanco a la marcada (−) o N. Si hay tierra, verde al pin redondo.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Aprieta los tornillos de las terminales firmemente. Asegura que el prensacable sujete la cubierta del cable — no los conductores internos.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Cierra el enchufe, aprieta el tornillo exterior. Prueba con el multímetro en continuidad antes de enchufar al contacto.</div></li>
      </ul>
    </div>
  </div>

  <!-- #059 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#059</span><span class="tip-title">Instalar una lámpara de emergencia (recargable)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Las lámparas de emergencia enchufables se cargan mientras hay corriente y encienden automáticamente en un corte de luz. Ideales en México donde los apagones son comunes.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Para instalar una lámpara de emergencia cableada (en caja de luz): apaga el breaker, conecta negro con negro, blanco con blanco a la caja donde antes iba una lámpara normal.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Estas lámparas tienen batería interna que se carga permanentemente desde la red y se activa en corte. La batería dura 3–5 horas de respaldo.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Coloca una en el pasillo, una en la cocina y una en la escalera si la hay — los puntos más peligrosos en la oscuridad.</div></li>
      </ul>
    </div>
  </div>

  <!-- #060 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#060</span><span class="tip-title">Instalar un detector de humo</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Coloca en el techo de recámaras, pasillo central y cocina (en la cocina, a 1 metro de la estufa para evitar falsas alarmas por vapor).</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Detectores de batería:</strong> solo atornilla la base al techo con 2 tornillos y taquetes. Inserta la batería y presiona TEST para verificar.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Detectores cableados:</strong> se conectan a 127V. Apaga el breaker, conecta negro y blanco a los cables de la caja. Muchos también tienen batería de respaldo.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Prueba mensualmente presionando el botón TEST. Cambia la batería cada año aunque no haya sonado nunca. Cambia el detector completo cada 10 años.</div></li>
      </ul>
    </div>
  </div>

  <!-- #061 #062 #063 #064 #065 #066 #067 -->

  <!-- #061 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#061</span><span class="tip-title">Instalar un contacto exterior resistente a la lluvia</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Usa cajas exteriores (tipo intemperie, gris o verde) con tapa con bisagra sellada. El contacto debe ser GFCI para exterior.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Sella la entrada del cable a la caja con silicón para exteriores. Sella también la unión entre la caja y la pared.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Usa cable con aislamiento para intemperie (tipo THWN/THHN) si el cable queda expuesto. Para cable dentro de pared, el estándar THW es suficiente.</div></li>
      </ul>
    </div>
  </div>

  <!-- #062 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#062</span><span class="tip-title">Cómo hacer una cintilla de cable ordenada en la pared</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Para cables de TV, internet, bocinas, etc. que no son eléctricos, usa prensacables de superficie o cintillas plásticas con adhesivo.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Separa siempre el cableado eléctrico del cableado de datos/audio — nunca en la misma canaleta. La corriente induce interferencia en las señales.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Para pasar cables detrás de pared sin abrir, sigue el método del tip #052. El cable HDMI, coaxial y de red es lo suficientemente flexible para pasarse con la guía.</div></li>
      </ul>
    </div>
  </div>

  <!-- #063 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#063</span><span class="tip-title">Instalar punto de red (cable ethernet) en la pared</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Pasa el cable cat6 por la pared o canaleta hasta la ubicación deseada. No dobles el cable en ángulos menores a 90° — el radio mínimo de doblez es 4 veces el diámetro del cable.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Usa una caja de pared para red (RJ45 keystone) y herramienta de impacto para terminar el cable en el conector. El orden de colores: estándar T568B (naranja-blanco, naranja, verde-blanco, azul, azul-blanco, verde, café-blanco, café).</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Prueba la conexión con un verificador de cable de red antes de cerrar la caja.</div></li>
      </ul>
    </div>
  </div>

  <!-- #064 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#064</span><span class="tip-title">Cambiar la placa de un apagador o contacto (cosmético)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>La placa (tapa decorativa) tiene un tornillo central visible. Desatornilla, retira la placa vieja.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>No necesitas apagar el breaker para cambiar solo la placa — no tocarás cables. Aun así evita introducir objetos metálicos en los orificios del contacto.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Las placas son estándar en México — el mismo tornillo y tamaño para casi todas las marcas (Leviton, Vimar, Gewiss). Solo verifica que sea para apagador sencillo, doble, contacto, o combinación según sea el caso.</div></li>
      </ul>
    </div>
  </div>

  <!-- #065 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#065</span><span class="tip-title">Instalar un foco empotrado (downlight)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Usa una sierra campana del diámetro del foco (generalmente 3.5" o 4") para hacer el orificio en el plafón de yeso.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Apaga el circuito. Conecta los cables en la caja del foco: negro a negro, blanco a blanco. Muchos focos LED empotrados traen su driver integrado y no necesitan caja adicional.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Introduce el foco en el orificio y presiona hasta que los ganchos de retención hagan clic sobre el plafón. Se sujetan solos.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Para plafones de concreto se necesita caja empotrada (octagonal) instalada antes de colar o abierta con cincel. En plafones de yeso el foco se sujeta directo.</div></li>
      </ul>
    </div>
  </div>

  <!-- #066 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#066</span><span class="tip-title">Cambiar el foco de un reflector exterior (PAR38)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Apaga el interruptor. Si el reflector está muy alto, usa escalera estable — nunca silla o mesa.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>El PAR38 es rosca estándar E26/E27 — gira antihorario para sacar. Puede estar pegado por el calor — da un jalón firme mientras giras.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Al reemplazar por LED: verifica que el nuevo sea compatible con dimmers si tienes. Los PAR38 LED modernos dan la misma luz con 1/4 del consumo.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Verifica que la clasificación de temperatura del LED sea adecuada para exterior (rango de operación -20°C a 45°C mínimo).</div></li>
      </ul>
    </div>
  </div>

  <!-- #067 -->
  <div class="tip-card" data-cat="e" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#067</span><span class="tip-title">Instalar una cámara de seguridad IP (cableada)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Las cámaras IP se alimentan por PoE (Power over Ethernet) — un solo cable cat6 lleva imagen y corriente. Solo necesitas pasar el cable desde el switch PoE hasta la cámara.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Taladra el orificio en la pared o techo para pasar el cable. Instala el soporte de la cámara con taquetes en concreto o tornillos en madera.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Sella el orificio del cable con silicón para exteriores si la cámara queda en exterior — el agua puede seguir el cable hacia adentro.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Apunta la cámara desde la app — la mayoría tienen asistente de ángulo. Evita apuntar directamente al sol o a fuentes de luz que saturen la imagen de noche.</div></li>
      </ul>
    </div>
  </div>
</div><!-- /electricidad -->

<!-- ══════════════ CARPINTERÍA ══════════════ -->
<div class="cat-section" data-sec="c">
  <div class="cat-header">
    <span class="cat-num">03</span>
    <span class="cat-title c">Carpintería</span>
    <span class="cat-badge badge-c">33 tips · #068–#100</span>
  </div>

  <!-- #068 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#068</span><span class="tip-title">Herramientas básicas con las que debes empezar</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>No necesitas todo de inicio. Este es el kit mínimo para 80% de los trabajos de carpintería doméstica en México.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Indispensables:</strong> serrucho universal, martillo de uña, nivel de burbuja, cinta métrica, escuadra, desarmadores (plano y estrella en varios tamaños), lápiz de carpintero.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Muy útiles:</strong> taladro percutor inalámbrico (cambia tu vida), juego de brocas, lijadora de mano o papel de lija (80, 120, 220), prensas tipo C o F.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Para después:</strong> caladora, sierra circular, router. Cómpralas cuando tengas un proyecto específico que las requiera.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Regla general: compra herramienta de calidad media, no la más barata. Una herramienta mala hace el trabajo frustrante y peligroso.</div></li>
      </ul>
    </div>
  </div>

  <!-- #069 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#069</span><span class="tip-title">Poner un taquete en concreto correctamente</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>El 90% de los taquetes que se caen es porque el orificio es de diámetro incorrecto o no se vació el polvo.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>El taquete y la broca deben ser del mismo diámetro. Un taquete #8 requiere broca 8 mm. Un taquete #10 requiere broca 10 mm.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Taladra en modo percutor (martillo + rotación) para concreto. La broca debe ser de punta de widia (tungsteno, punta negra triangular).</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Vacía el polvo del orificio</strong> soplando o con un sorbete. El polvo impide que el taquete expanda correctamente — es la causa #1 de taquetes que no sujetan.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Inserta el taquete a golpes de martillo hasta que quede al ras. Al atornillar, el taquete se expande contra las paredes del orificio creando el agarre.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Para cargas pesadas (cuadros grandes, muebles), usa taquetes de expansión metálicos (Fischer o similares) en lugar de los plásticos.</div></li>
      </ul>
    </div>
  </div>

  <!-- #070 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#070</span><span class="tip-title">Colgar cuadros y espejos perfectamente nivelados</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Decide la altura: el centro del cuadro debe quedar a 150–160 cm del piso (altura promedio de los ojos en México).</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Marca el punto donde irá el clavo o taquete. Si el cuadro tiene alambre en la parte trasera: sostén el cuadro donde quieres, mide desde la parte superior del cuadro hasta el alambre cuando está tenso — esa distancia te dice cuánto bajar el clavo de la parte superior marcada.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Para 2 clavos: mide la distancia exacta entre los ganchos traseros. Márcala en la pared con nivel. Coloca ambos clavos.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Para espejos pesados: usa taquetes #10 con tornillo de ojillo. Un espejo de 10 kg requiere mínimo 2 puntos de anclaje en concreto.</div></li>
      </ul>
    </div>
  </div>

  <!-- #071 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#071</span><span class="tip-title">Cortar madera con serrucho sin que se astille</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Marca la línea de corte con lápiz y escuadra. Repasa la línea con un cúter — esto corta las fibras superficiales y evita astillas en el lado visible.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Coloca la cara visible de la madera hacia arriba si usas serrucho (corta en el movimiento de empuje). Coloca la cara visible hacia abajo si usas caladora (corta en el movimiento de subida).</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Usa cinta de carrocero sobre la línea de corte para proteger el acabado — corta a través de la cinta y retírala después.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Apoya bien la pieza — la parte que va a caer debe estar soportada o el propio peso parte la madera antes del final del corte.</div></li>
      </ul>
    </div>
  </div>

  <!-- #072 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#072</span><span class="tip-title">Lijar correctamente para un acabado parejo</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Siempre lija en la <strong>dirección de la veta</strong> de la madera, nunca a contraveta o circular — las marcas quedan permanentes y el barniz las resalta.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Progresión de lijas: empieza gruesa (80 o 100), luego media (120 o 150), termina fina (180 o 220). No saltes grados — cada lija elimina las marcas de la anterior.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Usa un taco lijador o bloque — nunca la lija suelta en la mano. El taco aplica presión uniforme; la mano crea valles y montículos.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Entre capas de barniz o pintura, lija siempre con 220 para que la siguiente capa agarre bien.</div></li>
      </ul>
    </div>
  </div>

  <!-- #073 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#073</span><span class="tip-title">Instalar bisagras de puerta y ajustarlas</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Las bisagras de puertas interiores en México son mayormente de 3.5" o 4". Usa siempre 3 bisagras en puertas de más de 1.80 m de altura.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Marca la posición de la bisagra con lápiz. Hace un rebaje (encastre) con formón para que la bisagra quede al ras — si queda sobresalida, la puerta no cierra bien.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Para ajustar una puerta que roza: afloja los tornillos de la bisagra inferior y mueve el marco hacia afuera (para subir el lado inferior de la puerta) o hacia adentro (para bajar).</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Una puerta que no cierra o que se abre sola: verifica que el marco esté a plomo con el nivel. Casi siempre el problema es el marco, no la puerta.</div></li>
      </ul>
    </div>
  </div>

  <!-- #074 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#074</span><span class="tip-title">Reparar una puerta que no cierra o que roza</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Identifica dónde roza: pasa papel carbón o tiza en el canto de la puerta, ciérrala — la marca en el marco indica el punto exacto de contacto.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Si roza arriba:</strong> la bisagra inferior está suelta o tiene holgura. Ajusta o cambia los tornillos por tornillos más largos que lleguen a la madera sólida del marco.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Si roza en el canto lateral:</strong> cepilla o lija el canto en el punto de contacto. Cepilla en dirección de la veta con el cepillo bien afilado.</div></li>
        <li class="tip-step"><div class="ts">4</div><div><strong>Si infló por humedad:</strong> en México esto es muy común en temporada de lluvias. Lija el canto rozante, aplica sellador o pintura para impermeabilizar. La madera se contraerá de nuevo al secarse.</div></li>
      </ul>
    </div>
  </div>

  <!-- #075 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#075</span><span class="tip-title">Instalar una chapa o cerradura nueva</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Retira la chapa vieja: desatornilla las placas laterales, jala el pestillo y la manija. El mecanismo interno sale completo.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Lleva la chapa vieja a la ferretería para conseguir el reemplazo exacto — mismo ancho de espiga, misma distancia entre centro de perilla y borde.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Si cambias el tipo de chapa, puede que necesites ampliar o corregir la mortaja (el orificio en el canto de la puerta) con formón.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Verifica que el pestillo entre y salga limpio en el marco antes de atornillar todo. Lubrica con grafito en polvo o spray lubricante (no grasa — atrae polvo).</div></li>
      </ul>
    </div>
  </div>

  <!-- #076 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#076</span><span class="tip-title">Instalar repisas en la pared (flotantes)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Define la carga: una repisa de libros requiere soporte cada 40–50 cm. Una repisa decorativa aguanta con soportes en los extremos.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Marca una línea horizontal perfectamente nivelada con el nivel de burbuja. Los soportes deben quedar exactamente en esa línea.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>En concreto: taquetes #10 con tornillo de cabeza plana. En yeso con estructura metálica: usa anclas de mariposa o localiza los perfiles metálicos con un detector de montantes.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>La repisa debe sobresalir máximo 30 cm de la pared sin soporte central para cargas normales. Más de eso y necesitas un soporte intermedio.</div></li>
      </ul>
    </div>
  </div>

  <!-- #077 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#077</span><span class="tip-title">Ensamblar muebles de flatpack (tipo IKEA) correctamente</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Lee las instrucciones completas antes de empezar. Identifica y cuenta todas las piezas y herrajes — mucho mejor descubrir que falta algo antes que a la mitad del armado.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Arma sobre alfombra o cartón para no rayar las piezas. Nunca sobre piso de concreto.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Los conectores tipo excéntrico (cazo + tornillo): el tornillo va en la pieza A, el cazo en la pieza B. Encajan y giras el cazo 90° con un destornillador plano para bloquear. No fuerces — si no entra, el tornillo está demasiado adentro o afuera.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>El panel trasero de respaldo es lo que da rigidez al mueble. No lo omitas aunque parezca opcional — sin él el mueble se tuerce con el tiempo.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Al terminar, ancla el mueble alto a la pared con el kit de antivuelco incluido. En México los sismos hacen indispensable este paso para muebles de más de 1.50 m.</div></li>
      </ul>
    </div>
  </div>

  <!-- #078 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#078</span><span class="tip-title">Reparar un cajón que no corre bien</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Cajón que roza y atora:</strong> saca el cajón completamente. Busca el punto de roce (marca brillante). Lija ligeramente esa zona y aplica cera de vela o jabón seco en los laterales.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Cajón que se sale o cae:</strong> las guías metálicas tienen topes ajustables. Revisa si algún tope se movió o se perdió.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Guías dañadas:</strong> las guías telescópicas son económicas y fáciles de cambiar. Quita los tornillos de la guía vieja, instala la nueva en los mismos orificios. Verifica que ambas guías (derecha e izquierda) queden exactamente a la misma altura.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Si el fondo del cajón se pandea: refuerza con un listón de madera pegado y atornillado en el interior inferior del cajón.</div></li>
      </ul>
    </div>
  </div>

  <!-- #079 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#079</span><span class="tip-title">Reparar un mueble de melamina o MDF dañado</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>La melamina y el MDF son los materiales de muebles más comunes en México. Tienen reparaciones específicas.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Canto con chapa levantada:</strong> aplica pegamento blanco (PVA) bajo la chapa levantada con un palillo. Presiona con una prensa o cinta y deja 2 horas. Para cantos que siempre se levantan, usa pegamento de contacto.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Golpe en melamina (burbuja/descascarado):</strong> aplica pasta de relleno o masilla en el hueco, deja secar, lija al ras y aplica pintura del color más cercano. Para áreas grandes, usa lámina de melamina adhesiva del mismo color.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>MDF que se infló por agua:</strong> si la hinchazón es menor de 3 mm, puede lijarse al ras y sellarse con shellac antes de pintar. Si es mayor, la sección debe reemplazarse.</div></li>
      </ul>
    </div>
  </div>

  <!-- #080 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#080</span><span class="tip-title">Pintar madera — preparación y aplicación</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <div class="materiales">
        <span class="mat">Lija 120 y 220</span><span class="mat">Sellador o primer para madera</span><span class="mat">Pintura esmalte o vinílica</span><span class="mat">Brocha de cerdas suaves</span>
      </div>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Lija con 120 en dirección de la veta. Limpia el polvo con trapo húmedo y deja secar. La preparación es el 80% del resultado.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Aplica una capa de sellador o primer. Sella los poros de la madera y evita que la pintura final sea absorbida desigualmente. Deja secar 4 horas.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Lija ligeramente con 220 sobre el sellador seco. Limpia el polvo.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Aplica la primera capa de pintura en capas delgadas. Los últimos trazos deben ser en la dirección de la veta. Deja secar 4 horas, lija con 220, segunda capa.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Para puertas de fierro o madera exterior: usa esmalte alquídico (base aceite). Para muebles interiores: esmalte base agua es más fácil de aplicar y limpiar.</div></li>
      </ul>
    </div>
  </div>

  <!-- #081 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#081</span><span class="tip-title">Barnizar madera para acabado profesional</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Trabaja en lugar sin polvo y sin viento. El polvo que cae sobre el barniz fresco arruina el acabado.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Aplica el barniz con brocha de pelo suave en movimientos largos en la dirección de la veta. No regreses sobre zonas ya barnizadas — el barniz se aplica en una sola pasada.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Primera capa: ligeramente diluida (10% de thinner o agua según el tipo). Actúa como sellador. Lija con 220 cuando seque completamente (4–8 horas).</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Segunda y tercera capa: barniz sin diluir. Lija entre cada capa con 320 para acabado ultra liso.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Para acabado satinado: aplica una última capa con lija 400 en seco o 0000 lana de acero.</div></li>
      </ul>
    </div>
  </div>

  <!-- #082 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#082</span><span class="tip-title">Instalar piso laminado flotante</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>El piso flotante NO va pegado al suelo. "Flota" sobre una espuma base (underlayment). Esta es la instalación más sencilla para principiantes.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>El suelo debe estar limpio, seco y perfectamente plano. Diferencias de más de 3 mm en 1.8 metros hacen que el piso cruja o se deforme.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Deja 8 mm de espacio entre el piso y las paredes (espacio de expansión). Para eso usa cuñas de plástico mientras instalas. Las molduras de zoclo cubrirán ese espacio al final.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Los tablones encajan con sistema click. Coloca el siguiente tablón en ángulo de 45°, encaja el perfil y baja presionando hasta que haga clic. Un golpe suave con martillo y bloque de madera ayuda.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Instala las piezas de la última fila midiendo y cortando con caladora o sierra. Instala las molduras de zoclo sobre las paredes, nunca sobre el piso — así el piso puede expandirse libremente.</div></li>
      </ul>
    </div>
  </div>

  <!-- #083 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#083</span><span class="tip-title">Colocar azulejo o loseta pequeña en pared</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <div class="materiales">
        <span class="mat">Adhesivo cerámico (pegablock o similar)</span><span class="mat">Espátula dentada</span><span class="mat">Separadores de 2 mm</span><span class="mat">Crucetas</span><span class="mat">Nivel</span>
      </div>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Comienza desde el centro de la pared, no desde la esquina. Traza líneas guía verticales y horizontales perfectamente a plomo con nivel.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Aplica adhesivo en la pared (no en el azulejo) con la espátula dentada a 45°. El dentado crea surcos uniformes de adhesivo.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Presiona cada azulejo con movimiento de torsión suave y usa separadores (crucetas) para mantener juntas uniformes.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Deja secar 24 horas antes de aplicar el junteado (lechada). Aplica la lechada con la esponja diagonal a las juntas, limpia el exceso antes de que seque.</div></li>
      </ul>
    </div>
  </div>

  <!-- #084 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#084</span><span class="tip-title">Reparar una junta de azulejo (rejunteado)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Retira la junta vieja raspando con un destornillador plano o herramienta de quitar juntas. Profundidad mínima: 5 mm para que el junteado nuevo agarre bien.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Limpia con cepillo y aspira el polvo. La junta debe estar completamente limpia y seca.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Mezcla la lechada con agua hasta consistencia de pasta espesa. Aplica con espátula de hule diagonalmente a la junta para empujarla bien hacia adentro.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Retira el exceso con esponja húmeda (no mojada) en movimientos circulares. Deja secar 30 min y pule con paño seco.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Las juntas en esquinas interiores y en la unión pared-piso no van con lechada — van con silicón de baño. La lechada en esquinas se cuartea siempre.</div></li>
      </ul>
    </div>
  </div>

  <!-- #085 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#085</span><span class="tip-title">Hacer un tabique o muro de tablaroca</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>La tablaroca (drywall) es el material más rápido para hacer divisiones internas en México.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Instala los canales (perfiles en C) en piso y techo marcando la posición del muro con línea de tiza. Ancla con taquetes en concreto cada 60 cm.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Inserta los parantes (perfiles verticales en C, más angostos) dentro de los canales cada 40 cm. No atornilles en el canal — solo deben deslizarse para que el muro pueda moverse ligeramente sin cuartearse.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Corta la tablaroca con cúter: marca, corta por la línea, dobla y termina cortando el papel del otro lado. No necesitas sierra.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Atornilla la tablaroca al parante con tornillos para tablaroca cada 20 cm. La cabeza del tornillo debe quedar ligeramente hundida (1 mm) sin romper el papel.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Aplica pasta para tablaroca en las juntas con la espátula, coloca malla de fibra, otra capa de pasta. Lija con 120 y otra capa fina. Lija con 220 para acabado.</div></li>
      </ul>
    </div>
  </div>

  <!-- #086 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#086</span><span class="tip-title">Rellenar y reparar grietas en muros</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Grietas en aplanado (yeso o cemento):</strong> abre ligeramente la grieta con espátula o destornillador en forma de V — esto da más superficie de agarre al relleno.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Humedece la grieta con agua antes de rellenar — el yeso o mortero seco absorbe el agua del relleno y no endurece bien.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Rellena con pasta para reparar muros o mezcla de yeso + agua. Empuja bien dentro de la grieta con espátula, alisa al ras. Deja secar 24 horas.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Lija con 120 para nivelar, otra capa delgada si es necesario. Lija final con 220. Pinta sobre la reparación.</div></li>
        <li class="tip-step"><div class="ts">5</div><div><strong>Grietas que regresan:</strong> son grietas estructurales — requieren revisión de un ingeniero antes de tapar cosméticamente.</div></li>
      </ul>
    </div>
  </div>

  <!-- #087 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#087</span><span class="tip-title">Instalar cornisa o moldura decorativa en techo</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Las cornisas de poliuretano o unicel son las más fáciles para principiantes — se pegan, son ligeras y se cortan con serrucho.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Las esquinas requieren corte a 45°. Usa una caja ingleteadora para guiar el serrucho al ángulo exacto. La esquina interior se corta al revés de la exterior.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Aplica pegamento de construcción (tipo Resistol 850 o similar) en la cara trasera de la cornisa. Pega en posición y sujeta con cinta de carrocero mientras seca (20 min).</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Rellena la unión entre cornisas y entre la cornisa y la pared/techo con pasta para muros. Lija y pinta del mismo color que el techo.</div></li>
      </ul>
    </div>
  </div>

  <!-- #088 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#088</span><span class="tip-title">Instalar zoclos de madera o MDF</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Corta los zoclos a la longitud de cada tramo. Para las esquinas interiores: inglete a 45° en dirección opuesta. Para esquinas exteriores: inglete a 45° hacia afuera.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Fija a la pared con pistola clavadora o clavos de acabado (#4 o #6). Introduce los clavos en ángulo hacia la pared para que no se vean tanto.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Rellena los huecos de los clavos con pasta de madera del color más cercano. Lija cuando seque.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>La junta entre el zoclo y el piso se sella con silicón del color del zoclo — no queda fijo al piso, permite que el piso laminado se expanda libremente.</div></li>
      </ul>
    </div>
  </div>

  <!-- #089 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#089</span><span class="tip-title">Clavar sin partir la madera</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Haz un orificio piloto con broca de diámetro ligeramente menor al clavo o tornillo. Esto es especialmente importante en madera seca, MDF y en los extremos de la pieza.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Otra técnica: voltea el clavo y golpea ligeramente la punta con el martillo — aplana la punta y al clavarla corta las fibras en lugar de separarlas.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>En tornillos para madera: aplica un poco de cera de vela en la rosca. Entra mucho más fácil y no parte la madera.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Nunca claves a menos de 3 cm del extremo de una tabla sin orificio piloto — la madera siempre parte ahí.</div></li>
      </ul>
    </div>
  </div>

  <!-- #090 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#090</span><span class="tip-title">Pegar madera con resistencia: cola blanca PVA</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>La cola blanca (PVA) bien usada es más fuerte que la madera misma. La clave está en la preparación de la superficie y la presión de encolado.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Aplica una capa delgada y uniforme en <strong>ambas</strong> superficies. No en una sola — la junta necesita cola en los dos lados.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Une las piezas y aplica presión con prensas durante mínimo 1 hora. El exceso de cola que exprime es señal de presión correcta — límpialo con trapo húmedo antes de que seque.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>No pegues sobre superficies barnizadas o pintadas — lija siempre hasta llegar a madera limpia para que la cola agarre.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>La cola PVA no es resistente al agua — para exteriores usa cola para madera exterior (tipo Titebond III o equivalente).</div></li>
      </ul>
    </div>
  </div>

  <!-- #091 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#091</span><span class="tip-title">Instalar muebles de cocina (gabinetes altos)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Marca la línea inferior de los gabinetes altos con nivel — generalmente a 54 cm de la cubierta o a 195 cm del piso. Esta línea es la referencia para toda la instalación.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Instala primero las esquinas y los gabinetes de los extremos, luego los intermedios. Verifica que queden a plomo y nivelados antes de atornillar definitivamente.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Los taquetes en concreto deben ser #10 con tornillo de 3" mínimo. Cada gabinete necesita mínimo 4 puntos de anclaje a la pared.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Une los gabinetes entre sí con tornillos de unión antes de fijar a la pared — forman un bloque más resistente que cajones independientes.</div></li>
      </ul>
    </div>
  </div>

  <!-- #092 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#092</span><span class="tip-title">Ajustar bisagras de cocina (bisagra europea)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>La bisagra europea (la que tiene un botón redondo y se ajusta con tornillo) permite 3 tipos de ajuste sin herramientas especiales.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>Ajuste lateral (puerta muy cerca o lejos del marco):</strong> gira el tornillo central de la bisagra. A la derecha = puerta se aleja del centro. A la izquierda = puerta se acerca.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Ajuste de profundidad (puerta muy adentro o afuera del cajón):</strong> afloja los tornillos del soporte y desliza hacia adelante o atrás. Vuelve a apretar.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Ajuste vertical (puerta alta o baja):</strong> afloja el tornillo de montaje del soporte en el cajón y desliza arriba o abajo.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Haz todos los ajustes con la puerta cerrada para ver el resultado de inmediato. Ajusta de a pequeños incrementos.</div></li>
      </ul>
    </div>
  </div>

  <!-- #093 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#093</span><span class="tip-title">Hacer un orificio perfecto con taladro</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Marca el punto exacto con lápiz. Haz un pequeño punto con punzón o clavo + martillo — el punto guía la broca y evita que resbale al iniciar.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Para madera: broca de punta de pájaro (helicoidal normal). Para concreto: broca de widia (punta triangular metálica). Para metal: broca HSS (alta velocidad, plateada).</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Para hacer orificios limpios en madera sin astillas en la salida: pega cinta de carrocero en la cara de salida o coloca un trozo de madera de sacrificio detrás.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Velocidad: madera = alta velocidad. Metal = velocidad media + aceite de corte. Concreto = percutor + velocidad media.</div></li>
      </ul>
    </div>
  </div>

  <!-- #094 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#094</span><span class="tip-title">Impermeabilizar una azotea (membrana o pintura)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>La gotera es el problema más común en casas mexicanas. La impermeabilización correcta dura 5–10 años.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Limpia la azotea completamente — barrer, retirar polvo, plantas y suciedad. La impermeabilización sobre superficie sucia dura la mitad.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Repara grietas con sellador elástico o mezcla de cemento. Espera 24 horas antes de impermeabilizar.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Pintura acrílica impermeabilizante:</strong> aplica en temporada seca (mínimo 3 días sin lluvia). 2 capas en sentidos cruzados. Refuerza bordes, uniones y esquinas con tela de fibra de vidrio embebida en la primera capa.</div></li>
        <li class="tip-step"><div class="ts">4</div><div><strong>Membrana de polietileno:</strong> más duradera. Extiende la membrana, traslapa 10 cm en uniones y sella los bordes con sellador de poliuretano.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Verifica la pendiente — el agua debe escurrir hacia los bajantes. Una azotea plana siempre acumula agua y falla antes. Con arena mojada crea pendiente hacia los drenes antes de impermeabilizar.</div></li>
      </ul>
    </div>
  </div>

  <!-- #095 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#095</span><span class="tip-title">Pintar paredes interiores sin manchas ni marcas</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <div class="materiales">
        <span class="mat">Rodillo de pelo corto (9mm)</span><span class="mat">Brocha de 2"</span><span class="mat">Cinta de carrocero</span><span class="mat">Cubeta con rejilla</span>
      </div>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Pega cinta de carrocero en los bordes: junto al techo, rodapiés, marcos y contactos. La línea perfecta se hace con la cinta, no con el pulso.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Primero pinta los bordes y esquinas con brocha ("recortar"). Luego rellena con rodillo. Siempre en ese orden.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>No cargues demasiada pintura en el rodillo — escúrrela en la rejilla de la cubeta. El exceso hace salpicaduras y escurrimientos.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Aplica en movimiento de W o M sobre la pared para distribuir, luego pasa una sola vez vertical de arriba a abajo para nivelar. Nunca regreses sobre zonas casi secas.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Retira la cinta de carrocero mientras la pintura está aún ligeramente húmeda (30–60 min). Si esperas a que seque del todo, la cinta jala la pintura.</div></li>
      </ul>
    </div>
  </div>

  <!-- #096 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#096</span><span class="tip-title">Construir una mesa o banco sencillo</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>El primer proyecto de carpintería ideal: cuatro patas y un tablero. Sin herramientas especiales.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Diseño más sencillo: 4 patas de 2"x2" y un tablero de triplex 18 mm. Patas unidas al tablero con tacos de madera (corner blocks) y tornillos.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Corta las 4 patas exactamente a la misma longitud. Mide y corta todas juntas para que queden idénticas.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Ensambla primero los dos pares de patas con un larguero entre ellas. Luego une los dos marcos con los largueros del frente y fondo. Finalmente fija el tablero.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Verifica que no cabecea: colócalo en el piso y ve si tambalea. Si lo hace, lija ligeramente la pata más larga.</div></li>
      </ul>
    </div>
  </div>

  <!-- #097 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#097</span><span class="tip-title">Proteger madera exterior del sol y la lluvia</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>La madera exterior sin protección en México dura 1–2 años antes de cuartearse y pudrir. En zonas costeras como Acapulco, incluso menos por la humedad salina.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Prepara la madera: lija con 80 si hay pintura o barniz viejo. Limpia con trapo húmedo y seca 24 horas.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>Aceite de linaza:</strong> penetra la madera y la protege desde adentro. Aplica con trapo, deja absorber 2 horas, retira el exceso. Repite 2 veces al año.</div></li>
        <li class="tip-step"><div class="ts">4</div><div><strong>Barniz marino:</strong> la protección más duradera para exteriores. Aplica 3 capas lijando entre cada una. Dura 2–3 años antes de necesitar mantenimiento.</div></li>
        <li class="tip-step"><div class="ts">5</div><div>Protege siempre los cantos y la parte inferior de las piezas — por donde más entra la humedad.</div></li>
      </ul>
    </div>
  </div>

  <!-- #098 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#098</span><span class="tip-title">Instalar una puerta corredera (tipo granero)</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>El riel superior debe anclarse en una viga o elemento estructural — no solo en drywall o aplanado. Si no hay viga, instala un cabezal de madera sólida anclado a la estructura.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>El riel debe estar perfectamente nivelado — una desviación de 3 mm por metro hace que la puerta se mueva sola hacia un lado.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Instala los carritos (rodamientos) en la puerta antes de colgarla. La mayoría tiene ajuste de altura que permite nivelar la puerta después de instalar.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Instala una guía en el piso — solo un tornillo con tope de plástico o una pequeña escuadra que evita que la puerta se salga de su plano.</div></li>
      </ul>
    </div>
  </div>

  <!-- #099 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#099</span><span class="tip-title">Usar pegamento de contacto correctamente</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>El Resistol amarillo (neopreno) es el pegamento más usado en carpintería mexicana, pero muchos lo usan mal.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div>Aplica en <strong>ambas</strong> superficies. Extiende una capa pareja con espátula o palo — ni muy gruesa ni muy delgada.</div></li>
        <li class="tip-step"><div class="ts">2</div><div>Espera a que el pegamento esté <strong>seco al tacto</strong> pero aún pegajoso (generalmente 5–15 minutos según el clima). El error más común es unir inmediatamente — el pegamento de contacto actúa de contacto, no de relleno.</div></li>
        <li class="tip-step"><div class="ts">3</div><div>Una vez que pegas las superficies, <strong>no hay corrección posible</strong>. Alinea perfectamente antes de tocar. Si necesitas reposicionar, pon papel encerado entre las piezas mientras las alineas y retíralo al final.</div></li>
        <li class="tip-step"><div class="ts">4</div><div>Golpea con martillo de hule uniformemente para asegurar el contacto completo. La presión activa la unión.</div></li>
      </ul>
    </div>
  </div>

  <!-- #100 -->
  <div class="tip-card" data-cat="c" onclick="toggle(this)">
    <div class="tip-header"><span class="tip-n">#100</span><span class="tip-title">Los 10 errores más comunes del bricolajero principiante</span><span class="tip-arrow">›</span></div>
    <div class="tip-body">
      <p>El conocimiento más valioso: qué <em>no</em> hacer.</p>
      <ul class="tip-steps">
        <li class="tip-step"><div class="ts">1</div><div><strong>No medir dos veces antes de cortar.</strong> "Mide dos veces, corta una vez" es la regla #1 del carpintero. La madera cortada de más no tiene vuelta atrás.</div></li>
        <li class="tip-step"><div class="ts">2</div><div><strong>Trabajar con electricidad sin verificar con el detector.</strong> Un apagador puede venir de un breaker diferente al que apagaste.</div></li>
        <li class="tip-step"><div class="ts">3</div><div><strong>No usar taquete en el diámetro correcto.</strong> Los taquetes se caen por este error, no por el peso.</div></li>
        <li class="tip-step"><div class="ts">4</div><div><strong>Poner teflón al revés.</strong> Si va al sentido contrario de la rosca, la rosca lo desenrolla al armar y no sella.</div></li>
        <li class="tip-step"><div class="ts">5</div><div><strong>Sobre-apretar.</strong> El sobre-apriete rompe taquetes en la pared, aplana tuercas de plástico, parte perfiles de cobre y deforma roscas.</div></li>
        <li class="tip-step"><div class="ts">6</div><div><strong>No fotografiar antes de desmontar.</strong> La foto tarda 2 segundos; recordar cómo estaba conectado puede tardar horas.</div></li>
        <li class="tip-step"><div class="ts">7</div><div><strong>Usar la herramienta equivocada para ahorrar tiempo.</strong> Un desarmador como cincel, unas pinzas como llave, un cúter como sierra. Resulta más lento, más peligroso y con peor resultado.</div></li>
        <li class="tip-step"><div class="ts">8</div><div><strong>No preparar la superficie antes de pintar/barnizar.</strong> La preparación es 80% del resultado. La pintura más cara sobre superficie mal preparada se ve horrible.</div></li>
        <li class="tip-step"><div class="ts">9</div><div><strong>Mezclar materiales incompatibles.</strong> Pegamento PVC blanco en tubería CPVC amarilla. Silicón de baño en lugar de lechada para azulejo. Cada material tiene su producto específico.</div></li>
        <li class="tip-step"><div class="ts">10</div><div><strong>Apresurarse.</strong> Los tiempos de secado, curado y fraguado existen por razones físicas — no son sugerencias. El trabajo que se apresura se repite.</div></li>
      </ul>
    </div>
  </div>

</div><!-- /carpinteria -->

</div><!-- /main -->

<script>
function toggle(card){
  const isOpen = card.classList.contains('open');
  document.querySelectorAll('.tip-card.open').forEach(c => c.classList.remove('open'));
  if(!isOpen){
    card.classList.add('open');
    setTimeout(() => card.scrollIntoView({behavior:'smooth', block:'nearest'}), 40);
  }
}

function filtrar(cat, btn){
  document.querySelectorAll('.filter-btn').forEach(b => {
    b.classList.remove('active-all','active-p','active-e','active-c');
  });
  const cls = cat === 'all' ? 'active-all' : cat === 'p' ? 'active-p' : cat === 'e' ? 'active-e' : 'active-c';
  btn.classList.add(cls);

  document.querySelectorAll('.cat-section').forEach(s => {
    s.style.display = (cat === 'all' || s.dataset.sec === cat) ? '' : 'none';
  });
  document.querySelectorAll('.tip-card').forEach(c => {
    c.style.display = (cat === 'all' || c.dataset.cat === cat) ? '' : 'none';
    c.classList.remove('open');
  });
}
</script>
</body>
</html>
