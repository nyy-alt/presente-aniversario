<!DOCTYPE html>
<html lang="pt-BR">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Birthday Protocol</title>

<style>

/* =========================================
   CONFIGURAÇÕES GERAIS
========================================= */

* {
    box-sizing: border-box;
}

html,
body {
    margin: 0;
    padding: 0;
    min-height: 100%;
}

body {

    font-family: Arial, Helvetica, sans-serif;

    color: #111;

    overflow-x: hidden;

    background:
        radial-gradient(
            circle at 50% 15%,
            #ffffff 0%,
            #bcbcbc 22%,
            #555 55%,
            #080808 100%
        );
}


/* =========================================
   FUNDO CYBER — GRADE ANIMADA
========================================= */

body::before {

    content: "";

    position: fixed;

    inset: -100px;

    z-index: 0;

    pointer-events: none;

    background:
        linear-gradient(
            rgba(255,255,255,.055) 1px,
            transparent 1px
        ),
        linear-gradient(
            90deg,
            rgba(255,255,255,.055) 1px,
            transparent 1px
        );

    background-size: 55px 55px;

    transform:
        perspective(500px)
        rotateX(55deg)
        scale(1.5);

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


/* =========================================
   SCANLINES
========================================= */

body::after {

    content: "";

    position: fixed;

    inset: 0;

    z-index: 1;

    pointer-events: none;

    background:
        linear-gradient(
            transparent 0%,
            transparent 47%,
            rgba(255,255,255,.10) 50%,
            transparent 53%,
            transparent 100%
        );

    background-size: 100% 180px;

    animation: scanMove 5s linear infinite;

    opacity: .35;

}

@keyframes scanMove {

    from {
        background-position: 0 -180px;
    }

    to {
        background-position: 0 100vh;
    }

}


/* =========================================
   LUZ CHROME
========================================= */

.chrome-light {

    position: fixed;

    inset: -50%;

    z-index: 1;

    pointer-events: none;

    background:
        linear-gradient(
            120deg,
            transparent 35%,
            rgba(255,255,255,.20) 48%,
            rgba(255,255,255,.04) 52%,
            transparent 65%
        );

    animation: chromeMove 7s linear infinite;

}

@keyframes chromeMove {

    from {
        transform: translateX(-30%);
    }

    to {
        transform: translateX(30%);
    }

}


/* =========================================
   PÁGINAS
========================================= */

.page {

    display: none;

    min-height: 100vh;

    width: 100%;

    padding: 30px 15px;

    align-items: center;

    justify-content: center;

    position: relative;

    z-index: 5;

}

.page.active {

    display: flex;

}


/* =========================================
   PAINEL
========================================= */

.panel {

    position: relative;

    z-index: 10;

    width: min(900px, 100%);

    padding: 35px 25px;

    text-align: center;

    border-radius: 25px;

    background:
        linear-gradient(
            145deg,
            rgba(255,255,255,.88),
            rgba(200,200,210,.68),
            rgba(255,255,255,.88)
        );

    border: 2px solid rgba(255,255,255,.95);

    box-shadow:

        inset 0 0 30px rgba(255,255,255,.85),

        inset 0 0 60px rgba(0,0,0,.18),

        0 20px 60px rgba(0,0,0,.50);

    backdrop-filter: blur(10px);

    animation: panelAppear .7s ease;

}

@keyframes panelAppear {

    from {

        opacity: 0;

        transform:
            scale(.94)
            translateY(15px);

    }

    to {

        opacity: 1;

        transform:
            scale(1)
            translateY(0);

    }

}


/* =========================================
   TÍTULOS
========================================= */

h1 {

    font-size: clamp(30px, 8vw, 65px);

    margin: 10px 0 25px;

    letter-spacing: 4px;

    text-transform: uppercase;

    color: #181818;

    text-shadow:

        1px 1px 0 #fff,

        2px 2px 0 #999,

        4px 4px 10px rgba(0,0,0,.35);

}

h2 {

    font-size: clamp(21px, 5vw, 32px);

    line-height: 1.35;

}

p {

    font-size: 17px;

    line-height: 1.75;

}


/* =========================================
   BOTÕES
========================================= */

.cyber-btn {

    position: relative;

    z-index: 20;

    display: block;

    width: min(500px, 95%);

    margin: 12px auto;

    padding: 15px 20px;

    border-radius: 12px;

    border: 2px solid #555;

    background:
        linear-gradient(
            145deg,
            #ffffff,
            #c8c8c8,
            #eeeeee,
            #999999
        );

    color: #111;

    font-weight: bold;

    font-size: 15px;

    letter-spacing: 1px;

    cursor: pointer;

    box-shadow:

        inset 0 2px 3px rgba(255,255,255,.9),

        inset 0 -3px 5px rgba(0,0,0,.25),

        0 6px 12px rgba(0,0,0,.25);

    transition: .2s;

    pointer-events: auto;

}

.cyber-btn:hover {

    transform: translateY(-3px);

    box-shadow:

        inset 0 2px 3px white,

        0 10px 20px rgba(0,0,0,.35);

}

.cyber-btn:active {

    transform: scale(.96);

}


/* =========================================
   MENSAGENS
========================================= */

.message {

    margin: 20px auto;

    font-weight: bold;

    font-size: 18px;

    min-height: 25px;

}

.correct {

    color: #111;

    text-shadow: 0 0 8px white;

}

.wrong {

    color: #555;

}


/* =========================================
   QUIZ
========================================= */

.quiz-number {

    font-size: 13px;

    letter-spacing: 4px;

    font-weight: bold;

    color: #555;

    margin-bottom: 15px;

}


/* =========================================
   LABIRINTO
========================================= */

#maze {

    display: grid;

    width: min(88vw, 600px);

    aspect-ratio: 1 / 1;

    margin: 25px auto;

    border: 3px solid #333;

    background: #111;

    position: relative;

    z-index: 15;

}

