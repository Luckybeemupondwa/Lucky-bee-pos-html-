<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Bee POS | Management System</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@400;700&family=Plus+Jakarta+Sans:wght@400;600;800&display=swap');
        body { font-family: 'Plus Jakarta Sans', sans-serif; background-color: #f8fafc; }
        .hide { display: none !important; }
        .receipt-font { font-family: 'Roboto Mono', monospace; }
        
        /* FEATURE 1: Low Stock Animation */
        @keyframes pulse-red {
            0% { box-shadow: 0 0 0 0 rgba(239, 68, 68, 0.4); }
            70% { box-shadow: 0 0 0 10px rgba(239, 68, 68, 0); }
            100% { box-shadow: 0 0 0 0 rgba(239, 68, 68, 0); }
        }
        .low-stock { animation: pulse-red 2s infinite; border-color: #fecaca !important; }

        /* FEATURE 2: Custom Scrollbars */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #f1f5f9; }
        ::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: #94a3b8; }
    </style>
</head>
<body class="h-screen overflow-hidden flex flex-col text-slate-900">

    <div id="loginScreen" class="fixed inset-0 z-[9999] bg-slate-950 flex items-center justify-center p-4">
        <div class="bg-white p-10 rounded-3xl shadow-2xl w-full max-w-sm border border-slate-100">
            <div class="text-center mb-8">
                <div class="w-20 h-20 bg-amber-400 rounded-2xl mx-auto flex items-center justify-center text-4xl shadow-xl shadow-amber-200 mb-4">🐝</div>
                <h1 class="text-3xl font-800 text-slate-900 tracking-tighter">LUCKY BEE</h1>
                <p class="text-slate-400 text-sm font-semibold uppercase tracking-widest">Enterprise POS</p>
            </div>
            <div class="space-y-4">
                <input id="loginUser" type="text" placeholder="Username" value="admin" class="w-full bg-slate-50 border-2 border-slate-100 p-4 rounded-xl outline-none focus:border-amber-400 transition-all">
                <input id="loginPass" type="password" placeholder="Password" value="1234" class="w-full bg-slate-50 border-2 border-slate-100 p-4 rounded-xl outline-none focus:border-amber-400 transition-all">
                <button onclick="loginApp()" class="w-full bg-amber-400 hover:bg-amber-500 text-slate-950 font-black py-4 rounded-xl shadow-lg transition-all active:scale-95">UNLOCK TERMINAL</button>
            </div>
        </div>
    </div>

    <header id="topBar" class="bg-white border-b border-slate-200 h-20 flex items-center justify-between px-8 shrink-0 hide">
        <div class="flex items-center gap-12">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 bg-amber-400 rounded-lg flex items-center justify-center text-xl shadow-sm">🐝</div>
                <span class="font-black text-2xl tracking-tighter">LuckyBee</span>
            </div>
            <nav class="flex h-20">
                <button onclick="navView('pos')" id="nav-pos" class="px-6 flex items-center gap-2 border-b-4 border-transparent font-bold text-slate-400 hover:text-slate-900 transition-all">
                    <i class="fa-solid fa-cash-register"></i> TERMINAL
                </button>
                <button onclick="navView('inv')" id="nav-inv" class="px-6 flex items-center gap-2 border-b-4 border-transparent font-bold text-slate-400 hover:text-slate-900 transition-all">
                    <i class="fa-solid fa-boxes-stacked"></i> INVENTORY
                </button>
                <button onclick="navView('dash')" id="nav-dash" class="px-6 flex items-center gap-2 border-b-4 border-transparent font-bold text-slate-400 hover:text-slate-900 transition-all">
                    <i class="fa-solid fa-chart-line"></i> SALES
                </button>
            </nav>
        </div>
        <div class="flex items-center gap-6">
            <div class="text-right">
                <p class="text-xs font-bold text-slate-400 uppercase">Cashier</p>
                <p class="text-sm font-black text-slate-900">Admin User</p>
            </div>
            <button onclick="location.reload()" class="w-10 h-10 flex items-center justify-center rounded-full bg-red-50 text-red-500 hover:bg-red-500 hover:text-white transition-all">
                <i class="fa-solid fa-power-off"></i>
            </button>
        </div>
    </header>

    <main id="mainContent" class="flex-1 flex overflow-hidden hide">
        
        <section class="flex-1 flex flex-col min-w-0">
            
            <div id="view-pos" class="flex-1 flex flex-col view-section">
                <div class="p-6 bg-white border-b border-slate-200">
                    <div class="relative w-full max-w-2xl">
                        <i class="fa-solid fa-magnifying-glass absolute left-4 top-1/2 -translate-y-1/2 text-slate-400"></i>
                        <input id="posSearch" type="text" placeholder="Press SPACE to search products..." onkeyup="renderPOS()" class="w-full pl-12 pr-4 py-4 bg-slate-100 rounded-2xl outline-none focus:ring-2 focus:ring-amber-400 transition-all font-semibold">
                    </div>
                </div>
                <div id="posGrid" class="flex-1 overflow-y-auto p-6 grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-4 content-start">
                    </div>
            </div>

            <div id="view-inv" class="flex-1 p-8 overflow-y-auto hide view-section">
                <div class="flex justify-between items-center mb-8">
                    <h2 class="text-3xl font-black text-slate-900 tracking-tight">Warehouse Control</h2>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-12 gap-8">
                    <div class="md:col-span-4 bg-white p-8 rounded-3xl border border-slate-200 shadow-sm">
                        <h3 id="formTitle" class="font-black text-xl mb-6">Create New Item</h3>
                        <div class="space-y-4">
                            <input id="pName" type="text" placeholder="Item Name" class="w-full border-2 border-slate-50 p-4 rounded-xl outline-none focus:border-amber-400 bg-slate-50">
                            <input id="pPrice" type="number" placeholder="Retail Price (K)" class="w-full border-2 border-slate-50 p-4 rounded-xl outline-none focus:border-amber-400 bg-slate-50">
                            <input id="pQty" type="number" placeholder="Initial Stock" class="w-full border-2 border-slate-50 p-4 rounded-xl outline-none focus:border-amber-400 bg-slate-50">
                            <input type="hidden" id="editIndex" value="-1">
                            <div class="flex gap-2 pt-4">
                                <button onclick="saveProduct()" class="flex-1 bg-slate-900 text-white font-black py-4 rounded-xl hover:bg-black transition-all">SAVE PRODUCT</button>
                                <button onclick="cancelEdit()" id="btnCancel" class="hide bg-slate-200 px-6 rounded-xl font-bold">X</button>
                            </div>
                        </div>
                    </div>
                    <div class="md:col-span-8 bg-white rounded-3xl border border-slate-200 shadow-sm overflow-hidden">
                        <table class="w-full text-left">
                            <thead class="bg-slate-50/50 border-b border-slate-100 text-slate-400 text-xs font-bold uppercase tracking-widest">
                                <tr><th class="p-6">Product Description</th><th class="p-6">Price</th><th class="p-6">Stock</th><th class="p-6 text-right">Actions</th></tr>
                            </thead>
                            <tbody id="invList" class="divide-y divide-slate-100"></tbody>
                        </table>
                    </div>
                </div>
            </div>

            <div id="view-dash" class="flex-1 p-8 overflow-y-auto hide view-section">
                <h2 class="text-3xl font-black text-slate-900 tracking-tight mb-8">Financial Overview</h2>
                <div class="grid grid-cols-3 gap-8 mb-10">
                    <div class="bg-amber-400 p-8 rounded-3xl shadow-xl shadow-amber-100">
                        <div class="text-amber-950 text-xs font-black uppercase tracking-widest opacity-60 mb-2">Total Income</div>
                        <div class="text-4xl font-black text-amber-950" id="dashRev">K 0.00</div>
                    </div>
                    <div class="bg-white p-8 rounded-3xl border border-slate-200 shadow-sm">
                        <div class="text-slate-400 text-xs font-black uppercase tracking-widest mb-2">Units Sold</div>
                        <div class="text-4xl font-black text-slate-900" id="dashSold">0</div>
                    </div>
                    <div class="bg-white p-8 rounded-3xl border border-slate-200 shadow-sm">
                        <div class="text-slate-400 text-xs font-black uppercase tracking-widest mb-2">Unique SKUs</div>
                        <div class="text-4xl font-black text-slate-900" id="dashItems">0</div>
                    </div>
                </div>
                <div class="bg-white rounded-3xl border border-slate-200 shadow-sm overflow-hidden">
                    <div class="p-6 font-black text-lg border-b border-slate-100 flex items-center justify-between">
                        <span>Latest Transactions</span>
                        <span class="text-xs bg-slate-100 px-3 py-1 rounded-full text-slate-500 uppercase">Live Data</span>
                    </div>
                    <table class="w-full text-left">
                        <tbody id="txHistory" class="divide-y divide-slate-50"></tbody>
                    </table>
                </div>
            </div>
        </section>

        <aside id="posBasket" class="w-[420px] bg-white border-l border-slate-200 flex flex-col shrink-0">
            <div class="p-6 border-b border-slate-200 flex justify-between items-center bg-slate-50/50">
                <span class="font-black text-xl tracking-tighter">ORDER DETAILS</span>
                <button onclick="clearCart()" class="text-xs font-black text-red-500 hover:bg-red-50 px-3 py-1 rounded-lg">CLEAR ALL</button>
            </div>
            <div id="cartList" class="flex-1 overflow-y-auto p-6 space-y-3">
                </div>
            <div class="p-8 bg-white border-t border-slate-200 shadow-[0_-10px_30px_rgba(0,0,0,0.03)]">
                <div class="flex justify-between mb-4">
                    <span class="text-slate-400 font-bold">Subtotal</span>
                    <span class="font-bold" id="cartSub">K 0.00</span>
                </div>
                <div class="flex justify-between items-center mb-8">
                    <span class="text-xl font-black">TOTAL</span>
                    <span class="text-4xl font-black text-amber-500" id="cartTotal">K 0.00</span>
                </div>
                <button onclick="checkout()" class="w-full bg-slate-950 text-white font-black py-5 rounded-2xl text-xl shadow-xl hover:bg-black transition-all active:scale-95 flex items-center justify-center gap-3">
                    <i class="fa-solid fa-check-circle text-amber-400"></i> COMPLETE SALE
                </button>
                <p class="text-center text-[10px] text-slate-300 font-bold mt-4 uppercase tracking-widest">Shortcut: Press [END] Key to Checkout</p>
            </div>
        </aside>

    </main>

    <script>
        let db = [], sales = [], cart = [];

        // FEATURE 3: Keyboard Shortcuts
        window.addEventListener('keydown', (e) => {
            if(e.code === 'Space' && e.target.tagName !== 'INPUT') {
                e.preventDefault();
                document.getElementById('posSearch').focus();
            }
            if(e.code === 'End') {
                e.preventDefault();
                checkout();
            }
        });

        function loginApp() {
            const u = document.getElementById('loginUser').value.trim();
            const p = document.getElementById('loginPass').value.trim();
            if(u === 'admin' && p === '1234') {
                try {
                    db = JSON.parse(localStorage.getItem('lb_v27_db')) || [];
                    sales = JSON.parse(localStorage.getItem('lb_v27_sales')) || [];
                } catch(e){}
                document.getElementById('loginScreen').classList.add('hide');
                document.getElementById('topBar').classList.remove('hide');
                document.getElementById('mainContent').classList.remove('hide');
                navView('pos');
                refreshAll();
            } else alert("Access Denied");
        }

        function navView(id) {
            document.querySelectorAll('.view-section').forEach(v => v.classList.add('hide'));
            document.querySelectorAll('nav button').forEach(b => {
                b.classList.remove('border-amber-400', 'text-slate-900');
                b.classList.add('text-slate-400');
            });
            
            document.getElementById(`view-${id}`).classList.remove('hide');
            document.getElementById(`nav-${id}`).classList.add('border-amber-400', 'text-slate-900');
            document.getElementById('posBasket').classList.toggle('hide', id !== 'pos');
        }

        function saveProduct() {
            const name = document.getElementById('pName').value.trim();
            const price = parseFloat(document.getElementById('pPrice').value);
            const qty = parseInt(document.getElementById('pQty').value);
            const idx = parseInt(document.getElementById('editIndex').value);
            if(!name || isNaN(price)) return alert("Invalid Data");

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
            document.getElementById('formTitle').innerText = "Update Item";
            document.getElementById('btnCancel').classList.remove('hide');
        }

        function deleteItem(i) { if(confirm("Confirm deletion?")) { db.splice(i,1); saveData(); refreshAll(); } }

        function renderInventory() {
            document.getElementById('invList').innerHTML = db.map((item, i) => `
                <tr class="hover:bg-slate-50 transition-colors">
                    <td class="p-6 font-bold text-slate-800">${item.name}</td>
                    <td class="p-6 font-black text-amber-600">K ${item.price.toFixed(2)}</td>
                    <td class="p-6">
                        <span class="${item.qty <= 5 ? 'text-red-500 bg-red-50' : 'text-slate-600 bg-slate-100'} px-3 py-1 rounded-lg font-black text-xs uppercase">
                            ${item.qty} in stock
                        </span>
                    </td>
                    <td class="p-6 text-right">
                        <button onclick="editItem(${i})" class="text-blue-600 font-black mr-4 hover:underline">EDIT</button>
                        <button onclick="deleteItem(${i})" class="text-red-400 font-black hover:text-red-600">DEL</button>
                    </td>
                </tr>
            `).join('');
        }

        function renderPOS() {
            const q = document.getElementById('posSearch').value.toLowerCase();
            document.getElementById('posGrid').innerHTML = db.map((item, i) => {
                // FEATURE 2: Smart Price Search (Check name OR price)
                if(q && !item.name.toLowerCase().includes(q) && !item.price.toString().includes(q)) return '';
                
                const disabled = item.qty <= 0;
                // FEATURE 1: Visual Alert for low stock
                const stockAlert = (!disabled && item.qty <= 5) ? 'low-stock' : '';

                return `
                <div onclick="${!disabled ? `addToCart(${i})` : ''}" class="bg-white p-5 rounded-2xl border border-slate-200 hover:border-amber-400 cursor-pointer transition-all shadow-sm flex flex-col justify-between h-40 ${disabled ? 'opacity-30 grayscale' : ''} ${stockAlert}">
                    <div class="font-black text-slate-900 leading-tight text-lg uppercase tracking-tighter">${item.name}</div>
                    <div class="flex justify-between items-end">
                        <span class="text-[10px] font-black uppercase ${item.qty <= 5 ? 'text-red-500' : 'text-slate-400'}">${item.qty} LEFT</span>
                        <span class="text-2xl font-black text-slate-950">K${item.price.toFixed(2)}</span>
                    </div>
                </div>`;
            }).join('');
        }

        function addToCart(i) {
            const existing = cart.find(c => c.index === i);
            if(existing) {
                if(existing.qty >= db[i].qty) return;
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
                <div class="bg-slate-50 p-4 rounded-2xl flex justify-between items-center border border-slate-100">
                    <div class="min-w-0 flex-1">
                        <div class="font-black text-slate-900 truncate uppercase text-xs tracking-tight">${c.name}</div>
                        <div class="text-xs font-bold text-amber-600">K${c.price.toFixed(2)}</div>
                    </div>
                    <div class="flex items-center gap-3 ml-4 bg-white p-1 rounded-xl shadow-sm border border-slate-100">
                        <button onclick="updateCart(${i},-1)" class="w-8 h-8 rounded-lg font-black text-slate-400 hover:text-red-500">-</button>
                        <span class="font-black text-sm w-4 text-center">${c.qty}</span>
                        <button onclick="updateCart(${i},1)" class="w-8 h-8 rounded-lg font-black text-slate-400 hover:text-amber-500">+</button>
                    </div>
                </div>`;
            }).join('') || `<div class="h-full flex flex-col items-center justify-center text-slate-300 py-20"><i class="fa-solid fa-basket-shopping text-4xl mb-2 opacity-20"></i><p class="font-black uppercase tracking-widest text-[10px]">Ready for order</p></div>`;
            
            document.getElementById('cartSub').innerText = `K ${total.toFixed(2)}`;
            document.getElementById('cartTotal').innerText = `K ${total.toFixed(2)}`;
        }

        function updateCart(i, amt) {
            cart[i].qty += amt;
            if(cart[i].qty > db[cart[i].index].qty) cart[i].qty = db[cart[i].index].qty;
            if(cart[i].qty <= 0) cart.splice(i, 1);
            renderCart();
        }

        function c
