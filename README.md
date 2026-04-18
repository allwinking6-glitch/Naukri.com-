<!DOCTYPE html>
<html>
<head>
  <title>Naukri Clone - Job Portal</title>

  <style>
    body { margin:0; font-family: Arial; }

    .hidden { display:none; }

    /* LOGIN PAGE */
    .login {
      height:100vh;
      display:flex;
      flex-direction:column;
      justify-content:center;
      align-items:center;
      color:white;
      background:url('https://images.unsplash.com/photo-1492724441997-5dc865305da7') no-repeat center/cover;
      background-color: rgba(0,0,0,0.6);
      background-blend-mode: darken;
    }

    /* MAIN SITE */
    .section { padding:30px; text-align:center; }

    .btn {
      padding:10px 20px;
      background:orange;
      border:none;
      cursor:pointer;
      margin:5px;
    }

    input, textarea {
      padding:10px;
      margin:5px;
      width:220px;
    }

    .flex {
      display:flex;
      flex-wrap:wrap;
      justify-content:center;
    }

    .card {
      border:1px solid #ccc;
      padding:15px;
      margin:10px;
      border-radius:10px;
      width:150px;
    }

    .job {
      border:1px solid #ccc;
      margin:10px;
      padding:10px;
      border-radius:8px;
    }

    .header {
      background:#222;
      color:white;
      padding:10px;
      text-align:center;
    }

  </style>
</head>

<body>

<!-- LOGIN PAGE -->
<div id="loginPage" class="login">
  <h1>Welcome to Job Portal</h1>
  <p>Helping 10,000+ People Get Jobs</p>

  <input id="email" placeholder="Email">
  <input id="password" placeholder="Password">
  <button class="btn" onclick="login()">Login</button>
</div>

<!-- MAIN WEBSITE -->
<div id="mainPage" class="hidden">

  <div class="header">
    <h2>Find Your Dream Job</h2>
  </div>

  <!-- JOB TYPES -->
  <div class="section">
    <h2>Jobs for Everyone</h2>
    <div class="flex">
      <div class="card">Freshers</div>
      <div class="card">Experienced</div>
      <div class="card">Students</div>
      <div class="card">Drivers</div>
      <div class="card">Delivery</div>
      <div class="card">Office Jobs</div>
    </div>
  </div>

  <!-- SEARCH -->
  <div class="section">
    <h2>Search Jobs</h2>
    <input id="search" placeholder="Job Title">
    <input id="location" placeholder="Location">
    <input id="salary" placeholder="Salary">
    <br>
    <button class="btn" onclick="searchJob()">Search</button>
  </div>

  <!-- APPLY -->
  <div class="section">
    <h2>Apply for Job</h2>
    <input id="name" placeholder="Name">
    <input id="job" placeholder="Job Title">
    <input id="loc" placeholder="Location">
    <input id="sal" placeholder="Salary">
    <br>
    <input type="file" id="resume">
    <br>
    <textarea id="opinion" placeholder="What job are you looking for?"></textarea>
    <br>
    <button class="btn" onclick="apply()">Apply</button>
  </div>

  <!-- ADMIN PANEL -->
  <div id="adminPanel" class="section hidden">
    <h2>Admin Panel</h2>
    <button class="btn" onclick="loadData()">View Applications</button>
    <div id="admin"></div>
  </div>

</div>

<script>
let applications = [];

const ADMIN = {
  email: "admin@gmail.com",
  password: "1234"
};

function login(){
  if(email.value === ADMIN.email && password.value === ADMIN.password){
    alert("Welcome Admin");
    loginPage.classList.add("hidden");
    mainPage.classList.remove("hidden");
    adminPanel.classList.remove("hidden");
  } else {
    alert("Welcome User");
    loginPage.classList.add("hidden");
    mainPage.classList.remove("hidden");
  }
}

function searchJob(){
  alert("Searching for: " + search.value);
}

function apply(){
  const file = resume.files[0];

  const data = {
    name: name.value,
    job: job.value,
    location: loc.value,
    salary: sal.value,
    opinion: opinion.value,
    resume: file ? file.name : "No file"
  };

  applications.push(data);
  alert("Application submitted successfully!");
}

function loadData(){
  admin.innerHTML = applications.map(a => `
    <div class="job">
      <h3>${a.name}</h3>
      <p><b>Job:</b> ${a.job}</p>
      <p><b>Location:</b> ${a.location}</p>
      <p><b>Salary:</b> ${a.salary}</p>
      <p><b>Looking For:</b> ${a.opinion}</p>
      <p><b>Resume:</b> ${a.resume}</p>
    </div>
  `).join("");
}
</script>

</body>
</html>
