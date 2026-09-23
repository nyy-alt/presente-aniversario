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
      #666a6
