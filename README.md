# Estrategia Comercial Inmobiliaria – Andes Capital Real Estate | Sprint 11

Este repositorio contiene el proyecto de visualización desarrollado durante el Sprint 10 para **Andes Capital Real Estate**, empresa inmobiliaria que gestiona la venta de propiedades a través de distintos canales y segmentos de clientes.

El modelo de datos integra una tabla de hechos de ventas con tres tablas dimensionales (clientes, propiedades y calendario), estructuradas en **esquema estrella**, para analizar **8,500 transacciones** y **$6,012 millones** en ingresos durante el período 2023–2024.

---

## 📂 Contenido del repositorio

- `notebooks/S11_Proyecto_InmobiliarioGrupoAndes.ipynb`
  → Notebook de planificación y documentación: limpieza de datos, modelado, medidas DAX, diseño del dashboard y resumen ejecutivo.

- `data/hecho_ventas_propiedades.xlsx`
  → Tabla de hechos con las transacciones de venta: precio, comisión, canal, cliente y propiedad.

- `data/dim_clientes.xlsx`
  → Dimensión de clientes: segmento de comprador, país y ciudad.

- `data/dim_propiedades.xlsx`
  → Dimensión de propiedades: tipo, categoría, barrio, habitaciones, tamaño y precio publicado.

- `dashboard/Proyecto_Sprint_11.pbix`
  → Archivo de Power BI con el modelo de datos en esquema estrella, medidas DAX y las tres vistas del dashboard (Overview Ejecutivo, Análisis Comercial y Análisis de Cohortes).

- `assets/overview_ejecutivo.png`
  → Captura de la vista Overview Ejecutivo con KPIs, evolución temporal e ingreso por ciudad.

- `assets/analisis_comercial.png`
  → Captura de la vista Análisis Comercial con ingreso por tipo de propiedad, canal de venta y segmento de comprador.

- `assets/analisis_cohortes.png`
  → Captura de la vista Análisis de Cohortes con matriz de retención e ingreso total por cohorte mensual.

- `assets/modelo_datos.png`
  → Captura del esquema estrella con las relaciones entre tablas en Power BI.

---

## 📊 Estructura del Dashboard

El dashboard está compuesto por **3 pestañas navegables** con botones de acceso entre vistas:

**1️⃣ Overview Ejecutivo**
Vista de alto nivel con 5 KPIs principales: Ingreso Total ($6,01 mil M), Cantidad de Ventas (9 mil), Ticket Promedio ($707,35 mil), Comisión Total ($200,63 mill.) y Crecimiento YoY (11,14%). Incluye gráfico de barras de ingreso por ciudad, gráfico de líneas con Ingreso Total, Ventas YTD, Ventas MTD y Ventas YTD Año Anterior, y gráfico de serie temporal mensual con líneas de referencia (máximo, promedio y mínimo). Filtro por Año.

**2️⃣ Análisis Comercial**
Análisis de ingreso por tipo de propiedad, canal de venta y segmento de comprador mediante gráficos de barras. Incluye tabla con formato condicional que muestra Ingreso Total, Cantidad de Ventas y Ticket Promedio por tipo de propiedad (Casa, Comercial, Departamento).

**3️⃣ Análisis de Cohortes**
Dos matrices: **Porcentaje de retención** (tasa de recompra por cohorte mensual desde 2023-01) y **Matriz de Ingreso Total** por cohorte y mes de venta, con formato de calor para identificar patrones de recurrencia.

---

## 🧩 Modelo de datos

Esquema estrella con las siguientes tablas y relaciones (cardinalidad 1:*, filtro simple):

- `hecho_ventas_propiedades` → tabla central de hechos
- `dim_propiedades` → relacionada por `id_propiedad`
- `dim_clientes` → relacionada por `id_cliente`
- `dim_Fecha` → relacionada por `fecha_venta`, con campos: Año, Mes, Mes Numero, Año-Mes

