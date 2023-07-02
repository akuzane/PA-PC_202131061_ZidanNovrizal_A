# PROJEK AKHIR PENGOLAHAN CITRA - A

Pada project akhir ini, Saya Zidan Novrizal dengan NIM 202131061 akan menjelaskan jalannya program dengan ketentuan project yaitu "Deteksi Gambar Contour"

sebelum masuk ke tahapan program bekerja, disini saya ingin memberikan ringkasan mengenai teori yang mendukung mengenai projek terkait

## Deteksi Gambar Kontur 
adalah proses identifikasi dan pemisahan objek dari latar belakang dalam sebuah gambar berdasarkan perbedaan intensitas atau tekstur. Tujuannya adalah untuk mengidentifikasi tepi dan garis-garis yang membentuk objek dalam gambar.

Proses deteksi gambar kontur umumnya melibatkan beberapa langkah, seperti:

1. Pra-pemrosesan: Gambar diolah terlebih dahulu untuk menghilangkan noise atau gangguan yang tidak diinginkan. Hal ini dapat dilakukan dengan teknik seperti penghalusan atau pengurangan noise.

2. Peningkatan kontras: Kontras gambar ditingkatkan untuk memperjelas perbedaan intensitas antara objek dan latar belakang. Ini dapat dilakukan dengan menggunakan teknik seperti peningkatan histogram atau filter penajaman.

3. Segmentasi: Gambar dibagi menjadi beberapa bagian yang terkait dengan objek menggunakan algoritma segmentasi. Metode segmentasi yang umum digunakan adalah metode berbasis intensitas atau berbasis warna.

4. Deteksi tepi: Tepi dan garis-garis dalam gambar diidentifikasi menggunakan operator deteksi tepi seperti Operator Sobel, Operator Canny, atau Operator Prewitt. Operator ini memperhatikan perbedaan intensitas di sekitar setiap piksel untuk menemukan perubahan yang signifikan.

5. Penyaringan kontur: Kontur yang terdeteksi dapat diperbaiki atau dihaluskan untuk menghilangkan noise atau detail yang tidak diinginkan. Ini dapat dilakukan dengan menggunakan teknik seperti morfologi matematika atau penyaringan Gaussian.

6. Pengklasifikasian kontur: Kontur yang dihasilkan kemudian diklasifikasikan menjadi kontur utama (kontur objek yang diinginkan) dan kontur tambahan (kontur yang tidak relevan atau noise). Hal ini dapat dilakukan dengan menggunakan metode pengklasifikasi seperti pendekatan geometri atau pendekatan berbasis fitur.

Deteksi gambar kontur memiliki banyak aplikasi, termasuk pengenalan pola, deteksi objek, segmentasi gambar, pengenalan wajah, pengolahan citra medis, dan lain sebagainya. Dengan deteksi gambar kontur, kita dapat mengidentifikasi dan memisahkan objek dari latar belakang dengan lebih baik, memungkinkan berbagai analisis dan pengolahan lebih lanjut pada gambar tersebut.

## Penjelasan Program
Berikut ini merupakan penjelasan dari tahapan program pada repository ini

### 1. Import Library
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
Mengimport library yang diperlukan, yaitu cv2 dari OpenCV dan numpy serta matplotlib.pyplot dari Matplotlib.

### 2. Deklarasi Variabel yang dibutuhkan
```python
gambar = cv2.imread('gambar.jpg')
```
Menggunakan fungsi cv2.imread() untuk membaca gambar dengan nama 'gambar.jpg' dan menyimpannya ke dalam variabel gambar.

### 3. Konversi gambar ke skala abu-abu
```python
abu_abu = cv2.cvtColor(gambar, cv2.COLOR_BGR2GRAY)
```
Menggunakan fungsi cv2.cvtColor() untuk mengonversi gambar dari format BGR (default OpenCV) menjadi skala abu-abu menggunakan konstanta cv2.COLOR_BGR2GRAY. Hasil konversi disimpan dalam variabel abu_abu.

### 4. Operasi deteksi tepi pada gambar
```python
tanda_tepi = cv2.Canny(abu_abu, 30, 150)
```
Menggunakan fungsi cv2.Canny() untuk melakukan operasi deteksi tepi pada gambar dengan parameter threshold minimum 30 dan threshold maksimum 150. Hasil operasi disimpan dalam variabel tanda_tepi.

### 5. Mencari kontur pada gambar
```python
kontur, _ = cv2.findContours(tanda_tepi, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
```
Menggunakan fungsi cv2.findContours() untuk mencari kontur pada gambar dengan menggunakan mode cv2.RETR_EXTERNAL yang mengembalikan kontur eksternal saja, dan metode cv2.CHAIN_APPROX_SIMPLE yang mengkompres kontur dengan hanya menyimpan titik-titik ekstrem. Hasil kontur disimpan dalam variabel kontur.

### 6. Salinan gambar asli
```python
gambar_asli = np.copy(gambar)
```
Membuat salinan gambar asli dengan menggunakan fungsi np.copy() untuk menghindari modifikasi langsung pada gambar asli.

### 7. Gambar kontur pada gambar asli
```python
cv2.drawContours(gambar_asli, kontur, -1, (0, 0, 255), 3)
```
Baris kode cv2.drawContours(gambar_asli, kontur, -1, (0, 0, 255), 3) digunakan untuk menggambar kontur pada gambar asli.

### 8. Salinan gambar asli dengan latar belakang putih
```python
gambar_putih = np.ones_like(gambar) * 255
```
Membuat salinan gambar asli dengan latar belakang putih dengan menggunakan fungsi np.ones_like() untuk membuat array dengan ukuran yang sama dengan gambar asli dan diisi dengan nilai 255 (putih).

### 9. Pendeklarasian Subplots
```python
fig, ax = plt.subplots(1, 3, figsize=(15, 11))
```
Membuat subplot dengan ukuran 1x3 (satu baris, tiga kolom) menggunakan plt.subplots().

### 10. Menampilkan hasil gambar dengan Subplots
```python
# Menampilkan gambar asli pada subplot pertama
ax[0].imshow(cv2.cvtColor(gambar, cv2.COLOR_BGR2RGB))
ax[0].set_title('Gambar Asli')

# Menampilkan gambar dengan kontur pada subplot kedua
ax[1].imshow(cv2.cvtColor(gambar_putih, cv2.COLOR_BGR2RGB))
ax[1].set_title('Gambar dengan Kontur(1)')

# Menampilkan gambar kontur pada latar belakang putih pada subplot ketiga
ax[2].imshow(cv2.cvtColor(gambar_asli, cv2.COLOR_BGR2RGB))
ax[2].set_title('Gambar dengan Kontur(2)')
```
Menampilkan gambar menggunakan subplots yang sudah dideklarasikan.

## Sumber

[LearnOpenCV - Contour Detection](https://learnopencv.com/contour-detection-using-opencv-python-c/)
