# Redalytica Intelligence

**Inteligencia de mercado eléctrico español**

Análisis del sistema peninsular 2020–2026 y caso de estudio del apagón nacional del 28 de abril de 2025

![Licencia MIT](https://img.shields.io/badge/Licencia-MIT-blue.svg) ![Python 3.11](https://img.shields.io/badge/Python-3.11-blue.svg) ![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-yellow.svg) ![Premios STEAM 2026](https://img.shields.io/badge/Premios%20STEAM-2026-green.svg)

---

## Índice

1. [Visión general](#1-visión-general)
2. [Cifras clave del análisis](#2-cifras-clave-del-análisis)
3. [Caso de negocio: Redalytica Intelligence](#3-caso-de-negocio-redalytica-intelligence)
4. [Arquitectura técnica](#4-arquitectura-técnica)
5. [Estructura del repositorio](#5-estructura-del-repositorio)
6. [Cómo reproducir el proyecto](#6-cómo-reproducir-el-proyecto)
7. [Fuentes de datos](#7-fuentes-de-datos)
8. [El dashboard: 6 vistas operativas](#8-el-dashboard-6-vistas-operativas)
9. [Equipo](#9-equipo)
10. [Licencia y contacto](#10-licencia-y-contacto)

---

## 1. Visión general

Redalytica Intelligence es un proyecto académico desarrollado para los Premios STEAM 2026 de la Universidad Europea de Valencia (Grado en Ciencia de Datos Aplicada) que construye el producto mínimo viable de una plataforma de inteligencia de mercado eléctrico para el sistema peninsular español.

El proyecto combina dos planos complementarios:

- **Análisis técnico**: caracterización completa del sistema eléctrico peninsular durante 2020–2026, con foco específico en el apagón nacional del 28 de abril de 2025, sobre un modelo de datos consolidado con 270.544 registros oficiales.
- **Caso de negocio**: definición de problema cuantificado, mercado direccionable, líneas de producto, perfiles de cliente, modelo de monetización y proyecciones financieras a tres años para un eventual lanzamiento comercial.

El sistema eléctrico español ha cruzado el 49,8% de generación renovable en 2025, pero esta transición ha introducido una volatilidad estructural sin precedentes. Las empresas necesitan inteligencia accionable sobre este mercado. Redalytica Intelligence cubre ese hueco.

---

## 2. Cifras clave del análisis

| Indicador | Valor | Contexto |
|---|---|---|
| Generación total analizada | 1.546.107 GWh | Periodo 2020–2026 |
| Porcentaje renovable medio | 49,77% | Validado vs. REE oficial |
| Intensidad de carbono | 117,71 gCO₂/kWh | Coherente con CSRD |
| Demanda peninsular total | 1.455.002 GWh | Excluye no peninsular |
| Potencia instalada | 140.516 MW | Más reciente |
| Factor de carga sistémico | 15,68% | Tras corrección metodológica |
| Coeficiente variación precios | 110,9% | Volatilidad extrema |
| Horas con precio negativo | 4.034 | En 198 días distintos |
| Rango de precios horario | −14,05 → +654,91 €/MWh | Spread 47× |
| Caída generación apagón | −44,3% | 28 de abril de 2025 |
| Coste económico apagón | 1.300–1.800 M€ | CEOE / CEPYME |
| PYMES afectadas | ≈ 280.000 | CEPYME |
| Medidas DAX auditadas | 65 | Dos ciclos de revisión |
| Diferencia vs. publicaciones REE | < 5% | Validación cruzada |

---

## 3. Caso de negocio: Redalytica Intelligence

### 3.1 El problema que resolvemos

Las empresas españolas enfrentan cuatro problemas tangibles derivados de la transición energética:

1. **Volatilidad extrema de precios**: una industria mediana puede tener desviaciones de hasta 1,5 M€/año en su factura energética por una decisión incorrecta entre tarifa fija e indexada.
2. **Riesgo sistémico de interrupción**: el apagón del 28 de abril de 2025 costó a la economía española 1.300–1.800 M€ en 8–10 horas. Ninguna herramienta accesible permite a las empresas cuantificar su exposición.
3. **Cumplimiento normativo CSRD**: 16.000 empresas españolas obligadas desde 2025 a reportar intensidad de carbono eléctrica. Sin herramientas adecuadas para optimizar perfil de consumo.
4. **Valoración de activos renovables**: fondos de infraestructura necesitan modelos de captura de precio peninsular. Una desviación del 10% supone 50–100 M€ en la valoración de un parque medio.

### 3.2 Mercado

| Nivel | Cifra | Definición |
|---|---|---|
| TAM | 30.000 M€/año | Mercado eléctrico español facturado total (CNMC) |
| SAM | 80–120 M€/año | Servicios de información y consultoría energética |
| SOM Año 3 | 500–600 k€/año | 0,5% del SAM bajo escenario conservador |

### 3.3 Las 4 líneas de producto

- **Redalytica Dashboard** — Cuadro de mando bajo suscripción (desde 79 €/mes)
- **Redalytica API** — Interfaz de datos para integración (desde 149 €/mes)
- **Redalytica Reports** — Informes especializados (2.500–12.000 €/informe)
- **Redalytica Consulting** — Consultoría puntual (750 €/día)

### 3.4 Buyer personas

| Perfil | Sector típico | Rango anual |
|---|---|---|
| Dirección compras energéticas | Cerámica, química, acería | 6.000–12.000 € |
| Trading comercializadora | Comercializadoras mid-market | 18.000–30.000 € |
| Sustainability Officer retail | Mercadona, El Corte Inglés, Inditex | 60–120 k€ |
| Asset Manager fondos renovables | Macquarie, Plenium, Q-Energy | 35–80 k€ |
| COO datacenter | Microsoft Azure, AWS, Equinix | 80–150 k€ |

### 3.5 Proyecciones financieras (escenario conservador)

| Concepto | Año 1 | Año 2 | Año 3 |
|---|---|---|---|
| Clientes recurrentes | 5 | 20 | 41 |
| Ingresos totales | 45.000 € | 210.000 € | 560.000 € |
| EBITDA | −30.000 € | +45.000 € | +240.000 € |
| Margen EBITDA | — | 21% | 43% |

**Break-even operativo:** mes 14–18.

---

## 4. Arquitectura técnica

```
┌─────────────────────────────────────────────────────────────────┐
│                       FUENTES DE DATOS                          │
├──────────────────────┬───────────────────┬──────────────────────┤
│   REE REData         │   REE ESIOS       │   OMIE (referencia)  │
│   API pública        │   API autenticada │   Validación cruzada │
│   Diaria/mensual     │   10 min / hora   │   Horaria oficial    │
└──────────┬───────────┴────────┬──────────┴──────────┬───────────┘
           │                    │                     │
           ▼                    ▼                     ▼
┌─────────────────────────────────────────────────────────────────┐
│                  CAPA DE INGESTA Y PROCESAMIENTO                │
│       Python 3.11  ·  pandas  ·  requests  ·  numpy             │
│   4 notebooks documentados con validación cruzada y auditoría   │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                   CAPA ANALÍTICA (Power BI)                     │
│  · Modelo dimensional con 13 tablas y 10 relaciones             │
│  · 65 medidas DAX organizadas en 8 carpetas temáticas           │
│  · Validación: diferencia <5% frente a publicaciones REE        │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                      CAPA DE PRESENTACIÓN                       │
│        Dashboard con 6 vistas interactivas integradas           │
└─────────────────────────────────────────────────────────────────┘
```

Diagrama de arquitectura completo disponible en `/docs/Figura_10_Arquitectura_Tecnica.svg`.

### Stack tecnológico

| Componente | Tecnología |
|---|---|
| Lenguaje de procesamiento | Python 3.11 |
| Librerías principales | pandas, numpy, requests, matplotlib |
| Visualización | Power BI Desktop |
| Lenguaje de cálculo | DAX (Data Analysis Expressions) |
| Documentación técnica | Markdown + Word |
| Control de versiones | Git + GitHub |

---

## 5. Estructura del repositorio

```
premios-steam-2026/
│
├── README.md                                       ← Este documento
├── LICENSE                                         ← MIT License
├── requirements.txt                                ← Dependencias Python
├── .gitignore
├── .env.example                                    ← Plantilla de variables
├── tema-energia-espana.json                        ← Tema visual Power BI v1
├── tema-energia-espana-v2.json                     ← Tema visual Power BI v2
│
├── notebooks/
│   ├── README.md                                   ← Documentación de notebooks
│   ├── 00_descubrir_ids_correctos.ipynb            ← Catálogo oficial ESIOS
│   ├── 02_validacion_cruzada_v3.ipynb              ← Validación vs. fuentes oficiales
│   ├── 03_descarga_DEFINITIVA_apagon.ipynb         ← Ingesta API ESIOS apagón
│   └── 04_v3_procesador_final.ipynb                ← Procesamiento y agregación
│
├── datos/
│   ├── README.md                                   ← Política de almacenamiento
│   ├── redata_raw/                                 ← (ignorado por .gitignore)
│   └── esios_raw/                                  ← (ignorado por .gitignore)
│
├── tableau/
│   ├── README.md                                   ← Documentación del dashboard
│   └── capturas/                                   ← Las 6 vistas en PNG
│       ├── 01_cero_neto_cero_apagones.png
│       ├── 02_mix_energetico.png
│       ├── 03_resistencia_transicion.png
│       ├── 04_28_abril_2025_apagon.png
│       ├── 05_anomalias_sistema.png
│       └── 06_anatomia_apagon.png
│
├── memoria/
│   ├── README.md
│   └── Memoria_Redalytica_Intelligence_STEAM2026_final.docx
│
├── presentacion/
│   ├── README.md
│   └── Redalytica_Intelligence_Presentation_Final.pptx
│
└── docs/
    ├── README.md
    ├── Figura_10_Arquitectura_Tecnica.svg          ← Diagrama vectorial
    └── Figura_10_Arquitectura_Tecnica.png          ← Diagrama exportado
```

> **Nota:** los CSVs brutos (carpetas `datos/redata_raw/` y `datos/esios_raw/`) y el archivo Power BI Desktop (`dashboard-energia-espana.pbix`) no se incluyen en este repositorio por su volumen. Disponibles en repositorio externo bajo solicitud al equipo.

---

## 6. Cómo reproducir el proyecto

### Requisitos previos

- Python 3.11 o superior
- Power BI Desktop (última versión, gratuita para Windows)
- Token API ESIOS: solicitar gratuitamente enviando email a consultasios@ree.es indicando finalidad académica o de investigación
- Git instalado

### Pasos

```bash
# 1. Clonar repositorio
git clone https://github.com/[usuario]/redalytica-intelligence.git
cd redalytica-intelligence

# 2. Crear entorno virtual e instalar dependencias
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate

pip install -r requirements.txt

# 3. Configurar token ESIOS
cp .env.example .env
# Editar el archivo .env y rellenar la variable ESIOS_TOKEN

# 4. Ejecutar notebooks en orden
jupyter notebook

# Abrir y ejecutar siguiendo el orden indicado en notebooks/README.md:
#   00_descubrir_ids_correctos.ipynb
#   02_validacion_cruzada_v3.ipynb
#   03_descarga_DEFINITIVA_apagon.ipynb
#   04_v3_procesador_final.ipynb

# 5. Abrir el dashboard
# Solicitar el archivo dashboard-energia-espana.pbix al equipo
# y abrirlo con Power BI Desktop
```

---

## 7. Fuentes de datos

Todos los datos provienen de fuentes oficiales públicas. No hay datos de pago ni propietarios.

| Fuente | Tipo | URL | Cobertura | Volumen |
|---|---|---|---|---|
| REE REData | API pública sin autenticación | https://www.ree.es/es/apidatos | 2020–2026 diaria/mensual | 270.544 registros |
| REE ESIOS | API autenticada (token gratuito) | https://api.esios.ree.es | 25–30 abril 2025 horaria | ≈ 43.000 registros |
| OMIE | Web pública | https://www.omie.es | 2020–2025 referencia | Validación cruzada |
| CNMC | Informes PDF | https://www.cnmc.es | 2020–Q1 2026 | Contraste |

### Cómo solicitar el token ESIOS

1. Enviar email a consultasios@ree.es
2. Indicar nombre, organización (universidad) y finalidad (proyecto académico)
3. Recepción del token en aproximadamente 24–48 horas
4. Configurar el token en el archivo `.env` (creado a partir de `.env.example`)

> El token ESIOS es personal e intransferible. El archivo `.env` está incluido en `.gitignore` para evitar su subida accidental.

---

## 8. El dashboard: 6 vistas operativas

| # | Vista | Contenido principal |
|---|---|---|
| 1 | Cero Neto, Cero Apagones | KPIs principales del sistema 2020–2026 y narrativa hero |
| 2 | Mix Energético | Treemap, área apilada y tabla detallada de 17 tecnologías |
| 3 | Resistencia y Transición | Análisis de la demanda peninsular, estacionalidad y variaciones interanuales |
| 4 | 28 de abril de 2025: el apagón | Anatomía minuto a minuto del evento con datos ESIOS |
| 5 | Anomalías del Sistema | Precios negativos, crisis 2022 y eventos extremos |
| 6 | Anatomía del apagón | Desglose tecnológico minuto a minuto desde ESIOS |

Capturas de las seis vistas disponibles en `/tableau/capturas/`.

### Paleta corporativa

| Color | Hex | Uso |
|---|---|---|
| Azul Renovable | `#1E5288` | Primario, KPIs |
| Verde Sostenible | `#3CB371` | Renovables |
| Naranja Crisis | `#E76F51` | Apagón, alertas |
| Violeta Nuclear | `#7C7DAD` | Tecnología nuclear |
| Amarillo Solar | `#F4C430` | Solar FV |
| Turquesa Hidráulica | `#7FCDCD` | Hidráulica |
| Azul Cielo Eólica | `#5DADE2` | Eólica |
| Antracita | `#2B2D42` | Texto principal |
| Gris Perla | `#F4F4F6` | Fondos |

Definición completa en `tema-energia-espana-v2.json` (raíz del repositorio).

---

## 9. Equipo

| Miembro | Rol |
|---|---|
| Héctor Ferrándiz Sanchis | Arquitectura técnica, modelo de datos, dashboard Power BI |
| Martina Arellano | Storytelling, presentación y comunicación comercial |
| David González | Análisis estadístico y validación cruzada |
| Irene Bautista | Caso de negocio y segmentación de mercado |

**Tutor académico:** José Luis Gómez Ortega

**Institución:** Universidad Europea de Valencia · Grado en Ciencia de Datos Aplicada · Curso 2025–2026

---

## 10. Licencia y contacto

Este proyecto está publicado bajo licencia MIT (ver `LICENSE`). El uso académico, formativo y comercial está permitido siempre que se mantenga la atribución a los autores.

**Contacto principal:** farrandizhector@gmail.com

Bibliografía completa disponible en la memoria académica (`memoria/`).

---

*Redalytica Intelligence · Premios STEAM 2026 · Universidad Europea de Valencia*

*Construido con datos públicos · validado contra fuentes oficiales · diseñado para impacto real*
