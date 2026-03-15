# Similarity Transformation and Diagonalization

## 1. Apa itu Transformasi Similaritas?
Transformasi similaritas terjadi ketika kita mengambil sebuah matriks persegi $A$, lalu mengalikan bagian depannya dengan invers dari sebuah matriks $P$ (yaitu $P^{-1}$) dan bagian belakangnya dengan matriks $P$ itu sendiri.Persamaannya dituliskan sebagai:

$$P^{-1}AP$$

Dua matriks (misalnya $A$ dan $B$) dikatakan similar jika ada matriks nonsingular $P$ sedemikian rupa sehingga $B = P^{-1}AP$.
Tujuan utama dari transformasi ini biasanya adalah untuk Diagonalisasi. Kita mencari matriks $P$ yang tepat sehingga hasil dari $P^{-1}AP$ menjadi matriks diagonal (matriks yang angkanya hanya ada di garis diagonal tengah). Matriks diagonal jauh lebih mudah dihitung dalam operasi matematika yang kompleks.

## Sifat Invariant (Tidak Berubah)
Bagian terpenting dari gambar tersebut adalah pembuktian bahwa Eigenvalues (nilai eigen) tidak berubah meskipun matriksnya telah ditransformasi.

Dalam persamaan (1.2.22), ditunjukkan bahwa:

* Persamaan Karakteristik tetap sama: Determinan dari $|P^{-1}AP - \lambda I|$ sama dengan determinan $|A - \lambda I|$.

* Artinya: Jika Anda memiliki matriks $A$ dan mengubahnya menjadi $P^{-1}AP$, angka-angka "Eigenvalue" ($\lambda$) yang Anda dapatkan akan tetap persis sama.



# 77. Contoh dari Similarity Transformation and Diagonalization
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



