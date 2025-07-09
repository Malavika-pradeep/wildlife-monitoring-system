
#  Wildlife Monitoring and Poaching Prevention using OpenCV

This project implements a lightweight computer vision pipeline for **wildlife detection and poaching prevention** using **pure OpenCV techniques** — no deep learning involved. The system operates on a sequence of wildlife images and uses **salience detection, segmentation, and temporal consistency analysis** to identify animals.

---

##  **Project Highlights**

- ✅ **Pure OpenCV-based** solution — no need for heavy models or training datasets.
- ✅ Combines **temporal**, **spatial**, and **salience-based attention** to detect foreground objects.
- ✅ Lightweight classification using **temporal patch matching and histogram correlation**.
- ✅ Designed for **wildlife monitoring** and **basic anti-poaching surveillance** in remote areas.

---

##  **Step-by-Step Working**

### 1️⃣ **Image Loading**
- Loads a sequence of 5 wildlife images using OpenCV and `glob`.
- Displays them for inspection.

### 2️⃣ **Salience Detection (Attention Mapping)**

#### ✅ Temporal Salience:
- Difference between current image and blurred background model using `cv2.absdiff`.

#### ✅ Spatial Salience:
- Sharp edges detected by subtracting Gaussian-blurred image from the original.

#### ✅ Combined Salience:
- Merge both maps to get attention regions likely to contain animals.

### 3️⃣ **Graph Cut-Based Foreground Segmentation**
- Applies distance transform-based refinement.
- Generates segmentation proposals using multiple alpha thresholds.

### 4️⃣ **Foreground Mask and Bounding Box Extraction**
- Threshold + contour detection to generate bounding boxes.

### 5️⃣ **Temporal Patch Matching**
- Histogram comparison across image sequence.
- Weighted scoring for temporal and visual similarity.

### 6️⃣ **Classification: Animal vs. Background**
- **Score ≤ 0** → Animal  (Green Box)
- **Score > 0** → Background  (Red Box)

---

##  **Installation & Requirements**

Install the required dependencies:

```bash
pip install opencv-python numpy matplotlib