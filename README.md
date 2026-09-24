<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Birthday Web Present</title>

<style>

/* =====================================================
   CONFIGURAÇÕES GERAIS
===================================================== */

* {
    box-sizing: border-box;
    -webkit-tap-highlight-color: transparent;
}

html {
    scroll-behavior: smooth;
}

body {
    margin: 0;
    min-height: 100vh;

    font-family: Arial, Helvetica, sans-serif;

    color: #111;

    background:
        linear-gradient(
            rgba(255,255,255,.12),
            rgba(0,0,0,.28)
        ),
        url("chrome.jpg");

    background-size: cover;
    background-position: center;
    background-attachment: fixed;

    overflow-x: hidden;
}


/* =====================================================
   LUZ CHROME ANIMADA
===================================================== */

body::before {
    content: "";

    position: fixed;
    inset: -100%;

    z-index: -2;

    pointer-events: none;

    background:
        linear-gradient(
            120deg,
            transparent 35%,
            rgba(255,255,255,.5) 48%,
            transparent 60%
        );

    background-size: 200% 200%;

    animation: chromeMove 9s linear infinite;
}

@keyframes chromeMove {

    0% {
        transform: translateX(-25%) translateY(-10%);
    }

    50% {
        transform: translateX(25%) translateY(10%);
    }

    100% {
        transform: translateX(-25%) translateY(-10%);
    }

}


/* =====================================================
   SCANLINE
===================================================== */

body::after {
    content: "";

    position: fixed;
    inset: 0;

    pointer-events: none;

    z-index: 999;

    background:
        linear-gradient(
            transparent 0%,
            transparent 48%,
            rgba(255,255,255,.16) 50%,
            transparent 52%,
            transparent 100%
        );

    background-size: 100% 160px;

    animation: scanline 5s linear infinite;

    opacity: .35;
}

@keyframes scanline {

    from {
        background-position: 0 -160px;
    }

    to {
        background-position: 0 160px;
    }

}


/* =====================================================
   PÁGINAS
===================================================== */

.page {

    display: none;

    min-height: 100vh;

    width: 100%;

    padding: 25px 15px;

    align-items: center;
    justify-content: center;
}

.page.active {
    display: flex;
}


/* =====================================================
   PAINEL
===================================================== */

.panel {

    width: min(900px, 100%);

    padding: 32px 22px;

    text-align: center;

    border-radius: 24px;

    background:
        linear-gradient(
            145deg,
            rgba(255,255,255,.88),
            rgba(205,205,210,.68),
            rgba(255,255,255,.86)
        );

    border: 2px solid rgba(255,255,255,.95);

    box-shadow:

        inset 0 0 25px rgba(255,255,255,.9),

        inset 0 0 60px rgba(0,0,0,.12),

        0 20px 60px rgba(0,0,0,.38);

    backdrop-filter: blur(10px);

    animation: panelIn .55s ease;
}

@keyframes panelIn {

    from {
        opacity: 0;
        transform: translateY(20px) scale(.96);
    }

    to {
        opacity: 1;
        transform: translateY(0) scale(1);
    }

}


/* =====================================================
   TEXTOS
===================================================== */

h1 {

    margin: 10px 0 25px;

    font-size: clamp(30px, 8vw, 65px);

    letter-spacing: 4px;

    text-transform: uppercase;

    color: #151515;

    text-shadow:
        1px 1px 0 #fff,
        3px 3px 0 #aaa,
        5px 5px 12px rgba(0,0,0,.28);
}

h2 {

    font-size: clamp(20px, 5vw, 30px);

    line-height: 1.4;
}

p {

    font-size: 17px;

    line-height: 1.75;
}

.small-label {

    font-size: 12px;

    letter-spacing: 4px;

    font-weight: bold;

    color: #555;

    margin-bottom: 15px;
}


/* =====================================================
   BOTÕES
===================================================== */

