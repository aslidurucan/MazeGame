# MazeGame (Gezgin Robot) 🧩🤖

Bu proje, bir **labirent (maze)** haritasını bir URL üzerinden indirip belleğe alan ve gezgin bir robotun başlangıç noktasından hedefe doğru adım adım ilerlemesini simüle eden Java (Swing) tabanlı bir masaüstü uygulamasıdır. Robot ilerledikçe çevresindeki hücreleri görünür hale getirir, geçtiği yolları işaretler ve sonunda labirenti görsel olarak ekrana çizer.

---

## 📌 Proje Amacı

- URL üzerinden alınan bir metin dosyasını labirent haritasına dönüştürmek
- Labirent üzerinde robot hareketini simüle etmek
- Geçilen, görülen ve yanlış yolları işaretlemek
- Sonucu Swing arayüzünde grid yapısında göstermek
- Adım sayısı ve çalışma süresini ölçmek

---

## ⚙️ Nasıl Çalışır?

1. Kullanıcı `Main` sınıfındaki menüden URL seçer.
2. `URLReader` sınıfı URL'deki `.txt` dosyasını indirir.
3. Dosya içeriği `String[][]` matrise dönüştürülür.
4. `Engel` sınıfı bu matrisi `Hucre[][]` nesne dizisine çevirir.
5. Robot `(0,0)` konumundan başlayarak belirli bir öncelik sırasına göre hareket eder.
6. Robotun geçtiği ve gördüğü hücreler işaretlenir.
7. Son durum Swing arayüzünde görselleştirilir.
8. Toplam adım sayısı ve geçen süre konsola yazdırılır.

---

## 📂 Proje Yapısı

```
GezginRobot/
 └── src/
     └── app/
         ├── Main.java
         ├── Robot.java
         ├── Hucre.java
         ├── Engel.java
         ├── Izgara.java
         ├── URLReader.java
         ├── Uygulama.java
         ├── Button.java
         └── images/
```

---

## 🧠 Sınıfların Görevleri

### `Main.java`
- Programın giriş noktasıdır.
- Menü işlemlerini yönetir.
- Robotu çalıştırır.
- Swing penceresini oluşturur ve grid’i çizer.

### `Robot.java`
- Robotun konumunu ve hareket algoritmasını içerir.
- Adım sayısını tutar.
- Görünür hücreleri günceller.

### `Hucre.java`
Her hücre için:
- Satır / sütun bilgisi
- Engel mi?
- Ziyaret edildi mi?
- Görünür mü?
- Yanlış yol mu?

bilgilerini tutar.

### `URLReader.java`
- URL’den veri indirir.
- Satırları karakter karakter matrise çevirir.

### `Engel.java`
- Matris içindeki pozitif değerleri engel olarak işaretler.
- `Hucre[][]` yapısını oluşturur.

### `Izgara.java`
- URLReader ve Engel sınıflarını birleştirerek grid üretir.

### `Button.java`
- `JButton` türevidir.
- Hücre koordinatlarını tutar.

### `Uygulama.java`
- Süre ölçümü ve performans takibi yapar.

---

## 🌐 Varsayılan URL’ler

Kod içinde iki örnek URL tanımlıdır:

```java
static final String url1 = "http://bilgisayar.kocaeli.edu.tr/prolab2/url1.txt";
static final String url2 = "http://bilgisayar.kocaeli.edu.tr/prolab2/url2.txt";
```

Metin dosyasında:
- `0` → geçilebilir alan
- `>0` → engel

---

## 🤖 Robot Hareket Mantığı

Robot aşağıdaki öncelik sırasına göre ilerler:

1. Sağa
2. Aşağı
3. Sola
4. Yukarı

Her hareket:
- `adimSayisi` artırılır.
- Hücre `visited = true` yapılır.
- Çevredeki komşular `visible = true` yapılır.
- Çıkmaz durumunda geri dönüş yapılır ve `yanlisYol = true` işaretlenir.

---

## 🖥️ Çalıştırma

### IntelliJ IDEA ile

1. Projeyi açın.
2. `src/app/Main.java` dosyasını çalıştırın.
3. Konsoldan:
   - `1` → URL değiştir
   - `2` → Çalıştır
   - `3` → Çıkış

---

### Komut Satırı ile

```bash
cd GezginRobot/src
javac app/*.java
java app.Main
```

---

## 🖼️ Önemli: Görsel Dosya Yolu Problemi

Kod içinde ImageIcon kullanımı sabit Windows path ile yazılmıştır:

```java
new ImageIcon("C:\\Users\\...\\images\\robot.png")
```

Bu farklı bilgisayarlarda çalışmaz.

Önerilen çözüm:

```java
new ImageIcon(Main.class.getResource("/app/images/robot.png"))
```

Bu sayede görseller classpath üzerinden yüklenir.

---

## 📊 Çıktı

Program çalıştırıldığında:

- Robot labirenti çözer
- Swing penceresi açılır
- Engel, robot, yol ve başlangıç/bitiriş görselleri gösterilir
- Konsola:
  - Toplam adım sayısı
  - Geçen süre (ms)

yazdırılır.

---

## 🚀 Geliştirme Önerileri

- DFS veya BFS algoritması ile daha sağlam yol bulma
- Animasyonlu adım adım ilerleme
- Sınır kontrollerinin güçlendirilmesi
- Harita formatının genişletilmesi (boşluklu sayı desteği)
- GUI iyileştirmeleri

---

## 📌 Başlangıç Noktası

Programı başlatmak için:

```
src/app/Main.java
```

---
