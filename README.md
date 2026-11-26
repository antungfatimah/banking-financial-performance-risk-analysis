# Banking Financial Performance & Risk Analysis

Analisis eksploratif kinerja dan risiko industri perbankan Indonesia berdasarkan empat indikator utama: **NPL** (kredit bermasalah), **ROA** (profitabilitas), **CAR** (kecukupan modal), dan **LDR** (likuiditas). Data bulanan agregat Januari 2018 sampai Juni 2025 (90 bulan).

![Dashboard](screenshot_dashboard.png)
<!-- TODO: simpan dashboard_perbankan.png sebagai screenshot_dashboard.png -->

## Isi repositori

| Berkas | Keterangan |
| --- | --- |
| `Banking_Risk_Analysis_v2.ipynb` | Notebook analisis (pembersihan, tren, hubungan antarindikator) |
| `spi_bulanan_repaired_v2.csv` | Data bulanan yang dipakai |
| `dashboard_perbankan.html` | Dashboard (HTML, Chart.js) |
| `screenshot_dashboard.png` | Tangkapan layar dashboard |

## Cara melihat dashboard

Buka `dashboard_perbankan.html` di browser (klik dua kali). Grafik memerlukan koneksi internet karena pustaka Chart.js dimuat dari CDN.

## Data

- Rujukan: Statistik Perbankan Indonesia (SPI), Otoritas Jasa Keuangan.
- Deret bulanan disusun dari beberapa file SPI. Kolom `Sumber_SPI` pada CSV mencatat file asal tiap baris.
- Indikator: NPL gross, ROA, CAR, LDR, dan NIM (NIM disimpan di CSV tetapi tidak menjadi fokus analisis).

## Temuan

<!-- TODO: tulis ulang dengan kata-katamu sendiri -->
1. **NPL terkendali.** NPL naik dari 2,86% (Jan 2018) ke puncak 3,35% (Agu 2021), lalu turun ke 2,22% (Jun 2025). Jaraknya ke batas 5% tidak pernah kurang dari 1,65 poin persentase.
2. **ROA turun saat COVID, lalu pulih.** ROA terendah 1,59% (Des 2020). Rata-ratanya 2,49% sebelum COVID (Jan 2018 – Feb 2020), 1,93% saat COVID (Mar 2020 – Des 2021), dan 2,59% pada periode pemulihan (Jan 2022 – Jun 2025).
3. **Modal menebal, LDR turun.** CAR terendah 21,67% (Mar 2020), masih 13,67 poin di atas minimum 8%, dan naik ke 25,81% (Jun 2025). Rata-rata CAR naik dari 23,00% ke 26,14%, sedangkan rata-rata LDR turun dari 93,27% ke 83,40%. Korelasi CAR dan LDR −0,58.
4. **NPL dan ROA: hati-hati menafsirkan.** Korelasi −0,79 pada level, tetapi hanya 0,05 pada perubahan bulanan. Kuatnya hubungan lebih mencerminkan tren yang bergerak searah, bukan bukti sebab-akibat.

## Keterbatasan

- **Data kosong:** ROA, CAR, LDR, dan NIM bulan Juni–September 2021 tidak tersedia dan sengaja dibiarkan kosong (tidak diinterpolasi). Statistik dihitung dari bulan yang terisi.
- **Presisi angka:** nilai pada CSV berdesimal enam, sedangkan OJK merilis rasio dua desimal. Pada sejumlah bulan yang dicocokkan dengan siaran pers OJK, hasil pembulatannya sama, tetapi pengecekan itu hanya sampel, bukan seluruh data. Ada selisih kecil pada beberapa bulan (misalnya CAR Maret 2023).
- **LDR** belum diverifikasi ke sumber resmi.
- **Ambang LDR 84–94%** adalah asumsi analisis, bukan ketentuan OJK.
- Data agregat industri, tanpa perbandingan antarbank. Korelasi tidak menunjukkan sebab-akibat.

## Cara menjalankan notebook

```bash
pip install pandas numpy matplotlib jupyter
jupyter notebook Banking_Risk_Analysis_v2.ipynb
```

Letakkan `spi_bulanan_repaired_v2.csv` di folder yang sama dengan notebook. Grafik tersimpan otomatis ke folder `figures/`.

## Alat

Python (pandas, NumPy, Matplotlib) untuk analisis; HTML dan Chart.js untuk dashboard.
