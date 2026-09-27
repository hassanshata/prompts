# Day 02 - Prompt Engineering

## Prompt #1

**الأصلي:**  
`اعملي login`

**الناقص:**  
- Role: مش محدد هل المطلوب Laravel ولا Flutter ولا حاجة تانية.
- Context: مفيش معلومات عن المشروع أو طريقة الـ authentication الحالية.
- Task: كلمة login لوحدها مش موضحة هل المطلوب API ولا UI.
- Constraints: مفيش إصدار ولا ممنوعات.
- Examples: مش ضروري هنا لأن المطلوب standard ومحدد.
- Format: مش محدد شكل الرد.
- Success Criteria: مفيش تعريف واضح إن الـ login نجح إمتى.

**النسخة الكاملة:**

```text
أنت Laravel 11 backend developer وبتشتغل على API موجود بالفعل.
المشروع PHP 8.2 وLaravel 11 وMySQL 8 وبيستخدم Laravel Sanctum.
عندي User model وجدول users فيهم email وpassword.

المطلوب: اكتب login endpoint على POST /api/v1/login يقبل email وpassword،
ولو البيانات صح يرجع user data وtoken، ولو غلط يرجع 401 برسالة واضحة.

القيود:
- استخدم الموجود في Laravel فقط، من غير أي package جديدة.
- ما تغيرش User model ولا شكل جدول users.
- استخدم Form Request للـ validation.
- ما ترجعش password أو أي بيانات حساسة.

المخرج:
1) Route
2) LoginRequest
3) Controller method
4) مثال JSON للـ success والـ error
من غير شرح طويل.

معيار النجاح:
الـ endpoint يرجع 200 + token مع البيانات الصحيحة،
401 مع password غلط، و422 لو email/password ناقصين.

مش محتاج Example إضافي لأن شكل الـ endpoint والـ responses متحدد بالفعل.
```

**مخرج الأصلي (ملخص):**  
طلع login عام وافترض شكل المشروع من نفسه، وركز على form فيها email وpassword من غير ما يعرف أنا شغال بأي framework أو authentication system.

**مخرج المحول (ملخص):**  
طلع endpoint واضح بـ Laravel Sanctum، مع validation وstatus codes محددة وresponse آمن من غير password.

**الفرق:**  
1. الأصلي افترض التقنية، لكن المحول اتقيد بـ Laravel 11 وSanctum.  
2. الأصلي ماكانش واضح فيه الـ validation والـ errors، المحول غطاهم.  
3. المحول طلع ملفات وشكل response ينفع أستخدمهم مباشرة في المشروع.

---

## Prompt #3

**الأصلي:**  
`اكتبلي دالة تحسب الضريبة`

**الناقص:**  
- Role: مش محدد لغة البرمجة أو البيئة.
- Context: مش معروف الدالة هتستخدم فين.
- Task: مش واضح هل ترجع قيمة الضريبة بس ولا الإجمالي بعد الضريبة.
- Constraints: مفيش نوع inputs أو طريقة التعامل مع القيم الغلط.
- Examples: ناقص مثال يوضح الحساب المطلوب.
- Format: مش محدد هل عايز كود فقط ولا شرح.
- Success Criteria: مفيش حالات نقدر نختبر بيها الدالة.

**النسخة الكاملة:**

```text
أنت PHP 8.2 developer.
عندي checkout service وعايز دالة صغيرة تحسب قيمة الضريبة فقط، مش الإجمالي.

اكتب function اسمها calculateTax تستقبل:
- amount: float أو int أكبر من أو يساوي 0
- taxRate: float كنسبة مئوية، مثال 14 يعني 14%

القيود:
- من غير أي package.
- ما تستخدمش global variables.
- لو amount أو taxRate أقل من 0 ارمي InvalidArgumentException.
- النتيجة تتقرب إلى منزلتين عشريتين.

مثال:
calculateTax(1000, 14) => 140.00
calculateTax(250, 10) => 25.00

المخرج: كود PHP فقط للدالة + 3 test cases بسيطة.

معيار النجاح:
الأمثلة اللي فوق تطلع بالقيم المكتوبة،
والـ negative input يرمي exception.
```

**مخرج الأصلي (ملخص):**  
كتب دالة عامة وافترض نسبة ضريبة ثابتة، وما وضحش هل الناتج ضريبة بس ولا السعر بعد الإضافة.

