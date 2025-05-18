# 🐟 Analisis Produk Hasil Laut Sumatera

Proyek ini bertujuan untuk menganalisis data hasil laut dari berbagai kabupaten/kota di wilayah Sumatera menggunakan teknologi **Big Data**, khususnya **Hadoop Stack dan Apache Spark MLlib**. Fokus utama proyek ini adalah melakukan **klasterisasi wilayah** berdasarkan volume dan nilai produksi hasil laut, serta menyajikannya dalam bentuk visualisasi peta sebaran.

---

## 🚀 Teknologi yang Digunakan

- **Apache Hadoop** – Distributed storage dengan HDFS
- **Apache Spark** – Pemrosesan data dan ML (KMeans Clustering)
- **Apache Hive** – Query data dalam HDFS
- **Python (Folium, Geopandas)** – Visualisasi data spasial
- **Jupyter Notebook / PySpark Script** – Analisis dan pipeline
- **GitHub Actions** *(opsional)* – CI/CD pipeline untuk workflow

---

## 🧱 Arsitektur Proyek

```mermaid
graph TD;
    A[Data Sources: CSV/API/DB] --> B[Ingestion ke HDFS];
    B --> C[Apache Spark - ETL & Clustering];
    C --> D[Apache Hive - Querying];
    C --> E[Output Hasil Klaster];
    E --> F[Visualisasi Peta - Python/Folium];
