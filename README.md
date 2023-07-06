# PROJEK AKHIR PENGOLAHAN CITRA - A

Pada project akhir ini, Saya Zidan Novrizal dengan NIM 202131061 akan menjelaskan jalannya program dengan ketentuan project yaitu "Deteksi Gambar Contour"

Repository ini berisi implementasi algoritma deteksi kontur pada gambar menggunakan Jupyter Notebook dengan menggunakan beberapa teknologi dan dan alat untuk membantu menjalankan dan memahami kode yang ada.

sebelum masuk ke tahapan Instalasi, Teknologi dan Penjelasan kode program, disini saya ingin memberikan ringkasan mengenai teori yang mendukung mengenai projek terkait

```python
"Program hanya bisa mendeteksi objek yang memiliki 4 sudut(persegi)"
```

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

## Penggunaan Jupyter Notebook

1. Pastikan Anda memiliki Python dan Jupyter Notebook terinstal di komputer Anda. Jika belum, Anda dapat menginstalnya menggunakan pip (package manager Python) dengan menjalankan perintah berikut:
```bash
pip install jupyter notebook
```

2. Clone repository ini ke komputer Anda menggunakan perintah berikut:
```bash
git clone https://github.com/akuzane/PA-PC_202131061_ZidanNovrizal_A
```

3. Buka terminal atau command prompt, arahkan ke direktori repository yang telah Anda clone, dan jalankan perintah berikut untuk memulai Jupyter Notebook:
```bash
jupyter notebook
```

4. Jupyter Notebook akan terbuka di browser Anda. Navigasikan ke direktori repository dan buka file Jupyter Notebook dengan ekstensi .ipynb.
```bash
git clone https://github.com/akuzane/PA-PC_202131061_ZidanNovrizal_A
```

5. Di dalam Jupyter Notebook, Anda akan menemukan langkah-langkah deteksi gambar kontur yang dijelaskan dengan komentar dan kode Python. Anda dapat menjalankan setiap sel kode dengan menekan tombol Shift + Enter.

6. Ikuti instruksi yang ada dalam Jupyter Notebook untuk melihat hasil deteksi gambar kontur.

## Teknologi yang Digunakan
<br>
<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" height="60" alt="python logo"  />
  <img width="16" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/jupyter/jupyter-original.svg" height="60" alt="jupyter logo"  />
  <img width="16" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/opencv/opencv-original.svg" height="60" alt="opencv logo"  />
  <img width="16" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/numpy/numpy-original.svg" height="60" alt="numpy logo"  />
</div>
<br>

