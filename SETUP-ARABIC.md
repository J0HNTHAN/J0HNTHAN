# دليل الإعداد الكامل — J0HNTHAN GitHub Profile

---

## 🗂️ الملفات اللي هتحتاجها

```
johnthan-github-profile/
│
├── README.md                              ← صفحة البروفايل نفسها
├── ACTIVITY.md                            ← سجل النشاط (البوت بيحدثه)
│
└── .github/
    └── workflows/
        ├── activity-tracker.yml           ← بيتحدث عند كل push
        ├── pr-commenter.yml               ← بيكتب كومنت على كل PR
        └── generate-snake.yml             ← بيعمل أنيميشن الثعبان
```

---

## 🪜 الخطوات خطوة بخطوة

---

### ● الخطوة 1 — عمل الـ Repository الخاص بالبروفايل

ده أهم خطوة. GitHub عندها ميزة خاصة: لو عملت Repository اسمه **نفس اسم اليوزرنيم بتاعك**، المحتوى بتاعه بيظهر تلقائياً في صفحة البروفايل.

1. روح على **github.com** وادخل على حسابك
2. اضغط الـ **"+"** في أعلى الشاشة يمين → اختار **"New repository"**
3. في خانة **"Repository name"** اكتب بالظبط: `J0HNTHAN`
   - (نفس حرف كبير وصغير زي اليوزرنيم)
4. اختار **"Public"** (لازم تكون Public عشان تبان)
5. **تيك على "Add a README file"**
6. اضغط **"Create repository"**

> ✅ هتلاقي GitHub قالك: *"J0HNTHAN/J0HNTHAN is a special repository..."* ده معناه صح!

---

### ● الخطوة 2 — رفع الملفات على الـ Repository

#### الطريقة السهلة (drag & drop):

1. افتح الـ repository اللي عملته
2. احذف الـ `README.md` الموجود
3. اسحب وودّع الملفات التالية:
   - `README.md` (من المجلد اللي حملته)
   - `ACTIVITY.md`
4. اضغط **"Commit changes"**

#### الطريقة بالـ Git (لو عندك Git مثبت):

افتح الـ terminal أو CMD وانسخ الأوامر دي:

```bash
# ── نزّل الـ repo على جهازك ──
git clone https://github.com/J0HNTHAN/J0HNTHAN.git
cd J0HNTHAN

# ── انسخ الملفات من المجلد اللي حملته ──
# (اضبط الـ path حسب مكان المجلد عندك)
copy "C:\path\to\johnthan-github-profile\README.md" .
copy "C:\path\to\johnthan-github-profile\ACTIVITY.md" .

# ── ارفع التغييرات ──
git add .
git commit -m "✨ Setup profile README"
git push origin main
```

---

### ● الخطوة 3 — رفع ملفات الـ Workflows

الـ workflows محتاجة تكون في مجلد اسمه بالظبط `.github/workflows/`

#### طريقة سهلة عن طريق GitHub مباشرة:

1. في الـ repository، اضغط على **"Add file"** → **"Create new file"**
2. في خانة الاسم اكتب: `.github/workflows/activity-tracker.yml`
   - GitHub هيعمل المجلدات تلقائياً لما تكتب الـ `/`
3. الصق المحتوى من ملف `activity-tracker.yml`
4. اضغط **"Commit new file"**
5. كرر نفس الكلام مع `pr-commenter.yml` و `generate-snake.yml`

---

### ● الخطوة 4 — تفعيل الـ Workflows

1. افتح الـ repository
2. اضغط على تبويبة **"Actions"** في الأعلى
3. لو ظهرت رسالة بتسألك تفعّل الـ Actions، اضغط **"I understand my workflows, go ahead and enable them"**
4. ✅ خلاص! الـ workflows هتشتغل تلقائياً من دلوقتي

---

### ● الخطوة 5 — تشغيل الـ Snake لأول مرة

الثعبان محتاج يتولد مرة بيدك الأول:

1. روح على **Actions**
2. في الشريط الأيسر اختار **"· Contribution Snake ·"**
3. اضغط **"Run workflow"** → **"Run workflow"**
4. استنى دقيقة وتاني صفحة → هيظهر ✅ أخضر
5. ✅ الثعبان اتولد وهيبان في البروفايل!

---

### ● الخطوة 6 — تعديل معلوماتك في الـ README

افتح `README.md` وعدّل الأجزاء دي:

| مكان في الملف | اللي هتغيره |
|---------------|-------------|
| `role` في الـ yaml block | شغلتك / مسماك الوظيفي |
| `location` | مدينتك |
| `currently` | البروجكت اللي شغال عليه |
| بادج الـ LinkedIn | لينك الـ LinkedIn بتاعك |
| `your@email.com` | الإيميل بتاعك |
| رابط الـ PracticalWebApp | لينك الـ repo الصح |

---

### ● الخطوة 7 — Pinned Repositories (اختياري)

عشان تثبّت أهم بروجكتاتك في صفحة البروفايل:

1. روح على **github.com/J0HNTHAN** (صفحتك الشخصية)
2. اضغط **"Customize your pins"**
3. اختار أهم 6 repos تحب تعرضهم
4. اضغط **"Save pins"**

---

## ✅ التحقق من إن كل شيء شغال

بعد ما ترفع الملفات، اعمل أي commit بسيط في أي repo عندك. بعد دقيقتين:

1. روح على **Actions** في الـ J0HNTHAN repository
2. المفروض تلاقي workflow اشتغل وعليه ✅
3. روح على **README.md** — المفروض الـ Activity Log اتغير
4. روح على صفحة **github.com/J0HNTHAN** — المفروض الصفحة تبان

---

## 🛠️ لو في مشكلة

| المشكلة | الحل |
|---------|------|
| الـ workflow بيفشل | روح Actions → افتح الـ run الفاشل → شوف السطر الأحمر |
| الثعبان مش بيبان | تأكد إن الـ generate-snake.yml اتشغل وعمل branch اسمه `output` |
| الـ stats cards مش بتظهر | اللينكات بتاعت `github-readme-stats` بتاخد وقت، استنى دقائق |
| الـ README مش بيبان في البروفايل | تأكد إن اسم الـ repo بالظبط نفس اليوزرنيم |

---

## 🎨 أيقونات وعناصر زيادة ممكن تضيفها

```
# Dividers
· · · · · · · · · · · · · · · · · · · · ·
░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

# Bullet markers
◈ ◉ ● ◦ ·  ▸ ▹ ► ◆ ◇ ✦ ✧

# Box corners
┌─┐   ╔═╗   ╭─╮
│ │   ║ ║   │ │
└─┘   ╚═╝   ╰─╯
```

---

_ملف الإعداد ده اتعمل خصيصاً لـ J0HNTHAN 🇪🇬_
