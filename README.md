<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Study Buddy</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f9fafb;
      color: #333;
      text-align: center;
      padding: 40px;
    }
    h1 {
      color: #2563eb;
    }
    #question-box, #answer-box {
      margin: 20px auto;
      padding: 20px;
      border-radius: 10px;
      max-width: 500px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
      font-size: 1.2rem;
    }
    #question-box {
      background: #e0f2fe;
      font-weight: bold;
    }
    #answer-box {
      background: #fef3c7;
    }
    button {
      padding: 10px 20px;
      margin-top: 20px;
      border: none;
      border-radius: 8px;
      background: #2563eb;
      color: #fff;
      cursor: pointer;
      font-size: 1rem;
    }
    button:hover {
      background: #1e40af;
    }
  </style>
</head>
<body>
  <h1>📚 Study Buddy</h1>
  <div id="question-box">Loading question...</div>
  <div id="answer-box">Loading answer...</div>
  <button onclick="loadQuestions()">🔄 Load Another</button>

  <script>
    async function loadQuestions() {
      try {
        const res = await fetch("YOUR_WEB_APP_URL_HERE"); // 🔑 replace this
        const data = await res.json();

        // Pick a random question
        const randomIndex = Math.floor(Math.random() * data.length);
        const item = data[randomIndex];

        document.getElementById("question-box").innerText = "Q: " + item.Question;
        document.getElementById("answer-box").innerText = "A: " + item.Answer;
      } catch (err) {
        console.error("Error loading data:", err);
        document.getElementById("question-box").innerText = "⚠️ Failed to load question.";
        document.getElementById("answer-box").innerText = "";
      }
    }

    // Load first question on startup
    loadQuestions();
  </script>
</body>
</html>