.cyber-btn {

    display: block;

    width: min(520px, 95%);

    margin: 12px auto;

    padding: 15px 20px;

    border-radius: 12px;

    border: 2px solid #555;

    background:
        linear-gradient(
            145deg,
            #ffffff,
            #c8c8c8,
            #f5f5f5,
            #8d8d8d
        );

    color: #111;

    font-size: 15px;

    font-weight: bold;

    letter-spacing: 1px;

    cursor: pointer;

    box-shadow:
        inset 0 2px 3px rgba(255,255,255,.95),
        inset 0 -3px 5px rgba(0,0,0,.2),
        0 6px 12px rgba(0,0,0,.25);

    transition: transform .15s, box-shadow .15s;
}

.cyber-btn:hover {

    transform: translateY(-2px);

    box-shadow:
        inset 0 2px 3px white,
        0 10px 20px rgba(0,0,0,.3);
}

.cyber-btn:active {

    transform: scale(.96);
}


/* =====================================================
   MENSAGENS
===================================================== */

.message {

    min-height: 28px;

    margin: 18px auto;

    font-size: 17px;

    font-weight: bold;
}

.correct {
    color: #111;
}

.error {
    color: #555;
}


/* =====================================================
   QUIZ
===================================================== */

.quiz-question {

    margin: 20px auto 30px;

    max-width: 750px;

    line-height: 1.5;
}


/* =====================================================
   PRESENTE
===================================================== */

.gift {

    font-size: 90px;

    animation: giftFloat 2s ease-in-out infinite;
}

@keyframes giftFloat {

    0%,100% {
        transform: translateY(0) rotate(-3deg);
    }

    50% {
        transform: translateY(-13px) rotate(3deg);
    }
}


/* =====================================================
   LABIRINTO
===================================================== */

#maze {

    width: min(88vw, 600px);

    aspect-ratio: 1 / 1;

    margin: 25px auto;

    display: grid;

    border: 3px solid #222;

    background: #111;
}

.maze-cell {

    min-width: 0;
    min-height: 0;

    background: rgba(255,255,255,.32);

    border: 1px solid rgba(0,0,0,.08);
}

.maze-wall {

    background:
        linear-gradient(
            135deg,
            #111,
            #888,
            #222,
            #eee,
            #333
        );

    border: 1px solid #111;
}

.maze-player {

    background: #fff !important;

    box-shadow:
        inset 0 0 8px #111,
        0 0 14px #fff;
}

.maze-goal {

    background: #777 !important;

    box-shadow:
        inset 0 0 8px #fff,
        0 0 18px #fff;
}


/* =====================================================
   JOGO DA VELHA
===================================================== */

.tic-board {

    width: min(86vw, 420px);

    aspect-ratio: 1 / 1;

    margin: 28px auto;

    display: grid;

    grid-template-columns: repeat(3, 1fr);

    gap: 8px;
}

.tic-cell {

    width: 100%;
    height: 100%;

    padding: 0;

    border: 2px solid #333;

    border-radius: 14px;

    background:
        linear-gradient(
            145deg,
            #f8f8f8,
            #a7a7a7,
            #ffffff,
            #777
        );

    font-size: clamp(42px, 14vw, 78px);

    font-weight: bold;

    color: #111;

    cursor: pointer;

    box-shadow:
        inset 0 0 12px rgba(255,255,255,.9),
        0 5px 10px rgba(0,0,0,.25);

    touch-action: manipulation;
}

.tic-cell:active {
    transform: scale(.94);
}

.tic-cell.o {

    color: #333;

    text-shadow:
        2px 2px 0 white,
        3px 3px 5px #777;
}

.tic-cell.x {

    color: #111;

    text-shadow:
        2px 2px 0 white,
        3px 3px 5px #777;
}


/* =====================================================
   MEMÓRIA
===================================================== */

.memory-board {

    width: min(94vw, 500px);

    margin: 25px auto;

    display: grid;

    grid-template-columns: repeat(4, 1fr);

    gap: 9px;
}

.memory-card {

    aspect-ratio: 1 / 1;

    border: 2px solid #444;

    border-radius: 12px;

    background:
        linear-gradient(
            135deg,
            #222,
            #aaa,
            #eee,
            #555
        );

    color: #111;

    font-size: clamp(24px, 8vw, 38px);

    font-weight: bold;

    cursor: pointer;

    box-shadow:
        inset 0 0 10px rgba(255,255,255,.6),
        0 5px 10px rgba(0,0,0,.25);

    touch-action: manipulation;
}

