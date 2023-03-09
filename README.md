# image-editor
All the pixels of the image are stored as dinamically alocated matrices, using malloc() and free() functions from the stdlib.h library.

*) I defined the datatype 'image', that contains all the necessary information about the loaded image, including the dinamically allocated matrices of pixels.

*) I defined the structure 'filter_values' that stores the kernel values of the filters that can be applied.

*) There are 8 possible commands that can be recieved from input:

LOAD - Load the image from the given file into memory
SELECT ALL - Select the whole image
SELECT - Select a portion of the image, situated between the given indices
CROP - Crop the selection, keeping the new smaller image
ROTATE - Rotate the selection with given angle
APPLY - Apply one of the filters to the selection
SAVE [ascii] - Save the selection into a plain / ascii file
EXIT - Free the allocated memory and exit the program
Commands:
LOAD

free the memory of the previously loaded image, if it exists
store all the information located in the header about the new image (magic word, width, height, max value)
allocate memory for the pixel matrices (1 matrix for grayscale / 3 matrices for RGB)
using the magic word, decide whether the image is stored as plain or binary and read the values accordingly
store the value of each pixel in the specific matrices (gray/red/green/blue)
select the whole image
SELECT ALL

select the whole image
same as 'SELECT 0 0 img->width img->height'
SELECT

check if the coordinates are valid
memorise the selection
CROP

allocate memory for a temporary matrix that will represent the cropped channel
crop each channel based on the given selection and store the values in the specific temporary matrix
free memory of the old channel
allocate memory for the new channel that will have a smaller no. of pixels
save the values from the temporary matrix
free the memory for the temporary matrix
ROTATE

check if angle is a valid integer
rotate the selection for each channel to the right until meeting the desired angle I. if the selection is not equal to the whole matrix: - allocate memory for a temporary matrix that stores the rotated selection - update the values in the selection to the new ones - frees the temporary matrix II. if the selection is equal to the whole matrix: - allocate memory for a temporary matrix that stores the rotated image - free the memory for the given channel with dimesions w x h - allocate memory for the channel with dimensions h x w - set the values in the channel to the new ones - free the temporary matrix * after each image rotation make sure to change the width & height of the image and select all of it
APPLY

apply one of the filters: EDGE, SHARPEN, BLUR, GAUSSIAN BLUR
allocate new matrices for each color channel (RGB), which will initially have the elements of the selection
compute the kernel sum for each pixel, then save the sum as the new pixel value
update the value for the pixels in selection to the new filtered ones
free the temporary matrices
SAVE [ascii]

read the file where the image should be saved
check whether keyword 'ascii' is present => image will be saved as plain; otherwise, image will be saved as binary
save the new magic word and the image's header in the file
save the pixel values for each channel, either as plain or binary
close the files
EXIT

free the memory for the loaded image, if it exists
stop the program
