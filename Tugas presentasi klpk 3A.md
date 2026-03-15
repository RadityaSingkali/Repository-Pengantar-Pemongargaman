# Similarity Transformation and Diagonalization

## 1. Apa itu Transformasi Similaritas?
Transformasi similaritas terjadi ketika kita mengambil sebuah matriks persegi $A$, lalu mengalikan bagian depannya dengan invers dari sebuah matriks $P$ (yaitu $P^{-1}$) dan bagian belakangnya dengan matriks $P$ itu sendiri.Persamaannya dituliskan sebagai:

$$P^{-1}AP$$

Dua matriks (misalnya $A$ dan $B$) dikatakan similar jika ada matriks nonsingular $P$ sedemikian rupa sehingga $B = P^{-1}AP$.
Tujuan utama dari transformasi ini biasanya adalah untuk Diagonalisasi. Kita mencari matriks $P$ yang tepat sehingga hasil dari $P^{-1}AP$ menjadi matriks diagonal (matriks yang angkanya hanya ada di garis diagonal tengah). Matriks diagonal jauh lebih mudah dihitung dalam operasi matematika yang kompleks.

## 2. Apa itu Diagonalization
Diagonalisasi adalah kasus khusus dari Similarity Transformation di mana kita mencari matriks $P$ sehingga matriks hasil transformasinya ($D$) berbentuk matriks diagonal.

$$D = P^{-1}AP$$

Di sini, $D$ adalah matriks yang semua elemennya nol, kecuali pada diagonal utama.

Syarat DiagonalisasiSebuah matriks $A$ berukuran $n \times n$ dapat didiagonalisasi jika dan hanya jika $A$ memiliki $n$ vektor eigen yang bebas linear.

omponen Matriks P dan D
Jika kita berhasil menemukan vektor eigen dan nilai eigen dari $A$:

* Matriks $P$ (Matriks Modal): Kolom-kolomnya berisi vektor-vektor eigen dari $A$.

* Matriks $D$: Elemen diagonal utamanya adalah nilai-nilai eigen ($\lambda$) yang bersesuaian dengan vektor eigen di $P$.


## 3. Sifat Invariant (Tidak Berubah)
Bagian terpenting dari gambar tersebut adalah pembuktian bahwa Eigenvalues (nilai eigen) tidak berubah meskipun matriksnya telah ditransformasi.

Dalam persamaan (1.2.22), ditunjukkan bahwa:

* Persamaan Karakteristik tetap sama: Determinan dari $|P^{-1}AP - \lambda I|$ sama dengan determinan $|A - \lambda I|$.

* Artinya: Jika Anda memiliki matriks $A$ dan mengubahnya menjadi $P^{-1}AP$, angka-angka "Eigenvalue" ($\lambda$) yang Anda dapatkan akan tetap persis sama.



# Contoh dari Similarity Transformation and Diagonalization
Misalkan kita memiliki matriks $A$:$$A = \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix}$$Tujuan kita adalah mencari matriks $P$ sedemikian rupa sehingga $P^{-1}AP = D$, di mana $D$ adalah matriks diagonal.

### Langkah 1: Mencari Eigenvalues ($\lambda$)Kita gunakan persamaan karakteristik: $\det(A - \lambda I) = 0$.

$$\det \begin{pmatrix} 1-\lambda & 2 \\ 2 & 1-\lambda \end{pmatrix} = 0$$
$$(1-\lambda)(1-\lambda) - (2)(2) = 0$$
$$\lambda^2 - 2\lambda - 3 = 0$$
$$(\lambda - 3)(\lambda + 1) = 0$$

Maka, $\lambda_1 = 3$ dan $\lambda_2 = -1$.

### Langkah 2: Mencari Eigenvectors ($v$)
Untuk setiap $\lambda$, kita cari vektor $v$ yang memenuhi $(A - \lambda I)v = 0$.

* Untuk $\lambda = 3$: didapat eigenvector $v_1 = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$

* Untuk $\lambda = -1$: didapat eigenvector $v_2 = \begin{pmatrix} 1 \\ -1 \end{pmatrix}$

### Langkah 3: Menyusun Matriks $P$ dan $P^{-1}$

Matriks $P$ dibentuk dengan meletakkan eigenvectors sebagai kolom-kolomnya:

$$P = \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$$

Lalu kita cari inversnya ($P^{-1}$):

$$P^{-1} = \frac{1}{-2} \begin{pmatrix} -1 & -1 \\ -1 & 1 \end{pmatrix} = \begin{pmatrix} 0.5 & 0.5 \\ 0.5 & -0.5 \end{pmatrix}$$

### Langkah 4: Melakukan Transformasi Similaritas
Sekarang kita hitung $P^{-1}AP$:

$$D = \begin{pmatrix} 0.5 & 0.5 \\ 0.5 & -0.5 \end{pmatrix} \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$$

### Hasil:

$$D = \begin{pmatrix} 3 & 0 \\ 0 & -1 \end{pmatrix}$$


## Contoh penggunaan dalam python 
```python
import numpy as np

A = np.array([[0, 2], 
              [1, 1]])

L_vals, V = np.linalg.eig(A)

L = np.diag(L_vals)

V_inv = np.linalg.inv(V)
L1 = V_inv @ A @ V

print("Matriks A:\n", A)
print("\nModal Matrix (V):\n", V)
print("\nEigenvalue Matrix (L):\n", L)
print("\nHasil L1 (V^-1 * A * V):\n", L1)

# Hasil dari pythonnya:
Matriks A:
 [[0 2]
 [1 1]]

Modal Matrix (V):
 [[-0.89442719 -0.70710678]
 [ 0.4472136  -0.70710678]]

Eigenvalue Matrix (L):
 [[-1.  0.]
 [ 0.  2.]]

Hasil L1 (V^-1 * A * V):
 [[-1.00000000e+00  3.33066907e-16]
 [ 0.00000000e+00  2.00000000e+00]]
 ```


