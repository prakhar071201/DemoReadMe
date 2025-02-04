# Data Prep Agent POC

## ⚠️ Note
> Uploaded files get stored in the session. If you reset or close the tab, you will need to start over from the beginning.

---

## 📌 **Stages in Data Preparation**

### **1️⃣ Aggregation & Cleaning**

#### **📝 Step 1: Upload File**
- Upload a dataset to start the data preparation process.

#### **🔹 Generate Aggregation Suggestions**
- **Endpoint:** `/aggregation_suggestions/`
- **Method:** `POST`
- **Payload:** `None`
- **Response:** Returns suggestions for aggregating numerical columns.

#### **🔹 Apply Aggregation Suggestions**
- **Endpoint:** `/apply_aggregations_suggestions/`
- **Method:** `POST`
- **Payload Format:**
  ```json
  {
      "selected_methods": {
          "total_seats": ["mean", "max"],
          "assigned_seats": ["median", "min"]
      }
  }
  ```
- **Response:** Applies selected aggregation methods to the dataset.

#### **🔹 Generate Cleaning Suggestions**
- **Endpoint:** `/generate_cleaning_suggestions/`
- **Method:** `POST`
- **Payload:** `None`
- **Response:** Returns suggested data cleaning actions (e.g., removing duplicates, filling missing values).

#### **🔹 Apply Cleaning Suggestions**
- **Endpoint:** `/apply_clean_suggestions/`
- **Method:** `POST`
- **Payload Format:**
  ```json
  {
      "indices": [0, 2, 4]
  }
  ```
- **Response:** Cleans the dataset based on the selected indices.

---

### **2️⃣ [Work in Progress]**
🚧 More steps will be added as the POC progresses.

---

### **📌 Next Steps**
- Add further processing stages such as **Feature Engineering, Data Splitting, Model Training, and Inference**.
- Enhance the API for better validation and performance.

---
🚀 **This POC aims to automate data preparation efficiently!** 🚀

