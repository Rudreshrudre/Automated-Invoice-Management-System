<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Invoice Management System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        header {
            background-color: #333;
            color: white;
            padding: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        nav ul {
            list-style: none;
            margin: 0;
            padding: 0;
            display: flex;
        }

        nav ul li {
            margin-left: 20px;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
        }

        main {
            padding: 20px;
        }

        .screen {
            display: none;
        }

        .screen.active {
            display: block;
        }

        #upload-area {
            border: 2px dashed #ccc;
            padding: 20px;
            text-align: center;
            cursor: pointer;
        }

        #upload-area p {
            margin: 0;
            color: #777;
        }

        #upload-status {
            margin-top: 10px;
        }

        .filters {
            margin-bottom: 20px;
        }

        .filters select, .filters input {
            margin-right: 10px;
        }

        .summary-cards {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
        }

        .card {
            background-color: #f5f5f5;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            flex: 1;
            text-align: center;
        }

        .card:not(:last-child) {
            margin-right: 10px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }

        table th, table td {
            border: 1px solid #ccc;
            padding: 10px;
            text-align: left;
        }

        table th {
            background-color: #f5f5f5;
        }

        #invoice-summary p {
            margin: 0 0 10px 0;
        }

        #extracted-data label {
            display: block;
            margin-top: 10px;
        }

        #extracted-data input {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
        }

        #actions button {
            margin-right: 10px;
            padding: 10px 20px;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        #actions button:hover {
            background-color: #0056b3;
        }

        footer {
            background-color: #333;
            color: white;
            padding: 10px;
            text-align: center;
            position: fixed;
            width: 100%;
            bottom: 0;
        }
    </style>
</head>
<body>
<header>
    <h1>Invoice Management System</h1>
    <nav>
        <ul>
            <li><a href="#login">Login</a></li>
            <li><a href="#upload">Upload</a></li>
            <li><a href="#dashboard">Dashboard</a></li>
            <li><a href="#settings">Settings</a></li>
            <li><a href="#logout">Logout</a></li>
        </ul>
    </nav>
</header>

<main>
    <!-- Login Screen -->
    <section id="login" class="screen active">
        <h2>Login</h2>
        <form id="login-form">
            <label for="username">Username:</label>
            <input type="text" id="username" name="username" required>
            <label for="password">Password:</label>
            <input type="password" id="password" name="password" required>
            <button type="submit">Login</button>
        </form>
        <p id="login-error" style="color: red; display: none;">Incorrect username or password.</p>
    </section>

    <!-- Upload Screen -->
    <section id="upload" class="screen">
        <h2>Upload Invoice</h2>
        <div id="upload-area">
            <p>Drag and drop files here or click to upload</p>
            <input type="file" id="file-input" multiple>
        </div>
        <div id="upload-status"></div>
    </section>

    <!-- Dashboard Screen -->
    <section id="dashboard" class="screen">
        <h2>Dashboard</h2>
        <div class="filters">
            <select id="status-filter">
                <option value="all">All</option>
                <option value="pending">Pending</option>
                <option value="paid">Paid</option>
                <option value="overdue">Overdue</option>
            </select>
            <input type="date" id="date-filter">
        </div>
        <div class="summary-cards">
            <div class="card" id="total-invoices">Total Invoices: 0</div>
            <div class="card" id="pending-invoices">Pending: 0</div>
            <div class="card" id="paid-invoices">Paid: 0</div>
            <div class="card" id="overdue-invoices">Overdue: 0</div>
        </div>
        <table>
            <thead>
            <tr>
                <th>Invoice Number</th>
                <th>Vendor</th>
                <th>Amount</th>
                <th>Due Date</th>
                <th>Status</th>
            </tr>
            </thead>
            <tbody id="invoice-list">
            </tbody>
        </table>
    </section>

    <!-- Settings Screen -->
    <section id="settings" class="screen">
        <h2>Settings</h2>
        <div id="settings-content">
            <h3>User Settings</h3>
            <table id="user-table">
                <thead>
                <tr>
                    <th>Username</th>
                    <th>Password</th>
                </tr>
                </thead>
                <tbody>
                <tr>
                    <td>admin</td>
                    <td>password</td>
                </tr>
                </tbody>
            </table>
        </div>
    </section>

    <!-- Invoice Detail Screen -->
    <section id="invoice-detail" class="screen">
        <h2>Invoice Detail</h2>
        <div id="invoice-summary">
            <p>Invoice Number: <span id="detail-invoice-number"></span></p>
            <p>Vendor: <span id="detail-vendor"></span></p>
            <p>Invoice Date: <span id="detail-invoice-date"></span></p>
            <p>Due Date: <span id="detail-due-date"></span></p>
            <p>Amount: <span id="detail-amount"></span></p>
            <p>Status: <span id="detail-status"></span></p>
        </div>
        <div id="extracted-data">
            <label for="edit-invoice-number">Invoice Number</label>
            <input type="text" id="edit-invoice-number">
            <label for="edit-amount">Amount</label>
            <input type="text" id="edit-amount">
            <label for="edit-due-date">Due Date</label>
            <input type="date" id="edit-due-date">
            <button id="save-changes">Save Changes</button>
        </div>
        <div id="actions">
            <button id="mark-paid">Mark as Paid</button>
            <button id="send-reminder">Send Reminder</button>
            <button id="delete-invoice">Delete Invoice</button>
        </div>
    </section>
