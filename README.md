<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Typing Master Pro</title>
<style>
body {
  margin:0; font-family:Arial; background:#0f0f1a; color:#fff; text-align:center;
}
.container { padding:20px; }
button {
  padding:10px 20px; margin:5px; border:none; border-radius:10px;
  background:#6c5ce7; color:white; cursor:pointer;
}
button:hover { background:#a29bfe; }
#textDisplay {
  margin:20px auto; width:80%; padding:20px;
  background:#1e1e2e; border-radius:10px;
}
.correct { color:lightgreen; }
.incorrect { color:red; text-decoration:underline; }
input {
  width:80%; padding:10px; font-size:18px;
}
.stats { margin-top:20px; }
</style>
</head>
<body>
<div class="container">
<h1>Typing Master Pro</h1>
<p>Improve your speed & earn online</p><div>
  <h3>Select Level</h3>
  <button onclick="setLevel('easy')">Easy</button>
  <button onclick="setLevel('medium')">Medium</button>
  <button onclick="setLevel('hard')">Hard</button>
</div><div>
  <h3>Select Time</h3>
  <button onclick="setTime(30)">30 sec</button>
  <button onclick="setTime(60)">60 sec</button>
</div><button onclick="startTest()">Start Test</button>

<div id="textDisplay"></div>
<input id="inputBox" placeholder="Start typing..." disabled /><div class="stats">
  <p>Time: <span id="time">0</span></p>
  <p>WPM: <span id="wpm">0</span></p>
  <p>Accuracy: <span id="accuracy">0</span>%</p>
  <p>Mistakes: <span id="mistakes">0</span></p>
</div><h2 id="result"></h2><hr>
<h2>Training & Skills</h2>
<p>Typing speed helps you earn online via freelancing.</p>
<p>Practice daily to improve accuracy and speed.</p>
<p>Use proper finger placement.</p>
<p>Consistency is key to success.</p></div><script>
let level='easy';
let time=30;
let timer;
let timeLeft;
let text='';
let mistakes=0;

const texts={
 easy:"this is simple typing test practice",
 medium:"Typing is a useful skill for freelancing jobs",
 hard:"Advanced typing includes punctuation, numbers & symbols!"
};

function setLevel(l){ level=l; }
function setTime(t){ time=t; }

function startTest(){
 text=texts[level];
 document.getElementById('textDisplay').innerText=text;
 document.getElementById('inputBox').value='';
 document.getElementById('inputBox').disabled=false;
 document.getElementById('inputBox').focus();
 timeLeft=time;
 mistakes=0;
 timer=setInterval(updateTimer,1000);
}

function updateTimer(){
 if(timeLeft<=0){ endTest(); return; }
 timeLeft--;
 document.getElementById('time').innerText=timeLeft;
 calcStats();
}

function calcStats(){
 let input=document.getElementById('inputBox').value;
 let correct=0;
 mistakes=0;

 for(let i=0;i<input.length;i++){
   if(input[i]===text[i]) correct++;
   else mistakes++;
 }

 let wpm=Math.round((correct/5)/(time/60));
 let acc=Math.round((correct/input.length)*100)||0;

 document.getElementById('wpm').innerText=wpm;
 document.getElementById('accuracy').innerText=acc;
 document.getElementById('mistakes').innerText=mistakes;
}

function endTest(){
 clearInterval(timer);
 document.getElementById('inputBox').disabled=true;
 document.getElementById('result').innerText="Test Completed!";
}
</script></body>
</html>
