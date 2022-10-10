# Crear plantilla con proyecto Laravel en máquina virtual

Después de haber instalado **composer**, es posible dar la instrucción de crear un proyecto nuevo, situado en el directorio **"sites"** de la máquina virtual. El código a ejecutar es el siguiente:

    sudo composer create-project laravel/laravel:8.6.12
    
Es posible que surja una alerta por utilizar **sudo**, es una medida de seguridad.
Si algún paquete no se logra descargar correctamente por falta de alguna dependencia; **composer** intentará guardarlo en la memoria caché e instalarlo desde ahí.
Una vez creada la carpeta, se copiará con un nuevo nombre para reemplazar la ya existente **"lfts.isw811.xyz**

    sudo cp -r laravel lfts.isw811.xyz

Cabe señalar que la ruta del archivo **.conf** en el directorio **vhosts** correspondiente al sitio web, debe estar configurada de manera que encuentre al archivo **index.html** dentro del directorio **Public** contenido en el proyecto **Laravel**. Al final se vuelve a copiar el archivo **.conf** a la ruta de **/etc/apache/sites-available** para reemplazar el anterior y se vuelve a confirmar en consola la utilización de dicho archivo:

    sudo a2ensite lfts.isw811.xyz.conf && sudo systemctl reload apache2

Por último, desde el interior del directorio del sitio se ejecuta el comando:

    php artisan serve

Con esto aparecerá en la terminal un proceso de carga para poder utilizar el sitio web con su dominio correspondiente.
