# INF2310LAB
## Krypton

## Nivel 0 ➔ 1

**Descripción:** En este nivel, se nos instruye a ingresar al servidor mediante SSH usando el nombre de usuario `krypton1` y la contraseña Base64 codificada.

**Solución:**
Abrimos una terminal y nos conectamos al servidor usando el siguiente comando:
```bash
ssh krypton1@krypton.labs.overthewire.org -p 2231
```
La contraseña está codificada en Base64. Se puede utilizar una herramienta como CyberChef para decodificarla.
La contraseña decodificada para el nivel 1 es: KRYPTONISGREAT.

## Nivel 1 ➔ 2

**Descripción:** En este nivel, se nos indica que la mayoría de los niveles están almacenados en el directorio `/somegame/`. Se debe cambiar al directorio `/krypton1` y leer el archivo README. El archivo contiene un mensaje cifrado usando el cifrado ROT13.

**Solución:**
Accedemos al directorio `/somegame/` usando:
```bash
cd /somegame/
```
Cambiamos al directorio `krypton1`:
```bash
cd krypton1
```
Leemos el archivo `README`:
```bash
cat README
```
El mensaje dentro del archivo `README` está cifrado con ROT13. Usamos una herramienta como [Cryptii](https://cryptii.com) para decodificar el texto en ROT13.
La contraseña decodificada para el nivel 2 es: ROTTEN.

## Nivel 2 ➔ 3

**Descripción:** En este nivel, tenemos un archivo de clave cifrado y un programa que cifra nuestra entrada usando el mismo método. El desafío consiste en descubrir el valor exacto del desplazamiento del Cifrado César.

**Solución:**
Cambiamos al directorio del desafío:
```bash
cd /krypton/krypton2
```
Leemos el archivo `README`:
```bash
cat README
```
El archivo contiene una clave cifrada con Cifrado César, pero no sabemos el valor del desplazamiento. Para encontrarlo, podemos generar un archivo de prueba y cifrarlo.
Creamos una carpeta temporal y enlazamos el archivo de clave:
```bash
mktemp -d
cd /tmp/tmp.1mLghTok9p
ln -s /krypton/krypton2/keyfile.dat
chmod 777 .
```
Creamos un archivo de prueba con la letra "A":
```bash
echo "AAA" > example.txt
```
Ciframos el archivo y observamos el desplazamiento. El carácter resultante será "M", lo que significa que el valor del desplazamiento es 12.
Usando una herramienta como Cryptii, decodificamos el texto cifrado con un desplazamiento de 12.
La contraseña decodificada para el nivel 3 es: CAESARISEASY.

## Nivel 3 ➔ 4

**Descripción:** En este nivel, se nos presenta un texto cifrado con un método de sustitución más avanzado. La solución implica el análisis de frecuencia de las letras para encontrar el valor de la clave.

**Solución:**
Cambiamos al directorio del desafío:
```bash
cd /krypton/krypton3
```
Leemos el archivo `README`:
```bash
cat README
```
El mensaje nos dice que el texto ha sido cifrado con un método de sustitución. Sin embargo, dado que tenemos varios textos cifrados interceptados, podemos usar análisis de frecuencia para descubrir el patrón.
Analizamos la frecuencia de las letras en el texto cifrado utilizando herramientas en línea que nos muestran la frecuencia de las letras en textos en inglés.
De acuerdo con el análisis, la letra "S" en el texto cifrado corresponde a la letra "e" en el texto original, "Q" corresponde a "t", y así sucesivamente.
Al observar patrones como letras repetidas en el texto cifrado, podemos deducir la clave. Por ejemplo, "VV" se repite, lo que sugiere que "V" corresponde a una letra que aparece dos veces en el texto original, como la "e".
Podemos usar una herramienta como [quipquip](https://quipqiup.com) para resolver el cifrado, pegando el texto cifrado y agregando la contraseña al final del texto.
La contraseña obtenida para el nivel 4 es: BRUTE.

## Nivel 4 ➔ 5

**Descripción:** En este nivel, se utiliza un cifrado de Vigenère con una longitud de clave de 6. El desafío consiste en descifrar el texto cifrado utilizando la clave correcta.

**Solución:**
Cambiamos al directorio del desafío:
```bash
cd /krypton/krypton4
```
Lee el archivo `README`:
```bash
cat README
```
El archivo nos informa que se utiliza un cifrado de Vigenère y que la longitud de la clave es 6. El texto cifrado es: `HCIKV RJOX`.
Usamos una herramienta como [Dcode.fr](https://www.dcode.fr/vigenere-cipher) para descifrar el texto. Ingresamos el texto cifrado y especificamos una longitud de clave de 6.
El resultado sugiere que la clave es `FREKEY`. Utilizamos esta clave para descifrar el texto y obtener el siguiente mensaje.
Usando la clave `FREKEY`, desciframos el mensaje cifrado `HCIKV RJOX`, y obtenemos la contraseña para el siguiente nivel.
La contraseña obtenida para el nivel 5 es: CLEARTEXT.

## Nivel 5 ➔ 6

**Descripción:** En este nivel, no se nos proporciona la longitud de la clave. Nuestro primer objetivo es determinar la longitud de la clave y luego utilizarla para encontrar la clave y descifrar el mensaje.

**Solución:**
Cambiamos al directorio del desafío:
```bash
cd /krypton/krypton5
```
Leemos el archivo `README`:
```bash
cat README
```
La clave no está proporcionada, pero podemos usar una herramienta como [Dcode.fr](https://www.dcode.fr/vigenere-cipher) para determinar la longitud de la clave y descifrar el mensaje automáticamente.
Usamos la función de "Decryption" automática en Dcode.fr, que identificará la longitud de la clave y nos dará el resultado directamente.
El análisis revela que la clave es `KEYLENGTH`. Usando esta clave, desciframos el texto `BELOS Z` y obtenemos la contraseña para el siguiente nivel.
La contraseña obtenida para el nivel 6 es: RANDOM.

## Nivel 6 ➔ 7

**Descripción:** Este nivel introduce el concepto de "One Time Pad" (OTP) y cifrados de flujo. El desafío consiste en realizar un ataque de texto claro conocido (chosen-plaintext attack) usando una clave débil generada aleatoriamente y cifrada con un algoritmo de flujo.

**Solución:**
Cambiamos al directorio del desafío:
```bash
cd /krypton/krypton6
```
Lee el archivo `README`:
```bash
cat README
```
El desafío utiliza un cifrado de flujo y se nos proporciona una clave débil. Se sugiere realizar un ataque de texto claro conocido utilizando un archivo de entrada que controlemos y un generador de números aleatorios débil.
Creamos un archivo de prueba con 50 caracteres "A":
```bash
cd /tmp
touch test.txt
python -c "print 'A'*50" > test.txt
```
Luego, creamos un enlace simbólico al archivo `keyfile.dat` y usamos el programa de cifrado `encrypt6`:
```bash
ln -s /krypton/krypton6/keyfile.dat
/krypton/krypton6/encrypt6 test.txt output.txt
cat output.txt
```
Observamos que el texto cifrado se repite después de un número determinado de caracteres. Esto indica la longitud del keystream.
Realizamos el mismo proceso con 50 caracteres "B" en lugar de "A" para obtener otro texto cifrado repetido.
Ahora podemos comparar los dos textos cifrados y conocer las transformaciones para cada letra.
Usamos un script en Python para calcular la diferencia de cada carácter en el texto cifrado y aplicar un descifrado.
El script de Python calcula las diferencias de desplazamiento para cada letra y las aplica al texto cifrado de la bandera para obtener el siguiente mensaje.
La contraseña obtenida para el nivel 7 es: LFSRISNOTRANDOM.

## Nivel 7

**Descripción:**
Cambiamos al directorio del desafío:
```bash
cd /krypton/krypton7
```
Lee el archivo `README`:
```bash
cat README
```

**Contenido del mensaje:**
El mensaje indica es el siguiente:
```bash
Congratulations on beating Krypton!```
