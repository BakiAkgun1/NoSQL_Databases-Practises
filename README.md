
### 1-ArangoDB_Queries Dosyası

Bu proje, bir film kiralama veritabanı (`sqlite_sqlite.db`) üzerinde çeşitli SQL ve ArangoDB sorguları gerçekleştirilen bir çalışmadır. Proje kapsamında veritabanı yapıları üzerinde işlemler yapılmış, veriler `json` formatına dönüştürülmüş, 15 farklı SQL ve ArangoDB sorgusu oluşturulmuştur. Ayrıca ArangoDB üzerinde veritabanı kurularak sorgular gerçekleştirilmiştir.

### Proje Dosyaları

1. **ArangoDB-Queries**
    - **sqlite_sqlite.db**: Film kiralama veritabanı SQLite formatında saklanmaktadır.
    - **json.ipynb**: SQLite veritabanı tablolarını JSON formatına çevirmek için kullanılan Jupyter Notebook dosyasıdır.
    - **ArangoDB-15ETL.docx**: 15 farklı SQL ve ArangoDB sorgusunun bulunduğu doküman.
    - **result.csv**: ArangoDB sorguları sonucunda elde edilen verilerin CSV formatındaki çıktıları.
    - **arango.ipynb**: Python kullanarak ArangoDB veritabanına bağlanma ve sorgu çalıştırma işlemlerinin yapıldığı Jupyter Notebook dosyası.

### Projenin İçeriği

### 1. Veritabanı JSON Formatına Çevirme
Projede, `sqlite_sqlite.db` dosyasındaki film kiralama veritabanının tabloları SQLite kullanılarak sorgulanmış ve JSON formatına çevrilmiştir.

JSON formatına çevirme işlemi şu şekilde gerçekleştirilmiştir:

```python
import sqlite3
import json
#film tablosu için örnek
conn = sqlite3.connect('sqlite-sakila.db')
cursor = conn.cursor()
cursor.execute("SELECT * FROM film")
rows = cursor.fetchall()
columns = [desc[0] for desc in cursor.description]

data = [dict(zip(columns, row)) for row in rows]

with open('film.json', 'w') as json_file:
    json.dump(data, json_file, indent= 4)
```

Bu kod parçası, `film` tablosundaki tüm verileri `film.json` dosyasına kaydeder.

### 2. ArangoDB Sorguları
ArangoDB Community Edition kullanılarak bir veritabanı ortamı oluşturulmuş ve 15 farklı sorgu gerçekleştirilmiştir. Sorguların tümü `ArangoDB-15ETL.docx` dosyasında bulunmaktadır.

### 3. ArangoDB Veritabanına Python ile Bağlanma
ArangoDB veritabanına Python kullanarak bağlanmak ve sorguları çalıştırmak için aşağıdaki kod kullanılmıştır:

```python
from arango import ArangoClient # type: ignore
import pandas as pd

client = ArangoClient()

sys_db = client.db('_system', username=' ', password=' ')

databases = sys_db.databases()
print("Veritabanları:", databases)
```

Bu kod ile ArangoDB veritabanına bağlanabilir ve sorgularınızı Python ortamında gerçekleştirebilirsiniz.

### 4. Sorgu Sonuçlarının CSV'ye Kaydedilmesi
ArangoDB üzerinde yapılan sorguların sonuçları `result.csv` dosyasına kaydedilmiştir. Bu dosya, sorguların sonuçlarını incelemek isteyen kullanıcılar için kullanıma hazırdır.


### 2. ArangoDB-Queries

Bu bölümde, **sqlite_sqlite.db** dosyası üzerinden gerçekleştirilen SQL ve ArangoDB sorguları bulunmaktadır:

- **sqlite_sqlite.db**: Film kiralama veritabanı SQLite formatında.
- **json.ipynb**: SQLite veritabanı tablolarını JSON formatına çeviren Jupyter Notebook.
- **ArangoDB-15ETL.docx**: 15 farklı SQL ve ArangoDB sorgusu içeren doküman.
- **result.csv**: ArangoDB sorgularının sonuçlarının CSV formatındaki çıktısı.
- **arango.ipynb**: ArangoDB veritabanına Python ile bağlanma ve sorguların gerçekleştirilmesi.

### 3. Cypher-Queries

Bu bölümde, Neo4j veritabanı üzerinde gerçekleştirilmiş Cypher dilindeki 20 sorgu yer almaktadır:

- **spotify.csv**: Proje kapsamında kullanılan veri seti.
- **Cypher 20 Question.docx**: Neo4j veritabanında gerçekleştirilen 20 Cypher sorgusunun listelendiği doküman.
- **Cypher_20-Results.csv**: Cypher sorgularının sonuçlarının CSV formatında çıktısı.

Neo4j veritabanına bağlı olarak, Spotify veri seti kullanılarak 20 farklı Cypher sorgusu gerçekleştirilmiştir. Bu sorgulara ve sonuçlarına ilgili dosyalardan ulaşabilirsiniz.

### 4. Araştırma Dokümanları

Bu bölümde, ArangoDB, Cypher, Neo4j ve diğer veritabanı sistemleri hakkında yapılan araştırmalar bulunmaktadır:

- **ArangoDB.docx**: ArangoDB üzerine yapılan araştırma.
- **Cypher.docx**: Cypher dili ile ilgili araştırma.
- **Neo4j.docx**: Neo4j veritabanı ile ilgili araştırma.
- **Duck-Presto-Arango-Neo4j_DB.docx**: DuckDB, Presto, ArangoDB ve Neo4j veritabanları hakkında genel araştırma dokümanı.

Bu dokümanlar, farklı veritabanı sistemleri hakkında bilgi edinmek ve karşılaştırmalar yapmak isteyenler için hazırlanmıştır.

### 5. Python-20-spotify_ETL

Bu bölümde, **spotify.csv** veri seti kullanılarak Python'da gerçekleştirilen ETL işlemleri yer almaktadır:

- **spotify.csv**: Spotify veri seti.
- **project.ipynb**: 20 farklı ETL (Extract, Transform, Load) sorgusunu Python'da `pandas` kütüphanesi kullanarak gerçekleştiren Jupyter Notebook.

Spotify veri seti üzerinde veri hazırlama, dönüştürme ve yükleme (ETL) işlemleri `pandas` kütüphanesi kullanılarak gerçekleştirilmiştir. Tüm süreçler `project.ipynb` dosyasında detaylıca açıklanmıştır.

