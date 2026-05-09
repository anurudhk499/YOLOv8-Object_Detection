# 🎯 YOLOv8 Object Detection

Real-time object detection using [YOLOv8](https://github.com/ultralytics/ultralytics) — supports both static images and live webcam feed.

---

## 📌 Features

- Detect objects in a static image using YOLOv8n (nano model)
- Real-time object detection via webcam
- Auto-downloads the pre-trained model on first run
- Bounding box annotations rendered directly on frame/image

---

## 🛠️ Requirements

- Python 3.8+
- A webcam (for live detection)

Install dependencies:

```bash
pip install ultralytics opencv-python
```

---

## 🚀 Usage

### 1. Image Detection

Place your image in the project directory and name it `image.jpg`, then run the first notebook cell.

```python
from ultralytics import YOLO
import cv2

model = YOLO("yolov8n.pt")       # Auto-downloads on first run
img = cv2.imread("image.jpg")
results = model(img)

output = results[0].plot()
cv2.imshow("Detection", output)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

**Sample output:**
```
0: 640x480 1 cat, 1 dog, 96.3ms
Speed: 54.3ms preprocess, 96.3ms inference, 2.0ms postprocess
```

### 2. Live Webcam Detection

Run the second notebook cell to start live detection. Press `q` to quit.

```python
cap = cv2.VideoCapture(0)

while True:
    ret, frame = cap.read()
    results = model(frame)
    output = results[0].plot()

    cv2.imshow("Detection", output)
    if cv2.waitKey(1) == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```

---

## 📁 Project Structure

```
📦 yolo-object-detection
 ┣ 📓 YOLO.ipynb         # Main notebook
 ┣ 🖼️ image.jpg          # Input image (add your own)
 ┗ 📄 README.md
```

> The `yolov8n.pt` model file is downloaded automatically by Ultralytics on first run.

---

## 🤖 Model Info

| Model     | Size  | mAP  | Speed (CPU) |
|-----------|-------|------|-------------|
| YOLOv8n   | 3.2M  | 37.3 | ~96ms/img   |

Using **YOLOv8 Nano** — the fastest and lightest variant, great for real-time use on standard hardware. Can detect **80 COCO classes** including people, vehicles, animals, and everyday objects.

---

## 📚 References

- [Ultralytics YOLOv8 Docs](https://docs.ultralytics.com/)
- [COCO Dataset Classes](https://cocodataset.org/)

---

## 👤 Author

**Anurudh** — B.Tech AI & ML, Srinivas University  
[GitHub Profile](https://github.com/)
