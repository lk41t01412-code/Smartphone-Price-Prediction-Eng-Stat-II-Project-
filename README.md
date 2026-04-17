# Smartphone Price Prediction using Multiple Linear Regression

โปรเจกต์นี้เป็นส่วนหนึ่งของรายวิชา **2104210 Engineering Statistics II** (ภาคการศึกษาปลาย ปีการศึกษา 2568) ภาควิชาวิศวกรรมอุตสาหการ คณะวิศวกรรมศาสตร์ จุฬาลงกรณ์มหาวิทยาลัย

## 📝 Summary
โปรเจกต์นี้มีวัตถุประสงค์เพื่อสร้างโมเดลทางสถิติเพื่อ **พยากรณ์ราคาสมาร์ตโฟน** โดยใช้การวิเคราะห์การถดถอยพหุคูณ (**Multiple Linear Regression**) เพื่อศึกษาปัจจัยต่างๆ เช่น ขนาดหน้าจอ (Screen Size), แรม (RAM), ความจุหน่วยความจำ (ROM) และความจุแบตเตอรี่ (Battery) ที่มีผลต่อราคาตลาด

## 🔗 ลิงก์ที่เกี่ยวข้อง
* **Google Colab:** [View Notebook](https://colab.research.google.com/drive/1u9REbqAK_MBLT9yp5WGjRvQMIbnqFn-6?usp=sharing)

## 🛠️ ขั้นตอนการดำเนินงาน
1.  **Data Cleaning:**
    * กำจัดข้อมูลกลุ่มสมาร์ตโฟนหน้าจอพับได้ (Foldable) ออกเนื่องจากเป็น Outlier ที่มีราคาและขนาดหน้าจอโดดจากกลุ่มปกติ
    * จัดการข้อมูล Missing Values
2.  **Feature Engineering:**
    * การทำ **Binarize Battery** เพื่อลดความคลาดเคลื่อนของโมเดล (เนื่องจากมือถือราคาประหยัดมักให้แบตเตอรี่สูงเกินความคาดหมายของโมเดลเชิงเส้น)
3.  **Model Building:**
    * สร้างโมเดล Regression โดยพิจารณาตัวแปรอิสระที่มีนัยสำคัญ
4.  **Model Evaluation:**
    * ตรวจสอบ Residual Analysis, Multicollinearity (VIF) และความแม่นยำของโมเดล

## 📊 ตัวแปรที่ใช้ในการศึกษา
* **Dependent Variable (Y):** Price (ราคาสมาร์ตโฟน)
* **Independent Variables (X):**
    * RAM
    * Storage (ROM)
    * Screen Size
    * Battery Capacity

## 🚀 ข้อเสนอแนะสำหรับการพัฒนาต่อ
* **Advanced Models:** ควรพิจารณาใช้ Machine Learning เช่น Random Forest หรือ XGBoost เพื่อจับความสัมพันธ์แบบ Non-linearity และ Interaction Effects
* **Feature Expansion:** เพิ่มตัวแปรด้านภูมิภาค (Region), ช่องทางการจำหน่าย และคะแนนรีวิวจากผู้ใช้งาน (Review Score)

## 👥 คณะผู้จัดทำ
1. นายชิษณุพงศ์ ชินศิริโชคชัย (6730116021)
2. นางสาวดาวิกา มงคลรัตนอารี (6730178921)
3. นายณชพล ชวนอยู่ (6730129121)

**อาจารย์ที่ปรึกษา:** รศ. ดร. อังศุมาลิน เสนจันทร์ฒิไชย
