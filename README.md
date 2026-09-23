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

body {
    margin: 0;
    background:
        linear-gradient(rgba(255,255,255,.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.025) 1px, transparent 1px),
        #050505;
    background-size: 25px 25px;
    color: #eee;
    font-family: 'Share Tech Mono', monospace;
    min-height: 100vh;
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
        rgba(255,255,255,.018) 4px
    );
    z-index: 999;
}

.page {
    display: none;
    min-height: 100vh;
    padding: 35px 20px;
    justify-content: center;
    align-items: center;
}

.page.active {
    display: flex;
}

.container {
    width: 100%;
    max-width: 850px;
    border: 1px solid #777;
    background: linear-gradient(145deg, #151515, #050505);
    padding: 35px;
    box-shadow:
        0 0 0 1px #222,
        0 0 35px rgba(255,255,255,.08),
        inset 0 0 35px rgba(255,255,255,.025);
}

.system {
    font-size: 12px;
    color: #888;
    letter-spacing: 3px;
    margin-bottom: 15px;
}

h1, h2 {
    font-family: 'Orbitron', sans-serif;
    letter-spacing: 3px;
}

h1 {
    font-size: clamp(25px, 7vw, 50px);
}

h2 {
    font-size: clamp(20px, 5vw, 32px);
}

.subtitle {
    color: #aaa;
    line-height: 1.8;
}

.cyber-text {
    font-family: 'Orbitron', sans-serif;
    text-transform: uppercase;
}

/* BOTÕES */

button {
    font-family: 'Share Tech Mono', monospace;
    cursor: pointer;
}

.cyber-btn {
    margin-top: 25px;
    padding: 13px 20px;
    background: linear-gradient(#ddd, #777);
    border: 1px solid white;
    color: #050505;
    font-weight: bold;
    letter-spacing: 2px;
    box-shadow: 4px 4px 0 #333;
    transition: .15s;
}

.cyber-btn:hover {
    transform: translate(2px, 2px);
    box-shadow: 2px 2px 0 #333;
}

.small-btn {
    margin-top: 25px;
    padding: 8px 13px;
    font-size: 11px;
    background: transparent;
    color: #aaa;
    border: 1px solid #555;
}

/* PÁGINA 1 */

.music-warning {
    border: 1px solid #aaa;
    padding: 25px;
    margin: 25px 0;
    background: #0c0c0c;
}

.warning {
    color: #ddd;
    font-family: 'Orbitron', sans-serif;
    font-size: clamp(16px, 4vw, 24px);
    line-height: 1.5;
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
    background: #101010;
    color: #ccc;
    border: 1px solid #555;
    letter-spacing: 1px;
    transition: .2s;
}

.choice button:hover {
    background: #ddd;
    color: #050505;
    border-color: white;
}

.message-box {
    margin-top: 20px;
    border-left: 2px solid #aaa;
    padding: 15px;
    color: #aaa;
    line-height: 1.7;
    display: none;
}

.message-box.show {
    display: block;
}

/* TEXTO */

.letter {
    line-height: 1.9;
    color: #ccc;
    white-space: pre-line;
    font-size: 15px;
}

.divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, #aaa, transparent);
    margin: 30px 0;
}

/* QUIZ */

.quiz-question {
    border: 1px solid #444;
    padding: 25px;
    margin: 20px 0;
    background: #0b0b0b;
}

.quiz-question p {
    line-height: 1.7;
    color: #ddd;
}

.quiz-options {
    display: grid;
    gap: 10px;
}

.quiz-options button {
    padding: 13px;
    background: #151515;
    color: #bbb;
    border: 1px solid #444;
    text-align: left;
}

.quiz-options button:hover {
    border-color: #aaa;
    color: white;
}

.quiz-result {
    margin-top: 15px;
    min-height: 25px;
    font-weight: bold;
}

/* LABIRINTO */

.maze-wrapper {
    overflow-x: auto;
    padding: 15px 0;
}

#maze {
    display: grid;
    grid-template-columns: repeat(21, 24px);
    grid-template-rows: repeat(21, 24px);
    gap: 2px;
    width: max-content;
    margin: auto;
    padding: 10px;
    background: #080808;
    border: 1px solid #555;
}

.cell {
    width: 24px;
    height: 24px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 8px;
}

.wall {
    background: #777;
    box-shadow: inset 0 0 5px #333;
}

.path {
    background: #111;
}

