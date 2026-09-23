<!DOCTYPE html>
<html lang="pt-BR">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>birthday_protocol.exe</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800&family=Share+Tech+Mono&display=swap" rel="stylesheet">

<style>

/* =========================
   CONFIGURAÇÕES GERAIS
========================= */

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;

  background:
    linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px),
    #050505;

  background-size: 30px 30px;

  color: #ddd;

  font-family: "Share Tech Mono", monospace;

  overflow-x: hidden;
}

/* efeito de tela */

body::before {
  content: "";
  position: fixed;
  inset: 0;

  pointer-events: none;

  background:
    repeating-linear-gradient(
      0deg,
      transparent,
      transparent 3px,
      rgba(255,255,255,0.025) 4px
    );
}

.hidden {
  display: none !important;
}


/* =========================
   TELAS
========================= */

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

  padding: 30px;

  border: 1px solid #666;

  background:
    linear-gradient(
      145deg,
      #171717,
      #050505
    );

  box-shadow:
    0 0 30px rgba(255,255,255,0.05),
    inset 0 0 35px rgba(255,255,255,0.025);
}


/* =========================
   TEXTOS
========================= */

.system {
  margin-bottom: 18px;

  color: #777;

  font-size: 10px;

  letter-spacing: 3px;
}

h1 {
  margin: 0 0 15px;

  font-family: "Orbitron", sans-serif;

  font-size: clamp(28px, 8vw, 52px);

  letter-spacing: 3px;

  background:
    linear-gradient(
      #ffffff,
      #777777
    );

  -webkit-background-clip: text;

  color: transparent;
}

h2 {
  font-family: "Orbitron", sans-serif;

  font-size: 18px;

  letter-spacing: 2px;
}

p {
  color: #aaa;

  line-height: 1.7;
}


/* =========================
   BOTÕES
========================= */

button {
  font-family: "Share Tech Mono", monospace;

  cursor: pointer;

  transition: 0.2s;
}

button:hover {
  transform: translateY(-2px);

  filter: brightness(1.2);
}


/* =========================
   MÚSICA
========================= */

.music-option {

  width: 100%;

  display: block;

  margin: 10px 0;

  padding: 15px;

  text-align: left;

  color: #ccc;

  background:
    linear-gradient(
      145deg,
      #191919,
      #080808
    );

  border: 1px solid #444;

  font-size: 13px;

  letter-spacing: 1px;
}

.music-option:hover {
  border-color: #aaa;
}

.music-option.selected {

  border-color: white;

  background:
    linear-gradient(
      145deg,
      #303030,
      #101010
    );

  box-shadow:
    0 0 18px rgba(255,255,255,0.08);
}


/* música selecionada */

.now-playing {

  margin-top: 20px;

  padding: 13px 15px;

  border-left: 2px solid #aaa;

  background: #0b0b0b;

  color: #777;

  font-size: 10px;

  letter-spacing: 1px;
}

.now-playing span {
  color: white;
}


/* BOTÃO PEQUENO */

.tiny-next {

  display: block;

  margin: 16px auto 0;

  padding: 5px 10px;

  border: 1px solid #555;

  background: #111;

  color: #999;

  font-family: "Share Tech Mono", monospace;

  font-size: 9px;

  letter-spacing: 1px;

  text-transform: uppercase;
}

.tiny-next:hover {

  color: white;

  border-color: #aaa;

  background: #181818;
}


/* =========================
   QUIZ
========================= */

.question {

  margin-top: 28px;

  padding-top: 10px;

}

.answer {

  display: block;

  width: 100%;

  margin: 8px 0;

  padding: 13px;

  text-align: left;

  color: #ccc;

  background: #0b0b0b;

  border: 1px solid #444;
}

.answer:hover {
  border-color: #aaa;
}

.success {

  margin-top: 15px;

  padding: 13px;

  border-left: 2px solid #aaa;

  background: #0b0b0b;

  color: #ccc;
}

