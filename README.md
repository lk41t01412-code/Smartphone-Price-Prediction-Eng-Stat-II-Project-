# Smartphone Price Prediction using Multiple Linear Regression

โปรเจกต์นี้เป็นส่วนหนึ่งของรายวิชา **2104210 Engineering Statistics II** (ภาคการศึกษาปลาย ปีการศึกษา 2568) ภาควิชาวิศวกรรมอุตสาหการ คณะวิศวกรรมศาสตร์ จุฬาลงกรณ์มหาวิทยาลัย

โปรเจกต์นี้มีวัตถุประสงค์เพื่อสร้างโมเดลทางสถิติเพื่อ **พยากรณ์ราคาสมาร์ตโฟน** โดยใช้การวิเคราะห์การถดถอยพหุคูณ (**Multiple Linear Regression**) เพื่อศึกษาปัจจัยต่างๆ เช่น ขนาดหน้าจอ (Screen Size), แรม (RAM), ความจุหน่วยความจำ (ROM) และความจุแบตเตอรี่ (Battery) ที่มีผลต่อราคาตลาด

## ลิงก์ที่เกี่ยวข้อง
* **Google Colab:** [View Notebook](https://colab.research.google.com/drive/1u9REbqAK_MBLT9yp5WGjRvQMIbnqFn-6?usp=sharing)

## ขั้นตอนการดำเนินงานหลัก

0.  **Data Colection**
    * เก็บข้อมูลสเปคและราคาของโทรศัพท์มือถือจากแบรนด์ดัง 12 แบรนด์ จำนวน 744 record ตั้งแต่ปี ค.ศ. 2020-2025
    * เก็บข้อมูลมือถือเพิ่มเติมในต้นปี ค.ศ. 2026 เพื่อใช้เป็น Test set สำหรับ Evaluate model เพิ่มเติม

1.  **Exploratory Data Analysis (EDA)**
    * จัดการข้อมูล Missing Values
    * วิเคราะห์การกระจายตัวของข้อมูลตัวแปรต่าง
    * ดู correlation heatmap เพื่อดูความสัมพันธ์ระหว่างตัวแปร
    * ดูค่า VIF เพื่อวิเคราะห์ความเสี่ยง multicollinearity

2.  **Baseline Modeling**
    * preprocess ข้อมูลต่างๆและนำไปสร้างโมเดล baseline linear regression
    * วิเคราะห์ความสมเหตุสมผลของ co-efficientcy
    * วิเคราะห์ประสิทธิภาพโมเดล (R², R²adj, RMSE, F, P-Value)
    * วิเคราะห์ residual
    * วิเคราะห์นัยสำคัญของแต่ละตัวแปร (T-test for significant)
    * วิเคราะห์ผลของ interaction ระหว่างตัวแปร (Test for interaction)
    * วิเคราะห์ผลใน 10 fold cross-validation

3.  **Feature Engineering**
    * การทำ **log_antutu**, **ultrawild_grade**, **has_telehoto** เพื่อลดความคลาดเคลื่อนของโมเดล (เนื่องจากมือถือราคาประหยัดมักให้แบตเตอรี่สูงเกินความคาดหมายของโมเดลเชิงเส้น)
    * กำจัดข้อมูลกลุ่มสมาร์ตโฟนหน้าจอพับ (Foldable) ออกเนื่องจากเป็น Outlier ที่มีราคาและขนาดหน้าจอโดดจากกลุ่มปกติ
    * กำจัด Dummies variable ของ processor_brand ออก เนื่องจากเสี่ยง multicollinearity

3.  **Model V2 Building:**
    * สร้างโมเดล Regression โดยพิจารณาตัวแปรอิสระที่มีนัยสำคัญ
    * วิเคราะห์ความสมเหตุสมผลของ co-efficientcy
    * วิเคราะห์ประสิทธิภาพโมเดล (R², R²adj, RMSE, F, P-Value)
    * วิเคราะห์ residual
    * วิเคราะห์นัยสำคัญของแต่ละตัวแปร (T-test for significant)
    * วิเคราะห์ผลใน 10 fold cross-validation
    * Feature Selection โดยใช้ Stepwise Selection

4.  **Model Evaluation on 2026 Data Test set**
    * วิเคราะห์ประสิทธิภาพโมเดล (R², R²adj, RMSE, F, P-Value) ใน 3 โมเดล (Model V2, Binarized Battery, No Battery)
    * วิเคราะห์ผลของการ Feature Selection บนข้อมูลปี 2026


# Summary
## ตัวแปรที่ใช้ในการศึกษา
* **Dependent Variable (Y):** Price (ราคาสมาร์ตโฟน)
* **Independent Variables (X):**
    * Brands
    * RAM
    * Storage (ROM)
    * Screen Size
    * Weight
    * Battery Capacity
    * Antutu Score
    * Processor Brand
    * Launch Year
    * Camera Specifications
    * Fold & Flip

## ข้อเสนอแนะสำหรับการพัฒนาต่อ
* **Advanced Models:** ควรพิจารณาใช้ Machine Learning เช่น Random Forest หรือ XGBoost เพื่อจับความสัมพันธ์แบบ Non-linearity และ Interaction Effects
* **Feature Expansion:** เพิ่มตัวแปรด้านภูมิภาค (Region), ช่องทางการจำหน่าย และคะแนนรีวิวจากผู้ใช้งาน (Review Score)

## คณะผู้จัดทำ
1. นายชิษณุพงศ์ ชินศิริโชคชัย (6730116021)
2. นางสาวดาวิกา มงคลรัตนอารี (6730178921)
3. นายณชพล ชวนอยู่ (6730129121)

**อาจารย์ที่ปรึกษา:** รศ. ดร. อังศุมาลิน เสนจันทร์ฒิไชย
