<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Lucky Bee POS | Pro</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --brand: #6366f1;
            --bg: #f1f5f9;
            --card: #ffffff;
            --text: #1e293b;
            --muted: #64748b;
            --border: #e2e8f0;
            --success: #10b981;
            --danger: #ef4444;
        }

        [data-theme="dark"] {
            --bg: #0f172a;
            --card: #1e293b;
            --text: #f8fafc;
            --muted: #94a3b8;
            --border: #334155;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
        body { background: var(--bg); color: var(--text); line-height: 1.5; }

        /* --- UI HELPERS --- */
        .hidden { display: none !important; }
        .flex { display: flex; align-items: center; gap: 10px; }
        .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }

        /* --- SIDEBAR --- */
        nav { 
            width: 260px; background: var(--card); border-right: 1px solid var(--border); 
            height: 100vh; position: fixed; padding: 30px 20px; display: flex; flex-direction: column;
        }
        .nav-btn {
            padding: 14px 18px; border-radius: 12px; color: var(--muted); font-weight: 600;
            display: flex; align-items: center; gap: 12px; cursor: pointer; border: none; background: none;
            width: 100%; margin-bottom: 5px; transition: 0.2s; font-size: 15px;
        }
        .nav-btn.active { background: var(--brand); color: white; }

        /* --- MAIN CONTENT --- */
        main { margin-left: 260px; padding: 40px; min-height: 100vh; }
        .header { margin-bottom: 30px; }
        .header h1 { font-size: 28px; font-weight: 800; }

        /* --- CARDS & FORMS --- */
        .card { 
            background: var(--card); border-radius: 20px; padding: 25px; 
            border: 1px solid var(--border); box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
            margin-bottom: 20px;
        }
        
        label { display: block; font-size: 12px; font-weight: 700; color: var(--muted); margin-bottom: 5px; text-transform: uppercase; }
        input { 
            width: 100%; padding: 12px 16px; border-radius: 10px; border: 2px solid var(--border);
            background: var(--bg); color: var(--text); margin-bottom: 15px; outline: none; font-size: 15px;
        }
        input:focus { border-color: var(--brand); }

        .btn {
            padding: 14px 24px; border-radius: 10px; border: none; font-weight: 700;
            cursor: pointer; background: var(--brand); color: white; display: flex; align-items: center; justify-content: center; gap: 8px;
        }

        /* --- INVENTORY LIST --- */
        .inv-item {
            display: grid; grid-template-columns: 80px 1fr 100px 100px auto;
            align-items: center; padding: 15px; border-bottom: 1px solid var(--border);
        }
        .inv-item:last-child { border: none; }
        .badge { padding: 4px 10px; border-radius: 20px; font-size: 12px; font-weight: 700; }
        .badge-low { background: #fee2e2; color: #ef4444; }
        .badge-ok { background: #dcfce7; color: #16a34a; }

        /* --- POS TERMINAL --- */
        .product-card {
            background: var(--card); border: 1px solid var(--border); padding: 20px;
            border-radius: 15px; text-align: center; cursor: pointer; transition: 0.2s;
        }
        .product-card:hover { border-color: var(--brand); transform: translateY(-3px); }

        /* --- SPLASH/LOGIN --- */
        #splash { position: fixed; inset: 0; background: #0f172a; z-index: 1000; display: flex; flex-direction: column; align-items: center; justify-content: center; }
        #loginPage { position: fixed; inset: 0; background: var(--bg); z-index: 900; display: flex; align-items: center; justify-content: center; }
        
        @media (max-width: 900px) {
            nav { width: 80px; padding: 20px 10px; }
            nav span, .nav-btn span { display: none; }
            main { margin-left: 80px; padding: 20px; }
            .grid-2 { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

<div id="splash">
    <h1 style="color:white; font-size: 40px;">🐝</h1>
    <div style="width: 150px; height: 4px; background: rgba(255,255,255,0.1); margin-top: 20px; border-radius: 10px; overflow: hidden;">
        <div style="width: 100%; height: 100%; background: var(--brand); animation: load 2s forwards;"></div>
    </div>
</div>

<div id="loginPage" class="hidden">
    <div class="card" style="width: 350px; text-align: center;">
        <h2 style="margin-bottom: 20px;">Welcome Back</h2>
        <input id="user" placeholder="Username" value="admin">
        <input id="pass" type="password" placeholder="Password" value="1234">
        <button class="btn" style="width: 100%;" onclick="doLogin()">Open Shop</button>
    </div>
</div>

<nav id="sidebar" class="hidden">
    <h2 style="margin-bottom: 30px; font-weight: 800;">BeePOS 🐝</h2>
    <button class="nav-btn active" onclick="showTab('dash', this)">📊 <span>Dashboard</span></button>
    <button class="nav-btn" onclick="showTab('pos', this)">🛒 <span>Terminal</span></button>
    <button class="nav-btn" onclick="showTab('inv', this)">📦 <span>Inventory</span></button>
    <div style="margin-top: auto;">
        <button class="nav-btn" onclick="toggleTheme()">🌓 <span>Theme</span></button>
        <button class="nav-btn" onclick="location.reload()" style="color:var(--danger)">🚪 <span>Logout</span></button>
    </div>
</nav>

<main id="mainApp" class="hidden">
    
    <div id="dash" class="tab-content">
        <div class="header"><h1>Dashboard</h1></div>
        <div class="grid-2">
            <div class="card">
                <label>Daily Revenue</label>
                <h1 id="statRev">K 0.00</h1>
            </div>
            <div class="card">
                <label>Active Inventory</label>
                <h1 id="statInv">0 Items</h1>
            </div>
        </div>
    </div>

    <div id="pos" class="tab-content hidden">
        <div class="header"><h1>Sales Terminal</h1></div>
        <div class="grid-2" style="grid-template-columns: 1.5fr 1fr;">
            <div>
                <input id="search" placeholder="🔍 Search product name or scan barcode..." onkeyup="renderPOS()">
                <div id="posGrid" style="display: grid; grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); gap: 15px;"></div>
            </div>
            <div class="card">
                <h3>Order Summary</h3>
                <div id="cartList" style="margin: 20px 0; min-height: 200px;"></div>
                <div class="flex" style="justify-content: space-between; border-top: 2px solid var(--bg); pt: 15px;">
                    <h3>Total</h3>
                    <h2 id="cartTotal">K 0.00</h2>
                </div>
                <button class="btn" style="width: 100%; margin-top: 20px; background: var(--success);" onclick="checkout()">Checkout</button>
            </div>
        </div>
    </div>

    <div id="inv" class="tab-content hidden">
        <div class="header"><h1>Stock Management</h1></div>
        <div class="grid-2" style="grid-template-columns: 350px 1fr;">
            <div class="card">
                <h3 style="margin-bottom: 20px;">Add New Product</h3>
                <label>Barcode / SKU</label>
                <input id="p_bar" placeholder="Scan or type...">
                
                <label>Product Name</label>
                <input id="p_name" placeholder="e.g. Coca Cola 500ml">
                
                <div class="grid-2">
                    <div>
                        <label>Cost (K)</label>
                        <input id="p_cost" type="number" placeholder="0.00">
                    </div>
                    <div>
                        <label>Price (K)</label>
                        <input id="p_price" type="number" placeholder="0.00">
                    </div>
                </div>
                
                <label>Initial Stock Qty</label>
                <input id="p_qty" type="number" placeholder="10">
                
                <button class="btn" style="width: 100%;" onclick="addInventory()">Save to Stock</button>
            </div>

            <div class="card" style="padding: 0;">
                <div style="padding: 20px; border-bottom: 1px solid var(--border);">
                    <h3>Current Inventory</h3>
                </div>
                <div id="inventoryList" style="max-height: 60vh; overflow-y: auto;">
                    </div>
            </div>
        </div>
    </div>
</main>

<script>
    let inventory = JSON.parse(localStorage.getItem('lucky_inv')) || [];
    let sales = JSON.parse(localStorage.getItem('lucky_sales')) || [];
    let cart = [];

    // Splash Loader
    setTimeout(() => {
        document.getElementById('splash').classList.add('hidden');
        document.getElementById('loginPage').classList.remove('hidden');
    }, 2000);

    function doLogin() {
        document.getElementById('loginPage').classList.add('hidden');
        document.getElementById('sidebar').classList.remove('hidden');
        document.getElementById('mainApp').classList.remove('hidden');
        refresh();
    }

    function addInventory() {
        const name = document.getElementById('p_name').value;
        const barcode = document.getElementById('p_bar').value;
        const cost = parseFloat(document.getElementById('p_cost').value) || 0;
        const price = parseFloat(document.getElementById('p_price').value) || 0;
        const qty = parseInt(document.getElementById('p_qty').value) || 1;

        if(!name) return alert("Please enter a product name");

        inventory.unshift({ barcode, name, cost, price, qty, sold: 0 });
        save();
        refresh();
        
        // Clear inputs
        ['p_name','p_bar','p_cost','p_price','p_qty'].forEach(id => document.getElementById(id).value = '');
    }

    function renderInventory() {
        const container = document.getElementById('inventoryList');
        if(inventory.length === 0) {
            container.innerHTML = `<div style="padding:40px; text-align:center; color:var(--muted)">No items in stock. Add your first product on the left.</div>`;
            return;
        }
        container.innerHTML = inventory.map((item, i) => `
            <div class="inv-item">
                <code style="font-size:11px;">${item.barcode || 'NO-BAR'}</code>
                <div><strong>${item.name}</strong></div>
                <div style="color:var(--success)">K ${item.price}</div>
                <div><span class="badge ${item.qty < 5 ? 'badge-low' : 'badge-ok'}">${item.qty} left</span></div>
                <button onclick="deleteItem(${i})" style="color:var(--danger); border:none; background:none; cursor:pointer; font-weight:700;">Delete</button>
            </div>
        `).join('');
    }

    function renderPOS() {
        const q = document.getElementById('search').value.toLowerCase();
        document.getElementById('posGrid').innerHTML = inventory.filter(p => p.name.toLowerCase().includes(q) || p.barcode.includes(q)).map((p, i) => `
            <div class="product-card" onclick="addToCart(${inventory.indexOf(p)})">
                <strong>${p.name}</strong>
                <div style="color:var(--brand); font-weight:800; margin-top:10px;">K ${p.price}</div>
            </div>
        `).join('');
    }

    function addToCart(i) {
        let p = inventory[i];
        if(p.qty <= 0) return alert("Out of stock!");
        let exist = cart.find(c => c.index === i);
        if(exist) exist.qty++; else cart.push({ index: i, name: p.name, price: p.price, qty: 1 });
        renderCart();
    }

    function renderCart() {
        let total = 0;
        document.getElementById('cartList').innerHTML = cart.map(c => {
            total += c.price * c.qty;
            return `<div class="flex" style="justify-content:space-between; margin-bottom:10px;">
                <span>${c.name} x${c.qty}</span>
                <strong>K ${(c.price * c.qty).toFixed(2)}</strong>
            </div>`;
        }).join('');
        document.getElementById('cartTotal').innerText = 'K ' + total.toFixed(2);
    }

    function checkout() {
        if(cart.length === 0) return;
        cart.forEach(c => {
            inventory[c.index].qty -= c.qty;
            inventory[c.index].sold += c.qty;
        });
        sales.push({ total: parseFloat(document.getElementById('cartTotal').innerText.replace('K ', '')), date: new Date() });
        cart = [];
        save(); refresh(); renderCart();
        alert("Sale Successful!");
    }

    function refresh() {
        renderInventory();
        renderPOS();
        document.getElementById('statInv').innerText = inventory.length + " Items";
        const totalRev = sales.reduce((a, b) => a + b.total, 0);
        document.getElementById('statRev').innerText = 'K ' + totalRev.toFixed(2);
    }

    function showTab(id, btn) {
        document.querySelectorAll('.tab-content').forEach(t => t.classList.add('hidden'));
        document.getElementById(id).classList.remove('hidden');
        document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
    }

    function toggleTheme() {
        const b = document.body;
        b.setAttribute('data-theme', b.getAttribute('data-theme') === 'light' ? 'dark' : 'light');
    }

    function save() { localStorage.setItem('lucky_inv', JSON.stringify(inventory)); localStorage.setItem('lucky_sales', JSON.stringify(sales)); }
    function deleteItem(i) { if(confirm('Delete this item?')) { inventory.splice(i, 1); save(); refresh(); } }

    @keyframes load { from { width: 0%; } to { width: 100%; } }
</script>
</body>
</html>
