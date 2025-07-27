<?html
session_start();

// Initialize cart if not already set
if (!isset($_SESSION['cart'])) {
    $_SESSION['cart'] = [];
}

// Handle quantity update
if (isset($_POST['update_quantity'])) {
    $product_id = $_POST['product_id'];
    $new_quantity = (int)$_POST['quantity'];

    foreach ($_SESSION['cart'] as &$item) {
        if ($item['id'] == $product_id) {
            if ($new_quantity > 0) {
                $item['quantity'] = $new_quantity;
            } else {
                // If quantity is 0 or less, remove the item
                unset($_SESSION['cart'][array_search($item, $_SESSION['cart'])]);
            }
            break;
        }
    }
    $_SESSION['cart'] = array_values($_SESSION['cart']); // Re-index array
    header('Location: checkout.html');
    exit();
}

// Handle Remove from Cart action (similar to ourproducts.html but for checkout page)
if (isset($_GET['remove_from_cart'])) {
    $product_id_to_remove = $_GET['remove_from_cart'];
    foreach ($_SESSION['cart'] as $key => $item) {
        if ($item['id'] == $product_id_to_remove) {
            unset($_SESSION['cart'][$key]);
            break;
        }
    }
    $_SESSION['cart'] = array_values($_SESSION['cart']); // Re-index array
    header('Location: checkout.html');
    exit();
}

// Handle Place Order action
if (isset($_POST['place_order'])) {
    // In a real application, you would:
    // 1. Validate shipping information (you can add server-side validation here)
    // 2. Save shipping information to session or database temporarily

    // Calculate total again to ensure it's fresh and not tampered with from client-side
    $subtotal_for_order = 0;
    foreach ($_SESSION['cart'] as $item) {
        $subtotal_for_order += $item['price'] * $item['quantity'];
    }
    $shipping_cost_for_order = ($subtotal_for_order > 0) ? 5.00 : 0.00;
    $total_for_order = $subtotal_for_order + $shipping_cost_for_order;

    // Store the total amount and potentially shipping info in session for the payment page
    $_SESSION['order_total'] = $total_for_order;
    // You might also want to store shipping details if you need them on the payment page
    $_SESSION['shipping_info'] = [
        'full_name' => $_POST['full_name'],
        'address' => $_POST['address'],
        'city' => $_POST['city'],
        'state' => $_POST['state'],
        'zip' => $_POST['zip']
    ];

    // Redirect to the payment page
    header('Location: payment.html');
    exit();
}


// Calculate cart totals
$subtotal = 0;
foreach ($_SESSION['cart'] as $item) {
    $subtotal += $item['price'] * $item['quantity'];
}

$shipping_cost = ($subtotal > 0) ? 5.00 : 0.00; // Flat shipping rate if there are items
$total = $subtotal + $shipping_cost;

// Calculate total items in cart for display in header
$cart_item_count = 0;
foreach ($_SESSION['cart'] as $item) {
    $cart_item_count += $item['quantity'];
}

