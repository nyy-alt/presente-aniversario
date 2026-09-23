<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Protocol</title>

<style>
* {
    box-sizing: border-box;
}

html, body {
    margin: 0;
    padding: 0;
    width: 100%;
    min-height: 100%;
    font-family: Arial, Helvetica, sans-serif;
    background: #050505;
    color: #eee;
}

body {
    min-height: 100vh;
    overflow-x: hidden;
}

/* FUNDO CYBER ANIMADO */
body::before {
    content: "";
    position: fixed;
    inset: -100px;
    z-index: -3;

    background:
        linear-gradient(rgba(255,255,255,.05) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.05) 1px, transparent 1px);

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

/* SCANLINES */
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
        background-position: 0 180px;
    }
}

/* PÁGINAS */

.page {
    display: none;
    min-height: 100vh;
    width: 100%;
    padding: 35px 20px;

    align-items: center;
    justify-content: center;
}

.page.active {
    display: flex;
}

.panel {
    width: min(900px, 100%);
    padding: 35px 25px;

    border: 1px solid #aaa;

    background:
        linear-gradient(
            145deg,
            rgba(255,255,255,.12),
            rgba(20,20,20,.92)
        );

    box-shadow:
        0 0 25px rgba(255,255,255,.08),
        inset 0 0 30px rgba(255,255,255,.04);

    text-align: center;
}

h1 {
    font-size: clamp(28px, 7vw, 60px);
    letter-spacing: 4px;
    margin-bottom: 25px;
    text-transform: uppercase;

    background: linear-gradient(
        90deg,
        #777,
        #fff,
        #888,
        #fff,
        #666
    );

    -webkit-background-clip: text;
    color: transparent;

    background-size: 300%;
    animation: chrome 4s linear infinite;
}

@keyframes chrome {
    from {
        background-position: 0%;
    }

    to {
        background-position: 300%;
    }
}

p {
    font-size: 17px;
    line-height: 1.7;
}

.cyber-btn {
    margin: 10px;
    padding: 15px 25px;

    background: #111;
    color: #eee;

    border: 1px solid #aaa;

    font-weight: bold;
    letter-spacing: 1px;

    cursor: pointer;

    box-shadow:
        0 0 10px rgba(255,255,255,.08),
        inset 0 0 10px rgba(255,255,255,.04);

    transition: .2s;
}

.cyber-btn:hover {
    background: #ddd;
    color: #000;
    transform: translateY(-2px);
}

.cyber-btn:active {
    transform: scale(.96);
}

.message {
    margin: 20px auto;
    min-height: 25px;
    font-weight: bold;
    letter-spacing: 1px;
}

/* QUIZ */

.question {
    margin: 30px 0;
    padding: 20px;

    border: 1px solid #555;
    background: rgba(0,0,0,.45);
}

.question h2 {
    font-size: 20px;
}

.answer {
    display: block;
    width: 100%;
    margin: 10px 0;
}

/* MAZE */

#maze {
    display: grid;

    width: min(90vw, 600px);
    aspect-ratio: 1 / 1;

    margin: 25px auto;

    border: 2px solid #aaa;
}

.cell {
    background: #050505;
    border: 1px solid #181818;
}

.wall {
    background:
        linear-gradient(
            135deg,
            #333,
            #777,
            #222
        );

    border: 1px solid #aaa;
}

.player {
    background: #fff !important;
    box-shadow: 0 0 15px #fff;
}

.goal {
    background: #888 !important;
    box-shadow: 0 0 15px #aaa;
}

/* PRESENTE */

.gift {
    font-size: 90px;
    margin: 20px;
    animation: giftFloat 2s ease-in-out infinite;
}

@keyframes giftFloat {
    0%,100% {
        transform: translateY(0) rotate(-2deg);
    }

    50% {
        transform: translateY(-12px) rotate(2deg);
    }
}

/* CARDS */

.cards {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 18px;
    margin-top: 30px;
}

.card {
    padding: 25px;

    border: 1px solid #777;

    background:
        linear-gradient(
            145deg,
            #222,
            #080808
        );

    transition: .3s;
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 0 20px rgba(255,255,255,.15);
}

.card h3 {
    font-size: 15px;
    letter-spacing: 2px;
}

/* FINAL */

.final-title {
    animation: finalPulse 2s infinite;
}

@keyframes finalPulse {
    0%,100% {
        transform: scale(1);
        text-shadow: 0 0 5px #fff;
    }

    50% {
        transform: scale(1.05);
        text-shadow:
            0 0 10px #fff,
            0 0 30px #aaa;
    }
}

