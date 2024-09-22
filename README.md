[Uploading login.html…]()<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login & Registrasi</title>
    <link rel="stylesheet" href="login.css">
</head>
<body>

<div class="container" id="formContainer">
    <h2 id="formTitle">Login</h2>
    <form id="loginForm" onsubmit="return handleSubmit(event);">
        <input type="text" id="username" placeholder="Username" required>
        <input type="password" id="password" placeholder="Password" required>
        <button type="submit">Login</button>
    </form>
    <div class="toggle">
        <span>Belum punya akun? <a href="#" id="toggleLink">Registrasi</a></span>
    </div>
    <div id="errorMessage" style="color: red; display: none;"></div>
</div>

<!-- Kotak input untuk memasukkan kode OTP -->
<div class="container" id="otpContainer" style="display: none;">
    <h2>Verifikasi OTP</h2>
    <form id="otpForm" onsubmit="return handleOtpSubmit(event);">
        <input type="text" id="otpCode" placeholder="Masukkan kode OTP" required>
        <button type="submit">Verifikasi</button>
    </form>
    <div id="otpErrorMessage" style="color: red; display: none;"></div>
</div>

<script>
    const formContainer = document.getElementById('formContainer');
    const otpContainer = document.getElementById('otpContainer');
    const formTitle = document.getElementById('formTitle');
    const loginForm = document.getElementById('loginForm');
    const toggleLink = document.getElementById('toggleLink');
    const errorMessage = document.getElementById('errorMessage');
    const otpErrorMessage = document.getElementById('otpErrorMessage');
    let storedOtp;

    toggleLink.addEventListener('click', (e) => {
        e.preventDefault();
        if (formTitle.innerText === 'Login') {
            formTitle.innerText = 'Registrasi';
            loginForm.innerHTML = `
                <input type="text" id="fullName" placeholder="Nama Lengkap" required>
                <input type="text" id="username" placeholder="Username" required>
                <input type="email" id="email" placeholder="Email" required>
                <input type="password" id="password" placeholder="Password" required>
                <select id="gender" required>
                    <option value="" disabled selected>Jenis Kelamin</option>
                    <option value="male">Pria</option>
                    <option value="female">Wanita</option>
                    <option value="other">Lainnya</option>
                </select>
                <input type="date" id="dob" placeholder="Tanggal Lahir" required>
                <input type="text" id="address" placeholder="Alamat" required>
                <input type="tel" id="phone" placeholder="Nomor Handphone" required>
                <button type="submit">Registrasi</button>
            `;
            toggleLink.innerText = 'Sudah punya akun? Login';
            errorMessage.style.display = 'none'; 
        } else {
            formTitle.innerText = 'Login';
            loginForm.innerHTML = `
                <input type="text" id="username" placeholder="Username" required>
                <input type="password" id="password" placeholder="Password" required>
                <button type="submit">Login</button>
            `;
            toggleLink.innerText = 'Belum punya akun? Registrasi';
            errorMessage.style.display = 'none'; 
        }
    });

    function handleSubmit(event) {
        event.preventDefault(); 
        const username = document.getElementById('username').value;
        const password = document.getElementById('password').value;
        
        if (formTitle.innerText === 'Login') {
            const storedUser = JSON.parse(localStorage.getItem(username));
            if (storedUser && storedUser.password === password) {
                localStorage.setItem('loggedInUser', username); 
                window.location.href = 'dashboard.html';
            } else {
                errorMessage.textContent = 'Username atau password salah.';
                errorMessage.style.display = 'block';
            }
        } else {
            const email = document.getElementById('email').value;
            const dob = document.getElementById('dob').value;
            const fullName = document.getElementById('fullName').value;
            const gender = document.getElementById('gender').value;
            const address = document.getElementById('address').value;
            const phone = document.getElementById('phone').value;

            if (localStorage.getItem(username)) {
                errorMessage.textContent = 'Username sudah digunakan.';
                errorMessage.style.display = 'block';
            } else {
                storedOtp = generateOtp(); 
                sendOtpToEmail(email, storedOtp); 
                formContainer.style.display = 'none';
                otpContainer.style.display = 'block';

                // Simpan data registrasi ke localStorage
                const userData = { password, email, dob, fullName, gender, address, phone };
                localStorage.setItem(username, JSON.stringify(userData));
            }
        }
        return false; 
    }

    function handleOtpSubmit(event) {
        event.preventDefault();
        const otpCode = document.getElementById('otpCode').value;

        if (otpCode === storedOtp) {
            alert('Registrasi berhasil! Anda dapat login sekarang.');
            formTitle.innerText = 'Login';
            loginForm.innerHTML = `
                <input type="text" id="username" placeholder="Username" required>
                <input type="password" id="password" placeholder="Password" required>
                <button type="submit">Login</button>
            `;
            toggleLink.innerText = 'Belum punya akun? Registrasi';
            errorMessage.style.display = 'none'; 
            formContainer.style.display = 'block'; 
            otpContainer.style.display = 'none'; 
            document.getElementById('otpCode').value = '';
            storedOtp = ''; 
        } else {
            otpErrorMessage.textContent = 'Kode OTP salah.';
            otpErrorMessage.style.display = 'block';
        }
        return false;
    }

    function generateOtp() {
        return Math.floor(100000 + Math.random() * 900000).toString(); 
    }

    function sendOtpToEmail(email, otp) {
        alert(`Kode OTP telah dikirim ke ${email}: ${otp}`); 
    }

</script>

</body>
</html>

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    color: #333;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 800px;
    margin: auto;
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
    color: #2c3e50;
}

.section {
    margin-bottom: 20px;
    padding: 15px;
    border-left: 5px solid #3498db;
    background: #ecf0f1;
    border-radius: 5px;
}

.section h2 {
    color: #2980b9;
}

.back-button {
    display: inline-block;
    margin-top: 20px;
    padding: 10px 15px;
    color: white;
    background: #2980b9;
    text-decoration: none;
    border-radius: 5px;
}

