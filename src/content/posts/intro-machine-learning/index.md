---
title: 'Catatan Belajar Machine Learning'
published: 2025-10-20
draft: false
tags: ['machine-learning', 'artificial-intelligence', 'deep-learning']
description: 'Catatan pribadi saya tentang konsep dasar dan teknik dalam machine learning.'
---

## Apa Itu Model Machine Learning?
**Model machine learning** adalah sebuah **algoritma matematika** yang diubah dalam bentuk **kode program** yang memungkinkan komputer untuk **belajar dari data** dan membuat **prediksi** atau **keputusan tanpa diprogram secara eksplisit** untuk tugas tertentu.

## Pemrograman Tradisional vs Machine Learning
Dalam **pemrograman tradisional**, kita **menulis kode yang secara eksplisit** memberi tahu komputer apa yang harus dilakukan dalam setiap situasi. Namun, dalam **machine learning**, kita memberikan data kepada model dan membiarkannya **menemukan pola dan hubungan dalam data** tersebut.

## Machine Learning vs Deep Learning

**Machine learning** adalah cabang dari kecerdasan buatan yang berfokus pada pengembangan algoritma yang memungkinkan komputer untuk belajar dari data.

Sedangkan **deep learning** adalah subbidang dari machine learning yang menggunakan **jaringan saraf tiruan** dengan banyak lapisan (***deep neural networks***) untuk memodelkan dan memahami pola yang kompleks dalam data.

| Aspek | Machine Learning (ML) | Deep Learning (DL) |
|-------|----------------------|-------------------|
| **Komputasi** | Cenderung ringan | Lebih berat |
| **Kecepatan** | Cenderung cepat | Lebih lambat |
| **Size** | Cenderung kecil | Lebih besar |

## Learning Paradigms dalam Machine Learning
1. **Supervised Learning**: Model dilatih menggunakan data berlabel, di mana input dan output diketahui.
2. **Unsupervised Learning**: Model dilatih menggunakan data tidak berlabel, di mana hanya input yang tersedia.
3. **Semi-Supervised Learning**: Kombinasi dari supervised dan unsupervised learning, di mana model dilatih menggunakan **sejumlah kecil data berlabel** dan sejumlah besar data tidak berlabel.
4. **Reinforcement Learning**: Model belajar melalui interaksi dengan lingkungan, menerima umpan balik dalam bentuk **hadiah** atau **hukuman** (*reward & punishment*).

### Supervised Learning
Dalam **supervised learning**, model dilatih menggunakan **data berlabel**, di mana setiap input memiliki output yang diketahui.

Tujuan dari supervised learning adalah agar model dapat **mempelajari hubungan antara input dan output** sehingga dapat membuat **prediksi yang akurat** pada data baru. Setiap pasangan input-output dalam data pelatihan disebut sebagai **contoh pelatihan**.

Input dapat berupa fitur-fitur yang relevan, sedangkan output adalah label atau nilai yang ingin diprediksi oleh model.

![Supervised learning illustraction](./supervised-learning.png 'Supervised learning illustration')

### Unsupervised Learning
Dalam **unsupervised learning**, model dilatih menggunakan **data tidak berlabel**, di mana hanya input yang tersedia tanpa output yang diketahui. Tujuan dari unsupervised learning adalah untuk ***menemukan pola, struktur, atau hubungan tersembunyi dalam data***.

Model mencoba mengelompokkan data berdasarkan kemiripan atau menemukan representasi yang lebih sederhana dari data tersebut. Beberapa teknik umum dalam unsupervised learning meliputi **clustering** (pengelompokan) dan **dimensionality reduction** (pengurangan dimensi).

![Unsupervised learning illustration](./unsupervised-learning-pola-hewan.png 'Unsupervised learning illustration')

### Semi-Supervised Learning
Dalam **semi-supervised learning**, model dilatih menggunakan kombinasi **data berlabel** dan **data tidak berlabel**. Biasanya, hanya **sebagian kecil dari data yang memiliki label**, sedangkan sebagian besar data tidak berlabel.

Tujuan dari semi-supervised learning adalah untuk **memanfaatkan informasi dari data tidak berlabel untuk meningkatkan kinerja model** yang dilatih dengan data berlabel. Teknik ini berguna **ketika mendapatkan data berlabel mahal atau sulit**, tetapi data tidak berlabel tersedia dalam jumlah besar.

**Contoh aplikasi semi-supervised learning** adalah **Google Photos** yang menggunakan teknik ini untuk mengelompokkan foto berdasarkan wajah orang. Google Photos memiliki **jutaan foto yang tidak berlabel** dari pengguna, tetapi hanya **sebagian kecil foto yang diberi label** oleh pengguna (misalnya dengan menandai nama orang dalam foto).

Model menggunakan **data berlabel** (foto yang sudah ditandai) untuk belajar mengenali wajah tertentu, kemudian **memanfaatkan data tidak berlabel** (jutaan foto lainnya) untuk **meningkatkan akurasi pengenalan wajah** dan mengelompokkan foto-foto serupa. Dengan cara ini, Google Photos dapat **secara otomatis mengelompokkan foto berdasarkan orang** tanpa perlu pengguna menandai setiap foto secara manual.

### Reinforcement Learning
Dalam **reinforcement learning**, model belajar melalui interaksi dengan lingkungan, menerima **umpan balik** dalam bentuk **hadiah** atau **hukuman** (*reward & punishment*). Model mencoba untuk **memaksimalkan total hadiah** yang diterima selama interaksi dengan lingkungan. Teknik ini sering digunakan dalam **permainan**, **robotika**, dan **sistem rekomendasi**.

Model reinforcement learning biasanya terdiri dari **agen** yang mengambil tindakan dalam lingkungan, dan **lingkungan** memberikan umpan balik berdasarkan tindakan tersebut. **Agen belajar untuk memilih tindakan yang menghasilkan hadiah tertinggi** dari waktu ke waktu melalui proses trial-and-error.

![Reinforcement learning illustration](./reinforcement-learning.png 'Reinforcement learning illustration')
