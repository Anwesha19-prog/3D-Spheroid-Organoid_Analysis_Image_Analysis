# Spheroid_Analysis
spheroidAnalysis
Analysis of spheroid images for varying intensity

MATLAB Script -> SpheroidAnalysis_input.m

Author: Dr. Anwesha Sarkar, Bhupesh Verma

Date: October 10, 2023

Description: This script analyses the spheroids and outputs Offset value (in μm), Area of ROI (in pixels), Total (Integrated) intensity, Mean Intensity, Median intensity, Std. Deviation of Intensity, Maximum intensity in the excel sheet. The excel provides these values in a region of length specified by the 'offset length' variable.

Usage: This script requires spheroidAnalysis.m, calc_intensity.m and get_conv_hull.m in the same folder as this script. User needs to input the name of the image to be process ONLY IN TIF format. User also needs to specify the size of the spheroids from the experiments and adjust the minComponentSize to remove the noise from the image. Also dilation_radius can be increased if the image contains larger holes which needs to be filled.

Notes:

User input required for physical_size_of_image and offset_length

It is advised to first find the minComponentSize and dilation_radius variable for an image. Recommended values of minComponentSize are 20, 40, 60 and 80 for minComponentSize AND 5, 10, 20 and 30 for dilation_radius.

In this code, it is assumed that images captured have the same height and width (or no. of pixels in both directions)

This code is prepared for spheroid analysis for Anwesha Sarkar's PhD thesis at University College Dublin (UCD)

<img width="413" alt="GitHub1" src="https://github.com/user-attachments/assets/2cb97264-92f1-4e40-b398-91d29d77fb02" />
<img width="434" alt="GitHub2" src="https://github.com/user-attachments/assets/5eb0dd77-1511-4bac-8bfd-d6868b2a7b4c" />
<img width="561" alt="GitHub3" src="https://github.com/user-attachments/assets/a897eb78-566c-4031-b3fc-86a8bcd07f89" />

