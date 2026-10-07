# Text Similarity
## Identitas
Kelas 2025C

Program Studi S1 Sains Data

Universitas Negeri Surabaya

Nama Anggota:

Namira Rachmi Andini (25031554153)

Syahira Nanda Raihanna (25031554199)
## Deskripsi

Repository ini berisi implementasi **Text Similarity** untuk mengukur tingkat kemiripan antara sebuah query dengan dokumen teks yang terdapat pada dataset film.

Dataset yang digunakan adalah `combined.csv`. Dataset tersebut berisi informasi film, sedangkan kolom **description** digunakan sebagai sumber teks untuk proses pencarian berdasarkan kemiripan. Kolom **title** digunakan untuk menampilkan judul film dari hasil pencarian.

Pada proses ini digunakan dua metode pengukuran kemiripan, yaitu **Cosine Similarity** dan **Jaccard Similarity**. Cosine Similarity digunakan bersama representasi TF-IDF, sedangkan Jaccard Similarity digunakan bersama representasi binary.

## Langkah-Langkah

### 1. Mempersiapkan Dataset

Dataset `combined.csv` dibaca menggunakan Pandas.

Data yang digunakan berasal dari kolom `description` sebagai dokumen teks dan kolom `title` sebagai identitas film yang akan ditampilkan pada hasil pencarian.

### 2. Membentuk Corpus

Setiap deskripsi film diproses menjadi corpus.

Pada tahap ini dilakukan beberapa preprocessing sederhana, yaitu:

* Mengubah teks menjadi lowercase.
* Menghapus stopwords bahasa Inggris.
* Melakukan stemming menggunakan Porter Stemmer.

Hasil preprocessing kemudian disimpan sebagai corpus yang digunakan pada proses perhitungan similarity.

### 3. Membentuk Representasi TF-IDF

Corpus diubah menjadi representasi numerik menggunakan **TF-IDF Vectorizer**.

Representasi ini digunakan untuk menunjukkan tingkat kepentingan setiap kata dalam masing-masing deskripsi film.

### 4. Memasukkan Query

Sebuah query dimasukkan sebagai teks pencarian.

Contoh query yang digunakan:

`a young man who discovers a mysterious secret`

Query tersebut kemudian diproses menggunakan vectorizer yang sama dengan yang digunakan pada dokumen.

### 5. Menghitung Cosine Similarity

Cosine Similarity digunakan untuk mengukur kemiripan antara vector query dengan vector setiap dokumen film.

Nilai similarity yang semakin mendekati `1` menunjukkan bahwa dokumen memiliki kemiripan yang semakin tinggi dengan query.

Sebaliknya, nilai yang mendekati `0` menunjukkan tingkat kemiripan yang rendah.

### 6. Mengurutkan Hasil Cosine Similarity

Setelah nilai kemiripan diperoleh untuk seluruh dokumen, hasilnya diurutkan dari nilai similarity terbesar ke terkecil.

Kemudian dipilih **10 dokumen dengan nilai similarity tertinggi** sebagai hasil pencarian.

### 7. Menampilkan Hasil Cosine Similarity

Hasil pencarian ditampilkan dalam bentuk tabel yang berisi:

* **Title** → judul film
* **Description** → deskripsi film
* **Similarities** → nilai kemiripan dengan query

Dengan demikian, film yang memiliki deskripsi paling mirip dengan query dapat diketahui berdasarkan nilai Cosine Similarity.

### 8. Membentuk Binary Representation

Selain TF-IDF, corpus juga diubah menjadi representasi binary menggunakan **CountVectorizer** dengan parameter `binary=True`.

Representasi ini menunjukkan keberadaan suatu kata pada setiap dokumen.

Nilai `1` menunjukkan kata terdapat pada dokumen, sedangkan nilai `0` menunjukkan kata tidak terdapat pada dokumen.

### 9. Menghitung Jaccard Similarity

Representasi binary digunakan untuk menghitung **Jaccard Similarity** antara query dan setiap dokumen.

Jaccard Similarity membandingkan kesamaan kata yang muncul pada query dan dokumen.

Semakin tinggi nilai similarity, semakin banyak kata yang sama antara query dengan dokumen tersebut.

### 10. Mengurutkan dan Menampilkan Hasil Jaccard Similarity

Nilai Jaccard Similarity dari seluruh dokumen diurutkan dari yang terbesar hingga terkecil.

Sebanyak **10 film dengan nilai similarity tertinggi** kemudian ditampilkan dalam tabel yang berisi judul, deskripsi, dan nilai kemiripan.

## Metode yang Digunakan

Repository ini menggunakan dua metode utama untuk mengukur kemiripan teks:

1. **Cosine Similarity**
   Digunakan pada representasi TF-IDF untuk mengukur kemiripan berdasarkan arah vektor dokumen dan query.

2. **Jaccard Similarity**
   Digunakan pada representasi binary untuk mengukur kesamaan berdasarkan kata yang muncul pada query dan dokumen.

## Hasil

Hasil akhir berupa **10 film yang paling mirip dengan query** berdasarkan masing-masing metode similarity.

Dengan menggunakan dua metode tersebut, hasil kemiripan teks dapat dibandingkan berdasarkan representasi TF-IDF dan representasi binary.

