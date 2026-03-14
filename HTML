<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Bee POS Pro</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    
    <style>
        :root {
            --primary: #4f46e5; --primary-dark: #4338ca; --success: #10b981;
            --warning: #f59e0b; --danger: #ef4444; --bg-main: #f8fafc;
            --sidebar-bg: #1e293b; --card-bg: #ffffff; --text-main: #1e293b; --text-muted: #64748b;
        }

        * { box-sizing: border-box; font-family: 'Inter', sans-serif; transition: all 0.2s ease; }
        body { margin: 0; background: var(--bg-main); color: var(--text-main); display: flex; min-height: 100vh; overflow-x: hidden; }

        /* Sidebar Navigation */
        nav { width: 260px; background: var(--sidebar-bg); color: white; display: flex; flex-direction: column; padding: 20px; position: fixed; height: 100vh; z-index: 100; }
        nav h2 { font-size: 1.2rem; margin-bottom: 5px; display: flex; align-items: center; gap: 10px; }
        #liveClock { font-size: 11px; color: #94a3b8; margin-bottom: 25px; }
        .nav-btn { background: transparent; color: #cbd5e1; text-align: left; padding: 12px; margin: 4px 0; width: 100%; border-radius: 8px; border: none; cursor: pointer; font-weight: 500; display: flex; align-items: center; gap: 10px; }
        .nav-btn:hover { background: #334155; color: white; }
        .nav-btn.active { background: var(--primary); color: white; }

        /* Content Area */
        main { margin-left: 260px; flex: 1; padding: 25px; width: calc(100% - 260px); }
        header { margin-bottom: 25px; display: flex; justify-content: space-between; align-items: center; background: white; padding: 15px 25px; margin: -25px -25px 25px -25px; border-bottom: 1px solid #e2e8f0; }

        .card { background: var(--card-bg); border-radius: 12px; padding: 20px; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05); margin-bottom: 20px; border: 1px solid #f1f5f9; }
        h3 { margin-top: 0; font-weight: 600; font-size: 16px; }

        input, select { width: 100%; padding: 10px; margin-bottom: 10px; border-radius: 8px; border: 1px solid #e2e8f0; font-size: 14px; outline: none; }
        
        .btn { padding: 10px 18px; border-radius: 8px; border: none; font-weight: 600; cursor: pointer; display: inline-flex; align-items: center; gap: 8px; font-size: 13px; }
        .btn-primary { background: var(--primary); color: white; }
        .btn-success { background: var(--success); color: white; }
        .btn-danger { background: var(--danger); color: white; }
        .btn-full { width: 100%; justify-content: center; }

        /* Terminal UI */
        .category-scroll { display: flex; gap: 8px; overflow-x: auto; padding-bottom: 10px; margin-bottom: 15px; scrollbar-width: none; }
        .cat-pill { padding: 6px 14px; background: #e2e8f0; border-radius: 20px; font-size: 11px; font-weight: 600; cursor: pointer; white-space: nowrap; }
        .cat-pill.active { background: var(--primary); color: white; }

        .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 15px; margin-bottom: 20px; }
        .stat-card { padding: 15px; border-radius: 12px; color: white; }
        .stat-1 { background: linear-gradient(135deg, #6366f1, #4f46e5); }
        .stat-2 { background: linear-gradient(135deg, #10b981, #059669); }

        .product-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(130px, 1fr)); gap: 10px; }
        .product-item { background: #f8fafc; border: 1px solid #e2e8f0; padding: 12px; border-radius: 10px; text-align: center; cursor: pointer; }
        .product-item:hover { border-color: var(--primary); transform: translateY(-2px); background: white; }

        table { width: 100%; border-collapse: collapse; font-size: 13px; }
        th { text-align: left; color: var(--text-muted); padding: 10px; border-bottom: 2px solid #f1f5f9; }
        td { padding: 10px; border-bottom: 1px solid #f1f5f9; }

        /* Login */
        #loginPage { position: fixed; inset: 0; background: var(--sidebar-bg); z-index: 1000; display: flex; align-items: center; justify-content: center; }
        .login-card { background: white; padding: 40px; border-radius: 16px; width: 340px; text-align: center; box-shadow: 0 20px 25px -5px rgba(0,0,0,0.2); }

        .hidden { display: none !important; }
        #notification-container { position: fixed; top: 20px; right: 20px; z-index: 9999; }
        .toast { background: white; padding: 12px 20px; border-radius: 8px; box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1); margin-bottom: 8px; border-left: 4px solid var(--primary); font-size: 13px; font-weight: 500; animation: slide 0.3s ease; }
        @keyframes slide { from { transform: translateX(100%); } to { transform: translateX(0); } }

        @media (max-width: 768px) { nav { width: 70px; padding: 10px; } nav span, #liveClock, nav h2 { display: none; } main { margin-left: 70px; width: calc(100% - 70px); } }
    </style>
</head>
<body>

<div id="notification-container"></div>

<div id="loginPage">
    <div class="login-card">
        <h2 style="color: var(--primary); margin-bottom: 5px;">Lucky Bee 6.2</h2>
        <p style="color: var(--text-muted); font-size: 13px; margin-bottom: 20px;">Secure Point of Sale Terminal</p>
        <input id="username" placeholder="Username" value="admin">
        <input id="password" type="password" placeholder="Password" value="1234">
        <button class="btn btn-primary btn-full" onclick="login()">Login to Terminal</button>
        <p style="font-size: 10px; color: #94a3b8; margin-top: 15px;">Admin: 1234 | Cashier: 1111</p>
    </div>
</div>

<nav id="sidebar" class="hidden">
    <h2>🐝 <span>Lucky Bee</span></h2>
    <div id="liveClock"></div>
    <button class="nav-btn active" onclick="showTab('dashboard', this)"><span>📊</span> <span>Dashboard</span></button>
    <button class="nav-btn" onclick="showTab('posPage', this)"><span>🛒</span> <span>Terminal</span></button>
    <button id="navInventory" class="nav-btn" onclick="showTab('inventoryPage', this)"><span>📦</span> <span>Inventory</span></button>
    <button class="nav-btn" onclick="showTab('salesPage', this)"><span>📜</span> <span>History</span></button>
    <div style="margin-top: auto;">
        <button class="nav-btn btn-danger" onclick="logout()" style="color: white; background: #dc2626; border-radius: 8px;"><span>🚪</span> <span>Logout</span></button>
    </div>
</nav>

<main id="mainContent" class="hidden">
    <header>
        <h3 id="currentTabTitle">Dashboard</h3>
        <div id="userBadge" style="font-weight: 700; color: var(--primary); font-size: 12px; letter-spacing: 0.5px;"></div>
    </header>

    <div id="dashboard" class="tab-content">
        <div class="stats-grid">
            <div class="stat-card stat-1"><h3>Items</h3><h2 id="totalProducts">0</h2></div>
            <div class="stat-card stat-2"><h3>Revenue</h3><h2>K <span id="totalRevenue">0.00</span></h2></div>
        </div>
        <div class="card">
            <h3>Recent Sales Trend</h3>
            <canvas id="salesChart" height="120"></canvas>
        </div>
    </div>

    <div id="posPage" class="tab-content hidden">
        <div style="display: grid; grid-template-columns: 1.6fr 1fr; gap: 20px;">
            <div>
                <div class="category-scroll" id="catFilterList"></div>
                <div class="card">
                    <input id="searchInput" placeholder="🔍 Search products..." onkeyup="filterProducts()">
                    <div id="productButtons" class="product-grid"></div>
                </div>
            </div>
            <div class="card">
                <h3>Current Cart</h3>
                <div id="cartList" style="min-height: 250px; border: 1px dashed #e2e8f0; border-radius: 8px; padding: 10px; margin-bottom: 15px;"></div>
                <div style="font-size: 1.3rem; font-weight: 700; margin-bottom: 15px; display: flex; justify-content: space-between;">
                    <span>Total</span>
                    <span style="color: var(--primary)">K <span id="totalValue">0.00</span></span>
                </div>
                <button class="btn btn-success btn-full" style="padding: 15px;" onclick="checkout()">COMPLETE SALE</button>
            </div>
        </div>
    </div>

    <div id="inventoryPage" class="tab-content hidden">
        <div class="card">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;">
                <h3>Product Management</h3>
                <button class="btn btn-success" onclick="exportCSV()">📥 Export Inventory</button>
            </div>
            <div style="display: grid; grid-template-columns: 2fr 1fr 1fr 1fr auto; gap: 8px; margin-bottom: 20px;">
                <input id="pname" placeholder="Name">
                <input id="pprice" type="number" placeholder="Price">
                <input id="pqty" type="number" placeholder="Qty">
                <select id="pcat">
                    <option value="General">General</option>
                    <option value="Food">Food</option>
                    <option value="Drinks">Drinks</option>
                    <option value="Hardware">Hardware</option>
                </select>
                <button class="btn btn-primary" onclick="addProduct()">Add</button>
            </div>
            <table>
                <thead><tr><th>Name</th><th>Category</th><th>Price</th><th>Stock</th><th>Action</th></tr></thead>
                <tbody id="inventoryList"></tbody>
            </table>
        </div>
    </div>

    <div id="salesPage" class="tab-content hidden">
        <div class="card">
            <table>
                <thead><tr><th>TXN ID</th><th>Date</th><th>Amount</th><th>Receipt</th></tr></thead>
                <tbody id="salesList"></tbody>
            </table>
        </div>
    </div>
</main>

<script>
    // Global State
    let inventory = JSON.parse(localStorage.getItem("lb_inventory")) || [];
    let sales = JSON.parse(localStorage.getItem("lb_sales")) || [];
    let cart = [];
    let currentCategory = "All";
    let myChart = null;
    let userRole = "";

    // Clock
    setInterval(() => {
        const el = document.getElementById('liveClock');
        if(el) el.innerText = new Date().toLocaleString();
    }, 1000);

    // Login logic
    function login() {
        const u = document.getElementById("username").value.trim();
        const p = document.getElementById("password").value.trim();
        if ((u === "admin" && p === "1234") || (u === "cashier" && p === "1111")) {
            userRole = u;
            document.getElementById("loginPage").classList.add("hidden");
            document.getElementById("sidebar").classList.remove("hidden");
            document.getElementById("mainContent").classList.remove("hidden");
            document.getElementById("userBadge").innerText = "AUTHORIZED: " + u.toUpperCase();
            
            if(u !== 'admin') document.getElementById("navInventory").classList.add("hidden");
            initApp();
        } else {
            notify("Invalid Credentials", "danger");
        }
    }

    function initApp() {
        updateStats();
        loadInventory();
        loadCategoryFilters();
        filterProducts();
        loadSalesHistory();
        drawChart();
        checkLowStock();
    }

    function notify(msg, type = 'primary') {
        const container = document.getElementById('notification-container');
        const toast = document.createElement('div');
        toast.className = 'toast';
        toast.style.borderLeftColor = `var(--${type})`;
        toast.innerText = msg;
        container.appendChild(toast);
        setTimeout(() => { toast.style.opacity = '0'; setTimeout(() => toast.remove(), 500); }, 3000);
    }

    function addProduct() {
        const name = document.getElementById("pname").value;
        const price = parseFloat(document.getElementById("pprice").value);
        const qty = parseInt(document.getElementById("pqty").value);
        const cat = document.getElementById("pcat").value;
        
        if(!name || isNaN(price) || isNaN(qty)) return notify("Fill all fields correctly", "danger");

        inventory.push({ name, price, qty, category: cat });
        saveData(); initApp();
        notify("Product added successfully", "success");
        document.getElementById("pname").value = "";
        document.getElementById("pprice").value = "";
        document.getElementById("pqty").value = "";
    }

    function loadCategoryFilters() {
        const cats = ["All", ...new Set(inventory.map(p => p.category))];
        const container = document.getElementById("catFilterList");
        container.innerHTML = cats.map(c => `
            <div class="cat-pill ${currentCategory === c ? 'active' : ''}" onclick="setCategory('${c}')">${c}</div>
        `).join('');
    }

    function setCategory(cat) {
        currentCategory = cat;
        loadCategoryFilters();
        filterProducts();
    }

    function filterProducts() {
        const q = document.getElementById("searchInput").value.toLowerCase();
        const grid = document.getElementById("productButtons");
        grid.innerHTML = inventory.map((p, i) => {
            const matchCat = currentCategory === "All" || p.category === currentCategory;
            const matchSearch = p.name.toLowerCase().includes(q);
            if(matchCat && matchSearch && p.qty > 0) {
                return `<div class="product-item" onclick="addToCart(${i})">
                    <strong>${p.name}</strong><br>
                    <small style="color:var(--text-muted)">${p.category}</small><br>
                    <span style="color:var(--primary); font-weight:bold;">K${p.price.toFixed(2)}</span>
                </div>`;
            }
            return '';
        }).join('');
    }

    function addToCart(i) {
        let item = inventory[i];
        let found = cart.find(c => c.index === i);
        if (found) {
            if(found.qty < item.qty) found.qty++;
            else notify("Max stock reached", "warning");
        } else {
            cart.push({ index: i, name: item.name, price: item.price, qty: 1 });
        }
        renderCart();
    }

    function renderCart() {
        const list = document.getElementById("cartList");
        let total = 0;
        if(cart.length === 0) { list.innerHTML = "<p style='text-align:center; color:#94a3b8; font-size:12px;'>Cart is empty</p>"; }
        else {
            list.innerHTML = cart.map((c, i) => {
                total += c.price * c.qty;
                return `<div style="display:flex; justify-content:space-between; margin-bottom:8px; font-size:12px;">
                    <span>${c.name} x${c.qty}</span>
                    <span>K${(c.price * c.qty).toFixed(2)} <button onclick="removeItem(${i})" style="color:var(--danger); border:none; background:none; cursor:pointer; font-weight:bold;">×</button></span>
                </div>`;
            }).join('');
        }
        document.getElementById("totalValue").innerText = total.toFixed(2);
    }

    function checkout() {
        if (!cart.length) return notify("Cart is empty", "warning");
        let total = 0;
        let itemsSummary = [];
        
        cart.forEach(c => {
            inventory[c.index].qty -= c.qty;
            total += c.price * c.qty;
            itemsSummary.push(`${c.name}(${c.qty})`);
        });

        const txn = {
            id: 'LB' + Math.floor(1000 + Math.random() * 9000),
            date: new Date().toLocaleString(),
            amount: total,
            items: itemsSummary.join(', ')
        };

        sales.unshift(txn);
        cart = [];
        saveData(); initApp(); renderCart();
        notify("Sale Completed! TXN: " + txn.id, "success");
    }

    function loadInventory() {
        document.getElementById("inventoryList").innerHTML = inventory.map((p, i) => `
            <tr>
                <td><strong>${p.name}</strong></td>
                <td>${p.category}</td>
                <td>K${p.price.toFixed(2)}</td>
                <td>${p.qty} ${p.qty <= 5 ? '⚠️' : ''}</td>
                <td><button class="btn btn-danger" onclick="deleteProduct(${i})" style="padding:4px 8px; font-size:10px;">Del</button></td>
            </tr>
        `).join('');
    }

    function loadSalesHistory() {
        document.getElementById("salesList").innerHTML = sales.map(s => `
            <tr>
                <td><code>${s.id}</code></td>
                <td>${s.date}</td>
                <td>K${s.amount.toFixed(2)}</td>
                <td><button class="btn btn-primary" onclick="notify('Generating PDF...')" style="padding:4px 8px; font-size:10px;">PDF</button></td>
            </tr>
        `).join('');
    }

    function checkLowStock() {
        const low = inventory.filter(p => p.qty <= 5);
        if(low.length > 0 && userRole === 'admin') notify(`Low Stock: ${low.length} items need attention!`, "warning");
    }

    function drawChart() {
        const ctx = document.getElementById("salesChart").getContext('2d');
        if(myChart) myChart.destroy();
        const recent = sales.slice(0, 10).reverse();
        myChart = new Chart(ctx, {
            type: 'line',
            data: {
                labels: recent.map(s => s.id),
                datasets: [{ label: 'Sales K', data: recent.map(s => s.amount), borderColor: '#4f46e5', tension: 0.3, fill: true, backgroundColor: 'rgba(79, 70, 229, 0.05)' }]
            },
            options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
        });
    }

    function updateStats() {
        document.getElementById("totalProducts").innerText = inventory.length;
        const rev = sales.reduce((a, b) => a + b.amount, 0);
        document.getElementById("totalRevenue").innerText = rev.toFixed(2);
    }

    function exportCSV() {
        let csv = "Name,Category,Price,Qty\n";
        inventory.forEach(p => csv += `${p.name},${p.category},${p.price},${p.qty}\n`);
        const blob = new Blob([csv], { type: 'text/csv' });
        const url = window.URL.createObjectURL(blob);
        const a = document.createElement('a');
        a.href = url;
        a.download = `LB_Inventory_${Date.now()}.csv`;
        a.click();
    }

    function showTab(tabId, btn) {
        document.querySelectorAll('.tab-content').forEach(t => t.classList.add('hidden'));
        document.getElementById(tabId).classList.remove('hidden');
        document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        document.getElementById('currentTabTitle').innerText = btn.innerText.trim();
        if(tabId === 'dashboard') drawChart();
    }

    function deleteProduct(i) { if(confirm("Remove product?")) { inventory.splice(i, 1); saveData(); initApp(); } }
    function removeItem(i) { cart.splice(i, 1); renderCart(); }
    function logout() { location.reload(); }
    function saveData() { localStorage.setItem("lb_inventory", JSON.stringify(inventory)); localStorage.setItem("lb_sales", JSON.stringify(sales)); }
</script>
</body>
</html>
