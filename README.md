<!DOCTYPE html>
<html lang="en" id="mainHtml">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Tactical Hub - Final All-In-One</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&display=swap" rel="stylesheet">
    <style>
        :root { --emerald: #10b981; --blue: #3b82f6; --red: #ef4444; }
        body { background-color: #020617; color: white; font-family: 'Cairo', sans-serif; margin: 0; padding: 0; }
        
        /* Force text colors for GitHub compatibility */
        .glass-panel { background: rgba(15, 23, 42, 0.9); backdrop-filter: blur(20px); border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 20px; }
        .input-cell { background: #0f172a !important; border: 1px solid #334155 !important; color: #ffffff !important; padding: 10px; border-radius: 6px; width: 100%; text-align: center; font-weight: bold; }
        .select-cell { background: #1e293b !important; border: 1px solid var(--emerald) !important; color: #ffffff !important; padding: 10px; border-radius: 6px; width: 100%; font-weight: bold; cursor: pointer; }
        .table-text { color: #ffffff !important; font-weight: 600; }
        .table-header { font-size: 0.75rem; font-weight: 900; color: #94a3b8 !important; text-transform: uppercase; padding: 12px; background: #1e293b; }
        
        /* Banner & Navigation */
        .alpha-banner { background: linear-gradient(90deg, #064e3b, #020617); border-bottom: 2px solid var(--emerald); padding: 12px; text-align: center; font-weight: 900; position: sticky; top: 0; z-index: 100; }
        .lang-toggle { position: fixed; top: 70px; right: 20px; z-index: 200; cursor: pointer; background: var(--blue); padding: 10px 20px; border-radius: 50px; font-weight: 900; box-shadow: 0 4px 15px rgba(0,0,0,0.5); }
        
        /* Video HUD */
        .video-box { border: 2px dashed #334155; border-radius: 16px; background: #000; position: relative; overflow: hidden; }
        .video-box:hover { border-color: var(--emerald); }
        
        @media print { .no-print { display: none !important; } }
    </style>
</head>
<body dir="ltr">

    <!-- LANGUAGE TOGGLE -->
    <div class="lang-toggle flex items-center gap-2 no-print" onclick="toggleLanguage()">
        <span id="langName">العربية</span> 🌐
    </div>

    <!-- TOP STATEMENT -->
    <div class="alpha-banner no-print">
        <span id="txtBanner" class="text-white">⚠️ Team Alpha is the team that appears on the LEFT of each video clip.</span>
    </div>

    <div class="max-w-7xl mx-auto p-4 lg:p-10 space-y-12">
        <header class="text-center space-y-2">
            <h1 class="text-4xl lg:text-5xl font-black text-emerald-400 uppercase tracking-tighter" id="txtMainTitle">AI Tactical Prediction Hub</h1>
            <p class="text-slate-400 text-sm font-bold" id="txtSubTitle">Location-Aware Analysis & Historical Video Mapping</p>
        </header>

        <!-- 1. REQUIREMENT TABLES (8 METRICS + LOCATION) -->
        <section class="space-y-6 no-print">
            <h2 class="text-xl font-black border-l-4 border-emerald-500 pl-4 uppercase" id="txtStep1">1. Mandatory Seasonal Statistics</h2>
            
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <!-- TEAM A -->
                <div class="glass-panel overflow-hidden border-b-4 border-blue-500">
                    <div class="bg-blue-600/20 p-4"><input type="text" id="nameA" value="Team Alpha" oninput="updateMappingOptions()" class="bg-transparent font-black text-blue-400 uppercase outline-none text-xl w-full"></div>
                    <table class="w-full text-sm">
                        <thead><tr><th class="table-header" id="thReqA">Requirement</th><th class="table-header" id="thValA">Value</th></tr></thead>
                        <tbody id="tableBodyA"></tbody>
                    </table>
                </div>

                <!-- TEAM B -->
                <div class="glass-panel overflow-hidden border-b-4 border-red-500">
                    <div class="bg-red-600/20 p-4"><input type="text" id="nameB" value="Team Beta" oninput="updateMappingOptions()" class="bg-transparent font-black text-red-400 uppercase outline-none text-xl w-full"></div>
                    <table class="w-full text-sm">
                        <thead><tr><th class="table-header" id="thReqB">Requirement</th><th class="table-header" id="thValB">Value</th></tr></thead>
                        <tbody id="tableBodyB"></tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- 2. DUAL VIDEO MAPPING -->
        <section class="space-y-6 no-print">
            <h2 class="text-xl font-black border-l-4 border-blue-500 pl-4 uppercase" id="txtStep2">2. Last Match Video Mapping</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div class="glass-panel p-6 space-y-4">
                    <label class="text-[10px] font-black uppercase text-emerald-500" id="lblMap1">Which team is on the LEFT in this video?</label>
                    <select id="mapV1" class="select-cell"></select>
                    <div onclick="document.getElementById('file1').click()" class="aspect-video video-box flex items-center justify-center cursor-pointer border border-white/5">
                        <video id="vPrev1" class="hidden w-full h-full object-cover"></video>
                        <span id="vPrompt1" class="text-xs text-slate-500 font-bold uppercase">Upload Match Recording #1</span>
                    </div>
                    <input type="file" id="file1" class="hidden" accept="video/mp4" onchange="preview(event, 1)">
                </div>

                <div class="glass-panel p-6 space-y-4">
                    <label class="text-[10px] font-black uppercase text-emerald-500" id="lblMap2">Which team is on the LEFT in this video?</label>
                    <select id="mapV2" class="select-cell"></select>
                    <div onclick="document.getElementById('file2').click()" class="aspect-video video-box flex items-center justify-center cursor-pointer border border-white/5">
                        <video id="vPrev2" class="hidden w-full h-full object-cover"></video>
                        <span id="vPrompt2" class="text-xs text-slate-500 font-bold uppercase">Upload Match Recording #2</span>
                    </div>
                    <input type="file" id="file2" class="hidden" accept="video/mp4" onchange="preview(event, 2)">
                </div>
            </div>
        </section>

        <div class="text-center py-6 no-print">
            <button onclick="processAI()" class="bg-emerald-600 px-16 py-6 rounded-2xl font-black text-2xl hover:bg-emerald-500 shadow-xl transition-all active:scale-95" id="btnRun">RUN AI ANALYSES</button>
        </div>

        <!-- RESULTS SECTION -->
        <section id="results" class="hidden space-y-6 pb-20">
            <div class="glass-panel p-10 border-t-8 border-emerald-500 text-center">
                <h2 class="text-xs font-black text-slate-500 uppercase tracking-widest mb-8" id="resTitle">Tactical Win Probability</h2>
                <div class="flex flex-col lg:flex-row justify-around items-center gap-10">
                    <div class="flex-1">
                        <div id="resNameA" class="text-2xl font-black text-blue-400 uppercase">---</div>
                        <div id="resLocA" class="text-[10px] text-slate-500 font-bold uppercase mb-2">---</div>
                        <div id="resProbA" class="text-8xl font-black text-white">0%</div>
                    </div>
                    <div class="w-full max-w-md h-6 bg-slate-900 rounded-full flex overflow-hidden border border-white/10 shadow-inner">
                        <div id="barA" class="bg-blue-600 h-full transition-all duration-1000"></div>
                        <div id="barB" class="bg-red-600 h-full transition-all duration-1000"></div>
                    </div>
                    <div class="flex-1">
                        <div id="resNameB" class="text-2xl font-black text-red-400 uppercase">---</div>
                        <div id="resLocB" class="text-[10px] text-slate-500 font-bold uppercase mb-2">---</div>
                        <div id="resProbB" class="text-8xl font-black text-white">0%</div>
                    </div>
                </div>
                <div id="aiLogic" class="mt-10 p-6 bg-white/5 rounded-2xl text-slate-300 italic text-sm border-l-4 border-emerald-500 text-left"></div>
                
                <div class="mt-8 no-print">
                    <button onclick="saveAnalysis()" class="bg-blue-600 px-8 py-3 rounded-xl font-black text-sm hover:bg-blue-500">💾 SAVE ANALYSIS REPORT</button>
                </div>
            </div>
        </section>
    </div>

    <script>
        const i18n = {
            en: {
                banner: "⚠️ Team Alpha is the team that appears on the LEFT of each video clip.",
                mainTitle: "AI Tactical Prediction Hub",
                subTitle: "Location-Aware Analysis & Historical Video Mapping",
                step1: "1. Mandatory Seasonal Statistics",
                step2: "2. Last Match Video Mapping",
                req: "Requirement", val: "Value",
                fields: ["Games Played (GP)", "Points Made (PTS)", "Winning Games (W)", "Tie Games (D)", "Lost Games (L)", "Goals Made (GF)", "Goals Against (GA)", "Goal Variance (GD)", "Game Location"],
                locationOpts: ["Home", "Guest", "Neutral"],
                run: "RUN AI ANALYSES", resT: "Tactical Win Probability", lang: "العربية"
            },
            ar: {
                banner: "⚠️ الفريق 'ألفا' هو الفريق الذي يظهر على يسار شاشة الفيديو دائماً.",
                mainTitle: "مركز التوقعات التكتيكي الذكي",
                subTitle: "التحليل المكاني وربط سجلات الفيديو التاريخية",
                step1: "1. الإحصائيات الموسمية الإلزامية",
                step2: "2. ربط فيديو آخر مباراة مسجلة",
                req: "المعيار المطلوب", val: "القيمة",
                fields: ["المباريات (GP)", "النقاط (PTS)", "فوز (W)", "تعادل (D)", "خسارة (L)", "أهداف له (GF)", "أهداف عليه (GA)", "فارق الأهداف (GD)", "موقع المباراة"],
                locationOpts: ["داخل الأرض (Home)", "خارج الأرض (Guest)", "أرض محايدة (Neutral)"],
                run: "بدء التحليل الذكي", resT: "احتمالية الفوز التكتيكية", lang: "English"
            }
        };

        const fieldKeys = ["gp", "pts", "w", "d", "l", "gf", "ga", "var", "loc"];
        let currentLang = 'en';

        function toggleLanguage() {
            currentLang = currentLang === 'en' ? 'ar' : 'en';
            document.getElementById('mainHtml').dir = currentLang === 'ar' ? 'rtl' : 'ltr';
            renderStaticText();
            renderTables();
        }

        function renderStaticText() {
            const l = i18n[currentLang];
            document.getElementById('langName').innerText = l.lang;
            document.getElementById('txtBanner').innerText = l.banner;
            document.getElementById('txtMainTitle').innerText = l.mainTitle;
            document.getElementById('txtSubTitle').innerText = l.subTitle;
            document.getElementById('txtStep1').innerText = l.step1;
            document.getElementById('txtStep2').innerText = l.step2;
            document.getElementById('thReqA').innerText = l.req; document.getElementById('thValA').innerText = l.val;
            document.getElementById('thReqB').innerText = l.req; document.getElementById('thValB').innerText = l.val;
            document.getElementById('btnRun').innerText = l.run;
            document.getElementById('resTitle').innerText = l.resT;
        }

        function renderTables() {
            const l = i18n[currentLang];
            const generateHTML = (team) => fieldKeys.map((key, i) => {
                if(key === 'loc') {
                    return `<tr class="border-b border-white/5">
                        <td class="p-3 table-text">${l.fields[i]}</td>
                        <td><select id="loc${team}" class="select-cell">
                            <option value="home">${l.locationOpts[0]}</option>
                            <option value="guest">${l.locationOpts[1]}</option>
                            <option value="neutral">${l.locationOpts[2]}</option>
                        </select></td>
                    </tr>`;
                }
                return `<tr class="border-b border-white/5">
                    <td class="p-3 table-text">${l.fields[i]}</td>
                    <td><input type="number" id="${key}${team}" class="input-cell ${key==='var'?'text-emerald-400':''}" value="0" ${key==='var'?'readonly':''}></td>
                </tr>`;
            }).join('');

            document.getElementById('tableBodyA').innerHTML = generateHTML('A');
            document.getElementById('tableBodyB').innerHTML = generateHTML('B');
            
            // Add GD calculation listeners
            ['A', 'B'].forEach(t => {
                ['gf', 'ga'].forEach(f => {
                    const el = document.getElementById(`${f}${t}`);
                    if(el) el.addEventListener('input', () => {
                        const gf = parseInt(document.getElementById(`gf${t}`).value) || 0;
                        const ga = parseInt(document.getElementById(`ga${t}`).value) || 0;
                        document.getElementById(`var${t}`).value = gf - ga;
                    });
                });
            });
            updateMappingOptions();
        }

        function updateMappingOptions() {
            const nA = document.getElementById('nameA').value || 'Team Alpha';
            const nB = document.getElementById('nameB').value || 'Team Beta';
            const opts = `<option value="A">${nA}</option><option value="B">${nB}</option>`;
            document.getElementById('mapV1').innerHTML = opts;
            document.getElementById('mapV2').innerHTML = opts;
        }

        function preview(e, id) {
            const file = e.target.files[0];
            if (!file) return;
            const v = document.getElementById(`vPrev${id}`);
            v.src = URL.createObjectURL(file);
            v.classList.remove('hidden');
            document.getElementById(`vPrompt${id}`).classList.add('hidden');
        }

        function processAI() {
            const getT = (t) => ({
                name: document.getElementById(`name${t}`).value,
                gp: parseInt(document.getElementById(`gp${t}`).value) || 1,
                pts: parseInt(document.getElementById(`pts${t}`).value) || 0,
                w: parseInt(document.getElementById(`w${t}`).value) || 0,
                gf: parseInt(document.getElementById(`gf${t}`).value) || 0,
                ga: parseInt(document.getElementById(`ga${t}`).value) || 0,
                gd: parseInt(document.getElementById(`var${t}`).value) || 0,
                loc: document.getElementById(`loc${t}`).value
            });

            const a = getT('A'); const b = getT('B');
            const getMult = (loc) => loc === 'home' ? 1.15 : loc === 'guest' ? 0.90 : 1.0;

            const calc = (t) => {
                const base = (t.pts/t.gp * 40) + (t.w/t.gp * 20) + (t.gd/t.gp * 40);
                return base * getMult(t.loc);
            };

            const sA = calc(a); const sB = calc(b);
            const pA = (sA / (sA + sB) * 100).toFixed(1);
            const pB = (100 - pA).toFixed(1);

            document.getElementById('results').classList.remove('hidden');
            document.getElementById('resNameA').innerText = a.name;
            document.getElementById('resNameB').innerText = b.name;
            document.getElementById('resLocA').innerText = a.loc;
            document.getElementById('resLocB').innerText = b.loc;
            document.getElementById('resProbA').innerText = pA + "%";
            document.getElementById('resProbB').innerText = pB + "%";
            document.getElementById('barA').style.width = pA + "%";
            document.getElementById('barB').style.width = pB + "%";

            const logic = currentLang === 'en' 
                ? `Inference: Location factor applied (${getMult(a.loc)}x vs ${getMult(b.loc)}x). Strategic Strength: ${a.name} [${sA.toFixed(1)}] | ${b.name} [${sB.toFixed(1)}]. Variance Trend: ${a.gd > b.gd ? a.name : b.name} is more stable.`
                : `الاستنتاج: تم تطبيق عامل الأرض (${getMult(a.loc)}x مقابل ${getMult(b.loc)}x). القوة الاستراتيجية: ${a.name} [${sA.toFixed(1)}] | ${b.name} [${sB.toFixed(1)}]. ميل الفارق: ${a.gd > b.gd ? a.name : b.name} أكثر استقراراً.`;
            
            document.getElementById('aiLogic').innerText = logic;
            window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' });
        }

        function saveAnalysis() {
            const analystName = document.getElementById('nameA').value + "_vs_" + document.getElementById('nameB').value;
            const content = document.getElementById('results').innerHTML;
            const blob = new Blob([`<html><body style="background:#020617;color:white;font-family:sans-serif;padding:50px;">${content}</body></html>`], {type: "text/html"});
            const a = document.createElement("a");
            a.href = URL.createObjectURL(blob);
            a.download = `AI_Report_${analystName}.html`;
            a.click();
        }

        // Initialize On Load
        window.onload = () => {
            renderStaticText();
            renderTables();
            updateMappingOptions();
        };
    </script>
</body>
</html>
