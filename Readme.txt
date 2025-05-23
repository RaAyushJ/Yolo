Embedded vs. Desktop Person Detection System

This repository contains the implementation of a dual-platform person detection system:

    An embedded system using ESP32-CAM with TensorFlow Lite

    A desktop system running YOLO for high-accuracy detection

The goal is to compare performance metrics such as inference time, accuracy, and energy consumption across these platforms.
Repository Structure

File/Folder	        	Description
esp32cam-gdrive/		Arduino sketch for ESP32-CAM that captures images, runs TFLite models, and uploads images to Google Drive
Base64/    			Contains base64.cpp and base64.h used for encoding/decoding images for HTTP transmission
person_detect_model_data/	Contains the quantized TensorFlow Lite model data for person detection (in .h format)
yoloarduino/			Arduino code for communicating with YOLO; possibly manages detection pipeline
esp32cam_person/		Main code or labels related to the ESP32-CAM person detection setup


Setup Instructions
Hardware Requirements

    ESP32-CAM Module (with OV2640 sensor)

    Computer or Laptop (for running YOLO)

    Micro USB cables

    Wi-Fi network for ESP32-CAM connectivity

Software Requirements
For ESP32-CAM (Embedded System)

    Arduino IDE or PlatformIO

    Required Libraries:

        esp_camera.h

        WiFi.h

        TensorFlow Lite for Microcontrollers

        Base64 encoding/decoding (Base64/base64.cpp, Base64/base64.h)

For Desktop System (YOLO via Python)

    Python 3.x

    Ultralytics YOLO

    OpenCV

    Google Drive API (optional for automation)

    Jupyter Notebook (optional)

Usage Instructions
1. Setting Up the Embedded System (ESP32-CAM)

    Open the Arduino IDE and load the sketch from esp32cam-gdrive/.

    Configure your Wi-Fi credentials in the code.

    Upload the code to the ESP32-CAM.

    Ensure person_detect_model_data/person_detect_model_data.h contains your TFLite model.

    Power the ESP32-CAM — it will:

        Capture images

        Run inference locally

        Upload results to Google Drive

2. Setting Up the Desktop System with YOLO

    Install required Python dependencies:

pip install ultralytics opencv-python

Download images from Google Drive (manually or via API).

Run the detection script:

    python detect_yolo.py

    The script processes images, draws bounding boxes, and displays accuracy results.

3. Image Transfer and Data Flow

    ESP32-CAM uploads Base64-encoded images to Google Drive.

    The desktop system fetches these images for high-accuracy detection using YOLO.

    Results are visualized and stored for analysis.

Notes and Customization

    Adjust detection thresholds, image resolutions, and model hyperparameters as needed.

    Train and replace the .h model file in person_detect_model_data/ for improved accuracy.

    Ensure synchronization of image sources for fair comparison between platforms.

License

This project is intended for research and educational purposes. Use it responsibly.
Acknowledgments

    TensorFlow Lite for Microcontrollers

    Ultralytics YOLO

    OpenCV