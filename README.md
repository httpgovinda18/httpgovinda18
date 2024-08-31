<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Slider</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
        }

        .slider {
            position: relative;
            width: 80%;
            max-width: 800px;
            overflow: hidden;
        }

        .slides {
            display: flex;
            transition: transform 0.5s ease-in-out;
        }

        .slide {
            min-width: 100%;
            box-sizing: border-box;
        }

        .slide img {
            width: 100%;
            height: auto;
            display: block;
        }

        button {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background-color: rgba(0, 0, 0, 0.5);
            color: white;
            border: none;
            cursor: pointer;
            padding: 10px;
            font-size: 24px;
            z-index: 10;
        }

        .prev {
            left: 10px;
        }

        .next {
            right: 10px;
        }
    </style>
</head>
<body>
    <div class="slider">
        <div class="slides">
            <div class="slide"><img src="image1.jpg" alt="Image 1"></div>
            <div class="slide"><img src="image2.jpg" alt="Image 2"></div>
            <div class="slide"><img src="image3.jpg" alt="Image 3"></div>
        </div>
        <button class="prev">❮</button>
        <button class="next">❯</button>
    </div>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const slides = document.querySelector('.slides');
            const slideCount = document.querySelectorAll('.slide').length;
            let currentIndex = 0;

            function showSlide(index) {
                if (index >= slideCount) {
                    currentIndex = 0;
                } else if (index < 0) {
                    currentIndex = slideCount - 1;
                } else {
                    currentIndex = index;
                }
                slides.style.transform = translateX(${-currentIndex * 100}%);
            }

            document.querySelector('.prev').addEventListener('click', () => {
                showSlide(currentIndex - 1);
            });

            document.querySelector('.next').addEventListener('click', () => {
                showSlide(currentIndex + 1);
            });

            setInterval(() => {
                showSlide(currentIndex + 1);
            }, 3000); 
        });
    </script>
</body>
</html>
