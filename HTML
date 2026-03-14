<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Lucky Bee POS | Enterprise</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700;800&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --brand: #6366f1; --bg: #f8fafc; --sidebar: #ffffff; --card: #ffffff;
            --text: #0f172a; --muted: #64748b; --border: #cbd5e1; --success: #10b981;
        }

        [data-theme="dark"] {
            --bg: #020617; --sidebar: #0f172a; --card: #1e293b;
            --text: #f8fafc; --muted: #94a3b8; --border: #334155;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Plus Jakarta Sans', sans-serif; }
        body { background: var(--bg); color: var(--text); overflow-x: hidden; }

        /* --- STABLE LOGIN BOX --- */
        #loginPage {
            position: fixed; inset: 0; background: var(--bg); z-index: 10000;
            display: flex; align-items: center; justify-content: center;
        }
        .login-card {
            background: var(--card); padding: 40px; border-radius: 24px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.15);
            width: 380px; text-align: center; border: 1px solid var(--border);
        }

        /* --- LAYOUT --- */
        nav { 
            width: 280px; background: var(--sidebar); border-right: 1px solid var(--border); 
            height: 100vh; position: fixed; padding: 40px 24px; z-index: 500;
        }
        main { margin-left: 280px; padding: 40px; min-height: 100vh; }

        .nav-link {
            padding: 14px 18px; border-radius: 12px; color: var(--muted); font-weight: 700;
            display: flex; align-items: center; gap: 12px; cursor: pointer; border: none; background: none;
            width: 100%; margin-bottom: 8px; font-size: 15px; transition: 0.2s;
        }
        .nav-link.active { background: var(--brand); color: white; box-shadow: 0 10px 15px -3px rgba(99, 102, 241, 0.3); }

        /* --- COMPONENTS --- */
        .card { background: var(--card); border-radius: 20px; padding: 25px; border: 1px solid var(--border); margin-bottom: 25px; }
        
        label { display: block; font-size: 11px; font-weight: 800; color: var(--muted); text-transform: uppercase; margin-bottom: 6px; }
        input { 
            width: 100%; padding: 14px; border-radius: 10px; border: 2px solid var(--border); 
            background: var(--bg); color: var(--text); margin-bottom: 15px; outline: none; font-size: 15px;
        }
        input:focus { border-color: var(--brand); }

        .btn { 
            background: var(--brand); color: white; padding: 14px 24px; border: none; 
            border-radius: 10px; font-weight: 800; cursor: pointer; transition: 0.2s;
        }
        .btn:active { transform: scale(0.98); }

        /* --- INVENTORY VIEW --- */
        .inv-table { width: 100%; border-collapse: collapse; }
        .inv-header { background: var(--bg); font-weight: 800; font-size: 12px; color: var(--muted); text-transform: uppercase; }
        .inv-header td { padding: 15px; }
        .inv-row td { padding: 15px; border-bottom: 1px solid var(--border); }

        .hidden { display: none !important; }
        @media (max-width: 1024px) { nav { width: 80px; } nav span { display: none; } main { margin-left: 80px; width: calc(100% - 80px); } }
    </style>
</head>
<body data-theme="light">

<div id="loginPage">
    <div class="login-card">
        <div style="font-size: 50px; margin-bottom: 15px;">🐝</div>
        <h1 style="margin-bottom: 8px; font-weight: 800;">Lucky Bee POS</h1>
        <p style="color: var(--muted); margin-bottom: 30px;">Login to your dashboard</p>
        
        <label>Username</label>
        <input id="u_name" type="text" value="admin">
        <label>Password</label>
        <input id="u_pass" type="password" value="1234">
        
        <button class="btn" style="width: 100%; margin-top: 10px;" onclick="unlockApp()">Unlock Terminal</button>
    </div>
</div>

