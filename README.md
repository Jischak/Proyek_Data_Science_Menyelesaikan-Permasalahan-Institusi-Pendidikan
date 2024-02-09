# Proyek_Data_Science_Menyelesaikan-Permasalahan-Institusi-Pendidikan
Proyek untuk mendeteksi siswa yang mungkin akan melakukan dropout

## Business Understanding
Jaya Jaya Institut merupakan salah satu institusi pendidikan perguruan yang telah berdiri sejak tahun 2000. Hingga saat ini ia telah mencetak banyak lulusan dengan reputasi yang sangat baik.

### Permasalahan Bisnis
Permasalahan pada Jaya Jaya Institut adalah terdapat banyak juga siswa yang tidak menyelesaikan pendidikannya alias dropout. Jumlah dropout yang tinggi ini tentunya menjadi salah satu masalah yang besar untuk sebuah institusi pendidikan. Oleh karena itu, Jaya Jaya Institut ingin mendeteksi secepat mungkin siswa yang mungkin akan melakukan dropout sehingga dapat diberi bimbingan khusus.

### Cakupan Proyek
<p>Untuk menjawab permasalahan bisnis tersebut, kita akan mengidentifikasi berbagai faktor yang mempengaruhi tingginya angka dropout. Nah, pada proyek ini kita akan membuat bussiness dashboard untuk membantu memonitori berbagai faktor tersebut. 
</p>

<p>Selain itu, kita akan menerapkan analisis klasifikasi untuk fitur dropout dengan metode machine learning. Algoritma machine learning yang digunakan akan disesuaikan dengan keadaan dataset (akan ditentukan pada tahapan modeling). Kita juga akan melakukan sedikit proses Exploratory Data Analysis (EDA) untuk memperoleh gambaran terkait dataset yang akan kita gunakan. Pada prosesnya, kita juga akan coba melihat karakteristik dari setiap kelompok data (berdasarkan beberapa kolom kategoris) yang terdapat dalam dataset. 
</p>

Nah, berdasarkan cakupan proyek tersebut, kita membutuhkan beberapa resource dan tool, yaitu

1. data siswa di Jaya Jaya Institut (data.csv).
2. Tool yang digunakan untuk membuat bussiness dashboard adalah Looker Studio.
3. bahasa pemrograman Python sebagai tool utama kita dalam proyek ini.
4. berbagai library pendukung untuk pengolahan data dan pengembangan model machine learning.

### Persiapan

Sumber data: https://github.com/dicodingacademy/dicoding_dataset/tree/main/students_performance