**مخرج المحول (ملخص):**  
كتب دالة reusable بتستقبل المبلغ والنسبة، بتقرب منزلتين وبتتعامل مع القيم السالبة، ومعاها tests واضحة.

**الفرق:**  
1. النسبة بقت input بدل ما النموذج يفترضها.  
2. اتحدد بالظبط الدالة بترجع إيه.  
3. بقى فيه حالات اختبار نعرف منها الدالة صح ولا لأ.

---

## Prompt #4

**الأصلي:**  
`حسنلي الأداء`

**الناقص:**  
- Role: مش محدد نوع الخبرة المطلوبة.
- Context: مفيش كود ولا وصف للمشكلة.
- Task: كلمة الأداء واسعة جدًا.
- Constraints: مش معروف إيه اللي ممنوع يتغير.
- Examples: مش محتاج مثال إضافي لأننا هنحط الكود الحالي والقياس الحالي.
- Format: مش محدد عايز patch ولا شرح.
- Success Criteria: مفيش رقم نقيس عليه التحسن.

**النسخة الكاملة:**

```text
أنت Laravel 11 performance engineer.

عندي endpoint بيرجع آخر 100 order مع اسم العميل وعدد الـ items.
الكود الحالي:

$orders = Order::latest()->take(100)->get();

foreach ($orders as $order) {
    $order->customer_name = $order->user->name;
    $order->items_count = $order->items()->count();
}

return response()->json($orders);

المشكلة إن Laravel Debugbar بيبين حوالي 201 query للطلب الواحد للـ endpoint.

المطلوب: حسن أداء الكود ده فقط وقلل عدد database queries.

القيود:
- Laravel 11 / PHP 8.2 / MySQL 8.
- ما تغيرش شكل JSON الحالي.
- ما تضفش package.
- ما تستخدمش raw SQL إلا لو مفيش حل Eloquent مناسب.
- ما تعملش refactor لملفات مالهاش علاقة.

المخرج:
1) السبب في سطرين بالكتير.
2) الكود المعدل كامل.
3) عدد queries المتوقع بعد التعديل.

معيار النجاح:
نفس البيانات ونفس JSON، وعدد الـ queries يبقى 3 أو أقل.

مش محتاج Example إضافي لأن الكود الحالي والقياس الحالي موجودين.
```

**مخرج الأصلي (ملخص):**  
رد بنصائح عامة زي caching وتقليل الصور وتحسين database من غير ما يعرف أصلًا المشكلة فين.

**مخرج المحول (ملخص):**  
حدد مشكلة N+1 واستخدم eager loading وwithCount، ونزل عدد الـ queries بشكل كبير من غير ما يغير شكل الـ response.

**الفرق:**  
1. الأصلي نصائح عامة، المحول عالج الكود نفسه.  
2. المحول حافظ على شكل الـ JSON بدل ما يقترح refactor كبير.  
3. بقى فيه رقم واضح نقيس بيه التحسن.

---

## Prompt #6

**الأصلي:**  
`ليه الاختبار بيفشل`

**الناقص:**  
- Role: مش محدد framework أو test runner.
- Context: مفيش test ولا error message.
- Task: مش واضح هل المطلوب تفسير ولا تعديل.
- Constraints: مفيش حدود للتعديل.
- Examples: مش ضروري لأن الـ failing test نفسه هو المثال.
- Format: مش محدد شكل التحليل.
- Success Criteria: مش معروف إمتى نعتبر المشكلة اتحلت.

**النسخة الكاملة:**

```text
أنت Laravel 11 developer وخبير في PHPUnit وFeature Tests.

عندي الاختبار ده:

public function test_admin_can_create_user(): void
{
    $admin = User::factory()->create(['role' => 'admin']);

    $response = $this->actingAs($admin, 'sanctum')
        ->postJson('/api/v1/users', [
            'name' => 'Ahmed Ali',
            'email' => 'ahmed@example.com',
        ]);

    $response->assertCreated();
}

والـ endpoint بيستخدم StoreUserRequest وفيه rules:

return [
    'name' => ['required', 'string'],
    'email' => ['required', 'email', 'unique:users,email'],
    'role' => ['required', Rule::in(['admin', 'agent'])],
];

الاختبار بيفشل بـ:
Expected response status code [201] but received 422.

المطلوب: حدد السبب الجذري للفشل واديني أقل تعديل منطقي يخلي الاختبار يعبر عن الـ endpoint الحالي.

القيود:
- ما تشيلش validation من الـ endpoint.
- ما تغيرش rule الخاصة بـ role.
- ما تضفش package.
- ما تعدلش أي كود غير مرتبط بالمشكلة.

المخرج:
- السبب في سطر واحد.
- الجزء المعدل من الاختبار فقط.
- سطر يوضح ليه التعديل صح.

معيار النجاح:
الاختبار يعدي ويرجع 201 مع الحفاظ على validation الحالية.

مش محتاج Example إضافي لأن الاختبار نفسه والـ error موجودين.
```