.cell {

    background: rgba(255,255,255,.35);

    border: 1px solid rgba(0,0,0,.1);

}

.wall {

    background:
        linear-gradient(
            135deg,
            #111,
            #aaa,
            #222,
            #eee,
            #333
        );

    border: 1px solid #111;

}

.player {

    background: #fff !important;

    box-shadow:

        inset 0 0 10px #000,

        0 0 15px white;

}

.goal {

    background: #777 !important;

    box-shadow: 0 0 20px #fff;

}


/* =========================================
   PRESENTE
========================================= */

.gift {

    font-size: 90px;

    animation: floatingGift 2s infinite ease-in-out;

}

@keyframes floatingGift {

    0%,
    100% {

        transform:
            translateY(0)
            rotate(-3deg);

    }

    50% {

        transform:
            translateY(-15px)
            rotate(3deg);

    }

}


/* =========================================
   FINAL
========================================= */

.final-screen {

    position: relative;

    min-height: 430px;

    overflow: hidden;

    border-radius: 20px;

    background:
        linear-gradient(
            180deg,
            #111,
            #555,
            #111
        );

    border: 2px solid #eee;

    box-shadow:

        inset 0 0 50px rgba(255,255,255,.20),

        0 0 40px rgba(0,0,0,.50);

    padding: 40px 20px;

}

.final-text {

    position: relative;

    z-index: 10;

    font-size: clamp(35px, 9vw, 70px);

    font-weight: bold;

    text-transform: uppercase;

    animation: finalGlow 2s infinite;

}

@keyframes finalGlow {

    0%,
    100% {

        transform: scale(1);

        text-shadow:

            0 0 5px white,

            0 0 15px #888;

    }

    50% {

        transform: scale(1.05);

        text-shadow:

            0 0 15px white,

            0 0 35px #555;

    }

}


/* =========================================
   PISO FUTURISTA
========================================= */

.cyber-floor {

    position: absolute;

    left: -20%;

    right: -20%;

    bottom: -70px;

    height: 180px;

    transform:
        perspective(300px)
        rotateX(60deg);

    background:

        linear-gradient(
            rgba(255,255,255,.25) 2px,
            transparent 2px
        ),

        linear-gradient(
            90deg,
            rgba(255,255,255,.25) 2px,
            transparent 2px
        );

    background-size: 45px 45px;

    animation: floorMove 2s linear infinite;

}

@keyframes floorMove {

    from {
        background-position: 0 0;
    }

    to {
        background-position: 0 45px;
    }

}


/* =========================================
   DANÇARINOS
========================================= */

.dancers {

    position: relative;

    z-index: 8;

    height: 180px;

    display: flex;

    justify-content: center;

    align-items: center;

    gap: 25px;

    margin-top: 20px;

}

.dancer {

    width: 28px;

    height: 90px;

    position: relative;

    background:
        linear-gradient(
            90deg,
            #111,
            #eee,
            #555
        );

    border-radius: 15px;

    box-shadow:

        0 0 15px rgba(255,255,255,.5);

    animation:
        dance 1s ease-in-out infinite alternate;

}

.dancer:nth-child(2) {
    animation-delay: .15s;
}

