<?html
session_start();


// Database connection
$conn = new mysqli("localhost", "root", "", "didoxx");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Initialize cart if not already set
if (!isset($_SESSION['cart'])) {
    $_SESSION['cart'] = [];
}

// Count total items in cart
$cart_item_count = 0;
foreach ($_SESSION['cart'] as $item) {
    $cart_item_count += $item['quantity'];
}


// Handle Add to Cart
if (isset($_POST['add_to_cart'])) {
    $product_id = $_POST['product_id'];
    $product_name = $_POST['product_name'];
    $product_price = $_POST['product_price'];
    $product_image = $_POST['product_image'];

    $found = false;
    foreach ($_SESSION['cart'] as &$item) {
        if ($item['id'] == $product_id) {
            $item['quantity']++;
            $found = true;
            break;
        }
    }
    if (!$found) {
        $_SESSION['cart'][] = [
            'id' => $product_id,
            'name' => $product_name,
            'price' => $product_price,
            'image' => $product_image,
            'quantity' => 1
        ];
    }

    header('Location: ourproducts.html');
    exit();
}

// Handle Remove from Cart
if (isset($_GET['remove_from_cart'])) {
    $product_id_to_remove = $_GET['remove_from_cart'];
    foreach ($_SESSION['cart'] as $key => $item) {
        if ($item['id'] == $product_id_to_remove) {
            unset($_SESSION['cart'][$key]);
            break;
        }
    }
    $_SESSION['cart'] = array_values($_SESSION['cart']); // Re-index
    header('Location: ourproducts.html');
    exit();
}

// Get products from DB
$cart_item_count = 0;
foreach ($_SESSION['cart'] as $item) {
    $cart_item_count += $item['quantity'];
}

// Category filter
$category_filter = isset($_GET['category']) ? $_GET['category'] : 'all';

if ($category_filter === 'all') {
    $query = "SELECT * FROM products WHERE stock > 0";
    $stmt = $conn->prepare($query);
} else {
    $query = "SELECT * FROM products WHERE category = ? AND stock > 0";
    $stmt = $conn->prepare($query);
    $stmt->bind_param("s", $category_filter);
}

$stmt->execute();
$result = $stmt->get_result();

$filtered_products = [];
while ($row = $result->fetch_assoc()) {
    $filtered_products[] = $row;
}
?>



<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Our Products - DIDOXX</title>
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
      --spacing-sm: 1rem;
    --spacing-md: 2rem;
    --spacing-lg: 2rem;
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

      /* Ensure cart button is visible and correctly ordered on mobile */
      .cart-btn {
        order: 2; /* Place it after the mobile menu button */
      }
    }

    
    .product-container {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 20px;
    }

    .product-card {
        border: 1px solid #ccc;
        border-radius: 10px;
        padding: 0.5rem;
        width: 250px;
        text-align: center;
        background-color: #f9f9f9;
        box-shadow: 2px 2px 6px rgba(0,0,0,0.1);
    }

    .product-image {
        max-width: 80%;
        height: 140px;
        object-fit: cover;
        margin-bottom: 10px;
    }
  
    h1 {
      font-family: var(--font-heading);
      font-weight: 800;
      font-size: 3.5rem;
      color: var(--color-heading);
      margin-bottom: 0rem;
      line-height: 1.1;
      text-align: center;
    }

    p.lead {
      font-size: 1.125rem;
      color: var(--color-text);
      max-width: 700px;
      margin: 0 auto 0.1rem;
      text-align: center;
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
      flex-wrap: wrap;
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

    /* Filter Section Styles */
    .filter-section {
      display: flex;
      justify-content: flex-end; /* Align filter to the right */
      align-items: center;
      margin-bottom: 0.2rem;
      gap: 1rem;
    }

    .filter-section label {
      font-weight: 600;
      color: var(--color-primary);
      font-size: 1rem;
    }

    .filter-section select {
      padding: 0.5rem 1rem;
      border: 1.5px solid #d1d5db;
      border-radius: 0.5rem;
      font-size: 1rem;
      font-family: var(--font-body);
      background-color: var(--color-bg);
      color: var(--color-primary);
      cursor: pointer;
      transition: border-color 0.3s ease, box-shadow 0.3s ease;
    }

    .filter-section select:focus {
      border-color: var(--color-accent);
      outline: none;
      box-shadow: 0 0 8px rgba(0,81,135,0.25);
    }

    .product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(215px, 1fr));
  gap: 1.5rem;
  padding: 1rem 0;
  justify-items: center;
}

