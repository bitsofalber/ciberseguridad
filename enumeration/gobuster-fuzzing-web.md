# 🛠️ Gobuster - Fuzzing Web

## 📂 **Fuzzing Web: Descubriendo Rutas y Subdominios Ocultos**

Cuando realizamos una auditoría en los puertos **80/443**, no solo debemos centrarnos en lo que es visible a simple vista. Existen rutas y directorios ocultos, como `/wp-login`, `/uploads`, `/robots.txt`, o `/sitemap.xml`, pero también hay muchos más que no aparecerán directamente en el código fuente.

Aquí es donde entra en juego el **Fuzzing**, una técnica que utiliza herramientas automatizadas para descubrir directorios, archivos y subdominios desconocidos en una web. Esto se hace proporcionando un diccionario con palabras clave, que la herramienta utilizará para realizar pruebas sistemáticas y reportar cualquier coincidencia.

En esta guía, exploraremos **Gobuster**, una de las herramientas más potentes para el fuzzing web.

### 🔍 **Gobuster - Enumeración y Fuzzing Web**

**Gobuster** es una herramienta de línea de comandos diseñada para descubrir directorios, subdominios y hosts virtuales en servidores web. Es rápida, eficiente y se utiliza ampliamente en pruebas de penetración.

#### 🚀 **Modos Principales de Gobuster**

| **Modo**  | **Descripción**                                          |
| --------- | -------------------------------------------------------- |
| **dir**   | Enumeración de directorios y archivos.                   |
| **dns**   | Descubrimiento de subdominios a través de consultas DNS. |
| **vhost** | Enumeración de hosts virtuales en servidores web.        |

***

### ⚙️ **Parámetros Clave en Gobuster**

| **Flag**           | **Descripción**                                                 |
| ------------------ | --------------------------------------------------------------- |
| `-u`               | URL objetivo.                                                   |
| `-w`               | Ruta del diccionario a utilizar.                                |
| `-t`               | Número de hilos en paralelo para agilizar el escaneo.           |
| `-x`               | Extensiones a buscar (Ejemplo: php, txt, html).                 |
| `-s`               | Filtrar por códigos de estado positivos.                        |
| `-k`               | Omitir la verificación SSL.                                     |
| `-b`               | Ocultar códigos de estado específicos (Ejemplo: 404, 403, 301). |
| `--exclude-length` | Excluir respuestas según su tamaño.                             |
| `-o`               | Exportar los resultados a un archivo.                           |

***

### 📚 **Wordlists Recomendados**

Para obtener mejores resultados, se recomienda utilizar wordlists optimizadas para fuzzing web.

### 📂 **Directorios y Archivos**

* `/usr/share/wordlists/dirb/common.txt`
* `/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`

### 📂 **Subdominios**

* `/usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt`

***

### 🛠️ **Ejemplos de Uso**

#### 🔹 **Modo `dir` (Enumeración de Directorios y Archivos)**

```bash
gobuster dir -u <url> -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -t <hilos>
```

#### 🔹 **Modo `dns` (Búsqueda de Subdominios)**

```bash
gobuster dns -d <url> -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```

#### 🔹 **Modo `vhost` (Descubrimiento de Virtual Hosts)**

```bash
gobuster vhost -u <url> -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -t 20
```

***

### 📌 **Consejos para una Auditoría Eficiente**

✔️ **Utiliza múltiples diccionarios** para mejorar la tasa de detección.\
✔️ **Excluye códigos de estado irrelevantes** (`-b 404,403,301`) para limpiar los resultados.
