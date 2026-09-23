<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>birthday_protocol.exe</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800&family=Share+Tech+Mono&display=swap" rel="stylesheet">

<style>

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  background:
    linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px),
    #050505;
  background-size: 30px 30px;
  color: #ddd;
  font-family: "Share Tech Mono", monospace;
  min-height: 100vh;
  overflow-x: hidden;
}

body::before {
  content: "";
  position: fixed;
  inset: 0;
  pointer-events: none;
  background: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 3px,
    rgba(255,255,255,0.025) 4px
  );
}

.hidden {
  display: none !important;
}

.screen {
  min-height: 100vh;
  padding: 35px 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.panel {
  width: 100%;
  max-width: 700px;
  border: 1px solid #777;
  padding: 28px;
  background: linear-gradient(145deg, #151515, #050505);
  box-shadow:
    0 0 25px rgba(255,255,255,0.05),
    inset 0 0 30px rgba(255,255,255,0.025);
}

.system {
  font-size: 11px;
  color: #888;
  letter-spacing: 2px;
  margin-bottom: 20px;
}

h1 {
  font-family: "Orbitron", sans-serif;
  font-size: clamp(25px, 7vw, 48px);
  letter-spacing: 3px;
  margin: 0 0 15px;
  background: linear-gradient(#fff, #777);
  -webkit-background-clip: text;
  color: transparent;
}

h2 {
  font-family: "Orbitron", sans-serif;
  font-size: 20px;
  letter-spacing: 2px;
}

p {
  line-height: 1.7;
  color: #bbb;
}

button {
  font-family: "Share Tech Mono", monospace;
  border: 1px solid #999;
  background: linear-gradient(145deg, #eee, #777);
  color: #050505;
  padding: 12px 18px;
  cursor: pointer;
  text-transform: uppercase;
  letter-spacing: 1px;
  transition: 0.2s;
}

button:hover {
  filter: brightness(1.25);
  transform: translateY(-1px);
}

.music-option {
  display: block;
  width: 100%;
  margin: 10px 0;
  text-align: left;
  background: linear-gradient(145deg, #202020, #090909);
  color: #ddd;
  border: 1px solid #555;
}

.music-option.selected {
  border-color: #fff;
  box-shadow: 0 0 15px rgba(255,255,255,0.15);
}

.now-playing {
  margin-top: 20px;
  padding: 15px;
  border: 1px solid #555;
  background: #0b0b0b;
}

.now-playing span {
  color: white;
}

.controls {
  margin-top: 12px;
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.controls button {
  font-size: 10px;
  padding: 7px 10px;
}

/* BOTÃO PEQUENININHO */

.tiny-next {
  display: block;
  margin: 15px auto 0;
  padding: 5px 10px;
  font-size: 9px;
  letter-spacing: 1px;
  background: linear-gradient(145deg, #ddd, #777);
  color: #050505;
  border: 1px solid #888;
}

/* QUIZ */

.question {
  margin: 25px 0;
}

.answer {
  display: block;
  width: 100%;
  margin: 8px 0;
  background: #111;
  color: #ccc;
  border: 1px solid #555;
  text-align: left;
}

.answer:hover {
  border-color: #aaa;
}

.error {
  margin-top: 15px;
  padding: 15px;
  border: 1px solid #777;
  color: #ddd;
  background: #111;
}

.success {
  margin-top: 15px;
  padding: 15px;
  border: 1px solid #aaa;
  background: #111;
}

/* MAZE */

.maze-wrapper {
  text-align: center;
}

.maze {
  display: grid;
  grid-template-columns: repeat(9, 28px);
  grid-template-rows: repeat(9, 28px);
  gap: 2px;
  justify-content: center;
  margin: 25px auto;
}

.cell {
  width: 28px;
  height: 28px;
  border: 1px solid #333;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 8px;
}

.wall {
  background: #ddd;
}

.path {
  background: #090909;
}

.player {
  background: #aaa;
  color: #000;
  font-size: 8px;
  font-weight: bold;
}

.goal {
  background: linear-gradient(145deg, #fff, #777);
  color: #000;
  font-size: 7px;
  font-weight: bold;
}

.controls-maze {
  display: grid;
  grid-template-columns: repeat(3, 45px);
  justify-content: center;
  gap: 5px;
  margin-top: 15px;
}

.controls-maze button {
  padding: 10px;
  font-size: 15px;
}

.up {
  grid-column: 2;
}

.left {
  grid-column: 1;
}

.down {
  grid-column: 2;
}

.right {
  grid-column: 3;
}

/* REWARD */

.reward {
  text-align: center;
}

.dancers {
  display: flex;
  justify-content: center;
  align-items: end;
  gap: 25px;
  height: 180px;
  margin: 25px 0;
}

.dancer {
  width: 35px;
  height: 100px;
  background: linear-gradient(90deg, #555, #eee, #666);
  border-radius: 20px 20px 5px 5px;
  position: relative;
  animation: dance 0.8s infinite alternate ease-in-out;
}

.dancer:nth-child(2) {
  animation-delay: 0.15s;
}

.dancer:nth-child(3) {
  animation-delay: 0.3s;
}

.dancer:nth-child(4) {
  animation-delay: 0.45s;
}

.dancer::before {
  content: "";
  position: absolute;
  width: 35px;
  height: 35px;
  border-radius: 50%;
  background: #ddd;
  top: -30px;
  left: 0;
}

@keyframes dance {
  from {
    transform: rotate(-8deg) translateY(5px);
  }

  to {
    transform: rotate(8deg) translateY(-10px);
  }
}

.access {
  margin: 20px 0;
  line-height: 2;
  color: #aaa;
}

/* MENSAGEM */

.message {
  white-space: pre-line;
  border-left: 2px solid #777;
  padding-left: 18px;
  margin-top: 20px;
}

/* DATABASE */

.database {
  margin-top: 30px;
}

.card {
  border: 1px solid #555;
  padding: 18px;
  margin: 12px 0;
  background: linear-gradient(145deg, #111, #070707);
}

.card-title {
  font-size: 10px;
  color: #888;
  letter-spacing: 2px;
  margin-bottom: 8px;
}

.card-content {
  color: #eee;
  font-size: 16px;
}

.final {
  text-align: center;
  margin-top: 45px;
  padding-top: 30px;
  border-top: 1px solid #444;
}

@media (max-width: 500px) {

  .panel {
    padding: 20px;
  }

  .maze {
    grid-template-columns: repeat(9, 25px);
    grid-template-rows: repeat(9, 25px);
  }

  .cell {
    width: 25px;
    height: 25px;
  }

  .dancers {
    gap: 15px;
  }

}

</style>
</head>

<body>


<!-- ========================= -->
<!-- PÁGINA 1 - MÚSICA -->
<!-- ========================= -->

<section id="musicScreen" class="screen">

  <div class="panel">

    <div class="system">
      SYSTEM // BIRTHDAY_PROTOCOL
    </div>

    <h1>ESCOLHA</h1>

    <p>
      escolha uma música para começar
    </p>

    <button
      class="music-option"
      onclick="selectMusic('NASA — ENHYPEN', 'music/nasa.mp3', this)">
      NASA — ENHYPEN
    </button>

    <button
      class="music-option"
      onclick="selectMusic('NO WAY BACK — ENHYPEN', 'music/no-way-back.mp3', this)">
      NO WAY BACK — ENHYPEN
    </button>

    <button
      class="music-option"
      onclick="selectMusic('ICONIC BY MISTAKE — KATSEYE', 'music/iconic-by-mistake.mp3', this)">
      ICONIC BY MISTAKE — KATSEYE
    </button>


    <div id="nowPlaying" class="now-playing hidden">

      <div>
        NOW PLAYING:
        <span id="songName"></span>
      </div>

      <div class="controls">

        <button onclick="toggleMusic()">
          PLAY / PAUSE
        </button>

        <button onclick="restartMusic()">
          RESTART
        </button>

      </div>

    </div>


    <!-- BOTÃO NOVO -->

    <button
      id="continueButton"
      class="tiny-next hidden"
      onclick="nextPage()">
      próxima página →
    </button>


  </div>

</section>



<!-- ========================= -->
<!-- PÁGINA 2 - QUIZ -->
<!-- ========================= -->

<section id="quizScreen" class="screen hidden">

  <div class="panel">

    <div class="system">
      SYSTEM // SECURITY_CHECK
    </div>

    <h1>QUIZ</h1>


    <div class="question">

      <h2>01 // MEMÓRIA</h2>

      <p>
        Qual música a gente ficava dançando na TV da sala e a mãe aparecia do lado e a gente fingia que nada tava acontecendo?
      </p>

      <button class="answer" onclick="answerQ1(false)">
        Nasa — ATEEZ
      </button>

      <button class="answer" onclick="answerQ1(true)">
        Fire — BTS
      </button>

      <button class="answer" onclick="answerQ1(false)">
        Way Back — ENHYPEN
      </button>

    </div>


    <div id="q1Result"></div>


    <div id="question2" class="question hidden">

      <h2>02 // VIBE</h2>

      <p>
        Qual destas vibes combina mais com vc?
      </p>

      <button class="answer" onclick="answerQ2(false)">
        Rosa pastel
      </button>

      <button class="answer" onclick="answerQ2(true)">
        Cyber
      </button>

      <button class="answer" onclick="answerQ2(false)">
        Cottagecore
      </button>

    </div>


    <div id="q2Result"></div>


    <div id="question3" class="question hidden">

      <h2>03 // IDENTIDADE</h2>

      <p>
        Quem é a pessoa que está desbloqueando este sistema?
      </p>

      <button class="answer" onclick="answerQ3(true)">
        A aniversariante
      </button>

      <button class="answer" onclick="answerQ3(false)">
        Não sou a aniversariante
      </button>

    </div>


    <div id="q3Result"></div>


    <button
      id="retryButton"
      class="hidden"
      onclick="retryQ3()">
      TENTAR NOVAMENTE
    </button>


  </div>

</section>



<!-- ========================= -->
<!-- PÁGINA 3 - MAZE -->
<!-- ========================= -->

<section id="mazeScreen" class="screen hidden">

  <div class="panel maze-wrapper">

    <div class="system">
      SYSTEM // MAZE_PROTOCOL
    </div>

    <h1>MAZE</h1>

    <p>
      encontre o caminho até o seu presente.
    </p>

    <div id="maze" class="maze"></div>

    <div class="controls-maze">

      <button class="up" onclick="movePlayer(-1,0)">
        ↑
      </button>

      <button class="left" onclick="movePlayer(0,-1)">
        ←
      </button>

      <button class="down" onclick="movePlayer(1,0)">
        ↓
      </button>

      <button class="right" onclick="movePlayer(0,1)">
        →
      </button>

    </div>

  </div>

</section>



<!-- ========================= -->
<!-- PÁGINA 4 - PRESENTE -->
<!-- ========================= -->

<section id="rewardScreen" class="screen hidden">

  <div class="panel reward">

    <div class="system">
      SYSTEM // ACCESS_GRANTED
    </div>

    <h1>
      PRESENTE<br>
      DESBLOQUEADO!
    </h1>


    <div class="dancers">

      <div class="dancer"></div>
      <div class="dancer"></div>
      <div class="dancer"></div>
      <div class="dancer"></div>

    </div>


    <div class="access">

      ✓ MAZE COMPLETE<br>
      ✓ ACCESS GRANTED<br>
      ✓ BIRTHDAY PROTOCOL COMPLETE

    </div>


    <button onclick="openPresent()">
      ABRIR O PRESENTE
    </button>

  </div>

</section>



<!-- ========================= -->
<!-- PÁGINA 5 - FINAL -->
<!-- ========================= -->

<section id="finalScreen" class="screen hidden">

  <div class="panel">

    <div class="system">
      MESSAGE.EXE
    </div>

    <h1>
      FELIZ<br>
      ANIVERSÁRIO
    </h1>


    <div class="message">

Feliz aniversárioooo! 
Demorou 2 semanas pra eu conseguir fazer esse site, tem muito código 😭 Mas eu consegui!
Bom, eu achei que um texto no whatsapp apenas seria muito simples, quis criar algo que fosse mais especial ❤️ Dediquei meu tempo a video aulas no YT e pedi ajuda pro Chat GPT pra fazer ele super bonitinho, então eu espero que tenha dado certo!! Sem mais enrolação, vamos ao presente virtual kdkdkkd


Eu quero primeiramente te agradecer por ter sido a pessoa que mais me apoiou por todos esses anos 🫶🏼 crescer com vc foi o melhor presente da minha vida, porque eu pude contar com vc sempre, contar tudo que acontece comigo, pedir ajuda com roupas, cabelo (inclusive vc que me ensinou a fazer o cabelo), aprendi a lidar com pessoas, conheci k-pop por vc também, aprendi a ter gostos próprios e etc... Você, diferente de qualquer outro familiar, foi uma das pessoas mais presentes na minha vida, e eu agradeço muito a Deus por isso... Pensando agora, eu não sei o que seria da minha vida sem vc, acho que eu seria uma feia, lascada, sem saber arrumar o cabelo e sem personalidade própria kskskskksksksk😭🫶🏼

Também quero te desejar um ótimo aniversário 🎂, que vc possa ter o melhor aniversário da sua vida, ganhar seu tablet, o melhor bolo e se melhores fotos!!! Vou te obrigar a se arrumar pra tirar fotos aesthetics ok? Vc agora está no auge da idade, idade de diva, então vc vai conquistsr tudo o que vc sonhava em ter 😌

    </div>



    <div class="database">

      <div class="system">
        PERSONAL_DATABASE
      </div>


      <div class="card">

        <div class="card-title">
          MÚSICA QUE ME LEMBRA VOCÊ
        </div>

        <div class="card-content">
          Nasa — ATEEZ
        </div>

      </div>


      <div class="card">

        <div class="card-title">
          UMA COISA QUE VOCÊ AMA
        </div>

        <div class="card-content">
          Eu, claro 😌
        </div>

      </div>


      <div class="card">

        <div class="card-title">
          UMA MEMÓRIA NOSSA
        </div>

        <div class="card-content">
          A época do BTS que a gente dançava Fire KSKSKSKKDKD
        </div>

      </div>


      <div class="card">

        <div class="card-title">
          UMA COISA QUE COMBINA COM VOCÊ
        </div>

        <div class="card-content">
          Cyber
        </div>

      </div>

    </div>



    <div class="final">

      <h2>
        FELIZ ANIVERSÁRIO, DIVA. 🩶
      </h2>

      <p>
        birthday_protocol.exe foi concluído com sucesso.
      </p>

    </div>


  </div>

</section>



<script>

/* ========================= */
/* MÚSICA */
/* ========================= */

let audio = null;
let selectedSong = "";


function selectMusic(name, file, button) {

  if (audio) {
    audio.pause();
    audio.currentTime = 0;
  }


  audio = new Audio(file);

  audio.loop = true;


  selectedSong = name;


  document.getElementById("songName").innerText = name;

  document
    .getElementById("nowPlaying")
    .classList.remove("hidden");


  document
    .getElementById("continueButton")
    .classList.remove("hidden");


  document
    .querySelectorAll(".music-option")
    .forEach(btn => btn.classList.remove("selected"));


  if (button) {
    button.classList.add("selected");
  }


  audio.play().catch(() => {

    console.log(
      "A música não conseguiu tocar. Verifique o nome e o formato do arquivo."
    );

  });

}


/* PLAY / PAUSE */

function toggleMusic() {

  if (!audio) return;


  if (audio.paused) {

    audio.play();

  } else {

    audio.pause();

  }

}


/* RESTART */

function restartMusic() {

  if (!audio) return;

  audio.currentTime = 0;

  audio.play();

}


/* PRÓXIMA PÁGINA */

function nextPage() {

  document
    .getElementById("musicScreen")
    .classList.add("hidden");


  document
    .getElementById("quizScreen")
    .classList.remove("hidden");

}


/* ========================= */
/* QUIZ */
/* ========================= */

function answerQ1(correct) {

  const result = document.getElementById("q1Result");


  if (correct) {

    result.innerHTML = `
      <div class="success">
        ✓ resposta correta.
      </div>
    `;


    document
      .getElementById("question2")
      .classList.remove("hidden");

  } else {

    result.innerHTML = `
      <div class="error">
        ✕ resposta incorreta.
        tente novamente.
      </div>
    `;

  }

}


function answerQ2(correct) {

  const result = document.getElementById("q2Result");


  if (correct) {

    result.innerHTML = `
      <div class="success">
        ✓ resposta correta.
      </div>
    `;


    document
      .getElementById("question3")
      .classList.remove("hidden");

  } else {

    result.innerHTML = `
      <div class="error">
        ✕ resposta incorreta.
        tente novamente.
      </div>
    `;

  }

}


function answerQ3(correct) {

  const result = document.getElementById("q3Result");


  if (correct) {

    result.innerHTML = `
      <div class="success">
        ✓ acesso liberado.
      </div>
    `;


    document
      .getElementById("retryButton")
      .classList.add("hidden");


    setTimeout(() => {

      document
        .getElementById("quizScreen")
        .classList.add("hidden");


      document
        .getElementById("mazeScreen")
        .classList.remove("hidden");


      createMaze();

    }, 800);


  } else {

    result.innerHTML = `
      <div class="error">
        error - seu acesso foi negado, vc não é o destinatário do presente, retire-se imediatamente
      </div>
    `;


    document
      .getElementById("retryButton")
      .classList.remove("hidden");

  }

}


function retryQ3() {

  document
    .getElementById("q3Result")
    .innerHTML = "";


  document
    .getElementById("retryButton")
    .classList.add("hidden");

}



/* ========================= */
/* MAZE */
/* ========================= */

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


let playerRow = 1;
let playerCol = 1;

const goalRow = 7;
const goalCol = 7;


function createMaze() {

  const maze = document.getElementById("maze");

  maze.innerHTML = "";


  for (let row = 0; row < 9; row++) {

    for (let col = 0; col < 9; col++) {

      const cell = document.createElement("div");

      cell.classList.add("cell");


      if (mazeMap[row][col] === "1") {

        cell.classList.add("wall");

      } else {

        cell.classList.add("path");

      }


      if (
        row === playerRow &&
        col === playerCol
      ) {

        cell.classList.add("player");
        cell.innerText = "VOCÊ";

      }


      if (
        row === goalRow &&
        col === goalCol
      ) {

        cell.classList.add("goal");
        cell.innerText = "PRESENTE";

      }


      maze.appendChild(cell);

    }

  }

}


function movePlayer(rowChange, colChange) {

  const newRow = playerRow + rowChange;
  const newCol = playerCol + colChange;


  if (
    newRow < 0 ||
    newRow >= 9 ||
    newCol < 0 ||
    newCol >= 9
  ) {

    return;

  }


  if (mazeMap[newRow][newCol] === "1") {

    return;

  }


  playerRow = newRow;
  playerCol = newCol;


  createMaze();


  if (
    playerRow === goalRow &&
    playerCol === goalCol
  ) {

    setTimeout(() => {

      document
        .getElementById("mazeScreen")
        .classList.add("hidden");


      document
        .getElementById("rewardScreen")
        .classList.remove("hidden");

    }, 400);

  }

}



/* TECLADO */

document.addEventListener("keydown", function(event) {

  if (
    document
      .getElementById("mazeScreen")
      .classList.contains("hidden")
  ) {

    return;

  }


  if (
    event.key === "ArrowUp" ||
    event.key.toLowerCase() === "w"
  ) {

    movePlayer(-1, 0);

  }


  if (
    event.key === "ArrowDown" ||
    event.key.toLowerCase() === "s"
  ) {

    movePlayer(1, 0);

  }


  if (
    event.key === "ArrowLeft" ||
    event.key.toLowerCase() === "a"
  ) {

    movePlayer(0, -1);

  }


  if (
    event.key === "ArrowRight" ||
    event.key.toLowerCase() === "d"
  ) {

    movePlayer(0, 1);

  }

});


/* ========================= */
/* PRESENTE */
/* ========================= */

function openPresent() {

  document
    .getElementById("rewardScreen")
    .classList.add("hidden");


  document
    .getElementById("finalScreen")
    .classList.remove("hidden");


  window.scrollTo({
    top: 0,
    behavior: "smooth"
  });

}

</script>

</body>
</html>
