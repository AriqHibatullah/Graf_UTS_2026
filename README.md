# UTS Graf Sains Data 2026: Python Driver untuk (Neo4J) dan Rekomendasi
Project ini merupakan pengerjaan Ujian Tengah Semester mata kuliah Graf Sains Data Semeester 7 (Gasal 2026/2027), S1 Sains Data.
Ujian ini dikerjakan oleh:
| Nama | Muhammad Ariq Hibatullah |
| :--- | :--- |
| NIM | 23031554064 |
| Kelas | Graf Sains Data 2023A |

## Isi Repositori
- **main.ipynb**, merupakan file Notebook yang berisi seluruh jawaban untuk soal UTS.
- **data/**, merupakan folder yang berisi dataset asli RetailRocket e-commerce.
- **data_filtered/**, merupakan hasil data P1 dan P2 yang telah difilter yang dibuat dalam Notebook.
- **requirment.txt**, merupakan kumpulan pakeet-paket yang dibutuhkan untuk menjalankan Notebook.

## Dataset yang digunakan
Data yang digunakan merupakan RetailRocket e-commerce dataset (Roman Zykov, Kaggle), file events.csv.

Pembagian periode (filter) pada data tersebut:
- P1 -> `15/5/2025` - `3/7/2025` (6 Minggu)
- P2 -> `4/7/2025` - `17/7/2025` (2 Minggu)

## Overview hasil yang didapat
| Perihal | Hasil |
| :--- | :--- |
| Jumlah Node | User Overlap: 11.104, Item Overlap: 61.287  |
| Jumlah Event | P1: 1.009.164, P2: 292.404 |
| Proyeksi yang digunakan | Proyeksi Item (Item-Item) |
| User acak terpilih | 142299 |
| 3 Item iklan | 460241, 158188, 83840 |
| Hit@5 | 0 |
| NDCG@5  | 0 |

Hasil Hit@5 dan NDCG@5 bernilai 0 karena tidak satupun rekomendasi terdapat pada Ground Truth. Hal tersebut terjadi pada Pengguna `142299` akibat tingginya kelangkaan data (extreme sparsity) dan bias model Item-Based KNN terhadap kelompok produk populer di dense core, sehingga gagal merekomendasikan item aktual P2 (`172774`) yang bersifat long-tail. Dinamika preferensi pengguna yang terfragmentasi serta ground truth P2 yang hanya berjumlah satu item menciptakan sparsity bottleneck pada pengujian skala individu, yang menegaskan perlunya mengevaluasi performa model berdasarkan rata-rata agregat (Mean Hit@5 dan Mean NDCG@5) di seluruh sampel pengguna.
