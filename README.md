
<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>أداة السكة الحديد (المواقع) - تصميم عصري</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&family=Tajawal:wght@400;700&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200" rel="stylesheet" />

<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>

<style>
/* === متغيرات الألوان الأساسية - لوحة ألوان عصرية (Vibrant & Deep) === */
:root {
  /* وضع الألوان الأساسية الجديدة (Purple/Sky Blue Gradient) */
  --primary-color: #4a00e0; /* بنفسجي غامق (Main) */
  --primary-color-light: #8e2de2; /* بنفسجي فاتح (Accent) */
  --accent-color: #00b894; /* زمردي (Success/Save) */
  --danger-color: #ff6b6b; /* أحمر (Delete) */
  
  /* الوضع النهاري (Light Mode - نيو-مورفيزم خفيف) */
  --bg-color-light: #f4f7f9; /* خلفية هادئة جداً */
  --surface-color-light: #ffffff; /* سطح البطاقات */
  --text-color-light: #1e3a8a; /* أزرق داكن للنص (لراحة العين) */
  --shadow-light: 0 8px 30px rgba(0, 0, 0, 0.08); /* ظل ناعم */
  --border-light: #e0e7ee; /* حدود خفيفة */
  --input-bg-light: #ffffff; 
}

/* === النمط الليلي (Dark Mode - عميق ودافئ) === */
body.dark-mode {
  --bg-color-dark: #121212; /* أسود عميق (OLED friendly) */
  --surface-color-dark: #1e1e1e; /* سطح البطاقات الداكن */
  --text-color-dark: #f0f0f0; /* نص فاتح جداً */
  --shadow-dark: 0 8px 30px rgba(0, 0, 0, 0.6); /* ظل عميق */
  --border-dark: #3a3a3a;
  --input-bg-dark: #2a2a2a; 
  
  /* تحديث الألوان الرئيسية للوضع الليلي (Gold/Emerald) */
  --primary-color: #ffeaa7; /* ذهبي فاتح (Main/Text) */
  --primary-color-light: #55efc4; /* نعناعي فاتح (Accent) */
  --accent-color: #00b894; /* زمردي (Success/Save) */
}


/* ------------------------------------------- */
/* === أنماط النصوص والواجهة العامة === */
body {
  margin: 0;
  background: var(--bg-color-light);
  font-family: "Tajawal", "Cairo", sans-serif; /* تغيير خط الجسم إلى Tajawal */
  color: var(--text-color-light);
  padding-bottom: 30px; 
  transition: background 0.5s, color 0.5s;
  line-height: 1.6;
}

/* 📐 تحسين مظهر الخط في الوضع الليلي */
body.dark-mode {
    font-family: "Cairo", "Tajawal", sans-serif; /* Cairo للنص العربي الداكن */
}

/* === إطار RHALLAB - تصميم متوهج عصري === */
#rhallabTitleContainer {
    text-align: center;
    padding: 25px 15px;
    /* التعديل هنا: زيادة الهامش السفلي من 0 إلى 30px */
    margin: 15px 15px 30px; 
    /* خلفية زجاجية/متوهجة (Glassmorphism/Vibrant) */
    background: linear-gradient(135deg, var(--primary-color) 0%, var(--primary-color-light) 100%);
    color: #ffffff;
    border-radius: 25px;
    box-shadow: 0 12px 40px rgba(74, 0, 224, 0.4);
    animation: neonGlow 4s infinite alternate; 
    transition: all 0.5s;
    overflow: hidden; /* لإخفاء تجاوز الظل */
    position: relative;
    z-index: 1;
}

#rhallabTitle {
    font-size: 52px; 
    font-weight: 900; 
    margin: 0;
    letter-spacing: 6px; 
    text-shadow: 0 4px 8px rgba(0, 0, 0, 0.5); /* ظل نص قوي */
    font-family: "Cairo", sans-serif;
}