<nav id="sidebar" class="hidden">
    <div style="font-size: 22px; font-weight: 800; margin-bottom: 40px; color: var(--brand)">🐝 BeePOS</div>
    <button class="nav-link active" onclick="switchTab('dash', this)">📊 <span>Dashboard</span></button>
    <button class="nav-link" onclick="switchTab('pos', this)">🛒 <span>Terminal</span></button>
    <button class="nav-link" onclick="switchTab('inv', this)">📦 <span>Inventory</span></button>
    
    <div style="position: absolute; bottom: 30px; width: calc(100% - 48px);">
        <button class="nav-link" onclick="toggleTheme()">🌓 <span>Theme</span></button>
        <button class="nav-link" onclick="location.reload()" style="color: var(--danger)">🚪 <span>Logout</span></button>
    </div>
</nav>

<main id="mainApp" class="hidden">
    
    <div id="dash" class="tab-view">
        <h1 style="margin-bottom: 25px;">Business Insights</h1>
        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 20px;">
            <div class="card">
                <label>Gross Sales</label>
                <h1 id="statSales" style="font-size: 32px; color: var(--brand)">K 0.00</h1>
            </div>
            <div class="card">
                <label>Inventory Count</label>
                <h1 id="statCount" style="font-size: 32px;">0 Items</h1>
            </div>
        </div>
    </div>

    <div id="pos" class="tab-view hidden">
        <h1 style="margin-bottom: 25px;">Sales Terminal</h1>
        <div style="display: grid; grid-template-columns: 1.6fr 1fr; gap: 30px;">
            <div>
                <input id="posSearch" placeholder="🔍 Search product or scan..." onkeyup="renderPOS()">
                <div id="posGrid" style="display: grid; grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); gap: 15px;"></div>
            </div>
            <div class="card">
                <h3 style="margin-bottom: 20px;">Current Cart</h3>
                <div id="cartItems" style="min-height: 250px; margin-bottom: 20px;"></div>
                <div style="display:flex; justify-content:space-between; border-top: 2px solid var(--bg); padding-top: 20px;">
                    <span style="font-weight: 800; font-size: 20px;">Total</span>
                    <span id="cartTotal" style="font-weight: 800; font-size: 24px; color: var(--brand);">K 0.00</span>
                </div>
                <button class="btn" style="width: 100%; margin-top: 20px; background: var(--success);" onclick="processSale()">Complete Sale</button>
            </div>
        </div>
    </div>

    <div id="inv" class="tab-view hidden">
        <h1 style="margin-bottom: 25px;">Stock Management</h1>
        <div style="display: grid; grid-template-columns: 320px 1fr; gap: 30px;">
            <div class="card">
                <h3 style="margin-bottom: 20px;">Add Item</h3>
                <label>Barcode</label><input id="i_bar" placeholder="Scan here...">
                <label>Product Name</label><input id="i_name" placeholder="Name of item">
                <label>Sale Price (K)</label><input id="i_price" type="number" placeholder="0.00">
                <label>Current Stock</label><input id="i_qty" type="number" value="10">
                <button class="btn" style="width: 100%;" onclick="saveToStock()">Add to Inventory</button>
            </div>
            <div class="card" style="padding: 0; overflow: hidden;">
                <table class="inv-table">
                    <tr class="inv-header">
                        <td>Product Details</td><td>Price</td><td>Stock</td><td>Action</td>
                    </tr>
                    <tbody id="invBody"></tbody>
                </table>
            </div>
        </div>
    </div>
</main>

