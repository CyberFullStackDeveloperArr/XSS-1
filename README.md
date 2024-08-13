# XSS - 1

| Cross Site Scripting |
|---------|
|<div style="text-align:justify;">XSS (Cross Site Scripting) adalah jenis serangan keamanan pada aplikasi web di mana penyerang memasukkan kode berbahaya (biasanya dalam bentuk skrip) ke dalam halaman web yang kemudian dieksekusi oleh browser pengguna lain. Serangan ini memanfaatkan kelemahan validasi input pada aplikasi web yang memungkinkan kode berbahaya tersebut disuntikkan ke dalam halaman web yang dianggap aman oleh pengguna.</div>  |

1. xss
```
<image/src/onerror=prompt(8)>
```
> **Penjelasan: 1**
> - **&lt;image&gt;** Dalam HTML yang valid, tag ini seharusnya adalah &lt;img&gt; Jika menggunakan tag yang tidak valid seperti &lt;image&gt;, browser mungkin mengabaikannya atau mencoba menginterpretasikannya sebagai tag gambar yang salah.

> - Atribut **src** Biasanya, atribut ini berisi URL gambar yang ingin ditampilkan. Namun, dalam kasus XSS, src mungkin kosong atau diatur ke URL yang tidak valid sehingga menyebabkan kesalahan pemuatan gambar.

> - Atribut **onerror** Digunakan untuk menangani kesalahan saat gambar tidak dapat dimuat. Dengan menyuntikkan JavaScript dalam atribut ini, penyerang dapat mengeksekusi skrip jahat ketika terjadi kesalahan.

> - Fungsi **prompt(8)** Ini akan memunculkan kotak dialog yang meminta input dari pengguna dengan pesan 8. Fungsi ini digunakan untuk menguji apakah skrip jahat berhasil dieksekusi dan bisa menampilkan data atau melakukan tindakan lainnya.

2. xss
```
<img/src/onerror=prompt(8)>
```
> **Penjelasan: 2**
> - **&lt;img&gt;** adalah tag HTML yang valid dan digunakan untuk gambar.

> - **img/src/onerror=prompt(8)**  Ini adalah teknik XSS yang efektif menggunakan tag &lt;img&gt; yang valid untuk memanfaatkan atribut onerror dan menjalankan JavaScript.

3. xss
```
<image src/onerror=prompt(8)>
```
> **Penjelasan: 3**
> - src/onerror=prompt(8) menunjukkan bahwa ada spasi antara src dan onerror. Ini membuat src dianggap sebagai atribut dengan nilai kosong dan onerror menjadi atribut dengan nilai prompt(8).

4. xss
```
<img src/onerror=prompt(8)>
```
> **Penjelasan: 4**
> - Ini adalah payload XSS yang valid. Dalam hal ini, src adalah atribut dari elemen **&lt;img&gt;**, dan onerror adalah atribut event handler yang digunakan untuk menjalankan JavaScript ketika terjadi kesalahan pemuatan gambar.
> - Karena tidak ada nilai yang diberikan untuk src, browser akan mencoba memuat gambar tetapi akan gagal, yang kemudian memicu event onerror dan menjalankan prompt(8).

5. xss
```
<image src =q onerror=prompt(8)>
```
> **Penjelasan: 5**
> - Dalam kasus ini, src diberi nilai q, yang biasanya tidak valid karena q bukan URL gambar yang valid. Namun, karena src yang tidak valid atau kosong, ini dapat menyebabkan kesalahan saat mencoba memuat gambar, memicu event onerror.

6. xss
```
<img src="ghost.jpg" onerror="alert('XSS Attack')">
```
> **Penjelasan: 6**
> - Atribut src menentukan sumber gambar. Dalam contoh ini, src diatur ke ghost.jpg, yang mengacu pada file gambar yang tidak ada (karena file tersebut invalid atau tidak ditemukan). Tujuan dari pengaturan ini adalah untuk memicu event onerror karena gambar tidak dapat dimuat.

> - alert('XSS Attack'): Ini adalah kode JavaScript yang dijalankan ketika onerror dipicu. Dalam hal ini, alert('XSS Attack') adalah fungsi JavaScript yang menampilkan kotak dialog peringatan dengan pesan "XSS Attack".


| Ghost Code Night |
|---------|
|<div style="text-align:justify;">Contoh eksploitasi XSS yang disertakan dalam dokumentasi ini hanya untuk **tujuan pendidikan dan pembelajaran**, jika ada seseorang yang menggunakan hal ini untuk tujuan yang tidak baik, atau melanggar aturan/etika **kami tidak bertaggung jawab**, xss adalah kerentanan keamanan yang memungkinkan penyerang menyuntikkan skrip berbahaya ke dalam situs web. Tujuan dari contoh ini adalah untuk **memahami** bagaimana serangan ini bekerja dan bagaimana melindungi aplikasi Anda dari potensi risiko.</div>  |

- **HARAP DI INGAT**
- Jangan gunakan teknik ini pada sistem atau aplikasi tanpa izin
- Jangan Di gunakan untuk kejahatan
- Bijak Lah
- Berbuat Baik lah 
- Setiap Perbuatan Pasti Ada Balasannya
- Jangan Lupa Bersyukur