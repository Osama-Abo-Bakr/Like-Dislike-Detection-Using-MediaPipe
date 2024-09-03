# Like & Dislike Detection Using MediaPipe

## Overview
The Like & Dislike Detection project is a real-time hand gesture recognition system that detects "Like" and "Dislike" gestures using MediaPipe and OpenCV. When a gesture is recognized, the system displays a corresponding image (thumbs up for Like, thumbs down for Dislike) over the video feed. This project showcases the power of computer vision in creating interactive and intuitive systems.

## Features
- **Real-Time Detection:** The system uses a webcam to capture and process video frames in real-time.
- **Gesture Recognition:** Identifies "Like" and "Dislike" gestures based on the position of fingers and the thumb.
- **Visual Feedback:** Displays a thumbs-up or thumbs-down image when the respective gesture is detected.

## Dependencies
To run this project, you will need the following libraries:
- OpenCV
- MediaPipe
- NumPy

You can install these dependencies using pip:
```bash
pip install opencv-python mediapipe numpy
```

## How It Works
1. **Hand Landmark Detection:** The project utilizes MediaPipe’s Hand solution to detect hand landmarks in each frame.
2. **Gesture Logic:** By analyzing the relative positions of finger tips and the thumb, the system determines whether the gesture is a "Like" or "Dislike."
3. **Display Results:** Based on the detected gesture, the system overlays the corresponding image (like or dislike) on the video feed.

## Code Explanation

### Image Processing
The project first loads the "Like" and "Dislike" images and resizes them for display.
```python
like_image = cv2.imread('like.png')
like_image = cv2.resize(like_image, (200, 180))

dislike_image = cv2.imread('dislike.png')
dislike_image = cv2.resize(dislike_image, (200, 180))
```

### Hand Detection
Using MediaPipe, the project initializes the hand detection model and processes the webcam feed.
```python
mp_hand = mp.solutions.hands
hands = mp_hand.Hands()
draw_utils = mp.solutions.drawing_utils
```

### Gesture Detection
The system checks the position of the fingers to determine if the hand is showing a "Like" or "Dislike" gesture.
```python
if lm_list[thump_tip].y < lm_list[thump_tip-1].y < lm_list[thump_tip-2].y:
    cv2.putText(image, 'LIKE', ...)
    image[35:35+h, 30:30+w] = like_image
```
If the thumb is positioned above the index finger, the "Like" gesture is detected. If it is below, the "Dislike" gesture is detected.


## Future Enhancements
- **Multi-Hand Detection:** Extend the system to handle multiple hands in the frame.
- **Gesture Customization:** Add more gestures and corresponding actions.
- **Performance Optimization:** Improve the processing speed for smoother real-time detection.

## Conclusion
This project demonstrates the potential of gesture recognition systems in creating more natural and interactive human-computer interactions. It serves as a foundational step toward more complex applications such as sign language recognition, gaming controls, and interactive displays.
