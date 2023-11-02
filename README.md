
# **Jetson Nano Kurulum adımları**

## İçindekiler

- [1. Kurulum Esnasındaki Ayarlar](#1-kurulum-esnasındaki-ayarlar)
- [2. Pip Setup](#2-pip-setup)
- [3. Jtop](#3-jtop)
- [4. TailScale](#4-tailscale)
- [5. NoMachine](#5-nomachine)
- [6. VsCode](#6-vscode)
- [7. OpenCV](#7-opencv)

## **1. Kurulum Esnasındaki Ayarlar**
* Kurulum sırasında parola sorulmadan giriş yapılabilmesi için auto login aktif edilmelidir. Eğer bu işlem yapılmadıysa kurulum bittikten sonra Settings -> User Account -> oto login aktif hale getirilmelidir.

* Settings -> Brightness & Lock Uyku seçeneklerini kapatın
## **2. Pip Setup**
(Default python3 version 3.6.9)
```bash
sudo apt update
sudo apt upgrade
sudo apt install python3-pip
pip3 --version
```
## **3. Jtop**
``` bash
sudo pip3 install -U jetson-stats
```


## **4. TailScale**
[TailScale](https://tailscale.com/download/linux) ücretsiz bir VPN hizmetidir. İndirme linki ve detaylar linkteki sayfada mevcuttur.

Alttaki komutu çalıştırdıktan sonra terminalde çıkan linke tıklayarak TailScale hesabınınz ile  cihazı bağlayama işlemini tamamlayabilirsiniz.

```bash
curl -fsSL https://tailscale.com/install.sh | sh
```

## **5. NoMachine**
NoMachine ücretsiz ve kullanımı basit bir uzaktan erişim servisidir 

[Buradaki](https://downloads.nomachine.com/download/?id=117&distro=ARM) dosya indirildikten sonra alttaki kod çalıştırılarak kurulum tamamlanır.

```bash
sudo dpkg -i nomachine_8.9.1_1_arm64.deb
```

* Kurulum bittikten sonra NoMachine Service -> Status -> Start the server at system startup seçeneği aktif hale getirilmelidir

* NoMachine Service -> Updates -> Automatically check for updates Pasif hale getirilmelidir

* Uzaktan erişmek için TailScale' e giriş yaptıktan sonra [admin panelinden](https://login.tailscale.com/admin/machines) uzaktan erişmek istenilen cihazın ip adresi kopyalandıktan sonra NoMachine -> Add kısmından ip ve port bilgileri girilerek cihaza uzaktan erişim sağlanır

* NoMachine default port: 4000


## **6. VsCode**
```bash
git clone https://github.com/JetsonHacksNano/installVSCode.git
cd installVSCode
./installVSCode.sh
```

## **7. OpenCV** 
Default olarak opencv kurulu fakat CUDA pasif haldedir. bunu aktif hale getirmek için şu adımlar uygulanır. Bu işlem minimum 2 saat sürmektedir. [Github Repo](https://github.com/mdegans/nano_build_opencv)

```bash
./build_opencv.sh
```



