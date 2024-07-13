# Geometrix Citra

### 1. Import Library

### 2. Pembacaan Citra

### 3. Penampilan Citra Asli

### 4. Citra Rotated
```
rows, cols = img.shape[:2]
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
M = cv2.getRotationMatrix2D(((cols-1)/2.0, (rows-1)/2.0),45,1)
img_rotated = cv2.warpAffine(img,M,(cols,rows))
```
Pertama-tama, saya mengambil dimensi dari citra saya menggunakan ```img.shape```. Ini akan mengembalikan nilai tinggi, lebar, dan saluran warna dari citra, tetapi saya hanya akan mengambil nilai tinggi (baris) dan lebar (kolom) dari citra dan mengabaikan saluran warnanya dengan menambahkan [:2]. Nilai baris dan kolom ini akan disimpan dalam variabel rows, cols. Sebelum masuk ke rotasi citra, saya mengonversi citra terlebih dahulu dari BGR (format citra default OpenCV) ke RGB menggunakan fungsi ```cvtColor``` dari OpenCV. Untuk rotasi gambarnya, saya memakai fungsi ```getRotationMatrix2D``` di mana parameternya ada titik tengah citra (agar citra seimbang setelah diputar), sudut berputarnya citra sebesar 45 derajat, dan skala penentu bahwa citra tidak diperbesar maupun diperkecil. Lalu, fungsi ```warpAffine``` akan menerapkan transformasi ini ke citra asli. Parameter ketiga (cols, rows) menentukan ukuran keluaran citra yang telah diputar. Hasilnya adalah citra yang telah diputar 45 derajat disimpan dalam variabel img_rotated. 

```
fig,axs = plt.subplots(1, 2, figsize = (15,5))
axs[0].imshow(img)
axs[0].set_title("Citra Asli")
axs[1].imshow(img_rotated)
axs[1].set_title("After Rotated")
```
Setelah itu, citra asli dan citra asli yang sudah dirotasi tadi, saya tampilkan pada dua subplot yang terpisah. 
### 5. Citra Resized
```
img_resized = cv2.resize(img, (img.shape[1] // 3, img.shape[0] // 2))
```
Baris kode ini bertujuan untuk me-resize citra asli tadi menggunakan fungsi ```resize``` dari OpenCV. Caranya adalah dengan mengubah ukurannya menjadi sepertiga dari lebar aslinya citra dan setengah dari tinggi aslinya citra. img.shape[0] adalah nilai tinggi citra, dan img.shape[1] adalah nilai lebar citra.

```
fig, axs = plt.subplots(1, 2, figsize=(15, 5))
axs[0].imshow(img)
axs[0].set_title("Citra Asli")
axs[1].imshow(img_resized)
axs[1].set_title("After Resized")
```
Setelah itu, citra asli dan citra asli yang sudah diresize tadi, saya tampilkan pada dua subplot yang terpisah. 

### 6. Citra Cropped
```
img_cropped = img[0:img.shape[0]//2, 0:img.shape[1]//2]
```
Baris ini akan mengambil (slicing) citra dari baris 0 hingga setengah dari tinggi citra dan kolom 0 hingga setengah dari lebar citra. Maka, citra yang akan diambil adalah bagian kiri atas dari citra asli. Citra cropped ini akan disimpan dalam variabel img_cropped.

```
fig, axs = plt.subplots(1, 2, figsize=(15, 5))
axs[0].imshow(img)
axs[0].set_title("Citra Asli")
axs[1].imshow(img_cropped)
axs[1].set_title("After Cropped")
```
Setelah itu, citra asli dan citra asli yang sudah dicrop tadi, saya tampilkan pada dua subplot yang terpisah. 
### 7. Citra Flipped
```
img_flipped = cv2.flip(img, 1)
```
Baris ini akan mengflip citra asli dengan menggunakan fungsi ```flip``` secara horizontal karena parameternya adalah 1. Citra asli akan mengalami pembalikkan arah dan disimpan dalam variabel img_flipped.
```
fig, axs = plt.subplots(1, 2, figsize=(15, 5))
axs[0].imshow(img)
axs[0].set_title("Citra Asli")
axs[1].imshow(img_flipped)
axs[1].set_title("After Flipped")
```
Setelah itu, citra asli dan citra asli yang sudah diflip tadi, saya tampilkan pada dua subplot yang terpisah. 
### 8. Citra Translated
```
rows, cols = img.shape[:2]
M = np.float32([[1, 0, 50], [0, 1, 25]])
img_translated = cv2.warpAffine(img, M, (cols, rows))
```
Baris kode ini membuat matriks transformasi afine yang digunakan untuk menggeser gambar ke kanan sebanyak 50 piksel dan ke bawah sebanyak 25 piksel. Matriks ini kemudian digunakan dengan fungsi ```warpAffine``` untuk menerapkan translasi ini pada citra.
```
fig, axs = plt.subplots(1, 2, figsize=(15, 5))
axs[0].imshow(img)
axs[0].set_title('Citra Asli')
axs[1].imshow(img_translated)
axs[1].set_title('After Translated')
```
Setelah itu, citra asli dan citra asli yang sudah ditranslasi tadi, saya tampilkan pada dua subplot yang terpisah. 

## Teori Pendukung

