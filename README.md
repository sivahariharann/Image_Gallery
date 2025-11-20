# Ex.08 Design of Interactive Image Gallery
## DATE:10-11-2025
## AIM
  To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS

## Step 1:

Clone the github repository and create Django admin interface

## Step 2:

Change settings.py file to allow request from all hosts.

## Step 3:

Use CSS for positioning and styling.

## Step 4:

Write JavaScript program for implementing interactivit

## Step 5:

Validate the HTML and CSS code

## Step 6:

Publish the website in the given URL.

## PROGRAM
'''
#gallery.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Interactive Photo Gallery</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(to right, #fdfbfb, #ebedee);
      color: #333;
    }

    h1 {
      text-align: center;
      padding: 40px 10px 20px;
      font-size: 2.5rem;
      background: linear-gradient(90deg, #ff6a00, #ee0979);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      font-weight: bold;
    }

    .gallery-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
      padding: 20px;
      max-width: 1200px;
      margin: auto;
    }

    .gallery-item img {
      width: 100%;
      height: 250px;
      object-fit: cover;
      border-radius: 15px;
      box-shadow: 0 6px 16px rgba(0, 0, 0, 0.1);
      transition: transform 0.35s ease, box-shadow 0.35s ease;
      cursor: pointer;
    }

    .gallery-item img:hover {
      transform: scale(1.05);
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
    }

    .modal {
      display: none;
      position: fixed;
      inset: 0;
      background-color: rgba(0, 0, 0, 0.85);
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }

    .modal-content {
      max-width: 90%;
      max-height: 80%;
      border-radius: 12px;
      box-shadow: 0 0 30px rgba(255, 255, 255, 0.15);
      animation: fadeIn 0.3s ease-in-out;
    }

    .close {
      position: absolute;
      top: 20px;
      right: 30px;
      font-size: 40px;
      color: #fff;
      cursor: pointer;
      font-weight: bold;
      transition: color 0.3s ease;
    }

    .close:hover {
      color: #ffcccc;
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: scale(0.95);
      }
      to {
        opacity: 1;
        transform: scale(1);
      }
    }

    @media (max-width: 600px) {
      .gallery-item img {
        height: 180px;
      }
    }
  </style>
</head>
<body>

  <h1>Interactive Photo Gallery</h1>

  <div class="gallery-container">
    <div class="gallery-item">
      <img src="Ferrari.jpg" alt="Image 1">
    </div>
    <div class="gallery-item">
      <img src="mercedes.jpg" alt="Image 2">
    </div>
    <div class="gallery-item">
      <img src="mclaren.jpg" alt="Image 3">
    </div>
    <div class="gallery-item">
      <img src="Bugatti.jpg" alt="Image 4">
    </div>
    <div class="gallery-item">
      <img src="BMW.jpg" alt="Image 5">
    </div>
  </div>

  <div class="modal" id="modal">
    <span class="close" id="close">&times;</span>
    <img class="modal-content" id="modal-img" alt="Expanded view">
  </div>

  <script>
    const modal = document.getElementById('modal');
    const modalImg = document.getElementById('modal-img');
    const closeBtn = document.getElementById('close');
    const images = document.querySelectorAll('.gallery-item img');

    images.forEach(img => {
      img.addEventListener('click', () => {
        modal.style.display = 'flex';
        modalImg.src = img.src;
        modalImg.alt = img.alt;
      });
    });

    closeBtn.addEventListener('click', () => {
      modal.style.display = 'none';
    });

    modal.addEventListener('click', (e) => {
      if (e.target === modal) {
        modal.style.display = 'none';
      }
    });
  </script>

</body>
</html>


#styles.css

/* General body styling */
body {
    margin: 0;
    padding: 0;
    font-family: 'Segoe UI', Arial, sans-serif;
    background: linear-gradient(to right, #f0f2f5, #dfe9f3);
    color: #333;
}

/* Container for the image gallery */
.gallery-container {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 24px;
    padding: 50px 20px;
    max-width: 1200px;
    margin: auto;
}

/* Individual image styling */
.gallery-item img {
    width: 100%;
    height: 250px;
    object-fit: cover;
    border-radius: 14px;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
    transition: transform 0.35s ease, box-shadow 0.35s ease;
    cursor: pointer;
}

.gallery-item img:hover {
    transform: scale(1.05);
    box-shadow: 0 16px 32px rgba(0, 0, 0, 0.18);
}

/* Modal overlay */
.modal {
    display: none;
    position: fixed;
    inset: 0;
    background-color: rgba(0, 0, 0, 0.85);
    justify-content: center;
    align-items: center;
    z-index: 1000;
    animation: fadeIn 0.3s ease-in-out;
}

/* Modal image content */
.modal-content {
    max-width: 90%;
    max-height: 80%;
    border-radius: 12px;
    box-shadow: 0 0 40px rgba(255, 255, 255, 0.2);
    animation: zoomIn 0.3s ease;
}

/* Close button */
.close {
    position: absolute;
    top: 25px;
    right: 35px;
    font-size: 38px;
    color: #fff;
    font-weight: bold;
    cursor: pointer;
    transition: color 0.3s ease;
}

.close:hover,
.close:focus {
    color: #ffbbbb;
}

/* Animations */
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

@keyframes zoomIn {
    from { transform: scale(0.95); opacity: 0.8; }
    to { transform: scale(1); opacity: 1; }
}

/* Responsive adjustment */
@media (max-width: 600px) {
    .gallery-item img {
        height: 180px;
    }

    .close {
        top: 20px;
        right: 25px;
        font-size: 32px;
    }
}


#js


document.addEventListener('DOMContentLoaded', () => {
  const images = document.querySelectorAll('.gallery-item img');
  const modal = document.getElementById('modal');
  const modalImg = document.getElementById('modal-img');
  const closeBtn = document.getElementById('close');

  // Function to open modal
  const openModal = (src, alt) => {
    modal.style.display = 'flex';
    modalImg.src = src;
    modalImg.alt = alt || 'Expanded image';
    modalImg.classList.add('fade-in');
  };

  // Function to close modal
  const closeModal = () => {
    modal.style.display = 'none';
    modalImg.src = '';
    modalImg.alt = '';
    modalImg.classList.remove('fade-in');
  };

  // Open modal on image click
  images.forEach(image => {
    image.addEventListener('click', () => {
      openModal(image.src, image.alt);
    });
  });

  // Close modal on close button
  closeBtn.addEventListener('click', closeModal);

  // Close modal on background click
  modal.addEventListener('click', event => {
    if (event.target === modal) {
      closeModal();
    }
  });
});
'''

## OUTPUT
![alt text](<Screenshot 2025-11-09 151053.png>)
![alt text](<Screenshot 2025-11-09 151504.png>)
![alt text](<Screenshot 2025-11-09 151516.png>)
![alt text](<Screenshot 2025-11-09 151527.png>)
![alt text](<Screenshot 2025-11-09 151542.png>)
![alt text](<Screenshot 2025-11-09 151558.png>)
## RESULT
  The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
