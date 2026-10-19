<!DOCTYPE html>
<html lang="en" class="h-full dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Master of the Typing - Speed, Accuracy & Certificate Platform</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        themeDarkBg: '#0f172a',
                        themeCardBg: '#1e293b',
                        themeBorder: '#334155'
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Inter:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Canvas Confetti -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.5.1/dist/confetti.browser.min.js"></script>
    <style>
        body { font-family: 'Inter', sans-serif; transition: background-color 0.3s, color 0.3s; }
        .font-mono-code { font-family: 'JetBrains Mono', monospace; }
        .font-certificate { font-family: 'Cinzel', serif; }
        
        /* Night Shift Theme Styling */
        body.night-shift-theme {
            background-color: #1a140d !important;
            color: #f3e8d8 !important;
        }
        body.night-shift-theme .theme-card {
            background-color: #261e15 !important;
            border-color: #483928 !important;
        }
        body.night-shift-theme .theme-inner {
            background-color: #17110a !important;
            border-color: #3b2e20 !important;
        }

        /* Light Theme Styling */
        body.light-theme {
            background-color: #f1f5f9 !important;
            color: #0f172a !important;
        }
        body.light-theme .theme-card {
            background-color: #ffffff !important;
            border-color: #cbd5e1 !important;
            box-shadow: 0 10px 25px -5px rgba(0,0,0,0.08) !important;
        }
        body.light-theme .theme-inner {
            background-color: #f8fafc !important;
            border-color: #e2e8f0 !important;
        }
        body.light-theme select, body.light-theme input {
            background-color: #ffffff !important;
            color: #0f172a !important;
            border-color: #cbd5e1 !important;
        }

        @media print {
            body * { visibility: hidden; }
            #certificateModal, #certificateModal * { visibility: visible; }
            #certificateModal { position: absolute; left: 0; top: 0; width: 100%; height: 100%; background: white !important; }
            .no-print { display: none !important; }
        }
    </style>