.final-box {
    margin-top: 25px;
    padding: 25px;

    border: 1px solid #aaa;

    background: rgba(255,255,255,.04);
}

@media (max-width: 600px) {

    .page {
        padding: 20px 12px;
    }

    .panel {
        padding: 25px 15px;
    }

    .cards {
        grid-template-columns: 1fr;
    }

    .cyber-btn {
        width: 90%;
    }
}
</style>
</head>

<body>


<!-- PÁGINA 1 -->

<section class="page active" id="page1">

<div class="panel">

<h1>BIRTHDAY PROTOCOL</h1>

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



<!-- PÁGINA 2 -->

<section class="page" id="page2">

<div class="panel">

<h1>ACCESS GRANTED</h1>

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
onclick="nextPage(3)">
CONTINUAR →
</button>

</div>

</section>



<!-- PÁGINA 3 -->

<section class="page" id="page3">

<div class="panel">

<h1>SYSTEM QUIZ</h1>


<div class="question">

<h2>
Qual música a gente ficava dançando na TV da sala e a mãe aparecia do lado e a gente fingia que nada tava acontecendo?
</h2>

<button class="cyber-btn answer">
Fire — BTS
</button>

<button class="cyber-btn answer">
Nasa — ATEEZ
</button>

<button class="cyber-btn answer">
Way Back — ENHYPEN
</button>

</div>


<div class="question">

<h2>
Qual destas vibes combina mais com vc?
</h2>

<button class="cyber-btn answer">
Cyber
</button>

<button class="cyber-btn answer">
Rosa pastel
</button>

<button class="cyber-btn answer">
Cottagecore
</button>

</div>


<div class="question">

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

<div id="quizMessage" class="message"></div>

</div>

</div>

</section>



<!-- PÁGINA 4 -->

<section class="page" id="page4">

<div class="panel">

<h1>CYBER MAZE</h1>

<p>
ENCONTRE O PRESENTE.
<br>
Use as setas do teclado ou os botões abaixo.
</p>

<div id="maze"></div>

<div>

<button class="cyber-btn" onclick="movePlayer(0,-1)">↑</button>

<br>

<button class="cyber-btn" onclick="movePlayer(-1,0)">←</button>

<button class="cyber-btn" onclick="movePlayer(0,1)">↓</button>

<button class="cyber-btn" onclick="movePlayer(1,0)">→</button>

</div>

<div id="mazeMessage" class="message"></div>

</div>

</section>



<!-- PÁGINA 5 -->

<section class="page" id="page5">

<div class="panel">

<div class="gift">🎁</div>

<h1>PRESENTE DESBLOQUEADO</h1>

<p>
Eu quero primeiramente te agradecer por ter sido a pessoa que mais me apoiou por todos esses anos 🫶🏼
crescer com vc foi o melhor presente da minha vida, porque eu pude contar com vc sempre,
contar tudo que acontece comigo, pedir ajuda com roupas, cabelo
(inclusive vc que me ensinou a fazer o cabelo), aprendi a lidar com pessoas,
conheci k-pop por vc também, aprendi a ter gostos próprios e etc...
<br><br>

Você, diferente de qualquer outro familiar, foi uma das pessoas mais presentes na minha vida,
e eu agradeço muito a Deus por isso...
<br><br>

Pensando agora, eu não sei o que seria da minha vida sem vc,
acho que eu seria uma feia, lascada, sem saber arrumar o cabelo
e sem personalidade própria kskskskksksksk😭🫶🏼
<br><br>

Também quero te desejar um ótimo aniversário 🎂,
que vc possa ter o melhor aniversário da sua vida,
ganhar seu tablet, o melhor bolo e se melhores fotos!!!
<br><br>

Vou te obrigar a se arrumar pra tirar fotos aesthetics ok?
Vc agora está no auge da idade, idade de diva,
então vc vai conquistsr tudo o que vc sonhava em ter 😌
</p>

<button
class="cyber-btn"
onclick="nextPage(6)">
CONTINUAR →
</button>

</div>

</section>



<!-- PÁGINA 6 -->

<section class="page" id="page6">

<div class="panel">

<h1>FILES ABOUT YOU</h1>

<div class="cards">

<div class="card">
<h3>MÚSICA QUE ME LEMBRA VOCÊ</h3>
<p>Nasa — ATEEZ</p>
</div>

<div class="card">
<h3>UMA COISA QUE VOCÊ AMA</h3>
<p>Eu, claro 😌</p>
</div>

<div class="card">
<h3>UMA MEMÓRIA NOSSA</h3>
<p>A época do BTS que a gente dançava Fire KSKSKSKKDKD</p>
</div>

