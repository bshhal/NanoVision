# Nanoparticles Optimization Using AI for Therapy and Biosensor

## Research Project

This project is part of a research project conducted under the supervision of a professor at Kennesaw State University.

The research focuses on using **artificial intelligence to help optimize nanoparticles for biomedical applications**, with an emphasis on their use in **therapy and biosensing**.

The overall idea is to combine nanotechnology, experimental work, and AI-based analysis to better understand and optimize how nanoparticles can be used for biomedical applications.

### Research Paper

The research is based on and related to the work published in *Biosensors*:

[Research Paper – MDPI Biosensors](https://www.mdpi.com/2079-6374/15/1/19)

---

## What I Am Working On

My part of the research focuses on the **computer vision and machine learning side** of the project.

The goal is to use images from the experimental process and develop a computer-vision system that can automatically identify and analyze relevant features instead of relying entirely on manual inspection.

For this, I am using **Ultralytics YOLO** to train an object-detection model.

In simple terms, the model is being trained to look at an image, find the part of the image that matters, and identify its location.

This provides a starting point for automatically analyzing experimental results and extracting useful information from the images.

---

## What the Code Does

The code in this repository is mainly responsible for preparing the image data, training the YOLO model, and running the trained model on new images.

The workflow is roughly:

**Images → Annotation → Dataset → YOLO Training → Detection → Analysis**

### 1. Image Dataset

The project contains images collected for the research.

These images are separated into the appropriate dataset folders so they can be used for training and testing the model.

### 2. Image Annotation

Before YOLO can learn what to detect, the relevant areas in the images need to be identified.

The images are annotated using **Roboflow**.

The annotations tell the model:

> "This is the region you should learn to recognize."

These annotations are then converted into a format that YOLO can use.

### 3. YOLO Dataset Configuration

The `data.yaml` file tells YOLO where the dataset is located and what classes the model should learn.

For example, the dataset configuration contains information about:

- Training images
- Validation images
- Number of classes
- Class names

### 4. Model Training

The project uses **Ultralytics YOLO** for object detection.

A lightweight YOLO model such as `YOLO26n` is used as the starting model.

The training process looks at the annotated images and gradually learns the visual patterns associated with the regions we want to detect.

A typical training command is:

```bash
yolo train data=yolo_lfa/data.yaml model=yolo26n.pt epochs=5
