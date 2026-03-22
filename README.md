# ANNOTATION-https://app.roboflow.com/object-detection-kgtuv/craters-boulders-detection-gvnd3/generate/preprocessing
https://colab.research.google.com/drive/1Jy0X9izLvTHhGwHCm6xjmQBETnrOQLQE#scrollTo=Q_hSVfo-Q_p5
https://colab.research.google.com/drive/1Jy0X9izLvTHhGwHCm6xjmQBETnrOQLQE#scrollTo=qQTrXschgfYp
https://drive.google.com/drive/recent
https://colab.research.google.com/drive/1BiFgqewKJg3k1s2PNdXHBTe1CimLF4Hg#scrollTo=s2ZlPxsjb6uk
Introduction

Crater and boulder detection is a critical task in planetary science, enabling terrain analysis, landing site selection, and geological interpretation of celestial bodies such as the Moon and Mars. Traditional image processing techniques struggle due to noise, illumination variations, and complex surface textures.

This project explores the application of deep learning-based object detection techniques to accurately identify craters and boulders from satellite imagery.

Given a planetary surface image:

Detect craters and boulders
Localize them using bounding boxes
Classify them into respective categories

Challenges include:

Low contrast images
Irregular shapes
Varying sizes (small to large craters)
Shadow and lighting inconsistencies


Data Acquisition

Datasets used:

NASA lunar datasets (LROC)
Mars datasets (HiRISE)
Annotated datasets using LabelImg / Roboflow

Each image contains labeled bounding boxes for:

Craters
Boulders  


3.2 Preprocessing

Image preprocessing steps include:

Resizing images to fixed input size (e.g., 320×320 / 416×416)
Normalization (pixel values scaled between 0–1)
Color space correction (BGR → RGB using OpenCV)
Data augmentation:
Rotation
Flipping
Scaling

These steps improve model generalization and robustness.  

3.3 Model Architecture

This project utilizes:

YOLOv3-tiny (OpenCV DNN implementation)
Optionally extendable to YOLOv8
Key Components:
Backbone Network (Feature Extraction)
Extracts spatial features such as edges, textures, and shapes.
Detection Head
Predicts:
Bounding box coordinates (x, y, width, height)
Object confidence score
Class probabilities  



Input Image
   ↓
Preprocessing (Resize, Normalize)
   ↓
Blob Conversion (OpenCV DNN)
   ↓
Forward Pass (YOLO)
   ↓
Feature Maps
   ↓
Bounding Box Prediction
   ↓
Non-Max Suppression (NMS)
   ↓
Final Detection Output  


OpenCV DNN Integration

The model is implemented using OpenCV DNN, which enables:

Loading pre-trained YOLO weights (.weights)
Parsing network architecture (.cfg)
Running inference without external frameworks

Key functions used:

cv2.dnn.readNetFromDarknet() → Load model
cv2.dnn.blobFromImage() → Preprocess input
net.forward() → Perform inference  

Results & Observations
 Strengths
Efficient real-time detection using YOLOv3-tiny
Good performance on medium and large craters
Fast inference suitable for deployment
 Limitations
Difficulty detecting very small craters
False positives in shadow regions
Reduced accuracy in highly noisy terra  

Future Enhancements
Upgrade to YOLOv8 for better accuracy
Use hyperspectral data for material-based detection
Implement attention mechanisms for small object detection
Apply segmentation models (Mask R-CNN) for precise shape detection
7. Key Learnings
Deep learning significantly outperforms traditional methods in complex terrain analysis
Preprocessing plays a crucial role in improving detection performance
Model selection (speed vs accuracy trade-off) is critical for real-world applications  


This project demonstrates the effectiveness of deep learning-based object detection for planetary surface analysis. Using YOLO architecture, the system successfully identifies craters and boulders with high efficiency.

The approach can be extended to:

Autonomous rover navigation
Space mission planning
Geological mapping  

Crater & Boulder Detection using YOLO

This project implements an object detection pipeline using YOLO to identify craters and boulders from planetary surface images. The system leverages OpenCV’s DNN module for efficient inference and demonstrates real-time detection capabilities.  



