# 🔍 Puerto 21 - FTP

##

## 🔹 Puerto 21 - FTP (File Transfer Protocol)

El **puerto 21** es el puerto estándar utilizado por el protocolo **FTP** para la transferencia de archivos entre un cliente y un servidor. **FTP** puede operar en **modo activo** o **modo pasivo**, dependiendo de la configuración del servidor y las restricciones de red.

#### 🔍 Reconocimiento del Puerto 21

Si encontramos el **puerto 21** abierto, debemos centrarnos en verificar si el acceso mediante el usuario **anonymous** está habilitado. Para ello, podemos utilizar los scripts de **Nmap**.

```bash
ls -lah /usr/share/nmap/scripts | grep "ftp-*" # Buscar todos los scriptps que tiene nmap para FTP.
nmap -p21 -sCV <ip_objetivo> 
nmap --script=ftp-anon -p 21 <ip_objetivo> # Utilizar script específico.
nmap --script "ftp-*" -p 21 <ip_objetivo> # Utilizar todos los scripts relacionados con el serivicio ftp.
```

<figure><img src="../.gitbook/assets/Captura de pantalla 2025-02-22 085859.png" alt=""><figcaption></figcaption></figure>



Si en el reporte se indica que el acceso mediante el usuario **anonymous** está habilitado, procederemos a conectarnos al servicio **FTP** con el siguiente comando:

```bash
ftp <ip_obetivo> # Esperamos a que nos solicite las credenciales.
```

Esperamos a que el servicio nos solicite las credenciales. Cuando se nos pida ingresar un usuario y una contraseña, debemos utilizar:

```bash
username: anonymous
password: anonymous
```

Si el inicio de sesión con el usuario **anonymous** no estuviera habilitado, podríamos utilizar la herramienta **Hydra** para realizar pruebas de acceso mediante la siguiente sintaxis:

```bash
hydra -l <username> -P /usr/share/wordlists/rockyou.txt ftp # Podemos utilizar el diccionario de nuestra elección.
```

Una vez que hayamos conseguido acceder al servicio **FTP**, independientemente del método utilizado, es fundamental conocer y utilizar una serie de comandos clave para interactuar con el sistema y verificar qué opciones están disponibles.

```bash
ls - # Listar los directórios o archivos que hay disponibles. 
get <nombre_archivo> - # Descargar archivo nombrado.
put <nombre_archivo> - # Este comando debemos ver si lo tenemos disponible y nos servirá para subir archivos desde nuestra máquina atacante al servicio 21.
wget -m ftp://anonymous:anonymous@<ip> # Descargarmos todo el contenido del directório FTP.
```

#### **🔹 Explotación con Metasploit Framework en servidores FTP**

**Metasploit Framework** proporciona varios módulos diseñados para explotar vulnerabilidades en servidores **FTP**. A continuación, algunos ejemplos prácticos:

```bash
use auxiliary/scanner/ftp/ftp_version # Enumeración FTP
set RHOSTS <ip_target>/24 # ip de la máquina víctima.
set THREADS 50 
exploit 
 
use auxiliary/scanner/ftp/ftp_login # Fuerza bruta FTP.
set RHOSTS <ip_target> # ip de la máquina víctima.
set USER_FILE /path/to/users.txt # Seleccionamos diccionario de usuarios.
set PASS_FILE /path/to/passwords.txt # Seleccionamos diccionario de contraseñas.
set THREADS 10 
exploit
```

> Siempre recomiendo probar distintos tipos de ataques, reconocimiento y exploración con varias herramientas. Así se aprende más y se pueden encontrar las mejores opciones para cada caso.

## Check List:

* [ ] Comprobar si está habilitado el login mediante el usuario anonymous. ✅
* [ ] Comprobar versión del servicio FTP por si hubiera alguna vulnerabilidad. ✅
* [ ] Comprobar si nos deja subir archivos al servicio con el comando `put.` ✅

{% embed url="https://www.youtube.com/watch?ab_channel=HenkoSec&v=vHgWnL95HhQ" %}

