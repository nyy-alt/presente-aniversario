<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>BIRTHDAY_PROTOCOL</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800&family=Share+Tech+Mono&display=swap');

* {
    box-sizing: border-box;
}

html, body {
    margin: 0;
    width: 100%;
    min-height: 100%;
}

body {
    background: #030303;
    color: #eee;
    font-family: 'Share Tech Mono', monospace;
    overflow-x: hidden;
}

/* =========================
   FUNDO CYBER EM MOVIMENTO
========================= */

body::before {
    content: "";
    position: fixed;
    inset: -100px;
    z-index: -3;

    background:
        linear-gradient(rgba(255,255,255,.045) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.045) 1px, transparent 1px);

    background-size: 55px 55px;

    transform: perspective(500px) rotateX(55deg) scale(1.5);

    animation: gridMove 8s linear infinite;
}

@keyframes gridMove {
    from {
        background-position: 0 0, 0 0;
    }

    to {
        background-position: 0 55px, 55px 0;
    }
}

/* linhas luminosas passando */

body::after {
    content: "";
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 1000;

    background:
        linear-gradient(
            transparent 0%,
            transparent 47%,
            rgba(255,255,255,.09) 50%,
            transparent 53%,
            transparent 100%
        );

    background-size: 100% 180px;

    animation: scan 5s linear infinite;
    opacity: .35;
}

@keyframes scan {
    from {
        background-position: 0 -180px;
    }

    to {
        background-position: 0 100vh;
    }
}

/* =========================
   PÁGINAS
========================= */

.page {
    display: none;
    min-height: 100vh;
    padding: 35px 18px;
    justify-content: center;
    align-items: center;
}

.page.active {
    display: flex;
}

.container {
    position: relative;
    width: 100%;
    max-width: 850px;

    padding: 35px;

    background:
        linear-gradient(
            145deg,
            rgba(30,30,30,.96),
            rgba(5,5,5,.97)
        );

    border: 1px solid #777;

    box-shadow:
        0 0 0 1px #171717,
        0 0 25px rgba(255,255,255,.07),
        inset 0 0 35px rgba(255,255,255,.025);

    overflow: hidden;
}

/* decoração dentro do painel */

.container::before {
    content: "";
    position: absolute;
    width: 180px;
    height: 180px;

    right: -100px;
    top: -100px;

    border: 1px solid #555;
    transform: rotate(45deg);

    animation: rotateDecor 12s linear infinite;
}

@keyframes rotateDecor {
    to {
        transform: rotate(405deg);
    }
}

.system {
    color: #777;
    font-size: 11px;
    letter-spacing: 3px;
    margin-bottom: 18px;
}

h1,
h2 {
    font-family: 'Orbitron', sans-serif;
    letter-spacing: 3px;
}

h1 {
    font-size: clamp(27px, 7vw, 52px);
}

h2 {
    font-size: clamp(21px, 5vw, 34px);
}

.subtitle {
    color: #999;
    line-height: 1.8;
}

.divider {
    height: 1px;

    background:
        linear-gradient(
            90deg,
            transparent,
            #aaa,
            transparent
        );

    margin: 28px 0;
}

/* =========================
   BOTÕES
========================= */

.cyber-btn {
    margin-top: 25px;
    padding: 13px 20px;

    background:
        linear-gradient(
            135deg,
            #f1f1f1,
            #777,
            #d5d5d5
        );

    border: 1px solid white;

    color: #050505;

    font-family: 'Orbitron', sans-serif;
    font-weight: bold;

    letter-spacing: 2px;

    box-shadow:
        5px 5px 0 #222,
        0 0 15px rgba(255,255,255,.12);

    transition: .2s;
}

.cyber-btn:hover {
    transform: translate(3px,3px);
    box-shadow: 2px 2px 0 #222;
}

.small-btn {
    margin-top: 25px;

    padding: 9px 14px;

    background: rgba(0,0,0,.5);

    color: #aaa;

    border: 1px solid #555;

    font-family: 'Share Tech Mono', monospace;

    letter-spacing: 1px;

    transition: .2s;
}

