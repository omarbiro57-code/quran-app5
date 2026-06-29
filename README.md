[index.html](https://github.com/user-attachments/files/29457836/index.html)

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>القرآن الكريم | The Holy Quran</title>
  <link rel="stylesheet" href="style.css" />
  <link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400;1,700&family=Cairo:wght@300;400;500;600;700;800;900&family=Tajawal:wght@300;400;500;700;800;900&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />
</head>
<body class="theme-emerald">
  <div class="app-container">
    
    <header class="app-header">
      <div class="header-logo" id="logoBtn">
        <div class="logo-icon"><i class="fa-solid fa-book-quran"></i></div>
        <div class="logo-text">
          <span class="logo-main">القرآن الكريم</span>
          <span class="logo-sub">THE HOLY QURAN</span>
        </div>
      </div>

      <div class="header-search-bar">
        <i class="fa-solid fa-magnifying-glass search-icon"></i>
        <input type="text" id="globalSearchInput" placeholder="ابحث عن سورة، آية، أو كلمة..." autocomplete="off" />
        <button id="clearSearchBtn" class="clear-search-btn"><i class="fa-solid fa-xmark"></i></button>
      </div>

      <div class="header-actions">
        <button class="action-btn" id="toggleSettingsBtn" title="إعدادات القراءة">
          <i class="fa-solid fa-sliders"></i>
        </button>
        <button class="action-btn" id="toggleBookmarksBtn" title="المفضلة والعلامات">
          <i class="fa-solid fa-bookmark"></i>
          <span class="badge" id="bookmarkBadge" style="display:none;">0</span>
        </button>
        <div class="theme-selector-dropdown">
          <button class="action-btn" id="themeBtn" title="تغيير المظهر">
            <i class="fa-solid fa-palette"></i>
          </button>
          <div class="theme-dropdown-content" id="themeDropdown">
            <button class="theme-opt opt-emerald active" data-theme="emerald">
              <span class="color-dot"></span> الزمردي
            </button>
            <button class="theme-opt opt-dark" data-theme="dark">
              <span class="color-dot"></span> الليل الفاخر
            </button>
            <button class="theme-opt opt-sepia" data-theme="sepia">
              <span class="color-dot"></span> الورقي الدافئ
            </button>
            <button class="theme-opt opt-light" data-theme="light">
              <span class="color-dot"></span> النهار الهادئ
            </button>
          </div>
        </div>
      </div>
    </header>

    <div class="content-wrapper">
      
      <aside class="app-sidebar" id="appSidebar">
        <button class="close-sidebar-btn" id="closeSidebarBtn"><i class="fa-solid fa-xmark"></i></button>
        
        <div class="sidebar-section">
          <h3><i class="fa-solid fa-microphone-lines"></i> اختيار القارئ</h3>
          <div class="reciter-selector">
            <select id="reciterSelect" class="form-select">
              <option value="ar.alafasy" selected>مشاري راشد العفاسي</option>
              <option value="ar.abdulbasitmuhammadabdusamad">عبد الباسط عبد الصمد</option>
              <option value="ar.husary">محمود خليل الحصري</option>
              <option value="ar.hudhaify">علي الحذيفي</option>
              <option value="ar.minshawi">محمد صديق المنشاوي</option>
            </select>
          </div>
        </div>

        <div class="sidebar-section" id="quickSettingsPanel">
          <h3><i class="fa-solid fa-font"></i> خيارات الخط والقراءة</h3>
          <div class="setting-item">
            <label for="arabicFontSize">حجم الخط العربي</label>
            <div class="range-control">
              <input type="range" id="arabicFontSize" min="20" max="50" value="32" step="2" />
              <span class="range-value" id="arabicFontSizeVal">32px</span>
            </div>
          </div>
          <div class="setting-item">
            <label for="translationFontSize">حجم خط الترجمة</label>
            <div class="range-control">
              <input type="range" id="translationFontSize" min="14" max="28" value="18" step="1" />
              <span class="range-value" id="translationFontSizeVal">18px</span>
            </div>
          </div>
          <div class="setting-item check-item">
            <input type="checkbox" id="showTranslation" checked />
            <label for="showTranslation">عرض الترجمة والتفسير</label>
          </div>
        </div>

        <div class="sidebar-section">
          <h3><i class="fa-solid fa-star"></i> الآيات المحفوظة</h3>
          <div class="bookmarks-list" id="bookmarksList">
            <p class="empty-msg">لا توجد آيات محفوظة حالياً</p>
          </div>
        </div>
      </aside>

      <main class="main-content" id="mainContent">
        
        <div id="loadingOverlay" class="loading-overlay hidden">
          <div class="spinner"></div>
          <p>جاري التحميل...</p>
        </div>

        <section id="surahIndexSection" class="content-section active">
          <div class="welcome-banner">
            <div class="banner-content">
              <h1>بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ</h1>
              <p>﴿إِنَّا نَحْنُ نَزَّلْنَا الذِّكْرَ وَإِنَّا لَهُ لَحَافِظُونَ﴾</p>
              <div class="index-filters">
                <button class="filter-btn active" data-filter="all">الكل</button>
                <button class="filter-btn" data-filter="meccan">مكي</button>
                <button class="filter-btn" data-filter="medinan">مدني</button>
              </div>
            </div>
          </div>
          
          <div class="surah-grid" id="surahGrid"></div>
        </section>

        <section id="surahReaderSection" class="content-section">
          <div class="reader-header">
            <button class="back-btn" id="backToIndexBtn"><i class="fa-solid fa-arrow-right"></i> العودة للفهرس</button>
            <div class="surah-details">
              <h2 id="readerSurahName">اسم السورة</h2>
              <p id="readerSurahInfo">سورة مكيّة • ٧ آيات</p>
            </div>
            <div class="reader-actions-top">
              <button class="action-btn-pill" id="playFullSurahBtn"><i class="fa-solid fa-play"></i> تشغيل السورة</button>
            </div>
          </div>

          <div class="bismillah-block" id="bismillahBlock">
            بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ
          </div>

          <div class="quran-reader-container" id="quranReaderContainer"></div>
        </section>

        <section id="searchResultsSection" class="content-section">
          <div class="search-results-header">
            <button class="back-btn" id="closeSearchBtn"><i class="fa-solid fa-arrow-right"></i> إغلاق البحث</button>
            <h2>نتائج البحث عن: <span id="searchKeyword" class="highlight-text">""</span></h2>
            <p id="searchResultsCount">تم العثور على 0 نتيجة</p>
          </div>
          
          <div class="search-results-container" id="searchResultsContainer"></div>
        </section>

      </main>
    </div>

    <footer class="app-player" id="appPlayer">
      <div class="player-progress-container">
        <input type="range" id="audioProgress" min="0" max="100" value="0" />
        <div class="player-time">
          <span id="currentTime">00:00</span>
          <span id="durationTime">00:00</span>
        </div>
      </div>

      <div class="player-main-controls">
        <div class="player-surah-info">
          <div class="player-icon-box"><i class="fa-solid fa-play"></i></div>
          <div class="player-info-text">
            <span class="player-surah-title" id="playerSurahTitle">اختر سورة للبدء</span>
            <span class="player-reciter-name" id="playerReciterName">مشاري راشد العفاسي</span>
          </div>
        </div>

        <div class="player-buttons">
          <button class="player-btn" id="prevAyahBtn" title="الآية السابقة"><i class="fa-solid fa-step-forward"></i></button>
          <button class="player-btn play-pause-btn" id="playPauseBtn" title="تشغيل / إيقاف"><i class="fa-solid fa-play"></i></button>
          <button class="player-btn" id="nextAyahBtn" title="الآية التالية"><i class="fa-solid fa-step-backward"></i></button>
          
          <span class="controls-divider">|</span>

          <button class="player-btn toggle-btn" id="repeatAyahBtn" title="تكرار الآية (مغلق)"><i class="fa-solid fa-repeat"></i></button>
          <button class="player-btn toggle-btn active" id="autoScrollBtn" title="التمرير التلقائي (مفعل)"><i class="fa-solid fa-arrows-to-eye"></i></button>
          
          <div class="speed-control-container">
            <button class="player-btn" id="speedBtn" title="سرعة التشغيل">1.0x</button>
            <div class="speed-menu" id="speedMenu">
              <button data-speed="0.75">0.75x</button>
              <button class="active" data-speed="1.0">1.0x</button>
              <button data-speed="1.25">1.25x</button>
              <button data-speed="1.5">1.5x</button>
              <button data-speed="2.0">2.0x</button>
            </div>
          </div>
        </div>

        <div class="player-secondary-controls">
          <div class="volume-control">
            <button class="player-btn" id="muteBtn" title="كتم الصوت"><i class="fa-solid fa-volume-high"></i></button>
            <input type="range" id="volumeSlider" min="0" max="100" value="80" />
          </div>
        </div>
      </div>
    </footer>
    
    <audio id="quranAudio" preload="auto"></audio>
  </div>

  <script src="main.js"></script>
</body>
</html>
