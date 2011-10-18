---
title: About Kebab Project
layout: wikistyle
---

# Kebab Reloaded'ın Apache Üzerine Kurulumu

## Apache etc/hosts ayarlarının yapılması

**Nano ile /etc/hosts dosyanıza domain kayıtlarını girmek**

* `sudo nano /etc/hosts`
* Root şifresinizi giriniz.
* Aşağıdaki satırı ekleyiniz

<pre>
    127.0.0.1  www.kebab.local
    127.0.0.1  static.kebab.local
</pre>

* Çıkmak için 'ctrl + x' tuşlarına basınız sonra 'Y' ile onaylıyınız.

**Nano ile Apache'nin sanal makine ayarlarının yapılması**

* `cd /etc/apache2/sites-available/`
* `sudo touch kebab.local`
* `sudo nano kebab.local`
* Aşağıdaki satırları ekliyoruz

<pre>
  <VirtualHost *:80>
    ServerName   www.kebab.local
    DocumentRoot /var/www/kebab/web
  </VirtualHost>
</pre>

* Çıkmak için 'ctrl + x' tuşlarına basınız sonra 'Y' ile onaylıyınız.
* `sudo a2ensite kebab.local`

**Git ile projeyi download etmek**

* `cd /var/www`
* `git clone git@github.com:kebab-project/kebab-project.git kebab`

**Projenin Database ayarlarını yapmak**

Kebab Reloaded varsayılan olarak SQLite veritabanını kullanır. Eğer SQLite kullancaksanız bu adımları atlayabilirsiniz.

Mysql için database ayarı

* `nano /var/www/kebab/application/configs/database.ini'
* SQLite veritabanı ayarları önüne `;` işareti kullanarak kapatınız
* MySqli veritabanı ayarlarının önünde ki `;` ifadeyi kaldırınız.
* MySqli kullanıcı adı ve şifrenizi yazınız.

<pre>
    ;database.doctrine.connections.master.dsn     = "mysql://root:root@localhost/kebab_production"
    database.doctrine.connections.master.dsn     = "sqlite:///" APPLICATION_PATH "/variables/databases/kebab_production.db"
</pre>

yerine

<pre>
    database.doctrine.connections.master.dsn     = "mysql://kullanici_adi:sifre@localhost/kebab_production"
    ;database.doctrine.connections.master.dsn     = "sqlite:///" APPLICATION_PATH "/variables/databases/kebab_production.db"
</pre>

**Veritabanını oluşturmak**

* `cd /var/www/kebab/developer/scripts/`
* `./doctrine build-all`

**Veritabanına başlangıç verilerini yüklemek**

* `./doctrine load-data`

**Kurulumu Test Etmek**

* Eğer bütün aşamalar doğru ise `www.kebab.local` adresine girdiğiniz de Kebab Project sayfasınız göreceksiniz.
* `www.kebab.local/backend` adresinde login ekranını göreceksiniz varsayılan olarak iki adet kullanıcı vardır.

* admin / admin
* member /member