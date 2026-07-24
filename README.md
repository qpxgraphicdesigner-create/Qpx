<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>QPX Platform - منصة التعلم الاحترافية</title>
<script src="https://cdn.tailwindcss.com"></script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
<style>
  @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700;800;900&display=swap');
  
  :root {
    --primary: #6366f1;
    --primary-dark: #4f46e5;
    --secondary: #ec4899;
    --bg: #0f172a;
    --glass: rgba(30, 41, 59, 0.7);
  }
  
  * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
  
  body {
    font-family: 'Cairo', sans-serif;
    background: linear-gradient(135deg, #0f172a 0%, #1e1b4b 50%, #0f172a 100%);
    color: #e2e8f0;
    overflow-x: hidden;
    margin: 0;
    min-height: 100vh;
  }
  
  /* Enhanced Glassmorphism */
  .glass-panel {
    background: rgba(30, 41, 59, 0.6);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border: 1px solid rgba(255,255,255,0.1);
    box-shadow: 0 8px 32px rgba(0,0,0,0.3);
  }
  
  .glass-card {
    background: rgba(30, 41, 59, 0.5);
    backdrop-filter: blur(16px);
    border: 1px solid rgba(255,255,255,0.08);
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  }
  
  .glass-card:hover {
    background: rgba(30, 41, 59, 0.7);
    border-color: rgba(99, 102, 241, 0.3);
    transform: translateY(-4px);
    box-shadow: 0 20px 40px rgba(99, 102, 241, 0.15);
  }
  
  /* Gradient Text */
  .gradient-text {
    background: linear-gradient(135deg, #818cf8 0%, #c084fc 50%, #ec4899 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  
  /* Animations */
  .fade-in { animation: fadeIn 0.5s cubic-bezier(0.4, 0, 0.2, 1); }
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  
  .slide-up { animation: slideUp 0.6s cubic-bezier(0.4, 0, 0.2, 1); }
  @keyframes slideUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }
  
  /* Custom Scrollbar */
  ::-webkit-scrollbar { width: 8px; height: 8px; }
  ::-webkit-scrollbar-track { background: rgba(15, 23, 42, 0.5); }
  ::-webkit-scrollbar-thumb { 
    background: linear-gradient(135deg, #6366f1, #ec4899);
    border-radius: 10px;
  }
  
  /* Video Player */
  .video-wrapper {
    position: relative;
    width: 100%;
    aspect-ratio: 16/9;
    background: #000;
    border-radius: 1.5rem;
    overflow: hidden;
    box-shadow: 0 25px 50px -12px rgba(99, 102, 241, 0.25);
  }
  
  .video-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(0,0,0,0.7), rgba(99, 102, 241, 0.3));
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.3s;
    z-index: 10;
  }
  
  .video-overlay:hover {
    background: linear-gradient(135deg, rgba(0,0,0,0.5), rgba(99, 102, 241, 0.4));
  }
  
  .play-btn {
    width: 100px;
    height: 100px;
    background: linear-gradient(135deg, #6366f1, #ec4899);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 0 50px rgba(99, 102, 241, 0.6);
    transition: transform 0.3s;
    animation: pulse 2s infinite;
  }
  
  @keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.05); }
  }
  
  .video-overlay:hover .play-btn {
    transform: scale(1.1);
  }
  
  .watermark {
    position: absolute;
    color: rgba(255,255,255,0.08);
    font-weight: 900;
    pointer-events: none;
    animation: moveWM 20s infinite linear;
    white-space: nowrap;
    font-size: 1.2rem;
    z-index: 5;
  }
  
  @keyframes moveWM {
    0% { transform: translate(0, 0) rotate(-15deg); }
    50% { transform: translate(50px, 50px) rotate(-15deg); }
    100% { transform: translate(0, 0) rotate(-15deg); }
  }
  
  /* Navigation */
  .nav-item {
    transition: all 0.3s ease;
    position: relative;
    border-radius: 1rem;
  }
  
  .nav-item.active {
    background: linear-gradient(135deg, rgba(99, 102, 241, 0.2), rgba(236, 72, 153, 0.2));
    color: #818cf8;
    border: 1px solid rgba(99, 102, 241, 0.3);
  }
  
  .nav-item:hover:not(.active) {
    background: rgba(255,255,255,0.05);
    color: #fff;
    transform: translateX(-5px);
  }
  
  /* Buttons */
  .btn-primary {
    background: linear-gradient(135deg, #6366f1, #ec4899);
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }
  
  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 15px 35px -5px rgba(99, 102, 241, 0.5);
  }
  
  .btn-primary::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
    transition: left 0.5s;
  }
  
  .btn-primary:hover::before {
    left: 100%;
  }
  
  .btn-danger {
    background: linear-gradient(135deg, #ef4444, #dc2626);
    transition: all 0.3s;
  }
  
  .btn-danger:hover {
    transform: translateY(-1px);
    box-shadow: 0 10px 25px -5px rgba(239, 68, 68, 0.4);
  }
  
  /* Course Cards */
  .course-card {
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    position: relative;
    overflow: hidden;
  }
  
  .course-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, #6366f1, #ec4899);
    transform: scaleX(0);
    transform-origin: right;
    transition: transform 0.4s;
  }
  
  .course-card:hover::before {
    transform: scaleX(1);
    transform-origin: left;
  }
  
  .course-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 25px 50px -12px rgba(99, 102, 241, 0.25);
  }
  
  /* Modal */
  .modal-bg {
    background: rgba(0,0,0,0.85);
    backdrop-filter: blur(12px);
  }
  
  input, textarea, select {
    direction: rtl;
  }
  
  .badge-active {
    background: linear-gradient(135deg, rgba(34,197,94,0.2), rgba(34,197,94,0.1));
    color: #4ade80;
    border: 1px solid rgba(34,197,94,0.3);
  }
  
  .badge-suspended {
    background: linear-gradient(135deg, rgba(239,68,68,0.2), rgba(239,68,68,0.1));
    color: #f87171;
    border: 1px solid rgba(239,68,68,0.3);
  }
  
  /* Teacher Section */
  .teacher-section {
    background: linear-gradient(135deg, rgba(99, 102, 241, 0.1), rgba(236, 72, 153, 0.05));
    border: 1px solid rgba(99, 102, 241, 0.2);
    border-radius: 2rem;
    padding: 2rem;
    margin-bottom: 2rem;
  }
  
  /* Exam Options */
  .exam-option {
    transition: all 0.3s;
    cursor: pointer;
  }
  
  .exam-option:hover {
    background: rgba(99, 102, 241, 0.2);
    border-color: #6366f1;
    transform: translateX(-5px);
  }
  
  .exam-option.selected {
    background: rgba(99, 102, 241, 0.3);
    border-color: #818cf8;
  }
  
  .exam-option.correct {
    background: rgba(34,197,94,0.2);
    border-color: #22c55e;
  }
  
  .exam-option.wrong {
    background: rgba(239,68,68,0.2);
    border-color: #ef4444;
  }
</style>
</head>
<body class="min-h-screen flex flex-col">

<!-- ============ LOGIN SCREEN ============ -->
<div id="loginScreen" class="flex-1 flex items-center justify-center p-4 relative min-h-screen">
  <!-- Animated Background -->
  <div class="absolute inset-0 overflow-hidden">
    <div class="absolute w-[600px] h-[600px] bg-indigo-600/20 rounded-full blur-3xl top-[-200px] left-[-200px] animate-pulse"></div>
    <div class="absolute w-[600px] h-[600px] bg-pink-600/20 rounded-full blur-3xl bottom-[-200px] right-[-200px] animate-pulse" style="animation-delay: 1s;"></div>
    <div class="absolute w-[400px] h-[400px] bg-purple-600/15 rounded-full blur-3xl top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 animate-pulse" style="animation-delay: 2s;"></div>
  </div>

  <div class="glass-panel w-full max-w-md rounded-3xl p-8 fade-in relative z-10 border border-white/10">
    <!-- Logo -->
    <div class="text-center mb-8">
      <div class="w-24 h-24 mx-auto mb-4 relative">
        <img src="https://image.qwenlm.ai/public_source/e40baaad-0a04-46cc-ac1f-8f323211659f/12ddb90ed-a860-4fee-ad69-729901238973.png" 
             alt="QPX Platform Logo" 
             class="w-full h-full object-contain drop-shadow-2xl">
      </div>
      <h1 class="text-4xl font-black gradient-text tracking-tight mb-2">QPX Platform</h1>
      <p class="text-gray-400 text-sm font-medium">منصة التعلم الاحترافية المتكاملة</p>
    </div>
    
    <!-- Role Selector -->
    <div class="flex bg-slate-800/80 p-1.5 rounded-2xl mb-6 border border-white/5">
      <button onclick="setRole('student')" class="role-tab flex-1 py-3 text-sm font-bold rounded-xl transition text-white bg-gradient-to-r from-indigo-600 to-pink-600 shadow-lg" data-role="student">
        <i class="fas fa-user-graduate ml-1"></i> طالب
      </button>
      <button onclick="setRole('teacher')" class="role-tab flex-1 py-3 text-sm font-bold rounded-xl transition text-gray-400 hover:text-white" data-role="teacher">
        <i class="fas fa-chalkboard-teacher ml-1"></i> مدرس
      </button>
      <button onclick="setRole('admin')" class="role-tab flex-1 py-3 text-sm font-bold rounded-xl transition text-gray-400 hover:text-white" data-role="admin">
        <i class="fas fa-user-shield ml-1"></i> مدير
      </button>
    </div>

    <!-- Login Form -->
    <form onsubmit="handleLogin(event)" class="space-y-4">
      <div class="relative">
        <i class="fas fa-user absolute right-4 top-1/2 -translate-y-1/2 text-gray-500"></i>
        <input type="text" id="loginUser" placeholder="اسم المستخدم / المعرف" 
               class="w-full bg-slate-900/80 border border-slate-700 rounded-xl pr-12 pl-4 py-4 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-500/50 outline-none transition text-sm font-medium text-white" required>
      </div>
      <div class="relative">
        <i class="fas fa-lock absolute right-4 top-1/2 -translate-y-1/2 text-gray-500"></i>
        <input type="password" id="loginPass" placeholder="كلمة المرور" 
               class="w-full bg-slate-900/80 border border-slate-700 rounded-xl pr-12 pl-4 py-4 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-500/50 outline-none transition text-sm font-medium text-white" required>
      </div>
      <button type="submit" class="w-full btn-primary text-white font-bold py-4 rounded-xl shadow-lg text-base mt-2">
        <i class="fas fa-sign-in-alt ml-2"></i> تسجيل الدخول الآمن
      </button>
    </form>
    
    <div id="loginMsg" class="mt-4 text-center text-sm text-red-400 font-medium hidden bg-red-500/10 py-3 rounded-xl border border-red-500/20"></div>
    
    <div class="mt-6 text-center">
      <p class="text-xs text-gray-500 bg-slate-800/50 p-3 rounded-lg">
        <i class="fas fa-info-circle ml-1"></i>
        للتجربة: طالب (S1 / s123) | مدرس (T1 / t123) | مدير (admin / admin123)
      </p>
    </div>
  </div>