**مخرج الأصلي (ملخص):**  
طلب مني أشوف الـ error أو الكود لأن مفيش أي معلومات كفاية تحدد سبب الفشل.

**مخرج المحول (ملخص):**  
حدد إن `role` required ومش متبعتة في request، وعدل test data بإضافة role بدل ما يلغي الـ validation.

**الفرق:**  
1. الأصلي ماقدرش يشخص المشكلة لعدم وجود بيانات.  
2. المحول وصل للسبب من الـ test والـ rules والـ status code.  
3. الإصلاح كان صغير ومحدد بدل تغييرات عشوائية في الـ endpoint.

---

## Prompt #7

**الأصلي:**  
`اكتب SQL يجيب الطلبات`

**الناقص:**  
- Role: مش محدد نوع قاعدة البيانات.
- Context: مفيش schema للجداول.
- Task: مش معروف أنهي طلبات بالظبط.
- Constraints: مش محدد شروط التاريخ أو الحالة أو الأداء.
- Examples: محتاج شكل للأعمدة المطلوبة.
- Format: مش محدد هل عايز query بس ولا شرح.
- Success Criteria: مش معروف نتحقق من النتيجة إزاي.

**النسخة الكاملة:**

```text
أنت MySQL 8 developer.

عندي الجداول دي:

users(
    id BIGINT PRIMARY KEY,
    name VARCHAR(100)
)

orders(
    id BIGINT PRIMARY KEY,
    user_id BIGINT,
    status VARCHAR(20),
    created_at DATETIME
)

order_items(
    id BIGINT PRIMARY KEY,
    order_id BIGINT,
    quantity INT,
    unit_price DECIMAL(10,2)
)

المطلوب:
اكتب SQL query ترجع الطلبات المدفوعة فقط خلال آخر 30 يوم،
ومع كل طلب:
order_id, customer_name, created_at, total_amount

total_amount = مجموع quantity * unit_price لكل items الخاصة بالطلب.

القيود:
- MySQL 8.
- ما تستخدمش SELECT *.
- لازم تشتغل مع ONLY_FULL_GROUP_BY.
- الطلب يظهر مرة واحدة فقط حتى لو فيه أكتر من item.

مثال شكل النتيجة:
order_id | customer_name | created_at | total_amount

المخرج: SQL query فقط.

معيار النجاح:
مفيش duplicate orders،
وtotal_amount يتحسب من كل items،
وأي order حالته غير paid ما يظهرش.
```

**مخرج الأصلي (ملخص):**  
كتب `SELECT * FROM orders;` تقريبًا، لأن مفيش أي شروط أو معلومات عن الجداول.

**مخرج المحول (ملخص):**  
طلع query فيها joins وSUM وGROUP BY وفيلتر status والتاريخ، وطلعت الأعمدة المطلوبة فقط.

**الفرق:**  
1. الأصلي جاب كل الطلبات من غير معنى محدد.  
2. المحول استخدم schema الحقيقي وعرف العلاقات.  
3. الناتج بقى جاهز للحالة المطلوبة ومفيهوش duplicates.

---

## Prompt #9

**الأصلي:**  
`ترجم الملف ده`

**الناقص:**  
- Role: مش محدد نوع الترجمة.
- Context: مش معروف نوع الملف ولا الجمهور.
- Task: مش محدد من أنهي لغة لأنهي لغة.
- Constraints: مش معروف إيه اللي لازم يفضل زي ما هو.
- Examples: مثال صغير مفيد لتثبيت طريقة التعامل مع المصطلحات.
- Format: لازم يحافظ على Markdown.
- Success Criteria: محتاج شروط تمنع كسر الكود والروابط.

**النسخة الكاملة:**