/* تأثير الإضاءة النيونية */
@keyframes neonGlow {
    0% { box-shadow: 0 12px 40px rgba(74, 0, 224, 0.4), 0 0 10px rgba(142, 45, 226, 0.8); }
    100% { box-shadow: 0 12px 50px rgba(74, 0, 224, 0.7), 0 0 20px rgba(142, 45, 226, 1); }
}

body.dark-mode #rhallabTitleContainer {
    /* ألوان ليلية: أخضر / نعناعي */
    background: linear-gradient(135deg, #00b894 0%, #00cec9 100%); 
    box-shadow: 0 12px 40px rgba(0, 184, 148, 0.4);
    color: var(--text-color-dark);
}
body.dark-mode @keyframes neonGlow {
    0% { box-shadow: 0 12px 40px rgba(0, 184, 148, 0.4), 0 0 10px rgba(0, 206, 201, 0.8); }
    100% { box-shadow: 0 12px 50px rgba(0, 184, 148, 0.7), 0 0 20px rgba(0, 206, 201, 1); }
}


/* === شريط علوي أنيق وعملي === */
#topBar {
  background: var(--surface-color-light);
  padding: 10px 15px;
  box-shadow: var(--shadow-light);
  display: flex;
  align-items: center;
  gap: 10px;
  /* تم إزالة الهامش السفلي من هنا، حيث أصبح الهامش في العنوان كافياً */
  margin-bottom: 20px; 
  border-bottom-left-radius: 15px;
  border-bottom-right-radius: 15px;
}

body.dark-mode #topBar {
    background: var(--surface-color-dark);
    box-shadow: var(--shadow-dark);
}

#searchBox {
  flex-grow: 1;
  padding: 12px 20px;
  border-radius: 25px;
  border: 1px solid var(--border-light);
  font-size: 16px;
  background: var(--input-bg-light);
  color: var(--text-color-light);
  transition: all 0.3s;
}
#searchBox:focus {
  border-color: var(--primary-color-light);
  box-shadow: 0 0 0 4px rgba(142, 45, 226, 0.2); 
  background: var(--surface-color-light);
}
body.dark-mode #searchBox {
    background: var(--input-bg-dark);
    border-color: var(--border-dark);
    color: var(--text-color-dark);
}
body.dark-mode #searchBox:focus {
    border-color: var(--primary-color);
    box-shadow: 0 0 0 4px rgba(255, 234, 167, 0.2);
}

/* زر البحث الأساسي */
#topBar .search-btn { 
  background: var(--primary-color-light);
  color: white; 
  padding: 10px 18px; 
  border-radius: 25px;
  font-size: 15px;
  font-weight: 600;
  transition: all 0.3s ease-in-out;
  display: flex; 
  align-items: center;
  gap: 5px;
  border: none;
  cursor: pointer;
}
#topBar .search-btn:hover {
    background: var(--primary-color);
}
#topBar .search-btn:active {
  transform: scale(0.95);
}

/* زر الإلغاء (الأحمر) */
#topBar #cancelSearchBtn {
    background: var(--danger-color);
}
#topBar #cancelSearchBtn:hover {
    background: #e74c3c;
}

/* زر التبديل بين الوضعين - تصميم أنيق وعصري */
#modeToggleBtn {
  background: var(--border-light); 
  border: none;
  color: var(--primary-color);
  width: 48px; 
  height: 48px; 
  border-radius: 50%; 
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: all 0.3s;
  cursor: pointer;
}
#modeToggleBtn:hover {
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    transform: rotate(15deg);
}
body.dark-mode #modeToggleBtn {
    background: #333;
    color: var(--primary-color); /* اللون الذهبي الفاتح */
}


/* === قائمة الأزرار الرئيسية - تصميم Glassmorphism خفيف === */
#mainButtons {
  padding: 0 15px; 
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr)); 
  gap: 15px; 
  margin-top: 25px; 
}

button.action {
  background: var(--surface-color-light);
  border: none;
  padding: 20px 10px; 
  border-radius: 20px;
  font-size: 16px;
  font-weight: 700;
  box-shadow: var(--shadow-light);
  transition: transform 0.3s, box-shadow 0.3s, background 0.5s;
  color: var(--text-color-light); 
  cursor: pointer;
  /* إضافة تأثير Glassmorphism خفيف في الوضع النهاري */
  backdrop-filter: blur(5px);
}

