# 📊 Dashboard de Control de Productividad y Calidad en Manufactura Multiplanta

## 🎯 Problema de Negocio
Una empresa manufacturera multinacional con operaciones en 8 países (Japón, Canadá, China, Francia, India, Alemania, EE. UU. y Brasil) registra variaciones significativas en la eficiencia de sus líneas de producción y cuellos de botella generados por tiempos no productivos[cite: 10].

La gerencia de operaciones requiere visibilidad centralizada para:
* Evaluar el volumen global de producción frente al volumen de piezas rechazadas[cite: 10].
* Identificar los principales obstáculos operativos que generan horas no productivas[cite: 10].
* Comparar el desempeño técnico por ubicación, operador y periodo mensual[cite: 10].
* Establecer un estándar de calidad (>99%) e índice de productividad general[cite: 10].

---

## 📁 Dataset / Fuente de Datos
* **Origen:** Registros transaccionales de planta de producción (`Productividad.xlsx`).
* **Volumen:** 31,616 órdenes de producción registradas entre enero de 2021 y enero de 2022.
* **Campos clave:** `No. Orden`, `Operador`, `Ubicación`, `Producto`, `Obstáculos`, `Fecha inicio`, `Fecha fin`, `Total Horas`, `Piezas producidas` y `Piezas rechazadas`.

---

## ⚙️ Metodología y Proceso
1. **Limpieza y Preparación de Datos (Power Query):**
   * Detección y tratamiento de valores nulos en el campo `Obstáculos` (categorizados como *"Sin Obstáculos / Operación Normal"*).
   * Creación de la columna calculada `Piezas Buenas = Piezas producidas - Piezas rechazadas`.
2. **Modelado de Datos y Métricas en DAX:**
   * Creación de una tabla de fechas dedicada (*Calendar Table*) para habilitar inteligencia de tiempo dinámico por mes y año.
   * Desarrollo de medidas DAX para cuantificar horas productivas, horas no productivas y la tasa de calidad global.
3. **Diseño UX/UI en Power BI:**
   * Implementación de una interfaz ejecutiva en modo oscuro con navegación interactiva mediante segmentadores por *Operador*, *Mes* y *Ubicación*[cite: 10].
   * Integración de tarjetas de KPI principales (*Piezas Buenas*, *Piezas Rechazadas*, *Horas Productivas*) e indicadores visuales de medidor (*Gauge charts*) para medir Porcentaje de Calidad y Productividad[cite: 10].

---

## 🛠️ Herramientas Utilizadas
* **Power BI Desktop:** Modelado de datos, lenguaje DAX, Power Query y maquetación interactiva del reporte[cite: 10].
* **Excel / Python (Pandas):** Auditoría previa de datos, validación de distribuciones y comprobación de métricas de consistencia.

---

## 💡 Hallazgos Principales (Insights)
* **Calidad Global Alta con Desviaciones Puntuales:** De un total de **3,084,251 piezas producidas**, se obtuvieron **3,063,175 piezas buenas**, alcanzando un porcentaje de calidad del **99.32%** (superando la meta corporativa del 99%)[cite: 10]. Sin embargo, se registraron **21,076 piezas rechazadas**.
* **Impacto Severo de Horas No Productivas:** Del total de 39,846.55 horas operativas registradas, **8,890.41 horas (22.3%) correspondieron a tiempos con obstáculos/paradas**.
* **Concentración de Cuellos de Botella:** Dos obstáculos explican el **77.3%** del total de tiempo perdido:
  1. **Preparación de la máquina:** 3,735.73 horas perdidas (42.0% del tiempo de parada).
  2. **Control de calidad:** 3,137.49 horas perdidas (35.3% del tiempo de parada).
* **Distribución Geográfica:** Japón (5,984.9 hrs) y Canadá (5,343.9 hrs) lideran el consumo de horas de producción, concentrando también el mayor volumen fabricado.

---

## 🎯 Recomendaciones de Negocio
* **Estandarización de Ajuste de Maquinaria (SMED):** Implementar la metodología *Single-Minute Exchange of Die* (SMED) en los procesos de *"Preparación de la máquina"* para reducir el tiempo de cambio de formato e incrementar la disponibilidad en un 15%.
* **Reingeniería del Flujo de Control de Calidad:** Rediseñar la inspección de calidad para integrar controles en línea o muestreos automatizados, disminuyendo el cuello de botella de 3,137 horas.
* **Capacitación Operativa:** Replicar las mejores prácticas de las plantas con mejor relación Piezas/Hora en las ubicaciones que presentan mayores paradas por *"Falla del operador"* (660.3 horas perdidas).

---

## 🚀 ¿Qué decisión tomaría con estos datos?
1. **Reasignación de Presupuesto CAPEX/OPEX:** Redirigir el presupuesto de mantenimiento preventivo prioritariamente hacia la automatización del *setup* de maquinaria en las plantas de Japón y Canadá.
2. **Establecimiento de SLA Internos para Inspecciones:** Fijar un tiempo máximo estándar para las revisiones del área de Calidad, minimizando el tiempo muerto entre tandas de producción.
3. **Plan de Incentivos por OEE:** Evaluar el rendimiento individual y por ubicación integrando no solo la cantidad de piezas producidas, sino la tasa de paradas evitables.

---

## 🖼️ Evidencias / Dashboard

![Dashboard de Productividad y Piezas Fabricadas](Productividad_piezas_fabricadas.pdf)[cite: 10]

---

## 📂 Estructura del Repositorio
```text
├── README.md                           <- Presentación ejecutiva del proyecto
├── data/
│   └── Productividad.xlsx               <- Dataset original / procesado
├── dashboard/
│   ├── Productividad_Planta.pbix       <- Archivo ejecutable de Power BI
│   └── screenshots/                    <- Capturas de pantalla del reporte
│       └── overview.png
└── dax_measures/
    └── Calidad_y_Productividad.dax     <- Código DAX utilizado para KPIs
