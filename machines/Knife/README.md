# Knife

**النظام:** Linux &nbsp;|&nbsp; **الصعوبة:** Easy &nbsp;|&nbsp; **التصنيف:** Machine

## الملخص

جهاز يستغل وجود إصدار تطويري (dev) من PHP 8.1.0 يحتوي على باب خلفي (backdoor) عبر ترويسة HTTP، ثم يصعّد الصلاحيات عبر صلاحية sudo ممنوحة لأداة `knife`.

## سلسلة الاختراق

<details>
<summary>1. الاستطلاع (Enumeration)</summary>

فحص الخادم كشف عن تشغيل نسخة تطويرية غير مستقرة من PHP (8.1.0-dev) تحتوي على ثغرة باب خلفي معروفة.
</details>

<details>
<summary>2. نقطة الدخول (Foothold)</summary>

استغلال الباب الخلفي عبر إرسال كود PHP داخل ترويسة `User-Agentt` (بحرف t إضافي)، مما أتاح تنفيذ أوامر عن بُعد والحصول على shell أولي.
</details>

<details>
<summary>3. تصعيد الصلاحيات (Privilege Escalation)</summary>

اكتشاف أن المستخدم يملك صلاحية تشغيل أداة `knife` عبر `sudo` بدون قيود، واستغلال إحدى ميزاتها (تنفيذ كود Ruby) للحصول على صلاحيات root.
</details>

## تعيين MITRE ATT&CK

| Tactic | Technique | ID |
|---|---|---|
| Initial Access | Exploit Public-Facing Application | T1190 |
| Execution | Command and Scripting Interpreter | T1059 |
| Privilege Escalation | Abuse Elevation Control Mechanism (Sudo) | T1548.003 |

## الدروس المستفادة

- تشغيل إصدارات تطويرية (dev/beta) من البرمجيات في بيئة إنتاج يفتح المجال لثغرات غير معروفة عمومًا.
- منح صلاحيات `sudo` لأدوات تحتوي على وظائف تنفيذ كود (مثل knife) يجب أن يكون مقيدًا بدقة.
