# EdgeInferInator

This project demonstrates the use of TinyML for anomaly detection and pattern classification on an ESP32 microcontroller. The goal is to enable autonomous, edge-based inference on ESP32, reducing reliance on centralized systems like Home Assistant. This setup integrates seamlessly with Home Assistant for home automation and MongoDB Atlas for cloud data backup, while utilizing Edge Impulse, TensorFlow Lite Micro, MQTT, REST APIs, and Cloudflare's Argo Tunnel.

## Table of Contents
- [Project Overview](#project-overview)
- [TinyML - An Introduction](#tinyml---an-introduction)
- [Why This Project?](#why-this-project)
- [Tech Stack and Frameworks](#tech-stack-and-frameworks)
- [Installation and Setup](#installation-and-setup)
- [Usage](#usage)
- [Future Work and Improvements](#future-work-and-improvements)

## Project Overview
The primary objective of this project is to perform real-time anomaly detection and pattern classification directly on the ESP32, allowing it to operate autonomously from Home Assistant. Data is collected, preprocessed, and trained using Edge Impulse, then deployed to the ESP32 as a TensorFlow Lite Micro (TFLite Micro) model. The ESP32 communicates detected anomalies or classifications to Home Assistant using MQTT, and backs up data to MongoDB Atlas via a REST API.

## TinyML - An Introduction
**TinyML** is the application of machine learning (ML) on small, low-power devices such as microcontrollers (MCUs). By enabling these devices to make intelligent decisions independently, TinyML makes applications like predictive maintenance, anomaly detection, and health monitoring more efficient. TinyML brings several advantages:
- **Decentralization**: Reduces dependency on central servers.
- **Low Latency**: Enables faster responses as processing happens locally.
- **Reduced Bandwidth**: Minimizes data transfer by performing inference on-device.

## Why This Project?
Home Assistant (HA) is a powerful tool for home automation, typically relying on a centralized approach where devices report data to HA, which then performs any necessary processing or inference. However, this setup makes HA a single point of dependency. By moving the inference to the ESP32, this project aims to decentralize the automation system, making it more robust, autonomous, and less reliant on a centralized controller.

## Tech Stack and Frameworks
The project leverages a combination of machine learning, networking, and IoT technologies:

1. **Edge Impulse**  
   - Used for data collection, preprocessing, training, and conversion to a TFLite Micro model.
   - Provides an easy-to-use interface for building ML models for edge devices.

2. **TensorFlow Lite Micro**  
   - Deployed on the ESP32 for real-time inference.
   - Lightweight, optimized library designed to run ML models on embedded systems.

3. **ESP32 Microcontroller**  
   - Performs on-device inference and communicates with other components in the system.
   - Acts as the main compute unit for executing the ML model.

4. **MQTT Protocol**  
   - Used to send data from ESP32 to Home Assistant.
   - Lightweight messaging protocol that ensures efficient communication.

5. **REST API**  
   - Logs data from ESP32 to MongoDB Atlas for cloud storage and backup.
   - Provides a reliable way to store historical data and facilitate remote access.

6. **MongoDB Atlas**  
   - Cloud-based NoSQL database that stores historical data.
   - Allows secure, scalable storage and retrieval of classified data and anomalies.

7. **Cloudflare Argo Tunnel**  
   - Exposes Home Assistant instance securely to the cloud.
   - Paired with a domain from GoDaddy, enabling secure remote access to Home Assistant.

## Installation and Setup
To get this project up and running, follow these steps:

1. **Collect and Train Data**:
   - Use Edge Impulse to collect and preprocess data for training.
   - Train the model and export it as a TensorFlow Lite Micro (.tflite) model.

2. **Deploy Model on ESP32**:
   - Use Arduino IDE or PlatformIO to load the model onto the ESP32.
   - Include TensorFlow Lite Micro libraries to run the model.

3. **Set Up MQTT for Home Assistant**:
   - Configure the MQTT broker within Home Assistant.
   - Program the ESP32 to send classified data to Home Assistant over MQTT.

4. **Configure REST API for MongoDB Atlas**:
   - Set up a MongoDB Atlas account and create a collection to store data.
   - Write an HTTP POST function on the ESP32 to log data to MongoDB.

5. **Expose Home Assistant to the Cloud**:
   - Use Cloudflare's Argo Tunnel to create a secure, accessible endpoint for Home Assistant.
   - Configure the domain obtained from GoDaddy for remote access.

## Usage
1. Power up the ESP32 to initiate pattern classification and anomaly detection.
2. ESP32 sends classification notifications to Home Assistant via MQTT for real-time monitoring.
3. ESP32 logs classified patterns and anomalies to MongoDB Atlas, ensuring historical data is accessible for further analysis.
4. Monitor and manage the setup remotely through Home Assistant, using the Cloudflare tunnel.

## Future Work and Improvements
- **Expand Model Capabilities**: Enhance the model to recognize more complex patterns.
- **Data Analysis**: Implement a dashboard for managing all the process under one roof.
- **Optimization**: Optimize model and MQTT configurations for minimal latency and improved power efficiency and reducing size.

## Conclusion
This project exemplifies the power of TinyML in creating autonomous, decentralized, and resilient IoT systems. By leveraging Edge Impulse, TensorFlow Lite Micro, MQTT, and REST APIs, we enable the ESP32 to not only make intelligent decisions but also to integrate seamlessly with centralized platforms like Home Assistant and MongoDB Atlas for broader data management and automation.

---
Final notes: the code provided have all the api keys and other credentials in it, feel free to use this until i destroy the instances.
