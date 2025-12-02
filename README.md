# MNIST Dataset Using TensorFlow with Real Camera Capture

This project demonstrates how to build, train, and evaluate a simple neural network on the MNIST dataset using TensorFlow and Keras. It also showcases capturing images using a real webcam in Google Colab for further experimentation or custom data collection.

## Table of Contents

- [Project Overview](#project-overview)
- [Setup & Requirements](#setup--requirements)
- [Code Structure](#code-structure)
- [Using the Real Camera in Colab](#using-the-real-camera-in-colab)
- [Steps](#steps)
- [Libraries Used](#libraries-used)
- [Results & Visualization](#results--visualization)
- [Notes](#notes)

---

## Project Overview

- Load and preprocess the MNIST dataset.
- Build and train a neural network model using TensorFlow and Keras.
- Evaluate model performance using accuracy and a confusion matrix.
- Capture images using a real webcam directly in Google Colab notebook.

## Setup & Requirements

To run this notebook, you need:

- Google Colab (recommended for webcam capture)
- Python 3
- The following Python libraries:
  - tensorflow
  - keras
  - numpy
  - matplotlib
  - seaborn
  - IPython.display
  - google.colab (Colab only)

## Code Structure

1. **Data Loading & Exploration:**  Load MNIST data, visualize shapes, and preview samples.
2. **Preprocessing:** Normalize pixel data for better training results.
3. **Model Build & Train:** Create a simple neural network using Sequential API.
4. **Evaluation:** Accuracy calculation and confusion matrix visualization.
5. **Real Camera Capture:**
   - Uses Google Colab’s JS APIs to access webcam and take photos.
   - Images are saved and displayed in the notebook for further use.

## Using the Real Camera in Colab

A unique part of this notebook is using Google Colab's support for browser-side JavaScript to access your webcam. The captured image is saved as `photo.jpg` in the runtime’s working directory and can be used for custom prediction or dataset augmentation.

**Webcam Capture Process:**
- Notebook requests webcam permissions to capture an image.
- User clicks 'Capture' to take a photo.
- The photo is saved and displayed in the notebook.

Sample code for webcam capture:
```python
from IPython.display import display, Javascript
from google.colab.output import eval_js
from base64 import b64decode

def take_photo(filename='photo.jpg', quality=0.8):
    js = Javascript(''' ... (JavaScript code to access webcam) ... ''')
    display(js)
    data = eval_js('takePhoto({})'.format(quality))
    binary = b64decode(data.split(',')[1])
    with open(filename, 'wb') as f:
        f.write(binary)
    return filename
```

## Steps

1. **Import Libraries**
2. **Load MNIST Dataset**
3. **Explore Data Shapes**
4. **Normalize Data**
5. **Define Model Structure**
6. **Compile & Train Model**
7. **Evaluate on Test Data**
8. **Generate Predictions & Confusion Matrix**
9. **Visualize with Matplotlib & Seaborn**
10. **Capture Real Image from Webcam in Colab**

## Libraries Used

- `tensorflow` and `keras` : Building and training neural networks
- `numpy` : Array operations
- `matplotlib`, `seaborn` : Data visualization and confusion matrix
- `IPython.display`, `google.colab.output` : Displaying images and accessing webcam in Colab
- `base64` : Handling encoded images

## Results & Visualization

- The model achieves high accuracy (>97%) on MNIST.
- Confusion matrix is plotted to visualize class performance.
- Webcam photo capture is interactive and shown inline.


## Notes

- **Webcam access works only in Google Colab**. Local Jupyter Notebooks cannot directly access browser webcam.
- Captured images (`photo.jpg`) can be loaded and processed for prediction/augmentation in later cells.
- Experiment with your own digit images captured live!

---

**Repository:** [MNIST-Dataset-Using-Tensorflow_RealCamera](https://github.com/Vikash8294/MNIST-Dataset-Using-Tensorflow_RealCamera/)
