edu-guide-greek/
├── README.md
├── index.html
├── courses.html
├── ai-chatbot.html
├── theoritiki-lessons.html
├── theoritiki-exercises.html
├── theoritiki-solutions.html
├── thetiki-lessons.html
├── thetiki-exercises.html
├── thetiki-solutions.html
├── texnologiki-lessons.html
├── texnologiki-exercises.html
├── texnologiki-solutions.html
├── math-algebra.html
├── math-geometry.html
├── sos.html
├── data/
│   ├── theoritiki.json
│   ├── thetiki.json
│   ├── texnologiki.json
│   └── math.json
└── assets/
    ├── style.css
    └── script.js

/* README.md */
# edu-guide-greek
Πλήρες εκπαιδευτικό βοήθημα για υποψήφιους Πανελλαδικών. Περιλαμβάνει μαθήματα, ασκήσεις, λύσεις, SOS και AI βοηθό.

/* index.html */
<!DOCTYPE html>
<html lang="el">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>edu-guide-greek</title>
<link rel="stylesheet" href="assets/style.css">
</head>
<body>
<h1>Κεντρική σελίδα - Επιλογή Κατεύθυνσης</h1>
<ul>
<li><a href="theoritiki-lessons.html">Θεωρητική Κατεύθυνση</a></li>
<li><a href="thetiki-lessons.html">Θετική Κατεύθυνση</a></li>
<li><a href="texnologiki-lessons.html">Τεχνολογική/Οικονομική Κατεύθυνση</a></li>
<li><a href="math-algebra.html">Μαθηματικά</a></li>
<li><a href="ai-chatbot.html">AI Βοηθός</a></li>
</ul>
</body>
</html>

/* ai-chatbot.html */
<!DOCTYPE html>
<html lang="el">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Φροντιστηριακός Βοηθός</title>
<link rel="stylesheet" href="assets/style.css">
</head>
<body>
<h1>Ψηφιακό Φροντιστήριο AI</h1>
<div id="chatbox"></div>
<input type="text" id="userInput" placeholder="Γράψε την ερώτηση..." />
<button onclick="sendMessage()">Αποστολή</button>
<script>
async function sendMessage() {
  const input = document.getElementById("userInput");
  const msg = input.value.trim();
  if(!msg) return;
  const chatbox = document.getElementById("chatbox");
  chatbox.innerHTML += `<div><b>Μαθητής:</b> ${msg}</div>`;

  const response = await fetch("https://api.openai.com/v1/chat/completions", {
    method:"POST",
    headers:{
      "Content-Type":"application/json",
      "Authorization":"Bearer YOUR_API_KEY"
    },
    body: JSON.stringify({
      model:"gpt-4",
      messages:[
        { role:"system", content:"Είσαι ευγενικός καθηγητής. Απαντάς μόνο σε ερωτήσεις μαθημάτων. Αν η ερώτηση είναι off-topic, επαναφέρεις τη συζήτηση ευγενικά στο μάθημα." },
        { role:"user", content: msg }
      ],
      max_tokens: 500
    })
  });

  const data = await response.json();
  const answer = data.choices[0].message.content;
  chatbox.innerHTML += `<div><b>AI:</b> ${answer}</div>`;
  chatbox.scrollTop = chatbox.scrollHeight;
  input.value = "";
}
</script>
</body>
</html>

/* Παραδείγματα HTML για Lessons, Exercises, Solutions */
/* theoritiki-lessons.html */
<!DOCTYPE html>
<html lang="el">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Θεωρητική Κατεύθυνση - Μαθήματα</title>
<link rel="stylesheet" href="assets/style.css">
</head>
<body>
<h1>Θεωρητική Κατεύθυνση - Μαθήματα</h1>
<ul id="lessonsList"></ul>
<a href="index.html">← Επιστροφή στην αρχική</a>
<script src="assets/script.js"></script>
<script>loadLessons('theoritiki.json', 'lessonsList');</script>
</body>
</html>

/* theoritiki-exercises.html */
<!DOCTYPE html>
<html lang="el">
<head><meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0"><title>Θεωρητική - Ασκήσεις</title><link rel="stylesheet" href="assets/style.css"></head>
<body>
<h1>Θεωρητική Κατεύθυνση - Ασκήσεις</h1>
<ul id="exercisesList"></ul>
<a href="index.html">← Επιστροφή στην αρχική</a>
<script src="assets/script.js"></script>
<script>loadExercises('theoritiki.json', 'exercisesList');</script>
</body>
</html>

/* theoritiki-solutions.html */
<!DOCTYPE html>
<html lang="el">
<head><meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0"><title>Θεωρητική - Λύσεις</title><link rel="stylesheet" href="assets/style.css"></head>
<body>
<h1>Θεωρητική Κατεύθυνση - Λύσεις</h1>
<ul id="solutionsList"></ul>
<a href="index.html">← Επιστροφή στην αρχική</a>
<script src="assets/script.js"></script>
<script>loadSolutions('theoritiki.json', 'solutionsList');</script>
</body>
</html>

