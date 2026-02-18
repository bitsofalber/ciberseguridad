# 🔑 Escalada de Privilegios (PrivEsc)

Esta fase se centra en elevar los privilegios de una cuenta de usuario con acceso limitado a un nivel superior (como `root` en Linux o `SYSTEM` en Windows). Es un paso crítico para obtener el control total sobre el sistema comprometido.

---

## 📂 Metodologías por Sistema Operativo

He dividido los recursos de escalada según el entorno objetivo para facilitar la consulta rápida:

| Sistema | Descripción Técnica | Documentación |
| :--- | :--- | :--- |
| 🐧 **Linux** | Explotación de SUID, Kernel, tareas Cron y archivos de configuración. | [Ver Notas](./linux.md) |
| 🪟 **Windows** | Análisis de permisos de servicios, DLL Hijacking y vulnerabilidades de Kernel. | [Ver Notas](./windows.md) |

---

## 📌 Objetivos del Privilege Escalation

* **Enumeración Local:** Identificar configuraciones erróneas y parches de seguridad faltantes.
* **Elevación Vertical:** Pasar de un usuario estándar a un administrador o superusuario.
* **Elevación Horizontal:** Acceder a otras cuentas de usuario con el mismo nivel de privilegios pero con información diferente.
* **Explotación de Vectores:** Uso de herramientas de automatización y scripts manuales para detectar debilidades.

---

## 📽️ Comunidad y Contenido
Puedes seguir mi progreso y contenido adicional en:

* 🎥 **YouTube** → [bitsofalber](https://www.youtube.com/@bitsofalber)
* 📸 **Instagram** → [@bitsofalber](https://www.instagram.com/bitsofalber/)
* 💼 **LinkedIn** → [ahidalgotech](https://linkedin.com/in/ahidalgotech)

---
[⬅️ Volver a Ciberseguridad](../README.md)
