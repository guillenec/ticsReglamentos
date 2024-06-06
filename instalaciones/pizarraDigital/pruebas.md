Pizarra Digital Ebeam Edge

Estos paquetes son un "reempaquetado" del original de Luidia que están hechos para versiones de Ubuntu. Contienen los drivers para que el lápiz funcione como puntero de mouse. Y la aplicación para dibujar sobre el escritorio. Están desarrollados para que funcionen sobre Huayra

Lamentablemente es todos software privativo y de 32bits.

El paquete pretende ser multiarch, para instalarlo en sistemas de 64bits se tiene que agregar la arquitectura de i386

$ dpkg --add-architecture i386

luego:

$ sudo apt-get install ebeam-diva ebeam-interact

El paquete está en estapa de desarrollo y todavía no esta completo el 100% de funcionalidad.     me ayudas a instalarlo en     administrador@conectarigualdad  ~  neofetch
                     `                   administrador@conectarigualdad
            .       .       `            ------------------------------
       ``    -      .      .             OS: Huayra 5.0 x86_64
        `.`   -` `. -  `` .`             Host: SF20GM7
          ..`-`-` + -  / .`     ```      Kernel: 4.19.0-26-amd64
          .--.+--`+:- :/.`.-``.`        Uptime: 2 hours, 49 mins
            -+/so::h:.d-`./:`.`          Packages: 2891 (dpkg), 2 (snap)
              :hNhyMomy:os-...-.  ````   Shell: zsh 5.7.1
               .dhsshNmNhoo+:-``.```     Resolution: 1366x768
                `ohy:-NMds+::-.``        DE: MATE
            ````.hNN+`mMNho/:-....````   WM: Metacity (Marco)
       `````     `../dmNhoo+/:..``       WM Theme: Huayra-JM
    ````            .dh++o/:....`        Theme: Huayra-JM [GTK2/3]
.+s/`                `/s-.-.:.`` ````    Icons: huayra-jm [GTK2/3]
::``::`..`           Terminal: mate-terminal
                          .``..         Terminal Font: JetBrainsMonoNL Nerd Fo
                                ``       CPU: Intel Celeron N4020 (2) @ 2.800GH
                                         GPU: Intel Device 3185
                                         Memory: 5189MiB / 7802MiB

READMEsource.md: *No hay* código fuente de ésta aplicación.

El paquete está armado con los archivo del original eBeamInteractiveSuite_3.2.2.2_Ubuntu12_32bit.tgz que
se descarga del sitio de Luidia.com.

Ese archivo comprimido trae un autoextraible que se llama *scrapbook-selfextracting.
A su vez, dentro de este hay embebido un instalador y el paquete .deb (ebeam-interact-1.0.deb)
Que contiene realmente los archivos ue valen la pena.

Como está empaquetado y pensado a una versión específica de ubuntu, tuvimos que desarmarlo (con dpkg-deb -x)
y volverlo a empaquetar de tal forma que funcione sobre Debian (en principio fue jessie y ahora stretch [Huayra4])

Se quitaron todos los archivos libQt* que están en la raiz de las aplicaciones para que se usen directamente
los de la distro, porque esos estaban enlazados con librerías que ya no existen.

 /opt/interact/bin
 /opt/interact/eBeamToolPallete
 /opt/diva

De esta forma, logramos ejecutar ScrapBook, la Paleta y la utilidad de calibración.

Si conocés a alguien que esté trabajando sobre código libre para ésta herramienta, avisanos!    README.md: # Pizarra Digital Ebeam Edge

Estos paquetes son un "reempaquetado" del original de Luidia que están hechos para versiones de Ubuntu.
Contienen los drivers para que el lápiz funcione como puntero de mouse. Y la aplicación para dibujar
sobre el escritorio. Están desarrollados para que funcionen sobre Huayra

Lamentablemente es todos software privativo y de 32bits.

El paquete pretende ser multiarch, para instalarlo en sistemas de 64bits se tiene que agregar la arquitectura de i386

$ dpkg --add-architecture i386

luego:

$ sudo apt-get install ebeam-diva ebeam-interact

El paquete está en estapa de desarrollo y todavía no esta completo el 100% de funcionalidad.

este ees el link del repo <https://github.com/HuayraLinux/pkg-ebeam/tree/master>
ChatGPT