.small-btn:hover {
    color: white;
    border-color: #aaa;
}

/* =========================
   PÁGINA 1
========================= */

.music-warning {
    position: relative;

    padding: 25px;

    margin: 25px 0;

    border: 1px solid #777;

    background:
        linear-gradient(
            135deg,
            rgba(255,255,255,.05),
            rgba(0,0,0,.6)
        );

    box-shadow:
        inset 0 0 20px rgba(255,255,255,.025);
}

.music-warning::before {
    content: "!";
    position: absolute;

    right: 18px;
    top: 10px;

    font-family: 'Orbitron';
    font-size: 35px;

    color: #555;
}

.warning {
    font-family: 'Orbitron', sans-serif;
    font-size: clamp(15px, 4vw, 23px);
    line-height: 1.6;
}

.choice {
    display: flex;
    flex-direction: column;
    gap: 12px;

    margin-top: 25px;
}

.choice button {
    padding: 16px;

    text-align: left;

    background:
        linear-gradient(
            90deg,
            #111,
            #191919,
            #0a0a0a
        );

    color: #bbb;

    border: 1px solid #444;

    font-family: 'Orbitron', sans-serif;

    letter-spacing: 1px;

    transition: .2s;
}

.choice button:hover {
    background: linear-gradient(90deg,#ddd,#777);
    color: #050505;
    border-color: white;
    transform: translateX(5px);
}

.message-box {
    margin-top: 18px;

    padding: 15px;

    border-left: 2px solid #aaa;

    color: #aaa;

    line-height: 1.7;

    display: none;
}

.message-box.show {
    display: block;
}

/* =========================
   TEXTO
========================= */

.letter {
    color: #ccc;

    line-height: 1.9;

    font-size: 15px;

    white-space: pre-line;
}

/* =========================
   QUIZ
========================= */

.quiz-question {
    padding: 23px;

    margin: 18px 0;

    background: rgba(5,5,5,.7);

    border: 1px solid #444;

    box-shadow: inset 0 0 20px rgba(255,255,255,.015);
}

.quiz-question p {
    color: #ccc;
    line-height: 1.7;
}

.quiz-options {
    display: grid;
    gap: 9px;
}

.quiz-options button {
    padding: 13px;

    text-align: left;

    background: #111;

    color: #aaa;

    border: 1px solid #444;

    transition: .2s;
}

.quiz-options button:hover {
    color: white;
    border-color: #aaa;
    transform: translateX(3px);
}

.quiz-result {
    min-height: 25px;
    margin-top: 13px;
}

/* =========================
   LABIRINTO
========================= */

.maze-wrapper {
    width: 100%;
    overflow: auto;

    margin-top: 20px;

    padding: 12px;

    border: 1px solid #333;

    background: #050505;
}

#maze {
    display: grid;

    grid-template-columns: repeat(21, 23px);
    grid-template-rows: repeat(21, 23px);

    gap: 2px;

    width: max-content;

    margin: auto;

    padding: 8px;
}

.cell {
    width: 23px;
    height: 23px;

    display: flex;

    justify-content: center;
    align-items: center;

    font-size: 6px;
}

.wall {
    background:
        linear-gradient(
            135deg,
            #777,
            #222
        );

    border: 1px solid #888;

    box-shadow:
        inset 0 0 4px #000;
}

.path {
    background: #090909;

    border: 1px solid #151515;
}

.player {
    background:
        linear-gradient(
            135deg,
            white,
            #666
        );

    color: #000;

    font-weight: bold;

    box-shadow:
        0 0 12px rgba(255,255,255,.5);
}

.goal {
    background:
        linear-gradient(
            135deg,
            #aaa,
            #333
        );

    color: white;

    font-weight: bold;

    box-shadow:
        0 0 15px rgba(255,255,255,.25);
}

.controls {
    display: grid;

    grid-template-columns: repeat(3, 55px);

    justify-content: center;

    gap: 6px;

    margin-top: 20px;
}

