<?html
session_start();

// Database connection settings
$servername = "localhost";
$dbusername = "root";
$dbpassword = "";
$dbname = "didoxx"; // Change to your actual DB name

$conn = new mysqli($servername, $dbusername, $dbpassword, $dbname);
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$errors = [];
$success = "";

if ($_SERVER["REQUEST_METHOD"] === "POST") {
    $username = trim($_POST['username'] ?? '');
    $email = trim($_POST['email'] ?? '');
    $phone = trim($_POST['phone'] ?? '');
    $password = $_POST['password'] ?? '';
    $passwordConfirm = $_POST['passwordConfirm'] ?? '';

    // Basic validations
    if (!$username) {
        $errors[] = "Username is required.";
    }
    if (!$email || !filter_var($email, FILTER_VALIDATE_EMAIL)) {
        $errors[] = "A valid email is required.";
    }
    if ($phone && !preg_match('/^\+?[0-9\s-]{7,15}$/', $phone)) {
        $errors[] = "Please enter a valid phone number.";
    }
    if (!$password || strlen($password) < 8) {
        $errors[] = "Password must be at least 8 characters.";
    }
    if ($password !== $passwordConfirm) {
        $errors[] = "Passwords do not match.";
    }

    // Check for existing username or email
    if (empty($errors)) {
        $stmt = $conn->prepare("SELECT id FROM users WHERE username = ? OR email = ?");
        $stmt->bind_param("ss", $username, $email);
        $stmt->execute();
        $stmt->store_result();
        if ($stmt->num_rows > 0) {
            $errors[] = "Username or email already exists.";
        }
        $stmt->close();
    }

    // Insert new user if no errors
    if (empty($errors)) {
        $hashedPassword = password_hash($password, PASSWORD_DEFAULT);
        $stmt = $conn->prepare("INSERT INTO users (username, email, phone, password) VALUES (?, ?, ?, ?)");
        $stmt->bind_param("ssss", $username, $email, $phone, $hashedPassword);
        if ($stmt->execute()) {
            // Redirect to login page after successful registration
            header("Location: login.html");
            exit(); // Ensure no further code is executed after the redirect
        } else {
            $errors[] = "Error: " . $stmt->error;
        }
        $stmt->close();
    }
}