Para instalar los paquetes de eBeam Edge en tu sistema Huayra 5.0 de 64 bits, sigue estos pasos detallados:

    Agrega la arquitectura i386 a tu sistema: Esto es necesario porque los paquetes son de 32 bits y necesitas permitir que tu sistema instale paquetes de esta arquitectura.

    bash

sudo dpkg --add-architecture i386

Actualiza la lista de paquetes: Después de agregar la arquitectura i386, debes actualizar tu lista de paquetes para que tu sistema reconozca los nuevos paquetes disponibles.

bash

sudo apt-get update

Instala los paquetes necesarios: Ahora puedes instalar los paquetes ebeam-diva y ebeam-interact.

bash

    sudo apt-get install ebeam-diva ebeam-interact

Aquí hay una guía paso a paso que incluye verificar posibles dependencias y problemas:
Paso 1: Agregar la arquitectura i386

bash

sudo dpkg --add-architecture i386

Paso 2: Actualizar los repositorios

bash

sudo apt-get update

Paso 3: Instalar los paquetes eBeam

bash

sudo apt-get install ebeam-diva ebeam-interact

Nota

Durante la instalación, pueden surgir algunos problemas de dependencias debido a la naturaleza de los paquetes de 32 bits en un sistema de 64 bits. Si te encuentras con problemas de dependencias, intenta resolverlos instalando manualmente las bibliotecas faltantes.
Solución de problemas

    Verificar dependencias:
    Si la instalación de ebeam-diva y ebeam-interact falla debido a dependencias, puedes intentar instalar las bibliotecas manualmente. Utiliza apt-cache search para encontrar las versiones correctas de las bibliotecas necesarias:

    bash

sudo apt-cache search <nombre-dependencia>

Instalar dependencias manualmente:
Por ejemplo, si necesitas instalar libqt4-core:i386, puedes hacerlo con:

bash

    sudo apt-get install libqt4-core:i386

Confirmar la instalación

Después de la instalación, verifica que los archivos se han colocado correctamente en sus respectivos directorios:

    /opt/interact/bin
    /opt/interact/eBeamToolPallete
    /opt/diva

Ejecutar las aplicaciones

Para asegurarte de que todo esté funcionando correctamente, ejecuta las aplicaciones proporcionadas por eBeam, como ScrapBook, la Paleta y la utilidad de calibración desde sus ubicaciones en /opt.
Enlaces adicionales

Para más detalles sobre el repositorio y posibles actualizaciones, puedes consultar el repositorio en GitHub que mencionaste:
Repositorio eBeam en GitHub
Consideraciones finales

Este software está en desarrollo y puede que no ofrezca el 100% de funcionalidad esperada. Mantente al tanto de las actualizaciones y colabora con los desarrolladores si encuentras errores o tienes sugerencias para mejorar la compatibilidad.

Si necesitas más ayuda o te encuentras con algún problema específico durante la instalación, no dudes en preguntar.
 administrador@conectarigualdad  ~  sudo apt-get update

[sudo] password for administrador:
Sorry, try again.
[sudo] password for administrador:
Obj:1 <http://repo.huayra.educar.gob.ar/huayra> austral InRelease
Obj:2 <http://repo.huayra.educar.gob.ar/huayra> austral-updates InRelease
Obj:3 <https://dl.google.com/linux/chrome/deb> stable InRelease
Obj:4 <http://security.debian.org/debian-security> buster/updates InRelease
Obj:5 <http://deb.debian.org/debian> buster InRelease
Obj:6 <http://repo.mysql.com/apt/debian> bookworm InRelease
Obj:7 <http://deb.debian.org/debian> buster-updates InRelease
Des:8 <https://packages.microsoft.com/repos/edge> stable InRelease [3.590 B]
Obj:9 <http://ppa.launchpad.net/phpmyadmin/ppa/ubuntu> focal InRelease
Descargados 3.590 B en 2s (1.755 B/s)
Leyendo lista de paquetes... Hecho
 administrador@conectarigualdad  ~  sudo apt-get install ebeam-diva ebeam-interac
 ✘ administrador@conectarigualdad  ~  sudo dpkg --add-architecture i386

 administrador@conectarigualdad  ~  sudo apt-get update

