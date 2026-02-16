# 🛠️ Nikto - Escaner Web

## ![](<../.gitbook/assets/DALL·E 2025-02-22 08.21.05 - A high-tech cybersecurity-themed image featuring the Nikto tool. The image showcases a hacker-style computer screen with lines of code scanning for vu.webp>)

## **🛠️ Nikto - Escaneo de Vulnerabilidades Web**

Nikto es una herramienta diseñada específicamente para este propósito: escanear servidores web en busca de vulnerabilidades conocidas, configuraciones incorrectas y archivos peligrosos. En esta guía, aprenderemos a utilizar Nikto de manera efectiva para auditar la seguridad de un servidor web.

### **🔍 Nikto - Introducción y Modos de Uso:**

Nikto es un escáner de vulnerabilidades de servidores web que realiza pruebas rápidas y automatizadas. A diferencia de herramientas como Burp Suite o Nessus, Nikto se especializa en detectar configuraciones incorrectas, versiones desactualizadas de software y archivos públicamente accesibles.

### **🎡 Características Clave de Nikto**

| Opción      | Descripción                                                        |
| ----------- | ------------------------------------------------------------------ |
| Target Host | URL o IP del servidor a analizar.                                  |
| Port        | Puerto en el que escucha el servidor (por defecto, 80 o 443).      |
| SSL/TLS     | Habilita el escaneo sobre HTTPS.                                   |
| User-Agent  | Personaliza la cabecera del agente de usuario.                     |
| Output      | Guarda los resultados en un archivo.                               |
| Timeout     | Define un límite de tiempo para cada solicitud.                    |
| Throttling  | Controla la velocidad de las peticiones para evitar ser bloqueado. |

### **📚 Diccionarios y Firmas Utilizadas**

Nikto utiliza una base de datos con miles de pruebas para detectar vulnerabilidades comunes. Algunas de las firmas que emplea incluyen:

* Detectar versiones de software desactualizadas (Apache, Nginx, IIS, etc.).
* Identificar archivos de configuración expuestos (robots.txt, .htaccess, phpinfo.php).
* Analizar cabeceras HTTP en busca de configuraciones inseguras.

### **🛠️ ¿Cómo utilizar Nikto?**

```bash
nikto -h <url> # Escaneo simple con Nikto.
nikto -h <url> -p 443 # Si el servidor usa un puerto diferente al 80 o queremos analizar HTTPS:
nikto -h <url> -useragent "Mozilla/5.0 (Windows NT 10.0; Win64; x64)" # Evitar la Detección Modificando el User-Agent
nikto -h <url> -tuning -<número> # Excluir Ciertos Tipos de Pruebas, (-2=evita pruebas de archivos peligrosos.) (-4=evita pruebas de inyección SQL.) (-6=evita pruebas de XSS.)
nikto -h <url> -delay 2 # Controlar la Velocidad del Escaneo
```