Konteks data:
  1. Marital Status: status pernikahan dari siswa. (Kategorikal) 1 – single; 2 – married; 3 – widower; 4 – divorced; 5 – facto union; 6 – legally separated;
  2. Application mode: Metode aplikasi yang digunakan oleh siswa. (Kategorikal).
     - 1: 1st phase -> general contingent
     - 2: Ordinance -> No. 612/93
     - 5: 1st phase -> special contingent (Azores Island)
     - 7: Holders of other higher courses
     - 10: Ordinance No. 854-B/99
     - 15: International student (bachelor)
     - 16: 1st phase -> special contingent (Madeira Island)
     - 17: 2nd phase -> general contingent
     - 18: 3rd phase -> general contingent
     - 26: Ordinance No. 533-A/99, item b2) (Different Plan)
     - 27: Ordinance No. 533-A/99, item b3 (Other Institution)
     - 39: Over 23 years old 42 -> Transfer
     - 43: Change of course 44 -> Technological specialization diploma holders
     - 51: Change of institution/course
     - 53: Short cycle diploma holders
     - 57: Change of institution/course (International)
  3. Application order: Urutan siswa yang mendaftar. (Numerik) 0 adalah pilihan pertama; dan 9 pilihan terakhir.
  4. Course: Mata kuliah yang diambil oleh siswa. (Kategorikal).
     - 33: Biofuel Production Technologies
     - 171: Animation and Multimedia Design
     - 8014: Social Service (evening attendance)
     - 9003: Agronomy
     - 9070: Communication Design
     - 9085: Veterinary Nursing
     - 9119: Informatics Engineering
     - 9130: Equinculture
     - 9147: Management
     - 9238: Social Service
     - 9254: Tourism
     - 9500: Nursing
     - 9556: Oral Hygiene
     - 9670: Advertising and Marketing Management
     - 9773: Journalism and Communication
     - 9853: Basic Education
     - 9991: Management (evening attendance)
  5. Daytime/evening attendance: Apakah siswa menghadiri kelas pada siang hari atau malam hari. (Kategorikal) 1 - daytime/siang hari 0 - evening/malam hari
  6. Previous qualification: Kualifikasi yang diperoleh siswa sebelum mendaftar di pendidikan tinggi. (Kategorikal).
     - 1: Secondary education
     - 2: Higher education -> bachelor's degree
     - 3: Higher education -> degree
     - 4: Higher education -> master's
     - 5: Higher education -> doctorate
     - 6: Frequency of higher education
     - 9: 12th year of schooling -> not completed
     - 10: 11th year of schooling -> not completed
     - 12: Other -> 11th year of schooling
     - 14: 10th year of schooling
     - 15: 10th year of schooling -> not completed
     - 19: Basic education 3rd cycle (9th/10th/11th year) or equiv
     - 38: Basic education 2nd cycle (6th/7th/8th year) or equiv
     - 39: Technological specialization course
     - 40: Higher education -> degree (1st cycle)
     - 42: Professional higher technical course
     - 43: Higher education -> master (2nd cycle)
  7. Previous qualification (grade): Nilai kualifikasi sebelumnya (antara 0 dan 200)
  8. Nacionality: kewarganegaraan siswa. (Kategorikal)
     - 1: Portuguese;
     - 2: German;
     - 6: Spanish;
     - 11: Italian;
     - 13: Dutch;
     - 14: English;
     - 17: Lithuanian;
     - 21: Angolan;
     - 22: Cape Verdean;
     - 24: Guinean;
     - 25: Mozambican;
     - 26: Santomean;
     - 32: Turkish;
     - 41: Brazilian;
     - 62: Romanian;
     - 100: Moldova (Republic of);
     - 101: Mexican;
     - 103: Ukrainian;
     - 105: Russian;
     - 108: Cuban;
     - 109: Colombian
  9. Mother's qualification: Kualifikasi ibu siswa. (Kategorikal)
     - 1: Secondary Education -> 12th Year of Schooling or Eq.
     - 2: Higher Education -> Bachelor's Degree
     - 3: Higher Education -> Degree
     - 4: Higher Education -> Master's
     - 5: Higher Education -> Doctorate
     - 6: Frequency of Higher Education
     - 9: 12th Year of Schooling -> Not Completed
     - 10: 11th Year of Schooling -> Not Completed
     - 11: 7th Year (Old)
     - 12: Other -> 11th Year of Schooling
     - 14: 10th Year of Schooling
     - 18: General commerce course
     - 19: Basic Education 3rd Cycle (9th/10th/11th Year) or Equiv.
     - 22: Technical-professional course
     - 26: 7th year of schooling
     - 27: 2nd cycle of the general high school course
     - 29: 9th Year of Schooling - Not Completed
     - 30: 8th year of schooling
     - 34: Unknown
     - 35: Can't read or write
     - 36: Can read without having a 4th year of schooling
     - 37: Basic education 1st cycle (4th/5th year) or equiv.
     - 38: Basic Education 2nd Cycle (6th/7th/8th Year) or Equiv.
     - 39: Technological specialization course
     - 40: Higher education -> degree (1st cycle)
     - 41: Specialized higher studies course
     - 42: Professional higher technical course
     - 43: Higher Education -> Master (2nd cycle)
     - 44: Higher Education -> Doctorate (3rd cycle)
  10. Father's qualification: Kualifikasi ayah siswa. (Kategorikal)
      - 1: Secondary Education -> 12th Year of Schooling or Eq
      - 2: Higher Education -> Bachelor's Degree
      - 3: Higher Education -> Degree
      - 4: Higher Education -> Master's
      - 5: Higher Education -> Doctorate
      - 6: Frequency of Higher Education
      - 9: 12th Year of Schooling -> Not Completed
      - 10: 11th Year of Schooling -> Not Completed
      - 11: 7th Year (Old)
      - 12: Other -> 11th Year of Schooling
      - 13: 2nd year complementary high school course
      - 14: 10th Year of Schooling
      - 18: General commerce course
      - 19: Basic Education 3rd Cycle (9th/10th/11th Year) or Equiv.
      - 20: Complementary High School Course
      - 22: Technical-professional course
      - 25: Complementary High School Course -> not concluded
      - 26: 7th year of schooling
      - 27: 2nd cycle of the general high school course
      - 29: 9th Year of Schooling -> Not Completed
      - 30: 8th year of schooling
      - 31: General Course of Administration and Commerce
      - 33: Supplementary Accounting and Administration
      - 34: Unknown
      - 35: Can't read or write
      - 36: Can read without having a 4th year of schooling
      - 37: Basic education 1st cycle (4th/5th year) or equiv.
      - 38: Basic Education 2nd Cycle (6th/7th/8th Year) or Equiv.
      - 39: Technological specialization course
      - 40: Higher education -> degree (1st cycle)
      - 41: Specialized higher studies course
      - 42: Professional higher technical course
      - 43: Higher Education -> Master (2nd cycle)
      - 44: Higher Education - Doctorate (3rd cycle)
  11. Mother's occupation: Pekerjaan ibu siswa. (Kategorikal).
      - 0: Student
      - 1: Representatives of the Legislative Power and Executive Bodies, Directors, Directors and Executive Managers
      - 2: Specialists in Intellectual and Scientific Activities
      - 3: Intermediate Level Technicians and Professions
      - 4: Administrative staff
      - 5: Personal Services, Security and Safety Workers and Sellers
      - 6: Farmers and Skilled Workers in Agriculture, Fisheries and Forestry
      - 7: Skilled Workers in Industry, Construction and Craftsmen
      - 8: Installation and Machine Operators and Assembly Workers
      - 9: Unskilled Workers
      - 10: Armed Forces Professions
      - 90: Other Situation
      - 99: (blank)
      - 122: Health professionals
      - 123: teachers
      - 125: Specialists in information and communication technologies (ICT)
      - 131: Intermediate level science and engineering technicians and professions
      - 132: Technicians and professionals, of intermediate level of health
      - 134: Intermediate level technicians from legal, social, sports, cultural and similar services
      - 141: Office workers, secretaries in general and data processing operators
      - 143: Data, accounting, statistical, financial services and registry-related operators
      - 144: Other administrative support staff
      - 151: personal service workers
      - 152: sellers
      - 153: Personal care workers and the like
      - 171: Skilled construction workers and the like, except electricians
      - 173: Skilled workers in printing, precision instrument manufacturing, jewelers, artisans and the like
      - 175: Workers in food processing, woodworking, clothing and other industries and crafts
      - 191: cleaning workers
      - 192: Unskilled workers in agriculture, animal production, fisheries and forestry
      - 193: Unskilled workers in extractive industry, construction, manufacturing and transport
      - 194: Meal preparation assistants
  12. Father's occupation: Pekerjaan ayah siswa. (Kategorikal)
      - 0: Student
      - 1: Representatives of the Legislative Power and Executive Bodies, Directors, Directors and Executive Managers
      - 2: Specialists in Intellectual and Scientific Activities
      - 3: Intermediate Level Technicians and Professions
      - 4: Administrative staff
      - 5: Personal Services, Security and Safety Workers and Sellers
      - 6: Farmers and Skilled Workers in Agriculture, Fisheries and Forestry
      - 7: Skilled Workers in Industry, Construction and Craftsmen
      - 8: Installation and Machine Operators and Assembly Workers
      - 9: Unskilled Workers
      - 10: Armed Forces Professions
      - 90: Other Situation
      - 99: (blank)
      - 101: Armed Forces Officers
      - 102: Armed Forces Sergeants
      - 103: Other Armed Forces personnel
      - 112: Directors of administrative and commercial services
      - 114: Hotel, catering, trade and other services directors
      - 121: Specialists in the physical sciences, mathematics, engineering and related techniques
      - 122: Health professionals
      - 123: teachers
      - 124: Specialists in finance, accounting, administrative organization, public and commercial relations
      - 131: Intermediate level science and engineering technicians and professions
      - 132: Technicians and professionals, of intermediate level of health
      - 134: Intermediate level technicians from legal, social, sports, cultural and similar services
      - 135: Information and communication technology technicians
      - 141: Office workers, secretaries in general and data processing operators
      - 143: Data, accounting, statistical, financial services and registry-related operators
      - 144: Other administrative support staff
      - 151: personal service workers
      - 152: sellers
      - 153: Personal care workers and the like
      - 154: Protection and security services personnel
      - 161: Market-oriented farmers and skilled agricultural and animal production workers
      - 163: Farmers, livestock keepers, fishermen, hunters and gatherers, subsistence
      - 171: Skilled construction workers and the like, except electricians
      - 172: Skilled workers in metallurgy, metalworking and similar
      - 174: Skilled workers in electricity and electronics
      - 175: Workers in food processing, woodworking, clothing and other industries and crafts
      - 181: Fixed plant and machine operators
      - 182: assembly workers
      - 183: Vehicle drivers and mobile equipment operators
      - 192: Unskilled workers in agriculture, animal production, fisheries and forestry
      - 193: Unskilled workers in extractive industry, construction, manufacturing and transport
      - 194: Meal preparation assistants
      - 195: Street vendors (except food) and street service providers
  13. Admission grade: Nilai ujian masuk (antara 0 dan 200)
  14. Displaced: Apakah siswa tersebut adalah orang yang terlantar. (Kategorikal) 1 - ya 0 - tidak
  15. Educational special needs: Apakah siswa memiliki kebutuhan pendidikan khusus. (Kategorikal) 1 - ya 0 - tidak
  16. Debtor: Apakah siswa tersebut adalah seorang peminjam. (Kategorikal) 1 - ya 0 - tidak
  17. Tuition fees up to date: Apakah biaya pendidikan siswa sudah sesuai dengan yang terbaru. (Kategorikal) 1 - ya 0 - tidak
  18. Gender: Jenis kelamin siswa. (Kategorikal) 1 - laki-laki 0 - perempuan
  19. Scholarship holder: Apakah siswa tersebut adalah pemegang beasiswa. (Kategorikal) 1 - ya 0 - tidak
  20. Age at enrollment: Usia siswa pada saat pendaftaran. (Numerik)
  21. International: Apakah siswa tersebut adalah siswa internasional. (Kategorikal) 1 - ya 0 - tidak
  22. Curricular units 1st sem (credited): Jumlah unit pelajaran yang dikredit oleh mahasiswa pada semester pertama. (Numerik)
  23. Curricular units 1st sem (enrolled): Jumlah unit pelajaran yang diambil oleh mahasiswa pada semester pertama. (Numerik)
  24. Curricular units 1st sem (evaluations): Jumlah unit pelajaran yang dievaluasi oleh mahasiswa pada semester pertama. (Numerik)
  25. Curricular units 1st sem (approved): Jumlah unit kurikuler yang disetujui oleh mahasiswa pada semester pertama. (Numerik)