.product-card {
  background: var(--color-bg);
  border-radius: var(--border-radius);
  box-shadow: var(--shadow-light);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  height: 100%;
  width: 100%;
  max-width: 240px;
}

.product-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.1);
}

.product-card img {
  width: 100%;
  height: 140px;
  object-fit: cover;
  border-bottom: 1px solid #eee;
}

.product-info {
  padding: 0.5rem;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.product-info h4 {
  font-family: var(--font-heading);
  color: var(--color-primary);
  font-size: 1.1rem;
  margin: 0.2rem 0;
}

.product-info p {
  font-size: 0.85rem;
  color: var(--color-text);
  margin: 0.2rem 0;
  flex-grow: 1;
  line-height: 1.4;
}

.product-price {
  font-family: var(--font-heading);
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--color-accent);
  margin: 0.2rem 0;
}

.add-to-cart-form {
  margin-top: auto;
  display: flex;
  justify-content: center;
}

.add-to-cart-form button {
  background-color: var(--color-accent);
  color: white;
  font-weight: 600;
  font-size: 0.9rem;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
  width: 100%;
}

.add-to-cart-form button:hover,
.add-to-cart-form button:focus {
  background-color: #10375c;
  transform: translateY(-2px);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
}


    /* Cart Modal Styles */
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

    /* Footer Styles (identical to index.html) */
    footer {
      background: #000;
      color: #fff;
      padding: 3rem 2;
      margin-top: 3rem;
      border-radius: 0%;
    }

    .footer-container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 1rem;
    }

    .footer-content {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 2rem;
    }

    .footer-column h3 {
      font-family: var(--font-heading);
      color: #fff;
      margin-bottom: 1rem;
      font-size: 1.2rem;
    }

    .footer-column ul {
      list-style: none;
      padding: 0;
    }

    .footer-column ul li {
      margin-bottom: 0.5rem;
    }

    .footer-column ul li a {
      color: #aaa;
      text-decoration: none;
      transition: color 0.3s ease;
      font-size: 0.9rem;
    }

    .footer-column ul li a:hover {
      color: var(--color-accent);
    }

    .social-links {
      display: inline;
      gap: 1rem;
    }

    .social-links a {
      color: #aaa;
      font-size: 1.5rem;
      transition: color 0.3s ease;
    }

    .social-links a:hover {
      color: var(--color-accent);
    }

    .footer-bottom {
      margin-top: 2rem;
      padding-top: 2rem;
      border-top: 1px solid #333;
      text-align: center;
      color: #777;
      font-size: 0.9rem;
    }

    @media (max-width: 836px) {
      .footer-content {
        grid-template-columns: repeat(2, 1fr);
      }
      
      h1 {
        font-size: 2.5rem;
      }
      .product-grid {
        grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); /* Even smaller on tablet */
        gap: 1rem;
      }
      .filter-section {
        justify-content: center; /* Center filter on smaller screens */
        flex-direction: column;
        align-items: flex-start;
      }
    }

    @media (max-width: 200px) {
      .footer-content {
        grid-template-columns: 1fr;
      }
      
      h1 {
        font-size: 2rem;
      }
      .product-grid {
        grid-template-columns: 1fr; /* Single column on mobile */
      }
      .cart-modal-content {
        width: 95%;
        padding: 1.5rem;
      }
      .cart-item {
        flex-direction: column;
        align-items: flex-start;
        text-align: left;
      }
      .cart-item img {
        margin-bottom: 0.5rem;
      }
      .cart-item-price {
        align-self: flex-end;
      }
      .remove-item-btn {
        position: absolute;
        top: 1rem;
        right: 1rem;
      }
    }
  </style>
