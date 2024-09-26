
# Procedimiento de instalación y uso de `qrencode` para generar códigos QR en sistemas basados en Debian

## 1. Instalar `qrencode` en Linux (Huayra/Debian)

En distribuciones basadas en Debian como Huayra, utiliza el siguiente comando para instalar `qrencode`:

```bash
sudo apt update
sudo apt install qrencode
```

## 2. Verificar la instalación

Una vez instalada, verifica que `qrencode` está disponible ejecutando:

```bash
qrencode --version
```

Si se muestra la versión del programa, la instalación fue exitosa.

## 3. Generar un código QR básico

Para generar un código QR a partir de una URL o texto, usa el siguiente comando:

```bash
qrencode -o qr.png "https://www.ejemplo.com"
```

Este comando generará un archivo de imagen (`qr.png`) con el código QR de la URL proporcionada.

## 4. Especificar el tamaño del código QR

Puedes ajustar el tamaño de los bloques (módulos) del código QR usando el parámetro `-s` seguido del tamaño que desees. A mayor valor, más grandes serán los módulos:

```bash
qrencode -o qr.png -s 10 "https://www.ejemplo.com"
```

- `-o qr.png`: Especifica el archivo de salida (la imagen del código QR).
- `-s 10`: Define el tamaño de los módulos en píxeles (en este caso, 10x10 píxeles por módulo).

## 5. Mostrar el código QR en la terminal

Si no deseas crear un archivo de imagen y simplemente quieres ver el código QR en la terminal (usando caracteres ASCII), puedes hacerlo con:

```bash
qrencode -t ANSI "https://www.ejemplo.com"
```

## 6. Guardar el código QR en formato SVG o EPS

Puedes generar el código QR en formato vectorial como SVG o EPS. Por ejemplo, para generar un archivo SVG:

```bash
qrencode -o qr.svg -t SVG "https://www.ejemplo.com"
```

Para EPS:

```bash
qrencode -o qr.eps -t EPS "https://www.ejemplo.com"
```

## 7. Consideraciones para impresión

Para asegurar que el código QR sea escaneable al imprimir, sigue estas recomendaciones:

- Utiliza una resolución de **300 dpi** al generar el archivo para asegurar una buena calidad de impresión.
- Ajusta el tamaño de los módulos (con `-s`) según el tamaño físico que necesites para tu impresión.

## 8. Verificar la lectura del código QR

Antes de imprimir, prueba el código QR escaneándolo con un lector de QR en tu smartphone o una aplicación de escaneo para asegurarte de que se lea correctamente.
