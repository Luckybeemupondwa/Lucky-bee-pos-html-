<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Bee POS Pro</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

    <style>
        :root {
            --brand: #6366f1; --brand-hover: #4f46e5;
            --bg: #f8fafc; --sidebar: #ffffff; --card: #ffffff;
            --text-main: #0f172a; --text-muted: #64748b;
            --border: #e2e8f0; --input: #ffffff;
            --shadow: 0 1px 3px 0 rgb(0 0 0 / 0.1);
        }

        [data-theme="dark"] {
            --bg: #0f172a; --sidebar: #1e293b; --card: #1e293b;
            --text-main: #f8fafc; --text-muted: #94a3b8;
            --border: #334155; --input: #0f172a;
            --shadow: 0 4px 6px -1px rgb(0 0 0 / 0.3);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Plus Jakarta Sans', sans-serif; transition: background 0.3s ease, border 0.3s ease; }
        
        body { background: var(--bg); color: var(--text-main); display: flex; min-height: 100vh; }

        /* Navigation */
        nav {
            width: 260px; background: var(--sidebar); border-right: 1px solid var(--border);
            display: flex; flex-direction: column; padding: 30px 20px; position: fixed; height: 100vh; z-index: 100;
        }
        .logo { font-size: 20px; font-weight: 800; color: var(--brand); margin-bottom: 40px; display: flex; align-items: center; gap: 10px; }
        
        .nav-link {
            padding: 12px 15px; border-radius: 10px; color: var(--text-muted);
            font-weight: 600; display: flex; align-items: center; gap: 12px;
            cursor: pointer; margin-bottom: 5px; border: none; background: none; width: 100%; font-size: 14px;
        }
        .nav-link:hover { background: rgba(99, 102, 241, 0.05); color: var(--brand); }
        .nav-link.active { background: var(--brand); color: white; }

        /* Header */
        main { margin-left: 260px; flex: 1; padding: 30px; }
        .header-bar { display: flex; justify-content: space-between; align-items: center; margin-bottom: 30px; }

        /* Theme Toggle */
        .theme-switch {
            background: var(--border); width: 50px; height: 26px; border-radius: 50px; 
            position: relative; cursor: pointer; display: flex; align-items: center; padding: 0 5px;
        }
        .theme-ball {
            width: 18px; height: 18px; background: var(--brand); border-radius: 50%;
            position: absolute; transition: 0.3s; transform: translateX(0);
        }
        [data-theme="dark"] .theme-ball { transform: translateX(22px); background: #fbbf24; }

        /* Dashboard Components */
        .grid-3 { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; margin-bottom: 30px; }
        .stat-card { background: var(--card); padding: 20px; border-radius: 15px; border: 1px solid var(--border); box-shadow: var(--shadow); }
        .stat-card span { font-size: 12px; font-weight: 700; color: var(--text-muted); text-transform: uppercase; }
        .stat-card h2 { font-size: 24px; margin-top: 5px; }

        .card { background: var(--card); border-radius: 15px; border: 1px solid var(--border); padding: 24px; box-shadow: var(--shadow); }

        /* Forms */
        input, select {
            width: 100%; padding: 12px; border-radius: 10px; border: 1px solid var(--border);
            background: var(--input); color: var(--text-main); font-size: 14px; outline: none; margin-bottom: 15px;
        }
        input:focus { border-color: var(--brand); box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.2); }

        .btn { padding: 12px 20px; border-radius: 10px; border: none; font-weight: 700; cursor: pointer; display: inline-flex; align-items: center; gap: 8px; font-size: 14px; }
        .btn-brand { background: var(--brand); color: white; }
        .btn-brand:hover { background: var(--brand-hover); }

        /* Product Grid */
        .product-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); gap: 15px; }
        .product-card {
            background: var(--card); border: 1px solid var(--border); padding: 20px; border-radius: 12px;
            text-align: center; cursor: pointer; transition: 0.2s;
        }
        .product-card:hover { border-color: var(--brand); transform: translateY(-3px); }

        /* Cart */
        .cart-item { display: flex; justify-content: space-between; padding: 10px 0; border-bottom: 1px solid var(--border); font-size: 14px; }

        /* Tables */
        table { width: 100%; border-collapse: collapse; }
        th { text-align: left; padding: 15px; color: var(--text-muted); font-size: 12px; border-bottom: 1px solid var(--border); text-transform: uppercase; }
        td { padding: 15px; border-bottom: 1px solid var(--border); font-size: 14px; }

        .hidden { display: none !important; }

        /* Responsive */
        @media (max-width: 900px) {
            nav { width: 80px; }
            nav span, .logo span { display: none; }
            main { margin-left: 80px; }
        }
    </style>
</head>
<body data-theme="light">

