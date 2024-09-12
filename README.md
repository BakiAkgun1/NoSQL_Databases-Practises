
# NoSQL Veritabanı Sorguları ve ETL Projesi

Bu proje, ArangoDB, Neo4j ve Python kullanılarak gerçekleştirilen veritabanı sorguları ve ETL işlemlerini içermektedir. Projede farklı veritabanı sistemleri üzerinde sorgular yapıldı, sonuçlar CSV formatında kaydedildi ve araştırma dokümanları oluşturuldu. Ayrıca Spotify veri seti kullanılarak Python'da ETL süreçleri uygulandı.

## Proje Adımları:
1. **ArangoDB Sorguları**: SQLite veritabanındaki tablolar JSON formatına dönüştürüldü ve ArangoDB üzerinde 15 farklı sorgu gerçekleştirildi. Sorgu sonuçları CSV formatında saklandı.
   
2. **Neo4j ve Cypher Sorguları**: Neo4j veritabanında, Cypher dili kullanılarak 20 farklı sorgu yapıldı ve sonuçlar CSV dosyasına kaydedildi.

3. **Araştırma Dokümanları**: ArangoDB, Neo4j ve Cypher gibi veritabanı sistemleri hakkında çeşitli araştırmalar yapıldı ve ilgili dokümanlar oluşturuldu.

4. **Python ile ETL İşlemleri**: Spotify veri seti kullanılarak Python'da `pandas` kütüphanesi ile 20 farklı ETL işlemi gerçekleştirildi ve süreçler Jupyter Notebook formatında belgelendi.


Bu proje, veritabanı yönetimi, sorgulama dilleri ve veri işleme alanlarında çalışmak isteyenler için kapsamlı bir referans niteliğindedir.

![_e9b99b89-6d81-4125-8d5e-8a087ffbc771](https://github.com/user-attachments/assets/1c3bea86-6383-41d7-9113-c3f6874ec53e)

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

###  Veritabanı JSON Formatına Çevirme
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

### ArangoDB Sorguları
ArangoDB Community Edition kullanılarak bir veritabanı ortamı oluşturulmuş ve 15 farklı sorgu gerçekleştirilmiştir. Sorguların tümü `ArangoDB-15ETL.docx` dosyasında bulunmaktadır.

###  ArangoDB Veritabanına Python ile Bağlanma
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

###  Sorgu Sonuçlarının CSV'ye Kaydedilmesi
ArangoDB üzerinde yapılan sorguların sonuçları `result.csv` dosyasına kaydedilmiştir. Bu dosya, sorguların sonuçlarını incelemek isteyen kullanıcılar için kullanıma hazırdır.


### 2. ArangoDB-Queries
![image](https://github.com/user-attachments/assets/791e20e4-58f8-464f-9a8d-bb5b104c73e2)

Bu bölümde, **sqlite_sqlite.db** dosyası üzerinden gerçekleştirilen SQL ve ArangoDB sorguları bulunmaktadır:

- **sqlite_sqlite.db**: Film kiralama veritabanı SQLite formatında.
- **json.ipynb**: SQLite veritabanı tablolarını JSON formatına çeviren Jupyter Notebook.
- **ArangoDB-15ETL.docx**: 15 farklı SQL ve ArangoDB sorgusu içeren doküman.
- **result.csv**: ArangoDB sorgularının sonuçlarının CSV formatındaki çıktısı.
- **arango.ipynb**: ArangoDB veritabanına Python ile bağlanma ve sorguların gerçekleştirilmesi.

### 3. Cypher-Queries
![image](https://github.com/user-attachments/assets/5c5ad5cb-2a68-4b03-983e-fb6565e05360)

Bu bölümde, Neo4j veritabanı üzerinde gerçekleştirilmiş Cypher dilindeki 20 sorgu yer almaktadır:

- **spotify.csv**: Proje kapsamında kullanılan veri seti.
- **Cypher 20 Question.docx**: Neo4j veritabanında gerçekleştirilen 20 Cypher sorgusunun listelendiği doküman.
- **Cypher_20-Results.csv**: Cypher sorgularının sonuçlarının CSV formatında çıktısı.

Neo4j veritabanına bağlı olarak, Spotify veri seti kullanılarak 20 farklı Cypher sorgusu gerçekleştirilmiştir. Bu sorgulara ve sonuçlarına ilgili dosyalardan ulaşabilirsiniz.

### 4. Araştırma Dokümanları

Bu bölümde, ArangoDB, Cypher, Neo4j ve diğer veritabanı sistemleri hakkında yapılan araştırmalar bulunmaktadır:
![image](https://github.com/user-attachments/assets/314ff5a7-a43d-45b1-9d76-9eaece423841)

- **ArangoDB.docx**: ArangoDB üzerine yapılan araştırma.
- **Cypher.docx**: Cypher dili ile ilgili araştırma.
- **Neo4j.docx**: Neo4j veritabanı ile ilgili araştırma.
- **Duck-Presto-Arango-Neo4j_DB.docx**: DuckDB, Presto, ArangoDB ve Neo4j veritabanları hakkında genel araştırma dokümanı.

Bu dokümanlar, farklı veritabanı sistemleri hakkında bilgi edinmek ve karşılaştırmalar yapmak isteyenler için hazırlanmıştır.

### 5. Python-20-spotify_ETL
![image](https://github.com/user-attachments/assets/3d83e7bc-a89f-47eb-a3ab-5db3e5263d72)

Bu bölümde, **spotify.csv** veri seti kullanılarak Python'da gerçekleştirilen ETL işlemleri yer almaktadır:

- **spotify.csv**: Spotify veri seti.
- **project.ipynb**: 20 farklı ETL (Extract, Transform, Load) sorgusunu Python'da `pandas` kütüphanesi kullanarak gerçekleştiren Jupyter Notebook.

Spotify veri seti üzerinde veri hazırlama, dönüştürme ve yükleme (ETL) işlemleri `pandas` kütüphanesi kullanılarak gerçekleştirilmiştir. Tüm süreçler `project.ipynb` dosyasında detaylıca açıklanmıştır.