.controls button {
    height: 45px;

    background:
        linear-gradient(
            145deg,
            #222,
            #080808
        );

    color: #ddd;

    border: 1px solid #555;

    font-size: 18px;
}

.controls button:hover {
    background: #ddd;
    color: #000;
}

.maze-status {
    text-align: center;

    color: #777;

    margin-top: 15px;

    font-size: 12px;
}

/* =========================
   PRESENTE
========================= */

.present {
    text-align: center;
}

.present-box {
    position: relative;

    width: 180px;
    height: 130px;

    margin: 40px auto;

    background:
        linear-gradient(
            145deg,
            #eee,
            #777,
            #222
        );

    border: 2px solid #aaa;

    box-shadow:
        0 0 30px rgba(255,255,255,.15);

    animation: floating 2.5s ease-in-out infinite;
}

.present-box::before {
    content: "";

    position: absolute;

    left: 77px;
    top: 0;

    width: 23px;
    height: 100%;

    background:
        linear-gradient(
            90deg,
            #222,
            #aaa,
            #333
        );
}

.present-box::after {
    content: "";

    position: absolute;

    left: -8px;
    top: -18px;

    width: 192px;
    height: 27px;

    background:
        linear-gradient(
            #eee,
            #777
        );

    border: 2px solid #aaa;
}

@keyframes floating {
    0%,100% {
        transform: translateY(0);
    }

    50% {
        transform: translateY(-10px);
    }
}

/* =========================
   CARDS
========================= */

.cards {
    display: grid;

    grid-template-columns: repeat(2,1fr);

    gap: 15px;
}

.card {
    min-height: 135px;

    padding: 20px;

    background:
        linear-gradient(
            145deg,
            #171717,
            #080808
        );

    border: 1px solid #444;

    position: relative;

    overflow: hidden;
}

.card::after {
    content: "";

    position: absolute;

    width: 100%;
    height: 1px;

    background: #777;

    left: -100%;

    bottom: 0;

    animation: cardScan 3s linear infinite;
}

@keyframes cardScan {
    to {
        left: 100%;
    }
}

.card-title {
    color: #777;

    font-size: 10px;

    letter-spacing: 2px;

    margin-bottom: 15px;
}

.card-content {
    font-family: 'Orbitron', sans-serif;

    color: #ddd;

    line-height: 1.5;
}

/* =========================
   FINAL
========================= */

.final-screen {
    text-align: center;
}

.final-title {
    font-size: clamp(28px,8vw,60px);
}

.final-sub {
    color: #777;

    line-height: 1.8;

    letter-spacing: 2px;
}

/* PISTA FINAL */

.dance-floor {
    position: relative;

    width: 100%;
    height: 270px;

    margin: 35px auto;

    overflow: hidden;

    border: 1px solid #444;

    background:
        linear-gradient(
            90deg,
            transparent 49%,
            #333 50%,
            transparent 51%
        ),
        linear-gradient(
            #111 50%,
            #050505 50%
        );

    background-size:
        70px 100%,
        100% 100%;
}

.dance-floor::before {
    content: "";

    position: absolute;

    width: 100%;
    height: 100%;

    background:
        linear-gradient(
            transparent,
            rgba(255,255,255,.12),
            transparent
        );

    animation: floorLight 2s linear infinite;
}

@keyframes floorLight {
    from {
        transform: translateY(-100%);
    }

    to {
        transform: translateY(100%);
    }
}

.dancers {
    position: absolute;

    inset: 0;

    display: flex;

    justify-content: center;
    align-items: center;

    gap: 28px;

    z-index: 2;
}