Proyek ini dibuat melalaui Google Colaboratory (Google Colab). Namun Anda dapat menjalankan proyek ini juga melalui Jupyter Notebook, maka ikuti langkah setup environment dibawah ini:
Setup environment menggunakan conda:
  1. Buka terminal atau PowerShell
  2. Jalankan perintah berikut untuk membuat environment baru
  ```
  conda create --name student-classification-project python=3.9
  ```
  3. Aktifkan virtual environment dengan menjalankan perintah berikut
  ```
  conda activate student-classification-project
  ```
  4. Instal semua library yang dibutuhkan dengan perintah berikut.
  ```
  pip install numpy pandas matplotlib seaborn jupyter scikit-learn==1.2.2
  ```
  5. Buka jupyter-notebook dengan menjalankan perintah berikut.
  ```
  jupyter-notebook .
  ```


## Business Dashboard

### Apa yang ingin diketahui?
Dalam proyek ini, business dashboard yang dibuat untuk memonitori data dropout. Berikut beberapa pertanyaan yang akan kita cari jawabannya dalam proyek ini.

Link Pertanyaan + Jawaban: 
```
https://docs.google.com/spreadsheets/d/1c_3Th8-2sbVCJe6vJvhG48uSjxX9n8ExNBIZqhRrZQY/edit?usp=sharing
```