.back-button:hover {
    background: #1a6d8c;
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Manajemen Stoma</title>
    <link rel="stylesheet" href="manajemen_stoma.css"> <!-- Link ke file CSS -->
</head>
<body>
    <div class="container">
        <h1>Manajemen Stoma</h1>
        <p>Manajemen stoma adalah proses perawatan dan pemantauan stoma untuk memastikan kesehatan dan kenyamanan pasien. Berikut adalah beberapa aspek penting dalam manajemen stoma:</p>

        <div class="section">
            <h2>1. Perawatan Stoma</h2>
            <p>Perawatan yang tepat dapat membantu mencegah iritasi dan infeksi. Pastikan area stoma selalu bersih dan kering.</p>
        </div>

        <div class="section">
            <h2>2. Pemantauan Kesehatan</h2>
            <p>Selalu perhatikan perubahan pada stoma Anda. Segera konsultasikan ke dokter jika ada tanda-tanda infeksi atau masalah lainnya.</p>
        </div>

        <div class="section">
            <h2>3. Pemilihan Alat Bantu</h2>
            <p>Pilih alat bantu yang sesuai dengan jenis stoma Anda. Alat yang tepat dapat meningkatkan kenyamanan dan mencegah kebocoran.</p>
        </div>

        <div class="section">
            <h2>4. Nutrisi dan Diet</h2>
            <p>Perhatikan asupan makanan Anda. Beberapa makanan dapat mempengaruhi kesehatan stoma dan pencernaan.</p>
        </div>

        <div class="section">
            <h2>5. Dukungan Emosional</h2>
            <p>Berbicara dengan profesional kesehatan atau bergabung dengan kelompok dukungan dapat membantu Anda mengatasi tantangan emosional terkait stoma.</p>
        </div>

        <a href="dashboard.html" class="back-button">Kembali ke Dashboard</a>
    </div>
</body>
</html>

body {
    font-family: 'Arial', sans-serif;
    background-color: #f0f8ff;
    margin: 0;
    padding: 0;
}

.container {
    max-width: 800px;
    margin: 50px auto;
    padding: 20px;
    background-color: #ffffff;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
    text-align: center;
}

header {
    margin-bottom: 20px;
}

h1 {
    color: #2c3e50;
    font-size: 2.2em;
}

p {
    color: #34495e;
}

.notification-list {
    display: flex;
    justify-content: center;
    flex-direction: column;
    gap: 20px;
}

.notification-item {
    display: flex;
    align-items: center;
    background-color: #eafaf1;
    border-left: 5px solid #28a745;
    padding: 15px;
    border-radius: 5px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
}

.notification-item:hover {
    transform: scale(1.02);
}

.icon {
    font-size: 2.5em;
    color: #28a745;
    margin-right: 20px;
}

.message h2 {
    margin: 0;
    font-size: 1.5em;
    color: #2c3e50;
}

.message p {
    margin: 5px 0;
    color: #555;
}

.time {
    font-size: 0.9em;
    color: #888;
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="notifications.css">
    <title>Notifikasi Kesehatan</title>
</head>
<body>
    <div class="container">
        <header>
            <h1>Notifikasi Harian</h1>
            <p>Ingat untuk melaporkan kesehatan Anda setiap hari pukul <strong>07.00 WIB</strong>.</p>
        </header>
        <section class="notification-list">
            <div class="notification-item">
                <div class="icon">&#128276;</div>
                <div class="message">
                    <h2>Pengingat Kesehatan</h2>
                    <p>Jangan lupa untuk melakukan pengecekan kesehatan Anda hari ini dan laporkan hasilnya!</p>
                    <span class="time">Setiap Hari: 07.00 WIB</span>
                </div>
            </div>
        </section>
    </div>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 800px;
    margin: 0 auto;
    background: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
    color: #333;
}

h2 {
    color: #007bff;
    margin-top: 20px;
}

.nutrisi-diperlukan, .nutrisi-dihindari {
    margin-bottom: 30px;
    padding: 15px;
    border-left: 5px solid #0f5132;
    background-color: #e9ecef;
    border-radius: 5px;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    margin-bottom: 10px;
}

.back-button {
    display: inline-block;
    margin-top: 20px;
    padding: 10px 15px;
    background-color: #007bff;
    color: white;
    text-decoration: none;
    border-radius: 5px;
    text-align: center;
}

.back-button:hover {
    background-color: #0056b3;
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nutrisi untuk Penderita Stoma</title>
    <link rel="stylesheet" href="nutrisi.css"> <!-- Link ke file CSS -->
</head>
<body>
    <div class="container">
        <h1>Nutrisi untuk Penderita Stoma</h1>

        <section class="nutrisi-diperlukan">
            <h2>Nutrisi yang Diperlukan</h2>
            <ul>
                <li>
                    <strong>Protein:</strong> Penting untuk penyembuhan dan memperbaiki jaringan.
                    <ul>
                        <li>Contoh: Daging ayam, ikan, telur, dan kacang-kacangan.</li>
                    </ul>
                </li>
                <li>
                    <strong>Serat:</strong> Membantu menjaga kesehatan pencernaan.
                    <ul>
                        <li>Contoh: Sayuran hijau, buah-buahan, dan biji-bijian.</li>
                    </ul>
                </li>
                <li>
                    <strong>Vitamin dan Mineral:</strong> Seperti vitamin C, vitamin D, dan kalsium untuk mendukung sistem imun dan kesehatan tulang.
                    <ul>
                        <li>Contoh: Jeruk (vitamin C), susu (kalsium), dan ikan berlemak (vitamin D).</li>
                    </ul>
                </li>
                <li>
                    <strong>Cairan:</strong> Pastikan cukup terhidrasi untuk mencegah dehidrasi.
                    <ul>
                        <li>Contoh: Air, jus buah, dan sup.</li>
                    </ul>
                </li>
            </ul>
        </section>

        <section class="nutrisi-dihindari">
            <h2>Nutrisi yang Harus Dihindari</h2>
            <ul>
                <li>
                    <strong>Makanan Berlemak Tinggi:</strong> Dapat menyebabkan ketidaknyamanan pencernaan.
                    <ul>
                        <li>Contoh: Makanan cepat saji, gorengan, dan daging berlemak.</li>
                    </ul>
                </li>
                <li>
                    <strong>Makanan Pedas:</strong> Dapat memicu iritasi pada saluran pencernaan.
                    <ul>
                        <li>Contoh: Cabai, saus sambal, dan makanan berbumbu kuat.</li>
                    </ul>
                </li>
                <li>
                    <strong>Minuman Berkarbonasi:</strong> Dapat menyebabkan gas dan kembung.
                    <ul>
                        <li>Contoh: Soda dan minuman bersoda lainnya.</li>
                    </ul>
                </li>
                <li>
                    <strong>Produk Susu:</strong> Beberapa orang mungkin mengalami kesulitan mencerna produk susu.
                    <ul>
                        <li>Contoh: Susu, keju, dan yogurt.</li>
                    </ul>
                </li>
            </ul>
        </section>

        <a href="dashboard.html" class="back-button">Kembali ke Dashboard</a>
    </div>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 20px;
    background-color: #f4f4f4;
}

.container {
    max-width: 600px;
    margin: auto;
    background: white;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

h1, h2 {
    color: #333;
}

.profile-container {
    display: flex;
    align-items: center; /* Center vertically */
}

.profile-frame {
    width: 150px;
    height: 150px;
    border: 5px solid #ccc;
    border-radius: 50%;
    overflow: hidden;
    margin-right: 20px;
    display: flex; /* Flexbox for centering */
    justify-content: center; /* Center horizontally */
    align-items: center; /* Center vertically */
}

.profile-frame img {
    width: 100%; /* Make sure image covers the frame */
    height: 100%; /* Full height */
    object-fit: cover; /* Crop image to fit */
}

.profile-info, .health-check {
    margin-bottom: 20px;
}

label {
    display: block;
    margin: 10px 0 5px;
}

input {
    width: calc(100% - 20px);
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 3px;
}

button {
    padding: 10px 15px;
    background-color: #5cb85c;
    color: white;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

button:hover {
    background-color: #4cae4c;
}

.avatar-options {
    margin-top: 10px;
}

.avatar-options img {
    width: 50px;
    height: 50px;
    margin-right: 5px;
    cursor: pointer;
}

#uploadButton {
    margin-top: 10px;
}

/* Gaya untuk ikon logout */
.footer-menu {
    margin-top: 20px;
    text-align: center;
}

.footer-menu a {
    display: inline-block;
    margin-top: 10px;
    text-decoration: none;
    color: #333; /* Warna teks */
}

.footer-menu .icon {
    width: 20px; /* Ukuran ikon */
    height: 20px; /* Ukuran ikon */
    vertical-align: middle;
    margin-right: 5px; /* Jarak antara ikon dan teks */
}

#logoutBtn {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: transparent;
    border: none;
    cursor: pointer;
    margin-top: 10px; /* Jarak antara tombol edit profil dan logout */
}

#logoutBtn:hover .icon {
    color: red; /* Warna ikon saat hover */
}

