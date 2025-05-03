
### 1. Event Handling 🎈 

- <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Button Click</title>
    <style>
        #magicButton {
            padding: 10px 20px;
            font-size: 16px;
            background-color: royalblue;
            color: white;
            border: none;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        #magicButton:hover {
            background-color: deepskyblue;
        }
    </style>
</head>
<body>

    <button id="magicButton">Click me!</button>
    <p id="message"></p>

    <script>
        const button = document.getElementById("magicButton");
        const message = document.getElementById("message");

        // Click Event
        button.addEventListener("click", () => {
            message.textContent = "Button clicked! ✅";
        });

        // Hover Event
        button.addEventListener("mouseenter", () => {
            message.textContent = "You're hovering over the button! 🏄";
        });

        button.addEventListener("mouseleave", () => {
            message.textContent = "";
        });

        // Keypress Detection
        document.addEventListener("keydown", (event) => {
            message.textContent = `Key pressed: ${event.key} ⌨️`;
        });

        // Secret Action: Double Click
        button.addEventListener("dblclick", () => {
            message.textContent = "Double-click detected! Secret action activated! 🤫✨";
        });

    </script>

</body>
</html>

### 2. Interactive Elements 🎮 

- <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Moving Image Gallery</title>
    <style>
        #gallery-container {
            width: 300px;
            text-align: center;
            margin: auto;
        }
        #gallery-image {
            width: 100%;
            height: auto;
            border-radius: 10px;
            transition: opacity 0.5s ease-in-out;
        }
        #controls {
            margin-top: 10px;
        }
        button {
            padding: 10px;
            background: royalblue;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background: deepskyblue;
        }
    </style>
</head>
<body>

    <div id="gallery-container">
        <img id="gallery-image" src="image1.jpg" alt="Gallery Image">
        <div id="controls">
            <button onclick="prevImage()">⬅️ Prev</button>
            <button onclick="nextImage()">Next ➡️</button>
        </div>
    </div>

    <script>
        const images = ["git.jpeg", "Group Stadies.jpeg", "collaboration.jpg", "Respect.jpeg"];
        let currentIndex = 0;

        function updateImage() {
            const galleryImage = document.getElementById("gallery-image");
            galleryImage.style.opacity = 0;
            setTimeout(() => {
                galleryImage.src = images[currentIndex];
                galleryImage.style.opacity = 1;
            }, 300);
        }

        function prevImage() {
            currentIndex = (currentIndex - 1 + images.length) % images.length;
            updateImage();
        }

        function nextImage() {
            currentIndex = (currentIndex + 1) % images.length;
            updateImage();
        }
    </script>

</body>
</html>

### 3. Form Validation 📋✅  

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form Validation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 20px;
        }
        form {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background: lightgray;
            border-radius: 5px;
        }
        input {
            width: 100%;
            padding: 8px;
            margin: 10px 0;
            border: 1px solid gray;
            border-radius: 5px;
        }
        .error {
            color: red;
            font-size: 14px;
        }
    </style>
</head>
<body>

    <form id="signup-form">
        <h2>Sign Up</h2>
        <label>Email:</label>
        <input type="email" id="email" placeholder="Enter your email">
        <span class="error" id="emailError"></span>

        <label>Password:</label>
        <input type="password" id="password" placeholder="Enter password">
        <span class="error" id="passwordError"></span>

        <button type="submit">Register</button>
    </form>

    <script>
        const emailInput = document.getElementById("email");
        const passwordInput = document.getElementById("password");
        const emailError = document.getElementById("emailError");
        const passwordError = document.getElementById("passwordError");
        const form = document.getElementById("signup-form");

        function validateEmail() {
            const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,6}$/;
            if (!emailInput.value.match(emailPattern)) {
                emailError.textContent = "Invalid email format ❌";
            } else {
                emailError.textContent = "";
            }
        }

        function validatePassword() {
            if (passwordInput.value.length < 8) {
                passwordError.textContent = "Password must be at least 8 characters ❌";
            } else {
                passwordError.textContent = "";
            }
        }

        emailInput.addEventListener("input", validateEmail);
        passwordInput.addEventListener("input", validatePassword);

        form.addEventListener("submit", (event) => {
            validateEmail();
            validatePassword();

            if (emailError.textContent || passwordError.textContent) {
                event.preventDefault();
            }
        });
    </script>

</body>
</html>
