<!DOCTYPE html>
<html>

 <head>
 <title>Hack Fb-Account.</title>
<style>
html { 
background: black; 
height: 100%; 
overflow: hidden;

 } 
 
 body { 
 margin: 0; 
 padding: 0; 
 height: 100%; 
 
 }
 
  
  
  div { 
  color: red; 
  
  } 
  
  
  
  .innerDiv { 
  position: absolute; 
  left: 50px; 
  top: 150px
  
  }
  
  p {
    
      font-size:25px;
      width:250px;
      border:none;
      background-color:black;
      color:red;
      position:absolute;
      left:6px;
     
  }
  
 #btn {
     background:linear-gradient(to bottom, #000 , #0F0);
     color:red;
     font-height:bold;
     width:55px;
     height:30px;
     border:1px solid #0F0; 
     border-radius:5px;
     position: absolute;
     top: 127px;
     left:95px;
     
 }
 
 #input-text {
     width:245px;
     height: 25px;
     border:1px solid #0F0;
     border-radius:5px;
     color:#0F0;
     background-color:black;
     position: absolute;
     top:87px;
     left:4px;
 }

::placeholder {
  color: red; 
  }
 
</style>
 </head>

 <body>
<script>
const canvas = document.getElementById('Matrix'); 
const context = canvas.getContext('2d');
 
canvas.width = window.innerWidth; 
canvas.height = window.innerHeight; 


const binary = '011010010101000101110101001010101010101010101010110101010100101010101010101010101'; 
const binary2 = '011010010101000101110101001010101010101010101010110101010100101010101010101010101'; 
const binary3 = '011010010101000101110101001010101010101010101010110101010100101010101010101010101'; 

const alphabet = binary + binary2 + binary3; 

const fontSize = 16; 
const columns = canvas.width / fontSize; 

const rainDrops = []; 
for (let x = 0; x < columns; x++) { rainDrops[x] = 1; } 

const draw = () => { context.fillStyle = 'rgba(0, 0, 0, 0.05)'; context.fillRect(0, 0, canvas.width, canvas.height); context.fillStyle = '#0F0'; context.font = fontSize + 'px monospace';

 for (let i = 0; i < rainDrops.length; i++) { const text = alphabet.charAt(Math.floor(Math.random() * alphabet.length)); context.fillText(text, i * fontSize, rainDrops[i] * fontSize);
 
  if (rainDrops[i] * fontSize > canvas.height && Math.random() > 0.975) { rainDrops[i] = 0; } rainDrops[i]++; } }; setInterval(draw, 30);


const input = document.querySelector("#input-text");

function scan(){
  let name = input.value;
  if (name == "") {
    alert("PLEASE ENTER A NAME")
  } 
  
  else {
    document.getElementById("mytext").innerHTML = "Searching Info.....Pls wait"
    
    setTimeout(function () {
        document.getElementById("mytext").innerHTML = "Just-kidding HAHAHA"
    },10000);
    
    setTimeout(function () {
        document.getElementById("mytext").innerHTML = "Asa ka!! HAHA"
    },11000);
  }
};

</script>
 
 <canvas id="Matrix" style="width: 100%; height: 100%;"></canvas>
<script src="./index.js"></script>
<div id="wrapper">
  <div class="innerDiv">
    <span></span>
    <br/>
    <p id="mytext"></p><br>
    <input type="text" id="input-text" placeholder=" Enter The Name" required>
    <input type="submit" id="btn" onclick="scan()">
  </div>
</div>
 
 </body>
 
 </html>
