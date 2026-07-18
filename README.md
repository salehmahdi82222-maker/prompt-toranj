<!DOCTYPE html>
<html lang="fa" dir="rtl" data-theme="dark">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>گرافیت پلاس | جستجوی هوشمند تصاویر</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@100;300;400;500;600;700;800;900&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
/* ============== متغیرهای تم ============== */
:root[data-theme="dark"] {
  --bg: #0a0a14;
  --bg-2: #12122a;
  --card: #181838;
  --card-hover: #202040;
  --fg: #f0f0f8;
  --muted: #8a8ab0;
  --accent: #ff4757;
  --accent-2: #ff6b81;
  --accent-glow: rgba(255, 71, 87, 0.35);
  --secondary: #6c5ce7;
  --secondary-glow: rgba(108, 92, 231, 0.3);
  --border: rgba(255, 255, 255, 0.08);
  --border-strong: rgba(255, 255, 255, 0.18);
  --shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
  --shadow-glow: 0 0 40px var(--accent-glow);
  --grad-bg: radial-gradient(ellipse at top right, rgba(255, 71, 87, 0.18), transparent 50%),
             radial-gradient(ellipse at bottom left, rgba(108, 92, 231, 0.12), transparent 55%);
  --glass: rgba(24, 24, 56, 0.6);
  --success: #2ed573;
  --danger: #ff4757;
}

:root[data-theme="light"] {
  --bg: #faf6f0;
  --bg-2: #ffffff;
  --card: #ffffff;
  --card-hover: #fcf9f5;
  --fg: #1a1a2e;
  --muted: #6c6c80;
  --accent: #e63946;
  --accent-2: #f1556c;
  --accent-glow: rgba(230, 57, 70, 0.22);
  --secondary: #5f4dd6;
  --secondary-glow: rgba(95, 77, 214, 0.18);
  --border: rgba(0, 0, 0, 0.08);
  --border-strong: rgba(0, 0, 0, 0.16);
  --shadow: 0 10px 40px rgba(0, 0, 0, 0.08);
  --shadow-glow: 0 0 40px var(--accent-glow);
  --grad-bg: radial-gradient(ellipse at top right, rgba(230, 57, 70, 0.1), transparent 50%),
             radial-gradient(ellipse at bottom left, rgba(95, 77, 214, 0.07), transparent 55%);
  --glass: rgba(255, 255, 255, 0.7);
  --success: #1da851;
  --danger: #e63946;
}

/* ============== ریست ============== */
* { margin: 0; padding: 0; box-sizing: border-box; }
html { scroll-behavior: smooth; }
body {
  font-family: 'Vazirmatn', sans-serif;
  background: var(--bg);
  color: var(--fg);
  min-height: 100vh;
  overflow-x: hidden;
  transition: background 0.6s ease, color 0.6s ease;
  position: relative;
}

/* پس‌زمینه اتمسفریک */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background: var(--grad-bg);
  z-index: -2;
  transition: opacity 0.6s ease;
}

.blob {
  position: fixed;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.5;
  z-index: -1;
  pointer-events: none;
  animation: float 20s ease-in-out infinite;
}
.blob-1 {
  width: 400px; height: 400px;
  background: var(--accent);
  top: -100px; right: -100px;
  opacity: 0.2;
}
.blob-2 {
  width: 350px; height: 350px;
  background: var(--secondary);
  bottom: -100px; left: -100px;
  opacity: 0.18;
  animation-delay: -10s;
}
@keyframes float {
  0%, 100% { transform: translate(0, 0) scale(1); }
  33% { transform: translate(30px, -30px) scale(1.05); }
  66% { transform: translate(-20px, 20px) scale(0.95); }
}

/* ============== هدر ============== */
.header {
  position: sticky;
  top: 0;
  z-index: 100;
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  background: var(--glass);
  border-bottom: 1px solid var(--border);
  padding: 16px 32px;
  animation: slideDown 0.7s cubic-bezier(0.16, 1, 0.3, 1);
}
@keyframes slideDown {
  from { transform: translateY(-100%); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}
.header-inner {
  max-width: 1600px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}
.logo {
  display: flex;
  align-items: center;
  gap: 12px;
  font-weight: 800;
  font-size: 22px;
  color: var(--fg);
  text-decoration: none;
}
.logo-icon {
  width: 42px; height: 42px;
  display: grid; place-items: center;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  border-radius: 12px;
  color: white;
  font-size: 20px;
  box-shadow: 0 8px 24px var(--accent-glow);
  animation: pulse 3s ease-in-out infinite;
}
@keyframes pulse {
  0%, 100% { transform: scale(1); box-shadow: 0 8px 24px var(--accent-glow); }
  50% { transform: scale(1.05); box-shadow: 0 12px 32px var(--accent-glow); }
}
.logo-text {
  background: linear-gradient(135deg, var(--accent), var(--secondary));
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
.header-actions {
  display: flex;
  align-items: center;
  gap: 12px;
}
.theme-toggle {
  width: 44px; height: 44px;
  border-radius: 12px;
  border: 1px solid var(--border-strong);
  background: var(--card);
  color: var(--fg);
  cursor: pointer;
  display: grid; place-items: center;
  font-size: 18px;
  transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  position: relative;
  overflow: hidden;
}
.theme-toggle:hover {
  transform: translateY(-2px) rotate(15deg);
  border-color: var(--accent);
  box-shadow: 0 8px 20px var(--accent-glow);
}
.theme-toggle i {
  transition: transform 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55);
}
[data-theme="dark"] .theme-toggle .icon-sun { display: block; }
[data-theme="dark"] .theme-toggle .icon-moon { display: none; }
[data-theme="light"] .theme-toggle .icon-sun { display: none; }
[data-theme="light"] .theme-toggle .icon-moon { display: block; }

.btn-external {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 10px 18px;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  color: white;
  border: none;
  border-radius: 12px;
  font-family: inherit;
  font-weight: 600;
  font-size: 14px;
  cursor: pointer;
  text-decoration: none;
  transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  box-shadow: 0 6px 18px var(--accent-glow);
  position: relative;
  overflow: hidden;
}
.btn-external::before {
  content: '';
  position: absolute;
  top: 50%; left: 50%;
  width: 0; height: 0;
  background: rgba(255,255,255,0.3);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: width 0.6s, height 0.6s;
}
.btn-external:hover::before { width: 300px; height: 300px; }
.btn-external:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 28px var(--accent-glow);
}
.btn-external i { transition: transform 0.3s; }
.btn-external:hover i { transform: translateX(-3px); }

