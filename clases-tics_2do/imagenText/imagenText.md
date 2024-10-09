
# imagen a texto

## instalamos el tesseract

```bash
sudo apt install tesseract-ocr
```

## uso

```bash
tesseract 1.png 1txt

# luego
cat 1txt.txt
Cual de los siguientes es un ambito valido de configuracién de GIT? Marque todas las que correspondan.
Hay 3 respuestas correctas

Global

User

Local

System

# Fin del procedimiento
```

## Ejersicio Practico

1) Compruebe si Tesseract OCR está instalado.
2) Instale Tesseract OCR y las dependencias necesarias si no están presentes.
3) Ofrezca un menú de uso para guiar al usuario.
4) Permita pasar una imagen como argumento para convertirla en texto.

## Creaccion de unscript para automatizar y explicar esto

```bash
#!/bin/bash

# Comprobar si Tesseract OCR está instalado
if ! command -v tesseract &> /dev/null
then
    echo "Tesseract no está instalado. Instalando..."
    sudo apt-get update
    sudo apt-get install -y tesseract-ocr
    echo "Tesseract instalado con éxito."
fi

# Comprobar si se proporcionó una imagen como argumento
if [ -z "$1" ]; then
    echo "No se proporcionó una imagen como argumento."
    echo "Por favor, introduce la ruta completa de la imagen:"
    read imagen
else
    imagen="$1"
fi

# Comprobar si el archivo de imagen existe
if [ ! -f "$imagen" ]; then
    echo "El archivo $imagen no existe."
    exit 1
fi

# Convertir la imagen a texto
echo "Procesando la imagen $imagen..."
tesseract "$imagen" stdout

# Opción para guardar la salida en un archivo
echo "¿Deseas guardar el texto en un archivo? (s/n)"
read respuesta

if [ "$respuesta" == "s" ]; then
    echo "Introduce el nombre del archivo (sin extensión):"
    read nombre_archivo
    tesseract "$imagen" "$nombre_archivo"
    echo "Texto guardado en $nombre_archivo.txt"
else
    echo "Texto no guardado."
fi
```

### ¿Cómo Funciona?

- **Verificación del Argumento**: El script primero verifica si se ha pasado un argumento (la ruta de la imagen). Si no se ha pasado, solicita al usuario que ingrese la ruta manualmente.
- **Entrada Interactiva**: Si no se pasa la imagen como argumento (caso común cuando se ejecuta desde un lanzador), el script solicita al usuario la ruta de la imagen durante la ejecución.

### Ejecución desde un Lanzador

Cuando se ejecuta desde un lanzador:

- Se abrirá una terminal pidiendo al usuario que introduzca la ruta de la imagen si no se pasó un argumento desde la terminal.
- Esto asegura que el script funcione bien tanto cuando se ejecuta directamente desde la terminal como cuando se ejecuta desde un lanzador gráfico.

### Actualización del Lanzador

El archivo `.desktop` puede seguir siendo el mismo:

```ini
[Desktop Entry]
Version=1.0
Name=Image to Text
Comment=Convertir imagen a texto usando Tesseract OCR
Exec=gnome-terminal -- ~/image_to_text.sh
Icon=/usr/share/icons/hicolor/48x48/apps/tesseract.png  # Cambia esta ruta si tienes un icono específico
Terminal=true
Type=Application
Categories=Utility;Application;
```

### Ejemplo de Uso

- **Desde la Terminal**: Puedes seguir pasando la ruta de la imagen como argumento:

  ```bash
  ~/image_to_text.sh /ruta/a/tu/imagen.png
  ```

- **Desde el Lanzador**: Se abrirá una terminal y el script te pedirá que ingreses la ruta de la imagen manualmente.

Este enfoque asegura que el script sea flexible y fácil de usar en ambos contextos, tanto en la terminal como desde un entorno gráfico.
