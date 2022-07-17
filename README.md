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



**Explanation of thought process**
1st method: I tried to segment the barrel out of the background using edge detection. I used the cv2.Canny() function to detect edges. I tried to better my results using different levels of blurring using cv2.medianBlur() and defining a lower bound threshold 0 or 70% of the median pixel value defined using np.median(), whichever is higher and an upper threshold 255 or 30% above the median value, whichever is lower. This is the best result I got of the image I was working on:

<img width="283" alt="Screenshot 2022-07-17 at 14 31 15" src="https://user-images.githubusercontent.com/97196465/179398414-c5544188-dc52-46ff-8d7f-f224c5c979de.png">

Using cv2.drawContours(), I then tried to fill the countours of the barrel, however, even with varying the thresholds I only managed to get the lights in the back to fill and not the contour as seen below:

<img width="559" alt="Screenshot 2022-07-17 at 14 36 38" src="https://user-images.githubusercontent.com/97196465/179398713-72b0f11c-2f4d-4243-9192-a34756b1810f.png">

2nd method: I segmented by color instead of my contour, which looking back was the obvious choice. HSV seemed to be the appropriate color space as HSV After a bit of research since the HSV separate color from intensity which is important as the barrel must be segmented in different lightings. Red on the hsv color map is present on the two extremities: HUE(0-10) and HUE(170-180). At first I created 2 masks and overlayed them to include both extremeties of the HSV color map. This way all the nuances of red would all be present. However, it turns out that the barrel is more of a pink-red then it is an orange-red and the higher values of HUE were better for differentiating the barrel from other red objects like from the dark red chairs seen below. On the left side is the original picture, in the middle the segmented mask 







