# Guia instalacion phpMyadmin

1. Descargamos el paquete desde la pagina web:
  [phpMyadmin](https://www.phpmyadmin.net/downloads/)

* Descomprimimos y proseguimos:

  ```bash
  unzip nombre_del_archivo.zip
  ```

* movemos a la ubicacion deseada:

  ```bash
  sudo mv phpMyAdmin-x.y.z /var/www/html/
  ```

* configuramos phpMyadmin:

  ```bash
  cd /var/www/html/phpMyAdmin-x.y.z
  cp config.sample.inc.php config.inc.php
  ```

* probamos acceder desde el navegador a phpmyadmin:
  <http://localhost/phpMyadmin****etc>..

* verificamos: nano /var/www/html/phpMyAdmin-5.2.1-all-languages/config.inc.php

  ```bash
   $cfg['Servers'][$i]['auth_type'] = 'cookie';
   $cfg['Servers'][$i]['host'] = 'localhost';
   $cfg['Servers'][$i]['compress'] = false;
   $cfg['Servers'][$i]['AllowNoPassword'] = false;
  ```
