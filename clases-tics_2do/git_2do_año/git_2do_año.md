
# **Guía para Instalar Git y Crear tu Primer Repositorio en GitHub** 🚀

## **Objetivo** 🎯

Aprender a instalar Git, crear una cuenta en GitHub, crear un repositorio, y trabajar con archivos Markdown para crear un perfil personalizado en GitHub.

---

## **Paso 1: Abrir la Terminal en Linux** 🖥️

1. Para empezar, necesitamos abrir la terminal. Presiona las teclas **Ctrl + T** al mismo tiempo para abrirla. 💻

2. Una vez abierta la terminal, verificaremos si Git ya está instalado en tu sistema con el siguiente comando:

   ```bash
   git --version
   ```

   Si Git está instalado, verás un mensaje que indica la versión de Git que tienes instalada. Por ejemplo:

   ```bash
   git version 2.25.1
   ```

---

## **Paso 2: Instalar Git (si no está instalado)** 🛠️

1. Si Git no está instalado o ves un mensaje de error, instálalo con el siguiente comando:

   ```bash
   sudo apt install git
   ```

   🔐 *Nota:* Es posible que te pida tu contraseña. Escríbela y presiona **Enter**.

2. Después de que termine la instalación, verifica nuevamente que Git esté instalado correctamente usando:

   ```bash
   git --version
   ```

---

## **Paso Opcional: Generar y Configurar una Clave SSH** 🔐

Antes de clonar tu repositorio, es una buena práctica configurar una clave SSH para que GitHub te permita conectarte de forma segura sin tener que ingresar tu usuario y contraseña cada vez que envíes cambios.

### **Generar una clave SSH**

1. Abre la terminal y genera una nueva clave SSH con el siguiente comando (reemplaza el correo por el tuyo):

   ```bash
   ssh-keygen -t rsa -b 4096 -C "tucorreo@example.com"
   ```

2. Verás una serie de preguntas. Puedes presionar **Enter** para aceptar las opciones predeterminadas. También te pedirá que ingreses una frase de contraseña opcional para mayor seguridad.

📝 **Nota:**
Al generar la clave SSH, te pedirá una frase de contraseña para mayor seguridad. Esta frase es opcional, y si no la deseas, simplemente presiona **Enter** para dejarla vacía.

3. El resultado será similar a este:

   ```bash
   Generating public/private rsa key pair.
   Enter file in which to save the key (/home/tuusuario/.ssh/id_rsa): 
   Enter passphrase (empty for no passphrase): 
   Enter same passphrase again: 
   Your identification has been saved in /home/tuusuario/.ssh/id_rsa
   Your public key has been saved in /home/tuusuario/.ssh/id_rsa.pub
   ```

### **Verificar la clave generada**

1. Para verificar que la clave se generó correctamente, ejecuta el siguiente comando:

   ```bash
   cat ~/.ssh/id_rsa.pub
   ```

2. Verás tu clave pública que comienza con `ssh-rsa` y termina con tu correo electrónico.

   ```bash
   ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA... == tucorreo@example.com
   ```

### **Añadir la clave SSH a GitHub**

1. Abre GitHub y ve a la configuración de tu cuenta:  
   **Avatar (esquina superior derecha) → Settings → SSH and GPG keys**.

2. Haz clic en el botón **New SSH key**.

3. Pon un título significativo para identificar la clave (por ejemplo, "Mi computadora") y pega la clave que copiaste en el paso anterior.

4. Guarda los cambios. GitHub te pedirá que ingreses tu contraseña para confirmar.

---

## **Paso 6: Clonar tu Repositorio Usando SSH** 🔗

1. Una vez configurada tu clave SSH, copia la URL SSH de tu repositorio en GitHub. Será algo como esto:

   ```bash
   git@github.com:tuusuario/mi-perfil.git
   ```

2. En la terminal, usa el siguiente comando para clonar el repositorio:

   ```bash
   git clone git@github.com:tuusuario/mi-perfil.git
   ```

3. Esto creará una carpeta en tu computadora llamada **mi-perfil**, que será una copia exacta de tu repositorio en GitHub. 🗂️

---

## **Paso 7: Crear y Personalizar tu README.md con Markdown** ✍️

1. Navega hasta la carpeta de tu repositorio:

   ```bash
   cd mi-perfil
   ```

2. Ahora, editemos el archivo **README.md** con Markdown para personalizar tu perfil.

3. Abre **README.md** con tu editor de texto preferido (puedes usar **nano** desde la terminal):

   ```bash
   nano README.md
   ```

4. Escribe un título y una breve descripción sobre ti en formato Markdown. Aquí tienes un ejemplo:

   ```markdown
   # ¡Hola! 👋 Soy [Tu Nombre]
   
   ¡Bienvenido a mi perfil de GitHub! Soy un entusiasta de la programación y aquí comparto mis proyectos. 🚀

   ## Tecnologías que manejo:
   - Python 🐍
   - HTML y CSS 🌐
   - Git y GitHub 💻

   ## Proyectos destacados:
   - [Mi primer proyecto](https://github.com/tuusuario/mi-proyecto)
   ```

5. Guarda el archivo presionando **Ctrl + O** y luego **Ctrl + X** para salir del editor. 💾

---

## **Paso 8: Agregar, Commitear y Pushear los Cambios a GitHub** ⬆️

1. Después de hacer los cambios en tu **README.md**, es hora de enviarlos a GitHub. Primero, debemos agregar los cambios:

   ```bash
   git add README.md
   ```

2. Luego, haz un **commit** con un mensaje que describa los cambios que hiciste:

   ```bash
   git commit -m "Añadí información sobre mí en el README"
   ```

3. Finalmente, sube tus cambios a GitHub (pushea los cambios):

   ```bash
   git push origin main
   ```

---

## **Paso 9: Verifica los Cambios en GitHub** 🔍

1. Vuelve a tu navegador y visita tu repositorio en GitHub.

2. Deberías ver el archivo **README.md** actualizado en la página principal de tu repositorio con la información que acabas de agregar. 👏

---

## **Paso 10: Próximos Pasos** 🚀

- **Explora más comandos de Git**: Ahora que tienes una base sólida, puedes explorar más comandos como `git pull`, `git branch`, y `git merge`.
  
- **Colaboración**: Aprende a trabajar con ramas y contribuye a proyectos colaborativos. 🤝

- **Sigue mejorando tu perfil de GitHub**: Puedes continuar editando tu archivo **README.md** para mostrar tus habilidades, proyectos y otros datos relevantes.

---

## **Resumen de Comandos Clave** 📝

- **Verificar versión de Git**:  

  ```bash
  git --version
  ```

- **Configurar Git**:  

  ```bash
  git config --global user.name "Tu Nombre"  
  git config --global user.email "tucorreo@example.com"
  ```

- **Clonar repositorio**:  

  ```bash
  git clone URL_DEL_REPOSITORIO
  ```

- **Agregar archivos al seguimiento de Git**:  

  ```bash
  git add ARCHIVO
  ```

- **Hacer un commit**:  

  ```bash
  git commit -m "Descripción del cambio"
  ```

- **Subir cambios a GitHub**:  

  ```bash
  git push origin main
  ```
