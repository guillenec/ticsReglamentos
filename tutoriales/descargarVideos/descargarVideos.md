
# Guía para Descargar Videos y Audios de YouTube con `yt-dlp` 🎥🎵

## Instalación de `yt-dlp` 🚀

### En Debian (Linux Huayra) 🐧

1. **Actualizar el sistema:**
   Abre una terminal y ejecuta:

   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Instalar `yt-dlp` usando pip:**
   Primero, asegúrate de tener Python y pip instalados:

   ```bash
   sudo apt install python3 python3-pip -y
   ```

   Luego, instala `yt-dlp`:

   ```bash
   pip3 install yt-dlp
   ```

3. **(Opcional) Instalar binario independiente de `yt-dlp`:**

   ```bash
   sudo curl -L https://yt-dlp.org/downloads/latest/yt-dlp -o /usr/local/bin/yt-dlp
   sudo chmod a+rx /usr/local/bin/yt-dlp
   ```

### En Arch Linux 🐧

1. **Actualizar el sistema:**
   Abre una terminal y ejecuta:

   ```bash
   sudo pacman -Syu
   ```

2. **Instalar `yt-dlp`:**

   ```bash
   sudo pacman -S yt-dlp
   ```

## Uso de `yt-dlp` para Descargar Video y Audio 🎬🎧

### Descargar Audio en MP3 🎵

Para descargar solo el audio de un video de YouTube y convertirlo a MP3, usa el siguiente comando:

```bash
yt-dlp -x --audio-format mp3 "URL_DEL_VIDEO"
```

Ejemplo para el Himno Nacional Argentino:

```bash
yt-dlp -x --audio-format mp3 "https://www.youtube.com/watch?v=OqSQo2aifAA"
```

### Descargar Video 📹

Para descargar el video completo de YouTube, usa el siguiente comando:

```bash
yt-dlp "URL_DEL_VIDEO"
```

Ejemplo para el Himno Nacional Argentino:

```bash
yt-dlp "https://www.youtube.com/watch?v=OqSQo2aifAA"
```

### Guardar en una Carpeta Específica 📁

Para guardar el archivo en una carpeta específica, usa la opción `-o`:

```bash
yt-dlp -x --audio-format mp3 -o "~/Descargas/%(title)s.%(ext)s" "URL_DEL_VIDEO"
```

## Ejemplos Completos 📝

### Descargar Audio del Himno Nacional Argentino

```bash
yt-dlp -x --audio-format mp3 "https://www.youtube.com/watch?v=OqSQo2aifAA"
```

### Descargar Audio del Himno de Río

```bash
yt-dlp -x --audio-format mp3 "https://www.youtube.com/watch?v=b-7BfFd9ZAw"
```

### Descargar Audio de "A Mi Bandera"

```bash
yt-dlp -x --audio-format mp3 "https://www.youtube.com/watch?v=9S4wZqhKMHk"
```

## Notas Adicionales 📌

- Asegúrate de tener instaladas las dependencias necesarias para la conversión de audio (como `ffmpeg`). Puedes instalarlas con:
  - debian

    ```bash
    sudo apt install ffmpeg
    ```

  - Arch Linux

    ```bash
    sudo pacman -S ffmpeg
    ```

## 🎬🎧 Guia en video

[Guia en video - descargar audio y video](https://youtu.be/LEDmKFR7baM)