La tabla de hechos incluye columnas calculadas adicionales: `Cohorte`, `Mes Venta` y `Meses desde inicio`, usadas en el análisis de cohortes.

---

## 🧠 Objetivos

### Objetivo del análisis

Construir un dashboard ejecutivo en Power BI que permita a Andes Capital Real Estate analizar su desempeño comercial, entender el comportamiento de sus clientes y propiedades, e identificar oportunidades estratégicas de crecimiento y retención, a partir de un modelo de datos estructurado en esquema estrella con inteligencia de tiempo.

### Objetivos de aprendizaje

- Preparar y validar datos para análisis en Power BI (Power Query)
- Construir un modelo de datos en esquema estrella con tabla calendario dinámica (`dim_Fecha`)
- Crear medidas analíticas en DAX: Ingreso Total, Ticket Promedio, Comisión Total, YoY, YTD y MTD
- Aplicar inteligencia de tiempo para analizar tendencias y crecimiento año contra año
- Diseñar dashboards con tres vistas navegables: Overview Ejecutivo, Análisis Comercial y Cohortes
- Analizar recurrencia de clientes mediante matrices de retención e ingreso por cohorte mensual

---

## 📊 Etapas del proyecto

| Paso | Descripción |
|------|-------------|
| 1 | Limpieza de datos: tipos, nulos y duplicados en claves primarias |
| 2 | Creación de tabla calendario `dim_Fecha` con DAX (`CALENDAR`, `ADDCOLUMNS`) |
| 3 | Modelado en esquema estrella: relaciones 1:* con dirección de filtro simple |
| 4 | Creación de medidas DAX: métricas base, YoY, YTD, MTD y columnas de cohorte |
| 5 | Diseño del dashboard: Overview Ejecutivo, Análisis Comercial y Análisis de Cohortes |
| 6 | Resumen ejecutivo: hallazgos, métricas clave, insights y recomendaciones estratégicas |

---

## 🛠️ Herramientas utilizadas

- Power BI Desktop
- Visualizaciones nativas (barras, líneas, tarjetas KPI, matrices de cohortes con formato condicional)
- DAX (medidas de inteligencia de tiempo: YoY, YTD, MTD; columnas calculadas: Cohorte, Mes Venta, Meses desde inicio)
- Power Query (limpieza y transformación de datos)
- Jupyter Notebook

---

## 💡 Principales hallazgos

- El ingreso total del período fue de **$6,012 millones** generado por **8,500 ventas**, con un ticket promedio de **$707,353** por transacción y comisiones por **$200,63 millones**
- Los tres tipos de propiedad (Casa, Comercial, Departamento) generan **ingresos casi idénticos**, pero con dinámicas muy distintas: **Departamento** lidera en volumen (5,105 unidades) y **Comercial** en ticket promedio ($1,797,097)
- El canal **Corredor** concentra la mayor participación en ingresos, superando ampliamente al canal Directo
- El segmento **Primera vez** lidera en ingreso total, siendo el motor principal del negocio por volumen
- **Ciudad de México** concentra la mayor parte del ingreso por ciudad, seguida de Bogotá
- Las ventas muestran un crecimiento **YoY del 11,14%** y la brecha entre 2024 y 2023 se amplía mes a mes
- Los **picos de inicio de año** marcan el ritmo de los ingresos con caídas pronunciadas en mitad del año
- La cohorte de **enero 2023** muestra la mayor recurrencia sostenida; la retención promedio por período se estabiliza alrededor del **9%**


---
👤 Autor
Juan Castelblanco - Analista de Datos - ConnectaTel
Sprint 7 - Análisis de Comportamiento de Clientes 2024

📝 Licencia
Este proyecto es de uso educativo y forma parte del programa de análisis de datos.

*Análisis basado en transacciones inmobiliarias 2023–2025 | Andes Capital Real Estate – Data Analytics Team*  
*Fecha de análisis: Marzo 2026*