<div class="card">
<h3>UMA COISA QUE COMBINA COM VOCÊ</h3>
<p>Cyber</p>
</div>

</div>

<br>

<button
class="cyber-btn"
onclick="nextPage(7)">
FINALIZAR PROTOCOLO →
</button>

</div>

</section>



<!-- PÁGINA 7 -->

<section class="page" id="page7">

<div class="panel">

<h1 class="final-title">
VOCÊ CHEGOU AO FINAL.
</h1>

<div class="final-box">

<p>✓ ALL FILES UNLOCKED</p>
<p>✓ ACCESS GRANTED</p>
<p>✓ BIRTHDAY PROTOCOL COMPLETE</p>

<h1>FELIZ ANIVERSÁRIO, DIVA. 🩶</h1>

<p>
birthday_protocol.exe foi concluído com sucesso.
</p>

</div>

</div>

</section>



<script>

/* =========================
   TROCA DE PÁGINA
========================= */

function nextPage(number) {

    document.querySelectorAll(".page").forEach(function(page) {
        page.classList.remove("active");
    });

    const target = document.getElementById("page" + number);

    if (target) {
        target.classList.add("active");

        window.scrollTo({
            top: 0,
            behavior: "smooth"
        });
    }
}


/* =========================
   BOTÃO DA MÚSICA
========================= */

function musicChoice(placed) {

    const message = document.getElementById("musicMessage");

    if (placed === true) {

        message.textContent =
        "✓ MÚSICA DETECTADA. ATMOSFERA CYBERPUNK ATIVADA.";

        message.style.display = "block";

        /*
        COLOQUEI = VAI DIRETO PARA A PÁGINA 2
        */

        setTimeout(function() {
            nextPage(2);
        }, 450);

    } else {

        message.textContent =
        "É ORA COLOCAAAAAR !!! 😡😡😡";

        message.style.display = "block";
    }
}


/* =========================
   QUIZ
========================= */

function unlockSystem() {

    const message = document.getElementById("quizMessage");

    message.textContent =
    "✓ ACESSO LIBERADO. PREPARE-SE.";

    setTimeout(function() {
        nextPage(4);
        createMaze();
    }, 700);
}


function wrongPerson() {

    const message = document.getElementById("quizMessage");

    message.textContent =
    "error - seu acesso foi negado, vc não é o destinatário do presente, retire-se imediatamente";
}


/* =========================
   MAZE
========================= */

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

    const maze = document.getElementById("maze");

    maze.innerHTML = "";

    maze.style.gridTemplateColumns =
        "repeat(" + mazeMap[0].length + ", 1fr)";

    for (let y = 0; y < mazeMap.length; y++) {

        for (let x = 0; x < mazeMap[y].length; x++) {

            const cell = document.createElement("div");

            cell.classList.add("cell");

            if (mazeMap[y][x] === "1") {
                cell.classList.add("wall");
            }

            if (x === playerX && y === playerY) {
                cell.classList.add("player");
                cell.title = "VOCÊ";
            }

            if (x === goalX && y === goalY) {
                cell.classList.add("goal");
                cell.title = "PRESENTE";
            }

            maze.appendChild(cell);
        }
    }
}


function movePlayer(dx, dy) {

    const newX = playerX + dx;
    const newY = playerY + dy;

    if (
        newY < 0 ||
        newY >= mazeMap.length ||
        newX < 0 ||
        newX >= mazeMap[0].length
    ) {
        return;
    }

    if (mazeMap[newY][newX] === "1") {
        return;
    }

    playerX = newX;
    playerY = newY;

    createMaze();

    if (playerX === goalX && playerY === goalY) {

        document.getElementById("mazeMessage").textContent =
        "✓ PRESENTE ENCONTRADO!";

        setTimeout(function() {
            nextPage(5);
        }, 800);
    }
}


/* =========================
   TECLADO
========================= */

document.addEventListener("keydown", function(event) {

    if (
        event.key === "ArrowUp" ||
        event.key === "ArrowDown" ||
        event.key === "ArrowLeft" ||
        event.key === "ArrowRight"
    ) {

        event.preventDefault();

        if (event.key === "ArrowUp") {
            movePlayer(0,-1);
        }

        if (event.key === "ArrowDown") {
            movePlayer(0,1);
        }

        if (event.key === "ArrowLeft") {
            movePlayer(-1,0);
        }

        if (event.key === "ArrowRight") {
            movePlayer(1,0);
        }
    }

});

</script>

</body>
</html>
