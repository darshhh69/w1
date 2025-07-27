<?html
session_start();

if (!isset($_SESSION['user_id']) || $_SESSION['role'] !== 'admin') {
    header("Location: login.html");
    exit();
}

$conn = new mysqli("localhost", "root", "", "didoxx");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Fetch user and contact data
$userCountQuery = $conn->query("SELECT COUNT(*) AS total FROM users");
$userCount = $userCountQuery->fetch_assoc()['total'] ?? 0;
$usersQuery = $conn->query("SELECT id, username, email, role, created_at FROM users ORDER BY id DESC LIMIT 10");
$contactQuery = $conn->query("SELECT * FROM contact ORDER BY submitted_at DESC");

// Initialize cart
if (!isset($_SESSION['cart'])) {
    $_SESSION['cart'] = [];
}
$cart_item_count = 0;
foreach ($_SESSION['cart'] as $item) {
    $cart_item_count += $item['quantity'];
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin Dashboard - DIDOXX</title>
    <link rel="stylesheet" href="didox.css" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Inherit styles consistent with contact.html */
        :root {
            --color-bg: #ffffff;
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
            display: none;
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

        @media (max-width: 768px) {
            nav ul {
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
                display: none; /* Hidden by default, show with JS if mobile menu button is enabled */
            }
            nav ul.show {
                display: flex;
            }
            .mobile-menu-button {
                display: flex;
            }
        }

        h1, h2, h3 {
            font-family: var(--font-heading);
            color: var(--color-heading);
            margin-bottom: 1rem;
            line-height: 1.1;
        }
        h1 { font-size: 3.5rem; text-align: center; }
        h2 { font-size: 2.5rem; text-align: center; }
        h3 { font-size: 1.75rem; }

        .main-container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1rem;
        }

        .dashboard-header {
            text-align: center;
            margin-bottom: 2rem;
            padding: 1.5rem;
            background-color: #f9fafb;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow-light);
        }

        .stats-card {
            background: var(--color-bg);
            border-radius: var(--border-radius);
            padding: 1.5rem;
            margin-bottom: 2rem;
            box-shadow: var(--shadow-light);
            text-align: center;
        }
        .stats-card h3 {
            margin-top: 0;
            margin-bottom: 0.75rem;
            color: var(--color-primary);
        }
        .stats-card p {
            font-size: 1.1rem;
            color: var(--color-text);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 1rem 0;
            background: var(--color-bg);
            box-shadow: var(--shadow-light);
            border-radius: var(--border-radius);
            overflow: hidden;
        }

        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #eee;
            color: var(--color-text);
        }

        th {
            background-color: var(--color-accent);
            color: white;
            font-weight: 600;
        }

        tr:nth-child(even) {
            background-color: #f8f9fa;
        }

        tr:hover {
            background-color: #f1f1f1;
        }

        .action-links {
            margin-top: 2rem;
            text-align: center;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 1rem;
        }

        .action-links a {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.75rem 1.5rem;
            background: var(--color-accent);
            color: white;
            text-decoration: none;
            border-radius: 0.5rem;
            transition: background-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
            font-weight: 600;
            font-size: 1rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .action-links a:hover {
            background: #10375c;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }

        /* Dropdown styles (copied from contact.html) */
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

        /* Cart button styling (copied from contact.html) */
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

        /* Cart Modal Styles (copied from contact.html) */
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

        /* Footer Styles (identical to contact.html) */
        footer {
            background: #000;
            color: #fff;
            padding: 3rem 2; /* Adjusted padding */
            margin-top: 3rem;
            border-radius: 0%;
        }

        .footer-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1rem;
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
            display: inline; /* Changed to inline to match contact.html */
            gap: 1rem; /* Changed to 2rem to match contact.html */
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
      /* Added for consistency with ourproducts.html */
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

    @media (max-width: 200px) {
      .footer-content {
        grid-template-columns: 1fr;
      }
      
      h1 {
        font-size: 2rem;
      }
      /* Added for consistency with ourproducts.html */
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
     /* Hero Section */
    .hero {
      background-color: #f9fafb;
      border-radius: var(--border-radius);
      padding: 3rem 2rem;
      text-align: center;
      margin: 2rem 0 4rem;
      box-shadow: var(--shadow-light);
    }
    .hero h1 {
      font-family: var(--font-heading);
      font-weight: 800;
      font-size: 3rem;
      color: var(--color-heading);
      margin-bottom: 1rem;
      line-height: 1.2;
    }
    .hero p {
      font-size: 1.125rem;
      color: var(--color-text);
      max-width: 700px;
      margin: 0 auto 2rem;
      line-height: 1.5;
    }
    .hero .btn-primary {
      background-color: var(--color-accent);
      color: white;
      font-weight: 700;
      font-size: 1.125rem;
      padding: 0.75rem 2.5rem;
      border: none;
      border-radius: 0.5rem;
      cursor: pointer;
      transition: background-color 0.3s ease;
      text-decoration: none;
      display: inline-block;
    }
    .hero .btn-primary:hover,
    .hero .btn-primary:focus {
      background-color: #10375c;
      outline: none;
				  
					  
					   
    }
    </style>
</head>
<body>
    <header>
        <a href="didox.html" aria-label="Home" class="logo">DIDOXX</a>
        <button class="mobile-menu-button" aria-expanded="false" aria-controls="primary-navigation" aria-label="Toggle menu">
            <svg viewBox="0 0 24 24" aria-hidden="true" focusable="false">
                <line x1="3" y1="6" x2="21" y2="6"></line>
                <line x1="3" y1="12" x2="21" y2="12"></line>
                <line x1="3" y1="18" x2="21" y2="18"></line>
            </svg>
        </button>
        <nav>
            <ul id="primary-navigation" role="menu">
                <li><a href="index.html" role="menuitem" tabindex="0">Home</a></li>
                <li><a href="add_product.html"><i class="fas fa-box"></i> Manage Products</a></li>
                <li><a href="admin_orders_summary.html"><i class="fas fa-clipboard-list"></i> View Orders</a></li>
                <li><a href="admin_contacts.html"><i class="fas fa-envelope"></i> Contact Messages</a></li>
                <li><a href="login.html?action=logout"><i class="fas fa-sign-out-alt"></i> Logout</a></li>
                <li class="dropdown" a href="#" class="dropbtn" role="menuitem" tabindex="0">
                    <img src="studio/user0.png" alt="User Profile" style="width: 25px; height: 24px;">
                  </a>
                  <div class="dropdown-content">
                    <?html if (isset($_SESSION['user_id'])): ?>
                      <a href="#"><?html echo htmlspecialchars($_SESSION['username']); ?></a>
                      <a href="login.html?action=logout">Logout</a>
                    <?html else: ?>
                      <a href="login.html">Login</a>
                      <a href="registration.html">Register</a>
                    <?html endif; ?>
                  </div>
                </li>
            </ul>
            <!-- Cart Button (copied from contact.html) -->
            <button class="cart-btn" id="cart-btn" aria-label="View Shopping Cart">
                <i class="fas fa-shopping-cart"></i>
                <span class="cart-count" id="cart-count"><?html echo $cart_item_count; ?></span>
            </button>
        </nav>
    </header>

    <div class="main-container container">
        <div class="dashboard-header">
            <h2>Admin Dashboard</h2>
            <p>Welcome back, <?= htmlspecialchars($_SESSION['username']) ?></p>
        </div>

        <div class="stats-card">
            <h3>Website Statistics</h3>
            <p>Total Registered Users: <strong><?= $userCount ?></strong></p>
        </div>

        <h3>Recent Users</h3>
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Username</th>
                    <th>Email</th>
                    <th>Role</th>
                    <th>Join Date</th>
                </tr>
            </thead>
            <tbody>
                <?html while($user = $usersQuery->fetch_assoc()): ?>
                    <tr>
                        <td><?= $user['id'] ?></td>
                        <td><?= htmlspecialchars($user['username']) ?></td>
                        <td><?= htmlspecialchars($user['email']) ?></td>
                        <td><?= ucfirst($user['role']) ?></td>
                        <td><?= date('M d, Y', strtotime($user['created_at'])) ?></td>
                    </tr>
                <?html endwhile; ?>
            </tbody>
        </table>

        
    </div>

    <!-- Cart Modal (copied from contact.html) -->
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
                            <img src="<?html echo htmlspecialchars($item['image'] ?? 'placeholder.jpg'); ?>" alt="<?html echo htmlspecialchars($item['name'] ?? 'Product'); ?>">
                            <div class="cart-item-details">
                                <h5><?html echo htmlspecialchars($item['name'] ?? 'Unknown Product'); ?></h5>
                                <p>Quantity: <?html echo htmlspecialchars($item['quantity']); ?></p>
                            </div>
                            <div class="cart-item-price">$<?html echo number_format($item_total, 2); ?></div>
                            <a href="ourproducts.html?remove_from_cart=<?html echo htmlspecialchars($item['id']); ?>" class="remove-item-btn" aria-label="Remove <?html echo htmlspecialchars($item['name'] ?? 'item'); ?> from cart">
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
                    <button class="checkout" onclick="window.location.href='ourproducts.html'">Go to Products</button>
                </div>
            <?html endif; ?>
        </div>
    </div>

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

        if (menuButton && navMenu) {
            menuButton.addEventListener('click', () => {
                const isExpanded = menuButton.getAttribute('aria-expanded') === 'true';
                menuButton.setAttribute('aria-expanded', String(!isExpanded));
                navMenu.classList.toggle('show');
            });
        }

        // Cart Modal functionality (copied from contact.html)
        const cartBtn = document.getElementById('cart-btn');
        const cartModal = document.getElementById('cartModal');
        const closeButton = document.querySelector('.close-button');
        const continueShoppingBtn = document.getElementById('continueShoppingBtn');

        if (cartBtn) { // Check if cartBtn exists before adding event listener
            cartBtn.addEventListener('click', () => {
                cartModal.style.display = 'flex'; // Use flex to center content
            });
        }

        if (closeButton) { // Check if closeButton exists
            closeButton.addEventListener('click', () => {
                cartModal.style.display = 'none';
            });
        }

        if (continueShoppingBtn) { // Check if continueShoppingBtn exists
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

<?html $conn->close(); ?>
