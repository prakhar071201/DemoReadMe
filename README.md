
# 🚀 **Data Prep Agent POC**

A Proof of Concept (POC) showcasing how data preparation can be automated using intelligent agents. This open-source project demonstrates how businesses can utilize these agents to handle data cleaning, aggregation, feature engineering, model training, and inference with ease. 

## ⚠️ **Note**

> Uploaded files are stored in the session. If you refresh or close the tab, the session will be lost, and you'll need to restart the process.

---

## 📦 **Project Setup**

### 🖥️ **Backend Setup**

1. **Clone the Repository:**

   ```bash
   git clone <repository-link>
   cd <repository-folder>
   ```

2. **Create a Virtual Environment:**

   ```bash
   python -m venv venv
   ```

3. **Activate the Virtual Environment:**

   - **For Windows:**
     ```bash
     venv\Scripts\activate
     ```
   - **For macOS/Linux:**
     ```bash
     source venv/bin/activate
     ```

4. **Install the Required Packages:**

   ```bash
   pip install -r requirements.txt
   ```

5. **Export the OpenAI API Key:**

   ```bash
   export OPENAI_API_KEY="your-openai-api-key"
   ```

6. **Start the Backend Server:**

   ```bash
   python manage.py runserver
   ```

---

### 🌐 **Frontend Setup**

1. **Clone the Repository:**

   ```bash
   git clone <repository-link>
   cd <frontend-folder>
   ```

2. **Install Dependencies:**

   ```bash
   npm install
   ```

3. **Run the Frontend:**

   ```bash
   npm start
   ```

---

## ⚙️ **Making Changes**

### 📡 **Adding New APIs**

- Add new API functions inside `apiCalls.js` for easy integration with the frontend.
- Example:
  ```javascript
  export const newApiFunction = async (payload) => {
    const response = await axios.post("/new-endpoint/", payload);
    return response.data;
  };
  ```

### 🧩 **Creating New Components**

- Build reusable components based on the APIs.
- Check the `components` folder for examples of existing components.

### 🗃️ **Backend Development**

- Create APIs using agents in the `views.py` file.
- Register new APIs in `urls.py` to expose them for frontend use.

---

## 📊 **Stages in Data Preparation**

### **1️⃣ Aggregation & Cleaning**

#### 🗂️ **Upload File**

- Upload your dataset to begin the data preparation process.

#### 🔹 **Generate Cleaning Suggestions**

- **Endpoint:** `/generate_cleaning_suggestions/`
- **Method:** `GET`
- **Response:** Suggested actions like removing duplicates, filling missing values, etc.

#### 🔹 **Apply Cleaning Suggestions**

- **Endpoint:** `/apply_cleaning_suggestions/`
- **Method:** `POST`
- **Payload:**
  ```json
  {
    "indices": [0, 2, 4]
  }
  ```
- Apply suggestions selectively or apply all by leaving the payload empty.

#### 🔹 **Generate Aggregation Suggestions**

- **Endpoint:** `/aggregation_suggestions/`
- **Method:** `GET`
- **Response:** Suggestions for aggregating numerical columns.

#### 🔹 **Apply Aggregation Suggestions**

- **Endpoint:** `/apply_aggregations_suggestions/`
- **Method:** `POST`
- **Payload:**
  ```json
  {
    "selected_methods": {
      "total_seats": ["mean", "max"],
      "assigned_seats": ["median", "min"]
    }
  }
  ```

---

### **2️⃣ Joining Files**

#### 🔹 **Upload Files**

- **Endpoint:** `/upload/`
- **Method:** `POST`
- **Payload:**
  ```json
  {
    "file1": "File1.csv",
    "file2": "File2.csv"
  }
  ```

#### 🔹 **Run Join Operation**

- **Endpoint:** `/analyze-join-suggestions/`
- **Method:** `GET`
- Automatically identifies and joins files based on matching columns.

---

### **3️⃣ Feature Engineering**

#### 🔹 **Generate Feature Suggestions**

- **Endpoint:** `/suggest_methods/`
- **Method:** `GET`
- Suggests potential transformations and new features to enhance model performance.

#### 🔹 **Apply Feature Suggestions**

- **Endpoint:** `/apply_feature_selection_methods/`
- **Method:** `POST`
- **Payload:**
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

---

### **4️⃣ Model Training & Inference**

#### 🔹 **Model Training**

- **Endpoint:** `/model_training/`
- **Method:** `GET`
- Trains the model on the dataset.

#### 🔹 **Model Selection**

- **Endpoint:** `/model_selection/`
- **Method:** `POST`
- Selects the best model based on evaluation metrics.

#### 🔹 **Model Inference**

- **Endpoint:** `/model_inference/`
- **Method:** `GET`
- Runs inference using the trained model.

---

### **5️⃣ Download Processed Data**

#### 🔹 **Download CSV**

- **Endpoint:** `/download_csv/`
- **Method:** `POST`
- **Payload:**
  ```json
  {
    "stage": "Feature Engineering"
  }
  ```
- Downloads the requested processed dataset.

---

## 📌 **API Endpoints**

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

---

## 🤖 **Why This POC?**
This project demonstrates the power of automation in data preparation. By leveraging intelligent agents, we can:

- **Save Time**: Automate repetitive tasks like cleaning and feature engineering.
- **Improve Accuracy**: Reduce human error with algorithmic checks.
- **Flexible Architecture**: Add new APIs and components effortlessly.

---

## 🚀 Contribute to the Project

Want to improve this project? Feel free to open issues, submit pull requests, and suggest new features!

```bash
# Fork this repository
# Create a new branch
git checkout -b feature-new-api

# Make your changes
# Commit and push
git add .
git commit -m "Added new API for data analysis"
git push origin feature-new-api
```

---

## 💬 Connect with Us

If you have questions, suggestions, or want to collaborate, feel free to reach out via issues or pull requests.


🚀 **This POC aims to automate data preparation efficiently!** 🚀
