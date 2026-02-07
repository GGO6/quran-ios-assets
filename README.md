# أصول تطبيق مصحف iOS (quran-ios-assets)

هذا المجلد يحتوي كل الملفات الكبيرة التي يمكن رفعها إلى ريبو منفصل وتحميلها عند أول فتح للتطبيق.

## المحتويات (~229 MB)

| المسار | الوصف | الحجم التقريبي |
|--------|--------|----------------|
| **quran.json** | نص القرآن (سور وآيات) | ~1.9 MB |
| **reciters.json** | قائمة القراء ومصادر الصوت | ~12 KB |
| **qpc-v2-15-lines.db** | قاعدة بيانات ترقيم المصحف (604 صفحة) | ~236 KB |
| **qpc-v2.json** | غليفات الكلمات (مزامنة التلاوة) | ~7.8 MB |
| **qpc-v2-ayah-by-ayah-glyphs.json** | غليفات الآيات للصفحة المدنية | ~896 KB |
| **QPCFonts/** | خطوط مصحف المدينة (604 ملف .ttf، صفحة لكل خط) | ~200 MB |
| **MadinahPages/** | نصوص صفحات المصحف (page_001.txt … page_604.txt) | ~2.4 MB |
| **RecitationSegments/** | مقاطع التلاوة كلمة بكلمة (8 ملفات: JSON + DB) | ~17 MB |

## رفع إلى GitHub

1. أنشئ ريبو جديداً (مثلاً `quran-ios-assets`).
2. ارفع محتويات هذا المجلد بحيث تكون الملفات في جذر الريبو أو تحته.
3. Base URL للتحميل (Raw) يكون مثل:  
   `https://raw.githubusercontent.com/USERNAME/quran-ios-assets/main`

## التوافق مع التطبيق

التطبيق يحمّل كل الملفات أعلاه عند أول فتح (إن لم تكن في الـ Bundle)، ويخزنها في Application Support. الخدمات تقرأ من المسار المحمّل أولاً ثم الـ Bundle:

- **الملفات الجذرية** → `QuranAppData/`
- **QPCFonts** → `QuranAppData/QPCFonts/`
- **MadinahPages** → `QuranAppData/MadinahPages/`
- **RecitationSegments** → `QuranAppData/RecitationSegments/`

يجب أن يطابق هيكل الريبو هذا بالضبط (نفس أسماء المجلدات والملفات).
