# Tebus Emas Semarang – Kalkulator Penaksir Harga Emas

Aplikasi web berbasis **HTML + JavaScript** untuk menghitung estimasi harga tebus emas, biaya penebusan, dan estimasi cashback, serta menyediakan output siap dibagikan ke WhatsApp untuk tim internal maupun customer.

---

## 📝 DUA OUTPUT OTOMATIS: CUSTOMER & TIM TEBUS
Aplikasi ini secara otomatis menghasilkan **dua output berbeda**:
- **Output Customer:**
  - Bahasa sopan, persuasif, dan transparan.
  - Siap copy/share ke WhatsApp customer.
- **Output Tim Tebus:**
  - Laporan internal lengkap, detail margin dan catatan.
  - Siap copy/share ke WhatsApp tim internal.

Kedua output dapat ditampilkan bersamaan di halaman, masing-masing dengan tombol "Share ke WhatsApp".

---

## 📥 INPUT YANG DIISI USER
- **Berat emas (gram)**
- **Harga pasar per gram (Rp)**
- **Jumlah pinjaman di pegadaian (Rp)**

---

## 🧮 RUMUS PERHITUNGAN
- **Biaya Penebusan** = Jumlah Pinjaman + (10% x Jumlah Pinjaman)
- **Nilai Pasar Emas** = Berat x Harga per gram
- **Cashback Total** = Nilai Pasar – Biaya Penebusan
- **Cashback Customer** = Cashback Total _(langsung, tidak dibagi dua)_

---

## ✍ FORMAT OUTPUT 1 – UNTUK TIM TEBUS EMAS
Tampilan lengkap dan rinci, siap copy/share ke WhatsApp tim:

```html
<!-- Contoh HTML untuk output tim -->
<div id="outputTim">
  <b>📄 Laporan Internal – Tim Tebus Emas</b><br>
  Nama Customer: <span id="namaTim">[Nama]</span><br>
  Tanggal Penebusan: <span id="tglTim">[Tanggal]</span><br>
  Berat Emas: <span id="beratTim"></span> gram<br>
  Harga per Gram: <span id="hargaTim"></span><br>
  Nilai Pasar: <span id="nilaiTim"></span><br>
  <br>
  Jumlah Pinjaman Pegadaian: <span id="pinjamanTim"></span><br>
  Biaya Penebusan (Pinjaman + 10%): <span id="tebusTim"></span><br>
  <br>
  Total Cashback: <span id="cashbackTim"></span><br>
  <i>Catatan: Semakin lama menunggu, biaya bunga terus bertambah dan margin keuntungan menurun.</i><br>
  <br>
  ✅ Siap untuk proses tebus hari ini.<br>
  <button onclick="shareToWA('tim')">Share ke WhatsApp</button>
</div>
```

---

## 💌 FORMAT OUTPUT 2 – UNTUK CUSTOMER
Tampilan sopan, persuasif, dan siap copy/share ke WhatsApp customer:

```html
<!-- Contoh HTML untuk output customer -->
<div id="outputCustomer">
  <b>Assalamu'alaikum Kak <span id="namaCust">[Nama]</span>,</b><br><br>
  Berikut ini rincian penaksiran emas Kakak:<br>
  📦 Berat: <span id="beratCust"></span> gram<br>
  💰 Harga Pasar Saat Ini: <span id="hargaCust"></span>/gram<br>
  📊 Nilai Pasar Emas: <span id="nilaiCust"></span><br>
  <br>
  📉 Jumlah Pinjaman: <span id="pinjamanCust"></span><br>
  💳 Biaya Penebusan: <span id="tebusCust"></span><br>
  <br>
  💎 Estimasi Cashback: <span id="cashbackCust"></span><br>
  <br>
  <i>Semakin cepat proses penebusan, semakin tinggi nilai yang bisa Kakak terima. Jika menunggu lebih lama, bunga pegadaian akan terus bertambah dan mengurangi nilai emas Kakak 😢</i><br>
  <br>
  Kami siap bantu COD kapan saja. Silakan hubungi tim kami segera ya, Kak 😊<br>
  <br>
  Salam hangat,<br>
  <b>Tim Tebus Emas Semarang</b><br>
  <button onclick="shareToWA('customer')">Share ke WhatsApp</button>
</div>
```

---

## 🖥️ CONTOH IMPLEMENTASI HTML/JS: MENAMPILKAN DUA OUTPUT SEKALIGUS

```html
<!-- Form input -->
<input id="berat" type="number" placeholder="Berat (gram)">
<input id="harga" type="number" placeholder="Harga per gram">
<input id="pinjaman" type="number" placeholder="Jumlah pinjaman">
<button onclick="proses()">Hitung</button>

<!-- Output Customer dan Tim -->
<div id="outputCustomer"></div>
<div id="outputTim"></div>

<script>
function proses() {
  const berat = parseFloat(document.getElementById('berat').value) || 0;
  const harga = parseFloat(document.getElementById('harga').value) || 0;
  const pinjaman = parseFloat(document.getElementById('pinjaman').value) || 0;
  const nilaiPasar = berat * harga;
  const biayaTebus = pinjaman * 1.10;
  const cashback = nilaiPasar - biayaTebus;
  // Output Customer
  document.getElementById('outputCustomer').innerHTML =
    `<b>Assalamu'alaikum Kak,</b><br>Berikut rincian penaksiran emas:<br>`+
    `📦 Berat: ${berat} gram<br>💰 Harga: Rp ${harga}/gram<br>📊 Nilai Pasar: Rp ${nilaiPasar}<br>`+
    `📉 Pinjaman: Rp ${pinjaman}<br>💳 Biaya Tebus: Rp ${biayaTebus}<br>💎 Estimasi Cashback: Rp ${cashback > 0 ? cashback : 0}<br>`;
  // Output Tim
  document.getElementById('outputTim').innerHTML =
    `<b>📄 Laporan Internal – Tim Tebus Emas</b><br>`+
    `Berat: ${berat} gram<br>Harga: Rp ${harga}<br>Nilai Pasar: Rp ${nilaiPasar}<br>`+
    `Pinjaman: Rp ${pinjaman}<br>Biaya Tebus: Rp ${biayaTebus}<br>Total Cashback: Rp ${cashback > 0 ? cashback : 0}<br>`;
}
</script>
```

---

## 🚀 FITUR UTAMA
- Perhitungan otomatis berbasis JavaScript.
- Output customer & tim tebus tampil bersamaan.
- Masing-masing output siap copy/share ke WhatsApp.
- Format pesan menyesuaikan kebutuhan (internal/customer).
- UI responsif dan mudah digunakan.

---

## 🛠️ CONTOH LOGIKA JS UNTUK PERHITUNGAN
```js
function hitungTebus(berat, hargaPerGram, pinjaman) {
  const nilaiPasar = berat * hargaPerGram;
  const biayaTebus = pinjaman * 1.10;
  const cashback = nilaiPasar - biayaTebus;
  return { nilaiPasar, biayaTebus, cashback: cashback > 0 ? cashback : 0 };
}
```

---

## 🎯 TUJUAN UTAMA
- Mempermudah tim menghitung potensi keuntungan
- Memberi customer informasi yang transparan, sopan, dan meyakinkan
- Mendorong tindakan cepat sebelum emas dilelang
- Menyediakan output yang siap dibagikan via WhatsApp