button.action:hover {
  box-shadow: 0 10px 25px rgba(0,0,0,0.15); 
  background: linear-gradient(145deg, var(--bg-color-light) 50%, var(--surface-color-light) 100%);
}
button.action:active {
  transform: scale(0.95); 
}

body.dark-mode button.action {
    background: var(--surface-color-dark);
    box-shadow: var(--shadow-dark);
    color: var(--text-color-dark);
}
body.dark-mode button.action:hover {
    background: linear-gradient(145deg, #252525 50%, var(--surface-color-dark) 100%);
}


/* أيقونات الأزرار الرئيسية */
.icon {
  font-size: 40px; 
  color: var(--primary-color-light);
  transition: color 0.4s, transform 0.2s;
  margin-bottom: 5px;
  display: block; /* لتمكين الهامش السفلي */
}
.icon:hover {
    transform: scale(1.08);
}

.icon-save { color: var(--accent-color); } /* لون زمردي للحفظ */ 
body.dark-mode .icon-save { color: var(--accent-color); }


/* === حاوية الجداول المصنفة - تصميم البطاقات (Cards) === */
#pointsTablesContainer {
    padding: 0 15px;
    margin-top: 30px;
}

#categorizedTablesGrid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); 
    gap: 20px;
}

#otherTableContainer {
    grid-column: 1 / -1; 
    margin-top: 20px; 
}


.points-category-container {
  padding: 15px;
  background: var(--surface-color-light);
  border-radius: 20px; /* حواف أكثر استدارة */
  box-shadow: var(--shadow-light);
  transition: background 0.5s, box-shadow 0.5s;
  border: 1px solid var(--border-light);
}
body.dark-mode .points-category-container {
    background: var(--surface-color-dark);
    box-shadow: var(--shadow-dark);
    border-color: var(--border-dark);
}

.points-category-container h2 {
  color: var(--primary-color);
  font-size: 18px; 
  display: flex;
  align-items: center;
  gap: 10px;
  padding-bottom: 10px;
  border-bottom: 2px solid var(--border-light);
  margin-bottom: 15px;
  font-weight: 700;
  font-family: "Cairo", sans-serif;
}
body.dark-mode .points-category-container h2 {
    color: var(--primary-color); 
    border-bottom-color: var(--border-dark);
}

.points-category-container h2 .material-symbols-outlined {
    font-size: 34px !important; 
    color: var(--primary-color-light) !important;
}

.points-table {
  width: 100%;
  border-collapse: separate; /* لفصل الحدود عن بعضها */
  border-spacing: 0 5px; /* تباعد بين الصفوف */
  font-size: 14px; 
}

.points-table th, .points-table td {
  padding: 10px; 
  text-align: right;
  /* إزالة الحدود الداخلية التقليدية */
  border: none;
}

.points-table thead tr {
    /* لون داكن للرأس */
    background: #e9ecef;
    border-radius: 10px; 
}
.points-table th {
  background: #e9ecef;
  font-weight: 700;
  color: #343a40;
}
body.dark-mode .points-table thead tr {
    background: #2a2a2a;
}
body.dark-mode .points-table th {
    background: #2a2a2a;
    color: var(--primary-color-light);
}


.points-table tbody tr {
    transition: background 0.3s;
    border-radius: 10px;
    margin-bottom: 5px;
}

.points-table tr:hover {
  background: #f0f6ff; /* لون تظليل ناعم في النهاري */
  cursor: pointer;
}
body.dark-mode .points-table tr:hover {
  background: #2a2a2a; /* لون تظليل ناعم في الليلي */
}

/* عمود الإجراءات (الإزالة) */
.points-table .action-col {
    text-align: center;
    width: 60px;
}
.delete-btn {
    background: var(--danger-color);
    padding: 8px 12px;
    border-radius: 8px;
    font-size: 13px;
    color: white;
    border: none;
    cursor: pointer;
    transition: background 0.3s, transform 0.2s;
    font-weight: 700;
}
.delete-btn:hover {
    background: #e74c3c;
    transform: scale(1.05);
}


