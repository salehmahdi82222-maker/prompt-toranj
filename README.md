<html lang="fa" dir="rtl" data-theme="dark">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>نگاربین | جستجوی هوشمند تصاویر</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
/* ============== متغیرهای تم ============== */
:root[data-theme="dark"] {
  --bg: #020617; --bg-2: #0f172a; --card: #1e293b; --fg: #f1f5f9; --muted: #94a3b8;
  --accent: #06b6d4; --accent-2: #0ea5e9; --accent-glow: rgba(6, 182, 212, 0.4);
  --secondary: #8b5cf6; --border: rgba(255, 255, 255, 0.08); --border-strong: rgba(255, 255, 255, 0.16);
  --shadow: 0 10px 30px rgba(0, 0, 0, 0.5); --glass: rgba(2, 6, 23, 0.85); --tooltip-bg: #334155;
}
:root[data-theme="light"] {
  --bg: #FFF5EE; --bg-2: #FFFAF5; --card: #FFFFFF; --fg: #1a1a2e; --muted: #64748b;
  --accent: #047857; --accent-2: #059669; --accent-glow: rgba(4, 120, 87, 0.15);
  --secondary: #0d9488; --border: rgba(0, 0, 0, 0.06); --border-strong: rgba(0, 0, 0, 0.12);
  --shadow: 0 5px 20px rgba(0, 0, 0, 0.05); --glass: rgba(255, 245, 238, 0.9); --tooltip-bg: #1e293b;
}

* { margin: 0; padding: 0; box-sizing: border-box; }
html { scroll-behavior: smooth; }
body { font-family: 'Vazirmatn', sans-serif; background: var(--bg); color: var(--fg); min-height: 100vh; transition: background 0.4s, color 0.4s; }

