# 🤖 دليل ROS الشامل

---

## 📑 جدول المحتويات

1. [مقدمة عن ROS](#مقدمة-عن-ros)
2. [أوامر Linux الأساسية](#أوامر-linux-الأساسية)
4. [تثبيت ROS 2 - Humble](#تثبيت-ros-2---humble)
6. [أوامر ROS 2](#أوامر-ros-2)

---

## مقدمة عن ROS

### ما هو نظام ROS؟

**ROS** (Robot Operating System) هو نظام تشغيل مفتوح المصدر مصمم خصيصاً لتطبيقات الروبوتات. يوفر أدوات وحزم برمجية شاملة تسهل تطوير وتشغيل الروبوتات المعقدة.

### ✨ المميزات الأساسية:

- ✓ تواصل فعال وموثوق بين مكونات الروبوت
- ✓ مكتبات شاملة للتحكم والاستشعار
- ✓ محاكاة ثلاثية الأبعاد (Gazebo)
- ✓ أدوات تصور البيانات (RViz)
- ✓ مدعوم من قبل مجتمع عالمي ضخم
- ✓ مجاني وسهل التعديل

---

## أوامر Linux الأساسية

هذه الأوامر ضرورية جداً قبل البدء مع ROS:

| الأمر | الشرح | مثال |
|------|-------|------|
| `ls` | عرض محتويات المجلد الحالي | `$ ls -la` |
| `cd [مسار]` | الانتقال إلى مجلد معين | `$ cd Desktop` |
| `pwd` | عرض المسار الحالي | `$ pwd` |
| `mkdir [اسم]` | إنشاء مجلد جديد | `$ mkdir robot` |
| `sudo` | تنفيذ الأمر كمسؤول | `$ sudo apt-get update` |
| `apt-get update` | تحديث قائمة الحزم | `$ sudo apt-get update` |
| `apt-get install` | تثبيت حزمة | `$ sudo apt-get install ros-humble` |
| `nano [ملف]` | فتح محرر نصوص | `$ nano setup.bash` |
| `source [ملف]` | تحميل متغيرات البيئة | `$ source ~/.bashrc` |
| `echo` | طباعة نص أو متغير | `$ echo $ROS_DISTRO` |

---

---

## تثبيت ROS 2 - Humble

### ⚠️ المتطلبات:
- **نظام التشغيل:** Ubuntu 22.04 LTS أو أحدث
- **الذاكرة:** 4 GB على الأقل
- **المساحة:** 2-3 GB على الأقل

### 🔧 خطوات التثبيت:

#### الخطوة 1️⃣: تحديث النظام
```bash
sudo apt update && sudo apt upgrade -y
```

#### الخطوة 2️⃣: تثبيت البرامج المساعدة
```bash
sudo apt install software-properties-common curl -y
```

#### الخطوة 3️⃣: إضافة المفتاح
```bash
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

#### الخطوة 4️⃣: إضافة المستودع
```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

#### الخطوة 5️⃣: تحديث الحزم
```bash
sudo apt update
```

#### الخطوة 6️⃣: تثبيت ROS 2 Humble
```bash
sudo apt install ros-humble-desktop -y
```

#### الخطوة 7️⃣: إعداد البيئة
```bash
echo 'source /opt/ros/humble/setup.bash' >> ~/.bashrc
```

#### الخطوة 8️⃣: تحميل الإعدادات
```bash
source ~/.bashrc
```

#### الخطوة 9️⃣: التحقق من التثبيت
```bash
ros2 --version
```

---

## أوامر ROS 2

### الأوامر الأساسية:

| الأمر | الشرح |
|------|-------|
| `ros2 node list` | عرض قائمة العقد النشطة |
| `ros2 topic list` | عرض قائمة المواضيع المتاحة |
| `ros2 service list` | عرض قائمة الخدمات المتاحة |
| `ros2 topic echo [topic_name]` | عرض البيانات المرسلة عبر موضوع |
| `ros2 interface show [msg_type]` | عرض هيكل الرسالة |
| `ros2 launch [package] [launch_file]` | تشغيل ملف إطلاق |
| `ros2 run [package] [executable]` | تشغيل عقدة أو برنامج |
| `ros2 param list` | عرض قائمة المعاملات |
| `ros2 param set [node] [param] [value]` | تعيين قيمة معامل |
| `ros2 param get [node] [param]` | الحصول على قيمة معامل |
| `ros2 node info [node_name]` | الحصول على معلومات عقدة |
| `ros2 topic info [topic_name]` | الحصول على معلومات موضوع |

