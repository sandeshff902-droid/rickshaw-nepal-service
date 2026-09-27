<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>RICKSHAW NEPAL SERVICE</title>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
  font-family:Arial,sans-serif;
}

body{
  background:#f4f5f7;
  color:#171717;
}

header{
  background:#111;
  color:#ffd000;
  text-align:center;
  padding:24px 15px;
}

.logo{
  font-size:45px;
}

header h1{
  font-size:25px;
  margin-top:5px;
}

header p{
  color:white;
  margin-top:6px;
}

.container{
  max-width:470px;
  margin:auto;
  padding:15px;
}

.card{
  background:white;
  padding:20px;
  margin-bottom:15px;
  border-radius:18px;
  box-shadow:0 4px 15px #0001;
}

h2{
  margin-bottom:15px;
}

h3{
  margin:15px 0 8px;
}

input,select{
  width:100%;
  padding:13px;
  margin:6px 0;
  border:1px solid #ddd;
  border-radius:10px;
  font-size:15px;
}

button{
  width:100%;
  padding:14px;
  margin-top:10px;
  border:0;
  border-radius:11px;
  background:#ffd000;
  color:#111;
  font-size:16px;
  font-weight:bold;
}

.dark{
  background:#111;
  color:white;
}

.green{
  background:#18a558;
  color:white;
}

.red{
  background:#e53935;
  color:white;
}

.blue{
  background:#1976d2;
  color:white;
}

.hidden{
  display:none!important;
}

.info{
  background:#fff8d7;
  padding:13px;
  border-radius:11px;
  margin-bottom:10px;
}

.notification{
  background:#fff0a8;
  padding:14px;
  border-radius:12px;
  margin-bottom:12px;
  font-weight:bold;
}

.fare{
  background:#fff7cf;
  padding:17px;
  text-align:center;
  border-radius:12px;
  margin-top:10px;
}

.fare strong{
  font-size:30px;
  color:#d49d00;
}

.ride,
.customer{
  background:#f7f7f7;
  padding:15px;
  border-radius:12px;
  margin-top:10px;
  line-height:1.7;
}

.stat{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:10px;
}

.stat div{
  background:#f3f3f3;
  padding:15px;
  border-radius:12px;
  text-align:center;
}

.stat b{
  font-size:24px;
}

.badge{
  display:inline-block;
  padding:5px 9px;
  border-radius:20px;
  background:#fff0a8;
  font-size:12px;
  font-weight:bold;
}

.small{
  color:#666;
  font-size:13px;
  margin-top:8px;
}
</style>
</head>

<body>

<header>

<div class="logo">🚖</div>

<h1>RICKSHAW NEPAL SERVICE</h1>

<p>
🇳🇵 Bagmati Province • Rs. 20/KM
</p>

</header>


<div class="container">


<!-- LOGIN -->

<div class="card" id="loginPage">

<h2>👋 Welcome</h2>

<button onclick="showCustomerLogin()">
👤 Customer Login
</button>

<button class="dark" onclick="showAdminLogin()">
🛠️ Admin Login
</button>


<div id="customerLogin">

<h3>Customer Login</h3>

<input
id="loginEmail"
placeholder="Email or Phone"
>

<input
id="loginPassword"
type="password"
placeholder="Password"
>

<button onclick="customerLogin()">
Login
</button>

<button class="dark" onclick="showSignup()">
Create Account
</button>

</div>


<div id="adminLogin" class="hidden">

<h3>🛠️ Admin Login</h3>

<input
id="adminID"
placeholder="Admin ID"
>

<input
id="adminPassword"
type="password"
placeholder="Admin Password"
>

<button
class="green"
onclick="adminLogin()"
>
🔐 Login Admin
</button>

<p class="small">
Admin credentials are private.
</p>

</div>

</div>



<!-- SIGN UP -->

<div class="card hidden" id="signupPage">

<h2>📝 Customer Sign Up</h2>

<input
id="signupName"
placeholder="Full Name"
>

<input
id="signupPhone"
placeholder="Phone Number"
>

<input
id="signupEmail"
placeholder="Email"
>

<input
id="signupPassword"
type="password"
placeholder="Create Password"
>


<button onclick="generateOTP()">
📩 Send Verification Code
</button>


<div id="otpArea" class="hidden">

<div class="info">

Demo verification code:

<br><br>

<b
id="otpCode"
style="font-size:25px"
></b>

</div>


<input
id="otpInput"
placeholder="Enter verification code"
>


<button onclick="verifySignup()">
✅ Verify Account
</button>

</div>


<button
class="dark"
onclick="backLogin()"
>
Back
</button>

</div>



