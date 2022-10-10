# Instalación de Composer

Verificar si existe PHP instalado en el equipo, de lo contrario se puede instalar con el siguiente comando:

    $ sudo apt-get intall php-cli -y

Para obtener el archivo _"composer.phar"_, se ingresa el siguiente código en la terminal:

    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    php -r "if (hash_file('sha384', 'composer-setup.php') === '55ce33d7678c5a611085589f1f3ddf8b3c52d662cd01d4ba75c0ee0459970c2200a51f492d557530c71c15d8dba01eae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
    php composer-setup.php
    php -r "unlink('composer-setup.php');"

Para lograr invocarlo desde cualquier lugar, se mueve el archivo descargado hacia el directorio **bin**:

    $ sudo mv composer.phar /usr/local/bin/composer

Ahora **composer** puede utilizarse de manera global, para comprobarlo, se llama desde la terminal: 

    $ composer

Ésto desplegará todas las opciones disponibles, que se utilizarán luego para crear un proyecto con **Laravel**.

