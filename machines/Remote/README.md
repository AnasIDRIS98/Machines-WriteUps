# Remote

**النظام:** Windows &nbsp;|&nbsp; **الصعوبة:** Easy &nbsp;|&nbsp; **التصنيف:** Machine

## الملخص

جهاز Windows يبدأ بتسريب ملف نسخ احتياطي عبر NFS، يليه كسر تجزئة (Hash) من قاعدة بيانات Umbraco، ثم تنفيذ كود عن بُعد عبر خاصية XSLT Scripting في لوحة إدارة Umbraco، مع وجود مسارين مختلفين لتصعيد الصلاحيات.

## سلسلة الاختراق

<details>
<summary>1. الاستطلاع (Enumeration)</summary>

اكتشاف مشاركة NFS باسم `site_backups` قابلة للوصول بدون مصادقة، تحتوي على نسخة من موقع الويب.
</details>

<details>
<summary>2. نقطة الدخول (Foothold)</summary>

استخراج ملف قاعدة بيانات `Umbraco.sdf` من النسخة الاحتياطية وكسر تجزئة كلمة مرور المسؤول منه. تسجيل الدخول للوحة إدارة Umbraco واستغلال خاصية XSLT (عبر `msxsl:script`) لتنفيذ أوامر على الخادم.
</details>

<details>
<summary>3. تصعيد الصلاحيات (Privilege Escalation)</summary>

تم اختبار مسارين للوصول إلى صلاحيات SYSTEM:
- استغلال PrintSpoofer.
- إعادة استخدام كلمة مرور من إعدادات TeamViewer الإصدار 7 المخزنة على الجهاز.
</details>

## تعيين MITRE ATT&CK

| Tactic | Technique | ID |
|---|---|---|
| Credential Access | Unsecured Credentials (NFS Backup) | T1552 |
| Credential Access | Brute Force (Hash Cracking) | T1110.002 |
| Initial Access | Exploit Public-Facing Application | T1190 |
| Privilege Escalation | Abuse Elevation Control Mechanism | T1548 |
| Privilege Escalation | Valid Accounts (Credential Reuse) | T1078 |

## الدروس المستفادة

- النسخ الاحتياطية المكشوفة عبر مشاركات الشبكة تُعد مصدرًا غنيًا للمعلومات الحساسة.
- إعادة استخدام كلمات المرور بين خدمات مختلفة على نفس الجهاز يوسّع سطح الهجوم بشكل كبير.