/* === قسم QR Code - شكل دائري وجذاب === */
#qrCodeContainer {
    margin: 40px auto 10px;
    padding: 20px;
    background: var(--surface-color-light);
    border-radius: 50%; /* جعلها دائرية */
    box-shadow: var(--shadow-light);
    width: 200px;
    height: 200px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    direction: ltr; 
    transition: all 0.5s;
    overflow: hidden; /* لإخفاء تجاوز الرمز */
}
#qrCodeContainer:hover {
    box-shadow: 0 15px 40px rgba(0, 0, 0, 0.2);
    transform: translateY(-5px);
}

#qrCodeContainer p {
    font-size: 13px;
    color: var(--text-color-light);
    margin-top: 10px;
    direction: rtl;
    font-family: "Tajawal", sans-serif;
    opacity: 0.8;
}

body.dark-mode #qrCodeContainer {
    background: var(--surface-color-dark);
    box-shadow: var(--shadow-dark);
}
body.dark-mode #qrCodeContainer p {
    color: #ccc;
}

/* 📐 تمرير الرمز إلى المنتصف بالضبط */
#qrcode {
    line-height: 0;
}
#qrcode img {
    margin: 0 auto;
}
</style>
</head>
<body dir="rtl" onload="initApp()">

<div id="rhallabTitleContainer">
    <h1 id="rhallabTitle">RHALLAB</h1>
</div>

<div id="topBar">
  <input id="searchBox" placeholder="ابحث عن موقع محفوظ بالاسم..." dir="rtl">
  
  <button onclick="searchLocation()" class="search-btn">
    <span class="material-symbols-outlined">search</span>
    بحث
  </button>
  
  <button id="cancelSearchBtn" onclick="clearSearch()" class="search-btn" style="display:none;">
    <span class="material-symbols-outlined">close</span>
    إلغاء
  </button>
  
  <button id="modeToggleBtn" onclick="toggleDarkMode()" title="تبديل الوضع">
    <span id="modeIcon" class="material-symbols-outlined">light_mode</span>
  </button>
</div>

<div id="mainButtons">

  <button class="action" onclick="locateMe()">
    <span class="icon material-symbols-outlined">my_location</span>
    موقعي الحالي
  </button>

  <button class="action" onclick="saveMyLocation()">
    <span class="icon material-symbols-outlined icon-save">save</span>
    حفظ موقعي
  </button>

  <button class="action" onclick="promptForManualLocation()">
    <span class="icon material-symbols-outlined">add_location_alt</span>
    إضافة يدويًا 🗺️
  </button>
</div>

<div id="pointsTablesContainer">
    <div id="categorizedTablesGrid">
    </div>
    <div id="otherTableContainer">
    </div>
</div>

<div id="qrCodeContainer">
    <div id="qrcode"></div>
    <p>امسح ضوئيًا للوصول إلى النسخة الرئيسية من الأداة.</p>
</div>


<script>
// المفتاح المستخدم لحفظ البيانات والمظهر
const STORAGE_KEY = 'railway_saved_points';
const DARK_MODE_KEY = 'railway_dark_mode';

// 🛑 تم تعديل هذه القيمة لتبدأ بقائمة فارغة لـ "حذف جميع الأماكن"
let savedPoints = []; 
// إذا كنت تريد إفراغ الذاكرة المحلية فورًا عند التحميل لتأكيد الحذف:
// localStorage.removeItem(STORAGE_KEY); 

const CATEGORIES = ['PK', 'AD', 'TJ', 'V'];

// متغير لتخزين المواقع التي سيتم عرضها (إما الكل أو نتائج البحث)
let currentPointsToDisplay = savedPoints; 

// حفظ قائمة المواقع في الذاكرة المحلية
function savePointsToStorage() {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(savedPoints));
    // بعد الحفظ، يجب تحديث قائمة العرض الحالية أيضًا إذا لم نكن في وضع التصفية
    if (document.getElementById("cancelSearchBtn").style.display === 'none') {
        currentPointsToDisplay = savedPoints;
    }
}

