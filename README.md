# presente-aniversario
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Um presentinho para você 🎀</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  background: #fff5f8;
  color: #624653;
  font-family: Georgia, "Times New Roman", serif;
}

button {
  font-family: inherit;
}

.container {
  width: min(92%, 650px);
  margin: auto;
  padding: 35px 0 50px;
}

.hero {
  position: relative;
  overflow: hidden;
  text-align: center;
  padding: 45px 25px;
  border-radius: 30px;
  background: linear-gradient(145deg, #fffafd, #ffeef5);
  border: 1px solid #f1d3df;
  box-shadow: 0 10px 30px rgba(170, 100, 130, 0.10);
}

.decor {
  position: absolute;
  font-size: 24px;
  animation: float 3s ease-in-out infinite;
}

.d1 { top: 20px; left: 12%; }
.d2 { top: 30px; right: 12%; animation-delay: .8s; }
.d3 { bottom: 25px; left: 18%; animation-delay: 1.4s; }
.d4 { bottom: 20px; right: 18%; animation-delay: 2s; }

@keyframes float {
  50% {
    transform: translateY(-8px) rotate(5deg);
  }
}

.ribbon {
  font-size: 55px;
}

h1 {
  color: #b86f8e;
  font-size: clamp(32px, 9vw, 55px);
  margin: 12px 0;
}

.subtitle {
  font-size: 16px;
  line-height: 1.7;
  max-width: 500px;
  margin: auto;
}

button {
  border: none;
  border-radius: 30px;
  padding: 14px 22px;
  background: #d88eac;
  color: white;
  font-size: 15px;
  cursor: pointer;
  margin-top: 20px;
  box-shadow: 0 6px 15px rgba(216,142,172,.25);
}

button:active {
  transform: scale(.97);
}

.hidden {
  display: none;
}

.content {
  margin-top: 20px;
  display: grid;
  gap: 16px;
}

.card {
  background: white;
  border: 1px solid #f0d8e1;
  border-radius: 24px;
  padding: 24px;
  box-shadow: 0 6px 20px rgba(170,100,130,.08);
}

.card h2 {
  margin-top: 0;
  color: #b86f8e;
}

.letter {
  line-height: 1.9;
  font-size: 16px;
}

.reveal {
  width: 100%;
  background: #fff5f8;
  color: #ad6382;
  border: 1px dashed #dda8bd;
  box-shadow: none;
}

.surprise {
  background: #fff0f5;
  border-radius: 18px;
  padding: 17px;
  margin-top: 12px;
  text-align: center;
  line-height: 1.7;
}

.memories {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

.memory {
  min-height: 100px;
  border-radius: 18px;
  background: #fff6f9;
  border: 1px solid #f0d8e1;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 15px;
}

.final {
  text-align: center;
  background: linear-gradient(145deg, #fff0f6, #fffafd);
}

.final-big {
  font-size: 42px;
}

.confetti {
  position: fixed;
  top: 45%;
  font-size: 24px;
  pointer-events: none;
  z-index: 999;
  transition: transform 1.2s ease, opacity 1.2s ease;
}

@media (max-width: 450px) {
  .memories {
    grid-template-columns: 1fr;
  }

  .hero {
    padding: 38px 18px;
  }

  .card {
    padding: 20px;
  }
}
</style>
</head>

<body>

<div class="container">

  <section class="hero">

    <span class="decor d1">♡</span>
    <span class="decor d2">✦</span>
    <span class="decor d3">♡</span>
    <span class="decor d4">✧</span>

    <div class="ribbon">🎀</div>

    <h1>Um presentinho para você</h1>

    <p class="subtitle">
      Eu fiz uma coisinha especial para você...
      tem algumas surpresinhas escondidas aqui. ♡
    </p>

    <button id="openButton">
      Abrir meu presente 🎁
    </button>

  </section>


  <main id="content" class="content hidden">

    <section class="card">

      <h2>💌 Uma cartinha</h2>

      <p class="letter">

        Feliz aniversário! 💗

        <br><br>

        Eu espero que seu dia seja cheio de coisas boas,
        risadas, momentos felizes e pessoas que façam
        você se sentir muito amada.

        <br><br>

        Você é uma pessoa muito especial para mim
        e eu queria deixar registrado, de um jeitinho
        diferente, o quanto eu gosto de ter você na minha vida.

        <br><br>

        Que esse novo ano tenha muitos momentos
        que façam você sorrir de verdade. 🎀

        <br><br>

        Com muito carinho,
        <br>
        alguém que te ama muito. ♡

      </p>

    </section>


    <section class="card">

      <h2>🎁 Uma surpresa...</h2>

      <p>
        Tem uma coisinha escondida aqui.
        Você precisa clicar para descobrir! 👀
      </p>

      <button class="reveal" data-target="surprise1">
        Descobrir ♡
      </button>

      <div id="surprise1" class="surprise hidden">

        🫂💗

        <br><br>

        Você desbloqueou um abraço virtual
        gigantesco!

        <br>

        Espero que ele chegue até você mesmo
        estando longe. 🎀

      </div>

    </section>


    <section class="card">

      <h2>🌷 Coisinhas que me lembram você</h2>

      <div class="memories">

        <div class="memory">
          🎧<br>
          Uma música que me lembra você
        </div>

        <div class="memory">
          🍓<br>
          Uma coisa que você ama
        </div>

        <div class="memory">
          📸<br>
          Uma memória nossa
        </div>

        <div class="memory">
          🧸<br>
          Uma coisa que combina com você
        </div>

      </div>

      <p style="font-size:13px;opacity:.65;text-align:center;">
        Essas partes podem ser personalizadas depois. ♡
      </p>

    </section>


    <section class="card">

      <h2>💗 Mais uma surpresa</h2>

      <p>
        Prometo que essa é a última...
        ou talvez não. 👀
      </p>

      <button class="reveal" data-target="surprise2">
        Abrir ✨
      </button>

      <div id="surprise2" class="surprise hidden">

        ✦ ♡ ✧ 💕 ✦ ♡ ✧

        <br><br>

        Você é muito importante para mim.

        <br><br>

        Nunca se esqueça disso, tá? 🎀

      </div>

    </section>


    <section class="card final">

      <div class="final-big">
        🎂💗🎀
      </div>

      <h2>
        Feliz aniversário!
      </h2>

      <p>
        Que seu dia seja tão especial quanto você.
      </p>

      <p>
        Eu te amo muito! ♡
      </p>

      <button id="finalButton">
        Uma última surpresa ✨
      </button>

      <div id="finalSurprise" class="surprise hidden">

        💗 ✦ ♡ ✧ 💕 ✦ ♡ ✧ 💗

        <br><br>

        Feliz aniversário! 🎀

        <br><br>

        Espero que você guarde esse
        presentinho com carinho.

        <br><br>

        ♡♡♡

      </div>

    </section>

  </main>

</div>


<script>

const openButton = document.getElementById("openButton");
const content = document.getElementById("content");

openButton.addEventListener("click", function() {

  content.classList.remove("hidden");

  openButton.textContent = "Presente aberto! 💗";

  openButton.disabled = true;

  content.scrollIntoView({
    behavior: "smooth"
  });

});


const revealButtons =
document.querySelectorAll(".reveal");

revealButtons.forEach(function(button) {

  button.addEventListener("click", function() {

    const target =
    document.getElementById(
      button.dataset.target
    );

    target.classList.remove("hidden");

    button.textContent =
    "Surpresa desbloqueada! ✨";

    button.disabled = true;

  });

});


const finalButton =
document.getElementById("finalButton");

const finalSurprise =
document.getElementById("finalSurprise");

finalButton.addEventListener("click", function() {

  finalSurprise.classList.remove("hidden");

  finalButton.textContent =
  "💗";

  finalButton.disabled = true;


  const symbols = [
    "♡",
    "✦",
    "🎀",
    "💕",
    "✧"
  ];


  for (let i = 0; i < 25; i++) {

    const item =
    document.createElement("span");

    item.className = "confetti";

    item.textContent =
    symbols[i % symbols.length];

    item.style.left =
    (10 + Math.random() * 80) + "%";

    document.body.appendChild(item);


    setTimeout(function() {

      item.style.transform =
      "translateY(" +
      (150 + Math.random() * 300) +
      "px) rotate(" +
      (Math.random() * 180 - 90) +
      "deg)";

      item.style.opacity = "0";

    }, 50);


    setTimeout(function() {

      item.remove();

    }, 1400);

  }

});

</script>

</body>
</html>
