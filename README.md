# Mandarin public news, updates and releases

This is the single public home for Mandarin developer news, reserved update metadata, and future GitHub Releases/downloads. It contains no application source code. Currently it contains only metadata and documentation; no release or APK is published.

Base URL: `https://raw.githubusercontent.com/SENESO/mandarin-player-updates/main/`

## Developer news

[`metadata.json`](metadata.json) is the news index, currently `[]` (no published announcements). Its contract is [`metadata.schema.json`](metadata.schema.json). The current local news reader points to this repository's raw `metadata.json` and `content/<id>` endpoints; this does not establish that a distributed application build has been updated or tested.

Field names are case-sensitive:

| Field | Type | Meaning |
| --- | --- | --- |
| `id` | string | Safe article filename, used verbatim in `content/<id>`; required by the publishing contract. |
| `Title` | string | Required public headline. |
| `Description` | string | Optional summary; defaults to empty text. |
| `ImageURL` | string, array of strings, or null | Optional HTTPS public image URLs; an array is preferred. |
| `Important` | boolean | Optional highlight flag; defaults to false. |
| `Author` | string | Required public display name, not private account details. |
| `Date` | integer | Unix timestamp in milliseconds; publish an explicit value. |

For every published entry, add its reviewed Markdown article at `content/<id>` with exactly the same identifier. The client fetches article content as text. Use stable, unique identifiers matching the schema; do not include slashes, dot segments or URL escapes. An empty index needs no content directory. The publishing schema preserves the current client's field casing and array format, while requiring explicit article identifiers and dates rather than relying on permissive client defaults.

## Update metadata: disabled

[`updates.json`](updates.json) is a reserved manifest, governed by [`updates.schema.json`](updates.schema.json):

- `schemaVersion`: `1`.
- `enabled`: `false`.
- `channels.stable`: `null`.
- `channels.beta`: `null`.

Version 1 defines only the inactive state: it advertises no release, version, download URL or installation instruction. An active-release contract needs a separately reviewed schema revision. Creating or editing this file does not activate application updates.

The current development updater reads this manifest as an approval gate. **Public schema v1 remains inactive-only**; it cannot approve downloads, even if someone merely changes its `enabled` value. A separately reviewed active contract uses `schemaVersion: 2`, `enabled: true`, and stable/beta channel objects containing `tag` and `sourceArchiveUrl`. A channel may remain null. The matching GPL archive must be publicly accessible in a separate source location, never this repository or a private development URL. Source correspondence must be verified before activation.

The updater selects only that approved tag from this same repository's GitHub Releases API and requires an exact build-specific uploaded APK asset, supported MIME, valid size and SHA-256 digest. Package identity, a strictly newer version and matching non-debug signer are checked before Android's user-confirmed installer. Missing approval/assets do not fall back to a release web page or another repository.

Manual update capability is implemented in the current development version. Startup/background checks stay behind a separate default-disabled build gate pending device validation. This is not evidence that a distributed build or real upgrade has passed end-to-end checks. No automatic download or silent installation is enabled. The v2 publishing schema still needs review before any active public payload is introduced; no application code is published here.

## Future releases: this same repository

The intended public release home is [GitHub Releases](https://github.com/SENESO/mandarin-player-updates/releases). No release is published and updates remain disabled. Do not publish APKs or enable update polling until real-device startup and complete end-to-end update validation pass, including package identity, upgrade compatibility and signing checks.

Before publishing any GPL-covered binary, make its complete matching Corresponding Source publicly accessible **separately** and link it clearly from that release. Keep application source and source archives out of this repository and its release assets. GitHub's automatically generated archives of this metadata repository are not the application's Corresponding Source. The separate source must match the binary and include the materials required by the applicable GPL obligations; a private development link is not sufficient.

Publish only reviewed public announcements and release information. Never commit tokens, credentials, private account details, private draft information, application source or unreviewed binaries. There are no automated publication workflows here.

## بالعربية

مستودع عام واحد للأخبار وبيانات التحديثات وإصدارات التطبيق لاحقًا، من غير كود التطبيق. حاليًا الأخبار فارغة وبيانات التحديث معطّلة، ولم يُنشر أي APK أو إصدار. قارئ الأخبار المحلي يشير إلى هذا المستودع، ودعم المحدّث في التطوير الحالي يقرأ ملف الاعتماد أيضًا. يظل مخطط v1 معطّلًا فقط؛ عقد التفعيل المستقبلي v2 يحتاج مراجعة ونشر مخططه بعد اجتياز بوابات الأجهزة والتحديث الكامل. قدرة الفحص اليدوي موجودة، بينما فحص الإقلاع والخلفية خلف بوابة منفصلة مقفولة افتراضيًا. لا يُنشر APK أو تُفعّل القناة قبل التحقق الفعلي، ولا يوجد تنزيل أو تثبيت صامت. المصدر المطابق يُتاح علنًا في مكان منفصل ويرتبط بالإصدار وفق GPL، مع بقاء كود التطبيق خارج هذا المستودع.
