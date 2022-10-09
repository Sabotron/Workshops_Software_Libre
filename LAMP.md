#Instalación de paquetes necesarios para crea un entorno **LAMP**

Dentro de la máquina virtual que se usará como servidor, se instalan las siguientes dependencias básicas (pero necesarias):

 + apache2
 + curl
 + git
 + mariadb-server
 + mariadb-client
 + php7.4
 + php7.4-bcmath
 + php7.4-curl
 + php7.4-json
 + php7.4-mbstring
 + php7.4-mysql
 + php7.4-xml

Se pueden ejecutar todas las instalaciones con un solo comando, la instrucción **-y** automatizará la confirmación para instalar cada uno de los paquetes:

	$ sudo apt-get install apache2 curl git mariadb-server mariadb-client php7.4 php7.4-bcmath php7.4-curl php7.4-json php7.4-mbstring php7.4-mysql php7.4-xml -y

Cuando la instalación haya sido exitosa, se procede deben habilitar varios módulos necesarios con el siguiente comando:

    $ sudo a2enmod vhost_alias rewrite ssl && sudo systemctl restart apache2

El **ServerName** de Apache en la máquina virtual, se configura de esta manera:

    $ echo "ServerName webserver" | sudo tee -a /etc/apache2/apache2.conf

Se puede comprobar desde el navegador 
