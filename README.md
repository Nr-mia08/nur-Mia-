# nur-Mia-<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Saran Motivasi Hari Ini</title>
    <style>
        /* --- RESET & BASE STYLES --- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f0fdf4; /* Hijau sangat muda (mint segar) */
            color: #166534; /* Hijau tua untuk teks */
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden; /* Mencegah scrollbar muncul saat tombol lari */
        }

        /* --- CARD CONTAINER --- */
        .card {
            background-color: #ffffff; /* Putih bersih */
            padding: 2.5rem;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(22, 101, 52, 0.1);
            text-align: center;
            max-width: 450px;
            width: 90%;
            border: 2px solid #bbf7d0;
            position: relative;
            transition: all 0.3s ease;
        }

        /* --- STICKERS / EMOJIS --- */
        .sticker-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 1.5rem;
        }

        .sticker {
            font-size: 3rem;
            animation: float 3s ease-in-out infinite;
        }

        .sticker:nth-child(2) {
            animation-delay: 0.5s;
        }

        .sticker:nth-child(3) {
            animation-delay: 1s;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        /* --- TYPOGRAPHY --- */
        h1 {
            font-size: 1.8rem;
            margin-bottom: 1rem;
            color: #15803d;
        }

        p {
            font-size: 1.1rem;
            line-height: 1.6;
            margin-bottom: 2rem;
            color: #4b5563;
        }

        #quote-display {
            font-weight: 600;
            color: #16a34a;
            min-height: 50px;
        }

        /* --- BUTTONS --- */
        .btn-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            min-height: 50px;
            align-items: center;
        }

        .btn {
            padding: 0.8rem 2rem;
            font-size: 1rem;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        .btn:active {
            transform: scale(0.95);
        }

        #btn-oke {
            background-color: #16a34a; /* Hijau utama */
            color: white;
            box-shadow: 0 4px 12px rgba(22, 163, 74, 0.3);
        }

        #btn-oke:hover {
            background-color: #15803d;
        }

        #btn-tidak {
            background-color: #f3f4f6; /* Abu-abu putih netral */
            color: #4b5563;
            border: 1px solid #d1d5db;
            position: relative; /* Penting untuk pergerakan JavaScript */
            z-index: 10;
        }
    </style>
</head>
<body>

    <div class="card">
        <!-- Area Stiker Motivasi -->
        <div class="sticker-container">
            <span class="sticker">🌱</span>
            <span class="sticker">✨</span>
            <span class="sticker">💪</span>
        </div>

        <h1 id="title">Halo, Teman! 👋</h1>
        <p id="quote-display">Apakah kamu siap menerima saran motivasi terbaik untuk hari yang luar biasa ini?</p>

        <div class="btn-container">
            <button class="btn" id="btn-oke">Oke!</button>
            <button class="btn" id="btn-tidak">Tidak</button>
        </div>
    </div>

    <script>
        const btnOke = document.getElementById('btn-oke');
        const btnTidak = document.getElementById('btn-tidak');
        const quoteDisplay = document.getElementById('quote-display');
        const titleText = document.getElementById('title');

        // Kumpulan pesan motivasi positif
        const motivasiQuotes = [
            "Kemajuan sekecil apa pun tetaplah kemajuan. Kamu sudah melangkah, banggalah pada dirimu! 🌟",
            "Jangan membandingkan bab pertama hidupmu dengan bab ke-20 hidup orang lain. Fokus pada ceritamu! ✨",
            "Satu-satunya batasan untuk meraih hari esok adalah keraguan kita hari ini. Kamu pasti bisa! 🚀",
            "Ingat, badai pasti berlalu dan setelah itu pelangi yang indah akan muncul. Tetap bertahan, ya! 🌱",
            "Kamu lebih kuat dari yang kamu pikirkan, dan kamu berhak mendapatkan hal-hal baik di dunia ini. 💪"
        ];

        // Fungsi saat tombol "Tidak" disentuh atau didekati (untuk PC & HP)
        function lariDariKenyataan() {
            // Menghitung batas aman agar tombol tidak lari keluar layar browser
            const padding Lari = 100;
            const x acak = Math.random() * (window.innerWidth - paddingLari);
            const y acak = Math.random() * (window.innerHeight - paddingLari);

            // Mengubah posisi tombol menjadi absolut agar bisa berpindah bebas
            btnTidak.style.position = 'fixed';
            btnTidak.style.left = x acak + 'px';
            btnTidak.style.top = y acak + 'px';
        }

        // Efek menghindar saat mouse mendekat (PC) atau disentuh (HP)
        btnTidak.addEventListener('mouseover', lariDariKenyataan);
        btnTidak.addEventListener('touchstart', (e) => {
            e.preventDefault(); // Mencegah klik tidak sengaja di HP
            lariDariKenyataan();
        });

        // Fungsi saat tombol "Oke" ditekan
        btnOke.addEventListener('click', () => {
            // Ambil kutipan acak dari array
            const indexAcak = Math.floor(Math.random() * motivasiQuotes.length);
            quoteDisplay.innerHTML = motivasiQuotes[indexAcak];
            
            // Ubah judul jadi lebih ramah
            titleText.innerText = "Pesan Untukmu: 🔥";

            // Kembalikan tombol 'Tidak' ke tempat semula jika sempat lari
            btnTidak.style.position = 'relative';
            btnTidak.style.left = 'auto';
            btnTidak.style.top = 'auto';
        });
    </script>

</body>
</html>
