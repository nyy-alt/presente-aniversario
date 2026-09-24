<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Birthday Web Present</title>

<style>

* {
    box-sizing: border-box;
}

html, body {
    margin: 0;
    padding: 0;
    min-height: 100%;
}

body {
    font-family: Arial, Helvetica, sans-serif;
    color: #111;

    background:
        linear-gradient(
            rgba(255,255,255,.18),
            rgba(0,0,0,.30)
        ),
        url("chrome.jpg");

    background-size: cover;
    background-position: center;
    background-attachment: fixed;

    overflow-x: hidden;
}


/* =================================
   EFEITO CHROME MOVENDO
================================= */

body::before {
    content: "";
    position: fixed;
    inset: 0;

    pointer-events: none;
    z-index: 999;

    background:
        linear-gradient(
            120deg,
            transparent 0%,
            rgba(255,255,255,.35) 45%,
            transparent 55%
        );

    background-size: 250% 250%;

    animation: chromeLight 8s linear infinite;

    mix-blend-mode: screen;
}

@keyframes chromeLight {

    0% {
        background-position: 200% 0;
    }

    100% {
        background-position: -200% 0;
    }

}


/* =================================
   PÁGINAS
================================= */

.page {

    display: none;

    min-height: 100vh;
    width: 100%;

    padding: 30px 15px;

    align-items: center;
    justify-content: center;
}

.page.active {
    display: flex;
}


/* =================================
   PAINEL
================================= */

.panel {

    width: min(900px, 100%);

    padding: 35px 25px;

    text-align: center;

    border-radius: 25px;

    background:
        linear-gradient(
            145deg,
            rgba(255,255,255,.78),
            rgba(210,210,220,.55),
            rgba(255,255,255,.82)
        );

    border: 2px solid rgba(255,255,255,.9);

    box-shadow:

        inset 0 0 30px rgba(255,255,255,.8),

        inset 0 0 60px rgba(0,0,0,.15),

        0 20px 60px rgba(0,0,0,.35);

    backdrop-filter: blur(8px);

    animation: panelAppear .7s ease;

}

@keyframes panelAppear {

    from {
        opacity: 0;
        transform: scale(.94) translateY(15px);
    }

    to {
        opacity: 1;
        transform: scale(1) translateY(0);
    }

}


/* =================================
   TÍTULOS
================================= */

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


/* =================================
   BOTÕES
================================= */

