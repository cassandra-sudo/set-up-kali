![](https://raw.githubusercontent.com/cassandra-sudo/set-up-kali/main/chapter2/image/cover.png)

# 🗒️ Text Manipulation

A modo de ejemplo, usaré archivos del mejor sistema de detección de intrusiones en red (NIDS) del mundo, Snort, desarrollado inicialmente por Marty Roesch y ahora propiedad de Cisco. Los NIDS se utilizan habitualmente para detectar intrusiones de hackers, así que si quieres ser un hacker exitoso, debes estar familiarizado con las formas en que los NIDS pueden disuadir ataques y cómo puedes abusar de ellos para evitar ser detectado.

Si no viene instalado por defecto, lo descargamos con <code>sudo apt install snort</code>.

Verifica que este instalado:

bash
```
snort -v
```

### ⭐ Viewing Files

bash
```
# The most basic display command
cat /etc/snort/snort.lua

# See the first 20 lines of the file
head -20 /etc/snort/snort.lua

# View the last lines of a file
tail /etc/snort/snort.lua

# Numbering the lines
nl /etc/snort/snort.lua

```

### 💎 Filtering with grep

El comando grep es probablemente el más utilizado para la manipulación de texto. Permite filtrar el contenido de un archivo para su visualización. Por ejemplo, si desea ver todas las líneas que incluyen la palabra «output» en su archivo <code>snort.conf</code>, puede usar <code>cat</code> y pedirle que muestre solo esas líneas.

bash
```
cat /etc/snort/snort.lua | grep output
```

### 🕵🏼‍♀️ Hacker Challenge: Using grep, nl, tail, and head**

Supongamos que quieres mostrar las cinco líneas inmediatamente anteriores a la línea que dice **-- 5. configure detection**: Configurar los complementos de salida usando al menos cuatro de los comandos que acabas de aprender. ¿Cómo lo harías? (Hint: estos comandos tienen muchas más opciones que las que hemos visto. Puedes aprender más comandos usando el comando integrado de Linux "man". Por ejemplo, <code>man tail</code> mostrará el archivo de ayuda del comando <code>tail</code>).
Hay muchas maneras de resolver este desafío; aquí te muestro qué líneas debes cambiar para hacerlo de una manera, y tu trabajo es encontrar otro método.

**Paso 1**
***

bash
```
nl /etc/snort/snort.lua | grep configure
```

![](https://raw.githubusercontent.com/cassandra-sudo/set-up-kali/main/chapter2/image/cat_snort.png)

Podemos ver que la línea **-- 5. configure detection**: Configurar complementos de salida es la línea 143, y sabemos que queremos las cinco líneas anteriores a la línea 143, así como la línea 512 en sí (es decir, las líneas 138 a 143).

