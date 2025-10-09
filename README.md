# 📊 Analisis Sentimen Tweet Terhadap Trump

Proyek ini merupakan bagian dari penugasan mata kuliah yang berfokus pada teknik pemrosesan teks, dan implementasi analisis sentimen menggunakan pustaka populer Python.

---

## 👨‍💻 Informasi Penugasan

| Keterangan      | Detail                                                                |
| :-------------- | :-------------------------------------------------------------------- |
| **Nama**        | **Muhammad Habsyi Mubarak**                                           |
| **NIM**         | **5220411094**                                                        |
| **Tugas Wajib** | Scraping data dari internet dan Melakukan **Case Folding** pada teks. |
| **Topik Data**  | Sentimen publik terhadap kata kunci **"Trump"** dalam bahasa inggris. |
| **Jumlah Data** | Minimal **"1000"** baris data.                                        |

---

## 🛠️ Alat dan Pustaka yang Digunakan

Proyek ini memanfaatkan beberapa alat utama untuk setiap tahapan proses:

| Tahapan Proyek                  | Alat/Pustaka Utama                                          |
| :------------------------------ | :---------------------------------------------------------- |
| **Pengambilan Data (Scraping)** | `tweet-harvest` (versi 2.6.1)                               |
| **Pemrosesan Data**             | `Pandas`                                                    |
| **Analisis Sentimen**           | **VADER** (Valence Aware Dictionary and sEntiment Reasoner) |
| **Visualisasi Hasil**           | `Seaborn` dan `Matplotlib`                                  |

---

## 🔍 Detail Pengambilan Data (Scraping)

Data tweet diambil menggunakan `tweet-harvest` dengan konfigurasi yang spesifik untuk mendapatkan data yang relevan dan terbatas.

| Parameter              | Nilai / Deskripsi                                                                                                                                |
| :--------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nama File Output**   | `trump.csv`                                                                                                                                      |
| **Batas Data (Limit)** | **2000** tweet                                                                                                                                   |
| **Keyword Pencarian**  | `(trump OR #Trump) -filter:retweets -filter:replies -giveaway -promo -deal -card -trumpet since:2025-05-01 until:2025-10-09 min_faves:5 lang:en` |
| **Tanggal Pencarian**  | Dari **2025-05-01** hingga **2025-10-09**                                                                                                        |
| **Bahasa**             | Bahasa Inggris (`lang:en`)                                                                                                                       |

### Perintah Scraping yang Digunakan

```bash
# Crawl Data (versi optimal)

filename = 'trump.csv'
keyword = '(trump OR #Trump) -filter:retweets -filter:replies -giveaway -promo -deal -card -trumpet since:2025-05-01 until:2025-10-09 min_faves:5 lang:en'
limit = 2000

!npx -y tweet-harvest@2.6.1 -o "{filename}" -s "{keyword}" --tab "LATEST" -l {limit} --token {twitter_auth_token}
```

### 🧾 Perbandingan Sebelum dan Sesudah Cleaning

| full_text                                                                                                                                                                                                                                                                        | clean_text                                                                                                                                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| WATCH: Gov. JB Pritzker claims President Trump always chickens out after he called for his arrest. We've done nothing wrong here. And very importantly it's Donald Trump that is breaching the Constitution breaking the law. We're taking him to court. https://t.co/C7jXkNkvW3 | watch gov jb pritzker claims president trump always chickens out after he called for his arrest weve done nothing wrong here and very importantly its donald trump that is breaching the constitution breaking the law were taking him to court |
| Trump raised the Bar and the rest ...                                                                                                                                                                                                                                            | trump raised the bar and the rest                                                                                                                                                                                                               |
| Sen FETTERMAN votes NO on the War Powers Resolution...                                                                                                                                                                                                                           | sen fetterman votes no on the war powers resolution that would require congressional approval before the trump admin conducted additional military strikes in the caribbean                                                                     |
| President Trump Beats Democrats AGAIN - Massive Court Victory...                                                                                                                                                                                                                 | president trump beats democrats again massive court victory read the full article below                                                                                                                                                         |
| Trump Announces Israel Hamas PEACE PLAN SIGNED...                                                                                                                                                                                                                                | trump announces israel hamas peace plan signed israel to withdraw troops timcast irl                                                                                                                                                            |