// تهيئة التطبيق عند التحميل
function initApp() {
    // 💡 إعادة تحميل قائمة المواقع من الذاكرة المحلية بعد الحذف الأولي للتأكد
    savedPoints = JSON.parse(localStorage.getItem(STORAGE_KEY)) || [];
    currentPointsToDisplay = savedPoints;
    
    loadDarkModeSetting(); 
    renderPointsTable();
    generateQRCode(); // توليد رمز QR عند التحميل
}

// توليد رمز QR Code (تم تحديث الرابط هنا)
function generateQRCode() {
    // تفريغ الرمز القديم قبل إنشاء الجديد
    const qrCodeDiv = document.getElementById("qrcode");
    qrCodeDiv.innerHTML = ''; 
    
    // تحديد الألوان بناءً على الوضع
    const colorDark = document.body.classList.contains('dark-mode') ? "#f0f0f0" : "#000000";
    const colorLight = document.body.classList.contains('dark-mode') ? "#1e1e1e" : "#ffffff";
    
    new QRCode(qrCodeDiv, {
        // الرابط الجديد
        text: "https://codepen.io/Mahdi-Rhallab/pen/azNGdeG", 
        width: 128,
        height: 128,
        colorDark : colorDark,
        colorLight : colorLight,
        correctLevel : QRCode.CorrectLevel.H
    });
}


// تحميل إعداد الوضع المظلم وتطبيقه
function loadDarkModeSetting() {
    const isDarkMode = localStorage.getItem(DARK_MODE_KEY) === 'true';
    if (isDarkMode) {
        document.body.classList.add('dark-mode');
        document.getElementById('modeIcon').textContent = 'dark_mode';
    } else {
        document.body.classList.remove('dark-mode');
        document.getElementById('modeIcon').textContent = 'light_mode';
    }
}

// تبديل الوضع الليلي
function toggleDarkMode() {
    const isDarkMode = document.body.classList.toggle('dark-mode');
    localStorage.setItem(DARK_MODE_KEY, isDarkMode);
    
    document.getElementById('modeIcon').textContent = isDarkMode ? 'dark_mode' : 'light_mode';
    // إعادة توليد QR Code بلون مناسب للوضع الجديد
    generateQRCode();
}

/**
 * تصنيف المواقع بناءً على البادئة (تأخذ القائمة كمدخل)
 */
function categorizePoints(pointsList) {
    const categorized = { PK: [], AD: [], TJ: [], V: [], Other: [] };
    
    pointsList.forEach(p => {
        const nameUpper = p.name.trim().toUpperCase();
        let assigned = false;
        
        for (const category of CATEGORIES) {
            if (nameUpper.startsWith(category)) {
                categorized[category].push(p);
                assigned = true;
                break;
            }
        }
        
        if (!assigned) {
            categorized.Other.push(p);
        }
    });
    
    return categorized;
}


