# ROS 2 Humble Installation & Setup Guide on WSL2

هذا المستودع يحتوي على توثيق كامل لعملية تثبيت بيئة **Ubuntu 22.04 LTS** باستخدام **WSL2** على نظام Windows، وإعداد **ROS 2 Humble Desktop**، مع عرض للمشكلات التي تم مواجهتها أثناء التثبيت وكيفية معالجتها.

---

## 📋 مواصفات البيئة (Environment Details)
- **OS:** Windows 11
- **Subsystem:** WSL2 (Windows Subsystem for Linux)
- **Linux Distribution:** Ubuntu 22.04.5 LTS
- **ROS Version:** ROS 2 Humble Hawksbill (Desktop Install)

---

## 🛠️ خطوات التثبيت (Installation Steps)

### 1. إعداد بيئة لينكس (Ubuntu على WSL2)
تم تفعيل WSL وتشغيل نسخة Ubuntu عبر موجه الأوامر (PowerShell):
```bash
wsl --install -d Ubuntu-22.04
