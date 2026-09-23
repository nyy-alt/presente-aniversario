<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>BIRTHDAY // SYSTEM</title>

<style>

@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&family=Share+Tech+Mono&display=swap');

*{
    box-sizing:border-box;
}

html{
    scroll-behavior:smooth;
}

body{
    margin:0;
    min-height:100vh;

    background:
        radial-gradient(circle at 50% -10%, #5b5b5b 0%, #202020 20%, #090909 52%, #020202 100%);

    color:#e5e5e5;

    font-family:'Share Tech Mono', monospace;

    overflow-x:hidden;
}


/* ===== METAL GRID ===== */

body::before{
    content:"";
    position:fixed;
    inset:0;
    pointer-events:none;

    background:
        linear-gradient(rgba(255,255,255,.035) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,.035) 1px, transparent 1px);

    background-size:35px 35px;

    opacity:.5;

    z-index:-2;
}


/* ===== METALLIC LIGHT ===== */

body::after{
    content:"";
    position:fixed;
    inset:0;
    pointer-events:none;

    background:
        linear-gradient(
            115deg,
            transparent 15%,
            rgba(255,255,255,.10) 25%,
            transparent 35%
        );

    animation:metalLight 8s linear infinite;

    z-index:-1;
}

@keyframes metalLight{

    0%{
        transform:translateX(-80%);
    }

    100%{
        transform:translateX(80%);
    }

}


/* ===== CONTAINER ===== */

.container{
    width:min(92%,900px);
    margin:auto;
    padding:35px 0 80px;
}


/* ===== SYSTEM ===== */

.system{
    font-size:11px;
    letter-spacing:2px;
    color:#777;
    line-height:1.8;
}

.system span{
    color:#dcdcdc;
}


/* ===== MAIN HERO ===== */

.hero{

    position:relative;

    padding:55px 30px;

    background:
        linear-gradient(
            145deg,
            rgba(255,255,255,.12),
            rgba(255,255,255,.025) 35%,
            rgba(0,0,0,.65)
        );

    border:1px solid #777;

    box-shadow:
        inset 0 1px rgba(255,255,255,.3),
        inset 0 -2px rgba(0,0,0,.9),
        0 20px 60px rgba(0,0,0,.7);

    overflow:hidden;
}


/* metallic top line */

.hero::before{

    content:"";

    position:absolute;

    top:0;
    left:0;

    width:100%;
    height:3px;

    background:
        linear-gradient(
            90deg,
            #222,
            #fff,
            #777,
            #fff,
            #222
        );

    box-shadow:
        0 0 10px rgba(255,255,255,.5);
}


/* ===== SCREWS ===== */

.hero::after{

    content:"✦                         ✦";

    position:absolute;

    top:12px;
    left:18px;

    width:calc(100% - 36px);

    color:#777;

    font-size:12px;

    white-space:pre;

}


/* ===== TITLE ===== */

.glitch{

    position:relative;

    font-family:'Orbitron',sans-serif;

    font-size:clamp(30px,8vw,67px);

    font-weight:900;

    letter-spacing:3px;

    color:#f1f1f1;

    margin:30px 0 25px;

    text-shadow:
        0 1px #fff,
        0 2px #aaa,
        0 3px #555,
        0 7px 15px #000;
}


/* chrome shine */

.glitch::after{

    content:attr(data-text);

    position:absolute;

    left:0;
    top:0;

    width:100%;

    color:transparent;

    background:
        linear-gradient(
            180deg,
            #ffffff 0%,
            #777 22%,
            #eeeeee 38%,
            #333 52%,
            #f5f5f5 68%,
            #555 85%,
            #fff 100%
        );

    -webkit-background-clip:text;
    background-clip:text;

    opacity:.8;

}


/* ===== TERMINAL ===== */

.terminal{

    padding:20px;

    background:
        linear-gradient(
            145deg,
            #1b1b1b,
            #070707
        );

    border:1px solid #555;

    box-shadow:
        inset 0 1px rgba(255,255,255,.12),
        inset 0 -3px rgba(0,0,0,.8);

    color:#999;

    line-height:1.8;

    font-size:13px;
}

.terminal .silver{
    color:#eee;
}


/* ===== INTRO ===== */

.intro{

    max-width:720px;

    margin-top:25px;

    color:#c1c1c1;

    line-height:2;

    font-size:15px;
}


