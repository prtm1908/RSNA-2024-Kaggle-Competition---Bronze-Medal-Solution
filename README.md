# RSNA 2024 Lumbar Spine Degenerative Classification

This repository contains code for a two-stage approach to classify degenerative conditions in lumbar spine MRI scans. The solution uses a combination of vertebra detection and classification models to predict the severity of various spinal conditions.

## Overview

The solution consists of two main stages:

1. **Stage 1: Vertebra Detection and Localization**
   - Uses SpineNet to detect and localize vertebrae in the MRI scans
   - Identifies key vertebral levels (L1-L5 and S1)
   - Generates bounding boxes for each vertebral region

2. **Stage 2: Condition Classification**
   - Uses a 3D CNN model (CoAtNet) to classify conditions for each vertebral region
   - Implements a cumulative logit model for ordinal classification
   - Handles multiple conditions:
     - Spinal Canal Stenosis
     - Left/Right Subarticular Stenosis
     - Left/Right Neural Foraminal Narrowing
   - Provides severity predictions (normal/mild, moderate, severe)

## Technical Details

- Built using PyTorch and Open3D
- Uses cumulative logit heads for ordinal classification
- Implements a fallback mechanism for cases where vertebra detection fails
- Processes 3D MRI volumes with multiple modalities (T1, T2, T2/STIR)

## Dependencies

- PyTorch
- Open3D
- timm_3d
- spacecutter
- pydicom
- numpy
- pandas

## Usage

The notebook demonstrates the complete inference pipeline:
1. Load and preprocess MRI scans
2. Detect vertebrae and generate bounding boxes
3. Run classification on each vertebral region
4. Generate final predictions in the required submission format

## Output

The model generates predictions in a CSV format with the following columns:
- row_id: Unique identifier for each prediction
- normal_mild: Probability of normal/mild condition
- moderate: Probability of moderate condition
- severe: Probability of severe condition

## License

This project is part of the RSNA 2024 competition and follows the competition's terms and conditions. 
