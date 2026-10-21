# Mandarin public metadata

This repository contains public news and update metadata only. It contains no application source code, APKs, credentials, private repository history, or private release details.

Base URL: `https://raw.githubusercontent.com/SENESO/mandarin-player-updates/main/`

## News

`metadata.json` is the public news index consumed by Mandarin. An empty array means there are no published announcements. There is no fallback to another project's news.

Each future news entry uses these fields: `id`, `Title`, `Description`, `ImageURL` (an array of public image URLs), `Important` (boolean), `Author`, and `Date` (Unix timestamp in milliseconds). Its Markdown article is served at `content/<id>`, using the exact same identifier. Publish only reviewed public announcements. Use Arabic and English text as appropriate; never put tokens or private links in news.

## Update metadata

`updates.json` is a reserved, inactive metadata manifest. `enabled: false` and null channels advertise no available update. This file does not enable polling or installation in any app. The current application updater does not consume this manifest yet; integration and a versioned release contract require their own validation.

No public APK or active update will be added until startup/device validation and complete end-to-end update checks pass. Any future binary distribution must provide the matching GPL source archive in a separate distribution channel; no application source belongs in this metadata repository.

## بالعربية

هذا المستودع العام مخصص لبيانات الأخبار والتحديثات فقط، ولا يحتوي على كود التطبيق أو ملفات APK أو توكنات أو تاريخ التطوير أو بيانات إصدارات خاصة.

ملف `metadata.json` هو فهرس الأخبار، وهو فارغ إلى أن تُنشر أخبار فعلية معتمدة. ملف `updates.json` محجوز للتكامل لاحقًا ومعطّل؛ إنشاؤه لا يفعّل التحديث التلقائي في التطبيق. يظل مستودع التطوير خاصًا، ولا يُنشر APK أو يُفعّل التحديث قبل نجاح اختبارات التشغيل على الأجهزة ومسار التحديث الكامل. أي توزيع لاحق للملفات التنفيذية يجب أن يرافقه أرشيف المصدر المطابق في قناة توزيع منفصلة وفق GPL.
