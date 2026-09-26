# 🎨 CanvasCraft — Interactive Drawing Board

### A Browser-Based Digital Drawing Application Powered by HTML5 Canvas

**CanvasCraft** is a lightweight, interactive drawing board built using **HTML5 Canvas, CSS3, and Vanilla JavaScript**.

It allows users to draw freely on a digital canvas, change brush colors and sizes, erase content, draw rectangles, clear the canvas, and download their artwork as a PNG image.

The project demonstrates practical usage of the **Canvas API, mouse events, DOM manipulation, event-driven programming, and client-side image export**.

---

## 🌐 Live Demo

🚀 **[Open CanvasCraft](https://gfg-project-8.vercel.app/)**

---

# ✨ Features

## 🖊️ Freehand Drawing

Draw freely on the canvas using the mouse.

The application tracks:

* Mouse press
* Mouse movement
* Mouse release

to create smooth continuous strokes.

---

## 🎨 Color Picker

Choose any drawing color using the built-in HTML color picker.

```text
Color: 🎨 #000000
```

The selected color is automatically applied to subsequent pen strokes.

---

## 📏 Adjustable Brush Size

Control the thickness of the drawing brush using a range slider.

```text
Brush Size

1px ───────────────●────────────── 20px
```

The brush width is dynamically updated according to the selected value.

---

## 🧽 Eraser Tool

Switch from drawing mode to eraser mode to remove existing strokes.

The eraser works by drawing using the canvas background color.

---

## ▭ Rectangle / Square Tool

CanvasCraft allows users to create rectangular shapes by:

1. Selecting the **Square** tool.
2. Clicking and holding on the canvas.
3. Moving the mouse.
4. Releasing the mouse.

The application calculates the starting and ending coordinates and draws the rectangle dynamically.

---

## 🧹 Clear Canvas

The **Clean** button removes everything from the canvas.

```javascript
ctx.clearRect(0, 0, canvas.width, canvas.height);
```

This provides a quick way to start a new drawing.

---

## ⬇️ Download Drawing

Users can save their artwork as a PNG image directly from the browser.

The application converts the canvas into an image using:

```javascript
canvas.toDataURL("image/png");
```

and automatically downloads the generated image.

---

# 🧠 How It Works

CanvasCraft uses the HTML5 Canvas API as the main drawing surface.

```text
                    USER
                      │
                      ▼
             ┌─────────────────┐
             │  Select a Tool  │
             └────────┬────────┘
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
        Pen         Eraser      Square
          │           │           │
          └───────────┼───────────┘
                      ▼
             ┌─────────────────┐
             │ HTML5 CANVAS    │
             │ 2D Rendering    │
             └────────┬────────┘
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
      Clear Canvas           Download PNG
```

---

# 🛠️ Tech Stack

| Technology           | Purpose                      |
| -------------------- | ---------------------------- |
| **HTML5**            | Application structure        |
| **CSS3**             | User interface and styling   |
| **JavaScript ES6+**  | Application logic            |
| **HTML5 Canvas API** | Drawing and rendering        |
| **DOM API**          | Element and event management |
| **Mouse Events**     | Drawing interactions         |
| **Vercel**           | Deployment                   |

---

# 🏗️ Project Architecture

CanvasCraft follows a simple client-side architecture:

```text
┌──────────────────────────────┐
│          HTML5 UI            │
│                              │
│ Color | Brush | Tools        │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       JavaScript Logic       │
│                              │
│ Event Handling               │
│ Tool State                   │
│ Drawing Logic                │
│ Canvas Operations            │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       Canvas 2D Context      │
│                              │
│ Lines / Rectangles / Erasing │
└──────────────────────────────┘
```

---

# 📂 Project Structure

```text
CanvasCraft/
│
├── index.html       # Application structure
├── style.css        # Styling and UI
├── app.js           # Drawing and interaction logic
└── README.md        # Project documentation
```

The current repository contains the core HTML, CSS, and JavaScript implementation for the drawing application.

---

# ⚙️ Core Implementation

## 1. Canvas Initialization

The application obtains the 2D rendering context:

```javascript
const ctx = canvas.getContext("2d");
```

and initializes the canvas dimensions:

```javascript
canvas.height = 420;
canvas.width = 800;
```

The drawing configuration includes:

```javascript
ctx.strokeStyle = colorPicker.value;
ctx.lineWidth = brushSizeSelector.value;
ctx.lineCap = "round";
```

This creates rounded, smoother line endings.

---

## 2. Freehand Drawing

The drawing process is divided into three stages:

```text
mousedown
    ↓
mousemove
    ↓
mouseup
```

### Start Drawing

When the mouse button is pressed, the application starts a new path:

```javascript
ctx.beginPath();
ctx.moveTo(e.offsetX, e.offsetY);
```

### Draw

While the mouse moves, the application continuously creates line segments:

```javascript
ctx.lineTo(e.offsetX, e.offsetY);
ctx.stroke();
```

### Stop Drawing

When the mouse button is released, drawing mode is disabled.

This event-driven approach creates the freehand drawing experience.

---

# 🧩 Tool State Management

CanvasCraft maintains internal state variables to determine the active drawing mode:

```javascript
let isDrawing = false;
let currentTool = "pen";
let isDrawingSquare = false;
```

These variables determine whether the application should:

* Draw freehand
* Erase
* Draw a rectangle

This is a simple example of **state management using JavaScript variables**.

---

# 🖊️ Pen Tool

When the Pen tool is selected:

```javascript
currentTool = "pen";
```

the selected color from the color picker is used for drawing.

The Pen button is also visually marked as active through CSS classes.

---

# 🧽 Eraser Tool

The Eraser changes the current tool:

```javascript
currentTool = "eraser";
```

During drawing, the application uses the canvas background color instead of the selected drawing color:

```javascript
ctx.strokeStyle =
    currentTool == "eraser"
    ? "#ffffff"
    : colorPicker.value;
```

This produces the erasing effect.

---

# ▭ Rectangle Drawing

The rectangle tool stores the initial mouse coordinates:

```javascript
startX = e.offsetX;
startY = e.offsetY;
```

When the mouse is released, the ending coordinates are calculated:

```javascript
let width = endX - startX;
let height = endY - startY;
```

The rectangle is then rendered using:

```javascript
ctx.rect(startX, startY, width, height);
ctx.stroke();
```

---

# 📥 Download System

CanvasCraft provides client-side image export.

The canvas is converted into a PNG data URL:

```javascript
let canvasImage = canvas.toDataURL("image/png");
```

A temporary `<a>` element is then created to trigger the download.

The exported file is named:

```text
WhiteBoard.png
```

---

# 🚀 Getting Started

## Prerequisites

No backend, database, or package manager is required.

You only need:

* A modern web browser
* Git
* VS Code or another code editor

---

## 1. Clone the Repository

```bash
git clone https://github.com/SumitHelge-star/GFG-PROJECT-8.git
```

---

## 2. Navigate to the Project

```bash
cd GFG-PROJECT-8
```

---

## 3. Run the Application

Because CanvasCraft is a static frontend application, you can open:

```text
index.html
```

directly in your browser.

For development, **VS Code Live Server** is recommended.

---

# 🎯 Learning Outcomes

This project demonstrates several important frontend development concepts.

### HTML

* Semantic structure
* Form controls
* Buttons
* Canvas element

### CSS

* Layout design
* Tool styling
* Active-state styling
* Responsive UI concepts

### JavaScript

* DOM manipulation
* Event listeners
* State management
* Mouse events
* Conditional logic
* Dynamic Canvas rendering
* Client-side file generation

### Canvas API

* `getContext()`
* `beginPath()`
* `moveTo()`
* `lineTo()`
* `stroke()`
* `rect()`
* `clearRect()`
* `toDataURL()`

---

# 🔮 Future Improvements

The current application can be extended into a more complete browser-based drawing editor.

### 🎨 Drawing Features

* Circle and triangle tools
* Filled shapes
* Line tool
* Arrow tool
* Text tool
* Custom brush styles
* Opacity control

### ↩️ Editing Features

* Undo / Redo
* Clear confirmation
* Select and move objects
* Resize shapes
* Copy / paste
* Drawing history

### 📱 User Experience

* Touch-screen support
* Mobile responsive canvas
* Keyboard shortcuts
* Dark/light mode
* Improved toolbar
* Color palette presets

### 💾 Export

* JPG export
* WebP export
* Custom filename
* Export quality selection
* Canvas size customization

---

# 🌟 Project Highlights

```text
🎨 Interactive Drawing Board
🖊️ Freehand Pen
🧽 Eraser
▭ Rectangle Tool
🎨 Custom Color Picker
📏 Adjustable Brush Size
🧹 Clear Canvas
⬇️ PNG Download
⚡ Client-Side Processing
🖥️ HTML5 Canvas
📱 Browser-Based
```

---

# 👨‍💻 Author

## Sumit Helge

**Computer Science & Engineering**

Full-Stack Developer | Generative AI | Software Engineering

### GitHub

https://github.com/SumitHelge-star

---

# 📄 License

This project is available for educational and personal use.

---

## 🎨 CanvasCraft

> **Draw. Create. Express. — Directly in your browser.**
