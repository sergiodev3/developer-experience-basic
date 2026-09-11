# Guía Práctica de PowerShell: Ejercicio y Notas Docentes

A continuación se detallan los comandos exactos que los alumnos deben ejecutar para resolver cada uno de los puntos del ejercicio práctico, así como consejos didácticos para el docente.

---

## 💻 Pasos del Ejercicio Práctico

### Paso 1: Ver ubicación actual
```powershell
pwd
```

### Paso 2: Crear carpeta principal
```powershell
mkdir Practica_PowerShell
```

### Paso 3: Entrar a la carpeta principal
```powershell
cd Practica_PowerShell
```

### Paso 4: Crear dos subcarpetas
```powershell
mkdir Documentos
mkdir Borradores
```

### Paso 5: Entrar a Documentos y crear archivo con contenido inicial
```powershell
cd Documentos
"Hola, este es mi primer archivo" > mensaje.txt
```

### Paso 6: Añadir contenido sin borrar el anterior (usando `>>`)
```powershell
"PowerShell es muy util" >> mensaje.txt
```

### Paso 7: Leer contenido del archivo
```powershell
Get-Content mensaje.txt
# (Alternativa breve: cat mensaje.txt)
```

### Paso 8: Subir de nivel a Practica_PowerShell
```powershell
cd ..
```

### Paso 9: Entrar a Borradores y crear archivo temporal
```powershell
cd Borradores
New-Item temporal.txt
```

### Paso 10: Eliminar el archivo temporal
```powershell
Remove-Item temporal.txt
# (Alternativa breve: rm temporal.txt o del temporal.txt)
```

### Paso 11: Subir de nivel a Practica_PowerShell
```powershell
cd ..
```

### Paso 12: Eliminar la carpeta vacía Borradores
```powershell
Remove-Item Borradores
# (Alternativa breve: rmdir Borradores)
```

### Paso 13: Listar contenido para verificar resultados
```powershell
ls
```

---

## 💡 Consejos y Notas Didácticas para el Docente

* **Uso de la tecla TAB:** Enfatice a los alumnos el uso de la tecla **Tabulador** al escribir rutas o nombres de carpetas. Ayuda a evitar errores ortográficos y agiliza la escritura.
* **Diferencia entre `>` y `>>`:** Asegúrese de explicar que el operador simple `>` sobreescribe todo el archivo, mientras que el operador doble `>>` agrega texto al final respetando lo existente.
* **El parámetro `-Recurse`:** Si una carpeta contiene archivos dentro y se intenta borrar con `Remove-Item`, PowerShell pedirá confirmación o lanzará un error. Explique que para borrar una carpeta no vacía se usa `Remove-Item carpeta -Recurse`.
