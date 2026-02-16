# 🛠️ Ffuf - Fuzzing Web

## 🚀 **Fuzzing Web con FFUF: Descubrimiento de Directorios y Subdominios**

Cuando realizamos auditorías en aplicaciones web, no siempre es suficiente analizar lo visible. Existen rutas, directorios y subdominios ocultos que pueden contener información sensible o puntos de entrada vulnerables.

Para descubrir estos elementos ocultos, utilizamos **fuzzing**, una técnica que emplea diccionarios para probar múltiples combinaciones y detectar recursos expuestos. En esta guía, aprenderemos a utilizar **FFUF (Fuzz Faster U Fool)**, una de las herramientas más rápidas y eficientes para esta tarea.

***

### 🔍 **FFUF - Introducción y Modos de Uso**

**FFUF** es una herramienta de fuzzing de código abierto, desarrollada para realizar búsquedas de directorios, archivos y subdominios en servidores web de manera rápida y eficiente.

#### 🚀 **Modos Principales de FFUF**

| **Modo**  | **Descripción**                                        |
| --------- | ------------------------------------------------------ |
| **DIR**   | Enumeración de directorios y archivos web.             |
| **DNS**   | Descubrimiento de subdominios mediante fuzzing de DNS. |
| **VHOST** | Enumeración de hosts virtuales en servidores web.      |

***

### ⚙️ **Parámetros Clave en FFUF**

| **Flag**      | **Descripción**                                            |
| ------------- | ---------------------------------------------------------- |
| `-u`          | URL objetivo donde se realizará el fuzzing.                |
| `-w`          | Ruta del diccionario a utilizar.                           |
| `-t`          | Número de hilos en paralelo para agilizar el escaneo.      |
| `-e`          | Extensiones a buscar (Ejemplo: php, txt, html).            |
| `-fc`         | Filtrar por códigos de estado (Ejemplo: 403, 404, 301).    |
| `-fs`         | Excluir respuestas según su tamaño en bytes.               |
| `-mc`         | Mostrar solo respuestas con códigos de estado específicos. |
| `-o`          | Exportar resultados a un archivo (json, csv, txt).         |
| `--recursion` | Activar escaneo recursivo en directorios descubiertos.     |

***

### 📚 **Wordlists Recomendadas**

📂 **Directorios y Archivos**

* `/usr/share/wordlists/dirb/common.txt`
* `/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`

📂 **Subdominios**

* `/usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt`

***

### 🛠️ **Ejemplos de Uso**

#### 🔹 **Modo `dir` (Enumeración de Directorios y Archivos)**

```bash
ffuf -u <url>/FUZZ -w <ruta_diccionario.txt> -t 50 -fc 404,403,301
```

📌 **Explicación:**\
✔ `-u http://<url>/FUZZ` → Reemplaza `FUZZ` con cada palabra del diccionario.\
✔ `-w /usr/share/wordlists/...` → Diccionario utilizado.\
✔ `-t 50` → Ejecuta el escaneo con 50 hilos en paralelo.\
✔ `-fc 404,403,301` → Excluye respuestas con esos códigos de estado.

***

#### 🔹 **Modo `dns` (Búsqueda de Subdominios)**

```bash
ffuf -u <url> -w <ruta_diccionario.txt> -t 50 -mc 200
```

📌 **Explicación:**\
✔ `FUZZ.example.com` → Se reemplaza `FUZZ` con palabras del diccionario para buscar subdominios.\
✔ `-mc 200` → Muestra solo respuestas con código **200** (OK).

***

#### 🔹 **Modo `vhost` (Descubrimiento de Virtual Hosts)**

```bash
ffuf -u <url> -H "Host: FUZZ.<url>" -w <ruta_diccionario.txt> -t 50 -mc 200
```

📌 **Explicación:**\
✔ `-H "Host: FUZZ.example.com"` → Modifica el encabezado **Host** para probar diferentes nombres de host.\
✔ `-mc 200` → Muestra solo respuestas con código **200** (OK).

***

### 🎯 **Filtrado Avanzado de Resultados**

Para mejorar la precisión del escaneo, podemos aplicar filtros avanzados:

#### **🔹 Ocultar respuestas con códigos de estado específicos**

```bash
ffuf -u <url>/FUZZ -w <ruta_diccionario.txt> -fc 404,403,301
```

#### **🔹 Excluir respuestas por tamaño**

```bash
ffuf -u <url>/FUZZ -w <ruta_diccionario.txt> -fs 1234
```

📌 **Explicación:**\
✔ `-fs 1234` → Excluye respuestas de **1234 bytes** de tamaño.

***

### 📌 **Consejos para un Escaneo Eficiente**

✔ **Utiliza wordlists específicas** para cada tipo de prueba.\
✔ **Ajusta los hilos (`-t`)** según el rendimiento del servidor.\
✔ **Filtra resultados irrelevantes** (`-fc`, `-fs`, `-mc`).\
✔ **Prueba con diferentes herramientas**, como `gobuster` o `dirbuster`, para comparar resultados.
