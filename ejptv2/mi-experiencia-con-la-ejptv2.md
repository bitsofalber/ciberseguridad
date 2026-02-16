# 🔰 Mi experiencia con la eJPTv2

## ✅ <mark style="color:red;">Mi experiencia con la certificación eJPTv2 + TIPS clave para aprobarla en 2025</mark>

## ¡Hola a todos!

Después de mucho esfuerzo y dedicación, he conseguido aprobar la certificación **eJPTv2** en este 2025. Quiero compartir mi experiencia completa, desde cómo me preparé, qué estudié, cómo fue el examen y algunos **TIPS clave** que te pueden ayudar a conseguirlo tú también.

Aquí te dejo toda la información organizada por secciones:

***

## 🔍 <mark style="color:green;">¿Qué es la certificación eJPTv2?</mark>

La **eJPTv2 (eLearnSecurity Junior Penetration Tester)** es una de las mejores certificaciones para quienes quieren iniciarse en el mundo del **hacking ético** y el **pentesting**.

Ofrecida por **INE Security**, es una certificación **práctica**, en la que no solo necesitas conocimientos teóricos, sino que debes demostrar habilidades en escenarios reales.

💰 **Precio**: entre **200$ y 250$**, aunque suelen lanzar **descuentos** en fechas clave como **Navidad** o **Black Friday**.

***

## 📚 <mark style="color:green;">¿Qué nivel es necesario antes de presentarte?</mark>

Esta es una de las preguntas más comunes:

### **¿Cuánto hay que saber antes de presentarse?**

La respuesta es: **depende de ti y de cómo te sientas de preparado.**

Si puedes resolver máquinas de nivel **fácil** en plataformas como HackTheBox o TryHackMe, dominas conceptos básicos de ciberseguridad, comprendes los CMS más comunes y sus vectores de ataque, y tienes clara la metodología de un pentest, es probable que ya estés cerca de estar listo.

En mi caso, al tener poco tiempo libre por el trabajo, me llevó alrededor de **1 año** prepararme. Sin embargo, cada persona es un mundo: hay quien lo consigue en 2 meses y otros que necesitan 4 intentos. **Tu ritmo es el correcto.**

### 🔔 **Dato personal:**

Empecé desde cero en ciberseguridad a los **31 años**. Nunca es tarde si te apasiona este mundo y disfrutas entendiendo cómo funcionan las cosas por dentro.

***

## <mark style="color:green;">🧩 ¿Cómo es el examen? ¿Qué te vas a encontrar?</mark>

El examen es **browser-based**, es decir, se hace completamente desde el navegador. Todo lo necesario está **integrado** en el laboratorio virtual que te proporcionan.

### 🔒 **Restricciones importantes:**

* No puedes **subir scripts propios**.
* No podrás usar herramientas como **LinPEAS**.
* No se permite **pivoting** externo (con chisel, por ejemplo). Tendrás que realizar el pivoting usando solo lo que ofrece el entorno.

### 📌 **Estructura:**

* 37 **preguntas** relacionadas con la máquina.
* 48 horas para realizar el examen.
* Algunas son de **selección múltiple**, otras consisten en capturar **flags**, o proporcionar **contraseñas**.

### ⚠️ **Incidencias habituales:**

Puede que tengas que **reiniciar** la máquina varias veces por fallos técnicos.

### 🔑 **Clave del examen:**

La **enumeración** es fundamental. Sin una buena enumeración de **hosts, puertos, servicios y CMS**, estarás perdido.

### 💡 **Recuerda:**

No es un **CTF** tradicional. No busques soluciones rebuscadas o creativas. Se trata de aplicar **metodología real** de pentesting.

***

### 🔥 Dificultades que me encontré

### 📌 **Ganar acceso inicial**:

Es clave conocer **diferentes métodos de explotación**, desde:

* Payloads de **msfvenom**.
* One-liners de **bash**.
* Ejecuciones remotas en archivos **PHP**.

## 🚨 <mark style="color:green;">**No te desesperes si algo no funciona a la primera.**</mark> <mark style="color:green;"></mark><mark style="color:green;">Mantén la calma y sigue intentando.</mark>

### 🐇 **Rabbit Holes:**

En más de una ocasión perdí tiempo en caminos erróneos por pensar que era más difícil de lo que realmente era. **Simplifica.**

***

## <mark style="color:green;">🛠️ Herramientas clave para el examen</mark>

