# A. Overview Software
1. Apache Hadoop
Apache Hadoop adalah sebuah kerangka kerja perangkat lunak open-source yang memungkinkan pemrosesan data skala besar dalam lingkungan yang terdistribusi.  Dikembangkan oleh Apache Software Foundation, Hadoop dirancang untuk menyimpan dan memproses sejumlah besar data menggunakan kluster komputer yang terdiri dari banyak node.

Apache Hadoop digunakan dalam berbagai skenario yang membutuhkan pemrosesan data besar (big data), seperti analitik data, pembelajaran mesin, dan penyimpanan data untuk bisnis. Organisasi seperti perusahaan teknologi, layanan keuangan, dan sektor kesehatan menggunakan Hadoop untuk menganalisis sejumlah besar data dalam waktu yang relatif singkat, yang memungkinkan pengambilan keputusan yang lebih baik dan lebih cepat.

* Hadoop Distributed File System (HDFS)
HDFS adalah sistem penyimpanan terdistribusi yang dirancang untuk berjalan di perangkat keras standar dan menawarkan penyimpanan data yang sangat andal dan toleran terhadap kegagalan.
* MapReduce
MapReduce adalah model pemrograman dan mesin pemrosesan data dalam Hadoop. Ini memungkinkan pemrosesan paralel dari data yang besar dengan membagi tugas menjadi dua fase: Map (memetakan) dan Reduce (mengurangi).
* YARN (Yet Another Resource Negotiator)
YARN adalah manajer sumber daya di Hadoop yang mengelola dan menjadwalkan pekerjaan serta sumber daya komputasi dalam kluster Hadoop.
* Hadoop Common
Hadoop Common adalah serangkaian utilitas dan pustaka yang mendukung modul lain dalam Hadoop. Ini mencakup antarmuka pemrograman aplikasi (API) dan alat umum yang digunakan oleh komponen Hadoop lainnya.


2. Apache Derby
Apache Derby adalah sebuah sistem manajemen basis data relasional (RDBMS) yang sepenuhnya ditulis dalam Java. Ini merupakan proyek open-source dari Apache Software Foundation dan dikenal karena ukurannya yang kecil, portabilitas, serta kemampuannya untuk diintegrasikan ke dalam aplikasi Java

Apache Derby dirancang sebagai RDBMS ringan dengan ukuran sekitar 2 MB. Ukurannya yang kecil memungkinkan untuk disertakan langsung ke dalam aplikasi Java, menjadikannya pilihan populer untuk aplikasi yang membutuhkan penyimpanan data terintegrasi. Karena sepenuhnya ditulis dalam Java, Apache Derby dapat dijalankan di berbagai platform yang mendukung JVM (Java Virtual Machine), seperti Windows, macOS, dan Linux.

3. Apache Hive
Apache Hive adalah perangkat lunak open-source yang dirancang untuk mengelola dan menganalisis data besar yang disimpan dalam sistem file terdistribusi, seperti Hadoop Distributed File System (HDFS). Hive menyediakan antarmuka berbasis SQL yang memungkinkan pengguna melakukan query dan mengelola data dalam skala besar dengan mudah, tanpa perlu menulis kode MapReduce secara langsung

Apache Hive merupakan alat yang kuat untuk analisis data skala besar di lingkungan Hadoop. Ini menyediakan antarmuka yang familiar bagi pengguna SQL, memungkinkan mereka untuk menjalankan query dan analisis data besar tanpa perlu menulis kode pemrosesan data yang kompleks. Meskipun bukan solusi ideal untuk kebutuhan real-time, Hive tetap menjadi komponen penting dalam ekosistem Hadoop untuk analisis data batch.

Hive sering digunakan untuk pengolahan data warehousing di atas Hadoop, memungkinkan analisis data besar dengan SQL dan Hive digunakan untuk menjalankan proses ETL pada data dalam Hadoop, di mana data diolah dan dipersiapkan untuk analisis lebih lanjut serta Hive dapat diintegrasikan dengan alat business intelligence (BI) seperti Tableau atau Microsoft Power BI untuk visualisasi data.

HiveQL merupakan Bahasa query yang menyerupai SQL, yang memudahkan transisi bagi pengguna SQL untuk bekerja dengan data di Hadoop.

Eksekusi MapReduce di balik layar, query yang ditulis dalam HiveQL dikompilasi menjadi tugas MapReduce yang dieksekusi di atas kluster Hadoop.

Dukungan untuk Partisi dan Bucket, Hive mendukung pembagian data menjadi partisi dan bucket, yang dapat meningkatkan efisiensi query dengan memungkinkan akses yang lebih cepat ke subset data tertentu.

