Aquí tienes el archivo **README.md** completo, unificado y corregido. He eliminado las referencias contradictorias a otras provincias y lo he centrado en la estructura de datos que hemos blindado en el conversor.

---

# 🏭 Censo Electoral Sindical 2026 - FeSMC UGT CLM

Aplicación web progresiva (PWA) diseñada para la gestión, consulta y trabajo de campo del censo de empresas de cara a las elecciones sindicales 2026. 

Este sistema permite a los delegados y técnicos disponer de toda la información de las empresas de la provincia de **Ciudad Real** de forma instantánea, incluso sin conexión a internet.

---

## 📁 Estructura del Proyecto

```text
censo-cr-2026/
├── index.html        → Buscador principal y visor de tarjetas (UI)
├── datos.js          → Base de datos (JSON) generada desde el conversor
├── conversor.html    → Herramienta técnica Excel -> JavaScript
├── sw.js             → Service Worker (Soporte offline y caché)
├── manifest.json     → Configuración de instalación PWA
├── favicon.png       → Icono de la pestaña (Identidad asFeSMCUGTclm)
└── README.md         → Documentación del sistema (este archivo)
```

---

## 🚀 Funcionalidades Principales

### 🔍 Buscador y Filtros Inteligentes
* **Búsqueda Global:** Filtra por nombre de empresa, municipio o código CNAE.
* **Segmentación por Federación:** Botones rápidos para FICA, FESMC y UGT-SP con códigos de colores corporativos.
* **Estadísticas Automáticas:** Visualización del número total de empresas y suma de trabajadores según el filtro activo.

### 📲 Herramientas de Movilidad
* **WhatsApp Directo:** Botón para compartir la ficha técnica de la empresa (CIF, Dirección, CNAE, Actividad) con formato profesional y emojis.
* **Geolocalización:** Acceso a Google Maps con direcciones normalizadas.
* **Soporte Offline:** Una vez abierta la web, se puede consultar sin cobertura gracias a la tecnología PWA.

---

## 🔄 Flujo de Actualización de Datos

Para mantener el censo al día, sigue estrictamente este proceso:

1. **Preparar el Excel:** Los datos deben seguir el orden de columnas especificado abajo.
2. **Abrir el Conversor:** Ejecuta `conversor.html` en tu navegador.
3. **Procesar:** Sube el archivo `.xlsx`. El sistema limpiará las direcciones y normalizará el texto.
4. **Actualizar GitHub:** Copia el código generado, borra el contenido de `datos.js` y pega el nuevo. Haz clic en **Commit changes**.

---

## 📊 Estructura Obligatoria del Excel

El archivo de Excel **debe** empezar en la **Fila 2** (la fila 1 se ignora por ser cabecera) y respetar este orden de columnas:

| Columna | Campo | Descripción / Ejemplo |
| :--- | :--- | :--- |
| **A** | **Empresa** | Nombre o Razón Social |
| **B** | **Dirección** | Calle, Vía o Polígono (Ej: `Rdde Alarcos 28`) |
| **C** | **Localidad** | Municipio (Ej: `Alcázar de San Juan`) |
| **D** | **CP** | Código Postal |
| **E** | **Provincia** | Ciudad Real |
| **F** | **SS** | Número de la Seguridad Social |
| **G** | **CIF** | Identificador fiscal |
| **H** | **Trab.** | Cantidad de trabajadores (Número) |
| **I** | **CNAE** | Código numérico de actividad |
| **J** | **Actividad** | Descripción del sector |
| **K** | **Federación** | Siglas: `FICA`, `FESMC` o `UGT-SP` |

---

## 🛠️ Lógica de Limpieza de Datos

El **conversor.html** realiza las siguientes mejoras automáticas:
* **Normalización de Vías:** Detecta abreviaturas como `RD`, `TR`, `PJ` o `CM` y las transforma en **Ronda**, **Travesía**, **Pasaje** o **Camino**.
* **Corrección de Estilo:** Convierte textos en mayúsculas fijas a formato oración (más legible).
* **Seguridad JS:** Elimina comillas simples (`'`) para evitar errores en la base de datos.
* **Tratamiento de Bajos:** Detecta `BJ` o `BAJO` y lo unifica como "Bajo".

---

## 🌐 Despliegue (GitHub Pages)

1. Sube los archivos a tu repositorio de GitHub.
2. Ve a **Settings** > **Pages**.
3. En **Branch**, selecciona `main` y la carpeta `/(root)`.
4. La aplicación estará disponible en la URL proporcionada por GitHub (aprox. 2 minutos después del commit).

---

¿Hay algún detalle técnico adicional sobre el despliegue o el funcionamiento del Service Worker que quieras que añada?

---

¿Te parece bien este enfoque o quieres que añadamos alguna sección específica sobre los objetivos de votos o delegados?
