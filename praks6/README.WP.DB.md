# Andmebaasi server

Andmebaasi paigaldamiseks oli vaja kasutada mariadb-serveri moodulit
See sai installeeritud käskudega
```
apt-get install mariadb-server
mysql_secure_installation
```
Peale seda oli vaja minna andmebaasi ning see ära seadistada, kui sees olin kasutasin käske:
```
CREATE DATABASE wordpress;
CREATE USER 'wpuser'@'localhost' IDENTIFIED BY 'qwerty';
CREATE USER 'wpuser'@'10.2.0.4' IDENTIFIED BY 'qwerty';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wpuser'@'localhost ja 10.0.2.4';
```

Andmebaas oli nüüd valmis

Selle testimiseks sisestasin wordpressi serveril käsu:
```
mysql -u wpuser@10.0.2.6 -p
```

# Wordpressi server

Wordpressi installeerimiseks oli vaja minna läbi tavalisest wordpressi installatsiooni protsessist

Ennem oli muidugi vaja installeerida mariadb klient ja php mysql
```
apt-get install mariadb-client
apt-get install php-mysql
```

Nüüd pidi allalaadima wordpressi ning selle lahti pakkima käskudega:
```
wget http://wordpress.org/latest.zip
```
ja lahtipakkimiseks
```
unzip -q latest.zip /var/www/html/
```
Ning siis pidi andma serverile load neid kauste lugema
```
chown -R www-data:www-data /var/www/html/wordpress
chmod -R 755 /var/www/html/wordpress
```
Nüüd oligi kõik valmis. Kui soov oli siis võis modifitseerida wordpressi configuration faili, kuigi seda saab teha siis kui wordpressi lehele lähen.




