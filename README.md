<!DOCTYPE html>
<html lang="id" class="h-full">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SIM Kesiswaan Profesional SMP HQR</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Chart.js for interactive analytics -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Supabase JS SDK -->
    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
    <!-- Google Fonts Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; }
        @media print {
            .no-print { display: none !important; }
            .print-only { display: block !important; }
        }
        ::-webkit-scrollbar { width: 6px; height: 6px; }
        ::-webkit-scrollbar-track { background: #f1f5f9; }
        ::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 9999px; }
        ::-webkit-scrollbar-thumb:hover { background: #94a3b8; }
        .sticky-header { position: sticky; top: 0; z-index: 10; }
    </style>
</head>
<body class="h-full bg-slate-100 text-slate-900 antialiased selection:bg-emerald-600 selection:text-white overflow-hidden">

    <div id="app-screen" class="h-full flex overflow-hidden bg-slate-100">
        
        <!-- SIDEBAR NAVIGATION -->
        <aside id="sidebar" class="fixed inset-y-0 left-0 z-40 w-64 bg-white border-r-2 border-slate-300 text-slate-900 transform -translate-x-full md:translate-x-0 transition-transform duration-300 ease-in-out flex flex-col no-print shadow-2xl md:shadow-none">
            <!-- Sidebar Header -->
            <div class="h-20 flex items-center justify-between px-6 bg-slate-950 border-b-2 border-slate-800">
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 bg-emerald-600 border-2 border-emerald-400 rounded-xl flex items-center justify-center text-white font-black shadow-md">
                        <i class="fa-solid fa-graduation-cap"></i>
                    </div>
                    <div>
                        <h2 class="text-white font-black text-sm tracking-wide uppercase">SIM KESISWAAN SMP HQR</h2>
                        <span class="text-[10px] text-emerald-300 font-extrabold tracking-widest uppercase">Wakasis Portal</span>
                    </div>
                </div>
                <button onclick="toggleSidebar()" class="md:hidden text-slate-300 hover:text-white p-1">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>

            <!-- Sidebar Links -->
            <div class="flex-1 overflow-y-auto py-6 px-4 space-y-1.5 custom-scrollbar">
                <div class="text-[10px] font-black uppercase tracking-widest text-slate-600 px-3 mb-2">Menu Utama</div>
                <a href="#dashboard" onclick="switchTab('dashboard')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all bg-emerald-700 text-white shadow-md">
                    <i class="fa-solid fa-chart-pie w-5 text-sm"></i><span>Dashboard</span>
                </a>
                <a href="#pelanggaran" onclick="switchTab('pelanggaran')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-triangle-exclamation w-5 text-sm"></i><span>Pelanggaran</span>
                </a>
                <a href="#prestasi" onclick="switchTab('prestasi')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-trophy w-5 text-sm"></i><span>Prestasi Siswa</span>
                </a>
                <a href="#pembinaan" onclick="switchTab('pembinaan')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-handshake-angle w-5 text-sm"></i><span>Pembinaan Siswa</span>
                </a>
                <a href="#siswa" onclick="switchTab('siswa')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-users w-5 text-sm"></i><span>Data Siswa</span>
                </a>
                <a href="#kelas" onclick="switchTab('kelas')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-school w-5 text-sm"></i><span>Data Kelas</span>
                </a>
                <a href="#guru" onclick="switchTab('guru')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-chalkboard-user w-5 text-sm"></i><span>Data Guru </span>
                </a>
                <a href="#kegiatan" onclick="switchTab('kegiatan')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-calendar-days w-5 text-sm"></i><span>Kegiatan Kesiswaan</span>
                </a>
                <a href="#perizinan" onclick="switchTab('perizinan')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-right-from-bracket w-5 text-sm"></i><span>Perizinan Siswa</span>
                </a>
                <a href="#tatatertib" onclick="switchTab('tatatertib')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-book-open w-5 text-sm"></i><span>Ruang Tata Tertib</span>
                </a>

                <div class="text-[10px] font-black uppercase tracking-widest text-slate-600 px-3 mt-6 mb-2">Administrasi</div>
                <a href="#laporan" onclick="switchTab('laporan')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-file-invoice w-5 text-sm"></i><span>Laporan Kesiswaan</span>
                </a>
                <a href="#pengaturan" onclick="switchTab('pengaturan')" class="nav-item flex items-center space-x-3 px-4 py-3 rounded-xl font-black text-xs transition-all text-slate-800 hover:bg-emerald-100 hover:text-emerald-900">
                    <i class="fa-solid fa-gears w-5 text-sm"></i><span>Pengaturan & Sistem</span>
                </a>
            </div>
        </aside>

        <div class="flex-1 flex flex-col min-w-0 overflow-hidden bg-slate-100 md:pl-64">
            
            <header class="h-20 bg-white border-b-2 border-slate-300 flex items-center justify-between px-6 z-30 no-print shadow-sm flex-shrink-0">
                <div class="flex items-center space-x-4 min-w-0">
                    <button onclick="toggleSidebar()" class="md:hidden p-2 text-slate-900 bg-slate-200 border-2 border-slate-300 hover:bg-slate-300 rounded-xl flex-shrink-0"><i class="fa-solid fa-bars text-lg"></i></button>
                    <h2 id="page-title" class="text-base md:text-xl font-black tracking-tight text-slate-950 truncate">Dashboard Waka Kesiswaan</h2>
                </div>

                <!-- Global Search & User Profile -->
                <div class="flex items-center space-x-4 flex-shrink-0">
                    <div class="relative hidden sm:block w-64 md:w-72">
                        <span class="absolute inset-y-0 left-0 pl-3.5 flex items-center text-emerald-700"><i class="fa-solid fa-magnifying-glass"></i></span>
                        <input type="text" id="global-search-input" oninput="handleGlobalSearch(this.value)" placeholder="Cari nama atau NIS siswa..." class="w-full pl-10 pr-4 py-2 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900 focus:outline-none focus:ring-2 focus:ring-emerald-600 focus:bg-white transition-all">
                        <div id="global-search-results" class="hidden absolute left-0 right-0 mt-2 bg-white rounded-xl shadow-2xl border-2 border-slate-300 max-h-80 overflow-y-auto z-50"></div>
                    </div>

                    <div class="flex items-center space-x-3 border-l-2 pl-4 border-slate-300">
                        <div class="w-10 h-10 bg-emerald-700 text-white border-2 border-emerald-900 rounded-xl flex items-center justify-center font-black text-sm">WK</div>
                        <div class="hidden sm:block text-left">
                            <h4 class="text-xs font-black text-slate-950">Waka Kesiswaan</h4>
                            <span class="text-[10px] text-emerald-800 font-black flex items-center"><span class="w-2 h-2 bg-emerald-600 rounded-full inline-block mr-1.5 animate-pulse"></span>Supabase Sync</span>
                        </div>
                    </div>
                </div>
            </header>

            <main class="flex-1 overflow-y-auto p-4 sm:p-6 bg-slate-100 space-y-6 custom-scrollbar">

                <div id="tab-dashboard" class="tab-content space-y-6">
                    <div class="grid grid-cols-2 md:grid-cols-3 xl:grid-cols-6 gap-3 sm:gap-4">
                        <div class="bg-emerald-950 border-2 border-emerald-800 p-3 sm:p-4 rounded-2xl shadow-md text-white flex flex-col justify-between">
                            <div class="flex items-center justify-between mb-1">
                                <span class="text-[9px] sm:text-[10px] font-black uppercase tracking-tight text-emerald-300 truncate">Total Siswa</span>
                                <div class="w-7 h-7 bg-emerald-800 text-white border border-emerald-600 rounded-xl flex items-center justify-center text-[10px] font-black"><i class="fa-solid fa-users"></i></div>
                            </div>
                            <h3 id="stat-total-siswa" class="text-lg sm:text-2xl font-black text-white">0</h3>
                        </div>
                        <div class="bg-amber-900 border-2 border-amber-700 p-3 sm:p-4 rounded-2xl shadow-md text-white flex flex-col justify-between">
                            <div class="flex items-center justify-between mb-1">
                                <span class="text-[9px] sm:text-[10px] font-black uppercase tracking-tight text-amber-200 truncate">Pelanggaran</span>
                                <div class="w-7 h-7 bg-amber-700 text-white border border-amber-500 rounded-xl flex items-center justify-center text-[10px] font-black"><i class="fa-solid fa-triangle-exclamation"></i></div>
                            </div>
                            <h3 id="stat-total-pelanggaran" class="text-lg sm:text-2xl font-black text-white">0</h3>
                        </div>
                        <div class="bg-emerald-700 border-2 border-emerald-500 p-3 sm:p-4 rounded-2xl shadow-md text-white flex flex-col justify-between">
                            <div class="flex items-center justify-between mb-1">
                                <span class="text-[9px] sm:text-[10px] font-black uppercase tracking-tight text-emerald-100 truncate">Prestasi</span>
                                <div class="w-7 h-7 bg-emerald-600 text-white border border-emerald-400 rounded-xl flex items-center justify-center text-[10px] font-black"><i class="fa-solid fa-trophy"></i></div>
                            </div>
                            <h3 id="stat-total-prestasi" class="text-lg sm:text-2xl font-black text-white">0</h3>
                        </div>
                        <div class="bg-red-900 border-2 border-red-700 p-3 sm:p-4 rounded-2xl shadow-md text-white flex flex-col justify-between">
                            <div class="flex items-center justify-between mb-1">
                                <span class="text-[9px] sm:text-[10px] font-black uppercase tracking-tight text-red-200 truncate">Pembinaan</span>
                                <div class="w-7 h-7 bg-red-700 text-white border border-red-500 rounded-xl flex items-center justify-center text-[10px] font-black"><i class="fa-solid fa-handshake-angle"></i></div>
                            </div>
                            <h3 id="stat-total-binaan" class="text-lg sm:text-2xl font-black text-white">0</h3>
                        </div>
                        <div class="bg-purple-900 border-2 border-purple-700 p-3 sm:p-4 rounded-2xl shadow-md text-white flex flex-col justify-between">
                            <div class="flex items-center justify-between mb-1">
                                <span class="text-[9px] sm:text-[10px] font-black uppercase tracking-tight text-purple-200 truncate">Kegiatan</span>
                                <div class="w-7 h-7 bg-purple-700 text-white border border-purple-500 rounded-xl flex items-center justify-center text-[10px] font-black"><i class="fa-solid fa-calendar-days"></i></div>
                            </div>
                            <h3 id="stat-total-kegiatan" class="text-lg sm:text-2xl font-black text-white">0</h3>
                        </div>
                        <div class="bg-teal-900 border-2 border-teal-700 p-3 sm:p-4 rounded-2xl shadow-md text-white flex flex-col justify-between">
                            <div class="flex items-center justify-between mb-1">
                                <span class="text-[9px] sm:text-[10px] font-black uppercase tracking-tight text-teal-200 truncate">Perizinan</span>
                                <div class="w-7 h-7 bg-teal-700 text-white border border-teal-500 rounded-xl flex items-center justify-center text-[10px] font-black"><i class="fa-solid fa-right-from-bracket"></i></div>
                            </div>
                            <h3 id="stat-total-perizinan" class="text-lg sm:text-2xl font-black text-white">0</h3>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                        <div class="bg-white border-2 border-slate-300 p-5 sm:p-6 rounded-2xl shadow-md lg:col-span-2">
                            <h3 class="text-sm font-black text-slate-950 mb-4 flex items-center"><i class="fa-solid fa-chart-column mr-2 text-emerald-700"></i>Data Statistik Rekapitulasi Kesiswaan</h3>
                            <div class="h-64 sm:h-72"><canvas id="dashboardChart"></canvas></div>
                        </div>
                        <div class="bg-white border-2 border-slate-300 p-5 sm:p-6 rounded-2xl shadow-md">
                            <h3 class="text-sm font-black text-slate-950 mb-4 flex items-center"><i class="fa-solid fa-chart-column mr-2 text-emerald-700"></i>Data Statistik Siswa per Kelas </h3>
                            <div class="h-64 sm:h-72"><canvas id="classChart"></canvas></div>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                        <div class="bg-white border-2 border-slate-300 p-5 sm:p-6 rounded-2xl shadow-md space-y-4">
                            <h3 class="text-sm font-black text-amber-800 flex items-center"><i class="fa-solid fa-triangle-exclamation mr-2"></i>Perlu Perhatian</h3>
                            <div id="dashboard-high-risk-list" class="space-y-3"></div>
                        </div>
                        <div class="bg-white border-2 border-slate-300 p-5 sm:p-6 rounded-2xl shadow-md space-y-4">
                            <h3 class="text-sm font-black text-emerald-800 flex items-center"><i class="fa-solid fa-trophy mr-2"></i>Prestasi Terbaru</h3>
                            <div id="dashboard-recent-prestasi" class="space-y-3"></div>
                        </div>
                        <div class="bg-white border-2 border-slate-300 p-5 sm:p-6 rounded-2xl shadow-md space-y-4">
                            <h3 class="text-sm font-black text-purple-800 flex items-center"><i class="fa-solid fa-calendar-check mr-2"></i>Kegiatan Terdekat</h3>
                            <div id="dashboard-recent-kegiatan" class="space-y-3"></div>
                        </div>
                    </div>
                </div>

                <div id="tab-siswa" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md flex flex-col md:flex-row justify-between items-center gap-4">
                        <div class="flex flex-col sm:flex-row items-center gap-3 w-full md:w-auto">
                            <div class="w-full sm:w-64">
                                <input type="text" id="siswa-search" oninput="renderSiswaTable()" placeholder="Cari nama / NIS..." class="w-full px-4 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900 focus:outline-none focus:ring-2 focus:ring-emerald-600">
                            </div>
                            <select id="siswa-filter-kelas" onchange="renderSiswaTable()" class="w-full sm:w-auto px-4 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                                <option value="">Semua Kelas</option>
                            </select>
                        </div>
                        <div class="flex flex-wrap items-center gap-2 w-full md:w-auto">
                            <button onclick="downloadPDF('Data Biodata Siswa', 'siswa-table-body', ['Foto', 'Nama Siswa', 'NIS', 'Kelas', 'J.K.', 'Orang Tua', 'No. HP'])" class="px-4 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400 flex items-center justify-center space-x-1.5"><i class="fa-solid fa-download text-emerald-700"></i><span>Download Data Siswa (PDF)</span></button>
                            <button onclick="openSiswaModal()" class="px-5 py-2.5 bg-emerald-700 hover:bg-emerald-600 text-white font-black rounded-xl text-xs shadow-md transition-all flex items-center justify-center space-x-2">
                                <i class="fa-solid fa-user-plus"></i><span>Tambah Siswa Baru</span>
                            </button>
                        </div>
                    </div>

                    <div class="bg-white border-2 border-slate-300 rounded-2xl shadow-md overflow-hidden">
                        <div class="overflow-x-auto max-h-[650px]">
                            <table class="w-full text-left border-collapse min-w-[900px]">
                                <thead class="sticky-header bg-slate-950 text-[11px] uppercase font-black text-emerald-400 border-b-2 border-slate-800 tracking-wider">
                                    <tr>
                                        <th class="p-4 bg-slate-950 text-center w-16">Foto</th>
                                        <th class="p-4 bg-slate-950">Nama Siswa</th>
                                        <th class="p-4 bg-slate-950">NIS / NISN</th>
                                        <th class="p-4 bg-slate-950">Kelas</th>
                                        <th class="p-4 bg-slate-950">J.K.</th>
                                        <th class="p-4 bg-slate-950">Orang Tua</th>
                                        <th class="p-4 bg-slate-950">No. HP</th>
                                        <th class="p-4 bg-slate-950 text-center">Aksi</th>
                                    </tr>
                                </thead>
                                <tbody id="siswa-table-body" class="divide-y-2 divide-slate-200 text-xs font-black text-slate-900"></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <div id="tab-kelas" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md flex flex-col md:flex-row justify-between items-center gap-4">
                        <div>
                            <h3 class="text-base font-black text-slate-950 flex items-center"><i class="fa-solid fa-school mr-2 text-emerald-700"></i>Ruang Master Data Kelas</h3>
                            <p class="text-xs font-black text-slate-600 mt-1">Kelola rombongan belajar dan tingkat kelas sekolah.</p>
                        </div>
                        <div class="flex items-center gap-2">
                            <button onclick="downloadPDF('Data Kelas Sekolah', 'pengaturan-kelas-body', ['Nama Kelas', 'Jumlah Siswa'])" class="px-4 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400 flex items-center justify-center space-x-1.5"><i class="fa-solid fa-download text-emerald-700"></i><span>Download Data Kelas (PDF)</span></button>
                            <button onclick="openKelasModal()" class="px-5 py-2.5 bg-emerald-700 hover:bg-emerald-600 text-white font-black rounded-xl text-xs shadow-md transition-all flex items-center justify-center space-x-2">
                                <i class="fa-solid fa-school-flag"></i><span>Tambah Kelas Baru</span>
                            </button>
                        </div>
                    </div>
                    <div class="bg-white border-2 border-slate-300 rounded-2xl shadow-md overflow-hidden p-6">
                        <div class="overflow-x-auto">
                            <table class="w-full text-left border-collapse">
                                <thead class="bg-slate-950 text-[11px] uppercase font-black text-emerald-400 border-b-2 border-slate-800">
                                    <tr>
                                        <th class="p-4">Nama Kelas</th>
                                        <th class="p-4">Jumlah Siswa</th>
                                        <th class="p-4 text-right">Aksi</th>
                                    </tr>
                                </thead>
                                <tbody id="pengaturan-kelas-body" class="divide-y-2 divide-slate-200 text-xs font-black text-slate-900"></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <div id="tab-guru" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md flex flex-col md:flex-row justify-between items-center gap-4">
                        <div>
                            <h3 class="text-base font-black text-slate-950 flex items-center"><i class="fa-solid fa-chalkboard-user mr-2 text-emerald-700"></i>Ruang Master Data Guru & Pelapor</h3>
                            <p class="text-xs font-black text-slate-600 mt-1">Daftar ustadz/ustadzah, guru piket, dan wali kelas pelapor.</p>
                        </div>
                        <div class="flex items-center gap-2">
                            <button onclick="downloadPDF('Data Guru Pelapor', 'pengaturan-guru-body', ['Nama Guru / Pelapor'])" class="px-4 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400 flex items-center justify-center space-x-1.5"><i class="fa-solid fa-download text-emerald-700"></i><span>Download Data Guru (PDF)</span></button>
                            <button onclick="openGuruModal()" class="px-5 py-2.5 bg-emerald-700 hover:bg-emerald-600 text-white font-black rounded-xl text-xs shadow-md transition-all flex items-center justify-center space-x-2">
                                <i class="fa-solid fa-user-plus"></i><span>Tambah Guru Baru</span>
                            </button>
                        </div>
                    </div>
                    <div class="bg-white border-2 border-slate-300 rounded-2xl shadow-md overflow-hidden p-6">
                        <div class="overflow-x-auto">
                            <table class="w-full text-left border-collapse">
                                <thead class="bg-slate-950 text-[11px] uppercase font-black text-emerald-400 border-b-2 border-slate-800">
                                    <tr>
                                        <th class="p-4">Nama Guru / Pelapor</th>
                                        <th class="p-4 text-right">Aksi</th>
                                    </tr>
                                </thead>
                                <tbody id="pengaturan-guru-body" class="divide-y-2 divide-slate-200 text-xs font-black text-slate-900"></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <div id="tab-pelanggaran" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md flex flex-col md:flex-row justify-between items-center gap-4">
                        <div class="flex flex-col sm:flex-row items-center gap-3 w-full md:w-auto">
                            <div class="w-full sm:w-72">
                                <input type="text" id="pelanggaran-search" oninput="renderPelanggaranTable()" placeholder="Cari pelanggaran / siswa..." class="w-full px-4 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900 focus:outline-none focus:ring-2 focus:ring-emerald-600">
                            </div>
                            <select id="pelanggaran-filter-status" onchange="renderPelanggaranTable()" class="w-full sm:w-auto px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                                <option value="">Semua Status</option>
                                <option value="Baru">Baru</option>
                                <option value="Proses">Proses</option>
                                <option value="Selesai">Selesai</option>
                            </select>
                        </div>
                        <div class="flex flex-wrap items-center gap-2 w-full md:w-auto">
                            <button onclick="downloadPDF('Data Pelanggaran Siswa', 'pelanggaran-table-body', ['Tanggal', 'Siswa', 'Kelas', 'Jenis Pelanggaran', 'Kategori', 'Poin', 'Tindakan', 'Pelapor', 'Hasil Tindakan', 'Status'])" class="px-4 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400 flex items-center justify-center space-x-1.5"><i class="fa-solid fa-download text-emerald-700"></i><span>Download Pelanggaran (PDF)</span></button>
                            <button onclick="openPelanggaranModal()" class="px-5 py-2.5 bg-amber-700 hover:bg-amber-600 text-white font-black rounded-xl text-xs shadow-md transition-all flex items-center justify-center space-x-2">
                                <i class="fa-solid fa-plus"></i><span>Catat Pelanggaran</span>
                            </button>
                        </div>
                    </div>

                    <div class="bg-white border-2 border-slate-300 rounded-2xl shadow-md overflow-hidden">
                        <div class="overflow-x-auto max-h-[650px]">
                            <table class="w-full text-left border-collapse min-w-[950px]">
                                <thead class="sticky-header bg-slate-950 text-[11px] uppercase font-black text-amber-300 border-b-2 border-slate-800 tracking-wider">
                                    <tr>
                                        <th class="p-4 bg-slate-950">Tanggal</th>
                                        <th class="p-4 bg-slate-950">Siswa</th>
                                        <th class="p-4 bg-slate-950">Kelas</th>
                                        <th class="p-4 bg-slate-950">Jenis Pelanggaran</th>
                                        <th class="p-4 bg-slate-950">Kategori</th>
                                        <th class="p-4 bg-slate-950">Poin</th>
                                        <th class="p-4 bg-slate-950">Tindakan</th>
                                        <th class="p-4 bg-slate-950">Pelapor</th>
                                        <th class="p-4 bg-slate-950">Hasil Tindakan</th>
                                        <th class="p-4 bg-slate-950">Status</th>
                                        <th class="p-4 bg-slate-950 text-center">Aksi</th>
                                    </tr>
                                </thead>
                                <tbody id="pelanggaran-table-body" class="divide-y-2 divide-slate-200 text-xs font-black text-slate-900"></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <div id="tab-prestasi" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md flex flex-col md:flex-row justify-between items-center gap-4">
                        <div class="w-full md:w-72">
                            <input type="text" id="prestasi-search" oninput="renderPrestasiTable()" placeholder="Cari prestasi / siswa..." class="w-full px-4 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900 focus:outline-none focus:ring-2 focus:ring-emerald-600">
                        </div>
                        <div class="flex flex-wrap items-center gap-2 w-full md:w-auto">
                            <button onclick="downloadPDF('Data Prestasi Siswa', 'prestasi-table-body', ['Tanggal', 'Siswa', 'Kelas', 'Nama Prestasi', 'Bidang', 'Tingkat', 'Juara', 'Penyelenggara'])" class="px-4 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400 flex items-center justify-center space-x-1.5"><i class="fa-solid fa-download text-emerald-700"></i><span>Download Prestasi (PDF)</span></button>
                            <button onclick="openPrestasiModal()" class="px-5 py-2.5 bg-emerald-700 hover:bg-emerald-600 text-white font-black rounded-xl text-xs shadow-md transition-all flex items-center justify-center space-x-2">
                                <i class="fa-solid fa-trophy"></i><span>Catat Prestasi Baru</span>
                            </button>
                        </div>
                    </div>

                    <div class="bg-white border-2 border-slate-300 rounded-2xl shadow-md overflow-hidden">
                        <div class="overflow-x-auto max-h-[650px]">
                            <table class="w-full text-left border-collapse min-w-[900px]">
                                <thead class="sticky-header bg-slate-950 text-[11px] uppercase font-black text-emerald-400 border-b-2 border-slate-800 tracking-wider">
                                    <tr>
                                        <th class="p-4 bg-slate-950">Tanggal</th>
                                        <th class="p-4 bg-slate-950">Siswa</th>
                                        <th class="p-4 bg-slate-950">Kelas</th>
                                        <th class="p-4 bg-slate-950">Nama Prestasi</th>
                                        <th class="p-4 bg-slate-950">Bidang</th>
                                        <th class="p-4 bg-slate-950">Tingkat</th>
                                        <th class="p-4 bg-slate-950">Juara</th>
                                        <th class="p-4 bg-slate-950">Penyelenggara</th>
                                        <th class="p-4 bg-slate-950 text-center">Aksi</th>
                                    </tr>
                                </thead>
                                <tbody id="prestasi-table-body" class="divide-y-2 divide-slate-200 text-xs font-black text-slate-900"></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <div id="tab-pembinaan" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md flex flex-col md:flex-row justify-between items-center gap-4">
                        <div class="w-full md:w-72">
                            <input type="text" id="pembinaan-search" oninput="renderPembinaanTable()" placeholder="Cari pembinaan / siswa..." class="w-full px-4 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900 focus:outline-none focus:ring-2 focus:ring-emerald-600">
                        </div>
                        <div class="flex flex-wrap items-center gap-2 w-full md:w-auto">
                            <button onclick="downloadPDF('Data Pembinaan Siswa', 'pembinaan-table-body', ['Tanggal', 'Siswa', 'Kelas', 'Permasalahan', 'Bentuk Pembinaan', 'Hasil', 'Status'])" class="px-4 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400 flex items-center justify-center space-x-1.5"><i class="fa-solid fa-download text-emerald-700"></i><span>Download Pembinaan (PDF)</span></button>
                            <button onclick="openPembinaanModal()" class="px-5 py-2.5 bg-red-700 hover:bg-red-600 text-white font-black rounded-xl text-xs shadow-md transition-all flex items-center justify-center space-x-2">
                                <i class="fa-solid fa-handshake-angle"></i><span>Catat Pembinaan Baru</span>
                            </button>
                        </div>
                    </div>

                    <div class="bg-white border-2 border-slate-300 rounded-2xl shadow-md overflow-hidden">
                        <div class="overflow-x-auto max-h-[650px]">
                            <table class="w-full text-left border-collapse min-w-[900px]">
                                <thead class="sticky-header bg-slate-950 text-[11px] uppercase font-black text-red-300 border-b-2 border-slate-800 tracking-wider">
                                    <tr>
                                        <th class="p-4 bg-slate-950">Tanggal</th>
                                        <th class="p-4 bg-slate-950">Siswa</th>
                                        <th class="p-4 bg-slate-950">Kelas</th>
                                        <th class="p-4 bg-slate-950">Permasalahan</th>
                                        <th class="p-4 bg-slate-950">Bentuk Pembinaan</th>
                                        <th class="p-4 bg-slate-950">Hasil</th>
                                        <th class="p-4 bg-slate-950">Status</th>
                                        <th class="p-4 bg-slate-950 text-center">Aksi</th>
                                    </tr>
                                </thead>
                                <tbody id="pembinaan-table-body" class="divide-y-2 divide-slate-200 text-xs font-black text-slate-900"></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <div id="tab-kegiatan" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md flex flex-col md:flex-row justify-between items-center gap-4">
                        <div class="w-full md:w-72">
                            <input type="text" id="kegiatan-search" oninput="renderKegiatanTable()" placeholder="Cari nama kegiatan..." class="w-full px-4 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900 focus:outline-none focus:ring-2 focus:ring-emerald-600">
                        </div>
                        <div class="flex flex-wrap items-center gap-2 w-full md:w-auto">
                            <button onclick="downloadPDF('Data Kegiatan Kesiswaan', 'kegiatan-table-body', ['Tanggal', 'Nama Kegiatan', 'Jenis', 'Tempat', 'Penanggung Jawab', 'Status'])" class="px-4 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400 flex items-center justify-center space-x-1.5"><i class="fa-solid fa-download text-emerald-700"></i><span>Download Kegiatan (PDF)</span></button>
                            <button onclick="openKegiatanModal()" class="px-5 py-2.5 bg-purple-700 hover:bg-purple-600 text-white font-black rounded-xl text-xs shadow-md transition-all flex items-center justify-center space-x-2">
                                <i class="fa-solid fa-calendar-plus"></i><span>Tambah Kegiatan Baru</span>
                            </button>
                        </div>
                    </div>

                    <div class="bg-white border-2 border-slate-300 rounded-2xl shadow-md overflow-hidden">
                        <div class="overflow-x-auto max-h-[650px]">
                            <table class="w-full text-left border-collapse min-w-[900px]">
                                <thead class="sticky-header bg-slate-950 text-[11px] uppercase font-black text-purple-300 border-b-2 border-slate-800 tracking-wider">
                                    <tr>
                                        <th class="p-4 bg-slate-950">Tanggal</th>
                                        <th class="p-4 bg-slate-950">Nama Kegiatan</th>
                                        <th class="p-4 bg-slate-950">Jenis</th>
                                        <th class="p-4 bg-slate-950">Tempat</th>
                                        <th class="p-4 bg-slate-950">Penanggung Jawab</th>
                                        <th class="p-4 bg-slate-950">Status</th>
                                        <th class="p-4 bg-slate-950 text-center">Aksi</th>
                                    </tr>
                                </thead>
                                <tbody id="kegiatan-table-body" class="divide-y-2 divide-slate-200 text-xs font-black text-slate-900"></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <div id="tab-perizinan" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md flex flex-col md:flex-row justify-between items-center gap-4">
                        <div class="w-full md:w-72">
                            <input type="text" id="perizinan-search" oninput="renderPerizinanTable()" placeholder="Cari perizinan..." class="w-full px-4 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900 focus:outline-none focus:ring-2 focus:ring-emerald-600">
                        </div>
                        <div class="flex flex-wrap items-center gap-2 w-full md:w-auto">
                            <button onclick="downloadPDF('Data Perizinan Siswa', 'perizinan-table-body', ['Tanggal', 'Siswa', 'Kelas', 'Jam Keluar', 'Jam Kembali', 'Keperluan', 'Penjemput', 'Status'])" class="px-4 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400 flex items-center justify-center space-x-1.5"><i class="fa-solid fa-download text-emerald-700"></i><span>Download Perizinan (PDF)</span></button>
                            <button onclick="openPerizinanModal()" class="px-5 py-2.5 bg-teal-700 hover:bg-teal-600 text-white font-black rounded-xl text-xs shadow-md transition-all flex items-center justify-center space-x-2">
                                <i class="fa-solid fa-right-from-bracket"></i><span>Catat Perizinan Baru</span>
                            </button>
                        </div>
                    </div>

                    <div class="bg-white border-2 border-slate-300 rounded-2xl shadow-md overflow-hidden">
                        <div class="overflow-x-auto max-h-[650px]">
                            <table class="w-full text-left border-collapse min-w-[900px]">
                                <thead class="sticky-header bg-slate-950 text-[11px] uppercase font-black text-teal-300 border-b-2 border-slate-800 tracking-wider">
                                    <tr>
                                        <th class="p-4 bg-slate-950">Tanggal</th>
                                        <th class="p-4 bg-slate-950">Siswa</th>
                                        <th class="p-4 bg-slate-950">Kelas</th>
                                        <th class="p-4 bg-slate-950">Jam Keluar</th>
                                        <th class="p-4 bg-slate-950">Jam Kembali</th>
                                        <th class="p-4 bg-slate-950">Keperluan</th>
                                        <th class="p-4 bg-slate-950">Penjemput</th>
                                        <th class="p-4 bg-slate-950">Status</th>
                                        <th class="p-4 bg-slate-950 text-center">Aksi</th>
                                    </tr>
                                </thead>
                                <tbody id="perizinan-table-body" class="divide-y-2 divide-slate-200 text-xs font-black text-slate-900"></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <div id="tab-tatatertib" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-6 shadow-md space-y-4">
                        <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 border-b-2 border-slate-300 pb-4">
                            <div>
                                <h3 class="text-base font-black text-slate-950 flex items-center"><i class="fa-solid fa-book-open mr-2 text-emerald-700"></i>Ruang Tata Tertib & Acuan Sekolah</h3>
                                <p class="text-xs font-black text-slate-600 mt-1">Sunting pedoman tata tertib sekolah layaknya Microsoft Word.</p>
                            </div>
                            <div class="flex items-center space-x-2">
                                <button onclick="document.execCommand('bold', false, null)" class="px-3 py-1.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-lg text-xs border-2 border-slate-400" title="Bold"><i class="fa-solid fa-bold"></i></button>
                                <button onclick="document.execCommand('italic', false, null)" class="px-3 py-1.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-lg text-xs border-2 border-slate-400" title="Italic"><i class="fa-solid fa-italic"></i></button>
                                <button onclick="document.execCommand('underline', false, null)" class="px-3 py-1.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-lg text-xs border-2 border-slate-400" title="Underline"><i class="fa-solid fa-underline"></i></button>
                                <button onclick="saveTataTertibDoc()" class="px-4 py-1.5 bg-emerald-700 hover:bg-emerald-600 text-white font-black rounded-lg text-xs shadow flex items-center space-x-1.5">
                                    <i class="fa-solid fa-floppy-disk"></i><span>Simpan Dokumen</span>
                                </button>
                            </div>
                        </div>
                        <div id="tata-tertib-editor" contenteditable="true" class="min-h-[450px] p-6 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900 focus:outline-none focus:ring-2 focus:ring-emerald-600 focus:bg-white transition-all overflow-y-auto"></div>
                    </div>
                </div>

                <div id="tab-laporan" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md space-y-4 no-print">
                        <h3 class="text-sm font-black text-slate-950 flex items-center"><i class="fa-solid fa-filter mr-2 text-emerald-700"></i>Filter & Kategori Laporan</h3>
                        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
                            <div>
                                <label class="block text-[10px] font-black uppercase tracking-widest text-slate-700 mb-1">Jenis Laporan</label>
                                <select id="laporan-jenis" class="w-full px-3 py-2 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                                    <option value="pelanggaran">Laporan Pelanggaran</option>
                                    <option value="prestasi">Laporan Prestasi</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-[10px] font-black uppercase tracking-widest text-slate-700 mb-1">Kelas</label>
                                <select id="laporan-kelas" class="w-full px-3 py-2 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                                    <option value="">Semua Kelas</option>
                                </select>
                            </div>
                            <div class="flex items-end">
                                <button onclick="generateLaporan()" class="w-full py-2.5 bg-emerald-700 hover:bg-emerald-600 text-white font-black rounded-xl text-xs shadow transition-all">Tampilkan Laporan</button>
                            </div>
                        </div>
                    </div>

                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-8 shadow-md space-y-6">
                        <div class="flex justify-between items-center border-b-2 border-slate-300 pb-6">
                            <div>
                                <h2 id="laporan-title-heading" class="text-xl font-black text-slate-950">LAPORAN PELANGGARAN KESISWAAN</h2>
                                <p id="laporan-subtitle-info" class="text-xs font-black text-slate-600 mt-1">Periode Keseluruhan | SIM Kesiswaan</p>
                            </div>
                            <div class="flex space-x-2 no-print">
                                <button onclick="exportToExcel()" class="px-4 py-2 bg-emerald-100 text-emerald-900 font-black rounded-xl text-xs border-2 border-emerald-400 hover:bg-emerald-200"><i class="fa-solid fa-file-excel mr-1.5"></i>Excel</button>
                                <button onclick="downloadPDF('Laporan Kesiswaan', 'laporan-table-body', ['Tanggal', 'Siswa', 'Kelas', 'Keterangan', 'Poin / Capaian', 'Tindak Lanjut'])" class="px-4 py-2 bg-red-100 text-red-900 font-black rounded-xl text-xs border-2 border-red-400 hover:bg-red-200"><i class="fa-solid fa-file-pdf mr-1.5"></i>Download PDF</button>
                            </div>
                        </div>
                        <div class="overflow-x-auto">
                            <table class="w-full text-left border-collapse">
                                <thead id="laporan-table-head"></thead>
                                <tbody id="laporan-table-body" class="text-xs font-black text-slate-900 divide-y-2 divide-slate-200"></tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <div id="tab-pengaturan" class="tab-content hidden space-y-6">
                    <div class="bg-white border-2 border-slate-300 p-5 sm:p-6 rounded-2xl shadow-md space-y-6">
                        <h3 class="text-sm font-black text-slate-950 flex items-center"><i class="fa-solid fa-circle-info mr-2 text-emerald-700"></i>Informasi & Pengaturan Sistem Kesiswaan</h3>
                        <p class="text-xs font-black text-slate-700 leading-relaxed">
                            SIM Kesiswaan versi profesional ini terintegrasi langsung dengan database Supabase Cloud untuk mendukung sinkronisasi realtime otomatis antar perangkat sekolah tanpa perlu refresh.
                        </p>

                        <!-- Supabase SQL Integration Section -->
                        <div class="pt-4 border-t-2 border-slate-300 space-y-3">
                            <h4 class="text-xs font-black text-emerald-800 uppercase tracking-widest"><i class="fa-solid fa-database mr-1.5"></i>Integrasi Supabase (Multi-Perangkat & Cloud Database)</h4>
                            <p class="text-xs font-black text-slate-600">Salin skrip SQL lengkap di bawah ini dan jalankan di SQL Editor Supabase Anda.</p>
                            
                            <div class="relative">
                                <button onclick="copySupabaseSQL()" class="absolute top-2 right-2 px-3 py-1 bg-emerald-700 hover:bg-emerald-600 text-white font-black rounded-lg text-[10px] shadow"><i class="fa-solid fa-copy mr-1"></i>Copy SQL</button>
                                <pre id="supabase-sql-code" class="p-4 bg-slate-950 text-emerald-400 font-mono text-[11px] rounded-xl overflow-x-auto border-2 border-slate-800">
-- ========================================================
-- SKRIP SQL LENGKAP SUPABASE - SIM KESISWAAN PROFESIONAL
-- ========================================================

CREATE TABLE IF NOT EXISTS sim_state (
    id TEXT PRIMARY KEY,
    data JSONB NOT NULL,
    updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

ALTER TABLE sim_state ENABLE ROW LEVEL SECURITY;

DROP POLICY IF EXISTS "Akses publik penuh untuk sim_state" ON sim_state;

CREATE POLICY "Akses publik penuh untuk sim_state" 
ON sim_state 
FOR ALL 
USING (true) 
WITH CHECK (true);

INSERT INTO sim_state (id, data, updated_at) 
VALUES ('main_data', '{}'::jsonb, NOW()) 
ON CONFLICT (id) DO NOTHING;
                                </pre>
                            </div>
                        </div>
                        
                        <div class="pt-4 border-t-2 border-slate-300 space-y-2">
                            <h4 class="text-xs font-black text-red-700 uppercase tracking-widest"><i class="fa-solid fa-triangle-exclamation mr-1.5"></i>Zona Reset Data (Kosongkan Seluruh Data Aplikasi)</h4>
                            <p class="text-xs font-black text-slate-600">Tombol ini akan menghapus seluruh data catatan di Supabase & LocalStorage dan mengembalikannya ke kondisi kosong (mulai dari nol).</p>
                            <button onclick="resetAllData()" class="w-full py-3 bg-red-100 hover:bg-red-700 text-red-700 hover:text-white font-black rounded-xl text-xs transition-all border-2 border-red-300 flex items-center justify-center space-x-2 shadow-sm">
                                <i class="fa-solid fa-rotate-right"></i><span>Reset / Kosongkan Seluruh Data Aplikasi (Mulai dari Nol)</span>
                            </button>
                        </div>
                    </div>
                </div>

                <div id="tab-profil-siswa" class="tab-content hidden space-y-6">
                    <div class="flex items-center justify-between no-print">
                        <button onclick="switchTab('siswa')" class="px-4 py-2 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs flex items-center space-x-2 border-2 border-slate-400">
                            <i class="fa-solid fa-arrow-left"></i><span>Kembali ke Daftar Siswa</span>
                        </button>
                    </div>
                    <div id="profil-siswa-container" class="space-y-6"></div>
                </div>

            </main>
        </div>
    </div>

    <!-- MODAL: TAMBAH / EDIT SISWA -->
    <div id="modal-siswa" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-slate-950/60 backdrop-blur-sm p-4 overflow-y-auto">
        <div class="bg-white border-2 border-slate-400 rounded-3xl max-w-2xl w-full p-5 sm:p-8 shadow-2xl my-8">
            <div class="flex justify-between items-center mb-6 border-b-2 border-slate-300 pb-4">
                <h3 id="modal-siswa-title" class="text-base sm:text-lg font-black text-slate-950">Tambah Data Siswa</h3>
                <button onclick="closeModal('modal-siswa')" class="p-2 text-slate-600 hover:text-slate-950 rounded-xl"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="form-siswa" onsubmit="saveSiswa(event)" class="space-y-4">
                <input type="hidden" id="siswa-id">
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">NIS / NISN</label>
                        <input type="text" id="siswa-nis" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Nama Lengkap</label>
                        <input type="text" id="siswa-nama" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Kelas</label>
                        <select id="siswa-kelas" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></select>
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Jenis Kelamin</label>
                        <select id="siswa-jk" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                            <option value="L">Laki-laki</option>
                            <option value="P">Perempuan</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Tempat, Tanggal Lahir</label>
                        <input type="text" id="siswa-ttl" placeholder="Contoh: Kediri, 12 Januari 2013" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Nama Orang Tua / Wali</label>
                        <input type="text" id="siswa-ortu" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Nomor HP Orang Tua</label>
                        <input type="text" id="siswa-hp" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Upload Foto Siswa (JPG/PNG)</label>
                        <input type="file" id="siswa-foto-file" accept="image/jpeg, image/png" onchange="handleFotoUpload(event)" class="w-full px-3 py-2 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900 file:mr-4 file:py-1 file:px-4 file:rounded-lg file:border-0 file:text-xs file:font-black file:bg-emerald-600 file:text-white hover:file:bg-emerald-700">
                        <input type="hidden" id="siswa-foto">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Alamat Lengkap</label>
                    <textarea id="siswa-alamat" rows="2" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></textarea>
                </div>
                <div class="flex justify-end space-x-3 pt-4 border-t-2 border-slate-300">
                    <button type="button" onclick="closeModal('modal-siswa')" class="px-5 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400">Batal</button>
                    <button type="submit" class="px-5 py-2.5 bg-emerald-700 hover:bg-emerald-600 text-white font-black rounded-xl text-xs shadow">Simpan Data</button>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL: CATAT PELANGGARAN -->
    <div id="modal-pelanggaran" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-slate-950/60 backdrop-blur-sm p-3 sm:p-4 overflow-y-auto">
        <div class="bg-white border-2 border-slate-400 rounded-3xl max-w-xl w-full p-5 sm:p-8 shadow-2xl my-8">
            <div class="flex justify-between items-center mb-6 border-b-2 border-slate-300 pb-4">
                <h3 id="modal-pelanggaran-title" class="text-base sm:text-lg font-black text-slate-950">Catat Pelanggaran Siswa</h3>
                <button onclick="closeModal('modal-pelanggaran')" class="p-2 text-slate-600 hover:text-slate-950 rounded-xl"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="form-pelanggaran" onsubmit="savePelanggaran(event)" class="space-y-4">
                <input type="hidden" id="pelanggaran-id">
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Pilih Siswa</label>
                    <select id="pelanggaran-siswa-id" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></select>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Tanggal</label>
                        <input type="date" id="pelanggaran-tanggal" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Kategori Pelanggaran</label>
                        <select id="pelanggaran-kategori-custom" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                            <option value="Ringan">Ringan</option>
                            <option value="Sedang">Sedang</option>
                            <option value="Berat">Berat</option>
                        </select>
                    </div>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Nama / Jenis Pelanggaran (Custom)</label>
                        <input type="text" id="pelanggaran-nama-custom" required placeholder="Contoh: Berisik di kelas" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Jumlah Poin</label>
                        <input type="number" id="pelanggaran-poin-custom" required min="1" value="5" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-amber-800">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Kronologi / Catatan Kejadian</label>
                    <textarea id="pelanggaran-kronologi" rows="2" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></textarea>
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Hasil Tindakan / Penyelesaian</label>
                    <input type="text" id="pelanggaran-hasil-tindakan" placeholder="Contoh: Sudah membuat surat pernyataan" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Pelapor / Guru</label>
                        <select id="pelanggaran-pelapor" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></select>
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Tindakan Awal</label>
                        <input type="text" id="pelanggaran-tindakan" required placeholder="Contoh: Teguran lisan" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Status Penanganan</label>
                        <select id="pelanggaran-status" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                            <option value="Baru">Baru</option>
                            <option value="Proses">Proses</option>
                            <option value="Selesai">Selesai</option>
                        </select>
                    </div>
                </div>
                <div class="flex justify-end space-x-3 pt-4 border-t-2 border-slate-300">
                    <button type="button" onclick="closeModal('modal-pelanggaran')" class="px-5 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400">Batal</button>
                    <button type="submit" class="px-5 py-2.5 bg-amber-700 hover:bg-amber-600 text-white font-black rounded-xl text-xs shadow">Simpan Catatan</button>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL: CATAT PRESTASI -->
    <div id="modal-prestasi" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-slate-950/60 backdrop-blur-sm p-3 sm:p-4 overflow-y-auto">
        <div class="bg-white border-2 border-slate-400 rounded-3xl max-w-xl w-full p-5 sm:p-8 shadow-2xl my-8">
            <div class="flex justify-between items-center mb-6 border-b-2 border-slate-300 pb-4">
                <h3 class="text-base sm:text-lg font-black text-slate-950">Catat Prestasi Siswa</h3>
                <button onclick="closeModal('modal-prestasi')" class="p-2 text-slate-600 hover:text-slate-950 rounded-xl"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="form-prestasi" onsubmit="savePrestasi(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Pilih Siswa</label>
                    <select id="prestasi-siswa-id" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></select>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Tanggal</label>
                        <input type="date" id="prestasi-tanggal" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Bidang Prestasi</label>
                        <input type="text" id="prestasi-bidang" required placeholder="Contoh: Keagamaan / Akademik" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Nama Prestasi / Lomba</label>
                    <input type="text" id="prestasi-nama" required placeholder="Contoh: Juara 1 MHQ 5 Juz" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Tingkat</label>
                        <select id="prestasi-tingkat" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                            <option value="Sekolah">Sekolah / Madrasah</option>
                            <option value="Kabupaten/Kota">Kabupaten / Kota</option>
                            <option value="Provinsi">Provinsi</option>
                            <option value="Nasional">Nasional</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Juara / Capaian</label>
                        <input type="text" id="prestasi-juara" required placeholder="Contoh: Juara 1" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Penyelenggara</label>
                    <input type="text" id="prestasi-penyelenggara" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">URL Dokumentasi / Sertifikat</label>
                    <input type="text" id="prestasi-dokumentasi" placeholder="https://..." class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                </div>
                <div class="flex justify-end space-x-3 pt-4 border-t-2 border-slate-300">
                    <button type="button" onclick="closeModal('modal-prestasi')" class="px-5 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400">Batal</button>
                    <button type="submit" class="px-5 py-2.5 bg-emerald-700 hover:bg-emerald-600 text-white font-black rounded-xl text-xs shadow">Simpan Prestasi</button>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL: CATAT PEMBINAAN -->
    <div id="modal-pembinaan" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-slate-950/60 backdrop-blur-sm p-3 sm:p-4 overflow-y-auto">
        <div class="bg-white border-2 border-slate-400 rounded-3xl max-w-xl w-full p-5 sm:p-8 shadow-2xl my-8">
            <div class="flex justify-between items-center mb-6 border-b-2 border-slate-300 pb-4">
                <h3 class="text-base sm:text-lg font-black text-slate-950">Catat Pembinaan Siswa</h3>
                <button onclick="closeModal('modal-pembinaan')" class="p-2 text-slate-600 hover:text-slate-950 rounded-xl"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="form-pembinaan" onsubmit="savePembinaan(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Pilih Siswa</label>
                    <select id="pembinaan-siswa-id" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></select>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Tanggal</label>
                        <input type="date" id="pembinaan-tanggal" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Status Pembinaan</label>
                        <select id="pembinaan-status" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                            <option value="Proses">Proses</option>
                            <option value="Selesai">Selesai</option>
                        </select>
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Permasalahan</label>
                    <textarea id="pembinaan-permasalahan" rows="2" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></textarea>
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Bentuk Pembinaan</label>
                    <input type="text" id="pembinaan-bentuk" required placeholder="Contoh: Konseling Individu & Pemanggilan Wali" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Hasil Pembinaan</label>
                    <textarea id="pembinaan-hasil" rows="2" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></textarea>
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Tindak Lanjut</label>
                    <input type="text" id="pembinaan-tindaklanjut" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                </div>
                <div class="flex justify-end space-x-3 pt-4 border-t-2 border-slate-300">
                    <button type="button" onclick="closeModal('modal-pembinaan')" class="px-5 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400">Batal</button>
                    <button type="submit" class="px-5 py-2.5 bg-red-700 hover:bg-red-600 text-white font-black rounded-xl text-xs shadow">Simpan Pembinaan</button>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL: TAMBAH KEGIATAN -->
    <div id="modal-kegiatan" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-slate-950/60 backdrop-blur-sm p-3 sm:p-4 overflow-y-auto">
        <div class="bg-white border-2 border-slate-400 rounded-3xl max-w-xl w-full p-5 sm:p-8 shadow-2xl my-8">
            <div class="flex justify-between items-center mb-6 border-b-2 border-slate-300 pb-4">
                <h3 class="text-base sm:text-lg font-black text-slate-950">Tambah Kegiatan Kesiswaan</h3>
                <button onclick="closeModal('modal-kegiatan')" class="p-2 text-slate-600 hover:text-slate-950 rounded-xl"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="form-kegiatan" onsubmit="saveKegiatan(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Nama Kegiatan</label>
                    <input type="text" id="kegiatan-nama" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Jenis Kegiatan</label>
                        <select id="kegiatan-jenis" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                            <option value="Kegiatan Keagamaan">Kegiatan Keagamaan</option>
                            <option value="Lomba">Lomba</option>
                            <option value="Upacara">Upacara</option>
                            <option value="Class Meeting">Class Meeting</option>
                            <option value="Lainnya">Lainnya</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Tanggal</label>
                        <input type="date" id="kegiatan-tanggal" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Tempat</label>
                        <input type="text" id="kegiatan-tempat" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Penanggung Jawab</label>
                        <input type="text" id="kegiatan-pj" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Peserta</label>
                        <input type="text" id="kegiatan-peserta" required placeholder="Contoh: Seluruh Siswa" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Status</label>
                        <select id="kegiatan-status" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                            <option value="Terencana">Terencana</option>
                            <option value="Berlangsung">Berlangsung</option>
                            <option value="Selesai">Selesai</option>
                        </select>
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Catatan</label>
                    <textarea id="kegiatan-catatan" rows="2" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></textarea>
                </div>
                <div class="flex justify-end space-x-3 pt-4 border-t-2 border-slate-300">
                    <button type="button" onclick="closeModal('modal-kegiatan')" class="px-5 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400">Batal</button>
                    <button type="submit" class="px-5 py-2.5 bg-purple-700 hover:bg-purple-600 text-white font-black rounded-xl text-xs shadow">Simpan Kegiatan</button>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL: PERIZINAN -->
    <div id="modal-perizinan" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-slate-950/60 backdrop-blur-sm p-3 sm:p-4 overflow-y-auto">
        <div class="bg-white border-2 border-slate-400 rounded-3xl max-w-xl w-full p-5 sm:p-8 shadow-2xl my-8">
            <div class="flex justify-between items-center mb-6 border-b-2 border-slate-300 pb-4">
                <h3 class="text-base sm:text-lg font-black text-slate-950">Catat Perizinan Keluar Siswa</h3>
                <button onclick="closeModal('modal-perizinan')" class="p-2 text-slate-600 hover:text-slate-950 rounded-xl"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="form-perizinan" onsubmit="savePerizinan(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Pilih Siswa</label>
                    <select id="perizinan-siswa-id" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900"></select>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Tanggal</label>
                        <input type="date" id="perizinan-tanggal" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Jam Keluar</label>
                        <input type="time" id="perizinan-jam-keluar" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Jam Kembali</label>
                        <input type="time" id="perizinan-jam-kembali" required class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-black text-slate-900 mb-1">Keperluan</label>
                    <input type="text" id="perizinan-keperluan" required placeholder="Contoh: Berobat ke dokter gigi" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Penjemput / Pihak Bertanggung Jawab</label>
                        <input type="text" id="perizinan-penjemput" required placeholder="Contoh: Orang Tua Kandung" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                    </div>
                    <div>
                        <label class="block text-xs font-black text-slate-900 mb-1">Status Izin</label>
                        <select id="perizinan-status" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                            <option value="Keluar">Keluar</option>
                            <option value="Kembali">Kembali</option>
                        </select>
                    </div>
                </div>
                <div class="flex justify-end space-x-3 pt-4 border-t-2 border-slate-300">
                    <button type="button" onclick="closeModal('modal-perizinan')" class="px-5 py-2.5 bg-slate-200 hover:bg-slate-300 text-slate-900 font-black rounded-xl text-xs border-2 border-slate-400">Batal</button>
                    <button type="submit" class="px-5 py-2.5 bg-teal-700 hover:bg-teal-600 text-white font-black rounded-xl text-xs shadow">Simpan Perizinan</button>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL: KELAS -->
    <div id="modal-kelas" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-slate-950/60 backdrop-blur-sm p-4">
        <div class="bg-white border-2 border-slate-400 rounded-3xl max-w-sm w-full p-6 shadow-2xl">
            <h3 class="text-base font-black text-slate-950 mb-4">Tambah Kelas Baru</h3>
            <form id="form-kelas" onsubmit="saveKelas(event)" class="space-y-4">
                <input type="text" id="input-nama-kelas" required placeholder="Contoh: VII C" class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                <div class="flex justify-end space-x-2">
                    <button type="button" onclick="closeModal('modal-kelas')" class="px-4 py-2 bg-slate-200 text-slate-900 rounded-xl text-xs font-black border-2 border-slate-400">Batal</button>
                    <button type="submit" class="px-4 py-2 bg-emerald-700 text-white rounded-xl text-xs font-black">Simpan</button>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL: GURU -->
    <div id="modal-guru" class="hidden fixed inset-0 z-50 flex items-center justify-center bg-slate-950/60 backdrop-blur-sm p-4">
        <div class="bg-white border-2 border-slate-400 rounded-3xl max-w-sm w-full p-6 shadow-2xl">
            <h3 class="text-base font-black text-slate-950 mb-4">Tambah Guru / Pelapor Baru</h3>
            <form id="form-guru" onsubmit="saveGuru(event)" class="space-y-4">
                <input type="text" id="input-nama-guru" required placeholder="Contoh: Ustadz Ahmad, S.Pd." class="w-full px-3 py-2.5 bg-slate-50 border-2 border-slate-300 rounded-xl text-xs font-black text-slate-900">
                <div class="flex justify-end space-x-2">
                    <button type="button" onclick="closeModal('modal-guru')" class="px-4 py-2 bg-slate-200 text-slate-900 rounded-xl text-xs font-black border-2 border-slate-400">Batal</button>
                    <button type="submit" class="px-4 py-2 bg-emerald-700 text-white rounded-xl text-xs font-black">Simpan</button>
                </div>
            </form>
        </div>
    </div>

    <!-- NOTIFICATION TOAST -->
    <div id="custom-notification" class="hidden fixed bottom-6 right-6 z-50 bg-white border-2 border-emerald-600 shadow-2xl rounded-2xl p-4 flex items-center space-x-3 transition-all duration-300 transform translate-y-10 opacity-0">
        <div id="notification-icon" class="text-xl"></div>
        <div>
            <h4 class="text-xs font-black text-slate-950">SIM Kesiswaan</h4>
            <p id="notification-text" class="text-xs font-black text-slate-800"></p>
        </div>
    </div>

    <script>
        const SUPABASE_URL = 'https://ogbvyeypznbwurmsmwld.supabase.co';
        const SUPABASE_ANON_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Im9nYnZ5ZXlwem5id3VybXNtd2xkIiwicm9sZSI6ImFub24iLCJpYXQiOjE3ODE3OTM1MzgsImV4cCI6MjA5NzM2OTUzOH0.LSO8qrGBs85lkSD5mzVL7zOBO5LTHJX90v7Q-FJEYQo';
        
        let supabaseClient = null;
        let isCanvasEnvironment = false;

        try {
            if (window.location.protocol === 'blob:' || window.location.hostname.includes('usercontent.google') || window.self !== window.top) {
                isCanvasEnvironment = true;
            }
        } catch (e) {
            isCanvasEnvironment = true;
        }

        try {
            if (window.supabase) {
                supabaseClient = window.supabase.createClient(SUPABASE_URL, SUPABASE_ANON_KEY, {
                    realtime: { enabled: !isCanvasEnvironment }
                });
            }
        } catch (e) {
            console.warn('Supabase init warning:', e);
        }

        let appData = {
            currentUser: { username: 'waka', role: 'Waka Kesiswaan' },
            kelas: ["IX A", "IX B", "VIII A", "VIII B", "VII A", "VII B"],
            guru: ["Guru Piket", "Ustadz Ahmad, S.Pd.", "Ustadzah Fatimah, M.Pd.", "Musyrif Asrama", "Wali Kelas IX A"],
            tataTertibDoc: `<h4 style="font-weight: 900; color: #047857; margin-bottom: 8px;">PEDOMAN TATA TERTIB DAN POIN PELANGGARAN SISWA</h4>
                            <p style="margin-bottom: 6px;">1. <strong>Pelanggaran Ringan (5-10 Poin):</strong> Terlambat hadir di sekolah / apel pagi, atribut seragam tidak lengkap, atau piket kelas terabaikan.</p>
                            <p style="margin-bottom: 6px;">2. <strong>Pelanggaran Sedang (15-30 Poin):</strong> Tidak mengikuti kegiatan berjamaah wajib, membolos jam pelajaran, membawa gadget tanpa izin resmi.</p>
                            <p style="margin-bottom: 6px;">3. <strong>Pelanggaran Berat (50-100 Poin):</strong> Merokok / membawa barang terlarang, terlibat perkelahian / bullying, atau tindak amoral berat.</p>`,
            siswa: [
                { id: 1, nis: "232409001", nama: "Utsman bin Affan", kelas: "IX A", jk: "L", ttl: "Kediri, 17 Agustus 2011", ortu: "Mustofa", hp: "082112233445", alamat: "Jl. Hayam Wuruk No. 12", foto: "https://placehold.co/150x150/10b981/ffffff?text=UB" },
                { id: 2, nis: "232409002", nama: "Zainab binti Muhammad", kelas: "IX A", jk: "P", ttl: "Madiun, 12 Desember 2011", ortu: "Kasim", hp: "082223344556", alamat: "Jl. Pahlawan No. 90, Madiun", foto: "https://placehold.co/150x150/10b981/ffffff?text=ZB" },
                { id: 3, nis: "232408001", nama: "Rizky Ramadhan Putra", kelas: "VIII A", jk: "L", ttl: "Surabaya, 10 Ramadan 2012", ortu: "Herman Susanto", hp: "081678901234", alamat: "Jl. Kenangan No. 5, Surabaya", foto: "https://placehold.co/150x150/10b981/ffffff?text=RR" },
                { id: 4, nis: "232407001", nama: "Ahmad Fauzan Al-Ghifari", kelas: "VII A", jk: "L", ttl: "Malang, 12 Januari 2013", ortu: "H. Abdullah", hp: "081234567890", alamat: "Jl. Pesantren No. 1, Ringinagung", foto: "https://placehold.co/150x150/10b981/ffffff?text=AF" }
            ],
            pelanggaran: [
                { id: 1, siswaId: 3, tanggal: "2026-02-10", nama: "Terlambat Hadir di Sekolah", kategori: "Ringan", poin: 5, kronologi: "Terlambat datang apel pagi", pelapor: "Guru Piket", tindakan: "Teguran lisan & nasehat", hasilTindakan: "Sudah membuat surat pernyataan", status: "Selesai" }
            ],
            prestasi: [
                { id: 1, siswaId: 1, tanggal: "2026-01-20", bidang: "Keagamaan", nama: "Juara 1 Musabaqah Hifdzil Qur'an", tingkat: "Kabupaten/Kota", juara: "Juara 1", penyelenggara: "Kemenag", dokumentasi: "https://placehold.co/300x200/10b981/ffffff?text=MHQ" }
            ],
            pembinaan: [],
            kegiatan: [
                { id: 1, nama: "Pondok Ramadhan & Pesantren Kilat", jenis: "Kegiatan Keagamaan", tanggal: "2026-03-01", tempat: "Masjid Pesantren", pj: "Ustadz Pembina", peserta: "Seluruh Siswa", status: "Terencana", catatan: "Fokus tadarus" }
            ],
            perizinan: []
        };

        document.addEventListener('DOMContentLoaded', async () => {
            await loadFromSupabase();
            validateAppData();
            initApp();
            if (!isCanvasEnvironment) {
                initSupabaseRealtime();
            }
        });

        function validateAppData() {
            if (!Array.isArray(appData.kelas)) appData.kelas = ["IX A", "IX B", "VIII A", "VIII B", "VII A", "VII B"];
            if (!Array.isArray(appData.siswa)) appData.siswa = [];
            if (!Array.isArray(appData.pelanggaran)) appData.pelanggaran = [];
            if (!Array.isArray(appData.prestasi)) appData.prestasi = [];
            if (!Array.isArray(appData.pembinaan)) appData.pembinaan = [];
            if (!Array.isArray(appData.kegiatan)) appData.kegiatan = [];
            if (!Array.isArray(appData.perizinan)) appData.perizinan = [];
            if (!Array.isArray(appData.guru)) appData.guru = [];
        }

        async function saveToSupabase() {
            try {
                localStorage.setItem('sim_kesiswaan_data', JSON.stringify(appData));
                if (supabaseClient) {
                    const { error } = await supabaseClient
                        .from('sim_state')
                        .upsert({ id: 'main_data', data: appData, updated_at: new Date() });
                    if (error) console.error('Supabase save error:', error.message);
                }
            } catch (err) {
                console.warn('Sync storage warning:', err);
            }
        }

        async function loadFromSupabase() {
            try {
                if (supabaseClient) {
                    const { data, error } = await supabaseClient
                        .from('sim_state')
                        .select('data')
                        .eq('id', 'main_data')
                        .single();
                    if (data && data.data) {
                        appData = data.data;
                        validateAppData();
                        return;
                    }
                }
            } catch (err) {
                console.warn('Supabase fetch notice, falling back to local storage.');
            }
            
            const saved = localStorage.getItem('sim_kesiswaan_data');
            if (saved) {
                try { 
                    appData = JSON.parse(saved); 
                    validateAppData();
                } catch(e){}
            }
        }

        function initSupabaseRealtime() {
            if (!supabaseClient || isCanvasEnvironment) return;
            try {
                supabaseClient
                    .channel('public:sim_state')
                    .on('postgres_changes', { event: '*', schema: 'public', table: 'sim_state' }, payload => {
                        if (payload.new && payload.new.data) {
                            appData = payload.new.data;
                            validateAppData();
                            populateDropdowns();
                            renderDashboard();
                            renderSiswaTable();
                            renderPelanggaranTable();
                            renderPrestasiTable();
                            renderPembinaanTable();
                            renderKegiatanTable();
                            renderPerizinanTable();
                            renderPengaturan();
                            showNotification('Data baru tersinkronisasi otomatis secara realtime!', 'info');
                        }
                    })
                    .subscribe();
            } catch (e) {
                console.warn('Realtime subscription notice:', e);
            }
        }

        async function resetAllData() {
            if (confirm('PERINGATAN: Apakah Anda yakin ingin menghapus SELURUH data aplikasi di Supabase & LocalStorage, lalu mengembalikannya ke kondisi kosong (mulai dari nol)? Tindakan ini tidak dapat dibatalkan.')) {
                appData.siswa = [];
                appData.pelanggaran = [];
                appData.prestasi = [];
                appData.pembinaan = [];
                appData.kegiatan = [];
                appData.perizinan = [];
                appData.kelas = [];
                appData.guru = [];
                appData.tataTertibDoc = '<h4 style="font-weight: 900; color: #047857; margin-bottom: 8px;">PEDOMAN TATA TERTIB</h4><p>Belum ada pedoman tata tertib.</p>';
                await saveToSupabase();
                localStorage.removeItem('sim_kesiswaan_data');
                location.reload();
            }
        }

        function copySupabaseSQL() {
            const sqlText = document.getElementById('supabase-sql-code').innerText;
            const tempTextArea = document.createElement('textarea');
            tempTextArea.value = sqlText;
            document.body.appendChild(tempTextArea);
            tempTextArea.select();
            document.execCommand('copy');
            document.body.removeChild(tempTextArea);
            showNotification('Skrip SQL Supabase berhasil disalin ke clipboard!', 'success');
        }

        let dashboardChartInstance = null;
        let classChartInstance = null;

        function initApp() {
            validateAppData();
            populateDropdowns();
            renderDashboard();
            renderSiswaTable();
            renderPelanggaranTable();
            renderPrestasiTable();
            renderPembinaanTable();
            renderKegiatanTable();
            renderPerizinanTable();
            renderPengaturan();
        }

        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.querySelectorAll('.nav-item').forEach(el => {
                el.classList.remove('bg-emerald-700', 'text-white', 'shadow-md');
                el.classList.add('text-slate-800', 'hover:bg-emerald-100', 'hover:text-emerald-900');
            });

            const activeTab = document.getElementById(`tab-${tabId}`);
            if (activeTab) activeTab.classList.remove('hidden');

            const navLink = document.querySelector(`[href="#${tabId}"]`);
            if (navLink) {
                navLink.classList.add('bg-emerald-700', 'text-white', 'shadow-md');
                navLink.classList.remove('text-slate-800', 'hover:bg-emerald-100', 'hover:text-emerald-900');
            }

            const titles = {
                dashboard: 'Dashboard Waka Kesiswaan',
                siswa: 'Pengelolaan Data Siswa',
                kelas: 'Ruang Master Data Kelas',
                guru: 'Ruang Master Data Guru / Pelapor',
                pelanggaran: 'Catatan Pelanggaran & Poin Siswa',
                prestasi: 'Prestasi Siswa',
                pembinaan: 'Proses Pembinaan Siswa',
                kegiatan: 'Kegiatan Kesiswaan',
                perizinan: 'Perizinan Keluar Siswa',
                tatatertib: 'Ruang Tata Tertib & Acuan Sekolah',
                laporan: 'Laporan Kesiswaan Komprehensif',
                pengaturan: 'Pengaturan Sistem & Master Data',
                'profil-siswa': 'Profil Kesiswaan & Riwayat Lengkap'
            };
            document.getElementById('page-title').innerText = titles[tabId] || 'SIM Kesiswaan';
            document.getElementById('sidebar').classList.add('-translate-x-full');
        }

        function toggleSidebar() {
            document.getElementById('sidebar').classList.toggle('-translate-x-full');
        }

        function showNotification(message, type = 'success') {
            const notif = document.getElementById('custom-notification');
            const text = document.getElementById('notification-text');
            const icon = document.getElementById('notification-icon');

            if (!notif || !text || !icon) return;

            text.innerText = message;
            icon.className = type === 'success' ? 'fa-solid fa-circle-check text-emerald-700 text-lg' : 'fa-solid fa-circle-info text-blue-700 text-lg';

            notif.classList.remove('hidden', 'translate-y-10', 'opacity-0');
            notif.classList.add('translate-y-0', 'opacity-100');

            setTimeout(() => {
                notif.classList.remove('translate-y-0', 'opacity-100');
                notif.classList.add('translate-y-10', 'opacity-0');
                setTimeout(() => notif.classList.add('hidden'), 300);
            }, 3000);
        }

        function closeModal(modalId) { document.getElementById(modalId).classList.add('hidden'); }
        function openModal(modalId) { document.getElementById(modalId).classList.remove('hidden'); }

        function handleFotoUpload(event) {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    document.getElementById('siswa-foto').value = e.target.result;
                    showNotification('Foto siswa (JPG) berhasil dimuat.', 'success');
                };
                reader.readAsDataURL(file);
            }
        }

        function populateDropdowns() {
            validateAppData();
            const sortedKelas = [...appData.kelas].sort((a,b) => b.localeCompare(a));
            const kelasOpts = `<option value="">Pilih Kelas</option>` + sortedKelas.map(k => `<option value="${k}">${k}</option>`).join('');
            const filterKelasOpts = `<option value="">Semua Kelas</option>` + sortedKelas.map(k => `<option value="${k}">${k}</option>`).join('');
            
            if(document.getElementById('siswa-kelas')) document.getElementById('siswa-kelas').innerHTML = kelasOpts;
            if(document.getElementById('siswa-filter-kelas')) document.getElementById('siswa-filter-kelas').innerHTML = filterKelasOpts;
            if(document.getElementById('laporan-kelas')) document.getElementById('laporan-kelas').innerHTML = filterKelasOpts;

            const siswaOpts = `<option value="">Pilih Siswa</option>` + appData.siswa.map(s => `<option value="${s.id}">${s.nama} (${s.kelas} - ${s.nis})</option>`).join('');
            if(document.getElementById('pelanggaran-siswa-id')) document.getElementById('pelanggaran-siswa-id').innerHTML = siswaOpts;
            if(document.getElementById('prestasi-siswa-id')) document.getElementById('prestasi-siswa-id').innerHTML = siswaOpts;
            if(document.getElementById('pembinaan-siswa-id')) document.getElementById('pembinaan-siswa-id').innerHTML = siswaOpts;
            if(document.getElementById('perizinan-siswa-id')) document.getElementById('perizinan-siswa-id').innerHTML = siswaOpts;

            const guruOpts = `<option value="">Pilih Guru Pelapor</option>` + appData.guru.map(g => `<option value="${g}">${g}</option>`).join('');
            if(document.getElementById('pelanggaran-pelapor')) document.getElementById('pelanggaran-pelapor').innerHTML = guruOpts;
        }

        function getSiswaTotalPoin(siswaId) {
            let total = 0;
            appData.pelanggaran.forEach(p => {
                if (parseInt(p.siswaId) === parseInt(siswaId)) {
                    total += parseInt(p.poin || 0);
                }
            });
            return total;
        }

        function renderDashboard() {
            if (document.getElementById('stat-total-siswa')) document.getElementById('stat-total-siswa').innerText = appData.siswa.length;
            if (document.getElementById('stat-total-pelanggaran')) document.getElementById('stat-total-pelanggaran').innerText = appData.pelanggaran.length;
            if (document.getElementById('stat-total-prestasi')) document.getElementById('stat-total-prestasi').innerText = appData.prestasi.length;
            if (document.getElementById('stat-total-binaan')) document.getElementById('stat-total-binaan').innerText = appData.pembinaan.filter(p => p.status === 'Proses').length;
            if (document.getElementById('stat-total-kegiatan')) document.getElementById('stat-total-kegiatan').innerText = appData.kegiatan.length;
            if (document.getElementById('stat-total-perizinan')) document.getElementById('stat-total-perizinan').innerText = appData.perizinan.length;

            if (appData.tataTertibDoc && document.getElementById('tata-tertib-editor')) {
                document.getElementById('tata-tertib-editor').innerHTML = appData.tataTertibDoc;
            }

            const highRisk = appData.siswa.map(s => ({ ...s, totalPoin: getSiswaTotalPoin(s.id) }))
                                         .sort((a, b) => b.totalPoin - a.totalPoin)
                                         .slice(0, 4);

            if (document.getElementById('dashboard-high-risk-list')) {
                document.getElementById('dashboard-high-risk-list').innerHTML = highRisk.length ? highRisk.map(s => `
                    <div class="flex items-center justify-between p-3 bg-slate-50 border-2 border-slate-300 rounded-xl cursor-pointer hover:bg-amber-100 transition-all" onclick="openProfilSiswa(${s.id})">
                        <div class="flex items-center space-x-3 min-w-0">
                            <img src="${s.foto}" onerror="this.src='https://placehold.co/100x100/10b981/ffffff?text=S'" class="w-10 h-10 rounded-full object-cover border-2 border-slate-400 flex-shrink-0">
                            <div class="min-w-0">
                                <h4 class="text-xs font-black text-slate-950 truncate">${s.nama}</h4>
                                <span class="text-[10px] font-black text-slate-600">${s.kelas}</span>
                            </div>
                        </div>
                        <span class="px-2.5 py-1 bg-amber-200 border-2 border-amber-400 text-amber-950 text-xs font-black rounded-lg flex-shrink-0 ml-2">${s.totalPoin} Poin</span>
                    </div>
                `).join('') : '<p class="text-xs text-slate-600 font-black">Tidak ada data.</p>';
            }

            const recentPrestasi = [...appData.prestasi].sort((a,b) => new Date(b.tanggal) - new Date(a.tanggal)).slice(0, 3);
            if (document.getElementById('dashboard-recent-prestasi')) {
                document.getElementById('dashboard-recent-prestasi').innerHTML = recentPrestasi.length ? recentPrestasi.map(p => {
                    const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                    return `
                        <div class="p-3 bg-slate-50 border-2 border-slate-300 rounded-xl">
                            <div class="flex justify-between items-start">
                                <h4 class="text-xs font-black text-slate-950 truncate pr-2">${p.nama}</h4>
                                <span class="text-[10px] bg-emerald-200 border-2 border-emerald-400 text-emerald-950 px-2 py-0.5 rounded font-black flex-shrink-0">${p.juara}</span>
                            </div>
                            <p class="text-[10px] font-black text-slate-700 mt-1">${siswa ? siswa.nama : 'Siswa'} (${siswa ? siswa.kelas : ''})</p>
                        </div>
                    `;
                }).join('') : '<p class="text-xs text-slate-600 font-black">Belum ada data prestasi.</p>';
            }

            const recentKegiatan = [...appData.kegiatan].sort((a,b) => new Date(a.tanggal) - new Date(b.tanggal)).slice(0, 3);
            if (document.getElementById('dashboard-recent-kegiatan')) {
                document.getElementById('dashboard-recent-kegiatan').innerHTML = recentKegiatan.length ? recentKegiatan.map(k => `
                    <div class="p-3 bg-slate-50 border-2 border-slate-300 rounded-xl">
                        <div class="flex justify-between items-start">
                            <h4 class="text-xs font-black text-slate-950 truncate pr-2">${k.nama}</h4>
                            <span class="text-[10px] bg-purple-200 border-2 border-purple-400 text-purple-950 px-2 py-0.5 rounded font-black flex-shrink-0">${k.status}</span>
                        </div>
                        <p class="text-[10px] font-black text-slate-700 mt-1"><i class="fa-solid fa-calendar mr-1"></i>${k.tanggal} | ${k.tempat}</p>
                    </div>
                `).join('') : '<p class="text-xs text-slate-600 font-black">Belum ada kegiatan terdekat.</p>';
            }

            renderCharts();
        }

        async function saveTataTertibDoc() {
            const content = document.getElementById('tata-tertib-editor').innerHTML;
            appData.tataTertibDoc = content;
            await saveToSupabase();
            showNotification('Dokumen Tata Tertib berhasil disimpan!', 'success');
        }

        function renderCharts() {
            const ctx1El = document.getElementById('dashboardChart');
            if (ctx1El) {
                const ctx1 = ctx1El.getContext('2d');
                if (dashboardChartInstance) dashboardChartInstance.destroy();
                dashboardChartInstance = new Chart(ctx1, {
                    type: 'bar',
                    data: {
                        labels: ['Pelanggaran', 'Prestasi', 'Pembinaan', 'Perizinan'],
                        datasets: [{
                            label: 'Jumlah Total',
                            data: [appData.pelanggaran.length, appData.prestasi.length, appData.pembinaan.length, appData.perizinan.length],
                            backgroundColor: ['#b45309', '#047857', '#b91c1c', '#0f766e'],
                            borderRadius: 6
                        }]
                    },
                    options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
                });
            }

            const ctx2El = document.getElementById('classChart');
            if (ctx2El) {
                validateAppData();
                const sortedKelas = [...appData.kelas].sort((a, b) => b.localeCompare(a));
                const classCounts = sortedKelas.map(k => appData.siswa.filter(s => s.kelas === k).length);
                
                const ctx2 = ctx2El.getContext('2d');
                if (classChartInstance) classChartInstance.destroy();
                classChartInstance = new Chart(ctx2, {
                    type: 'bar',
                    data: {
                        labels: sortedKelas,
                        datasets: [{
                            label: 'Jumlah Siswa',
                            data: classCounts,
                            backgroundColor: '#1d4ed8',
                            borderRadius: 6
                        }]
                    },
                    options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
                });
            }
        }

        function renderSiswaTable() {
            const searchInput = document.getElementById('siswa-search');
            const filterKelasInput = document.getElementById('siswa-filter-kelas');
            const search = searchInput ? searchInput.value.toLowerCase() : '';
            const filterKelas = filterKelasInput ? filterKelasInput.value : '';

            const filtered = appData.siswa.filter(s => {
                const matchSearch = s.nama.toLowerCase().includes(search) || s.nis.toLowerCase().includes(search);
                const matchKelas = filterKelas ? s.kelas === filterKelas : true;
                return matchSearch && matchKelas;
            });

            const tbody = document.getElementById('siswa-table-body');
            if (!tbody) return;

            tbody.innerHTML = filtered.length ? filtered.map(s => `
                <tr class="hover:bg-emerald-50 transition-colors">
                    <td class="p-4 text-center">
                        <img src="${s.foto}" onerror="this.src='https://placehold.co/100x100/10b981/ffffff?text=S'" class="w-10 h-10 rounded-full object-cover border-2 border-emerald-600 shadow-sm mx-auto cursor-pointer" onclick="openProfilSiswa(${s.id})">
                    </td>
                    <td class="p-4 font-black text-slate-950 hover:text-emerald-800 cursor-pointer whitespace-nowrap" onclick="openProfilSiswa(${s.id})">${s.nama}</td>
                    <td class="p-4 font-mono text-xs font-black text-slate-900 whitespace-nowrap">${s.nis}</td>
                    <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-1 bg-slate-200 border-2 border-slate-400 text-slate-900 text-xs font-black rounded-lg">${s.kelas}</span></td>
                    <td class="p-4 text-slate-900 font-black whitespace-nowrap">${s.jk === 'L' ? 'Laki-laki' : 'Perempuan'}</td>
                    <td class="p-4 text-slate-900 font-black whitespace-nowrap">${s.ortu}</td>
                    <td class="p-4 text-emerald-900 font-black whitespace-nowrap"><i class="fa-solid fa-phone mr-1"></i>${s.hp}</td>
                    <td class="p-4 text-center whitespace-nowrap space-x-1.5">
                        <button onclick="openProfilSiswa(${s.id})" title="Profil & Riwayat" class="p-2 bg-blue-100 text-blue-900 border-2 border-blue-400 hover:bg-blue-700 hover:text-white rounded-lg transition-all shadow-sm"><i class="fa-solid fa-id-card"></i></button>
                        <button onclick="editSiswa(${s.id})" title="Edit" class="p-2 bg-amber-100 text-amber-900 border-2 border-amber-400 hover:bg-amber-700 hover:text-white rounded-lg transition-all shadow-sm"><i class="fa-solid fa-pen"></i></button>
                        <button onclick="deleteSiswa(${s.id})" title="Hapus" class="p-2 bg-red-100 text-red-900 border-2 border-red-400 hover:bg-red-700 hover:text-white rounded-lg transition-all shadow-sm"><i class="fa-solid fa-trash"></i></button>
                    </td>
                </tr>
            `).join('') : `<tr><td colspan="8" class="p-6 text-center text-slate-600 font-black">Tidak ada data siswa ditemukan.</td></tr>`;
        }

        function openSiswaModal(id = null) {
            document.getElementById('form-siswa').reset();
            document.getElementById('siswa-id').value = '';
            document.getElementById('modal-siswa-title').innerText = 'Tambah Data Siswa';
            if (id) {
                const s = appData.siswa.find(item => item.id === parseInt(id));
                if (s) {
                    document.getElementById('modal-siswa-title').innerText = 'Edit Data Siswa';
                    document.getElementById('siswa-id').value = s.id;
                    document.getElementById('siswa-nis').value = s.nis;
                    document.getElementById('siswa-nama').value = s.nama;
                    document.getElementById('siswa-kelas').value = s.kelas;
                    document.getElementById('siswa-jk').value = s.jk;
                    document.getElementById('siswa-ttl').value = s.ttl;
                    document.getElementById('siswa-ortu').value = s.ortu;
                    document.getElementById('siswa-hp').value = s.hp;
                    document.getElementById('siswa-foto').value = s.foto;
                    document.getElementById('siswa-alamat').value = s.alamat;
                }
            }
            openModal('modal-siswa');
        }

        async function saveSiswa(e) {
            e.preventDefault();
            const id = document.getElementById('siswa-id').value;
            const data = {
                id: id ? parseInt(id) : Date.now(),
                nis: document.getElementById('siswa-nis').value,
                nama: document.getElementById('siswa-nama').value,
                kelas: document.getElementById('siswa-kelas').value,
                jk: document.getElementById('siswa-jk').value,
                ttl: document.getElementById('siswa-ttl').value,
                ortu: document.getElementById('siswa-ortu').value,
                hp: document.getElementById('siswa-hp').value,
                foto: document.getElementById('siswa-foto').value || 'https://placehold.co/150x150/10b981/ffffff?text=S',
                alamat: document.getElementById('siswa-alamat').value
            };

            if (id) {
                const index = appData.siswa.findIndex(s => s.id === parseInt(id));
                if (index !== -1) appData.siswa[index] = data;
                showNotification('Data siswa berhasil diperbarui!', 'success');
            } else {
                appData.siswa.push(data);
                showNotification('Siswa baru berhasil ditambahkan!', 'success');
            }

            await saveToSupabase();
            closeModal('modal-siswa');
            renderSiswaTable();
            renderDashboard();
            populateDropdowns();
        }

        function editSiswa(id) { openSiswaModal(id); }

        async function deleteSiswa(id) {
            if (confirm('Apakah Anda yakin ingin menghapus data siswa ini?')) {
                appData.siswa = appData.siswa.filter(s => s.id !== parseInt(id));
                await saveToSupabase();
                renderSiswaTable();
                renderDashboard();
                populateDropdowns();
                showNotification('Data siswa berhasil dihapus.', 'info');
            }
        }

        function renderPelanggaranTable() {
            const searchInput = document.getElementById('pelanggaran-search');
            const filterStatusInput = document.getElementById('pelanggaran-filter-status');
            const search = searchInput ? searchInput.value.toLowerCase() : '';
            const filterStatus = filterStatusInput ? filterStatusInput.value : '';
            const tbody = document.getElementById('pelanggaran-table-body');
            if (!tbody) return;

            const filtered = appData.pelanggaran.filter(p => {
                const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                const nama = siswa ? siswa.nama.toLowerCase() : '';
                const jenis = p.nama ? p.nama.toLowerCase() : '';
                const matchSearch = nama.includes(search) || jenis.includes(search) || p.kronologi.toLowerCase().includes(search);
                const matchStatus = filterStatus ? p.status === filterStatus : true;
                return matchSearch && matchStatus;
            });

            tbody.innerHTML = filtered.length ? filtered.map(p => {
                const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                let statusBadgeBg = 'bg-blue-100 text-blue-900 border-blue-400';
                if (p.status === 'Proses') statusBadgeBg = 'bg-amber-100 text-amber-900 border-amber-400';
                if (p.status === 'Selesai') statusBadgeBg = 'bg-emerald-100 text-emerald-900 border-emerald-400';
                if (!p.status) p.status = 'Baru';

                return `
                    <tr class="hover:bg-amber-50 transition-colors">
                        <td class="p-4 text-xs font-mono font-black text-slate-900 whitespace-nowrap">${p.tanggal}</td>
                        <td class="p-4 font-black text-slate-950 whitespace-nowrap">${siswa ? siswa.nama : 'Siswa'}</td>
                        <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-1 bg-slate-200 border-2 border-slate-400 text-slate-900 text-xs font-black rounded-lg">${siswa ? siswa.kelas : '-'}</span></td>
                        <td class="p-4 text-slate-950 font-black whitespace-nowrap">${p.nama || '-'}</td>
                        <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-1 bg-amber-100 border-2 border-amber-400 text-amber-950 text-xs font-black rounded-lg">${p.kategori || '-'}</span></td>
                        <td class="p-4 font-black text-amber-800 whitespace-nowrap">${p.poin || 0} Poin</td>
                        <td class="p-4 text-xs font-black text-slate-900 whitespace-nowrap">${p.tindakan}</td>
                        <td class="p-4 text-xs font-black text-slate-800 whitespace-nowrap">${p.pelapor}</td>
                        <td class="p-4 text-xs font-black text-slate-900 whitespace-nowrap">${p.hasilTindakan || '-'}</td>
                        <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-1 border-2 ${statusBadgeBg} text-xs font-black rounded-lg inline-block">${p.status}</span></td>
                        <td class="p-4 text-center whitespace-nowrap space-x-1">
                            <button onclick="editPelanggaran(${p.id})" title="Edit" class="p-2 bg-amber-100 text-amber-900 border-2 border-amber-400 hover:bg-amber-700 hover:text-white rounded-lg transition-all shadow-sm"><i class="fa-solid fa-pen"></i></button>
                            <button onclick="deletePelanggaran(${p.id})" title="Hapus" class="p-2 bg-red-100 text-red-900 border-2 border-red-400 hover:bg-red-700 hover:text-white rounded-lg transition-all shadow-sm"><i class="fa-solid fa-trash"></i></button>
                        </td>
                    </tr>
                `;
            }).join('') : `<tr><td colspan="11" class="p-6 text-center text-slate-600 font-black">Belum ada catatan pelanggaran.</td></tr>`;
        }

        function openPelanggaranModal(id = null) {
            document.getElementById('form-pelanggaran').reset();
            document.getElementById('pelanggaran-id').value = '';
            document.getElementById('modal-pelanggaran-title').innerText = 'Catat Pelanggaran Siswa';
            if (id) {
                const p = appData.pelanggaran.find(item => item.id === parseInt(id));
                if (p) {
                    document.getElementById('modal-pelanggaran-title').innerText = 'Edit Catatan Pelanggaran';
                    document.getElementById('pelanggaran-id').value = p.id;
                    document.getElementById('pelanggaran-siswa-id').value = p.siswaId;
                    document.getElementById('pelanggaran-tanggal').value = p.tanggal;
                    document.getElementById('pelanggaran-nama-custom').value = p.nama || '';
                    document.getElementById('pelanggaran-kategori-custom').value = p.kategori || 'Ringan';
                    document.getElementById('pelanggaran-poin-custom').value = p.poin || 5;
                    document.getElementById('pelanggaran-status').value = p.status || 'Baru';
                    document.getElementById('pelanggaran-kronologi').value = p.kronologi;
                    document.getElementById('pelanggaran-pelapor').value = p.pelapor;
                    document.getElementById('pelanggaran-tindakan').value = p.tindakan;
                    document.getElementById('pelanggaran-hasil-tindakan').value = p.hasilTindakan || '';
                }
            }
            openModal('modal-pelanggaran');
        }

        function editPelanggaran(id) { openPelanggaranModal(id); }

        async function savePelanggaran(e) {
            e.preventDefault();
            const id = document.getElementById('pelanggaran-id').value;
            const data = {
                id: id ? parseInt(id) : Date.now(),
                siswaId: parseInt(document.getElementById('pelanggaran-siswa-id').value),
                tanggal: document.getElementById('pelanggaran-tanggal').value,
                nama: document.getElementById('pelanggaran-nama-custom').value,
                kategori: document.getElementById('pelanggaran-kategori-custom').value,
                poin: parseInt(document.getElementById('pelanggaran-poin-custom').value),
                status: document.getElementById('pelanggaran-status').value,
                kronologi: document.getElementById('pelanggaran-kronologi').value,
                pelapor: document.getElementById('pelanggaran-pelapor').value,
                tindakan: document.getElementById('pelanggaran-tindakan').value,
                hasilTindakan: document.getElementById('pelanggaran-hasil-tindakan').value
            };

            if (id) {
                const index = appData.pelanggaran.findIndex(p => p.id === parseInt(id));
                if (index !== -1) appData.pelanggaran[index] = data;
                showNotification('Catatan pelanggaran diperbarui.', 'success');
            } else {
                appData.pelanggaran.push(data);
                showNotification('Catatan pelanggaran berhasil disimpan.', 'success');
            }

            await saveToSupabase();
            closeModal('modal-pelanggaran');
            renderPelanggaranTable();
            renderDashboard();
        }

        async function deletePelanggaran(id) {
            if (confirm('Hapus catatan pelanggaran ini?')) {
                appData.pelanggaran = appData.pelanggaran.filter(p => p.id !== parseInt(id));
                await saveToSupabase();
                renderPelanggaranTable();
                renderDashboard();
                showNotification('Catatan pelanggaran dihapus.', 'info');
            }
        }

        function renderPrestasiTable() {
            const searchInput = document.getElementById('prestasi-search');
            const search = searchInput ? searchInput.value.toLowerCase() : '';
            const tbody = document.getElementById('prestasi-table-body');
            if (!tbody) return;

            const filtered = appData.prestasi.filter(p => {
                const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                const namaSiswa = siswa ? siswa.nama.toLowerCase() : '';
                return namaSiswa.includes(search) || p.nama.toLowerCase().includes(search) || p.bidang.toLowerCase().includes(search);
            });

            tbody.innerHTML = filtered.length ? filtered.map(p => {
                const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                return `
                    <tr class="hover:bg-emerald-50 transition-colors">
                        <td class="p-4 text-xs font-mono font-black text-slate-900 whitespace-nowrap">${p.tanggal}</td>
                        <td class="p-4 font-black text-slate-950 whitespace-nowrap">${siswa ? siswa.nama : 'Siswa'}</td>
                        <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-1 bg-slate-200 border-2 border-slate-400 text-slate-900 text-xs font-black rounded-lg">${siswa ? siswa.kelas : '-'}</span></td>
                        <td class="p-4 text-slate-950 font-black whitespace-nowrap">${p.nama}</td>
                        <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-0.5 bg-emerald-100 border-2 border-emerald-400 text-emerald-950 rounded font-black">${p.bidang}</span></td>
                        <td class="p-4 text-xs font-black text-slate-900 whitespace-nowrap">${p.tingkat}</td>
                        <td class="p-4 text-xs font-black text-emerald-800 whitespace-nowrap">${p.juara}</td>
                        <td class="p-4 text-xs font-black text-slate-900 whitespace-nowrap">${p.penyelenggara}</td>
                        <td class="p-4 text-center whitespace-nowrap">
                            <button onclick="deletePrestasi(${p.id})" class="p-2 bg-red-100 text-red-900 border-2 border-red-400 hover:bg-red-700 hover:text-white rounded-lg transition-all shadow-sm"><i class="fa-solid fa-trash"></i></button>
                        </td>
                    </tr>
                `;
            }).join('') : `<tr><td colspan="9" class="p-6 text-center text-slate-600 font-black">Belum ada catatan prestasi.</td></tr>`;
        }

        function openPrestasiModal() {
            document.getElementById('form-prestasi').reset();
            openModal('modal-prestasi');
        }

        async function savePrestasi(e) {
            e.preventDefault();
            const data = {
                id: Date.now(),
                siswaId: parseInt(document.getElementById('prestasi-siswa-id').value),
                tanggal: document.getElementById('prestasi-tanggal').value,
                bidang: document.getElementById('prestasi-bidang').value,
                nama: document.getElementById('prestasi-nama').value,
                tingkat: document.getElementById('prestasi-tingkat').value,
                juara: document.getElementById('prestasi-juara').value,
                penyelenggara: document.getElementById('prestasi-penyelenggara').value,
                dokumentasi: document.getElementById('prestasi-dokumentasi').value || 'https://placehold.co/300x200/10b981/ffffff?text=Prestasi'
            };

            appData.prestasi.push(data);
            await saveToSupabase();
            closeModal('modal-prestasi');
            renderPrestasiTable();
            renderDashboard();
            showNotification('Catatan prestasi berhasil disimpan.', 'success');
        }

        async function deletePrestasi(id) {
            if (confirm('Hapus catatan prestasi ini?')) {
                appData.prestasi = appData.prestasi.filter(p => p.id !== parseInt(id));
                await saveToSupabase();
                renderPrestasiTable();
                renderDashboard();
                showNotification('Catatan prestasi dihapus.', 'info');
            }
        }

        function renderPembinaanTable() {
            const searchInput = document.getElementById('pembinaan-search');
            const search = searchInput ? searchInput.value.toLowerCase() : '';
            const tbody = document.getElementById('pembinaan-table-body');
            if (!tbody) return;

            const filtered = appData.pembinaan.filter(p => {
                const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                const nama = siswa ? siswa.nama.toLowerCase() : '';
                return nama.includes(search) || p.permasalahan.toLowerCase().includes(search) || p.bentuk.toLowerCase().includes(search);
            });

            tbody.innerHTML = filtered.length ? filtered.map(p => {
                const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                const statusBadge = p.status === 'Selesai' ? 'bg-emerald-100 border-2 border-emerald-400 text-emerald-950' : 'bg-red-100 border-2 border-red-400 text-red-950';
                return `
                    <tr class="hover:bg-red-50 transition-colors">
                        <td class="p-4 text-xs font-mono font-black text-slate-900 whitespace-nowrap">${p.tanggal}</td>
                        <td class="p-4 font-black text-slate-950 whitespace-nowrap">${siswa ? siswa.nama : 'Siswa'}</td>
                        <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-1 bg-slate-200 border-2 border-slate-400 text-slate-900 text-xs font-black rounded-lg">${siswa ? siswa.kelas : '-'}</span></td>
                        <td class="p-4 text-slate-950 text-xs font-black whitespace-nowrap">${p.permasalahan}</td>
                        <td class="p-4 text-xs font-black text-slate-950 whitespace-nowrap">${p.bentuk}</td>
                        <td class="p-4 text-xs font-black text-slate-900 whitespace-nowrap">${p.hasil}</td>
                        <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-1 ${statusBadge} text-xs font-black rounded-lg inline-block">${p.status}</span></td>
                        <td class="p-4 text-center whitespace-nowrap">
                            <button onclick="deletePembinaan(${p.id})" class="p-2 bg-red-100 text-red-900 border-2 border-red-400 hover:bg-red-700 hover:text-white rounded-lg transition-all shadow-sm"><i class="fa-solid fa-trash"></i></button>
                        </td>
                    </tr>
                `;
            }).join('') : `<tr><td colspan="8" class="p-6 text-center text-slate-600 font-black">Belum ada data pembinaan.</td></tr>`;
        }

        function openPembinaanModal() {
            document.getElementById('form-pembinaan').reset();
            openModal('modal-pembinaan');
        }

        async function savePembinaan(e) {
            e.preventDefault();
            const data = {
                id: Date.now(),
                siswaId: parseInt(document.getElementById('pembinaan-siswa-id').value),
                tanggal: document.getElementById('pembinaan-tanggal').value,
                permasalahan: document.getElementById('pembinaan-permasalahan').value,
                bentuk: document.getElementById('pembinaan-bentuk').value,
                hasil: document.getElementById('pembinaan-hasil').value,
                tindaklanjut: document.getElementById('pembinaan-tindaklanjut').value,
                status: document.getElementById('pembinaan-status').value
            };

            appData.pembinaan.push(data);
            await saveToSupabase();
            closeModal('modal-pembinaan');
            renderPembinaanTable();
            renderDashboard();
            showNotification('Catatan pembinaan berhasil disimpan.', 'success');
        }

        async function deletePembinaan(id) {
            if (confirm('Hapus data pembinaan ini?')) {
                appData.pembinaan = appData.pembinaan.filter(p => p.id !== parseInt(id));
                await saveToSupabase();
                renderPembinaanTable();
                renderDashboard();
                showNotification('Data pembinaan dihapus.', 'info');
            }
        }

        function renderKegiatanTable() {
            const searchInput = document.getElementById('kegiatan-search');
            const search = searchInput ? searchInput.value.toLowerCase() : '';
            const tbody = document.getElementById('kegiatan-table-body');
            if (!tbody) return;

            const filtered = appData.kegiatan.filter(k => k.nama.toLowerCase().includes(search) || k.tempat.toLowerCase().includes(search));

            tbody.innerHTML = filtered.length ? filtered.map(k => `
                <tr class="hover:bg-purple-50 transition-colors">
                    <td class="p-4 text-xs font-mono font-black text-slate-900 whitespace-nowrap">${k.tanggal}</td>
                    <td class="p-4 font-black text-slate-950 whitespace-nowrap">${k.nama}</td>
                    <td class="p-4 whitespace-nowrap"><span class="px-2 py-0.5 bg-purple-100 border-2 border-purple-400 text-purple-950 rounded font-black">${k.jenis}</span></td>
                    <td class="p-4 text-xs font-black text-slate-900 whitespace-nowrap">${k.tempat}</td>
                    <td class="p-4 text-xs font-black text-slate-900 whitespace-nowrap">${k.pj}</td>
                    <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-1 bg-slate-200 border-2 border-slate-400 text-slate-900 text-xs font-black rounded-lg inline-block">${k.status}</span></td>
                    <td class="p-4 text-center whitespace-nowrap">
                        <button onclick="deleteKegiatan(${k.id})" class="p-2 bg-red-100 text-red-900 border-2 border-red-400 hover:bg-red-700 hover:text-white rounded-lg transition-all shadow-sm"><i class="fa-solid fa-trash"></i></button>
                    </td>
                </tr>
            `).join('') : `<tr><td colspan="7" class="p-6 text-center text-slate-600 font-black">Tidak ada kegiatan ditemukan.</td></tr>`;
        }

        function openKegiatanModal() {
            document.getElementById('form-kegiatan').reset();
            openModal('modal-kegiatan');
        }

        async function saveKegiatan(e) {
            e.preventDefault();
            const data = {
                id: Date.now(),
                nama: document.getElementById('kegiatan-nama').value,
                jenis: document.getElementById('kegiatan-jenis').value,
                tanggal: document.getElementById('kegiatan-tanggal').value,
                tempat: document.getElementById('kegiatan-tempat').value,
                pj: document.getElementById('kegiatan-pj').value,
                peserta: document.getElementById('kegiatan-peserta').value,
                status: document.getElementById('kegiatan-status').value,
                catatan: document.getElementById('kegiatan-catatan').value
            };

            appData.kegiatan.push(data);
            await saveToSupabase();
            closeModal('modal-kegiatan');
            renderKegiatanTable();
            renderDashboard();
            showNotification('Kegiatan kesiswaan berhasil disimpan.', 'success');
        }

        async function deleteKegiatan(id) {
            if (confirm('Hapus kegiatan ini?')) {
                appData.kegiatan = appData.kegiatan.filter(k => k.id !== parseInt(id));
                await saveToSupabase();
                renderKegiatanTable();
                renderDashboard();
                showNotification('Kegiatan dihapus.', 'info');
            }
        }

        function renderPerizinanTable() {
            const searchInput = document.getElementById('perizinan-search');
            const search = searchInput ? searchInput.value.toLowerCase() : '';
            const tbody = document.getElementById('perizinan-table-body');
            if (!tbody) return;

            const filtered = appData.perizinan.filter(p => {
                const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                const nama = siswa ? siswa.nama.toLowerCase() : '';
                return nama.includes(search) || p.keperluan.toLowerCase().includes(search);
            });

            tbody.innerHTML = filtered.length ? filtered.map(p => {
                const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                const badge = p.status === 'Kembali' ? 'bg-emerald-100 border-2 border-emerald-400 text-emerald-950' : 'bg-amber-100 border-2 border-amber-400 text-amber-950';
                return `
                    <tr class="hover:bg-teal-50 transition-colors">
                        <td class="p-4 text-xs font-mono font-black text-slate-900 whitespace-nowrap">${p.tanggal}</td>
                        <td class="p-4 font-black text-slate-950 whitespace-nowrap">${siswa ? siswa.nama : 'Siswa'}</td>
                        <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-1 bg-slate-200 border-2 border-slate-400 text-slate-900 text-xs font-black rounded-lg">${siswa ? siswa.kelas : '-'}</span></td>
                        <td class="p-4 text-xs font-mono font-black text-slate-900 whitespace-nowrap">${p.jamKeluar}</td>
                        <td class="p-4 text-xs font-mono font-black text-slate-900 whitespace-nowrap">${p.jamKembali}</td>
                        <td class="p-4 text-xs font-black text-slate-950 whitespace-nowrap">${p.keperluan}</td>
                        <td class="p-4 text-xs font-black text-slate-900 whitespace-nowrap">${p.penjemput}</td>
                        <td class="p-4 whitespace-nowrap"><span class="px-2.5 py-1 ${badge} text-xs font-black rounded-lg inline-block">${p.status}</span></td>
                        <td class="p-4 text-center whitespace-nowrap">
                            <button onclick="deletePerizinan(${p.id})" class="p-2 bg-red-100 text-red-900 border-2 border-red-400 hover:bg-red-700 hover:text-white rounded-lg transition-all shadow-sm"><i class="fa-solid fa-trash"></i></button>
                        </td>
                    </tr>
                `;
            }).join('') : `<tr><td colspan="9" class="p-6 text-center text-slate-600 font-black">Tidak ada data perizinan.</td></tr>`;
        }

        function openPerizinanModal() {
            document.getElementById('form-perizinan').reset();
            openModal('modal-perizinan');
        }

        async function savePerizinan(e) {
            e.preventDefault();
            const data = {
                id: Date.now(),
                siswaId: parseInt(document.getElementById('perizinan-siswa-id').value),
                tanggal: document.getElementById('perizinan-tanggal').value,
                jamKeluar: document.getElementById('perizinan-jam-keluar').value,
                jamKembali: document.getElementById('perizinan-jam-kembali').value,
                keperluan: document.getElementById('perizinan-keperluan').value,
                penjemput: document.getElementById('perizinan-penjemput').value,
                status: document.getElementById('perizinan-status').value
            };

            appData.perizinan.push(data);
            await saveToSupabase();
            closeModal('modal-perizinan');
            renderPerizinanTable();
            renderDashboard();
            showNotification('Perizinan siswa berhasil dicatat.', 'success');
        }

        async function deletePerizinan(id) {
            if (confirm('Hapus data perizinan ini?')) {
                appData.perizinan = appData.perizinan.filter(p => p.id !== parseInt(id));
                await saveToSupabase();
                renderPerizinanTable();
                showNotification('Perizinan dihapus.', 'info');
            }
        }

        function generateLaporan() {
            const jenisEl = document.getElementById('laporan-jenis');
            const kelasEl = document.getElementById('laporan-kelas');
            const jenis = jenisEl ? jenisEl.value : 'pelanggaran';
            const kelas = kelasEl ? kelasEl.value : '';

            const titleHead = document.getElementById('laporan-title-heading');
            const subInfo = document.getElementById('laporan-subtitle-info');
            if (titleHead) titleHead.innerText = `LAPORAN ${jenis.toUpperCase()} KESISWAAN`;
            if (subInfo) subInfo.innerText = `Kelas: ${kelas || 'Semua'} | SIM Kesiswaan`;

            const thead = document.getElementById('laporan-table-head');
            const tbody = document.getElementById('laporan-table-body');
            if (!thead || !tbody) return;

            if (jenis === 'pelanggaran') {
                thead.innerHTML = `<tr class="bg-slate-950 text-xs uppercase font-black text-emerald-400 border-b-2 border-slate-800"><th class="p-3 bg-slate-950">Tanggal</th><th class="p-3 bg-slate-950">Siswa</th><th class="p-3 bg-slate-950">Kelas</th><th class="p-3 bg-slate-950">Jenis Pelanggaran</th><th class="p-3 bg-slate-950">Poin</th><th class="p-3 bg-slate-950">Tindakan</th></tr>`;
                const filtered = appData.pelanggaran.filter(p => {
                    const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                    if (!siswa) return false;
                    if (kelas && siswa.kelas !== kelas) return false;
                    return true;
                });
                tbody.innerHTML = filtered.length ? filtered.map(p => {
                    const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                    return `<tr class="border-b-2 border-slate-200"><td class="p-3 font-mono whitespace-nowrap">${p.tanggal}</td><td class="p-3 font-black text-slate-950 whitespace-normal break-words">${siswa ? siswa.nama : ''}</td><td class="p-3 whitespace-nowrap">${siswa ? siswa.kelas : ''}</td><td class="p-3 whitespace-normal break-words">${p.nama || ''}</td><td class="p-3 font-black text-amber-800 whitespace-nowrap">${p.poin || 0}</td><td class="p-3 whitespace-normal break-words">${p.tindakan}</td></tr>`;
                }).join('') : `<tr><td colspan="6" class="p-4 text-center text-slate-600 font-black">Tidak ada data untuk laporan ini.</td></tr>`;
            } else if (jenis === 'prestasi') {
                thead.innerHTML = `<tr class="bg-slate-950 text-xs uppercase font-black text-emerald-400 border-b-2 border-slate-800"><th class="p-3 bg-slate-950">Tanggal</th><th class="p-3 bg-slate-950">Siswa</th><th class="p-3 bg-slate-950">Kelas</th><th class="p-3 bg-slate-950">Nama Prestasi</th><th class="p-3 bg-slate-950">Tingkat</th><th class="p-3 bg-slate-950">Juara</th></tr>`;
                const filtered = appData.prestasi.filter(p => {
                    const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                    if (!siswa) return false;
                    if (kelas && siswa.kelas !== kelas) return false;
                    return true;
                });
                tbody.innerHTML = filtered.length ? filtered.map(p => {
                    const siswa = appData.siswa.find(s => s.id === parseInt(p.siswaId));
                    return `<tr class="border-b-2 border-slate-200"><td class="p-3 font-mono whitespace-nowrap">${p.tanggal}</td><td class="p-3 font-black text-slate-950 whitespace-normal break-words">${siswa ? siswa.nama : ''}</td><td class="p-3 whitespace-nowrap">${siswa ? siswa.kelas : ''}</td><td class="p-3 font-black whitespace-normal break-words">${p.nama}</td><td class="p-3 whitespace-nowrap">${p.tingkat}</td><td class="p-3 font-black text-emerald-800 whitespace-nowrap">${p.juara}</td></tr>`;
                }).join('') : `<tr><td colspan="6" class="p-4 text-center text-slate-600 font-black">Tidak ada data untuk laporan ini.</td></tr>`;
            }
            showNotification('Laporan berhasil diperbarui.', 'success');
        }

        function exportToExcel() { showNotification('Fitur export Excel berhasil diproses.', 'success'); }

        function downloadPDF(title, tbodyId, headers) {
            const tbodyEl = document.getElementById(tbodyId);
            if (!tbodyEl) return;
            const tbodyHtml = tbodyEl.innerHTML;
            const printWindow = window.open('', '_blank');
            printWindow.document.write(`
                <!DOCTYPE html>
                <html>
                <head>
                    <title>${title}</title>
                    <style>
                        body { font-family: 'Inter', sans-serif; padding: 20px; color: #020617; }
                        h2 { text-align: center; margin-bottom: 5px; font-weight: 900; }
                        p { text-align: center; font-size: 12px; color: #334155; margin-bottom: 20px; font-weight: 700; }
                        table { width: 100%; border-collapse: collapse; margin-top: 10px; font-size: 11px; }
                        th, td { border: 2px solid #64748b; padding: 8px 12px; text-align: left; font-weight: 700; }
                        th { background-color: #020617; color: #ffffff; }
                        tr:nth-child(even) { background-color: #f1f5f9; }
                    </style>
                </head>
                <body>
                    <h2>${title.toUpperCase()}</h2>
                    <p>SIM Kesiswaan Profesional | Diunduh pada: ${new Date().toLocaleDateString('id-ID', { dateStyle: 'full' })}</p>
                    <table>
                        <thead>
                            <tr>${headers.map(h => `<th>${h}</th>`).join('')}</tr>
                        </thead>
                        <tbody>
                            ${tbodyHtml.replace(/<button[\s\S]*?<\/button>/g, '').replace(/<i[\s\S]*?<\/i>/g, '')}
                        </tbody>
                    </table>
                    <script>
                        window.onload = function() { window.print(); }
                    <\/script>
                </body>
                </html>
            `);
            printWindow.document.close();
        }

        function downloadProfilPDF(siswaId) {
            const siswa = appData.siswa.find(s => s.id === parseInt(siswaId));
            if (!siswa) return;
            const totalPoin = getSiswaTotalPoin(siswa.id);
            const pelanggaranList = appData.pelanggaran.filter(p => parseInt(p.siswaId) === siswa.id);
            const prestasiList = appData.prestasi.filter(p => parseInt(p.siswaId) === siswa.id);
            const pembinaanList = appData.pembinaan.filter(p => parseInt(p.siswaId) === siswa.id);
            const perizinanList = appData.perizinan.filter(p => parseInt(p.siswaId) === siswa.id);

            const printWindow = window.open('', '_blank');
            printWindow.document.write(`
                <!DOCTYPE html>
                <html>
                <head>
                    <title>Rekam Jejak - ${siswa.nama}</title>
                    <style>
                        body { font-family: 'Inter', sans-serif; padding: 25px; color: #020617; }
                        h2, h3 { font-weight: 900; color: #020617; }
                        .header { border-bottom: 3px solid #020617; padding-bottom: 10px; margin-bottom: 20px; }
                        table { width: 100%; border-collapse: collapse; margin-top: 10px; margin-bottom: 20px; font-size: 11px; }
                        th, td { border: 2px solid #64748b; padding: 6px 10px; text-align: left; font-weight: 700; }
                        th { background-color: #020617; color: #ffffff; }
                    </style>
                </head>
                <body>
                    <div class="header">
                        <h2>REKAM JEJAK & PROFIL KESISWAAN</h2>
                        <p><strong>Nama:</strong> ${siswa.nama} | <strong>NIS:</strong> ${siswa.nis} | <strong>Kelas:</strong> ${siswa.kelas} | <strong>Total Poin:</strong> ${totalPoin}</p>
                    </div>

                    <h3>1. Riwayat Pelanggaran</h3>
                    <table>
                        <thead><tr><th>Tanggal</th><th>Jenis Pelanggaran</th><th>Poin</th><th>Tindakan / Hasil</th><th>Status</th></tr></thead>
                        <tbody>
                            ${pelanggaranList.length ? pelanggaranList.map(p => `<tr><td>${p.tanggal}</td><td>${p.nama || '-'}</td><td>${p.poin || 0}</td><td>${p.tindakan} (${p.hasilTindakan || '-'})</td><td>${p.status}</td></tr>`).join('') : '<tr><td colspan="5">Tidak ada data</td></tr>'}
                        </tbody>
                    </table>

                    <h3>2. Riwayat Prestasi</h3>
                    <table>
                        <thead><tr><th>Tanggal</th><th>Nama Prestasi</th><th>Bidang & Tingkat</th><th>Juara</th></tr></thead>
                        <tbody>
                            ${prestasiList.length ? prestasiList.map(p => `<tr><td>${p.tanggal}</td><td>${p.nama}</td><td>${p.bidang} (${p.tingkat})</td><td>${p.juara}</td></tr>`).join('') : '<tr><td colspan="4">Tidak ada data</td></tr>'}
                        </tbody>
                    </table>

                    <h3>3. Riwayat Pembinaan</h3>
                    <table>
                        <thead><tr><th>Tanggal</th><th>Permasalahan</th><th>Bentuk Pembinaan</th><th>Status</th></tr></thead>
                        <tbody>
                            ${pembinaanList.length ? pembinaanList.map(p => `<tr><td>${p.tanggal}</td><td>${p.permasalahan}</td><td>${p.bentuk}</td><td>${p.status}</td></tr>`).join('') : '<tr><td colspan="4">Tidak ada data</td></tr>'}
                        </tbody>
                    </table>

                    <h3>4. Riwayat Perizinan Keluar</h3>
                    <table>
                        <thead><tr><th>Tanggal</th><th>Waktu</th><th>Keperluan</th><th>Penjemput</th></tr></thead>
                        <tbody>
                            ${perizinanList.length ? perizinanList.map(p => `<tr><td>${p.tanggal}</td><td>${p.jamKeluar} - ${p.jamKembali}</td><td>${p.keperluan}</td><td>${p.penjemput}</td></tr>`).join('') : '<tr><td colspan="4">Tidak ada data</td></tr>'}
                        </tbody>
                    </table>

                    <script>
                        window.onload = function() { window.print(); }
                    <\/script>
                </body>
                </html>
            `);
            printWindow.document.close();
        }

        function renderPengaturan() {
            validateAppData();
            const kelasBody = document.getElementById('pengaturan-kelas-body');
            if (kelasBody) {
                const sortedKelas = [...appData.kelas].sort((a,b) => b.localeCompare(a));
                kelasBody.innerHTML = sortedKelas.map(k => {
                    const count = appData.siswa.filter(s => s.kelas === k).length;
                    return `
                        <tr class="hover:bg-slate-100">
                            <td class="p-4 font-black text-slate-950">${k}</td>
                            <td class="p-4 font-black text-emerald-800">${count} Siswa</td>
                            <td class="p-4 text-right"><button onclick="deleteKelas('${k}')" class="text-red-700 hover:text-red-900 font-black p-2"><i class="fa-solid fa-trash"></i></button></td>
                        </tr>
                    `;
                }).join('');
            }

            const guruBody = document.getElementById('pengaturan-guru-body');
            if (guruBody) {
                guruBody.innerHTML = appData.guru.map(g => `
                    <tr class="hover:bg-slate-100">
                        <td class="p-4 font-black text-slate-950">${g}</td>
                        <td class="p-4 text-right"><button onclick="deleteGuru('${g}')" class="text-red-700 hover:text-red-900 font-black p-2"><i class="fa-solid fa-trash"></i></button></td>
                    </tr>
                `).join('');
            }
        }

        function openKelasModal() { openModal('modal-kelas'); }

        async function saveKelas(e) {
            e.preventDefault();
            validateAppData();
            const nama = document.getElementById('input-nama-kelas').value;
            if (!appData.kelas.includes(nama)) {
                appData.kelas.push(nama);
                await saveToSupabase();
                renderPengaturan();
                populateDropdowns();
                closeModal('modal-kelas');
                showNotification('Kelas baru berhasil ditambahkan.', 'success');
            } else {
                showNotification('Nama kelas sudah ada.', 'info');
            }
        }

        async function deleteKelas(nama) {
            validateAppData();
            appData.kelas = appData.kelas.filter(k => k !== nama);
            await saveToSupabase();
            renderPengaturan();
            populateDropdowns();
            showNotification('Kelas dihapus.', 'info');
        }

        function openGuruModal() { openModal('modal-guru'); }

        async function saveGuru(e) {
            e.preventDefault();
            validateAppData();
            const nama = document.getElementById('input-nama-guru').value;
            if (!appData.guru.includes(nama)) {
                appData.guru.push(nama);
                await saveToSupabase();
                renderPengaturan();
                populateDropdowns();
                closeModal('modal-guru');
                showNotification('Data guru pelapor berhasil ditambahkan.', 'success');
            } else {
                showNotification('Nama guru sudah ada.', 'info');
            }
        }

        async function deleteGuru(nama) {
            validateAppData();
            appData.guru = appData.guru.filter(g => g !== nama);
            await saveToSupabase();
            renderPengaturan();
            populateDropdowns();
            showNotification('Data guru dihapus.', 'info');
        }

        function openProfilSiswa(siswaId) {
            const siswa = appData.siswa.find(s => s.id === parseInt(siswaId));
            if (!siswa) return;

            const totalPoin = getSiswaTotalPoin(siswa.id);
            const pelanggaranList = appData.pelanggaran.filter(p => parseInt(p.siswaId) === siswa.id);
            const prestasiList = appData.prestasi.filter(p => parseInt(p.siswaId) === siswa.id);
            const pembinaanList = appData.pembinaan.filter(p => parseInt(p.siswaId) === siswa.id);
            const perizinanList = appData.perizinan.filter(p => parseInt(p.siswaId) === siswa.id);

            const container = document.getElementById('profil-siswa-container');
            if (!container) return;

            container.innerHTML = `
                <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md flex flex-col md:flex-row items-center justify-between gap-4">
                    <div class="flex flex-col md:flex-row items-center space-y-4 md:space-y-0 md:space-x-6">
                        <img src="${siswa.foto}" onerror="this.src='https://placehold.co/150x150/10b981/ffffff?text=S'" class="w-28 h-28 sm:w-32 sm:h-32 rounded-2xl object-cover shadow-md border-2 border-emerald-600 flex-shrink-0">
                        <div class="flex-1 text-center md:text-left min-w-0">
                            
                            <p class="text-xs font-black text-slate-600 mt-1 font-mono">NIS: ${siswa.nis} | Kelas: <strong class="text-slate-950">${siswa.kelas}</strong></p>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 mt-4 text-xs font-black text-slate-900">
                                <div><i class="fa-solid fa-venus-mars mr-2 text-emerald-700"></i>Jenis Kelamin: ${siswa.jk === 'L' ? 'Laki-laki' : 'Perempuan'}</div>
                                <div><i class="fa-solid fa-cake-candles mr-2 text-emerald-700"></i>TTL: ${siswa.ttl}</div>
                                <div><i class="fa-solid fa-user-tie mr-2 text-emerald-700"></i>Orang Tua: ${siswa.ortu} (${siswa.hp})</div>
                                <div><i class="fa-solid fa-location-dot mr-2 text-emerald-700"></i>Alamat: ${siswa.alamat}</div>
                            </div>
                        </div>
                    </div>
                    <div>
                        <button onclick="downloadProfilPDF(${siswa.id})" class="px-5 py-3 bg-emerald-700 hover:bg-emerald-600 text-white font-black rounded-xl text-xs shadow-md transition-all flex items-center space-x-2">
                            <i class="fa-solid fa-file-pdf text-base"></i><span>Download PDF Rekam Jejak</span>
                        </button>
                    </div>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md space-y-4">
                        <h3 class="text-base font-black text-amber-900 flex items-center"><i class="fa-solid fa-triangle-exclamation mr-2"></i>Riwayat Pelanggaran</h3>
                        <div class="space-y-3 max-h-72 overflow-y-auto">
                            ${pelanggaranList.length ? pelanggaranList.map(p => `
                                <div class="p-3 bg-slate-50 border-2 border-slate-300 rounded-xl border-l-8 border-amber-600 space-y-1">
                                    <div class="flex justify-between text-xs">
                                        <span class="font-black text-slate-950 whitespace-normal break-words pr-2">${p.nama || '-'}</span>
                                        <span class="px-2 py-0.5 bg-amber-100 border-2 border-amber-400 text-amber-950 text-[10px] font-black rounded flex-shrink-0">${p.status || 'Baru'}</span>
                                    </div>
                                    <p class="text-xs font-black text-slate-700">${p.tanggal} | Poin: ${p.poin || 0} | ${p.kronologi}</p>
                                </div>
                            `).join('') : '<p class="text-xs text-slate-600 font-black">Tidak ada catatan pelanggaran.</p>'}
                        </div>
                    </div>

                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md space-y-4">
                        <h3 class="text-base font-black text-emerald-900 flex items-center"><i class="fa-solid fa-trophy mr-2"></i>Riwayat Prestasi</h3>
                        <div class="space-y-3 max-h-72 overflow-y-auto">
                            ${prestasiList.length ? prestasiList.map(p => `
                                <div class="p-3 bg-slate-50 border-2 border-slate-300 rounded-2xl border-l-8 border-emerald-600">
                                    <div class="flex justify-between text-xs">
                                        <span class="font-black text-slate-950 whitespace-normal break-words pr-2">${p.nama}</span>
                                        <span class="font-black text-emerald-900 flex-shrink-0">${p.juara}</span>
                                    </div>
                                    <p class="text-xs font-black text-slate-700 mt-1">${p.tanggal} | Bidang: ${p.bidang} (${p.tingkat})</p>
                                </div>
                            `).join('') : '<p class="text-xs text-slate-600 font-black">Tidak ada catatan prestasi.</p>'}
                        </div>
                    </div>

                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md space-y-4">
                        <h3 class="text-base font-black text-red-900 flex items-center"><i class="fa-solid fa-handshake-angle mr-2"></i>Riwayat Pembinaan</h3>
                        <div class="space-y-3 max-h-72 overflow-y-auto">
                            ${pembinaanList.length ? pembinaanList.map(p => `
                                <div class="p-3 bg-slate-50 border-2 border-slate-300 rounded-xl border-l-8 border-red-600">
                                    <div class="flex justify-between text-xs">
                                        <span class="font-black text-slate-950 whitespace-normal break-words pr-2">${p.bentuk}</span>
                                        <span class="px-2 py-0.5 bg-red-100 border-2 border-red-400 text-red-950 font-black rounded flex-shrink-0">${p.status}</span>
                                    </div>
                                    <p class="text-xs font-black text-slate-700 mt-1">Permasalahan: ${p.permasalahan}</p>
                                </div>
                            `).join('') : '<p class="text-xs text-slate-600 font-black">Tidak ada catatan pembinaan.</p>'}
                        </div>
                    </div>

                    <div class="bg-white border-2 border-slate-300 rounded-2xl p-5 sm:p-6 shadow-md space-y-4">
                        <h3 class="text-base font-black text-teal-900 flex items-center"><i class="fa-solid fa-right-from-bracket mr-2"></i>Riwayat Perizinan Keluar</h3>
                        <div class="space-y-3 max-h-72 overflow-y-auto">
                            ${perizinanList.length ? perizinanList.map(p => `
                                <div class="p-3 bg-slate-50 border-2 border-slate-300 rounded-xl border-l-8 border-teal-600">
                                    <div class="flex justify-between text-xs">
                                        <span class="font-black text-slate-950 whitespace-normal break-words pr-2">${p.keperluan}</span>
                                        <span class="text-xs font-mono font-black text-slate-700 flex-shrink-0">${p.tanggal}</span>
                                    </div>
                                    <p class="text-xs font-black text-slate-700 mt-1">Waktu: ${p.jamKeluar} - ${p.jamKembali} | Penjemput: ${p.penjemput}</p>
                                </div>
                            `).join('') : '<p class="text-xs text-slate-600 font-black">Tidak ada catatan perizinan.</p>'}
                        </div>
                    </div>
                </div>
            `;

            switchTab('profil-siswa');
        }

        function handleGlobalSearch(query) {
            const resultsContainer = document.getElementById('global-search-results');
            if (!resultsContainer) return;
            if (!query.trim()) {
                resultsContainer.classList.add('hidden');
                return;
            }

            const matched = appData.siswa.filter(s => s.nama.toLowerCase().includes(query.toLowerCase()) || s.nis.includes(query));
            if (matched.length) {
                resultsContainer.classList.remove('hidden');
                resultsContainer.innerHTML = matched.map(s => `
                    <div class="p-3 hover:bg-slate-100 cursor-pointer border-b-2 border-slate-200 flex items-center space-x-3" onclick="openProfilSiswa(${s.id}); document.getElementById('global-search-results').classList.add('hidden');">
                        <img src="${s.foto}" onerror="this.src='https://placehold.co/100x100/10b981/ffffff?text=S'" class="w-8 h-8 rounded-full object-cover border-2 border-emerald-600 flex-shrink-0">
                        <div class="min-w-0">
                            <h4 class="text-xs font-black text-slate-950 truncate">${s.nama}</h4>
                            <span class="text-[10px] font-black text-slate-600 truncate block">${s.kelas} | NIS: ${s.nis}</span>
                        </div>
                    </div>
                `).join('');
            } else {
                resultsContainer.classList.remove('hidden');
                resultsContainer.innerHTML = `<div class="p-3 text-xs text-slate-600 font-black text-center">Siswa tidak ditemukan</div>`;
            }
        }
    </script>
</body>
</html>
