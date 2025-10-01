<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Cửa Hàng Điện Nước Văn Tự</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background: #f5f6fa;
            margin: 0;
        }
        .topbar {
            background: #3182ce;
            color: #fff;
            padding: 0 24px;
            height: 56px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 2px 8px rgba(0,0,0,0.07);
        }
        .topbar .logo {
            font-size: 1.7rem;
            font-weight: bold;
            letter-spacing: 1px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .topbar .search-bar {
            flex: 1;
            margin: 0 32px;
            display: flex;
            align-items: center;
            max-width: 400px;
        }
        .topbar input[type="text"] {
            width: 100%;
            padding: 8px 12px;
            border-radius: 6px 0 0 6px;
            border: none;
            font-size: 1rem;
        }
        .topbar button {
            background: #225ea8;
            color: #fff;
            border: none;
            padding: 8px 16px;
            border-radius: 0 6px 6px 0;
            cursor: pointer;
            font-weight: 600;
        }
        .topbar .user {
            display: flex;
            align-items: center;
            gap: 16px;
        }
        .avatar {
            width: 36px;
            height: 36px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid #fff;
            background: #eee;
        }
        .username {
            font-weight: 600;
            font-size: 1.1rem;
            letter-spacing: 0.5px;
        }
        .logout-btn {
            background: #fff;
            color: #3182ce;
            border: none;
            padding: 6px 18px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.2s;
            font-size: 1rem;
        }
        .logout-btn:hover {
            background: #e6f0ff;
        }
        .sidebar {
            position: fixed;
            top: 56px;
            left: 0;
            width: 220px;
            height: calc(100vh - 56px);
            background: #fff;
            box-shadow: 2px 0 8px rgba(0,0,0,0.07);
            z-index: 10;
            display: flex;
            flex-direction: column;
            gap: 0;
            padding-top: 0;
        }
        .sidebar-section {
            padding: 24px 16px 0 16px;
        }
        .sidebar-section h3 {
            color: #3182ce;
            font-size: 1.1rem;
            margin-bottom: 12px;
            font-weight: 700;
        }
        .sidebar-section label {
            display: block;
            margin-bottom: 8px;
            font-size: 1rem;
            color: #225ea8;
            cursor: pointer;
        }
        .sidebar-section input[type="checkbox"] {
            margin-right: 8px;
        }
        .sidebar-section .filter-group {
            margin-bottom: 18px;
        }
        .sidebar-btns {
            display: flex;
            flex-direction: column;
            gap: 18px;
            margin-top: 32px;
            align-items: flex-start;
        }
        .sidebar-btn {
            width: 180px;
            height: 48px;
            border-radius: 12px;
            background: #e6f0ff;
            display: flex;
            align-items: center;
            gap: 12px;
            cursor: pointer;
            position: relative;
            transition: background 0.2s, box-shadow 0.2s;
            padding: 0 18px;
            font-weight: 600;
            color: #3182ce;
            font-size: 1rem;
            box-shadow: 0 2px 8px rgba(49,130,206,0.04);
        }
        .sidebar-btn.active, .sidebar-btn:hover {
            background: #3182ce;
            color: #fff;
            box-shadow: 0 4px 16px rgba(49,130,206,0.12);
        }
        .sidebar-btn svg {
            flex-shrink: 0;
            transition: filter 0.2s;
        }
        .sidebar-btn.active svg, .sidebar-btn:hover svg {
            filter: brightness(0) invert(1);
        }
        .sidebar-btn .notify {
            position: absolute;
            top: 8px;
            right: 18px;
            background: #e53935;
            color: #fff;
            border-radius: 50%;
            padding: 2px 7px;
            font-size: 13px;
            font-weight: bold;
            border: 2px solid #fff;
            min-width: 24px;
            text-align: center;
        }
        .main-content {
            margin-left: 220px;
            margin-top: 56px;
            padding: 32px 16px;
            max-width: 1100px;
        }
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 24px;
        }
        .product-card {
            background: #fff;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.07);
            padding: 18px;
            text-align: center;
            position: relative;
            transition: box-shadow 0.2s;
        }
        .product-card:hover {
            box-shadow: 0 4px 16px rgba(49,130,206,0.15);
        }
        .product-card img {
            width: 80px;
            height: 80px;
            object-fit: contain;
            margin-bottom: 12px;
        }
        .product-card h4 {
            color: #225ea8;
            font-size: 1.1rem;
            margin: 0 0 8px 0;
            font-weight: 700;
        }
        .product-card .price {
            color: #e53935;
            font-weight: bold;
            font-size: 1.1rem;
            margin-bottom: 8px;
        }
        .product-card .desc {
            color: #444;
            font-size: 0.95rem;
            margin-bottom: 8px;
        }
        .product-card .buy-btn {
            background: #3182ce;
            color: #fff;
            border: none;
            padding: 8px 16px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            margin-top: 8px;
        }
        .product-card .buy-btn:hover {
            background: #225ea8;
        }
        .product-card .add-cart {
            position: absolute;
            top: 12px;
            right: 12px;
            background: #e6f0ff;
            border: none;
            border-radius: 50%;
            width: 32px;
            height: 32px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .product-card .add-cart:hover {
            background: #3182ce;
        }
        .cart-panel {
            position: fixed;
            top: 56px;
            right: 0;
            width: 340px;
            height: calc(100vh - 56px);
            background: #fff;
            box-shadow: -2px 0 8px rgba(0,0,0,0.07);
            z-index: 20;
            border-radius: 0 0 0 12px;
            display: none;
            flex-direction: column;
        }
        .cart-panel h3 {
            color: #3182ce;
            font-size: 1.1rem;
            margin: 24px 0 12px 24px;
            font-weight: 700;
        }
        .cart-list {
            flex: 1;
            overflow-y: auto;
            padding: 0 24px;
        }
        .cart-item {
            display: flex;
            align-items: center;
            gap: 12px;
            border-bottom: 1px solid #eee;
            padding: 12px 0;
        }
        .cart-item img {
            width: 40px;
            height: 40px;
            object-fit: contain;
            border-radius: 8px;
            background: #f5f6fa;
        }
        .cart-item .cart-title {
            flex: 1;
            font-weight: 600;
            color: #225ea8;
        }
        .cart-item .cart-price {
            color: #e53935;
            font-weight: bold;
        }
        .cart-item .cart-remove {
            background: #e53935;
            color: #fff;
            border: none;
            border-radius: 6px;
            padding: 2px 8px;
            cursor: pointer;
            font-size: 0.95rem;
        }
        .cart-panel .cart-total {
            padding: 16px 24px;
            font-weight: 700;
            color: #225ea8;
            border-top: 1px solid #eee;
        }
        .cart-panel .cart-checkout {
            background: #3182ce;
            color: #fff;
            border: none;
            padding: 12px 0;
            width: 90%;
            margin: 16px auto;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
        }
        .cart-panel .cart-checkout:hover {
            background: #225ea8;
        }
        .card {
            background: #fff;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.07);
            padding: 32px;
            margin-bottom: 32px;
        }
        .card h2 {
            margin-top: 0;
            font-size: 1.3rem;
            color: #3182ce;
            font-weight: 700;
            letter-spacing: 0.5px;
        }
        .profile-flex {
            display: flex;
            align-items: center;
            gap: 24px;
        }
        .profile-avatar {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid #3182ce;
            background: #eee;
        }
        .profile-info {
            font-size: 1.05rem;
            color: #222;
            font-weight: 500;
        }
        .profile-form label {
            font-weight: 600;
            margin-top: 12px;
            display: block;
            color: #3182ce;
        }
        .profile-form input {
            width: 100%;
            padding: 8px;
            margin-top: 4px;
            border: 1px solid #bcd0ee;
            border-radius: 6px;
            font-size: 1rem;
        }
        .profile-form button {
            background: #3182ce;
            color: #fff;
            border: none;
            padding: 8px 24px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            margin-top: 16px;
        }
        .profile-form button:hover {
            background: #225ea8;
        }
        .footer {
            text-align: center;
            padding: 24px 0;
            background: #3182ce;
            color: #fff;
            margin-top: 32px;
            font-size: 1.1rem;
            font-weight: 500;
            letter-spacing: 0.5px;
        }
        .auth-container {
            max-width: 400px;
            margin: 80px auto;
            background: #fff;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.07);
            padding: 32px;
            animation: fadeIn 0.5s;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px);}
            to { opacity: 1; transform: translateY(0);}
        }
        .auth-container h2 {
            text-align: center;
            margin-bottom: 24px;
            color: #3182ce;
            font-weight: 700;
            letter-spacing: 0.5px;
        }
        .auth-container label {
            font-weight: 600;
            margin-bottom: 4px;
            display: block;
            color: #3182ce;
        }
        .auth-container input, .auth-container select {
            width: 100%;
            padding: 10px;
            margin-bottom: 14px;
            border: 1px solid #3182ce;
            border-radius: 4px;
            box-sizing: border-box;
            font-size: 1rem;
        }
        .auth-container .btn-group {
            display: flex;
            gap: 16px;
            justify-content: center;
        }
        .auth-container button {
            background: #3182ce;
            color: #fff;
            border: none;
            padding: 10px 24px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: background 0.2s;
        }
        .auth-container button.cancel {
            background: #aaa;
        }
        .auth-container button:hover {
            background: #225ea8;
        }
        .auth-container .switch-link {
            text-align: center;
            margin-top: 12px;
        }
        .auth-container .switch-link a {
            color: #3182ce;
            text-decoration: underline;
            cursor: pointer;
            font-weight: 600;
        }
        @media (max-width: 900px) {
            .main-content { margin-left: 0; padding: 8px; max-width: 100vw;}
            .sidebar { display: none !important; }
            .topbar { flex-direction: column; height: auto; padding: 12px 8px; }
            .cart-panel { width: 100vw; right: 0; border-radius: 0;}
        }
    </style>
