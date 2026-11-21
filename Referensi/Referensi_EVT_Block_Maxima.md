# Referensi VaR dengan EVT Block Maxima

Tanggal penelusuran: 12 November 2026. Pencarian menggunakan kata kunci "value at risk", "block maxima", "generalized extreme value", dan "saham". Identitas serta kesesuaian metode diperiksa melalui laman jurnal; teks lengkap diperiksa untuk Najamuddin dkk. dan Ambarsari dkk.

## 1. Acuan utama: analisis per saham

Najamuddin, F. F., Herdiani, E. T., & Jaya, A. K. (2024). Value at Risk Estimation Using Extreme Value Theory Approach in Indonesia Stock Exchange. *BAREKENG: Jurnal Ilmu Matematika dan Terapan, 18*(2), 695–706.

- DOI: https://doi.org/10.30598/barekengvol18iss2pp0695-0706
- Laman jurnal: https://ojs3.unpatti.ac.id/index.php/barekeng/article/view/10373
- PDF lokal: [Najamuddin_2024_VaR_EVT.pdf](Artikel_EVT_BM/Najamuddin_2024_VaR_EVT.pdf)
- Objek: HMSP, ICBP, INDF, dan UNVR, 1 Februari 2017–31 Januari 2023.
- Metode: membandingkan BM–GEV dengan POT–GPD; blok berisi lima observasi perdagangan; estimasi parameter menggunakan MLE; backtesting memakai Z statistic.
- Bagian penting: 2.2–2.8 untuk return, BM, estimasi parameter, kesesuaian distribusi, dan VaR; bagian 3.3 untuk penerapan BM.
- Kesesuaian proyek: acuan paling dekat untuk perbandingan risiko tiga saham secara individual.
- Perbedaan: persamaan (1) menggunakan simple return. Notebook proyek menggunakan log return sesuai permintaan, sehingga merupakan adaptasi metode dan tidak diharapkan mereproduksi angka artikel.

## 2. Acuan BM–GEV pada portofolio

Ayuni, N., Rizki, S. W., & Perdana, H. (2020). Analisis Risiko Portofolio LQ45 Menggunakan Pendekatan Value at Risk Block Maxima-Generalized Extreme Value. *Bimaster: Buletin Ilmiah Matematika, Statistika dan Terapannya, 9*(2).

- DOI: https://doi.org/10.26418/bbimst.v9i2.39914
- Laman jurnal: https://jurnal.untan.ac.id/index.php/jbmstr/article/view/39914
- PDF daring: https://jurnal.untan.ac.id/index.php/jbmstr/article/view/39914/75676585484
- Objek: portofolio PTBA, ANTM, PGAS, BBCA, dan ICBP, periode 2018.
- Metode: BM dengan distribusi GEV untuk estimasi VaR portofolio.
- Kesesuaian proyek: referensi pendamping bila analisis selanjutnya dikembangkan menjadi portofolio TLKM, EXCL, dan ISAT.
- Status pemeriksaan: identitas dan metode diperiksa melalui laman jurnal; bagian studi kasus PDF juga ditinjau melalui penelusuran daring. Unduhan langsung PDF ke direktori lokal ditolak server dengan HTTP 403.

## 3. Acuan tambahan dengan pemodelan volatilitas

Ambarsari, A., Sudarno, & Tarno. (2016). Perbandingan Pendekatan Generalized Extreme Value dan Generalized Pareto Distribution untuk Perhitungan Value at Risk pada Portofolio Saham. *Jurnal Gaussian, 5*(3), 361–371.

- DOI: https://doi.org/10.14710/j.gauss.5.3.361-371
- Laman jurnal: https://ejournal3.undip.ac.id/index.php/gaussian/article/view/14692
- PDF lokal: [Ambarsari_2016_GEV_GPD_Portofolio.pdf](Artikel_EVT_BM/Ambarsari_2016_GEV_GPD_Portofolio.pdf)
- Objek: saham Astra International dan Panin Financial, 1 Januari 2010–22 Januari 2016.
- Metode: membandingkan BM–GEV dan POT–GPD pada portofolio, dengan pembahasan ARIMA dan GARCH untuk volatilitas.
- Kesesuaian proyek: referensi tambahan bila dependensi waktu dan perubahan volatilitas perlu ditangani sebelum pemodelan ekstrem.
- Batas penggunaan: alur dengan model volatilitas memerlukan tahapan tambahan dibandingkan BM langsung pada return. Notebook awal belum menerapkan pemodelan tersebut.

## 4. Keputusan dan pemeriksaan untuk tahap berikutnya

Catatan berikut merupakan pertimbangan metodologis proyek, bukan kesimpulan empiris notebook.

- Analisis awal dilakukan per saham; pembentukan dan pembobotan portofolio belum ditentukan.
- Definisikan kerugian log sebagai `L_t = -r_t` sebelum mengambil maksimum blok agar ekor yang dimodelkan merepresentasikan kerugian posisi long. Maksimum return positif merepresentasikan keuntungan ekstrem.
- Notebook lengkap memakai blok tidak tumpang tindih sepanjang lima observasi perdagangan; blok tidak lengkap di akhir periode estimasi dikeluarkan. Pemeriksaan sensitivitas memakai panjang 10 dan 21 observasi tanpa mengubah model utama berdasarkan hasil pengujian.
- Bedakan kuantil distribusi maksimum blok dengan kuantil kerugian harian; konversinya harus menjelaskan asumsi dependensi serta horizon VaR.
- Notebook lengkap memakai tingkat kepercayaan 95% dan 99%, estimasi statis pada return 2020–2024, serta backtesting Kupiec pada return 2025 dengan signifikansi 5%. Ambang VaR tidak diperbarui selama periode pengujian.
- Notebook mempertahankan observasi ekstrem dan tidak melakukan winsorization, interpolasi, atau pengisian harga hilang.

## 5. Sumber data dan aksi korporasi

- [Dokumentasi yfinance.download](https://ranaroussi.github.io/yfinance/reference/api/yfinance.download.html): parameter tanggal akhir bersifat eksklusif. Pengambilan memakai `start="2020-01-01"`, `end="2026-01-01"`, `auto_adjust=False`, dan `actions=True`; log return dihitung dari `Adj Close`.
- [KSEI: jadwal stock split ISAT](https://www.ksei.co.id/Announcement/Files/ISAT_MCONV_20241015_ID.pdf): rasio 1:4; perdagangan dengan nominal baru di pasar reguler mulai 14 Oktober 2024. Harga historis dari penyedia dapat sudah disesuaikan terhadap split; hindari menerapkan penyesuaian split kedua kali secara manual.
- [XLSMART: keterbukaan informasi](https://www.xlsmart.co.id/id/tata-kelola/aksi-perusahaan?tab=disclosure): terdapat penggabungan usaha pada April 2025. Seri EXCL melintasi perubahan perusahaan; konteks ini perlu dicatat saat menafsirkan keseluruhan periode.
- Basis `Adj Close` mencakup penyesuaian dividen serta split menurut penyedia. Pilihan basis harga ini perlu dinyatakan pada laporan dan dibedakan dari return yang hanya menggunakan harga penutupan.
- Cache harga tersedia di `Analisis/data/`; harga historis dapat direvisi penyedia. Notebook membaca CSV harga lokal secara langsung; pengunduhan ulang tidak menjadi bagian dari alur analisis.
