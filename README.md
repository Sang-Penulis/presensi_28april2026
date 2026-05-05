<!DOCTYPE html>
<html lang="id">    
<head>
<meta charset="UTF-8">
<title>Form Mahasiswa</title>

<style>
body {
    font-family: 'Segoe UI', sans-serif;
    margin: 0;
    min-height: 100vh;
    background: linear-gradient(135deg, #00c6ff, #0072ff);
    display: flex;
    flex-direction: column;
    align-items: center;
}

h2 {
    text-align: center;
    color: white;
    margin-top: 20px;
}

form {
    width: 600px;
    background: linear-gradient(135deg, #ff00cc, #4a00e0);
    padding: 20px;
    border-radius: 15px;
    margin-top: 10px;
    box-shadow: 0 10px 25px rgba(0,0,0,0.3);
    color: white;

    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
}

textarea {
    grid-column: span 2;
}

.jk-container {
    grid-column: span 2;
    display: flex;
    gap: 20px;
}

button {
    padding: 10px;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-weight: bold;
}

.submit { background: #00ffcc; color: black; }
.reset { background: #222; color: white; }

form button {
    width: 100%;
}

table {
    width: 90%;
    margin-top: 20px;
    border-collapse: collapse;
    background: rgba(255,255,255,0.15);
    backdrop-filter: blur(10px);
    border-radius: 10px;
    overflow: hidden;
    color: white;
}

th, td {
    padding: 10px;
    text-align: center;
}
</style>

</head>

<body>

<h2>Form Data Mahasiswa</h2>

<form id="formMahasiswa">
    <label>NIM</label>
    <input type="text" id="nim" required>

    <label>Nama</label>
    <input type="text" id="nama" required>

    <label>Alamat</label>
    <textarea id="alamat"></textarea>

    <label>Jenis Kelamin</label>
    <div class="jk-container">
        <label><input type="radio" name="jk" value="Pria"> Pria</label>
        <label><input type="radio" name="jk" value="Wanita"> Wanita</label>
    </div>

    <label>Tanggal Lahir</label>
    <select id="tanggal"></select>

    <select id="bulan">
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

    <select id="tahun"></select>

    <label>Password</label>
    <input type="password" id="password" required>

    <button type="submit" class="submit">Submit</button>
    <button type="reset" class="reset">Reset</button>
</form>

<h2>Data Mahasiswa</h2>

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
    <tbody id="tableBody"></tbody>
</table>

<script>
// generate tanggal
for (let i = 1; i <= 31; i++) {
    let opt = document.createElement("option");
    opt.value = i;
    opt.text = i;
    document.getElementById("tanggal").appendChild(opt);
}

// generate tahun (DINAMIS)
let tahunSekarang = new Date().getFullYear();
for (let i = 1990; i <= tahunSekarang; i++) {
    let opt = document.createElement("option");
    opt.value = i;
    opt.text = i;
    document.getElementById("tahun").appendChild(opt);
}

// handle submit
document.getElementById("formMahasiswa").addEventListener("submit", function(e){
    e.preventDefault();

    let nim = document.getElementById("nim").value.trim();
    let nama = document.getElementById("nama").value.trim();
    let alamat = document.getElementById("alamat").value.trim();
    let password = document.getElementById("password").value;

    // VALIDASI JK
    let jkInput = document.querySelector('input[name="jk"]:checked');
    if (!jkInput) {
        alert("Pilih jenis kelamin!");
        return;
    }
    let jk = jkInput.value;

    let ttl = document.getElementById("tanggal").value + "-" +
              document.getElementById("bulan").value + "-" +
              document.getElementById("tahun").value;

    // SAMARKAN PASSWORD (FIXED)
    let hiddenPass = "******";

    let row = `
        <tr>
            <td>${nim}</td>
            <td>${nama}</td>
            <td>${alamat}</td>
            <td>${jk}</td>
            <td>${ttl}</td>
            <td>${hiddenPass}</td>
            <td><button onclick="hapus(this)">Hapus</button></td>
        </tr>
    `;

    // LEBIH AMAN
    document.getElementById("tableBody")
        .insertAdjacentHTML("beforeend", row);

    // RESET FORM
    document.getElementById("formMahasiswa").reset();
});

// hapus data
function hapus(btn){
    btn.parentElement.parentElement.remove();
}
</script>

</body>
</html>
