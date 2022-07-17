# Segmentation_mask_for_orange_barrels

**Explanation**
This code takes an input of the same orange barrel in different localisations and lightings and outputs a segmentation mask of only two colors: black and white. The white pixel being an orange pixel and a non-orange pixel a black pixel.




**Example**
Here is an example for one image: on the left the original image, on the right the segmentation mask

<img width="603" alt="Screenshot 2022-07-17 at 13 59 32" src="https://user-images.githubusercontent.com/97196465/179397182-f59e3a6e-be33-45b1-8559-bfa7aef8ce84.png">





**Requirements to run this code:**
- Have the original pictures of the orange barrels in a folder named 'input' in the same folder that this code file is saved in.
- Have a folder named 'output' for the processed barrel images to be saved in, situated in the same folder that this code file is saved in.
- The variable path must be modified to fit the path to the localisation where the source code is saved in your directory.
- OpenCV 4.6.0
- Python 3.9.7
- Libraries imported: cv2, numpy and os

