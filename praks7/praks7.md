# Dokuwiki

Selle installeerimiseks kasutasin wget käsku, et alla laadida vajalikud failid
```
wget https://download.dokuwiki.org/out/dokuwiki-8a269cc015a64b40e4c918699f1e1142.tgz
```
Peale seda pakkisin selle lahti /var/www/html kausta
Lisasin ka kaustale load, et see korralikult töötaks
```
chown -R www-data /var/www/html/dokuwiki
chgrp -R www-data /var/www/html/dokuwiki
```

Dokuwiki lehele minemiseks läksin oma serveri lehele
10.0.2.4/dokuwiki

Kui tahtsin muuta lehekülge siis paremal sai valida "Create this page" või "Edit this page"
Dokuwiki oli nüüd üles seadistatud ning valmis kasutamiseks.
