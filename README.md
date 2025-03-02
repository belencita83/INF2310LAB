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