/* ============== بخش جستجو ============== */
.search-hero {
  padding: 60px 32px 30px;
  text-align: center;
  max-width: 900px;
  margin: 0 auto;
  animation: fadeUp 0.9s 0.2s both cubic-bezier(0.16, 1, 0.3, 1);
}
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}
.hero-title {
  font-size: clamp(32px, 5vw, 56px);
  font-weight: 900;
  line-height: 1.2;
  margin-bottom: 16px;
  background: linear-gradient(135deg, var(--fg) 0%, var(--accent) 50%, var(--secondary) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
.hero-subtitle {
  color: var(--muted);
  font-size: 16px;
  margin-bottom: 32px;
  line-height: 1.7;
}
.search-box {
  position: relative;
  max-width: 700px;
  margin: 0 auto;
}
.search-input {
  width: 100%;
  padding: 18px 60px 18px 110px;
  font-family: inherit;
  font-size: 16px;
  background: var(--card);
  color: var(--fg);
  border: 2px solid var(--border-strong);
  border-radius: 18px;
  outline: none;
  transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  box-shadow: var(--shadow);
}
.search-input:focus {
  border-color: var(--accent);
  box-shadow: 0 0 0 4px var(--accent-glow), var(--shadow);
  transform: translateY(-2px);
}
.search-input::placeholder { color: var(--muted); }
.search-btn {
  position: absolute;
  left: 8px;
  top: 50%;
  transform: translateY(-50%);
  padding: 10px 22px;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  color: white;
  border: none;
  border-radius: 12px;
  font-family: inherit;
  font-weight: 600;
  font-size: 14px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 6px;
  transition: all 0.3s;
}
.search-btn:hover { box-shadow: 0 6px 16px var(--accent-glow); }
.search-btn:active { transform: translateY(-50%) scale(0.96); }
.search-icon {
  position: absolute;
  right: 22px;
  top: 50%;
  transform: translateY(-50%);
  color: var(--muted);
  font-size: 18px;
  pointer-events: none;
}
.search-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
  margin-top: 20px;
}
.search-tag {
  padding: 6px 14px;
  background: var(--card);
  border: 1px solid var(--border-strong);
  border-radius: 100px;
  color: var(--muted);
  font-size: 13px;
  cursor: pointer;
  transition: all 0.3s;
  font-family: inherit;
}
.search-tag:hover {
  color: var(--accent);
  border-color: var(--accent);
  transform: translateY(-2px);
}

/* ============== چیدمان اصلی ============== */
.layout {
  max-width: 1600px;
  margin: 0 auto;
  padding: 20px 32px 60px;
  display: grid;
  grid-template-columns: 1fr 380px;
  gap: 32px;
  align-items: start;
}

/* ============== شبکه تصاویر ============== */
.content-area {
  min-width: 0;
}
.results-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
  padding: 14px 20px;
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 14px;
  animation: fadeUp 0.6s both;
}
.results-title {
  font-size: 15px;
  font-weight: 600;
  color: var(--fg);
}
.results-title span { color: var(--accent); font-weight: 800; }
.results-count {
  font-size: 13px;
  color: var(--muted);
}

.image-grid {
  column-count: 3;
  column-gap: 16px;
}
.image-card {
  break-inside: avoid;
  margin-bottom: 16px;
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 16px;
  overflow: hidden;
  position: relative;
  transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  animation: cardIn 0.6s both;
}
@keyframes cardIn {
  from { opacity: 0; transform: translateY(30px) scale(0.96); }
  to { opacity: 1; transform: translateY(0) scale(1); }
}
.image-card:hover {
  transform: translateY(-6px);
  border-color: var(--accent);
  box-shadow: 0 20px 40px rgba(0,0,0,0.3), 0 0 30px var(--accent-glow);
}
.image-card.disliked-out {
  animation: cardOut 0.5s forwards;
}
@keyframes cardOut {
  to { opacity: 0; transform: scale(0.8) translateY(-20px); filter: blur(10px); }
}
.image-wrap {
  position: relative;
  overflow: hidden;
  background: var(--bg-2);
}
.image-wrap img {
  width: 100%;
  display: block;
  transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1);
}
.image-card:hover .image-wrap img { transform: scale(1.06); }
.image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.7) 0%, transparent 50%);
  opacity: 0;
  transition: opacity 0.4s;
  display: flex;
  align-items: flex-end;
  padding: 14px;
}
.image-card:hover .image-overlay { opacity: 1; }
.image-tag {
  color: white;
  font-size: 12px;
  background: rgba(255,255,255,0.15);
  backdrop-filter: blur(10px);
  padding: 4px 10px;
  border-radius: 100px;
  border: 1px solid rgba(255,255,255,0.2);
}
.image-actions {
  padding: 12px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 8px;
}
.action-btn {
  padding: 9px 6px;
  border: 1px solid var(--border-strong);
  background: var(--bg-2);
  color: var(--fg);
  border-radius: 10px;
  font-family: inherit;
  font-size: 12px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 5px;
  position: relative;
  overflow: hidden;
}
.action-btn i { font-size: 13px; }
.action-btn:hover { transform: translateY(-2px); }
.action-btn.save:hover {
  background: var(--accent);
  color: white;
  border-color: var(--accent);
  box-shadow: 0 6px 14px var(--accent-glow);
}
.action-btn.like:hover {
  background: var(--success);
  color: white;
  border-color: var(--success);
}
.action-btn.like.liked {
  background: var(--success);
  color: white;
  border-color: var(--success);
}
.action-btn.dislike:hover {
  background: var(--danger);
  color: white;
  border-color: var(--danger);
}

