# Timelapse

**النظام:** Windows (Active Directory) &nbsp;|&nbsp; **الصعوبة:** Easy &nbsp;|&nbsp; **التصنيف:** Machine

## الملخص

جهاز Active Directory متكامل يبدأ بمشاركة SMB مجهولة تحتوي على شهادة PFX محمية بكلمة مرور، ينتهي بإساءة استخدام صلاحيات LAPS للوصول إلى حساب Domain Admin.

## سلسلة الاختراق

<details>
<summary>1. الاستطلاع (Enumeration)</summary>

الوصول إلى مشاركة SMB تسمح بالدخول المجهول، واكتشاف أرشيف مضغوط يحتوي على شهادة `.pfx`.
</details>

<details>
<summary>2. نقطة الدخول (Foothold)</summary>

استخدام `zip2john` و `pfx2john` لاستخراج تجزئة كلمة مرور الأرشيف والشهادة وكسرها. استخدام الشهادة المستخرجة للمصادقة عبر Evil-WinRM والحصول على وصول أولي إلى الجهاز.
</details>

<details>
<summary>3. تصعيد الصلاحيات (Privilege Escalation)</summary>

العثور على بيانات اعتماد مخزّنة في سجل أوامر PowerShell (PowerShell History) تعود لمستخدم آخر يملك عضوية في مجموعة `LAPS_Readers`. استخدام أداة LAPSToolkit لقراءة كلمة مرور المدير المحلي المُدارة عبر LAPS، والوصول في النهاية إلى صلاحيات Domain Admin.
</details>

## تعيين MITRE ATT&CK

| Tactic | Technique | ID |
|---|---|---|
| Credential Access | Unsecured Credentials (Archive/Certificate) | T1552.001 |
| Credential Access | Brute Force (Hash Cracking) | T1110.002 |
| Initial Access | Valid Accounts | T1078 |
| Credential Access | Unsecured Credentials (PowerShell History) | T1552.003 |
| Privilege Escalation | Steal or Forge Certificates / LAPS Abuse | T1552.006 |

## الدروس المستفادة

- سجل أوامر PowerShell قد يحتوي على بيانات اعتماد بشكل غير مقصود، وتنظيفه دوريًا ضروري.
- صلاحيات قراءة كلمات مرور LAPS يجب أن تُمنح بأقل قدر ممكن (Least Privilege) وتُراقب.
