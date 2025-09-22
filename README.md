# Gesture_controlled_mobile_robotic_arm
Designed and built a 6DOF Rover and Robotic Arm powered by Jetson Nano. The Ardupilot platform was utilized to control the movements and actions of the mobile robotic arm. Trained a Gesture Recognition Model in Python through OpenCV, Tensorflow and mediapipe and integrating it into the Robotic Arm.

https://github.com/user-attachments/assets/5a50baf3-4e7f-45a8-a71a-663e1d412ac1

## Comprehensive Project Overview: Gesture-Controlled Mobile Robotic Arm

This document outlines the complete project for a mobile robotic arm controlled by hand gestures captured through a device camera. It integrates various components to achieve this functionality:

**1. Gesture Recognition System:**

* **Technology:** Leverages OpenCV, a computer vision library, and a pre-trained model from the `hand-gesture-recognition-using-mediapipe` repository.
* **Functionality:**
    * Captures hand movements from the camera feed.
    * Employs MediaPipe for hand landmark detection.
    * Classifies hand gestures based on detected keypoints using a Multi-Layer Perceptron (MLP) model.  
    * (Optional) Can be extended to incorporate more advanced machine learning models (e.g., CNNs) for potentially improved accuracy.
* **Model Training:**
    * The provided model is trained on hand keypoint data for various gestures (configurable).
    * Users can add or modify training data to recognize additional gestures.
    * Jupyter Notebooks guide users through the training process for both hand sign and finger gesture recognition.

**2. Command Routing based on Hand Laterality:**

* The application differentiates between right and left hand gestures to control separate functionalities:
    * **Right Hand Gestures:** Control the rover (mobile platform) through commands sent using DroneKit-Python.
    * **Left Hand Gestures:** Control the movements of the 6 DOF robotic arm using SMBus communication.

**3. Rover Control System:**

* **Rover Programming:**
    * Mission Planner, a software tool for drone flight planning, is used to **simulate** the rover's movements.
* **Command Interface:**
    * DroneKit-Python, a library for interfacing with drones and other autonomous vehicles, is used to send movement commands to the **simulated** rover based on recognized hand gestures.

**4. Robotic Arm Design and Control:**

* **Rover Design:**
    * The physical structure of the rover is designed to accommodate all necessary components, including the camera for gesture recognition and the connection to the Jetson Nano.
* **6 DOF Robotic Arm Construction:**
    * A 6-Degrees-of-Freedom (DOF) robotic arm is built to provide the necessary range of motion for various tasks.
* **Robotic Arm Programming:**
    * SMBus, a communication protocol for interfacing devices, is employed to program and control the servo motors of the robotic arm. This allows for precise movement of the arm at specific angles based on the interpreted hand gestures.

**5. Overall System Integration:**

1. The gesture recognition application running on the Jetson Nano captures hand movements through the camera.
2. The model analyzes the hand keypoints and classifies the gesture.
3. Based on hand laterality (right or left) and the recognized gesture, the system sends control commands:
    * Right hand gestures: Commands are sent via DroneKit-Python to control the **simulated** rover.
    * Left hand gestures: Commands are sent via SMBus to control the robotic arm movements.

**Additional Considerations:**

* The `hand-gesture-recognition-using-mediapipe` repository offers finger gesture recognition as well.
* The project can be further enhanced by exploring alternative machine learning models like CNNs for potentially better gesture recognition accuracy, especially for complex gestures.

This comprehensive overview provides a detailed explanation of each component's functionality and how they work together to achieve the project's objective: a mobile robotic arm controlled by intuitive hand gestures. 

**Requirements**
To run the program, you need the following dependencies:
● mediapipe 0.8.1
● OpenCV 3.4.2 or later
● Tensorflow 2.3.0 or later
● tf-nightly 2.5.0.dev or later (required only for creating a TFLite model with
LSTM)
● scikit-learn 0.23.2 or later (optional, for displaying the confusion matrix)
● matplotlib 3.3.2 or later (optional, for displaying the confusion matrix)


## Run the Gesture-Controlled Rover Demo!
Ready to take control of your rover with your hand gestures?  Here's how to run the demo using your webcam:

**1. Open your terminal:**
Locate your terminal application and launch it. 

**2. Navigate to the project directory:**
Use the `cd` command to navigate to the directory where the project files are stored. For example, if your files are in a folder named example "gesture_control_rover" on your desktop, you would type:

**3. Run the demo:**
Execute the following command to start the demo:
python Gesture_app.py

**4. Control the Rover with Hand Gestures:**
A window will appear showing your webcam feed with a boundary box around your hand. Position your hand within the box to control the rover's movements:

* **Move Upward:** Makes the rover move forward.
* **Move Downward:** Makes the rover move backward.
* **Move Left:** Makes the rover turn left.
* **Move Right:** Makes the rover turn right.

**5. Customize the Demo (Optional):**
The demo offers several options for customization. You can use the following flags with the `python app.py` command:

* `--device`: Specify the camera device number (default: 0)
* `--width`: Set the width of the camera capture (default: 960)
* `--height`: Set the height of the camera capture (default: 540)
* `--use_static_image_mode`: Enable static image mode for MediaPipe inference (default: off)
* `--min_detection_confidence`: Adjust the minimum detection confidence threshold (default: 0.5)
* `--min_tracking_confidence`: Adjust the minimum tracking confidence threshold (default: 0.5)

**Example with Customization:**
```
python app.py --width=640 --height=480 --min_detection_confidence=0.7
```

This example sets the camera capture resolution to 640x480 and increases the minimum detection confidence for a more robust gesture recognition.

**Have fun controlling your rover with the power of hand gestures!**