</div>

<!-- ============ MAIN APP ============ -->
<div id="mainApp" class="hidden flex-1 flex flex-col md:flex-row h-screen overflow-hidden">
  
  <!-- Sidebar Navigation -->
  <nav class="glass-panel md:w-72 w-full h-16 md:h-full fixed bottom-0 md:relative z-40 flex md:flex-col justify-around md:justify-start md:p-4 order-2 md:order-1 border-l border-white/5">
    <!-- Logo Section -->
    <div class="hidden md:flex items-center gap-3 px-4 py-6 border-b border-white/10 mb-6">
      <div class="w-12 h-12 rounded-xl overflow-hidden shadow-lg">
        <img src="https://image.qwenlm.ai/public_source/e40baaad-0a04-46cc-ac1f-8f323211659f/12ddb90ed-a860-4fee-ad69-729901238973.png" 
             alt="Logo" class="w-full h-full object-contain">
      </div>
      <div>
        <span class="font-black text-white text-xl tracking-wide block">QPX</span>
        <span class="text-[10px] text-gray-400 font-medium">منصة التعلم</span>
      </div>
    </div>
    
    <!-- Nav Items -->
    <div class="flex md:flex-col w-full justify-around md:justify-start md:space-y-2 overflow-x-auto md:overflow-visible px-2 md:px-0" id="navItems">
      <!-- Injected by JS -->
    </div>
    
    <!-- Logout -->
    <div class="hidden md:block mt-auto pt-6 border-t border-white/10 px-2">
      <button onclick="logout()" class="w-full flex items-center gap-3 px-4 py-3 text-red-400 hover:bg-red-500/10 rounded-xl transition group">
        <i class="fas fa-sign-out-alt group-hover:-translate-x-1 transition-transform"></i> 
        <span class="font-bold text-sm">تسجيل الخروج</span>
      </button>
    </div>
  </nav>

  <!-- Main Content -->
  <main class="flex-1 overflow-y-auto p-4 md:p-8 pb-24 md:pb-8 order-1 md:order-2 relative scroll-smooth">
    <header class="flex justify-between items-center mb-8 sticky top-0 bg-slate-950/80 backdrop-blur-xl z-30 py-4 -mx-4 md:-mx-8 px-4 md:px-8 border-b border-white/5">
      <div>
        <h2 id="pageTitle" class="text-2xl md:text-3xl font-black text-white">الرئيسية</h2>
        <p id="pageSubtitle" class="text-sm text-gray-400 mt-1">أهلاً بعودتك</p>
      </div>
      <div class="flex items-center gap-4">
        <button onclick="navigate('profile')" class="flex items-center gap-3 glass-panel pl-4 pr-2 py-2 rounded-full hover:bg-white/5 transition group border border-white/10">
          <img id="headerAvatar" src="" class="w-10 h-10 rounded-full border-2 border-indigo-500 object-cover bg-slate-800">
          <div class="hidden md:block text-right">
            <p id="headerName" class="text-sm font-bold text-white group-hover:text-indigo-400 transition">User</p>
            <p id="headerRole" class="text-[10px] text-gray-400">Role</p>
          </div>
        </button>
      </div>
    </header>
    
    <div id="contentArea" class="fade-in min-h-[60vh]"></div>
  </main>
</div>

<!-- ============ VIDEO PLAYER MODAL ============ -->
<div id="videoModal" class="fixed inset-0 bg-black z-[100] hidden flex flex-col">
  <div class="p-4 flex justify-between items-center bg-slate-900 border-b border-white/10">
    <div class="flex items-center gap-3">
      <button onclick="closeVideo()" class="w-10 h-10 rounded-full bg-slate-800 flex items-center justify-center text-gray-400 hover:text-white hover:bg-slate-700 transition">
        <i class="fas fa-arrow-right"></i>
      </button>
      <h3 class="font-bold text-white text-lg" id="vidTitle">عنوان الدرس</h3>
    </div>
    <div class="flex gap-2">
      <button onclick="shareLesson()" class="w-10 h-10 rounded-full bg-indigo-600/20 text-indigo-400 flex items-center justify-center hover:bg-indigo-600 hover:text-white transition" title="مشاركة">
        <i class="fas fa-share-alt"></i>
      </button>
      <button onclick="closeVideo()" class="w-10 h-10 rounded-full bg-red-500/20 text-red-400 flex items-center justify-center hover:bg-red-500 hover:text-white transition" title="إغلاق">
        <i class="fas fa-times"></i>
      </button>
    </div>
  </div>
  
  <div class="flex-1 overflow-y-auto bg-slate-950 p-4 md:p-8">
    <div class="max-w-6xl mx-auto space-y-6">
      <!-- Video Container -->
      <div class="video-wrapper border border-white/10" id="vidContainer">
        <div class="video-overlay" id="videoOverlay" onclick="activateVideo()">
          <div class="play-btn">
            <i class="fas fa-play text-white text-4xl mr-1"></i>
          </div>
          <p class="text-white font-bold mt-6 text-xl">اضغط لبدء تشغيل الحصة</p>
          <p class="text-gray-300 text-sm mt-2">يدعم الوضع الأفقي وملء الشاشة</p>
        </div>
        <div id="wmLayer" class="absolute inset-0 pointer-events-none overflow-hidden"></div>
        <iframe id="videoFrame" class="w-full h-full absolute inset-0 hidden" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        
        <button onclick="toggleFullscreen()" class="absolute bottom-6 left-6 z-20 bg-black/60 hover:bg-indigo-600 text-white px-6 py-3 rounded-xl backdrop-blur-sm transition flex items-center gap-2 border border-white/10 font-bold">
          <i class="fas fa-expand"></i> <span>ملء الشاشة</span>
        </button>
      </div>

      <!-- Lesson Details -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
        <!-- Notes -->
        <div class="lg:col-span-2 glass-panel rounded-2xl p-6 border border-white/10">
          <div class="flex items-center gap-3 mb-4">
            <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-yellow-500 to-orange-500 flex items-center justify-center text-white shadow-lg">
              <i class="fas fa-book-open text-xl"></i>
            </div>
            <h3 class="font-bold text-xl text-white">ملزمة وملاحظات الحصة</h3>
          </div>
          <div id="lessonNotesContent" class="prose prose-invert max-w-none text-gray-300 leading-relaxed bg-slate-900/50 p-6 rounded-xl border border-white/5">
          </div>
          <button class="mt-4 w-full py-4 bg-gradient-to-r from-indigo-600 to-pink-600 hover:from-indigo-700 hover:to-pink-700 text-white rounded-xl transition flex items-center justify-center gap-2 font-bold shadow-lg">
            <i class="fas fa-download"></i> تحميل الملزمة كملف PDF
          </button>
        </div>

        <!-- Exam -->
        <div class="glass-panel rounded-2xl p-6 border border-white/10 flex flex-col">
          <div class="flex items-center gap-3 mb-4">
            <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-green-500 to-emerald-500 flex items-center justify-center text-white shadow-lg">
              <i class="fas fa-clipboard-check text-xl"></i>
            </div>
            <h3 class="font-bold text-xl text-white">اختبار الحصة</h3>
          </div>
          <div id="lessonExamContent" class="flex-1 flex flex-col items-center justify-center text-center py-4">
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ============ GENERIC MODAL ============ -->
<div id="genericModal" class="fixed inset-0 modal-bg z-[90] hidden flex items-center justify-center p-4">
  <div class="glass-panel w-full max-w-lg rounded-2xl p-6 max-h-[90vh] overflow-y-auto fade-in border border-white/10" id="modalContent"></div>
</div>