Integrasi dengan Hadoop Ecosystem, Hive terintegrasi dengan baik dengan komponen lain dalam ekosistem Hadoop seperti HDFS untuk penyimpanan, Apache HBase untuk penyimpanan data yang lebih terstruktur, dan Apache Tez atau Apache Spark sebagai alternatif mesin eksekusi untuk MapReduce.


# B. Dokumentasi praktik instalasi software dan perintah CRUD
1. Download software apache hadoop => [Download Hadoop](https://hadoop.apache.org/release/2.7.0.html)
2. Download software apache derby => [Download Derby] (https://db.apache.org/derby/releases/release-10_14_2_0.html)
3. Download software apache hive => [Download Hive] https://dlcdn.apache.org/hive/
4. Extract file zip ketiga software tersebut dan pindahkan ke directory C:\
5. Tambahkan di **Environment Variables…** untuk variable **DERBY_HOME, HADOOP_USER_CLASSPATH, HIVE_BIN, HIVE_HOME dan HIVE_LIB**
6. Tambahkan di **System variables** untuk variable **HADOOP_USER_CLASSPATH** dan tambahkan di variable **PATH (C:\hadoop\bin, C:\hadoop\sbin, C:\hive\bin, C:\derby\bin)**
7. Pada folder C:\hive\conf file dengan nama **hive-default.xml.template** diubah menjadi **hive-site.xml**
8. Masuk ke folder C:\hadoop\etc\hadoop, buka file hadoop-env.cmd, kemudian set JAVA_HOME=%JAVA_HOME% diubah menjadi set JAVA_HOME=C:\Java\jdk1.8.0_202
9. Masuk ke folder C:\hadoop\etc\hadoop, buka file core-site.xml, tambahkan configuration berikut:
*<configuration>*
*<property>*
*<name>fs.defaultFS</name>*
*<value>hdfs://localhost:9000</value>*
*</property>*
*</configuration>*
10. Masuk ke folder C:\hadoop\etc\hadoop, buka file mapred-site.xml, tambahkan configuration berikut:
*<configuration>*
*<property>*
*<name>mapreduce.framework.name</name>*
*<value>yarn</value>*
*</property>*
*</configuration>*
11. Buat folder *data* yang berisi folder *namenode* dan *datanode* pada folder C:\hadoop
12. Masuk ke folder C:\hadoop\etc\hadoop, buka file httpfs-site.xml, tambahkan configuration berikut:
*<configuration>*
*<property>*
*<name>dfs.replication</name>*
*<value>1</value>*
*</property>*
*<property>*
*<name>dfs.namenode.name.dir</name>*
*<value>C:\hadoop\data\namenode</value>*
*</property>*
*<property>*
*<name>dfs.datanode.data.dir</name>*
*<value>C:\hadoop\data\datanode</value>*
*</property>*
*</configuration>*
13. Masuk ke folder C:\hadoop\etc\hadoop, buka file yarn-site.xml, tambahkan configuration berikut:
*<configuration>*
*<property>*
*<name>yarn.nodemanager.aux-service</name>*
*<value>mapreduce_shuffle</value>*
*</property>*
*<property>*
*<name>yarn.nodemanager.auxservices.mapreduce.shuffle.class</name>*
*<value>org.apache.hadoop.mapred.ShuffleHandler</value>*
*</property>*
*</configuration>*
14. Buka command promt run as Administrator
15. Ketikan *start-dfs.cmd*, untuk mengaktifkan service Hadoop dfs
16. Ketikan *start-yarn.cmd*, untuk mengaktifkan service Hadoop yarn
17. Ketikan *StartNetworkServer -h 0.0.0.0*
18. Untuk memastikan semua service telah aktif, ketikan *jps*
14560 DataNode
4960 ResourceManager
5936 NameNode
768 NodeManager
14636 Jps
19. Ketikan *hive* pada command promt
20. Untuk membuat database ketikan *create database datawarehouse;*
21. Untuk menampilkan database ketikan *show database;*
22. Untuk membuat tabel ketikan *create table latihan(id int, nama string, tempat_lahir strin);*
23. Untuk menginput ke tabel yang sudah dibuat, ketikan *insert into table latihan values (1,'Iqbal','Subang');*
24. Untuk menampilkan data yang sudah diinput, ketikan *select * from latihan;*
25. Untuk mengupdate data pada table latihan, ketikan *update latihan set nama='Muhammad Iqbal' where id='1'*
26. Untuk menghapus data pada table, ketikan *delete from latihan where id='1'*

-------------------
Terima kasih



 