### Bagaimana proses membuat business dashboard dalam proyek ini?
Business dashboard menggunakan dataset yang telah melalui tahapan persiapan. Dataset tersebut di ekspor dalam format csv dari notebook.ipynb dan setelah itu di import ke dalam Looker Studio. Selain itu, pada looker studio ada penyesuaian dan modifikasi tipe data pada beberapa variabel. Disisi lain, terdapat juga penambahan dibuat penambahan beberapa variabel baru untuk kebutuhan visualisasi di dashboard.

Link business dashboard: 
```

```

### Deskripsi Business Dashboard

#### Dashboard Karyawan Jaya Jaya Maju - Attrition
Business dashboard ini berisi visualisasi data dari variabel-variabel yang mempengaruhi attrition. Dimana, tampilan awal menunjukan keselurhan data. Namun, apabila kita ingin melihat data yang tegolong dalam attrition maka dapat dilakukan filter. Untuk data attrition, kita dapat memberi nilai 1 pada menu filter yang terdapat di bagian kanan atas. Sebaliknya, untuk yang data yang tidak tergolong attrition maka kita dapat memberi nilai 0.  

- Gambar



## Menjalankan Sistem Machine Learning
Berikut ini cara untuk menjalankan prototype Machine Learning untuk prediksi Attrition Karyawan di Jaya Jaya Maju.
Prototype ini bisa dicoba baik secara lokal (offline) maupun online. 
- Gambar

