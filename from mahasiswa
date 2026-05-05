<!DOCTYPE html>
<html lang="id">    
<head>
    <meta charset="UTF-8"> <!-- Mengatur karakter encoding agar mendukung simbol universal -->
    <title>Form Mahasiswa</title>

    <style>
        body {
            font-family: 'Segoe UI', sans-serif; /* Mengatur jenis huruf */
            margin: 0; /* Menghilangkan margin bawaan browser */
            min-height: 100vh; /* Memastikan tinggi body minimal seukuran layar */
            background: linear-gradient(135deg, #00c6ff, #0072ff); /* Latar belakang gradasi biru */
            display: flex; /* Mengaktifkan mode flexbox */
            flex-direction: column; /* Mengatur arah konten secara vertikal */
            align-items: center; /* Mengatur konten agar rata tengah secara horizontal */
        }

        h2 {
            text-align: center; /* Teks judul di tengah */
            color: white; /* Warna teks putih */
            margin-top: 20px; /* Jarak atas judul */
        }

        form {
            width: 600px; /* Lebar formulir */
            background: linear-gradient(135deg, #ff00cc, #4a00e0); /* Latar gradasi ungu-pink */
            padding: 20px; /* Jarak dalam formulir */
            border-radius: 15px; /* Sudut formulir melengkung */
            margin-top: 10px; /* Jarak atas formulir */
            box-shadow: 0 10px 25px rgba(0,0,0,0.3); /* Memberikan efek bayangan */
            color: white; /* Warna teks di dalam form */

            display: grid; /* Mengaktifkan mode grid */
            grid-template-columns: 1fr 1fr; /* Membagi form menjadi 2 kolom sama besar */
            gap: 10px; /* Jarak antar elemen di dalam grid */
        }

        textarea {
            grid-column: span 2; /* Membuat kotak alamat memenuhi 2 kolom */
        }

        .jk-container {
            grid-column: span 2; /* Membuat wadah Jenis Kelamin memenuhi 2 kolom */
            display: flex; /* Menyusun pilihan radio button secara menyamping */
            gap: 20px; /* Jarak antar pilihan Pria dan Wanita */
        }

        button {
            padding: 10px; /* Ukuran dalam tombol */
            border: none; /* Menghapus garis tepi tombol */
            border-radius: 8px; /* Sudut tombol melengkung */
            cursor: pointer; /* Mengubah kursor jadi tangan saat diarahkan ke tombol */
            font-weight: bold; /* Menebalkan teks tombol */
        }

        .submit { background: #00ffcc; color: black; } /* Warna tombol submit hijau toska */
        .reset { background: #222; color: white; } /* Warna tombol reset hitam */

        form button {
            width: 100%; /* Membuat tombol memenuhi lebar kolom grid */
        }

        table {
            width: 90%; /* Lebar tabel */
            margin-top: 20px; /* Jarak atas tabel */
            border-collapse: collapse; /* Menghilangkan celah antar garis tabel */
            background: rgba(255,255,255,0.15); /* Warna transparan putih */
            backdrop-filter: blur(10px); /* Efek blur di belakang tabel (glassmorphism) */
            border-radius: 10px; /* Sudut tabel melengkung */
            overflow: hidden; /* Memastikan sudut melengkung memotong isi tabel */
            color: white; /* Warna teks tabel */
        }

        th, td {
            padding: 10px; /* Jarak dalam sel tabel */
            text-align: center; /* Teks tabel rata tengah */
        }
    </style>
</head>

<body>

<h2>Form Data Mahasiswa</h2>

<!-- Formulir Input -->
<form id="formMahasiswa">
    <label>NIM</label>
    <input type="text" id="nim" required> <!-- Input teks untuk NIM -->

    <label>Nama</label>
    <input type="text" id="nama" required> <!-- Input teks untuk Nama -->

    <label>Alamat</label>
    <textarea id="alamat"></textarea> <!-- Area teks panjang untuk Alamat -->

    <label>Jenis Kelamin</label>
    <div class="jk-container">
        <label><input type="radio" name="jk" value="Pria"> Pria</label> <!-- Pilihan Pria -->
        <label><input type="radio" name="jk" value="Wanita"> Wanita</label> <!-- Pilihan Wanita -->
    </div>

    <label>Tanggal Lahir</label>
    <select id="tanggal"></select> <!-- Dropdown tanggal (diisi oleh JS) -->

    <select id="bulan"> <!-- Dropdown bulan manual -->
        <option value="01">Januari</option>
        <option value="02">Februari</option>
        <option value="03">Maret</option>
        <option value="04">April</option>
        <option value="05">Mei</option>
        <option value="06">Juni</option>
        <option value="07">Juli</option>
        <option value="08">Agustus</option>
        <option value="09">September</option>
        <option value="10">Oktober</option>
        <option value="11">November</option>
        <option value="12">Desember</option>
    </select>

    <select id="tahun"></select> <!-- Dropdown tahun (diisi oleh JS) -->

    <label>Password</label>
    <input type="password" id="password" required> <!-- Input tersembunyi untuk password -->

    <button type="submit" class="submit">Submit</button> <!-- Tombol kirim data -->
    <button type="reset" class="reset">Reset</button> <!-- Tombol kosongkan form -->
</form>

<h2>Data Mahasiswa</h2>

<!-- Tabel Tampilan -->
<table>
    <thead>
        <tr>
            <th>NIM</th>
            <th>Nama</th>
            <th>Alamat</th>
            <th>JK</th>
            <th>TTL</th>
            <th>Password</th>
            <th>Aksi</th>
        </tr>
    </thead>
    <tbody id="tableBody"></tbody> <!-- Tempat baris data baru ditambahkan -->
</table>

<script>
// Loop untuk membuat angka 1 sampai 31 di dropdown tanggal
for (let i = 1; i <= 31; i++) {
    let opt = document.createElement("option"); // Buat elemen option baru
    opt.value = i; // Atur nilai option
    opt.text = i; // Atur teks yang muncul
    document.getElementById("tanggal").appendChild(opt); // Masukkan ke dalam select tanggal
}

// Mengambil tahun saat ini secara otomatis dari sistem
let tahunSekarang = new Date().getFullYear();
// Loop untuk mengisi dropdown tahun dari 1990 sampai tahun sekarang
for (let i = 1990; i <= tahunSekarang; i++) {
    let opt = document.createElement("option"); // Buat elemen option baru
    opt.value = i; // Atur nilai tahun
    opt.text = i; // Atur teks tahun
    document.getElementById("tahun").appendChild(opt); // Masukkan ke dalam select tahun
}

// Fungsi utama saat form dikirim (tombol submit ditekan)
document.getElementById("formMahasiswa").addEventListener("submit", function(e){
    e.preventDefault(); // Menghentikan perilaku default browser (agar tidak reload halaman)

    // Mengambil semua nilai dari kotak input
    let nim = document.getElementById("nim").value.trim(); // Ambil NIM
    let nama = document.getElementById("nama").value.trim(); // Ambil Nama
    let alamat = document.getElementById("alamat").value.trim(); // Ambil Alamat
    let password = document.getElementById("password").value; // Ambil Password asli

    // Mencari input jenis kelamin yang sedang dicentang (checked)
    let jkInput = document.querySelector('input[name="jk"]:checked');
    if (!jkInput) {
        alert("Pilih jenis kelamin!"); // Peringatan jika belum pilih JK
        return; // Hentikan fungsi
    }
    let jk = jkInput.value; // Simpan nilai Pria atau Wanita

    // Menggabungkan pilihan tanggal, bulan, dan tahun menjadi satu teks
    let ttl = document.getElementById("tanggal").value + "-" +
              document.getElementById("bulan").value + "-" +
              document.getElementById("tahun").value;

    // Membuat teks samaran untuk kolom password di tabel
    let hiddenPass = "**";

    // Menyusun baris tabel (HTML) dengan data yang sudah diambil
    let row = `
        <tr>
            <td>${nim}</td>
            <td>${nama}</td>
            <td>${alamat}</td>
            <td>${jk}</td>
            <td>${ttl}</td>
            <td>${hiddenPass}</td>
            <td><button onclick="hapus(this)">Hapus</button></td> <!-- Tombol hapus spesifik baris ini -->
        </tr>
    `;

    // Memasukkan baris HTML baru ke dalam tabel body di posisi paling bawah
    document.getElementById("tableBody").insertAdjacentHTML("beforeend", row);

    // Mengosongkan kembali seluruh isi formulir setelah berhasil
    document.getElementById("formMahasiswa").reset();
});

// Fungsi untuk menghapus baris tabel
function hapus(btn){
    // btn (tombol) -> parentnya (td) -> parentnya lagi (tr) -> hapus elemen tr tersebut
    btn.parentElement.parentElement.remove();
}
</script>

</body>
</html>