<!-- CUSTOMER APP -->

<div
id="customerApp"
class="hidden"
>


<div class="card">

<h2>👤 My Account</h2>

<div
class="info"
id="myAccount"
></div>

</div>



<div class="card">

<h2>
🚖 Book Your Ride
</h2>


<div class="info">

🇳🇵 <b>Bagmati Province</b>

<br>

💰 <b>Rs. 20 per KM</b>

</div>


<div
id="activeWarning"
class="notification hidden"
>

🚫 You already have an active ride.

<br>

Please wait until the current ride
is completed.

</div>



<div id="bookingForm">

<input
id="pickup"
placeholder="📍 Pickup Location"
>

<input
id="destination"
placeholder="📍 Destination"
>

<input
id="distance"
type="number"
min="0.1"
step="0.1"
placeholder="📏 Distance in KM"
>


<div class="fare">

<p>
Estimated Fare
</p>

<strong>

Rs.
<span id="fare">
0
</span>

</strong>

</div>


<button onclick="calculateFare()">
💰 Calculate Fare
</button>


<select id="payment">

<option>
💵 Cash Payment
</option>

<option>
📱 Online QR Payment
</option>

</select>


<button onclick="bookRide()">
🚖 BOOK RIDE
</button>

</div>


<div id="customerStatus"></div>

</div>



<div class="card">

<h2>
🧾 My Ride History
</h2>

<div id="myHistory">
No rides yet.
</div>

</div>


<button
class="red"
onclick="logout()"
>
Logout
</button>

</div>



<!-- ADMIN APP -->

<div
id="adminApp"
class="hidden"
>


<div class="card">

<h2>
🛠️ Admin Dashboard
</h2>


<div class="stat">

<div>

<b id="activeCount">
0
</b>

<p>
Active Rides
</p>

</div>


<div>

<b id="totalCount">
0
</b>

<p>
Total Rides
</p>

</div>

</div>


<div
class="stat"
style="margin-top:10px"
>

<div>

<b id="customerCount">
0
</b>

<p>
Customers
</p>

</div>


<div>

<b id="completedCount">
0
</b>

<p>
Completed
</p>

</div>

</div>

</div>



<div class="card">

<h2>
🔔 Active Ride Requests
</h2>

<div id="adminActiveRides">
No active rides.
</div>

</div>



<div class="card">

<h2>
🧾 Ride History
</h2>

<div id="adminHistory">
No completed rides.
</div>

</div>



<div class="card">

<h2>
👥 Customers
</h2>

<input
id="customerSearch"
placeholder="🔎 Search name, email or phone"
oninput="searchCustomers()"
>

<div id="adminCustomers">
No customers.
</div>

</div>



<div class="card">

<div class="info">

🛡️ Admin credentials are hidden
from the public interface.

</div>


<button
class="red"
onclick="logout()"
>
Logout Admin
</button>

</div>

</div>

</div>



<script>

/* PRIVATE ADMIN LOGIN */

const ADMIN_ID =
"SANDESH@11222";

const ADMIN_PASSWORD =
"SANDESH@11222";


let customers =
JSON.parse(
localStorage.getItem("nr_customers")
|| "[]"
);


let rides =
JSON.parse(
localStorage.getItem("nr_rides")
|| "[]"
);


let currentCustomer =
null;


let generatedOTP =
"";


function saveData(){

localStorage.setItem(
"nr_customers",
JSON.stringify(customers)
);

localStorage.setItem(
"nr_rides",
JSON.stringify(rides)
);

}


function showCustomerLogin(){

document
.getElementById("customerLogin")
.classList.remove("hidden");

document
.getElementById("adminLogin")
.classList.add("hidden");

}


function showAdminLogin(){

document
.getElementById("adminLogin")
.classList.remove("hidden");

document
.getElementById("customerLogin")
.classList.add("hidden");

}


function showSignup(){

document
.getElementById("loginPage")
.classList.add("hidden");

document
.getElementById("signupPage")
.classList.remove("hidden");

}


function backLogin(){

document
.getElementById("signupPage")
.classList.add("hidden");

document
.getElementById("loginPage")
.classList.remove("hidden");

}


function generateOTP(){

let name =
document.getElementById("signupName")
.value.trim();

let phone =
document.getElementById("signupPhone")
.value.trim();

let email =
document.getElementById("signupEmail")
.value.trim()
.toLowerCase();

let password =
document.getElementById("signupPassword")
.value;

if(!name || !phone || !email || !password){

alert("Please fill all information.");

return;

}


if(
customers.some(
c => c.phone === phone
)
){

alert(
"❌ This phone number already has an account."
);

return;

}


if(
customers.some(
c => c.email === email
)
){

alert(
"❌ This email already has an account."
);

return;

}


generatedOTP =
String(
Math.floor(
100000 +
Math.random()*900000
)
);


document
.getElementById("otpCode")
.innerText =
generatedOTP;


document
.getElementById("otpArea")
.classList
.remove("hidden");

}