```text
أنت technical translator فاهم software documentation.

ترجم محتوى README.md التالي من English إلى Arabic لمطورين مبتدئين:

# Setup

Run `npm install` first.

Create a `.env` file and add:
- `API_URL`
- `APP_KEY`

Then run:

```bash
npm run dev
```

For more details, check [Laravel Docs](https://laravel.com/docs).

المطلوب:
ترجم النص البشري للعربي فقط.

القيود:
- ما تترجمش أسماء الأوامر أو الملفات أو environment variables.
- ما تغيرش أي code block.
- ما تغيرش URLs.
- خليك محافظ على نفس Markdown headings والقوائم.
- استخدم عربي بسيط، وسيب المصطلحات التقنية المشهورة بالإنجليزي لو ترجمتها هتبقى غريبة.

مثال:
"Run the migration" => "شغّل الـ migration"

المخرج:
نفس الملف Markdown كامل بعد الترجمة فقط، من غير شرح قبل أو بعد.

معيار النجاح:
`npm install`, `.env`, `API_URL`, `APP_KEY`, `npm run dev` والرابط يفضلوا زي ما هم بالحرف،
والـ Markdown يفضل سليم.
```

**مخرج الأصلي (ملخص):**  
سأل عن الملف أو بدأ يترجم بشكل عام من غير ما يعرف اللغة المطلوبة أو الحاجات اللي ممنوع تتغير.

**مخرج المحول (ملخص):**  
ترجم النصوص البشرية للعربي وحافظ على commands والـ variables والـ links والـ Markdown زي ما هي.

**الفرق:**  
1. اتجاه الترجمة بقى محدد.  
2. العناصر التقنية الحساسة بقت محمية من الترجمة.  
3. الناتج بقى ينفع أرجعه مكان README مباشرة.

---

## Prompt #10

**الأصلي:**  
`اشرح Laravel`

**الناقص:**  
- Role: مش محدد مستوى الشرح.
- Context: مش معروف أنا مبتدئ ولا عندي خبرة.
- Task: Laravel موضوع واسع جدًا ومحتاج scope.
- Constraints: لازم نحدد طول ومستوى المصطلحات.
- Examples: مش ضروري لأن ده شرح تعليمي مش تصنيف أو output ثابت.
- Format: محتاج ترتيب يسهل المذاكرة.
- Success Criteria: لازم يبقى فيه طريقة أعرف إني فهمت الأساسيات.

**النسخة الكاملة:**

```text
أنت مدرس Laravel 11 لمطور بيعرف أساسيات PHP لكن أول مرة يشتغل framework.

اشرحلي Laravel من ناحية الأساسيات اللي أحتاجها عشان أفهم مشروع API بسيط.
ركز فقط على:
1) Routing
2) Controllers
3) Models وEloquent
4) Migrations
5) Form Requests
6) Resources
7) Request lifecycle بشكل مبسط

القيود:
- Laravel 11.
- ما تدخلش في queues أو events أو broadcasting.
- استخدم لغة بسيطة ومصطلحات إنجليزي جنب العربي.
- الشرح كله مايزدش عن 900 كلمة.

المخرج:
- كل نقطة بعنوان صغير.
- تحت كل نقطة شرح مختصر.
- مثال كود صغير لما يكون مفيد.
- في الآخر 5 أسئلة مراجعة من غير إجابات.

معيار النجاح:
بعد الشرح أقدر أحدد request بيمشي من route لحد controller/model والـ response،
وأفهم وظيفة كل عنصر من السبعة.

مش محتاج Example إضافي لأن المطلوب شرح تعليمي والنطاق وشكل الناتج متحددين.
```

**مخرج الأصلي (ملخص):**  
طلع شرح واسع جدًا عن Laravel وتاريخه ومميزاته وMVC وحاجات كتير مش كلها مهمة للي أنا محتاجه.

**مخرج المحول (ملخص):**  
ركز على أجزاء محددة أحتاجها في API project، ورتبهم بشكل سهل ومع أمثلة قصيرة وأسئلة مراجعة.

**الفرق:**  
1. الأصلي كان واسع ومشتت، المحول حدد scope واضح.  
2. الشرح اتظبط على مستوى شخص فاهم PHP ولسه جديد في Laravel.  
3. بقى فيه معيار واضح أعرف منه هل فهمت الأساسيات ولا لأ.