.memory-card.open {
    background: #eee;
}

.memory-card.matched {
    background: #fff;

    box-shadow:
        0 0 20px rgba(255,255,255,.95);
}


/* =====================================================
   FINAL
===================================================== */

.final-text {

    font-size: clamp(35px, 9vw, 70px);

    font-weight: bold;

    text-transform: uppercase;

    animation: finalGlow 2s infinite;
}

@keyframes finalGlow {

    0%,100% {

        transform: scale(1);

        text-shadow:
            0 0 5px #fff,
            0 0 15px #888;
    }

    50% {

        transform: scale(1.05);

        text-shadow:
            0 0 15px #fff,
            0 0 35px #555;
    }
}


/* =====================================================
   MOBILE
===================================================== */

@media(max-width:600px) {

    .page {
        padding: 15px 10px;
    }

    .panel {
        padding: 25px 14px;
        border-radius: 20px;
    }

    .memory-board {
        gap: 6px;
    }

    p {
        font-size: 16px;
    }
}

</style>
</head>


<body>


<!-- =====================================================
     PÁGINA 1 — MÚSICA
===================================================== -->

<section class="page active" id="page1">

<div class="panel">

<div class="small-label">
BIRTHDAY PROTOCOL
</div>

<h1>WELCOME</h1>

<p>
ANTES DE CONTINUAR, É OBRIGATÓRIO COLOCAR UMA MÚSICA BEM CYBERPUNK PRA COMBINAR 😡
</p>

<button
class="cyber-btn"
onclick="chooseMusic(true)">
COLOQUEI
</button>

<button
class="cyber-btn"
onclick="chooseMusic(false)">
AINDA NÃO COLOQUEI
</button>

<div
id="musicMessage"
class="message">
</div>

</div>

</section>



<!-- =====================================================
     PÁGINA 2 — INTRO
===================================================== -->

<section class="page" id="page2">

<div class="panel">

<div class="small-label">
FILE 02
</div>

<h1>ACCESS GRANTED</h1>

<p>

Feliz aniversárioooo!

<br><br>

Demorou 2 semanas pra eu conseguir fazer esse site, tem muito código 😭
Mas eu consegui!

<br><br>

Bom, eu achei que um texto no whatsapp apenas seria muito simples,
quis criar algo que fosse mais especial ❤️ Dediquei meu tempo a video aulas
no YT e pedi ajuda pro Chat GPT pra fazer ele super bonitinho,
então eu espero que tenha dado certo!!

<br><br>

Sem mais enrolação, vamos ao presente virtual kdkdkkd

</p>

<button
class="cyber-btn"
onclick="goToPage(3)">
CONTINUAR →
</button>

</div>

</section>



<!-- =====================================================
     PÁGINA 3 — QUIZ 1
===================================================== -->

<section class="page" id="page3">

<div class="panel">

<div class="small-label">
QUESTION 01 / 03
</div>

<h1>QUIZ</h1>

<h2 class="quiz-question">

Qual música a gente ficava dançando na TV da sala e a mãe aparecia do lado e a gente fingia que nada tava acontecendo?

</h2>

<button
class="cyber-btn"
onclick="answerQuiz(3, true)">
Fire — BTS
</button>

<button
class="cyber-btn"
onclick="answerQuiz(3, false)">
Nasa — ATEEZ
</button>

<button
class="cyber-btn"
onclick="answerQuiz(3, false)">
Way Back — ENHYPEN
</button>

<div
id="quizMessage3"
class="message">
</div>

</div>

</section>



<!-- =====================================================
     PÁGINA 4 — QUIZ 2
===================================================== -->

<section class="page" id="page4">

<div class="panel">

<div class="small-label">
QUESTION 02 / 03
</div>

<h1>QUIZ</h1>

<h2 class="quiz-question">

Qual destas vibes combina mais com vc?

</h2>