.dancer:nth-child(3) {
    animation-delay: .30s;
}

.dancer:nth-child(4) {
    animation-delay: .45s;
}

.dancer::before {

    content: "";

    position: absolute;

    width: 38px;

    height: 38px;

    border-radius: 50%;

    background:
        radial-gradient(
            circle at 35% 30%,
            white,
            #999,
            #111
        );

    top: -45px;

    left: -5px;

}

.dancer::after {

    content: "";

    position: absolute;

    width: 70px;

    height: 8px;

    background:
        linear-gradient(
            90deg,
            transparent,
            #222,
            #eee,
            #222,
            transparent
        );

    top: 28px;

    left: -20px;

    transform: rotate(-25deg);

}

@keyframes dance {

    from {

        transform:
            rotate(-10deg)
            translateY(10px);

    }

    to {

        transform:
            rotate(10deg)
            translateY(-12px);

    }

}


/* =========================================
   TEXTO FINAL
========================================= */

.system-checks {

    position: relative;

    z-index: 10;

    margin-top: 25px;

    font-family: monospace;

    font-size: 14px;

    line-height: 2;

    letter-spacing: 2px;

    color: white;

}

.final-subtitle {

    position: relative;

    z-index: 10;

    font-family: monospace;

    font-size: 15px;

    margin-top: 15px;

    color: white;

}


/* =========================================
   MOBILE
========================================= */

@media(max-width:600px) {

    .panel {

        padding: 25px 15px;

        border-radius: 20px;

    }

    p {

        font-size: 16px;

    }

    .dancers {

        gap: 14px;

    }

}

</style>

</head>


<body>


<div class="chrome-light"></div>


<!-- =====================================================
     PÁGINA 1 — MÚSICA
===================================================== -->

<section class="page active" id="page1">

<div class="panel">

<h1>Birthday Protocol</h1>

<p>

ANTES DE CONTINUAR, É OBRIGATÓRIO COLOCAR UMA MÚSICA BEM CYBERPUNK PRA COMBINAR 😡

</p>

<button
class="cyber-btn"
type="button"
onclick="musicChoice(true)">

COLOQUEI

</button>

<button
class="cyber-btn"
type="button"
onclick="musicChoice(false)">

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

<h1>Access Granted</h1>

<p>

Feliz aniversárioooo!

<br><br>

Demorou 2 semanas pra eu conseguir fazer esse site, tem muito código 😭
Mas eu consegui!

<br><br>

Bom, eu achei que um texto no whatsapp apenas seria muito simples,
quis criar algo que fosse mais especial ❤️
Dediquei meu tempo a video aulas no YT e pedi ajuda pro Chat GPT
pra fazer ele super bonitinho, então eu espero que tenha dado certo!!

<br><br>

Sem mais enrolação, vamos ao presente virtual kdkdkkd

</p>

<button
class="cyber-btn"
type="button"
onclick="showPage(3)">

CONTINUAR →

</button>

</div>

</section>



<!-- =====================================================
     PÁGINA 3 — QUIZ 1
===================================================== -->

<section class="page" id="page3">

<div class="panel">

<div class="quiz-number">

QUESTION 01 / 03

</div>

<h1>Quiz</h1>

<h2>

Qual música a gente ficava dançando na TV da sala
e a mãe aparecia do lado e a gente fingia que nada
tava acontecendo?

</h2>

<button
class="cyber-btn"
type="button"
onclick="quizAnswer(3,true)">

Fire — BTS

</button>

<button
class="cyber-btn"
type="button"
onclick="quizAnswer(3,false)">

Nasa — ATEEZ

</button>

<button
class="cyber-btn"
type="button"
onclick="quizAnswer(3,false)">

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

<div class="quiz-number">

QUESTION 02 / 03

</div>

<h1>Quiz</h1>

<h2>

Qual destas vibes combina mais com vc?

</h2>

<button
class="cyber-btn"
type="button"
onclick="quizAnswer(4,false)">

Rosa pastel

</button>

<button
class="cyber-btn"
type="button"
onclick="quizAnswer(4,true)">

Cyber

</button>

<button
class="cyber-btn"
type="button"
onclick="quizAnswer(4,false)">

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

<div class="quiz-number">

QUESTION 03 / 03

</div>

<h1>Security</h1>

<h2>

Quem é a pessoa que está desbloqueando este sistema?

</h2>

<button
class="cyber-btn"
type="button"
onclick="unlockSystem()">

A aniversariante

</button>

<button
class="cyber-btn"
type="button"
onclick="wrongPerson()">

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

