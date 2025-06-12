## 🧪 Model Experimentation Structure

Organized for clarity across binary (B) and multiclass (M) model tasks.

### 1. 📥 Imports
All required libraries.

### 2. 🧰 Helper Functions
- **2.0 Shared**: evaluation, logging, plotting
- **2.1 B-specific**: binary ROC, class weights
- **2.2 M-specific**: confusion matrices, multiclass ROC

### 3. ⚙️ Config Lists
- **3.1 B Models**: B-01 to B-10 configurations
- **3.2 M Models**: M-01 to M-09 configurations

### 4. 🧠 Training Functions
- **4.1 B Models**: `train_b_models()`
- **4.2 M Models**: `train_cell_cnn_models()`
> Universal function possible, but separated for clarity

### 5. 📊 Visualisations (post-training)
- **5.1 B Models**:
  - a. Accuracy/Loss
  - b. ROC curves
- **5.2 M Models**:
  - a. Confusion matrices (4 per row)
  - b. Per-class ROC curves (4 per row)

### 6. 📋 Results Tables
- **6.1** `is_cancerous_results` – B model F1 scores
- **6.2** `cell_type_results` – M model F1 scores


### General Admin

1. **Image Folder Handling (`patch_images`)**
   - Due to GitHub’s file size limitations, the `patch_images` folder (containing ~20k images) **cannot be committed** to the repository.
   - Before running the notebook:
     - Manually drag the `patch_images` folder into:  
       `Image_classification_data/patch_images`
   - Example project structure:
     ```
     .
     ├── Image_classification_data
     │   ├── data_labels_mainData.csv
     │   ├── data_labels_extraData.csv
     │   └── patch_images/        ← DROP IMAGE FOLDER HERE
     ├── s3925523_s3886768.ipynb
     └── README.md
     ```

2. **Installing TensorFlow + Environment Setup**
   - Ensure you're using **Python 3.10.x** (not 3.12+ or older than 3.7).
   - Set up a conda environment (recommended):
     ```bash
     conda create -n ml-ass2 python=3.10
     conda activate ml-ass2
     pip install tensorflow pandas matplotlib pillow scikit-learn
     ```
   - You may also need to manually install `jinja2` if table rendering breaks:
     ```bash
     pip install jinja2
     ```

3. **Model Training Time**
   - The full **model experimentation block (FNN + CNN)** can take **10–15 minutes on first run**, especially with image loading and early stopping.

---

### Tasks To Do / Assist With

#### Notebook + Report Review

1. **Validation Set**
   - The dataset is split into train/val/test, but the validation set is currently **not fully used**.
   - Please help **integrate the validation set into hyperparameter tuning** or model comparisons.

2. **Improve Image Viewer**
   - Make the image preview block in the EDA section **look nicer** (e.g., titles, spacing, grid layout).

3. **Write EDA Observations**
   - Add **written analysis** of the dataset after the EDA visualizations:
     - Class imbalance
     - Cancerous/non-cancerous distribution
     - Cell type frequencies

4. **General Report Editing**
   - Many sections are still adapted from a previous project.
   - Please help **reword, restructure, and rewrite** to make the report cohesive and task-specific.

5. **Check Criteria Compliance**
   - Review what has been implemented so far (code + models) and **compare it with assignment criteria**.
   - Identify any missing elements to make the notebook **ready for submission**.

  