<button
class="cyber-btn"
onclick="answerQuiz(4, false)">
Rosa pastel
</button>

<button
class="cyber-btn"
onclick="answerQuiz(4, true)">
Cyber
</button>

<button
class="cyber-btn"
onclick="answerQuiz(4, false)">
Cottagecore
</button>

<div
id="quizMessage4"
class="message">
</div>

</div>

</section>



<!-- =====================================================
     PÁGINA 5 — QUIZ 3
===================================================== -->

<section class="page" id="page5">

<div class="panel">

<div class="small-label">
QUESTION 03 / 03
</div>

<h1>SECURITY</h1>

<h2 class="quiz-question">

Quem é a pessoa que está desbloqueando este sistema?

</h2>

<button
class="cyber-btn"
onclick="answerFinalQuiz(true)">
A aniversariante
</button>

<button
class="cyber-btn"
onclick="answerFinalQuiz(false)">
Não sou a aniversariante
</button>

<div
id="quizMessage5"
class="message">
</div>

</div>

</section>



<!-- =====================================================
     PÁGINA 6 — LABIRINTO
===================================================== -->

<section class="page" id="page6">

<div class="panel">

<div class="small-label">
FILE 06 — MAZE
</div>

<h1>CYBER MAZE</h1>

<p>
Encontre o presente.
<br>
O quadrado branco é você.
</p>

<div id="maze"></div>

<button
class="cyber-btn"
onclick="moveMaze(0,-1)">
↑
</button>

<button
class="cyber-btn"
onclick="moveMaze(-1,0)">
←
</button>

<button
class="cyber-btn"
onclick="moveMaze(0,1)">
↓
</button>

<button
class="cyber-btn"
onclick="moveMaze(1,0)">
→
</button>

<div
id="mazeMessage"
class="message">
</div>

</div>

</section>



<!-- =====================================================
     PÁGINA 7 — PRESENTE
===================================================== -->

<section class="page" id="page7">

<div class="panel">

<div class="gift">
🎁
</div>

<div class="small-label">
FILE UNLOCKED
</div>

<h1>PRESENTE</h1>

<p>

Eu quero primeiramente te agradecer por ter sido a pessoa que mais me apoiou por todos esses anos 🫶🏼 crescer com vc foi o melhor presente da minha vida, porque eu pude contar com vc sempre, contar tudo que acontece comigo, pedir ajuda com roupas, cabelo (inclusive vc que me ensinou a fazer o cabelo), aprendi a lidar com pessoas, conheci k-pop por vc também, aprendi a ter gostos próprios e etc... Você, diferente de qualquer outro familiar, foi uma das pessoas mais presentes na minha vida, e eu agradeço muito a Deus por isso... Pensando agora, eu não sei o que seria da minha vida sem vc, acho que eu seria uma feia, lascada, sem saber arrumar o cabelo e sem personalidade própria kskskskksksksk😭🫶🏼

<br><br>

Também quero te desejar um ótimo aniversário 🎂, que vc possa ter o melhor aniversário da sua vida, ganhar seu tablet, o melhor bolo e se melhores fotos!!! Vou te obrigar a se arrumar pra tirar fotos aesthetics ok? Vc agora está no auge da idade, idade de diva, então vc vai conquistsr tudo o que vc sonhava em ter 😌

</p>

<button
class="cyber-btn"
onclick="goToPage(8)">
PRÓXIMO JOGO →
</button>

</div>

</section>



<!-- =====================================================
     PÁGINA 8 — JOGO DA VELHA
===================================================== -->

<section class="page" id="page8">

<div class="panel">

<div class="small-label">
SYSTEM VS PLAYER
</div>

<h1>JOGO DA VELHA</h1>

<p>

Você é <b>O</b>.<br>
O robô é <b>X</b>.

<br><br>

Derrote o robô para continuar.

</p>

<div
id="ticBoard"
class="tic-board">
</div>

<div
id="ticMessage"
class="message">
SUA VEZ.
</div>

<button
class="cyber-btn"
onclick="resetTicTacToe()">
RECOMEÇAR
</button>