.error {

  margin-top: 15px;

  padding: 13px;

  border-left: 2px solid #777;

  background: #0b0b0b;

  color: #aaa;

  line-height: 1.6;
}


/* =========================
   MAZE
========================= */

.maze-wrapper {
  text-align: center;
}

.maze {

  display: grid;

  grid-template-columns:
    repeat(9, 28px);

  grid-template-rows:
    repeat(9, 28px);

  gap: 2px;

  justify-content: center;

  margin: 25px auto;
}

.cell {

  width: 28px;
  height: 28px;

  display: flex;

  justify-content: center;
  align-items: center;

  border: 1px solid #333;

  font-size: 7px;
}

.wall {
  background: #ddd;
}

.path {
  background: #090909;
}

.player {

  background:
    linear-gradient(
      145deg,
      #fff,
      #888
    );

  color: #000;

  font-weight: bold;
}

.goal {

  background:
    linear-gradient(
      145deg,
      #fff,
      #777
    );

  color: #000;

  font-weight: bold;

  font-size: 6px;
}


/* CONTROLES DO LABIRINTO */

.controls-maze {

  display: grid;

  grid-template-columns:
    repeat(3, 45px);

  justify-content: center;

  gap: 5px;

  margin-top: 20px;
}

.controls-maze button {

  padding: 10px;

  border: 1px solid #555;

  background: #111;

  color: #ccc;

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


/* =========================
   PRESENTE
========================= */

.reward {
  text-align: center;
}

.dancers {

  height: 170px;

  display: flex;

  justify-content: center;

  align-items: end;

  gap: 25px;

  margin: 30px 0;
}

.dancer {

  width: 35px;

  height: 100px;

  position: relative;

  border-radius: 20px 20px 5px 5px;

  background:
    linear-gradient(
      90deg,
      #555,
      #eee,
      #666
    );

  animation:
    dance 0.8s
    infinite alternate
    ease-in-out;
}

.dancer:nth-child(2) {
  animation-delay: .15s;
}

.dancer:nth-child(3) {
  animation-delay: .3s;
}

.dancer:nth-child(4) {
  animation-delay: .45s;
}

.dancer::before {

  content: "";

  position: absolute;

  width: 35px;
  height: 35px;

  top: -30px;
  left: 0;

  border-radius: 50%;

  background: #ddd;
}

@keyframes dance {

  from {
    transform:
      rotate(-8deg)
      translateY(5px);
  }

  to {
    transform:
      rotate(8deg)
      translateY(-10px);
  }

}

.access {

  margin: 20px 0;

  color: #999;

  line-height: 2;
}


/* =========================
   MENSAGEM
========================= */

.message {

  margin-top: 25px;

  padding-left: 18px;

  border-left: 2px solid #666;

  white-space: pre-line;

  line-height: 1.8;

  color: #bbb;
}


/* =========================
   DATABASE
========================= */

.database {

  margin-top: 40px;
}

.card {

  margin: 12px 0;

  padding: 18px;

  border: 1px solid #444;

  background:
    linear-gradient(
      145deg,
      #121212,
      #070707
    );
}

.card-title {

  margin-bottom: 8px;

  color: #777;

  font-size: 9px;

  letter-spacing: 2px;
}

.card-content {

  color: #eee;

  font-size: 15px;
}


/* =========================
   FINAL
========================= */

.final {

  margin-top: 45px;

  padding-top: 30px;

  border-top: 1px solid #444;

  text-align: center;
}


/* =========================
   CELULAR
========================= */

@media (max-width: 500px) {

  .panel {
    padding: 20px;
  }

  .maze {

    grid-template-columns:
      repeat(9, 25px);

    grid-template-rows:
      repeat(9, 25px);

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


<!-- ==================================================
     PÁGINA 1 — ESCOLHA DA MÚSICA
================================================== -->

<section
  id="musicScreen"
  class="screen"
>

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
      onclick="
        selectMusic(
          'NASA — ENHYPEN',
          'nasa.mp3',
          this
        )
      "
    >
      NASA — ENHYPEN
    </button>


    <button
      class="music-option"
      onclick="
        selectMusic(
          'NO WAY BACK — ENHYPEN',
          'no-way-back.mp3',
          this
        )
      "
    >
      NO WAY BACK — ENHYPEN
    </button>


    <button
      class="music-option"
      onclick="
        selectMusic(
          'ICONIC BY MISTAKE — KATSEYE',
          'iconic-by-mistake.mp3',
          this
        )
      "
    >
      ICONIC BY MISTAKE — KATSEYE
    </button>


    <div
      id="nowPlaying"
      class="now-playing hidden"
    >

      NOW PLAYING:

      <span id="songName"></span>

    </div>


    <button
      id="continueButton"
      class="tiny-next hidden"
      onclick="nextPage()"
    >
      próxima página →
    </button>

  </div>

</section>



<!-- ==================================================
     PÁGINA 2 — QUIZ
================================================== -->

<section
  id="quizScreen"
  class="screen hidden"
>

  <div class="panel">

    <div class="system">
      SYSTEM // SECURITY_CHECK
    </div>

    <h1>QUIZ</h1>


    <!-- QUESTÃO 1 -->

    <div class="question">

      <h2>
        01 // MEMÓRIA
      </h2>

      <p>
        Qual música a gente ficava dançando na TV da sala e a mãe aparecia do lado e a gente fingia que nada tava acontecendo?
      </p>


      <button
        class="answer"
        onclick="answerQ1(false)"
      >
        Nasa — ATEEZ
      </button>


      <button
        class="answer"
        onclick="answerQ1(true)"
      >
        Fire — BTS
      </button>


      <button
        class="answer"
        onclick="answerQ1(false)"
      >
        Way Back — ENHYPEN
      </button>

    </div>


    <div id="q1Result"></div>


    <!-- QUESTÃO 2 -->

    <div
      id="question2"
      class="question hidden"
    >

      <h2>
        02 // VIBE
      </h2>

      <p>
        Qual destas vibes combina mais com vc?
      </p>


      <button
        class="answer"
        onclick="answerQ2(false)"
      >
        Rosa pastel
      </button>


      <button
        class="answer"
        onclick="answerQ2(true)"
      >
        Cyber
      </button>


      <button
        class="answer"
        onclick="answerQ2(false)"
      >
        Cottagecore
      </button>

    </div>


    <div id="q2Result"></div>


    <!-- QUESTÃO 3 -->

    <div
      id="question3"
      class="question hidden"
    >

      <h2>
        03 // IDENTIDADE
      </h2>

      <p>
        Quem é a pessoa que está desbloqueando este sistema?
      </p>


      <button
        class="answer"
        onclick="answerQ3(true)"
      >
        A aniversariante
      </button>


      <button
        class="answer"
        onclick="answerQ3(false)"
      >
        Não sou a aniversariante
      </button>

    </div>


    <div id="q3Result"></div>


    <button
      id="retryButton"
      class="tiny-next hidden"
      onclick="retryQ3()"
    >
      TENTAR NOVAMENTE
    </button>

  </div>

</section>



<!-- ==================================================
     PÁGINA 3 — LABIRINTO
================================================== -->

<section
  id="mazeScreen"
  class="screen hidden"
>

  <div class="panel maze-wrapper">

    <div class="system">
      SYSTEM // MAZE_PROTOCOL
    </div>

    <h1>MAZE</h1>

    <p>
      encontre o caminho até o seu presente.
    </p>


    <div
      id="maze"
      class="maze"
    ></div>


    <div class="controls-maze">

      <button
        class="up"
        onclick="movePlayer(-1,0)"
      >
        ↑
      </button>

      <button
        class="left"
        onclick="movePlayer(0,-1)"
      >
        ←
      </button>

      <button
        class="down"
        onclick="movePlayer(1,0)"
      >
        ↓
      </button>

      <button
        class="right"
        onclick="movePlayer(0,1)"
      >
        →
      </button>

    </div>

  </div>

</section>



<!-- ==================================================
     PÁGINA 4 — PRESENTE
================================================== -->

<section
  id="rewardScreen"
  class="screen hidden"
>

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


    <button
      class="tiny-next"
      onclick="openPresent()"
    >
      ABRIR O PRESENTE
    </button>

  </div>

</section>



<!-- ==================================================
     PÁGINA 5 — MENSAGEM FINAL
================================================== -->

<section
  id="finalScreen"
  class="screen hidden"
>

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


    <!-- DATABASE -->

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


    <!-- FINAL -->

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

/* ==================================================
   MÚSICA
================================================== */

let audio = null;


/* escolher música */

function selectMusic(name, file, button) {

  /* para a música anterior */

  if (audio) {

    audio.pause();

    audio.currentTime = 0;

  }


  /* cria a nova música */

  audio = new Audio(file);

  audio.loop = true;


  /* mostra o nome */

  document.getElementById("songName").innerText = name;


  document
    .getElementById("nowPlaying")
    .classList.remove("hidden");


  /* mostra o botão próxima página */

  document
    .getElementById("continueButton")
    .classList
    .remove("hidden");


  /* marca a música selecionada */

  document
    .querySelectorAll(".music-option")
    .forEach(function(btn) {

      btn.classList.remove("selected");

    });


  button.classList.add("selected");


  /* tenta começar a música */

  audio.play().catch(function() {

    console.log(
      "Não foi possível tocar o arquivo."
    );

  });

}


/* ==================================================
   PRÓXIMA PÁGINA
================================================== */

function nextPage() {

  document
    .getElementById("musicScreen")
    .classList
    .add("hidden");


  document
    .getElementById("quizScreen")
    .classList
    .remove("hidden");


  window.scrollTo(0, 0);

}


/* ==================================================
   QUESTÃO 1
================================================== */

function answerQ1(correct) {

  const result =
    document.getElementById("q1Result");


  if (correct) {

    result.innerHTML = `
      <div class="success">
        ✓ resposta correta.
      </div>
    `;


    document
      .getElementById("question2")
      .classList
      .remove("hidden");

  }

  else {

    result.innerHTML = `
      <div class="error">
        ✕ resposta incorreta. tente novamente.
      </div>
    `;

  }

}


/* ==================================================
   QUESTÃO 2
================================================== */

function answerQ2(correct) {

  const result =
    document.getElementById("q2Result");


  if (correct) {

    result.innerHTML = `
      <div class="success">
        ✓ resposta correta.
      </div>
    `;


    document
      .getElementById("question3")
      .classList
      .remove("hidden");

  }

  else {

    result.innerHTML = `
      <div class="error">
        ✕ resposta incorreta. tente novamente.
      </div>
    `;

  }

}


/* ==================================================
   QUESTÃO 3
================================================== */

function answerQ3(correct) {

  const result =
    document.getElementById("q3Result");


  if (correct) {

    result.innerHTML = `
      <div class="success">
        ✓ acesso liberado.
      </div>
    `;


    document
      .getElementById("retryButton")
      .classList
      .add("hidden");


    setTimeout(function() {

      document
        .getElementById("quizScreen")
        .classList
        .add("hidden");


      document
        .getElementById("mazeScreen")
        .classList
        .remove("hidden");


      createMaze();


    }, 700);

  }

  else {

    result.innerHTML = `
      <div class="error">
        error - seu acesso foi negado, vc não é o destinatário do presente, retire-se imediatamente
      </div>
    `;


    document
      .getElementById("retryButton")
      .classList
      .remove("hidden");

  }

}


/* tentar novamente */

function retryQ3() {

  document
    .getElementById("q3Result")
    .innerHTML = "";


  document
    .getElementById("retryButton")
    .classList
    .add("hidden");

}


/* ==================================================
   LABIRINTO
================================================== */

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


/* criar labirinto */

function createMaze() {

  const maze =
    documen