<div id="loginPage" style="position:fixed; inset:0; background:#0f172a; z-index:1000; display:flex; align-items:center; justify-content:center;">
    <div class="card" style="width:360px; text-align:center;">
        <h1 style="color:var(--brand); margin-bottom:10px;">Lucky Bee 🐝</h1>
        <p style="color:var(--text-muted); margin-bottom:25px;">Terminal Authentication</p>
        <input id="username" placeholder="Username" value="admin">
        <input id="password" type="password" placeholder="Password" value="1234">
        <button class="btn btn-brand" style="width:100%" onclick="login()">Enter Terminal</button>
    </div>
</div>

<nav id="sidebar" class="hidden">
    <div class="logo">🐝 <span>Lucky Bee</span></div>
    <button class="nav-link active" onclick="showTab('dashboard', this)">📊 <span>Dashboard</span></button>
    <button class="nav-link" onclick="showTab('posTab', this)">🛒 <span>Terminal</span></button>
    <button class="nav-link" id="invLink" onclick="showTab('invTab', this)">📦 <span>Inventory</span></button>
    <button class="nav-link" onclick="showTab('historyTab', this)">📜 <span>History</span></button>
    
    <div style="margin-top:auto; padding-top:20px;">
        <div style="display:flex; align-items:center; justify-content:space-between; margin-bottom:20px;">
            <span style="font-size:12px; font-weight:700;">THEME</span>
            <div class="theme-switch" onclick="toggleTheme()"><div class="theme-ball"></div></div>
        </div>
        <button class="nav-link" onclick="location.reload()" style="color:var(--danger)">🚪 <span>Logout</span></button>
    </div>
</nav>

<main id="mainContent" class="hidden">
    <div class="header-bar">
        <h1 id="tabTitle">Overview</h1>
        <div id="userBadge" style="font-weight:700; opacity:0.6; font-size:12px;"></div>
    </div>

    <div id="dashboard" class="tab-content">
        <div class="grid-3">
            <div class="stat-card"><span>Revenue</span><h2 id="dashRev">K 0.00</h2></div>
            <div class="stat-card"><span>Items Sold</span><h2 id="dashSales">0</h2></div>
            <div class="stat-card"><span>Stock Levels</span><h2 id="dashStock">0</h2></div>
        </div>
        <div class="card">
            <h3 style="margin-bottom:20px;">Sales Analytics</h3>
            <canvas id="salesChart" height="100"></canvas>
        </div>
    </div>

    <div id="posTab" class="tab-content hidden">
        <div style="display:grid; grid-template-columns: 1.5fr 1fr; gap:25px;">
            <div>
                <input id="posSearch" placeholder="🔍 Search catalog..." onkeyup="renderPOS()">
                <div id="productGrid" class="product-grid"></div>
            </div>
            <div class="card">
                <h3>Order Summary</h3>
                <div id="cartBox" style="min-height:250px; margin:20px 0;"></div>
                <div style="display:flex; justify-content:space-between; font-weight:800; font-size:20px; padding-top:20px; border-top:1px solid var(--border);">
                    <span>Total</span><span style="color:var(--brand)">K <span id="cartTotal">0.00</span></span>
                </div>
                <button class="btn btn-brand" style="width:100%; margin-top:25px; padding:18px;" onclick="checkout()">Complete Sale</button>
            </div>
        </div>
    </div>

    <div id="invTab" class="tab-content hidden">
        <div class="card" style="margin-bottom:25px;">
            <h3 style="margin-bottom:20px;">Restock / Add Items</h3>
            <div style="display:grid; grid-template-columns: 2fr 1fr 1fr 1fr auto; gap:10px;">
                <input id="pname" placeholder="Item Name">
                <input id="pprice" type="number" placeholder="Price">
                <input id="pqty" type="number" placeholder="Qty">
                <select id="pcat"><option>General</option><option>Food</option><option>Drinks</option></select>
                <button class="btn btn-brand" onclick="addItem()">Save Item</button>
            </div>
        </div>
        <div class="card">
            <table id="invTable">
                <thead><tr><th>Product</th><th>Category</th><th>Price</th><th>Stock</th><th>Action</th></tr></thead>
                <tbody id="invBody"></tbody>
            </table>
        </div>
    </div>

    <div id="historyTab" class="tab-content hidden">
        <div class="card">
            <table>
                <thead><tr><th>Transaction</th><th>Date</th><th>Amount</th><th>Status</th></tr></thead>
                <tbody id="historyBody"></tbody>
            </table>
        </div>
    </div>
</main>