/* Gaya untuk tombol kembali */
.back-button {
    display: flex;
    align-items: center;
    cursor: pointer;
    margin-bottom: 20px;
}

.back-button .icon {
    width: 20px;
    height: 20px;
    margin-right: 5px; /* Jarak antara ikon dan teks */
}

/* Media Queries for Responsiveness */
@media (max-width: 600px) {
    .profile-frame {
        width: 100px; /* Adjust width for mobile */
        height: 100px; /* Adjust height for mobile */
    }
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profil Pengguna</title>
    <link rel="stylesheet" href="profile.css">
</head>
<body>

<div class="container">
    <div class="back-button" onclick="window.location.href='dashboard.html'">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="icon">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
        </svg>
        <span>Kembali</span>
    </div>

    <h1>Profil Pengguna</h1>
    
    <div class="profile-container">
        <div class="profile-frame" id="profileFrame">
            <img src="anon.png" id="profilePhoto" alt="Foto Profil"> <!-- Gambar anonim -->
        </div>
        <div class="profile-info">
            <h2>Informasi Pribadi</h2>
            <p><strong>Nama Lengkap:</strong> <span id="fullNameDisplay"></span></p>
            <p><strong>Username:</strong> <span id="usernameDisplay"></span></p>
            <p><strong>Email:</strong> <span id="emailDisplay"></span></p>
            <p><strong>Usia:</strong> <span id="ageDisplay"></span></p>
            <p><strong>Nomor Handphone:</strong> <span id="phoneDisplay"></span></p>
            <button id="editProfileButton">Edit Profil</button>
        </div>
    </div>

    <button id="selectProfileButton">Pilih Profil</button>
    <input type="file" id="fileInput" accept="image/*" style="display:none;" onchange="loadImage(event)">
    <div class="avatar-options" id="avatarOptions" style="display: none;">
        <!-- Opsi avatar akan diisi di sini jika diperlukan -->
    </div>

    <div class="footer-menu">
        <a href="#" id="logoutBtn">
            <!-- Ikon Logout -->
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="icon">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1m-6-5a9 9 0 100-18 9 9 0 000 18z" />
            </svg>
            <span>Logout</span>
        </a>
    </div>
</div>

<script>
    // Menampilkan informasi pengguna
    const username = localStorage.getItem('loggedInUser');
    document.getElementById('usernameDisplay').textContent = username;

    // Mengambil data dari localStorage
    const userData = JSON.parse(localStorage.getItem(username));
    const fullName = userData ? userData.fullName : 'Tidak tersedia';
    const email = userData ? userData.email : 'Tidak tersedia';
    const age = userData ? calculateAge(userData.dob) : 'Tidak tersedia'; // Hitung usia berdasarkan tanggal lahir
    const phone = userData ? userData.phone : 'Tidak tersedia';

    document.getElementById('fullNameDisplay').textContent = fullName;
    document.getElementById('emailDisplay').textContent = email;
    document.getElementById('ageDisplay').textContent = age;
    document.getElementById('phoneDisplay').textContent = phone;

    // Mengambil foto profil dari localStorage jika ada
    const savedPhoto = localStorage.getItem(`${username}_profilePhoto`);
    if (savedPhoto) {
        document.getElementById('profilePhoto').src = savedPhoto;
    }

    function loadImage(event) {
        const file = event.target.files[0];
        if (file) {
            const reader = new FileReader();
            reader.onload = function(e) {
                document.getElementById('profilePhoto').src = e.target.result;
                localStorage.setItem(`${username}_profilePhoto`, e.target.result); // Simpan foto ke localStorage
            }
            reader.readAsDataURL(file);
        }
    }

    function calculateAge(dob) {
        const birthDate = new Date(dob);
        const ageDiff = Date.now() - birthDate.getTime();
        const ageDate = new Date(ageDiff);
        return Math.abs(ageDate.getUTCFullYear() - 1970);
    }

    document.getElementById('editProfileButton').addEventListener('click', () => {
        alert('Fitur edit profil belum tersedia!');
    });

    document.getElementById('selectProfileButton').addEventListener('click', () => {
        const avatarOptions = document.getElementById('avatarOptions');
        avatarOptions.style.display = avatarOptions.style.display === 'none' ? 'block' : 'none'; // Tampilkan atau sembunyikan opsi avatar
        document.getElementById('fileInput').click(); // Buka dialog pemilihan foto pribadi
    });

    document.getElementById('logoutBtn').addEventListener('click', function() {
        // Hapus user dari localStorage dan redirect ke halaman login
        localStorage.removeItem('loggedInUser');
        window.location.href = 'login.html';
    });
</script>

</body>
</html>

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 600px;
    margin: 0 auto;
    background: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
    color: #333;
}

