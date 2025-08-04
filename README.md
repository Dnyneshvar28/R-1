<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>Privacy Policy</title></head>
<body>
  <h1>Privacy Policy</h1>
  <p>We do not collect personal data. Ads shown on this site are managed by Google AdSense which may use cookies to personalize ads.</p>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Typing Test</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <!-- AdSense Header Slot -->
  <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js" crossorigin="anonymous"></script>
  <ins class="adsbygoogle"
       style="display:block; text-align:center;"
       data-ad-client="ca-pub-xxxxxxxxxxxxxxxx"
       data-ad-slot="1234567890"
       data-ad-format="auto"
       data-full-width-responsive="true"></ins>
  <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>

  <div class="container">
    <h1>Typing Speed Test</h1>
    <div class="controls">
      <label for="language">Language:</label>
      <select id="language" onchange="changeLanguage()">
        <option value="english">English</option>
        <option value="hindi">Hindi</option>
        <option value="marathi">Marathi</option>
      </select>
    </div>
    <p id="text-display"></p>
    <textarea id="text-input" placeholder="Start typing here..." disabled></textarea>
    <div id="result">
      <p>Time Left: <span id="timer">60</span> sec</p>
      <p>WPM: <span id="wpm">0</span></p>
      <p>Accuracy: <span id="accuracy">0%</span></p>
      <button onclick="startTest()">Start Test</button>
    </div>
    <div class="leaderboard">
      <h2>Leaderboard (Local)</h2>
      <ol id="leaderboard-list"></ol>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>

const texts = {
  english: "Typing tests are a great way to improve your typing speed and accuracy. Practice makes perfect.",
  hindi: "टाइपिंग परीक्षण आपके टाइपिंग कौशल को बेहतर बनाने का एक शानदार तरीका है। अभ्यास से ही परिपूर्णता आती है।",
  marathi: "टायपिंग चाचणी हा टायपिंग गती आणि अचूकता सुधारण्यासाठी एक उत्कृष्ट मार्ग आहे. सराव केल्याने यश मिळते."
};

let startTime, timerInterval;
let timeLeft = 60;
let currentLang = "english";
let sampleText = texts[currentLang];

function changeLanguage() {
  currentLang = document.getElementById("language").value;
  sampleText = texts[currentLang];
  document.getElementById("text-display").innerText = sampleText;
  resetTest();
}

function startTest() {
  document.getElementById("text-input").value = "";
  document.getElementById("text-input").disabled = false;
  document.getElementById("text-input").focus();
  document.getElementById("wpm").innerText = "0";
  document.getElementById("accuracy").innerText = "0%";
  timeLeft = 60;
  document.getElementById("timer").innerText = timeLeft;
  document.getElementById("text-display").innerText = sampleText;
  startTime = new Date();
  clearInterval(timerInterval);
  timerInterval = setInterval(updateTimer, 1000);
}

function updateTimer() {
  timeLeft--;
  document.getElementById("timer").innerText = timeLeft;
  if (timeLeft <= 0) {
    clearInterval(timerInterval);
    document.getElementById("text-input").disabled = true;
    saveToLeaderboard();
  }
}

document.getElementById("text-input").addEventListener("input", function () {
  const typedText = this.value;
  const timeElapsed = (new Date() - startTime) / 1000 / 60;
  const typedWords = typedText.trim().split(/\s+/).length;
  const wpm = Math.round(typedWords / timeElapsed);

  let correctChars = 0;
  for (let i = 0; i < typedText.length; i++) {
    if (typedText[i] === sampleText[i]) correctChars++;
  }
  const accuracy = Math.round((correctChars / sampleText.length) * 100);

  document.getElementById("wpm").innerText = wpm || 0;
  document.getElementById("accuracy").innerText = accuracy + "%";
});

function saveToLeaderboard() {
  const name = prompt("Enter your name for leaderboard:");
  const wpm = document.getElementById("wpm").innerText;
  const entry = `${name} (${currentLang}) - ${wpm} WPM`;
  let list = document.getElementById("leaderboard-list");
  let item = document.createElement("li");
  item.textContent = entry;
  list.appendChild(item);
}

function resetTest() {
  document.getElementById("text-input").value = "";
  document.getElementById("text-input").disabled = true;
  document.getElementById("wpm").innerText = "0";
  document.getElementById("accuracy").innerText = "0%";
  clearInterval(timerInterval);
  document.getElementById("timer").innerText = "60";
}

<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>About Us</title></head>
<body>
  <h1>About This Typing Test</h1>
  <p>This typing test website is designed to help users improve their typing speed and accuracy in English, Hindi, and Marathi. Built for practice and performance measurement.</p>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head><meta charset="UTF-8"><title>Contact Us</title></head>
<body>
  <h1>Contact Us</h1>
  <p>If you have any questions or suggestions, feel free to email us at <strong>typingtest@example.com</strong>.</p>
</body>
</html>

body {
  font-family: Arial, sans-serif;
  background: #f2f2f2;
  text-align: center;
  padding: 30px;
}
.container {
  max-width: 700px;
  margin: auto;
  background: white;
  padding: 20px;
  border-radius: 12px;
}
#text-display {
  font-size: 18px;
  margin-bottom: 20px;
}
textarea {
  width: 100%;
  height: 120px;
  font-size: 16px;
  padding: 10px;
}
#result {
  margin-top: 20px;
}
button {
  padding: 10px 20px;
  font-size: 16px;
}
.controls {
  margin-bottom: 10px;
}
.leaderboard {
  margin-top: 30px;
  text-align: left;
}
