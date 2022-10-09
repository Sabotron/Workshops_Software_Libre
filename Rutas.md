
# Creación de Rutas en la máquina anfitriona

En el archivo _hosts_ se ingresan los siguientes dominios:

   + **webserver**
   + **mibanco.com**
   + **lfts.isw811.xyz**
   + **miblog.com**

La **IP** será la misma que fue asignada en el archivo _Vagrantfile_ para la máquia virtual.
El comando para editar el archivo con **nano** es el siguiente:

    $ sudo nano /etc/hosts

Dentro del archivo se agregan los dominios después de la **IP**, por ejemplo:

	192.168.58.10 webserver
	192.168.58.10 mibanco.com
	192.168.58.10 lfts.isw811.xyz
	192.168.58.10 miblog.com

Se guardan los cambios con **ctrl + o**, luego se confirma la acción con **Enter** para después salir del editor usando **ctrl + x**

Para comprobar que los dominios responden a las solicitudes correctamente, se puede hacer _ping_ a cada uno de ellos por separado:

    $ ping webserver
    $ ping mibanco.com
    $ ping lfts.isw811.xyz
    $ ping miblog.com

***el nombre del primer dominio en la lista será el que aparezca junto a la confirmación de los paquetes enviados, aunque se solicite otro dominio.***

Para cambiar el nombre de la máquina virtual, se accede a ella con la orden **vagrant ssh** y se ingresa el siguiente comando: 

    $ sudo hostnamectl set-hostname webserver && sudo sed -i -e 's/bullseye/webserver/g' /etc/hosts

El nombre por default de la distro será reemplazado por **_'webserver'_**.