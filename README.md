# Ex05 Image Carousel
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
App.css
```
#root {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  text-align: center;
}

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.react:hover {
  filter: drop-shadow(0 0 2em #61dafbaa);
}

@keyframes logo-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

@media (prefers-reduced-motion: no-preference) {
  a:nth-of-type(2) .logo {
    animation: logo-spin infinite 20s linear;
  }
}

.card {
  padding: 2em;
}

.read-the-docs {
  color: #888;
}
```
App.jsx
```
#root {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  text-align: center;
}

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.react:hover {
  filter: drop-shadow(0 0 2em #61dafbaa);
}

@keyframes logo-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

@media (prefers-reduced-motion: no-preference) {
  a:nth-of-type(2) .logo {
    animation: logo-spin infinite 20s linear;
  }
}

.card {
  padding: 2em;
}

.read-the-docs {
  color: #888;
}
```
ImageCarousel.jsx
```
import React, { useState, useEffect } from 'react';

const images = [
  'https://picsum.photos/id/1018/600/400',
  'https://picsum.photos/id/1015/600/400',
  'https://picsum.photos/id/1019/600/400',
  'https://picsum.photos/id/1020/600/400',
];

export default function ImageCarousel() {
  const [currentIndex, setCurrentIndex] = useState(0);

  // Next image function
  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  // Previous image function
  const prevImage = () => {
    setCurrentIndex((currentIndex - 1 + images.length) % images.length);
  };

  // Auto-rotation effect
  useEffect(() => {
    const interval = setInterval(() => {
      nextImage();
    }, 3000);

    // Cleanup on unmount
    return () => clearInterval(interval);
  }, [currentIndex]); // currentIndex in dependency ensures it updates correctly

 return (
  <div style={{ width: '600px', margin: 'auto', textAlign: 'center' }}>
    <h2>Image Carousel</h2>
    <img
      src={images[currentIndex]}
      alt={`Slide ${currentIndex}`}
      style={{ width: '100%', height: 'auto', borderRadius: '10px' }}
    />
    <div style={{ marginTop: '10px' }}>
      <button onClick={prevImage}>Previous</button>
      <span style={{ margin: '0 15px' }}>
        {currentIndex + 1} / {images.length}
      </span>
      <button onClick={nextImage}>Next</button>
    </div>

    {/* Add your footer here */}
    <footer style={{ marginTop: '20px', fontStyle: 'italic', color: '#555' }}>
      <p>Name: DIVYA M</p>
      <p>Register Number: 212223040043</p>
    </footer>
  </div>
);

}
```
## OUTPUT
<img width="956" height="952" alt="image" src="https://github.com/user-attachments/assets/d7f34b05-56ad-4745-83da-2488128e33e4" />
<img width="959" height="959" alt="image" src="https://github.com/user-attachments/assets/10936bf3-2c7a-4e64-b902-d641399e13ba" />
<img width="956" height="1012" alt="image" src="https://github.com/user-attachments/assets/db70325e-9d99-4b4f-9a8f-04292a2198cd" />
<img width="956" height="1010" alt="image" src="https://github.com/user-attachments/assets/6fefa133-c4c2-4048-9046-8b69d11a0a5a" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
