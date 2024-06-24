
# 📲 Instalación y Uso de `scrcpy` en Archcraft

## Introducción

`scrcpy` es una herramienta gratuita y de código abierto que te permite reflejar y controlar un dispositivo Android desde tu PC. Es especialmente útil para crear tutoriales, demostraciones y más.

## Características

- 🎥 **Reflejo de Pantalla**: Visualiza y controla tu dispositivo Android en tu PC.
- ⚡ **Baja Latencia**: Experiencia de uso casi en tiempo real.
- 🔄 **Control Completo**: Usa el teclado y el ratón para interactuar con tu dispositivo.

## Requisitos Previos

- 📱 Un dispositivo Android con **Depuración USB** habilitada.
- 🖥️ Un PC con Archcraft (o cualquier distribución basada en Arch Linux).

## Pasos de Instalación

### Opción 1: Usando `pacman`

#### 1. Actualiza tu Sistema

Primero, asegúrate de que tu sistema está completamente actualizado:

```sh
sudo pacman -Syu
```

#### 2. Instala `scrcpy`

Instala `scrcpy` utilizando el gestor de paquetes `pacman`:

```sh
sudo pacman -S scrcpy
```

#### 3. Verifica la Instalación

Asegúrate de que `scrcpy` se ha instalado correctamente verificando su versión:

```sh
scrcpy --version
```

Deberías ver algo como:

```sh
scrcpy 1.17
```

### Opción 2: Usando `yay`

#### 1. Instala `yay` (si no lo tienes instalado)

Si no tienes `yay` instalado, puedes hacerlo ejecutando:

```sh
sudo pacman -S yay
```

#### 2. Actualiza tu Sistema

Primero, asegúrate de que tu sistema está completamente actualizado:

```sh
yay -Syu
```

#### 3. Instala `scrcpy`

Instala `scrcpy` utilizando `yay`:

```sh
yay -S scrcpy
```

#### 4. Verifica la Instalación

Asegúrate de que `scrcpy` se ha instalado correctamente verificando su versión:

```sh
scrcpy --version
```

Deberías ver algo como:

```sh
scrcpy 1.17
```

## Uso de `scrcpy`

### 1. Habilita la Depuración USB en tu Android

Para habilitar la depuración USB en tu dispositivo Android:

1. Ve a **Configuración > Acerca del teléfono**.
2. Toca varias veces en **Número de compilación** hasta que se activen las **Opciones de desarrollador**.
3. Ve a **Opciones de desarrollador** y activa **Depuración USB**.

### 2. Conecta tu Android al PC

Conecta tu dispositivo Android a tu PC usando un cable USB.

### 3. Ejecuta `scrcpy`

Abre una terminal en tu PC y ejecuta el siguiente comando:

```sh
scrcpy
```

Esto abrirá una ventana en tu PC mostrando la pantalla de tu Android, permitiéndote controlarlo con tu teclado y ratón.

## Conclusión

¡Y eso es todo! Ahora puedes usar `scrcpy` para reflejar y controlar tu dispositivo Android desde tu PC con Archcraft. Si tienes alguna pregunta o encuentras algún problema, no dudes en buscar ayuda en la [documentación oficial de `scrcpy`](https://github.com/Genymobile/scrcpy).

---

¡Espero que este documento te sea útil! Si necesitas más ayuda o información, estoy aquí para asistirte.