### Bagaiamana mencoba prototype secara lokal?
  1. Buka terminal atau PowerShell
  2. Aktifkan virtual environment yang telah dibuat sebelumnya
  ```
  conda activate employee-classification-project
  ```
  3. Masuk ke lokasi dimana file streamlit (prediksi.py) berada
  4. Jalankan file streamlit dengan perintah berikut ini:
  ```
  streamlit run prediksi.py
  ```

### Bagaiamana mencoba prototype secara online?
Tentunya, mudah kok... kamu bisa mengakses melalui link dibawah ini:
```
https://proyekdatasciencemenyelesaikan-permasalahan-human-resources-uq.streamlit.app/
```

## Conclusion
Berikut ini konklusi dari proyek ini:
  1. Jumlah karyawan yang keluar dari Perusahaan Jaya Jaya Maju adalah sebanyak 179 orang dari total 1058 karyawan atau apabila dipresentasekan sebanyak 16,9%.
  2. Beberapa faktor yang mempengaruhi karyawan untuk keluar dari perusahaan antara lain:
     - Jarak tempat tinggal ke kantor: Karyawan yang memiliki jarak tempat tinggal ke kantor antara 0-5 Km dominan untuk keluar dari perusahaan, dimana pada kasus ini sebanyak 72 orang.
     - Total Lama Bekerja: Karyawan yang memiliki total bekerja selama 10 tahun (0-10 tahun) cenderung lebih besar untuk keluar dari perusahaan dibanding total lama bekerja 10-20 tahun, 20-30 tahun, >40 tahun. Kontribusi-nya sebanyak 137 orang.
     - Keterlibatan dalam Pekerjaan: Karyawan yang memiliki keterlibatan tinggi (high) dalam pekerjaan memiliki presentase untuk keluar dari perusahaan lebih tinggi (sebanyak 51,4%) dari pada yang keterlibatannya sedang (medium), rendah (low), dan sangat tinggi (very high).
     - Tingkat Pekerjaan (rendah - tinggi / 1 - 5): Tingkat pekerjaan yang rendah memiliki kontribusi tertinggi untuk jumlah karyawan yang keluar dengan jumlah sebanyak 108 orang.
     - Kepuasan Lingkungan Kerja: Karyawan yang keluar cenderung memiliki kepuasan yang rendah (low) di lingkungan bekerjanya, dengan presentase sebanyak 31,8%.
     - Kepuasan Pekerjaan: Keryawan yang keluar cenderung memiliki kepuasan akan pekerjaannya yang tinggi (high), hal ini didukung dengan presentase sebanyak 34,6%.
     - Tingkat Performa: Jumlah karyawan yang keluar namun memiliki tingkat performa tinggi (151 orang) lebih banyak signifikan dibandingkan yang memiliki tingkat performa yang rendah (28 orang).
     - Kepuasan Hubungan Kerja: Karyawan yang keluar cederung memiliki kepuasan hubungan kerja yang sangat tinggi (very high) yaitu dengan presentase sebanyak 29,1%. Disisi lain, untuk karyawan dengan kepuasan hubungan kerja tinggi (high) dan rendah (low) memiliki presentase yang tidak berbeda jauh daripada kepusasan hubungan kerja yang sangat tinggi (very high) dengan masing-masing memiliki presentase 27,4% dan 25,7%.
     - Keseimbangan Kehidupan Kerja: Karyawan yang keluar didominasi oleh para karyawan yang memiliki keseimbangan kehidupan kerja yang sangat baik (excellent) dengan jumlah karyawan sebanyak 94 orang. Disisi lain, karyawan yang keluar dengan keseimbangan kehidupan kerja baik (good), luar biasa (outstanding), dan rendah (low) memiliki jumlah masing-masing adalah 45, 22, dan 18 orang.
  4. Dari 179 orang yang keluar dari perusahaan, dominan memiliki umur 31 tahun. Hal ini didukung dengan jumlah karyawan yang keluar adalah sebanyak 14 orang.
  5. Berdasarkan peran pekerjaan karyawan yang keluar dari perusahaan terbanyak tergolong dalam peran pekerjaan sebagai Laboratory Technician dengan jumlah sebanyak 49 orang.

