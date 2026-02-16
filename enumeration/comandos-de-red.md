# 🌐 Comandos de Red

### Una recopilación de comandos esenciales para gestionar y diagnosticar redes en **Linux, Windows y macOS**.

***

### 🚏 **1. Routing - Tabla de Enrutamiento**

| **Sistema Operativo**   | **Comando**   |
| ----------------------- | ------------- |
| 🐧 **Linux**            | `ip route`    |
| 🖥️ **Windows**         | `route print` |
| 🍏 **Mac OS X / Linux** | `netstat -r`  |

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

### 📌 **Descripción:** Estos comandos muestran la tabla de enrutamiento de la red, permitiendo identificar cómo se dirigen los paquetes.

***

### 📡 **2. IP - Información de Interfaces de Red**

| **Sistema Operativo**   | **Comando**                                          |
| ----------------------- | ---------------------------------------------------- |
| 🐧 **Linux**            | <p><code>ip a</code><br><code>ip -br -c a</code></p> |
| 🖥️ **Windows**         | `ipconfig /all`                                      |
| 🍏 **Mac OS X / Linux** | `ifconfig`                                           |

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption><p>Posible sálida del comando <code>ip -a</code></p></figcaption></figure>

### 📌 **Descripción:** Muestra información detallada sobre las interfaces de red, direcciones IP asignadas y configuraciones activas.