Obj:1 <http://repo.huayra.educar.gob.ar/huayra> austral InRelease
Obj:2 <http://repo.huayra.educar.gob.ar/huayra> austral-updates InRelease
Obj:3 <http://security.debian.org/debian-security> buster/updates InRelease
Obj:4 <http://deb.debian.org/debian> buster InRelease
Obj:5 <http://repo.mysql.com/apt/debian> bookworm InRelease
Obj:6 <http://deb.debian.org/debian> buster-updates InRelease
Obj:7 <https://dl.google.com/linux/chrome/deb> stable InRelease
Obj:8 <http://ppa.launchpad.net/phpmyadmin/ppa/ubuntu> focal InRelease
Des:9 <https://packages.microsoft.com/repos/edge> stable InRelease [3.590 B]
Descargados 3.590 B en 2s (2.100 B/s)
Leyendo lista de paquetes... Hecho
 administrador@conectarigualdad  ~  sudo apt-get update

Obj:1 <http://repo.huayra.educar.gob.ar/huayra> austral InRelease
Obj:2 <http://deb.debian.org/debian> buster InRelease
Obj:3 <http://security.debian.org/debian-security> buster/updates InRelease
Obj:4 <http://repo.mysql.com/apt/debian> bookworm InRelease
Obj:5 <http://repo.huayra.educar.gob.ar/huayra> austral-updates InRelease
Obj:6 <http://deb.debian.org/debian> buster-updates InRelease
Obj:7 <https://dl.google.com/linux/chrome/deb> stable InRelease
Obj:8 <http://ppa.launchpad.net/phpmyadmin/ppa/ubuntu> focal InRelease
Des:9 <https://packages.microsoft.com/repos/edge> stable InRelease [3.590 B]
Descargados 3.590 B en 2s (2.136 B/s)
Leyendo lista de paquetes... Hecho
 administrador@conectarigualdad  ~  sudo apt-get install ebeam-diva ebeam-interact

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete ebeam-diva
E: No se ha podido localizar el paquete ebeam-interact
 ✘ administrador@conectarigualdad  ~  sudo apt-get install ebeam-diva ebeam-interact

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete ebeam-diva
E: No se ha podido localizar el paquete ebeam-interact
 ✘ administrador@conectarigualdad  ~  sudo apt-cache search ebeam-diva
 administrador@conectarigualdad  ~  sudo apt-cache search ebeam
 administrador@conectarigualdad  ~  sudo apt-cache search diva
octave-divand - n-dimensional interpolation for Octave
ruby-diva - Implementation of expression for handling things for mikutter
isdnactivecards - ISDN utilities - active ISDN card support
 administrador@conectarigualdad  ~  sudo apt-cache search ebeam-interact
 administrador@conectarigualdad  ~ 
ChatGPT

Parece que los paquetes ebeam-diva y ebeam-interact no están disponibles en los repositorios configurados en tu sistema. Para instalarlos, puedes descargarlos y configurarlos manualmente desde el repositorio de GitHub mencionado.
Pasos para descargar e instalar manualmente los paquetes

    Clonar el repositorio de GitHub:

    bash

git clone <https://github.com/HuayraLinux/pkg-ebeam.git>

Cambiar al directorio del repositorio clonado:

bash

cd pkg-ebeam

Construir e instalar los paquetes:
Primero, asegúrate de que tienes dpkg-dev instalado para poder construir los paquetes:

bash

sudo apt-get install dpkg-dev

Construir los paquetes:

bash

dpkg-buildpackage -us -uc

Este comando construirá los paquetes y creará los archivos .deb necesarios.

Instalar los paquetes construidos:
Una vez construidos, puedes instalar los paquetes .deb generados en el directorio padre del repositorio clonado:

bash

cd ..
sudo dpkg -i ebeam-diva_*.deb
sudo dpkg -i ebeam-interact_*.deb

Resolver dependencias:
Si hay dependencias faltantes, puedes resolverlas con:

bash

    sudo apt-get install -f

Alternativa: Descargar e instalar directamente los archivos .deb

Si prefieres no construir los paquetes desde el código fuente, puedes intentar buscar directamente los archivos .deb en el repositorio de GitHub o en otro lugar confiable.

    Buscar los archivos .deb en el repositorio de GitHub:
        Visita este enlace y navega para encontrar los archivos .deb.
        Descarga los archivos .deb correspondientes a ebeam-diva y ebeam-interact.

    Instalar los archivos .deb descargados:
    Navega al directorio donde descargaste los archivos .deb y ejecuta:

    bash

sudo dpkg -i ebeam-diva_*.deb
sudo dpkg -i ebeam-interact_*.deb

Resolver dependencias:
Si hay dependencias faltantes, puedes resolverlas con:

bash

    sudo apt-get install -f

Confirmar la instalación

