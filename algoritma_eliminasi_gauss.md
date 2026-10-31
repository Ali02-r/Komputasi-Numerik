# Algoritma Eliminasi Gauss untuk Menyelesaikan SPL 3 Variabel

Nama : Ali Rafshanjani
NIM  : 202511420023
Mata kuliah : Komputasi Numerik

## 1. Latar Belakang Masalah

Sistem persamaan linear (SPL) tiga variabel adalah tiga persamaan linear yang memuat tiga bilangan yang belum diketahui, yaitu x1, x2, dan x3. Bentuk umumnya:

```
a11·x1 + a12·x2 + a13·x3 = c1
a21·x1 + a22·x2 + a23·x3 = c2
a31·x1 + a32·x2 + a33·x3 = c3
```

Algoritma ini bertugas menemukan nilai x1, x2, dan x3 yang memenuhi ketiga persamaan sekaligus.

- **Masukan:** sembilan koefisien `a` dan tiga konstanta `c`
- **Keluaran:** nilai x1, x2, x3, atau keterangan bahwa sistem tidak mempunyai solusi tunggal

## 2. Ide Dasar Metode

Eliminasi Gauss menyelesaikan SPL dengan menyederhanakannya sedikit demi sedikit sampai jawabannya mudah dibaca. Prosesnya terdiri dari dua fase:

1. **Eliminasi maju:** koefisien yang berada di bawah diagonal utama dibuat menjadi 0, sehingga sistem berbentuk tangga. Persamaan ketiga hanya memuat x3, persamaan kedua memuat x2 dan x3, sedangkan persamaan pertama masih memuat ketiganya.
2. **Substitusi mundur:** x3 dihitung lebih dulu dari persamaan ketiga. Nilainya dipakai untuk mencari x2, lalu keduanya dipakai untuk mencari x1.

Agar penulisan lebih ringkas, koefisien dan konstanta digabung dalam satu tabel yang disebut **matriks augmented** `M` (3 baris dan 4 kolom). Kolom keempat berisi konstanta `c`.

```
| a11 a12 a13 | c1 |      baris 1
| a21 a22 a23 | c2 |      baris 2
| a31 a32 a33 | c3 |      baris 3
```

## 3. Langkah-langkah Penyelesaian
 
1. Masukkan koefisien `a` dan konstanta `c`, lalu susun matriks augmented `M`.
2. Lakukan eliminasi maju untuk kolom `k = 1, 2, 3`:
   1. Periksa pivot, yaitu `M[k][k]`. Bila nilainya 0, cari baris di bawah baris `k` yang elemen kolom `k`-nya tidak 0, lalu tukar posisinya. Bila tidak ada baris yang bisa ditukar, tampilkan "tidak ada solusi tunggal" dan hentikan algoritma.
   2. Untuk setiap baris `i` di bawah baris `k`, hitung `faktor = M[i][k] / M[k][k]`, lalu kurangkan baris `i` dengan faktor kali baris `k`. Dengan cara ini `M[i][k]` menjadi 0.
3. Lakukan substitusi mundur: hitung x3 dari baris 3, kemudian x2 dari baris 2, dan terakhir x1 dari baris 1.
4. Tampilkan x1, x2, dan x3.
