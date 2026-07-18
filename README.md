<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>استودیو پرامپت | گالری و ساخت پرامپت</title>
    <link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;500;700;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #050505;
            --text-color: #39FF14;
            --accent-glow: #39FF14;
            --glass-bg: rgba(10, 10, 10, 0.6);
            --glass-border: rgba(57, 255, 20, 0.3);
            --input-bg: rgba(0, 0, 0, 0.7);
            --particle-color: 57, 255, 20;
            --danger-color: #ff4c4c;
        }

        .theme-light {
            --bg-color: #FDFEFE;
            --text-color: #047857;
            --accent-glow: #10B981;
            --glass-bg: rgba(255, 255, 255, 0.6);
            --glass-border: rgba(16, 185, 129, 0.4);
            --input-bg: rgba(255, 255, 255, 0.8);
            --particle-color: 16, 185, 129;
            --danger-color: #e53e3e;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            font-family: 'Vazirmatn', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            min-height: 100vh;
            overflow-x: hidden;
            transition: background-color 0.5s, color 0.5s;
        }

        #particle-canvas {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            z-index: -1; pointer-events: none;
        }

        .neon-text { text-shadow: 0 0 5px var(--accent-glow), 0 0 10px var(--accent-glow), 0 0 20px var(--accent-glow); }
        .hidden { display: none !important; }

        /* --- Layout & Containers --- */
        .view-container {
            max-width: 800px;
            margin: 0 auto;
            padding: 40px 20px 100px 20px; /* padding bottom for floating btns */
            position: relative;
            z-index: 1;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

        /* --- Header --- */
        header { text-align: center; margin-bottom: 40px; position: relative; }
        h1 { font-size: 3rem; font-weight: 900; letter-spacing: 2px; margin-bottom: 10px; }
        .subtitle { font-size: 1rem; font-weight: 300; opacity: 0.9; }

        .theme-toggle, .back-btn {
            position: absolute; top: 0; left: 0;
            background: var(--glass-bg); border: 1px solid var(--glass-border);
            color: var(--text-color); padding: 8px 16px; border-radius: 20px;
            cursor: pointer; backdrop-filter: blur(10px); font-family: 'Vazirmatn', sans-serif;
            transition: all 0.3s; text-decoration: none; display: inline-block;
        }
        .theme-toggle:hover, .back-btn:hover { box-shadow: 0 0 15px var(--accent-glow); }

        /* --- Glass Cards --- */
        .card {
            background: var(--glass-bg); backdrop-filter: blur(15px); -webkit-backdrop-filter: blur(15px);
            border: 1px solid var(--glass-border); border-radius: 20px; padding: 25px;
            margin-bottom: 25px; box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3); transition: all 0.3s ease;
        }
        .card:hover { border-color: var(--accent-glow); box-shadow: 0 0 20px rgba(var(--particle-color), 0.2); }

        /* --- Forms --- */
        label { display: block; margin-bottom: 10px; font-weight: 700; font-size: 1.1rem; }
        input, select, textarea {
            width: 100%; padding: 12px 15px; background: var(--input-bg);
            border: 1px solid var(--glass-border); border-radius: 12px;
            color: var(--text-color); font-family: 'Vazirmatn', sans-serif;
            font-size: 1rem; outline: none; transition: all 0.3s;
        }
        input:focus, select:focus, textarea:focus { border-color: var(--accent-glow); box-shadow: 0 0 10px rgba(var(--particle-color), 0.4); }
        select { cursor: pointer; appearance: none; background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%2339FF14' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3e%3cpolyline points='6 9 12 15 18 9'%3e%3c/polyline%3e%3c/svg%3e"); background-repeat: no-repeat; background-position: left 1rem center; background-size: 1em; padding-left: 40px; }
        .theme-light select { background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%2310B981' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3e%3cpolyline points='6 9 12 15 18 9'%3e%3c/polyline%3e%3c/svg%3e"); }
        textarea { resize: vertical; min-height: 80px; }

        /* --- Radio Buttons --- */
        .radio-group { display: flex; gap: 15px; }
        .radio-group label { flex: 1; display: flex; align-items: center; justify-content: center; padding: 12px; background: var(--input-bg); border: 1px solid var(--glass-border); border-radius: 12px; cursor: pointer; transition: all 0.3s; font-weight: 500; margin-bottom: 0; }
        .radio-group input[type="radio"] { width: auto; margin-left: 8px; accent-color: var(--accent-glow); }
        .radio-group input[type="radio"]:checked + span { color: var(--accent-glow); font-weight: 800; }
        .radio-group label:has(input:checked) { border-color: var(--accent-glow); box-shadow: 0 0 15px rgba(var(--particle-color), 0.3); background: rgba(var(--particle-color), 0.1); }

        /* --- Buttons --- */
        .btn { width: 100%; padding: 16px; border: none; border-radius: 12px; font-family: 'Vazirmatn', sans-serif; font-size: 1.2rem; font-weight: 700; cursor: pointer; transition: all 0.3s; text-transform: uppercase; letter-spacing: 1px; text-align: center; }
        .btn-generate { background: var(--accent-glow); color: #000; box-shadow: 0 0 20px rgba(var(--particle-color), 0.5); }
        .btn-generate:hover { transform: translateY(-2px); box-shadow: 0 0 30px rgba(var(--particle-color), 0.8); }
        .btn-generate:disabled { opacity: 0.6; cursor: not-allowed; }
        .btn-copy { background: transparent; color: var(--text-color); border: 2px solid var(--accent-glow); }
        .btn-copy:hover { background: rgba(var(--particle-color), 0.1); }

        /* --- Floating Buttons --- */
        .float-btn {
            position: fixed; bottom: 30px; left: 30px; z-index: 100;
            background: var(--glass-bg); backdrop-filter: blur(10px);
            border: 1px solid var(--accent-glow); color: var(--text-color);
            padding: 12px 24px; border-radius: 30px; cursor: pointer;
            font-family: 'Vazirmatn', sans-serif; font-weight: 700;
            box-shadow: 0 0 20px rgba(var(--particle-color), 0.4);
            transition: all 0.3s; display: flex; align-items: center; gap: 8px;
        }
        .float-btn:hover { transform: scale(1.05); }

        /* --- Gallery --- */
        #gallery-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px; margin-top: 20px;
        }
        .gallery-card {
            background: var(--glass-bg); border: 1px solid var(--glass-border);
            border-radius: 15px; overflow: hidden; transition: all 0.3s;
        }
        .gallery-card:hover { transform: translateY(-5px); box-shadow: 0 10px 30px rgba(var(--particle-color), 0.2); }
        .gallery-card img { width: 100%; height: 200px; object-fit: cover; border-bottom: 1px solid var(--glass-border); }
        .gallery-card .content { padding: 15px; }
        .gallery-card .prompt-text { font-size: 0.9rem; color: #aaa; height: 80px; overflow: hidden; position: relative; margin-bottom: 10px; }
        .theme-light .gallery-card .prompt-text { color: #444; }
        .gallery-card .copy-gallery-btn {
            background: rgba(var(--particle-color), 0.2); color: var(--text-color);
            border: 1px solid var(--glass-border); padding: 8px; width: 100%;
            border-radius: 8px; cursor: pointer; transition: 0.3s; font-family: 'Vazirmatn';
        }
        .gallery-card .copy-gallery-btn:hover { background: rgba(var(--particle-color), 0.4); }

        /* --- Footer Blink Button --- */
        .footer-submit-container {
            position: fixed; bottom: 0; left: 0; width: 100%; z-index: 90;
            background: linear-gradient(to top, var(--bg-color) 60%, transparent);
            padding: 30px 20px 20px 20px; text-align: center;
        }
        .blink-btn {
            background: var(--accent-glow); color: #000; border: none;
            padding: 15px 40px; font-size: 1.1rem; font-weight: 800;
            border-radius: 50px; cursor: pointer; font-family: 'Vazirmatn';
            box-shadow: 0 0 20px var(--accent-glow);
            animation: blink 1.5s infinite alternate;
        }
        @keyframes blink {
            0% { opacity: 0.7; transform: scale(1); box-shadow: 0 0 15px var(--accent-glow); }
            100% { opacity: 1; transform: scale(1.05); box-shadow: 0 0 35px var(--accent-glow); }
        }

        /* --- Modal --- */
        .modal-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.8); backdrop-filter: blur(5px);
            z-index: 200; display: flex; align-items: center; justify-content: center;
            padding: 20px; animation: fadeIn 0.3s;
        }
        .modal-content {
            max-width: 500px; width: 100%; background: var(--bg-color);
            border: 1px solid var(--accent-glow); border-radius: 20px;
            padding: 30px; position: relative; box-shadow: 0 0 40px rgba(var(--particle-color), 0.3);
        }
        .modal-close {
            position: absolute; top: 15px; left: 15px; background: none;
            border: none; color: var(--danger-color); font-size: 2rem;
            cursor: pointer; font-weight: bold;
        }
        .file-upload-area {
            border: 2px dashed var(--glass-border); padding: 30px;
            text-align: center; border-radius: 12px; cursor: pointer;
            transition: all 0.3s; margin-bottom: 15px;
        }
        .file-upload-area:hover { border-color: var(--accent-glow); background: rgba(var(--particle-color), 0.05); }
        .file-upload-area input[type="file"] { display: none; }
        .file-upload-area i { font-size: 2rem; color: var(--accent-glow); display: block; margin-bottom: 10px; }
        
        #promptOutput { white-space: pre-wrap; font-family: 'Courier New', monospace; line-height: 1.8; margin-bottom: 15px; color: #ccc; }
        .theme-light #promptOutput { color: #333; }
        #copyMsg { text-align: center; color: var(--accent-glow); margin-top: 10px; font-weight: bold; }

        @keyframes pulse { 0% { opacity: 0.6; } 50% { opacity: 1; } 100% { opacity: 0.6; } }
        .loading { animation: pulse 1.5s infinite; }
    </style>
</head>
<body>
    <canvas id="particle-canvas"></canvas>

    <!-- ========== ویو اصلی: استودیو ساخت پرامپت ========== -->
    <div id="main-view" class="view-container">
        <header>
            <button class="theme-toggle" onclick="toggleTheme()">تغییر تم 🌓</button>
            <h1 class="neon-text">استودیو پرامپت</h1>
            <p class="subtitle">تصویر رویایی خود را در چند مرحله به پرامپتی حرفه‌ای تبدیل کنید</p>
        </header>

        <div class="card">
            <label>۱. ایده یا موضوع اصلی تصویر</label>
            <input type="text" id="mainIdea" placeholder="مثال: یک گربه فضانورد در حال شناختن کهکشان">
            <label style="margin-top: 20px;">۲. توضیحات اضافه برای بهتر شدن پرامپت</label>
            <textarea id="details" placeholder="مثال: گربه باید نارنجی باشد و کهکشان ها رنگ های گرم داشته باشند"></textarea>
        </div>

        <div class="card">
            <label>۳. سبک تصویر (Style)</label>
            <select id="style">
                <option value="Photorealistic">فتورئال (Photorealistic)</option>
                <option value="Cinematic">سینمایی (Cinematic)</option>
                <option value="Anime">انیمه (Anime)</option>
                <option value="3D Render">رندر سه‌بعدی (3D Render)</option>
                <option value="Oil Painting">نقاشی رنگ روغن (Oil Painting)</option>
                <option value="Watercolor">آبرنگ (Watercolor)</option>
                <option value="Cyberpunk">سایبرپانک (Cyberpunk)</option>
                <option value="Fantasy Art">هنر فانتزی (Fantasy Art)</option>
                <option value="Minimalist">مینیمالیست (Minimalist)</option>
                <option value="Pop Art">پاپ آرت (Pop Art)</option>
                <option value="Surrealism">سورئالیسم (Surrealism)</option>
            </select>

            <label style="margin-top: 20px;">۴. نورپردازی و فضا</label>
            <select id="lighting">
                <option value="Golden Hour">نور طلایی غروب (Golden Hour)</option>
                <option value="Studio Lighting">نورپردازی استودیویی (Studio Lighting)</option>
                <option value="Neon Lights">نورهای نئونی (Neon Lights)</option>
                <option value="Soft Natural Light">نور طبیعی ملایم (Soft Natural Light)</option>
                <option value="Dramatic Lighting">نورپردازی دراماتیک (Dramatic Lighting)</option>
                <option value="Volumetric Lighting">نورپردازی حجمی (Volumetric Lighting)</option>
                <option value="Dark & Moody">تاریک و رازآلود (Dark & Moody)</option>
            </select>

            <label style="margin-top: 20px;">۵. ابعاد تصویر</label>
            <select id="dimensions">
                <option value="16:9 Landscape">16:9 افقی (یوتیوب / ویندوز)</option>
                <option value="9:16 Portrait">16:9 عمودی (استوری / شورتز)</option>
                <option value="1:1 Square">1:1 مربع (پست اینستاگرام)</option>
                <option value="4:5 Portrait">4:5 عمودی (فید اینستاگرام)</option>
                <option value="2:3 Portrait">2:3 عمودی (پرتره کلاسیک)</option>
                <option value="3:2 Landscape">2:3 افقی (عکاسی معمول)</option>
                <option value="21:9 Ultrawide">21:9 سینمایی فوق عریض</option>
            </select>

            <label style="margin-top: 20px;">۶. زاویه دوربین و ترکیب‌بندی</label>
            <select id="cameraAngle">
                <option value="Wide Shot">نمای باز (Wide Shot)</option>
                <option value="Close-up">نمای نزدیک (Close-up)</option>
                <option value="Aerial View">نمای هوایی/پهپاد (Aerial View)</option>
                <option value="Low Angle">زاویه پایین (Low Angle)</option>
                <option value="High Angle">زاویه بالا (High Angle)</option>
                <option value="Macro">نمای ماکرو (Macro)</option>
            </select>
        </div>

        <div class="card">
            <label>۷. آیا در تصویر متن داشته باشد؟</label>
            <div class="radio-group">
                <label><input type="radio" name="hasText" value="no" checked onclick="toggleTextInput()"><span>خیر</span></label>
                <label><input type="radio" name="hasText" value="yes" onclick="toggleTextInput()"><span>بله</span></label>
            </div>
            <div id="textLanguageContainer" class="hidden" style="margin-top: 20px;">
                <label>زبان متن داخل عکس:</label>
                <select id="textLanguage">
                    <option value="English">انگلیسی</option>
                    <option value="Persian">فارسی</option>
                    <option value="Hebrew">عبری</option>
                    <option value="Arabic">عربی</option>
                </select>
            </div>
        </div>

        <div class="card">
            <label>۸. پرامپت برای کدام هوش مصنوعی است؟</label>
            <select id="aiModel" onchange="toggleOtherAI()">
                <option value="ChatGPT (DALL-E 3)">ChatGPT</option>
                <option value="Midjourney">Midjourney</option>
                <option value="Nano Banana">Nano Banana</option>
                <option value="Stable Diffusion">Stable Diffusion</option>
                <option value="Leonardo AI">Leonardo AI</option>
                <option value="other">سایر...</option>
            </select>
            <input type="text" id="otherAIInput" class="hidden" style="margin-top: 15px;" placeholder="نام هوش مصنوعی را به انگلیسی تایپ کنید">
        </div>

        <button id="generateBtn" class="btn btn-generate" onclick="generatePrompt()">ساخت پرامپت حرفه‌ای ✨</button>

        <div id="outputCard" class="card hidden" style="margin-top: 25px;">
            <h3 style="margin-bottom: 15px; color: var(--accent-glow);">پرامپت نهایی شما:</h3>
            <div id="promptOutput"></div>
            <button class="btn btn-copy" onclick="copyText(document.getElementById('promptOutput').innerText, this)">کپی کردن پرامپت 📋</button>
        </div>
    </div>

    <!-- ========== ویو گالری پرامپت‌ها ========== -->
    <div id="gallery-view" class="view-container hidden">
        <header>
            <a href="javascript:void(0)" class="back-btn" onclick="showView('main-view')">بازگشت ⬅️</a>
            <h1 class="neon-text">گالری پرامپت‌ها</h1>
            <p class="subtitle">پرامپت‌های تایید شده توسط کاربران سایت</p>
        </header>
        
        <div id="gallery-grid"></div>

        <!-- فوتر چشمک زن -->
        <div class="footer-submit-container">
            <button class="blink-btn" onclick="openSubmitModal()">➕ اضافه کردن پرامپت از سمت شما</button>
        </div>
    </div>

    <!-- دکمه شناور دسترسی به گالری -->
    <button id="gallery-float-btn" class="float-btn" onclick="showView('gallery-view')">
        🖼️ گالری پرامپت‌ها
    </button>

    <!-- ========== مودال ارسال پرامپت جدید ========== -->
    <div id="submit-modal" class="modal-overlay hidden">
        <div class="modal-content">
            <button class="modal-close" onclick="closeSubmitModal()">&times;</button>
            <h2 style="margin-bottom: 20px; color: var(--accent-glow);">ارسال پرامپت برای پشتیبانی</h2>
            <p style="margin-bottom: 15px; font-size: 0.9rem; opacity: 0.8;">پرامپت و عکس نمونه شما پس از تایید پشتیبانی در گالری قرار می‌گیرد.</p>
            
            <label>۱. عکس نمونه (در صورت تایید، در گالری نمایش داده می‌شود)</label>
            <label class="file-upload-area" for="promptImage">
                <i>📷</i>
                <span id="file-name">برای انتخاب کلیک کنید</span>
                <input type="file" id="promptImage" accept="image/*" onchange="updateFileName(this)">
            </label>

            <label>۲. متن پرامپت (انگلیسی)</label>
            <textarea id="submittedPromptText" rows="5" placeholder="متن کامل پرامپت را اینجا وارد کنید..."></textarea>

            <button class="btn btn-generate" style="margin-top: 20px;" onclick="submitPromptToSupport()">ارسال برای پشتیبانی 🚀</button>
        </div>
    </div>

    <script>
        // ================= سیستم ذرات معلق =================
        const canvas = document.getElementById('particle-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function resizeCanvas() { canvas.width = window.innerWidth; canvas.height = window.innerHeight; }
        function getParticleColor() { return getComputedStyle(document.body).getPropertyValue('--particle-color').trim(); }

        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width; this.y = Math.random() * canvas.height;
                this.size = Math.random() * 3 + 1;
                this.speedX = (Math.random() * 0.5 - 0.25) * 0.5; this.speedY = (Math.random() * 0.5 - 0.25) * 0.5;
                this.opacity = Math.random() * 0.5 + 0.2;
            }
            update() {
                this.x += this.speedX; this.y += this.speedY;
                if (this.x < 0 || this.x > canvas.width) this.speedX *= -1;
                if (this.y < 0 || this.y > canvas.height) this.speedY *= -1;
            }
            draw() {
                const color = getParticleColor();
                ctx.beginPath(); ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = `rgba(${color}, ${this.opacity})`;
                ctx.shadowBlur = 15; ctx.shadowColor = `rgba(${color}, 1)`; ctx.fill();
            }
        }

        function initParticles() {
            particles = [];
            const numberOfParticles = (window.innerWidth * window.innerHeight) / 15000;
            for (let i = 0; i < numberOfParticles; i++) particles.push(new Particle());
        }
        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => { p.update(); p.draw(); });
            requestAnimationFrame(animateParticles);
        }
        window.addEventListener('resize', () => { resizeCanvas(); initParticles(); });
        resizeCanvas(); initParticles(); animateParticles();

        // ================= توابع رابط کاربری =================
        function toggleTheme() { document.body.classList.toggle('theme-light'); }
        function toggleTextInput() {
            const isYes = document.querySelector('input[name="hasText"][value="yes"]').checked;
            document.getElementById('textLanguageContainer').classList.toggle('hidden', !isYes);
        }
        function toggleOtherAI() {
            const aiModel = document.getElementById('aiModel').value;
            document.getElementById('otherAIInput').classList.toggle('hidden', aiModel !== 'other');
        }

        function showView(viewId) {
            document.querySelectorAll('.view-container').forEach(v => v.classList.add('hidden'));
            document.getElementById(viewId).classList.remove('hidden');
            
            // مخفی کردن دکمه شناور گالری در صفحه گالری
            document.getElementById('gallery-float-btn').style.display = viewId === 'gallery-view' ? 'none' : 'flex';
            window.scrollTo(0, 0);
        }

        // ================= تابع عمومی کپی متن =================
        function copyText(text, btn) {
            navigator.clipboard.writeText(text).then(() => {
                const originalText = btn.innerText;
                btn.innerText = 'کپی شد! ✅';
                setTimeout(() => btn.innerText = originalText, 2000);
            }).catch(err => {
                const textArea = document.createElement('textarea');
                textArea.value = text; document.body.appendChild(textArea); textArea.select();
                try { document.execCommand('copy'); btn.innerText = 'کپی شد! ✅'; setTimeout(() => btn.innerText = originalText, 2000); } 
                catch (e) { alert('خطا در کپی کردن'); }
                document.body.removeChild(textArea);
            });
        }

        // ================= ساخت پرامپت و ترجمه =================
        async function translateToEnglish(text) {
            if (!text || /[a-zA-Z]/.test(text)) return text;
            try {
                const url = `https://api.mymemory.translated.net/get?q=${encodeURIComponent(text)}&langpair=fa|en`;
                const response = await fetch(url); const data = await response.json();
                return data.responseData ? data.responseData.translatedText : text;
            } catch (error) { return text; }
        }

        async function generatePrompt() {
            const generateBtn = document.getElementById('generateBtn');
            generateBtn.innerText = 'در حال پردازش و ترجمه...';
            generateBtn.classList.add('loading'); generateBtn.disabled = true;

            const mainIdea = document.getElementById('mainIdea').value;
            const details = document.getElementById('details').value;
            const style = document.getElementById('style').value;
            const lighting = document.getElementById('lighting').value;
            const dimensions = document.getElementById('dimensions').value;
            const cameraAngle = document.getElementById('cameraAngle').value;
            const hasText = document.querySelector('input[name="hasText"]:checked').value;
            const textLanguage = document.getElementById('textLanguage').value;
            let aiModel = document.getElementById('aiModel').value;
            if (aiModel === 'other') aiModel = document.getElementById('otherAIInput').value || 'AI';

            if (!mainIdea) {
                alert('لطفاً ایده اصلی را وارد کنید.');
                generateBtn.innerText = 'ساخت پرامپت حرفه‌ای ✨'; generateBtn.classList.remove('loading'); generateBtn.disabled = false;
                return;
            }

            const translatedIdea = await translateToEnglish(mainIdea);
            const translatedDetails = await translateToEnglish(details);

            let prompt = `Subject: ${translatedIdea}.\n`;
            if (translatedDetails) prompt += `Additional Details: ${translatedDetails}.\n`;
            prompt += `Art Style: ${style}.\nLighting & Mood: ${lighting}.\n`;
            prompt += `Camera Angle & Composition: ${cameraAngle}.\nAspect Ratio: ${dimensions}.\n`;
            
            if (hasText === 'yes') prompt += `Text Overlay: Include text written in ${textLanguage}. Ensure the text is legible and seamlessly integrated into the image.\n`;
            else prompt += `Text Overlay: No text.\n`;

            prompt += `Quality Enhancers: Masterpiece, 8k resolution, ultra-detailed, hyper-realistic, sharp focus, professional color grading, highly intricate, award-winning visual quality.\n`;
            prompt += `Optimized for: ${aiModel}.`;

            document.getElementById('promptOutput').innerText = prompt;
            document.getElementById('outputCard').classList.remove('hidden');
            generateBtn.innerText = 'ساخت پرامپت حرفه‌ای ✨'; generateBtn.classList.remove('loading'); generateBtn.disabled = false;
            document.getElementById('outputCard').scrollIntoView({ behavior: 'smooth' });
        }

        // ================= سیستم گالری و ارسال پرامپت =================
        
        // پرامپت‌های نمونه (شبیه‌سازی دیتابیس)
        let galleryPrompts = [
            { id: 1, image: "https://images.unsplash.com/photo-1518709268805-4e9042af9f23?q=80&w=1000&auto=format&fit=crop", prompt: "A futuristic cyberpunk city street at night, neon lights reflecting in puddles, flying cars, cinematic lighting, 8k resolution, photorealistic, Blade Runner style." },
            { id: 2, image: "https://images.unsplash.com/photo-1518837695005-2083093ee35b?q=80&w=1000&auto=format&fit=crop", prompt: "A majestic lion in the savannah during golden hour, dramatic lighting, ultra-detailed fur, close-up shot, nature photography, award-winning." },
            { id: 3, image: "https://images.unsplash.com/photo-1451187580459-43490279c0fa?q=80&w=1000&auto=format&fit=crop", prompt: "Earth viewed from space, highly detailed atmosphere, stars in the background, volumetric lighting, 3D render, masterpiece." }
        ];

        function renderGallery() {
            const grid = document.getElementById('gallery-grid');
            grid.innerHTML = '';
            galleryPrompts.forEach(item => {
                const card = document.createElement('div');
                card.className = 'gallery-card';
                card.innerHTML = `
                    <img src="${item.image}" alt="Prompt Image">
                    <div class="content">
                        <div class="prompt-text">${item.prompt}</div>
                        <button class="copy-gallery-btn" onclick="copyText('${item.prompt.replace(/'/g, "\\'")}', this)">کپی پرامپت 📋</button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function openSubmitModal() { document.getElementById('submit-modal').classList.remove('hidden'); }
        function closeSubmitModal() { document.getElementById('submit-modal').classList.add('hidden'); }
        function updateFileName(input) {
            const fileName = input.files[0] ? input.files[0].name : 'برای انتخاب کلیک کنید';
            document.getElementById('file-name').innerText = fileName;
        }

        async function submitPromptToSupport() {
            const imageFile = document.getElementById('promptImage').files[0];
            const promptText = document.getElementById('submittedPromptText').value;

            if (!imageFile || !promptText) {
                alert('لطفاً هم عکس و هم متن پرامپت را وارد کنید.');
                return;
            }

            // شبیه‌سازی ارسال به پشتیبانی
            // در محیط واقعی، اینجا باید از FormData و fetch برای ارسال به سرور (API) استفاده کنید:
            /*
            const formData = new FormData();
            formData.append('image', imageFile);
            formData.append('prompt', promptText);
            
            try {
                const res = await fetch('https://your-website.com/api/submit-prompt', {
                    method: 'POST',
                    body: formData
                });
                if(res.ok) alert('پرامپت شما با موفقیت ارسال شد!');
            } catch(err) {
                alert('خطا در ارسال');
            }
            */

            // شبیه‌سازی موفقیت‌آمیز بودن ارسال
            const submitBtn = event.target;
            submitBtn.innerText = 'در حال ارسال...';
            submitBtn.disabled = true;

            setTimeout(() => {
                alert('✅ پرامپت و عکس شما با موفقیت برای پشتیبانی ارسال شد. پس از تایید، در گالری قرار می‌گیرد.');
                document.getElementById('promptImage').value = '';
                document.getElementById('submittedPromptText').value = '';
                document.getElementById('file-name').innerText = 'برای انتخاب کلیک کنید';
                closeSubmitModal();
                submitBtn.innerText = 'ارسال برای پشتیبانی 🚀';
                submitBtn.disabled = false;
            }, 1500);
        }

        // اجرای اولیه
        renderGallery();
    </script>
</body>
</html>
