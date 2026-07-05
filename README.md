<!DOCTYPE html>
<html lang="en">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Hospital Patient Counter</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,sans-serif;
}

body{
    display:flex;
    justify-content:center;
    align-items:center;
    min-height:100vh;
    background:linear-gradient(135deg,#0093E9,#80D0C7);
}

.container{
    width:450px;
    background:white;
    padding:30px;
    border-radius:20px;
    box-shadow:0 15px 35px rgba(0,0,0,0.3);
    animation:fadeIn 1s;
}

@keyframes fadeIn{

    from{
        opacity:0;
        transform:translateY(-30px);
    }

    to{
        opacity:1;
        transform:translateY(0);
    }

}

h1{
    text-align:center;
    color:#0077b6;
    margin-bottom:20px;
}

label{
    display:block;
    margin-top:15px;
    font-weight:bold;
    color:#333;
}

input,
select,
textarea{

    width:100%;
    padding:12px;
    margin-top:6px;
    border:2px solid #ccc;
    border-radius:10px;
    font-size:16px;
    transition:.3s;

}

input:focus,
select:focus,
textarea:focus{

    border-color:#0093E9;
    outline:none;
    box-shadow:0 0 8px #80D0C7;

}

textarea{
    resize:none;
    height:90px;
}

button{

    width:100%;
    padding:14px;
    margin-top:25px;
    border:none;
    border-radius:10px;
    background:linear-gradient(to right,#0093E9,#00C9A7);
    color:white;
    font-size:18px;
    cursor:pointer;
    transition:.3s;

}

button:hover{
    transform:scale(1.05);
}

.result{

    margin-top:25px;
    padding:15px;
    background:#f4f9ff;
    border-left:6px solid #0093E9;
    border-radius:10px;
    display:none;

}

.result h2{
    color:#0077b6;
    margin-bottom:10px;
}

.result p{
    font-size:18px;
    margin:8px 0;
}

.footer{
    text-align:center;
    margin-top:20px;
    color:gray;
    font-size:14px;
}

</style>

</head>

<body>

<div class="container">

<h1>🏥 Hospital Patient Counter</h1>

<label>Total Hospital Beds</label>
<input type="number" id="beds" placeholder="Enter total beds">

<label>Patients Admitted</label>
<input type="number" id="admitted" placeholder="Enter admitted patients">

<label>Patients Discharged</label>
<input type="number" id="discharged" placeholder="Enter discharged patients">

<label>Doctor Availability</label>
<select id="doctor">

<option value="">-- Select Doctor --</option>

<option>Dr. Smith (General Physician)</option>

<option>Dr. John (Cardiologist)</option>

<option>Dr. Emily (Neurologist)</option>

<option>Dr. David (Orthopedic)</option>

<option>Dr. Sarah (Pediatrician)</option>

</select>

<label>Reason for Admission</label>

<textarea id="reason" placeholder="Enter reason for admission"></textarea>

<button onclick="calculatePatients()">Calculate</button>

<div class="result" id="result">

<h2>Hospital Report</h2>

<p id="current"></p>

<p id="available"></p>

<p id="occupancy"></p>

<p id="doctorResult"></p>

<p id="reasonResult"></p>

</div>

<div class="footer">

Hospital Management System

</div>

</div>

<script>

function calculatePatients(){

let beds = Number(document.getElementById("beds").value);

let admitted = Number(document.getElementById("admitted").value);

let discharged = Number(document.getElementById("discharged").value);

let doctor = document.getElementById("doctor").value;

let reason = document.getElementById("reason").value;

if(
document.getElementById("beds").value=="" ||
document.getElementById("admitted").value=="" ||
document.getElementById("discharged").value=="" ||
doctor=="" ||
reason==""
){

alert("Please fill all fields.");

return;

}

if(admitted > beds){

alert("Admitted patients cannot be greater than total beds.");

return;

}

if(discharged > admitted){

alert("Discharged patients cannot be greater than admitted patients.");

return;

}

let current = admitted - discharged;

let available = beds - current;

let occupancy = (current / beds) * 100;

document.getElementById("current").innerHTML =
"👨‍⚕️ Current Patients : <b>"+current+"</b>";

document.getElementById("available").innerHTML =
"🛏️ Available Beds : <b>"+available+"</b>";

document.getElementById("occupancy").innerHTML =
"📊 Bed Occupancy : <b>"+occupancy.toFixed(2)+"%</b>";

document.getElementById("doctorResult").innerHTML =
"👨‍⚕️ Assigned Doctor : <b>"+doctor+"</b>";

document.getElementById("reasonResult").innerHTML =
"🩺 Reason for Admission : <b>"+reason+"</b>";

document.getElementById("result").style.display="block";

}

</script>

</body>
</html>
