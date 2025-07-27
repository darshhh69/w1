<?html
session_start();


// Check if user is logged in
if (!isset($_SESSION['user_id'])) {
    // Redirect to login page
    header("Location: login.html");
    exit();
}

// Redirect to checkout if cart or order total is not set
if (!isset($_SESSION['cart']) || empty($_SESSION['cart']) || !isset($_SESSION['order_total'])) {
    header('Location: checkout.html');
    exit();
}

$order_total = $_SESSION['order_total'];
$shipping_info = $_SESSION['shipping_info'] ?? [];

// Variable to control popup display
$payment_successful = false;
$payment_method_used = '';

// Handle payment submission (placeholder)
if (isset($_POST['process_payment'])) {
    // In a real application, you would integrate with a payment gateway here.
    // This is a placeholder for demonstration purposes.

    // The 'payment_method' field from the form will tell us which method was chosen.
    $payment_method = $_POST['payment_method'] ?? 'unknown';

    // For demonstration, let's simulate a successful payment for any method
    // In a real scenario, each method would have its own validation and API call.

    // Set flag for successful payment and store method
    $payment_successful = true;
    $payment_method_used = $payment_method;

    // Clear the cart and session variables related to the order after successful payment
    unset($_SESSION['cart']);
    unset($_SESSION['order_total']);
    unset($_SESSION['shipping_info']);

    // IMPORTANT: We are NOT redirecting here anymore.
    // The page will reload, and the JavaScript will detect $payment_successful.
}

// Calculate total items in cart for display in header (same as checkout.html)
$cart_item_count = 0;
if (isset($_SESSION['cart'])) {
    foreach ($_SESSION['cart'] as $item) {
        $cart_item_count += $item['quantity'];
    }
}

