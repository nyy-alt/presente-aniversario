<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BIRTHDAY_PROTOCOL</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800&family=Share+Tech+Mono&display=swap" rel="stylesheet">

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
}

body{
  background:
    linear-gradient(rgba(255,255,255,.025) 1px,transparent 1px),
    linear-gradient(90deg,rgba(255,255,255,.025) 1px,transparent 1px),
    #070707;
  background-size:30px 30px;
  color:#eee;
  font-family:'Share Tech Mono',monospace;
  min-height:100vh;
  overflow-x:hidden;
}

body::before{
  content:"";
  position:fixed;
  inset:0;
  pointer-events:none;
  background:repeating-linear-gradient(
    to bottom,
    transparent 0px,
    transparent 3px,
    rgba(255,255,255,.025) 4px
  );
  z-index:100;
}

.hidden{
  display:none !important;
}

.container{
  width:min(900px,92%);
  margin:auto;
}

.screen{
  min-height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:30px 0;
}

.panel{
  background:linear-gradient(145deg,#191919,#090909);
  border:1px solid #8d8d8d;
  box-shadow:
    0 0 0 1px #252525,
    0 15px 50px rgba(0,0,0,.8),
    inset 0 0 25px rgba(255,255,255,.025);
  padding:30px;
  position:relative;
}

.panel::before{
  content:"";
  position:absolute;
  top:0;
  left:0;
  width:100%;
  height:3px;
  background:linear-gradient(90deg,#555,#fff,#555);
}

.label{
  color:#888;
  font-size:11px;
  letter-spacing:3px;
  margin-bottom:12px;
}

h1,h2,h3{
  font-family:'Orbitron',sans-serif;
}

h1{
  font-size:clamp(32px,8vw,72px);
  background:linear-gradient(#fff,#777,#fff);
  -webkit-background-clip:text;
  color:transparent;
  text-align:center;
}

.subtitle{
  text-align:center;
  color:#aaa;
  margin:18px 0 28px;
  line-height:1.7;
}

.chrome-button{
  display:block;
  width:100%;
  border:1px solid #aaa;
  background:linear-gradient(#eeeeee,#777,#dedede);
  color:#090909;
  font-family:'Orbitron',sans-serif;
  font-weight:700;
  letter-spacing:2px;
  padding:15px;
  cursor:pointer;
  transition:.2s;
}

.chrome-button:hover{
  transform:translateY(-2px);
  filter:brightness(1.15);
}

.topbar{
  display:flex;
  justify-content:space-between;
  align-items:center;
  border-bottom:1px solid #444;
  padding-bottom:15px;
  margin-bottom:25px;
  font-size:11px;
  color:#888;
}

.protocol{
  color:#ddd;
}

/* QUIZ */

.quiz-box{
  max-width:760px;
  margin:auto;
}

.progress{
  height:5px;
  background:#222;
  margin:20px 0 35px;
  border:1px solid #444;
}

.progress-fill{
  height:100%;
  width:33%;
  background:linear-gradient(90deg,#777,#fff,#777);
  transition:.3s;
}

.question-number{
  color:#777;
  letter-spacing:3px;
  font-size:12px;
  margin-bottom:15px;
}

.question{
  font-family:'Orbitron',sans-serif;
  font-size:clamp(20px,4vw,30px);
  line-height:1.4;
  margin-bottom:25px;
}

.answers{
  display:grid;
  gap:12px;
}

.answer{
  padding:16px;
  background:#111;
  border:1px solid #555;
  color:#ddd;
  text-align:left;
  font-family:'Share Tech Mono',monospace;
  cursor:pointer;
  transition:.2s;
}

.answer:hover{
  background:linear-gradient(90deg,#222,#444,#222);
  border-color:#aaa;
}

.answer.correct{
  border-color:#ddd;
  background:#303030;
}

.answer.wrong{
  border-color:#666;
  background:#171717;
}

.feedback{
  min-height:30px;
  margin-top:18px;
  color:#aaa;
  line-height:1.5;
}

.error{
  margin-top:25px;
  padding:25px;
  border:1px solid #777;
  background:#0c0c0c;
  text-align:center;
}

.error-code{
  font-family:'Orbitron',sans-serif;
  font-size:35px;
  margin-bottom:15px;
}

.error-text{
  color:#aaa;
  line-height:1.7;
}

/* MAZE */

.maze-wrapper{
  max-width:600px;
  margin:auto;
  text-align:center;
}

.maze-title{
  font-family:'Orbitron',sans-serif;
  font-size:28px;
  margin-bottom:8px;
}

.maze-subtitle{
  color:#777;
  margin-bottom:25px;
}

.maze{
  width:min(90vw,450px);
  aspect-ratio:1;
  margin:0 auto 25px;
  display:grid;
  grid-template-columns:repeat(9,1fr);
  border:2px solid #777;
  background:#111;
}

.cell{
  border:1px solid #222;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:8px;
  text-align:center;
}

.wall{
  background:linear-gradient(135deg,#292929,#090909);
}

.path{
  background:#111;
}

.player{
  background:linear-gradient(135deg,#fff,#888);
  color:#000;
  font-size:10px;
  font-weight:bold;
}

.goal{
  background:linear-gradient(135deg,#777,#eee,#555);
  color:#000;
  font-size:8px;
  font-weight:bold;
}

.controls{
  display:grid;
  grid-template-columns:repeat(3,60px);
  justify-content:center;
  gap:7px;
}

.controls button{
  height:50px;
  background:#151515;
  color:#ddd;
  border:1px solid #555;
  font-size:20px;
  cursor:pointer;
}

.controls button:hover{
  background:#333;
}

/* DANCE */

.reward{
  text-align:center;
  max-width:700px;
  margin:auto;
}

.reward-title{
  font-family:'Orbitron',sans-serif;
  font-size:clamp(25px,6vw,45px);
  background:linear-gradient(#fff,#777,#fff);
  -webkit-background-clip:text;
  color:transparent;
}

.dance-stage{
  height:220px;
  margin:30px auto;
  border:1px solid #444;
  background:
    linear-gradient(#151515,#080808);
  display:flex;
  justify-content:center;
  align-items:end;
  gap:20px;
  overflow:hidden;
}

.dancer{
  width:35px;
  height:100px;
  background:linear-gradient(#eee,#777,#eee);
  border-radius:20px 20px 8px 8px;
  position:relative;
  animation:dance .65s infinite alternate ease-in-out;
}

.dancer::before{
  content:"";
  position:absolute;
  width:35px;
  height:35px;
  border-radius:50%;
  background:#ccc;
  top:-38px;
  left:0;
}

.dancer:nth-child(2){
  animation-delay:.15s;
}

.dancer:nth-child(3){
  animation-delay:.3s;
}

.dancer:nth-child(4){
  animation-delay:.45s;
}

@keyframes dance{
  from{
    transform:rotate(-8deg) translateY(8px);
  }
  to{
    transform:rotate(8deg) translateY(-18px);
  }
}

.unlock{
  margin-top:20px;
  padding:15px;
  border:1px solid #777;
  color:#ccc;
}

/* FINAL CONTENT */

.section{
  margin-bottom:35px;
}

.section-title{
  font-size:24px;
  margin-bottom:20px;
  color:#ddd;
}

.message{
  white-space:pre-line;
  color:#ccc;
  line-height:1.9;
  font-size:15px;
}

.database{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:15px;
}

.card{
  padding:20px;
  border:1px solid #444;
  background:linear-gradient(145deg,#171717,#090909);
}

.card-label{
  color:#777;
  font-size:10px;
  letter-spacing:2px;
  margin-bottom:12px;
}

.card-value{
  font-family:'Orbitron',sans-serif;
  color:#eee;
  line-height:1.5;
}

.final{
  text-align:center;
  padding:45px 20px;
}

.final h2{
  font-size:clamp(25px,6vw,50px);
}

.final p{
  color:#888;
  margin-top:15px;
}

@media(max-width:600px){
  .panel{
    padding:20px;
  }

  .database{
    grid-template-columns:1fr;
  }

  .dance-stage{
    gap:10px;
  }

  .dancer{
    width:28px;
  }

  .dancer::before{
    width:28px;
    height:28px;
  }
}
</style>
</head>

<body>

<!-- =========================
     1. QUIZ / INÍCIO
========================= -->

<section id="quizScreen" class="screen">
  <div class="container">
    <div class="panel quiz-box">

      <div class="topbar">
        <span>SYSTEM // BIRTHDAY_PROTOCOL</span>
        <span>STATUS: LOCKED</span>
      </div>

      <div class="label">SECURITY CHECK</div>

      <h1>ACCESS</h1>

      <p class="subtitle">
        Complete todas as verificações para acessar<br>
        o presente virtual.
      </p>

      <div class="progress">
        <div id="progressFill" class="progress-fill"></div>
      </div>

      <div id="quizContent"></div>

    </div>
  </div>
</section>


<!-- =========================
     2. LABIRINTO
========================= -->

<section id="mazeScreen" class="screen hidden">
  <div class="container">

    <div class="panel maze-wrapper">

      <div class="topbar">
        <span>MAZE.EXE</span>
        <span>ACCESS: GRANTED</span>
      </div>

      <div class="maze-title">ENCONTRE SEU PRESENTE</div>

      <div class="maze-subtitle">
        Leve <b>VOCÊ</b> até <b>SEU PRESENTE</b>.
      </div>

      <div id="maze" class="maze"></div>

      <div class="controls">
        <div></div>
        <button onclick="movePlayer(0,-1)">↑</button>
        <div></div>

        <button onclick="movePlayer(-1,0)">←</button>
        <button onclick="movePlayer(1,0)">↓</button>
        <button onclick="movePlayer(0,1)">→</button>
      </div>

    </div>

  </div>
</section>


<!-- =========================
     3. RECOMPENSA
========================= -->

<section id="rewardScreen" class="screen hidden">
  <div class="container">

    <div class="panel reward">

      <div class="label">SYSTEM MESSAGE</div>

      <div class="reward-title">
        PRESENTE<br>DESBLOQUEADO!
      </div>

      <div class="dance-stage">
        <div class="dancer"></div>
        <div class="dancer"></div>
        <div class="dancer"></div>
        <div class="dancer"></div>
      </div>

      <div class="unlock">
        ✓ MAZE COMPLETE<br>
        ✓ ACCESS GRANTED<br>
        ✓ BIRTHDAY PROTOCOL COMPLETE
      </div>

      <br>

      <button class="chrome-button" onclick="openGift()">
        ABRIR O PRESENTE
      </button>

    </div>

  </div>
</section>


<!-- =========================
     4. CONTEÚDO DO PRESENTE
========================= -->

<main id="giftScreen" class="hidden">

  <div class="container" style="padding:40px 0;">

    <!-- MENSAGEM -->

    <section class="section panel">

      <div class="topbar">
        <span>MESSAGE.EXE</span>
        <span>FILE: BIRTHDAY.txt</span>
      </div>

      <div class="label">PERSONAL MESSAGE</div>

      <h2 class="section-title">
        FELIZ ANIVERSÁRIOOO! 🩶
      </h2>

      <div class="message">
Demorou 2 semanas pra eu conseguir fazer esse site, tem muito código 😭 Mas eu consegui!
Bom, eu achei que um texto no whatsapp apenas seria muito simples, quis criar algo que fosse mais especial ❤️ Dediquei meu tempo a video aulas no YT e pedi ajuda pro Chat GPT pra fazer ele super bonitinho, então eu espero que tenha dado certo!! Sem mais enrolação, vamos ao presente virtual kdkdkkd


Eu quero primeiramente te agradecer por ter sido a pessoa que mais me apoiou por todos esses anos 🫶🏼 crescer com vc foi o melhor presente da minha vida, porque eu pude contar com vc sempre, contar tudo que acontece comigo, pedir ajuda com roupas, cabelo (inclusive vc que me ensinou a fazer o cabelo), aprendi a lidar com pessoas, conheci k-pop por vc também, aprendi a ter gostos próprios e etc... Você, diferente de qualquer outro familiar, foi uma das pessoas mais presentes na minha vida, e eu agradeço muito a Deus por isso... Pensando agora, eu não sei o que seria da minha vida sem vc, acho que eu seria uma feia, lascada, sem saber arrumar o cabelo e sem personalidade própria kskskskksksksk😭🫶🏼

Também quero te desejar um ótimo aniversário 🎂, que vc possa ter o melhor aniversário da sua vida, ganhar seu tablet, o melhor bolo e se melhores fotos!!! Vou te obrigar a se arrumar pra tirar fotos aesthetics ok? Vc agora está no auge da idade, idade de diva, então vc vai conquistsr tudo o que vc sonhava em ter 😌
      </div>

    </section>


    <!-- DATABASE -->

    <section class="section panel">

      <div class="topbar">
        <span>PERSONAL_DATABASE</span>
        <span>FILE: SISTER.dat</span>
      </div>

      <div class="label">PROFILE INFORMATION</div>

      <h2 class="section-title">
        DADOS DA ANIVERSARIANTE
      </h2>

      <div class="database">

        <div class="card">
          <div class="card-label">
            MÚSICA QUE ME LEMBRA VOCÊ
          </div>
          <div class="card-value">
            Nasa — ATEEZ
          </div>
        </div>

        <div class="card">
          <div class="card-label">
            UMA COISA QUE VOCÊ AMA
          </div>
          <div class="card-value">
            Eu, claro 😌
          </div>
        </div>

        <div class="card">
          <div class="card-label">
            UMA MEMÓRIA NOSSA
          </div>
          <div class="card-value">
            A época do BTS que a gente dançava Fire KSKSKSKKDKD
          </div>
        </div>

        <div class="card">
          <div class="card-label">
            UMA COISA QUE COMBINA COM VOCÊ
          </div>
          <div class="card-value">
            Cyber
          </div>
        </div>

      </div>

    </section>


    <!-- FINAL -->

    <section class="section panel final">

      <div class="label">SYSTEM // COMPLETE</div>

      <h2>
        FELIZ ANIVERSÁRIO,<br>
        DIVA. 🩶
      </h2>

      <p>
        birthday_protocol.exe foi concluído com sucesso.
      </p>

    </section>

  </div>

</main>


<script>

/* =========================
   QUIZ
========================= */

const questions = [

  {
    question:
    "Qual música a gente ficava dançando na TV da sala e a mãe aparecia do lado e a gente fingia que nada tava acontecendo?",

    answers:[
      "Nasa — ATEEZ",
      "Fire — BTS",
      "Way Back — ENHYPEN"
    ],

    correct:1
  },

  {
    question:
    "Qual destas vibes combina mais com vc?",

    answers:[
      "Rosa pastel",
      "Cyber",
      "Cottagecore"
    ],

    correct:1
  },

  {
    question:
    "Quem é a pessoa que está desbloqueando este sistema?",

    answers:[
      "A aniversariante",
      "Não sou a aniversariante"
    ],

    correct:0
  }

];

let currentQuestion = 0;

const quizContent = document.getElementById("quizContent");
const progressFill = document.getElementById("progressFill");

function showQuestion(){

  const q = questions[currentQuestion];

  progressFill.style.width =
    ((currentQuestion + 1) / questions.length * 100) + "%";

  quizContent.innerHTML = `

    <div class="question-number">
      QUESTION ${currentQuestion + 1} / ${questions.length}
    </div>

    <div class="question">
      ${q.question}
    </div>

    <div class="answers">

      ${q.answers.map((answer,index)=>`

        <button
          class="answer"
          onclick="answerQuestion(${index})">
          ${answer}
        </button>

      `).join("")}

    </div>

    <div id="feedback" class="feedback"></div>
  `;
}

function answerQuestion(index){

  const q = questions[currentQuestion];
  const buttons = document.querySelectorAll(".answer");
  const feedback = document.getElementById("feedback");

  if(index === q.correct){

    buttons[index].classList.add("correct");

    if(currentQuestion === 2){

      feedback.innerHTML =
        "✓ ACESSO LIBERADO";

      setTimeout(()=>{
        document.getElementById("quizScreen")
          .classList.add("hidden");

        document.getElementById("mazeScreen")
          .classList.remove("hidden");

        drawMaze();

      },1000);

      return;
    }

    feedback.innerHTML = "✓ RESPOSTA CORRETA";

    setTimeout(()=>{
      currentQuestion++;
      showQuestion();
    },700);

  }else{

    buttons[index].classList.add("wrong");

    if(currentQuestion === 2){

      quizContent.innerHTML = `

        <div class="error">

          <div class="error-code">
            ERROR 403
          </div>

          <div class="error-text">
            SEU ACESSO FOI NEGADO.<br><br>
            VOCÊ NÃO É O DESTINATÁRIO DO PRESENTE.<br><br>
            RETIRE-SE IMEDIATAMENTE.
          </div>

          <br>

          <button
            class="chrome-button"
            onclick="retryQuiz()">
            TENTAR NOVAMENTE
          </button>

        </div>

      `;

      return;
    }

    feedback.innerHTML =
      "✕ RESPOSTA INCORRETA. TENTE NOVAMENTE.";
  }
}

function retryQuiz(){

  currentQuestion = 2;
  showQuestion();

}

showQuestion();


/* =========================
   LABIRINTO
========================= */

const mazeMap = [

  "111111111",
  "100000001",
  "101111101",
  "101000101",
  "101011101",
  "101010001",
  "101011101",
  "100000001",
  "111111111"

];

let player = {
  row:1,
  col:1
};

const goal = {
  row:7,
  col:7
};

function drawMaze(){

  const maze = document.getElementById("maze");

  maze.innerHTML = "";

  for(let row=0; row<9; row++){

    for(let col=0; col<9; col++){

      const cell =
        document.createElement("div");

      cell.classList.add("cell");

      if(mazeMap[row][col] === "1"){

        cell.classList.add("wall");

      }else{

        cell.classList.add("path");

      }

      if(
        row === player.row &&
        col === player.col
      ){

        cell.classList.add("player");
        cell.innerText = "VOCÊ";

      }

      if(
        row === goal.row &&
        col === goal.col
      ){

        cell.classList.add("goal");
        cell.innerText = "SEU\nPRESENTE";

      }

      maze.appendChild(cell);
    }
  }
}

function movePlayer(rowMove,colMove){

  const newRow =
    player.row + rowMove;

  const newCol =
    player.col + colMove;

  if(
    newRow < 0 ||
    newRow >= 9 ||
    newCol < 0 ||
    newCol >= 9
  ){
    return;
  }

  if(
    mazeMap[newRow][newCol] === "1"
  ){
    return;
  }

  player.row = newRow;
  player.col = newCol;

  drawMaze();

  if(
    player.row === goal.row &&
    player.col === goal.col
  ){

    setTimeout(()=>{
      document.getElementById("mazeScreen")
        .classList.add("hidden");

      document.getElementById("rewardScreen")
        .classList.remove("hidden");
    },500);

  }
}


/* =========================
   TECLADO
========================= */

document.addEventListener("keydown",(event)=>{

  if(
    document.getElementById("mazeScreen")
      .classList.contains("hidden")
  ){
    return;
  }

  if(event.key === "ArrowUp" || event.key === "w"){
    movePlayer(-1,0);
  }

  if(event.key === "ArrowDown" || event.key === "s"){
    movePlayer(1,0);
  }

  if(event.key === "ArrowLeft" || event.key === "a"){
    movePlayer(0,-1);
  }

  if(event.key === "ArrowRight" || event.key === "d"){
    movePlayer(0,1);
  }

});


/* =========================
   ABRIR PRESENTE
========================= */

function openGift(){

  document.getElementById("rewardScreen")
    .classList.add("hidden");

  document.getElementById("giftScreen")
    .classList.remove("hidden");

  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}

</script>

</body>
</html>