function verifySignup(){

let code =
document
.getElementById("otpInput")
.value.trim();


if(
code !== generatedOTP
){

alert(
"❌ Wrong verification code."
);

return;

}


let phone =
document
.getElementById("signupPhone")
.value.trim();


let email =
document
.getElementById("signupEmail")
.value.trim()
.toLowerCase();


if(
customers.some(
c => c.phone === phone
)
){

alert(
"❌ Phone number already registered."
);

return;

}


if(
customers.some(
c => c.email === email
)
){

alert(
"❌ Email already registered."
);

return;

}


let customer = {

id:
"CUS" + Date.now(),

name:
document
.getElementById("signupName")
.value.trim(),

phone:
phone,

email:
email,

password:
document
.getElementById("signupPassword")
.value

};


customers.push(customer);

saveData();


alert(
"✅ Account created successfully!"
);


generatedOTP = "";

backLogin();

}


function customerLogin(){

let login =
document
.getElementById("loginEmail")
.value.trim()
.toLowerCase();


let password =
document
.getElementById("loginPassword")
.value;


let customer =
customers.find(

c =>

(
c.email === login ||
c.phone === login
)

&&

c.password === password

);


if(!customer){

alert(
"❌ Wrong Email/Phone or Password."
);

return;

}


currentCustomer =
customer;


document
.getElementById("loginPage")
.classList
.add("hidden");


document
.getElementById("customerApp")
.classList
.remove("hidden");


loadCustomer();

}


function adminLogin(){

let id =
document
.getElementById("adminID")
.value.trim();


let password =
document
.getElementById("adminPassword")
.value;


if(
id === ADMIN_ID &&
password === ADMIN_PASSWORD
){

document
.getElementById("loginPage")
.classList
.add("hidden");


document
.getElementById("adminApp")
.classList
.remove("hidden");


loadAdmin();

}else{

alert(
"❌ Wrong Admin ID or Password."
);

}

}


function getActiveRide(customerID){

return rides.find(

r =>

r.customerID === customerID
&&
r.status !== "Completed"

);

}


function loadCustomer(){

document
.getElementById("myAccount")
.innerHTML =

`
<b>👤 ${currentCustomer.name}</b>
<br>
📱 ${currentCustomer.phone}
<br>
📧 ${currentCustomer.email}
<br>
🆔 ${currentCustomer.id}
`;


let active =
getActiveRide(
currentCustomer.id
);


if(active){

document
.getElementById("activeWarning")
.classList
.remove("hidden");


document
.getElementById("bookingForm")
.classList
.add("hidden");


document
.getElementById("customerStatus")
.innerHTML =

`
<div class="notification">

🚖 Active Ride

<br>

Status:
<b>${active.status}</b>

<br>

📍 ${active.pickup}
→
${active.destination}

<br>

💰 Rs. ${active.fare}

</div>
`;

}else{

document
.getElementById("activeWarning")
.classList
.add("hidden");


document
.getElementById("bookingForm")
.classList
.remove("hidden");


document
.getElementById("customerStatus")
.innerHTML = "";

}


showMyHistory();

}


function calculateFare(){

let d =
Number(
document
.getElementById("distance")
.value
);


if(d <= 0){

alert(
"Enter distance first."
);

return;

}


document
.getElementById("fare")
.innerText =
d * 20;

}


function bookRide(){

let active =
getActiveRide(
currentCustomer.id
);


if(active){

alert(
"🚫 You already have an active ride."
);

return;

}


let pickup =
document
.getElementById("pickup")
.value.trim();


let destination =
document
.getElementById("destination")
.value.trim();


let distance =
Number(
document
.getElementById("distance")
.value
);


let payment =
document
.getElementById("payment")
.value;


if(
!pickup ||
!destination ||
distance <= 0
){

alert(
"Please enter all ride details."
);

return;

}


let ride = {

id:
"RIDE" + Date.now(),

customerID:
currentCustomer.id,

customerName:
currentCustomer.name,

phone:
currentCustomer.phone,

email:
currentCustomer.email,

pickup:
pickup,

destination:
destination,

distance:
distance,

fare:
distance * 20,

payment:
payment,

status:
"Pending",

createdAt:
new Date().toLocaleString()

};


rides.push(ride);

saveData();


alert(
"🚖 Ride booked! Admin has received the request."
);


loadCustomer();

}