?>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Payment - DIDOXX</title>
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

      /* Ensure cart button is visible and correctly ordered on mobile */
      .cart-btn {
        order: 2; /* Place it after the mobile menu button */
      }
    }

    h1 {
      font-family: var(--font-heading);
      font-weight: 800;
      font-size: 3.5rem;
      color: var(--color-heading);
      margin-bottom: 1rem;
      line-height: 1.1;
      text-align: center;
    }

    p.lead {
      font-size: 1.125rem;
      color: var(--color-text);
      max-width: 700px;
      margin: 0 auto 3rem;
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

    /* Cart button styling */
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

    /* Payment Page Specific Styles */
    .payment-container {
        display: flex;
        flex-direction: column;
        gap: 2rem;
        margin-top: 2rem;
        max-width: 700px;
        margin-left: auto;
        margin-right: auto;
    }

    .payment-section {
        background: var(--color-bg);
        border-radius: var(--border-radius);
        box-shadow: var(--shadow-light);
        padding: 2rem;
    }

    .payment-section h2 {
        font-family: var(--font-heading);
        color: var(--color-primary);
        margin-top: 0;
        margin-bottom: 1.5rem;
        font-size: 1.8rem;
        border-bottom: 1px solid #eee;
        padding-bottom: 0.75rem;
    }

    .order-details, .shipping-details {
        margin-bottom: 1.5rem;
    }

    .order-details div, .shipping-details div {
        display: flex;
        justify-content: space-between;
        margin-bottom: 0.75rem;
        font-size: 1rem;
            align-items

: baseline;
    flex-direction: column;
    }

    .order-details .total-amount {
        font-size: 1.6rem;
        font-weight: 700;
        color: var(--color-primary);
        margin-top: 1rem;
        padding-top: 1rem;
        border-top: 1px solid #ddd;
    }

    .shipping-details p {
        margin: 0.5rem 0;
        color: var(--color-primary);
        font-weight: 500;
    }

    .payment-form .form-group {
        margin-bottom: 1rem;
    }

    .payment-form label {
        display: block;
        margin-bottom: 0.5rem;
        font-weight: 600;
        color: var(--color-primary);
    }

    .payment-form input[type="text"],
    .payment-form input[type="number"],
    .payment-form input[type="month"],
    .payment-form select { /* Added select for payment methods */
        width: 100%;
        padding: 0.75rem;
        border: 1px solid #ccc;
        border-radius: 0.5rem;
        font-size: 1rem;
        font-family: var(--font-body);
    }

    .payment-form input[type="text"]:focus,
    .payment-form input[type="number"]:focus,
    .payment-form input[type="month"]:focus,
    .payment-form select:focus {
        border-color: var(--color-accent);
        outline: none;
        box-shadow: 0 0 0 3px rgba(0,81,135,0.2);
    }

    .payment-form .card-details {
        display: flex;
        gap: 1rem;
    }

    .payment-form .card-details .form-group {
        flex: 1;
    }

    /* Styles for payment method selection */
    .payment-method-options {
        margin-bottom: 1.5rem;
    }

    .payment-method-options .method-group {
        margin-bottom: 1rem;
        border: 1px solid #ededed;
        border-radius: 0.5rem;
        padding: 1rem;
        background-color: #f2f6fd;
    }

    .payment-method-options .method-group h3 {
        font-size: 1.2rem;
        color: var(--color-primary);
        margin-top: 0;
        margin-bottom: 0.75rem;
        border-bottom: 1px solid #ddd;
        padding-bottom: 0.5rem;
    }

    .payment-method-options .radio-option {
        display: flex;
        align-items: center;
        margin-bottom: 0.5rem;
        cursor: pointer;
        padding: 0.5rem;
        border-radius: 0.3rem;
        transition: background-color 0.2s ease;
    }

    .payment-method-options .radio-option:hover {
        background-color: #f0f0f0;
    }

    .payment-method-options input[type="radio"] {
        margin-right: 0.75rem;
        transform: scale(1.2);
    }

    .payment-method-options label {
        font-weight: 500;
        color: var(--color-primary);
        cursor: pointer;
        margin-bottom: 0; /* Override default label margin */
    }

    /* Specific form fields for Card Payment */
    #card_payment_fields {
        display: none; /* Hidden by default */
        margin-top: 1rem;
        padding-top: 1rem;
        border-top: 1px solid #eee;
    }

    /* Specific form fields for Net Banking */
    #net_banking_fields {
        display: none; /* Hidden by default */
        margin-top: 1rem;
        padding-top: 1rem;
        border-top: 1px solid #eee;
    }

    .process-payment-btn {
        background-color: var(--color-accent);
        color: white;
        font-weight: 600;
        font-size: 1.1rem;
        padding: 1rem 2rem;
        border: none;
        border-radius: 0.5rem;
        cursor: pointer;
        transition: background-color 0.3s ease, transform 0.3s ease;
        width: 100%;
        margin-top: 1.5rem;
    }

    .process-payment-btn:hover {
        background-color: #10375c;
        transform: translateY(-2px);
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
    }

    /* Footer Styles (identical to ourproducts.html) */
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

    @media (max-width: 768px) {
      .footer-content {
        grid-template-columns: repeat(2, 1fr);
      }
      h1 {
        font-size: 2.5rem;
      }
      .payment-container {
        padding: 0 1rem;
      }
      .payment-form .card-details {
        flex-direction: column;
        gap: 0;
      }
    }

    @media (max-width: 200px) {
      .footer-content {
        grid-template-columns: 1fr;
      }
      h1 {
        font-size: 2rem;
      }
    }

    /* Styles for the Confirmation Modal/Popup */
    .modal {
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

    .modal-content {
      background-color: #fefefe;
      margin: auto;
      padding: 30px;
      border: 1px solid #888;
      width: 80%;
      max-width: 500px;
      border-radius: var(--border-radius);
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
      text-align: center;
      position: relative;
      animation: animatetop 0.4s;
    }

    @keyframes animatetop {
      from {top: -300px; opacity: 0}
      to {top: 0; opacity: 1}
    }

    .modal-content h2 {
      color: var(--color-primary);
      font-size: 2rem;
      margin-bottom: 1rem;
    }

    .modal-content p {
      font-size: 1.1rem;
      color: var(--color-text);
      margin-bottom: 1.5rem;
    }

    .modal-content .close-btn {
      background-color: var(--color-accent);
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 0.5rem;
      cursor: pointer;
      font-size: 1rem;
      transition: background-color 0.3s ease;
    }

    .modal-content .close-btn:hover {
      background-color: #10375c;
    }

    .modal-content .icon {
        font-size: 4rem;
        color: #28a745; /* Green for success */
        margin-bottom: 1rem;
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
      <h1>Payment Information</h1>
      <p class="lead">Please select your preferred payment method and provide details.</p>

      <div class="payment-container">
        <section class="payment-section">
          <h2>Order Summary</h2>
          <div class="order-details">
            <div>
              <span>Order Total:</span>
              <span class="total-amount">$<?html echo number_format($order_total, 2); ?></span>
            </div>
          </div>

          <h2>Shipping Details</h2>
          <div class="shipping-details">
            <?html if (!empty($shipping_info)): ?>
              <p><strong>Full Name:</strong> <?html echo htmlspecialchars($shipping_info['full_name']); ?></p>
              <p><strong>Address:</strong> <?html echo htmlspecialchars($shipping_info['address']); ?></p>
              <p><strong>City:</strong> <?html echo htmlspecialchars($shipping_info['city']); ?></p>
              <p><strong>State:</strong> <?html echo htmlspecialchars($shipping_info['state']); ?></p>
              <p><strong>Zip Code:</strong> <?html echo htmlspecialchars($shipping_info['zip']); ?></p>
            <?html else: ?>
              <p>Shipping information not available. Please go back to checkout.</p>
            <?html endif; ?>
          </div>
        </section>

        <section class="payment-section">
          <h2>Select Payment Method</h2>
          <form class="payment-form" method="post" action="payment.html">
            <div class="payment-method-options">

              <div class="method-group">
                <h3>UPI / QR Code</h3>
                <div class="radio-option">
                  <input type="radio" id="gpay" name="payment_method" value="Google Pay" required onchange="togglePaymentFields()">
                  <label for="gpay">Google Pay (GPay)</label>
                </div>
                <div class="radio-option">
                  <input type="radio" id="phonepe" name="payment_method" value="PhonePe" onchange="togglePaymentFields()">
                  <label for="phonepe">PhonePe</label>
                </div>
                <div class="radio-option">
                  <input type="radio" id="paytm_upi" name="payment_method" value="Paytm UPI" onchange="togglePaymentFields()">
                  <label for="paytm_upi">Paytm UPI</label>
                </div>
                <div class="radio-option">
                  <input type="radio" id="bhim_app" name="payment_method" value="BHIM App" onchange="togglePaymentFields()">
                  <label for="bhim_app">BHIM App</label>
                </div>
                <div class="radio-option">
                  <input type="radio" id="amazon_pay_upi" name="payment_method" value="Amazon Pay UPI" onchange="togglePaymentFields()">
                  <label for="amazon_pay_upi">Amazon Pay UPI</label>
                </div>
              </div>

              <div class="method-group">
                <h3>Net Banking</h3>
                <div class="radio-option">
                  <input type="radio" id="net_banking" name="payment_method" value="Net Banking" onchange="togglePaymentFields()">
                  <label for="net_banking">Net Banking (Select Bank)</label>
                </div>
                <div id="net_banking_fields">
                    <div class="form-group">
                        <label for="bank_select">Select Bank</label>
                        <select id="bank_select" name="bank_name">
                            <option value="">-- Select Your Bank --</option>
                            <option value="SBI">State Bank of India (SBI)</option>
                            <option value="HDFC">HDFC Bank</option>
                            <option value="ICICI">ICICI Bank</option>
                            <option value="Axis">Axis Bank</option>
                            <option value="Kotak">Kotak Mahindra Bank</option>
                            <option value="Other">Other Bank</option>
                        </select>
                    </div>
                </div>
              </div>

              <div class="method-group">
                <h3>Card Payments</h3>
                <div class="radio-option">
                  <input type="radio" id="card_payment" name="payment_method" value="Card Payment" onchange="togglePaymentFields()">
                  <label for="card_payment">Credit / Debit Card</label>
                </div>
                <div id="card_payment_fields">
                    <div class="form-group">
                      <label for="card_number">Card Number</label>
                      <input type="text" id="card_number" name="card_number" placeholder="XXXX XXXX XXXX XXXX" pattern="[0-9]{13,19}" title="Credit card number (13-19 digits)">
                    </div>
                    <div class="form-group">
                      <label for="card_name">Name on Card</label>
                      <input type="text" id="card_name" name="card_name">
                    </div>
                    <div class="card-details">
                      <div class="form-group">
                        <label for="expiry_date">Expiry Date</label>
                        <input type="month" id="expiry_date" name="expiry_date" placeholder="MM/YY">
                      </div>
                      <div class="form-group">
                        <label for="cvv">CVV</label>
                        <input type="text" id="cvv" name="cvv" placeholder="XXX" pattern="[0-9]{3,4}" title="CVV (3 or 4 digits)">
                      </div>
                    </div>
                </div>
              </div>

              <div class="method-group">
                <h3>Mobile Wallets</h3>
                <div class="radio-option">
                  <input type="radio" id="paytm_wallet" name="payment_method" value="Paytm Wallet" onchange="togglePaymentFields()">
                  <label for="paytm_wallet">Paytm Wallet</label>
                </div>
                <div class="radio-option">
                  <input type="radio" id="mobikwik" name="payment_method" value="Mobikwik" onchange="togglePaymentFields()">
                  <label for="mobikwik">Mobikwik</label>
                </div>
                <div class="radio-option">
                  <input type="radio" id="freecharge" name="payment_method" value="Freecharge" onchange="togglePaymentFields()">
                  <label for="freecharge">Freecharge</label>
                </div>
                <div class="radio-option">
                  <input type="radio" id="amazon_pay_wallet" name="payment_method" value="Amazon Pay Wallet" onchange="togglePaymentFields()">
                  <label for="amazon_pay_wallet">Amazon Pay Wallet</label>
                </div>
              </div>

              <div class="method-group">
                <h3>Cash on Delivery</h3>
                <div class="radio-option">
                  <input type="radio" id="cod" name="payment_method" value="Cash on Delivery" onchange="togglePaymentFields()">
                  <label for="cod">Cash on Delivery (COD)</label>
                </div>
              </div>

            </div>
            <button type="submit" name="process_payment" class="process-payment-btn">Complete Order</button>
          </form>
        </section>
      </div>
    </div>
  </main>

  <!-- Confirmation Modal Structure -->
  <div id="confirmationModal" class="modal">
    <div class="modal-content">
      <span class="icon"><i class="fas fa-check-circle"></i></span>
      <h2>Order Confirmed!</h2>
      <p>Your order has been successfully placed.</p>
      <p>Payment Method: <strong id="paymentMethodDisplay"></strong></p>
      <p>Thank you for your purchase!</p>
      <button class="close-btn" onclick="closeModal()">Continue Shopping</button>
    </div>
  </div>

  <!-- Footer (identical to ourproducts.html) -->
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
    // Mobile menu toggle (from ourproducts.html)
    const menuButton = document.querySelector('.mobile-menu-button');
    const navMenu = document.getElementById('primary-navigation');

    menuButton.addEventListener('click', () => {
      const isExpanded = menuButton.getAttribute('aria-expanded') === 'true';
      menuButton.setAttribute('aria-expanded', String(!isExpanded));
      navMenu.classList.toggle('show');
    });

    // No cart modal needed on payment page, but keeping the script structure for consistency
    const cartBtn = document.getElementById('cart-btn');
    if (cartBtn) {
        cartBtn.addEventListener('click', () => {
            // On payment page, clicking cart button might just scroll to top or do nothing
            // or you could redirect to ourproducts.html if desired.
            // For now, it does nothing specific.
        });
    }

    // JavaScript to toggle specific payment fields based on selection
    function togglePaymentFields() {
        const cardFields = document.getElementById('card_payment_fields');
        const netBankingFields = document.getElementById('net_banking_fields');
        const selectedMethod = document.querySelector('input[name="payment_method"]:checked');

        // Hide all specific fields first
        cardFields.style.display = 'none';
        netBankingFields.style.display = 'none';

        // Make card fields optional by default
        document.getElementById('card_number').removeAttribute('required');
        document.getElementById('card_name').removeAttribute('required');
        document.getElementById('expiry_date').removeAttribute('required');
        document.getElementById('cvv').removeAttribute('required');
        document.getElementById('bank_select').removeAttribute('required');


        if (selectedMethod) {
            if (selectedMethod.value === 'Card Payment') {
                cardFields.style.display = 'block';
                // Make card fields required when selected
                document.getElementById('card_number').setAttribute('required', 'required');
                document.getElementById('card_name').setAttribute('required', 'required');
                document.getElementById('expiry_date').setAttribute('required', 'required');
                document.getElementById('cvv').setAttribute('required', 'required');
            } else if (selectedMethod.value === 'Net Banking') {
                netBankingFields.style.display = 'block';
                document.getElementById('bank_select').setAttribute('required', 'required');
            }
        }
    }

    // Confirmation Modal JavaScript
    const confirmationModal = document.getElementById('confirmationModal');
    const paymentMethodDisplay = document.getElementById('paymentMethodDisplay');

    function showConfirmationModal(method) {
        paymentMethodDisplay.textContent = method;
        confirmationModal.style.display = 'flex'; // Use flex to center content
    }

    function closeModal() {
        confirmationModal.style.display = 'none';
        // Optionally redirect to home or products page after closing modal
        window.location.href = 'ourproducts.html'; // Example: Redirect to products page
    }

    // Check if payment was successful on page load (after form submission)
    document.addEventListener('DOMContentLoaded', () => {
        togglePaymentFields(); // Call this to set initial state of payment fields

        <?html if ($payment_successful): ?>
            showConfirmationModal('<?html echo htmlspecialchars($payment_method_used); ?>');
        <?html endif; ?>
    });
  </script>
</body>
</html>
