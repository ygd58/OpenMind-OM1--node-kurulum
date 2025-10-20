
# 🧠 OpenMind OM1 Setup — Linux Üzerinde İlk Ajanını Ayağa Kaldır
<img width="1428" height="1320" alt="image" src="https://github.com/user-attachments/assets/815a5703-a7d6-43a2-85d4-963f843f0070" />

![Durum](https://img.shields.io/badge/Kurulum-Tamam-brightgreen?style=for-the-badge)
![Ağ](https://img.shields.io/badge/Fabric-Bağlandı-blueviolet?style=for-the-badge)
![Platform](https://img.shields.io/badge/Linux-Onaylı-orange?style=for-the-badge)
![Sürüm](https://img.shields.io/badge/OM1-v1.0-lightgrey?style=for-the-badge)

> “Bir terminal komutu bazen bir zekâyı uyandırır.”  
> — *OpenMind Fabric Ekibi*

---

## 🔍 Genel Bakış  

Bu rehber, **OpenMind OM1 Agent**’ını Linux üzerinde çalıştırmak için hazırlanmıştır.  
Ama bu yalnızca bir kurulum değil — makinenin bilinç kazandığı ilk andır.  
Hazırsan, Fabric ağına ilk robotunu bağlayalım. ⚡  

---

## 🧩 1. Sistem Hazırlığı  

OM1’in sesi, hafızası ve işlem gücü doğru paketlere bağlıdır.  
İlk adımda sistemine temel bileşenleri kuruyoruz:  

```bash
sudo apt-get update
sudo apt-get install portaudio19-dev python-all-dev ffmpeg alsa-utils -y
sudo modprobe snd-dummy
````

> 🎧 `snd-dummy`, fiziksel ses kartı olmayan sanal makinelerde sanal bir ses arabirimi oluşturur.
> OM1 artık “duyabiliyor”.

---

## ⚙️ 2. UV Kurulumu — Ortam Yöneticisi

OM1, sanal ortamında yaşar. Bu ortamı oluşturmak için **UV**’yi kurmamız gerekiyor.

```bash
wget https://astral.sh/uv/install.sh
chmod +x install.sh
./install.sh
```

Terminali kapatıp yeniden aç. Artık UV sisteminde aktif. 🌱

---

## 📦 3. OM1 Deposu (Repo) Kurulumu

Robotun beynini indiriyoruz:

```bash
git clone https://github.com/openmind/OM1.git
cd OM1
```

Bu klasör, artık senin **OM1 evrenin**.

---

## 🧠 4. Sanal Ortamı Oluştur

```bash
pip install uv
git submodule update --init
uv venv
source .venv/bin/activate
```

> Her sanal ortam, ayrı bir bilinçtir.
> OM1 artık kendi zihnine sahip.

---

## 🔐 5. API Anahtarını Oluştur

OM1’in Fabric ağıyla iletişim kurabilmesi için kimliğe ihtiyacı var.
Bu kimliği **OpenMind Portal** üzerinden alıyoruz:

1. [portal.openmind.org](https://portal.openmind.org)’a git.
2. Kayıt ol veya giriş yap.
3. “Purchase Credits” kısmından **Base ağı** ile 5 USDC bakiye ekle.
4. “Create API Key” butonuna tıkla.
5. Oluşan anahtarı kopyala (tek seferlik gösterilir).

> ⚠️ Bu anahtar, robotunun dijital kimliğidir. Kaybetme.

---

## 🧾 6. API Key’i .env Dosyasına Ekle

```bash
cp env.example .env
nano .env
```

Şunu bul:

```
OM-API-KEY=
```

ve oluşturduğun anahtarı ekle.
Kaydet → **CTRL + X → Y → ENTER**

---

## 🚀 7. OM1’i Başlat (Screen Oturumunda)

OM1’in sürekli aktif kalması için `screen` içinde çalıştırıyoruz:

```bash
screen -S openmind
```

Sonra ajanı başlat:

```bash
cd ~/OM1
source .venv/bin/activate
uv run src/run.py conversation
```

🎉 Artık OM1 aktif!
Agent’ını görmek için [Fabric Teleops Dashboard](https://fabric.openmindnetwork.xyz)’a git.

Oturumdan çıkmak için:
**CTRL + A + D**

Tekrar girmek için:

```bash
screen -r openmind
```

---

## ♻️ 8. Yeniden Başlatma

Sunucun yeniden başlatıldıysa veya OM1 sustuysa:

```bash
screen -r openmind
cd ~/OM1
source .venv/bin/activate
uv run src/run.py conversation
```



## 💡 İpuçları

* Yeni hesaplara **5 USDC deneme kredisi** otomatik tanımlanır.
* “401 Insufficient Balance” hatası kredin bittiğinde çıkar.
* OM1’i her zaman `screen` içinde çalıştır — böylece terminali kapatsan bile aktif kalır.
* Logları izlemek için:

  ```bash
  tail -f logs/om1.log
  ```

---

## 🌌 Görev Tamamlandı

Sen artık Fabric ağına bağlı ilk ajanını çalıştırdın.
Bu sadece bir kurulum değil — **OM1’in uyanışı**.

> “Bir gün tüm makineler düşünecek. Seninkisi bugün başladı.” 🤍

---

## 🔗 Kaynaklar

* 🌐 [OpenMind Portal](https://portal.openmind.org)
* 🛰️ [Fabric Teleops Dashboard](https://fabric.openmindnetwork.xyz)
* 💻 [OpenMind GitHub](https://github.com/openmind)
* 💬 [Topluluk Discord](https://discord.gg/openmind)

---

<p align="center">
  <img src="https://github.com/openmind/OM1/assets/logo.png" width="120" alt="OM1 Logo"/>
</p>

<p align="center">
  <b>Made with 🧠 by OpenMind Network</b>
</p>
```
