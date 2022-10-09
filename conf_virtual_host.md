# Creación de directorios para páginas Web y archivos de configuración.

Se debe crear un árbol de directorios en la máquina física para separar los archivos necesarios de distintas páginas web, ubicando la terminal en la carpeta de **vagrant** donde se encuentra el _Vagrantfile_. Los directorios corresponden a las páginas web de _lfts.isw811.xyz_ y _miblog.com_, se crearán con el comando **mkdir** con la instrucción **-p** para crear las subcarpetas inexistentes de una vez:

    $ sudo mkdir -p sites/lfts.isw811.xyz/public && sudo mkdir -p sites/miblog.com

Luego se crean los archivos _index.html_ correspondientes, con el comando **touch**

    $ sudo touch sites/lfts.isw811.xyz/public/index.html && sudo touch sites/miblog.com/index.html

Para agregar un saludo en el contenido de los archivos _index.html_ basta con ejecutar los siguientes comandos para cada caso: 

    $ echo '<h1>Hola Mundo!</h1>' | sudo tee sites/lfts.isw811.xyz/public/index.html
    $ echo '<h1>Bienvenido a mi blog!</h1>' | sudo tee sites/miblog.com/index.html

## Creación de archivos .conf

Los virtual host requieren ser habilitados mediante unos archivos ,conf que brindan instrucciones para los servicios.
Desde la máquina física se crean las plantillas en la carpeta sincronizada de **Vagrant**: 

    $ sudo touch lfts.isw811.xyz.conf && sudo touch miblog.com.conf

Una vez creados, se abre el editor de preferencia (en este caso **nano**) y se pega la siguiente información: 

***Para el archivo _lfts.isw811.xyz.conf_ *** 

    <VirtualHost *:80>
    ServerAdmin webmaster@lfts.isw811.xyz
    ServerName lfts.isw811.xyz

    # Indexes + Directory Root.
    DirectoryIndex index.php index.html
    DocumentRoot /home/vagrant/sites/lfts.isw811.xyz/public

    <Directory /home/vagrant/sites/lfts.isw811.xyz/public>
        DirectoryIndex index.php index.html
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/lfts.isw811.xyz.error.log
    LogLevel warn
    CustomLog ${APACHE_LOG_DIR}/lfts.isw811.xyz.access.log combined
    </VirtualHost>


***Luego para el archivo _miblog.com.conf_ *** 

    <VirtualHost *:80>
    ServerAdmin webmaster@miblog.com.conf
    ServerName miblog.com

    # Indexes + Directory Root.
    DirectoryIndex index.php index.html
    DocumentRoot /home/vagrant/sites/miblog.com

    <Directory /home/vagrant/sites/miblog.com>
        DirectoryIndex index.php index.html
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/miblog.com.error.log
    LogLevel warn
    CustomLog ${APACHE_LOG_DIR}/miblog.com.access.log combined
    </VirtualHost>

Queda pendiente copiar cada archivo de configuración dentro de la carpeta **"sites-available"** de **Apache** desde la máquina virtual:

    $ sudo cp /vagrant/sites/lfts.isw811.xyz/lfts.isw811.xyz.conf /etc/apache2/sites-available/
    $ sudo cp /vagrant/sites/miblog.com/miblog.com.conf /etc/apache2/sites-available/

Por cada archivo copiado en **/etc/apache2/sites-available**, se habilita el sitio (en este caso, _lfts.isw811.xyz_) de la siguiente manera:

    $ sudo apache2ctl -t
    $ sudo a2ensite ltfs.isw811.xyz.conf
    $ sudo systemctl reload apache2.service

Lo mismo para _miblog.com_:

    $ sudo apache2ctl -t
    $ sudo a2ensite miblog.com.conf
    $ sudo systemctl reload apache2.service

Y listo! Ahora solo falta confirmar que los sitios web estén disponibles, ingresando sus dominios correspondientes en el navegador, deberá aparecer el saludo creado anteriormente. 



