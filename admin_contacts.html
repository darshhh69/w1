<?html
session_start();

// Only allow admin access
if (!isset($_SESSION['user_id']) || $_SESSION['role'] !== 'admin') {
    header("Location: login.html");
    exit();
}

// Connect to the database
$conn = new mysqli("localhost", "root", "", "didoxx");
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Fetch contact messages
$contactQuery = $conn->query("SELECT * FROM contact ORDER BY submitted_at DESC");

// Optional: fetch cart count (for header icon)
if (!isset($_SESSION['cart'])) {
    $_SESSION['cart'] = [];
}
$cart_item_count = 0;
foreach ($_SESSION['cart'] as $item) {
    $cart_item_count += (int)$item['quantity'];
}
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Admin - Contact Messages</title>
    <link rel="stylesheet" href="style.css"> <!-- your main CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        body {
            background: #f9f9f9;
            font-family: Arial, sans-serif;
            padding: 20px;
        }
        table {
            border-collapse: collapse;
            width: 100%;
            background: #fff;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        table th, table td {
            padding: 12px;
            border: 1px solid #ccc;
            text-align: left;
        }
        table th {
            background-color: #333;
            color: #fff;
        }
        h2 {
            margin-bottom: 20px;
        }
        .back-btn {
            display: inline-block;
            margin-bottom: 15px;
            padding: 8px 16px;
            background: #444;
            color: white;
            text-decoration: none;
            border-radius: 5px;
        }
        .back-btn:hover {
            background: #000;
        }
    </style>
</head>
<body>

<a class="back-btn" href="admin.html"><i class="fas fa-arrow-left"></i> Back to Admin Dashboard</a>

<h2>Contact Messages</h2>

<?html if ($contactQuery->num_rows > 0): ?>
    <table>
        <thead>
            <tr>
                <th>ID</th>
                <th>Name</th>
                <th>Email</th>
                <th>Phone</th>
                <th>Subject</th>
                <th>Message</th>
                <th>Submitted At</th>
            </tr>
        </thead>
        <tbody>
            <?html while ($row = $contactQuery->fetch_assoc()): ?>
            <tr>
                <td><?= htmlspecialchars($row['id']) ?></td>
                <td><?= htmlspecialchars($row['name']) ?></td>
                <td><?= htmlspecialchars($row['email']) ?></td>
                <td><?= htmlspecialchars($row['phone']) ?></td>
                <td><?= htmlspecialchars($row['subject']) ?></td>
                <td><?= nl2br(htmlspecialchars($row['message'])) ?></td>
                <td><?= htmlspecialchars($row['submitted_at']) ?></td>
            </tr>
            <?html endwhile; ?>
        </tbody>
    </table>
<?html else: ?>
    <p>No contact messages found.</p>
<?html endif; ?>

</body>
</html>