.player {
    background: #ddd;
    color: #000;
    font-weight: bold;
}

.goal {
    background: #555;
    color: white;
    font-weight: bold;
    font-size: 7px;
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
    background: #171717;
    border: 1px solid #555;
    color: white;
    font-size: 18px;
}

.controls button:hover {
    background: #ddd;
    color: #000;
}

.maze-status {
    text-align: center;
    margin-top: 15px;
    color: #999;
}

/* PRESENTE */

.present {
    text-align: center;
    padding: 20px;
}

.present-box {
    width: 180px;
    height: 130px;
    margin: 35px auto;
    position: relative;
    background: linear-gradient(145deg, #ddd, #555);
    border: 2px solid #aaa;
    box-shadow: 0 0 35px rgba(255,255,255,.15);
    animation: floating 2.5s infinite ease-in-out;
}

.present-box::before {
    content: "";
    position: absolute;
    left: 78px;
    top: 0;
    width: 22px;
    height: 100%;
    background: #333;
}

.present-box::after {
    content: "";
    position: absolute;
    left: -8px;
    top: -18px;
    width: 192px;
    height: 28px;
    background: linear-gradient(#eee, #666);
    border: 2px solid #aaa;
}

@keyframes floating {
    50% {
        transform: translateY(-10px);
    }
}

/* CARDS */

.cards {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 15px;
}

.card {
    border: 1px solid #444;
    padding: 20px;
    background: linear-gradient(145deg, #141414, #090909);
    min-height: 130px;
}

.card-title {
    color: #777;
    font-size: 11px;
    letter-spacing: 2px;
    margin-bottom: 15px;
}

.card-content {
    font-family: 'Orbitron', sans-serif;
    color: #ddd;
    line-height: 1.5;
}

/* FINAL */

.final-screen {
    text-align: center;
}

.final-title {
    font-size: clamp(28px, 8vw, 60px);
}

.final-sub {
    color: #999;
    letter-spacing: 2px;
}

/* ANIMAÇÃO FINAL */

.dance-floor {
    width: 100%;
    height: 260px;
    position: relative;
    margin: 35px auto;
    overflow: hidden;
    border: 1px solid #444;
    background:
        linear-gradient(90deg, transparent 49%, #333 50%, transparent 51%),
        linear-gradient(#111 50%, #080808 50%);
}

.dance-floor::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 70px;
    background:
        linear-gradient(90deg,
        transparent 0 10%,
        #333 10% 11%,
        transparent 11% 20%,
        #333 20% 21%,
        transparent 21% 30%,
        #333 30% 31%,
        transparent 31% 40%,
        #333 40% 41%,
        transparent 41% 50%,
        #333 50% 51%,
        transparent 51% 60%,
        #333 60% 61%,
        transparent 61% 70%,
        #333 70% 71%,
        transparent 71% 80%,
        #333 80% 81%,
        transparent 81%
        );
    transform: perspective(150px) rotateX(35deg);
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

.dancer:nth-child(2) { animation-delay: .15s; }
.dancer:nth-child(3) { animation-delay: .3s; }
.dancer:nth-child(4) { animation-delay: .45s; }

.head {
    width: 27px;
    height: 27px;
    border-radius: 50%;
    background: linear-gradient(145deg, white, #555);
    margin: auto;
}

.body {
    width: 30px;
    height: 55px;
    margin: 4px auto;
    background: linear-gradient(90deg, #aaa, #222, #ddd);
    border-radius: 10px 10px 5px 5px;
}

.leg {
    position: absolute;
    width: 8px;
    height: 38px;
    background: #aaa;
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

.arm {
    position: absolute;
    width: 7px;
    height: 42px;
    background: #888;
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

@keyframes dance {
    from {
        transform: translateY(8px) rotate(-5deg);
    }
    to {
        transform: translateY(-10px) rotate(7deg);
    }
}

.final-message {
    font-family: 'Orbitron', sans-serif;
    font-size: clamp(16px, 4vw, 25px);
    line-height: 1.7;
    margin-top: 25px;
}

/* MOBILE */

@media (max-width: 600px) {
    .container {
        padding: 22px;
    }

    .cards {
        grid-template-columns: 1fr;
    }

    #maze {
        grid-template-columns: repeat(21, 20px);
        grid-template-rows: repeat(21, 20px);
    }

    .cell {
        width: 20px;
        height: 20px;
        font-size: 6px;
    }

    .dancers {
        gap: 12px;
    }
}
</style>
</head>

<body>

<!-- PÁGINA 1 -->
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
O sistema detectou que a atmosfera cyber ainda não foi ativada.
<br><br>
Selecione uma opção para continuar.
</p>

<div class="choice">

<button onclick="musicChoice(1)">
[ OPÇÃO 1 ] — COLOQUEI
</button>

<button onclick="musicChoice(3)">
[ OPÇÃO 3 ] — AINDA NÃO COLOQUEI
</button>

</div>

<div class="message-box" id="musicMessage"></div>

<button class="cyber-btn" id="musicContinue"
onclick="nextPage(2)"
style="display:none;">
PRÓXIMA PÁGINA →
</button>

</div>
</section>


<!-- PÁGINA 2 -->
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


<!-- PÁGINA 3 -->
<section class="page" id="page3">
<div class="container">

<div class="system">
SYSTEM // BIRTHDAY_PROTOCOL // 003
</div>

<h2>IDENTITY_CHECK.EXE</h2>

<p class="subtitle">
Antes de liberar o restante do sistema, algumas informações precisam ser verificadas.
</p>


<div class="quiz-question">

<p>
<strong>01 //</strong><br>
Qual música a gente ficava dançando na TV da sala e a mãe aparecia do lado e a gente fingia que nada tava acontecendo?
</p>

<div class="quiz-options">

<button onclick="answer(this, true)">
Fire — BTS
</button>

<button onclick="answer(this, false)">
Nasa — ATEEZ
</button>

<button onclick="answer(this, false)">
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

<button onclick="answer(this, false)">
Rosa pastel
</button>

<button onclick="answer(this, false)">
Cottagecore
</button>

<button onclick="answer(this, true)">
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

<button onclick="finalQuiz(this, true)">
A aniversariante
</button>

<button onclick="finalQuiz(this, false)">
Não sou a aniversariante
</button>

</div>

<div class="quiz-result"></div>
</div>

</div>
</section>


<!-- PÁGINA 4 -->
<section class="page" id="page4">
<div class="container">

<div class="system">
SYSTEM // BIRTHDAY_PROTOCOL // 004
</div>

<h2>MAZE_PROTOCOL</h2>

<p class="subtitle">
O acesso foi liberado.
<br>
Agora encontre o caminho até o seu presente.
</p>

<div class="maze-wrapper">
<div id="maze"></div>
</div>

<div class="maze-status" id="mazeStatus">
LOCALIZAÇÃO: ENTRADA
</div>

<div class="controls">

<div></div>
<button onclick="move(0,-1)">▲</button>
<div></div>

<button onclick="move(-1,0)">◀</button>
<button onclick="move(0,1)">▼</button>
<button onclick="move(1,0)">▶</button>

</div>

<p class="subtitle" style="text-align:center;font-size:12px;">
Você também pode usar as setas do teclado.
</p>

</div>
</section>


<!-- PÁGINA 5 -->
<section class="page" id="page5">
<div class="container present">

<div class="system">
SYSTEM // BIRTHDAY_PROTOCOL // 005
</div>

<h2>PRESENT.EXE</h2>

<div class="present-box"></div>

<div class="letter" style="text-align:left;">

Eu quero primeiramente te agradecer por ter sido a pessoa que mais me apoiou por todos esses anos 🫶🏼 crescer com vc foi o melhor presente da minha vida, porque eu pude contar com vc sempre, contar tudo que acontece comigo, pedir ajuda com roupas, cabelo (inclusive vc que me ensinou a fazer o cabelo), aprendi a lidar com pessoas, conheci k-pop por vc também, aprendi a ter gostos próprios e etc... Você, diferente de qualquer outro familiar, foi uma das pessoas mais presentes na minha vida, e eu agradeço muito a Deus por isso... Pensando agora, eu não sei o que seria da minha vida sem vc, acho que eu seria uma feia, lascada, sem saber arrumar o cabelo e sem personalidade própria kskskskksksksk😭🫶🏼

Também quero te desejar um ótimo aniversário 🎂, que vc possa ter o melhor aniversário da sua vida, ganhar seu tablet, o melhor bolo e se melhores fotos!!! Vou te obrigar a se arrumar pra tirar fotos aesthetics ok? Vc agora está no auge da idade, idade de diva, então vc vai conquistsr tudo o que vc sonhava em ter 😌

</div>

<button class="small-btn" onclick="nextPage(6)">
CONTINUAR →
</button>

</div>
</section>


<!-- PÁGINA 6 -->
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
<div class="card-content">
Cyber
</div>
</div>

</div>

<button class="small-btn" onclick="nextPage(7)">
FINALIZAR PROTOCOLO →
</button>

</div>
</section>


<!-- PÁGINA 7 -->
<section class="page" id="page7">
<div class="container final-screen">

<div class="system">
SYSTEM // BIRTHDAY_PROTOCOL // 007
</div>

<h1 class="final-title">
VOCÊ CHEGOU AO FINAL.
</h1>

<p class="final-sub">
✓ ALL FILES UNLOCKED<br>
✓ ACCESS GRANTED<br>
✓ BIRTHDAY PROTOCOL COMPLETE
</p>

<div class="dance-floor">

<div class="dancers">

<div class="dancer">
<div class="head"></div>
<div class="body"></div>
<div class="arm left"></div>
<div class="arm right"></div>
<div class="leg left"></div>
<div class="leg right"></div>
</div>

<div class="dancer">
<div class="head"></div>
<div class="body"></div>
<div class="arm left"></div>
<div class="arm right"></div>
<div class="leg left"></div>
<div class="leg right"></div>
</div>

<div class="dancer">
<div class="head"></div>
<div class="body"></div>
<div class="arm left"></div>
<div class="arm right"></div>
<div class="leg left"></div>
<div class="leg right"></div>
</div>

<div class="dancer">
<div class="head"></div>
<div class="body"></div>
<div class="arm left"></div>
<div class="arm right"></div>
<div class="leg left"></div>
<div class="leg right"></div>
</div>

</div>
</div>

<div class="final-message">
FELIZ ANIVERSÁRIO, DIVA. 🩶
</div>

<p class="subtitle">
birthday_protocol.exe foi concluído com sucesso.
</p>

</div>
</section>


<script>

/* NAVEGAÇÃO */

function nextPage(number) {

    document.querySelectorAll(".page").forEach(function(page) {
        page.classList.remove("active");
    });

    document.getElementById("page" + number).classList.add("active");

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });

    if (number === 4) {
        createMaze();
    }
}


/* PÁGINA 1 */

function musicChoice(option) {

    const message = document.getElementById("musicMessage");
    const continueButton = document.getElementById("musicContinue");

    if (option === 1) {

        message.innerText =
        "✓ MÚSICA DETECTADA. Atmosfera cyberpunk ativada. Pode continuar.";

        message.classList.add("show");
        continueButton.style.display = "inline-block";

    } else {

        message.innerText =
        "É ORA COLOCAAAAAR !!! 😡😡😡";

        message.classList.add("show");
        continueButton.style.display = "none";
    }
}


/* QUIZ */

function answer(button, correct) {

    const result = button.parentElement.nextElementSibling;

    if (correct) {

        result.innerText = "✓ CORRETO. Acesso mantido.";
        result.style.color = "#ddd";

    } else {

        result.innerText = "✕ ERRO. Tenta de novo 😭";
        result.style.color = "#888";
    }
}


function finalQuiz(button, correct) {

    const result = button.parentElement.nextElementSibling;

    if (correct) {

        result.innerText = "✓ acesso liberado";

        result.style.color = "#ddd";

        setTimeout(function() {
            nextPage(4);
        }, 800);

    } else {

        result.innerText =
        "error - seu acesso foi negado, vc não é o destinatário do presente, retire-se imediatamente";

        result.style.color = "#aaa";
    }
}


/* LABIRINTO */

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

let player = {
    x: 1,
    y: 1
};

const goal = {
    x: 19,
    y: 19
};


function createMaze() {

    const maze = document.getElementById("maze");

    maze.innerHTML = "";

    player.x = 1;
    player.y = 1;

    for (let y = 0; y < mazeMap.length; y++) {

        for (let x = 0; x < mazeMap[y].length; x++) {

            const cell = document.createElement("div");

            cell.classList.add("cell");

            if (mazeMap[y][x] === "1") {

                cell.classList.add("wall");

            } else {

                cell.classList.add("path");

                if (x === player.x && y === player.y) {

                    cell.classList.add("player");
                    cell.innerText = "VOCÊ";

                }

                if (x === goal.x && y === goal.y) {

                    cell.classList.add("goal");
             
