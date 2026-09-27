# My Prompt Templates

القوالب دي معمولة عشان أستخدمها في الشغل بدل ما أبدأ كل مرة من الصفر.  
كل حاجة بين `[ ]` بتتغير حسب المهمة.

---

## 1) Laravel Bug Fix

```text
أنت Laravel [VERSION] developer.

السياق:
المشروع PHP [PHP_VERSION] وLaravel [VERSION] وDatabase [DB].
المشكلة بتحصل في [FEATURE / ENDPOINT].

الكود:
[PASTE CODE]

الخطأ:
[PASTE ERROR]

المطلوب:
حدد السبب الجذري للمشكلة واعمل أقل تعديل ممكن لإصلاحها.

القيود:
- ما تضفش packages.
- ما تغيرش public function signatures.
- ما تعملش refactor لملفات مالهاش علاقة.
- حافظ على السلوك الحالي لباقي الكود.

مثال لشكل الإجابة:
السبب: ...
التعديل: ...

المخرج:
1) السبب في نقاط قصيرة.
2) الكود المعدل فقط.
3) طريقة سريعة أختبر بيها الإصلاح.

معيار النجاح:
الخطأ يختفي والـ tests الحالية تفضل شغالة.
```

---

## 2) Laravel API Endpoint

```text
أنت Laravel [VERSION] backend developer.

المشروع:
[AUTH METHOD]
[DATABASE]
[EXISTING MODELS / TABLES]

المطلوب:
اكتب endpoint:
[METHOD] [URL]

الـ input:
[FIELDS + VALIDATION]

الـ output:
[EXPECTED RESPONSE]

القيود:
- استخدم Form Request وAPI Resource.
- ما تضفش package.
- ما تغيرش ملفات موجودة إلا لو ذكرتها.
- استخدم status codes مناسبة.

مثال response:
[OPTIONAL JSON EXAMPLE]

المخرج:
الملفات المطلوبة كاملة من غير شرح طويل.

معيار النجاح:
[SUCCESS CASE]
[VALIDATION CASE]
[AUTH CASE]
```

---

## 3) MySQL Query Builder

```text
أنت MySQL 8 developer.

Schema:
[PASTE TABLES + IMPORTANT COLUMNS]

المطلوب:
اكتب query تعمل:
[WHAT DATA I NEED]

الشروط:
[FILTERS]
[SORTING]
[DATE RANGE]
[GROUPING]

القيود:
- MySQL 8.
- ما تستخدمش SELECT *.
- لازم تشتغل مع ONLY_FULL_GROUP_BY.
- تجنب subqueries لو join أو aggregation أوضح.

مثال شكل الناتج:
[COLUMN_1 | COLUMN_2 | COLUMN_3]

المخرج:
SQL فقط، وبعده سطر واحد لو فيه index مهم جدًا.

معيار النجاح:
[NO DUPLICATES / CORRECT TOTAL / PERFORMANCE CONDITION]
```

---

## 4) Flutter API Integration

```text
أنت Flutter developer شغال بـ Dart [VERSION].

السياق:
عندي screen اسمها [SCREEN NAME].
الـ API:
[METHOD] [URL]
بيرجع:
[JSON RESPONSE]

المطلوب:
اربط الـ screen بالـ API واعرض البيانات.

الحالات المطلوبة:
- loading
- success
- empty
- error

القيود:
- استخدم الـ state management الموجود عندي: [PROVIDER / BLOC / RIVERPOD / SETSTATE].
- ما تضفش package جديدة.
- ما تغيرش شكل الـ API model من غير سبب.
- null safety لازم تفضل سليمة.

مثال:
[OPTIONAL MODEL OR JSON]

المخرج:
الملفات أو الأجزاء المعدلة فقط.

معيار النجاح:
البيانات تظهر صح، وكل الحالات الأربع ليها UI واضح، ومفيش crash لو response فاضي.
```

---

## 5) Next.js Page

```text
أنت Next.js [VERSION] + TypeScript developer.

المشروع بيستخدم:
[APP ROUTER / PAGES ROUTER]
[UI LIBRARY OR CSS METHOD]
[AUTH IF ANY]

المطلوب:
اعمل صفحة [PAGE NAME] تعرض [DATA / FEATURE].

الحالات:
- loading
- empty
- error
- success

القيود:
- ما تستخدمش any.
- ما تضفش package.
- حافظ على الـ components الموجودة.
- استخدم Server Component أو Client Component حسب الحاجة فقط.

مثال للشكل أو الـ data:
[OPTIONAL EXAMPLE]

المخرج:
الكود كامل للملفات الجديدة، والتعديلات الضرورية فقط في الملفات القديمة.

معيار النجاح:
TypeScript يمر من غير errors والصفحة تغطي الحالات الأربع.
```

---

