<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lucky Bee POS | Fixed</title>
    <style>
        :root { --brand: #6366f1; --bg: #f1f5f9; --text: #1e293b; --border: #cbd5e1; }
        * { box-sizing: border-box; font-family: sans-serif; margin: 0; padding: 0; }
        body { background: var(--bg); color: var(--text); padding: 20px; }

        /* --- THE LOGIN BOX (Always visible first) --- */
        #loginOverlay {
            position: fixed; inset: 0; background: #6366f1; z-index: 99999;
            display: flex; align-items: center; justify-content: center;
        }
        .login-card {
            background: white; padding: 40px; border-radius: 15px;
            width: 320px; text-align: center; box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        /* --- LAYOUT --- */
        #app { display: none; } /* Hidden until login */
        .container { max-width: 1000px; margin: 0 auto; display: grid; grid-template-columns: 350px 1fr; gap: 20px; }
        
        /* --- UI COMPONENTS --- */
        .card { background: white; padding: 20px; border-radius: 10px; border: 1px solid var(--border); margin-bottom: 20px; }
        input { width: 100%; padding: 12px; margin: 10px 0; border: 1px solid var(--border); border-radius: 5px; font-size: 16px; }
        button { width: 100%; padding: 12px; background: var(--brand); color: white; border: none; border-radius: 5px; font-weight: bold; cursor: pointer; }
        
        /* --- INVENTORY LIST --- */
        .inv-item { display: flex; justify-content: space-between; padding: 10px; border-bottom: 1px solid #eee; }
        .inv-item:last-child { border: none; }
        .badge { background: #fee2e2; color: #ef4444; padding: 2px 8px; border-radius: 10px; font-size: 12px; }
    </style>
</head>
<body>

<div id="loginOverlay">
    <div class="login-card">
        <h1 style="margin-bottom: 10px;">🐝</h1>
        <h2>BeePOS Login</h2>
        <input id="user" type="text" placeholder="Username" value="admin">
        <input id="pass" type="password" placeholder="Password" value="1234">
        <button onclick="unlock()">Enter Shop</button>
    </div>
</div>

<div id="app">
    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px;">
        <h1>Lucky Bee Inventory 🐝</h1>
        <button onclick="location.reload()" style="width: auto; background: #64748b;">Logout</button>
    </div>

    <div class="container">
        <div class="card">
            <h3>Add New Product</h3>
            <input id="pName" placeholder="Product Name">
            <input id="pPrice" type="number" placeholder="Price (K)">
            <input id="pQty" type="number" placeholder="Quantity">
            <button onclick="addItem()" style="background: #10b981;">Save to Stock</button>
        </div>

        <div class="card" style="padding: 0;">
            <div style="padding: 20px; border-bottom: 1px solid var(--border); background: #f8fafc; border-radius: 10px 10px 0 0;">
                <h3 id="totalTitle">Stock Items (0)</h3>
            </div>
            <div id="itemList" style="max-height: 500px; overflow-y: auto;">
                <div style="padding: 20px; text-align: center; color: #94a3b8;">No items yet. Add one on the left.</div>
            </div>
        </div>
    </div>
</div>

<script>
    // Load data from phone/PC memory
    let db = JSON.parse(localStorage.getItem('lucky_v18')) || [];

    function unlock() {
        // Simple login check
        if(document.getElementById('user').value === 'admin') {
            document.getElementById('loginOverlay').style.display = 'none';
            document.getElementById('app').style.display = 'block';
            render();
        } else {
            alert("Wrong credentials");
        }
    }

    function addItem() {
        const n = document.getElementById('pName').value;
        const p = document.getElementById('pPrice').value;
        const q = document.getElementById('pQty').value;

        if(!n || !p) return alert("Fill in name and price");

        // Add to data
        db.unshift({ name: n, price: p, qty: q });
        localStorage.setItem('lucky_v18', JSON.stringify(db));

        // Clear inputs
        document.getElementById('pName').value = '';
        document.getElementById('pPrice').value = '';
        document.getElementById('pQty').value = '';

        render();
    }

    function render() {
        const list = document.getElementById('itemList');
        document.getElementById('totalTitle').innerText = `Stock Items (${db.length})`;
        
        if(db.length === 0) {
            list.innerHTML = `<div style="padding:20px; text-align:center;">Empty list</div>`;
            return;
        }

        list.innerHTML = db.map((item, i) => `
            <div class="inv-item">
                <div>
                    <strong>${item.name}</strong><br>
                    <span style="color: #6366f1; font-weight: bold;">K${item.price}</span>
                </div>
                <div style="text-align: right;">
                    <span class="badge">Stock: ${item.qty}</span><br>
                    <small onclick="del(${i})" style="color:red; cursor:pointer;">Delete</small>
                </div>
            </div>
        `).join('');
    }

    function del(i) {
        if(confirm("Delete?")) {
            db.splice(i, 1);
            localStorage.setItem('lucky_v18', JSON.stringify(db));
            render();
        }
    }
</script>

</body>
</html>
