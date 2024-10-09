# install git

* instalacion

```bash
sudo apt-get update
sudo apt-get install git
```

* creamos usuario y mail

```bash
git config --global user.name "Tu Nombre" 
git config --global user.email "tu@email.com"
```

* Verificamos mail y user de git:

```bash
guille@pescado  ~/repos_git  git config user.name
  guille
```

```bash
guille@pescado  ~/repos_git  git config user.email
  guillermoneculqueo@gmail.com
```

# clave SSh

***
📝 Nota:
al generar una clave ssh nos pedira si queremos ingresar un frase, para mayor seguridad. Esta  "frase de contraseña" es opcional, si no se desea, simplemente se puede presionar "Enter" para dejarla vacía.
***

* Generamos una nueva clave

```bash
 guille@pescado  ~  ssh-keygen -t rsa -b 4096 -C "guillermoneculqueo@gmail.com"
Generating public/private rsa key pair.
...
```

* Verificamos:

```bash
guille@pescado  ~  cat ~/.ssh/id_rsa.pub 
ssh-rsa AAA...
...
== guillermoneculqueo@gmail.com
```

* ssh en github
  * nos dirigimos a nuestro usuario en github: <https://github.com/guillenec>
  * click en el "avatar" -> settings -> SSH and GPG keys
  * hacemos click en el boton New SSH key
  * pegamos la clave creada , ponemos un nombre significativo y guardamos
  * una vez guardemos nos pedira confirmar, pidienndonos nuestro password de github, lo colocamos y confirmamos.

* clonamos un repo por primera vez:

```bash
 guille@pescado  ~/repos_git/noCountry  git clone git@github.com:No-Country/s10-19-n-csharp-react.git
  Clonando en 's10-19-n-csharp-react'...
  The authenticity of host 'github.com (20.201.28.151)' can't be established.
  ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
  This key is not known by any other names
  Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
  Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
  remote: Enumerating objects: 26, done.
  remote: Counting objects: 100% (26/26), done.
  remote: Compressing objects: 100% (21/21), done.
  remote: Total 26 (delta 0), reused 26 (delta 0), pack-reused 0
  Recibiendo objetos: 100% (26/26), 44.32 KiB | 796.00 KiB/s, listo.
```

***
📝 Nota:
cuando nos pregunte si deseas continuar conectando, colocamos si, nos aparecera una ventana emergente, la cual capturara el escritorio, colocamos la frase creada anteriormente a la hora de generar la SSH Key, y ya se deberia haber clonado el repo.
esto es normal la primera vez que te conectas a un servidor SSH desconocido y está relacionado con la seguridad.
***

* Verifico:

```bash
 guille@pescado  ~/repos_git/noCountry  ls s10-19-n-csharp-react 
  backend  frontend
```

# generar token gitHub

* Nos dirigimos a nuestro perfil de github:
  <https://github.com/settings/profile>
* click en el "avatar" -> settings -> < > Developer settings -> Personal access tokens -> tokens (classic)
* luego click en Generate a personal acces token:
   Allí, genera un nuevo token con los permisos necesarios (probablemente solo necesites los permisos de lectura y escritura para repositorios). Guarda este token en un lugar seguro.
* Utilizar el token en lugar de la contraseña:

```bash
git clone https://github.com/No-Country/s10-19-n-csharp-react.git
Username for 'https://github.com': guillenec
Password for 'https://guillenec@github.com': <tu-token-de-acceso-personal>
```

* Configurar el token como credencial:

***
📝 Nota :
esta accion se realiza si o si despues de haber usado un token en alguna operacion(clone, push, etc), como por ejemplo en el ejemplo anterior, al clonar un repositorio
***

Si no deseas ingresar el token cada vez que realizas una operación de git, puedes configurarlo como una credencial utilizando el comando git config:

```bash
git config --global credential.helper store
```

Esto almacenará el token en el almacenamiento de credenciales de Git después de que lo ingreses manualmente en una operación de autenticación. La próxima vez que realices una operación que requiera autenticación, Git usará automáticamente la información almacenada en lugar de pedirte que ingreses el nombre de usuario y el token nuevamente.
