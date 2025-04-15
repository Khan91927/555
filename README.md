<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Superior Lalazar Public School - Phone Directory</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f4f4f9;
    }
    header {
      background: #004080;
      color: white;
      padding: 20px;
      text-align: center;
    }
    .container {
      padding: 15px;
    }
    input[type="text"], input[type="password"] {
      padding: 10px;
      margin: 10px 5px;
      width: 100%;
      max-width: 300px;
      box-sizing: border-box;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
      background: white;
    }
    th, td {
      padding: 10px;
      border: 1px solid #ccc;
      text-align: left;
    }
    th {
      background: #004080;
      color: white;
    }
    .driver-section {
      background: #e8f0fe;
      padding: 10px;
      margin-bottom: 20px;
      border: 1px solid #004080;
    }
    .fab {
      position: fixed;
      bottom: 20px;
      right: 20px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .fab button {
      background-color: #004080;
      color: white;
      border: none;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      font-size: 20px;
      cursor: pointer;
    }
    .hidden {
      display: none;
    }
    @media screen and (max-width: 600px) {
      th, td {
        font-size: 12px;
      }
      .fab button {
        width: 40px;
        height: 40px;
        font-size: 16px;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>Superior Lalazar Public School Kot Campus</h1>
    <p>Developed by Kamran Khan</p>
  </header>

  <div id="loginSection" class="container">
    <h2>Login Required</h2>
    <input type="password" id="passwordInput" placeholder="Enter password" />
    <button onclick="checkPassword()">Login</button>
    <p id="loginError" style="color:red;"></p>
  </div>

  <div id="mainSection" class="container hidden">
    <div class="driver-section">
      <h3>Car Driver Phone Numbers</h3>
      <ul>
        <li>Driver 1: 0300-1234567</li>
        <li>Driver 2: 0301-9876543</li>
      </ul>
    </div>

    <input type="text" id="searchInput" onkeyup="searchTable()" placeholder="Search by Name, ID or Father Name" />

    <table id="studentTable">
      <thead>
        <tr>
          <th>ID</th><th>Class</th><th>Section</th><th>Name</th><th>Father Name</th><th>Gender</th><th>Phone 1</th><th>Phone 2</th><th>Phone 3</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>501</td><td>Nursery</td><td>A</td><td>Ali Khan</td><td>Ahmed Khan</td><td>Male</td><td>03123456789</td><td></td><td></td></tr>
      </tbody>
    </table>
  </div>

  <div class="fab hidden" id="fabControls">
    <button title="Add" onclick="alert('Add Student')">+</button>
    <button title="Edit" onclick="alert('Edit Student')">✎</button>
    <button title="Remove" onclick="alert('Remove Student')">−</button>
  </div>

  <script>
    const PASSWORD = "admin123"; // Change this to your secure password

    function checkPassword() {
      const input = document.getElementById('passwordInput').value;
      if (input === PASSWORD) {
        document.getElementById('loginSection').classList.add('hidden');
        document.getElementById('mainSection').classList.remove('hidden');
        document.getElementById('fabControls').classList.remove('hidden');
      } else {
        document.getElementById('loginError').textContent = "Incorrect password. Please try again.";
      }
    }

    function searchTable() {
      const input = document.getElementById("searchInput").value.toLowerCase();
      const rows = document.querySelectorAll("#studentTable tbody tr");
      rows.forEach(row => {
        const text = row.textContent.toLowerCase();
        row.style.display = text.includes(input) ? "" : "none";
      });
    }
  </script>
</body>
</html>
