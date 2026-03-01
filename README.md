<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Болзооны урилга</title>

<style>
body{
    margin:0;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg,#ff9a9e,#fad0c4);
    font-family:Arial;
    overflow:hidden;
    text-align:center;
    transition:1s;
}
.container{position:relative;}

button{
    padding:12px 25px;
    font-size:18px;
    border:none;
    border-radius:25px;
    cursor:pointer;
    margin:10px;
}

#yesBtn{
    background:#ff4d6d;
    color:white;
}

#noBtn{
    background:white;
    color:#ff4d6d;
    position:absolute;
}

#loveMessage{
    position:absolute;
    color:white;
    font-size:32px;
    display:none;
    z-index:10;
    animation:fadeIn 2s ease-in-out;
}

@keyframes fadeIn{
    from{opacity:0;transform:scale(0.5);}
    to{opacity:1;transform:scale(1);}
}

.heart{
    position:absolute;
    font-size:20px;
    animation:explode 2s ease-out forwards;
}

@keyframes explode{
    0%{transform:translate(0,0) scale(1);opacity:1;}
    100%{transform:translate(var(--x),var(--y)) scale(1.5);opacity:0;}
}
</style>
</head>

<body>

<div class="container" id="mainContent">
<h1>3-р сарын 7-ны өдөр надтай хамт болзоонд явах уу? 💌</h1>
<button id="yesBtn">Тийм 💖</button>
<button id="noBtn">Үгүй 😢</button>
</div>

<div id="loveMessage">
Баярлалаа хайраа 💕 <br>
Уулзах өдрөө тэсэн ядан хүлээж байна ❤️
</div>

<script>
const noBtn=document.getElementById("noBtn");
const yesBtn=document.getElementById("yesBtn");
const mainContent=document.getElementById("mainContent");
const loveMessage=document.getElementById("loveMessage");

// Үгүй товч зугтаах
noBtn.addEventListener("mouseover",()=>{
    const x=Math.random()*(window.innerWidth-100);
    const y=Math.random()*(window.innerHeight-50);
    noBtn.style.left=x+"px";
    noBtn.style.top=y+"px";
});

// Тийм дарахад scene солигдох
yesBtn.addEventListener("click",()=>{
    mainContent.style.display="none";
    document.body.style.background="black";
    loveMessage.style.display="block";
    createHeartFirework();
    setInterval(createHeartFirework,1500);
});

// Зүрхэн Firework
function createHeartFirework(){
    const centerX=window.innerWidth/2;
    const centerY=window.innerHeight/2;

    for(let i=0;i<80;i++){
        let heart=document.createElement("div");
        heart.classList.add("heart");
        heart.innerHTML="❤️";

        heart.style.left=centerX+"px";
        heart.style.top=centerY+"px";

        const angle=Math.random()*2*Math.PI;
        const radius=Math.random()*300;

        const x=Math.cos(angle)*radius+"px";
        const y=Math.sin(angle)*radius+"px";

        heart.style.setProperty("--x",x);
        heart.style.setProperty("--y",y);

        document.body.appendChild(heart);

        setTimeout(()=>{heart.remove();},2000);
    }
}
</script>

</body>
</html>
