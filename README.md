<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Caption Generator</title>

<style>
body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: linear-gradient(135deg, #5f0a87, #0f3c78);
    color: white;
}

.container {
    display: flex;
    flex-wrap: wrap;
    min-height: 100vh;
    align-items: center;
    justify-content: center;
    padding: 20px;
}

/* LEFT SIDE */
.left {
    flex: 1;
    max-width: 400px;
}

.left h1 {
    font-size: 40px;
    margin-bottom: 10px;
}

.left p {
    opacity: 0.8;
    margin-bottom: 20px;
}

textarea {
    width: 100%;
    padding: 15px;
    border-radius: 15px;
    border: none;
    outline: none;
    font-size: 16px;
}

button {
    margin-top: 15px;
    padding: 12px 25px;
    border: none;
    border-radius: 20px;
    background: #ff9800;
    color: white;
    font-size: 16px;
    cursor: pointer;
}

button:hover {
    background: #ffa726;
}

/* RIGHT SIDE */
.right {
    flex: 1;
    max-width: 500px;
    margin-left: 40px;
}

.output {
    background: rgba(255,255,255,0.1);
    padding: 20px;
    border-radius: 20px;
    backdrop-filter: blur(10px);
}

.caption {
    background: rgba(255,255,255,0.15);
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 10px;
    animation: fade 0.5s ease;
}

@keyframes fade {
    from {opacity: 0;}
    to {opacity: 1;}
}

@media(max-width: 768px){
    .container {
        flex-direction: column;
    }
    .right {
        margin-left: 0;
        margin-top: 20px;
    }
}
</style>

</head>
<body>

<div class="container">

    <!-- LEFT -->
    <div class="left">
        <h1>AI Caption Generator</h1>
        <p>Generate viral captions instantly for your videos 🚀</p>

        <textarea id="inputText" placeholder="Enter your idea..."></textarea>
        <button onclick="generateCaptions()">Generate Captions</button>
    </div>

    <!-- RIGHT -->
    <div class="right">
        <div class="output" id="output">
            <p>Your captions will appear here...</p>
        </div>
    </div>

</div>

<script>
function generateCaptions() {
    const text = document.getElementById("inputText").value;
    const output = document.getElementById("output");

    if (!text) {
        output.innerHTML = "<div class='caption'>⚠️ Please enter text</div>";
        return;
    }

    const templates = [
        `🔥 ${text} vibes only!`,
        `💫 Living the moment: ${text}`,
        `❤️ ${text} feels different`,
        `🚀 ${text} to the next level`,
        `🌸 ${text} but make it aesthetic`,
        `😎 ${text} energy`,
        `💔 ${text} hits hard`,
        `✨ ${text} magic moment`,
        `🎬 ${text} story begins`,
        `🌍 ${text} world`,
        `📸 Captured: ${text}`,
        `🎯 ${text} goal vibes`,
        `🔥 Can't stop ${text}`,
        `💥 ${text} impact`,
        `🎵 ${text} rhythm`
    ];

    let captions = [];

    for (let i = 0; i < 10; i++) {
        const random = templates[Math.floor(Math.random() * templates.length)];
        captions.push(`<div class="caption">${random}</div>`);
    }

    output.innerHTML = captions.join("");
}
</script>

</body>
</html>
Ai caption generator 
