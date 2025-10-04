# Lab Assignment Submission

This repository contains the solutions for the take-home assignment.

## Q1: Vision Transformer on CIFAR-10

### How to Run
1.  Open `q1.ipynb` in Google Colab with a GPU runtime.
2.  Connect to Google Drive when prompted by the first cell.
3.  Run all cells from top to bottom. The notebook will train the model, save the best version to Google Drive, and report the final accuracy.

### Best Model Configuration
-   **Epochs Trained:** 15
-   **Patch Size:** 4x4
-   **Model Depth:** 7
-   **Embedding Dimension:** 384
-   **Optimizer:** AdamW with CosineAnnealingLR

### Results
| Model | Test Accuracy |
| :--- | :---: |
| ViT (15 Epochs) | 70.68% |  <- 

---

## Q2: Text-Driven Image Segmentation with SAM

### Pipeline Description
This notebook (`q2.ipynb`) demonstrates text-prompted image segmentation. The pipeline is as follows:
1.  **Text-to-Box:** It uses a pre-trained **GroundingDINO** model to take a text prompt and an image, and it outputs bounding boxes for the described object.
2.  **Box-to-Mask:** These bounding boxes are then fed as prompts to the **Segment Anything Model (SAM)** to generate a precise segmentation mask.
3.  **Visualization:** The final mask is overlaid on the original image.

### Limitations
-   The pipeline's success is highly dependent on the detection capabilities of the pre-trained GroundingDINO model.
-   During testing, the `grounding-dino-base` model successfully detected some common objects, but failed on others (e.g., 'cat', 'circuit') with the given confidence thresholds.
-   **Crucially, the pipeline is robust.** Instead of crashing when an object is not detected, it handles the case gracefully and displays a "not found" message, demonstrating proper error handling.
-   **Note on SAM 2:** The assignment mentioned SAM 2, but due to its limited public availability, this implementation uses the original Segment Anything Model (SAM).
