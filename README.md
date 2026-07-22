# README - Program Tugas Akhir

**Judul:** Analisis Gerakan Lengan Saat Latihan Bicep Curl pada Video Menggunakan Pose Estimation Berbasis Deep Learning Menggunakan MediaPipe
**Nama:** Henry Abimanyu Dewandani
**NIM:** 1301220283
**Prodi:** S1 Informatika, Telkom University

## Ringkasan
Program ini mengestimasi sudut siku dari video Bicep Curl memakai dua model pose estimation (MediaPipe BlazePose dan YOLOv8-Pose), lalu menghitung repetisi otomatis berbasis ambang sudut adaptif serta mengekstraksi parameter kinematika (ROM, kecepatan angular, Time Under Tension).

## File Program Final
Hanya empat file ini yang dipakai untuk hasil di buku TA. Sisanya arsip.

| Peran | File | Output |
|---|---|---|
| Analisis BlazePose (3 skenario + subjek 2) | `Code_TA_BlazePose_Analysis/2026-06-12-code_TA_V6_2_feedback_fix.ipynb` | `outputs_v6_2_feedbackfix/` |
| Komparasi utama (adaptive threshold) | `Code_Comparison/2026-06-11-code_TA_Comparison_v3_pixel_fix.ipynb` | `comparison_outputs_v3/` |
| Komparasi mode fixed (pendukung) | `Code_Comparison/2026-06-12-code_TA_Comparison_v3_fixed_threshold.ipynb` | `comparison_outputs_v3_fixed/` |
| Demo live (webcam) | `Code_TA_BlazePose_Analysis/2026-06-12-code_TA_V6_2_LIVE.ipynb` | dibuat saat run |

Model pembanding: `yolov8m-pose.pt` (Medium). File `yolov8n-pose.pt` hanya diunduh otomatis oleh ultralytics untuk cek AMP, bukan model komparasi.

## Cara Menjalankan
1. Pasang Python 3.11 dan dependency: `pip install -r requirements.txt`
2. Buka notebook di VS Code atau Jupyter.
3. Sesuaikan path video input pada sel konfigurasi (folder `Dataset video Bicep curl/`).
4. Jalankan sel dari atas ke bawah. Output CSV, XLSX, dan video anotasi tersimpan di folder output masing-masing.
5. Untuk demo live, jalankan notebook LIVE, tekan `Q` untuk berhenti.

## Catatan Penting
- Semua angka akurasi di buku (MAE, RMSE, rep count) berasal dari run CPU yang konsisten.
- Run GPU hanya dipakai untuk angka FPS YOLOv8 (sekitar 30,3 FPS). MAE run GPU berbeda karena perbedaan numerik backend setelah instalasi torch CUDA, jadi jangan dicampur dengan angka CPU.
- Perhitungan sudut memakai koordinat pixel (pixel fix), bukan koordinat ternormalisasi, agar sudut tidak terdistorsi rasio aspek.

## Lingkungan Uji
- OS: Windows
- Python: 3.11
- GPU (opsional, hanya untuk uji FPS YOLOv8): NVIDIA GeForce RTX 2050
