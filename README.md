# RedPill OS

RedPill OS هي توزيعة لينكس مخصصة لاختبار الاختراق (Penetration Testing) مبنية على Debian 12 (Bookworm) مع واجهة سطح المكتب XFCE الخفيفة والسريعة.

## الميزات الرئيسية:

- **القاعدة:** Debian 12 (Bookworm)
- **سطح المكتب:** XFCE
- **النواة:** Linux 6.1 Kernel
- **المستخدم الافتراضي:** `redteam` (بدون كلمة مرور في الجلسة المباشرة)
- **أدوات الاختراق:** أكثر من 100 أداة مقسمة إلى فئات (الاستطلاع، اختراق الويب، الشبكات اللاسلكية، الاستغلال وما بعد الاختراق).
- **سكربتات RedPill المخصصة:**
  - `quickscan <target>`: مسح شامل وسريع للهدف.
  - `anonymize`: تشغيل Tor وفتح المتصفح عبر Proxychains للتخفي.
  - `gen-payload <LHOST> <LPORT>`: إنشاء حمولات (Payloads) بسرعة.
  - `redpill-update`: تحديث كافة أدوات النظام بضغطة واحدة.

## كيفية البناء (Build):

لإنشاء ملف ISO الخاص بـ RedPill OS، ستحتاج إلى بيئة Debian/Ubuntu مثبت عليها `live-build`.

1. **تثبيت live-build:**
   ```bash
   sudo apt update
   sudo apt install live-build
   ```

2. **استنساخ المستودع:**
   ```bash
   git clone https://github.com/mohmmadsedeg30-design/RedPill-OS.git
   cd RedPill-OS
   ```

3. **بدء عملية البناء:**
   ```bash
   sudo lb config --architecture amd64 --distribution bookworm --bootstrap-flavour minimal --archive-areas "main contrib non-free non-free-firmware" --debian-installer live --binary-images iso-hybrid --bootappend-live "locales=en_US.UTF-8 keyboard-layouts=us timezone=Etc/UTC hostname=redpill username=redteam" --apt-recommends no
   sudo lb build
   ```

4. **جعل السكربتات قابلة للتنفيذ:**
   ```bash
   chmod +x config/chroot_local-includes/usr/local/bin/*
   ```

بعد اكتمال عملية البناء، ستجد ملف الـ ISO في المجلد الرئيسي للمشروع.
