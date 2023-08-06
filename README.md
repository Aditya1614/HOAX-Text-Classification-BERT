# HOAX-Text-Classification-BERT

## Project Overview

<img src="https://github.com/Aditya1614/HOAX-Text-Classification-BERT/assets/93992324/1f677618-fa13-40a6-b959-7c09d7c4fa3c" width="700">

## Problem Understanding
Hoax adalah informasi sesat dan berbahaya karena dapat menyesatkan persepsi manusia dengan menyampaikan informasi palsu sebagai kebenaran. Saat  ini,  hoax  sangat  banyak  tersebar  melalui  media  internet.  Perkembangan teknologi  informasi  yang  begitu  cepat  memicu  penyebaran  informasi  hoax melalui  internet  menjadi  tidak  terkontrol. Menurut survei Katadata Insight Center (KIC) yang bekerjasama dengan Kementerian Komunikasi dan Informatika serta SiBerkreasi Setidaknya 30% sampai hampir 60% orang Indonesia terpapar hoaks saat mengakses dan berkomunikasi melalui dunia maya.  Sehingga kami membuat sistem klasifikasi berita hoax dengan menggunakan pendekatan transfer learning dan menggunakan BERT sebagai modelnya. 

## Data Understanding
Dalam project ini, kami menggunakan dataset yang bersumber dari situs kaggle yang dapat diakses di <a href="https://www.kaggle.com/datasets/linkgish/indonesian-fact-and-hoax-political-news">Indonesian Fact and Hoax Political News</a>.

Dataset memiliki 4 file berformat xlsx di dalamnya yaitu dataset_cnn_10k_cleaned.xlsx, dataset_kompas_4k_cleaned.xlsx, dataset_tempo_6k_cleaned.xlsx, dan dataset_turnbackhoax_10_cleaned.xlsx.

Variable yang ada di dataset ini yaitu sebagai berikut:
- Title: judul dari berita
- Timestamp: waktu berita ini diakses
- FullText: narasi lengkap dari berita
- Tags: tag berita tersebut
- Author: penulis berita
- Url: link berita
- text_new: narasi yang sudah dirapikan
- hoax: label berita, 0 berarti berita valid dan 1 berarti berita hoax
  
Khusus untuk dataset_turnbackhoax_10_cleaned.xlsx ada penambahan variable yaitu:
- Politik: 1 berarti berita terkait politik dan 0 berarti bukan berita terkait politik
- Narasi: narasi dari berita

Dalam project ini, kita menggabungkan semua dataset menjadi satu dan hanya akan menggunakan variable Title dan hoax saja.

## Exploratory Data Analysis (EDA)
1. Jumlah data valid dan data hoax.
   
   ![eda](https://github.com/Aditya1614/HOAX-Text-Classification-BERT/assets/93992324/c42ca95e-82cb-4a78-becf-f16d5dc6fc52)

   Dari visualisasi ini dapat diketahui bahwa data dengan label 0 atau valid berjumlah sekitar 20.000 data sedangkan data dengan label 1 atau hoax berjumlah sekitar 10.000 data.

2. WordCloud

   ![wordcloud](https://github.com/Aditya1614/HOAX-Text-Classification-BERT/assets/93992324/0892013f-f18b-4162-9d5c-8f9837d3cd23)

   Dari visualisasi ini dapat diketahui bahwa kata yang sering muncul kebanyakan yaitu terkait dengan politik.

## Data Pre-processing

1. Menangani missing value

   ![null](https://github.com/Aditya1614/HOAX-Text-Classification-BERT/assets/93992324/f3d19260-d647-4a28-a324-2f8b84f48f43)

   Disini terdapat missing value pada variable Title sebanyak 21 data. Penanganan missing value ini kita lakukan dengan cara dihapus menggunakan fungsi dropna()

2. Train-test split

   <img src="https://github.com/Aditya1614/HOAX-Text-Classification-BERT/assets/93992324/6f4fa54e-feab-42ec-a8c8-3cb241cdff0a" width="500">

   Disini kita membagi data menjadi data latih dan data uji dengan proporsi 90-10. Sehingga terdapat 28.198 data latih dan 3134 data uji.

3. Tokenizer

   Dalam project ini, kami menggunakan tokenizer "bert-base-multilingual-cased". Tokenizer ini adalah pre-trained model yang telah dilatih menggunakan 104 bahasa termasuk bahasa indonesia. Untuk menggunakan tokenizer ini kita tidak perlu menghapus stopword karena tokenizer ini dapat mengenali makna dari teks, menghapus stopword hanya akan menghilangkan makna dari teks tersebut. Kita juga tidak melakukan stemming karena tokenizer ini sendiri dapat memecah kata menjadi sub-kata

   

    
