# Brain Tumor Detection

## 1. Project Overview

This project provides a complete solution for brain tumor analysis from MRI scans. It utilizes deep learning models to perform two key tasks:

1.  **Classification:** A Vision Transformer (ViT) model classifies the MRI scan into one of four categories: `glioma`, `meningioma`, `pituitary` tumor, or `no tumor`.
2.  **Segmentation:** A U-Net model generates a segmentation mask, highlighting the potential location and area of the tumor on the MRI scan.

The entire application is wrapped in a user-friendly web interface powered by Gradio, allowing for easy interaction and visualization of the results.

---

## 2. Models

* **Classification Model:** A Vision Transformer (ViT) was trained for the classification task. The complete training process, data preprocessing, and augmentation details can be found in the `ViT_Train_Classification.ipynb` notebook.
* **Segmentation Model:** A U-Net architecture was used for the segmentation task.

---

## 3. Setup and Installation

Follow these steps to set up and run the application on your local machine.

### Step 1: Clone the Repository

First, clone this repository to your local machine using git:

```bash
git clone <your-repository-url>
cd <repository-directory>
```

### Step 2: Assemble the Classification Model

The Vision Transformer model (`brain_tumor_vit_model_5extra.h5`) has been split into multiple parts due to its size. You must reassemble it before running the application.

1.  Locate the `.zip` file containing the model parts (e.g., `brain_tumor_vit_model.zip`).
2.  Extract the contents of this zip file. This will merge the parts and create the complete `brain_tumor_vit_model_5extra.h5` file.

### Step 3: Install Dependencies

This project requires several Python libraries. It is recommended to create a virtual environment to manage these dependencies.

```bash
# Create a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

# Install the required packages
pip install tensorflow gradio numpy opencv-python Pillow
```

---

## 4. Running the Application

### Step 1: Place the Model Files

Ensure that the following two model files are placed in the root directory of the project:

1.  `brain_tumor_vit_model_5extra.h5` (The complete ViT model you assembled in the setup step).
2.  `seg_model_v2.h5` (The U-Net segmentation model).

### Step 2: Launch the Gradio App

Run the main application script from your terminal:

```bash
python app.py
```

*(Note: If you named your main Gradio script something else, use that name instead of `app.py`)*

### Step 3: Access the Web Interface

After running the script, your terminal will display a message indicating that the server is running, along with a local URL.

```
Running on local URL:  [http://127.0.0.1:7860](http://127.0.0.1:7860)
```

Open this URL in your web browser to access the Brain Tumor Analysis application.

---

## 5. How to Use the App

The web interface is simple and intuitive:

1.  **Upload Image:** Drag and drop an MRI scan into the image box, or click on it to open a file browser.
2.  **Analyze:** Once an image is uploaded, click the "Analyze Image" button.
3.  **View Results:**
    * The **Classification Results** will appear on the right, showing the predicted class and the model's confidence scores.
    * The **Segmentation Mask** will be displayed below the classification results, visually highlighting the predicted tumor area.
