# -zel-sitem
kimseye yapılmamıs bir proje
<!DOCTYPE html>
<html>
<head>
<title>Ultimate Aşk Makinesi 💖</title>
<style>
body{
    background: linear-gradient(to bottom, pink, hotpink);
    text-align:center;
    font-family:Arial;
    overflow:hidden;
    margin:0;
}

h1{
    color:white;
    margin-top:40px;
}

button{
    padding:10px 20px;
    font-size:20px;
    margin:20px;
    border:none;
    border-radius:12px;
    cursor:pointer;
    transition:0.3s;
}

#evet{
    background:red;
    color:white;
}

#hayir{
    background:gray;
    color:white;
    position:absolute;
}

#skor{
    color:white;
    font-size:20px;
}

#mesaj{
    color:white;
    font-size:22px;
    margin-top:10px;
}

.kalp{
    position:absolute;
    font-size:25px;
    animation:dus 4s linear infinite;
}

@keyframes dus{
    0%{transform:translateY(-10px);}
    100%{transform:translateY(100vh);}
}

.yakala{
    position:absolute;
    font-size:30px;
    cursor:pointer;
}
</style>
</head>
<body>

<h1>Beni Seviyor musun? 😍</h1>

<button id="evet" onclick="evetTikla()">Evet 💖</button>
<button id="hayir" onclick="hayirTikla()">Hayır 😢</button>

<p id="skor">Skor: 0</p>
<p id="mesaj"></p>

<script>
let skor = 0;
let evetBoyut = 20;

const askCumleleri = [
"Seni düşündüğüm her an kalbim hızlanıyor ❤️",
"Hayatımın en güzel kısmısın 💕",
"Sen benim en güzel hikayemsin ✨",
"Gülüşün dünyama güneş gibi doğuyor ☀️",
"Sonsuza kadar sen 💖",
"Kalbim sadece senin için atıyor 💓",
"İyi ki varsın sevgilim 😍",
"Sen olmadan eksik kalırım 🥺",
"Birlikte yaşlanalım mı? 💍",
"Sana her gün yeniden aşık oluyorum 💘"
];

const hayirMesajlari = [
"Emin misin? 😏",
"Kalbin evet diyor bence 😌",
"Beni sevmiyor musun gerçekten? 💔",
"Son kararın mı bu? 👀",
"Bir daha düşün derim 😎",
"Kaçamazsın bu aşktan 💘",
"Bak kırılıyorum ama 🥺"
];

// HAYIR BUTONU
function hayirTikla(){
    const x = Math.random() * (window.innerWidth - 150);
    const y = Math.random() * (window.innerHeight - 100);

    const buton = document.getElementById("hayir");
    buton.style.left = x + "px";
    buton.style.top = y + "px";

    const rastgele = Math.floor(Math.random()*hayirMesajlari.length);
    buton.innerText = hayirMesajlari[rastgele];
}

// EVET BUTONU
function evetTikla(){
    skor++;
    document.getElementById("skor").innerText = "Skor: " + skor;

    evetBoyut += 4;
    document.getElementById("evet").style.fontSize = evetBoyut + "px";

    const rastgele = Math.floor(Math.random()*askCumleleri.length);
    document.getElementById("mesaj").innerText = askCumleleri[rastgele];

    kalpYagdir();

    if(skor >= 20){
        finalEkran();
    }
}

// KALP YAĞMURU
function kalpYagdir(){
    const kalp = document.createElement("div");
    kalp.classList.add("kalp");
    kalp.innerText = "💖";
    kalp.style.left = Math.random()*window.innerWidth + "px";
    document.body.appendChild(kalp);
    setTimeout(()=>kalp.remove(),4000);
}

// KALP YAKALAMA OYUNU
setInterval(()=>{
    const kalp = document.createElement("div");
    kalp.classList.add("yakala");
    kalp.innerText="❤️";
    kalp.style.left = Math.random()*window.innerWidth+"px";
    kalp.style.top = Math.random()*window.innerHeight+"px";

    kalp.onclick=function(){
        skor+=5;
        document.getElementById("skor").innerText="Skor: "+skor;
        kalp.remove();
    }

    document.body.appendChild(kalp);
    setTimeout(()=>kalp.remove(),2000);
},2000);

// FİNAL
function finalEkran(){
    document.body.innerHTML="<h1 style='color:white;font-size:60px;margin-top:200px;'>SENİ ÇOK SEVİYORUM 💖👑</h1>";
    for(let i=0;i<60;i++){
        const kalp=document.createElement("div");
        kalp.classList.add("kalp");
        kalp.innerText="🎆";
        kalp.style.left=Math.random()*window.innerWidth+"px";
        document.body.appendChild(kalp);
    }
}
</script>

</body>
</html>
