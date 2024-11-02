# Aps
social-media-website/
├── index.html
├── profile.html
├── styles.css
├── script.js

HTML (index.html)

<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>সোশ্যাল মিডিয়া</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>সোশ্যাল মিডিয়া</h1>
        <nav>
            <a href="profile.html">প্রোফাইল</a>
            <a href="#">লগ আউট</a>
        </nav>
    </header>
    <main>
        <h2>নতুন পোস্ট তৈরি করুন</h2>
        <textarea id="postContent" placeholder="আপনার চিন্তাভাবনা লিখুন..."></textarea>
        <button id="postButton">পোস্ট করুন</button>
        
        <div id="posts"></div>
    </main>
    <footer>
        <p>&copy; 2024 সোশ্যাল মিডিয়া</p>
    </footer>
    <script src="script.js"></script>
</body>
</html>

HTML (profile.html)

<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>প্রোফাইল</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>প্রোফাইল</h1>
        <nav>
            <a href="index.html">হোম</a>
            <a href="#">লগ আউট</a>
        </nav>
    </header>
    <main>
        <h2>প্রোফাইল আপডেট করুন</h2>
        <input type="file" id="profilePic" accept="image/*">
        <button id="uploadButton">ছবি আপলোড করুন</button>
        <div id="profileImageContainer"></div>
    </main>
    <footer>
        <p>&copy; 2024 সোশ্যাল মিডিয়া</p>
    </footer>
    <script src="script.js"></script>
</body>
</html>

CSS (styles.css)

body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

header {
    background: #35424a;
    color: white;
    padding: 20px;
    text-align: center;
}

nav a {
    margin: 0 15px;
    color: white;
    text-decoration: none;
}

main {
    padding: 20px;
}

textarea {
    width: 100%;
    height: 100px;
}

footer {
    text-align: center;
    padding: 10px;
    background: #35424a;
    color: white;
    position: relative;
    bottom: 0;
    width: 100%;
}

#posts {
    margin-top: 20px;
}

JavaScript (script.js)

document.getElementById('postButton').addEventListener('click', () => {
    const content = document.getElementById('postContent').value;
    if (content) {
        const postDiv = document.createElement('div');
        postDiv.className = 'post';
        postDiv.innerHTML = `<p>${content}</p><button class="likeButton">লাইক</button> <span class="likeCount">0</span>`;

        document.getElementById('posts').appendChild(postDiv);
        document.getElementById('postContent').value = '';

        const likeButton = postDiv.querySelector('.likeButton');
        const likeCount = postDiv.querySelector('.likeCount');

        likeButton.addEventListener('click', () => {
            let count = parseInt(likeCount.innerText);
            count++;
            likeCount.innerText = count;
        });
    }
});

document.getElementById('uploadButton').addEventListener('click', () => {
    const fileInput = document.getElementById('profilePic');
    const file = fileInput.files[0];
    if (file) {
        const reader = new FileReader();
        reader.onload = function (e) {
            const img = document.createElement('img');
            img.src = e.target.result;
            img.style.width = '100px'; // Set width as needed
            img.style.height = '100px'; // Set height as needed
            document.getElementById('profileImageContainer').appendChild(img);
        };
        reader.readAsDataURL(file);
    }
});




