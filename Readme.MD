# Optimasi Biaya Sewa Cloud Server: Program Linear

Tugas UTS **Pemodelan dan Simulasi** (Soal 2): Kelompok 2, Kelas A.

Notebook ini mencari kombinasi jam sewa dua jenis server dengan biaya paling rendah, tetapi tetap memenuhi kebutuhan minimal instruksi pemrosesan dan akses basis data.

## Model

| Variabel | Keterangan |
|---|---|
| `x` | Jam sewa Server Standar |
| `y` | Jam sewa Server Performa Tinggi |

$$\min Z = 8000x + 12000y$$

Kendala:

- `20x + 10y ≥ 100` (instruksi pemrosesan)
- `10x + 30y ≥ 90` (akses basis data)
- `x, y ≥ 0`

## Isi Notebook

1. **Metode grafik**: menghitung titik pojok daerah layak, lalu mengevaluasi nilai `Z` di setiap titik.
2. **Visualisasi**: membuat plot daerah layak, garis kendala, dan garis iso-biaya. Plot disimpan sebagai `grafik_daerah_layak.png`.
3. **Verifikasi `linprog`**: menyelesaikan model dengan solver HiGHS dari SciPy, termasuk shadow price.
4. **Versi bilangan bulat**: menghitung solusi jika jam sewa harus bulat.

## Hasil

| Skenario | x (jam) | y (jam) | Biaya minimum |
|---|---|---|---|
| Kontinu | 4,2 | 1,6 | Rp52.800 |
| Jam bulat | 4 | 2 | Rp56.000 |

Shadow price: Rp240 per satuan instruksi dan Rp320 per satuan akses basis data. Pada solusi optimum, kedua kendala terpenuhi tepat di batas minimalnya.

## Menjalankan

```bash
pip install numpy matplotlib scipy
jupyter notebook A_Kelompok_2_UTS_Soal_2.ipynb
```

Notebook juga bisa langsung dibuka di Google Colab. Opsi `integrality` pada `linprog` membutuhkan SciPy ≥ 1.9.

## Anggota Kelompok

| NIM | Nama |
|---|---|
| 2408561001 | Nayla Lareina Widyastuti Seregar |
| 2408561004 | Si Ngurah Putu Juliarta |
| 2408561025 | I Wayan Yudhiastara Sudarmawan |
| 2408561049 | I Gusti Ayu Titania Pramesti Maharani |
| 2408561114 | I Putu Wahyu Eka Saputra |

## Referensi

- H. A. Taha, *Operations Research: An Introduction*, 10th ed. Pearson, 2017.
- P. Virtanen *et al.*, "SciPy 1.0: Fundamental algorithms for scientific computing in Python," *Nature Methods*, vol. 17, no. 3, pp. 261–272, 2020, doi: 10.1038/s41592-019-0686-2.