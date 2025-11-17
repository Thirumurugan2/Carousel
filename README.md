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
App.jsx
```
import React, { useState } from "react";
import "./app.css";


export default function App() {
const images = [
"https://images.unsplash.com/photo-1506765515384-028b60a970df?w=1200",
"https://images.unsplash.com/photo-1500534623283-312aade485b7?w=1200",
"https://images.unsplash.com/photo-1521295121783-8a321d551ad2?w=1200",
"https://images.unsplash.com/photo-1506744038136-46273834b3fb?w=1200",
"https://images.unsplash.com/photo-1519125323398-675f0ddb6308?w=1200",
];


const [index, setIndex] = useState(0);


const next = () => setIndex((index + 1) % images.length);
const prev = () => setIndex((index - 1 + images.length) % images.length);


return (
<div className="carousel">
<h1>Image Carousel</h1>
<button onClick={prev} className="btn">❮</button>
<img src={images[index]} alt="slide" className="slide" />
<button onClick={next} className="btn">❯</button>
<br />
<div>
  <footer className="name"> Name : THIRUMURUGAN R</footer>
  <p className="regno"> RegNo : 212223220118</p>
</div>
<br />
</div>

);
}
```

App.css
```
.carousel {
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
gap: 20px;
width: 100%;
margin-top: 30px;
}


.slide {
width: 75%;
max-width: 900px;
border-radius: 16px;
box-shadow: 0 8px 20px rgba(0, 0, 0, 0.25);
transition: transform 0.4s ease, box-shadow 0.4s ease;
}


.slide:hover {
transform: scale(1.03);
box-shadow: 0 12px 28px rgba(0, 0, 0, 0.3);
}


.btn {
font-size: 28px;
background: linear-gradient(135deg, #00000090, #00000050);
color: white;
border: none;
padding: 12px 18px;
border-radius: 50%;
cursor: pointer;
backdrop-filter: blur(6px);
transition: 0.3s ease;
}


.btn:hover {
background: #000000cc;
transform: scale(1.1);
}

.name {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: 30px;
  color: rgb(255, 255, 255);
  background-color: rgb(168, 0, 92);
  padding: 10px;
  border-radius: 20px;
}

.regno {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: 30px;
  color: rgb(255, 255, 255);
  background-color: rgb(168, 0, 92);
  padding: 10px;
  border-radius: 20px;
  text-align: center;
}
```

## OUTPUT
<img width="1918" height="1018" alt="image" src="https://github.com/user-attachments/assets/e61c9c5f-75d1-4f22-ae40-6d425554f30a" />
<img width="1918" height="1017" alt="image" src="https://github.com/user-attachments/assets/2f9bb6bd-c275-49e9-a26b-6c036d18bbec" />
<img width="1917" height="1021" alt="image" src="https://github.com/user-attachments/assets/69f0776f-839d-4580-8d56-b527a9dfa523" />
<img width="1918" height="1022" alt="image" src="https://github.com/user-attachments/assets/fb37bd14-b515-4c5e-93b7-f7d0215670aa" />




## RESULT
The program for creating Image Carousel using React is executed successfully.
