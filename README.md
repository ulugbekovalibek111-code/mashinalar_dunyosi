# mashinalar_dunyosii
Mashinalar yaratilish tarixi va turlari
<!DOCTYPE html>
<html lang="uz" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Avtomobillar Dunyosi: Tarixi va Turlari</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        darkBg: '#0b0f19',
                        cardBg: '#131a2a',
                        accentAmber: '#f59e0b',
                        accentCyan: '#06b6d4',
                    }
                }
            }
        }
    </script>
    <style>
        /* Asosiy ranglar, shisha effekti va oyna animatsiyalari */
        body {
            background-color: #0b0f19;
            color: #f8fafc;
        }
        .glass-card {
            background: rgba(19, 26, 42, 0.82);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.08);
        }
        .glass-nav {
            background: rgba(11, 15, 25, 0.92);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
        }
        .timeline-line::before {
            content: '';
            position: absolute;
            top: 0;
            bottom: 0;
            left: 20px;
            width: 3px;
            background: linear-gradient(to bottom, #f59e0b, #06b6d4);
            border-radius: 999px;
        }
        @media (min-width: 768px) {
            .timeline-line::before {
                left: 50%;
                transform: translateX(-50%);
            }
        }
        .hero-glow {
            background: radial-gradient(circle at 50% 25%, rgba(245, 158, 11, 0.16) 0%, rgba(6, 182, 212, 0.08) 40%, rgba(11, 15, 25, 0) 75%);
        }
        /* Har bir bo'lim alohida oyna sifatida ko'rinadi */
        .page-view {
            display: none;
            animation: pageFadeIn 0.35s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .page-view.active {
            display: block;
        }
        @keyframes pageFadeIn {
            from {
                opacity: 0;
                transform: translateY(14px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
    </style>
</head>
<body class="antialiased selection:bg-amber-500 selection:text-slate-950 overflow-x-hidden min-h-screen flex flex-col">

    <!-- Yuqori navigatsiya paneli (Alohida oynalar o'rtasida o'tish) -->
    <header class="fixed top-0 left-0 right-0 z-40 glass-nav transition-all duration-300">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16 md:h-20">
                <!-- Brend logotipi -->
                <button type="button" onclick="navigateTo('home')" class="flex items-center space-x-3 group text-left focus:outline-none">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-amber-500 to-orange-600 flex items-center justify-center shadow-lg shadow-amber-500/20 group-hover:scale-105 transition-transform">
                        <svg class="w-6 h-6 text-slate-950" fill="none" stroke="currentColor" stroke-width="2.2" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M8 17h8M5 17H3v-4l2-5h14l2 5v4h-2m-11 0a2 2 0 104 0m4 0a2 2 0 104 0" />
                        </svg>
                    </div>
                    <div>
                        <span class="font-extrabold text-lg sm:text-xl tracking-tight text-white">AVTO<span class="text-amber-400">TARIX</span></span>
                        <span class="hidden sm:block text-[10px] uppercase tracking-widest text-slate-400">Ensiklopediya</span>
                    </div>
                </button>

                <!-- Desktop oynalar menyusi -->
                <nav class="hidden lg:flex items-center space-x-1.5 text-sm font-medium">
                    <button type="button" data-page="home" class="nav-tab px-3.5 py-2 rounded-xl transition-all">Bosh sahifa</button>
                    <button type="button" data-page="history" class="nav-tab px-3.5 py-2 rounded-xl transition-all">Yaratilish Tarixi</button>
                    <button type="button" data-page="types" class="nav-tab px-3.5 py-2 rounded-xl transition-all">Avtomobil Turlari (16)</button>
                    <button type="button" data-page="gallery" class="nav-tab px-3.5 py-2 rounded-xl transition-all">Foto Galereya</button>
                    <button type="button" data-page="quiz" class="nav-tab px-3.5 py-2 rounded-xl transition-all">Bilimni Sinash</button>
                </nav>

                <!-- Mobil menyu tugmasi -->
                <button id="mobile-menu-btn" type="button" aria-label="Menyuni ochish" class="lg:hidden p-2.5 rounded-xl text-slate-300 hover:text-white hover:bg-slate-800/60 focus:outline-none">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
                    </svg>
                </button>
            </div>
        </div>

        <!-- Mobil ochiluvchi menyu -->
        <div id="mobile-menu" class="hidden lg:hidden border-t border-slate-800 bg-slate-950/95 px-4 pt-3 pb-5 space-y-2">
            <button type="button" data-page="home" class="mobile-nav-tab w-full text-left block px-4 py-3 rounded-xl transition-colors">Bosh sahifa</button>
            <button type="button" data-page="history" class="mobile-nav-tab w-full text-left block px-4 py-3 rounded-xl transition-colors">Yaratilish Tarixi</button>
            <button type="button" data-page="types" class="mobile-nav-tab w-full text-left block px-4 py-3 rounded-xl transition-colors">Avtomobil Turlari (16)</button>
            <button type="button" data-page="gallery" class="mobile-nav-tab w-full text-left block px-4 py-3 rounded-xl transition-colors">Foto Galereya</button>
            <button type="button" data-page="quiz" class="mobile-nav-tab w-full text-left block px-4 py-3 rounded-xl transition-colors">Bilimni Sinash (Test)</button>
        </div>
    </header>

    <!-- ASOSIY OYNALAR KONTEYNERI -->
    <main class="flex-grow pt-20 md:pt-24">

        <!-- ========================================================= -->
        <!-- 1-OYNA: BOSH SAHIFA                                       -->
        <!-- ========================================================= -->
        <section id="view-home" class="page-view active hero-glow py-10 md:py-16">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 lg:gap-12 items-center">
                    <div class="lg:col-span-7 text-center lg:text-left">
                        <div class="inline-flex items-center space-x-2 px-3.5 py-1.5 rounded-full bg-amber-500/10 border border-amber-500/30 text-amber-400 text-xs sm:text-sm font-medium mb-6">
                            <span class="w-2 h-2 rounded-full bg-amber-400 animate-pulse"></span>
                            <span>1769-yildan bugungi kungacha bo'lgan avtomobil evolyutsiyasi</span>
                        </div>
                        <h1 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold tracking-tight text-white leading-tight mb-6">
                            Avtomobillar Dunyosi: <span class="text-transparent bg-clip-text bg-gradient-to-r from-amber-400 via-orange-400 to-cyan-400">Tarixi va Turlari</span>
                        </h1>
                        <p class="text-base sm:text-lg text-slate-300 max-w-2xl mx-auto lg:mx-0 mb-8 leading-relaxed">
                            Ilk bug'li aravalardan tortib zamonaviy elektromobillar va giperkarlargacha bo'lgan yo'lni o'rganing. Har bir bo'lim alohida oynada ochiladi — 16 xil avtomobil turi, yaratilish sanalari, foto galereya va viktorina sizning ixtiyoringizda.
                        </p>
                        <div class="flex flex-col sm:flex-row items-center justify-center lg:justify-start gap-4">
                            <button type="button" onclick="navigateTo('history')" class="w-full sm:w-auto px-7 py-3.5 rounded-xl bg-gradient-to-r from-amber-500 to-orange-600 text-slate-950 font-bold text-sm sm:text-base shadow-lg shadow-amber-500/25 hover:shadow-amber-500/40 hover:-translate-y-0.5 transition-all text-center">
                                Yaratilish Tarixi Oynasi &rarr;
                            </button>
                            <button type="button" onclick="navigateTo('types')" class="w-full sm:w-auto px-7 py-3.5 rounded-xl glass-card text-white font-semibold text-sm sm:text-base hover:bg-slate-800/80 border border-slate-700 hover:-translate-y-0.5 transition-all text-center">
                                16 ta Avtomobil Turi Oynasi
                            </button>
                        </div>

                        <!-- Asosiy ko'rsatkichlar -->
                        <div class="grid grid-cols-3 gap-4 mt-10 pt-8 border-t border-slate-800/80 max-w-lg mx-auto lg:mx-0">
                            <div>
                                <p class="text-2xl sm:text-3xl font-extrabold text-amber-400">1769</p>
                                <p class="text-xs sm:text-sm text-slate-400 mt-1">Ilk bug'li arava</p>
                            </div>
                            <div>
                                <p class="text-2xl sm:text-3xl font-extrabold text-cyan-400">1886</p>
                                <p class="text-xs sm:text-sm text-slate-400 mt-1">Ilk benzinli avto</p>
                            </div>
                            <div>
                                <p class="text-2xl sm:text-3xl font-extrabold text-white">16 Tur</p>
                                <p class="text-xs sm:text-sm text-slate-400 mt-1">Kuzov tasnifi</p>
                            </div>
                        </div>
                    </div>

                    <!-- Bosh sahifa surat kartasi -->
                    <div class="lg:col-span-5">
                        <div class="glass-card rounded-3xl p-4 sm:p-5 relative overflow-hidden border border-slate-700/60 shadow-2xl group">
                            <div class="flex items-center justify-between mb-3 px-1">
                                <span class="text-xs font-semibold uppercase tracking-wider text-cyan-400 bg-cyan-500/10 px-3 py-1 rounded-full">Tezlik va Texnologiya</span>
                                <span class="text-xs text-slate-400">1769 — 2026</span>
                            </div>

                            <div class="relative rounded-2xl overflow-hidden aspect-[16/10] bg-slate-900 border border-slate-800">
                                <img
                                    src="https://images.unsplash.com/photo-1544636331-e26879cd4d9b?auto=format&fit=crop&w=900&q=80"
                                    alt="Zamonaviy sport avtomobili"
                                    onerror="handleImageFallback(this, 'sport')"
                                    class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700"
                                >
                                <div class="absolute inset-0 bg-gradient-to-t from-slate-950/90 via-slate-950/20 to-transparent"></div>
                                <div class="absolute bottom-3 left-3 right-3 flex items-center justify-between">
                                    <div>
                                        <p class="text-xs text-amber-400 font-semibold">Aerodinamika & Quvvat</p>
                                        <p class="text-sm font-bold text-white">XXI asr muhandislik san'ati</p>
                                    </div>
                                    <span class="px-2.5 py-1 rounded-lg bg-slate-950/80 border border-slate-700 text-[11px] font-bold text-cyan-400">16 Tur Avto</span>
                                </div>
                            </div>

                            <div class="grid grid-cols-2 gap-3 mt-4 text-xs">
                                <div class="bg-slate-900/80 p-3 rounded-xl border border-slate-800">
                                    <span class="text-slate-400 block">Birinchi patent</span>
                                    <span class="font-bold text-white text-sm">29-yanvar, 1886</span>
                                </div>
                                <div class="bg-slate-900/80 p-3 rounded-xl border border-slate-800">
                                    <span class="text-slate-400 block">Zamonaviy davr</span>
                                    <span class="font-bold text-cyan-400 text-sm">EV, Gibrid & Giperkar</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Oynalarga tezkor o'tish kartalari -->
                <div class="mt-16">
                    <h2 class="text-xl sm:text-2xl font-bold text-white mb-6 text-center lg:text-left">Alohida Oynalar Bo'ylab Sayohat</h2>
                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-5">
                        <div onclick="navigateTo('history')" class="glass-card rounded-2xl p-6 border border-slate-800 hover:border-amber-500/50 cursor-pointer transition-all hover:-translate-y-1 group">
                            <div class="w-11 h-11 rounded-xl bg-amber-500/15 text-amber-400 flex items-center justify-center mb-4 font-extrabold text-lg">01</div>
                            <h3 class="text-lg font-bold text-white group-hover:text-amber-400 transition-colors mb-2">Yaratilish Tarixi</h3>
                            <p class="text-xs sm:text-sm text-slate-400 mb-4">1769-yildan bugungacha bo'lgan muhim ixtiro sanalari va muhandislar xronologiyasi.</p>
                            <span class="text-xs font-semibold text-amber-400">Oynani ochish &rarr;</span>
                        </div>

                        <div onclick="navigateTo('types')" class="glass-card rounded-2xl p-6 border border-slate-800 hover:border-cyan-500/50 cursor-pointer transition-all hover:-translate-y-1 group">
                            <div class="w-11 h-11 rounded-xl bg-cyan-500/15 text-cyan-400 flex items-center justify-center mb-4 font-extrabold text-lg">02</div>
                            <h3 class="text-lg font-bold text-white group-hover:text-cyan-400 transition-colors mb-2">Avtomobil Turlari (16)</h3>
                            <p class="text-xs sm:text-sm text-slate-400 mb-4">Sedan, SUV, Sportkar, EV, Universal, Kabriolet, Miniven, Giperkar, Gibrid va boshqalar.</p>
                            <span class="text-xs font-semibold text-cyan-400">Oynani ochish &rarr;</span>
                        </div>

                        <div onclick="navigateTo('gallery')" class="glass-card rounded-2xl p-6 border border-slate-800 hover:border-emerald-500/50 cursor-pointer transition-all hover:-translate-y-1 group">
                            <div class="w-11 h-11 rounded-xl bg-emerald-500/15 text-emerald-400 flex items-center justify-center mb-4 font-extrabold text-lg">03</div>
                            <h3 class="text-lg font-bold text-white group-hover:text-emerald-400 transition-colors mb-2">Foto Galereya</h3>
                            <p class="text-xs sm:text-sm text-slate-400 mb-4">Turli mashina turlarining suratlari, kategoriya filtrlari va kattalashtirib ko'rish oynasi.</p>
                            <span class="text-xs font-semibold text-emerald-400">Oynani ochish &rarr;</span>
                        </div>

                        <div onclick="navigateTo('quiz')" class="glass-card rounded-2xl p-6 border border-slate-800 hover:border-purple-500/50 cursor-pointer transition-all hover:-translate-y-1 group">
                            <div class="w-11 h-11 rounded-xl bg-purple-500/15 text-purple-400 flex items-center justify-center mb-4 font-extrabold text-lg">04</div>
                            <h3 class="text-lg font-bold text-white group-hover:text-purple-400 transition-colors mb-2">Bilimlar Viktorinasi</h3>
                            <p class="text-xs sm:text-sm text-slate-400 mb-4">Avtomobil turlari va yaratilish sanalari bo'yicha interaktiv bilim sinovi.</p>
                            <span class="text-xs font-semibold text-purple-400">Oynani ochish &rarr;</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ========================================================= -->
        <!-- 2-OYNA: YARATILISH TARIXI                                 -->
        <!-- ========================================================= -->
        <section id="view-history" class="page-view py-10 md:py-14">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex flex-col lg:flex-row lg:items-end justify-between gap-6 mb-12 pb-6 border-b border-slate-800">
                    <div>
                        <span class="text-amber-400 font-semibold text-xs uppercase tracking-wider">Alohida Oyna &bull; Xronologiya</span>
                        <h2 class="text-3xl sm:text-4xl font-extrabold text-white mt-1">Avtomobillar Yaratilish Tarixi</h2>
                        <p class="text-slate-400 text-sm sm:text-base mt-2 max-w-2xl">
                            1769-yildagi ilk bug'li aravadan boshlab bugungi zamonaviy elektromobillargacha bo'lgan muhim yaratilish sanalari. Batafsil texnik ma'lumot uchun kartani bosing.
                        </p>
                    </div>
                    <div class="relative w-full lg:w-80">
                        <svg class="w-5 h-5 text-slate-400 absolute left-3.5 top-1/2 -translate-y-1/2" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-4.35-4.35M17 11a6 6 0 11-12 0 6 6 0 0112 0z" />
                        </svg>
                        <input type="text" id="historySearchInput" placeholder="Yil yoki ixtirochini qidiring..." class="w-full pl-11 pr-4 py-3 rounded-xl bg-slate-900/90 border border-slate-700 text-sm text-white placeholder-slate-400 focus:outline-none focus:border-amber-500 transition-colors">
                    </div>
                </div>

                <!-- Tarixiy xronologiya kartalari -->
                <div id="timelineContainer" class="relative timeline-line space-y-10 md:space-y-12"></div>

                <!-- Oynalararo navigatsiya -->
                <div class="mt-16 pt-8 border-t border-slate-800 flex flex-wrap items-center justify-between gap-4">
                    <button type="button" onclick="navigateTo('home')" class="px-5 py-3 rounded-xl glass-card text-slate-300 hover:text-white font-semibold text-sm transition-all">
                        &larr; Bosh sahifa oynasi
                    </button>
                    <button type="button" onclick="navigateTo('types')" class="px-6 py-3 rounded-xl bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold text-sm transition-all">
                        Keyingi oyna: Avtomobil Turlari (16) &rarr;
                    </button>
                </div>
            </div>
        </section>

        <!-- ========================================================= -->
        <!-- 3-OYNA: AVTOMOBIL TURLARI (16 TA TUR)                     -->
        <!-- ========================================================= -->
        <section id="view-types" class="page-view py-10 md:py-14">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex flex-col lg:flex-row lg:items-end justify-between gap-6 mb-8 pb-6 border-b border-slate-800">
                    <div>
                        <span class="text-cyan-400 font-semibold text-xs uppercase tracking-wider">Alohida Oyna &bull; 16 xil kuzov va texnologiya</span>
                        <h2 class="text-3xl sm:text-4xl font-extrabold text-white mt-1">Avtomobillar Turlari</h2>
                        <p class="text-slate-400 text-sm sm:text-base mt-2 max-w-2xl">
                            Kuzov tuzilishi, dvigatel tizimi va vazifasiga ko'ra 16 ta asosiy avtomobil turi hamda ularning yaratilish davrlari. Batafsil oyna uchun kartani bosing.
                        </p>
                    </div>

                    <div class="relative w-full lg:w-80">
                        <svg class="w-5 h-5 text-slate-400 absolute left-3.5 top-1/2 -translate-y-1/2" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-4.35-4.35M17 11a6 6 0 11-12 0 6 6 0 0112 0z" />
                        </svg>
                        <input type="text" id="typesSearchInput" placeholder="Tur, yil yoki modelni qidiring..." class="w-full pl-11 pr-4 py-3 rounded-xl bg-slate-900/90 border border-slate-700 text-sm text-white placeholder-slate-400 focus:outline-none focus:border-cyan-500 transition-colors">
                    </div>
                </div>

                <!-- Guruh/kategoriya filtrlari -->
                <div id="filterButtons" class="flex flex-wrap gap-2 mb-8">
                    <button type="button" data-filter="all" class="filter-btn active px-4 py-2.5 rounded-xl text-xs sm:text-sm font-semibold bg-amber-500 text-slate-950 shadow-md transition-all">Barchasi (16)</button>
                    <button type="button" data-filter="daily" class="filter-btn px-4 py-2.5 rounded-xl text-xs sm:text-sm font-semibold glass-card text-slate-300 hover:text-white transition-all">Kundalik va Oila</button>
                    <button type="button" data-filter="speed" class="filter-btn px-4 py-2.5 rounded-xl text-xs sm:text-sm font-semibold glass-card text-slate-300 hover:text-white transition-all">Tezlik va Sport</button>
                    <button type="button" data-filter="eco" class="filter-btn px-4 py-2.5 rounded-xl text-xs sm:text-sm font-semibold glass-card text-slate-300 hover:text-white transition-all">Ekologik va Maxsus</button>
                </div>

                <!-- 16 ta avtomobil turi kartalari -->
                <div id="carTypesGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6"></div>

                <!-- Qidiruv natijasi topilmasa -->
                <div id="noResultsMessage" class="hidden text-center py-12 glass-card rounded-2xl">
                    <p class="text-slate-300 font-medium text-lg">So'rovingiz bo'yicha avtomobil turi topilmadi.</p>
                    <button id="resetAllFilters" type="button" class="mt-4 px-5 py-2.5 rounded-xl bg-amber-500 text-slate-950 font-semibold text-sm">Barcha 16 turni ko'rsatish</button>
                </div>

                <!-- Oynalararo navigatsiya -->
                <div class="mt-16 pt-8 border-t border-slate-800 flex flex-wrap items-center justify-between gap-4">
                    <button type="button" onclick="navigateTo('history')" class="px-5 py-3 rounded-xl glass-card text-slate-300 hover:text-white font-semibold text-sm transition-all">
                        &larr; Oldingi oyna: Yaratilish Tarixi
                    </button>
                    <button type="button" onclick="navigateTo('gallery')" class="px-6 py-3 rounded-xl bg-cyan-500 hover:bg-cyan-400 text-slate-950 font-bold text-sm transition-all">
                        Keyingi oyna: Foto Galereya &rarr;
                    </button>
                </div>
            </div>
        </section>

        <!-- ========================================================= -->
        <!-- 4-OYNA: FOTO GALEREYA                                     -->
        <!-- ========================================================= -->
        <section id="view-gallery" class="page-view py-10 md:py-14">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex flex-col md:flex-row md:items-end justify-between gap-6 mb-8 pb-6 border-b border-slate-800">
                    <div>
                        <span class="text-emerald-400 font-semibold text-xs uppercase tracking-wider">Alohida Oyna &bull; Vizual Ko'rgazma</span>
                        <h2 class="text-3xl sm:text-4xl font-extrabold text-white mt-1">Avtomobillar Foto Galereyasi</h2>
                        <p class="text-slate-400 text-sm sm:text-base mt-2 max-w-2xl">
                            Turli avtomobil turlari va davrlarga oid suratlar to'plami. Rasmni kattalashtirib ko'rish uchun ustiga bosing.
                        </p>
                    </div>

                    <div id="galleryFilters" class="flex flex-wrap gap-2">
                        <button type="button" data-gfilter="all" class="g-filter-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-emerald-500 text-slate-950 transition-all">Barchasi</button>
                        <button type="button" data-gfilter="supercar" class="g-filter-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-semibold glass-card text-slate-300 hover:text-white transition-all">Sport & Giperkar</button>
                        <button type="button" data-gfilter="retro" class="g-filter-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-semibold glass-card text-slate-300 hover:text-white transition-all">Retro & Klassik</button>
                        <button type="button" data-gfilter="ev" class="g-filter-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-semibold glass-card text-slate-300 hover:text-white transition-all">EV & Gibrid</button>
                        <button type="button" data-gfilter="suv" class="g-filter-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-semibold glass-card text-slate-300 hover:text-white transition-all">SUV & Pikap</button>
                    </div>
                </div>

                <div id="galleryGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6"></div>

                <!-- Oynalararo navigatsiya -->
                <div class="mt-16 pt-8 border-t border-slate-800 flex flex-wrap items-center justify-between gap-4">
                    <button type="button" onclick="navigateTo('types')" class="px-5 py-3 rounded-xl glass-card text-slate-300 hover:text-white font-semibold text-sm transition-all">
                        &larr; Oldingi oyna: Avtomobil Turlari
                    </button>
                    <button type="button" onclick="navigateTo('quiz')" class="px-6 py-3 rounded-xl bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold text-sm transition-all">
                        Keyingi oyna: Bilimni Sinash (Test) &rarr;
                    </button>
                </div>
            </div>
        </section>

        <!-- ========================================================= -->
        <!-- 5-OYNA: BILIMLAR VIKTORINASI                              -->
        <!-- ========================================================= -->
        <section id="view-quiz" class="page-view py-10 md:py-14">
            <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="glass-card rounded-3xl p-6 sm:p-10 border border-slate-700/70 shadow-2xl relative overflow-hidden">
                    <div class="absolute top-0 right-0 w-64 h-64 bg-cyan-500/10 rounded-full blur-3xl pointer-events-none"></div>

                    <div class="text-center mb-8">
                        <span class="px-3.5 py-1 rounded-full bg-cyan-500/10 border border-cyan-500/30 text-cyan-400 text-xs font-semibold uppercase tracking-wider">Alohida Oyna &bull; Interaktiv Test</span>
                        <h2 class="text-2xl sm:text-3xl font-extrabold text-white mt-3">Avtomobil Tarixi va Turlari Viktorinasi</h2>
                        <p class="text-slate-400 text-sm mt-2">6 ta savolga javob bering va avtomobilsozlik bo'yicha bilimingizni tekshiring.</p>
                    </div>

                    <div id="quizBox">
                        <div class="flex items-center justify-between text-xs text-slate-400 mb-2">
                            <span id="quizStepText">Savol: 1 / 6</span>
                            <span id="quizScoreText">Ball: 0</span>
                        </div>
                        <div class="w-full h-2 bg-slate-800 rounded-full overflow-hidden mb-6">
                            <div id="quizProgressBar" class="h-full bg-gradient-to-r from-amber-500 to-cyan-400 transition-all duration-300" style="width: 16.6%"></div>
                        </div>

                        <h3 id="quizQuestion" class="text-lg sm:text-xl font-bold text-white mb-6"></h3>
                        <div id="quizOptions" class="space-y-3"></div>

                        <div id="quizFeedback" class="hidden mt-5 p-4 rounded-xl text-sm"></div>
                        <div class="mt-6 flex justify-end">
                            <button id="nextQuestionBtn" type="button" class="hidden px-6 py-3 rounded-xl bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold text-sm transition-all">Keyingi savol &rarr;</button>
                        </div>
                    </div>

                    <div id="quizResultBox" class="hidden text-center py-6">
                        <div class="w-20 h-20 mx-auto rounded-2xl bg-gradient-to-br from-amber-500 to-cyan-500 flex items-center justify-center text-slate-950 font-extrabold text-3xl mb-4 shadow-lg">
                            <span id="finalScoreDisplay">6/6</span>
                        </div>
                        <h3 id="resultTitle" class="text-2xl font-bold text-white mb-2">Ajoyib natija!</h3>
                        <p id="resultDesc" class="text-slate-300 text-sm sm:text-base max-w-md mx-auto mb-6"></p>
                        <div class="flex flex-wrap justify-center gap-3">
                            <button id="restartQuizBtn" type="button" class="px-6 py-3 rounded-xl bg-slate-800 hover:bg-slate-700 text-white font-semibold text-sm border border-slate-600 transition-all">Qaytadan boshlash</button>
                            <button type="button" onclick="navigateTo('home')" class="px-6 py-3 rounded-xl bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold text-sm transition-all">Bosh sahifaga o'tish</button>
                        </div>
                    </div>
                </div>

                <!-- Oynalararo navigatsiya -->
                <div class="mt-10 flex flex-wrap items-center justify-between gap-4">
                    <button type="button" onclick="navigateTo('gallery')" class="px-5 py-3 rounded-xl glass-card text-slate-300 hover:text-white font-semibold text-sm transition-all">
                        &larr; Oldingi oyna: Foto Galereya
                    </button>
                    <button type="button" onclick="navigateTo('home')" class="px-5 py-3 rounded-xl glass-card text-amber-400 hover:text-amber-300 font-semibold text-sm transition-all">
                        Bosh sahifa oynasiga qaytish
                    </button>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="border-t border-slate-800/80 bg-slate-950 py-8 mt-auto">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-4">
            <div class="flex items-center space-x-2">
                <span class="font-extrabold text-lg text-white">AVTO<span class="text-amber-400">TARIX</span></span>
                <span class="text-slate-500 text-sm">| O'zbek tilidagi avtomobil ensiklopediyasi</span>
            </div>
            <p class="text-xs sm:text-sm text-slate-400 text-center sm:text-right">
                &copy; 2026 Avtomobillar Dunyosi. Barcha bo'limlar alohida oynalarda ishlaydi.
            </p>
        </div>
    </footer>

    <!-- Batafsil Ma'lumot va Kattalashtirilgan Rasm Modali -->
    <div id="detailModal" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-slate-950/85 backdrop-blur-sm">
        <div class="glass-card rounded-3xl max-w-2xl w-full max-h-[90vh] overflow-y-auto p-6 sm:p-8 border border-slate-700 shadow-2xl relative">
            <button id="closeModalBtn" type="button" aria-label="Yopish" class="absolute top-5 right-5 z-10 p-2.5 rounded-xl bg-slate-900/90 text-slate-300 hover:text-white hover:bg-slate-700 transition-colors border border-slate-700">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2.2" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                </svg>
            </button>

            <div id="modalBadge" class="inline-block px-3 py-1 rounded-full text-xs font-semibold bg-amber-500/15 text-amber-400 border border-amber-500/30 mb-3"></div>
            <h3 id="modalTitle" class="text-2xl sm:text-3xl font-extrabold text-white mb-2"></h3>
            <p id="modalSubtitle" class="text-sm text-cyan-400 font-medium mb-5"></p>

            <div id="modalMediaContainer" class="bg-slate-900/80 rounded-2xl overflow-hidden mb-6 border border-slate-800 aspect-[16/9] relative"></div>

            <div class="space-y-4 text-slate-300 text-sm sm:text-base leading-relaxed">
                <p id="modalDescription"></p>

                <div id="modalSpecsBox" class="bg-slate-900/70 rounded-2xl p-4 border border-slate-800">
                    <h4 class="font-bold text-amber-400 text-sm uppercase tracking-wider mb-2">Asosiy xususiyatlar va Texnik jihatlar:</h4>
                    <ul id="modalSpecs" class="list-disc list-inside space-y-1.5 text-slate-300 text-sm"></ul>
                </div>

                <div id="modalFactBox" class="bg-cyan-950/30 rounded-2xl p-4 border border-cyan-500/20">
                    <h4 class="font-bold text-cyan-400 text-sm uppercase tracking-wider mb-1">Qiziqarli fakt:</h4>
                    <p id="modalFact" class="text-slate-200 text-sm"></p>
                </div>
            </div>
        </div>
    </div>

    <script>
        // =========================================================================
        // 1. ISHONCHLI SVG ZAXIRA RASM TIZIMI (onerror orqali ishga tushadi)
        // =========================================================================
        function getFallbackSvgDataUri(type = 'default') {
            const palette = {
                sport: '#f43f5e',
                suv: '#06b6d4',
                ev: '#10b981',
                classic: '#f59e0b',
                default: '#f59e0b'
            };
            const strokeColor = palette[type] || palette.default;
            const svg = `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 420 230" width="420" height="230">
                <rect width="420" height="230" fill="#0f172a"/>
                <circle cx="210" cy="115" r="95" fill="${strokeColor}" fill-opacity="0.08"/>
                <path d="M60 158 C72 128, 108 98, 165 95 H245 C288 98, 328 122, 360 140 V158 H315 C315 136, 282 136, 282 158 H138 C138 136, 105 136, 105 158 H60 Z" fill="#1e293b" stroke="${strokeColor}" stroke-width="3.5"/>
                <path d="M132 126 L170 101 H242 L284 126 H132 Z" fill="#0b0f19" stroke="#38bdf8" stroke-width="2"/>
                <circle cx="121" cy="160" r="23" fill="#090d16" stroke="#94a3b8" stroke-width="4.5"/>
                <circle cx="299" cy="160" r="23" fill="#090d16" stroke="#94a3b8" stroke-width="4.5"/>
                <text x="210" y="206" fill="#64748b" font-family="sans-serif" font-size="12" text-anchor="middle">AVTOTARIX ILUSTRATSIYASI</text>
            </svg>`;
            return 'data:image/svg+xml;charset=UTF-8,' + encodeURIComponent(svg);
        }

        window.handleImageFallback = function(imgElement, type = 'default') {
            if (!imgElement) return;
            imgElement.onerror = null;
            imgElement.src = getFallbackSvgDataUri(type);
        };

        // =========================================================================
        // 2. ALOHIDA OYNALAR (SAHIFALAR) BOSHQARUVCHISI
        // =========================================================================
        const validPages = ['home', 'history', 'types', 'gallery', 'quiz'];

        window.navigateTo = function(pageId, updateHash = true) {
            if (!validPages.includes(pageId)) pageId = 'home';

            document.querySelectorAll('.page-view').forEach(section => {
                section.classList.remove('active');
            });
            const activeView = document.getElementById(`view-${pageId}`);
            if (activeView) activeView.classList.add('active');

            document.querySelectorAll('.nav-tab').forEach(btn => {
                if (btn.getAttribute('data-page') === pageId) {
                    btn.className = 'nav-tab px-3.5 py-2 rounded-xl bg-amber-500 text-slate-950 font-bold shadow-md shadow-amber-500/20 transition-all';
                } else {
                    btn.className = 'nav-tab px-3.5 py-2 rounded-xl text-slate-300 hover:text-white hover:bg-slate-800/60 transition-all';
                }
            });

            document.querySelectorAll('.mobile-nav-tab').forEach(btn => {
                if (btn.getAttribute('data-page') === pageId) {
                    btn.className = 'mobile-nav-tab w-full text-left block px-4 py-3 rounded-xl bg-amber-500/20 text-amber-400 font-bold border border-amber-500/30 transition-colors';
                } else {
                    btn.className = 'mobile-nav-tab w-full text-left block px-4 py-3 rounded-xl text-slate-300 hover:bg-slate-800 transition-colors';
                }
            });

            document.getElementById('mobile-menu').classList.add('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });

            if (updateHash) {
                try {
                    history.replaceState(null, '', `#${pageId}`);
                } catch (e) {
                    window.location.hash = pageId;
                }
            }
        };

        document.querySelectorAll('.nav-tab, .mobile-nav-tab').forEach(btn => {
            btn.addEventListener('click', () => navigateTo(btn.getAttribute('data-page')));
        });

        window.addEventListener('hashchange', () => {
            const hash = window.location.hash.replace('#', '');
            navigateTo(hash || 'home', false);
        });

        // =========================================================================
        // 3. YARATILISH TARIXI MA'LUMOTLARI (1769 — HOZIRGACHA)
        // =========================================================================
        const timelineData = [
            {
                id: 't-1769',
                year: '1769-yil',
                title: 'Ilk Bug\'li Avtomobil (Fardier à vapeur)',
                inventor: 'Nikola-Jozef Kyuno (Fransiya)',
                image: 'https://images.unsplash.com/photo-1517524008697-84bbe3c3fd98?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'classic',
                shortDesc: 'Insoniyat tarixida o\'zi harakatlanuvchi birinchi mexanik transport vositasi yaratildi.',
                fullDesc: 'Fransuz muhandisi Nikola-Jozef Kyuno og\'ir artilleriya qurollarini tashish uchun bug\' dvigateli bilan ishlaydigan uch g\'ildirakli aravani ixtiro qildi. Bu avtomobilsozlik tarixidagi eng ilk tamal toshi bo\'ldi.',
                specs: [
                    'Dvigatel: Ikki silindrli bug\' mashinasi',
                    'Maksimal tezlik: ~4 km/soat',
                    'Yoqilg\'i: Ko\'mir va o\'tin yordamida qizdiriladigan suv bug\'i'
                ],
                fact: '1771-yilda ushbu bug\'li arava sinov paytida boshqaruvni yo\'qotib, devorga urilgan va tarixdagi ilk yo\'l hodisasini qayd etgan.'
            },
            {
                id: 't-1886',
                year: '1886-yil, 29-yanvar',
                title: 'Benz Patent-Motorwagen (Ilk Benzinli Avto)',
                inventor: 'Karl Benz (Germaniya)',
                image: 'https://images.unsplash.com/photo-1566008885218-90abf9200ddb?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'classic',
                shortDesc: 'Ichki yonuv dvigateliga ega zamonaviy avtomobilning rasmiy yaratilgan kuni.',
                fullDesc: 'Germaniyalik muhandis Karl Benz benzin bilan ishlovchi to\'rt taktli ichki yonuv dvigatelli uch g\'ildirakli avtomobil uchun DRP 37435 patentini oldi. Shu sana zamonaviy avtomobil tug\'ilgan kun hisoblanadi.',
                specs: [
                    'Quvvat: 0.75 ot kuchi (1 silindr, 954 sm³)',
                    'Maksimal tezlik: 16 km/soat',
                    'Tuzilishi: Yengil metall rama va katta g\'ildiraklar'
                ],
                fact: '1888-yilda Karl Benzning rafiqasi Berta Benz eriga aytmasdan ikki o\'g\'li bilan ushbu mashinada 106 km yo\'l bosib, ilk uzoq masofali avtosayohatni amalga oshirgan.'
            },
            {
                id: 't-1908',
                year: '1908-yil, 1-oktabr',
                title: 'Ford Model T va Konveyer Inqilobi',
                inventor: 'Genri Ford (AQSH)',
                image: 'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'classic',
                shortDesc: 'Avtomobilni boylar o\'yinchog\'idan oddiy xalq transportiga aylantirgan model.',
                fullDesc: 'Genri Ford 1913-yilda joriy etgan harakatlanuvchi konveyer liniyasi ishlab chiqarish tannarxini keskin kamaytirdi. 1908–1927-yillar oralig\'ida 15 milliondan ortiq Model T ishlab chiqarildi.',
                specs: [
                    'Dvigatel: 2.9 litrli 4 silindrli, 20 ot kuchi',
                    'Uzatmalar qutisi: 2 pog\'onali planetar',
                    'Xususiyati: Mustahkam va oson ta\'mirlanadigan konstruksiya'
                ],
                fact: 'Model T dastlab turli ranglarda chiqqan, biroq tezkor bo\'yash talabi sababli 1914–1925-yillarda faqat qora rangda ishlab chiqarilgan.'
            },
            {
                id: 't-1997',
                year: '1997-yil, 10-dekabr',
                title: 'Toyota Prius — Dunyodagi Ilk Ommaviy Gibrid',
                inventor: 'Toyota Motor Corporation (Yaponiya)',
                image: 'https://images.unsplash.com/photo-1593941707882-a5bba14938c7?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'ev',
                shortDesc: 'Benzin va elektr dvigatelini uyg\'unlashtirgan ekologik yangi davr boshlanishi.',
                fullDesc: 'Toyota Prius ichki yonuv dvigateli va elektr motorini birlashtirib, yoqilg\'i tejamkorligi va zararli gazlarni kamaytirishda yangi standart yaratdi.',
                specs: [
                    'Tizim: Ketma-parallel gibrid (Hybrid Synergy Drive)',
                    'Afzalligi: Past yoqilg\'i sarfi va regenerativ tormozlash',
                    'Ta\'siri: Keyingi avlod gibrid va EV texnologiyalariga yo\'l ochdi'
                ],
                fact: 'Prius nomi lotincha so\'zdan olingan bo\'lib, "avvalgi" yoki "oldinga yuruvchi" ma\'nosini anglatadi.'
            },
            {
                id: 't-2008',
                year: '2008-yil',
                title: 'Zamonaviy Elektromobillar Davri (Tesla Roadster)',
                inventor: 'Tesla Motors (AQSH)',
                image: 'https://images.unsplash.com/photo-1560958089-b8a1929cea89?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'ev',
                shortDesc: 'Litiy-ion batareyali elektromobil 350 km dan ortiq yurish masofasini namoyish etdi.',
                fullDesc: 'Zamonaviy litiy-ion akkumulyator texnologiyalari elektromobillarning shahar ichidagi qisqa masofali transportdan uzoq safarlarga mos kuchli avtomobillarga aylanishini ta\'minladi.',
                specs: [
                    'Quvvat manbai: Litiy-ion batareya paketi',
                    'Xususiyati: 0 dan boshlab maksimal moment beruvchi elektr motor',
                    'Zamonaviy tendensiya: Tezkor zaryadlash va avtopilot tizimlari'
                ],
                fact: 'Elektr dvigateli ichki yonuv dvigateliga qaraganda ancha kam harakatlanuvchi qismlardan iborat.'
            }
        ];

        // =========================================================================
        // 4. KENGAYTIRILGAN AVTOMOBIL TURLARI (16 TA TUR)
        // Guruhlar: 'daily' (Kundalik va Oila), 'speed' (Tezlik va Sport), 'eco' (Ekologik va Maxsus)
        // =========================================================================
        const carTypesData = [
            {
                id: 'sedan',
                name: 'Sedan',
                category: 'daily',
                categoryLabel: 'Kundalik va Oila',
                era: 'Yaratilish davri: XX asr boshlari (1910-yillar)',
                image: 'https://images.unsplash.com/photo-1555215695-3004980ad54e?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'default',
                shortDesc: '4 eshikli, 5 o\'rinli va alohida yukxona (bagaj) bo\'lmaga ega eng ommabop yengil avtomobil.',
                examples: 'Toyota Camry, BMW 3-Series, Mercedes-Benz E-Class',
                specs: [
                    'Kuzov: 3 qismli (dvigatel, salon, alohida bagaj)',
                    'Afzalligi: Qulaylik, barqarorlik va shahar-trassa muvozanati',
                    'Qo\'llanilishi: Kundalik yurish, oilaviy safar va biznes'
                ],
                fact: 'Inglizcha "sedan" atamasi dastlab XVIII asrda odamlar tashilgan yopiq zambilga nisbatan ishlatilgan.'
            },
            {
                id: 'suv',
                name: 'SUV / Yo\'ltanlamas',
                category: 'daily',
                categoryLabel: 'Kundalik va Oila',
                era: 'Yaratilish davri: 1940–1980-yillar (Willys Jeep, Range Rover)',
                image: 'https://images.unsplash.com/photo-1519641471654-76ce0107ad1b?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'suv',
                shortDesc: 'Yuqori klirens, mustahkam tuzilma va ko\'pincha to\'liq g\'ildirak tortish (AWD/4WD) tizimiga ega avtomobil.',
                examples: 'Toyota Land Cruiser, Range Rover, Jeep Wrangler',
                specs: [
                    'Afzalligi: Og\'ir yo\'llar, loy, qor va tog\'larda yuqori o\'tuvchanlik',
                    'Ko\'rinish: Haydovchi uchun baland va keng ko\'rinish burchagi',
                    'Tuzilishi: Rama yoki kuchaytirilgan ko\'taruvchi kuzov'
                ],
                fact: '1970-yilda chiqqan ilk Range Rover ham yo\'ltanlamas kuchini, ham lyuks salon qulayligini birlashtirgan.'
            },
            {
                id: 'sport',
                name: 'Sportkar',
                category: 'speed',
                categoryLabel: 'Tezlik va Sport',
                era: 'Yaratilish davri: 1920–1950-yillar',
                image: 'https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'sport',
                shortDesc: 'Yuqori tezlik, tezkor tezlashuv, keskin boshqaruv va aerodinamik shaklga yo\'naltirilgan avtomobil.',
                examples: 'Porsche 911, Chevrolet Corvette, Nissan GT-R',
                specs: [
                    'Dinamika: Past markaziy og\'irlik va kuchli dvigatel',
                    'Boshqaruv: Qattiqroq podveska va aniq rul tizimi',
                    'Maqsad: Sport trassalari va faol haydash zavqi'
                ],
                fact: 'Sportkarlar ko\'pincha yengil alyuminiy yoki karbon detallardan yasaladi.'
            },
            {
                id: 'ev',
                name: 'Elektromobil (EV)',
                category: 'eco',
                categoryLabel: 'Ekologik va Maxsus',
                era: 'Yaratilish davri: XIX asr oxiri (1880-yillar) / Zamonaviy boom: 2008+',
                image: 'https://images.unsplash.com/photo-1560958089-b8a1929cea89?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'ev',
                shortDesc: 'Faqat elektr dvigatel va akkumulyator batareyasi yordamida harakatlanuvchi ekologik toza transport.',
                examples: 'Tesla Model 3, Porsche Taycan, Hyundai Ioniq 5',
                specs: [
                    'Ekologiya: Harakat paytida chiqindi gaz chiqarmaydi',
                    'Texnologiya: Tinch yurish va tezkor moment uzatish',
                    'Quvvatlash: Elektr tarmog\'i va maxsus zaryad stansiyalari'
                ],
                fact: '1900-yil atrofida Nyu-York taksilarining bir qismi aynan elektromobil bo\'lgan.'
            },
            {
                id: 'coupe',
                name: 'Kupe (Coupe)',
                category: 'speed',
                categoryLabel: 'Tezlik va Sport',
                era: 'Yaratilish davri: XX asr 20–30-yillari',
                image: 'https://images.unsplash.com/photo-1583121274602-3e2820c69888?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'sport',
                shortDesc: 'Odatda 2 eshikli, orqa tomoni qiya tushuvchi sportcha va nafis siluetli avtomobil.',
                examples: 'Audi A5 Coupe, Ford Mustang, Mercedes-Benz C-Class Coupe',
                specs: [
                    'Dizayn: Past tom chizig\'i va dinamik ko\'rinish',
                    'Eshiklar: Asosan 2 ta yon eshik',
                    'Xususiyati: Sport uslubi va shaxsiy qulaylik'
                ],
                fact: 'Fransuzcha "couper" so\'zi "kesish" ma\'nosini bildirib, dastlab qisqartirilgan kuzovli ekipajni anglatgan.'
            },
            {
                id: 'retro',
                name: 'Retro / Klassik',
                category: 'eco',
                categoryLabel: 'Ekologik va Maxsus',
                era: 'Yaratilish davri: 1900–1980-yillar (hamda zamonaviy retro uslub)',
                image: 'https://images.unsplash.com/photo-1511919884226-fecbf30a6297?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'classic',
                shortDesc: 'Tarixiy ahamiyatga ega qadimiy modellar yoki o\'tmish dizayni ruhida yaratilgan avtomobillar.',
                examples: 'Volkswagen Beetle, Ford Mustang (1964), Mercedes-Benz 300SL',
                specs: [
                    'Qiymat: Kolleksiya, muzey va tarixiy meros ahamiyati',
                    'Uslub: Xromlangan detallar va o\'ziga xos salon',
                    'Texnika: Klassik mexanik yechimlar'
                ],
                fact: 'Klassik avtomobillar ko\'plab mamlakatlarda alohida tarixiy transport sifatida ro\'yxatga olinadi.'
            },
            {
                id: 'hatchback',
                name: 'Xetchbek',
                category: 'daily',
                categoryLabel: 'Kundalik va Oila',
                era: 'Yaratilish davri: 1930–1960-yillar',
                image: 'https://images.unsplash.com/photo-1609521263047-f8f205293f24?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'default',
                shortDesc: 'Orqa eshigi yukxona bilan birgalikda yuqoriga ochiluvchi, ixcham shahar avtomobili.',
                examples: 'Volkswagen Golf, Toyota Corolla Hatchback, Honda Civic',
                specs: [
                    'O\'lcham: Ixcham uzunlik va shahar tirbandligida qulaylik',
                    'Sig\'im: Orqa o\'rindiqlarni yig\'ib yuk joyini oshirish imkoni',
                    'Tejamkorlik: Nisbatan kam yoqilg\'i sarfi'
                ],
                fact: 'Xetchbek kuzovi shaharda mashina qo\'yish va yuk tashishni bir vaqtning o\'zida qulay qiladi.'
            },
            {
                id: 'pickup',
                name: 'Pikap',
                category: 'eco',
                categoryLabel: 'Ekologik va Maxsus',
                era: 'Yaratilish davri: 1910–1920-yillar',
                image: 'https://images.unsplash.com/photo-1559416523-140ddc3d238c?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'suv',
                shortDesc: 'Old qismida yo\'lovchi kabinasi va orqasida ochiq yuk platformasiga ega amaliy avtomobil.',
                examples: 'Ford F-150, Toyota Hilux, RAM 1500',
                specs: [
                    'Yuk ko\'tarish: Qurilish, xo\'jalik va safar yuklari uchun qulay',
                    'Chidamlilik: Og\'ir sharoitlarga moslashtirilgan shassi',
                    'Kabina: Bir yoki ikki qatorli yo\'lovchi kabinasi'
                ],
                fact: 'Pikaplar qishloq xo\'jaligi va qurilishdan tortib sayohat va off-road sportigacha keng qo\'llaniladi.'
            },
            {
                id: 'wagon',
                name: 'Universal (Wagon)',
                category: 'daily',
                categoryLabel: 'Kundalik va Oila',
                era: 'Yaratilish davri: 1920–1930-yillar',
                image: 'https://images.unsplash.com/photo-1502877338535-766e1452684a?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'default',
                shortDesc: 'Tom qismi sedan kabi orqagacha cho\'zilgan, keng yukxonali oilaviy va safar avtomobili.',
                examples: 'Audi A6 Avant, Volvo V90, Subaru Outback',
                specs: [
                    'Afzalligi: Sedan boshqaruvchanligi + katta yukxona hajmi',
                    'Safar: Uzoq masofali oilaviy sayohatlar uchun juda qulay',
                    'Amaliylik: Tom relinglari orqali qo\'shimcha yuk imkoni'
                ],
                fact: 'Yevropada universal avtomobillar uzoq yo\'llarda past shamol qarshiligi tufayli juda mashhur.'
            },
            {
                id: 'convertible',
                name: 'Kabriolet / Rodster',
                category: 'speed',
                categoryLabel: 'Tezlik va Sport',
                era: 'Yaratilish davri: XX asr boshlari',
                image: 'https://images.unsplash.com/photo-1542362567-891b3e24b6b5?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'sport',
                shortDesc: 'Yig\'iluvchi yoki olinadigan yumshoq/qattiq tomga ega ochiq kuzovli avtomobil.',
                examples: 'Mazda MX-5 Miata, Porsche 718 Boxster, BMW Z4',
                specs: [
                    'Kuzov: Ochiq osmon ostida yurish imkonini beruvchi tom',
                    'Rodster: Ko\'pincha 2 o\'rinli, engil va sportcha',
                    'Tafsilot: Maxsus mustahkamlangan kuzov konstruksiyasi'
                ],
                fact: 'Rodster atamasi dastlab tomisiz, yengil va tezkor ikki o\'rinli avtomobillarga berilgan.'
            },
            {
                id: 'minivan',
                name: 'Miniven / MPV',
                category: 'daily',
                categoryLabel: 'Kundalik va Oila',
                era: 'Yaratilish davri: 1980-yillar (Chrysler Voyager, Renault Espace)',
                image: 'https://images.unsplash.com/photo-1549317661-bd32c8ce0db2?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'default',
                shortDesc: 'Katta oilalar va guruhlar uchun mo\'ljallangan, 6–8 o\'rinli va keng ichki makonli avtomobil.',
                examples: 'Kia Carnival, Toyota Sienna, Mercedes-Benz V-Class',
                specs: [
                    'Sig\'im: 3 qatorli o\'rindiqlar va keng salon',
                    'Eshiklar: Ko\'pincha suriluvchi yon eshiklar',
                    'Qulaylik: Uzoq safarlarda yuqori yo\'lovchi qulayligi'
                ],
                fact: 'MPV (Multi-Purpose Vehicle) — ko\'p maqsadli transport vositasi degan ma\'noni anglatadi.'
            },
            {
                id: 'liftback',
                name: 'Liftbek / Fastbek',
                category: 'daily',
                categoryLabel: 'Kundalik va Oila',
                era: 'Yaratilish davri: 1960–1970-yillar',
                image: 'https://images.unsplash.com/photo-1617531653332-bd46c24f2068?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'default',
                shortDesc: 'Sedan siluetiga ega bo\'lsa-da, orqa oynasi bilan birga ko\'tariluvchi eshikli kuzov.',
                examples: 'Skoda Octavia Liftback, Audi A7 Sportback, Toyota Prius (ayrim avlod)',
                specs: [
                    'Uyg\'unlik: Nafis sedan ko\'rinishi + keng yukxona kirishi',
                    'Aerodinamika: Silliq tushuvchi orqa oyna chizig\'i',
                    'Amaliylik: Katta hajmli buyumlarni yuklash oson'
                ],
                fact: 'Liftbeklar o\'zining ko\'p qirraliligi tufayli Yevropa va Osiyoda keng tarqalgan.'
            },
            {
                id: 'crossover',
                name: 'Krossover (CUV)',
                category: 'daily',
                categoryLabel: 'Kundalik va Oila',
                era: 'Yaratilish davri: 1990-yillar oxiri — 2000-yillar boshlari',
                image: 'https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'suv',
                shortDesc: 'Yengil avtomobil platformasida yaratilgan, SUV ko\'rinishli va shaharga moslashgan avtomobil.',
                examples: 'Toyota RAV4, Honda CR-V, Hyundai Tucson',
                specs: [
                    'Platforma: Yengil avtomobil bazasi (monokok kuzov)',
                    'Tejamkorlik: Klassik og\'ir SUV larga nisbatan yumshoqroq va tejamkorroq',
                    'Universal: Shahar, yomg\'ir va yengil tuproq yo\'llar uchun mos'
                ],
                fact: 'Bugungi kunda krossoverlar dunyo bo\'yicha eng tez o\'sayotgan avtomobil segmentlaridan biridir.'
            },
            {
                id: 'limousine',
                name: 'Limuzin',
                category: 'eco',
                categoryLabel: 'Ekologik va Maxsus',
                era: 'Yaratilish davri: XX asr boshlari (1902–1920-yillar)',
                image: 'https://images.unsplash.com/photo-1563720223185-11003d516935?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'classic',
                shortDesc: 'Uzaytirilgan g\'ildirak bazasi, hashamatli ichki salon va yuqori darajadagi qulaylikka ega avtomobil.',
                examples: 'Mercedes-Maybach S-Class, Rolls-Royce Phantom Extended',
                specs: [
                    'Qulaylik: Orqa yo\'lovchilar uchun keng oyoq joyi va lyuks jihozlar',
                    'Maqom: Rasmiy uchrashuvlar, marosimlar va VIP safarlar',
                    'Maxfiylik: Tovush izolyatsiyasi va maxsus pardalar/oynalar'
                ],
                fact: 'Limuzin nomi dastlab Fransiyaning Limuzin viloyatidagi chopon uslubiga bog\'liq holda paydo bo\'lgan.'
            },
            {
                id: 'hypercar',
                name: 'Giperkar',
                category: 'speed',
                categoryLabel: 'Tezlik va Sport',
                era: 'Yaratilish davri: 1990-yillar oxiri — XXI asr (Bugatti Veyron, Koenigsegg)',
                image: 'https://images.unsplash.com/photo-1544636331-e26879cd4d9b?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'sport',
                shortDesc: 'Sportkardan ham yuqori quvvat (1000+ ot kuchi), noyob muhandislik va ekstremal tezlikka ega avtomobil.',
                examples: 'Bugatti Chiron, Koenigsegg Jesko, Rimac Nevera',
                specs: [
                    'Quvvat: 1000 ot kuchidan yuqori ko\'rsatkichlar',
                    'Materiallar: Karbon monokok, titan va eng yengil qotishmalar',
                    'Ishlab chiqarish: Cheklangan, noyob seriyalarda'
                ],
                fact: 'Giperkarlar aerodinamikani boshqarish uchun faol qanotlar va murakkab diffuzorlardan foydalanadi.'
            },
            {
                id: 'hybrid',
                name: 'Gibrid / Plug-in Gibrid',
                category: 'eco',
                categoryLabel: 'Ekologik va Maxsus',
                era: 'Yaratilish davri: 1997-yil (ommaviy) / Plug-in rivoji: 2010+',
                image: 'https://images.unsplash.com/photo-1593941707882-a5bba14938c7?auto=format&fit=crop&w=800&q=80',
                fallbackType: 'ev',
                shortDesc: 'Ichki yonuv dvigateli va elektr motorini birgalikda ishlatuvchi tejamkor va moslashuvchan avtomobil.',
                examples: 'Toyota Prius, BYD Song Plus DM-i, Lexus RX Hybrid',
                specs: [
                    'Moslashuvchanlik: Shaharda elektrda, uzoq masofada gibrid/benzin rejimida',
                    'Plug-in (PHEV): Rozetkadan zaryadlanib, ma\'lum masofani faqat elektrda bosadi',
                    'Tejamkorlik: Yoqilg\'i sarfini sezilarli kamaytiradi'
                ],
                fact: 'Gibrid tizim tormozlash paytidagi kinetik energiyani qayta elektr energiyasiga aylantira oladi.'
            }
        ];

        // =========================================================================
        // 5. FOTO GALEREYA MA'LUMOTLARI
        // =========================================================================
        const galleryData = [
            {
                id: 'g-1',
                title: 'Zamonaviy Giperkar Aerodinamikasi',
                category: 'supercar',
                categoryLabel: 'Sport & Giperkar',
                year: 'XXI asr',
                image: 'https://images.unsplash.com/photo-1544636331-e26879cd4d9b?auto=format&fit=crop&w=900&q=80',
                fallbackType: 'sport',
                desc: 'Yuqori tezlikdagi barqarorlik va maksimal quvvat uchun yaratilgan sport/giperkar dizayni.'
            },
            {
                id: 'g-2',
                title: 'Klassik Sport Kupe',
                category: 'supercar',
                categoryLabel: 'Sport & Giperkar',
                year: 'Klassik sport',
                image: 'https://images.unsplash.com/photo-1503376780353-7e6692767b70?auto=format&fit=crop&w=900&q=80',
                fallbackType: 'sport',
                desc: 'Past markaziy tortishish markazi va aniq boshqaruvga ega sport avtomobili.'
            },
            {
                id: 'g-3',
                title: 'Tarixiy Retro Avtomobil',
                category: 'retro',
                categoryLabel: 'Retro & Klassik',
                year: 'XX asr',
                image: 'https://images.unsplash.com/photo-1511919884226-fecbf30a6297?auto=format&fit=crop&w=900&q=80',
                fallbackType: 'classic',
                desc: 'Avtomobilsozlik tarixidagi o\'ziga xos dizayn va klassik uslub namunasi.'
            },
            {
                id: 'g-4',
                title: 'Ilk Mexanik Va Tarixiy Rux',
                category: 'retro',
                categoryLabel: 'Retro & Klassik',
                year: '1769–1920',
                image: 'https://images.unsplash.com/photo-1566008885218-90abf9200ddb?auto=format&fit=crop&w=900&q=80',
                fallbackType: 'classic',
                desc: 'Ilk ixtirolar va muhandislik izlanishlari ramzi.'
            },
            {
                id: 'g-5',
                title: 'Zamonaviy Elektromobil (EV)',
                category: 'ev',
                categoryLabel: 'EV & Gibrid',
                year: '2008-yildan',
                image: 'https://images.unsplash.com/photo-1560958089-b8a1929cea89?auto=format&fit=crop&w=900&q=80',
                fallbackType: 'ev',
                desc: 'Elektr dvigatel va zamonaviy akkumulyator texnologiyasiga ega avtomobil.'
            },
            {
                id: 'g-6',
                title: 'Gibrid Va Ekologik Transport',
                category: 'ev',
                categoryLabel: 'EV & Gibrid',
                year: '1997-yildan',
                image: 'https://images.unsplash.com/photo-1593941707882-a5bba14938c7?auto=format&fit=crop&w=900&q=80',
                fallbackType: 'ev',
                desc: 'Yoqilg\'i tejamkorligi va ekologik samaradorlikni uyg\'unlashtirgan yechim.'
            },
            {
                id: 'g-7',
                title: 'Yo\'ltanlamas SUV',
                category: 'suv',
                categoryLabel: 'SUV & Pikap',
                year: '1940–hozirgacha',
                image: 'https://images.unsplash.com/photo-1519641471654-76ce0107ad1b?auto=format&fit=crop&w=900&q=80',
                fallbackType: 'suv',
                desc: 'Murakkab yo\'l sharoitlari va keng oilaviy sayohatlar uchun mo\'ljallangan SUV.'
            },
            {
                id: 'g-8',
                title: 'Amaliy Yuk Platformali Pikap',
                category: 'suv',
                categoryLabel: 'SUV & Pikap',
                year: '1910–hozirgacha',
                image: 'https://images.unsplash.com/photo-1559416523-140ddc3d238c?auto=format&fit=crop&w=900&q=80',
                fallbackType: 'suv',
                desc: 'Ochiq kuzovli yuk bo\'lmasi va mustahkam shassiga ega pikap avtomobili.'
            },
            {
                id: 'g-9',
                title: 'Shahar va Trassa Sedani',
                category: 'suv',
                categoryLabel: 'SUV & Pikap',
                year: '1910–hozirgacha',
                image: 'https://images.unsplash.com/photo-1555215695-3004980ad54e?auto=format&fit=crop&w=900&q=80',
                fallbackType: 'default',
                desc: 'Qulaylik, boshqaruv aniqligi va kundalik foydalanish uyg\'unligi.'
            }
        ];

        // =========================================================================
        // 6. VIKTORINA SAVOLLARI
        // =========================================================================
        const quizData = [
            {
                question: '1. Birinchi benzinli ichki yonuv dvigatelli avtomobil (Benz Patent-Motorwagen) qaysi yilda patentlangan?',
                options: ['1769-yil', '1886-yil', '1908-yil', '1997-yil'],
                correct: 1,
                explanation: 'Karl Benz 1886-yil 29-yanvarda benzinli ichki yonuv dvigatelli avtomobil uchun patent olgan.'
            },
            {
                question: '2. Insoniyat tarixidagi ilk bug\'li aravani (1769-yil) kim ixtiro qilgan?',
                options: ['Genri Ford', 'Nikola-Jozef Kyuno', 'Karl Benz', 'Gotlib Daymler'],
                correct: 1,
                explanation: 'Fransuz ixtirochisi Nikola-Jozef Kyuno 1769-yilda bug\' dvigatelli aravani yaratgan.'
            },
            {
                question: '3. Konveyer ishlab chiqarishini keng joriy etib, avtomobilni ommalashtirgan model qaysi?',
                options: ['Toyota Prius', 'Ford Model T', 'Porsche 911', 'Volkswagen Golf'],
                correct: 1,
                explanation: 'Genri Fordning 1908-yilda taqdim etilgan Model T avtomobili ommaviy ishlab chiqarish ramziga aylangan.'
            },
            {
                question: '4. Qaysi kuzov turi orqa eshigi yukxona bilan birga yuqoriga ochilishi va ixchamligi bilan ajralib turadi?',
                options: ['Limuzin', 'Pikap', 'Xetchbek', 'Rodster'],
                correct: 2,
                explanation: 'Xetchbek kuzovi orqa yukxona eshigining yuqoriga ochilishi va shahar sharoitiga mos ixchamligi bilan tanilgan.'
            },
            {
                question: '5. Dunyodagi ilk ommaviy gibrid avtomobil (Toyota Prius) qaysi yilda taqdim etilgan?',
                options: ['1975-yil', '1988-yil', '1997-yil', '2008-yil'],
                correct: 2,
                explanation: 'Toyota Prius 1997-yil dekabr oyida Yaponiyada sotuvga chiqarilgan.'
            },
            {
                question: '6. Qaysi avtomobil turi oldinda yo\'lovchi kabinasi va orqada ochiq yuk platformasiga ega?',
                options: ['Pikap', 'Kupe', 'Limuzin', 'Universal'],
                correct: 0,
                explanation: 'Pikap avtomobillari ochiq yuk platformasi va mustahkam tuzilmasi bilan ajralib turadi.'
            }
        ];

        // =========================================================================
        // 7. RENDER FUNKSIYALARI (TARIX, 16 TUR, GALEREYA)
        // =========================================================================
        const timelineContainer = document.getElementById('timelineContainer');
        const carTypesGrid = document.getElementById('carTypesGrid');
        const galleryGrid = document.getElementById('galleryGrid');

        function renderTimeline(filterText = '') {
            const query = filterText.trim().toLowerCase();
            const filtered = timelineData.filter(item =>
                item.year.toLowerCase().includes(query) ||
                item.title.toLowerCase().includes(query) ||
                item.inventor.toLowerCase().includes(query) ||
                item.shortDesc.toLowerCase().includes(query)
            );

            if (filtered.length === 0) {
                timelineContainer.innerHTML = `<div class="glass-card rounded-2xl p-8 text-center text-slate-300">Qidiruv bo'yicha tarixiy bosqich topilmadi.</div>`;
                return;
            }

            timelineContainer.innerHTML = filtered.map((item, idx) => {
                const isLeft = idx % 2 === 0;
                return `
                    <div class="relative flex flex-col md:flex-row items-start ${isLeft ? 'md:justify-start' : 'md:justify-end'}">
                        <div class="hidden md:flex absolute left-1/2 -translate-x-1/2 w-5 h-5 rounded-full bg-amber-400 border-4 border-slate-950 shadow-md z-10 mt-6"></div>
                        <div class="md:hidden absolute left-[11px] top-7 w-4 h-4 rounded-full bg-amber-400 border-2 border-slate-950 z-10"></div>

                        <div onclick="openDetailModal('timeline', '${item.id}')" class="w-full md:w-[46%] pl-10 md:pl-0 ${isLeft ? 'md:pr-8' : 'md:pl-8'} cursor-pointer group">
                            <div class="glass-card rounded-2xl overflow-hidden border border-slate-800 hover:border-amber-500/50 transition-all duration-300 hover:-translate-y-1 shadow-lg">
                                <div class="relative h-44 sm:h-48 w-full overflow-hidden bg-slate-900">
                                    <img
                                        src="${item.image}"
                                        alt="${item.title}"
                                        onerror="handleImageFallback(this, '${item.fallbackType}')"
                                        class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
                                    >
                                    <div class="absolute inset-0 bg-gradient-to-t from-slate-950/90 via-slate-950/25 to-transparent"></div>
                                    <span class="absolute top-3 left-3 px-3 py-1 rounded-full text-xs font-bold bg-amber-500 text-slate-950 shadow">${item.year}</span>
                                </div>

                                <div class="p-5 sm:p-6">
                                    <h3 class="text-lg sm:text-xl font-bold text-white group-hover:text-amber-400 transition-colors">${item.title}</h3>
                                    <p class="text-xs sm:text-sm text-cyan-400 font-medium mt-1 mb-3">${item.inventor}</p>
                                    <p class="text-xs sm:text-sm text-slate-300 leading-relaxed mb-4">${item.shortDesc}</p>
                                    <span class="inline-flex items-center text-xs font-semibold text-amber-400 group-hover:translate-x-1 transition-transform">
                                        Batafsil texnik oyna &rarr;
                                    </span>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            }).join('');
        }

        let currentTypeFilter = 'all';
        let currentTypeSearch = '';

        function renderCarTypes() {
            const query = currentTypeSearch.trim().toLowerCase();
            const filtered = carTypesData.filter(car => {
                const matchesCategory = currentTypeFilter === 'all' || car.category === currentTypeFilter;
                const matchesSearch =
                    car.name.toLowerCase().includes(query) ||
                    car.era.toLowerCase().includes(query) ||
                    car.shortDesc.toLowerCase().includes(query) ||
                    car.examples.toLowerCase().includes(query);
                return matchesCategory && matchesSearch;
            });

            const noResults = document.getElementById('noResultsMessage');
            if (filtered.length === 0) {
                carTypesGrid.innerHTML = '';
                noResults.classList.remove('hidden');
                return;
            }

            noResults.classList.add('hidden');
            carTypesGrid.innerHTML = filtered.map(car => `
                <div onclick="openDetailModal('type', '${car.id}')" class="glass-card rounded-2xl overflow-hidden border border-slate-800 hover:border-cyan-500/50 transition-all duration-300 hover:-translate-y-1.5 cursor-pointer flex flex-col justify-between group shadow-lg">
                    <div>
                        <div class="relative h-44 w-full overflow-hidden bg-slate-900">
                            <img
                                src="${car.image}"
                                alt="${car.name}"
                                onerror="handleImageFallback(this, '${car.fallbackType}')"
                                class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
                            >
                            <div class="absolute inset-0 bg-gradient-to-t from-slate-950/85 via-transparent to-transparent"></div>
                            <span class="absolute top-3 left-3 px-2.5 py-1 rounded-lg bg-slate-950/80 border border-slate-700/80 text-[11px] font-semibold text-cyan-300">
                                ${car.categoryLabel}
                            </span>
                        </div>

                        <div class="p-5">
                            <h3 class="text-lg font-bold text-white group-hover:text-cyan-400 transition-colors">${car.name}</h3>
                            <p class="text-[11px] font-semibold text-amber-400 mt-1 mb-2.5">${car.era}</p>
                            <p class="text-xs sm:text-sm text-slate-300 leading-relaxed mb-3">${car.shortDesc}</p>
                        </div>
                    </div>

                    <div class="px-5 pb-5 pt-3 border-t border-slate-800/80">
                        <p class="text-[11px] text-slate-400 mb-3"><strong class="text-slate-200">Modellar:</strong> ${car.examples}</p>
                        <span class="text-xs font-semibold text-cyan-400 group-hover:underline">Batafsil ma'lumot &rarr;</span>
                    </div>
                </div>
            `).join('');
        }

        function renderGallery(gFilter = 'all') {
            const filtered = gFilter === 'all'
                ? galleryData
                : galleryData.filter(item => item.category === gFilter);

            galleryGrid.innerHTML = filtered.map(item => `
                <div onclick="openDetailModal('gallery', '${item.id}')" class="glass-card rounded-2xl overflow-hidden border border-slate-800 hover:border-emerald-500/50 transition-all cursor-pointer group shadow-lg">
                    <div class="relative aspect-[16/10] w-full overflow-hidden bg-slate-900">
                        <img
                            src="${item.image}"
                            alt="${item.title}"
                            onerror="handleImageFallback(this, '${item.fallbackType}')"
                            class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
                        >
                        <div class="absolute inset-0 bg-gradient-to-t from-slate-950/90 via-slate-950/20 to-transparent"></div>
                        <span class="absolute top-3 left-3 px-2.5 py-1 rounded-lg bg-slate-950/80 border border-slate-700 text-[11px] font-semibold text-emerald-400">${item.categoryLabel}</span>
                        <span class="absolute top-3 right-3 px-2.5 py-1 rounded-lg bg-slate-950/80 border border-slate-700 text-[11px] font-semibold text-slate-300">${item.year}</span>
                        <div class="absolute bottom-3 left-3 right-3">
                            <h3 class="text-base font-bold text-white group-hover:text-emerald-400 transition-colors">${item.title}</h3>
                            <p class="text-xs text-slate-300 mt-0.5 line-clamp-1">${item.desc}</p>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        // =========================================================================
        // 8. MODAL OYNA BOSHQARUVI
        // =========================================================================
        const detailModal = document.getElementById('detailModal');
        const closeModalBtn = document.getElementById('closeModalBtn');

        window.openDetailModal = function(kind, id) {
            let data = null;
            if (kind === 'timeline') {
                const found = timelineData.find(x => x.id === id);
                if (!found) return;
                data = {
                    badge: found.year,
                    title: found.title,
                    subtitle: `Ixtirochi / Davlat: ${found.inventor}`,
                    image: found.image,
                    fallbackType: found.fallbackType,
                    description: found.fullDesc,
                    specs: found.specs,
                    fact: found.fact
                };
            } else if (kind === 'type') {
                const found = carTypesData.find(x => x.id === id);
                if (!found) return;
                data = {
                    badge: `${found.categoryLabel} • ${found.era}`,
                    title: found.name,
                    subtitle: `Mashhur modellar: ${found.examples}`,
                    image: found.image,
                    fallbackType: found.fallbackType,
                    description: found.shortDesc,
                    specs: found.specs,
                    fact: found.fact
                };
            } else if (kind === 'gallery') {
                const found = galleryData.find(x => x.id === id);
                if (!found) return;
                data = {
                    badge: `${found.categoryLabel} • ${found.year}`,
                    title: found.title,
                    subtitle: 'Foto Galereya — Kattalashtirilgan ko\'rinish',
                    image: found.image,
                    fallbackType: found.fallbackType,
                    description: found.desc,
                    specs: [
                        `Kategoriya: ${found.categoryLabel}`,
                        `Davr: ${found.year}`,
                        'Rasmni yopish uchun tashqi maydonga yoki X tugmasiga bosing'
                    ],
                    fact: 'Har bir avtomobil turi o\'z davrining muhandislik va dizayn ehtiyojlariga javob berish uchun shakllangan.'
                };
            }

            if (!data) return;

            document.getElementById('modalBadge').textContent = data.badge;
            document.getElementById('modalTitle').textContent = data.title;
            document.getElementById('modalSubtitle').textContent = data.subtitle;
            document.getElementById('modalMediaContainer').innerHTML = `
                <img
                    src="${data.image}"
                    alt="${data.title}"
                    onerror="handleImageFallback(this, '${data.fallbackType}')"
                    class="w-full h-full object-cover"
                >
            `;
            document.getElementById('modalDescription').textContent = data.description;
            document.getElementById('modalSpecs').innerHTML = data.specs.map(s => `<li>${s}</li>`).join('');
            document.getElementById('modalFact').textContent = data.fact;

            detailModal.classList.remove('hidden');
            detailModal.classList.add('flex');
            document.body.style.overflow = 'hidden';
        };

        function closeDetailModal() {
            detailModal.classList.add('hidden');
            detailModal.classList.remove('flex');
            document.body.style.overflow = '';
        }

        closeModalBtn.addEventListener('click', closeDetailModal);
        detailModal.addEventListener('click', (e) => {
            if (e.target === detailModal) closeDetailModal();
        });
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape' && !detailModal.classList.contains('hidden')) {
                closeDetailModal();
            }
        });

        // =========================================================================
        // 9. QIDIRUV, FILTRLAR VA VIKTORINA MANTIQI
        // =========================================================================
        document.getElementById('mobile-menu-btn').addEventListener('click', () => {
            document.getElementById('mobile-menu').classList.toggle('hidden');
        });

        document.getElementById('historySearchInput').addEventListener('input', (e) => {
            renderTimeline(e.target.value);
        });

        document.getElementById('typesSearchInput').addEventListener('input', (e) => {
            currentTypeSearch = e.target.value;
            renderCarTypes();
        });

        document.querySelectorAll('.filter-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                document.querySelectorAll('.filter-btn').forEach(b => {
                    b.className = 'filter-btn px-4 py-2.5 rounded-xl text-xs sm:text-sm font-semibold glass-card text-slate-300 hover:text-white transition-all';
                });
                btn.className = 'filter-btn active px-4 py-2.5 rounded-xl text-xs sm:text-sm font-semibold bg-amber-500 text-slate-950 shadow-md transition-all';
                currentTypeFilter = btn.getAttribute('data-filter');
                renderCarTypes();
            });
        });

        document.getElementById('resetAllFilters').addEventListener('click', () => {
            currentTypeFilter = 'all';
            currentTypeSearch = '';
            document.getElementById('typesSearchInput').value = '';
            document.querySelectorAll('.filter-btn').forEach(b => {
                if (b.getAttribute('data-filter') === 'all') {
                    b.className = 'filter-btn active px-4 py-2.5 rounded-xl text-xs sm:text-sm font-semibold bg-amber-500 text-slate-950 shadow-md transition-all';
                } else {
                    b.className = 'filter-btn px-4 py-2.5 rounded-xl text-xs sm:text-sm font-semibold glass-card text-slate-300 hover:text-white transition-all';
                }
            });
            renderCarTypes();
        });

        document.querySelectorAll('.g-filter-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                document.querySelectorAll('.g-filter-btn').forEach(b => {
                    b.className = 'g-filter-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-semibold glass-card text-slate-300 hover:text-white transition-all';
                });
                btn.className = 'g-filter-btn px-4 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-emerald-500 text-slate-950 transition-all';
                renderGallery(btn.getAttribute('data-gfilter'));
            });
        });

        // Viktorina boshqaruvi
        let currentQuizIndex = 0;
        let score = 0;
        let answered = false;

        const quizQuestionEl = document.getElementById('quizQuestion');
        const quizOptionsEl = document.getElementById('quizOptions');
        const quizFeedbackEl = document.getElementById('quizFeedback');
        const nextQuestionBtn = document.getElementById('nextQuestionBtn');
        const quizStepText = document.getElementById('quizStepText');
        const quizScoreText = document.getElementById('quizScoreText');
        const quizProgressBar = document.getElementById('quizProgressBar');
        const quizBox = document.getElementById('quizBox');
        const quizResultBox = document.getElementById('quizResultBox');

        function loadQuizQuestion() {
            answered = false;
            const q = quizData[currentQuizIndex];
            quizStepText.textContent = `Savol: ${currentQuizIndex + 1} / ${quizData.length}`;
            quizScoreText.textContent = `Ball: ${score}`;
            quizProgressBar.style.width = `${((currentQuizIndex + 1) / quizData.length) * 100}%`;
            quizQuestionEl.textContent = q.question;
            quizFeedbackEl.classList.add('hidden');
            nextQuestionBtn.classList.add('hidden');
            quizOptionsEl.innerHTML = '';

            q.options.forEach((opt, idx) => {
                const btn = document.createElement('button');
                btn.type = 'button';
                btn.className = 'w-full text-left px-5 py-3.5 rounded-xl bg-slate-900/80 hover:bg-slate-800 border border-slate-700/80 text-slate-200 text-sm sm:text-base font-medium transition-all flex items-center justify-between';
                btn.innerHTML = `<span>${opt}</span><span class="text-xs text-slate-500">Tanlash</span>`;
                btn.addEventListener('click', () => selectQuizOption(idx, btn));
                quizOptionsEl.appendChild(btn);
            });
        }

        function selectQuizOption(selectedIdx, btnElement) {
            if (answered) return;
            answered = true;
            const q = quizData[currentQuizIndex];
            const allOptionBtns = quizOptionsEl.querySelectorAll('button');

            allOptionBtns.forEach((b, i) => {
                b.disabled = true;
                if (i === q.correct) {
                    b.className = 'w-full text-left px-5 py-3.5 rounded-xl bg-emerald-500/20 border border-emerald-500 text-emerald-300 text-sm sm:text-base font-semibold flex items-center justify-between';
                    b.innerHTML = `<span>${q.options[i]}</span><span class="text-xs font-bold">To'g'ri</span>`;
                }
            });

            if (selectedIdx === q.correct) {
                score++;
                quizScoreText.textContent = `Ball: ${score}`;
                quizFeedbackEl.className = 'mt-5 p-4 rounded-xl text-sm bg-emerald-950/50 border border-emerald-500/30 text-emerald-200';
                quizFeedbackEl.innerHTML = `<strong>Barakalla!</strong> ${q.explanation}`;
            } else {
                btnElement.className = 'w-full text-left px-5 py-3.5 rounded-xl bg-rose-500/20 border border-rose-500 text-rose-300 text-sm sm:text-base font-semibold flex items-center justify-between';
                btnElement.innerHTML = `<span>${q.options[selectedIdx]}</span><span class="text-xs font-bold">Xato</span>`;
                quizFeedbackEl.className = 'mt-5 p-4 rounded-xl text-sm bg-rose-950/50 border border-rose-500/30 text-rose-200';
                quizFeedbackEl.innerHTML = `<strong>Noto'g'ri javob.</strong> ${q.explanation}`;
            }

            quizFeedbackEl.classList.remove('hidden');
            nextQuestionBtn.classList.remove('hidden');
            nextQuestionBtn.textContent = currentQuizIndex === quizData.length - 1 ? 'Natijani ko\'rish' : 'Keyingi savol →';
        }

        nextQuestionBtn.addEventListener('click', () => {
            currentQuizIndex++;
            if (currentQuizIndex < quizData.length) {
                loadQuizQuestion();
            } else {
                showQuizResult();
            }
        });

        function showQuizResult() {
            quizBox.classList.add('hidden');
            quizResultBox.classList.remove('hidden');
            document.getElementById('finalScoreDisplay').textContent = `${score}/${quizData.length}`;

            const resultTitle = document.getElementById('resultTitle');
            const resultDesc = document.getElementById('resultDesc');

            if (score === quizData.length) {
                resultTitle.textContent = 'Haqiqiy Avto-Ekspert!';
                resultDesc.textContent = 'Siz avtomobillar tarixi va turlari bo\'yicha barcha savollarga mukammal javob berdingiz!';
            } else if (score >= 4) {
                resultTitle.textContent = 'Juda yaxshi natija!';
                resultDesc.textContent = 'Siz avtomobilsozlik tarixi va asosiy turlarini yaxshi bilasiz. Yana bir bor sinab ko\'rishingiz mumkin.';
            } else {
                resultTitle.textContent = 'Yaxshi boshlanish!';
                resultDesc.textContent = 'Yaratilish Tarixi va Avtomobil Turlari oynalarini ko\'rib chiqib, testni qayta topshirib ko\'ring.';
            }
        }

        document.getElementById('restartQuizBtn').addEventListener('click', () => {
            currentQuizIndex = 0;
            score = 0;
            quizResultBox.classList.add('hidden');
            quizBox.classList.remove('hidden');
            loadQuizQuestion();
        });

        // Boshlang'ich yuklash
        renderTimeline();
        renderCarTypes();
        renderGallery();
        loadQuizQuestion();

        const initialHash = window.location.hash.replace('#', '');
        navigateTo(validPages.includes(initialHash) ? initialHash : 'home', false);
    </script>
</body>
</html>