<div class="quiz-number">

FILE 06 — MAZE

</div>

<h1>Cyber Maze</h1>

<p>

Encontre o presente.

<br>

Você começa no quadrado branco.
O presente está no final.

</p>

<div id="maze"></div>


<button
class="cyber-btn"
type="button"
onclick="movePlayer(0,-1)">

↑

</button>

<button
class="cyber-btn"
type="button"
onclick="movePlayer(-1,0)">

←

</button>

<button
class="cyber-btn"
type="button"
onclick="movePlayer(0,1)">

↓

</button>

<button
class="cyber-btn"
type="button"
onclick="movePlayer(1,0)">

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

<h1>Presente</h1>

<p>

Eu quero primeiramente te agradecer por ter sido a pessoa que mais me apoiou por todos esses anos 🫶🏼 crescer com vc foi o melhor presente da minha vida, porque eu pude contar com vc sempre, contar tudo que acontece comigo, pedir ajuda com roupas, cabelo (inclusive vc que me ensinou a fazer o cabelo), aprendi a lidar com pessoas, conheci k-pop por vc também, aprendi a ter gostos próprios e etc... Você, diferente de qualquer outro familiar, foi uma das pessoas mais presentes na minha vida, e eu agradeço muito a Deus por isso... Pensando agora, eu não sei o que seria da minha vida sem vc, acho que eu seria uma feia, lascada, sem saber arrumar o cabelo e sem personalidade própria kskskskksksksk😭🫶🏼

<br><br>

Também quero te desejar um ótimo aniversário 🎂, que vc possa ter o melhor aniversário da sua vida, ganhar seu tablet, o melhor bolo e se melhores fotos!!! Vou te obrigar a se arrumar pra tirar fotos aesthetics ok? Vc agora está no auge da idade, idade de diva, então vc vai conquistsr tudo o que vc sonhava em ter 😌

</p>

<button
class="cyber-btn"
type="button"
onclick="showPage(8)">

FINALIZAR PROTOCOLO →

</button>

</div>

</section>



<!-- =====================================================
     PÁGINA 8 — FINAL
===================================================== -->

<section class="page" id="page8">

<div class="panel">

<div class="final-screen">

<div class="quiz-number">

SYSTEM FINAL FILE

</div>

<div class="final-text">

VOCÊ CHEGOU AO FINAL.

</div>


<div class="dancers">

<div class="dancer"></div>

<div class="dancer"></div>

<div class="dancer"></div>

<div class="dancer"></div>

</div>


<div class="cyber-floor"></div>


<div class="system-checks">

✓ ALL FILES UNLOCKED

<br>

✓ ACCESS GRANTED

<br>

✓ BIRTHDAY PROTOCOL COMPLETE

</div>


<p class="final-subtitle">

FELIZ ANIVERSÁRIO, DIVA. 🩶

<br><br>

birthday_protocol.exe foi concluído com sucesso.

</p>

</div>

</div>

</section>



<script>


/* =====================================================
   NAVEGAÇÃO
===================================================== */

function showPage(number) {

    const pages =
        document.querySelectorAll(".page");

    pages.forEach(function(page) {

        page.classList.remove("active");

    });


    const selectedPage =
        document.getElementById("page" + number);


    if(selectedPage) {

        selectedPage.classList.add("active");

        window.scrollTo({
            top: 0,
            behavior: "instant"
        });

    }

}



/* =====================================================
   MÚSICA
===================================================== */

function musicChoice(placed) {

    const message =
        document.getElementById("musicMessage");


    if(placed) {

        message.textContent =
            "✓ MÚSICA DETECTADA.";

        message.className =
            "message correct";


        setTimeout(function() {

            showPage(2);

        }, 500);

    }

    else {

        message.textContent =
            "É ORA COLOCAAAAAR !!! 😡😡😡";

        message.className =
            "message wrong";

    }

}



/* =====================================================
   QUIZ
===================================================== */

function quizAnswer(page, correct) {

    const message =
        document.getElementById(
            "quizMessage" + page
        );


    if(correct) {

        message.textContent =
            "✓ RESPOSTA CORRETA";

        message.className =
            "message correct";


        setTimeout(function() {

            showPage(page + 1);

        }, 900);

    }

    else {

        message.textContent =
            "✕ RESPOSTA INCORRETA. TENTA DE NOVO.";

        message.className =
            "message wrong";

    }

}



/* =====================================================
   SECURITY
===================================================== */

function unlockSystem() {

    const message =
        document.getElementById("quizMessage5");


    message.textContent =
    
