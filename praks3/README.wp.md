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