<script>
    // --- DATA STATE ---
    let stock = JSON.parse(localStorage.getItem('bee_v17_stock')) || [];
    let sales = JSON.parse(localStorage.getItem('bee_v17_sales')) || [];
    let cart = [];

    // --- CORE APP FLOW ---
    function unlockApp() {
        // Double check inputs (optional for admin/1234)
        document.getElementById('loginPage').style.display = 'none';
        document.getElementById('sidebar').classList.remove('hidden');
        document.getElementById('mainApp').classList.remove('hidden');
        syncAll();
    }

    function saveToStock() {
        const name = document.getElementById('i_name').value;
        const price = parseFloat(document.getElementById('i_price').value) || 0;
        const qty = parseInt(document.getElementById('i_qty').value) || 0;
        const bar = document.getElementById('i_bar').value;

        if(!name || price <= 0) return alert("Please enter Name and Price");

        stock.unshift({ barcode: bar, name: name, price: price, qty: qty });
        localStorage.setItem('bee_v17_stock', JSON.stringify(stock));
        
        // Clear inputs
        ['i_name','i_price','i_qty','i_bar'].forEach(id => document.getElementById(id).value = '');
        syncAll();
    }

    function syncAll() {
        // 1. Render Inventory Table
        const tbody = document.getElementById('invBody');
        tbody.innerHTML = stock.map((item, idx) => `
            <tr class="inv-row">
                <td><b>${item.name}</b><br><small style="color:var(--muted)">${item.barcode || 'No SKU'}</small></td>
                <td>K ${item.price.toFixed(2)}</td>
                <td><span style="font-weight:700">${item.qty}</span></td>
                <td><button onclick="removeStock(${idx})" style="color:red; background:none; border:none; cursor:pointer; font-weight:800">Delete</button></td>
            </tr>
        `).join('');

        // 2. Render POS Grid
        renderPOS();

        // 3. Update Dashboard Stats
        const totalRev = sales.reduce((a, b) => a + b, 0);
        document.getElementById('statSales').innerText = 'K ' + totalRev.toFixed(2);
        document.getElementById('statCount').innerText = stock.length + ' Items';
    }

    function renderPOS() {
        const query = document.getElementById('posSearch').value.toLowerCase();
        const grid = document.getElementById('posGrid');
        grid.innerHTML = stock.filter(p => p.name.toLowerCase().includes(query)).map((p) => {
            const index = stock.indexOf(p);
            return `
                <div class="card" onclick="addToCart(${index})" style="padding:15px; text-align:center; cursor:pointer; margin-bottom:0;">
                    <div style="font-size:11px; color:var(--muted); font-weight:700;">QTY: ${p.qty}</div>
                    <strong style="display:block; margin-top:5px;">${p.name}</strong>
                    <div style="color:var(--brand); font-weight:800; margin-top:8px;">K ${p.price.toFixed(2)}</div>
                </div>
            `;
        }).join('');
    }

    function addToCart(idx) {
        const item = stock[idx];
        if(item.qty <= 0) return alert("Out of Stock!");
        
        const existing = cart.find(c => c.stockIndex === idx);
        if(existing) existing.count++; 
        else cart.push({ stockIndex: idx, name: item.name, price: item.price, count: 1 });
        
        updateCartUI();
    }

    function updateCartUI() {
        let total = 0;
        const area = document.getElementById('cartItems');
        area.innerHTML = cart.map(c => {
            total += (c.price * c.count);
            return `<div style="display:flex; justify-content:space-between; margin-bottom:12px;">
                <span>${c.name} x${c.count}</span>
                <strong>K ${(c.price * c.count).toFixed(2)}</strong>
            </div>`;
        }).join('');
        document.getElementById('cartTotal').innerText = 'K ' + total.toFixed(2);
    }

    function processSale() {
        if(cart.length === 0) return;
        
        cart.forEach(item => {
            stock[item.stockIndex].qty -= item.count;
        });

        const finalTotal = parseFloat(document.getElementById('cartTotal').innerText.replace('K ', ''));
        sales.push(finalTotal);
        
        localStorage.setItem('bee_v17_stock', JSON.stringify(stock));
        localStorage.setItem('bee_v17_sales', JSON.stringify(sales));
        
        cart = [];
        updateCartUI();
        syncAll();
        alert("Transaction Recorded Successfully!");
    }

    function switchTab(id, btn) {
        document.querySelectorAll('.tab-view').forEach(t => t.classList.add('hidden'));
        document.getElementById(id).classList.remove('hidden');
        document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
        btn.classList.add('active');
    }

    function removeStock(idx) {
        if(confirm("Permanently delete this item?")) {
            stock.splice(idx, 1);
            localStorage.setItem('bee_v17_stock', JSON.stringify(stock));
            syncAll();
        }
    }

    function toggleTheme() {
        const b = document.body;
        b.setAttribute('data-theme', b.getAttribute('data-theme') === 'light' ? 'dark' : 'light');
    }
</script>
</body>
</html>
