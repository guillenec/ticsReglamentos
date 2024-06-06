# Instalacion tienda snap + lanzador

## instalacion y configuracion

Para instalar Snap y la tienda de aplicaciones de Snap (Snap Store) en tu sistema Linux, sigue estos pasos. Snap es un sistema de empaquetado y despliegue de software desarrollado por Canonical, la empresa detrás de Ubuntu.

* Actualizar los repositorios:

  ```sh
  sudo apt update
  ```

* Instalar Snap:

  ```sh
  sudo apt install snapd
  ```

## Instalar Snap Store

Una vez que Snap está instalado, puedes instalar la Snap Store (tienda de aplicaciones de Snap) usando Snap:

  ```sh
  sudo snap install snap-store
  ```

## crear un lanzador

* Crear el archivo .desktop

  ```bash
  sudo nano /usr/share/applications/snap-store.desktop
  ```

* Agrega el siguiente contenido al archivo, usando snap run snap-store y especificando una ruta al icono si tienes una imagen personalizada:

  ```bash
      [Desktop Entry]
      Name=Snap Store
      Comment=Browse and install snaps
      Exec=snap run snap-store
      Icon=/path/to/your/icon.png
      Terminal=false
      Type=Application
      Categories=Utility;PackageManager;

      Cambia /path/to/your/icon.png por la ruta real de tu icono personalizado.
  ```

* Busca y descarga una imagen de icono que prefieras. luego buscamos:

```bash
  sudo find / -name snap-store.png
  Si encuentras el icono, toma nota de la ruta completa.
```

* Colocar el icono en una ubicación estándar

Coloca el icono en una ubicación estándar para iconos, como **/usr/share/pixmaps/ o ~/.local/share/icons/**.

* Ejemplo de copiar a /usr/share/pixmaps/:

```bash
  sudo cp /path/to/your/icon.png /usr/share/pixmaps/snap-store.png
```

* Actualizar el archivo .desktop con la ruta del icono

  Si colocaste el icono en /usr/share/pixmaps/, actualiza la línea del icono en el archivo .desktop:

  ```bash
  Icon=/usr/share/pixmaps/snap-store.png
  ```

* Guardar y cerrar el archivo
en vim **esc + : wq**

* Actualizar la base de datos de aplicaciones

  ```bash
  sudo update-desktop-database
  ```

* *Verificar la creación del lanzador

Busca "Snap Store" en el menú de aplicaciones de tu entorno de escritorio. Deberías ver el icono de Snap Store y poder lanzarlo desde allí.

Con estos pasos, deberías poder crear un lanzador para Snap Store que se ejecute correctamente y tenga un icono personalizado.