?>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Checkout - DIDOXX</title>
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
      padding: 0.4rem 1rem;
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
      margin-bottom: 0.1rem;
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

    /* Checkout Page Specific Styles */
    .checkout-container {
        display: flex;
        flex-wrap: wrap;
        gap: 2rem;
        margin-top: 2rem;
    }

    .checkout-section {
        background: var(--color-bg);
        border-radius: var(--border-radius);
        box-shadow: var(--shadow-light);
        padding: 2rem;
        flex: 1;
        min-width: 300px;
    }

    .checkout-section h2 {
        font-family: var(--font-heading);
        color: var(--color-primary);
        margin-top: 0;
        margin-bottom: 1.5rem;
        font-size: 1.8rem;
        border-bottom: 1px solid #eee;
        padding-bottom: 0.75rem;
    }

    /* Cart Summary */
    .checkout-cart-items {
        list-style: none;
        padding: 0;
        margin-bottom: 1.5rem;
    }

    .checkout-cart-item {
        display: flex;
        align-items: center;
        gap: 1rem;
        padding: 1rem 0;
        border-bottom: 1px solid #eee;
        flex-wrap: wrap;
    }

    .checkout-cart-item:last-child {
        border-bottom: none;
    }

    .checkout-cart-item img {
        width: 80px;
        height: 80px;
        object-fit: cover;
        border-radius: 0.5rem;
    }

    .checkout-item-details {
        flex-grow: 1;
    }

    .checkout-item-details h5 {
        margin: 0;
        font-size: 1.1rem;
        color: var(--color-primary);
    }

    .checkout-item-details p {
        margin: 0.25rem 0 0;
        font-size: 0.9rem;
        color: var(--color-text);
    }

    .checkout-item-price {
        font-weight: 600;
        color: var(--color-accent);
        white-space: nowrap;
    }

    .quantity-controls {
        display: flex;
        align-items: center;
        gap: 0.5rem;
    }

    .quantity-controls input[type="number"] {
        width: 60px;
        padding: 0.4rem;
        border: 1px solid #ccc;
        border-radius: 0.3rem;
        text-align: center;
        font-size: 0.9rem;
    }

    .quantity-controls button {
        background-color: var(--color-accent);
        color: white;
        border: none;
        padding: 0.4rem 0.8rem;
        border-radius: 0.3rem;
        cursor: pointer;
        transition: background-color 0.3s ease;
        font-size: 0.9rem;
    }

    .quantity-controls button:hover {
        background-color: #10375c;
    }

    .remove-item-btn {
        background: none;
        border: none;
        color: #e74c3c;
        cursor: pointer;
        font-size: 1.2rem;
        transition: color 0.3s ease;
        margin-left: 1rem;
    }

    .remove-item-btn:hover {
        color: #c0392b;
    }

    .order-summary {
        border-top: 1px solid #eee;
        padding-top: 1.5rem;
        margin-top: 1.5rem;
    }

    .order-summary div {
        display: flex;
        justify-content: space-between;
        margin-bottom: 0.75rem;
        font-size: 1rem;
    }

    .order-summary .total {
        font-size: 1.4rem;
        font-weight: 700;
        color: var(--color-primary);
        margin-top: 1rem;
        padding-top: 1rem;
        border-top: 1px solid #ddd;
    }

    /* Shipping Form */
    .shipping-form .form-group {
        margin-bottom: 1rem;
    }

    .shipping-form label {
        display: block;
        margin-bottom: 0.5rem;
        font-weight: 600;
        color: var(--color-primary);
    }

    .shipping-form input[type="text"] {
        width: 100%;
        padding: 0.75rem;
        border: 1px solid #ccc;
        border-radius: 0.5rem;
        font-size: 1rem;
        font-family: var(--font-body);
    }

    .shipping-form input[type="text"]:focus {
        border-color: var(--color-accent);
        outline: none;
        box-shadow: 0 0 0 3px rgba(0,81,135,0.2);
    }

    .shipping-form .city-state-zip {
        display: flex;
        gap: 1rem;
    }

    .shipping-form .city-state-zip .form-group {
        flex: 1;
    }

    .place-order-btn {
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

    .place-order-btn:hover {
        background-color: #10375c;
        transform: translateY(-2px);
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
    }

    /* Footer Styles (identical to ourproducts.html) */
    footer {
      background: #000;
      color: #fff;
      padding: 3rem 2;
      margin-top: 0.1rem;
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
      .checkout-container {
        flex-direction: column;
      }
    }

    @media (max-width: 200px) {
      .footer-content {
        grid-template-columns: 1fr;
      }
      h1 {
        font-size: 2rem;
      }
      .checkout-cart-item {
        flex-direction: column;
        align-items: flex-start;
        text-align: left;
      }
      .checkout-cart-item img {
        margin-bottom: 0.5rem;
      }
      .checkout-item-price {
        align-self: flex-end;
      }
      .remove-item-btn {
        position: absolute; /* Adjust if needed, might overlap with quantity controls */
        top: 1rem;
        right: 1rem;
      }
      .quantity-controls {
        width: 100%;
        justify-content: space-between;
      }
      .shipping-form .city-state-zip {
        flex-direction: column;
        gap: 0;
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
      <h1>Checkout</h1>
      <p class="lead">Please review your order and provide your shipping details.</p>

      <div class="checkout-container">
        <section class="checkout-section" style="flex: 2;">
          <h2>Your Order</h2>
          <?html if (empty($_SESSION['cart'])): ?>
            <p style="text-align: center; color: var(--color-text);">Your cart is empty. Please add items to proceed to checkout.</p>
            <div style="text-align: center; margin-top: 2rem;">
                <a href="ourproducts.html" class="place-order-btn" style="display: inline-block; width: auto; padding: 0.75rem 1.5rem;">Continue Shopping</a>
            </div>
          <?html else: ?>
            <ul class="checkout-cart-items">
              <?html foreach ($_SESSION['cart'] as $item): ?>
                <li class="checkout-cart-item">
                  <img src="<?html echo htmlspecialchars($item['image']); ?>" alt="<?html echo htmlspecialchars($item['name']); ?>">
                  <div class="checkout-item-details">
                    <h5><?html echo htmlspecialchars($item['name']); ?></h5>
                    <p>Price: $<?html echo number_format($item['price'], 2); ?></p>
                    <form class="quantity-controls" method="post" action="checkout.html">
                        <input type="hidden" name="product_id" value="<?html echo htmlspecialchars($item['id']); ?>">
                        <label for="quantity-<?html echo htmlspecialchars($item['id']); ?>" class="sr-only">Quantity for <?html echo htmlspecialchars($item['name']); ?></label>
                        <input type="number" id="quantity-<?html echo htmlspecialchars($item['id']); ?>" name="quantity" value="<?html echo htmlspecialchars($item['quantity']); ?>" min="1" max="99" aria-label="Quantity">
                        <button type="submit" name="update_quantity">Update</button>
                    </form>
                  </div>
                  <div class="checkout-item-price">$<?html echo number_format($item['price'] * $item['quantity'], 2); ?></div>
                  <a href="checkout.html?remove_from_cart=<?html echo htmlspecialchars($item['id']); ?>" class="remove-item-btn" aria-label="Remove <?html echo htmlspecialchars($item['name']); ?> from cart">
                    <i class="fas fa-trash-alt"></i>
                  </a>
                </li>
              <?html endforeach; ?>
            </ul>

            <div class="order-summary">
              <div>
                <span>Subtotal:</span>
                <span>$<?html echo number_format($subtotal, 2); ?></span>
              </div>
              <div>
                <span>Shipping:</span>
                <span>$<?html echo number_format($shipping_cost, 2); ?></span>
              </div>
              <div class="total">
                <span>Order Total:</span>
                <span>$<?html echo number_format($total, 2); ?></span>
              </div>
            </div>
          <?html endif; ?>
        </section>

        <?html if (!empty($_SESSION['cart'])): ?>
        <section class="checkout-section" style="flex: 1;">
          <h2>Shipping Information</h2>
          <form class="shipping-form" method="post" action="checkout.html">
            <div class="form-group">
              <label for="full_name">Full Name</label>
              <input type="text" id="full_name" name="full_name" required aria-required="true">
            </div>
            <div class="form-group">
              <label for="address">Address</label>
              <input type="text" id="address" name="address" required aria-required="true">
            </div>
            <div class="city-state-zip">
              <div class="form-group">
                <label for="city">City</label>
                <input type="text" id="city" name="city" required aria-required="true">
              </div>
              <div class="form-group">
                <label for="state">State</label>
                <input type="text" id="state" name="state" required aria-required="true">
              </div>
              <div class="form-group">
                <label for="zip">Zip Code</label>
                <input type="text" id="zip" name="zip" required aria-required="true">
              </div>
            </div>
            <button type="submit" name="place_order" class="place-order-btn">Place Order</button>
          </form>
        </section>
        <?html endif; ?>
      </div>
    </div>
  </main>

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

    // No cart modal needed on checkout page, but keeping the script structure for consistency
    // You can remove the cart modal related JS if you wish, as it's not used here.
    const cartBtn = document.getElementById('cart-btn');
    if (cartBtn) {
        cartBtn.addEventListener('click', () => {
            // On checkout page, clicking cart button might just scroll to top or do nothing
            // or you could redirect to ourproducts.html if desired.
            // For now, it does nothing specific.
        });
    }
  </script>
</body>
</html>