.laporan-item {
    margin-bottom: 20px;
    padding: 15px;
    background-color: #e9ecef;
    border-radius: 5px;
}

.pesan-kesehatan {
    margin-top: 20px;
    padding: 15px;
    background-color: #d1e7dd;
    border-left: 5px solid #0f5132;
    border-radius: 5px;
}

.back-button {
    display: inline-block;
    margin-top: 20px;
    padding: 10px 15px;
    background-color: #007bff;
    color: white;
    text-decoration: none;
    border-radius: 5px;
    text-align: center;
}

.back-button:hover {
    background-color: #0056b3;
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laporan Kesehatan Penderita Stoma</title>
    <link rel="stylesheet" href="reports.css"> <!-- Link ke file CSS -->
</head>
<body>
    <div class="container">
        <h1>Laporan Kesehatan Harian</h1>
        <div id="laporanContainer">
            <!-- Laporan akan ditampilkan di sini -->
        </div>

        <a href="dashboard.html" class="back-button">Kembali ke Dashboard</a>
    </div>

    <script>
        // Ambil data laporan dari localStorage
        const laporanList = JSON.parse(localStorage.getItem('laporanKesehatanList')) || [];
        const laporanContainer = document.getElementById('laporanContainer');

        if (laporanList.length > 0) {
            laporanList.forEach((laporan) => {
                const laporanDiv = document.createElement('div');
                laporanDiv.classList.add('laporan-item');
                laporanDiv.innerHTML = `
                    <h3>Tanggal: ${laporan.tanggal}</h3>
                    <p>Kondisi Stoma: ${laporan.kondisiStoma}</p>
                    <p>Nyeri: ${laporan.nyeri}</p>
                    <p>Aktivitas Fisik: ${laporan.aktivitas}</p>
                    <p>Konsumsi Air: ${laporan.konsumsiAir} liter</p>
                    <p>Warna Cairan: ${laporan.warnaCairan}</p>
                    <p>Jumlah Cairan: ${laporan.jumlahCairan} liter</p>
                    <p>Konsistensi Cairan: ${laporan.konsistensiCairan}</p>
                    <p>Bau Cairan: ${laporan.bauCairan}</p>
                    <hr>
                `;

                // Menentukan pesan berdasarkan kondisi dan menambahkannya ke laporan
                let pesan = '';
                if (laporan.kondisiStoma === 'baik') {
                    pesan = 'Anda dalam kondisi baik. Tetap jaga kesehatan!';
                } else if (laporan.kondisiStoma === 'iritasi') {
                    pesan = 'Anda mengalami iritasi. Segera konsultasikan dengan dokter jika tidak membaik.';
                } else if (laporan.kondisiStoma === 'infeksi') {
                    pesan = 'Anda mengalami infeksi. Penting untuk segera mendapatkan perawatan medis.';
                } else if (laporan.kondisiStoma === 'bengkak') {
                    pesan = 'Anda mengalami pembengkakan. Harap lakukan pemeriksaan lebih lanjut.';
                }

                // Tambahkan pesan ke laporan
                laporanDiv.innerHTML += `<p><strong>Pesan:</strong> ${pesan}</p>`;
                laporanContainer.appendChild(laporanDiv);
            });
        } else {
            laporanContainer.innerHTML = '<p>Belum ada laporan kesehatan.</p>';
        }
    </script>
</body>
</html>

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    color: #333;
    padding: 20px;
}

.container {
    max-width: 900px;
    margin: auto;
    background-color: #fff;
    padding: 30px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
}

h1 {
    color: #007BFF;
    font-size: 2.5em;
    margin-bottom: 20px;
}

h2 {
    color: #0056b3;
    font-size: 1.8em;
    margin-top: 30px;
    margin-bottom: 10px;
}

p {
    font-size: 1.2em;
    margin-bottom: 20px;
    line-height: 1.6;
}

ul {
    list-style-type: disc;
    margin-left: 40px;
    margin-bottom: 20px;
}

ul li {
    font-size: 1.1em;
    margin-bottom: 10px;
}

.back-button {
    display: inline-block;
    padding: 10px 20px;
    background-color: #007BFF;
    color: #fff;
    text-decoration: none;
    border-radius: 5px;
    margin-top: 20px;
    transition: background-color 0.3s ease;
}