</head>
<body>
    <div class="topbar">
        <div class="logo">
            <svg width="32" height="32" fill="#fff" style="margin-right:4px;"><rect x="6" y="8" width="20" height="16" rx="4" fill="#fff" opacity="0.8"/><rect x="10" y="12" width="12" height="8" rx="2" fill="#3182ce"/></svg>
            Điện Nước Văn Tự
        </div>
        <div class="search-bar" id="search-bar" style="display:none;">
            <input type="text" id="searchInput" placeholder="Tìm sản phẩm...">
            <button onclick="searchProducts()">Tìm kiếm</button>
        </div>
        <div class="user" id="user-info" style="display:none;">
            <img id="avatar-header" class="avatar" src="https://cdn-icons-png.flaticon.com/512/149/149071.png" alt="Avatar">
            <span id="username-header" class="username"></span>
            <button class="logout-btn" onclick="logoutUser()">Đăng xuất</button>
        </div>
    </div>
    <!-- Đăng nhập/Đăng ký -->
    <div class="auth-container" id="loginForm">
        <h2>ĐĂNG NHẬP</h2>
        <form onsubmit="return handleLogin(event)">
            <label for="login-username">Username</label>
            <input type="text" id="login-username" required autocomplete="username">
            <label for="login-password">Mật khẩu</label>
            <input type="password" id="login-password" required autocomplete="current-password">
            <div class="btn-group">
                <button type="submit">Đăng nhập</button>
            </div>
        </form>
        <div class="switch-link">
            Chưa có tài khoản? <a onclick="showRegister()">Đăng ký ngay</a>
        </div>
    </div>
    <div class="auth-container" id="registerForm" style="display:none;">
        <h2>ĐĂNG KÝ TÀI KHOẢN</h2>
        <form onsubmit="return handleRegister(event)">
            <label for="reg-username">Nhập username</label>
            <input type="text" id="reg-username" required autocomplete="username">
            <label for="reg-password">Nhập mật khẩu</label>
            <input type="password" id="reg-password" required autocomplete="new-password">
            <label for="reg-email">Nhập địa chỉ email</label>
            <input type="email" id="reg-email" required autocomplete="email">
            <label for="reg-dob">Ngày sinh</label>
            <input type="date" id="reg-dob">
            <label for="reg-gender">Giới tính</label>
            <select id="reg-gender">
                <option value="Nam">Nam</option>
                <option value="Nữ">Nữ</option>
                <option value="Khác">Khác</option>
            </select>
            <div class="btn-group">
                <button type="button" class="cancel" onclick="showLogin()">Quay lại</button>
                <button type="submit">Đăng ký</button>
            </div>
        </form>
        <div class="switch-link">
            Đã có tài khoản? <a onclick="showLogin()">Đăng nhập</a>
        </div>
    </div>
    <!-- Sidebar menu -->
    <div id="sidebar" class="sidebar" style="display:none;">
        <div class="sidebar-section">
            <h3>Bộ lọc sản phẩm</h3>
            <div class="filter-group">
                <label><input type="checkbox" class="filter-cat" value="Vòi nước inox">Vòi nước inox</label>
                <label><input type="checkbox" class="filter-cat" value="Bóng đèn LED">Bóng đèn LED</label>
                <label><input type="checkbox" class="filter-cat" value="Ổ cắm điện">Ổ cắm điện</label>
                <label><input type="checkbox" class="filter-cat" value="Ống nước PVC">Ống nước PVC</label>
                <label><input type="checkbox" class="filter-cat" value="Dây điện">Dây điện</label>
                <label><input type="checkbox" class="filter-cat" value="Van nước">Van nước</label>
            </div>
            <div class="filter-group">
                <label for="priceMin">Giá từ</label>
                <input type="number" id="priceMin" style="width:80px;"> -
                <label for="priceMax">đến</label>
                <input type="number" id="priceMax" style="width:80px;">
                <button onclick="filterProducts()" style="margin-top:8px;background:#3182ce;color:#fff;border:none;padding:4px 12px;border-radius:6px;cursor:pointer;">Áp dụng</button>
            </div>
        </div>
        <div class="sidebar-btns">
            <div class="sidebar-btn" id="btn-products" onclick="showSection('products')" title="Sản phẩm">
                <svg width="24" height="24" fill="#3182ce"><rect x="5" y="5" width="14" height="14" rx="4" fill="#e6f0ff"/><rect x="9" y="9" width="6" height="6" rx="2" fill="#3182ce"/></svg>
                <span>Sản phẩm</span>
            </div>
            <div class="sidebar-btn" id="btn-cart" onclick="toggleCart()" title="Giỏ hàng">
                <svg width="24" height="24" fill="#3182ce"><rect x="5" y="9" width="14" height="7" rx="3" fill="#e6f0ff"/><rect x="9" y="12" width="6" height="3" rx="1.5" fill="#3182ce"/></svg>
                <span>Giỏ hàng</span>
                <span class="notify" id="cart-count" style="display:none;">0</span>
            </div>
            <div class="sidebar-btn" id="btn-notify" onclick="showSection('notify')" title="Thông báo">
                <svg width="24" height="24" fill="#3182ce"><path d="M12 2C8.13 2 5 5.13 5 9v5c0 .55-.45 1-1 1H3v2h18v-2h-1c-.55 0-1-.45-1-1V9c0-3.87-3.13-7-7-7zm0 20c1.1 0 2-.9 2-2h-4c0 1.1.9 2 2 2z"/></svg>
                <span>Thông báo</span>
                <span class="notify" id="notify-count" style="display:none;">0</span>
            </div>
            <div class="sidebar-btn" id="btn-chatbot" onclick="showSection('chatbot')" title="Chat BOT AI">
                <svg width="24" height="24" fill="#3182ce"><circle cx="12" cy="12" r="10" stroke="#3182ce" stroke-width="2" fill="#e6f0ff"/><text x="6" y="17" font-size="10" fill="#3182ce">BOT</text></svg>
                <span>Chat BOT AI</span>
            </div>
            <div class="sidebar-btn" id="btn-profile" onclick="showSection('profile')" title="Hồ sơ">
                <svg width="24" height="24" fill="#3182ce"><circle cx="12" cy="8" r="6" fill="#e6f0ff"/><rect x="6" y="16" width="12" height="4" rx="2" fill="#e6f0ff"/></svg>
                <span>Hồ sơ</span>
            </div>
        </div>
    </div>
    <!-- Giỏ hàng -->
    <div class="cart-panel" id="cart-panel">
        <h3>Giỏ hàng của bạn</h3>
        <div class="cart-list" id="cart-list"></div>
        <div class="cart-total" id="cart-total"></div>
        <button class="cart-checkout" onclick="checkoutCart()">Thanh toán</button>
    </div>
    <!-- Main content -->
    <div class="main-content" id="main-content" style="display:none;">
        <!-- Trang mua đồ -->
        <div class="card" id="products-section" style="display:none;">
            <h2>Danh mục sản phẩm</h2>
            <div class="product-grid" id="product-grid"></div>
        </div>
        <!-- Thông báo -->
        <div class="card" id="notify-section" style="display:none;">
            <h2>Thông báo</h2>
            <div id="notification-list"></div>
        </div>
        <!-- Chat với BOT AI -->
        <div class="card" id="chatbot-section" style="display:none;">
            <h2>Chat với BOT AI</h2>
            <input type="text" id="chatInput" placeholder="Nhập câu hỏi về sản phẩm..." style="width:80%;padding:8px;font-size:1rem;">
            <button type="button" onclick="chatbotReply()" style="padding:8px 16px;background:#3182ce;color:#fff;border:none;border-radius:6px;font-weight:600;">Gửi</button>
            <div id="chatReply" style="margin-top:12px;color:#3182ce;font-weight:500;"></div>
        </div>
        <!-- Hồ sơ người dùng -->
        <div class="card" id="profile-section" style="display:none;">
            <h2>Hồ sơ người dùng</h2>
            <div class="profile-flex">
                <div>
                    <img id="avatar-img" class="profile-avatar" src="https://cdn-icons-png.flaticon.com/512/149/149071.png" alt="Avatar">
                    <form onsubmit="return changeAvatar(event)" style="margin-top:8px;">
                        <input type="file" id="avatar-input" accept="image/*" style="display:none;">
                        <label for="avatar-input" style="background:#3182ce;color:#fff;padding:6px 16px;border-radius:6px;cursor:pointer;font-weight:600;">Đổi ảnh đại diện</label>
                        <button type="submit" style="display:none;">Lưu</button>
                    </form>
                </div>
                <div class="profile-info" id="profile-info"></div>
            </div>
            <form class="profile-form" onsubmit="return saveSettings(event)">
                <label for="settings-email">Email</label>
                <input type="email" id="settings-email">
                <label for="settings-password">Đổi mật khẩu</label>
                <input type="password" id="settings-password" placeholder="Nhập mật khẩu mới">
                <button type="submit">Lưu cài đặt</button>
            </form>
            <div id="settings-msg" style="color:green;margin-top:8px;"></div>
        </div>
    </div>
    <div class="footer">
        &copy; 2025 Cửa Hàng Điện Nước Văn Tự
    </div>
    <script>
        let users = [];
        let currentUser = null;
        let notifications = [
            { text: "Bạn có đơn hàng mới!", read: false },
            { text: "Khuyến mãi: Giảm giá 10% cho bóng đèn LED!", read: false },
            { text: "Tin nhắn mới từ cửa hàng.", read: false }
        ];
        // Sản phẩm mẫu
        let products = [
            { id: 1, name: "Vòi nước inox", price: 120000, img: "https://cdn-icons-png.flaticon.com/512/2933/2933811.png", desc: "Vòi nước inox bền, chống rỉ." },
            { id: 2, name: "Bóng đèn LED", price: 45000, img: "https://cdn-icons-png.flaticon.com/512/2933/2933826.png", desc: "Tiết kiệm điện, sáng mạnh." },
            { id: 3, name: "Ổ cắm điện", price: 65000, img: "https://cdn-icons-png.flaticon.com/512/2933/2933822.png", desc: "Ổ cắm đa năng, an toàn." },
            { id: 4, name: "Ống nước PVC", price: 30000, img: "https://cdn-icons-png.flaticon.com/512/2933/2933824.png", desc: "Ống nước PVC chịu lực tốt." },
            { id: 5, name: "Dây điện", price: 15000, img: "https://cdn-icons-png.flaticon.com/512/2933/2933817.png", desc: "Dây điện lõi đồng, an toàn." },
            { id: 6, name: "Van nước", price: 35000, img: "https://cdn-icons-png.flaticon.com/512/2933/2933813.png", desc: "Van nước nhựa, dễ lắp đặt." }
        ];
        let cart = [];

        function showRegister() {
            document.getElementById('loginForm').style.display = 'none';
            document.getElementById('registerForm').style.display = 'block';
        }
        function showLogin() {
            document.getElementById('registerForm').style.display = 'none';
            document.getElementById('loginForm').style.display = 'block';
        }
        function handleRegister(e) {
            e.preventDefault();
            const username = document.getElementById('reg-username').value;
            const password = document.getElementById('reg-password').value;
            const email = document.getElementById('reg-email').value;
            const dob = document.getElementById('reg-dob').value;
            const gender = document.getElementById('reg-gender').value;
            if (users.find(u => u.username === username)) {
                alert('Username đã tồn tại!');
                return false;
            }
            users.push({ username, password, email, dob, gender, avatar: "", phone: "" });
            localStorage.setItem('users', JSON.stringify(users));
            alert('Đăng ký thành công! Vui lòng đăng nhập.');
            showLogin();
            return false;
        }
        function handleLogin(e) {
            e.preventDefault();
            const username = document.getElementById('login-username').value;
            const password = document.getElementById('login-password').value;
            const user = users.find(u => u.username === username && u.password === password);
            if (!user) {
                alert('Sai username hoặc mật khẩu! Nếu chưa có tài khoản, hãy đăng ký.');
                return false;
            }
            currentUser = user;
            localStorage.setItem('currentUser', JSON.stringify(currentUser));
            localStorage.setItem('users', JSON.stringify(users));
            document.getElementById('loginForm').style.display = 'none';
            document.getElementById('registerForm').style.display = 'none';
            document.getElementById('sidebar').style.display = 'flex';
            document.getElementById('main-content').style.display = 'block';
            document.getElementById('user-info').style.display = 'flex';
            document.getElementById('search-bar').style.display = 'flex';
            document.getElementById('avatar-header').src = currentUser.avatar || "https://cdn-icons-png.flaticon.com/512/149/149071.png";
            document.getElementById('username-header').innerText = currentUser.username;
            showSection('products');
            updateNotificationCount();
            showProfile();
            renderProducts(products);
            updateCartCount();
            return false;
        }
        function logoutUser() {
            currentUser = null;
            localStorage.removeItem('currentUser');
            document.getElementById('user-info').style.display = 'none';
            document.getElementById('sidebar').style.display = 'none';
            document.getElementById('main-content').style.display = 'none';
            document.getElementById('search-bar').style.display = 'none';
            document.getElementById('cart-panel').style.display = 'none';
            showLogin();
            return false;
        }
        function showSection(section) {
            document.getElementById('products-section').style.display = 'none';
            document.getElementById('notify-section').style.display = 'none';
            document.getElementById('chatbot-section').style.display = 'none';
            document.getElementById('profile-section').style.display = 'none';
            document.getElementById('btn-products').classList.remove('active');
            document.getElementById('btn-cart').classList.remove('active');
            document.getElementById('btn-notify').classList.remove('active');
            document.getElementById('btn-chatbot').classList.remove('active');
            document.getElementById('btn-profile').classList.remove('active');
            if (section === 'products') {
                document.getElementById('products-section').style.display = 'block';
                document.getElementById('btn-products').classList.add('active');
                renderProducts(products);
            }
            if (section === 'notify') {
                document.getElementById('notify-section').style.display = 'block';
                document.getElementById('btn-notify').classList.add('active');
                renderNotifications();
            }
            if (section === 'chatbot') {
                document.getElementById('chatbot-section').style.display = 'block';
                document.getElementById('btn-chatbot').classList.add('active');
            }
            if (section === 'profile') {
                document.getElementById('profile-section').style.display = 'block';
                document.getElementById('btn-profile').classList.add('active');
                showProfile();
            }
        }
        function renderProducts(list) {
            const grid = document.getElementById('product-grid');
            grid.innerHTML = '';
            if (list.length === 0) {
                grid.innerHTML = '<div style="color:#e53935;font-weight:600;">Không tìm thấy sản phẩm phù hợp!</div>';
                return;
            }
            list.forEach(p => {
                grid.innerHTML += `
                <div class="product-card">
                    <button class="add-cart" title="Thêm vào giỏ" onclick="addToCart(${p.id})">
                        <svg width="20" height="20" fill="#3182ce"><rect x="4" y="7" width="12" height="7" rx="2" fill="#e6f0ff"/><rect x="7" y="10" width="6" height="3" rx="1.5" fill="#3182ce"/></svg>
                    </button>
                    <img src="${p.img}" alt="${p.name}">
                    <h4>${p.name}</h4>
                    <div class="desc">${p.desc}</div>
                    <div class="price">${p.price.toLocaleString()}đ</div>
                    <button class="buy-btn" onclick="addToCart(${p.id});toggleCart();">Mua ngay</button>
                </div>
                `;
            });
        }
        function addToCart(id) {
            const prod = products.find(p => p.id === id);
            if (!prod) return;
            const idx = cart.findIndex(c => c.id === id);
            if (idx >= 0) {
                cart[idx].qty += 1;
            } else {
                cart.push({ ...prod, qty: 1 });
            }
            updateCartCount();
            saveCart();
        }
        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + item.qty, 0);
            const cartCount = document.getElementById('cart-count');
            cartCount.innerText = count;
            cartCount.style.display = count > 0 ? 'inline' : 'none';
        }
        function toggleCart() {
            const panel = document.getElementById('cart-panel');
            if (panel.style.display === 'none' || panel.style.display === '') {
                renderCart();
                panel.style.display = 'flex';
                document.getElementById('btn-cart').classList.add('active');
            } else {
                panel.style.display = 'none';
                document.getElementById('btn-cart').classList.remove('active');
            }
        }
        function renderCart() {
            const list = document.getElementById('cart-list');
            list.innerHTML = '';
            let total = 0;
            cart.forEach(item => {
                total += item.price * item.qty;
                list.innerHTML += `
                <div class="cart-item">
                    <img src="${item.img}" alt="${item.name}">
                    <span class="cart-title">${item.name}</span>
                    <span>x${item.qty}</span>
                    <span class="cart-price">${(item.price * item.qty).toLocaleString()}đ</span>
                    <button class="cart-remove" onclick="removeCart(${item.id})">Xóa</button>
                </div>
                `;
            });
            document.getElementById('cart-total').innerText = "Tổng cộng: " + total.toLocaleString() + "đ";
        }
        function removeCart(id) {
            cart = cart.filter(item => item.id !== id);
            updateCartCount();
            renderCart();
            saveCart();
        }
        function checkoutCart() {
            if (cart.length === 0) {
                alert("Giỏ hàng trống!");
                return;
            }
            alert("Đặt hàng thành công! Cảm ơn bạn đã mua sắm.");
            cart = [];
            updateCartCount();
            renderCart();
            saveCart();
            document.getElementById('cart-panel').style.display = 'none';
        }
        function saveCart() {
            localStorage.setItem('cart', JSON.stringify(cart));
        }
        function loadCart() {
            const saved = localStorage.getItem('cart');
            if (saved) cart = JSON.parse(saved);
            updateCartCount();
        }
        function renderNotifications() {
            const list = document.getElementById('notification-list');
            list.innerHTML = "";
            notifications.forEach((n, i) => {
                const item = document.createElement('div');
                item.style.padding = "8px 0";
                item.style.borderBottom = "1px solid #eee";
                item.style.cursor = "pointer";
                item.style.background = n.read ? "#fff" : "#e6f0ff";
                item.innerText = n.text;
                item.onclick = function() {
                    notifications[i].read = true;
                    updateNotificationCount();
                    renderNotifications();
                };
                list.appendChild(item);
            });
            updateNotificationCount();
        }
        function updateNotificationCount() {
            const unread = notifications.filter(n => !n.read).length;
            const notifyCount = document.getElementById('notify-count');
            if (unread > 0) {
                notifyCount.innerText = unread > 9 ? "9+" : unread;
                notifyCount.style.display = "inline";
            } else {
                notifyCount.style.display = "none";
            }
        }
        // Thay thế hàm chatbotReply bằng gọi API ChatGPT
        async function chatbotReply() {
            const input = document.getElementById('chatInput').value;
            document.getElementById('chatReply').innerText = "Đang trả lời...";
            // Thay YOUR_OPENAI_API_KEY bằng API key của bạn
            const apiKey = "YOUR_OPENAI_API_KEY";
            const response = await fetch("https://api.openai.com/v1/chat/completions", {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                    "Authorization": "Bearer " + apiKey
                },
                body: JSON.stringify({
                    model: "gpt-3.5-turbo",
                    messages: [
                        {role: "system", content: "Bạn là chuyên gia tư vấn đồ điện nước, máy bơm, mô tơ, trả lời ngắn gọn, dễ hiểu, ưu tiên giải thích cho khách hàng phổ thông, hiểu cả từ địa phương và câu tắt."},
                        {role: "user", content: input}
                    ],
                    max_tokens: 200
                })
            });
            const data = await response.json();
            if (data.choices && data.choices[0]) {
                document.getElementById('chatReply').innerText = data.choices[0].message.content;
            } else {
                document.getElementById('chatReply').innerText = "Xin lỗi, hiện tại tôi chưa trả lời được. Bạn vui lòng hỏi lại sau!";
            }
        }
        function showProfile() {
            let avatarSrc = currentUser.avatar || "https://cdn-icons-png.flaticon.com/512/149/149071.png";
            document.getElementById('avatar-img').src = avatarSrc;
            document.getElementById('profile-info').innerHTML =
                `<b>Username:</b> ${currentUser.username}<br>
                 <b>Email:</b> ${currentUser.email}<br>
                 <b>Số điện thoại:</b> ${currentUser.phone || ''}<br>
                 <b>Ngày sinh:</b> ${currentUser.dob || ''}<br>
                 <b>Giới tính:</b> ${currentUser.gender || ''}`;
            document.getElementById('settings-email').value = currentUser.email;
            document.getElementById('settings-password').value = '';
        }
        function changeAvatar(event) {
            event.preventDefault();
            const input = document.getElementById('avatar-input');
            if (input.files && input.files[0]) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    currentUser.avatar = e.target.result;
                    document.getElementById('avatar-img').src = currentUser.avatar;
                    document.getElementById('avatar-header').src = currentUser.avatar;
                    localStorage.setItem('currentUser', JSON.stringify(currentUser));
                    localStorage.setItem('users', JSON.stringify(users));
                };
                reader.readAsDataURL(input.files[0]);
            }
            return false;
        }
        document.getElementById('avatar-input').addEventListener('change', function() {
            changeAvatar(new Event('submit'));
        });
        function saveSettings(e) {
            e.preventDefault();
            currentUser.email = document.getElementById('settings-email').value;
            const newPass = document.getElementById('settings-password').value;
            if (newPass) currentUser.password = newPass;
            localStorage.setItem('currentUser', JSON.stringify(currentUser));
            localStorage.setItem('users', JSON.stringify(users));
            document.getElementById('settings-msg').innerText = 'Đã lưu cài đặt!';
            showProfile();
            return false;
        }
        // Tìm kiếm sản phẩm
        function searchProducts() {
            const keyword = document.getElementById('searchInput').value.toLowerCase();
            let filtered = products.filter(p => p.name.toLowerCase().includes(keyword) || p.desc.toLowerCase().includes(keyword));
            renderProducts(filtered);
        }
        // Lọc sản phẩm theo bộ lọc
        function filterProducts() {
            let cats = Array.from(document.querySelectorAll('.filter-cat:checked')).map(e => e.value);
            let min = parseInt(document.getElementById('priceMin').value) || 0;
            let max = parseInt(document.getElementById('priceMax').value) || 999999999;
            let filtered = products.filter(p => {
                let okCat = cats.length === 0 || cats.includes(p.name);
                let okPrice = p.price >= min && p.price <= max;
                return okCat && okPrice;
            });
            renderProducts(filtered);
        }
        // Khi reload, vào trang mua đồ nếu đã đăng nhập
        window.onload = function() {
            const savedUsers = localStorage.getItem('users');
            if (savedUsers) {
                users = JSON.parse(savedUsers);
            }
            const savedUser = localStorage.getItem('currentUser');
            loadCart();
            if (savedUser) {
                currentUser = JSON.parse(savedUser);
                document.getElementById('loginForm').style.display = 'none';
                document.getElementById('registerForm').style.display = 'none';
                document.getElementById('sidebar').style.display = 'flex';
                document.getElementById('main-content').style.display = 'block';
                document.getElementById('user-info').style.display = 'flex';
                document.getElementById('search-bar').style.display = 'flex';
                document.getElementById('avatar-header').src = currentUser.avatar || "https://cdn-icons-png.flaticon.com/512/149/149071.png";
                document.getElementById('username-header').innerText = currentUser.username;
                showSection('products');
                updateNotificationCount();
                showProfile();
                renderProducts(products);
                updateCartCount();
            }
            // Thêm sự kiện Enter cho chatInput
            document.getElementById('chatInput').addEventListener('keydown', function(e) {
                if (e.key === 'Enter') {
                    chatbotReply();
                }
            });
        };
    </script>
</body>
</html>
