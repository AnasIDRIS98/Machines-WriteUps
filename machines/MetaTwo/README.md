# MetaTwo

**النظام:** Linux &nbsp;|&nbsp; **الصعوبة:** Easy &nbsp;|&nbsp; **التصنيف:** Machine

## الملخص

جهاز يجمع بين ثغرتين في إضافات WordPress (SQL Injection و XXE) للوصول إلى بيانات اعتماد، وينتهي بتصعيد صلاحيات عبر إساءة استخدام أداة إدارة كلمات مرور GPG تُدعى Passpie.

## سلسلة الاختراق

<details>
<summary>1. الاستطلاع (Enumeration)</summary>

اكتشاف موقع WordPress مع إضافة (Plugin) تحتوي على ثغرات معروفة.
</details>

<details>
<summary>2. نقطة الدخول (Foothold)</summary>

استغلال ثغرة SQL Injection (CVE-2022-0739) في إضافة WordPress لاستخراج بيانات اعتماد المستخدمين. بشكل موازٍ، استغلال ثغرة XXE (CVE-2021-29447) للوصول إلى ملفات النظام، مما أدى في النهاية إلى الحصول على shell أولي.
</details>

<details>
<summary>3. تصعيد الصلاحيات (Privilege Escalation)</summary>

اكتشاف أداة Passpie المستخدمة لإدارة كلمات المرور عبر GPG، واستغلال إعداداتها للوصول إلى صلاحيات أعلى.
</details>

## تعيين MITRE ATT&CK

| Tactic | Technique | ID |
|---|---|---|
| Initial Access | Exploit Public-Facing Application | T1190 |
| Credential Access | Exploitation for Credential Access (SQLi) | T1212 |
| Credential Access | Unsecured Credentials (GPG Store) | T1552 |
| Privilege Escalation | Exploitation for Privilege Escalation | T1068 |

## الدروس المستفادة

- إضافات WordPress من أكثر مصادر الثغرات شيوعًا، ويجب فحصها ومتابعة تحديثاتها بانتظام.
- أدوات إدارة كلمات المرور المحلية (مثل Passpie) قد تتحول إلى نقطة ضعف إذا لم تُهيّأ بشكل آمن.