### Rekomendasi Action Items
Berikut ini beberapa rekomendasi action items yang harus dilakukan oleh perusahaan:
  1. Dalam perekrutan karyawan baru dapat disarankan untuk mengambil karyawan yang telah memiliki total lama bekerja selama 10 tahun.
  2. Memperbaiki lingkungan kerja dengan mencari alasan spesifiknya, seperti:
     - Apabila terkait fasilitas perusahaan dapat meninjau dan perbaiki kondisi fasilitas
     - Memperbaiki hubungan Atasan-Bawahan dengan memberikan pelatihan manajemen untuk meningkatkan keterampilan kepemimpinan dan hubungan antara atasan dan bawahan.
     - Melakukan Komunikasi Terbuka dan Jelas dengan menyelenggarakan pertemuan rutin atau forum terbuka
     - Membuat program Pengembangan Karyawan sebagai peluang untuk pengembangan keterampilan dan pertumbuhan karir
     - Memberi Pengakuan dan Apresiasi melalui implementasi program pengakuan karyawan, seperti penghargaan atau ucapan terima kasih berkala.
  3. Kepuasan pekerjaan yang tinggi, namun dominan karyawan memilih untuk keluar, berikut ini action itemnya:
     - Melakukan exit interview mendalam dengan karyawan yang memutuskan untuk keluar walaupun memiliki kepuasan pekerjaan yang tinggi.
     - Meninjau dan mengevaluasi peluang pengembangan karir yang tersedia bagi karyawan.
     - Menyediakan lebih banyak program pengembangan keterampilan dan pelatihan untuk meningkatkan keahlian karyawan.
     - Meningkatkan program pengakuan dan apresiasi untuk memastikan karyawan merasa dihargai.
     - Melakukan evaluasi faktor-faktor lingkungan kerja seperti hubungan antar rekan kerja, budaya perusahaan, dan manajemen.
     - Meninjau kebijakan kompensasi dan pastikan bahwa mereka kompetitif dengan industri.
  4. Karyawan yang keluar dominan memiliki work-life balance yang sangat baik, action itemnya adalah:
     - Melakukan exit interview mendalam dengan karyawan yang meninggalkan perusahaan untuk memahami alasan mereka meskipun memiliki work-life balance yang baik.
     - Meninjau dan mengevaluasi faktor-faktor kesejahteraan dan kepuasan karyawan selain work-life balance secara rutin.
     - Berikan perhatian khusus pada program pengembangan karir dan peluang pertumbuhan.
     - Konsultasikan dengan karyawan yang masih aktif mengenai pengalaman mereka dengan work-life balance dan apa yang dapat ditingkatkan.
     - Tingkatkan keterbukaan komunikasi antara manajemen dan karyawan untuk memahami kebutuhan mereka secara lebih baik.
     - Tinjau dan evaluasi budaya perusahaan untuk memastikan bahwa nilai-nilai dan praktik perusahaan mendukung work-life balance.
  5. Berikut ini action item yang perlu dilakukan terkait fenomena karyawan yang keluar namun memiliki keterlibatan dalam pekerjaan yang tinggi:
     - Melakukan exit interview yang mendalam untuk memahami alasan karyawan meninggalkan perusahaan meskipun memiliki tingkat keterlibatan tinggi.
     - Meninjau kebijakan dan praktik manajemen untuk memastikan bahwa karyawan merasa didukung dan diakui.
     - Meningkatkan komunikasi internal untuk memastikan karyawan merasa terhubung dan diberi informasi secara jelas.
     - Mengimplementasikan program pengakuan dan penghargaan yang secara aktif menghargai kontribusi karyawan.
     - Fokus pada menciptakan lingkungan kerja yang inklusif dan mendukung kolaborasi.
     - Pertimbangkan kebijakan fleksibilitas kerja untuk memberikan karyawan lebih banyak kendali atas jadwal mereka.
  6. Apa saja action items yang dapat dilakukan dalam menyikapi fenomena karyawan yang dominan keluar walaupun memiliki kepuasan hubungan yang sangat tinggi?
     - Melakukan exit interview yang mendalam untuk memahami dengan lebih baik alasan karyawan meninggalkan perusahaan meskipun memiliki kepuasan hubungan kerja yang sangat tinggi.
     - Meninjau faktor-faktor eksternal yang mungkin memengaruhi keputusan karyawan, seperti tawaran pekerjaan dari perusahaan lain atau perubahan kondisi pribadi.
     - Menyediakan peluang pengembangan karir dan pertumbuhan yang jelas untuk mendorong karyawan tetap di perusahaan.
     - Meninjau gaya kepemimpinan di berbagai tingkatan organisasi untuk memastikan bahwa karyawan merasa didukung dan dihargai.
     - Meningkatkan program penghargaan dan pengakuan untuk menunjukkan apresiasi terhadap kontribusi karyawan.