Después de seguir cualquiera de estos métodos, asegúrate de que los programas se han instalado correctamente verificando las ubicaciones de los archivos y ejecutando las aplicaciones.

Si tienes más problemas o necesitas más ayuda con algún paso específico, no dudes en preguntar.
 administrador@conectarigualdad  ~  git clone git@github.com:HuayraLinux/pkg-ebeam.git
Clonando en 'pkg-ebeam'...
remote: Enumerating objects: 4658, done.
remote: Total 4658 (delta 0), reused 0 (delta 0), pack-reused 4658
Recibiendo objetos: 100% (4658/4658), 147.94 MiB | 270.00 KiB/s, listo.
Resolviendo deltas: 100% (387/387), listo.
Revisando archivos: 100% (5831/5831), listo.
 administrador@conectarigualdad  ~  ls
 ADUARDA.pdf              git_guille                 notas.md
'Biblioteca de calibre'   gm12u320                   pkg-ebeam
 BRF                      guia2.kadenlive.md         Plantillas
'Calibre Library'         GUia.md                    posibleDB.md
 composer.json            Imágenes                   scriptsGuille
 composer.lock            kadenliveInstalacion.txt  'Sin título 1.odt'
 db_admin                 lmms                       vendor
 Descargas                miPendrive                 Videos
 Documentos               miUsb
 Escritorio               Música
 administrador@conectarigualdad  ~  cd pkg-ebeam
 administrador@conectarigualdad  ~/pkg-ebeam   master  ls
debian  etc  opt
 administrador@conectarigualdad  ~/pkg-ebeam   master  sudo apt-get install dpkg-dev

[sudo] password for administrador:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
dpkg-dev ya está en su versión más reciente (1.19.8).
fijado dpkg-dev como instalado manualmente.
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 106 no actualizados.
 administrador@conectarigualdad  ~/pkg-ebeam   master  dpkg-buildpackage -us -uc

dpkg-buildpackage: información: paquete fuente ebeam-tools
dpkg-buildpackage: información: versión de las fuentes 3.2.2.2huayra4
dpkg-buildpackage: información: distribución de las fuentes unstable
dpkg-buildpackage: información: fuentes modificadas por Fernando Toledo <ragnarok@docksud.com.ar>
dpkg-buildpackage: información: arquitectura del sistema amd64
 dpkg-source --before-build .
 fakeroot debian/rules clean
dh clean
   dh_clean
 dpkg-source -b .
dpkg-source: información: usando el formato de fuente «3.0 (native)»
dpkg-source: información: construyendo ebeam-tools en ebeam-tools_3.2.2.2huayra4.tar.xz
dpkg-source: información: construyendo ebeam-tools en ebeam-tools_3.2.2.2huayra4.dsc
 debian/rules build
dh build
   dh_update_autotools_config
 fakeroot debian/rules binary
dh binary
   dh_testroot
   dh_prep
   dh_install
   dh_installdocs
   dh_installchangelogs
   dh_perl
   dh_link
   dh_strip_nondeterminism
strip-nondeterminism: debian/ebeam-interact/opt/interact/bin/aspose.metafiles-1.8.0.jar: ignoring signed JAR file
 Normalized debian/ebeam-interact/opt/interact/bin/aspose.metafiles-1.8.0.jar
strip-nondeterminism: debian/ebeam-interact/opt/interact/bin/Aspose.Words.jdk16.jar: ignoring signed JAR file
 Normalized debian/ebeam-interact/opt/interact/bin/Aspose.Words.jdk16.jar
strip-nondeterminism: debian/ebeam-interact/opt/interact/bin/aspose.slides-8.0.0.jar: ignoring signed JAR file
 Normalized debian/ebeam-interact/opt/interact/bin/aspose.slides-8.0.0.jar
strip-nondeterminism: debian/ebeam-interact/opt/interact/bin/aspose-cells-7.6.1.jar: ignoring signed JAR file
 Normalized debian/ebeam-interact/opt/interact/bin/aspose-cells-7.6.1.jar
   dh_compress
   dh_fixperms
   dh_missing
   dh_strip
   dh_makeshlibs
   debian/rules override_dh_shlibdeps
make[1]: se entra en el directorio '/home/administrador/pkg-ebeam'

# LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu/libfakeroot:/usr/lib64/libfakeroot:/usr/lib32/libfakeroot:opt/diva:opt/interact/bin dh_shlibdeps --dpkg-shlibdeps-params=--ignore-missing-info

