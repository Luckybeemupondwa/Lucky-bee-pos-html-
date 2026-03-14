<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Lucky Bee POS</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;800&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

    <style>
        :root {
            --brand: #6366f1; 
            --brand-grad: linear-gradient(135deg, #6366f1 0%, #a855f7 100%);
            --bg: #f8fafc; --card: #ffffff; --text: #0f172a; --muted: #64748b; --border: #e2e8f0;
        }

        [data-theme="dark"] {
            --bg: #020617; --card: #0f172a; --text: #f8fafc; --muted: #94a3b8; --border: #1e293b;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Plus Jakarta Sans', sans-serif; }
        body { background: var(--bg); color: var(--text); overflow-x: hidden; }

        /* --- SPLASH SCREEN --- */
        #splash {
            position: fixed; inset: 0; background: #0f172a; z-index: 5000;
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            transition: opacity 0.8s ease-out;
        }
        .bee-logo {
            font-size: 60px; animation: float 2s infinite ease-in-out; margin-bottom: 20px;
        }
        @keyframes float { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-20px); } }
        
        .loader-bar {
            width: 200px; height: 4px; background: rgba(255,255,255,0.1);
            border-radius: 10px; overflow: hidden;
        }
        .loader-progress {
            width: 0%; height: 100%; background: var(--brand-grad);
            animation: load 2.5s forwards;
        }
        @keyframes load { to { width: 100%; } }

        /* --- LOGIN PAGE --- */
        #loginPage {
            position: fixed; inset: 0; background: var(--bg); z-index: 4000;
            display: flex; align-items: center; justify-content: center;
        }
        .login-card {
            width: 380px; padding: 40px; background: var(--card); border-radius: 30px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.1); text-align: center;
        }

        /* --- MAIN LAYOUT --- */
        nav { 
            width: 280px; background: var(--card); border-right: 1px solid var(--border); 
            height: 100vh; position: fixed; padding: 40px 20px; z-index: 100;
        }
        main { margin-left: 280px; padding: 40px; width: calc(100% - 280px); min-height: 100vh; }

        /* UI ELEMENTS */
        .nav-link {
            padding: 14px 18px; border-radius: 14px; color: var(--muted); font-weight: 600;
            display: flex; align-items: center; gap: 12px; cursor: pointer; margin-bottom: 8px; border: none; background: none; width: 100%; transition: 0.2s;
        }
        .nav-link.active { background: var(--brand-grad); color: white; box-shadow: 0 10px 15px -3px rgba(99, 102, 241, 0.3); }

        .card { background: var(--card); border-radius: 24px; border: 1px solid var(--border); padding: 25px; margin-bottom: 25px; }
        
        input { 
            width: 100%; padding: 14px; border-radius: 12px; border: 1px solid var(--border); 
            background: var(--bg); color: var(--text); margin-bottom: 12px; outline: none;
        }
        .btn { 
            padding: 14px 24px; border-radius: 12px; border: none; font-weight: 700; cursor: pointer;
            background: var(--brand-grad); color: white; transition: 0.3s;
        }
        .btn:active { transform: scale(0.95); }

        .product-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); gap: 15px; }
        .p-card { 
            background: var(--card); border: 1px solid var(--border); padding: 20px; 
            border-radius: 20px; text-align: center; cursor: pointer;
        }
        
        table { width: 100%; border-collapse: collapse; }
        th { text-align: left; padding: 15px; font-size: 11px; color: var(--muted); text-transform: uppercase; border-bottom: 1px solid var(--border); }
        td { padding: 15px; border-bottom: 1px solid var(--border); font-size: 14px; }

        .hidden { display: none !important; }
        @media (max-width: 1024px) { nav { width: 85px; } nav span { display: none; } main { margin-left: 85px; width: calc(100% - 85px); } }
    </style>
</head>
<body>

<div id="splash">
    <div class="bee-logo">🐝</div>
    <h2 style="color: white; margin-bottom: 20px; letter-spacing: 2px;">LUCKY BEE</h2>
    <div class="loader-bar"><div class="loader-progress"></div></div>
</div>

<div id="loginPage" class="hidden">
    <div class="login-card">
        <div style="font-size: 40px; margin-bottom: 10px;">🐝</div>
        <h2 style="margin-bottom: 30px; font-weight: 800;">Welcome Back</h2>
        <input id="username" placeholder="Username" value="admin">
        <input id="password" type="password" placeholder="Password" value="1234">
        <button class="btn" style="width: 100%;" onclick="attemptLogin()">Launch POS</button>
    </div>
</div>

<nav id="sidebar" class="hidden">
    <div style="font-size: 24px; font-weight: 800; margin-bottom: 40px; color: var(--brand)">🐝 BeePOS</div>
    <button class="nav-link active" onclick="showTab('dash', this)">📊 <span>Insights</span></button>
    <button class="nav-link" onclick="showTab('pos', this)">🛒 <span>Terminal</span></button>
    <button class="nav-link" onclick="showTab('inv', this)">📦 <span>Inventory</span></button>
    <div style="margin-top: auto;">
        <button class="nav-link" onclick="toggleTheme()">🌓 <span>Theme</span></button>
        <button class="nav-link" onclick="location.reload()" style="color: var(--danger)">🚪 <span>Logout</span></button>
    </div>
</nav>

