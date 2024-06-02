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
     - 39: Over 23 years old
     - 42: Transfer
     - 43: Change of course
     - 44: Technological specialization diploma holders
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
  16. Debtor: Apakah siswa tersebut adalah seseorang yang memiliki utang atau tunggakan pembayaran terhadap lembaga pendidikan. (Kategorikal) 1 - ya 0 - tidak
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
  pip install -r requirements.txt
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
https://lookerstudio.google.com/reporting/143bfbce-c288-4cd5-9901-51d11c682ddc
```

### Deskripsi Business Dashboard

#### Dashboard Karyawan Jaya Jaya Maju - Attrition
Business dashboard ini berisi visualisasi data dari variabel-variabel yang mempengaruhi attrition. Dimana, tampilan awal menunjukan keselurhan data. Namun, apabila kita ingin melihat data yang tegolong dalam attrition maka dapat dilakukan filter. Untuk data attrition, kita dapat memberi nilai 1 pada menu filter yang terdapat di bagian kanan atas. Sebaliknya, untuk yang data yang tidak tergolong attrition maka kita dapat memberi nilai 0.  

![Dashboard Siswa di Institut Jaya Jaya Maju - Google Chrome 2024-02-11 23-35-15](https://github.com/Jischak/Proyek_Data_Science_Menyelesaikan-Permasalahan-Institusi-Pendidikan/assets/52368239/a2df210e-a3ce-4eb9-ae8a-486fa9a939ea)

## Menjalankan Sistem Machine Learning
Berikut ini cara untuk menjalankan prototype Machine Learning untuk prediksi Attrition Karyawan di Jaya Jaya Maju.
Prototype ini bisa dicoba baik secara lokal (offline) maupun online. 

![image](https://github.com/Jischak/Proyek_Data_Science_Menyelesaikan-Permasalahan-Institusi-Pendidikan/assets/52368239/230a28d0-0860-4e66-a568-c82614b19fb2)


### Bagaiamana mencoba prototype secara lokal?
  1. Buka terminal atau PowerShell
  2. Aktifkan virtual environment yang telah dibuat sebelumnya
  ```
  conda activate employee-classification-project
  ```
  3. Masuk ke lokasi dimana file streamlit (prediksi.py) berada
  4. Jalankan file streamlit dengan perintah berikut ini:
  ```
  streamlit run prediksi_dropout.py
  ```

### Bagaiamana mencoba prototype secara online?
Tentunya, mudah kok... kamu bisa mengakses melalui link dibawah ini:
```
https://proyekdatasciencemenyelesaikan-permasalahan-institusi-pendidik.streamlit.app/
```

## Conclusion
Berikut ini konklusi dari proyek ini:
  1. Jumlah siswa yang dropout / berhenti / keluar dari Institut Jaya Jaya adalah sebanyak 1421 siswa dari total 4424 siswa atau apabila dalam presentase sebesar 32,1%.
  2. Mayoritas siswa yang dropout adalah siswa yang memiliki status "single" dengan jumlah sebanyak 1184 siswa. Disisi lain, untuk siswa yang dropout dan memiliki status married adalah sebanyak 179. Sisanya adalah siswa yang memiliki status divorced, factor union, legally separated, dan widower dengan masing-masing memiliki jumlah sebanyak 42 siswa, 11 siswa, 4 siswa, dan 1 siswa.
  3. Siswa yang dropout kebanyakan adalah siswa yang mempunyai waktu studi di siang hari dengan jumlah siswa sebanyak 1214 siswa. Sedangkan, jumlah siswa yang drop out dan memiliki waktu studi di malam adalah sebanyak 207 siswa.
  4. Siswa yang dropout mayoritas adalah siswa yang memiliki pendidikan terakhir di jenjang pendidikan menengah (secondary education) dengan jumlah sebanyak 1078 siswa.
  5. Jumlah siswa yang dropout dan memiliki kewarganegaraan Portugal adalah sebanyak 1389.
  6. Beberapa faktor yang mempengaruhi siswa untuk keluar dari studi antara lain:
     - Pekerjaan orang tua: Mayoritas siswa yang keluar dari studi adalah siswa yang orang tuanya bekerja sebagai pekerja yang tidak membutuhkan keterampilan khusus, dimana pada kasus ini adalah sebanyak 323 siswa yang ayahnya memiliki pekerjaan tersebut. Selain itu, hal yang sama berlaku juga untuk siswa yang ibunya bekerja, dimana jumlah siswanya sebanyak 490 siswa.
     - Masyarakat terlantar / kurang mampu: Hampir setengah dari jumlah siswa yang dropout tergolong dalam masyarakat kurang mampu, hal ini terlihat dengan presentase-nya sebanyak 47,1%.
     - Umur: Mayoritas siswa yang dropout adalah siswa yang berumur 19 tahun, dengan jumlah sebanyak 207 siswa. Selanjutnya, siswa dengan umur 18 sebanyak 202 siswa, umur 20 sebanyak 133 siswa, dan umur 21 sebanyak 93 siswa. 
  7. Terdapat juga siswa yang berkebutuhan khusus dan memilih untuk dropout, jumlahnya adalah sebanyak 17 siswa.
  8. Walaupun siswa yang dominan untuk dropout adalah siswa yang bukan penerima beasiswa (1287). Namun, terdapat juga siswa penerima beasiswa dan memilih dropout, jumlahnya sebanyak 134.
  9. Mayoritas siswa yang dropout adalah siswa yang bukan tergolong siswa internasional dengan jumlah sebanyak 1389 siswa. Walaupun, terdapat juga siswa Inetrnasional yang dropout dengan jumlah sebanyak 32.
  10. Terkait siswa yang dropout dan biaya pendidikan sudah diperbaharui / tidak, didominasi oleh siswa yang biaya pendidikannya sudah diperbaharui (terbaru) dengan jumlah sebanyak 964 siswa. Walaupun tidak sedikit juga siswa yang biaya pendidikannya belum diperbaharui (sebanyak 457 siswa).
  11. Berdasarkan jenis kelamain, siswa yang dropout didominasi oleh siswa perempuan dengan presentase sebanyak 50,7%. Disisi lain, presentase siswa laki-laki yang dropout adalah 49,3%.

### Rekomendasi Action Items
Berikut ini beberapa rekomendasi action items yang harus dilakukan oleh perusahaan:
  1. Tindak lanjut untuk siswa yang dropout dan memiliki orang tua bekerja sebagai pekerja yang tidak membutuhkan keterampilan khusus, antara lain:
     - Mendekati siswa secara individu untuk memahami alasan di balik keputusan mereka untuk dropout. Memberikan kesempatan kepada siswa untuk berbicara tentang masalah yang mereka hadapi dan mendengarkan dengan empati.
     - Melakukan pendekatan kolaboratif dengan orang tua siswa, berkomunikasi secara teratur dengan orang tua siswa untuk membangun kemitraan dalam mendukung perkembangan pendidikan anak-anak mereka.
     - Mengidentifikasi siswa yang mengalami kesulitan finansial dan memberikan bantuan dalam hal pembayaran biaya sekolah, buku pelajaran, atau peralatan belajar. Selain itum dapat juga menawarkan program beasiswa atau bantuan keuangan bagi siswa yang membutuhkan.
     - Menyediakan program tutoring atau bimbingan akademik bagi siswa yang membutuhkan bantuan tambahan dalam pelajaran mereka. Mengadakan kelas remedial atau kelas tambahan untuk membantu siswa mengejar ketinggalan akademis dan merasa lebih percaya diri.
  2. Tindak lanjut untuk siswa yang dropout dan tergolong dalam masyarakat terlantar / kurang mampu
     - Mendirikan pusat bantuan sosial di sekolah untuk memberikan layanan kesejahteraan, bantuan finansial, dan dukungan emosional bagi siswa dan keluarga mereka. Menyediakan akses ke layanan kesehatan mental dan konseling untuk membantu siswa mengatasi stres dan tantangan yang mereka hadapi.
     - Mendekati siswa secara individu untuk memahami alasan di balik keputusan mereka untuk dropout dan mengidentifikasi kebutuhan mereka. Memberikan bimbingan akademik dan mentoring untuk membantu siswa mengejar ketinggalan akademis dan merasa lebih percaya diri dalam kemampuan belajar mereka.
     - Menawarkan program beasiswa atau dana bantuan keuangan bagi siswa yang membutuhkan, untuk membantu mengurangi beban finansial mereka.
     - Berkolaborasi dengan organisasi non-profit, lembaga amal, atau lembaga agama di komunitas untuk menyediakan bantuan tambahan kepada siswa dan keluarga mereka.
     - Mengembangkan program pemulihan khusus untuk membantu siswa kembali ke jalur pendidikan, dengan menyediakan dukungan dan bimbingan berkelanjutan.
     - Menyediakan pelatihan keterampilan hidup yang praktis, seperti keterampilan keuangan, keterampilan komunikasi, dan keterampilan kerja, untuk membantu siswa mempersiapkan diri untuk kehidupan setelah sekolah.
  3. Tindak lanjut untuk siswa yang dropout dan tergolong dalam rentang umur 18-21 tahun:
     - Mendekati siswa secara individu untuk memahami alasan di balik keputusan mereka untuk dropout dan memberikan dukungan serta bimbingan yang diperlukan untuk membantu mereka mengatasi hambatan dan mencapai tujuan pendidikan mereka.
     - Menyediakan program pendidikan kembali yang dirancang khusus untuk siswa yang telah dropout. Program ini dapat membantu siswa mengejar ketinggalan akademis dan meraih kualifikasi pendidikan yang setara dengan tingkat pendidikan mereka.
     - Memberikan dukungan sosial yang kuat, konseling, dan bantuan kesejahteraan kepada siswa untuk membantu mereka mengatasi stres, kecemasan, dan tantangan kehidupan yang mungkin menyebabkan mereka dropout.
     - Mengintegrasikan kurikulum yang berbasis keterampilan ke dalam program pendidikan untuk memberikan siswa keterampilan praktis yang dapat meningkatkan peluang mereka untuk mendapatkan pekerjaan yang stabil dan berkelanjutan.
     - Berkolaborasi dengan perguruan tinggi atau lembaga pelatihan lokal untuk menyediakan program pendidikan lanjutan atau pelatihan keterampilan yang dapat membantu siswa mencapai tujuan pendidikan dan karir mereka.