<script>
// ==========================================
// DATABASE (Updated for Multiple Teachers)
// ==========================================
const defaultDB = {
  admins: [{ 
    id: 'admin', 
    pass: 'admin123', 
    name: 'المدير العام', 
    avatar: 'https://ui-avatars.com/api/?name=Admin&background=6366f1&color=fff' 
  }],
  teachers: [
    { 
      id: 'T1', 
      pass: 't123', 
      name: 'م. أحمد الفيزياء', 
      phone: '01012345678', 
      code: 'PHY-2026', 
      active: true, 
      avatar: 'https://ui-avatars.com/api/?name=Ahmed&background=10b981&color=fff' 
    },
    { 
      id: 'T2', 
      pass: 't456', 
      name: 'أ. سارة الإنجليزي', 
      phone: '01098765432', 
      code: 'ENG-2026', 
      active: true, 
      avatar: 'https://ui-avatars.com/api/?name=Sarah&background=ec4899&color=fff' 
    }
  ],
  students: [
    { 
      id: 'S1', 
      pass: 's123', 
      name: 'علي حسن', 
      teacherIds: ['T1', 'T2'], // Multiple teachers!
      active: true, 
      courses: { 'C1': true, 'C2': false, 'C3': true },
      avatar: 'https://ui-avatars.com/api/?name=Ali&background=f59e0b&color=fff' 
    },
    { 
      id: 'S2', 
      pass: 's789', 
      name: 'منى سعيد', 
      teacherIds: ['T2'], 
      active: true, 
      courses: { 'C3': true },
      avatar: 'https://ui-avatars.com/api/?name=Mona&background=8b5cf6&color=fff' 
    }
  ],
  courses: [
    { 
      id: 'C1', 
      title: 'الفيزياء الحديثة', 
      teacherId: 'T1', 
      lessons: [
        {
          id: 'L1', 
          title: 'الحصة الأولى: مقدمة في الفيزياء الحديثة', 
          duration: '45:00', 
          url: 'https://www.youtube.com/embed/dQw4w9WgXcQ', 
          notes: 'في هذه الحصة سنتعرف على أساسيات الفيزياء الحديثة، نظرية النسبية، ومفاهيم الكم الأولى. يرجى مراجعة الفصل الأول من الكتاب المدرسي.'
        },
        {
          id: 'L2', 
          title: 'الحصة الثانية: الحركة والميكانيكا', 
          duration: '52:30', 
          url: 'https://www.youtube.com/embed/dQw4w9WgXcQ', 
          notes: 'شرح مفصل لقوانين نيوتن للحركة مع أمثلة تطبيقية محلولة.'
        }
      ]
    },
    { 
      id: 'C2', 
      title: 'ميكانيكا الكم المتقدمة', 
      teacherId: 'T1', 
      lessons: [] 
    },
    { 
      id: 'C3', 
      title: 'English Grammar Master', 
      teacherId: 'T2', 
      lessons: [
        {
          id: 'L3', 
          title: 'Lesson 1: Advanced Tenses', 
          duration: '38:00', 
          url: 'https://www.youtube.com/embed/dQw4w9WgXcQ', 
          notes: 'Focus on Present Perfect and Past Perfect usage with practical examples.'
        }
      ]
    }
  ],
  exams: [
    { 
      id: 'E1', 
      courseId: 'C1', 
      lessonId: 'L1', 
      title: 'اختبار الحصة الأولى', 
      active: true, 
      questions: [
        { q: 'ما هي وحدة قياس القوة في النظام الدولي؟', options: ['نيوتن','جول','واط','أمبير'], correct: 0 },
        { q: 'سرعة الضوء في الفراغ تساوي تقريباً:', options: ['3×10 م/ث','3×10⁸ م/ث','3×10¹⁰ م/ث','3×10⁴ م/ث'], correct: 1 },
        { q: 'من هو العالم الذي صاغ قانون الجاذبية الكونية؟', options: ['أينشتاين','نيوتن','جاليليو','كوبرنيكوس'], correct: 1 }
      ]
    }
  ],
  pendingTeachers: []
};

let DB = JSON.parse(localStorage.getItem('qpx_db')) || defaultDB;
function saveDB() { localStorage.setItem('qpx_db', JSON.stringify(DB)); }

let currentUser = null;
let currentRole = 'student';
let currentLessonId = null;

// ==========================================
// AUTHENTICATION
// ==========================================
function setRole(role) {
  currentRole = role;
  document.querySelectorAll('.role-tab').forEach(btn => {
    if(btn.dataset.role === role) {
      btn.className = "role-tab flex-1 py-3 text-sm font-bold rounded-xl transition text-white bg-gradient-to-r from-indigo-600 to-pink-600 shadow-lg";
    } else {
      btn.className = "role-tab flex-1 py-3 text-sm font-bold rounded-xl transition text-gray-400 hover:text-white hover:bg-white/5";
    }
  });
}

function handleLogin(e) {
  e.preventDefault();
  const u = document.getElementById('loginUser').value.trim();
  const p = document.getElementById('loginPass').value.trim();
  const msg = document.getElementById('loginMsg');
  let user = null;

  if (currentRole === 'admin' && u === DB.admins[0].id && p === DB.admins[0].pass) {
    user = {...DB.admins[0], role:'admin'};
  } else if (currentRole === 'teacher') { 
    const t = DB.teachers.find(x => x.id === u && x.pass === p); 
    if(t && !t.active) { showLoginError("حسابك موقوف حالياً. يرجى التواصل مع الإدارة."); return; } 
    user = t ? {...t, role:'teacher'} : null; 
  } else if (currentRole === 'student') { 
    const s = DB.students.find(x => x.id === u && x.pass === p); 
    if(s && !s.active) { showLoginError("حسابك موقوف. يرجى سداد الاشتراك أو التواصل مع الإدارة."); return; } 
    user = s ? {...s, role:'student'} : null; 
  }

  if (user) {
    currentUser = user;
    document.getElementById('loginScreen').classList.add('hidden');
    document.getElementById('mainApp').classList.remove('hidden');
    updateHeader();
    initApp();
  } else { showLoginError("بيانات الدخول غير صحيحة، تأكد من المعرف وكلمة المرور"); }
}

function showLoginError(txt) {
  const msg = document.getElementById('loginMsg');
  msg.textContent = txt;
  msg.classList.remove('hidden');
  setTimeout(() => msg.classList.add('hidden'), 4000);
}

function logout() { 
  currentUser = null;
  document.getElementById('mainApp').classList.add('hidden');
  document.getElementById('loginScreen').classList.remove('hidden');
  document.getElementById('loginUser').value = '';
  document.getElementById('loginPass').value = '';
}

function updateHeader() {
  document.getElementById('headerName').textContent = currentUser.name;
  document.getElementById('headerRole').textContent = currentUser.role === 'admin' ? 'مدير النظام' : (currentUser.role === 'teacher' ? 'مدرس' : 'طالب');
  document.getElementById('headerAvatar').src = currentUser.avatar || `https://ui-avatars.com/api/?name=${currentUser.name}&background=6366f1&color=fff`;
}

// ==========================================
// NAVIGATION
// ==========================================
function initApp() { renderNav(); navigate('dashboard'); }

function renderNav() {
  const nav = document.getElementById('navItems');
  let items = [];
  
  if (currentUser.role === 'student') {
    items = [
      {id:'dashboard', icon:'fa-home', label:'كورساتي'},
      {id:'exams', icon:'fa-clipboard-check', label:'امتحاناتي'},
      {id:'profile', icon:'fa-user-circle', label:'ملفي الشخصي'}
    ];
  } else if (currentUser.role === 'teacher') {
    items = [
      {id:'dashboard', icon:'fa-users', label:'طلابي'},
      {id:'courses', icon:'fa-book', label:'إدارة الكورسات'},
      {id:'exams', icon:'fa-clipboard-list', label:'الامتحانات'},
      {id:'profile', icon:'fa-user-circle', label:'ملفي الشخصي'}
    ];
  } else {
    items = [
      {id:'dashboard', icon:'fa-chart-pie', label:'لوحة القيادة'},
      {id:'teachers', icon:'fa-chalkboard-teacher', label:'المدرسين'},
      {id:'students', icon:'fa-users-cog', label:'الطلاب'},
      {id:'allcourses', icon:'fa-book-open', label:'كل الكورسات'}
    ];
  }

  nav.innerHTML = items.map(i => `
    <button onclick="navigate('${i.id}')" class="nav-item flex flex-col md:flex-row items-center md:gap-4 p-3 md:px-4 md:py-3.5 rounded-xl text-gray-400 w-full" data-target="${i.id}">
      <i class="fas ${i.icon} text-xl mb-1 md:mb-0"></i>
      <span class="text-[11px] md:text-sm font-bold">${i.label}</span>
    </button>
  `).join('');
}

