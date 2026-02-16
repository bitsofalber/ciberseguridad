# 📍 Windows - Post-Explotación

## 🚀 WINDOWS POST EXPLOTACIÓN&#x20;

La post-explotación es una fase crítica en las pruebas de penetración que ocurre después de obtener acceso inicial a un sistema. Esta etapa es fundamental para comprender el alcance real de una vulnerabilidad y evaluar el impacto potencial en la seguridad del sistema.

### 📝 La fase de post-explotación se centra en tres objetivos principales:

* Recolección de información del sistema comprometido.
* Escalada de privilegios.
* Movimiento lateral en la red.

### 🔹 Técnicas de Reconocimiento del Sistema

### 🔍 Información del sistema

```powershell
systeminfo  # Información general del sistema
wmic os get Caption, Version, BuildNumber  # Versión del sistema operativo
hostname  # Nombre del host
dir C:\Users  # Usuarios en el sistema
```

### 🔍 Información del usuario

```powershell
whoami  # Usuario actual
whoami /priv  # Privilegios del usuario actual
net user  # Usuarios del sistema
net localgroup Administrators  # Usuarios con privilegios de administrador
```

### Si encontramos usuarios con privilegios, podemos intentar elevar privilegios usando exploits conocidos.

### 🔍 Explotación del Kernel

```powershell
systeminfo | findstr /B /C:"OS Version"  # Verificar versión del sistema operativo
wmic qfe get HotFixID  # Listar parches instalados
```

Consultar la siguiente web para exploits conocidos: [https://www.exploit-db.com/](https://www.exploit-db.com/)

### 🔍 Búsqueda de Credenciales

```powershell
findstr /si password *.txt *.ini *.config  # Buscar contraseñas en archivos de configuración
reg query HKLM /f password /t REG_SZ /s  # Buscar credenciales en el registro
```

### 🔍 Análisis de Historial

```powershell
type C:\Users\<usuario>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt  # Historial de comandos de PowerShell
type C:\Users\<usuario>\ntuser.dat.LOG1  # Registro de actividad del usuario
```

### 🔍 Buscar Claves SSH

```powershell
dir /s /b C:\Users\*.ssh\id_rsa  # Buscar claves privadas SSH
dir /s /b C:\Users\*.ssh\authorized_keys  # Claves autorizadas
```

### 🔍 Configuraciones SUID/SGID (Equivalente a Windows: Archivos con permisos elevados)

```powershell
icacls C:\Windows\System32  # Ver permisos de archivos del sistema
icacls C:\Users\<usuario> /grant Everyone:F  # Modificar permisos (requiere privilegios elevados)
```

### 🔍 Tareas Programadas

```powershell
schtasks /query /fo LIST /v  # Listar tareas programadas
dir C:\Windows\Tasks  # Ver tareas programadas manualmente
dir C:\Windows\System32\Tasks  # Tareas programadas por el sistema
```

### 🔍 Servicios y Configuraciones Sensibles

```powershell
wmic service list brief  # Listar servicios en ejecución
net start  # Ver servicios iniciados
Get-WmiObject Win32_Service | Select-Object Name, StartName  # Ver servicios con cuentas privilegiadas
```

### 🔍 Configuración de Red y Conexiones

```powershell
ipconfig /all  # Configuración de red
netstat -ano  # Conexiones activas y procesos asociados
arp -a  # Tabla ARP
route print  # Tabla de enrutamiento
```

### 🔍 Archivos y Directorios Sensibles

```powershell
dir /s /b C:\Users\*\AppData\Roaming\Microsoft\Windows\Recent  # Archivos recientes
dir /s /b C:\Users\*\Documents\  # Documentos del usuario
dir /s /b C:\Users\*\Desktop\  # Escritorio de los usuarios
dir /s /b C:\Windows\System32\config  # Archivos de configuración
```

### 🔍 Archivos de Configuración de Tareas Programadas

```powershell
dir /s /b C:\Windows\System32\Tasks  # Listar tareas programadas
dir /s /b C:\Windows\Tasks  # Listar tareas ocultas
```

<figure><img src="../.gitbook/assets/DALL·E 2025-02-17 10.40.59 - A hacker wearing a dark hoodie and a mask, sitting in front of multiple computer screens filled with code and security warnings. The hacker is holding.webp" alt="" width="563"><figcaption></figcaption></figure>
