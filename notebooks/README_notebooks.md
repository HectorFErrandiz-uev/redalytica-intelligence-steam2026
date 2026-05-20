# /notebooks

Notebooks Jupyter que reproducen el pipeline completo de extracción, validación y procesamiento de datos de Redalytica Intelligence. Constituyen la trazabilidad técnica del proyecto y deben ejecutarse en el orden indicado.

## Contenido

| Notebook | Propósito |
|---|---|
| `00_descubrir_ids_correctos.ipynb` | Identifica y verifica los identificadores oficiales actualizados de los indicadores de la API ESIOS de Red Eléctrica de España. Genera el catálogo completo de los 2.019 indicadores disponibles y selecciona los 12 utilizados en el análisis. |
| `02_validacion_cruzada_v3.ipynb` | Cruza los agregados anuales obtenidos de REData con las publicaciones oficiales de Red Eléctrica de España, OMIE y CNMC para los ejercicios 2020 a 2024. Documenta las desviaciones y certifica que se mantienen por debajo del cinco por ciento en todos los indicadores principales. |
| `03_descarga_DEFINITIVA_apagon.ipynb` | Descarga los datos horarios y de diez minutos de ESIOS para la ventana del apagón del 28 de abril de 2025, comprendida entre el 25 y el 30 de abril. Produce los 24 CSVs brutos que alimentan el análisis forense. |
| `04_v3_procesado_final.ipynb` | Procesa, agrega y limpia los datos descargados. Construye las tablas maestras que se cargan en el modelo dimensional de Power BI: generación por tecnología, demanda, precios, intensidad de carbono y anatomía técnica del apagón. |

## Orden de ejecución

Los notebooks están numerados según el orden lógico recomendado. Las dependencias son:

1. `00` debe ejecutarse antes que `03`, ya que proporciona los identificadores actualizados de la API ESIOS
2. `02` puede ejecutarse de forma independiente una vez disponibles los datos de REData
3. `03` debe ejecutarse antes que `04`, ya que produce los archivos de entrada del procesamiento
4. `04` consume las salidas de `03` y produce las tablas finales consumidas por Power BI

## Requisitos previos

Antes de ejecutar los notebooks:

1. Crear un entorno virtual de Python e instalar las dependencias listadas en `requirements.txt`
2. Solicitar un token personal de la API ESIOS en https://www.esios.ree.es/es/pagina/api
3. Copiar el archivo `.env.example` a `.env` y rellenar la variable `ESIOS_TOKEN` con el token personal
4. Verificar conexión a internet estable

## Reproducibilidad

Los notebooks están diseñados para ser reproducibles desde cero. Toda la lógica está documentada en celdas markdown intercaladas con el código. Las celdas de descarga registran el momento exacto de la ejecución y el número de registros obtenidos.

El tiempo aproximado de ejecución completa del pipeline en un equipo estándar es de quince a veinte minutos, distribuidos principalmente en las llamadas a la API ESIOS. El procesamiento local posterior se completa en menos de dos minutos.

## Convenciones técnicas

- Codificación de archivos: UTF-8 sin BOM
- Marcas temporales: ISO 8601 con zona horaria explícita (UTC+2, CEST)
- Separador decimal: punto
- Separador de miles: ninguno
- Nombres de columnas: en inglés, en minúsculas y con guiones bajos como separadores
