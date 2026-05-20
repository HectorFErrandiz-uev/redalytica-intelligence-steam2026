# /tableau

Dashboard analítico de Redalytica Intelligence construido en Power BI Desktop.

## Contenido visible en el repositorio

| Archivo | Descripción |
|---|---|
| `capturas/vista_01_resumen_ejecutivo.png` | KPIs principales del sistema eléctrico peninsular y hero "España hacia 2030". |
| `capturas/vista_02_mix_energetico.png` | Treemap del mix energético, gráfico de área apilada por tecnología y tabla detallada de las 17 tecnologías de generación. |
| `capturas/vista_03_demanda_estabilidad.png` | Tres KPIs de demanda y tres visualizaciones sobre estacionalidad y estabilidad de la red. |
| `capturas/vista_04_apagon.png` | Cuatro KPIs y tres gráficos centrados en el día 28 de abril de 2025: caída de demanda, generación y recuperación. |
| `capturas/vista_05_anomalias_crisis.png` | Detección de horas con precio negativo, eventos extremos y tabla TOP 5 de anomalías. |
| `capturas/vista_06_anatomia_esios.png` | Forensia técnica horaria del apagón con datos ESIOS a granularidad de 10 minutos. |

## Archivo Power BI Desktop

El archivo `dashboard-energia-espana.pbix` (modelo dimensional con 13 tablas, 65 medidas DAX auditadas y conexión a CSVs procesados de REData, ESIOS y OMIE) no se incluye en este repositorio porque supera el límite de tamaño de GitHub.

Disponible bajo solicitud al equipo. Los datos crudos sobre los que opera están documentados en `/datos/README.md`.

## Reproducibilidad

Para reproducir el dashboard:

1. Descargar el archivo `.pbix` desde el enlace facilitado por el equipo
2. Abrirlo con Power BI Desktop (versión gratuita)
3. Apuntar las fuentes de datos a la ubicación local de los CSVs descargados con los notebooks de la carpeta `/notebooks`
4. Actualizar el modelo (Inicio → Actualizar)

## Sistema de diseño

El dashboard utiliza la paleta corporativa documentada en `/docs/paleta_corporativa.md`, con tipografías Segoe UI para los títulos y Consolas para los valores numéricos.
