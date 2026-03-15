<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Bee POS | Management System</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@400;700&family=Inter:wght@400;600;800&display=swap');
        body { font-family: 'Inter', sans-serif; background-color: #f1f5f9; }
        .hide { display: none !important; }
        .receipt-font { font-family: 'Roboto Mono', monospace; }
        .sidebar-link.active { background: #1e293b; color: white; border-left: 4px solid #eab308; }
    </style>
</head>
<body class="h-screen overflow-hidden flex flex-col">

    <div id="loginScreen" class="fixed inset-0 z-[9999] bg-slate-900 flex items-center justify-center">
        <div class="bg-white p-10 rounded-xl shadow-2xl w-full max-w-sm">
            <div class="text-center mb-8">
                <div class="text-4xl mb-2">🐝</div>
                <h1 class="text-2xl font-800 text-slate-900 uppercase tracking-widest">Lucky Bee</h1>
                <p class="text-slate-400 text-sm">Point of Sale System</p>
            </div>
            <div class="space-y-4">
                <input id="loginUser" type="text" placeholder="Username" value="admin" class="w-full border-2 border-slate-100 p-3 rounded-lg outline-none focus:border-yellow-500">
                <input id="loginPass" type="password" placeholder="Password" value="1234" class="w-full border-2 border-slate-100 p-3 rounded-lg outline-none focus:border-yellow-500">
                <button onclick="loginApp()" class="w-full bg-yellow-400 hover:bg-yellow-500 text-slate-900 font-bold py-3 rounded-lg transition-all">SIGN IN</button>
            </div>
        </div>
    </div>

    <header id="topBar" class="bg-slate-900 text-white h-16 flex items-center justify-between px-6 shrink-0 hide">
        <div class="flex items-center gap-8">
            <div class="flex items-center gap-2">
                <span class="text-2xl">🐝</span>
                <span class="font-black text-xl tracking-tight">LUCKY BEE</span>
            </div>
            <nav class="flex h-16">
                <button onclick="navView('pos')" id="nav-pos" class="px-6 flex items-center gap-2 hover:bg-slate-800 border-b-4 border-transparent font-bold">
                    <i class="fa-solid fa-cash-register"></i> TERMINAL
                </button>
                <button onclick="navView('inv')" id="nav-inv" class="px-6 flex items-center gap-2 hover:bg-slate-800 border-b-4 border-transparent font-bold">
                    <i class="fa-solid fa-boxes-stacked"></i> INVENTORY
                </button>
                <button onclick="navView('dash')" id="nav-dash" class="px-6 flex items-center gap-2 hover:bg-slate-800 border-b-4 border-transparent font-bold">
                    <i class="fa-solid fa-chart-line"></i> SALES REPORT
                </button>
            </nav>
        </div>
        <div class="flex items-center gap-4">
            <span class="text-slate-400 text-sm">Station: 01</span>
            <button onclick="location.reload()" class="bg-red-500/20 text-red-400 px-3 py-1 rounded text-xs font-bold hover:bg-red-500 hover:text-white">LOGOUT</button>
        </div>
    </header>

    <main id="mainContent" class="flex-1 flex overflow-hidden hide">
        
        <section class="flex-1 flex flex-col min-w-0">
            
            <div id="view-pos" class="flex-1 flex flex-col view-section">
                <div class="p-4 bg-white border-b flex gap-4">
                    <div class="relative flex-1">
                        <i class="fa-solid fa-search absolute left-4 top-1/2 -translate-y-1/2 text-slate-400"></i>
                        <input id="posSearch" type="text" placeholder="Search product name..." onkeyup="renderPOS()" class="w-full pl-12 pr-4 py-3 bg-slate-100 rounded-lg outline-none focus:ring-2 focus:ring-yellow-400">
                    </div>
                </div>
                <div id="posGrid" class="flex-1 overflow-y-auto p-4 grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-3 content-start">
                    </div>
            </div>

            <div id="view-inv" class="flex-1 p-6 overflow-y-auto hide view-section">
                <div class="flex justify-between items-center mb-6">
                    <h2 class="text-2xl font-black text-slate-800 uppercase">Manage Stock</h2>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <div class="bg-white p-6 rounded-xl border-2 border-slate-200">
                        <h3 id="formTitle" class="font-bold text-lg mb-4">Add New Item</h3>
                        <div class="space-y-4">
                            <input id="pName" type="text" placeholder="Item Name" class="w-full border p-3 rounded-lg outline-none">
                            <input id="pPrice" type="number" placeholder="Price (K)" class="w-full border p-3 rounded-lg outline-none">
                            <input id="pQty" type="number" placeholder="Stock Quantity" class="w-full border p-3 rounded-lg outline-none">
                            <input type="hidden" id="editIndex" value="-1">
                            <div class="flex gap-2">
                                <button onclick="saveProduct()" class="flex-1 bg-slate-900 text-white font-bold py-3 rounded-lg">SAVE ITEM</button>
                                <button onclick="cancelEdit()" id="btnCancel" class="hide bg-slate-200 px-4 rounded-lg">X</button>
                            </div>
                        </div>
                    </div>
                    <div class="md:col-span-2 bg-white rounded-xl border-2 border-slate-200 overflow-hidden">
                        <table class="w-full text-left">
                            <thead class="bg-slate-50 border-b border-slate-200">
                                <tr><th class="p-4">Product</th><th class="p-4">Price</th><th class="p-4">Stock</th><th class="p-4 text-right">Actions</th></tr>
                            </thead>
                            <tbody id="invList" class="divide-y divide-slate-100"></tbody>
                        </table>
                    </div>
                </div>
            </div>

            <div id="view-dash" class="flex-1 p-6 overflow-y-auto hide view-section">
                <h2 class="text-2xl font-black text-slate-800 uppercase mb-6">Sales Performance</h2>
                <div class="grid grid-cols-3 gap-6 mb-8">
                    <div class="bg-white p-6 rounded-xl border-b-4 border-yellow-400 shadow-sm">
                        <div class="text-slate-400 text-xs font-bold uppercase">Total Revenue</div>
                        <div class="text-3xl font-black" id="dashRev">K 0.00</div>
                    </div>
                    <div class="bg-white p-6 rounded-xl border-b-4 border-slate-800 shadow-sm">
                        <div class="text-slate-400 text-xs font-bold uppercase">Sales Volume</div>
                        <div class="text-3xl font-black" id="dashSold">0</div>
                    </div>
                    <div class="bg-white p-6 rounded-xl border-b-4 border-emerald-500 shadow-sm">
                        <div class="text-slate-400 text-xs font-bold uppercase">Inventory Items</div>
                        <div class="text-3xl font-black" id="dashItems">0</div>
                    </div>
                </div>
                <div class="bg-white rounded-xl border-2 border-slate-200">
                    <div class="p-4 font-bold border-b">Recent Transactions</div>
                    <table class="w-full text-left">
                        <tbody id="txHistory" class="divide-y divide-slate-100"></tbody>
                    </table>
                </div>
            </div>
        </section>

        <aside id="posBasket" class="w-96 bg-white border-l-2 border-slate-200 flex flex-col shrink-0">
            <div class="p-4 bg-slate-50 border-b flex justify-between items-center">
                <span class="font-bold text-slate-800">SHOPPING CART</span>
                <button onclick="clearCart()" class="text-xs font-bold text-red-500 hover:underline">EMPTY</button>
            </div>
            <div id="cartList" class="flex-1 overflow-y-auto p-4 space-y-2">
                </div>
            <div class="p-6 bg-slate-900 text-white">
                <div class="flex justify-between mb-2 text-slate-400 font-bold uppercase text-xs">
                    <span>Subtotal</span><span id="cartSub">K 0.00</span>
                </div>
                <div class="flex justify-between mb-6">
                    <span class="text-lg font-bold">TOTAL</span>
                    <span class="text-2xl font-black text-yellow-400" id="cartTotal">K 0.00</span>
                </div>
                <button onclick="checkout()" class="w-full bg-yellow-400 hover:bg-yellow-500 text-slate-900 font-black py-4 rounded-lg text-lg transition-all">
                    COMPLETE ORDER (CASH)
                </button>
            </div>
        </aside>

    </main>

    <script>
        let db = [], sales = [], cart = [];

        function loginApp() {
            const u = document.getElementById('loginUser').value.trim();
            const p = document.getElementById('loginPass').value.trim();
            if(u === 'admin' && p === '1234') {
                try {
                    db = JSON.parse(localStorage.getItem('lb_v26_db')) || [];
                    sales = JSON.parse(localStorage.getItem('lb_v26_sales')) || [];
                } catch(e){}
                document.getElementById('loginScreen').classList.add('hide');
                document.getElementById('topBar').classList.remove('hide');
                document.getElementById('mainContent').classList.remove('hide');
                navView('pos');
                refreshAll();
            } else alert("Invalid credentials");
        }

        function navView(id) {
            document.querySelectorAll('.view-section').forEach(v => v.classList.add('hide'));
            document.querySelectorAll('nav button').forEach(b => b.classList.remove('border-yellow-400', 'bg-slate-800'));
            
            document.getElementById(`view-${id}`).classList.remove('hide');
            document.getElementById(`nav-${id}`).classList.add('border-yellow-400', 'bg-slate-800');
            
            // Show/Hide Cart sidebar depending on view
            if(id === 'pos') document.getElementById('posBasket').classList.remove('hide');
            else document.getElementById('posBasket').classList.add('hide');
        }

        // --- INVENTORY LOGIC ---
        function saveProduct() {
            const name = document.getElementById('pName').value.trim();
            const price = parseFloat(document.getElementById('pPrice').value);
            const qty = parseInt(document.getElementById('pQty').value);
            const idx = parseInt(document.getElementById('editIndex').value);
            if(!name || isNaN(price)) return alert("Fill all fields correctly");

            if(idx >= 0) db[idx] = { name, price, qty };
            else db.unshift({ name, price, qty });
            
            saveData(); cancelEdit(); refreshAll();
        }

        function cancelEdit() {
            document.getElementById('pName').value = '';
            document.getElementById('pPrice').value = '';
            document.getElementById('pQty').value = '';
            document.getElementById('editIndex').value = '-1';
            document.getElementById('formTitle').innerText = "Add New Item";
            document.getElementById('btnCancel').classList.add('hide');
        }

        function editItem(i) {
            document.getElementById('pName').value = db[i].name;
            document.getElementById('pPrice').value = db[i].price;
            document.getElementById('pQty').value = db[i].qty;
            document.getElementById('editIndex').value = i;
            document.getElementById('formTitle').innerText = "Edit Item";
            document.getElementById('btnCancel').classList.remove('hide');
        }

        function deleteItem(i) { if(confirm("Delete item?")) { db.splice(i,1); saveData(); refreshAll(); } }

        function renderInventory() {
            document.getElementById('invList').innerHTML = db.map((item, i) => `
                <tr class="hover:bg-slate-50">
                    <td class="p-4 font-bold text-slate-700">${item.name}</td>
                    <td class="p-4 text-slate-500">K ${item.price.toFixed(2)}</td>
                    <td class="p-4"><span class="bg-slate-100 px-2 py-1 rounded font-bold">${item.qty}</span></td>
                    <td class="p-4 text-right">
                        <button onclick="editItem(${i})" class="text-blue-600 font-bold mr-3 text-sm">EDIT</button>
                        <button onclick="deleteItem(${i})" class="text-red-500 font-bold text-sm">DELETE</button>
                    </td>
                </tr>
            `).join('');
        }

        // --- POS LOGIC ---
        function renderPOS() {
            const q = document.getElementById('posSearch').value.toLowerCase();
            document.getElementById('posGrid').innerHTML = db.map((item, i) => {
                if(q && !item.name.toLowerCase().includes(q)) return '';
                const disabled = item.qty <= 0;
                return `
                <div onclick="${!disabled ? `addToCart(${i})` : ''}" class="bg-white p-4 rounded-xl border-2 border-transparent hover:border-yellow-400 cursor-pointer transition-all shadow-sm flex flex-col justify-between h-32 ${disabled ? 'opacity-40 grayscale' : ''}">
                    <div class="font-extrabold text-slate-800 leading-tight">${item.name}</div>
                    <div class="flex justify-between items-end">
                        <span class="text-xs text-slate-400 font-bold">STOCK: ${item.qty}</span>
                        <span class="text-lg font-black text-slate-900">K${item.price.toFixed(2)}</span>
                    </div>
                </div>`;
            }).join('');
        }

        function addToCart(i) {
            const existing = cart.find(c => c.index === i);
            if(existing) {
                if(existing.qty >= db[i].qty) return alert("Out of stock!");
                existing.qty++;
            } else {
                cart.push({ index: i, name: db[i].name, price: db[i].price, qty: 1 });
            }
            renderCart();
        }

        function renderCart() {
            let total = 0;
            document.getElementById('cartList').innerHTML = cart.map((c, i) => {
                const sub = c.price * c.qty;
                total += sub;
                return `
                <div class="bg-slate-50 p-3 rounded-lg flex justify-between items-center border border-slate-200">
                    <div class="min-w-0 flex-1">
                        <div class="font-bold text-slate-800 truncate">${c.name}</div>
                        <div class="text-xs text-slate-500">K${c.price.toFixed(2)} x ${c.qty}</div>
                    </div>
                    <div class="flex items-center gap-2 ml-4">
                        <button onclick="updateCart(${i},-1)" class="w-6 h-6 bg-slate-200 rounded font-bold">-</button>
                        <span class="font-bold w-4 text-center">${c.qty}</span>
                        <button onclick="updateCart(${i},1)" class="w-6 h-6 bg-slate-200 rounded font-bold">+</button>
                    </div>
                </div>`;
            }).join('') || `<div class="h-full flex items-center justify-center text-slate-300 font-bold uppercase tracking-tighter">Basket is Empty</div>`;
            
            document.getElementById('cartSub').innerText = `K ${total.toFixed(2)}`;
            document.getElementById('cartTotal').innerText = `K ${total.toFixed(2)}`;
        }

        function updateCart(i, amt) {
            cart[i].qty += amt;
            if(cart[i].qty > db[cart[i].index].qty) cart[i].qty = db[cart[i].index].qty;
            if(cart[i].qty <= 0) cart.splice(i, 1);
            renderCart();
        }

        function clearCart() { cart = []; renderCart(); }

        function checkout() {
            if(!cart.length) return;
            let total = 0, itemsCount = 0;
            cart.forEach(c => {
                db[c.index].qty -= c.qty;
                total += (c.price * c.qty);
                itemsCount += c.qty;
            });
            sales.unshift({ id: Date.now().toString().slice(-6), date: new Date().toLocaleString(), total, items: itemsCount });
            saveData(); cart = []; refreshAll();
            alert("Transaction Complete!");
        }

        function renderDashboard() {
            const rev = sales.reduce((a,b) => a + b.total, 0);
            const sold = sales.reduce((a,b) => a + b.items, 0);
            document.getElementById('dashRev').innerText = `K ${rev.toFixed(2)}`;
            document.getElementById('dashSold').innerText = sold;
            document.getElementById('dashItems').innerText = db.length;
            document.getElementById('txHistory').innerHTML = sales.map(s => `
                <tr class="text-sm">
                    <td class="p-4 font-mono text-slate-500">#${s.id}</td>
                    <td class="p-4">${s.date}</td>
                    <td class="p-4 font-bold">${s.items} Items</td>
                    <td class="p-4 font-black">K ${s.total.toFixed(2)}</td>
                </tr>
            `).join('');
        }

        function saveData() {
            try {
                localStorage.setItem('lb_v26_db', JSON.stringify(db));
                localStorage.setItem('lb_v26_sales', JSON.stringify(sales));
            } catch(e){}
        }

        function refreshAll() { renderInventory(); renderPOS(); renderCart(); renderDashboard(); }
    </script>
</body>
</html>
