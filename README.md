<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
<meta name="theme-color" content="#0f1226">
<title>Олимпиады на БВИ — мобильный гид</title>
<style>
  :root{
    --bg:#0f1226;--card:#171a32;--card2:#1d2142;--line:#2a2f55;--txt:#e7e9f5;--muted:#a4a9c9;
    --l1:#16c784;--l2:#f6c945;--l3:#ff7a59;--accent:#8b5cf6;--blue:#7c9cff;
    --bvi:#10331f;--bviT:#5ee6a8;--h100:#3a2f10;--h100T:#f6d870;--noT:#6b7099;
  }
  *{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
  html,body{margin:0;padding:0}
  body{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Arial,sans-serif;
    background:linear-gradient(170deg,#0f1226,#141833 55%,#1a1140);color:var(--txt);
    font-size:16px;line-height:1.5;padding-bottom:84px;-webkit-text-size-adjust:100%}
  .top{padding:18px 16px 12px;position:sticky;top:0;z-index:50;
    background:rgba(15,18,38,.92);backdrop-filter:blur(10px);border-bottom:1px solid var(--line)}
  h1{font-size:19px;margin:0 0 3px;font-weight:800;letter-spacing:-.3px}
  .sub{color:var(--muted);font-size:12.5px;margin:0}
  .wrap{padding:14px 14px 30px;max-width:560px;margin:0 auto}
  h2{font-size:17px;margin:22px 0 4px;font-weight:800;display:flex;align-items:center;gap:8px}
  .h2sub{color:var(--muted);font-size:12.5px;margin:0 0 12px}
  /* ====== ВКЛАДКИ СНИЗУ ====== */
  .tabbar{position:fixed;left:0;right:0;bottom:0;z-index:60;display:flex;
    background:rgba(20,24,52,.97);backdrop-filter:blur(12px);border-top:1px solid var(--line)}
  .tabbar button{flex:1;background:none;border:none;color:var(--muted);
    padding:9px 2px 10px;font-size:10.5px;font-weight:600;cursor:pointer;display:flex;
    flex-direction:column;align-items:center;gap:3px;transition:color .15s}
  .tabbar button .ic{font-size:19px}
  .tabbar button.on{color:#fff}
  .tabbar button.on .ic{transform:scale(1.12)}
  .view{display:none}
  .view.on{display:block;animation:f .25s ease}
  @keyframes f{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:none}}
  /* ====== ФИЛЬТР ПРЕДМЕТА ====== */
  .seg{display:flex;gap:6px;margin:0 0 14px;position:sticky;top:64px;z-index:40;
    background:rgba(15,18,38,.0);padding:2px 0}
  .seg button{flex:1;background:var(--card);border:1px solid var(--line);color:var(--muted);
    padding:9px 4px;border-radius:11px;font-size:13px;font-weight:700;cursor:pointer}
  .seg button.on{background:var(--accent);border-color:var(--accent);color:#fff}
  /* ====== КАРТОЧКА ОЛИМПИАДЫ ====== */
  .olymp{background:var(--card);border:1px solid var(--line);border-radius:16px;
    padding:13px 14px;margin-bottom:11px}
  .olymp .row1{display:flex;justify-content:space-between;align-items:flex-start;gap:8px}
  .olymp .nm{font-weight:700;font-size:15.5px;color:#fff;line-height:1.3}
  .lvlbadge{flex-shrink:0;font-weight:800;font-size:12px;padding:3px 9px;border-radius:8px}
  .lv1{background:rgba(22,199,132,.16);color:var(--l1)}
  .lv2{background:rgba(246,201,69,.16);color:var(--l2)}
  .lv3{background:rgba(255,122,89,.16);color:var(--l3)}
  .lvV{background:rgba(124,156,255,.16);color:var(--blue)}
  .meta{display:flex;align-items:center;gap:10px;margin:7px 0 11px;flex-wrap:wrap}
  .stars{color:var(--l2);font-size:13px;letter-spacing:1px}
  .tag10{font-size:10.5px;font-weight:700;background:var(--accent);color:#fff;padding:2px 8px;border-radius:7px}
  /* сетка вузов */
  .unis{display:grid;grid-template-columns:repeat(5,1fr);gap:5px}
  .uni{text-align:center;border-radius:9px;padding:7px 2px 6px;background:#12152b;border:1px solid var(--line)}
  .uni .u{font-size:10px;color:var(--muted);font-weight:700;margin-bottom:3px;display:block;letter-spacing:.2px}
  .uni .v{font-size:11px;font-weight:800;border-radius:6px;padding:3px 0;display:block}
  .v.bvi{background:var(--bvi);color:var(--bviT)}
  .v.h100{background:var(--h100);color:var(--h100T)}
  .v.no{background:#222644;color:var(--noT)}
  /* ====== БЛОКИ-ЗАМЕТКИ ====== */
  .note{background:var(--card);border:1px solid var(--line);border-left:4px solid var(--l2);
    border-radius:12px;padding:12px 14px;margin:12px 0;font-size:14px}
  .note.warn{border-left-color:var(--l3)} .note.ok{border-left-color:var(--l1)}
  .note b{color:#fff}
  .note ul{margin:7px 0 2px;padding-left:18px} .note li{margin:5px 0}
  /* легенда */
  .legend{display:flex;flex-wrap:wrap;gap:6px;margin:0 0 14px}
  .lg{font-size:11.5px;padding:5px 10px;border-radius:20px;background:var(--card);border:1px solid var(--line);
    display:inline-flex;align-items:center;gap:6px}
  .dot{width:9px;height:9px;border-radius:50%}
  .d1{background:var(--l1)}.d2{background:var(--l2)}.d3{background:var(--l3)}.dv{background:var(--blue)}
  /* ====== АККОРДЕОН (вузы / календарь) ====== */
  details{background:var(--card);border:1px solid var(--line);border-radius:14px;margin-bottom:10px;overflow:hidden}
  summary{padding:14px 16px;font-weight:700;font-size:15.5px;cursor:pointer;list-style:none;
    display:flex;justify-content:space-between;align-items:center;color:#fff}
  summary::-webkit-details-marker{display:none}
  summary .chev{transition:transform .2s;color:var(--muted);font-size:13px}
  details[open] summary .chev{transform:rotate(180deg)}
  .acc-body{padding:2px 16px 15px;font-size:14px}
  .acc-body b{color:#fff}
  .acc-body p{margin:9px 0}
  .acc-body .lab{font-size:12px;color:var(--accent);font-weight:800;text-transform:uppercase;letter-spacing:.5px;margin-top:11px}
  /* топ-нумерация */
  .topitem{display:flex;gap:11px;align-items:flex-start;background:var(--card);border:1px solid var(--line);
    border-radius:14px;padding:12px 13px;margin-bottom:9px}
  .topitem .n{flex-shrink:0;width:28px;height:28px;border-radius:9px;background:var(--accent);color:#fff;
    font-weight:800;display:flex;align-items:center;justify-content:center;font-size:14px}
  .topitem .nm{font-weight:700;color:#fff;font-size:15px}
  .topitem .desc{color:var(--muted);font-size:12.5px;margin-top:3px}
  .topitem .pj{margin-top:5px;display:flex;gap:5px;flex-wrap:wrap}
  .pj span{font-size:10px;padding:2px 7px;border-radius:12px}
  .pm{background:rgba(124,156,255,.16);color:var(--blue)}
  .pf{background:rgba(255,122,89,.16);color:var(--l3)}
  .pin{background:rgba(22,199,132,.16);color:var(--l1)}
  /* календарь */
  .cal{background:var(--card);border:1px solid var(--line);border-radius:14px;padding:12px 14px;margin-bottom:11px}
  .cal h3{margin:0 0 9px;font-size:15px;display:flex;align-items:center;gap:7px}
  .calrow{display:flex;justify-content:space-between;gap:10px;padding:8px 0;border-bottom:1px solid var(--line)}
  .calrow:last-child{border-bottom:none}
  .calrow .l{font-weight:600;font-size:14px}
  .calrow .l small{display:block;color:var(--muted);font-size:11px;font-weight:500;margin-top:2px}
  .calrow .r{text-align:right;flex-shrink:0}
  .calrow .r .d{color:var(--bviT);font-weight:700;font-size:13px;white-space:nowrap}
  .calrow .r small{display:block;color:var(--muted);font-size:11px;margin-top:2px}
  .foot{color:var(--muted);font-size:11px;margin-top:18px;border-top:1px solid var(--line);padding-top:12px}
  a{color:var(--blue)}
</style>
</head>
<body>

<div class="top">
  <h1>🎓 Олимпиады на БВИ</h1>
  <p class="sub">МГУ · МФТИ · Бауман · ВШЭ · ИТМО · 10 класс</p>
</div>

<div class="wrap">

  <!-- ============ VIEW: ТАБЛИЦЫ ============ -->
  <div class="view on" id="v-table">
    <div class="legend">
      <span class="lg"><span class="dot d1"></span>I ур.</span>
      <span class="lg"><span class="dot d2"></span>II ур.</span>
      <span class="lg"><span class="dot d3"></span>III ур.</span>
      <span class="lg"><span class="dot dv"></span>ВсОШ</span>
      <span class="lg">★ сложность</span>
    </div>

    <div class="note warn">
      <b>⚠️ Про 10 класс.</b> Для БВИ в МГУ/МФТИ/Баумане нужен диплом <b>за 11 класс</b>. Диплом за 10 класс действует 4 года (копилка), но «боевым» его принимают только <b>«Физтех» (МФТИ)</b> и <b>ВШЭ</b> (за 10 и 11 кл). Значок <span class="tag10">10 кл</span> = годен за 10 класс.
    </div>

    <div class="seg" id="seg">
      <button class="on" data-s="math">📐 Матем.</button>
      <button data-s="phys">⚛️ Физика</button>
      <button data-s="inf">💻 Информ.</button>
    </div>

    <div id="cards"></div>

    <div class="note">
      <b>Обозначения:</b> <span style="color:var(--bviT)">БВИ</span> — без экзаменов · <span style="color:var(--h100T)">100</span> — 100 баллов ЕГЭ · <span style="color:var(--noT)">—</span> — нет льготы. «БВИ*» в МФТИ — только победителям, отдельные группы.
    </div>
  </div>

  <!-- ============ VIEW: ТОПЫ ============ -->
  <div class="view" id="v-top">
    <h2>🏆 ТОП-универсал</h2>
    <p class="h2sub">Дают БВИ во всех 5 вузах сразу — выбор, если вуз не определён.</p>

    <div class="topitem"><div class="n">1</div><div><div class="nm">ВсОШ (финал)</div><div class="desc">Безусловный БВИ везде, без подтверждения профильным ЕГЭ. Максимум.</div><div class="pj"><span class="pm">мат</span><span class="pf">физ</span><span class="pin">инф</span></div></div></div>
    <div class="topitem"><div class="n">2</div><div><div class="nm">Московская олимп. (МОШ)</div><div class="desc">I уровень по всем трём предметам, признаётся всеми.</div><div class="pj"><span class="pm">мат</span><span class="pf">физ</span><span class="pin">инф</span></div></div></div>
    <div class="topitem"><div class="n">3</div><div><div class="nm">Высшая проба (ВШЭ)</div><div class="desc">I ур. (мат/инф). Засчитывает диплом за 10 класс. Доступнее.</div><div class="pj"><span class="pm">мат</span><span class="pf">физ</span><span class="pin">инф</span></div></div></div>
    <div class="topitem"><div class="n">4</div><div><div class="nm">Ломоносов (МГУ)</div><div class="desc">I ур., БВИ везде, удобный онлайн-отбор.</div><div class="pj"><span class="pm">мат</span><span class="pf">физ</span></div></div></div>
    <div class="topitem"><div class="n">5</div><div><div class="nm">Покори Воробьёвы горы!</div><div class="desc">I ур., «парная» к Ломоносову.</div><div class="pj"><span class="pm">мат</span><span class="pf">физ</span></div></div></div>
    <div class="topitem"><div class="n">6</div><div><div class="nm">Физтех (МФТИ)</div><div class="desc">Физика — I ур. (БВИ везде). Диплом за 10 класс годен для МФТИ.</div><div class="pj"><span class="pm">мат</span><span class="pf">физ</span><span class="pin">инф</span></div></div></div>
    <div class="topitem"><div class="n">7</div><div><div class="nm">Росатом (физ-мат)</div><div class="desc">Физика — I ур., БВИ везде. Много очных площадок.</div><div class="pj"><span class="pm">мат</span><span class="pf">физ</span></div></div></div>
    <div class="topitem"><div class="n">8</div><div><div class="nm">Открытая по программир.</div><div class="desc">I ур., БВИ везде. Топ для информатиков.</div><div class="pj"><span class="pin">инф</span></div></div></div>

    <h2>🎓 Топ под каждый вуз</h2>
    <p class="h2sub">Нажмите на вуз, чтобы раскрыть приоритеты по предметам.</p>

    <details>
      <summary>🟣 МФТИ (Физтех) <span class="chev">▾</span></summary>
      <div class="acc-body">
        <div class="lab">Математика</div><p>Физтех [10] → ОММО/МОШ/Турнир городов/СПб (БВИ* на ФПМИ) → Ломоносов, ПВГ, Высшая проба.</p>
        <div class="lab">Физика</div><p>Физтех [10] + Росатом → Ломоносов, ПВГ, МОШ, Инженерная (I ур.).</p>
        <div class="lab">Информатика</div><p>Физтех [10] → Открытая по прогр., МОШ, Высшая проба, ТехноКубок → Innopolis, СПбГУ (БВИ*).</p>
        <div class="note warn" style="margin:10px 0 0">2026: БВИ <b>только победителям</b>; ЕГЭ-порог <b>80 б.</b>; списки на ПМИ сокращены.</div>
      </div>
    </details>

    <details>
      <summary>🔵 МГУ им. Ломоносова <span class="chev">▾</span></summary>
      <div class="acc-body">
        <div class="lab">Математика</div><p>Ломоносов, ПВГ → МОШ/ММО, Турнир городов, СПб, Высшая проба, СПбГУ (I ур., БВИ) → Физтех, ОММО, Курчатов (100 б.).</p>
        <div class="lab">Физика</div><p>Ломоносов, ПВГ, Физтех, Росатом, МОШ, Инженерная (I ур., БВИ) → Высшая проба, СПбГУ (100 б.).</p>
        <div class="lab">Информатика</div><p>МОШ, Высшая проба, Открытая по прогр., ТехноКубок (I ур., БВИ).</p>
      </div>
    </details>

    <details>
      <summary>🟠 МГТУ им. Баумана <span class="chev">▾</span></summary>
      <div class="acc-body">
        <div class="note ok" style="margin:6px 0 8px">Самый лояльный: БВИ за I и II уровни.</div>
        <div class="lab">Математика</div><p>Любая I ур. → Физтех, ОММО, Курчатов, Всесибирская, Росатом (II ур.) → Шаг в будущее (своя).</p>
        <div class="lab">Физика</div><p>Физтех, Росатом, Ломоносов, ПВГ, МОШ, Инженерная (I) → Высшая проба, СПбГУ, Курчатов, Шаг в будущее (II).</p>
        <div class="lab">Информатика</div><p>МОШ, Высшая проба, Открытая по прогр., ТехноКубок (I) → Физтех, Innopolis, Всесибирская, СПбГУ (II).</p>
      </div>
    </details>

    <details>
      <summary>🟢 НИУ ВШЭ <span class="chev">▾</span></summary>
      <div class="acc-body">
        <div class="note ok" style="margin:6px 0 8px">Засчитывает дипломы за <b>10 и 11 класс</b> — лучший для раннего старта.</div>
        <div class="lab">Математика</div><p>Высшая проба [10] (приоритет) → Ломоносов, ПВГ, МОШ, Турнир городов, СПбГУ (I ур.).</p>
        <div class="lab">Физика</div><p>Высшая проба [10] → Физтех, Росатом, Ломоносов, ПВГ, МОШ, Инженерная (I ур.).</p>
        <div class="lab">Информатика</div><p>Высшая проба [10] → МОШ, Открытая по прогр., ТехноКубок (I ур.).</p>
      </div>
    </details>

    <details>
      <summary>🟡 ИТМО <span class="chev">▾</span></summary>
      <div class="acc-body">
        <div class="note ok" style="margin:6px 0 8px">Сильнейший по информатике/программированию.</div>
        <div class="lab">Информатика</div><p>Олимп. ИТМО + Открытая по прогр., МОШ, Высшая проба, ТехноКубок (I) → Innopolis (II) → Открытая олимп. ИТМО (III).</p>
        <div class="lab">Математика</div><p>Все I ур. → Открытая олимп. ИТМО (своя, III ур.).</p>
        <div class="lab">Физика</div><p>Физтех, Росатом, Ломоносов, ПВГ, МОШ, Инженерная (I ур.).</p>
      </div>
    </details>
  </div>

  <!-- ============ VIEW: КАЛЕНДАРЬ ============ -->
  <div class="view" id="v-cal">
    <h2>📅 Календарь регистраций</h2>
    <p class="h2sub">Годовой цикл (по сезону 2025/26). Сверяйтесь с сайтом олимпиады!</p>

    <div class="note warn">
      <b>Поставьте напоминание на 1 сентября</b> и зарегистрируйтесь сразу на все нужные олимпиады — почти все регистрации закрываются к концу октября.
    </div>

    <div class="cal">
      <h3>🍂 Сентябрь — старт регистраций</h3>
      <div class="calrow"><div class="l">Высшая проба (ВШЭ)<small>мат·физ·инф · I ур.</small></div><div class="r"><span class="d">с 20 авг</span><small>до 20 окт</small></div></div>
      <div class="calrow"><div class="l">Физтех (МФТИ)<small>мат·физ·инф · I/II ур.</small></div><div class="r"><span class="d">~9 сент</span><small>до туров (окт)</small></div></div>
      <div class="calrow"><div class="l">Росатом<small>мат·физ · I/II ур.</small></div><div class="r"><span class="d">сентябрь</span><small>до очного тура</small></div></div>
      <div class="calrow"><div class="l">Московская олимп. (МОШ)<small>мат·физ·инф · I ур.</small></div><div class="r"><span class="d">сентябрь</span><small>до отбора</small></div></div>
    </div>

    <div class="cal">
      <h3>🍁 Окт–Ноя — пик регистраций</h3>
      <div class="calrow"><div class="l">Ломоносов (МГУ)<small>мат·физ · I ур.</small></div><div class="r"><span class="d">окт–нояб</span><small>отбор: нояб–дек</small></div></div>
      <div class="calrow"><div class="l">Покори Воробьёвы горы!<small>мат·физ · I ур.</small></div><div class="r"><span class="d">окт–нояб</span><small>отбор: нояб–дек</small></div></div>
      <div class="calrow"><div class="l">Открытая по программир.<small>инф · I ур.</small></div><div class="r"><span class="d">окт–нояб</span><small>отбор: нояб–дек</small></div></div>
      <div class="calrow"><div class="l">Олимп. ИТМО<small>инф·мат · I/III ур.</small></div><div class="r"><span class="d">окт–нояб</span><small>отбор: нояб–дек</small></div></div>
      <div class="calrow"><div class="l">ТехноКубок<small>инф · I ур.</small></div><div class="r"><span class="d">окт–дек</span><small>отбор: нояб–янв</small></div></div>
      <div class="calrow"><div class="l">Турнир городов<small>мат · I ур.</small></div><div class="r"><span class="d">в школе</span><small>тур: октябрь</small></div></div>
      <div class="calrow"><div class="l">Курчатов<small>мат·физ · II ур.</small></div><div class="r"><span class="d">окт–нояб</span><small>отбор: ноябрь</small></div></div>
      <div class="calrow"><div class="l">Всесибирская открытая<small>мат·физ·инф · II ур.</small></div><div class="r"><span class="d">окт–нояб</span><small>отбор: ноябрь</small></div></div>
      <div class="calrow"><div class="l">ОММО<small>мат · II ур.</small></div><div class="r"><span class="d">нояб–дек</span><small>финал: кон. дек</small></div></div>
      <div class="calrow"><div class="l">Innopolis Open<small>инф·мат · II ур.</small></div><div class="r"><span class="d">окт–нояб</span><small>отбор: нояб–дек</small></div></div>
      <div class="calrow"><div class="l">Инженерная олимпиада<small>физ · I ур.</small></div><div class="r"><span class="d">окт–нояб</span><small>отбор: нояб–дек</small></div></div>
      <div class="calrow"><div class="l">Шаг в будущее (Бауман)<small>мат·физ · II/III ур.</small></div><div class="r"><span class="d">окт–дек</span><small>отбор: дек–янв</small></div></div>
    </div>

    <div class="cal">
      <h3>❄️ Дек–Апр — финалы (очно)</h3>
      <div class="calrow"><div class="l">Высшая проба — финал</div><div class="r"><span class="d">6–16 фев</span><small>очно/центры</small></div></div>
      <div class="calrow"><div class="l">Физтех — финал</div><div class="r"><span class="d">фев–март</span><small>очно</small></div></div>
      <div class="calrow"><div class="l">Перечневые — финалы</div><div class="r"><span class="d">фев–март</span><small>рег. после отбора</small></div></div>
      <div class="calrow"><div class="l">Рег. этап ВсОШ</div><div class="r"><span class="d">янв–фев</span><small>проход на финал</small></div></div>
      <div class="calrow"><div class="l">Финал ВсОШ</div><div class="r"><span class="d">март–апр</span><small>безусловный БВИ</small></div></div>
    </div>

    <div class="note warn">
      ⚠️ С 2025/26 финалы олимпиад <b>одного профиля — в один день</b>. На отбор регистрируйтесь широко, к финалу выбирайте одну.
    </div>

    <div class="foot">
      Источники: приказ Минобрнауки № 669 от 30.08.2025; olymp.mipt.ru, olymp.hse.ru, olimpiada.ru, rsr-olymp.ru. Даты — ориентир по сезону 2025/26. Перед подачей сверяйтесь с правилами приёма вузов. Июнь 2026.
    </div>
  </div>

</div>

<!-- ============ ВКЛАДКИ ============ -->
<nav class="tabbar">
  <button class="on" data-v="v-table"><span class="ic">📊</span>Таблицы</button>
  <button data-v="v-top"><span class="ic">🏆</span>Топы</button>
  <button data-v="v-cal"><span class="ic">📅</span>Календарь</button>
</nav>

<script>
// ===== данные олимпиад =====
var DATA = {
  math:[
    {n:"ВсОШ (финал)",lv:"V",s:5,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Московская матем. (ММО/МОШ)",lv:"1",s:5,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Турнир городов",lv:"1",s:5,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Ломоносов (МГУ)",lv:"1",s:4,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Покори Воробьёвы горы!",lv:"1",s:4,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Высшая проба (ВШЭ)",lv:"1",s:4,t10:1,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Олимпиада СПбГУ",lv:"1",s:4,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"СПб олимпиада школьников",lv:"1",s:5,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Физтех (МФТИ)",lv:"2",s:4,t10:1,u:["h100","bvi","bvi","h100","h100"]},
    {n:"ОММО",lv:"2",s:4,t10:0,u:["h100","bvi*","bvi","h100","h100"]},
    {n:"Курчатов",lv:"2",s:3,t10:0,u:["h100","h100","bvi","h100","h100"]},
    {n:"Всесибирская открытая",lv:"2",s:3,t10:0,u:["h100","h100","bvi","h100","h100"]},
    {n:"Росатом (физ-мат)",lv:"2",s:3,t10:0,u:["h100","h100","bvi","h100","h100"]},
    {n:"Шаг в будущее (Бауман)",lv:"3",s:2,t10:0,u:["no","no","bvi","no","no"]},
    {n:"Открытая олимп. (ИТМО)",lv:"3",s:2,t10:0,u:["no","no","h100","no","bvi"]}
  ],
  phys:[
    {n:"ВсОШ (финал)",lv:"V",s:5,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Физтех (МФТИ)",lv:"1",s:4,t10:1,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Росатом (физ-мат)",lv:"1",s:4,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Ломоносов (МГУ)",lv:"1",s:4,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Покори Воробьёвы горы!",lv:"1",s:4,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Московская олимп. по физике",lv:"1",s:5,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Инженерная олимпиада",lv:"1",s:3,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Высшая проба (ВШЭ)",lv:"2",s:3,t10:1,u:["h100","h100","bvi","bvi","h100"]},
    {n:"Олимпиада СПбГУ",lv:"2",s:4,t10:0,u:["h100","h100","bvi","h100","h100"]},
    {n:"Всесибирская открытая",lv:"2",s:3,t10:0,u:["h100","h100","bvi","h100","h100"]},
    {n:"Курчатов",lv:"2",s:3,t10:0,u:["h100","h100","bvi","h100","h100"]},
    {n:"Интернет-олимп. по физике",lv:"2",s:3,t10:0,u:["h100","h100","h100","h100","h100"]},
    {n:"Шаг в будущее (Бауман)",lv:"2",s:2,t10:0,u:["h100","h100","bvi","h100","h100"]},
    {n:"Надежда энергетики",lv:"3",s:2,t10:0,u:["no","no","h100","no","no"]}
  ],
  inf:[
    {n:"ВсОШ (финал)",lv:"V",s:5,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Открытая по программир.",lv:"1",s:5,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Олимп. инф. и прогр. (ИТМО)",lv:"1",s:5,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Московская олимп. (информ.)",lv:"1",s:5,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Высшая проба (ВШЭ)",lv:"1",s:4,t10:1,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"ТехноКубок",lv:"1",s:4,t10:0,u:["bvi","bvi","bvi","bvi","bvi"]},
    {n:"Физтех (информатика)",lv:"2",s:4,t10:1,u:["h100","bvi","bvi","h100","h100"]},
    {n:"Innopolis Open",lv:"2",s:4,t10:0,u:["h100","bvi*","bvi","h100","bvi"]},
    {n:"Всесибирская открытая",lv:"2",s:3,t10:0,u:["h100","bvi*","bvi","h100","h100"]},
    {n:"Олимпиада СПбГУ",lv:"2",s:4,t10:0,u:["h100","bvi*","bvi","h100","h100"]},
    {n:"Открытая олимп. (ИТМО)",lv:"3",s:2,t10:0,u:["no","no","h100","no","bvi"]}
  ]
};
var UNIS=["МГУ","МФТИ","БМН","ВШЭ","ИТМО"];
function lvClass(lv){return lv=="1"?"lv1":lv=="2"?"lv2":lv=="3"?"lv3":"lvV";}
function lvText(lv){return lv=="V"?"ВсОШ":"L"+lv+" ".replace(/\s/,"")=="L"+lv?(lv+" ур."):lv;}
function stars(s){var f="★".repeat(s),e="☆".repeat(5-s);return f+e;}
function valClass(v){return v.indexOf("bvi")===0?"bvi":v=="h100"?"h100":"no";}
function valText(v){return v=="bvi"?"БВИ":v=="bvi*"?"БВИ*":v=="h100"?"100":"—";}

function render(subj){
  var arr=DATA[subj], html="";
  arr.forEach(function(o){
    var lc = o.lv=="1"?"lv1":o.lv=="2"?"lv2":o.lv=="3"?"lv3":"lvV";
    var lt = o.lv=="V"?"ВсОШ":o.lv+" ур.";
    var unis="";
    for(var i=0;i<5;i++){
      var v=o.u[i];
      unis+='<div class="uni"><span class="u">'+UNIS[i]+'</span><span class="v '+valClass(v)+'">'+valText(v)+'</span></div>';
    }
    html+='<div class="olymp">'
      +'<div class="row1"><div class="nm">'+o.n+'</div><div class="lvlbadge '+lc+'">'+lt+'</div></div>'
      +'<div class="meta"><span class="stars">'+stars(o.s)+'</span>'+(o.t10?'<span class="tag10">10 кл ✓</span>':'')+'</div>'
      +'<div class="unis">'+unis+'</div>'
      +'</div>';
  });
  document.getElementById("cards").innerHTML=html;
}
render("math");

// фильтр предмета
document.getElementById("seg").addEventListener("click",function(e){
  var b=e.target.closest("button"); if(!b)return;
  this.querySelectorAll("button").forEach(function(x){x.classList.remove("on")});
  b.classList.add("on");
  render(b.dataset.s);
  window.scrollTo({top:0,behavior:"smooth"});
});

// вкладки снизу
document.querySelector(".tabbar").addEventListener("click",function(e){
  var b=e.target.closest("button"); if(!b)return;
  this.querySelectorAll("button").forEach(function(x){x.classList.remove("on")});
  b.classList.add("on");
  document.querySelectorAll(".view").forEach(function(v){v.classList.remove("on")});
  document.getElementById(b.dataset.v).classList.add("on");
  window.scrollTo({top:0,behavior:"smooth"});
});
</script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'a05ee907be57c58e',t:'MTc4MDQ5MTkzNQ=='};var a=document.createElement('script');a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
