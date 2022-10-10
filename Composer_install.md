# Instalación de Composer

**Para evitar problemas con dependencias que difieren entre la máquina anfitriona y la virtual, se instaló **_composer_** directamente en la segunda antes mencionada.**


Para obtener el archivo _"composer.phar"_, se ingresa el siguiente código en la terminal:

    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
    php composer-setup.php

Hay que mover el archivo **composer.phar** hacia una carpeta que brinde el acceso global. 

    sudo mkdir -p /opt/composer && sudo mv composer.phar /opt/composer

Luego se crea un "_enlace simbólico_":

    sudo ln -s /usr/bin/composer /opt/composer/composer.phar

Tras correr el comando anterior, es posible que se muestre un mensaje advirtiendo que el archivo ya existía, de cualquier manera, se procede con el siguiente comando: 

    sudo ln -s /opt/composer/composer.phar /usr/bin/composer

Ahora **composer** puede utilizarse de manera global, para comprobarlo, se llama desde la terminal: 

    $ composer