.cyber-btn {

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


/* =================================
   MENSAGENS
================================= */

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


/* =================================
   QUIZ
================================= */

.quiz-number {

    font-size: 13px;

    letter-spacing: 4px;

    font-weight: bold;

    color: #555;

    margin-bottom: 15px;

}


/* =================================
   LABIRINTO
================================= */

#maze {

    display: grid;

    width: min(88vw, 600px);

    aspect-ratio: 1 / 1;

    margin: 25px auto;

    border: 3px solid #333;

    background: #111;

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


/* =================================
   PRESENTE
================================= */

.gift {

    font-size: 90px;

    animation: floatingGift 2s infinite ease-in-out;

}

@keyframes floatingGift {

    0%,100% {
        transform: translateY(0) rotate(-3deg);
    }

    50% {
        transform: translateY(-15px) rotate(3deg);
    }

}


/* ==========================================
   JOGO DA VELHA
========================================== */

let ticBoard = [];
let ticGameOver = false;

const PLAYER = "O";
const ROBOT = "X";


function resetTicTacToe() {

    ticBoard = [
        "", "", "",
        "", "", "",
        "", "", ""
    ];

    ticGameOver = false;

    document.getElementById("ticMessage").textContent =
        "SUA VEZ.";

    document.getElementById("ticContinue").style.display =
        "none";

    drawTicTacToe();
}


function drawTicTacToe() {

    const board =
        document.getElementById("ticBoard");

    board.innerHTML = "";

    for(let i = 0; i < 9; i++) {

        const button =
            document.createElement("button");

        button.className = "tic-cell";

        button.textContent =
            ticBoard[i];

        if(ticBoard[i] === "O") {
            button.classList.add("o");
        }

        if(ticBoard[i] === "X") {
            button.classList.add("x");
        }

        button.addEventListener(
            "click",
            function() {
                playerMove(i);
            }
        );

        board.appendChild(button);
    }
}


function playerMove(position) {

    if(ticGameOver) {
        return;
    }

    if(ticBoard[position] !== "") {
        return;
    }

    ticBoard[position] = PLAYER;

    drawTicTacToe();

    if(checkTicWinner(PLAYER)) {

        playerWon();

        return;
    }

    if(ticBoard.every(cell => cell !== "")) {

        drawTicDraw();

        return;
    }

    document.getElementById("ticMessage").textContent =
        "ROBÔ PENSANDO...";

    setTimeout(robotTurn, 600);
}


function robotTurn() {

    if(ticGameOver) {
        return;
    }

    const empty =
        ticBoard
        .map((cell, index) =>
            cell === "" ? index : null
        )
        .filter(index => index !== null);


    if(empty.length === 0) {
        return;
    }


    /*
    O ROBÔ TENTA GANHAR
    */

    for(const position of empty) {

        ticBoard[position] = ROBOT;

        if(checkTicWinner(ROBOT)) {

            drawTicTacToe();

            robotWon();

            return;
        }

        ticBoard[position] = "";
    }


    /*
    O ROBÔ TENTA BLOQUEAR VOCÊ
    */

    for(const position of empty) {

        ticBoard[position] = PLAYER;

        if(checkTicWinner(PLAYER)) {

            ticBoard[position] = ROBOT;

            drawTicTacToe();

            document.getElementById("ticMessage").textContent =
                "SUA VEZ.";

            return;
        }

        ticBoard[position] = "";
    }


    /*
    SE O CENTRO ESTIVER LIVRE,
    O ROBÔ PEGA
    */

    if(ticBoard[4] === "") {

        ticBoard[4] = ROBOT;

    }

    else {

        /*
        CASO CONTRÁRIO,
        ESCOLHE UMA CASA ALEATÓRIA
        */

        const randomPosition =
            empty[
                Math.floor(
                    Math.random() * empty.length
                )
            ];

        ticBoard[randomPosition] = ROBOT;
    }


    drawTicTacToe();


    if(checkTicWinner(ROBOT)) {

        robotWon();

        return;
    }


    if(ticBoard.every(cell => cell !== "")) {

        drawTicDraw();

        return;
    }


    document.getElementById("ticMessage").textContent =
        "SUA VEZ.";
}


function checkTicWinner(player) {

    const combinations = [

        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],

        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],

        [0, 4, 8],
        [2, 4, 6]

    ];


    return combinations.some(
        combination =>
            combination.every(
                position =>
                    ticBoard[position] === player
            )
    );
}


function playerWon() {

    ticGameOver = true;

    document.getElementById("ticMessage").textContent =
        "✓ VOCÊ DERROTOU O ROBÔ!";


    document.getElementById("ticContinue").style.display =
        "block";
}


function robotWon() {

    ticGameOver = true;

    document.getElementById("ticMessage").textContent =
        "O ROBÔ GANHOU 😭 TENTA DE NOVO!";
}


function drawTicDraw() {

    ticGameOver = true;

    document.getElementById("ticMessage").textContent =
        "EMPATE! O ROBÔ SOBREVIVEU 😭";
}


/* INICIA O JOGO */

resetTicTacToe();
    
/* =================================
   MEMÓRIA
================================= */

.memory-title {

    font-size: 15px;

    letter-spacing: 4px;

    font-weight: bold;

}

.memory-board {

    display: grid;

    grid-template-columns: repeat(4, 1fr);

    gap: 10px;

    width: min(92vw, 500px);

    margin: 30px auto;

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

    cursor: pointer;

    font-size: 30px;

    display: flex;

    align-items: center;

    justify-content: center;

    box-shadow:

        inset 0 0 10px rgba(255,255,255,.6),

        0 5px 10px rgba(0,0,0,.3);

    transition: .25s;

}

.memory-card.flipped {

    background: #eee;

    transform: rotateY(180deg);

}

.memory-card.matched {

    background: white;

    box-shadow: 0 0 20px rgba(255,255,255,.9);

}


/* =================================
   FINAL
================================= */

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


/* =================================
   MOBILE
================================= */

@media(max-width:600px) {

    .panel {

        padding: 25px 15px;

        border-radius: 20px;

    }

    .memory-board {

        gap: 7px;

    }

}

</style>
</head>


<body>


<!-- ==========================================
     PÁGINA 1
========================================== -->

<section class="page active" id="page1">

<div class="panel">

<h1>Birthday Protocol</h1>

<p>

