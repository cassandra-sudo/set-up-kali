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

Podemos ver que la línea **-- 5. configure detection**: Configurar se configura la detección de amenazas es la línea 143, y sabemos que queremos las cinco líneas anteriores a la línea 143, así como la línea 143 en sí (es decir, las líneas 138 a 143).

**Paso 2**
***

bash
```
tail -n+143 /etc/snort/snort.lua | head -n 6
```

![](https://raw.githubusercontent.com/cassandra-sudo/set-up-kali/main/chapter2/image/cat_snort2.png)

**⚡ Using sed to Find and Replace**

El comando sed permite buscar instancias de una palabra o un patrón de texto y luego realizar una acción sobre él. El nombre del comando Text Manipulation 23 es una contracción de _stream editor_. En su forma más básica, sed funciona como la función Buscar y Reemplazar de Windows.

Busque la palabra «outputs» en el archivo <code>snort.conf</code> usando grep, de la siguiente manera:

bash
```
cat /etc/snort/snort.lua | grep outputs
```

![](https://raw.githubusercontent.com/cassandra-sudo/set-up-kali/main/chapter2/image/outputs.png)

Debería ver que el comando <code>grep</code> encontró dos instancias de «outputs».

Supongamos que desea que sed reemplace cada instancia de «outputs» con «Salida» (recuerde que la mayor parte de Linux distingue entre mayúsculas y minúsculas) y luego guarde el nuevo archivo en snort2.conf.

bash
```
sed s/outputs/Salida/g /etc/snort/snort.lua > snort2.lua
```

El comando <code>s</code> realiza la sustitución: primero se introduce el término buscado (mysql) y luego el término por el que se desea reemplazar (MySQL), separados por una barra diagonal (<code>/</code>). El indicador <code>g</code> indica a Linux que se desea que la sustitución se realice globalmente. El resultado se guarda en un nuevo archivo llamado <code>snort2.conf</code>.

Si quisiera reemplazar solo la primera aparición del término mysql, debería omitir la opción <code>g</code> final.

bash
```
sed s/outputs/Salida/ /etc/snort/snort.lua > snort2.lua
```

También puede usar el comando sed para buscar y reemplazar cualquier ocurrencia específica de una palabra, en lugar de todas las ocurrencias o solo la primera. Por ejemplo, si desea reemplazar solo la segunda ocurrencia de la palabra mysql, simplemente coloque el número de la ocurrencia (en este caso, 2) al final del comando:

bash
```
sed s/outputs/Salida/2 /etc/snort/snort.lua > snort2.lua
```

### 🎁 Viewing Files with more and less**

**Controlling the Display with more**

El comando <code>more</code> muestra una página de un archivo a la vez y le permite avanzar página hacia abajo usando la tecla <code>Down</code>.

bash
```
more /etc/snort/snort.lua
```

**Displaying and Filtering with less**

