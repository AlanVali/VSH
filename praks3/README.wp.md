# PHP moodulid
php moodulite installeerimiseks täiendasin faili /etc/apt/sources.list:
```
deb http://packages.dotdeb.org jessie all
deb-src http://packages.dotdeb.org jessie all
```
Peale seda salvestasin faili ja tegin apt-get update peale mida sai installida
php7.0 mooduleid käsuga
```
apt-get install php7.0-(moodul siia)
```
# Mysql

Nüüd sai installida mysql
Läksin /tmp kausta ning kasutasin käsku
```
wget https://dev.mysql.com/get/mysql-apt-config_0.8.9-1_all.deb
```
Käsuga dpkg -i mysql-apt-config_0.8.9-1_all.deb pakkisin selle lahti ning siis tuli
ette configuratsiooni aken kus sai valida versiooni
Valitud versioon on Mysql 5.6
Peale seda sai tehtud:
```
apt-get update
apt-get install mysql-community-server
```

Et sisselogida ilma paroolita pidi tegema root kodu kaustas faili
.my.cnf kuhu sai sisestatud
```
[mysql]
user=root
password=qwerty
```
# Phpmyadmin

Nüüd sai installitud phpmyadmin käsuga
```
apt-get install phpmyadmin
```
Ette tuli aken kus järgisin juhendit

Et php fail töötaks kasutaja kaustas on vaja teha lihtsalt index.php
Faili sisuks võis panna näiteks:
```
<?php echo '<p> Test </p>'; ?>
```

Sellest on aru saada et kõik töötab


# HTTPS installeerimine

Esimese asjana oli vaja teha käsud
```
apt-get update
apt-get upgrade openssl
```
Kui apache2 on juba olemas siis sai kasutada käske
```
a2enmod ssl
a2ensite default-ssl
```
Peale seda sai taaskäivitatud apache2
Tehtud sai kaust ssl asukohta /etc/apache2/ssl

Peale seda pidi n.ö allkirjastama certificati käsuga:
```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt
```
Nüüd täitsin väljad ära
Kui ette tuli küsimus "Common name"
Siis pidi sisestama oma lehekülje nime ehk minu puhul IP

Peale seda sai kasutatud chmod käsku et anda load ssl kaustale

Siis sai muudetud /etc/apache2/sites-enabled/default-ssl.conf faili (fail olemas praks3 kaustas)

Ja HTTPS oligi olemas

# Wordpress
Wordpressi installeerimiseks sai mindud /var/www/html kausta ja kasutatud käske
```
wget http://wordpress.org/latest.zip
apt install unzip
unzip -q latest.zip
```
Nüüd sai antud wordpress kaustale kindlad load, et apache saaks neid kasutada

MySQL-is sai tehtud uue andmebaasi nimega wordpress_sample

Uus kasutaja: wp_user parooliga qwerty

Kasutajale sai antud kõik privileegid

ning siis oli vaja privileege uuendada

Peale seda oli wordpress valmis kasutamiseks ning seda üles seadistada leheküljelt "Minu.IP/wordpress"