ANTES DE CONTINUAR, É OBRIGATÓRIO COLOCAR UMA MÚSICA BEM CYBERPUNK PRA COMBINAR 😡

</p>

<button
class="cyber-btn"
onclick="musicChoice(true)">

COLOQUEI

</button>

<button
class="cyber-btn"
onclick="musicChoice(false)">

AINDA NÃO COLOQUEI

</button>

<div id="musicMessage" class="message"></div>

</div>

</section>



<!-- ==========================================
     PÁGINA 2
========================================== -->

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
onclick="showPage(3)">

CONTINUAR →

</button>

</div>

</section>



<!-- ==========================================
     PÁGINA 3 — QUIZ 1
========================================== -->

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
onclick="quizAnswer(3,true)">

Fire — BTS

</button>

<button
class="cyber-btn"
onclick="quizAnswer(3,false)">

Nasa — ATEEZ

</button>

<button
class="cyber-btn"
onclick="quizAnswer(3,false)">

Way Back — ENHYPEN

</button>

<div id="quizMessage3" class="message"></div>

</div>

</section>



<!-- ==========================================
     PÁGINA 4 — QUIZ 2
========================================== -->

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
onclick="quizAnswer(4,false)">

Rosa pastel

</button>

<button
class="cyber-btn"
onclick="quizAnswer(4,true)">

Cyber

</button>

<button
class="cyber-btn"
onclick="quizAnswer(4,false)">

Cottagecore

</button>

<div id="quizMessage4" class="message"></div>

</div>

</section>



<!-- ==========================================
     PÁGINA 5 — QUIZ 3
========================================== -->

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
onclick="unlockSystem()">

A aniversariante

</button>

<button
class="cyber-btn"
onclick="wrongPerson()">

Não sou a aniversariante

</button>

<div id="quizMessage5" class="message"></div>

</div>

</section>



<!-- ==========================================
     PÁGINA 6 — LABIRINTO
========================================== -->

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
onclick="movePlayer(0,-1)">

↑

</button>

<button
class="cyber-btn"
onclick="movePlayer(-1,0)">

←

</button>

<button
class="cyber-btn"
onclick="movePlayer(0,1)">

↓

</button>

<button
class="cyber-btn"
onclick="movePlayer(1,0)">

→

</button>

<div id="mazeMessage" class="message"></div>

</div>

</section>



<!-- ==========================================
     PÁGINA 7 — PRESENTE
========================================== -->

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
onclick="showPage(8)">

PRÓXIMO JOGO →

</button>

</div>

</section>



<!-- ==========================================
     PÁGINA 8 — JOGO DA VELHA
========================================== -->

<section class="page" id="page8">

<div class="panel">

<div class="tic-title">
SYSTEM VS PLAYER
</div>

<h1>Tic Tac Toe</h1>

<p>

Você é <b>O</b>.

<br>

O robô é <b>X</b>.

<br><br>

Derrote o sistema para continuar.

</p>

<div id="ticBoard" class="tic-board"></div>

<div id="ticMessage" class="message">

SUA VEZ.

</div>

<button
class="cyber-btn"
onclick="resetTicTacToe()">

REINICIAR JOGO

</button>

<button
id="ticContinue"
class="cyber-btn"
style="display:none;"
onclick="showPage(9)">

CONTINUAR →

</button>

</div>

</section>



<!-- ==========================================
     PÁGINA 9 — TEXTO
========================================== -->

<section class="page" id="page9">

<div class="panel">

<h1>Parabéns!</h1>

<p>

parabéns, mais uma conquista do dia KSKDKDK

</p>

<p>

Quero te parabenizar por mais um ano de vida com todos esses joguinhos legaizinhos pra vce se divertir um pouquinho 🫶🏼 saiba que eu te amo muito viu? E nenhum desses textinhos foram tirados de uma IA, eu fiz a mão todos 😋 a única coisa que eu tive que pedir ajuda pra IA foi como fazer um site interativo KSKSKKSKSKDK então se vc achar falhas de texto, ignore T-T

</p>

<button
class="cyber-btn"
onclick="showPage(10)">

ÚLTIMO JOGO →

</button>

</div>

</section>



<!-- ==========================================
     PÁGINA 10 — MEMÓRIA
========================================== -->

<section class="page" id="page10">

<div class="panel">

<div class="memory-title">
FINAL FILE
</div>

<h1>último jogo!! Hehehe</h1>

<p>