function navigate(page) {
  document.querySelectorAll('.nav-item').forEach(b => b.classList.toggle('active', b.dataset.target === page));
  const c = document.getElementById('contentArea');
  const t = document.getElementById('pageTitle');
  const st = document.getElementById('pageSubtitle');
  
  c.className = 'fade-in';
  c.innerHTML = '<div class="flex justify-center py-20"><i class="fas fa-circle-notch fa-spin text-3xl text-indigo-500"></i></div>';

  setTimeout(() => {
    const routes = {
      student: { 
        dashboard: ['كورساتي', 'جميع الكورسات من مدرسيك', renderStudentDashboard], 
        exams: ['الامتحانات المتاحة', 'أدّ الامتحانات وحصل على درجاتك', renderStudentExams], 
        profile: ['الملف الشخصي', 'تحديث بياناتك وصورتك الشخصية', renderProfile] 
      },
      teacher: { 
        dashboard: ['إدارة الطلاب', 'مراقبة تقدم طلابك وتفعيل الكورسات', renderTeacherStudents], 
        courses: ['كورساتي', 'إضافة الحصص والملاحظات', renderTeacherCourses], 
        exams: ['إدارة الامتحانات', 'إنشاء وتفعيل الاختبارات', renderTeacherExams],
        profile: ['الملف الشخصي', 'تحديث بياناتك وصورتك الشخصية', renderProfile]
      },
      admin: { 
        dashboard: ['لوحة القيادة', 'إحصائيات المنصة الشاملة', renderAdminDash], 
        teachers: ['إدارة المدرسين', 'إضافة وتفعيل حسابات المدرسين', renderAdminTeachers], 
        students: ['مراقبة الطلاب', 'إدارة حسابات الطلاب', renderAdminStudents], 
        allcourses: ['جميع الكورسات', 'محتوى المنصة التعليمي', renderAdminAllCourses] 
      }
    };

    const route = routes[currentUser.role]?.[page] || routes[currentUser.role]['dashboard'];
    t.textContent = route[0];
    st.textContent = route[1];
    route[2](c);
  }, 150);
}

// ==========================================
// STUDENT VIEWS (Updated for Multiple Teachers)
// ==========================================
function renderStudentDashboard(c) {
  const myTeacherIds = currentUser.teacherIds || [];
  const myTeachers = DB.teachers.filter(t => myTeacherIds.includes(t.id));
  
  if (myTeachers.length === 0) {
    c.innerHTML = `<div class="glass-panel p-10 rounded-3xl text-center"><i class="fas fa-user-clock text-5xl text-gray-600 mb-4"></i><h3 class="text-xl font-bold text-white">لم يتم تعيين أي مدرس لك بعد</h3><p class="text-gray-400 mt-2">يرجى التواصل مع الإدارة لتعيين مدرسيك وبدء رحلتك التعليمية.</p></div>`;
    return;
  }

  let html = '';
  
  myTeachers.forEach(teacher => {
    const teacherCourses = DB.courses.filter(cr => cr.teacherId === teacher.id);
    const activeCourses = teacherCourses.filter(cr => currentUser.courses[cr.id]);
    
    html += `
      <div class="teacher-section slide-up">
        <!-- Teacher Header -->
        <div class="flex flex-col md:flex-row items-center gap-6 mb-8 pb-6 border-b border-white/10">
          <img src="${teacher.avatar}" class="w-20 h-20 rounded-2xl border-2 border-indigo-500 object-cover shadow-lg">
          <div class="text-center md:text-right flex-1">
            <h3 class="font-black text-2xl text-white mb-1">${teacher.name}</h3>
            <p class="text-indigo-300 font-medium">كود المادة: <span class="font-mono bg-indigo-500/20 px-2 py-0.5 rounded text-indigo-300">${teacher.code}</span></p>
          </div>
          <div class="flex gap-3">
            <div class="text-center px-4 py-2 bg-slate-800/50 rounded-xl border border-white/5">
              <p class="text-2xl font-black text-white">${teacherCourses.length}</p>
              <p class="text-xs text-gray-400">كورس متاح</p>
            </div>
            <div class="text-center px-4 py-2 bg-green-500/10 rounded-xl border border-green-500/20">
              <p class="text-2xl font-black text-green-400">${activeCourses.length}</p>
              <p class="text-xs text-gray-400">نشط</p>
            </div>
          </div>
        </div>

        <!-- Courses Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          ${teacherCourses.map(cr => {
            const isActive = currentUser.courses[cr.id];
            return `
            <div class="glass-card rounded-2xl overflow-hidden course-card border border-white/5 ${!isActive ? 'opacity-70 grayscale-[0.5]' : ''}">
              <div class="h-32 bg-gradient-to-br from-indigo-600/20 to-pink-600/20 relative flex items-center justify-center border-b border-white/5">
                <i class="fas ${isActive ? 'fa-infinity' : 'fa-lock'} text-5xl ${isActive ? 'text-indigo-500/50' : 'text-gray-700'}"></i>
                <span class="absolute top-4 left-4 text-[10px] font-bold px-3 py-1 rounded-full ${isActive ? 'badge-active' : 'badge-suspended'}">
                  ${isActive ? 'مشترك ونشط' : 'الاشتراك معلق'}
                </span>
              </div>
              <div class="p-6">
                <h3 class="font-black text-lg text-white mb-1">${cr.title}</h3>
                <p class="text-xs text-gray-400 mb-4 flex items-center gap-2"><i class="fas fa-layer-group"></i> ${cr.lessons.length} حصة مسجلة</p>
                
                ${isActive ? `
                  <div class="space-y-3">
                    ${cr.lessons.length > 0 ? cr.lessons.map(l => `
                      <div onclick="openLessonPlayer('${cr.id}', '${l.id}')" class="group flex items-center justify-between p-3 bg-slate-800/40 rounded-xl cursor-pointer hover:bg-indigo-600/20 hover:border-indigo-500/30 border border-transparent transition-all">
                        <div class="flex items-center gap-3">
                          <div class="w-8 h-8 rounded-lg bg-indigo-500/20 flex items-center justify-center text-indigo-400 group-hover:bg-indigo-500 group-hover:text-white transition"><i class="fas fa-play text-xs"></i></div>
                          <div>
                            <span class="text-sm font-bold text-gray-200 group-hover:text-white block">${l.title}</span>
                            <span class="text-[10px] text-gray-500"><i class="far fa-clock ml-1"></i>${l.duration}</span>
                          </div>
                        </div>
                        <i class="fas fa-chevron-left text-xs text-gray-600 group-hover:text-indigo-400 transition"></i>
                      </div>
                    `).join('') : '<p class="text-sm text-gray-500 text-center py-4">لم يتم إضافة حصص بعد</p>'}
                  </div>
                ` : `
                  <div class="mt-2 p-4 bg-red-500/10 border border-red-500/20 rounded-xl text-center">
                    <p class="text-sm font-bold text-red-400"><i class="fas fa-exclamation-circle ml-1"></i> الكورس معلق حتى إتمام سداد الاشتراك</p>
                  </div>
                `}
              </div>
            </div>`;
          }).join('')}
        </div>
      </div>
    `;
  });

  c.innerHTML = html;
}

function openLessonPlayer(courseId, lessonId) {
  const course = DB.courses.find(c => c.id === courseId);
  const lesson = course.lessons.find(l => l.id === lessonId);
  currentLessonId = lessonId;
  
  document.getElementById('vidTitle').textContent = lesson.title;
  document.getElementById('videoModal').classList.remove('hidden');
  document.body.style.overflow = 'hidden';
  
  document.getElementById('videoOverlay').classList.remove('hidden');
  document.getElementById('videoFrame').classList.add('hidden');
  document.getElementById('videoFrame').src = '';
  
  document.getElementById('lessonNotesContent').innerHTML = lesson.notes ? `<p>${lesson.notes}</p>` : '<p class="text-gray-500 italic">لا توجد ملاحظات مضافة لهذه الحصة.</p>';
  
  const exam = DB.exams.find(e => e.courseId === courseId && e.lessonId === lessonId && e.active);
  if (exam) {
    document.getElementById('lessonExamContent').innerHTML = `
      <div class="w-full">
        <p class="text-gray-300 mb-4 text-sm">اختبار قصير لقياس استيعابك للحصة</p>
        <button onclick="closeVideo(); setTimeout(()=>startExam('${exam.id}'), 300)" class="w-full btn-primary text-white font-bold py-3 rounded-xl flex items-center justify-center gap-2">
          <i class="fas fa-pen-alt"></i> بدء الاختبار الآن
        </button>
      </div>
    `;
  } else {
    document.getElementById('lessonExamContent').innerHTML = `<p class="text-gray-500 text-sm">لا يوجد اختبار مرفق بهذه الحصة حالياً.</p>`;
  }

  const wmLayer = document.getElementById('wmLayer');
  wmLayer.innerHTML = '';
  for(let i=0; i<6; i++){
    const wm = document.createElement('div');
    wm.className = 'watermark';
    wm.textContent = `${currentUser.name} - ${currentUser.id}`;
    wm.style.top = (10 + Math.random() * 80) + '%';
    wm.style.left = (10 + Math.random() * 80) + '%';
    wm.style.animationDelay = (Math.random() * 10) + 's';
    wmLayer.appendChild(wm);
  }
}

function activateVideo() {
  const frame = document.getElementById('videoFrame');
  const overlay = document.getElementById('videoOverlay');
  frame.src = frame.src || "https://www.youtube.com/embed/dQw4w9WgXcQ?autoplay=1&rel=0&modestbranding=1"; 
  overlay.classList.add('hidden');
  frame.classList.remove('hidden');
}

function toggleFullscreen() {
  const container = document.getElementById('vidContainer');
  if (!document.fullscreenElement) {
    container.requestFullscreen().catch(err => alert(`Error: ${err.message}`));
  } else {
    document.exitFullscreen();
  }
}

function shareLesson() {
  const title = document.getElementById('vidTitle').textContent;
  if (navigator.share) {
    navigator.share({ title: 'QPX Platform', text: `شاهد حصة: ${title}`, url: window.location.href });
  } else {
    navigator.clipboard.writeText(window.location.href);
    alert('تم نسخ رابط الحصة بنجاح!');
  }
}

