---
description: >-
  Un hotfix es una actualización de software diseñada para corregir errores
  críticos, fallos de seguridad o problemas urgentes en un sistema sin necesidad
  de esperar una actualización mayor.
---

# ⚙️ HotFixed

💡 Puede ser que durante el examen veais que hay una pregunta que con mencionan que debeís introducir algún dato relacionado con los HotFixed

## Comandos para encontrar HotFixes en Windows

Existen dos métodos principales para encontrar los HotFixes instalados en un sistema Windows:

### 1. Usando PowerShell

```powershell
Get-HotFix # Ver todos los HotFixes instalados
Get-HotFix.count # # Contar el número total de HotFixes
Get-HotFix | Sort-Object -Property InstalledOn -Descending # Ordenar por fecha de instalación
Get-HotFix -Id KB4577586 # Buscar un HotFix específico (ejemplo: KB4577586)
```

### 2. Usando WMIC (Windows Management Instrumentation Command-line)

```powershell
REM Ver lista de HotFixes en formato tabla
wmic qfe list brief /format:table

REM Ver información detallada
wmic qfe list full
```

💡 Tip: El comando PowerShell es más moderno y ofrece mejor formato de salida, mientras que WMIC es compatible con versiones más antiguas de Windows.
