import os
from PIL import Image
import numpy as np

def simple_classifier(image_path):

    img = Image.open(image_path)
    img = img.resize((64, 64))

    arr = np.array(img)

    r = arr[:, :, 0].mean()
    g = arr[:, :, 1].mean()
    b = arr[:, :, 2].mean()

    if g > r and g > b:
        return "nature"

    if r > g and r > b:
        return "people"

    return "other"