* 🔹 **Nmap** – Enumeración de hosts, puertos y servicios (y scripts NSE).
* 🔹 **Metasploit** – Indispensable para explotación y pivoting.
* 🔹 **dirb** / **wfuzz** – Para descubrir directorios ocultos.
* 🔹 **CrackMapExec, smbmap y smbclient** – Exploración de recursos compartidos.
* 🔹 **FTP** y **SSH** – Acceso, subida y descarga de archivos.
* 🔹 **Hydra** – Ataques de fuerza bruta.
* 🔹 **msfvenom** – Creación de payloads.
* 🔹 **JohnTheRipper** – Cracking de hashes e **id\_rsa**.
* 🔹 **searchsploit** – Búsqueda rápida de exploits.

📌 **TIP:** Aprende varias herramientas para cada tarea, por si alguna falla.

***

## 📅 <mark style="color:green;">Mi preparación y recursos</mark>

#### 🔹 Formación autodidacta:

✅ Videos, blogs y contenido de:

* [El Pingüino de Mario](https://www.youtube.com/@ElPinguinoDeMario)
* [ZunderRub](https://www.youtube.com/@zunderrub)
* [Hackavis](https://www.youtube.com/@Hackavis)
* [Xerosec](https://www.youtube.com/@xerosec)
* [S4vitar](https://www.youtube.com/@s4vitar)
* [RinkuTech](https://www.youtube.com/@rinkutech_)

#### 🔹 Plataformas prácticas:

* [DockerLabs](https://www.dockerlabs.es/#/)
* [The Hackers Labs](https://thehackerslabs.com/)
* [HackTheBox](https://www.hackthebox.com/)
* [TryHackMe](https://tryhackme.com/)
* [VulnHub](https://www.vulnhub.com/)

#### 🔹 Formación adicional:

* **INE Security** – Los cursos oficiales de eJPTv2 (en inglés) son muy completos.
* **Programa de Pablo Rinku** – Me ayudó a afianzar metodología y conceptos.

## 🔹 <mark style="color:green;">Creación de contenido propio:</mark>

* [YouTube Henkosec](https://www.youtube.com/@henkosec)
* [GitBook Henkosec Wiki](https://henkosec.gitbook.io/henkosec/ejptv2wiki)
* [Instagram Henkosec](https://www.instagram.com/henkosec/)

***

## <mark style="color:green;">🕒 Organización del tiempo de estudio</mark>

📌 **Clave:** Organización y constancia.

1️⃣ Elige un tema (ej. Auditoría WordPress). 2️⃣ Estudia teoría, herramientas y metodología. 3️⃣ Toma **buenos apuntes**. 4️⃣ Ponlo en práctica con máquinas reales.

🔁 **Repite el proceso con cada concepto clave.**

***

## <mark style="color:green;">✅ Conocimientos cubiertos en eJPTv2</mark>

* 🖥️ **Linux y Windows básico.**
* 📊 **Metodologías de hacking ético.**
* 🌐 **Fundamentos de redes.**
* 🔎 **Escaneo y análisis de redes y servicios.**
* 🔓 **Explotación de vulnerabilidades comunes.**
* 🪜 **Escalada de privilegios y pivoting.**
* 🔐 **Cracking de hashes y contraseñas.**
* 🛠️ **Uso de herramientas manuales y automatizadas.**

***

### 💡 <mark style="color:green;">TIPS clave para el examen</mark>

* 📔 Prepara **apuntes sólidos**.
* 📝 Toma notas durante el examen (hosts, puertos, credenciales, etc.).
* 🗺️ Haz un mapa visual de la red (usa [Draw.io](https://app.diagrams.net/)).
* 🧩 Usa herramientas como **CherryTree**, **Obsidian** o **Notion**.
* 🔁 Usa diferentes herramientas para validar resultados.

⚠️ Y fuera del examen:

* 🛌 Duerme bien la noche anterior.
* ☕ Café y mente despejada.
* 🧘‍♂️ Descansa si te bloqueas.
* 💪 Confía en ti mismo.

***

### 🎯 <mark style="color:green;">Conclusión</mark>

📚 **Estudia mucho.**

🛠️ **Practica sin parar.**

📔 **Toma buenos apuntes.**

💪 **Confía en ti mismo.**

🔐 **Con trabajo y constancia, lo conseguirás.**



<figure><img src="../.gitbook/assets/1_hf2Yba0ZGG15JHpMA-lbZw.png" alt=""><figcaption></figcaption></figure>

