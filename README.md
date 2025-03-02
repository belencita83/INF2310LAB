# INF2310LAB
## Bandit

### Nivel 00

**Descripción:** En este nivel, tienes que conectarte al servidor SSH con la contraseña proporcionada.

**Comandos utilizados:**
```bash
ssh bandit0@bandit.labs.overthewire.org
```
**Solución:** La contraseña para el nivel 0 fue bandit0.

### Nivel 0

**Descripción:** En este nivel, debes encontrar el archivo readme en el directorio home y obtener la contraseña.

**Comandos utilizados:**
```bash
ls            # Listar los archivos en el directorio
cat readme    # Mostrar el contenido del archivo 'readme'
```
**Solución:** La contraseña para el nivel 1 es: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If.

### Nivel 1

**Descripción:** En este nivel, debes encontrar un archivo oculto llamado - y leer su contenido para obtener la contraseña.

**Comandos utilizados:**
```bash
ls             # Listar los archivos en el directorio
cat ./-        # Leer el archivo oculto '-'
```
**Solución:** La contraseña para el nivel 2 es: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx.

### Nivel 2

**Descripción:** En este nivel, hay un archivo con espacios en su nombre que debes leer para obtener la contraseña.

**Comandos utilizados:**
```bash
ls                                # Listar los archivos en el directorio
cat spaces\ in\ this\ filename    # Leer el archivo con espacios en el nombre
```
**Solución:** La contraseña para el nivel 3 es: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx.

### Nivel 3

**Descripción:** En este nivel, debes acceder a un directorio llamado inhere y leer el archivo ...Hiding-From-You para obtener la contraseña.

**Comandos utilizados:**
```bash
ls                        # Listar los archivos en el directorio
cd inhere/                # Acceder al directorio 'inhere'
ls -la                    # Listar los archivos detallados en 'inhere'
cat ...Hiding-From-You    # Leer el archivo con el nombre oculto
```
**Solución:** La contraseña para el nivel 4 es: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ.

### Nivel 4

**Descripción:** En este nivel, hay varios archivos llamados -fileXX en el directorio inhere. Debes encontrar el archivo que contiene la contraseña.

**Comandos utilizados:**
```bash
ls               # Listar los archivos en el directorio
file ./-file00   # Verificar el tipo de archivo
file ./-file01   # Verificar el tipo de archivo
...
cat ./-file07    # Leer el archivo que contiene la contraseña
```
**Solución:** La contraseña para el nivel 5 es: 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw.

### Nivel 5

**Descripción:** En este nivel, hay múltiples directorios llamados maybehereXX dentro del directorio inhere. Debes encontrar un archivo oculto que: Sea legible. Tenga un tamaño exacto de 1033 bytes. No sea ejecutable.

**Comandos utilizados:**
```bash
ls                                              # Listar los archivos y directorios en 'inhere'
find . -readable -size 1033c -not -executable   # Buscar el archivo con las características indicadas
cat ./maybehere07/.file2                        # Leer el archivo encontrado
```
**Solución:** La contraseña para el nivel 6 es: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG.

### Nivel 6

**Descripción:** En este nivel, debes encontrar un archivo en el sistema que: Es propiedad del usuario bandit7. Pertenece al grupo bandit6. Tiene un tamaño exacto de 33 bytes.

**Comandos utilizados:**
```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null   # Buscar el archivo evitando errores de permisos
cat /var/lib/dpkg/info/bandit7.password                     # Leer el contenido del archivo encontrado
```
**Solución:** La contraseña para el nivel 7 es: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj.

### Nivel 7

**Descripción:** En este nivel, debemos encontrar una línea específica dentro del archivo data.txt. La línea contiene la palabra "millionth" seguida de la contraseña.

**Comandos utilizados:**
```bash
ls                          # Listar los archivos en el directorio
wc -l data.txt              # Contar las líneas del archivo 'data.txt'
cat data.txt                # Mostrar todo el contenido del archivo (no recomendado para archivos grandes)
grep "millionth" data.txt   # Filtrar y encontrar la línea que contiene "millionth"
```
**Solución:** La contraseña para el nivel 8 es: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc.

### Nivel 8

**Descripción:** En este nivel, el archivo data.txt contiene 1001 líneas de texto, de las cuales una sola línea aparece una vez. La tarea es encontrar esa línea única, que contiene la contraseña.

**Comandos utilizados:**
```bash
ls                          # Listar los archivos en el directorio
wc -l data.txt              # Contar las líneas del archivo 'data.txt'
cat data.txt                # Mostrar todo el contenido del archivo (no recomendado)
sort data.txt               # Ordenar las líneas del archivo
uniq -c                     # Contar cuántas veces aparece cada línea
grep -v 10                  # Filtrar las líneas que no aparecen 10 veces (muestra la única repetida 1 vez)
```
**Solución:** La contraseña para el nivel 9 es: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM.