/* ============== صفحه‌بندی ============== */
.pagination {
  margin-top: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
}
.page-numbers {
  display: flex;
  align-items: center;
  gap: 8px;
  flex-wrap: wrap;
  justify-content: center;
}
.page-btn {
  min-width: 42px;
  height: 42px;
  padding: 0 14px;
  border: 1px solid var(--border-strong);
  background: var(--card);
  color: var(--fg);
  border-radius: 12px;
  font-family: inherit;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  display: flex;
  align-items: center;
  justify-content: center;
}
.page-btn:hover:not(:disabled) {
  border-color: var(--accent);
  color: var(--accent);
  transform: translateY(-2px);
}
.page-btn.active {
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  color: white;
  border-color: transparent;
  box-shadow: 0 6px 16px var(--accent-glow);
}
.page-btn:disabled {
  opacity: 0.4;
  cursor: not-allowed;
}
.page-dots {
  color: var(--muted);
  padding: 0 4px;
}
.page-nav-row {
  display: flex;
  gap: 12px;
}
.page-nav {
  padding: 10px 20px;
  border: 1px solid var(--border-strong);
  background: var(--card);
  color: var(--fg);
  border-radius: 12px;
  font-family: inherit;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s;
  display: flex;
  align-items: center;
  gap: 8px;
}
.page-nav:hover:not(:disabled) {
  background: var(--accent);
  color: white;
  border-color: var(--accent);
  transform: translateY(-2px);
  box-shadow: 0 8px 20px var(--accent-glow);
}
.page-nav:disabled {
  opacity: 0.4;
  cursor: not-allowed;
}

/* ============== ساید‌بار ============== */
.sidebar {
  display: flex;
  flex-direction: column;
  gap: 24px;
  position: sticky;
  top: 100px;
}
.widget {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 20px;
  overflow: hidden;
  box-shadow: var(--shadow);
  animation: fadeUp 0.8s 0.3s both cubic-bezier(0.16, 1, 0.3, 1);
  transition: all 0.4s;
}
.widget:hover {
  border-color: var(--border-strong);
  transform: translateY(-3px);
  box-shadow: 0 16px 40px rgba(0,0,0,0.15);
}
.widget-header {
  padding: 16px 20px;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  color: white;
  display: flex;
  align-items: center;
  gap: 12px;
}
.widget.secondary .widget-header {
  background: linear-gradient(135deg, var(--secondary), #8b7bff);
}
.widget-icon {
  width: 36px; height: 36px;
  background: rgba(255,255,255,0.2);
  border-radius: 10px;
  display: grid; place-items: center;
  font-size: 16px;
  backdrop-filter: blur(10px);
}
.widget-title {
  font-size: 15px;
  font-weight: 700;
}
.widget-body { padding: 16px; }

/* نمایش زنده 16:9 */
.live-preview {
  position: relative;
  width: 100%;
  aspect-ratio: 16 / 9;
  border-radius: 12px;
  overflow: hidden;
  background: var(--bg-2);
  border: 1px solid var(--border);
}
/* کانال گرافیک ترنج */
.channel-preview {
  background: linear-gradient(135deg, #1a1a35 0%, #2d1b4e 100%);
  display: flex;
  flex-direction: column;
}
.channel-preview::before {
  content: '';
  position: absolute;
  inset: 0;
  background: 
    radial-gradient(circle at 20% 30%, rgba(255,71,87,0.3), transparent 40%),
    radial-gradient(circle at 80% 70%, rgba(108,92,231,0.3), transparent 40%);
  animation: bgShift 8s ease-in-out infinite alternate;
}
@keyframes bgShift {
  to { transform: scale(1.2) rotate(20deg); }
}
.live-badge {
  position: absolute;
  top: 10px; right: 10px;
  background: var(--danger);
  color: white;
  padding: 3px 10px;
  border-radius: 100px;
  font-size: 11px;
  font-weight: 700;
  display: flex;
  align-items: center;
  gap: 5px;
  z-index: 3;
}
.live-dot {
  width: 7px; height: 7px;
  background: white;
  border-radius: 50%;
  animation: blink 1.2s infinite;
}
@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.3; }
}
.channel-content {
  position: relative;
  z-index: 2;
  padding: 14px;
  display: flex;
  flex-direction: column;
  height: 100%;
  color: white;
}
.channel-top {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}
.channel-avatar {
  width: 38px; height: 38px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--accent), var(--secondary));
  display: grid; place-items: center;
  font-weight: 800;
  font-size: 16px;
  border: 2px solid rgba(255,255,255,0.3);
}
.channel-name {
  font-size: 13px;
  font-weight: 700;
}
.channel-meta {
  font-size: 10px;
  opacity: 0.7;
}
.chat-stream {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 6px;
  overflow: hidden;
}
.chat-msg {
  background: rgba(255,255,255,0.1);
  backdrop-filter: blur(10px);
  padding: 6px 10px;
  border-radius: 10px;
  font-size: 11px;
  border: 1px solid rgba(255,255,255,0.1);
  animation: msgIn 0.5s both;
  max-width: 85%;
}
.chat-msg strong { color: var(--accent-2); margin-left: 4px; }
@keyframes msgIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}
.channel-stats {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
  font-size: 10px;
  opacity: 0.8;
}
.channel-stats span i { color: var(--accent-2); margin-left: 3px; }

