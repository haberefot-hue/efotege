# EFOT Web Sitesi — Kurulum ve Kullanım Rehberi

Bu klasör, Ege Üniversitesi Fotoğraf Topluluğu web sitesinin tamamını içerir:

| Klasör / dosya | Ne işe yarar |
|---|---|
| `index.html` | Sitenin kendisi (tasarım ve kod) |
| `content/` | Sitedeki tüm içerik: duyurular, sergiler, portfolyo, bülten, dergiler, envanter… |
| `images/` | Tüm fotoğraflar. Panelden yüklenenler `images/uploads/` içine gider |
| `admin/` | Yönetim paneli (`siteadresi/admin`) |

İçerik **yönetim panelinden** düzenlenir; kod bilgisi gerekmez. Kurulum bir kez yapılır.

---

## 1. GitHub'a yükleme

Site dosyaları GitHub'da saklanır; panelde yapılan her değişiklik oraya kaydedilir.

1. [github.com](https://github.com) üzerinden, topluluğun ortak e-postasıyla bir hesap açın.
2. Sağ üstteki **+** → **New repository**. Ad: `efot-site`. Diğerlerini olduğu gibi bırakıp **Create repository**.
3. Dosyaları yükleyin. En kolay yol **GitHub Desktop** uygulamasıdır ([desktop.github.com](https://desktop.github.com)):
   - Uygulamada depoyu bilgisayarınıza klonlayın (**Clone repository**).
   - Bu klasörün **içindeki** tüm dosya ve klasörleri, klonladığınız klasöre kopyalayın.
   - Uygulamada bir açıklama yazıp **Commit to main**, ardından **Push origin**.

   > Tarayıcıdan yüklemek isterseniz: GitHub tek seferde en fazla 100 dosya kabul eder. Önce `images` dışındaki her şeyi, sonra `images` içindeki klasörleri parça parça sürükleyin.

## 2. Netlify'da yayına alma

1. [netlify.com](https://netlify.com) → aynı e-postayla hesap açın (**Sign up with GitHub** en pratiğidir).
2. **Add new site** → **Import an existing project** → **GitHub** → `efot-site` deposunu seçin.
3. Ayarlarda **Build command** boş, **Publish directory** boş (ya da `/`) kalsın → **Deploy**.
4. Bir dakika içinde site `rastgele-ad.netlify.app` adresinde yayında olur.
5. Adı değiştirmek için: **Site configuration** → **Change site name** (örn. `efot-ege`).

## 3. Yönetim panelini açma (bir kerelik)

Panelin GitHub ile giriş yapabilmesi için iki anahtar gerekir.

**a) GitHub'da uygulama oluşturun**
1. GitHub → sağ üstte profil fotoğrafı → **Settings** → en altta **Developer settings** → **OAuth Apps** → **New OAuth App**.
2. Doldurun:
   - *Application name:* `EFOT Panel`
   - *Homepage URL:* sitenizin adresi (örn. `https://efot-ege.netlify.app`)
   - *Authorization callback URL:* `https://api.netlify.com/auth/done`
3. **Register application** → açılan sayfadaki **Client ID**'yi kopyalayın, **Generate a new client secret** ile gizli anahtarı üretip onu da kopyalayın.

**b) Netlify'a tanıtın**
1. Netlify'da sitenizde **Site configuration** → **Access & security** (bazı hesaplarda *Access control*) → **OAuth**.
2. **Install provider** → **GitHub** → Client ID ve Client Secret'ı yapıştırıp kaydedin.

**c) Panel ayarındaki depo adını yazın**
1. GitHub'da deponuzda `admin/config.yml` dosyasını açın → kalem simgesi (**Edit**).
2. `repo: GITHUB-KULLANICI-ADI/efot-site` satırını kendi kullanıcı adınızla değiştirin (örn. `repo: efotege/efot-site`).
3. **Commit changes**.

**d) Giriş yapın**
`https://siteadresiniz/admin` adresine gidin → **GitHub ile giriş yap**. Panel açılır.

## 4. Başka yöneticiler eklemek

Paneli kullanacak her kişinin bir GitHub hesabı olmalı. GitHub'da depo → **Settings** → **Collaborators** → **Add people** ile ekleyin. Davet kabul edildiğinde `/admin` adresinden giriş yapabilirler. Görevi biten yöneticileri buradan çıkarabilirsiniz.

## 5. Panelin kullanımı

- Sol menüden bölümü seçin (Sergiler, Duyurular, Envanter…).
- Listelerde **Ekle** ile yeni öğe açılır; öğeleri tutup sürükleyerek sıralayabilirsiniz. Sitede de aynı sırayla görünür.
- İşiniz bitince üstteki **Yayınla** (Publish) düğmesine basın. Değişiklik yaklaşık 1 dakika içinde siteye yansır.

**Fotoğraf yüklerken:** Panel fotoğrafları küçültmez. Telefondan ya da makineden gelen dosyaları yüklemeden önce uzun kenarı **1600–2000 piksel**, boyutu **1 MB'ın altında** olacak şekilde küçültün (ör. squoosh.app ücretsiz ve tarayıcıda çalışır). Böylece site hızlı açılır.

## 6. Alan adı (isteğe bağlı)

Netlify'da **Domain management** → **Add a domain**. Üniversiteden `efot.ege.edu.tr` gibi bir alt alan adı alırsanız ya da `efot.com.tr` gibi bir adres satın alırsanız buradan bağlayıp ekrandaki yönergeleri izleyin. Netlify ücretsiz HTTPS sertifikasını kendisi ekler.

---

**Not:** Siteyi bilgisayarınızda `index.html`'e çift tıklayarak açarsanız içerik görünmez; bu normaldir. İçerik ayrı dosyalardan yüklendiği için site yalnızca yayındayken (Netlify) doğru çalışır.
