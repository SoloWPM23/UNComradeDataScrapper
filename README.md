# UN Comtrade Data Extractor

Code Python untuk mengekstrak data perdagangan internasional dari API UN Comtrade, khususnya data impor dan ekspor Indonesia untuk komoditas pesawat tempur dan rudal.

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

2. **Konfigurasi parameter** pada Cell 2:
   ```python
   subscription_key = '<API KEY>'   # ganti API key sesuai milik anda
   directory = '<SAVE DIR>'         # Contoh: 'C:/Users/YourName/Documents/comtrade_data'
   ```

3. **Sesuaikan parameter ekstraksi** pada Cell 4 sesuai kebutuhan:
   ```python
   years = [2022, 2023, 2024, 2025]     # Ubah tahun sesuai kebutuhan
   flows = ['M', 'X']                   # M = Impor, X = Ekspor
   codes = ['880230', '880240', '9306'] # Kode HS produk yang ingin diunduh
   ```

4. Jalankan semua cell secara berurutan:
   - **Cell 1**: Import library yang diperlukan
   - **Cell 2**: Konfigurasi direktori penyimpanan
   - **Cell 3**: Setup variabel tanggal untuk referensi
   - **Cell 4**: Ekstrak data dari UN Comtrade dengan parameter yang telah dikonfigurasi
   - **Cell 5**: Simpan data ke file Excel

## 📊 Output

Script akan menghasilkan file Excel dengan nama format: `comtrade_YYYY-MM-DD.xlsx`

File berisi kolom-kolom:
- Data perdagangan asli dari UN Comtrade (termasuk: reporter, partner, trade value, quantity, dll)
- `Year`: Tahun data
- `FlowCode`: Kode aliran (M untuk impor, X untuk ekspor)
- `HSCode`: Kode HS komoditas

## 🔑 Catatan Penting

### Konfigurasi Parameter

#### Direktori Penyimpanan (`directory`)
- Pastikan direktori yang ditentukan dapat diakses dan memiliki ruang disk yang cukup
- Script akan membuat direktori secara otomatis jika belum ada
- Contoh path: `C:\Users\YourName\Documents\data` atau `./output`

#### Tahun (`years`)
- Dapat diubah sesuai kebutuhan analisis
- Semakin banyak tahun, semakin lama proses ekstraksi

#### Aliran (`flows`)
- `M`: Impor (Import)
- `X`: Ekspor (Export)
- Dapat hanya menggunakan salah satu atau keduanya

#### Kode HS (`codes`)
- `880230`: Pesawat tempur (Combat aircraft)
- `880240`: Komponen pesawat tempur (Aircraft parts)
- `9306`: Rudal dan amunisi (Missiles and ammunition)
- Dapat ditambah/dikurangi sesuai komoditas yang ingin dianalisis

### API Key (Opsional)
- Data publik UN Comtrade dapat diakses tanpa API key
- Untuk menggunakan API key dengan quota lebih tinggi, daftarkan di [UN Comtrade](https://comtrade.un.org/)
- Jika tidak menggunakan API key, biarkan parameter `subscription_key` kosong

### Performa & Batasan
- UN Comtrade API memiliki batasan permintaan per waktu
- Total request = jumlah tahun × jumlah aliran × jumlah kode HS
- Contoh: 4 tahun × 2 aliran × 3 kode = 24 request total
- Jika mengalami timeout atau error, coba kurangi jumlah kombinasi parameter

## 🐛 Troubleshooting

| Masalah | Solusi |
|---------|--------|
| ModuleNotFoundError | Pastikan semua dependensi terinstall dengan `pip install -r requirements.txt` |
| Timeout/Connection Error | Periksa koneksi internet dan coba lagi atau kurangi jumlah request |
| Directory Error | Pastikan path direktori valid dan tidak menggunakan karakter khusus |
| Data kosong | Verifikasi kode HS dan tahun yang digunakan valid di UN Comtrade |

## 📚 Referensi

- [UN Comtrade API](https://comtradedeveloper.un.org/)
- [Pandas](https://pandas.pydata.org/)
- [Comtradeapicall](https://pypi.org/project/comtradeapicall/)

## 📝 Lisensi

Project ini dibuat untuk keperluan pembelajaran dan analisis data.

## ✍️ Author

**Solo Wandika Putra Manurung**
- GitHub: [@SoloWPM23](https://github.com/SoloWPM23)

Created for data analysis and trade statistics learning purposes.