function closeVideo() {
  document.getElementById('videoModal').classList.add('hidden');
  document.getElementById('videoFrame').src = '';
  document.body.style.overflow = 'auto';
}

function startExam(examId) {
  const exam = DB.exams.find(e => e.id === examId);
  const c = document.getElementById('contentArea');
  document.getElementById('pageTitle').textContent = exam.title;
  document.getElementById('pageSubtitle').textContent = 'أجب عن جميع الأسئلة بعناية';
  
  c.innerHTML = `
    <button onclick="navigate('dashboard')" class="mb-6 text-sm text-indigo-400 hover:text-white flex items-center gap-2 transition"><i class="fas fa-arrow-right"></i> عودة للكورسات</button>
    <div class="max-w-3xl mx-auto">
      <div class="glass-panel p-6 rounded-3xl mb-6 border border-indigo-500/20 bg-indigo-900/10">
        <h3 class="font-black text-xl text-white mb-2">${exam.title}</h3>
        <div class="flex items-center gap-4 text-sm text-gray-400">
          <span><i class="fas fa-question-circle ml-1"></i> ${exam.questions.length} أسئلة</span>
          <span><i class="fas fa-star ml-1 text-yellow-500"></i> درجة النجاح: 50%</span>
        </div>
      </div>
      <form id="examForm" onsubmit="submitExam(event, '${exam.id}')" class="space-y-6">
        ${exam.questions.map((q, qi) => `
          <div class="glass-panel p-6 rounded-2xl border border-white/5">
            <p class="font-bold text-lg mb-4 text-white"><span class="text-indigo-400 ml-2">${qi+1}.</span> ${q.q}</p>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
              ${q.options.map((opt, oi) => `
                <label class="exam-option flex items-center gap-3 p-4 rounded-xl border border-slate-700 bg-slate-800/30 cursor-pointer hover:bg-indigo-600/10 hover:border-indigo-500/50 transition-all">
                  <input type="radio" name="q${qi}" value="${oi}" required class="w-5 h-5 accent-indigo-500 cursor-pointer">
                  <span class="text-sm font-medium text-gray-200">${opt}</span>
                </label>
              `).join('')}
            </div>
          </div>
        `).join('')}
        <button type="submit" class="w-full btn-primary text-white font-black py-4 rounded-xl text-lg shadow-lg shadow-indigo-500/25 mt-8">تسليم الإجابات واعتماد النتيجة</button>
      </form>
    </div>
  `;
}

function submitExam(e, examId) {
  e.preventDefault();
  const exam = DB.exams.find(ex => ex.id === examId);
  let score = 0;
  const total = exam.questions.length;
  
  exam.questions.forEach((q, i) => {
    const selected = document.querySelector(`input[name="q${i}"]:checked`);
    if (selected && parseInt(selected.value) === q.correct) score++;
  });

  const percentage = Math.round((score/total)*100);
  const passed = percentage >= 50;
  
  const c = document.getElementById('contentArea');
  c.innerHTML = `
    <div class="max-w-md mx-auto glass-panel p-10 rounded-3xl text-center border border-white/10 mt-10">
      <div class="w-28 h-28 mx-auto rounded-full flex items-center justify-center text-5xl mb-6 ${passed ? 'bg-green-500/20 text-green-400' : 'bg-red-500/20 text-red-400'} animate-bounce">
        <i class="fas ${passed ? 'fa-trophy' : 'fa-redo'}"></i>
      </div>
      <h2 class="text-3xl font-black text-white mb-2">${passed ? 'مبروك! نتيجة ممتازة' : 'حاول مرة أخرى'}</h2>
      <div class="text-6xl font-black ${passed ? 'text-green-400' : 'text-red-400'} mb-4">${percentage}%</div>
      <p class="text-gray-400 mb-8 text-lg">أجبت بشكل صحيح على ${score} من ${total} أسئلة</p>
      <button onclick="navigate('dashboard')" class="btn-primary text-white px-10 py-3.5 rounded-xl font-bold text-lg w-full">العودة للكورسات</button>
    </div>
  `;
}

function renderStudentExams(c) {
  const myCourseIds = Object.keys(currentUser.courses).filter(k => currentUser.courses[k]);
  const availableExams = DB.exams.filter(ex => myCourseIds.includes(ex.courseId) && ex.active);
  
  if (availableExams.length === 0) {
    c.innerHTML = `<div class="glass-panel p-16 rounded-3xl text-center border border-white/5"><i class="fas fa-hourglass-half text-5xl text-yellow-500/50 mb-4"></i><h3 class="text-xl font-bold text-white">لا توجد امتحانات نشطة حالياً</h3><p class="text-gray-400 mt-2">تابع الكورسات وسيتم إشعارك عند توفر امتحان جديد.</p></div>`;
    return;
  }
  
  c.innerHTML = `
    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      ${availableExams.map(ex => {
        const course = DB.courses.find(cr => cr.id === ex.courseId);
        return `
        <div onclick="startExam('${ex.id}')" class="glass-card p-6 rounded-2xl cursor-pointer border-r-4 border-yellow-500 group">
          <div class="flex items-center gap-4 mb-3">
            <div class="w-12 h-12 rounded-xl bg-yellow-500/10 flex items-center justify-center text-yellow-400 group-hover:scale-110 transition"><i class="fas fa-clipboard-check text-xl"></i></div>
            <div>
              <h3 class="font-bold text-lg text-white">${ex.title}</h3>
              <p class="text-xs text-gray-400">المادة: ${course?.title || 'غير محدد'}</p>
            </div>
          </div>
          <div class="flex items-center justify-between mt-4 pt-4 border-t border-white/5">
            <span class="text-xs font-bold text-gray-400"><i class="fas fa-question-circle ml-1"></i> ${ex.questions.length} سؤال</span>
            <span class="text-xs font-bold text-indigo-400 group-hover:translate-x-[-5px] transition">ابدأ الآن <i class="fas fa-arrow-left mr-1"></i></span>
          </div>
        </div>`;
      }).join('')}
    </div>
  `;
}

// ==========================================
// PROFILE VIEW
// ==========================================
function renderProfile(c) {
  const isTeacher = currentUser.role === 'teacher';
  const extraInfo = isTeacher ? `<p class="text-sm text-gray-400">كود المادة: <span class="text-white font-mono bg-slate-800 px-2 py-0.5 rounded">${currentUser.code}</span></p>` : 
                   (currentUser.role === 'student' ? `<p class="text-sm text-gray-400">المدرسين المشتركين معهم: <span class="text-white">${(currentUser.teacherIds || []).length} مدرس</span></p>` : '');

  c.innerHTML = `
    <div class="max-w-2xl mx-auto">
      <div class="glass-panel p-8 rounded-3xl text-center border border-white/10 relative overflow-hidden">
        <div class="absolute top-0 left-0 w-full h-32 bg-gradient-to-r from-indigo-600 to-pink-600 opacity-50"></div>
        
        <div class="relative z-10 mt-12 mb-6">
          <div class="relative inline-block group">
            <img id="profileAvatarImg" src="${currentUser.avatar}" class="w-32 h-32 rounded-full border-4 border-slate-900 object-cover shadow-2xl bg-slate-800">
            <label class="absolute bottom-1 right-1 w-10 h-10 bg-indigo-600 rounded-full flex items-center justify-center text-white cursor-pointer hover:bg-indigo-500 transition shadow-lg border-2 border-slate-900" title="تغيير الصورة">
              <i class="fas fa-camera text-sm"></i>
              <input type="file" accept="image/*" class="hidden" onchange="handleAvatarUpload(this)">
            </label>
          </div>
        </div>
        
        <h2 class="text-3xl font-black text-white mb-2">${currentUser.name}</h2>
        <p class="text-indigo-400 font-mono text-sm bg-indigo-500/10 inline-block px-4 py-1.5 rounded-full border border-indigo-500/20 mb-6">ID: ${currentUser.id}</p>
        
        <div class="text-right space-y-4 max-w-sm mx-auto bg-slate-900/50 p-6 rounded-2xl border border-white/5">
          ${extraInfo}
          <p class="text-sm text-gray-400">نوع الحساب: <span class="text-white font-bold">${currentUser.role === 'admin' ? 'مدير النظام' : (currentUser.role === 'teacher' ? 'مدرس' : 'طالب')}</span></p>
          <p class="text-sm text-gray-400">حالة الحساب: <span class="text-green-400 font-bold flex items-center gap-2"><span class="w-2 h-2 bg-green-400 rounded-full animate-pulse"></span> نشط</span></p>
        </div>
      </div>
    </div>
  `;
}

function handleAvatarUpload(input) {
  if (input.files && input.files[0]) {
    const reader = new FileReader();
    reader.onload = function(e) {
      const base64Img = e.target.result;
      const rolePlural = currentUser.role === 'admin' ? 'admins' : (currentUser.role + 's');
      const userInDb = DB[rolePlural].find(u => u.id === currentUser.id);
      if (userInDb) {
        userInDb.avatar = base64Img;
        currentUser.avatar = base64Img;
        saveDB();
        updateHeader();
        document.getElementById('profileAvatarImg').src = base64Img;
        const label = input.parentElement;
        label.classList.add('bg-green-500');
        setTimeout(() => label.classList.remove('bg-green-500'), 1000);
      }
    };
    reader.readAsDataURL(input.files[0]);
  }
}

