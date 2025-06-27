![](https://raw.githubusercontent.com/cassandra-sudo/set-up-kali/main/image/cover.png)

# 🥁 Primeros pasos en GNU/Linux.

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
sudo passwd root
```