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


## 2️⃣ Bit‑Plane Decomposition
Each bit plane was extracted by shifting and masking individual bits of the pixel values.

The resulting 8 images span from Bit 0 (lowest) to Bit 7 (highest).

🧩 Code snippet excerpt:


content_copy
python

note_add
ویرایش با Canvas
bit_plane = ((image >> i) & 1) * 255
📍 «در این بخش باید تصویر سری هشت‌تایی کامرمن و تصویر سری هشت‌تایی سینوسی مصنوعی قرار گیرد

(خروجی‌هایی که هرکدام عنوان دارند: “Cameraman - Bit n” و “Sinusoidal Synthetic - Bit n”).»

## 3️⃣ Bit‑Plane Visual Interpretation
Lower bits (0–3): Capture salt‑and‑pepper details and noise patterns.
Higher bits (4–7): Describe dominant structures, shapes, and intensity transitions.
In the Cameraman, the contour and silhouette are primarily visible in bits 6 and 7.

In the Sinusoidal Synthetic, each bit plane represents a frequency‑modulated band of alternating stripes.

📍 «در این بخش فقط یکی از مجموعه تصاویر کامل هشت‌تایی را قرار بده (مثلاً مجموعه کامرمن که وضوح بیشتری دارد).»

## 4️⃣ Manual Histogram Plotting
To analyse the binary distribution per plane, pixel counts for each intensity (0 or 255) were computed manually and rendered as side‑by‑side bar rectangles.

🧮 Code excerpt:


content_copy
python

note_add
ویرایش با Canvas
plt.fill([x_left, x_left, x_right, x_right],
         [0, y, y, 0],
         color='black' if x == 255 else 'gray')
Four representative bits were selected: Bits 7, 5, 3, 0, for both images.

📍 «در این بخش باید دو تصویر هیستوگرام دستی را بگذاری: یکی مربوط به کامرمن و یکی مربوط به سینوسی مصنوعی (تصاویر نمودارهای چهارگانه با محور Intensity و Pixel Count).»
