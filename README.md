<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Family House Cleaning - Book Now</title>
    <style>
        /* Reset & basic styles */
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Arial', sans-serif; }
        body { background: #f7f9fc; color: #1c3c66; line-height: 1.6; }
        a { text-decoration: none; color: inherit; }

        /* Container */
        .container { max-width: 900px; margin: 40px auto; padding: 20px; background: #fff; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); }

        /* Header */
        header { text-align: center; margin-bottom: 30px; }
        header img { max-width: 150px; margin-bottom: 10px; }
        header h1 { font-size: 28px; margin-bottom: 5px; }
        header p { font-size: 16px; color: #4d5c6e; }

        /* Booking Form */
        .booking-form { display: flex; flex-direction: column; gap: 15px; padding: 10px; }
        .booking-form label { font-weight: bold; margin-bottom: 5px; display: block; }
        .booking-form input[type="text"],
        .booking-form input[type="email"],
        .booking-form input[type="number"],
        .booking-form select { width: 100%; padding: 10px; border: 1px solid #ccd1d9; border-radius: 6px; font-size: 16px; }
        .booking-form .frequency-options { display: flex; gap: 10px; margin-top: 5px; }
        .booking-form .frequency-options label { font-weight: normal; }

        /* Estimated Price */
        .estimated-price { font-size: 20px; font-weight: bold; text-align: center; margin-top: 10px; color: #0a8f3b; }

        /* Payment Options */
        .payment-methods { display: flex; gap: 20px; align-items: center; margin-top: 10px; }
        .payment-methods label { display: flex; align-items: center; gap: 5px; font-weight: normal; }

        /* Submit Button */
        .booking-form button { margin-top: 15px; padding: 12px; background: #0a8f3b; color: #fff; font-size: 18px; font-weight: bold; border: none; border-radius: 6px; cursor: pointer; transition: 0.3s; }
        .booking-form button:hover { background: #07712e; }

        /* Services section */
        .services { display: flex; justify-content: space-between; flex-wrap: wrap; margin-top: 30px; gap: 15px; }
        .service-item { flex: 1 1 200px; background: #eaf4ff; padding: 15px; border-radius: 8px; text-align: center; font-weight: bold; color: #1c3c66; }

        /* Responsive */
        @media(max-width: 600px){
            .services { flex-direction: column; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <header>
            <img src="data:image/png;base64,REPLACE_WITH_YOUR_BASE64_LOGO" alt="Family House Cleaning Logo">
            <h1>Family House Cleaning</h1>
            <p>We clean, so you can focus on what matters</p>
            <p>📞 (914) 635-5975</p>
        </header>

        <!-- Booking Form -->
        <form class="booking-form" oninput="calculatePrice()">
            <label for="name">Full Name</label>
            <input type="text" id="name" name="name" required>

            <label for="phone">Phone Number</label>
            <input type="text" id="phone" name="phone" required>

            <label for="email">Email Address</label>
            <input type="email" id="email" name="email" required>

            <label>Frequency</label>
            <div class="frequency-options">
                <label><input type="radio" name="frequency" value="one-time" checked> One-Time</label>
                <label><input type="radio" name="frequency" value="weekly"> Weekly (10% off)</label>
                <label><input type="radio" name="frequency" value="bi-weekly"> Bi-Weekly (5% off)</label>
                <label><input type="radio" name="frequency" value="monthly"> Monthly</label>
            </div>

            <label for="rooms">Rooms</label>
            <input type="number" id="rooms" name="rooms" min="0" value="1">

            <label for="bathrooms">Bathrooms</label>
            <input type="number" id="bathrooms" name="bathrooms" min="0" value="1">

            <div class="estimated-price" id="estimatedPrice">$0.00</div>

            <label>Payment Method</label>
            <div class="payment-methods">
                <label><input type="radio" name="payment" value="cash" checked> Cash</label>
                <label><input type="radio" name="payment" value="zelle"> Zelle</label>
            </div>

            <button type="submit">Submit Booking</button>
        </form>

        <!-- Services -->
        <div class="services">
            <div class="service-item">Standard Cleaning</div>
            <div class="service-item">Deep Cleaning</div>
            <div class="service-item">Move In/Out Cleaning</div>
            <div class="service-item">Eco-Friendly Products</div>
        </div>
    </div>

    <script>
        const roomPrice = 40;
        const bathroomPrice = 25;

        function calculatePrice() {
            const rooms = parseInt(document.getElementById('rooms').value) || 0;
            const bathrooms = parseInt(document.getElementById('bathrooms').value) || 0;
            const frequency = document.querySelector('input[name="frequency"]:checked').value;

            let price = (rooms * roomPrice) + (bathrooms * bathroomPrice);

            // Apply discounts
            if(frequency === 'weekly') price *= 0.9;
            if(frequency === 'bi-weekly') price *= 0.95;

            document.getElementById('estimatedPrice').textContent = `$${price.toFixed(2)}`;
        }

        // Initialize price
        calculatePrice();
    </script>
</body>
</html>
