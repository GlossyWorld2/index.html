<!DOCTYPE html>

<html lang="ru">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width,initial-scale=1">

<title>Glossy World</title>

<style>

*{box-sizing:border-box}

body{margin:0;min-height:100vh;font-family:Arial,sans-serif;color:#164e60;background:linear-gradient(135deg,#a5f3ff,#e5ffff,#7bdcf2);transition:.5s;overflow-x:hidden}

body.dorfic{background:linear-gradient(135deg,#ffbd63,#ffdf9b,#ff923d);color:#793900}

body.eco{background:linear-gradient(135deg,#b5f5c3,#e6ffe5,#69d9b0);color:#175c42}

body.night{background:linear-gradient(135deg,#07152f,#102c58,#315b91);color:#e0f2ff}

.decorations{position:fixed;inset:0;overflow:hidden;pointer-events:none;z-index:-1}

.orb{position:absolute;border-radius:50%;background:radial-gradient(circle at 30% 25%,#fff,#ffffff66,#8deeff55,#ffffff20);border:1px solid #ffffffa8;box-shadow:inset -8px -12px 25px #ffffff44,inset 5px 5px 15px #ffffff99,0 10px 30px #2387a333;animation:float 9s ease-in-out infinite}

.orb:nth-child(1){width:100px;height:100px;left:7%;top:20%}

.orb:nth-child(2){width:48px;height:48px;right:12%;top:14%;animation-delay:2s}

.orb:nth-child(3){width:145px;height:145px;right:5%;top:60%;animation-delay:1s}

.orb:nth-child(4){width:65px;height:65px;left:15%;top:75%;animation-delay:3s}

.orb:nth-child(5){width:28px;height:28px;left:48%;top:45%;animation-delay:4s}

.orb:nth-child(6){width:75px;height:75px;left:55%;top:85%;animation-delay:2s}

@keyframes float{50%{transform:translateY(-25px) rotate(12deg)}}

.stars{position:fixed;inset:0;pointer-events:none;z-index:-1;display:none}

body.night .stars{display:block}

.star{position:absolute;width:3px;height:3px;border-radius:50%;background:white;box-shadow:0 0 8px 3px #8ccfff;animation:twinkle 2s infinite alternate}

.star:nth-child(1){left:10%;top:12%}.star:nth-child(2){left:25%;top:35%}

.star:nth-child(3){left:80%;top:20%}.star:nth-child(4){left:65%;top:65%}

.star:nth-child(5){left:90%;top:78%}.star:nth-child(6){left:40%;top:80%}

.star:nth-child(7){left:55%;top:15%}.star:nth-child(8){left:15%;top:65%}

@keyframes twinkle{to{opacity:1;transform:scale(1.5)}}

.moon{display:none;position:fixed;right:9%;top:18%;width:85px;height:85px;border-radius:50%;background:radial-gradient(circle at 35% 30%,#fff,#cce8ff 65%,#7eb9ec);box-shadow:0 0 30px #a4d9ff,0 0 80px #529cdb88;z-index:-1}

body.night .moon{display:block}

header{text-align:center;padding:35px 15px}

h1{font-size:clamp(30px,7vw,55px);margin:5px;text-shadow:0 3px 10px #fff}

.subtitle{font-size:16px}

nav,.text-controls,.model-controls{display:flex;justify-content:center;flex-wrap:wrap;gap:10px;padding:10px}

button{border:1px solid #ffffffbb;border-radius:18px;padding:12px 17px;font-size:14px;font-weight:bold;color:#14576c;background:linear-gradient(145deg,#ffffffed,#8be9f5aa);box-shadow:0 5px 15px #398da555,inset 0 2px 5px white;cursor:pointer;transition:.25s}

button:active{transform:scale(.94)}

button.active{outline:3px solid #ffffffaa;transform:translateY(-2px)}

body.dorfic button{color:#854000;background:linear-gradient(145deg,#fff1c9,#ffad4d)}

body.eco button{color:#175c42;background:linear-gradient(145deg,#fff,#82edb4)}

body.night button{color:#d9efff;background:linear-gradient(145deg,#355d91,#10284e)}

main{max-width:950px;margin:auto;padding:15px}

.glass{padding:25px;margin:18px 0;border:1px solid #ffffffbb;border-radius:28px;background:linear-gradient(135deg,#ffffff99,#ffffff30);backdrop-filter:blur(15px);-webkit-backdrop-filter:blur(15px);box-shadow:0 12px 30px #287b9250,inset 0 2px 10px #ffffffbb}

body.dorfic .glass{box-shadow:0 12px 30px #a95a2850,inset 0 2px 10px #ffffffbb}

body.eco .glass{box-shadow:0 12px 30px #26885c44,inset 0 2px 10px #ffffffbb}

body.night .glass{background:linear-gradient(135deg,#a4d5ff30,#1a376866);border-color:#a6d9ff99;box-shadow:0 12px 35px #0007,inset 0 2px 12px #c8eaff55}

h2{margin-top:0;font-size:27px}

p{font-size:17px;line-height:1.7}

.page{display:none;animation:appear .5s}

.page.show{display:block}

@keyframes appear{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:translateY(0)}}

body.text-glass h1,body.text-glass h2,body.text-glass p,body.text-glass .subtitle{color:transparent;background:linear-gradient(110deg,#fff,#83eaff,#fff,#b6f8ff);background-clip:text;-webkit-background-clip:text;-webkit-text-stroke:.5px #ffffffbb;filter:drop-shadow(0 2px 5px #279bb977)}

body.text-aero h1,body.text-aero h2,body.text-aero p,body.text-aero .subtitle{color:#087b9d;text-shadow:0 2px 5px #fff,0 4px 8px #5bd5e6}

body.text-dorfic h1,body.text-dorfic h2,body.text-dorfic p,body.text-dorfic .subtitle{color:#c66a16;text-shadow:0 2px 5px #fff0c9,0 4px 8px #ffb45d}

body.dorfic.text-glass h1,body.dorfic.text-glass h2,body.dorfic.text-glass p,body.dorfic.text-glass .subtitle{background:linear-gradient(110deg,#fff,#ffc36e,#fff2d0,#ff9b38);background-clip:text;-webkit-background-clip:text}

body.eco.text-glass h1,body.eco.text-glass h2,body.eco.text-glass p,body.eco.text-glass .subtitle{background:linear-gradient(110deg,#fff,#8affc5,#fff,#72dca8);background-clip:text;-webkit-background-clip:text}

body.night.text-glass h1,body.night.text-glass h2,body.night.text-glass p,body.night.text-glass .subtitle{background:linear-gradient(110deg,#fff,#9bd8ff,#fff,#91baff);background-clip:text;-webkit-background-clip:text}

body.night.text-aero h1,body.night.text-aero h2,body.night.text-aero p,body.night.text-aero .subtitle{color:#a9dfff;text-shadow:0 2px 8px #438bc9}

body.night.text-dorfic h1,body.night.text-dorfic h2,body.night.text-dorfic p,body.night.text-dorfic .subtitle{color:#ffcb8c;text-shadow:0 2px 8px #a85d39}

.model-stage{height:360px;border-radius:25px;overflow:hidden;position:relative;background:radial-gradient(ellipse at 50% 40%,#ffffff,#c5f4ff 55%,#75cce5);border:1px solid #ffffffdd;box-shadow:inset 0 0 35px #ffffffaa,0 8px 25px #368da533;touch-action:none}

body.night .model-stage{background:radial-gradient(ellipse at 50% 40%,#527eb5,#132d58 65%,#06142d)}

body.dorfic .model-stage{background:radial-gradient(ellipse at 50% 40%,#fff1cf,#ffc36c 65%,#e98c38)}

body.eco .model-stage{background:radial-gradient(ellipse at 50% 40%,#edfff1,#a6e9bc 65%,#4bbd8c)}

#threeCanvas{width:100%;height:100%;display:block;touch-action:none}

.model-label{text-align:center;font-weight:bold;margin-top:16px}

.color-row{display:flex;align-items:center;justify-content:center;gap:12px;margin:18px 0;flex-wrap:wrap}

input[type=color]{width:55px;height:42px;border:2px solid white;border-radius:12px;background:transparent;cursor:pointer}

.model-controls button{min-width:105px}

#rgbButton{background:linear-gradient(110deg,#ff5555,#ffbd4a,#f8f65c,#65ed8b,#55dfff,#8c75ff,#ed75e9);color:#173b57;border:1px solid #fff;box-shadow:0 0 15px #a78bfa88,inset 0 2px 6px #fff}

#rgbButton.active{outline:3px solid #fff;box-shadow:0 0 22px #b46dff}

#threeError{display:none;text-align:center;padding:12px;color:#a22;font-weight:bold}

footer{text-align:center;padding:25px;opacity:.8}

</style>

</head>

<body class="text-glass">

<div class="decorations">

<div class="orb"></div><div class="orb"></div><div class="orb"></div>

<div class="orb"></div><div class="orb"></div><div class="orb"></div>

</div>

<div class="stars">

<div class="star"></div><div class="star"></div><div class="star"></div>

<div class="star"></div><div class="star"></div><div class="star"></div>

<div class="star"></div><div class="star"></div>

</div>

<div class="moon"></div>

<header>

<h1>✨ Glossy World ✨</h1>

<div class="subtitle">Добро пожаловать в мир глянца!</div>

</header>

<nav>

<button class="active" onclick="setTheme('aero',this)">🌊 Frutiger Aero</button>

<button onclick="setTheme('dorfic',this)">🧡 Dorfic</button>

<button onclick="setTheme('eco',this)">🌿 Frutiger Eco</button>

<button onclick="setTheme('night',this)">🌙 Frutiger Night</button>

<button onclick="setTheme('models',this)">💎 3D Models</button>

</nav>

<main>

<div class="glass">

<h2>✨ Настройка текста</h2>

<p>Выбери оформление надписей:</p>

<div class="text-controls">

<button class="active" onclick="setText('glass',this)">💎 Стеклянный</button>

<button onclick="setText('aero',this)">🌊 Aero</button>

<button onclick="setText('dorfic',this)">🧡 Dorfic</button>

</div>

</div>

<section id="aero" class="page show">

<div class="glass">

<h2>🌊 Что такое Frutiger Aero?</h2>

<p>Frutiger Aero — эстетика середины 2000-х и начала 2010-х годов. Она сочетает голубые и зелёные оттенки, прозрачное стекло, блестящие поверхности, воду, природу и футуристические интерфейсы.</p>

<p>Это атмосфера старых операционных систем, красивых обоев, пузырьков, глянцевых кнопок и технологий будущего.</p>

</div>

<div class="glass"><h2>💧 Атмосфера 2000s</h2><p>Прозрачные окна, голубые градиенты, отражения и мягкие блики создают настроение технологичного будущего.</p></div>

</section>

<section id="dorfic" class="page">

<div class="glass"><h2>🧡 Что такое Dorfic?</h2><p>Dorfic — яркая глянцевая эстетика с оранжевыми, янтарными и золотистыми оттенками. Представь блестящие пластиковые поверхности, солнечные отражения и тёплые стеклянные панели.</p><p>Здесь всё наполнено оранжевым светом, тёплыми градиентами и красивым блеском.</p></div>

<div class="glass"><h2>🍊 Оранжевый мир</h2><p>Солнечные блики, янтарные кнопки и прозрачные панели — всё в стиле Dorfic!</p></div>

</section>

<section id="eco" class="page">

<div class="glass"><h2>🌿 Что такое Frutiger Eco?</h2><p>Frutiger Eco — природная эстетика, в которой технологии встречаются с природой: сочная зелень, прозрачная вода, солнечный свет и чистые природные цвета.</p><p>Представь зелёные листья, стеклянные поверхности, капли воды и светлые футуристические интерфейсы.</p></div>

<div class="glass"><h2>🍃 Природа и технологии</h2><p>Зелёные оттенки, мягкие отражения, свежесть и ощущение экологичного будущего.</p></div>

</section>

<section id="night" class="page">

<div class="glass"><h2>🌙 Что такое Frutiger Night?</h2><p>Frutiger Night — ночная интерпретация глянцевой эстетики. Тёмно-синие оттенки, сияющие звёзды, лунный свет и прозрачные стеклянные поверхности создают атмосферу цифровой ночи.</p><p>Представь ночной город, голубые огни, светящиеся пузырьки и гладкие отражающие панели.</p></div>

<div class="glass"><h2>🌌 Ночная атмосфера</h2><p>Мягкое свечение, глубокие синие цвета, серебристые блики и звёздное небо — всё напоминает футуристический интерфейс из далёкого будущего.</p></div>

</section>

<section id="models" class="page">

<div class="glass">

<h2>💎 3D Glossy Models</h2>

<p>Добро пожаловать в коллекцию блестящих 3D-объектов! Выбирай модель, меняй цвет и наблюдай за вращением.</p>

<div class="model-stage" id="stage"><canvas id="threeCanvas"></canvas></div>

<div class="model-label" id="modelName">💎 Стеклянная сфера</div>

<div class="model-controls">

<button class="active" onclick="selectModel('sphere',this)">🔮 Сфера</button>

<button onclick="selectModel('cube',this)">🧊 Куб</button>

<button onclick="selectModel('crystal',this)">💎 Кристалл</button>

<button onclick="selectModel('ring',this)">🪩 Кольцо</button>

<button onclick="selectModel('google',this)">🌈 Google G</button>

<button onclick="selectModel('windows',this)">🪟 Windows</button>

</div>

<div class="color-row">

<label for="colorPicker">🎨 Цвет модели:</label>

<input id="colorPicker" type="color" value="#4de3ef">

<button id="rgbButton" onclick="toggleRGB()">🌈 RGB переливание: ВЫКЛ</button>

<button onclick="toggleRotation()" id="rotateButton">⏸ Пауза</button>

</div>

<div id="threeError"></div>

</div>

<div class="glass">

<h2>✨ Коллекция Glossy</h2>

<p>Настоящие трёхмерные объекты с объёмной геометрией, глянцевыми материалами, освещением и отражающими бликами.</p>

</div>

</section>

</main>

<footer>✨ Glossy World · 2000s aesthetic ✨</footer>

<script>

function setTheme(theme,button){

document.body.classList.remove('dorfic','eco','night');

if(['dorfic','eco','night'].includes(theme))document.body.classList.add(theme);

document.querySelectorAll('nav button').forEach(b=>b.classList.remove('active'));

button.classList.add('active');

document.querySelectorAll('.page').forEach(p=>p.classList.remove('show'));

document.getElementById(theme).classList.add('show');

window.dispatchEvent(new Event('resize'));

}

function setText(style,button){

document.body.classList.remove('text-glass','text-aero','text-dorfic');

document.body.classList.add('text-'+style);

document.querySelectorAll('.text-controls button').forEach(b=>b.classList.remove('active'));

button.classList.add('active');

}

const names={

sphere:'🔮 Стеклянная сфера',

cube:'🧊 Глянцевый куб',

crystal:'💎 Кристалл',

ring:'🪩 Глянцевое кольцо',

google:'💎 Стеклянный Google G',

windows:'🪟 Стеклянный Windows'

};

function selectModel(name,button){

if(window.buildGlossyModel)window.buildGlossyModel(name);

document.getElementById('modelName').textContent=names[name];

document.querySelectorAll('.model-controls button').forEach(b=>b.classList.remove('active'));

button.classList.add('active');

}

window.rotating=true;

function toggleRotation(){

window.rotating=!window.rotating;

document.getElementById('rotateButton').textContent=window.rotating?'⏸ Пауза':'▶ Вращать';

}

document.getElementById('colorPicker').addEventListener('input',function(){

if(window.setGlossyColor)window.setGlossyColor(this.value);

});

function toggleRGB(){if(window.toggleGlossyRGB)window.toggleGlossyRGB();}

</script>

<script type="module">

import * as THREE from "https://esm.sh/three@0.170.0";

const stage=document.getElementById("stage");

const canvas=document.getElementById("threeCanvas");

const errorBox=document.getElementById("threeError");

const colorPicker=document.getElementById("colorPicker");

const rgbButton=document.getElementById("rgbButton");

let scene,camera,renderer,object;

let materials=[];

let currentColor=colorPicker.value;

let dragging=false,lastX=0,lastY=0;

let rotationX=-0.15,rotationY=0;

let targetX=-0.15,targetY=0;

let rgbEnabled=false,rgbHue=0;

try{

scene=new THREE.Scene();

camera=new THREE.PerspectiveCamera(38,1,.1,100);

camera.position.set(0,2.2,6.5);

camera.lookAt(0,0,0);

renderer=new THREE.WebGLRenderer({canvas,antialias:true,alpha:true});

renderer.setPixelRatio(Math.min(window.devicePixelRatio||1,2));

renderer.outputColorSpace=THREE.SRGBColorSpace;

renderer.toneMapping=THREE.ACESFilmicToneMapping;

renderer.toneMappingExposure=1.25;

const envCanvas=document.createElement("canvas");

envCanvas.width=1024;envCanvas.height=512;

const ctx=envCanvas.getContext("2d");

const gradient=ctx.createLinearGradient(0,0,0,512);

gradient.addColorStop(0,"#bceeff");

gradient.addColorStop(.35,"#ffffff");

gradient.addColorStop(.65,"#75c9e8");

gradient.addColorStop(1,"#164e75");

ctx.fillStyle=gradient;ctx.fillRect(0,0,1024,512);

ctx.fillStyle="#ffffff";

ctx.fillRect(100,75,150,190);

ctx.fillRect(390,35,100,220);

ctx.fillRect(700,90,190,150);

ctx.fillStyle="#a7f1ff";ctx.fillRect(280,280,180,55);

ctx.fillStyle="#e2fcff";ctx.fillRect(560,300,240,35);

const envTexture=new THREE.CanvasTexture(envCanvas);

envTexture.mapping=THREE.EquirectangularReflectionMapping;

envTexture.colorSpace=THREE.SRGBColorSpace;

scene.environment=envTexture;

scene.environmentIntensity=1.4;

scene.add(new THREE.HemisphereLight(0xffffff,0x5797b0,2.2));

const keyLight=new THREE.DirectionalLight(0xffffff,3.5);

keyLight.position.set(4,6,5);scene.add(keyLight);

const fillLight=new THREE.PointLight(0x7beaff,80);

fillLight.position.set(-4,2,3);scene.add(fillLight);

const backLight=new THREE.PointLight(0xffffff,100);

backLight.position.set(1,3,-4);scene.add(backLight);

const bottomLight=new THREE.PointLight(0x4ddfff,40);

bottomLight.position.set(0,-3,2);scene.add(bottomLight);

const platform=new THREE.Mesh(

new THREE.CylinderGeometry(1.8,1.8,.12,96),

new THREE.MeshPhysicalMaterial({color:0x9ceeff,metalness:.25,roughness:.16,clearcoat:1,transparent:true,opacity:.65})

);

platform.position.y=-1.45;scene.add(platform);

const platformRing=new THREE.Mesh(

new THREE.TorusGeometry(1.55,.025,12,100),

new THREE.MeshBasicMaterial({color:0xffffff})

);

platformRing.rotation.x=Math.PI/2;

platformRing.position.y=-1.37;scene.add(platformRing);

function makeMaterial(){

const mat=new THREE.MeshPhysicalMaterial({

color:currentColor,metalness:0,roughness:.025,

transmission:.88,thickness:1.15,ior:1.25,

clearcoat:1,clearcoatRoughness:.015,

envMapIntensity:2.1,

attenuationColor:new THREE.Color(currentColor),

attenuationDistance:3.5

});

materials.push(mat);return mat;

}

function addGlassMesh(group,geometry){

const mesh=new THREE.Mesh(geometry,makeMaterial());

group.add(mesh);return mesh;

}

/* ИСПРАВЛЕННЫЙ ОБЪЁМНЫЙ GOOGLE G */

function buildGoogle(group){

const radius=.88;

const tubeRadius=.15;

const points=[];

/* Открытая дуга справа */

const start=Math.PI/4;

const end=Math.PI*7/4;

for(let i=0;i<=180;i++){

const angle=start+(end-start)*i/180;

points.push(new THREE.Vector3(

radius*Math.cos(angle),

radius*Math.sin(angle),

0

));

}

const curve=new THREE.CatmullRomCurve3(points);

const ringGeometry=new THREE.TubeGeometry(

curve,220,tubeRadius,32,false

);

addGlassMesh(group,ringGeometry);

/* Перекладина буквы G */

const bar=addGlassMesh(

group,new THREE.BoxGeometry(.78,.29,.30)

);

bar.position.set(.43,0,.02);

/* Правый конец перекладины */

const vertical=addGlassMesh(

group,new THREE.BoxGeometry(.29,.48,.30)

);

vertical.position.set(.69,-.20,.02);

}

function buildWindows(group){

const positions=[[-.48,.48],[.48,.48],[-.48,-.48],[.48,-.48]];

positions.forEach(([x,y])=>{

const shape=new THREE.Shape();

const w=.83,h=.76,skew=.10;

shape.moveTo(-w/2,-h/2);

shape.lineTo(w/2,-h/2+skew);

shape.lineTo(w/2,h/2+skew);

shape.lineTo(-w/2,h/2);

shape.closePath();

const geometry=new THREE.ExtrudeGeometry(shape,{

depth:.22,bevelEnabled:true,bevelSegments:8,steps:1,

bevelSize:.055,bevelThickness:.055

});

const pane=addGlassMesh(group,geometry);

pane.position.set(x,y,0);

});

group.rotation.y=-.12;

}

function disposeObject(group){

if(!group)return;

const geometries=new Set(),oldMaterials=new Set();

group.traverse(child=>{

if(child.geometry)geometries.add(child.geometry);

if(child.material){

if(Array.isArray(child.material))child.material.forEach(m=>oldMaterials.add(m));

else oldMaterials.add(child.material);

}

});

geometries.forEach(g=>g.dispose());

oldMaterials.forEach(m=>m.dispose());

}

function buildModel(type){

if(object){scene.remove(object);disposeObject(object);}

object=new THREE.Group();

materials=[];

if(type==="sphere")addGlassMesh(object,new THREE.SphereGeometry(1.25,96,96));

if(type==="cube"){

const mesh=addGlassMesh(object,new THREE.BoxGeometry(1.9,1.9,1.9,2,2,2));

const edges=new THREE.LineSegments(

new THREE.EdgesGeometry(mesh.geometry),

new THREE.LineBasicMaterial({color:0xdfffff,transparent:true,opacity:.7})

);

mesh.add(edges);

}

if(type==="crystal")addGlassMesh(object,new THREE.OctahedronGeometry(1.45,0));

if(type==="ring"){

const mesh=addGlassMesh(object,new THREE.TorusGeometry(1.05,.34,48,120));

mesh.rotation.x=.4;

}

if(type==="google")buildGoogle(object);

if(type==="windows")buildWindows(object);

object.position.y=.1;

scene.add(object);

targetX=-.15;targetY=0;

applyCurrentColor();

}

function applyCurrentColor(){

materials.forEach(mat=>{

mat.color.set(currentColor);

mat.attenuationColor.set(currentColor);

});

}

window.buildGlossyModel=buildModel;

window.setGlossyColor=(color)=>{

currentColor=color;

if(rgbEnabled){

rgbEnabled=false;

rgbButton.classList.remove("active");

rgbButton.textContent="🌈 RGB переливание: ВЫКЛ";

}

applyCurrentColor();

};

window.toggleGlossyRGB=()=>{

rgbEnabled=!rgbEnabled;

rgbButton.classList.toggle("active",rgbEnabled);

rgbButton.textContent=rgbEnabled?

"🌈 RGB переливание: ВКЛ":

"🌈 RGB переливание: ВЫКЛ";

if(!rgbEnabled){

applyCurrentColor();

colorPicker.value=currentColor;

}

};

canvas.addEventListener("pointerdown",event=>{

dragging=true;lastX=event.clientX;lastY=event.clientY;

canvas.setPointerCapture(event.pointerId);

});

canvas.addEventListener("pointermove",event=>{

if(!dragging)return;

const dx=event.clientX-lastX,dy=event.clientY-lastY;

targetY+=dx*.012;targetX+=dy*.012;

targetX=Math.max(-1.35,Math.min(1.35,targetX));

lastX=event.clientX;lastY=event.clientY;

});

function stopDrag(){dragging=false}

canvas.addEventListener("pointerup",stopDrag);

canvas.addEventListener("pointercancel",stopDrag);

function resize(){

const width=stage.clientWidth,height=stage.clientHeight;

if(!width||!height)return;

camera.aspect=width/height;

camera.updateProjectionMatrix();

renderer.setSize(width,height,false);

}

new ResizeObserver(resize).observe(stage);

window.addEventListener("resize",resize);

buildModel("sphere");

resize();

function animate(){

requestAnimationFrame(animate);

if(rgbEnabled){

rgbHue=(rgbHue+.0018)%1;

const rgbColor=new THREE.Color().setHSL(rgbHue,.95,.58);

materials.forEach(mat=>{

mat.color.copy(rgbColor);

mat.attenuationColor.copy(rgbColor);

});

}

if(object){

if(window.rotating&&!dragging)targetY+=.006;

rotationY+=(targetY-rotationY)*.12;

rotationX+=(targetX-rotationX)*.12;

object.rotation.y=rotationY;

object.rotation.x=rotationX;

}

renderer.render(scene,camera);

}

animate();

}catch(error){

errorBox.style.display="block";

errorBox.textContent="Не удалось загрузить 3D. Проверь интернет и поддержку WebGL.";

console.error(error);

}

</script>

</body>

</html>
