---
title: 'Catatan Belajar Machine Learning'
published: 2025-10-20
draft: false
tags: ['machine-learning', 'artificial-intelligence', 'deep-learning']
description: 'Catatan pribadi saya tentang konsep dasar dan teknik dalam machine learning.'
---

## 1. Apa Itu Model Machine Learning?
**Model machine learning** adalah sebuah **algoritma matematika** yang diubah dalam bentuk **kode program** yang memungkinkan komputer untuk **belajar dari data** dan membuat **prediksi** atau **keputusan tanpa diprogram secara eksplisit** untuk tugas tertentu.

## 2. Pemrograman Tradisional vs Machine Learning
Dalam **pemrograman tradisional**, kita **menulis kode yang secara eksplisit** memberi tahu komputer apa yang harus dilakukan dalam setiap situasi. Namun, dalam **machine learning**, kita memberikan data kepada model dan membiarkannya **menemukan pola dan hubungan dalam data** tersebut.

## 3. Machine Learning vs Deep Learning

**Machine learning** adalah cabang dari kecerdasan buatan yang berfokus pada pengembangan algoritma yang memungkinkan komputer untuk belajar dari data.

Sedangkan **deep learning** adalah subbidang dari machine learning yang menggunakan **jaringan saraf tiruan** dengan banyak lapisan (***deep neural networks***) untuk memodelkan dan memahami pola yang kompleks dalam data.

| Aspek | Machine Learning (ML) | Deep Learning (DL) |
|-------|----------------------|-------------------|
| **Komputasi** | Cenderung ringan | Lebih berat |
| **Kecepatan** | Cenderung cepat | Lebih lambat |
| **Size** | Cenderung kecil | Lebih besar |

## 4. Learning Paradigms dalam Machine Learning
1. **Supervised Learning**: Model dilatih menggunakan data berlabel, di mana input dan output diketahui.
2. **Unsupervised Learning**: Model dilatih menggunakan data tidak berlabel, di mana hanya input yang tersedia.
3. **Semi-Supervised Learning**: Kombinasi dari supervised dan unsupervised learning, di mana model dilatih menggunakan **sejumlah kecil data berlabel** dan sejumlah besar data tidak berlabel.
4. **Reinforcement Learning**: Model belajar melalui interaksi dengan lingkungan, menerima umpan balik dalam bentuk **hadiah** atau **hukuman** (*reward & punishment*).

### 4.1. Supervised Learning
Dalam **supervised learning**, model dilatih menggunakan **data berlabel**, di mana setiap input memiliki output yang diketahui.

Tujuan dari supervised learning adalah agar model dapat **mempelajari hubungan antara input dan output** sehingga dapat membuat **prediksi yang akurat** pada data baru. Setiap pasangan input-output dalam data pelatihan disebut sebagai **contoh pelatihan**.

Input dapat berupa fitur-fitur yang relevan, sedangkan output adalah label atau nilai yang ingin diprediksi oleh model.

![Supervised learning illustraction](./supervised-learning.png 'Supervised learning illustration')
![Algoritma Supervised Learning](./algoritma-supervised-learning.png 'Algoritma Supervised Learning')
![Kontinu & Kategorikal](./kontinyu-kategorikal.png 'Kontinu & Kategorikal')

#### 4.1.1. Regresi

#### 4.1.1.1. Definisi
Hubungan antara **satu atau lebih variable independen** (X, yang memengaruhi) terhadap **satu variable dependen** (Y, yang dipengaruhi).

#### 4.1.1.2. Tujuan
**Memprediksi nilai kontinu** berdasarkan hubungan tersebut.

#### 4.1.1.3. Contoh aplikasi regresi
1. **Pertumbuhan ekonomi (Y)** dipengaruhi oleh:
   1. Jumlah lapangan pekerjaan (X1)
   2. Daya beli masyarakat (X2)
   3. Tingkat inflasi (X3)
   4. Suku bunga (X4)
2. **Suhu udara (Y**) dipengaruhi oleh:
   1. Waktu dalam sehari (X1)
   2. Kelembapan (X2)
   3. Kecepatan angin (X3)
3. **Harga rumah (Y)** dipengaruhi oleh:
   1. Luas bangunan (X1)
   2. Lokasi (X2)
   3. Jumlah kamar tidur (X3)
   4. Usia bangunan (X4)

#### 4.1.1.4. Syarat/Asumsi Penggunaan Model Regresi
1. Data harus terdistribusi normal
2. Tidak ada korelasi antar variabel independen (tidak ada multikolinearitas)