.back-button:hover {
    background-color: #0056b3;
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stoma - Informasi Lengkap</title>
    <link rel="stylesheet" href="stoma.css"> <!-- Link ke file CSS -->
</head>
<body>
    <div class="container">
        <h1>Apa Itu Stoma?</h1>
        <p>Stoma adalah sebuah lubang buatan yang dibuat melalui operasi untuk menghubungkan bagian dalam tubuh dengan bagian luar, biasanya untuk keperluan ekskresi. Stoma bisa berada di usus besar, usus kecil, atau kandung kemih, dan memerlukan perawatan khusus.</p>

        <h2>Komplikasi yang Bisa Terjadi</h2>
        <ul>
            <li>Infeksi di sekitar stoma</li>
            <li>Hernia stoma (tonjolan jaringan di sekitar stoma)</li>
            <li>Masalah iritasi kulit akibat cairan tubuh</li>
            <li>Perubahan bentuk atau ukuran stoma</li>
            <li>Sumbatan usus yang dapat menyebabkan nyeri dan kembung</li>
        </ul>

        <h2>Aksesoris yang Harus Disediakan oleh Penderita Stoma</h2>
        <ul>
            <li>Kantong stoma (untuk menampung ekskresi)</li>
            <li>Perekat kulit untuk melindungi area sekitar stoma</li>
            <li>Pembersih antiseptik khusus stoma</li>
            <li>Sabuk stoma untuk menopang kantong</li>
            <li>Pelindung kulit untuk mencegah iritasi</li>
        </ul>

        <a href="dashboard.html" class="back-button">Kembali ke Dashboard</a>
    </div>
</body>
</html>

body {
    font-family: 'Arial', sans-serif;
    background-color: #e9ecef;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 800px;
    margin: 0 auto;
    background: #ffffff;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
    color: #007bff;
    margin-bottom: 20px;
}

h2 {
    color: #0f5132;
    margin-top: 20px;
    border-bottom: 2px solid #007bff;
    padding-bottom: 5px;
}

.aktivitas-dilakukan, .aktivitas-dihindari {
    margin-bottom: 30px;
}

.aktivitas-card {
    background-color: #f1f1f1;
    border-radius: 5px;
    padding: 15px;
    margin: 10px 0;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    transition: transform 0.2s;
}

.aktivitas-card:hover {
    transform: scale(1.02);
}

p {
    margin: 0;
}

.back-button {
    display: inline-block;
    margin-top: 20px;
    padding: 12px 18px;
    background-color: #007bff;
    color: white;
    text-decoration: none;
    border-radius: 5px;
    text-align: center;
    transition: background-color 0.3s;
}

.back-button:hover {
    background-color: #0056b3;
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aktivitas untuk Penderita Stoma</title>
    <link rel="stylesheet" href="aktivitas.css"> <!-- Link ke file CSS -->
</head>
<body>
    <div class="container">
        <h1>Aktivitas untuk Penderita Stoma</h1>

        <section class="aktivitas-dilakukan">
            <h2>Aktivitas yang Harus Dilakukan</h2>
            <div class="aktivitas-card">
                <p>✅ Olahraga ringan seperti berjalan kaki atau yoga.</p>
            </div>
            <div class="aktivitas-card">
                <p>✅ Latihan pernapasan untuk meningkatkan kapasitas paru-paru.</p>
            </div>
            <div class="aktivitas-card">
                <p>✅ Menjaga kebersihan area stoma dan sekitarnya.</p>
            </div>
            <div class="aktivitas-card">
                <p>✅ Melakukan aktivitas sosial untuk menjaga kesehatan mental.</p>
            </div>
        </section>

        <section class="aktivitas-dihindari">
            <h2>Aktivitas yang Harus Dihindari</h2>
            <div class="aktivitas-card">
                <p>❌ Aktivitas fisik berat seperti angkat beban yang dapat membebani perut.</p>
            </div>
            <div class="aktivitas-card">
                <p>❌ Olahraga kontak yang dapat berisiko cedera.</p>
            </div>
            <div class="aktivitas-card">
                <p>❌ Menahan napas terlalu lama saat melakukan aktivitas.</p>
            </div>
            <div class="aktivitas-card">
                <p>❌ Mengabaikan tanda-tanda ketidaknyamanan atau masalah pada stoma.</p>
            </div>
        </section>

        <a href="dashboard.html" class="back-button">Kembali ke Dashboard</a>
    </div>
</body>
</html>

/* cek_kesehatan.css */
.container {
    width: 90%;
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f7f7f7;
    border-radius: 10px;
}

label {
    display: block;
    margin-top: 10px;
}

input, select {
    width: 100%;
    padding: 10px;
    margin: 5px 0;
    border-radius: 5px;
    border: 1px solid #ccc;
}

input[type="submit"] {
    background-color: #4CAF50;
    color: white;
    border: none;
    cursor: pointer;
}

.back-button {
    display: inline-block;
    margin-top: 20px;
    padding: 10px;
    background-color: #007BFF;
    color: white;
    text-decoration: none;
    border-radius: 5px;
}

.hasil-cek {
    margin-top: 20px;
}

/* laporan.css */
.container {
    width: 90%;
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 10px;
}

.laporan-item {
    background-color: #f9f9f9;
    padding: 15px;
    margin-bottom: 15px;
    border: 1px solid #ddd;
    border-radius: 5px;
}

.back-button {
    display: inline-block;
    margin-top: 20px;
    padding: 10px;
    background-color: #007BFF;
    color: white;
    text-decoration: none;
    border-radius: 5px;
}
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cek Kesehatan Penderita Stoma</title>
    <link rel="stylesheet" href="cek_kesehatan.css"> <!-- Link ke file CSS -->
</head>
<body>
    <div class="container">
        <h1>Cek Kesehatan Penderita Stoma</h1>
        <p>Isi form di bawah ini untuk melakukan cek kesehatan harian Anda.</p>
        
        <form id="cekKesehatanForm">
            <label for="tanggal">Tanggal:</label>
            <input type="text" id="tanggal" name="tanggal" readonly> <!-- Tanggal otomatis diisi -->

            <label for="kondisiStoma">Kondisi Stoma:</label>
            <select id="kondisiStoma" name="kondisiStoma" required>
                <option value="">Pilih kondisi</option>
                <option value="baik">Baik</option>
                <option value="iritasi">Iritasi</option>
                <option value="infeksi">Infeksi</option>
                <option value="bengkak">Bengkak</option>
            </select>

            <label for="nyeri">Apakah Anda merasakan nyeri di area stoma?</label>
            <select id="nyeri" name="nyeri" required>
                <option value="">Pilih jawaban</option>
                <option value="ya">Ya</option>
                <option value="tidak">Tidak</option>
            </select>

            <label for="aktivitas">Apakah Anda sudah melakukan aktivitas fisik hari ini?</label>
            <select id="aktivitas" name="aktivitas" required>
                <option value="">Pilih jawaban</option>
                <option value="sudah">Sudah</option>
                <option value="belum">Belum</option>
            </select>

            <label for="konsumsiAir">Berapa banyak air yang Anda konsumsi hari ini (liter)?</label>
            <input type="number" id="konsumsiAir" name="konsumsiAir" step="0.1" min="0" max="10" required>

            <label for="warnaCairan">Warna Cairan:</label>
            <select id="warnaCairan" name="warnaCairan" required>
                <option value="">Pilih warna</option>
                <option value="jernih">Jernih</option>
                <option value="kuning">Kuning</option>
                <option value="hijau">Hijau</option>
                <option value="merah">Merah</option>
                <option value="coklat">Coklat</option>
            </select>

            <label for="jumlahCairan">Jumlah Cairan (liter):</label>
            <input type="number" id="jumlahCairan" name="jumlahCairan" step="0.1" min="0" max="10" required>

            <label for="konsistensiCairan">Konsistensi Cairan:</label>
            <select id="konsistensiCairan" name="konsistensiCairan" required>
                <option value="">Pilih konsistensi</option>
                <option value="cair">Cair</option>
                <option value="kental">Kental</option>
                <option value="padat">Padat</option>
            </select>

            <label for="bauCairan">Bau Cairan:</label>
            <select id="bauCairan" name="bauCairan" required>
                <option value="">Pilih bau</option>
                <option value="normal">Normal</option>
                <option value="busuk">Busuk</option>
                <option value="asam">Asam</option>
                <option value="tidak ada">Tidak Ada</option>
            </select>

            <input type="submit" value="Kirim Cek Kesehatan">
        </form>

        <div id="hasilCekKesehatan" class="hasil-cek" style="display: none;">
            <h2>Terima Kasih!</h2>
            <p>Laporan kesehatan Anda telah dikirim.</p>
        </div>

        <a href="dashboard.html" class="back-button">Kembali ke Dashboard</a>
    </div>

    <script>
        // Mengambil tanggal saat ini dan menampilkan di input tanggal
        const today = new Date();
        const formattedDate = today.toLocaleDateString('id-ID', {
            day: 'numeric',
            month: 'long',
            year: 'numeric'
        });
        document.getElementById('tanggal').value = formattedDate;

        // Menyimpan data ke localStorage dan menampilkan hasil cek
        const form = document.getElementById('cekKesehatanForm');

        form.addEventListener('submit', function(event) {
            event.preventDefault();

            // Ambil nilai dari form
            const tanggal = document.getElementById('tanggal').value;
            const kondisiStoma = document.getElementById('kondisiStoma').value;
            const nyeri = document.getElementById('nyeri').value;
            const aktivitas = document.getElementById('aktivitas').value;
            const konsumsiAir = document.getElementById('konsumsiAir').value;
            const warnaCairan = document.getElementById('warnaCairan').value;
            const jumlahCairan = document.getElementById('jumlahCairan').value;
            const konsistensiCairan = document.getElementById('konsistensiCairan').value;
            const bauCairan = document.getElementById('bauCairan').value;

            // Buat objek laporan kesehatan
            const laporanKesehatan = {
                tanggal,
                kondisiStoma,
                nyeri,
                aktivitas,
                konsumsiAir,
                warnaCairan,
                jumlahCairan,
                konsistensiCairan,
                bauCairan
            };

            // Ambil data laporan yang sudah ada di localStorage, jika ada
            let laporanList = JSON.parse(localStorage.getItem('laporanKesehatanList')) || [];

            // Tambahkan laporan baru
            laporanList.push(laporanKesehatan);

            // Simpan kembali ke localStorage
            localStorage.setItem('laporanKesehatanList', JSON.stringify(laporanList));

            // Alihkan ke halaman laporan
            window.location.href = 'reports.html'; // Ganti dengan nama file laporan Anda
        });
    </script>
</body>
</html>

/* Reset margin dan padding */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    background: linear-gradient(135deg, #74ebd5, #acb6e5); /* Gradient background */
    color: #333;
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh; /* Pastikan body memenuhi tinggi viewport */
}

/* Container utama */
.container {
    background-color: white;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
    text-align: left; /* Rata kiri teks dalam container */
    max-width: 400px;
    width: 100%;
    margin: 40px auto; /* Rata tengah dan beri margin atas */
    transition: transform 0.3s; /* Efek transisi saat hover */
}

.container:hover {
    transform: translateY(-5px); /* Efek mengangkat saat hover */
}

h1 {
    margin-bottom: 10px;
    color: #5a5a5a;
    text-shadow: 1px 1px 2px rgba(255, 255, 255, 0.5); /* Efek bayangan pada teks */
}

p {
    margin-bottom: 30px;
    font-size: 1.2rem;
    color: #333;
}

/* Styling untuk kontainer pencarian */
.search-container {
    display: flex;
    margin-bottom: 20px; /* Jarak bawah untuk pemisah */
}

#searchInput {
    flex: 1; /* Mengisi ruang yang tersedia */
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px 0 0 5px;
    font-size: 1rem;
    transition: border-color 0.3s;
    outline: none;
}

#searchInput:focus {
    border-color: #5a5a5a; /* Ganti warna border saat fokus */
    box-shadow: 0 0 5px rgba(90, 90, 90, 0.5); /* Efek bayangan saat fokus */
}

