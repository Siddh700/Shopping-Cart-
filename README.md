# Shopping-Cart-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Simple Add to Cart</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f2f2f2;
      margin: 0;
      padding: 20px;
    }

    h1 {
      text-align: center;
    }

    .container {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: center;
    }

    .product {
      background: white;
      padding: 15px;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      width: 200px;
      text-align: center;
    }

    .product button {
      background: #28a745;
      color: white;
      padding: 8px 12px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 10px;
    }

    .cart {
      margin-top: 40px;
      background: white;
      padding: 20px;
      border-radius: 8px;
      max-width: 400px;
      margin-left: auto;
      margin-right: auto;
    }

    ul {
      list-style: none;
      padding: 0;
    }

    li {
      margin: 8px 0;
    }
  </style>
</head>
<body>

  <h1>Simple Shopping Cart</h1>

  <div class="container" id="product-list">
    <!-- Products will be inserted here -->
  </div>

  <div class="cart">
    <h2>Your Cart</h2>
    <ul id="cart-items"></ul>
    <p><strong>Total: $<span id="total">0.00</span></strong></p>
  </div>

  <script>
    const products = [
      { id: 1, name: "Product A", price: 10.00 },
      { id: 2, name: "Product B", price: 15.50 },
      { id: 3, name: "Product C", price: 7.25 }
    ];

    const cart = [];
    const productList = document.getElementById('product-list');
    const cartItems = document.getElementById('cart-items');
    const totalSpan = document.getElementById('total');

    function renderProducts() {
      products.forEach(product => {
        const div = document.createElement('div');
        div.className = 'product';
        div.innerHTML = `
          <h3>${product.name}</h3>
          <p>Price: $${product.price.toFixed(2)}</p>
          <button onclick="addToCart(${product.id})">Add to Cart</button>
        `;
        productList.appendChild(div);
      });
    }

    function addToCart(productId) {
      const product = products.find(p => p.id === productId);
      cart.push(product);
      renderCart();
    }

    function renderCart() {
      cartItems.innerHTML = '';
      let total = 0;
      cart.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.name} - $${item.price.toFixed(2)}`;
        cartItems.appendChild(li);
        total += item.price;
      });
      totalSpan.textContent = total.toFixed(2);
    }

    renderProducts();
  </script>

</body>
</html>
