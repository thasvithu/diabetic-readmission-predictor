#### **1. Patient Identification**
*   **`encounter_id`**: Unique ID for the hospital stay. (Will be dropped, not a feature).
*   **`patient_nbr`**: Unique ID for the patient. (Will be dropped, not a feature).

#### **2. Demographic Information**
*   **`race`**: Patient's race (e.g., Caucasian, AfricanAmerican, Hispanic).
*   **`gender`**: Male, Female.
*   **`age`**: Age group, in 10-year intervals (e.g., `[40-50)`, `[50-60)`).
*   **`weight`**: Weight in pounds. *(Note: 97% missing, likely unusable)*.

#### **3. Admission & Discharge Details**
*   **`admission_type_id`**: How patient was admitted (e.g., 1-Emergency, 2-Urgent, 3-Elective).
*   **`discharge_disposition_id`**: How patient left (e.g., 1-Home, 3-Expired, 6-Transferred). **(Very Important)**
*   **`admission_source_id`**: Where patient was admitted from (e.g., 1-Physician Referral, 7-Emergency Room).
*   **`time_in_hospital`**: Number of days between admission and discharge.

#### **4. Hospital System & Care Provided**
*   **`payer_code`**: Insurance provider (e.g., MC-Medicare, MD-Medicaid). *(52% missing)*.
*   **`medical_specialty`**: Department of the admitting physician (e.g., Cardiology, Surgery). *(53% missing, many categories)*.
*   **`num_lab_procedures`**: Number of lab tests performed during the stay.
*   **`num_procedures`**: Number of procedures (other than lab tests) performed.
*   **`num_medications`**: Number of distinct generic names administered.

#### **5. Prior Utilization (Visits in the Past Year)**
*   **`number_outpatient`**: Number of outpatient visits (clinic, doctor's office).
*   **`number_emergency`**: Number of emergency room visits.
*   **`number_inpatient`**: Number of previous hospital admissions (stays). **(Strong Predictor)**
*   **`number_diagnoses`**: Number of diagnoses entered into the system.

#### **6. Diagnosis & Test Results**
*   **`diag_1`**: Primary diagnosis (ICD-9 code).
*   **`diag_2`**: Secondary diagnosis.
*   **`diag_3`**: Additional secondary diagnosis.
*   **`max_glu_serum`**: Glucose test result (Values: `">200"`, `">300"`, `"normal"`, `"none"`).
*   **`A1Cresult`**: A1c test result (Values: `">8"`, `">7"`, `"normal"`, `"none"`).

#### **7. Medications (24 Features)**
**For each medication below, the value indicates what happened during the stay:**
*   `"no"` = not prescribed
*   `"steady"` = no change in dosage
*   `"up"` = dosage increased
*   `"down"` = dosage decreased

**List of Medications:**
`metformin`, `repaglinide`, `nateglinide`, `chlorpropamide`, `glimepiride`, `acetohexamide`, `glipizide`, `glyburide`, `tolbutamide`, `pioglitazone`, `rosiglitazone`, `acarbose`, `miglitol`, `troglitazone`, `tolazamide`, `examide`, `citoglipton`, `insulin`, `glyburide-metformin`, `glipizide-metformin`, `glimepiride-pioglitazone`, `metformin-rosiglitazone`, `metformin-pioglitazone`

#### **8. Medication Summaries**
*   **`change`**: Was there any change in diabetic medications? (`"ch"` for change, `"no"` for no change).
*   **`diabetesMed`**: Was any diabetes medication prescribed? (`"yes"` or `"no"`).

#### **9. Target Variable**
*   **`readmitted`**: **What we want to predict.**
    *   `"NO"` = Not readmitted.
    *   `"<30"` = Readmitted within 30 days. **(Key focus)**
    *   `">30"` = Readmitted after 30 days.

---