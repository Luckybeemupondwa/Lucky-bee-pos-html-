<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Bee | Premium POS</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: { sans: ['Inter', 'sans-serif'] },
                    colors: { 
                        bee: '#FACC15',
                        surface: '#0F172A',
                        card: '#1E293B'
                    }
                }
            }
        }
    </script>
    <style>
        body { background-color: #020617; color: #f8fafc; }
        .hide { display: none !important; }
        .glass { background: rgba(30, 41, 59, 0.7); backdrop-filter: blur(12px); border: 1px solid rgba(255,255,255,0.1); }
        .active-nav { background: #FACC15 !important; color: #020617 !important; box-shadow: 0 4px 15px rgba(250, 204, 21, 0.3); }
        input::placeholder { color: #64748b; }
        /* Custom scrollbar for dark mode */
        ::-webkit-scrollbar { width: 5px; }
        ::-webkit-scrollbar-thumb { background: #334155; border-radius: 10px; }
    </style>
</head>
<body class="h-screen overflow-hidden flex">

    <div id="loginScreen" class="fixed inset-0 z-[9999] bg-[#020617] flex items-center justify-center p-6">
        <div class="glass p-10 rounded-[2rem] w-full max-w-md text-center shadow-2xl">
            <div class="w-24 h-24 bg-bee rounded-3xl mx-auto flex items-center justify-center text-5xl mb-6 shadow-[0_0_30px_rgba(250,204,21,0.4)]">🐝</div>
            <h1 class="text-4xl font-extrabold tracking-tighter mb-2">Lucky Bee</h1>
            <p class="text-slate-400 font-medium mb-10">Sign in to your register</p>
            
            <div class="space-y-4 text-left">
                <input id="loginUser" type="text" placeholder="Username" value="admin" class="w-full bg-slate-800/50 border border-slate-700 px-5 py-4 rounded-2xl outline-none focus:border-bee transition-all text-white">
                <input id="loginPass" type="password" placeholder="Password" value="1234" class="w-full bg-slate-800/50 border border-slate-700 px-5 py-4 rounded-2xl outline-none focus:border-bee transition-all text-white">
                <button onclick="loginApp()" class="w-full bg-bee text-black font-extrabold py-4 rounded-2xl hover:scale-[1.02] active:scale-95 transition-all mt-6 shadow-lg">
                    UNLOCK SYSTEM
                </button>
            </div>
        </div>
    </div>

    <aside id="sidebar" class="w-72 bg-surface border-r border-slate-800 flex flex-col hide p-6">
        <div class="flex items-center gap-4 mb-12 px-2">
            <div class="w-10 h-10 bg-bee rounded-xl flex items-center justify-center text-black font-bold">B</div>
            <span class="text-2xl font-black tracking-tighter">Lucky Bee</span>
        </div>
        
        <nav class="flex-1 space-y-3">
            <button onclick="navView('dash')" id="nav-dash" class="w-full flex items-center gap-4 px-5 py-4 rounded-2xl text-slate-400 font-bold hover:bg-slate-800 transition-all active-nav">
                <i class="fa-solid fa-house-chimney text-xl"></i> Dashboard
            </button>
            <button onclick="navView('pos')" id="nav-pos" class="w-full flex items-center gap-4 px-5 py-4 rounded-2xl text-slate-400 font-bold hover:bg-slate-800 transition-all">
                <i class="fa-solid fa-receipt text-xl"></i> Terminal
            </button>
            <button onclick="navView('inv')" id="nav-inv" class="w-full flex items-center gap-4 px-5 py-4 rounded-2xl text-slate-400 font-bold hover:bg-slate-800 transition-all">
                <i class="fa-solid fa-box-archive text-xl"></i> Stock
            </button>
        </nav>

        <button onclick="location.reload()" class="mt-auto flex items-center gap-4 px-5 py-4 text-red-400 font-bold hover:bg-red-500/10 rounded-2xl transition-all">
            <i class="fa-solid fa-power-off"></i> Logout
        </button>
    </aside>

    <main id="mainContent" class="flex-1 flex flex-col hide">
        
        <div id="view-dash" class="p-10 overflow-y-auto view-section">
            <header class="mb-12">
                <h1 class="text-4xl font-black tracking-tight mb-2">Morning, Admin 👋</h1>
                <p class="text-slate-500 font-medium">Here's what's happening today.</p>
            </header>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-12">
                <div class="glass p-8 rounded-[2rem]">
                    <p class="text-slate-400 text-sm font-bold uppercase tracking-widest mb-4">Daily Sales</p>
                    <div class="text-5xl font-black text-bee" id="dashRev">K 0.00</div>
                </div>
                <div class="glass p-8 rounded-[2rem]">
                    <p class="text-slate-400 text-sm font-bold uppercase tracking-widest mb-4">Volume</p>
                    <div class="text-5xl font-black" id="dashSold">0</div>
                </div>
                <div class="glass p-8 rounded-[2rem]">
                    <p class="text-slate-400 text-sm font-bold uppercase tracking-widest mb-4">SKU Count</p>
                    <div class="text-5xl font-black" id="dashItems">0</div>
                </div>
            </div>

            <div class="glass rounded-[2rem] overflow-hidden">
                <div class="p-8 border-b border-slate-800 font-black text-xl">Recent Sales Log</div>
                <table class="w-full text-left">
                    <thead class="bg-slate-800/30 text-slate-500 text-xs uppercase tracking-tighter">
                        <tr><th class="p-6">TX ID</th><th class="p-6">Date</th><th class="p-6">Items</th><th class="p-6">Value</th></tr>
                    </thead>
                    <tbody id="txHistory" class="divide-y divide-slate-800"></tbody>
                </table>
            </div>
        </div>

        <div id="view-pos" class="h-full flex hide view-section">
            <div class="flex-1 p-8 flex flex-col h-full">
                <div class="relative mb-8">
                    <i class="fa-solid fa-search absolute left-6 top-6 text-slate-500"></i>
                    <input id="posSearch" type="text" placeholder="Start typing to find products..." onkeyup="renderPOS()" class="w-full bg-slate-900 border border-slate-800 pl-16 pr-6 py-5 rounded-[1.5rem] outline-none focus:border-bee text-xl">
                </div>
                <div id="posGrid" class="grid grid-cols-2 lg:grid-cols-4 gap-6 overflow-y-auto pb-10"></div>
            </div>

            <div class="w-[450px] bg-surface border-l border-slate-800 flex flex-col">
                <div class="p-8 flex justify-between items-end border-b border-slate-800">
                    <h2 class="text-2xl font-black">Current Order</h2>
                    <button onclick="clearCart()" class="text-red-500 font-bold text-sm">RESET</button>
                </div>
                <div id="cartList" class="flex-1 overflow-y-auto p-6 space-y-4"></div>
                <div class="p-8 glass m-6 rounded-[2rem] space-y-6">
                    <div class="flex justify-between text-slate-400 font-bold"><span>Tax (0%)</span><span>K 0.00</span></div>
                    <div class="flex justify-between text-3xl font-black"><span>Total</span><span class="text-bee" id="cartTotal">K 0.00</span></div>
                    <button onclick="checkout()" class="w-full bg-bee text-black font-black py-6 rounded-2xl text-xl shadow-lg hover:brightness-110 active:scale-95 transition-all">CHECKOUT</button>
                </div>
            </div>
        </div>

        <div id="view-inv" class="p-10 hide view-section flex flex-col h-full">
            <h1 class="text-4xl font-black mb-10">Warehouse Inventory</h1>
            <div class="grid grid-cols-12 gap-8 flex-1 overflow-hidden">
                <div class="col-span-4 glass p-8 rounded-[2.5rem] h-fit">
                    <h3 class="text-xl font-black mb-8" id="formTitle">Create New Item</h3>
                    <input type="hidden" id="editIndex" value="-1">
                    <div class="space-y-6">
                        <input id="pName" type="text" placeholder="Product Name" class="w-full bg-slate-800/50 border border-slate-700 px-5 py-4 rounded-xl outline-none focus:border-bee">
                        <div class="grid grid-cols-2 gap-4">
                            <input id="pPrice" type="number" placeholder="Price (K)" class="w-full bg-slate-800/50 border border-slate-700 px-5 py-4 rounded-xl outline-none focus:border-bee">
                            <input id="pQty" type="number" placeholder="Stock" class="w-full bg-slate-800/50 border border-slate-700 px-5 py-4 rounded-xl outline-none focus:border-bee">
                        </div>
                        <div class="flex gap-4">
                            <button onclick="saveProduct()" class="flex-1 bg-bee text-black font-black py-4 rounded-xl transition-all">SAVE PRODUCT</button>
                            <button onclick="cancelEdit()" id="btnCancel" class="hide bg-slate-700 p-4 rounded-xl">X</button>
                        </div>
                    </div>
                </div>
                <div class="col-span-8 glass rounded-[2.5rem] overflow-hidden flex flex-col">
                    <div class="p-6 border-b border-slate-800">
                        <input id="invSearch" type="text" placeholder="Filter inventory..." onkeyup="renderInventory()" class="bg-slate-900 border border-slate-800 px-6 py-3 rounded-xl w-full max-w-sm outline-none">
                    </div>
                    <div class="overflow-y-auto flex-1">
                        <table class="w-full text-left">
                            <thead class="bg-slate-800/30 text-slate-500 text-xs font-bold uppercase">
                                <tr><th class="p-6">Item Name</th><th class="p-6">Price</th><th class="p-6">Stock</th><th class="p-6">Actions</th></tr>
                            </thead>
                            <tbody id="invList" class="divide-y divide-slate-800/50"></tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <script>
        let db = [], sales = [], cart = [];

        function loginApp() {
            const user = document.getElementById('loginUser').value.trim();
            const pass = document.getElementById('loginPass').value.trim();

            if (user === 'admin' && pass === '1234') {
                try {
                    db = JSON.parse(localStorage.getItem('lb_v25_db')) || [];
                    sales = JSON.parse(localStorage.getItem('lb_v25_sales')) || [];
                } catch(e) {}
                
                document.getElementById('loginScreen').classList.add('hide');
                document.getElementById('sidebar').classList.remove('hide');
                document.getElementById('mainContent').classList.remove('hide');
                refreshAll();
            } else {
                alert("Login Failed");
            }
        }

        function navView(id) {
            document.querySelectorAll('.view-section').forEach(v => v.classList.add('hide'));
            document.querySelectorAll('nav button').forEach(b => b.classList.remove('active-nav'));
            document.getElementById(`view-${id}`).classList.remove('hide');
            document.getElementById(`nav-${id}`).classList.add('active-nav');
        }

        // --- CORE LOGIC ---
        function saveProduct() {
            const name = document.getElementById('pName').value;
            const price = parseFloat(document.getElementById('pPrice').value);
            const qty = parseInt(document.getElementById('pQty').value);
            const idx = parseInt(document.getElementById('editIndex').value);

            if(!name || isNaN(price)) return;
            if(idx >= 0) db[idx] = { name, price, qty };
            else db.unshift({ name, price, qty });

            saveData(); cancelEdit(); refreshAll();
        }

        function cancelEdit() {
            document.getElementById('pName').value = '';
            document.getElementById('pPrice').value = '';
            document.getElementById('pQty').value = '';
            document.getElementById('editIndex').value = '-1';
            document.getElementById('formTitle').innerText = "Create New Item";
            document.getElementById('btnCancel').classList.add('hide');
        }

        function editItem(i) {
            document.getElementById('pName').value = db[i].name;
            document.getElementById('pPrice').value = db[i].price;
            document.getElementById('pQty').value = db[i].qty;
            document.getElementById('editIndex').value = i;
            document.getElementById('formTitle').innerText = "Updating Item";
            document.getElementById('btnCancel').classList.remove('hide');
        }

        function renderInventory() {
            const q = document.getElementById('invSearch').value.toLowerCase();
            document.getElementById('invList').innerHTML = db.map((item, i) => {
                if(q && !item.name.toLowerCase().includes(q)) return '';
                return `<tr class="hover:bg-slate-800/20 transition">
                    <td class="p-6 font-bold text-lg">${item.name}</td>
                    <td class="p-6 text-bee font-bold">K ${item.price.toFixed(2)}</td>
                    <td class="p-6"><span class="bg-slate-800 px-3 py-1 rounded-lg text-sm">${item.qty} in stock</span></td>
                    <td class="p-6">
                        <button onclick="editItem(${i})" class="text-blue-400 mr-4 font-bold">EDIT</button>
                        <button onclick="deleteItem(${i})" class="text-red-500 font-bold">DELETE</button>
                    </td>
                </tr>`;
            }).join('');
        }

        function deleteItem(i) { if(confirm("Delete?")) { db.splice(i,1); saveData(); refreshAll(); } }

        function renderPOS() {
            const q = document.getElementById('posSearch').value.toLowerCase();
            document.getElementById('posGrid').innerHTML = db.map((item, i) => {
                if(q && !item.name.toLowerCase().includes(q)) return '';
                const stockCol = item.qty < 5 ? 'text-red-500' : 'text-slate-500';
                return `<div onclick="addToCart(${i})" class="glass p-6 rounded-[2rem] cursor-pointer hover:border-bee transition-all active:scale-95">
                    <div class="text-xl font-black mb-2 truncate">${item.name}</div>
                    <div class="flex justify-between items-center">
                        <span class="text-2xl font-black text-bee">K${item.price.toFixed(2)}</span>
                        <span class="text-xs font-bold ${stockCol}">QTY ${item.qty}</span>
                    </div>
                </div>`;
            }).join('');
        }

        function addToCart(i) {
            const item = db[i];
            const ext = cart.find(c => c.index === i);
            if(ext) { if(ext.qty >= item.qty) return; ext.qty++; }
            else cart.push({ index: i, name: item.name, price: item.price, qty: 1 });
            renderCart();
        }

        function renderCart() {
            let total = 0;
            document.getElementById('cartList').innerHTML = cart.map((c, i) => {
                total += (c.price * c.qty);
                return `<div class="bg-slate-800/50 p-5 rounded-2xl flex justify-between items-center">
                    <div>
                        <div class="font-bold text-lg">${c.name}</div>
                        <div class="text-bee font-bold">K${c.price.toFixed(2)}</div>
                    </div>
                    <div class="flex items-center gap-4 bg-slate-900 rounded-xl p-2 border border-slate-700">
                        <button onclick="updateCart(${i},-1)" class="w-8 h-8 font-black">-</button>
                        <span class="font-black">${c.qty}</span>
                        <button onclick="updateCart(${i},1)" class="w-8 h-8 font-black text-bee">+</button>
                    </div>
                </div>`;
            }).join('') || `<div class="text-center text-slate-600 py-20 font-bold">NO ITEMS ADDED</div>`;
            document.getElementById('cartTotal').innerText = `K ${total.toFixed(2)}`;
        }

        function updateCart(i, v) {
            cart[i].qty += v;
            if(cart[i].qty > db[cart[i].index].qty) cart[i].qty = db[cart[i].index].qty;
            if(cart[i].qty <= 0) cart.splice(i,1);
            renderCart();
        }

        function checkout() {
            if(!cart.length) return;
            let total = 0, items = 0;
            cart.forEach(c => { db[c.index].qty -= c.qty; total += (c.price * c.qty); items += c.qty; });
            sales.unshift({ id: 'LB-'+Date.now().toString().slice(-6), date: new Date().toLocaleDateString(), total, items });
            saveData(); cart = []; refreshAll(); alert("Payment Successful!");
        }

        function renderDashboard() {
            const rev = sales.reduce((a,b)=>a+b.total, 0);
            const sold = sales.reduce((a,b)=>a+b.items, 0);
            document.getElementById('dashRev').innerText = `K ${rev.toFixed(2)}`;
            document.getElementById('dashSold').innerText = sold;
            document.getElementById('dashItems').innerText = db.length;
            document.getElementById('txHistory').innerHTML = sales.slice(0,8).map(tx => `
                <tr class="hover:bg-slate-800/10">
                    <td class="p-6 font-mono text-bee">#${tx.id}</td>
                    <td class="p-6 text-slate-400">${tx.date}</td>
                    <td class="p-6 font-bold">${tx.items}</td>
                    <td class="p-6 font-black text-lg">K ${tx.total.toFixed(2)}</td>
                </tr>
            `).join('');
        }

        function saveData() { 
            try { localStorage.setItem('lb_v25_db', JSON.stringify(db)); localStorage.setItem('lb_v25_sales', JSON.stringify(sales)); } catch(e) {} 
        }

        function clearCart() { cart = []; renderCart(); }
        function refreshAll() { renderInventory(); renderPOS(); renderCart(); renderDashboard(); }
    </script>
</body>
</html>
