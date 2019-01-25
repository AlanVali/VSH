# Virtual hosts ehk nime lahendus
Alustuseks tegin uue kausta nimega alan.ee asukohta
/var/www/alan.ee
Sinna sisse tegin public_html kausta (pole vajalik)
Kaustadele andsin õigused käskudega
```
chown -R www-data /var/www/alan.ee
chgrp -R www-data /var/www/alan.ee
```

Kausta sisse tegin ka index.html faili mis toimis saidina
Faili sisu võis olla mida tahad

Peale seda pidi kopeerima apache2 default konfiguratsiooni asukohast:
/etc/apache2/sites-available/000-default.conf
Asukohta
/etc/apache2/sites-available/alan.ee.conf

Avasin uue tehtud faili 
ning muutsin järgmised read:
```
DocumentRoot /var/www/alan.ee
ServerName alan.ee
ServerAlias www.alan.ee
```
Kõik muu jätsin samaks
Nüüd pidi lehekülje lubama ja käivitama
Käsuga:
```
a2ensite alan.ee.conf
```
ning peale seda
```
service apache2 restart
```
Kui vajalik siis peab ka minema faili
/etc/hosts
ning sinna lisama rea
(sinu VMi IP)	alan.ee
Peale seda restart apachele ning lehekülg peaks töötama.

