<!DOCTYPE html>
<html lang="pt-BR">

<head>

<meta charset="UTF-8">

<meta name="viewport"
content="width=device-width, initial-scale=1.0">

<title>ACCESS // BIRTHDAY</title>

<style>

@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800&family=Share+Tech+Mono&display=swap');

*{
box-sizing:border-box;
}

html{
scroll-behavior:smooth;
}

body{

margin:0;

background:
radial-gradient(circle at 50% 20%,#151515 0%,#050505 45%,#000 100%);

color:#e8e8e8;

font-family:'Share Tech Mono',monospace;

min-height:100vh;

overflow-x:hidden;

}

/* SCANLINES */

body::before{

content:"";

position:fixed;

inset:0;

pointer-events:none;

z-index:100;

background:
repeating-linear-gradient(
to bottom,
rgba(255,255,255,.025) 0px,
rgba(255,255,255,.025) 1px,
transparent 1px,
transparent 4px
);

}

/* GRID */

body::after{

content:"";

position:fixed;

inset:0;

pointer-events:none;

opacity:.12;

background-image:
linear-gradient(#222 1px,transparent 1px),
linear-gradient(90deg,#222 1px,transparent 1px);

background-size:40px 40px;

}

/* MAIN */

.container{

width:min(92%,900px);

margin:auto;

padding:50px 0 80px;

}

/* TERMINAL HEADER */

.system{

font-size:12px;

color:#666;

margin-bottom:25px;

letter-spacing:2px;

}

.system span{

color:#00ff9d;

}

/* HERO */

.hero{

position:relative;

padding:55px 30px;

border:1px solid #252525;

background:rgba(5,5,5,.9);

box-shadow:
0 0 30px rgba(0,255,157,.05);

overflow:hidden;

}

.hero::before{

content:"";

position:absolute;

left:0;
top:0;

width:3px;
height:100%;

background:#00ff9d;

box-shadow:
0 0 15px #00ff9d;

}

.hero::after{

content:"";

position:absolute;

top:0;
left:-100%;

width:50%;
height:100%;

background:
linear-gradient(
90deg,
transparent,
rgba(0,255,157,.08),
transparent
);

animation:scan 4s linear infinite;

}

@keyframes scan{

to{
left:150%;
}

}

/* GLITCH TITLE */

.glitch{

font-family:'Orbitron',sans-serif;

font-size:
clamp(30px,8vw,70px);

font-weight:800;

color:#fff;

letter-spacing:3px;

position:relative;

margin:15px 0 25px;

}

.glitch::before,
.glitch::after{

content:attr(data-text);

position:absolute;

left:0;

top:0;

width:100%;

overflow:hidden;

}

.glitch::before{

color:#ff1744;

transform:translate(2px,0);

clip-path:inset(0 0 55% 0);

animation:glitch1 2s infinite linear alternate-reverse;

}

.glitch::after{

color:#00e5ff;

transform:translate(-2px,0);

clip-path:inset(55% 0 0 0);

animation:glitch2 1.7s infinite linear alternate-reverse;

}

@keyframes glitch1{

0%,90%{
transform:translate(2px,0);
}

92%{
transform:translate(-4px,2px);
}

95%{
transform:translate(3px,-2px);
}

100%{
transform:translate(2px,0);
}

}

@keyframes glitch2{

0%,88%{
transform:translate(-2px,0);
}

91%{
transform:translate(5px,-1px);
}

96%{
transform:translate(-3px,2px);
}

100%{
transform:translate(-2px,0);
}

}

/* TEXT */

.intro{

max-width:700px;

line-height:1.9;

color:#aaa;

font-size:15px;

}

.highlight{

color:#00ff9d;

}

/* BUTTON */

button{

background:#050505;

color:#00ff9d;

border:1px solid #00ff9d;

padding:14px 22px;

font-family:'Share Tech Mono',monospace;

font-size:14px;

cursor:pointer;

margin-top:25px;

transition:.2s;

letter-spacing:1px;

}

button:hover{

background:#00ff9d;

color:#000;

box-shadow:
0 0 20px rgba(0,255,157,.4);

}

button:disabled{

opacity:.5;

cursor:default;

}

/* CONTENT */

.content{

margin-top:25px;

display:grid;

gap:20px;

}

.hidden{

display:none;

}

/* CARDS */

.card{

background:rgba(7,7,7,.95);

border:1px solid #292929;

padding:28px;

position:relative;

}

.card::before{

content:"";

position:absolute;

top:0;
left:0;

width:35px;
height:2px;

background:#00ff9d;

box-shadow:0 0 10px #00ff9d;

}

.card h2{

font-family:'Orbitron',sans-serif;

font-size:18px;

color:#00ff9d;

letter-spacing:2px;

margin-top:0;

}

.card p{

line-height:2;

color:#bbb;

}

/* TERMINAL */

.terminal{

background:#020202;

border:1px solid #222;

padding:18px;

font-size:13px;

line-height:1.8;

color:#777;

}

.terminal .green{

color:#00ff9d;

}

/* LETTER */

.letter{

font-size:15px;

white-space:pre-line;

}

/* DATABASE */

.database{

display:grid;

grid-template-columns:
repeat(2,1fr);

gap:12px;

}

.data{

border:1px solid #252525;

padding:20px;

background:#030303;

transition:.2s;

}

.data:hover{

border-color:#00ff9d;

transform:translateY(-2px);

box-shadow:
0 0 15px rgba(0,255,157,.08);

}

.data small{

display:block;

color:#555;

margin-bottom:10px;

font-size:11px;

letter-spacing:1px;

}

.data strong{

color:#eee;

font-size:15px;

}

/* FINAL */

.final{

text-align:center;

padding:50px 25px;

}

.final h2{

font-size:25px;

}

.final .big{

font-family:'Orbitron',sans-serif;

font-size:
clamp(24px,6vw,45px);

color:#fff;

margin:25px 0;

}

/* CURSOR */

.cursor{

display:inline-block;

width:8px;

height:18px;

background:#00ff9d;

margin-left:4px;

animation:blink .8s infinite;

vertical-align:middle;

}

@keyframes blink{

50%{
opacity:0;
}

}

/* MUSIC */

.musicbox{

border:1px solid #292929;

padding:20px;

background:#020202;

}

.musicbox audio{

width:100%;

margin-top:15px;

filter:invert(1);

}

/* MOBILE */

@media(max-width:600px){

.container{

padding-top:25px;

}

.hero{

padding:40px 20px;

}

.database{

grid-template-columns:1fr;

}

.card{

padding:22px 18px;

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

SYSTEM STATUS:

<span>ONLINE</span>

&nbsp; //

&nbsp; ACCESS GRANTED

</div>


<section class="hero">

<div class="system">

USER: SISTER

<br>

FILE: BIRTHDAY.exe

</div>


<h1
class="glitch"
data-text="FELIZ ANIVERSÁRIOOO!">

FELIZ ANIVERSÁRIOOO!

</h1>


<div class="terminal">

<span class="green">></span>

initializing birthday project...

<br>

<span class="green">></span>

loading memories...

<br>

<span class="green">></span>

loading message...

<br>

<span class="green">></span>

project completed after 2 weeks

<br>

<span class="green">></span>

<span id="typing"></span>
<span class="cursor"></span>

</div>


<p class="intro">

Demorou 2 semanas pra eu conseguir fazer esse site,
tem muito código 😭 Mas eu consegui!

<br><br>

Bom, eu achei que um texto no WhatsApp apenas seria
muito simples, quis criar algo que fosse mais especial ❤️

Dediquei meu tempo a video aulas no YT e pedi ajuda
pro Chat GPT pra fazer ele super bonitinho, então eu
espero que tenha dado certo!!

<br><br>

Sem mais enrolação, vamos ao presente virtual
kdkdkkd

</p>


<button id="access">

[ ACCESS PRESENT ]

</button>


</section>



<main id="content" class="content hidden">


<section class="card">

<h2>// MESSAGE.exe</h2>


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

<h2>// PERSONAL DATABASE</h2>


<div class="database">


<div class="data">

<small>MUSIC.exe</small>

<strong>
Nasa — ATEEZ
</strong>

</div>


<div class="data">

<small>THING_SHE_LOVES</small>

<strong>
Eu, claro 😌
</strong>

</div>


<div class="data">

<small>MEMORY_001</small>

<strong>
A época do BTS em que a gente dançava Fire KSKSKSKKDKD
</strong>

</div>


<div class="data">

<small>AESTHETIC_PROFILE</small>

<strong>
CYBER
</strong>

</div>


</div>

</section>



<section class="card">

<h2>// AUDIO TRANSMISSION</h2>


<div class="musicbox">

<p>

TRACK DETECTED:

<br>

<span style="color:#00ff9d">

ENHYPEN — Way Back

</span>

</p>


<audio
id="music"
controls
loop>

<source
src="way-back.mp3"
type="audio/mpeg">

Seu navegador não suporta áudio.

</audio>


</div>


<p style="font-size:12px;color:#555">

// pressione PLAY para iniciar a transmissão

</p>

</section>



<section class="card final">


<div class="system">

FINAL FILE

</div>


<div class="big">

MISSION COMPLETE.
</div>


<p>

Você desbloqueou o presente inteiro.

</p>


<p style="color:#00ff9d">

Happy Birthday, diva.

</p>


<button id="final">

[ EXECUTE FINAL MESSAGE ]

</button>


<div
id="finalMessage"
class="terminal hidden"
style="margin-top:25px">

<span class="green">

> birthday.exe completed successfully

</span>

<br><br>

Obrigada por existir.

<br>

Obrigada por ser minha irmã.

<br>

E obrigada por ter feito parte
de quem eu sou hoje. 🫶🏼

<br><br>

<span class="green">

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

access.textContent="[ PRESENT ACCESSED ]";

access.disabled=true;

content.scrollIntoView({
behavior:"smooth"
});

});



const finalButton =
document.getElementById("final");

const finalMessage =
document.getElementById("finalMessage");


finalButton.addEventListener("click",()=>{

finalMessage.classList.remove("hidden");

finalButton.textContent=
"[ MESSAGE EXECUTED ]";

finalButton.disabled=true;

});



const text =
"welcome, sister...";

const typing =
document.getElementById("typing");

let index=0;


function type(){

if(index < text.length){

typing.textContent +=
text.charAt(index);

index++;

setTimeout(type,70);

}

}


type();


</script>


</body>

</html>
