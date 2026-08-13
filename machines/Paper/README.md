# Paper

**النظام:** Linux &nbsp;|&nbsp; **الصعوبة:** Easy &nbsp;|&nbsp; **التصنيف:** Machine

## الملخص

سلسلة اختراق متكاملة تبدأ بثغرة إفصاح معلومات في WordPress، تمر عبر إساءة استخدام بوت Rocket.Chat، وتنتهي بتصعيد صلاحيات عبر ثغرة معروفة في Polkit.

## سلسلة الاختراق

<details>
<summary>1. الاستطلاع (Enumeration)</summary>

اكتشاف موقع WordPress ونطاقات فرعية إضافية عبر فحص عناوين IP الافتراضية والمضيفين الافتراضيين (Virtual Hosts).
</details>

<details>
<summary>2. نقطة الدخول (Foothold)</summary>

استغلال ثغرة إفصاح معلومات في WordPress (CVE-2019-17671) للوصول إلى منشورات غير منشورة كشفت عن بيانات اعتماد لخدمة Rocket.Chat. تم استغلال بوت داخل Rocket.Chat لتنفيذ أوامر والحصول على shell أولي.
</details>

<details>
<summary>3. تصعيد الصلاحيات (Privilege Escalation)</summary>

استغلال ثغرة Polkit المعروفة (CVE-2021-3560) للحصول على صلاحيات root.
</details>

## تعيين MITRE ATT&CK

| Tactic | Technique | ID |
|---|---|---|
| Initial Access | Exploit Public-Facing Application | T1190 |
| Credential Access | Unsecured Credentials | T1552 |
| Execution | Command and Scripting Interpreter | T1059 |
| Privilege Escalation | Exploitation for Privilege Escalation | T1068 |

## الدروس المستفادة

- المحتوى "غير المنشور" في أنظمة إدارة المحتوى قد يكون قابلاً للوصول عبر ثغرات API غير موثقة.
- أهمية تحديث الأنظمة الفرعية (Polkit) وعدم الاكتفاء بتحديث التطبيق الرئيسي فقط.
