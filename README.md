# 🐘 Lord Ganesh Python Color Sketch Drawing

A Python-based project that converts a Lord Ganesh image into an animated **color contour sketch** using **OpenCV, NumPy, and Turtle Graphics**.

The program processes the input image, detects its edges and contours using OpenCV, and then uses Turtle Graphics to draw those contours on the screen with the **original colors of the image**.

---

## ✨ Features

* 🐘 **Lord Ganesh Sketch** – Converts a Ganesh image into a digital Turtle sketch.
* 🎨 **Original Image Colors** – The sketch uses the original colors detected from the image.
* 🖼️ **Custom Image Support** – Any PNG or JPG image can be used.
* 🔍 **Edge Detection** – Uses OpenCV Canny Edge Detection to detect image edges.
* 🌀 **Contour Detection** – Extracts contours from the processed image.
* ⚡ **Animated Drawing** – The sketch is drawn step-by-step using Turtle Graphics.
* 🖥️ **80% Screen Window** – The Turtle window is automatically set to 80% of the screen.
* 📐 **Automatic Image Scaling** – The image is resized according to the available window size.
* 🖤 **Black Background** – The sketch is displayed on a black background.

---

## 🛠️ Technologies Used

* **Python 3**
* **OpenCV**
* **NumPy**
* **Turtle Graphics**

---

## 📋 Requirements

Make sure Python 3.x is installed on your computer.

Install the required libraries using:

```bash
pip install opencv-python numpy
```

### Turtle

`Turtle` is included with the standard Python installation on Windows.

---

## 🚀 How to Run

### 1. Download or clone the project

Download the project files and open the project folder in VS Code or another Python editor.

### 2. Add the image

Place your Ganesh image in the same folder as the Python file.

The current code uses:

```python
image_path = 'ganesh_2.png'
```

So the project folder should contain:

```text
ganesh_2.png
```

### 3. Run the Python program

```bash
python ganesh.py
```

The Turtle window will open and the Ganesh sketch will start drawing automatically.

---

## 🔄 How the Program Works

The project follows these steps:

### Step 1 — Load Image

OpenCV loads the input image:

```python
img = cv2.imread(image_path)
```

If the image is not found, an error message is displayed.

---

### Step 2 — Create Turtle Window

A Turtle screen is created with a black background:

```python
screen = turtle.Screen()
screen.setup(width=0.8, height=0.8)
screen.bgcolor("black")
```

The window covers approximately 80% of the screen.

---

### Step 3 — Resize Image

The image is automatically resized according to the Turtle window:

```python
img = cv2.resize(img, (width, height))
```

This helps the drawing fit properly inside the window.

---

### Step 4 — Convert Image to Grayscale

The image is converted from BGR to grayscale:

```python
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
```

Grayscale makes edge detection easier.

---

### Step 5 — Apply Gaussian Blur

Gaussian Blur is applied to reduce unnecessary noise:

```python
blur = cv2.GaussianBlur(gray, (5, 5), 0)
```

---

### Step 6 — Detect Edges

Canny Edge Detection is used to detect the important edges of the image:

```python
edges = cv2.Canny(blur, 60, 150)
```

---

### Step 7 — Find Contours

OpenCV finds contours from the detected edges:

```python
contours, _ = cv2.findContours(
    edges,
    cv2.RETR_LIST,
    cv2.CHAIN_APPROX_NONE
)
```

These contours are then used by Turtle for drawing.

---

### Step 8 — Apply Original Colors

For every contour, the program gets the color from the original image:

```python
b, g, r = img[first_pt[1], first_pt[0]]
```

Because OpenCV stores colors in **BGR format**, the values are converted to RGB before sending them to Turtle:

```python
t.pencolor(int(r), int(g), int(b))
```

Therefore, the sketch uses the **original colors from the image**.

---

### Step 9 — Draw Using Turtle

The detected contour points are converted into Turtle coordinates:

```python
t.goto(x, y)
```

Turtle then follows the contour points and creates the sketch.

---

## 🎨 Color Customization

The current code uses the original image colors:

```python
t.pencolor(int(r), int(g), int(b))
```

### Golden Color

If you want to draw the sketch in **golden color**, replace the original color line with:

```python
t.pencolor(255, 215, 0)
```

So this:

```python
b, g, r = img[first_pt[1], first_pt[0]]
t.pencolor(int(r), int(g), int(b))
```

can become:

```python
t.pencolor(255, 215, 0)
```

---

## ⚡ Animation Speed

The drawing speed is controlled using:

```python
screen.tracer(15, 0)
```

You can change the value depending on the required animation speed.

For example:

```python
screen.tracer(5, 0)
```

or:

```python
screen.tracer(30, 0)
```

---

## 🖼️ Use Another Image

To use another image, change:

```python
image_path = 'ganesh_2.png'
```

For example:

```python
image_path = 'my_photo.jpg'
```

Make sure the image is placed in the same project folder.

---

## 📁 Project Structure

```text
Ganesh-Color-Sketch/
│
├── ganesh.py
├── ganesh_2.png
└── README.md
```

---

## 🎯 Project Purpose

This project demonstrates how **Python, OpenCV, NumPy, and Turtle Graphics** can work together to create an animated digital artwork.

It is useful for learning:

* Image Processing
* Edge Detection
* Contour Detection
* RGB/BGR Color Conversion
* Coordinate Transformation
* Turtle Graphics
* Python Programming

---

## 👩‍💻 Author

**Mansi Goswami**

BCA Graduate | Python Backend Developer | Django Developer
