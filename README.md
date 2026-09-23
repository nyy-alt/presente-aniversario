<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Protocol</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800&family=Share+Tech+Mono&display=swap" rel="stylesheet">

<style>
*{
  box-sizing:border-box;
}

html{
  scroll-behavior:smooth;
}

body{
  margin:0;
  background:
    radial-gradient(circle at 50% 0%,#303236 0%,#111214 35%,#050506 75%);
  color:#eee;
  font-family:"Share Tech Mono",monospace;
  overflow-x:hidden;
}

body:before{
  content:"";
  position:fixed;
  inset:0;
  pointer-events:none;
  background:
    linear-gradient(rgba(255,255,255,.025) 1px,transparent 1px),
    linear-gradient(90deg,rgba(255,255,255,.025) 1px,transparent 1px);
  background-size:32px 32px;
  z-index:-2;
}

body:after{
  content:"";
  position:fixed;
  width:200%;
  height:3px;
  background:linear-gradient(
    90deg,
    transparent,
    rgba(255,255,255,.25),
    transparent
  );
  top:20%;
  left:-50%;
  animation:scan 7s linear infinite;
  opacity:.35;
  pointer-events:none;
}

@keyframes scan{
  from{transform:translateY(-100px)}
  to{transform:translateY(100vh)}
}

.hidden{
  display:none!important;
}

.container{
  width:min(92%,900px);
  margin:auto;
}

.chrome{
  background:
    linear-gradient(
      145deg,
      #08090a 0%,
      #25272a 20%,
      #666a6e 35%,
      #17191b 50%,
      #777b7f 65%,
      #17191b 82%,
      #08090a 100%
    );
  border:1px solid #aaa;
  box-shadow:
    inset 0 1px rgba(255,255,255,.8),
    inset 0 -1px rgba(0,0,0,.9),
    0 15px 45px rgba(0,0,0,.65);
}

header{
  min-height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:30px 15px;
}

.hero{
  width:min(850px,100%);
  padding:45px 25px;
  text-align:center;
  border-radius:18px;
  position:relative;
  overflow:hidden;
}

.hero:after{
  content:"";
  position:absolute;
  inset:0;
  background:linear-gradient(
    115deg,
    transparent 20%,
    rgba(255,255,255,.15) 45%,
    transparent 55%
  );
  animation:shine 5s infinite;
  pointer-events:none;
}

@keyframes shine{
  0%,65%{transform:translateX(-100%)}
  100%{transform:translateX(100%)}
}

.system{
  font-size:11px;
  letter-spacing:3px;
  color:#c7c9cb;
  margin-bottom:20px;
}

h1{
  font-family:"Orbitron",sans-serif;
  font-size:clamp(32px,8vw,75px);
  letter-spacing:4px;
  margin:0 0 20px;
  background:linear-gradient(
    #fff,
    #777,
    #f5f5f5,
    #555,
    #fff
  );
  -webkit-background-clip:text;
  color:transparent;
}

.subtitle{
  color:#bbb;
  line-height:1.7;
  max-width:650px;
  margin:0 auto 30px;
}

button{
  font-family:"Share Tech Mono",monospace;
  cursor:pointer;
}

.chrome-btn{
  border:1px solid #aaa;
  border-radius:8px;
  padding:15px 25px;
  background:
    linear-gradient(#f5f5f5,#777,#ddd,#555);
  color:#0a0a0a;
  font-weight:bold;
  letter-spacing:2px;
  box-shadow:
    inset 0 1px #fff,
    0 5px 15px #0008;
  transition:.2s;
}

.chrome-btn:hover{
  transform:translateY(-2px);
  filter:brightness(1.15);
}

.chrome-btn:active{
  transform:translateY(1px);
}

main{
  padding:50px 0 80px;
}

.section{
  margin-bottom:45px;
}

.panel{
  padding:25px;
  border-radius:15px;
  margin-bottom:20px;
  background:
    linear-gradient(145deg,#181a1d,#090a0b);
  border:1px solid #62666a;
  box-shadow:
    inset 0 1px rgba(255,255,255,.08),
    0 10px 30px #0007;
}

.panel-title{
  font-family:"Orbitron",sans-serif;
  font-size:clamp(18px,5vw,27px);
  letter-spacing:2px;
  margin:0 0 18px;
  color:#eee;
}

.panel p{
  line-height:1.8;
  color:#d0d2d4;
  white-space:pre-line;
}

.badge{
  display:inline-block;
  padding:6px 10px;
  border:1px solid #777;
  font-size:10px;
  letter-spacing:2px;
  color:#bbb;
  margin-bottom:15px;
}

.database{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:15px;
}

.info-card{
  background:
    linear-gradient(145deg,#222427,#0b0c0e);
  border:1px solid #555;
  border-radius:10px;
  padding:18px;
}

.info-title{
  font-size:11px;
  letter-spacing:2px;
  color:#aaa;
  margin-bottom:10px;
}

.info-value{
  font-family:"Orbitron",sans-serif;
  font-size:14px;
  color:#eee;
  line-height:1.5;
}

/* QUIZ */

.quiz-card{
  padding:25px;
  border-radius:15px;
  background:linear-gradient(145deg,#17191b,#090a0b);
  border:1px solid #666;
  margin-bottom:20px;
}

.quiz-card.locked{
  opacity:.3;
  pointer-events:none;
}

.question{
  font-family:"Orbitron",sans-serif;
  font-size:18px;
  line-height:1.5;
  margin-bottom:20px;
}

.answer{
  width:100%;
  padding:15px;
  margin:6px 0;
  border-radius:8px;
  border:1px solid #555;
  background:linear-gradient(#292b2e,#0b0c0d);
  color:#eee;
  text-align:left;
  font-family:"Share Tech Mono",monospace;
  transition:.2s;
}

.answer:hover{
  border-color:#aaa;
  background:linear-gradient(#444,#111);
}

.answer.correct{
  background:linear-gradient(#eee,#777);
  color:#111;
  border-color:#fff;
}

.answer.wrong{
  opacity:.5;
}

.success{
  color:#ddd;
  font-size:11px;
  letter-spacing:2px;
  margin-top:12px;
}

/* PROGRESS */

.progress-wrap{
  margin:20px 0;
}

.progress-info{
  display:flex;
  justify-content:space-between;
  font-size:10px;
  color:#aaa;
  margin-bottom:7px;
}

.progress{
  height:8px;
  background:#222;
  border:1px solid #555;
  border-radius:99px;
  overflow:hidden;
}

.progress-bar{
  height:100%;
  width:0%;
  background:linear-gradient(90deg,#555,#fff,#777);
  transition:.5s;
}

/* MAZE */

.maze-wrap{
  display:flex;
  justify-content:center;
  margin:25px 0;
}

.maze{
  width:min(420px,100%);
  aspect-ratio:1;
  display:grid;
  grid-template-columns:repeat(9,1fr);
  grid-template-rows:repeat(9,1fr);
  border:2px solid #aaa;
  background:#08090a;
}

.cell{
  display:flex;
  justify-content:center;
  align-items:center;
  text-align:center;
  font-size:clamp(6px,1.9vw,10px);
  font-weight:bold;
}

.wall{
  background:
    linear-gradient(
      135deg,
      #555,
      #151617,
      #777
    );
  border:1px solid #090909;
}

.path{
  background:#101214;
  border:1px solid #1d2022;
}

.player{
  background:linear-gradient(#fff,#777,#ddd);
  color:#08090a;
  border:2px solid white;
  font-size:clamp(6px,1.8vw,9px);
}

.goal{
  background:linear-gradient(#eee,#666,#ddd);
  color:#050505;
  border:2px solid white;
  font-size:clamp(5px,1.7vw,9px);
}

.controls{
  display:grid;
  grid-template-columns:55px 55px 55px;
  justify-content:center;
  gap:7px;
  margin-top:18px;
}

.controls button{
  height:50px;
  border-radius:8px;
  border:1px solid #999;
  background:linear-gradient(#eee,#777,#ddd);
  color:#111;
  font-size:20px;
  font-weight:bold;
}

.empty{
  visibility:hidden;
}

.maze-status{
  text-align:center;
  font-size:11px;
  color:#aaa;
  letter-spacing:2px;
  margin-top:15px;
}

/* REWARD */

.reward{
  text-align:center;
  padding:35px 20px;
  border-radius:16px;
  background:
    linear-gradient(
      145deg,
      #eee,
      #777,
      #eee,
      #555
    );
  color:#08090a;
  border:1px solid white;
  box-shadow:0 15px 45px #0009;
}

.reward h2{
  font-family:"Orbitron",sans-serif;
  letter-spacing:3px;
}

.reward p{
  line-height:1.7;
}

footer{
  text-align:center;
  color:#666;
  font-size:10px;
  letter-spacing:2px;
  padding:40px 0;
}

@media(max-width:600px){
  .database{
    grid-template-columns:1fr;
  }

  .hero{
    padding:35px 18px;
  }

  .panel{
    padding:20px;
  }
}
</style>
</head>

<body>

<header id="start">

  <div class="hero chrome">

    <div class="system">
      SYSTEM // BIRTHDAY_PROTOCOL
    </div>

    <h1>FELIZ<br>ANIVERSÁRIOOO!</h1>

    <p class="subtitle">
      Feliz aniversárioooo!<br><br>

      Demorou 2 semanas pra eu conseguir fazer esse site,
      tem muito código 😭 Mas eu consegui!<br><br>

      Bom, eu achei que um texto no whatsapp apenas seria
      muito simples, quis criar algo que fosse mais especial ❤️
      Dediquei meu tempo a video aulas no YT e pedi ajuda pro
      Chat GPT pra fazer ele super bonitinho, então eu espero
      que tenha dado certo!!<br><br>

      Sem mais enrolação, vamos ao presente virtual kdkdkkd
    </p>

    <button class="chrome-btn" id="startBtn">
      INICIAR PROTOCOLO
    </button>

  </div>

</header>


<main id="site" class="hidden">

<div class="container">


<!-- CARTA -->

<section class="section">

  <div class="panel">

    <span class="badge">MESSAGE.EXE</span>

    <h2 class="panel-title">
      UMA MENSAGEM PARA VOCÊ
    </h2>

    <p>
Eu quero primeiramente te agradecer por ter sido a pessoa que mais me apoiou por todos esses anos 🫶🏼 crescer com vc foi o melhor presente da minha vida, porque eu pude contar com vc sempre, contar tudo que acontece comigo, pedir ajuda com roupas, cabelo (inclusive vc que me ensinou a fazer o cabelo), aprendi a lidar com pessoas, conheci k-pop por vc também, aprendi a ter gostos próprios e etc... Você, diferente de qualquer outro familiar, foi uma das pessoas mais presentes na minha vida, e eu agradeço muito a Deus por isso... Pensando agora, eu não sei o que seria da minha vida sem vc, acho que eu seria uma feia, lascada, sem saber arrumar o cabelo e sem personalidade própria kskskskksksksk😭🫶🏼

Também quero te desejar um ótimo aniversário 🎂, que vc possa ter o melhor aniversário da sua vida, ganhar seu tablet, o melhor bolo e se melhores fotos!!! Vou te obrigar a se arrumar pra tirar fotos aesthetics ok? Vc agora está no auge da idade, idade de diva, então vc vai conquistsr tudo o que vc sonhava em ter 😌
    </p>

  </div>

</section>


<!-- DATABASE -->

<section class="section">

  <div class="panel">

    <span class="badge">PERSONAL_DATABASE</span>

    <h2 class="panel-title">
      ARQUIVOS PESSOAIS
    </h2>

    <div class="database">

      <div class="info-card">
        <div class="info-title">
          MÚSICA QUE ME LEMBRA VOCÊ
        </div>
        <div class="info-value">
          Nasa — ATEEZ
        </div>
      </div>

      <div class="info-card">
        <div class="info-title">
          UMA COISA QUE VOCÊ AMA
        </div>
        <div class="info-value">
          Eu, claro 😌
        </div>
      </div>

      <div class="info-card">
        <div class="info-title">
          UMA MEMÓRIA NOSSA
        </div>
        <div class="info-value">
          A época do BTS que a gente dançava Fire KSKSKSKKDKD
        </div>
      </div>

      <div class="info-card">
        <div class="info-title">
          UMA COISA QUE COMBINA COM VOCÊ
        </div>
        <div class="info-value">
          Cyber
        </div>
      </div>

    </div>

  </div>

</section>


<!-- QUIZ -->

<section class="section">

  <div class="panel">

    <span class="badge">SECURITY_SYSTEM</span>

    <h2 class="panel-title">
      COMPLETE AS MISSÕES
    </h2>

    <p>
      Existem arquivos bloqueados no sistema.
      Complete todas as verificações para continuar.
    </p>

    <div class="progress-wrap">

      <div class="progress-info">
        <span>MISSION PROGRESS</span>
        <span id="progressText">0 / 3</span>
      </div>

      <div class="progress">
        <div class="progress-bar" id="progressBar"></div>
      </div>

    </div>

  </div>


  <!-- PERGUNTA 1 -->

  <div class="quiz-card" id="quiz1">

    <span class="badge">01 // MEMORY CHECK</span>

    <div class="question">
      Qual música a gente ficava dançando na TV da sala e a mãe aparecia do lado e a gente fingia que nada tava acontecendo?
    </div>

    <button class="answer" data-correct="true">
      Fire — BTS
    </button>

    <button class="answer" data-correct="false">
      Nasa — ATEEZ
    </button>

    <button class="answer" data-correct="false">
      Way Back — ENHYPEN
    </button>

    <div class="success"></div>

  </div>


  <!-- PERGUNTA 2 -->

  <div class="quiz-card locked" id="quiz2">

    <span class="badge">02 // VIBE DETECTION</span>

    <div class="question">
      Qual destas vibes combina mais com vc?
    </div>

    <button class="answer" data-correct="false" disabled>
      Rosa pastel
    </button>

    <button class="answer" data-correct="true" disabled>
      Cyber
    </button>

    <button class="answer" data-correct="false" disabled>
      Cottagecore
    </button>

    <div class="success"></div>

  </div>


  <!-- PERGUNTA 3 -->

  <div class="quiz-card locked" id="quiz3">

    <span class="badge">03 // FINAL VERIFICATION</span>

    <div class="question">
      Quem é a pessoa que está desbloqueando este sistema?
    </div>

    <button class="answer" id="finalAnswer" disabled>
      A ANIVERSARIANTE, OBVIAMENTE.
    </button>

    <div class="success"></div>

  </div>

</section>


<!-- LABIRINTO -->

<section class="section hidden" id="mazeSection">

  <div class="panel">

    <span class="badge">04 // PRESENT_MAZE</span>

    <h2 class="panel-title">
      FIND THE PRESENT.
    </h2>

    <p>
      Você entrou no sistema de segurança.<br>
      Encontre o caminho correto e atravesse o labirinto
      para desbloquear seu presente.
    </p>

    <div class="maze-wrap">

      <div class="maze" id="maze"></div>

    </div>

    <div class="controls">

      <button class="empty"></button>

      <button data-move="up">↑</button>

      <button class="empty"></button>

      <button data-move="left">←</button>

      <button data-move="down">↓</button>

      <button data-move="right">→</button>

    </div>

    <div class="maze-status" id="mazeStatus">
      LOCALIZE: VOCÊ
    </div>

  </div>

</section>


<!-- PRESENTE -->

<section class="section hidden" id="rewardSection">

  <div class="reward">

    <h2>
      ACCESS GRANTED // 100%
    </h2>

    <p>
      Você conseguiu.
    </p>

    <p>
      O sistema foi completamente desbloqueado.
    </p>

    <p style="font-size:22px;font-family:Orbitron;">
      ✦ SEU PRESENTE ✦
    </p>

    <button class="chrome-btn" id="openFinal">
      ABRIR PRESENTE
    </button>

  </div>

</section>


<!-- FINAL -->

<section class="section hidden" id="finalSection">

  <div class="panel">

    <span class="badge">
      SYSTEM // MISSION_COMPLETE
    </span>

    <h2 class="panel-title">
      FELIZ ANIVERSÁRIO 🩶
    </h2>

    <p>
      E finalmente chegamos ao fim do sistema KKKKKKK.

      Eu espero que você tenha gostado desse presente
      tanto quanto eu gostei de fazer ele.

      Te amo muito 🫶🏼

      Feliz aniversário!!!
    </p>

    <div style="
      text-align:center;
      margin-top:30px;
      font-family:Orbitron;
      letter-spacing:3px;
      color:#ddd;
    ">
      END OF PROTOCOL
    </div>

  </div>

</section>


<footer>
  BIRTHDAY_PROTOCOL // SYSTEM COMPLETE
</footer>

</div>

</main>


<script>

const startBtn = document.getElementById("startBtn");
const site = document.getElementById("site");

startBtn.addEventListener("click",()=>{

  document.getElementById("start").classList.add("hidden");

  site.classList.remove("hidden");

  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

});


/* =========================
   QUIZ
========================= */

let completed = 0;

const progressBar =
document.getElementById("progressBar");

const progressText =
document.getElementById("progressText");

const quizzes = [
  document.getElementById("quiz1"),
  document.getElementById("quiz2"),
  document.getElementById("quiz3")
];

function updateProgress(){

  progressBar.style.width =
    (completed / 3 * 100) + "%";

  progressText.textContent =
    completed + " / 3";

}


document.querySelectorAll(".answer").forEach(button=>{

  button.addEventListener("click",()=>{

    const quiz =
      button.closest(".quiz-card");

    const success =
      quiz.querySelector(".success");

    if(button.dataset.correct === "true"){

      quiz.querySelectorAll(".answer")
        .forEach(b=>b.disabled=true);

      button.classList.add("correct");

      success.textContent =
        "✓ ACCESS VERIFIED";

      completed++;

      updateProgress();

      if(completed < 3){

        const next =
          quizzes[completed];

        next.classList.remove("locked");

        next.querySelectorAll(".answer")
          .forEach(b=>b.disabled=false);

      }

      if(completed === 3){

        setTimeout(()=>{

          document.getElementById("mazeSection")
            .classList.remove("hidden");

          document.getElementById("mazeSection")
            .scrollIntoView({
              behavior:"smooth"
            });

          createMaze();

        },700);

      }

    }else{

      button.classList.add("wrong");

      const oldText =
        button.textContent;

      button.textContent =
        "✕ INCORRETO — TENTE NOVAMENTE";

      setTimeout(()=>{

        button.classList.remove("wrong");

        button.textContent =
          oldText;

      },900);

    }

  });

});


/* =========================
   MAZE
========================= */

const mazeLayout = [

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
  r:1,
  c:1
};

const goal = {
  r:7,
  c:7
};

let mazeCreated=false;


function createMaze(){

  if(mazeCreated) return;

  mazeCreated=true;

  renderMaze();

}


function renderMaze(){

  const maze =
    document.getElementById("maze");

  maze.innerHTML="";

  mazeLayout.forEach((row,r)=>{

    [...row].forEach((value,c)=>{

      const cell =
        document.createElement("div");

      cell.className =
        "cell " +
        (value==="1" ? "wall":"path");

      if(
        player.r===r &&
        player.c===c
      ){

        cell.classList.add("player");

        cell.textContent =
          "VOCÊ";

      }

      if(
        goal.r===r &&
        goal.c===c
      ){

        cell.classList.add("goal");

        cell.textContent =
          "SEU PRESENTE";

      }

      maze.appendChild(cell);

    });

  });

}


function movePlayer(dr,dc){

  const nr =
    player.r + dr;

  const nc =
    player.c + dc;

  if(
    nr<0 ||
    nr>8 ||
    nc<0 ||
    nc>8
  ) return;

  if(
    mazeLayout[nr][nc]==="1"
  ) return;

  player={
    r:nr,
    c:nc
  };

  renderMaze();

  if(
    player.r===goal.r &&
    player.c===goal.c
  ){

    document.getElementById("mazeStatus")
      .textContent =
      "DESTINO LOCALIZADO ✓";

    setTimeout(()=>{

      document.getElementById("rewardSection")
        .classList.remove("hidden");

      document.getElementById("rewardSection")
        .scrollIntoView({
          behavior:"smooth"
        });

    },500);

  }else{

    document.getElementById("mazeStatus")
      .textContent =
      "LOCALIZE: SEU PRESENTE";

  }

}


const moveMap={

  up:[-1,0],

  down:[1,0],

  left:[0,-1],

  right:[0,1]

};


document.querySelectorAll(
  "#mazeSection [data-move]"
).forEach(button=>{

  button.addEventListener("click",()=>{

    const move =
      moveMap[
        button.dataset.move
      ];

    movePlayer(
      move[0],
      move[1]
    );

  });

});


document.addEventListener("keydown",(event)=>{

  const map={

    ArrowUp:"up",
    ArrowDown:"down",
    ArrowLeft:"left",
    ArrowRight:"right",

    w:"up",
    s:"down",
    a:"left",
    d:"right"

  };

  if(map[event.key]){

    event.preventDefault();

    const move =
      moveMap[
        map[event.key]
      ];

    movePlayer(
      move[0],
      move[1]
    );

  }

});


/* =========================
   PRESENTE
========================= */

document.getElementById("openFinal")
.addEventListener("click",()=>{

  document.getElementById("finalSection")
    .classList.remove("hidden");

  document.getElementById("finalSection")
    .scrollIntoView({
      behavior:"smooth"
    });

});


updateProgress();

</script>

</body>
</html>
