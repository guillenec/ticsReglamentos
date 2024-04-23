# Guia Cambio de Password Windows Desde Linux

## Montamos la partiion con windows  

vamos a huaira y montamos la particion donde esta instalado windows.. posiblemente necesitemos instalar el sys archivo NTFS:

```bash
sudo apt-get install ntfs-3g
mkdir ~/windows_mount
sudo mount -t ntfs-3g /dev/sdXn ~/windows_mount
```

## Remplazamos utilman x cmd

sobre escribimos el archivo de las utilidades que aaparece al inicio en windows antes de iniciar secion por el de cmd.exe, de esta maner al apretar en este boton se podra abrir la terminal de windows y cambiar el password a mano.

```bash
‌cd ~/rutaMountWindows/Windows/System32/
//backapiamos Utilman
cp Utilman.exe Utilman.exe.bak
//remplazamos luego por el cmd
cp cmd.exe Utilman.exe
systemctl reboot
```

## Listamos modificamos pass  

Se reiniciara la pc, y al hacer click en el boton de utilidades ya accederemos a la terminal, desde aca hacemos todo, se puede sacar todo. por lo que solo nos queda modificar el pass de el usuario que haya.. en el caso de esta pc el usuario es Estudiante:

```bash
net user
net user Estudiante *
nuevo Password ***
Repetimos el password ***
```

## tarea inversa, para que al cliquiar en las utilidades no nos abra el cmd, remplazamos Utilman.exe por el backup que realizamos Utilman.exe.back y listo
