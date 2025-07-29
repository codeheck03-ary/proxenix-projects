# proxenix-projects

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simple Online Education Platform</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: #f4f4f4;
    }
    header {
      background: #4CAF50;
      color: white;
      padding: 15px;
      text-align: center;
    }
    nav {
      background: #333;
      padding: 10px;
      text-align: center;
    }
    nav a {
      color: white;
      margin: 0 10px;
      text-decoration: none;
    }
    .container {
      padding: 20px;
    }
    .course {
      background: white;
      padding: 15px;
      margin: 10px 0;
      border-radius: 5px;
    }
    .discussion, .progress, .login-form, .notification {
      background: #fff;
      padding: 15px;
      margin-top: 20px;
      border-radius: 5px;
    }
    input, button {
      padding: 10px;
      margin: 5px 0;
      width: 100%;
    }
    button {
      background-color: #4CAF50;
      color: white;
      border: none;
    }
  </style>
</head>
<body>
  <header>
    <h1>LearnOnline Platform</h1>
  </header>

  <nav>
    <a href="#courses">Courses</a>
    <a href="#login">Login</a>
    <a href="#progress">Progress</a>
    <a href="#discussion">Discussion</a>
  </nav>

  <div class="container">
    <section id="login" class="login-form">
      <h2>Login</h2>
      <input type="text" placeholder="Username" id="username">
      <input type="password" placeholder="Password" id="password">
      <button onclick="login()">Login</button>
    </section>

    <section id="courses">
       h2>Available Courses</h2>
      <div class="course">
        <h3>Web Development Basics</h3>
        <p>Learn HTML, CSS, and JavaScript.</p>
        <button onclick="enroll('Web Development Basics')">Enroll</button>
      </div>
      <div class="course">
        <h3>Data Science Intro</h3>
        <p>Explore data and build basic models.</p>
        <button onclick="enroll('Data Science Intro')">Enroll</button>
      </div>
    </section>

    <section id="progress" class="progress">
      <h2>Your Progress</h2>
      <p id="progressText">Not enrolled in any course yet.</p>
    </section>

    <section id="discussion" class="discussion">
      <h2>Discussion Channel</h2>
      <textarea id="discussionInput" rows="4" placeholder="Type your question..."></textarea>
      <button onclick="postDiscussion()">Post</button>
      <div id="discussionBoard"></div>
    </section>

    <section class="notification">
      <h2>Notifications</h2>
      <ul id="notificationList">
        <li>Welcome to LearnOnline!</li>
      </ul>
    </section>
  </div>

  <script>
    function login() {
      const user = document.getElementById('username').value;
      const pass = document.getElementById('password').value;
      if (user && pass) {
        alert('Login successful!');
        addNotification(`User ${user} logged in.`);
      } else {
        alert('Please enter username and password.');
      }
    }

    function enroll(courseName) {
      document.getElementById('progressText').textContent = `You are enrolled in: ${courseName}`;
      addNotification(`Enrolled in ${courseName}`);
    }

    function postDiscussion() {
      const input = document.getElementById('discussionInput');
      const board = document.getElementById('discussionBoard');
      if (input.value.trim() !== '') {
        const post = document.createElement('p');
        post.textContent = input.value;
        board.appendChild(post);
        input.value = '';
        addNotification('New discussion post added');
      }
    }

    function addNotification(message) {
      const list = document.getElementById('notificationList');
      const item = document.createElement('li');
      item.textContent = message;
      list.appendChild(item);
    }
  </script>
</body>
</html>
