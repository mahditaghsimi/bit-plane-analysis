# bit-plane-analysis
Python project for bit-plane slicing and histogram visualization of grayscale images using OpenCV and Matplotlib. Includes educational examples with Cameraman and Sinusoidal test patterns.
## Overview
In an 8‑bit grayscale image, each pixel intensity is represented by 8 binary digits.
The least significant bits (LSBs) capture fine details and noise, while the most significant bits (MSBs) carry the general structure and brightness information.

## 1️ Input Images
Two test cases were used:
Cameraman — natural photograph, classic in image processing.
Sinusoidal Synthetic — artificially generated diagonal wave pattern.

<img width="256" height="256" alt="Sinusoidal-Synthetic" src="https://github.com/user-attachments/assets/4b5836c7-05f0-4b9f-b02b-96cb12f8f9f7" />
<img width="256" height="256" alt="Cameraman" src="https://github.com/user-attachments/assets/b883ce50-ce18-4672-afb3-735721ee6e69" />


## 2️ Bit‑Plane Decomposition
Each bit plane was extracted by shifting and masking individual bits of the pixel values.
The resulting 8 images span from Bit 0 (lowest) to Bit 7 (highest).
Code snippet excerpt:

```bit_plane = ((image >> i) & 1) * 255```
<img width="1189" height="688" alt="download (1)" src="https://github.com/user-attachments/assets/23c6aac2-cdd1-4045-a9de-a00d95da74bf" />
<img width="1189" height="688" alt="download" src="https://github.com/user-attachments/assets/70960b13-a998-4223-b4b3-ec1e60c00b5d" />


## 3️ Bit‑Plane Visual Interpretation
Lower bits (0–3): Capture salt‑and‑pepper details and noise patterns.
Higher bits (4–7): Describe dominant structures, shapes, and intensity transitions.
In the Cameraman, the contour and silhouette are primarily visible in bits 6 and 7.

In the Sinusoidal Synthetic, each bit plane represents a frequency‑modulated band of alternating stripes.
<img width="1189" height="688" alt="download" src="https://github.com/user-attachments/assets/3985f6b1-bf2f-42b8-8357-4f2164755872" />


## 4️ Manual Histogram Plotting
To analyse the binary distribution per plane, pixel counts for each intensity (0 or 255) were computed manually and rendered as side‑by‑side bar rectangles.
Code excerpt:
```
plt.fill([x_left, x_left, x_right, x_right],
         [0, y, y, 0],
         color='black' if x == 255 else 'gray')
Four representative bits were selected: Bits 7, 5, 3, 0, for both images.
```
<img width="989" height="790" alt="download (3)" src="https://github.com/user-attachments/assets/89459c29-15a0-4705-b270-69836fe10041" />
<img width="989" height="790" alt="download (2)" src="https://github.com/user-attachments/assets/8a11bace-1951-491e-9ffa-50a7d3ec3a30" />

## 5️ Comparative Observations
Image Type	Dominant Bits	Structure Visibility	Pixel Intensity Distribution
Cameraman	6–7	Clear object boundaries	Skewed toward 0 & 255
Sinusoidal Synthetic	5–7	Periodic pattern	Balanced binary bands