// وظيفة لعرض المواقع المحفوظة في الجداول المصنفة (تستخدم currentPointsToDisplay)
function renderPointsTable() {
    const pointsToCategorize = currentPointsToDisplay; 
    
    const gridContainer = document.getElementById('categorizedTablesGrid');
    const otherContainer = document.getElementById('otherTableContainer');
    gridContainer.innerHTML = ''; 
    otherContainer.innerHTML = '';
    
    const categorized = categorizePoints(pointsToCategorize); 
    
    // تعريف ترتيب واسم كل جدول للعرض
    const tablesInfo = [
        { category: 'PK', title: 'مواقع PK (الكيلومتر)', icon: 'railway_alert' },
        { category: 'AD', title: 'مواقع AD (التحويلات)', icon: 'fork_right' },
        { category: 'TJ', title: 'مواقع TJ (تقاطعات)', icon: 'timeline' },
        { category: 'V', title: 'مواقع V (نقاط التفتيش)', icon: 'pin_drop' },
        { category: 'Other', title: 'مواقع أخرى', icon: 'grid_view' }
    ];

    tablesInfo.forEach(info => {
        const points = categorized[info.category];
        
        const categoryDiv = document.createElement('div');
        categoryDiv.className = 'points-category-container';
        
        categoryDiv.innerHTML = `
            <h2>
              <span class="material-symbols-outlined">${info.icon}</span>
              ${info.title} (${points.length})
            </h2>
            <table class="points-table">
              <thead>
                <tr>
                  <th>الاسم</th>
                  <th class="action-col">حذف</th>
                </tr>
              </thead>
              <tbody id="table-body-${info.category}">
              </tbody>
            </table>
        `;
        
        // وضع الجداول في الحاوية المناسبة
        if (info.category === 'Other') {
            otherContainer.appendChild(categoryDiv);
        } else {
            gridContainer.appendChild(categoryDiv);
        }
        
        const tableBody = categoryDiv.querySelector('tbody');
        
        if (points.length === 0) {
            tableBody.innerHTML = '<tr><td colspan="2" style="text-align: center; color: #777;">لا توجد مواقع في هذه الفئة.</td></tr>';
            return;
        }

        points.forEach((p, index) => {
            // البحث عن الفهرس الأصلي في savedPoints
            const globalIndex = savedPoints.findIndex(sp => sp.name === p.name && sp.lat === p.lat && sp.lng === p.lng); 
            
            const row = tableBody.insertRow();
            // عند النقر على الصف، يتم فتح الموقع في الخريطة
            row.onclick = () => openLocation(p.lat, p.lng); 

            let cellName = row.insertCell();
            cellName.textContent = p.name;
            
            let cellAction = row.insertCell();
            cellAction.classList.add('action-col');
            
            const deleteBtn = document.createElement('button');
            deleteBtn.textContent = 'حذف';
            deleteBtn.className = 'delete-btn';
            // استخدام الفهرس الأصلي للحذف مع التأكيد
            deleteBtn.onclick = (event) => {
                event.stopPropagation(); 
                deletePoint(globalIndex); 
            };
            cellAction.appendChild(deleteBtn);
        });
    });
}

// 🛑 تم تصحيح هذه الدالة
function openLocation(lat, lng) {
    // بناء الرابط باستخدام الصيغة القياسية لخرائط جوجل: /@lat,lng,zoom
    // تم استخدام زوم 19 لتموضع أدق
    // **تم تصحيح بناء الرابط**
    let url = `http://maps.google.com/?q=${lat},${lng}&ll=${lat},${lng}&z=19`; 
    window.open(url, "_blank");
}

// ✅ حذف موقع (بدون كلمة مرور)
function deletePoint(index) {
    if (index === -1) {
        alert("❌ فشل في تحديد الموقع المراد حذفه.");
        return;
    }
    
    // 💡 تم حذف طلب الكود
    const confirmDelete = confirm(`هل أنت متأكد من حذف الموقع "${savedPoints[index].name}"؟`);
    
    if (confirmDelete) {
        savedPoints.splice(index, 1); 
        savePointsToStorage(); 
        alert("✔ تم الحذف بنجاح.");
        renderPointsTable(); 
    } else {
        alert("تم إلغاء الحذف.");
    }
}

// ✅ تحديد موقعي (مع دقة عالية ووقت انتظار) - **تم حذف الـ Alert**
function locateMe() {
  if (!navigator.geolocation) {
    alert("❌ المتصفح لا يدعم تحديد الموقع الجغرافي.");
    return;
  }
  
  const options = {
    enableHighAccuracy: true,
    timeout: 10000, 
    maximumAge: 0 
  };
  
  // تم حذف: alert("جاري محاولة تحديد موقعك بدقة عالية... الرجاء الانتظار."); 

  navigator.geolocation.getCurrentPosition(pos => {
    openLocation(pos.coords.latitude, pos.coords.longitude);
  }, (error) => {
    let errorMessage = "❌ تعذر تحديد موقعك بدقة. تأكد من تفعيل خدمة الموقع.";
    if (error.code === error.PERMISSION_DENIED) {
        errorMessage = "❌ رفضت الوصول إلى الموقع الجغرافي. تأكد من إعطاء الإذن للمتصفح.";
    } else if (error.code === error.TIMEOUT) {
        errorMessage = "❌ انتهت مهلة تحديد الموقع. حاول مجدداً في مكان ذو إشارة أفضل.";
    }
    alert(`${errorMessage} (${error.message})`);
  }, options);
}

