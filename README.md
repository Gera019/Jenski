<!DOCTYPE html>
<html>
<head>
    <title>Jen's Quiz Adventure ✨🧠🌍</title>
    <meta charset="UTF-8">
    <style>
        body {
            font-family: 'Segoe UI', sans-serif;
            background-color: #ffeef2;
            text-align: center;
            padding: 40px;
            color: #444;
        }

        h1 {
            color: #c77dff;
            font-size: 32px;
        }

        #question {
            font-size: 20px;
            margin-bottom: 20px;
        }

        .btn {
            padding: 10px 25px;
            margin: 10px;
            border: none;
            border-radius: 12px;
            background-color: #ffd6e0;
            color: #333;
            font-size: 16px;
            cursor: pointer;
            transition: 0.3s;
        }

        .btn:hover {
            background-color: #ffb3c6;
        }

        #result, #score {
            font-weight: bold;
            font-size: 18px;
            margin-top: 20px;
        }

        #nextBtn, #restartBtn {
            display: none;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <h1>Jen's Quiz Adventure ✨🧠🌍</h1>
    <p id="question">Loading question...</p>
    <div id="buttons"></div>

    <p id="result"></p>
    <button id="nextBtn" class="btn" onclick="nextQuestion()">Next Question</button>
    <button id="restartBtn" class="btn" onclick="restartGame()">Restart</button>
    <p id="score">Score: 0</p>

    <script>
        const questions = [
            // MATH QUESTIONS
            { question: "Math 🧮: What is 325 + 178?", options: ["503", "502", "504"], answer: "503" },
            { question: "Math 🧮: What is 412 - 189?", options: ["223", "222", "221"], answer: "223" },
            { question: "Math 🧮: What is 789 + 111?", options: ["900", "910", "899"], answer: "900" },
            { question: "Math 🧮: What is 600 - 397?", options: ["203", "202", "201"], answer: "203" },
            { question: "Math 🧮: What is 123 + 456?", options: ["578", "579", "580"], answer: "579" },

            // SCIENCE / PHYSICS QUESTIONS
            { question: "Physics 🌍: What is the third planet from the Sun?", options: ["Mars", "Earth", "Venus"], answer: "Earth" },
            { question: "Physics ⚖️: Who formulated the three laws of motion?", options: ["Einstein", "Newton", "Galileo"], answer: "Newton" },
            { question: "Physics 🌌: Which galaxy is Earth located in?", options: ["Andromeda", "Milky Way", "Whirlpool"], answer: "Milky Way" },
            { question: "Physics ⚗️: What happens when vinegar and baking soda mix?", options: ["It explodes", "It bubbles and fizzes", "It melts"], answer: "It bubbles and fizzes" },
            { question: "Physics 🧪: Which of these is a chemical change?", options: ["Melting ice", "Boiling water", "Burning paper"], answer: "Burning paper" }
        ];

        let current = 0;
        let score = 0;

        function loadQuestion() {
            const q = questions[current];
            document.getElementById("question").textContent = q.question;
            const buttonsDiv = document.getElementById("buttons");
            buttonsDiv.innerHTML = "";

            q.options.forEach(option => {
                const btn = document.createElement("button");
                btn.className = "btn";
                btn.textContent = option;
                btn.onclick = () => checkAnswer(option);
                buttonsDiv.appendChild(btn);
            });

            document.getElementById("result").textContent = "";
            document.getElementById("nextBtn").style.display = "none";
        }

        function checkAnswer(selected) {
            const correct = questions[current].answer;
            const result = document.getElementById("result");

            if (selected === correct) {
                result.textContent = "✅ Correct!";
                result.style.color = "green";
                score++;
            } else {
                result.textContent = ❌ Wrong! The correct answer is ${correct}.;
                result.style.color = "red";
            }

            document.getElementById("score").textContent = Score: ${score};
            document.getElementById("nextBtn").style.display = "inline-block";

            const btns = document.querySelectorAll(".btn");
            btns.forEach(btn => btn.disabled = true);
        }

        function nextQuestion() {
            current++;
            if (current < questions.length) {
                loadQuestion();
            } else {
                // FINALE MESSAGE
                document.getElementById("question").innerHTML =
                    "Quiz Complete!<br>Well done, Adventurer! ✨🎉🌟<br>You explored your brain and conquered the quiz!";
                document.getElementById("buttons").innerHTML = "";
                document.getElementById("result").textContent = Final Score: ${score}/${questions.length};
                document.getElementById("nextBtn").style.display = "none";
                document.getElementById("restartBtn").style.display = "inline-block";
            }
        }

        function restartGame() {
            current = 0;
            score = 0;
            document.getElementById("score").textContent = "Score: 0";
            document.getElementById("restartBtn").style.display = "none";
            loadQuestion();
        }

        // Start the quiz
        loadQuestion();
    </script>

</body>
</html>
