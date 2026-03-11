import os
import shutil
from classifier.image_classifier import simple_classifier


class GalleryManager:

    def __init__(self, image_folder):

        self.folder = image_folder

    def organize(self):

        for file in os.listdir(self.folder):

            if not file.lower().endswith((".jpg", ".png")):
                continue

            path = os.path.join(self.folder, file)

            label = simple_classifier(path)

            target = os.path.join(self.folder, label)

            os.makedirs(target, exist_ok=True)

            shutil.move(path, os.path.join(target, file))

            print("Moved", file, "to", label)
