<!DOCTYPE html>
<html>
<head>
    <title>Login Panel</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="login-box">
    <h2>Login</h2>

    <input type="text" id="username" placeholder="Username">

    <input type="password" id="password" placeholder="Password">

    <button onclick="login()">Login</button>
</div>

<script>
function login() {
    let user = document.getElementById("username").value;
    let pass = document.getElementById("password").value;

    if(user=="admin" && pass=="1234"){
        window.location="dashboard.html";
    }else{
        alert("Wrong Login");
    }
}
</script>

</body>
</html>
<!DOCTYPE html>
<html>
<head>
<title>Dashboard</title>
<link rel="stylesheet" href="style.css">
</head>
<body>

<h1>Work Dashboard</h1>

<div class="dashboard">

<div class="room-box">
<h2>Room Clear</h2>

<input type="text" id="taskInput" placeholder="Add Task">

<button onclick="addTask()">Add</button>

<ul id="taskList"></ul>

</div>

<div class="report-box">

<h2>Report</h2>

<p>Total Completed Work :
<span id="completedCount">0</span></p>

<p>Last Completed Date :
<span id="lastDate">-</span></p>

</div>

</div>

<script src="script.js"></script>

</body>
</html>
body{
font-family:Arial;
background:#f4f4f4;
padding:20px;
}

.login-box{
width:300px;
margin:auto;
background:white;
padding:20px;
border-radius:10px;
}

input{
width:100%;
padding:10px;
margin:10px 0;
}

button{
padding:10px 20px;
background:green;
color:white;
border:none;
cursor:pointer;
}

.dashboard{
display:flex;
gap:20px;
}

.room-box,
.report-box{
background:white;
padding:20px;
border-radius:10px;
width:45%;
}

li{
margin:10px 0;
}
let completed = 0;

function addTask(){

let task = document.getElementById("taskInput").value;

if(task==""){
alert("Task Enter Karo");
return;
}

let li = document.createElement("li");

li.innerHTML = `
${task}
<button onclick="completeTask(this)">
Complete
</button>
`;

document.getElementById("taskList").appendChild(li);

document.getElementById("taskInput").value="";
}

function completeTask(btn){

btn.parentElement.style.textDecoration="line-through";

completed++;

document.getElementById("completedCount").innerText=completed;

let date = new Date();

document.getElementById("lastDate").innerText=
date.toLocaleString();

btn.remove();
}