/* پیش‌نمایش سایت */
.site-preview {
  background: linear-gradient(135deg, #f5f5f5 0%, #e8e8f0 100%);
  position: relative;
}
[data-theme="dark"] .site-preview {
  background: linear-gradient(135deg, #2a2a4a 0%, #1a1a35 100%);
}
.site-browser {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
}
.browser-bar {
  background: rgba(0,0,0,0.1);
  padding: 6px 8px;
  display: flex;
  align-items: center;
  gap: 4px;
}
[data-theme="dark"] .browser-bar { background: rgba(255,255,255,0.05); }
.browser-dot {
  width: 7px; height: 7px;
  border-radius: 50%;
}
.browser-dot.r { background: #ff5f57; }
.browser-dot.y { background: #ffbd2e; }
.browser-dot.g { background: #28ca42; }
.browser-url {
  flex: 1;
  background: rgba(255,255,255,0.5);
  border-radius: 6px;
  padding: 3px 8px;
  font-size: 9px;
  color: var(--muted);
  margin-right: 6px;
  text-align: center;
}
[data-theme="dark"] .browser-url { background: rgba(255,255,255,0.1); color: var(--muted); }
.site-content {
  flex: 1;
  padding: 12px;
  display: flex;
  flex-direction: column;
  gap: 8px;
  position: relative;
  overflow: hidden;
}
.site-hero {
  background: linear-gradient(135deg, var(--accent), var(--secondary));
  border-radius: 8px;
  padding: 10px;
  color: white;
  display: flex;
  align-items: center;
  gap: 8px;
  animation: shimmer 3s ease-in-out infinite;
}
@keyframes shimmer {
  0%, 100% { box-shadow: 0 0 0 rgba(255,71,87,0); }
  50% { box-shadow: 0 0 20px rgba(255,71,87,0.5); }
}
.site-hero-logo {
  width: 22px; height: 22px;
  background: rgba(255,255,255,0.2);
  border-radius: 6px;
  display: grid; place-items: center;
  font-size: 11px;
}
.site-hero-text {
  font-size: 11px;
  font-weight: 800;
}
.site-skeleton {
  height: 8px;
  background: linear-gradient(90deg, rgba(0,0,0,0.06) 25%, rgba(0,0,0,0.12) 50%, rgba(0,0,0,0.06) 75%);
  background-size: 200% 100%;
  animation: skeleton 1.8s infinite;
  border-radius: 4px;
}
[data-theme="dark"] .site-skeleton {
  background: linear-gradient(90deg, rgba(255,255,255,0.05) 25%, rgba(255,255,255,0.12) 50%, rgba(255,255,255,0.05) 75%);
  background-size: 200% 100%;
}
@keyframes skeleton {
  to { background-position: -200% 0; }
}
.site-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6px;
  margin-top: 2px;
}
.site-grid-item {
  height: 30px;
  background: rgba(0,0,0,0.05);
  border-radius: 6px;
}
[data-theme="dark"] .site-grid-item { background: rgba(255,255,255,0.05); }
.site-cta {
  margin-top: auto;
  height: 18px;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  border-radius: 6px;
  animation: pulse 2.5s infinite;
}

.widget-action {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  padding: 12px;
  margin-top: 14px;
  background: var(--bg-2);
  color: var(--fg);
  border: 1px solid var(--border-strong);
  border-radius: 12px;
  font-family: inherit;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  text-decoration: none;
  transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  position: relative;
  overflow: hidden;
}
.widget-action::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  transform: translateY(100%);
  transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  z-index: 0;
}
.widget-action:hover::before { transform: translateY(0); }
.widget-action:hover { color: white; border-color: transparent; }
.widget-action span, .widget-action i { position: relative; z-index: 1; }

/* ============== حالت خالی ============== */
.empty-state {
  grid-column: 1 / -1;
  text-align: center;
  padding: 60px 20px;
  color: var(--muted);
}
.empty-state i {
  font-size: 60px;
  margin-bottom: 16px;
  background: linear-gradient(135deg, var(--accent), var(--secondary));
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
.empty-state h3 {
  color: var(--fg);
  font-size: 20px;
  margin-bottom: 8px;
}
.empty-state p { font-size: 14px; }

/* ============== لودینگ ============== */
.loading-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.loading-card {
  background: var(--card);
  border-radius: 16px;
  overflow: hidden;
  border: 1px solid var(--border);
}
.loading-img {
  width: 100%;
  aspect-ratio: 3/4;
  background: linear-gradient(90deg, var(--bg-2) 25%, var(--card-hover) 50%, var(--bg-2) 75%);
  background-size: 200% 100%;
  animation: skeleton 1.5s infinite;
}

/* ============== توست ============== */
.toast-container {
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1000;
  display: flex;
  flex-direction: column;
  gap: 10px;
  align-items: center;
  pointer-events: none;
}
.toast {
  background: var(--card);
  border: 1px solid var(--border-strong);
  color: var(--fg);
  padding: 12px 22px;
  border-radius: 12px;
  font-size: 14px;
  font-weight: 600;
  box-shadow: var(--shadow);
  display: flex;
  align-items: center;
  gap: 10px;
  animation: toastIn 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  backdrop-filter: blur(20px);
  min-width: 220px;
  justify-content: center;
  pointer-events: auto;
}
.toast.success { border-color: var(--success); }
.toast.success i { color: var(--success); }
.toast.error { border-color: var(--danger); }
.toast.error i { color: var(--danger); }
.toast.info i { color: var(--accent); }
.toast.hide { animation: toastOut 0.4s forwards; }
@keyframes toastIn {
  from { opacity: 0; transform: translateY(20px) scale(0.9); }
  to { opacity: 1; transform: translateY(0) scale(1); }
}
@keyframes toastOut {
  to { opacity: 0; transform: translateY(20px) scale(0.9); }
}

/* ============== فوتر ============== */
.footer {
  text-align: center;
  padding: 30px 20px;
  color: var(--muted);
  font-size: 13px;
  border-top: 1px solid var(--border);
  margin-top: 40px;
}
.footer a { color: var(--accent); text-decoration: none; }

/* ============== ریسپانسیو ============== */
@media (max-width: 1200px) {
  .layout { grid-template-columns: 1fr 320px; gap: 24px; }
  .image-grid { column-count: 2; }
}
@media (max-width: 900px) {
  .layout { grid-template-columns: 1fr; }
  .sidebar { position: static; flex-direction: row; flex-wrap: wrap; }
  .widget { flex: 1 1 280px; }
  .search-hero { padding: 40px 20px 20px; }
  .header { padding: 14px 20px; }
  .layout { padding: 20px; }
}
@media (max-width: 600px) {
  .image-grid { column-count: 1; }
  .loading-grid { grid-template-columns: 1fr 1fr; }
  .header-inner { flex-wrap: wrap; }
  .btn-external span { display: none; }
  .btn-external { padding: 10px 14px; }
  .search-input { padding: 16px 14px 16px 90px; font-size: 14px; }
  .search-btn { padding: 8px 14px; font-size: 13px; }
  .search-btn span { display: none; }
  .hero-title { font-size: 30px; }
  .page-btn { min-width: 38px; height: 38px; font-size: 13px; }
  .page-nav { padding: 8px 14px; font-size: 13px; }
  .sidebar { flex-direction: column; }
}

/* اسکرول‌بار */
::-webkit-scrollbar { width: 10px; height: 10px; }
::-webkit-scrollbar-track { background: var(--bg); }
::-webkit-scrollbar-thumb { background: var(--border-strong); border-radius: 10px; }
::-webkit-scrollbar-thumb:hover { background: var(--accent); }

::selection { background: var(--accent); color: white; }

/* Reduced motion */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
</style>
</head>
<body>

<!-- پس‌زمینه اتمسفریک -->
<div class="blob blob-1"></div>
<div class="blob blob-2"></div>

<!-- هدر -->
<header class="header">
  <div class="header-inner">
    <a href="#" class="logo">
      <div class="logo-icon"><i class="fa-solid fa-bolt"></i></div>
      <span class="logo-text">گرافیت پلاس</span>
    </a>
    <div class="header-actions">
      <button class="theme-toggle" id="themeToggle" aria-label="تغییر تم">
        <i class="fa-solid fa-sun icon-sun"></i>
        <i class="fa-solid fa-moon icon-moon"></i>
      </button>
      <a href="https://graphit-plus.ir" target="_blank" rel="noopener" class="btn-external">
        <i class="fa-solid fa-arrow-up-right-from-square"></i>
        <span>رفتن به سایت گرافیت پلاس</span>
      </a>
    </div>
  </div>
</header>

<!-- بخش جستجو -->
<section class="search-hero">
  <h1 class="hero-title">جستجوی هوشمند تصاویر</h1>
  <p class="hero-subtitle">هرچه می‌خواهی جستجو کن، هزاران تصویر باکیفیت در انتظار توست</p>
  <div class="search-box">
    <form id="searchForm">
      <i class="fa-solid fa-magnifying-glass search-icon"></i>
      <input type="text" id="searchInput" class="search-input" placeholder="مثلاً: طراحی، طبیعت، هنر، معماری..." autocomplete="off">
      <button type="submit" class="search-btn">
        <i class="fa-solid fa-search"></i>
        <span>جستجو</span>
      </button>
    </form>
    <div class="search-tags">
      <button class="search-tag" data-tag="طراحی">طراحی</button>
      <button class="search-tag" data-tag="طبیعت">طبیعت</button>
      <button class="search-tag" data-tag="معماری">معماری</button>
      <button class="search-tag" data-tag="هنر">هنر</button>
      <button class="search-tag" data-tag="تکنولوژی">تکنولوژی</button>
      <button class="search-tag" data-tag="سفر">سفر</button>
    </div>
  </div>
</section>

<!-- چیدمان اصلی -->
<div class="layout">
  <!-- محتوای اصلی -->
  <main class="content-area">
    <div class="results-header">
      <div class="results-title">نتایج جستجو برای: <span id="currentQuery">طراحی</span></div>
      <div class="results-count" id="resultsCount">۰ تصویر</div>
    </div>
    
    <div id="gridContainer">
      <div class="image-grid" id="imageGrid"></div>
    </div>
    
    <!-- صفحه‌بندی -->
    <div class="pagination" id="pagination" style="display:none;">
      <div class="page-numbers" id="pageNumbers"></div>
      <div class="page-nav-row">
        <button class="page-nav" id="prevBtn" disabled>
          <i class="fa-solid fa-angle-right"></i>
          <span>صفحه قبلی</span>
        </button>
        <button class="page-nav" id="nextBtn">
          <span>صفحه بعدی</span>
          <i class="fa-solid fa-angle-left"></i>
        </button>
      </div>
    </div>
  </main>

  <!-- ساید‌بار -->
  <aside class="sidebar">
    <!-- ویجت کانال گرافیک ترنج -->
    <div class="widget">
      <div class="widget-header">
        <div class="widget-icon"><i class="fa-brands fa-telegram"></i></div>
        <div class="widget-title">کانال گرافیک ترنج</div>
      </div>
      <div class="widget-body">
        <div class="live-preview channel-preview">
          <div class="live-badge">
            <span class="live-dot"></span>
            <span>زنده</span>
          </div>
          <div class="channel-content">
            <div class="channel-top">
              <div class="channel-avatar">گ</div>
              <div>
                <div class="channel-name">گرافیک ترنج</div>
                <div class="channel-meta">۲٬۴۵۰ عضو آنلاین</div>
              </div>
            </div>
            <div class="chat-stream" id="chatStream">
              <div class="chat-msg"><strong>ترنج:</strong> قالب جدید گرافیکی منتشر شد!</div>
              <div class="chat-msg"><strong>ترنج:</strong> آموزش طراحی لوگو فردا ساعت ۱۸</div>
              <div class="chat-msg"><strong>ترنج:</strong> پک رایگان آیکون دانلود کنید</div>
            </div>
            <div class="channel-stats">
              <span><i class="fa-solid fa-users"></i> ۲٬۴۵۰ آنلاین</span>
              <span><i class="fa-solid fa-eye"></i> ۱۲٬۳۰۰ بازدید</span>
            </div>
          </div>
        </div>
        <a href="https://eitaa.com/graphic_toranj" target="_blank" rel="noopener" class="widget-action">
          <i class="fa-solid fa-right-to-bracket"></i>
          <span>ورود به کانال</span>
        </a>
      </div>
    </div>

    <!-- ویجت سایت گرافیت پلاس -->
    <div class="widget secondary">
      <div class="widget-header">
        <div class="widget-icon"><i class="fa-solid fa-globe"></i></div>
        <div class="widget-title">سایت گرافیت پلاس</div>
      </div>
      <div class="widget-body">
        <div class="live-preview site-preview">
          <div class="site-browser">
            <div class="browser-bar">
              <span class="browser-dot r"></span>
              <span class="browser-dot y"></span>
              <span class="browser-dot g"></span>
              <div class="browser-url">graphit-plus.ir</div>
            </div>
            <div class="site-content">
              <div class="site-hero">
                <div class="site-hero-logo"><i class="fa-solid fa-bolt"></i></div>
                <div class="site-hero-text">گرافیت پلاس</div>
              </div>
              <div class="site-skeleton" style="width: 80%;"></div>
              <div class="site-skeleton" style="width: 60%;"></div>
              <div class="site-grid">
                <div class="site-grid-item"></div>
                <div class="site-grid-item"></div>
              </div>
              <div class="site-cta"></div>
            </div>
          </div>
        </div>
        <a href="https://graphit-plus.ir" target="_blank" rel="noopener" class="widget-action">
          <i class="fa-solid fa-arrow-up-right-from-square"></i>
          <span>ورود به سایت</span>
        </a>
      </div>
    </div>
  </aside>
</div>

<!-- فوتر -->
<footer class="footer">
  طراحی شده با ❤️ توسط تیم گرافیت پلاس — تمامی حقوق محفوظ است
</footer>

<!-- توست‌ها -->
<div class="toast-container" id="toastContainer"></div>

<script>
/* ============== مدیریت وضعیت ============== */
const state = {
  query: 'طراحی',
  page: 1,
  perPage: 18,
  totalPages: 12,
  dislikedSeeds: new Set(),   // seed های نامناسب
  likedImages: new Set(),     // id تصاویر پسندیده‌شده
  isLoading: false
};

// دیکشنری برای تبدیل اعداد انگلیسی به فارسی
const faDigits = ['۰','۱','۲','۳','۴','۵','۶','۷','۸','۹'];
const toFa = (n) => String(n).replace(/\d/g, d => faDigits[d]);

// تابع هش برای تولید seed پایدار از روی کوئری
function hashString(str) {
  let hash = 5381;
  for (let i = 0; i < str.length; i++) {
    hash = ((hash << 5) + hash) + str.charCodeAt(i);
    hash = hash & 0xffffffff;
  }
  return Math.abs(hash);
}

// بررسی فیلتر شدن seed (شبیه‌سازی "نمایش ندادن سبک مشابه")
function isFiltered(seed) {
  for (const d of state.dislikedSeeds) {
    if (Math.abs(d - seed) <= 4) return true; // فیلتر seedهای نزدیک
  }
  return false;
}

// تولید لیست تصاویر برای صفحه فعلی
function generateImages(query, page) {
  const baseSeed = hashString(query);
  const startIndex = (page - 1) * state.perPage;
  const images = [];
  const heights = [400, 500, 600, 700, 520, 640, 480, 580];
  let attempts = 0;
  let offset = 0;
  
  while (images.length < state.perPage && attempts < state.perPage * 20) {
    const seed = baseSeed + startIndex + offset;
    if (!isFiltered(seed)) {
      const h = heights[seed % heights.length];
      images.push({
        id: `${query}-${seed}-${offset}`,
        seed: seed,
        height: h,
        thumb: `https://picsum.photos/seed/${seed}/400/${h}`,
        full: `https://picsum.photos/seed/${seed}/800/${h * 2}`
      });
    }
    offset++;
    attempts++;
  }
  return images;
}

/* ============== رندر گرید ============== */
function renderGrid() {
  const grid = document.getElementById('imageGrid');
  const container = document.getElementById('gridContainer');
  
  if (state.isLoading) return;
  state.isLoading = true;
  
  // نمایش لودینگ
  grid.style.display = 'none';
  let loadingEl = container.querySelector('.loading-grid');
  if (!loadingEl) {
    loadingEl = document.createElement('div');
    loadingEl.className = 'loading-grid';
    loadingEl.innerHTML = Array(9).fill(0).map(() => 
      `<div class="loading-card"><div class="loading-img"></div></div>`
    ).join('');
    container.appendChild(loadingEl);
  }
  loadingEl.style.display = 'grid';
  
  setTimeout(() => {
    const images = generateImages(state.query, state.page);
    loadingEl.style.display = 'none';
    grid.style.display = 'block';
    
    if (images.length === 0) {
      grid.innerHTML = `
        <div class="empty-state">
          <i class="fa-solid fa-images"></i>
          <h3>تصویری یافت نشد</h3>
          <p>با فیلترهای فعلی تصویری برای نمایش وجود ندارد.</p>
        </div>
      `;
    } else {
      grid.innerHTML = images.map((img, i) => {
        const liked = state.likedImages.has(img.id) ? 'liked' : '';
        return `
          <article class="image-card" data-id="${img.id}" data-seed="${img.seed}" data-full="${img.full}" style="animation-delay: ${i * 0.04}s">
            <div class="image-wrap">
              <img src="${img.thumb}" alt="نتیجه جستجو برای ${state.query}" loading="lazy">
              <div class="image-overlay">
                <span class="image-tag">#${state.query}</span>
              </div>
            </div>
            <div class="image-actions">
              <button class="action-btn save" data-action="save">
                <i class="fa-solid fa-download"></i>
                <span>ذخیره</span>
              </button>
              <button class="action-btn like ${liked}" data-action="like">
                <i class="fa-solid fa-heart"></i>
                <span>پسند</span>
              </button>
              <button class="action-btn dislike" data-action="dislike">
                <i class="fa-solid fa-thumbs-down"></i>
                <span>نپسند</span>
              </button>
            </div>
          </article>
        `;
      }).join('');
    }
    
    document.getElementById('resultsCount').textContent = toFa(images.length) + ' تصویر';
    document.getElementById('currentQuery').textContent = state.query;
    
    state.isLoading = false;
    renderPagination();
  }, 600);
}

/* ============== صفحه‌بندی ============== */
function renderPagination() {
  const pag = document.getElementById('pagination');
  const numbers = document.getElementById('pageNumbers');
  const prevBtn = document.getElementById('prevBtn');
  const nextBtn = document.getElementById('nextBtn');
  
  pag.style.display = 'flex';
  
  const current = state.page;
  const last = state.totalPages;
  let pages = [];
  
  // صفحه 1 همیشه
  pages.push(1);
  
  // اگر فاصله بین 1 و current-1 بیشتر از 1 باشد، ... بگذار
  if (current - 1 > 2) pages.push('...');
  
  // صفحات قبلی، فعلی، بعدی
  for (let p = current - 1; p <= current + 1; p++) {
    if (p > 1 && p < last) pages.push(p);
  }
  
  // اگر فاصله بین current+1 و last بیشتر از 1 باشد، ... بگذار
  if (last - current > 2) pages.push('...');
  
  // صفحه آخر همیشه (اگر بیشتر از 1 باشد)
  if (last > 1) pages.push(last);
  
  // حذف تکراری‌ها
  pages = [...new Set(pages)];
  
  numbers.innerHTML = pages.map(p => {
    if (p === '...') return `<span class="page-dots">...</span>`;
    return `<button class="page-btn ${p === current ? 'active' : ''}" data-page="${p}">${toFa(p)}</button>`;
  }).join('');
  
  prevBtn.disabled = current === 1;
  nextBtn.disabled = current === last;
  
  // اتصال رویدادها
  numbers.querySelectorAll('.page-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      const p = parseInt(btn.dataset.page);
      if (p !== state.page) {
        state.page = p;
        renderGrid();
        window.scrollTo({ top: document.querySelector('.layout').offsetTop - 80, behavior: 'smooth' });
      }
    });
  });
}

/* ============== اکشن‌های کارت ============== */
document.getElementById('imageGrid').addEventListener('click', async (e) => {
  const btn = e.target.closest('.action-btn');
  if (!btn) return;
  
  const card = btn.closest('.image-card');
  const action = btn.dataset.action;
  const id = card.dataset.id;
  const seed = parseInt(card.dataset.seed);
  const fullUrl = card.dataset.full;
  
  if (action === 'save') {
    // دانلود تصویر
    showToast('در حال دانلود تصویر...', 'info');
    try {
      const response = await fetch(fullUrl);
      const blob = await response.blob();
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = `graphit-plus-${state.query}-${seed}.jpg`;
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      URL.revokeObjectURL(url);
      showToast('تصویر با موفقیت ذخیره شد', 'success');
    } catch (err) {
      // در صورت خطای CORS، در تب جدید باز کن
      window.open(fullUrl, '_blank');
      showToast('تصویر در تب جدید باز شد', 'info');
    }
  } else if (action === 'like') {
    if (state.likedImages.has(id)) {
      state.likedImages.delete(id);
      btn.classList.remove('liked');
      showToast('از پسندها حذف شد', 'info');
    } else {
      state.likedImages.add(id);
      btn.classList.add('liked');
      showToast('به پسندها اضافه شد', 'success');
    }
    // انیمیشن ضربان قلب
    btn.style.transform = 'scale(1.2)';
    setTimeout(() => btn.style.transform = '', 200);
  } else if (action === 'dislike') {
    // اضافه کردن به لیست نامناسب (و seedهای اطراف برای شبیه‌سازی سبک مشابه)
    state.dislikedSeeds.add(seed);
    showToast('تصویر حذف شد و سبک مشابه نمایش داده نخواهد شد', 'success');
    
    // انیمیشن خروج
    card.classList.add('disliked-out');
    setTimeout(() => {
      card.remove();
      // بررسی تعداد باقی‌مانده
      const remaining = document.querySelectorAll('.image-card').length;
      const countEl = document.getElementById('resultsCount');
      countEl.textContent = toFa(remaining) + ' تصویر';
      if (remaining === 0) {
        renderGrid(); // بارگذاری مجدد در صورت خالی شدن
      }
    }, 500);
  }
});

/* ============== جستجو ============== */
document.getElementById('searchForm').addEventListener('submit', (e) => {
  e.preventDefault();
  const value = document.getElementById('searchInput').value.trim();
  if (!value) return;
  performSearch(value);
});

document.querySelectorAll('.search-tag').forEach(tag => {
  tag.addEventListener('click', () => {
    const value = tag.dataset.tag;
    document.getElementById('searchInput').value = value;
    performSearch(value);
  });
});

function performSearch(query) {
  state.query = query;
  state.page = 1;
  state.dislikedSeeds.clear(); // ریست فیلترها برای جستجوی جدید
  renderGrid();
}

/* ============== دکمه‌های قبلی/بعدی ============== */
document.getElementById('prevBtn').addEventListener('click', () => {
  if (state.page > 1 && !state.isLoading) {
    state.page--;
    renderGrid();
    window.scrollTo({ top: document.querySelector('.layout').offsetTop - 80, behavior: 'smooth' });
  }
});
document.getElementById('nextBtn').addEventListener('click', () => {
  if (state.page < state.totalPages && !state.isLoading) {
    state.page++;
    renderGrid();
    window.scrollTo({ top: document.querySelector('.layout').offsetTop - 80, behavior: 'smooth' });
  }
});

/* ============== تم ============== */
const themeToggle = document.getElementById('themeToggle');
themeToggle.addEventListener('click', () => {
  const html = document.documentElement;
  const current = html.getAttribute('data-theme');
  const next = current === 'dark' ? 'light' : 'dark';
  html.setAttribute('data-theme', next);
  localStorage.setItem('theme', next);
  showToast(next === 'dark' ? 'تم تیره فعال شد' : 'تم روشن فعال شد', 'info');
});

// بارگذاری تم ذخیره‌شده
const savedTheme = localStorage.getItem('theme');
if (savedTheme) document.documentElement.setAttribute('data-theme', savedTheme);

/* ============== توست ============== */
function showToast(message, type = 'info') {
  const container = document.getElementById('toastContainer');
  const toast = document.createElement('div');
  toast.className = `toast ${type}`;
  const icon = type === 'success' ? 'circle-check' : type === 'error' ? 'circle-xmark' : 'circle-info';
  toast.innerHTML = `<i class="fa-solid fa-${icon}"></i><span>${message}</span>`;
  container.appendChild(toast);
  setTimeout(() => {
    toast.classList.add('hide');
    setTimeout(() => toast.remove(), 400);
  }, 2800);
}

/* ============== انیمیشن پیام‌های کانال ============== */
const channelMessages = [
  'قالب جدید گرافیکی منتشر شد!',
  'آموزش طراحی لوگو فردا ساعت ۱۸',
  'پک رایگان آیکون دانلود کنید',
  'نکته رنگ‌شناسی: ترکیب طلایی و مشکی',
  'مسابقه بهترین طراحی هفته آینده',
  'فایل لایه‌باز پوستر جدید اضافه شد',
  'ترفند فتوشاپ: ماسک‌های هیبریدی',
  'الهام از طراحی‌های مینیمال اسکاندیناوی'
];
let msgIndex = 3;
setInterval(() => {
  const stream = document.getElementById('chatStream');
  if (!stream) return;
  const msg = document.createElement('div');
  msg.className = 'chat-msg';
  msg.innerHTML = `<strong>ترنج:</strong> ${channelMessages[msgIndex % channelMessages.length]}`;
  stream.appendChild(msg);
  if (stream.children.length > 3) stream.removeChild(stream.firstChild);
  msgIndex++;
}, 3500);

/* ============== بارگذاری اولیه ============== */
document.getElementById('searchInput').value = state.query;
renderGrid();
</script>

</body>
</html>
