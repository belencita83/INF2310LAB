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

### Nivel 15

**Descripción:** En este nivel, encontramos un servidor en el puerto 30001 que requiere autenticación mediante un binario SSL. Debemos usar openssl para conectarnos y enviar la contraseña del nivel actual para obtener la del siguiente nivel.

**Comandos utilizados:**
```bash
openssl s_client    # Se usa para establecer una conexión segura con un servidor SSL/TLS
echo                #  Imprime un mensaje en la terminal
nc (netcat)         # Para probar la conexión antes de usar openssl (opcional)
```
**Solución:** Conectarse al servidor en el puerto 30001 usando openssl: openssl s_client -connect localhost:30001 -quiet
Una vez dentro, enviar la contraseña del nivel 15. Recibiremos la contraseña para el nivel 16: kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx.

### Nivel 16

**Descripción:** En este nivel, se nos proporciona la contraseña encriptada y necesitamos descifrarla utilizando una conexión segura. Se nos informa que hay varios puertos abiertos en localhost y debemos encontrar el que nos permita obtener la clave privada SSH para conectarnos al siguiente nivel.

**Comandos utilizados:**
```bash
nmap -p 31000-32000 localhost                               # Escanear puertos abiertos en el rango 31000-32000
openssl s_client -connect localhost:PUERTO -quiet           # Conectar con OpenSSL a los puertos abiertos manualmente
nano rsafile                                                # Guardar la clave privada en un archivo
chmod 600 rsafile                                           # Asignar permisos seguros al archivo
```
**Solución:** Usar ssh -i rsafile bandit17@... para acceder al nivel 17. Ahora tenemos acceso al siguiente nivel.

### Nivel 17

**Descripción:** En este nivel, la contraseña para el siguiente nivel está almacenada en el archivo /etc/bandit_pass/bandit17. Sin embargo, el usuario bandit17 solo tiene permisos para leer este archivo cuando inicia sesión a través de un programa especial que se ejecuta en port 30001 en localhost.

**Comandos utilizados:**
```bash
whoami                                           # Verificar el usuario actual
ssh bandit17@bandit.labs.overthewire.org -p 2220 # Conectar al servidor con SSH
cat /etc/bandit_pass/bandit17                    # Intentar leer la contraseña del siguiente nivel
diff passwords.old passwords.new                 # Comparar los archivos
```
**Solución:** Comparando passwords.old y passwords.new, obtenemos el valor actualizado, la contraseña: x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO.

### Nivel 18

**Descripción:** Al conectarnos con bandit18, la sesión se cierra inmediatamente después del inicio de sesión. Esto significa que no podemos interactuar con el sistema de manera normal y debemos encontrar una forma alternativa de leer archivos.