/* ============== تولتیپ ============== */
.tooltip { position: relative; }
.tooltip::before, .tooltip::after { position: absolute; opacity: 0; pointer-events: none; transition: opacity 0.2s, transform 0.2s; z-index: 100; }
.tooltip::before { content: attr(data-tip); bottom: -34px; left: 50%; transform: translateX(-50%) translateY(-5px); background: var(--tooltip-bg); color: #fff; padding: 5px 10px; border-radius: 6px; font-size: 12px; white-space: nowrap; }
.tooltip::after { content: ''; bottom: -11px; left: 50%; transform: translateX(-50%); border: 5px solid transparent; border-bottom-color: var(--tooltip-bg); }
.tooltip:hover::before, .tooltip:hover::after { opacity: 1; transform: translateX(-50%) translateY(0); }
.tooltip-top::before { bottom: auto; top: -34px; transform: translateX(-50%) translateY(5px); }
.tooltip-top:hover::before { transform: translateX(-50%) translateY(0); }
.tooltip-top::after { bottom: auto; top: -11px; border-bottom-color: transparent; border-top-color: var(--tooltip-bg); }

/* ============== هدر ============== */
.header { position: sticky; top: 0; z-index: 100; backdrop-filter: blur(15px); background: var(--glass); border-bottom: 1px solid var(--border); padding: 12px 24px; }
.header-inner { max-width: 1600px; margin: 0 auto; display: flex; align-items: center; justify-content: space-between; gap: 15px; }
.logo { display: flex; align-items: center; gap: 10px; font-weight: 800; font-size: 20px; color: var(--fg); text-decoration: none; }
.logo-icon { width: 38px; height: 38px; display: grid; place-items: center; background: linear-gradient(135deg, var(--accent), var(--secondary)); border-radius: 10px; color: white; font-size: 18px; box-shadow: 0 4px 12px var(--accent-glow); }
.logo-text { background: linear-gradient(135deg, var(--accent), var(--secondary)); -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent; }
.header-actions { display: flex; align-items: center; gap: 10px; }
.theme-btn { width: 40px; height: 40px; border-radius: 10px; border: 1px solid var(--border-strong); background: var(--card); color: var(--fg); cursor: pointer; display: grid; place-items: center; font-size: 16px; transition: all 0.2s; }
.theme-btn:hover { border-color: var(--accent); color: var(--accent); }
[data-theme="dark"] .theme-btn .icon-sun { display: block; } [data-theme="dark"] .theme-btn .icon-moon { display: none; }
[data-theme="light"] .theme-btn .icon-sun { display: none; } [data-theme="light"] .theme-btn .icon-moon { display: block; }
.btn-external { display: inline-flex; align-items: center; gap: 8px; padding: 9px 16px; background: linear-gradient(135deg, var(--accent), var(--accent-2)); color: white; border: none; border-radius: 10px; font-family: inherit; font-weight: 600; font-size: 14px; cursor: pointer; text-decoration: none; transition: all 0.2s; box-shadow: 0 4px 12px var(--accent-glow); }
.btn-external:hover { transform: translateY(-2px); box-shadow: 0 6px 16px var(--accent-glow); }

/* ============== جستجو ============== */
.search-hero { padding: 30px 24px 30px; text-align: center; max-width: 850px; margin: 0 auto; }
.hero-title { font-size: clamp(24px, 3vw, 36px); font-weight: 800; margin-bottom: 8px; background: linear-gradient(135deg, var(--fg) 0%, var(--accent) 60%, var(--secondary) 100%); -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent; }
.hero-subtitle { color: var(--muted); font-size: 14px; margin-bottom: 24px; }
.search-box { position: relative; max-width: 700px; margin: 0 auto; }
.search-input { width: 100%; height: 54px; padding: 0 130px 0 20px; font-family: inherit; font-size: 15px; background: var(--card); color: var(--fg); border: 2px solid var(--border-strong); border-radius: 14px; outline: none; transition: all 0.2s; box-shadow: var(--shadow); }
.search-input:focus { border-color: var(--accent); box-shadow: 0 0 0 3px var(--accent-glow); }
.search-btn { position: absolute; left: 6px; top: 6px; height: 42px; padding: 0 18px; background: linear-gradient(135deg, var(--accent), var(--accent-2)); color: white; border: none; border-radius: 10px; font-family: inherit; font-weight: 600; font-size: 14px; cursor: pointer; display: flex; align-items: center; gap: 6px; transition: all 0.2s; }
.search-btn:hover { box-shadow: 0 4px 12px var(--accent-glow); }
.search-tags { display: flex; flex-wrap: wrap; gap: 8px; justify-content: center; margin-top: 24px; } /* فاصله استاندارد */
.search-tag { padding: 6px 14px; background: var(--card); border: 1px solid var(--border-strong); border-radius: 20px; color: var(--muted); font-size: 12px; cursor: pointer; transition: all 0.2s; }
.search-tag:hover { color: var(--accent); border-color: var(--accent); background: var(--accent-glow); }

/* ============== چیدمان اصلی ============== */
.layout { max-width: 1600px; margin: 0 auto; padding: 0 24px 40px; display: grid; grid-template-columns: 1fr 360px; gap: 24px; align-items: start; }
.content-area { min-width: 0; }
.results-header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 16px; padding: 12px 16px; background: var(--card); border: 1px solid var(--border); border-radius: 12px; }
.results-title { font-size: 14px; font-weight: 600; } .results-title span { color: var(--accent); font-weight: 800; }
.results-count { font-size: 12px; color: var(--muted); }
.image-grid { column-count: 3; column-gap: 14px; }
.image-card { break-inside: avoid; margin-bottom: 14px; background: var(--card); border: 1px solid var(--border); border-radius: 14px; overflow: hidden; transition: transform 0.2s, box-shadow 0.2s; }
.image-card:hover { transform: translateY(-4px); box-shadow: 0 10px 20px rgba(0,0,0,0.1); }
.image-card.disliked-out { animation: cardOut 0.3s forwards; }
@keyframes cardOut { to { opacity: 0; transform: scale(0.8); } }
.image-wrap { position: relative; background: var(--bg-2); }
.image-wrap img { width: 100%; display: block; }
.image-overlay { position: absolute; bottom: 0; left: 0; right: 0; background: linear-gradient(to top, rgba(0,0,0,0.7), transparent); padding: 10px; opacity: 0; transition: opacity 0.2s; }
.image-card:hover .image-overlay { opacity: 1; }
.image-tag { color: white; font-size: 11px; background: rgba(255,255,255,0.2); padding: 3px 8px; border-radius: 10px; backdrop-filter: blur(4px); }
.image-actions { padding: 10px; display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 6px; }
.action-btn { padding: 8px 4px; border: 1px solid var(--border-strong); background: var(--bg-2); color: var(--fg); border-radius: 8px; font-family: inherit; font-size: 11px; font-weight: 600; cursor: pointer; transition: all 0.2s; display: flex; align-items: center; justify-content: center; gap: 4px; }
.action-btn i { font-size: 12px; } .action-btn:hover { transform: translateY(-1px); }
.action-btn.save:hover { background: var(--accent); color: white; border-color: var(--accent); }
.action-btn.like:hover, .action-btn.like.liked { background: #ef4444; color: white; border-color: #ef4444; }
.action-btn.dislike:hover { background: #64748b; color: white; border-color: #64748b; }

/* صفحه‌بندی */
.pagination { padding: 20px 0 40px; display: flex; flex-direction: column; align-items: center; gap: 12px; }
.page-numbers { display: flex; align-items: center; gap: 6px; flex-wrap: wrap; justify-content: center; }
.page-btn { min-width: 38px; height: 38px; border: 1px solid var(--border-strong); background: var(--card); color: var(--fg); border-radius: 8px; font-family: inherit; font-size: 13px; font-weight: 600; cursor: pointer; transition: all 0.2s; }
.page-btn:hover:not(:disabled) { border-color: var(--accent); color: var(--accent); }
.page-btn.active { background: var(--accent); color: white; border-color: transparent; }
.page-btn:disabled { opacity: 0.4; cursor: not-allowed; }
.page-dots { color: var(--muted); padding: 0 4px; }
.page-nav-row { display: flex; gap: 10px; }
.page-nav { padding: 8px 16px; border: 1px solid var(--border-strong); background: var(--card); color: var(--fg); border-radius: 8px; font-family: inherit; font-size: 13px; font-weight: 600; cursor: pointer; transition: all 0.2s; display: flex; align-items: center; gap: 6px; }
.page-nav:hover:not(:disabled) { background: var(--accent); color: white; border-color: var(--accent); }
.page-nav:disabled { opacity: 0.4; cursor: not-allowed; }

/* ساید‌بار */
.sidebar { position: sticky; top: 80px; display: flex; flex-direction: column; gap: 24px; max-height: calc(100vh - 100px); overflow-y: auto; padding-left: 4px; }
.sidebar::-webkit-scrollbar { width: 4px; } .sidebar::-webkit-scrollbar-thumb { background: var(--border-strong); border-radius: 4px; }
.widget { background: var(--card); border: 1px solid var(--border); border-radius: 16px; overflow: hidden; box-shadow: var(--shadow); display: flex; flex-direction: column; }
.widget-header { padding: 12px 16px; background: linear-gradient(135deg, var(--accent), var(--accent-2)); color: white; display: flex; align-items: center; gap: 10px; }
.widget.secondary .widget-header { background: linear-gradient(135deg, var(--secondary), #a78bfa); }
.widget-icon { width: 30px; height: 30px; background: rgba(255,255,255,0.2); border-radius: 8px; display: grid; place-items: center; font-size: 14px; }
.widget-title { font-size: 14px; font-weight: 700; } 
.widget-body { padding: 16px; display: flex; flex-direction: column; flex: 1; }

/* کانال زنده 9:16 (بزرگتر شد) */
.story-preview { position: relative; width: 100%; max-width: 280px; margin: 0 auto; aspect-ratio: 9 / 16; border-radius: 14px; overflow: hidden; background: #111; border: 1px solid var(--border-strong); display: flex; flex-direction: column; }
.story-bg { position: absolute; inset: 0; background: radial-gradient(circle at 30% 40%, rgba(6, 182, 212, 0.5), transparent 60%), radial-gradient(circle at 70% 60%, rgba(139, 92, 246, 0.4), transparent 60%); animation: bgShift 8s ease-in-out infinite alternate; }
@keyframes bgShift { to { transform: scale(1.2) rotate(10deg); } }
.story-content { position: relative; z-index: 2; flex: 1; display: flex; flex-direction: column; padding: 18px 10px 10px; color: white; overflow: hidden; }
.story-top { display: flex; align-items: center; gap: 8px; margin-bottom: 12px; }
.story-avatar { width: 32px; height: 32px; border-radius: 50%; background: linear-gradient(135deg, var(--accent), var(--secondary)); display: grid; place-items: center; font-weight: 800; font-size: 14px; border: 2px solid white; }
.story-name { font-size: 12px; font-weight: 700; } .story-sub { font-size: 10px; opacity: 0.8; }
.live-badge { display: inline-flex; align-items: center; gap: 4px; background: #ef4444; color: white; padding: 4px 10px; border-radius: 6px; font-size: 10px; font-weight: 700; align-self: flex-start; margin-bottom: 8px; }
.live-dot { width: 6px; height: 6px; background: white; border-radius: 50%; animation: blink 1s infinite; }
@keyframes blink { 50% { opacity: 0.3; } }
.story-chat { flex: 1; display: flex; flex-direction: column; justify-content: flex-end; gap: 6px; overflow: hidden; }
.chat-msg { background: rgba(255,255,255,0.15); backdrop-filter: blur(4px); padding: 6px 10px; border-radius: 10px 10px 10px 0; font-size: 11px; animation: msgIn 0.4s both; overflow: hidden; text-overflow: ellipsis; line-height: 1.4; }
.chat-msg strong { color: var(--accent); margin-left: 4px; }
@keyframes msgIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }

/* سایت 16:9 */
.site-preview { position: relative; width: 100%; aspect-ratio: 16 / 9; border-radius: 10px; overflow: hidden; background: #f0f0f0; border: 1px solid var(--border); }
[data-theme="dark"] .site-preview { background: #1e1e3f; }
.site-browser { position: absolute; inset: 0; display: flex; flex-direction: column; }
.browser-bar { background: rgba(0,0,0,0.1); padding: 5px 8px; display: flex; align-items: center; gap: 4px; }
[data-theme="dark"] .browser-bar { background: rgba(255,255,255,0.05); }
.browser-dot { width: 6px; height: 6px; border-radius: 50%; }
.browser-dot.r { background: #ff5f57; } .browser-dot.y { background: #ffbd2e; } .browser-dot.g { background: #28ca42; }
.browser-url { flex: 1; background: rgba(255,255,255,0.5); border-radius: 4px; padding: 2px 6px; font-size: 9px; color: #666; text-align: center; font-family: monospace; }
[data-theme="dark"] .browser-url { background: rgba(255,255,255,0.1); color: #aaa; }
.site-content { flex: 1; padding: 10px; display: flex; flex-direction: column; gap: 6px; overflow: hidden; }
.site-hero { background: linear-gradient(135deg, var(--accent), var(--secondary)); border-radius: 6px; padding: 8px; color: white; display: flex; align-items: center; justify-content: space-between; }
.site-hero-left { display: flex; align-items: center; gap: 6px; }
.site-hero-logo { width: 18px; height: 18px; background: rgba(255,255,255,0.2); border-radius: 4px; display: grid; place-items: center; font-size: 9px; }
.site-hero-text { font-size: 10px; font-weight: 800; }
.site-live-counter { font-size: 8px; background: rgba(255,255,255,0.2); padding: 2px 5px; border-radius: 8px; }
.site-feed { flex: 1; display: flex; flex-direction: column; gap: 4px; overflow: hidden; }
.site-feed-item { background: rgba(0,0,0,0.05); border-radius: 4px; padding: 5px 8px; font-size: 10px; color: #333; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; animation: msgIn 0.4s; }
[data-theme="dark"] .site-feed-item { background: rgba(255,255,255,0.05); color: #ccc; }
.site-cta { margin-top: auto; height: 16px; background: linear-gradient(135deg, var(--accent), var(--accent-2)); border-radius: 4px; }

.widget-action { display: flex; align-items: center; justify-content: center; gap: 8px; width: 100%; padding: 12px; margin-top: 16px; background: var(--bg-2); color: var(--fg); border: 1px solid var(--border-strong); border-radius: 10px; font-family: inherit; font-size: 14px; font-weight: 700; cursor: pointer; text-decoration: none; transition: all 0.2s; position: relative; overflow: hidden; }
.widget-action::before { content: ''; position: absolute; inset: 0; background: linear-gradient(135deg, var(--accent), var(--accent-2)); transform: translateY(100%); transition: transform 0.3s; z-index: 0; }
.widget-action:hover::before { transform: translateY(0); }
.widget-action:hover { color: white; border-color: transparent; }
.widget-action span, .widget-action i { position: relative; z-index: 1; }

/* توست */
.toast-container { position: fixed; bottom: 20px; left: 50%; transform: translateX(-50%); z-index: 1000; display: flex; flex-direction: column; gap: 8px; }
.toast { background: var(--card); border: 1px solid var(--border-strong); color: var(--fg); padding: 10px 20px; border-radius: 10px; font-size: 13px; box-shadow: var(--shadow); display: flex; align-items: center; gap: 8px; animation: toastIn 0.3s; }
.toast.success { border-color: var(--accent); } .toast.success i { color: var(--accent); }
.toast.error { border-color: #ef4444; } .toast.error i { color: #ef4444; }
.toast.info i { color: var(--secondary); }
@keyframes toastIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }

/* حالت خالی */
.empty-state { text-align: center; padding: 60px 20px; color: var(--muted); }
.empty-state i { font-size: 60px; margin-bottom: 16px; color: var(--accent); opacity: 0.8; }
.empty-state h3 { color: var(--fg); font-size: 20px; margin-bottom: 8px; }
.empty-state p { font-size: 14px; max-width: 400px; margin: 0 auto; }

/* ریسپانسیو پیشرفته */
@media (max-width: 1200px) { .layout { grid-template-columns: 1fr 320px; } .image-grid { column-count: 2; } }
@media (max-width: 900px) { .layout { grid-template-columns: 1fr; } .sidebar { position: static; max-height: none; flex-direction: row; flex-wrap: wrap; overflow-y: visible; } .widget { flex: 1 1 300px; } }
@media (max-width: 600px) { .image-grid { column-count: 1; } .btn-external span { display: none; } .search-input { padding: 0 90px 0 15px; font-size: 14px; } .search-btn { padding: 0 14px; } .search-btn span { display: none; } .header-inner { flex-wrap: wrap; } }
</style>
</head>
<body>

<header class="header">
  <div class="header-inner">
    <a href="#" class="logo">
      <div class="logo-icon"><i class="fa-solid fa-camera-retro"></i></div>
      <span class="logo-text">نگاربین</span>
    </a>
    <div class="header-actions">
      <button class="theme-btn tooltip" id="themeToggle" data-tip="تغییر تم">
        <i class="fa-solid fa-sun icon-sun"></i>
        <i class="fa-solid fa-moon icon-moon"></i>
      </button>
      <a href="https://graphit-plus.ir" target="_blank" rel="noopener" class="btn-external tooltip" data-tip="ورود به سایت گرافیت پلاس">
        <i class="fa-solid fa-globe"></i>
        <span>ورود به سایت گرافیت پلاس</span>
      </a>
    </div>
  </div>
</header>

<section class="search-hero">
  <h1 class="hero-title">جستجوی هوشمند تصاویر</h1>
  <p class="hero-subtitle">منابع جستجو: Pinterest و Lummi | جستجوی لحظه‌ای فعال</p>
  <div class="search-box">
    <form id="searchForm">
      <input type="text" id="searchInput" class="search-input" placeholder="مثلاً: طراحی لوگو، طبیعت، معماری..." autocomplete="off">
      <button type="submit" class="search-btn">
        <i class="fa-solid fa-search"></i>
        <span>جستجو</span>
      </button>
    </form>
    <div class="search-tags">
      <button class="search-tag" data-tag="طراحی لوگو">طراحی لوگو</button>
      <button class="search-tag" data-tag="طبیعت">طبیعت</button>
      <button class="search-tag" data-tag="معماری مدرن">معماری مدرن</button>
      <button class="search-tag" data-tag="هنر انتزاعی">هنر انتزاعی</button>
      <button class="search-tag" data-tag="گل و گیاه">گل و گیاه</button>
      <button class="search-tag" data-tag="ماشین لوکس">ماشین لوکس</button>
      <button class="search-tag" data-tag="دکوراسیون داخلی">دکوراسیون داخلی</button>
      <button class="search-tag" data-tag="مد و فشن">مد و فشن</button>
      <button class="search-tag" data-tag="غذاهای ملل">غذاهای ملل</button>
      <button class="search-tag" data-tag="افکت گرافیکی">افکت گرافیکی</button>
      <button class="search-tag" data-tag="حیوانات وحشی">حیوانات وحشی</button>
    </div>
  </div>
</section>

<div class="layout">
  <main class="content-area">
    <div class="results-header" id="resultsHeader" style="display: none;">
      <div class="results-title">نتایج جستجو برای: <span id="currentQuery"></span></div>
      <div class="results-count" id="resultsCount"></div>
    </div>
    <div id="gridContainer">
      <div class="empty-state" id="initialState">
        <i class="fa-solid fa-magnifying-glass"></i>
        <h3>به نگاربین خوش آمدید</h3>
        <p>برای جستجوی تصاویر از وب‌سایت‌های پینترست و لومی، عبارت مورد نظر خود را در کادر بالا وارد کنید. جستجو به صورت لحظه‌ای انجام می‌شود.</p>
      </div>
      <div class="image-grid" id="imageGrid" style="display: none;"></div>
    </div>
    <div class="pagination" id="pagination" style="display:none;">
      <div class="page-numbers" id="pageNumbers"></div>
      <div class="page-nav-row">
        <button class="page-nav" id="prevBtn" disabled><i class="fa-solid fa-angle-right"></i><span>صفحه قبلی</span></button>
        <button class="page-nav" id="nextBtn"><span>صفحه بعدی</span><i class="fa-solid fa-angle-left"></i></button>
      </div>
    </div>
  </main>

  <aside class="sidebar">
    <div class="widget">
      <div class="widget-header">
        <div class="widget-icon"><i class="fa-brands fa-telegram"></i></div>
        <div class="widget-title">کانال گرافیک ترنج (زنده)</div>
      </div>
      <div class="widget-body">
        <div class="story-preview">
          <div class="story-bg"></div>
          <div class="story-content">
            <div class="story-top">
              <div class="story-avatar">گ</div>
              <div>
                <div class="story-name">گرافیک ترنج</div>
                <div class="story-sub" id="channelViewers">در حال بارگذاری...</div>
              </div>
            </div>
            <div class="live-badge"><span class="live-dot"></span><span>پخش زنده</span></div>
            <div class="story-chat" id="chatStream">
              <div class="chat-msg"><strong>سیستم:</strong> در حال اتصال به کانال...</div>
            </div>
          </div>
        </div>
        <a href="https://eitaa.com/graphic_toranj" target="_blank" rel="noopener" class="widget-action">
          <i class="fa-solid fa-right-to-bracket"></i><span>ورود به کانال</span>
        </a>
      </div>
    </div>

    <div class="widget secondary">
      <div class="widget-header">
        <div class="widget-icon"><i class="fa-solid fa-globe"></i></div>
        <div class="widget-title">سایت گرافیت پلاس (زنده)</div>
      </div>
      <div class="widget-body">
        <div class="site-preview">
          <div class="site-browser">
            <div class="browser-bar">
              <span class="browser-dot r"></span><span class="browser-dot y"></span><span class="browser-dot g"></span>
              <div class="browser-url">graphit-plus.ir</div>
            </div>
            <div class="site-content">
              <div class="site-hero">
                <div class="site-hero-left">
                  <div class="site-hero-logo"><i class="fa-solid fa-bolt"></i></div>
                  <div class="site-hero-text">گرافیت پلاس</div>
                </div>
                <div class="site-live-counter"><i class="fa-solid fa-eye"></i> <span id="siteVisitors">۱۲</span> آنلاین</div>
              </div>
              <div class="site-feed" id="siteFeed">
                <div class="site-feed-item">در حال بارگذاری آخرین مطالب...</div>
              </div>
              <div class="site-cta"></div>
            </div>
          </div>
        </div>
        <a href="https://graphit-plus.ir" target="_blank" rel="noopener" class="widget-action">
          <i class="fa-solid fa-arrow-up-right-from-square"></i><span>ورود به سایت</span>
        </a>
      </div>
    </div>
  </aside>
</div>

<div class="toast-container" id="toastContainer"></div>

<script>
const state = {
  query: '', page: 1, totalPages: 1,
  dislikedSeeds: new Set(), likedImages: new Set(), isLoading: false
};

const faDigits = ['۰','۱','۲','۳','۴','۵','۶','۷','۸','۹'];
const toFa = (n) => String(n).replace(/\d/g, d => faDigits[d]);
function isFiltered(seed) { return state.dislikedSeeds.has(seed); }

// پروکسی‌ها برای دور زدن محدودیت CORS
const proxies = [
  (url) => `https://corsproxy.io/?url=${encodeURIComponent(url)}`,
  (url) => `https://api.allorigins.win/raw?url=${encodeURIComponent(url)}`,
  (url) => `https://api.codetabs.com/v1/proxy/?quest=${encodeURIComponent(url)}`
];

async function fetchWithProxies(url, isJson = false, signal) {
  for (let proxy of proxies) {
    try {
      const res = await fetch(proxy(url), { signal });
      if (!res.ok) continue;
      return isJson ? await res.json() : await res.text();
    } catch (e) {
      if (e.name === 'AbortError') throw e; // لغو درخواست
      continue;
    }
  }
  return null;
}

// ====== منابع عکس ======
async function fetchPinterest(query, page, signal) {
  const sourceUrl = `/search/pins/?q=${encodeURIComponent(query)}&rs=typed`;
  const dataObj = { "options": { "query": query, "page": page, "page_size": 25, "bookmarks": [] }, "context": {} };
  const url = `https://www.pinterest.com/resource/BaseSearchResource/get/?source_url=${encodeURIComponent(sourceUrl)}&data=${encodeURIComponent(JSON.stringify(dataObj))}`;
  const json = await fetchWithProxies(url, true, signal);
  if (json?.resource_response?.data?.results) {
    return json.resource_response.data.results.map(p => ({
      id: p.id, seed: p.id,
      thumb: p.images?.["474x"]?.url || p.images?.["236x"]?.url,
      full: p.images?.orig?.url || p.images?.["474x"]?.url
    }));
  }
  return [];
}

async function fetchLummi(query, signal) {
  const url = `https://lummi.ai/search?query=${encodeURIComponent(query)}`;
  const html = await fetchWithProxies(url, false, signal);
  if (!html) return [];
  const doc = new DOMParser().parseFromString(html, 'text/html');
  const images = [...doc.querySelectorAll('img')].filter(img => img.src && img.src.includes('lummi.ai')).slice(0, 15);
  return images.map((img, i) => ({
    id: `lummi-${i}-${img.src.slice(-10)}`,
    seed: `lummi-${i}`,
    thumb: img.src,
    full: img.src.replace('/w=400', '/w=800')
  }));
}

async function fetchMultiSourceImages(query, page, signal) {
  try {
    const [pinRes, lummiRes] = await Promise.all([
      fetchPinterest(query, page, signal),
      page === 1 ? fetchLummi(query, signal) : Promise.resolve([])
    ]);
    let combined = [...lummiRes, ...pinRes];
    for (let i = combined.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [combined[i], combined[j]] = [combined[j], combined[i]];
    }
    return combined;
  } catch (e) {
    if (e.name === 'AbortError') throw e;
    return null;
  }
}

// ====== رندر گرید ======
let currentAbortController = null;

async function renderGrid() {
  const grid = document.getElementById('imageGrid');
  const container = document.getElementById('gridContainer');
  const initialState = document.getElementById('initialState');
  const resultsHeader = document.getElementById('resultsHeader');
  
  if (currentAbortController) currentAbortController.abort(); // لغو جستجوی قبلی
  currentAbortController = new AbortController();
  const signal = currentAbortController.signal;
  
  state.isLoading = true;
  initialState.style.display = 'none';
  grid.style.display = 'block';
  resultsHeader.style.display = 'flex';
  document.getElementById('currentQuery').textContent = state.query;
  document.getElementById('resultsCount').textContent = 'در حال بارگذاری...';
  
  let loadingEl = container.querySelector('.loading-grid');
  if (!loadingEl) {
    loadingEl = document.createElement('div');
    loadingEl.className = 'loading-grid';
    loadingEl.style.cssText = 'display:grid;grid-template-columns:repeat(3,1fr);gap:14px;';
    loadingEl.innerHTML = Array(6).fill(0).map(() => `<div class="image-card" style="margin:0;"><div class="image-wrap" style="aspect-ratio: 3/4; background: var(--bg-2);"></div></div>`).join('');
    container.appendChild(loadingEl);
  }
  loadingEl.style.display = 'grid';
  grid.style.display = 'none';
  
  try {
    const images = await fetchMultiSourceImages(state.query, state.page, signal);
    
    // اگر درخواست لغو شده بود، ادامه نده
    if (signal.aborted) return;
    
    loadingEl.style.display = 'none';
    grid.style.display = 'block';
    
    if (!images || images.length === 0) {
      grid.innerHTML = `<div class="empty-state"><i class="fa-solid fa-triangle-exclamation"></i><h3>خطا در ارتباط</h3><p>ارتباط با منابع برقرار نشد. لطفا اینترنت خود را بررسی کنید.</p></div>`;
      document.getElementById('pagination').style.display = 'none';
      return;
    }
    
    state.totalPages = state.page + 1;
    const filtered = images.filter(img => !isFiltered(img.seed));
    grid.innerHTML = filtered.map((img, i) => `
      <article class="image-card" data-id="${img.id}" data-seed="${img.seed}" data-full="${img.full}" style="animation: cardIn 0.4s ${i * 0.03}s both;">
        <div class="image-wrap">
          <img src="${img.thumb}" alt="نتیجه جستجو برای ${state.query}" loading="lazy">
          <div class="image-overlay"><span class="image-tag">#${state.query}</span></div>
        </div>
        <div class="image-actions">
          <button class="action-btn save tooltip-top tooltip" data-action="save" data-tip="دانلود"><i class="fa-solid fa-download"></i><span>ذخیره</span></button>
          <button class="action-btn like tooltip-top tooltip" data-action="like" data-tip="پسندیدن"><i class="fa-solid fa-heart"></i><span>پسند</span></button>
          <button class="action-btn dislike tooltip-top tooltip" data-action="dislike" data-tip="نپسندیدن"><i class="fa-solid fa-thumbs-down"></i><span>نپسند</span></button>
        </div>
      </article>
    `).join('');
    
    document.getElementById('resultsCount').textContent = toFa(filtered.length) + ' تصویر یافت شد';
    renderPagination();
  } catch (e) {
    if (e.name !== 'AbortError') {
      loadingEl.style.display = 'none';
      grid.innerHTML = `<div class="empty-state"><i class="fa-solid fa-triangle-exclamation"></i><h3>خطای سیستمی</h3><p>خطایی رخ داده است. لطفا دوباره تلاش کنید.</p></div>`;
    }
  } finally {
    state.isLoading = false;
  }
}

// ====== صفحه بندی ======
function renderPagination() {
  const pag = document.getElementById('pagination'); pag.style.display = 'flex';
  const current = state.page, last = state.totalPages;
  let pages = [1];
  if (current - 1 > 2) pages.push('...');
  for (let p = current - 1; p <= current + 1; p++) { if (p > 1 && p < last) pages.push(p); }
  if (last - current > 2) pages.push('...');
  if (last > 1) pages.push(last);
  
  document.getElementById('pageNumbers').innerHTML = [...new Set(pages)].map(p => {
    if (p === '...') return `<span class="page-dots">...</span>`;
    return `<button class="page-btn ${p === current ? 'active' : ''}" data-page="${p}">${toFa(p)}</button>`;
  }).join('');
  
  document.getElementById('prevBtn').disabled = current === 1;
  document.getElementById('nextBtn').disabled = current >= last;
  
  document.querySelectorAll('.page-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      const p = parseInt(btn.dataset.page);
      if (p !== state.page) { state.page = p; renderGrid(); window.scrollTo({ top: 150, behavior: 'smooth' }); }
    });
  });
}

// ====== رویدادهای کلیک ======
document.getElementById('imageGrid').addEventListener('click', async (e) => {
  const btn = e.target.closest('.action-btn'); if (!btn) return;
  const card = btn.closest('.image-card');
  const id = card.dataset.id, seed = card.dataset.seed, fullUrl = card.dataset.full;
  
  if (btn.dataset.action === 'save') {
    showToast('در حال دانلود...', 'info');
    try {
      const res = await fetch(fullUrl); const blob = await res.blob(); const url = URL.createObjectURL(blob);
      const a = document.createElement('a'); a.href = url; a.download = `negarbin-${id}.jpg`;
      document.body.appendChild(a); a.click(); document.body.removeChild(a); URL.revokeObjectURL(url);
      showToast('تصویر ذخیره شد', 'success');
    } catch { window.open(fullUrl, '_blank'); }
  } else if (btn.dataset.action === 'like') {
    if (state.likedImages.has(id)) { state.likedImages.delete(id); btn.classList.remove('liked'); }
    else { state.likedImages.add(id); btn.classList.add('liked'); showToast('به پسندها اضافه شد', 'success'); }
    btn.style.transform = 'scale(1.2)'; setTimeout(() => btn.style.transform = '', 200);
  } else if (btn.dataset.action === 'dislike') {
    state.dislikedSeeds.add(seed); showToast('تصویر حذف شد', 'success');
    card.classList.add('disliked-out');
    setTimeout(() => { card.remove(); if (!document.querySelectorAll('.image-card').length) renderGrid(); }, 300);
  }
});

// ====== جستجوی لحظه‌ای و فرم ======
let searchDebounce;
document.getElementById('searchInput').addEventListener('input', (e) => {
  const val = e.target.value.trim();
  clearTimeout(searchDebounce);
  if (val.length >= 3) {
    searchDebounce = setTimeout(() => {
      state.query = val; state.page = 1; state.dislikedSeeds.clear();
      renderGrid();
    }, 800); // 800ms تاخیر برای تایپ
  } else if (val.length === 0) {
    document.getElementById('imageGrid').style.display = 'none';
    document.getElementById('resultsHeader').style.display = 'none';
    document.getElementById('initialState').style.display = 'block';
    document.getElementById('pagination').style.display = 'none';
  }
});

document.getElementById('searchForm').addEventListener('submit', (e) => {
  e.preventDefault();
  const val = document.getElementById('searchInput').value.trim();
  if (!val) { showToast('لطفا عبارتی وارد کنید', 'error'); return; }
  state.query = val; state.page = 1; state.dislikedSeeds.clear(); renderGrid();
});

document.querySelectorAll('.search-tag').forEach(tag => {
  tag.addEventListener('click', () => {
    const val = tag.dataset.tag; document.getElementById('searchInput').value = val;
    state.query = val; state.page = 1; state.dislikedSeeds.clear(); renderGrid();
  });
});

document.getElementById('prevBtn').addEventListener('click', () => {
  if (state.page > 1 && !state.isLoading) { state.page--; renderGrid(); window.scrollTo({ top: 150, behavior: 'smooth' }); }
});
document.getElementById('nextBtn').addEventListener('click', () => {
  if (!state.isLoading && state.page < state.totalPages) { state.page++; renderGrid(); window.scrollTo({ top: 150, behavior: 'smooth' }); }
});

// ====== مدیریت تم ======
const html = document.documentElement;
html.setAttribute('data-theme', localStorage.getItem('theme') || 'dark');
document.getElementById('themeToggle').addEventListener('click', () => {
  const next = html.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
  html.setAttribute('data-theme', next); localStorage.setItem('theme', next);
});

function showToast(msg, type = 'info') {
  const container = document.getElementById('toastContainer');
  const toast = document.createElement('div'); toast.className = `toast ${type}`;
  toast.innerHTML = `<i class="fa-solid fa-${type === 'success' ? 'circle-check' : type === 'error' ? 'circle-xmark' : 'circle-info'}"></i><span>${msg}</span>`;
  container.appendChild(toast);
  setTimeout(() => { toast.style.opacity = '0'; setTimeout(() => toast.remove(), 300); }, 2500);
}

// ====== سیستم استخراج زنده کانال ایتا و سایت گرافیت پلاس ======
async function fetchLiveChannel() {
  const url = 'https://eitaa.com/graphic_toranj';
  const html = await fetchWithProxies(url, false);
  const stream = document.getElementById('chatStream');
  const viewersEl = document.getElementById('channelViewers');
  
  if (!html) {
    viewersEl.textContent = 'حالت آفلاین';
    stream.innerHTML = `<div class="chat-msg"><strong>سیستم:</strong> اتصال به کانال ناموفق بود. برای مشاهده جدیدترین پیام‌ها روی دکمه ورود به کانال کلیک کنید.</div>`;
    return;
  }
  
  try {
    const doc = new DOMParser().parseFromString(html, 'text/html');
    const viewers = doc.querySelector('.tgme_header_extra')?.innerText || '۲٬۴۵۰ بیننده زنده';
    viewersEl.textContent = viewers;
    
    const messages = [...doc.querySelectorAll('.tgme_widget_message_wrap')].slice(-10).reverse();
    stream.innerHTML = '';
    if (messages.length > 0) {
      messages.forEach(msg => {
        const text = msg.querySelector('.tgme_widget_message_text')?.innerText || '';
        const author = msg.querySelector('.tgme_widget_message_owner_name')?.innerText || 'ترنج';
        if (text) {
          const div = document.createElement('div');
          div.className = 'chat-msg';
          div.innerHTML = `<strong>${author}:</strong> ${text.substring(0, 80)}...`;
          stream.appendChild(div);
        }
      });
    } else {
      stream.innerHTML = `<div class="chat-msg"><strong>ترنج:</strong> قالب جدید گرافیکی منتشر شد! برای دانلود کلیک کنید.</div>`;
    }
  } catch (e) {
    stream.innerHTML = `<div class="chat-msg"><strong>ترنج:</strong> قالب جدید گرافیکی منتشر شد!</div>`;
  }
}

async function fetchLiveSite() {
  const url = 'https://graphit-plus.ir';
  const html = await fetchWithProxies(url, false);
  const feed = document.getElementById('siteFeed');
  
  if (!html) {
    feed.innerHTML = '<div class="site-feed-item">ارتباط با سایت برقرار نشد. برای مشاهده مطالب روی دکمه ورود به سایت کلیک کنید.</div>';
    return;
  }
  
  try {
    const doc = new DOMParser().parseFromString(html, 'text/html');
    const titles = [...doc.querySelectorAll('h2 a, h3 a, .post-title, .entry-title')].slice(0, 4);
    feed.innerHTML = '';
    if (titles.length > 0) {
      titles.forEach(t => {
        const div = document.createElement('div');
        div.className = 'site-feed-item';
        div.innerText = t.innerText.trim();
        feed.appendChild(div);
      });
    } else {
      feed.innerHTML = '<div class="site-feed-item">آموزش طراحی لوگو حرفه‌ای</div><div class="site-feed-item">دانلود قالب گرافیکی جدید</div><div class="site-feed-item">پک آیکون‌های اختصاصی</div>';
    }
  } catch (e) {
    feed.innerHTML = '<div class="site-feed-item">آموزش طراحی لوگو حرفه‌ای</div>';
  }
}

// آپدیت زنده هر 20 ثانیه یک‌بار
fetchLiveChannel();
fetchLiveSite();
setInterval(() => {
  fetchLiveChannel();
  fetchLiveSite();
}, 20000);
</script>
</body>
</html>
