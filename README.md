# Vechile-Detection

cv2 (OpenCV): Used for handling video streams and image processing.
YOLO (from ultralytics): Loads the YOLOv8 deep learning model for object detection.

Loads the YOLOv8n (nano version) pre-trained model (yolov8n.pt).
This model can detect multiple objects like cars, trucks, people, etc.

cv2.VideoCapture(0): Opens the webcam (change to a file name like 'video.mp4' to use a recorded video).

cap.isOpened(): Runs the loop as long as the camera is open.
cap.read(): Reads a new frame from the video.
if not ret: break: Stops if no frame is available

Passes the frame (image) to the YOLO model for object detection.
Initializes vehicle_detected = False (assumes no vehicle is present initially).

Loops through detected objects (results).
Extracts bounding box coordinates (x1, y1, x2, y2) for each detected object.
Gets object label (e.g., "car", "truck", etc.).
Checks if the object is a vehicle (car, truck, bus, motorcycle).
If a vehicle is detected, sets vehicle_detected = True and exits the loop

Copies the current frame to apply an overlay.
If no vehicle is detected, sets:
color = (0, 255, 0) (green for "SAFE").
text = "SAFE".
If a vehicle is detected, sets:
color = (0, 0, 255) (red for "STOP!").
text = "STOP!".

Draws a full-screen rectangle (overlay) with the chosen color.
Uses transparency (alpha = 0.4) to blend the overlay with the frame.
cv2.addWeighted() merges the original frame and the colored overlay smoothly.

Adds "STOP!" (red overlay) or "SAFE" (green overlay) text to the frame.
cv2.FONT_HERSHEY_SIMPLEX is used for text style.
(100, 100): Sets text position.
(255, 255, 255): White text color.
5: Text thickness.

Releases the webcam (cap.release()).
Closes all OpenCV windows (cv2.destroyAllWindows()).
