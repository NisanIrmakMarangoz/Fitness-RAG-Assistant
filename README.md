
# Fitness Bilgi Asistanı (RAG - Gemini Destekli)

Bu proje, **Retrieval Augmented Generation (RAG)** mimarisi ile
geliştirilmiş küçük çaplı bir fitness chatbotudur.

## Projenin Amacı

Projenin amacı, veri setinde yer alan bilgilere
göre bazı egzersizler (örnek: deadlift, squat, bench press vb.) ve beslenme hakkında
sorulan soruları doğru ve güvenilir bir şekilde cevaplamaktır.

## Özellikler

* **Veri Kapsamı:** Beslenme ve temel egzersizler hakkında detaylı veri.
* **Yapay Zeka Modeli:** Google **Gemini API** kullanılır.
* **Mimari:** **LangChain LCEL** (Expression Language) ile oluşturulmuş RAG zinciri.
* **Veri Yönetimi:** **Vektörleştirme** ile veriye hızlı erişim.

## Çalıştırmak İçin

1.  **Colab not defterindeki hücreleri sırayla tek tek çalıştırın.**
2.  **API Anahtarı Kontrolü:** Eğer API anahtarı çalışmazsa, soldaki kilit simgesine tıklayın ve API anahtarınızın doğru tanımlandığından emin olun.
3.  **Arayüze Geçiş:** Tüm hücreler çalıştırılınca (son aşamada) Gradio arayüzü otomatik olarak açılacaktır.
4.  **Sorgulama:** İsterseniz verilen 3 örnek sorgudan birini veya veri setinin içinde yer alacak şekilde istediğiniz soruyu sorabilirsiniz.

## Çözüm Mimarisi
**Çözülen Problem: LLM Halüsinasyonu**

**Projemiz, LLM'e cevap vermeden önce güvenilir bir kaynaktan (kendi veri setimizden) ilgili bilgiyi bulmasını zorunlu kılarak bu problemi ortadan kaldırır.**

**https://github.com/NisanIrmakMarangoz/Fitness-RAG-Assistant**


**https://466f49412a63b9083a.gradio.live**

