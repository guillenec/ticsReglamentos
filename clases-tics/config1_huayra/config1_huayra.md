# Procedimiento de configuracion de huayra linux

## veificar entorno de ventanas

```bash
echo $XDG_CURRENT_DESKTOP
```

## instalar fuentes

* copiamos la fuente al directorio de fuentes del sistema

 ```bash
 sudo cp /ruta/a/tus/fuentes/*.ttf /usr/share/fonts/
 ```

* Actualizamos la cache de fuentes:

 ```bash
 sudo fc-cache -fv
 ```

## Instalar y Aplicar Temas de Color

* Instalar herramientas necesarias:
 Asegúrate de tener instaladas las herramientas necesarias para administrar temas

 ```bash
 sudo apt-get install mate-themes mate-tweak
 ```

* Descargar y Copiar Temas compatibles (gtk3):
 Descarga temas compatibles con MATE desde sitios como Gnome-look.org.
 Copia el tema descargado al directorio de temas:

 ```bash
 sudo cp -r /ruta/a/tu/tema /usr/share/themes/
 ```

* Aplicar el Tema:
 Abre MATE Tweak desde el menú de aplicaciones o ejecuta:

 ```bash
 mate-tweak
 ```

 Nota: Ve a la sección Apariencia.
 Selecciona el tema que acabas de instalar en la sección de Tema.
 Cambiar el Tema de la Terminal
 Cambiar el tema de la terminal:
 Abre mate-terminal.
 Ve a Editar > Preferencias del perfil.
 Selecciona el perfil que estás usando (por defecto es Sin nombre).
 Ve a la pestaña Colores.
 Aquí puedes personalizar los colores de fondo, texto y otros elementos de la terminal.

## Resumen de Comandos

```bash
# Copiar fuentes al directorio de fuentes del sistema
sudo cp /ruta/a/tus/fuentes/*.ttf /usr/share/fonts/
sudo fc-cache -fv

# Instalar herramientas de administración de temas
sudo apt-get install mate-themes mate-tweak

# Copiar temas al directorio de temas del sistema
sudo cp -r /ruta/a/tu/tema /usr/share/themes/

# Abrir MATE Tweak para cambiar el tema
mate-tweak
```

## Links importantes

NOTA: [personaliza huayra linux](https://huayra.educar.gob.ar/primeros-pasos/)

## persoalizacion de escritorio

[gome looks](https://www.gnome-look.org/browse/)

## Vamos a configurar temas

* Descargamos compatible gtk3 desde gnome looks.

 ```bash
  administrador@conectarigualdad  ~/Descargas/temas/temas  ls
 Andromeda                             Nordic-darker-v40
 Dracula                               Nordic-Polar
 Dracula-pink-accent                   Nordic-Polar-standard-buttons
 Dracula-pink-accent-standard-buttons  Nordic-Polar-standard-buttons-v40
 Mojave-Dark                           Nordic-Polar-v40
 Nordic-darker

 administrador@conectarigualdad  ~/Descargas/temas/temas  sudo cp -r ./* ~/.themes 
 [sudo] password for administrador: 
 
  administrador@conectarigualdad  ~/Descargas/temas/temas  ls ~/.themes 
 Andromeda                             Nordic-darker-v40
 Dracula                               Nordic-Polar
 Dracula-pink-accent                   Nordic-Polar-standard-buttons
 Dracula-pink-accent-standard-buttons  Nordic-Polar-standard-buttons-v40
 Mojave-Dark                           Nordic-Polar-v40
 Nordic-darker
 
 ```

 **NOTA** en teoria esta carpeta es un link simbolico hacia /usr/share/hemes, tambien puedo copiarlos directamente aca .

  1. luego solo deberiamos abrir el menu de configuraciones:
  2. En huayra hacemos clic derecho sobre el escritorio seleccionamos cambiar fondo d eecritorio.
  3. vamos donde dice temas y ya comenzamos a modificar, cambiar el tema manualmente.. si hacemos clic en personalizar podremos cambiar el paquete de icono.

## cambiamos el entorno de ventanas

* para ello usaremos usaremos **tasksel**

## distros linux

* [distros linux](https://es.wikipedia.org/wiki/Anexo:Distribuciones_Linux)
* [distros hacking](https://blog.elhacker.net/2021/11/mejores-distribuciones-de-linux-para-hacking-etico-pentest.html)
  * [parrot os](https://parrotsec.org/)
  * [kali Linux](https://www.kali.org/)
  * [black arch](https://blackarch.org/)

## entornos de ventana linux

### mas comunes

* [entornos de ventana comunes](https://www.arsys.es/blog/entornos-escritorio-linux)
* [mas entornos](https://victorhckinthefreeworld.com/2020/02/28/38-gestores-de-ventanas-o-entornos-de-escritorio-para-linux/)

NOTA: las siguientes son paginas donde ver entornos:

* [unixporn](https://www.reddit.com/r/unixporn/)

*

## distros llamativas y comunes

* [debian](https://www.debian.org/index.es.html)
* [mint](https://linuxmint.com/)
* [steam](https://store.steampowered.com/steamos)
* [arch](https://archlinux.org/)
* [archcraft](https://archcraft.io/)

## Etornos personalizados por la comunidad

* [Zlcube kali bspwn](https://github.com/ZLCube/KaliBspwm)
* [dotfile](https://github.com/gh0stzk/dotfiles)
* [zprogrer bspwn](https://github.com/Zproger/bspwm-dotfiles)
