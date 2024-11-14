# jenifa_gog.github.io
Task
# Welcome to the task

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ABC India Web Application</title>
  <style>
    body { font-family: Arial, sans-serif; }
    header, footer { text-align: center; background-color: #f8f8f8; padding: 10px; }
    .container { text-align: center; margin-top: 20px; }
    .hidden { display: none; }
    .button { margin: 10px; padding: 10px 20px; cursor: pointer; }
  </style>
</head>
<body>
  <header>
    <a href="#" onclick="showSection('home')">Home</a> | 
    <a href="#" onclick="showSection('about')">About Us</a> | 
    <a href="#" onclick="showSection('contact')">Contact Us</a> | 
    <a href="#" onclick="showSection('login')">Login</a> | 
    <a href="#" onclick="showSection('signup')">Sign Up</a>
  </header>

  <div id="home" class="container">
    <h2>Welcome to Home Page</h2>
    <p>Copyright @ Abc India 2024</p>
  </div>

  <div id="about" class="container hidden">
    <h2>About Us</h2>
    <p>Hi, this is the website of ABC India. We provide various products and services for Industry.</p>
  </div>

  <div id="contact" class="container hidden">
    <h2>Contact Us</h2>
    <p>C-456, Sector-3, Noida, Uttar Pradesh, India</p>
  </div>

  <div id="login" class="container hidden">
    <h2>Login</h2>
    <form onsubmit="return loginUser(event)">
      <input type="text" id="loginUserId" placeholder="User ID (Email or Mobile)" required><br><br>
      <input type="password" id="loginPassword" placeholder="Password" required><br><br>
      <button type="submit" class="button">Login</button>
    </form>
    <p id="loginError" style="color: red; display: none;">Invalid credentials. Please try again.</p>
  </div>

  <div id="signup" class="container hidden">
    <h2>Sign Up</h2>
    <form onsubmit="return registerUser(event)">
      <input type="text" id="signupName" placeholder="User Name" required><br><br>
      <input type="email" id="signupEmail" placeholder="Email" required><br><br>
      <input type="text" id="signupMobile" placeholder="Mobile" required><br><br>
      <input type="password" id="signupPassword" placeholder="Password" required><br><br>
      <input type="password" id="signupRetypePassword" placeholder="Retype Password" required><br><br>
      <button type="submit" class="button">Create New User</button>
    </form>
    <p id="signupError" style="color: red; display: none;">Passwords do not match. Please try again.</p>
  </div>

  <div id="dashboard" class="container hidden">
    <h2>Welcome <span id="userName"></span> to Dashboard</h2>
    <p>Here you can perform tasks from the left menu.</p>
    <nav>
      <a href="#" onclick="showSection('changePassword')">Change Password</a> | 
      <a href="#" onclick="logout()">Logout</a>
    </nav>
  </div>

  <div id="changePassword" class="container hidden">
    <h2>Change Password</h2>
    <form>
      <input type="text" placeholder="User ID" disabled><br><br>
      <input type="password" placeholder="New Password" required><br><br>
      <input type="password" placeholder="Old Password" required><br><br>
      <button type="submit" class="button">Update Password</button>
    </form>
  </div>

  <footer>
    <p>Practical Test Case | ADTUPTC14112024 | Your Name | Your Mobile</p>
  </footer>

  <script>
    function showSection(sectionId) {
      document.querySelectorAll('.container').forEach(div => div.classList.add('hidden'));
      document.getElementById(sectionId).classList.remove('hidden');
    }

    function loginUser(event) {
      event.preventDefault();
      const userId = document.getElementById('loginUserId').value;
      const password = document.getElementById('loginPassword').value;
      
      // For demonstration, using a hardcoded check
      if ((userId === localStorage.getItem('userEmail') || userId === localStorage.getItem('userMobile')) &&
          password === localStorage.getItem('userPassword')) {
        document.getElementById('userName').innerText = localStorage.getItem('userName');
        showSection('dashboard');
      } else {
        document.getElementById('loginError').style.display = 'block';
      }
    }

    function registerUser(event) {
      event.preventDefault();
      const name = document.getElementById('signupName').value;
      const email = document.getElementById('signupEmail').value;
      const mobile = document.getElementById('signupMobile').value;
      const password = document.getElementById('signupPassword').value;
      const retypePassword = document.getElementById('signupRetypePassword').value;
      
      if (password !== retypePassword) {
        document.getElementById('signupError').style.display = 'block';
        return;
      }
      
      localStorage.setItem('userName', name);
      localStorage.setItem('userEmail', email);
      localStorage.setItem('userMobile', mobile);
      localStorage.setItem('userPassword', password);
      showSection('login');
    }

    function logout() {
      showSection('home');
    }
  </script>
</body>
</html>
