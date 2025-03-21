# INF2310LAB
## Leviathan

### Nivel 0

**Descripción:** Para el primer nivel, debemos iniciar sesión en Leviathan mediante SSH con las credenciales proporcionadas.

**Usuario:** leviathan0
**Contraseña:** leviathan0

**Solución:**
```bash
ssh leviathan0@leviathan.labs.overthewire.org
```

### Nivel 0 → Nivel 1

**Solución:**
Exploramos el directorio home:
```bash
ls -a
```
Vemos un directorio oculto llamado .backup. Al ingresar en él, encontramos un archivo llamado bookmarks.html. Buscamos referencias a "leviathan1" dentro del archivo:
```bash
grep leviathan1 bookmarks.html
```
Esto nos revela la contraseña.
La contraseña para el nivel 1 es: 3QJ3TgzHDq.

### Nivel 1 → Nivel 2

**Solución:**
Listamos los archivos disponibles en el directorio home:
```bash
ls -a
```
Vemos un ejecutable llamado check. Lo ejecutamos:
```bash
./check
```
Nos solicita una contraseña, y al ingresar "1234", obtenemos un mensaje de error.
Ejecutamos ltrace para analizar las llamadas a librerías:
```bash
ltrace ./check
```
En la salida vemos que strcmp compara nuestra entrada con "sex". Probamos con esta palabra clave:
```bash
./check
password: sex
```
Esto nos permite cambiar al usuario leviathan2. Ahora leemos la contraseña del siguiente nivel:
```bash
cat /etc/leviathan_pass/leviathan2
```
La contraseña para el nivel 2 es: NsN1HwFoyN.

### Nivel 2 → Nivel 3

**Solución:**
Listamos los archivos disponibles en el directorio home:
```bash
ls -la
```
Vemos un ejecutable llamado printfile con permisos SUID del usuario leviathan3. Intentamos ejecutarlo con un archivo:
```bash
./printfile /etc/leviathan_pass/leviathan3
```
Nos muestra un mensaje de error: "You cant have that file...".
Ejecutamos ltrace para analizar su comportamiento:
```bash
ltrace ./printfile test.txt
```
Observamos que usa access() para verificar permisos y luego usa /bin/cat para mostrar el contenido del archivo. Podemos aprovechar esto creando un archivo con un espacio en su nombre:
```bash
touch "pass file.txt"
ltrace ./printfile "pass file.txt"
```
Esto divide la entrada en dos archivos: pass y file.txt. Creamos un enlace simbólico para explotar esta vulnerabilidad:
```bash
ln -s /etc/leviathan_pass/leviathan3 pass
./printfile "pass file.txt"
```
Esto nos muestra la contraseña.
La contraseña para el nivel 3 es: f0n8h2iWLP.

### Nivel 3 → Nivel 4

**Solución:**
Listamos los archivos disponibles en el directorio home:
```bash
ls -la
```
Vemos un ejecutable llamado level3 con permisos SUID del usuario leviathan4. Lo ejecutamos:
```bash
./level3
Enter the password> 1234
bzzzzzzzzap. WRONG
```
Parece que verifica una contraseña.
Ejecutamos ltrace para analizar su comportamiento:
```bash
ltrace ./level3
```
Vemos que compara nuestra entrada con la cadena snlprintf. Probamos esta palabra como contraseña:
```bash
./level3
Enter the password> snlprintf
[You've got shell]!
```
Esto nos otorga acceso al usuario leviathan4. Ahora leemos la contraseña del siguiente nivel:
```bash
cat /etc/leviathan_pass/leviathan4
```
Esto nos muestra la contraseña.
La contraseña para el nivel 4 es: WG1egElCvO.

### Nivel 4 → Nivel 5

**Solución:**
Listamos los archivos en el directorio home:
```bash
ls -la
```
Encontramos un directorio oculto .trash:
```bash
cd .trash
ls -la
```
Dentro de .trash, hay un archivo ejecutable llamado bin con permisos SUID del usuario leviathan5. Al ejecutarlo:
```bash
./bin
```
La salida muestra una secuencia binaria: 01010100 01101001 .... Convertimos esta secuencia a ASCII usando una herramienta en línea y obtenemos la contraseña.
La contraseña para el nivel 5 es: 0dyxT7F4QD.

### Nivel 5 → Nivel 6

**Solución:**
Listamos los archivos en el directorio home:
```bash
ls -la
```
Encontramos un ejecutable llamado leviathan5 con permisos SUID del usuario leviathan6. Lo ejecutamos:
```bash
./leviathan5
```
El mensaje indica que busca un archivo en /tmp/file.log. Analizamos con ltrace:
```bash
ltrace ./leviathan5
```
Vemos que usa fopen("/tmp/file.log", "r"). Para explotar esto, creamos un enlace simbólico hacia la contraseña:
```bash
ln -s /etc/leviathan_pass/leviathan6 /tmp/file.log
./leviathan5
```
Esto nos muestra la contraseña del siguiente nivel.
La contraseña para el nivel 6 es: szo7HDB88w.

### Nivel 6 → Nivel 7

**Solución:**
Listamos los archivos en el directorio home:
```bash
ls -la
```
Encontramos un ejecutable llamado leviathan6. Al ejecutarlo:
```bash
./leviathan6
```
Nos solicita un código de 4 dígitos. Para forzar el código, escribimos un script de fuerza bruta:
```bash
#!/bin/bash
for a in {0000..9999}; do
  ~/leviathan6 $a
done
```
Lo guardamos, damos permisos de ejecución y lo ejecutamos:
```bash
chmod +x brute.sh
./brute.sh
```
El script ejecuta todas las combinaciones y nos da acceso al usuario leviathan7. Luego, obtenemos la contraseña:
```bash
cat /etc/leviathan_pass/leviathan7
```
La contraseña para el nivel 7 es: qEs5Io5yM8.

### Nivel 7

**Descripción:**
Al acceder al nivel 7, encontramos un archivo CONGRATULATIONS. Lo leemos:
```bash
cat CONGRATULATIONS
```

**Contenido del mensaje:**
El mensaje indica que hemos completado Leviathan y sugiere intentar desafíos más avanzados.
```bash
Well Done, you seem to have used a *nix system before, now try something more serious.
(Please don't post writeups, solutions or spoilers about the games on the web. Thank you!)
```