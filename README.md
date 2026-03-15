<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Bee POS | Cloud</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;800&display=swap');
        body { font-family: 'Plus Jakarta Sans', sans-serif; background-color: #f8fafc; }
        .hide { display: none !important; }
        
        @keyframes pulse-red {
            0% { box-shadow: 0 0 0 0 rgba(239, 68, 68, 0.4); }
            70% { box-shadow: 0 0 0 10px rgba(239, 68, 68, 0); }
            100% { box-shadow: 0 0 0 0 rgba(239, 68, 68, 0); }
        }
        .low-stock { animation: pulse-red 2s infinite; border-color: #fecaca !important; }

        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 10px; }
    </style>
</head>
<body class="h-screen overflow-hidden flex flex-col text-slate-900">

    <div id="loginScreen" class="fixed inset-0 z-[9999] bg-slate-950 flex items-center justify-center p-4">
        <div class="bg-white p-10 rounded-3xl shadow-2xl w-full max-w-sm border border-slate-100">
            <div class="text-center mb-8">
                <div class="w-20 h-20 bg-amber-400 rounded-2xl mx-auto flex items-center justify-center text-4xl shadow-xl shadow-amber-200 mb-4">🐝</div>
                <h1 class="text-3xl font-800 text-slate-900 tracking-tighter">LUCKY BEE</h1>
                <p class="text-slate-400 text-sm font-semibold uppercase tracking-widest">Enterprise Cloud</p>
            </div>
            <div class="space-y-4">
                <input id="loginUser" type="text" placeholder="Username" value="admin" class="w-full bg-slate-50 border-2 border-slate-100 p-4 rounded-xl outline-none focus:border-amber-400 transition-all">
                <input id="loginPass" type="password" placeholder="Password" value="1234" class="w-full bg-slate-50 border-2 border-slate-100 p-4 rounded-xl outline-none focus:border-amber-400 transition-all">
                <button onclick="loginApp()" class="w-full bg-amber-400 hover:bg-amber-500 text-slate-950 font-black py-4 rounded-xl shadow-lg transition-all active:scale-95">UNLOCK SYSTEM</button>
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
                <p class="text-xs font-bold text-emerald-500 uppercase flex items-center justify-end gap-1">
                    <span class="w-2 h-2 bg-emerald-500 rounded-full"></span> Online
                </p>
                <p class="text-sm font-black text-slate-900">Admin</p>
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
                        <input id="posSearch" type="text" placeholder="Search by name or price..." onkeyup="renderPOS()" class="w-full pl-12 pr-4 py-4 bg-slate-100 rounded-2xl outline-none focus:ring-2 focus:ring-amber-400 transition-all font-semibold">
                    </div>
                </div>
                <div id="posGrid" class="flex-1 overflow-y-auto p-6 grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-4 content-start"></div>
            </div>

            <div id="view-inv" class="flex-1 p-8 overflow-y-auto hide view-section">
                <div class="grid grid-cols-1 md:grid-cols-12 gap-8">
                    <div class="md:col-span-4 bg-white p-8 rounded-3xl border border-slate-200 shadow-sm h-fit">
                        <h3 id="formTitle" class="font-black text-xl mb-6">Product Setup</h3>
                        <div class="space-y-4">
                            <input id="pName" type="text" placeholder="Item Name" class="w-full border-2 border-slate-50 p-4 rounded-xl outline-none focus:border-amber-400 bg-slate-50">
                            <input id="pPrice" type="number" placeholder="Price (K)" class="w-full border-2 border-slate-50 p-4 rounded-xl outline-none focus:border-amber-400 bg-slate-50">
                            <input id="pQty" type="number" placeholder="Stock" class="w-full border-2 border-slate-50 p-4 rounded-xl outline-none focus:border-amber-400 bg-slate-50">
                            <input type="hidden" id="editIndex" value="-1">
                            <div class="flex gap-2">
                                <button onclick="saveProduct()" class="flex-1 bg-slate-900 text-white font-black py-4 rounded-xl">SAVE</button>
                                <button onclick="cancelEdit()" id="btnCancel" class="hide bg-slate-200 px-4 rounded-xl">X</button>
                            </div>
                        </div>
                    </div>
                    <div class="md:col-span-8 bg-white rounded-3xl border border-slate-200 overflow-hidden">
                        <table class="w-full text-left">
                            <thead class="bg-slate-50 text-xs font-bold uppercase tracking-widest text-slate-400">
                                <tr><th class="p-6">Description</th><th class="p-6">Price</th><th class="p-6">Stock</th><th class="p-6 text-right">Actions</th></tr>
                            </thead>
                            <tbody id="invList" class="divide-y divide-slate-100"></tbody>
                        </table>
                    </div>
                </div>
            </div>

            <div id="view-dash" class="flex-1 p-8 overflow-y-auto hide view-section">
                <div class="grid grid-cols-3 gap-8 mb-8">
                    <div class="bg-amber-400 p-8 rounded-3xl shadow-xl shadow-amber-100">
                        <div class="text-amber-950 text-xs font-black uppercase opacity-60 mb-2">Revenue</div>
                        <div class="text-4xl font-black text-amber-950" id="dashRev">K 0.00</div>
                    </div>
                    <div class="bg-white p-8 rounded-3xl border shadow-sm">
                        <div class="text-slate-400 text-xs font-black uppercase mb-2">Sold</div>
                        <div class="text-4xl font-black" id="dashSold">0</div>
                    </div>
                    <div class="bg-white p-8 rounded-3xl border shadow-sm">
                        <div class="text-slate-400 text-xs font-black uppercase mb-2">Inventory</div>
                        <div class="text-4xl font-black" id="dashItems">0</div>
                    </div>
                </div>
                <div class="bg-white rounded-3xl border overflow-hidden">
                    <table class="w-full text-left">
                        <tbody id="txHistory" class="divide-y divide-slate-50"></tbody>
                    </table>
                </div>
            </div>
        </section>

        <aside id="posBasket" class="w-[420px] bg-white border-l border-slate-200 flex flex-col shrink-0">
            <div class="p-6 border-b flex justify-between items-center bg-slate-50/50">
                <span class="font-black text-xl">ORDER</span>
                <button onclick="clearCart()" class="text-xs font-black text-red-500">RESET</button>
            </div>
            <div id="cartList" class="flex-1 overflow-y-auto p-6 space-y-3"></div>
            <div class="p-8 border-t">
                <div class="flex justify-between items-center mb-6">
                    <span class="text-xl font-black">TOTAL</span>
                    <span class="text-4xl font-black text-amber-500" id="cartTotal">K 0.00</span>
                </div>
                <button onclick="checkout()" class="w-full bg-slate-950 text-white font-black py-5 rounded-2xl text-xl shadow-xl active:scale-95 transition-all">COMPLETE SALE</button>
            </div>
        </aside>
    </main>

    <script>
        let db = [], sales = [], cart = [];

        // UNIVERSAL MEMORY ENGINE
        function getMem(k) { try { return localStorage.getItem(k) || sessionStorage.getItem(k); } catch(e) { return null; } }
        function setMem(k, v) { try { localStorage.setItem(k, v); sessionStorage.setItem(k, v); } catch(e) { sessionStorage.setItem(k, v); } }

        function loginApp() {
            const u = document.getElementById('loginUser').value.trim();
            const p = document.getElementById('loginPass').value.trim();
            if(u === 'admin' && p === '1234') {
                const sDb = getMem('lb_v28_db');
                const sSl = getMem('lb_v28_sales');
                db = sDb ? JSON.parse(sDb) : [];
                sales = sSl ? JSON.parse(sSl) : [];
                
                document.getElementById('loginScreen').classList.add('hide');
                document.getElementById('topBar').classList.remove('hide');
                document.getElementById('mainContent').classList.remove('hide');
                navView('pos'); refreshAll();
            } else alert("Access Denied");
        }

        function navView(id) {
            document.querySelectorAll('.view-section').forEach(v => v.classList.add('hide'));
            document.querySelectorAll('nav button').forEach(b => b.classList.remove('border-amber-400', 'text-slate-900'));
            document.getElementById(`view-${id}`).classList.remove('hide');
            document.getElementById(`nav-${id}`).classList.add('border-amber-400', 'text-slate-900');
            document.getElementById('posBasket').classList.toggle('hide', id !== 'pos');
        }

        function saveProduct() {
            const name = document.getElementById('pName').value.trim();
            const price = parseFloat(document.getElementById('pPrice').value);
            const qty = parseInt(document.getElementById('pQty').value);
            const idx = parseInt(document.getElementById('editIndex').value);
            if(!name || isNaN(price)) return;
            if(idx >= 0) db[idx] = { name, price, qty };
            else db.unshift({ name, price, qty });
            saveData(); cancelEdit(); refreshAll();
        }

        function cancelEdit() {
            document.getElementById('pName').value = ''; document.getElementById('pPrice').value = '';
            document.getElementById('pQty').value = ''; document.getElementById('editIndex').value = '-1';
            document.getElementById('formTitle').innerText = "Product Setup";
            document.getElementById('btnCancel').classList.add('hide');
        }

        function editItem(i) {
            document.getElementById('pName').value = db[i].name; document.getElementById('pPrice').value = db[i].price;
            document.getElementById('pQty').value = db[i].qty; document.getElementById('editIndex').value = i;
            document.getElementById('formTitle').innerText = "Update Item";
            document.getElementById('btnCancel').classList.remove('hide');
        }

        function deleteItem(i) { if(confirm("Delete?")) { db.splice(i,1); saveData(); refreshAll(); } }

        function renderInventory() {
            document.getElementById('invList').innerHTML = db.map((item, i) => `
                <tr class="hover:bg-slate-50">
                    <td class="p-6 font-bold">${item.name}</td>
                    <td class="p-6 font-black text-amber-600">K ${item.price.toFixed(2)}</td>
                    <td class="p-6"><span class="px-3 py-1 rounded-lg bg-slate-100 font-black text-xs">${item.qty} UNITS</span></td>
                    <td class="p-6 text-right">
                        <button onclick="editItem(${i})" class="text-blue-600 font-black mr-4">EDIT</button>
                        <button onclick="deleteItem(${i})" class="text-red-400 font-black">DEL</button>
                    </td>
                </tr>
            `).join('');
        }

        function renderPOS() {
            const q = document.getElementById('posSearch').value.toLowerCase();
            document.getElementById('posGrid').innerHTML = db.map((item, i) => {
                if(q && !item.name.toLowerCase().includes(q) && !item.price.toString().includes(q)) return '';
                const disabled = item.qty <= 0;
                return `
                <div onclick="${!disabled ? `addToCart(${i})` : ''}" class="bg-white p-5 rounded-2xl border hover:border-amber-400 cursor-pointer transition-all shadow-sm flex flex-col justify-between h-40 ${disabled ? 'opacity-30 grayscale' : ''} ${item.qty <= 5 && !disabled ? 'low-stock' : ''}">
                    <div class="font-black text-slate-900 uppercase text-lg leading-tight tracking-tighter">${item.name}</div>
                    <div class="flex justify-between items-end">
                        <span class="text-[10px] font-black ${item.qty <= 5 ? 'text-red-500' : 'text-slate-400'}">${item.qty} LEFT</span>
                        <span class="text-2xl font-black text-slate-950">K${item.price.toFixed(2)}</span>
                    </div>
                </div>`;
            }).join('');
        }

        function addToCart(i) {
            const existing = cart.find(c => c.index === i);
            if(existing) { if(existing.qty >= db[i].qty) return; existing.qty++; }
            else cart.push({ index: i, name: db[i].name, price: db[i].price, qty: 1 });
            renderCart();
        }

        function renderCart() {
            let total = 0;
            document.getElementById('cartList').innerHTML = cart.map((c, i) => {
                total += (c.price * c.qty);
                return `<div class="bg-slate-50 p-4 rounded-2xl flex justify-between items-center border">
                    <div class="min-w-0 flex-1">
                        <div class="font-black text-xs truncate uppercase">${c.name}</div>
                        <div class="text-xs font-bold text-amber-600">K${c.price.toFixed(2)}</div>
                    </div>
                    <div class="flex items-center gap-3 ml-4 bg-white p-1 rounded-xl shadow-sm">
                        <button onclick="updateCart(${i},-1)" class="w-8 h-8 rounded-lg font-black">-</button>
                        <span class="font-black text-sm">${c.qty}</span>
                        <button onclick="updateCart(${i},1)" class="w-8 h-8 rounded-lg font-black">+</button>
                    </div>
                </div>`;
            }).join('') || `<div class="h-full flex flex-col items-center justify-center text-slate-300 py-20 font-black uppercase text-[10px]">Empty Order</div>`;
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
            cart.forEach(c => { db[c.index].qty -= c.qty; total += (c.price * c.qty); itemsCount += c.qty; });
            sales.unshift({ id: Date.now().toString().slice(-6), date: new Date().toLocaleString(), total, items: itemsCount });
            saveData(); cart = []; refreshAll(); alert("Sale Complete!");
        }

        function renderDashboard() {
            const rev = sales.reduce((a,b) => a + b.total, 0);
            document.getElementById('dashRev').innerText = `K ${rev.toFixed(2)}`;
            document.getElementById('dashSold').innerText = sales.reduce((a,b) => a + b.items, 0);
            document.getElementById('dashItems').innerText = db.length;
            document.getElementById('txHistory').innerHTML = sales.map(s => `
                <tr class="text-sm"><td class="p-6 font-mono text-slate-400">#${s.id}</td><td class="p-6 font-bold">${s.date}</td><td class="p-6 font-black uppercase">${s.items} UNIT(S)</td><td class="p-6 font-black text-lg text-amber-600">K ${s.total.toFixed(2)}</td></tr>
            `).join('');
        }

        function saveData() { setMem('lb_v28_db', JSON.stringify(db)); setMem('lb_v28_sales', JSON.stringify(sales)); }
        function refreshAll() { renderInventory(); renderPOS(); renderCart(); renderDashboard(); }
    </script>
</body>
</html>
