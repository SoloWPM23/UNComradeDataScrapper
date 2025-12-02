# UN Comtrade Data Extractor

Aplikasi Python untuk mengekstrak data perdagangan internasional dari API UN Comtrade, khususnya data impor dan ekspor Indonesia untuk komoditas pesawat tempur dan rudal.

## 📋 Deskripsi

Script ini menggunakan API UN Comtrade untuk mengambil data perdagangan bilateral dari Indonesia dengan parameter:
- **Tahun**: 2022, 2023, 2024, 2025
- **Tipe Aliran**: Impor (M) dan Ekspor (X)
- **Komoditas (Kode HS)**:
  - `880230`: Pesawat tempur
  - `880240`: Komponen pesawat tempur
  - `9306`: Rudal dan komponen rudal

Data yang diambil kemudian digabungkan dan disimpan dalam format file Excel (.xlsx).

## 🚀 Fitur Utama

- Mengakses API UN Comtrade tanpa autentikasi terbatas (untuk data publik)
- Mengambil data perdagangan multi-tahun secara otomatis
- Mengolah dan menggabungkan data dari berbagai kombinasi parameter
- Menyimpan hasil dalam format Excel dengan timestamp
- Error handling untuk data kosong

## 📦 Dependensi

Lihat file `requirements.txt` untuk daftar lengkap dependensi:

- `pandas`: Untuk manipulasi dan analisis data
- `requests`: Untuk permintaan HTTP
- `comtradeapicall`: Library untuk akses API UN Comtrade
- `openpyxl`: Untuk membaca dan menulis file Excel

## 🔧 Instalasi

1. Clone atau download project ini
2. Buat virtual environment (opsional tapi direkomendasikan):
   ```bash
   python -m venv venv
   ```
   
3. Aktivasi virtual environment:
   - **Windows**:
     ```bash
     venv\Scripts\activate
     ```
   - **Linux/Mac**:
     ```bash
     source venv/bin/activate
     ```

4. Install dependensi:
   ```bash
   pip install -r requirements.txt
   ```

## 💻 Cara Penggunaan

1. Buka file `UN_usable.ipynb` di Jupyter Notebook atau JupyterLab
2. Pada Cell 2, sesuaikan konfigurasi:
   ```python
   subscription_key = '<API KEY>'  # Ganti dengan API key Anda (jika diperlukan)
   directory = '<SAVE DIR>'         # Ganti dengan direktori penyimpanan file
   ```

3. Jalankan semua cell secara berurutan:
   - **Cell 1**: Import library yang diperlukan
   - **Cell 2**: Konfigurasi API key dan direktori penyimpanan
   - **Cell 3**: Setup variabel tanggal
   - **Cell 4**: Ekstrak data dari UN Comtrade
   - **Cell 5**: Simpan data ke file Excel

## 📊 Output

Script akan menghasilkan file Excel dengan nama format: `comtrade_YYYY-MM-DD.xlsx`

File berisi kolom-kolom:
- Data perdagangan asli dari UN Comtrade (termasuk: reporter, partner, trade value, quantity, dll)
- `Year`: Tahun data
- `FlowCode`: Kode aliran (M untuk impor, X untuk ekspor)
- `HSCode`: Kode HS komoditas

## 🔑 Catatan Penting

### API Key
- Data publik UN Comtrade dapat diakses tanpa API key
- Untuk menggunakan API key dengan quota lebih tinggi, daftarkan di [UN Comtrade](https://comtrade.un.org/)
- Jika tidak menggunakan API key, biarkan parameter `subscription_key` kosong

### Direktori Penyimpanan
- Pastikan direktori yang ditentukan dapat diakses dan memiliki ruang disk yang cukup
- Script akan membuat direktori secara otomatis jika belum ada

### Batasan Rate
- UN Comtrade API memiliki batasan permintaan per waktu
- Jika mengalami error timeout, coba kurangi jumlah tahun atau kode produk

## 🐛 Troubleshooting

| Masalah | Solusi |
|---------|--------|
| ModuleNotFoundError | Pastikan semua dependensi terinstall dengan `pip install -r requirements.txt` |
| Timeout/Connection Error | Periksa koneksi internet dan coba lagi atau kurangi jumlah request |
| Directory Error | Pastikan path direktori valid dan tidak menggunakan karakter khusus |
| Data kosong | Verifikasi kode HS dan tahun yang digunakan valid di UN Comtrade |

## 📚 Referensi

- [UN Comtrade API Documentation](https://comtrade.un.org/api/)
- [Klasifikasi HS](https://www.witsонline.org/)
- [Pandas Documentation](https://pandas.pydata.org/)

## 📝 Lisensi

Project ini dibuat untuk keperluan pembelajaran dan analisis data.

## ✍️ Author

Created for data analysis and trade statistics learning purposes.
