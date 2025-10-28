
# 🚀 FITNESS BİLGİ ASİSTANI - PROJE RAPORU VE ÇALIŞMA KILAVUZU

Bu rapor, projenin teknik mimarisini, kullanılan teknolojileri ve canlı web arayüzünün nasıl kullanılacağını detaylandırmaktadır.

---

## 📐 BÖLÜM A: ÇÖZÜM MİMARİSİ (RAG)

### A.1 Mimarinin Çözdüğü Temel Problem
**Problem:** Büyük Dil Modellerinin (LLM) uydurma (halüsinasyon) eğilimi ve özel/niş konularda bilgi yetersizliği.
**RAG Çözümü:** LLM (Gemini 2.5 Flash), cevap vermeden önce **güvenilir, özel veri setimizden** ilgili bilgiyi (Bağlamı) bulmaya zorlanır. Bu, doğruluk oranını artırır ve güncel kalmayı sağlar.

### A.2 Kullanılan Teknolojiler
| Kategori | Teknoloji | Rolü |
| :--- | :--- | :--- |
| **Büyük Dil Modeli (LLM)** | **Google Gemini 2.5 Flash** | Nihai cevabı, sağlanan bağlama göre üretir. |
| **Orkestrasyon** | **LangChain (LCEL)** | RAG zincirinin adımlarını (Prompt, LLM, Retriever) yöneten çerçevedir. |
| **Vektör DB** | **ChromaDB** | Veri parçalarının vektör formunda tutulduğu yerel veritabanı. |
| **Vektörleştirme** | **Sentence-Transformers** | Metinleri arama yapılabilir sayı dizilerine (Vektörlere) çevirir. |
| **Web Arayüzü** | **Gradio** | Son kullanıcının erişebileceği sohbet arayüzünü sağlar. |

### A.3 RAG Akış Şeması
Proje, her sorguda şu akışı izler:
Soru $
ightarrow$ ChromaDB (Arama) $
ightarrow$ İlgili Veri Parçaları $
ightarrow$ Prompt Şablonu $
ightarrow$ Gemini $
ightarrow$ Nihai Cevap

---

## 🌐 BÖLÜM B: WEB ARAYÜZÜ & PRODUCT KILAVUZU (Test ve Kabiliyetler)

Bu bölüm, canlı uygulamanın nasıl kullanılacağını, hangi kabiliyetlere sahip olduğunu ve test senaryolarını içerir.

### B.1 Uygulama Linki (Deploy Link)
Canlı uygulamaya erişim linki aşağıdadır. https://34a77e75c55bcd5454.gradio.live


### B.2 Kullanıcı Akışı ve Çalışma Prensibi

Kullanıcı, Gradio arayüzünde sadece soru yazar. Arka planda sistem, sorulan konuya **yalnızca kendi bilgi havuzunda** arama yaparak cevap bulur.

**Arayüz Görünümü (Boş Başlangıç):**
*https://github.com/NisanIrmakMarangoz/images-/blob/main/Bosarayuz.png*

**Çalışma Akışı Özeti:**
1.  **Girdi:** Kullanıcı Fitness, Beslenme veya Programlama sorusu sorar.
2.  **Arama:** RAG sistemi, özel veri setimizde en uygun bilgiyi (Bağlamı) bulur.
3.  **Cevap Üretme:** Gemini, bu bağlamı kullanarak, dışarıdan bilgi eklemeden cevabı üretir.
4.  **Hata Yönetimi:** Bilgi seti dışında kalan sorularda, sistem **"Bu konuda veri setimde bilgi bulunmamaktadır."** uyarısıyla güvenilirliğini korur.

### B.3 Projenin Temel Kabiliyetleri ve Test Senaryoları

Projenin başarıyla çalıştığını göstermek için aşağıdaki testleri arayüzde uygulayın:

| Kabiliyet Alanı | Test Sorusu | Amacı (Kanıtı) |
| :--- | :--- | :--- |
| **Egzersiz Uzmanlığı** | "Bench Press'te hangi kaslar çalışır?" | Temel veri setindeki spesifik bilgiyi doğru getirdiğini kanıtlar. |
| **Genişletilmiş Bilgi (Beslenme)** | "Kreatin takviyesinin faydaları ve günlük dozu nedir?" | Sonradan eklenen ve vektörleştirilen yeni bilgiyi kullanabildiğini test eder. |
| **Programlama Kapsamı** | "Push/Pull/Legs sistemi kimler için uygundur?" | Antrenman programlama bilgisini sunabildiğini gösterir. |

**Örnek Başarılı Cevap:**
*https://github.com/NisanIrmakMarangoz/images-/blob/main/basarilicevap1.png*
*https://github.com/NisanIrmakMarangoz/images-/blob/main/basarilicevap2.png*

**Halüsinasyon Önleme (Hata Yönetimi):**
| Kabiliyet Alanı | Test Sorusu | Amacı (Kanıtı) |
| :--- | :--- | :--- |
| **Halüsinasyon Önleme** | "En popüler 5 yoga pozu nedir?" | Sistemin bilmediği bir alanda **uydurmadığını** göstererek RAG'ın ana faydasını kanıtlar. |

**Örnek Hata Yönetimi:**
*https://github.com/NisanIrmakMarangoz/images-/blob/main/hatamesaji.png*


