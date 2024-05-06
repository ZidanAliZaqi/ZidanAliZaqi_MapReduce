# ZidanAliZaqi_MapReduce

# Instalasi java
Mengonfigurasi lingkungan Linux untuk pengembangan dengan menginstal OpenJDK 8, mengatur versi Java yang digunakan, dan memulai server SSH untuk akses tanpa kata sandi. Selanjutnya, script tersebut mendownload dan menginstal Hadoop 3.2.3, menyesuaikan konfigurasinya untuk menggunakan JDK yang diinstal, dan mengatur variabel lingkungan yang diperlukan untuk menjalankan Hadoop. Proses ini mempersiapkan sistem untuk pengembangan dan pengujian aplikasi yang berbasis Hadoop, mengintegrasikan penyimpanan data dan pemrosesan terdistribusi.

# Konfigurasi File HDFS
Menginisialisasi kluster Hadoop dengan memformat NameNode untuk mempersiapkan Sistem File Terdistribusi Hadoop (HDFS) dan mengatur variabel lingkungan untuk mendefinisikan hak akses pengguna untuk berbagai daemon Hadoop. Kemudian, skrip meluncurkan layanan HDFS penting, termasuk NameNode dan DataNode, diikuti dengan memulai layanan YARN yang mengelola alokasi sumber daya dan penjadwalan pekerjaan di seluruh kluster. Akhirnya, skrip memverifikasi operasi layanan ini dengan mencantumkan proses Java yang aktif, mengonfirmasi bahwa komponen ekosistem Hadoop berjalan seperti yang diharapkan. Pengaturan ini memungkinkan fungsionalitas penyimpanan dan pemrosesan terdistribusi yang diperlukan untuk menangani set data besar secara efisien.

# Mapper.py
Skrip `mapper.py` merupakan bagian dari proses MapReduce yang digunakan untuk mengolah teks. Skrip ini membaca input teks baris demi baris dari STDIN, membersihkan spasi di awal dan akhir baris, dan memisahkan baris tersebut menjadi kata-kata. Setiap kata kemudian dicetak ke STDOUT dalam format `kata\t1`, di mana `\t` merupakan pemisah tab dan angka ‘1’ menunjukkan satu kemunculan dari kata tersebut. Output ini nantinya akan digunakan sebagai input untuk proses reduksi di MapReduce, di mana frekuensi total setiap kata dihitung. Skrip ini efektif dalam mempersiapkan data untuk analisis frekuensi kata, menggunakan prinsip pemetaan untuk mendistribusikan dan memproses data secara efisien.

# Reducer.py 
Skrip Reducer.py ini adalah bagian dari proses `Reducer` dalam paradigma MapReduce yang berfungsi untuk mengagregasi hasil output dari skrip `Mapper`. Setelah memproses baris demi baris dari STDIN, skrip ini membersihkan spasi di awal dan akhir setiap baris dan memisahkan kata dari jumlahnya berdasarkan tab yang telah didefinisikan pada skrip `Mapper`. Setiap jumlah diubah dari string menjadi integer. Skrip memeriksa apakah kata saat ini sama dengan kata sebelumnya; jika iya, ia menambahkan jumlahnya. Jika tidak, skrip mencetak kata dan jumlah total ke STDOUT sebelum mengatur ulang penghitungan untuk kata baru. Proses ini memastikan bahwa setiap kata dari input hanya dicetak sekali dengan jumlah totalnya. Pada akhir input, skrip juga memastikan kata terakhir dicetak jika perlu. Metode ini efektif untuk mengagregasi dan menghitung frekuensi setiap kata dalam data besar, memanfaatkan fitur sortir Hadoop yang mengurutkan output dari `Mapper` sebelum diteruskan ke `Reducer`.

# Menampilkan Output Pada Google Collab 
dengan kode '!$HADOOP_HOME/bin/hdfs dfs -cat /word_count/output/part-00000 | head -50' Perintah yang Aakan tampilkan 50 baris pertama dari hasil pekerjaan MapReduce pada sistem Hadoop, khususnya dari sebuah tugas penghitungan kata. Perintah ini mengeksekusi `hdfs dfs -cat` untuk menggabungkan dan menampilkan isi file output `part-00000` yang berada di direktori `/word_count/output` pada Hadoop Distributed File System (HDFS). Output dari file tersebut kemudian disaring dengan perintah `head` untuk hanya menampilkan 50 baris pertama, memungkinkan pengguna untuk cepat memeriksa dan memverifikasi hasil sebagian dari tugas yang telah dijalankan, tanpa perlu mengunduh atau melihat keseluruhan file yang mungkin sangat besar.

# Menampilkan Output Pada Google Collab ke Direktori Lokal
'!$HADOOP_HOME/bin/hdfs dfs -copyToLocal /word_count/output/part-00000 /content/HDFS_WordCount.txt' Perintah ini digunakan untuk menyalin file hasil dari pekerjaan MapReduce di Hadoop, yang terletak di `/word_count/output/part-00000`, dari Hadoop Distributed File System (HDFS) ke sistem file lokal di direktori `/content/` dengan nama `HDFS_WordCount.txt`. Ini memudahkan akses dan analisis lebih lanjut dari data output MapReduce pada lingkungan lokal.

# Berikut Tampilan Screenshot Output
![Output SS](output_keseluruhan.png)