# 🔍 Fase de Enumeración

La enumeración es el proceso de establecer una conexión activa con el sistema para descubrir vectores de ataque potenciales. El objetivo es identificar servicios, versiones y configuraciones vulnerables.

---

## 🛠️ Metodología de Reconocimiento

He dividido esta fase en diferentes vectores según el objetivo:

| Técnica | Herramienta Principal | Documentación |
| :--- | :--- | :--- |
| **Escaneo de Puertos** | `Nmap` | [Comandos de Red](./comandos-de-red.md) |
| **Host Discovery** | `ARP-Scan` / `Nmap` | [Descubrimiento de Hosts](./descubrimiento-de-hosts.md) |
| **Fuzzing Web** | `Gobuster` | [Gobuster Guide](./gobuster-fuzzing-web.md) |
| **Fuzzing Avanzado** | `FFUF` | [FFUF Masterclass](./ffuf-fuzzing-web.md) |
| **Directorios Web** | `Dirbuster` | [Dirbuster Lab](./dirbuster-fuzzing-web.md) |
| **Auditoría Web** | `Nikto` | [Nikto Scanner](./nikto-escaner-web.md) |

---

## 📌 Notas de Estudio
Pro Tip: Durante la enumeración, siempre guarda los resultados en archivos de texto (-oN en Nmap) para consultarlos más tarde sin tener que repetir el escaneo.
Enumeración DNS: Comprobar siempre transferencias de zona.
Enumeración SMB: Listar recursos compartidos sin credenciales (Null Sessions).
Enumeración SNMP: Utilizar onesixtyone para encontrar comunidades públicas.

## 📽️ Comunidad y Contenido
Sigue mi progreso y contenido adicional en:

* 🎥 **YouTube** → [bitsofalber](https://www.youtube.com/@bitsofalber)
* 📸 **Instagram** → [@bitsofalber](https://www.instagram.com/bitsofalber/)
* 💼 **LinkedIn** → [ahidalgotech](https://linkedin.com/in/ahidalgotech)

---
[⬅️ Volver a Ciberseguridad](../README.md)
