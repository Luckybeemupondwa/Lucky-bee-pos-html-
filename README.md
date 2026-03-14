<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Bee POS Pro - Enterprise</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

    <style>
        :root {
            --brand: #6366f1; --bg: #f8fafc; --sidebar: #ffffff; --card: #ffffff;
            --text-main: #0f172a; --text-muted: #64748b; --border: #e2e8f0;
            --success: #10b981; --danger: #ef4444; --warning: #f59e0b;
        }

        [data-theme="dark"] {
            --bg: #0f172a; --sidebar: #1e293b; --card: #1e293b;
            --text-main: #f8fafc; --text-muted: #94a3b8; --border: #334155;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Plus Jakarta Sans', sans-serif; }
        body { background: var(--bg); color: var(--text-main); display: flex; min-height: 100vh; transition: 0.3s; }

        /* Sidebar */
        nav { width: 260px; background: var(--sidebar); border-right: 1px solid var(--border); display: flex; flex-direction: column; padding: 30px 20px; position: fixed; height: 100vh; z-index: 100; }
        .nav-link { padding: 12px 15px; border-radius: 12px; color: var(--text-muted); font-weight: 600; display: flex; align-items: center; gap: 12px; cursor: pointer; margin-bottom: 5px; border: none; background: none; width: 100%; font-size: 14px; text-align: left; }
        .nav-link.active { background: var(--brand); color: white; box-shadow: 0 4px 12px rgba(99, 102, 241, 0.3); }

        /* Content Area */
        main { margin-left: 260px; flex: 1; padding: 30px; width: calc(100% - 260px); }
        .card { background: var(--card); border-radius: 16px; border: 1px solid var(--border); padding: 24px; box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.05); margin-bottom: 25px; }
        
        /* Stats Grid */
        .grid-4 { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 15px; margin-bottom: 25px; }
        .stat-box { padding: 20px; border-radius: 12px; border: 1px solid var(--border); background: var(--card); }
        .stat-box small { font-size: 11px; font-weight: 700; color: var(--text-muted); text-transform: uppercase; }
        .stat-box h2 { font-size: 22px; margin-top: 5px; }

        /* Form Elements */
        input, select { width: 100%; padding: 12px; border-radius: 10px; border: 1px solid var(--border); background: var(--bg); color: var(--text-main); margin-bottom: 10px; outline: none; }
        .btn { padding: 12px 20px; border-radius: 10px; border: none; font-weight: 700; cursor: pointer; display: flex; align-items: center; gap: 8px; font-size: 14px; justify-content: center; }
        .btn-brand { background: var(--brand); color: white; }
        .btn-outline { background: transparent; border: 1px solid var(--border); color: var(--text-main); }

        /* POS Grid */
        .product-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(130px, 1fr)); gap: 12px; }
        .product-card { background: var(--card); border: 1px solid var(--border); padding: 15px; border-radius: 12px; text-align: center; cursor: pointer; position: relative; }
        .product-card .stock-label { position: absolute; top: 5px; right: 5px; font-size: 9px; padding: 2px 5px; border-radius: 4px; background: var(--bg); border: 1px solid var(--border); }

        /* Tables */
        table { width: 100%; border-collapse: collapse; }
        th { text-align: left; padding: 12px; font-size: 11px; color: var(--text-muted); text-transform: uppercase; border-bottom: 2px solid var(--border); }
        td { padding: 12px; border-bottom: 1px solid var(--border); font-size: 13px; }

        .badge { padding: 4px 8px; border-radius: 6px; font-size: 10px; font-weight: 800; }
        .badge-success { background: #dcfce7; color: #16a34a; }
        .badge-danger { background: #fee2e2; color: #ef4444; }

        .hidden { display: none !important; }
        @media (max-width: 1024px) { nav { width: 80px; } nav span { display: none; } main { margin-left: 80px; width: calc(100% - 80px); } }
    </style>
</head>
<body data-theme="light">

<div id="loginPage" style="position:fixed; inset:0; background:#0f172a; z-index:2000; display:flex; align-items:center; justify-content:center;">
    <div class="card" style="width:360px; text-align:center;">
        <h1 style="color:var(--brand); margin-bottom:20px;">Lucky Bee 🐝</h1>
        <input id="username" placeholder="Username" value="admin">
        <input id="password" type="password" placeholder="Password" value="1234">
        <button class="btn btn-brand" style="width:100%" onclick="login()">Enter Terminal</button>
    </div>
</div>

<nav id="sidebar" class="hidden">
    <div style="font-size:20px; font-weight:800; color:var(--brand); margin-bottom:30px;">🐝 Lucky Bee</div>
    <button class="nav-link active" onclick="showTab('dashboard', this)">📊 <span>Insights</span></button>
    <button class="nav-link" onclick="showTab('posTab', this)">🛒 <span>Terminal</span></button>
    <button class="nav-link" onclick="showTab('invTab', this)">📦 <span>Inventory</span></button>
    <button class="nav-link" onclick="showTab('loyaltyTab', this)">👥 <span>Customers</span></button>
    <button class="nav-link" onclick="showTab('expenseTab', this)">💸 <span>Expenses</span></button>
    
    <div style="margin-top:auto;">
        <button class="nav-link" onclick="toggleTheme()">🌓 <span>Theme</span></button>
        <button class="nav-link" onclick="location.reload()" style="color:var(--danger)">🚪 <span>Logout</span></button>
    </div>
</nav>

<main id="mainContent" class="hidden">
    <h1 id="tabTitle" style="margin-bottom:20px;">Insights</h1>

    <div id="dashboard" class="tab-content">
        <div class="grid-4">
            <div class="stat-box"><small>Total Revenue</small><h2 id="statRev">K 0.00</h2></div>
            <div class="stat-box"><small>Net Profit</small><h2 id="statProfit" style="color:var(--success)">K 0.00</h2></div>
            <div class="stat-box"><small>Expenses</small><h2 id="statExp" style="color:var(--danger)">K 0.00</h2></div>
            <div class="stat-box"><small>Customers</small><h2 id="statCust">0</h2></div>
        </div>
        <div class="card"><h3>Revenue Stream</h3><canvas id="salesChart" height="80"></canvas></div>
    </div>

    <div id="posTab" class="tab-content hidden">
        <div style="display:grid; grid-template-columns: 1.5fr 1fr; gap:20px;">
            <div>
                <input id="posSearch" placeholder="🔍 Scan or Search Product..." onkeyup="renderPOS()">
                <div id="productGrid" class="product-grid"></div>
            </div>
            <div class="card">
                <h3>Current Order</h3>
                <select id="cartCustomer"><option value="">Walk-in Customer</option></select>
                <div id="cartBox" style="min-height:250px; margin:15px 0; border-bottom:1px solid var(--border); overflow-y:auto;"></div>
                <div style="display:flex; justify-content:space-between; font-weight:800; font-size:22px; margin-bottom:15px;">
                    <span>Total</span><span>K <span id="cartTotal">0.00</span></span>
                </div>
                <small>Payment Method:</small>
                <select id="paymentMethod" style="margin-top:5px;">
                    <option value="Cash">Cash</option>
                    <option value="Mobile Money">Mobile Money</option>
                    <option value="Card">Bank Card</option>
                </select>
                <button class="btn btn-brand" style="width:100%;" onclick="checkout()">Complete Transaction</button>
            </div>
        </div>
    </div>

    <div id="invTab" class="tab-content hidden">
        <div class="card">
            <h3>Manage Products</h3>
            <div style="display:grid; grid-template-columns: 1fr 2fr 1fr 1fr 1fr auto; gap:10px; margin-top:15px;">
                <input id="pbar" placeholder="Barcode">
                <input id="pname" placeholder="Name">
                <input id="pcost" type="number" placeholder="Cost Price">
                <input id="pprice" type="number" placeholder="Sell Price">
                <input id="pqty" type="number" placeholder="Stock">
                <button class="btn btn-brand" onclick="addItem()">Save</button>
            </div>
            <table>
                <thead><tr><th>Barcode</th><th>Name</th><th>Profit/Unit</th><th>Stock</th><th>Actions</th></tr></thead>
                <tbody id="invBody"></tbody>
            </table>
        </div>
    </div>

    <div id="loyaltyTab" class="tab-content hidden">
        <div class="card">
            <h3>Customer Registry</h3>
            <div style="display:grid; grid-template-columns: 2fr 2fr auto; gap:10px; margin-top:15px;">
                <input id="cname" placeholder="Customer Name">
                <input id="cphone" placeholder="Phone Number">
                <button class="btn btn-brand" onclick="addCustomer()">Register Customer</button>
            </div>
            <table style="margin-top:20px;">
                <thead><tr><th>Name</th><th>Phone</th><th>Total Spent</th></tr></thead>
                <tbody id="loyaltyBody"></tbody>
            </table>
        </div>
    </div>

    <div id="expenseTab" class="tab-content hidden">
        <div class="card">
            <h3>Log Business Expense</h3>
            <div style="display:grid; grid-template-columns: 2fr 1fr auto; gap:10px; margin-top:15px;">
                <input id="ename" placeholder="Expense (e.g. Rent, Transport, Electricity)">
                <input id="eamt" type="number" placeholder="Amount">
                <button class="btn btn-brand" onclick="addExpense()">Log Expense</button>
            </div>
            <table style="margin-top:20px;">
                <thead><tr><th>Description</th><th>Date</th><th>Amount</th></tr></thead>
                <tbody id="expenseBody"></tbody>
            </table>
        </div>
    </div>
</main>

<script>
    let inventory = JSON.parse(localStorage.getItem('lb_v12_inv')) || [];
    let sales = JSON.parse(localStorage.getItem('lb_v12_sales')) || [];
    let expenses = JSON.parse(localStorage.getItem('lb_v12_exp')) || [];
    let customers = JSON.parse(localStorage.getItem('lb_v12_cust')) || [];
    let cart = [];

    function login() {
        document.getElementById('loginPage').classList.add('hidden');
        document.getElementById('sidebar').classList.remove('hidden');
        document.getElementById('mainContent').classList.remove('hidden');
        refresh();
    }

    function refresh() {
        renderInventory(); renderPOS(); renderLoyalty(); renderExpenses(); updateStats();
    }

    // --- LOGIC FUNCTIONS ---
    function addItem() {
        const barcode = document.getElementById('pbar').value;
        const name = document.getElementById('pname').value;
        const cost = parseFloat(document.getElementById('pcost').value) || 0;
        const price = parseFloat(document.getElementById('pprice').value) || 0;
        const qty = parseInt(document.getElementById('pqty').value) || 0;
        if(!name) return;
        inventory.push({ barcode, name, cost, price, qty, sold: 0 });
        save(); refresh();
        ['pbar','pname','pcost','pprice','pqty'].forEach(id => document.getElementById(id).value = '');
    }

    function addCustomer() {
        const name = document.getElementById('cname').value;
        const phone = document.getElementById('cphone').value;
        if(!name) return;
        customers.push({ name, phone, spent: 0 });
        save(); refresh();
        document.getElementById('cname').value = ''; document.getElementById('cphone').value = '';
    }

    function addExpense() {
        const desc = document.getElementById('ename').value;
        const amt = parseFloat(document.getElementById('eamt').value) || 0;
        if(!desc || !amt) return;
        expenses.push({ desc, amt, date: new Date().toLocaleDateString() });
        save(); refresh();
        document.getElementById('ename').value = ''; document.getElementById('eamt').value = '';
    }

    function addToCart(i) {
        let p = inventory[i];
        if(p.qty <= 0) return alert('Out of stock');
        let item = cart.find(c => c.index === i);
        if(item) item.qty++; else cart.push({ index: i, name: p.name, price: p.price, qty: 1 });
        renderCart();
    }

    function checkout() {
        if(!cart.length) return;
        const total = parseFloat(document.getElementById('cartTotal').innerText);
        const method = document.getElementById('paymentMethod').value;
        const custIdx = document.getElementById('cartCustomer').value;

        let transactionProfit = 0;

        cart.forEach(c => {
            const prod = inventory[c.index];
            prod.qty -= c.qty;
            prod.sold += c.qty;
            transactionProfit += (prod.price - prod.cost) * c.qty;
        });

        if(custIdx !== "") customers[custIdx].spent += total;

        sales.unshift({ 
            id: 'LB'+Math.floor(Math.random()*9000), 
            amount: total, 
            profit: transactionProfit,
            method: method,
            date: new Date().toLocaleDateString() 
        });

        cart = []; save(); refresh(); renderCart();
        alert('Sale Confirmed via ' + method);
    }

    // --- RENDER FUNCTIONS ---
    function renderInventory() {
        document.getElementById('invBody').innerHTML = inventory.map((p, i) => `
            <tr>
                <td><code>${p.barcode || 'N/A'}</code></td>
                <td><b>${p.name}</b></td>
                <td style="color:var(--success)">K${(p.price - p.cost).toFixed(2)}</td>
                <td><span class="badge ${p.qty < 5 ? 'badge-danger' : 'badge-success'}">${p.qty} left</span></td>
                <td><button onclick="deleteItem(${i})" style="color:var(--danger); border:none; background:none; cursor:pointer;">Remove</button></td>
            </tr>
        `).join('');
    }

    function renderPOS() {
        const q = document.getElementById('posSearch').value.toLowerCase();
        document.getElementById('productGrid').innerHTML = inventory.filter(p => p.name.toLowerCase().includes(q) || p.barcode.includes(q)).map((p, i) => `
            <div class="product-card" onclick="addToCart(${inventory.indexOf(p)})">
                <div class="stock-label">${p.qty}</div>
                <strong>${p.name}</strong><br>
                <small style="color:var(--brand)">K${p.price.toFixed(2)}</small>
            </div>
        `).join('');
    }

    function renderCart() {
        let total = 0;
        document.getElementById('cartBox').innerHTML = cart.map((c, i) => {
            total += c.price * c.qty;
            return `<div style="display:flex; justify-content:space-between; margin-bottom:10px; font-size:13px;">
                <span>${c.name} x${c.qty}</span>
                <strong>K${(c.price*c.qty).toFixed(2)}</strong>
            </div>`;
        }).join('');
        document.getElementById('cartTotal').innerText = total.toFixed(2);
    }

    function renderLoyalty() {
        document.getElementById('loyaltyBody').innerHTML = customers.map(c => `
            <tr><td>${c.name}</td><td>${c.phone}</td><td>K${c.spent.toFixed(2)}</td></tr>
        `).join('');
        document.getElementById('cartCustomer').innerHTML = '<option value="">Walk-in Customer</option>' + 
            customers.map((c, i) => `<option value="${i}">${c.name}</option>`).join('');
    }

    function renderExpenses() {
        document.getElementById('expenseBody').innerHTML = expenses.map(e => `
            <tr><td>${e.desc}</td><td>${e.date}</td><td style="color:var(--danger)">K${e.amt.toFixed(2)}</td></tr>
        `).join('');
    }

    function updateStats() {
        const rev = sales.reduce((a,b) => a+b.amount, 0);
        const grossProfit = sales.reduce((a,b) => a+b.profit, 0);
        const exp = expenses.reduce((a,b) => a+b.amt, 0);
        document.getElementById('statRev').innerText = 'K ' + rev.toFixed(2);
        document.getElementById('statProfit').innerText = 'K ' + (grossProfit - exp).toFixed(2);
        document.getElementById('statExp').innerText = 'K ' + exp.toFixed(2);
        document.getElementById('statCust').innerText = customers.length;
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

    function save() {
        localStorage.setItem('lb_v12_inv', JSON.stringify(inventory));
        localStorage.setItem('lb_v12_sales', JSON.stringify(sales));
        localStorage.setItem('lb_v12_exp', JSON.stringify(expenses));
        localStorage.setItem('lb_v12_cust', JSON.stringify(customers));
    }
    function deleteItem(i) { inventory.splice(i,1); save(); refresh(); }
</script>
</body>
</html>