<script>
    let inventory = JSON.parse(localStorage.getItem('lb_v8_inv')) || [];
    let sales = JSON.parse(localStorage.getItem('lb_v8_sales')) || [];
    let cart = [];
    let myChart = null;

    function login() {
        const u = document.getElementById('username').value;
        const p = document.getElementById('password').value;
        if ((u === 'admin' && p === '1234') || (u === 'cashier' && p === '1111')) {
            document.getElementById('loginPage').classList.add('hidden');
            document.getElementById('sidebar').classList.remove('hidden');
            document.getElementById('mainContent').classList.remove('hidden');
            document.getElementById('userBadge').innerText = "TERMINAL: " + u.toUpperCase();
            if(u !== 'admin') document.getElementById('invLink').classList.add('hidden');
            refresh();
        } else { alert('Access Denied'); }
    }

    function toggleTheme() {
        const body = document.body;
        const current = body.getAttribute('data-theme');
        body.setAttribute('data-theme', current === 'light' ? 'dark' : 'light');
    }

    function refresh() {
        renderDashboard();
        renderInventory();
        renderPOS();
        renderHistory();
    }

    function addItem() {
        const name = document.getElementById('pname').value;
        const price = parseFloat(document.getElementById('pprice').value);
        const qty = parseInt(document.getElementById('pqty').value);
        const cat = document.getElementById('pcat').value;
        if(!name || isNaN(price)) return;
        inventory.push({ name, price, qty, cat });
        save(); refresh();
        document.getElementById('pname').value = '';
    }

    function renderInventory() {
        document.getElementById('invBody').innerHTML = inventory.map((p, i) => `
            <tr>
                <td><strong>${p.name}</strong></td>
                <td>${p.cat}</td>
                <td>K${p.price.toFixed(2)}</td>
                <td>${p.qty}</td>
                <td><button onclick="deleteItem(${i})" style="color:var(--brand); border:none; background:none; cursor:pointer;">Remove</button></td>
            </tr>
        `).join('');
    }

    function renderPOS() {
        const q = document.getElementById('posSearch').value.toLowerCase();
        document.getElementById('productGrid').innerHTML = inventory.filter(p => p.name.toLowerCase().includes(q)).map((p, i) => `
            <div class="product-card" onclick="addToCart(${inventory.indexOf(p)})">
                <div style="font-weight:700;">${p.name}</div>
                <div style="color:var(--brand); font-size:14px; margin-top:5px;">K${p.price.toFixed(2)}</div>
            </div>
        `).join('');
    }

    function addToCart(i) {
        let p = inventory[i];
        if(p.qty <= 0) return alert('Out of Stock');
        let item = cart.find(c => c.index === i);
        if(item) {
            if(item.qty < p.qty) item.qty++;
            else alert('Limit Reached');
        } else {
            cart.push({ index: i, name: p.name, price: p.price, qty: 1 });
        }
        renderCart();
    }

    function renderCart() {
        let total = 0;
        document.getElementById('cartBox').innerHTML = cart.map(c => {
            total += c.price * c.qty;
            return `<div class="cart-item"><span>${c.name} x${c.qty}</span><strong>K${(c.price * c.qty).toFixed(2)}</strong></div>`;
        }).join('');
        document.getElementById('cartTotal').innerText = total.toFixed(2);
    }

    function checkout() {
        if(!cart.length) return;
        let total = cart.reduce((a, b) => a + (b.price * b.qty), 0);
        cart.forEach(c => inventory[c.index].qty -= c.qty);
        sales.unshift({ id: 'TXN'+Math.floor(Math.random()*9000), date: new Date().toLocaleDateString(), amount: total });
        cart = []; save(); refresh(); renderCart();
        alert('Sale Finalized');
    }

    function renderDashboard() {
        const rev = sales.reduce((a, b) => a + b.amount, 0);
        document.getElementById('dashRev').innerText = 'K ' + rev.toFixed(2);
        document.getElementById('dashSales').innerText = sales.length;
        document.getElementById('dashStock').innerText = inventory.length;
        drawChart();
    }

    function drawChart() {
        const ctx = document.getElementById('salesChart').getContext('2d');
        if(myChart) myChart.destroy();
        myChart = new Chart(ctx, {
            type: 'line',
            data: {
                labels: sales.slice(0,5).map(s => s.id).reverse(),
                datasets: [{ label: 'Revenue', data: sales.slice(0,5).map(s => s.amount).reverse(), borderColor: '#6366f1', tension: 0.4, fill: true, backgroundColor: 'rgba(99, 102, 241, 0.1)' }]
            },
            options: { responsive: true, plugins: { legend: { display: false } }, scales: { y: { display: false }, x: { grid: { display: false } } } }
        });
    }

    function renderHistory() {
        document.getElementById('historyBody').innerHTML = sales.map(s => `
            <tr><td>#${s.id}</td><td>${s.date}</td><td>K${s.amount.toFixed(2)}</td><td><span style="color:var(--success)">● Completed</span></td></tr>
        `).join('');
    }

    function showTab(id, btn) {
        document.querySelectorAll('.tab-content').forEach(t => t.classList.add('hidden'));
        document.getElementById(id).classList.remove('hidden');
        document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
        btn.classList.add('active');
        document.getElementById('tabTitle').innerText = btn.innerText.trim();
        if(id === 'dashboard') drawChart();
    }

    function deleteItem(i) { inventory.splice(i, 1); save(); refresh(); }
    function save() { localStorage.setItem('lb_v8_inv', JSON.stringify(inventory)); localStorage.setItem('lb_v8_sales', JSON.stringify(sales)); }
</script>
</body>
</html>
