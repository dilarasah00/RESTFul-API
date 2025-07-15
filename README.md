# RESTFUL-API TEST PROJESİ

Bu proje, [ahmetozmtn/RESTFul-API](https://github.com/ahmetozmtn/RESTFul-API) için API ve Veritabanı kontrol testleri içermektedir.

Testler `api_db_tests` klasöründe, test sonuçları ise `test_report.md` dosyasında yer almaktadır.

# Proje Klasör Yapısı
```
api_db_tests/
├── data/
│ ├── add_users.json # Test için kullanılan geçerli kullanıcı verileri
│ └── invalid_data_for_add.json # Negatif test verileri (eksik/boş alanlar)
│
├── tests/
│ ├── test_e2e.py # End-to-End (E2E) test senaryoları
│ └── test_negative.py # Negatif test senaryoları
│
├── test_report.md # Uygulanan senaryo özeti ve gözlemler
├── requirements_for_test.py # Testlerde kullanılan endpoint ve query tanımları
├── request_handler.py # HTTP istek yardımcı fonksiyonları (GET, POST, PUT, DELETE)
└── conftest.py # Fixture’lar ve ortak yapılandırmalar



## 🧪 Test Senaryoları

### ✅ 1. Pozitif Senaryolar (Happy Path)

- **[POST] /api/addData**  
  Kullanıcı başarıyla eklenmeli.

- **[GET] /api/getData**  
  Tüm kullanıcılar eksiksiz şekilde getirilmeli.

- **[PUT] /api/updateData/<id>**  
  Kullanıcı başarıyla güncellenmeli.

- **[DELETE] /api/deleteData/<id>**  
  Belirtilen kullanıcı başarıyla silinmeli.

- **[DELETE] /api/allDelete**  
  Tüm kullanıcılar eksiksiz şekilde silinmeli.

- **Veritabanı Kontrolleri:**  
  - Eklenen kullanıcılar veritabanında yer almalı.  
  - Güncellenen bilgiler veritabanında değişmiş olmalı.  
  - Silinen kullanıcılar veritabanında bulunmamalı.

---

### ❌ 2. Negatif Senaryolar (Olumsuz Kullanım)

- Eksik alanlarla kayıt ekleme denemesi  
- Boş alanlarla kayıt ekleme denemesi  
- Var olmayan bir ID ile kullanıcı güncelleme  
- Var olmayan bir ID ile kullanıcı silme



## 🧪 Testleri Çalıştırmak

### 1️⃣ Ortamı Hazırlama

Projeyi klonladıktan sonra, testlerin çalışması için gerekli bağımlılıkları yükleyin:

```bash
# Sanal ortam oluştur (isteğe bağlı ama önerilir)
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate     # Windows

# Gereken paketleri yükle
pip install -r requirements.txt
```

---

### 2️⃣ API Uygulamasını Başlatma

Testlerin doğru çalışabilmesi için, API sunucusunun aktif olması gerekir.

```bash
python main.py
```

API başarıyla çalıştığında aşağıdaki uç noktalar (endpoints) aktif olur:

- `POST /api/addData`
- `GET /api/getData`
- `DELETE /api/deleteData/<id>`
- `DELETE /api/allDelete`
- `PUT /api/updateData/<id>`

---

### 3️⃣ Testleri Çalıştırma

Test senaryoları `api_db_tests/tests/` klasöründe yer almaktadır.

Tüm testleri çalıştırmak için:

```bash
pytest api_db_tests/tests/
```

> ✅ Test çıktıları terminalde gösterilir. Ayrıca `test_logs.log` dosyasına log bilgileri yazılır.