## 6) Performance Review

```text
أنت performance engineer متخصص في [LARAVEL / NEXT.JS / MYSQL].

المشكلة:
[DESCRIBE SLOW PART]

القياس الحالي:
[QUERY COUNT / RESPONSE TIME / MEMORY / BUILD SIZE]

الكود:
[PASTE CODE]

المطلوب:
حدد أكبر سبب مؤثر على الأداء واعمل تعديل مركز عليه.

القيود:
- ما تغيرش الـ public behavior.
- ما تضفش package.
- ما تعملش optimization نظري من غير دليل من الكود.
- حافظ على readability.

مثال للهدف:
response time من [X] إلى أقل من [Y].

المخرج:
1) السبب.
2) الكود أو الـ diff.
3) قبل/بعد المتوقع.

معيار النجاح:
[MEASURABLE TARGET]
```

---

## 7) Failing Test Analysis

```text
أنت [FRAMEWORK] developer وخبير في testing.

الاختبار:
[PASTE TEST]

الخطأ:
[PASTE ERROR / ASSERTION]

الكود المرتبط:
[PASTE CONTROLLER / SERVICE / FUNCTION]

المطلوب:
حدد ليه الاختبار بيفشل، وبعدها اقترح أقل تعديل صحيح.

القيود:
- ما تلغيش validation أو authorization عشان تعدي الاختبار.
- ما تحذفش test.
- ما تضفش package.
- فرق بين bug في الكود وtest expectation غلط.

مثال لشكل الرد:
السبب: ...
مكان المشكلة: ...

المخرج:
سبب مختصر + التعديل فقط + سبب اختيار التعديل.

معيار النجاح:
الاختبار يعدي من غير ما نكسر behavior صحيح موجود.
```

---

## 8) cPanel Deployment Check

```text
أنت Linux/cPanel deployment engineer وعندك خبرة في نشر [LARAVEL / NEXT.JS / PHP].

السياق:
الاستضافة: [CPANEL HOSTING DETAILS]
الدومين: [DOMAIN OR SUBDOMAIN]
الإصدار: [PHP / NODE VERSION]
المشكلة: [ERROR OR CURRENT STATUS]

المطلوب:
حدد خطوات النشر أو إصلاح المشكلة على cPanel بالترتيب.

القيود:
- ما تفترضش SSH لو أنا ما قلتش إنه متاح.
- ما تطلبش تغيير DNS إلا لو ضروري.
- ما تضفش services خارجية.
- أي command لازم يكون متوافق مع البيئة المذكورة.

مثال:
لو SSH غير متاح، استخدم File Manager وTerminal الموجودين في cPanel فقط.

المخرج:
خطوات مرقمة، وكل خطوة فيها مكان التنفيذ بالظبط.

معيار النجاح:
الموقع يفتح من الدومين المحدد والـ production error يختفي.
```

---

## 9) Technical File Translation

```text
أنت technical translator فاهم software development.

ترجم الملف التالي من [SOURCE LANGUAGE] إلى [TARGET LANGUAGE]:
[PASTE FILE CONTENT]

الجمهور:
[DEVELOPERS / CLIENT / BEGINNERS]

القيود:
- ما تغيرش code blocks.
- ما تترجمش variable names أو commands أو URLs.
- حافظ على Markdown / JSON structure.
- سيب المصطلحات التقنية المشهورة بالإنجليزي لو ده أوضح.

مثال:
[ONE SHORT TRANSLATION EXAMPLE]

المخرج:
الملف بعد الترجمة فقط، بنفس التنسيق.

معيار النجاح:
كل الكود والـ identifiers والـ links يفضلوا بالحرف، والنص البشري فقط هو اللي يتترجم.
```

---

## 10) Code Review From Another Role

```text
أنت reviewer متشكك ومتخصص في [SECURITY / PERFORMANCE / CLEAN CODE].

السياق:
الـ stack هو [STACK].
الكود ده بيعمل [PURPOSE].

الكود:
[PASTE CODE]

المطلوب:
راجع الكود من زاوية [SECURITY / PERFORMANCE / CLEAN CODE] فقط.

القيود:
- ما تعيدش كتابة المشروع كله.
- ما تعتبرش اختلاف style bug.
- أي مشكلة تذكرها لازم تربطها بسطر أو behavior واضح.
- صنف المشكلة High / Medium / Low بناءً على تأثيرها داخل الكود ده فقط.

مثال لشكل المشكلة:
المشكلة: ...
المكان: ...
التأثير: ...
التعديل المقترح: ...

المخرج:
حد أقصى 5 مشاكل، وبعدهم أهم تعديل أبدأ بيه.

معيار النجاح:
كل نقطة تكون قابلة للتنفيذ ومبنية على الكود الموجود، من غير افتراضات خارجية.
```