$conn->close();
?>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>DIDOXX - Registration</title>
  <link rel="stylesheet" href="didox.css" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    /* Inherit styles consistent with About.html */
    :root {
      --color-bg: #ffffffff;
      --color-primary: #111827;
      --color-accent: #005187;
      --color-text: #6b7280;
      --color-heading: #111827;
      --border-radius: 0.75rem;
      --shadow-light: 0 4px 12px rgba(0,0,0,0.05);
      --font-heading: 'Poppins', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      --font-body: 'Inter', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: var(--font-body);
      background-color: var(--color-bg);
      color: var(--color-text);
      line-height: 1.6;
      font-size: 18px;
      font-weight: 400;
      animation: fadeIn 1s ease-in-out;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    a {
      color: var(--color-accent);
      text-decoration: none;
      font-weight: 600;
      transition: color 0.3s ease;
    }
    a:hover, a:focus {
      color: #10375c;
      outline: none;
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 1.5rem 1rem;
    }

    header {
      position: sticky;
      top: 0;
      background: var(--color-bg);
      box-shadow: var(--shadow-light);
      padding: 0.75rem 1rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 1000;
    }
    .logo {
      font-family: var(--font-heading);
      font-weight: 700;
      font-size: 1.75rem;
      color: var(--color-primary);
      user-select: none;
      margin-right: 32px;
    }

    nav {
      display: flex;
      align-items: center;
      gap: 32px;
      flex-grow: 1; /* Allow nav to grow and push header-actions to the right */
      justify-content: flex-end; /* Align nav items to the right on desktop */
    }

    nav ul {
      list-style: none;
      margin: 0;
      padding: 0;
      display: flex;
      gap: 2rem;
    }
    nav li a {
      font-weight: 600;
      color: var(--color-accent);
      font-size: 1rem;
      padding: 0.25rem 0.5rem;
      border-radius: 0.375rem;
      transition: background-color 0.3s ease, color 0.3s ease;
    }
    nav li a:hover, nav li a:focus {
      background-color: var(--color-accent);
      color: #fff;
      outline: none;
    }

    /* Mobile menu button styling */
    .mobile-menu-button {
      display: none; /* Hidden by default on desktop */
      background: none;
      border: none;
      cursor: pointer;
      padding: 0.5rem;
      border-radius: 0.375rem;
      transition: background-color 0.3s ease;
      color: var(--color-accent);
      align-items: center;
      justify-content: center;
    }
    .mobile-menu-button:focus, .mobile-menu-button:hover {
      background-color: var(--color-accent);
      color: #fff;
      outline: none;
    }
    .mobile-menu-button svg {
      width: 24px;
      height: 24px;
      stroke: currentColor;
      stroke-width: 2;
      stroke-linecap: round;
      stroke-linejoin: round;
      fill: none;
      display: block;
    }

    /* New styles for header-actions container */
    .header-actions {
      display: flex; /* Use flex to align its children (mobile button and cart) */
      align-items: center;
      gap: 0.5rem; /* Space between mobile button and cart */
    }

    @media (max-width: 768px) {
      /* Adjust header for mobile */
      header {
        justify-content: space-between; /* Keep logo left, actions right */
      }

      /* Hide the main navigation links on mobile */
      nav ul {
        display: none;
        flex-direction: column;
        gap: 1rem;
        background: var(--color-bg);
        position: absolute;
        top: 60px;
        left: 0;
        right: 0;
        padding: 1rem 2rem;
        box-shadow: var(--shadow-light);
        border-radius: 0 0 var(--border-radius) var(--border-radius);
        z-index: 999;
      }
      nav ul.show {
        display: flex;
      }

      /* Adjust nav for mobile - it should not take up flex-grow space */
      nav {
        flex-grow: 0; /* Reset flex-grow for nav on mobile */
        gap: 0; /* Remove gap for nav on mobile if its children are hidden */
      }

      /* Show the mobile menu button on mobile */
      .mobile-menu-button {
        display: flex; /* Show on mobile */
        order: 1; /* Place it before the cart button */
      
      }
    }

    main {
      flex-grow: 1;
      padding: 3rem 1rem 5rem;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    form.registration-form {
      max-width: 400px;
      width: 100%;
      background: var(--color-bg);
      box-shadow: var(--shadow-light);
      border-radius: var(--border-radius);
      padding: 2.5rem 3rem;
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
      animation: fadeIn 1s ease-in-out;
    }

    h1 {
      font-family: var(--font-heading);
      font-weight: 800;
      font-size: 2.4rem;
      color: var(--color-heading);
      margin-top: 0.1rem;
      margin-bottom: 0.1rem;
      text-align: center;
      user-select: none;
    }

    label {
      font-weight: 600;
      color: var(--color-primary);
      margin-bottom: 0.5rem;
      display: block;
      font-size: 1rem;
    }

    input[type="text"],
    input[type="email"],
    input[type="tel"],
    input[type="password"] {
      width: 100%;
      padding: 0.75rem 1rem;
      border: 1.5px solid #d1d5db;
      border-radius: 0.5rem;
      font-size: 1rem;
      font-family: var(--font-body);
      transition: border-color 0.3s ease, transform 0.3s ease;
      resize: vertical;
      min-height: 40px;
    }

    input[type="text"]:focus,
    input[type="email"]:focus,
    input[type="tel"]:focus,
    input[type="password"]:focus {
      border-color: var(--color-accent);
      outline: none;
      box-shadow: 0 0 8px rgba(0,81,135,0.25);
      transform: scale(1.02);
    }

    button[type="submit"] {
      background-color: var(--color-accent);
      color: white;
      font-weight: 700;
      font-size: 1.125rem;
      padding: 0.75rem 2.5rem;
      border: none;
      border-radius: 0.5rem;
      cursor: pointer;
      transition: background-color 0.3s ease, transform 0.3s ease;
      align-self: center;
      width: max-content;
      min-width: 160px;
      user-select: none;
    }

    button[type="submit"]:hover,
    button[type="submit"]:focus {
      background-color: #10375c;
      outline: none;
      transform: scale(1.05);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    }


    /* Dropdown styles */
    .dropdown {
      position: relative;
      display: inline-block;
    }

    .dropdown-content {
      display: none;
      position: absolute;
      background-color: var(--color-bg);
      min-width: 160px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.2);
      z-index: 1;
      border-radius: var(--border-radius);
      right: 0; /* Align dropdown to the right */
    }

    .dropdown-content a {
      color: var(--color-text);
      padding: 12px 16px;
      text-decoration: none;
      display: block;
      text-align: left;
    }

    .dropdown-content a:hover {
      background-color: var(--color-accent);
      color: #fff;
    }

    .dropdown:hover .dropdown-content {
      display: block;
    }

    /* Cart button styling (Copied from ourproducts.html) */
    .cart-btn {
      background: none;
      border: none;
      cursor: pointer;
      color: var(--color-accent);
      font-size: 1.1rem;
      position: relative;
      padding: 0.4rem;
      border-radius: 0.375rem;
      transition: background-color 0.3s ease, color 0.3s ease;
    }
    .cart-btn:hover, .cart-btn:focus {
      background-color: var(--color-accent);
      color: #fff;
      outline: none;
    }
    .cart-count {
      position: absolute;
      top: 0;
      right: 0;
      background-color: #e74c3c; /* Red dot */
      color: white;
      border-radius: 50%;
      padding: 0.10rem 0.3rem;
      font-size: 0.55rem;
      line-height: 1.2;
      min-width: 0.50px;
      text-align: center;
      transform: translate(50%, -50%);
      display: <?html echo ($cart_item_count > 0) ? 'block' : 'none'; ?>; /* Hide if 0 items */
    }

    /* Cart Modal Styles (Copied from ourproducts.html) */
    .cart-modal {
      display: none; /* Hidden by default */
      position: fixed; /* Stay in place */
      z-index: 1001; /* Sit on top */
      left: 0;
      top: 0;
      width: 100%; /* Full width */
      height: 100%; /* Full height */
      overflow: auto; /* Enable scroll if needed */
      background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
      justify-content: center;
      align-items: center;
    }

    .cart-modal-content {
      background-color: var(--color-bg);
      margin: auto;
      padding: 2rem;
      border-radius: var(--border-radius);
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
      width: 90%;
      max-width: 700px;
      position: relative;
      animation: slideIn 0.3s ease-out;
    }

    @keyframes slideIn {
      from { transform: translateY(-50px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }

    .close-button {
      color: #aaa;
      float: right;
      font-size: 28px;
      font-weight: bold;
      position: absolute;
      top: 10px;
      right: 20px;
    }

    .close-button:hover,
    .close-button:focus {
      color: var(--color-primary);
      text-decoration: none;
      cursor: pointer;
    }

    .cart-modal-content h2 {
      font-family: var(--font-heading);
      color: var(--color-primary);
      margin-top: 0;
      margin-bottom: 1.5rem;
      text-align: center;
    }

    .cart-items {
      list-style: none;
      padding: 0;
      margin-bottom: 1.5rem;
      max-height: 400px;
      overflow-y: auto;
    }

    .cart-item {
      display: flex;
      align-items: center;
      gap: 1rem;
      padding: 1rem 0;
      border-bottom: 1px solid #eee;
    }

    .cart-item:last-child {
      border-bottom: none;
    }

    .cart-item img {
      width: 80px;
      height: 80px;
      object-fit: cover;
      border-radius: 0.5rem;
    }

    .cart-item-details {
      flex-grow: 1;
    }

    .cart-item-details h5 {
      margin: 0;
      font-size: 1.1rem;
      color: var(--color-primary);
    }

    .cart-item-details p {
      margin: 0.25rem 0 0;
      font-size: 0.9rem;
      color: var(--color-text);
    }

    .cart-item-price {
      font-weight: 600;
      color: var(--color-accent);
      white-space: nowrap;
    }

    .remove-item-btn {
      background: none;
      border: none;
      color: #e74c3c;
      cursor: pointer;
      font-size: 1.2rem;
      transition: color 0.3s ease;
    }

    .remove-item-btn:hover {
      color: #c0392b;
    }

    .cart-total {
      text-align: right;
      font-size: 1.2rem;
      font-weight: 700;
      color: var(--color-primary);
      margin-top: 1.5rem;
      padding-top: 1rem;
      border-top: 1px solid #eee;
    }

    .cart-actions {
      display: flex;
      justify-content: flex-end;
      gap: 1rem;
      margin-top: 1.5rem;
    }

    .cart-actions button {
      padding: 0.75rem 1.5rem;
      border-radius: 0.5rem;
      font-weight: 600;
      cursor: pointer;
      transition: background-color 0.3s ease, transform 0.3s ease;
    }

    .cart-actions .continue-shopping {
      background-color: #f0f0f0;
      color: var(--color-primary);
      border: 1px solid #ddd;
    }

    .cart-actions .continue-shopping:hover {
      background-color: #e0e0e0;
      transform: translateY(-2px);
    }

    .cart-actions .checkout {
      background-color: var(--color-accent);
      color: white;
      border: none;
    }

    .cart-actions .checkout:hover {
      background-color: #10375c;
      transform: translateY(-2px);
    }

    
    .form-footer {
      text-align: center;
      font-size: 0.9rem;
      color: var(--color-text);
    }
    .form-footer a {
      font-weight: 600;
      color: var(--color-accent);
      text-decoration: none;
    }
    .form-footer a:hover,
    .form-footer a:focus {
      color: #10375c;
      outline: none;
      text-decoration: underline;
    }

    .error-messages {
      background: #fee2e2;
      border: 1px solid #fca5a5;
      padding: 1rem;
      border-radius: 0.5rem;
      color: #b91c1c;
      margin-bottom: 1rem;
      font-weight: 600;
    }

    .success-message {
      background: #d1fae5;
      border: 1px solid #34d399;
      padding: 1rem;
      border-radius: 0.5rem;
      color: #065f46;
      margin-bottom: 1rem;
      font-weight: 600;
    }
 /* Responsive */
    @media (max-width: 768px) {
      nav ul {
        gap: 1rem;
        flex-wrap: wrap;
        justify-content: center;
      }
      form.registration-form {
        padding: 1.5rem 1.5rem;
      }
      h1 {
        font-size: 2.25rem;
      }
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
      }
      to {
        opacity: 1;
      }
    }
  </style>
</head>
<body>
<header>
  <a href="index.html" aria-label="Home" class="logo">DIDOXX</a>
  <nav>
    <ul>
      <a href="index.html">Home</a>
      <a href="About.html">About-us</a>
      <a href="ourproducts.html">Our products</a>
      <a href="contact.html">Contact</a>
      <a href="login.html">Login</a>
    </ul>
  </nav>

  <!-- New container for mobile menu and cart button -->
    <div class="header-actions">
      <button class="mobile-menu-button" aria-expanded="false" aria-controls="primary-navigation" aria-label="Toggle menu">
        <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <line x1="3" y1="6" x2="21" y2="6"></line>
          <line x1="3" y1="12" x2="21" y2="12"></line>
          <line x1="3" y1="18" x2="21" y2="18"></line>
        </svg>
      </button>
      
         
    </div>
</header>
<main>
  <?html if ($errors): ?>
    <div class="error-messages" role="alert" aria-live="assertive">
      <ul>
        <?html foreach ($errors as $error): ?>
          <li><?= htmlspecialchars($error) ?></li>
        <?html endforeach; ?>
      </ul>
    </div>
  <?html endif; ?>
  <?html if ($success): ?>
    <div class="success-message" role="alert" aria-live="polite"><?= $success ?></div>
  <?html endif; ?>

  <form class="registration-form" id="registrationForm" method="POST" action="registration.html" novalidate>
    <h1>Create Account</h1>
    
    <label for="username">Username</label>
    <input type="text" id="username" name="username" required autocomplete="username" placeholder="Enter your username" value="<?= htmlspecialchars($_POST['username'] ?? '') ?>" />
    
    <label for="email">Email address</label>
    <input type="email" id="email" name="email" required autocomplete="email" placeholder="Enter your email" value="<?= htmlspecialchars($_POST['email'] ?? '') ?>" />
    
    <label for="phone">Phone Number (optional)</label>
    <input type="tel" id="phone" name="phone" autocomplete="tel" placeholder="e.g. +011-666-9999" pattern="^\+?[0-9\s-]{7,15}$" value="<?= htmlspecialchars($_POST['phone'] ?? '') ?>" />
    
    <label for="password">Password</label>
    <input type="password" id="password" name="password" required autocomplete="new-password" placeholder="Enter a strong password" minlength="8" />
    
    <label for="passwordConfirm">Confirm Password</label>
    <input type="password" id="passwordConfirm" name="passwordConfirm" required autocomplete="new-password" placeholder="Confirm your password" minlength="8" />
    
    <button type="submit">Register</button>
    
    <div class="form-footer">
      Already have an account? <a href="login.html">Login here</a>.
    </div>
  </form>
</main>

<script>
  document.addEventListener('DOMContentLoaded', function () {
    const menuButton = document.querySelector('.mobile-menu-button');
    const navMenu = document.querySelector('nav ul');

    menuButton.addEventListener('click', function () {
      navMenu.classList.toggle('show');

      // Optional: toggle accessibility attribute
      const isExpanded = menuButton.getAttribute('aria-expanded') === 'true';
      menuButton.setAttribute('aria-expanded', String(!isExpanded));
    });
  });
</script>


</body>
</html>
