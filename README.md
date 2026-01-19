<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>hack.co</title>
  <style>
    body{
      margin:0;
      height:100vh;
      display:flex;
      flex-direction:column;
      align-items:center;
      justify-content:center;
      background:#111;
      color:#0f0;
      font-family:monospace;
    }
    button{
      padding:10px 20px;
      margin:10px;
      font-size:1.2rem;
      cursor:pointer;
      background:#0f0;
      color:#000;
      border:none;
      border-radius:4px;
    }
    button:hover{background:#0c0;}
    input{
      padding:8px;
      font-size:1rem;
      margin:5px;
    }
    #bar{
      width:250px;
      height:20px;
      border:1px solid #0f0;
      margin-top:15px;
    }
    #fill{
      height:100%;
      width:0%;
      background:#0f0;
      transition:width 2.5s linear;
    }
  </style>
</head>
<body>

<!-- HOME -->
<section id="home">
  <h1>hack.co</h1>
  <button onclick="show('mainMenu')">redirect</button>
</section>

<!-- MAIN MENU -->
<section id="mainMenu" style="display:none;">
  <button onclick="show('changePlacePw')">CHANGE PLACE</button>
  <button onclick="show('freezeTeleportPw')">FREEZE TELEPORT</button>
</section>

<!-- CHANGE PLACE PASSWORD -->
<section id="changePlacePw" style="display:none;">
  <p>enter password</p>
  <input id="cpPw" type="password"/>
  <button onclick="checkCP()">submit</button>
  <p id="cpMsg"></p>
</section>

<!-- CHANGE PLACE ADDRESS -->
<section id="changePlaceAddr" style="display:none;">
  <p>ACCESS GRANTED</p>
  <input id="addr" placeholder="type any address"/>
  <button onclick="loadBar('change')">submit</button>
</section>

<!-- FREEZE TELEPORT PASSWORD -->
<section id="freezeTeleportPw" style="display:none;">
  <p>enter password</p>
  <input id="ftPw" type="password"/>
  <button onclick="checkFT()">submit</button>
  <p id="ftMsg"></p>
</section>

<!-- SELECT PERSON -->
<section id="selectPerson" style="display:none;">
  <p>ACCESS GRANTED</p>
  <p>select a person</p>
  <button onclick="loadBar('freeze')">Random Dude</button>
  <button onclick="loadBar('freeze')">Jane Doe</button>
  <button onclick="loadBar('freeze')">Johnny Stick</button>
  <button onclick="loadBar('freeze')">404 User</button>
</section>

<!-- PROGRESS BAR -->
<section id="progress" style="display:none;">
  <p>THANK YOU FOR HACKING ; REDIRECTING STICKMAN NOW</p>
  <div id="bar"><div id="fill"></div></div>
</section>

<script>
const sections=['home','mainMenu','changePlacePw','changePlaceAddr','freezeTeleportPw','selectPerson','progress'];
function show(id){
  sections.forEach(s=>document.getElementById(s).style.display='none');
  document.getElementById(id).style.display='flex';
  document.getElementById(id).style.flexDirection='column';
  document.getElementById(id).style.alignItems='center';
}
function checkCP(){
  const val=document.getElementById('cpPw').value;
  if(val==='0601'){show('changePlaceAddr'); document.getElementById('cpMsg').textContent='';}
  else{document.getElementById('cpMsg').textContent='ACCESS DENIED';}
}
function checkFT(){
  const val=document.getElementById('ftPw').value;
  if(val==='0601'||val==='0326'){show('selectPerson'); document.getElementById('ftMsg').textContent='';}
  else{document.getElementById('ftMsg').textContent='ACCESS DENIED';}
}
function loadBar(from){
  show('progress');
  const fill=document.getElementById('fill');
  fill.style.width='0%';
  setTimeout(()=>fill.style.width='100%',50);
  setTimeout(()=>show('home'),2600);
}
</script>

</body>
</html>
