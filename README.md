# Yt-hub-
"YouTube channel promotion platform built with HTML, CSS, and JavaScript."
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Notifications - YT Hub</title>
  <style>
    body {
      font-family: sans-serif;
      background: #eef2f7;
      padding: 30px;
      text-align: center;
    }
    .box {
      max-width: 700px;
      margin: auto;
      background: white;
      border-radius: 12px;
      padding: 20px;
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Monthly Events - YT Hub</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f4f7fa;
      padding: 30px;
      text-align: center;
    }
    .card {
      background: white;
      padding: 20px;
      margin: 15px auto;
      max-width: 600px;
      border-radius: 12px;
      box-shadow: 0 0 1
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Premium Membership - YT Hub</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f2f2f2;
      padding: 30px;
      text-align: center;
    }
    .card {
      background: white;
      padding: 25px;
      max-width: 600px;
      margin: auto;
      border-radius: 15px;
      box-shadow: 0 0 12px rgba(0,0,0,0.1);
    }
    h2 {
      margin-bottom: 10px;
    }
    ul {
      text-align:
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Your History - YT Hub</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f2f4f7;
      padding: 20px;
      text-align: center;
    }
    .container {
      max-width: 700px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    .entry {
      border-bottom: 1px solid #ddd;
      padding: 12px 0;
      text-align: left;
    }
    .entry:last-child {
      border-bottom: none;
    }
    .entry a {
      font-weight: bold;
      color: #007bff;
      text-decoration: none;
    }
    .entry small
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Leaderboard - YT Hub</title>
  <style>
    body {
      font-family: sans-serif;
      background: #eef0f5;
      padding: 20px;
      text-align: center;
    }
    h2 {
      margin-bottom: 10px;
    }
    .board {
      max-width: 600px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 0 8px rgba(0,0,0,0.1);
    }
    .user-row {
      display: flex;
      justify-content: space-between;
      padding: 10px;
      margin: 8px 0;
      border-bottom: 1px solid #ccc;
    }
    .user-row:nth-child(1) { background: #ffd70033; font-weight: bold; }
    .user-row:nth-child(2) { background: #c0c0c033; font-weight: bold; }
    .user-row:nth-child(3) { background: #cd7f3233; font-weight: bold; }
  </style>
</head>
<body>

  <h2>🏆 Top YT Hub Users</h2>
  <div class="board" id="boardList"></div>

  <script>
    const submissions = JSON.parse(localStorage.getItem("ytSubmissions") || "[]");
    const pointsMap = {};

    // Total up points for each user
    submissions.forEach(entry => {
      if (!entry.owner) return;
      if (!pointsMap[entry.owner]) {
        pointsMap[entry.owner] = {
          points: 0,
          subs: 0,
          likes: 0,
          views: 0
        };
      }

      pointsMap[entry.owner].points += entry.points;
      pointsMap[entry.owner].subs += entry.subs;
      pointsMap[entry.owner].likes += entry.likes;
      pointsMap[entry.owner].views += entry.views;
    });

    const sorted = Object.entries(pointsMap).sort((a, b) => b[1].points - a[1].points);

    const board = document.getElementById("boardList");
    sorted.forEach(([user, data], i) => {
      const div = document.createElement("div");
      div.className = "user-row";
      div.innerHTML = `
        <span>#${i + 1} - ${user}</span>
        <span>Points: ${data.points} | Subs: ${data.subs} | Likes: ${data.likes} | Views: ${data.views}</span>
      `;
      board.appendChild(div);
    });
  </script>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Browse Channels - YT Hub</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f9f9f9;
      padding: 20px;
      text-align: center;
    }
    .container {
      max-width: 800px;
      margin: auto;
    }
    .card {
      background: white;
      margin: 15px 0;
      padding: 15px;
      border-radius: 12px;
      box-shadow: 0 0 8px rgba(0,0,0,0.1);
      text-align: left;
    }
    .card img {
      width: 100%;
      border-radius: 10px;
      max-height: 200px;
      object-fit: cover;
    }
    .card h3 {
      margin-top: 10px;
    }
    .btn-group button {
      margin: 5px;
      padding: 8px 15px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      color: white;
      font-weight: bold;
    }
    .subscribe { background: #dc3545; }
    .like { background: #007bff; }
    .view { background: #28a745; }
  </style>
</head>
<body>

  <h2>🔥 Browse & Interact</h2>
  <p>Get points by helping others!</p>

  <div class="container" id="channelList"></div>

  <script>
    let data = JSON.parse(localStorage.getItem("ytSubmissions") || "[]");
    const currentUser = localStorage.getItem("ytUser") || "Guest";
    let points = parseInt(localStorage.getItem("ytPoints") || "0");

    function saveData() {
      localStorage.setItem("ytSubmissions", JSON.stringify(data));
      localStorage.setItem("ytPoints", points.toString());
    }

    function renderCards() {
      const list = document.getElementById("channelList");
      list.innerHTML = "";

      data.forEach((item, index) => {
        // skip own sub
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Submit Channel or Video - YT Hub</title>
  <style>
    body {
      font-family: sans-serif;
      background: #eef2f8;
      padding: 20px;
      text-align: center;
    }
    .form-box {
      background: white;
      max-width: 450px;
      margin: auto;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    input, button {
      width: 90%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 6px;
    }
    button {
      background: #28a745;
      color: white;
      font-weight: bold;
      cursor: pointer;
      border: none;
    }
    button:hover {
      background: #218838;
    }
    .back {
      margin-top: 20px;
      font-size: 14px;
      display: inline-block;
      text-decoration: underline;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <div class="form-box">
    <h2>Sub
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>YT Hub Dashboard</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f0f0f8;
      padding: 20px;
      text-align: center;
    }
    .dashboard {
      max-width: 400px;
      margin: auto;
      background: white;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0,0,0,0.15);
    }
    h2 {
      color: #333;
    }
    .points {
      font-size: 20px;
      margin: 10px 0 30px;
      color: #007bff;
    }
    button {
      width: 90%;
      padding: 12px;
      margin: 10px 0;
      font-size: 16px;
      border: none;
      border-radius: 8px;
      background: #007bff;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background: #0056b3;
    }
  </style>
</head>
<body>

  <div class="dashboard">
    <h2>Welcome, <span id="username">User</span>!</h2>
    <div class="points">Points: <span id="points">0</span></div>

    <button onclick="goTo('submit.html')">📤 Submit Channel / Video</button>
    <button onclick="goTo('browse.html')">🔍 Browse Others</button>
    <button onclick="goTo('leaderboard.html')">🏆 Leaderboard</button>
    <button onclick="goTo('history.html')">📜 History</button>
    <button onclick="goTo('events.html')">🎉 Events</button>
    <button onclick="goTo('premium.html')">💎 Premium</button>
  </div>

  <script>
    // Fetch user info from localStorage
    const name = localStorage.getItem("ytUser") || "Guest";
    const points = localStorage.getItem("ytPoints") || "0";

    document.getElementById("username").innerText = name;
    document.getElementById("points").innerText = points;

    function goTo(page) {
      window.location.href = page;
    }
  </script>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Login - YT Hub</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f2f2f2;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }
    .login-box {
      background: white;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
      text-align: center;
    }
    input, button {
      padding: 10px;
      width: 80%;
      margin: 10px 0;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    button {
      background: #007bff;
      color: white;
      border: none;
    }
  </style>
</head>
<body>

  <div class="login-box">
    <h2>YT Hub Login</h2>
    <input type="text" id="username" placeholder="Enter your name" />
    <input type="email" id="email" placeholder="Enter your email" />
    <button onclick="login()">Login</button>
  </div>

  <script>
    function login() {
      const name = document.getElementById('username').value.trim();
      const email = document.getElementById('email').value.trim();

      if (name === '' || email === '') {
        alert("Please enter both name and email.");
        return;
      }

      // Save user data to localStorage
      localStorage.setItem("ytUser", name);
      localStorage.setItem("ytEmail", email);
      localStorage.setItem("ytPoints", "0");

      window.location.href = "dashboard.html"; // next page
    }
  </script>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Login - YT Hub</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f2f2f2;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }
    .login-box {
      background: white;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
      text-align: center;
    }
    input, button {
      padding: 10px;
      width: 80%;
      margin: 10px 0;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    button {
      background: #007bff;
      color: white;
      border: none;
    }
  </style>
</head>
<body>

  <div class="login-box">
    <h2>YT Hub Login</h2>
    <input type="text" id="username" placeholder="Enter your name" />
    <button onclick="login()">Login</button>
  </div>

  <script>
    function login() {
      const name = document.getElementById('username').value;
      if (name.trim() === '') {
        alert("Please enter a valid name.");
        return;
      }
      // Save user and points in localStorage
      localStorage.setItem("ytUser", name);
      localStorage.setItem("ytPoints", "0");
      window.location.href = "dashboard.html"; // next page
    }
  </script>

</body>
</html>