### Nivel 9

**Descripción:** En este nivel, el archivo data.txt es un archivo binario que contiene datos no legibles directamente. La tarea es encontrar la contraseña oculta dentro de él.

**Comandos utilizados:**
```bash
ls                          # Listar los archivos en el directorio
file data.txt               # Identificar el tipo de archivo
strings data.txt            # Extraer cadenas de texto legibles desde el archivo binario
grep =                      # Filtrar las líneas que contienen el carácter '='
```
**Solución:** Dentro del contenido extraído, se observó que la contraseña estaba en la línea con el formato "password is ...". La contraseña para el nivel 10 es: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey.

### Nivel 10

**Descripción:** En este nivel, el archivo data.txt contiene un texto codificado en Base64. La tarea es decodificarlo para obtener la contraseña.

**Comandos utilizados:**
```bash
ls                          # Listar los archivos en el directorio
cat data.txt                # Ver el contenido del archivo
cat data.txt | base64 -d    # Decodificar el contenido en Base64
```
**Solución:** Después de decodificar el texto en Base64, se obtuvo la siguiente contraseña para el nivel 11: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr.

### Nivel 11

**Descripción:** El archivo data.txt contiene un texto cifrado en ROT13, un cifrado de sustitución que reemplaza cada letra por la que está 13 posiciones adelante en el alfabeto. La tarea es descifrarlo para obtener la contraseña.

**Comandos utilizados:**
```bash
ls -l                                       # Ver permisos y dueño del archivo
cat data.txt                                # Ver el contenido del archivo
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'    # Descifrar ROT13
```
**Solución:** Después de aplicar ROT13, se obtuvo la siguiente contraseña para el nivel 12: 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4.

### Nivel 12

**Descripción:** En este nivel, encontramos un archivo llamado data.txt que ha sido comprimido y codificado varias veces. La tarea consiste en revertir estos procesos para revelar la contraseña del siguiente nivel.

**Comandos utilizados:**
```bash
file data.txt                  # Identificar el tipo de archivo
mv data.txt data.gz            # Cambiar nombre para reconocer extensión
gunzip data.gz                 # Extraer archivo
mv data data.bz2               # Cambiar nombre para reconocer extensión
bzip2 -d data.bz2              # Extraer archivo
mv data data.tar               # Cambiar nombre para reconocer extensión
tar -xf data.tar               # Extraer archivos del tar
base64 -d data > data_decoded  # Decodificar contenido
mv data_decoded data           # Renombrar archivo decodificado
cat data.txt                   # Mostrar el contenido final (debería contener la contraseña)
```
**Solución:** Después de repetir los pasos de extracción y decodificación, finalmente obtenemos la contraseña para el nivel 13: FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn.

### Nivel 13

**Descripción:** En este nivel, la contraseña de bandit14 no está almacenada en un archivo de texto como en niveles anteriores, sino que se proporciona una clave SSH privada (sshkey.private) en el directorio de bandit13. Esta clave nos permite acceder al siguiente usuario sin necesidad de una contraseña.

**Comandos utilizados:**
```bash
ls                                               # Listar archivos en el directorio de bandit13
ssh -i sshkey.private bandit14@localhost -p 2220 # Conectarse a bandit14 usando la clave privada SSH
```
**Solución:** Usamos ls para ver qué archivos hay en el directorio. Vemos que existe sshkey.private, que es una clave privada SSH.
              Nos conectamos a bandit14 usando esta clave con el comando: ssh -i sshkey.private bandit14@localhost -p 2220
              Esto nos permite acceder sin necesidad de ingresar una contraseña.

### Nivel 14

**Descripción:** En este nivel, la contraseña de bandit15 se encuentra en un archivo de texto ubicado en /etc/bandit_pass/bandit14, pero para continuar necesitamos enviarla a un servicio escuchando en el puerto 30000 usando netcat (nc).

**Comandos utilizados:**
```bash
cat /etc/bandit_pass/bandit14   # Leer la contraseña de bandit14
nc localhost 30000              # Conectar al puerto 30000 y enviar la contraseña
```
**Solución:** Obtenemos la contraseña de bandit14 usando: cat /etc/bandit_pass/bandit14. La contraseña obtenida es: MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS. Nos conectamos al servicio en el puerto 30000 con nc: nc localhost 30000. Luego, ingresamos la contraseña anterior y presionamos Enter.
              Obtenemos la contraseña para el nivel 15: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo.

