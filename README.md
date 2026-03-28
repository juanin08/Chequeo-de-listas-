# Chequeo-de-listas-
Chqueo  de listas en base appsheets
📦 CheckList Bolsas — AppSheet + Google Sheets
> **Español** | [English below](#-checklist-bolsas--appsheet--google-sheets-1)
---
📋 Descripción
Sistema de control de despacho desarrollado con AppSheet y Google Sheets, orientado a agilizar la verificación de bolsas en un entorno farmacéutico. Permite registrar en tiempo real qué bolsas han sido chequeadas, identificar las pendientes y visualizar el estado general del proceso mediante un semáforo visual.
Este proyecto forma parte del portafolio académico de herramientas no-code/low-code aplicadas a la gestión operacional en salud.
---
🎯 Problema que resuelve
En el área de despacho de una farmacia, cada bolsa lleva asociado el nombre de un paciente. El proceso de verificación manual era propenso a errores, omisiones y pérdida de tiempo. Esta app digitaliza y agiliza ese proceso directamente desde el teléfono móvil.
---
⚙️ Tecnologías utilizadas
Herramienta	Uso
Google Sheets	Base de datos (lista oficial de nombres y registro de chequeos)
AppSheet	Interfaz móvil no-code
openpyxl (Python)	Generación de la planilla base con formato profesional
---
🗂️ Estructura del proyecto
```
CheckList_Bolsas/
│
├── CheckList_Bolsas.xlsx     # Planilla base con hojas Nombres y Registros
└── README.md                 # Documentación del proyecto
```
Hojas de Google Sheets
`Nombres` — Lista oficial de pacientes (solo lectura desde la app)
`Registros` — Registro automático de cada bolsa chequeada (ID único + Nombre)
---
📱 Funcionalidades de la app
Vista	Función
🔲 Chequear Bolsas	Formulario con buscador predictivo por nombre
📋 Historial	Lista de todas las bolsas ya chequeadas
⏳ Pendientes	Solo muestra los nombres que aún no han sido chequeados
🔴🟢 Todos	Vista completa con semáforo visual (chequeado/pendiente)
---
🔧 Lógica de configuración en AppSheet
Tabla `Nombres`
Columna `Nombre` → tipo Text, configurada como Label
Columna `Chequeado` → tipo Yes/No, calculada con fórmula:
```
  IN([Nombre], Registros[Nombre])
  ```
Permisos: solo lectura (Add/Edit/Delete desactivados)
Tabla `Registros`
Columna `ID` → tipo Text, Key, generada automáticamente con:
```
  UNIQUEID()
  ```
Columna `Nombre` → tipo Ref apuntando a tabla `Nombres`
Validación de duplicados con:
```
  COUNT(SELECT(Registros[Nombre], [Nombre] = [_THISROW].[Nombre])) <= 1
  ```
Slice `Slice_Pendientes`
Filtra la tabla `Nombres` mostrando solo los no chequeados:
```
  NOT(IN([Nombre], Registros[Nombre]))
  ```
---
🚀 Cómo replicar este proyecto
Descarga el archivo `CheckList_Bolsas.xlsx`
Súbelo a Google Drive
Reemplaza los nombres de ejemplo en la hoja `Nombres` con los datos reales
Entra a appsheet.com → Make a new app → Start with your own data
Conecta el archivo desde Google Drive
Configura las tablas, columnas y vistas según la documentación de este README
Publica la app y accede desde el teléfono móvil
---
👤 Autor
Juan Luis — Geólogo | Analista de Datos  
Certificación: IBM Data Science Professional Certificate
---
---
📦 CheckList Bolsas — AppSheet + Google Sheets
> **English** | [Español arriba](#-checklist-bolsas--appsheet--google-sheets)
---
📋 Description
A dispatch control system built with AppSheet and Google Sheets, designed to streamline bag verification in a pharmacy setting. It enables real-time tracking of which bags have been checked, highlights pending ones, and provides a visual status overview through color-coded indicators.
This project is part of an academic portfolio focused on no-code/low-code tools applied to operational management in healthcare.
---
🎯 Problem it solves
In a pharmacy dispatch area, each bag is associated with a patient's name. The manual verification process was error-prone, subject to omissions, and time-consuming. This app digitizes and streamlines that process directly from a mobile phone.
---
⚙️ Technologies used
Tool	Purpose
Google Sheets	Database (official name list and check-in records)
AppSheet	No-code mobile interface
openpyxl (Python)	Base spreadsheet generation with professional formatting
---
🗂️ Project structure
```
CheckList_Bolsas/
│
├── CheckList_Bolsas.xlsx     # Base spreadsheet with Nombres and Registros sheets
└── README.md                 # Project documentation
```
Google Sheets tabs
`Nombres` — Official patient list (read-only from the app)
`Registros` — Automatic log of each checked bag (unique ID + Name)
---
📱 App features
View	Purpose
🔲 Chequear Bolsas	Form with predictive search by name
📋 Historial	List of all already-checked bags
⏳ Pendientes	Shows only names not yet checked
🔴🟢 Todos	Full list with visual traffic light (checked/pending)
---
🔧 AppSheet configuration logic
`Nombres` table
`Nombre` column → Text type, set as Label
`Chequeado` column → Yes/No type, calculated with:
```
  IN([Nombre], Registros[Nombre])
  ```
Permissions: read-only (Add/Edit/Delete disabled)
`Registros` table
`ID` column → Text type, Key, auto-generated with:
```
  UNIQUEID()
  ```
`Nombre` column → Ref type pointing to `Nombres` table
Duplicate validation:
```
  COUNT(SELECT(Registros[Nombre], [Nombre] = [_THISROW].[Nombre])) <= 1
  ```
`Slice_Pendientes` slice
Filters `Nombres` table to show only unchecked entries:
```
  NOT(IN([Nombre], Registros[Nombre]))
  ```
---
🚀 How to replicate this project
Download the `CheckList_Bolsas.xlsx` file
Upload it to Google Drive
Replace the sample names in the `Nombres` sheet with real data
Go to appsheet.com → Make a new app → Start with your own data
Connect the file from Google Drive
Configure tables, columns and views following this README
Publish the app and access it from your mobile phone
---
👤 Author
Juan Luis — Geologist | Data Analyst  
Certification: IBM Data Science Professional Certificate
