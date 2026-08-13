# Sequel

**النظام:** Linux &nbsp;|&nbsp; **الصعوبة:** Very Easy &nbsp;|&nbsp; **التصنيف:** Starting Point

## الملخص

جهاز يركز على استطلاع خدمة MySQL/MariaDB والوصول إليها مباشرة بحساب root بدون كلمة مرور، وهو مثال كلاسيكي على خطورة ترك خدمات قواعد البيانات بإعدادات افتراضية مكشوفة.

## سلسلة الاختراق

<details>
<summary>1. الاستطلاع (Enumeration)</summary>

فحص المنافذ المفتوحة عبر `nmap` كشف عن خدمة MySQL/MariaDB على المنفذ الافتراضي.
</details>

<details>
<summary>2. نقطة الدخول (Foothold)</summary>

محاولة تسجيل الدخول بحساب `root` بدون كلمة مرور نجحت مباشرة، مما أتاح الوصول الكامل لقاعدة البيانات واستخراج الفلاغ منها دون الحاجة لاستغلال إضافي.
</details>

## تعيين MITRE ATT&CK

| Tactic | Technique | ID |
|---|---|---|
| Reconnaissance | Active Scanning (Service Scan) | T1595.002 |
| Initial Access | Valid Accounts (Default Credentials) | T1078.001 |

## الدروس المستفادة

- أهمية تغيير كلمات المرور الافتراضية فور تثبيت أي خدمة.
- خدمات قواعد البيانات المكشوفة على الشبكة تُعد نقطة دخول شائعة وسهلة الاستغلال.