.dancer {
    position: relative;

    width: 35px;
    height: 100px;

    animation: dance .7s infinite alternate ease-in-out;
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

.head {
    width: 27px;
    height: 27px;

    margin: auto;

    border-radius: 50%;

    background:
        linear-gradient(
            145deg,
            white,
            #555
        );
}

.body {
    width: 30px;
    height: 55px;

    margin: 4px auto;

    background:
        linear-gradient(
            90deg,
            #aaa,
            #222,
            #ddd
        );

    border-radius: 10px 10px 5px 5px;
}

.arm,
.leg {
    position: absolute;

    background: #999;
}

.arm {
    width: 7px;
    height: 42px;

    top: 30px;
}

.arm.left {
    left: 0;
    transform: rotate(35deg);
}

.arm.right {
    right: 0;
    transform: rotate(-35deg);
}

.leg {
    width: 8px;
    height: 38px;

    bottom: 0;
}

.leg.left {
    left: 8px;
    transform: rotate(10deg);
}

.leg.right {
    right: 8px;
    transform: rotate(-10deg);
}

@keyframes dance {
    from {
        transform:
            translateY(8px)
            rotate(-5deg);
    }

    to {
        transform:
            translateY(-10px)
            rotate(7deg);
    }
}

.final-message {
    font-family: 'Orbitron', sans-serif;

    font-size: clamp(16px,4vw,25px);

    line-height: 1.7;

    margin-top: 25px;
}

/* =========================
   MOBILE
========================= */

@media (max-width: 600px) {

    .container {
        padding: 22px;
    }

    .cards {
        grid-template-columns: 1fr;
    }

    #maze {
        grid-template-columns: repeat(21,20px);
        grid-template-rows: repeat(21,20px);
    }

    .cell {
        width: 20px;
        height: 20px;
    }

    .dancers {
        gap: 12px;
    }
}
</style>
</head>

<body>

<!-- =================================================
PÁGINA 1
================================================= -->

<section class="page active" id="page1">

<div class="container">

<div class="system">
SYSTEM // BIRTHDAY_PROTOCOL // 001
</div>

<h1>ACESSO NECESSÁRIO</h1>

<div class="music-warning">

<div class="warning">
ANTES DE CONTINUAR, É OBRIGATÓRIO COLOCAR UMA MÚSICA BEM CYBERPUNK PRA COMBINAR 😡
</div>

</div>

<p class="subtitle">
O sistema exige uma trilha sonora compatível com a atmosfera.
<br><br>
Depois de colocar a música, confirme abaixo.
</p>

<div class="choice">

<button onclick="musicChoice(true)">
COLOQUEI
</button>

<button onclick="musicChoice(false)">
AINDA NÃO COLOQUEI
</button>

</div>

<div class="message-box" id="musicMessage"></div>

<button
class="cyber-btn"
id="musicContinue"
onclick="nextPage(2)"
style="display:none;"
>
PRÓXIMA PÁGINA →
</button>

</div>

</section>


<!-- =================================================
PÁGINA 2
================================================= -->

<section class="page" id="page2">

<div class="container">

<div class="system">
SYSTEM // BIRTHDAY_PROTOCOL // 002
</div>

<h2>MESSAGE.INIT</h2>

<div class="divider"></div>

<div class="letter">
Feliz aniversárioooo! 
Demorou 2 semanas pra eu conseguir fazer esse site, tem muito código 😭 Mas eu consegui!
Bom, eu achei que um texto no whatsapp apenas seria muito simples, quis criar algo que fosse mais especial ❤️ Dediquei meu tempo a video aulas no YT e pedi ajuda pro Chat GPT pra fazer ele super bonitinho, então eu espero que tenha dado certo!! Sem mais enrolação, vamos ao presente virtual kdkdkkd
</div>

<button class="small-btn" onclick="nextPage(3)">
PRÓXIMA PÁGINA →
</button>

</div>

</section>


<!-- =================================================
PÁGINA 3
================================================= -->

<section class="page" id="page3">

<div class="container">

<div class="system">
SYSTEM // BIRTHDAY_PROTOCOL // 003
</div>

<h2>IDENTITY_CHECK.EXE</h2>

<p class="subtitle">
Algumas informações precisam ser verificadas antes de liberar o próximo arquivo.
</p>


<div class="quiz-question">

<p>
<strong>01 //</strong><br>
Qual música a gente ficava dançando na TV da sala e a mãe aparecia do lado e a gente fingia que nada tava acontecendo?
</p>

<div class="quiz-options">

