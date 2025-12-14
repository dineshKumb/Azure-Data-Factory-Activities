# Event-Driven Azure Data Factory Orchestration Pipeline

## 📌 Overview
This project demonstrates a **fully automated, event-driven Azure Data Factory (ADF) pipeline** designed using modular child pipelines and a parent orchestration pipeline.

The solution reacts to file-arrival events, orchestrates sequential pipeline execution, integrates external data via HTTP APIs, applies conditional logic and looping patterns, performs transformations using Data Flows, and delivers analytics-ready datasets into a structured Data Lake.

---

## 🚀 Key Capabilities Covered

- Event-based triggering using **Storage Event Triggers**
- Parent–child pipeline orchestration
- Sequential pipeline execution
- Dynamic file handling & cleanup
- External data ingestion via **HTTP API (GitHub)**
- Conditional processing using **If Condition + ForEach**
- Schema-based transformations using **ADF Data Flows**
- Dataset splitting, filtering, and aggregation
- Analytics-ready outputs for downstream teams

---

## 🏗️ Data Lake Folder Structure
- **Source**  
  Incoming files dropped with a specific naming convention.

- **Destination**  
  Central processing area where source files and external API data are combined and transformed.

- **Reporting**  
  Final curated datasets ready for consumption by the analytics team.

---

## 🔄 Pipeline Architecture

### **1️⃣ Storage Event Trigger**
- Monitors the **Source** folder
- Fires the **Parent Pipeline** when a file with a defined naming pattern is detected
- Enables fully automated, event-driven execution

---

### **2️⃣ Parent Pipeline**
- Acts as the orchestration layer
- Triggers multiple child pipelines **in sequence**
- Ensures controlled execution flow and dependency management

---

### **3️⃣ Child Pipeline 1 — Source File Ingestion**
- Copies the incoming file from **Source → Destination**
- Deletes the file from Source after successful copy  
  *(Prevents duplicate triggering and reprocessing)*

---

### **4️⃣ Child Pipeline 2 — External API Ingestion**
- Fetches additional data from a **GitHub repository using HTTP API**
- Stores fetched data into the **Destination** folder
- Demonstrates API-based ingestion in ADF

---

### **5️⃣ Child Pipeline 3 — Conditional Processing & Transformation**

#### **File Validation Logic**
- Uses **ForEach Activity** to iterate over files
- Uses **If Condition Activity** to:
  - Check whether required files exist
  - Ensure only **specific files** are processed (not all files)

#### **Data Transformation (ADF Data Flow)**
- Selects only required columns
- Applies transformation logic
- Splits the dataset based on conditions applied to a key column
- Produces **three separate outputs**:
  - Two condition-based datasets
  - One aggregated dataset saved directly for analytics consumption

---

## ⚙️ Tech Stack
- **Azure Data Factory**
- **ADF Pipelines & Data Flows**
- **Azure Data Lake Storage**
- **HTTP API (GitHub Integration)**
- **Event Triggers**
- **ForEach & If Condition Activities**

---

## 📊 Output for Analytics Team
- Clean, filtered, and split datasets
- One pre-aggregated table ready for reporting
- Files stored in the **Reporting** folder
- No manual preprocessing required

---

## 📈 Why This Project Matters
- Demonstrates real-world ADF orchestration patterns
- Shows understanding of event-driven pipelines
- Handles idempotency and duplicate-trigger prevention
- Combines internal and external data sources
- Delivers analytics-ready outputs, not raw dumps

---

## 🔧 Execution Flow Summary

1. File arrives in **Source** folder  
2. Storage Event Trigger fires Parent Pipeline  
3. Parent Pipeline triggers:
   - Source ingestion pipeline
   - GitHub API ingestion pipeline
   - Conditional transformation pipeline  
4. Transformed and split datasets saved into **Reporting** folder  

---

<img width="602" height="155" alt="Picture5" src="https://github.com/user-attachments/assets/93f4722d-400f-4505-9be1-f8bb797b8a60" />
<img width="1379" height="491" alt="Picture6" src="https://github.com/user-attachments/assets/5ae89a79-755c-4418-afc9-b70c911153d9" />
<img width="1059" height="352" alt="Picture2" src="https://github.com/user-attachments/assets/d8fa2a31-111a-4dc2-9ddb-b25f04af5c88" />
<img width="1076" height="294" alt="Picture3" src="https://github.com/user-attachments/assets/d28af570-6679-4c47-9426-5d473e2882e1" />
<img width="1034" height="262" alt="Picture0" src="https://github.com/user-attachments/assets/fa0c8f8b-a795-4277-8e30-8c84e49ae770" />
<img width="2020" height="412" alt="Picture1" src="https://github.com/user-attachments/assets/e93a7115-0fe2-4149-88e6-7159daeac4ac" />
<img width="1684" height="622" alt="Picture4" src="https://github.com/user-attachments/assets/3c1aec97-cfcb-43e5-a766-be1959890f7d" />


