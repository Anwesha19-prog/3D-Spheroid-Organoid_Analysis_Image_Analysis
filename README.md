# 3D Spheroid Organoid Image Analysis (MATLAB)

Quantitative analysis of **3D spheroid/organoid microscopy images** to measure morphology and fluorescence/intensity statistics in user-defined **offset regions** (e.g., shells/rings around a spheroid). Designed for both **biologists** (easy-to-run workflow, clear outputs) and **image-analysis users** (tunable segmentation parameters).

---

## What this project does

Given a **single-channel `.tif` image** containing a spheroid/organoid, the pipeline:

1. Segments the spheroid region of interest (ROI)
2. Optionally fills holes / removes small noise components
3. Computes intensity metrics within the ROI and within regions defined by an **offset length**
4. Exports results to an **Excel file** including:

- Offset value (μm)
- Area of ROI (pixels)
- Total / Integrated intensity
- Mean intensity
- Median intensity
- Standard deviation of intensity
- Maximum intensity

---

## Repository entry point

- **Main script:** `SpheroidAnalysis_input.m`  
- **Required helper functions (must be in the same folder):**
  - `spheroidAnalysis.m`
  - `calc_intensity.m`
  - `get_conv_hull.m`

---

## Requirements

- **MATLAB** (tested in a standard MATLAB environment)
- Input images must be **TIF/TIFF (`.tif`) format**  
  > Current workflow assumes images have **equal height and width** (square images), or at least the same pixel count in both directions.

---

## Quick start (biologists)

1. Put the following files in the **same folder**:
   - `SpheroidAnalysis_input.m`
   - `spheroidAnalysis.m`
   - `calc_intensity.m`
   - `get_conv_hull.m`

2. Place your **`.tif` spheroid image(s)** in the same folder (or note their paths).

3. Open MATLAB, set your **Current Folder** to this project folder.

4. Run:
   ```matlab
   SpheroidAnalysis_input
   ```

5. When prompted / when editing the script, provide:
   - `physical_size_of_image` (real-world image size / calibration)
   - `offset_length` (length of the offset region in **μm**)
   - image filename (must be `.tif`)

6. An **Excel spreadsheet** will be generated with the computed measurements.

---

## Key parameters to tune (image analysis users)

The segmentation quality depends strongly on your imaging conditions. The following parameters are commonly adjusted:

### `minComponentSize`
Removes small connected components (noise).  
**Recommended trial values:** `20`, `40`, `60`, `80`

### `dilation_radius`
Controls how strongly gaps/holes are closed during morphological operations.  
Increase this if your spheroid mask has internal holes.  
**Recommended trial values:** `5`, `10`, `20`, `30`

### Practical tuning workflow (recommended)
1. Pick a **representative image**
2. Sweep `minComponentSize` and `dilation_radius` using the recommended values above
3. Visually confirm the ROI mask matches the spheroid boundary
4. Lock parameters and process the remaining images

---

## Inputs and outputs

### Input
- `.tif` image of a spheroid/organoid (single image per run, as currently described)

### Output (Excel)
One row (or a set of rows) containing:
- Offset (μm)
- ROI area (pixels)
- Integrated intensity
- Mean / median intensity
- Intensity standard deviation
- Maximum intensity

> The Excel values are computed for a region defined by the `offset_length` variable.

<img width="413" alt="GitHub1" src="https://github.com/user-attachments/assets/2cb97264-92f1-4e40-b398-91d29d77fb02" />
<img width="434" alt="GitHub2" src="https://github.com/user-attachments/assets/5eb0dd77-1511-4bac-8bfd-d6868b2a7b4c" />
<img width="561" alt="GitHub3" src="https://github.com/user-attachments/assets/a897eb78-566c-4031-b3fc-86a8bcd07f89" />

---

## Assumptions and limitations

- Images are assumed to have the **same number of pixels in x and y** (square acquisition or equivalent handling).
- Input format: **TIF only**
- This code is parameter-sensitive; you should validate segmentation on a subset of images before batch analysis.

---

## Citation / attribution

**Author:** Dr. Anwesha Sarkar  
**Date:** October 10, 2023  

Prepared for spheroid analysis as part of Dr. Sarkar’s PhD thesis at **University College Dublin (UCD)**.

---

## Suggested next improvements (optional)

Possible extension to the the README and/or the codebase includes:

- Batch processing of multiple images in a folder
- Example images + expected output screenshot
- A “Troubleshooting” section (common segmentation failures and fixes)
- Clear calibration guidance (pixel size, μm-per-pixel)
- MATLAB version/toolbox notes (if any are required)


