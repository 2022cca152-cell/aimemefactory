# aimemefactory
This is a korean-simple-ai-meme-factory
<!DOCTYPE html>
<html lang="ko" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>AI 밈 팩토리 - Z세대 짤 생성기 & AI 캡션 헬퍼</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome CDN -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts (Impact & Black Han Sans) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Black+Han+Sans&family=Impact&family=Pretendard:wght@400;700;900&display=swap" rel="stylesheet">
    <!-- Canvas Confetti -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        y2k: {
                            neonPink: '#ff007f',
                            neonLime: '#39ff14',
                            neonPurple: '#a100ff',
                            neonCyan: '#00f0ff',
                            neonYellow: '#ffe600',
                            bgDark: '#0a0915',
                            cardDark: '#16132b',
                        }
                    },
                    fontFamily: {
                        impact: ['Impact', 'Black Han Sans', 'sans-serif'],
                        sans: ['Pretendard', 'sans-serif'],
                        blackhan: ['Black Han Sans', 'sans-serif']
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom CSS & Cyber-Kitsch Effects */
        body {
            font-family: 'Pretendard', sans-serif;
            background-color: #0a0915;
            color: #ffffff;
            overflow-x: hidden;
        }

        .font-meme {
            font-family: 'Impact', 'Black Han Sans', sans-serif;
            letter-spacing: 0.5px;
        }

        .neon-border-pink {
            border: 2px solid #ff007f;
            box-shadow: 0 0 15px rgba(255, 0, 127, 0.4);
        }

        .neon-border-cyan {
            border: 2px solid #00f0ff;
            box-shadow: 0 0 15px rgba(0, 240, 255, 0.4);
        }

        .neon-text-lime {
            color: #39ff14;
            text-shadow: 0 0 8px rgba(57, 255, 20, 0.8);
        }

        .glass-panel {
            background: rgba(22, 19, 43, 0.85);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.12);
        }

        /* Y2K Glowing Grid Animation */
        .bg-grid {
            background-image: linear-gradient(to right, rgba(255, 0, 127, 0.05) 1px, transparent 1px),
                              linear-gradient(to bottom, rgba(0, 240, 255, 0.05) 1px, transparent 1px);
            background-size: 30px 30px;
        }

        /* Canvas Scrollbar & Layout adjustments */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #0a0915;
        }
        ::-webkit-scrollbar-thumb {
            background: #ff007f;
            border-radius: 4px;
        }

        /* Pulse glow for AI Button */
        @keyframes pulse-glow {
            0%, 100% { box-shadow: 0 0 15px #a100ff, 0 0 30px #ff007f; }
            50% { box-shadow: 0 0 25px #ff007f, 0 0 45px #00f0ff; }
        }
        .ai-pulse-btn {
            animation: pulse-glow 3s infinite ease-in-out;
        }
    </style>
</head>
<body class="bg-y2k-bgDark min-h-screen bg-grid flex flex-col selection:bg-y2k-neonPink selection:text-black">

    <header class="sticky top-0 z-50 glass-panel border-b border-white/10 px-4 py-3">
        <div class="max-w-6xl mx-auto flex items-center justify-between">
            <a href="#" class="flex items-center gap-2 group">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-y2k-neonPink via-y2k-neonPurple to-y2k-neonCyan p-0.5 transform group-hover:rotate-6 transition-transform">
                    <div class="w-full h-full bg-y2k-bgDark rounded-[10px] flex items-center justify-center font-black text-xl text-y2k-neonLime">
                        🤪
                    </div>
                </div>
                <div>
                    <h1 class="font-black font-blackhan text-xl tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-y2k-neonPink via-y2k-neonYellow to-y2k-neonCyan">
                        AI MEME FACTORY
                    </h1>
                    <p class="text-[10px] font-bold text-y2k-neonCyan tracking-widest uppercase">Gen-Z Viral Meme Lab</p>
                </div>
            </a>

            <div class="flex items-center gap-2">
                <button onclick="scrollToStudio()" class="px-3.5 py-1.5 rounded-xl bg-y2k-neonPink hover:bg-pink-600 text-black font-extrabold text-xs shadow-lg transition-all flex items-center gap-1.5">
                    <i class="fa-solid fa-wand-magic-sparkles"></i>
                    <span>짤 만들기</span>
                </button>
                <button onclick="scrollToFeed()" class="px-3 py-1.5 rounded-xl bg-white/10 hover:bg-white/20 text-white font-bold text-xs transition-all hidden sm:flex items-center gap-1">
                    <i class="fa-solid fa-fire text-y2k-neonYellow"></i>
                    <span>인기 밈</span>
                </button>
            </div>
        </div>
    </header>

    <main class="flex-grow max-w-6xl w-full mx-auto px-3 sm:px-6 py-6 space-y-8">

        <!-- STUDIO SECTION -->
        <section id="studio-section" class="space-y-6">
            
            <div class="text-center space-y-2">
                <span class="inline-block px-3 py-1 rounded-full bg-y2k-neonPurple/20 border border-y2k-neonPurple text-y2k-neonLime text-xs font-bold uppercase tracking-wider">
                    ⚡ 10초 만에 킹받는 짤 완성
                </span>
                <h2 class="text-2xl sm:text-4xl font-black font-blackhan tracking-wide">
                    Z세대 전용 <span class="text-y2k-neonPink">AI 밈 생성기</span>
                </h2>
                <p class="text-xs sm:text-sm text-slate-400">
                    원하는 템플릿을 고르고, AI 캡션 도우미 버튼을 눌러 센스 넘치는 드립을 완성해보세요!
                </p>
            </div>

            <!-- Studio Main Canvas & Controls Grid -->
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-start">
                
                <!-- LEFT: Canvas Preview Container (lg:col-span-7) -->
                <div class="lg:col-span-7 glass-panel rounded-3xl p-4 sm:p-6 border border-white/10 space-y-4">
                    
                    <div class="flex items-center justify-between text-xs text-slate-400">
                        <span class="font-bold flex items-center gap-1 text-y2k-neonCyan">
                            <i class="fa-solid fa-display"></i> 캔버스 실시간 미리보기
                        </span>
                        <span class="text-[11px] bg-white/5 px-2.5 py-1 rounded-full border border-white/10">
                            스프라이트/스티커 드래그 가능
                        </span>
                    </div>

                    <!-- Canvas Wrapper -->
                    <div class="relative w-full aspect-square bg-black/60 rounded-2xl border-2 border-dashed border-white/20 overflow-hidden flex items-center justify-center group" id="canvas-wrapper">
                        <canvas id="memeCanvas" class="max-w-full max-h-full object-contain cursor-crosshair"></canvas>
                        
                        <!-- Overlay loading screen -->
                        <div id="canvas-loading" class="absolute inset-0 bg-y2k-bgDark/80 backdrop-blur-sm flex flex-col items-center justify-center gap-3 hidden z-30">
                            <i class="fa-solid fa-circle-notch fa-spin text-3xl text-y2k-neonPink"></i>
                            <span class="text-xs font-bold text-y2k-neonCyan">AI가 센스있는 드립 생성 중...</span>
                        </div>
                    </div>

                    <!-- Export & Quick Actions -->
                    <div class="grid grid-cols-2 sm:grid-cols-3 gap-2 pt-2">
                        <button onclick="downloadMeme()" class="col-span-2 sm:col-span-1 px-4 py-3 rounded-2xl bg-gradient-to-r from-y2k-neonPink to-y2k-neonPurple hover:opacity-95 text-black font-extrabold text-xs sm:text-sm shadow-xl transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-download text-base"></i>
                            <span>짤 다운로드</span>
                        </button>

                        <button onclick="shareMeme()" class="px-4 py-3 rounded-2xl bg-y2k-neonCyan/20 hover:bg-y2k-neonCyan/30 border border-y2k-neonCyan text-y2k-neonCyan font-bold text-xs sm:text-sm transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-share-nodes"></i>
                            <span>공유하기</span>
                        </button>

                        <button onclick="postToFeed()" class="px-4 py-3 rounded-2xl bg-y2k-neonYellow/20 hover:bg-y2k-neonYellow/30 border border-y2k-neonYellow text-y2k-neonYellow font-bold text-xs sm:text-sm transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-paper-plane"></i>
                            <span>피드에 자랑</span>
                        </button>
                    </div>

                </div>

                <!-- RIGHT: Controls Panel (lg:col-span-5) -->
                <div class="lg:col-span-5 space-y-5">
                    
                    <!-- AI Caption Generator Panel -->
                    <div class="glass-panel rounded-3xl p-5 border border-y2k-neonPurple shadow-xl space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs font-extrabold text-y2k-neonPink uppercase tracking-wider flex items-center gap-1.5">
                                <i class="fa-solid fa-brain"></i> AI 드립 도우미
                            </span>
                            <span class="text-[10px] text-y2k-neonLime font-bold bg-y2k-neonLime/10 px-2 py-0.5 rounded-full border border-y2k-neonLime/30">Auto Mode</span>
                        </div>

                        <div class="grid grid-cols-2 gap-2">
                            <select id="ai-topic" class="px-3 py-2 rounded-xl bg-y2k-bgDark border border-white/20 text-xs font-bold text-slate-200 focus:outline-none focus:border-y2k-neonPink">
                                <option value="school">🎒 학교/시험/공부</option>
                                <option value="kpop">💖 K-POP/덕질/최애</option>
                                <option value="mbti">🧩 MBTI/특징</option>
                                <option value="daily">🤪 병맛/억울한 일상</option>
                            </select>

                            <button onclick="generateAICaption()" class="ai-pulse-btn py-2 px-3 rounded-xl bg-gradient-to-r from-y2k-neonPurple via-y2k-neonPink to-y2k-neonCyan hover:opacity-90 text-black font-black text-xs transition-all flex items-center justify-center gap-1.5">
                                <i class="fa-solid fa-wand-magic-sparkles text-sm"></i>
                                <span>AI 드립 뽑기!</span>
                            </button>
                        </div>
                    </div>

                    <!-- Template Selector -->
                    <div class="glass-panel rounded-3xl p-5 border border-white/10 space-y-3">
                        <div class="flex items-center justify-between">
                            <label class="text-xs font-extrabold text-slate-300 uppercase tracking-wider">1. 템플릿 선택</label>
                            <label class="cursor-pointer text-xs text-y2k-neonCyan font-bold hover:underline flex items-center gap-1">
                                <i class="fa-solid fa-upload"></i> 내 사진 업로드
                                <input type="file" id="image-upload" accept="image/*" class="hidden" onchange="handleImageUpload(event)">
                            </label>
                        </div>

                        <div class="grid grid-cols-4 gap-2 max-h-36 overflow-y-auto pr-1" id="template-grid">
                            <!-- Dynamic Template Thumbnails inserted via JS -->
                        </div>
                    </div>

                    <!-- Text Customization Controls -->
                    <div class="glass-panel rounded-3xl p-5 border border-white/10 space-y-4">
                        <label class="text-xs font-extrabold text-slate-300 uppercase tracking-wider block">2. 문구 & 텍스트 스타일</label>

                        <div class="space-y-2.5">
                            <div>
                                <span class="text-[11px] text-slate-400 font-bold block mb-1">상단 텍스트 (TOP)</span>
                                <input type="text" id="input-top-text" value="시험 기간 내 머릿속" oninput="updateCanvas()" placeholder="상단 문구 입력..." class="w-full px-3.5 py-2.5 rounded-xl bg-y2k-bgDark border border-white/15 text-xs text-white placeholder-slate-500 focus:outline-none focus:border-y2k-neonCyan">
                            </div>

                            <div>
                                <span class="text-[11px] text-slate-400 font-bold block mb-1">하단 텍스트 (BOTTOM)</span>
                                <input type="text" id="input-bottom-text" value="공부 빼고 다 재밌음 ㅋㅋㅋ" oninput="updateCanvas()" placeholder="하단 문구 입력..." class="w-full px-3.5 py-2.5 rounded-xl bg-y2k-bgDark border border-white/15 text-xs text-white placeholder-slate-500 focus:outline-none focus:border-y2k-neonPink">
                            </div>
                        </div>

                        <!-- Font Options Grid -->
                        <div class="grid grid-cols-2 gap-3 pt-1">
                            <div>
                                <span class="text-[11px] text-slate-400 font-bold block mb-1">글자 색상</span>
                                <input type="color" id="input-text-color" value="#ffffff" onchange="updateCanvas()" class="w-full h-9 rounded-xl bg-y2k-bgDark border border-white/15 p-1 cursor-pointer">
                            </div>
                            <div>
                                <span class="text-[11px] text-slate-400 font-bold block mb-1">글자 크기</span>
                                <input type="range" id="input-text-size" min="20" max="70" value="42" oninput="updateCanvas()" class="w-full accent-y2k-neonPink mt-2">
                            </div>
                        </div>
                    </div>

                    <!-- Stickers & Emojis -->
                    <div class="glass-panel rounded-3xl p-5 border border-white/10 space-y-3">
                        <div class="flex items-center justify-between">
                            <label class="text-xs font-extrabold text-slate-300 uppercase tracking-wider">3. 스티커 / 이모지 추가</label>
                            <button onclick="clearStickers()" class="text-[10px] text-slate-400 hover:text-y2k-neonPink">스티커 초기화</button>
                        </div>

                        <div class="flex items-center gap-2 overflow-x-auto pb-1 scrollbar-none text-2xl">
                            <button onclick="addSticker('🔥')" class="p-2 rounded-xl bg-white/5 hover:bg-white/15 transition-all">🔥</button>
                            <button onclick="addSticker('💀')" class="p-2 rounded-xl bg-white/5 hover:bg-white/15 transition-all">💀</button>
                            <button onclick="addSticker('👑')" class="p-2 rounded-xl bg-white/5 hover:bg-white/15 transition-all">👑</button>
                            <button onclick="addSticker('✨')" class="p-2 rounded-xl bg-white/5 hover:bg-white/15 transition-all">✨</button>
                            <button onclick="addSticker('😭')" class="p-2 rounded-xl bg-white/5 hover:bg-white/15 transition-all">😭</button>
                            <button onclick="addSticker('💖')" class="p-2 rounded-xl bg-white/5 hover:bg-white/15 transition-all">💖</button>
                            <button onclick="addSticker('🤡')" class="p-2 rounded-xl bg-white/5 hover:bg-white/15 transition-all">🤡</button>
                            <button onclick="addSticker('🕶️')" class="p-2 rounded-xl bg-white/5 hover:bg-white/15 transition-all">🕶️</button>
                        </div>
                    </div>

                </div>

            </div>

        </section>

        <!-- VIRAL FEED SECTION -->
        <section id="feed-section" class="space-y-6 pt-6 border-t border-white/10">
            
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3">
                <div>
                    <h3 class="text-xl sm:text-2xl font-black font-blackhan text-white flex items-center gap-2">
                        <i class="fa-solid fa-fire text-y2k-neonYellow"></i> 실시간 10대 인기 짤방
                    </h3>
                    <p class="text-xs text-slate-400">지금 애들이 제일 많이 퍼나르는 신상 밈들!</p>
                </div>

                <!-- Feed Category Filter -->
                <div class="flex items-center gap-1.5 overflow-x-auto pb-1">
                    <button onclick="filterFeed('all')" class="feed-cat-btn active-feed-cat px-3 py-1.5 rounded-full text-xs font-bold bg-y2k-neonPink text-black whitespace-nowrap">
                        🔥 전체
                    </button>
                    <button onclick="filterFeed('school')" class="feed-cat-btn px-3 py-1.5 rounded-full text-xs font-bold glass-panel text-slate-300 hover:text-white whitespace-nowrap">
                        🎒 학교/시험
                    </button>
                    <button onclick="filterFeed('kpop')" class="feed-cat-btn px-3 py-1.5 rounded-full text-xs font-bold glass-panel text-slate-300 hover:text-white whitespace-nowrap">
                        💖 덕질
                    </button>
                    <button onclick="filterFeed('daily')" class="feed-cat-btn px-3 py-1.5 rounded-full text-xs font-bold glass-panel text-slate-300 hover:text-white whitespace-nowrap">
                        🤪 병맛
                    </button>
                </div>
            </div>

            <!-- Feed Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-5" id="feed-grid-container">
                <!-- Dynamic Feed Cards rendered via JS -->
            </div>

        </section>

    </main>

    <!-- Footer -->
    <footer class="border-t border-white/10 py-6 text-center text-xs text-slate-500">
        <p>© 2026 AI MEME FACTORY. Designed for Teens & Gen-Z.</p>
    </footer>

    <script>
        /* Preset Templates (Placeholder SVG data URLs & Unsplash Meme Stock) */
        const memeTemplates = [
            {
                id: 't1',
                name: '시바견 짤',
                url: 'https://images.unsplash.com/photo-1583511655857-d19b40a7a54e?w=600&auto=format&fit=crop&q=80'
            },
            {
                id: 't2',
                name: '놀란 고양이',
                url: 'https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?w=600&auto=format&fit=crop&q=80'
            },
            {
                id: 't3',
                name: '고민중인 미어캣',
                url: 'https://images.unsplash.com/photo-1551085254-e96b210df58a?w=600&auto=format&fit=crop&q=80'
            },
            {
                id: 't4',
                name: '무념무상 강아지',
                url: 'https://images.unsplash.com/photo-1537151625747-768eb6cf92b2?w=600&auto=format&fit=crop&q=80'
            }
        ];

        /* AI Captions Preset Database */
        const aiCaptions = {
            school: [
                { top: "시험 전날 내 머릿속", bottom: "기억나는 건 시험 범위 발표날 뿐" },
                { top: "월요일 1교시 체육시간", bottom: "영혼은 이미 침대에 있음" },
                { top: "선생님이랑 눈 마주쳤을 때", bottom: "(제발 나 시키지 마세요...)" },
                { top: "급식에 소시지 나온 날", bottom: "전교 1등보다 빠른 속도로 이동" }
            ],
            kpop: [
                { top: "최애가 셀카 올렸을 때", bottom: "숨 참고 러브 다이브 심장 마비" },
                { top: "티켓팅 실패했을 때", bottom: "내 손가락은 왜 이 모양인가" },
                { top: "포카 깠는데 최애 나왔을 때", bottom: "세상아 내가 성공했다 ㅠㅠ" },
                { top: "콘서트 공지 떴을 때", bottom: "내 통장: 제발 그만해..." }
            ],
            mbti: [
                { top: "F 100% 친구한테 고민 상담함", bottom: "너 진짜 속상했겠다 (속으로 딴생각)" },
                { top: "T 친구가 우울해서 빵 샀다고 할 때", bottom: " 무슨 빵? 칼로리 얼마임?" },
                { top: "E 100%의 주말 약속 취소됐을 때", bottom: "당장 다른 친구 전화 돌림" },
                { top: "I 100%의 약속 취소 소식 들었을 때", bottom: "속으로 만세 3창 부름 ㅋㅋㅋ" }
            ],
            daily: [
                { top: "용돈 받은 지 3분 뒤", bottom: "통장 잔고: 120원" },
                { top: "다이어트 선언 10분 후", bottom: "마라탕에 분모자 추가중" },
                { top: "짝사랑 상대한테 메시지 옴", bottom: "답장 고민하느라 3시간 경과" },
                { top: "새벽 2시 유튜브 알고리즘", bottom: "인도 길거리 음식 만드는 법 시청중" }
            ]
        };

        /* Community Feed Mock Data */
        let feedMemes = [
            {
                id: 'f1',
                category: 'school',
                imageUrl: 'https://images.unsplash.com/photo-1583511655857-d19b40a7a54e?w=600&auto=format&fit=crop&q=80',
                topText: '시험 시작 5분 전',
                bottomText: '내가 아는 건 오직 내 이름뿐',
                likes: 124,
                author: '시험범위파괴자'
            },
            {
                id: 'f2',
                category: 'kpop',
                imageUrl: 'https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?w=600&auto=format&fit=crop&q=80',
                topText: '최애 실물 영접한 순간',
                bottomText: '숨 쉬는 법 잊어버림',
                likes: 289,
                author: '포카집착녀'
            },
            {
                id: 'f3',
                category: 'daily',
                imageUrl: 'https://images.unsplash.com/photo-1551085254-e96b210df58a?w=600&auto=format&fit=crop&q=80',
                topText: '월요일 아침 7시 알람',
                bottomText: '지구가 오늘 멈추게 해주세요',
                likes: 95,
                author: '침대위의슬롯'
            }
        ];

        /* Canvas & State Variables */
        let canvas, ctx;
        let currentImage = new Image();
        let activeStickers = [];
        let selectedTemplateId = 't1';

        window.onload = function() {
            canvas = document.getElementById('memeCanvas');
            ctx = canvas.getContext('2d');

            renderTemplateGrid();
            loadTemplate(memeTemplates[0].url);
            renderFeed('all');
        };

        /* Render Template Grid Thumbnails */
        function renderTemplateGrid() {
            const grid = document.getElementById('template-grid');
            grid.innerHTML = memeTemplates.map(t => `
                <div onclick="selectTemplate('${t.id}', '${t.url}')" class="relative aspect-square rounded-xl overflow-hidden border-2 cursor-pointer transition-all ${t.id === selectedTemplateId ? 'border-y2k-neonPink scale-95 shadow-md' : 'border-white/10 opacity-70 hover:opacity-100'}">
                    <img src="${t.url}" alt="${t.name}" class="w-full h-full object-cover">
                </div>
            `).join('');
        }

        function selectTemplate(id, url) {
            selectedTemplateId = id;
            renderTemplateGrid();
            loadTemplate(url);
        }

        function handleImageUpload(e) {
            const file = e.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function(event) {
                selectedTemplateId = null;
                renderTemplateGrid();
                loadTemplate(event.target.result);
            };
            reader.readAsDataURL(file);
        }

        function loadTemplate(url) {
            currentImage = new Image();
            currentImage.crossOrigin = 'anonymous';
            currentImage.onload = function() {
                // Set canvas internal resolution
                canvas.width = 600;
                canvas.height = 600;
                updateCanvas();
            };
            currentImage.src = url;
        }

        function updateCanvas() {
            if (!ctx || !currentImage.complete) return;

            // Clear canvas
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Draw Background Image (Cover Mode)
            ctx.drawImage(currentImage, 0, 0, canvas.width, canvas.height);

            // Draw Text Style Settings
            const topText = document.getElementById('input-top-text').value;
            const bottomText = document.getElementById('input-bottom-text').value;
            const textColor = document.getElementById('input-text-color').value;
            const fontSize = document.getElementById('input-text-size').value;

            ctx.fillStyle = textColor;
            ctx.strokeStyle = '#000000';
            ctx.lineWidth = Math.max(4, fontSize / 8);
            ctx.font = `900 ${fontSize}px "Impact", "Black Han Sans", sans-serif`;
            ctx.textAlign = 'center';

            // Top Text Drawing
            if (topText) {
                ctx.textBaseline = 'top';
                ctx.strokeText(topText, canvas.width / 2, 25);
                ctx.fillText(topText, canvas.width / 2, 25);
            }

            // Bottom Text Drawing
            if (bottomText) {
                ctx.textBaseline = 'bottom';
                ctx.strokeText(bottomText, canvas.width / 2, canvas.height - 25);
                ctx.fillText(bottomText, canvas.width / 2, canvas.height - 25);
            }

            // Draw Stickers
            activeStickers.forEach(s => {
                ctx.font = `${s.size}px sans-serif`;
                ctx.textBaseline = 'middle';
                ctx.fillText(s.emoji, s.x, s.y);
            });
        }

        /* Sticker Handling */
        function addSticker(emoji) {
            activeStickers.push({
                emoji: emoji,
                x: canvas.width / 2 + (Math.random() * 100 - 50),
                y: canvas.height / 2 + (Math.random() * 100 - 50),
                size: 50
            });
            updateCanvas();
        }

        function clearStickers() {
            activeStickers = [];
            updateCanvas();
        }

        function generateAICaption() {
            const topic = document.getElementById('ai-topic').value;
            const list = aiCaptions[topic] || aiCaptions.daily;

            const loader = document.getElementById('canvas-loading');
            loader.classList.remove('hidden');

            setTimeout(() => {
                const randomCaption = list[Math.floor(Math.random() * list.length)];
                document.getElementById('input-top-text').value = randomCaption.top;
                document.getElementById('input-bottom-text').value = randomCaption.bottom;
                
                loader.classList.add('hidden');
                updateCanvas();

                confetti({
                    particleCount: 40,
                    spread: 60,
                    origin: { y: 0.6 }
                });
            }, 600);
        }

        /* Export Options */
        function downloadMeme() {
            const dataUrl = canvas.toDataURL('image/png');
            const a = document.createElement('a');
            a.href = dataUrl;
            a.download = `meme-factory-${Date.now()}.png`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
        }

        function shareMeme() {
            if (navigator.share) {
                canvas.toBlob(blob => {
                    const file = new File([blob], 'meme.png', { type: 'image/png' });
                    navigator.share({
                        title: 'AI 밈 팩토리 - 내가 만든 짤',
                        text: '내가 만든 킹받는 짤 구경해라 ㅋㅋㅋ',
                        files: [file]
                    }).catch(() => {});
                });
            } else {
                copyToClipboard(window.location.href, "웹사이트 링크가 복사되었습니다! 친구들에게 공유하세요.");
            }
        }

        function postToFeed() {
            const topText = document.getElementById('input-top-text').value;
            const bottomText = document.getElementById('input-bottom-text').value;
            const topic = document.getElementById('ai-topic').value;

            const newFeedItem = {
                id: `f-${Date.now()}`,
                category: topic,
                imageUrl: canvas.toDataURL('image/png'),
                topText: topText,
                bottomText: bottomText,
                likes: 1,
                author: '방금 막 만든 유저'
            };

            feedMemes.unshift(newFeedItem);
            renderFeed('all');
            scrollToFeed();

            confetti({
                particleCount: 80,
                spread: 100,
                origin: { y: 0.8 }
            });
        }

        function renderFeed(cat) {
            const container = document.getElementById('feed-grid-container');
            const items = cat === 'all' ? feedMemes : feedMemes.filter(m => m.category === cat);

            if (items.length === 0) {
                container.innerHTML = `<div class="col-span-full text-center py-8 text-xs text-slate-500">등록된 짤이 없습니다. 첫번째 짤을 자랑해보세요!</div>`;
                return;
            }

            container.innerHTML = items.map(item => `
                <div class="glass-panel rounded-3xl p-4 border border-white/10 space-y-3 flex flex-col justify-between group hover:border-y2k-neonPink/50 transition-all">
                    <div class="space-y-2">
                        <div class="aspect-square rounded-2xl overflow-hidden bg-black/50 border border-white/10">
                            <img src="${item.imageUrl}" alt="Meme" class="w-full h-full object-contain">
                        </div>
                        <div class="flex items-center justify-between text-xs pt-1">
                            <span class="font-bold text-y2k-neonCyan">@${item.author}</span>
                            <span class="text-[10px] bg-white/10 px-2 py-0.5 rounded-full text-slate-300">${item.category}</span>
                        </div>
                    </div>

                    <div class="flex items-center justify-between border-t border-white/10 pt-2">
                        <button onclick="likeFeedItem('${item.id}', this)" class="flex items-center gap-1.5 text-xs font-bold text-slate-400 hover:text-y2k-neonPink transition-colors">
                            <i class="fa-solid fa-heart text-y2k-neonPink"></i>
                            <span id="like-count-${item.id}">${item.likes}</span>
                        </button>
                        <button onclick="shareMemeItem('${item.id}')" class="text-slate-400 hover:text-white text-xs">
                            <i class="fa-solid fa-share-nodes"></i>
                        </button>
                    </div>
                </div>
            `).join('');
        }

        function filterFeed(cat) {
            document.querySelectorAll('.feed-cat-btn').forEach(b => {
                b.classList.remove('bg-y2k-neonPink', 'text-black');
                b.classList.add('glass-panel', 'text-slate-300');
            });
            event.currentTarget.classList.add('bg-y2k-neonPink', 'text-black');
            renderFeed(cat);
        }

        function likeFeedItem(id, btn) {
            const item = feedMemes.find(m => m.id === id);
            if (item) {
                item.likes++;
                document.getElementById(`like-count-${id}`).innerText = item.likes;
                btn.classList.add('scale-125');
                setTimeout(() => btn.classList.remove('scale-125'), 200);
            }
        }

        function scrollToStudio() {
            document.getElementById('studio-section').scrollIntoView({ behavior: 'smooth' });
        }

        function scrollToFeed() {
            document.getElementById('feed-section').scrollIntoView({ behavior: 'smooth' });
        }

        function copyToClipboard(text, msg) {
            const dummy = document.createElement('textarea');
            document.body.appendChild(dummy);
            dummy.value = text;
            dummy.select();
            document.execCommand('copy');
            document.body.removeChild(dummy);

            const toast = document.createElement('div');
            toast.className = 'fixed bottom-6 left-1/2 -translate-x-1/2 bg-y2k-neonPink text-black px-6 py-3 rounded-2xl shadow-2xl z-50 text-xs font-black flex items-center gap-2 animate-bounce';
            toast.innerHTML = `<i class="fa-solid fa-check"></i> ${msg}`;
            document.body.appendChild(toast);
            setTimeout(() => toast.remove(), 2200);
        }
    </script>
</body>
</html>