// ==========================================
// TEACHER VIEWS (Updated for Multiple Teachers)
// ==========================================
function renderTeacherStudents(c) {
  // Find students who have courses from this teacher
  const myCourseIds = DB.courses.filter(cr => cr.teacherId === currentUser.id).map(cr => cr.id);
  const myStudents = DB.students.filter(s => 
    s.teacherIds.includes(currentUser.id) && 
    Object.keys(s.courses || {}).some(cid => myCourseIds.includes(cid))
  );
  
  c.innerHTML = `
    <div class="space-y-4">
      ${myStudents.length === 0 ? '<div class="glass-panel p-10 rounded-3xl text-center"><p class="text-gray-400">لا يوجد طلاب مسجلين في كورساتك حالياً</p></div>' : ''}
      ${myStudents.map(s => `
        <div class="glass-card p-5 rounded-2xl border border-white/5">
          <div class="flex justify-between items-center mb-4">
            <div class="flex items-center gap-4">
              <img src="${s.avatar}" class="w-12 h-12 rounded-full object-cover border border-white/10">
              <div>
                <h3 class="font-bold text-white text-lg">${s.name}</h3>
                <p class="text-xs text-gray-400 font-mono">ID: ${s.id}</p>
              </div>
            </div>
            <span class="px-3 py-1 rounded-full text-xs font-bold ${s.active ? 'badge-active' : 'badge-suspended'}">${s.active ? 'نشط' : 'موقوف'}</span>
          </div>
          <div class="bg-slate-900/50 p-4 rounded-xl border border-white/5">
            <p class="text-xs text-gray-400 mb-3 font-bold uppercase tracking-wider">صلاحيات الوصول لكورساتك:</p>
            <div class="space-y-2">
              ${DB.courses.filter(cr => cr.teacherId === currentUser.id).map(cr => `
                <div class="flex items-center justify-between p-3 rounded-lg hover:bg-slate-800/50 transition">
                  <span class="text-sm font-medium text-gray-200">${cr.title}</span>
                  <button onclick="toggleCourseAccess('${s.id}','${cr.id}')" class="text-xs px-4 py-2 rounded-lg font-bold transition ${s.courses[cr.id] ? 'bg-green-600 text-white hover:bg-green-700' : 'bg-slate-700 text-gray-400 hover:bg-slate-600'}">
                    ${s.courses[cr.id] ? '<i class="fas fa-check ml-1"></i> مفعل' : '<i class="fas fa-times ml-1"></i> ملغي'}
                  </button>
                </div>
              `).join('')}
            </div>
          </div>
        </div>
      `).join('')}
    </div>
  `;
}

function toggleCourseAccess(sid, cid) {
  const s = DB.students.find(x => x.id === sid);
  if (!s.courses) s.courses = {};
  s.courses[cid] = !s.courses[cid];
  saveDB();
  renderTeacherStudents(document.getElementById('contentArea'));
}

function renderTeacherCourses(c) {
  const myCourses = DB.courses.filter(cr => cr.teacherId === currentUser.id);
  c.innerHTML = `
    <button onclick="showAddCourseModal()" class="mb-6 btn-primary text-white px-6 py-3 rounded-xl font-bold flex items-center gap-2 shadow-lg shadow-indigo-500/20">
      <i class="fas fa-plus-circle"></i> إضافة كورس جديد
    </button>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      ${myCourses.map(cr => `
        <div class="glass-card rounded-2xl p-6 course-card border border-white/5">
          <div class="flex justify-between items-start mb-4">
            <div>
              <h3 class="font-bold text-xl text-white">${cr.title}</h3>
              <p class="text-xs text-gray-400 mt-1 flex items-center gap-2"><i class="fas fa-video"></i> ${cr.lessons.length} حصة مسجلة</p>
            </div>
            <button onclick="deleteCourse('${cr.id}')" class="text-red-400 hover:text-red-300 hover:bg-red-500/10 p-2 rounded-lg transition"><i class="fas fa-trash-alt"></i></button>
          </div>
          <div class="space-y-2 mb-4 max-h-60 overflow-y-auto pr-1">
            ${cr.lessons.map(l => `
              <div class="flex items-center justify-between p-3 bg-slate-800/40 rounded-xl border border-white/5 group hover:border-indigo-500/30 transition">
                <div class="flex-1 min-w-0">
                  <span class="text-sm font-medium text-gray-200 block truncate">${l.title}</span>
                  <p class="text-[10px] text-gray-500 mt-0.5"><i class="far fa-clock ml-1"></i>${l.duration}</p>
                </div>
                <button onclick="deleteLesson('${cr.id}','${l.id}')" class="text-gray-600 hover:text-red-400 p-2 rounded-lg hover:bg-red-500/10 transition opacity-0 group-hover:opacity-100"><i class="fas fa-times"></i></button>
              </div>
            `).join('')}
            ${cr.lessons.length === 0 ? '<p class="text-xs text-gray-500 text-center py-4 italic">لا توجد حصص مضافة بعد</p>' : ''}
          </div>
          <button onclick="showAddLessonModal('${cr.id}')" class="w-full py-3 border-2 border-dashed border-indigo-500/30 rounded-xl text-indigo-400 text-sm font-bold hover:bg-indigo-500/10 hover:border-indigo-500/50 transition flex items-center justify-center gap-2">
            <i class="fas fa-plus"></i> إضافة حصة جديدة
          </button>
        </div>
      `).join('')}
    </div>
  `;
}

function showAddCourseModal() {
  showModal(`
    <h3 class="font-black text-xl mb-6 text-white flex items-center gap-2"><i class="fas fa-book text-indigo-500"></i> إضافة كورس جديد</h3>
    <form onsubmit="addCourse(event)" class="space-y-4">
      <input type="text" id="newCourseTitle" placeholder="اسم الكورس (مثال: الفيزياء للصف الثالث)" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-3.5 text-white focus:border-indigo-500 outline-none" required>
      <button type="submit" class="w-full btn-primary text-white py-3.5 rounded-xl font-bold">إنشاء الكورس</button>
    </form>
  `);
}

function addCourse(e) {
  e.preventDefault();
  const title = document.getElementById('newCourseTitle').value.trim();
  const id = 'C' + Date.now();
  DB.courses.push({ id, title, teacherId: currentUser.id, lessons: [] });
  saveDB();
  closeModal();
  renderTeacherCourses(document.getElementById('contentArea'));
}

function deleteCourse(cid) {
  if (!confirm('هل أنت متأكد من حذف هذا الكورس؟ سيتم حذف جميع الحصص والامتحانات المرتبطة به.')) return;
  DB.courses = DB.courses.filter(c => c.id !== cid);
  DB.exams = DB.exams.filter(e => e.courseId !== cid);
  saveDB();
  renderTeacherCourses(document.getElementById('contentArea'));
}

function showAddLessonModal(courseId) {
  const course = DB.courses.find(c => c.id === courseId);
  const lessonNum = course.lessons.length + 1;
  showModal(`
    <h3 class="font-black text-xl mb-2 text-white">إضافة حصة جديدة</h3>
    <p class="text-sm text-gray-400 mb-6">الكورس: <span class="text-indigo-400 font-bold">${course.title}</span></p>
    <form onsubmit="addLesson(event, '${courseId}')" class="space-y-4">
      <input type="text" id="lessonTitle" value="الحصة ${lessonNum}: " placeholder="عنوان الحصة" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-3 text-white focus:border-indigo-500 outline-none" required>
      <div class="grid grid-cols-2 gap-3">
        <input type="text" id="lessonDuration" placeholder="المدة (45:00)" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-3 text-white focus:border-indigo-500 outline-none" required>
        <input type="url" id="lessonUrl" placeholder="رابط الفيديو (Embed URL)" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-3 text-white focus:border-indigo-500 outline-none" required>
      </div>
      <textarea id="lessonNotes" rows="3" placeholder="ملاحظات أو ملزمة الحصة (ستظهر للطالب تحت الفيديو)" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-3 text-white focus:border-indigo-500 outline-none text-sm"></textarea>
      
      <div class="border-2 border-dashed border-slate-700 rounded-xl p-6 text-center hover:bg-slate-800/50 transition cursor-pointer">
        <i class="fas fa-cloud-upload-alt text-2xl text-gray-500 mb-2"></i>
        <p class="text-xs text-gray-400">أو ارفع ملف الفيديو مباشرة (سيتم ربطه لاحقاً بـ Backend)</p>
        <input type="file" accept="video/*" class="mt-2 text-xs text-gray-400 file:bg-indigo-600 file:text-white file:border-0 file:rounded-lg file:px-3 file:py-1.5 file:text-xs file:cursor-pointer">
      </div>
      
      <button type="submit" class="w-full btn-primary text-white py-3.5 rounded-xl font-bold mt-2">حفظ وإضافة الحصة</button>
    </form>
  `);
}

function addLesson(e, courseId) {
  e.preventDefault();
  const course = DB.courses.find(c => c.id === courseId);
  const lesson = {
    id: 'L' + Date.now(),
    title: document.getElementById('lessonTitle').value.trim(),
    duration: document.getElementById('lessonDuration').value.trim(),
    url: document.getElementById('lessonUrl').value.trim(),
    notes: document.getElementById('lessonNotes').value.trim()
  };
  course.lessons.push(lesson);
  saveDB();
  closeModal();
  renderTeacherCourses(document.getElementById('contentArea'));
}

