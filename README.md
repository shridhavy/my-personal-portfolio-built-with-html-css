<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gulshan Yadav - Portfolio</title>
    <style>
        body {
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #000;
            color: #f1f1f1;
            overflow-x: hidden;
        }

        canvas#stars {
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
        }

        header {
            text-align: center;
            padding: 40px;
            background: #111;
        }

        header h1 {
            font-size: 3em;
            color: #00ffff;
        }

        .container {
            padding: 30px;
            max-width: 1000px;
            margin: auto;
        }

        img.profile {
            display: block;
            margin: auto;
            width: 200px;
            height: 200px;
            border-radius: 50%;
            border: 4px solid #00ffff;
            object-fit: cover;
        }

        .intro,
        .skills,
        .gallery,
        .contact,
        .thankyou,
        .upload-section {
            margin-top: 40px;
            animation: fadeIn 1.5s ease-in;
        }

        .skills-buttons button {
            background: #00ffff;
            color: #000;
            padding: 10px 20px;
            margin: 5px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
        }

        .skills-details {
            margin-top: 20px;
            display: none;
            background: #222;
            padding: 15px;
            border-radius: 10px;
        }

        .skills-details.active {
            display: block;
        }

        .gallery img,
        .upload-preview img,
        .upload-preview video {
            width: 100%;
            max-width: 150px;
            height: auto;
            margin: 10px;
            border-radius: 10px;
            object-fit: cover;
            border: 2px solid #00ffff;
            transition: transform 0.3s;
        }

        .gallery img:hover {
            transform: scale(1.05);
        }

        .contact-box {
            background: #222;
            padding: 20px;
            border-radius: 10px;
        }

        .thankyou {
            text-align: center;
            font-size: 1.5em;
            color: #ff66cc;
            margin-top: 60px;
        }

        h2 {
            color: #00ffff;
        }

        .upload-section input {
            margin-top: 10px;
        }

        .upload-preview {
            display: flex;
            flex-wrap: wrap;
        }

        @keyframes fadeIn {
            0% {
                opacity: 0;
                transform: translateY(30px);
            }

            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @media screen and (max-width: 600px) {
            header h1 {
                font-size: 2em;
            }

            .skills-buttons button {
                font-size: 0.9em;
                padding: 8px 15px;
            }

            img.profile {
                width: 150px;
                height: 150px;
            }

            .gallery img,
            .upload-preview img,
            .upload-preview video {
                max-width: 100px;
            }
        }
    </style>
</head>

<body>
    <canvas id="stars"></canvas>

    <audio autoplay loop>
        <source src="https://www.bensound.com/bensound-music/bensound-slowmotion.mp3" type="audio/mp3">
    </audio>

    <header>
        <h1>Gulshan Yadav</h1>
        <a href="https://www.instagram.com/gulshan_2k5?igsh=MTAyaDZrdnJmZnhuYg==" style="color: #00ffff; text-decoration: none;">Instagram Profile</a>
    </header>

    <div class="container">
        <img src="https://i.ibb.co/vw4w60h/gulshan.jpg" alt="Gulshan Yadav" class="profile">

        <div class="intro">
            <h2>About Me</h2>
            <p>Hello! I'm <strong>Gulshan Yadav</strong>, passionate about performing arts including acting, dancing, singing, karate and nukkad naatak.</p>
        </div>

        <div class="skills">
            <h2>My Skills</h2>
            <div class="skills-buttons">
                <button onclick="showDetail('acting')">Acting 🎭</button>
                <button onclick="showDetail('dancing')">Dancing 💃</button>
                <button onclick="showDetail('singing')">Singing 🎤</button>
                <button onclick="showDetail('karate')">Karate 🥋</button>
            </div>
            <div id="acting" class="skills-details">
                <p>Experienced in dramatic and street theatre performances. Acted in impactful roles related to social themes.</p>
            </div>
            <div id="dancing" class="skills-details">
                <p>Energetic dancer skilled in freestyle and traditional styles. Participated in school and local events.</p>
            </div>
            <div id="singing" class="skills-details">
                <p>Love singing classical and Bollywood songs. Performances in local cultural shows and school functions.</p>
            </div>
            <div id="karate" class="skills-details">
                <p>Trained in karate and participated in district level events. Focused on discipline and fitness.</p>
            </div>
        </div>

        <div class="upload-section">
            <h2>Upload My Skills Images/Videos</h2>
            <input type="file" accept="image/*,video/*" multiple onchange="previewFiles(event)">
            <div class="upload-preview" id="preview"></div>
        </div>

        <div class="gallery">
            <h2>Gallery</h2>
            <img src="https://i.ibb.co/5LFxXZL/gallery1.jpg" alt="Performance 1">
            <img src="https://i.ibb.co/CKYcJBs/gallery2.jpg" alt="Performance 2">
            <img src="https://i.ibb.co/yWdncbW/gallery3.jpg" alt="Performance 3">
        </div>

        <div class="gallery">
            <h2>Certificates</h2>
            <p>Uploaded soon: Participation and winning certificates for nukkad naatak and other competitions.</p>
        </div>

        <div class="contact">
            <h2>Contact</h2>
            <div class="contact-box">
                <p><strong>Phone:</strong> 7973102036</p>
                <p><strong>Email:</strong> gulshan137yadav@gmail.com</p>
            </div>
        </div>

        <div class="thankyou">
            <p>Thank you for visiting!</p>
        </div>
    </div>

    <script>
        function showDetail(id) {
            const details = document.querySelectorAll('.skills-details');
            details.forEach(detail => detail.classList.remove('active'));
            document.getElementById(id).classList.add('active');
        }

        // Stars animation background
        const canvas = document.getElementById('stars');
        const ctx = canvas.getContext('2d');
        let stars = [], count = 100;

        function resize() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        function createStars() {
            stars = [];
            for (let i = 0; i < count; i++) {
                stars.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    radius: Math.random() * 1.5,
                    alpha: Math.random()
                });
            }
        }

        function drawStars() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            for (let star of stars) {
                ctx.beginPath();
                ctx.arc(star.x, star.y, star.radius, 0, 2 * Math.PI);
                ctx.fillStyle = `rgba(255, 255, 255, ${star.alpha})`;
                ctx.fill();
            }
            requestAnimationFrame(drawStars);
        }

        window.addEventListener('resize', () => {
            resize();
            createStars();
        });

        resize();
        createStars();
        drawStars();

        // Preview uploads
        function previewFiles(event) {
            const files = event.target.files;
            const preview = document.getElementById('preview');
            preview.innerHTML = '';

            for (let file of files) {
                const reader = new FileReader();
                reader.onload = function (e) {
                    const url = e.target.result;
                    const element = document.createElement(file.type.startsWith('video') ? 'video' : 'img');
                    element.src = url;
                    if (file.type.startsWith('video')) element.controls = true;
                    preview.appendChild(element);
                };
                reader.readAsDataURL(file);
            }
        }
    </script>
</body>

</html>
