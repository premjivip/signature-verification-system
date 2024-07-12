## Signature-Matching
Application to detect the similarity of two signatures.

This Application helps mathematically evaluate similarity of two signatures. 
Simply capture or upload the picture of both signatures to be compared.
Both the images will be displayed on the screen that are being compared.
The popup will show the percentage match of the signatures.
The signatures are compared using structural_similarity in skimage.metrics package.


## Prerequisites
1. Python >=3.6
2. OpenCV
3. Scipy
4. Scikit-image


## Run
1. `pip install requirements.txt`
2. `python main.py`


## Please open an issue if
* you have any suggestion to improve this project
* you noticed any problem or error


## signature.py
```C
import cv2
from skimage.metrics import structural_similarity as ssim

# TODO add contour detection for enhanced accuracy


def match(path1, path2):
    # read the images
    img1 = cv2.imread(path1)
    img2 = cv2.imread(path2)
    # turn images to grayscale
    img1 = cv2.cvtColor(img1, cv2.COLOR_BGR2GRAY)
    img2 = cv2.cvtColor(img2, cv2.COLOR_BGR2GRAY)
    # resize images for comparison
    img1 = cv2.resize(img1, (300, 300))
    img2 = cv2.resize(img2, (300, 300))
    # display both images
    cv2.imshow("One", img1)
    cv2.imshow("Two", img2)
    cv2.waitKey(0)
    cv2.destroyAllWindows()
    similarity_value = "{:.2f}".format(ssim(img1, img2)*100)
    # print("answer is ", float(similarity_value),
    #       "type=", type(similarity_value))
    return float(similarity_value)


# ans = match("D:\\Code\\Git stuff\\Signature-Matching\\assets\\1.png",
#             "D:\\Code\\Git stuff\\Signature-Matching\\assets\\3.png")
# print(ans)
# print(type(ans))

