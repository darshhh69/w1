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

// Correct SQL query with user email alias
$sql = "SELECT users.username, users.email AS user_email, COUNT(orders.id) AS total_orders
        FROM orders 
        JOIN users ON orders.user_id = users.id
        GROUP BY users.id";

$result = $conn->query($sql);
?>

<!DOCTYPE html>
<html>
<head>
    <title>User Orders Summary</title>
</head>
<body>
    <h2>User Orders Summary</h2>

    <!-- Place your table here -->
    <table border="1">
        <tr>
            <th>User Email</th>
            <th>Total Orders</th>
        </tr>
        <?html while($row = $result->fetch_assoc()): ?>
        <tr>
            <td><?= htmlspecialchars($row['user_email']) ?></td>
            <td><?= $row['total_orders'] ?></td>
        </tr>
        <?html endwhile; ?>
    </table>

</body>
</html>
