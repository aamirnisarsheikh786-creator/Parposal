<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Love Quiz</title>

<style>
body {
    margin: 0;
    background: linear-gradient(135deg, #ff6a88, #ff99ac);
    font-family: Arial, sans-serif;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
}

.heart {
    position: absolute;
    color: red;
    animation: float 6s linear infinite;
}

@keyframes float {
    0% {transform: translateY(0); opacity: 1;}
    100% {transform: translateY(-800px); opacity: 0;}
}

#card {
    background: white;
    width: 360px;
    padding: 25px;
    border-radius: 20px;
    text-align: center;
    box-shadow: 0 0 25px rgba(0,0,0,0.3);
}

button {
    background: #ff4d6d;
    color: white;
    border: none;
    padding: 10px 18px;
    border-radius: 20px;
    margin: 8px;
    cursor: pointer;
    font-size: 15px;
}

#watermark {
    margin-top: 15px;
    font-size: 11px;
    color: gray;
}

/* Popup */
#popup {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: rgba(0,0,0,0.6);
    display: none;
    justify-content: center;
    align-items: center;
}

#popupBox {
    background: white;
    padding: 30px;
    border-radius: 20px;
    text-align: center;
    animation: scale 0.5s ease;
}

@keyframes scale {
    from {transform: scale(0.5);}
    to {transform: scale(1);}
}
</style>
</head>

<body>

<div id="card">
    <h2>Small Quiz 💖</h2>
    <p id="question">Question 1: How is Aamir as a person?</p>
    <div id="answers">
        <button onclick="nextQuestion()">Kind & Caring</button>
        <button onclick="nextQuestion()">Rude</button>
    </div>
</div>

<!-- Popup -->
<div id="popup">
  <div id="popupBox">
    <h2>🎉 Congratulations 💖</h2>
    <p>You just made Aamir the happiest person!</p>
    <button onclick="goWhatsApp()">Continue</button>
  </div>
</div>

<script>
let step = 1;

function nextQuestion() {
    let question = document.getElementById("question");
    let answers = document.getElementById("answers");

    if (step === 1) {
        question.innerText = "Question 2: How does Aamir treat people he cares about?";
        answers.innerHTML =
            '<button onclick="nextQuestion()">With respect and love</button>' +
            '<button onclick="nextQuestion()">With anger</button>';
        step++;
    }
    else if (step === 2) {
        question.innerText = "Question 3: What kind of heart does Aamir have?";
        answers.innerHTML =
            '<button onclick="nextQuestion()">A pure and honest heart</button>' +
            '<button onclick="nextQuestion()">A selfish heart</button>';
        step++;
    }
    else if (step === 3) {
        question.innerText = "Question 4: What kind of love does Aamir believe in?";
        answers.innerHTML =
            '<button onclick="nextQuestion()">💍 A lifetime love with loyalty and respect</button>' +
            '<button onclick="nextQuestion()">🎭 Just time-pass with no real feelings</button>';
        step++;
    }
    else {
        document.getElementById("card").innerHTML =
        '<h2>My Heart\'s Message 💗</h2>' +
        '<p>' +
        'I don\'t know what is happening to me and to my heart.<br>' +
        'I feel restless without you and I am not at peace until I talk to you.<br><br>' +
        'I think I am starting to fall in love with you.<br><br>' +
        'If you want, would you like to be in a relationship with me?<br>' +
        'Will you accept my proposal or reject it?' +
        '</p>' +
        '<h3>❤️ Yes or No ❤️</h3>' +
        '<button onclick="showPopup()">Yes</button>' +
        '<button onclick="sendNo()">No</button>' +
        '<div id="watermark">Made by Aamir Nisar</div>';
    }
}

function showPopup(){
    document.getElementById("popup").style.display = "flex";
}

function goWhatsApp(){
  window.location.href = "https://wa.me/917051932522?text=I%20accept%20your%20proposal%20Aamir.%20I%20want%20to%20be%20in%20a%20relationship%20with%20you.";
}

function sendNo(){
  window.location.href = "https://wa.me/917051932522?text=I%20am%20sorry%20Aamir,%20I%20cannot%20accept%20your%20proposal.";
}

// hearts animation
setInterval(function(){
    let heart = document.createElement("div");
    heart.className = "heart";
    heart.innerHTML = "❤️";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = (15 + Math.random() * 25) + "px";
    document.body.appendChild(heart);
    setTimeout(function(){ heart.remove(); }, 6000);
}, 400);
</script>

</body>
</html>
