# Habitly — Team Split

| # | الشخص | Name | المسؤولية | الملفات |
|---|---|---|---|---|
| 1 | أحمد ابراهيم شعبان | Ahmed Ibrahim Shaaban | Core / Infra Lead — Tokens + Components + Data Layer + Router | `tokens.css`, `components.css`, `data.js`, `router.js`, `index.html` |
| 2 | داليا سامى عبدالعزيز | Dalia Samy Abdelaziz | Dashboard | `dashboard.html/css/js` |
| 3 | نهلة ياسر عرفات عبد الحي | Nahla Yasser Arafat Abdelhay | My Habits | `habits.html/css/js` |
| 4 | بسملة حسن عبدالله | Basmala Hassan Abdallah | Statistics | `stats.html/css/js` |
| 5 | منال عزت احمد جاد | Manal Ezzat Ahmed Gad | Settings + Recommendations | `settings.html/css/js`, `recommendations.js` |

## Rules of Engagement
- Only the Core Lead reads/writes `data.js`. Anyone needing a new function should request it from the Core Lead.
- No hardcoded CSS values — everything must come from `tokens.css`.
- Anyone doing a major restructure of `data.js` or `tokens.css` should confirm the two layers exist and coordinate with whoever already built on top of them.
- Each person is responsible for their page being responsive (480px / 780px).
- Git: each person works on their own branch, merged into `main` after Contract Lead sign-off, one day before the deadline.

---

## Design decisions — Q&A for discussion / مناقشة المشروع

Questions an evaluator is likely to ask, and the short answer for each.

**ليه اخترتوا الألوان دي؟ / Why this palette?**
مبنيّة على فكرة "الدفتر اليومي" (ledger) مش "لوحة تحكم تقنية" — خلفية خضراء غامقة قريبة من لون الجلد المدبوغ، ولون ذهبي كلون حبر بدل الأخضر النيون المعتاد في تطبيقات التتبع. القيم كلها متغيرات CSS (`custom properties`) في `tokens.css`، مفيش لون واحد مكتوب يدوي في أي ملف تاني.
*Built around a "ledger" concept, not a tech dashboard — a deep, leather-toned green background with an ink-gold accent instead of the neon-green that's everywhere in habit apps. Every value is a CSS custom property in `tokens.css`; no page hardcodes a color.*

**إيه العنصر المميز في التصميم؟ / What's the signature element?**
حلقة التقدّم (`.seal`) مصممة كـ"ختم شمعي" باستخدام `conic-gradient`، والسلسلة (streak) بتتعرض كعلامات "تالي" (`.tally`) زي العدّ اليدوي في دفتر حقيقي، مجمّعة في خمسات — بدل النقط العادية.
*The progress ring (`.seal`) is styled as a wax-seal stamp using a `conic-gradient`; streaks render as `.tally` marks — grouped in fives like a hand-kept count — instead of plain dots.*

**إزاي الفريق قسم الشغل من غير ما يتعارض؟ / How did the team avoid merge conflicts?**
كل شخص مسؤول عن ملفاته بس (`dashboard.html/css/js` لشخص، `habits.html/css/js` لشخص تاني...)، وملف بيانات واحد مشترك (`data.js`) بيديره الـ Core Lead بس، عشان محدش يكتب أرقام يدوي في صفحته.
*Each person owns their own file set; one shared data file (`data.js`) is edited only by the Core Lead, so nobody hardcodes numbers into their own page.*

**إزاي التطبيق بيدعم اللغة العربية؟ / How does the Arabic toggle work?**
زرار في الهيدر (`js/i18n.js`) بيبدّل بين قاموسين (en/ar)، بيغيّر `dir` و`lang` على الـ `<html>`، ويحفظ الاختيار في `localStorage` عشان يفضل زي ما هو لما تتنقل بين الصفحات. التخطيط بيتقلب تلقائي للـ RTL لأن الـ CSS مبني على خصائص "منطقية" (`margin-inline`, `padding-inline-end`) مش `left`/`right` تقليدية.
*A header button (`js/i18n.js`) swaps between two dictionaries (en/ar), sets `dir`/`lang` on `<html>`, and saves the choice in `localStorage` so it persists across pages. Layout mirrors into RTL automatically because the CSS uses logical properties (`margin-inline`, `padding-inline-end`) instead of hardcoded `left`/`right`.*

**ليه مفيش framework زي React أو Bootstrap؟ / Why no framework?**
عشان الهدف إثبات فهم HTML/CSS/JS الأساسي — كل component (الكارت، الـ pill، الـ progress ring) اتبنى بـ CSS عادي وقابل لإعادة الاستخدام عبر الصفحات كلها من غير أي build step.
*The goal is to demonstrate core HTML/CSS/JS — every component (card, pill, progress ring) is plain, reusable CSS with no build step required.*