function deleteLesson(courseId, lessonId) {
  const course = DB.courses.find(c => c.id === courseId);
  course.lessons = course.lessons.filter(l => l.id !== lessonId);
  saveDB();
  renderTeacherCourses(document.getElementById('contentArea'));
}

function renderTeacherExams(c) {
  const myCourseIds = DB.courses.filter(cr => cr.teacherId === currentUser.id).map(cr => cr.id);
  const myExams = DB.exams.filter(ex => myCourseIds.includes(ex.courseId));
  
  c.innerHTML = `
    <button onclick="showCreateExamModal()" class="mb-6 btn-primary text-white px-6 py-3 rounded-xl font-bold flex items-center gap-2 shadow-lg shadow-indigo-500/20">
      <i class="fas fa-plus-circle"></i> إنشاء امتحان جديد
    </button>
    <div class="space-y-4">
      ${myExams.length === 0 ? '<div class="glass-panel p-10 rounded-3xl text-center"><p class="text-gray-400">لم تقم بإنشاء أي امتحانات بعد</p></div>' : ''}
      ${myExams.map(ex => {
        const course = DB.courses.find(cr => cr.id === ex.courseId);
        return `
        <div class="glass-panel p-5 rounded-2xl border border-white/5">
          <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-4 gap-4">
            <div>
              <h3 class="font-bold text-lg text-white">${ex.title}</h3>
              <p class="text-xs text-gray-400 mt-1">المادة: ${course?.title} | <span class="text-indigo-400">${ex.questions.length} أسئلة</span></p>
            </div>
            <div class="flex items-center gap-2 w-full md:w-auto">
              <button onclick="toggleExamActive('${ex.id}')" class="flex-1 md:flex-none text-xs px-4 py-2 rounded-lg font-bold transition ${ex.active ? 'bg-green-600 text-white hover:bg-green-700' : 'bg-slate-700 text-gray-400 hover:bg-slate-600'}">
                ${ex.active ? '<i class="fas fa-eye ml-1"></i> مفعل للطلاب' : '<i class="fas fa-eye-slash ml-1"></i> مخفي'}
              </button>
              <button onclick="deleteExam('${ex.id}')" class="w-10 h-10 flex items-center justify-center rounded-lg text-red-400 hover:bg-red-500/10 transition"><i class="fas fa-trash-alt"></i></button>
            </div>
          </div>
          <div class="bg-slate-900/50 p-4 rounded-xl border border-white/5">
            ${ex.questions.slice(0, 2).map((q,i) => `<p class="text-xs text-gray-400 mb-2 truncate"><span class="text-indigo-400 font-bold ml-1">${i+1}.</span> ${q.q}</p>`).join('')}
            ${ex.questions.length > 2 ? `<p class="text-xs text-gray-500 text-center mt-2">... و ${ex.questions.length - 2} أسئلة أخرى</p>` : ''}
          </div>
        </div>`;
      }).join('')}
    </div>
  `;
}

let questionCount = 1;
function showCreateExamModal() {
  const myCourses = DB.courses.filter(cr => cr.teacherId === currentUser.id);
  if(myCourses.length === 0) { alert('يجب إضافة كورس أولاً قبل إنشاء امتحان'); return; }
  
  questionCount = 1;
  showModal(`
    <h3 class="font-black text-xl mb-4 text-white">إنشاء امتحان ذكي</h3>
    <form onsubmit="createExam(event)" class="space-y-4">
      <select id="examCourse" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-3 text-white outline-none" required>
        <option value="">اختر الكورس المستهدف</option>
        ${myCourses.map(cr => `<option value="${cr.id}">${cr.title}</option>`).join('')}
      </select>
      <input type="text" id="examTitle" placeholder="عنوان الامتحان (مثال: اختبار الحصة الأولى)" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-3 text-white outline-none" required>
      
      <div id="questionsContainer" class="space-y-4 max-h-[40vh] overflow-y-auto pr-2">
        ${getQuestionHTML(1)}
      </div>
      
      <button type="button" onclick="addQuestionField()" class="w-full py-3 border-2 border-dashed border-indigo-500/40 rounded-xl text-indigo-400 text-sm font-bold hover:bg-indigo-500/10 transition">
        <i class="fas fa-plus ml-1"></i> إضافة سؤال آخر
      </button>
      <button type="submit" class="w-full btn-primary text-white py-3.5 rounded-xl font-bold">حفظ الامتحان</button>
    </form>
  `);
}

function getQuestionHTML(num) {
  return `
    <div class="question-block bg-slate-900/50 p-4 rounded-xl relative border border-white/5">
      <button type="button" onclick="this.parentElement.remove()" class="absolute top-2 left-2 text-gray-500 hover:text-red-400 transition"><i class="fas fa-times"></i></button>
      <p class="text-xs text-indigo-400 font-bold mb-3">السؤال ${num}</p>
      <input type="text" name="question" placeholder="نص السؤال" class="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 mb-3 text-sm text-white outline-none focus:border-indigo-500" required>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-2 mb-3">
        <input type="text" name="opt0" placeholder="الخيار أ" class="bg-slate-800 border border-slate-700 rounded-lg p-2 text-sm text-white outline-none" required>
        <input type="text" name="opt1" placeholder="الخيار ب" class="bg-slate-800 border border-slate-700 rounded-lg p-2 text-sm text-white outline-none" required>
        <input type="text" name="opt2" placeholder="الخيار ج" class="bg-slate-800 border border-slate-700 rounded-lg p-2 text-sm text-white outline-none" required>
        <input type="text" name="opt3" placeholder="الخيار د" class="bg-slate-800 border border-slate-700 rounded-lg p-2 text-sm text-white outline-none" required>
      </div>
      <select name="correct" class="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-sm text-white outline-none">
        <option value="0">الإجابة الصحيحة هي: أ</option>
        <option value="1">الإجابة الصحيحة هي: ب</option>
        <option value="2">الإجابة الصحيحة هي: ج</option>
        <option value="3">الإجابة الصحيحة هي: د</option>
      </select>
    </div>
  `;
}

function addQuestionField() {
  questionCount++;
  document.getElementById('questionsContainer').insertAdjacentHTML('beforeend', getQuestionHTML(questionCount));
}

function createExam(e) {
  e.preventDefault();
  const courseId = document.getElementById('examCourse').value;
  const title = document.getElementById('examTitle').value.trim();
  const blocks = document.querySelectorAll('.question-block');
  const questions = [];
  
  blocks.forEach(block => {
    const inputs = block.querySelectorAll('input[type="text"]');
    const correctSelect = block.querySelector('select[name="correct"]');
    if (inputs.length >= 5) {
      questions.push({
        q: inputs[0].value.trim(),
        options: [inputs[1].value.trim(), inputs[2].value.trim(), inputs[3].value.trim(), inputs[4].value.trim()],
        correct: parseInt(correctSelect.value)
      });
    }
  });

  if (questions.length === 0) { alert('يجب إضافة سؤال واحد على الأقل'); return; }

  const course = DB.courses.find(c => c.id === courseId);
  const targetLessonId = course.lessons.length > 0 ? course.lessons[0].id : null;

  DB.exams.push({ id: 'E'+Date.now(), courseId, lessonId: targetLessonId, title, active: false, questions });
  questionCount = 1;
  saveDB();
  closeModal();
  renderTeacherExams(document.getElementById('contentArea'));
}

function toggleExamActive(eid) {
  const ex = DB.exams.find(e => e.id === eid);
  ex.active = !ex.active;
  saveDB();
  renderTeacherExams(document.getElementById('contentArea'));
}

function deleteExam(eid) {
  if (!confirm('حذف هذا الامتحان نهائياً؟')) return;
  DB.exams = DB.exams.filter(e => e.id !== eid);
  saveDB();
  renderTeacherExams(document.getElementById('contentArea'));
}

// ==========================================
// ADMIN VIEWS
// ==========================================
function renderAdminDash(c) {
  c.innerHTML = `
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
      <div class="glass-panel p-6 rounded-2xl border-b-4 border-indigo-500">
        <h3 class="text-gray-400 text-sm font-medium">المدرسين</h3>
        <p class="text-4xl font-black text-white mt-2">${DB.teachers.length}</p>
      </div>
      <div class="glass-panel p-6 rounded-2xl border-b-4 border-green-500">
        <h3 class="text-gray-400 text-sm font-medium">الطلاب النشطين</h3>
        <p class="text-4xl font-black text-white mt-2">${DB.students.filter(s=>s.active).length}</p>
      </div>
      <div class="glass-panel p-6 rounded-2xl border-b-4 border-yellow-500">
        <h3 class="text-gray-400 text-sm font-medium">إجمالي الكورسات</h3>
        <p class="text-4xl font-black text-white mt-2">${DB.courses.length}</p>
      </div>
      <div class="glass-panel p-6 rounded-2xl border-b-4 border-purple-500">
        <h3 class="text-gray-400 text-sm font-medium">الامتحانات</h3>
        <p class="text-4xl font-black text-white mt-2">${DB.exams.length}</p>
      </div>
    </div>
    <div class="glass-panel p-6 rounded-2xl border border-white/5">
      <h3 class="font-bold text-lg mb-4 text-white">آخر النشاطات على المنصة</h3>
      <div class="space-y-4 text-sm">
        <div class="flex items-center gap-3 p-3 bg-slate-800/30 rounded-xl"><i class="fas fa-user-plus text-green-400 text-lg"></i><span class="text-gray-300">تم تسجيل <b class="text-white">${DB.students.length}</b> طالب في النظام</span></div>
        <div class="flex items-center gap-3 p-3 bg-slate-800/30 rounded-xl"><i class="fas fa-book text-indigo-400 text-lg"></i><span class="text-gray-300">يوجد <b class="text-white">${DB.courses.reduce((a,c)=>a+c.lessons.length,0)}</b> حصة تعليمية متاحة حالياً</span></div>
      </div>
    </div>
  `;
}

