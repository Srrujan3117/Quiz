<!DOCTYPE html>
<html>
<head>
<title>IKS MCQ Quiz</title>
<style>
body{
    font-family: Arial, sans-serif;
    background:#f2f4f8;
    padding:20px;
}
.container{
    background:white;
    padding:20px;
    border-radius:10px;
    box-shadow:0 0 10px rgba(0,0,0,0.1);
}
.question{
    margin-bottom:15px;
    padding:10px;
    border-radius:6px;
}
.correct{
    background:#d4edda;
}
.wrong{
    background:#f8d7da;
}
button{
    padding:10px 20px;
    background:#4285F4;
    color:white;
    border:none;
    border-radius:5px;
    cursor:pointer;
}
button:hover{
    background:#3367d6;
}
#result{
    margin-top:20px;
    font-size:18px;
    font-weight:bold;
}
.answer{
    margin-top:5px;
    font-weight:bold;
}
</style>
</head>
<body>

<div class="container">
<h2>IKS Project - MCQ Quiz</h2>

<form id="quizForm"></form>

<button onclick="calculateScore()">Submit Quiz</button>

<div id="result"></div>

</div>

<script>

const questions = [
["IKS stands for?",["Indian Knowledge Society","Indian Knowledge System","International Knowledge System","Indian Kingdom Studies"],1],
["IKS is rooted in?",["Modern textbooks","Western philosophy","Vedas and Upanishads","Industrial revolution"],2],
["Knowledge in IKS is?",["Fragmented","Isolated","Interconnected","Commercial"],2],
["“सेतुबन्धं कारयेत्” is from?",["Manusmriti","Arthashastra","Rigveda","Bhagavad Gita"],1],
["Ancient farming followed?",["Market demand","Government orders","Seasons","Random methods"],2],
["Wooden ploughs pulled by?",["Horses","Oxen","Elephants","Camels"],1],
["Crop diversity reduces?",["Pollution","Biodiversity","Crop failure","Soil erosion"],2],
["Water was considered?",["Commercial","Sacred","Private","Limited"],1],
["Step-wells common in?",["Kerala","Gujarat & Rajasthan","Bihar","Punjab"],1],
["Rainwater harvesting prevents?",["Floods","Water scarcity","Dry rivers","Pollution"],1],
["Waste disposed?",["Near houses","Rivers","Far from settlement","Streets"],2],
["Indus Valley had?",["No drainage","Covered drains","Plastic system","Factories"],1],
["अपव्ययं न कुर्यात् means?",["Waste resources","Save water","Do not waste resources","Grow trees"],2],
["Sacred groves were?",["Commercial forests","Sacred ecosystems","Mining areas","Royal property"],1],
["Plants born?",["After humans","After animals","Before gods","After forests"],2],
["Cutting trees was?",["Good practice","Neutral","Sinful","Profitable"],2],
["Architecture guided by?",["Industrial design","Vastu Shastra","Random design","Political system"],1],
["Mud walls give?",["Decoration","Insulation","Weak structure","Pollution"],1],
["Iron Pillar famous for?",["Gold plating","Rust resistance","Music","Wood carving"],1],
["Hampi pillars produce?",["Light","Musical notes","Water","Heat"],1],
["Biodiversity linked to?",["Religion and culture","Mining","Pollution","Industry"],0],
["Sacred groves act as?",["Factories","Mini biosphere reserves","Roads","Markets"],1],
["Yoga derived from?",["Yajna","Yuj","Yukti","Yatra"],1],
["Skill in action refers to?",["Bhakti Yoga","Jnana Yoga","Karma Yoga","Hatha Yoga"],2],
["Brahmacharya means?",["Ignorance","Right use of energy","Wealth","Anger"],1],
["Upanishads shift from?",["Ritual to inquiry","Trade","Forest","Fire"],0],
["Monsoon decides?",["Festivals","Sowing and harvesting","Architecture","Waste disposal"],1],
["Ancient waste system followed?",["Dumping","Zero waste principle","Plastic use","Excess consumption"],1],
["Sacred groves preserve?",["Roads","Rare species","Metals","Buildings"],1],
["Goal of Yoga?",["Physical strength","Union of Atman & Brahman","Wealth creation","Political power"],1]
];

const form = document.getElementById("quizForm");

questions.forEach((q, index) => {
    const div = document.createElement("div");
    div.classList.add("question");
    div.id = "question"+index;

    let html = `<p>${index+1}. ${q[0]}</p>`;
    q[1].forEach((option, i) => {
        html += `<input type="radio" name="q${index}" value="${i}"> ${option}<br>`;
    });

    div.innerHTML = html;
    form.appendChild(div);
});

function calculateScore(){

    let score = 0;

    questions.forEach((q, index) => {

        const selected = document.querySelector(`input[name="q${index}"]:checked`);
        const questionDiv = document.getElementById("question"+index);

        // Remove previous result if resubmitted
        const oldAnswer = questionDiv.querySelector(".answer");
        if(oldAnswer) oldAnswer.remove();

        let correctText = q[1][q[2]];

        if(selected){
            if(parseInt(selected.value) === q[2]){
                score++;
                questionDiv.classList.add("correct");
                questionDiv.classList.remove("wrong");
                questionDiv.innerHTML += `<div class="answer" style="color:green;">✔ Correct Answer: ${correctText}</div>`;
            } else {
                questionDiv.classList.add("wrong");
                questionDiv.classList.remove("correct");
                questionDiv.innerHTML += `<div class="answer" style="color:green;">Correct Answer: ${correctText}</div>`;
            }
        } else {
            questionDiv.classList.add("wrong");
            questionDiv.classList.remove("correct");
            questionDiv.innerHTML += `<div class="answer" style="color:green;">Correct Answer: ${correctText}</div>`;
        }

    });

    document.getElementById("result").innerHTML =
        `Final Score: ${score} / 30`;

}

</script>

</body>
</html>
