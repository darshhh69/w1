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

$upload_dir = "studio/";

// Handle delete
if (isset($_POST['delete_id'])) {
    $delete_id = $_POST['delete_id'];
    $conn->query("DELETE FROM products WHERE id = $delete_id");
}

// Handle edit fetch
$editing = false;
$edit_product = [];
if (isset($_POST['edit_id'])) {
    $edit_id = $_POST['edit_id'];
    $result = $conn->query("SELECT * FROM products WHERE id = $edit_id");
    if ($result->num_rows > 0) {
        $edit_product = $result->fetch_assoc();
        $editing = true;
    }
}

// Handle form submission
if ($_SERVER["REQUEST_METHOD"] == "POST" && isset($_POST['submit_product'])) {
    $name = $_POST['product_name'];
    $description = $_POST['description'];
    $price = $_POST['price'];
    $stock = $_POST['stock'];

    // Handle image upload
    $imagePath = $edit_product['image'] ?? ''; // Default to old image
    if (isset($_FILES['image']) && $_FILES['image']['error'] === 0) {
        $imageName = basename($_FILES['image']['name']);
        $targetFile = $upload_dir . time() . "_" . $imageName;
        move_uploaded_file($_FILES["image"]["tmp_name"], $targetFile);
        $imagePath = $targetFile;
    }

    if (isset($_POST['editing_id'])) {
        // Update product
        $update_id = $_POST['editing_id'];
        $stmt = $conn->prepare("UPDATE products SET name=?, description=?, price=?, image=?, stock=? WHERE id=?");
        $stmt->bind_param("ssdsii", $name, $description, $price, $imagePath, $stock, $update_id);
        $stmt->execute();
        $stmt->close();
        echo "<script>alert('Product updated!'); window.location='add_product.html';</script>";
        exit();
    } else {
        // Add new product
        $stmt = $conn->prepare("INSERT INTO products (name, description, price, image, stock) VALUES (?, ?, ?, ?, ?)");
        $stmt->bind_param("ssdsi", $name, $description, $price, $imagePath, $stock);
        $stmt->execute();
        $stmt->close();
        echo "<script>alert('Product added!'); window.location='add_product.html';</script>";
        exit();
    }
}

// Get all products
$products = $conn->query("SELECT * FROM products ORDER BY id DESC");
?>

<!DOCTYPE html>
<html>
<head>
    <title>Admin - Add/Edit Product</title>
    <style>
        table, th, td { border: 1px solid #aaa; border-collapse: collapse; padding: 8px; }
    </style>
</head>
<body>
    <h2><?= $editing ? 'Edit' : 'Add New' ?> Product</h2>
    <form method="post" enctype="multipart/form-data">
        <?html if ($editing): ?>
            <input type="hidden" name="editing_id" value="<?= $edit_product['id'] ?>">
        <?html endif; ?>

        <label>Product Name:</label><br>
        <input type="text" name="product_name" value="<?= $edit_product['name'] ?? '' ?>" required><br><br>

        <label>Description:</label><br>
        <textarea name="description" rows="4" required><?= $edit_product['description'] ?? '' ?></textarea><br><br>

        <label>Price (₹):</label><br>
        <input type="number" step="0.01" name="price" value="<?= $edit_product['price'] ?? '' ?>" required><br><br>

        <label>Image (Upload):</label><br>
        <input type="file" name="image" accept="image/*"><br>
        <?html if (!empty($edit_product['image'])): ?>
            <img src="<?= $edit_product['image'] ?>" width="100"><br>
        <?html endif; ?>
        <br>

        <label>Stock:</label><br>
        <input type="number" name="stock" value="<?= $edit_product['stock'] ?? 0 ?>" min="0"><br><br>

        <button type="submit" name="submit_product"><?= $editing ? 'Update' : 'Add' ?> Product</button>
    </form>

    <hr>
    <h2>All Products</h2>
    <table>
        <tr>
            <th>ID</th><th>Name</th><th>Price</th><th>Stock</th><th>Image</th><th>Actions</th>
        </tr>
        <?html while ($product = $products->fetch_assoc()): ?>
            <tr>
                <td><?= $product['id'] ?></td>
                <td><?= htmlspecialchars($product['name']) ?></td>
                <td>₹<?= $product['price'] ?></td>
                <td><?= $product['stock'] ?></td>
                <td><img src="<?= htmlspecialchars($product['image']) ?>" width="60"></td>
                <td>
                    <form method="post" style="display:inline;">
                        <input type="hidden" name="edit_id" value="<?= $product['id'] ?>">
                        <button type="submit">Edit</button>
                    </form>
                    <form method="post" style="display:inline;" onsubmit="return confirm('Are you sure to delete this product?');">
                        <input type="hidden" name="delete_id" value="<?= $product['id'] ?>">
                        <button type="submit">Delete</button>
                    </form>
                </td>
            </tr>
        <?html endwhile; ?>
    </table>
</body>
</html>