#searchButton {
    padding: 10px 15px;
    background-color: #5a5a5a; /* Warna latar belakang tombol */
    color: white; /* Warna teks tombol */
    border: none;
    border-radius: 0 5px 5px 0;
    cursor: pointer;
    font-size: 1rem;
    transition: background-color 0.3s, transform 0.3s;
}

#searchButton:hover {
    background-color: #4a4a4a; /* Warna latar belakang saat hover */
    transform: scale(1.05); /* Efek scale saat hover */
}

/* Kotak informasi */
.boxes-container {
    display: flex; /* Mengubah untuk menjadi satu baris */
    flex-direction: column; /* Mengubah arah menjadi kolom */
    gap: 20px; /* Jarak antara kotak */
    margin: 40px 0; /* Jarak atas dan bawah untuk menghindari tumpang tindih */
    width: 100%; /* Pastikan container mengisi lebar */
    max-width: 400px; /* Batasi lebar maksimal untuk responsivitas */
}

.box {
    margin: 10px;
    background-color: white;
    border-radius: 10px;
    padding: 20px; /* Sesuaikan padding */
    text-align: center;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s, box-shadow 0.3s; /* Tambahkan transisi untuk bayangan */
}

.box:hover {
    transform: scale(1.05); /* Efek mouse-over */
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2); /* Efek bayangan saat hover */
}

