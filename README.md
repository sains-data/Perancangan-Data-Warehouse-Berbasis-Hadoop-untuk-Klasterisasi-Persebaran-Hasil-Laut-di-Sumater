# 🐟 Analisis Produk Hasil Laut Sumatera

Proyek ini bertujuan untuk menganalisis data hasil laut dari berbagai kabupaten/kota di wilayah Sumatera menggunakan teknologi **Big Data**, khususnya **Hadoop Stack dan Apache Spark MLlib**. Fokus utama proyek ini adalah melakukan **klasterisasi wilayah** berdasarkan volume dan nilai produksi hasil laut, serta menyajikannya dalam bentuk visualisasi peta sebaran.

---

## 🚀 Teknologi yang Digunakan
| **No** | **Teknologi**  | **Kategori**            | **Fungsi Utama**                                                                                                                                     |
| ------ | -------------- | ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1      | Hadoop HDFS    | Storage                 | Menyimpan data mentah (bronze), hasil transformasi (silver), dan agregasi (gold) secara terdistribusi.                                               |
| 2      | Hadoop YARN    | Resource Management     | Mengatur sumber daya (CPU/RAM) dan menjadwalkan eksekusi job Spark secara terdistribusi.                                                             |
| 3      | Apache Hive    | Query Engine / Metadata | Menyediakan SQL-like interface (HiveQL) dan metadata management untuk query analitik.                                                                |
| 4      | Apache Spark   | ETL / Analytics Engine  | Melakukan pembersihan data, transformasi, klasterisasi, dan agregasi batch processing.                                                               |
| 5      | Hive Metastore | Metadata Store          | Menyimpan skema dan metadata tabel Hive yang digunakan dalam SQL query.                                                                              |
| 6      | Apache HBase   | NoSQL Database          | Menyimpan dan mengakses data besar secara real-time dengan model kolom lebar, digunakan untuk penyimpanan data hasil transformasi di lapisan Silver. |
| 7      | Apache Flume   | Data Ingestion          | Mengalirkan data hasil laut dari file eksternal (CSV/API) ke HDFS secara otomatis.                                                                   |
| 8      | Python Folium  | Visualisasi Spasial     | Menampilkan hasil analisis spasial dalam bentuk peta interaktif berbasis wilayah produksi laut.                                                      |
---

## ⚙️ Orkestrasi DAG dengan Apache Airflow
```plaintext
dag_export_pipeline:
├── task_1: fetch_csv_from_source
├── task_2: load_to_hdfs_bronze
├── task_3: spark_transform_to_silver
├── task_4: spark_aggregate_to_gold
├── task_5: hive_refresh_tables
├── task_6: metastore_management
├── task_7: spark_cluster_management
└── task_8: notify_team_or_export_to_dashboard
```


## 🧱 Arsitektur Proyek

```mermaid
graph TD;
    A[Data Sources: CSV/API/DB] --> B[Ingestion ke HDFS];
    B --> C[Apache Spark - ETL & Clustering];
    C --> D[Apache Hive - Querying];
    C --> E[Output Hasil Klaster];
    E --> F[Visualisasi Peta - Python/Folium];