<button
id="ticContinue"
class="cyber-btn"
style="display:none;"
onclick="goToPage(9)">
CONTINUAR →
</button>

</div>

</section>



<!-- =====================================================
     PÁGINA 9 — TEXTO
===================================================== -->

<section class="page" id="page9">

<div class="panel">

<div class="small-label">
CONGRATULATIONS
</div>

<h1>PARABÉNS!</h1>

<p>

parabéns, mais uma conquista do dia KSKDKDK

</p>

<p>

Quero te parabenizar por mais um ano de vida com todos esses joguinhos legaizinhos pra vce se divertir um pouquinho 🫶🏼 saiba que eu te amo muito viu? E nenhum desses textinhos foram tirados de uma IA, eu fiz a mão todos 😋 a única coisa que eu tive que pedir ajuda pra IA foi como fazer um site interativo KSKSKKSKSKDK então se vc achar falhas de texto, ignore T-T

</p>

<button
class="cyber-btn"
onclick="goToPage(10)">
ÚLTIMO JOGO →
</button>

</div>

</section>



<!-- =====================================================
     PÁGINA 10 — MEMÓRIA
===================================================== -->

<section class="page" id="page10">

<div class="panel">

<div class="small-label">
FINAL GAME
</div>

<h1>último jogo!! Hehehe</h1>

<p>
Encontre todos os pares 👀
</p>

<div
id="memoryBoard"
class="memory-board">
</div>

<div
id="memoryMessage"
class="message">
</div>

</div>

</section>



<!-- =====================================================
     PÁGINA 11 — FINAL
===================================================== -->

<section class="page" id="page11">

<div class="panel">

<div class="small-label">
SYSTEM COMPLETE
</div>

<div class="final-text">
fim do web presenteeeee
</div>

<p>

✓ TODOS OS ARQUIVOS DESBLOQUEADOS

<br>

✓ TODOS OS JOGOS CONCLUÍDOS

<br>

✓ BIRTHDAY PROTOCOL COMPLETE

</p>

<h1>
FELIZ ANIVERSÁRIO, DIVA. 🩶
</h1>

</div>

</section>



<script>

/* =====================================================
   NAVEGAÇÃO
===================================================== */

function goToPage(number) {

    const pages =
        document.querySelectorAll(".page");

    pages.forEach(function(page) {

        page.classList.remove("active");

    });

    const destination =
        document.getElementById("page" + number);

    if(destination) {

        destination.classList.add("active");

        window.scrollTo(0, 0);
    }


    /*
       Quando entrar no jogo da velha,
       garante que ele esteja pronto.
    */

    if(number === 8) {

        resetTicTacToe();

    }


    /*
       Quando entrar na memória,
       começa um jogo novo.
    */

    if(number === 10) {

        startMemory();

    }

}



/* =====================================================
   MÚSICA
===================================================== */

function chooseMusic(putMusic) {

    const message =
        document.getElementById("musicMessage");


    if(putMusic === true) {

        message.textContent =
            "✓ MÚSICA DETECTADA. ACESSO LIBERADO.";

        setTimeout(function() {

            goToPage(2);

        }, 500);

    }

    else {

        message.textContent =
            "É ORA COLOCAAAAAR !!! 😡😡😡";

    }

}



/* =====================================================
   QUIZ
===================================================== */

function answerQuiz(pageNumber, correct) {

    const message =
        document.getElementById(
            "quizMessage" + pageNumber
        );


    if(correct === true) {

        message.textContent =
            "✓ RESPOSTA CORRETA";

        message.className =
            "message correct";


        setTimeout(function() {

            goToPage(pageNumber + 1);

        }, 850);

    }

    else {

        message.textContent =
            "✕ RESPOSTA INCORRETA. TENTA DE NOVO.";

        message.className =
            "message error";

    }

}



function answerFinalQuiz(correct) {

    const message =
        document.getElementById(
            "quizMessage5"
        );


    if(correct === true) {

        message.textContent =
            "✓ RESPOSTA CORRETA — ACESSO LIBERADO";

        message.className =
            "message correct";


        setTimeout(function() {

            goToPage(6);
