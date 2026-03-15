<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Bee POS | Enterprise</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: { sans: ['"Plus Jakarta Sans"', 'sans-serif'] },
                    colors: { brand: '#6366f1', dark: '#0f172a' }
                }
            }
        }
    </script>
    <style>
        body { font-family: 'Plus Jakarta Sans', sans-serif; background-color: #f8fafc; }
        .hide { display: none !important; }
        /* Scrollbar styling */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 10px; }
        @media print {
            body * { visibility: hidden; }
            #print-area, #print-area * { visibility: visible; }
            #print-area { position: absolute; left: 0; top: 0; width: 100%; padding: 20px; font-family: monospace; }
        }
    </style>
</head>
<body class="text-slate-800 antialiased h-screen overflow-hidden flex">

    <div id="loginScreen" class="fixed inset-0 z-[9999] bg-slate-900 flex items-center justify-center p-4 transition-opacity duration-300">
        <div class="bg-white rounded-3xl p-8 w-full max-w-md shadow-2xl text-center">
            <div class="w-20 h-20 bg-gradient-to-br from-indigo-500 to-purple-600 rounded-2xl mx-auto flex items-center justify-center text-4xl text-white shadow-lg mb-6">🐝</div>
            <h1 class="text-3xl font-extrabold text-slate-900 mb-2">Lucky Bee</h1>
            <p class="text-slate-500 mb-8 font-medium">Enterprise POS Terminal</p>
            
            <div class="space-y-4 text-left">
                <div>
                    <label class="block text-xs font-bold text-slate-400 uppercase tracking-wide mb-1">Username</label>
                    <input id="loginUser" type="text" value="admin" class="w-full px-4 py-3 rounded-xl border border-slate-200 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 outline-none transition-all">
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-400 uppercase tracking-wide mb-1">Password</label>
                    <input id="loginPass" type="password" value="1234" class="w-full px-4 py-3 rounded-xl border border-slate-200 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 outline-none transition-all">
                </div>
                <button onclick="app.login()" class="w-full bg-gradient-to-r from-indigo-600 to-indigo-500 hover:from-indigo-500 hover:to-indigo-400 text-white font-bold py-4 rounded-xl shadow-md transition-all transform active:scale-[0.98] mt-4">
                    Unlock Register <i class="fa-solid fa-unlock ml-2"></i>
                </button>
            </div>
        </div>
    </div>

    <aside id="sidebar" class="w-64 bg-white border-r border-slate-200 flex flex-col hide transition-all duration-300 z-50">
        <div class="p-6 flex items-center gap-3">
            <div class="w-10 h-10 bg-indigo-600 rounded-xl flex items-center justify-center text-white text-xl shadow-md">🐝</div>
            <span class="text-xl font-extrabold text-slate-800 tracking-tight">BeePOS</span>
        </div>
        <nav class="flex-1 px-4 space-y-2 mt-4">
            <button onclick="app.nav('dash')" id="nav-dash" class="w-full flex items-center gap-3 px-4 py-3 rounded-xl text-slate-500 font-semibold hover:bg-slate-50 transition-colors nav-btn active:bg-indigo-50 active:text-indigo-600 bg-indigo-50 text-indigo-600">
                <i class="fa-solid fa-chart-pie w-5"></i> Dashboard
            </button>
            <button onclick="app.nav('pos')" id="nav-pos" class="w-full flex items-center gap-3 px-4 py-3 rounded-xl text-slate-500 font-semibold hover:bg-slate-50 transition-colors nav-btn">
                <i class="fa-solid fa-cash-register w-5"></i> Terminal
            </button>
            <button onclick="app.nav('inv')" id="nav-inv" class="w-full flex items-center gap-3 px-4 py-3 rounded-xl text-slate-500 font-semibold hover:bg-slate-50 transition-colors nav-btn">
                <i class="fa-solid fa-boxes-stacked w-5"></i> Inventory
            </button>
        </nav>
        <div class="p-4 border-t border-slate-100">
            <button onclick="location.reload()" class="w-full flex items-center gap-3 px-4 py-3 rounded-xl text-red-500 font-semibold hover:bg-red-50 transition-colors">
                <i class="fa-solid fa-right-from-bracket w-5"></i> Lock Screen
            </button>
        </div>
    </aside>

    <main id="mainContent" class="flex-1 h-screen overflow-y-auto bg-slate-50 hide">
        
        <div id="view-dash" class="p-8 view-section">
            <h1 class="text-3xl font-extrabold text-slate-800 mb-8">Business Overview</h1>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
                <div class="bg-white p-6 rounded-2xl border border-slate-200 shadow-sm">
                    <div class="text-slate-400 font-bold text-xs uppercase tracking-wider mb-2 flex items-center gap-2"><i class="fa-solid fa-money-bill-wave text-emerald-500"></i> Total Revenue</div>
                    <div class="text-4xl font-extrabold text-slate-800" id="dashRev">K 0.00</div>
                </div>
                <div class="bg-white p-6 rounded-2xl border border-slate-200 shadow-sm">
                    <div class="text-slate-400 font-bold text-xs uppercase tracking-wider mb-2 flex items-center gap-2"><i class="fa-solid fa-bag-shopping text-indigo-500"></i> Items Sold</div>
                    <div class="text-4xl font-extrabold text-slate-800" id="dashSold">0</div>
                </div>
                <div class="bg-white p-6 rounded-2xl border border-slate-200 shadow-sm">
                    <div class="text-slate-400 font-bold text-xs uppercase tracking-wider mb-2 flex items-center gap-2"><i class="fa-solid fa-box text-orange-500"></i> Unique Items in Stock</div>
                    <div class="text-4xl font-extrabold text-slate-800" id="dashItems">0</div>
                </div>
            </div>
            
            <h2 class="text-xl font-bold text-slate-800 mb-4">Recent Transactions</h2>
            <div class="bg-white rounded-2xl border border-slate-200 shadow-sm overflow-hidden">
                <table class="w-full text-left border-collapse">
                    <thead>
                        <tr class="bg-slate-50 text-slate-500 text-xs uppercase tracking-wider">
                            <th class="p-4 font-bold border-b border-slate-200">Receipt ID</th>
                            <th class="p-4 font-bold border-b border-slate-200">Time</th>
                            <th class="p-4 font-bold border-b border-slate-200">Items</th>
                            <th class="p-4 font-bold border-b border-slate-200">Total (K)</th>
                        </tr>
                    </thead>
                    <tbody id="txHistory"></tbody>
                </table>
            </div>
        </div>

        <div id="view-pos" class="h-full flex flex-col md:flex-row hide view-section">
            <div class="flex-1 p-6 flex flex-col h-full overflow-hidden">
                <div class="relative mb-6">
                    <i class="fa-solid fa-magnifying-glass absolute left-4 top-4 text-slate-400"></i>
                    <input id="posSearch" type="text" placeholder="Search by name or barcode..." onkeyup="app.renderPOS()" class="w-full pl-12 pr-4 py-3 rounded-xl border border-slate-200 shadow-sm focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 outline-none text-lg">
                </div>
                <div id="posGrid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 overflow-y-auto pb-20 pr-2">
                    </div>
            </div>
            
            <div class="w-full md:w-[400px] bg-white border-l border-slate-200 flex flex-col h-full shadow-xl z-10">
                <div class="p-6 border-b border-slate-200 bg-slate-50 flex justify-between items-center">
                    <h2 class="text-xl font-extrabold text-slate-800"><i class="fa-solid fa-cart-shopping mr-2 text-indigo-500"></i> Current Order</h2>
                    <button onclick="app.clearCart()" class="text-sm text-red-500 font-bold hover:bg-red-50 px-3 py-1 rounded-lg transition"><i class="fa-solid fa-trash"></i> Clear</button>
                </div>
                
                <div id="cartList" class="flex-1 overflow-y-auto p-4 space-y-3">
                    </div>

                <div class="p-6 border-t border-slate-200 bg-slate-50">
                    <div class="flex justify-between items-center mb-4 text-slate-500 font-semibold">
                        <span>Subtotal</span><span id="cartSub">K 0.00</span>
                    </div>
                    <div class="flex justify-between items-center mb-6 text-2xl font-extrabold text-slate-900">
                        <span>Total</span><span id="cartTotal" class="text-indigo-600">K 0.00</span>
                    </div>
                    <button onclick="app.checkout()" class="w-full bg-emerald-500 hover:bg-emerald-600 text-white text-lg font-bold py-4 rounded-xl shadow-lg transition-transform transform active:scale-95 flex items-center justify-center gap-2">
                        <i class="fa-solid fa-check-circle"></i> Charge Order
                    </button>
                </div>
            </div>
        </div>

        <div id="view-inv" class="p-8 view-section hide">
            <div class="flex justify-between items-end mb-8">
                <div>
                    <h1 class="text-3xl font-extrabold text-slate-800 mb-2">Stock Management</h1>
                    <p class="text-slate-500 font-medium">Add, edit, and track your products.</p>
                </div>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <div class="bg-white p-6 rounded-2xl border border-slate-200 shadow-sm h-fit sticky top-8">
                    <h3 class="text-lg font-bold text-slate-800 mb-6 border-b pb-4" id="formTitle"><i class="fa-solid fa-plus-circle text-indigo-500 mr-2"></i>Add New Product</h3>
                    <input type="hidden" id="editIndex" value="-1">
                    
                    <div class="space-y-4">
                        <div>
                            <label class="block text-xs font-bold text-slate-500 uppercase mb-1">Product Name *</label>
                            <input id="pName" type="text" placeholder="e.g. 500ml Fanta" class="w-full px-4 py-2 rounded-lg border border-slate-300 focus:border-indigo-500 outline-none">
                        </div>
                        <div class="grid grid-cols-2 gap-4">
                            <div>
                                <label class="block text-xs font-bold text-slate-500 uppercase mb-1">Price (K) *</label>
                                <input id="pPrice" type="number" placeholder="0.00" class="w-full px-4 py-2 rounded-lg border border-slate-300 focus:border-indigo-500 outline-none">
                            </div>
                            <div>
                                <label class="block text-xs font-bold text-slate-500 uppercase mb-1">Stock Qty *</label>
                                <input id="pQty" type="number" placeholder="0" class="w-full px-4 py-2 rounded-lg border border-slate-300 focus:border-indigo-500 outline-none">
                            </div>
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-slate-500 uppercase mb-1">Barcode / SKU (Optional)</label>
                            <input id="pBar" type="text" placeholder="Scan barcode..." class="w-full px-4 py-2 rounded-lg border border-slate-300 focus:border-indigo-500 outline-none">
                        </div>
                        
                        <div class="flex gap-2 pt-2">
                            <button onclick="app.saveProduct()" class="flex-1 bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-3 rounded-lg transition"><i class="fa-solid fa-floppy-disk mr-2"></i> Save Item</button>
                            <button onclick="app.cancelEdit()" id="btnCancel" class="hide bg-slate-200 hover:bg-slate-300 text-slate-700 font-bold py-3 px-4 rounded-lg transition"><i class="fa-solid fa-xmark"></i></button>
                        </div>
                    </div>
                </div>

                <div class="lg:col-span-2 bg-white rounded-2xl border border-slate-200 shadow-sm overflow-hidden">
                    <div class="p-4 border-b border-slate-200 bg-slate-50 flex justify-between items-center">
                        <div class="relative w-full max-w-sm">
                            <i class="fa-solid fa-search absolute left-3 top-3 text-slate-400"></i>
                            <input id="invSearch" type="text" placeholder="Search inventory..." onkeyup="app.renderInventory()" class="w-full pl-10 pr-4 py-2 rounded-lg border border-slate-300 focus:border-indigo-500 outline-none text-sm">
                        </div>
                    </div>
                    <div class="overflow-x-auto max-h-[600px] overflow-y-auto">
                        <table class="w-full text-left border-collapse">
                            <thead class="sticky top-0 bg-white shadow-sm z-10">
                                <tr class="text-slate-500 text-xs uppercase tracking-wider">
                                    <th class="p-4 font-bold border-b border-slate-200">Product Info</th>
                                    <th class="p-4 font-bold border-b border-slate-200">Price</th>
                                    <th class="p-4 font-bold border-b border-slate-200">Stock</th>
                                    <th class="p-4 font-bold border-b border-slate-200 text-right">Actions</th>
                                </tr>
                            </thead>
                            <tbody id="invList" class="divide-y divide-slate-100"></tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <div id="print-area" class="hide text-black bg-white"></div>

    <script>
        // CORE APPLICATION LOGIC
        const app = {
            db: JSON.parse(localStorage.getItem('lb_v22_db')) || [],
            sales: JSON.parse(localStorage.getItem('lb_v22_sales')) || [],
            cart: [],

            // 1. AUTH & NAVIGATION
            login() {
                // Ensure UI un-hides perfectly
                document.getElementById('loginScreen').style.opacity = '0';
                setTimeout(() => {
                    document.getElementById('loginScreen').classList.add('hide');
                    document.getElementById('sidebar').classList.remove('hide');
                    document.getElementById('mainContent').classList.remove('hide');
                    this.refreshAll();
                }, 300);
            },

            nav(viewId) {
                document.querySelectorAll('.view-section').forEach(el => el.classList.add('hide'));
                document.querySelectorAll('.nav-btn').forEach(el => {
                    el.classList.remove('bg-indigo-50', 'text-indigo-600');
                    el.classList.add('text-slate-500');
                });
                
                document.getElementById(`view-${viewId}`).classList.remove('hide');
                const btn = document.getElementById(`nav-${viewId}`);
                btn.classList.remove('text-slate-500');
                btn.classList.add('bg-indigo-50', 'text-indigo-600');
                
                if(viewId === 'pos') document.getElementById('posSearch').focus();
            },

            // 2. INVENTORY MANAGEMENT
            saveProduct() {
                const name = document.getElementById('pName').value.trim();
                const price = parseFloat(document.getElementById('pPrice').value) || 0;
                const qty = parseInt(document.getElementById('pQty').value) || 0;
                const barcode = document.getElementById('pBar').value.trim();
                const editIdx = parseInt(document.getElementById('editIndex').value);

                if(!name || price <= 0) return alert("Product Name and valid Price are required.");

                const item = { name, price, qty, barcode };

                if(editIdx >= 0) {
                    this.db[editIdx] = item; // Update existing
                } else {
                    this.db.unshift(item); // Add new
                }

                this.saveData();
                this.cancelEdit();
                this.refreshAll();
            },

            editProduct(index) {
                const item = this.db[index];
                document.getElementById('pName').value = item.name;
                document.getElementById('pPrice').value = item.price;
                document.getElementById('pQty').value = item.qty;
                document.getElementById('pBar').value = item.barcode || '';
                document.getElementById('editIndex').value = index;
                
                document.getElementById('formTitle').innerHTML = `<i class="fa-solid fa-pen text-orange-500 mr-2"></i>Edit Product`;
                document.getElementById('btnCancel').classList.remove('hide');
            },

            cancelEdit() {
                document.getElementById('pName').value = '';
                document.getElementById('pPrice').value = '';
                document.getElementById('pQty').value = '';
                document.getElementById('pBar').value = '';
                document.getElementById('editIndex').value = '-1';
                document.getElementById('formTitle').innerHTML = `<i class="fa-solid fa-plus-circle text-indigo-500 mr-2"></i>Add New Product`;
                document.getElementById('btnCancel').classList.add('hide');
            },

            deleteProduct(index) {
                if(confirm(`Are you sure you want to delete ${this.db[index].name}?`)) {
                    this.db.splice(index, 1);
                    this.saveData();
                    this.refreshAll();
                }
            },

            renderInventory() {
                const q = document.getElementById('invSearch').value.toLowerCase();
                const tbody = document.getElementById('invList');
                
                const html = this.db.map((item, i) => {
                    if(q && !item.name.toLowerCase().includes(q) && !(item.barcode||'').includes(q)) return '';
                    
                    const stockClass = item.qty <= 5 ? 'bg-red-100 text-red-700' : 'bg-emerald-100 text-emerald-700';
                    return `
                        <tr class="hover:bg-slate-50 transition">
                            <td class="p-4">
                                <div class="font-bold text-slate-800">${item.name}</div>
                                <div class="text-xs text-slate-400 font-mono">${item.barcode || 'No Barcode'}</div>
                            </td>
                            <td class="p-4 font-bold text-indigo-600">K ${item.price.toFixed(2)}</td>
                            <td class="p-4"><span class="px-3 py-1 rounded-full text-xs font-bold ${stockClass}">${item.qty}</span></td>
                            <td class="p-4 text-right space-
