```markdown
#Text Editor for PPM and PGM Images

This project is a command-line text editor designed to manipulate PPM and PGM image files. It supports a range of operations such as loading, selecting, editing, saving, and processing images. The program handles commands sequentially in a loop until the `EXIT` command is received.

---

## Supported Commands

### 1. **LOAD**
- Loads a PPM or PGM image file into memory.
- Skips comments and reads the image type and pixel data.
- Supports grayscale, black-and-white, and color images.
- If the file does not exist or is invalid, displays an error message and frees any previously loaded image data.
- By default, the entire image is selected after loading.

---

### 2. **SELECT**
- Allows selecting a specific region of the image or the entire image.
- **Usage:**
  - `SELECT ALL`: Selects the entire image.
  - `SELECT x1 y1 x2 y2`: Selects a rectangular region specified by the coordinates `(x1, y1)` and `(x2, y2)`.
- If the coordinates are invalid or if no image is loaded, an error message is displayed.

---

### 3. **SAVE**
- Saves the current image to a file.
- Supports ASCII and binary formats, depending on the command's format specifier.
- Writes pixel values based on the image type (grayscale or color).

---

### 4. **CROP**
- Crops the image to the selected region.
- Allocates new memory for the cropped region and updates the image dimensions.
- Frees the memory of the original image and replaces it with the cropped version.

---

### 5. **EQUALIZE**
- Equalizes the histogram of the grayscale image.
- Computes the frequency of each pixel value and adjusts the pixel intensities using a standard histogram equalization algorithm.

---

### 6. **APPLY**
- Applies a filter to the image.
- Supported filters: `edge`, `sharpen`, `gaussian_blur`, and `blur`.
- Filters are applied using a 3x3 kernel and involve convolution calculations.
- If the image is not in color format, an error message is displayed.

---

### 7. **HISTOGRAM**
- Generates a histogram for grayscale or black-and-white images.
- Groups pixel intensities into bins and calculates their frequencies.
- Displays the histogram using stars (`*`) to represent frequency magnitudes.

---

### 8. **ROTATE**
- Rotates the image by a specified angle (90°, 180°, 270°).
- Only square selections can be rotated unless the entire image is selected.
- Supports both grayscale and color images.

---

### 9. **EXIT**
- Frees all allocated memory and terminates the program.
- Displays an appropriate message if no image is loaded.

---

## Implementation Details

1. **Memory Management**:
   - Dynamically allocates memory for image matrices and auxiliary structures.
   - Frees memory after operations like cropping, equalizing, and exiting.

2. **Error Handling**:
   - Verifies the validity of commands and their parameters.
   - Displays meaningful error messages for invalid operations or missing files.

3. **Image Processing**:
   - Handles color and grayscale images differently where necessary.
   - Implements efficient algorithms for operations like filtering, cropping, and histogram generation.

4. **File Handling**:
   - Reads and writes image data in both ASCII and binary formats.
   - Ensures compatibility with standard PPM and PGM image formats.

---

## Summary
This text-based image editor provides essential functionalities for managing and processing PPM and PGM images. With its modular and efficient implementation, it enables users to perform advanced image manipulations without a graphical interface.
```
