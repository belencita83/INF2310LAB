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