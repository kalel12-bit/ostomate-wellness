[Uploading dashboard.html…]()<!DOCTYPE html>
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

<!DOCTYPE html>
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

<?xml version="1.0" encoding="UTF-8"?>
<svg version="1.1" viewBox="0 0 2048 1927" width="1280" height="1280" xmlns="http://www.w3.org/2000/svg">
<path transform="translate(0)" d="m0 0h2048v1927h-2048z" fill="#95C2C5"/>
<path transform="translate(0)" d="m0 0h2048v505l-9 9-7 8-12 12-7 8-12 14-7 8-12 13-7 8-9 10-9 11-11 13-15 23-9 17-5 13-5 12-3 8-2 8-4 13-7 15-8 12-10 10-14 11-13 10-10 8-14 12-11 9-16 16-10 13-12 14-11 13-9 11-10 11-9 11-12 13-9 10-14 14-1 2h-2v2h-2l-2 4-17 16-8 7h-2l-1 3-10 8h-2l-1 3-8 6h-2v2l-5 3h-2v2l-5 3h-2v2l-5 2v2l-3 2h-3v2l-28 14-5 2h-3v2l-8 2-9 2v2l-6 1h-14l-17-6-11-3-5-3-3-4-6-2-4-4 1-4 5-3 10-4 3-3-5 3-8 2-12 4h-22l-36-6-4-2-14-2-6-3-1-4 4-3 25-6 18-3 8-3 10-2 15-8v-2h-4v-2l-27 9-24 5h-6v2l-11 1-17 3-15 1-7-3-13-4-13-2-21-1-2-1v-3h-5l1-3 9-2v-2l9-2 13-2 7-2 7-1 25-2 37-5 14-1v-2l16-3 7-3 5-6h2l2-6-7 1-9 4-5 3-19 5-21 3-35 4-30 5-33 7h-3v2l-13 3-7 1-19 1-6 3-11 2-14 1h-10l-16-8-9-7-4-3-6-14-9-26-7-15-8-14-3-2-2-6-4-8-3-10h-2l-2-10v-7l4-8h2v-6l4-4h5v-2l-15-2-6-2 6 8 1 4-3 7h-3l-2-12-5-9-1-5 2-2-1-9 5-5 10-4 13-4 9-5 2-3 7-1v-2l10-4 10-5 6-4 4-4 13-9 14-11 13-10 5-5 8-7 10-7 3-3 8-7 10-8 10-7 9-4 1-3 12-6 1-2 7-2v-2l17-7 8-2 15-5 13-4 24-7 9-1 10-4 9-2 12-5 11-3 11-4h3v-2l9-3 8-2 13-4 11-5h3v-2l13-5 15-5 12-6 9-3 5-3 8-3 29-12 8-4 2-2 9-3 8-5 10-4 19-10 9-6 12-6 15-10 11-7 6-5 6-2 1-2h2l1-3 4-4h2l2-6h2l1-5 3-5 4-10h2l1-4 7-9 3-7 5-5 3-5 1-4 4-4 3-5 2-5h2l1-6 2-1 1-4 3-3 6-11 2-6h2l2-6 6-11 3-9 4-10 5-12 4-13 4-8 6-21 3-10v-12l-2-2-7 17-9 26-8 22-6 13-11 23-4 10-2 4h-2l-3 9-4 7-2 5-3 3-2 5h-2l-2 6-15 24-7 12-8 13-3 5-7 11-6 7-14 10-18 10-7 4-11 5h-6l-4-9-2-34-6-51-4-23-3-39-3-27-2-24-3-17-2-15-1-13v-37h-2l-1 35v60l5 57v8l-2 5-6 3h9l2 3 3 27 2 24 3 26 2 9 2 21 1 7h2l1 4h2v5l-7 5-9 4-16 8-7 3-5 2h-3l-1 3-9 2-10 5h-3v2l-12 4-6 4-13 5h-3v2l-12 3-13 5-11 5-20 8h-3v-10l4-14 1-8v-14l-1-18-5-11-9-3-3 3h-3l8 8 3 10 2 3v14l-5 16-5 12-7 8-6 12-4 4-5 1v2l-18 7-10 2h-5v2l-15 6-10 2-11 4-13 4-14 4-6 3-13 4-21 9-17 9-5 4-5 2-13 10-9 6-5 5-11 9-10 9-20 16-18 13-7 5-5 3-17 11-10 5-12 5-10 5-12 2h-44l-26-4-26-6-19-5-18-9-13-5-17-9-14-10-11-8-38-28-12-9-12-8-9-4-23-4-4-4 2-5 10-5 14-5 59-5 61-3 65-5 35-5 84-14 7-1 3 1v-2h5v-1l8 1v-3l24-5 3-1h10v-2l15-3h7l2 1 1-2 8-3 12-3 5-1v-2l6-2 14-3 14-5 4-2 9-2 3-2 9-3 13-5 15-6 12-5 46-23 31-15 10-4 6-4 20-12 11-7 19-13 4-1 2-4 11-9 10-9 5-6 5-5 11-10 11-14 8-7 10-6h3v-2l5-1h-4l-10 2h-4v2l-10 6-9 8-6 7-5 5-13 12-12 12-10 8-3 3h-2v2l-18 13-18 11-11 6-12 7h-4v2l-10 4-19 10-30 14-10 4-17 7-8 4h-3v2l-13 4h-3v2l-13 4-17 5h-3v2l-20 5-5 2h-9v2l-8 2-17 2-23 5-10 2-24 5h-4v2l-61 11-51 8-20 1-12 2-58 6-44 2-32 1-44 3-7-1-5-2-1-4 3-3 3-2 18-6 15-6 10-3v-2l4-2 1-3-8-1-21 3-32 8-36 12-22 9-16 6-20 8-36 15-27 13-10 6-11 5-19 10-7 6-8 4-7 3-6 3-22 13-15 9-6 4-5 2-3 1v2l-36 18-12 4-9 2-19 6-6 2-24 4h-17l-3-2v-8l5-7 5-12 8-18 2-3v-11l-3-1v-10l2-9 7-8 9-9 10-14 3-7 8-14 6-12 1-8h-2l-8 14-10 15-11 11-5 7-4 8-5 1-1-1v-48l-2-13-3-8-8-13-13-14-14-11-4-5-9-5v-2l-5-1v-2l-5-1-5-5-13-9-5-3-9-4-8-6-6-3v-2l-5-2-10-6v-2l-5-1-8-4-3-3-7-3-15-8-16-8-23-12-7-4-7-3-28-14-3-3-9-4v-2l-9-3-22-12-21-12-15-10-7-5-3-1v-2h-3v-2h-3v-2l-4-2-11-9-10-9-8-7-9-11-1-5-3-1-4-13-3-7 1 14-3-4-1-11h-2v8l5 18 5 12 4 7 16 10 11 8 21 14 19 12 14 9 24 14 27 16 16 9 18 10 12 7 11 6 11 7 8 4 10 6 10 5 17 10 11 7 7 5 9 5 21 14 7 5v2l4 1 3 2v2l4 1v2h3v2l4 1v2l4 1 5 4v2l4 1 6 5 3 4 5 3 13 11 3 5 5 5 4 8 1 43 2 26v11l2 4v14l-5 12-4 7h-2l-1 6-6 12-4 4-5 11-3 9-5-3-13-13-3-7-5-5-8-9-5-6-8-6-5-12-1-1-1-14h-2l-2-13-8-19-3-5-2-6-8-13-4-5-2-7h-3l3 13 6 14 2 4h2l5 12 4 7v3h2l1 2 1 11 4 13 1 9 4 9 4 4 3 7 3 3 3 1 7 8 7 7 12 18 12 16 1 3 4 4 7 13 3 3 8 16 4 10 1 5v7l-2 7h-2l-1 5h-2l-1 6-5 11-1 2h-2l-1 5-6 8-8 7-7 5h-9l-8-3v-2l-4-2-5-4-5-5-8-7-43-43-7-8-6-5-7-8-1-3h-2l-2-5-6-2-8-7-2-3-5-2-3-3-8-5v-3h-6l-1 4-4-2-9-10-8-8-8-4-5-4-2-1 6 9 8 9 11 8 13 13 4 16 2 7h2l4 9 6 10 1 1v6l4 2 7 10 5 5 5 10 8 7 5 9v4l4 2 4 5 6 9 5 16v11l-5 5-7 11-8 10-14 7-10 2h-9l-11-8-8-8-4-2-5-8-14-15-6-5-3-6-7-9-10-16-8-13-3-6-9-8-10-5 6 9 8 18v2h2l11 21 6 11 9 12 14 15 14 10 10 8 2 4v7l-6 12-16 16-5 3-12-2-15-5-14-6-17-10-16-11-15-11-10-7-8-3-8-7-4-7v-2h-2l-4-9-10-15h-1l1 8 4 10v2h2l6 11 2 5 5 9 3 7 2 7 4 10 4 6 4 13 4 8 3 7 4 9 2 9h2l1 6h2l7 13 3 5 6 11 2 4h2l4 10 6 10 1 9h2l8 16 4 10 1 16-2 7h-11l-7-2-9-9-7-8-4-3-3-5-1-4-4-2-4-7-5-5-5-7-3-5-5-7-1-3-3-2-1-3-2-1-1-3-2-1-6-11-1-3h-2l-2-5-4-4-8-11-6-11-2-5h-2v-2l-3-1-3-5v-2h-2l-1-3-5-5-1-4h-2l-3-5v-2h-2l-5-8v-2h-2l-9-14-1-4-3-1-5-9v-2h-2l-1-4h-2l-3-5v-2h-2l-1-4h-2l-5-8v-2h-2v-3l-3-1-7-11-8-11-10-15-13-20-9-13-8-11-3-3z" fill="#95C2C5"/>
<path transform="translate(2047,529)" d="m0 0h1v1398h-2048v-1057l7 6 6 9 7 10 10 15 10 14 8 11 2 5 5 5 5 8 5 5 1 3 2 1 5 9 3 1 6 10 9 11 4 5 3 5 4 4 6 11 5 5 1 5h2l7 11 9 13 5 9 7 11 8 13 6 9v3h2l3 5v3l3 1 8 13 3 5 1 5-5-5-3 1-4 1-10-13-10-15-16-26-8-16-7-10-8-13-9-15-8-11 7 14 13 23 7 12 5 12v6l-3 4 1 8 11 30 10 30 14 39 24 68 16 50 9 27 14 50 17 65 11 41 9 24 10 20 8 12 12 17 11 13 13 12 11 9 14 13 8 7 20 20 11 9 13 11 4 2v2l5 2 5 3 1 2 4 2 1-1h5v2l4 2 1 3 3 1v3l17 10 8 4 1-1-5-3-4-4-2-5-24-16-17-13-13-10-11-9-16-13-14-11-10-8v-2l-4-2-18-22-10-13-6-12-9-16-8-16-10-25-11-30-12-39-17-61-14-51-10-32-11-35-14-41-9-24-11-29-7-15-7-14 1-4 5 1 7 8 3 5v6l7 8 12 24 15 36 15 40 8 23 9 29 15 52 14 49 14 54 10 34 10 26 8 16 22 33 9 12 9 10 7 8 13 12 11 9 18 13 15 10 21 13 23 13 24 12 55 23 15 6 16 6 12 4 7 3 10 3 8 3 11 4 16 5 21 5h13l23 1h38l21-1 14-2 22-7 27-2h81l30 3 25 5 23 7 20 8 16 6 36 15 23 10 28 10 50 17 34 10 116 31 55 16 45 12 26 6 36 7 37 5 37 4 29 2 24 1h58l27-3 53-9 48-9 22-4 24-6 18-6 27-11 13-6 8-4 16-11 7-4 5 2v2h2l2 5 6-1 2-7 2-24 2-31 2-39v-55l-4-55-1-3-2-22-3-14-7-34-4-21-9-44-5-21-5-25-9-54-4-27-5-47-2-16-8-60-8-54-5-51-4-56-5-37-6-29-12-44-10-32-17-47-4-8-3-2 1-4 12-15 11-14 8-10 27-27 14-11h2v-2l7-4 3-3 4-3h2v-2l10-7h2v-2l5-2v-2l11-9 6-6h2l3-6h2l2-4 6-11 5-14 6-21 8-24 7-15 7-11 5-6 9-11 7-9 13-13 7-8 4-5h2l2-4 5-6h2l2-4 12-13 5-5 10-8 7-8 11-12z" fill="#F6F8F9"/>
<path transform="translate(871,672)" d="m0 0h9l12 4 20 13 11 7 12 8 17 11 18 12 14 9 6 4 5 2 6 4 7 3 5 5 3 4 1 3 3 33 2 8 5 13 6 16 8 20 9 20 15 25 11 16 14 15 5 6 14 11 10 7 5 1-3-5 3-1-6-5-5-5-13-11-10-10-10-14-10-15-6-16-6-15-7-16-7-22v-10l3 3 11 20 3 4 3 7 13 27 2 4v3h2l4 9 6 9 10 14 6 7 6 3 4 5 9 6 10 5 3 1v-2l6 2 7 6 5 1-4-8-6-5v-2l-6-2-20-11-3-2v-2h-3v-2l-4-2-7-8-7-10-9-15-13-25-9-17-8-13-8-16-6-14-4-12v-7h9l9 3v2l9 2 26 6 16 3 27 2 7 1 3 3 11 23 1 2v25l5 14v2h3l11 23 4 7 9 19 3 12v9l-11 6-8 6v4l8-3 10-7 4 2 7 17 7 3 1 3-6 5-10 2-8 1-1 1h-10l-13-1 1 2 10 3 15 3h16l21-2 20-4h20l9-4 4-3h3v2l4 2v2l22 1 78 10 16 6 10 5 27 8 28 6 14 2 15 5 25 11 15 5 18 5 17 1v-2l11-2 10-4 7-1v-2l9-3 12-7 5-3 5 1 1 1 2 96v74l-2 44-4 34-6 36-7 30-8 31-8 23-12 32-12 29-12 31-10 25-7 21-2 11-2 3-2 15-2 8-2 13v36l4 26 4 27 1 2 1 14-52 5-78 11-1 1-18 2-28 5-1 1-16 2-27 6-1 1-14 2h-6v2l-25 4-40 7-41 6-22 2h-13l-6-3v-2h-2l-6-11-8-20-6-17-10-30-6-23-3-13-1-5v-8l17-1 16-3 19-1 39-4 5-1 22-2 1-1 46-6 26-3 13-3 25-4 14-3 9-2 20-6 5-3 1-2-17 2-21 4-11 1-17 3-41 5-31 4-10 2-12 1-10 2-37 4-11 2-27 3-11 2-18 2-7 1-2-18-4-16-6-14-8-10-3-2v-2l-6-2-2-1v-2l-5-1v-2l-9-3-16-5-19-7-18-11-10-9-1-2-5-3-13-13-9-11-2-1-1-3-4-4v-4h-2l-8-11-4-8-10-16-3-6v-2h-2l-8-15-2-6h-2l-6-13v-2h-2l-14-29-10-23-7-16-9-25-3-10-1-7v-13l-6-8-10-40-1-1-2-12-4-18-6-28-7-46-2-13-1-22-1-6-3-62v-48l1-31 4-44 1-10 1-22 1-10 1-1 6-42 10-49 3-18 3-21 2-6 5-9z" fill="#F6F8F9"/>
<path transform="translate(988)" d="m0 0h1060v505l-9 9-7 8-12 12-7 8-12 14-7 8-12 13-7 8-9 10-9 11-11 13-15 23-9 17-5 13-5 12-3 8-2 8-4 13-7 15-8 12-10 10-14 11-13 10-10 8-14 12-11 9-16 16-10 13-12 14-11 13-9 11-10 11-9 11-12 13-9 10-14 14-1 2h-2v2h-2l-2 4-17 16-8 7h-2l-1 3-10 8h-2l-1 3-8 6h-2v2l-5 3h-2v2l-5 3h-2v2l-5 2v2l-3 2h-3v2l-28 14-5 2h-3v2l-8 2-9 2v2l-6 1h-14l-17-6-11-3-5-3-3-4-6-2-4-4 1-4 5-3 10-4 3-3-5 3-8 2-12 4h-22l-36-6-4-2-14-2-6-3-1-4 4-3 25-6 18-3 8-3 10-2 15-8v-2h-4v-2l-27 9-24 5h-6v2l-11 1-17 3-15 1-7-3-13-4-13-2-21-1-2-1v-3h-5l1-3 9-2v-2l9-2 13-2 7-2 7-1 25-2 37-5 14-1v-2l16-3 7-3 5-6h2l2-6-7 1-9 4-5 3-19 5-21 3-35 4-30 5-33 7h-3v2l-13 3-7 1-19 1-6 3-11 2-14 1h-10l-16-8-9-7-4-3-6-14-9-26-7-15-8-14-3-2-2-6-4-8-3-10h-2l-2-10v-7l4-8h2v-6l4-4h5v-2l-15-2-6-2 6 8 1 4-3 7h-3l-2-12-5-9-1-5 2-2-1-9 5-5 10-4 13-4 9-5 2-3 7-1v-2l10-4 10-5 6-4 4-4 13-9 14-11 13-10 5-5 8-7 10-7 3-3 8-7 10-8 10-7 9-4 1-3 12-6 1-2 7-2v-2l17-7 8-2 15-5 13-4 24-7 9-1 10-4 9-2 12-5 11-3 11-4h3v-2l9-3 8-2 13-4 11-5h3v-2l13-5 15-5 12-6 9-3 5-3 8-3 29-12 8-4 2-2 9-3 8-5 10-4 19-10 9-6 12-6 15-10 11-7 6-5 6-2 1-2h2l1-3 4-4h2l2-6h2l1-5 3-5 4-10h2l1-4 7-9 3-7 5-5 3-5 1-4 4-4 3-5 2-5h2l1-6 2-1 1-4 3-3 6-11 2-6h2l2-6 6-11 3-9 4-10 5-12 4-13 4-8 6-21 3-10v-12l-2-2-7 17-9 26-8 22-6 13-11 23-4 10-2 4h-2l-3 9-4 7-2 5-3 3-2 5h-2l-2 6-15 24-7 12-8 13-3 5-7 11-6 7-14 10-18 10-7 4-11 5-5-1-3-7-1-9-2-44-6-46-3-27-2-11-2-18-3-29-3-41v-96h-7l-13-3-16-8-11-7-13-9-26-14-19-9-26-10-12-4-10-4-38-11-32-8-52-10-66-11-16-2-15-3-9-1-19-3-12-2-15-2-11-2-70-10-24-4-14-2-27-4-41-5-44-4-36-2h-118l-51 2-66 5-74 9-45 7-69 13-63 13-50 11-17 4h-6v-2l11-8h2l1-3 7-3 30-8 38-10 29-7 37-8 60-11 43-6 63-7 44-4 30-2 30-1h61l59 1 35 1 45 3 71 7 80 11 61 10 52 10 79 17 18 3v-3l-15-6-19-4-21-7-38-9-49-9-63-10-115-15-47-5-18-3-17-4z" fill="#FBD8BE"/>
<path transform="translate(0)" d="m0 0h772l2 6-1 1-37 4-39 4-63 8-36 6-48 9-58 12-39 9-25 6-14 4-23 6-13 4-12 3-8 3-37 12-15 5-10 4-23 8-12 5-15 6-15 7-10 6-8 4-20 12-8 5h-2v2l-5 3h-2v2l19-12 14-8 13-6h3v-2l14-3h6l3 3 11 1 1 3-24 10-20 9-25 13-24 15-17 9-21 21-7 8-6 7-5 5-11 14-9 14-4 7v11l5 26 3 13 6 19 4 13 4 8 5 5 14 9 23 16 24 15 12 8 24 14 17 10 19 11 15 9 11 6 16 9 11 6 11 7 8 4 10 6 10 5 17 10 11 7 7 5 9 5 21 14 7 5v2l4 1 3 2v2l4 1v2h3v2l4 1v2l4 1 5 4v2l4 1 6 5 3 4 5 3 13 11 3 5 5 5 4 8 1 43 2 26v11l2 4v14l-5 12-4 7h-2l-1 6-6 12-4 4-5 11-3 9-5-3-13-13-3-7-5-5-8-9-5-6-8-6-5-12-1-1-1-14h-2l-2-13-8-19-3-5-2-6-8-13-4-5-2-7h-3l3 13 6 14 2 4h2l5 12 4 7v3h2l1 2 1 11 4 13 1 9 4 9 4 4 3 7 3 3 3 1 7 8 7 7 12 18 12 16 1 3 4 4 7 13 3 3 8 16 4 10 1 5v7l-2 7h-2l-1 5h-2l-1 6-5 11-1 2h-2l-1 5-6 8-8 7-7 5h-9l-8-3v-2l-4-2-5-4-5-5-8-7-43-43-7-8-6-5-7-8-1-3h-2l-2-5-6-2-8-7-2-3-5-2-3-3-8-5v-3h-6l-1 4-4-2-9-10-8-8-8-4-5-4-2-1 6 9 8 9 11 8 13 13 4 16 2 7h2l4 9 6 10 1 1v6l4 2 7 10 5 5 5 10 8 7 5 9v4l4 2 4 5 6 9 5 16v11l-5 5-7 11-8 10-14 7-10 2h-9l-11-8-8-8-4-2-5-8-14-15-6-5-3-6-7-9-10-16-8-13-3-6-9-8-10-5 6 9 8 18v2h2l11 21 6 11 9 12 14 15 14 10 10 8 2 4v7l-6 12-16 16-5 3-12-2-15-5-14-6-17-10-16-11-15-11-10-7-8-3-8-7-4-7v-2h-2l-4-9-10-15h-1l1 8 4 10v2h2l6 11 2 5 5 9 3 7 2 7 4 10 4 6 4 13 4 8 3 7 4 9 2 9h2l1 6h2l7 13 3 5 6 11 2 4h2l4 10 6 10 1 9h2l8 16 4 10 1 16-2 7h-11l-7-2-9-9-7-8-4-3-3-5-1-4-4-2-4-7-5-5-5-7-3-5-5-7-1-3-3-2-1-3-2-1-1-3-2-1-6-11-1-3h-2l-2-5-4-4-8-11-6-11-2-5h-2v-2l-3-1-3-5v-2h-2l-1-3-5-5-1-4h-2l-3-5v-2h-2l-5-8v-2h-2l-9-14-1-4-3-1-5-9v-2h-2l-1-4h-2l-3-5v-2h-2l-1-4h-2l-5-8v-2h-2v-3l-3-1-7-11-8-11-10-15-13-20-9-13-8-11-3-3z" fill="#FBD8BE"/>
<path transform="translate(849,645)" d="m0 0 7 1-1 6-2 5 2 3-1 6-8 10v12l-3 8-12 78-5 48-2 26-2 36-2 16-3 5-3 1-3-1 1 10 1 1 4 39 1 30 2 21 2 28 3 41 2 10 7 43 4 26 8 32 2 12 4 12 3 8v4h2l4 12-1 4-14 2-53 3-26 1h-59l-14-1-2-1-22-3-30-5-16-3-19-4-30-7-10-2-32-8-37-12-33-12-39-15-19-8-5-2v-2l-5-1-12-5-10-4-8-4-8-3-12-6-8-3-9-4-24-12-22-12-17-10-13-7-8-4v-2l-5-2-13-10-11-7-5-6-2-6h-2l-3-7v-2h-2l-5-10-2-8h-2l-3-7-3-11v-4l7-1h21l8 3 4 4 18 6 16 3 5 1h11l11-6 12-11 6-5 4-10 3-4 23-2 12-6 6-6 6-2 2-4 7-8 7-12 3-4 2-6 5-4-1-9-3-7-7-3-6-5-5-8-1-7 4-5h2l1-4 5-3 5 2 12 13 12 11 3 1v2l5 2 7 4v2l18 3 8-3 18-4 2-1 3-5 7-6 5-7h2l2-5 5-8 2-7 2-10v-24l-4-11-15-24-6-8-2-8h32l15-2 15-4 26-10 18-8 24-13 16-9 3-3 17-10 11-6 6-4h4v-2l17-9h2v-2l14-6 10-4 8-2 1-2 19-7h3v-2l13-4 9-4 9-3 5-2 14-3 42-12z" fill="#FBD8BE"/>
<path transform="translate(988)" d="m0 0h1060v261h-19l-20-2-9-3-9-1-83-1-39 1-9 2-5 3h-3l-3 9-4 10-9 26-8 22-6 13-11 23-4 10-2 4h-2l-3 9-4 7-2 5-3 3-2 5h-2l-2 6-15 24-7 12-8 13-3 5-7 11-6 7-14 10-18 10-7 4-11 5-5-1-3-7-1-9-2-44-6-46-3-27-2-11-2-18-3-29-3-41v-96h-7l-13-3-16-8-11-7-13-9-26-14-19-9-26-10-12-4-10-4-38-11-32-8-52-10-66-11-16-2-15-3-9-1-19-3-12-2-15-2-11-2-70-10-24-4-14-2-27-4-41-5-44-4-36-2h-118l-51 2-66 5-74 9-45 7-69 13-63 13-50 11-17 4h-6v-2l11-8h2l1-3 7-3 30-8 38-10 29-7 37-8 60-11 43-6 63-7 44-4 30-2 30-1h61l59 1 35 1 45 3 71 7 80 11 61 10 52 10 79 17 18 3v-3l-15-6-19-4-21-7-38-9-49-9-63-10-115-15-47-5-18-3-17-4z" fill="#F6F8F9"/>
<path transform="translate(1651,224)" d="m0 0h2l1 37 2 22 3 16 2 16 3 36 1 6 3 39 5 30 5 44 2 34 3 8h6l15-7 19-11 12-8 6-5 8-11 3-5 9-16 6-9 6-11 8-12 6-11 2-1 3-7 2-1 3-8 3-4 3-8h2l2-6 7-16 9-19 8-19 4-12 7-20 6-16 4-8 3 3v12l-8 28-4 9-4 10-4 13-4 9-6 16-8 15h-2l-2 8-7 12h-2l-1 5h-2l-1 6-2 1-3 7-4 6h-2l-1 5-5 8-4 4-2 5-7 9-1 3h-2l-3 10-5 10-2 1-2 5-6 5-1 2h-2l-1 3-7 3-8 6-17 11-11 7-8 4-13 8-19 9-6 3-11 6-6 2-7 4-8 4-13 5-10 4-12 5-7 3-12 5-6 3-6 2-16 6h-3v2l-12 5-7 3-8 2-15 4h-2v2l-16 6-11 3-13 5-12 3-4 2-12 2-21 6-16 5-14 5-8 2-12 5h-3v2l-4 2h-3l-1 3-10 5h-2l-1 4-9 4-11 8-11 9-6 5h-2l-1 3-13 9-5 5-4 2-2 4-26 20-14 10h-2l-2 4-8 5-7 3-8 3h-2v2l-7 2-5 5-14 6-9 2-9 5-1 2 1 10-2 2 4 10 2 3 1 12h3l1-5 1-4-4-6-2-4 16 2 5 2v2l-6 2-2 2-1 6h-2l-2 6-1 2v7l1 3v7h2l8 18 1 1v5l4 2 8 14 7 15 7 20 4 12 3 4v4l4 2 9 7 16 8h10l20-2 9-3 2-1 19-1 17-3h3v-2l31-7 28-5 33-4 23-3 15-3 13-4 4-3 10-4h5v4l-2 3h-2l-2 4-4 4-9 3-13 1v2l-36 5-23 3-17 1-13 2-5 2-18 2v2l-9 3 4 2v3h11l16 2 12 2 14 4 3 2 15-1 17-3h11v-2l26-5 19-6 9-3h3v2l6-1-2 4-15 8-17 4-5 2-18 3-21 5-3 2 1 4 10 3 9 1 9 3 31 5h22l14-5 8-2 3-1-1 3-8 4-8 3-1 5 4 3 6 2 2 4 4 1 7 3 14 4 8 3h20v-2l11-4h6v-2l8-3 26-13h2v-2l6-2v-2l5-2v-2l5-3h2v-2l5-3h2v-2l6-4 7-6 10-8 5-5 8-7 7-7 8-7 2-3h2v-2h2l2-4 19-19 7-8 13-15 12-14 9-10 7-9 9-10 9-11 7-9 9-10 12-12 11-9 14-12 13-10 16-12 15-14 9-14 6-13 4-13 5-16 5-12 6-15 11-20 10-15 8-10 11-13 9-10 7-8 11-12 7-8 13-15 9-10 7-8 12-12 7-8 4-3v24l-7 6-7 8-8 9-12 9-7 8-9 10-1 2h-2l-2 4-5 6h-2l-2 4-7 7-7 8-6 7h-2l-2 4-12 14-4 6-6 8-8 16-4 9-9 28-6 21-6 12-5 8h-2l-2 4-12 12-6 5h-2v2l-5 2v2l-10 7h-2v2l-6 4h-2l-1 3-5 3h-2v2l-11 8-13 12-21 21-6 8-22 28-4 4-3 5-5 6h-2l-2 5-4 4-6 7-9 11-41 41-8 7-13 11-10 8-14 11-5 2-4 8 3 14v165l-2 47-4 36-5 28-9 37-4 15-3 9-3 11-4 10-9 27-4 10-5 15-5 14-4 10-5 12-4 10-5 12-10 27-6 19-6 23-1 5-1 15v24l3 27 7 32 1 8v14l-5 1-3-2-3-7-1-10-3-13-5-38-1-4v-36l3-19 2-7 1-10 3-6 2-10 4-14 4-10 17-43 14-35 5-13 3-8 6-15 8-24 11-44 7-36 5-38 2-27 1-27v-74l-2-96-5-1-17 10-4 2h-5v2l-11 4-9 3h-8v2l-7 1-14-2-14-4-15-5-30-13-15-4-14-2-27-6-23-7-12-6-14-5-73-9-5-1-22-2-4-4v-2l-6 3-4 3-6 2h-20l-20 4-21 2h-16l-20-4-6-3v-2h23l4-1 13-2 6-4 1-4-7-2-6-13-3-6-5 2-8 6-7 1-1-4 9-7 10-5v-9l-4-14-9-20-6-10-7-15v-2h-3l-6-16v-25l-8-17-5-9-1-1-16-2-18-1-35-7-16-5v-2l-8-1-1-1-9-1 2 10 7 19 8 16 9 16 8 14 7 14 12 22 11 17 11 11v2h3v2l5 2 22 12 5 5 5 4 2 7h-5l-5-4v-2l-6-2-2-1v2l-5-1-8-4-11-8-2-4-6-2-9-10-8-12-7-10-2-5v-3h-2l-4-9-12-25-5-10-6-10-7-13v9l9 27 5 11 10 25 4 9 10 15 10 13 11 11 14 11v2l3 1v2l4 2-3 2 2 4h-5l-11-8-10-8-8-7-7-8-9-10-10-15-12-20-8-16-9-21-8-20-5-15-2-4-3-28-1-11-3-6-5-5-8-4-6-4-5-2-18-11-11-8-24-15-10-7-23-15-13-8-10-3h-9l-6 10-3 16-3 24-10 48-5 32-2 15-1 1-1 10-1 22-3 34-2 20-1 31v48l3 62 1 6 1 22 2 13 7 46 6 28 5 21 1 9 2 5 9 36 6 8v13l2 10 10 30 7 15 5 12 11 24 8 17v2h2l6 13v2h2l4 8 6 11v2h2l8 15 7 10 5 10 5 6v2h2l2 7 3 1v3l4 2 12 14 10 10 4 2 5 5 8 7 15 9 24 9 14 4 6 3v2l5 1v2l6 2 8 7 7 10 6 15 4 19v12l7-2 26-3 11-2 19-2 11-2 45-5 2-1 19-2 13-2 36-5 26-3 17-3 16-2 22-4h11l-1 3-7 4-18 5-9 2-14 3-36 6-10 2-64 8-1 1-22 2-15 2-29 3-19 1-16 3h-17l4 24 6 21 8 26 7 20 10 25 5 8v3h2l3 3 3 1h13l29-3 45-7 39-7 15-1v-2l20-3 9-3 25-5 10-1 6-2 29-5 12-1 7-2 22-1 1-1 9-1h23l1 4-4 3-22 6-67 11-99 18-39 6-31 4h-7v2l-8 1h-43l-9-7-5-2-4-4-6-15-10-28-7-27-11-51-3-21-7-19-4-10-6-10-7-9-10-6-16-8-24-9-11-3-11-6-10-7-14-14-13-17-11-17-2-3v-3h-2l-10-16-14-22-10-18-9-16-11-23-10-21-10-23-9-24-3-7-1-10-3-10-1-2-17 2-9 2-43 3h-84l-26-2-27-5-13-3-9-2-15-2-15-4-9-2-21-5-16-5-27-8-25-7-8-3-17-6-12-5-7-3-17-6-12-5-30-12-9-3-8-4-10-4-12-5-10-2-13-5-10-5-17-10-19-9v-2l-6-2-21-12-9-4-7-3-8-2 1 8 9 12 1 5 1 14 1 5-5 13-6 9-7 4-14 1-16-6-13-11-7-7-2-1-2-6-10-14-3-5-8-13-2-1-3-6v-2h-2l-4-8-7-10-6-11-7-10-6-10-10-15-2-5h-2l-2-5-5-5-7-12-5-5-1-5-3-1-9-12-4-5-2-6-4-1-4-6v-3l-3-1-3-5v-2l-4-2-4-7-6-7-4-7-10-14-7-10-12-18-8-11-7-8v-22l6 5 9 13 15 23 21 31 7 10 3 3v3h2l5 8v2h2l1 4h2l3 5v2h2l1 4h2l6 11 2 1 4 7 6 9v2h2l5 8v2h2l3 5v2h2l4 7 3 2v3h2l4 7 2 1v2h2l8 13 4 7 6 8v2l3 1 1 5h2l7 11v3l3 1v3l3 1 1 3 3 2 5 9 3 3 4 7 4 6 3 2 4 7 3 2 3 5 1 4 4 2 7 7 7 8 3 3 6 1h11l1-6-1-16-9-21-2-5h-2l-3-11-7-12-1-6h-2l-6-9-5-10-4-6-3-6v-2h-2l-1-6h-2l-4-11-5-10-4-10-4-11-3-7-3-4-4-10-2-9-6-12-2-2-3-7-3-6v-2h-2l-6-15v-5h3l7 10 5 8 1 6h2l6 10 8 6 9 4 15 11 17 12 13 8 14 8 21 8 13 3 5-1 10-9 4-4h2l8-16v-7l-3-5-13-10-11-8-8-8-9-11-10-15-8-17-3-5v-2h-2l-9-20-5-7v-2l5 2 8 4 8 8 5 10 13 21 8 11 3 4 3 5 10 9 10 11 3 6 5 3 7 7 10 7h9l13-3 9-5h2l2-4 8-10 6-10 3-2v-11l-6-18-8-11-4-3-3-7-3-6-5-4v-2l-3-1-5-10-5-5-8-11-2-1-2-7-6-10-3-7v-2h-2l-5-13-2-10-14-14-6-4-8-7-8-10-1-4 5 2 5 4 6 3 7 6 9 11 4 2 1-3h6v3l5 2 6 4 1 2 5 2 1 3 4 2 4 4 6 3 2 5h2l7 8 14 14 7 8 5 6 8 7 18 18 5 4 4 5 9 7 5 5 4 3v2l7 1 1 1h9l12-9 7-8 3-7h2l3-9 4-10h2l1-5h2l1-14-3-11-8-16-2-6-3-1-8-14v-2l-3-1-4-7-10-13-5-8-8-11-11-11v-2l-4-1-5-6-2-6-4-4-3-7-2-14-3-8-1-13h-2l-9-19v-3h-2l-6-10-4-11-1-10h3l3 9 3 1 8 14 2 2 3 9 6 13 3 7 1 13h2l1 3 1 11 7 14 9 7 8 10 6 5 4 6 2 6 8 7 7 6 2-3 3-10 5-9 3-3 6-12 1-4 2-1 7-15 1-3v-14l-2-4v-13l-2-24-1-43-4-8-5-5-4-6-13-11-5-3-5-6-6-3-5-5-4-2-1-2-3-1v-2h-3l-1-2-3-1v-2l-4-2-3-1-4-4-19-13-7-4-16-10-5-4-11-6-17-10-12-6-6-4-9-5-12-7-11-6-17-10-10-5-17-10-18-11-11-6-19-11-23-15-19-12-17-12-21-14-4-7-5-12-5-18v-11l1 3h2l3 13-1-15 3 4 5 17 3 3 4 8 12 13 8 7 13 11 6 4v2h3v2h3v2l4 1 12 8 11 7 21 12 24 13 5 2v2l9 3 6 5 17 8 11 6 10 4 22 12 13 7 7 3 16 9 5 2 5 4 10 4v2l5 2 10 6 1 2 8 4 5 4 12 5 10 8 10 7v2l5 1v2l5 1v2l4 1 7 5 5 5 15 13 11 12 8 13 3 11 1 15v42l5-1 4-8 7-9 9-9 10-16 8-13 3 1-1 8-7 14-9 15-3 7-10 13-13 13-2 4-1 7v10l3 3v9l-6 11-4 10-6 13-4 6v8l2 1h17l24-4 11-4 14-4 16-4 12-5 5-3 19-10 5-1v-2l4-3 7-3 13-8 22-13 9-5 5-3 10-4 4-1 2-4 12-7 64-32 16-6 21-9 16-6 13-5 25-10 33-11 32-8 22-3 7 2-1 4-4 1v2l-25 10-15 5h-3l-1 2-4 3 1 4 6 2 32-2 17-1 60-2 25-2 57-6 4-1 20-1 62-10 45-8h5v-2l28-6 10-2 28-6 20-2v-2l13-2 9-3 12-2v-2l20-6 8-3h5v-2l12-4h4v-2l11-5 20-8 8-4 14-6 15-7 15-8 12-5h2v-2l7-3 17-9 24-15 13-10h2v-2l11-9 12-11 17-17 9-8 12-12 7-4h2v-2l18-4v2l-5 1v2l-12 6-12 12-11 13-8 7-5 5-12 13-14 11-2 3-7 4-10 7-12 8-22 13-9 6-18 8-25 12-32 16-15 7-16 7-14 5-11 5-6 2-5 2-9 2-12 5-10 3-9 2h-4v2l-9 3-11 2-1 2-7 2-13 1-9 1v2l-13 2-20 4h-4v3h-7l-3 1-3-1v2h-5l-5 1-84 14-35 5-81 6-45 2-59 5-14 5-10 5-1 6 20 4 9 2 11 6 16 12 15 11 18 13 8 6 19 14 15 9 15 7 13 5 9 5 12 4 31 7 22 4 8 1h44l12-2 12-6 10-4 13-7 14-9 9-6 17-12 20-16 13-11 9-8 8-7 22-16 8-4 9-6 23-11 16-6 10-3 8-3 14-4 6-2 14-5 10-2 9-4h3v-2l18-4 13-5h2v-2l7-2 9-18 6-7 6-15 3-11v-14l-4-8-2-6-6-5v-2h3l1-3 4-1 8 4 5 11 1 18v14l-2 11-3 11v8l-1 2 12-4 7-4 10-4 13-5 10-3 1-1h6v-2l20-8 2-2 12-3v-2l9-4 6-3 7-1 1-2 9-4 12-5 11-6 10-4 4-3 1-5h-2l-1-4h-2l-2-7-3-28-2-10-3-26-2-23-2-20-1-2h-11l4-3 4-1 1-5-1-19-4-46v-60l1-27zm-802 421-34 9-46 13-9 2-7 3-7 2-12 5-8 2v2l-6 1-16 6-3 3-9 2-21 9v2l-6 2-13 7v2l-6 1-9 6-13 7-12 7-4 4-15 8-22 12-20 9-24 9-19 5-11 1h-32l2 8 11 16 12 20 2 7v24l-2 10-3 8-6 10v2l-4 2-6 8-6 5-1 3-14 4-10 2-6 2-16-3-1-3-9-5h-2v-2l-5-3-16-15-7-8-4-1-5 3-1 4-4 2-2 3 1 7 5 8 7 6 6 2 3 7 1 9-6 5-2 7-4 5-8 13-6 6v2l-6 2-7 7-11 5-23 2-5 8-3 7-8 7-10 9-10 5h-11l-13-3-12-2-7-3-9-3-4-4-6-2h-21l-7 1 1 9 3 7 2 6h2l3 10 4 8h2l2 7 1 2h2l2 6 6 7 14 9 12 9h2v2l10 5 11 6 17 10 34 18 14 7 7 3 12 5 12 6 11 4 5 3 16 6 4 2h3l1 3 16 6 33 13 27 10 37 13 22 7 29 7 36 8 17 4 19 3 20 4 25 4 10 1 2 1 14 1h59l45-2 34-2 14-2 1-4-4-12h-2l-1-7-4-10-3-13-5-22-5-21-7-45-4-26-1-3-3-44-3-37-1-10-1-32-4-36-1-1-1-10 5 1 3-3 2-10 2-25 2-31 3-35 4-37 6-36 5-33 3-8v-12l8-10 1-6-2-5 3-5v-4z" fill="#7F4B3E"/>
<path transform="translate(1511,1170)" d="m0 0h5l-1 9-8 22-15 32-10 23-12 23-9 15-7 11-13 22-10 15-3 5-2 3h-2l-2 6 5-1 12-11 8-8 5-9 11-18 4-12 5-10 6-8 7-12h2v-2l7-4 19-7 7-4 10-4 17-6 5-3 14-5 4-3 9-4 19-8 16-8h7l3 9v5l-4 8-8 7-8 10-11 18-2 5h-2l-2 5-7 11-3 1-2 5-10 13-6 7h-2l-2 5-3 4h-2l-2 4-16 16-16 14h-2l-1 3-12 9-24 16-14 7-10 6-12 7-11 6-23 12-34 15-29 11-37 13-20 7-37 15-18 8-11 6-9 8-6 10-3 16v24l-2 11-4 3-22 6-9 3-11 2-7 1-17-1-7-4-6-8-7-5-1-6 3-7v-10l-3-11-4-6-7-14-11-11-16-11-11-8-10-8-14-12-13-11-15-14-13-12v-2l-4-2-12-13-8-10-13-16-14-22-8-17-7-15-4-10-12-24-5-15-6-21-4-10-2-4v-9l2-2 6 1 13 8 28 15 12 6 15 6 12 5 22 7 26 6 13 2 16 2 22 1 40 1h179l44-2 24-2 6-2 7 2 3-1 17-1 18-5 10-4 13-3 8-1h3 9l12-25 13-32 3-10 1-2h2v-9l3-1 8-17 4-4z" fill="#CBD7DD"/>
<path transform="translate(0)" d="m0 0h772l2 6-1 1-37 4-39 4-63 8-36 6-48 9-58 12-39 9-25 6-14 4-23 6-13 4-12 3-8 3-37 12-15 5-10 4-23 8-12 5-15 6-15 7-10 6-8 4-20 12-8 5h-2v2l-5 3h-2v2l19-12 14-8 13-6h3v-2l14-3h6l3 3 11 1 1 3-24 10-20 9-25 13-24 15-17 9-21 21-7 8-6 7-5 5-11 14-9 14-4 4-8-5-2-5-28 2-44 5h-5z" fill="#F6F8F9"/>
<path transform="translate(1646,395)" d="m0 0h8l3 5v6h2l2 16 2 24 3 26 2 9 2 21 1 7h2l1 4h2v5l-7 5-9 4-16 8-7 3-5 2h-3l-1 3-9 2-10 5h-3v2l-12 4-6 4-13 5h-3v2l-12 3-13 5-11 5-20 8h-3v-10l4-14 1-8v-14l-1-18-5-11-9-3-3 3h-3l8 8 3 10 2 3v14l-5 16-5 12-7 8-6 12-4 4-5 1v2l-18 7-10 2h-5v2l-15 6-10 2-11 4-13 4-14 4-6 3-13 4-21 9-17 9-5 4-5 2-13 10-9 6-5 5-11 9-10 9-20 16-18 13-7 5-5 3-17 11-10 5-12 5-10 5-12 2h-44l-26-4-26-6-19-5-18-9-13-5-17-9-14-10-11-8-38-28-12-9-12-8-9-4-23-4-4-4 2-5 10-5 14-5 59-5 61-3 65-5 35-5 84-14 7-1 3 1v-2h5v-1l8 1v-3l24-5 3-1h10v-2l15-3h7l2 1 1-2 8-3 12-3 5-1v-2l6-2 14-3 14-5 4-2 9-2 3-2 9-3 13-5 15-6 12-5 46-23 31-15 10-4 6-4 20-12 11-7 19-13 4-1 2-4 11-9 10-9 5-6 5-5 11-10 11-14 8-7 10-6z" fill="#F6F8F9"/>
<path transform="translate(96,319)" d="m0 0 1 3h2l3 13-1-15 3 4 5 17 3 3 4 8 12 13 8 7 13 11 6 4v2h3v2h3v2l4 1 12 8 11 7 21 12 24 13 5 2v2l9 3 6 5 17 8 11 6 10 4 22 12 13 7 7 3 16 9 5 2 5 4 10 4v2l5 2 10 6 1 2 8 4 5 4 12 5 10 8 10 7v2l5 1v2l5 1v2l4 1 7 5 5 5 15 13 11 12 8 13 3 11 1 15v42l5-1 4-8 7-9 9-9 10-16 8-13 3 1-1 8-7 14-9 15-3 7-10 13-13 13-2 4-1 7v10l3 3v9l-6 11-4 10-6 13-4 6v8l2 1h17l24-4 11-4 14-4 16-4 12-5 5-3 19-10 5-1v-2l4-3 7-3 13-8 22-13 9-5 5-3 10-4 4-1 2-4 12-7 64-32 16-6 21-9 16-6 13-5 25-10 33-11 32-8 22-3 7 2-1 4-4 1v2l-25 10-15 5h-3l-1 2-4 3 1 4 6 2 32-2 17-1 60-2 25-2 57-6 4-1 20-1 62-10 45-8h5v-2l28-6 10-2 28-6 20-2v-2l13-2 9-3 12-2v-2l20-6 8-3h5v-2l12-4h4v-2l11-5 20-8 8-4 14-6 15-7 15-8 12-5h2v-2l7-3 17-9 24-15 13-10h2v-2l11-9 12-11 17-17 9-8 12-12 7-4h2v-2l18-4v2l-5 1v2l-12 6-12 12-11 13-8 7-5 5-12 13-14 11-2 3-7 4-10 7-12 8-22 13-9 6-18 8-25 12-32 16-15 7-16 7-14 5-11 5-6 2-5 2-9 2-12 5-10 3-9 2h-4v2l-9 3-11 2-1 2-7 2-13 1-9 1v2l-13 2-20 4h-4v3h-7l-3 1-3-1v2h-5l-5 1-84 14-35 5-81 6-45 2-59 5-14 5-10 5-1 6 20 4v1h-22l-9 2-8 6-4 6 1 5v7l-4 16-10 61-6 52-4 51-2 50v66l1 13 1 35 2 31 6 45 6 34 4 19 1 8 3 8 9 37v7l-2-4-5-13-3-13-5-22-5-21-7-45-4-26-1-3-3-44-3-37-1-10-1-32-4-36-1-1v-10h5l3-5 3-29 1-23 3-38 5-45 6-36 5-33 3-8v-12l8-10 1-6-2-5 3-5 1-4h-7l-34 9-46 13-9 2-7 3-7 2-12 5-8 1v2l-17 6-5 1-1 3-13 4-17 7h-2v2l-17 9h-2v2l-7 3-11 7-10 5-10 6h-2l-1 3-18 10-22 12-20 9-24 9-19 5-11 1h-19l-13-1 4 10 9 12 13 22 2 7v24l-2 10-3 8-7 12-5 5-5 6-5 4-2 4-14 4-10 2-6 2-16-4-3-3-9-5v-2l-4-1-17-16-7-8-4-1-5 2-1 4-5 5 1 7 4 6v2l4 2 3 3 6 2 3 4 2 7v6l-6 5-2 7-4 5-8 13-7 8-8 5-5 5-11 5-23 2-5 9-2 5-10 9-9 8-10 5h-11l-13-3-12-2-7-3-9-3-4-4-6-2h-28l2 9 3 7 1 6h2l7 16 3 9 7 11 8 7 9 6 12 12-5-1-2-1h-6l-1 5 2 2 3 2 3 10 4 4 1 10h-3l-7-12v-2h-2l-3-11v-2l-5-5-7-10-7-11v-2l-4-2-6-11v-2h-2l-1-6h-2l-4-11-5-10-4-10-4-11-3-7-3-4-4-10-2-9-6-12-2-2-3-7-3-6v-2h-2l-6-15v-5h3l7 10 5 8 1 6h2l6 10 8 6 9 4 15 11 17 12 13 8 14 8 21 8 13 3 5-1 10-9 4-4h2l8-16v-7l-3-5-13-10-11-8-8-8-9-11-10-15-8-17-3-5v-2h-2l-9-20-5-7v-2l5 2 8 4 8 8 5 10 13 21 8 11 3 4 3 5 10 9 10 11 3 6 5 3 7 7 10 7h9l13-3 9-5h2l2-4 8-10 6-10 3-2v-11l-6-18-8-11-4-3-3-7-3-6-5-4v-2l-3-1-5-10-5-5-8-11-2-1-2-7-6-10-3-7v-2h-2l-5-13-2-10-14-14-6-4-8-7-8-10-1-4 5 2 5 4 6 3 7 6 9 11 4 2 1-3h6v3l5 2 6 4 1 2 5 2 1 3 4 2 4 4 6 3 2 5h2l7 8 14 14 7 8 5 6 8 7 18 18 5 4 4 5 9 7 5 5 4 3v2l7 1 1 1h9l12-9 7-8 3-7h2l3-9 4-10h2l1-5h2l1-14-3-11-8-16-2-6-3-1-8-14v-2l-3-1-4-7-10-13-5-8-8-11-11-11v-2l-4-1-5-6-2-6-4-4-3-7-2-14-3-8-1-13h-2l-9-19v-3h-2l-6-10-4-11-1-10h3l3 9 3 1 8 14 2 2 3 9 6 13 3 7 1 13h2l1 3 1 11 7 14 9 7 8 10 6 5 4 6 2 6 8 7 7 6 2-3 3-10 5-9 3-3 6-12 1-4 2-1 7-15 1-3v-14l-2-4v-13l-2-24-1-43-4-8-5-5-4-6-13-11-5-3-5-6-6-3-5-5-4-2-1-2-3-1v-2h-3l-1-2-3-1v-2l-4-2-3-1-4-4-19-13-7-4-16-10-5-4-11-6-17-10-12-6-6-4-9-5-12-7-11-6-17-10-10-5-17-10-18-11-11-6-19-11-23-15-19-12-17-12-21-14-4-7-5-12-5-18z" fill="#251413"/>
<path transform="translate(869,662)" d="m0 0h16l12 1 14 7 16 12 15 11 18 13 8 6 15 11 1 4 3 7 9 4 8 5 17 8v2l5 2-1 3-4-3-10-3-6-4-5-2-6-4-5-2-18-11-11-8-24-15-10-7-23-15-13-8-10-3h-9l-6 10-3 16-3 24-10 48-5 32-2 15-1 1-1 10-1 22-3 34-2 20-1 31v48l3 62 1 6 1 22 2 13 7 46 6 28 5 21 1 9 2 5 9 36 6 8v13l2 10 10 30 7 15 5 12 11 24 8 17v2h2l6 13v2h2l4 8 6 11v2h2l8 15 7 10 5 10 5 6v2h2l2 7 3 1v3l4 2 12 14 10 10 4 2 5 5 8 7 15 9 24 9 14 4 6 3v2l5 1v2l6 2 8 7 7 10 6 15 4 19v12l7-2 26-3 11-2 19-2 11-2 45-5 2-1 19-2 13-2 36-5 26-3 17-3 16-2 22-4h11l-1 3-7 4-18 5-9 2-14 3-36 6-10 2-64 8-1 1-22 2-15 2-29 3-19 1-16 3h-17l4 24 6 21 8 26 7 20 10 25 5 8v3h2l3 3 3 1h13l29-3 45-7 39-7 15-1v-2l20-3 9-3 25-5 10-1 6-2 29-5 12-1 7-2 22-1 1-1 9-1h23l1 4-4 3-22 6-67 11-99 18-39 6-31 4h-7v2l-8 1h-43l-9-7-5-2-4-4-6-15-10-28-7-27-11-51-3-21-7-19-4-10-6-10-7-9-10-6-16-8-24-9-11-3-11-6-10-7-14-14-13-17-11-17-2-3v-3h-2l-10-16-14-22-10-18-9-16-11-23-10-21-10-23-9-24-3-7-1-10-3-10-1-2-17 2-9 2-43 3h-84l-26-2-27-5-13-3-9-2-15-2-15-4-9-2-21-5-16-5-27-8-25-7-8-3-17-6-12-5-7-3-17-6-12-5-30-12-9-3-8-4-10-4-12-5-10-2-13-5-10-5-17-10-19-9v-2l-6-2-21-12-9-4-7-3-8-2 1 8 9 12 1 5 1 14 1 5-5 13-6 9-7 4-14 1-16-6-13-11-7-7-2-1-2-6-10-14-3-5-8-13-2-1-3-6v-2h-2l-4-8-7-10-6-11-7-10-6-10-10-15-2-5h-2l-2-5-5-5-7-12-5-5-1-5-3-1-9-12-4-5-2-6-4-1-4-6v-3l-3-1-3-5v-2l-4-2-4-7-6-7-4-7-10-14-7-10-12-18-8-11-7-8v-22l6 5 9 13 15 23 21 31 7 10 3 3v3h2l5 8v2h2l1 4h2l3 5v2h2l1 4h2l6 11 2 1 4 7 6 9v2h2l5 8v2h2l3 5v2h2l4 7 3 2v3h2l4 7 2 1v2h2l8 13 4 7 6 8v2l3 1 1 5h2l7 11v3l3 1v3l3 1 1 3 3 2 5 9 3 3 4 7 4 6 3 2 4 7 3 2 3 5 1 4 4 2 7 7 7 8 3 3 6 1h11l1-6-1-16-9-21-2-5h-2l-3-11-7-12-1-6h-2l-6-9-3-6 1-3 6 10 8 12 5 5 1 4 2 10h2l8 14h1l-1-10-4-4-3-10-4-2-1-4 2-4h6l4 1-11-11-11-7-8-9-6-11v-3h2l3 9h2l5 8 5 5 12 8 14 10v2l5 1 12 7 9 5 21 12 39 20 7 3 12 5 12 6 11 4 5 3 16 6 7 3 1 2 16 6 33 13 27 10 37 13 22 7 29 7 36 8 17 4 19 3 20 4 25 4 10 1 2 1 14 1h59l45-2 34-2 14-2-2-10-2-5-4-20-8-31-1-1-3-18-7-36-6-43-2-22-1-18-1-35-1-13v-66l2-50 4-51 6-52 11-67 3-10v-7l-1-5 5-7 8-6z" fill="#6E6B68"/>
<path transform="translate(849,645)" d="m0 0 7 1-1 6-2 5 2 3-1 6-8 10v12l-3 8-12 78-5 48-2 26-2 36-2 16-3 5-3 1-3-1 1 10 1 1 4 39 1 30 2 21 2 28 3 41 2 10 7 43 4 26 8 32 2 12 4 12 3 8v4h2v8l-2 7-44 3h-31l-2-4v-20l3-62 3-43 3-39 3-47 3-46 1-7 4-59 1-12v-28l-4-21-6-21-5-20-3-8-5-21-3-10-3-14-2-6-2-14-3-13-2-12-12-21 1-5 6-8 2-8 21-7 36-10z" fill="#F6F8F9"/>
<path transform="translate(1646,395)" d="m0 0h8l3 5v6h2l2 16 2 24 3 26 2 9 2 21 1 7h2l1 4h2v5l-7 5-9 4-16 8-7 3-5 2h-3l-1 3-9 2-10 5h-3v2l-12 4-6 4-13 5h-3v2l-12 3-13 5-11 5-20 8h-3v-10l4-14 1-8v-14l-1-18-5-11-9-3-3 3h-3l8 8 3 10 2 3v14l-5 16-5 12-7 8-6 12-4 4-5 1v2l-18 7-10 2h-5v2l-15 6-10 2-11 4-13 4-14 4-6 3-13 4-21 9-17 9-5 4-2-1-3-3 1-5 10-8 8-2 10 1 3-3 7-2 9-3 8-4 9-1 8-3h5l1-3 6-3 9-2 15-7 9-1 2 2 2-2h3v-2l7-1 3-2h4v-2l7-3 12-2 10-4 4-10 6-12 7-8 3-8 2-11v-13l-4-13-7-9v-2l-4-2 11-6 9-6 17-10 15-10 11-8h3l2-4 11-9 10-9 5-6 5-5 11-10 11-14 8-7 10-6z" fill="#FAD8BE"/>
<path transform="translate(1636,394)" d="m0 0 1 2-5 1v2l-12 6-12 12-11 13-8 7-5 5-12 13-14 11-2 3-7 4-10 7-12 8-22 13-9 6-18 8-25 12-32 16-15 7-16 7-14 5-11 5-6 2-5 2-9 2-12 5-10 3-9 2h-4v2l-9 3-11 2-1 2-7 2-13 1-9 1v2l-13 2-20 4h-4v3h-7l-3 1-3-1v2h-5l-5 1-84 14-35 5-81 6-45 2-59 5-14 5-10 5-1 6 20 4v1h-22l-9 2-8 6-4 6 1 5v7l-4 16-10 61-6 52-4 51-2 50v66l1 13 1 35 2 31 6 45 6 34 4 19 1 8 3 8 9 37v7l-2-4-5-13-3-13-5-22-5-21-7-45-4-26-1-3-3-44-3-37-1-10-1-32-4-36-1-1v-10h5l3-5 3-29 1-23 3-38 5-45 6-36 5-33 3-8v-12l8-10 1-6-2-5 3-5 1-4h-7l-34 9-46 13-2-1 10-4 11-3 7-3 9-3 20-6 12-1v-2l19-4h6l2 1-1 7-1 3 5-2 14-10 16-4 3-1v-2h2v-2l-23 1-13 2-2 1-12 1-9 2-53 10-15 4-21 6-12 3v-3l-8 3-1 3-8 4-12 4-32 16-4 1 5-5 15-8 40-20 21-10 20-8 17-7 20-8 16-6 15-6 33-11 32-8 22-3 7 2-1 4-4 1v2l-25 10-15 5h-3l-1 2-4 3 1 4 6 2 32-2 17-1 60-2 25-2 57-6 4-1 20-1 62-10 45-8h5v-2l28-6 10-2 28-6 20-2v-2l13-2 9-3 12-2v-2l20-6 8-3h5v-2l12-4h4v-2l11-5 20-8 8-4 14-6 15-7 15-8 12-5h2v-2l7-3 17-9 24-15 13-10h2v-2l11-9 12-11 17-17 9-8 12-12 7-4h2v-2z" fill="#726C69"/>
<path transform="translate(2047,505)" d="m0 0h1v24l-7 6-7 8-8 9-12 9-7 8-9 10-1 2h-2l-2 4-5 6h-2l-2 4-7 7-7 8-6 7h-2l-2 4-12 14-4 6-6 8-8 16-4 9-9 28-6 21-6 12-5 8h-2l-2 4-12 12-6 5h-2v2l-5 2v2l-10 7h-2v2l-6 4h-2l-1 3-5 3h-2v2l-11 8-13 12-21 21-6 8-22 28-4 4-3 5-5 6h-2l-2 5-4 4-6 7-9 11-41 41-8 7-13 11-10 8-14 11-5 2-4 8 3 14v165l-2 47-4 36-5 28-9 37-4 15-3 9-3 11-4 10-9 27-4 10-5 15-5 14-4 10-5 12-4 10-5 12-10 27-6 19-6 23-1 5-1 15v24l3 27 7 32 1 8v14l-5 1-3-2-3-7-1-10-3-13-5-38-1-4v-36l3-19 2-7 1-10 3-6 2-10 4-14 4-10 17-43 14-35 5-13 3-8 6-15 8-24 11-44 7-36 5-38 2-27 1-27v-74l-2-96-5-1-17 10-4 2h-5v2l-11 4-9 3-8 1h-14v-1l11-1 13-5v-2l-6 2-4-1 6-3 9-3 8-4 13-4 10-7 9-5 3 1 9-6 8-6 11-8 13-10v-2l-3 2-3-1 5-5h2v-2l5-3 23-23 1-2h2l2-6 20-20 7-8 13-15 12-14 9-10 7-9 9-10 9-11 7-9 9-10 12-12 11-9 14-12 13-10 16-12 15-14 9-14 6-13 4-13 5-16 5-12 6-15 11-20 10-15 8-10 11-13 9-10 7-8 11-12 7-8 13-15 9-10 7-8 12-12 7-8z" fill="#3C1E1A"/>
<path transform="translate(1651,224)" d="m0 0h2l1 37 2 22 3 16 2 16 3 36 1 6 3 39 5 30 5 44 2 34 3 8h6l15-7 19-11 12-8 6-5 8-11 3-5 9-16 6-9 6-11 8-12 6-11 2-1 3-7 2-1 3-8 3-4 3-8h2l2-6 7-16 9-19 8-19 4-12 7-20 6-16 4-8 3 3v12l-8 28-4 9-4 10-4 13-4 9-6 16-8 15h-2l-2 8-7 12h-2l-1 5h-2l-1 6-2 1-3 7-4 6h-2l-1 5-5 8-4 4-2 5-7 9-1 3h-2l-3 10-5 10-2 1-2 5-6 5-1 2h-2l-1 3-7 3-8 6-17 11-11 7-8 4-13 8-19 9-6 3-11 6-6 2-7 4-8 4-13 5-10 4-12 5-7 3-12 5-6 3-6 2-16 6h-3v2l-12 5-7 3-8 2-15 4h-2v2l-16 6-11 3-13 5-12 3-4 2-12 2-21 6-16 5-14 5-8 2-12 5h-3v2l-4 2h-3l-1 3-10 5h-2l-1 4-9 4-11 8-11 9-6 5h-2l-1 3-13 9-5 5-4 2-2 4-26 20-8 4-18 12-15 7-5 2-12 2-3-3 16-8 3-1 1-3 16-10 9-6 17-12 20-16 13-11 9-8 8-7 22-16 8-4 9-6 23-11 16-6 10-3 8-3 14-4 6-2 14-5 10-2 9-4h3v-2l18-4 13-5h2v-2l7-2 9-18 6-7 6-15 3-11v-14l-4-8-2-6-6-5v-2h3l1-3 4-1 8 4 5 11 1 18v14l-2 11-3 11v8l-1 2 12-4 7-4 10-4 13-5 10-3 1-1h6v-2l20-8 2-2 12-3v-2l9-4 6-3 7-1 1-2 9-4 12-5 11-6 10-4 4-3 1-5h-2l-1-4h-2l-2-7-3-28-2-10-3-26-2-23-2-20-1-2h-11l4-3 4-1 1-5-1-19-4-46v-60l1-27z" fill="#49302C"/>
<path transform="translate(896,1329)" d="m0 0h2l1 4h2l2 5 2 8 14 28 4 4-3-4 1-3 4 4 3 7 7 7 4 8v2h2l8 15 7 10 5 10 5 6v2h2l2 7 3 1v3l4 2 12 14 10 10 4 2 5 5 8 7 15 9 24 9 14 4 6 3v2l5 1v2l6 2 8 7 7 10 6 15 4 19v12l7-2 26-3 11-2 19-2 11-2 45-5 2-1 19-2 13-2 36-5 26-3 17-3 16-2 22-4h11l-1 3-7 4-18 5-9 2-14 3-36 6-10 2-64 8-1 1-22 2-15 2-29 3-19 1-16 3h-17l4 24 6 21 8 26 7 20 10 25 5 8v3h2l3 3 3 1h13l29-3 45-7 39-7 15-1v-2l20-3 9-3 25-5 10-1 6-2 29-5 12-1 7-2 22-1 1-1 9-1h23l1 4-4 3-22 6-67 11-99 18-39 6-31 4h-7v2l-8 1h-43l-9-7-5-2-4-4-6-15-10-28-7-27-11-51-3-21-7-19-4-10-6-10-7-9-10-6-16-8-24-9-11-3-11-6-10-7-14-14-13-17-11-17-2-3v-3h-2l-10-16-14-22-10-18-9-16-11-23-3-11z" fill="#3E2C2B"/>
<path transform="translate(1047,770)" d="m0 0 14 3 18 5 30 6 25 3 7 3 8 13 7 15-1 10v10l2 6v8h2l9 21 10 19 7 11 5 8 1 12-5 3-8 3h-8l-9-4-19-7-17-9-16-12-7-11-9-13-10-21-6-10-8-16-6-10-7-16-6-9-4-13-2-6z" fill="#F7F9FA"/>
<path transform="translate(1767,873)" d="m0 0 7 4 17 47 10 30 13 47 6 27 5 35 2 19 4 56 4 40 13 90 4 36 2 14 4 37 8 52 5 29 6 28 4 18 9 44 5 25 7 37 2 7 2 22 1 3 4 55v55l-2 39-2 31-2 24-5 2 1 5-4 1-2-4v-27l4-67v-69l-1-19-5-38-8-45-5-25-10-51-4-18-2-10-2-7-2-16-7-40-8-57-8-53-4-30-4-25-1-12-2-10-6-56-5-53-5-37v-8h-2l-6-36-9-39-6-24-6-26-4-17-7-19-2-8z" fill="#4C3E3D"/>
<path transform="translate(869,662)" d="m0 0h16l12 1 14 7 16 12 15 11 18 13 8 6 15 11 1 4 3 7 9 4 8 5 17 8v2l5 2-1 3-4-3-10-3-6-4-5-2-6-4-5-2-18-11-11-8-24-15-10-7-23-15-13-8-10-3h-9l-6 10-3 16-3 24-10 48-5 32-2 15-1 1-1 10-1 22-3 34-2 20-1 31v48l3 62 1 6 1 22 2 13 7 46 6 28 5 21 1 9 2 5 9 36 6 8v13l2 10 10 30 7 15 5 12 11 24 8 17v2h2l6 13v2h2l3 6-1 2-4-4-2-3v-4l-3-1 1 4-3-1-5-8-8-18-4-7-2-11h-2l-1-4h-2l3 7v5l-2-2-7-15-10-23-9-24-3-7-1-10-3-10-1-2-17 2-9 2-43 3h-84l-26-2-27-5v-1l11 1 22 3 34 1h61l21-2 6-1 26-2 8-2 17-1h11l-2-6-5-1-7 1-1-7-3-9-4-20-8-31-1-1-3-18-7-36-6-43-2-22-1-18-1-35-1-13v-66l2-50 4-51 6-52 11-67 3-10v-7l-1-5 5-7 8-6z" fill="#63423C"/>
<path transform="translate(548,1221)" d="m0 0 11 3 16 5 21 5 13 3 16 4 10 1 9 2 13 3 27 5 26 2h84l43-3 16-3 10-1 4 8 2 11-1 4h-21l-10 1-43 2-37 2-2 1-97 4h-135l-9-2-8-4-3-2v-2h23l2-3 10-3 1-3-5-1 3-3 5-1 4-1v-2l-4-2-2-2-6-1-2-3-14-4-3-4 7 1 4 2h5v-2h-5l-2-2-1-5 6 1v2l6-1 3 4 5 1 3-1-2-2 4-2 1-4-9 1-7 1-3-1 2-5 4-1v2l7 1-2-1 2-4 6 2z" fill="#919896"/>
<path transform="translate(96,319)" d="m0 0 1 3h2l3 13-1-15 3 4 5 17 3 3 4 8 12 13 8 7 13 11 6 4v2h3v2h3v2l4 1 12 8 11 7 21 12 24 13 5 2v2l9 3 6 5 17 8 11 6 10 4 22 12 13 7 7 3 16 9 5 2 5 4 10 4v2l5 2 10 6 1 2 8 4 5 4 12 5 10 8 10 7v2l5 1v2l5 1v2l4 1 7 5 5 5 15 13 11 12 8 13 3 11 1 15v42l5-1 4-8 7-9 9-9 10-16 8-13 3 1-1 8-7 14-9 15-3 7-10 13-13 13-2 4-1 7v10l3 3v9l-6 11-4 10-4 9h-2v2h-2l-1 4-4 2-5 17-3 3-4 1-1-6 1-8 3-6 4-12 5-10 1-4 2-1 7-15 1-3v-14l-2-4v-13l-2-24-1-43-4-8-5-5-4-6-13-11-5-3-5-6-6-3-5-5-4-2-1-2-3-1v-2h-3l-1-2-3-1v-2l-4-2-3-1-4-4-19-13-7-4-16-10-5-4-11-6-17-10-12-6-6-4-9-5-12-7-11-6-17-10-10-5-17-10-18-11-11-6-19-11-23-15-19-12-17-12-21-14-4-7-5-12-5-18z" fill="#361714"/>
<path transform="translate(1741,917)" d="m0 0 4 1 12 24v3l3 1 13 32 10 28 7 24 9 48 4 21 3 26 2 9 4 3h2l2-3-2-26-2-19-1-5 1-7h1l5 42 6 64 4 34 1 2 2 18 6 40v9h-1l-4-26-2-6-4-24-3-8v-3h-2l-2-4-1 8-1 13v25l3 32 4 25 5 28 6 31 10 52 7 39 9 54v10l-1 2h-2l-2-7-3-3-8-33-5-25-2-13-8-35-10-51-2-13v-6h-2l-7-48-3-25-2-22-3-40-2-18-3-42-3-34-3-29-3-24-5-35-10-35-5-13-13-34-8-17-5-11z" fill="#919896"/>
<path transform="translate(772)" d="m0 0h216l14 4 15 3 45 5 56 7 69 9 63 10 49 9 38 9 21 7 19 4 12 5 3 2v3l-13-1-30-6-39-9-61-12-60-10-79-11-37-4-53-5-34-2-35-1-59-1h-61l-30 1-44 3-30 3h-9v-1l29-4 17-3 14-2 5-2h3v-2l-6 1-21 1-2-2 16-2z" fill="#97C4C7"/>
<path transform="translate(880,1378)" d="m0 0 3 1-1 8-6 12-10 16-7 13-6 10-8 15-5 7-3 6h-2v3h-2v3h-2l-1 5h-2l-1 5h-2v3h-2v3h-2l-3 9-3 5h-2l-1 5-1 2h-2l-1 4-2 4h-2l-1 4-6 10h-2l-2 6-13 20-5 8h-2l-1 5h-2l-1 4-10 14-10 15-9 16-11 19-4 6-4 5-3 4h-2l1-10 8-15 3-6 9-15 5-9 20-32 1-3h2l2-6 2-3h2l1-5 7-12h2l2-6 5-5 1-3h2l1-5 4-5 4-6 2-5 3-5 5-7 4-7 4-6h2l1-5h2l3-10 9-13h2l2-6 4-8-3 1-2 4-4 2-2 4-5 3-7 8-16 14-9 7-12 8-12 9-8 5h-2v2l-22 14-4 2h-3v2l-19 12-16 9h-3v2l-7 4h-3v2l-24 13-12 7-9 3v2h-4v2l-16 8-12 5-10 5-8 2v2l-16 6-9 4-12 6h-4v2l-6 1v2l-10 3v2l-10 4-13 4h-4v-2l5-3 6-4h2v-2l5-2 4-2v-2l7-5 5-2 8-4 10-6 6-5 9-3 6-3 10-6 29-15 10-4 6-3 5-1v-2l6-3 7-1v-2l20-9h2l1-3 41-20 23-13 19-12 7-4 8-5h2v-2l13-10 6-2 2-4 8-5 3-5 11-10 7-5 4-4h2l2-5 7-7 6-8 2-5 5-4h2v-2l9-6 2-2 2-5 8-11z" fill="#60423D"/>
<path transform="translate(1639,995)" d="m0 0 1 3 3 14v165l-2 47-4 36-5 28-9 37-4 15-3 9-3 11-4 10-9 27-4 10-5 15-5 14-4 10-5 12-4 10-5 12-10 27-6 19-6 23-1 5-1 15v24l3 27 7 32 1 8v14l-5 1-3-2-3-7-1-10-3-13-5-38-1-4v-36l3-19 2-7 1-10 3-6 2-10 4-14 4-10 17-43 14-35 5-13 3-8 6-15 8-24 11-44 7-36 5-38 2-27 1-27v-74l-2-96-4-2 2-5 7-5z" fill="#483B3C"/>
<path transform="translate(1040,768)" d="m0 0h9l9 3v1l-11-1-2 2 5 14 3 7 7 12 4 10 8 13 8 17 8 14 8 16 7 10 7 11 17 12 17 9 17 6 9 4h8l12-5-1-12-5-8-9-15-11-21-5-12v-3h-2l-2-11-1-3v-10l1-10-9-19-6-9-6-2-17-2v-1h10l16 2 3 3 11 23 1 2v25l5 14v2h3l11 23 4 7 9 19 3 12v9l-11 6-8 6v4l8-3 10-7 4 2 7 17 7 3 1 3-6 5-10 2-8 1-1 1h-10l-13-1 1 2 10 3 15 3h16l21-2 20-4h20l9-4 4-3h3v2l4 2v2l22 1 5 1v1l-36-1-9 4-7 1-24 1-24 3h-26l-23-5-17-6-26-13 3-1-3-5 3-1-6-5-5-5-13-11-10-10-10-14-10-15-6-16-6-15-7-16-7-22v-10l3 3 11 20 3 4 3 7 13 27 2 4v3h2l4 9 6 9 10 14 6 7 6 3 4 5 9 6 10 5 3 1v-2l6 2 7 6 5 1-4-8-6-5v-2l-6-2-20-11-3-2v-2h-3v-2l-4-2-7-8-7-10-9-15-13-25-9-17-8-13-8-16-6-14-4-12z" fill="#C59E88"/>
<path transform="translate(1503,509)" d="m0 0 9 3 6 12 1 18v14l-2 11-3 11v8l-1 2 12-4 7-4 10-4 13-5 10-3 1-1h6v-2l20-8 2-2 12-3v-2l5-1-1 2h-2v2h5l1 3-4 3-5 1-1 3 10-5 11-2-1 2-13 5-10 4-12 5-7 3-12 5-6 3-6 2-16 6h-3v2l-12 5-7 3-8 2-15 4h-2v2l-16 6-11 3-13 5-12 3-4 2-12 2-21 6-16 5-14 5-8 2-12 5h-3v2l-4 2h-3l-1 3-10 5h-2l-1 4-9 4-11 8-11 9-6 5h-2l-1 3-13 9-5 5-4 2-2 4-26 20-8 4-18 12-15 7-5 2-12 2-3-3 16-8 3-1 1-3 16-10 9-6 17-12 20-16 13-11 9-8 8-7 22-16 8-4 9-6 23-11 16-6 10-3 8-3 14-4 6-2 14-5 10-2 9-4h3v-2l18-4 13-5h2v-2l7-2 9-18 6-7 6-15 3-11v-14l-4-8-2-6-6-5v-2h3l1-3z" fill="#381A17"/>
<path transform="translate(221,866)" d="m0 0 5 2 8 4 8 8 5 10 13 21 8 11 3 4 3 5 10 9 10 11 3 6 5 3 7 7 10 7h9l13-3 9-5h2l2-4 8-10 6-10 3-2v-11l-6-18-8-11-4-3 1-4 9 11 5 7 5 15 4 7 6-7-2-9-9-7-6-5 1-4 1 3 4 2 3 3 6 2 3 4 2 7v6l-6 5-2 7-4 5-8 13-7 8-8 5-5 5-11 5-23 2-5 9-2 5-10 9-9 8-10 5h-11l-13-3-12-2-7-3-9-3-4-4-6-2h-28l2 9 3 7 1 6h2l7 16 3 9 7 11 8 7 9 6 12 12-5-1-2-1h-6l-1 5 2 2 3 2 3 10 4 4 1 10h-3l-7-12v-2h-2l-3-11v-2l-5-5-7-10-7-11v-2l-4-2-6-11v-2h-2l-1-6h-2l-4-11-5-10-4-10-4-11-3-7-3-4-4-10-2-9-6-12-2-2-3-7-3-6v-2h-2l-6-15v-5h3l7 10 5 8 1 6h2l6 10 8 6 9 4 15 11 17 12 13 8 14 8 21 8 13 3 5-1 10-9 4-4h2l8-16v-7l-3-5-13-10-11-8-8-8-9-11-10-15-8-17-3-5v-2h-2l-9-20-5-7z" fill="#7B4E43"/>
<path transform="translate(1161,1841)" d="m0 0 7 1 24 7 74 21 36 9 32 7 55 9 10 2 50 8 37 4 30 1h74l34-2 38-5 29-5 32-7 25-6 21-6 17-6 4 1-13 6-15 6-37 12-42 12-41 7-44 6-18 2-22 2h-64l-1-2-21-4-49-8-87-19-47-11-41-11-65-22-22-8z" fill="#97C3C7"/>
<path transform="translate(157,1152)" d="m0 0 2 3 13 35 9 25 15 44 13 43 8 28 18 65 11 38 9 29 11 30 10 24 8 16 8 14 4 8 7 11 6 7 9 11 8 10 8 7 14 11 13 11 9 7 16 13 20 15 19 13 10 7 2 5 3 2v2l5 2 2 3-5-1-20-11-5-4h2l-6-7-2-1v-2l-7 2v-2l-4-1-2-2-1-2-5-2-2-1v-2l-5-2-13-11-14-12-22-22-8-7-10-9-11-9-13-12-11-13-9-13-11-17-12-25-9-27-10-39-15-57-12-43-1-7 2 3 1 6 1-5-1-2-2-15-6-27-5-21-3-8-3-15-2-4-2-9-3-7-6-21-7-18-6-17-6-15z" fill="#99C4C8"/>
<path transform="translate(1636,394)" d="m0 0 1 2-5 1v2l-12 6-12 12-11 13-8 7-5 5-12 13-14 11-2 3-7 4-10 7-12 8-22 13-9 6-18 8-25 12-32 16-15 7-16 7-14 5-11 5-6 2-5 2-9 2-12 5-10 3-9 2-25 6-5 2-26 5-40 8h-6v2l-31 6h-14v-2l5-2 2-2 2 1-1-2h-2l-1-4 1-1 17-3 56-11h4v-2l23-5 20-3 9-3h4v-2l13-2 9-3 12-2v-2l20-6 8-3h5v-2l12-4h4v-2l11-5 20-8 8-4 14-6 15-7 15-8 12-5h2v-2l7-3 17-9 24-15 13-10h2v-2l11-9 12-11 17-17 9-8 12-12 7-4h2v-2z" fill="#1F1211"/>
<path transform="translate(1826,1194)" d="m0 0 2 4 3 11 6 43 2 18 2 11 7 49 4 23 5 40 9 49 5 27 1 1v9h2l4 21v-8l-6-26-3-17v-6l3 3v7h2l3 11 4 18 9 44 5 25 7 37 2 7 2 22 1 3 4 55v55l-2 39-2 31-2 24-5 2 1 5-4 1-2-4v-27l4-67v-69l-1-19-5-38-8-45-5-25-10-51-4-18-2-10-2-7-2-16-7-40-8-57-8-53-4-30-4-25-1-12-2-10z" fill="#3D2523"/>
<path transform="translate(1701,928)" d="m0 0 2 1-1 2h-2l-2 4-24 24h-3v2l-6 5 5-2 2-1-2 5-14 11-10 7-12 9-6 3v-2l-16 9-5 4-15 5-10 5-10 3 5-1 4-1 2 2-4 3-11 4 3 2-7 1-14-2-14-4-15-5-30-13-15-4-14-2-27-6-23-7-12-6-14-5-73-9-5-1-22-2-5-6 1-5 10-2 21-2 34-8 30-5 11-1h9v1l-17 4-19 3-5 2-18 2v2l-9 3 4 2v3h11l16 2 12 2 14 4 3 2 15-1 17-3h11v-2l26-5 19-6 9-3h3v2l6-1-2 4-15 8-17 4-5 2-18 3-21 5-3 2 1 4 10 3 9 1 9 3 31 5h22l14-5 8-2 3-1-1 3-8 4-8 3-1 5 4 3 6 2 2 4 4 1 7 3 14 4 8 3h20v-2l11-4h6v-2l8-3 26-13h2v-2l6-2v-2l5-2v-2l5-3h2v-2l5-3h2v-2l6-4 7-6 10-8 5-5 8-7 7-7 8-7 2-3h2z" fill="#61413B"/>
<path transform="translate(827,941)" d="m0 0h4l1 76 2 16 3 19 1 22 2 13 7 46 6 28 5 21 1 9 2 5 9 36 6 8v13l2 10 10 30 7 15 5 12 11 24 8 17v2h2l6 13v2h2l3 6-1 2-4-4-2-3v-4l-3-1 1 4-3-1-5-8-8-18-4-7-2-11h-2l-1-4h-2l3 7v5l-2-2-7-15-10-23-9-24-3-7-1-10-3-10-1-2-17 2-9 2-43 3h-84l-26-2-27-5v-1l11 1 22 3 34 1h61l21-2 6-1 26-2 8-2 17-1h11l-2-6-5-1-7 1-1-7-3-9-4-20-8-31-1-1-3-18-7-36-6-43-2-22-1-18v-89z" fill="#483838"/>
<path transform="translate(388,519)" d="m0 0 5 2 5 4 12 5 10 8 10 7v2l5 1v2l5 1v2l4 1 7 5 5 5 15 13 11 12 8 13 3 11 1 15v42l5-1 4-8 7-9 9-9 10-16 8-13 3 1-1 8-7 14-9 15-3 7-10 13-13 13-2 4-1 7v10l3 3v9l-6 11-4 10-4 9h-2v2h-2l-1 4-4 2-5 17-3 3-4 1-1-6 1-8 3-6 4-12 5-10 1-4 2-1 7-15 1-3v-14l-2-4v-13l-2-24-1-43-4-8-5-5-4-6-13-11-5-3-5-6-6-3-5-5-4-2-1-2-3-1v-2h-3l-1-2-3-1v-2l-4-2-3-1-8-8 5 2 15 10 11 8 14 11v-1l-10-8-1-3h-2v-3l-5-2-3-3-3-2 1-1h-3v-2l-6-2-2-4 2-2h3l-3-1-1-2-4 1-4-2v-2l-4-1-2-6-4 2-5-3v-2h-2v-4l-2-1z" fill="#150A0A"/>
<path transform="translate(878,631)" d="m0 0h23v2h-2v2l-3 2-16 4-14 10-5 1 2-10h-8l-15 3h-4v2l-15 3-20 6-9 3-7 3-17 5-8 3-7 3-7 2-12 5-8 1v2l-17 6-5 1-1 3-13 4-24 10-15 8-8 4-12 7-8 4-11 6-11 5-8 4-11 4-24 12-10 4-12 4-7 3-6 1-1-2 15-6 3-2 8-2 13-6 3-3 28-14h2l1-4 7-2v-2l4-3 7-3 13-8 22-13 9-5 5-3 10-4 16-8 21-10 8-4 12-4 3-2-1-2 6-3h4l1 2 24-7 21-5 16-4 19-3 20-4 9-2 12-1 10-2z" fill="#331613"/>
<path transform="translate(368,629)" d="m0 0h3l3 9 3 1 8 14 2 2 3 9 6 13 3 7 1 13h2l1 3 1 11 7 14 9 7 8 10 6 5 4 6 2 6 8 7 7 6 2-3 3-10 5-9 3-1-3 11-2 3-1 12h4l3-5 4-14 5-3 1-3h2l1-2-1 4-4 6v8l2 1h17l24-4 11-4 14-4 16-4 12-5 5-3 15-8 2 1-3 3-28 14h-2l-1 3-15 7-8 2-12 5-2 2 10-3 10-4 12-4 17-8 7-4 9-4 7-3 9-4 11-5 12-7 14-7 6-4 20-10 3 1-17 9h-2v2l-7 3-11 7-10 5-10 6h-2l-1 3-18 10-22 12-20 9-24 9-19 5-11 1h-19l-13-1 4 10 9 12 13 22 1 7h-2l-4-10-12-19-7-10-3-5v-4h-2l-2-3v-3l-5-2-10-9-10-14-3-3 4 7 6 8 3 6 8 10 9 14-1 2-4-6v-2l-3-1-4-7-10-13-5-8-8-11-11-11v-2l-4-1-5-6-2-6-4-4-3-7-2-14-3-8-1-13h-2l-9-19v-3h-2l-6-10-4-11z" fill="#5D3D38"/>
<path transform="translate(291,464)" d="m0 0 5 1 7 3 9 4v2l6 2 24 12 5 3 10 4 16 8 14 9 3 4 7 4 5 4v2l5 1 9 2 14 10v2h2l3 5 19 13 8 6 3 5 10 9 9 10 2 5 3 1 2 4v3l11 2 5 7 11 3 7 4 4-3 4-7 6-10 16-36 6-15 6-14 7-17 8-10 4-6 3-1 1 4-7 25-9 24-9 22-5 13-7 15-5 11h-2l-2 6-9 17-12 18-1-2 10-17 6-12 1-8h-2l-8 14-10 15-11 11-5 7-4 8-5 1-1-1v-48l-2-13-3-8-8-13-13-14-14-11-4-5-9-5v-2l-5-1v-2l-5-1-5-5-13-9-5-3-9-4-8-6-6-3v-2l-5-2-10-6v-2l-5-1-8-4-3-3-7-3-15-8-16-8-23-12z" fill="#9C9E9B"/>
<path transform="translate(548,1221)" d="m0 0 11 3 16 5 21 5 13 3 16 4 10 1 11 3 8 3 15 4 2 4 2-2 5 1-2 4-4 1-1 2-15 1h-27l-8 1h-9l-28 2h-36l-14 4h-8l2-3 10-3 1-3-5-1 3-3 5-1 4-1v-2l-4-2-2-2-6-1-2-3-14-4-3-4 7 1 4 2h5v-2h-5l-2-2-1-5 6 1v2l6-1 3 4 5 1 3-1-2-2 4-2 1-4-9 1-7 1-3-1 2-5 4-1v2l7 1-2-1 2-4 6 2z" fill="#9D9F9C"/>
<path transform="translate(394,1164)" d="m0 0 5 1 15 6 21 8h6l12 5 5 3 15 4 16 5 12 4v2l10 2 19 6 11 1 24 6 36 8 17 4 19 3 20 4 25 4 10 1 2 1 14 1h59l45-2 34-2 24-3 4 4v4l-2 1h-11l-15 1-16 3-18 1-14 2-13 1h-61l-34-1-41-6-12-2-2-1-15-2-15-4-9-2-21-5-16-5-27-8-25-7-8-3-17-6-12-5-7-3-17-6-12-5-30-12-10-5z" fill="#2F1211"/>
<path transform="translate(0,848)" d="m0 0 6 5 9 13 15 23 21 31 7 10 3 3v3h2l5 8v2h2l1 4h2l3 5v2h2l1 4h2l6 11 2 1 4 7 6 9v2h2l5 8v2h2l3 5v2h2l4 7 3 2v3h2l4 7 2 1v2h2l3 9 8 12 13 19 8 12 8 11 20 30 4 5 2 6-2 5 3 7-8-4-13-18-3-5-8-13-2-1-3-6v-2h-2l-4-8-7-10-6-11-7-10-6-10-10-15-2-5h-2l-2-5-5-5-7-12-5-5-1-5-3-1-9-12-4-5-2-6-4-1-4-6v-3l-3-1-3-5v-2l-4-2-4-7-6-7-4-7-10-14-7-10-12-18-8-11-7-8z" fill="#3A1B18"/>
<path transform="translate(1825,1254)" d="m0 0 2 3 2 6 1 18 2 16 4 14 2 6 3 1 5 29v6h2l7 49 7 39 1 11 2 7 2 10 7 32 9 49 3 13v9l-3 3h-2l-6-25-2-7-6-1-4-16-2-14-6-29-4-26-8-42-8-47-5-36-4-29-3-24v-7l1-3v-13z" fill="#F1F4F4"/>
<path transform="translate(1453,1681)" d="m0 0h23l1 4-4 3-22 6-67 11-99 18-39 6-31 4h-7v2l-8 1h-31l-8-1-1-2h2l-1-4 39-4 21-2 13-2 7-2 10-1 10-2v-2l27-5 15-1v-2l20-3 9-3 25-5 10-1 6-2 29-5 12-1 7-2 22-1 1-1z" fill="#3D2320"/>
<path transform="translate(1006,8)" d="m0 0 25 2 31 2 56 7 69 9 63 10 49 9 38 9 21 7 19 4 12 5 3 2v3l-13-1-30-6-39-9-61-12-60-10-79-11-18-2v-2l-16-1-13-2-16-3-17-1-22-2-5-2-1-4z" fill="#7EB8C9"/>
<path transform="translate(1865,759)" d="m0 0 2 1-2 3 1 5 5 1-4 4-6 4h-2v2l-6 4h-2l-1 3-5 3h-2v2l-11 8-13 12-21 21-6 8-22 28-4 4-3 5-5 6h-2l-2 5-4 4-6 7-9 11-41 41-8 7-13 11-10 8-14 11-5 2-2 4-10 6-9 9-10 6-9 5h-5v2l-11 4-9 3-8 1h-14v-1l11-1 13-5v-2l-6 2-4-1 6-3 9-3 8-4 13-4 10-7 9-5 3 1 9-6 8-6 11-8 13-10v-2l-3 2-3-1 5-5h2v-2l5-3 23-23 1-2h2l2-6 20-20 7-8 13-15 12-14 9-10 7-9 9-10 9-11 7-9 9-10 12-12 11-9 14-12 13-10z" fill="#391B18"/>
<path transform="translate(1619,1330)" d="m0 0h1v7l-4 12-3 11-4 10-9 27-4 10-5 15-5 14-4 10-5 12-4 10-5 12-10 27-6 19-6 23-1 5-1 15v24l3 27 7 32 1 8v14l-5 1-3-2-3-7-1-10-3-13-5-38-1-4v-36l3-19 2-7 1-10 3-6 2-10 4-14 4-10 17-43 14-35 5-13 3-8 6-15 1-4 3-1 1-4h4l1-6 5-15 3-5 1-7z" fill="#3B2726"/>
<path transform="translate(1767,873)" d="m0 0 7 4 17 47 10 30 13 47 6 27 5 35 2 19 4 56 4 40 4 28-1 4-2-9-4-22h-1l-1 9h-1l-3-19-2-37 1-14-2-23v-10h-2l1 16-3 1-3-21-3-31-7-32-2-7 1 10 3 19v7h-1l-5-28-9-39-6-24-6-26-4-17-7-19-2-8z" fill="#726D69"/>
<path transform="translate(744,1261)" d="m0 0h38l36 2h13l13 1 3 2-1 3-65 5-124 5h-71l-21-2-3-1 1-5 1-1 10-1h32l63-3 33-2 16-2z" fill="#706C68"/>
<path transform="translate(763,1497)" d="m0 0h2v2l-4 1v2l-22 14-4 2h-3v2l-19 12-16 9h-3v2l-7 4h-3v2l-24 13-12 7-9 3v2h-4v2l-16 8-12 5-10 5-8 2v2l-16 6-9 4-12 6h-4v2l-6 1v2l-10 3v2l-10 4-13 4h-4v-2l5-3 6-4h2v-2l5-2 4-2v-2l7-5 5-2 8-4 10-6 6-5 9-3 6-3 10-6 29-15 10-4 6-3 5-1v-2l6-3 7-1v-2l20-9 10-4h2v-2l9-4 4-2 11-1 3-2 9-3 13-7 13-8 10-6z" fill="#3D2725"/>
<path transform="translate(1651,224)" d="m0 0h2l1 37 2 22 3 16 2 16 3 36 1 6 3 39 5 30 5 44 2 34 3 8 4 2-10 5-2-1 1-5h-2l-1-4h-2l-2-7-3-28-2-10-3-26-2-23-2-20-1-2h-11l4-3 4-1 1-5-1-19-4-46v-60l1-27z" fill="#947265"/>
<path transform="translate(1448,715)" d="m0 0h5l7 3-1 3-12 2-5 2-1 4-5 2-6 2v2l-8 3-4 1v2l-7 6-9 3-9 5-6 5h-3l-2 4-8 7-7 9-9 11-9 9-10 8-16 8-7 2h-38l-4 3-5 1h-16l-6 10h-2l-2 5-4 5-7 12h-2l-1 5-4 5-6 2v-5l2-3 3-9 7-10 1-3h2v-3h2l2-5 4-6v-4l7-2 21-2 19-2 15-3 5-3 8-1v-2l10-6h2v-2l8-6 12-11 10-8 5-2 2-3h2l2-4 6-5h2v-2l10-6 12-8 5-4 5-2 10-7 10-5 9-3 6-1z" fill="#351714"/>
<path transform="translate(780,8)" d="m0 0h6v2l-8 3-26 4-17 3-17 2-1 1-69 8-39 6-18 2-44 8-30 6-14 2-4-1-28 5h-10l4-2v-2l70-15 41-8 45-8 44-6 50-6 31-3h18z" fill="#7EB8C9"/>
<path transform="translate(245,1098)" d="m0 0 8 1 7 3 9 4 25 14 2 1v2l6 2 16 8 18 10 6 3 16 6 10 2 15 7 10 4 6 3 10 3 28 11 15 6 14 5 11 5 4 2-13 3-9-4-4-2-17-4-15-3 1 3-11-3-10-5h-2v-2l-5-1-8-5-11-6-12-5-10-5-5-2-16-8-10-6-13-8-19-10-12-5-7-1-5 3-6 12-5 15-4 4 3-10 1-5-1-8-1-11-4-7-6-8-1-6z" fill="#8F9693"/>
<path transform="translate(1461,511)" d="m0 0 3 1-16 8-20 9-13 6-15 6-8 4h-3v2l-13 4h-3v2l-13 4-17 5h-3v2l-20 5-5 2h-9v2l-8 2-17 2-23 5-10 2-24 5h-4v2l-61 11-51 8-30 1 3-2 4-1h8v-2l34-6 50-11 53-12 38-8 36-7 50-10 34-10 23-8 11-5 20-9 16-7z" fill="#B3BEBD"/>
<path transform="translate(140,918)" d="m0 0 5 5 4 6 5 8 1 6h2l6 10 8 6 9 4 15 11 17 12 13 8 14 8 8 3-1 3 5 1 13 4 6 2v1h-9l-13-3-9-2-10-5-3-1v-2l-6-2-16-7-10-10-2-3-8-4h-6l-3 1 2 9 5 12 2 3v5l3 1 4 10 1 6h2l7 16 3 9 7 11 8 7 9 6 12 12-5-1-2-1h-6l-1 5 2 2 3 2 3 10 4 4 1 10h-3l-7-12v-2h-2l-3-11v-2l-5-5-7-10-7-11v-2l-4-2-6-11v-2h-2l-1-6h-2l-4-11-5-10-4-10-4-11-3-7-3-4-4-10-2-9-6-12-2-2-3-7-3-6v-2h-2l-6-15v-5z" fill="#271513"/>
<path transform="translate(1040,768)" d="m0 0h9l9 3v1l-11-1-2 2 5 14 3 7 7 12 4 10 8 13 8 17 8 14 8 16 7 10 7 11 17 12 17 9 17 6 9 4h8l12-5-1-12-5-8-9-15-11-21-5-12v-3h-2l-2-11-1-3v-10l1-10-9-19-6-9-6-2-17-2v-1h10l16 2 3 3 11 23 1 2v25l5 14v2h3l11 23 4 7 9 19 3 12v9l-11 6-8 6v4l8-3 10-7 4 2 5 12-3-1-4-9-4 1-6 4-11 10h-9l-7-3-10-4-9-4-10-6-7-4-7-7-3-6h2l4 5 9 6 10 5 3 1v-2l6 2 7 6 5 1-4-8-6-5v-2l-6-2-20-11-3-2v-2h-3v-2l-4-2-7-8-7-10-9-15-13-25-9-17-8-13-8-16-6-14-4-12z" fill="#919896"/>
<path transform="translate(1011,752)" d="m0 0 5 1 5 4 2 10 3 16 4 22 1 6h2l-1-4 1-2 4 2v6l-3 2-2-1 3 8 3 12 3 7v3h4l-1-4-3-7v-7l1-5-2-12-5-12-1-4v-9l2-1 10 20 3 8 8 15-1 2-11-20v9l9 27 5 11 10 25 4 9 10 15 10 13 11 11 14 11v2l3 1v2l4 2-3 2 2 4h-5l-11-8-10-8-8-7-7-8-9-10-10-15-12-20-8-16-9-21-8-20-5-15-2-4-3-28-1-11-3-6z" fill="#987668"/>
<path transform="translate(1784,1013)" d="m0 0 2 3 5 18 8 44 4 21 3 26 2 9 4 3h2l2-3-2-26-2-19-1-5 1-7h1l5 42 6 64 4 34 1 2 2 18 6 40v9h-1l-4-26-2-6-4-24-3-8v-3h-2l-2-4-1 8-1 13v25l3 32 4 25 5 28 6 31 10 52 7 39 9 54v10l-1 2h-2l-2-9-2-22-5-37-6-35-11-55-3-14-7-37-6-35-3-32v-45l-2-30-9-63-3-15-5-35-5-34-5-19z" fill="#9C9E9B"/>
<path transform="translate(1477,913)" d="m0 0h5v4l-2 3h-2l-2 4-4 4-9 3-13 1v2l-36 5-23 3h-11v-1l12-3-22 2-23 4-34 8-29 3-2 1-1 4-6 4-9 4h-20l-20 4-21 2h-16l-20-4-6-3v-2h23l4-1 13-2 6-4 1-4-7-2-6-13-3-6-5 2-8 6-7 1-1-4 9-7 10-5 1-9 2 4 1 9 9 18 15 10v6l-2 4 13-1 5-2 13-2 12 1h2v-2h-18l-12-5 2-1 5 2h10l20-2 9-3 2-1 19-1 17-3h3v-2l31-7 28-5 33-4 23-3 15-3 13-4 4-3z" fill="#724338"/>
<path transform="translate(1381,1550)" d="m0 0h11l-1 3-7 4-18 5-9 2-14 3-36 6-10 2-64 8-1 1-22 2-32 2h-17v-3-3l16-4 28-3 25-3 2-1 19-2 13-2 36-5 26-3 17-3 16-2z" fill="#1D1212"/>
<path transform="translate(931,589)" d="m0 0 8 2-1 4-16 6-20 7-19 6-8 5-14 3-12 4-9 4-12 3-6 2-11 2-18 5-13 3-10 2-8 5-15 3v-2l9-4 6-2 1-3 28-12 16-6 13-5 25-10 33-11 32-8z" fill="#706C68"/>
<path transform="translate(1388,937)" d="m0 0h9v1l-17 4-19 3-5 2-18 2v2l-9 3 4 2v3h11l16 2 12 2 14 4 3 2 15-1 17-3h11v-2l26-5 19-6 9-3h3v2l6-1-2 4-15 8h-6l-3-1-15 3-18 2-23 5-22 3-6 2v1l-14-1-58-7-5-1-22-2-5-6 1-5 10-2 21-2 34-8 30-5z" fill="#7A4539"/>
<path transform="translate(954,291)" d="m0 0v3l-8 12-9 9-8 7-7 7-8 7-13 13-11 9-13 11-20 18-11 9-13 11-17 14-10 8-12 9-18 14-16 12-14 12-12 9-10 7-9 4-3-1 22-18 15-13 11-9 11-10 14-11 13-10 14-12 4-1 2-4 8-7 4-1 1-3 8-6h2l2-4h2v-2l7-5h2v-2l8-6 4-2 2-4 14-11 12-11 7-6h2v-2l8-6 8-7 16-13 16-15z" fill="#4D4141"/>
<path transform="translate(1818,1214)" d="m0 0 3 2v3h2l5 15 4 24 2 10 2 11v7h2l9 59v8h-1l-6-35-3-3-4-11-2-10-2-13-1-18-3-7v13l-1 9 2 18 5 34 3 26 6 36 9 50 4 21 5 31 6 29 2 13 1 6 6 1 4 10 4 18v5l-3 3-5-3-4-9-7-32-15-90-10-53-10-51-5-29-3-19-3-34v-23l1-18z" fill="#B0BBBB"/>
<path transform="translate(1385,632)" d="m0 0h8l-5 4-9 1-2 5-17 7-8 4-7 4-7 5-8 3-13 10-16 12-9 8h-2v2l-8 6h-2v2l-3 3h-2v2l-6 4-5 5-5 6-13 10-5 4-7 3-18 12-15 7-5 2-12 2-3-3 16-8 3-1 1-3 16-10 9-6 17-12 20-16 13-11 9-8 8-7 22-16 8-4 9-6 23-11 16-6 10-3z" fill="#361816"/>
<path transform="translate(840,1435)" d="m0 0h3l-1 5-5 9-5 5-6 10-3 8-2 1-1 4-3 3-5 7-4 7-5 8-4 8-6 8-2 5h-2l-1 4-4 4-3 6-3 3h-2l-1-2h-3l2-10 2-3 1-13-7-4-5 1-8 2v-3l1-3 12-9h3l2-5 14-10 8-6 9-7 7-6 8-7 6-7 5-3 2-4 4-2z" fill="#B0BBBB"/>
<path transform="translate(1385,41)" d="m0 0 10 1 40 10 27 8 36 12 33 12 24 10 25 12 14 8 20 10v2h-7l-10-3-26-11-36-15-29-11-60-20-27-10-12-5-19-7z" fill="#7FB8C9"/>
<path transform="translate(709,701)" d="m0 0h11l4 3v2l5 2 3 6 2 14-3-1-6-8-5-6-7-1-2 3v42l1 15 4 7 5 3 19 2v9l-4 5-8 5-7 1-15-3-5-8-3-14-1-5-1-23 1-6 1-26 3-9 5-8z" fill="#C59E88"/>
<path transform="translate(151,1146)" d="m0 0 3 3 4 9 10 25 6 17 7 21 3 10 2 5 2 8 3 13 3 11 3 9 3 14 5 21 2 9 1 11 1 2v5h-2l-2-9h-2l-20-61-12-36-13-37-9-25v-10l1-7v-6z" fill="#7BB7C9"/>
<path transform="translate(852,668)" d="m0 0v3l-4 6 1 5v7l-4 16-10 61-6 52-4 51-2 50v66l1 13 1 35 2 31 6 45 6 34 4 19 1 8 3 8 9 37v7l-2-4-5-13-3-13-5-22-5-21-7-45-4-26-1-3-3-44-3-37-1-10-1-32-4-36-1-1v-10h5l3-5 3-29 1-23 3-38 5-45 6-36 5-33 3-8v-12z" fill="#B2BDBD"/>
<path transform="translate(96,319)" d="m0 0 1 3h2l3 13-1-15 3 4 5 17 3 3 4 8 12 13 8 7 13 11 6 4v2h3v2h3v2l4 1 12 8 11 7 21 12 24 13 5 2v2l9 3 6 5 17 8 1 4 5 3 5 2 5 5-4-1-12-5-16-8-14-8-4 1-16-10-11-6-19-11-23-15-19-12-17-12-21-14-4-7-5-12-5-18z" fill="#382221"/>
<path transform="translate(131,1034)" d="m0 0 4 4 5 9 8 11v2l3 1 1 5h2l7 11v3l3 1v3l3 1 1 3 3 2 5 9 3 3 4 7 4 6 3 2 4 7 3 2 3 5 1 4 4 2 7 7 7 8 3 3 6 1h11l1-6-1-16-9-21-2-5h-2l-1-7 3 4 1 4 3 1 5 9 7 11 2 4 2 1v-18l-7-12-7-11-2-5v-4l5 1 19 12 8 5-2 1-5-3-12-3 1 8 9 12 1 5 1 14 1 5-5 13-6 9-7 4-14 1-16-6-13-11-7-7-2-1 1-4 1 2 6 3-3-6 2-7-5-8-7-10-10-15-7-10-12-17-7-11-10-14-6-9z" fill="#7F4A3D"/>
<path transform="translate(1341,567)" d="m0 0h3v2l-3 3 3 2-21 7-9 2-25 6-5 2-26 5-40 8h-6v2l-31 6h-14v-2l5-2 2-2 2 1-1-2h-2l-1-4 1-1 17-3 56-11h4v-2l23-5 20-3 9-3h4v-2h5v2l-9 3 12-1 12-3 11-3z" fill="#5D3F3A"/>
<path transform="translate(829,1464)" d="m0 0 1 4-2 4 4-2-2 7h-2l-1 5h-2v3h-2v3h-2l-3 9-3 5h-2l-1 5-1 2h-2l-1 4-2 4h-2l-1 4-6 10h-2l-2 6-13 20-5 8h-2l-1 5h-2l-1 4-10 14-10 15-9 16-11 19-4 6-4 5-3 4h-2l1-10 8-15 3-6 9-15 5-9 20-32 1-3h2l2-6 2-3h2l1-5 7-12h2l2-6 5-5 1-3h2l1-5 4-5 4-6 2-5 3-5 5-7 4-7 4-6h2l1-5h2v-2l5-5z" fill="#211414"/>
<path transform="translate(1044,807)" d="m0 0 3 3 11 20 3 4 3 7 13 27 2 4v3h2l4 9 6 9 10 14 6 7 4 2 6 9 11 10 9 6 5 6 5 2 2 4-10-1-21-11-5-5-13-11-10-10-10-14-10-15-6-16-6-15-7-16-7-22z" fill="#F6F7F6"/>
<path transform="translate(1469,1632)" d="m0 0 6 2 1 2-5 5-12 9-8 4-18 6-18 5h-6l-2-1v3l-8 1-7 2-7 1-2-3h2v-2l16-4 4-2 9-1h-8l-4 2-9 2-10 2-6 2h-17l3-2 5-4 9-1 2-1h-12-3-5l-4 2-5-1-1 2h-10l3-2 32-7h4l1-2 10-2 4-1 6-2 21-4 15-3 14-4z" fill="#CBD7DE"/>
<path transform="translate(1647,183)" d="m0 0 12 1 1 2v94l4 53 3 22 2 21 2 12 5 42 3 22 2 44 2 12 1 3 2 2-4-1-3-8-2-34-6-51-4-23-3-39-3-27-2-24-3-17-2-15-1-13v-37h-2l-1 35v60l5 57v8l-2 5-6 3h9l2 3v11h-1l-2-9-1-1h-8l-11 3h-3v-2l5-1h-4l-10 1 4-3 24-8 2-3-2-25-3-35-2-36v-19l1-32z" fill="#919896"/>
<path transform="translate(1769,963)" d="m0 0 5 1 2 4 3 1 5 9 5 10v3l2 1 3 6 8 36 5 32 2 12 2 15 1 2 2 21 2 6 1 12-5 5-5-5-3-16-3-25-8-42-5-25-9-29-4-11-4-16z" fill="#B2BEBE"/>
<path transform="translate(1753,467)" d="m0 0h2v7h1l-1 7-6 5-1 2h-2l-1 3-7 3-8 6-17 11-11 7-8 4-13 8-19 9-6 3-11 6-6 2-7 4-3 2-15 3-8 4h-2l1-4 6-2 2-4h-5v-2l9-6 4-2 7-1 1-2 9-4 12-5 11-6 10-4 16-8 16-7 16-10 12-7 10-8 9-12z" fill="#231513"/>
<path transform="translate(870,1234)" d="m0 0 5 4 1 6v9l2 10 10 30 7 15 5 12 11 24 8 17v2h2l6 13v2h2l3 6-1 2-4-4-2-3v-4l-3-1 1 4-3-1-5-8-8-18-4-7-2-11h-2l-1-4h-2l3 7v5l-2-2-7-15-10-23-9-24-3-7-1-10-3-10-1-2-17 2-9 2-43 3h-84l-26-2-27-5v-1l11 1 22 3 34 1h61l21-2 6-1 26-2 8-2 17-1h11l-2-6-2-1z" fill="#63413A"/>
<path transform="translate(1605,420)" d="m0 0v3l-7 8-3 2-4 7-12 13-10 10h-2v2h-2l-2 6-6 7-6 2-11 6-17 10-10 4-3 1v2l-2 1h-6v2l-4 2h-3v3l5-2 1-2 9 2 1 3-8-2-3 3h-3l8 8 3 10 2 3v14l-5 16-5 12-7 8-6 12-4 4-5 1v2l-18 7-10 2h-5v2l-15 6-10 2-11 4-13 4-14 4-6 3-13 4-21 9-17 9-5 4-2-1-3-3 1-5 10-8 8-2 10 1 3-3 7-2 9-3 8-4 9-1 8-3h5l1-3 6-3 9-2 15-7 9-1 2 2 2-2h3v-2l7-1 3-2h4v-2l7-3 12-2 10-4 4-10 6-12 7-8 3-8 2-11v-13l-4-13-7-9v-2l-4-2 11-6 9-6 17-10 15-10 11-8h3l2-4 11-9 10-9 5-6 5-5 11-10z" fill="#AEB6B5"/>
<path transform="translate(1511,1170)" d="m0 0h5l-1 9-8 22-15 32-10 23-12 23-9 15-7 11-13 22-10 15-3 5-2 3h-2l-2 4-4 6-7 6-2 5-5 4-4 5-4 2h-3l1-3 8-7 9-11 5-9 4-8h2v-3h2l2-5 4-7h2l2-5 4-8h3l2-6 5-9 8-14 1-4 2-1 6-11 12-25 13-32 3-10 1-2h2v-9l3-1 8-17 4-4z" fill="#726F6C"/>
<path transform="translate(432,755)" d="m0 0 3 1 7 11 6 7 10 8 2 1 2 6h2l2 5 21 33 3 6v4h3v24l-2 10-3 8-7 12-5 5-5 6-8 6-11 1-1-2 2-2v-4l3-2 3-5 6-9 1-3h2l3-9 4-10h2l1-5h2l1-14-3-11-8-16-2-6-3-1-6-14-11-15-6-8-3-6-7-9z" fill="#1E0F0E"/>
<path transform="translate(884,664)" d="m0 0h11l13 4 11 8 38 28 11 8 15 11 1 4 3 7 9 4 8 5 17 8v2l5 2-1 3-4-3-10-3-6-4-5-2-6-4-5-2-18-11-11-8-24-15-10-7-23-15-13-8-6-2-1-2-7-3 1-2 7-1z" fill="#371A17"/>
<path transform="translate(1207,760)" d="m0 0 2 1-5 4-12 6-12 7-19 6-4 4 1 8 1 7 9 2 19 1 25 3 18 2 10 2 7 1 21-3 3-1 1-2 4-1h13l4-2 9-2 12-4 14-10 6-4 11-10 5-5 6-5h2v-2l12-2-2 4-5 5-5 2-10 8-7 7-10 8h-2v2l-10 6h-2v2l-10 3-7 3-11 2-26 3-14 1-6 2-1 5-1-4h-7l-9 4-6 1-7-3-7-1-3 1-4-3-10-3-5-3-7-1v2l-3 3h-2l2-4 2-2h5v-2l-15-2-6-2 6 8 1 4-3 7h-3l-2-12-5-9-1-5 2-2-1-9 5-5 10-4 13-4 9-5 2-3 7-1v-2z" fill="#C69F89"/>
<path transform="translate(310,799)" d="m0 0 5 2 6 7 6 8 9 9 3 1v2h2l1 3 4 3 4 7 4 4 3 1v2l4 1 2 1v2h2l2 5h2v13l-4 4-3 5-5 4-4-1-5-5-2-6-5-5-9-13-3-5-2-5-2-1-6-11-4-9-4-8-1-5z" fill="#DABBA4"/>
<path transform="translate(1908,1649)" d="m0 0h1l2 26v55l-2 39-2 31-2 24-5 2 1 5-4 1-2-4v-27l4-67 1-56h1l1 14 1 2 1-25 2-4 1 2z" fill="#372221"/>
<path transform="translate(1556,583)" d="m0 0 3 1-2 2-13 4-5 1v2l-12 5-7 3-8 2-15 4h-2v2l-16 6-11 3-13 5-12 3-4 2-12 2-21 6-16 5-14 5-8 2-12 5h-3v2l-4 2h-3l-1 3-10 5h-2l-1 4-9 4-11 8-11 9-6 5h-2l-1 3-13 9-5 5-4 2-2 4-6 5-2-1 7-6 5-5 3-1v-2h2l1-3h2v-2l8-6h2v-2l11-9 13-10 12-9 5-4 9-3 9-7 10-4 12-6 6-1 2-5 9-2 3-2-2-2 14-4 6-2 14-5 10-2 9-4h3v-2l18-4 13-5h2v-2l4-1-3 6v2l5-2 3-4h8l9-3 7-1 9-4 21-6z" fill="#5F3E38"/>
<path transform="translate(1545,1667)" d="m0 0 2 3 1 3 7 1v-7h1v9l-16 5-24 5-33 5-41 7-37 5-36 6 1 2-21 4-40 7-21 3h-8l-47 7-15 2h-10v-1l59-8 46-8 88-16 50-8 24-7 1-4h-23l-9 1-1 1h-14v-1l73-10 34-3h9z" fill="#766D68"/>
<path transform="translate(1826,1194)" d="m0 0 2 4 3 11 6 43 2 18 2 11 7 49 4 23 5 40 9 49 5 27 1 1v9h2l2 11 2 16 3 12 2 12 5 28 4 16 4 29 1 11 1 9-3 1-3-22-8-44-5-25-9-46-4-18-2-10-2-7-2-16-7-40-8-57-8-53-4-30-4-25-1-12-2-10z" fill="#231515"/>
<path transform="translate(388,519)" d="m0 0 5 2 5 4 12 5 10 8 10 7v2l5 1v2l5 1v2l4 1 7 5 5 5 15 13 11 12 8 13-1 3-7-8-5-4-5-5-6-2-3-3-6-1v-2h-3l13 11 10 11 5 10 1 6 1 45 3 26 1 22-5 13-6 11h-2v-4l2-1 7-15 1-3v-14l-2-4v-13l-2-24-1-43-4-8-5-5-4-6-13-11-5-3-5-6-6-3-5-5-4-2-1-2-3-1v-2h-3l-1-2-3-1v-2l-4-2-3-1-8-8 5 2 15 10 11 8 14 11v-1l-10-8-1-3h-2v-3l-5-2-3-3-3-2 1-1h-3v-2l-6-2-2-4 2-2h3l-3-1-1-2-4 1-4-2v-2l-4-1-2-6-4 2-5-3v-2h-2v-4l-2-1z" fill="#351F1E"/>
<path transform="translate(1548,1502)" d="m0 0h1l1 7 1 5-2 9-2 8v6l1 4-3 13-1 15v24l3 27 7 32 1 8v14l-5 1-3-2-3-7-1-10-3-13-5-38-1-4v-36l3-19 2-7 1-10 3-6 2-10z" fill="#624844"/>
<path transform="translate(1165,26)" d="m0 0h8l65 10 56 10 31 7 25 7 16 5 11 2 12 5 3 2v3l-13-1-30-6-39-9-61-12-35-6v-1l14 1 49 9h4l-25-6v-2l-10-3-11-3-70-11z" fill="#99C4C8"/>
<path transform="translate(113,1015)" d="m0 0 5 3 3 4v2l3 1 4 7 3 2 3 7 9 13 11 16 8 12 8 11 20 30 4 5 2 6-2 5 3 7-8-4-13-18-3-5-8-13-2-1-3-6v-2h-2l-4-8-7-10-6-11-7-10-6-10-10-15-2-5h-2l-4-8 1-2h2z" fill="#311412"/>
<path transform="translate(1630 1e3)" d="m0 0 4 2 2 8 1 95v33l-1 50v41l-2 23-3 19-5 21-4 9-4 8-2 8-1-4 8-39 5-35 2-19 2-44v-74l-2-96-3-3z" fill="#767470"/>
<path transform="translate(2047,505)" d="m0 0h1v24l-7 6-7 8-8 9-12 9-7 8-10 11-5 3-7 1-3 1-1 3-8 4-1-2 6-9 11-12 7-8 13-15 9-10 7-8 12-12 7-8z" fill="#201110"/>
<path transform="translate(1753,880)" d="m0 0v3l-6 8-12 13-3 6 2 1-40 40-8 7-13 11-10 8-14 11-5 2-2 4-10 6-9 9-10 6-9 5h-5v2l-11 4-9 3-8 1h-14v-1l11-1 13-5v-2l-6 2-4-1 6-3 9-3 8-4 13-4 10-7 9-5 3 1 9-6 8-6 11-8 13-10v-2l-3 2-3-1 5-5h2v-2l5-3 3-3 5-3 16-15h2l1-3h2l2-4 7-7 7-8 12-12h2l2-4 14-16z" fill="#583B38"/>
<path transform="translate(1067,184)" d="m0 0 1 3-9 11h-2l-2 4-10 10-7 8-15 15-7 8-22 22-11 9-10 8-5 2-2 4-15 13-3 2 2-4 4-7-12 12-8 7-11 9-10 9-2-1 10-10 7-6 20-20 9-6 11-10h2l1-4 10-10 8-7 12-12 8-7 13-12 3-1v-2l8-7 10-10 8-7 3-1 5-5h2l2-4z" fill="#919896"/>
<path transform="translate(1416 1e3)" d="m0 0 11 3 8 5 7 3 21 10 10 6 12 7 9 4v2l6 2 16 9 14 10 15 12 11 9 11 11 1 4-4-1-20-14-13-9-15-10-15-8-21-13-15-9-13-8-19-12-10-7-7-5z" fill="#211414"/>
<path transform="translate(1408,987)" d="m0 0 4 1 27 8 28 6 14 2-4 1 1 7 4 4-1 5-4 3-9 1-12-6-4 1-13-7-7-3-5-3-11-3-9-5-8-7v-1l10-1z" fill="#FBECD8"/>
<path transform="translate(219,1380)" d="m0 0 2 2 6 16 4 10 3 7 7 22 3 9 4 9 4 16 3 10v6l2 1 3 12 3 7 4 10 3 9 6 13 1 5-3 1-11-17-12-25-9-27-10-39-13-49z" fill="#7DB8C9"/>
<path transform="translate(583,510)" d="m0 0 2 2-3 13-8 22-12 30-7 17-11 25-9 17-12 18-1-2 10-17 6-12 1-8h-2l-8 14-10 15-11 11-5 7-1-2 4-10 5-2 8-10 5-9 6-9 7-14 10-19 11-27 6-15 7-16 9-15z" fill="#6F6C68"/>
<path transform="translate(1380,547)" d="m0 0h5l-4 2-5 2h-3v2l-13 4-17 5h-3v2l-20 5-5 2h-9v2l-8 2-17 2-23 5-10 2-24 5h-4v2l-61 11-51 8h-10v-1l39-6 49-9 16-4-15 2-6 1h-8l2-2 28-6 24-4 15-4 24-4 12-1 2-1 12-2 18-4 14-3 6-1 1 1 22-6-1-2 9-2 7-1z" fill="#DCBDA7"/>
<path transform="translate(1382,761)" d="m0 0 2 1-12 11-6 9-5 5-9 10-10 9-14 8-12 4h-38l-4 3-5 1h-16l-6 10h-2l-2 5-4 5-7 12h-2l-1 5-4 5-6 2v-5l2-3 3-9 7-10 1-3h2v-3h2l2-5 4-6v-4l7-2 21-2 19-2 15-3 5-3 8-1v-2l5-3 2 1-8 6-9 4 12-1 10-5 9-4 13-10 10-7 10-13 8-8z" fill="#7D4639"/>
<path transform="translate(706,699)" d="m0 0 16 1 8 7 4 7 3 9 3 5 2 9-1 9-2 5h-2l-1 2-3-7-4-15-3-7-3-5 1-2 7 8v2h2l-2-13-2-6-5-2v-2l-4-2h-11l-4 2-5 10-1 5-1 26-1 8 1 21 3 16 5 10 7 1 8 2 7-1 9-6 2-3 1-9h-10l-9-1-6-4-4-7-1-15v-42l3-4 7 1v1l-7 2-1 2 1 52 3 7 5 3 16 1h5l2 2v9l-2 8-6 7h-2l-1 3h-3l-1 3-4 1h-7l-9-2-5-5-6-11-4-23v-23l3-34 4-8 3-7z" fill="#DEBFA8"/>
<path transform="translate(83,288)" d="m0 0 3 1 3 13v4h2l2 7 2 11 6 19 4 13 4 8 5 5 14 9 23 16 24 15 12 8 24 14 17 10 19 11 8 5v2l-8-2-9-5-11-6-7-5v-2l-5-2-7-5-16-8-12-5-14-8-11-8-12-5-8-6-10-8-14-9-4-5-4-6-1-6-4-4-4-11-5-19-3-10-3-8-2-8 1-8z" fill="#FBEBD6"/>
<path transform="translate(298,112)" d="m0 0 17 3 8 2v2l-21 8-30 11-10 4h-2l-2-2-10-1-1-3h-8l-9 2h-5v2l-5 2-3-1 17-9 18-7 39-12z" fill="#CBD7DE"/>
<path transform="translate(394,1164)" d="m0 0 5 1 15 6 21 8h6l12 5 5 3 15 4 16 5 12 4v2l10 2 19 6 11 1 24 6 36 8 17 4 19 3 20 4 25 4v1l-13-1-13-2-23 1-16-4-7-3-11-3-10-1h-7l-18-6-16-4-14-3-12-4v2l10 2-4 1-21-6-8-3-17-6-12-5-7-3-17-6-12-5-30-12-10-5z" fill="#462520"/>
<path transform="translate(1374,942)" d="m0 0h5l-4 3-8 3-1 5 3 2 7 1 26 2 7 3 11 1 36-6 16-5 12-3 10-3h5l-1 4-3 3-4-1h-2v-2l-27 9-24 5h-6v2l-11 1-17 3-15 1-7-3-13-4-13-2-21-1-2-1v-3h-5l1-3 9-2v-2l9-2 13-2 7-2z" fill="#C19B86"/>
<path transform="translate(931,597)" d="m0 0 3 1-25 10-15 5h-3l-1 2-4 3 1 4 6 2 32-2 17-1 60-2 25-2 57-6 4-1h13v1l-67 9-29 2-41 1-37 2-40 3-30 5-21 3-11 2-11 3-4-1 3-3 21-7 7-2 17-6 11-3 8-2 8-5 17-5 20-7z" fill="#919896"/>
<path transform="translate(896,1329)" d="m0 0h2l1 4h2l2 5 2 8 14 28 4 4-3-4 1-3 4 4 3 7 7 7 4 8v2h2l8 15 7 10 5 10 5 6v2h2l2 7 3 1 4 10 7 8 2 5-7-1-5-5-3-1-13-20-2-3v-3h-2l-10-16-14-22-10-18-9-16-11-23-3-11z" fill="#3D2928"/>
<path transform="translate(1042,769)" d="m0 0 5 1-2 3 5 14 3 7 7 12 4 10 8 13 8 17 8 14 8 16 7 10 7 11 17 12 17 9 17 6 9 4h8l12-5-1-12-5-8-9-15-11-21-5-12v-3h-2l-2-11-1-3v-10l1-10-9-19-6-9-6-2-17-2v-1h10l16 2 3 3 11 23 1 2v25l5 14v2h3l11 23 4 7 9 19 2 7v12l-5 3-11 5h-6l-18-8-15-6-19-11-11-10-11-17-6-9-11-21-10-19-9-15-6-14-5-7-6-18-2-7z" fill="#A9B1B0"/>
<path transform="translate(1453,1681)" d="m0 0h23l1 4-4 3-22 6-67 11-22 4h-6v-1l15-3h3v-2l3-3 26-6 5-3 6-2-26 3-8 2-26 4h-6l3-2 16-2 6-2 29-5 12-1 7-2 22-1 1-1z" fill="#483B3C"/>
<path transform="translate(302,1565)" d="m0 0 5 4 6 8 9 11 5 6 11 9 13 11 17 13 9 8 13 10 16 12 19 13 10 7 2 5 3 2v2l5 2 2 3-5-1-20-11-5-4h2l-6-7-2-1v-2l-7 2v-2l-4-1-2-2-1-2-5-2-2-1v-2l-5-2-13-11-14-12-22-22-8-7-10-9-1-5-6-8-8-11z" fill="#9EC6CA"/>
<path transform="translate(878,631)" d="m0 0h23v2h-2v2l-3 2-16 4-14 10-5 1 2-10h-8l-15 3h-4v2l-15 3-7 1 2-2 7-3-9 1-8 4-3-2 2-2-15 3-29 8-18 6-20 7-13 5-27 12-3-1 32-16 17-6 3-2-1-2 6-3h4l1 2 24-7 21-5 16-4 19-3 20-4 9-2 12-1 10-2z" fill="#5E3E39"/>
<path transform="translate(1164,847)" d="m0 0 2 1 4 9 6 10 8 15v2h2l9 20 3 7v3h2l6 17v2l3 1 2 3v4l4 2 9 7 9 5 1 2 11 4 18 1v2l-2 1-15-1-12 3-13 2-3-1 2-10-4-2-10-6-6-9-4-9-1-2-1-13h-2l-4-14-9-20-6-10-8-17z" fill="#5D403B"/>
<path transform="translate(588,499)" d="m0 0 2 1-2 11-8 26-15 37-5 13-7 15-5 11-1-3 13-30 12-31 6-16 5-15 1-7-3 3-9 15-8 18-10 25-8 19-10 19-8 15-5 7-3 6-9 11-5 1-1 2v-6l3-5v-9l-1-11-1-7 1-2 6 1 7 2 5 3 4-3 4-7 6-10 16-36 6-15 6-14 7-17 8-10 4-6z" fill="#919896"/>
<path transform="translate(1388,758)" d="m0 0 2 1-5 5-8 10-4 6-6 7-2 3h-2v2l-8 7-9 10-9 6-8 5-9 4-9 2h-15l-9-2-8 1-5 1-1 4-7 6-4 3-6-1v-2h-2v-2l-4-2-3-1 5-9 5-1h12l7-2 2-2h38l14-5 13-8 15-14 6-8h2l2-5 9-10 6-5 1-2z" fill="#DDBEA7"/>
<path transform="translate(974,1453)" d="m0 0 5 5 15 16 5 5 4 2 5 5 8 7 15 9 24 9 14 4 2 2-6-1 1 4h-3v2l5 2 4 4-6-2-14-7-24-9-11-3-11-6-10-7-14-14-10-13h3l4 4 7 2-8-11-4-6z" fill="#483939"/>
<path transform="translate(1420,532)" d="m0 0 2 1-4 4h5l-5 4h-2v2l2 1-12 6-16 7-14 5-11 5-6 2-5 2-9 2h-5l2-4h2v-2l-7 3-18 5-10 1-2 1h-8l3-2 5-2h4v-2l20-6 9-1v-2l20-6 8-3h5v-2l12-4h4v-2l11-5z" fill="#3A2625"/>
<path transform="translate(1657,364)" d="m0 0 2 2 3 16 4 35 5 22 3 21 4 44 2 9-5-2-4-8-2-5-3-24-2-10-3-26-2-23-2-20-1-2h-11l4-3 5-3 1-2 1-19z" fill="#8A5A4C"/>
<path transform="translate(1153,1114)" d="m0 0 12 7 16 10 16 8 19 8 30 9 26 9 18 7 5 2v1l-17-1-48-13-12-4-9-4-14-5-19-10-11-8-11-11z" fill="#979B99"/>
<path transform="translate(1051,869)" d="m0 0h2v3l5-1 5 5 2 4h2l1 4h2l11 17 8 11 9 10 12 11 8 6v2l3 1v2l4 2-3 2 2 4h-5l-11-8-10-8-8-7-7-8-9-10-10-15-12-20z" fill="#654742"/>
<path transform="translate(522,1211)" d="m0 0 16 4 24 5 16 6 4 1h10l10 2 13 4 12 4 13 1 16-1 29 4 2 1v2l5-1 2 2 12-1 18 1 4 2-1 2-9 1h-8l-7-1-1-1-37-1-16-1-12-2-2-1-15-2-15-4-9-2-21-5-16-5-27-8v-2l-10-2z" fill="#1A0F0F"/>
<path transform="translate(1193,917)" d="m0 0 2 4 1 9 9 18 15 10v6l-2 4 13-1 5-2 13-2 12 1 7-2 10-4 3 2-6 4-9 4h-20l-20 4-21 2h-16l-20-4-6-3v-2h23l4-1 13-2 6-4 1-4-7-2-6-13-3-6-5 2-8 6-7 1-1-4 9-7 10-5z" fill="#937265"/>
<path transform="translate(1121,942)" d="m0 0 6 3 5 5 11 7 4 3 6 2h28l20-3 6-2-1-2-5-3 1-4 2 4 6 2 1 3-6 5-10 2-8 1-1 1h-10l-13-1 1 2 10 3 15 3h16l21-2 20-4h20l9-4 4-3h3v2l4 2v2l22 1 5 1v1l-36-1-9 4-7 1-24 1-24 3h-26l-23-5-17-6-26-13 3-1-3-5 3-1-3-2z" fill="#989C9A"/>
<path transform="translate(717,606)" d="m0 0h2v4l-8 7-11 8-19 13-15 10-20 14-17 12-9 6-20 12-13 7h-5v-4l13-8 14-8 10-7 19-13 11-8 13-9 14-9 12-8 10-7 18-11z" fill="#6F6C69"/>
<path transform="translate(786,1471)" d="m0 0 2 1-12 10h-2v2l-10 6-13 8-22 13-18 10-22 11-15 7-3 3-17 8h-3v2l-11 4h-2v2l-5 2-13 6-23 11-18 10-4 3-8 3-7 2-1 3-9 5-7 3-3-1 28-17 17-9 22-12 16-8 15-8 23-11 11-5 19-9 12-7 32-16 17-9 15-9 14-10z" fill="#F7F8F7"/>
<path transform="translate(1803,1008)" d="m0 0 2 3 4 15 5 24 3 31 2 14v7l2-1-1-14 1-2h2l2 18 1 20-1 12 2 34 2 13v8l3 17-1 3-3-8-1-4-2 3-6-60-5-49-4-29v-8h-2l-2-21-3-18z" fill="#463738"/>
<path transform="translate(1065,1516)" d="m0 0 10 2v2l5 1v2l6 2 8 7 7 10 6 15 4 19 1 12 1 5-1-2-5 2v14h-1l-3-19-2-10-6-16-4-10-6-10-7-9-6-4-4-4-5-3v-2h3z" fill="#442B28"/>
<path transform="translate(1189,768)" d="m0 0 2 1-10 6-13 4-10 4-4 4 1 10-2 2 4 10 2 3 1 12h3l1-5 1-4-4-6-2-4 16 2 5 2v2l-6 2-2 2-1 6h-2l-2 6-1 2v7l1 3v7h2l8 18 1 1v5l4 2 8 14 7 15 7 20 3 9-1 3-6-16v-3h-2l-5-12-7-16v-2h-2l-9-17-8-13-2-6v8h-2l-6-16v-25l-8-17-5-9-1-1-16-2-18-1-5-1v-1l37 1 7 3 3 2 1-4 5-6 10-4 16-4z" fill="#9A9A97"/>
<path transform="translate(1264,1874)" d="m0 0h8l64 14 34 7 21 4 10 4 15 4 18 3h18l12 3 3 4-1 1h-14l-39-7-99-22-48-12v-2z" fill="#7FB8C9"/>
<path transform="translate(492,613)" d="m0 0h1l1 15v42l5-1 4-8 7-9 9-9 10-16 8-13 3 1-1 8-7 14-9 15-3 7-10 13-13 13-2 4-1 7v10l3 3v9l-6 11-4 10-4 9-1-3 4-12h2v-5l2-4h2v-36l3-7-3-1-1-2v-34z" fill="#351F1E"/>
<path transform="translate(1503,509)" d="m0 0 9 3 6 12 1 18v14l-2 11-3 11v8l-1 2 2 1-10 4h-2v-5l1-1 1-9 4-10 3-9h-2l-1 4-4 10-6 10h-2v2l-2 1 4 4-8 4-5 5v-3l8-15 6-7 6-15 3-11v-14l-4-8-2-6-6-5v-2h3l1-3z" fill="#443535"/>
<path transform="translate(1058,623)" d="m0 0 33 2h12v1l-22 3-81 6-45 2-59 5-14 5-10 5-1 6 11 2v1h-10l-10-1v-3l6-5 5-5 9-3 3-3 4-2 14-2 42-3 41-2 20-2 23-4 10-2z" fill="#939997"/>
<path transform="translate(836,1052)" d="m0 0h1l1 22 2 13 7 46 6 28 5 21 1 9 2 5 9 36v2l-6 1-3-9-7-30-6-25-5-20-4-28-3-16v-10l-1-4 1-6z" fill="#7A6E68"/>
<path transform="translate(373,907)" d="m0 0 8 1 4 6 1 7h2v10l-5 7-7 14-6 9-9 15-12 6-18 6-10-2h-7l-4 4-2 10-18 18-7 3-3 1h-14l-4-1v-2l-8-1-6-2 4-1 13 3h11l11-6 12-11 6-5 4-10 3-4 23-2 12-6 6-6 6-2 2-4 7-8 7-12 3-4 2-6 5-4-1-9-3-7-7-3z" fill="#DEBFA8"/>
<path transform="translate(151,385)" d="m0 0 4 2v2h3v2h3v2l4 1 12 8 11 7 21 12 24 13 5 2v2l9 3 6 5 17 8 1 4 5 3 5 2 5 5-4-1-12-5-16-8-14-8-4 1-16-10-11-6-19-11-3-3v-2l-15-10-14-10-5-5z" fill="#5C3D37"/>
<path transform="translate(262,762)" d="m0 0 5 2 5 4 6 3 7 6 9 11 4 2 1-3h6v3l5 2 6 4 1 2 5 2 1 3 4 2 4 4 6 3 2 5h2l7 8 14 14 7 8 3 3-1 2-10-9-2-1v5l5 1 3 4-1 3-1-3h-2v-2l-6-2v-2l-4-1-7-8-2-4-3-2v-3h-2v-2l-4-1-8-7-4-6-3-4v-2l-4-2-1-3-4-1v14l-2-4-2-13 2-1-2-3h-11-2l5 4-1 3-13-13-6-4-8-7-8-10z" fill="#432B29"/>
<path transform="translate(1804,968)" d="m0 0 2 4 10 37 6 31 4 31 5 67 4 40 4 28-1 4-2-9-4-22h-1l-1 9h-1l-3-19-2-37 1-14-1-25-2-21-5-27-4-29-10-45z" fill="#957365"/>
<path transform="translate(216,861)" d="m0 0 6 1 5 5 11 5 8 7 12 20 9 14 8 9 3 6 5 5 5 6v2l3 1 7 9 5 3 2 3v3l3 1 7 8 3 2h6l13-3 6-4 7-2 4-7 6-5 6-11 2-3v-16l2 3 2 6v11l-5 5-7 11-8 10-14 7-10 2h-9l-11-8-8-8-4-2-5-8-14-15-6-5-3-6-7-9-10-16-8-13-3-6-9-8-10-5 6 9-1 3-9-12z" fill="#DDBEA7"/>
<path transform="translate(1912,686)" d="m0 0 2 4 1 9-2 8-1 8-1 1-1 10-6 10-4 7h-2l-2 4-12 12-6 5h-2v2l-5 3h-5l-1-3 1-2-2-1 5-7 11-9 8-8 8-13 6-13 4-13z" fill="#1F1110"/>
<path transform="translate(1341,567)" d="m0 0h3v2l-3 3 3 2-21 7-9 2-25 6-5 2-26 5-34 7h-10l3-2 5-2 17-3 7-2 6-1 7-2 12-3 3-2-12 1v-4h2v-2l9-2 20-3 9-3h4v-2h5v2l-9 3 12-1 12-3 11-3z" fill="#4A3938"/>
<path transform="translate(232,878)" d="m0 0 4 2 4 5 12 20 7 11 9 11 7 8 5 5 9 11 6 5 7 8 5 6 5 3 3 3v2l-5 5-3 9-5 2 3-11 1-7-10-11-4-4-8-5-5-3-10-9-7-9-8-11-8-16-8-15-4-8-2-3z" fill="#341E1D"/>
<path transform="translate(925,587)" d="m0 0h11l8 4v3l-5 2-3-1 2-1 1-3-8-1-21 3-32 8-36 12-22 9-16 6-20 8-36 15-27 13-10 6-11 5-19 10-7 6-8 4-7 2 2-3h2l2-4 2-3 9-4 18-10 20-9 13-6 17-8 15-7 29-12 13-6 30-12 28-10 26-8 26-6z" fill="#919896"/>
<path transform="translate(180,1007)" d="m0 0 3 1 4 5 7 16 8 16 8 14 9 8 9 6 12 12-5-1-2-1h-6l-1 5 2 2 3 2 3 10 4 4 1 10h-3l-7-12v-2h-2l-3-11v-2l-5-5-7-10-7-11v-2l-4-2-6-11v-2h-2l-1-6h-2l-4-11-5-10z" fill="#36201F"/>
<path transform="translate(641,707)" d="m0 0h2l-2 4h3l5-2 3 3 3 1-12 6-12 7-8 4-11 6-11 5-8 4-11 4-24 12-10 4-12 4-7 3-6 1-1-2 15-6 3-2 8-2 13-6 3-3 28-14h2l1-4 7-2v-2l4-3 7-3 13-8z" fill="#331816"/>
<path transform="translate(1852,261)" d="m0 0 3 3v12l-8 28-4 9-4 10-4 13-4 9-6 16-8 15h-1v-6l4-7 1-4h-2l2-6 4-7 1-8 1-5h-2l3-9 5-14 7-19 7-20z" fill="#4D3C3A"/>
<path transform="translate(1701,928)" d="m0 0 2 1-1 2h-2l-2 4-24 24h-3v2l-6 5 5-2 2-1-2 5-14 11-10 7-12 9-6 3v-2l-16 9-5 4-15 5-10 5-22 6h-13l-9-2-10-2v-2h-5l-5-5-7-1-1-2-3-2 4-1-2-3 4 1 2 4 4 1 7 3 14 4 8 3h20v-2l11-4h6v-2l8-3 26-13h2v-2l6-2v-2l5-2v-2l5-3h2v-2l5-3h2v-2l6-4 7-6 10-8 5-5 8-7 7-7 8-7 2-3h2z" fill="#7C4A3E"/>
<path transform="translate(1816,1326)" d="m0 0 2 1 5 23 5 16 8 38 5 27 2 22v15l-2-3-10-43-11-55-4-28-1-11z" fill="#6F6C69"/>
<path transform="translate(1284,1717)" d="m0 0 4 1h15l-1 2-49 8-38 5h-7v2l-8 1h-31l-8-1-1-2h2l-1-4 39-4 16-1-1 2h15l6-2 11-1 17-3h17l1-2z" fill="#351F1E"/>
<path transform="translate(204,1061)" d="m0 0 4 5 7 11 7 10 3 2 2 13h2l8 14h1l-1-10-4-4-3-10-4-2-1-4 2-4h6l4 1-4-5 4 2 23 15 8 4 7 4v2l4 2 5 4 18 10 10 6-3 1-9-5-10-4-21-12-23-14-11-7-3-1 4 11 11 17 2 4v15l-1 3-4-2-2-5-4-5-6-11-4-5-9-17-3-5-1-6h-2l-6-9-3-6z" fill="#4A3838"/>
<path transform="translate(688,697)" d="m0 0h9l-2 4-8 6-23 11-17 11-7 4-11 7-26 13-6 1v-2l4-3h2v-2l12-8 5-2 1-4 10-6 11-6 6-4h4v-2l17-9h2v-2l14-6z" fill="#FBEBD6"/>
<path transform="translate(1908,1649)" d="m0 0h1l2 26v55l-2 39-1 10h-1v-11l1-24-3 1v2h-2l-2-9-2 36-2 4 1-25 1-19 1-56h1l1 14 1 2 1-25 2-4 1 2z" fill="#514544"/>
<path transform="translate(374,854)" d="m0 0 4 2 22 22 5 4 4 5 9 7 5 5 4 3v2l7 1 1 1h9l12-9v3l-3 1 1 5-1 2 12-1-1 3-14 4-10 2-6 2-16-4-3-3-9-5v-2l-4-1-17-16-7-8-4-1-5 2-1 4h-2l2-5 5-5 6 1 9 11 8 8 5 2 8 6 2 1 1-2h5l-7-8-7-9-9-9-8-7-12-13z" fill="#2F1210"/>
<path transform="translate(710,678)" d="m0 0 5 1 4 4-1 3-11 4h-3l-1 3-13 4-24 10-10 5-5 1-2-3-5 2-5 1 5-8 18-10 10-4 6-3 10-3z" fill="#1D100F"/>
<path transform="translate(1658,190)" d="m0 0h2v90l4 53 3 22 2 21 2 12 5 42 3 22 2 44 2 12 1 3 2 2-4-1-3-8-2-34-6-51-4-23-3-39-3-27-3-42-3-27v-57z" fill="#C39F8A"/>
<path transform="translate(610,739)" d="m0 0 2 1-10 6-18 10-21 11-33 13-13 4-9 2-11 1h-19l-13-1 4 10 9 12 13 22 1 7h-2l-4-10-12-19-7-10-3-5v-4h-2l-1-8 2-2h10l15 2h10l15-2 23-7 28-11 22-10 9-5 10-4z" fill="#C59E88"/>
<path transform="translate(1465,964)" d="m0 0 2 1-9 5-4 1-3 6v5l6 2 6 3 1 2 8 1 4 2 7 1h12l7-2v-2l4-2h12l-2 2-8 2-12 4h-22l-36-6-4-2-14-2-6-3-1-4 4-3 25-6 18-3z" fill="#DDBDA7"/>
<path transform="translate(811,1462)" d="m0 0 2 1-10 9-8 6-12 8-16 12-6 1-11 7-20 12-15 8-6 2-7 1-8 2-5 3-6 1v2l-10 3 3-3 39-19 23-13 19-12 7-4 8-5h2v-2l13-10h3l-8 8 4-3h3v-2l4-3 6 1v-2l-2-1 6-5 2 1-3 4 7-7z" fill="#766A65"/>
<path transform="translate(873,606)" d="m0 0 3 1-1 4-12 7-16 5-15 6-16 4-24 8-7 3-10 2-6 2-8 4-12 3h-2v-2l9-4 7-3 25-10 31-12 12-4 21-8 18-5z" fill="#7C4538"/>
<path transform="translate(161,952)" d="m0 0 8 6 10 4 12 9 18 13 16 10 14 8 8 3-1 3 5 1 13 4 6 2v1h-9l-13-3-9-2-10-5-3-1v-2l-6-2-16-7-10-10-2-3-8-4h-6l-3 1 2 9 1 4-3-3-3-8v-6l1-1 10 1 1-3-3-4v-2l-10-3-5-3v-2l-4-1z" fill="#714940"/>
<path transform="translate(1726,1893)" d="m0 0 3 1-1 3-45 13-41 7-22 3h-13l2-2 8-3 11-3 5-3 17-3 11-1 7 1 1-2h7l13-4 25-4z" fill="#7EB8C9"/>
<path transform="translate(368,629)" d="m0 0h3l3 9 3 1 8 14 2 2 3 9 6 13 3 7 1 13h2l1 3 2 16 6 12h-2v3h2l4 8 8 7 3 3-1 3-9-9v-2l-4-1-5-6-2-6-4-4-3-7-2-14-3-8-1-13h-2l-9-19v-3h-2l-6-10-4-11z" fill="#221212"/>
<path transform="translate(419,79)" d="m0 0 4 1-8 7-7 5h-2v2l4 1-40 10-30 9-8 2v-2l14-7 9-5 12-8 21-7z" fill="#CBD7DE"/>
<path transform="translate(827,941)" d="m0 0h4l-1 64v24l1 31 1 21v6h-2l-2-6-3-30-1-18v-89z" fill="#36201F"/>
<path transform="translate(1385,632)" d="m0 0h8l-5 4-9 1-2 5-17 7-8 4-7 4-7 5-8 3-13 10-16 12-4 2 2-10-5 3h-3l6-5 14-10 5-4 7-3 9-6 23-11 16-6 10-3z" fill="#351A18"/>
<path transform="translate(1776,855)" d="m0 0 1 4-8 10-3 3-3 5-5 6h-2l-2 5-4 4-6 7-9 11h-3l1-4 7-8 9-10 4-7-7 6-6 8-5 6-8 7-11 11-7 8-4 5-8 7-15 14-2-1 19-19 1-2h2l2-6 20-20 7-8 13-15 12-14 5-4h2l2-4 5-1 3-3z" fill="#331715"/>
<path transform="translate(1826,1194)" d="m0 0 2 4 3 11 6 43 2 18 2 11 7 49 4 23 5 40 2 10v7l-4-4-4-25-9-62-6-42-7-46-1-12-2-10z" fill="#372221"/>
<path transform="translate(247,1101)" d="m0 0 17 8 10 4 19 10 19 11 15 9 6 3v2l4 1 10 6 7 4-3 1-5-3-21-11-9-6-12-7-12-6-12-5-7-1-5 3-6 12-5 15-4 4 3-10 1-5-1-8-1-11-4-7-5-6v-6z" fill="#9EA09D"/>
<path transform="translate(359,842)" d="m0 0 4 2 11 9 7 8 9 10 12 11 6 7 7 8 2 4-8 2-8-6-6-3-9-9-7-8-1-3-6-4-2-4-1-9h-2l-2-7-2-2-4-1-1-3z" fill="#160A0A"/>
<path transform="translate(1089,888)" d="m0 0h2l2 2h3l7 8 5 4 3 1 4 4v2h3v2l5 2 22 12 5 5 5 4 2 7h-5l-5-4v-2l-6-2-2-1v2l-5-1-8-4-11-8-2-4-6-2-9-10-8-12z" fill="#603E38"/>
<path transform="translate(1556,583)" d="m0 0 3 1-2 2-13 4-5 1v2l-12 5-7 3-8 2-15 4h-2v2l-16 6-11 3-13 5-12 3-4 2-12 2-7 1 2-4 5-1v-2l4-2h6v-2l5-3 6 1 6-1v-3l7-2 20-4 5-5 5-1 8-1 5-2 7-1 9-4 21-6z" fill="#7C483C"/>
<path transform="translate(833,399)" d="m0 0 3 1-8 7-7 6h-2v2l-11 9-9 7-11 8-13 11v3l-11 8-13 11-17 13-10 7-9 4-3-1 22-18 15-13 11-9 11-10 14-11 13-10 4-2-4 5 9-6 7-7 10-8z" fill="#6E6B68"/>
<path transform="translate(1385,41)" d="m0 0 10 1 40 10 27 8 36 12 33 12 24 10 11 5-4 1-12-6-20-7-35-13 1 1-4 1-57-18-12-3-1 2-15-6-19-7z" fill="#97C2C5"/>
<path transform="translate(1511,1170)" d="m0 0h5l-1 9-8 22-3 7-2-2-2 6-4 4-11 24-4 4-7 18-4 6-6 11-11 18-3 3 2-6 4-7 1-4 2-1 6-11 12-25 13-32 3-10 1-2h2v-9l3-1 8-17 4-4z" fill="#949B99"/>
<path transform="translate(1094,899)" d="m0 0 4 4 9 11 4 2 6 9 11 10 9 6 5 6 5 2 2 4-10-1-21-11-5-5-13-11-1-5-10-12v-6z" fill="#FCF0DD"/>
<path transform="translate(178,976)" d="m0 0 9 1 7 5 7 8 5 4 18 8 2 1v2l5 1 8 4 6 2v2l3 1-8-1-7-3-9-3-4-4-6-2h-28l1 6-3-1-2-7-4-7-4-12 1-4z" fill="#926F62"/>
<path transform="translate(1651,224)" d="m0 0h2l1 71 3 44 4 30 1 13h-1l-3-16h-1l-1 19-3 3 1-4-1-19-4-46v-60l1-27z" fill="#6F6C68"/>
<path transform="translate(763,1497)" d="m0 0h2v2l-4 1v2l-22 14-4 2h-3v2l-19 12-16 9h-3v2l-7 4h-3v2l-9 5h-2v-2l2-2h-10l-1-2-12 5-3-1h2v-2l20-9 10-4h2v-2l9-4 4-2 11-1 3-2 9-3 13-7 13-8 10-6z" fill="#61403A"/>
<path transform="translate(1753,467)" d="m0 0h2v7h1l-1 7-6 5-1 2h-2l-1 3-7 3-8 6-17 11-11 7-8 4-6 4h-2l1-3 12-7-4-3-4 2-4-1 4-3 13-6 19-11 12-8 6-5 9-12z" fill="#3B1C19"/>
<path transform="translate(66,952)" d="m0 0 1 2 4 2 4 5v2h2v-6l2 4h2l6 11 2 1 4 7 6 9v2h2l5 8v2h2l3 5v2h2l4 7 3 2v3h2l4 7 2 1v2h2l1 4-5-3-3-6-9-9v2l-1 2h-2l-1 2-8-12-3-5-4-4-1-5-3-1-9-12-4-5-2-5h2l-7-11-5-7z" fill="#452B27"/>
<path transform="translate(1817,796)" d="m0 0v3l-17 17-10 13-12 14-11 13-9 11-10 11-9 11-12 13-9 10-6 6h-4l2-5 12-13 7-8 1-2h2l2-4 8-10 10-12 8-7 5-6 5-5 9-10 10-13 6-8 12-12z" fill="#FAE9D5"/>
<path transform="translate(487,737)" d="m0 0 1 4-3 9h4v2l6 1 8 4 14 2 10-2 5-2 20-5 5 1 1 2-13 3-19 6-6 2-24 4h-17l-3-2v-8l5-7 5-12z" fill="#9E9F9C"/>
<path transform="translate(113,1015)" d="m0 0 5 3 3 4v2l3 1 4 7 3 2 3 7 9 13 5 10 6 9 4 7v2h-4l4 8v2l-3-1-7-11-8-13-8-12-4-7-10-15-2-5h-2l-4-8 1-2h2z" fill="#1C0F0F"/>
<path transform="translate(491,691)" d="m0 0h1l1 17v12l-1 4h-2l-2 9h-2l-3 12-2 5h-2l-1 4-4 2-5 17-3 3-4 1-1-6 1-8 3-6 4-12 5-10 3-1 7-14 3-9v-13h1l1 6h1z" fill="#1A0E0E"/>
<path transform="translate(1038,766)" d="m0 0 7 1v1h-5l2 10 7 19 8 16 9 16 8 14 7 14 12 22 11 17 6 7-4-2-5-4-6-7-3 1-1-3h-2l1 4-4-4-5-10v-3h-2l-4-9-7-15 2-9-7-14-6-9-8-16-7-16-4-12z" fill="#79706A"/>
<path transform="translate(1653,980)" d="m0 0m-1 1m-1 1 1 3-6 5h-2l-2 4-10 6-9 9-10 6-9 5h-5v2l-11 4-9 3-8 1h-14v-1l11-1 13-5v-2l-6 2-4-1 6-3 9-3 8-4 13-4 10-7 9-5 3 1 9-6 8-6z" fill="#392423"/>
<path transform="translate(832,893)" d="m0 0h1v91l2 38v15l-2-4-2-16v-76h-4l-2 4-1 53h-1v-64l1-28 2-9 4-2z" fill="#473B3B"/>
<path transform="translate(858,1403)" d="m0 0v3l-3 1-2 4-9 11-1 5 2-2h3l-1 5h-2l-1 7-1-2-3 1-2 4-4 2-2 4-5 3-7 8-5 5-7 3-6 6-2-1 3-4-5 4 1 3h-6l-4 2v2l-5 3-3 2 2-4 8-8h2l2-4 8-5 3-5 11-10 7-5 4-4h2l2-5 7-7 6-8 2-5 5-4h2v-2z" fill="#6B4138"/>
<path transform="translate(420,642)" d="m0 0h2l-1 8-3 8-4 13-3 8-5 4-1 7-2 5 2 10 4 13 3 6v3l-4-5-4-10-1-1-1-14h-2l-2-13-8-19-3-5v-5l3 1 7 10 4 1 5-5 5-6 4-10 3-1v-2z" fill="#DDBEA7"/>
<path transform="translate(814,635)" d="m0 0 4 1-7 3 2 3-10 1v2l-16 4-25 6-12 4-9 2v-3l-8 3-1 3-8 4-12 4-32 16-4 1 5-5 15-8 40-20 21-10 6-1-1 3-13 5h-2v2l12-3 10-5 7-2 17-4z" fill="#927265"/>
<path transform="translate(1840,1403)" d="m0 0h2l7 39 4 21 5 31 6 29 2 13 1 6 6 1 4 10 4 18v5l-3 3-5-3-4-9-7-32-15-90-7-38z" fill="#B3BEBE"/>
<path transform="translate(232,1085)" d="m0 0 5 1 19 12 8 5-2 1-5-3-12-3 1 8 9 12 1 5 1 14 1 5-5 13-6 9-7 4-14 1-16-6-1-2 15 5h13l7-5 3-8 3-27-2-9-7-12-7-11-2-5z" fill="#8D7267"/>
<path transform="translate(856,1249)" d="m0 0h5l6 6v8l-2 1-18-1-3-1-32-1-17-2-1-3 12-2 27-1 12-1 6-2z" fill="#9D9F9C"/>
<path transform="translate(1161,1841)" d="m0 0 7 1 24 7 74 21 36 9 32 7 31 5-4 2-9-1-49-10-31-7h-6l-4 1-26-8-53-18-22-8z" fill="#9FC7CA"/>
<path transform="translate(1994,580)" d="m0 0 3 1h-2l-2 4-5 6h-2l-2 4-7 7-5 6-5 1v-2h2l-2-2-3 3h-2l-2 4-4 6h-2l-2 4-4 4-4 7-6 5h-2l1-7 9-13 11-13 9-11 9-10v3l-2 4h3l1-2 4-2 4-4 7-1z" fill="#381916"/>
<path transform="translate(822,892)" d="m0 0h1v93l1 13 1 35 2 31 6 45 6 34 4 19 1 8 3 8 9 37v7l-2-4-5-13-3-13-5-22-5-21-7-45-2-20-2-15-2-29-2-45v-78z" fill="#8D8F8D"/>
<path transform="translate(353,893)" d="m0 0 5 5 5 6 5 7 5 15 4 7 6-7-2-9-9-7-6-5 1-4 1 3 4 2 3 3 6 2 3 4 2 7v6l-6 5-2 7-4 5-8 13-7 8-8 5-5 5-11 5-12 1h-10l3-2 18-3 3-2-8 1h-9v-1l18-3 12-6h2l2-4 8-10 6-10 3-2v-11l-6-18-8-11-4-3z" fill="#81574B"/>
<path transform="translate(1367,761)" d="m0 0 3 1-7 8-5 2-10 8-7 7-10 8h-2v2l-6 1h-3l-12 6h-3v2l-13 4-23 3-21 3-13-1-21-3-31-4-4-2h8l25 3 18 2 10 2 7 1 21-3 3-1 1-2 4-1h13l4-2 9-2 12-4 14-10 6-4 11-10 5-5 6-5h2v-2z" fill="#DEBFA8"/>
<path transform="translate(1388,937)" d="m0 0h9v1l-17 4-19 3-5 2-14 2-12 3-12 2-8 2-1 5-14 4h-9l-5-5 1-5 10-2 21-2 34-8 30-5z" fill="#351E1C"/>
<path transform="translate(942,1401)" d="m0 0 4 4 9 15v2l5 2 5 5 3 11 9 12 11 12 13 14 10 8 10 7 17 7 15 4 6 3 9 4 11 7 6 7-5-2v-2l-5-1v-2l-9-3-16-5-19-7-18-11-10-9-1-2-5-3-13-13-9-11-2-1-1-3-4-4v-4h-2l-8-11-4-8-10-16z" fill="#949A97"/>
<path transform="translate(1563,1463)" d="m0 0 3 3 2-3h3v2l3 1-4 9-12 32-6 19-3 11h-2l-1 2v-8l4-15v-6l-1-1v-10l4-10z" fill="#3C2927"/>
<path transform="translate(747,586)" d="m0 0 3 1v3h-2v2l-18 13-13 8h-3l3-3h2v-4l-30 19-10 7-17 11-14 10-20 14-27 18-11 6-8 5v2l4 2-7 1-3-2 2-4 16-9 14-8 20-14 18-13 14-10 15-10 26-17 22-14 17-11z" fill="#919896"/>
<path transform="translate(1293,811)" d="m0 0h7v1l-19 3h-4v2l-6 3h-10l-4-1-5 4-5 9h-2l-2 5-4 5-7 12h-2l-1 5-4 5-6 2v-5l2-3 3-9 7-10 1-3h2v-3h2l2-5 4-6v-4l7-2 21-2 19-2z" fill="#86594C"/>
<path transform="translate(1370,944)" d="m0 0h5l-8 4-1 5 3 2 7 1 26 2 7 3 11 1 36-6 16-5 12-3 10-3h5l-1 4-3 3-4-1h-2v-2l-27 9-24 5-14 1-5 1h-19l-13-3-7-2-22-2-6-2v-5l4-3z" fill="#DEBFA8"/>
<path transform="translate(1463,918)" d="m0 0 3 1-5 3-19 5-21 3-35 4-30 5-33 7h-3v2l-13 3-7 1-19 1-6 3-11 2-14 1h-10l-12-6 2-1 9 3h22l10-2 8-3 22-2 38-9 28-6 33-4 30-3 13-2h5v-2l14-3z" fill="#C59E88"/>
<path transform="translate(1605,420)" d="m0 0v3l-7 8-3 2-4 7-12 13-10 10h-2v2h-2l-2 6-6 7-6 2-11 6-17 10-10 4-3 1v2l-5 1 3-3 2-4 17-10 15-10 11-8h3l2-4 11-9 10-9 5-6 5-5 11-10z" fill="#D1B4A0"/>
<path transform="translate(404,712)" d="m0 0 3 4 4 9 9 7 8 10 6 5 4 6 2 6 8 7 7 6 2-3 3-10 5-9 1 2-4 10-3 16-4 1-12-12-5-4-4-7-2-1 4 7 6 8 3 6 8 10 9 14-1 2-4-6v-2l-3-1-4-7-10-13-5-8-8-11-3-6-12-12-1-5h-2l1-4-3-4-3-7z" fill="#63403A"/>
<path transform="translate(1042,769)" d="m0 0 5 1-2 3 5 14 3 7 7 12 4 10 8 13 8 17 8 14 8 16 7 10 7 11 17 12 17 9 17 6 9 4h8l12-5 2-1-2 4-9 4-5 2h-6l-18-8-15-6-19-11-11-10-11-17-6-9-11-21-10-19-9-15-6-14-5-7-6-18-2-7z" fill="#B2BEBE"/>
<path transform="translate(1875,249)" d="m0 0h50l46 2 22 2 7 1v1l-94-1-37 1-9 2-5 3h-3l-1-4 4-4z" fill="#FFF2DE"/>
<path transform="translate(1117,1654)" d="m0 0 2 1 4 16 10 28 10 19v3l9 2h1l-1-5 2 1v3h2l3 3 3 1h13l29-3 45-7 12-1-2 2-8 2-16 2-1 1-21 3-30 3-22 1 1 4-1 1 8 1v1h-12l-9-7-5-2-4-4-6-15-10-28-6-23z" fill="#706C68"/>
<path transform="translate(1163,1580)" d="m0 0h7v1l-9 2 2 4h15l16-1h11v1l-39 4-19 1-16 3h-17v6h-1l-1-13 6-2 26-3 11-2z" fill="#4D3D3B"/>
<path transform="translate(857,1226)" d="m0 0 2 1 2 10-6 2-9 1-53 3-26 1h-59l-14-1-2-1-10-1v-1h39l59-1h31l44-3z" fill="#CAB5A4"/>
<path transform="translate(1411,1688)" d="m0 0 4 1-2 2-15 5-15 4h-6l-1 3h-2v2l-18 4-17 3-10 2h-7l4-2 8-1v-2l8-4 7-3 1-1h7v-2l14-2 3-3 12-2 2-1z" fill="#351F1E"/>
<path transform="translate(201,1042)" d="m0 0h2l3 9h2l5 8 5 5 12 8 14 10v2l5 1 12 7 9 5 21 12 39 20 1 3-18-6 11 6 1 2-9-3-4-2-3-3-20-11-9-6-5-4v-2l-4-1-6-4-10-5-18-12-24-18-6-7-6-11z" fill="#804C3F"/>
<path transform="translate(968,1739)" d="m0 0 6 1 32 12 43 19 26 10 20 7 4 3-5 1-40-14-26-11-28-12-21-8-8-4z" fill="#81B9C9"/>
<path transform="translate(295,480)" d="m0 0 5 2 11 7 8 4 10 6 10 5 17 10 11 7 7 5 9 5 9 6 5 5 1 2-5-1-26-16-24-13-5-4-11-6-7-5-9-5-7-6-8-4-2-3z" fill="#FBEAD5"/>
<path transform="translate(1126,1651)" d="m0 0 2 3 11 32 10 25 3 5 2 7 1 2-4-1-6-2-2-1-8-16-4-9 1-3 1 4h2l-7-23-2-7z" fill="#664640"/>
<path transform="translate(90,268)" d="m0 0 1 2 1 8 5 13 4 11 2 8 1 9 3 9v7h-1l-3-11-1 1 1 12-3-4-1-11h-2l-2 4-2-5-2-10-5-26v-11z" fill="#997C6F"/>
<path transform="translate(1469,960)" d="m0 0h5l-2 1v2l-11 3-5 2-18 3-14 3-10 2-2 2-1 5-10-1-1-1-9-1-6-3-1-2 12-3 21-3 24-5 20-2z" fill="#351917"/>
<path transform="translate(756,1588)" d="m0 0h2l-2 4-13 21-10 18-7 12-5 6-3 4h-2l1-10 8-15 3-6 9-15 5-9 4-5 1 2z" fill="#4D4241"/>
<path transform="translate(239,445)" d="m0 0 11 6 26 13 9 3-5-4-5-2-6-4 4-1 8 4 10 4 22 12-3 3 3 3-1 2-15-7-7 1-8-5-17-10-10-5-17-10z" fill="#3C2422"/>
<path transform="translate(707,711)" d="m0 0h1l1 62 1 7 3 6v2l-4 1-2-3v-3l-3-1-3-14v-48z" fill="#957365"/>
<path transform="translate(1388,758)" d="m0 0 2 1-5 5-8 10-4 6-6 3-4 6-16 16h-2v2l-11 7-7 4-11 3-7 1-30-1-7 3-16 3-3-1-3 1 2-5 5-1h12l7-2 2-2h38l14-5 13-8 15-14 6-8h2l2-5 9-10 6-5 1-2z" fill="#C39D87"/>
<path transform="translate(403,544)" d="m0 0 5 2 15 10 11 8 14 11 13 11 8 7 8 9 5 10 1 6 1 45 3 26 1 22-5 13-6 11h-2v-4l2-1 7-15 1-3v-14l-2-4v-13l-2-24-1-43-4-8-5-5-4-6-13-11-5-3-5-6-6-3-5-5-4-2-1-2-3-1v-2h-3l-1-2-3-1v-2l-4-2-3-1-4-4z" fill="#926859"/>
<path transform="translate(1636,394)" d="m0 0 1 2-5 1v2l-12 6-12 12-11 13-8 7-5 5-12 13-14 11-2 3-3-1 10-9 8-7 7-8h2l2-4 3-1 5-10-2 1-5 3-4 2 5-6 5-5 9-8 12-12 7-4h2v-2z" fill="#412D2C"/>
<path transform="translate(1556,1673)" d="m0 0 1 4-15 5-28 6-48 9-79 12-8 1h-16v-1l63-10 35-5 40-7 25-4 21-5 9-2z" fill="#969B98"/>
<path transform="translate(1121,942)" d="m0 0 6 3 5 5 11 7 4 3 6 2h28l20-3 6-2-1-2-5-3 1-4 2 4 6 2 1 3-6 5-10 2-8 1-1 1h-10l-13-1 1 2 10 3 5 1-2 2-13-1-17-6-26-13 3-1-3-5 3-1-3-2z" fill="#929896"/>
<path transform="translate(954,291)" d="m0 0v3l-8 12-9 9-8 7-7 7-8 7-11 11h-4v-2l-6 5h-2v2l-7 6-2-1 7-9 12-11h2v-2l8-6 8-7 16-13 16-15z" fill="#4B3B3A"/>
<path transform="translate(413,1163)" d="m0 0 8 2 9 4 19 6 10 5 15 5 23 8 22 7 14 7v1h-7l-44-15-48-18-20-8z" fill="#F8E5D0"/>
<path transform="translate(1543,1519)" d="m0 0 1 4-2 5-2-1-20 6-8 3-2-1-1 2-2-1-1 2-5 1-2 1-7 1-3 2h-10l-3 1-8-1 2-2 35-12 23-7 10-1 4 3z" fill="#9CA4A3"/>
<path transform="translate(834,1109)" d="m0 0h1l3 16h2l5 30 6 25 10 41 3 13 2 1 1-3v2h3v2l-10 2-1-7-3-9-4-20-8-31-1-1-3-18-6-30z" fill="#463839"/>
<path transform="translate(1441,923)" d="m0 0h7v1l-26 4-29 3-31 4-28 6-33 8-22 2-11 4-7 1h-22l-13-4-6-4 4-1 10 5 6 2h18l14-3 5-2 21-2 15-4 23-6 13-4 22-3 26-3 37-3z" fill="#DEBFA8"/>
<path transform="translate(817,645)" d="m0 0h6l1 2-10 3v2l-13 4-9 3-7 3-17 5-8 3-3-1 2-1-7 1-6 1 4-4 15-6 21-7 7-2-3-2 15-3 1 2-2 1 3 1z" fill="#3D2523"/>
<path transform="translate(1062,860)" d="m0 0h2l5 9 3 3 4 11 2 5 5-1 3-1 8 11-1 4-3 1v6l10 12 1 3h-3l-8-8-10-14-10-15-6-16-3-9z" fill="#F5F6F6"/>
<path transform="translate(836,1052)" d="m0 0h1l1 22 2 13 7 46 1 5 1 15 1 9-1-2h-2l-1 4-4-19-3-22-3-16v-10l-1-4 1-6z" fill="#6F4B43"/>
<path transform="translate(1666,428)" d="m0 0 2 3v2h2l4 27 4 44 2 9-5-2-4-8-1-4-1-19-2-17z" fill="#453333"/>
<path transform="translate(231,875)" d="m0 0 6 2 6 9 13 22 5 7 5 5 5 6 3 5 10 9 10 11 3 6 5 3 7 7 11 8h9l9-1-4 4-21 4-4 4 1-5 3-3h2l-5-6-5-3-7-8-4-5-3-2v-2l-4-2-7-9-5-4-7-9-7-8-7-10-13-22-6-8-3-2-1 3z" fill="#815549"/>
<path transform="translate(1013,741)" d="m0 0 15 5 11 6 12 4 31 7 22 4 8 1h50l-6 3-51 1-12-2-10-1-2-1v2h-2v-2l-6 1 1-3h-6l-7-3-16-4-2-1v-2l-6-2-11-6-9-3-4-2z" fill="#A28070"/>
<path transform="translate(2047,529)" d="m0 0 1 3-8 7-6 7-7 7-3 8-10 15-9 8-10 3-4 2-7 8-6 6-2-1 9-9 1-2h2l2-4 5-6h2l2-4 12-13 5-5 10-8 7-8 11-12z" fill="#F3D1B7"/>
<path transform="translate(870,1234)" d="m0 0 5 4 1 6v9l2 10 10 30 7 15 5 12 11 24 8 17v2h-2l-4-7-3-9-8-16-7-15-5-11-5-8v-3h-2l-6-15-5-13-3-12v-7l3-1 1-6-3-3z" fill="#8E7367"/>
<path transform="translate(1825,1104)" d="m0 0 2 1 2 21 1 1 5 51 4 28-1 4-2-9-4-22h-1l-1 9h-1l-3-19-2-37 1-14z" fill="#7F746E"/>
<path transform="translate(1548,1502)" d="m0 0h1l1 7 1 5-2 9-2 8v6l1 4-3 13-3 17-2 2-4-3v-18l3-13 1-10 3-6 2-10z" fill="#4B3F3F"/>
<path transform="translate(253,747)" d="m0 0 5 3 17 17 12 9 4 5 5 4-2 4-9-10-8-8-8-4-5-4-2-1 6 9 8 9 11 8 13 13 1 9-2-3-3-7-7-4-10-7-7-6-7-9-6-8-7-15z" fill="#DDBEA7"/>
<path transform="translate(1448,715)" d="m0 0h5l7 3-1 3-12 2-5 2-1 4-5 2-6 2v2l-8 3-4 1v2l-7 6-9 2 3-3 4-2 5-6 2-2v-3l-5 1 4-4 10-6 9-4 11-2z" fill="#3F201C"/>
<path transform="translate(1449,1300)" d="m0 0 2 4-11 16-5 8 5-4v4l-9 14-3 5-2 3h-2l-2 4-4 6-7 6-2 5-5 4-4 5-4 2h-3l1-3 8-7 9-11 5-9 4-8h2v-3h2l2-5 4-7h2l2-5 4-8h3l2-6 5-9z" fill="#7A7876"/>
<path transform="translate(1510,559)" d="m0 0h2l-1 8-2 2-3 9-1 9-2 6 6-3h7l-1 4-2 2v2l-6 2-5 1-9 2h-6l-4 5-4 1-2-2 6-8 6-3 4-4 5-2-4-4 3-1v-2h2l2-5 5-9z" fill="#301513"/>
<path transform="translate(1420,532)" d="m0 0 2 1-4 4h5l-5 4h-2v2l2 1-12 6-8 3h-6l2-4-10 4h-3v2l-9 2-10 3 1-2-3-2 8-3h5v-2l12-4h4v-2l11-5z" fill="#3B1D1A"/>
<path transform="translate(1453,1681)" d="m0 0h23l1 4-4 3-22 6-24 4h-7v-2h2l2-4 12-3 13-2 4-2-10-1 1-2z" fill="#603F3A"/>
<path transform="translate(1191,935)" d="m0 0 4 1 4 9 2 1 2 7 5 3-3 3-17 3-9 1h-7v-1l15-4h8l2-4-2 1h-7l-6-2-5-2-1-4 8-7z" fill="#9E9F9C"/>
<path transform="translate(1630 1e3)" d="m0 0 3 1 1 30 1 69v59l-2 44-1 15h-1v-17l1-27v-74l-2-96-3-3z" fill="#BFA898"/>
<path transform="translate(1108,1560)" d="m0 0 3 1 5 5 6 5 3 5 7 3 17 1 6-1 2 2-13 3-26 3-7 1-2-18-1-3z" fill="#F3F5F5"/>
<path transform="translate(157,1114)" d="m0 0 4 4 5 6v2l3-2 4-1 4 5h3l8 11 1 11-2 4-5 1-4-1-4-9-5-9-7-12-5-8z" fill="#B1BBBB"/>
<path transform="translate(593,735)" d="m0 0 2 1-3 3-30 15-12 5-25 7-18 4-12 2h-15l-7-3v-9l4-4v10l2 1h17l24-4 11-4 14-4 16-4 12-5 5-3z" fill="#6F6B68"/>
<path transform="translate(965,711)" d="m0 0 6 3 12 9 1 4 3 7 9 4 8 5 17 8v2l5 2-1 3-4-3-10-3-6-4-5-2-6-4-5-2-18-11-11-8 3-2 5-1 1-2h-2v-2l-3-1z" fill="#442D2B"/>
<path transform="translate(391,1159)" d="m0 0 9 1 12 5 30 12 35 13 37 13 22 7v1l-9-1-26-8v-2l-7-1-13-5-23-6-12-6-5-2-9-1-21-8-1-3-6-2-10-4z" fill="#7F4A3D"/>
<path transform="translate(723,1630)" d="m0 0v3l-5 10-2 10 9-9-2 5-7 11-4 5-5 2-1 4-3 7h-2l-2 4-3 4-5-1-1-3 7-11 3-9 5-5 2-5 5-2 4-10 4-5z" fill="#9DA09D"/>
<path transform="translate(985,1466)" d="m0 0 7 6 7 7 4 2 5 5 8 7 15 9 24 9 14 4 2 2-6-1 1 4h-3v2l5 2 4 4-6-2-14-7-24-9-11-3-3-3 11 3 15 5 1-1-19-10-3-2v-2l-4-2-9-7-17-16-4-4z" fill="#6F6A67"/>
<path transform="translate(881,1293)" d="m0 0 4 1 6 11 18 39 4 7 4 12h4l6 13v2h2l3 6-1 2-4-4-2-3v-4l-3-1 1 4-3-1-5-8-8-18-4-7-2-11h-2l-1-4h-2l-5-13-9-19z" fill="#673F38"/>
<path transform="translate(1630 1e3)" d="m0 0 4 2 2 8 1 95v33l-1 50-1 13-2 1v-14l1-27v-59l-1-69-1-30-4-1z" fill="#8A7166"/>
<path transform="translate(1636,1013)" d="m0 0 2 1 1 86v35l-1 23v39l-1 29h-1l-1-22v-16l1-47v-33l-1-94z" fill="#613E38"/>
<path transform="translate(945,634)" d="m0 0h55v1l-45 2-59 5-14 5-10 5-1 6 11 2v1h-10l-10-1v-3l6-5 5-5 9-3 3-3 4-2 14-2z" fill="#A5ACAB"/>
<path transform="translate(668,705)" d="m0 0 3 1-17 9h-2v2l-7 3-11 7-10 5-14 8-11 6-10 4-16 8-24 10-25 9-16 4-10 1h-10l-25-3v-1l11-1 12 2h16l15-3 20-6 28-11 14-7 7-3 20-10 1-2 9-4 12-7 14-7 6-4 16-8z" fill="#7D4639"/>
<path transform="translate(1477,913)" d="m0 0h5v4l-2 3h-2l-2 4-4 4-9 3-13 1 1-2 4-1-9 1-24 3-26 3-17 1 2-2 16-2 14-1 36-5 8-3 1-2 7-2 4-3z" fill="#7F4A3D"/>
<path transform="translate(866,677)" d="m0 0h2l-2 5-2 6-3 21-4 24-9 43-6 42h-1v-16l4-28h2l1-12 2-17 7-41 4-20 4-6z" fill="#B99C8B"/>
<path transform="translate(203,1129)" d="m0 0h5l10 7 6 3h6l3-3 4 1 1 4-1 10-4 4-10-2-5-3-4-7-11-12z" fill="#FEF1DD"/>
<path transform="translate(161,952)" d="m0 0 8 6 10 4 13 10 5 7 4 1v2l5 2 7 6 13 8v2l3 1-4 1-7-4-10-4-12-10-9-6-9-1-3 1 2 9 1 4-3-3-3-8v-6l1-1 10 1 1-3-3-4v-2l-10-3-5-3v-2l-4-1z" fill="#37201F"/>
<path transform="translate(751,1497)" d="m0 0 2 1-3 1-2 4-1 1 3-1 2 2-14 8-13 8-10 5-6 2-7 1-8 2-5 3-6 1v2l-10 3 3-3 39-19 23-13z" fill="#8C665A"/>
<path transform="translate(1494,1007)" d="m0 0 9 1 5 3 12 3 3 3v2h5v2h8l5 2 6 1h13l12-3 3 1 6-2 2 2-4 3-11 4 3 2-7 1-14-2-14-4-15-5-25-11z" fill="#5E4440"/>
<path transform="translate(1193,909)" d="m0 0 3 4 1 14 8 18 7 6 15 5h6l12 5 18 1v2l-2 1-15-1-12 3-13 2-3-1 2-10-4-2-10-6-6-9-4-9-1-2-2-13z" fill="#5D3D38"/>
<path transform="translate(1614,999)" d="m0 0 2 1-6 7-8 4-10 3-10 5-22 6h-13l-9-2-10-2v-2h-5l-5-5-7-1-1-2-3-2 4-1-2-3 4 1 2 4 4 1 7 3 14 4 8 3h20v-2l11-4h6v-2l8-3 16-8z" fill="#88584A"/>
<path transform="translate(1200,589)" d="m0 0 3 1-5 2-22 5-51 9-27 4-10 1h-10l3-2 31-5 31-6 29-5 9-1 6-1z" fill="#F7F9FA"/>
<path transform="translate(1848,784)" d="m0 0 3 1-6 4h-2v2l-11 8-13 12-21 21-6 8-3 3-1-4 2-5 9-10 7-8 24-24 4-1 4-3 6-2z" fill="#402927"/>
<path transform="translate(1011,232)" d="m0 0 2 1-10 10-8 7-12 12-8 7-4 4-1 3-8 7-12 9-8 7-14 14-3 1-2 4-8 7-4 4-2-1 3-5 5-5h2l1-3 8-7 10-9 8-7 5-5 15-14 15-15 8-7 3-1 1-3h2v-2l10-8z" fill="#B6C1C1"/>
<path transform="translate(394,1164)" d="m0 0 5 1 15 6 21 8h6l12 5 5 3 15 4 16 5 12 4-2 3-7-1h-3l-2 1-11-5-13-5-17-6-12-5-30-12-10-5z" fill="#533A37"/>
<path transform="translate(1118,909)" d="m0 0 11 6 29 14 5 4 4 9 1 3-1 2h-7l-12-4-16-8-8-6-2-3 14 7 3 1v-2l6 2 7 6 5 1-4-8-6-5v-2l-6-2-20-11-3-2z" fill="#6F6B68"/>
<path transform="translate(829,1464)" d="m0 0 1 4-2 4 4-2-2 7h-2l-1 5h-2v3h-2v3h-2l-3 9-3 5h-2l-1 5-2 2-1-7 1-4h-2l-1 3-4 3-1 5h-2l2-7 3-5 5-7 4-7 4-6h2l1-5h2v-2l5-5z" fill="#402C2A"/>
<path transform="translate(382,663)" d="m0 0 4 5 9 17 3 13h1l-3-14-2-9 2 2 3 7 1 13h2l1 3 2 16 6 12h-2v3h2l4 8 8 7 3 3-1 3-9-9v-2l-4-1-5-6-2-6-4-4-3-7-2-14-3-8-1-13h-2l-8-16z" fill="#6F4D44"/>
<path transform="translate(1065,1516)" d="m0 0 10 2v2l5 1v2l6 2 8 7 7 10 2 7-3-3v-2l-3-1v-2h-2v-2h-5-2l-3 3-7-9-6-4-4-4-5-3v-2h3z" fill="#4C3F3E"/>
<path transform="translate(1371,633)" d="m0 0 6 1-3 3-21 8-21 10-11 7h-3l-3-3 1-5 10-8 8-2 10 1 3-3 7-2 9-3z" fill="#B1BBBB"/>
<path transform="translate(373,907)" d="m0 0 8 1 4 6 2 7v9l-5 6-5 10-9 14-7 9-5 5-11 6-10 4-22 1-4 3 2-5 1-1 23-2 12-6 6-6 6-2 2-4 7-8 7-12 3-4 2-6 5-4-1-9-3-7-7-3z" fill="#C49D87"/>
<path transform="translate(312,1125)" d="m0 0 5 1 13 5 4-1 7 4 8 3 12 6 11 4 5 3 16 6 7 3v1h-12l-22-10-21-8-21-9-11-6z" fill="#987567"/>
<path transform="translate(867,1236)" d="m0 0 5 1 2 3v4l-2 1h-11l-15 1-16 3-18 1-14 2h-8v-1l18-4 24-1 9-3 1-2-15 1h-15v-1l34-2z" fill="#382120"/>
<path transform="translate(983,724)" d="m0 0 9 5 7 5 4 4 14 9 7 4 4 1v2l5 1 1 3 5 3v3l-10 6-3-1-4-11-4-4 4 1 3 2 1-2-5-2v-2l-4-1-26-13-6-4-3-8z" fill="#5D3D38"/>
<path transform="translate(1296,679)" d="m0 0h3v7l-12 9-3 4h-2l-1 3-5 2-4 2-1 4-8 6h-6v-5l13-11 8-7 9-7 2-3 5-2z" fill="#1C100F"/>
<path transform="translate(1160,827)" d="m0 0h3l2 10 2 9h2l8 18 1 1v5l4 2 8 14 7 15 7 20 3 9-1 3-6-16v-3h-2l-5-12-7-16v-2h-2l-9-17-8-13-2-6v8l-2-3-2-9-1-1z" fill="#7A4B40"/>
<path transform="translate(1351,1710)" d="m0 0h19l-3 2-54 9-25 4h-8l-47 7-15 2h-10v-1l59-8 46-8z" fill="#7D7D7A"/>
<path transform="translate(1741,917)" d="m0 0 4 1 7 14 7 15 6 16 4 13 3 10 4 10v6l-2-1-7-18-13-34-8-17-5-11z" fill="#6F6C69"/>
<path transform="translate(216,861)" d="m0 0 6 1 5 5 8 4 9 8 10 18 9 14 8 11 11 13 9 10 8 10 12 12h-3l-8-8-4-2-5-8-14-15-6-5-3-6-7-9-10-16-8-13-3-6-9-8-10-5 6 9-1 3-9-12z" fill="#C19B85"/>
<path transform="translate(955,1430)" d="m0 0 4 1 7 9v2h2l2 7 3 1 4 10 7 8 2 5-7-1-5-5-3-1-12-18-1-9-3-6z" fill="#3B2625"/>
<path transform="translate(610,739)" d="m0 0 2 1-10 6-14 6-17 9-21 9-25 9-16 4-5 1h-24l-13-2h-4l1 7h-2l-1-8 2-2h10l15 2h10l15-2 23-7 28-11 22-10 9-5 10-4z" fill="#9B7869"/>
<path transform="translate(180,1007)" d="m0 0 3 1 4 5 7 16 8 16 7 12-1 2-5-6 1 8-4-3-5-10v-2h-2l-1-6h-2l-4-11-5-10z" fill="#311C19"/>
<path transform="translate(1786,1873)" d="m0 0 4 1-13 6-15 6-31 10-3-1-2-1-12 3-25 4h-3v-2l37-8 25-6 21-6z" fill="#9DC6C9"/>
<path transform="translate(291,464)" d="m0 0 5 1 7 3 9 4v2l6 2 24 12 5 3 10 4 16 8 14 9 3 4 5 3-2 1-9-3v-2l-5-2-10-6v-2l-5-1-8-4-3-3-7-3-15-8-16-8-23-12z" fill="#DABCA8"/>
<path transform="translate(233,1078)" d="m0 0 4 2 23 15 8 4 7 4v2l4 2 5 4 18 10 10 6-3 1-9-5-10-4-21-12-23-14-9-6v-2l2-1-6-5z" fill="#5C3C38"/>
<path transform="translate(1334,950)" d="m0 0 4 1-9 3 4 2v3h11l16 2 12 2 14 4 3 2 15-1 5-1h8l-4 2-26 4-7 1-3-1v-2h5v-2l-7-1-11-3-21-2-14-1-9-2-2-1v-3l12-5z" fill="#937265"/>
<path transform="translate(850,673)" d="m0 0v3l1 13-3 9-12 71-4 33-4 50-2 18-1 20h-1v-21l4-51 6-52 11-67 3-10v-7l-1-5z" fill="#776D67"/>
<path transform="translate(557,1598)" d="m0 0h2l-1 3-4 3h-4v2l-4 2-5 8 7-1-2 2h-4v2l-10 3v2l-10 4-13 4h-4v-2l5-3 6-4h2v-2l5-2 4-2v-2l7-5 5-2 8-4z" fill="#504545"/>
<path transform="translate(1213,954)" d="m0 0 7 4v6l-2 4 13-1 5-2 13-2 12 1 7-2 10-4 3 2-6 4-9 4h-20l-15 3h-26v-4l6-3h2v-2l2-1z" fill="#726C68"/>
<path transform="translate(1639,995)" d="m0 0 1 3 3 14v165l-1 27h-1v-185l-2-9-4-9 2-4z" fill="#6F6C69"/>
<path transform="translate(1450,928)" d="m0 0 7 1v1l-6 1-1 3-36 5-23 3h-11v-1l12-3h-14v-1l25-3 19-2 24-3z" fill="#7B584E"/>
<path transform="translate(1242,715)" d="m0 0h3l-2 5-4 2-3 6-14 10-5 3-17 11h-3l1-5 3-1v-2l14-6 11-8-3-1-1-2-5 1-5 2-4-1 15-7 10-4z" fill="#FDF1DE"/>
<path transform="translate(1207,760)" d="m0 0 2 1-5 4-12 6-12 7-19 6-4 4 1 8 1 7 16 3v1h-10l-6-2 6 8 1 4-3 7h-3l-2-12-5-9-1-5 2-2-1-9 5-5 10-4 13-4 9-5 2-3 7-1v-2z" fill="#C59E88"/>
<path transform="translate(1664,401)" d="m0 0h1l3 15 4 17 2 11v8h2l3 31 1 21 3 8 4 2-10 5-2-1 1-5h-2l-1-4h-2l-2-7 1-4 5 12 4 2-2-8-4-44-4-27-4-16-1-7z" fill="#6F6C69"/>
<path transform="translate(981,266)" d="m0 0v3l-11 11v4h-2l-2 4-15 13-3 2 2-4 4-7-12 12-8 7-11 9-10 9-2-1 10-10 7-6 20-20 9-6 11-10h2v-2z" fill="#6F6A66"/>
<path transform="translate(621,1575)" d="m0 0 7 1v2l-4 1v2l-7 4-10 4-10 5-8 2v2l-16 6-7 3h-5v-2l13-7 8-3 2 1v-2l5-3 2 1v-2l4-2h3l1-2 4-2h3v-2l10-4z" fill="#341917"/>
<path transform="translate(873,606)" d="m0 0 3 1-1 4-12 7-16 5-9 4h-3l-1-3h-11l3-2 21-8 16-5z" fill="#7D4639"/>
<path transform="translate(1831,1366)" d="m0 0h2l7 36 11 60 10 60v10l-1 2h-2l-2-9-2-22-5-37-6-35-11-55z" fill="#9EA09D"/>
<path transform="translate(1416,974)" d="m0 0 4 1-6 3 1 4 10 3 7 2 3 3 11 5 9 2 1 1 19 2-1 2-16-1-23-5-23-7-12-6-7-2v-1h7l1 1 10 1 1-5z" fill="#593833"/>
<path transform="translate(66,952)" d="m0 0 1 2 4 2 4 5v2h2v-6l2 4h2l6 11 1 1v7l7 10 9 12v2l-4-2-5-5v-2l-5-2-12-15-2-5h2l-7-11-5-7z" fill="#49322F"/>
<path transform="translate(1011,752)" d="m0 0 5 1 2 1 2 4 2 20 6 28 6 23 6 17-1 3-11-28-6-17-2-4-3-28-1-11-3-6z" fill="#B39D8F"/>
<path transform="translate(1341,567)" d="m0 0h3v2l-3 3 3 2-21 7-9 2-6 1-1-3-7 1-3-1v-4l-4-1 9-3h4v-2h5v2l-9 3 12-1 12-3 11-3z" fill="#4A3B39"/>
<path transform="translate(388,518)" d="m0 0 9 2 5 4v2l5 1 9 2 14 10v2h2l3 5 19 13 8 6 3 5 10 9 9 10 6 11-1 2-9-14-13-14-14-11-4-5-9-5v-2l-5-1v-2l-5-1-5-5-13-9-5-3-9-4-8-6z" fill="#9D9088"/>
<path transform="translate(666,1541)" d="m0 0h5l-4 3-13 6h-3v2l-11 4h-2v2l-5 2-13 6-23 11-18 10-4 3-8 3-7 2-1 3-9 5-7 3-3-1 28-17 8-4 9-3 22-12 26-12 14-8 11-5z" fill="#EECCB3"/>
<path transform="translate(1768,892)" d="m0 0h2l8 21 6 25 7 31 7 27-1 4-9-33-3-12-3-9-3-12-3-9-7-14v-6l-1-7z" fill="#919896"/>
<path transform="translate(844,643)" d="m0 0h16l-1 9-2 6 1 1v5l-3 3-2-1 1-6-2-5 3-5 1-4h-7l-34 9-46 13-2-1 10-4 11-3 7-3 9-3 20-6 12-1v-2z" fill="#A3A39F"/>
<path transform="translate(884,664)" d="m0 0h11l13 4 11 8 15 11-3 1-5-2v-2l-4 1-4-3-1-3-9-3-3-3v-4h-2v2l-7-1h-3l4 9-5-2-8-3-1-2-7-3 1-2 7-1z" fill="#402725"/>
<path transform="translate(1385,640)" d="m0 0h5l-3 2-11 4-8 2-12 5h-3v2l-4 2h-3l-1 3-10 5h-2l-1 4-9 4-11 8-11 9-6 5h-2l-1 3-13 9-5 5-4 2-2 4-6 5-2-1 7-6 5-5 3-1v-2h2l1-3h2v-2l8-6h2v-2l11-9 13-10 12-9 5-4 9-3 9-7 10-4 12-6z" fill="#805549"/>
<path transform="translate(852,668)" d="m0 0v3l-4 6 1 5v7l-4 16-10 61-6 52-4 51h-1v-17l4-48 6-49 9-56 3-10v-15z" fill="#989C99"/>
<path transform="translate(1745,881)" d="m0 0v3l-2 4 2-1-2 5-27 27-7 8-4 5-8 7-15 14-2-1 19-19 1-2h2l2-6 20-20 7-8 13-15z" fill="#462A27"/>
<path transform="translate(326,816)" d="m0 0 7 6 3 3 3 1v2h2l1 3 4 3 4 7 4 4 3 1v2l4 1 2 1v2h2l2 5h2v13l-4 4-3 5-3 2 3-12 4-1-2-3-1-6-7-8-5-5-4-3-3-1-7-12-6-1v-2l-2-1-3-6z" fill="#C29B86"/>
<path transform="translate(492,613)" d="m0 0h1l1 15v42l5-1 4-8 7-9 9-9 10-16 8-13 3 1-1 8-7 14h-3l-2-2-8 11-9 9-5 8-3 6-4 5-3 3-2-3-1-3z" fill="#5D3D38"/>
<path transform="translate(1076,619)" d="m0 0h10l11 2 2 4-15 1-16-1-10-1-19 1-21 4-19 3h-6l3-2 10-2 1-1 24-3 10-2h16z" fill="#947265"/>
<path transform="translate(374,877)" d="m0 0 5 2 12 13 12 11 3 1v2l5 2 7 4v2l18 3 8-3 18-4 2-1 3-5 7-6 5-7v3l-4 8-6 6h-2v2l-10 5-11 3-14 1-14-3-6-5-9-5-17-16-6-5-2-4-8 2-3 5-2 1-1 7-2-3 1-6 3-3h2l1-4z" fill="#C49D87"/>
<path transform="translate(855,1246)" d="m0 0h9l1 4-4-2-15 2-9 2-43 3h-84l-26-2-27-5v-1l11 1 33 4 17 1h70l32-3 17-1 8-2z" fill="#6F6C69"/>
<path transform="translate(1511,512)" d="m0 0 3 3 4 9 1 18v14l-2 11-3 11v8l-1 2 2 1-11 3 3-13 5-10 3-13v-33l-3-1-1-2z" fill="#B59C8D"/>
<path transform="translate(1658,190)" d="m0 0h2l-1 78-1 9h-1l-2-16v-57z" fill="#A4A9A7"/>
<path transform="translate(1852,261)" d="m0 0 3 3v12l-8 28-4 9h-2l1-11 2-7 1-8h-2l1-8 5-12z" fill="#4C322E"/>
<path transform="translate(1051,869)" d="m0 0h2v3l5-1 5 5 2 4h2l1 4h2l6 9v2h-3l-1 3h-3l-2 2-7-10-8-14z" fill="#7F4C3F"/>
<path transform="translate(1088,1537)" d="m0 0 7 2v2h2l4 5 3 4 2 10v7l-2-3-2-5-1 7v5l-3-1-4-12-6-12-2-3 1-4z" fill="#1E1313"/>
<path transform="translate(232,878)" d="m0 0 4 2 4 5 12 20 7 11 2 2-1 4-3 3-3-1-8-16-8-15-4-8-2-3z" fill="#301412"/>
<path transform="translate(942,1401)" d="m0 0 4 4 9 15v2l5 2 5 5 3 11 9 12 11 12 13 14 10 8 7 5v1h-5l-10-9-1-2-5-3-13-13-9-11-2-1-1-3-4-4v-4h-2l-8-11-4-8-10-16z" fill="#ABB4B3"/>
<path transform="translate(774,651)" d="m0 0 3 1h-2v2l-23 7-27 9-15 6-27 12-3-1 32-16 17-6 3-2-1-2 6-3h4l1 2 24-7z" fill="#734338"/>
<path transform="translate(320,482)" d="m0 0h3l7 2 14 8 5 3 5 2 5 4 10 4v2l5 2 10 6 1 2 3 2-7-1-9-3v-2h-2v-2h-2l-1-2-12-4-1-3 1-1-5-3h-5-3v-2h-5l-2-6-5-2-2 1 2 1-1 2-12-6z" fill="#492D2A"/>
<path transform="translate(262,762)" d="m0 0 5 2 5 4 6 3 7 6 9 11 4 2 1-3h6v2l-4 1-2 3-6-1 6 5-1 3-13-13-6-4-8-7-8-10z" fill="#917164"/>
<path transform="translate(1040,768)" d="m0 0h9l9 3v1l-10-1-6-1 3 9 5 16 6 9 7 16 8 13 12 23 10 19v3l-4-4-14-27-9-17-8-13-8-16-6-14-4-12z" fill="#989C99"/>
<path transform="translate(1358,557)" d="m0 0h6l-2 4-10 4-10 2-5 3-18 5-10 1-2 1h-8l3-2 5-2h4v-2l20-6 9-1v-2z" fill="#351917"/>
<path transform="translate(876,1256)" d="m0 0 2 3v3h2l3 11 4 10 4 11 5 13 5 11 8 18 18 36 5 5 2 9h2v5l-4-5-3-6v-2h-2l-6-13v-2h-2l-14-29-10-23-7-16-9-25-3-10z" fill="#D0AC95"/>
<path transform="translate(193,413)" d="m0 0 5 2 28 15 12 6v2l9 3 3 2-1 2-3-2-6-1 1 2-5-2-7-4-7-2-4-4-12-7-9-5-7-4v-2z" fill="#784F44"/>
<path transform="translate(178,976)" d="m0 0h6l4 4 4 2 4 8-3 1-2-1-1 5-4 3-4-2-6-9-2-6 1-4z" fill="#C29C86"/>
<path transform="translate(1540,1628)" d="m0 0h1l4 18 2 6v2h2v-5h2l2 4 2 16v5l-5 1-3-2-3-7-1-10-3-13z" fill="#3D2928"/>
<path transform="translate(560,767)" d="m0 0 3 1-20 9-21 8-11 3-20 3h-23l1 5-3-4-1-6h32l15-2 15-4 26-10z" fill="#DDBEA7"/>
<path transform="translate(763,1497)" d="m0 0h2v2l-4 1v2l-22 14-4 2h-3v2l-19 12-16 9h-3v2l-7 4h-3v2h-6l4-5 16-7h2v-2l3-1 1-2h4l2-4 12-5 3-3 30-18z" fill="#4C4040"/>
<path transform="translate(452,578)" d="m0 0 5 2v2h6l4 4 7 2 3 3v2l4 2 5 6 3 2v2h2l1 8h-2l-4-9-5-4v-2l-2 1 3 9 2 9v46h-1l-1-45-2-9-6-9-9-10-11-9z" fill="#2F1210"/>
<path transform="translate(599,1227)" d="m0 0 14 1 24 4 20 4 25 4v1l-13-1-13-2-23 1-16-4-7-3-11-3z" fill="#492721"/>
<path transform="translate(113,1015)" d="m0 0 5 3 3 4v2l3 1 4 7 3 2-1 7 9 14 1 5-4-4-7-11-4-1-9-14v-2h-2l-4-8 1-2h2z" fill="#331D1C"/>
<path transform="translate(378,935)" d="m0 0 1 3-6 9-7 11-7 8-8 5-5 5-11 5-12 1h-10l3-2 18-3 3-2-8 1h-9v-1l18-3 12-6h2l2-4 6-7v3l5-2 7-12 1-3 4-4z" fill="#957365"/>
<path transform="translate(1067,184)" d="m0 0 1 3-8 9-6 2-2 4-26 26h-2l-1 3-3-1-10 8h-3l16-15h2v-2l8-7 10-10 8-7 3-1 5-5h2l2-4z" fill="#9D9F9C"/>
<path transform="translate(1305,584)" d="m0 0h5l-4 2-5 2-11 2-1 2-7 2-13 1-9 1v2l-13 2-20 4h-4v3h-7l-3 1-3-1v2h-5l-5 1-35 6h-6v-1l48-9h5v-2l42-8 23-5 11-2 9-3z" fill="#848684"/>
<path transform="translate(1310,966)" d="m0 0h12l34 2 6-1 8 2v3h2l1 3h-10l-50-6z" fill="#64433D"/>
<path transform="translate(373,874)" d="m0 0 6 1 9 11 8 8 11 9 6 4 16 7h8l19-5 9-2-1 3-14 4-10 2-6 2-16-4-3-3-9-5v-2l-4-1-17-16-7-8-4-1-5 2-1 4h-2l2-5z" fill="#815346"/>
<path transform="translate(1507,499)" d="m0 0h2l-1 3-3 2h-3v2l-4 2h-3v3l5-2 1-2 9 2 1 3-8-2-3 3h-3l8 8 3 10 2 3v14l-5 16-2 6h-1l1-8 2-14v-13l-4-13-7-9v-2l-4-2 11-6z" fill="#A0A7A5"/>
<path transform="translate(550,750)" d="m0 0h6l2 3-13 3-19 6-6 2-24 4h-17v-1l14-1 13-4-1-4 12 1 10-2 5-2 8-2z" fill="#919896"/>
<path transform="translate(1767,440)" d="m0 0 2 3v3h-2v5l1-1 4-2-2 4-1 3h-2l-3 10-5 10-3 1-2-1 1-8-5 2 2-4 9-16z" fill="#4A322F"/>
<path transform="translate(151,385)" d="m0 0 4 2v2h3v2h3v2l4 1 12 8 11 7 5 3v2h-3v2l6 2 7 5-1 3-5-2-10-6v-3l-15-10-14-10-5-5z" fill="#5E4440"/>
<path transform="translate(1438,1311)" d="m0 0 2 4-2 1-1 5-5 8h-2l-1 4-5 8h-2v3h-2l-2 7-4 5-3-1-1-4 9-13 4-7 9-14 4-5z" fill="#F6F8F9"/>
<path transform="translate(1503,559)" d="m0 0 1 3-3 12-8 10-6 12-4 4-5 1v2l-18 7-7 1 1-5 7-3 12-2 10-4 4-10 6-12 7-8z" fill="#B2BCBC"/>
<path transform="translate(585,741)" d="m0 0h2l-1 6-28 14-10 4-12 4-7 3-6 1-1-2 15-6 3-2 8-2 13-6 3-3 16-8z" fill="#372221"/>
<path transform="translate(1290,1720)" d="m0 0h7v1l-44 7-38 5h-7v2l-8 1h-31l-8-1-1-2h2l-1-4h6l2 5h11l17-1 25-4 29-3z" fill="#4A3838"/>
<path transform="translate(1195,914)" d="m0 0 4 4 7 18 6 7 5 5 11 7 1 2-11-3-9-4-6-7-5-12-2-4z" fill="#301513"/>
<path transform="translate(886,615)" d="m0 0 3 1-3 2 1 4 4 2-25 6-12 1-4-2 4-4 12-4 12-1z" fill="#9EA09D"/>
<path transform="translate(751,1266)" d="m0 0h30l10 1v3l-13 2h-34l-3-1 2-4z" fill="#7D4639"/>
<path transform="translate(745,1606)" d="m0 0 1 2-10 18-8 14-7 9-3 4h-2l1-10 8-15 3-6 5-8 1 2-7 15v4l4-9 4-10h2v4l7-13z" fill="#6F6C69"/>
<path transform="translate(403,544)" d="m0 0 5 2 15 10 11 8 14 11 13 11 8 7 8 9 5 10v6l-6-12-5-5-4-6-13-11-5-3-5-6-6-3-5-5-4-2-1-2-3-1v-2h-3l-1-2-3-1v-2l-4-2-3-1-4-4z" fill="#804D40"/>
<path transform="translate(413,1663)" d="m0 0 5 2 10 7 8 6 1 4 3 2v2l5 2 2 3-5-1-20-11-5-4h2l-7-8z" fill="#CAD6DD"/>
<path transform="translate(308,991)" d="m0 0h1v7l-3 5-8 7-8 8-7 3-3 1h-14l-4-1v-2l-8-1-6-2 4-1 13 3h11l11-6 5-4 6-2v-2l8-6z" fill="#DEBFA8"/>
<path transform="translate(1354,792)" d="m0 0 2 1-7 7-10 8-16 8-7 2h-38l-4 3-5 1h-12l-3-2 4-2 3 1h10l6-3 27-1 16-2 13-5 9-6 11-9z" fill="#957365"/>
<path transform="translate(761,1567)" d="m0 0 3 3h4l2 1-2 4-9 13-5 3-7 5h-1v-5l9-14z" fill="#3C2827"/>
<path transform="translate(1831,1175)" d="m0 0 2 4 4 22 2 9 3 16v6l-3-1-2-16-1-2-2 1v-4h-2l-4-20v-7l2-4z" fill="#63433E"/>
<path transform="translate(884,640)" d="m0 0 3 1-4 1-1 3-11 4-5 5-4 5 24 2 5 1v1h-22l-9 2-6 5-1-3 4-3v-5l-1-3 3-8 1-5h-10v-1l11-1 2 1-1 7-1 3 5-2 10-7z" fill="#937467"/>
<path transform="translate(1714,925)" d="m0 0m-1 1m-1 1m-1 1m-1 1m-1 1 2 1-1 4-16 16-8 7-13 11-20 16-1-3 10-9 8-6 2-3 5-3 14-13 5-5 7-6z" fill="#483938"/>
<path transform="translate(869,662)" d="m0 0h16l12 1 5 2-3 1-15-2v2l-7 2 3 2 4 2-4 1h-9l-4 2v-4l-2-1v-2l-6 4h-5l6-8z" fill="#6A4943"/>
<path transform="translate(1782,420)" d="m0 0h2l-2 14-3 4-2 5-4 5-4 2-1 2-2-1 1-5 1-4 1-6 7-11 5-2z" fill="#3C1F1C"/>
<path transform="translate(1821,1143)" d="m0 0h1l1 9h2l3 25 1 5v8l3 17-1 3-3-8-1-4-2 3-4-38z" fill="#453738"/>
<path transform="translate(96,300)" d="m0 0 1 2 3 1 3 7 1 9 3 9v7h-1l-3-11-1 1 1 12-3-4-1-11h-2l-2 4-2-5-1-16h2z" fill="#6F6B68"/>
<path transform="translate(861,1244)" d="m0 0h12v2h-5l-1 5-2-1-1-3h-9l-13 2-5 1-29 2-20 2h-70l-17-1v-1h84l21-2 6-1 26-2 8-2z" fill="#4B3838"/>
<path transform="translate(1174,1135)" d="m0 0 6 1 2 1v2l9 3 7 3 25 10 21 6 15 5v1h-7l-29-8-9-4-16-6-16-8-8-5z" fill="#544847"/>
<path transform="translate(1967,604)" d="m0 0 2 1v2l-1 1 3 1-7 8h-2l-2 4-12 14-4 6-3 2 1-9 4-5 3-5 5-6 3-3v-2l8-7z" fill="#3F2623"/>
<path transform="translate(292,999)" d="m0 0 2 1-7 8h5l-5 5-11 6h-11l-20-5 4-2 12 3h8l-16-4-7-3v-2l5 1 16 5 9 1 8-6z" fill="#814F41"/>
<path transform="translate(96,319)" d="m0 0 1 3h2l3 13-1-15 3 4 5 17 3 3 2 7h-2l-1 2-5-3-3-5-2 3-5-18z" fill="#493C3C"/>
<path transform="translate(820,1446)" d="m0 0 3 1-2 2-2 1 2 4-5 5-1 3-7 3-6 6-2-1 3-4-5 4 1 3h-6l-4 2v2l-5 3-3 2 2-4 8-8h2l2-4 11-7z" fill="#5E3F39"/>
<path transform="translate(737,1241)" d="m0 0h75v1l-45 2h-59l-14-1v-1z" fill="#A28273"/>
<path transform="translate(1535,592)" d="m0 0 4 1-12 5-7 3-8 2-15 4h-2v2l-16 6-11 3-13 5h-6l3-2 10-5 9-3 2-1 10-1 7-3-2-2 21-5 5-1v-2l12-4z" fill="#C59E88"/>
<path transform="translate(1461,511)" d="m0 0 3 1-16 8-20 9-13 6-15 6-8 4h-3v2l-9 1-14 5h-5v-2l13-5 20-6 19-7 45-20z" fill="#EEE5DD"/>
<path transform="translate(230,1083)" d="m0 0 7 1v2l-5-1 4 11 11 17 2 4v15l-1 3-4-2-2-5-4-5 1-3h5l-1-4-2-2-4-11-4-6-4-11z" fill="#603D38"/>
<path transform="translate(367,908)" d="m0 0 5 1 10 8 2 9-2 3h-2l-2 4-2 2-6-14-3-10z" fill="#301311"/>
<path transform="translate(1122,1637)" d="m0 0 2 3 2 7 1 21 3 9 5 17v3h-2l-1-4h-2l-8-22-1-7 2 2-1-8-1-10h2z" fill="#493C3C"/>
<path transform="translate(559,754)" d="m0 0 3 1-16 8-8 2-12 5-3 2 1 2-16 3h-6l-2-4 6-2 15-3 8-2v-2l23-7z" fill="#443738"/>
<path transform="translate(1416 1e3)" d="m0 0 11 3 8 5 7 3 21 10 3 3-7-1v2l-4-1-3-2v-2h-5-3l-11-7-10-7-7-5z" fill="#7B4A3E"/>
<path transform="translate(1207,1145)" d="m0 0 6 1 26 8 16 5 35 13 5 2v1h-7l-12-5-8-3-32-10-9-3-19-7z" fill="#5D5251"/>
<path transform="translate(1153,1114)" d="m0 0 12 7 13 8 1 3 14 8-2 3-9-4v-2l-9-1-9-7-10-10z" fill="#B6C0C0"/>
<path transform="translate(1250,818)" d="m0 0 4 1-4 5-6 8-2 1-2 4-3 1-2 5-6 12-6 5 1-7 4-10 4-7 5-3 2-3 3-1 2-9z" fill="#341E1D"/>
<path transform="translate(1536,1603)" d="m0 0h1l2 9 2 1 2 10v7h2v8l1 5 2-3h2v3h2l3 17v9h-1l-2-16-1-4h-2v5h-2l-4-13-2-8-2 1-3-20z" fill="#46393A"/>
<path transform="translate(1885,1556)" d="m0 0 3 2 4 16 4 29 1 11 1 9-3 1-3-22-7-39z" fill="#261211"/>
<path transform="translate(120,371)" d="m0 0 4 2 14 9 3 2v2l5 1 7 5 5 2 17 12 12 8 2 3-5-1-17-11-19-12-17-12-11-8z" fill="#3D1F1B"/>
<path transform="translate(1018,755)" d="m0 0 4 4 3 21 5 25 1 6h2l-1-4 1-2 4 2v6l-3 2-2-1 3 8 1 10-3-3-8-31-4-20-2-20z" fill="#947365"/>
<path transform="translate(931,589)" d="m0 0 8 2-1 3v-2h-15l-36 9-25 7-24 8-12 5-3-1 19-8 36-12 32-8z" fill="#957365"/>
<path transform="translate(1164,847)" d="m0 0 2 1 4 9 6 10 9 17 3 10 3 7-1 3-1-4h-2l-8-17-6-10-8-17z" fill="#321816"/>
<path transform="translate(1279,965)" d="m0 0 29 2 5 1v1l-36-1-9 4-7 1-24 1-24 3h-26l-19-4v-1h12l4 1v2h26l24-3 7-1 24-1z" fill="#B0BAB9"/>
<path transform="translate(712,665)" d="m0 0v3l-5 2-3 3-16 8-11 7-3 3-8 4-7 2 2-3h2l2-4 2-3 9-4 18-10z" fill="#929592"/>
<path transform="translate(1821,1085)" d="m0 0h2l2 18 1 20-1 12 1 16v12h-1l-3-33-3-20v-8l2-1-1-14z" fill="#5D3D38"/>
<path transform="translate(1454,923)" d="m0 0 2 1-9 4-36 5-21 2-27 4-38 8h-5l3-2 33-7 30-5 44-5 20-4z" fill="#957365"/>
<path transform="translate(878,631)" d="m0 0h23v2h-2v2l-3 2-17 3h-6l-7-4 3-2h4v-2z" fill="#433738"/>
<path transform="translate(344,824)" d="m0 0 9 6 9 9 7 8 3 3-1 2-10-9-2-1v5l5 1 3 4-1 3-1-3h-2v-2l-6-2v-2h-2l-5-6-3-6-5-5 2-1 2 1z" fill="#3E2523"/>
<path transform="translate(1813 1e3)" d="m0 0 2 4 6 29 5 37 3 41v14h-1l-5-58-7-47-3-14z" fill="#CAA791"/>
<path transform="translate(1107,903)" d="m0 0h4l4 4v2h3v2l5 2 7 4 4 9-3 1-12-8v-2l-5-2-4-2-4-1-3-5 3 1v2h2z" fill="#453738"/>
<path transform="translate(1486,949)" d="m0 0h3v2l6-1-2 4-15 8-3-1 5-3-1-3-12 5-8 2-10 1-5-1v-1l21-5z" fill="#814E40"/>
<path transform="translate(1472,725)" d="m0 0h16v3l-1 1-14 2-8 3-6 3-8 2h-7l3-3 16-8z" fill="#8D5C4D"/>
<path transform="translate(456,897)" d="m0 0v3l-3 1 1 5-1 2h5l-2 2-19 5h-8v-2h4l-3-3v-2l-3-3 4-1 4 2h9z" fill="#331B1A"/>
<path transform="translate(853,1175)" d="m0 0 2 4 4 12 2 5 9 36v2l-5-1-10-41-2-10z" fill="#976A5B"/>
<path transform="translate(196,1132)" d="m0 0 5 5 5 7-1 2-4 1 2 5 7 6v2l3 1-2 1-6-3-12-11-5-4 1-4 1 2 6 3-3-6 2-5z" fill="#624844"/>
<path transform="translate(1178,865)" d="m0 0 5 5 5 8 10 19 5 16 5 12v2h2l3 10 4 6 3 4-4-2-5-4-6-14-9-26-7-15-8-14-3-2z" fill="#C59E88"/>
<path transform="translate(527,634)" d="m0 0 2 1 1 5-7 12-3 7-7 9-1-3h2l1-5 4-7h-2v2h-2l-2 5h-2v-3l-2-2 11-11z" fill="#473B3C"/>
<path transform="translate(1536,1670)" d="m0 0h7l-4 2-3 1-33 3-59 7-1 1h-14v-1l73-10z" fill="#A1A8A6"/>
<path transform="translate(1292,953)" d="m0 0h17l-2 1-1 3-7 2v2l-8 3h-6l-4-4 1-5z" fill="#301210"/>
<path transform="translate(784,777)" d="m0 0 3 1 3 8 5 19 3 13-2 1-4-9-1-5h-2l-2-5-5-14v-8z" fill="#B4BEBD"/>
<path transform="translate(1198,591)" d="m0 0m-5 1h16v1l-57 10-44 7h-10v-1l39-6 49-9z" fill="#C1AB9B"/>
<path transform="translate(302,1565)" d="m0 0 5 4 6 8 9 11 5 6 11 9 13 11h-3l-9-6-1 2-11-10-8-7-2-6-6-8-8-11z" fill="#CAD6DD"/>
<path transform="translate(1044,807)" d="m0 0 3 3 8 15v6l2 5h-2l1 10h-2l-6-16-4-13z" fill="#FCF4E6"/>
<path transform="translate(488,1200)" d="m0 0 9 2 4-1 29 9-4 1h-4v2l10 2-4 1-21-6-8-3-10-4z" fill="#362221"/>
<path transform="translate(903,1341)" d="m0 0 4 4 2 6h4l4 12h4l6 13v2h2l3 6-1 2-4-4-2-3v-4l-3-1 1 4-3-1-5-8-8-18-4-7z" fill="#483737"/>
<path transform="translate(762,668)" d="m0 0 4 1-6 3-2 2-2 7-6 8-2 2-3-8-3-1-8 1 3-3 6-3h2l1-3 14-5z" fill="#F6E6D2"/>
<path transform="translate(768,451)" d="m0 0 2 3h-2l-1 3h-2l-1 4-13 11-9 7-7 3-5 4-2-1 12-11 8-7 11-9 7-6z" fill="#594C4A"/>
<path transform="translate(1161,1841)" d="m0 0 7 1 24 7 42 12-4 1-8-1-4 1-43-15-14-5z" fill="#CBD7DE"/>
<path transform="translate(1766,869)" d="m0 0 2 1-6 8-4 5h-2l-2 5-4 4-6 7-9 11h-3l1-4 7-8 9-10 4-6v-4l8-7z" fill="#3E2B2A"/>
<path transform="translate(836,1142)" d="m0 0h1l5 23 4 9 10 41v7l-2-4-5-13-3-13-5-22-5-21z" fill="#989E9C"/>
<path transform="translate(225,1101)" d="m0 0 3 4 1 4 3 1 5 9 3 8 4 13v13l-1 2h-2l-1 3-4 2h-7l-5-4h15l1-6-1-16-9-21-2-5h-2z" fill="#9F7A6A"/>
<path transform="translate(368,920)" d="m0 0 2 3 2 6v11l-5 5-7 11-8 10-14 7-10 2h-9l-1-2h6l15-4 12-6 9-11 4-10 4-6z" fill="#CDA992"/>
<path transform="translate(1896,1784)" d="m0 0h1v25l3 1h-3v3h2v-2h2l1 5 3-4v12l-5 2 1 5-4 1-2-4v-27z" fill="#493E3F"/>
<path transform="translate(824,1457)" d="m0 0 2 1-3 9-4 2-2 5-7 13-3-1v-5l-4-2 3-5 5-3 9-10z" fill="#F5F8F9"/>
<path transform="translate(1114,923)" d="m0 0 7 6 9 7 7 5 5 6 5 2 2 4-10-1-12-6 3-2-11-13-5-6z" fill="#F7F9FA"/>
<path transform="translate(1193,917)" d="m0 0 2 4 1 9 4 8 2 7h-2l-6-12-5 2-8 6-7 1-1-4 9-7 10-5z" fill="#8F7265"/>
<path transform="translate(1245,832)" d="m0 0h2l-2 5-5 9-10 17-8 11-4-1-2-3 2-10 4-5-1 5-2 6 6-3 4-5 1-4h2l2-5 6-10z" fill="#D3B29B"/>
<path transform="translate(1322,796)" d="m0 0 5 1-5 4-5 2v2l-10 3-7 3-11 2-19 2h-5l1-2 8-2 18-2 9-3h4v-2l10-4z" fill="#C39D87"/>
<path transform="translate(368,629)" d="m0 0h3l3 9 3 1 8 14 2 2v5l-9-9 3 9h-2l-6-10-4-11z" fill="#583B37"/>
<path transform="translate(1121,942)" d="m0 0 6 3 5 5 11 7 8 6-1 2-11-3-18-9 3-1-3-5 3-1-3-2z" fill="#94766A"/>
<path transform="translate(221,866)" d="m0 0 5 2 8 4 8 8 5 10 13 21 2 5-5-5-12-20-8-13-6-3 2 10 3 6-1 4-9-20-5-7z" fill="#957365"/>
<path transform="translate(751,1497)" d="m0 0 2 1-3 1-2 4-1 1 3-1 2 2-14 8-13 8-6 2v-2l3-2h3v-2h2v-2l-3-2 24-14z" fill="#7F7771"/>
<path transform="translate(200,998)" d="m0 0h11l11 3 4 2v2l5 1 8 4 6 2v2l3 1-8-1-7-3-9-3-4-4-6-2h-28l1 6-2-1v-7l1-1z" fill="#C19A85"/>
<path transform="translate(89,1006)" d="m0 0 5 5 7 10 7 12 8 13 3 11-2 1-10-18-18-32z" fill="#9CA5A3"/>
<path transform="translate(110,333)" d="m0 0 3 1 10 13 1 5h-2l1 7 2 1-4-1-8-10-1-5-3-1-1-2v-7z" fill="#B0BCBC"/>
<path transform="translate(877,1286)" d="m0 0 3 4 9 20 7 15 2 9 1 7-2-2-7-15-10-23-2-5z" fill="#4C4242"/>
<path transform="translate(1181,867)" d="m0 0 6 5 6 9 4 8 4 4 3 6v11l5 12v5l-2-2-6-15-5-15-10-19-4-6z" fill="#DEBFA8"/>
<path transform="translate(771,445)" d="m0 0m-1 1m-1 1m-1 1m-1 1m-1 1m-2 1h2l-1 3-8 7-11 9-11 10-5 5 8-6 2 1-14 11-11 5-3-1 22-18 15-13 11-9z" fill="#6F6C69"/>
<path transform="translate(1255,1715)" d="m0 0h6l-2 2-8 2-16 2-1 1-21 3-30 3h-22l-5-2 1-2 5 2h13l29-3 45-7z" fill="#8C8B89"/>
<path transform="translate(1191,937)" d="m0 0 4 2 3 7-1 5-4 2-11-2-2-4 7-8z" fill="#F7F9FA"/>
<path transform="translate(511,668)" d="m0 0v3l-14 14-2 4-1 7v10l3 3v9l-6 11-4 10-4 9-1-3 4-12h2v-5l2-4h2v-36l2-5 5-3 7-8z" fill="#6D6864"/>
<path transform="translate(1531,1523)" d="m0 0h6l1 3-12 5-12 4-2 1-2-1-1 2-5-5 2-2z" fill="#989F9D"/>
<path transform="translate(1494,945)" d="m0 0h5l-1 4-3 3-4-1h-2v-2l-27 9-24 5h-5l1-3 22-4 16-5 12-3z" fill="#DBBBA4"/>
<path transform="translate(1448,715)" d="m0 0h5l7 3-1 3-12 2-5 2-1 4-5 2-6 2v2l-7 1 12-9 1-5-3-1 14-4z" fill="#865749"/>
<path transform="translate(200,426)" d="m0 0 6 2 11 7 11 6 19 11 8 5v2l-8-2-9-5-11-6-7-5v-2l-5-2-7-5-8-4z" fill="#F9E7D2"/>
<path transform="translate(473,737)" d="m0 0 1 4-5 13-1 5 5-2-4 16-3 3-4 1-1-6 1-8 3-6 4-12z" fill="#2A1110"/>
<path transform="translate(239,445)" d="m0 0 11 6 26 13 7 3 2 4 3 3-6-1-17-10-10-5-17-10z" fill="#3D1F1C"/>
<path transform="translate(1092,877)" d="m0 0 5 3 12 18 9 8 23 13 5 2v2l2 1-5-1-21-11-7-3v-2l-4-2-7-8-7-10-5-8z" fill="#939794"/>
<path transform="translate(1647,387)" d="m0 0h6v2l-6 3h9l2 3v11h-1l-2-9-1-1h-8l-11 3h-3v-2l5-1h-4l-10 1 4-3z" fill="#A08578"/>
<path transform="translate(1140,1691)" d="m0 0 2 3 9 21 4 10-4-1-6-2-2-1v-2h2l-6-15v-10z" fill="#845043"/>
<path transform="translate(185,1117)" d="m0 0 3 3 6 8 2 6-2 5 3 7-8-4-4-6h2l-4-8 2-5z" fill="#36201E"/>
<path transform="translate(1803,1008)" d="m0 0 2 3 4 15 5 24 2 20v8h-1l-4-25-1-5-1 7h-1l-2-21-3-18z" fill="#5D3E39"/>
<path transform="translate(866,677)" d="m0 0h2l-2 5-2 6-3 21-4 24-5 23h-1l1-10 3-14 3-35 3-13 4-6z" fill="#BAA89C"/>
<path transform="translate(1203,583)" d="m0 0m-4 1h4v2l-28 6-5 2-47 9-23 4h-7v-1l34-6 50-11z" fill="#B3BEBE"/>
<path transform="translate(388,519)" d="m0 0 5 2 5 4 12 5 10 8 2 2-3 2-3-1-1-2-4 1-4-2v-2l-4-1-2-6-4 2-5-3v-2h-2v-4l-2-1z" fill="#3F2523"/>
<path transform="translate(1136,1584)" d="m0 0h8v1h-6v2l2 1-4 1-8 3-7 1 10 1v1h-17v6h-1l-1-13 6-2z" fill="#544848"/>
<path transform="translate(858,1403)" d="m0 0v3l-3 1-2 4-9 11-12 16-7 8-6 2-13 12h-2l2-4 11-10 7-5 4-4h2l2-5 7-7 6-8 2-5 5-4h2v-2z" fill="#897C75"/>
<path transform="translate(605,738)" d="m0 0 2 1-5 3-30 15-27 11-17 6-4-1v-1l10-3 10-4 12-4 17-8 7-4 9-4 7-3z" fill="#513A38"/>
<path transform="translate(983,724)" d="m0 0 9 5 7 5 4 4 14 9 4 4-4-1-26-13-6-4-3-8z" fill="#60403A"/>
<path transform="translate(965,274)" d="m0 0 2 1-11 11-4 5-6 4-18 18-3 1-2 4-8 7-4 4-2-1 3-5 5-5h2l1-3 8-7 10-9 8-7 5-5z" fill="#DAE2E6"/>
<path transform="translate(1448,968)" d="m0 0h7v1l-10 2-1 1-14 2-9 3-1 3h-2v2l17 1 3 2-1 1 13 3 9 2v1l-11-1-13-3-1-1-14-2-6-3-1-4 4-3 25-6z" fill="#B18C79"/>
<path transform="translate(1013,741)" d="m0 0 15 5 11 6 12 4 31 7 22 4v1h-8l-19-3-23-5-13-4-15-8-9-3-4-2z" fill="#CDA993"/>
<path transform="translate(2025,555)" d="m0 0 1 2-11 18-10 9-10 3-4 2-7 8-6 6-2-1 9-9 1-2h2l2-4 8-6 5-4h5v-2l7-5 7-11z" fill="#F5E5D2"/>
<path transform="translate(1089,888)" d="m0 0h2l2 2h3l7 8 5 5v7h-2l-1-1 4 6-4-2-9-11-6-9z" fill="#684B45"/>
<path transform="translate(0,848)" d="m0 0 6 5 7 10-1 4-3-2-1 3h-2l2 5-8-3z" fill="#1E0F0E"/>
<path transform="translate(1385,632)" d="m0 0h8l-5 4-9 1-2 5-17 7-5 2v-2l2-1v-3l-4-1 18-7 10-3z" fill="#3E2A29"/>
<path transform="translate(1657,364)" d="m0 0 2 2 3 16 1 11v18l-2-4-5-22v-19z" fill="#5E3D38"/>
<path transform="translate(1451,1693)" d="m0 0m-6 1 10 1v1l-50 7-36 6-13 1v-1l51-9z" fill="#786D67"/>
<path transform="translate(668,705)" d="m0 0 3 1-17 9h-2v2l-7 3-11 7-10 5-14 8-11 6-4-1 5-3 6-3 1-2 9-4 12-7 14-7 6-4 16-8z" fill="#804F43"/>
<path transform="translate(840,1435)" d="m0 0h3l-1 5-5 9-5 5-6 10-3 8-2 1-1 4-3 3-5 7-1-3 6-12 6-7 2-5h2l1-5 4-6 2-5v-3l4-2z" fill="#A0A7A5"/>
<path transform="translate(1253,819)" d="m0 0 2 1-4 5-4 7h-2l-2 5-4 5-7 12h-2l-1 5-4 5-6 2v-5l2-3 3-9 3-2-3 9v3l5-6 8-15 4-3 1-4 6-5 4-6z" fill="#7D4F43"/>
<path transform="translate(1036,790)" d="m0 0 3 3 14 25 4 8-1 2-11-20v9l9 27 5 11-1 3-7-15-8-24-3-14-4-10z" fill="#BFA694"/>
<path transform="translate(390,682)" d="m0 0h2l1 2 1 11 4 13 1 9 4 9 4 4 3 7 3 3 3 1 7 8 7 7 3 5v2l-3-1-5-8-3-2v-2h-2v-2l-4-2-11-11-9-19-2-15-2-5z" fill="#C59E88"/>
<path transform="translate(1114,1603)" d="m0 0h1l3 16 4 14-1 4-1-1-2 3-3-8-5-22v-5l3 3z" fill="#514545"/>
<path transform="translate(520,777)" d="m0 0m-4 1h4v2l-5 2-11 2h-24l-13-2h-4l1 7h-2l-1-8 2-2h10l15 2h10l15-2z" fill="#937264"/>
<path transform="translate(1480,600)" d="m0 0 2 1-4 6 1 2-13 3-6 2h-6v3l-7 2-6-2 2-2 9-3 24-9h2v-2z" fill="#5E3D38"/>
<path transform="translate(404,712)" d="m0 0 3 4 4 9 9 7 8 10 6 5 4 6 1 6-3-3-4-5v-2l-4-2-15-14-4-5v-2l-5-10z" fill="#835F53"/>
<path transform="translate(831,941)" d="m0 0h1l1 43 2 38v15l-2-4-2-16z" fill="#896659"/>
<path transform="translate(865,631)" d="m0 0m-8 1h8v2l-2 1-12 1-9 2-32 6h-7v-1l10-2 5-2 11-3 19-3z" fill="#746D68"/>
<path transform="translate(1517,521)" d="m0 0 2 2 2 18 1 4-2 23-2 3v5l1 5-1 4 1 2-6 1v-10l4-14 1-8v-14z" fill="#DDBFA8"/>
<path transform="translate(202,1052)" d="m0 0 5 5 5 7 7 5 5 3v3h-5l-2 4-7-8-7-12z" fill="#170B0B"/>
<path transform="translate(1605,420)" d="m0 0v3l-7 8-3 2-4 7-12 13-10 10-2-1 1-2-2-1 13-12 5-6 5-5 11-10z" fill="#D0AF99"/>
<path transform="translate(836,392)" d="m0 0 2 1-3 4 7-5-2 4-3 3-7 3-14 12-8 7-9 7-2-1 10-11 7-5h2l2-4 8-7 4-1 1-3z" fill="#5E4946"/>
<path transform="translate(246,1106)" d="m0 0 8 6 2 2 4 12 4 3-3 10-4 12-4 4 3-10 1-5-1-8-1-11-4-7-5-6z" fill="#919896"/>
<path transform="translate(178,993)" d="m0 0 2 1 4 8v5l3 1 4 10 1 6h2l7 16-1 2-10-19-4-10v-2l-3-1-2-2v7l-2-1-4-10-1-4h5z" fill="#492823"/>
<path transform="translate(1126,933)" d="m0 0 5 2 10 6 9 7 9 6v3l-5 1-8-2-7-3 4-1h5l-1-3-5-1-6-7-10-7z" fill="#DEBFA8"/>
<path transform="translate(463,889)" d="m0 0 1 2-4 8 7-1 4 1 4-3-2 4-10 8-11 1-1-2 2-2v-4l3-2 3-5z" fill="#341513"/>
<path transform="translate(1038,766)" d="m0 0 7 1v1h-5l2 10 7 19 8 16 9 16 6 10-1 2-3-3-5-10-6-9-8-16-7-16-4-12z" fill="#907265"/>
<path transform="translate(820,621)" d="m0 0 4 1-1 2-17 6-41 16h-2v-2l28-12 16-6z" fill="#7A6E67"/>
<path transform="translate(1263,590)" d="m0 0m-4 1h4v4l-39 8h-10l3-2 5-2 17-3 7-2 6-1z" fill="#463737"/>
<path transform="translate(822,411)" d="m0 0m-1 1m-2 1 2 1-2 1zm-2 2h2l-1 4-13 11-11 8-17 13-3-1 10-9 12-9 13-10z" fill="#554847"/>
<path transform="translate(1117,785)" d="m0 0h10l16 2 3 3 11 23 1 2v9l-3-1-1-8-9-17-5-8-6-2-17-2z" fill="#B3BEBE"/>
<path transform="translate(1678,443)" d="m0 0 2 3 1 8 2 38 2 15 2 3 4 2-5 1-3-2-2-6-1-9-2-44z" fill="#F2D4BC"/>
<path transform="translate(1630 1e3)" d="m0 0 3 1 1 30v33h-1l-2-10-1-50-3-3z" fill="#A1A8A6"/>
<path transform="translate(1469,960)" d="m0 0h5l-2 1v2l-11 3-5 2-18 3h-4v-2h3l-1-3 5-2 20-2z" fill="#402724"/>
<path transform="translate(1196,812)" d="m0 0h8l29 4 1 2-7 3-5 1-7-3-4-2-12-1-3-1z" fill="#957365"/>
<path transform="translate(1159,805)" d="m0 0 16 2 5 2v2l-6 2-6 9-2 4h-2l1-11-4-6z" fill="#86574A"/>
<path transform="translate(1343,797)" d="m0 0 2 1-7 6-5 3-13 5-6 1-17 2h-5l2-1v-2h6v-2l7-3 10-2v-2l5-3 2 1-8 6-9 4 12-1 10-5 9-4z" fill="#583C38"/>
<path transform="translate(1197,752)" d="m0 0 3 1-10 6-7 3 2 2 5-1h6l-3 2-16 6-8-1 1-3 5-4 5-3 10-4z" fill="#5F3E38"/>
<path transform="translate(260,758)" d="m0 0 6 3 8 7-2 1-8-6-2-1 6 9 8 9 11 8 13 13 1 9-2-3-3-7-8-8-13-9-9-10-6-8z" fill="#C39C86"/>
<path transform="translate(1666,428)" d="m0 0 2 3v2h2l4 27v10h-1l-2-12h-1l-1 14h-1l-1-9z" fill="#5D3D38"/>
<path transform="translate(255,1096)" d="m0 0 5 2 6 3v2l6 2 7 4v2l7 1 16 9 10 6-3 1-9-5-10-4-21-12-13-8z" fill="#523936"/>
<path transform="translate(1189,768)" d="m0 0 2 1-10 6-13 4-10 4-4 4 1 10-3 1-5-8v-2h-2l1-2 5 3 1-4 5-6 10-4 16-4z" fill="#957365"/>
<path transform="translate(465,750)" d="m0 0 1 2-4 10-3 16-4 1-12-12-4-6 1-2 8 7 7 6 2-3 3-10z" fill="#C29B85"/>
<path transform="translate(596,37)" d="m0 0h8v1l-53 10-32 7h-2l1-3 29-6 44-8z" fill="#A0C7CB"/>
<path transform="translate(1850,1363)" d="m0 0h3l5 36 1 4v7l-4-4-4-25-1-7z" fill="#2C1A19"/>
<path transform="translate(1321,671)" d="m0 0 1 3-9 6-13 11-5 4h-2l-1 3-13 9-5 5-4 2-2 4-6 5-2-1 7-6 5-5 3-1v-2h2l1-3h2v-2l8-6h2v-2l11-9 13-10z" fill="#7F5448"/>
<path transform="translate(1277,1874)" d="m0 0 8 1 34 8 32 6 14 2-4 2-9-1-49-10-26-6z" fill="#A5C9CD"/>
<path transform="translate(302,983)" d="m0 0 2 2-1 8 3-1-1 5-10 9-5 3-4-1 7-8 4-7z" fill="#7D5044"/>
<path transform="translate(1279,950)" d="m0 0h12l-1 2-9 1-6 3-11 2-14 1h-10l-12-6 2-1 9 3h22l10-2z" fill="#C59E88"/>
<path transform="translate(1675,452)" d="m0 0h1l3 31 1 21 3 8 4 2-10 5-2-1 1-5h-2l-1-4h-2l-2-7 1-4 5 12 4 2-1-4-2-36-1-10z" fill="#997A6C"/>
<path transform="translate(491,691)" d="m0 0h1l1 17v12l-1 4h-2l-1 3-1-4-6 3 3-10 2-5v-13h1l1 6h1z" fill="#351C1B"/>
<path transform="translate(1505,522)" d="m0 0 4 5 3 4v23l-3 4-5 14-7 10-5 4 2-5 6-7 6-15 3-11v-14l-4-8z" fill="#6F6C69"/>
<path transform="translate(1553,469)" d="m0 0 2 1-1 3-8 5-5 5-7 4-16 9-9 3 3-3 15-9 15-10z" fill="#A79A90"/>
<path transform="translate(855,1246)" d="m0 0h9l1 4-4-2-15 2-9 2-43 3h-7l1-2 32-3 17-1 8-2z" fill="#766D68"/>
<path transform="translate(366,901)" d="m0 0 2 1v2l4 2 3 3 6 2 3 4 2 7v6l-6 5-5 8h-2v-14l4 6 6-7-2-9-9-7-6-5z" fill="#7D4F44"/>
<path transform="translate(1902,706)" d="m0 0 1 4-4 12-5 9-7 10-4 1 1-5 4-4h2v-5l3-5 3-7z" fill="#F9E8D3"/>
<path transform="translate(685,1241)" d="m0 0h7l2 1 14 1h76l-2 2h-79l-9 1h-2v-3l-5 1v-2z" fill="#412522"/>
<path transform="translate(1408,634)" d="m0 0 4 1-13 5-13 4-16 6-13 6-10 4-2-1 1-2 7-2v-2l17-7 8-2 15-5 13-4z" fill="#BD9782"/>
<path transform="translate(192,972)" d="m0 0 9 6 11 8 13 8 14 8 5 2v1h-6l-8-4-4-1-4-4-12-7-7-6-2-1v-2l-5-1-4-5z" fill="#825346"/>
<path transform="translate(387,657)" d="m0 0h2l7 13 5 2 2 9-2 16h-1l-2-13-8-19-3-5z" fill="#C19B85"/>
<path transform="translate(828,623)" d="m0 0h6l1 5-19 5-3 1h-9l4-3 5-1v-2l10-4z" fill="#613E38"/>
<path transform="translate(433,547)" d="m0 0 5 1 16 11 8 6 3 5 10 9 9 10 6 11-1 2-9-14-13-14-14-11-4-5-9-5v-2l-5-1v-2z" fill="#8B8B88"/>
<path transform="translate(1658,268)" d="m0 0h1l5 65 3 22v5h-2l-2-9-3-36-2-27z" fill="#C7A48F"/>
<path transform="translate(1135,1714)" d="m0 0 2 2 4 8 3 3 7 3 6 5 22 1v1h-31l-6-5-6-10z" fill="#8E9492"/>
<path transform="translate(320,482)" d="m0 0h3l7 2 14 8 9 6h-3-5-3v-2h-5l-2-6-5-2-2 1 2 1-1 2-12-6z" fill="#3C2422"/>
<path transform="translate(1578,435)" d="m0 0v3l-3 3-3 5-3 3-2 3-3 2-3 5-3 1v2l-5 1-4 3-4-1 4-2v-2l11-9 12-11z" fill="#4A3836"/>
<path transform="translate(1630 1e3)" d="m0 0 4 2 2 8v64h-1l-1-29-1-12-1-30-4-1z" fill="#6F6C69"/>
<path transform="translate(557,1598)" d="m0 0h2l-1 3-4 3h-4v2l-4 2-4 6-6 2-12 5-2-1 3-3h2v-2l7-5 5-2 8-4z" fill="#5D3D38"/>
<path transform="translate(754,458)" d="m0 0 2 1-11 10-11 9-12 10-9 7 6-1-3 3-11 6h-2l2-4 6-6h2l1-3 14-10 14-12 11-9z" fill="#909694"/>
<path transform="translate(1176,1130)" d="m0 0 5 1 16 8 11 5v2l7 3-1 3-10-3-6-3-6-2v-4l-16-9z" fill="#A2A7A5"/>
<path transform="translate(1463,918)" d="m0 0 3 1-5 3-19 5-21 3-18 2h-10l1-2 43-5 11-1v-2l14-3z" fill="#C59E88"/>
<path transform="translate(140,918)" d="m0 0 5 5 4 6 5 8-1 4-4-7v-2h-3l5 10 1 6-3-3-2-6h-2l-6-15v-5z" fill="#442420"/>
<path transform="translate(374,854)" d="m0 0 4 2 22 22 5 4 4 5 9 7 5 5 4 3v2l-5-2-10-9-5-4-7-8-17-16-9-10z" fill="#825549"/>
<path transform="translate(578,536)" d="m0 0 1 3-11 28-6 15-6 14-6 13-2 4-1-3 13-30 12-31 5-12z" fill="#919896"/>
<path transform="translate(723,1630)" d="m0 0v3l-5 10-2 10 9-9-2 5-7 11-4 5-4 2 1-6 4-10 2-9 5-7z" fill="#919896"/>
<path transform="translate(825,1435)" d="m0 0 2 1-9 9-6 5-2 4-5 4-3 5-7 4-2 3-2-1 2-4 7-6 4-6 8-7 5-6 5-2v-2z" fill="#B9C2C2"/>
<path transform="translate(962,1417)" d="m0 0 7 6 5 6 8 6 12 11 5 5h-3l-11-7-4-3v-2l-4-2-11-13-4-5z" fill="#FFF2DE"/>
<path transform="translate(1459,1293)" d="m0 0 1 2-10 17-8 13-4 1-3 3v-3l8-12 7-10 5-8z" fill="#4F403F"/>
<path transform="translate(1227,729)" d="m0 0 2 4-7 5-5 3-17 11h-3l1-5 3-1v-2l14-6z" fill="#F1DCC7"/>
<path transform="translate(1388,937)" d="m0 0h9v1l-17 4-19 3-5 2-4-1 4-1v-2l-3-1 24-4z" fill="#3C2422"/>
<path transform="translate(1365,764)" d="m0 0 3 1-5 5-5 2-10 8-7 7-10 8h-2v2l-5-1 2-4 4-1h2l3-5 4-2h3l2-4 5-5 14-10z" fill="#C09984"/>
<path transform="translate(718,701)" d="m0 0 6 3v2l5 2 3 6 2 14-3-1-6-8-5-6-3-3 4 1 4 3h2l-1-4-6-4z" fill="#C59E88"/>
<path transform="translate(498,649)" d="m0 0h5l1 8-3 10-3 2h-3v-14l2-5z" fill="#C09B86"/>
<path transform="translate(1286,575)" d="m0 0h8l-1 2-25 4-14 3h-4v2l-18 4h-12l4-2 24-5 10-2z" fill="#C59E88"/>
<path transform="translate(437,551)" d="m0 0h3v2l4 1 7 5 5 5 15 13 11 12 8 13-1 3-9-14-9-11-8-7-10-8-12-10z" fill="#493838"/>
<path transform="translate(1436,1542)" d="m0 0 5 1v2l3 1-1 2-9 2-2 1h-15l5-5z" fill="#71706E"/>
<path transform="translate(1431,986)" d="m0 0 4 1 19 4 13 2v1l-7 1h-1v3l-9-1-11-4-6-4z" fill="#835144"/>
<path transform="translate(180,979)" d="m0 0 5 1 4 11-1 4h-4v-3l-6-1-2-4v-7z" fill="#DCBDA6"/>
<path transform="translate(1787,839)" d="m0 0 2 1-1 5-10 13-2-2-5 3-2 2-3-1 8-8 8-10h2v-2z" fill="#3A2422"/>
<path transform="translate(262,762)" d="m0 0 5 2 5 4 8 7 6 6v4l-5-2-9-8v-2l-4-1-6-8z" fill="#846E65"/>
<path transform="translate(850,714)" d="m0 0h3l1 3-2 18-2 3-4-1v-18z" fill="#433738"/>
<path transform="translate(915,328)" d="m0 0h1v6l-13 13h-4v-2l-6 5-2-1 9-9 5-3 4-5z" fill="#433535"/>
<path transform="translate(1478,1247)" d="m0 0 1 3-5 12-4 6-6 11-11 18-3 3 2-6 4-7 1-4 2-1 6-11 11-23z" fill="#989E9C"/>
<path transform="translate(1545,1077)" d="m0 0 4 2 15 14 4 5v2l-4-1-16-11 4-1-3-3-3-1z" fill="#503D3B"/>
<path transform="translate(863,668)" d="m0 0h2v2l3 1-2 5-6 7-6-2-2-7 1-2 7-2z" fill="#351F1E"/>
<path transform="translate(1380,547)" d="m0 0h5l-4 2-5 2h-3v2l-13 4-17 5h-3v2l-12 2 4-3h3v-2l18-5-1-2 9-2 7-1z" fill="#D1B09A"/>
<path transform="translate(1085,1529)" d="m0 0 4 1v2l4 2 5 3 5 10-1 2-2-5-3-1v-2h-2v-2h-5-2l-3 3-4-8v-2h2v-2z" fill="#442C29"/>
<path transform="translate(801,1496)" d="m0 0 2 1v5l-4 8-6 8-3 1v3l-5 3 2-6 6-11 4-5 2-6z" fill="#F5F7F8"/>
<path transform="translate(1569,1448)" d="m0 0 5 1-1 3 2 1v9l-1 3h-3v-2l-6 4-1-1 1-8z" fill="#311A18"/>
<path transform="translate(1013,754)" d="m0 0 4 2 2 10 2 17 3 16 5 18-1 4-6-17-2-4-3-28-1-11z" fill="#B3BEBE"/>
<path transform="translate(1511,514)" d="m0 0 2 2 3 6 1 10v27l-4 16-5 12-1 3 2 1-5 1 3-13 5-10 3-13v-33l-3-1-1-2z" fill="#826F66"/>
<path transform="translate(1326,561)" d="m0 0 9 1-3 2-4 1v2l-13 4h-9v-2l2-1-4-2 20-4z" fill="#D5B59F"/>
<path transform="translate(1184,882)" d="m0 0 5 2 6 12 12 34-1 3-6-16v-3h-2l-5-12-7-16v-2h-2z" fill="#895E51"/>
<path transform="translate(616,727)" d="m0 0 5 2 1 2-12 6-16 7-5 2-3-1 9-5 10-6 9-5z" fill="#351F1E"/>
<path transform="translate(1548,576)" d="m0 0h2l-1 3-20 8-9 3-3-1 4-4 7-3 12-5z" fill="#271A18"/>
<path transform="translate(235,129)" d="m0 0 2 1-3 1v2l-16 8-3 3-17 9-19 12-3 1v-2l5-3h2v-2l12-7 15-9 8-5 10-5z" fill="#A7C4C6"/>
<path transform="translate(753,1261)" d="m0 0h29l36 2h13l13 1 3 2-1 3-9-3-29-1-27-2-28-1z" fill="#957365"/>
<path transform="translate(1192,932)" d="m0 0 4 2 5 12-3-1-4-9-4 1-6 4-11 10h-9l-5-2v-1l11-1 10-6 7-6z" fill="#9D9F9C"/>
<path transform="translate(903,667)" d="m0 0 5 1 11 8 15 11-3 1-5-2v-2l-4 1-4-3-1-3-9-3-3-3z" fill="#422C2A"/>
<path transform="translate(131,1034)" d="m0 0 4 4 5 9 8 11v2l3 1 1 5h2l7 11v3l3 1v3l3 1 1 3 3 2-1 2-5-5-9-12-7-11-7-10-11-16z" fill="#926556"/>
<path transform="translate(1494,1007)" d="m0 0 9 1 5 3 12 3 3 3v2h5v2l4 1-2 1-9-2-25-11z" fill="#533834"/>
<path transform="translate(1367,761)" d="m0 0 3 1-5 3-12 8-7 5-4 6-7 2 6-7 7-8 8-6h2v-2z" fill="#DDBEA7"/>
<path transform="translate(1827,1217)" d="m0 0 2 2 2 18 6 40v9h-1l-4-26-2-6-2-12z" fill="#878885"/>
<path transform="translate(204,1061)" d="m0 0 4 5 7 11 7 10 3 2 2 13h2l3 6-1 2-3-3-9-17-3-5-1-6h-2l-6-9-3-6z" fill="#7E5145"/>
<path transform="translate(1077,608)" d="m0 0h8l-4 2 3 2-38 4h-8l4-2 21-4z" fill="#B3BEBE"/>
<path transform="translate(248,1145)" d="m0 0h1l1 9 3-1-2 6-5 6-6 3-14 1-16-6-1-2 15 5h13l7-5 3-8z" fill="#6F6C69"/>
<path transform="translate(1088,610)" d="m0 0h13v1l-51 7h-23v-1l57-6z" fill="#9A9E9B"/>
<path transform="translate(1860,1393)" d="m0 0 2 1 1 9 3 4 3 17v17h-1l-7-36z" fill="#3A2524"/>
<path transform="translate(137,1099)" d="m0 0 3 1 9 15v3l-3-3h-4l-2 3-5-11 1-7z" fill="#CBD7DE"/>
<path transform="translate(1361,782)" d="m0 0v3l-15 11-11 8-8 2 2-4 7-2 1-2h2l1-3 2-3 5-2 3-3 6-3 4-1z" fill="#351F1E"/>
<path transform="translate(1193,1726)" d="m0 0h15v2l-12 4h-15l-3-3 5-2z" fill="#301312"/>
<path transform="translate(394,1164)" d="m0 0 5 1 15 6 21 8 11 5 12 5-3 1-13-5-38-15-10-5z" fill="#493838"/>
<path transform="translate(209,1059)" d="m0 0 7 6 11 7 2 2v6l-7 2h-5l-3-5 1-2 3 2 1-2 5-1-2-3-6-3-6-5z" fill="#2F1210"/>
<path transform="translate(1381,1550)" d="m0 0h11l-1 3-7 4-6 1v-3l-9 2-4-1 1-1-3-2 12-2z" fill="#463938"/>
<path transform="translate(1322,952)" d="m0 0h5l-2 2-8 3h-2l-1 5-7 1v3h-21v-1l14-2 6-2h3v-5l9-3z" fill="#583C38"/>
<path transform="translate(632,1556)" d="m0 0 2 1-16 8-19 9-10 6-8 4-3-1 16-9 23-12 9-4z" fill="#F9F6F1"/>
<path transform="translate(703,1244)" d="m0 0 21 1 4 2-1 2-9 1h-8l-7-1-1-1-9-1v-1z" fill="#140A0A"/>
<path transform="translate(857,1226)" d="m0 0 2 1 2 10-6 2-9 1-29 1v-1l10-2 28-2z" fill="#939391"/>
<path transform="translate(1191,935)" d="m0 0 4 1 5 12-2 5-3 2h-7l-6-2-5-2-1-4 8-7zm0 2-5 3-6 7 2 4 11 2 5-3-1-6-3-6z" fill="#B3BEBD"/>
<path transform="translate(231,875)" d="m0 0 6 2 6 9 13 22 5 7 2 1-1 4-5-5-16-27-6-8-3-2-1 3z" fill="#6F4239"/>
<path transform="translate(835,627)" d="m0 0m-3 1 8 1v1l-12 3-6 2-11 2-18 5-3-1 13-5 19-6z" fill="#756D68"/>
<path transform="translate(1897,1625)" d="m0 0h2l2 8 1 9v21h-2l-3-23z" fill="#2E1716"/>
<path transform="translate(1088,1537)" d="m0 0 7 2v2h2l4 5 3 4 2 10v7l-2-3-2-5-1 2h-2l-2-4 3-1-1-8-4-5-7-1-1 3-1-5z" fill="#321513"/>
<path transform="translate(763,1497)" d="m0 0h2v2l-4 1v2l-22 14-4 2h-3v2l-6 4-2-1-1-2 14-8 13-8z" fill="#5C4744"/>
<path transform="translate(1021,1494)" d="m0 0 5 1 12 5 15 4 6 3 9 4 8 5-2 1-8-4-25-9-13-5-7-4z" fill="#B3BEBE"/>
<path transform="translate(1509,77)" d="m0 0 9 2 35 14 13 6-4 1-12-6-20-7-21-8z" fill="#9ABDBF"/>
<path transform="translate(1156,929)" d="m0 0 5 2 3 5 4 9-1 2h-7l-12-4-11-6 3-1 8 4 16 5-2-5-4-4-1-5z" fill="#957365"/>
<path transform="translate(479,891)" d="m0 0v3l-4 8-6 6h-2v2l-10 5-6 2-11-1 4-2 18-4 2-1 3-5 7-6z" fill="#A37D6C"/>
<path transform="translate(464,789)" d="m0 0 4 5 11 16 12 20 1 7h-2l-4-10-12-19-7-10-3-5z" fill="#956B5C"/>
<path transform="translate(484,671)" d="m0 0h1l2 18 1 22-5 13-6 11h-2v-4l2-1 7-15 1-3v-14l-1-3z" fill="#7D5449"/>
<path transform="translate(1510,559)" d="m0 0h2l-1 8-2 2-3 9-1 9-3-1-3 3-5-2 1-2h2v-2h2l2-5 5-9z" fill="#351F1E"/>
<path transform="translate(1636,1141)" d="m0 0h1l1 40v16l-1 29h-1l-1-22v-16z" fill="#653F38"/>
<path transform="translate(306,970)" d="m0 0 5 2 4 4v2l-5 5-3 9-5 2 3-11 1-7-2-3 2-1z" fill="#361F1D"/>
<path transform="translate(1070,870)" d="m0 0 4 1 4 4h3l4 9-2 4-3 1-4-4-4-10z" fill="#FBEFDD"/>
<path transform="translate(189,820)" d="m0 0 5 2 6 7v3h2l1 2 3 1 3 9-5-2-3-3-2-4-4-3-1-3-5-5z" fill="#755046"/>
<path transform="translate(91,993)" d="m0 0 4 2v2l4 2 3 4h3l4 9 2 5 3 1-1 2h-2l-1 2-8-12-3-5-4-4-1-5-3-1z" fill="#544240"/>
<path transform="translate(233,884)" d="m0 0 4 4 8 16 8 17 1 4-3-1-8-16-7-13-3-8z" fill="#7D4D41"/>
<path transform="translate(955,1430)" d="m0 0 4 1 7 9v2h2v7l2 4-4-2-2-4h-2l-1-5h-2l-4-9z" fill="#371D1C"/>
<path transform="translate(1691,945)" d="m0 0 2 1-7 8-11 10-5 1-3 2-3-1 5-5h2v-2l5-3 3-3 5-3 3-3z" fill="#6F4238"/>
<path transform="translate(1192,917)" d="m0 0h1v9l-11 6-6 2h-8l-6-3-7-4-7-2v-2l-2-1 9 2 15 7 9-1 12-6z" fill="#9D9F9C"/>
<path transform="translate(1480,598)" d="m0 0h5l-2 2-5 1v2l-18 7-7 1 1-5 7-3 12-2z" fill="#A3A5A2"/>
<path transform="translate(672,1535)" d="m0 0m-1 1m-3 1h3v2h-2v2l-11 4-15 7-6 4-11 3 4-4 33-16z" fill="#F7F8F9"/>
<path transform="translate(1701,928)" d="m0 0 2 1-1 2h-2l-2 4-24 24h-3v2l-8 7-4 2 6-8 9-8 8-7 7-7 8-7 2-3h2z" fill="#7E4D41"/>
<path transform="translate(1140,778)" d="m0 0h14l1 5-3 3-1 3-5-2-1-3-5-1-2-3h2z" fill="#714238"/>
<path transform="translate(1507,499)" d="m0 0h2l-1 3-3 2h-3v2l-4 2h-3v3l5-2 1-2 9 2 1 3-8-2-3 3h-3l8 8-1 4-1-3-4-2-5-7v-2l-4-2 11-6z" fill="#9B9E9C"/>
<path transform="translate(1281,952)" d="m0 0h9v1l-9 2-8 4-21 2h-10l-9-4 2-1 5 2h10l20-2 9-3z" fill="#947264"/>
<path transform="translate(364,884)" d="m0 0 2 1-3 4 1 7 2 3 2 7 2 2-4 1-12-15-3-2 1-2 7 5 1-7z" fill="#4B2B26"/>
<path transform="translate(1108,1591)" d="m0 0h4l2 10v8l-3-4-2 5-2-1-1-16z" fill="#36201F"/>
<path transform="translate(292,999)" d="m0 0 2 1-7 8h5l-5 5-11 6h-11v-1l11-1v-2l-3-1 8-4z" fill="#85574A"/>
<path transform="translate(1406,622)" d="m0 0m-7 1h17l-3 2-9 2-8 3-14 4-6 3-2-1 3-1v-2l11-4h5l1-3z" fill="#A3A5A2"/>
<path transform="translate(576,1584)" d="m0 0h2l-2 4-5 4-11 3-1 3-9 5-7 3-3-1 28-17z" fill="#EFE6DF"/>
<path transform="translate(1511,1170)" d="m0 0h5l-1 7-1-2-3 2-4 7-6 9-3 9h-2v-9l3-1 8-17 4-4z" fill="#ABC0C1"/>
<path transform="translate(1371,633)" d="m0 0 6 1-3 3-21 8-9 3 3-6 7-2 9-3z" fill="#AAB5B5"/>
<path transform="translate(373,503)" d="m0 0 5 2 16 10 14 9 7 4-1 2-12-4-5-5-9-6-1-3-5-2-9-6z" fill="#B2BDBD"/>
<path transform="translate(1402,1687)" d="m0 0h6l-3 2-7 2-10 1-8 2-26 4h-6l3-2 16-2 6-2z" fill="#8E8682"/>
<path transform="translate(1176,812)" d="m0 0h7l5 3 10 3 4 3 5-1 7 2 5 2h6l-3 3h-7l-2-3h-14l-2-3-10-3v-2l-10-2z" fill="#DEBFA8"/>
<path transform="translate(1290,700)" d="m0 0h2l-1 4h-2l-1 3-9 7-3 1v2l-10 6-4 2 6-8 2-3 7-3 7-7h4z" fill="#FDEDD8"/>
<path transform="translate(96,319)" d="m0 0 1 3h2l3 13-1-15 3 4 2 8h-1v11l-3-3-1-2-2 2-3-10z" fill="#64413B"/>
<path transform="translate(835,1437)" d="m0 0h4l-1 3-4 2-2 4-5 3-7 8-5 4 2-4 3-3v-2l-2-2 6-4 5-6 5-2z" fill="#5E4946"/>
<path transform="translate(1519,986)" d="m0 0h2l-1 3-8 4-8 3-1 5-2 1-9-6 4-2 14-5 8-2z" fill="#957263"/>
<path transform="translate(263,917)" d="m0 0 5 5 3 4 3 5 10 9 10 11h-3l-8-9-6-3-9-11-6-7z" fill="#82584C"/>
<path transform="translate(1450,611)" d="m0 0 3 1-5 3-7 1-2 4h-2v2l-10 2v2l-7 2 1-2 5-3 1-2-9 3-2-1 7-3 10-2 9-4h3v-2z" fill="#61413B"/>
<path transform="translate(201,424)" d="m0 0h5l16 10v2l6 2 5 3v2l-5-1-14-8-12-7z" fill="#533732"/>
<path transform="translate(1672,406)" d="m0 0h1l6 46v8h-1l-1-7v-9l-3-1-3-24z" fill="#CBAC98"/>
<path transform="translate(254,924)" d="m0 0 4 4 6 8 9 11 10 9v2l-4-2-8-7-11-12-7-10z" fill="#7F4F42"/>
<path transform="translate(1854,773)" d="m0 0 1 4h-2v2l4 1-6 4-8 4-7 1 5-5 7-8 4-1z" fill="#392220"/>
<path transform="translate(1446,1022)" d="m0 0 6 1v2l4 2 3 1-1-3 11 3 6 3-4 2 1 2-6-2-4-2h-5l-10-6z" fill="#3E2826"/>
<path transform="translate(1331,565)" d="m0 0h6v1l-13 4v3l-5 2-10 1-2 1h-8l3-2 5-2h4v-2z" fill="#4A2F2B"/>
<path transform="translate(583,510)" d="m0 0 2 2-3 13-5 14-1-4v-7l-1-5 7-12z" fill="#957365"/>
<path transform="translate(1385,41)" d="m0 0 10 1 17 4 6 3v1h-10l-12-3-10-4z" fill="#86BBC9"/>
<path transform="translate(1218,1156)" d="m0 0h10l9 3 22 7v1h-7l-29-8-5-2z" fill="#665D5B"/>
<path transform="translate(714,702)" d="m0 0 5 1 5 5 3 2v4l-3 1-6-5-8-1v-5z" fill="#957365"/>
<path transform="translate(880,645)" d="m0 0 3 1-11 6-1 6 11 2v1h-10l-10-1v-3l6-5 5-5z" fill="#C7A18B"/>
<path transform="translate(954,291)" d="m0 0v3l-8 12-9 9-4 2 2-4 3-4-3 3-2-1 7-7 8-7z" fill="#4F3F3D"/>
<path transform="translate(491,644)" d="m0 0h1l1 27 2 5 7-4h2l-1 4-6 7h-2v-2l-3-1-1-2z" fill="#331A19"/>
<path transform="translate(312,973)" d="m0 0 6 2h11l9-1-4 4-21 4-4 4 1-5 3-3h2z" fill="#7D4639"/>
<path transform="translate(290,954)" d="m0 0 5 2 7 8 4 5 1 4-5-1-7-9-6-4z" fill="#301412"/>
<path transform="translate(1220,947)" d="m0 0 5 1 9 4 6 2h18l14-3 5-2h10v1l-10 2-9 3-7 1h-22l-13-4-6-4z" fill="#DEBFA8"/>
<path transform="translate(1035,783)" d="m0 0 3 4 8 16-1 2-8-14 1 5 5 16 1 10-2-1-2-12-5-12-1-4v-9z" fill="#937265"/>
<path transform="translate(722,669)" d="m0 0 3 1-15 6-27 12-3-1 32-16z" fill="#653F38"/>
<path transform="translate(1306,571)" d="m0 0h5v2l-9 3 11-1-2 5-8 2-6-1v-4l-4-1 9-3h4z" fill="#553D3A"/>
<path transform="translate(1344,59)" d="m0 0 9 2 13 4 11 2 12 5 3 2v3h-7l3-2-12-6-21-3-3-1v-2l-7-2z" fill="#CBD7DE"/>
<path transform="translate(1723,1891)" d="m0 0 4 1-3 3-35 6h-3v-2z" fill="#9DC6C9"/>
<path transform="translate(360,950)" d="m0 0v3l-9 11-14 7-13 3-6-1v-1l19-4 6-4 7-2 4-7z" fill="#DEBFA8"/>
<path transform="translate(1556,583)" d="m0 0 3 1-2 2-13 4-12 4-18 4v2l-3 1h-7v-2l7-1 9-4 21-6z" fill="#7B4E43"/>
<path transform="translate(518,1621)" d="m0 0h4v3h6l-4 3-10 4-9 1v-2l5-3 6-4h2z" fill="#67534E"/>
<path transform="translate(1543,1519)" d="m0 0 1 4-2 5-2-1-7 1 3-2h2l-1-2-11 1-25 8-4 2h-6l3-2 27-9 12-3h5l4 3z" fill="#B1BCBC"/>
<path transform="translate(390,1177)" d="m0 0 5 1 11 5 10 3 9 3-2 1 1 3-11-3-10-5h-2v-2l-5-1-6-4z" fill="#9DA09D"/>
<path transform="translate(467,811)" d="m0 0 3 4 8 16 3 8 1 5v7l-2 7h-1l-1-18-3-9-5-9-3-7z" fill="#9B7262"/>
<path transform="translate(1212,605)" d="m0 0h11v2h-7l-3 1-3-1v2h-5l-5 1-35 6h-6v-1z" fill="#A2A9A7"/>
<path transform="translate(1892,1587)" d="m0 0h2l2 20 2 11v5l-3 1-3-22-1-11z" fill="#2F1514"/>
<path transform="translate(1804,968)" d="m0 0 2 4 7 25v10l-2-1-7-30-1-5z" fill="#A07F70"/>
<path transform="translate(1730,908)" d="m0 0h2v2l2 1-22 22-2-3 6-7 8-7z" fill="#4D4343"/>
<path transform="translate(711,669)" d="m0 0m-3 1h3l-2 4-21 10-10 5-2-1 10-7 14-7z" fill="#8E7165"/>
<path transform="translate(1608,408)" d="m0 0h3l-2 6-6 4-3 1v6l-4 4-3-1 1-6h2l2-4 5-6z" fill="#24100F"/>
<path transform="translate(950,291)" d="m0 0 2 1-11 11-8 7-5 6-11 9-4 4-2-1 10-10 7-6 20-20z" fill="#A2A9A8"/>
<path transform="translate(1178,865)" d="m0 0 5 5 5 8 10 19 1 8-2-1-7-17-6-10-4-6-2-1z" fill="#C39C86"/>
<path transform="translate(831,802)" d="m0 0h1l1 23-1 10-3 15h-1v-11z" fill="#7D4639"/>
<path transform="translate(493,613)" d="m0 0h1l1 8v47l5-1-2 4-5-1z" fill="#8D7B72"/>
<path transform="translate(1614,999)" d="m0 0 2 1-6 7-8 4-13 3-4-1 8-3 16-8z" fill="#7E5347"/>
<path transform="translate(1436,965)" d="m0 0m-4 1 5 1v2h-3l-1 3-9 2-4-1 1-2h-8l4-2z" fill="#3B1D1A"/>
<path transform="translate(259,765)" d="m0 0 3 1 8 10 6 7 14 10 5 6-5-2-5-4-6-4-7-6-7-9-6-8z" fill="#DEBFA8"/>
<path transform="translate(368,625)" d="m0 0 5 3 4 9-1 2-3-3-2-7h-3l3 13 2 5-1 3-1-5h-2l-4-11v-7z" fill="#D9B8A2"/>
<path transform="translate(878,631)" d="m0 0h23v2h-2v2l-3 2-9 1-2-6-12 1v-1z" fill="#5D3D38"/>
<path transform="translate(1691,499)" d="m0 0 4 2 1 9-2 1h-7l-3-4 1-4h3z" fill="#FCEED9"/>
<path transform="translate(430,756)" d="m0 0h2l8 11 5 9 8 10 9 14-1 2-4-6v-2l-3-1-4-7-10-13-5-8-5-7z" fill="#825447"/>
<path transform="translate(1382,761)" d="m0 0 2 1-12 11-6 9-5 5-4 5-10 5-2-1 9-7 7-5 10-13 8-8z" fill="#764B41"/>
<path transform="translate(857,704)" d="m0 0h1v8l-2 20-5 24h-2l1-11z" fill="#A68372"/>
<path transform="translate(168,960)" d="m0 0 13 5 4 6-1 2-9-3-7-4-1-5z" fill="#37201E"/>
<path transform="translate(1195,755)" d="m0 0 5 3h6l-2 2-8 3-12 2-3-3z" fill="#351F1E"/>
<path transform="translate(47,931)" d="m0 0 5 4 5 6 6 10v3l-4-1-7-11-4-4z" fill="#281A18"/>
<path transform="translate(336,857)" d="m0 0 8 3 4 10 5 6 2-3 1 2-2 7-6-5-2-6-5-5-5-7z" fill="#AF8B79"/>
<path transform="translate(361,512)" d="m0 0 4 2 11 6 5 3 4 4v2l-5-2-9-5-5-2-5-5z" fill="#150A0A"/>
<path transform="translate(1812,1077)" d="m0 0h1l5 42v8l-2-4-1-1-2-24-2-14z" fill="#858785"/>
<path transform="translate(113,1015)" d="m0 0 5 3 3 4v2l3 1 4 7 3 2-1 4-2 2-4-7-8-11v-2h-2l-2-4z" fill="#341614"/>
<path transform="translate(1462 1e3)" d="m0 0 11 1-1 2 3 2v2l-7 2h-6l-3-2v-3l6-2z" fill="#FBD8BE"/>
<path transform="translate(146,925)" d="m0 0h2l11 15 3 5v3h2l3 8-4-2-6-9v-2h-2l-4-9-4-6z" fill="#CFAC96"/>
<path transform="translate(373,874)" d="m0 0 6 1 9 11 8 8-3 1-11-11-4-5-4-1-5 2-1 4h-2l2-5z" fill="#815347"/>
<path transform="translate(394,675)" d="m0 0 2 2 3 7 1 13h2l1 9-3-1v10h-1l-2-14-2-4v-9h1l2 10h1l-3-14z" fill="#6A443C"/>
<path transform="translate(291,464)" d="m0 0 5 1 7 3 9 4v2l6 2 9 5 1 3-5-2-31-16z" fill="#C4A490"/>
<path transform="translate(979,260)" d="m0 0 2 3-10 10-1 3-8 7-7 5 2-4 9-9 2-5 8-7z" fill="#B4BFBF"/>
<path transform="translate(198,1054)" d="m0 0 2 1 3 5 8 15 2 4h2l4 10v3l-5-8-2-4-5-5-5-9-4-10z" fill="#D1AF98"/>
<path transform="translate(1122,926)" d="m0 0 14 7 3 1v-2l6 2 9 7-3 1-9-4-12-4-8-7z" fill="#706C68"/>
<path transform="translate(1477,913)" d="m0 0h5v4l-2 3-10 2h-5l2-5z" fill="#6E4840"/>
<path transform="translate(1418,1697)" d="m0 0 2 2-53 9-11 1v-1l31-6 15-3z" fill="#5A3C38"/>
<path transform="translate(788,1471)" d="m0 0 2 1-8 8-5 6-8 6h-4l1-3 6-5h2v-2l13-10z" fill="#7D574C"/>
<path transform="translate(1548,1640)" d="m0 0h2v3h2l3 17v9h-1l-2-16-1-4h-2v5h-2l-3-8v-3h2z" fill="#493D3E"/>
<path transform="translate(666,1541)" d="m0 0h5l-4 3-13 6h-3v2l-9 3-4-1 16-8z" fill="#ECD2BC"/>
<path transform="translate(853,1175)" d="m0 0 2 4 4 12 3 21-1 4-7-29-1-5z" fill="#643F38"/>
<path transform="translate(232,878)" d="m0 0 4 2 4 5 5 8-1 2-3 3-7-13-2-3z" fill="#351F1E"/>
<path transform="translate(1081,869)" d="m0 0 4 4 9 13-1 2h-4l1 4-4-4-3-10v-3z" fill="#8D7165"/>
<path transform="translate(1174,779)" d="m0 0 3 1-14 5-5 5 3 11 3 2 15 2v1h-11l-9-3-3-10v-5l7-6z" fill="#DEBFA8"/>
<path transform="translate(1395,547)" d="m0 0v3l-2 2 4 2-12 5-3-1v-1l-5-1 4-1v-2l13-5z" fill="#402C2B"/>
<path transform="translate(965,274)" d="m0 0 2 1-11 11-4 5-6 4-10 10-2-2 10-10 8-7z" fill="#F7F9FA"/>
<path transform="translate(1161,1729)" d="m0 0h6l2 5h39v1l-8 1h-31l-8-1-1-2h2z" fill="#5C4B49"/>
<path transform="translate(833,1457)" d="m0 0v3l-1 7 3-5h2l1-5h2l-1 6-2 3h-2v3h-2l-1 3v-2l-4 3-2 3 1-5 2-3v-3l-5 5 2-5 4-6z" fill="#483B3B"/>
<path transform="translate(229,1075)" d="m0 0 7 6 4 4-5-1-2-1h-6l-1 7-5-3-3-5h3l1-2v2l5-2h2z" fill="#351F1E"/>
<path transform="translate(1375,936)" d="m0 0 4 1-2 2-30 5-8 2-4-1 8-3z" fill="#714238"/>
<path transform="translate(1193,909)" d="m0 0 3 4 1 14 8 18 7 6 3 2-6-1-5-4-9-18-2-13z" fill="#563B38"/>
<path transform="translate(1203,583)" d="m0 0m-4 1h4v2l-28 6-5 2-11 2 1-3z" fill="#B3BEBE"/>
<path transform="translate(1636,394)" d="m0 0 1 2-5 1v2l-12 6-7 7-2-1 7-7 1-2-4-1 4-1v-2z" fill="#7B5247"/>
<path transform="translate(1015,1492)" d="m0 0h5l1 3 5 2 12 5 20 7 1 2-11-3-8-3-9-2-16-10z" fill="#9B9F9C"/>
<path transform="translate(655,1246)" d="m0 0 25 1v2h13l7 1v2h-10l-35-5z" fill="#3E2928"/>
<path transform="translate(1416 1e3)" d="m0 0 11 3 8 5 7 3 2 2-6-1v-2l-3 2 1 2-4-2-15-10z" fill="#7C5E55"/>
<path transform="translate(355,846)" d="m0 0h2v2l4 1 2 1v2h2l2 5h2v13l-4 4-3 5-3 2 2-6h2l1-5 4-1-3-12-8-7z" fill="#7C584D"/>
<path transform="translate(772)" d="m0 0h15l-2 6-12 1z" fill="#CBD7DE"/>
<path transform="translate(984,1463)" d="m0 0 7 6 8 7 10 9 6 4 3 3h-5l-10-9-1-2-5-3-13-13z" fill="#A5ACAB"/>
<path transform="translate(198,1039)" d="m0 0 3 3 7 14v3l-5-6 1 8-4-3-5-10 1-2 4 2z" fill="#40201C"/>
<path transform="translate(292,1008)" d="m0 0v3l-6 6-10 4-14-1-14-4 4-1 13 3h11l11-6z" fill="#C59E88"/>
<path transform="translate(239,1006)" d="m0 0 10 2 11 4 9 2 1 2h-9l-15-4-7-5z" fill="#5D3D38"/>
<path transform="translate(355,959)" d="m0 0v3l-5 5-12 6-10 2h-9l-1-2h6l15-4 12-6z" fill="#C59E88"/>
<path transform="translate(1778,842)" d="m0 0h4l-2 4-13 14-6 5-2-1 9-10 9-11z" fill="#3A1D1B"/>
<path transform="translate(625,728)" d="m0 0 2 2-13 8-15 8-4-1 5-3 6-3 1-2 9-4z" fill="#7E5145"/>
<path transform="translate(1350,651)" d="m0 0 4 1-8 4-8 6-10 3 1-3h2v-2l10-6z" fill="#341D1C"/>
<path transform="translate(492,613)" d="m0 0h1l1 15v44h4l-1 4-3 1-2-6z" fill="#523835"/>
<path transform="translate(1410,631)" d="m0 0h9l-3 2-16 5-10 2 1-3 7-3 2-2h7z" fill="#855547"/>
<path transform="translate(1624,1298)" d="m0 0 1 4-2 1zm-2 5h1l-1 9-3 10-4 2-2 3 1-7h2l1-8 4-8z" fill="#61443F"/>
<path transform="translate(1207,933)" d="m0 0 4 4v4l4 2 9 7 9 5v1h-5l-11-7-5-4-6-8v-3z" fill="#80564A"/>
<path transform="translate(1359,770)" d="m0 0h2v2l-8 7-9 8-4 1-1 3-4 3h-2v2l-4 1v-2l8-6 12-11z" fill="#764C42"/>
<path transform="translate(867,1236)" d="m0 0 5 1 2 3v4l-4 1-7-2-1-1v-5z" fill="#28110F"/>
<path transform="translate(1512,1175)" d="m0 0h2l1 4-3 9-1-2-5 2-7 12-1-2 5-10 6-8z" fill="#A0A4A1"/>
<path transform="translate(1477,955)" d="m0 0h2l2 4-6 3-6-1-15 3h-12l1-2 16-1 14-4z" fill="#5E3D38"/>
<path transform="translate(1468,955)" d="m0 0h6l-1 3-14 4-10 1-5-1v-1l21-5z" fill="#855547"/>
<path transform="translate(1385,640)" d="m0 0h5l-3 2-11 4-8 2-15 6-4-1 10-4 12-6z" fill="#6E4138"/>
<path transform="translate(368,629)" d="m0 0h3l3 9 3 1 8 14 2 4-5-5-5-6-5-9-1 5-2-3z" fill="#8A7166"/>
<path transform="translate(1391,541)" d="m0 0 1 2-5 1v2l-19 6-7 1v-2l13-5z" fill="#F6F7F6"/>
<path transform="translate(1215,1150)" d="m0 0 9 2 11 3 6 3v2l-7-1-17-5-3-3z" fill="#A4AAA9"/>
<path transform="translate(1203,941)" d="m0 0 10 8 1-3 11 7 4 4-11-3-9-4-6-7z" fill="#351F1E"/>
<path transform="translate(1237,739)" d="m0 0 2 1-11 8h-2l-2 4-8 5-7 3-5 2v-3l17-9z" fill="#855A4E"/>
<path transform="translate(413,727)" d="m0 0 6 4 9 11 6 5 4 6 1 6-3-3-4-5-3-5-7-8-5-4-4-5z" fill="#BF9A85"/>
<path transform="translate(851,644)" d="m0 0h6l2 4-1 6-1 4 1 1v5l-3 3-2-1 1-6-2-5 3-5 1-4-5-1z" fill="#C1AD9F"/>
<path transform="translate(1852,269)" d="m0 0 2 2v8l-3 9h-3v-16h3z" fill="#1D0E0D"/>
<path transform="translate(204,988)" d="m0 0 12 5 4 2 5 2 1 3 3 1-4 1-7-4-10-4-4-4z" fill="#341D1C"/>
<path transform="translate(267,945)" d="m0 0 7 6 10 8 11 8 6 5-1 2-22-16-11-11z" fill="#C59E88"/>
<path transform="translate(718,788)" d="m0 0h15l-2 5-5 2h-5l-3-3z" fill="#957365"/>
<path transform="translate(1541,482)" d="m0 0m-1 1m-2 1h2v2l-17 10-10 4-3 1v2l-5 1 4-5 17-8 8-5z" fill="#CBBCAE"/>
<path transform="translate(845,1415)" d="m0 0v3l-8 10-6 7-3 3-16 14v-3l15-14 11-11z" fill="#919896"/>
<path transform="translate(858,1403)" d="m0 0v3l-3 1-2 4-9 11-8 10-5 3 2-4 10-11 4-8 5-4h2v-2z" fill="#887066"/>
<path transform="translate(808,1247)" d="m0 0h22v2l-18 1-14 2h-8v-1z" fill="#351F1E"/>
<path transform="translate(201,1042)" d="m0 0h2l3 9h2l5 8 5 5 12 8-3 1-12-8-8-9-6-11z" fill="#825346"/>
<path transform="translate(198,980)" d="m0 0h3v2l5 2 7 6 7 4-1 2-14-7h-3l-4-4z" fill="#513937"/>
<path transform="translate(1160,827)" d="m0 0h3v11l3 8 2 1-1 4-2-3v8l-2-3-2-9-1-1z" fill="#5F413C"/>
<path transform="translate(1170,817)" d="m0 0 1 4h-2l-2 6-1 2v7l1 7-2-3-2-5v-8h-3v13h-1v-15l4-1 1-5 1 3-1 4h2l2-6z" fill="#A58676"/>
<path transform="translate(1341,567)" d="m0 0h3v2l-3 2-10 2-4 1v2l-13 2h-3l3-3 12-3 11-3z" fill="#493838"/>
<path transform="translate(1111,917)" d="m0 0h2l4 5 5 3 5 6 13 7 1 3-4-2-15-8-8-8z" fill="#AD9A8D"/>
<path transform="translate(1232,841)" d="m0 0h1v7l-6 9-4 3 1-7 3-8z" fill="#311411"/>
<path transform="translate(919,1359)" d="m0 0 3 3 5 10 5 5 2 9h2v5l-4-5-3-6v-2h-2l-6-13v-2h-2z" fill="#ECCFB7"/>
<path transform="translate(240,1134)" d="m0 0 2 3 1 11-2 9-5 3h-7l-5-4h15l1-6z" fill="#C9A48D"/>
<path transform="translate(273,1120)" d="m0 0 7 1 6 4v3l-9-1-7-4z" fill="#B2BEBE"/>
<path transform="translate(266,938)" d="m0 0h3v2h5l2 5 5 5 2 4-4-1-10-9-3-4z" fill="#2F1210"/>
<path transform="translate(1714,925)" d="m0 0m-1 1m-1 1m-1 1m-1 1m-1 1 2 1-1 4-12 12h-4l2-4 7-6z" fill="#443635"/>
<path transform="translate(1053,826)" d="m0 0 2 1 1 6 1 3h-2l1 10h-2l-3-7-1-12z" fill="#FEF2E1"/>
<path transform="translate(167,1090)" d="m0 0 4 2 8 10 4 7 4 6 3 2 1 4-4-1-18-27z" fill="#855648"/>
<path transform="translate(255,1096)" d="m0 0 5 2 6 3v2l6 2 7 4v2l4 1 4 3-6-1-22-13-4-4z" fill="#453231"/>
<path transform="translate(1418,983)" d="m0 0h17l3 2-1 1 13 3 9 2v1l-11-1-13-3-1-1-14-2z" fill="#BB9581"/>
<path transform="translate(275,770)" d="m0 0 4 2 6 5 9 11 4 2 1-3h6v2l-4 1-2 3-5-1-7-8-9-10z" fill="#B39583"/>
<path transform="translate(1591,434)" d="m0 0v3l-8 10-12 12-5 1 4-5 8-7 6-7 5-5z" fill="#A48373"/>
<path transform="translate(836,1142)" d="m0 0h1l5 23 4 9v12l-2-4-7-28-1-5z" fill="#A5B0AF"/>
<path transform="translate(836,1052)" d="m0 0h1l1 22 2 13 2 14v5l-3-4-2-22-1-3z" fill="#AA8372"/>
<path transform="translate(1635,997)" d="m0 0 2 1-1 3 5 11-1 2-2-2-2 1-4-9-6 3 2-5z" fill="#5D3D38"/>
<path transform="translate(1506,987)" d="m0 0h12l-2 2-8 2-12 4h-22v-1l21-1 7-2v-2z" fill="#CAA58E"/>
<path transform="translate(1278,956)" d="m0 0h2l1 3-6 1-10 4-2-1-18-1v-1l28-3z" fill="#7D4639"/>
<path transform="translate(405,727)" d="m0 0 4 2v2h2l4 8 8 7 3 3-1 3-9-9v-2l-4-1-5-6z" fill="#764F45"/>
<path transform="translate(391,668)" d="m0 0 3 4 3 12 3 14-1 3-3-6-2-10-4-7 1-3 1 2z" fill="#39201E"/>
<path transform="translate(816,409)" d="m0 0h3l-2 4-10 9-8 6-2-1 10-11 7-5h2z" fill="#594441"/>
<path transform="translate(1657,364)" d="m0 0 2 2 3 16v8h-1l-2-9-1-1-1 5h-1v-19z" fill="#7D4639"/>
<path transform="translate(680,1247)" d="m0 0h22l1 1 7 1 1 2h-11l-20-2z" fill="#2F110F"/>
<path transform="translate(369,860)" d="m0 0h1l2 7 2 4 5 3-2 1-5 1-2 3-2-1v-3l-4 1 2-5 3-1z" fill="#432421"/>
<path transform="translate(862,622)" d="m0 0h3v2l-3 3 4 1v2l-12 1-4-2 4-4z" fill="#9EA09D"/>
<path transform="translate(1449,1300)" d="m0 0 2 4-11 16-5 7h-2l2-5 3-6h3l2-6 5-9z" fill="#828582"/>
<path transform="translate(1511,1052)" d="m0 0 5 2 7 5-2 4-5-1v-2l-5-2-5-3 2-1 2 1z" fill="#382221"/>
<path transform="translate(1180,972)" d="m0 0 9 1h16l10-1h10v1l-18 2-1 1h-16l-6-1v-2z" fill="#959B98"/>
<path transform="translate(216,861)" d="m0 0 6 1 5 5 6 3 1 2-5-2-8-4 6 9-1 3-9-12z" fill="#C59E88"/>
<path transform="translate(605,738)" d="m0 0 2 1-5 3-26 13-2-1 3-4 12-5 7-3z" fill="#543B38"/>
<path transform="translate(716,686)" d="m0 0h7l-1 4-8 5-5-2 2-4z" fill="#FCECD7"/>
<path transform="translate(1026,630)" d="m0 0h12l5 1v1l-27 2h-10v-2z" fill="#A9B0AF"/>
<path transform="translate(165,400)" d="m0 0 7 4 15 10 2 3-5-1-17-11-2-2z" fill="#442A27"/>
<path transform="translate(1e3 243)" d="m0 0 2 1-26 26-5 4-2-1 11-11 8-7z" fill="#999D9A"/>
<path transform="translate(1651,224)" d="m0 0h2v30h-1v-5h-2v-17z" fill="#957365"/>
<path transform="translate(1872,1471)" d="m0 0h2l5 21v9l-2-1-3-15v-6h-2z" fill="#423536"/>
<path transform="translate(84,978)" d="m0 0h2v2h2l7 10 9 12v2l-4-2-5-5-6-11-5-6z" fill="#463636"/>
<path transform="translate(786,1471)" d="m0 0 2 1-12 10h-2v2l-10 6-7 4h-2v-2l12-7 14-10z" fill="#F2ECE6"/>
<path transform="translate(901,1327)" d="m0 0h2l16 34v2h-2l-4-7-3-9-8-16z" fill="#916B5E"/>
<path transform="translate(649,1237)" d="m0 0 13 1 23 3 2 2h-14l-7-2h-9l-8-2z" fill="#2F1210"/>
<path transform="translate(193 1e3)" d="m0 0h21l6 2-4 1h-29l-1 2v-4z" fill="#DEBFA8"/>
<path transform="translate(372,941)" d="m0 0 1 3-8 13-3 2-3-1 3-6 3-3z" fill="#7E483B"/>
<path transform="translate(520,637)" d="m0 0v3l-4 5-3 5-7 8-4 4 3-10 3-3 3-1 8-10z" fill="#907265"/>
<path transform="translate(865,639)" d="m0 0 4 1-1 4-1 2 4 1-6 5h-4l2-10-2-1z" fill="#7D4639"/>
<path transform="translate(460,567)" d="m0 0 4 2 12 11 8 9 6 11-1 2-9-14-13-14-7-6z" fill="#6F6C69"/>
<path transform="translate(1535,592)" d="m0 0 4 1-12 5-7 3h-6v-3l12-4z" fill="#BB9580"/>
<path transform="translate(1513,561)" d="m0 0 1 3-3 10-4 7-2 12h-2v-5l1-1 1-9 4-10 3-1z" fill="#4F3836"/>
<path transform="translate(463,907)" d="m0 0h2l-1 3-14 4-10 2h-9v-1l14-3z" fill="#6F453B"/>
<path transform="translate(1040,768)" d="m0 0h9l9 3v1l-10-1-6-1 3 9 2 10-2 1-5-15z" fill="#9D9E9A"/>
<path transform="translate(1047,628)" d="m0 0h34v1l-26 2h-10v-2z" fill="#A5AAA8"/>
<path transform="translate(754,458)" d="m0 0 2 1-11 10-11 9-12 10-2-1 10-9 11-9z" fill="#919896"/>
<path transform="translate(735,1611)" d="m0 0 1 2-1 2h3l1 3-3 3 1-5h-2l-3 10-4 9-2 1 1-7 6-13z" fill="#5D3F3A"/>
<path transform="translate(861,1247)" d="m0 0 3 1 2 6-2-1v-2l-8-1-10 2-1 1-13 1v-2l21-4z" fill="#919896"/>
<path transform="translate(829,1098)" d="m0 0 2 2 3 16 1 6v15h-1l-4-28z" fill="#999F9E"/>
<path transform="translate(227,1082)" d="m0 0h6l-3 2 3 10 4 8 2 5-6-4-1-5-3-7-3-1-1-4z" fill="#433738"/>
<path transform="translate(1347,943)" d="m0 0h9v2l-9 3-9 1-3-2 8-3z" fill="#381C1A"/>
<path transform="translate(1253,819)" d="m0 0 2 1-4 5-4 7h-2l-2 5-4 5-2 2-3 2 1-5 5-5 2-5 6-5 4-6z" fill="#764D43"/>
<path transform="translate(312,804)" d="m0 0 4 1 3 7-1 4-3 1-2-1-2-10z" fill="#F9D6BC"/>
<path transform="translate(1848,784)" d="m0 0 3 1-6 4h-2v2l-11 8-2 1 2-4 2-5 4-3 6-2z" fill="#5F433E"/>
<path transform="translate(852,668)" d="m0 0v3l-4 6 1 5v7l-4 16h-1v-10l2-6v-15z" fill="#9BA09E"/>
<path transform="translate(1165,1581)" d="m0 0 5 1 3 4v2h-12v-3-3z" fill="#2F110F"/>
<path transform="translate(982,1478)" d="m0 0 7 6 12 11 13 8-3 1-14-9-15-15z" fill="#6F6C69"/>
<path transform="translate(857,1205)" d="m0 0h2l7 28v2l-3-1-6-26z" fill="#6F6C69"/>
<path transform="translate(89,1006)" d="m0 0 5 5 7 10 5 8-1 3-6-8-4-5-6-11z" fill="#B2BCBC"/>
<path transform="translate(437,751)" d="m0 0 3 3 4 6 7 6 2 3h2l4-10 1 2-3 11-2 1-16-14z" fill="#DBBCA5"/>
<path transform="translate(409,729)" d="m0 0 3 1 14 16 1 4-14-12-2-4v-3h-2z" fill="#341E1D"/>
<path transform="translate(1650,190)" d="m0 0h5l-1 11-2 9h-1l-1-8z" fill="#756D68"/>
<path transform="translate(757,1493)" d="m0 0 2 1-2 3 2 3-5 4-7 1-4 1 2-3 4-2 5-6z" fill="#7E655D"/>
<path transform="translate(1438,962)" d="m0 0h5l-2 3-20 4h-4l1-3 3-1h11v-2z" fill="#754E44"/>
<path transform="translate(481,748)" d="m0 0 1 3-4 5-4 4v9l6 2 1 2h-5v2l-4-2v-14l2-4 4-2 1-3h2z" fill="#7D4639"/>
<path transform="translate(1880,743)" d="m0 0h2l-1 4-10 9-4 1 2-5 9-8z" fill="#F8E5D0"/>
<path transform="translate(712,665)" d="m0 0v3l-5 2-3 3-9 3-10 3 3-3z" fill="#9EA09D"/>
<path transform="translate(625,1563)" d="m0 0 2 1-16 8-13 7-4-1 19-10z" fill="#8A6053"/>
<path transform="translate(501,1200)" d="m0 0 7 1 28 9v1l-9-1-26-8z" fill="#75493E"/>
<path transform="translate(288 1e3)" d="m0 0 3 1-10 10-5 3-12-2-4-2h18l7-6 1-2h2z" fill="#CDA892"/>
<path transform="translate(1419,988)" d="m0 0 8 1 13 5v2l-7-1-14-4z" fill="#3D201D"/>
<path transform="translate(161,952)" d="m0 0 8 6 10 4 12 9-3 1-7-5v-2l-10-3-5-3v-2l-4-1z" fill="#8A6254"/>
<path transform="translate(1221,855)" d="m0 0 1 3-2 3-1 5 6-3 5-5-2 5-6 7-3 1-2-2v-7z" fill="#B6917D"/>
<path transform="translate(341,818)" d="m0 0 4 2 7 8 9 7v2l3 1 3 5 3 3-1 2-7-7-7-8-6-5-7-8z" fill="#B89683"/>
<path transform="translate(1613,402)" d="m0 0h6l-2 4-6 7h-2l2-5-5 3h-3l7-7z" fill="#372120"/>
<path transform="translate(185,1007)" d="m0 0 2 1 4 10 1 6h2l7 16-1 2-10-19-5-12z" fill="#84574A"/>
<path transform="translate(194,983)" d="m0 0 4 2 12 9 10 4 6 4-2 1-20-9-10-10z" fill="#6A4038"/>
<path transform="translate(1388,758)" d="m0 0 2 1-5 5-8 10-4 6-1-3 1-4 8-8 3-5z" fill="#D4B39C"/>
<path transform="translate(1227,729)" d="m0 0 2 4-7 5-5 3-6 2 2-4z" fill="#F5E3CF"/>
<path transform="translate(1502,504)" d="m0 0 9 1 3 7-1 3-3-5-9-3-2 4h-4v-3l7-2z" fill="#CAD0D0"/>
<path transform="translate(351,496)" d="m0 0 4 2 4 3 5 2 4 4-1 2-12-4-1-3 1-1-4-4z" fill="#452B27"/>
<path transform="translate(335,489)" d="m0 0 5 1 12 7 1 2-8-1h-3v-2h-5z" fill="#3A2221"/>
<path transform="translate(1397,1663)" d="m0 0m-2 1h2v2h2v2l-7 2-7 1-2-3h2v-2z" fill="#CED9E0"/>
<path transform="translate(1821,1163)" d="m0 0h1l2 20v8h-2l-2-6v-12z" fill="#828482"/>
<path transform="translate(1463,918)" d="m0 0 3 1-5 3-19 5-12 1 1-2 12-2h5v-2l14-3z" fill="#C59E88"/>
<path transform="translate(425,904)" d="m0 0 3 1v2l3 1v4l3 1-5 1-5-1-3-2h2v-4l2-2z" fill="#331A19"/>
<path transform="translate(317,828)" d="m0 0 4 5 4 6v3l4 2 3 7 4 6v2l-4-2-4-7-1-6-3-1-6-10z" fill="#543A36"/>
<path transform="translate(1389,740)" d="m0 0 6 1-1 4-7 5-2-1-1-4z" fill="#DABAA3"/>
<path transform="translate(373,650)" d="m0 0 6 8v2h2l5 12 4 7-1 3-8-14-3-9-3-1-2-4z" fill="#CFAC96"/>
<path transform="translate(432,541)" d="m0 0 10 5 5 5 1 3-4-1-11-8z" fill="#B3BEBE"/>
<path transform="translate(812,1490)" d="m0 0h2l-2 7-4 1-1 3-4 3-1 5h-2l2-7 3-5 4-6z" fill="#3B201E"/>
<path transform="translate(1207,1145)" d="m0 0 6 1 23 7-4 2-11-3-13-5z" fill="#74706D"/>
<path transform="translate(228,872)" d="m0 0 5 1 2 3-4-1 2 10 3 6-1 4-7-15z" fill="#8D5D4F"/>
<path transform="translate(350,829)" d="m0 0 5 3 7 7 7 8 3 3-1 2-10-9-5-6-5-5z" fill="#584846"/>
<path transform="translate(1244,817)" d="m0 0h10l-4 2-5 1-2 9-4 2-3 4h-2v-2h2l2-5 4-6v-4z" fill="#7B4F44"/>
<path transform="translate(1907,690)" d="m0 0h1v8l-3 8-2 7-1-3v-9l4-10z" fill="#EFDBC7"/>
<path transform="translate(1551,469)" d="m0 0 2 1-14 10-9 6-2-1 2-4 13-7z" fill="#3E2C2C"/>
<path transform="translate(662,1547)" d="m0 0 4 1-1 2h3v2l-10 3-5 2 2-5 1-2 6-1z" fill="#423536"/>
<path transform="translate(1531,1523)" d="m0 0h6l1 3-6 3h-3v-2l2-1-10 2-7 2-4-1z" fill="#9FA19E"/>
<path transform="translate(782,1244)" d="m0 0h6l1 2-3 2h-18l-3-2 4-1z" fill="#140A0A"/>
<path transform="translate(1412,971)" d="m0 0h9l-1 3-8 2h-10l-1-2 10-2z" fill="#240F0E"/>
<path transform="translate(456,897)" d="m0 0v3l-7 6-6 3-9-1-7-3 4-1 4 2h9z" fill="#73473D"/>
<path transform="translate(803,644)" d="m0 0 4 1-9 3-20 5-3-1h2v-2z" fill="#673F38"/>
<path transform="translate(1944,624)" d="m0 0 1 3-2 7-5 4h-2l1-7 5-5h2z" fill="#1E100F"/>
<path transform="translate(1501,588)" d="m0 0 1 4v4l-10 2v-5z" fill="#140A0A"/>
<path transform="translate(1350,557)" d="m0 0h8v1l-15 4h-3v2l-12 2 4-3h3v-2z" fill="#C6A18C"/>
<path transform="translate(1349,555)" d="m0 0h8l-4 2-22 6v-3l13-4z" fill="#F7F9FA"/>
<path transform="translate(205,146)" d="m0 0v3l-20 12-7 5h-2v-2l5-3h2v-2l12-7z" fill="#A0C6CA"/>
<path transform="translate(936,1391)" d="m0 0 5 5 8 6 5 5-1 2-12-8v-2h-2l-3-5z" fill="#EBDAC7"/>
<path transform="translate(1407,1366)" d="m0 0 2 3v2l-5 4-4 5-4 2h-3l1-3 8-7z" fill="#9CA5A3"/>
<path transform="translate(1821,1143)" d="m0 0h1l2 15v15h-2l-1-10z" fill="#3A2625"/>
<path transform="translate(1494,945)" d="m0 0h5l-1 4-3 3-4-1h-2v-2l-7 2v-2z" fill="#A78372"/>
<path transform="translate(1089,888)" d="m0 0h2l2 2h3l5 6h-2l1 5-5-5h-3l-3-6z" fill="#74453B"/>
<path transform="translate(1183,882)" d="m0 0 2 2 3 10 3 7-1 3-1-4h-2l-7-15h3z" fill="#3B2524"/>
<path transform="translate(353,836)" d="m0 0 4 1 4 5h-2v5l5 1 3 4-1 3-1-3h-2v-2l-6-2v-7l-5-1z" fill="#301413"/>
<path transform="translate(1046,789)" d="m0 0h2l4 9 4 6 2 5-1 4-2-2-9-19z" fill="#9A9D9A"/>
<path transform="translate(269,769)" d="m0 0 5 2 6 7 5 5-3 1-10-9v-2h-2z" fill="#603E38"/>
<path transform="translate(432,755)" d="m0 0 3 1 7 11 6 8h-2l-1 2-3-4-3-6-7-9z" fill="#321B1A"/>
<path transform="translate(516,646)" d="m0 0 2 1-8 8-5 8-3 6-3 3h-5l4-2 5-9 7-9z" fill="#653F38"/>
<path transform="translate(1473,612)" d="m0 0h5l-4 2-4 1v2l-15 6h-6l3-2 10-5 9-3z" fill="#AE8A78"/>
<path transform="translate(1305,584)" d="m0 0h5l-4 2-5 2-11 2-1 2-7 2-2-2 13-5z" fill="#9DA7A7"/>
<path transform="translate(1239,585)" d="m0 0h11l-4 2-14 3h-12l4-2z" fill="#A98979"/>
<path transform="translate(1656,385)" d="m0 0h1l2 9v12h-1l-1-11-1-2h-11l4-3 6-4z" fill="#804C3E"/>
<path transform="translate(919,1363)" d="m0 0h2l6 13v2h2l3 6-1 2-4-4-2-3v-4l-3-1z" fill="#8C675A"/>
<path transform="translate(209,1342)" d="m0 0 3 4 2 9 1 4v6h-2l-4-14z" fill="#84BBC9"/>
<path transform="translate(848,1143)" d="m0 0h1l6 27-1 4v-3h-2l-4-18z" fill="#AF8D7C"/>
<path transform="translate(110,1018)" d="m0 0 6 2 6 9-1 2-5-1v-2h-2l-4-8z" fill="#3C2625"/>
<path transform="translate(1429 1e3)" d="m0 0h8l3 1 1 3-5 2-8-1z" fill="#FCD9BF"/>
<path transform="translate(1168,972)" d="m0 0h12l4 1v2l26 1v1h-23l-19-4z" fill="#AFB8B8"/>
<path transform="translate(1310,962)" d="m0 0 12 1 1 2h-10l-2 3-18-1v-1h14v-3z" fill="#836156"/>
<path transform="translate(428,906)" d="m0 0 9 2 5 1-4 1-1 2-1 1h6v1l-5 1h-8v-2h4l-3-3v-2z" fill="#351F1E"/>
<path transform="translate(1207,760)" d="m0 0 2 1-5 4-12 6-5 2 5-7 7-1v-2z" fill="#BC9681"/>
<path transform="translate(1250,598)" d="m0 0h6l-3 2-2 2h-5l-3 1-5 1-4-1v2l-8 1-3-2 24-5z" fill="#B1C5C8"/>
<path transform="translate(749,466)" d="m0 0 2 1-6 7-5 5-10 7-2-1 12-11 8-7z" fill="#523A38"/>
<path transform="translate(239,445)" d="m0 0 11 6 7 4v3l-5-2-14-8z" fill="#412522"/>
<path transform="translate(190,414)" d="m0 0 12 6 12 7 9 6-2 1-15-9-9-5-7-4z" fill="#6F6C69"/>
<path transform="translate(801,1472)" d="m0 0h2l-2 4-3 4-7 3-2 2-7 2 5-5 9-6z" fill="#93B4B6"/>
<path transform="translate(436,1179)" d="m0 0 7 1 10 4 5 3 2 2-6-1-18-7z" fill="#5D3D38"/>
<path transform="translate(173,973)" d="m0 0 9 1v2l-7 2 2 9 1 4-3-3-3-8v-6z" fill="#7C5449"/>
<path transform="translate(170,967)" d="m0 0 5 2 8 2v3h-10l-1 4h-2z" fill="#2F1513"/>
<path transform="translate(1413,733)" d="m0 0h3l1 4-7 6-3-1-1-3 4-5z" fill="#150A0A"/>
<path transform="translate(1425,621)" d="m0 0h2l-2 4-6 4h-4v-2h-2v-3z" fill="#37201F"/>
<path transform="translate(1198,591)" d="m0 0m-5 1h16v1l-16 3-17 1 4-2z" fill="#D2B19B"/>
<path transform="translate(1578,446)" d="m0 0 2 1-8 8-14 11-2 3-3-1 10-9 8-7z" fill="#45312F"/>
<path transform="translate(193,413)" d="m0 0 5 2 15 8-4 2-18-10z" fill="#71544C"/>
<path transform="translate(1117,1645)" d="m0 0 2 2 2 6 3 8v7l-2-4h-2l-3-16z" fill="#301D1D"/>
<path transform="translate(985,1466)" d="m0 0 7 6 7 7 4 2 8 8v2l-4-2-7-7-8-7-7-7z" fill="#756E6A"/>
<path transform="translate(383,926)" d="m0 0 1 3-5 6-4 6h-2v-14l4 6z" fill="#6C4138"/>
<path transform="translate(354,897)" d="m0 0 6 5 4 6 3 5 1 7-4-3-8-16z" fill="#D0AD96"/>
<path transform="translate(511,668)" d="m0 0v3l-14 14-2 4-3 1 2-7 5-3 7-8z" fill="#5A504E"/>
<path transform="translate(880,647)" d="m0 0h5l-4 3-7 4v3l6 2v1h-6l-4-4 2-5z" fill="#FCF3E6"/>
<path transform="translate(403,544)" d="m0 0 5 2 15 10 4 3v3h-2v-2h-3l-1-2-3-1v-2l-4-2-3-1-4-4z" fill="#825043"/>
<path transform="translate(822,411)" d="m0 0m-1 1m-2 1 2 1-2 1zm-2 2h2l-1 4-13 11-2-1 2-4 10-8z" fill="#564948"/>
<path transform="translate(693,1539)" d="m0 0m-3 1h3l-1 4-5 3h-3v2h-6l4-5z" fill="#3F2E2E"/>
<path transform="translate(742,1510)" d="m0 0m-2 1h2v3l-7 4h-3v2l-6 4-2-1-1-2 14-8z" fill="#5B4542"/>
<path transform="translate(1643,985)" d="m0 0 3 1-12 9-6 3v-2l-2-1 10-6 5-2z" fill="#5C3C37"/>
<path transform="translate(310,799)" d="m0 0 5 2 6 7 5 6-1 2-2-1v-2l-3-1v-3l-3-1-2-3-3-1-1 5h-1z" fill="#C09F8C"/>
<path transform="translate(1038,766)" d="m0 0 7 1v1h-5l2 10 3 9v3h-2l-5-15z" fill="#947265"/>
<path transform="translate(1457,611)" d="m0 0h2l-1 3h-4v3l-7 2-6-2 2-2z" fill="#5D3D38"/>
<path transform="translate(1681,492)" d="m0 0h2l2 15 2 3 4 2-5 1-3-2-2-6z" fill="#EECCB4"/>
<path transform="translate(189,416)" d="m0 0 5 1 9 6-1 3-5-2-10-6z" fill="#5D3E38"/>
<path transform="translate(120,371)" d="m0 0 4 2 14 9 3 2-1 3-12-8-8-6z" fill="#40201C"/>
<path transform="translate(1406,1658)" d="m0 0h10l-2 2-9 1-10 4h-6l1-2 5-2 7-1z" fill="#F7F9FA"/>
<path transform="translate(834,1109)" d="m0 0h1l3 16 1 12-1-4h-2l-2-11z" fill="#382524"/>
<path transform="translate(1680,954)" d="m0 0m-1 1m-1 1m-1 1m-1 1m-1 1m-1 1m-1 1m-1 1m-1 1 1 2-4 5-8 6h-2l2-4 8-7z" fill="#754438"/>
<path transform="translate(433,763)" d="m0 0 5 4 6 10 7 9-1 2-5-5-5-8-3-3-4-7z" fill="#CDA993"/>
<path transform="translate(1380,764)" d="m0 0 2 1-9 9-1 6-9 5 1-3h2l2-5 9-10z" fill="#BD9682"/>
<path transform="translate(559,754)" d="m0 0 3 1-16 8-8 1v-3l14-4z" fill="#483838"/>
<path transform="translate(909,332)" d="m0 0h2l-2 4-8 8 1 3h-3v-2l-6 5-2-1 9-9 5-3z" fill="#372323"/>
<path transform="translate(632,1556)" d="m0 0 2 1-22 11h-2l1-3 14-7 5-1z" fill="#FAF5EC"/>
<path transform="translate(703,1524)" d="m0 0 2 1-16 9-6 1v2l-10 3 3-3z" fill="#C3A491"/>
<path transform="translate(811,1462)" d="m0 0 2 1-10 9-6 4h-3v-2l5-1v-2l-2-1 6-5 2 1-3 4 7-7z" fill="#6A615E"/>
<path transform="translate(1382,1295)" d="m0 0 5 5 8 14-2 4-11-21z" fill="#F5F7F8"/>
<path transform="translate(1478,1247)" d="m0 0 1 3-5 12-5 3 2-6 5-11z" fill="#979E9C"/>
<path transform="translate(221,1087)" d="m0 0 4 2 2 13h2l3 6-1 2-3-3-6-12z" fill="#64453E"/>
<path transform="translate(1434,1013)" d="m0 0h4v2l5 1 4 7h-3l-8-5z" fill="#604743"/>
<path transform="translate(1301,948)" d="m0 0m14-1h5l-3 2-17 3h-10l3-3h13z" fill="#A68271"/>
<path transform="translate(414,910)" d="m0 0 4 2v2l18 3 3-1h8l-1 2-14 1-14-3-4-4z" fill="#C59E88"/>
<path transform="translate(373,907)" d="m0 0 8 1 4 6 2 7v7h-1l-3-13-3-4-6-2zm12 21m-2 1 2 1-6 5 2-4z" fill="#BB9581"/>
<path transform="translate(233,884)" d="m0 0 4 4 6 13v3h-2l-5-9-3-8z" fill="#77483D"/>
<path transform="translate(441,762)" d="m0 0 13 13 3 1 2-8h1l-1 10-4 1-12-12z" fill="#8C7165"/>
<path transform="translate(1194,752)" d="m0 0 3 1-8 5-12 4v-2h2v-2l6-4 2-1z" fill="#E3C1A9"/>
<path transform="translate(487,737)" d="m0 0 1 4-5 13-6 7-1-3 5-7 5-12z" fill="#919896"/>
<path transform="translate(774,651)" d="m0 0 3 1h-2v2l-17 5h-3l1-3z" fill="#704238"/>
<path transform="translate(817,645)" d="m0 0h6l1 2-10 3v2h-7l3-4z" fill="#36201F"/>
<path transform="translate(471,578)" d="m0 0 5 4 8 10 6 10-1 3-9-14-9-11z" fill="#443738"/>
<path transform="translate(1332,566)" d="m0 0h5l1 3-9 3-5 1-2-2 5-3z" fill="#361F1E"/>
<path transform="translate(1666,467)" d="m0 0h1v5h2l1 8v18h-1l-3-24z" fill="#83584B"/>
<path transform="translate(63,260)" d="m0 0h15l5 2 3 6-1 2-6-4-2-5h-14z" fill="#FFF2DE"/>
<path transform="translate(1904,1817)" d="m0 0h1v7l-5 2 1 5-4 1-2-4v-9l2 4v2l6-2z" fill="#73706D"/>
<path transform="translate(1630 1e3)" d="m0 0 4 2 2 8-1 5-1 18h-1l-1-30-4-1z" fill="#7F6F68"/>
<path transform="translate(1475,950)" d="m0 0h7l-2 2-18 6-8 1 3-2 10-2v-2z" fill="#CCA891"/>
<path transform="translate(367,908)" d="m0 0h3l5 6-1 7h-2l-1-3-2-1z" fill="#180C0B"/>
<path transform="translate(448,775)" d="m0 0 4 2 6 5 2 1 2 6h2l2 5 1 4-5-5-3-6-3-2v-2l-3-1z" fill="#321816"/>
<path transform="translate(476,756)" d="m0 0 1 2v8l2 1 17 1v1h-19l-3-1-1-2v-6z" fill="#927265"/>
<path transform="translate(1507,559)" d="m0 0 1 2-4 11-7 10-5 4 2-5 6-7 6-14z" fill="#736C68"/>
<path transform="translate(1511,514)" d="m0 0 2 2 3 6 1 10v22h-1l-1-31-3-1-1-2z" fill="#726C68"/>
<path transform="translate(101,305)" d="m0 0 3 4 5 11-3 1-1 4-3-11z" fill="#919896"/>
<path transform="translate(1538,88)" d="m0 0 5 1 21 9 2 2-7-1-9-5-12-4z" fill="#9BB6B6"/>
<path transform="translate(880,1378)" d="m0 0 3 1-1 8h-1v-6l-4 3h-2l-2 4-6 8v-3l8-11z" fill="#7A6E67"/>
<path transform="translate(867,1255)" d="m0 0 2 4 4 16 3 9-1 4-6-17-1-5z" fill="#726C68"/>
<path transform="translate(1232,1154)" d="m0 0h7l13 4-1 3-11-3-8-3z" fill="#5C5352"/>
<path transform="translate(281,941)" d="m0 0 4 2 7 8 4 4 5 6-1 2-6-7-3-2v-2l-4-2-6-7z" fill="#6E4138"/>
<path transform="translate(1452,713)" d="m0 0 10 1 3 3v2l-5 1v-2l-7-2-3-2z" fill="#D2B099"/>
<path transform="translate(1517,497)" d="m0 0 2 1-3 1v5h-2l-1 6-2-4h-5l-1-2 5-1v-2z" fill="#F7F9FA"/>
<path transform="translate(327,482)" d="m0 0 5 1 10 5 5 3-1 2-6-2-13-8z" fill="#D2B29C"/>
<path transform="translate(332,483)" d="m0 0 5 1 25 12 2 2-5-1-8-4-5-2-14-7z" fill="#B3BEBE"/>
<path transform="translate(151,385)" d="m0 0 4 2v2h3v2h3v2l4 1v2l-4 1-7-5-3-5z" fill="#4A3D3D"/>
<path transform="translate(782,1526)" d="m0 0h3l-1 5-3 6-3 3h-2l1-4 2-5z" fill="#DFE2E4"/>
<path transform="translate(1853,1391)" d="m0 0 4 2 2 10v7l-4-4-2-10z" fill="#392423"/>
<path transform="translate(301,974)" d="m0 0 2 2v7l-6 12-5 5-1-3 2-3h3l2-5 2-4z" fill="#C8A28C"/>
<path transform="translate(1304,961)" d="m0 0h5l-2 1v4h-21v-1l14-2z" fill="#583F3B"/>
<path transform="translate(1229,956)" d="m0 0 5 1 4 4v2l-7 1-2-5-2-2z" fill="#463738"/>
<path transform="translate(331,810)" d="m0 0 4 1 4 4v2h2v2l-5-2-1 1-5-3-1-4z" fill="#594541"/>
<path transform="translate(1044,790)" d="m0 0h2l8 16 3 9h-2l-8-16z" fill="#8B7165"/>
<path transform="translate(1036,790)" d="m0 0 3 3 5 9-1 2v3 5l-2-4-4-12-1-1z" fill="#C39D88"/>
<path transform="translate(1013,741)" d="m0 0 15 5 11 6-4 1-9-5-9-3-4-2z" fill="#BE9E8C"/>
<path transform="translate(502,672)" d="m0 0h2l-1 4-6 7h-2v-2l-3-1 1-2h4l2-4z" fill="#301413"/>
<path transform="translate(1371,633)" d="m0 0 6 1-3 3-8 3h-5l5-5z" fill="#ADB7B7"/>
<path transform="translate(1498,574)" d="m0 0h2l-2 4-5 6-6 12-1-2 5-13z" fill="#999D9A"/>
<path transform="translate(1528,486)" d="m0 0 2 1-4 5-15 7-2-1 13-8z" fill="#888986"/>
<path transform="translate(1561,454)" d="m0 0h2l-1 4-4 2v2l-5 1-4 3-4-1 4-2v-2l8-3z" fill="#3E2927"/>
<path transform="translate(1609,413)" d="m0 0v3l-12 14-2-1 4-4 1-6 5-4z" fill="#4D2B26"/>
<path transform="translate(898,340)" d="m0 0 2 1-8 8-1 3-7 6-2-1 7-9z" fill="#45312F"/>
<path transform="translate(1451,1693)" d="m0 0m-6 1 10 1v1l-21 3-4-1 4-2z" fill="#7F6F67"/>
<path transform="translate(386,1151)" d="m0 0 10 3 5 4 5 2-4 1-16-7z" fill="#FEECD7"/>
<path transform="translate(1029,821)" d="m0 0 3 1 8 24-1 3-10-25z" fill="#BCAA9D"/>
<path transform="translate(315,802)" d="m0 0 4 1 7 9 3 5 8 7-1 2-9-8-4-6-3-4v-2l-4-2z" fill="#6F5C56"/>
<path transform="translate(844,643)" d="m0 0h16v5h-2l-1-3h-6l-2 1h-13l4-2z" fill="#93918D"/>
<path transform="translate(1662,335)" d="m0 0h2l3 20v5h-2l-2-9z" fill="#CBA690"/>
<path transform="translate(381,1647)" d="m0 0 11 7 6 4 1 3-2 1v-2l-5-2-2-1v-2l-5-2-5-5z" fill="#B3C3C4"/>
<path transform="translate(1478,1538)" d="m0 0 4 1-3 1 10 2v1h-10l-3 1-8-1 2-2z" fill="#A9B6B6"/>
<path transform="translate(535,1276)" d="m0 0h15v2l-2 1h-18v-2z" fill="#6F6C69"/>
<path transform="translate(1509 1e3)" d="m0 0 4 1 2 4 4 1 1 3-9-1-1-2-3-2 4-1z" fill="#825043"/>
<path transform="translate(1192,917)" d="m0 0h1v9l-11 6-1 1h-5l3-3 12-6z" fill="#999D9A"/>
<path transform="translate(140,918)" d="m0 0 5 5 1 4-5-4 5 13-1 3-6-15v-5z" fill="#8A6053"/>
<path transform="translate(1153,785)" d="m0 0 1 2 1 10-3 1-5-8v-2h-2l1-2 5 3z" fill="#937366"/>
<path transform="translate(1420,736)" d="m0 0 3 1-2 2h-3v2l-7 6-9 2 3-3 11-7z" fill="#83584B"/>
<path transform="translate(1448,715)" d="m0 0h5l7 3-1 3-11 1 4-6z" fill="#9A7465"/>
<path transform="translate(1345,565)" d="m0 0 3 1v2h5v2l-8 3h-5l2-4h2v-2l-2-1z" fill="#331A19"/>
<path transform="translate(1553,469)" d="m0 0 2 1-1 3-11 6-8 5-2-1 19-13z" fill="#8F7E75"/>
<path transform="translate(1356,1710)" d="m0 0h14l-3 2-18 3h-5l4-2h5v-2z" fill="#9A9D9B"/>
<path transform="translate(974,1453)" d="m0 0 5 5 6 7v3l-4-2-6-8z" fill="#5E4C49"/>
<path transform="translate(840,1435)" d="m0 0h3l-1 5-5 9h-1v-6l-3 1 1-3 4-2z" fill="#8A837E"/>
<path transform="translate(223,1006)" d="m0 0 9 2 5 2 8 2v2l3 1-8-1-7-3-9-3z" fill="#D1B09A"/>
<path transform="translate(464,789)" d="m0 0 4 5 8 11 1 6-3-3-7-10-3-5z" fill="#855A4D"/>
<path transform="translate(416,745)" d="m0 0 4 1 10 10 3 5v2l-3-1-5-8-3-2v-2h-2v-2l-4-2z" fill="#D1AE97"/>
<path transform="translate(484,671)" d="m0 0h1l2 18v9h-2l-1-3z" fill="#5C3730"/>
<path transform="translate(700,677)" d="m0 0h7l-4 2-20 9-3-1 16-8z" fill="#5D3D38"/>
<path transform="translate(836,646)" d="m0 0h9l-3 2-19 5h-5l4-2 6-2 4-2z" fill="#AAB2B1"/>
<path transform="translate(368,627)" d="m0 0 3 1-3 1 3 13 2 5-1 3-1-5h-2l-3-8 1-9z" fill="#CCA791"/>
<path transform="translate(1467,606)" d="m0 0 2 1v4l-11 3 1-3-7 2 1-2 12-4z" fill="#613E38"/>
<path transform="translate(1450,1680)" d="m0 0h13v1l-19 2-1 1h-14v-1z" fill="#9DA19E"/>
<path transform="translate(1883,1535)" d="m0 0h1l3 17v5l-3 1-2-8v-5l1-3z" fill="#311918"/>
<path transform="translate(131,1034)" d="m0 0 4 4 5 9 5 7-1 3-13-19z" fill="#8A5F52"/>
<path transform="translate(1196,941)" d="m0 0 3 4 1 5-5 5h-7l-3-3h8l4-2z" fill="#BEBEB8"/>
<path transform="translate(1126,913)" d="m0 0 6 1 14 7v2l2 1-5-1-17-9z" fill="#969B99"/>
<path transform="translate(1044,807)" d="m0 0 3 3v2h-2l4 13 2 7-1 4-6-19z" fill="#F7F9FA"/>
<path transform="translate(1035,795)" d="m0 0 3 1 5 16 1 10-2-1-2-12-5-12z" fill="#957365"/>
<path transform="translate(1404,731)" d="m0 0h2l2 3 2 1-9 4-2-1-1-4z" fill="#D7B6A0"/>
<path transform="translate(1591,431)" d="m0 0 3 1-8 9-8 6v-3h2l2-4 3-1 2-4z" fill="#412927"/>
<path transform="translate(1207,1731)" d="m0 0h7l-2 2-14 2h-18v-1l17-1z" fill="#473838"/>
<path transform="translate(558,1603)" d="m0 0 2 1-5 4-9 1-2 4-2-1 5-6h3v-2l5 1z" fill="#423637"/>
<path transform="translate(1890,1574)" d="m0 0h2l1 5v8l-2 4-2-7z" fill="#2A1312"/>
<path transform="translate(534,1224)" d="m0 0 2 1 2 2 6 1-4 2-7 1-3-1 2-5z" fill="#9EA09D"/>
<path transform="translate(1554,1084)" d="m0 0 7 6 7 8v2l-4-1-4-4h3l-7-6z" fill="#8E8E8B"/>
<path transform="translate(308,988)" d="m0 0 1 3-3 8-6 5h-2v2l-5 2 6-7 6-5z" fill="#C09A84"/>
<path transform="translate(1279,960)" d="m0 0h3v2l4 2v1l-14 1 5-5z" fill="#92928E"/>
<path transform="translate(373,874)" d="m0 0 6 1 3 5-8-2-5 2-1 4h-2l2-5z" fill="#7E5347"/>
<path transform="translate(372,852)" d="m0 0 5 5 14 15h-3l-7-6-3-5-6-6z" fill="#321715"/>
<path transform="translate(213,857)" d="m0 0 6 1 4 3-1 2-6-2 3 8h-2l-4-8z" fill="#DEBFA8"/>
<path transform="translate(200,833)" d="m0 0 6 2 3 9-5-2-3-3z" fill="#573832"/>
<path transform="translate(1322,800)" d="m0 0 2 1-8 6-9 4h-7l4-2 5-3 8-1v-2z" fill="#82584C"/>
<path transform="translate(628,720)" d="m0 0 5 1v4l-8 3-1-4z" fill="#341E1D"/>
<path transform="translate(1493,587)" d="m0 0 4 1 2 2-8 4-5 5v-3l3-5z" fill="#452F2C"/>
<path transform="translate(1363,1553)" d="m0 0h12l8 2-3 3h-2v-3l-9 2-4-1 1-1z" fill="#422E2D"/>
<path transform="translate(791,1536)" d="m0 0 2 1-7 11-1-3-3-1 4-6h5z" fill="#341F1D"/>
<path transform="translate(1065,1516)" d="m0 0 10 2-3 1v3l-7 1-2-1v-2h3z" fill="#5E413C"/>
<path transform="translate(975,1451)" d="m0 0 17 17-1 2-13-12-3-4z" fill="#A9B1B0"/>
<path transform="translate(1241,1158)" d="m0 0 11 3 10 3-1 2-9-2-12-3z" fill="#A0A6A4"/>
<path transform="translate(1815,1100)" d="m0 0h1l2 19v8l-2-4-1-1z" fill="#81817E"/>
<path transform="translate(1357,941)" d="m0 0h7l3 3-7 2-8 1 1-2h3v-2l-3-1z" fill="#4B2F2B"/>
<path transform="translate(1789,832)" d="m0 0h2l-2 5-2 3h-3v2l-5 1 3-6 5-3z" fill="#211110"/>
<path transform="translate(1455,732)" d="m0 0 3 1-1 3-6 3h-7l3-3z" fill="#89594B"/>
<path transform="translate(866,677)" d="m0 0h2l-2 5-2 6-2 11-2 1 2-18z" fill="#C7A591"/>
<path transform="translate(673,685)" d="m0 0 2 1-2 3-6 3-1 3-7 2 2-3h2l2-4 2-3z" fill="#9B9C99"/>
<path transform="translate(371,636)" d="m0 0 2 2 1 7 2 7h2l3 6v2h-2l-6-10-2-6z" fill="#815548"/>
<path transform="translate(1511,577)" d="m0 0 1 3 1 8 2 1-8 1 2-9z" fill="#989995"/>
<path transform="translate(1852,261)" d="m0 0 3 3v12h-1l-2-6-2 2v-7z" fill="#472925"/>
<path transform="translate(515,1625)" d="m0 0h2l1 3-4 3-9 1v-2l5-3z" fill="#634E49"/>
<path transform="translate(637,1555)" d="m0 0 3 1h-2v2l-5 2-13 6v-3z" fill="#E9C6AE"/>
<path transform="translate(1556,1501)" d="m0 0 3 1-3 12-2 7h-1l1-11v-6z" fill="#514746"/>
<path transform="translate(818,1473)" d="m0 0h2v4l-3 3-5 7-1-3 5-10z" fill="#9FA5A3"/>
<path transform="translate(829,1447)" d="m0 0v3l-4 5-8 7-6 4-2-1 9-7 7-7z" fill="#989E9B"/>
<path transform="translate(870,1387)" d="m0 0v3l-3 4-2 5-4 4h-2l2-5 3-5 5-5z" fill="#989692"/>
<path transform="translate(903,1334)" d="m0 0 3 4 6 11v2h-3l-5-9-1-5z" fill="#6D4138"/>
<path transform="translate(1208,927)" d="m0 0h2l3 10 4 6 3 4-4-2-5-4-2-5z" fill="#CEAC96"/>
<path transform="translate(366,901)" d="m0 0 2 1v2l4 2 3 3 6 2 2 4-11-5-6-5z" fill="#886053"/>
<path transform="translate(490,724)" d="m0 0h1l-1 9-5 10-2 5-1-3 4-12h2v-5z" fill="#645D5B"/>
<path transform="translate(403,700)" d="m0 0h1l3 13 5 11v3l-4-5-4-10-1-1z" fill="#BF9983"/>
<path transform="translate(965,274)" d="m0 0 2 1-16 16v-4z" fill="#E6EBED"/>
<path transform="translate(1680,1900)" d="m0 0h6l-4 3-7 2h-6l-1-3z" fill="#9AC4C8"/>
<path transform="translate(679,1545)" d="m0 0 2 2-1 1 2 2-7 4h-2v-2l2-2h-7l2-2 6-2z" fill="#4B3E3E"/>
<path transform="translate(1489,1537)" d="m0 0h4l-1 4h-14l1-2z" fill="#8C9492"/>
<path transform="translate(774,1482)" d="m0 0 3 1-5 7-3 2h-4l1-3 6-5h2z" fill="#714940"/>
<path transform="translate(1240,1161)" d="m0 0 7 1 12 4v1h-7l-12-3z" fill="#777572"/>
<path transform="translate(1536,1023)" d="m0 0 16 4 2 1v2l-8-1-10-3z" fill="#5D514F"/>
<path transform="translate(84,993)" d="m0 0 5 4 6 12-3-1-7-10z" fill="#FFF2DE"/>
<path transform="translate(427,902)" d="m0 0 5 1 14 1-2 3h-9l-8-3z" fill="#BF9C87"/>
<path transform="translate(1179,870)" d="m0 0 5 5 3 6v2l-4-1-4-7z" fill="#7F5549"/>
<path transform="translate(307,824)" d="m0 0 2 2 3 7 6 10v3l-6-7-3-4-2-7z" fill="#9E7565"/>
<path transform="translate(804,426)" d="m0 0v3l-5 5-5 4-3-1 5-5z" fill="#504342"/>
<path transform="translate(534,1610)" d="m0 0 2 1-6 8-8 2 3-4h2v-2z" fill="#865F52"/>
<path transform="translate(1885,1531)" d="m0 0 2 3 2 6v9l-2-1-3-16z" fill="#423637"/>
<path transform="translate(834,1432)" d="m0 0v3l-3 5-5 5-4 2v-3l4-1 1-4 1-2h2v-2z" fill="#726C68"/>
<path transform="translate(1679,953)" d="m0 0 2 1-11 11-3 2-3-1 5-5h2v-2l5-3z" fill="#563733"/>
<path transform="translate(1192,932)" d="m0 0 4 2 5 12-3-1-4-9-6 1-1-2z" fill="#989C9A"/>
<path transform="translate(1162,835)" d="m0 0h2l3 8v3h2l3 6v2h-2l-2-4v-3l-4-2z" fill="#926556"/>
<path transform="translate(880,645)" d="m0 0 3 1-11 6-1 6h-2v-8l4-3z" fill="#D2B19B"/>
<path transform="translate(1309,580)" d="m0 0m-2 0 2 1-1 3-7 2h-6l1-2z" fill="#382221"/>
<path transform="translate(1744,482)" d="m0 0h6l-2 6-7 1 1-5z" fill="#1B0D0D"/>
<path transform="translate(805,1510)" d="m0 0h4l-2 5-1 2h-2l-1 4-2-4 1-5z" fill="#3B2726"/>
<path transform="translate(984,1463)" d="m0 0 7 6 8 7 1 4-7-6-9-9z" fill="#9DA2A0"/>
<path transform="translate(1251,1159)" d="m0 0 7 1 8 3-1 3-13-4z" fill="#514645"/>
<path transform="translate(1453,1022)" d="m0 0 10 2 3 3-7-1v2l-4-1-3-2z" fill="#644640"/>
<path transform="translate(163,974)" d="m0 0 5 5 3 9-1 3-3-4-4-10z" fill="#59352D"/>
<path transform="translate(1370,939)" d="m0 0h6l-2 4h-11l1-3z" fill="#3A201E"/>
<path transform="translate(372,924)" d="m0 0 4 1 4 4-2 4-2 2-4-9z" fill="#351F1E"/>
<path transform="translate(383,880)" d="m0 0 4 2 4 3v2h2l5 8-4-2-8-8z" fill="#301311"/>
<path transform="translate(1245,832)" d="m0 0h2l-2 5-5 9-4 2 2-6z" fill="#D4B19B"/>
<path transform="translate(301,789)" d="m0 0 6 1 9 6 1 3-4-2-6-4-7-1z" fill="#443130"/>
<path transform="translate(1197,752)" d="m0 0 3 1-10 6-11 4-2-1 8-4 7-3z" fill="#82564A"/>
<path transform="translate(613,724)" d="m0 0 2 1-10 7-5 3h-5l2-2 5-1v-2l4-3z" fill="#564A48"/>
<path transform="translate(404,727)" d="m0 0 3 3 3 7 3 3 3 1 2 4-5-2-8-8z" fill="#BA9480"/>
<path transform="translate(1358,557)" d="m0 0 2 1-7 3h-6v2l-6 2-4-1h3v-2z" fill="#7C584D"/>
<path transform="translate(93,312)" d="m0 0h2l3 6-1 4-2 4-2-5z" fill="#8D5E50"/>
<path transform="translate(723,1630)" d="m0 0v3l-5 10-2 5-2 1 1-7 5-7z" fill="#959A98"/>
<path transform="translate(1894,1608)" d="m0 0h2l2 10v5l-3 1z" fill="#321B19"/>
<path transform="translate(1543,1519)" d="m0 0 1 4-2 5-2-1-7 1 3-2h2l-1-2-4-2 5-1 4 3z" fill="#ABB2B1"/>
<path transform="translate(834,1443)" d="m0 0 1 3-6 8h-2v2l-3-1 5-6 1-3z" fill="#F4F6F7"/>
<path transform="translate(964,1437)" d="m0 0 3 1 8 12v3h-2l-1-3-4-4v-4h-2z" fill="#9CA19F"/>
<path transform="translate(942,1401)" d="m0 0 4 4 8 13-1 4-7-12-4-7z" fill="#9C958F"/>
<path transform="translate(866,1387)" d="m0 0 2 1-9 14-2-1 6-12z" fill="#F7F9FA"/>
<path transform="translate(1405,1359)" d="m0 0h3l1 5-3 5h-3l1-8z" fill="#F7F9FA"/>
<path transform="translate(1226,1155)" d="m0 0h9l6 3v2l-7-1-6-2z" fill="#BAC1C1"/>
<path transform="translate(119,1034)" d="m0 0 4 5 6 10h-3l-7-10-1-3z" fill="#EEE3D4"/>
<path transform="translate(371,927)" d="m0 0h2v14l-7 8-3 3 2-6 4-5 2-1z" fill="#937062"/>
<path transform="translate(193,821)" d="m0 0 4 2 6 7v3l4 1 1 6-2-1v-4l-4-1v-2h-2l-3-5z" fill="#C19D88"/>
<path transform="translate(1145,779)" d="m0 0h8l-1 4-7 1-3-3z" fill="#351F1E"/>
<path transform="translate(375,638)" d="m0 0 3 3 8 13v3l-4-5-5-6z" fill="#A68473"/>
<path transform="translate(1502,573)" d="m0 0h2l-2 5-3 5h-2v2l-5 5-2 1 1-5 7-6z" fill="#54403E"/>
<path transform="translate(1623,556)" d="m0 0 2 1-12 5-6 2 2-4 8-3z" fill="#5B3730"/>
<path transform="translate(218,434)" d="m0 0h4v2l6 2 5 3v2l-5-1-9-6z" fill="#402422"/>
<path transform="translate(827,399)" d="m0 0 2 1-2 5-6 5-4-2z" fill="#67514D"/>
<path transform="translate(927,313)" d="m0 0 3 1-14 12-3 3-2-1 10-10z" fill="#88837E"/>
<path transform="translate(1436,1542)" d="m0 0 5 1v2l3 1-1 2h-7l2-4-8 1 3-2z" fill="#9EA7A6"/>
<path transform="translate(1880,1538)" d="m0 0h1l3 15-1 5-2-4-2-14z" fill="#BDC5C8"/>
<path transform="translate(828,1434)" d="m0 0 1 2-5 6-10 8-3 2 2-4 13-12z" fill="#989C99"/>
<path transform="translate(868,1246)" d="m0 0h4l-1 2-2-1 2 13-3-1v-4h-2l-1-5z" fill="#63443E"/>
<path transform="translate(682,1249)" d="m0 0h11l7 1v2h-10l-7-1z" fill="#3F2B2A"/>
<path transform="translate(1174,1135)" d="m0 0 6 1 2 1v2l7 2v3l-6-2-9-6z" fill="#7E7E7B"/>
<path transform="translate(1814,1125)" d="m0 0h2l1 9-5 5v-3z" fill="#95C2C4"/>
<path transform="translate(118,1016)" d="m0 0 2 1v3h2l4 7 2 1v2h2l1 4-5-3-3-6-4-4z" fill="#946B5C"/>
<path transform="translate(1630 1e3)" d="m0 0 3 1v16l-2-3-1-10-3-3z" fill="#9FA7A6"/>
<path transform="translate(246,1006)" d="m0 0 5 1 13 4v2l-8-1-10-4z" fill="#855548"/>
<path transform="translate(305,983)" d="m0 0h3v7l-3 3-3 1z" fill="#371A18"/>
<path transform="translate(488,882)" d="m0 0 3 1-1 6-4 3-1-5z" fill="#FFF2DE"/>
<path transform="translate(231,875)" d="m0 0 6 2 4 6-1 4-4-6-4-3-1 3z" fill="#663F38"/>
<path transform="translate(367,860)" d="m0 0h2v10l-4 4-3 5-3 2 2-6h2l1-5 4-1z" fill="#8F6C5E"/>
<path transform="translate(473,737)" d="m0 0 1 4-5 13-3 1 3-10z" fill="#4A2621"/>
<path transform="translate(1309,678)" d="m0 0 3 1-11 8-4 2 2-5 3-3 6-2z" fill="#351F1E"/>
<path transform="translate(889,639)" d="m0 0h11v1l-10 2-5 4-3-1 1-3z" fill="#9FA19D"/>
<path transform="translate(1491,604)" d="m0 0h5l-3 2-4 4-6 2h-5l3-2 4-2 2-3z" fill="#957365"/>
<path transform="translate(1599,419)" d="m0 0h1v6l-4 4-3-1 1-4z" fill="#190C0B"/>
<path transform="translate(1489,1923)" d="m0 0 11 1 8 2v1h-14l-1-2z" fill="#CBD7DE"/>
<path transform="translate(389,1160)" d="m0 0 5 1 16 7-3 1-17-7z" fill="#706C68"/>
<path transform="translate(1188,1142)" d="m0 0 4 1 9 3 1 4-7-2-6-3z" fill="#635A58"/>
<path transform="translate(225,1101)" d="m0 0 3 4 1 4 3 1 2 4v5l-3-4-3-5v-2h-2z" fill="#BE9984"/>
<path transform="translate(237,1085)" d="m0 0h5v2l4 2 4 4-5-1-8-5z" fill="#4D3938"/>
<path transform="translate(1496 1e3)" d="m0 0 9 4 1 3-10-2-1-4z" fill="#794538"/>
<path transform="translate(1662,973)" d="m0 0 1 4-10 8-1-3z" fill="#433231"/>
<path transform="translate(1220,947)" d="m0 0 5 1 9 4 5 2v1l-7-1-9-4z" fill="#D7B69F"/>
<path transform="translate(305,789)" d="m0 0 8 1 6 8h-3l-3-3-8-5z" fill="#A38677"/>
<path transform="translate(688,697)" d="m0 0 2 1-3 1v2l-13 4-3-1 14-6z" fill="#A47B6A"/>
<path transform="translate(1321,671)" d="m0 0 1 3-9 6-5 4-3-1 13-10z" fill="#78493E"/>
<path transform="translate(279,473)" d="m0 0 7 1 6 4v2l-10-3z" fill="#F8E5D0"/>
<path transform="translate(857,373)" d="m0 0v3l-3 1v2l-7 5-2-1 4-6 5-2z" fill="#D2D9D9"/>
<path transform="translate(111,341)" d="m0 0 4 4 5 10-4-2-4-6z" fill="#E4E9EB"/>
<path transform="translate(1103,1585)" d="m0 0 4 4 1 3-1 1v14h-1l-3-19z" fill="#574E4D"/>
<path transform="translate(641,1550)" d="m0 0m-3 1h3v2l-4 3-11 3 4-4z" fill="#F8F7F5"/>
<path transform="translate(823,1472)" d="m0 0 2 1-2 7-5 5v-6l3-1z" fill="#311412"/>
<path transform="translate(825,1460)" d="m0 0 1 4-3 8-6 2 2-5 4-4z" fill="#A6ADAC"/>
<path transform="translate(1597,1377)" d="m0 0 4 2-2 9-4-3 1-6z" fill="#4C4040"/>
<path transform="translate(879,1376)" d="m0 0 4 1 1 5-2-3-5 2-5 6-1-2 4-7z" fill="#939997"/>
<path transform="translate(1589,1013)" d="m0 0 3 1-10 5-9 2v-2l12-5z" fill="#71453B"/>
<path transform="translate(1149,966)" d="m0 0 9 1 10 3v2l-7-1-12-4z" fill="#A7ADAB"/>
<path transform="translate(1458,958)" d="m0 0 4 1-3 3-10 1-5-1v-1z" fill="#895D50"/>
<path transform="translate(1086,914)" d="m0 0h3l1 2 3 1 1 4-4 1v-2h-3v-3l-2-1z" fill="#3C2B2A"/>
<path transform="translate(488,872)" d="m0 0h1v6l-6 9-1-2 4-11z" fill="#633C33"/>
<path transform="translate(478,858)" d="m0 0 1 4-8 16-1-2 5-13h2z" fill="#8F6658"/>
<path transform="translate(782,778)" d="m0 0 2 2 4 16-1 4-5-14z" fill="#DEBFA8"/>
<path transform="translate(1140,778)" d="m0 0h14l-1 4v-3l-10 2 2 3-5-1-2-3h2z" fill="#5D3D38"/>
<path transform="translate(394,672)" d="m0 0 5 3 1 6v9h-1l-2-8-3-7z" fill="#907265"/>
<path transform="translate(824,648)" d="m0 0 5 1-3 2-8 2h-7l3-2z" fill="#8B8580"/>
<path transform="translate(810,645)" d="m0 0h7l-4 3-7 3-3-2 2-3z" fill="#443738"/>
<path transform="translate(884,640)" d="m0 0 3 1-4 1-1 3-5 2-4-1 3-3z" fill="#927265"/>
<path transform="translate(865,623)" d="m0 0h5l2 3-9 2-3-1z" fill="#ACBFBF"/>
<path transform="translate(1757,475)" d="m0 0 1 2-2 5-2 4h-2v2l-6 1 2-1 1-3 4-4h2z" fill="#B28D7A"/>
<path transform="translate(810,411)" d="m0 0 4 1-10 8-4 3h-2v-2l10-8z" fill="#ADB6B5"/>
<path transform="translate(104,331)" d="m0 0 2 1 4 11 1 5-4-5-3-6z" fill="#423232"/>
<path transform="translate(938,308)" d="m0 0 2 1-6 6-3 5h-3l2-5 2-3 5-3z" fill="#3B2827"/>
<path transform="translate(1849,278)" d="m0 0 1 2 3-1-2 9h-3v-8z" fill="#321513"/>
<path transform="translate(969,274)" d="m0 0 1 2-8 7-7 5 2-4 9-9z" fill="#A0A7A5"/>
<path transform="translate(724,1514)" d="m0 0 4 1-1 2h-2v2l-6 3-3-1 3-3h2v-2h3z" fill="#71483F"/>
<path transform="translate(833,1457)" d="m0 0v3l-2 8-2-3-5 5 2-5 4-6z" fill="#4D3A39"/>
<path transform="translate(860,1404)" d="m0 0h2l-1 6-8 4 2-5z" fill="#433738"/>
<path transform="translate(1398,1325)" d="m0 0h3l4 8 1 7-3-3-5-10z" fill="#F7F9FA"/>
<path transform="translate(204,1061)" d="m0 0 4 5 6 9-1 4-6-9-3-6z" fill="#845A4E"/>
<path transform="translate(1453,1018)" d="m0 0 6 1 7 5v2l-5-2-7-3z" fill="#F5F1EB"/>
<path transform="translate(1614,999)" d="m0 0 2 1-5 6-7 1-5 1 1-2z" fill="#9A7060"/>
<path transform="translate(1207,933)" d="m0 0 4 4v4l3 1 1 5-5-5-5-6 1-2z" fill="#764D43"/>
<path transform="translate(1200,917)" d="m0 0 2 3 5 13-1 2-2-1-4-10z" fill="#714238"/>
<path transform="translate(1195,914)" d="m0 0 4 4 1 6-4 3z" fill="#341E1D"/>
<path transform="translate(298,786)" d="m0 0h8l7 2 2 4-10-3v-2h-6l-1 4-2-1z" fill="#DABCA5"/>
<path transform="translate(1448,716)" d="m0 0h4l-2 4-3 3h-5l3-5z" fill="#76453A"/>
<path transform="translate(741,676)" d="m0 0 4 1-8 4-11 2v-2l13-4z" fill="#C7A38F"/>
<path transform="translate(1289,585)" d="m0 0 5 1-1 2-10 2h-5l3-3z" fill="#362120"/>
<path transform="translate(1562,450)" d="m0 0 2 1-8 9-5 1 6-7z" fill="#62504D"/>
<path transform="translate(226,437)" d="m0 0 5 1 6 4 2 4h-4l-4-3h2v-2l-5-2z" fill="#4E332F"/>
<path transform="translate(663,1545)" d="m0 0 2 1-3 3-10 4-3-1h2v-2z" fill="#724E45"/>
<path transform="translate(286,1538)" d="m0 0 3 3 7 13 1 4-4-4-7-14z" fill="#CBD7DE"/>
<path transform="translate(801,1501)" d="m0 0 2 1-4 8-6 8-2 1 2-4 5-8z" fill="#9A9B98"/>
<path transform="translate(798,1460)" d="m0 0 1 2 5-2-2 3-7 4-2 3-2-1 2-4z" fill="#B1ABA4"/>
<path transform="translate(853,1175)" d="m0 0 2 4 4 12-1 3-1-5h-2l-2-7z" fill="#754A40"/>
<path transform="translate(1555,1088)" d="m0 0 5 3 5 6-7-2-6-4 3-1z" fill="#5E5150"/>
<path transform="translate(1517,1017)" d="m0 0 6 1 5 1v2l4 1-2 1-9-2z" fill="#472F2D"/>
<path transform="translate(276,1013)" d="m0 0h2v2l4 1-6 3h-11v-1l11-1v-2l-3-1z" fill="#957365"/>
<path transform="translate(178,991)" d="m0 0 5 5 3 2-1 9h-1l-2-7-4-7z" fill="#81594D"/>
<path transform="translate(1226,865)" d="m0 0v3l-4 6-4-1-2-3 1-3 3 3z" fill="#DEBFA8"/>
<path transform="translate(341,830)" d="m0 0 5 2 4 5 3 5 2 4-6-5-5-8z" fill="#7A584E"/>
<path transform="translate(1160,812)" d="m0 0h3l1 6-1 2-4-1v-6z" fill="#E0D7CE"/>
<path transform="translate(1380,753)" d="m0 0 2 1-10 10-4-1 8-7h2v-2z" fill="#69443B"/>
<path transform="translate(1037,753)" d="m0 0 7 1 9 3 1 2-11-2-6-3z" fill="#CDA892"/>
<path transform="translate(1426,735)" d="m0 0 2 1-5 2-2 4-3 2-4-1 4-2v-2z" fill="#C6A38E"/>
<path transform="translate(1350,562)" d="m0 0m-6 1h6v2l-9 3h-5l1-3z" fill="#301513"/>
<path transform="translate(1400,538)" d="m0 0 2 1-10 6h-3v2l-4-1h2v-2l5-1v-2z" fill="#E2CDBF"/>
<path transform="translate(1503,509)" d="m0 0 6 2 2 1-1 2-4-2-4 1-1 5-4-3v-2h3l1-3z" fill="#67605D"/>
<path transform="translate(878,359)" d="m0 0v3l-7 7-2-1 3-6 2-2z" fill="#453130"/>
<path transform="translate(1865,1407)" d="m0 0h1l3 17-1 3-2-5-2-8z" fill="#786058"/>
<path transform="translate(894,1311)" d="m0 0h2l6 14v2h-2l-6-14z" fill="#917265"/>
<path transform="translate(1202,1143)" d="m0 0 6 1v2l7 3-1 3-2-1-3-2-6-3z" fill="#959795"/>
<path transform="translate(1416 1e3)" d="m0 0 11 3 3 3-5 1-9-6z" fill="#88665A"/>
<path transform="translate(192,972)" d="m0 0 9 6 5 5-5-1v-2l-5-1-4-5z" fill="#7A5146"/>
<path transform="translate(1700,935)" d="m0 0m-1 1m-1 1m-1 1 2 1-2 4-4 3-5 1 5-5z" fill="#623E38"/>
<path transform="translate(1068,861)" d="m0 0h5l5 8-1 4-2-4-5-5z" fill="#FDF3E3"/>
<path transform="translate(484,822)" d="m0 0 3 1 5 10v4h-2l-4-10z" fill="#8F6456"/>
<path transform="translate(1840,789)" d="m0 0h3v2l-11 8-2 1 2-4 5-5z" fill="#704B42"/>
<path transform="translate(536,768)" d="m0 0h6l-2 2-12 4-4-1v-1l10-3z" fill="#543B38"/>
<path transform="translate(1174,761)" d="m0 0 3 1-4 3-5 2-5-1v-2l9-2z" fill="#EDDAC9"/>
<path transform="translate(574,752)" d="m0 0 2 1-4 4-7 3h-5l4-3z" fill="#4E3938"/>
<path transform="translate(607,738)" d="m0 0 3 2-11 6-4-1 5-3 6-3z" fill="#87594B"/>
<path transform="translate(807,653)" d="m0 0h11l-3 2-3 1h-11l3-2z" fill="#999995"/>
<path transform="translate(377,650)" d="m0 0 4 2 3 5h-2l1 6h-2l-2-7z" fill="#39201E"/>
<path transform="translate(1385,632)" d="m0 0h8l-5 4h-10l4-3z" fill="#452E2B"/>
<path transform="translate(1385,630)" d="m0 0h8l-4 2-11 4-4 1 1-2h2v-2z" fill="#979895"/>
<path transform="translate(1173,590)" d="m0 0m-4 1h4l-1 3-13 2 1-3z" fill="#BEBEB8"/>
<path transform="translate(1507,499)" d="m0 0h2l-1 3-3 2h-3v2l-4 2-4-1 8-5z" fill="#8A8A86"/>
<path transform="translate(1820,363)" d="m0 0h3l-2 5-4 8h-1v-6z" fill="#7E5D52"/>
<path transform="translate(101,320)" d="m0 0 3 4 2 8-3 4-2-11z" fill="#613E38"/>
<path transform="translate(871,1381)" d="m0 0 3 1-8 11v-3-3z" fill="#B3BEBE"/>
<path transform="translate(549,1229)" d="m0 0h10l-2 4-9-1z" fill="#9AAFAE"/>
<path transform="translate(1252,1163)" d="m0 0 10 2 6 1 1 3-16-4z" fill="#A5AFAD"/>
<path transform="translate(157,1128)" d="m0 0 3 4 4 8-1 2-5-5-2-4z" fill="#CBD7DE"/>
<path transform="translate(1425,967)" d="m0 0h7v1l-9 3h-10l4-2z" fill="#351F1E"/>
<path transform="translate(1119,941)" d="m0 0 2 1v2l4 2-4 2-5-2v-3l3 1z" fill="#7E483B"/>
<path transform="translate(1111,917)" d="m0 0h2l4 5 3 3 4 6-4-2-8-9z" fill="#BA9F8E"/>
<path transform="translate(338,862)" d="m0 0 5 5 1 3 4 2v2l-5-2-5-6z" fill="#53342F"/>
<path transform="translate(1164,847)" d="m0 0 2 1 4 9-2 4-2-3-2-6z" fill="#372120"/>
<path transform="translate(1031,747)" d="m0 0 7 2 9 4v1h-6l-10-5z" fill="#FCF4E6"/>
<path transform="translate(423,736)" d="m0 0h2v2l5 2 4 5-1 2-9-8z" fill="#DEBFA8"/>
<path transform="translate(409,729)" d="m0 0 3 1 5 6 1 4-4-1-3-5v-3h-2z" fill="#2F1A19"/>
<path transform="translate(1385,640)" d="m0 0h5l-3 2-11 4h-3l1-3z" fill="#87594C"/>
<path transform="translate(1976,579)" d="m0 0h2l-1 4-5 6h-3v-2h2l1-4z" fill="#FAE6D1"/>
<path transform="translate(1286,575)" d="m0 0h8l-1 2-11 2h-4v-2z" fill="#A68170"/>
<path transform="translate(1377,557)" d="m0 0h3v2l2 1-7 3h-4l2-4z" fill="#36201E"/>
<path transform="translate(1680,510)" d="m0 0 1 2 6 1-4 3-6 2v-6h2z" fill="#706C68"/>
<path transform="translate(295,480)" d="m0 0 5 2 5 3-1 2-5-1-5-5z" fill="#F7E3CD"/>
<path transform="translate(291,464)" d="m0 0 5 1 7 3 4 3-7-1-9-5z" fill="#C4A997"/>
<path transform="translate(1799,403)" d="m0 0h2l-1 4-2 1-3 7-3 3 2-7 4-7z" fill="#825E53"/>
<path transform="translate(540,1607)" d="m0 0 2 1-6 8-5 1 5-7z" fill="#6D473F"/>
<path transform="translate(576,1584)" d="m0 0h2l-2 4-5 4-6 1 4-4 3-1z" fill="#F0DAC8"/>
<path transform="translate(518,1210)" d="m0 0h5l-1 3 10 2-4 1-14-4z" fill="#423534"/>
<path transform="translate(394,1164)" d="m0 0 5 1 12 5-2 2-15-7z" fill="#553B38"/>
<path transform="translate(210,1075)" d="m0 0 3 2v2h2l4 10v3l-5-8-4-7z" fill="#BE9883"/>
<path transform="translate(201,1042)" d="m0 0h2l3 9h2l2 5h-3l-6-11z" fill="#8B5F52"/>
<path transform="translate(1122,926)" d="m0 0 4 2 11 6v1l-7-1-8-7z" fill="#806F67"/>
<path transform="translate(1059,852)" d="m0 0 3 1v3h2v4l-4 1z" fill="#FDF3E3"/>
<path transform="translate(1074,841)" d="m0 0 3 4 5 9-1 2-3-3-4-7z" fill="#9A9D9A"/>
<path transform="translate(1300,811)" d="m0 0h5l-1 3-12 1 2-1v-2z" fill="#623C35"/>
<path transform="translate(1380,767)" d="m0 0v3l-7 10-1-3 2-4z" fill="#DEBFA8"/>
<path transform="translate(441,766)" d="m0 0 4 2 10 10-1 2-9-8z" fill="#563B38"/>
<path transform="translate(430,756)" d="m0 0h2l8 11-1 4-4-6-5-7z" fill="#82584C"/>
<path transform="translate(262,762)" d="m0 0 5 2 2 3h-2l3 4-1 2-6-7z" fill="#937265"/>
<path transform="translate(1446,735)" d="m0 0 3 1-4 2 5 1-2 2h-6l-2-3 2-2z" fill="#D4B29B"/>
<path transform="translate(390,682)" d="m0 0h2l1 2 1 11 2 5-1 3-3-7z" fill="#BD9782"/>
<path transform="translate(1015,631)" d="m0 0h9v1l-8 2h-10v-2z" fill="#A4A9A7"/>
<path transform="translate(1212,605)" d="m0 0h11v2h-7l-3 1-3-1v2h-3v-3z" fill="#B0BABB"/>
<path transform="translate(1502,600)" d="m0 0 7 1v1l-9 2h-9l4-2z" fill="#825649"/>
<path transform="translate(1110,1591)" d="m0 0h2l1 7-1 2h-2l-2-6z" fill="#140A0A"/>
<path transform="translate(1375,1551)" d="m0 0h6l-1 3 6 1-2 2-12-4z" fill="#5C5656"/>
<path transform="translate(791,1470)" d="m0 0 2 1-2 4h-2v2l-5 3-3 2 2-4z" fill="#613F39"/>
<path transform="translate(835,1437)" d="m0 0h4l-1 3-4 2-2 4-1-3-2-1z" fill="#6B514B"/>
<path transform="translate(1470,1264)" d="m0 0 1 2-4 8-4 2 2-5 3-6z" fill="#9AA19F"/>
<path transform="translate(548,1232)" d="m0 0h9l2 1v2l-5 1-5-1z" fill="#919896"/>
<path transform="translate(209,1059)" d="m0 0 7 6 7 4-4 1-9-7z" fill="#301513"/>
<path transform="translate(248,1012)" d="m0 0 12 3v2l-8-1-7-2z" fill="#895C4F"/>
<path transform="translate(1111,907)" d="m0 0h4v2h3l1 5-5-1v-2h-2z" fill="#392423"/>
<path transform="translate(1024,804)" d="m0 0 2 2 3 11-1 4-5-15z" fill="#DEBFA8"/>
<path transform="translate(1359,770)" d="m0 0h2v2l-6 5-5 3-4 2 5-6z" fill="#896053"/>
<path transform="translate(469,765)" d="m0 0h1l-1 8-3 3-4 1-1-6 1 3 5-3z" fill="#351F1E"/>
<path transform="translate(1433,721)" d="m0 0h5v4h3l-1 3-5 2h-3l3-3 1-5z" fill="#653F38"/>
<path transform="translate(373,650)" d="m0 0 6 8v2h2l1 5h-2l-2-6-3-1-2-4z" fill="#C39F8A"/>
<path transform="translate(1442,623)" d="m0 0h7l-3 2-7 3h-6l4-3z" fill="#B5917E"/>
<path transform="translate(1450,611)" d="m0 0 3 1-5 3-7 2h-5l3-2 6-1v-2z" fill="#826055"/>
<path transform="translate(1503,559)" d="m0 0 1 3-3 12-3-1 3-9z" fill="#A6ADAC"/>
<path transform="translate(1408,542)" d="m0 0h5l-2 1-1 3-11 2 3-3z" fill="#341E1D"/>
<path transform="translate(768,451)" d="m0 0 2 3h-2l-1 3h-2v2l-3 1 1-5z" fill="#563B38"/>
<path transform="translate(224,430)" d="m0 0 5 2 9 4v2l2 1-5-1-11-7z" fill="#77716C"/>
<path transform="translate(110,363)" d="m0 0h3v2h2l1-2 3 4v3l-6-2z" fill="#160A0A"/>
<path transform="translate(1509,77)" d="m0 0 9 2 5 2-1 2-11-3-2-1z" fill="#9BBCBD"/>
<path transform="translate(1897,1589)" d="m0 0h2l1 9-3 3-1-10z" fill="#433738"/>
<path transform="translate(808,1503)" d="m0 0 2 2-1 5h-2l-1 2h-3l2-5z" fill="#301513"/>
<path transform="translate(843,1440)" d="m0 0 2 1-2 5-4 7-1-3z" fill="#433738"/>
<path transform="translate(892,1326)" d="m0 0 1 2 3 1 3 7v5l-2-2-5-10z" fill="#5B5453"/>
<path transform="translate(1459,1293)" d="m0 0 1 2-5 8-4 1 2-5 5-5z" fill="#5E4642"/>
<path transform="translate(857,1226)" d="m0 0 2 1v10l-4-1z" fill="#A8B1B0"/>
<path transform="translate(1272,1170)" d="m0 0 9 1 5 2v1h-8l-7-2z" fill="#ADB8B7"/>
<path transform="translate(1163,1127)" d="m0 0 4 1 9 6-3 2-9-7z" fill="#9BA09E"/>
<path transform="translate(1470,1032)" d="m0 0h6l2 2-3 2h2v2h-4v-2l-2-1z" fill="#341816"/>
<path transform="translate(1635,997)" d="m0 0 2 1-2 5-5 1-4 3 2-5z" fill="#453939"/>
<path transform="translate(96,994)" d="m0 0 4 2 4 6v2l-4-2-4-5z" fill="#503A38"/>
<path transform="translate(1670,957)" d="m0 0 2 1-1 3-8 7-4 2 6-8z" fill="#824F41"/>
<path transform="translate(1083,878)" d="m0 0 3 3 2 5h2v6l-4-4z" fill="#846157"/>
<path transform="translate(1160,827)" d="m0 0h3v8h-1l-1 8h-1z" fill="#7B493D"/>
<path transform="translate(343,821)" d="m0 0 6 5-1 2-3-2 1 3-4-1-1-4z" fill="#473737"/>
<path transform="translate(1296,687)" d="m0 0 1 3-5 5h-2v2l-2-1 1-4z" fill="#331A19"/>
<path transform="translate(387,657)" d="m0 0h2l5 10-1 3-2-2-4-8z" fill="#AB8A78"/>
<path transform="translate(437,551)" d="m0 0h3v2l4 1 7 5-2 1-7-4z" fill="#5A4C4A"/>
<path transform="translate(877,356)" d="m0 0 2 1-13 11-2-1 11-10z" fill="#E8ECED"/>
<path transform="translate(1495,72)" d="m0 0 9 2 5 2v2l-6-1-8-3z" fill="#9CC1C4"/>
<path transform="translate(1902,1825)" d="m0 0h2v5l-4 3h-4l1-3v2l4-1-1-5z" fill="#979E9C"/>
<path transform="translate(557,1598)" d="m0 0h2l-1 3-4 3-7 1 4-4z" fill="#744E44"/>
<path transform="translate(562,1598)" d="m0 0 2 1-1 2h-3v2l-6 3 1-4z" fill="#351F1E"/>
<path transform="translate(1108,1591)" d="m0 0 1 3 1 5h-1l-1 6-2-4v-8z" fill="#311716"/>
<path transform="translate(572,1586)" d="m0 0v3l-6 3-6 4-2-1 5-4z" fill="#F7F8F9"/>
<path transform="translate(896,1329)" d="m0 0h2l1 4h2l2 5-1 3-2-5h-2l-2-4z" fill="#3F3131"/>
<path transform="translate(835,1127)" d="m0 0h1l2 11v4h-3z" fill="#8A8D8B"/>
<path transform="translate(132,1048)" d="m0 0h3l5 10-1 2-7-10z" fill="#311715"/>
<path transform="translate(1393,980)" d="m0 0h7l10 6-2 1-8-4-7-2z" fill="#855649"/>
<path transform="translate(1333,946)" d="m0 0 4 1 1 3-8 1 1-3-2-1z" fill="#3F2421"/>
<path transform="translate(1691,945)" d="m0 0 2 1-7 8-4 1 6-7z" fill="#734338"/>
<path transform="translate(1208,939)" d="m0 0 4 4 3 7-5-2-2-6z" fill="#321918"/>
<path transform="translate(146,927)" d="m0 0 5 5 3 5-1 4-7-12z" fill="#7C5247"/>
<path transform="translate(1463,918)" d="m0 0 3 1-5 3-10 2-3-2 14-3z" fill="#C5A28D"/>
<path transform="translate(366,884)" d="m0 0h3l-2 4-2 1-1 7-2-3 1-6z" fill="#CFAC96"/>
<path transform="translate(376,880)" d="m0 0 4 2 3 6-4-2v-2l-9-1 3-2z" fill="#DEBFA8"/>
<path transform="translate(1311,808)" d="m0 0 4 1 4 2-14 1 3-3z" fill="#351F1E"/>
<path transform="translate(465,750)" d="m0 0 1 2-4 10-1 6h-1v-9z" fill="#A98574"/>
<path transform="translate(1467,731)" d="m0 0h5l-3 2-9 3-5 1 2-1v-2z" fill="#B28D7B"/>
<path transform="translate(1422,731)" d="m0 0 7 1-4 3-6 2 1-4z" fill="#351F1E"/>
<path transform="translate(1337,656)" d="m0 0m-1 1m-1 1 1 3 2 1-10 3 1-3h2v-2z" fill="#351F1E"/>
<path transform="translate(588,499)" d="m0 0 2 1-2 11h-1l-1-7-1-3z" fill="#9EA09D"/>
<path transform="translate(1541,482)" d="m0 0m-1 1m-2 1h2v2l-10 6-2-1 6-5z" fill="#DEBFA8"/>
<path transform="translate(200,426)" d="m0 0 6 2 7 4-1 2-12-6z" fill="#F5E0CB"/>
<path transform="translate(1613,402)" d="m0 0 2 1-4 5-5 3h-3l7-7z" fill="#574B49"/>
<path transform="translate(862,367)" d="m0 0 4 2-8 6-1-3z" fill="#B1BABA"/>
<path transform="translate(215,140)" d="m0 0 2 3-11 5v-3z" fill="#A9C7CB"/>
<path transform="translate(1786,1873)" d="m0 0 4 1-12 5-1-3z" fill="#B1CDD2"/>
<path transform="translate(1428,1547)" d="m0 0m-6 1h6l-1 3h-10l1-2z" fill="#4C4242"/>
<path transform="translate(730,1517)" d="m0 0 4 1h-2v2l-6 4-2-1-1-2z" fill="#5C4744"/>
<path transform="translate(1073,1517)" d="m0 0h5l7 7h-3l-2-1v-2l-5-1v-2z" fill="#929694"/>
<path transform="translate(829,1464)" d="m0 0 1 4-5 5-2-1v-2l5-5z" fill="#37211F"/>
<path transform="translate(845,1425)" d="m0 0h3l-1 5h-2l-1 3-2-3 2-4z" fill="#77554C"/>
<path transform="translate(858,1403)" d="m0 0v3l-3 1-2 4-7 4 2-4 4-3h2v-2z" fill="#8F8680"/>
<path transform="translate(1862,1389)" d="m0 0h1l2 16-3-2z" fill="#75605A"/>
<path transform="translate(1804,968)" d="m0 0 2 4 2 10h-2l-3-11z" fill="#AB8876"/>
<path transform="translate(312,973)" d="m0 0 4 2 2 2-9 9 1-5 3-3h2z" fill="#653F38"/>
<path transform="translate(1680,949)" d="m0 0m-1 1m-1 1 2 2-6 6-3-1 5-5z" fill="#77483D"/>
<path transform="translate(159,946)" d="m0 0 5 2 3 8-4-2-4-6z" fill="#D1AF98"/>
<path transform="translate(248,910)" d="m0 0 5 4 1 2v6l-2-1-4-8z" fill="#351F1E"/>
<path transform="translate(394,895)" d="m0 0 5 1 6 6v2l-4-2-7-6z" fill="#84574A"/>
<path transform="translate(328,846)" d="m0 0 4 5 4 6v2l-4-2-4-7z" fill="#462C2A"/>
<path transform="translate(357,846)" d="m0 0 7 2 3 4-1 3-1-3h-2v-2l-6-2z" fill="#341B19"/>
<path transform="translate(360,840)" d="m0 0 4 2 8 8-1 2-10-9z" fill="#553834"/>
<path transform="translate(292,791)" d="m0 0 8 1v9l-2-4-6-5z" fill="#5F3D38"/>
<path transform="translate(481,748)" d="m0 0 1 3-4 5-6 6 1-6 5-3 1-3h2z" fill="#5C4C4A"/>
<path transform="translate(1934,651)" d="m0 0 1 3-5 11h-1v-6z" fill="#563A34"/>
<path transform="translate(379,643)" d="m0 0 7 6 1 6-4-4-4-6z" fill="#D4B29C"/>
<path transform="translate(1457,611)" d="m0 0h2l-1 3-7 2h-6l3-2z" fill="#351F1E"/>
<path transform="translate(1404,546)" d="m0 0h9l-4 3-6 1v-3z" fill="#402F2E"/>
<path transform="translate(1508,505)" d="m0 0 4 1 2 9-4-5-2-1v-2l-2-1z" fill="#D9BEAA"/>
<path transform="translate(831,403)" d="m0 0m-1 1m-1 1m-1 1m-1 1m-2 1 2 1-2 2 1 2-5 4h-2l2-4z" fill="#514544"/>
<path transform="translate(908,331)" d="m0 0 2 1-7 8-4-1 4-2v-2z" fill="#5D4E4B"/>
<path transform="translate(1402,1687)" d="m0 0h6l-3 2-7 2-4-1h2v-2z" fill="#877B77"/>
<path transform="translate(527,1619)" d="m0 0h5l-5 4-5 1v-3z" fill="#3C2423"/>
<path transform="translate(592,1579)" d="m0 0h2v2l-9 5-4-1z" fill="#8C6456"/>
<path transform="translate(776,1559)" d="m0 0 2 1-3 5h-2l-1 5-1-4 1-4 4-1z" fill="#443332"/>
<path transform="translate(826,1438)" d="m0 0 2 1-2 4-5 3-3 3-3-1 9-7z" fill="#8C7165"/>
<path transform="translate(1853,1384)" d="m0 0 3 1v8l-2 2-1-4z" fill="#261514"/>
<path transform="translate(925,1376)" d="m0 0h2v2h2l3 6-1 2-4-4-2-3z" fill="#79564C"/>
<path transform="translate(646,1245)" d="m0 0 9 1 7 3-3 1-12-3z" fill="#878C89"/>
<path transform="translate(515,1237)" d="m0 0 7 1 3 4-7-1z" fill="#9EA09D"/>
<path transform="translate(1500,1191)" d="m0 0 1 2-3 9h-2v-9z" fill="#B4C1C3"/>
<path transform="translate(224,1097)" d="m0 0 3 3v2h2l3 6-1 2-3-3-4-8z" fill="#7F5348"/>
<path transform="translate(230,1083)" d="m0 0 7 1v2l-5-1v6l-2-2-1-5z" fill="#5A3C38"/>
<path transform="translate(1446,1022)" d="m0 0 6 1v2l3 1-1 2-5-2-3-3z" fill="#4A3736"/>
<path transform="translate(239,1006)" d="m0 0 5 1 7 4v1h-5l-7-5z" fill="#351F1E"/>
<path transform="translate(1621,995)" d="m0 0 2 1-2 1zm-2 2h2v3l-8 4 3-6z" fill="#7D4E42"/>
<path transform="translate(1430,991)" d="m0 0 4 1 6 2v2l-7-1-5-1z" fill="#482E2A"/>
<path transform="translate(1412,975)" d="m0 0 2 1-2 2-1 5-2-1 1-4-6 1 1-3z" fill="#3B2322"/>
<path transform="translate(183,968)" d="m0 0 5 3 4 1-1 2-2 3-4-4z" fill="#483838"/>
<path transform="translate(1434,960)" d="m0 0h15v1l-11 2h-5z" fill="#CDA993"/>
<path transform="translate(424,913)" d="m0 0 7 2 8 1-3 2-12-2z" fill="#855A4D"/>
<path transform="translate(456,897)" d="m0 0v3l-7 6-4-1z" fill="#7B4E42"/>
<path transform="translate(353,893)" d="m0 0 5 5 5 6h-3l-5-6-2-1z" fill="#83584C"/>
<path transform="translate(1234,835)" d="m0 0 2 1-2 5-6 4 2-5 2-4z" fill="#55312A"/>
<path transform="translate(467,798)" d="m0 0 5 5 3 5-1 2-4-4-3-5z" fill="#301513"/>
<path transform="translate(1354,789)" d="m0 0 2 1-4 5-7 2 5-5z" fill="#5B3C38"/>
<path transform="translate(1328,791)" d="m0 0 4 1-1 3h-2v2l-5-1 2-4z" fill="#C49D87"/>
<path transform="translate(1186,753)" d="m0 0v3l-2 4-7 2v-2h2v-2l6-4z" fill="#F2DAC4"/>
<path transform="translate(1426,725)" d="m0 0h7l-1 4h-5z" fill="#160A0A"/>
<path transform="translate(1432,722)" d="m0 0h4v5l-5 4 2-6-2-1z" fill="#301513"/>
<path transform="translate(712,665)" d="m0 0v3l-5 2-3 3-2-1 5-5z" fill="#9B9E9B"/>
<path transform="translate(1504,604)" d="m0 0h5l-3 2-8 3h-3v-2z" fill="#DEBFA8"/>
<path transform="translate(487,602)" d="m0 0 2 1v2h2l1 8h-2l-3-8z" fill="#392221"/>
<path transform="translate(2025,555)" d="m0 0 1 2-7 11h-2l2-4z" fill="#FFF2DE"/>
<path transform="translate(1368,561)" d="m0 0h3l1 3-9 3 3-5z" fill="#4C3A38"/>
<path transform="translate(2047,529)" d="m0 0 1 3-8 7-2 1 2-5z" fill="#E9D3C4"/>
<path transform="translate(1726,492)" d="m0 0 2 1-3 3h-2v2l-9 2 5-4z" fill="#775349"/>
<path transform="translate(193,413)" d="m0 0 5 2 4 4-2 1-9-5z" fill="#775147"/>
<path transform="translate(189,416)" d="m0 0h3l5 5-1 2-9-5z" fill="#533631"/>
<path transform="translate(843,384)" d="m0 0h2v2l-7 6-5 2 5-6z" fill="#DFE6E7"/>
<path transform="translate(981,262)" d="m0 0 2 1-6 7-5 4-2-1z" fill="#989C99"/>
</svg>

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
    position: relative; /* Mengubah menjadi relative */
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

