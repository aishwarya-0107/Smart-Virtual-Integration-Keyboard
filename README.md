# 💻 Virtual Keyboard & Hand Tracking System

## ⭐ Project Overview

This project is a key component of the **Smart Integration System**, focusing on the development of a fully functional, **computer vision-based Virtual Keyboard**. [cite_start]It utilizes a webcam and hand tracking to allow users to input text and commands through natural hand gestures, addressing the limitations of relying on physical keyboards[cite: 15].

[cite_start]The system provides an intuitive, hands-free, and accessible input method, making technology more inclusive and usable in diverse environments like kiosks, smart TVs, and mobile applications[cite: 17, 19].

---

## ✨ Features & Functionality

* [cite_start]**Multimodal Foundation:** This system forms the "touch" component, designed to seamlessly integrate with a complementary voice recognition module (as outlined in the full system architecture)[cite: 11, 24].
* [cite_start]**Hand Tracking and Gesture Input:** Uses a standard webcam and **OpenCV** to detect and track the user's hand in real-time[cite: 106].
* [cite_start]**Virtual QWERTY Layout:** Renders a QWERTY-style keyboard interface using the `cv2` library[cite: 111, 194].
* [cite_start]**"Hover" Detection:** A key is visually highlighted when the tip of the **right index finger (Landmark 8)** hovers over it, indicating a potential selection [cite: 167, 169-174].
* [cite_start]**"Click" Emulation:** A virtual click is registered when a secondary hand gesture (e.g., a specific finger combination on the left hand, as shown in the original source code logic) is detected, triggering the key press [cite: 175-183].
* [cite_start]**System Integration:** Leverages the `pynput` library (in `virtual_keyboard_main.py`) or `pyautogui` (in the full implementation) to simulate **actual key presses** on the operating system, allowing the user to type into any active text field[cite: 71, 184].
* [cite_start]**Real-Time Text Feedback:** Displays the accumulated input text in a dedicated text box on the screen [cite: 142-153].

---

## 🛠️ Technology Stack

The core of this system is built on **Python** for its extensive library support in computer vision and system control.

### **Key Python Libraries**

| Library | Purpose |
| :--- | :--- |
| **`cv2` (OpenCV)** | Handles video stream capture, image processing, and rendering the virtual keyboard interface. |
| **`cvzone.HandTrackingModule`** | [cite_start]Provides robust, pre-trained models for detecting and extracting 21 hand landmarks for gesture recognition[cite: 107]. |
| **`pynput.keyboard.Controller`** | Used in `virtual_keyboard_main.py` to control and simulate operating system keyboard presses. |
| **`numpy`** | Essential for array manipulation, image blending, and creating the keyboard overlay. |
| **`threading`** / **`speech_recognition`** | (Used in the full system, not just `virtual_keyboard_main.py`) [cite_start]For concurrent background voice input processing [cite: 58, 74-97]. |

---

## 🏗️ Technical Implementation Details

The core logic for the keyboard and hand tracking is contained within `virtual_keyboard_main.py`.

### **Input Processing and Hand Tracking**

* **Hand Detection:** `detector.findHands(img)` locates the hand and its landmarks.
* **Drawing Overlay:** The `drawAll` function uses `cv2.addWeighted` with an `alpha` value for transparency, creating a visible yet non-obstructive keyboard interface over the live video feed.
* **Click Logic:** The current cursor position is defined by the **index finger tip** (`lmlist[8]`). The click action itself is verified by checking the position of the **middle finger tip** (`lmlist[12]`) within the same key boundary, and a one-second `time.sleep(1)` is applied to debounce the button press.

### **System Architecture (Context)**

This component aligns with the overall system design:
1.  [cite_start]**Input Devices:** The webcam and hand tracking emulate the **Touch Sensor Screen** input[cite: 64].
2.  [cite_start]**Input Processing:** The hand-tracking logic acts as the **Touch Event Handler**[cite: 64].
3.  [cite_start]**Application Interface:** Text output is routed through the **UI Manager**[cite: 64].

---

## 🚀 Installation and Setup

### **1. Prerequisites**
* [cite_start]A computer with **Python 3.7 or above**[cite: 54].
* [cite_start]A functioning webcam (Video Capture 0 or 1)[cite: 103].
* [cite_start]Recommended hardware: 4GB RAM (8GB preferred) and an i5 processor or better[cite: 48, 49].

### **2. Setup Instructions**
1.  **Clone the repository:**
    ```bash
    git clone [Your Repository URL]
    cd [Your Repository Name]
    ```
2.  **Install Python dependencies:**
    ```bash
    pip install opencv-python numpy cvzone pynput
    # For the full system (with voice):
    # pip install SpeechRecognition PyAudio pyttsx3
    ```
3.  **Running the Virtual Keyboard Component**
    Execute the main Python script for the hand-tracking virtual keyboard:

    ```bash
    python virtual_keyboard_main.py
    ```

---

## 🖼️ Output Screenshots

| Virtual Keyboard (Clean) | Live Hand Tracking | Comprehensive System Interface (Example) |
| :---: | :---: | :---: |
| ![keyboard-dark.png](keyboard-dark.png) | ![live-keyboard.png](live-keyboard.png) | ![keyboard-image.png](keyboard-image.png) |

---

## ⏭️ Future Scope

Future plans for the integrated system include:
* [cite_start]Improving how touch and voice inputs work together for enhanced command interpretation[cite: 213].
* [cite_start]Adding features to increase accessibility for individuals with various impairments[cite: 28, 217].
* [cite_start]Supporting more device types like smartwatches and VR headsets[cite: 215].
* [cite_start]Optimizing for low-latency response and compatibility across platforms[cite: 30].

---

## 📄 Licensing

[Insert license information, e.g., MIT License]