function renderAdminTeachers(c) {
  c.innerHTML = `
    <button onclick="showCreateTeacherModal()" class="mb-6 btn-primary text-white px-6 py-3 rounded-xl font-bold flex items-center gap-2">
      <i class="fas fa-user-plus"></i> إنشاء حساب مدرس جديد
    </button>
    <div class="glass-panel rounded-2xl overflow-hidden border border-white/5">
      <div class="overflow-x-auto">
        <table class="w-full text-right text-sm">
          <thead class="bg-slate-800/80 text-gray-400 border-b border-white/5">
            <tr><th class="p-4 font-bold">الاسم</th><th class="p-4 font-bold">الهاتف</th><th class="p-4 font-bold">الكود</th><th class="p-4 font-bold">الحالة</th><th class="p-4 font-bold">إجراءات</th></tr>
          </thead>
          <tbody class="divide-y divide-slate-700/50">
            ${DB.teachers.map(t => `
              <tr class="hover:bg-slate-800/30 transition">
                <td class="p-4 font-bold text-white flex items-center gap-3"><img src="${t.avatar}" class="w-8 h-8 rounded-full">${t.name}</td>
                <td class="p-4 font-mono text-xs text-gray-400">${t.phone||'-'}</td>
                <td class="p-4 font-mono text-indigo-400 font-bold">${t.code}</td>
                <td class="p-4"><span class="px-3 py-1 rounded-full text-xs font-bold ${t.active?'badge-active':'badge-suspended'}">${t.active?'نشط':'موقوف'}</span></td>
                <td class="p-4">
                  <div class="flex gap-2">
                    <button onclick="toggleTeacherStatus('${t.id}')" class="text-xs ${t.active?'bg-yellow-600 hover:bg-yellow-700':'bg-green-600 hover:bg-green-700'} px-3 py-1.5 rounded-lg text-white transition font-bold">${t.active?'إيقاف':'تفعيل'}</button>
                    <button onclick="deleteTeacher('${t.id}')" class="text-xs bg-red-600 hover:bg-red-700 px-3 py-1.5 rounded-lg text-white transition font-bold">حذف</button>
                  </div>
                </td>
              </tr>
            `).join('')}
          </tbody>
        </table>
      </div>
    </div>
  `;
}

function showCreateTeacherModal() {
  showModal(`
    <h3 class="font-black text-xl mb-4 text-white">إنشاء حساب مدرس جديد</h3>
    <form onsubmit="createTeacher(event)" class="space-y-4">
      <input type="text" id="newTName" placeholder="الاسم الكامل للمدرس" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-3 text-white outline-none" required>
      <input type="tel" id="newTPhone" placeholder="رقم الهاتف" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-3 text-white outline-none" required>
      <input type="text" id="newTCode" placeholder="كود المادة (مثال: MATH-2026)" class="w-full bg-slate-900 border border-slate-700 rounded-xl p-3 text-white outline-none" required>
      <button type="submit" class="w-full btn-primary text-white py-3.5 rounded-xl font-bold">إنشاء وتوليد بيانات الدخول</button>
    </form>
    <div id="newTCreds" class="hidden mt-4 p-4 bg-green-500/10 border border-green-500/30 rounded-xl text-center">
      <p class="text-green-400 text-sm font-bold mb-2">✓ تم الإنشاء بنجاح!</p>
      <p class="text-xs text-gray-400 mb-2">انسخ البيانات وأرسلها للمدرس:</p>
      <div class="font-mono text-base bg-slate-900 p-3 rounded-lg text-white" id="credText"></div>
    </div>
  `);
}

function createTeacher(e) {
  e.preventDefault();
  const name = document.getElementById('newTName').value.trim();
  const phone = document.getElementById('newTPhone').value.trim();
  const code = document.getElementById('newTCode').value.trim();
  const id = 'T' + Math.floor(Math.random()*9000+1000);
  const pass = Math.random().toString(36).slice(-6);
  
  DB.teachers.push({ id, pass, name, phone, code, active: true, avatar: `https://ui-avatars.com/api/?name=${name}&background=10b981&color=fff` });
  saveDB();
  
  document.getElementById('newTCreds').classList.remove('hidden');
  document.getElementById('credText').innerHTML = `المعرف: <b class="text-indigo-400">${id}</b><br>كلمة المرور: <b class="text-yellow-400">${pass}</b>`;
}

function toggleTeacherStatus(tid) {
  const t = DB.teachers.find(x => x.id === tid);
  t.active = !t.active;
  saveDB();
  renderAdminTeachers(document.getElementById('contentArea'));
}

function deleteTeacher(tid) {
  if (!confirm('⚠️ هل أنت متأكد من حذف هذا المدرس؟ سيتم حذف كورساته وطلابُه المرتبطون به.')) return;
  DB.teachers = DB.teachers.filter(t => t.id !== tid);
  DB.courses = DB.courses.filter(c => c.teacherId !== tid);
  DB.exams = DB.exams.filter(e => !DB.courses.find(c => c.id === e.courseId));
  saveDB();
  renderAdminTeachers(document.getElementById('contentArea'));
}

function renderAdminStudents(c) {
  c.innerHTML = `
    <div class="glass-panel rounded-2xl overflow-hidden border border-white/5">
      <div class="overflow-x-auto">
        <table class="w-full text-right text-sm">
          <thead class="bg-slate-800/80 text-gray-400 border-b border-white/5"><tr><th class="p-4 font-bold">الطالب</th><th class="p-4 font-bold">المدرسين</th><th class="p-4 font-bold">الحالة</th><th class="p-4 font-bold">إجراء</th></tr></thead>
          <tbody class="divide-y divide-slate-700/50">
            ${DB.students.map(s => {
              const teachers = DB.teachers.filter(t => s.teacherIds.includes(t.id));
              return `<tr class="hover:bg-slate-800/30 transition">
                <td class="p-4 font-bold text-white flex items-center gap-3"><img src="${s.avatar}" class="w-8 h-8 rounded-full">${s.name}</td>
                <td class="p-4 text-gray-400">${teachers.length > 0 ? teachers.map(t => t.name).join('، ') : '<span class="text-red-400">غير معين</span>'}</td>
                <td class="p-4"><span class="px-3 py-1 rounded-full text-xs font-bold ${s.active?'badge-active':'badge-suspended'}">${s.active?'نشط':'موقوف'}</span></td>
                <td class="p-4"><button onclick="toggleStudentStatus('${s.id}')" class="text-xs bg-slate-700 hover:bg-indigo-600 px-4 py-2 rounded-lg text-white transition font-bold">${s.active?'إيقاف':'تفعيل'}</button></td>
              </tr>`;
            }).join('')}
          </tbody>
        </table>
      </div>
    </div>
  `;
}

function toggleStudentStatus(id) {
  const s = DB.students.find(x => x.id === id);
  s.active = !s.active;
  saveDB();
  renderAdminStudents(document.getElementById('contentArea'));
}

function renderAdminAllCourses(c) {
  c.innerHTML = `
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      ${DB.courses.map(cr => {
        const teacher = DB.teachers.find(t => t.id === cr.teacherId);
        return `
        <div class="glass-card rounded-2xl p-5 course-card border border-white/5">
          <div class="flex justify-between items-start mb-3">
            <h3 class="font-bold text-lg text-white">${cr.title}</h3>
            <span class="text-[10px] bg-indigo-500/20 text-indigo-400 px-2 py-1 rounded-full font-bold">${cr.lessons.length} حصة</span>
          </div>
          <p class="text-xs text-gray-400 mb-3 flex items-center gap-2"><img src="${teacher?.avatar}" class="w-5 h-5 rounded-full"> ${teacher?.name || 'غير محدد'}</p>
          <div class="mt-4 pt-3 border-t border-slate-700/50">
            <button onclick="deleteCourseAdmin('${cr.id}')" class="text-xs text-red-400 hover:text-red-300 font-bold flex items-center gap-1"><i class="fas fa-trash"></i> حذف الكورس نهائياً</button>
          </div>
        </div>`;
      }).join('')}
    </div>
  `;
}

function deleteCourseAdmin(cid) {
  if (!confirm('حذف هذا الكورس نهائياً؟')) return;
  DB.courses = DB.courses.filter(c => c.id !== cid);
  DB.exams = DB.exams.filter(e => e.courseId !== cid);
  saveDB();
  renderAdminAllCourses(document.getElementById('contentArea'));
}

// ==========================================
// MODAL HELPERS
// ==========================================
function showModal(html) {
  document.getElementById('modalContent').innerHTML = html;
  document.getElementById('genericModal').classList.remove('hidden');
}
function closeModal() {
  document.getElementById('genericModal').classList.add('hidden');
}
document.getElementById('genericModal').addEventListener('click', function(e) {
  if (e.target === this) closeModal();
});

// Global Protection
document.addEventListener('contextmenu', e => e.preventDefault());
document.addEventListener('keydown', e => {
  if (e.key === 'Escape') { closeVideo(); closeModal(); }
});
</script>
</body>
</html>
