# 🛠️ Dirbuster - Fuzzing Web

## 🚀 **Fuzzing Web con DirBuster: Descubrimiento de Directorios y Archivos Ocultos**

Cuando realizamos pruebas de penetración en aplicaciones web, no basta con analizar lo que es visible en la interfaz. Muchos directorios y archivos importantes no aparecen en la estructura pública del sitio, pero siguen siendo accesibles si sabemos cómo buscarlos.

**DirBuster** es una herramienta diseñada específicamente para este propósito: buscar directorios y archivos ocultos en servidores web mediante ataques de fuerza bruta basados en diccionarios. En esta guía, aprenderemos a utilizar **DirBuster** de manera efectiva para descubrir rutas sensibles y posibles puntos de entrada en una auditoría web.

***

### 🔍 **DirBuster - Introducción y Modos de Uso**

**DirBuster** es una herramienta basada en Java, creada por **OWASP**, que permite la exploración de directorios y archivos ocultos en servidores web. A diferencia de otras herramientas como **Gobuster** o **FFUF**, **DirBuster** tiene una interfaz gráfica y permite realizar búsquedas tanto con listas predefinidas como con ataques de fuerza bruta generados dinámicamente.



***

### ⚙️ **Parámetros Clave en DirBuster**

| **Opción**                | **Descripción**                                                    |
| ------------------------- | ------------------------------------------------------------------ |
| `Target URL`              | URL del sitio web objetivo.                                        |
| `Wordlist`                | Diccionario de nombres de directorios y archivos a buscar.         |
| `Number of Threads`       | Número de hilos en paralelo para optimizar el escaneo.             |
| `File Extension`          | Extensiones específicas a buscar (Ejemplo: php, txt, html).        |
| `Go Faster`               | Acelera la búsqueda con técnicas de optimización.                  |
| `Follow Redirects`        | Permite seguir redirecciones HTTP automáticamente.                 |
| `Stop if too many errors` | Detiene el escaneo si el servidor responde con demasiados errores. |

***

### 📚 **Wordlists Recomendadas**

📂 **Directorios y Archivos**

* `/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt`
* `/usr/share/wordlists/dirb/common.txt`

📂 **Archivos Sensibles**

* `/usr/share/wordlists/dirbuster/directory-list-2.3-small.txt`

***

### 🛠️ **Ejemplos de Uso**

#### 🔹 **Escaneo de Directorios y Archivos con Interfaz Gráfica**

1️⃣ Abre **DirBuster** desde la terminal:

```bash
java -jar DirBuster.jar
```

2️⃣ Ingresa la **URL objetivo** en el campo "Target URL".\
3️⃣ Selecciona la **wordlist** (`directory-list-2.3-medium.txt`).\
4️⃣ Define el número de **hilos** (recomendado: **50-100** para velocidad óptima).\
5️⃣ Si deseas buscar archivos con extensiones específicas, agrégalas en "File Extension" (Ejemplo: `php, txt, html`).\
6️⃣ Haz clic en **Start** para comenzar el escaneo.

***

#### 🔹 **Modo de Línea de Comandos (CLI)**

Si prefieres trabajar sin interfaz gráfica, **DirBuster** también permite ejecutar escaneos desde la terminal:

```bash
dirbuster -u <url> -l <ruta_diccionario.txt> -t 50 -e php,txt,html -o resultado.txt
```

📌 **Explicación:**\
✔ `-u <url>` → Define la URL objetivo.\
✔ `-l <diccionario>` → Indica el diccionario a utilizar.\
✔ `-t 50` → Usa 50 hilos para mayor velocidad.\
✔ `-e php,txt,html` → Busca archivos con extensiones específicas.\
✔ `-o resultado.txt` → Guarda los resultados en un archivo.

***

#### 🔹 **Filtrado de Respuestas Irrelevantes**

Para evitar respuestas con códigos de estado no útiles como **403 (Prohibido)** o **404 (No encontrado)**, podemos agregar filtros en la interfaz gráfica o línea de comandos:

```bash
dirbuster -u <url> -l <ruta_diccionario.txt> -t 50 -e php,txt,html -o resultado.txt --exclude-status 403,404
```

### 📌 **Explicación:**

\
✔ `--exclude-status 403,404` → Oculta respuestas con códigos **403** y **404**.

***
