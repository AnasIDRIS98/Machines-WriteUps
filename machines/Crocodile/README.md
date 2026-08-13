# Crocodile

**النظام:** Linux &nbsp;|&nbsp; **الصعوبة:** Very Easy &nbsp;|&nbsp; **التصنيف:** Starting Point

## الملخص

جهاز يوضّح كيف يمكن لتسريب بيانات بسيط عبر FTP مجهول الهوية أن يؤدي مباشرة إلى تجاوز نظام تسجيل الدخول في تطبيق ويب.

## سلسلة الاختراق

<details>
<summary>1. الاستطلاع (Enumeration)</summary>

فحص المنافذ أظهر خدمة FTP تسمح بالدخول المجهول (Anonymous Login)، بالإضافة إلى خدمة ويب.
</details>

<details>
<summary>2. نقطة الدخول (Foothold)</summary>

الدخول المجهول إلى FTP كشف عن ملف يحتوي على بيانات اعتماد. تم استخدام هذه البيانات لتجاوز صفحة `login.php` والوصول إلى لوحة الإدارة، والحصول على الفلاغ منها.
</details>

## تعيين MITRE ATT&CK

| Tactic | Technique | ID |
|---|---|---|
| Reconnaissance | Active Scanning | T1595 |
| Credential Access | Unsecured Credentials (في ملف نصي عبر FTP) | T1552.001 |
| Initial Access | Valid Accounts | T1078 |

## الدروس المستفادة

- الخدمات المجهولة (Anonymous Access) يجب تعطيلها ما لم تكن ضرورية فعليًا.
- تخزين بيانات الاعتماد كنص صريح في ملفات يمكن الوصول إليها هو خطأ شائع وخطير.
