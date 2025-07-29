# Proyek-UAS-ComputerVision
Proyek OCR Plat Nomor Kendaraan dengan Visual Language Model (VLM) dan LM Studio
Ini adalah repositori untuk proyek Optical Character Recognition (OCR) plat nomor kendaraan menggunakan Visual Language Model (VLM) yang diintegrasikan dengan LM Studio dan diimplementasikan menggunakan Python. Proyek ini bertujuan untuk mengotomatisasi ekstraksi teks dari gambar plat nomor dan mengevaluasi akurasinya menggunakan metrik Character Error Rate (CER).

# Fitur Utama
- Integrasi LM Studio: Memanfaatkan LM Studio sebagai server inferensi lokal untuk menjalankan model VLM.
- Visual Language Model (VLM): Menggunakan model multimodal seperti LLaVA atau BakLLaVA untuk memproses gambar dan menghasilkan teks plat nomor. Model spesifik yang berhasil digunakan adalah llava-phi-3-mini.
- Deteksi Plat Nomor Otomatis: Program membaca gambar plat nomor dari dataset yang telah dianotasi.
- Ekstraksi Teks: Mengirimkan input gambar dari dataset ke LM Studio dengan prompt spesifik untuk mengekstrak nomor plat.
- Evaluasi CER: Menghitung Character Error Rate (CER) untuk mengukur akurasi prediksi dibandingkan dengan ground truth.
- Output CSV: Menyimpan hasil prediksi dan skor CER ke dalam file CSV (hasil_prediksi.csv) untuk analisis lebih lanjut.
# Persyaratan Sistem
Sistem Operasi: Windows 10/11
- Python 3.x
- LM Studio
- Kartu Grafis NVIDIA dengan VRAM memadai (minimal 4GB VRAM. Model llava-phi-3-mini berhasil berjalan pada NVIDIA GeForce GTX 1050 dengan 4GB VRAM).
- Download Dataset Berikut : https://www.kaggle.com/datasets/juanthomaswijaya/indonesian-license-plate-dataset
- Dari Dataset tersebut ambil file yang berasal dari Folder Indonesian License Plate Recognition (folder test) yang dijadikan 1 dari Folder Label .txt & Folder Images .jpg
## Pengaturan 

1.  **Struktur Folder**: Pastikan folder `test` dari dataset berada di direktori yang sama dengan skrip Python Anda.
     ```
    proyek-ocr/
    ├── test/
    │   ├── gambar1.jpg
    │   └── gambar1.txt
    └── predict.py
    └── evaluate.py
    ```

2.  **Install Dependensi**:
    ```bash
    pip install pandas requests
    ```
# Panduan Pengoperasian Program
Ikuti langkah-langkah di bawah ini untuk menjalankan sistem OCR Plat Nomor Kendaraan Anda:

# 1. **Inisiasi Layanan Model di LM Studio**
- Buka aplikasi LM Studio di komputer Anda.
- Akses bagian "Local Inference Server" (biasanya ikon chip).
- Pilih dan muat model Visual Language Model (VLM) yang telah Anda unduh, seperti llava-phi-3-mini-gguf. Pastikan proses pemuatan model berhasil tanpa error.
- Pastikan fitur dukungan visual (Vision Support) diaktifkan. Cari opsi atau checkbox yang relevan di pengaturan server lokal LM Studio Anda untuk memastikan model dapat memproses gambar.
- Klik tombol "Start Server" untuk memulai layanan model. Pastikan status server menunjukkan "Running".

# 2. **Eksekusi Skrip Python**
- Setelah server LM Studio berjalan dan model berhasil dimuat, lanjutkan dengan menjalankan skrip Python Anda:
- Buka Terminal atau Command Prompt, lalu navigasikan ke direktori utama proyek Anda (COMPUTERVISION_OCR).
  
Langkah 2.1: Persiapan Data Ground Truth
  
  Jalankan skrip predict.py terlebih dahulu:
```
 `predict.py` 
```
- Skrip ini akan memproses file anotasi dari dataset Anda dan menghasilkan file ground_truth.csv di dalam folder test dataset Anda, yang berisi data plat nomor asli.

Langkah 2.2: Prediksi dan Evaluasi OCR

Selanjutnya, jalankan skrip evaluate.py:
```  
    `evaluate.py`
```

- Skrip ini akan mengambil gambar dari dataset, mengirimkannya ke LM Studio untuk diproses oleh VLM, dan kemudian menghitung Character Error Rate (CER) dari hasil prediksi.

Seluruh hasil prediksi dan skor evaluasi akan secara otomatis disimpan dalam file CSV bernama hasil_prediksi.csv di direktori proyek Anda.