/* ===== BUTTON ===== */

button{

    position:relative;

    background:
        linear-gradient(
            180deg,
            #eeeeee 0%,
            #888 45%,
            #222 50%,
            #777 100%
        );

    border:1px solid #aaa;

    color:#080808;

    padding:14px 25px;

    font-family:'Orbitron',sans-serif;

    font-size:12px;

    font-weight:700;

    letter-spacing:1.5px;

    cursor:pointer;

    margin-top:25px;

    box-shadow:
        inset 0 1px rgba(255,255,255,.8),
        inset 0 -2px rgba(0,0,0,.7),
        0 6px 15px rgba(0,0,0,.6);

    transition:.2s;
}

button:hover{

    filter:brightness(1.25);

    transform:translateY(-2px);

    box-shadow:
        inset 0 1px white,
        0 0 20px rgba(255,255,255,.25);
}

button:active{

    transform:translateY(1px);

}

button:disabled{

    opacity:.45;
}


/* ===== CONTENT ===== */

.content{

    display:grid;

    gap:22px;

    margin-top:25px;
}

.hidden{
    display:none;
}


/* ===== METAL CARDS ===== */

.card{

    position:relative;

    padding:28px;

    background:
        linear-gradient(
            135deg,
            rgba(255,255,255,.09),
            rgba(255,255,255,.025) 35%,
            rgba(0,0,0,.7)
        );

    border:1px solid #555;

    box-shadow:
        inset 0 1px rgba(255,255,255,.18),
        inset 0 -2px rgba(0,0,0,.8),
        0 15px 35px rgba(0,0,0,.45);
}


/* metal corner */

.card::before{

    content:"";

    position:absolute;

    top:0;
    left:0;

    width:45px;
    height:2px;

    background:
        linear-gradient(
            90deg,
            #fff,
            #666,
            transparent
        );
}


/* ===== TITLES ===== */

.card h2{

    font-family:'Orbitron',sans-serif;

    font-size:17px;

    letter-spacing:2px;

    color:#eee;

    margin-top:0;

    text-shadow:
        0 1px #000,
        0 0 8px rgba(255,255,255,.15);
}

.card h2::before{

    content:"[ ";

    color:#777;
}

.card h2::after{

    content:" ]";

    color:#777;
}


/* ===== TEXT ===== */

.card p{

    color:#c2c2c2;

    line-height:2;

}

.letter{

    white-space:pre-line;

    font-size:15px;
}


/* ===== DATABASE ===== */

.database{

    display:grid;

    grid-template-columns:repeat(2,1fr);

    gap:13px;
}

.data{

    padding:20px;

    background:
        linear-gradient(
            145deg,
            #242424,
            #080808
        );

    border:1px solid #4c4c4c;

    box-shadow:
        inset 0 1px rgba(255,255,255,.1),
        inset 0 -2px rgba(0,0,0,.9);

    transition:.2s;
}

.data:hover{

    border-color:#aaa;

    transform:translateY(-2px);

    box-shadow:
        inset 0 1px rgba(255,255,255,.2),
        0 8px 20px rgba(0,0,0,.6);
}

.data small{

    display:block;

    color:#777;

    font-size:10px;

    letter-spacing:2px;

    margin-bottom:10px;
}

.data strong{

    color:#eee;

    font-size:15px;

    line-height:1.6;
}


/* ===== FINAL ===== */

.final{

    text-align:center;

    padding:55px 25px;
}

.final .big{

    font-family:'Orbitron',sans-serif;

    font-size:clamp(25px,6vw,48px);

    font-weight:800;

    color:#eee;

    text-shadow:
        0 2px #777,
        0 4px #222,
        0 10px 20px #000;

    margin:25px 0;
}


/* ===== FINAL MESSAGE ===== */

.final-message{

    margin-top:25px;

    text-align:left;
}


/* ===== MOBILE ===== */

@media(max-width:600px){

    .container{
        padding-top:20px;
    }

    .hero{
        padding:45px 20px;
    }

    .card{
        padding:22px 18px;
    }

    .database{
        grid-template-columns:1fr;
    }

    .glitch{
        letter-spacing:1px;
    }

}

</style>

</head>


<body>


<div class="container">


<div class="system">

SYSTEM // BIRTHDAY PROJECT

<br>

STATUS:
<span>ONLINE</span>

