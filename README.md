PORTABLE COLORIMETRIC SYSTEM FOR RAPID MILK SPOILAGE DETECTION

🥛 1. Comprehensive Project Overview

The Portable Colorimetric System for Rapid Milk Spoilage Detection is an Edge AI-based embedded system developed to identify the freshness level of milk samples using optical sensing techniques. The system utilizes a TCS34725 RGB Color Sensor to measure the reflected light characteristics of milk and classify its quality in real time.

As milk undergoes spoilage, bacterial activity alters its optical density, opacity, and light reflectance properties. These variations are captured by the RGB sensor and processed by a microcontroller. The system then determines whether the milk is Fresh, Moderate, or Unsafe and displays the result on an OLED screen.

⚙️ 2. Architectural Structure

The system consists of three major modules:

Sensing Module

The TCS34725 RGB Color Sensor captures Red, Green, Blue, and Clear (RGB+C) light intensity values reflected from the milk sample.

 Processing Module

The Arduino/ESP32 microcontroller reads the sensor values, performs classification, and controls the display unit.

Display Module

The SSD1306 OLED display provides real-time visualization of milk freshness status.

 🔌 3. Hardware Requirements & Circuitry

 Microcontroller Board

Arduino Uno, Arduino Nano, or ESP32 can be used as the central processing unit for the system.

 TCS34725 RGB Color Sensor

The sensor contains an integrated white LED and an IR-blocking filter for accurate color measurement. It captures RGB and Clear light values from the milk sample.

 SSD1306 OLED Display

The OLED display is used to show classification results and sensor information.

 I2C Communication

Both the RGB sensor and OLED display communicate through the I2C protocol using shared SDA and SCL pins.

 🧠 4. Artificial Intelligence & Logic Walkthrough

 Part A: Machine Learning Training Phase

The machine learning model is created using TensorFlow and Keras.

 Data Collection

RGB values are collected from fresh, moderate, and spoiled milk samples and stored as a training dataset.

 Data Normalization

The collected RGB values are normalized by dividing each value by 255.0 before training.

 Neural Network Architecture

The model consists of:

* Input Layer – Accepts normalized RGB values.
* Hidden Layer 1 – 8 neurons with ReLU activation.
* Hidden Layer 2 – 6 neurons with ReLU activation.
* Output Layer – 3 neurons with Softmax activation.

The output classes are:

* Fresh
* Moderate
* Unsafe

 Model Deployment

The trained TensorFlow model is converted into TensorFlow Lite format and exported as a C header file (`model.h`) for embedded deployment.

 Part B: Embedded Classification Logic

The embedded firmware continuously reads RGB+C values from the TCS34725 sensor.

In the current implementation, milk classification is determined using the Clear (C) channel value.

 Classification Thresholds

* C > 2200 → Spoiled
* 1400 ≤ C ≤ 2200 → Fresh
* 1000 ≤ C < 1400 → Moderate
* C < 1000 → Normal/Light

These thresholds were obtained from experimentally collected milk samples.

 🔬 5. Working Principle

The built-in LED of the TCS34725 sensor illuminates the milk sample. The reflected light is measured by the sensor and converted into digital RGB+C values.

As milk spoils, changes in turbidity, opacity, and optical density affect the reflected light intensity. The microcontroller analyzes these values and determines the freshness category. The result is displayed instantly on the OLED screen.

 🚀 6. Future Enhancements

 TensorFlow Lite Integration

Activate the embedded TensorFlow Lite model for direct AI-based prediction instead of threshold-based classification.

 Dark Chamber Design

Use a light-proof enclosure to eliminate environmental lighting variations and improve measurement consistency.

 Large Dataset Training

Collect additional milk samples under various spoilage conditions to improve model accuracy and generalization.

 IoT Connectivity

Upgrade to ESP32 and integrate cloud platforms such as ThingSpeak, Blynk, or AWS IoT for remote monitoring and data logging.

 📌 7. Conclusion

The Portable Colorimetric System for Rapid Milk Spoilage Detection combines optical sensing, embedded systems, and Edge AI to provide a rapid and non-destructive method for milk freshness assessment. By analyzing RGB sensor data and applying intelligent classification techniques, the system offers a low-cost, portable, and real-time solution for milk quality monitoring.
