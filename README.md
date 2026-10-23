<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>TRTT Heart Tree ❤️ Roksana</title>
<style>
*{margin:0;padding:0;overflow:hidden}
body{background:#020210}
canvas{display:block;width:100vw;height:100vh}
#tap{position:fixed;bottom:22px;width:100%;text-align:center;color:#fff;font-family:sans-serif;font-size:15px}
</style>
</head>
<body>
<canvas id="c"></canvas>
<div id="tap">🌸 Tap to Bloom 🌸 Roksana → Taifa ❤️ Tasrif 🇮🇹🇧🇩</div>
<script>
const C=document.getElementById('c'),X=C.getContext('2d');let W,H;
function R(){W=C.width=innerWidth;H=C.height=innerHeight}R();onresize=R;
let blooms=[],B=[];
class Br{constructor(x,y,a,l,d,col){this.x=x;this.y=y;this.a=a;this.l=l;this.d=d;this.col=col;this.g=0}
step(){if(this.g<this.l){this.g+=this.l*0.045;return false}
if(this.d>0){let nl=this.l*0.7;
if(this.d==4){
B.push(new Br(this.x+Math.cos(this.a)*this.l,this.y+Math.sin(this.a)*this.l,-1.0,95,3,'#ff8ac6'));
B.push(new Br(this.x+Math.cos(this.a)*this.l,this.y+Math.sin(this.a)*this.l,1.0,95,3,'#6ab7ff'));
return true;}
B.push(new Br(this.x+Math.cos(this.a)*this.l,this.y+Math.sin(this.a)*this.l,this.a-0.6, nl,this.d-1,col));
B.push(new Br(this.x+Math.cos(this.a)*this.l,this.y+Math.sin(this.a)*this.l,this.a+0.6, nl,this.d-1,col));
}else{for(let i=0;i<5;i++)blooms.push({x:this.x,y:this.y,vx:(Math.random()-0.5)*1,vy:Math.random()*-1.5,r:Math.random()*3+2,col:col,life:1})}
return true}}
function init(){B=[new Br(W/2,H,-Math.PI/2,150,4,'#e6c29a')];blooms=[]}
init();
function draw(){
X.fillStyle='rgba(2,2,16,0.25)';X.fillRect(0,0,W,H);
B.forEach(b=>{
X.beginPath();X.moveTo(b.x,b.y);X.lineTo(b.x+Math.cos(b.a)*b.g,b.y+Math.sin(b.a)*b.g);
X.strokeStyle=b.col;X.lineWidth=b.d*2.5;X.lineCap='round';X.stroke();
});
blooms.forEach((b,i)=>{
b.x+=b.vx;b.y+=b.vy;b.vy+=0.015;b.life-=0.003;
X.globalAlpha=b.life;X.beginPath();X.arc(b.x,b.y,b.r,0,6.28);X.fillStyle=b.col;X.fill();X.globalAlpha=1;
if(b.life<=0)blooms.splice(i,1);
});
X.font='bold '+(W*0.06)+'px serif';X.textAlign='center';X.fillStyle='rgba(255,255,255,0.9)';
X.fillText('R',W/2,H-70);
X.font=(W*0.04)+'px serif';X.fillStyle='#ff9ec6';X.fillText('Taifa',W*0.25,H*0.42);
X.fillStyle='#8ac6ff';X.fillText('Tasrif',W*0.75,H*0.42);
}
function loop(){let a=false;B.forEach(b=>{if(!b.step())a=true});draw();if(a||blooms.length>0)requestAnimationFrame(loop)}
loop();
C.onclick=()=>{init();loop()};
</script>
</body>
</html>
