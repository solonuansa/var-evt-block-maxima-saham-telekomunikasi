# Estimasi Value at Risk Saham Telekomunikasi dengan EVT Block Maxima

Proyek ini mengestimasi dan membandingkan risiko kerugian harian saham TLKM, ISAT, dan EXCL menggunakan *Value at Risk* (VaR) pada tingkat kepercayaan 95% dan 99%.

## Data dan Metodologi

Analisis memakai harga penutupan yang telah disesuaikan (*Adj Close*) dari Yahoo Finance untuk 2019–2025. Harga TLKM yang kosong pada 19 Juni 2019 direkonstruksi dari harga penutupan yang dilaporkan Profindo.

Periode estimasi 2019–2024 mencakup 1.455 return harian per saham. Metode *Block Maxima* mengambil kerugian terbesar dari setiap blok lima observasi, lalu memodelkannya dengan distribusi *Generalized Extreme Value* (GEV). Periode backtesting 2025 mencakup 236 observasi per saham dan memakai uji Kupiec serta Christoffersen.

## Hasil

| Saham | VaR 95% | VaR 99% | Exception 95% | Exception 99% |
| --- | ---: | ---: | ---: | ---: |
| TLKM | 2,71% | 4,29% | 18 | 6 |
| ISAT | 4,25% | 6,76% | 16 | 4 |
| EXCL | 3,61% | 5,73% | 5 | 1 |

ISAT memiliki VaR tertinggi pada kedua tingkat kepercayaan, diikuti EXCL dan TLKM. Uji gabungan Christoffersen pada taraf signifikansi 5% hanya menolak hasil TLKM pada VaR 99% (*p* = 0,0430).