<main id="mainApp" class="hidden">
    <h1 id="pageTitle" style="margin-bottom: 30px;">Business Insights</h1>

    <div id="dash" class="tab">
        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; margin-bottom: 30px;">
            <div class="card"><h5>Revenue</h5><h2 id="revVal">K 0.00</h2></div>
            <div class="card"><h5>Items Sold</h5><h2 id="soldVal">0</h2></div>
            <div class="card"><h5>Low Stock</h5><h2 id="lowVal" style="color:red">0</h2></div>
        </div>
        <div class="card">
            <canvas id="salesChart" height="100"></canvas>
        </div>
    </div>

    <div id="pos" class="tab hidden">
        <div style="display: grid; grid-template-columns: 1.6fr 1fr; gap: 30px;">
            <div>
                <input id="search" placeholder="Search product..." onkeyup="drawPOS()">
                <div id="grid" class="product-grid"></div>
            </div>
            <div class="card">
                <h3>Cart</h3>
                <div id="cart" style="min-height: 300px; margin: 20px 0;"></div>
                <div style="display: flex; justify-content: space-between; font-size: 24px; font-weight: 800;">
                    <span>Total</span><span>K <span id="total">0.00</span></span>
                </div>
                <button class="btn" style="width:100%; margin-top: 20px;" onclick="checkout()">Pay & Print</button>
            </div>
        </div>
    </div>

    <div id="inv" class="tab hidden">
        <div class="card">
            <div style="display: grid; grid-template-columns: 1fr 2fr 1fr 1fr auto; gap: 10px;">
                <input id="p_bar" placeholder="Barcode">
                <input id="p_name" placeholder="Product Name">
                <input id="p_cost" type="number" placeholder="Cost">
                <input id="p_price" type="number" placeholder="Price">
                <button class="btn" onclick="addStock()">Add</button>
            </div>
        </div>
        <div class="card">
            <table>
                <thead><tr><th>Barcode</th><th>Name</th><th>Margin</th><th>Stock</th></tr></thead>
                <tbody id="invTbl"></tbody>
            </table>
        </div>
    </div>
</main>

<script>
    let inventory = JSON.parse(localStorage.getItem('bee_inv')) || [];
    let sales = JSON.parse(localStorage.getItem('bee_sales')) || [];
    let cart = [];

    // 1. Splash Logic
    window.onload = () => {
        setTimeout(() => {
            document.getElementById('splash').style.opacity = '0';
            setTimeout(() => {
                document.getElementById('splash').classList.add('hidden');
                document.getElementById('loginPage').classList.remove('hidden');
            }, 800);
        }, 2500);
    };

    function attemptLogin() {
        document.getElementById('loginPage').classList.add('hidden');
        document.getElementById('sidebar').classList.remove('hidden');
        document.getElementById('mainApp').classList.remove('hidden');
        refresh();
    }

    function addStock() {
        const n = document.getElementById('p_name').value;
        const c = parseFloat(document.getElementById('p_cost').value) || 0;
        const p = parseFloat(document.getElementById('p_price').value) || 0;
        const b = document.getElementById('p_bar').value;
        if(!n) return;
        inventory.push({ barcode: b, name: n, cost: c, price: p, qty: 10, sold: 0 });
        save(); refresh();
    }

    function drawPOS() {
        const q = document.getElementById('search').value.toLowerCase();
        document.getElementById('grid').innerHTML = inventory.filter(p => p.name.toLowerCase().includes(q)).map((p, i) => `
            <div class="p-card" onclick="addToCart(${inventory.indexOf(p)})">
                <strong>${p.name}</strong><br>
                <span style="color:var(--brand); font-weight:800;">K${p.price.toFixed(2)}</span>
            </div>
        `).join('');
    }

    function addToCart(i) {
        let item = cart.find(c => c.index === i);
        if(item) item.qty++; else cart.push({ index: i, name: inventory[i].name, price: inventory[i].price, qty: 1 });
        renderCart();
    }

    function renderCart() {
        let t = 0;
        document.getElementById('cart').innerHTML = cart.map(c => {
            t += c.price * c.qty;
            return `<div style="display:flex; justify-content:space-between; margin-bottom:10px;">
                <span>${c.name} x${c.qty}</span><b>K${(c.price*c.qty).toFixed(2)}</b>
            </div>`;
        }).join('');
        document.getElementById('total').innerText = t.toFixed(2);
    }

    function checkout() {
        if(!cart.length) return;
        cart.forEach(c => {
            inventory[c.index].qty -= c.qty;
            inventory[c.index].sold += c.qty;
        });
        sales.push({ total: parseFloat(document.getElementById('total').innerText), date: new Date().toLocaleDateString() });
        cart = []; save(); refresh(); renderCart();
        alert("Sale Complete!");
    }

    function refresh() {
        document.getElementById('invTbl').innerHTML = inventory.map(p => `
            <tr><td>${p.barcode}</td><td><b>${p.name}</b></td><td>K${(p.price-p.cost).toFixed(2)}</td><td>${p.qty}</td></tr>
        `).join('');
        const rev = sales.reduce((a,b) => a+b.total, 0);
        document.getElementById('revVal').innerText = 'K ' + rev.toFixed(2);
        document.getElementById('soldVal').innerText = inventory.reduce((a,b) => a+b.sold, 0);
        document.getElementById('lowVal').innerText = inventory.filter(p => p.qty < 5).length;
        drawPOS();
    }

    function showTab(id, btn) {
        document.querySelectorAll('.tab').forEach(t => t.classList.add('hidden'));
        document.getElementById(id).classList.remove('hidden');
        document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
        btn.classList.add('active');
    }

    function toggleTheme() {
        const b = document.body;
        b.setAttribute('data-theme', b.getAttribute('data-theme') === 'light' ? 'dark' : 'light');
    }

    function save() { 
        localStorage.setItem('bee_inv', JSON.stringify(inventory)); 
        localStorage.setItem('bee_sales', JSON.stringify(sales)); 
    }
</script>
</body>
</html>