function showMyHistory(){

let list =
rides.filter(
r =>
r.customerID ===
currentCustomer.id
);


let box =
document
.getElementById("myHistory");


if(!list.length){

box.innerHTML =
"No rides yet.";

return;

}


box.innerHTML =

list
.slice()
.reverse()
.map(

r =>

`
<div class="ride">

<b>
🚖 ${r.id}
</b>

<br>

<span class="badge">
${r.status}
</span>

<br>

📍 ${r.pickup}
→
${r.destination}

<br>

📏 ${r.distance} KM

<br>

💰 Rs. ${r.fare}

<br>

💳 ${r.payment}

<br>

<span class="small">
${r.createdAt}
</span>

</div>
`

)
.join("");

}


function loadAdmin(){

customers =
JSON.parse(
localStorage.getItem("nr_customers")
|| "[]"
);


rides =
JSON.parse(
localStorage.getItem("nr_rides")
|| "[]"
);


let active =
rides.filter(
r =>
r.status !== "Completed"
);


let completed =
rides.filter(
r =>
r.status === "Completed"
);


document
.getElementById("activeCount")
.innerText =
active.length;


document
.getElementById("totalCount")
.innerText =
rides.length;


document
.getElementById("customerCount")
.innerText =
customers.length;


document
.getElementById("completedCount")
.innerText =
completed.length;


showActiveRides();

showHistory();

showCustomers();

}


function showActiveRides(){

let active =
rides.filter(
r =>
r.status !== "Completed"
);


let box =
document
.getElementById("adminActiveRides");


if(!active.length){

box.innerHTML =
"No active rides.";

return;

}


box.innerHTML =

active.map(

r =>

`
<div class="ride">

<b>
🚖 ${r.id}
</b>

<br>

<span class="badge">
${r.status}
</span>

<br><br>

👤 <b>${r.customerName}</b>

<br>

📱 ${r.phone}

<br>

📧 ${r.email}

<br>

📍 ${r.pickup}

<br>

🏁 ${r.destination}

<br>

📏 ${r.distance} KM

<br>

💰 Rs. ${r.fare}

<br>

💳 ${r.payment}


${
r.status === "Pending"

?

`
<button
class="green"
onclick="acceptRide('${r.id}')"
>
✅ Accept Ride
</button>
`

:

""
}


<button
class="blue"
onclick="completeRide('${r.id}')"
>
🏁 Complete Ride
</button>


<button
class="dark"
onclick="callCustomer('${r.phone}')"
>
📞 Call Customer
</button>

</div>

`

)

.join("");

}


function acceptRide(id){

let ride =
rides.find(
r =>
r.id === id
);


if(!ride)return;


ride.status =
"Accepted";


saveData();

loadAdmin();

}


function completeRide(id){

let ride =
rides.find(
r =>
r.id === id
);


if(!ride)return;


ride.status =
"Completed";


saveData();

loadAdmin();


alert(
"🏁 Ride completed. Customer can book another ride."
);

}


function showHistory(){

let list =
rides.filter(
r =>
r.status === "Completed"
);


let box =
document
.getElementById("adminHistory");


if(!list.length){

box.innerHTML =
"No completed rides.";

return;

}


box.innerHTML =

list
.slice()
.reverse()
.map(

r =>

`
<div class="ride">

<b>
🧾 ${r.id}
</b>

<br>

👤 ${r.customerName}

<br>

📍 ${r.pickup}
→
${r.destination}

<br>

💰 Rs. ${r.fare}

<br>

🟢 Completed

</div>
`

)
.join("");

}


function showCustomers(
list = customers
){

let box =
document
.getElementById("adminCustomers");


if(!list.length){

box.innerHTML =
"No customers.";

return;

}


box.innerHTML =

list.map(

c =>

`
<div class="customer">

<b>
👤 ${c.name}
</b>

<br>

🆔 ${c.id}

<br>

📱 ${c.phone}

<br>

📧 ${c.email}

<br>

<button
class="blue"
onclick="callCustomer('${c.phone}')"
>
📞 Call
</button>

</div>
`

)
.join("");

}


function searchCustomers(){

let q =
document
.getElementById("customerSearch")
.value
.toLowerCase();


let filtered =
customers.filter(

c =>

c.name
.toLowerCase()
.includes(q)

||

c.email
.toLowerCase()
.includes(q)

||

c.phone
.includes(q)

);


showCustomers(
filtered
);

}


function callCustomer(phone){

window.location.href =
"tel:" + phone;

}


function logout(){

location.reload();

}

</script>

</body>
</html>
