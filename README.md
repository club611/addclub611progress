<html lang="ja"><head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="main.js"></script>
  <title>club611progress</title>
  <style>
      *{ margin: 0; padding: 0; }
      body {
        background-color: #000;
        text-align: center;
      }
      p{
        color: #fff;
        margin-top: 60px;
      }
      
      @keyframes example {
     0% {
         transform:rotate(0deg);
     }
     100% {
         transform:rotate(360deg);
     }
  }
  #cv {
     animation:example linear 20s infinite;
  }
  
  form{
    margin-top: 20px;
  }
  </style>
</head>
<body>

<p>
正<span id="title">2.5</span>角形<br>
頂点:<span id="vertex">5</span>個
</p>

<canvas id="cv" width="500" height="500"></canvas>

<p>n/m&gt;2<br>(2より大きな有理数を入力してください)</p>

<form id="select" name="select">
  <input id="number_input" type="number" name="number" class="number">
  <input class="ok" type="button" value="作成" onclick="check()">
</form>

<script>



var cvs = document.getElementById("cv");
var ctx = cvs.getContext("2d");
var r = 200;
var n = 2.5;
var array = [];
var values = [ 2];
var theta = 0;
var addX = 0;
var addY = 0;

var grad  = ctx.createLinearGradient(0, 0, 0, 600);

grad.addColorStop(0,'rgb(255, 255, 0)');
grad.addColorStop(0.5,'rgb(0, 255, 255)');
grad.addColorStop(1,'rgb(255, 0, 255)');

var text = document.getElementById('title').textContent;

var num = Math.floor(n * 100);

for (var j = 0; j < 2 ; j++) {
  if (num % 2 == 0) {
        num = num / 2;
    }
  if (num % 5 == 0) {
        num = num / 5;
    }
}

console.log(num);





theta = theta + Math.PI*2/n;

ctx.beginPath();
ctx.lineWidth = 1;
ctx.strokeStyle = grad;
ctx.moveTo(250 + r*Math.cos(theta),250 + r*Math.sin(theta));

for (let i = 0; i < 5; i++){

  theta = theta + Math.PI*2/n;

  addX = r*Math.cos(theta);
  addY = r*Math.sin(theta);
  ctx.lineTo( 250 + addX , 250 + addY );

}

ctx.stroke();

function check(){

num = Math.floor(document.select.number.value * 10000 + 0.5);

document.getElementById('title').textContent = document.select.number.value;

for (var j = 0; j < 4 ; j++) {
  if (num % 2 == 0) {
        num = num / 2;
    }
  if (num % 5 == 0) {
        num = num / 5;
    }
}

document.getElementById('vertex').textContent = num;

console.log(num);

ctx.clearRect(0, 0, 500, 500);

theta = theta + Math.PI*2/document.select.number.value;

ctx.beginPath();
ctx.strokeStyle = grad;
ctx.moveTo(250 + r*Math.cos(theta),250 + r*Math.sin(theta));

for (let i = 0; i < num ; i++){

  theta = theta + Math.PI*2/document.select.number.value;

  addX = r*Math.cos(theta);
  addY = r*Math.sin(theta);
  ctx.lineTo( 250 + addX , 250 + addY );

}

ctx.stroke();

}




</script>


</body></html>
