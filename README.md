<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Gallegos Trailers - Estatus Producción</title>
<style>
body{font-family:Arial,Helvetica,sans-serif;background:#f4f4f4;margin:0}
header{background:#111;color:white;padding:20px;text-align:center}
header img{height:70px}
.subtitle{font-size:14px;color:#ccc}
.container{padding:20px}
.grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px}
.station{background:white;border-radius:10px;padding:25px;text-align:center;box-shadow:0 4px 10px rgba(0,0,0,0.15)}
.station h2{font-size:28px;margin-bottom:10px}
.status{font-size:22px;font-weight:bold;padding:10px;border-radius:6px;margin-bottom:10px}
.noiniciado{background:#e74c3c;color:white}
.proceso{background:#f39c12;color:white}
.terminado{background:#27ae60;color:white}
button{padding:10px 15px;margin:5px;border:none;border-radius:6px;font-size:14px;cursor:pointer}
.start{background:#f39c12;color:white}
.finish{background:#27ae60;color:white}
.reset{background:#e74c3c;color:white}
.time{font-size:14px;color:#555;margin-top:5px}
footer{text-align:center;padding:15px;font-size:12px;background:#222;color:#aaa;margin-top:30px}
</style>
</head>
<body>

<header>
<img src="logo.png" alt="Gallegos Trailers">
<h1>ESTATUS DE PRODUCCIÓN - ÁREA HABILITADO</h1>
<div class="subtitle">Sistema de control visual | Departamento Ingeniería de Procesos</div>
</header>

<div class="container">
<div class="grid" id="stations"></div>
</div>

<footer>
Gallegos Trailers | Departamento de Ingeniería de Procesos
</footer>

<script>
const estaciones=[
"Programación",
"Pantógrafo",
"Pulido de Lienzos",
"Seamer",
"Roladora",
"Dobladora",
"Abombadora",
"Cejadora",
"Roladora de Perfiles"
];

const grid=document.getElementById("stations");

estaciones.forEach((nombre,i)=>{
const card=document.createElement("div");
card.className="station";

card.innerHTML=`
<h2>${nombre}</h2>
<div class="status noiniciado" id="status${i}">NO INICIADO</div>

<button class="start" onclick="iniciar(${i})">Iniciar</button>
<button class="finish" onclick="terminar(${i})">Terminar</button>
<button class="reset" onclick="resetear(${i})">Reset</button>

<div class="time" id="inicio${i}">Inicio: -</div>
<div class="time" id="fin${i}">Fin: -</div>
`;

grid.appendChild(card);
});

function hora(){
const d=new Date();
return d.toLocaleString();
}

function iniciar(i){
const status=document.getElementById("status"+i);
status.className="status proceso";
status.innerText="EN PROCESO";
document.getElementById("inicio"+i).innerText="Inicio: "+hora();
}

function terminar(i){
const status=document.getElementById("status"+i);
status.className="status terminado";
status.innerText="TERMINADO";
document.getElementById("fin"+i).innerText="Fin: "+hora();
}

function resetear(i){
const status=document.getElementById("status"+i);
status.className="status noiniciado";
status.innerText="NO INICIADO";
document.getElementById("inicio"+i).innerText="Inicio: -";
document.getElementById("fin"+i).innerText="Fin: -";
}
</script>

</body>
</html>