#### 4.1.2. Klasifikasi

Digunakan untuk **mengkategorikan data** ke dalam kelas-kelas tertentu, seperti:
   1. Mengidentifikasi email sebagai spam atau bukan spam.
   2. Mengenali gambar hewan (misalnya kucing vs anjing).


### 4.2. Unsupervised Learning
Dalam **unsupervised learning**, model dilatih menggunakan **data tidak berlabel**, di mana hanya input yang tersedia tanpa output yang diketahui. Tujuan dari unsupervised learning adalah untuk ***menemukan pola, struktur, atau hubungan tersembunyi dalam data***.

Model mencoba mengelompokkan data berdasarkan kemiripan atau menemukan representasi yang lebih sederhana dari data tersebut. Beberapa teknik umum dalam unsupervised learning meliputi **clustering** (pengelompokan) dan **dimensionality reduction** (pengurangan dimensi).

![Unsupervised learning illustration](./unsupervised-learning-pola-hewan.png 'Unsupervised learning illustration')
![Algoritma Unsupervised Learning](./algoritma-unsupervised-learning.png 'Algoritma Unsupervised Learning')

#### 4.2.1. Clustering
**Mengelompokkan** data ke dalam grup **berdasarkan kemiripan**, seperti algoritma K-Means.

#### 4.2.2. Dimensionality Reduction
Mengurangi jumlah fitur dalam data sambil mempertahankan informasi penting, seperti PCA (Principal Component Analysis).

### Semi-Supervised Learning
Dalam **semi-supervised learning**, model dilatih menggunakan kombinasi **data berlabel** dan **data tidak berlabel**. Biasanya, hanya **sebagian kecil dari data yang memiliki label**, sedangkan sebagian besar data tidak berlabel.

Tujuan dari semi-supervised learning adalah untuk **memanfaatkan informasi dari data tidak berlabel untuk meningkatkan kinerja model** yang dilatih dengan data berlabel. Teknik ini berguna **ketika mendapatkan data berlabel mahal atau sulit**, tetapi data tidak berlabel tersedia dalam jumlah besar.

**Contoh aplikasi semi-supervised learning** adalah **Google Photos** yang menggunakan teknik ini untuk mengelompokkan foto berdasarkan wajah orang. Google Photos memiliki **jutaan foto yang tidak berlabel** dari pengguna, tetapi hanya **sebagian kecil foto yang diberi label** oleh pengguna (misalnya dengan menandai nama orang dalam foto).

Model menggunakan **data berlabel** (foto yang sudah ditandai) untuk belajar mengenali wajah tertentu, kemudian **memanfaatkan data tidak berlabel** (jutaan foto lainnya) untuk **meningkatkan akurasi pengenalan wajah** dan mengelompokkan foto-foto serupa. Dengan cara ini, Google Photos dapat **secara otomatis mengelompokkan foto berdasarkan orang** tanpa perlu pengguna menandai setiap foto secara manual.

### Reinforcement Learning
Dalam **reinforcement learning**, model belajar melalui interaksi dengan lingkungan, menerima **umpan balik** dalam bentuk **hadiah** atau **hukuman** (*reward & punishment*). Model mencoba untuk **memaksimalkan total hadiah** yang diterima selama interaksi dengan lingkungan. Teknik ini sering digunakan dalam **permainan**, **robotika**, dan **sistem rekomendasi**.

Model reinforcement learning biasanya terdiri dari **agen** yang mengambil tindakan dalam lingkungan, dan **lingkungan** memberikan umpan balik berdasarkan tindakan tersebut. **Agen belajar untuk memilih tindakan yang menghasilkan hadiah tertinggi** dari waktu ke waktu melalui proses trial-and-error.

![Reinforcement learning illustration](./reinforcement-learning.png 'Reinforcement learning illustration')

## 5. Overfitting
Overfitting terjadi ketika model machine learning **terlalu kompleks** dan **menyesuaikan diri terlalu baik dengan data pelatihan**. Akibatnya, model tersebut memiliki **kinerja yang sangat baik pada data pelatihan** tetapi **buruk pada data baru atau data pengujian**. Hal ini terjadi karena model menangkap **noise** atau **pola acak** dalam data pelatihan yang tidak berlaku untuk data lain.

## 6. Underfitting
Underfitting terjadi ketika model machine learning **terlalu sederhana** dan **tidak dapat menangkap pola yang mendasari data**. Akibatnya, model memiliki **kinerja yang buruk baik pada data pelatihan maupun data baru**.