
# 📸 Instalación y Configuración de DroidCam en Archcraft

## Introducción

DroidCam es una aplicación que permite utilizar tu dispositivo Android como una cámara web para tu PC. Esta guía te ayudará a instalar DroidCam y configurar el modo HD en Archcraft, así como a solucionar problemas comunes.

## Instalación de DroidCam

### Usando `yay`

Para instalar DroidCam, usa el siguiente comando:

```sh
yay -S droidcam
```

### Error Común

Después de la instalación, podrías ver el siguiente error al intentar ejecutar DroidCam:

```bash
error: Droidcam/v42loopback device not found (/dev/video[0-9]).  Did it install correctly?  If you had a kernel update, you may need to re-install
```

## Solución de Problemas

### Verificar si el Módulo `v4l2loopback` está Cargado

Para verificar si el módulo `v4l2loopback` está cargado, ejecuta el siguiente comando:

```sh
lsmod | grep v4l2loopback
```

#### Si no Aparece Nada

Si el comando anterior no devuelve ningún resultado, significa que el módulo no está cargado.

### Cargar Manualmente el Módulo `v4l2loopback`

Puedes intentar cargar manualmente el módulo `v4l2loopback` con el siguiente comando:

```sh
sudo modprobe v4l2loopback_dc
```

### Verificar la Carga del Módulo

Después de cargar el módulo, verifica que se ha cargado correctamente:

```sh
ls /dev/video*
```

Deberías ver algo como `/dev/video0`.

También puedes verificar el estado del módulo con:

```sh
lsmod | grep v4l2loopback
```

Deberías ver una salida similar a:

```bash
v4l2loopback_dc        40960  0
videodev              393216  1 v4l2loopback_dc
```

### Ejemplo de Sesión de Comandos

```sh
# Verificar si el módulo está cargado
lsmod | grep v4l2loopback

# Si no aparece nada, cargar el módulo manualmente
sudo modprobe v4l2loopback_dc

# Verificar dispositivos de video
ls /dev/video*

# Verificar de nuevo si el módulo está cargado
lsmod | grep v4l2loopback
```

### Ejemplo de Salida Esperada

```sh
# Verificar dispositivos de video
/dev/video0

# Verificar el estado del módulo
v4l2loopback_dc        40960  0
videodev              393216  1 v4l2loopback_dc
```

## Instalación Manual de DroidCam (Si es Necesario)

### Descarga e Instalación del Cliente

```sh
cd /tmp/
wget -O droidcam_latest.zip https://files.dev47apps.net/linux/droidcam_2.1.3.zip
unzip droidcam_latest.zip -d droidcam
cd droidcam && sudo ./install-client
```

### Instalación del Módulo de Video

```sh
sudo ./install-video
```

Si tienes Secure Boot habilitado, el script de instalación intentará firmar los controladores automáticamente. Si la firma falla, tendrás que firmar el controlador manualmente siguiendo las instrucciones de tu distribución para la firma de módulos con Secure Boot.

### Verificar la Instalación del Módulo

```sh
lsmod | grep v4l2loopback
```

Deberías ver `v4l2loopback_dc` en la salida.

## Modo HD: Cambiar la Resolución de la Cámara Web

### Cerrar Programas y Descargar el Controlador

1. Cierra cualquier programa que esté usando la cámara web de DroidCam.
2. Descarga el controlador:

```sh
sudo rmmod v4l2loopback_dc
```

### Recargar el Controlador con Nuevas Opciones

Reemplaza `WIDTH` y `HEIGHT` con las dimensiones deseadas:

```sh
sudo insmod /lib/modules/$(uname -r)/kernel/drivers/media/video/v4l2loopback-dc.ko width=WIDTH height=HEIGHT
```

Ejemplos de tamaños estándar:

- 640×480
- 960×720
- 1280×720 (720p)
- 1920×1080 (1080p)

### Hacer Permanente el Cambio de Resolución

Edita el archivo `/etc/modprobe.d/droidcam.conf` con las nuevas opciones para que el cambio sea permanente.

## Instalación de DroidCam en el Teléfono

- Descargar la Aplicación
Abre Google Play Store en tu dispositivo Android.
Busca "DroidCam" y descarga la aplicación desarrollada por "Dev47Apps".
Habilitar Opciones de Desarrollador

## Para habilitar las opciones de desarrollador en tu teléfono Android, sigue estos pasos

- Ve a Ajustes.
- Selecciona Acerca del teléfono.
- Toca el campo Número de compilación 7 veces.
  Verás un mensaje indicando que estás a punto de habilitar las opciones de desarrollador. Sigue tocando hasta que recibas un mensaje notificando que ahora eres desarrollador. Si ya eres desarrollador, verás un mensaje que indica que ya eres desarrollador.
- Toca la flecha hacia atrás una vez hayas terminado y aparecerá Opciones de desarrollo en Ajustes.

## Especificar el Dispositivo Correcto en ADB

- Listar Dispositivos Conectados

```bash
adb devices
```

- Establecer el Dispositivo por Defecto

```bash
export ANDROID_SERIAL=ZE222NL677
```

### Ejecutar DroidCam con el Dispositivo Especificado

```bash
droidcam-cli adb 4747

```

### Ejecutar Scrcpy con el Dispositivo Específico

```bash
scrcpy -s ZE222NL677
```

### Ejemplo Completo

```bash
# Listar dispositivos conectados
adb devices

# Salida esperada:
# List of devices attached
# ZE222NL677 device
# ZY227KQKCD device

# Establecer el dispositivo por defecto
export ANDROID_SERIAL=ZE222NL677

# Ejecutar DroidCam
droidcam-cli adb 4747

# Ejecutar Scrcpy especificando el dispositivo
scrcpy -s ZE222NL677

```

## Conclusión

Siguiendo estos pasos, deberías poder instalar y configurar DroidCam en Archcraft, incluyendo la configuración del modo HD. Si continúas teniendo problemas, asegúrate de que todas las dependencias están instaladas y actualizadas.