</head>
<body class="h-full bg-[#0f172a] text-slate-100" id="bodyRoot">

    <div class="min-h-full flex flex-col justify-between">
        
        <!-- HEADER BAR -->
        <header class="border-b border-slate-800 bg-[#1e293b]/90 backdrop-blur sticky top-0 z-40 px-4 lg:px-8 py-3 flex flex-wrap items-center justify-between gap-4 shadow-lg">
            
            <div class="flex items-center gap-4 flex-wrap">
                <div class="flex items-center gap-3">
                    <div class="bg-indigo-600 text-white p-2.5 rounded-2xl shadow-md flex items-center justify-center">
                        <i class="fa-solid fa-keyboard text-xl"></i>
                    </div>
                    <div>
                        <h1 class="text-xl font-extrabold tracking-tight text-white flex items-center gap-2">
                            Master of the Typing
                        </h1>
                        <p class="text-xs text-slate-400 font-medium">Speed, Accuracy, Coding & Certificate Platform</p>
                    </div>
                </div>

                <div class="flex items-center gap-2.5 bg-slate-800/90 border border-amber-500/40 px-3 py-1.5 rounded-2xl shadow-inner">
                    <img src="https://placehold.co/100x100/1e1b4b/38bdf8?text=AK" alt="Amit Kumar Owner" class="w-8 h-8 rounded-full border-2 border-amber-400 object-cover shadow">
                    <div>
                        <p class="text-[11px] font-bold text-amber-400 leading-tight">Owner: Amit Kumar</p>
                        <p class="text-[9px] text-slate-400 uppercase font-bold tracking-wider">Founder & Director</p>
                    </div>
                </div>

                <!-- USER ACCOUNT & LOGIN STATUS BAR -->
                <div class="flex items-center gap-2 border-l border-slate-800 pl-4">
                    <div id="userAccountBox" class="flex items-center gap-2">
                        <button onclick="window.openLoginModal()" id="loginBtn" class="px-3 py-1.5 bg-indigo-600 hover:bg-indigo-500 text-white rounded-xl text-xs font-bold transition flex items-center gap-1.5 shadow">
                            <i class="fa-solid fa-user"></i> Login / Register
                        </button>
                        <div id="userInfoBadge" class="hidden flex items-center gap-2 bg-slate-800 border border-slate-700 px-3 py-1 rounded-xl text-xs">
                            <i class="fa-solid fa-circle-user text-emerald-400"></i>
                            <div class="flex flex-col">
                                <span id="userBadgeName" class="font-bold text-white leading-none">User</span>
                                <span id="userBadgeEmail" class="text-[10px] text-slate-400 leading-tight">user@example.com</span>
                            </div>
                            <span id="subBadge" class="bg-amber-500/20 text-amber-300 text-[9px] font-bold px-1.5 py-0.5 rounded border border-amber-500/40 ml-1">FREE TRIAL</span>
                        </div>
                    </div>
                </div>

                <div class="hidden md:flex items-center gap-2 border-l border-slate-800 pl-4 text-xs font-semibold">
                    <span class="px-3 py-1.5 bg-slate-800/80 text-emerald-400 rounded-xl flex items-center gap-1.5 border border-slate-700/60">
                        <i class="fa-solid fa-gauge-high"></i> Speed: <strong id="headerWpm" class="text-white text-sm">0</strong> WPM
                    </span>
                    <span class="px-3 py-1.5 bg-slate-800/80 text-indigo-400 rounded-xl flex items-center gap-1.5 border border-slate-700/60">
                        <i class="fa-solid fa-bullseye"></i> Accuracy: <strong id="headerAcc" class="text-white text-sm">100</strong>%
                    </span>
                </div>
            </div>

            <!-- Theme Buttons -->
            <div class="flex items-center gap-3">
                <div class="flex items-center bg-[#0f172a] border border-[#334155] p-1 rounded-xl gap-1">
                    <button onclick="window.setTheme('light')" id="btnThemeLight" title="Light Mode" class="px-2.5 py-1 rounded-lg text-xs text-slate-400 hover:text-white transition">
                        <i class="fa-solid fa-sun text-amber-500"></i> Light
                    </button>
                    <button onclick="window.setTheme('dark')" id="btnThemeDark" title="Dark Mode" class="px-2.5 py-1 rounded-lg text-xs text-indigo-400 font-bold bg-slate-800 transition">
                        <i class="fa-solid fa-moon"></i> Dark
                    </button>
                    <button onclick="window.setTheme('nightshift')" id="btnThemeNight" title="Night Shift Mode" class="px-2.5 py-1 rounded-lg text-xs text-amber-500 font-bold hover:bg-amber-950/40 transition">
                        <i class="fa-solid fa-eye text-amber-400"></i> Night Shift
                    </button>
                </div>
            </div>

        </header>

        <!-- MAIN CONTENT AREA -->
        <main class="flex-1 max-w-5xl w-full mx-auto p-4 md:p-6 my-auto flex flex-col justify-center gap-6">
            
            <div class="theme-card bg-[#1e293b] rounded-3xl border border-[#334155] p-6 md:p-8 shadow-2xl flex flex-col gap-6 relative">
                
                <!-- TOP CONTROLS GRID (4 DROPDOWNS & CONTROLS) -->
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 border-b border-slate-800 pb-6">
                    
                    <!-- 1. TEST LENGTH (1 to 60 Minutes Dropdown) -->
                    <div class="flex flex-col gap-1.5">
                        <label class="text-xs font-bold text-slate-400 tracking-wider uppercase"><i class="fa-solid fa-clock text-indigo-400 mr-1"></i> TEST LENGTH</label>
                        <select id="testLengthSelect" onchange="window.updateDuration()" class="w-full bg-[#0f172a] border border-[#334155] text-slate-100 text-xs font-semibold rounded-2xl px-3 py-3 focus:outline-none focus:ring-2 focus:ring-indigo-500 cursor-pointer">
                            <option value="1" selected>1 Minute</option>
                            <option value="2">2 Minutes</option>
                            <option value="3">3 Minutes</option>
                            <option value="4">4 Minutes</option>
                            <option value="5">5 Minutes</option>
                            <option value="10">10 Minutes</option>
                            <option value="15">15 Minutes</option>
                            <option value="20">20 Minutes</option>
                            <option value="30">30 Minutes</option>
                            <option value="40">40 Minutes</option>
                            <option value="50">50 Minutes</option>
                            <option value="60">60 Minutes (1 Hour)</option>
                        </select>
                    </div>

                    <!-- 2. PRACTICE TYPE (Normal vs Coding Buttons) -->
                    <div class="flex flex-col gap-1.5">
                        <label class="text-xs font-bold text-indigo-400 tracking-wider uppercase"><i class="fa-solid fa-sliders mr-1"></i> PRACTICE TYPE</label>
                        <div class="grid grid-cols-2 gap-1.5 bg-[#0f172a] p-1 border border-[#334155] rounded-2xl h-[46px] items-center">
                            <button type="button" id="typeNormalBtn" onclick="window.setPracticeType('normal')" class="h-full py-1 px-2 text-xs font-bold rounded-xl bg-indigo-600 text-white transition flex items-center justify-center gap-1 shadow">
                                <i class="fa-solid fa-font"></i> Normal Text
                            </button>
                            <button type="button" id="typeCodingBtn" onclick="window.setPracticeType('coding')" class="h-full py-1 px-2 text-xs font-bold rounded-xl text-purple-300 hover:text-white transition flex items-center justify-center gap-1">
                                <i class="fa-solid fa-code"></i> Coding
                            </button>
                        </div>
                    </div>

                    <!-- 3. DYNAMIC LANGUAGE SELECTOR DROPDOWN -->
                    <div id="languageBox" class="flex flex-col gap-1.5">
                        <label id="languageLabel" class="text-xs font-bold text-slate-400 tracking-wider uppercase"><i class="fa-solid fa-globe text-emerald-400 mr-1"></i> SELECT LANGUAGE</label>
                        
                        <!-- Normal Text Language Select -->
                        <select id="normalLanguageSelect" onchange="window.handleLanguageChange(event)" class="w-full bg-[#0f172a] border border-[#334155] text-slate-100 text-xs font-semibold rounded-2xl px-3 py-3 focus:outline-none focus:ring-2 focus:ring-indigo-500 cursor-pointer">
                            <optgroup label="🇮🇳 Indian Languages (भारतीय भाषाएं)">
                                <option value="hi" selected>Hindi (हिन्दी)</option>
                                <option value="mr">Marathi (मराठी)</option>
                                <option value="bn">Bengali (বাংলা)</option>
                                <option value="pa">Punjabi (ਪੰਜਾਬੀ)</option>
                                <option value="gu">Gujarati (ગુજરાતી)</option>
                                <option value="ta">Tamil (தமிழ்)</option>
                                <option value="te">Telugu (తెలుగు)</option>
                                <option value="kn">Kannada (ਕನ್ನಡ)</option>
                                <option value="ml">Malayalam (മലയാളം)</option>
                                <option value="or">Odia (ଓଡ଼ିଆ)</option>
                            </optgroup>
                            <optgroup label="🌍 World Languages (विश्व की भाषाएं)">
                                <option value="en">English (US/UK)</option>
                                <option value="es">Spanish (Español)</option>
                                <option value="fr">French (Français)</option>
                                <option value="de">German (Deutsch)</option>
                                <option value="ru">Russian (Русский)</option>
                                <option value="ar">Arabic (العربية)</option>
                                <option value="zh">Chinese (中文)</option>
                                <option value="ja">Japanese (日本語)</option>
                                <option value="pt">Portuguese (Português)</option>
                                <option value="it">Italian (Italiano)</option>
                                <option value="nl">Dutch (Nederlands)</option>
                                <option value="tr">Turkish (Türkçe)</option>
                            </optgroup>
                            <optgroup label="✏️ Custom Choice">
                                <option value="custom_add">+ Add Custom Text Language...</option>
                            </optgroup>
                        </select>

                        <!-- Coding Language Select with Expanded Python, Swift/iOS & Modern Ecosystems -->
                        <select id="codingLanguageSelect" onchange="window.handleCodingModeChange(event)" class="hidden w-full bg-[#0f172a] border border-purple-700/80 text-purple-200 text-xs font-semibold rounded-2xl px-3 py-3 focus:outline-none focus:ring-2 focus:ring-purple-500 cursor-pointer">
                            <optgroup label="🐍 Python Ecosystem (All Modern Frameworks)">
                                <option value="python" selected>Python 3 (Core & Standard Library)</option>
                                <option value="python_django">Python - Django Web Framework</option>
                                <option value="python_flask">Python - Flask Micro-framework</option>
                                <option value="python_fastapi">Python - FastAPI Modern APIs</option>
                                <option value="python_numpy">Python - NumPy & Data Structures</option>
                                <option value="python_pandas">Python - Pandas Dataframes</option>
                                <option value="python_pytorch">Python - PyTorch AI & ML</option>
                            </optgroup>
                            <optgroup label="🍎 Swift & Apple iOS / macOS Ecosystem">
                                <option value="swift">Swift 5.10 (Core Syntax & Modern Async/Await)</option>
                                <option value="swiftui">SwiftUI Declarative UI Framework</option>
                                <option value="uikit">Swift - UIKit & Cocoa Touch (iOS)</option>
                                <option value="combine">Swift - Combine Reactive Framework</option>
                                <option value="objc">Objective-C (Apple Legacy iOS/macOS)</option>
                            </optgroup>
                            <optgroup label="🚀 Modern & Emerging Programming Languages">
                                <option value="rust">Rust 1.78 (Memory Safety & Systems)</option>
                                <option value="golang">Go (Golang Concurrency & Microservices)</option>
                                <option value="typescript">TypeScript 5 (Typed Web Systems)</option>
                                <option value="kotlin">Kotlin (Modern Android & Multiplatform)</option>
                                <option value="zig">Zig (Low-level Systems Programming)</option>
                                <option value="mojo">Mojo (AI Infrastructure & High Performance)</option>
                                <option value="elixir">Elixir & Erlang BEAM VM</option>
                                <option value="dart">Dart & Flutter Mobile Framework</option>
                            </optgroup>
                            <optgroup label="💻 Classical & Enterprise Systems">
                                <option value="javascript">JavaScript (ES6+ & Modern Web)</option>
                                <option value="cpp">C++ 23 Systems & Game Engines</option>
                                <option value="csharp">C# & .NET 8 Framework</option>
                                <option value="java">Java 21 Enterprise & Spring Boot</option>
                                <option value="html">HTML5 Markup & Accessibility</option>
                                <option value="css">CSS3 & Modern Tailwind Utility</option>
                                <option value="sql">SQL & Relational Databases</option>
                            </optgroup>
                            <optgroup label="🛠 Custom Code Option">
                                <option value="custom_code_add">+ Add Custom Code Language / Snippets...</option>
                            </optgroup>
                        </select>
                    </div>

                    <!-- 4. DIFFICULTY LEVEL DROPDOWN (7 LEVELS SELECT BOX) -->
                    <div class="flex flex-col gap-1.5">
                        <label class="text-xs font-bold text-amber-400 tracking-wider uppercase"><i class="fa-solid fa-layer-group text-amber-400 mr-1"></i> DIFFICULTY LEVEL</label>
                        <select id="diffLevelSelect" onchange="window.handleDifficultySelect(event)" class="w-full bg-[#0f172a] border border-amber-500/50 text-amber-200 text-xs font-semibold rounded-2xl px-3 py-3 focus:outline-none focus:ring-2 focus:ring-amber-500 cursor-pointer">
                            <option value="1">Level 1: Very Easy</option>
                            <option value="2">Level 2: Easy</option>
                            <option value="3" selected>Level 3: Moderate</option>
                            <option value="4">Level 4: Standard</option>
                            <option value="5">Level 5: Challenging</option>
                            <option value="6">Level 6: Hard</option>
                            <option value="7">Level 7: Extreme</option>
                        </select>
                    </div>

                </div>

                <!-- SECONDARY CONTROL BAR -->
                <div class="flex flex-wrap items-center justify-between gap-3 bg-slate-900/60 p-3 rounded-2xl border border-slate-800">
                    <div class="flex items-center gap-2">
                        <span class="text-xs font-bold text-slate-300 uppercase tracking-wider"><i class="fa-solid fa-sliders text-indigo-400 mr-1"></i> MODE:</span>
                        <div class="flex items-center bg-[#0f172a] p-1 rounded-xl border border-slate-700">
                            <button onclick="window.setTypingMode('single')" id="btnModeSingle" class="px-3 py-1.5 rounded-lg text-xs font-bold text-white bg-indigo-600 transition">
                                Single Line (Enter Next)
                            </button>
                            <button onclick="window.setTypingMode('multi')" id="btnModeMulti" class="px-3 py-1.5 rounded-lg text-xs font-bold text-slate-400 hover:text-white transition">
                                Multi-Line Paragraph
                            </button>
                        </div>
                    </div>

                    <div class="flex items-center gap-2">
                        <button onclick="window.switchRandomPassage()" class="px-3.5 py-1.5 bg-slate-800 hover:bg-slate-700 text-xs font-bold text-indigo-300 rounded-xl border border-slate-700 flex items-center gap-1.5 transition">
                            <i class="fa-solid fa-shuffle"></i> Change Passage (<span id="passageCountBadge">Passage 1/10</span>)
                        </button>
                    </div>
                </div>

                <!-- TIMER & STATUS DISPLAY -->
                <div class="flex items-center justify-between">
                    <div>
                        <div class="flex items-baseline gap-3">
                            <span id="bigTimerDisplay" class="text-4xl md:text-5xl font-black font-mono-code tracking-wider text-white">01 : 00</span>
                            <span id="readyIndicator" class="inline-flex items-center gap-1.5 text-xs font-semibold text-emerald-400 bg-emerald-950/60 border border-emerald-800/60 px-2.5 py-1 rounded-full">
                                <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span> Ready
                            </span>
                        </div>
                        <p class="text-xs text-slate-400 mt-1 font-medium">Timer starts automatically when you type your first character.</p>
                    </div>

                    <div class="flex items-center gap-2">
                        <button onclick="window.resetTest()" class="px-3.5 py-2 bg-indigo-600/20 hover:bg-indigo-600/40 text-indigo-300 border border-indigo-500/40 rounded-xl text-xs font-bold flex items-center gap-2 transition">
                            <i class="fa-solid fa-rotate-right"></i> Restart Test
                        </button>
                    </div>
                </div>

                <!-- TYPING DISPLAY BOX -->
                <div class="theme-inner bg-[#0f172a] rounded-2xl border border-[#334155] p-5 md:p-6 flex flex-col gap-4 shadow-inner relative">
                    
                    <div class="flex items-center justify-between text-xs font-mono-code text-emerald-400 font-bold uppercase tracking-wider">
                        <span id="lineTrackerTag">NORMAL · LINE 1 OF 3</span>
                        <span id="typingInstructionHint" class="text-slate-400 font-sans normal-case">Type line, then press <kbd class="px-2 py-0.5 bg-slate-800 border border-slate-700 text-slate-200 rounded text-[11px]">Enter</kbd></span>
                    </div>

                    <!-- TARGET DISPLAY TEXT -->
                    <div id="targetTextDisplay" class="font-mono-code text-lg md:text-xl leading-relaxed text-slate-200 tracking-wide select-none min-h-[120px] flex flex-col gap-2 p-4 bg-slate-900/60 rounded-xl border border-slate-800/80">
                    </div>

                    <!-- INPUT FIELD -->
                    <div class="relative mt-1">
                        <input type="text" id="typingInputField" oninput="window.handleInput(event)" onkeydown="window.handleKeyDown(event)" autocomplete="off" placeholder="Start typing here to begin test..." class="w-full bg-[#1e293b] border border-[#334155] focus:border-indigo-500 text-white font-mono-code text-base md:text-lg px-4 py-3.5 rounded-xl focus:outline-none focus:ring-2 focus:ring-indigo-500/50 shadow-inner">
                    </div>

                    <div class="flex flex-wrap items-center justify-between text-xs text-slate-500 pt-1 gap-2">
                        <span id="activeModeBadge" class="flex items-center gap-1.5 text-indigo-400 font-bold"><i class="fa-solid fa-circle-check"></i> Active Practice Mode: HINDI</span>
                        <span class="text-slate-400">Owner: <strong class="text-amber-400">Amit Kumar</strong></span>
                    </div>

                </div>

            </div>

        </main>

        <footer class="border-t border-slate-800 py-4 px-6 text-center text-xs text-slate-500 flex flex-wrap justify-between items-center max-w-5xl mx-auto w-full gap-2">
            <span>© 2026 Master of the Typing · Owner & Director: <strong>Amit Kumar</strong></span>
            <span>Speed, Accuracy, 7 Difficulty Levels, Swift/Python/Modern Code & Official Certificate</span>
        </footer>

    </div>

    <!-- CUSTOM TEXT LANGUAGE MODAL -->
    <div id="customLanguageModal" class="fixed inset-0 bg-slate-950/85 backdrop-blur-md z-50 hidden flex items-center justify-center p-4">
        <div class="bg-[#1e293b] rounded-3xl max-w-md w-full p-6 shadow-2xl border border-emerald-500/50 flex flex-col gap-4">
            <div class="flex items-center justify-between">
                <h3 class="font-bold text-base text-white flex items-center gap-2"><i class="fa-solid fa-globe text-emerald-400"></i> Add Custom Text Language</h3>
                <button onclick="window.closeCustomLanguageModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <p class="text-xs text-slate-300">Enter custom language name and custom sentences to practice:</p>
            <input type="text" id="customLanguageName" placeholder="e.g. Sanskrit, Dogri, Esperanto..." class="bg-[#0f172a] border border-[#334155] text-white text-xs p-3 rounded-xl focus:outline-none">
            <textarea id="customLanguagePassage" rows="3" placeholder="Enter practice sentences separated by line breaks..." class="bg-[#0f172a] border border-[#334155] text-white text-xs p-3 rounded-xl focus:outline-none font-mono-code"></textarea>
            <button onclick="window.saveCustomLanguage()" class="bg-emerald-600 hover:bg-emerald-500 text-white font-bold py-2.5 rounded-xl text-xs">Add Language</button>
        </div>
    </div>

    <!-- CUSTOM CODING LANGUAGE MODAL -->
    <div id="customCodingModal" class="fixed inset-0 bg-slate-950/85 backdrop-blur-md z-50 hidden flex items-center justify-center p-4">
        <div class="bg-[#1e293b] rounded-3xl max-w-md w-full p-6 shadow-2xl border border-purple-500/50 flex flex-col gap-4">
            <div class="flex items-center justify-between">
                <h3 class="font-bold text-base text-white flex items-center gap-2"><i class="fa-solid fa-code text-purple-400"></i> Add Custom Coding Language / Snippet</h3>
                <button onclick="window.closeCustomCodingModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <p class="text-xs text-slate-300">Enter custom coding framework/language name and code snippet:</p>
            <input type="text" id="customCodingName" placeholder="e.g. Carbon, Nim, Q#, Haskell..." class="bg-[#0f172a] border border-[#334155] text-white text-xs p-3 rounded-xl focus:outline-none">
            <textarea id="customCodingSnippet" rows="4" placeholder="Enter code snippet lines to practice..." class="bg-[#0f172a] border border-[#334155] text-purple-200 text-xs p-3 rounded-xl focus:outline-none font-mono-code"></textarea>
            <button onclick="window.saveCustomCodingLanguage()" class="bg-purple-600 hover:bg-purple-500 text-white font-bold py-2.5 rounded-xl text-xs">Add Coding Language</button>
        </div>
    </div>

    <!-- CERTIFICATE MODAL -->
    <div id="certificateModal" class="fixed inset-0 bg-slate-950/90 backdrop-blur-md z-50 hidden flex items-center justify-center p-4 overflow-y-auto">
        <div class="bg-white text-slate-900 rounded-3xl max-w-3xl w-full p-8 shadow-2xl border-4 border-amber-500 relative flex flex-col gap-6 my-auto">
            
            <div class="border-4 border-double border-amber-600 p-6 rounded-2xl flex flex-col items-center text-center gap-4 relative bg-amber-50/20">
                
                <div class="flex justify-between items-center w-full border-b border-amber-200 pb-4">
                    <div class="flex items-center gap-2 text-indigo-900 font-black text-lg">
                        <i class="fa-solid fa-keyboard text-amber-600"></i> MASTER OF THE TYPING
                    </div>
                    <span class="text-xs font-bold uppercase tracking-widest text-amber-700 bg-amber-100 px-3 py-1 rounded-full border border-amber-300">Official Certificate</span>
                </div>

                <div class="py-2">
                    <h2 class="font-certificate text-2xl md:text-3xl text-amber-900 font-bold tracking-wider">CERTIFICATE OF TYPING PROFICIENCY</h2>
                    <p class="text-xs text-slate-600 uppercase tracking-widest mt-1">This is to certify that</p>
                </div>

                <div class="w-full border-b-2 border-slate-800 pb-2 max-w-md">
                    <input type="text" id="certStudentName" value="Candidate Typist" class="text-center font-bold text-xl md:text-2xl text-indigo-950 w-full focus:outline-none bg-transparent" placeholder="Click to enter your name">
                </div>

                <p class="text-xs md:text-sm text-slate-700 max-w-lg leading-relaxed">
                    has successfully completed the typing speed and accuracy assessment on <strong>Master of the Typing</strong> under difficulty <strong id="certDiffLabel">Level 3 (Moderate)</strong> using language <strong id="certLangLabel">Hindi</strong>.
                </p>

                <!-- STATS GRID -->
                <div class="grid grid-cols-3 gap-4 w-full max-w-lg bg-amber-100/60 p-4 rounded-xl border border-amber-300 my-2">
                    <div class="flex flex-col items-center">
                        <span class="text-[10px] text-amber-800 font-bold uppercase">NET SPEED</span>
                        <span id="certWpmVal" class="text-2xl font-black text-indigo-950">45 WPM</span>
                    </div>
                    <div class="flex flex-col items-center border-x border-amber-300">
                        <span class="text-[10px] text-amber-800 font-bold uppercase">ACCURACY</span>
                        <span id="certAccVal" class="text-2xl font-black text-emerald-700">98%</span>
                    </div>
                    <div class="flex flex-col items-center">
                        <span class="text-[10px] text-amber-800 font-bold uppercase">DURATION</span>
                        <span id="certTimeVal" class="text-2xl font-black text-slate-800">1 Min</span>
                    </div>
                </div>

                <!-- SIGNATURE & SEAL -->
                <div class="flex justify-between items-end w-full pt-6 mt-2 border-t border-amber-200">
                    <div class="text-left text-[11px]">
                        <p class="font-bold text-slate-800">Date Issued:</p>
                        <p id="certDateVal" class="text-slate-600">October 16, 2026</p>
                    </div>

                    <div class="w-20 h-20 rounded-full border-2 border-amber-600 bg-amber-50 flex items-center justify-center text-amber-700 text-xs font-bold text-center p-1 shadow-inner">
                        OFFICIAL<br>SEAL
                    </div>

                    <div class="text-right text-[11px] flex flex-col items-end">
                        <span class="font-serif italic font-bold text-lg text-indigo-950 border-b border-slate-800 px-4 pb-1 mb-1">Amit Kumar</span>
                        <p class="font-bold text-amber-900">Amit Kumar</p>
                        <p class="text-[10px] text-slate-500">Founder & Owner</p>
                    </div>
                </div>

            </div>

            <div class="flex items-center justify-between no-print pt-2">
                <button onclick="window.closeCertificateModal()" class="px-4 py-2 bg-slate-200 hover:bg-slate-300 text-slate-800 text-xs font-bold rounded-xl transition">
                    Close
                </button>
                <div class="flex items-center gap-2">
                    <button onclick="window.printCertificate()" class="px-5 py-2.5 bg-indigo-600 hover:bg-indigo-700 text-white text-xs font-bold rounded-xl shadow-lg transition flex items-center gap-2">
                        <i class="fa-solid fa-print"></i> Print / Save Certificate PDF
                    </button>
                </div>
            </div>

        </div>
    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        const passageDatabase = {
            // INDIAN LANGUAGES
            hi: [
                ["टाइपिंग गति सुधारने के लिए नियमित अभ्यास आवश्यक है।", "कंप्यूटर पर सही उंगलियों का उपयोग करके तेज़ी से टाइप करें।", "सटीकता पर ध्यान केंद्रित करें, गति अपने आप बढ़ती जाएगी।"],
                ["डिजिटल युग में सही टाइपिंग कौशल बहुत महत्वपूर्ण है।", "हर दिन केवल दस मिनट का अभ्यास आपको कुशल बना सकता है।"],
                ["भारतीय प्रौद्योगिकी क्षेत्र में हिंदी टाइपिंग का महत्व बढ़ रहा है।", "कंप्यूटर साक्षरता में गति और सटीकता दोनों की जरूरत होती है।"],
                ["सफलता पाने के लिए निरंतर प्रयास और धैर्य बेहद जरूरी है।", "गलतियों को सुधारकर ही आप एक बेहतर टाइपिस्ट बन सकते हैं।"],
                ["ज्ञान और कौशल का संगम ही मनुष्य को महान बनाता है।", "अभ्यास से ही कठिन कार्य भी सुलभ और सरल हो जाते हैं।"]
            ],
            mr: [
                ["संगणकावर वेगाने टाइप करण्यासाठी रोज सराव करणे आवश्यक आहे.", "योग्य बोटांचा वापर करून अचूकता वाढवा."],
                ["मराठी टंकलेखन कौशल्य डिजिटल क्षेत्रात अत्यंत उपयुक्त ठरते.", "नियमित सरावाने तुमचा टायपिंग वेग झपाट्याने वाढतो."]
            ],
            bn: [
                ["কম্পিউটারে দ্রুত টাইপ করার জন্য প্রতিদিন অনুশীলন প্রয়োজন।", "সঠিক আঙুল ব্যবহার করে টাইপিং গতি ও নির্ভুলতা বৃদ্ধি করুন।"],
                ["ডিজিটাল যুগে টাইপিং দক্ষতা অত্যন্ত প্রয়োজনীয় একটি দক্ষতা।", "নিয়মিত চর্চা আপনাকে একজন দক্ষ টাইপিস্ট করে তুলবে।"]
            ],
            pa: [
                ["ਕੰਪਿਊਟਰ 'ਤੇ ਤੇਜ਼ ਟਾਈਪਿੰਗ ਲਈ ਰੋਜ਼ਾਨਾ ਅਭਿਆਸ ਬਹੁਤ ਜ਼ਰੂਰੀ ਹੈ।", "ਹੀ ਉਂਗਲਾਂ ਦੀ ਵਰਤੋਂ ਨਾਲ ਆਪਣੀ ਗਤੀ ਵਧਾਓ।"]
            ],
            gu: [
                ["કમ્પ્યુટર પર ઝડપી ટાઇપિંગ માટે નિયમિત અભ્યાસ જરૂરી છે.", "સાચી આંગળીઓનો ઉપયોગ કરીને ચોકસાઈ વધારો."]
            ],
            ta: [
                ["கணினியில் வேகமாக தட்டச்சு செய்ய தினமும் பயிற்சி அவசியம்.", "சரியான விரல்களைப் பயன்படுத்தி வேகத்தை உயர்த்துங்கள்."]
            ],
            te: [
                ["కంప్యూటర్‌లో వేగంగా టైప్ చేయడానికి ప్రతిరోజూ సాధన అవసరం.", "సరైన వేళ్లను ఉపయోగించి ఖచ్చితత్వాన్ని పెంచుకోండి."]
            ],
            kn: [
                ["ಕಂಪ್ಯೂಟರ್‌ನಲ್ಲಿ ವೇಗವಾಗಿ ಟೈಪ್ ಮಾಡಲು ಪ್ರತಿದಿನ ಅಭ್ಯಾಸ ಅಗತ್ಯ.", "ಸರಿಯಾದ ಬೆರಳುಗಳನ್ನು ಬಳಸಿ ನಿಖರತೆಯನ್ನು ಹೆಚ್ಚಿಸಿ."]
            ],
            ml: [
                ["കമ്പ്യൂട്ടറിൽ വേഗത്തിൽ ടൈപ്പ് ചെയ്യാൻ ദിവസവും പരിശീലനം വേണം.", "ശരിയായ വിരലുകൾ ഉപയോഗിച്ച് കൃത്യത ഉറപ്പാക്കുക."]
            ],
            or: [
                ["କମ୍ପ୍ୟୁଟରରେ ଦ୍ରୁତ ଟାଇପିଂ ପାଇଁ ନିୟମିତ ଅଭ୍ୟାସ ଆବଶ୍ୟକ।", "ସଠିକ୍ ଅଙ୍ଗୁଳି ବ୍ୟବହାର କରି ଗତି ବୃଦ୍ଧି କରନ୍ତୁ।"]
            ],

            // WORLD LANGUAGES
            en: [
                ["Fast typing skills improve digital productivity significantly.", "Regular typing drills help build muscle memory and finger speed.", "Focus on accuracy first, and typing velocity will naturally follow."],
                ["Technology continues to shape how we communicate every day.", "Learning touch typing saves hundreds of hours every single year."],
                ["Mastering keyboard shortcuts accelerates daily office productivity.", "Maintain ergonomic posture to avoid strain during long sessions."]
            ],
            es: [
                ["La mecanografía rápida mejora significativamente la productividad digital.", "El entrenamiento constante desarrolla la memoria muscular en los dedos."],
                ["Mantener una postura ergonómica evita la fatiga durante sesiones largas.", "La precisión en el tecleo reduce los errores de edición posterior."]
            ],
            fr: [
                ["La dactylographie rapide améliore considérablement la productivité numérique.", "Un entraînement régulier permet de développer la mémoire musculaire."],
                ["Concentrez-vous sur la précision pour acquérir une vitesse naturelle.", "L'utilisation de raccourcis clavier accélère le travail quotidien."]
            ],
            de: [
                ["Schnelles Tippen verbessert die digitale Produktivität erheblich.", "Regelmäßiges Üben baut das Muskelgedächtnis für hohe Geschwindigkeit auf."],
                ["Achten Sie auf Präzision, die Tippgeschwindigkeit kommt von alleine.", "Ergonomische Haltung schützt vor Ermüdung bei langen Arbeitssitzungen."]
            ],
            ru: [
                ["Быстрая печать значительно повышает цифровую производительность.", "Регулярные упражнения развивают мышечную память пальцев."],
                ["Сфокусируйтесь на точности, и скорость придет естественным образом."]
            ],
            ar: [
                ["الكتابة السريعة على لوحة المفاتيح تزيد من الإنتاجية الرقمية بشكل كبير.", "التدريب المنتظم يساعد على بناء الذاكرة العضلية للأصابع."],
                ["ركز على الدقة أولاً وستزداد السرعة تلقائياً مع الممارسة."]
            ],
            zh: [
                ["快速打字技能显著提高数字工作效率。", "定期练习有助于建立手指的肌肉记忆。"],
                ["首先关注准确率，打字速度自然会随之提升。"]
            ],
            ja: [
                ["タイピング速度の向上はデジタル生産性を大幅に高めます。", "毎日の練習が指の筋肉記憶を構築する鍵となります。"],
                ["正確さに集中することで、自然と速度も向上の途をたどります。"]
            ],
            pt: [
                ["A dactilografia rápida aumenta significativamente a produtividade digital.", "O treino regular desenvolve a memória muscular dos dedos."]
            ],
            it: [
                ["La dattilografia veloce migliora notevolmente la produttività digitale.", "L'esercizio costante sviluppa la memoria muscolare delle dita."]
            ],
            nl: [
                ["Snel typen verhoogt de digitale productiviteit aanzienlijk.", "Regelmatig oefenen bouwt spiergeheugen op in de vingers."]
            ],
            tr: [
                ["Hızlı klavye kullanımı dijital verimliliği önemli ölçüde artırır.", "Düzenli pratik yapmak parmaklarda kas hafızası oluşturur."]
            ],

            // 🐍 PYTHON ECOSYSTEM
            python: [
                ["def calculate_wpm(characters, minutes): return round((characters / 5) / minutes)", "print('Master of the Typing - Owner: Amit Kumar')", "for i in range(10): total_score += i"],
                ["import math\ndef get_circle_area(radius): return math.pi * (radius ** 2)"],
                ["class TypistProfile:\n    def __init__(self, name, wpm): self.name = name\n        self.wpm = wpm"]
            ],
            python_django: [
                ["from django.db import models\nclass Article(models.Model):\n    title = models.CharField(max_length=200)\n    created_at = models.DateTimeField(auto_now_add=True)"],
                ["from django.shortcuts import render\ndef home_view(request):\n    return render(request, 'index.html', {'status': 'active'})"]
            ],
            python_flask: [
                ["from flask import Flask, jsonify\napp = Flask(__name__)\n@app.route('/api/stats')\ndef get_stats(): return jsonify({'wpm': 65, 'accuracy': 99})"]
            ],
            python_fastapi: [
                ["from fastapi import FastAPI\napp = FastAPI()\n@app.get('/items/{item_id}')\nasync def read_item(item_id: int): return {'item_id': item_id}"]
            ],
            python_numpy: [
                ["import numpy as np\nmatrix = np.zeros((3, 3), dtype=np.float64)\nmean_val = np.mean(matrix)"]
            ],
            python_pandas: [
                ["import pandas as pd\ndf = pd.read_csv('results.csv')\nfiltered_df = df[df['wpm'] > 50].sort_values(by='accuracy')"]
            ],
            python_pytorch: [
                ["import torch\nimport torch.nn as nn\ntensor = torch.tensor([1.0, 2.0, 3.0], requires_grad=True)\nloss = tensor.sum()"]
            ],

            // 🍎 SWIFT & APPLE ECOSYSTEM
            swift: [
                ["struct UserProfile {\n    let name: String\n    var wpmScore: Int\n}", "func performAsyncFetch() async throws -> String { return \"Data Loaded\" }"],
                ["guard let url = URL(string: \"https://api.example.com\") else { return }\nlet (data, _) = try await URLSession.shared.data(from: url)"]
            ],
            swiftui: [
                ["import SwiftUI\nstruct ContentView: View {\n    var body: some View {\n        Text(\"Master of the Typing\").font(.title).padding()\n    }\n}"],
                ["@State private var isCompleted: Bool = false\nButton(\"Start Assessment\") { isCompleted.toggle() }"]
            ],
            uikit: [
                ["import UIKit\nclass ViewController: UIViewController {\n    override func viewDidLoad() {\n        super.viewDidLoad()\n        view.backgroundColor = .systemBackground\n    }\n}"]
            ],
            combine: [
                ["import Combine\nvar cancellables = Set<AnyCancellable>()\nsubject.sink { completion in print(completion) } receiveValue: { value in print(value) }.store(in: &cancellables)"]
            ],
            objc: [
                ["#import <Foundation/Foundation.h>\n@interface Person : NSObject\n@property (nonatomic, copy) NSString *name;\n@end"]
            ],

            // 🚀 MODERN & EMERGING LANGUAGES
            rust: [
                ["fn calculate_velocity(chars: usize, time_mins: f64) -> usize { ((chars as f64 / 5.0) / time_mins) as usize }"],
                ["pub struct TypingStats {\n    pub wpm: u32,\n    pub accuracy: f32,\n}\nlet stats = TypingStats { wpm: 60, accuracy: 98.5 };"]
            ],
            golang: [
                ["package main\nimport \"fmt\"\nfunc main() { fmt.Println(\"Master of the Typing - Go Runtime\") }"],
                ["type Typist struct {\n    Name string\n    WPM  int\n}\nch := make(chan int, 10)"]
            ],
            typescript: [
                ["interface UserScore {\n    name: string;\n    wpm: number;\n    accuracy: number;\n}\nconst logScore = (user: UserScore): void => console.log(user.wpm);"]
            ],
            kotlin: [
                ["data class TypistProfile(val name: String, var wpm: Int)\nfun main() { println(\"Kotlin Android Typing Engine\") }"]
            ],
            zig: [
                ["const std = @import(\"std\");\npub fn main() !void {\n    std.debug.print(\"Master of the Typing Zig Engine\\n\", .{});\n}"]
            ],
            mojo: [
                ["fn calculate_matrix_speed() -> Float64:\n    let val: Float64 = 98.6\n    return val"]
            ],
            elixir: [
                ["defmodule TypingEngine do\n  def calculate_wpm(words, time) do\n    words / time\n  end\nend"]
            ],
            dart: [
                ["import 'package:flutter/material.dart';\nvoid main() => runApp(const MaterialApp(home: Text('Flutter Speed Test')));"]
            ],

            // 💻 CLASSICAL & ENTERPRISE
            javascript: [
                ["const calculateSpeed = (chars, mins) => Math.round((chars / 5) / mins);", "document.getElementById('headerWpm').innerText = currentWpm;"],
                ["function calculateAccuracy(typed, errors) { return Math.max(0, Math.round(((typed - errors) / typed) * 100)); }"]
            ],
            cpp: [
                ["#include <iostream>\nusing namespace std;\nint main() { cout << \"Master of the Typing!\" << endl; return 0; }"]
            ],
            csharp: [
                ["using System;\nnamespace TypingApp {\n    class Program {\n        static void Main() { Console.WriteLine(\"C# .NET 8 Engine\"); }\n    }\n}"]
            ],
            java: [
                ["public class Main {\n    public static void main(String[] args) {\n        System.out.println(\"Java Enterprise Engine\");\n    }\n}"]
            ],
            html: [
                ["<div class=\"flex items-center justify-between p-4 bg-slate-900 rounded-xl\"><h2 class=\"text-lg font-bold\">Master Typing</h2></div>"]
            ],
            css: [
                [".typing-container { display: flex; align-items: center; justify-content: center; background-color: #0f172a; }"]
            ],
            sql: [
                ["SELECT user_id, name, MAX(wpm) AS top_speed FROM user_scores WHERE accuracy >= 95 GROUP BY user_id, name ORDER BY top_speed DESC;"]
            ]
        };

        window.practiceModeType = 'normal'; // 'normal' or 'coding'
        window.currentLangKey = 'hi';
        window.currentPassageIndex = 0;
        window.activePassageList = [];
        window.currentLineIndex = 0;
        window.typingDisplayMode = 'single'; // 'single' or 'multi'
        window.currentDiffLevel = 3; // 1 to 7

        window.testActive = false;
        window.durationMinutes = 1;
        window.timeLeft = 60;
        window.timerInterval = null;
        window.totalCharsTyped = 0;
        window.mistakesCount = 0;
        window.startTime = null;

        const diffLabels = {
            1: "Level 1: Very Easy",
            2: "Level 2: Easy",
            3: "Level 3: Moderate",
            4: "Level 4: Standard",
            5: "Level 5: Challenging",
            6: "Level 6: Hard",
            7: "Level 7: Extreme"
        };

        window.handleDifficultySelect = function(e) {
            window.currentDiffLevel = parseInt(e.target.value, 10) || 3;
            window.resetTest();
        };

        window.setTheme = function(mode) {
            const body = document.getElementById('bodyRoot');
            const btnLight = document.getElementById('btnThemeLight');
            const btnDark = document.getElementById('btnThemeDark');
            const btnNight = document.getElementById('btnThemeNight');

            body.classList.remove('light-theme', 'night-shift-theme');
            btnLight.className = "px-2.5 py-1 rounded-lg text-xs text-slate-400 hover:text-white transition";
            btnDark.className = "px-2.5 py-1 rounded-lg text-xs text-slate-400 hover:text-white transition";
            btnNight.className = "px-2.5 py-1 rounded-lg text-xs text-amber-500 font-bold hover:bg-amber-950/40 transition";

            if (mode === 'light') {
                body.classList.add('light-theme');
                btnLight.className = "px-2.5 py-1 rounded-lg text-xs font-bold text-slate-900 bg-white shadow transition";
            } else if (mode === 'nightshift') {
                body.classList.add('night-shift-theme');
                btnNight.className = "px-2.5 py-1 rounded-lg text-xs font-bold text-amber-300 bg-amber-950/80 border border-amber-500/50 transition";
            } else {
                btnDark.className = "px-2.5 py-1 rounded-lg text-xs font-bold text-indigo-400 bg-slate-800 transition";
            }
        };

        window.setPracticeType = function(type) {
            window.practiceModeType = type;
            const normBtn = document.getElementById('typeNormalBtn');
            const codeBtn = document.getElementById('typeCodingBtn');
            const normSel = document.getElementById('normalLanguageSelect');
            const codeSel = document.getElementById('codingLanguageSelect');

            if (type === 'normal') {
                normBtn.className = "h-full py-1 px-2 text-xs font-bold rounded-xl bg-indigo-600 text-white transition flex items-center justify-center gap-1 shadow";
                codeBtn.className = "h-full py-1 px-2 text-xs font-bold rounded-xl text-purple-300 hover:text-white transition flex items-center justify-center gap-1";
                normSel.classList.remove('hidden');
                codeSel.classList.add('hidden');
                window.currentLangKey = normSel.value || 'hi';
            } else {
                codeBtn.className = "h-full py-1 px-2 text-xs font-bold rounded-xl bg-purple-600 text-white transition flex items-center justify-center gap-1 shadow";
                normBtn.className = "h-full py-1 px-2 text-xs font-bold rounded-xl text-indigo-300 hover:text-white transition flex items-center justify-center gap-1";
                codeSel.classList.remove('hidden');
                normSel.classList.add('hidden');
                window.currentLangKey = codeSel.value || 'python';
            }

            window.resetTest();
        };

        window.handleLanguageChange = function(e) {
            const val = e.target.value;
            if (val === 'custom_add') {
                window.openCustomLanguageModal();
                return;
            }
            window.currentLangKey = val;
            window.currentPassageIndex = 0;
            window.resetTest();
        };

        window.handleCodingModeChange = function(e) {
            const val = e.target.value;
            if (val === 'custom_code_add') {
                window.openCustomCodingModal();
                return;
            }
            window.currentLangKey = val;
            window.currentPassageIndex = 0;
            window.resetTest();
        };

        window.switchRandomPassage = function() {
            let pool = passageDatabase[window.currentLangKey] || passageDatabase['en'];
            window.currentPassageIndex = (window.currentPassageIndex + 1) % pool.length;
            window.resetTest();
        };

        function loadTextForMode() {
            let pool = passageDatabase[window.currentLangKey] || passageDatabase['hi'] || passageDatabase['en'];
            window.currentPassageIndex = window.currentPassageIndex % pool.length;
            window.activePassageList = pool[window.currentPassageIndex];

            document.getElementById('passageCountBadge').innerText = `Passage ${window.currentPassageIndex + 1}/${pool.length}`;
            window.currentLineIndex = 0;
            window.renderTypingArea();
            
            const activeBadge = document.getElementById('activeModeBadge');
            activeBadge.innerText = `Active Practice Mode: ${window.currentLangKey.toUpperCase()} (${diffLabels[window.currentDiffLevel]})`;
        }

        window.renderTypingArea = function() {
            const displayBox = document.getElementById('targetTextDisplay');
            if (!displayBox) return;
            displayBox.innerHTML = '';

            const totalLines = window.activePassageList.length;
            document.getElementById('lineTrackerTag').innerText = `${window.practiceModeType.toUpperCase()} · LINE ${window.currentLineIndex + 1} OF ${totalLines}`;

            if (window.typingDisplayMode === 'single') {
                document.getElementById('typingInstructionHint').innerHTML = `Type line, then press <kbd class="px-2 py-0.5 bg-slate-800 border border-slate-700 text-slate-200 rounded text-[11px]">Enter</kbd>`;
                const targetLine = window.activePassageList[window.currentLineIndex] || '';
                const lineDiv = document.createElement('div');
                lineDiv.className = "text-lg md:text-xl font-bold tracking-wide leading-relaxed";
                
                const typedVal = document.getElementById('typingInputField').value || '';
                
                for (let i = 0; i < targetLine.length; i++) {
                    const charSpan = document.createElement('span');
                    charSpan.innerText = targetLine[i];
                    if (i < typedVal.length) {
                        if (typedVal[i] === targetLine[i]) {
                            charSpan.className = "text-emerald-400 bg-emerald-950/40 rounded px-0.5";
                        } else {
                            charSpan.className = "text-rose-400 bg-rose-950/60 rounded px-0.5 underline decoration-rose-500";
                        }
                    } else if (i === typedVal.length) {
                        charSpan.className = "text-amber-300 bg-amber-500/20 border-b-2 border-amber-400 animate-pulse px-0.5";
                    } else {
                        charSpan.className = "text-slate-400";
                    }
                    lineDiv.appendChild(charSpan);
                }
                displayBox.appendChild(lineDiv);
            } else {
                document.getElementById('typingInstructionHint').innerHTML = `Type paragraph text line by line`;
                window.activePassageList.forEach((lineText, idx) => {
                    const lineDiv = document.createElement('div');
                    lineDiv.className = idx === window.currentLineIndex ? "text-slate-100 font-bold bg-slate-800/80 p-2 rounded-lg border border-indigo-500/40" : "text-slate-500 opacity-60 p-1";
                    lineDiv.innerText = lineText;
                    displayBox.appendChild(lineDiv);
                });
            }
        };

        window.handleInput = function(e) {
            if (!window.testActive) {
                window.startTimer();
            }

            window.totalCharsTyped++;
            window.calculateMetrics();
            window.renderTypingArea();
        };

        window.handleKeyDown = function(e) {
            if (e.key === 'Enter') {
                e.preventDefault();
                const currentInput = document.getElementById('typingInputField').value;
                const targetLine = window.activePassageList[window.currentLineIndex] || '';

                if (currentInput.length >= Math.floor(targetLine.length * 0.4)) {
                    window.currentLineIndex++;
                    if (window.currentLineIndex >= window.activePassageList.length) {
                        window.finishTest();
                    } else {
                        document.getElementById('typingInputField').value = '';
                        window.renderTypingArea();
                    }
                }
            }
        };

        window.updateDuration = function() {
            const sel = document.getElementById('testLengthSelect');
            window.durationMinutes = parseInt(sel.value, 10) || 1;
            window.resetTest();
        };

        window.setTypingMode = function(mode) {
            window.typingDisplayMode = mode;
            const btnSingle = document.getElementById('btnModeSingle');
            const btnMulti = document.getElementById('btnModeMulti');

            if (mode === 'single') {
                btnSingle.className = "px-3 py-1.5 rounded-lg text-xs font-bold text-white bg-indigo-600 transition";
                btnMulti.className = "px-3 py-1.5 rounded-lg text-xs font-bold text-slate-400 hover:text-white transition";
            } else {
                btnMulti.className = "px-3 py-1.5 rounded-lg text-xs font-bold text-white bg-indigo-600 transition";
                btnSingle.className = "px-3 py-1.5 rounded-lg text-xs font-bold text-slate-400 hover:text-white transition";
            }
            window.renderTypingArea();
        };

        window.startTimer = function() {
            window.testActive = true;
            window.startTime = new Date();
            document.getElementById('readyIndicator').innerHTML = `<span class="w-2 h-2 rounded-full bg-amber-400 animate-ping"></span> Typing in Progress...`;
            
            window.timerInterval = setInterval(() => {
                window.timeLeft--;
                document.getElementById('bigTimerDisplay').innerText = window.formatTimer(window.timeLeft);

                window.calculateMetrics();

                if (window.timeLeft <= 0) {
                    clearInterval(window.timerInterval);
                    window.finishTest();
                }
            }, 1000);
        };

        window.calculateMetrics = function() {
            if (!window.startTime) return;
            const elapsedMins = Math.max(0.01, (window.durationMinutes * 60 - window.timeLeft) / 60);
            const typedVal = document.getElementById('typingInputField').value;
            const wordsTyped = (window.totalCharsTyped + typedVal.length) / 5;
            const wpm = Math.max(0, Math.round(wordsTyped / elapsedMins));

            document.getElementById('headerWpm').innerText = wpm;
            document.getElementById('headerAcc').innerText = 98;
        };

        window.finishTest = function() {
            window.testActive = false;
            if (window.timerInterval) clearInterval(window.timerInterval);

            const finalWpm = parseInt(document.getElementById('headerWpm').innerText, 10) || 0;

            if (typeof confetti === 'function' && finalWpm > 0) {
                confetti({ particleCount: 120, spread: 80, origin: { y: 0.6 } });
            }

            window.openCertificateModal(finalWpm, 98);
        };

        window.resetTest = function() {
            if (window.timerInterval) clearInterval(window.timerInterval);
            window.testActive = false;
            window.timeLeft = window.durationMinutes * 60;
            window.totalCharsTyped = 0;
            window.mistakesCount = 0;
            window.startTime = null;

            document.getElementById('bigTimerDisplay').innerText = window.formatTimer(window.timeLeft);
            document.getElementById('headerWpm').innerText = '0';
            document.getElementById('headerAcc').innerText = '100';
            document.getElementById('readyIndicator').innerHTML = `<span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span> Ready`;
            
            const inputField = document.getElementById('typingInputField');
            if (inputField) inputField.value = '';

            loadTextForMode();
        };

        window.formatTimer = function(seconds) {
            const m = Math.floor(seconds / 60);
            const s = seconds % 60;
            return `${m < 10 ? '0' + m : m} : ${s < 10 ? '0' + s : s}`;
        };

        window.openCustomLanguageModal = function() { document.getElementById('customLanguageModal').classList.remove('hidden'); };
        window.closeCustomLanguageModal = function() { 
            document.getElementById('customLanguageModal').classList.add('hidden'); 
            document.getElementById('normalLanguageSelect').value = window.currentLangKey;
        };

        window.openCustomCodingModal = function() { document.getElementById('customCodingModal').classList.remove('hidden'); };
        window.closeCustomCodingModal = function() { 
            document.getElementById('customCodingModal').classList.add('hidden'); 
            document.getElementById('codingLanguageSelect').value = window.currentLangKey;
        };

        window.openCertificateModal = function(wpm, acc) {
            document.getElementById('certWpmVal').innerText = `${wpm} WPM`;
            document.getElementById('certAccVal').innerText = `${acc}%`;
            document.getElementById('certTimeVal').innerText = `${window.durationMinutes} Min`;
            document.getElementById('certDiffLabel').innerText = diffLabels[window.currentDiffLevel];
            document.getElementById('certLangLabel').innerText = window.currentLangKey.toUpperCase();
            document.getElementById('certDateVal').innerText = new Date().toLocaleDateString('en-US', { year: 'numeric', month: 'long', day: 'numeric' });
            
            document.getElementById('certificateModal').classList.remove('hidden');
        };

        window.closeCertificateModal = function() {
            document.getElementById('certificateModal').classList.add('hidden');
            window.resetTest();
        };

        window.printCertificate = function() {
            window.print();
        };

        window.saveCustomLanguage = function() {
            const langName = document.getElementById('customLanguageName').value.trim();
            const passageRaw = document.getElementById('customLanguagePassage').value.trim();
            if (!langName) return;
            
            const lines = passageRaw ? passageRaw.split('\n').filter(l => l.trim().length > 0) : [`Practice typing in ${langName} with speed and accuracy.`];
            const key = langName.toLowerCase().replace(/\s+/g, '_');
            
            passageDatabase[key] = [lines];

            const sel = document.getElementById('normalLanguageSelect');
            const opt = document.createElement('option');
            opt.value = key;
            opt.innerText = langName;
            sel.appendChild(opt);
            sel.value = key;
            
            window.currentLangKey = key;
            window.closeCustomLanguageModal();
            window.resetTest();
        };

        window.saveCustomCodingLanguage = function() {
            const codeName = document.getElementById('customCodingName').value.trim();
            const snippetRaw = document.getElementById('customCodingSnippet').value.trim();
            if (!codeName) return;

            const lines = snippetRaw ? snippetRaw.split('\n').filter(l => l.trim().length > 0) : [`// Custom snippet for ${codeName}\nconsole.log('Custom Code Engine Active');`];
            const key = codeName.toLowerCase().replace(/\s+/g, '_');

            passageDatabase[key] = [lines];

            const sel = document.getElementById('codingLanguageSelect');
            const opt = document.createElement('option');
            opt.value = key;
            opt.innerText = codeName;
            sel.appendChild(opt);
            sel.value = key;

            window.currentLangKey = key;
            window.closeCustomCodingModal();
            window.resetTest();
        };

        // Initialize on DOM load
        window.addEventListener('DOMContentLoaded', () => {
            window.setTheme('dark');
            window.setPracticeType('normal');
        });
    </script>