<button onclick="answer(this,true)">
Fire — BTS
</button>

<button onclick="answer(this,false)">
Nasa — ATEEZ
</button>

<button onclick="answer(this,false)">
Way Back — ENHYPEN
</button>

</div>

<div class="quiz-result"></div>

</div>


<div class="quiz-question">

<p>
<strong>02 //</strong><br>
Qual destas vibes combina mais com vc?
</p>

<div class="quiz-options">

<button onclick="answer(this,false)">
Rosa pastel
</button>

<button onclick="answer(this,false)">
Cottagecore
</button>

<button onclick="answer(this,true)">
Cyber
</button>

</div>

<div class="quiz-result"></div>

</div>


<div class="quiz-question">

<p>
<strong>03 //</strong><br>
Quem é a pessoa que está desbloqueando este sistema?
</p>

<div class="quiz-options">

<button onclick="finalQuiz(this,true)">
A aniversariante
</button>

<button onclick="finalQuiz(this,false)">
Não sou a aniversariante
</button>

</div>

<div class="quiz-result"></div>

</div>

</div>

</section>


<!-- =================================================
PÁGINA 4
================================================= -->

<section class="page" id="page4">

<div class="container">

<div class="system">
SYSTEM // BIRTHDAY_PROTOCOL // 004
</div>

<h2>MAZE_PROTOCOL</h2>

<p class="subtitle">
O acesso foi liberado.
<br>
Encontre o caminho até o seu presente.
</p>

<div class="maze-wrapper">
<div id="maze"></div>
</div>

<div class="maze-status" id="mazeStatus">
LOCALIZAÇÃO: ENTRADA
</div>

<div class="controls">

<div></div>

<button onclick="move(0,-1)">
▲
</button>

<div></div>

<button onclick="move(-1,0)">
◀
</button>

<button onclick="move(0,1)">
▼
</button>

<button onclick="move(1,0)">
▶
</button>

</div>

<p
class="subtitle"
style="text-align:center;font-size:12px;"
>
Use as setas acima ou as setas do teclado.
</p>

</div>

</section>


<!-- =================================================
PÁGINA 5
================================================= -->

<section class="page" id="page5">

<div class="container">

<div class="system">
SYSTEM // BIRTHDAY_PROTOCOL // 005
</div>

<h2>PRESENT.EXE</h2>

<div class="present-box"></div>

<div class="letter">

Eu quero primeiramente te agradecer por ter sido a pessoa que mais me apoiou por todos esses anos 🫶🏼 crescer com vc foi o melhor presente da minha vida, porque eu pude contar com vc sempre, contar tudo que acontece comigo, pedir ajuda com roupas, cabelo (inclusive vc que me ensinou a fazer o cabelo), aprendi a lidar com pessoas, conheci k-pop por vc também, aprendi a ter gostos próprios e etc... Você, diferente de qualquer outro familiar, foi uma das pessoas mais presentes na minha vida, e eu agradeço muito a Deus por isso... Pensando agora, eu não sei o que seria da minha vida sem vc, acho que eu seria uma feia, lascada, sem saber arrumar o cabelo e sem personalidade própria kskskskksksksk😭🫶🏼

Também quero te desejar um ótimo aniversário 🎂, que vc possa ter o melhor aniversário da sua vida, ganhar seu tablet, o melhor bolo e se melhores fotos!!! Vou te obrigar a se arrumar pra tirar fotos aesthetics ok? Vc agora está no auge da idade, idade de diva, então vc vai conquistsr tudo o que vc sonhava em ter 😌

</div>

<button class="small-btn" onclick="nextPage(6)">
CONTINUAR →
</button>

</div>

</section>


<!-- =================================================
PÁGINA 6
================================================= -->

<section class="page" id="page6">

<div class="container">

<div class="system">
SYSTEM // BIRTHDAY_PROTOCOL // 006
</div>

<h2>PERSONAL_DATABASE</h2>

<p class="subtitle">
Arquivos encontrados no sistema.
</p>

<div class="cards">

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

<div class="card-c