</main>

<footer>
    <p>Contact Info | Help/Support</p>
</footer>

<script>
    document.addEventListener('DOMContentLoaded', () => {
        const screens = document.querySelectorAll('.screen');
        const uploadArea = document.getElementById('upload-area');
        const fileInput = document.getElementById('file-input');
        const uploadStatus = document.getElementById('upload-status');
        const invoiceList = document.getElementById('invoice-list');
        const totalInvoices = document.getElementById('total-invoices');
        const pendingInvoices = document.getElementById('pending-invoices');
        const paidInvoices = document.getElementById('paid-invoices');
        const overdueInvoices = document.getElementById('overdue-invoices');
        const settingsContent = document.getElementById('settings-content');
        const loginForm = document.getElementById('login-form');
        const loginError = document.getElementById('login-error');
        const userTable = document.getElementById('user-table');

        let invoices = [];
        let isLoggedIn = false;

        function showScreen(id) {
            screens.forEach(screen => {
                screen.classList.remove('active');
            });
            document.getElementById(id).classList.add('active');

            if (id === 'dashboard' || id === 'upload' || id === 'settings') {
                if (!isLoggedIn) {
                    showScreen('login');
                }
            }
        }

        document.querySelectorAll('nav ul li a').forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const targetId = link.getAttribute('href').substring(1);
                if (targetId === 'logout') {
                    isLoggedIn = false;
                    showScreen('login');
                } else {
                    showScreen(targetId);
                }
            });
        });

        loginForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const username = loginForm.username.value;
            const password = loginForm.password.value;

            // Example simple authentication logic
            if (checkCredentials(username, password)) {
                isLoggedIn = true;
                loginError.style.display = 'none';
                showScreen('upload'); // Redirect to upload screen after successful login
            } else {
                loginError.style.display = 'block';
            }
        });

        function checkCredentials(username, password) {
            // Hardcoded credentials (for demonstration purposes)
            const users = [
                { username: 'admin', password: 'password' },
                { username: 'user1', password: 'user1pass' },
                { username: 'user2', password: 'user2pass' }
            ];

            return users.some(user => user.username === username && user.password === password);
        }

        uploadArea.addEventListener('click', () => fileInput.click());

        fileInput.addEventListener('change', (e) => {
            if (isLoggedIn) {
                handleFiles(e.target.files);
            }
        });

        uploadArea.addEventListener('dragover', (e) => {
            e.preventDefault();
            uploadArea.classList.add('dragover');
        });

        uploadArea.addEventListener('dragleave', () => {
            uploadArea.classList.remove('dragover');
        });

        uploadArea.addEventListener('drop', (e) => {
            e.preventDefault();
            uploadArea.classList.remove('dragover');
            if (isLoggedIn) {
                handleFiles(e.dataTransfer.files);
            }
        });

        function handleFiles(files) {
            Array.from(files).forEach(file => {
                const reader = new FileReader();
                reader.onload = (e) => {
                    const invoiceData = parseInvoice(e.target.result);
                    invoices.push(invoiceData);
                    updateDashboard();
                    uploadStatus.innerHTML += `<p>Uploaded: ${file.name}</p>`;
                };
                reader.readAsText(file);
            });
        }

        function parseInvoice(data) {
            // Simulate invoice data extraction
            return {
                number: 'INV-' + Math.floor(Math.random() * 10000),
                vendor: 'Vendor ' + Math.floor(Math.random() * 100),
                amount: '$' + (Math.random() * 1000).toFixed(2),
                dueDate: new Date(Date.now() + Math.random() * 10000000000).toISOString().split('T')[0],
                status: ['pending', 'paid', 'overdue'][Math.floor(Math.random() * 3)]
            };
        }

        function updateDashboard() {
            invoiceList.innerHTML = '';
            invoices.forEach(invoice => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${invoice.number}</td>
                    <td>${invoice.vendor}</td>
                    <td>${invoice.amount}</td>
                    <td>${invoice.dueDate}</td>
                    <td>${invoice.status}</td>
                `;
                invoiceList.appendChild(row);
            });
            totalInvoices.textContent = `Total Invoices: ${invoices.length}`;
            pendingInvoices.textContent = `Pending: ${invoices.filter(i => i.status === 'pending').length}`;
            paidInvoices.textContent = `Paid: ${invoices.filter(i => i.status === 'paid').length}`;
            overdueInvoices.textContent = `Overdue: ${invoices.filter(i => i.status === 'overdue').length}`;
        }

        showScreen('login'); // Initially show login screen
    });
</script>
</body>
</html>