</body>
</html>
    <!-- LOGIN / PROFILE MODAL -->
    <div id="loginModal" class="fixed inset-0 bg-slate-950/85 backdrop-blur-md z-50 hidden flex items-center justify-center p-4">
        <div class="bg-[#1e293b] rounded-3xl max-w-md w-full p-6 shadow-2xl border border-indigo-500/50 flex flex-col gap-4">
            <div class="flex items-center justify-between border-b border-slate-800 pb-3">
                <h3 class="font-bold text-base text-white flex items-center gap-2"><i class="fa-solid fa-user-gear text-indigo-400"></i> User Profile & Account</h3>
                <button onclick="window.closeLoginModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            
            <div class="flex flex-col gap-3">
                <div>
                    <label class="text-[11px] font-bold text-slate-400 uppercase mb-1 block">Full Name</label>
                    <input type="text" id="inputUserName" placeholder="Enter your full name" class="w-full bg-[#0f172a] border border-[#334155] text-white text-xs p-3 rounded-xl focus:outline-none focus:border-indigo-500">
                </div>
                <div>
                    <label class="text-[11px] font-bold text-slate-400 uppercase mb-1 block">Email Address (Required for Certificate)</label>
                    <input type="email" id="inputUserEmail" placeholder="yourname@example.com" class="w-full bg-[#0f172a] border border-[#334155] text-white text-xs p-3 rounded-xl focus:outline-none focus:border-indigo-500">
                </div>
                <div>
                    <label class="text-[11px] font-bold text-slate-400 uppercase mb-1 block">Physical Address / City (Optional for Certificate)</label>
                    <input type="text" id="inputUserAddress" placeholder="e.g. New Delhi, India" class="w-full bg-[#0f172a] border border-[#334155] text-white text-xs p-3 rounded-xl focus:outline-none focus:border-indigo-500">
                </div>
            </div>

            <button onclick="window.saveUserProfile()" class="bg-indigo-600 hover:bg-indigo-500 text-white font-bold py-3 rounded-xl text-xs shadow-lg transition">
                Save & Continue
            </button>
        </div>
    </div>

    <!-- SUBSCRIPTION PAYWALL MODAL (₹30/MONTH FOR CODING PRACTICE) -->
    <div id="subscriptionModal" class="fixed inset-0 bg-slate-950/90 backdrop-blur-md z-50 hidden flex items-center justify-center p-4">
        <div class="bg-[#1e293b] rounded-3xl max-w-md w-full p-6 shadow-2xl border-2 border-amber-500 flex flex-col gap-5 text-center relative">
            <button onclick="window.closeSubModal()" class="absolute top-4 right-4 text-slate-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            
            <div class="w-16 h-16 bg-amber-500/20 text-amber-400 border border-amber-500/40 rounded-full flex items-center justify-center text-3xl mx-auto mt-2">
                <i class="fa-solid fa-crown"></i>
            </div>

            <div>
                <span class="bg-amber-500/20 text-amber-300 text-[10px] font-bold uppercase tracking-widest px-3 py-1 rounded-full border border-amber-500/30">1-Month Free Trial Ended</span>
                <h3 class="text-2xl font-black text-white mt-2">Coding Mode Subscription</h3>
                <p class="text-xs text-slate-300 mt-1 leading-relaxed">
                    Your 30-day free trial for Coding Practice has expired. Subscribe to unlock unlimited Swift, Python, C++, and custom coding modules + VIP Certificates.
                </p>
            </div>

            <div class="bg-[#0f172a] p-4 rounded-2xl border border-slate-800 flex items-center justify-between">
                <div class="text-left">
                    <p class="text-xs text-slate-400 font-bold">Coding Plan</p>
                    <p class="text-lg font-extrabold text-amber-400">₹30 <span class="text-xs font-normal text-slate-400">/ Month (INR)</span></p>
                </div>
                <span class="text-emerald-400 text-xs font-bold bg-emerald-950/60 px-2.5 py-1 rounded-lg border border-emerald-800/60">Cancel Anytime</span>
            </div>

            <button onclick="window.processPayment()" class="w-full bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-400 hover:to-amber-500 text-slate-950 font-black py-3.5 rounded-2xl text-sm shadow-xl transition flex items-center justify-center gap-2">
                <i class="fa-solid fa-bolt"></i> Pay ₹30 / Month Now
            </button>
        </div>
    </div>

    <!-- CUSTOM TEXT LANGUAGE MODAL (NO PASSAGE TEXTAREA, AUTO GENERATED) -->
    <div id="customLanguageModal" class="fixed inset-0 bg-slate-950/85 backdrop-blur-md z-50 hidden flex items-center justify-center p-4">
        <div class="bg-[#1e293b] rounded-3xl max-w-md w-full p-6 shadow-2xl border border-emerald-500/50 flex flex-col gap-4">
            <div class="flex items-center justify-between">
                <h3 class="font-bold text-base text-white flex items-center gap-2"><i class="fa-solid fa-globe text-emerald-400"></i> Add Custom Text Language</h3>
                <button onclick="window.closeCustomLanguageModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <p class="text-xs text-slate-300">Enter the name of the language you wish to practice. Practice passages will be generated automatically for you!</p>
            <input type="text" id="customLanguageName" placeholder="e.g. Sanskrit, Dogri, Latin..." class="bg-[#0f172a] border border-[#334155] text-white text-xs p-3.5 rounded-xl focus:outline-none focus:border-emerald-500">
            <button onclick="window.saveCustomLanguage()" class="bg-emerald-600 hover:bg-emerald-500 text-white font-bold py-3 rounded-xl text-xs shadow-lg transition">
                + Add Language & Auto-Generate Practice
            </button>
        </div>
    </div>

    <!-- CUSTOM CODING LANGUAGE MODAL (NO CODE SNIPPET TEXTAREA, AUTO GENERATED) -->
    <div id="customCodingModal" class="fixed inset-0 bg-slate-950/85 backdrop-blur-md z-50 hidden flex items-center justify-center p-4">
        <div class="bg-[#1e293b] rounded-3xl max-w-md w-full p-6 shadow-2xl border border-purple-500/50 flex flex-col gap-4">
            <div class="flex items-center justify-between">
                <h3 class="font-bold text-base text-white flex items-center gap-2"><i class="fa-solid fa-code text-purple-400"></i> Add Custom Coding Framework</h3>
                <button onclick="window.closeCustomCodingModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
            </div>
            <p class="text-xs text-slate-300">Enter the framework or programming language name. Modern code snippets will be automatically structured for practice!</p>
            <input type="text" id="customCodingName" placeholder="e.g. Carbon, Nim, Haskell, Q#..." class="bg-[#0f172a] border border-[#334155] text-white text-xs p-3.5 rounded-xl focus:outline-none focus:border-purple-500 font-mono-code">
            <button onclick="window.saveCustomCodingLanguage()" class="bg-purple-600 hover:bg-purple-500 text-white font-bold py-3 rounded-xl text-xs shadow-lg transition">
                + Add Code & Auto-Generate Snippets
            </button>
        </div>
    </div>

    <!-- TIERED CERTIFICATE MODAL (BRONZE, SILVER, GOLD & PRO CODING) -->
    <div id="certificateModal" class="fixed inset-0 bg-slate-950/90 backdrop-blur-md z-50 hidden flex items-center justify-center p-4 overflow-y-auto">
        <div id="certFrameContainer" class="bg-white text-slate-900 rounded-3xl max-w-3xl w-full p-8 shadow-2xl border-4 border-amber-500 relative flex flex-col gap-6 my-auto">
            
            <div id="certBorderBox" class="border-4 border-double border-amber-600 p-6 rounded-2xl flex flex-col items-center text-center gap-4 relative bg-amber-50/20">
                
                <div class="flex justify-between items-center w-full border-b border-amber-200 pb-3">
                    <div class="flex items-center gap-2 text-indigo-900 font-black text-lg">
                        <i class="fa-solid fa-keyboard text-amber-600"></i> MASTER OF THE TYPING
                    </div>
                    <span id="certBadgeTag" class="text-xs font-black uppercase tracking-widest text-amber-800 bg-amber-200 px-3.5 py-1 rounded-full border border-amber-400 shadow-sm">
                        GOLD CERTIFICATE
                    </span>
                </div>

                <div class="py-1">
                    <h2 id="certTitleText" class="font-certificate text-2xl md:text-3xl text-amber-900 font-bold tracking-wider">CERTIFICATE OF TYPING PROFICIENCY</h2>
                    <p class="text-xs text-slate-600 uppercase tracking-widest mt-1">This is officially awarded to</p>
                </div>

                <!-- USER DETAILS BOX -->
                <div class="flex flex-col items-center gap-1 w-full max-w-lg">
                    <h3 id="certStudentName" class="font-bold text-2xl text-indigo-950 border-b-2 border-slate-800 px-6 pb-1">Candidate Typist</h3>
                    <p id="certStudentEmail" class="text-xs font-semibold text-slate-600">Email: user@example.com</p>
                    <p id="certStudentAddress" class="text-[11px] text-slate-500 italic hidden">Address: New Delhi, India</p>
                </div>

                <p class="text-xs md:text-sm text-slate-700 max-w-lg leading-relaxed">
                    for demonstrating exceptional typing skills in <strong id="certLangLabel">Hindi</strong> under <strong id="certDiffLabel">Level 3 (Moderate)</strong> with the performance metrics recorded below.
                </p>

                <!-- STATS GRID -->
                <div class="grid grid-cols-3 gap-4 w-full max-w-lg bg-amber-100/60 p-4 rounded-xl border border-amber-300 my-1">
                    <div class="flex flex-col items-center">
                        <span class="text-[10px] text-amber-800 font-bold uppercase">NET SPEED</span>
                        <span id="certWpmVal" class="text-2xl font-black text-indigo-950">45 WPM</span>
                    </div>
                    <div class="flex flex-col items-center border-x border-amber-300">
                        <span class="text-[10px] text-amber-800 font-bold uppercase">ACCURACY</span>
                        <span id="certAccVal" class="text-2xl font-black text-emerald-700">98%</span>
                    </div>
                    <div class="flex flex-col items-center">
                        <span class="text-[10px] text-amber-800 font-bold uppercase">TIER LEVEL</span>
                        <span id="certTierRank" class="text-2xl font-black text-amber-700">GOLD</span>
                    </div>
                </div>

                <!-- SIGNATURE, OWNER & SEAL -->
                <div class="flex justify-between items-end w-full pt-4 border-t border-amber-200">
                    <div class="text-left text-[11px]">
                        <p class="font-bold text-slate-800">Date Issued:</p>
                        <p id="certDateVal" class="text-slate-600">October 16, 2026</p>
                    </div>

                    <div id="certSealCircle" class="w-20 h-20 rounded-full border-2 border-amber-600 bg-amber-100/80 flex items-center justify-center text-amber-900 text-[10px] font-black text-center p-1 shadow-inner">
                        OFFICIAL<br>VERIFIED<br>SEAL
                    </div>

                    <div class="text-right text-[11px] flex flex-col items-end">
                        <span class="font-serif italic font-bold text-lg text-indigo-950 border-b border-slate-800 px-4 pb-0.5 mb-0.5">Amit Kumar</span>
                        <p class="font-bold text-amber-900">Owner: Amit Kumar</p>
                        <p class="text-[10px] text-slate-500">Founder & Director · Master of the Typing</p>
                    </div>
                </div>

            </div>

            <div class="flex items-center justify-between no-print pt-1">
                <button onclick="window.closeCertificateModal()" class="px-4 py-2 bg-slate-200 hover:bg-slate-300 text-slate-800 text-xs font-bold rounded-xl transition">
                    Close
                </button>
                <div class="flex items-center gap-2">
                    <button onclick="window.printCertificate()" class="px-5 py-2.5 bg-indigo-600 hover:bg-indigo-700 text-white text-xs font-bold rounded-xl shadow-lg transition flex items-center gap-2">
                        <i class="fa-solid fa-print"></i> Print / Download PDF Certificate
                    </button>
                </div>
            </div>

        </div>
    </div>

    <!-- JAVASCRIPT LOGIC UPDATES -->
    <script>
        // User Profile & Subscription State
        window.userProfile = {
            name: "Candidate Typist",
            email: "user@example.com",
            address: "",
            isLoggedIn: false,
            trialStartDate: Date.now(), // 30-day trial timer
            isPaidSubscribed: false
        };

        <!-- ... existing passageDatabase code ... -->

        window.saveUserProfile = function() {
            const name = document.getElementById('inputUserName').value.trim();
            const email = document.getElementById('inputUserEmail').value.trim();
            const address = document.getElementById('inputUserAddress').value.trim();

            if (!email) {
                alert("Please enter a valid email address.");
                return;
            }

            window.userProfile.name = name || "Candidate Typist";
            window.userProfile.email = email;
            window.userProfile.address = address;
            window.userProfile.isLoggedIn = true;

            document.getElementById('userBadgeName').innerText = window.userProfile.name;
            document.getElementById('userBadgeEmail').innerText = window.userProfile.email;
            document.getElementById('loginBtn').classList.add('hidden');
            document.getElementById('userInfoBadge').classList.remove('hidden');

            window.closeLoginModal();
        };

        window.openLoginModal = function() { document.getElementById('loginModal').classList.remove('hidden'); };
        window.closeLoginModal = function() { document.getElementById('loginModal').classList.add('hidden'); };

        window.checkCodingSubscription = function() {
            if (window.userProfile.isPaidSubscribed) return true;
            
            // Calculate 30 Days Free Trial
            const daysPassed = (Date.now() - window.userProfile.trialStartDate) / (1000 * 60 * 60 * 24);
            if (daysPassed > 30) {
                document.getElementById('subscriptionModal').classList.remove('hidden');
                return false;
            }
            return true;
        };

        window.closeSubModal = function() { document.getElementById('subscriptionModal').classList.add('hidden'); };

        window.processPayment = function() {
            window.userProfile.isPaidSubscribed = true;
            document.getElementById('subBadge').innerText = "PRO MEMBER (₹30/MO)";
            document.getElementById('subBadge').className = "bg-emerald-500/20 text-emerald-300 text-[9px] font-bold px-1.5 py-0.5 rounded border border-emerald-500/40 ml-1";
            window.closeSubModal();
            alert("Payment Successful! ₹30/month subscription activated. You now have full access to Coding Practice & Pro Certificates!");
        };

        // AUTO GENERATED TEXT/CODE FOR CUSTOM LANGUAGES (NO TEXTAREA REQUIRED)
        window.saveCustomLanguage = function() {
            const langName = document.getElementById('customLanguageName').value.trim();
            if (!langName) return;

            const key = langName.toLowerCase().replace(/\s+/g, '_');
            
            // Automatically generate practice sentences for this language name
            passageDatabase[key] = [
                [
                    `Welcome to typing practice for ${langName}.`,
                    `Consistent daily practice in ${langName} increases finger agility and precision.`,
                    `Focus on accurate keystrokes in ${langName} to master high speed.`
                ],
                [
                    `Digital communication in ${langName} opens new horizons.`,
                    `Speed and precision in ${langName} empower your technical workflow.`
                ]
            ];

            const sel = document.getElementById('normalLanguageSelect');
            const opt = document.createElement('option');
            opt.value = key;
            opt.innerText = `${langName} (Auto Generated)`;
            sel.appendChild(opt);
            sel.value = key;

            window.currentLangKey = key;
            window.closeCustomLanguageModal();
            window.resetTest();
        };

        window.saveCustomCodingLanguage = function() {
            const codeName = document.getElementById('customCodingName').value.trim();
            if (!codeName) return;

            const key = codeName.toLowerCase().replace(/\s+/g, '_');

            // Automatically generate modern code snippets for this custom coding framework
            passageDatabase[key] = [
                [
                    `// ${codeName} Auto-Generated Practice Module`,
                    `function execute${codeName.replace(/[^a-zA-Z]/g, '')}Pipeline(data) {`,
                    `    return data.filter(item => item.isValid).map(item => item.process());`,
                    `}`
                ],
                [
                    `class ${codeName.replace(/[^a-zA-Z]/g, '')}Service {`,
                    `    constructor(config) { this.config = config; }`,
                    `}`
                ]
            ];

            const sel = document.getElementById('codingLanguageSelect');
            const opt = document.createElement('option');
            opt.value = key;
            opt.innerText = `${codeName} (Auto Generated Code)`;
            sel.appendChild(opt);
            sel.value = key;

            window.currentLangKey = key;
            window.closeCustomCodingModal();
            window.resetTest();
        };

        // OVERRIDE setPracticeType to check 1-Month Free Trial / ₹30 Sub
        const origSetPracticeType = window.setPracticeType;
        window.setPracticeType = function(type) {
            if (type === 'coding') {
                if (!window.checkCodingSubscription()) {
                    return;
                }
            }
            origSetPracticeType(type);
        };

        // TIERED CERTIFICATE GENERATOR (BRONZE > 30, SILVER > 40, GOLD > 50 & VIP PRO FOR CODING)
        window.openCertificateModal = function(wpm, acc) {
            if (!window.userProfile.isLoggedIn) {
                // Auto prompt login if not done yet
                window.openLoginModal();
            }

            // Determine Tier
            let tier = "Participant";
            let badgeText = "PARTICIPANT CERTIFICATE";
            let sealColor = "border-slate-400 text-slate-700 bg-slate-100";

            if (wpm >= 50) {
                tier = "GOLD";
                badgeText = "🥇 GOLD TIER CERTIFICATE";
                sealColor = "border-amber-500 text-amber-900 bg-amber-100";
            } else if (wpm >= 40) {
                tier = "SILVER";
                badgeText = "🥈 SILVER TIER CERTIFICATE";
                sealColor = "border-slate-400 text-slate-800 bg-slate-200";
            } else if (wpm >= 30) {
                tier = "BRONZE";
                badgeText = "🥉 BRONZE TIER CERTIFICATE";
                sealColor = "border-amber-700 text-amber-900 bg-amber-200/60";
            }

            const isCodingOrSub = window.practiceModeType === 'coding' || window.userProfile.isPaidSubscribed;
            if (isCodingOrSub) {
                badgeText = `💎 PRO / VIP ${tier} CERTIFICATE (₹30 SUBSCRIBED)`;
            }

            document.getElementById('certBadgeTag').innerText = badgeText;
            document.getElementById('certTierRank').innerText = tier;
            document.getElementById('certWpmVal').innerText = `${wpm} WPM`;
            document.getElementById('certAccVal').innerText = `${acc}%`;
            document.getElementById('certDiffLabel').innerText = diffLabels[window.currentDiffLevel];
            document.getElementById('certLangLabel').innerText = window.currentLangKey.toUpperCase();
            
            document.getElementById('certStudentName').innerText = window.userProfile.name;
            document.getElementById('certStudentEmail').innerText = `Email: ${window.userProfile.email}`;

            const addrElem = document.getElementById('certStudentAddress');
            if (window.userProfile.address) {
                addrElem.innerText = `Address: ${window.userProfile.address}`;
                addrElem.classList.remove('hidden');
            } else {
                addrElem.classList.add('hidden');
            }

            document.getElementById('certDateVal').innerText = new Date().toLocaleDateString('en-US', { year: 'numeric', month: 'long', day: 'numeric' });
            
            document.getElementById('certificateModal').classList.remove('hidden');
        };

        <!-- ... existing initializers ... -->
    </script>
</body>
</html>