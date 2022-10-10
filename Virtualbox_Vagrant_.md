# Workshop 01 (Vagrant)

La instalación se realizó en Linux Lite 6 (Ubuntu Modificado).

## Instalación de Virtual Box

    sudo aptitude install virtualbox -y

## Instalación de Vagrant 

    $ sudo wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg

    $ sudo echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

    $ sudo apt update && sudo apt install vagrant

## Crear subfolders para la VM

Preferiblemente ubicar las carpetas y subcarpetas en el folder "home". Para este caso particular, se situó de la siguiente manera:

/home/VMs/Server

## Crear la VM

Una vez creadas las carpetas, se abre la terminal en la carpeta destinada para el servidor virtual y se procede a ingresar el siguiente comando:

    $ sudo vagrant init debian/bullseye64

Se creará un archivo "Vagrantfile" en la misma ubicación para configurar distintos parámetros.

## Descomentar la configuración de Red

Utilizar un editor de texto para modificar el archivo "Vagrantfile", encontrar la línea que contiene la configuración de la IP y remover el símbolo "#": 

#config.vm.network "private_network", ip: "192.168.33.10"

Recordar guardar los cambios antes de cerrar.
Es posible que se deba reingresar a editar este archivo, en caso de que la IP se encuentre fuera de rango. De ser así, simplemente cambiar sus parámetros e intentar de nuevo.

## Levantar la VM

Se ingresa el siguiente comando para iniciar la VM:

    $ sudo vagrant up


## Tomar el control de la VM por medio de SSH

Para utilizar la VM una vez que ésta esté corriendo, se ingresa el comando: 

    $ sudo vagrant ssh

Este comando simplificará los procesos para controlar la VM. 
Es posible identificar la máquina activa en la consola por medio del nombre de usuario, con el comando: 

    $ whoami

Retornará el string "vagrant" si tomó el control satisfactoriamente.
Para regresar a la máquina anfitrión, simplemente se dicta el comando: 
    
    $ exit

## Apagar la VM

La máquina virtual continuará encendida a menos que se le ordene apagarse, en este caso se emplea el comando:

    $ sudo vagrant halt

Un mensaje confirmará que la VM ha sido apagada 