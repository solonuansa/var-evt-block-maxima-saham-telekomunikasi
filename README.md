# Estimasi Value at Risk Saham Telekomunikasi dengan EVT Block Maxima

Proyek Manajemen Risiko ini mengestimasi Value at Risk (VaR) harian pada tingkat kepercayaan 95% dan 99% untuk TLKM, ISAT, dan EXCL. Metode *Block Maxima* mengambil kerugian terbesar dari setiap blok lima hari perdagangan, lalu memodelkannya dengan distribusi *Generalized Extreme Value* (GEV).

| Periode | Tahun | Penggunaan |
| --- | --- | --- |
| Estimasi | 2019–2024 | Mengestimasi parameter GEV dan menghitung VaR harian. |
| Backtesting | 2025 | Membandingkan ambang VaR tetap dengan kerugian aktual dan mengevaluasi *exception* melalui uji Kupiec dan Christoffersen. |

## Menjalankan analisis

Buka [notebook revisi](Analisis/Analisis_VaR_EVT_BM_TLKM_EXCL_ISAT_2019_2025_simple_return_R_revisi.ipynb) di Jupyter dengan kernel R (`IRkernel`). Pasang paket `quantmod`, `evd`, `extRemes`, `moments`, `ggplot2`, `dplyr`, dan `tidyr`, lalu jalankan sel secara berurutan. Notebook mengunduh input harga dan volume dari Yahoo Finance.

Output revisi tersimpan di notebook. Folder `Analisis/data` memuat salinan historis data Yahoo, `Analisis/output` memuat tabel hasil versi sebelumnya, dan `Referensi` memuat acuan metode serta pedoman tugas.
