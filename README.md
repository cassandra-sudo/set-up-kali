![](https://raw.githubusercontent.com/cassandra-sudo/set-up-kali/main/image/cover.png)

# 🥁 GETTING STARTED WITH THE BASICS.

### The Linux Filesytem

![](https://raw.githubusercontent.com/cassandra-sudo/set-up-kali/main/image/filesystem.png)

**User root, su, sudo**

🔥 <code>/</code> := <code>root</code> ('/' isn't command, is a location).
⭐ su := Switch User by deafaul root user => it asks you for the password.
🔴 sudo := SuperUser Do

**🗂️ How show list users**:
$ cat /etc/passwd
/*
output
root:x:0:0:root:/root:/bin/bash
gabriel:x:1000:1000:Gabriel,,,:/home/gabriel:/bin/bash
postgres:x:124:135:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
*/

😎 Campos importantes:

🚀 usuario:x:UID:GID:Nombre:/home/usuario:/bin/bash
    💡 UID: Identificador único de usuario.
        📌 0 = root
        📍 100+ = usuarios normales

**📜 Como ver y cambiar contraseñas**
📐 Ver estado de contraseñas:

Zsh
```
sudo passwd -S nombredeusuario
```

📐 Establecer una contraseña al usuario root.

Zsh
```
sudo passwd root
```

 📐 Cambiar tu propia contraseña:
 
Zsh
```
passwd
```

**🔒 Permisos en Debian**
Tipos de permisos:

Cada archivo o carpeta tiene 3 tipos de usuarios  y 3 tipos de permisos :

Tipo de usuario      Descripción
    u (user)             El dueño del archivo
    g (group)            Los usuarios del grupo
    o (others)           Todos los demás

Permisos             Acción
    r (read)         Leer contenido
    w (write)        Editar
    x (excecute)     Ejecutar como programa o entrar a carpeta
        
**👀 Show permissions**

Zsh
```
ls -al
```

Un posible output seria:

```
-rw-r--r-- 1 usuario usuario  4096 abr 5 10:00 archivo.txt
```

This mean:

⭐ -rw-r--r--: permisos
💫 usuario: dueño
💼 usuario: grupo
⚡ 4096: tamaño
😃 archivo.txt: nombre

**📌 Grupos y privilegios**
Los usuarios pueden pertenecer a grupos . Algunos grupos importantes son:

GRUPO            DESCRIPCIÓN
sudo             Usuarios que pueden usar «sudo».
adm              Pueden leer logs del sistema.
cdrom, plugdev   Para accesos a dispositivos

Para ver a qué groupos perteneces:
<code>$ groups</code>

Para añadir a un usuario al grupo sudo (dándole permisos de administrador):

Zsh
<code>sudo usermod -aG sudo nombredeusuario</code>

Finding yourself with pwd

Zsh
<code>pwd</code>

Cheking your login whoami

Zsh
<code>whoami</code>

**🆘 Getting Help**
I needed help using the best wireless cracking tool, aircrack-ng, I could simply type the aircrack-ng command followed by the --help command:

Zsh
```
aircrack-ng --help
```

I needed help using the hacker’s best port-scanning tool, nmap, I would enter the following:

Zsh
```
nmap -h
```

Referencing Manual Pages with man

Zsh
<code>man aircrack-ng</code>

**🍨 Finding Stuff**

Searching with locate

Zsh
```
locate aircrack-ng
```

Finding binaries with whereis

Zsh
```
whereis aircrack-ng
```

Finding binaries in the PATH variable with which

Zsh
```
which aircrack-ng
```

**⚡ Performing More Powerful Searches with find**
So, if I wanted to search for a file with the name _apache2_ starting in the root directory, I would enter the following:

Zsh
```
find / -type f -name apache2
```

One way to speed it up is to look only in the directory where you would expect to find the file(s) you need. 

Zsh
```
find /etc -type f -name apache2
```

Let’s look in the /etc directory for all files that begin with apache2 and
have any extension. 

Zsh
```
find /etc -type f -name apache2.\*
```

**💊 Filtering with grep**

Zsh
```
ps aux
```

Esto me proporciona una lista de todos los procesos que se están ejecutando en este sistema, pero ¿qué pasa si solo quiero encontrar un proceso para comprobar si se está ejecutando?
Puedo hacerlo canalizando la salida de ps a grep y buscando una palabra clave. Por ejemplo, para saber si el servicio apache2 se está ejecutando, escribiría lo siguiente.

Zsh
```
ps aux | grep apache2
```

Este comando le dice a Linux que muestre todos mis servicios y luego envíe esa salida a grep, que buscará en la salida la palabra clave apache2 y luego mostrará solo la salida relevante, ahorrándome así un tiempo considerable y mi vista.

## 🧩 Modifying Files and Directories.

- <code>cat</code><code>></code><code>>></code> new file
- <code>touch</code> new_file
- <code>mkdir</code> new_directory
- <code>cp</code> file_name /root/newdirectory/newfile
- <code>mv</code> file_name new_file_name
- <code>rm</code> file_name
- <code>rm -r</code>