&nbsp; // &nbsp;

MODE:
<span>PERSONAL</span>

</div>


<section class="hero">


<h1
class="glitch"
data-text="FELIZ ANIVERSÁRIOOO!">

FELIZ ANIVERSÁRIOOO!

</h1>


<div class="terminal">

<span class="silver">SYSTEM MESSAGE:</span>

<br>

>

loading birthday project...

<br>

>

2 weeks of development detected.

<br>

>

大量 de código detected.

<br>

>

project successfully completed.

<br><br>

>

<span class="silver">
welcome, sister.
</span>

</div>


<p class="intro">

Demorou 2 semanas pra eu conseguir fazer esse site,
tem muito código 😭 Mas eu consegui!

<br><br>

Bom, eu achei que um texto no whatsapp apenas seria
muito simples, quis criar algo que fosse mais especial ❤️

Dediquei meu tempo a video aulas no YT e pedi ajuda
pro Chat GPT pra fazer ele super bonitinho, então eu espero
que tenha dado certo!!

<br><br>

Sem mais enrolação, vamos ao presente virtual
kdkdkkd

</p>


<button id="access">

[ ACESSAR PRESENTE ]

</button>


</section>



<main id="content" class="content hidden">


<section class="card">


<h2>MESSAGE.EXE</h2>


<p class="letter">

Eu quero primeiramente te agradecer por ter sido a pessoa que mais me apoiou por todos esses anos 🫶🏼 crescer com vc foi o melhor presente da minha vida, porque eu pude contar com vc sempre, contar tudo que acontece comigo, pedir ajuda com roupas, cabelo (inclusive vc que me ensinou a fazer o cabelo), aprendi a lidar com pessoas, conheci k-pop por vc também, aprendi a ter gostos próprios e etc...

Você, diferente de qualquer outro familiar, foi uma das pessoas mais presentes na minha vida, e eu agradeço muito a Deus por isso...

Pensando agora, eu não sei o que seria da minha vida sem vc, acho que eu seria uma feia, lascada, sem saber arrumar o cabelo e sem personalidade própria kskskskksksksk😭🫶🏼

Também quero te desejar um ótimo aniversário 🎂, que vc possa ter o melhor aniversário da sua vida, ganhar seu tablet, o melhor bolo e se melhores fotos!!!

Vou te obrigar a se arrumar pra tirar fotos aesthetics ok?

Vc agora está no auge da idade, idade de diva, então vc vai conquistsr tudo o que vc sonhava em ter 😌

</p>


</section>



<section class="card">


<h2>PERSONAL DATABASE</h2>


<div class="database">


<div class="data">

<small>MÚSICA QUE ME LEMBRA VOCÊ</small>

<strong>
Nasa — ATEEZ
</strong>

</div>


<div class="data">

<small>UMA COISA QUE VOCÊ AMA</small>

<strong>
Eu, claro 😌
</strong>

</div>


<div class="data">

<small>UMA MEMÓRIA NOSSA</small>

<strong>
A época do BTS que a gente dançava Fire KSKSKSKKDKD
</strong>

</div>


<div class="data">

<small>UMA COISA QUE COMBINA COM VOCÊ</small>

<strong>
Cyber
</strong>

</div>


</div>


</section>



<section class="card final">


<div class="system">

FINAL FILE // 001

</div>


<div class="big">

MISSION COMPLETE.
</div>


<p>

Você chegou até o final.

</p>


<p>

Feliz aniversário, diva.

</p>


<button id="final">

[ EXECUTAR MENSAGEM FINAL ]

</button>


<div
id="finalMessage"
class="terminal final-message hidden">

<span class="silver">

> FINAL MESSAGE

</span>

<br><br>

Obrigada por existir.

<br><br>

Obrigada por ser minha irmã.

<br><br>

E obrigada por ter feito parte
de quem eu sou hoje. 🫶🏼

<br><br>

<span class="silver">

> END OF FILE_

</span>

</div>


</section>


</main>


</div>



<script>


const access =
document.getElementById("access");

const content =
document.getElementById("content");


access.addEventListener("click",()=>{

content.classList.remove("hidden");

access.textContent=
"[ PRESENTE ACESSADO ]";

access.disabled=true;

content.scrollIntoView({
behavior:"smooth"
});

});



const finalButton =
document.getElementById("final");
