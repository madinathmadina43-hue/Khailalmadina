<meta name='viewport' content='width=device-width, initial-scale=1'/><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Khail Al Madina Supermarket</title>
    <style>
        /* Previous styles remain the same – adding form-specific styles */
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f4f4f4;
            position: relative;
        }

        h1, h2, h3 { line-height: 1.2; }
        h1 { font-size: clamp(1.8rem, 6vw, 2.8rem); }
        h2 { font-size: clamp(1.5rem, 5vw, 2.2rem); }
        h3 { font-size: clamp(1.2rem, 4vw, 1.6rem); }
        p   { font-size: clamp(1rem, 3.5vw, 1.1rem); }

        header {
            background-color: #4CAF50;
            color: white;
            text-align: center;
            padding: 1.5rem 1rem;
        }

        nav {
            background-color: #333;
        }

        nav ul {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            list-style: none;
        }

        nav a {
            color: white;
            text-decoration: none;
            padding: 1rem 1.5rem;
            display: block;
            transition: background 0.3s;
        }

        nav a:hover { background-color: #555; }

        section {
            padding: 2rem 1rem;
            text-align: center;
        }

        #home    { background: #fff; }
        #products { background: #f9f9f9; }
        #order    { background: #fffef0; }
        #delivery { background: #fff; }
        #contact  { background: #f9f9f9; }

        .product-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 1.5rem;
            justify-content: center;
            margin-top: 1.5rem;
        }

        .product-item {
            flex: 1 1 280px;
            max-width: 320px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            overflow: hidden;
            transition: transform 0.3s;
        }

        .product-item:hover { transform: translateY(-5px); }

        .product-item img {
            width: 100%;
            height: auto;
            display: block;
        }

        .product-item h3, .product-item p { padding: 0.8rem 1rem; }

        footer {
            background: #333;
            color: white;
            text-align: center;
            padding: 1.5rem;
            margin-top: 2rem;
        }

        /* WhatsApp Button */
        .whatsapp-btn {
            display: inline-block;
            background-color: #25D366;
            color: white !important;
            font-weight: bold;
            text-decoration: none;
            padding: 0.9rem 1.8rem;
            border-radius: 50px;
            margin: 1rem 0;
            transition: all 0.3s;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            font-size: 1.1rem;
        }

        .whatsapp-btn:hover {
            background-color: #128C7E;
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(0,0,0,0.25);
        }

        .whatsapp-btn i { margin-right: 0.5rem; font-size: 1.3rem; }

        .fab-whatsapp {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #25D366;
            color: white;
            width: 65px;
            height: 65px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            box-shadow: 0 5px 15px rgba(0,0,0,0.4);
            z-index: 1000;
            text-decoration: none;
            transition: all 0.3s;
        }

        .fab-whatsapp:hover { transform: scale(1.1); background: #128C7E; }

        /* Order Form Styles */
        #order form {
            max-width: 700px;
            margin: 0 auto;
            background: white;
            padding: 2rem;
            border-radius: 12px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.1);
        }

        .form-group {
            margin-bottom: 1.2rem;
            text-align: left;
        }

        label {
            display: block;
            margin-bottom: 0.4rem;
            font-weight: bold;
        }

        input[type="text"],
        input[type="tel"],
        input[type="number"],
        textarea {
            width: 100%;
            padding: 0.7rem;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 1rem;
        }

        .product-selection {
            margin: 1.5rem 0;
        }

        .product-option {
            display: flex;
            align-items: center;
            margin-bottom: 0.8rem;
            gap: 1rem;
        }

        .product-option input[type="checkbox"] {
            width: 20px;
            height: 20px;
        }

        .product-option label {
            flex: 1;
            margin: 0;
        }

        .quantity-input {
            width: 70px;
            text-align: center;
        }

        .product-price {
            font-size: 0.9rem;
            color: #555;
            margin-left: auto;
        }

        #order-summary {
            background: #f8f9fa;
            padding: 1.2rem;
            border-radius: 8px;
            margin: 1.5rem 0;
            min-height: 100px;
        }

        #summaryText {
            white-space: pre-line;
        }

        #totalPrice {
            font-weight: bold;
            margin-top: 1rem;
        }

        #error-msg {
            color: #d32f2f;
            font-weight: bold;
            margin: 1rem 0;
        }

        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        section, header, nav { animation: fadeIn 1.2s ease-out; }

        @media (min-width: 768px) {
            nav ul { flex-wrap: nowrap; }
            section { padding: 3rem 2rem; }
        }

        @media (min-width: 1024px) {
            header { padding: 3rem 2rem; }
            .product-grid { max-width: 1200px; margin: 2rem auto 0; }
            section { max-width: 1200px; margin: 0 auto; }
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
</head>
<body>

    <header>
        <h1>Khail Al Madina Supermarket</h1>
        <p>Your One-Stop Shop for Fresh Groceries and More!</p>
        <p>Phone: 0526068899 | Sales and Online Delivery Available</p>
        <a href="https://wa.me/971526068899?text=Hello!%20I'd%20like%20to%20place%20an%20order%20from%20Khail%20Al%20Madina%20Supermarket." 
           class="whatsapp-btn" target="_blank" rel="noopener noreferrer">
            <i class="fab fa-whatsapp"></i> Quick Order via WhatsApp
        </a>
    </header>

    <nav>
        <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#products">Products</a></li>
            <li><a href="#order">Order Now</a></li>
            <li><a href="#delivery">Delivery</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>

    <section id="home">
        <h2>Welcome to Khail Al Madina Supermarket</h2>
        <p>We offer a wide range of fresh produce, household items, and daily essentials. Shop with us for quality products at affordable prices.</p>
    </section>

    <section id="products">
        <h2>Our Products</h2>
        <div class="product-grid">
            <div class="product-item">
                <img src="https://via.placeholder.com/400x300?text=Fresh+Fruits" alt="Fresh Fruits">
                <h3>Fresh Fruits</h3>
                <p>Apples, Bananas, Oranges, etc. (10 AED/unit)</p>
            </div>
            <div class="product-item">
                <img src="https://via.placeholder.com/400x300?text=Vegetables" alt="Vegetables">
                <h3>Vegetables</h3>
                <p>Tomatoes, Onions, Carrots, etc. (8 AED/unit)</p>
            </div>
            <div class="product-item">
                <img src="https://via.placeholder.com/400x300?text=Dairy" alt="Dairy">
                <h3>Dairy Products</h3>
                <p>Milk, Cheese, Yogurt, Eggs (15 AED/unit)</p>
            </div>
            <div class="product-item">
                <img src="https://via.placeholder.com/400x300?text=Snacks" alt="Snacks">
                <h3>Snacks</h3>
                <p>Chips, Biscuits, Chocolates (5 AED/unit)</p>
            </div>
        </div>
    </section>

    <section id="order">
        <h2>Place Your Order</h2>
        <p>Select items, enter quantity, fill your details and send order directly to us on WhatsApp!</p>

        <form id="orderForm">
            <div class="form-group">
                <label for="customerName">Your Name *</label>
                <input type="text" id="customerName" required>
            </div>

            <div class="form-group">
                <label for="customerPhone">Phone Number *</label>
                <input type="tel" id="customerPhone" required placeholder="e.g. 0526068899">
            </div>

            <div class="form-group">
                <label for="deliveryAddress">Delivery Address *</label>
                <textarea id="deliveryAddress" rows="3" required placeholder="Full address in Dubai"></textarea>
            </div>

            <div class="product-selection">
                <h3>Select Products & Quantity</h3>
                
                <div class="product-option">
                    <input type="checkbox" id="fruits" value="Fresh Fruits" data-price="10">
                    <label for="fruits">Fresh Fruits</label>
                    <span class="product-price">(10 AED/unit)</span>
                    <input type="number" class="quantity-input" min="1" value="1" id="qty-fruits" disabled>
                </div>

                <div class="product-option">
                    <input type="checkbox" id="vegetables" value="Vegetables" data-price="8">
                    <label for="vegetables">Vegetables</label>
                    <span class="product-price">(8 AED/unit)</span>
                    <input type="number" class="quantity-input" min="1" value="1" id="qty-vegetables" disabled>
                </div>

                <div class="product-option">
                    <input type="checkbox" id="dairy" value="Dairy Products" data-price="15">
                    <label for="dairy">Dairy Products</label>
                    <span class="product-price">(15 AED/unit)</span>
                    <input type="number" class="quantity-input" min="1" value="1" id="qty-dairy" disabled>
                </div>

                <div class="product-option">
                    <input type="checkbox" id="snacks" value="Snacks" data-price="5">
                    <label for="snacks">Snacks</label>
                    <span class="product-price">(5 AED/unit)</span>
                    <input type="number" class="quantity-input" min="1" value="1" id="qty-snacks" disabled>
                </div>

                <!-- You can add more items here later -->
            </div>

            <div class="form-group">
                <label for="notes">Additional Notes / Special Requests</label>
                <textarea id="notes" rows="3" placeholder="e.g. ripe bananas, no onions, delivery after 6 PM"></textarea>
            </div>

            <div id="order-summary">
                <h3>Order Summary</h3>
                <p id="summaryText">No items selected yet.</p>
                <p id="totalPrice">Total: 0 AED</p>
            </div>

            <div id="error-msg"></div>

            <button type="button" class="whatsapp-btn" onclick="sendOrderToWhatsApp()">
                <i class="fab fa-whatsapp"></i> Send Order via WhatsApp
            </button>
        </form>
    </section>

    <section id="delivery">
        <h2>Online Delivery</h2>
        <p>Enjoy hassle-free shopping. Place your order via the form above or directly on WhatsApp, and get it delivered to your doorstep in Dubai.</p>
        <a href="https://wa.me/971526068899?text=Hello!%20I'd%20like%20to%20place%20an%20order%20from%20Khail%20Al%20Madina%20Supermarket.%20Please%20send%20me%20your%20latest%20catalogue%20or%20prices." 
           class="whatsapp-btn" target="_blank" rel="noopener noreferrer">
            <i class="fab fa-whatsapp"></i> Order via WhatsApp
        </a>
    </section>

    <section id="contact">
        <h2>Contact Us</h2>
        <p>Phone: <a href="tel:0526068899">0526068899</a></p>
        <p>Email: info@khailalmadina.com</p>
        <p>Address: Dubai, UAE</p>
        <a href="https://wa.me/971526068899?text=Hi%20Khail%20Al%20Madina%20Team!%20I%20have%20a%20question%20about%20your%20products%20or%20delivery." 
           class="whatsapp-btn" target="_blank" rel="noopener noreferrer">
            <i class="fab fa-whatsapp"></i> Message us on WhatsApp
        </a>
    </section>

    <footer>
        <p>© 2026 Khail Al Madina Supermarket. All rights reserved.</p>
    </footer>

    <!-- Floating WhatsApp Button -->
    <a href="https://wa.me/971526068899?text=Hello!%20I'd%20like%20to%20order%20from%20Khail%20Al%20Madina%20Supermarket." 
       class="fab-whatsapp" target="_blank" rel="noopener noreferrer" title="Quick Chat">
        <i class="fab fa-whatsapp"></i>
    </a>

    <script>
        // Product prices defined in data-price attributes

        // Enable/disable quantity when checkbox is toggled
        const checkboxes = document.querySelectorAll('.product-option input[type="checkbox"]');
        checkboxes.forEach(checkbox => {
            checkbox.addEventListener('change', function() {
                const qtyInput = document.getElementById('qty-' + this.id);
                qtyInput.disabled = !this.checked;
                if (!this.checked) qtyInput.value = 1;
                updateSummary();
            });
        });

        // Update summary on any change
        document.querySelectorAll('input[type="checkbox"], input[type="number"]').forEach(el => {
            el.addEventListener('change', updateSummary);
            el.addEventListener('input', updateSummary);
        });

        function updateSummary() {
            let summary = "Selected Items:\n";
            let total = 0;
            let hasItems = false;

            checkboxes.forEach(checkbox => {
                if (checkbox.checked) {
                    const qty = parseInt(document.getElementById('qty-' + checkbox.id).value) || 1;
                    const price = parseFloat(checkbox.getAttribute('data-price')) || 0;
                    const subtotal = qty * price;
                    summary += `• ${checkbox.value} × ${qty} = ${subtotal} AED\n`;
                    total += subtotal;
                    hasItems = true;
                }
            });

            if (!hasItems) {
                summary = "No items selected yet.";
                total = 0;
            }

            document.getElementById('summaryText').innerText = summary;
            document.getElementById('totalPrice').innerText = `Total: ${total} AED`;
        }

        function sendOrderToWhatsApp() {
            const name = document.getElementById('customerName').value.trim();
            const phone = document.getElementById('customerPhone').value.trim();
            const address = document.getElementById('deliveryAddress').value.trim();
            const notes = document.getElementById('notes').value.trim();

            if (!name || !phone || !address) {
                document.getElementById('error-msg').innerText = "Please fill in Name, Phone, and Address.";
                return;
            }

            let orderItems = [];
            let total = 0;
            checkboxes.forEach(checkbox => {
                if (checkbox.checked) {
                    const qty = parseInt(document.getElementById('qty-' + checkbox.id).value) || 1;
                    const price = parseFloat(checkbox.getAttribute('data-price')) || 0;
                    const subtotal = qty * price;
                    orderItems.push(`${checkbox.value} × ${qty} = ${subtotal} AED`);
                    total += subtotal;
                }
            });

            if (orderItems.length === 0) {
                document.getElementById('error-msg').innerText = "Please select at least one product.";
                return;
            }

            document.getElementById('error-msg').innerText = "";

            const message = 
                `*New Order from Khail Al Madina Supermarket*%0A%0A` +
                `*Name:* ${encodeURIComponent(name)}%0A` +
                `*Phone:* ${encodeURIComponent(phone)}%0A` +
                `*Delivery Address:* ${encodeURIComponent(address)}%0A%0A` +
                `*Order Items:*%0A${orderItems.map(item => encodeURIComponent(item)).join('%0A')}%0A%0A` +
                `*Total:* ${total} AED%0A%0A` +
                (notes ? `*Notes:* ${encodeURIComponent(notes)}%0A%0A` : '') +
                `Please confirm my order! Thank you.`;

            const whatsappUrl = `https://wa.me/971526068899?text=${message}`;
            window.open(whatsappUrl, '_blank');
        }

        // Initial summary
        updateSummary();
    </script>

</body>
</html>
