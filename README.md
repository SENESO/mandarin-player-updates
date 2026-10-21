# Mandarin public channel

One public repository for Mandarin news, update approvals, and future approved APK releases. No application source code, credentials, private history, or private release data belongs here. No APK or public release has been published yet.

Base URL: `https://raw.githubusercontent.com/SENESO/mandarin-player-updates/main/`

## News

`metadata.json` is the news index. Its current empty array means there are no published announcements; clients must not fabricate sample news or fall back to another project's news.

Future entries use `id`, `Title`, `Description`, `ImageURL` (an array of public image URLs), `Important` (boolean), `Author`, and `Date` (Unix milliseconds). Markdown articles use `content/<id>` with the exact same identifier. Publish only reviewed public announcements, in Arabic and English as appropriate.

## Update approval contract

`updates.json` is currently **disabled**: `schemaVersion: 1`, `enabled: false`, and null stable/beta channels. This advertises no update and must not trigger a download.

After all release gates pass, an approved manifest may set `enabled: true` and use `channels.stable` and/or `channels.beta` objects with `tag` and `sourceArchiveUrl`. A channel may remain null. The matching GPL source archive must be publicly accessible at a separate location; it must not be the private development repository or this combined channel. Validate that its contents match the APK/tag before activating the channel.

The approved tag is resolved through this same repository's GitHub Releases API. Downloads require the exact build-specific APK asset name, uploaded state, valid size/MIME, and GitHub's SHA-256 asset digest. Drafts, arbitrary download URLs, missing integrity data, and another repository are not update sources.

Current development builds include manual update capability. Startup/background polling stays separately gated, and no download or installation should happen automatically. Android source-install permission and the user's system installer confirmation remain required.

Do not publish a real APK or enable the manifest until startup/device validation, full release checks, matching-source verification, and the end-to-end update gates pass. Local/mock tests do not prove a completed real Android upgrade.

## بالعربية

مستودع عام واحد للأخبار واعتماد التحديثات والإصدارات المستقبلية. لا يحتوي على كود التطبيق أو توكنات أو تاريخ التطوير أو بيانات إصدارات خاصة. لم يُنشر APK أو إصدار عام.

فهرس الأخبار `metadata.json` فارغ حاليًا، وملف `updates.json` معطّل وقناتاه فارغتان؛ لذلك لا يوجد تحديث متاح للتنزيل. يدعم عقد التحديث قناتي `stable` و`beta`، ولكل قناة مفعّلة `tag` ورابط `sourceArchiveUrl` عام لأرشيف GPL المطابق في مكان منفصل. ملفات APK المعتمدة لاحقًا تستخدم Releases في نفس المستودع، ويجري التحقق من الحجم وSHA-256 وهوية التطبيق والنسخة والتوقيع قبل تسليمها لمثبّت Android.

دعم الفحص اليدوي موجود في التطوير الحالي، بينما يظل فحص الإقلاع والخلفية خلف بوابة مستقلة. لا تُفعّل القناة أو يُنشر APK قبل نجاح اختبارات الأجهزة والتحديث الكامل والتحقق من المصدر المطابق؛ ولا يوجد تنزيل أو تثبيت صامت.
