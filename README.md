🤖 ROS 2 from Scratch – الدليل الشامل لتعلم ROS 2
🚀 ملخص كامل للمفاهيم الأساسية، أوامر التثبيت، وإنشاء أول روبوت محاكى باستخدام ROS 2

📌 المحتويات
ما هو ROS 2؟

تثبيت Ubuntu و ROS 2

أساسيات Linux للمبتدئين

المفاهيم الأساسية في ROS 2

إنشاء أول عقدة (Node)

التواصل بين العُقد (Topics, Services, Actions)

الباراميترات (Parameters)

ملفات الإطلاق (Launch Files)

إنشاء روبوت مخصص (URDF + TF)

محاكاة الروبوت في Gazebo

أهم الأوامر (Cheat Sheet)

ماذا بعد؟

🧠 ما هو ROS 2؟
https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/Ros_logo.svg/1200px-Ros_logo.svg.png

ROS 2 هو إطار عمل مفتوح المصدر لتطوير تطبيقات الروبوتات. يتكون من:

المكون	الوصف
🧩 Framework	هيكل برمجي موحّد لتطوير العُقد (Nodes)
🛠️ Tools	أدوات مساعدة مثل RViz و Gazebo و rqt_graph
🔌 Plugins	حزم جاهزة مثل Navigation 2 و MoveIt 2
🌍 Community	مجتمع ضخم من المطورين والباحثين
✅ مميزات ROS 2:

يدعم Python و C++

يعمل على Ubuntu، Windows، و macOS

موزع مجاني ومفتوح المصدر

مناسب للروبوتات المعقدة والمشاريع الصناعية

💻 تثبيت Ubuntu و ROS 2
🔹 المتطلبات الأساسية
نظام التشغيل: Ubuntu 24.04 (Noble Numbat)

إصدار ROS: Jazzy Jalisco (LTS حتى 2029)

🔹 خطوات التثبيت
bash
# 1. تحديث الحزم
sudo apt update && sudo apt upgrade -y

# 2. تثبيت الأدوات المطلوبة
sudo apt install software-properties-common curl -y

# 3. إضافة مفتاح ROS
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# 4. إضافة المستودع
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# 5. تثبيت ROS 2
sudo apt update
sudo apt install ros-jazzy-desktop -y

# 6. تثبيت أدوات التطوير
sudo apt install ros-dev-tools -y
🔹 تفعيل البيئة
bash
# إضافة إلى .bashrc للتشغيل التلقائي
echo 'source /opt/ros/jazzy/setup.bash' >> ~/.bashrc
source ~/.bashrc
🐧 أساسيات Linux للمبتدئين
الأمر	الوظيفة
ls	عرض محتويات المجلد
cd	التنقل بين المجلدات
pwd	عرض المسار الحالي
mkdir	إنشاء مجلد جديد
touch	إنشاء ملف جديد
rm	حذف ملف
rm -rf	حذف مجلد كامل
cp	نسخ ملف
mv	نقل أو إعادة تسمية ملف
nano	محرر نصوص داخل الطرفية
sudo	تنفيذ أمر بصلاحيات المدير
📁 هيكل نظام الملفات في Ubuntu
المسار	الوصف
/bin, /sbin	الأوامر الأساسية للنظام
/etc	ملفات الإعدادات
/home/user	المجلد الشخصي للمستخدم
/opt	مكان تثبيت ROS
/usr	البرامج المثبتة (مثل Program Files)
/var/log	سجلات النظام
/boot	ملفات الإقلاع
