flowchart TD
    Start([งานวิจัย: การทำนายการพ้นสภาพนักศึกษา<br/>ด้วย Deep Learning]) --> Phase1

    %% Phase 1: Data Collection & Preparation
    Phase1[<b>Phase 1: การรวบรวมและเตรียมข้อมูล</b><br/>Data Collection & Preparation]
    Phase1 --> P1_1[1.1 รวบรวมข้อมูลนักศึกษา N คน<br/>- ข้อมูลมัธยมปลาย GPAX, GPA แต่ละกลุ่ม, หน่วยกิต<br/>- คะแนน ONET 5 วิชา<br/>- ข้อมูลการศึกษา คณะ, สถานะการพ้นสภาพ]
    P1_1 --> P1_2[1.2 ตรวจสอบคุณภาพข้อมูล]
    P1_2 --> P1_3[1.3 จัดการข้อมูลที่หายไป Missing Values]
    P1_3 --> P1_4[1.4 Encode Categorical Variables]
    P1_4 --> P1_5[1.5 แบ่งข้อมูล<br/>Train 70% / Validation 15% / Test 15%]
    
    P1_5 --> Phase2

    %% Phase 2: Feature Selection
    Phase2[<b>Phase 2: การคัดเลือกฟีเจอร์</b><br/>Feature Selection]
    Phase2 --> P2_1[2.1 Discretize Continuous Features<br/>สำหรับ Chi-Squared]
    P2_1 --> P2_2[2.2 คำนวณ Chi-Squared Score<br/>ของทุกฟีเจอร์]
    P2_2 --> P2_3[2.3 จัดอันดับฟีเจอร์<br/>ตามความสำคัญ]
    P2_3 --> P2_4[2.4 ทดลองหาจำนวนฟีเจอร์<br/>ที่เหมาะสม K = 5, 10, 15, 20]
    P2_4 --> P2_5[2.5 เลือก K ที่ให้<br/>F1-Score สูงสุด]
    P2_5 --> P2_6[2.6 Normalize/Standardize<br/>ฟีเจอร์ที่เลือก]
    
    P2_6 --> Phase3

    %% Phase 3: Handling Imbalanced Data
    Phase3[<b>Phase 3: การจัดการข้อมูลไม่สมดุล</b><br/>Handling Imbalanced Data]
    Phase3 --> P3_1[3.1 วิเคราะห์<br/>Class Distribution]
    P3_1 --> P3_2[3.2 ทดลอง 3 เทคนิค:<br/>- Baseline ไม่จัดการ<br/>- SMOTE Oversampling<br/>- SMOTE + Class Weight]
    P3_2 --> P3_3[3.3 เลือกเทคนิค<br/>ที่ให้ผลดีที่สุด]
    
    P3_3 --> Phase4

    %% Phase 4: Model Development
    Phase4[<b>Phase 4: การออกแบบและพัฒนาโมเดล</b><br/>Model Development]
    Phase4 --> P4_1[4.1 ออกแบบสถาปัตยกรรม FNN<br/>- Input Layer K neurons<br/>- Hidden Layers หลาย Configurations<br/>- Output Layer 1 neuron, Sigmoid]
    P4_1 --> P4_2[4.2 กำหนด Hyperparameters<br/>เริ่มต้น]
    P4_2 --> P4_3[4.3 Implement โมเดล<br/>ด้วย TensorFlow/Keras]
    
    P4_3 --> Phase5

    %% Phase 5: Training & Tuning
    Phase5[<b>Phase 5: การฝึกสอนและปรับแต่งโมเดล</b><br/>Training & Tuning]
    Phase5 --> P5_1[5.1 ทดลองสถาปัตยกรรมต่างๆ]
    P5_1 --> P5_2[5.2 Hyperparameter Tuning<br/>Grid Search / Random Search]
    P5_2 --> P5_3[5.3 K-Fold Cross-Validation<br/>K=5]
    P5_3 --> P5_4[5.4 Early Stopping<br/>Patience = 15]
    P5_4 --> P5_5[5.5 เลือกโมเดล<br/>ที่ดีที่สุด]
    
    P5_5 --> Phase6

    %% Phase 6: Model Evaluation
    Phase6[<b>Phase 6: การประเมินผลโมเดล</b><br/>Model Evaluation]
    Phase6 --> P6_1[6.1 ทดสอบบน Test Set]
    P6_1 --> P6_2[6.2 คำนวณ Metrics:<br/>Accuracy, Precision, Recall, F1, AUC]
    P6_2 --> P6_3[6.3 สร้าง Confusion Matrix]
    P6_3 --> P6_4[6.4 วิเคราะห์ ROC Curve]
    P6_4 --> P6_5[6.5 Feature Importance Analysis]
    P6_5 --> P6_6[6.6 Error Analysis]
    
    P6_6 --> Phase7

    %% Phase 7: Comparison & Analysis
    Phase7[<b>Phase 7: การเปรียบเทียบและวิเคราะห์ผล</b>]
    Phase7 --> P7_1[7.1 เปรียบเทียบกับ Baseline Models<br/>- Logistic Regression<br/>- Random Forest<br/>- SVM]
    P7_1 --> P7_2[7.2 เปรียบเทียบผล<br/>ของ Feature Selection]
    P7_2 --> P7_3[7.3 เปรียบเทียบผล<br/>ของ Imbalance Handling]
    P7_3 --> P7_4[7.4 สรุปผลการทดลอง]
    
    P7_4 --> End([จบกระบวนการวิจัย])

    %% Styling
    classDef phaseStyle fill:#4A90E2,stroke:#2E5C8A,stroke-width:3px,color:#fff,font-weight:bold
    classDef stepStyle fill:#E8F4F8,stroke:#4A90E2,stroke-width:2px,color:#000
    classDef startEndStyle fill:#27AE60,stroke:#1E8449,stroke-width:3px,color:#fff,font-weight:bold
    
    class Phase1,Phase2,Phase3,Phase4,Phase5,Phase6,Phase7 phaseStyle
    class P1_1,P1_2,P1_3,P1_4,P1_5,P2_1,P2_2,P2_3,P2_4,P2_5,P2_6,P3_1,P3_2,P3_3,P4_1,P4_2,P4_3,P5_1,P5_2,P5_3,P5_4,P5_5,P6_1,P6_2,P6_3,P6_4,P6_5,P6_6,P7_1,P7_2,P7_3,P7_4 stepStyle
    class Start,End startEndStyle