.box svg {
    width: 40px; /* Ukuran ikon */
    height: 40px; /* Ukuran ikon */
    margin-bottom: 10px; /* Jarak antara ikon dan teks */
}

/* Footer menu styling */
.footer-menu {
    position:sticky; /* Mengubah menjadi relative */
    width: 100%;
    display: flex;
    justify-content: space-around;
    background-color: white;
    padding: 15px 0;
    box-shadow: 0 -4px 12px rgba(0, 0, 0, 0.1);
}

.menu-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-decoration: none;
    color: #333;
    font-size: 0.9rem;
    transition: transform 0.3s; /* Transisi saat hover */
}

.menu-item:hover {
    transform: translateY(-2px); /* Efek mengangkat saat hover */
}

.icon {
    width: 24px;
    height: 24px;
    margin-bottom: 5px;
    transition: transform 0.3s;
}

.menu-item:hover .icon {
    transform: scale(1.2);
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard</title>
    <link rel="stylesheet" href="dashboard.css"> <!-- Link ke file CSS -->
</head>
<body>
    <div class="container">
        <h1>Selamat datang di Portal Stoma!</h1>
        <p id="welcomeMessage"></p>
        <div class="search-container">
            <input type="text" id="searchInput" placeholder="Cari...">
            <button id="searchButton">Cari</button>
        </div>
        <div id="searchResults" class="search-results"></div> <!-- Tempat untuk menampilkan hasil pencarian -->
    </div>

    <!-- Kotak informasi -->
    <div class="boxes-container">
        <div class="left-column">
            <div class="box" onclick="window.location.href='stoma.html'">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 2a10 10 0 100 20 10 10 0 000-20z" />
                </svg>
                <h3>STOMA</h3>
            </div>
            <div class="box" onclick="window.location.href='nutrisi.html'">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 2L2 12h3v6h6v3h6v-3h3L12 2z" />
                </svg>
                <h3>NUTRISI</h3>
            </div>
        </div>
        <div class="right-column">
            <div class="box" onclick="window.location.href='aktivitas.html'">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 9l1-1h5l2 2-1 1-5-5-1 1-1-1z" />
                </svg>
                <h3>AKTIVITAS</h3>
            </div>
            <div class="box" onclick="window.location.href='cek_kesehatan.html'">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 2v2m0 16v2m4-20h2m-16 0h2m2 16h2m-6-6h2m12 0h2M2 12h2m16 0h2M4 4l16 16M4 20L20 4" />
                </svg>
                <h3>YOK CEK KESEHATAN KAMU!!<3</h3>
            </div>
        </div>
    </div>

    <div class="footer-menu">
        <a href="profile.html" class="menu-item">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="icon">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5.121 17.804A9 9 0 1118.879 17.8M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
            </svg>
            <span>Profil Pengguna</span>
        </a>
        <a href="reports.html" class="menu-item">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="icon">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3v18h18M9 3v4h6V3H9z" />
            </svg>
            <span>Laporan</span>
        </a>
        <a href="notifications.html" class="menu-item">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="icon">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-2.81A2 2 0 0117 13V9a7.002 7.002 0 00-13.994.002V13a2 2 0 01-.195.816L3 17h5m7 0v1a3 3 0 11-6 0v-1m6 0H9" />
            </svg>
            <span>Notifikasi</span>
        </a>
    </div>

    <script>
        const username = localStorage.getItem('loggedInUser');

        if (username) {
            document.getElementById('welcomeMessage').textContent = `Halo, ${username}! Selamat datang kembali.`;
        } else {
            window.location.href = 'login.html'; // Kembali ke halaman login jika tidak ada user
        }

        // Data contoh untuk pencarian
        const items = [
            { name: "Nutrisi Sehat", link: "nutrisi.html" },
            { name: "Aktivitas Fisik", link: "aktivitas.html" },
            { name: "Cek Kesehatan", link: "cek_kesehatan.html" },
            { name: "Manajemen Stoma", link: "manajemen_stoma.html" },
            { name: "Dukungan Emosional", link: "dukungan.html" },
            { name: "Informasi Medis", link: "informasi_medis.html" }
        ];

        document.getElementById('searchButton').addEventListener('click', () => {
            const query = document.getElementById('searchInput').value.toLowerCase();
            const resultsContainer = document.getElementById('searchResults');
            resultsContainer.innerHTML = ''; // Hapus hasil sebelumnya

            if (query) {
                const results = items.filter(item => item.name.toLowerCase().includes(query));
                if (results.length > 0) {
                    results.forEach(item => {
                        const div = document.createElement('div');
                        const link = document.createElement('a');
                        link.href = item.link; // Set link untuk diarahkan ke halaman yang relevan
                        link.textContent = item.name;
                        link.target = "_blank"; // Membuka link di tab baru (opsional)
                        div.appendChild(link);
                        resultsContainer.appendChild(div);
                    });
                } else {
                    resultsContainer.textContent = "Tidak ada hasil yang ditemukan.";
                }
            } else {
                alert("Silakan masukkan kata kunci pencarian.");
            }
        });
    </script>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    background-color: #eaeaea;
    color: #333;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 800px;
    margin: auto;
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    animation: fadeIn 1s ease-in;
}