</head>
<body>
  <header>
    <a href="didox.html" aria-label="Home" class="logo">DIDOXX</a>
    <nav>
      <ul id="primary-navigation" role="menu">
        <a href="index.html" role="menuitem" tabindex="0">Home</a>
        <a href="About.html" role="menuitem" tabindex="0">About-us</a>
        <a href="ourproducts.html" role="menuitem" tabindex="0">Our products</a>
        <a href="contact.html" role="menuitem" tabindex="0">Contact</a>
        <li class="dropdown" a href="#" class="dropbtn" role="menuitem" tabindex="0">
            <img src="studio/user0.png" alt="User Profile" style="width: 25px; height: 24px;">
          </a>
          <div class="dropdown-content">
          <?html if (isset($_SESSION['user_id']) && isset($_SESSION['username'])): ?>
            <a href="#"><?html echo htmlspecialchars($_SESSION['username']); ?></a>
            <a href="login.html?action=logout">Logout</a>
          <?html else: ?>
            <a href="login.html">Login</a>
            <a href="registration.html">Register</a>
          <?html endif; ?>
        </div>

        </li>
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
      <div>
      <button class="cart-btn" id="cart-btn" aria-label="View Shopping Cart">
        <i class="fas fa-shopping-cart"></i>
        <span class="cart-count" id="cart-count"><?html echo $cart_item_count; ?></span>
      </button>
          </div>
    </div>
  </header>


  <main>
    <div class="container">
      <h1>Our Products</h1>
      <p class="lead">Discover our wide range of high-quality products designed to meet your needs.</p>

      <section class="filter-section" aria-label="Product Filters">
        <label for="category-filter">Filter by Category:</label>
        <select id="category-filter" onchange="window.location.href = this.value;">
          <option value="ourproducts.html?category=all" <?html echo (!isset($_GET['category']) || $_GET['category'] === 'all') ? 'selected' : ''; ?>>All Categories</option>
          <?html foreach ($categories as $category): ?>
            <option value="ourproducts.html?category=<?html echo urlencode($category); ?>" <?html echo (isset($_GET['category']) && $_GET['category'] === $category) ? 'selected' : ''; ?>>
              <?html echo htmlspecialchars($category); ?>
            </option>
          <?html endforeach; ?>
        </select>
      </section>

      <section class="product-grid" aria-label="Product Listings">
        <?html if (empty($filtered_products)): ?>
            <p style="text-align: center; grid-column: 1 / -1; color: var(--color-text);">No products found in this category.</p>
        <?html else: ?>
            <?html foreach ($filtered_products as $product): ?>
            <article class="product-card" tabindex="0" aria-label="<?html echo htmlspecialchars($product['name']); ?>">
                <img src="<?html echo htmlspecialchars($product['image']); ?>" alt="<?html echo htmlspecialchars($product['name']); ?>" />
                <div class="product-info">
                <h4><?html echo htmlspecialchars($product['name']); ?></h4>
                <p><?html echo htmlspecialchars($product['description']); ?></p>
                <div class="product-price">$<?html echo number_format($product['price'], 2); ?></div>
                <form class="add-to-cart-form" method="post" action="ourproducts.html">
                    <input type="hidden" name="product_id" value="<?html echo htmlspecialchars($product['id']); ?>">
                    <input type="hidden" name="product_name" value="<?html echo htmlspecialchars($product['name']); ?>">
                    <input type="hidden" name="product_price" value="<?html echo htmlspecialchars($product['price']); ?>">
                    <input type="hidden" name="product_image" value="<?html echo htmlspecialchars($product['image']); ?>">
                    <button type="submit" name="add_to_cart">Add to Cart</button>
                </form>
                </div>
            </article>
            <?html endforeach; ?>
        <?html endif; ?>
      </section>
    </div>
  </main>

  <!-- Cart Modal -->
  <div id="cartModal" class="cart-modal" role="dialog" aria-modal="true" aria-labelledby="cartModalTitle">
    <div class="cart-modal-content">
      <span class="close-button" aria-label="Close cart">&times;</span>
      <h2 id="cartModalTitle">Your Shopping Cart</h2>
      <ul class="cart-items">
        <?html if (empty($_SESSION['cart'])): ?>
          <li style="text-align: center; color: var(--color-text);">Your cart is empty.</li>
        <?html else: ?>
          <?html
          $total_cart_price = 0;
          foreach ($_SESSION['cart'] as $item):
              $item_total = $item['price'] * $item['quantity'];
              $total_cart_price += $item_total;
          ?>
            <li class="cart-item">
              <img src="<?html echo htmlspecialchars($item['image']); ?>" alt="<?html echo htmlspecialchars($item['name']); ?>">
              <div class="cart-item-details">
                <h5><?html echo htmlspecialchars($item['name']); ?></h5>
                <p>Quantity: <?html echo htmlspecialchars($item['quantity']); ?></p>
              </div>
              <div class="cart-item-price">$<?html echo number_format($item_total, 2); ?></div>
              <a href="ourproducts.html?remove_from_cart=<?html echo htmlspecialchars($item['id']); ?>" class="remove-item-btn" aria-label="Remove <?html echo htmlspecialchars($item['name']); ?> from cart">
                <i class="fas fa-trash-alt"></i>
              </a>
            </li>
          <?html endforeach; ?>
        <?html endif; ?>
      </ul>
      <?html if (!empty($_SESSION['cart'])): ?>
        <div class="cart-total">
          Total: $<?html echo number_format($total_cart_price, 2); ?>
        </div>
        <div class="cart-actions">
          <button class="continue-shopping" id="continueShoppingBtn">Continue Shopping</button>
          <button class="checkout" onclick="window.location.href='checkout.html'">Proceed to Checkout</button>
        </div>
      <?html endif; ?>
    </div>
  </div>

  <!-- Footer (identical to index.html) -->
  <footer>
    <div class="footer-container">
      <div class="footer-content">
        <div class="footer-column">
          <h3>Company</h3>
          <ul>
            <li><a href="#">About Us</a></li>
            <li><a href="#">Careers</a></li>
            <li><a href="#">Press</a></li>
          </ul>
        </div>
        
        <div class="footer-column">
          <h3>Support</h3>
          <ul>
            <li><a href="#">Help Center</a></li>
            <li><a href="#">FAQs</a></li>
            <li><a href="#">Contact Support</a></li>
          </ul>
        </div>
        
        <div class="footer-column">
          <h3>Legal</h3>
          <ul>
            <li><a href="PRIVACY-POLICY.html">Privacy Policy</a></li>
            <li><a href="#">Terms of Service</a></li>
            <li><a href="#">Cookie Policy</a></li>
          </ul>
        </div>
        
        <div class="footer-column">
        <h3>Follow Us</h3>
        <ul class="social-links">
          <a href="#" aria-label="Facebook"><i class="fab fa-facebook"></i></a>
          <a href="#" aria-label="Twitter"><i class="fab fa-twitter"></i></a>
          <a href="https://www.instagram.com/didoxx_hub?igsh=MXVod2Z2ZmNvanhkag==" aria-label="Instagram"><i class="fab fa-instagram"></i></a>
        </ul>
        </div>
      </div>
      
      <div class="footer-bottom">
        <p>&copy; 2025 DIDOXX. All rights reserved.</p>
      </div>
    </div>
  </footer>

  <script>
    // Mobile menu toggle
    const menuButton = document.querySelector('.mobile-menu-button');
    const navMenu = document.getElementById('primary-navigation');

    menuButton.addEventListener('click', () => {
      const isExpanded = menuButton.getAttribute('aria-expanded') === 'true';
      menuButton.setAttribute('aria-expanded', String(!isExpanded));
      navMenu.classList.toggle('show');
    });

    // Cart Modal functionality
    const cartBtn = document.getElementById('cart-btn');
    const cartModal = document.getElementById('cartModal');
    const closeButton = document.querySelector('.close-button');
    const continueShoppingBtn = document.getElementById('continueShoppingBtn');

    cartBtn.addEventListener('click', () => {
      cartModal.style.display = 'flex'; // Use flex to center content
    });

    closeButton.addEventListener('click', () => {
      cartModal.style.display = 'none';
    });

    if (continueShoppingBtn) {
      continueShoppingBtn.addEventListener('click', () => {
        cartModal.style.display = 'none';
      });
    }

    // Close modal if user clicks outside of it
    window.addEventListener('click', (event) => {
      if (event.target == cartModal) {
        cartModal.style.display = 'none';
      }
    });
  </script>
</body>
</html>
