📦 RETEX — Sistema de Gestión de Calidad Aplicado al Reciclaje Textil

Proyecto académico desarrollado como caso de estudio para la asignatura de Sistemas de Gestión de Calidad
Ingeniería Industrial · 5.º cuatrimestre · 2024


📋 Descripción del proyecto
RETEX es una empresa ficticia de reciclaje textil utilizada como caso de estudio para aplicar de manera integral los fundamentos teóricos y las herramientas prácticas de la gestión de calidad en un entorno de manufactura.
El proyecto aplica la Trilogía de Juran (Planeación, Control y Mejora de la Calidad) como marco metodológico central, desarrollando un sistema completo que abarca desde la identificación de clientes y necesidades hasta el análisis financiero del costo de la no calidad y la propuesta de mejora tecnológica mediante espectroscopía NIR.
Problemática abordada
RETEX enfrenta una brecha de calidad en la pureza de la fibra reciclada clasificada. La inconsistencia en los niveles de pureza genera rechazos por parte de las hilanderías clientes, incrementa los costos operativos por reclasificación y afecta la competitividad de la empresa en el mercado de la moda sostenible.
Objetivos del proyecto

Diseñar un sistema de planeación de la calidad basado en la identificación sistemática de clientes, necesidades y características de calidad medibles.
Implementar herramientas de Control Estadístico de Procesos (SPC) para monitorear la estabilidad y capacidad del proceso de clasificación.
Definir un conjunto de KPIs alineados con las etapas operativas del proceso y los objetivos de calidad establecidos.
Cuantificar el Costo de la No Calidad (CONC) y evaluar el retorno de la inversión en la implementación de tecnología NIR como mejora de innovación.


🔍 Contenido del repositorio
El proyecto se compone de tres entregables principales:
1. Retex.pdf — Reporte Técnico
Documento académico que desarrolla en profundidad:

Planeación de la calidad con identificación de clientes internos y externos, necesidades explícitas y latentes, y traducción a características de calidad medibles con métricas y frecuencias definidas.
Análisis de estabilidad del proceso mediante gráficos de control tipo p (fracción defectuosa de pureza) y X̄-R (media y rango del peso de pacas).
Análisis de capacidad de proceso con cálculo e interpretación de los índices Cp y Cpk.
Definición de 6 KPIs operativos con umbrales de alerta, responsables y justificación técnica.
Análisis del Costo de la No Calidad con desglose por categorías (fallas internas, fallas externas, inspección y prevención) y propuesta de mejora mediante sensor NIR con cálculo de ROI superior al 70% en el primer año.

2. Retex.xlsx — Base de Datos y Modelos de Cálculo
Archivo de Excel estructurado con modelo de datos relacional compuesto por 6 tablas normalizadas:
Tabla Contenido Filas Lotes Catálogo de 52 lotes semanales con tipo de fibra, turno y operador52Mediciones_Pureza5 mediciones de pureza por lote con cálculo acumulado de Cp y Cpk260Peso_Pacas20 subgrupos de 5 pacas con límites de control X̄-R calculados100KPIs_DiariosRegistro semanal de 6 KPIs con semáforo de alerta automático312Costos_CONCDesglose mensual del CONC por categoría con ahorro potencial NIR 48 Operadores Catálogo de 6 operadores con promedio de pureza y evaluación
Incluye hoja de Resumen ejecutivo con fórmulas dinámicas que consolidan los indicadores clave de todas las tablas.
3. Retex .pbix — Dashboard Interactivo en Power BI
Dashboard profesional de 3 páginas con modelo de datos, relaciones entre tablas y medidas DAX:
Página 1 — Resumen Ejecutivo
Panorama general del sistema con 6 tarjetas KPI, gráfico de pureza por semana con línea de especificación mínima, gráfico de alertas por KPI y segmentador por mes.
<img width="1375" height="775" alt="image" src="https://github.com/user-attachments/assets/eca9b234-1bec-4803-b9c6-48b0ae771076" />
Página 2 — Control del Proceso
Gráficos de control X̄ y R con límites de control calculados, tarjetas de capacidad (Cp, Cpk, Sigma), tabla de señales por subgrupo y filtros por turno y operador.
<img width="1376" height="778" alt="image" src="https://github.com/user-attachments/assets/f0715f80-a2ce-43a9-a7f0-c300c1e9cdf9" />
Página 3 — CONC y ROI
Gráfico de CONC mensual apilado por categoría, tendencia acumulada anual, tarjetas de ahorro potencial y ROI proyectado, y simulador interactivo what-if con slider para modelar diferentes escenarios de reducción de errores con el sensor NIR.
<img width="1379" height="778" alt="image" src="https://github.com/user-attachments/assets/2f033325-56c1-4005-8803-4a65ae090390" />
🛠️ Tecnologías utilizadas
Herramienta Versión Uso en el proyecto Microsoft Excel 2021 / Microsoft 365 Estructuración de datos, fórmulas de SPC, cálculo de Cp/Cpk, KPIs y CONC Power BI Desktop 2024 Modelo de datos relacional, medidas DAX, visualizaciones y dashboard interactivo DAX (Data Analysis Expressions)—Medidas de capacidad de proceso, análisis de alertas, simulación what-if de ROI
Funciones y conceptos clave aplicados
Excel:

DISTR.NORM.INV para generación de datos simulados con distribución normal
DESVEST.P para cálculo de sigma poblacional
PROMEDIO.SI.CONJUNTO para análisis cruzado entre tablas
INDICE + COINCIDIR para búsquedas relacionales entre hojas
Tablas estructuradas con relaciones por ID_Lote
Formato condicional con semáforos automáticos

Power BI / DAX:

CALCULATE + FILTER + ALL para medidas con contexto controlado
STDEVX.P para sigma del proceso en tiempo real
SWITCH(TRUE()) para clasificación dinámica del estado del proceso
SELECTEDVALUE para integración con parámetros what-if
DIVIDE con manejo de errores para cálculo de ROI
Parámetro de intervalo numérico para simulación interactiva


📚 Marco teórico de referencia

Trilogía de Juran: Juran, J. M., & Godfrey, A. B. (1999). Juran's Quality Handbook. McGraw-Hill.
Control Estadístico de Procesos: Montgomery, D. C. (2019). Introduction to Statistical Quality Control. Wiley.
Sistema de gestión de calidad: ISO 9001:2015. Sistemas de gestión de la calidad — Requisitos.


👤 Autor
Sergio Montes Cruz
Estudiante de Ingeniería Industrial · 5.º cuatrimestre
Asignatura: Sistemas de Gestión de Calidad · 2024


Este proyecto fue desarrollado con fines académicos utilizando datos simulados para la empresa ficticia RETEX. Los valores numéricos son representativos y han sido generados mediante distribuciones estadísticas para reflejar el comportamiento real de un proceso de reciclaje textil.