h1 {
    text-align: center;
    color: #2c3e50;
}

.section {
    margin-bottom: 20px;
    padding: 15px;
    border-left: 5px solid #3498db;
    background: #f8f9fa;
    border-radius: 5px;
    transition: transform 0.3s;
}

.section:hover {
    transform: scale(1.02);
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
}

.section h2 {
    color: #2980b9;
}

.back-button {
    display: inline-block;
    margin-top: 20px;
    padding: 10px 15px;
    color: white;
    background: #2980b9;
    text-decoration: none;
    border-radius: 5px;
    transition: background 0.3s;
}

.back-button:hover {
    background: #1a6d8c;
}

@keyframes fadeIn {
    from {
        opacity: 0;
    }
    to {
        opacity: 1;
    }
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dukungan Emosional Penderita Stoma</title>
    <link rel="stylesheet" href="dukungan.css"> <!-- Link ke file CSS -->
</head>
<body>
    <div class="container">
        <h1>Dukungan Emosional untuk Penderita Stoma</h1>
        <p>Menjalani kehidupan dengan stoma bisa menjadi tantangan emosional. Dukungan yang tepat dapat membantu Anda mengatasi perasaan tersebut.</p>

        <div class="section">
            <h2>1. Berbicara dengan Profesional</h2>
            <p>Konsultasi dengan psikolog atau konselor dapat membantu Anda memahami dan mengatasi perasaan Anda.</p>
        </div>

        <div class="section">
            <h2>2. Bergabung dengan Kelompok Dukungan</h2>
            <p>Kelompok dukungan memberikan kesempatan untuk berbagi pengalaman dan mendapatkan perspektif dari orang lain yang menghadapi situasi serupa.</p>
        </div>

        <div class="section">
            <h2>3. Edukasi Diri Sendiri</h2>
            <p>Pahami kondisi Anda dan bagaimana cara mengelolanya. Pengetahuan dapat mengurangi kecemasan dan meningkatkan kepercayaan diri.</p>
        </div>

        <div class="section">
            <h2>4. Luangkan Waktu untuk Diri Sendiri</h2>
            <p>Penting untuk menjaga kesehatan mental. Lakukan aktivitas yang Anda nikmati dan yang dapat membantu meredakan stres.</p>
        </div>

        <div class="section">
            <h2>5. Jaga Hubungan Sosial</h2>
            <p>Jangan ragu untuk berbagi perasaan Anda dengan teman dan keluarga. Dukungan mereka bisa sangat berarti.</p>
        </div>

        <a href="dashboard.html" class="back-button">Kembali ke Dashboard</a>
    </div>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    color: #333;
    margin: 0;
    padding: 20px;
}

.container {
    max-width: 800px;
    margin: auto;
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
    color: #2c3e50;
}

.section {
    margin-bottom: 20px;
    padding: 15px;
    border-left: 5px solid #3498db;
    background: #ecf0f1;
    border-radius: 5px;
}

.section h2 {
    color: #2980b9;
}

.button, .back-button {
    display: inline-block;
    margin-top: 20px;
    padding: 10px 15px;
    color: white;
    background: #2980b9;
    text-decoration: none;
    border-radius: 5px;
    transition: background 0.3s;
}

.button:hover, .back-button:hover {
    background: #1a6d8c;
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Informasi Medis untuk Penderita Stoma</title>
    <link rel="stylesheet" href="informasi_medis.css"> <!-- Link ke file CSS -->
</head>
<body>
    <div class="container">
        <h1>Informasi Medis untuk Penderita Stoma</h1>
        
        <div class="section">
            <h2>Pengertian Stoma</h2>
            <p>Stoma adalah suatu pembukaan yang dibuat secara bedah pada permukaan tubuh untuk mengeluarkan produk tubuh seperti tinja atau urine.</p>
        </div>

        <div class="section">
            <h2>Perawatan Stoma</h2>
            <p>Perawatan yang baik penting untuk mencegah infeksi dan iritasi. Pastikan area stoma selalu bersih dan kering.</p>
        </div>

        <div class="section">
            <h2>Kondisi Kesehatan yang Perlu Diperhatikan</h2>
            <p>Perhatikan tanda-tanda infeksi seperti kemerahan, pembengkakan, atau keluarnya nanah dari stoma.</p>
        </div>

        <div class="section">
            <h2>Pemilihan Alat Bantu</h2>
            <p>Pilih alat bantu yang sesuai untuk stoma Anda agar nyaman dan mencegah kebocoran.</p>
        </div>

        <a href="dashboard.html" class="back-button">Kembali ke Dashboard</a>
    </div>
</body>
</html>

/* Reset dasar */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Arial', sans-serif;
    background: linear-gradient(135deg, #74ebd5, #acb6e5);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.container {
    background-color: white;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 100%;
    max-width: 400px;
    transition: transform 0.2s ease-in-out;
}

input {
    display: block;
    width: 100%;
    padding: 10px;
    margin: 10px 0;
    border: 1px solid #ccc;
    border-radius: 5px;
    transition: border 0.3s, background-color 0.3s;
}

input:focus {
    border-color: #74ebd5;
    background-color: #f0f0f0;
}

button {
    width: 100%;
    padding: 10px;
    background-color: #74ebd5;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #acb6e5;
}

.toggle {
    margin-top: 10px;
}

a {
    color: #74ebd5;
    cursor: pointer;
}

h2 {
    margin-bottom: 20px;
    color: #333;
}

#errorMessage, #otpErrorMessage {
    color: red;
    margin-top: 10px;
}

