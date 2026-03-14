<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Bee POS Pro - BI Edition</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

    <style>
        :root {
            --brand: #6366f1; --bg: #f8fafc; --sidebar: #ffffff; --card: #ffffff;
            --text-main: #0f172a; --text-muted: #64748b; --border: #e2e8f0;
            --success: #10b981; --danger: #ef4444;
        }

        [data-theme="dark"] {
            --bg: #0f172a; --sidebar: #1e293b; --card: #1e293b;
            --text-main: #f8fafc; --text-muted: #94a3b8; --border: #334155;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Plus Jakarta Sans', sans-serif; transition: background 0.2s; }
        body { background: var(--bg); color: var(--text-main); display: flex; min-height: 100vh; }

        /* Sidebar */
        nav { width: 260px; background: var(--sidebar); border-right: 1px solid var(--border); display: flex; flex-direction: column; padding: 30px 20px; position: fixed; height: 100vh; z-index: 100; }
        .nav-link { padding: 12px 15px; border-radius: 12px; color: var(--text-muted); font-weight: 600; display: flex; align-items: center; gap: 12px; cursor: pointer; margin-bottom: 8px; border: none; background: none; width: 100%; font-size: 14px; text-align: left; }
        .nav-link.active { background: var(--brand); color: white; box-shadow: 0 4px 12px rgba(99, 102, 241, 0.3); }

        /* Layout */
        main { margin-left: 260px; flex: 1; padding: 30px; width: calc(100% - 260px); }
        .card { background: var(--card); border-radius: 16px; border: 1px solid var(--border); padding: 24px; box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1); margin-bottom: 25px; }
        
        /* Stats */
        .grid-stats { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; margin-bottom: 25px; }
        .stat-box { padding: 20px; border-radius: 12px; border: 1px solid var(--border); background: var(--card); }
        .stat-box small { font-size: 11px; font-weight: 700; color: var(--text-muted); text-transform: uppercase; }
        .stat-box h2 { font-size: 24px; margin-top: 5px; }

        /* POS UI */
        .product-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); gap: 15px; }
        .product-card { background: var(--card); border: 1px solid var(--border); padding: 15px; border-radius: 12px; text-align: center; cursor: pointer; }
        .product-card:hover { border-color: var(--brand); transform: translateY(-2px); }

        /* Tables */
        table { width: 100%; border-collapse: collapse; margin-top: 10px; }
        th { text-align: left; padding: 12px; font-size: 12px; color: var(--text-muted); border-bottom: 2px solid var(--border); }
        td { padding: 12px; border-bottom: 1px solid var(--border); font-size: 14px; }

        input { width: 100%; padding: 12px; border-radius: 10px; border: 1px solid var(--border); background: var(--bg); color: var(--text-main); margin-bottom: 10px; outline: none; }
        .btn { padding: 12px 20px; border-radius: 10px; border: none; font-weight: 700; cursor: pointer; display: flex; align-items: center; gap: 8px; font-size: 14px; }
        .btn-brand { background: var(--brand); color: white; }

        #receipt-print { display: none; width: 80mm; padding: 10px; color: black; background: white; font-family: monospace; }
        @media print { body * { display: none; } #receipt-print { display: block; margin: 0 auto; } }
        .hidden { display: none !important; }
    </style>
</head>
<body data-theme="light">

<div id="loginPage" style="position:fixed; inset:0; background:#0f172a; z-index:2000; display:flex; align-items:center; justify-content:center;">
    <div class="card" style="width:360px; text-align:center;">
        <h1 style="color:var(--brand); margin-bottom:20px;">Lucky Bee 🐝</h1>
        <input id="username" placeholder="Username" value="admin">
        <input id="password" type="password" placeholder="Password" value="1234">
        <button class="btn btn-brand" style="width:100%" onclick="login()">Enter System</button>
    </div>
</div>

<nav id="sidebar" class="hidden">
    <div style="font-size:20px; font-weight:800; color:var(--brand); margin-bottom:30px;">🐝 Lucky Bee</div>
    <button class="nav-link active" onclick="showTab('dashboard', this)">📊 <span>Dashboard</span></button>
    <button class="nav-link" onclick="showTab('posTab', this)">🛒 <span>Terminal</span></button>
    <button class="nav-link" onclick="showTab('invTab', this)">📦 <span>Inventory</span></button>
    <button class="nav-link" onclick="showTab('reportTab', this)">📈 <span>Reports</span></button>
    
    <div style="margin-top:auto;">
        <button class="nav-link" onclick="toggleTheme()">🌓 <span>Theme Toggle</span></button>
        <button class="nav-link" onclick="location.reload()" style="color:var(--danger)">🚪 <span>Logout</span></button>
    </div>
</nav>

<main id="mainContent" class="hidden">
    <h1 id="tabTitle" style="margin-bottom:25px;">Dashboard</h1>

    <div id="dashboard" class="tab-content">
        <div class="grid-stats">
            <div class="stat-box"><small>Revenue</small><h2 id="statRev">K 0.00</h2></div>
            <div class="stat-box"><small>Items Sold</small><h2 id="statSold">0</h2></div>
            <div class="stat-box"><small>Low Stock</small><h2 id="statLow" style="color:var(--danger)">0</h2></div>
        </div>
        <div class="card"><h3>Sales Performance</h3><canvas id="salesChart" height="100"></canvas></div>
    </div>

    <div id="posTab" class="tab-content hidden">
        <div style="display:grid; grid-template-columns: 1.5fr 1fr; gap:25px;">
            <div>
                <input id="posSearch" placeholder="Scan Barcode or Type Product Name..." onkeyup="renderPOS()">
                <div id="productGrid" class="product-grid"></div>
            </div>
            <div class="card">
                <h3>Cart</h3>
                <div id="cartBox" style="min-height:300px; margin:15px 0; border-bottom:1px solid var(--border);"></div>
                <div style="display:flex; justify-content:space-between; font-weight:800; font-size:22px;">
                    <span>Total</span><span>K <span id="cartTotal">0.00</span></span>
                </div>
                <button class="btn btn-brand" style="width:100%; margin-top:20px;" onclick="checkout()">Complete & Print</button>
            </div>
        </div>
    </div>

    <div id="invTab" class="tab-content hidden">
        <div class="card">
            <h3>Update Inventory</h3>
            <div style="display:grid; grid-template-columns: 1fr 2fr 1fr 1fr auto; gap:10px; margin-top:15px;">
                <input id="pbarcode" placeholder="Barcode">
                <input id="pname" placeholder="Name">
                <input id="pprice" type="number" placeholder="Price">
                <input id="pqty" type="number" placeholder="Add Qty">
                <button class="btn btn-brand" onclick="addItem()">Add Stock</button>
            </div>
            <table>
                <thead><tr><th>Barcode</th><th>Name</th><th>Price</th><th>Stock</th><th>Action</th></tr></thead>
                <tbody id="invBody"></tbody>
            </table>
        </div>
    </div>

    <div id="reportTab" class="tab-content hidden">
        <div style="display:grid; grid-template-columns: 1fr 1fr; gap:25px;">
            <div class="card">
                <h3>Top Sellers</h3>
                <table id="topSellersTable"><thead><tr><th>Product</th><th>Qty Sold</th></tr></thead><tbody></tbody></table>
            </div>
            <div class="card">
                <h3>Stock Movement</h3>
                <p style="font-size:12px; color:var(--text-muted); margin-bottom:15px;">Items recently sold out of stock</p>
                <div id="stockOutLog"></div>
            </div>
        </div>
    </div>
</main>

<div id="receipt-print">
    <center><h3>LUCKY BEE 🐝</h3><p>Official Receipt</p></center>
    <div id="receiptItems"></div>
    <hr>
    <h3 id="receiptTotal"></h3>
    <center><p id="receiptDate"></p></center>
</div>

<script>
    let inventory = JSON.parse(localStorage.getItem('lb_v11_inv')) || [];
    let sales = JSON.parse(localStorage.getItem('lb_v11_sales')) || [];
    let movement = JSON.parse(localStorage.getItem('lb_v11_move')) || [];
    let cart = [];
    let scannerBuffer = "";

    function login() {
        document.getElementById('loginPage').classList.add('hidden');
        document.getElementById('sidebar').classList.remove('hidden');
        document.getElementById('mainContent').classList.remove('hidden');
        refresh();
    }

    // Barcode Scanner Listener
    document.addEventListener('keypress', e => {
        if (e.target.tagName === 'INPUT') return;
        if (e.key === 'Enter') {
            const idx = inventory.findIndex(p => p.barcode === scannerBuffer);
            if(idx !== -1) addToCart(idx);
            scannerBuffer = "";
        } else { scannerBuffer += e.key; }
    });

    function addItem() {
        const barcode = document.getElementById('pbarcode').value;
        const name = document.getElementById('pname').value;
        const price = parseFloat(document.getElementById('pprice').value) || 0;
        const qty = parseInt(document.getElementById('pqty').value) || 0;
        if(!name) return;
        inventory.push({ barcode, name, price, qty, sold: 0 });
        save(); refresh();
        ['pbarcode','pname','pprice','pqty'].forEach(id => document.getElementById(id).value = '');
    }

    function addToCart(i) {
        let p = inventory[i];
        if(p.qty <= 0) return alert('Out of Stock');
        let item = cart.find(c => c.index === i);
        if(item) item.qty++; else cart.push({ index: i, name: p.name, price: p.price, qty: 1 });
        renderCart();
    }

    function renderCart() {
        let total = 0;
        document.getElementById('cartBox').innerHTML = cart.map(c => {
            total += c.price * c.qty;
            return `<div style="display:flex; justify-content:space-between; margin-bottom:8px; font-size:14px;">
                <span>${c.name} x${c.qty}</span><strong>K${(c.price*c.qty).toFixed(2)}</strong>
            </div>`;
        }).join('');
        document.getElementById('cartTotal').innerText = total.toFixed(2);
    }

    function checkout() {
        if(!cart.length) return;
        const total = document.getElementById('cartTotal').innerText;
        
        // Print
        document.getElementById('receiptItems').innerHTML = cart.map(c => `<div>${c.name} x${c.qty} - K${(c.price*c.qty).toFixed(2)}</div>`).join('');
        document.getElementById('receiptTotal').innerText = "TOTAL: K" + total;
        document.getElementById('receiptDate').innerText = new Date().toLocaleString();
        
        // Update Stock & Movement
        cart.forEach(c => {
            inventory[c.index].qty -= c.qty;
            inventory[c.index].sold = (inventory[c.index].sold || 0) + c.qty;
            movement.unshift({ name: c.name, qty: c.qty, time: new Date().toLocaleTimeString() });
        });

        sales.unshift({ id: 'TXN'+Math.floor(Math.random()*9000), amount: parseFloat(total), date: new Date().toLocaleDateString() });
        cart = []; save(); refresh(); renderCart();
        window.print();
    }

    function renderReports() {
        const top = [...inventory].sort((a,b) => (b.sold||0) - (a.sold||0)).slice(0, 5);
        document.getElementById('topSellersTable').querySelector('tbody').innerHTML = top.map(p => 
            `<tr><td>${p.name}</td><td>${p.sold || 0}</td></tr>`
        ).join('');

        document.getElementById('stockOutLog').innerHTML = movement.slice(0, 10).map(m => 
            `<div style="font-size:13px; padding:8px 0; border-bottom:1px solid var(--border);">
                <b>${m.name}</b> moved out (${m.qty} units) at ${m.time}
            </div>`
        ).join('');
    }

    function renderInventory() {
        document.getElementById('invBody').innerHTML = inventory.map((p, i) => `
            <tr><td><code>${p.barcode}</code></td><td>${p.name}</td><td>K${p.price}</td><td>${p.qty}</td>
            <td><button onclick="deleteItem(${i})" style="color:var(--danger); border:none; background:none; cursor:pointer;">Del</button></td></tr>
        `).join('');
    }

    function renderPOS() {
        const q = document.getElementById('posSearch').value.toLowerCase();
        document.getElementById('productGrid').innerHTML = inventory.filter(p => p.name.toLowerCase().includes(q) || p.barcode.includes(q)).map((p, i) => `
            <div class="product-card" onclick="addToCart(${inventory.indexOf(p)})">
                <strong>${p.name}</strong><br><small>K${p.price}</small>
            </div>
        `).join('');
    }

    function refresh() {
        renderInventory(); renderPOS(); renderReports();
        const rev = sales.reduce((a,b) => a+b.amount, 0);
        document.getElementById('statRev').innerText = 'K ' + rev.toFixed(2);
        document.getElementById('statSold').innerText = inventory.reduce((a,b) => a+(b.sold||0), 0);
        document.getElementById('statLow').innerText = inventory.filter(p => p.qty < 5).length;
    }

    function toggleTheme() {
        const b = document.body;
        b.setAttribute('data-theme', b.getAttribute('data-theme') === 'light' ? 'dark' : 'light');
    }

    function showTab(id, btn) {
        document.querySelectorAll('.tab-content').forEach(t => t.classList.add('hidden'));
        document.getElementById(id).classList.remove('hidden');
        document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
        btn.classList.add('active');
        document.getElementById('tabTitle').innerText = btn.innerText.trim();
    }

    function deleteItem(i) { inventory.splice(i,1); save(); refresh(); }
    function save() { 
        localStorage.setItem('lb_v11_inv', JSON.stringify(inventory)); 
        localStorage.setItem('lb_v11_sales', JSON.stringify(sales));
        localStorage.setItem('lb_v11_move', JSON.stringify(movement));
    }
</script>
</body>
</html>
