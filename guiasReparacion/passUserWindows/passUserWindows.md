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

📓Nota **tarea inversa, para que al cliquiar en las utilidades no nos abra el cmd, remplazamos Utilman.exe por el backup que realizamos Utilman.exe.back y listo**
  
---

## Desde un usb Booteado con windows

### continuemos

Suponiendo que ya estás en la consola y has identificado la unidad donde está instalado Windows (generalmente C:), puedes seguir estos pasos:

1. **Cambiar al directorio `system32`:**

   ```cmd
   cd C:\Windows\System32
   ```

2. **Renombrar `magnify.exe` a `magnify2.exe`:**

   ```cmd
   ren magnify.exe magnify2.exe
   ```

3. **Copiar `cmd.exe` y renombrarlo como `magnify.exe`:**

   ```cmd
   copy cmd.exe magnify.exe
   ```

   Esto reemplazará el archivo de la lupa (`magnify.exe`) con una copia del símbolo del sistema (`cmd.exe`).

### Importante

Esta técnica se usa para abrir una consola con privilegios administrativos durante la pantalla de inicio de sesión de Windows, lo que te permitiría restablecer contraseñas u otras configuraciones de usuario.

Para utilizar el acceso al cmd renombrado como magnify, en la pantalla de inicio de sesión, puedes presionar la combinación de teclas **Win + U** para abrir la lupa. Como has renombrado `magnify.exe` a `cmd.exe`, en su lugar se abrirá una consola de comandos con permisos elevados.

### Restablecer la contraseña desde cmd

Una vez tengas la consola abierta desde la pantalla de inicio de sesión, puedes restablecer la contraseña del usuario:

1. **Listar todos los usuarios:**

   ```cmd
   net user
   ```

2. **Cambiar la contraseña de un usuario específico (por ejemplo, `Usuario`):**

    ```cmd
    net user
    net user Estudiante *
    nuevo Password ***
    Repetimos el password ***
    ```

3. **Cerrar la consola y tratar de iniciar sesión con la nueva contraseña.**

Finalmente, recuerda revertir los cambios:

1. Reinicia desde el pendrive de recuperación.
2. Cambia el nombre de `magnify2.exe` de nuevo a `magnify.exe` para restaurar la funcionalidad de la lupa:

   ```cmd
   ren magnify2.exe magnify.exe
   ```

Este proceso debería ayudarte a resolver el problema del usuario que olvidó su contraseña. Si tienes más preguntas o necesitas ayuda adicional, no dudes en preguntar.