// ✅ حفظ موقعي (بدون كلمة مرور) - **تم حذف الـ Alert**
function saveMyLocation() {
    // 💡 تم حذف طلب الكود
    
    if (!navigator.geolocation) {
        alert("❌ المتصفح لا يدعم تحديد الموقع الجغرافي.");
        return;
    }
    
    // تم حذف: alert("جاري محاولة تحديد موقعك بدقة عالية للحفظ... الرجاء الانتظار."); 
    
    const options = {
        enableHighAccuracy: true,
        timeout: 10000, 
        maximumAge: 0 
    };

    navigator.geolocation.getCurrentPosition(pos => {
        let name = prompt("الرجاء إدخال اسم للموقع المحفوظ (مثال: PK100):");
        if (!name || name.trim() === "") return;
        
        const trimmedName = name.trim();
        if (savedPoints.some(p => p.name.trim() === trimmedName)) {
            alert("❌ هذا الاسم موجود بالفعل. اختر اسماً آخر.");
            return;
        }

        savedPoints.push({
            name: trimmedName, 
            lat: pos.coords.latitude,
            lng: pos.coords.longitude
        });

        savePointsToStorage(); 
        alert("✔ تم الحفظ بنجاح.");
        renderPointsTable(); 
    }, (error) => {
        let errorMessage = "❌ تعذر تحديد موقعك بدقة للحفظ. تأكد من تفعيل خدمة الموقع.";
        if (error.code === error.PERMISSION_DENIED) {
            errorMessage = "❌ رفضت الوصول إلى الموقع الجغرافي. تأكد من إعطاء الإذن للمتصفح.";
        } else if (error.code === error.TIMEOUT) {
            errorMessage = "❌ انتهت مهلة تحديد الموقع. حاول مجدداً في مكان ذو إشارة أفضل.";
        }
        alert(`${errorMessage} (${error.message})`);
    }, options);
}