**Comandos utilizados:**
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220            # Conectarnos al servidor con la contraseña obtenida del nivel anterior
ssh bandit18@bandit.labs.overthewire.org -p 2220 ls         # Intentamos listar archivos antes de que la sesión se cierre
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme # Leemos el contenido del archivo readme antes de la desconexión forzada
ls -la                                                      # Comprobamos los permisos de los archivos
```
**Solución:** Dado que la sesión se cierra inmediatamente, ejecutamos el comando cat readme directamente en la conexión SSH. Esto nos devuelve la contraseña para el nivel 19: cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8.

### Nivel 19

**Descripción:** Al conectarnos como bandit19, encontramos un archivo llamado bandit20-do, que tiene el permiso SUID activado (-rwsr-x---). Esto significa que cuando ejecutamos este archivo, se ejecuta con los privilegios del usuario bandit20 en lugar de los de bandit19. El archivo bandit20-do permite ejecutar comandos como bandit20, lo que nos da la oportunidad de leer la contraseña del siguiente nivel.

**Comandos utilizados:**
```bash
./bandit20-do                               # Ejecutamos el archivo bandit20-do sin argumentos para ver su uso
./bandit20-do id                            # Verificamos el usuario con el que se ejecuta
./bandit20-do cat /etc/bandit_pass/bandit20 # Leemos la contraseña del usuario bandit20 en /etc/bandit_pass/bandit20
```
**Solución:** Leemos la contraseña del usuario bandit20 en /etc/bandit_pass/bandit20, que devuelve la contraseña para el nivel 20: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO.

### Nivel 20

**Descripción:** En este nivel, encontramos un binario llamado suconnect, el cual, al ejecutarlo con un número de puerto, se conecta a ese puerto en localhost y, si recibe la contraseña correcta, envía la contraseña del siguiente nivel.
Para resolverlo: Iniciar un servidor en un puerto específico para escuchar la conexión de suconnect. Enviar la contraseña actual a suconnect para recibir la nueva.

**Comandos utilizados:**
```bash
ls               # Listar archivos en el directorio
./suconnect      # Comprobar cómo funciona el binario
nc -lvp 2222     # Abrir un puerto con nc para escuchar conexiones
./suconnect 2222 # Ejecutar suconnect para que se conecte al puerto 2222
```
**Solución:** Suconnect se conectó a nuestro servidor en el puerto 2222, recibió la contraseña actual (0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO) y, al ser correcta, nos envió la del nivel 21: EeoULMCra2q0dSkYj561DX7s1CpBuOBt.

### Nivel 21

**Descripción:** En este nivel, encontramos un archivo cron en /etc/cron.d/cronjob_bandit22 que ejecuta un script (/usr/bin/cronjob_bandit22.sh) cada minuto como el usuario bandit22. Este script copia la contraseña del usuario bandit22 a un archivo temporal en /tmp/. El objetivo es leer ese archivo temporal para obtener la contraseña del siguiente nivel.

**Comandos utilizados:**
```bash
cd /etc/cron.d                            # Explorar las tareas cron en /etc/cron.d/.
ls -la                                    # Listar los archivos detallados en 'inhere'
cat cronjob_bandit22                      # Ver el contenido del cronjob de bandit22.
cat /usr/bin/cronjob_bandit22.sh          # Leer el contenido del script.
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv # Leer el archivo temporal donde se guarda la contraseña.
```
**Solución:** Leer el archivo /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv y obtener la contraseña para el nivel 22: tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q.

### Nivel 22

**Descripción:** En este nivel, encontramos un archivo cron en /etc/cron.d/cronjob_bandit23 que ejecuta un script (/usr/bin/cronjob_bandit23.sh) cada minuto como bandit23. Este script genera un hash MD5 de la cadena "I am user bandit23" y lo usa como nombre de archivo en /tmp/ para guardar la contraseña de bandit23.

**Comandos utilizados:**
```bash
cd /etc/cron.d                                      # Listar archivos en /etc/cron.d/
ls                                                  # Listar los archivos en el directorio
cat cronjob_bandit23                                # Ver el contenido del cronjob de bandit23
cat /usr/bin/cronjob_bandit23.sh                    # Leer el contenido del script
echo I am user bandit23 | md5sum | cut -d ' ' -f 1  # Generar el hash MD5 manualmente
cat /tmp/8ca319486bfbbc3663ea0fbe81326349           # Leer el archivo con la contraseña
```
**Solución:** Al leer el archivo con la contraseña: cat /tmp/8ca319486bfbbc3663ea0fbe81326349. Obtenemos la contraseña para el nivel 23: 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga.

### Nivel 23

**Descripción:** Se nos indica que la contraseña para el siguiente nivel está almacenada en un repositorio de git en /home/bandit23-git/repo. Debemos inspeccionar el historial de commits para encontrarla.

**Comandos utilizados:**
```bash
ls -la /home/bandit23-git/repo  # Listar el contenido del repositorio
git log                         # Ver historial de commits
git show <commit_id>            # Ver cambios en un commit específico
```
**Solución:** La contraseña se encuentra en un commit anterior dentro del historial del repositorio Git. La contraseña para el nivel 24: gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8.

### Nivel 24

**Descripción:** En este nivel, hay un programa que solo acepta la contraseña del nivel 23 y un PIN de 4 dígitos. Debemos encontrar el PIN correcto.

**Comandos utilizados:**
```bash
echo UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ 1234 | nc localhost 30002  # Probar conexión con un PIN
echo {0000..9999} | xargs -n1 -P10 -I{} sh -c 'echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ {}" | nc localhost 30002'
# Ataque de fuerza bruta para encontrar el PIN
```
**Solución:** Después de probar todos los PINs posibles, encontramos el correcto. La contraseña para el nivel 25: iCi86ttT4KSNe1armKiwbQNmB3YJP3q4.

### Nivel 25

**Descripción:** El nivel nos da un script en /usr/bin/showtext, que debemos analizar para encontrar la forma de obtener la contraseña.

**Comandos utilizados:**
```bash
ls -la /usr/bin/showtext                    # Ver detalles del script
echo "$(cat /etc/bandit_pass/bandit26)"     # Intentar leer la contraseña
echo "$(more /etc/bandit_pass/bandit26)"    # Usar el comando "more" dentro del script
```
**Solución:** Aprovechamos que more puede abrir un shell interactivo (!sh) para obtener la contraseña para el nivel 26: s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ.

### Nivel 26

**Descripción:** Nos encontramos en un entorno restringido donde la única opción es explotar la ejecución de comandos.

**Comandos utilizados:**
```bash
./bandit27-do cat /etc/bandit_pass/bandit27  # Ejecutar el binario con permisos elevados
```
**Solución:** Ejecutamos ./bandit27-do con el comando cat para leer la contraseña, para el nivel 27 es: upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB.

### Nivel 27

**Descripción:** En este nivel, encontramos un directorio ~/bandit27-git que contiene un repositorio de Git. Nuestra tarea es encontrar la contraseña del siguiente nivel explorando el historial del repositorio.

**Comandos utilizados:**
```bash
ls -la                     # Listar archivos ocultos para encontrar el repositorio Git
cd bandit27-git            # Acceder al directorio del repositorio
git log                    # Ver el historial de commits
git show <commit_id>       # Ver los cambios en un commit específico
git checkout <commit_id>^  # Restaurar una versión anterior del repositorio
```
**Solución:** Al inspeccionar los commits previos con git log y git show, encontramos que la contraseña fue eliminada en un commit anterior. Restauramos esa versión y obtenemos la contraseña para el nivel 28: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN.

