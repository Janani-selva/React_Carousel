# Ex05 Image Carousel
## Date: 29-05-2026

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

## Carousel.jsx
```
import React, { useState, useEffect } from "react";
import "./Carousel.css";

import img1 from "./assets/sg.png";
import img2 from "./assets/usa.png";
import img3 from "./assets/german.png";
import img4 from "./assets/japan.png";

function Carousel() {
  const images = [img1, img2, img3, img4];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex(
      (prevIndex) => (prevIndex + 1) % images.length
    );
  };

  const prevImage = () => {
    setCurrentIndex(
      (prevIndex) =>
        (prevIndex - 1 + images.length) % images.length
    );
  };

  useEffect(() => {
    const interval = setInterval(() => {
      setCurrentIndex(
        (prevIndex) =>
          (prevIndex + 1) % images.length
      );
    }, 3000);

    return () => clearInterval(interval);
  }, [images.length]);

  return (
    <div className="carousel-container">
      <h1>Image Carousel</h1>

      <img
        src={images[currentIndex]}
        alt="carousel"
        className="carousel-image"
      />

      <div className="buttons">
        <button onClick={prevImage}>◀ Previous</button>
        <button onClick={nextImage}>Next ▶</button>
      </div>
    </div>
  );
}

export default Carousel;
```

## Carousel.css
```
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #4e54c8, #8f94fb);
}

.carousel-container {
  text-align: center;
  margin-top: 40px;
}

.carousel-container h1 {
  color: white;
}

.carousel-image {
  width: 700px;
  height: 400px;
  object-fit: cover;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.3);
}

.buttons {
  margin-top: 20px;
}

.buttons button {
  padding: 10px 20px;
  margin: 0 10px;
  border: none;
  border-radius: 8px;
  background-color: #ffffff;
  color: #4e54c8;
  font-size: 16px;
  cursor: pointer;
  font-weight: bold;
}

.buttons button:hover {
  background-color: #e6e6e6;
}
```

## App.jsx
```
import React from "react";
import Carousel from "./Carousel";

function App() {
  return (
    <div>
      <Carousel />
    </div>
  );
}

export default App;
```

## OUTPUT

<img width="1767" height="1037" alt="Screenshot 2026-05-29 111555" src="https://github.com/user-attachments/assets/4e14ce1f-0f30-4075-878b-c995dacad060" />
<img width="1787" height="1061" alt="Screenshot 2026-05-29 111611" src="https://github.com/user-attachments/assets/12af9071-6787-4285-86c7-5499f442ae6e" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
