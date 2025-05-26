# 🤖 Duygu Tespitli Discord Botu – Geliştirme Rehberi

Bu projede, kullanıcının yüz ifadesine göre duygu tespiti yapan ve buna uygun şarkı öneren bir Discord botu geliştiriyoruz. Aşağıdaki özelliklerle botumuzu daha zeki, eğlenceli ve kişiselleştirilmiş hale getirebilirsiniz.

---

## 🚀 Özellik Listesi

### 🔧 1. Daha Gelişmiş Duygu Tespiti
✅ Şu an: sadece duyguyu tespit ediyor.  
✨ Geliştirme: yüz ifadesi detayları da analiz edilsin (örneğin: gülümsüyor mu, gözler açık mı?).

**Nasıl yapılır:**
- `Teachable Machine` ile yeni sınıflar (örneğin: `gülümseyen mutlu`, `ağlayan üzgün`) eklenebilir.
- Daha ileri düzey için `MediaPipe` kullanarak yüz mimikleri analiz edilebilir:
  - Göz açıklığı
  - Ağız eğriliği
  - Kaş konumu

---

### 📀 2. YouTube Linki ile Şarkı Önerisi
✅ Şu an: şarkının ismini öneriyor.  
✨ Geliştirme: doğrudan YouTube linkiyle şarkıyı oynat.

**Nasıl yapılır:**
- Şarkı isimleri ve linklerini bir sözlükte (dictionary) veya `.json` dosyasında tut.
- Bot cevabında kullanıcıya YouTube linkini gönder.

```python
song_links = {
    "Happy - Pharrell Williams": "https://www.youtube.com/watch?v=ZbZSe6N_BXs"
}

from gtts import gTTS
tts = gTTS("Sen mutlu görünüyorsun! Bu şarkıyı dinle!", lang='tr')
tts.save("voice.mp3")

{
  "123456789": {
    "last_emotion": "üzgün"
  }
}

responses = {
    "tr": {"happy": "Mutlu görünüyorsun! 🎉"},
    "en": {"happy": "You look happy! 🎉"}
}

with open("happy_avatar.png", "rb") as image:
    await bot.user.edit(avatar=image.read())
