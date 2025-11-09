# Ex05 Image Carousel
## Date: 15-10-2025

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM

## Carousel.js
```
import React, { useState } from "react";
import "./Carousel.css";

const Carousel = () => {
  const images = [
    "https://picsum.photos/id/1015/600/300",
    "https://picsum.photos/id/1016/600/300",
    "https://picsum.photos/id/1018/600/300",
    "https://picsum.photos/id/1025/600/300",
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const prevSlide = () => {
    setCurrentIndex((prev) =>
      prev === 0 ? images.length - 1 : prev - 1
    );
  };

  const nextSlide = () => {
    setCurrentIndex((prev) =>
      prev === images.length - 1 ? 0 : prev + 1
    );
  };

  return (
    <div className="carousel-container">
      <button className="nav-btn left" onClick={prevSlide}>❮</button>

      <img
        src={images[currentIndex]}
        alt="carousel-img"
        className="carousel-img"
      />

      <button className="nav-btn right" onClick={nextSlide}>❯</button>

      <div className="dots">
        {images.map((_, index) => (
          <span
            key={index}
            className={currentIndex === index ? "dot active" : "dot"}
            onClick={() => setCurrentIndex(index)}
          ></span>
        ))}
      </div>
    </div>
  );
};

export default Carousel;
```

## Carousel.css
```
.carousel-container {
  position: relative;
  width: 600px;
  margin: 30px auto;
  border-radius: 12px;
  overflow: hidden;
}

.carousel-img {
  width: 100%;
  border-radius: 10px;
  transition: 0.5s ease;
}

.nav-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0,0,0,0.4);
  border: none;
  color: white;
  font-size: 22px;
  padding: 10px 14px;
  cursor: pointer;
  border-radius: 6px;
}

.left { left: 10px; }
.right { right: 10px; }

.nav-btn:hover {
  background: rgba(0,0,0,0.6);
}

.dots {
  text-align: center;
  margin-top: 10px;
}

.dot {
  height: 10px;
  width: 10px;
  margin: 3px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  cursor: pointer;
}

.active {
  background-color: #007bff;
}
```

## App.js
```
import React from "react";
import Carousel from "./carousel.js";

function App() {
  return (
    <div>
      <h2 style={{textAlign: "center"}}>React Image Carousel</h2>
      <Carousel />
    </div>
  );
}

export default App;

```
## OUTPUT

<img width="1354" height="690" alt="image" src="https://github.com/user-attachments/assets/24155f4a-2813-471d-a870-faac4c9beaf3" />

<img width="1365" height="686" alt="image" src="https://github.com/user-attachments/assets/bf2ed636-e4ea-451b-a636-6e0626f681c3" />

## RESULT
The program for creating Image Carousel using React is executed successfully.