[Python](https://www.python.org/) merupakan bahasa pemrograman yang digunakan untuk menulis kode dalam [Jupyter Notebook](https://jupyter.org/), [OpenCV](https://opencv.org/) merupakan Library komputer visi yang digunakan untuk melakukan deteksi kontur pada gambar. [Numpy](https://numpy.org/) adalah Library Python yang digunakan untuk operasi matriks dan array numerik. dan [Matplotlib](https://matplotlib.org/) Library Python yang digunakan untuk memvisualisasikan gambar dan hasil deteksi kontur.

Pastikan Anda memiliki pengetahuan dasar tentang Python, Jupyter Notebook, OpenCV, NumPy, dan Matplotlib untuk memahami dan mengikuti kode dalam repository ini.

## Penjelasan Program
Berikut ini merupakan penjelasan dari tahapan program pada repository ini

1. **Import Library**
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
Mengimport library yang diperlukan, yaitu cv2 dari OpenCV dan numpy serta matplotlib.pyplot dari Matplotlib.

2. **Deklarasi Variabel yang dibutuhkan**
```python
gambar = cv2.imread('gambar.jpg')
```
Menggunakan fungsi cv2.imread() untuk membaca gambar dengan nama 'gambar.jpg' dan menyimpannya ke dalam variabel gambar.

3. **Konversi gambar ke skala abu-abu**
```python
abu_abu = cv2.cvtColor(gambar, cv2.COLOR_BGR2GRAY)
```
Menggunakan fungsi cv2.cvtColor() untuk mengonversi gambar dari format BGR (default OpenCV) menjadi skala abu-abu menggunakan konstanta cv2.COLOR_BGR2GRAY. Hasil konversi disimpan dalam variabel abu_abu.

4. **Operasi deteksi tepi pada gambar**
```python
tanda_tepi = cv2.Canny(abu_abu, 30, 150)
```
Menggunakan fungsi cv2.Canny() untuk melakukan operasi deteksi tepi pada gambar dengan parameter threshold minimum 30 dan threshold maksimum 150. Hasil operasi disimpan dalam variabel tanda_tepi.

5. **Mencari kontur pada gambar**
```python
kontur, _ = cv2.findContours(tanda_tepi, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
```
Menggunakan fungsi cv2.findContours() untuk mencari kontur pada gambar dengan menggunakan mode cv2.RETR_EXTERNAL yang mengembalikan kontur eksternal saja, dan metode cv2.CHAIN_APPROX_SIMPLE yang mengkompres kontur dengan hanya menyimpan titik-titik ekstrem. Hasil kontur disimpan dalam variabel kontur.

6. **Salinan gambar asli**
```python
gambar_asli = np.copy(gambar)
```
Membuat salinan gambar asli dengan menggunakan fungsi np.copy() untuk menghindari modifikasi langsung pada gambar asli.

7. **Gambar kontur pada gambar asli**
```python
cv2.drawContours(gambar_asli, kontur, -1, (0, 0, 255), 3)
```
Baris kode cv2.drawContours(gambar_asli, kontur, -1, (0, 0, 255), 3) digunakan untuk menggambar kontur pada gambar asli.

8. **Salinan gambar asli dengan latar belakang putih**
```python
gambar_putih = np.ones_like(gambar) * 255
```
Membuat salinan gambar asli dengan latar belakang putih dengan menggunakan fungsi np.ones_like() untuk membuat array dengan ukuran yang sama dengan gambar asli dan diisi dengan nilai 255 (putih).

9. **Melakukan deteksi bentuk objek/benda**
```python
# Deteksi bentuk benda
for cnt in kontur:
    
    # Menghitung jumlah sudut pada kontur
    sudut = cv2.approxPolyDP(cnt, 0.04 * cv2.arcLength(cnt, True), True)
    jumlah_sudut = len(sudut)
    
    # Deteksi bentuk persegi
    if jumlah_sudut == 4:
        cv2.drawContours(gambar_putih, [cnt], -1, (0, 0, 255), 2)
        cv2.drawContours(gambar_asli, [cnt], -1, (0, 0, 255), 2)
```
Pada setiap kontur, menghitung jumlah sudut menggunakan cv2.approxPolyDP(). Metode ini menggunakan pendekatan kurva untuk mengaproksimasi bentuk kontur. Hasilnya disimpan dalam variabel sudut.

Menghitung jumlah sudut dengan menggunakan len(sudut) dan menyimpannya dalam variabel jumlah_sudut.

Jika jumlah sudut adalah 4, artinya kontur memiliki 4 sudut dan merupakan bentuk persegi. Kemudian, menggunakan cv2.drawContours(), kontur tersebut digambar pada gambar_putih dan gambar_asli dengan warna (0, 0, 255) dan ketebalan 2.

10. **Flip gambar pada kontur latar belakang putih**
```python
gambar_putih_flip = cv2.flip(gambar_putih, 0)
```
Melakukan flipping (pemutarbalikan) pada gambar_putih menggunakan cv2.flip() dengan parameter 0 untuk melakukan flipping secara vertikal. Hasilnya disimpan dalam variabel gambar_putih_flip.

11. **Pendeklarasian Subplots**
```python
# Menampilkan gambar dalam subplot
fig, ax = plt.subplots(1, 3, figsize=(15, 10))
```
Membuat subplots dengan menggunakan plt.subplots() dengan 1 baris dan 3 kolom, dan mengatur ukuran plot dengan figsize=(15, 10). Hasilnya disimpan dalam variabel fig dan ax.

12. **Menampilkan hasil gambar dengan Subplots**
```python
# Menampilkan gambar asli pada subplot pertama
ax[0].imshow(cv2.cvtColor(gambar, cv2.COLOR_BGR2RGB))
ax[0].set_title('Gambar Asli')

# Menampilkan gambar kontur pada latar belakang putih pada subplot ketiga
ax[1].imshow(cv2.cvtColor(gambar_putih_flip, cv2.COLOR_BGR2RGB))
ax[1].set_title('Kontur dengan Latar Belakang Putih')

# Menampilkan gambar dengan bentuk benda yang terdeteksi pada subplot kedua
ax[2].imshow(cv2.cvtColor(gambar_asli, cv2.COLOR_BGR2RGB))
ax[2].set_title('Gambar dengan Bentuk Benda Terdeteksi')
```
Menampilkan gambar menggunakan subplots yang sudah dideklarasikan.

## Sumber
[LearnOpenCV - Contour Detection](https://learnopencv.com/contour-detection-using-opencv-python-c/)
[LearnOpenCV - Approxpolydp](https://www.educba.com/opencv-approxpolydp/)
