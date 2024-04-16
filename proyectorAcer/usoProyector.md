# Guia De Uso Proyector Acer - Huayra Linux

![imagen acer c120](https://clasicdn.paraguay.com/pictures/2016/07/29/330454/1972959L.jpg)

## Instalacion

solo en caso de no estar configurado:

1. instalamos paquetes necesarios:

```bash
sudo apt-get install git ffmpeg mplayer
```

2. Clonamos el repositorio desde donde instalaremos los controladores y demas necesario apra que ande nuestro proyector.

```bash
git clone https://github.com/slavrn/gm12u320.git
```

3. Dentro del repo encontraremos un archivo, el cual nos guiara para realizar la indtalacion de los paqutes necesarios para poder hacer andar el proyector:

```bash
 administrador@conectarigualdad  ~/gm12u320   master  cat INSTALL.spanish

 INSTALACIÓN
Se describe la correcta instalación para Debian 7.0. El procedimiento para
otras distribuciones puede variar.

1.- Este seguro de que tiene instaladas las cabeceras del kernel (paquete
kernel-headers)

2.- Compilar el módulo
    > make all
    
Nota: Las siguientes acciones se deben realizar como root
    
3.- Instalar el módulo
    > make modules_install
    > depmod -a

Nota: Como el proyector Acer C120 provee de una interface de almacenamiento
masivo USB, puede ser reconocida como una memoria USB.

Para prevenir esta acción y forzar al proyector ser reconocido como tal es
necesario hacer lo siguiente:

4.- En el directorio /etc/modprobe.d/ crear un archivo gm12u320 con la
siguiente linea:

install usb-storage /sbin/modprobe --ignore-install gm12u320 && /sbin/modprobe --ignore-install usb-storage


5. Ahora necesitamos modificar la imagen de initramfs image de la misma 
manera. Agregue la siguiente linea al archivo /etc/initramfs-tools/modules:
gm12u320

6. Ahora a volver a construir el initramfs:
    # update-initramfs -u


 ```
