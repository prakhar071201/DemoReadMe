# Data Prep Agent POC

## ⚠️ Note

> Uploaded files get stored in the session. If you reset or close the tab, you will need to start over from the beginning.

---

## 📌 **Stages in Data Preparation**

### **1️⃣ Aggregation & Cleaning**

#### **📝 Step 1: Upload File**

- Upload a dataset to start the data preparation process.

#### **🔹 Generate Cleaning Suggestions**

- **Endpoint:** `/generate_cleaning_suggestions/`
- **Method:** `GET`
- **Payload:** `None`
- **Response:** Returns suggested data cleaning actions (e.g., removing duplicates, filling missing values).

#### **🔹 Apply Cleaning Suggestions**

- **Endpoint:** `/apply_cleaning_suggestions/`
- **Method:** `POST`
- **Payload:** Leave empty to apply all suggestions or specify particular suggestions.
  ```json
  {
      "indices": [0, 2, 4]
  }
  ```
- **Response:** Cleans the dataset based on the selected indices.

#### **🔹 Generate Aggregation Suggestions**

- **Endpoint:** `/aggregation_suggestions/`
- **Method:** `GET`
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

---

### **2️⃣ Joining Files**

#### **🔹 Upload Files**

- **Endpoint:** `/upload/`
- **Method:** `POST`
- **Payload Format:**
  ```json
  {
      "file1": "File1.csv",
      "file2": "File2.csv"
  }
  ```
- **Response:** Uploads multiple files for joining operations.

#### **🔹 Run Join Operation**

- **Endpoint:** `/analyze-join-suggestions/`
- **Method:** `GET`
- **Payload:** `None`
- **Response:** Joins files based on matching criteria.

---

### **3️⃣ Feature Engineering**

#### **🔹 Generate Feature Suggestions**

- **Endpoint:** `/suggest_methods/`
- **Method:** `GET`
- **Payload:** `None`
- **Response:** Suggests new feature transformations.

#### **🔹 Apply Feature Suggestions**

- **Endpoint:** `/apply_feature_selection_methods/`
- **Method:** `POST`
- **Payload Format:**
  ```json
  {
    "selected_methods": [
      {
        "method_name": "variance_threshold",
        "category": "variance_based",
        "reason": "This method is suitable for removing numerical features with low variance, which helps in eliminating constant or near-constant features that do not contribute to the dataset.",
        "priority": "high"
      },
      {
        "method_name": "quasi_constant_removal",
        "category": "variance_based",
        "reason": "This method identifies and removes features where one value dominates, which is useful for both numerical and categorical features, ensuring that the dataset remains informative.",
        "priority": "high"
      }
    ]
  }
  ```
- **Response:** Applies feature selection methods.

---

### **4️⃣ Model Training & Inference**

#### **🔹 Model Training**

- **Endpoint:** `/model_training/`
- **Method:** `GET`
- **Payload:** `None`
- **Response:** Trains the model on the dataset.

#### **🔹 Model Selection**

- **Endpoint:** `/model_selection/`
- **Method:** `POST`
- **Payload:** `None`
- **Response:** Selects the best model based on evaluation metrics.

#### **🔹 Model Inference**

- **Endpoint:** `/model_inference/`
- **Method:** `GET`
- **Payload:** `None`
- **Response:** Runs inference using the trained model.

---

### **5️⃣ Download Processed Data**

#### **🔹 Download CSV**

- **Endpoint:** `/download_csv/`
- **Method:** `POST`
- **Payload Format:**
  ```json
  {
      "stage": "Feature Engineering"
  }
  ```
- **Response:** Downloads the requested processed dataset.

---

### **📌 API Endpoints**

> Below are all the available API endpoints for you to use. The ones explained above are some of the most important endpoints.

- `/upload_file_clean_agent/`
- `/generate_cleaning_suggestions/`
- `/apply_cleaning_suggestions/`
- `/view_dataset/`
- `/cleaning_summary/`
- `/column_mapping/`
- `/aggregation_suggestions/`
- `/apply_aggregations_suggestions/`
- `/upload/`
- `/analyze-join-suggestions/`
- `/identify_category/`
- `/confirm_category/`
- `/generate_field_mappings/`
- `/confirm_suggested_mappings/`
- `/modify_field_mappings/`
- `/add_critical_fields/`
- `/suggest_methods/`
- `/apply_feature_selection_methods/`
- `/download_csv/`
- `/view_dataframe/`
- `/reset_session/`
- `/session_debug/`
- `/validate_mappings/`
- `/convert_data_types/`
- `/leakage_detection/`
- `/categorical_features/`
- `/data_split/`
- `/model_training/`
- `/model_selection/`
- `/model_inference/`

🚀 **This POC aims to automate data preparation efficiently!** 🚀