Encontre todos os pares 👀

</p>

<div id="memoryBoard" class="memory-board"></div>

<div id="memoryMessage" class="message"></div>

</div>

</section>



<script>


/* ==========================================
   NAVEGAÇÃO
========================================== */

function showPage(number) {

    document
        .querySelectorAll(".page")
        .forEach(page => {

            page.classList.remove("active");

        });

    const page =
        document.getElementById("page" + number);

    if(page) {

        page.classList.add("active");

        window.scrollTo(0,0);

    }

}



/* ==========================================
   MÚSICA
========================================== */

function musicChoice(placed) {

    const message =
        document.getElementById("musicMessage");

    if(placed) {

        message.textContent =
            "✓ MÚSICA DETECTADA.";

        setTimeout(() => {

            showPage(2);

        }, 500);

    }

    else {

        message.textContent =
            "É ORA COLOCAAAAAR !!! 😡😡😡";

    }

}



/* ==========================================
   QUIZ
========================================== */

function quizAnswer(page, correct) {

    const message =
        document.getElementById("quizMessage" + page);

    if(correct) {

        message.textContent =
            "✓ RESPOSTA CORRETA";

        message.className =
            "message correct";

        setTimeout(() => {

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


function unlockSystem() {

    const message =
        document.getElementById("quizMessage5");

    message.textContent =
        "✓ RESPOSTA CORRETA — ACESSO LIBERADO";

    message.className =
        "message correct";

    setTimeout(() => {

        showPage(6);

        createMaze();

    }, 900);

}


function wrongPerson() {

    const message =
        document.getElementById("quizMessage5");

    message.textContent =
        "error - seu acesso foi negado, vc não é o destinatário do presente, retire-se imediatamente";

    message.className =
        "message wrong";

}



/* ==========================================
   LABIRINTO
========================================== */

const mazeMap = [

"111111111111111111111",
"100000000000000000001",
"101111111111111111101",
"101000000000000000101",
"101011111011111110101",
"101010001010000010101",
"101010101010111010101",
"101010101010101010101",
"101000101000101000101",
"101110101111101111101",
"100010100000100000001",
"111010111110111111101",
"100010000010000000101",
"101111111011111110101",
"101000001000000010101",
"101011101111111010101",
"101000100000001000101",
"101111101111101111101",
"100000001000001000001",
"101111111011111111101",
"100000000000000000001"

];

let playerX = 1;
let playerY = 1;

const goalX = 19;
const goalY = 19;


function createMaze() {

    const maze =
        document.getElementById("maze");

    maze.innerHTML = "";

    maze.style.gridTemplateColumns =
        `repeat(${mazeMap[0].length}, 1fr)`;


    for(let y = 0; y < mazeMap.length; y++) {

        for(let x = 0; x < mazeMap[y].length; x++) {

            const cell =
                document.createElement("div");

            cell.className = "cell";


            if(mazeMap[y][x] === "1") {

                cell.classList.add("wall");

            }


            if(x === playerX && y === playerY) {

                cell.classList.add("player");

            }


            if(x === goalX && y === goalY) {

                cell.classList.add("goal");

            }


            maze.appendChild(cell);

        }

    }

}


function movePlayer(dx,dy) {

    const newX =
        playerX + dx;

    const newY =
        playerY + dy;


    if(
        newX < 0 ||
        newY < 0 ||
        newY >= mazeMap.length ||
        newX >= mazeMap[0].length
    ) {

        return;

    }


    if(mazeMap[newY][newX] === "1") {

        return;

    }


    playerX = newX;
    playerY = newY;

    createMaze();


    if(
        playerX === goalX &&
        playerY === goalY
    ) {

        document
            .getElementById("mazeMessage")
            .textContent =
            "✓ PRESENTE ENCONTRADO!";

        setTimeout(() => {

            showPage(7);

        }, 800);

    }

}


document.addEventListener(
    "keydown",
    function(event) {

        if(event.key === "ArrowUp") {

            movePlayer(0,-1);

        }

        if(event.key === "ArrowDown") {

            movePlayer(0,1);

        }

        if(event.key === "ArrowLeft") {

            movePlayer(-1,0);

        }

        if(event.key === "ArrowRight") {

            movePlayer(1,0);

        }

    }
);



/* ==========================================
   JOGO DA VELHA
========================================== */

let ticBoard = [];

let ticGameOver = false;

const human = "O"
