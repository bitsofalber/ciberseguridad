# 🔍 Descubrimiento de HOSTS!

## 🔍 Descubrir equipos activos en nuestra red:

```bash
ip a # Muestra las direcciones IP asignadas a las interfaces de red del sistema.
ifconfig # Saber nuestra interfaz de red y nuestra ip
netdiscover -r <ip>/24 # Indicamos nuestro segmento de red
fping -a -g <ip/24>
sudo masscan -p<puertos> -Pn <rango_de_red> # Podemos analizar nuestra interfaz de red indicandole que nos busque por puertos específicos.
arp-scan -I <interfaz_de_red> --localnet --ignoredups # Buscar hosts en nuestra red local.
nmap -sn <ip>/24 #manda paquetes ICMP a ese segmento de red
sudo nmap -sS --min-rate 5000 -p- --open <ip> -oN tcp_scan.txt # Podemos añadir multiples ips separadas por ","
grep '^[0-9]' tcp_scan.txt | cut -d '/' -f1 | sort -u | xargs | tr ' ' ','
nmap --open -p<puertos> -sC -sV <ips> -Pn -On full_scan.txt`
```

> ✅ **Uso de múltiples herramientas:** En cada fase del examen, es fundamental emplear diferentes herramientas para realizar la misma tarea. Esto ayuda a reducir la posibilidad de falsos positivos o negativos.

## ¿Qué hacemos cuando identificamos los equipos accesibles?

> Es imprescindible **documentar** cada hallazgo, incluyendo:\
> 📌 Hosts detectados\
> 📌 Credenciales obtenidas\
> 📌 Subdominios encontrados\
> 📌 Otros datos relevantes

## 🖥️ **Análisis de Hosts**

Una vez identificadas las direcciones **IP**, debemos analizarlas en detalle. Para ello, utilizaremos **Nmap** y determinaremos qué puertos están activos en cada host con el siguiente comando:

```ruby
nmap -p- --open -T5 -sS -Pn -n -vvv <ip> -oN <output_name.txt> # Con este escaneo vamos a realizar un descubrimiento de puertos de manera rápida y mostrando por pantalla unicamente los puertos que encuentre abiertos y que me escanee los 65535 puertos y exportamos los resultados.
```

> #### 📂 **Exportación del Escaneo y Análisis de Puertos**
>
> Al **exportar el escaneo**, garantizamos la posibilidad de acceder a la información en cualquier momento para su revisión. Esto facilita el análisis posterior, permitiendo consultarla con comandos como: `cat`

🔎 **Puertos más comunes que podemos encontrar:**

<figure><img src="../.gitbook/assets/carbon (1).png" alt=""><figcaption><p>Listado de los puertos mas comunes que nos podemos encontrar en el examen.</p></figcaption></figure>

## 🔍 **Análisis de Servicios y Versiones con Nmap**

Una vez que hemos identificado qué puertos están abiertos, cerrados o filtrados en una dirección IP (por ejemplo, puertos **21**, **80**, **445**, etc.), el siguiente paso es analizar qué servicios están corriendo en esos puertos y qué versiones de esos servicios están activas.

Para realizar este análisis, utilizaremos los **scripts de Nmap** que vienen por defecto. Con el siguiente comando, podremos obtener información detallada sobre los servicios y sus versiones:

```ruby
nmap -p<puertos> <ip> -sCV -oN <output_name.txt> # Con este escaneo vamos a realizar lo anteriormente dicho.
```

### 📜 **Scripts Específicos de Nmap**

Una vez que tengamos el informe de los servicios y las versiones de cada puerto, es importante tener en cuenta que **Nmap** incluye una serie de **scripts específicos** para cada puerto detectado. Estos scripts nos permiten realizar análisis más profundos y detallados, tales como:

| Puerto       | Servicio                                | Scripts NSE                                                                                                 |
| ------------ | --------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **21**       | FTP (File Transfer Protocol)            | ftp-anon, ftp-bounce, ftp-brute, ftp-syst, ftp-proftpd-backdoor                                             |
| **22**       | SSH (Secure Shell)                      | ssh-brute, ssh-auth-methods, ssh-hostkey, ssh-run, sshv1                                                    |
| **23**       | Telnet                                  | telnet-brute, telnet-encryption, telnet-ntlm-info, telnet-robot                                             |
| **25**       | SMTP (Simple Mail Transfer Protocol)    | smtp-brute, smtp-open-relay, smtp-enum-users, smtp-ntlm-info, smtp-strangeport                              |
| **53**       | DNS (Domain Name System)                | dns-nsid, dns-recursion, dns-zone-transfer, dns-service-discovery, dns-random-srcport                       |
| **80**       | HTTP (Servidor Web No Cifrado)          | http-title, http-enum, http-methods, http-robots.txt, http-shellshock, http-sql-injection, http-php-version |
| **139, 445** | SMB (Server Message Block)              | smb-enum-shares, smb-enum-users, smb-os-discovery, smb-brute, smb-vuln-ms17-010, smb-vuln-ms08-067          |
| **143**      | IMAP (Internet Message Access Protocol) | imap-brute, imap-capabilities, imap-ntlm-info                                                               |
| **443**      | HTTPS (Servidor Web Seguro)             | ssl-enum-ciphers, ssl-cert, ssl-ccs-injection, ssl-heartbleed, ssl-poodle                                   |
| **3306**     | MySQL                                   | mysql-brute, mysql-databases, mysql-empty-password, mysql-users, mysql-vuln-cve2016-6662                    |
| **3389**     | RDP (Remote Desktop Protocol)           | rdp-brute, rdp-enum-encryption, rdp-vuln-ms12-020                                                           |
| **1521**     | Oracle Database                         | oracle-brute, oracle-enum-users, oracle-tns-version, oracle-vuln-cve2012-3137                               |
| **5900**     | VNC (Virtual Network Computing)         | vnc-brute, vnc-info, vnc-title, realvnc-auth-bypass                                                         |

Dichos scripts los podríamos ejecutar mediante la siguiente sintaxis:

```ruby
nmap --script=ftp-anon -p 21 <ip_objetivo> # Utilizar script específico.
nmap --script "ftp-*" -p 21 <ip_objetivo> # Utilizar todos los scripts relacionados con el serivicio ftp.
```

#### 🔍 **Análisis Detallado de los Resultados del Escaneo**

Una vez que hemos realizado el escaneo de la red y obtenido los siguientes resultados:

1. Identificación de los equipos en la red.
2. Análisis de los puertos abiertos en las direcciones IP encontradas.
3. Evaluación de los servicios y versiones en esos puertos.

El siguiente paso es **analizar cada uno de los resultados** que nos arrojan los escaneos para determinar qué acciones tomar.

A continuación, analizamos un ejemplo específico de puerto:

***

####