echo "override"
override
make[1]: se sale del directorio '/home/administrador/pkg-ebeam'
   dh_installdeb
   dh_gencontrol
   dh_md5sums
   dh_builddeb
dpkg-deb: construyendo el paquete `ebeam-diva' en`../ebeam-diva_3.2.2.2huayra4_amd64.deb'.
dpkg-deb: construyendo el paquete `ebeam-interact' en`../ebeam-interact_3.2.2.2huayra4_amd64.deb'.
dpkg-deb: construyendo el paquete `ebeam-diva-dbgsym' en`../ebeam-diva-dbgsym_3.2.2.2huayra4_amd64.deb'.
dpkg-deb: construyendo el paquete `ebeam-interact-dbgsym' en`../ebeam-interact-dbgsym_3.2.2.2huayra4_amd64.deb'.
 dpkg-genbuildinfo
Can't stat /usr/local/sbin: No such file or directory
 at /usr/share/perl5/Dpkg/Vendor/Debian.pm line 469.
 dpkg-genchanges  >../ebeam-tools_3.2.2.2huayra4_amd64.changes
dpkg-genchanges: información: incluyendo el código fuente completo en la subida
 dpkg-source --after-build .
dpkg-buildpackage: información: subida completa; paquete nativo de Debian (se incluye la fuente completa)
 administrador@conectarigualdad  ~/pkg-ebeam   master  ls
debian  etc  opt
 administrador@conectarigualdad  ~/pkg-ebeam   master  cd ..
 administrador@conectarigualdad  ~  ls
 ADUARDA.pdf                                      git_guille
'Biblioteca de calibre'                           gm12u320
 BRF                                              guia2.kadenlive.md
'Calibre Library'                                 GUia.md
 composer.json                                    Imágenes
 composer.lock                                    kadenliveInstalacion.txt
 db_admin                                         lmms
 Descargas                                        miPendrive
 Documentos                                       miUsb
 ebeam-diva_3.2.2.2huayra4_amd64.deb              Música
 ebeam-diva-dbgsym_3.2.2.2huayra4_amd64.deb       notas.md
 ebeam-interact_3.2.2.2huayra4_amd64.deb          pkg-ebeam
 ebeam-interact-dbgsym_3.2.2.2huayra4_amd64.deb   Plantillas
 ebeam-tools_3.2.2.2huayra4_amd64.buildinfo       posibleDB.md
 ebeam-tools_3.2.2.2huayra4_amd64.changes         scriptsGuille
 ebeam-tools_3.2.2.2huayra4.dsc                  'Sin título 1.odt'
 ebeam-tools_3.2.2.2huayra4.tar.xz                vendor
 Escritorio                                       Videos
 administrador@conectarigualdad  ~ 
ChatGPT

Perfecto, ya has construido los paquetes. Ahora solo necesitas instalarlos en tu sistema. Vamos a proceder con la instalación de los archivos .deb que has generado.
Instalación de los paquetes construidos

    Instalar los paquetes ebeam-diva y ebeam-interact:

    bash

sudo dpkg -i ebeam-diva_3.2.2.2huayra4_amd64.deb
sudo dpkg -i ebeam-interact_3.2.2.2huayra4_amd64.deb

Resolver posibles dependencias:
Si hay problemas de dependencias, puedes resolverlos con:

bash

    sudo apt-get install -f

Esto instalará los paquetes y resolverá cualquier dependencia faltante automáticamente.
Confirmar la instalación

Para asegurarte de que la instalación se haya realizado correctamente, verifica que los archivos se hayan colocado en las ubicaciones correctas y prueba ejecutar las aplicaciones.
Ubicación de los archivos y ejecución de las aplicaciones

Los archivos deberían estar en las siguientes ubicaciones:

    /opt/interact/bin
    /opt/interact/eBeamToolPallete
    /opt/diva

Puedes probar ejecutar las aplicaciones desde estas ubicaciones para asegurarte de que todo funciona correctamente.
Verificar la funcionalidad

    Ejecutar ScrapBook:

    bash

/opt/interact/bin/ScrapBook

Ejecutar la Paleta:

bash

/opt/interact/bin/eBeamToolPallete

Ejecutar la utilidad de calibración:

bash

    /opt/diva/calibration

Si encuentras algún problema durante la ejecución de estas aplicaciones, revisa los mensajes de error para diagnosticar y solucionar posibles problemas.

Si necesitas más ayuda o te encuentras con algún problema específico durante la instalación o ejecución, no dudes en preguntar.