// 🛑 تم تصحيح هذه الدالة لمعالجة مشكلة الفاصلة العشرية
function promptForManualLocation() {
    // 1. طلب اسم الموقع
    let name = prompt("الرجاء إدخال اسم للموقع المحفوظ (مثال: PK100):");
    if (!name || name.trim() === "") {
        alert("❌ الاسم مطلوب. تم إلغاء عملية الحفظ.");
        return;
    }
    
    const trimmedName = name.trim();
    if (savedPoints.some(p => p.name.trim() === trimmedName)) {
        alert("❌ هذا الاسم موجود بالفعل. اختر اسماً آخر.");
        return;
    }

    // 2. طلب الإحداثيات
    let coordsInput = prompt(
        "الرجاء لصق الإحداثيات بصيغة (خط العرض, خط الطول).\n" +
        "مثال (من الخريطة): 32,8528783, -6,9326862"
    );
    
    if (!coordsInput || coordsInput.trim() === "") {
        alert("❌ الإحداثيات مطلوبة. تم إلغاء عملية الحفظ.");
        return;
    }

    // دالة مساعدة لتنظيف الأرقام: استبدال جميع الفواصل (، أو ,) بنقطة (.).
    const cleanNumber = (str) => {
        return str.replace(/[\,\،]/g, '.');
    };

    // 3. معالجة الإحداثيات والتحقق منها (التصحيح الرئيسي)
    let cleanedInput = coordsInput.trim(); 
    let parts = [];

    // محاولة التقسيم باستخدام الفاصل الذي يسبق علامة السالب (إذا كانت موجودة)
    const negSeparatorIndex = cleanedInput.indexOf(', -');
    
    if (negSeparatorIndex !== -1) {
        // إذا وجدنا الفاصل ', -' (وهو شائع في الإدخال المحلي)
        const latPart = cleanedInput.substring(0, negSeparatorIndex);
        const lngPart = cleanedInput.substring(negSeparatorIndex + 2); 
        parts = [latPart, lngPart];
    } else {
        // إذا كانت الإحداثيات موجبة أو صيغة الإدخال مختلفة:
        // نبحث عن آخر فاصلة (لنفترض أنها فاصلة الإحداثيات وليس العشرية)
        const lastCommaIndex = cleanedInput.lastIndexOf(',');
        
        // إذا كان هناك أكثر من فاصلة واحدة، نعتبر الفاصلة الأخيرة هي فاصل الإحداثيات
        if (lastCommaIndex !== -1 && cleanedInput.indexOf(',') !== lastCommaIndex) {
            const latPart = cleanedInput.substring(0, lastCommaIndex);
            const lngPart = cleanedInput.substring(lastCommaIndex + 1);
            parts = [latPart, lngPart];
        } else {
            // في حالة عدم وجود فاصلتين (أي أن المدخل بصيغة دولية بالنقاط أو فاصلة واحدة فقط)
            const basicSplit = cleanedInput.split(/[\,\،]\s*/).filter(p => p.trim() !== '');
            if (basicSplit.length === 2) {
                parts = basicSplit;
            }
        }
    }
    
    if (parts.length < 2) {
        alert("❌ صيغة الإحداثيات غير صحيحة. يجب إدخال (خط العرض, خط الطول). تم إلغاء عملية الحفظ.");
        return;
    }

    // 4. تنظيف كل جزء على حدة وتحويل الفواصل العشرية إلى نقاط
    const lat = parseFloat(cleanNumber(parts[0]));
    const lng = parseFloat(cleanNumber(parts[1]));

    if (isNaN(lat) || isNaN(lng)) {
        alert("❌ صيغة الإحداثيات غير صحيحة بعد المعالجة. يرجى التأكد من أن الأرقام صحيحة. تم إلغاء عملية الحفظ.");
        return;
    }

    // 5. حفظ النقطة
    savedPoints.push({
        name: trimmedName, 
        lat: lat,
        lng: lng
    });

    savePointsToStorage(); 
    alert(`✔ تم حفظ الموقع "${trimmedName}" بنجاح.\nالإحداثيات المحفوظة: ${lat}, ${lng}`);
    renderPointsTable();
}


// ✅ بحث (تصفية مباشرة في الجداول)
function searchLocation() {
  let txt = document.getElementById("searchBox").value.trim();
  const cancelBtn = document.getElementById("cancelSearchBtn");

  if (!txt) {
    // إذا كان مربع البحث فارغًا، اعرض الكل
    clearSearch();
    return;
  }

  const searchLower = txt.toLowerCase();

  // تصفية المواقع بناءً على تطابق الاسم
  currentPointsToDisplay = savedPoints.filter(p => 
    p.name.toLowerCase().includes(searchLower)
  );
  
  if (currentPointsToDisplay.length === 0) {
    // لا نعرض alert في حالة عدم وجود نتائج ونكتفي بعرض جداول فارغة
    // alert(`❌ لا يوجد موقع يحتوي اسمه على "${txt}".`);
  }

  // إعادة عرض الجداول بالنتائج المفلترة
  renderPointsTable();
  
  // إظهار زر الإلغاء
  cancelBtn.style.display = 'flex';
}

// ✅ إلغاء البحث والعودة إلى العرض الكامل
function clearSearch() {
  document.getElementById("searchBox").value = "";
  document.getElementById("cancelSearchBtn").style.display = 'none';
  
  // التحقق مما إذا كانت قائمة العرض مختلفة عن القائمة الكاملة
  if (currentPointsToDisplay.length !== savedPoints.length || (currentPointsToDisplay !== savedPoints && savedPoints.length > 0)) {
    currentPointsToDisplay = savedPoints;
    renderPointsTable(); 
  }
  // في حالة عدم وجود أي نقاط محفوظة (savedPoints.length = 0)، لا حاجة لإعادة العرض.
}
</script>

</body>
</html>
