# 📊 Project Assistant

Project Assistant, proje yönetimini kolaylaştırmak için geliştirilmiş **Streamlit tabanlı bir uygulamadır**.  
Bu sistem, yerel dosyalardan oluşturulan bağlamı (**RAG - Retrieval Augmented Generation**) kullanarak proje bilgilerini **LLM modeli** üzerinden yanıtlayabilmektedir.  

---

## 🚀 Özellikler

- **Proje Sohbet Asistanı**: Kullanıcı sorularını anlayarak ilgili proje verilerinden yanıtlar üretir.  
- **RAG Entegrasyonu**: `data/Projeler` klasöründen içerik taranarak bağlam oluşturulur.  
- **LLM Destekli Yanıtlar**: `llm.py` aracılığıyla Ollama modelleri (örn. `gpt-oss:20b`) kullanılır.  
- **Proje Kartları & Doküman Erişimi**: Projeler için oluşturulan kayıtlı proje kartları ile toplantı konularına, tarihlerine, notlarına ve dokümanlarına hızlı erişim.  
- **Yerel Embedding Desteği**: `Embedding/` klasöründe saklanan `paraphrase-multilingual-MiniLM-L12-v2` modeli ile vektör aramaları.  
- **Modüler Yapı**: Tüm fonksiyonlar `src/` altında modüler olarak ayrılmıştır.  
- **Tamamen Yerel Çalışma**: İnternet bağlantısına gerek olmadan çalışabilir.  

---

## 🖥️ Arayüzler

Uygulama **2 ana arayüzden** oluşmaktadır:

1. **Proje Sohbet Asistanı (Project bot) (Chat UI)**  
   - Kullanıcı, doğal dilde soru sorar.  
   - Sistem `data/Projeler` klasöründen RAG ile bağlam çıkarır.  
   - Yanıtlar, Ollama üzerinden çalışan **LLM modeli** ile üretilir.  

2. **Proje Kartları Arayüzü (Project Cards)**  
   - Proje bazlı toplantı konuları, tarihleri, notları ve dokümanlarına erişim sağlar.  
   - Kullanıcı, belirli projeler için kayıtlı içerikleri görebilir.  
   - Kart tabanlı görselleştirme ile kolay kullanım sunar.  

---

## 📂 Proje Yapısı

```
ProjectAssistant/
├── app.py                # Ana Streamlit uygulaması
├── config.py             # Genel ayarlar ve yapılandırma
├── requirements.txt      # Python bağımlılıkları
├── README.md             # Genel açıklamalar
├── data/                 # Proje verileri
├── Embedding/            # Yerel embedding modeli
└── src/                  # Uygulama modülleri
    ├── docs.py           # Doküman okuma/işleme
    ├── llm.py            # LLM etkileşimi
    ├── prompts.py        # Sistem promptları
    ├── rag.py            # RAG işlemleri
    ├── storage.py        # Veri kayıt yönetimi
    ├── ui.py             # Streamlit UI bileşenleri
    └── utils.py          # Yardımcı fonksiyonlar
```

---

## ⚙️ Kurulum

1. **Proje dosyalarını indir**  
   - Projeyi `.zip` dosyası olarak indir ve bir klasöre çıkart.  
   - Örneğin: `C:\ProjectAssistant\`  

2. **Gerekli Python bağımlılıklarını kur**  
   Proje klasöründe aşağıdaki komutu çalıştır:  
   ```bash
   pip install -r requirements.txt
   ```  

3. **Embedding modelini hazırla**  
   - `Embedding/` klasöründe `paraphrase-multilingual-MiniLM-L12-v2` modeli bulunmalıdır.  
   - Eğer yoksa Hugging Face’den indirip bu klasöre kopyalayabilirsin.  

4. **LLM modelini yükle (Ollama ile)**  
   - [Ollama](https://ollama.ai/) LLM çalışma platformunu kur.  
   - Terminal veya komut satırında:  
     ```bash
     ollama pull gpt-oss:20b
     ```  
   - Bu model indirildikten sonra uygulama, sorulara yanıt üretmek için bunu kullanacaktır.  

5. **Uygulamayı çalıştır**  
   ```bash
   streamlit run app.py
   ```  

---

## 🔧 Yapılandırma

- **config.py** dosyası ile uygulamanın genel ayarları yönetilir:  
  - Varsayılan model adı  
  - Veri yolları  
  - UI ayarları  

---

## 📌 Notlar

- Proje, tamamen yerel çalışacak şekilde tasarlanmıştır.  
- Tüm veri kaynakları `data/Projeler` ve `data/Proje Dokümanları` klasörlerinde bulunmalıdır.  
- Her proje için ilgili dokümanlar `data/Proje Dokümanları/<Proje Adı>/` altında tutulmalıdır.  
- Kullanılan modeller:  
  - **LLM Modeli**: Ollama üzerinden `gpt-oss:20b`  
  - **Embedding Modeli**: `paraphrase-multilingual-MiniLM-L12-v2`  
